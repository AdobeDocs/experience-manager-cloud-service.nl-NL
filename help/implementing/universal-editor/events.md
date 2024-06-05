---
title: Universal Editor-gebeurtenissen
description: Leer over de verschillende gebeurtenissen die de Universele Redacteur verzendt die u kunt gebruiken om op inhoud of veranderingen UI in uw verre app te reageren.
exl-id: c9f7c284-f378-4725-a4e6-e4799f0f8175
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---

# Universal Editor-gebeurtenissen {#events}

Leer over de verschillende gebeurtenissen die de Universele Redacteur verzendt die u kunt gebruiken om op inhoud of veranderingen UI in uw verre app te reageren.

## Inleiding {#introduction}

Toepassingen kunnen verschillende vereisten hebben voor pagina- of componentupdates. Daarom verzendt de Universele Redacteur bepaalde gebeurtenissen naar verre toepassingen. Als de externe toepassing geen aangepaste gebeurtenislistener voor de verzonden gebeurtenis heeft, [fallback-gebeurtenislistener](#fallback-listeners) door de `universal-editor-cors` pakket wordt uitgevoerd.

Alle gebeurtenissen worden aangeroepen op het betrokken DOM-element van de externe pagina. Gebeurtenissen worden doorgegeven naar de `BODY` element waarbij de standaardgebeurtenislistener wordt opgegeven door de `universal-editor-cors` pakket is geregistreerd. Er zijn gebeurtenissen voor de inhoud en de gebeurtenissen voor UI.

Alle gebeurtenissen volgen een naamgevingsconventie.

* `aue:<content-or-ui>-<event-name>`

Bijvoorbeeld: `aue:content-update` en `aue:ui-select`

De gebeurtenissen omvatten de lading van het verzoek en van de reactie en worden teweeggebracht zodra de overeenkomstige vraag succesvol is. Voor meer informatie over oproepen en voorbeelden van hun lading, gelieve te zien het document [Universal Editor-aanroepen.](/help/implementing/universal-editor/calls.md)

## Gebeurtenissen voor bijwerken van inhoud {#content-events}

### aub:content-add {#content-add}

De `aue:content-add` gebeurtenis wordt geactiveerd wanneer een nieuwe component aan een container wordt toegevoegd.

De nuttige lading is inhoud van de Universele dienst van de Redacteur, met reserveinhoud van de componentendefinitie.

```json
{
    details: {
        request: request payload;   // what is sent to the service
        response: {                 // what is returned by the service
            resource: string;       // newly created content resource
            updates: [{
                resource: string;   // resource to update
                type: string;       // type of instrumentation
                content?: string;   // content to replace
            }]
        }
    }
}
```

### aub:content-details {#content-details}

De `aue:content-details` gebeurtenis wordt geactiveerd wanneer een component in de eigenschappenrails wordt geladen.

De nuttige lading is de inhoud van de component en naar keuze zijn schema.

```json
{
    details: {
        content: object             // content object
        model: [object]             // model object
        request: request payload;   // what is sent to the service
        response: response payload; // what is returned by the service
    }
}
```

### aub:content-move {#content-move}

De `aue:content-move` wordt geactiveerd wanneer een component wordt verplaatst.

De nuttige lading is de component, broncontainer, en doelcontainer.

```json
{
    details: {
        from: string;                   // container we move the component from
        component: string;              // component we move
        to: string;                     // container we move the component to
        before: string;                    // before which component shall we place the component
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service
    }
}
```

### aue:content-patch {#content-patch}

De `aue:content-patch` gebeurtenis wordt geactiveerd wanneer de gegevens van een component worden bijgewerkt in eigenschappen rail.

De payload is een JSON-patch van de bijgewerkte eigenschappen.

```json
{
    details: {
        patch: {
            name: string;               // attribute which is updated
            value: string;              // new value which is stored to the attribute
        },
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service
    }
}
```

### aub:content-remove {#content-remove}

De `aue:content-remove` gebeurtenis wordt geactiveerd wanneer een component uit een container wordt verwijderd.

De lading is item-id van de verwijderde component.

```json
{
    details: {
        resource: string;               // the resource which got removed
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service
    }
}
```

### aub:content-update {#content-update}

De `aue:content-update` gebeurtenis wordt geactiveerd wanneer de eigenschappen van een component in de context worden bijgewerkt.

De payload is de bijgewerkte waarde.

```json
{
    details: {
        value: string;                  // updated value
        request: request payload;       // what is sent to the service
        response: response payload;     // what is returned by the service 
    }
}
```

### Payloads passeren {#passing-payloads}

Voor alle update-gebeurtenissen voor de inhoud worden zowel de gevraagde payload als de antwoordlading aan de gebeurtenis doorgegeven. Bijvoorbeeld voor een updateoproep:

Payload aanvragen:

```json
{
  "connections": [
    {
      "name": "aemconnection",
      "protocol": "aem",
      "uri": "https://author-p7452-e12433.adobeaemcloud.com"
    }
  ],
  "target": {
    "resource": "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
    "type": "text",
    "prop": "title"
  },
  "value": "Alhoa Spirit Northern Norway!"
}
```

Respons Payload

```json
{
    "updates": [
        {
            "resource": "urn:aemconnection:/content/dam/wknd-shared/en/magazine/arctic-surfing/aloha-spirits-in-northern-norway/jcr:content/data/master",
            "prop": "title",
            "type": "text"
        }
    ]
}
```

## UI-gebeurtenissen {#ui-events}

### aue:ui-publish {#ui-publish}

De `aue:ui-publish` De gebeurtenis wordt geactiveerd wanneer inhoud wordt gepubliceerd (met oproeping op het `BODY` niveau).

De lading is een lijst van objecten IDs en hun publicatiestatus.

### aue:ui-select {#ui-select}

De `aue:ui-select` wordt geactiveerd wanneer een component wordt geselecteerd.

De nuttige lading is punt identiteitskaart, punteigenschappen, en punttype van de geselecteerde component.

```json
{
    details: {
        resource: string;       // resource of the selected
        prop: string;           // prop of the selected
        type: string;           // type of the selected
        selected: boolean;      // was selected or unselected
    }
}
```

### aue:ui-preview {#ui-preview}

De `aue:ui-preview` gebeurtenis wordt geactiveerd wanneer de bewerkingsmodus van de pagina wordt gewijzigd in **Voorvertoning**.

De payload is leeg voor deze gebeurtenis.

```json
{
    details: {}
}
```

### aue:bewerken {#ui-edit}

De `aue:ui-edit` gebeurtenis wordt geactiveerd wanneer de bewerkingsmodus van de pagina wordt gewijzigd in **Bewerken**.

De payload is leeg voor deze gebeurtenis.

```json
{
    details: {}
}
```

### aue:gebruikersinterface-viewport-change {#ui-viewport-change}

De `aue:ui-viewport-change` gebeurtenis wordt geactiveerd wanneer de grootte van de viewport wordt gewijzigd.

De nuttige lading is de afmetingen van viewport.

```json
{
    details: {
        height: number?;        // height of the viewport. Undefined when fullscreen
        width: number?;         // width of the viewport. Undefined when fullscreen
    }
}
```

### aue:geïnitialiseerd {#initialized}

De `aue:initialized` Deze gebeurtenis wordt geactiveerd om de externe pagina te laten weten dat deze is geladen in de Universal Editor.

De payload is leeg voor deze gebeurtenis.

```json
{
    details: {}
}
```

## Alternatieve gebeurtenislisteners {#fallback-listeners}

### Updates van inhoud {#content-update-fallbacks}

| Gebeurtenis | Gedrag |
|---|---|
| `aue:content-add` | Pagina opnieuw laden |
| `aue:content-details` | Niets doen |
| `aue:content-move` | De inhoud/structuur van de component naar het doelgebied verplaatsen |
| `aue:content-patch` | Pagina opnieuw laden |
| `aue:content-remove` | Het DOM-element verwijderen |
| `aue:content-update` | Werk de `innerHTML` met de lading |

### UI-gebeurtenissen {#ui-event-fallbacks}

| Gebeurtenis | Gedrag |
|---|---|
| `aue:ui-publish` | Niets doen |
| `aue:ui-select` | Naar het geselecteerde element schuiven |
| `aue:ui-preview` | Toevoegen `class="adobe-ue-preview"` naar tag HTML |
| `aue:ui-edit` | Toevoegen `class=adobe-ue-edit"` naar tag HTML |
| `aue:ui-viewport-change` | Niets doen |
| `aue:initialized` | Niets doen |

## Aanvullende bronnen {#additional-resources}

* [Universal Editor-aanroepen](/help/implementing/universal-editor/calls.md)

