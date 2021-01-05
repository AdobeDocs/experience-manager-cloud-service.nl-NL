---
title: Aangepaste regels voor codekwaliteit - Cloud Services
description: Aangepaste regels voor codekwaliteit - Cloud Services
translation-type: tm+mt
source-git-commit: 7fdbdd8bfe80d5f87d9917c905c8d04c4c277534
workflow-type: tm+mt
source-wordcount: '2285'
ht-degree: 6%

---


# Aangepaste regels voor codekwaliteit {#custom-code-quality-rules}


Op deze pagina worden de kwaliteitsregels voor aangepaste code beschreven die worden uitgevoerd door Cloud Manager en die zijn gemaakt op basis van de beste werkwijzen van AEM Engineering.

>[!NOTE]
>De hier opgegeven codevoorbeelden dienen slechts ter illustratie. Zie [Concepten](https://docs.sonarqube.org/7.4/user-guide/concepts/) om over concepten SonarQube en kwaliteitsregels te leren.

## SonarQube-regels {#sonarqube-rules}

In de volgende sectie worden de SonarQube-regels gemarkeerd:

### Gebruik geen potentieel gevaarlijke functies {#do-not-use-potentially-dangerous-functions}

**Sleutel**: CQRules:CWE-676

**Type**: Kwetsbaarheid

**Ernst**: Majoor

**Sinds**: Versie 2018.4.0

De methoden ***Thread.stop()*** en ***Thread.interrupt()*** kunnen problemen veroorzaken die moeilijk te reproduceren zijn en in sommige gevallen beveiligingsproblemen veroorzaken. Het gebruik ervan moet zorgvuldig worden gecontroleerd en gevalideerd. Over het algemeen is het doorgeven van berichten een veiligere manier om vergelijkbare doelen te bereiken.

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

**Sleutel**: CQRules:CWE-134

**Type**: Kwetsbaarheid

**Ernst**: Majoor

**Sinds**: Versie 2018.4.0

Het gebruiken van een formaatkoord van een externe bron (zoals een verzoekparameter of user-generated inhoud) kan een toepassing aan ontkenning van de dienstaanvallen blootstellen. Er zijn omstandigheden waarin een indelingstekenreeks extern kan worden beheerd, maar alleen is toegestaan vanuit vertrouwde bronnen.

#### Niet-compatibele code {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP-aanvragen moeten altijd socket hebben en time-outs verbinden {#http-requests-should-always-have-socket-and-connect-timeouts}

**Sleutel**: CQRules:ConnectionTimeoutMechanism

**Type**: Bug

**Ernst**: Kritiek

**Sinds**: Versie 2018.6.0

Wanneer het uitvoeren van HTTP- verzoeken van binnen een AEM toepassing, is het kritiek om ervoor te zorgen dat juiste onderbrekingen worden gevormd om onnodige draadconsumptie te vermijden. Jammer genoeg, is het standaardgedrag van zowel de standaardHTTP Cliënt van Java (java.net.HttpUrlConnection) als de algemeen gebruikte cliënt van de Componenten van Apache HTTP aan nooit onderbreking, zodat moeten de onderbrekingen uitdrukkelijk worden geplaatst. Bovendien zouden deze onderbrekingen, als beste praktijken, niet meer dan 60 seconden moeten zijn.

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

public void orDoThis() {
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

### Product-API&#39;s die met @ProviderType zijn geannoteerd, mogen niet worden geïmplementeerd of uitgebreid door klanten {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

**Sleutel**: CQBP-84, afhankelijkheden van CQBP-84

**Type**: Bug

**Ernst**: Kritiek

**Sinds**: Versie 2018.7.0

De AEM-API bevat Java-interfaces en -klassen die alleen door aangepaste code mogen worden gebruikt, maar niet geïmplementeerd. De interface *com.day.cq.wcm.api.Page* is bijvoorbeeld ontworpen om ***alleen door AEM*** te worden geïmplementeerd.

Wanneer nieuwe methoden aan deze interfaces worden toegevoegd, beïnvloeden deze aanvullende methoden geen bestaande code die deze interfaces gebruikt en daardoor wordt de toevoeging van nieuwe methoden aan deze interfaces beschouwd als compatibel met eerdere versies. Als echter door aangepaste code één van deze interfaces ***wordt geïmplementeerd***, heeft deze aangepaste code een risico voor compatibiliteit met eerdere versies voor de klant geïntroduceerd.

Interfaces (en klassen) die alleen bedoeld zijn om door AEM te worden geïmplementeerd, worden geannoteerd met *org.osgi.annotation.versioning.ProviderType* (of, in sommige gevallen, een vergelijkbare oudere annotatie *aQute.bnd.annotation.ProviderType*). Deze regel identificeert de gevallen waarin een dergelijke interface wordt uitgevoerd (of een klasse wordt uitgebreid) door douanecode.

#### Niet-compatibele code {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### ResourceResolver-objecten moeten altijd worden gesloten {#resourceresolver-objects-should-always-be-closed}

**Sleutel**: CQRules:CQBP-72

**Type**: Code Smell

**Ernst**: Majoor

**Sinds**: Versie 2018.4.0

ResourceResolver-objecten die zijn verkregen van de ResourceResolverFactory gebruiken systeembronnen. Hoewel er maatregelen op zijn plaats zijn om deze middelen terug te winnen wanneer een ResourceResolver niet meer in gebruik is, is het efficiënter om om het even welke geopende voorwerpen uitdrukkelijk te sluiten ResourceResolver door de close () methode te roepen.

Eén relatief gebruikelijke misvatting is dat ResourceResolver-objecten die zijn gemaakt met een bestaande JCR-sessie, niet expliciet moeten worden gesloten of dat de onderliggende JCR-sessie hierdoor wordt gesloten. Dit is niet het geval - ongeacht hoe een ResourceResolver wordt geopend, zou het moeten worden gesloten wanneer niet meer gebruikt. Aangezien ResourceResolver de Closeable interface uitvoert, is het ook mogelijk om de poging-met-middelen syntaxis in plaats van uitdrukkelijk te gebruiken close().

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

### Gebruik geen servletpaden naar links om servlets te registreren {#do-not-use-sling-servlet-paths-to-register-servlets}

**Sleutel**: CQRules:CQBP-75

**Type**: Code Smell

**Ernst**: Majoor

**Sinds**: Versie 2018.4.0

Zoals beschreven in [Sling documentation](http://sling.apache.org/documentation/the-sling-engine/servlets.html), bindingen serlets door wegen wordt ontmoedigd. Padgebonden servers kunnen geen standaard JCR-toegangsbesturingselementen gebruiken en vereisen daarom extra beveiligingsstrengheid. In plaats van het gebruiken van weg-gebonden servlets, wordt het geadviseerd om knopen in de bewaarplaats tot stand te brengen en servlets te registreren door middeltype.

#### Niet-compatibele code {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### De gevangen Uitzonderingen zouden moeten worden geregistreerd of worden geworpen, maar niet allebei {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

**Sleutel**: CQRules:CQBP-44—CatchAndOrLogOrThrow

**Type**: Code Smell

**Ernst**: Klein

**Sinds**: Versie 2018.4.0

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

### Vermijd het hebben van een logboekverklaring onmiddellijk gevolgd door een throw verklaring {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

**Sleutel**: CQRules:CQBP-44—ConsecutivelyLogAndThrow

**Type**: Code Smell

**Ernst**: Klein

**Sinds**: Versie 2018.4.0

Een ander gemeenschappelijk patroon te vermijden is een bericht te registreren en dan onmiddellijk een uitzondering te werpen. Dit geeft doorgaans aan dat het uitzonderingsbericht uiteindelijk wordt gedupliceerd in logbestanden.

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

### Meld u niet aan bij INFO bij het verwerken van GET- of HEAD-verzoeken {#avoid-logging-at-info-when-handling-get-or-head-requests}

**Sleutel**: CQRules:CQBP-44—LogInfoInGetOrHeadRequests

**Type**: Code Smell

**Ernst**: Klein

In het algemeen, zou het INFO logboekniveau moeten worden gebruikt om belangrijke acties te afbakenen en, door gebrek, AEM wordt gevormd om bij het INFO niveau of boven te registreren. GET- en HEAD-methoden mogen nooit alleen-lezen zijn en vormen dus geen belangrijke acties. Het registreren op het niveau INFO in antwoord op GET of HEAD verzoeken zal waarschijnlijk tot significante logboeklawaai leiden daardoor het moeilijker maken om nuttige informatie in logboekdossiers te identificeren. Het registreren wanneer de behandeling van GET of HEAD- verzoeken of op de niveaus van de WAARSCHUWING of van de FOUT zou moeten zijn wanneer iets verkeerd is gegaan of op de niveaus DEBUG of van de TRACE als de diepere het oplossen van problemeninformatie nuttig zou zijn.

>[!CAUTION]
>
>Dit is niet op access.log-type registreren voor elke verzoeken van toepassing.

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

**Sleutel**: CQRules:CQBP-44—ExceptionGetMessageIsFirstLogParam

**Type**: Code Smell

**Ernst**: Klein

**Sinds**: Versie 2018.4.0

Als beste praktijken, zouden de logboekberichten contextuele informatie over moeten verstrekken waar in de toepassing een uitzondering is voorgekomen. Hoewel de context ook door het gebruik van stapelsporen kan worden bepaald, over het algemeen zal het logboekbericht gemakkelijker zijn te lezen en te begrijpen. Dientengevolge, wanneer het registreren van een uitzondering, is het een slechte praktijk om het bericht van de uitzondering als logboekbericht te gebruiken - het uitzonderingsbericht zal bevatten wat verkeerd ging terwijl het logboekbericht zou moeten worden gebruikt om een logboeklezer te vertellen wat de toepassing deed toen de uitzondering gebeurde. Het uitzonderingsbericht zal nog worden geregistreerd; door uw eigen bericht te specificeren zullen de logboeken eenvoudig te begrijpen zijn.

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

### Login vangstblokken zou op het WARN of FOUTniveau {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level} moeten zijn

**Sleutel**: CQRules:CQBP-44—WrongLogLevelInCatchBlock

**Type**: Code Smell

**Ernst**: Klein

**Sinds**: Versie 2018.4.0

Zoals de naam suggereert, zouden de uitzonderingen van Java altijd in *uitzonderlijke* omstandigheden moeten worden gebruikt. Dientengevolge, wanneer een uitzondering wordt gevangen, is het belangrijk om ervoor te zorgen dat de logboekberichten op het aangewezen niveau - of WARN of FOUT worden geregistreerd. Dit zorgt ervoor dat die berichten correct in de logboeken verschijnen.

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

### Stapelsporen niet afdrukken naar de console {#do-not-print-stack-traces-to-the-console}

**Sleutel**: CQRules:CQBP-44—ExceptionPrintStackTrace

**Type**: Code Smell

**Ernst**: Klein

**Sinds**: Versie 2018.4.0

Zoals vermeld, is de context kritiek wanneer het begrip van logboekberichten. Wanneer u Exception.printStackTrace() gebruikt, wordt **only** de stacktracering uitgevoerd naar de standaardfoutenstream, waardoor alle context verloren gaat. Bovendien kunnen in een multithread-toepassing, zoals AEM, meerdere uitzonderingen parallel met deze methode worden afgedrukt, de stacksporen ervan overlappen, wat tot grote verwarring leidt. De uitzonderingen zouden door het registrerenkader slechts moeten worden geregistreerd.

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

### Uitvoer niet uitvoeren naar standaarduitvoer of standaardfout {#do-not-output-to-standard-output-or-standard-error}

**Sleutel**: CQRules:CQBP-44—LogLevelConsolePrinters

**Type**: Code Smell

**Ernst**: Klein

**Sinds**: Versie 2018.4.0

Het registreren in AEM zou altijd door het registrerenkader (SLF4J) moeten worden gedaan. De uitvoer rechtstreeks naar de standaardoutput of de standaardfoutenstromen verliest de structurele en contextafhankelijke informatie die door het registrerenkader wordt verstrekt en kan, in sommige gevallen, prestatieskwesties veroorzaken.

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

### Hardcoded /apps en /libs-paden voorkomen {#avoid-hardcoded-apps-and-libs-paths}

**Sleutel**: CQRules:CQBP-71

**Type**: Code Smell

**Ernst**: Klein

**Sinds**: Versie 2018.4.0

In het algemeen moeten paden die beginnen met /libs en /apps niet worden gecodeerd omdat de paden waarnaar ze verwijzen het meest worden opgeslagen als paden ten opzichte van het zoekpad Sling (dat standaard is ingesteld op /libs/apps). Het gebruik van het absolute pad kan leiden tot subtiele defecten die pas later in de levenscyclus van het project verschijnen.

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

### Verschuivende planner mag niet worden gebruikt {#sonarqube-sling-scheduler}

**Sleutel**: CQRules:AMSCORE-554

**Type**: Compatibiliteit van code met Cloud Service/Smal

**Ernst**: Klein

**Sinds**: Versie 2020.5.0

De Planner van de Verkoop moet niet voor taken worden gebruikt die een gewaarborgde uitvoering vereisen. Het verkopen van Geplande Banen garandeert uitvoering en beter geschikt voor zowel gegroepeerde als niet-gegroepeerde milieu&#39;s.

Raadpleeg [Apache Sling Event en Job Handling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) voor meer informatie over de manier waarop saldertaken worden uitgevoerd in een geclusterde omgeving.

### AEM verouderde API&#39;s mogen niet worden gebruikt {#sonarqube-aem-deprecated}

**Sleutel**: AMSCORE-553

**Type**: Compatibiliteit van code met Cloud Service/Smal

**Ernst**: Klein

**Sinds**: Versie 2020.5.0

Het AEM API-oppervlak wordt voortdurend herzien om te bepalen voor welke API&#39;s het gebruik wordt ontmoedigd en dus als afgekeurd wordt beschouwd.

In veel gevallen worden deze API&#39;s vervangen door de standaard Java *@Deprecated*-annotatie en, als zodanig, zoals bepaald door `squid:CallToDeprecatedMethod`.

Er zijn echter gevallen waarin een API afgekeurd is in de context van AEM, maar in andere contexten niet mag worden afgekeurd. Deze regel identificeert deze tweede klasse.

## Inhoudsregels voor OakPAL {#oakpal-rules}

U vindt hieronder de OakPAL-controles die zijn uitgevoerd door Cloud Manager.

>[!NOTE]
>OakPAL is een kader dat door een AEM Partner (en winnaar van 2019 AEM Rockstar North America) wordt ontwikkeld die inhoudspakketten valideert met behulp van een standalone Oak-opslagplaats.

### Klantpakketten moeten geen knooppunten maken of wijzigen onder /libs {#oakpal-customer-package}

**Sleutel**: BannedPaths

**Type**: Bug

**Ernst**: Blocker

**Sinds**: Versie 2019.6.0

Het is een al lang bestaande beste praktijk geweest dat de /libs inhoudsboom in de AEM inhoudsbewaarplaats als read-only door klanten zou moeten worden beschouwd. Als u knooppunten en eigenschappen wijzigt onder */libs*, ontstaat een aanzienlijk risico voor belangrijke en kleine updates. Wijzigingen in */libs* mogen alleen via officiële kanalen door Adobe worden aangebracht.

### Pakketten mogen geen dubbele OSGi-configuraties bevatten {#oakpal-package-osgi}

**Sleutel**: DuplicateOsgiConfigurations

**Type**: Bug

**Ernst**: Majoor

**Sinds**: Versie 2019.6.0

Een gemeenschappelijk probleem dat op complexe projecten voorkomt is waar de zelfde component OSGi veelvoudige tijden wordt gevormd. Dit leidt tot een dubbelzinnigheid over welke configuratie zal opereerbaar zijn. Deze regel is &quot;runmode-bewust&quot;in die zin dat het slechts kwesties zal identificeren waar de zelfde component veelvoudige tijden op de zelfde runmode (of combinatie runmodes) wordt gevormd.

#### Niet-compatibele code {#non-compliant-code-osgi}

```+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Compatibele code {#compliant-code-osgi}

```+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Mappen configureren en installeren mag alleen OSGi-knooppunten {#oakpal-config-install} bevatten

**Sleutel**: ConfigAndInstallShouldOnlyContainOsgiNodes

**Type**: Bug

**Ernst**: Majoor

**Sinds**: Versie 2019.6.0

Om veiligheidsredenen, zijn de wegen die */config/ en /install/* bevatten slechts leesbaar door administratieve gebruikers in AEM en zouden slechts voor OSGi- configuratie en OSGi- bundels moeten worden gebruikt. Als u andere typen inhoud onder paden plaatst die deze segmenten bevatten, resulteert dit in toepassingsgedrag dat per ongeluk verschilt tussen gebruikers met en zonder beheerdersrechten.

Een veelvoorkomend probleem is het gebruik van knooppunten met de naam `config` in componentdialoogvensters of wanneer u de configuratie van de rich text editor opgeeft voor inlinebewerking. Om dit op te lossen zou de beledigende knoop aan een volgzame naam moeten worden anders genoemd. Voor de rijke configuratie van de tekstredacteur maak gebruik van het `configPath` bezit op `cq:inplaceEditing` knoop om de nieuwe plaats te specificeren.

#### Niet-compatibele code {#non-compliant-code-config-install}

```
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Compatibele code {#compliant-code-config-install}

```
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### Pakketten mogen {#oakpal-no-overlap} niet overlappen

**Sleutel**: PackageOverlaps

**Type**: Bug

**Ernst**: Majoor

**Sinds**: Versie 2019.6.0

Gelijkaardig aan *de Pakketten zouden Duplicate OSGi Configurations* niet moeten bevatten is dit een gemeenschappelijk probleem op complexe projecten waar de zelfde knoopweg aan door veelvoudige afzonderlijke inhoudspakketten wordt geschreven. Terwijl het gebruiken van inhoudspakketgebiedsdelen kan worden gebruikt om een verenigbaar resultaat te verzekeren, is het beter om overlappingen volledig te vermijden.

### Standaardontwerpmodus mag geen klassieke UI {#oakpal-default-authoring} zijn

**Sleutel**: ClassicUIAuthoringMode

**Type**: Compatibiliteit van code met Cloud Service/Smal

**Ernst**: Klein

**Sinds**: Versie 2020.5.0

De configuratie OSGi `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` bepaalt de standaard auteurswijze binnen AEM. Aangezien Klassieke UI sinds AEM 6.4 is afgekeurd, zal een kwestie nu worden opgeheven wanneer de standaard auteurswijze aan Klassieke UI wordt gevormd.

### Componenten met dialoogvensters moeten dialoogvensters met aanraakinterface hebben {#oakpal-components-dialogs}

**Sleutel**: ComponentWithOnlyClassicUIDialog

**Type**: Compatibiliteit van code met Cloud Service/Smal

**Ernst**: Klein

**Sinds**: Versie 2020.5.0

AEM Componenten die een Klassieke UI dialoog hebben zouden altijd een overeenkomstige dialoog van de Aanraking UI moeten hebben zowel om een optimale auteurservaring te verstrekken als met het de plaatsingsmodel van de Cloud Service compatibel te zijn, waar Klassieke UI niet wordt gesteund. Deze regel verifieert de volgende scenario&#39;s:

* Een component met een Klassieke dialoog UI (namelijk een dialoog kindknoop) moet een overeenkomstige dialoog van de Aanraking UI (namelijk een `cq:dialog` kindknoop) hebben.
* Een component met een Klassieke UI-ontwerpdialoogvenster (d.w.z. een design_dialog-knooppunt) moet een overeenkomend dialoogvenster voor het aanraakinterface-ontwerp hebben (dat wil zeggen een `cq:design_dialog` onderliggende node).
* Een component met zowel een dialoogvenster voor klassieke gebruikersinterface als een dialoogvenster voor klassieke gebruikersinterface moet zowel een corresponderend dialoogvenster voor aanraakinterface als een overeenkomstig dialoogvenster voor aanraakgebruikersinterface hebben.

De documentatie van de Hulpmiddelen van de Modernisering van de AEM verstrekt documentatie en tooling voor hoe te om componenten van Klassieke UI in Aanraakinterface om te zetten. Raadpleeg [De AEM Moderniseringsgereedschappen](https://opensource.adobe.com/aem-modernize-tools/pages/tools.html) voor meer informatie.

### Pakketten mogen geen Mutable en Onveranderbare Inhoud {#oakpal-packages-immutable} mengen

**Sleutel**: ImmutableMutableMixedPackage

**Type**: Compatibiliteit van code met Cloud Service/Smal

**Ernst**: Klein

**Sinds**: Versie 2020.5.0

Om compatibel te zijn met het implementatiemodel van de Cloud Service, moeten afzonderlijke inhoudspakketten ofwel inhoud bevatten voor de onveranderlijke gebieden van de opslagplaats (dat wil zeggen dat `/apps and /libs, although /libs` niet door klantcode moet worden gewijzigd en een afzonderlijke schending veroorzaakt) of het veranderbare gebied (dat wil zeggen, alles anders), maar niet beide. Een pakket met zowel `/apps/myco/components/text and /etc/clientlibs/myco` is bijvoorbeeld niet compatibel met Cloud Service en zorgt ervoor dat een probleem wordt gerapporteerd.

Raadpleeg [AEM Projectstructuur](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) voor meer informatie.

### Reverse Replication Agents should not be used {#oakpal-reverse-replication}

**Sleutel**: ReverseReplication

**Type**: Compatibiliteit van code met Cloud Service/Smal

**Ernst**: Klein

**Sinds**: Versie 2020.5.0

Ondersteuning voor omgekeerde replicatie is niet beschikbaar in Cloud Service-implementaties, zoals beschreven in [Opmerkingen bij de release: Verwijderen van Replication Agents](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/release-notes/aem-cloud-changes.html#replication-agents).

De klanten die omgekeerde replicatie gebruiken zouden Adobe voor alternatieve oplossingen moeten contacteren.

