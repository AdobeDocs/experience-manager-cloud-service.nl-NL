---
title: HTTP-API voor assets
description: Leer over de implementatie, het gegevensmodel, en de eigenschappen van Activa HTTP API. Met de HTTP-API Middelen kunt u verschillende taken uitvoeren met betrekking tot elementen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 068195919c4bf73c41b1156eadb47544e4c41e65

---


# HTTP-API voor assets {#assets-http-api}

## Overzicht {#overview}

Met de HTTP-API voor Middelen kunt u CRUD-bewerkingen (read-read-update-delete) maken voor Elementen, zoals binaire elementen, metagegevens, uitvoeringen en opmerkingen, en voor gestructureerde inhoud met behulp van AEM Content Fragments. Deze wordt weergegeven op `/api/assets` en geïmplementeerd als REST API. Dit omvat [ondersteuning voor inhoudsfragmenten](content-fragments/content-fragments.md).

Toegang krijgen tot de API:

1. Open het API-servicedocument op `https://[hostname]:[port]/api.json`.
1. Volg de koppelingen van de service Middelen die naar `https://[hostname]:[server]/api/assets.json`leiden.

De API-reactie is een JSON-bestand voor sommige MIME-typen en een antwoordcode voor alle MIME-typen. Het JSON-antwoord is optioneel en is mogelijk niet beschikbaar, bijvoorbeeld voor PDF-bestanden. Vertrouw op de antwoordcode voor verdere analyse of acties.

Na de [!UICONTROL Off Time]zijn een middel en zijn vertoningen niet beschikbaar of via de Webinterface van Middelen of door HTTP API. De API retourneert een foutbericht van 404 als de [!UICONTROL Aan-tijd] in de toekomst is of de [!UICONTROL Uit-tijd] in het verleden is.

