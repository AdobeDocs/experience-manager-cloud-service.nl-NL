---
title: Query Builder-API
description: De functionaliteit van de Asset Share Query Builder wordt weergegeven via een Java API en een REST API.
translation-type: tm+mt
source-git-commit: 6b754a866be7979984d613b95a6137104be05399
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Query Builder-API {#query-builder-api}

De Bouwer van de Vraag biedt een gemakkelijke manier om de inhoudsbewaarplaats van AEM te vragen. De functionaliteit wordt beschikbaar gemaakt via een Java API en een REST API. In dit document worden deze API&#39;s beschreven.

De server-zijvraagbouwer ([`QueryBuilder`](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/QueryBuilder.html)) zal een vraagbeschrijving goedkeuren, creeert en in werking stelt een vraag van XPath, naar keuze filter de resultaatreeks, en ook extractie facetten, indien gewenst.

De vraagbeschrijving is eenvoudig een reeks predikaten ([`Predicate`](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/Predicate.html)). Voorbeelden zijn een full-text voorspelling die overeenkomt met de functie `jcr:contains()` in XPath.

Voor elk predicaatype, is er een beoordelaarcomponent ([`PredicateEvaluator`](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/eval/PredicateEvaluator.html)) die weet hoe te om dat specifieke predikaat voor XPath, het filtreren, en facetextractie te behandelen. Het is zeer gemakkelijk om douanebeoordelaars tot stand te brengen, die door componenten OSGi runtime gestopt zijn.

De REST API biedt toegang tot exact dezelfde functies via HTTP, waarbij reacties worden verzonden in JSON.

>[!NOTE]
>
>De API van QueryBuilder wordt gebouwd gebruikend JCR API. U kunt ook een query uitvoeren op de AEM JCR door de JCR API te gebruiken vanuit een OSGi-bundel. Zie [Adobe Experience Manager-gegevens opvragen met de JCR API](https://helpx.adobe.com/experience-manager/using/querying-experience-manager-data-using1.html) voor meer informatie.

## Gem-sessie {#gem-session}

[AEM ](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-index.html) Gemsis heeft een aantal technische diepteduiken in Adobe Experience Manager geleverd door Adobe-experts.

U kunt [de zitting herzien die aan de vraagbouwer](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-search-forms-using-querybuilder.html) voor een overzicht en gebruik van het hulpmiddel wordt gewijd.

## Voorbeeldquery&#39;s {#sample-queries}

Deze voorbeelden worden gegeven in de stijlnotatie Java-eigenschappen. Als u deze wilt gebruiken met de Java API, gebruikt u een Java `HashMap` zoals in het volgende API-voorbeeld.

Voor `QueryBuilder` JSON Servlet, omvat elk voorbeeld een steekproefverbinding aan een AEM installatie (bij de standaardplaats, `http://<host>:<port>`). U moet zich aanmelden bij uw AEM voordat u deze koppelingen kunt gebruiken.

>[!CAUTION]
>
>Standaard geeft de JSON-servlet van de querybuilder maximaal 10 resultaten weer.
>
>Als u de volgende parameter toevoegt, kan de servlet alle queryresultaten weergeven:
>
>`p.limit=-1`

>[!NOTE]
>
>Als u de geretourneerde JSON-gegevens in uw browser wilt weergeven, kunt u een plug-in gebruiken, zoals JSONView voor Firefox.

### Alle resultaten {#returning-all-results} retourneren

De volgende vraag zal **tien resultaten** (of om een maximum van tien te zijn) terugkeren, maar u op de hoogte brengen van **Aantal treffers:** die eigenlijk beschikbaar zijn:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
orderby=path
```

Dezelfde query (met de parameter `p.limit=-1`) retourneert **alle resultaten** (dit kan een hoog getal zijn, afhankelijk van uw instantie):

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path&p.limit=-1`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
p.limit=-1
orderby=path
```

### Het gebruiken van p.radenTotal om de Resultaten {#using-p-guesstotal-to-return-the-results} terug te keren

Het doel van de parameter `p.guessTotal` is het juiste aantal resultaten te retourneren dat kan worden getoond door de minimale levensvatbare waarden `p.offset` en `p.limit` te combineren. Het voordeel van deze parameter is dat de prestaties van grote resultaatsets verbeterd zijn. Zo voorkomt u het berekenen van het volledige totaal (bijvoorbeeld het aanroepen van `result.getSize()`) en het lezen van de volledige resultaatset, die volledig tot aan de OAK-engine en -index is geoptimaliseerd. Dit kan een belangrijk verschil zijn wanneer er honderdduizenden resultaten zijn, zowel in uitvoeringstijd als in geheugengebruik.

Het nadeel van de parameter is dat gebruikers het exacte totaal niet zien. Maar u kunt een minimumaantal zoals `p.guessTotal=1000` plaatsen zodat zal het altijd tot 1000 lezen, zodat krijgt u nauwkeurige totalen voor kleinere resultaatreeksen, maar als het meer dan dat is, kunt u slechts &quot;en meer&quot;tonen.

Voeg `p.guessTotal=true` aan de vraag hieronder toe om te zien hoe het werkt:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=true&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
p.guessTotal=true
orderby=path
```

De query retourneert de `p.limit`-standaardwaarde van `10`-resultaten met een `0`-verschuiving:

```xml
"success": true,
"results": 10,
"total": 10,
"more": true,
"offset": 0,
```

U kunt ook een numerieke waarde gebruiken om tot een aangepast aantal maximumresultaten te tellen. Gebruik dezelfde query als hierboven, maar wijzig de waarde van `p.guessTotal` in `50`:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=50&orderby=path`

Het zal een aantal de zelfde standaardgrens van 10 resultaten met een 0 compensatie terugkeren, maar zal slechts een maximum van 50 resultaten tonen:

```xml
"success": true,
"results": 10,
"total": 50,
"more": true,
"offset": 0,
```

### Paginering {#implementing-pagination} implementeren

Door gebrek zou de Bouwer van de Vraag ook het aantal treffers verstrekken. Afhankelijk van de resultaatgrootte dit zou lang kunnen duren aangezien het bepalen van de nauwkeurige telling het controleren van elk resultaat voor toegangsbeheer impliceert. Meestal wordt het totaal gebruikt om paginering voor de eindgebruiker UI uit te voeren. Aangezien het bepalen van de nauwkeurige telling langzaam kan zijn, wordt geadviseerd om van de eigenschap te gebruiken radenTotal om de paginering uit te voeren.

De interface kan bijvoorbeeld de volgende benadering aanpassen:

* Hiermee wordt de juiste telling opgehaald en weergegeven van het aantal totale treffers ([SearchResult.getTotalMatches()](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/result/SearchResult.html#getTotalMatches) of total in de `querybuilder.json`-respons) is kleiner dan of gelijk aan 100;
* Plaats `guessTotal` aan 100 terwijl het maken van de vraag aan de Bouwer van de Vraag.

* De reactie kan het volgende resultaat hebben:

   * `total=43`,  `more=false` - Geeft aan dat het totale aantal treffers 43 is. De interface kan tot tien resultaten als deel van de eerste pagina tonen en paginering voor de volgende drie pagina&#39;s verstrekken. U kunt deze implementatie ook gebruiken om een beschrijvende tekst weer te geven zoals **&quot;43 gevonden resultaten&quot;**.
   * `total=100`,  `more=true` - Geeft aan dat het totale aantal treffers groter is dan 100 en dat het exacte aantal niet bekend is. De interface kan maximaal tien pagina&#39;s weergeven als onderdeel van de eerste pagina en paginering voor de volgende tien pagina&#39;s bieden. U kunt dit ook gebruiken om tekst als **&quot;meer dan 100 gevonden resultaten&quot;te tonen**. Aangezien de gebruiker naar de volgende pagina gaat vraag aan de Bouwer van de Vraag wordt gemaakt zou de grens van `guessTotal` en ook van `offset` en `limit` parameters verhogen die.

`guessTotal` moet ook worden gebruikt in gevallen waarin de gebruikersinterface oneindig schuiven moet gebruiken om te voorkomen dat de Query Builder het exacte aantal treffers bepaalt.

### JAR-bestanden zoeken en deze bestellen, nieuwste eerst {#find-jar-files-and-order-them-newest-first}

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

### Alle pagina&#39;s zoeken en bestellen op Laatst gewijzigd, Aflopend {#find-all-pages-and-order-them-by-last-modified-but-descending}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified&orderby.sort=desc`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
orderby.sort=desc
```

### fullText zoeken, besteld door score {#fulltext-search-ordered-by-score}

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

Gebruik de `tagid` voorspelling zoals in het voorbeeld als u expliciete markering ID kent.

Gebruik `tag` voorspellen voor de weg van de markeringstitel (zonder ruimten).

Omdat, in het vorige voorbeeld, u naar pagina&#39;s (`cq:Page` knopen) zoekt, moet u de relatieve weg van die knoop voor `tagid.property` voorspellen gebruiken, die `jcr:content/cq:tags` is. Standaard zou `tagid.property` `cq:tags` zijn.

### Meerdere paden zoeken (met groepen) {#search-under-multiple-paths-using-groups}

`http://<host>:<port>/bin/querybuilder.json?fulltext=Experience&group.1_path=/content/wknd/us/en/magazine&group.2_path=/content/wknd/us/en/adventures&group.p.or=true`

```xml
fulltext=Experience
group.p.or=true
group.1_path=/content/wknd/us/en/magazine
group.2_path=/content/wknd/us/en/adventures
```

Deze query gebruikt een *group* (genoemd `group`), die fungeert om subexpressies binnen een query te scheiden, net als ronde haakjes doen in meer standaardnotaties. Bijvoorbeeld, zou de vorige vraag in een meer bekende stijl als kunnen worden uitgedrukt:

`"Experience" and ("/content/wknd/us/en/magazine" or "/content/wknd/us/en/adventures")`

Binnen de groep in het voorbeeld wordt de `path` predikaat meerdere keren gebruikt. Als u de twee instanties van de voorspelling wilt onderscheiden en rangschikken (de volgorde is vereist voor sommige voorspelling), moet u de voorspelling voorvoegsel geven met `N_`, waarbij `N` de volgorde-index is. In het vorige voorbeeld zijn de resulterende voorspellingen `1_path` en `2_path`.

De `p` in `p.or` is een speciaal scheidingsteken dat erop wijst dat wat volgt (in dit geval een `or`) een *parameter* van de groep is, in tegenstelling tot een subpredikaat van de groep, zoals `1_path`.

Als geen `p.or` wordt gegeven dan zijn alle predikaten ANDed samen, dat wil zeggen, elk resultaat moet aan alle predikaten voldoen.

>[!NOTE]
>
>U kunt niet hetzelfde numerieke voorvoegsel in één query gebruiken, zelfs niet voor verschillende voorspellingen.

### Zoeken naar eigenschappen {#search-for-properties}

Hier zoekt u naar alle pagina&#39;s van een bepaalde sjabloon met de eigenschap `cq:template`:

`http://<host>:<port>/bin/querybuilder.json?property=cq%3atemplate&property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&type=cq%3aPageContent`

```xml
type=cq:PageContent
property=cq:template
property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
```

Dit heeft het nadeel dat de `jcr:content` knopen van de pagina&#39;s, niet de pagina&#39;s zelf, zijn teruggekeerd. U kunt dit oplossen door op relatief pad te zoeken:

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3acontent%2fcq%3atemplate&property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&type=cq%3aPage`

```xml
type=cq:Page
property=jcr:content/cq:template
property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
```

### Zoeken naar meerdere eigenschappen {#search-for-multiple-properties}

Wanneer het gebruiken van het bezit voorspelt veelvoudige tijden, moet u de aantalprefixen opnieuw toevoegen:

`http://<host>:<port>/bin/querybuilder.json?1_property=jcr%3acontent%2fcq%3atemplate&1_property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&2_property=jcr%3acontent%2fjcr%3atitle&2_property.value=Cycling%20Tuscany&type=cq%3aPage`

```xml
type=cq:Page
1_property=jcr:content/cq:template
1_property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
2_property=jcr:content/jcr:title
2_property.value=Cycling Tuscany
```

### Zoeken naar meerdere eigenschapswaarden {#search-for-multiple-property-values}

Om grote groepen te vermijden wanneer u naar veelvoudige waarden van een bezit (`"A" or "B" or "C"`) wilt zoeken, kunt u veelvoudige waarden aan &lt;a1 verstrekken/> voorspelt:`property`

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

Door gebrek, zal QueryBuilder JSON Servlet een standaardreeks eigenschappen voor elke knoop in het onderzoeksresultaat (b.v. weg, naam, titel, enz.) terugkeren. Als u de controle wilt krijgen over de eigenschappen die worden geretourneerd, kunt u een van de volgende handelingen uitvoeren:

Geef het volgende op

```xml
p.hits=full
```

In dat geval worden alle eigenschappen voor elk knooppunt opgenomen:

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

en geef de eigenschappen op waarin u wilt gaan werken

```xml
p.properties
```

gescheiden door een spatie:

`http://<host>:<port>/bin/querybuilder.json?p.hits=selective&p.properties=sling%3aresourceType%20jcr%3aprimaryType&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=selective
p.properties=sling:resourceType jcr:primaryType
```

Een ander ding u kunt doen is kindknopen in de reactie van de Bouwer van de Vraag omvatten. Om dit te doen moet u specificeren

```xml
p.nodedepth=n
```

waarbij `n` het aantal niveaus is u de vraag wilt terugkeren. Een onderliggende node kan alleen worden geretourneerd als deze is opgegeven door de eigenschappenkiezer

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

Voor meer predikaten, zie [de Voorspelde Verwijzing van de Bouwer van de Vraag pagina](query-builder-predicates.md).

U kunt [Javadoc voor `PredicateEvaluator` ook controleren klassen ](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/eval/PredicateEvaluator.html). Javadoc voor deze klassen bevat de lijst met eigenschappen die u kunt gebruiken.

Het voorvoegsel van de klassenaam (bijvoorbeeld `similar` in [`SimilarityPredicateEvaluator`](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/eval/SimilarityPredicateEvaluator.html)) is de *principal-eigenschap* van de klasse. Dit bezit is ook de naam van predikaat aan gebruik in de vraag (in kleine letters).

Voor dergelijke belangrijkste eigenschappen, kunt u de vraag verkorten en `similar=/content/en` in plaats van de volledig - gekwalificeerde variant `similar.similar=/content/en` gebruiken. Het volledig gekwalificeerde formulier moet worden gebruikt voor alle niet-hoofdeigenschappen van een klasse.

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

## Vragen opslaan en laden {#storing-and-loading-queries}

U kunt query&#39;s opslaan in de opslagplaats, zodat u ze later kunt gebruiken. `QueryBuilder` voorziet de `storeQuery` methode van de volgende handtekening:

```java
void storeQuery(Query query, String path, boolean createFile, Session session) throws RepositoryException, IOException;
```

Bij gebruik van de [`QueryBuilder#storeQuery`](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/QueryBuilder.html#storeQuery-com.day.cq.search.Query-java.lang.String-boolean-javax.jcr.Session-) methode, wordt gegeven `Query` opgeslagen in de bewaarplaats als dossier of als bezit volgens de `createFile` argumentwaarde. In het volgende voorbeeld wordt getoond hoe u een `Query` als bestand opslaat naar het pad `/mypath/getfiles`:

```java
builder.storeQuery(query, "/mypath/getfiles", true, session);
```

Eerder opgeslagen query&#39;s kunnen vanuit de opslagplaats worden geladen met de methode [`QueryBuilder#loadQuery`](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/QueryBuilder.html#loadQuery-java.lang.String-javax.jcr.Session-):

```java
Query loadQuery(String path, Session session) throws RepositoryException, IOException
```

Een `Query` die is opgeslagen op het pad `/mypath/getfiles` kan bijvoorbeeld door het volgende fragment worden geladen:

```java
Query loadedQuery = builder.loadQuery("/mypath/getfiles", session);
```

## {#testing-and-debugging} testen en fouten opsporen

Voor het spelen rond en het zuiveren van de vragen van de Bouwer van de Vraag, kunt u de debugger console van de Bouwer van de Vraag gebruiken bij

`http://<host>:<port>/libs/cq/search/content/querydebug.html`

of anders de Query Builder JSON servlet op

`http://<host>:<port>/bin/querybuilder.json?path=/tmp`

`path=/tmp` is slechts een voorbeeld.

### Algemene foutopsporing in Recommendations {#general-debugging-recommendations}

### Verkrijg Verklarende XPath via het Registreren {#obtain-explain-able-xpath-via-logging}

Verklaar **all** vragen tijdens de ontwikkelingscyclus tegen de reeks van de doelindex.

1. Laat de logboeken van de BUG voor QueryBuilder toe om onderliggende, verklaarbare vraag van XPath te verkrijgen
   * Ga naar `https://<host>:<port>/system/console/slinglog`. Maak een nieuw logger voor `com.day.cq.search.impl.builder.QueryImpl` op **DEBUG**.
1. Zodra DEBUG voor de bovengenoemde klasse is toegelaten, zullen de logboeken XPath tonen dat door de Bouwer van de Vraag wordt geproduceerd.
1. Kopieer de vraag van XPath van de logboekingang voor de bijbehorende vraag van de Bouwer van de Vraag, bijvoorbeeld:
   * `com.day.cq.search.impl.builder.QueryImpl XPath query: /jcr:root/content//element(*, cq:Page)[(jcr:contains(jcr:content, "WKND") or jcr:contains(jcr:content/@cq:tags, "WKND"))]`
1. Plak de vraag van XPath in Verklaar Vraag als XPath om het vraagplan te verkrijgen.

### Verkrijg Verklarende XPath via Debugger van de Bouwer van de Vraag {#obtain-explain-able-xpath-via-the-query-builder-debugger}

Gebruik debugger van de Bouwer van de Vraag van de AEM om een verklaarbare vraag van XPath te produceren.

![Foutopsporing voor Query Builder](assets/query-builder-debugger.png)

1. Geef de query van Query Builder op in de foutopsporing van Query Builder
1. De zoekopdracht uitvoeren
1. De gegenereerde XPath ophalen
1. Plak de vraag van XPath in Verklaar Vraag als XPath om het vraagplan te verkrijgen

>[!NOTE]
>
>De vragen van de Bouwer van de niet Vraag (XPath, JCR-SQL2) kunnen direct aan Verklaar Vraag worden verstrekt.

## Fouten opsporen in query&#39;s met logboekregistratie {#debugging-queries-with-logging}

>[!NOTE]
>
>De configuratie van de loggers wordt beschreven in het document [Logging](/help/implementing/developing/introduction/logging.md).

De logboekoutput (niveau INFO) van de implementatie van de vraagbouwer wanneer het uitvoeren van de vraag die in de vorige sectie [het Testen en het Zuiveren wordt beschreven:](#testing-and-debugging)

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

Als u een vraag gebruikend predikaat beoordelaars hebt die filter of die een douaneorde door comparator gebruiken, zal dit ook in de vraag worden vermeld:

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
| [com.day.cq.search](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/package-summary.html) | Basic Query Builder en Query API |
| [com.day.cq.search.result](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/result/package-summary.html) | Resultaat-API |
| [com.day.cq.search.facets](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/facets/package-summary.html) | Facetten |
| [com.day.cq.search.facets.buckets](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/facets/buckets/package-summary.html) | Emmers (in facetten) |
| [com.day.cq.search.eval](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/eval/package-summary.html) | Voorspelende evaluatoren |
| [com.day.cq.search.facets.extractors](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/facets/extractors/package-summary.html) | Facet Extractor (voor beoordelaars) |
| [com.day.cq.search.writer](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/search/writer/package-summary.html) | JSON Result Hit Writer voor de servlet van de Bouwer van de Vraag (`/bin/querybuilder.json`) |
