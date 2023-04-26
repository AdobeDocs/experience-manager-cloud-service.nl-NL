---
title: UI-tests
description: Het testen van de UI van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw douanetoepassingen tot stand te brengen en automatisch in werking te stellen
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
source-git-commit: 24796bd7d9c5e726cda13885bc4bd7e4155610dc
workflow-type: tm+mt
source-wordcount: '2238'
ht-degree: 0%

---


# UI-tests {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="UI-tests"
>abstract="Het testen van de gebruikersinterface van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw toepassingen tot stand te brengen en automatisch in werking te stellen. De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om een brede keus in taal en kaders (zoals Java en Maven, Node en WebDriver.io, of om het even welk ander kader en technologie toe te staan die op Selenium worden voortgebouwd)."

Het testen van de gebruikersinterface van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw toepassingen tot stand te brengen en automatisch in werking te stellen.

## Overzicht {#custom-ui-testing}

AEM biedt een geïntegreerde suite [Kwaliteitspates van Cloud Manager](/help/implementing/cloud-manager/custom-code-quality-rules.md) voor vloeiende updates van aangepaste toepassingen. Met name ondersteunen IT-testpoorten al het maken en automatiseren van aangepaste tests met behulp van AEM API&#39;s.

De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om een brede keus in taal en kaders (zoals Java en Maven, Node en WebDriver.io, of om het even welk ander kader en technologie toe te staan die op Selenium worden voortgebouwd). Bovendien, kan een UI testproject gemakkelijk door te gebruiken worden geproduceerd [het AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html).

UI-tests worden uitgevoerd als onderdeel van een specifieke kwaliteitspoort voor elke Cloud Manager-pijplijn met een [**Aangepaste UI-tests** stap](/help/implementing/cloud-manager/deploy-code.md) in [productiepijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) of optioneel [niet-productieleidingen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md). Om het even welke tests van de UI met inbegrip van regressie en nieuwe functionaliteiten laten fouten toe om worden ontdekt en worden gemeld.

