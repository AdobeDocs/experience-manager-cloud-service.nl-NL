---
title: De Universal Editor Authoring-ervaring aanpassen
description: Leer over de verschillende uitbreidingspunten en andere eigenschappen die u toestaan om UI van de Universele Redacteur aan te passen om de behoeften van uw inhoudsauteurs te steunen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
source-git-commit: 11a244b7dd4810fbfec92b3effc362102e7322dc
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# De Universal Editor Authoring-ervaring aanpassen {#customizing-ue}

Leer over de verschillende uitbreidingspunten en andere eigenschappen die u toestaan om de auteurservaring van de Universele Redacteur aan te passen om de behoeften van uw inhoudsauteurs te steunen.

## Publiceren uitschakelen {#disable-publish}

Voor bepaalde ontwerpworkflows moet de inhoud worden gecontroleerd voordat deze wordt gepubliceerd. In dergelijke situaties mag de optie om te publiceren niet beschikbaar zijn voor auteurs.

De **Publiceren** Deze knop kan daarom volledig in een app worden onderdrukt door de volgende metagegevens toe te voegen.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```

## Componenten filteren {#filtering-components}

Wanneer u de Universal Editor gebruikt, kunt u de toegestane componenten per containercomponent beperken. Hiervoor moet u een extra scripttag invoeren, die naar de filterdefinitie verwijst.

```html
<script type="application/vnd.adobe.aue.filter+json" src="/static/filter-definition.json"></script>
```

Een filterdefinitie zou als het volgende kunnen kijken, die een container zou beperken om slechts het toevoegen van tekst en beelden toe te staan.

```json
[
  {
    "id": "container-filter",
     "components": ["text", "image"]
   }
]
```

Dan kunt u de filterdefinitie van uw containercomponent van verwijzingen voorzien door het bezit toe te voegen `data-aue-filter`, door de id van het filter door te geven dat u eerder hebt gedefinieerd.

```html
data-aue-filter="container-filter"
```

De instelling van `components` kenmerk in een filterdefinitie aan `null` Hiermee worden alle componenten toegestaan, alsof er geen filter is.

```json
[
  {
    "id": "another-container-filter",
     "components": null
   }
]
```

## Componenten voorwaardelijk tonen en verbergen in Eigenschapcontrole {#conditionally-hide}

Hoewel een component of componenten doorgaans beschikbaar zijn voor de auteurs, kunnen er bepaalde situaties zijn waarin dit geen nut heeft. In dergelijke gevallen kunt u componenten in de eigenschappen-rail verbergen door een `condition` aan de [velden van het componentmodel.](/help/implementing/universal-editor/field-types.md#fields)

Voorwaarden kunnen worden gedefinieerd met behulp van [JsonLogic-schema.](https://jsonlogic.com/) Als de voorwaarde waar is, wordt het veld weergegeven. Als de voorwaarde onwaar is, wordt het veld verborgen.

### Voorbeeldmodel {#sample-model}

```json
 {
    "id": "conditionally-revealed-component",
    "fields": [
      {
        "component": "boolean",
        "label": "Shall the text field be revealed?",
        "name": "reveal",
        "valueType": "boolean"
      },
      {
        "component": "text-input",
        "label": "Hidden text field",
        "name": "hidden-text",
        "valueType": "string",
        "condition": { "===": [{"var" : "reveal"}, true] }
      }
    ]
 }
```

#### Onjuiste voorwaarde {#false}

![Verborgen tekstveld](assets/hidden.png)

#### Voorwaarde waar {#true}

![Weergegeven tekstveld](assets/shown.png)

