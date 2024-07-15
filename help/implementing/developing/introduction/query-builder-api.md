---
title: Query Builder-API
description: De functionaliteit van de Asset Share Query Builder wordt weergegeven via een Java&trade; API en een REST API.
exl-id: d5f22422-c9da-4c9d-b81c-ffa5ea7cdc87
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1830'
ht-degree: 0%

---

# Query Builder-API {#query-builder-api}

De Bouwer van de Vraag biedt een gemakkelijke manier om de inhoudsbewaarplaats van AEM te vragen. De functionaliteit wordt beschikbaar gemaakt via een Java™ API en een REST API. In dit document worden deze API&#39;s beschreven.

De server-zijvraagbouwer ([`QueryBuilder` ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html)) keurt een vraagbeschrijving goed, creeert en stelt een vraag van XPath in werking, naar keuze filter de resultaatreeks, en ook haalt facetten, indien gewenst.

De vraagbeschrijving is eenvoudig een reeks predikaten ([`Predicate` ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/Predicate.html)). Voorbeelden zijn een voorspelling in volledige tekst, die overeenkomt met de functie `jcr:contains()` in XPath.

Voor elk predikaat type, is er een beoordelaarcomponent ([`PredicateEvaluator` ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html)) die weet hoe te om dat specifieke predikaat voor XPath, het filtreren, en facetextractie te behandelen. Het is gemakkelijk om douanebeoordelaars tot stand te brengen, die door componenten OSGi runtime gestopt zijn.

De REST API biedt toegang tot dezelfde functies via HTTP, waarbij reacties worden verzonden in JSON.

>[!NOTE]
>
>De API van QueryBuilder wordt gebouwd gebruikend JCR API. U kunt ook een query uitvoeren op de AEM JCR door de JCR API te gebruiken vanuit een OSGi-bundel. Voor informatie, zie [ het Vragen van de Gegevens van Adobe Experience Manager gebruikend JCR API ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/query-builder/querybuilder-api.html).

## Gem-sessie {#gem-session}

[ AEM Gems ](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/overview.html) is een reeks technische diepe duiken in Adobe Experience Manager die door de deskundigen van de Adobe worden geleverd.

U kunt [ de zitting herzien die aan de vraagbouwer ](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/gems2017/aem-search-forms-using-querybuilder.html) voor een overzicht en gebruik van het hulpmiddel wordt gewijd.

## Voorbeeldquery&#39;s {#sample-queries}

Deze voorbeelden worden gegeven in de stijlnotatie van Java™-eigenschappen. Als u deze wilt gebruiken met de Java™ API, gebruikt u een Java™ `HashMap` zoals in het volgende API-voorbeeld.

Voor de `QueryBuilder` JSON Servlet, omvat elk voorbeeld een steekproefverbinding aan een AEM installatie (bij de standaardplaats, `http://<host>:<port>`). Meld u aan bij uw AEM voordat u deze koppelingen gebruikt.

>[!CAUTION]
>
>Standaard geeft de JSON-servlet van de querybuilder maximaal tien resultaten weer.
>
>Als u de volgende parameter toevoegt, kan de servlet alle queryresultaten weergeven:
>
>`p.limit=-1`

>[!NOTE]
>
>Als u de geretourneerde JSON-gegevens in uw browser wilt weergeven, kunt u een plug-in gebruiken, zoals JSONView voor Firefox.

### Alle resultaten retourneren {#returning-all-results}

De volgende vraag **keert tien resultaten** (of om precies te zijn, een maximum van tien) terug, maar informeert u van het **Aantal hits:** dat beschikbaar is:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
orderby=path
```

De zelfde vraag (met de parameter `p.limit=-1`) **keert alle resultaten** terug (het zou een hoog aantal afhankelijk van uw instantie kunnen zijn):

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path&p.limit=-1`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
p.limit=-1
orderby=path
```

### Het gebruiken van p.radenTotal om de Resultaten terug te keren {#using-p-guesstotal-to-return-the-results}

Het doel van de parameter `p.guessTotal` is om het juiste aantal resultaten te retourneren dat kan worden weergegeven door de minimaal haalbare waarden `p.offset` en `p.limit` te combineren. Het voordeel van deze parameter is dat de prestaties van grote resultaatsets verbeterd zijn. Met deze parameter wordt ook vermeden dat het volledige totaal wordt berekend (bijvoorbeeld door `result.getSize()` aan te roepen) en dat de volledige resultaatset wordt gelezen, die tot op de Oak-engine en -index is geoptimaliseerd. Dit proces kan een significant verschil zijn wanneer er honderdduizenden resultaten zijn, zowel in uitvoeringstijd als in geheugengebruik.

Het nadeel van de parameter is dat gebruikers het exacte totaal niet zien. Maar u kunt een minimumaantal zoals `p.guessTotal=1000` plaatsen zodat het altijd tot 1000 leest. Op deze manier krijgt u exacte totalen voor kleinere resultaatsets, maar als het meer is, kunt u alleen &quot;en meer&quot; tonen.

Voeg `p.guessTotal=true` toe aan de onderstaande query om te zien hoe deze werkt:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=true&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
p.guessTotal=true
orderby=path
```

