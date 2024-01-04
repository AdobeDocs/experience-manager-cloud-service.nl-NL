---
title: Universal Editor-aanroepen
description: Leer over de verschillende soorten vraag die door de Universele Redacteur aan uw app wordt gemaakt om u te helpen wanneer het zuiveren.
source-git-commit: 16f2922a3745f9eb72f7070c30134e5149eb78ce
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---


# Universal Editor-aanroepen {#calls}

Leer over de verschillende soorten vraag die door de Universele Redacteur aan uw app wordt gemaakt om u te helpen wanneer het zuiveren.

{{universal-editor-status}}

## Overzicht {#overview}

De Universele Redacteur communiceert met uw van instrumenten voorzien app door een reeks bepaalde vraag. Dit is transparant voor en heeft geen invloed op de gebruikerservaring.

Voor de ontwikkelaar, echter, kan het begrip van deze vraag en wat zij doen waardevol zijn wanneer het zuiveren van uw toepassing wanneer het gebruiken van de Universele Redacteur. Als u van instrumenten van uw app hebt voorzien en het gedrag van de app niet correct is, kan het handig zijn om het dialoogvenster **Netwerk** van de ontwikkelaarsgereedschappen in uw browser en inspecteer de aanroepen terwijl u inhoud in uw app bewerkt.

![Voorbeeld van een detailsvraag op het lusje van het Netwerk van de ontwikkelaarshulpmiddelen van browser](assets/calls-network-tab.png)

* De **Payload** van de vraag bevat details van wat door de redacteur met inbegrip van het identificeren wordt bijgewerkt wat en hoe te om het bij te werken.
* De **Antwoord** bevat details over wat precies door de redactedienst is bijgewerkt. Hiermee kunt u het vernieuwen van de inhoud in de editor vereenvoudigen. In bepaalde gevallen, zoals `move` vraag, moet de volledige pagina worden verfrist.

Hieronder volgt een lijst met de typen aanroepen die de Universal Editor naar uw app uitvoert, samen met voorbeeldladingen en reacties.

## Bijwerken {#update}

An `update` Er wordt aangeroepen wanneer u inhoud in uw app bewerkt met de Universal Editor. De `update` houdt de veranderingen voort.

De nuttige lading omvat details van wat om aan JCR terug te schrijven.

* `itemid`: Het JCR-pad dat moet worden bijgewerkt
* `itemprop`: De JCR-eigenschap die wordt bijgewerkt
* `itemtype`: Het JCR-waardetype van de eigenschap die wordt bijgewerkt
* `value`: De bijgewerkte gegevens

### Voorbeeld van nuttige lading {#update-payload}

```json
{
  "op": "patch",
  "connections": {
    "aem": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "itemid": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "itemtype": "text",
    "itemprop": "jcr:title"
  },
  "value": "Tiny Toon Adventures"
}
```

### Samplereactie {#update-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
      "itemprop": "jcr:title",
      "itemtype": "text"
    }
  ]
}
```

## Details {#details}

A `details` Er wordt aangeroepen wanneer u uw app in de Universal Editor laadt om de inhoud van de app op te halen.

Zijn nuttige lading omvat de gegevens die moeten worden teruggegeven evenals details van wat de gegevens (het schema) vertegenwoordigen zodat kunnen zij in de Universele Redacteur worden teruggegeven.

* Voor een component haalt de Universal Editor alleen een `data` -object, aangezien het schema van de gegevens in de app is gedefinieerd.
* Voor Inhoudsfragmenten haalt de Universal Editor ook een `schema` -object omdat het inhoudsfragmentmodel is gedefinieerd in de JCR.

### Voorbeeld van nuttige lading {#details-payload}

```json
{
  "op": "patch",
  "connections": {
    "aem": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "itemid": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "itemtype": "component",
    "itemprop": ""
  }
}
```

### Samplereactie {#details-response}

```json
{
  "data": {
    "jcr:primaryType": "nt:unstructured",
    "jcr:title": "Tiny Toon Adventures!",
    "fileReference": "/content/dam/wknd-shared/en/adventures/riverside-camping-australia/adobestock-216674449.jpeg",
    "cq:panelTitle": "WKND Adventures",
    "actionsEnabled": "true",
    "jcr:lastModifiedBy": "admin",
    "titleFromPage": "false",
    "jcr:description": "<p>With WKND Adventures, you don't just see the world you experinece it.</p>",
    "jcr:lastModified": "Wed Jan 03 2024 09:06:05 GMT+0100",
    "descriptionFromPage": "true",
    "sling:resourceType": "wknd/components/teaser",
    "textIsRich": "true",
    "cq:styleIds": [
      "1555543212672"
    ],
    "actions": {
      "jcr:primaryType": "nt:unstructured",
      "item0": {
        "jcr:primaryType": "nt:unstructured",
        "link": "/content/wknd/language-masters/en/adventures",
        "text": "View Trips"
      }
    }
  }
}
```

## Toevoegen {#add}

An `add` Er wordt aangeroepen wanneer u een nieuwe component in uw app plaatst met de Universal Editor.

De lading omvat een `path` -object dat de locatie bevat waar de inhoud moet worden toegevoegd.

Het omvat tevens een `content` object met aanvullende objecten voor eindpuntspecifieke details van de inhoud die moet worden opgeslagen [voor elke insteekmodule.](/help/implementing/universal-editor/architecture.md) Als uw app bijvoorbeeld is gebaseerd op inhoud van AEM en Magento, bevat de payload voor elk systeem een gegevensobject.

### Voorbeeld van nuttige lading {#add-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "container": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container",
      "itemprop": ""
    }
  },
  "content": {
    "name": "text",
    "aem": {
      "page": {
        "resourceType": "wknd/components/text",
        "template": {
          "text": "Default Text"
        }
      }
    }
  }
}
```

