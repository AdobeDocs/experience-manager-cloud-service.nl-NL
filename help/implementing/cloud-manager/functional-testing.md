---
title: Functionele tests
description: Leer over de drie verschillende types van functionele tests die in het AEM as a Cloud Service plaatsingsproces worden gebouwd om kwaliteit en betrouwbaarheid van uw code te verzekeren.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: cd0b40ffa54eac0d7488b23329c4d2666c992da7
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---


# Functionele tests {#functional-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Functionele tests"
>abstract="Leer over de drie verschillende types van functionele tests die in het AEM as a Cloud Service plaatsingsproces worden gebouwd om kwaliteit en betrouwbaarheid van uw code te verzekeren."

Meer informatie over de drie verschillende typen functionele tests die in de [as a Cloud Service implementatieproces AEM](/help/implementing/cloud-manager/deploy-code.md) om de kwaliteit en betrouwbaarheid van uw code te garanderen.

## Overzicht {#overview}

Er zijn drie verschillende soorten functionele tests in AEM as a Cloud Service.

* [Functioneel testen van producten](#product-functional-testing)
* [Aangepaste functionele tests](#custom-functional-testing)
* [Aangepaste UI-tests](#custom-ui-testing)

Voor alle functionele tests kunnen de gedetailleerde resultaten van de tests als `.zip` bestand met de **Buildlog downloaden** knoop in het bouwstijloverzichtsscherm als deel van [implementatieproces.](/help/implementing/cloud-manager/deploy-code.md)

Deze logboeken bevatten niet de logboeken van het werkelijke AEM runtimeproces. Raadpleeg het document voor toegang tot deze logboeken [Logbestanden openen en beheren](/help/implementing/cloud-manager/manage-logs.md) voor meer informatie .

Zowel de functionele tests van het product als de aangepaste functionele tests zijn gebaseerd op de [AEM Clients testen.](https://github.com/adobe/aem-testing-clients)

### Functioneel testen van producten {#product-functional-testing}

De functionele tests van het product zijn een reeks stabiele HTTP integratietests (ITs) van kernfunctionaliteit in AEM zoals creatie en replicatietaken. Deze tests worden gehandhaafd door Adobe en zijn bedoeld om veranderingen in de code van de douanetoepassing te verhinderen worden opgesteld als het kernfunctionaliteit breekt.

* [Productiepijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md): Functionele tests voor producten worden automatisch uitgevoerd wanneer u nieuwe code implementeert in Cloud Manager en kunnen niet worden overgeslagen.
* [Niet-productiepijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md): De functionele tests van het product kunnen naar keuze worden geselecteerd om te lopen wanneer u uw niet productiepijplijn uitvoert.

De functionele tests van het product worden gehandhaafd als open-source-project. Zie [functionele producttests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) in GitHub voor meer informatie.

### Aangepaste functionele tests {#custom-functional-testing}

Terwijl het functionele testen van producten door Adobe wordt bepaald, kunt u uw eigen kwaliteitstests voor uw eigen toepassing schrijven. Dit wordt uitgevoerd als aangepaste functionele tests in het kader van de [productiepijpleiding](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) of optioneel [niet-productiepijpleiding](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) om de kwaliteit van uw toepassing te garanderen.

Het functionele testen van de douane wordt uitgevoerd zowel voor douanecode plaatsingen als duw verbeteringen, die het vooral belangrijk maken om goede functionele tests te schrijven die AEM codeveranderingen verhinderen uw toepassingscode te breken. De aangepaste functionele teststap is altijd aanwezig en kan niet worden overgeslagen.

### Aangepaste UI-tests {#custom-ui-testing}

Het testen van de gebruikersinterface van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw toepassingen tot stand te brengen en automatisch in werking te stellen. De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om voor een brede keus van taal en kaders zoals Java en Maven, Node en WebDriver.io, of om het even welk ander kader en technologie toe te staan die op Selenium worden voortgebouwd.

Raadpleeg het document [Aangepaste UI-tests](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) voor meer informatie .

## Aan de slag met functionele tests {#getting-started-functional-tests}

Nadat u een nieuwe gegevensopslagruimte voor code hebt gemaakt in Cloud Manager, kunt u `it.tests` De map wordt automatisch gemaakt met voorbeelden van testgevallen.

>[!NOTE]
>
>Als uw opslagplaats is gemaakt voordat Cloud Manager automatisch is gemaakt `it.tests` mappen, kunt u ook de nieuwste versie genereren met de [AEM Projectarchetype.](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/it.tests)

Wanneer u de inhoud van de `it.tests` kunt u de map gebruiken als basis voor uw eigen tests en vervolgens:

1. [Ontwikkel uw testcase.](#writing-functional-tests)
1. [Voer de tests lokaal uit.](#local-test-execution)
1. Leg uw code vast in de gegevensopslagruimte van Cloud Manager en voer een pijplijn van Cloud Manager uit.

## Aangepaste functionele tests schrijven {#writing-functional-tests}

De zelfde hulpmiddelen die Adobe gebruikt om product functionele tests te schrijven kunnen worden gebruikt om uw douane functionele tests te schrijven. Gebruik de [functionele producttests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) in GitHub als voorbeeld van hoe te om uw tests te schrijven.

De code voor een aangepaste functionele test is Java-code in het dialoogvenster `it.tests` van uw project. Het moet één JAR met alle functionele tests produceren. Als de build meer dan één testJAR produceert, is de geselecteerde JAR niet-deterministisch. Als er nultestJAR&#39;s worden geproduceerd, gaat de teststap standaard over. [Zie het AEM Project Archetype](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests) voor monstertests.

De tests worden uitgevoerd op door Adobe onderhouden testinfrastructuren met minimaal twee auteurinstanties, twee publiceerinstanties en een dispatcherconfiguratie. Dit betekent dat uw aangepaste functionele tests worden uitgevoerd tegen de gehele AEM stapel.

### Structuur van functionele tests {#functional-tests-structure}

Aangepaste functionele tests moeten worden verpakt als een afzonderlijk JAR-bestand dat wordt geproduceerd door dezelfde Maven-build als de artefacten die moeten worden ingezet voor AEM. Over het algemeen zou dit een afzonderlijke module Maven zijn. Het resulterende JAR-bestand moet alle vereiste afhankelijkheden bevatten en wordt gewoonlijk gemaakt met de opdracht `maven-assembly-plugin` met de `jar-with-dependencies` descriptor.

Bovendien moet de JAR de `Cloud-Manager-TestType` manifestkoptekst ingesteld op `integration-test`.

Hier volgt een voorbeeldconfiguratie voor de `maven-assembly-plugin`.

```java
<build>
    <plugins>
        <!-- Create self-contained jar with dependencies -->
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <version>3.1.0</version>
            <configuration>
                <descriptorRefs>
                    <descriptorRef>jar-with-dependencies</descriptorRef>
                </descriptorRefs>
                <archive>
                    <manifestEntries>
                        <Cloud-Manager-TestType>integration-test</Cloud-Manager-TestType>
                    </manifestEntries>
                </archive>
            </configuration>
            <executions>
                <execution>
                    <id>make-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
```

Binnen dit JAR-bestand moeten de klassenamen van de werkelijke uit te voeren tests eindigen in `IT`.

Een klasse met de naam `com.myco.tests.aem.it.ExampleIT` zou worden uitgevoerd, maar een klasse met de naam `com.myco.tests.aem.it.ExampleTest` niet.

Bovendien moet de testcode onder een pakket met de naam `it` (Het filter voor uitsluitingen van dekking is `**/it/**/*.java`).

De testklassen moeten normale JUnit-tests zijn. De testinfrastructuur is zodanig ontworpen en geconfigureerd dat deze compatibel is met de conventies die door de `aem-testing-clients` testbibliotheek. Ontwikkelaars worden ten zeerste aangeraden deze bibliotheek te gebruiken en de best practices ervan te volgen.

Raadpleeg de [`aem-testing-clients` GitHub-repo](https://github.com/adobe/aem-testing-clients) voor meer informatie .

>[!TIP]
>
>[Deze video bekijken](https://www.youtube.com/watch?v=yJX6r3xRLHU) over hoe u aangepaste functionele tests kunt gebruiken om uw vertrouwen in uw CI/CD pijpleidingen te verbeteren.

### Uitvoering lokale test {#local-test-execution}

Voordat u functionele tests activeert in een Cloud Manager-pijplijn, is het raadzaam de functionele tests lokaal uit te voeren met de [as a Cloud Service SDK AEM](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) of een werkelijk AEM as a Cloud Service instantie.

#### Vereisten {#prerequisites}

De tests in Cloud Manager worden uitgevoerd met een technische beheerder.

Voor het uitvoeren van de functionele tests van uw lokale computer, creeer een gebruiker met admin-als toestemmingen om het zelfde gedrag te bereiken.

#### Het lopen in winde {#running-in-an-ide}

Omdat testklassen JUnit-tests zijn, kunnen ze vanuit gangbare Java IDE&#39;s zoals Eclipse, IntelliJ en NetBeans worden uitgevoerd. Omdat zowel de functionele tests van het product als de douane functionele tests op de zelfde technologie gebaseerd zijn, kunnen allebei plaatselijk worden in werking gesteld door de producttests in uw douanetests te kopiëren.

Bij het uitvoeren van deze tests is het echter noodzakelijk een aantal verschillende systeemeigenschappen in te stellen die door de `aem-testing-clients` (en de onderliggende Sling Testing Clients)-bibliotheek.

De systeemeigenschappen zijn als volgt.

* `sling.it.instances - should be set to 2`
* `sling.it.instance.url.1 - should be set to the author URL, for example, http://localhost:4502`
* `sling.it.instance.runmode.1 - should be set to author`
* `sling.it.instance.adminUser.1 - should be set to the author admin user, for example, admin`
* `sling.it.instance.adminPassword.1 - should be set to the author admin password`
* `sling.it.instance.url.2 - should be set to the publish URL, for example, http://localhost:4503`
* `sling.it.instance.runmode.2 - should be set to publish`
* `sling.it.instance.adminUser.2 - should be set to the publish admin user, for example, admin`
* `sling.it.instance.adminPassword.2 - should be set to the publish admin password`

#### Alle tests uitvoeren met Maven {#using-maven}

1. Open een shell en navigeer naar de `it.tests` in uw opslagplaats.

1. Voer het volgende bevel uit die de noodzakelijke vangers verstrekken om de tests te beginnen gebruikend Maven.

```shell
mvn verify -Plocal \
    -Dit.author.url=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
    -Dit.author.user=<user> \
    -Dit.author.password=<password> \
    -Dit.publish.url=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
    -Dit.publish.user=<user> \
    -Dit.publish.password=<password>
```