De query retourneert de `p.limit` standaardwaarde van `10` resultaten met een `0` -verschuiving:

```xml
"success": true,
"results": 10,
"total": 10,
"more": true,
"offset": 0,
```

U kunt ook een numerieke waarde gebruiken om tot een aangepast aantal maximumresultaten te tellen. Gebruik dezelfde query als hierboven, maar wijzig de waarde van `p.guessTotal` in `50` :

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=50&orderby=path`

Het keert een aantal de zelfde standaardgrens van 10 resultaten met een 0 compensatie terug, maar toont slechts een maximum van 50 resultaten:

```xml
"success": true,
"results": 10,
"total": 50,
"more": true,
"offset": 0,
```

### Paginering implementeren {#implementing-pagination}

Door gebrek zou de Bouwer van de Vraag ook het aantal treffers verstrekken. Afhankelijk van de resultaatgrootte, zou dit aantal lange tijd kunnen vergen aangezien het bepalen van de nauwkeurige telling het controleren van elk resultaat voor toegangsbeheer impliceert. Meestal wordt het totaal gebruikt om paginering voor de eindgebruiker UI uit te voeren. Aangezien het bepalen van de nauwkeurige telling langzaam kan zijn, wordt geadviseerd dat u de gokTotal eigenschap gebruikt om de paginering uit te voeren.

De interface kan bijvoorbeeld de volgende benadering aanpassen:

* Krijg en toon de nauwkeurige telling van het aantal totale treffers ([ SearchResult.getTotalMatches () ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/result/SearchResult.html#getTotalMatches) of totaal in de `querybuilder.json` reactie) zijn minder dan of gelijk aan 100;
* Stel `guessTotal` in op 100 om de Query Builder aan te roepen.

* De reactie kan het volgende resultaat hebben:

   * `total=43` , `more=false` - Geeft aan dat het totale aantal hits 43 is. De interface kan tot tien resultaten als deel van de eerste pagina tonen en paginering voor de volgende drie pagina&#39;s verstrekken. U kunt deze implementatie ook gebruiken om een beschrijvende tekst zoals **&quot;43 gevonden resultaten&quot;te tonen**.
   * `total=100` , `more=true` - Geeft aan dat het totale aantal treffers groter is dan 100 en dat het exacte aantal niet bekend is. De interface kan maximaal tien pagina&#39;s weergeven als onderdeel van de eerste pagina en paginering voor de volgende tien pagina&#39;s bieden. U kunt deze eigenschap ook gebruiken om een tekst als **&quot;meer dan 100 gevonden resultaten&quot;te tonen**. Wanneer de gebruiker naar de volgende pagina&#39;s gaat, wordt bij aanroepen naar de Query Builder de limiet van `guessTotal` en ook van de parameters `offset` en `limit` verhoogd.

Gebruik `guessTotal` ook in gevallen waarin de gebruikersinterface oneindig schuiven moet gebruiken om te voorkomen dat de Query Builder het exacte aantal treffers bepaalt.

### JAR-bestanden zoeken en bestellen, nieuwste eerst {#find-jar-files-and-order-them-newest-first}

`http://<host>:<port>/bin/querybuilder.json?type=nt:file&nodename=*.jar&orderby=@jcr:content/jcr:lastModified&orderby.sort=desc`

```xml
type=nt:file
nodename=*.jar
orderby=@jcr:content/jcr:lastModified
orderby.sort=desc
```

