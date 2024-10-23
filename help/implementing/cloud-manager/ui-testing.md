---
title: UI-tests
description: Het testen van de UI van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw douanetoepassingen tot stand te brengen en automatisch in werking te stellen
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8703240a5b7b8ed751620f602470da45025f7b74
workflow-type: tm+mt
source-wordcount: '2698'
ht-degree: 0%

---


# UI-tests {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="UI-tests"
>abstract="Het testen UI van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw toepassingen tot stand te brengen en automatisch in werking te stellen. De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om een brede keus in taal en kaders (zoals Java en Maven, Node en WebDriver.io, of om het even welk ander kader en technologie toe te staan die op Selenium worden voortgebouwd)."

Het testen UI van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw toepassingen tot stand te brengen en automatisch in werking te stellen.

## Overzicht {#custom-ui-testing}

AEM verstrekt een geïntegreerde reeks van [ de kwaliteitsgates van Cloud Manager ](/help/implementing/cloud-manager/custom-code-quality-rules.md) om vlotte updates aan douanetoepassingen te verzekeren. Met name ondersteunen IT-testpoorten al het maken en automatiseren van aangepaste tests met behulp van AEM API&#39;s.

De tests UI worden verpakt in een beeld van de Docker om een brede keus in taal en kaders (zoals Cypress, Selenium, Java en Maven, en JavaScript) toe te staan. Ook, kan een UI testproject gemakkelijk worden geproduceerd door [ het Archieftype van het Project van de AEM te gebruiken ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/overview).

Adobe stimuleert het gebruik van Cypress, omdat deze in real time opnieuw laden en automatisch wachten biedt, wat tijd bespaart en de productiviteit tijdens het testen verbetert. Cypress biedt ook een eenvoudige en intuïtieve syntaxis, waardoor het gemakkelijk is om te leren en te gebruiken, zelfs voor mensen die nog niet aan tests hebben gewerkt.

De tests UI worden uitgevoerd als deel van een specifieke kwaliteitsgate voor elke pijpleiding van Cloud Manager met het Testen van de Douane UI van de a [**** stap ](/help/implementing/cloud-manager/deploy-code.md) in [ productiepijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) of naar keuze [ niet-productiepijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md). Om het even welke tests van de UI met inbegrip van regressie en nieuwe functionaliteiten toelaten om fouten te ontdekken en te melden.

