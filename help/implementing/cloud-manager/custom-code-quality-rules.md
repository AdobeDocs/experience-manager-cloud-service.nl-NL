---
title: Aangepaste regels voor codekwaliteit
description: Op deze pagina worden de regels voor de kwaliteit van aangepaste code beschreven die Cloud Manager uitvoert als onderdeel van het testen van de kwaliteit van de code. Ze zijn gebaseerd op best practices van Adobe Experience Manager Engineering.
exl-id: f40e5774-c76b-4c84-9d14-8e40ee6b775b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '4513'
ht-degree: 0%

---

# Aangepaste regels voor codekwaliteit {#custom-code-quality-rules}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_customcodequalityrules"
>title="Aangepaste regels voor codekwaliteit"
>abstract="Op deze pagina worden de regels voor de kwaliteit van aangepaste code beschreven die Cloud Manager uitvoert als onderdeel van het testen van de kwaliteit van de code. Ze zijn gebaseerd op best practices van Adobe Experience Manager Engineering."

Deze pagina beschrijft de de kwaliteitsregels van de douanecode die door Cloud Manager als deel van [ worden uitgevoerd codekwaliteit het testen ](/help/implementing/cloud-manager/code-quality-testing.md). Zij zijn gebaseerd op beste praktijken van de Techniek van de Experience Manager.

>[!NOTE]
>
>Volledige SonarQube-regels zijn niet beschikbaar voor downloaden vanwege informatie die eigendom is van de Adobe. U kunt de volledige lijst van regels [ downloaden gebruikend deze verbinding ](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx). Lees dit document verder voor beschrijvingen en voorbeelden van de regels.

>[!NOTE]
>
>De hier opgegeven codevoorbeelden dienen slechts ter illustratie. Zie de documentatie SonarQube [ Concepts ](https://docs.sonarqube.org/latest/) om over concepten SonarQube en kwaliteitsregels te leren.

## SonarQube-regels {#sonarqube-rules}

In de volgende sectie worden SonarQube-regels beschreven die door Cloud Manager worden uitgevoerd.

### Gebruik geen potentieel gevaarlijke functies {#do-not-use-potentially-dangerous-functions}

* **Sleutel**: CQRules:CWE-676
* **Type**: Vulnerability
* **Ernst**: Belangrijk
* **sinds**: Versie 2018.4.0

De methoden `Thread.stop()` en `Thread.interrupt()` kunnen problemen veroorzaken die moeilijk te reproduceren zijn, en soms ook beveiligingskwetsbaarheden. Het gebruik ervan moet zorgvuldig worden gecontroleerd en gevalideerd. Over het algemeen is het doorgeven van berichten een veiligere manier om vergelijkbare doelen te bereiken.

#### Niet-compatibele code {#non-compliant-code}

```java
public class DontDoThis implements Runnable {
  private Thread thread;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    thread.stop();  // UNSAFE!
  }
 
  public void run() {
    while (true) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

#### Compatibele code {#compliant-code}

```java
public class DoThis implements Runnable {
  private Thread thread;
  private boolean keepGoing = true;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    keepGoing = false;
  }
 
  public void run() {
    while (this.keepGoing) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

### Gebruik geen opmaaktekenreeksen die extern kunnen worden beheerd {#do-not-use-format-strings-which-may-be-externally-controlled}

* **Sleutel**: CQRules:CWE-134
* **Type**: Vulnerability
* **Ernst**: Belangrijk
* **sinds**: Versie 2018.4.0

Het gebruiken van een formaatkoord van een externe bron (zoals een verzoekparameter of user-generated inhoud) kan een toepassing aan ontkenning van de dienstaanvallen blootstellen. Er zijn omstandigheden waarin een indelingstekenreeks extern kan worden beheerd, maar alleen is toegestaan vanuit vertrouwde bronnen.

#### Niet-compatibele code {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP-aanvragen moeten altijd socket- en verbindingstime-outs hebben {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Sleutel**: CQRules:ConnectionTimeoutMechanism
* **Type**: Bug
* **Ernst**: Kritiek
* **sinds**: Versie 2018.6.0

Wanneer het uitvoeren van HTTP- verzoeken van binnen een toepassing van de Experience Manager, is het kritiek om ervoor te zorgen dat juiste onderbrekingen worden gevormd om onnodige draadconsumptie te vermijden. Jammer genoeg, is het standaardgedrag van zowel de standaardHTTP- Cliënt van Java™ (`java.net.HttpUrlConnection`) als de algemeen gebruikte cliënt van de Componenten van Apache HTTP aan geen tijd uit, zodat moeten de onderbrekingen uitdrukkelijk worden geplaatst. Bovendien zouden deze onderbrekingen, als beste praktijken, niet meer dan 60 seconden moeten zijn.

#### Niet-compatibele code {#non-compliant-code-2}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void dontDoThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  HttpClient httpClient = builder.build();

  // do something with the client
}

public void dontDoThisEither() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

#### Compatibele code {#compliant-code-1}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void doThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  RequestConfig requestConfig = RequestConfig.custom()
    .setConnectTimeout(5000)
    .setSocketTimeout(5000)
    .build();
  builder.setDefaultRequestConfig(requestConfig);
 
  HttpClient httpClient = builder.build();
   
  // do something with the client
}

