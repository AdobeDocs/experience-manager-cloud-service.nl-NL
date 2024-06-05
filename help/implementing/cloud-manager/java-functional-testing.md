---
title: Java&trade; functietests
description: Leer hoe u Java&trade schrijft; functionele tests voor AEM as a Cloud Service
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

Nadat u een nieuwe gegevensopslagruimte voor code hebt gemaakt in Cloud Manager, kunt u `it.tests` De map wordt automatisch gemaakt met voorbeelden van testgevallen.

>[!NOTE]
>
>Als uw opslagplaats is gemaakt voordat Cloud Manager automatisch is gemaakt `it.tests` mappen, kunt u ook de meest recente versie genereren met de [AEM Projectarchetype.](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/it.tests)

Wanneer u de inhoud van de `it.tests` kunt u de map gebruiken als basis voor uw eigen tests en vervolgens:

1. [Ontwikkel uw testdoosjes.](#writing-functional-tests)
1. [Voer de tests lokaal uit.](#local-test-execution)
1. Leg uw code vast in de gegevensopslagruimte van Cloud Manager en voer een pijplijn van Cloud Manager uit.

## Aangepaste functionele tests schrijven {#writing-functional-tests}

De zelfde hulpmiddelen die de Adobe gebruikt om product functionele tests te schrijven kunnen worden gebruikt om uw douane functionele tests te schrijven. Gebruik de [functionele producttests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) in GitHub als voorbeeld van hoe te om uw tests te schrijven.

De code voor een aangepaste functionele test is Java™-code in het dialoogvenster `it.tests` van uw project. Het moet één JAR met alle functionele tests produceren. Als de build meer dan één testJAR produceert, is de geselecteerde JAR niet-deterministisch. Als er nultestJAR&#39;s worden geproduceerd, gaat de teststap standaard over. [Zie het AEM Project Archetype](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests) voor monstertests.

De tests worden in werking gesteld op Adobe-onderhouden testende infrastructuur met inbegrip van minstens twee auteurinstanties, twee publiceer instanties, en een configuratie van de Verzender. Deze opstelling betekent dat uw douane functionele tests tegen de volledige AEM stapel in werking stellen.

### Structuur van functionele tests {#functional-tests-structure}

Aangepaste functionele tests moeten worden verpakt als een afzonderlijk JAR-bestand dat wordt geproduceerd door dezelfde Maven-build als de artefacten die moeten worden ingezet voor AEM. Over het algemeen zou deze build een aparte module Maven zijn. Het resulterende JAR-bestand moet alle vereiste afhankelijkheden bevatten en wordt gewoonlijk gemaakt met de opdracht `maven-assembly-plugin` met de `jar-with-dependencies` descriptor.

Bovendien moet de JAR de `Cloud-Manager-TestType` manifestkoptekst ingesteld op `integration-test`.

Hier volgt een voorbeeldconfiguratie voor de `maven-assembly-plugin`.

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

Binnen dit JAR-bestand moeten de klassenamen van de werkelijke uit te voeren tests eindigen in `IT`.

Een klasse met de naam `com.myco.tests.aem.it.ExampleIT` zou worden uitgevoerd, maar een klasse met de naam `com.myco.tests.aem.it.ExampleTest` niet.

Bovendien moet de testcode onder een pakket met de naam `it` (Het filter voor uitsluitingen van dekking is `**/it/**/*.java`).

De testklassen moeten normale JUnit-tests zijn. De testinfrastructuur is zodanig ontworpen en geconfigureerd dat deze compatibel is met de conventies die door de `aem-testing-clients` testbibliotheek. Ontwikkelaars worden aangeraden deze bibliotheek te gebruiken en de beste praktijken ervan te volgen.

Zie [`aem-testing-clients` GitHub-repo](https://github.com/adobe/aem-testing-clients) voor meer informatie .

>[!TIP]
>
>[Deze video bekijken](https://www.youtube.com/watch?v=yJX6r3xRLHU) over hoe u aangepaste functionele tests kunt gebruiken om uw vertrouwen in uw CI/CD pijpleidingen te verbeteren.

### Vereisten {#prerequisites}

1. De tests in Cloud Manager worden uitgevoerd met een technische beheerder.

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

Voor de komende wijzigingen in de containerinfrastructuur die wordt gebruikt om functionele tests uit te voeren, is de bibliotheek vereist [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) gebruikt in uw aangepaste functionele test die moet worden bijgewerkt naar ten minste versie **1.**
Zorg ervoor dat uw afhankelijkheid binnen `it.tests/pom.xml` is bijgewerkt.

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

Alvorens functionele tests in een pijplijn van de Manager van de Wolk te activeren, adviseert het om de functionele tests plaatselijk in werking te stellen gebruikend [AS A CLOUD SERVICE SDK AEM](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) of een werkelijk AEM as a Cloud Service instantie.

#### Het lopen in winde {#running-in-an-ide}

Omdat testklassen JUnit-tests zijn, kunnen ze worden uitgevoerd vanuit mainstream Java™ IDE&#39;s zoals Eclipse, IntelliJ en NetBeans. Omdat zowel de functionele tests van het product als de douane functionele tests op de zelfde technologie gebaseerd zijn, kunnen allebei plaatselijk worden in werking gesteld door de producttests in uw douanetests te kopiëren.

Bij het uitvoeren van deze tests is het echter noodzakelijk verschillende systeemeigenschappen in te stellen die door de `aem-testing-clients` (en de onderliggende Sling Testing Clients)-bibliotheek.

De systeemeigenschappen zijn als volgt.

| Eigenschap | Beschrijving | Voorbeeld |
|-------------------------------------|------------------------------------------------------------------|-------------------------|
| `sling.it.instances` | aantal instanties dat moet worden ingesteld op `2` | `2` |
| `sling.it.instance.url.1` | moet worden ingesteld op de URL van de auteur | `http://localhost:4502` |
| `sling.it.instance.runmode.1` | uitvoeringsmodus van de eerste instantie, moet worden ingesteld op `author` | `author` |
| `sling.it.instance.adminUser.1` | moet worden ingesteld op de scriptgebruiker. | `admin` |
| `sling.it.instance.adminPassword.1` | moet worden ingesteld op het beheerderswachtwoord van de auteur. |                         |
| `sling.it.instance.url.2` | moet worden ingesteld op de publicatie-URL | `http://localhost:4503` |
| `sling.it.instance.runmode.2` | uitvoeringsmodus van de tweede instantie, moet worden ingesteld op `publish` | `publish` |
| `sling.it.instance.adminUser.2` | moet worden ingesteld op de gebruiker van de publicatiebeheerder. | `admin` |
| `sling.it.instance.adminPassword.2` | moet worden ingesteld op het wachtwoord voor publicatiebeheer. |                         |



#### Alle tests uitvoeren met Maven {#using-maven}

1. Open een shell en navigeer naar `it.tests` in uw opslagplaats.

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

