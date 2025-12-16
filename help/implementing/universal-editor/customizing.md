---
title: De universele editor aanpassen
description: Leer over de verschillende opties om de Universele Redacteur aan te passen om de behoeften van uw inhoudsauteurs te steunen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
feature: Developing
role: Admin, Developer
source-git-commit: b7b89587a81d0cadc81d4b2a486c022557c4a9fb
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---


# De universele editor aanpassen {#customizing}

Leer over de verschillende opties om de Universele Redacteur aan te passen om de behoeften van uw inhoudsauteurs te steunen.

>[!TIP]
>
>De Universele Redacteur biedt ook vele [ uitbreidingspunten aan, ](/help/implementing/universal-editor/extending.md) toestaand u om zijn functionaliteit uit te breiden om aan uw projectbehoeften te voldoen.

## Meta Config-tags gebruiken {#meta-tags}

Voor bepaalde ontwerpworkflows moet u wellicht bepaalde functies van de universele editor gebruiken, niet andere. Om dergelijke diverse gevallen te steunen, zijn de metatags beschikbaar om bepaalde eigenschappen of knopen van de redacteur te vormen of onbruikbaar te maken.

Gebruik dit label in de sectie `<head>` van de pagina om een of meer functies uit te schakelen:

```html
<meta name="urn:adobe:aue:config:disable" content="..." />
```

Als u meerdere functies wilt uitschakelen, voert u een lijst met waarden in die door komma&#39;s wordt gescheiden.

Hieronder vindt u de ondersteunde waarden voor `content` , dat wil zeggen de functies die met metatags kunnen worden uitgeschakeld.

| Inhoudswaarde | Beschrijving |
|---|---|
| `publish` | Maak al [ het publiceren ](/help/sites-cloud/authoring/universal-editor/publishing.md) functionaliteit onbruikbaar, d.w.z. [ publiceer knoop ](/help/sites-cloud/authoring/universal-editor/navigation.md#publish) en [ unpublish knoop ](/help/sites-cloud/authoring/universal-editor/navigation.md#ellipsis) |
| `publish-live` | Maak live [ het publiceren ](/help/sites-cloud/authoring/universal-editor/publishing.md) onbruikbaar |
| `publish-preview` | Maak voorproef het publiceren onbruikbaar (als de [ voorproefdienst ](/help/sites-cloud/authoring/sites-console/previewing-content.md) beschikbaar is) |
| `unpublish` | Maak [ unpublish knoop ](/help/sites-cloud/authoring/universal-editor/publishing.md#unpublishing-content) onbruikbaar |
| `copy` | Maakt [ exemplaar en deegknopen ](/help/sites-cloud/authoring/universal-editor/authoring.md#copy-paste) onbruikbaar |
| `duplicate` | Schakelt [ dubbele knoop ](/help/sites-cloud/authoring/universal-editor/navigation.md#duplicate) onbruikbaar |
| `header-open-page` | Maakt [ open paginaknoop ](/help/sites-cloud/authoring/universal-editor/navigation.md#open-page) onbruikbaar |
| `aem-dev-login` | Maakt de [ ontwikkelaarslogin knoop ](/help/sites-cloud/authoring/universal-editor/navigation.md#local-developer-login) onbruikbaar |

## Het veranderen van Uw Eindpunt {#custom-endpoint}

Als u de Universal Editor-service, die door Adobe wordt gehost, maar uw eigen gehoste versie niet wilt gebruiken, kunt u dit instellen in een metatag. Gelieve te zien het document [ Begonnen het worden met de Universele Redacteur in AEM ](/help/implementing/universal-editor/getting-started.md##configuration-settings) voor details.

## Componenten filteren {#filtering-components}

U kunt de toegestane componenten per container in de Universele Redacteur beperken gebruikend componentenfilters. Gelieve te zien het document [ Filtrerend Componenten ](/help/implementing/universal-editor/filtering.md) voor meer informatie.

## Componenten voorwaardelijk tonen en verbergen in deelvenster Eigenschappen {#conditionally-hide}

Hoewel een component of componenten doorgaans beschikbaar zijn voor de auteurs, kunnen er bepaalde situaties zijn waarin dit geen nut heeft. In dergelijke gevallen, kunt u componenten in het eigenschappen paneel verbergen door a `condition` attributen aan de [ gebieden van het componentenmodel ](/help/implementing/universal-editor/field-types.md#fields) toe te voegen.

De voorwaarden kunnen worden bepaald gebruikend [ schema JsonLogic ](https://jsonlogic.com/). Als de voorwaarde waar is, wordt het veld weergegeven. Als de voorwaarde onwaar is, wordt het veld verborgen.

>[!BEGINTABS]

>[!TAB  Model van de Steekproef ]

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

>[!TAB  Onwaar van de Voorwaarde ]

![ Verborgen tekstgebied ](assets/hidden.png)

>[!TAB  de Toestand van 0} Waar {]

![ Getoonde tekstgebied ](assets/shown.png)

>[!ENDTABS]

## Aangepaste voorbeeld-URL&#39;s {#custom-preview-urls}

U kunt een douanevoorproef URL via a `urn:adobe:aue:config:preview` metaconfiguratie specificeren, die wanneer het klikken van de **Open pagina** knoop in de [ top-right toolbar van de redacteur ](/help/sites-cloud/authoring/universal-editor/navigation.md#universal-editor-toolbar) zal openen.

Hiervoor neemt u gewoon de gewenste voorvertoning-URL op in een metatag van de van instrumenten voorziene app, zoals in het volgende voorbeeld.

```html
<meta name="urn:adobe:aue:config:preview" content="https://wknd.site"/>
```
