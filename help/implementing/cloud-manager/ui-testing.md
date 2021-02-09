---
title: UI Testing - Cloud Services
description: UI Testing - Cloud Services
translation-type: tm+mt
source-git-commit: ea0c9675ca03b1d247c7e5fd13e03072fb4a13ae
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 0%

---


# UI Testen {#ui-testing}

De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om een brede keus in taal en kaders (zoals Java en Maven, Node en WebDriver.io, of om het even welk ander kader en technologie toe te staan die op Selenium worden voortgebouwd). De Docker-afbeelding kan met standaardgereedschappen worden gemaakt, maar tijdens de uitvoering ervan moet deze afbeelding bepaalde conventies respecteren. Bij het uitvoeren van de Docker-afbeelding wordt automatisch een Selenium-server ingericht. Met de onderstaande runtimeconventies heeft uw testcode toegang tot zowel de Selenium-server als de AEM die worden getest.

>[!NOTE]
> Het werkgebied en de productiepijpleidingen die vóór 10 februari 2021 zijn gemaakt, moeten worden bijgewerkt om de interfacetests te kunnen gebruiken zoals beschreven op deze pagina.
> Zie [Het vormen van uw CI-CD Pijpleiding](/help/implementing/cloud-manager/configure-pipeline.md) voor informatie over pijpleidingsconfiguratie.

## UI-tests voor het samenstellen van {#building-ui-tests}

De tests UI worden gebouwd uit een Docker bouwt context die door een Geweven project wordt geproduceerd. Cloud Manager gebruikt de Docker-ontwikkelcontext om een Docker-afbeelding te genereren die de werkelijke UI-tests bevat. Samengevat, produceert een Beweerd project een Docker bouwt context, en het Docker bouwt context beschrijft hoe te om een beeld van de Docker tot stand te brengen die de tests UI bevat.

