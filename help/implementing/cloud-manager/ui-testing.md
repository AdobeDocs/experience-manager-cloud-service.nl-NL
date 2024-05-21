---
title: UI-tests
description: Het testen van de UI van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw douanetoepassingen tot stand te brengen en automatisch in werking te stellen
exl-id: 3009f8cc-da12-4e55-9bce-b564621966dd
source-git-commit: 305098c7ebcb6145129b146d60538b5177b4f26d
workflow-type: tm+mt
source-wordcount: '2610'
ht-degree: 0%

---


# UI-tests {#ui-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_uitesting"
>title="UI-tests"
>abstract="Het testen UI van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw toepassingen tot stand te brengen en automatisch in werking te stellen. De tests UI zijn op selenium-Gebaseerde tests die in een beeld van de Docker worden verpakt om een brede keus in taal en kaders (zoals Java en Maven, Node en WebDriver.io, of om het even welk ander kader en technologie toe te staan die op Selenium worden voortgebouwd)."

Het testen UI van de douane is een facultatieve eigenschap die u toelaat om tests UI voor uw toepassingen tot stand te brengen en automatisch in werking te stellen.

## Overzicht {#custom-ui-testing}

AEM biedt een geïntegreerde suite [Kwaliteitspates van Cloud Manager](/help/implementing/cloud-manager/custom-code-quality-rules.md) voor vloeiende updates van aangepaste toepassingen. Met name ondersteunen IT-testpoorten al het maken en automatiseren van aangepaste tests met behulp van AEM API&#39;s.

UI-tests worden verpakt in een Docker-afbeelding, zodat u een ruime keuze kunt maken in taal en frameworks (zoals Cypress, Selenium, Java en Maven en JavaScript). Ook, kan een UI testproject gemakkelijk door te gebruiken worden geproduceerd [het AEM Project Archetype.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)

Adobe stimuleert het gebruik van Cypress, omdat deze in real time opnieuw laden en automatisch wachten biedt, wat tijd bespaart en de productiviteit tijdens het testen verbetert. Cypress biedt ook een eenvoudige en intuïtieve syntaxis, waardoor het gemakkelijk is om te leren en te gebruiken, zelfs voor mensen die nog niet aan tests hebben gewerkt.

UI-tests worden uitgevoerd als onderdeel van een specifieke kwaliteitspoort voor elke Cloud Manager-pijplijn met een [**Aangepaste UI-tests** stap](/help/implementing/cloud-manager/deploy-code.md) in [productiepijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) of optioneel [niet-productieleidingen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md). Om het even welke tests van de UI met inbegrip van regressie en nieuwe functionaliteiten toelaten om fouten te ontdekken en te melden.

