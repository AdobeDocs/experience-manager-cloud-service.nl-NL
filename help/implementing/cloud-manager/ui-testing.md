---
title: UI-tests
description: Het testen van de UI van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw douanetoepassingen tot stand te brengen en automatisch in werking te stellen
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
source-git-commit: 31e84b7383cd9774b0eaf8ee0f2fe39bcd77fa15
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 0%

---


# UI-tests {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="UI-tests"
>abstract="Het testen van de gebruikersinterface van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw toepassingen tot stand te brengen en automatisch in werking te stellen. De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om een brede keus in taal en kaders (zoals Java en Maven, Node en WebDriver.io, of om het even welk ander kader en technologie toe te staan die op Selenium worden voortgebouwd)."

Het testen van de gebruikersinterface van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw toepassingen tot stand te brengen en automatisch in werking te stellen.

## Overzicht {#custom-ui-testing}

AEM biedt een geïntegreerde suite [Kwaliteitspates van Cloud Manager](/help/implementing/cloud-manager/custom-code-quality-rules.md) voor vloeiende updates van aangepaste toepassingen. Met name wordt met de IT-test al begonnen met het maken en automatiseren van aangepaste tests met behulp van AEM API&#39;s.

De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om een brede keus in taal en kaders (zoals Java en Maven, Node en WebDriver.io, of om het even welk ander kader en technologie toe te staan die op Selenium worden voortgebouwd). Bovendien kan een UI testproject gemakkelijk door te gebruiken worden geproduceerd [het AEM Project Archetype.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)

UI-tests worden uitgevoerd als onderdeel van een specifieke kwaliteitspoort voor elke Cloud Manager-pijplijn met een [toegewijd **Aangepaste UI-tests** stap.](/help/implementing/cloud-manager/deploy-code.md) Om het even welke tests van de UI met inbegrip van regressie en nieuwe functionaliteiten laten fouten toe om worden ontdekt en worden gemeld.