Deze sectie gaat door de stappen nodig om een project van de Tests UI aan uw bewaarplaats toe te voegen. Als u in een haast bent of geen speciale vereisten voor de programmeertaal hebt, kan [AEM Project Archetype](https://github.com/adobe/aem-project-archetype) een project van de Tests UI voor u produceren.

### Een Docker-constructiecontext {#generate-docker-build-context} genereren

Om Docker te produceren bouwt context, hebt u een Gemaakt module nodig die:

- Produceert een archief dat `Dockerfile` en elk ander dossier noodzakelijk bevat om het beeld van de Docker met uw tests te bouwen.
- Hiermee wordt het archief gecodeerd met de classificator `ui-test-docker-context`.

De eenvoudigste manier om dit te bereiken is [Maven Insteekmodule van de Assemblage ](http://maven.apache.org/plugins/maven-assembly-plugin/) te vormen om het Docker te creëren bouwt contextarchief en wijst het juiste classificatiebureau aan het toe.

U kunt tests UI met verschillende technologieën en kaders bouwen, maar deze sectie veronderstelt dat uw project op een manier gelijkend op het volgende wordt opgemaakt.

```
├── Dockerfile
├── assembly-ui-test-docker-context.xml
├── pom.xml
├── test-module
│   ├── package.json
│   ├── index.js
│   └── wdio.conf.js
└── wait-for-grid.sh
```

Het `pom.xml` dossier behandelt de Maven bouwstijl. Voeg een uitvoering aan de Geweven Insteekmodule van de Assemblage toe gelijkend op het volgende.

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-assembly-plugin</artifactId>
    <configuration>
        <descriptors>
            <descriptor>${project.basedir}/assembly-ui-test-docker-context.xml</descriptor>
        </descriptors>
        <tarLongFileMode>gnu</tarLongFileMode>
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
```

Deze uitvoering instrueert de Geweven Insteekmodule van de Assemblage om een archief tot stand te brengen dat op de instructies in `assembly-ui-test-docker-context.xml` wordt gebaseerd, genoemd een &quot;assemblagebeschrijver&quot;in het jargon van de stop. De assemblagebeschrijver maakt een lijst van alle dossiers die deel van het archief moeten uitmaken.

```xml
<assembly>
    <id>ui-test-docker-context</id>
    <includeBaseDirectory>false</includeBaseDirectory>
    <formats>
        <format>tar.gz</format>
    </formats>
    <fileSets>
        <fileSet>
            <directory>${basedir}</directory>
            <includes>
                <include>Dockerfile</include>
                <include>wait-for-grid.sh</include>
            </includes>
        </fileSet>
        <fileSet>
            <directory>${basedir}/test-module</directory>
            <excludes>
                <exclude>node/**</exclude>
                <exclude>node_modules/**</exclude>
                <exclude>reports/**</exclude>
            </excludes>
        </fileSet>
    </fileSets>
</assembly>
```

De assemblagedescriptor geeft de plug-in de instructie een archief van het type `.tar.gz` te maken en wijst de `ui-test-docker-context`-classificator hieraan toe. Bovendien worden de bestanden weergegeven die in het archief moeten worden opgenomen:

- A `Dockerfile`, verplicht voor het bouwen van het beeld van de Dokker.
- Het `wait-for-grid.sh`-script, waarvan de doeleinden hieronder worden beschreven.
- De daadwerkelijke tests UI, die door een project Node.js in de `test-module` omslag worden uitgevoerd.

De assemblagebeschrijver sluit ook sommige dossiers uit die terwijl het runnen van de tests UI plaatselijk zouden kunnen worden geproduceerd. Dit garandeert een kleiner archief en snellere builds.

Het archief met de Docker-build-context wordt automatisch opgehaald door Cloud Manager, dat het Docker-image met uw tests zal maken tijdens de implementatiepijplijnen. Uiteindelijk voert Cloud Manager de Docker-afbeelding uit om de UI-tests op uw toepassing uit te voeren.

## Bezig met schrijven van UI-tests {#writing-ui-tests}

Deze sectie beschrijft de overeenkomsten die het beeld van de Docker dat uw tests UI bevat moet volgen. De Docker-afbeelding is gemaakt op basis van de constructiecontext van Docker die in de vorige sectie is beschreven.

### Omgevingsvariabelen {#environment-variables}

De volgende omgevingsvariabelen worden tijdens runtime aan de Docker-afbeelding doorgegeven.

| Variabele | Voorbeelden | Beschrijving |
|---|---|---|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | De URL van de seleniumserver |
| `SELENIUM_BROWSER` | `chrome`, `firefox` | De browserimplementatie die wordt gebruikt door de seleniumserver |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | De URL van de AEM instantie van de auteur |
| `AEM_AUTHOR_USERNAME` | `admin` | De gebruikersnaam voor aanmelding bij de AEM-instantie |
| `AEM_AUTHOR_PASSWORD` | `admin` | Het wachtwoord om zich aan te melden bij de instantie van de AEM auteur |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | De URL van de AEM-publicatie-instantie |
| `AEM_PUBLISH_USERNAME` | `admin` | De gebruikersnaam die moet worden gebruikt voor aanmelding bij de AEM-publicatie-instantie |
| `AEM_PUBLISH_PASSWORD` | `admin` | Het wachtwoord voor aanmelding bij de AEM-publicatie-instantie |
| `REPORTS_PATH` | `/usr/src/app/reports` | Het pad waar het XML-rapport van de testresultaten moet worden opgeslagen |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | De URL waarnaar het bestand moet worden geüpload om het toegankelijk te maken voor Selenium |

### Wachten tot Selenium gereed is {#waiting-for-selenium}

Alvorens de tests beginnen, is het de verantwoordelijkheid van het beeld van de Docker om ervoor te zorgen dat de server van Selenium in gebruik is. Wachten op de seleniumservice is een proces in twee stappen:

1. Lees URL van de dienst van Selenium van `SELENIUM_BASE_URL` milieuvariabele.
2. Opiniepeiling met regelmatige tussenpozen aan [status eindpunt](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) blootgesteld door Selenium API.

Zodra het statuseindpunt van Selenium met een positieve reactie beantwoordt, kunnen de tests eindelijk beginnen.

### Testrapporten genereren {#generate-test-reports}

De Docker-afbeelding moet testrapporten genereren in de XML-indeling JUnit en deze opslaan in het pad dat wordt aangegeven door de omgevingsvariabele `REPORTS_PATH`. De indeling JUnit XML is een wijdverbreide indeling voor het rapporteren van de resultaten van tests. Als de Docker-afbeelding gebruikmaakt van Java en Maven, zowel de [Maven Surefire-insteekmodule](https://maven.apache.org/surefire/maven-surefire-plugin/) als de [Maven Failsafe-insteekmodule](https://maven.apache.org/surefire/maven-failsafe-plugin/). Als het Docker-beeld samen met andere programmeertalen of testrunners wordt geïmplementeerd, controleert u de documentatie voor de gekozen hulpmiddelen om te weten hoe u JUnit-XML-rapporten kunt genereren.

### Bestanden uploaden (#upload-files)

Tests moeten soms bestanden uploaden naar de geteste toepassing. Om de implementatie van Selenium in verhouding tot uw tests flexibel te houden, is het niet mogelijk om een middel rechtstreeks naar Selenium te uploaden. In plaats daarvan voert het uploaden van een bestand een aantal tussenliggende stappen uit:

1. Upload het bestand naar de URL die door de omgevingsvariabele `UPLOAD_URL` is opgegeven. Het uploaden moet worden uitgevoerd in één verzoek van de POST met een meerdelige vorm. Het formulier met meerdere delen moet één bestandsveld hebben. Dit is gelijk aan `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`. Raadpleeg de documentatie en bibliotheken van de programmeertaal die in het beeld van de Docker wordt gebruikt om te weten hoe te om zulk een HTTP- verzoek uit te voeren.
2. Als de upload succesvol is, keert het verzoek een `200 OK` reactie van type `text/plain` terug. De inhoud van de reactie is een ondoorzichtige bestandshandgreep. U kunt deze greep gebruiken in plaats van een bestandspad in een `<input>`-element om het uploaden van bestanden in uw toepassing te testen.
