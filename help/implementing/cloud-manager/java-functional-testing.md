---
title: Java&trade; functionele tests
description: Leer hoe u Java &amp schrijft;handel; functionele tests voor AEM as a Cloud Service
exl-id: e014b8ad-ac9f-446c-bee8-adf05a6b4d70
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 369e49e5a047bcfb41712aeb952a30ca90f7802f
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 0%

---


# Functioneel testen in Java™

Meer informatie over het schrijven van functionele Java™-tests voor AEM as a Cloud Service

## Aan de slag met functionele tests {#getting-started-functional-tests}

Nadat u een nieuwe gegevensopslagruimte voor code hebt gemaakt in Cloud Manager, wordt er automatisch een map `it.tests` gemaakt met voorbeelden van testgevallen.

>[!NOTE]
>
>Als uw bewaarplaats vóór Cloud Manager automatisch creeerde `it.tests` omslagen werd gecreeerd, kunt u de recentste versie ook produceren gebruikend het [ Archetype van het Project van AEM ](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/it.tests).

Als u de inhoud van de map `it.tests` hebt, kunt u deze gebruiken als basis voor uw eigen tests en vervolgens:

1. [ ontwikkelt uw testgevallen ](#writing-functional-tests).
1. [ stel de tests plaatselijk in werking ](#local-test-execution).
1. Leg uw code vast in de Cloud Manager-opslagplaats en voer een Cloud Manager-pijplijn uit.

## Aangepaste functionele tests schrijven {#writing-functional-tests}

Dezelfde tools die Adobe gebruikt om functionele tests voor producten te schrijven, kunnen worden gebruikt om aangepaste functionele tests te schrijven. Gebruik de [ product functionele tests ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) in GitHub als voorbeeld van hoe te om uw tests te schrijven.

De code voor aangepaste functionele test is Java™-code in de map `it.tests` van uw project. Het moet één JAR met alle functionele tests produceren. Als de build meer dan één testJAR produceert, is de geselecteerde JAR niet-deterministisch. Als er nultestJAR&#39;s worden geproduceerd, gaat de teststap standaard over. Zie [ Archetype van het Project van AEM ](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests) voor steekproeftests.

De tests worden uitgevoerd op testinfrastructuren die door Adobe worden onderhouden, waaronder ten minste twee auteur-instanties, twee publiceer-instanties en een Dispatcher-configuratie. Dit betekent dat uw aangepaste functionele tests worden uitgevoerd op de hele AEM-stapel.

### Structuur van functionele tests {#functional-tests-structure}

Aangepaste functionele tests moeten worden verpakt als een afzonderlijk JAR-bestand dat door dezelfde Maven-build wordt geproduceerd als de artefacten die in AEM worden geïmplementeerd. Over het algemeen zou deze build een aparte module Maven zijn. Het resulterende JAR-bestand moet alle vereiste afhankelijkheden bevatten en wordt doorgaans gemaakt met de `maven-assembly-plugin` met behulp van de `jar-with-dependencies` -descriptor.

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
| Geheugen | 0,5 Gi | Hoeveelheid aan de test toegewezen geheugen, waarde in bytes |
| Time-out | 30 m | De tijdslimiet waarna de test stopt. |
| Aanbevolen duur | 15 m | Adobe raadt aan de tests te schrijven om deze tijd niet langer te laten duren. |

#### Afhankelijkheden

* aem-cloud-testing-clients:

De aanstaande veranderingen in de containerized infrastructuur voor het uitvoeren van functionele tests vereisen het bijwerken van [ aem-wolk-test-cliënten ](https://github.com/adobe/aem-testing-clients) bibliotheek in uw douane functionele tests aan versie **1.2.1** of hoger. Zorg ervoor dat de afhankelijkheid in het `it.tests/pom.xml` -bestand overeenkomstig wordt bijgewerkt.

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
>Als u er niet in slaagt de afhankelijkheidsbibliotheek bij te werken, kan dit leiden tot mislukte pijplijnen bij de stap Aangepast functioneel testen.

### Uitvoering lokale test {#local-test-execution}

Alvorens functionele tests in een pijpleiding van Cloud Manager te activeren, wordt het geadviseerd om de functionele tests plaatselijk in werking te stellen gebruikend [ AEM as a Cloud Service SDK ](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) of een daadwerkelijke instantie van AEM as a Cloud Service.

#### Het lopen in winde {#running-in-an-ide}

Omdat testklassen JUnit-tests zijn, kunnen ze worden uitgevoerd vanuit mainstream Java ™ IDE&#39;s zoals Eclipse, IntelliJ en NetBeans. Omdat zowel de functionele tests van het product als de douane functionele tests op de zelfde technologie gebaseerd zijn, kunnen allebei plaatselijk worden in werking gesteld door de producttests in uw douanetests te kopiëren.

Wanneer u deze tests uitvoert, moet u echter verschillende systeemeigenschappen instellen die door de bibliotheek `aem-testing-clients` (en de onderliggende testclients) worden verwacht.

De systeemeigenschappen zijn als volgt.

| Eigenschap | Beschrijving | Voorbeeld |
|-------------------------------------|------------------------------------------------------------------|-------------------------|
| `sling.it.instances` | Aantal instanties dat overeenkomt met de cloudservice moet zijn ingesteld op `2` . | `2` |
| `sling.it.instance.url.1` | Instellen op auteur-URL. | `http://localhost:4502` |
| `sling.it.instance.runmode.1` | De modus Uitvoeren van de eerste instantie. Instellen op `author` . | `author` |
| `sling.it.instance.adminUser.1` | Instellen op beheerder van auteur. | `admin` |
| `sling.it.instance.adminPassword.1` | Instellen op beheerderswachtwoord van auteur. |                         |
| `sling.it.instance.url.2` | instellen voor publiceren van URL. | `http://localhost:4503` |
| `sling.it.instance.runmode.2` | De modus Uitvoeren van de tweede instantie. Instellen op `publish` . | `publish` |
| `sling.it.instance.adminUser.2` | Instellen op publiceren van beheergebruiker. | `admin` |
| `sling.it.instance.adminPassword.2` | Stel deze optie in om het beheerderswachtwoord te publiceren. |                         |

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
