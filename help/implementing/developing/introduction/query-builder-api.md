---
title: Query Builder-API
description: De functionaliteit van de Asset Share Query Builder wordt weergegeven via een Java API en een REST API.
exl-id: d5f22422-c9da-4c9d-b81c-ffa5ea7cdc87
source-git-commit: c08e442e58a4ff36e89a213aa7b297b538ae3bab
workflow-type: tm+mt
source-wordcount: '2039'
ht-degree: 0%

---

# Query Builder-API {#query-builder-api}

De Bouwer van de Vraag biedt een gemakkelijke manier om de inhoudsbewaarplaats van AEM te vragen. De functionaliteit wordt beschikbaar gemaakt via een Java API en een REST API. In dit document worden deze API&#39;s beschreven.

De server-kant vraagbouwer ([`QueryBuilder`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html)) accepteert een querybeschrijving, maakt en voert een XPath-query uit, filtert de resultaatset optioneel en extraheert facetten indien gewenst.

De vraagbeschrijving is eenvoudig een reeks predikaten ([`Predicate`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/Predicate.html)). Voorbeelden zijn een voorspelling in volledige tekst, die overeenkomt met de `jcr:contains()` in XPath.

Voor elk predicaatype, is er een evaluatorcomponent ([`PredicateEvaluator`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html)) die weet hoe te om dat specifieke predikaat voor XPath, het filtreren, en facetextractie te behandelen. Het is zeer gemakkelijk om douanebeoordelaars tot stand te brengen, die door componenten OSGi runtime gestopt zijn.

De REST API biedt toegang tot exact dezelfde functies via HTTP, waarbij reacties worden verzonden in JSON.

