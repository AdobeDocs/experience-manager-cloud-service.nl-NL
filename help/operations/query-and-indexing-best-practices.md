---
title: Aanbevolen werkwijzen voor query en indexering
description: Leer hoe u indexen en query's optimaliseert op basis van de richtlijnen voor aanbevolen Adobe.
topic-tags: best-practices
source-git-commit: 565ca9f29c08a741edfd325090588c4bd7ae81f3
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 0%

---


# Aanbevolen werkwijzen voor query en indexering {#query-and-indexing-best-practices}

In AEM as a Cloud Service worden alle operationele aspecten met betrekking tot indexering geautomatiseerd. Op deze manier kunnen ontwikkelaars zich richten op het maken van efficiënte query&#39;s en de bijbehorende indexdefinities.

## Wanneer moet u query&#39;s gebruiken? {#when-to-use-queries}

Zoekopdrachten zijn een manier om toegang te krijgen tot inhoud, maar niet de enige mogelijkheid. In veel situaties kan inhoud in de opslagplaats effectiever worden benaderd met andere middelen. U zou moeten nadenken als de vragen de beste en meest efficiënte manier zijn om tot inhoud voor uw gebruiksgeval toegang te hebben.

### Opslagplaats en Taxonomie-ontwerp {#repository-and-taxonomy-design}

Bij het ontwerpen van de taxonomie van een gegevensopslagruimte moeten verschillende factoren in aanmerking worden genomen. Deze omvatten toegangscontroles, localisatie, component en paginabezitsovererving, en meer.

Terwijl het ontwerpen van een taxonomie die deze zorgen richt, is het ook belangrijk om de &quot;draagbaarheid&quot;van het indexeren ontwerp te overwegen. In dit verband is de verhandelbaarheid het vermogen van een taxonomie om inhoud toe te staan om voorspelbaar te worden betreden gebaseerd op zijn weg. Dit maakt voor een efficiënter systeem dat gemakkelijker is te handhaven dan één die veelvoudige vragen vereist om worden uitgevoerd.

Bovendien, wanneer het ontwerpen van een taxonomie, is het belangrijk om te overwegen of het opdracht geven belangrijk is. Wanneer expliciete volgorde niet vereist is en een groot aantal knooppunten op hetzelfde niveau wordt verwacht, wordt u beter een ongeordend knooppunttype gebruikt, zoals `sling:Folder` of `oak:Unstructured`. In gevallen waarin bestelling vereist is, `nt:unstructured` en `sling:OrderedFolder` zou beter zijn.

### Zoekopdrachten in componenten {#queries-in-components}

Aangezien de vragen één van de meer het belasten verrichtingen op een AEM systeem kunnen zijn, is het een goed idee om hen in uw componenten te vermijden. Als u meerdere query&#39;s hebt uitgevoerd telkens wanneer een pagina wordt gerenderd, kan dit vaak de prestaties van het systeem nadelig beïnvloeden. Er zijn twee strategieën die kunnen worden gebruikt om het uitvoeren van query&#39;s bij het renderen van componenten te voorkomen: **[knooppunten doorlopen](#traversing-nodes)** en **[Resultaten vooraf instellen.](#prefetching-results)**

### Doorlopende knooppunten {#traversing-nodes}

Als de gegevensopslagplaats op een dergelijke manier wordt ontworpen dat vroegere kennis van de plaats van de vereiste gegevens toestaat, kan de code die deze gegevens van de noodzakelijke wegen terugwint worden opgesteld zonder het moeten vragen in werking stellen om het te vinden.

Een voorbeeld hiervan is het renderen van inhoud die binnen een bepaalde categorie past. Een manier is om de inhoud te ordenen met een categorie-eigenschap die kan worden gevraagd om een component te vullen die items in een categorie weergeeft.

Een betere benadering zou zijn om deze inhoud in een taxonomie door categorie te structureren zodat het manueel kan worden teruggewonnen.

Als de inhoud bijvoorbeeld wordt opgeslagen in een taxonomie die lijkt op:

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

de `/content/myUnstructuredContent/parentCategory/childCategory` de knoop kan eenvoudig worden teruggewonnen, zijn kinderen kunnen worden ontleed en worden gebruikt om de component terug te geven.

Bovendien, wanneer u met een kleine of homogene resultaatreeks te maken hebt, kan het sneller zijn om de bewaarplaats over te steken en de vereiste knopen te verzamelen, eerder dan het ontwerpen van een vraag om de zelfde resultaatreeks terug te keren. In het algemeen moeten vragen worden vermeden wanneer dat mogelijk is.

### Voorkeursresultaten {#prefetching-results}

Soms staat de inhoud of de vereisten rond de component het gebruik van knooptraversal als methode toe om de vereiste gegevens terug te winnen. In dergelijke gevallen moeten de vereiste query&#39;s worden uitgevoerd voordat de component wordt gerenderd, zodat optimale prestaties worden gegarandeerd.