In tegenstelling tot aangepaste functionele tests, die HTTP-tests zijn die in Java zijn geschreven, kunnen UI-tests een Docker-afbeelding zijn met tests die in elke taal zijn geschreven, mits ze de conventies volgen die in de sectie zijn gedefinieerd [Interfacetests maken](#building-ui-tests).

>[!TIP]
>
>Adobe raadt aan Cypress te gebruiken voor het testen van de gebruikersinterface, volgens de code in het [AEM opslagplaats voor testmonsters](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-cypress).
> 
>Adobe biedt ook UI-testmodulevoorbeelden op basis van JavaScript met WebdriverIO (zie [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests)) en Java met WebDriver (zie [AEM opslagplaats voor testmonsters](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver)).

## Aan de slag met gebruikersinterfacetests {#get-started-ui-tests}

In deze sectie worden de stappen beschreven die zijn vereist voor het instellen van UI-tests voor uitvoering in Cloud Manager.

1. Bepaal de programmeertaal die u wilt gebruiken.

   * Voor Cypress, gebruik de steekproefcode van [AEM opslagplaats voor testmonsters](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-cypress).

   * Gebruik voor JavaScript en WDIO de voorbeeldcode die automatisch wordt gegenereerd in het dialoogvenster `ui.tests` van uw opslagplaats voor Cloud Manager.

     >[!NOTE]
     >
     >Als uw opslagplaats is gemaakt voordat Cloud Manager automatisch is gemaakt `ui.tests` mappen, kunt u ook de meest recente versie genereren met de [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests).

   * Gebruik voor Java en WebDriver de voorbeeldcode van het dialoogvenster [AEM opslagplaats voor testmonsters](https://github.com/adobe/aem-test-samples/tree/aem-cloud/ui-selenium-webdriver).

   * Zie de sectie voor andere programmeertalen [Interfacetests maken](#building-ui-tests) in dit document aan opstelling het testproject.

1. Zorg ervoor dat UI-tests worden geactiveerd zoals beschreven in de sectie [Klanten kiezen](#customer-opt-in) in dit document.

1. Ontwikkel uw testdoosjes en [Voer de tests lokaal uit](#run-ui-tests-locally).

1. Leg uw code vast in de gegevensopslagruimte van Cloud Manager en voer een pijplijn van Cloud Manager uit.

## Interfacetests maken {#building-ui-tests}

Een Maven project produceert een Docker bouwt context. In deze docker wordt de bouwcontext beschreven hoe u een Docker-afbeelding kunt maken die de UI-tests bevat en die door Cloud Manager wordt gebruikt om een Docker-afbeelding te genereren die de werkelijke UI-tests bevat.

In deze sectie worden de stappen beschreven die nodig zijn om een UI-testproject toe te voegen aan uw opslagplaats.

>[!TIP]
>
>De [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype) U kunt een project van Tests UI voor u produceren, dat aan de volgende beschrijving volgzaam is, als u geen speciale vereisten voor de programmeertaal hebt.

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

De assemblagebeschrijving geeft de plug-in de opdracht een archief van het type te maken `.tar.gz` en wijst de `ui-test-docker-context` classificator. Bovendien worden de bestanden weergegeven die in het archief moeten worden opgenomen, waaronder:

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
>Als uw project deze lijn niet omvat, geef het dossier uit om in het testen UI te kiezen.
>
>Het bestand kan een regel bevatten die u adviseert het bestand niet te bewerken. Dit is toe te schrijven aan het worden geïntroduceerd in uw project alvorens het opt-in testen UI werd geïntroduceerd en de cliënten waren niet bedoeld om het dossier uit te geven. Dit kan veilig worden genegeerd.

Als u de voorbeelden gebruikt die door Adobe worden verstrekt:

* Voor het JavaScript-veld `ui.tests` op basis van de [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests), kunt u onder bevel uitvoeren om de vereiste configuratie toe te voegen.

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

| Variabele | Voorbeelden | Beschrijving | Testframework |
|----------------------------|----------------------------------|---------------------------------------------------------------------------------------------------|---------------------|
| `SELENIUM_BASE_URL` | `http://my-ip:4444` | De URL van de seleniumserver | Alleen selenium |
| `SELENIUM_BROWSER` | `chrome` | De browserimplementatie die wordt gebruikt door de seleniumserver | Alleen selenium |
| `AEM_AUTHOR_URL` | `http://my-ip:4502/context-path` | De URL van de AEM instantie van de auteur | Alles |
| `AEM_AUTHOR_USERNAME` | `admin` | De gebruikersnaam die moet worden gebruikt om u aan te melden bij de instantie van de AEM auteur | Alles |
| `AEM_AUTHOR_PASSWORD` | `admin` | Het wachtwoord om u aan te melden bij de AEM | Alles |
| `AEM_PUBLISH_URL` | `http://my-ip:4503/context-path` | De URL van de AEM-instantie | Alles |
| `AEM_PUBLISH_USERNAME` | `admin` | De gebruikersnaam die moet worden gebruikt om u aan te melden bij de AEM-publicatie-instantie | Alles |
| `AEM_PUBLISH_PASSWORD` | `admin` | Het wachtwoord voor aanmelding bij de AEM-publicatie-instantie | Alles |
| `REPORTS_PATH` | `/usr/src/app/reports` | Het pad waar het XML-rapport van de testresultaten moet worden opgeslagen | Alles |
| `UPLOAD_URL` | `http://upload-host:9090/upload` | De URL waarnaar het bestand moet worden geüpload om deze toegankelijk te maken voor het testframework | Alles |
| `PROXY_HOST` | `proxy-host` | De hostnaam van de interne HTTP-proxy die moet worden gebruikt door het testframework | Alles behalve selenium |
| `PROXY_HTTPS_PORT` | `8071` | De luisterpoort van de proxyserver voor HTTPS-verbindingen (kan leeg zijn) | Alles behalve selenium |
| `PROXY_HTTP_PORT` | `8070` | De luisterpoort van de proxyserver voor HTTP-verbindingen (kan leeg zijn) | Alles behalve selenium |
| `PROXY_CA_PATH` | `/path/to/root_ca.pem` | Het pad naar het CA-certificaat dat door het testkader moet worden gebruikt | Alles behalve selenium |
| `PROXY_OBSERVABILITY_PORT` | `8081` | De HTTP-poort voor gezondheidscontrole van de proxyserver | Alles behalve selenium |
| `PROXY_RETRY_ATTEMPTS` | `12` | Voorgesteld aantal pogingen opnieuw proberen tijdens wachten op gereedheid van proxyserver | Alles behalve selenium |
| `PROXY_RETRY_DELAY` | `5` | Voorgestelde vertraging tussen pogingen opnieuw proberen terwijl het wachten op de gereedheid van de volmachtsserver | Alles behalve selenium |

De testmonsters van de Adobe verstrekken helperfuncties om tot de configuratieparameters toegang te hebben:

* Cypress: de standaardfunctie gebruiken `Cypress.env('VARIABLE_NAME')`
* JavaScript: Zie de [`lib/config.js`](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests.wdio/test-module/lib/config.js) module
* Java: Zie de [`Config`](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/Config.java) class

### Testrapporten genereren {#generate-test-reports}

De Docker-afbeelding moet testrapporten genereren in de XML-indeling JUnit en deze opslaan in het pad dat is opgegeven door de omgevingsvariabele `REPORTS_PATH`. De indeling JUnit XML is een veelgebruikte indeling voor het rapporteren van de resultaten van tests. Als de Docker-afbeelding gebruikmaakt van Java en Maven, gebruikt u standaardtestmodules zoals [Maven Surefire-plug-in](https://maven.apache.org/surefire/maven-surefire-plugin/) en [Maven Failsafe-insteekmodule](https://maven.apache.org/surefire/maven-failsafe-plugin/) kan dergelijke rapporten uit de doos produceren.

Als het Docker-beeld samen met andere programmeertalen of testrunners wordt geïmplementeerd, controleert u de documentatie voor de gekozen hulpmiddelen op hoe u JUnit-XML-rapporten kunt genereren.

>[!NOTE]
>
>Het resultaat van de teststap voor de gebruikersinterface wordt alleen op basis van de testrapporten geëvalueerd. Zorg ervoor dat u het rapport dienovereenkomstig voor uw testuitvoering produceert.
>
>De beweringen van het gebruik in plaats van enkel het registreren van een fout aan STDERR of het terugkeren van een niet-nul uitgangscode anders kan uw plaatsingspijpleiding normaal te werk gaan.
>
>Als een HTTP-proxy tijdens de uitvoering van de tests is gebruikt, bevatten de resultaten een `request.log` bestand.

### Vereisten {#prerequisites}

* De tests in Cloud Manager worden uitgevoerd met een technische beheerder.

>[!NOTE]
>
>Voor het uitvoeren van de functionele tests van uw lokale computer, creeer een gebruiker met admin-als toestemmingen om het zelfde gedrag te bereiken.

* De containerinfrastructuur die is bestemd voor functionele tests, wordt beperkt door de volgende grenzen:

| Type | Waarde | Beschrijving |
|----------------------|-------|-----------------------------------------------------------------------|
| CPU | 2,0 | Hoeveelheid CPU-tijd gereserveerd per testuitvoering |
| Geheugen | 1 GB | Hoeveelheid aan de test toegewezen geheugen, waarde in bytes |
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

1. Lees URL van de dienst van Selenium van de dienst `SELENIUM_BASE_URL` omgevingsvariabele.
1. Opiniepeiling met regelmatige tussenpozen tot de [statuseindpunt](https://github.com/SeleniumHQ/docker-selenium/#waiting-for-the-grid-to-be-ready) door de Selenium-API worden weergegeven.

Zodra het statuseindpunt van Selenium met een positieve reactie beantwoordt, kunnen de tests beginnen.

De teststeekproeven UI van de Adobe behandelen dit met het manuscript `wait-for-grid.sh`, die wordt uitgevoerd bij het opstarten van Docker en de daadwerkelijke testuitvoering pas begint wanneer het net klaar is.

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
   * De testmonsters van de Adobe verstrekken helperfuncties voor het uploaden van dossiers:
      * JavaScript: Zie de [getFileHandleForUpload](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/test-module/lib/wdio.commands.js) gebruiken.
      * Java: Zie de [FileHandler](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/test-module/src/main/java/com/adobe/cq/cloud/testing/ui/java/ui/tests/lib/FileHandler.java) klasse.
1. Als het uploaden is gelukt, retourneert de aanvraag een `200 OK` reactie van het type `text/plain`.
   * De inhoud van de reactie is een ondoorzichtige bestandshandgreep.
   * U kunt deze greep gebruiken in plaats van een bestandspad in een `<input>` -element om het uploaden van bestanden in uw toepassing te testen.

## Cypersspecifieke details

>[!NOTE]
>
>Deze sectie is alleen van toepassing wanneer Cypress de gekozen testinfrastructuur is.

### HTTP-proxy instellen

Het ingangspunt van de container van de Dokker moet de waarde van controleren `PROXY_HOST` omgevingsvariabele.

Als deze waarde leeg is, zijn geen extra stappen vereist en de tests zouden zonder de volmacht van HTTP moeten worden uitgevoerd.

Als het niet leeg is, moet het entryPoint manuscript:

1. Vorm een de volmachtsverbinding van HTTP voor het runnen van tests UI. Dit kan worden bereikt door de `HTTP_PROXY` omgevingsvariabele die is samengesteld met behulp van de volgende waarden:
   * Proxyhost, die wordt geleverd door `PROXY_HOST` variabel
   * Proxypoort, die wordt geleverd door `PROXY_HTTPS_PORT` of `PROXY_HTTP_PORT` variabele (de variabele met een niet-lege waarde wordt gebruikt)
2. Stel het CA-certificaat in dat wordt gebruikt wanneer u verbinding maakt met de HTTP-proxy. De locatie ervan wordt verstrekt door `PROXY_CA_PATH` variabele.
   * Dit kan worden bereikt door de uitvoer `NODE_EXTRA_CA_CERTS` omgevingsvariabele.
3. Wacht tot de HTTP-proxy gereed is.
   * Om de gereedheid te controleren, de omgevingsvariabelen `PROXY_HOST`, `PROXY_OBSERVABILITY_PORT`, `PROXY_RETRY_ATTEMPTS` en `PROXY_RETRY_DELAY` kan worden gebruikt.
   * U kunt controleren met een cURL-aanvraag. Controleer of u cURL hebt geïnstalleerd in uw `Dockerfile`.

Een voorbeeldimplementatie kan in het Centrum van de Test van de Module van de Steekproef van de Cypress op worden gevonden [GitHub.](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-cypress/test-module/run.sh)

## Specifieke gegevens voor afspelen

>[!NOTE]
>
> Deze sectie is alleen van toepassing wanneer Playwright de gekozen testinfrastructuur is.

### HTTP-proxy instellen

>[!NOTE]
>
> In gepresenteerde voorbeelden, veronderstellen wij Chrome als projectbrowser wordt gebruikt.

Net als bij Cypress moeten tests de HTTP-proxy gebruiken als een niet-lege proxy `PROXY_HOST` omgevingsvariabele wordt gegeven.

Daartoe moeten de volgende wijzigingen worden aangebracht.

#### Dockerfile

Installeer de URL en `libnss3-tools`, die `certutil.`

```dockerfile
RUN apt -y update \
    && apt -y --no-install-recommends install curl libnss3-tools \
    && rm -rf /var/lib/apt/lists/*
```

#### EnterPoint-script

Neem een basscript op dat, voor het geval `PROXY_HOST` de omgevingsvariabele wordt gegeven, doet het volgende:

1. Aan proxy gerelateerde variabelen exporteren, zoals `HTTP_PROXY` en `NODE_EXTRA_CA_CERTS`
2. Gebruiken `certutil` om proxy CA-certificaat voor chroom te installeren
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

De afspeelrechtconfiguratie wijzigen (bijvoorbeeld in `playwright.config.js`) gebruiken voor het geval dat de `HTTP_PROXY` omgevingsvariabele wordt ingesteld.

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

## UI-tests lokaal uitvoeren {#run-ui-tests-locally}

Alvorens tests UI in een pijpleiding van de Manager van de Wolk te activeren, adviseert het om de tests UI plaatselijk tegen te stellen [AS A CLOUD SERVICE SDK AEM](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) of tegen een werkelijk AEM as a Cloud Service instantie.

### Monster van Cypress-test {#cypress-sample}

1. Open een shell en navigeer naar `ui.tests/test-module` map in uw opslagplaats

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
>De logbestanden worden opgeslagen in het dialoogvenster `target/` van uw opslagplaats.
>
>Zie voor meer informatie [AEM opslagplaats voor testmonsters](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-cypress/test-module/README.md).

### Voorbeeld van JavaScript WebdriverIO-test {#javascript-sample}

1. Open een shell en navigeer naar `ui.tests` map in uw opslagplaats

1. Voer hieronder bevel uit om de tests te beginnen gebruikend Maven

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
>* De logbestanden worden opgeslagen in het dialoogvenster `target/reports` map van uw opslagplaats
>* U moet ervoor zorgen dat op uw computer de nieuwste Chrome-versie wordt uitgevoerd terwijl de test de meest recente release van ChromeDriver automatisch downloadt voor tests.
>
>Zie voor meer informatie [Opslagplaats voor projectarchetype AEM](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/ui.tests/README.md).

### Java Selenium WebDriver Test Sample {#java-sample}

1. Open een shell en navigeer naar `ui.tests/test-module` map in uw opslagplaats

1. Voer de onderstaande opdrachten uit om de tests te starten met Maven

   ```shell
   # Start selenium docker image (for x64 CPUs)
   docker run --platform linux/amd64 -d -p 4444:4444 selenium/standalone-chrome-debug:latest
   
   # Start selenium docker image (for ARM CPUs)
   docker run -d -p 4444:4444 seleniarm/standalone-chromium
   
   # Run the tests using the previously started Selenium instance
   mvn verify -Pui-tests-local-execution -DSELENIUM_BASE_URL=http://<server>:4444
   ```

>[!NOTE]
>
>De logbestanden worden opgeslagen in het dialoogvenster `target/reports` van uw opslagplaats.
>
>Zie voor meer informatie [AEM opslagplaats voor testmonsters](https://github.com/adobe/aem-test-samples/blob/aem-cloud/ui-selenium-webdriver/README.md).
