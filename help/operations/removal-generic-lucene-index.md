---
title: Verwijdering van de generieke index van de lucene
description: Verwijdering van de generieke index van de lucene
exl-id: fe0e00ac-f9c8-43cf-83c2-5a353f5eaeab
source-git-commit: bc7ef6567ad5baa4becd28a7e7d96bd6b579e1ad
workflow-type: tm+mt
source-wordcount: '1305'
ht-degree: 0%

---

# Verwijdering van de generieke lucene-index

Adobe is van plan de generieke lucene-index (`/oak:index/lucene-*`) van Adobe Experience Manager as a Cloud Service. Deze index is vervangen sinds AEM 6.5. In deze documentatie wordt het effect van dit besluit beschreven, samen met gedetailleerde beschrijvingen hoe te om te onderzoeken of een AEM geval wordt beïnvloed. Tot slot bevat het manieren om vragen te veranderen zodat werken zij zonder deze index aanwezig te zijn.

## Achtergrond

In AEM &#39;fulltext&#39; wordt gezocht naar de volgende functies:

* `jcr:contains()` in JCR XPATH
* `CONTAINS` in JCR-SQL2

Dergelijke vragen kunnen geen resultaten zonder een index terugkeren. In tegenstelling tot een vraag die slechts weg of bezitsbeperkingen bevat, zal een vraag die een fulltext beperking bevat waarvoor geen index kan worden gevonden (en zo wordt een traversal uitgevoerd) altijd 0 resultaten terugkeren.