>[!NOTE]
>
>Alle API-aanroepen die betrekking hebben op het uploaden of bijwerken van middelen of binaire bestanden in het algemeen (zoals uitvoeringen), worden voor AEM gedepreteerd als implementatie van een cloudservice. Gebruik in plaats hiervan [directe binaire upload-API&#39;s](developer-reference-material-apis.md#asset-upload-technical) voor het uploaden van binaire bestanden.

## Contentfragmenten {#content-fragments}

Een [inhoudsfragment](content-fragments/content-fragments.md) is een speciaal type element. Het kan worden gebruikt om tot gestructureerde gegevens, zoals teksten, aantallen, data toegang te hebben. Aangezien er verschillende verschillen zijn tussen `standard` elementen (zoals afbeeldingen of documenten), zijn enkele aanvullende regels van toepassing op de afhandeling van inhoudsfragmenten.

Zie Ondersteuning van [inhoudsfragmenten in de HTTP-API](content-fragments/content-fragments.md)van AEM Assets voor meer informatie.

## Gegevensmodel {#data-model}

De HTTP-API voor middelen stelt twee belangrijke elementen, mappen en elementen beschikbaar (voor standaardelementen).

Bovendien, stelt het meer gedetailleerde elementen voor de modellen van douanegegevens bloot die gestructureerde inhoud in de Fragments van de Inhoud beschrijven. Zie Gegevensmodellen [van](content-fragments/content-fragments.md) inhoudsfragmenten voor meer informatie.

### Mappen {#folders}

Mappen zijn vergelijkbaar met mappen in traditionele bestandssystemen. Het zijn containers voor andere mappen of berichten. Mappen hebben de volgende componenten:

**Entiteiten**: De entiteiten van een map zijn onderliggende elementen, mappen en elementen.

**Eigenschappen**:
* `name`  — Naam van de map. Dit is hetzelfde als het laatste segment in het URL-pad zonder de extensie
* `title` — Optionele titel van de map die kan worden weergegeven in plaats van de naam ervan

>[!NOTE]
>
>Sommige eigenschappen van map of element worden toegewezen aan een ander voorvoegsel. Het `jcr` voorvoegsel van `jcr:title`, `jcr:description`en `jcr:language` worden vervangen door het `dc` voorvoegsel. Daarom in de geretourneerde JSON `dc:title` en `dc:description` bevatten deze de waarden van respectievelijk `jcr:title` en `jcr:description`.

**Er zijn drie koppelingen beschikbaar in Koppelingsmappen** :
* `self`: Koppeling naar zichzelf
* `parent`: Koppeling maken naar de bovenliggende map
* `thumbnail`: (Optioneel) koppeling naar een miniatuurafbeelding van een map

### Assets {#assets}

In AEM bevat een element de volgende elementen:

* De eigenschappen en metagegevens van het element
* Meerdere uitvoeringen, zoals de oorspronkelijke uitvoering (het oorspronkelijk geüploade element), een miniatuur en verschillende andere uitvoeringen. Extra uitvoeringen kunnen afbeeldingen van verschillende grootten, videocoderingen of uit PDF of InDesign geëxtraheerde pagina&#39;s zijn.
* Optionele opmerkingen

Zie Ondersteuning van [inhoudsfragmenten in HTTP-API](content-fragments/content-fragments.md)van AEM-elementen voor informatie over elementen in inhoudsfragmenten.

In AEM heeft een map de volgende componenten:

* Entiteiten: De onderliggende elementen van Elementen zijn de uitvoeringen.
* Eigenschappen
* Koppelingen

De HTTP-API voor middelen biedt de volgende functies:

* Een mappenlijst ophalen
* Een map maken
* Een element maken (afgekeurd)
* Binair element bijwerken (afgekeurd)
* Metagegevens van elementen bijwerken
* Een elementuitvoering maken
* Een elementuitvoering bijwerken
* Een middelenopmerking maken
* Een map of element kopiëren
* Een map of element verplaatsen
* Een map, element of uitvoering verwijderen

>[!NOTE]
>
>Om de leesbaarheid te verbeteren, worden in de volgende voorbeelden de volledige cURL-notatie weggelaten. De notatie heeft in feite een correlatie met [Resty](https://github.com/micha/resty) , een scriptwrapper voor cURL.

<!-- TBD: The Console Manager is not available now. So how to configure the below? 

**Prerequisites**

* Go to `https://[aem_server]:[port]/system/console/configMgr`.
* Navigate to **Adobe Granite CSRF Filter**.
* Make sure the property **Filter Methods** includes: POST, PUT, DELETE.
-->

## Een mappenlijst ophalen {#retrieve-a-folder-listing}

Haalt een Siren-weergave op van een bestaande map en van de onderliggende entiteiten (submappen of elementen).

**Verzoek**

```
GET /api/assets/myFolder.json
```

**Antwoordcodes**

```
200 - OK - success
404 - NOT FOUND - folder does not exist or is not accessible
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

**Antwoord**

De klasse van de geretourneerde entiteit is assets/folder.

Eigenschappen van ingesloten entiteiten zijn een subset van de volledige reeks eigenschappen van elke entiteit. Om een volledige vertegenwoordiging van de entiteit te verkrijgen, zouden de cliënten de inhoud van URL moeten terugwinnen waarnaar door de verbinding met een `rel` van `self`. wordt verwezen.

## Een map maken {#create-a-folder}

Hiermee maakt u een nieuwe `sling`: op `OrderedFolder` het opgegeven pad. Als * in plaats van een knoopnaam wordt gegeven zal servlet de parameternaam als knooppuntnaam gebruiken. Gegevens die worden geaccepteerd als aanvraaggegevens zijn een Sirene-weergave van de nieuwe map of een set naam-waardeparen, gecodeerd als `application/www-form-urlencoded` of `multipart`/ `form`- `data`, handig om een map te maken die rechtstreeks afkomstig is van een HTML-formulier. Bovendien kunnen eigenschappen van de map worden opgegeven als URL-queryparameters.

De bewerking zal mislukken met een `500` antwoordcode als het bovenliggende knooppunt van het opgegeven pad niet bestaat. Als de map al bestaat, wordt een `409` antwoordcode geretourneerd.

**Parameters**

* `name` - Mapnaam

**Verzoek**

```
POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'
```

or

```
POST /api/assets/* -F"name=myfolder" -F"title=My Folder"
```

**Antwoordcodes**

```
201 - CREATED - on successful creation
409 - CONFLICT - if folder already exist
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Een element maken {#create-an-asset}

Zie [elementen uploaden](developer-reference-material-apis.md) voor informatie over het maken van elementen met behulp van API&#39;s. Middelen maken met de HTTP API is afgekeurd.

## Elementbinair bijwerken {#update-asset-binary}

Zie [elementen uploaden](developer-reference-material-apis.md) voor informatie over het bijwerken van middelenbinaire bestanden met behulp van API&#39;s. Het bijwerken van een element binair met behulp van de HTTP API is afgekeurd.

## Metagegevens van een element bijwerken {#update-asset-metadata}

Werkt de metagegevenseigenschappen van het element bij.

**Verzoek**

```
PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'
```

**Antwoordcodes**

```
200 - OK - if Asset has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Een elementuitvoering maken {#create-an-asset-rendition}

Hiermee maakt u een nieuwe uitvoering van elementen voor een element. Als er geen naam voor de parameter request is opgegeven, wordt de bestandsnaam gebruikt als naam voor de vertoning.

**Parameters**

* `name` - Naam van vertoning
* `file` - Bestandsverwijzing

**Verzoek**

```
POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"
```

or

```
POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"
```

**Antwoordcodes**

```
201 - CREATED - if Rendition has been created successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Een elementuitvoering bijwerken {#update-an-asset-rendition}

Updates vervangen een elementuitvoering door de nieuwe binaire gegevens.

**Verzoek**

```
PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png
```

**Antwoordcodes**

```
200 - OK - if Rendition has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Een middelenopmerking maken {#create-an-asset-comment}

Hiermee maakt u een nieuwe middelenopmerking.

**Parameters**

* `message` - Bericht
* `annotationData` - Annotatiegegevens (JSON)

**Verzoek**

```
POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"
```

**Antwoordcodes**

```
201 - CREATED - if Comment has been created successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Een map of element kopiëren {#copy-a-folder-or-asset}

Kopieert een map of element op het opgegeven pad naar een nieuwe bestemming.

**Aanvraagkoppen**

```
X-Destination - a new destination URI within the API solution scope to copy the resource to
X-Depth - either 'infinity' or '0'. The value '0' only copies the resource and its properties, no children.
X-Overwrite - 'F' to prevent overwriting an existing destination
```

**Verzoek**

```
COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"
```

**Antwoordcodes**

```
201 - CREATED - if folder/asset has been copied to a non-existing destination
204 - NO CONTENT - if the folder/asset has been copied to an existing destination
412 - PRECONDITION FAILED - if a request header is missing or
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Een map of element verplaatsen {#move-a-folder-or-asset}

Hiermee verplaatst u een map of element op het opgegeven pad naar een nieuwe bestemming.

**Aanvraagkoppen**

```
X-Destination - a new destination URI within the API solution scope to copy the resource to
X-Depth - either 'infinity' or '0'. The value '0' only copies the resource and its properties, no children.
X-Overwrite - either 'T' to force deletion of existing resources or 'F' to prevent overwriting an existing resource.
```

**Verzoek**

```
MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"
```

**Antwoordcodes**

```
201 - CREATED - if folder/asset has been copied to a non-existing destination
204 - NO CONTENT - if the folder/asset has been copied to an existing destination
412 - PRECONDITION FAILED - if a request header is missing or
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Een map, element of uitvoering verwijderen {#delete-a-folder-asset-or-rendition}

Hiermee verwijdert u een resource (-tree) bij het opgegeven pad.

**Verzoek**

```
DELETE /api/assets/myFolder
```

or

```
DELETE /api/assets/myFolder/myAsset.png
```

or

```xml
DELETE /api/assets/myFolder/myAsset.png/renditions/original
```

**Antwoordcodes**

```
200 - OK - if folder has been deleted successfully
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

