---
title: ContextHub toevoegen aan Pagina's en Toegang tot Sporen
description: Voeg ContextHub aan uw pagina's toe om de eigenschappen ContextHub toe te laten en aan de bibliotheken van JavaScript te verbinden ContextHub
exl-id: 8bfe2cff-3944-4e86-a95c-ebf1cb13913c
feature: Developing, Personalization
role: Admin, Architect, Developer
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# ContextHub toevoegen aan Pagina&#39;s en Toegang tot Sporen {#adding-contexthub-to-pages-and-accessing-stores}

Voeg ContextHub aan uw pagina&#39;s toe om de eigenschappen ContextHub toe te laten en aan de bibliotheken van JavaScript te verbinden ContextHub.

De ContextHub JavaScript API verleent toegang tot de contextgegevens die ContextHub beheert. Deze pagina beschrijft kort de belangrijkste eigenschappen van API voor de toegang tot van en het manipuleren van contextgegevens. Volg de koppelingen naar de API-naslagdocumentatie voor gedetailleerde informatie en codevoorbeelden.

## ContextHub toevoegen aan een paginacomponent {#adding-contexthub-to-a-page-component}

Om de eigenschappen ContextHub toe te laten en aan de bibliotheken van ContextHub JavaScript te verbinden, omvat de `contexthub` component in de `head` sectie van uw pagina. De HTML-code voor uw paginacomponent moet op het volgende voorbeeld lijken:

```xml
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

U moet ook vormen of de toolbar ContextHub op de wijze van de Voorproef verschijnt. Zie [ het Tonen van en het Hiding van ContextHub UI ](configuring-contexthub.md#showing-and-hiding-the-contexthub-ui).

## Informatie over ContextHub-winkels {#about-contexthub-stores}

De opslag van ContextHub van het gebruik om contextgegevens voort te zetten. ContextHub verstrekt de volgende types van opslag die de basis van alle opslagtypes vormen:

* [PersistedStore](contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersistedJSONPStore](contexthub-api.md#contexthub-store-persistedstore)

Alle winkeltypen zijn extensies van de klasse [`ContextHub.Store.Core`](contexthub-api.md#contexthub-store-core) . Voor informatie over het creëren van een opslagtype, zie [ Creërend de Opslag van de Douane ](extending-contexthub.md#creating-custom-store-candidates). Voor informatie over de types van steekproefopslag, zie [ de Kandidaten van de Winkel van de Steekproef ContextHub ](sample-stores.md).

### Persistentiemodi {#persistence-modes}

De opslag van de Hub van de context gebruikt één van de volgende persistentiemodi:

* **Lokaal:** gebruikt HTML5 localStorage om gegevens voort te zetten. Lokale opslag blijft in de browser tijdens sessies behouden.
* **Zitting:** gebruikt HTML5 sessionStorage om gegevens voort te zetten. De opslag van de zitting wordt voortgeduurd voor de browser zitting en is beschikbaar aan alle browser vensters.
* **Koekje:** gebruikt de browser inheemse steun van koekjes voor gegevensopslag. De gegevens van het koekje worden verzonden naar en van de server in HTTP- verzoeken.
* **Window.name:** gebruikt het window.name bezit om gegevens voort te zetten.
* **Geheugen:** gebruikt een voorwerp van JavaScript om gegevens voort te zetten.

Door gebrek, gebruikt de Hub van de Context de Lokale persistentiemodus. Als de browser geen ondersteuning biedt voor HTML5 localStorage of als dit niet is toegestaan, wordt de sessiepersistentie gebruikt. Als de browser HTML5 sessionStorage niet ondersteunt of toestaat, wordt Window.name persistence gebruikt.

### Gegevens opslaan {#store-data}

Intern vormen opslaggegevens een boomstructuur, waardoor waarden kunnen worden toegevoegd als primaire typen of complexe objecten. Wanneer u complexe objecten toevoegt aan opslagruimten, vormen de objecteigenschappen vertakkingen in de gegevensstructuur. Het volgende complexe object wordt bijvoorbeeld toegevoegd aan een lege opslaglocatie met de naam location:

```javascript
Object {
   number: 321,
   data: {
      city: "Basel",
      country: "Switzerland",
      details: {
         population: 173330,
         elevation: 260
      }
   }
}
```

De boomstructuur van de opslaggegevens kan als volgt worden geconceptualiseerd:

```text
/
|- number
|- data
      |- city
      |- country
      |- details
            |- population
            |- elevation