In tegenstelling tot aangepaste functionele tests, die HTTP-tests zijn die in Java zijn geschreven, kunnen UI-tests een Docker-afbeelding zijn met tests die in elke taal zijn geschreven, mits ze de conventies volgen die in de sectie zijn gedefinieerd [UI-tests maken.](#building-ui-tests)

>[!TIP]
>
>Adobe raadt u aan de structuur en taal (JavaScript en WDIO) te volgen die in het dialoogvenster [AEM Projectarchetype.](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests)

### Klanten kiezen {#customer-opt-in}

Als u wilt dat de gebruikersinterfacetests worden uitgevoerd door Cloud Manager, moet u zich aanmelden voor deze functie door een bestand toe te voegen aan uw opslagplaats.

* De bestandsnaam moet `testing.properties`.
* De bestandsinhoud moet `ui-tests.version=1`.
* Het bestand moet zich onder de toegewezen submodule voor UI-tests bevinden naast de `pom.xml` dossier van UI test submodule.
* Het bestand moet de basis van de ingebouwde `tar.gz` bestand.

De UI-tests worden uitgevoerd en uitgevoerd als dit bestand niet aanwezig is.

Als u een `testing.properties` bestand in het constructieartefact toevoegen `include` in de `assembly-ui-test-docker-context.xml` bestand.

```xml
[...]
<includes>
    <include>Dockerfile</include>
    <include>wait-for-grid.sh</include>
    <include>testing.properties</include> <!-- opt-in test module in Cloud Manager -->
</includes>
[...]
```

>[!NOTE]
>
>Als uw project deze lijn niet omvat, zult u het dossier moeten uitgeven om in het testen UI te kiezen.
>
>Het bestand kan een regel bevatten die u adviseert het bestand niet te bewerken. Dit is toe te schrijven aan het worden geïntroduceerd in uw project alvorens het opt-in testen UI werd geïntroduceerd en de cliënt was niet bedoeld om het dossier uit te geven. Dit kan veilig worden genegeerd.

## UI-tests samenstellen {#building-ui-tests}

Een Maven project produceert een Docker bouwt context. In deze docker wordt de bouwcontext beschreven hoe u een Docker-afbeelding kunt maken die de UI-tests bevat en die gebruikers van Cloud Manager kunnen gebruiken om een Docker-afbeelding te genereren die de werkelijke UI-tests bevat.

In deze sectie worden de stappen beschreven die nodig zijn om een UI-testproject toe te voegen aan uw opslagplaats.

>[!TIP]
>
>De [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype) Kan een project van de Tests UI produceren voor u geen speciale vereisten voor de programmeertaal hebt.

### Een docker Build-context genereren {#generate-docker-build-context}

Om Docker te produceren bouwt context, hebt u een Gemaakt module nodig die:

* Hiermee wordt een archief gemaakt dat een `Dockerfile` en elk ander bestand dat nodig is om het Docker-image met uw tests te maken.
* Hiermee wordt het archief gecodeerd met het `ui-test-docker-context` classificator.

De eenvoudigste manier om dit te doen is de [Insteekmodule Maven Assembly](https://maven.apache.org/plugins/maven-assembly-plugin/) om Docker te creëren bouwt contextarchief en wijst het juiste classificator aan het toe.

U kunt tests UI met verschillende technologieën en kaders bouwen, maar deze sectie veronderstelt dat uw project op een manier gelijkend op het volgende wordt opgemaakt.

```text
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

Deze uitvoering instrueert de Geweven Insteekmodule van de Assemblage om een archief tot stand te brengen dat op de instructies in wordt gebaseerd `assembly-ui-test-docker-context.xml`, een **assemblagedescriptor** in het jargon van de plug-in. De assemblagebeschrijver maakt een lijst van alle dossiers die deel van het archief moeten uitmaken.

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

De assemblagebeschrijving geeft de plug-in de opdracht een archief van het type te maken `.tar.gz` en wijst de `ui-test-docker-context` classificator. Bovendien worden de bestanden weergegeven die in het archief moeten worden opgenomen, inclusief de volgende bestanden.

* A `Dockerfile`, verplicht voor het samenstellen van de Docker-afbeelding
* De `wait-for-grid.sh` script, waarvan de doeleinden hieronder worden beschreven
* De daadwerkelijke tests UI die door een project Node.js in worden uitgevoerd `test-module` map

De assemblagebeschrijver sluit ook sommige dossiers uit die terwijl het runnen van de tests UI plaatselijk zouden kunnen worden geproduceerd. Dit garandeert een kleiner archief en snellere builds.

Het archief met de Docker-build-context wordt automatisch opgehaald door Cloud Manager, dat het Docker-image met uw tests zal maken tijdens de implementatiepijplijnen. Uiteindelijk voert Cloud Manager de Docker-afbeelding uit om de UI-tests op uw toepassing uit te voeren.

De build moet nul of één archief produceren. Als het nul archieven produceert, gaat de teststap door gebrek over. Als de build meer dan één archief produceert, is het geselecteerde archief niet-deterministisch.

## Tests voor gebruikersinterface schrijven {#writing-ui-tests}

Deze sectie beschrijft de overeenkomsten die het beeld van de Docker dat uw tests UI bevat moet volgen. De Docker-afbeelding is gemaakt op basis van de constructiecontext van Docker die in de vorige sectie is beschreven.

### Omgevingsvariabelen {#environment-variables}

De volgende omgevingsvariabelen worden tijdens runtime aan de Docker-afbeelding doorgegeven.

| Variabele | Voorbeelden | Beschrijving |
|---|---|---|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | De URL van de seleniumserver |
| `SELENIUM_BROWSER` | `chrome` | De browserimplementatie die wordt gebruikt door de seleniumserver |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | De URL van de AEM instantie van de auteur |
| `AEM_AUTHOR_USERNAME` | `admin` | De gebruikersnaam die moet worden gebruikt om u aan te melden bij de instantie van de AEM auteur |
| `AEM_AUTHOR_PASSWORD` | `admin` | Het wachtwoord om zich aan te melden bij de instantie van de AEM auteur |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | De URL van de AEM-publicatie-instantie |
| `AEM_PUBLISH_USERNAME` | `admin` | De gebruikersnaam die moet worden gebruikt voor aanmelding bij de AEM-publicatie-instantie |
| `AEM_PUBLISH_PASSWORD` | `admin` | Het wachtwoord voor aanmelding bij de AEM-publicatie-instantie |
| `REPORTS_PATH` | `/usr/src/app/reports` | Het pad waar het XML-rapport van de testresultaten moet worden opgeslagen |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | De URL waarnaar het bestand moet worden geüpload om het toegankelijk te maken voor Selenium |

### Wachten op klaar voor selenium {#waiting-for-selenium}

Alvorens de tests beginnen, is het de verantwoordelijkheid van het beeld van de Docker om ervoor te zorgen dat de server van Selenium in gebruik is. Wachten op de seleniumservice is een proces in twee stappen.

1. Lees URL van de dienst van Selenium van de dienst `SELENIUM_BASE_URL` omgevingsvariabele.
1. Opiniepeiling met regelmatige tussenpozen tot de [statuseindpunt](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) door de Selenium-API worden weergegeven.

Zodra het statuseindpunt van Selenium met een positieve reactie beantwoordt, kunnen de tests beginnen.

### Testrapporten genereren {#generate-test-reports}

De Docker-afbeelding moet testrapporten genereren in de XML-indeling JUnit en deze opslaan in het pad dat is opgegeven door de omgevingsvariabele `REPORTS_PATH`. De indeling JUnit XML is een veelgebruikte indeling voor het rapporteren van de resultaten van tests. Als de Docker-afbeelding gebruikmaakt van Java en Maven, gebruikt u standaardtestmodules zoals [Maven Surefire-plug-in](https://maven.apache.org/surefire/maven-surefire-plugin/) en [Maven Failsafe-insteekmodule](https://maven.apache.org/surefire/maven-failsafe-plugin/) kan dergelijke rapporten uit de doos produceren.

Als het Docker-beeld samen met andere programmeertalen of testrunners wordt geïmplementeerd, controleert u de documentatie voor de gekozen hulpmiddelen op hoe u JUnit-XML-rapporten kunt genereren.

### Schermafbeeldingen en video&#39;s vastleggen {#capture-screenshots}

De Docker-afbeelding kan aanvullende testuitvoer genereren (bijvoorbeeld screenshots, video&#39;s) en deze opslaan in het pad dat wordt aangegeven door de omgevingsvariabele `REPORTS_PATH`. Alle bestanden gevonden onder de `REPORTS_PATH` worden opgenomen in het archief van de testresultaten.

Als een archief van het testresultaat tijdens een UI testuitvoering is gecreeerd, bevat het dossier van het testlogboek aan het eind een verwijzing naar de plaats van het archief van het testresultaat.

```
[...]

===============================================================
The detailed test results can be downloaded from the URL below.
Note: the link will expire after 60 days

    https://results-host/test-results.zip

===============================================================
```

### Bestanden uploaden {#upload-files}

Tests moeten soms bestanden uploaden naar de toepassing die wordt getest. Om de implementatie van Selenium flexibel te houden ten opzichte van uw tests, is het niet mogelijk om een middel rechtstreeks naar Selenium te uploaden. In plaats daarvan moet u de volgende stappen uitvoeren om een bestand te uploaden.

1. Upload het bestand naar de URL die door de `UPLOAD_URL` omgevingsvariabele.
   * Het uploaden moet worden uitgevoerd in één verzoek van de POST met een meerdelige vorm.
   * Het formulier met meerdere delen moet één bestandsveld hebben.
   * Dit is gelijk aan `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`.
   * Raadpleeg de documentatie en bibliotheken van de programmeertaal die in het beeld van de Docker wordt gebruikt om te weten hoe te om zulk een HTTP- verzoek uit te voeren.
1. Als het uploaden is gelukt, retourneert de aanvraag een `200 OK` reactie van het type `text/plain`.
   * De inhoud van de reactie is een ondoorzichtige bestandshandgreep.
   * U kunt deze greep gebruiken in plaats van een bestandspad in een `<input>` -element om het uploaden van bestanden in uw toepassing te testen.