Als de resultaten die voor de component worden vereist op het tijdstip kunnen worden berekend dat het wordt geschreven en er geen verwachting is dat de inhoud zal veranderen, kan de vraag worden uitgevoerd nadat een verandering is gedaan.

Als de gegevens of de inhoud regelmatig zullen veranderen, kan de vraag op een programma of via een luisteraar voor updates aan de onderliggende gegevens worden uitgevoerd. Vervolgens kunnen de resultaten naar een gedeelde locatie in de opslagplaats worden geschreven. Om het even welke componenten die deze gegevens nodig hebben kunnen dan de waarden van deze enige knoop trekken zonder het moeten een vraag bij runtime uitvoeren.

Een gelijkaardige strategie kan worden gebruikt om het resultaat in een in geheugen geheim voorgeheugen te houden, dat bij opstarten wordt bevolkt en wanneer de veranderingen worden gedaan bijgewerkt (gebruikend JCR `ObservationListener` of een Sling `ResourceChangeListener`).

## Zoekopdrachten optimaliseren {#optimizing-queries}

De documentatie van de eikel verstrekt een [overzicht op hoog niveau hoe query&#39;s worden uitgevoerd.](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-processing) Dit vormt de basis van alle optimalisatieactiviteiten die in dit document worden beschreven.

AEM as a Cloud Service verstrekt het Hulpmiddel van de Prestaties van de Vraag, dat wordt ontworpen om het uitvoeren van efficiënte vragen te steunen.

* Het toont reeds uitgevoerde vragen met hun relevante prestatieskenmerken en het vraagplan.
* Het staat het uitvoeren van ad hoc vragen op diverse niveaus toe, die van enkel het tonen van het vraagplan tot het uitvoeren van de volledige vraag beginnen.

Het hulpmiddel van de Prestaties van de Vraag is bereikbaar via [Developer Console in Cloud Manager.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html#queries) AEM as a Cloud Service Hulpmiddel van de Prestaties van de Vraag van de Vraag levert meer informatie over de details van de vraaguitvoering over AEM 6.x versie.

Dit diagram illustreert de algemene stroom om het Hulpmiddel van de Prestaties van de Vraag te gebruiken om vragen te optimaliseren.

![Stroom voor optimalisatie van query](assets/query-optimization-flow.png)

### Index gebruiken {#use-an-index}

Elke vraag zou een index moeten gebruiken om optimale prestaties te leveren. In de meeste gevallen, zouden de bestaande out-of-box indexen moeten voldoende zijn om vragen te behandelen.

Soms moeten aangepaste eigenschappen worden toegevoegd aan een bestaande index, zodat aanvullende beperkingen kunnen worden gevraagd met de index. Zie het document [Inhoud zoeken en indexeren](/help/operations/indexing.md#changing-an-index) voor meer informatie . De [JCR-query-controle](#jcr-query-cheatsheet) in dit document wordt beschreven hoe een eigenschapdefinitie op een index eruit moet zien om een specifiek querytype te ondersteunen.

### De juiste criteria gebruiken {#use-the-right-criteria}

De primaire beperking op om het even welke vraag zou een bezitsgelijke moeten zijn, aangezien dit het meest efficiënte type is. Als u meer eigenschapbeperkingen toevoegt, beperkt u het resultaat verder.

De query-engine beschouwt slechts één index. Dat betekent dat een bestaande index kan en moet worden aangepast door er meer aangepaste indexeigenschappen aan toe te voegen.

De [JCR-query-werkblad](#jcr-query-cheatsheet) in dit document worden de beschikbare beperkingen vermeld en ook uitgelegd hoe een indexdefinitie eruit moet zien zodat deze kan worden opgepikt. Gebruik de [Query-prestaties](#query-performance-tool) om de vraag te testen en ervoor te zorgen dat de juiste index wordt gebruikt en dat de vraagmotor geen beperkingen buiten de index hoeft te evalueren.

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

Zie de sectie [Zoekopdrachten met grote resultaten](#queries-with-large-result-sets) van dit document als een potentieel grote resultaatreeks volledig moet worden verwerkt.

## JCR-query-controle {#jcr-query-cheatsheet}

Ter ondersteuning van de creatie van efficiënte JCR-query&#39;s en indexdefinities [JCR-query - Cheat Sheet](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/practices/best-practices-for-queries-and-indexing.html#jcrquerycheatsheet) kan tijdens de ontwikkeling worden gedownload en gebruikt als referentie.

Het bevat steekproefvragen voor QueryBuilder, XPath, en SQL-2, die veelvoudige scenario&#39;s behandelen die zich verschillend in termen van vraagprestaties gedragen. Het verstrekt ook aanbevelingen voor om indexen van het Eak te bouwen of aan te passen. De inhoud van dit Cheat Sheet is van toepassing op zowel AEM as a Cloud Service als AEM 6.5.

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
