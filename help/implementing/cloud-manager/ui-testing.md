---
title: UI-tests
description: Het testen van de UI van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw douanetoepassingen tot stand te brengen en automatisch in werking te stellen
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 7d86ec9cd7cc283082da44111ad897a5aa548f58
workflow-type: tm+mt
source-wordcount: '2664'
ht-degree: 0%

---


# UI-tests {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="UI-tests"
>abstract="Het testen UI van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw toepassingen tot stand te brengen en automatisch in werking te stellen. De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om een brede keus in taal en kaders toe te staan. Zoals Java en Maven, Node en WebDriver.io of een ander framework en technologie die op Selenium zijn gebaseerd."

Het testen UI van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw toepassingen tot stand te brengen en automatisch in werking te stellen.

## Overzicht {#custom-ui-testing}

AEM verstrekt een geïntegreerde reeks van [&#x200B; de kwaliteitsgates van Cloud Manager &#x200B;](/help/implementing/cloud-manager/custom-code-quality-rules.md) om vlotte updates aan douanetoepassingen te verzekeren. Met name de testpoorten van IT ondersteunen al het maken en automatiseren van aangepaste tests met AEM API&#39;s.

De tests UI worden verpakt in een beeld van de Docker om een brede keus in taal en kaders (zoals Cypress, Selenium, Java en Maven, en JavaScript) toe te staan. Ook, kan een UI testproject gemakkelijk worden geproduceerd door [&#x200B; het Archetype van het Project van AEM &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/developing/archetype/overview) te gebruiken.

Adobe moedigt het gebruik van Cypress aan, aangezien het in real time herladen en automatisch wachten aanbiedt, die helpt tijd te besparen en productiviteit tijdens het testen verbetert. Cypress biedt ook een eenvoudige en intuïtieve syntaxis, waardoor het gemakkelijk is om te leren en te gebruiken, zelfs voor gebruikers die nog niet aan tests hebben gewerkt.

De tests van UI lopen als kwaliteitsgate in het [**Testen van de Douane UI**](/help/implementing/cloud-manager/deploy-code.md) stap-vereist in [&#x200B; productiepijpleidingen &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md), facultatief in [&#x200B; niet-productiepijpleidingen &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md). Om het even welke tests van de UI met inbegrip van regressie en nieuwe functionaliteiten toelaten om fouten te ontdekken en te melden.

In tegenstelling tot aangepaste functionele tests, die HTTP-tests zijn die in Java zijn geschreven, kunnen UI-tests een Docker-afbeelding zijn. De tests kunnen in om het even welke taal worden geschreven, zolang zij de overeenkomsten volgen die in de sectie [&#x200B; worden bepaald de Tests van de Bouw UI &#x200B;](#building-ui-tests).

>[!TIP]
>
>Adobe adviseert gebruikend Cypress voor het testen UI, na de code die in de [&#x200B; bewaarplaats van de Steekproeven van AEM wordt verstrekt &#x200B;](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-cypress).
> 
>Adobe verstrekt ook UI-testmodulevoorbeelden op basis van JavaScript met WebdriverIO (zie [&#x200B; Archetype van het Project van AEM &#x200B;](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests)) en Java met WebDriver (zie [&#x200B; de bewaarplaats van de Steekproeven van AEM &#x200B;](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver)).

## Aan de slag met UI-tests {#get-started-ui-tests}

In deze sectie worden de stappen beschreven die zijn vereist voor het instellen van UI-tests voor uitvoering in Cloud Manager.

1. Bepaal het testframework dat u wilt gebruiken.

   * Voor Cypress (gebrek), gebruik de steekproefcode van de [&#x200B; bewaarplaats van de Steekproeven van de Test van AEM &#x200B;](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-cypress) of gebruik de steekproefcode die automatisch in de `ui.tests` omslag van uw bewaarplaats van Cloud Manager wordt geproduceerd.

   * Voor Playwright, gebruik de steekproefcode van de [&#x200B; bewaarplaats van de Steekproeven van de Test van AEM &#x200B;](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-playwright).

   * Voor Webdriver.IO, gebruik de steekproefcode van de [&#x200B; bewaarplaats van de Steekproeven van de Test van AEM &#x200B;](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-wdio).

   * Voor Selenium WebDriver, gebruik de steekproefcode van de [&#x200B; bewaarplaats van de Steekproeven van de Test van AEM &#x200B;](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver).

   * Voor andere programmeertalen, zie de sectie [&#x200B; Tests van de Bouw UI &#x200B;](#building-ui-tests) in dit document aan opstelling het testproject.

1. Zorg ervoor dat het testen UI zoals per de sectie [&#x200B; verkiesbare Klant &#x200B;](#customer-opt-in) in dit document wordt geactiveerd.

1. Ontwikkel uw testgevallen en [&#x200B; stel de tests plaatselijk &#x200B;](#run-ui-tests-locally) in werking.

1. Leg uw code vast in de Cloud Manager-opslagplaats en voer een Cloud Manager-pijplijn uit.

## UI-tests samenstellen {#building-ui-tests}

Een Maven project produceert een Docker bouwt context. In deze docker wordt de bouwcontext beschreven hoe u een Docker-afbeelding kunt maken die de UI-tests bevat en die door Cloud Manager wordt gebruikt om een Docker-afbeelding te genereren die de werkelijke UI-tests bevat.

In deze sectie worden de stappen beschreven die nodig zijn om een UI-testproject toe te voegen aan uw opslagplaats.

>[!TIP]
>
>Het [&#x200B; Archetype van het Project van AEM &#x200B;](https://github.com/adobe/aem-project-archetype) kan een project van de Tests UI voor u produceren, dat aan de volgende beschrijving volgzaam is, als u geen speciale vereisten voor de programmeertaal hebt.

### Een Docker-constructiecontext genereren {#generate-docker-build-context}

Om Docker te produceren bouwt context, hebt u een Gemaakt module nodig die:

* Produceert een archief dat een `Dockerfile` en elk ander dossier noodzakelijk bevat om het beeld van de Docker met uw tests te bouwen.
* Hiermee wordt het archief gecodeerd met de classificator `ui-test-docker-context` .

De eenvoudigste manier is de [&#x200B; Gemaakt Insteekmodule van de Assemblage te vormen &#x200B;](https://maven.apache.org/plugins/maven-assembly-plugin/) om het Docker te creëren bouwt contextarchief en wijst het juiste classificatiebureau aan het toe.

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

Het bestand `pom.xml` verzorgt de Maven-build. Voeg een uitvoering aan de Geweven Insteekmodule van de Assemblage toe gelijkend op het volgende.

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

Deze uitvoering instrueert de Geweven Insteekmodule van de Assemblage om een archief tot stand te brengen dat op de instructies in `assembly-ui-test-docker-context.xml` wordt gebaseerd, genoemd een **assemblagebeschrijver** in het jargon van de insteekmodule. De assemblagebeschrijver maakt een lijst van alle dossiers die deel van het archief moeten uitmaken.

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

De assemblagedescriptor geeft de plug-in de instructie een archief van het type `.tar.gz` te maken en wijst er de classificator `ui-test-docker-context` aan toe. Bovendien worden de bestanden weergegeven die in het archief moeten worden opgenomen, waaronder:

* A `Dockerfile`, verplicht voor het samenstellen van de Docker-afbeelding
* Het script `wait-for-grid.sh` , waarvan de doeleinden hieronder worden beschreven
* De daadwerkelijke tests UI, die door een project Node.js in de `test-module` omslag worden uitgevoerd

De assemblagebeschrijver sluit ook sommige dossiers uit die terwijl het runnen van de tests UI plaatselijk zouden kunnen worden geproduceerd. Dit garandeert een kleiner archief en snellere builds.

Cloud Manager neemt automatisch het Docker build-context archive op en bouwt het testbeeld tijdens plaatsingspijpleidingen. Uiteindelijk voert Cloud Manager de Docker-afbeelding uit om de UI-tests op uw toepassing uit te voeren.

De build moet nul of één archief produceren. Als het nul archieven produceert, gaat de teststap door gebrek over. Als de build meer dan één archief produceert, is het geselecteerde archief niet-deterministisch.

### Aanmelden bij klant {#customer-opt-in}

Cloud Manager kan uw UI-tests alleen uitvoeren als u zich aanmeldt voor deze functie door een bestand aan uw opslagplaats toe te voegen.

* De bestandsnaam moet `testing.properties` zijn.
* De bestandsinhoud moet `ui-tests.version=1` zijn.
* Het bestand moet zich onder de toegewezen submodule bevinden voor UI-tests naast het `pom.xml` -bestand van de submodule UI-tests.
* Het bestand moet de basis van het samengestelde `tar.gz` bestand zijn.

De UI-tests worden uitgevoerd en uitgevoerd als dit bestand niet aanwezig is.

Als u een `testing.properties` -bestand wilt opnemen in het constructieartefact, voegt u een `include` -instructie toe in het `assembly-ui-test-docker-context.xml` -bestand.

```xml
[...]
<includes>
    <include>Dockerfile</include>
    <include>wait-for-grid.sh</include>
    <include>testing.properties</include> <!-- opt-in test module in Cloud Manager -->
</includes>
[...]
```

>[!IMPORTANT]
>
>Als uw project deze lijn niet omvat, geef het dossier uit om in het testen UI te kiezen.
>
>Het dossier kan een lijn bevatten die zegt, *WIJZIGT NIET*.&quot; Het is eenvoudig een erfeniswaarschuwing van oudere malplaatjes/steekproeven en *niet* blokkeert u van het maken van opt-in uitgeeft die voor het testen van UI van Cloud Manager wordt vereist. U kunt het advies veilig negeren. Namelijk kunt u `assembly-ui-test-docker-context.xml` en `pom.xml` in *uw project* uitgeven wanneer het volgen van opt-in stappen (bijvoorbeeld, om `testing.properties` te omvatten).

Als u de voorbeelden gebruikt die door Adobe worden geleverd:

* Voor op JavaScript-Gebaseerde `ui.tests` omslag die van het [&#x200B; wordt geproduceerd Archetype van het Project van AEM &#x200B;](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests), kunt u onder bevel uitvoeren om de vereiste configuratie toe te voegen.

  ```shell
  echo "ui-tests.version=1" > testing.properties
  
  if ! grep -q "testing.properties" "assembly-ui-test-docker-context.xml"; then
    awk -v line='                <include>testing.properties</include>' '/<include>wait-for-grid.sh<\/include>/ { printf "%s\n%s\n", $0, line; next }; 1' assembly-ui-test-docker-context.xml > assembly-ui-test-docker-context.xml.new && mv assembly-ui-test-docker-context.xml.new assembly-ui-test-docker-context.xml
  fi
  ```

* De door Adobe geleverde testmonsters voor Cypress en Java Selenium hebben al de markering opt-in ingesteld.

## UI-tests schrijven {#writing-ui-tests}

Deze sectie beschrijft de overeenkomsten die het beeld van de Docker dat uw tests UI bevat moet volgen. De Docker-afbeelding is gemaakt op basis van de constructiecontext van Docker die in de vorige sectie is beschreven.

### Omgevingsvariabelen {#environment-variables}

De volgende omgevingsvariabelen worden bij uitvoering aan de Docker-afbeelding doorgegeven, afhankelijk van uw framework.

>[!NOTE]
>
> Deze waarden worden automatisch geplaatst tijdens pijpleidingsuitvoering; er is geen behoefte om hen manueel als pijpleidingsvariabelen te plaatsen.

| Variabele | Voorbeelden | Beschrijving | Testframework |
|----------------------------|----------------------------------|----------------------------------------------------------------------------------------------------|---------------------|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | URL van de seleniumserver | Alleen selenium |
| `SELENIUM_BROWSER` | `chrome` | Browserimplementatie gebruikt door de seleniumserver | Alleen selenium |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | URL van de AEM-instantie Auteur | Alles |
| `AEM_AUTHOR_USERNAME` | `admin` | Gebruikersnaam voor aanmelding bij de AEM-auteurinstantie | Alles |
| `AEM_AUTHOR_PASSWORD` | `admin` | Wachtwoord voor aanmelding bij de AEM-instantie van auteur | Alles |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | URL van de instantie AEM Publishing | Alle * |
| `AEM_PUBLISH_USERNAME` | `admin` | Gebruikersnaam voor aanmelding bij AEM-publicatie-instantie | Alle * |
| `AEM_PUBLISH_PASSWORD` | `admin` | Wachtwoord voor aanmelding bij de AEM-publicatie-instantie | Alle * |
| `REPORTS_PATH` | `/usr/src/app/reports` | Pad waarin het XML-rapport van de testresultaten moet worden opgeslagen | Alles |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | URL waarnaar het bestand moet worden geüpload om het toegankelijk te maken voor het testframework | Alles |
| `PROXY_HOST` | `proxy-host` | Hostnaam van de interne HTTP-proxy die moet worden gebruikt door het testframework | Alles behalve selenium |
| `PROXY_HTTPS_PORT` | `8071` | Luisterpoort naar proxyserver voor HTTPS-verbindingen (kan leeg zijn) | Alles behalve selenium |
| `PROXY_HTTP_PORT` | `8070` | De luisterpoort van de proxyserver voor HTTP-verbindingen (kan leeg zijn) | Alles behalve selenium |
| `PROXY_CA_PATH` | `/path/to/root_ca.pem` | Pad naar het CA-certificaat dat door het testkader moet worden gebruikt | Alles behalve selenium |
| `PROXY_OBSERVABILITY_PORT` | `8081` | HTTP-poort `healthcheck` van de proxyserver | Alles behalve selenium |
| `PROXY_RETRY_ATTEMPTS` | `12` | Voorgesteld aantal pogingen opnieuw proberen tijdens wachten op gereedheid van proxyserver | Alles behalve selenium |
| `PROXY_RETRY_DELAY` | `5` | Voorgestelde vertraging tussen pogingen opnieuw proberen terwijl het wachten op de gereedheid van de volmachtsserver | Alles behalve selenium |

`* these values will be empty if there is no publish instance`

De Adobe-testmonsters bieden hulpfuncties voor toegang tot de configuratieparameters:

Cypress: de standaardfunctie gebruiken `Cypress.env('VARIABLE_NAME')`
<!-- BOTH URLs are 404 JavaScript: See the [`lib/config.js`](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests.wdio/test-module/lib/config.js) module
* Java: See the [`Config`](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Config.java) class -->

### Testrapporten genereren {#generate-test-reports}

De Docker-afbeelding moet testrapporten genereren in de XML-indeling JUnit en deze opslaan in het pad dat is opgegeven door de omgevingsvariabele `REPORTS_PATH` . De indeling JUnit XML is een veelgebruikte indeling voor het rapporteren van de resultaten van tests. Als het beeld van de Docker Java en Geweven gebruikt, kunnen de standaardtestmodules zoals [&#x200B; Gemaakte Steven Stevige Insteekmodule &#x200B;](https://maven.apache.org/surefire/maven-surefire-plugin/) en [&#x200B; Geweven Insteekmodule Failsafe &#x200B;](https://maven.apache.org/surefire/maven-failsafe-plugin/) dergelijke rapporten uit de doos produceren.

Als het Docker-beeld samen met andere programmeertalen of testrunners wordt geïmplementeerd, controleert u de documentatie voor de gekozen hulpmiddelen op hoe u JUnit-XML-rapporten kunt genereren.

>[!NOTE]
>
>Het resultaat van de teststap voor de gebruikersinterface wordt alleen op basis van de testrapporten geëvalueerd. Zorg ervoor dat u het rapport dienovereenkomstig voor uw testuitvoering produceert.
>
>De beweringen van het gebruik in plaats van enkel het registreren van een fout aan STDERR of het terugkeren van een niet-nul uitgangscode anders kan uw plaatsingspijpleiding normaal te werk gaan.
>
>Als een HTTP-proxy is gebruikt tijdens de uitvoering van tests, bevatten de resultaten een `request.log` -bestand.

### Vereisten {#prerequisites}

* De tests in Cloud Manager worden uitgevoerd met een technische admin-gebruiker.

>[!NOTE]
>
>Voor het uitvoeren van de functionele tests van uw lokale computer, creeer een gebruiker met admin-als toestemmingen om het zelfde gedrag te bereiken.

* De containerinfrastructuur die is bestemd voor functionele tests, wordt beperkt door de volgende grenzen:

| Type | Waarde | Beschrijving |
|----------------------|-------|-----------------------------------------------------------------------|
| CPU | 2,0 | Hoeveelheid CPU-tijd gereserveerd per uitgevoerde test. |
| Geheugen | 1 GB | De hoeveelheid geheugen die aan de test wordt toegewezen. Waarde is in bytes. |
| Time-out | 30 m | Hoe lang de test loopt. |
| Aanbevolen duur | 15 m | Adobe beveelt aan dat de tests binnen deze termijn worden gehouden. |

* Als het doel Auteur/publiceer door IP voegend op lijst van gewenste personen wordt beschermd, moet de de testinfrastructuur van de pijpleiding UI worden gevoegd op lijst van gewenste personen of de tests UI kunnen met 403 Verboden ontbreken.
Zie ook [&#x200B; UI testmislukking in AEMaaCS toe te schrijven aan IP Voegend op lijst van gewenste personen &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-26654#) en [&#x200B; Inleiding aan IP Lijsten van gewenste personen &#x200B;](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

>[!NOTE]
>
> Als u meer middelen nodig hebt, maakt u een kwestie voor de klantenservice en beschrijft u uw gebruikscase. Adobe beoordeelt uw verzoek en biedt de juiste hulp.

## Seleniumspecifieke details

>[!NOTE]
>
>Dit punt is alleen van toepassing wanneer Selenium de gekozen testinfrastructuur is.

### Wacht tot Selenium klaar is {#waiting-for-selenium}

Alvorens de tests beginnen, is het de verantwoordelijkheid van het beeld van de Docker om ervoor te zorgen dat de server van Selenium in gebruik is. Wachten op de seleniumservice is een proces in twee stappen.

1. Lees URL van de dienst van Selenium van de `SELENIUM_BASE_URL` omgevingsvariabele.
1. Opiniepeiling bij regelmatige intervallen aan het [&#x200B; statuseindpunt &#x200B;](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) dat door Selenium API wordt blootgesteld.

Zodra het statuseindpunt van Selenium met een positieve reactie beantwoordt, kunnen de tests beginnen.

Voor Adobe UI-testvoorbeelden wordt `wait-for-grid.sh` gebruikt. Het loopt bij het begin van de Dokker en lanceert tests slechts nadat het net klaar is.


### Schermafbeeldingen en video&#39;s vastleggen {#capture-screenshots}

De Docker-afbeelding kan aanvullende testuitvoer genereren (bijvoorbeeld schermafbeeldingen of video&#39;s) en deze opslaan in het pad dat wordt aangegeven door de omgevingsvariabele `REPORTS_PATH` . Alle bestanden die onder `REPORTS_PATH` worden gevonden, worden opgenomen in het archief met testresultaten.

Met de testvoorbeelden die standaard door Adobe worden geleverd, maakt u schermafbeeldingen voor elke mislukte test.

U kunt de hulpfuncties gebruiken om schermafbeeldingen tot stand te brengen door uw tests.

<!-- BOTH URLS ARE 404
* JavaScript: [takeScreenshot command](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/commons.js)
* Java: [Commands](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Commands.java) -->

Als een archief van het testresultaat tijdens een UI testuitvoering wordt gecreeerd, kunt u het van Cloud Manager downloaden door de `Download Details` knoop onder de [**het Testen van de Douane UI** stap &#x200B;](/help/implementing/cloud-manager/deploy-code.md) te klikken.

### Bestanden uploaden {#upload-files}

Tests moeten soms bestanden uploaden naar de toepassing die wordt getest. Om de implementatie van Selenium flexibel te houden ten opzichte van uw tests, is het niet mogelijk om een middel rechtstreeks naar Selenium te uploaden. In plaats daarvan moet u de volgende stappen uitvoeren om een bestand te uploaden.

1. Upload het bestand naar de URL die door de omgevingsvariabele `UPLOAD_URL` wordt opgegeven.
   * Het uploaden moet worden uitgevoerd in één POST-aanvraag met een meerdelige vorm.
   * Het formulier met meerdere delen moet één bestandsveld hebben.
   * Gelijk aan `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"`.
   * Raadpleeg de documentatie en bibliotheken van de programmeertaal die in het beeld van de Docker wordt gebruikt om te weten hoe te om zulk een HTTP- verzoek uit te voeren.

   <!-- BOTH URLS ARE 404
   * The Adobe test samples provide helper functions for uploading files:
     * JavaScript: See the [getFileHandleForUpload](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/wdio.commands.js) command.
     * Java: See the [FileHandler](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/FileHandler.java) class. -->

1. Als het uploaden is voltooid, retourneert de aanvraag een `200 OK` reactie van het type `text/plain` .
   * De inhoud van de reactie is een ondoorzichtige bestandshandgreep.
   * U kunt deze greep gebruiken in plaats van een bestandspad in een `<input>` -element om het uploaden van bestanden in uw toepassing te testen.

## Cypersspecifieke details

>[!NOTE]
>
>Deze sectie is alleen van toepassing wanneer Cypress de gekozen testinfrastructuur is.

### HTTP-proxy instellen

Het ingangspunt van de Docker-container moet de waarde van de omgevingsvariabele `PROXY_HOST` controleren.

Als deze waarde leeg is, zijn geen extra stappen vereist en de tests zouden zonder een volmacht van HTTP moeten worden uitgevoerd.

Als het niet leeg is, moet het entryPoint manuscript:

1. Configureer een HTTP-proxyverbinding voor het uitvoeren van UI-tests door de omgevingsvariabele `HTTP_PROXY` te exporteren die met de volgende waarden is samengesteld:
   * Proxyhost, die wordt geleverd door `PROXY_HOST` variable
   * Proxypoort, die wordt opgegeven door `PROXY_HTTPS_PORT` of `PROXY_HTTP_PORT` variable (de variabele met een niet-lege waarde wordt gebruikt)
2. Stel het CA-certificaat in dat wordt gebruikt wanneer u verbinding maakt met de HTTP-proxy. De locatie wordt opgegeven door de variabele `PROXY_CA_PATH` .
   * Omgevingsvariabele `NODE_EXTRA_CA_CERTS` exporteren.
3. Wacht tot de HTTP-proxy gereed is.
   * U kunt de gereedheid controleren door de omgevingsvariabelen `PROXY_HOST` , `PROXY_OBSERVABILITY_PORT` , `PROXY_RETRY_ATTEMPTS` en `PROXY_RETRY_DELAY` te gebruiken.
   * U kunt controleren met een cURL-aanvraag. Controleer of u cURL hebt geïnstalleerd in uw `Dockerfile` .

Een voorbeeldimplementatie kan in het Centrum van de Test van de Steekproef van de Cypress van de Module op [&#x200B; GitHub &#x200B;](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-cypress/test-module/run.sh) worden gevonden.

## Specifieke gegevens voor afspelen

>[!NOTE]
>
> Deze sectie is alleen van toepassing wanneer `Playwright` de gekozen testinfrastructuur is.

### HTTP-proxy instellen

>[!NOTE]
>
> In de gepresenteerde voorbeelden gaat Adobe ervan uit dat Chrome wordt gebruikt als een projectbrowser.

Net als bij Cypress moeten tests de HTTP-proxy gebruiken als een niet-lege `PROXY_HOST` omgevingsvariabele wordt opgegeven.

In dat geval moeten de volgende wijzigingen worden aangebracht.

#### Dockerfile

Installeer cURL en `libnss3-tools` met `certutil.`

```dockerfile
RUN apt -y update \
    && apt -y --no-install-recommends install curl libnss3-tools \
    && rm -rf /var/lib/apt/lists/*
```

#### EnterPoint-script

Neem een basscript op dat, voor het geval `PROXY_HOST` environment variable wordt gegeven, het volgende doet:

1. Aan proxy gerelateerde variabelen exporteren, zoals `HTTP_PROXY` en `NODE_EXTRA_CA_CERTS`
2. Gebruik `certutil` om CA-proxycertificaat voor Chromium™ te installeren.
3. Wacht tot de volmacht van HTTP klaar is (of weg bij mislukking).

Voorbeeldimplementatie:

```bash
# setup proxy environment variables and CA certificate
if [ -n "${PROXY_HOST:-}" ]; then
  if [ -n "${PROXY_HTTPS_PORT:-}" ]; then
    export HTTP_PROXY="https://${PROXY_HOST}:${PROXY_HTTPS_PORT}"
  elif [ -n "${PROXY_HTTP_PORT:-}" ]; then
    export HTTP_PROXY="http://${PROXY_HOST}:${PROXY_HTTP_PORT}"
  fi
  if [ -n "${PROXY_CA_PATH:-}" ]; then
    echo "installing certificate"
    mkdir -p $HOME/.pki/nssdb
    certutil -d sql:$HOME/.pki/nssdb -A -t "CT,c,c" -n "EaaS Client Proxy Root" -i $PROXY_CA_PATH
    export NODE_EXTRA_CA_CERTS=${PROXY_CA_PATH}
  fi
  if [ -n "${PROXY_OBSERVABILITY_PORT:-}" ] && [ -n "${HTTP_PROXY:-}" ]; then
    echo "waiting for proxy"
    curl --silent  --retry ${PROXY_RETRY_ATTEMPTS:-3} --retry-connrefused --retry-delay ${PROXY_RETRY_DELAY:-10} \
      --proxy ${HTTP_PROXY} --proxy-cacert ${PROXY_CA_PATH:-""} \
      ${PROXY_HOST}:${PROXY_OBSERVABILITY_PORT}
    if [ $? -ne 0 ]; then
      echo "proxy is not ready"
      exit 1
    fi
  fi
fi
```

#### Configuratie afspelen

Wijzig de afspeelrechterconfiguratie (bijvoorbeeld in `playwright.config.js` ) om een proxy te gebruiken voor het geval dat de omgevingsvariabele `HTTP_PROXY` wordt ingesteld.

Voorbeeldimplementatie:

```javascript
const proxyServer = process.env.HTTP_PROXY || ''
```

```javascript
// enable proxy if set
if (proxyServer !== '') {
 cfg.use.proxy = {
  server: proxyServer,
 }
}
```

>[!NOTE]
>
> Een voorbeeldimplementatie kan in de Module van de Test van de Steekproef van de Playwright op [&#x200B; GitHub &#x200B;](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-playwright) worden gevonden.


## UI-tests lokaal uitvoeren {#run-ui-tests-locally}

Alvorens tests UI in een pijpleiding van Cloud Manager te activeren, adviseert Adobe dat u de tests UI plaatselijk tegen [&#x200B; SDK van AEM as a Cloud Service &#x200B;](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) in werking stelt. Of u voert de bewerking uit tegen een AEM as a Cloud Service-instantie.

### Cypersproefmonster {#cypress-sample}

1. Open een shell en navigeer naar de `ui.tests/test-module` -map in uw repository

1. Cypress en andere voorwaarden installeren

   ```shell
   npm install
   ```

1. Omgevingsvariabelen instellen die vereist zijn voor de uitvoering van de test

   ```shell
   export AEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com
   export AEM_AUTHOR_USERNAME=<user>
   export AEM_AUTHOR_PASSWORD=<password>
   export AEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com
   export AEM_PUBLISH_USERNAME=<user>
   export AEM_PUBLISH_PASSWORD=<password>
   export REPORTS_PATH=target/
   ```

1. Test uitvoeren met een van de volgende opdrachten

   ```shell
   npm test              # Using default Cypress browser
   npm run test-chrome   # Using Google Chrome browser
   npm run test-firefox  # Using Firefox browser
   ```

>[!NOTE]
>
>De logbestanden worden opgeslagen in de map `target/` van uw opslagplaats.
>
>Voor details, zie de [&#x200B; bewaarplaats van de Steekproeven van de Test van AEM &#x200B;](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-cypress/test-module/README.md).

### JavaScript WebdriverIO-testmonster {#javascript-sample}

1. Open een shell en navigeer naar de `ui.tests` map in uw repository.

1. Voer het volgende bevel uit om de tests te beginnen gebruikend Maven.

   ```shell
   mvn verify -Pui-tests-local-execution \
    -DAEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_AUTHOR_USERNAME=<user> \
    -DAEM_AUTHOR_PASSWORD=<password> \
    -DAEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_PUBLISH_USERNAME=<user> \
    -DAEM_PUBLISH_PASSWORD=<password>
   ```

>[!NOTE]
>
>* Met deze opdracht wordt een zelfstandige instantie van Selenium gestart en worden de tests tegen deze instantie uitgevoerd.
>* De logbestanden worden opgeslagen in de map `target/reports` van uw opslagplaats
>* U moet ervoor zorgen dat op uw computer de nieuwste Chrome-versie wordt uitgevoerd terwijl de test de meest recente release van ChromeDriver automatisch downloadt voor tests.
>
>Voor details, zie de [&#x200B; bewaarplaats van de Steekproeven van de Test van AEM &#x200B;](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-wdio).

### Testmonster afspelen {#playwright-sample}

1. Open een shell en navigeer naar de `ui.tests` -map in uw repository

1. Voer de onderstaande opdracht uit om een dockerafbeelding te maken met Maven

   ```shell
   mvn clean package -Pui-tests-docker-build
   ```

1. Voer hieronder bevel uit om de tests te beginnen gebruikend Maven

   ```shell
   mvn verify -Pui-tests-docker-execution \
    -DAEM_AUTHOR_URL=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_AUTHOR_USERNAME=<user> \
    -DAEM_AUTHOR_PASSWORD=<password> \
    -DAEM_PUBLISH_URL=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
    -DAEM_PUBLISH_USERNAME=<user> \
    -DAEM_PUBLISH_PASSWORD=<password>
   ```

>[!NOTE]
>
>De logbestanden worden opgeslagen in de map `target/` van uw opslagplaats.
>
>Voor details, zie de [&#x200B; bewaarplaats van de Steekproeven van de Test van AEM &#x200B;](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-playwright).


### Java Selenium WebDriver-testvoorbeeld {#java-sample}

1. Open een shell en navigeer naar de `ui.tests/test-module` -map in uw repository

1. Voer de onderstaande opdrachten uit om de tests te starten met Maven

   ```shell
   # Start selenium docker image
   # we mount /tmp/shared as a shared volume that will be used between selenium and the test module for uploads
   docker run -d -p 4444:4444 -v /tmp/shared:/tmp/shared selenium/standalone-chromium:latest
   
   # Run the tests using the previously started Selenium instance
   mvn verify -Pui-tests-local-execution -DSELENIUM_BASE_URL=http://<server>:4444
   ```

>[!NOTE]
>
>De logbestanden worden opgeslagen in de map `target/reports` van uw opslagplaats.
>
>Voor details, zie de [&#x200B; bewaarplaats van de Steekproeven van de Test van AEM &#x200B;](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/README.md).
