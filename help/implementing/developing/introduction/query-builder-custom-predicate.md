---
title: Het uitvoeren van een Evaluator van de Predicatie van de Douane voor de Bouwer van de Vraag
description: De Bouwer van de Vraag in AEM biedt een gemakkelijke, klantgerichte manier om de inhoudsbewaarplaats te vragen
exl-id: 8c2f8c22-1851-4313-a1c9-10d6d9b65824
source-git-commit: c08e442e58a4ff36e89a213aa7b297b538ae3bab
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 0%

---

# Het uitvoeren van een Evaluator van de Predicatie van de Douane voor de Bouwer van de Vraag {#implementing-a-custom-predicate-evaluator-for-the-query-builder}

In dit document wordt beschreven hoe u het dialoogvenster [Query Builder](query-builder-api.md) door een aangepaste evaluatieversie van de predikaat te implementeren.

## Overzicht {#overview}

De [Query Builder](query-builder-api.md) biedt een eenvoudige manier om de opslagplaats voor inhoud te vragen. AEM wordt geleverd met [een reeks beoordelaars met voorspelling](#query-builder-predicates.md) waarmee u uw gegevens kunt opvragen.

Nochtans zou u uw vragen kunnen willen vereenvoudigen door een douane uit te voeren predikt beoordelaar die wat ingewikkeldheid verbergt en een betere semantiek verzekert.

Een aangepaste predikaat kan ook andere dingen uitvoeren die niet direct mogelijk zijn met XPath, bijvoorbeeld:

* Gegevens opvragen van een andere service
* Aangepast filteren op basis van een berekening

>[!NOTE]
>
>De kwesties van prestaties moeten in overweging worden genomen wanneer het uitvoeren van een douane predikaat.

>[!TIP]
>
>U vindt voorbeelden van query&#39;s in het dialoogvenster [Query Builder](query-builder-api.md) document.

>[!TIP]
>
>U kunt de code van deze pagina op GitHub vinden
>
>* [Open aem-onderzoek-douane-predicaat-evaluatorproject op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)
>* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/archive/master.zip)


>[!NOTE]
>
>Deze verbonden code op GitHub en de codefragmenten in dit document worden verstrekt slechts voor demonstratiedoeleinden.

### Voorspelende evaluator in detail {#predicate-evaluator-in-detail}

Een predikaat beoordelaar behandelt de evaluatie van bepaalde predikaten, die de bepalende beperkingen van een vraag zijn.

Hiermee wordt een zoekrestrictie op een hoger niveau toegewezen (zoals `width>200`) naar een specifieke JCR-query die past bij het werkelijke inhoudsmodel (bijvoorbeeld `metadata/@width > 200`). Of het kan knopen manueel filtreren en hun beperkingen controleren.

>[!TIP]
>
>Voor meer informatie over de `PredicateEvaluator` en de `com.day.cq.search` pakket zie [Java-documentatie](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html?com/day/cq/search/package-summary.html).

### Implementatie van een aangepaste voorspellende evaluator voor replicatiemetagegevens {#implementing-a-custom-predicate-evaluator-for-replication-metadata}

Als voorbeeld beschrijft deze sectie hoe te om een douane te creëren predikaat beoordelaar die gegevens helpt die op de replicatiemetagegevens worden gebaseerd:

* `cq:lastReplicated` die de datum van de laatste replicatieactie opslaat
* `cq:lastReplicatedBy` die identiteitskaart van de gebruiker opslaat die de laatste replicatieactie teweegbracht
* `cq:lastReplicationAction` die de laatste replicatiehandeling opslaat (bijvoorbeeld activering, deactivering)

#### Replicatiemetagegevens met standaardvoorspellende evaluatoren opvragen {#querying-replication-metadata-with-default-predicate-evaluators}

Met de volgende query wordt de lijst met knooppunten opgehaald in `/content` vertakking die is geactiveerd door `admin` sinds het begin van het jaar.

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

Het doel van het `ReplicationPredicateEvaluator` moet bovenstaande query met de volgende syntaxis ondersteunen.

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
>De opzet van nieuwe AEM met inbegrip van het gebruik van maven wordt in detail toegelicht door [de WKND-zelfstudie.](develop-wknd-tutorial.md)

Eerst moet u de Geweven gebiedsdelen van uw project bijwerken. De `PredicateEvaluator` maakt deel uit van de `cq-search` artefact zodat moet het aan uw Gepompdossier van Maven worden toegevoegd.

>[!NOTE]
>
>Het toepassingsgebied van de `cq-search` afhankelijkheid is ingesteld op `provided` omdat `cq-search` wordt verstrekt door de `OSGi` container.

In het volgende fragment worden de verschillen in de `pom.xml` bestand, in [Unified Diff-indeling](https://en.wikipedia.org/wiki/Diff#Unified_format)

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

De `cq-search` het project bevat `AbstractPredicateEvaluator` abstracte klasse. Dit kan met een paar stappen worden uitgebreid om uw eigen douane uit te voeren voorspelt beoordelaar `(PredicateEvaluator`).

>[!NOTE]
>
>De volgende procedure laat zien hoe u een `Xpath` expressie om gegevens te filteren. Een andere mogelijkheid zou zijn om de `includes` methode die gegevens op rijbasis selecteert. Zie de [Java-documentatie](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html) voor meer informatie .

1. Een nieuwe Java-klasse maken die een uitbreiding `com.day.cq.search.eval.AbstractPredicateEvaluator`
1. Annoteer uw klasse met een `@Component` zoals fragmenten in [Unified Diff-indeling](https://en.wikipedia.org/wiki/Diff#Unified_format)

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
   >De `factory`moet een unieke tekenreeks zijn die begint met `com.day.cq.search.eval.PredicateEvaluator/`en eindigend met de naam van uw aangepaste `PredicateEvaluator`.

   >[!NOTE]
   >
   >De naam van de `PredicateEvaluator` is de predicaatnaam, die wordt gebruikt wanneer het bouwen van vragen.

1. Overschrijven:

   ```java
   public String getXPathExpression(Predicate predicate, EvaluationContext context)
   ```

   In de overschrijfmethode bouwt u een `Xpath` op basis van de `Predicate` geargumenteerd.

### Voorbeeld van een aangepaste voorspellende evaluator voor replicatiemetagegevens {#example-of-a-custom-predicate-evaluator-for-replication-metadata}

De volledige uitvoering van deze `PredicateEvaluator` Dit kan vergelijkbaar zijn met de volgende klasse.

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