### Alle pagina&#39;s zoeken en deze bestellen op Laatst gewijzigd {#find-all-pages-and-order-them-by-last-modified}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
```

### Alle pagina&#39;s zoeken en deze bestellen op Laatst gewijzigd, Aflopend {#find-all-pages-and-order-them-by-last-modified-but-descending}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified&orderby.sort=desc`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
orderby.sort=desc
```

### fullText-zoekopdracht, besteld door score {#fulltext-search-ordered-by-score}

`http://<host>:<port>/bin/querybuilder.json?fulltext=Management&orderby=@jcr:score&orderby.sort=desc`

```xml
fulltext=Management
orderby=@jcr:score
orderby.sort=desc
```

### Zoeken naar pagina&#39;s met een bepaalde tag {#search-for-pages-tagged-with-a-certain-tag}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&tagid=wknd:activity/cycling&tagid.property=jcr:content/cq:tags`

```xml
type=cq:Page
tagid=wknd:activity/cycling
tagid.property=jcr:content/cq:tags
```

Gebruik `tagid` predikaat zoals in het voorbeeld als u expliciete markering ID kent.

Gebruik `tag` prepress voor de weg van de markeringstitel (zonder ruimten).

In het vorige voorbeeld, omdat u naar pagina&#39;s (`cq:Page` knopen) zoekt, gebruik de relatieve weg van die knoop voor `tagid.property` predikaat, die `jcr:content/cq:tags` is. De standaardwaarde is `tagid.property` dan `cq:tags` .

### Meerdere paden zoeken (met groepen) {#search-under-multiple-paths-using-groups}

`http://<host>:<port>/bin/querybuilder.json?fulltext=Experience&group.1_path=/content/wknd/us/en/magazine&group.2_path=/content/wknd/us/en/adventures&group.p.or=true`

```xml
fulltext=Experience
group.p.or=true
group.1_path=/content/wknd/us/en/magazine
group.2_path=/content/wknd/us/en/adventures
```

Deze vraag gebruikt a *groep* (genoemd `group`), die handelt om subexpressies binnen een vraag te afbakenen, veel zoals haakjes in meer standaardnota&#39;s doen. Bijvoorbeeld, zou de vorige vraag in een meer bekende stijl als kunnen worden uitgedrukt:

`"Experience" and ("/content/wknd/us/en/magazine" or "/content/wknd/us/en/adventures")`

Binnen de groep in het voorbeeld wordt de voorspelling `path` meerdere keren gebruikt. Als u de twee instanties van de voorspelling wilt onderscheiden en rangschikken (de volgorde is vereist voor sommige voorspellen), moet u de voorspelling voorschrijven met `N_` waar `N` de volgorde-index is. In het vorige voorbeeld zijn de resulterende voorspellingen `1_path` en `2_path` .

`p` in `p.or` is een speciaal afbakening erop wijst die dat wat volgt (in dit geval een `or`) a *parameter* van de groep, in tegenstelling tot een subpredikaat van de groep, zoals `1_path` is.

Als er geen `p.or` wordt gegeven, dan zijn alle voorspellingen ANDed samen, dat wil zeggen, elk resultaat moet aan alle voorspellingen voldoen.

>[!NOTE]
>
>U kunt niet hetzelfde numerieke voorvoegsel in één query gebruiken, zelfs niet voor verschillende voorspellingen.

### Zoeken naar eigenschappen {#search-for-properties}

Hier zoekt u naar alle pagina&#39;s van een bepaalde sjabloon met de eigenschap `cq:template` :

`http://<host>:<port>/bin/querybuilder.json?property=cq%3atemplate&property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&type=cq%3aPageContent`

```xml
type=cq:PageContent
property=cq:template
property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
```

Het nadeel is dat de `jcr:content` knooppunten van de pagina&#39;s, niet de pagina&#39;s zelf, worden geretourneerd. U kunt dit probleem oplossen door te zoeken op een relatief pad:

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3acontent%2fcq%3atemplate&property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&type=cq%3aPage`

```xml
type=cq:Page
property=jcr:content/cq:template
property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
```

### Meerdere eigenschappen zoeken {#search-for-multiple-properties}

Wanneer het gebruiken van het bezit voorspelt veelvoudige tijden, moet u de aantalprefixen opnieuw toevoegen:

`http://<host>:<port>/bin/querybuilder.json?1_property=jcr%3acontent%2fcq%3atemplate&1_property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&2_property=jcr%3acontent%2fjcr%3atitle&2_property.value=Cycling%20Tuscany&type=cq%3aPage`

