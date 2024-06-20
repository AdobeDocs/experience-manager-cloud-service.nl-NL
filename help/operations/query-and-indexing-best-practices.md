---
title: Aanbevolen werkwijzen voor query en indexering
description: Leer hoe u indexen en query's optimaliseert op basis van de richtlijnen die de Adobe hanteert.
topic-tags: best-practices
exl-id: 37eae99d-542d-4580-b93f-f454008880b1
feature: Operations
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '3088'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor query en indexering {#query-and-indexing-best-practices}

In AEM as a Cloud Service worden alle operationele aspecten met betrekking tot indexering geautomatiseerd. Op deze manier kunnen ontwikkelaars zich richten op het maken van efficiënte query&#39;s en de bijbehorende indexdefinities.

## Wanneer moet u query&#39;s gebruiken? {#when-to-use-queries}

Zoekopdrachten zijn een manier om toegang te krijgen tot inhoud, maar niet de enige mogelijkheid. In veel situaties kan inhoud in de opslagplaats effectiever worden benaderd met andere middelen. U zou moeten nadenken als de vragen de beste en meest efficiënte manier zijn om tot inhoud voor uw gebruiksgeval toegang te hebben.

### Opslagplaats en Taxonomie-ontwerp {#repository-and-taxonomy-design}

Bij het ontwerpen van de taxonomie van een gegevensopslagruimte moeten verschillende factoren in aanmerking worden genomen. Deze omvatten toegangscontroles, localisatie, component en paginabezitsovererving, en meer.

Terwijl het ontwerpen van een taxonomie die deze zorgen richt, is het ook belangrijk om de &quot;draagbaarheid&quot;van het indexeren ontwerp te overwegen. In dit verband is de verhandelbaarheid het vermogen van een taxonomie om inhoud toe te staan om voorspelbaar te worden betreden gebaseerd op zijn weg. Dit maakt voor een efficiënter systeem dat gemakkelijker is te handhaven dan één die veelvoudige vragen vereist om worden uitgevoerd.

Ook, wanneer het ontwerpen van een taxonomie, is het belangrijk om te overwegen of het opdracht geven belangrijk is. Wanneer expliciete volgorde niet vereist is en een groot aantal knooppunten op hetzelfde niveau wordt verwacht, wordt u beter een ongeordend knooppunttype gebruikt, zoals `sling:Folder` of `oak:Unstructured`. In gevallen waarin bestelling vereist is, `nt:unstructured` en `sling:OrderedFolder` zou beter zijn.

### Zoekopdrachten in componenten {#queries-in-components}

Aangezien de vragen één van de meer het belasten verrichtingen op een AEM systeem kunnen zijn, is het een goed idee om hen in uw componenten te vermijden. Als u meerdere query&#39;s hebt uitgevoerd telkens wanneer een pagina wordt gerenderd, kan dit vaak de prestaties van het systeem nadelig beïnvloeden. Er zijn twee strategieën die kunnen worden gebruikt om het uitvoeren van query&#39;s bij het renderen van componenten te voorkomen: **[knooppunten doorlopen](#traversing-nodes)** en **[Resultaten vooraf instellen.](#prefetching-results)**

### Doorlopende knooppunten {#traversing-nodes}

Als de opslagplaats op een manier wordt ontworpen die vroegere kennis van de plaats van de vereiste gegevens toestaat, kan de code die deze gegevens van de noodzakelijke wegen terugwint worden opgesteld zonder het moeten vragen in werking stellen om het te vinden.

Een voorbeeld hiervan is het renderen van inhoud die binnen een bepaalde categorie past. Een manier is om de inhoud te ordenen met een categorie-eigenschap die kan worden gevraagd om een component te vullen die items in een categorie weergeeft.

Een betere benadering zou zijn om deze inhoud in een taxonomie door categorie te structureren zodat het manueel kan worden teruggewonnen.

Als de inhoud bijvoorbeeld wordt opgeslagen in een taxonomie die lijkt op:

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

de `/content/myUnstructuredContent/parentCategory/childCategory` de knoop kan eenvoudig worden teruggewonnen, zijn kinderen kunnen worden ontleed en worden gebruikt om de component terug te geven.

Wanneer u te maken hebt met een kleine of homogene resultaatset, kan het bovendien sneller zijn om de gegevensopslagruimte te doorlopen en de vereiste knooppunten te verzamelen in plaats van een query te maken om dezelfde resultatenset te retourneren. In het algemeen moeten vragen worden vermeden wanneer dat mogelijk is.

### Voorkeursresultaten {#prefetching-results}

Soms staat de inhoud of de vereisten rond de component het gebruik van knooptraversal als methode toe om de vereiste gegevens terug te winnen. In dergelijke gevallen moeten de vereiste query&#39;s worden uitgevoerd voordat de component wordt gerenderd, zodat optimale prestaties worden gegarandeerd.

Als de resultaten die voor de component worden vereist op het tijdstip kunnen worden berekend dat het wordt geschreven en er geen verwachting is dat de inhoud zal veranderen, kan de vraag worden uitgevoerd nadat een verandering is gedaan.

Als de gegevens of de inhoud regelmatig zullen veranderen, kan de vraag op een programma of via een luisteraar voor updates aan de onderliggende gegevens worden uitgevoerd. Vervolgens kunnen de resultaten naar een gedeelde locatie in de opslagplaats worden geschreven. Om het even welke componenten die deze gegevens nodig hebben kunnen dan de waarden van deze enige knoop trekken zonder het moeten een vraag bij runtime uitvoeren.

Een gelijkaardige strategie kan worden gebruikt om het resultaat in een in geheugen geheim voorgeheugen te houden, dat bij opstarten wordt bevolkt en wanneer de veranderingen worden gedaan bijgewerkt (gebruikend JCR `ObservationListener` of een Sling `ResourceChangeListener`).

## Zoekopdrachten optimaliseren {#optimizing-queries}

De documentatie van de eikel verstrekt een [overzicht op hoog niveau hoe query&#39;s worden uitgevoerd.](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-processing) Dit vormt de basis van alle optimalisatieactiviteiten die in dit document worden beschreven.

AEM as a Cloud Service biedt de [Query-prestaties](#query-performance-tool), die bedoeld is ter ondersteuning van het implementeren van efficiënte query&#39;s.

* Het toont reeds uitgevoerde vragen met hun relevante prestatieskenmerken en het vraagplan.
* Het staat het uitvoeren van ad hoc vragen op diverse niveaus toe, die van enkel het tonen van het vraagplan tot het uitvoeren van de volledige vraag beginnen.

Het hulpmiddel van de Prestaties van de Vraag is bereikbaar via [Developer Console in Cloud Manager.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html#queries) AEM as a Cloud Service Hulpmiddel van de Prestaties van de Vraag van de Vraag levert meer informatie over de details van de vraaguitvoering over de versie van AEM 6.x.

Dit diagram illustreert de algemene stroom om het Hulpmiddel van de Prestaties van de Vraag te gebruiken om vragen te optimaliseren.

![Stroom voor optimalisatie van query](assets/query-optimization-flow.png)

### Een index gebruiken {#use-an-index}

Elke vraag zou een index moeten gebruiken om optimale prestaties te leveren. In de meeste gevallen, zouden de bestaande out-of-box indexen moeten voldoende zijn om vragen te behandelen.

Soms moeten aangepaste eigenschappen worden toegevoegd aan een bestaande index, zodat aanvullende beperkingen kunnen worden gevraagd met de index. Zie het document [Inhoud zoeken en indexeren](/help/operations/indexing.md#changing-an-index) voor meer informatie . De [JCR-query-controle](#jcr-query-cheatsheet) in dit document wordt beschreven hoe een eigenschapdefinitie op een index moet kijken om een specifiek querytype te ondersteunen.

### De juiste criteria gebruiken {#use-the-right-criteria}

De primaire beperking op om het even welke vraag zou een bezitsgelijke moeten zijn, aangezien dit het meest efficiënte type is. Als u meer eigenschapbeperkingen toevoegt, beperkt u het resultaat verder.

De query-engine beschouwt slechts één index. Dat betekent dat een bestaande index kan en moet worden aangepast door er meer aangepaste indexeigenschappen aan toe te voegen.

De [JCR-query-werkblad](#jcr-query-cheatsheet) in dit document worden de beschikbare beperkingen vermeld en ook uitgelegd hoe een indexdefinitie eruit moet zien zodat deze wordt opgepikt. Gebruik de [Query-prestaties](#query-performance-tool) om de vraag te testen en ervoor te zorgen dat de juiste index wordt gebruikt en dat de vraagmotor geen beperkingen buiten de index hoeft te evalueren.

### Volgorde {#ordering}

Als een specifieke orde van het resultaat wordt gevraagd, zijn er twee manieren voor de vraagmotor om dit te bereiken:

1. De index kan het resultaat volledig en in de juiste volgorde leveren.
   * Dit werkt als de eigenschappen die voor het opdracht geven tot worden gebruikt met worden geannoteerd `ordered=true` in de indexdefinitie.
1. De query-engine voert het bestelproces uit.
   * Dit kan voorkomen wanneer de vraagmotor het filtreren buiten de index uitvoert of het het opdracht geven tot bezit niet met annoteert `ordered=true` eigenschap.
   * Dit vereist dat de volledige resultaatreeks in geheugen voor het sorteren wordt gelezen, die veel langzamer is dan de eerste optie.

### De resultaatgrootte beperken {#restrict-result-size}

De teruggewonnen grootte van het vraagresultaat is een belangrijke factor in vraagprestaties. Aangezien het resultaat op een luie manier wordt gehaald, is er een verschil in enkel het halen van de eerste 20 resultaten in vergelijking met het halen van 10.000 resultaten, zowel in runtime als geheugengebruik.

Dit betekent ook dat de grootte van de resultaatset alleen correct kan worden bepaald als alle resultaten worden opgehaald. Om deze reden, zou de opgehaalde resultaatreeks altijd moeten worden beperkt, of door de vraag (zie [JCR-query-werkblad](#jcr-query-cheatsheet) in dit document (voor meer informatie) of door de leesvolgorde van de resultaten te beperken.

Een dergelijke limiet voorkomt ook dat de query-engine de **traversale limiet** van 100.000 knopen, wat tot een gedwongen einde van de vraag leidt.

Zie de sectie [Vragen met grote resultaatsets](#queries-with-large-result-sets) van dit document als een potentieel grote resultaatreeks volledig moet worden verwerkt.

## Query-prestaties {#query-performance-tool}

Het hulpmiddel van de Prestaties van de Vraag (dat bij wordt gevestigd `/libs/granite/operations/content/diagnosistools/queryPerformance.html` en beschikbaar via de [Developer Console in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html#queries)) biedt -
* Een lijst met &#39;Trage query&#39;s&#39;; wordt momenteel gedefinieerd als het lezen/scannen van meer dan 5000 rijen.
* Een lijst met &#39;Populaire vragen&#39;
* Het hulpmiddel van de Vraag van het &quot;verklaart&quot;voor het begrip hoe een bepaalde vraag door Oak zal worden uitgevoerd.

![Query-prestaties](assets/query-performance-tool.png)

De tabellen &#39;Trage query&#39;s&#39; en &#39;Populaire query&#39;s&#39; bevatten:
* De query-instructie zelf.
* Details van de laatste Draad die de vraag uitvoerde, toestaand de pagina of toepassingseigenschap die de vraag uitvoeren om worden geïdentificeerd.
* De score &#39;Leesoptimalisatie&#39; voor de query.
   * Dit wordt berekend als de verhouding tussen het aantal rijen/knopen die worden gescand om de vraag in werking te stellen en het aantal passende gelezen resultaten.
   * Een vraag waarvoor elke beperking (en om het even welke opdracht) bij de index kan worden behandeld 90% of hierboven zal typisch scoren.
* Details van het maximumaantal rijen -
   * Lezen - geeft aan dat een rij is opgenomen als onderdeel van een resultaatset.
   * Gescand - erop wijzend dat een rij in de resultaten van de onderliggende indexvraag (in het geval van een geïndexeerde vraag) werd omvat of van het nodestore (in het geval van een bewaarplaats traversal) werd gelezen.

Deze lijsten helpen vragen identificeren die niet volledig geïndexeerd zijn (zie [Een index gebruiken](#use-an-index) of te veel knooppunten lezen (zie ook [Repository traversal](#repository-traversal) en [Indextraversal](#index-traversal)). Dergelijke vragen zullen worden benadrukt - de aangewezen gebieden van zorg worden gemerkt rood.

De `Reset Statistics` er is een optie om alle bestaande statistieken die in de tabellen worden verzameld, te verwijderen. Dit staat de uitvoering van een bepaalde vraag (of via de toepassing zelf of het Uitleg hulpmiddel van de Vraag) en de analyse van de uitvoeringsstatistieken toe.

### Query uitvoeren

Met het gereedschap Uitdrukkelijke query kunnen ontwikkelaars het uitvoeringsplan van de query begrijpen (zie [Het uitvoeringsplan voor de query lezen](#reading-query-execution-plan)), met inbegrip van details van om het even welke indexen die worden gebruikt wanneer het uitvoeren van de vraag. Dit kan worden gebruikt om te begrijpen hoe effectief een vraag wordt geïndexeerd om te voorspellen, of met terugwerkende kracht zijn prestaties te analyseren.

#### Een query verklaren

Ga als volgt te werk om een query uit te leggen:

* Selecteer de gewenste querytaal met de `Language` vervolgkeuzelijst.
* Voer de queryinstructie in het dialoogvenster `Query` veld.
* Indien nodig, selecteer hoe de vraag gebruikend de verstrekte checkboxes zal worden uitgevoerd.
   * Standaard hoeven JCR-query&#39;s niet te worden uitgevoerd om het uitvoeringsplan van de query te identificeren (dit is niet het geval voor QueryBuilder-query&#39;s).
   * Er zijn drie opties beschikbaar voor het uitvoeren van de query -
      * `Include Execution Time` - voer de query uit, maar probeer geen resultaten te lezen.
      * `Read first page of results` - voer de vraag uit en lees de eerste &quot;pagina&quot;van 20 resultaten (herhalend de beste praktijken voor het uitvoeren van vragen).
      * `Include Node Count` - voer de query uit en lees de gehele resultatenset (dit wordt meestal niet aanbevolen - zie [Indextraversal](#index-traversal)).

#### Pop-up Query-uitleg {#query-explanation-popup}

![Pop-up Query-uitleg](./assets/query-explanation-popup.png)

Na het selecteren `Explain`, wordt de gebruiker een pop-up voorgesteld beschrijvend het resultaat van de vraag verklaart (en uitvoering, als geselecteerd).
Deze pop-up bevat gegevens van -
* De gebruikte indexen wanneer het uitvoeren van de vraag (of geen index als de vraag gebruikend zou worden uitgevoerd [Repository traversal](#repository-traversal)).
* De uitvoeringstijd (als `Include Execution Time` selectievakje ingeschakeld) en aantal resultaten gelezen (als `Read first page of results` of `Include Node Count` selectievakjes ingeschakeld).
* Het uitvoeringsplan, dat gedetailleerde analyse toestaat hoe de vraag wordt uitgevoerd - zie [Het uitvoeringsplan voor de query lezen](#reading-query-execution-plan) hoe dit te interpreteren.
* De wegen van de eerste 20 vraagresultaten (als `Read first page of results` selectievakje ingeschakeld)
* De volledige logboeken van de vraagplanning, die de relatieve kosten van de indexen tonen die voor de uitvoering van deze vraag werden overwogen (de index met de laagste kosten zal worden gekozen).

#### Het uitvoeringsplan voor de query lezen {#reading-query-execution-plan}

Het Plan van de Uitvoering van de Vraag bevat alles wordt vereist om de prestaties van een bepaalde vraag te voorspellen (of te verklaren). Begrijp hoe efficiënt de vraag zal worden uitgevoerd door de beperkingen en het opdracht geven tot in de originele vraag JCR (of de Bouwer van de Vraag) aan de vraag te vergelijken die in de onderliggende index (Lucene, Elastic of Bezit) wordt uitgevoerd.

Kijk eens naar de volgende query -

```
/jcr:root/content/dam//element(*, dam:Asset) [jcr:content/metadata/dc:title = "My Title"] order by jcr:created
```

... bevat
* 3 beperkingen
   * nodetype (`dam:Asset`)
   * Pad (onderliggende elementen van `/content/dam`)
   * Eigenschap (`jcr:content/metadata/dc:title = "My Title"`)
* Volgorde van de `jcr:created` eigenschap

Het verklaren van deze vraag resulteert in het volgende plan -

```
[dam:Asset] as [a] /* lucene:damAssetLucene-9(/oak:index/damAssetLucene-9) +:ancestors:/content/dam +jcr:content/metadata/dc:title:My Title ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }] where ([a].[jcr:content/metadata/dc:title] = 'My Title') and (isdescendantnode([a], [/content/dam])) */
```

Binnen dit plan, is de sectie die de vraag beschrijft die in de onderliggende index wordt uitgevoerd -

```
lucene:damAssetLucene-9(/oak:index/damAssetLucene-9) +:ancestors:/content/dam +jcr:content/metadata/dc:title:My Title ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }]
```

In dit deel van het plan staat: -
* Er wordt een index gebruikt om deze query uit te voeren -
   * In dit geval de Lucene-index `/oak:index/damAssetLucene-9` zal worden gebruikt, zodat is de resterende informatie in de Syntaxis van de Vraag van Lucene.
* Alle 3 beperkingen worden afgehandeld door de index -
   * De nodetype-beperking
      * impliciet, omdat `damAssetLucene-9` alleen indexknooppunten van het type dam:Asset.
   * De padbeperking
      * omdat `+:ancestors:/content/dam` verschijnt in de vraag van Lucene.
   * De eigenschapsbeperking
      * omdat `+jcr:content/metadata/dc:title:My Title` verschijnt in de vraag van Lucene.
* De volgorde wordt afgehandeld door de index
   * omdat `ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }]`  verschijnt in de vraag van Lucene.

Zulk een vraag zal waarschijnlijk goed presteren, aangezien de resultaten die van de indexvraag zijn teruggekeerd niet verder in de vraagmotor (behalve het filtreren van de Controle van de Toegang) zullen worden gefiltreerd. Het is echter nog steeds mogelijk dat een dergelijke query langzaam wordt uitgevoerd als de beste praktijken niet worden gevolgd - zie [Indextraversal](#index-traversal) hieronder.

Een andere query overwegen -

```
/jcr:root/content/dam//element(*, dam:Asset) [jcr:content/metadata/myProperty = "My Property Value"] order by jcr:created
```

... bevat
* 3 beperkingen
   * nodetype (`dam:Asset`)
   * Pad (onderliggende elementen van `/content/dam`)
   * Eigenschap (`jcr:content/metadata/myProperty = "My Property Value"`)
* Volgorde van de `jcr:created` eigenschap**

Het verklaren van deze vraag resulteert in het volgende plan -

```
[dam:Asset] as [a] /* lucene:damAssetLucene-9-custom-1(/oak:index/damAssetLucene-9-custom-1) :ancestors:/content/dam ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }] where ([a].[jcr:content/metadata/myProperty] = 'My Property Value') and (isdescendantnode([a], [/content/dam])) */
```

Binnen dit plan, is de sectie die de vraag beschrijft die in de onderliggende index wordt uitgevoerd -

```
lucene:damAssetLucene-9(/oak:index/damAssetLucene-9) :ancestors:/content/dam ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }]
```

In dit deel van het plan staat: -
* Slechts 2 (van de 3) beperkingen worden door de index afgehandeld -
   * De nodetype-beperking
      * impliciet, omdat `damAssetLucene-9` alleen indexknooppunten van het type dam:Asset.
   * De padbeperking
      * omdat `+:ancestors:/content/dam` verschijnt in de vraag van Lucene.
* De eigenschapsbeperking `jcr:content/metadata/myProperty = "My Property Value"` wordt niet uitgevoerd bij de index, maar eerder zal als het filtreren van de Motor van de Vraag op de resultaten van de onderliggende vraag van Lucene worden toegepast.
   * Dit komt omdat `+jcr:content/metadata/myProperty:My Property Value` verschijnt niet in de vraag van Lucene, aangezien dit bezit niet in wordt geïndexeerd `damAssetLucene-9` index die wordt gebruikt voor deze query.

Dit plan van de vraaguitvoering zal in elk element onder resulteren `/content/dam` die van de index worden gelezen, en dan verder door de vraagmotor worden gefilterd (die slechts die die aanpassen de niet-geïndexeerde bezitsbeperking in de resultaatreeks).

Zelfs als slechts een klein percentage van de activa de beperking aanpast `jcr:content/metadata/myProperty = "My Property Value"`De query moet een groot aantal knooppunten lezen om de opgevraagde &#39;pagina&#39; met resultaten te kunnen vullen (poging daartoe). Dit kan in een slecht presterende vraag resulteren, die als laag zal worden getoond `Read Optimization` score in het hulpmiddel van de Prestaties van de Vraag) en kan tot berichten leiden WAARSCHUWING die erop wijzen dat de grote aantallen knopen (zie [Indextraversal](#index-traversal)).

Als u de prestaties van deze tweede query wilt optimaliseren, maakt u een aangepaste versie van de `damAssetLucene-9` index (`damAssetLucene-9-custom-1`) en voeg de volgende eigenschapdefinitie toe -

```
"myProperty": {
  "jcr:primaryType": "nt:unstructured",
  "propertyIndex": true,
  "name": "jcr:content/metadata/myProperty"
}
```

## JCR-query - Cheat Sheet {#jcr-query-cheatsheet}

Ter ondersteuning van de creatie van efficiënte JCR-query&#39;s en indexdefinities [JCR-query - Cheat Sheet](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/practices/best-practices-for-queries-and-indexing.html#jcrquerycheatsheet) kan tijdens de ontwikkeling worden gedownload en gebruikt als referentie.

Het bevat steekproefvragen voor QueryBuilder, XPath, en SQL-2, die veelvoudige scenario&#39;s behandelen die zich verschillend in termen van vraagprestaties gedragen. Het verstrekt ook aanbevelingen voor om indexen van het Eak te bouwen of aan te passen. De inhoud van dit Cheat Sheet geldt voor AEM as a Cloud Service en AEM 6.5.

## Aanbevolen werkwijzen voor indexdefinitie {#index-definition-best-practices}

Hieronder volgen enkele aanbevolen procedures voor het definiëren of uitbreiden van indexen.

* Voor nodetypes die bestaande indexen (zoals `dam:Asset` of `cq:Page`) geeft u de voorkeur aan uitbreiding van OOTB-indexen tot de toevoeging van nieuwe indexen.
   * Nieuwe indexen - met name fulltext-indexen - toevoegen aan de `dam:Asset` nodetype wordt sterk afgeraden (zie [deze notitie](/help/operations/indexing.md##index-names-index-names)).
* Nieuwe indexen toevoegen
   * Definieer altijd indexen van het type &#39;lucene&#39;.
   * Een indextag gebruiken in de indexdefinitie (en de bijbehorende query) en `selectionPolicy = tag` om ervoor te zorgen dat de index slechts voor de voorgenomen vragen wordt gebruikt.
   * Zorgen `queryPaths` en `includedPaths` beide worden opgegeven (meestal met dezelfde waarden).
   * Gebruiken `excludedPaths` om paden uit te sluiten die geen nuttige resultaten opleveren.
   * Gebruiken `analyzed` eigenschappen alleen wanneer dit vereist is, bijvoorbeeld wanneer u een beperking voor volledige-tekstquery moet gebruiken voor alleen die eigenschap.
   * Altijd opgeven `async = [ async, nrt ] `, `compatVersion = 2` en `evaluatePathRestrictions = true`.
   * Alleen opgeven `nodeScopeIndex = true` als u een fulltext-index voor knooppunten nodig hebt.

>[!NOTE]
>
>Zie voor meer informatie [Documentatie van de sindex voor eikopgeluiden](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

De geautomatiseerde controles van de pijpleiding van de Manager van de Wolk zullen sommige hierboven beschreven beste praktijken afdwingen.

## Vragen met grote resultaatsets {#queries-with-large-result-sets}

Hoewel het wordt geadviseerd om vragen met grote resultaatreeksen te vermijden, zijn er geldige gevallen waar de grote resultaatreeksen moeten worden verwerkt. Vaak is de omvang van het resultaat niet vooraf bekend, dus moeten er voorzorgsmaatregelen worden genomen om de verwerking betrouwbaar te maken.

* De query moet niet worden uitgevoerd binnen een aanvraag. In plaats daarvan moet de query worden uitgevoerd als onderdeel van een Sling Job of een AEM workflow. Deze hebben geen beperkingen in hun totale runtime, en zijn opnieuw begonnen voor het geval de instantie tijdens de verwerking van de vraag en zijn resultaten daalt.
* Om de vraaggrens van 100.000 knopen te overwinnen, zou u het gebruiken moeten overwegen [Hoofdsetpaginering](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) en splitst de query in meerdere subquery&#39;s.

## Repository traversal {#repository-traversal}

Zoekopdrachten die de gegevensopslagruimte doorlopen, gebruiken geen index en worden geregistreerd met een bericht dat lijkt op het volgende.

```text
28.06.2022 13:32:52.804 *WARN* [127.0.0.1 [1656415972414] POST /libs/settings/granite/operations/diagnosis/granite_queryperformance.explain.json HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.Cursors$TraversingCursor Traversed 98000 nodes with filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a /* xpath: //* */, path=*) called by com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet.getHeuristics; consider creating an index or changing the query
```

Met dit logboekfragment kunt u bepalen:

* De query zelf: `//*`
* De Java-code die deze query heeft uitgevoerd: `com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet::getHeuristics` helpen de maker van de query identificeren.

Met deze informatie, is het mogelijk om deze vraag te optimaliseren gebruikend de methodes die in worden beschreven [Zoekopdrachten optimaliseren](#optimizing-queries) van dit document.

### Indextraversal {#index-traversal}

Vragen die een index gebruiken, maar nog steeds grote aantallen knopen lezen worden geregistreerd met een bericht gelijkend op het volgende (neem nota van de termijn `Index-Traversed` eerder dan `Traversed`).

```text
05.10.2023 10:56:10.498 *WARN* [127.0.0.1 [1696502982443] POST /libs/settings/granite/operations/diagnosis/granite_queryperformance.explain.json HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.search.spi.query.FulltextIndex$FulltextPathCursor Index-Traversed 60000 nodes with filter Filter(query=select [jcr:path], [jcr:score], * from [dam:Asset] as a where isdescendantnode(a, '/content/dam') order by [jcr:content/metadata/unindexedProperty] /* xpath: /jcr:root/content/dam//element(*, dam:Asset) order by jcr:content/metadata/unindexedProperty */, path=/content/dam//*)
```

Dit kan om verschillende redenen voorkomen -

1. Niet kunnen alle beperkingen in de vraag bij de index worden behandeld.
   * In dit geval, wordt een superset van de definitieve resultaatreeks gelezen van de index en daarna gefilterd in de vraagmotor.
   * Dit is vele tijden langzamer dan het toepassen van beperkingen in de onderliggende indexvraag.
1. De query wordt gesorteerd door een eigenschap die niet is gemarkeerd als &#39;ordered&#39; in de index.
   * In dit geval, moeten alle resultaten die door de index zijn teruggekeerd door de vraagmotor worden gelezen en in geheugen worden gesorteerd.
   * Dit is vele tijden langzamer dan het toepassen van sortering in de onderliggende indexvraag.
1. De uitvoerder van de query probeert een grote resultaatset te doorlopen.
   * Deze situatie kan om verschillende redenen, zoals hieronder vermeld, plaatsvinden:

| Oorzaak | Oplossing |
|----------|--------------|
| De Commissie `p.guessTotal` (of het gebruik van een zeer grote gokTotal) veroorzakend QueryBuilder om grote aantallen resultaten telend resultaten te herhalen | Verlenen `p.guessTotal` met een geschikte waarde |
| Het gebruik van een grote of onbegrensde grens in de Bouwer van de Vraag (ie `p.limit=-1`) | Gebruik de juiste waarde voor `p.limit` (ideaal 1000 of lager) |
| Het gebruik van het filtreren predikt in de Bouwer van de Vraag die grote aantallen resultaten van de onderliggende vraag JCR filtreert | Filtervoorspelling vervangen door beperkingen die kunnen worden toegepast in de onderliggende JCR-query |
| Het gebruik van een op vergelijker-gebaseerde sortering in QueryBuilder | Vervangen door op eigenschappen gebaseerde volgorde in de onderliggende JCR-query (met eigenschappen die zijn geïndexeerd zoals geordend) |
| Filteren van grote aantallen resultaten als gevolg van toegangsbeheer | Pas extra geïndexeerde bezit of wegbeperking op de vraag toe om het Toegangsbeheer te weerspiegelen |
| Het gebruik van &#39;offsetpaginering&#39; met een grote verschuiving | Gebruik [Hoofdsetpaginering](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) |
| Herhaling van grote of onbegrensde aantallen resultaten | Gebruik [Hoofdsetpaginering](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) |
| Onjuiste index gekozen | Tags gebruiken in vraag- en indexdefinitie om te controleren of de verwachte index wordt gebruikt |