```

De boomstructuur bepaalt gegevenspunten in de opslag als sleutel/waardeparen. In het bovenstaande voorbeeld komt de sleutel `/number` overeen met de waarde `321` en de sleutel `/data/country` met de waarde `Switzerland` .

### Objecten bewerken {#manipulating-objects}

ContextHub biedt de [`ContextHub.Utils.JSON.tree`](contexthub-api.md#contexthub-utils-json-tree) -klasse voor het manipuleren van JavaScript-objecten. Gebruik de functies van deze klasse voor het manipuleren van JavaScript-objecten voordat u ze aan een winkel toevoegt of nadat u ze uit een winkel hebt opgehaald.

De klasse [`ContextHub.Utils.JSON`](contexthub-api.md#contexthub-utils-json) biedt ook functies voor het serieel ordenen van objecten met tekenreeksen en het ongedaan maken van tekenreeksen met objecten. Gebruik deze klasse voor het verwerken van JSON-gegevens om browsers te ondersteunen die de functies `JSON.parse` en `JSON.stringify` niet native bevatten.

## Interactief werken met ContextHub-winkels {#interacting-with-contexthub-stores}

Gebruik het JavaScript-object [`ContextHub`](contexthub-api.md#ui-event-constants) om een winkel te verkrijgen als een JavaScript-object. Nadat u het opslagobject hebt verkregen, kunt u de gegevens in het object bewerken. Gebruik de functie [`getAllStores`](contexthub-api.md#getallstores) of [`getStore`](contexthub-api.md#getstore-name) om de winkel te verkrijgen.

### Winkelgegevens openen {#accessing-store-data}

De JavaScript-klasse [`ContexHub.Store.Core`](contexthub-api.md#contexthub-store-core) definieert verschillende functies voor interactie met opslaggegevens. Met de volgende functies worden meerdere gegevensitems in objecten opgeslagen en opgehaald:

* [addAllItems](contexthub-api.md#addallitems-tree-options)
* [getTree](contexthub-api.md#gettree-includeinternals)

Afzonderlijke gegevensitems worden opgeslagen als een set sleutel-/waardeparen. Als u waarden wilt opslaan en ophalen, geeft u de bijbehorende sleutel op:

* [getItem](contexthub-api.md#getitem-key)
* [setItem](contexthub-api.md#setitem-key-value-options)

De opslagkandidaten van de douane kunnen extra functies bepalen die toegang verlenen om gegevens op te slaan.

>[!NOTE]
>
>ContextHub is niet door gebrek zich bewust van momenteel het programma geopend op publiceer servers en dergelijke gebruikers worden beschouwd door ContextHub als &quot;Anoniem.&quot;
>
>U kunt ContextHub bewust maken van het programma geopende gebruikers door de profielopslag te laden. Zie de steekproefcode: [ aem-sample-wij-retail op GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js).

### ContextHub Event {#contexthub-eventing}

ContextHub omvat een gebeurteniskader dat u toelaat om automatisch te reageren om gebeurtenissen op te slaan. Elk opslagobject bevat een [`ContextHub.Utils.Eventing`](contexthub-api.md#contexthub-utils-eventing) -object dat beschikbaar is als de [`eventing`](contexthub-api.md#eventing) -eigenschap van de winkel. Gebruik de functie [`on`](contexthub-api.md#on-name-handler-selector-triggerforpastevents) of [`once`](contexthub-api.md#once-name-handler-selector-triggerforpastevents) om een JavaScript-functie te binden aan een store-gebeurtenis.

## Contexthub gebruiken om cookies te manipuleren {#using-context-hub-to-manipulate-cookies}

De Context Hub JavaScript API biedt ondersteuning voor verschillende browsers voor het verwerken van browsercookies. De naamruimte [`ContextHub.Utils.Cookie`](contexthub-api.md#contexthub-utils-cookie) definieert verschillende functies voor het maken, bewerken en verwijderen van cookies.

## Opgeloste ContextHub-segmenten bepalen {#determining-resolved-contexthub-segments}

De ContextHub segmentmotor laat u toe om te bepalen welke van de geregistreerde segmenten in de huidige context worden opgelost. Gebruik de functie getResolvedSegments van de klasse [`ContextHub.SegmentEngine.SegmentManager`](contexthub-api.md#contexthub-segmentengine-segmentmanager) om omgezette segmenten op te halen. Vervolgens gebruikt u de functie `getName` of `getPath` van de klasse [`ContextHub.SegmentEngine.Segment`](contexthub-api.md#contexthub-segmentengine-segment) om te testen op een segment.

### ContextHub-segmenten {#contexthub-segments}

ContextHub-segmenten worden onder het knooppunt `/conf/<site>/settings/wcm/segments` geïnstalleerd.

De volgende segmenten worden geïnstalleerd met de [ plaats van het WKND leerprogramma ](/help/implementing/developing/introduction/develop-wknd-tutorial.md).

* zomer
* winter

De regels die worden gebruikt om deze segmenten op te lossen zijn als volgt samengevat:

* Eerst wordt de [ geolocatie ](sample-stores.md#contexthub-geolocation-sample-store-candidate) opslag gebruikt om breedtegraad van de gebruiker te bepalen.
* Dan bepaalt het maandgegevenspunt van de [ surferinfo opslag ](sample-stores.md#contexthub-surferinfo-sample-store-candidate) welk seizoen het in die breedtegraad is.

>[!WARNING]
>
>De geïnstalleerde segmenten worden verstrekt als verwijzingsconfiguraties om u te helpen uw eigen specifieke configuratie voor uw project bouwen. Niet direct gebruiken.

## Foutopsporing in ContextHub {#debugging-contexthub}

Er zijn verscheidene opties voor het zuiveren ContextHub met inbegrip van het produceren van logboeken. Zie [ het Vormen ContextHub voor meer informatie.](configuring-contexthub.md#logging-debug-messages-for-contexthub)

## Zie een Overzicht van het Kader ContextHub {#see-an-overview-of-the-contexthub-framework}

ContextHub verstrekt a [ diagnostische pagina ](contexthub-diagnostics.md) waar u een overzicht van het kader ContextHub kunt zien.