De generieke lucene-index (`/oak:index/lucene-*`) bestaat sinds AEM 6.0 / Eak 1.0 om een full-text zoekopdracht te geven in de meeste repository hiërarchie (sommige paden, zoals `/jcr:system` en `/var` zijn altijd van dit uitgesloten) maar deze index is grotendeels vervangen door indexen op meer specifieke knooppunttypen (bijvoorbeeld `damAssetLucene-*` voor de notatie &#39;dam:Asset&#39;) die zowel fullText- als eigenschapzoekopdrachten ondersteunt.

In AEM 6.5 werd de &quot;generische lucene&quot;index duidelijk zoals afgekeurd (erop gewezen dat het in toekomstige versies) zou worden verwijderd, en sindsdien is WARN geregistreerd toen de index is gebruikt:

```
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'search term') and isdescendantnode(a, '/content/mysite') /* xpath: /jcr:root/content/mysite//*[jcr:contains(.,"search term")] */ fullText="search" "term", path=/content/mysite//*). Please change the query or the index definitions.
```

In recente AEM versies is de index &#39;generic lucene&#39; gebruikt om een zeer klein aantal functies te ondersteunen. Deze worden opnieuw bewerkt om andere indexen te gebruiken of anderszins aangepast om de afhankelijkheid van deze index te verwijderen.
Zoekopdrachten met &#39;referentie lookup&#39;, van de hieronder weergegeven vorm, moeten nu bijvoorbeeld de index gebruiken op &#39;/oak:index/pathreference&#39; (die alleen waarden van String-eigenschappen indexeert die overeenkomen met een reguliere expressie die naar JCR-paden zoekt). 

```
//*[jcr:contains(., '"/content/dam/mysite"')]
```

Om grotere gegevensvolumes van klanten te ondersteunen, zal Adobe niet langer de &quot;generische lucene&quot;index op nieuwe AEM as a Cloud Service milieu&#39;s creëren en, daarna, zal beginnen de index uit bestaande bewaarplaatsen te verwijderen. We hebben de indexkosten al aangepast (via de eigenschappen &#39;costPerEntry&#39; en &#39;costPerExecution&#39;) om ervoor te zorgen dat andere indexen (zoals `/oak:index/pathreference`) wordt bij voorkeur gebruikt `/oak:index/lucene-*` waar mogelijk. 

De toepassingen van de klant die vragen gebruiken die nog afhankelijk van deze index zijn zouden onmiddellijk moeten worden bijgewerkt om andere bestaande indexen (die indien nodig kunnen worden aangepast) of nieuwe douaneindexen aan de klantentoepassing worden toegevoegd. Volledige instructies voor indexbeheer in AEM as a Cloud Service zijn te vinden op de [indexeringsdocumentatie](/help/operations/indexing.md).

## Hoe te om te zien of hangt uw toepassing van de &quot;generische lucene&quot;index af?

De generische lucene-index wordt momenteel gebruikt als een &#39;fallback&#39; als geen andere fulltext-index een query kan uitvoeren. Wanneer deze afgekeurde index wordt gebruikt, zal een bericht als dit op WARN niveau worden geregistreerd:

```
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*). Please change the query or the index definitions.
```

In sommige gevallen probeert Oak een andere fulltext-index te gebruiken (zoals `/oak:index/pathreference`) om de fulltext vraag te steunen, maar als het vraagkoord niet de regelmatige uitdrukking op de indexdefinitie aanpast, zal een bericht op WARN niveau worden geregistreerd en de vraag zal waarschijnlijk geen resultaten terugkeren.

```
org.apache.jackrabbit.oak.query.QueryImpl Potentially improper use of index /oak:index/pathReference with queryFilterRegex (["']|^)/ to search for value "test"
```

Zodra de &quot;generische lucene&quot;index is verwijderd, zal een bericht zoals hieronder getoond op WARN niveau worden geregistreerd als een fulltext vraag van geen geschikte indexdefinitie kan de plaats bepalen:

```
org.apache.jackrabbit.oak.query.QueryImpl Fulltext query without index for filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*); no results will be returned
```

Als om het even welk van deze het programma wordt geopend, zou u de vraag kunnen moeten herwerken om een verschillende fulltext index te gebruiken, of een nieuwe index verstrekken om de vraag te steunen. De details van de types van gebiedsdelen u zou kunnen zien, en hoe te om hen te richten, worden verstrekt hieronder.

## Mogelijke afhankelijkheden van de index van &quot;generieke lucene&quot;

### Publicatie

#### Aangepaste query&#39;s voor toepassingen

De gemeenschappelijkste bron van vragen die de &quot;generische lucene&quot;index bij Publish gebruiken zal vragen van de douanetoepassing zijn.

In de eenvoudigste gevallen kunnen dit query&#39;s zijn waarvoor geen nodetype is opgegeven (dit betekent &#39;nt:base&#39;) of nt:base die expliciet is opgegeven, zoals:

```
/jcr:root/content/mysite//*[jcr:contains(., 'search term')]
/jcr:root/content/mysite//element(*, nt:base)[jcr:contains(., 'search term')]
```

Vereiste actie: Deze query&#39;s kunnen worden gewijzigd om een geschikt nodetype te gebruiken. De query zou bijvoorbeeld resultaten kunnen opleveren die overeenkomen met pagina&#39;s (of een van de &#39;aggregaten&#39; onder het knooppunt cq:Page):

```
/jcr:root/content/mysite//element(*, cq:Page)[jcr:contains(., 'search term')]
```

In andere gevallen, zou een vraag een nodetype kunnen specificeren maar een fulltext beperking bevatten die niet door een andere fulltext index kan worden behandeld, zoals:

```
/jcr:root/content/dam//element(*, dam:Asset)[jcr:contains(jcr:content/metadata/@cq:tags, 'NewsTopics:cateogries/domestic'))]
```

In dit geval heeft de query het nodetype &#39;dam:Asset&#39;, maar bevat de query een fulltext beperking op het relatieve `jcr:content/metadata/@cq:tags` eigenschap.

Deze eigenschap is niet gemarkeerd als &#39;analyzed&#39; in de damAssetLucene-index (de fulltext-index die het meest wordt gebruikt voor query&#39;s tegen het &#39;dam:Asset&#39;-notatietype), zodat deze index niet kan worden gebruikt voor deze query.

Als dusdanig, valt de vraag terug op de &quot;generische fulltext&quot;index waar alle inbegrepen eigenschappen zoals geanalyseerd door de vervangingsgelijke bij duidelijk zijn `/oak:index/lucene-2/indexRules/nt:base/properties/prop`.

Handeling van de klant vereist: het markeren van `jcr:content/metadata/@cq:tags` eigenschap als &#39;analyzed&#39; in een aangepaste versie van de damAssetLucene-index resulteert in de verwerking van deze query door deze index en er wordt geen WARN geregistreerd.

### Auteur 

Naast vragen in de servers van de klantentoepassing, componenten OSGI en het teruggeven van manuscripten kan er een aantal auteur-specifieke toepassingen van de &quot;generische lucene&quot;index zijn. 

#### Referentiezoekopdracht

In het verleden is de index &#39;generic lucene&#39; gebruikt ter ondersteuning van &#39;reference search&#39; (zoeken naar inhoud die verwijzingen naar een ander inhoudspad bevat). Dergelijke query&#39;s moeten al zijn verplaatst om de nieuwe index &#39;/eikel:index/padreference&#39; te gebruiken.
Handeling van de klant vereist: geen actie van de klant vereist.


#### Pathfield-kiezer zoeken

AEM bevat een aangepaste component voor het dialoogvenster (Sling resource type &#39;granite/ui/components/koral/foundation/form/pathfield&#39;) waarmee u een browser (kiezer) kunt gebruiken voor het selecteren van een ander AEM.  De standaardpadveldkiezer (die wordt gebruikt wanneer er geen aangepaste eigenschap &#39;pickerSrc&#39; is gedefinieerd in de inhoudsstructuur) geeft een zoekbalk in het pop-updialoogvenster weer.
De knooptypes waartegen aan onderzoek-tegen kunnen worden gespecificeerd gebruikend het &quot;nodeTypes&quot;bezit.

Momenteel, als geen &quot;nodeTypes&quot;bezit aanwezig is, zal de onderliggende onderzoeksvraag het &quot;nt:base&quot;nodetype gebruiken, en zal daarom waarschijnlijk de &quot;generische lucene&quot;index gebruiken (typisch registrerend de WAARSCHUWINGSberichten die hieronder worden getoond).

```
20.01.2022 18:56:06.412 *WARN* [127.0.0.1 [1642704966377] POST /mnt/overlay/granite/ui/content/coral/foundation/form/pathfield/picker.result.single.html HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') and isdescendantnode(a, '/content') /* xpath: /jcr:root/content//element(*, nt:base)[(jcr:contains(., 'test'))] order by @jcr:score descending */ fullText="test", path=/content//*). Please change the query or the index definitions.
```

Voorafgaand aan verwijdering van &quot;generische luceen&quot;, zal de pathfield component worden bijgewerkt zodat het onderzoeksvakje voor componenten verborgen gebruikend de standaardplukker is, die geen &quot;nodeTypes&quot;bezit verstrekken.

| Pathfield-kiezer met zoeken | Pathfield-kiezer zonder zoeken |
|---|---|
| ![Pathfield-kiezer met zoeken](assets/index-pathfield-picker-with-search.png) | ![Pathfield-kiezer zonder zoeken](assets/index-pathfield-picker-without-search.png) |


Handeling van de klant vereist: Als geen onderzoek wordt vereist, wordt geen actie vereist van de klant.

Als de klant de functionaliteit van het Onderzoek binnen pathfeld plukker zou willen behouden, zou een bezit &quot;nodeTypes&quot;moeten worden verstrekt die van de knooptypes een lijst maken waartegen zij zouden willen vragen. Deze kunnen als komma-gescheiden lijst van nodetypes in een bezit van het Koord worden gespecificeerd.


>[!NOTE]
>De Redacteur van het ModelModel van het Fragment van de Inhoud gebruikt een gespecialiseerde pathfields met het Sling Type van Middel &quot;dam/cfm/models/editor/components/contentReference&quot;.
> * Momenteel voeren deze vragen zonder gespecificeerde knooptypes uit - resulterend in een WARN die wegens gebruik van de &quot;generische lucene&quot;index wordt geregistreerd.
> * Instanties van deze componenten worden binnenkort automatisch standaard ingesteld op het gebruik van &#39;cq:Page&#39;- en &#39;dam:Asset&#39;-nodetypes zonder verdere actie van de klant.
> * De eigenschap &#39;nodeTypes&#39; kan worden toegevoegd om deze standaardknooppunten te overschrijven. 





## Tijdlijn voor het verwijderen van &#39;generieke glucose&#39;

Adobe zal een tweefasenaanpak volgen om de generieke lucene-index te schrappen.

**Fase 1** (geplande start op 31 januari 2022): U kunt &#39;/ak:index/lucene-*&#39; niet meer maken in nieuwe AEM as a Cloud Service omgevingen.

**Fase 2** (gepland begin 31 maart 2022) : Verwijder de index &#39;/oak:index/lucene-*&#39; uit nieuwe AEM as a Cloud Service omgevingen.

Adobe zal de hierboven vermelde logboekberichten controleren en zal proberen om klanten te contacteren die afhankelijk van de &quot;generische lucene&quot;index blijven.

Als kortetermijnmatiging, indien nodig zal Adobe de definities van de douaneindex aan klantensystemen direct toevoegen om functionele of prestatieskwesties als resultaat van de verwijdering van de &quot;generische lucene&quot;index te verhinderen.

In dergelijke gevallen krijgt de klant de bijgewerkte indexdefinitie en wordt hem geadviseerd deze op te nemen in toekomstige versies van zijn toepassing via Cloud Manager.
