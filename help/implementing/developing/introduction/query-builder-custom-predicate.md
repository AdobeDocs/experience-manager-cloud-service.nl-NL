---
title: Het uitvoeren van een Evaluator van de Predicatie van de Douane voor de Bouwer van de Vraag
description: De Bouwer van de Vraag in AEM biedt een gemakkelijke, klantgerichte manier om de inhoudsbewaarplaats te vragen
exl-id: 8c2f8c22-1851-4313-a1c9-10d6d9b65824
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Het uitvoeren van een Evaluator van de Predicatie van de Douane voor de Bouwer van de Vraag {#implementing-a-custom-predicate-evaluator-for-the-query-builder}

Dit document beschrijft hoe te om de [&#x200B; Bouwer van de Vraag &#x200B;](query-builder-api.md) uit te breiden door een douane uit te voeren predikt beoordelaar.

## Overzicht {#overview}

De [&#x200B; Bouwer van de Vraag &#x200B;](query-builder-api.md) biedt een gemakkelijke manier aan om de inhoudsbewaarplaats te vragen. AEM komt met [&#x200B; een reeks predikaten beoordelaars &#x200B;](#query-builder-predicates.md) die u helpen uw gegevens vragen.

Nochtans zou u uw vragen kunnen willen vereenvoudigen door een douane uit te voeren predikt beoordelaar die wat ingewikkeldheid verbergt en een betere semantiek verzekert.

Een aangepaste predikaat kan ook andere dingen uitvoeren die niet direct mogelijk zijn met XPath, bijvoorbeeld:

* Gegevens opvragen van een andere service
* Aangepast filteren op basis van een berekening

>[!NOTE]
>
>De kwesties van prestaties moeten in overweging worden genomen wanneer het uitvoeren van een douane predikaat.

>[!TIP]
>
>U kunt voorbeelden van vragen in het [&#128279;](query-builder-api.md) document vinden van de Bouwer van de Vraag 0&rbrace; &lbrace;.

>[!TIP]
>
>U kunt de code van deze pagina op GitHub vinden
>
>* [&#x200B; open a-onderzoek-douane-predicaat-evaluatorproject op GitHub &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)
>* Download het project als [&#x200B; een dossier van het PIT &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/archive/master.zip)

>[!NOTE]
>
>Deze verbonden code op GitHub en de codefragmenten in dit document worden verstrekt slechts voor demonstratiedoeleinden.

### Voorspelende evaluator in detail {#predicate-evaluator-in-detail}

Een predikaat beoordelaar behandelt de evaluatie van bepaalde predikaten, die de bepalende beperkingen van een vraag zijn.

Er wordt een zoekbeperking op een hoger niveau (zoals `width>200` ) toegewezen aan een specifieke JCR-query die past bij het daadwerkelijke inhoudsmodel (bijvoorbeeld `metadata/@width > 200` ). Of het kan knopen manueel filtreren en hun beperkingen controleren.

>[!TIP]
>
>Voor meer informatie over `PredicateEvaluator` en het `com.day.cq.search` pakket zie de [&#x200B; documentatie van Java &#x200B;](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html?com/day/cq/search/package-summary.html).

### Implementatie van een aangepaste voorspellende evaluator voor replicatiemetagegevens {#implementing-a-custom-predicate-evaluator-for-replication-metadata}

Als voorbeeld beschrijft deze sectie hoe te om een douane te creëren predikaat beoordelaar die gegevens helpt die op de replicatiemetagegevens worden gebaseerd:

* `cq:lastReplicated` die de datum van de laatste replicatieactie opslaat
* `cq:lastReplicatedBy` die de id opslaat van de gebruiker die de laatste replicatieactie heeft geactiveerd.
* `cq:lastReplicationAction` die de laatste replicatiehandeling opslaat (bijvoorbeeld Activering, Deactivering)

#### Replicatiemetagegevens met standaardvoorspellende evaluatoren opvragen {#querying-replication-metadata-with-default-predicate-evaluators}

Met de volgende query wordt de lijst opgehaald met knooppunten in de `/content` -vertakking die door `admin` zijn geactiveerd sinds het begin van het jaar.

```xml
path=/content

1_property=cq:lastReplicatedBy
1_property.value=admin

2_property=cq:lastReplicationAction
2_property.value=Activate

daterange.property=cq:lastReplicated
daterange.lowerBound=2013-01-01T00:00:00.000+01:00
daterange.lowerOperation=>=
```

Deze vraag is geldig maar moeilijk te lezen en benadrukt niet het verband tussen de drie replicatieeigenschappen. Het uitvoeren van een douane predikaat evaluator zal de ingewikkeldheid verminderen en de semantiek van deze vraag verbeteren.

#### Doelstellingen {#objectives}

Het doel van de `ReplicationPredicateEvaluator` is om de bovenstaande query met de volgende syntaxis te ondersteunen.

```xml
path=/content

replic.by=admin
replic.since=2013-01-01T00:00:00.000+01:00
replic.action=Activate
```

Het groeperen van replicatiemagegevens predikt met een douane predikaat evaluator helpt om een zinvolle vraag tot stand te brengen.

#### Geweven afhankelijkheden bijwerken {#updating-maven-dependencies}

>[!TIP]
>
>De opstelling van nieuwe AEM projecten met inbegrip van het gebruiken van maven wordt verklaard in detail door [&#x200B; het WKND leerprogramma &#x200B;](develop-wknd-tutorial.md).

Eerst moet u de Geweven gebiedsdelen van uw project bijwerken. `PredicateEvaluator` maakt deel uit van het `cq-search` -artefact, dus moet het worden toegevoegd aan het GMaven-pomabestand.

>[!NOTE]
>
>Het bereik van de `cq-search` afhankelijkheid wordt ingesteld op `provided` omdat `cq-search` wordt opgegeven door de `OSGi` -container.

Het volgende fragment toont de verschillen in het `pom.xml` dossier, in [&#x200B; verenigd diff formaat &#x200B;](https://en.wikipedia.org/wiki/Diff#Unified_format)

```text
@@ -120,6 +120,12 @@
             <scope>provided</scope>
         <dependency>
+            <groupid>com.day.cq</groupid>
+            <artifactid>cq-search</artifactid>
+            <version>5.6.4</version>
+            <scope>provided</scope>
+        </dependency>
+        <dependency>
             <groupid>junit</groupid>
             <artifactid>junit</artifactid>
             <version>3.8.1</version></dependency>
```

#### Het schrijven van ReplicationPredicateEvaluator {#writing-the-replicationpredicateevaluator}

Het `cq-search` -project bevat de `AbstractPredicateEvaluator` abstracte klasse. Dit kan worden uitgebreid met een paar stappen om uw eigen aangepaste evaluatieversie van het predikaat te implementeren `(PredicateEvaluator` .)

>[!NOTE]
>
>In de volgende procedure wordt uitgelegd hoe u een expressie `Xpath` kunt bouwen om gegevens te filteren. Een andere mogelijkheid is om de methode `includes` te implementeren waarmee gegevens op rijbasis worden geselecteerd. Zie de [&#x200B; documentatie van Java &#x200B;](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html) voor meer informatie.

1. Een nieuwe Java-klasse maken die een uitbreiding vormt `com.day.cq.search.eval.AbstractPredicateEvaluator`
1. Annoteer uw klasse met a `@Component` als fragment toont in [&#x200B; verenigd diff formaat &#x200B;](https://en.wikipedia.org/wiki/Diff#Unified_format)

   ```text
   @@ -19,8 +19,11 @@
     */
    package com.adobe.aem.docs.search;
   
   +import org.apache.felix.scr.annotations.Component;
   +import com.day.cq.search.eval.AbstractPredicateEvaluator;
   
   +@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")
    public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {
   
    }
   ```

   >[!NOTE]
   >
   >`factory` moet een uniek koord zijn dat met `com.day.cq.search.eval.PredicateEvaluator/` begint en met de naam van uw douane `PredicateEvaluator` beëindigt.

   >[!NOTE]
   >
   >De naam van de `PredicateEvaluator` is de naam van de voorspelling, die wordt gebruikt bij het maken van query&#39;s.

1. Overschrijven:

   ```java
   public String getXPathExpression(Predicate predicate, EvaluationContext context)
   ```

   In de overschrijfmethode bouwt u een `Xpath` -expressie op basis van de `Predicate` in het argument.

### Voorbeeld van een aangepaste voorspellende evaluator voor replicatiemetagegevens {#example-of-a-custom-predicate-evaluator-for-replication-metadata}

De volledige implementatie van deze `PredicateEvaluator` is mogelijk vergelijkbaar met de volgende klasse.

```java
/*
 * #%L
 * aem-docs-custom-predicate-evaluator
 * %%
 * Copyright (C) 2013 Adobe Research
 * %%
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *      http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 * #L%
 */

package com.adobe.aem.docs.search;

import org.apache.felix.scr.annotations.Component;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.day.cq.search.Predicate;
import com.day.cq.search.eval.AbstractPredicateEvaluator;
import com.day.cq.search.eval.EvaluationContext;

@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")

public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {

    static final String PE_NAME = "replic";


    static final String PN_LAST_REPLICATED_BY = "cq:lastReplicatedBy";
    static final String PN_LAST_REPLICATED = "cq:lastReplicated";
    static final String PN_LAST_REPLICATED_ACTION = "cq:lastReplicationAction";

    static final String PREDICATE_BY = "by";
    static final String PREDICATE_SINCE = "since";
    static final String PREDICATE_SINCE_OP = " >= ";
    static final String PREDICATE_ACTION = "action";

    Logger log = LoggerFactory.getLogger(getClass());

    /**
     * Returns a XPath expression filtering by replication metadata.
     *
     * @see com.day.cq.search.eval.AbstractPredicateEvaluator#getXPathExpression(com.day.cq.search.Predicate,
     *      com.day.cq.search.eval.EvaluationContext)
     */

    @Override

    public String getXPathExpression(Predicate predicate,
            EvaluationContext context) {

        log.debug("predicate {}", predicate);

        String date = predicate.get(PREDICATE_SINCE);
        String user = predicate.get(PREDICATE_BY);
        String action = predicate.get(PREDICATE_ACTION);

        StringBuilder sb = new StringBuilder();

        if (date != null) {

            sb.append(PN_LAST_REPLICATED).append(PREDICATE_SINCE_OP);
            sb.append("xs:dateTime('").append(date).append("')");

        }

        if (user != null) {

            addAndOperator(sb);
            sb.append(PN_LAST_REPLICATED_BY);
            sb.append("='").append(user).append("'");

        }

        if (action != null) {

            addAndOperator(sb);
            sb.append(PN_LAST_REPLICATED_ACTION);
            sb.append("='").append(action).append("'");

        }

        String xpath = sb.toString();

        log.debug("xpath **{}**", xpath);

        return xpath;

    }

    /**
     * Add an and operator if the builder is not empty.
     *
     * @param sb a {@link StringBuilder} containing the query under construction
     */

    private void addAndOperator(StringBuilder sb) {

        if (sb.length() != 0) {

            sb.append(" and ");

        }

    }

}
```
