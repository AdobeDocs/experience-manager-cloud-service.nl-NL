---
title: ASSETS HTTP API
description: Creeer, lees, update, schrap, beheer digitale activa gebruikend HTTP API in  [!DNL Experience Manager Assets].
contentOwner: AG
feature: Assets HTTP API
role: Developer, Architect, Admin
exl-id: a3b7374d-f24b-4d6f-b6db-b9c9c962bb8d
source-git-commit: 4cec40947f1b50dd627321cabfbe43033a224f8b
workflow-type: tm+mt
source-wordcount: '1714'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager Assets] HTTP-API {#assets-http-api}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/extending/mac-api-assets.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

## Overzicht {#overview}

Met de HTTP-API van [!DNL Assets] kunt u CRUD-bewerkingen (read-read-update-delete) maken voor digitale elementen, waaronder metagegevens, vertoningen en opmerkingen, en voor gestructureerde inhoud met behulp van [!DNL Experience Manager] Inhoudsfragmenten. Deze wordt weergegeven in `/api/assets` en wordt geïmplementeerd als REST API. Het omvat [ steun voor de Fragmenten van de Inhoud ](/help/assets/content-fragments/assets-api-content-fragments.md).

>[!NOTE]
>
> Er is een gemoderniseerde OpenAPI-implementatie van de API voor contentfragmentbeheer beschikbaar. Voor volledige documentatie zie [ Beheer API van het Fragment van de Inhoud ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/). Het wordt aanbevolen de nieuwe OpenAPI-implementatie te gebruiken. Het bestaande gebruik van Assets HTTP API voor inhoudsfragmenten moet worden gemigreerd naar de nieuwe OpenAPI voor contentfragmentbeheer.

De API openen:

1. Open het API-servicedocument op `https://[hostname]:[port]/api.json` .
1. Volg de servicekoppeling [!DNL Assets] naar `https://[hostname]:[server]/api/assets.json` .

De API-reactie is een JSON-bestand voor sommige MIME-typen en een antwoordcode voor alle MIME-typen. Het JSON-antwoord is optioneel en is mogelijk niet beschikbaar, bijvoorbeeld voor PDF-bestanden. Vertrouw op de antwoordcode voor verdere analyse of acties.

>[!NOTE]
>
>Alle API-aanroepen die betrekking hebben op het uploaden of bijwerken van elementen of binaire bestanden in het algemeen (zoals uitvoeringen), zijn voor [!DNL Experience Manager] vervangen als een [!DNL Cloud Service] -implementatie. Voor het uploaden van binaire getallen, gebruik [ directe binaire upload APIs ](developer-reference-material-apis.md#asset-upload) in plaats daarvan.

## Inhoudsfragmenten {#content-fragments}

A [ het Fragment van de Inhoud ](/help/assets/content-fragments/content-fragments.md) is een speciaal type van activa. Het kan worden gebruikt om tot gestructureerde gegevens, zoals teksten, aantallen, data toegang te hebben. Aangezien er verschillende verschillen zijn tussen `standard` -elementen (zoals afbeeldingen of documenten), zijn er enkele aanvullende regels van toepassing op de afhandeling van inhoudsfragmenten.

Voor meer informatie, zie [ de steun van de Fragmenten van de Inhoud in  [!DNL Experience Manager Assets]  HTTP API ](/help/assets/content-fragments/assets-api-content-fragments.md).

>[!NOTE]
>
>Zie [ AEM APIs voor Gestructureerde Inhoudslevering en Beheer ](/help/headless/apis-headless-and-content-fragments.md) voor een overzicht van diverse beschikbare APIs en vergelijking van sommige betrokken concepten.
>
>Het [ Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

## Gegevensmodel {#data-model}

De [!DNL Assets] HTTP API stelt twee belangrijke elementen, omslagen en activa (voor standaardactiva) bloot. Bovendien worden meer gedetailleerde elementen beschikbaar gesteld voor aangepaste gegevensmodellen die gestructureerde inhoud in Content Fragments beschrijven. Zie {de gegevensmodellen van het Fragment van 0} Inhoud ](/help/assets/content-fragments/assets-api-content-fragments.md#content-models-and-content-fragments) voor verdere informatie.[

>[!NOTE]
>
>Het [ Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

### Mappen {#folders}

Mappen zijn vergelijkbaar met mappen zoals in traditionele bestandssystemen. De map kan alleen elementen, alleen mappen of mappen en elementen bevatten. Mappen hebben de volgende componenten:

**Entiteiten**: De entiteiten van een omslag zijn zijn kindelementen, die omslagen en activa kunnen zijn.

**Eigenschappen**:

* `name` is de naam van de map. Dit is het zelfde als het laatste segment in de weg URL zonder de uitbreiding.
* `title` is een optionele titel van de map die kan worden weergegeven in plaats van de naam ervan.

>[!NOTE]
>
>Sommige eigenschappen van map of element worden toegewezen aan een ander voorvoegsel. Het voorvoegsel `jcr` van `jcr:title` , `jcr:description` en `jcr:language` wordt vervangen door het voorvoegsel `dc` . Daarom bevatten `dc:title` en `dc:description` in de geretourneerde JSON de waarden van respectievelijk `jcr:title` en `jcr:description` .

**de Omslagen van Verbindingen** stellen drie verbindingen bloot:

* `self`: Koppeling naar zichzelf.
* `parent`: Koppeling naar de bovenliggende map.
* `thumbnail`: (Optioneel) koppel de miniatuurafbeelding van een map.

### Assets {#assets}

In [!DNL Experience Manager] bevat een element de volgende elementen:

* De eigenschappen en metagegevens van het element.
* Oorspronkelijk geüpload binair bestand van het element.
* Meerdere uitvoeringen, zoals geconfigureerd. Dit kunnen afbeeldingen van verschillende grootten, video&#39;s van verschillende coderingen of uitgenomen pagina&#39;s uit PDF- of [!DNL Adobe InDesign] bestanden zijn.
* Optionele opmerkingen.

Voor informatie over elementen in de Fragmenten van de Inhoud zie [ de Steun van de Fragmenten van de Inhoud in HTTP van Experience Manager Assets API ](/help/assets/content-fragments/assets-api-content-fragments.md).

>[!NOTE]
>
>Het [ Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

In [!DNL Experience Manager] heeft een map de volgende componenten:

* Entiteiten: De onderliggende elementen van activa zijn de uitvoeringen.
* Eigenschappen.
* Koppelingen.

## Beschikbare functies {#available-features}

De [!DNL Assets] HTTP API bevat de volgende functies:

* [ wint een omslaglijst ](#retrieve-a-folder-listing) terug.
* [ creeer een omslag ](#create-a-folder).
* [Een element maken (afgekeurd)](#create-an-asset)
* [ de activa binaire van de Update (afgekeurd) ](#update-asset-binary).
* [ de activameta-gegevens van de Update ](#update-asset-metadata).
* [ creeer een activa vertoning ](#create-an-asset-rendition).
* [ werk een activavertoning ](#update-an-asset-rendition) bij.
* [ creeer een activacommentaar ](#create-an-asset-comment).
* [ Kopieer een omslag of activa ](#copy-a-folder-or-asset).
* [ Beweeg een omslag of activa ](#move-a-folder-or-asset).
* [ Schrap een omslag, activa, of vertoning ](#delete-a-folder-asset-or-rendition).

>[!NOTE]
>
>Om de leesbaarheid te verbeteren, worden in de volgende voorbeelden de volledige cURL-notaties weggelaten. De aantekening correleert met [ Herstel ](https://github.com/micha/resty) dat een manuscriptomslag voor cURL is.

<!-- TBD: The Console Manager is not available now. So how to configure the below? 

**Prerequisites**

* Go to `https://[aem_server]:[port]/system/console/configMgr`.
* Navigate to **Adobe Granite CSRF Filter**.
* Make sure the property **Filter Methods** includes: POST, PUT, DELETE.
-->

## Een mappenlijst ophalen {#retrieve-a-folder-listing}

Haalt een Siren-weergave op van een bestaande map en van de onderliggende entiteiten (submappen of elementen).

**Verzoek**: `GET /api/assets/myFolder.json`

**de codes van de Reactie**: De antwoordcodes zijn:

* 200 - OK - succes.
* 404 - NIET GEVONDEN - map bestaat niet of is niet toegankelijk.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

**Reactie**: De klasse van de teruggekeerde entiteit is activa of een omslag. De eigenschappen van ingesloten entiteiten vormen een subset van de volledige reeks eigenschappen van elke entiteit. Om een volledige weergave van de entiteit te verkrijgen, moeten clients de inhoud ophalen van de URL waarnaar de koppeling verwijst met een `rel` van `self` .

## Een map maken {#create-a-folder}

Maakt een `sling`: `OrderedFolder` op het opgegeven pad. Als `*` wordt verstrekt in plaats van een knoopnaam, gebruikt servlet de parameternaam als knooppuntnaam. In het verzoek worden de volgende twee handelingen geaccepteerd:

* Een Sirene-weergave van de nieuwe map
* Een set naam-waardeparen, gecodeerd als `application/www-form-urlencoded` of `multipart`/ `form` - `data` . Dit is handig als u een map rechtstreeks vanuit een HTML-formulier wilt maken.

Ook kunnen eigenschappen van de map worden opgegeven als URL-queryparameters.

Een API-aanroep mislukt met een antwoordcode `500` als het bovenliggende knooppunt van het opgegeven pad niet bestaat. Een aanroep retourneert een antwoordcode `409` als de map bestaat.

**Parameters**: `name` is de omslagnaam.

**Verzoek**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"title=My Folder"`

**de codes van de Reactie**: De antwoordcodes zijn:

* 201 - GEMAAKT - over succesvol maken.
* 409 - CONFLICT - als de map bestaat.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een element maken {#create-an-asset}

Zie [ activa uploaden ](developer-reference-material-apis.md) voor informatie over hoe te om activa tot stand te brengen. U kunt geen middel tot stand brengen gebruikend HTTP API.

## Elementbinair bijwerken {#update-asset-binary}

Zie [ activa uploaden ](developer-reference-material-apis.md) voor informatie over hoe te om activa binaries bij te werken. U kunt een element binair niet bijwerken gebruikend HTTP API.

## Metagegevens van een element bijwerken {#update-asset-metadata}

Hiermee werkt u de metagegevenseigenschappen van het element bij. Als u een eigenschap in de naamruimte `dc:` bijwerkt, werkt de API dezelfde eigenschap in de naamruimte `jcr` bij. De API synchroniseert de eigenschappen niet onder de twee naamruimten.

**Verzoek**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'`

**de codes van de Reactie**: De antwoordcodes zijn:

* 200 - OK - als Asset met succes is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een elementuitvoering maken {#create-an-asset-rendition}

Een uitvoering voor een element maken. Als de naam van de parameter request niet wordt opgegeven, wordt de bestandsnaam gebruikt als naam voor de vertoning.

**Parameters**: De parameters zijn `name` voor naam van de vertoning en `file` als dossierverwijzing.

**Verzoek**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**de codes van de Reactie**

* 201 - GEMAAKT - als de vertoning is gemaakt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een elementuitvoering bijwerken {#update-an-asset-rendition}

Updates vervangen respectievelijk een elementuitvoering door de nieuwe binaire gegevens.

**Verzoek**: `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**de codes van de Reactie**: De antwoordcodes zijn:

* 200 - OK - als de vertoning correct is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een opmerking toevoegen aan een element {#create-an-asset-comment}

**Parameters**: De parameters zijn `message` voor het berichtlichaam van de commentaar en `annotationData` voor de gegevens van de Annotatie in formaat JSON.

**Verzoek**: `POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"`

**de codes van de Reactie**: De antwoordcodes zijn:

* 201 - GEMAAKT - als Opmerking is gemaakt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map of element kopiëren {#copy-a-folder-or-asset}

Hiermee kopieert u een map of element die beschikbaar is op het opgegeven pad naar een nieuwe bestemming.

**Kopballen van het Verzoek**: De parameters zijn:

* `X-Destination` - een nieuwe doel-URI binnen het bereik van de API-oplossing waarnaar de bron moet worden gekopieerd.
* `X-Depth` - ofwel `infinity` of `0` . Wanneer u `0` gebruikt, worden alleen de bron en de eigenschappen ervan gekopieerd en niet de onderliggende elementen.
* `X-Overwrite` - Gebruik `F` om te voorkomen dat een element op het bestaande doel wordt overschreven.

**Verzoek**: `COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"`

**de codes van de Reactie**: De antwoordcodes zijn:

* 201 - GEMAAKT - als de map/het element naar een niet-bestaand doel is gekopieerd.
* 204 - GEEN INHOUD - als de map of het middel naar een bestaande bestemming is gekopieerd.
* 412 - PRECONDITION MISLUKT - als een aanvraagkoptekst ontbreekt.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map of element verplaatsen {#move-a-folder-or-asset}

Hiermee verplaatst u een map of element op het opgegeven pad naar een nieuwe bestemming.

**Kopballen van het Verzoek**: De parameters zijn:

* `X-Destination` - een nieuwe doel-URI binnen het bereik van de API-oplossing waarnaar de bron moet worden gekopieerd.
* `X-Depth` - ofwel `infinity` of `0` . Wanneer u `0` gebruikt, worden alleen de bron en de eigenschappen ervan gekopieerd en niet de onderliggende elementen.
* `X-Overwrite` - Gebruik `T` om bestaande bronnen te verwijderen of `F` om te voorkomen dat een bestaande bron wordt overschreven.

**Verzoek**: `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

**de codes van de Reactie**: De antwoordcodes zijn:

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

**de codes van de Reactie**: De antwoordcodes zijn:

* 200 - OK - als de map is verwijderd.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Tips, aanbevolen procedures en beperkingen {#tips-limitations}

* Na [!UICONTROL Off Time] zijn een element en de bijbehorende uitvoeringen niet beschikbaar via de [!DNL Assets] -webinterface en via de HTTP-API. De API retourneert een foutbericht van 404 als de [!UICONTROL On Time] in de toekomst is of als [!UICONTROL Off Time] in het verleden is.

* Assets HTTP API retourneert de volledige metagegevens niet. De naamruimten zijn gecodeerd en alleen die naamruimten worden geretourneerd. Zie het elementpad `/jcr_content/metadata.json` voor volledige metagegevens.

* Sommige eigenschappen van map of element worden toegewezen aan een ander voorvoegsel wanneer ze worden bijgewerkt met behulp van API&#39;s. Het voorvoegsel `jcr` van `jcr:title` , `jcr:description` en `jcr:language` wordt vervangen door het voorvoegsel `dc` . Daarom bevatten `dc:title` en `dc:description` in de geretourneerde JSON de waarden van respectievelijk `jcr:title` en `jcr:description` .

**zie ook**

* [Assets vertalen](translate-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Publish Assets naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [ de verwijzingsdocumenten van de Ontwikkelaar voor  [!DNL Assets]](/help/assets/developer-reference-material-apis.md)
