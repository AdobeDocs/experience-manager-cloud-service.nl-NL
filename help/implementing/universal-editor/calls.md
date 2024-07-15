---
title: Universal Editor-aanroepen
description: Leer over de verschillende soorten vraag die door de Universele Redacteur aan uw app wordt gemaakt om u te helpen wanneer het zuiveren.
exl-id: 00d66e59-e445-4b5c-a5b1-c0a9f032ebd9
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---


# Universal Editor-aanroepen {#calls}

Leer over de verschillende soorten vraag die door de Universele Redacteur aan uw app wordt gemaakt om u te helpen wanneer het zuiveren.

## Overzicht {#overview}

De Universele Redacteur communiceert met uw van instrumenten voorzien app door een reeks bepaalde vraag. Dit is transparant voor en heeft geen invloed op de gebruikerservaring.

Voor de ontwikkelaar, echter, kan het begrip van deze vraag en wat zij doen waardevol zijn wanneer het zuiveren van uw toepassing wanneer het gebruiken van de Universele Redacteur. Als u van instrumenten uw app hebt voorzien en het zich niet zoals voorzien gedraagt, kan het nuttig zijn om het **lusje van het Netwerk** van de ontwikkelaarshulpmiddelen in uw browser te openen en de vraag te inspecteren aangezien u inhoud in uw app uitgeeft.

![ Voorbeeld van een detailvraag op het lusje van het Netwerk van de ontwikkelaarshulpmiddelen van browser ](assets/calls-network-tab.png)

* De **nuttige lading** van de vraag bevat details van wat door de redacteur met inbegrip van het identificeren van wat wordt bijgewerkt en hoe te om het bij te werken.
* De **Reactie** omvat details van wat precies door de redacteursdienst werd bijgewerkt. Hiermee kunt u het vernieuwen van de inhoud in de editor vereenvoudigen. In bepaalde gevallen, zoals bij een `move` -aanroep, moet de gehele pagina worden vernieuwd.

Zodra een vraag met succes wordt voltooid, worden de gebeurtenissen teweeggebracht die de lading van het verzoek en van de reactie omvatten, die voor uw eigen app kan worden aangepast. Gelieve te zien de de gebeurtenissen van de Universele Redacteur van het document [ ](/help/implementing/universal-editor/events.md) voor meer details.

Hieronder volgt een lijst met de typen aanroepen die de Universal Editor naar uw app uitvoert, samen met voorbeeldladingen en reacties.

## Bijwerken {#update}

Een `update` -aanroep doet zich voor wanneer u inhoud in uw app bewerkt met de Universal Editor. `update` houdt de wijzigingen aan.

De nuttige lading omvat details van wat om aan JCR terug te schrijven.

* `resource`: Het JCR-pad dat moet worden bijgewerkt
* `prop`: De JCR-eigenschap die wordt bijgewerkt
* `type`: Het JCR-waardetype van de eigenschap die wordt bijgewerkt
* `value`: De bijgewerkte gegevens

>[!BEGINTABS]

>[!TAB  Steekproef Payload ]

```json
{
  "connections": [
    {
      "name": "aem",
      "protocol": "aem",
      "uri": "https://localhost:8443"
    }
  ],
  "target": {
    "resource": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "type": "text",
    "prop": "jcr:title"
  },
  "value": "Tiny Toon Adventures"
}
```

>[!TAB  Reactie van de Steekproef ]

```json
{
  "updates": [
    {
      "resource": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
      "prop": "jcr:title",
      "type": "text"
    }
  ]
}
```

>[!ENDTABS]

## Details {#details}

Er verschijnt een `details` -aanroep wanneer u uw app in de Universal Editor laadt om de inhoud van de app op te halen.

Zijn nuttige lading omvat de gegevens die moeten worden teruggegeven evenals details van wat de gegevens (het schema) vertegenwoordigen zodat kunnen zij in de Universele Redacteur worden teruggegeven.

* Voor een component haalt de Universal Editor alleen een `data` -object op, aangezien het schema van de gegevens in de app is gedefinieerd.
* Voor inhoudsfragmenten haalt de Universal Editor ook een `schema` -object op, aangezien het Content Fragment Model is gedefinieerd in de JCR.

>[!BEGINTABS]

>[!TAB  Steekproef Payload ]

