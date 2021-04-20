---
title: HTTP-API voor assets
description: Digitale elementen maken, lezen, bijwerken, verwijderen en beheren met de HTTP API in [!DNL Experience Manager Assets].
contentOwner: AG
feature: Assets HTTP API,APIs
role: Developer,Architect,Administrator
exl-id: a3b7374d-f24b-4d6f-b6db-b9c9c962bb8d
translation-type: tm+mt
source-git-commit: b989833b7f1fa0c3de91f96e28a21859d97294cb
workflow-type: tm+mt
source-wordcount: '1516'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager Assets] HTTP-API  {#assets-http-api}

## Overzicht {#overview}

Met de HTTP-API [!DNL Assets] kunt u CRUD-bewerkingen (read-read-update-delete) maken op digitale elementen, waaronder metagegevens, uitvoeringen en opmerkingen, en op gestructureerde inhoud met behulp van [!DNL Experience Manager] Inhoudsfragmenten. Deze wordt weergegeven op `/api/assets` en wordt geïmplementeerd als REST API. Het omvat [steun voor Inhoudsfragmenten](/help/assets/content-fragments/assets-api-content-fragments.md).

Toegang krijgen tot de API:

1. Open het API-servicedocument op `https://[hostname]:[port]/api.json`.
1. Volg de [!DNL Assets] de dienstverbinding die aan `https://[hostname]:[server]/api/assets.json` leidt.

De API-reactie is een JSON-bestand voor sommige MIME-typen en een antwoordcode voor alle MIME-typen. Het JSON-antwoord is optioneel en is mogelijk niet beschikbaar, bijvoorbeeld voor PDF-bestanden. Vertrouw op de antwoordcode voor verdere analyse of acties.

>[!NOTE]
>
>Alle API-aanroepen met betrekking tot het uploaden of bijwerken van middelen of binaire bestanden in het algemeen (zoals uitvoeringen) zijn voor [!DNL Experience Manager] vervangen als een [!DNL Cloud Service]-implementatie. Voor het uploaden van binaire getallen, gebruik [directe binaire upload APIs](developer-reference-material-apis.md#asset-upload-technical) in plaats daarvan.

## Contentfragmenten {#content-fragments}

A [Inhoudsfragment](/help/assets/content-fragments/content-fragments.md) is een speciaal type element. Het kan worden gebruikt om tot gestructureerde gegevens, zoals teksten, aantallen, data toegang te hebben. Aangezien er verschillende verschillen zijn met `standard` elementen (zoals afbeeldingen of documenten), zijn enkele aanvullende regels van toepassing op de verwerking van inhoudsfragmenten.

Zie [Ondersteuning van inhoudsfragmenten in de  [!DNL Experience Manager Assets] HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md) voor meer informatie.

## Gegevensmodel {#data-model}

De [!DNL Assets] HTTP API stelt twee belangrijke elementen, omslagen en activa (voor standaardactiva) bloot. Bovendien worden meer gedetailleerde elementen beschikbaar gesteld voor aangepaste gegevensmodellen die gestructureerde inhoud in Content Fragments beschrijven. Zie [Gegevensmodellen van inhoudsfragmenten](/help/assets/content-fragments/assets-api-content-fragments.md#content-models-and-content-fragments) voor meer informatie.

### Mappen {#folders}

Mappen zijn vergelijkbaar met mappen zoals in traditionele bestandssystemen. De map kan alleen elementen, alleen mappen of mappen en elementen bevatten. Mappen hebben de volgende componenten:

**Entiteiten**: De entiteiten van een map zijn onderliggende elementen, mappen en elementen.

**Eigenschappen**:

* `name` is de naam van de map. Dit is het zelfde als het laatste segment in de weg URL zonder de uitbreiding.
* `title` is een optionele titel van de map die in plaats van de naam kan worden weergegeven.

>[!NOTE]
>
>Sommige eigenschappen van map of element worden toegewezen aan een ander voorvoegsel. Het voorvoegsel `jcr` van `jcr:title`, `jcr:description` en `jcr:language` worden vervangen door voorvoegsel `dc`. Daarom bevatten `dc:title` en `dc:description` in de geretourneerde JSON de waarden van respectievelijk `jcr:title` en `jcr:description`.

**** LinksMappen maken drie koppelingen zichtbaar:

* `self`: Koppeling naar zichzelf.
* `parent`: Koppeling naar de bovenliggende map.
* `thumbnail`: (Optioneel) koppeling naar een miniatuurafbeelding van een map.

### Assets {#assets}

In [!DNL Experience Manager] bevat een element de volgende elementen:

* De eigenschappen en metagegevens van het element.
* Oorspronkelijk geüpload binair bestand van het element.
* Meerdere uitvoeringen, zoals geconfigureerd. Dit kunnen afbeeldingen van verschillende grootten, video&#39;s van verschillende coderingen of uitgenomen pagina&#39;s uit PDF- of [!DNL Adobe InDesign]-bestanden zijn.
* Optionele opmerkingen.

Zie [Ondersteuning van inhoudsfragmenten in HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md) voor informatie over elementen in inhoudsfragmenten.

In [!DNL Experience Manager] heeft een map de volgende componenten:

* Entiteiten: De onderliggende elementen van activa zijn de uitvoeringen.
* Eigenschappen.
* Koppelingen.

## Beschikbare functies {#available-features}

De [!DNL Assets] HTTP-API bevat de volgende functies:

* [Haal een mappenlijst](#retrieve-a-folder-listing) op.
* [Maak een map](#create-a-folder).
* [Een element maken (afgekeurd)](#create-an-asset)
* [Binair element bijwerken (afgekeurd)](#update-asset-binary).
* [Metagegevens](#update-asset-metadata) van elementen bijwerken.
* [Een elementuitvoering](#create-an-asset-rendition) maken.
* [Een elementuitvoering](#update-an-asset-rendition) bijwerken.
* [Maak een middelenopmerking](#create-an-asset-comment).
* [Kopieer een map of element](#copy-a-folder-or-asset).
* [Een map of element](#move-a-folder-or-asset) verplaatsen.
* [Een map, element of uitvoering](#delete-a-folder-asset-or-rendition) verwijderen.

>[!NOTE]
>
>Om de leesbaarheid te verbeteren, worden in de volgende voorbeelden de volledige cURL-notaties weggelaten. De notatie correleert met [Resty](https://github.com/micha/resty) die een manuscriptomslag voor cURL is.

<!-- TBD: The Console Manager is not available now. So how to configure the below? 

**Prerequisites**

* Go to `https://[aem_server]:[port]/system/console/configMgr`.
* Navigate to **Adobe Granite CSRF Filter**.
* Make sure the property **Filter Methods** includes: POST, PUT, DELETE.
-->

## Een map ophalen {#retrieve-a-folder-listing}

Haalt een Siren-weergave op van een bestaande map en van de onderliggende entiteiten (submappen of elementen).

**Verzoek**:  `GET /api/assets/myFolder.json`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - succes.
* 404 - NIET GEVONDEN - map bestaat niet of is niet toegankelijk.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

**Reactie**: De klasse van de geretourneerde entiteit is een middel of een map. De eigenschappen van ingesloten entiteiten vormen een subset van de volledige reeks eigenschappen van elke entiteit. Om een volledige vertegenwoordiging van de entiteit te verkrijgen, zouden de cliënten de inhoud van URL moeten terugwinnen die door de verbinding met een `rel` van `self` wordt gericht.

## Een map {#create-a-folder} maken

Hiermee maakt u een `sling`: `OrderedFolder` op het opgegeven pad. Als `*` in plaats van een knooppuntnaam wordt verstrekt, gebruikt servlet de parameternaam als knooppuntnaam. In het verzoek worden de volgende twee handelingen geaccepteerd:

* Een Sirene-weergave van de nieuwe map
* Een reeks naam-waardeparen, gecodeerd als `application/www-form-urlencoded` of `multipart`/ `form`- `data`. Dit is handig als u een map rechtstreeks vanuit een HTML-formulier wilt maken.

Ook kunnen eigenschappen van de map worden opgegeven als URL-queryparameters.

Een API-aanroep mislukt met een `500`-antwoordcode als het bovenliggende knooppunt van het opgegeven pad niet bestaat. Een vraag keert een antwoordcode `409` terug als de omslag bestaat.

**Parameters**:  `name` is de mapnaam.

**Verzoek**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"title=My Folder"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - over succesvol maken.
* 409 - CONFLICT - als de map bestaat.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Elementen {#create-an-asset} maken

Zie [asset upload](developer-reference-material-apis.md) voor informatie over het maken van een element. U kunt geen middel tot stand brengen gebruikend HTTP API.

## Elementbinair {#update-asset-binary} bijwerken

Zie [Elementupload](developer-reference-material-apis.md) voor informatie over het bijwerken van elementbinaire bestanden. U kunt een element binair niet bijwerken gebruikend HTTP API.

## Metagegevens van een element {#update-asset-metadata} bijwerken

Werkt de metagegevenseigenschappen van het element bij. Als u een eigenschap bijwerkt in de naamruimte `dc:`, werkt de API dezelfde eigenschap bij in de naamruimte `jcr`. De API synchroniseert de eigenschappen niet onder de twee naamruimten.

**Verzoek**:  `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - als Asset met succes is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een elementuitvoering maken {#create-an-asset-rendition}

Een uitvoering voor een element maken. Als de naam van de parameter request niet wordt opgegeven, wordt de bestandsnaam gebruikt als naam voor de vertoning.

**Parameters**: De parameters zijn  `name` voor naam van de vertoning en  `file` als dossierverwijzing.

**Verzoek**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**Antwoordcodes**

* 201 - GEMAAKT - als de vertoning is gemaakt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Elementuitvoering {#update-an-asset-rendition} bijwerken

Updates vervangen respectievelijk een elementuitvoering door de nieuwe binaire gegevens.

**Verzoek**:  `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - als de vertoning correct is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Opmerking toevoegen aan een element {#create-an-asset-comment}

**Parameters**: De parameters zijn  `message` voor de berichttekst van de opmerking en  `annotationData` voor de annotatiegegevens in JSON-indeling.

**Verzoek**:  `POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als Opmerking is gemaakt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map of element kopiëren {#copy-a-folder-or-asset}

Hiermee kopieert u een map of element die beschikbaar is op het opgegeven pad naar een nieuwe bestemming.

**Aanvraagkoppen**: De parameters zijn:

* `X-Destination` - een nieuwe doel-URI binnen het bereik van de API-oplossing waarnaar de bron moet worden gekopieerd.
* `X-Depth` - hetzij  `infinity` hetzij  `0`. Wanneer u `0` gebruikt, worden alleen de bron en de eigenschappen ervan gekopieerd en niet de onderliggende elementen.
* `X-Overwrite` - Gebruik deze optie  `F` om te voorkomen dat een element op de bestaande bestemming wordt overschreven.

**Verzoek**:  `COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als de map/het element naar een niet-bestaand doel is gekopieerd.
* 204 - GEEN INHOUD - als de map of het middel naar een bestaande bestemming is gekopieerd.
* 412 - PRECONDITION MISLUKT - als een aanvraagkoptekst ontbreekt.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map of element verplaatsen {#move-a-folder-or-asset}

Hiermee verplaatst u een map of element op het opgegeven pad naar een nieuwe bestemming.

**Aanvraagkoppen**: De parameters zijn:

* `X-Destination` - een nieuwe doel-URI binnen het bereik van de API-oplossing waarnaar de bron moet worden gekopieerd.
* `X-Depth` - hetzij  `infinity` hetzij  `0`. Wanneer u `0` gebruikt, worden alleen de bron en de eigenschappen ervan gekopieerd en niet de onderliggende elementen.
* `X-Overwrite` - Gebruik deze optie  `T` om bestaande bronnen te verwijderen of  `F` om te voorkomen dat bestaande bronnen worden overschreven.

**Verzoek**:  `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als de map/het element naar een niet-bestaand doel is gekopieerd.
* 204 - GEEN INHOUD - als de map of het middel naar een bestaande bestemming is gekopieerd.
* 412 - PRECONDITION MISLUKT - als een aanvraagkoptekst ontbreekt.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map, element of uitvoering {#delete-a-folder-asset-or-rendition} verwijderen

Hiermee verwijdert u een resource (-tree) bij het opgegeven pad.

**Verzoek**

* `DELETE /api/assets/myFolder`
* `DELETE /api/assets/myFolder/myAsset.png`
* `DELETE /api/assets/myFolder/myAsset.png/renditions/original`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - als de map is verwijderd.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Tips, aanbevolen procedures en beperkingen {#tips-limitations}

* Na [!UICONTROL Off Time] zijn een middel en zijn vertoningen niet beschikbaar via de [!DNL Assets] Webinterface en door HTTP API. De API retourneert een foutbericht van 404 als [!UICONTROL On Time] in de toekomst is of als [!UICONTROL Off Time] in het verleden is.

* De HTTP-API van middelen retourneert de volledige metagegevens niet. De naamruimten zijn gecodeerd en alleen die naamruimten worden geretourneerd. Zie het elementpad `/jcr_content/metadata.json` voor volledige metagegevens.

* Sommige eigenschappen van map of element worden toegewezen aan een ander voorvoegsel wanneer ze worden bijgewerkt met behulp van API&#39;s. Het voorvoegsel `jcr` van `jcr:title`, `jcr:description` en `jcr:language` worden vervangen door voorvoegsel `dc`. Daarom bevatten `dc:title` en `dc:description` in de geretourneerde JSON de waarden van respectievelijk `jcr:title` en `jcr:description`.

>[!MORELIKETHIS]
>
>* [Referentiedocumenten voor ontwikkelaars voor [!DNL Assets]](/help/assets/developer-reference-material-apis.md)

