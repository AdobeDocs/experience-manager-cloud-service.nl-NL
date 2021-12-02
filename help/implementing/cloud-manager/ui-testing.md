---
title: UI Testing - Cloud Services
description: UI Testing - Cloud Services
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
source-git-commit: 710f156e606902ab5548169661d4a82c8cf4f819
workflow-type: tm+mt
source-wordcount: '1616'
ht-degree: 0%

---

# UI-tests {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="UI-tests"
>abstract="De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om een brede keus in taal en kaders (zoals Java en Maven, Node en WebDriver.io, of om het even welk ander kader en technologie toe te staan die op Selenium worden voortgebouwd). De Docker-afbeelding kan met standaardgereedschappen worden gemaakt, maar tijdens de uitvoering ervan moet deze afbeelding bepaalde conventies respecteren. Bij het uitvoeren van de Docker-afbeelding wordt automatisch een Selenium-server ingericht. Met de onderstaande runtimeconventies heeft uw testcode toegang tot zowel de Selenium-server als de AEM die worden getest."

De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om een brede keus in taal en kaders (zoals Java en Maven, Node en WebDriver.io, of om het even welk ander kader en technologie toe te staan die op Selenium worden voortgebouwd). De Docker-afbeelding kan met standaardgereedschappen worden gemaakt, maar tijdens de uitvoering ervan moet deze afbeelding bepaalde conventies respecteren. Bij het uitvoeren van de Docker-afbeelding wordt automatisch een Selenium-server ingericht. Met de onderstaande runtimeconventies heeft uw testcode toegang tot zowel de Selenium-server als de AEM die worden getest.

>[!NOTE]
> Het werkgebied en de productiepijpleidingen die vóór 10 februari 2021 zijn gemaakt, moeten worden bijgewerkt om de interfacetests te kunnen gebruiken zoals beschreven op deze pagina.
> Zie [CI-CD-pijpleidingen in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) voor informatie over pijpleidingsconfiguratie.

## Aangepaste UI-tests {#custom-ui-testing}

AEM biedt zijn klanten een geïntegreerde suite met Cloud Manager-kwaliteitspoorten om ervoor te zorgen dat hun toepassingen probleemloos worden bijgewerkt. Met name kunnen klanten met behulp van IT-testpoorten al hun eigen tests maken en automatiseren die gebruikmaken van AEM API&#39;s.