```json
{
  "connections": [
    {
      "name": "aem",
      "protocol": "aem",
      "uri": "https://localhost:8443"
    }
  ],
  "target": {
    "resource": "urn:aem:/content/wknd/language-masters/en/jcr:content/root/container/carousel/item_1571954853062",
    "type": "component",
    "prop": ""
  }
}
```

>[!TAB  Reactie van de Steekproef ]

```json
{
  "data": {
    "jcr:primaryType": "nt:unstructured",
    "jcr:title": "Tiny Toon Adventures",
    "fileReference": "/content/dam/wknd-shared/en/adventures/riverside-camping-australia/adobestock-216674449.jpeg",
    "cq:panelTitle": "WKND Adventures",
    "actionsEnabled": "true",
    "jcr:lastModifiedBy": "admin",
    "titleFromPage": "false",
    "jcr:description": "<p>With WKND Adventures, you don't just see the world you experinece it.</p>\r\n",
    "jcr:lastModified": "Fri Jan 19 2024 11:05:59 GMT+0100",
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

>[!ENDTABS]

## Toevoegen {#add}

Er treedt een `add` -aanroep op wanneer u een nieuwe component in uw app plaatst met de Universal Editor.

De lading ervan bevat een `path` -object dat de locatie bevat waar de inhoud moet worden toegevoegd.

Het omvat ook een `content` voorwerp met extra voorwerpen voor eindpunt-specifieke details van de inhoud die [ voor elke stop moet worden opgeslagen.](/help/implementing/universal-editor/architecture.md) Als uw app bijvoorbeeld is gebaseerd op inhoud van AEM en Magento, bevat de payload voor elk systeem een gegevensobject.

>[!BEGINTABS]

>[!TAB  Steekproef Payload ]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "target": {
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
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

>[!TAB  Reactie van de Steekproef ]

```json
{
  "updates": [
    {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container"
    }
  ],
  "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1138559521"
}
```

>[!ENDTABS]

## Verplaatsen {#move}

Een `move` -aanroep doet zich voor wanneer u een component binnen uw toepassing verplaatst met de Universal Editor.

De lading omvat een `from` voorwerp dat bepaalt waar de component was en een `to` voorwerp dat bepaalt waar het werd bewogen.

>[!BEGINTABS]

>[!TAB  Steekproef Payload ]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "from": {
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
    },
    "component": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_275525847",
      "type": "media",
      "prop": "fileReference"
    }
  },
  "to": {
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
    }
  }
}
```

>[!TAB  Reactie van de Steekproef ]

```json
{
  "updates": [
    {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container"
    }
  ]
}
```

>[!ENDTABS]

## Verwijderen {#remove}

Een `remove` -aanroep doet zich voor wanneer u een component in uw app verwijdert met de Universal Editor.

De lading ervan bevat het pad van het object dat is verwijderd.

>[!BEGINTABS]

>[!TAB  Steekproef Payload ]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "target": {
    "component": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_593170193",
      "type": "text",
      "prop": "text"
    },
    "container": {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "type": "container",
      "prop": ""
    }
  }
}
```

>[!TAB  Reactie van de Steekproef ]

```json
{
  "updates": [
    {
      "resource": "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container",
      "prop": "",
      "type": "container"
    }
  ]
}
```

>[!ENDTABS]

## Publish {#publish}

Een `publish` vraag komt voor wanneer u de **Publish** knoop in de Universele Redacteur klikt om de inhoud te publiceren die u hebt uitgegeven.

De Universal Editor herhaalt de inhoud en genereert een lijst met verwijzingen die ook moeten worden gepubliceerd.

>[!BEGINTABS]

>[!TAB  Steekproef Payload ]

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-pXXXX-eYYYYY.adobeaemcloud.com"
    }
  ],
  "references": [
    "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
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
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_229050934",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_2123678383",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1668104604",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/text_1138559521",
    "urn:aemconnection:/content/wknd/language-masters/en/universal-editor-container/jcr:content/root/container/image_275525847"
  ]
}
```

>[!TAB  Reactie van de Steekproef ]

```json
{
  "publishes": [
    "/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway",
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

>[!ENDTABS]

## Aanvullende bronnen {#additional-resources}

* [Universal Editor-gebeurtenissen](/help/implementing/universal-editor/events.md)

