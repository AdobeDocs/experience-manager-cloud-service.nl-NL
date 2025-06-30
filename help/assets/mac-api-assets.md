---
title: ASSETS HTTP API
description: Creeer, lees, update, schrap, beheer digitale activa gebruikend HTTP API in  [!DNL Experience Manager Assets].
contentOwner: AG
feature: Assets HTTP API
role: Developer, Architect, Admin
exl-id: a3b7374d-f24b-4d6f-b6db-b9c9c962bb8d
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '1685'
ht-degree: 0%

---

# Digitale middelen beheren met de [!DNL Adobe Experience Manager Assets] HTTP API{#assets-http-api}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/extending/mac-api-assets.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

## Aan de slag met de AEM [!DNL Assets] HTTP API {#overview}

Met de AEM [!DNL Assets] HTTP API zijn CRUD-bewerkingen (maken, lezen, bijwerken en verwijderen) op digitale elementen mogelijk via een REST-interface die beschikbaar is op /`api/assets` . Deze bewerkingen zijn van toepassing op metagegevens van elementen, uitvoeringen en opmerkingen. Het omvat [ steun voor de Fragmenten van de Inhoud ](/help/assets/content-fragments/assets-api-content-fragments.md).

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

## Inhoudsfragmenten beheren {#content-fragments}

A [ het Fragment van de Inhoud ](/help/assets/content-fragments/content-fragments.md) is een gestructureerd middel dat tekst, aantallen, en data opslaat. Aangezien er verschillende verschillen zijn tussen `standard` -elementen (zoals afbeeldingen of documenten), zijn er enkele aanvullende regels van toepassing op de afhandeling van inhoudsfragmenten.

Voor meer informatie, zie [ de steun van de Fragmenten van de Inhoud in  [!DNL Experience Manager Assets]  HTTP API ](/help/assets/content-fragments/assets-api-content-fragments.md).