### Samplereactie {#add-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container"
    }
  ]
}
```

## Verplaatsen {#move}

A `move` Er wordt aangeroepen wanneer u een component in uw app verplaatst met de Universal Editor.

De lading omvat een `from` object dat bepaalt waar de component zich bevond en een `to` object dat definieert waar het is verplaatst.

### Voorbeeld van nuttige lading {#move-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "from": {
    "container": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container",
      "itemprop": ""
    },
    "component": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1068508321",
      "itemtype": "text",
      "itemprop": "text"
    }
  },
  "to": {
    "container": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container",
      "itemprop": ""
    },
    "before": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_2063168902",
      "itemtype": "text",
      "itemprop": "text"
    }
  }
}
```

### Samplereactie {#move-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container"
    }
  ]
}
```

## Verwijderen {#remove}

A `remove` Er treedt een aanroep op wanneer u een component in uw app verwijdert met de Universal Editor.

De lading ervan bevat het pad van het object dat is verwijderd.

### Voorbeeld van nuttige lading {#remove-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "component": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1068508321",
      "itemtype": "text",
      "itemprop": "text"
    },
    "container": {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemtype": "container",
      "itemprop": ""
    }
  }
}
```

### Samplereactie {#remove-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "itemprop": "",
      "itemtype": "container"
    }
  ]
}
```

## Reparatie {#patch}

A `patch` wordt aangeroepen wanneer u inhoud in een dialoogvenster binnen uw app bijwerkt. Hierdoor wordt de inhoud op de pagina van de app als een JSON-patch bijgewerkt naar de bestaande inhoud.

De lading omvat het pad van de inhoud op de pagina en de JSON-patch van de aan te brengen wijziging.

### Voorbeeld van nuttige lading {#patch-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "path": {
    "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1540979193",
    "itemtype": "text",
    "itemprop": "text"
  },
  "patch": [
    {
      "op": "replace",
      "path": "/text",
      "value": "Still More WKND Adventures"
    }
  ]
}
```

### Samplereactie {#patch-response}

```json
{
  "updates": [
    {
      "itemid": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1540979193"
    }
  ]
}
```

## Publiceren {#publish}

A `publish` de vraag komt voor wanneer u klikt **Publiceren** in de Universal Editor om de inhoud te publiceren die u hebt bewerkt.

De Universal Editor herhaalt de inhoud en genereert een lijst met verwijzingen die ook moeten worden gepubliceerd.

### Voorbeeld van nuttige lading {#publish-payload}

```json
{
  "op": "patch",
  "connections": {
    "aemconnection": "aem:https://author-pXXXX-eYYYYY.adobeaemcloud.com"
  },
  "references": [
    "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
    "urn:aemconnection:/content/wknd/us/en/adventures/jcr:content/root/container/container/title",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/bali-surf-camp/bali-surf-camp/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/climbing-new-zealand/climbing-new-zealand/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/cycling-southern-utah/cycling-southern-utah/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/cycling-tuscany/cycling-tuscany/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/downhill-skiing-wyoming/downhill-skiing-wyoming/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/napa-wine-tasting/napa-wine-tasting/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/riverside-camping-australia/riverside-camping-australia/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/ski-touring-mont-blanc/ski-touring-mont-blanc/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/surf-camp-in-costa-rica/surf-camp-costa-rica/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/tahoe-skiing/tahoe-skiing/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/west-coast-cycling/west-coast-cycling/jcr:content/data/master",
    "urn:aemconnection:/content/dam/wknd-shared/en/adventures/yosemite-backpacking/yosemite-backpacking/jcr:content/data/master",
    "urn:aemconnection:/content/wknd/us/en/newsletter/jcr:content/root/container/title",
    "urn:aemconnection:/content/wknd/us/en/newsletter/jcr:content/root/container/text",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/title",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_2123678383",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1668104604",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_229050934",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_275525847",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_358189229",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_2063168902",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1540979193"
  ]
}
```

### Samplereactie {#publish-response}

```json
{
  "publishes": [
    "/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway",
    "/content/wknd/us/en/adventures",
    "/content/dam/wknd-shared/en/adventures/bali-surf-camp/bali-surf-camp",
    "/content/dam/wknd-shared/en/adventures/climbing-new-zealand/climbing-new-zealand",
    "/content/dam/wknd-shared/en/adventures/cycling-southern-utah/cycling-southern-utah",
    "/content/dam/wknd-shared/en/adventures/cycling-tuscany/cycling-tuscany",
    "/content/dam/wknd-shared/en/adventures/downhill-skiing-wyoming/downhill-skiing-wyoming",
    "/content/dam/wknd-shared/en/adventures/napa-wine-tasting/napa-wine-tasting",
    "/content/dam/wknd-shared/en/adventures/riverside-camping-australia/riverside-camping-australia",
    "/content/dam/wknd-shared/en/adventures/ski-touring-mont-blanc/ski-touring-mont-blanc",
    "/content/dam/wknd-shared/en/adventures/surf-camp-in-costa-rica/surf-camp-costa-rica",
    "/content/dam/wknd-shared/en/adventures/tahoe-skiing/tahoe-skiing",
    "/content/dam/wknd-shared/en/adventures/west-coast-cycling/west-coast-cycling",
    "/content/dam/wknd-shared/en/adventures/yosemite-backpacking/yosemite-backpacking",
    "/content/wknd/us/en/newsletter",
    "/content/wknd/language-masters/en/universal-editor-container"
  ]
}
```
