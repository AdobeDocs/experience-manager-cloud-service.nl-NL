---
title: De universele editor aanpassen en uitbreiden
description: Leer over de verschillende uitbreidingspunten en andere eigenschappen die u toestaan om UI van de Universele Redacteur aan te passen om de behoeften van uw inhoudsauteurs te steunen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---


# De universele editor aanpassen en uitbreiden {#customizing-extending}

Leer over de verschillende uitbreidingspunten en andere eigenschappen die u toestaan om de auteurservaring van de Universele Redacteur aan te passen om de behoeften van uw inhoudsauteurs te steunen.

## Overzicht {#overview}

De Universele Redacteur staat voor twee soorten aanpassing voor de behoeften van uw project toe.

* [ die de Universele Redacteur ](#customizing) aanpassen - de standaardfunctionaliteit van de Universele Redacteur kan via verscheidene aanpassingsconfiguraties worden aangepast.
* [ Uitbreidend de Universele Redacteur UI ](#extending) - UI van de Universele Redacteur kan ook worden uitgebreid gebruikend App Builder om aan uw projectbehoeften te voldoen.

Beide typen worden in de volgende secties beschreven.

## De universele editor aanpassen {#customizing}

De Universal Editor biedt verschillende ingebouwde opties om de functionaliteit ervan aan te passen.

### Publiceren uitschakelen {#disable-publish}

Voor bepaalde ontwerpworkflows moet de inhoud worden gecontroleerd voordat deze wordt gepubliceerd. In dergelijke situaties mag de optie om te publiceren niet beschikbaar zijn voor auteurs.

De **knoop van Publish** kan daarom volledig in app worden onderdrukt door de volgende meta-gegevens toe te voegen.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```

### Componenten filteren {#filtering-components}

U kunt de toegestane componenten per container in de Universele Redacteur beperken gebruikend componentenfilters. Gelieve te zien het document [ Filtrerend Componenten ](/help/implementing/universal-editor/filtering.md) voor meer informatie.

### Componenten voorwaardelijk tonen en verbergen in deelvenster Eigenschappen {#conditionally-hide}

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

>] de Toestand van 0} Waar {[!TAB 

![ Getoonde tekstgebied ](assets/shown.png)

>[!ENDTABS]

### Aangepaste voorbeeld-URL&#39;s {#custom-preview-urls}

U kunt een douanevoorproef URL via a `urn:adobe:aue:config:preview` metaconfiguratie specificeren, die wanneer het klikken van de **Open pagina** knoop in de [ top-right toolbar van de redacteur ](/help/sites-cloud/authoring/universal-editor/navigation.md#universal-editor-toolbar) zal openen.

Dit is met name nuttig voor toepassingen met specifieke voorproefvereisten, zoals die [ gebruikend Edge Delivery Services met het auteursrecht van WYSIWYG ](/help/edge/wysiwyg-authoring/authoring.md).

Hiervoor neemt u gewoon de gewenste voorvertoning-URL op in een metatag van de van instrumenten voorziene app, zoals in het volgende voorbeeld.

```html
<meta name="urn:adobe:aue:config:preview" content="https://wknd.site"/>
```

## De gebruikersinterface van de Universal Editor uitbreiden {#extending}

Als dienst van Adobe Experience Cloud, kan de Universele UI van de Redacteur worden uitgebreid gebruikend App Builder en de Experience Manager.

UI-extensies zijn JavaScript-toepassingen die zijn gebouwd met Adobe App Builder en die kunnen worden ingesloten in UI-toepassingen die worden uitgevoerd onder Adobe Experience Cloud Unified Shell, zoals de Universal Editor. U kunt uw eigen knoppen en handelingen toevoegen aan het koptekstmenu en het deelvenster Eigenschappen en u kunt ook uw eigen gebeurtenissen voor de Universal Editor maken.

Zie de volgende bronnen als u deze mogelijkheden wilt verkennen:

1. [ Uitbreidbaarheid UI ](https://developer.adobe.com/uix/docs/) - dit is de ontwikkelaardocumentatie voor uitbreiding UI.
1. [ UI de Gidsen van de Rekbaarheid ](https://developer.adobe.com/uix/docs/guides/) - geleidelijke instructies op hoe te om uw eigen uitbreiding te ontwikkelen
1. [ de Universele Punten van de Uitbreiding van de Redacteur ](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) - Universele redacteur-specifieke documentatie van het uitbreidingspunt

>[!TIP]
>
>Als u het leren door voorbeeld verkiest, te zien gelieve [ AEM UI rekbaarheidsleerprogramma ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview). Hoewel het zich concentreert op het uitbreiden van de console van het Fragment van de Inhoud, zijn de concepten voor het uitvoeren van een uitbreiding UI in de Universele Redacteur het zelfde.

[ Gebruikend Extension Manager in AEM Sites ](https://developer.adobe.com/uix/docs/extension-manager/), kunt u uw uitbreidingen op een per-instantiebasis toelaten of onbruikbaar maken, toegang tot de eerste partijuitbreidingen van de Adobe met inbegrip van die voor de Universele Redacteur, en veel meer.