>[!NOTE]
>
>Zie [ AEM APIs voor Gestructureerde Inhoudslevering en Beheer ](/help/headless/apis-headless-and-content-fragments.md) voor een overzicht van diverse beschikbare APIs en vergelijking van sommige betrokken concepten.
>
>Het [ Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

## Onderzoek het gegevensmodel {#data-model}

De [!DNL Assets] HTTP API stelt hoofdzakelijk twee elementen bloot: omslagen en standaardactiva. Het biedt ook gedetailleerde elementen voor aangepaste gegevensmodellen die in Inhoudsfragmenten worden gebruikt. Zie Gegevensmodellen van inhoudsfragmenten voor meer informatie. Zie {de gegevensmodellen van het Fragment van 0} Inhoud ](/help/assets/content-fragments/assets-api-content-fragments.md#content-models-and-content-fragments) voor verdere informatie.[

>[!NOTE]
>
>Het [ Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

### Mappen beheren {#folders}

Mappen zijn vergelijkbaar met mappen zoals in traditionele bestandssystemen. Mappen kunnen elementen, submappen of beide bevatten. Mappen hebben de volgende componenten:

**Entiteiten**: De entiteiten van een omslag zijn zijn kindelementen, die omslagen en activa kunnen zijn.

**Eigenschappen**:

* `name`: De naam van de map (het laatste segment van het URL-pad, zonder de extensie).
* `title`: Een optionele titel die wordt weergegeven in plaats van de mapnaam.

>[!NOTE]
>
>Sommige eigenschappen van map of element worden toegewezen aan een ander voorvoegsel. Het voorvoegsel `jcr` van `jcr:title` , `jcr:description` en `jcr:language` wordt vervangen door het voorvoegsel `dc` . Daarom bevatten `dc:title` en `dc:description` in de geretourneerde JSON de waarden van respectievelijk `jcr:title` en `jcr:description` .

**de Omslagen van Verbindingen** stellen drie verbindingen bloot:

* `self`: Een koppeling naar de map zelf.
* `parent`: een koppeling naar de bovenliggende map.
* `thumbnail` (Optioneel): een koppeling naar een miniatuurafbeelding van een map.

### Elementen beheren {#assets}

In [!DNL Experience Manager] bevat een element de volgende elementen:

* **Eigenschappen en meta-gegevens:** Beschrijvende informatie over de activa.
* **Binair dossier:** het oorspronkelijk geüploade dossier.
* **Vertoningen:** Veelgevormde vertoningen (zoals, beelden in diverse grootte, verschillende videocoderingen, of gehaalde pagina&#39;s van Pdfs/Adobe InDesign dossiers).
* **Commentaren (facultatief):** user-provided commentaren.

Voor informatie over elementen in de Fragmenten van de Inhoud zie [ de Steun van de Fragmenten van de Inhoud in HTTP van Experience Manager Assets API ](/help/assets/content-fragments/assets-api-content-fragments.md).

>[!NOTE]
>
>Het [ Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

In [!DNL Experience Manager] heeft een map de volgende componenten:

* Entiteiten: De onderliggende elementen van activa zijn de uitvoeringen.
* Eigenschappen.
* Koppelingen.

## Beschikbare API-bewerkingen verkennen {#available-features}

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
* Een set naam-waardeparen, gecodeerd als `application/www-form-urlencoded` of `multipart`/ `form` - `data` . Deze zijn handig als u een map rechtstreeks vanuit een HTML-formulier wilt maken.

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

Het maken van elementen wordt niet ondersteund via deze HTTP-API. Voor activa verwezenlijking, gebruik [ activa uploadt ](developer-reference-material-apis.md) API.

## Elementbinair bijwerken {#update-asset-binary}

Zie [ activa uploaden ](developer-reference-material-apis.md) voor informatie over hoe te om activa binaries bij te werken. U kunt een element binair niet bijwerken gebruikend HTTP API.

## Metagegevens van een element bijwerken {#update-asset-metadata}

Met deze bewerking worden de metagegevens van het element bijgewerkt. Wanneer u eigenschappen in de naamruimte `dc:` bijwerkt, wordt de bijbehorende eigenschap `jcr:` bijgewerkt. De API synchroniseert de eigenschappen echter niet onder de twee naamruimten.

**Verzoek**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'`

**de codes van de Reactie**: De antwoordcodes zijn:

* 200 - OK - als Asset met succes is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een elementuitvoering maken {#create-an-asset-rendition}

Een uitvoering voor een element maken. Als de naam van de parameter request niet wordt opgegeven, wordt de bestandsnaam gebruikt als naam voor de vertoning.

**Parameters**: De parameters zijn:

`name` : voor de renditienaam.
`file`: Het binaire bestand voor de vertoning als een verwijzing.

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

## Volg de aanbevolen werkwijzen en beperkingen van notities {#tips-limitations}

* Assets en de bijbehorende uitvoeringen zijn niet meer beschikbaar via de [!DNL Assets] -webinterface en de HTTP-API wanneer [!UICONTROL Off Time] wordt bereikt. De API retourneert een fout van 404 als de [!UICONTROL On Time] in de toekomst is of als [!UICONTROL Off Time] in het verleden is.

* De Assets HTTP-API retourneert alleen een subset met metagegevens. De naamruimten zijn gecodeerd en alleen die naamruimten worden geretourneerd. Zie het elementpad `/jcr_content/metadata.json` voor volledige metagegevens.

* Sommige eigenschappen van map of element worden toegewezen aan een ander voorvoegsel wanneer ze worden bijgewerkt met behulp van API&#39;s. Het voorvoegsel `jcr` van `jcr:title` , `jcr:description` en `jcr:language` wordt vervangen door het voorvoegsel `dc` . Daarom bevatten `dc:title` en `dc:description` in de geretourneerde JSON de waarden van respectievelijk `jcr:title` en `jcr:description` .

**Onderzoek verwante middelen**

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
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [ de verwijzingsdocumenten van de Ontwikkelaar voor  [!DNL Assets]](/help/assets/developer-reference-material-apis.md)