```xml
type=cq:Page
1_property=jcr:content/cq:template
1_property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
2_property=jcr:content/jcr:title
2_property.value=Cycling Tuscany
```

### Meerdere eigenschapswaarden zoeken {#search-for-multiple-property-values}

Om grote groepen te vermijden wanneer u naar veelvoudige waarden van een bezit (`"A" or "B" or "C"`) wilt zoeken, kunt u veelvoudige waarden aan `property` verstrekken predikaat:

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3atitle&property.1_value=Cycling%20Tuscany&property.2_value=Ski%20Touring&property.3_value=Whistler%20Mountain%20Biking`

```xml
property=jcr:title
property.1_value=Cycling Tuscany
property.2_value=Ski Touring
property.3_value=Whistler Mountain Biking
```

Voor eigenschappen met meerdere waarden kunt u ook vereisen dat meerdere waarden overeenkomen (`"A" and "B" and "C"`):

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3atitle&property.and=true&property.1_value=Cycling%20Tuscany&property.2_value=Ski%20Touring&property.3_value=Whistler%20Mountain%20Biking`

```xml
property=jcr:title
property.and=true
property.1_value=Cycling Tuscany
property.2_value=Ski Touring
property.3_value=Whistler Mountain Biking
```

## Wat wordt geretourneerd, verfijnen {#refining-what-is-returned}

Door gebrek, keert QueryBuilder JSON Servlet een standaardreeks eigenschappen voor elke knoop in het onderzoeksresultaat (bijvoorbeeld, weg, naam, en titel) terug. Als u de controle wilt verkrijgen over de eigenschappen die worden geretourneerd, kunt u een van de volgende handelingen uitvoeren:

Opgeven

```xml
p.hits=full
```

In dat geval worden alle eigenschappen opgenomen voor elk knooppunt:

`http://<host>:<port>/bin/querybuilder.json?p.hits=full&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=full
```

Gebruiken

```xml
p.hits=selective
```

Geef de eigenschappen op die u wilt ophalen

```xml
p.properties
```

Gescheiden door een spatie:

`http://<host>:<port>/bin/querybuilder.json?p.hits=selective&p.properties=sling%3aresourceType%20jcr%3aprimaryType&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=selective
p.properties=sling:resourceType jcr:primaryType
```

Een ander ding u kunt doen is kindknopen in de reactie van de Bouwer van de Vraag omvatten. Opgeven

```xml
p.nodedepth=n
```

Waar `n` het aantal niveaus is dat u de vraag wilt terugkeren. Als een onderliggende node moet worden geretourneerd, moet deze worden opgegeven door de eigenschappenkiezer

```xml
p.hits=full
```

Voorbeeld:

`http://<host>:<port>/bin/querybuilder.json?p.hits=full&p.nodedepth=5&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=full
p.nodedepth=5
```

## Meer voorspellingen {#morepredicates}

Voor meer predikaten, zie de [ Vooraf ingestelde pagina van de Verwijzing van de Bouwer van de Vraag ](query-builder-predicates.md).

U kunt [ Javadoc voor de `PredicateEvaluator` klassen ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html) ook controleren. Javadoc voor deze klassen bevat de lijst met eigenschappen die u kunt gebruiken.

De prefix van de klassennaam (bijvoorbeeld, `similar` in [`SimilarityPredicateEvaluator` ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/SimilarityPredicateEvaluator.html)) is het *belangrijkste bezit* van de klasse. Dit bezit is ook de naam van predikaat aan gebruik in de vraag (in kleine letters).

Voor dergelijke belangrijkste eigenschappen kunt u de query verkorten en `similar=/content/en` gebruiken in plaats van de volledig gekwalificeerde variant `similar.similar=/content/en` . Het volledig gekwalificeerde formulier moet worden gebruikt voor alle niet-hoofdeigenschappen van een klasse.

## Voorbeeld API-gebruik van Query Builder {#example-query-builder-api-usage}