public void orDoThis () {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
  urlConnection.setConnectTimeout(5000);
  urlConnection.setReadTimeout(5000);
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

### ResourceResolver-objecten altijd sluiten {#resourceresolver-objects-should-always-be-closed}

* **Sleutel**: CQRules:CQBP-72
* **Type**: Code Smell
* **Ernst**: Belangrijk
* **sinds**: Versie 2018.4.0

`ResourceResolver` -objecten die uit `ResourceResolverFactory` zijn opgehaald, gebruiken systeembronnen. Hoewel er maatregelen zijn om deze bronnen terug te winnen wanneer een `ResourceResolver` niet meer in gebruik is, is het efficiënter om geopende `ResourceResolver` -objecten expliciet te sluiten door de methode `close()` aan te roepen.

Een relatief gebruikelijke misvatting is dat `ResourceResolver` -objecten die met een bestaande JCR-sessie zijn gemaakt, niet expliciet moeten worden gesloten of dat de onderliggende JCR-sessie hierdoor wordt gesloten. Dat is niet het geval. Ongeacht hoe een `ResourceResolver` wordt geopend, moet deze worden gesloten wanneer deze niet meer wordt gebruikt. Aangezien `ResourceResolver` de interface `Closeable` implementeert, is het ook mogelijk om de syntaxis `try-with-resources` te gebruiken in plaats van `close()` expliciet aan te roepen.

#### Niet-compatibele code {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### Compatibele code {#compliant-code-2}

```java
public void doThis(Session session) throws Exception {
  ResourceResolver resolver = null;
  try {
    resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
    // do something with the resolver
  } finally {
    if (resolver != null) {
      resolver.close();
    }
  }
}

public void orDoThis(Session session) throws Exception {
  try (ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object) session))){
    // do something with the resolver
  }
}
```

### Gebruik geen Serlet-serverpaden naar elkaar om servlets te registreren {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Sleutel**: CQRules:CQBP-75
* **Type**: Code Smell
* **Ernst**: Belangrijk
* **sinds**: Versie 2018.4.0

Zoals die in de [ het Schuiven documentatie ](https://sling.apache.org/documentation/the-sling-engine/servlets.html) wordt beschreven, bindingen servlets door wegen wordt ontmoedigd. Padgebonden servers kunnen geen standaard JCR-toegangsbesturingselementen gebruiken en vereisen daarom extra beveiligingsstrengheid. In plaats van het gebruiken van weg-gebonden servlets, wordt het geadviseerd om knopen in de bewaarplaats tot stand te brengen en servlets te registreren door middeltype.

#### Niet-compatibele code {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Afgehandelde uitzonderingen zouden moeten worden geregistreerd of geworpen, niet allebei {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **Sleutel**: CQRules:CQBP-44-CatchAndOrLogOrThrow
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2018.4.0

In het algemeen, zou een uitzondering precies één keer moeten worden geregistreerd. Het registreren van uitzonderingen kan veelvoudige tijden verwarring veroorzaken aangezien het onduidelijk is hoe vaak een uitzondering voorkwam. Het meest gangbare patroon dat tot dit leidt is het registreren en het werpen van een gevangen uitzondering.

#### Niet-compatibele code {#non-compliant-code-6}

```java
public void dontDoThis() throws Exception {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
    throw e;
  }
}
```

#### Compatibele code {#compliant-code-3}

```java
public void doThis() {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
  }
}

public void orDoThis() throws MyCustomException {
  try {
    someOperation();
  } catch (Exception e) {
    throw new MyCustomException(e);
  }
}
```

### Vermijd loginstructies die onmiddellijk worden gevolgd door een throw-instructie {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **Sleutel**: CQRules:CQBP-44-OpeenvolgendLogAndThrow
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2018.4.0

Een ander gemeenschappelijk patroon te vermijden is een bericht te registreren en dan onmiddellijk een uitzondering te werpen. Deze praktijk wijst over het algemeen erop dat het uitzonderingsbericht omhoog gedupliceerd in logboekdossiers beëindigt.

#### Niet-compatibele code {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### Compatibele code {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### Meld u niet aan bij INFO wanneer u GET- of HEAD-verzoeken afhandelt {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Sleutel**: CQRules:CQBP-44-LogInfoInGetOrHeadRequests
* **Type**: Code Smell
* **Ernst**: Klein

In het algemeen, zou het INFO logboekniveau moeten worden gebruikt om belangrijke acties te afbakenen en, door gebrek, wordt de Experience Manager gevormd om bij het INFO niveau of boven te registreren. GET- en HEAD-methoden mogen nooit alleen-lezen zijn en vormen dus geen belangrijke acties. Het registreren op het niveau INFO in antwoord op GET of HEAD verzoeken zal waarschijnlijk tot significante logboeklawaai leiden, die het moeilijker maken om nuttige informatie in logboekdossiers te identificeren. Het registreren wanneer de behandeling van GET of HEAD- verzoeken of op de niveaus van de WAARSCHUWING of van de FOUT zou moeten zijn wanneer iets verkeerd is gegaan of op de niveaus DEBUG of van de TRACE als de diepere het oplossen van problemeninformatie nuttig zou zijn.

>[!NOTE]
>
>Dit is niet van toepassing op het registreren van het type `access.log` voor elke aanvraag.

#### Niet-compatibele code {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### Compatibele code {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### Gebruik Exception.getMessage() niet als de eerste parameter van een logboekinstructie {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Sleutel**: CQRules:CQBP-44-ExceptionGetMessageIsFirstLogParam
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2018.4.0

Als beste praktijken, zouden de logboekberichten contextuele informatie over moeten verstrekken waar in de toepassing een uitzondering is voorgekomen. Terwijl de context ook door stapelsporen te gebruiken kan worden bepaald, over het algemeen zal het logboekbericht gemakkelijker zijn te lezen en te begrijpen. Dientengevolge, wanneer het registreren van een uitzondering, is het een slechte praktijk om het bericht van de uitzondering als logboekbericht te gebruiken. Het uitzonderingsbericht bevat wat verkeerd ging terwijl het logboekbericht zou moeten worden gebruikt om een logboeklezer te vertellen wat de toepassing deed toen de uitzondering gebeurde. Het uitzonderingsbericht wordt nog geregistreerd. Door uw eigen bericht te specificeren, zijn de logboeken gemakkelijker te begrijpen.

#### Niet-compatibele code {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### Compatibele code {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Aanmelden van vangstblokken moet zich op het WARN- of FOUTniveau bevinden {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **Sleutel**: CQRules:CQBP-44-WrongLogLevelInCatchBlock
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2018.4.0

Zoals de naam al aangeeft, moeten Java™-uitzonderingen altijd in uitzonderlijke omstandigheden worden gebruikt. Dientengevolge, wanneer een uitzondering wordt gevangen, is het belangrijk om ervoor te zorgen dat de logboekberichten op het aangewezen niveau, of WARN of FOUT worden geregistreerd. Dit zorgt ervoor dat die berichten correct in de logboeken verschijnen.

#### Niet-compatibele code {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### Compatibele code {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Stapelsporen niet naar de console afdrukken {#do-not-print-stack-traces-to-the-console}

* **Sleutel**: CQRules:CQBP-44-ExceptionPrintStackTrace
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2018.4.0

Zoals vermeld, is de context kritiek wanneer het begrip van logboekberichten. Wanneer u `Exception.printStackTrace()` gebruikt, wordt alleen de stacktracering uitgevoerd naar de standaardfoutenstream, waardoor alle context verloren gaat. Als in een toepassing met meerdere threads, zoals Experience Managers, meerdere uitzonderingen parallel met deze methode worden afgedrukt, kunnen de stacksporen elkaar overlappen, wat tot grote verwarring leidt. De uitzonderingen zouden door het registrerenkader slechts moeten worden geregistreerd.

#### Niet-compatibele code {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### Compatibele code {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Niet uitvoeren naar standaarduitvoer of standaardfout {#do-not-output-to-standard-output-or-standard-error}

* **Sleutel**: CQRules:CQBP-44-LogLevelConsolePrinters
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2018.4.0

Het registreren in Experience Manager zou altijd door het registrerenkader (SLF4J) moeten worden gedaan. Als u rechtstreeks uitvoert naar de standaarduitvoer of standaardfoutenstromen, verliest u de structurele en contextuele informatie die door het logboekframework wordt verschaft. Soms kan dit prestatieproblemen veroorzaken.

#### Niet-compatibele code {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### Compatibele code {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Vermijd hardcoded /apps en /libs paden {#avoid-hardcoded-apps-and-libs-paths}

* **Sleutel**: CQRules:CQBP-71
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2018.4.0

Doorgaans moeten paden die beginnen met `/libs` en `/apps` niet worden gecodeerd als de paden waarnaar ze verwijzen, meestal worden opgeslagen als paden die relatief zijn ten opzichte van het zoekpad met de optie Schuivend, dat standaard is ingesteld op `/libs,/apps` . Het gebruik van het absolute pad kan leiden tot subtiele defecten die pas later in de levenscyclus van het project verschijnen.

#### Niet-compatibele code {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### Compatibele code {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### Gebruik geen Sling Planner {#sonarqube-sling-scheduler}

* **Sleutel**: CQRules:AMSCORE-554
* **Type**: De Verenigbaarheid van de Code Smell/van de Cloud Service
* **Ernst**: Klein
* **sinds**: Versie 2020.5.0

Gebruik Sling Scheduler niet voor taken waarvoor een gegarandeerde uitvoering is vereist. Het verkopen van Geplande Banen garandeert uitvoering en beter geschikt voor zowel gegroepeerde als niet-gegroepeerde milieu&#39;s.

Zie [ Apache het Sling Gebeurtenis en de Behandeling van de Baan ](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) om meer over te leren hoe het Verschuiven van Banen in gegroepeerde milieu&#39;s worden behandeld.

### Gebruik geen API&#39;s die zijn vervangen door Experience Managers {#sonarqube-aem-deprecated}

* **Sleutel**: AMSCORE-553
* **Type**: De Verenigbaarheid van de Code Smell/van de Cloud Service
* **Ernst**: Klein
* **sinds**: Versie 2020.5.0

Het API-oppervlak van de Experience Manager wordt voortdurend herzien om API&#39;s te identificeren waarvoor het gebruik wordt ontmoedigd en dus als afgekeurd wordt beschouwd.

Deze API&#39;s zijn vaak verouderd met de standaard Java™ `@Deprecated` -annotatie en worden daarom als zodanig herkend door `squid:CallToDeprecatedMethod` .

Er zijn echter gevallen waarin een API in de context van Experience Manager is afgekeurd, maar in andere contexten niet mag worden afgekeurd. Deze regel identificeert deze tweede klasse.

### Gebruik geen @Injectie-annotatie met @Optional in Sling Models {#sonarqube-slingmodels-inject-optional}

* **Sleutel**: InjectAnnotationWithOptionalInjectionCheck
* **Type**: De kwaliteit van de software
* **Ernst**: Klein
* **sinds**: Versie 2023.11

Het Apache Sling-project ontmoedigt het gebruik van de `@Inject` -annotatie in de context van Sling Models, omdat dit tot slechte prestaties kan leiden wanneer het wordt gecombineerd met `DefaultInjectionStrategy.OPTIONAL` (op veld- of klassenniveau). In plaats daarvan moeten meer specifieke injecties (zoals de `@ValueMapValue` - of `@OsgiInjector` -annotaties) worden gebruikt.

Controleer de [ documentatie van Apache Sling ](https://sling.apache.org/documentation/bundles/models.html#discouraged-annotations-1) voor meer informatie over de geadviseerde annotaties en waarom deze aanbeveling in de eerste plaats werd gemaakt.


### Instanties van een HTTPClient opnieuw gebruiken {#sonarqube-reuse-httpclient}

* **Sleutel**: AEMSRE-870
* **Type**: De kwaliteit van de software
* **Ernst**: Klein
* **sinds**: Versie 2023.11

AEM toepassingen bereiken vaak andere toepassingen met behulp van het HTTP-protocol en Apache HttpClient is een vaak gebruikte bibliotheek om dit te bereiken. Maar de verwezenlijking van zulk een voorwerp HttpClient komt met wat overheadkosten, zodat zouden deze voorwerpen zo veel mogelijk moeten worden opnieuw gebruikt.

Deze regel controleert dat zulk een voorwerp HttpClient niet privé binnen een methode, maar globaal op een klassenniveau is, zodat kan het worden opnieuw gebruikt. In dit geval moet het veld httpClient worden ingesteld in de constructor van de klasse of de methode `activate()` (als deze klasse een OSGi-component/service is).

Controleer de [ Gids van de Optimalisering ](https://hc.apache.org/httpclient-legacy/performance.html) van HttpClient voor sommige beste praktijken betreffende het gebruik van HttpClient.

#### Niet-compatibele code {#non-compliant-code-14}

```java
public void doHttpCall() {
  HttpClient httpclient = HttpClients.createDefault();
  // do something with the httpclient
}
```

#### Compatibele code {#compliant-code-11}

```java
public class myClass {

  HttpClient httpclient;

  public void doHttpCall() {
    // do something with the httpclient
  }

}
```

## Regels voor OakPAL-inhoud {#oakpal-rules}

In de volgende sectie worden de OakPAL-controles beschreven die door Cloud Manager worden uitgevoerd.

>[!NOTE]
>
>OakPAL is een framework dat inhoudspakketten valideert met behulp van een zelfstandige Oak-opslagplaats. Het werd ontwikkeld door een partner van de Experience Manager en winnaar van de Experience Manager Rockstar North America van 2019.

### Product-API&#39;s die met @ProviderType zijn geannoteerd, mogen niet door klanten worden geïmplementeerd of uitgebreid {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Sleutel**: CQBP-84
* **Type**: Bug
* **Ernst**: Kritiek
* **sinds**: Versie 2018.7.0

De Experience Manager-API bevat Java™-interfaces en -klassen die alleen bedoeld zijn voor gebruik — maar niet geïmplementeerd — door aangepaste code. De interface `com.day.cq.wcm.api.Page` moet bijvoorbeeld alleen door de Experience Manager worden geïmplementeerd.

Wanneer nieuwe methodes aan deze interfaces worden toegevoegd, beïnvloeden die extra methodes geen bestaande code die deze interfaces gebruikt. Dientengevolge, wordt de toevoeging van nieuwe methodes aan deze interfaces beschouwd achterwaarts-compatibel te zijn. Nochtans, als de douanecode één van deze interfaces uitvoert, heeft die douanecode een achterwaarts-verenigbaarheidsrisico voor de klant geïntroduceerd.

Interfaces en klassen — zoals geïmplementeerd door Experience Manager — zijn voorzien van een annotatie `org.osgi.annotation.versioning.ProviderType` of soms een vergelijkbare oudere annotatie `aQute.bnd.annotation.ProviderType` . Deze regel identificeert de gevallen waarin een dergelijke interface wordt uitgevoerd of een klasse door douanecode wordt uitgebreid.

#### Niet-compatibele code {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Aangepaste Lucene Oak-indexen moeten een Tika-configuratie hebben {#oakpal-indextikanode}

* **Sleutel**: IndexTikaNode
* **Type**: Bug
* **Ernst**: Blocker
* **sinds**: 2021.8.0

De veelvoudige uit-van-de-doos indexen van Oak van de Experience Manager omvatten een configuratie van de Tika en de aanpassingen van deze indexen moeten een configuratie van de Tika omvatten. Deze regel controleert op aanpassingen van de indexen `damAssetLucene` , `lucene` en `graphqlConfig` en geeft een probleem weer als een van de indexen `tika`  node ontbreekt of als het knooppunt `tika` een onderliggend knooppunt met de naam `config.xml` mist.

Zie [ het indexeren documentatie ](/help/operations/indexing.md#preparing-the-new-index-definition) voor meer informatie bij het aanpassen van indexdefinities.

#### Niet-compatibele code {#non-compliant-code-indextikanode}

```text
+ oak:index
    + damAssetLucene-1-custom
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - tags: [visualSimilaritySearch]
      - type: lucene
```

#### Compatibele code {#compliant-code-indextikanode}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Aangepaste Oak-indexen voor Lucene mogen niet synchroon zijn {#oakpal-indexasync}

* **Sleutel**: IndexAsyncProperty
* **Type**: Bug
* **Ernst**: Blocker
* **sinds**: 2021.8.0

Oak-indexen van het type `lucene` moeten altijd asynchroon worden geïndexeerd. Als u dit niet doet, kan dit leiden tot instabiliteit van het systeem. Meer informatie over de structuur van de indexen van Lucene kan in de [ documentatie van Oak ](https://jackrabbit.apache.org/oak/docs/query/lucene.html#index-definition) worden gevonden.

#### Niet-compatibele code {#non-compliant-code-indexasync}

```text
+ oak:index
    + damAssetLucene-1-custom
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - type: lucene
      - tags: [visualSimilaritySearch]
      + tika
        + config.xml
```

#### Compatibele code {#compliant-code-indexasync}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Aangepaste DAM Asset Lucene Oak-indexen hebben de juiste structuur  {#oakpal-damAssetLucene-sanity-check}

* **Sleutel**: IndexDamAssetLucene
* **Type**: Bug
* **Ernst**: Blocker
* **sinds**: 2021.6.0

Als u wilt dat het zoeken naar elementen correct werkt in Experience Manager Assets, moeten aanpassingen van de Oak-index van `damAssetLucene` een aantal richtlijnen volgen die specifiek zijn voor deze index. Deze regel controleert of de indexdefinitie een multi-getaxeerde eigenschap met de naam `tags` moet hebben die de waarde `visualSimilaritySearch` bevat.

#### Niet-compatibele code {#non-compliant-code-damAssetLucene}

```text
+ oak:index
    + damAssetLucene-1-custom
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - type: lucene
      + tika
        + config.xml
```

#### Compatibele code {#compliant-code-damAssetLucene}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Klantpakketten mogen geen knooppunten onder /libs maken of wijzigen {#oakpal-customer-package}

* **Sleutel**: BannedPath
* **Type**: Bug
* **Ernst**: Kritiek
* **sinds**: Versie 2019.6.0

Het is al lang een goede gewoonte om de `/libs` -inhoudsstructuur in de opslagplaats voor inhoud van de Experience Manager als alleen-lezen te beschouwen voor klanten. Als u knooppunten en eigenschappen wijzigt onder `/libs` , ontstaat een aanzienlijk risico voor belangrijke en kleine updates. Wijzigingen in `/libs` moeten via officiële Adobe plaatsvinden.

### De pakketten zouden geen dubbele configuraties OSGi moeten bevatten {#oakpal-package-osgi}

* **Sleutel**: DuplicateOsgiConfigurations
* **Type**: Bug
* **Ernst**: Belangrijk
* **sinds**: Versie 2019.6.0

Een gemeenschappelijk probleem dat op complexe projecten voorkomt is waar de zelfde component OSGi veelvoudige tijden wordt gevormd. Deze kwestie leidt tot dubbelzinnigheid over welke configuratie van toepassing is. Deze regel is &quot;runmode-bewust&quot;in die zin dat het slechts kwesties identificeert waar de zelfde component veelvoudige tijden op de zelfde looppaswijze of de combinatie looppaswijzen wordt gevormd.

>[!NOTE]
>
>Deze regel veroorzaakt kwesties waar de zelfde configuratie, bij de zelfde weg, in veelvoudige pakketten wordt bepaald, met inbegrip van gevallen waar het zelfde pakket in de algemene lijst van gebouwde pakketten wordt gedupliceerd.
>
>Als de build bijvoorbeeld pakketten met de naam `com.myco:com.myco.ui.apps` en `com.myco:com.myco.all` where `com.myco:com.myco.all` embeds `com.myco:com.myco.ui.apps` genereert, worden alle configuraties in `com.myco:com.myco.ui.apps` als duplicaten gerapporteerd.
>
>Dit is over het algemeen een geval van het niet volgen van de [ Richtlijnen van de Structuur van het Pakket van de Inhoud ](/help/implementing/developing/introduction/aem-project-content-package-structure.md). In dit specifieke voorbeeld ontbreekt de eigenschap `<cloudManagerTarget>none</cloudManagerTarget>` in het pakket `com.myco:com.myco.ui.apps` .

#### Niet-compatibele code {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Compatibele code {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Configureren en installatiemappen mogen alleen OSGi-knooppunten bevatten {#oakpal-config-install}

* **Sleutel**: ConfigAndInstallShouldOnlyContainOsgiNodes
* **Type**: Bug
* **Ernst**: Belangrijk
* **sinds**: Versie 2019.6.0

Om veiligheidsredenen, zijn de wegen die `/config/` en `/install/` bevatten slechts leesbaar door administratieve gebruikers in Experience Manager en zouden slechts voor configuratie OSGi en bundels OSGi moeten worden gebruikt. Als u andere typen inhoud onder paden plaatst die deze segmenten bevatten, resulteert dit in toepassingsgedrag dat per ongeluk verschilt tussen gebruikers met en zonder beheerdersrechten.

Een veelvoorkomend probleem is het gebruik van knooppunten met de naam `config` in componentdialoogvensters of wanneer u de configuratie van de rich text editor opgeeft voor inlinebewerking. Om dit probleem op te lossen, moet de naam van het desbetreffende knooppunt worden gewijzigd in een compatibele naam. Voor de configuratie van de RTF-editor gebruikt u de eigenschap `configPath` op het knooppunt `cq:inplaceEditing` om de nieuwe locatie op te geven.

#### Niet-compatibele code {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Compatibele code {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### Pakketten mogen elkaar niet overlappen {#oakpal-no-overlap}

* **Sleutel**: PackageOverlaps
* **Type**: Bug
* **Ernst**: Belangrijk
* **sinds**: Versie 2019.6.0

Gelijkaardig aan de [ Pakketten zouden de Dubbele regel van Configuraties niet moeten bevatten OSGi, ](#oakpal-package-osgi) dit is een gemeenschappelijk probleem op complexe projecten waar de zelfde knoopweg aan door veelvoudige afzonderlijke inhoudspakketten wordt geschreven. Terwijl het gebruiken van inhoudspakketgebiedsdelen kan worden gebruikt om een verenigbaar resultaat te verzekeren, is het beter om overlappingen volledig te vermijden.

### Standaardontwerpmodus mag geen klassieke UI zijn {#oakpal-default-authoring}

* **Sleutel**: ClassicUIAuthoringMode
* **Type**: De Verenigbaarheid van de Code Smell/van de Cloud Service
* **Ernst**: Klein
* **sinds**: Versie 2020.5.0

De configuratie OSGi `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` bepaalt de standaard auteurswijze binnen Experience Manager. Omdat Klassieke UI sinds Experience Manager 6.4 is afgekeurd, wordt een kwestie nu opgeheven wanneer de standaard auteurswijze aan Klassieke UI wordt gevormd.

### Componenten met dialoogvensters moeten een interface-aanraakdialoogvensters hebben {#oakpal-components-dialogs}

* **Sleutel**: ComponentWithOnlyClassicUIDialog
* **Type**: De Verenigbaarheid van de Code Smell/van de Cloud Service
* **Ernst**: Klein
* **sinds**: Versie 2020.5.0

Componenten van Experience Managers die een Klassieke UI-dialoogvenster hebben, moeten altijd een overeenkomstig dialoogvenster Touch UI hebben. Beide bieden een optimale ontwerpervaring en zijn compatibel met het implementatiemodel van de Cloud Service, waarbij de klassieke gebruikersinterface niet wordt ondersteund. Deze regel verifieert de volgende scenario&#39;s:

* Een component met een klassieke UI-dialoogvenster (dat wil zeggen een `dialog` onderliggende node) moet een overeenkomend Touch UI-dialoogvenster hebben (dat wil zeggen een `cq:dialog` onderliggende node).
* Een component met een klassieke UI-ontwerpdialoogvenster (dat wil zeggen een `design_dialog` -knooppunt) moet een corresponderend dialoogvenster voor het aanraakinterface-ontwerp hebben (dat wil zeggen een `cq:design_dialog` onderliggende node).
* Een component met zowel een dialoogvenster voor klassieke gebruikersinterface als een dialoogvenster voor klassieke gebruikersinterface moet zowel een corresponderend dialoogvenster voor aanraakinterface als een overeenkomstig dialoogvenster voor aanraakgebruikersinterface hebben.

De documentatie van de Hulpmiddelen van de Modernisering van de Experience Manager verstrekt documentatie en tooling voor hoe te om componenten van Klassieke UI in Aanraakinterface om te zetten. Zie [ de documentatie van Hulpmiddelen van de Modernisering van de Experience Manager ](https://opensource.adobe.com/aem-modernize-tools/) voor meer details.

### Pakketten mogen geen veranderbare en onveranderlijke inhoud mengen {#oakpal-packages-immutable}

* **Sleutel**: ImmutableMutableMixedPackage
* **Type**: De Verenigbaarheid van de Code Smell/van de Cloud Service
* **Ernst**: Klein
* **sinds**: Versie 2020.5.0

Om compatibel te zijn met het implementatiemodel van Cloud Servicen, moeten afzonderlijke inhoudspakketten inhoud bevatten voor de onveranderlijke gebieden van de opslagplaats (`/apps` en `/libs`) of het veranderbare gebied (alles niet in `/apps` of `/libs`), maar niet beide. Een pakket dat bijvoorbeeld zowel `/apps/myco/components/text` als `/etc/clientlibs/myco` bevat, is niet compatibel met Cloud Service en zorgt ervoor dat een probleem wordt gerapporteerd.

>[!NOTE]
>
>De regel [ Pakketten van de Klant zouden geen knopen onder /libs ](#oakpal-customer-package) moeten creëren of wijzigen altijd van toepassing zijn.

Zie ](/help/implementing/developing/introduction/aem-project-content-package-structure.md) de Structuur van het Project van de Experience Manager 0} {voor meer details.[

### Gebruik geen reverse-replicatiemiddelen {#oakpal-reverse-replication}

* **Sleutel**: ReverseReplication
* **Type**: De Verenigbaarheid van de Code Smell/van de Cloud Service
* **Ernst**: Klein
* **sinds**: Versie 2020.5.0

Steun voor omgekeerde replicatie is niet beschikbaar in de plaatsingen van de Cloud Service, zoals die als deel van Experience Manager as a Cloud Service [ wordt beschreven versienota&#39;s ](/help/release-notes/aem-cloud-changes.md#replication-agents).

De klanten die omgekeerde replicatie gebruiken zouden Adobe voor alternatieve oplossingen moeten contacteren.

### De middelen in volmacht-toegelaten cliëntbibliotheken zouden in een omslag genoemde middelen moeten zijn {#oakpal-resources-proxy}

* **Sleutel**: ClientlibProxyResource
* **Type**: Bug
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

Clientbibliotheken van Experience Managers kunnen statische bronnen bevatten, zoals afbeeldingen en lettertypen. Zoals beschreven in het document [ Gebruikend Voorbewerkers, ](/help/implementing/developing/introduction/clientlibs.md#using-preprocessors) wanneer het gebruiken van pro-xied cliëntbibliotheken moeten deze statische middelen in een kindomslag genoemd `resources` worden bevat om effectief op te worden van verwijzingen voorzien te publiceren instanties.

#### Niet-compatibele code {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### Compatibele code {#compliant-proxy-enabled}

```tet
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### Gebruik van workflowprocessen die niet compatibel zijn met Cloud Servicen {#oakpal-usage-cloud-service}

* **Sleutel**: CloudServiceIncompatibleWorkflowProcess
* **Type**: Bug
* **Ernst**: Belangrijk
* **sinds**: Versie 2021.2.0

Met de overgang naar assetmicro-services voor middelenverwerking op as a Cloud Service Experience Manager zijn verschillende workflowprocessen die werden gebruikt in on-premise- en AMS-versies van Experience Manager, niet ondersteund of overbodig geworden.

Het migratiehulpmiddel in de [ as a Cloud Service bewaarplaats van Assets GitHub van de Experience Manager ](https://github.com/adobe/aem-cloud-migration) kan worden gebruikt om werkschemamodellen tijdens migratie aan as a Cloud Service Experience Manager bij te werken.

### Het gebruik van statische sjablonen wordt afgeraden ten gunste van bewerkbare sjablonen {#oakpal-static-template}

* **Sleutel**: StaticTemplateUsage
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

Terwijl het gebruik van statische malplaatjes historisch algemeen in de projecten van de Experience Manager is, adviseert de Adobe editable malplaatjes omdat zij de meeste flexibiliteit verstrekken en extra eigenschappen steunen die niet in statische malplaatjes aanwezig zijn. Meer informatie kan in het document [ Malplaatjes van de Pagina ](/help/implementing/developing/components/templates.md) worden gevonden.

De migratie van statisch aan editable malplaatjes kan grotendeels worden geautomatiseerd gebruikend de [ Hulpmiddelen van de Modernisering van de Experience Manager ](https://opensource.adobe.com/aem-modernize-tools/).

### Het gebruik van oudere basiscomponenten wordt afgeraden {#oakpal-usage-legacy}

* **Sleutel**: LegacyFoundationComponentUsage
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

De oudere Foundation Components (componenten onder `/libs/foundation`) zijn afgekeurd voor verschillende versies van Experience Managers ten gunste van Core Components. Het gebruik van de Componenten van de Stichting als basis voor douanecomponenten (hetzij door bedekking of erfenis) wordt ontmoedigd en zou in de overeenkomstige Componenten van de Kern moeten worden omgezet.

Deze omzetting kan door de [ Hulpmiddelen van de Modernisering van de Experience Manager ](https://opensource.adobe.com/aem-modernize-tools/) worden vergemakkelijkt.

### Gebruik alleen ondersteunde namen van de uitvoermodi en de volgorde {#oakpal-supported-runmodes}

* **Sleutel**: SupportedRunmode
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

De as a Cloud Service van de Experience Manager dwingt een strikt noemend beleid voor looppas wijzenamen en een strikte het opdracht geven tot voor die looppaswijzen af. De lijst van gesteunde looppaswijzen kan in het document [ worden gevonden die aan Experience Manager as a Cloud Service ](/help/implementing/deploying/overview.md#runmodes) opstelt en om het even welke afwijking van dit wordt geïdentificeerd als kwestie.

### De definitieknooppunten van de de onderzoeksindex van de douane moeten directe kinderen van /oak zijn:index {#oakpal-custom-search}

* **Sleutel**: OakIndexLocation
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

Experience Manager as a Cloud Service vereist dat aangepaste zoekindexdefinities (dat wil zeggen knooppunten van het type `oak:QueryIndexDefinition` ) directe onderliggende knooppunten van `/oak:index` zijn. Indexen op andere locaties moeten worden verplaatst om compatibel te zijn met Experience Manager as a Cloud Service. Meer informatie over onderzoeksindexen kan in het document [ Inhoud Onderzoek en het Indexeren van de Inhoud ](/help/operations/indexing.md) worden gevonden.

### Definitieknooppunten van aangepaste zoekindex moeten een compatVersion van 2 hebben {#oakpal-custom-search-compatVersion}

* **Sleutel**: IndexCompatVersion
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

Experience Manager as a Cloud Service vereist dat voor aangepaste zoekindexdefinities (zoals knooppunten van het type `oak:QueryIndexDefinition` ) de eigenschap `compatVersion` is ingesteld op `2` . Andere waarden worden niet ondersteund door as a Cloud Service Experience Managers. Meer informatie over onderzoeksindexen kan op [ Inhoud het Onderzoek en het Indexeren van de Inhoud ](/help/operations/indexing.md) worden gevonden.

### Afstammende knooppunten van de definitieknooppunten van de aangepaste zoekindex moeten van het type &#39;niet-gestructureerd&#39; zijn {#oakpal-descendent-nodes}

* **Sleutel**: IndexDescendantNodeType
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

Problemen kunnen moeilijk worden opgelost wanneer een definitieknooppunt van een aangepaste zoekindex niet-geordende onderliggende knooppunten bevat. Om deze situatie te voorkomen, wordt aangeraden dat alle afstammende knooppunten van een knooppunt `oak:QueryIndexDefinition` van het type `nt:unstructured` zijn.

### De definitieknooppunten van de onderzoeksindex van de douane moeten een kindknoop genoemd indexRules bevatten die kinderen heeft {#oakpal-custom-search-index}

* **Sleutel**: IndexRulesNode
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

Een correct gedefinieerd definitieknoopknooppunt van een aangepaste zoekindex moet een onderliggend knooppunt met de naam `indexRules` bevatten, dat op zijn beurt minstens één onderliggend knooppunt moet hebben. Meer informatie kan in de [ documentatie van Oak ](https://jackrabbit.apache.org/oak/docs/query/lucene.html) worden gevonden.

### Definitieknooppunten van aangepaste zoekindex moeten de naamgevingsconventies volgen {#oakpal-custom-search-definitions}

* **Sleutel**: IndexName
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

De as a Cloud Service van de Experience Manager vereist dat de definities van de douaneonderzoek (namelijk knopen van type `oak:QueryIndexDefinition`) na een specifiek patroon moeten worden genoemd dat in het document [ wordt beschreven Inhoud Onderzoek en het Indexeren ](/help/operations/indexing.md).

### De de definitieknooppunten van de onderzoeksindex van de douane moeten het indextype Lucene gebruiken  {#oakpal-index-type-lucene}

* **Sleutel**: IndexType
* **Type**: Bug
* **Ernst**: Blocker
* **Sinds**: Versie 2021.2.0 (veranderde type en strengheid in 2021.8.0)

Experience Manager as a Cloud Service vereist dat definities van aangepaste zoekindexen (knooppunten van het type `oak:QueryIndexDefinition` ) een `type` -eigenschap hebben met de waarde ingesteld op `lucene` . Indexering met behulp van verouderde indextypen moet worden bijgewerkt voordat wordt overgeschakeld naar as a Cloud Service Experience Manager. Zie [ Inhoud Onderzoek en het Indexeren ](/help/operations/indexing.md#how-to-use) voor meer informatie.

### Definitieknooppunten van aangepaste zoekindex mogen geen eigenschap met de naam zaad bevatten {#oakpal-property-name-seed}

* **Sleutel**: IndexSeedProperty
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

Experience Manager as a Cloud Service verbiedt aangepaste zoekindexdefinities (knooppunten van het type `oak:QueryIndexDefinition` ) die een eigenschap met de naam `seed` bevatten. Indexering met deze eigenschap moet worden bijgewerkt voordat wordt overgeschakeld naar as a Cloud Service Experience Manager. Zie het document [ Inhoud Onderzoek en het Indexeren ](/help/operations/indexing.md#how-to-use) voor meer informatie.

### Definitie-knooppunten voor aangepaste zoekindex mogen geen eigenschap met de naam reindex bevatten {#oakpal-reindex-property}

* **Sleutel**: IndexReindexProperty
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2021.2.0

Experience Manager as a Cloud Service verbiedt aangepaste zoekindexdefinities (knooppunten van het type `oak:QueryIndexDefinition` ) die een eigenschap met de naam `reindex` bevatten. Indexering met deze eigenschap moet worden bijgewerkt voordat de migratie naar Experience Manager als een
Cloud Service. Zie het document [ Inhoud Onderzoek en het Indexeren ](/help/operations/indexing.md#how-to-use) voor meer informatie.

### Aangepaste DAM-knooppunten voor elementenwinst mogen geen queryPaths opgeven {#oakpal-damAssetLucene-queryPaths}

* **Sleutel**: IndexDamAssetLucene
* **Type**: Bug
* **Ernst**: Blocker
* **sinds**: Versie 2022.1.0

#### Niet-compatibele code {#non-compliant-code-damAssetLucene-queryPaths}

```text
+ oak:index
    + damAssetLucene-1-custom-1
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: [/content/dam]
      - queryPaths: [/content/dam]
      - type: lucene
      + tika
        + config.xml
```

#### Compatibele code {#compliant-code-damAssetLucene-queryPaths}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: [/content/dam]
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Als de definitie van de aangepaste zoekindex compatVersion bevat, moet deze zijn ingesteld op 2 {#oakpal-compatVersion}

* **Sleutel**: IndexCompatVersion
* **Type**: Code Smell
* **Ernst**: Belangrijk
* **sinds**: Versie 2022.1.0


### Indexknooppunt dat &#39;includedPaths&#39; opgeeft, moet ook &#39;queryPaths&#39; met dezelfde waarden opgeven {#oakpal-included-paths-without-query-paths}

* **Sleutel**: IndexIncludedPathsWithoutQueryPaths
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2023.1.0

Voor aangepaste indexen moeten zowel `includedPaths` als `queryPaths` zijn geconfigureerd met identieke waarden. Als één wordt gespecificeerd, moet andere het aanpassen. Er is echter een speciaal geval voor indexen van `damAssetLucene`, inclusief aangepaste versies. U moet hiervoor alleen `includedPaths` opgeven.

### Indexknooppunt dat nodeScopeIndex opgeeft op generiek knooppunttype moet ook includePaths en queryPaths specificeren {#oakpal-full-text-on-generic-node-type}

* **Sleutel**: IndexFulltextOnGenericType
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2023.1.0

Wanneer u de eigenschap `nodeScopeIndex` instelt voor een &quot;algemeen&quot; knooppunttype zoals `nt:unstructured` of `nt:base` , moet u ook de eigenschappen `includedPaths` en `queryPaths` opgeven.
`nt:base` kan als &quot;algemeen&quot;worden beschouwd, aangezien alle knooptypes van het erven. Als u dus een `nodeScopeIndex` on `nt:base` instelt, worden alle knooppunten in de gegevensopslagruimte geïndexeerd. Op dezelfde manier wordt `nt:unstructured` ook beschouwd als &#39;algemeen&#39;, omdat er veel knooppunten in opslagruimten van dit type zijn.

#### Niet-compatibele code {#non-compliant-code-full-text-on-generic-node-type}

```text
+ oak:index/acme.someIndex-custom-1
  - async: [async, nrt]
  - evaluatePathRestrictions: true
  - tags: [visualSimilaritySearch]
  - type: lucene
    + indexRules
      - jcr:primaryType: nt:unstructured
      + nt:base
        - jcr:primaryType: nt:unstructured
        + properties
          + acme.someIndex-custom-1
            - nodeScopeIndex: true
```

#### Compatibele code {#compliant-code-full-text-on-generic-node-type}

```text
+ oak:index/acme.someIndex-custom-1
  - async: [async, nrt]
  - evaluatePathRestrictions: true
  - tags: [visualSimilaritySearch]
  - type: lucene
  - includedPaths: ["/content/dam/"] 
  - queryPaths: ["/content/dam/"]
    + indexRules
      - jcr:primaryType: nt:unstructured
      + nt:base
        - jcr:primaryType: nt:unstructured
        + properties
          + acme.someIndex-custom-1
            - nodeScopeIndex: true
```

### De eigenschap queryLimitReads van de query-engine mag niet worden overschreven {#oakpal-query-limit-reads}

* **Sleutel**: OverrideOfQueryLimitReads
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2023.1.0

Als u de standaardwaarde overschrijft, wordt de pagina zeer traag gelezen, vooral wanneer er meer inhoud wordt toegevoegd.

### Meerdere actieve versies van dezelfde code {#oakpal-multiple-active-versions}

* **Sleutel**: IndexDetectMultipleActiveVersionsOfSameIndex
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2023.1.0

#### Niet-compatibele code {#non-compliant-code-multiple-active-versions}

```text
+ oak:index
  + damAssetLucene-1-custom-1
    ...
  + damAssetLucene-1-custom-2
    ...
  + damAssetLucene-1-custom-3
    ...
```

#### Compatibele code {#compliant-code-multiple-active-versions}

```text
+ damAssetLucene-1-custom-3
    ...
```


### De naam van volledig aangepaste indexdefinities moet in overeenstemming zijn met de officiële richtlijnen {#oakpal-fully-custom-index-name}

* **Sleutel**: IndexValidFullyCustomName
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2023.1.0

Het verwachte patroon voor volledig aangepaste indexnamen is: `[prefix].[indexName]-custom-[version]` . Meer informatie kan in het document [ Inhoud Onderzoek en het Indexeren van de Inhoud ](/help/operations/indexing.md) worden gevonden.

### Dezelfde eigenschap met verschillende geanalyseerde waarden in dezelfde indexdefinitie {#oakpal-same-property-different-analyzed-values}

#### Niet-compatibele code {#non-compliant-code-same-property-different-analyzed-values}

```text
+ indexRules
  + dam:Asset
    + properties
      + status
        - name: status
        - analyzed: true
  + dam:cfVariationNode
    + properties
      + status
        - name: status
```

#### Compatibele code {#compliant-code-same-property-different-analyzed-values}

Voorbeeld:

```text
+ indexRules
  + dam:Asset
    + properties
      + status
        - name: status
        - analyzed: true
  + dam:cfVariationNode
    + properties
      + status
        - name: status
        - analyzed: true
```

Voorbeeld:

```text
+ indexRules
  + dam:Asset
    + properties
      + status
        - name: status
  + dam:cfVariationNode
    + properties
      + status
        - name: status
        - analyzed: true
```

Als de geanalyseerde eigenschap niet expliciet is ingesteld, is de standaardwaarde false.

### Tags, eigenschap {#tags-property}

* **Sleutel**: IndexHasValidTagsProperty
* **Type**: Code Smell
* **Ernst**: Klein
* **sinds**: Versie 2023.1.0

Voor specifieke indexen, zorg ervoor u het markeringsbezit en zijn huidige waarden behoudt. Als u nieuwe waarden toevoegt aan de eigenschap tags, kan het verwijderen van bestaande waarden (of de eigenschap in zijn geheel) leiden tot onverwachte resultaten.

### De knooppunten van de indexdefinitie moeten niet in het inhoudspakket worden opgesteld UI {#oakpal-ui-content-package}

* **Sleutel**: IndexNotUnderUIContent
* **Type**: Verbetering
* **Ernst**: Klein
* **sinds**: Versie 2024.6.0

AEM Cloud Service staat toe dat definities van aangepaste zoekindexen (knooppunten van het type `oak:QueryIndexDefinition` ) niet worden geïmplementeerd in het pakket met UI-inhoud.

>[!WARNING]
>
>U wordt aangespoord om dit zo spoedig mogelijk te richten aangezien het pijpleidingen zal veroorzaken om te ontbreken beginnend met de [ versie van Cloud Manager Augustus 2024 ](/help/implementing/cloud-manager/release-notes/current.md).

### Aangepaste full-text indexdefinitie van type damAssetLucene moet correct worden voorgefixeerd met &#39;damAssetLucene&#39; {#oakpal-dam-asset-lucene}

* **Sleutel**: CustomFulltextIndexesOfTheDamAssetCheck
* **Type**: Verbetering
* **Ernst**: Klein
* **sinds**: Versie 2024.6.0

AEM Cloud Service staat toe dat aangepaste full-text indexdefinities van het type `damAssetLucene` worden voorafgegaan door andere items dan `damAssetLucene` .

>[!WARNING]
>
>U wordt aangespoord om dit zo spoedig mogelijk te richten aangezien het pijpleidingen zal veroorzaken om te ontbreken beginnend met de [ versie van Cloud Manager Augustus 2024 ](/help/implementing/cloud-manager/release-notes/current.md).

### De knooppunten van de indexdefinitie mogen geen eigenschappen met dezelfde naam bevatten {#oakpal-index-property-name}

* **Sleutel**: DuplicateNameProperty
* **Type**: Verbetering
* **Ernst**: Klein
* **sinds**: Versie 2024.6.0

AEM Cloud Service staat definities van aangepaste zoekindexen (knooppunten van het type `oak:QueryIndexDefinition` ) niet toe om eigenschappen met dezelfde naam te bevatten

>[!WARNING]
>
>U wordt aangespoord om dit zo spoedig mogelijk te richten aangezien het pijpleidingen zal veroorzaken om te ontbreken beginnend met de [ versie van Cloud Manager Augustus 2024 ](/help/implementing/cloud-manager/release-notes/current.md).

### Het aanpassen van bepaalde OTB-indexdefinities is verboden {#oakpal-customizing-ootb-index}

* **Sleutel**: RestrictIndexCustomization
* **Type**: Verbetering
* **Ernst**: Klein
* **sinds**: Versie 2024.6.0

AEM Cloud Service staat ongeoorloofde wijzigingen van de volgende OOTB-indexen niet toe:

* `nodetypeLucene`
* `slingResourceResolver`
* `socialLucene`
* `appsLibsLucene`
* `authorizables`
* `pathReference`

>[!WARNING]
>
>U wordt aangespoord om dit zo spoedig mogelijk te richten aangezien het pijpleidingen zal veroorzaken om te ontbreken beginnend met de [ versie van Cloud Manager Augustus 2024 ](/help/implementing/cloud-manager/release-notes/current.md).

### De conkenizers in de analysatoren moeten worden geconfigureerd met de naam &#39;tokenizer&#39;. {#oakpal-tokenizer}

* **Sleutel**: AnalyzerTokenizerConfigCheck
* **Type**: Verbetering
* **Ernst**: Klein
* **sinds**: Versie 2024.6.0

AEM Cloud Service staat het maken van kenizers met onjuiste namen in analysatoren niet toe. Tokenizers moeten altijd als `tokenizer` worden gedefinieerd.

>[!WARNING]
>
>U wordt aangespoord om dit zo spoedig mogelijk te richten aangezien het pijpleidingen zal veroorzaken om te ontbreken beginnend met de [ versie van Cloud Manager Augustus 2024 ](/help/implementing/cloud-manager/release-notes/current.md).

### Configuratie van indexdefinities mag geen spaties bevatten {#oakpal-indexing-definitions-spaces}

* **Sleutel**: PathSpacesCheck
* **Type**: Verbetering
* **Ernst**: Klein
* **sinds**: Versie 2024.7.0

AEM Cloud Service staat het maken van indexeringsdefinities die eigenschappen met spaties bevatten, niet toe.