In tegenstelling tot aangepaste functionele tests, die HTTP-tests zijn die in Java zijn geschreven, kunnen UI-tests een Docker-afbeelding zijn met tests die in elke taal zijn geschreven, mits ze de conventies volgen die in de sectie zijn gedefinieerd [UI-tests samenstellen](#building-ui-tests).

>[!TIP]
>
>Adobe raadt u aan de structuur en taal (JavaScript en WDIO) te volgen die in het dialoogvenster [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests).
>
>Adobe verstrekt ook een UI testmodulevoorbeeld dat op Java en WebDriver wordt gebaseerd. Raadpleeg de [AEM opslagplaats voor testmonsters](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver) voor meer informatie.

## Aan de slag met gebruikersinterfacetests {#get-started-ui-tests}

In deze sectie worden de stappen beschreven die zijn vereist voor het instellen van UI-tests voor uitvoering in Cloud Manager.

1. Bepaal de programmeertaal die u wilt gebruiken.

   * Gebruik voor JavaScript en WDIO de voorbeeldcode die automatisch wordt gegenereerd in het dialoogvenster `ui.tests` van uw opslagplaats voor Cloud Manager.

      >[!NOTE]
      >
      >Als uw opslagplaats is gemaakt voordat Cloud Manager automatisch is gemaakt `it.tests` mappen, kunt u ook de meest recente versie genereren met de [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/it.tests).

   * Gebruik voor Java en WebDriver de voorbeeldcode van het dialoogvenster [AEM opslagplaats voor testmonsters](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver).

   * Voor andere programmeertalen raadpleegt u de sectie [UI-tests samenstellen](#building-ui-tests) in dit document aan opstelling het testproject.

1. Zorg ervoor dat de UI-test wordt geactiveerd volgens de sectie [Klanten kiezen](#customer-opt-in) in dit document.

1. Ontwikkel uw testdoosjes en [ze lokaal uitvoeren](#run-ui-tests-locally).

1. Leg uw code vast in de gegevensopslagruimte van Cloud Manager en voer een pijplijn van Cloud Manager uit.

## UI-tests samenstellen {#building-ui-tests}

Een Maven project produceert een Docker bouwt context. In deze docker wordt de bouwcontext beschreven hoe u een Docker-afbeelding kunt maken die de UI-tests bevat en die door Cloud Manager wordt gebruikt om een Docker-afbeelding te genereren die de werkelijke UI-tests bevat.

In deze sectie worden de stappen beschreven die nodig zijn om een UI-testproject toe te voegen aan uw opslagplaats.

>[!TIP]
>
>De [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype) Kan een project van de Tests UI voor u produceren, dat aan de volgende beschrijving volgzaam is, als u geen speciale vereisten voor de programmeertaal hebt.

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

### Klanten kiezen {#customer-opt-in}

Als u wilt dat Cloud Manager uw UI-tests kan uitvoeren, moet u zich aanmelden voor deze functie door een bestand aan uw opslagplaats toe te voegen.

* De bestandsnaam moet `testing.properties`.
* De bestandsinhoud moet `ui-tests.version=1`.
* Het bestand moet zich onder de toegewezen submodule bevinden voor UI-tests naast de `pom.xml` dossier van UI test submodule.
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

Als u de voorbeelden gebruikt die door Adobe worden verstrekt:

* Voor het JavaScript-veld `ui.tests` op basis van de [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests), kunt u onder bevel uitvoeren om de vereiste configuratie toe te voegen.

   ```shell
   echo "ui-tests.version=1" > testing.properties
   
   if ! grep -q "testing.properties" "assembly-ui-test-docker-context.xml"; then
     awk -v line='                <include>testing.properties</include>' '/<include>wait-for-grid.sh<\/include>/ { printf "%s\n%s\n", $0, line; next }; 1' assembly-ui-test-docker-context.xml > assembly-ui-test-docker-context.xml.new && mv assembly-ui-test-docker-context.xml.new assembly-ui-test-docker-context.xml
   fi
   ```

* Voor de Java-testvoorbeelden die al worden aangeboden, is de markering voor aanmelden ingesteld.

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
| `AEM_AUTHOR_PASSWORD` | `admin` | Het wachtwoord om u aan te melden bij de AEM |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | De URL van de AEM-publicatie-instantie |
| `AEM_PUBLISH_USERNAME` | `admin` | De gebruikersnaam die moet worden gebruikt om u aan te melden bij de AEM-publicatie-instantie |
| `AEM_PUBLISH_PASSWORD` | `admin` | Het wachtwoord voor aanmelding bij de AEM-publicatie-instantie |
| `REPORTS_PATH` | `/usr/src/app/reports` | Het pad waar het XML-rapport van de testresultaten moet worden opgeslagen |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | De URL waarnaar het bestand moet worden geüpload om het toegankelijk te maken voor Selenium |

De Adobe testmonsters verstrekken helperfuncties om tot de configuratieparameters toegang te hebben:

* JavaScript: Zie de [lib/config.js](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/config.js) module
* Java: Zie de [Config](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Config.java) class

### Wachten op klaar voor selenium {#waiting-for-selenium}

Alvorens de tests beginnen, is het de verantwoordelijkheid van het beeld van de Docker om ervoor te zorgen dat de server van Selenium in gebruik is. Wachten op de seleniumservice is een proces in twee stappen.

1. Lees URL van de dienst van Selenium van de dienst `SELENIUM_BASE_URL` omgevingsvariabele.
1. Opiniepeiling met regelmatige tussenpozen tot de [statuseindpunt](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) door de Selenium-API worden weergegeven.

Zodra het statuseindpunt van Selenium met een positieve reactie beantwoordt, kunnen de tests beginnen.

De Adobe UI teststeekproeven behandelen dit met het manuscript `wait-for-grid.sh`, die wordt uitgevoerd bij het opstarten van Docker en de daadwerkelijke testuitvoering pas begint wanneer het net klaar is.

### Testrapporten genereren {#generate-test-reports}

De Docker-afbeelding moet testrapporten genereren in de XML-indeling JUnit en deze opslaan in het pad dat is opgegeven door de omgevingsvariabele `REPORTS_PATH`. De indeling JUnit XML is een veelgebruikte indeling voor het rapporteren van de resultaten van tests. Als de Docker-afbeelding gebruikmaakt van Java en Maven, gebruikt u standaardtestmodules zoals [Maven Surefire-plug-in](https://maven.apache.org/surefire/maven-surefire-plugin/) en [Maven Failsafe-insteekmodule](https://maven.apache.org/surefire/maven-failsafe-plugin/) kan dergelijke rapporten uit de doos produceren.

Als het Docker-beeld samen met andere programmeertalen of testrunners wordt geïmplementeerd, controleert u de documentatie voor de gekozen hulpmiddelen op hoe u JUnit-XML-rapporten kunt genereren.

>[!NOTE]
>
>Het resultaat van de teststap voor de gebruikersinterface wordt alleen op basis van de testrapporten geëvalueerd. Zorg ervoor dat u het rapport overeenkomstig voor de uitvoering van de test genereert.
>
>De beweringen van het gebruik in plaats van enkel het registreren van een fout aan STDERR of het terugkeren van een niet-nul uitgangscode anders kan uw plaatsingspijpleiding normaal te werk gaan.

### Schermafbeeldingen en video&#39;s vastleggen {#capture-screenshots}

De Docker-afbeelding kan aanvullende testuitvoer genereren (bijvoorbeeld screenshots of video&#39;s) en deze opslaan in het pad dat wordt aangegeven door de omgevingsvariabele `REPORTS_PATH`. Alle bestanden gevonden onder de `REPORTS_PATH` worden opgenomen in het archief van de testresultaten.

De teststeekproeven die door Adobe door gebrek worden verstrekt leiden tot schermafbeeldingen voor om het even welke ontbroken test.

U kunt de hulpfuncties gebruiken om schermafbeeldingen tot stand te brengen door uw tests.

* JavaScript: [takeScreenshot, opdracht](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/commons.js)
* Java: [Opdrachten](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Commands.java)

Als een archief met testresultaten wordt gemaakt tijdens een uitvoering van een UI-test, kunt u dit archief downloaden vanuit Cloud Manager met de opdracht `Download Details` onder de knop [**Aangepaste UI-tests** stap](/help/implementing/cloud-manager/deploy-code.md).

### Bestanden uploaden {#upload-files}

Tests moeten soms bestanden uploaden naar de toepassing die wordt getest. Om de implementatie van Selenium flexibel te houden ten opzichte van uw tests, is het niet mogelijk om een middel rechtstreeks naar Selenium te uploaden. In plaats daarvan moet u de volgende stappen uitvoeren om een bestand te uploaden.

1. Upload het bestand naar de URL die door de `UPLOAD_URL` omgevingsvariabele.
   * Het uploaden moet worden uitgevoerd in één verzoek van de POST met een meerdelige vorm.
   * Het formulier met meerdere delen moet één bestandsveld hebben.
   * Dit is gelijk aan `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`.
   * Raadpleeg de documentatie en bibliotheken van de programmeertaal die in het beeld van de Docker wordt gebruikt om te weten hoe te om zulk een HTTP- verzoek uit te voeren.
   * De monsters van de Adobe test verstrekken helperfuncties voor het uploaden van dossiers:
      * JavaScript: Zie de [getFileHandleForUpload](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/wdio.commands.js) gebruiken.
      * Java: Zie de [FileHandler](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/FileHandler.java) klasse.
1. Als het uploaden is gelukt, retourneert de aanvraag een `200 OK` reactie van het type `text/plain`.
   * De inhoud van de reactie is een ondoorzichtige bestandshandgreep.
   * U kunt deze greep gebruiken in plaats van een bestandspad in een `<input>` -element om het uploaden van bestanden in uw toepassing te testen.

### Vereisten {#prerequisites}

1. De tests in Cloud Manager worden uitgevoerd met een technische beheerder.

>[!NOTE]
>
>Voor het uitvoeren van de functionele tests van uw lokale computer, creeer een gebruiker met admin-als toestemmingen om het zelfde gedrag te bereiken.

1. De containerinfrastructuur die is bestemd voor functionele tests, wordt beperkt door de volgende grenzen:

| Type | Waarde | Beschrijving |
|----------------------|-------|--------------------------------------------------------------------|
| CPU | 2.0 | Hoeveelheid CPU-tijd gereserveerd per testuitvoering |
| Geheugen | 1Gi | Hoeveelheid geheugen dat aan de test is toegewezen, waarde in bytes |
| Time-out | 30m | De duur waarna de test wordt beëindigd. |
| Aanbevolen duur | 15m | Wij adviseren om de tests te schrijven om niet langer dan deze tijd te nemen. |

>[!NOTE]
>
> Indien u meer middelen nodig hebt, maak dan een geval voor de klantenservice en beschrijf uw gebruikscase. ons team zal uw verzoek beoordelen en passende hulp verlenen .


## UI-tests lokaal uitvoeren {#run-ui-tests-locally}

Alvorens tests UI in een pijpleiding van de Manager van de Wolk te activeren, adviseert het om de tests UI plaatselijk tegen te stellen [as a Cloud Service SDK AEM](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
of tegen een werkelijk AEM as a Cloud Service instantie.

### JavaScript-testvoorbeeld {#javascript-sample}

1. Open een shell en navigeer naar de `ui.tests` map in uw opslagplaats

1. Voer hieronder bevel uit om de tests te beginnen gebruikend Maven

   ```shell
   mvn verify -Pui-tests-local-execution \
   -DAEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
   -DAEM_AUTHOR_USERNAME=<user> \
   -DAEM_AUTHOR_PASSWORD=<password> \
   -DAEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
   -DAEM_PUBLISH_USERNAME=<user> \
   -DAEM_PUBLISH_PASSWORD=<password> \
   -DHEADLESS_BROWSER=true \
   -DSELENIUM_BROWSER=chrome
   ```

>[!NOTE]
>
>* Dit begint een standalone selenium instantie en voert de tests tegen het uit.
>* De logbestanden worden opgeslagen in het dialoogvenster `target/reports` map van uw opslagplaats
>* U moet ervoor zorgen dat de nieuwste Chrome-versie actief is wanneer de test de meest recente release van ChromeDriver automatisch downloadt voor tests.
>
>Zie voor meer informatie de [Opslagplaats voor projectarchetype AEM](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/README.md).

### Java Test Sample {#java-sample}

1. Open een shell en navigeer naar de `ui.tests/test-module` map in uw opslagplaats

1. Voer hieronder bevel uit om de tests te beginnen gebruikend Maven

   ```shell
   # Start selenium docker image (for x64 CPUs)
   docker run --platform linux/amd64 -d -p 4444:4444 selenium/standalone-chrome-debug:latest
   
   # Start selenium docker image (for ARM CPUs)
   docker run -d -p 4444:4444 seleniarm/standalone-chromium
   
   # Run the tests using the previously started Selenium instance
   mvn verify -Pui-tests-local-execution -DSELENIUM_BASE_URL=http://<server>:<port>
   ```

>[!NOTE]
>
>* De logbestanden worden opgeslagen in het dialoogvenster `target/reports` van uw opslagplaats.
>
>Zie voor meer informatie de [AEM opslagplaats voor testmonsters](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/README.md).