```java
   String fulltextSearchTerm = "WKND";

    // create query description as hash map (simplest way, same as form post)
    Map<String, String> map = new HashMap<String, String>();

// create query description as hash map (simplest way, same as form post)
    map.put("path", "/content");
    map.put("type", "cq:Page");
    map.put("group.p.or", "true"); // combine this group with OR
    map.put("group.1_fulltext", fulltextSearchTerm);
    map.put("group.1_fulltext.relPath", "jcr:content");
    map.put("group.2_fulltext", fulltextSearchTerm);
    map.put("group.2_fulltext.relPath", "jcr:content/@cq:tags");

    // can be done in map or with Query methods
    map.put("p.offset", "0"); // same as query.setStart(0) below
    map.put("p.limit", "20"); // same as query.setHitsPerPage(20) below

    Query query = builder.createQuery(PredicateGroup.create(map), session);
    query.setStart(0);
    query.setHitsPerPage(20);

    SearchResult result = query.getResult();

    // paging metadata
    int hitsPerPage = result.getHits().size(); // 20 (set above) or lower
    long totalMatches = result.getTotalMatches();
    long offset = result.getStartIndex();
    long numberOfPages = totalMatches / 20;

    //Place the results in XML to return to client
    DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
    DocumentBuilder builder = factory.newDocumentBuilder();
    Document doc = builder.newDocument();

    //Start building the XML to pass back to the AEM client
    Element root = doc.createElement( "results" );
    doc.appendChild( root );

    // iterating over the results
for (Hit hit : result.getHits()) {
       String path = hit.getPath();

      //Create a result element
      Element resultel = doc.createElement( "result" );
      root.appendChild( resultel );

      Element pathel = doc.createElement( "path" );
      pathel.appendChild( doc.createTextNode(path ) );
      resultel.appendChild( pathel );
    }
```

Dezelfde query die via HTTP wordt uitgevoerd met de Query Builder (JSON) Servlet:

`http://<host>:<port>/bin/querybuilder.json?path=/content&type=cq:Page&group.p.or=true&group.1_fulltext=WKND&group.1_fulltext.relPath=jcr:content&group.2_fulltext=WKND&group.2_fulltext.relPath=jcr:content/@cq:tags&p.offset=0&p.limit=20`

## Query&#39;s opslaan en laden {#storing-and-loading-queries}

U kunt query&#39;s opslaan in de opslagplaats, zodat u ze later kunt gebruiken. In `QueryBuilder` wordt de methode `storeQuery` voorzien van de volgende handtekening:

```java
void storeQuery(Query query, String path, boolean createFile, Session session) throws RepositoryException, IOException;
```

