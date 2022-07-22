---
title: Beste praktijken voor Vragen en het Indexeren
seo-title: Best Practices for Queries and Indexing
description: Dit artikel bevat richtlijnen voor het optimaliseren van indexen en query's.
seo-description: This article provides guidelines on how to optimize your indexes and queries.
topic-tags: best-practices
source-git-commit: 85cbdaa6e6d01856005cb47f289d391fb44bd65e
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 0%

---


# Beste praktijken voor Vragen en het Indexeren{#best-practices-for-queries-and-indexing}

In tegenstelling tot vorige versies in AEM as a Cloud Service worden alle operationele aspecten met betrekking tot indexering geautomatiseerd. Op deze manier kunnen ontwikkelaars zich richten op het maken van efficiënte query&#39;s en de bijbehorende indexdefinities.

## Wanneer moet u query&#39;s gebruiken? {#when-to-use-queries}

Zoekopdrachten zijn een manier om toegang tot inhoud te krijgen, maar niet de enige. Daarom moet worden beoordeeld of query&#39;s de beste en meest presterende manier zijn om toegang te krijgen tot inhoud. In veel situaties kan inhoud in de dataopslag op andere manieren beter worden benaderd.

### Opslagplaats en Taxonomie-ontwerp {#repository-and-taxonomy-design}

Bij het ontwerpen van de taxonomie van een gegevensopslagruimte moeten verschillende factoren in aanmerking worden genomen. Dit zijn onder andere toegangsbeheer, lokalisatie, component- en pagina-eigenschapovererving.

Terwijl het ontwerpen van een taxonomie die deze zorgen richt, is het ook belangrijk om de &quot;draagbaarheid&quot;van het indexeren ontwerp te overwegen. In deze context is de verhandelbaarheid de mogelijkheid van een taxonomie die het mogelijk maakt inhoud voorspelbaar toegankelijk te maken op basis van het pad ervan. Dit zal voor een krachtiger systeem maken dat gemakkelijker is te handhaven dan één die veel uit te voeren vragen zal vereisen.

Bovendien, wanneer het ontwerpen van een taxonomie, is het belangrijk om te overwegen of het opdracht geven belangrijk is. Wanneer expliciete volgorde niet vereist is en een groot aantal knooppunten op hetzelfde niveau wordt verwacht, wordt u beter een ongeordend knooppunttype gebruikt, zoals `sling:Folder` of `oak:Unstructured`. In gevallen waarin bestelling vereist is, `nt:unstructured` en `sling:OrderedFolder` zou beter zijn.

### Zoekopdrachten in componenten {#queries-in-components}

Aangezien de vragen één van de meer het belasten verrichtingen op een AEM systeem kunnen zijn, is het een goed idee om hen in uw componenten te vermijden. Als u meerdere query&#39;s hebt uitgevoerd telkens wanneer een pagina wordt gerenderd, kan dit vaak de prestaties van het systeem nadelig beïnvloeden. Er zijn twee strategieën die kunnen worden gebruikt om het uitvoeren van query&#39;s bij het renderen van componenten te voorkomen: **knooppunten doorlopen** en **Prefetingresultaten**.

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

Soms staan de inhoud of de vereisten rond de component het gebruik van knoopverkeer als methode om de vereiste gegevens terug te winnen niet toe. In deze gevallen, moeten de vereiste vragen worden uitgevoerd alvorens de component wordt teruggegeven zodat de optimale prestaties wordt gewaarborgd.

Als de resultaten die voor de component worden vereist op het tijdstip kunnen worden berekend dat het wordt geschreven en er geen verwachting is dat de inhoud zal veranderen, kan de vraag worden uitgevoerd nadat een verandering is gedaan.