In tegenstelling tot douane functionele tests, die de tests zijn van HTTP in Java worden geschreven, kunnen de tests UI een beeld van de Docker met tests zijn die in om het even welke taal worden geschreven, zolang zij de overeenkomsten volgen die in de sectie [ worden bepaald de Tests van de Bouw UI ](#building-ui-tests).

>[!TIP]
>
>De Adobe adviseert gebruikend Cypress voor het testen UI, na de code die in de [ wordt verstrekt AEM bewaarplaats van de Steekproeven van de Test ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-cypress).
> 
>De Adobe verstrekt ook UI de voorbeelden van de testmodule die op JavaScript van WebdriverIO (zie [ AEM Archetype van het Project ](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests)) en Java met WebDriver (zie [ AEM de bewaarplaats van de Steekproeven van de Test ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver)) worden gebaseerd.

## Aan de slag met gebruikersinterfacetests {#get-started-ui-tests}

In deze sectie worden de stappen beschreven die zijn vereist voor het instellen van UI-tests voor uitvoering in Cloud Manager.

1. Bepaal het testframework dat u wilt gebruiken.

   * Voor Cypress (gebrek), gebruik de steekproefcode van de [ AEM bewaarplaats van de Steekproeven van de Test ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-cypress) of gebruik de steekproefcode die automatisch in de `ui.tests` omslag van uw bewaarplaats van Cloud Manager wordt geproduceerd.

   * Voor Playwright, gebruik de steekproefcode van de [ AEM bewaarplaats van de Steekproeven van de Test ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-playwright).

   * Voor Webdriver.IO, gebruik de steekproefcode van de [ AEM bewaarplaats van de Steekproeven van de Test ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-wdio).

   * Voor Selenium WebDriver, gebruik de steekproefcode van de [ AEM bewaarplaats van de Steekproeven van de Test ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver).

   * Voor andere programmeertalen raadpleegt u het gedeelte [UI-tests](#building-ui-tests) in dit document om het testproject op te zetten.

1. Zorg ervoor dat ui-tests zijn geactiveerd op grond van het gedeelte [&#39;Opt-In](#customer-opt-in) &#39; van de klant in dit document.

1. Ontwikkel uw testcases en [voer de tests lokaal](#run-ui-tests-locally) uit.

1. Voer uw code door in de Cloud Manager-opslagplaats en voer een Cloud Manager-pipeline uit.

## Interfacetests maken {#building-ui-tests}

Een Maven project produceert een Docker bouwt context. In deze docker wordt de bouwcontext beschreven hoe u een Docker-afbeelding kunt maken die de UI-tests bevat en die door Cloud Manager wordt gebruikt om een Docker-afbeelding te genereren die de werkelijke UI-tests bevat.

In deze sectie worden de stappen beschreven die nodig zijn om een UI-testproject toe te voegen aan uw opslagplaats.

>[!TIP]
>
>Het [archetype](https://github.com/adobe/aem-project-archetype) van het AEM-project kan een UI-testproject voor u genereren, dat voldoet aan de volgende beschrijving als u geen speciale vereisten hebt voor de programmeertaal.

### Context van een Docker-build genereren {#generate-docker-build-context}

Om een Docker-buildcontext te genereren, hebt u een Maven-module nodig die:

* Produceert een archief dat een `Dockerfile` en elk ander dossier noodzakelijk bevat om het beeld van de Docker met uw tests te bouwen.
* Hiermee wordt het archief gecodeerd met de classificator `ui-test-docker-context` .

De eenvoudigste manier om dit te doen is de [ Gemaakt Insteekmodule van de Assemblage te vormen ](https://maven.apache.org/plugins/maven-assembly-plugin/) om het Docker te creëren bouwt contextarchief en wijst het juiste classificatiebureau aan het toe.

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

Het archief met de Docker-build-context wordt automatisch opgepakt door Cloud Manager, dat het Docker-image met uw tests zal maken tijdens de implementatiepijplijnen. Uiteindelijk zal Cloud Manager het Docker-beeld in werking stellen om de tests UI tegen uw toepassing uit te voeren.

De build moet nul of één archief produceren. Als het nul archieven produceert, gaat de teststap door gebrek over. Als de build meer dan één archief produceert, is het geselecteerde archief niet-deterministisch.

### Klanten kiezen {#customer-opt-in}

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

>[!NOTE]
>
>Als uw project deze lijn niet omvat, geef het dossier uit om in het testen UI te kiezen.
>
>Het bestand kan een regel bevatten die u adviseert het bestand niet te bewerken. Dit is toe te schrijven aan het worden geïntroduceerd in uw project alvorens het opt-in testen UI werd geïntroduceerd en de cliënten waren niet bedoeld om het dossier uit te geven. Dit kan veilig worden genegeerd.

Als u de voorbeelden gebruikt die door Adobe worden verstrekt:

* Voor de op JavaScript-Gebaseerde `ui.tests` die omslag van [ wordt geproduceerd AEM Archetype van het Project ](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests), kunt u onder bevel uitvoeren om de vereiste configuratie toe te voegen.

  ```shell
  echo "ui-tests.version=1" > testing.properties
  
  if ! grep -q "testing.properties" "assembly-ui-test-docker-context.xml"; then
    awk -v line='                <include>testing.properties</include>' '/<include>wait-for-grid.sh<\/include>/ { printf "%s\n%s\n", $0, line; next }; 1' assembly-ui-test-docker-context.xml > assembly-ui-test-docker-context.xml.new && mv assembly-ui-test-docker-context.xml.new assembly-ui-test-docker-context.xml
  fi
  ```

* De Cypress- en Java Selenium-testmonsters die door de Adobe worden geleverd, beschikken al over de markering opt-in.

## Tests voor gebruikersinterface schrijven {#writing-ui-tests}

Deze sectie beschrijft de overeenkomsten die het beeld van de Docker dat uw tests UI bevat moet volgen. De Docker-afbeelding is gemaakt op basis van de constructiecontext van Docker die in de vorige sectie is beschreven.

### Omgevingsvariabelen {#environment-variables}

De volgende omgevingsvariabelen worden bij uitvoering aan de Docker-afbeelding doorgegeven, afhankelijk van uw framework.

>[!NOTE]
>
> Deze waarden zullen automatisch tijdens pijpleidingsuitvoering worden geplaatst - er is geen behoefte om hen manueel als pijpleidingsvariabelen te plaatsen.

| Variabele | Voorbeelden | Beschrijving | Testframework |
|----------------------------|----------------------------------|----------------------------------------------------------------------------------------------------|---------------------|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | De URL van de seleniumserver | Alleen selenium |
| `SELENIUM_BROWSER` | `chrome` | De browserimplementatie die wordt gebruikt door de seleniumserver | Alleen selenium |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | De URL van de AEM instantie van de auteur | Alles |
| `AEM_AUTHOR_USERNAME` | `admin` | De gebruikersnaam die moet worden gebruikt om u aan te melden bij de instantie van de AEM auteur | Alles |
| `AEM_AUTHOR_PASSWORD` | `admin` | Het wachtwoord om u aan te melden bij de AEM | Alle |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | De URL van de AEM-publicatie-instantie | Alle* |
| `AEM_PUBLISH_USERNAME` | `admin` | De gebruikersnaam om u aan te melden bij de AEM-publicatie-instantie | Alle * |
| `AEM_PUBLISH_PASSWORD` | `admin` | Het wachtwoord voor aanmelding bij de AEM-publicatie-instantie | Alle * |
| `REPORTS_PATH` | `/usr/src/app/reports` | Het pad waar het XML-rapport van de testresultaten moet worden opgeslagen | Alles |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | De URL waarnaar het bestand moet worden geüpload om deze toegankelijk te maken voor het testframework | Alle |
| `PROXY_HOST` | `proxy-host` | De hostnaam van de interne HTTP-proxy die moet worden gebruikt door het testframework | Alles behalve selenium |
| `PROXY_HTTPS_PORT` | `8071` | De luisterpoort van de proxyserver voor HTTPS-verbindingen (kan leeg zijn) | Alles behalve selenium |
| `PROXY_HTTP_PORT` | `8070` | De luisterpoort van de proxyserver voor HTTP-verbindingen (kan leeg zijn) | Alles behalve selenium |
| `PROXY_CA_PATH` | `/path/to/root_ca.pem` | Het pad naar het CA-certificaat dat door het testkader moet worden gebruikt | Alles behalve selenium |
| `PROXY_OBSERVABILITY_PORT` | `8081` | De HTTP-poort voor gezondheidscontrole van de proxyserver | Alles behalve selenium |
| `PROXY_RETRY_ATTEMPTS` | `12` | Voorgesteld aantal pogingen opnieuw proberen tijdens wachten op gereedheid van proxyserver | Alles behalve selenium |
| `PROXY_RETRY_DELAY` | `5` | Voorgestelde vertraging tussen pogingen opnieuw proberen terwijl het wachten op de gereedheid van de volmachtsserver | Alles behalve selenium |

`* these values will be empty if there is no publish instance`

De testmonsters van de Adobe verstrekken helperfuncties om tot de configuratieparameters toegang te hebben:

* Cypress: de standaardfunctie gebruiken `Cypress.env('VARIABLE_NAME')`
* JavaScript: Zie de module [`lib/config.js` ](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests.wdio/test-module/lib/config.js)
* Java: Zie de [`Config` ](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Config.java) -klasse

### Testrapporten genereren {#generate-test-reports}

De Docker-afbeelding moet testrapporten genereren in de XML-indeling JUnit en deze opslaan in het pad dat is opgegeven door de omgevingsvariabele `REPORTS_PATH` . De indeling JUnit XML is een veelgebruikte indeling voor het rapporteren van de resultaten van tests. Als het beeld van de Docker Java en Geweven gebruikt, kunnen de standaardtestmodules zoals [ Gemaakte Steven Stevige Insteekmodule ](https://maven.apache.org/surefire/maven-surefire-plugin/) en [ Geweven Insteekmodule Failsafe ](https://maven.apache.org/surefire/maven-failsafe-plugin/) dergelijke rapporten uit de doos produceren.

Als het Docker-beeld samen met andere programmeertalen of testrunners wordt geïmplementeerd, controleert u de documentatie voor de gekozen hulpmiddelen op hoe u JUnit-XML-rapporten kunt genereren.

>[!NOTE]
>
>Het resultaat van de teststap voor de gebruikersinterface wordt alleen op basis van de testrapporten geëvalueerd. Zorg ervoor dat u het rapport dienovereenkomstig voor uw testuitvoering produceert.
>
>De beweringen van het gebruik in plaats van enkel het registreren van een fout aan STDERR of het terugkeren van een niet-nul uitgangscode anders kan uw plaatsingspijpleiding normaal te werk gaan.
>
>Als een HTTP-proxy tijdens de uitvoering van de test is gebruikt, bevatten de resultaten een `request.log` -bestand.

### Vereisten {#prerequisites}

* De tests in Cloud Manager worden uitgevoerd met een technische admin-gebruiker.

>[!NOTE]
>
>Voor het uitvoeren van de functionele tests van uw lokale computer, creeer een gebruiker met admin-als toestemmingen om het zelfde gedrag te bereiken.

* De containerinfrastructuur die is bestemd voor functionele tests, wordt beperkt door de volgende grenzen:

| Type | Waarde | Beschrijving |
|----------------------|-------|-----------------------------------------------------------------------|
| CPU | 2,0 | De hoeveelheid CPU-tijd die per testuitvoering is gereserveerd. |
| Geheugen | 1 GB | Hoeveelheid aan de test toegewezen geheugen, waarde in bytes. |
| Time-out | 30 m | De duur waarna de test wordt beëindigd. |
| Aanbevolen duur | 15 m | De Adobe beveelt aan de tests te schrijven om deze tijd niet langer te laten duren. |

>[!NOTE]
>
> Als u meer middelen nodig hebt, maakt u een kwestie voor de klantenservice en beschrijft u uw gebruikscase. De Adobe zal uw verzoek beoordelen en de juiste hulp bieden.

## Seleniumspecifieke details

>[!NOTE]
>
>Dit punt is alleen van toepassing wanneer Selenium de gekozen testinfrastructuur is.

### Wachten op klaar voor selenium {#waiting-for-selenium}

Alvorens de tests beginnen, is het de verantwoordelijkheid van het beeld van de Docker om ervoor te zorgen dat de server van Selenium in gebruik is. Wachten op de seleniumservice is een proces in twee stappen.

1. Lees de URL van de Volgens de omgevingsvariabele `SELENIUM_BASE_URL` .
1. Poll met regelmatige intervallen naar het [status-eindpunt](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) dat door de Api van Api van Tijd wordt blootgelegd.

Zodra het statuseindpunt van Endpoint met een positieve respons heeft beantwoord, kunnen de tests beginnen.

De Adobe UI-testvoorbeelden verwerken dit met het script `wait-for-grid.sh`, dat wordt uitgevoerd bij het opstarten van Docker en dat de feitelijke testuitvoering pas start wanneer het raster klaar is.

### Schermafbeeldingen en video&#39;s vastleggen {#capture-screenshots}

De Docker-afbeelding kan aanvullende testuitvoer genereren (bijvoorbeeld schermafbeeldingen of video&#39;s) en deze opslaan in het pad dat wordt aangegeven door de omgevingsvariabele `REPORTS_PATH` . Alle bestanden die onder `REPORTS_PATH` worden gevonden, worden opgenomen in het archief met testresultaten.

De teststeekproeven die door Adobe door gebrek worden verstrekt leiden tot schermafbeeldingen voor om het even welke ontbroken test.

U kunt de hulpfuncties gebruiken om schermafbeeldingen tot stand te brengen door uw tests.

* JavaScript: [opdracht takeScreenshot](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/commons.js)
* Java: [opdrachten](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Commands.java)

Als een archief van het testresultaat tijdens een UI testuitvoering wordt gecreeerd, kunt u het van Cloud Manager downloaden gebruikend de `Download Details` knoop onder de [**het Testen van de Douane UI** stap ](/help/implementing/cloud-manager/deploy-code.md).

### Bestanden uploaden {#upload-files}

Tests moeten soms bestanden uploaden naar de toepassing die wordt getest. Om de implementatie van Selenium flexibel te houden ten opzichte van uw tests, is het niet mogelijk om een middel rechtstreeks naar Selenium te uploaden. In plaats daarvan moet u de volgende stappen uitvoeren om een bestand te uploaden.

1. Upload het bestand naar de URL die door de omgevingsvariabele `UPLOAD_URL` wordt opgegeven.
   * Het uploaden moet worden uitgevoerd in één verzoek van de POST met een meerdelige vorm.
   * Het formulier met meerdere delen moet één bestandsveld hebben.
   * Dit is gelijk aan `curl -X POST ${UPLOAD_URL} -F "data=@file.txt"` .
   * Raadpleeg de documentatie en bibliotheken van de programmeertaal die in het beeld van de Docker wordt gebruikt om te weten hoe te om zulk een HTTP- verzoek uit te voeren.
   * De testmonsters van de Adobe verstrekken helperfuncties voor het uploaden van dossiers:
      * JavaScript: Zie [ getFileHandleForUpload ](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/wdio.commands.js) bevel.
      * Java: Zie de [ klasse FileHandler ](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/FileHandler.java).
1. Als het uploaden is voltooid, retourneert de aanvraag een `200 OK` reactie van het type `text/plain` .
   * De inhoud van de reactie is een ondoorzichtige bestandshandgreep.
   * U kunt deze greep gebruiken in plaats van een bestandspad in een `<input>` -element om het uploaden van bestanden in uw toepassing te testen.

## Cypersspecifieke details

>[!NOTE]
>
>Deze sectie is alleen van toepassing wanneer Cypress de gekozen testinfrastructuur is.

### HTTP-proxy instellen

Het ingangspunt van de Docker-container moet de waarde van de omgevingsvariabele `PROXY_HOST` controleren.

Als deze waarde leeg is, zijn geen extra stappen vereist en de tests zouden zonder de volmacht van HTTP moeten worden uitgevoerd.

Als het niet leeg is, moet het entryPoint manuscript:

1. Vorm een de volmachtsverbinding van HTTP voor het runnen van tests UI. Dit kan worden bereikt door de omgevingsvariabele `HTTP_PROXY` die is samengesteld, te exporteren met de volgende waarden:
   * Proxyhost, die wordt geleverd door `PROXY_HOST` variable
   * Proxypoort, die wordt opgegeven door `PROXY_HTTPS_PORT` of `PROXY_HTTP_PORT` variable (de variabele met een niet-lege waarde wordt gebruikt)
2. Stel het CA-certificaat in dat wordt gebruikt wanneer u verbinding maakt met de HTTP-proxy. De locatie wordt opgegeven door de variabele `PROXY_CA_PATH` .
   * Dit kan worden bereikt door de omgevingsvariabele `NODE_EXTRA_CA_CERTS` te exporteren.
3. Wacht tot de HTTP-proxy gereed is.
   * U kunt de gereedheid controleren door de omgevingsvariabelen `PROXY_HOST` , `PROXY_OBSERVABILITY_PORT` , `PROXY_RETRY_ATTEMPTS` en `PROXY_RETRY_DELAY` te gebruiken.
   * U kunt controleren met een cURL-aanvraag. Controleer of u cURL hebt geïnstalleerd in uw `Dockerfile` .

Een voorbeeldimplementatie kan in het Centrum van de Test van de Steekproef van de Cypress van de Module op [ GitHub ](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-cypress/test-module/run.sh) worden gevonden.

## Specifieke gegevens voor afspelen

>[!NOTE]
>
> Deze sectie is alleen van toepassing wanneer Playwright de gekozen testinfrastructuur is.

### HTTP-proxy instellen

>[!NOTE]
>
> In de voorgelegde voorbeelden, veronderstellen wij Chrome als projectbrowser wordt gebruikt.

Net als bij Cypress moeten tests de HTTP-proxy gebruiken als een niet-lege `PROXY_HOST` omgevingsvariabele wordt opgegeven.

Daartoe moeten de volgende wijzigingen worden aangebracht.

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
2. Gebruik `certutil` om CA-proxycertificaat voor chroom te installeren
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
> Een voorbeeldimplementatie kan in de Module van de Test van de Steekproef van de Playwright op [ GitHub ](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-playwright/) worden gevonden.


## UI-tests lokaal uitvoeren {#run-ui-tests-locally}

Voordat u UI-tests in een Cloud Manager-pipeline activeert, wordt het aanbevolen om de ui-tests lokaal uit te voeren op de [AEM als een Cloud Service-SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) of op een feitelijke AEM als een Cloud Service-instantie.

### Cypress Test Monster {#cypress-sample}

1. Een shell openen en naar de map in de `ui.tests/test-module` opslagplaats navigeren

1. Cypress en andere vereiste&#39;s installeren

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
>Voor details, zie [ AEM de bewaarplaats van de Steekproeven van de Test ](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-cypress/test-module/README.md).

### Voorbeeld van JavaScript-webdriverIO-test {#javascript-sample}

1. Een shell openen en naar de map in de `ui.tests` opslagplaats navigeren

1. Voer de onderstaande opdracht uit om de tests te starten met Maven.

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
>* Dit begint een standalone selenium instantie en voert de tests tegen het uit.
>* De logbestanden worden opgeslagen in de map `target/reports` van uw opslagplaats
>* U moet ervoor zorgen dat op uw computer de nieuwste Chrome-versie wordt uitgevoerd terwijl de test de meest recente release van ChromeDriver automatisch downloadt voor tests.
>
>Voor details, zie [ AEM de bewaarplaats van de Steekproeven van de Test ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-wdio).

### Voorbeeld van afspeelrechttest {#playwright-sample}

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
>Voor details, zie [ AEM de bewaarplaats van de Steekproeven van de Test ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-playwright).


### Java Selenium WebDriver Test Sample {#java-sample}

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
>Voor details, zie [ AEM de bewaarplaats van de Steekproeven van de Test ](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/README.md).