Wanneer u de methode [`QueryBuilder#storeQuery` ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html#storeQuery-com.day.cq.search.Query-java.lang.String-boolean-javax.jcr.Session-) gebruikt, wordt de gegeven `Query` in de opslagplaats opgeslagen als een bestand of als een eigenschap volgens de argumentwaarde `createFile` . In het volgende voorbeeld wordt getoond hoe u een `Query` als bestand opslaat naar het pad `/mypath/getfiles` :

```java
builder.storeQuery(query, "/mypath/getfiles", true, session);
```

Om het even welke eerder opgeslagen vragen kunnen van de bewaarplaats worden geladen door de [`QueryBuilder#loadQuery` ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html#loadQuery-java.lang.String-javax.jcr.Session-) methode te gebruiken:

```java
Query loadQuery(String path, Session session) throws RepositoryException, IOException
```

Een `Query` opgeslagen naar het pad `/mypath/getfiles` kan bijvoorbeeld door het volgende fragment worden geladen:

```java
Query loadedQuery = builder.loadQuery("/mypath/getfiles", session);
```

## Testen en fouten opsporen {#testing-and-debugging}

Voor het spelen rond en het zuiveren van de vragen van de Bouwer van de Vraag, kunt u de debugger console van de Bouwer van de Vraag gebruiken bij

`http://<host>:<port>/libs/cq/search/content/querydebug.html`

Of anders de Query Builder JSON servlet op

`http://<host>:<port>/bin/querybuilder.json?path=/tmp`

De `path=/tmp` is alleen een voorbeeld.

### Algemene foutopsporing in Recommendations {#general-debugging-recommendations}

### Uitleg XPath verkrijgen via Logging {#obtain-explain-able-xpath-via-logging}

Verklaar **alle** vragen tijdens de ontwikkelingscyclus tegen de reeks van de doelindex.

1. Laat de logboeken van de BUG voor QueryBuilder toe om onderliggende, verklaarbare vraag van XPath te verkrijgen
   * Navigeer naar `https://<host>:<port>/system/console/slinglog` . Creeer een registreerapparaat voor `com.day.cq.search.impl.builder.QueryImpl` bij **DEBUG**.
1. Nadat DEBUG voor de bovengenoemde klasse wordt toegelaten, tonen de logboeken XPath dat door de Bouwer van de Vraag wordt geproduceerd.
1. Kopieer de vraag van XPath van de logboekingang voor de bijbehorende vraag van de Bouwer van de Vraag, bijvoorbeeld:
   * `com.day.cq.search.impl.builder.QueryImpl XPath query: /jcr:root/content//element(*, cq:Page)[(jcr:contains(jcr:content, "WKND") or jcr:contains(jcr:content/@cq:tags, "WKND"))]`
1. Plak de vraag van XPath in Verklaar Vraag als XPath zodat kunt u het vraagplan verkrijgen.

### Verkrijg Verklarende XPath via Debugger van de Bouwer van de Vraag {#obtain-explain-able-xpath-via-the-query-builder-debugger}

Gebruik debugger van de Bouwer van de Vraag van de AEM om een verklaarbare vraag van XPath te produceren.

![ Debugger van de Bouwer van de Vraag ](assets/query-builder-debugger.png)

1. Geef de query van Query Builder op in de foutopsporing van Query Builder
1. De zoekopdracht uitvoeren
1. De gegenereerde XPath ophalen
1. Plak de vraag van XPath in Verklaar Vraag als XPath zodat kunt u het vraagplan verkrijgen

>[!NOTE]
>
>De vragen van de Bouwer van de niet-Vraag (XPath, JCR-SQL2) kunnen direct aan Verklaar Vraag worden verstrekt.

## Foutopsporing in query&#39;s met logboekregistratie {#debugging-queries-with-logging}

>[!NOTE]
>
>De configuratie van de registreerapparaten wordt beschreven in het document [ Registreren ](/help/implementing/developing/introduction/logging.md).

De logboekoutput (niveau INFO) van de implementatie van de vraagbouwer wanneer het uitvoeren van de vraag die in de vorige sectie [ wordt beschreven het Testen en het Zuiveren:](#testing-and-debugging)

```xml
com.day.cq.search.impl.builder.QueryImpl executing query (predicate tree):
null=group: limit=20, offset=0[
    {group=group: or=true[
        {1_fulltext=fulltext: fulltext=WKND, relPath=jcr:content}
        {2_fulltext=fulltext: fulltext=WKND, relPath=jcr:content/@cq:tags}
    ]}
    {path=path: path=/content}
    {type=type: type=cq:Page}
]
com.day.cq.search.impl.builder.QueryImpl XPath query: /jcr:root/content//element(*, cq:Page)[(jcr:contains(jcr:content, "WKND") or jcr:contains(jcr:content/@cq:tags, "WKND"))]
com.day.cq.search.impl.builder.QueryImpl no filtering predicates
com.day.cq.search.impl.builder.QueryImpl query execution took 69 ms
```

Als u een vraag gebruikend predikaat beoordelaars hebt die filter of die een douaneorde door comparator gebruiken, wordt het genoteerd in de vraag:

```xml
com.day.cq.search.impl.builder.QueryImpl executing query (predicate tree):
null=group: [
    {nodename=nodename: nodename=*.jar}
    {orderby=orderby: orderby=@jcr:content/jcr:lastModified}
    {type=type: type=nt:file}
]
com.day.cq.search.impl.builder.QueryImpl custom order by comparator: jcr:content/jcr:lastModified
com.day.cq.search.impl.builder.QueryImpl XPath query: //element(*, nt:file)
com.day.cq.search.impl.builder.QueryImpl filtering predicates: {nodename=nodename: nodename=*.jar}
com.day.cq.search.impl.builder.QueryImpl query execution took 272 ms
```

## Javadoc-koppelingen {#javadoc-links}

| **Javadoc** | **Beschrijving** |
|---|---|
| [ com.day.cq.search ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/package-summary.html) | Basic Query Builder en Query API |
| [ com.day.cq.search.result ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/result/package-summary.html) | Resultaat-API |
| [ com.day.cq.search.facets ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/package-summary.html) | Facetten |
| [ com.day.cq.search.facets.buckets ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/buckets/package-summary.html) | Emmers (in facetten) |
| [ com.day.cq.search.eval ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/package-summary.html) | Voorspelende evaluatoren |
| [ com.day.cq.search.facets.extractors ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/extractors/package-summary.html) | Facet Extractor (voor beoordelaars) |
| [ com.day.cq.search.writer ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/writer/package-summary.html) | JSON Result Hit Writer voor Query Builder servlet (`/bin/querybuilder.json`) |