Als de gegevens of de inhoud regelmatig zullen veranderen, kan de vraag op een programma of via een luisteraar voor updates aan de onderliggende gegevens worden uitgevoerd. Vervolgens kunnen de resultaten naar een gedeelde locatie in de opslagplaats worden geschreven. Om het even welke componenten die deze gegevens nodig hebben kunnen dan de waarden van deze enige knoop trekken zonder het moeten een vraag bij runtime uitvoeren.
Een gelijkaardige strategie kan worden gebruikt om het resultaat in een in-geheugengeheime voorgeheugen te houden, dat bij opstarten wordt bevolkt en bijgewerkt wanneer de veranderingen worden gedaan (gebruikend een JCR ObservationListener of een Sling ResourceChangeListener).

## Zoekopdrachten optimaliseren {#optimizing-queries}

De documentatie van de eikel verstrekt een [overzicht op hoog niveau hoe query&#39;s worden uitgevoerd](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-processing). Dit vormt de basis van alle optimalisatieactiviteiten die in dit document worden beschreven.

AEM als cloudservice biedt het hulpprogramma Query Performance, dat is ontworpen om het implementeren van efficiënte query&#39;s te ondersteunen.
* Het toont reeds uitgevoerde vragen met hun relevante prestatieskenmerken en het vraagplan.
* Het staat toe om ad hoc vragen op diverse niveaus uit te voeren, die van enkel het vraagplan tonen tot het uitvoeren van de volledige vraag beginnen.

Het hulpmiddel van de Prestaties van de Vraag is bereikbaar via [Developer Console in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html#queries). In tegenstelling tot het hulpmiddel van de Prestaties van de Vraag van vorige versies van AEM 6.x, levert het hulpmiddel van de prestatiesvraag dat voor AEM as a Cloud Service wordt verstrekt meer informatie over de details van de vraaguitvoering, die nuttig zijn om een vraag te verbeteren.


De algemene benadering hoe te om het Hulpmiddel van de Prestaties van de Vraag te gebruiken om vragen te optimaliseren wordt beschreven in deze grafiek.
![Stroom voor optimalisatie van query](assets/query-optimization-flow.png)



### Een index gebruiken {#use-an-index}

Elke vraag zou een index moeten gebruiken om optimale prestaties te leveren. In de meeste gevallen zouden bestaande out-of-box indexen voldoende moeten zijn om vragen te behandelen.
Soms moeten aangepaste eigenschappen aan een bestaande index worden toegevoegd, zodat met deze index aanvullende beperkingen kunnen worden aangevraagd. Zie [Inhoud zoeken en indexeren](/help/operations/indexing.md#changing-an-index) voor meer informatie . De [JCR-query-controle](#jcr-query-cheatsheet) beschrijft hoe een bezitsdefinitie op een index als een specifiek vraagtype moet kijken te steunen.



### De juiste criteria gebruiken

De primaire beperking op om het even welke vraag zou een bezitsgelijke moeten zijn, aangezien dit het meest efficiënte type is. Als u meer eigenschapbeperkingen toevoegt, wordt het resultaat verder beperkt.
De query-engine beschouwt slechts één index; dat betekent dat een bestaande index kan en moet worden aangepast door er meer aangepaste indexeigenschappen aan toe te voegen.

De [JCR-query-werkblad](#jcr-query-cheatsheet) geeft een overzicht van de beschikbare beperkingen en geeft ook aan hoe een indexdefinitie eruit moet zien zodat deze wordt opgepikt. Gebruik de [Query-prestaties](#query-performance-tool) om de vraag te testen en ervoor te zorgen dat de juiste index wordt gebruikt en dat de vraagmotor geen beperkingen buiten de index hoeft te evalueren.


### Volgorde

Als een specifieke orde van het resultaat wordt gevraagd, zijn er twee manieren voor de Motor van de Vraag om dit te bereiken:

1. Of de index kan het resultaat volledig en in de juiste orde leveren; dit werkt als de eigenschappen die voor het opdracht geven tot worden gebruikt met worden geannoteerd ```ordered=true``` in de indexdefinitie.
2. Als de Motor van de Vraag het filtreren buiten de index moet uitvoeren of als het het opdracht geven tot bezit niet met geannoteerd is ```ordered=true``` eigenschap, voert de Motor van de Vraag ook het het opdracht geven tot proces uit. In dit geval moet de volledige resultaatset in het geheugen worden gelezen om te sorteren. Dit is veel langzamer dan de eerste optie.





### De resultaatgrootte beperken

De teruggewonnen grootte van het vraagresultaat is een belangrijke factor in vraagprestaties. Aangezien het resultaat op een luie manier wordt gehaald, is er een verschil in enkel het halen van de eerste 20 resultaten in vergelijking met het halen van 10.000 resultaten, zowel in runtime als geheugengebruik.

Dit betekent ook dat de grootte van de resultaatset alleen correct kan worden bepaald als alle resultaten worden opgehaald. Om deze reden zou de opgehaalde resultaatreeks altijd moeten worden beperkt, of door de vraag (zie [JCR-query-werkblad](#jcr-query-cheatsheet) voor meer informatie) of door de leesvolgorde van de resultaten te beperken.
Een dergelijke limiet voorkomt ook dat de query-engine de **traversale limiet** van 100.000 knopen, wat tot een gedwongen einde van de vraag leidt.

Zie de sectie [Zoekopdrachten met grote resultaten](#queries-with-large-result-sets) hieronder als een potentieel grote resultaatreeks volledig moet worden verwerkt.


## JCR-query-controle

Ter ondersteuning van de creatie van efficiënte JCR-query&#39;s en indexdefinities [JCR-query - Cheat Sheet](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/practices/best-practices-for-queries-and-indexing.html#jcrquerycheatsheet) kan tijdens de ontwikkeling worden gedownload en gebruikt als referentie. Het bevat steekproefvragen voor QueryBuilder, XPath en SQL-2, die veelvoudige scenario&#39;s behandelen die zich verschillend in termen van vraagprestaties gedragen. Het verstrekt ook aanbevelingen voor om indexen van het Eak te bouwen of aan te passen. De inhoud van dit Cheat Sheet is van toepassing op AEM 6.5 en AEM as a Cloud Service.


## Vragen met grote resultaatsets

Hoewel het wordt geadviseerd om vragen met een grote resultaatreeks te vermijden, zijn er geldige gevallen waar het grote resultaat moet worden verwerkt. Vaak is de omvang van het resultaat niet van tevoren bekend, dus moeten er voorzorgsmaatregelen worden genomen om de verwerking betrouwbaar te maken.

* de query mag niet worden uitgevoerd binnen een verzoek; in plaats daarvan zou de vraag als deel van een het Verkopen Baan of een AEM werkschema moeten worden uitgevoerd. Deze hebben geen beperkingen in hun totale runtime, en zijn opnieuw begonnen voor het geval de instantie tijdens de verwerking van de vraag en zijn resultaten daalt.
* Om de vraaggrens van 100.000 gelezen knopen te overwinnen zou u moeten overwegen te gebruiken [Hoofdsetpaginering](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) en splitst de query in meerdere subquery&#39;s.



## Vraag die de gegevensopslagplaats oversteekt

Zoekopdrachten die de gegevensopslagruimte doorlopen, maken geen gebruik van een index en registreren een bericht als deze:

```text
28.06.2022 13:32:52.804 *WARN* [127.0.0.1 [1656415972414] POST /libs/settings/granite/operations/diagnosis/granite_queryperformance.explain.json HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.Cursors$TraversingCursor Traversed 98000 nodes with filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a /* xpath: //* */, path=*) called by com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet.getHeuristics; consider creating an index or changing the query
```

Dit logboekfragment bevat relevante informatie:

* de vraag zelf: ```//* ```
* de Java-code die deze query heeft uitgevoerd: ```com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet::getHeuristics```; dit helpt om de schepper van deze vraag te identificeren.

Met deze informatie is het mogelijk om deze query te optimaliseren met de methoden die worden beschreven in [Zoekopdrachten optimaliseren](#optimizing-queries).