>[!NOTE]
>
>De API van QueryBuilder wordt gebouwd gebruikend JCR API. U kunt ook een query uitvoeren op de AEM JCR door de JCR API te gebruiken vanuit een OSGi-bundel. Zie voor meer informatie [Adobe Experience Manager-gegevens opvragen met de JCR API](https://helpx.adobe.com/experience-manager/using/querying-experience-manager-data-using1.html).

## Gem-sessie {#gem-session}

[AEM Gems](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-index.html) Dit is een reeks technische diepteduiken in Adobe Experience Manager die door experts van Adobe worden geleverd.

U kunt [herzie de zitting specifiek aan de vraagbouwer wordt gewijd](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-search-forms-using-querybuilder.html) voor een overzicht en gebruik van het gereedschap.

## Voorbeeldquery&#39;s {#sample-queries}

Deze voorbeelden worden gegeven in de stijlnotatie Java-eigenschappen. Als u deze wilt gebruiken met de Java API, gebruikt u een Java `HashMap` zoals in het volgende API-voorbeeld.

Voor de `QueryBuilder` JSON Servlet, elk voorbeeld omvat een steekproefverbinding aan een AEM installatie (bij de standaardplaats, `http://<host>:<port>`). U moet zich aanmelden bij uw AEM voordat u deze koppelingen kunt gebruiken.

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

### Alle resultaten retourneren {#returning-all-results}

De volgende query wordt uitgevoerd **tien resultaten retourneren** (of om precies een maximum van tien te zijn), maar u op de hoogte te brengen van **Aantal treffers:** die daadwerkelijk beschikbaar zijn:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
orderby=path
```

Dezelfde query (met de parameter `p.limit=-1`) **Alle resultaten retourneren** (dit kan een hoog aantal zijn, afhankelijk van uw instantie):

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

Het doel van de `p.guessTotal` de parameter moet het juiste aantal resultaten opleveren dat kan worden aangetoond door de minimaal haalbare `p.offset` en `p.limit` waarden. Het voordeel van deze parameter is dat de prestaties van grote resultaatsets verbeterd zijn. Hiermee vermijdt u het volledige totaal te berekenen (bijvoorbeeld `result.getSize()`) en het lezen van de volledige resultaatset, volledig tot aan de OAK-engine en -index geoptimaliseerd. Dit kan een belangrijk verschil zijn wanneer er honderdduizenden resultaten zijn, zowel in uitvoeringstijd als in geheugengebruik.

Het nadeel van de parameter is dat gebruikers het exacte totaal niet zien. Maar u kunt een minimumaantal instellen zoals `p.guessTotal=1000` het zal altijd tot 1000 lezen, zodat krijgt u nauwkeurige totalen voor kleinere resultaatreeksen, maar als het meer is dan dat, kunt u slechts &quot;en meer&quot;tonen.

Toevoegen `p.guessTotal=true` aan de vraag hieronder om te zien hoe het werkt:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=true&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
p.guessTotal=true
orderby=path
```

De query retourneert de `p.limit` standaard `10` resultaten met een `0` verschuiving:

```xml
"success": true,
"results": 10,
"total": 10,
"more": true,
"offset": 0,
```

U kunt ook een numerieke waarde gebruiken om tot een aangepast aantal maximumresultaten te tellen. Gebruik dezelfde query als hierboven, maar wijzig de waarde van `p.guessTotal` tot `50`:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=50&orderby=path`

Het zal een aantal de zelfde standaardgrens van 10 resultaten met een 0 compensatie terugkeren, maar zal slechts een maximum van 50 resultaten tonen:

```xml
"success": true,
"results": 10,
"total": 50,
"more": true,
"offset": 0,
```

### Paginering implementeren {#implementing-pagination}

Door gebrek zou de Bouwer van de Vraag ook het aantal treffers verstrekken. Afhankelijk van de resultaatgrootte dit zou lang kunnen duren aangezien het bepalen van de nauwkeurige telling het controleren van elk resultaat voor toegangsbeheer impliceert. Meestal wordt het totaal gebruikt om paginering voor de eindgebruiker UI uit te voeren. Aangezien het bepalen van de nauwkeurige telling langzaam kan zijn, wordt geadviseerd om van de eigenschap te gebruiken radenTotal om de paginering uit te voeren.

De interface kan bijvoorbeeld de volgende benadering aanpassen:

* De juiste telling van het aantal totaalresultaten ophalen en weergeven ([SearchResult.getTotalMatches()](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/result/SearchResult.html#getTotalMatches) of totaal in de `querybuilder.json` respons) kleiner zijn dan of gelijk zijn aan 100;
* Set `guessTotal` aan 100 terwijl het maken van de vraag aan de Bouwer van de Vraag.

* De reactie kan het volgende resultaat hebben:

   * `total=43`, `more=false` - Geeft aan dat het totale aantal treffers 43 is. De interface kan tot tien resultaten als deel van de eerste pagina tonen en paginering voor de volgende drie pagina&#39;s verstrekken. U kunt deze implementatie ook gebruiken om een beschrijvende tekst weer te geven, zoals **&quot;43 resultaten gevonden&quot;**.
   * `total=100`, `more=true` - Geeft aan dat het totale aantal treffers groter is dan 100 en dat het exacte aantal niet bekend is. De interface kan maximaal tien pagina&#39;s weergeven als onderdeel van de eerste pagina en paginering voor de volgende tien pagina&#39;s bieden. U kunt dit ook gebruiken om tekst als **&quot;meer dan 100 resultaten gevonden&quot;**. Aangezien de gebruiker naar de volgende pagina vraag gaat die aan de Bouwer van de Vraag wordt gemaakt zou de grens van verhogen `guessTotal` en van de `offset` en `limit` parameters.

`guessTotal` moet ook worden gebruikt in gevallen waarin de gebruikersinterface oneindig schuiven moet gebruiken om te voorkomen dat de Query Builder het exacte aantal treffers bepaalt.

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

Gebruik de `tagid` voorspellen zoals in het voorbeeld als u expliciete markering ID kent.

Gebruik de `tag` bepalen voor het pad naar de tagtitel (zonder spaties).

Omdat u in het vorige voorbeeld naar pagina&#39;s zoekt (`cq:Page` knooppunten), moet u het relatieve pad van dat knooppunt gebruiken voor de `tagid.property` voorspellen, wat `jcr:content/cq:tags`. Standaard worden de `tagid.property` gewoon `cq:tags`.

### Meerdere paden zoeken (met groepen) {#search-under-multiple-paths-using-groups}

`http://<host>:<port>/bin/querybuilder.json?fulltext=Experience&group.1_path=/content/wknd/us/en/magazine&group.2_path=/content/wknd/us/en/adventures&group.p.or=true`

```xml
fulltext=Experience
group.p.or=true
group.1_path=/content/wknd/us/en/magazine
group.2_path=/content/wknd/us/en/adventures
```

Deze query gebruikt een *groep* (benoemd `group`), die fungeert als scheidingsteken voor subexpressies binnen een query, net als ronde haakjes in meer standaardnotaties. Bijvoorbeeld, zou de vorige vraag in een meer bekende stijl als kunnen worden uitgedrukt:

`"Experience" and ("/content/wknd/us/en/magazine" or "/content/wknd/us/en/adventures")`

In de groep in het voorbeeld worden de `path` predikaat wordt meerdere keren gebruikt. Om de twee instanties van predikaat (het opdracht geven tot wordt vereist voor sommige predikaten) te onderscheiden en te rangschikken, moet u prefixeren predikaten met `N_` waar `N` is de bestelindex. In het vorige voorbeeld zijn de resulterende voorspellingen `1_path` en `2_path`.

De `p` in `p.or` is een speciaal scheidingsteken dat aangeeft wat volgt (in dit geval `or`) is *parameter* van de groep, in tegenstelling tot een subpredicaat van de groep, zoals `1_path`.

Indien niet `p.or` Alle voorspellingen worden dan samen ENed gegeven, dat wil zeggen dat elk resultaat aan alle voorspellingen moet voldoen.

>[!NOTE]
>
>U kunt niet hetzelfde numerieke voorvoegsel in één query gebruiken, zelfs niet voor verschillende voorspellingen.

### Zoeken naar eigenschappen {#search-for-properties}

Hier zoekt u naar alle pagina&#39;s van een bepaalde sjabloon met de opdracht `cq:template` eigenschap:

`http://<host>:<port>/bin/querybuilder.json?property=cq%3atemplate&property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&type=cq%3aPageContent`

```xml
type=cq:PageContent
property=cq:template
property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
```

Dit heeft het nadeel dat de `jcr:content` knooppunten van de pagina&#39;s worden geretourneerd, niet de pagina&#39;s zelf. U kunt dit oplossen door op relatief pad te zoeken:

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

Grote groepen voorkomen wanneer u naar meerdere waarden van een eigenschap wilt zoeken (`"A" or "B" or "C"`), kunt u meerdere waarden opgeven voor de `property` voorspellen:

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3atitle&property.1_value=Cycling%20Tuscany&property.2_value=Ski%20Touring&property.3_value=Whistler%20Mountain%20Biking`

```xml
property=jcr:title
property.1_value=Cycling Tuscany
property.2_value=Ski Touring
property.3_value=Whistler Mountain Biking
```

Voor eigenschappen met meerdere waarden kunt u ook opgeven dat meerdere waarden overeenkomen (`"A" and "B" and "C"`):

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

waar `n` is het aantal niveaus u de vraag wilt terugkeren. Een onderliggende node kan alleen worden geretourneerd als deze is opgegeven door de eigenschappenkiezer

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

Voor meer voorspellingen raadpleegt u de [Voorspelde referentiepagina van Query Builder](query-builder-predicates.md).

U kunt ook de [Javadoc voor de `PredicateEvaluator` klassen](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html). Javadoc voor deze klassen bevat de lijst met eigenschappen die u kunt gebruiken.

Het voorvoegsel van de klassenaam (bijvoorbeeld `similar` in [`SimilarityPredicateEvaluator`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/SimilarityPredicateEvaluator.html)) is de *principal, eigenschap* van de klasse. Dit bezit is ook de naam van predikaat aan gebruik in de vraag (in kleine letters).

Voor dergelijke belangrijkste eigenschappen kunt u de query verkorten en het gebruik verkorten `similar=/content/en` in plaats van de volledig gekwalificeerde variant `similar.similar=/content/en`. Het volledig gekwalificeerde formulier moet worden gebruikt voor alle niet-hoofdeigenschappen van een klasse.

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

U kunt query&#39;s opslaan in de opslagplaats, zodat u ze later kunt gebruiken. De `QueryBuilder` verstrekt `storeQuery` methode met de volgende handtekening:

```java
void storeQuery(Query query, String path, boolean createFile, Session session) throws RepositoryException, IOException;
```

Wanneer u de [`QueryBuilder#storeQuery`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html#storeQuery-com.day.cq.search.Query-java.lang.String-boolean-javax.jcr.Session-) methode, de `Query` in de opslagplaats wordt opgeslagen als een bestand of als een eigenschap volgens de `createFile` argumentwaarde. In het volgende voorbeeld wordt getoond hoe u een `Query` naar het pad `/mypath/getfiles` als bestand:

```java
builder.storeQuery(query, "/mypath/getfiles", true, session);
```

Eerder opgeslagen query&#39;s kunnen vanuit de opslagplaats worden geladen met behulp van de [`QueryBuilder#loadQuery`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html#loadQuery-java.lang.String-javax.jcr.Session-) methode:

```java
Query loadQuery(String path, Session session) throws RepositoryException, IOException
```

Bijvoorbeeld een `Query` opgeslagen naar het pad `/mypath/getfiles` kan door het volgende fragment worden geladen:

```java
Query loadedQuery = builder.loadQuery("/mypath/getfiles", session);
```

## Testen en fouten opsporen {#testing-and-debugging}

Voor het spelen rond en het zuiveren van de vragen van de Bouwer van de Vraag, kunt u de debugger console van de Bouwer van de Vraag gebruiken bij

`http://<host>:<port>/libs/cq/search/content/querydebug.html`

of anders de Query Builder JSON servlet op

`http://<host>:<port>/bin/querybuilder.json?path=/tmp`

`path=/tmp` is slechts een voorbeeld.

### Algemene foutopsporing in Recommendations {#general-debugging-recommendations}

### Uitleg XPath verkrijgen via Logging {#obtain-explain-able-xpath-via-logging}

Uitleggen **alles** vragen tijdens de ontwikkelingscyclus tegen de reeks van de doelindex.

1. Laat de logboeken van de BUG voor QueryBuilder toe om onderliggende, verklaarbare vraag van XPath te verkrijgen
   * Ga naar `https://<host>:<port>/system/console/slinglog`. Een nieuw logger maken voor `com.day.cq.search.impl.builder.QueryImpl` om **DEBUG**.
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

## Foutopsporing in query&#39;s met logboekregistratie {#debugging-queries-with-logging}

>[!NOTE]
>
>De configuratie van de loggers wordt beschreven in het document [Logboekregistratie](/help/implementing/developing/introduction/logging.md).

De logboekoutput (niveau INFO) van de implementatie van de vraagbouwer wanneer het uitvoeren van de vraag die in de vorige sectie wordt beschreven [Testen en fouten opsporen:](#testing-and-debugging)

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
| [com.day.cq.search](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/package-summary.html) | Basic Query Builder en Query API |
| [com.day.cq.search.result](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/result/package-summary.html) | Resultaat-API |
| [com.day.cq.search.facets](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/package-summary.html) | Facetten |
| [com.day.cq.search.facets.buckets](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/buckets/package-summary.html) | Emmers (in facetten) |
| [com.day.cq.search.eval](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/package-summary.html) | Voorspelende evaluatoren |
| [com.day.cq.search.facets.extractors](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/extractors/package-summary.html) | Facet Extractor (voor beoordelaars) |
| [com.day.cq.search.writer](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/writer/package-summary.html) | JSON Result Hit Writer voor Query Builder servlet (`/bin/querybuilder.json`) |
