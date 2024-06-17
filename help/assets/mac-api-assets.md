---
title: Elementen HTTP-API
description: Digitale middelen maken, lezen, bijwerken, verwijderen en beheren met HTTP API in [!DNL Experience Manager Assets].
contentOwner: AG
feature: Assets HTTP API
role: Developer, Architect, Admin
exl-id: a3b7374d-f24b-4d6f-b6db-b9c9c962bb8d
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '1671'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager Assets] HTTP-API {#assets-http-api}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/extending/mac-api-assets.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

## Overzicht {#overview}

De [!DNL Assets] Met de HTTP-API kunt u CRUD-bewerkingen (read-read-update-delete) maken voor digitale elementen, waaronder metagegevens, uitvoeringen en opmerkingen, en voor gestructureerde inhoud met gebruik van [!DNL Experience Manager] Inhoudsfragmenten Het wordt blootgesteld bij `/api/assets` en is geïmplementeerd als REST API. Hieronder vallen [ondersteuning voor inhoudsfragmenten](/help/assets/content-fragments/assets-api-content-fragments.md).

>[!NOTE]
>
> Er is een gemoderniseerde OpenAPI-implementatie van de API voor contentfragmentbeheer beschikbaar. Zie voor volledige documentatie [Content Fragment Management API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/). Het wordt aanbevolen de nieuwe OpenAPI-implementatie te gebruiken. Het bestaande gebruik van middelen HTTP API voor inhoudsfragmenten moet worden gemigreerd naar de nieuwe OpenAPI voor contentfragmentbeheer.

De API openen:

1. Open het API-servicedocument op `https://[hostname]:[port]/api.json`.
1. Volg de [!DNL Assets] servicekoppeling die leidt naar `https://[hostname]:[server]/api/assets.json`.

De API-reactie is een JSON-bestand voor sommige MIME-typen en een antwoordcode voor alle MIME-typen. Het JSON-antwoord is optioneel en is mogelijk niet beschikbaar, bijvoorbeeld voor PDF-bestanden. Vertrouw op de antwoordcode voor verdere analyse of acties.

>[!NOTE]
>
>Alle API-aanroepen die betrekking hebben op het uploaden of bijwerken van elementen of binaire bestanden in het algemeen (zoals uitvoeringen) zijn vervangen door [!DNL Experience Manager] als [!DNL Cloud Service] implementatie. Gebruik voor het uploaden van binaire bestanden [directe binaire upload-API&#39;s](developer-reference-material-apis.md#asset-upload) in plaats daarvan.

## Inhoudsfragmenten {#content-fragments}

A [Inhoudsfragment](/help/assets/content-fragments/content-fragments.md) is een speciaal soort actief. Het kan worden gebruikt om tot gestructureerde gegevens, zoals teksten, aantallen, data toegang te hebben. Aangezien er verschillende verschillen zijn tussen `standard` elementen (zoals afbeeldingen of documenten), zijn enkele aanvullende regels van toepassing op de afhandeling van inhoudsfragmenten.

Zie voor meer informatie [Ondersteuning voor inhoudsfragmenten in het dialoogvenster [!DNL Experience Manager Assets] HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md).

>[!NOTE]
>
>De [Inhoudsfragment en Inhoudsfragmentmodel OpenAPI&#39;s](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

## Gegevensmodel {#data-model}

De [!DNL Assets] HTTP API stelt twee belangrijke elementen, omslagen en activa (voor standaardactiva) bloot. Bovendien worden meer gedetailleerde elementen beschikbaar gesteld voor aangepaste gegevensmodellen die gestructureerde inhoud in Content Fragments beschrijven. Zie [Gegevensmodellen van inhoudsfragmenten](/help/assets/content-fragments/assets-api-content-fragments.md#content-models-and-content-fragments) voor nadere informatie.

>[!NOTE]
>
>De [Inhoudsfragment en Inhoudsfragmentmodel OpenAPI&#39;s](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

### Mappen {#folders}

Mappen zijn vergelijkbaar met mappen zoals in traditionele bestandssystemen. De map kan alleen elementen, alleen mappen of mappen en elementen bevatten. Mappen hebben de volgende componenten:

**Entiteiten**: De entiteiten van een map zijn onderliggende elementen, mappen en elementen.

**Eigenschappen**:

* `name` is de naam van de map. Dit is het zelfde als het laatste segment in de weg URL zonder de uitbreiding.
* `title` is een optionele titel van de map die in plaats van de naam kan worden weergegeven.

>[!NOTE]
>
>Sommige eigenschappen van map of element worden toegewezen aan een ander voorvoegsel. De `jcr` voorvoegsel `jcr:title`, `jcr:description`, en `jcr:language` worden vervangen door `dc` voorvoegsel Vandaar in de geretourneerde JSON, `dc:title` en `dc:description` bevatten de waarden van `jcr:title` en `jcr:description`, respectievelijk.

**Koppelingen** Mappen maken drie koppelingen zichtbaar:

* `self`: Koppeling naar zichzelf.
* `parent`: Koppeling naar de bovenliggende map.
* `thumbnail`: (Optioneel) koppeling naar een miniatuurafbeelding van een map.

### Assets {#assets}

In [!DNL Experience Manager] een element bevat de volgende elementen:

* De eigenschappen en metagegevens van het element.
* Oorspronkelijk geüpload binair bestand van het element.
* Meerdere uitvoeringen, zoals geconfigureerd. Dit kunnen afbeeldingen van verschillende grootten, video&#39;s van verschillende coderingen of uitgenomen pagina&#39;s van PDF of [!DNL Adobe InDesign] bestanden.
* Optionele opmerkingen.

Zie voor informatie over elementen in inhoudsfragmenten [Ondersteuning voor inhoudsfragmenten in Experience Manager Assets HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md).

>[!NOTE]
>
>De [Inhoudsfragment en Inhoudsfragmentmodel OpenAPI&#39;s](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

In [!DNL Experience Manager] een map bevat de volgende componenten:

* Entiteiten: De onderliggende elementen van activa zijn de uitvoeringen.
* Eigenschappen.
* Koppelingen.

## Beschikbare functies {#available-features}

De [!DNL Assets] HTTP API bevat de volgende functies:

* [Een mappenlijst ophalen](#retrieve-a-folder-listing).
* [Een map maken](#create-a-folder).
* [Een element maken (afgekeurd)](#create-an-asset)
* [Binair element bijwerken (afgekeurd)](#update-asset-binary).
* [Metagegevens van elementen bijwerken](#update-asset-metadata).
* [Een elementuitvoering maken](#create-an-asset-rendition).
* [Een elementuitvoering bijwerken](#update-an-asset-rendition).
* [Een middelenopmerking maken](#create-an-asset-comment).
* [Een map of element kopiëren](#copy-a-folder-or-asset).
* [Een map of element verplaatsen](#move-a-folder-or-asset).
* [Een map, element of uitvoering verwijderen](#delete-a-folder-asset-or-rendition).

>[!NOTE]
>
>Om de leesbaarheid te verbeteren, worden in de volgende voorbeelden de volledige cURL-notaties weggelaten. De notatie correleert met [Herstellen](https://github.com/micha/resty) Dit is een scriptwrapper voor cURL.

<!-- TBD: The Console Manager is not available now. So how to configure the below? 

**Prerequisites**

* Go to `https://[aem_server]:[port]/system/console/configMgr`.
* Navigate to **Adobe Granite CSRF Filter**.
* Make sure the property **Filter Methods** includes: POST, PUT, DELETE.
-->

## Een mappenlijst ophalen {#retrieve-a-folder-listing}

Haalt een Siren-weergave op van een bestaande map en van de onderliggende entiteiten (submappen of elementen).

**Verzoek**: `GET /api/assets/myFolder.json`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - succes.
* 404 - NIET GEVONDEN - map bestaat niet of is niet toegankelijk.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

**Antwoord**: De klasse van de geretourneerde entiteit is een middel of een map. De eigenschappen van ingesloten entiteiten vormen een subset van de volledige reeks eigenschappen van elke entiteit. Om een volledige vertegenwoordiging van de entiteit te verkrijgen, zouden de cliënten de inhoud van URL moeten terugwinnen waarop de verbinding met `rel` van `self`.

## Een map maken {#create-a-folder}

Maakt een `sling`: `OrderedFolder` op het opgegeven pad. Indien `*` wordt verstrekt in plaats van een knoopnaam, gebruikt servlet de parameternaam als knooppuntnaam. In het verzoek worden de volgende twee handelingen geaccepteerd:

* Een Sirene-weergave van de nieuwe map
* Een set naam-waardeparen, gecodeerd als `application/www-form-urlencoded` of `multipart`/ `form`- `data`. Dit is handig als u een map rechtstreeks vanuit een HTML-formulier wilt maken.

Ook kunnen eigenschappen van de map worden opgegeven als URL-queryparameters.

Een API-aanroep mislukt met een `500` antwoordcode als het bovenliggende knooppunt van het opgegeven pad niet bestaat. Een vraag keert een reactiecode terug `409` als de map bestaat.

**Parameters**: `name` is de mapnaam.

**Verzoek**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"title=My Folder"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - over succesvol maken.
* 409 - CONFLICT - als de map bestaat.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een element maken {#create-an-asset}

Zie [elementen uploaden](developer-reference-material-apis.md) voor informatie over hoe u een element maakt. U kunt geen middel tot stand brengen gebruikend HTTP API.

## Elementbinair bijwerken {#update-asset-binary}

Zie [elementen uploaden](developer-reference-material-apis.md) voor informatie over het bijwerken van middelenbinaire bestanden. U kunt een element binair niet bijwerken gebruikend HTTP API.

## Metagegevens van een element bijwerken {#update-asset-metadata}

Hiermee werkt u de metagegevenseigenschappen van het element bij. Als u een eigenschap in het dialoogvenster `dc:` naamruimte, wordt dezelfde eigenschap in de API bijgewerkt `jcr` naamruimte. De API synchroniseert de eigenschappen niet onder de twee naamruimten.

**Verzoek**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - als Asset met succes is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een elementuitvoering maken {#create-an-asset-rendition}

Een uitvoering voor een element maken. Als de naam van de parameter request niet wordt opgegeven, wordt de bestandsnaam gebruikt als naam voor de vertoning.

**Parameters**: De parameters zijn `name` voor de naam van de vertoning en `file` als bestandsverwijzing.

**Verzoek**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**Antwoordcodes**

* 201 - GEMAAKT - als de vertoning is gemaakt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een elementuitvoering bijwerken {#update-an-asset-rendition}

Updates vervangen respectievelijk een elementuitvoering door de nieuwe binaire gegevens.

**Verzoek**: `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - als de vertoning correct is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een opmerking toevoegen aan een element {#create-an-asset-comment}

**Parameters**: De parameters zijn `message` voor de berichttekst van de opmerking en `annotationData` voor de Annotatiegegevens in JSON-indeling.

**Verzoek**: `POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als Opmerking is gemaakt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map of element kopiëren {#copy-a-folder-or-asset}

Hiermee kopieert u een map of element die beschikbaar is op het opgegeven pad naar een nieuwe bestemming.

**Aanvraagkoppen**: De parameters zijn:

* `X-Destination` - een nieuwe doel-URI binnen het bereik van de API-oplossing waarnaar de bron moet worden gekopieerd.
* `X-Depth` - hetzij `infinity` of `0`. Gebruiken `0` kopieert alleen de bron en zijn eigenschappen en niet zijn kinderen.
* `X-Overwrite` - Gebruik `F` om te voorkomen dat een actief op de bestaande bestemming wordt overschreven.

**Verzoek**: `COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als de map/het element naar een niet-bestaand doel is gekopieerd.
* 204 - GEEN INHOUD - als de map of het middel naar een bestaande bestemming is gekopieerd.
* 412 - PRECONDITION MISLUKT - als een aanvraagkoptekst ontbreekt.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map of element verplaatsen {#move-a-folder-or-asset}

Hiermee verplaatst u een map of element op het opgegeven pad naar een nieuwe bestemming.

**Aanvraagkoppen**: De parameters zijn:

* `X-Destination` - een nieuwe doel-URI binnen het bereik van de API-oplossing waarnaar de bron moet worden gekopieerd.
* `X-Depth` - hetzij `infinity` of `0`. Gebruiken `0` kopieert alleen de bron en zijn eigenschappen en niet zijn kinderen.
* `X-Overwrite` - Gebruik beide `T` om bestaande bronnen op geforceerde wijze te verwijderen of `F` om te voorkomen dat een bestaande bron wordt overschreven.

**Verzoek**: `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als de map/het element naar een niet-bestaand doel is gekopieerd.
* 204 - GEEN INHOUD - als de map of het middel naar een bestaande bestemming is gekopieerd.
* 412 - PRECONDITION MISLUKT - als een aanvraagkoptekst ontbreekt.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map, element of uitvoering verwijderen {#delete-a-folder-asset-or-rendition}

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

* Na de [!UICONTROL Off Time], een actief en de uitleveringen ervan niet beschikbaar zijn via de [!DNL Assets] en via de HTTP-API. De API geeft een foutbericht van 404 als de [!UICONTROL On Time] in de toekomst is of [!UICONTROL Off Time] is in het verleden.

* De HTTP-API van middelen retourneert de volledige metagegevens niet. De naamruimten zijn gecodeerd en alleen die naamruimten worden geretourneerd. Zie het middelenpad voor volledige metagegevens `/jcr_content/metadata.json`.

* Sommige eigenschappen van map of element worden toegewezen aan een ander voorvoegsel wanneer ze worden bijgewerkt met behulp van API&#39;s. De `jcr` voorvoegsel `jcr:title`, `jcr:description`, en `jcr:language` worden vervangen door `dc` voorvoegsel Vandaar in de geretourneerde JSON, `dc:title` en `dc:description` bevatten de waarden van `jcr:title` en `jcr:description`, respectievelijk.

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Middelen publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Referentiedocumenten voor ontwikkelaars voor [!DNL Assets]](/help/assets/developer-reference-material-apis.md)
