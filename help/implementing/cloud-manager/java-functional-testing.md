---
title: Java&trade; functionele tests
description: Leer hoe u Java&amp schrijft;handel; functionele tests voor AEM as a Cloud Service
exl-id: e014b8ad-ac9f-446c-bee8-adf05a6b4d70
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 0%

---

# Functioneel testen in Java™

Meer informatie over het schrijven van functionele Java™-tests voor AEM as a Cloud Service

## Aan de slag met functionele tests {#getting-started-functional-tests}

Nadat u een nieuwe gegevensopslagruimte voor code hebt gemaakt in Cloud Manager, wordt er automatisch een map `it.tests` gemaakt met voorbeelden van testgevallen.

>[!NOTE]
>
>Als uw bewaarplaats vóór Cloud Manager automatisch creeerde `it.tests` omslagen werd gecreeerd, kunt u de recentste versie ook produceren gebruikend [ AEM Archetype van het Project.](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/it.tests)

Als u de inhoud van de map `it.tests` hebt, kunt u deze gebruiken als basis voor uw eigen tests en vervolgens:

1. [Ontwikkel uw testdoosjes.](#writing-functional-tests)
1. [Voer de tests lokaal uit.](#local-test-execution)
1. Leg uw code vast in de Cloud Manager-opslagplaats en voer een Cloud Manager-pijplijn uit.

## Aangepaste functionele tests schrijven {#writing-functional-tests}

De zelfde hulpmiddelen die de Adobe gebruikt om product functionele tests te schrijven kunnen worden gebruikt om uw douane functionele tests te schrijven. Gebruik de [ product functionele tests ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) in GitHub als voorbeeld van hoe te om uw tests te schrijven.

De code voor aangepaste functionele test is Java™-code in de map `it.tests` van uw project. Het moet één JAR met alle functionele tests produceren. Als de build meer dan één testJAR produceert, is de geselecteerde JAR niet-deterministisch. Als er nultestJAR&#39;s worden geproduceerd, gaat de teststap standaard over. [ zie het AEM Archetype van het Project ](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests) voor steekproeftests.

De tests worden uitgevoerd op testinfrastructuur die door de Adobe wordt onderhouden, inclusief ten minste twee auteur-instanties, twee publiceer-instanties en een Dispatcher-configuratie. Deze opstelling betekent dat uw douane functionele tests tegen de volledige AEM stapel in werking stellen.

### Structuur van functionele tests {#functional-tests-structure}

Aangepaste functionele tests moeten worden verpakt als een afzonderlijk JAR-bestand dat wordt geproduceerd door dezelfde Maven-build als de artefacten die moeten worden ingezet voor AEM. Over het algemeen zou deze build een aparte module Maven zijn. Het resulterende JAR-bestand moet alle vereiste afhankelijkheden bevatten en wordt doorgaans gemaakt met de `maven-assembly-plugin` met behulp van de `jar-with-dependencies` -descriptor.

Daarnaast moet voor de JAR de header `Cloud-Manager-TestType` manifest zijn ingesteld op `integration-test` .

Hier volgt een voorbeeldconfiguratie voor de `maven-assembly-plugin` .

```XML
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
</build>
```

In dit JAR-bestand moeten de klassenamen van de tests die daadwerkelijk moeten worden uitgevoerd, eindigen in `IT` .

Een klasse met de naam `com.myco.tests.aem.it.ExampleIT` wordt bijvoorbeeld uitgevoerd, maar een klasse met de naam `com.myco.tests.aem.it.ExampleTest` niet.

Bovendien moet de testcode zich onder een pakket met de naam `it` bevinden om testcode uit te sluiten van de dekkingscontrole van de codescanfunctie (het filter voor dekkingsuitsluiting is `**/it/**/*.java` ).

De testklassen moeten normale JUnit-tests zijn. De testinfrastructuur is zodanig ontworpen en geconfigureerd dat deze compatibel is met de conventies die worden gebruikt in de testbibliotheek van `aem-testing-clients` . Ontwikkelaars worden aangeraden deze bibliotheek te gebruiken en de beste praktijken ervan te volgen.

Zie [`aem-testing-clients` reactie GitHub ](https://github.com/adobe/aem-testing-clients) voor meer details.

>[!TIP]
>
>[ bekijk deze video ](https://www.youtube.com/watch?v=yJX6r3xRLHU) over hoe u douane functionele tests kunt gebruiken om uw vertrouwen in uw pijpleidingen te verbeteren CI/CD.

### Vereisten {#prerequisites}

1. De tests in Cloud Manager worden uitgevoerd met een technische admin-gebruiker.

>[!NOTE]
>
>Voor het uitvoeren van de functionele tests van uw lokale computer, creeer een gebruiker met admin-als toestemmingen om het zelfde gedrag te bereiken.

1. De containerinfrastructuur die is bestemd voor functionele tests, wordt beperkt door de volgende grenzen:


| Type | Waarde | Beschrijving |
|----------------------|-------|--------------------------------------------------------------------|
| CPU | 0,5 | Hoeveelheid CPU-tijd gereserveerd per testuitvoering |
| Geheugen | 0,5 Gi | Hoeveelheid geheugen dat aan de test is toegewezen, waarde in bytes |
| Time-out | 30 m | De duur waarna de test wordt beëindigd. |
| Aanbevolen duur | 15 m | De Adobe beveelt aan de tests te schrijven om deze tijd niet langer te laten duren. |

>[!NOTE]
>
> Als u meer middelen nodig hebt, maakt u een geval voor de klantenservice en beschrijft u uw gebruiksscenario. Het team van de Adobe evalueert uw verzoek en biedt de gewenste hulp.

#### Afhankelijkheden

* aem-cloud-testing-clients:

De aanstaande veranderingen in de containerized infrastructuur die wordt gebruikt om functionele tests uit te voeren, zullen de bibliotheek [ aem-wolk-test-cliënten ](https://github.com/adobe/aem-testing-clients) vereisen die in uw douane functionele test wordt gebruikt om aan minstens versie **1.2.1** worden bijgewerkt
Zorg ervoor dat uw afhankelijkheid in `it.tests/pom.xml` is bijgewerkt.

```
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.1</version>
</dependency>
```

>[!NOTE]
>
>Deze wijziging moet worden uitgevoerd vóór 6 april 2024.
>Als u er niet in slaagt de afhankelijkheidsbibliotheek bij te werken, treedt er een fout op bij de stap Aangepast functioneel testen.

### Uitvoering lokale test {#local-test-execution}

Alvorens functionele tests in een pijpleiding van Cloud Manager te activeren, wordt het geadviseerd om de functionele tests plaatselijk in werking te stellen gebruikend [ AEM as a Cloud Service SDK ](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) of een daadwerkelijke instantie van AEM as a Cloud Service.

#### Het lopen in winde {#running-in-an-ide}

Omdat testklassen JUnit-tests zijn, kunnen ze worden uitgevoerd vanuit mainstream Java™ IDE&#39;s zoals Eclipse, IntelliJ en NetBeans. Omdat zowel de functionele tests van het product als de douane functionele tests op de zelfde technologie gebaseerd zijn, kunnen allebei plaatselijk worden in werking gesteld door de producttests in uw douanetests te kopiëren.

Wanneer u deze tests uitvoert, moet u echter verschillende systeemeigenschappen instellen die door de bibliotheek `aem-testing-clients` (en de onderliggende testclients) worden verwacht.

De systeemeigenschappen zijn als volgt.

| Eigenschap | Beschrijving | Voorbeeld |
|-------------------------------------|------------------------------------------------------------------|-------------------------|
| `sling.it.instances` | aantal instanties dat moet worden ingesteld op `2` om overeen te komen met de cloudservice | `2` |
| `sling.it.instance.url.1` | moet worden ingesteld op de URL van de auteur | `http://localhost:4502` |
| `sling.it.instance.runmode.1` | uitvoeringsmodus van de eerste instantie, moet worden ingesteld op `author` | `author` |
| `sling.it.instance.adminUser.1` | moet worden ingesteld op de scriptgebruiker. | `admin` |
| `sling.it.instance.adminPassword.1` | moet worden ingesteld op het beheerderswachtwoord van de auteur. |                         |
| `sling.it.instance.url.2` | moet worden ingesteld op de publicatie-URL | `http://localhost:4503` |
| `sling.it.instance.runmode.2` | uitvoeringsmodus van de tweede instantie, moet zijn ingesteld op `publish` | `publish` |
| `sling.it.instance.adminUser.2` | moet worden ingesteld op de gebruiker van de publicatiebeheerder. | `admin` |
| `sling.it.instance.adminPassword.2` | moet worden ingesteld op het wachtwoord voor publicatiebeheer. |                         |



#### Alle tests uitvoeren met Maven {#using-maven}

1. Open een shell en navigeer naar de `it.tests` map in uw repository.

1. Voer het volgende bevel uit die de noodzakelijke parameters verstrekken om de tests te beginnen gebruikend Maven.

```shell
mvn verify -Plocal \
    -Dit.author.url=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
    -Dit.author.user=<user> \
    -Dit.author.password=<password> \
    -Dit.publish.url=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
    -Dit.publish.user=<user> \
    -Dit.publish.password=<password>
```