De testfunctie voor aangepaste UI is een [optionele functie](#customer-opt-in) dat onze klanten toelaat om tests UI voor hun toepassingen tot stand te brengen en automatisch in werking te stellen. De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om een brede keus in taal en kaders (zoals Java en Maven, Node en WebDriver.io, of om het even welk ander kader en technologie toe te staan die op Selenium worden voortgebouwd). U kunt meer over leren hoe te om UI te bouwen en tests UI van hier te schrijven. Bovendien kan een project van de Tests UI gemakkelijk worden geproduceerd door het AEM Project Archetype te gebruiken.

De klanten kunnen (via GIT) douanetests en testreeks voor UI tot stand brengen. De UI-test wordt uitgevoerd als onderdeel van een specifieke kwaliteitspoort voor elke Cloud Manager-pijplijn met hun specifieke stap en feedbackinformatie. Om het even welke tests van de UI met inbegrip van regressie en nieuwe functionaliteiten, zullen fouten om toelaten worden ontdekt en worden gemeld binnen de klantencontext.

De tests van de UI van de Klant lopen automatisch op de pijpleiding van de Productie onder de &quot;Testen van de UI van de Douane&quot;stap.

In tegenstelling tot Aangepaste functionele tests die HTTP-tests zijn die in Java zijn geschreven, kunnen de UI-tests een dockerafbeelding zijn met tests die in elke taal zijn geschreven, mits deze de conventies volgen die zijn gedefinieerd op [UI-tests samenstellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/ui-testing.html?lang=en#building-ui-tests).

>[!NOTE]
>Aanbevolen wordt de structuur en de taal te volgen *(js en audio)* gemakkelijk in [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests) als uitgangspunt.

### Klanten kiezen {#customer-opt-in}

Om hun tests UI te hebben worden gebouwd en uitgevoerd, moeten de klanten &quot;opt-in&quot;door een dossier aan hun codebewaarplaats toe te voegen, onder de geproduceerde submodule voor tests UI (naast het pom.xml- dossier van UI test submodule) en ervoor te zorgen dat dit dossier bij de wortel van de gebouwde `tar.gz` bestand.

*Bestandsnaam*: `testing.properties`

*Inhoud*: `ui-tests.version=1`

Als dit niet in de ingebouwde `tar.gz` bestand, de UI-tests worden samengesteld en de uitvoeringen worden overgeslagen

Toevoegen `testing.properties` in het ingebouwde artefact, voeg een `include` instructie in `assembly-ui-test-docker-context.xml` bestand (in de submodule UI-tests).

>[!NOTE]
>Als uw project niet de lijn omvat, zult u dit dossier aan opt-in aan UI het testen moeten uitgeven. Als het dossier een lijn adviseert om niet uit te geven, te negeren gelieve dat advies.

    &quot;
    [...]
    &lt;includes>
    &lt;include>Dockerfile&lt;/include>
    &lt;include>wait-for-grid.sh&lt;/include>
    &lt;include>testing.properties&lt;/include> &lt;!>- testmodule voor aanmelden in Cloud Manager —>
    &lt;/includes>
    [...]
    &quot;

>[!NOTE]
>Productiepijpleidingen die vóór 10 februari 2021 zijn aangelegd, moeten worden bijgewerkt om de in dit punt beschreven interfacetests te kunnen gebruiken. Dit betekent hoofdzakelijk de Gebruiker de pijpleiding van de Productie moet uitgeven en klikt **Opslaan** van de BU, zelfs als er geen wijzigingen zijn aangebracht.
>Zie [Het vormen van uw CI-CD Pijpleiding](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager) om meer over pijpleidingsconfiguratie te leren.

## UI-tests samenstellen {#building-ui-tests}

De tests UI worden gebouwd uit een Docker bouwt context die door een Geweven project wordt geproduceerd. Cloud Manager gebruikt de Docker-ontwikkelcontext om een Docker-afbeelding te genereren die de werkelijke UI-tests bevat. Samengevat, produceert een Beweerd project een Docker bouwt context, en het Docker bouwt context beschrijft hoe te om een beeld van de Docker tot stand te brengen die de tests UI bevat.

Deze sectie gaat door de stappen nodig om een project van de Tests UI aan uw bewaarplaats toe te voegen. Als u haast hebt of geen speciale vereisten voor de programmeertaal hebt, kunt u de optie [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype) Kan een project van de Tests UI voor u produceren.

### Een Docker-constructiecontext genereren {#generate-docker-build-context}

Om Docker te produceren bouwt context, hebt u een Gemaakt module nodig die:

- Hiermee wordt een archief gemaakt dat een `Dockerfile` en elk ander bestand dat nodig is om het Docker-image met uw tests te maken.
- Hiermee wordt het archief gecodeerd met het `ui-test-docker-context` classificator.

De eenvoudigste manier om dit te bereiken is het vormen van [Insteekmodule Maven Assembly](http://maven.apache.org/plugins/maven-assembly-plugin/) om Docker te creëren bouwt contextarchief en wijst het juiste classificator aan het toe.

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

De `pom.xml` Het bestand verzorgt de Maven-build. Voeg een uitvoering aan de Geweven Insteekmodule van de Assemblage toe gelijkend op het volgende.

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

Deze uitvoering instrueert de Geweven Insteekmodule van de Assemblage om een archief tot stand te brengen dat op de instructies in wordt gebaseerd `assembly-ui-test-docker-context.xml`, een zogenaamde &#39;assemblagedescriptor&#39; in het jargon van de plug-in. De assemblagebeschrijver maakt een lijst van alle dossiers die deel van het archief moeten uitmaken.

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

De assemblagebeschrijving geeft de plug-in de opdracht een archief van het type te maken `.tar.gz` en wijst de `ui-test-docker-context` classificator. Bovendien worden de bestanden weergegeven die in het archief moeten worden opgenomen:

- A `Dockerfile`, verplicht voor het samenstellen van de Docker-afbeelding.
- De `wait-for-grid.sh` script, waarvan de doeleinden hieronder worden beschreven.
- De daadwerkelijke tests UI die door een project Node.js in worden uitgevoerd `test-module` map.

De assemblagebeschrijver sluit ook sommige dossiers uit die terwijl het runnen van de tests UI plaatselijk zouden kunnen worden geproduceerd. Dit garandeert een kleiner archief en snellere builds.

Het archief met de Docker-build-context wordt automatisch opgehaald door Cloud Manager, dat het Docker-image met uw tests zal maken tijdens de implementatiepijplijnen. Uiteindelijk voert Cloud Manager de Docker-afbeelding uit om de UI-tests op uw toepassing uit te voeren.

De build moet nul of één archief produceren. Als het nul archief produceert, gaat de teststap standaard over. Als de build meer dan één archief produceert, is het geselecteerde archief niet-deterministisch.

## Tests voor gebruikersinterface schrijven {#writing-ui-tests}

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

### Wachten tot Selenium klaar is {#waiting-for-selenium}

Alvorens de tests beginnen, is het de verantwoordelijkheid van het beeld van de Docker om ervoor te zorgen dat de server van Selenium in gebruik is. Wachten op de seleniumservice is een proces in twee stappen:

1. Lees URL van de dienst van Selenium van de dienst `SELENIUM_BASE_URL` omgevingsvariabele.
2. Opiniepeiling met regelmatige tussenpozen tot de [statuseindpunt](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) door de Selenium-API worden weergegeven.

Zodra het statuseindpunt van Selenium met een positieve reactie beantwoordt, kunnen de tests eindelijk beginnen.

### De testrapporten genereren {#generate-test-reports}

De Docker-afbeelding moet testrapporten genereren in de XML-indeling JUnit en deze opslaan in het pad dat is opgegeven door de omgevingsvariabele `REPORTS_PATH`. De indeling JUnit XML is een wijdverbreide indeling voor het rapporteren van de resultaten van tests. Als de Docker-afbeelding gebruikmaakt van Java en Maven, wordt zowel het [Maven Surefire-plug-in](https://maven.apache.org/surefire/maven-surefire-plugin/) en de [Maven Failsafe-insteekmodule](https://maven.apache.org/surefire/maven-failsafe-plugin/). Als het Docker-beeld samen met andere programmeertalen of testrunners wordt geïmplementeerd, controleert u de documentatie voor de gekozen hulpmiddelen om te weten hoe u JUnit-XML-rapporten kunt genereren.

### Bestanden uploaden {#upload-files}

Tests moeten soms bestanden uploaden naar de geteste toepassing. Om de implementatie van Selenium in verhouding tot uw tests flexibel te houden, is het niet mogelijk om een middel rechtstreeks naar Selenium te uploaden. In plaats daarvan voert het uploaden van een bestand een aantal tussenliggende stappen uit:

1. Upload het bestand naar de URL die door de `UPLOAD_URL` omgevingsvariabele. Het uploaden moet worden uitgevoerd in één verzoek van de POST met een meerdelige vorm. Het formulier met meerdere delen moet één bestandsveld hebben. Dit is gelijk aan `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`. Raadpleeg de documentatie en bibliotheken van de programmeertaal die in het beeld van de Docker wordt gebruikt om te weten hoe te om zulk een HTTP- verzoek uit te voeren.
2. Als het uploaden is gelukt, retourneert de aanvraag een `200 OK` reactie van het type `text/plain`. De inhoud van de reactie is een ondoorzichtige bestandshandgreep. U kunt deze greep gebruiken in plaats van een bestandspad in een `<input>` -element om het uploaden van bestanden in uw toepassing te testen.
