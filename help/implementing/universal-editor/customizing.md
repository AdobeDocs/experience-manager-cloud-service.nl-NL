---
title: De universele editor aanpassen en uitbreiden
description: Leer over de verschillende uitbreidingspunten en andere eigenschappen die u toestaan om UI van de Universele Redacteur aan te passen om de behoeften van uw inhoudsauteurs te steunen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
source-git-commit: bdd67fb383bf20399eacaf9b9c086ea8468ea742
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---


# De universele editor aanpassen en uitbreiden {#customizing-extending}

Leer over de verschillende uitbreidingspunten en andere eigenschappen die u toestaan om de auteurservaring van de Universele Redacteur aan te passen om de behoeften van uw inhoudsauteurs te steunen.

## Overzicht {#overview}

De Universele Redacteur staat voor twee soorten aanpassing voor de behoeften van uw project toe.

* [De universele editor aanpassen](#customizing) - De standaardfunctionaliteit van de Universal Editor kan via verschillende aanpassingsconfiguraties worden aangepast.
* [De gebruikersinterface van de Universal Editor uitbreiden](#extending) - UI van de Universele Redacteur kan ook worden uitgebreid gebruikend App Builder om aan uw projectbehoeften te voldoen.

Beide typen worden in de volgende secties beschreven.

## De universele editor aanpassen {#customizing}

De Universal Editor biedt verschillende ingebouwde opties om de functionaliteit ervan aan te passen.

### Publiceren uitschakelen {#disable-publish}

Voor bepaalde ontwerpworkflows moet de inhoud worden gecontroleerd voordat deze wordt gepubliceerd. In dergelijke situaties mag de optie om te publiceren niet beschikbaar zijn voor auteurs.

De **Publiceren** Deze knop kan daarom volledig in een app worden onderdrukt door de volgende metagegevens toe te voegen.

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

### Componenten voorwaardelijk tonen en verbergen in Eigenschapcontrole {#conditionally-hide}

Hoewel een component of componenten doorgaans beschikbaar zijn voor de auteurs, kunnen er bepaalde situaties zijn waarin dit geen nut heeft. In dergelijke gevallen kunt u componenten in de eigenschappen-rail verbergen door een `condition` aan de [velden van het componentmodel.](/help/implementing/universal-editor/field-types.md#fields)

Voorwaarden kunnen worden gedefinieerd met behulp van [JsonLogic-schema.](https://jsonlogic.com/) Als de voorwaarde waar is, wordt het veld weergegeven. Als de voorwaarde onwaar is, wordt het veld verborgen.

>[!BEGINTABS]

>[!TAB Voorbeeldmodel]

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

>[!TAB Onjuiste voorwaarde]

![Verborgen tekstveld](assets/hidden.png)

>[!TAB Voorwaarde waar]

![Weergegeven tekstveld](assets/shown.png)

>[!ENDTABS]

## De gebruikersinterface van de Universal Editor uitbreiden {#extending}

Als dienst van Adobe Experience Cloud, kan UI van de Universele Redacteur worden uitgebreid gebruikend de Bouwer van de App en de Experience Manager.

UI-extensies zijn JavaScript-toepassingen die zijn gemaakt met Adobe App Builder en die kunnen worden ingesloten in UI-toepassingen die worden uitgevoerd onder Adobe Experience Cloud Unified Shell, zoals de Universal Editor. U kunt uw eigen knoppen en handelingen toevoegen aan het koptekstmenu en de eigenschappen per spoor en u kunt uw eigen gebeurtenissen voor de Universal Editor maken.

Zie de volgende bronnen als u deze mogelijkheden wilt verkennen:

1. [UI-uitbreidbaarheid](https://developer.adobe.com/uix/docs/) - Dit is de ontwikkelaarsdocumentatie voor uitbreiding UI.
1. [UI-uitbreidingshulplijnen](https://developer.adobe.com/uix/docs/guides/) - Stapsgewijze instructies voor het ontwikkelen van uw eigen extensie
1. [De extensiepunten van de Universal Editor](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) - Universal Editor-specifieke documentatie voor extensiepunten

>[!TIP]
>
>Als u liever per voorbeeld wilt leren, raadpleegt u de [AEM zelfstudie over uitbreidbaarheid voor UI.](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview) Hoewel het zich concentreert op het uitbreiden van de console van het Fragment van de Inhoud, zijn de concepten voor het uitvoeren van een uitbreiding UI in de Universele Redacteur het zelfde.

[Extension Manager gebruiken in AEM Sites,](https://developer.adobe.com/uix/docs/extension-manager/) u kunt uw uitbreidingen op een per-instantie basis toelaten of onbruikbaar maken, hebt toegang tot de eerste partijuitbreidingen van de Adobe met inbegrip van die voor de Universele Redacteur, en nog veel meer.
