---
title: De universele editor aanpassen en uitbreiden
description: Leer over de verschillende uitbreidingspunten en andere eigenschappen die u toestaan om UI van de Universele Redacteur aan te passen om de behoeften van uw inhoudsauteurs te steunen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '578'
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

Vervolgens kunt u naar de filterdefinitie van de containercomponent verwijzen door de eigenschap `data-aue-filter` toe te voegen en de id door te geven van het filter dat u eerder hebt gedefinieerd.

```html
data-aue-filter="container-filter"
```

Als u het kenmerk `components` in een filterdefinitie instelt op `null` , worden alle componenten toegestaan, net als wanneer er geen filter is.

```json
[
  {
    "id": "another-container-filter",
     "components": null
   }
]
```

### Componenten voorwaardelijk tonen en verbergen in Eigenschapcontrole {#conditionally-hide}

Hoewel een component of componenten doorgaans beschikbaar zijn voor de auteurs, kunnen er bepaalde situaties zijn waarin dit geen nut heeft. In dergelijke gevallen, kunt u componenten in het eigenschappen spoor verbergen door a `condition` attributen aan de [ gebieden van het componentenmodel toe te voegen.](/help/implementing/universal-editor/field-types.md#fields)

De voorwaarden kunnen worden bepaald gebruikend [ schema JsonLogic.](https://jsonlogic.com/) Als de voorwaarde true is, wordt het veld weergegeven. Als de voorwaarde onwaar is, wordt het veld verborgen.

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

## De gebruikersinterface van de Universal Editor uitbreiden {#extending}

Als dienst van Adobe Experience Cloud, kan de Universele UI van de Redacteur worden uitgebreid gebruikend App Builder en de Experience Manager.

UI-extensies zijn JavaScript-toepassingen die zijn gebouwd met Adobe App Builder en die kunnen worden ingesloten in UI-toepassingen die worden uitgevoerd onder Adobe Experience Cloud Unified Shell, zoals de Universal Editor. U kunt uw eigen knoppen en handelingen toevoegen aan het koptekstmenu en de eigenschappen per spoor en u kunt uw eigen gebeurtenissen voor de Universal Editor maken.

Zie de volgende bronnen als u deze mogelijkheden wilt verkennen:

1. [ Uitbreidbaarheid UI ](https://developer.adobe.com/uix/docs/) - dit is de ontwikkelaardocumentatie voor uitbreiding UI.
1. [ UI de Gidsen van de Rekbaarheid ](https://developer.adobe.com/uix/docs/guides/) - geleidelijke instructies op hoe te om uw eigen uitbreiding te ontwikkelen
1. [ de Universele Punten van de Uitbreiding van de Redacteur ](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) - Universele redacteur-specifieke documentatie van het uitbreidingspunt

>[!TIP]
>
>Als u liever per voorbeeld wilt leren, raadpleegt u de zelfstudie over de uitbreidbaarheid van de gebruikersinterface van [AEM .](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview) Hoewel het zich concentreert op het uitbreiden van de console van het Fragment van de Inhoud, zijn de concepten voor het uitvoeren van een uitbreiding UI in de Universele Redacteur het zelfde.

[ Gebruikend Extension Manager in AEM Sites, ](https://developer.adobe.com/uix/docs/extension-manager/) u kunt uw uitbreidingen op een per-instantiebasis toelaten of onbruikbaar maken, toegang tot de eerste partijuitbreidingen van de Adobe met inbegrip van die voor de Universele Redacteur, en veel meer.
