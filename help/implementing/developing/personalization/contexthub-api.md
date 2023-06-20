---
title: ContextHub JavaScript API-naslaggids
description: De JavaScript API van ContextHub is beschikbaar aan uw manuscripten wanneer de component ContextHub aan de pagina is toegevoegd
exl-id: ec35bef5-610c-4e85-a43a-d4201b5eb03e
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '4620'
ht-degree: 0%

---

# ContextHub JavaScript API-naslaggids {#contexthub-javascript-api-reference}

De JavaScript-API van ContextHub is beschikbaar voor uw scripts wanneer de [De component ContextHub is toegevoegd aan de pagina](adding-contexthub.md).

## ContextHub-constanten {#contexthub-constants}

Constante waarden die door de JavaScript-API van ContextHub worden gedefinieerd.

### Gebeurtenisconstanten {#event-constants}

De volgende lijst maakt een lijst van de namengebeurtenissen die voor Winkels ContextHub voorkomen. Zie ook [ContextHub.Utils.Event](#contexthub-utils-eventing).

| Constante | Beschrijving | Waarde |
|---|---|---|
| `ContextHub.Constants.EVENT_NAMESPACE` | ContextHub-gebeurtenisnaamruimte | `ch` |
| `ContextHub.Constants.EVENT_ALL_STORES_READY` | Geeft aan dat alle vereiste winkels zijn geregistreerd, geïnitialiseerd en klaar zijn om te worden verbruikt | `all-stores-ready` |
| `ContextHub.Constants.EVENT_STORES_PARTIALLY_READY` | Geeft aan dat niet alle winkels binnen een bepaalde tijd zijn geïnitialiseerd | `stores-partially-ready` |
| `ContextHub.Constants.EVENT_STORE_REGISTERED` | Wordt geactiveerd wanneer een winkel is geregistreerd | `store-registered` |
| `ContextHub.Constants.EVENT_STORE_READY` | Geeft aan dat winkels klaar zijn om te werken. Het wordt teweeggebracht onmiddellijk na registratie, behalve JSONP slaat op, waar het in brand wordt gestoken wanneer het gegeven wordt opgehaald). | `store-ready` |
| `ContextHub.Constants.EVENT_STORE_UPDATED` | Wordt geactiveerd wanneer een winkel de persistentie bijwerkt | `store-updated` |
| `ContextHub.Constants.PERSISTENCE_CONTAINER_NAME` | Naam container voor persistentie | `ContextHubPersistence` |
| `ContextHub.Constants.SERVICE_RAW_RESPONSE_KEY` | Hiermee wordt de specifieke naam van de persistentiesleutel opgeslagen waar het Raw JSON-resultaat wordt opgeslagen | `/_/raw-response` |
| `ContextHub.Constants.SERVICE_RESPONSE_TIME_KEY` | Hiermee wordt een specifieke tijdstempel opgeslagen die aangeeft wanneer JSON-gegevens zijn opgehaald | `/_/response-time` |
| `ContextHub.Constants.SERVICE_LAST_URL_KEY` | Hiermee wordt de specifieke URL van de JSON-service opgeslagen die tijdens de laatste aanroep is gebruikt | `/_/url` |
| `ContextHub.Constants.IS_CONTAINER_EXPANDED` | Geeft aan of de UI van ContextHub is uitgebreid | `/_/container-expanded` |

### UI-gebeurtenisconstanten {#ui-event-constants}

De volgende lijst maakt een lijst van de namen van gebeurtenissen die voor ContextHub UI voorkomen.

| **Constante** | **Beschrijving** | **Waarde** |
|---|---|---|
| `ContextHub.Constants.EVENT_UI_MODE_REGISTERED` | Wordt geactiveerd wanneer een modus is geregistreerd | `ui-mode-registered` |
| `ContextHub.Constants.EVENT_UI_MODE_UNREGISTERED` | Wordt geactiveerd wanneer een modus niet is geregistreerd | `ui-mode-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODE_RENDERER_REGISTERED` | Wordt geactiveerd wanneer een modusrenderer is geregistreerd | `ui-mode-renderer-registered` |
| `ContextHub.Constants.EVENT_UI_MODE_RENDERER_UNREGISTERED` | Wordt geactiveerd wanneer een renderer voor een modus niet is geregistreerd | `ui-mode-renderer-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODE_ADDED` | Wordt geactiveerd wanneer een nieuwe modus wordt toegevoegd | `ui-mode-added` |
| `ContextHub.Constants.EVENT_UI_MODE_REMOVED` | Wordt geactiveerd wanneer een modus wordt verwijderd | `ui-mode-removed` |
| `ContextHub.Constants.EVENT_UI_MODE_SELECTED` | Wordt geactiveerd wanneer een modus door de gebruiker is geselecteerd | `ui-mode-selected` |
| `ContextHub.Constants.EVENT_UI_MODULE_REGISTERED` | Wordt geactiveerd wanneer een nieuwe module is geregistreerd | `ui-module-registered` |
| `ContextHub.Constants.EVENT_UI_MODULE_UNREGISTERED` | Wordt geactiveerd wanneer een module niet is geregistreerd | `ui-module-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODULE_RENDERER_REGISTERED` | Wordt geactiveerd wanneer een modulerenderer is geregistreerd | `ui-module-renderer-registered` |
| `ContextHub.Constants.EVENT_UI_MODULE_RENDERER_UNREGISTERED` | Wordt geactiveerd wanneer een modulerenderer niet is geregistreerd | `ui-module-renderer-unregistered` |
| `ContextHub.Constants.EVENT_UI_MODULE_ADDED` | Wordt geactiveerd wanneer een nieuwe module wordt toegevoegd | `ui-module-added` |
| `ContextHub.Constants.EVENT_UI_MODULE_REMOVED` | Wordt geactiveerd wanneer een module wordt verwijderd | `ui-module-removed` |
| `ContextHub.Constants.EVENT_UI_CONTAINER_ADDED` | Wordt geactiveerd wanneer de UI-container aan de pagina wordt toegevoegd | `ui-container-added` |
| `ContextHub.Constants.EVENT_UI_CONTAINER_OPENED` | Wordt geactiveerd wanneer de ContextHub UI wordt geopend | `ui-container-opened` |
| `ContextHub.Constants.EVENT_UI_CONTAINER_CLOSED` | Wordt geactiveerd wanneer de ContextHub-gebruikersinterface is samengevouwen | `ui-container-closed` |
| `ContextHub.Constants.EVENT_UI_PROPERTY_MODIFIED` | Wordt geactiveerd wanneer een eigenschap wordt gewijzigd | `ui-property-modified` |
| `ContextHub.Constants.EVENT_UI_RENDERED` | Wordt geactiveerd telkens wanneer de ContextHub UI wordt gerenderd (bijvoorbeeld, na een bezitsverandering) | `ui-rendered` |
| `ContextHub.Constants.EVENT_UI_INITIALIZED` | Wordt geactiveerd wanneer de UI-container wordt geïnitialiseerd | `ui-initialized` |
| `ContextHub.Constants.ACTIVE_UI_MODE` | Geeft de actieve UI-modus aan | `/_/active-ui-mode` |

## ContextHub JavaScript API-naslaggids {#contexthub-javascript-api-reference-2}

Het voorwerp ContextHub verleent toegang tot alle opslag.

### Functies (ContextHub) {#functions-contexthub}

#### getAllStores() {#getallstores}

Retourneert alle geregistreerde ContextHub-winkels.

Deze functie heeft geen parameters.

##### Retourneert {#returns-}

Een voorwerp dat alle opslag ContextHub bevat. Elke winkel is een object met dezelfde naam als de winkel.

##### Voorbeeld {#example-}

In het volgende voorbeeld worden alle opslagruimten opgehaald en wordt vervolgens de geolocatieopslag opgehaald:

```javascript
var allStores = ContextHub.getAllStores();
var geoloc = allStores.geolocation
```

#### getStore(name) {#getstore-name}

Hiermee wordt een winkel opgehaald als een JavaScript-object.

##### Parameters {#parameters-}

* **`name`:** De naam waarmee de winkel is geregistreerd.

##### Retourneert {#returns-getstore-name}

Een object dat de winkel vertegenwoordigt.

##### Voorbeeld {#example-getstore-name}

In het volgende voorbeeld wordt de opslag van de geolocatie opgehaald:

```javascript
var geoloc = ContextHub.getStore("geolocation");
```

## ContextHub.SegmentEngine.Segment {#contexthub-segmentengine-segment}

Vertegenwoordigt een segment ContextHub. Gebruik de `ContextHub.SegmentEngine.SegmentManager` om segmenten te verkrijgen.

### Functies (ContextHub.ContextEngine.Segment) {#functions-contexthub-contextengine-segment}

#### getName() {#getname}

Retourneert de naam van het segment als een tekenreekswaarde.

#### getPath() {#getpath}

Retourneert het repository pad van de segmentdefinitie als een String-waarde.

## ContextHub.SegmentEngine.SegmentManager {#contexthub-segmentengine-segmentmanager}

Verleent toegang tot segmenten ContextHub.

### Functies (ContextHub.SegmentEngine.SegmentManager) {#functions-contexthub-segmentengine-segmentmanager}

#### getResolvedSegments() {#getresolvedsegments}

Retourneert de segmenten die zijn omgezet in de huidige context. Deze functie heeft geen parameters.

##### Retourneert {#returns-getresolvedsegments}

Een array van `ContextHub.SegmentEngine.Segment` objecten.

## ContextHub.Store.Core {#contexthub-store-core}

De basisklasse voor opslag ContextHub.

### Eigenschappen (ContextHub.Store.Core) {#properties-contexthub-store-core}

#### voorkomen {#eventing}

A [`ContextHub.Utils.Eventing`](#contexthub-utils-eventing) object. Gebruik dit object voor het binden van functies om gebeurtenissen op te slaan. Voor informatie over de standaardwaarde en initialisatie raadpleegt u [`init(name,config)`](#init-name-config).

#### name {#name}

De naam van de winkel.

#### volharding {#persistence}

A `ContextHub.Utils.Persistence` object. Voor informatie over de standaardwaarde en initialisatie raadpleegt u [`init(name,config)`](#init-name-config).

### Functies (ContextHub.Store.Core) {#functions-contexthub-store-core}

#### addAllItems(tree, options) {#addallitems-tree-options}

Voegt een gegevensobject of een array samen met de opslaggegevens. Elk sleutelwaardepaar in het object of de array wordt aan de winkel toegevoegd (via de `setItem` functie):

* **Object:** Toetsen zijn de eigenschapnamen.
* **Array:** Toetsen zijn de arrayindexen.

Waarden kunnen objecten zijn.

##### Parameters {#parameters-addallitems}

* **`tree`:** (Object of array) De gegevens die aan de winkel moeten worden toegevoegd.
* **`options`:** (Object) Een optioneel object met opties dat wordt doorgegeven aan de functie setItem. Zie voor meer informatie de `options` parameter van [`setItem(key,value,options)`](#setitem-key-value-options).

##### Retourneert {#returns-addallitems}

A `boolean` waarde:

* Een waarde van `true` Hiermee wordt aangegeven dat het gegevensobject is opgeslagen.
* Een waarde van `false` Hiermee wordt aangegeven dat de gegevensopslag ongewijzigd blijft.

#### addReference(key, anotherKey) {#addreference-key-anotherkey}

Maakt een verwijzing van de ene toets naar de andere. Een sleutel kan niet naar zichzelf verwijzen.

##### Parameters {#parameters-addreference}

* **`key`:** De sleutel waarnaar wordt verwezen `anotherKey`.

* **`anotherkey`:** De sleutel waarnaar wordt verwezen door `key`.

##### Retourneert {#returns-addreference}

A `boolean` waarde:

* Een waarde van `true` geeft aan dat de verwijzing is toegevoegd.
* Een waarde van `false` geeft aan dat er geen verwijzing is toegevoegd.

#### noticeReadiness() {#announcereadiness}

Hiermee wordt het dialoogvenster `ready` voor deze winkel. Deze functie heeft geen parameters en retourneert geen waarde.

#### clean() {#clean}

Hiermee verwijdert u alle gegevens uit de winkel. De functie heeft geen parameters en geen geretourneerde waarde.

#### getItem(key) {#getitem-key}

Retourneert de waarde die aan een toets is gekoppeld.

##### Parameters {#parameters-getitem}

* **`key`:** (String) De sleutel waarvoor de waarde moet worden geretourneerd.

##### Retourneert {#returns-getitem}

Een object dat de waarde voor de toets vertegenwoordigt.

#### getKeys(includeInternal) {#getkeys-includeinternals}

Haalt de sleutels uit de opslag op. Naar keuze kunt u de sleutels terugwinnen die intern door het kader ContextHub worden gebruikt.

##### Parameters {#parameters-getkeys}

* **`includeInternals`:** Een waarde van `true` neemt intern gebruikte sleutels in de resultaten op. Deze toetsen beginnen met het onderstrepingsteken (`_`). De standaardwaarde is `false`.

##### Retourneert {#returns-getkeys}

Een array met sleutelnamen ( `string` waarden).

#### getReferences() {#getreferences}

Haalt de verwijzingen uit de opslag op.

##### Retourneert {#returns-getreferences}

Een array die naar toetsen verwijst als indexen voor de toetsen waarnaar wordt verwezen:

* Verwijzen naar sleutels komt overeen met de `key` parameter van de `addReference` functie.
* Sleutels waarnaar wordt verwezen, komen overeen met de `anotherKey` parameter van de `addReference` functie.

#### getTree(includeInternal) {#gettree-includeinternals}

Hiermee wordt de gegevensstructuur uit de opslagruimte opgehaald. Naar keuze kunt u de sleutel/waardeparen omvatten die intern door het kader ContextHub worden gebruikt.

##### Parameters {#parameters-gettree}

* `includeInternals:` Een waarde van `true` neemt intern-gebruikte sleutel/waardeparen in de resultaten op. De sleutels van deze gegevens beginnen met het onderstrepingsteken (`_`). De standaardwaarde is `false`.

##### Retourneert {#returns-gettree}

Een object dat de gegevensstructuur vertegenwoordigt. De sleutels zijn de bezitsnamen van het voorwerp.

#### init(name, config) {#init-name-config}

Initialiseert de winkel.

* Stelt de opslaggegevens in op een leeg object.
* Hiermee stelt u de opslagverwijzingen in naar een leeg object.
* De `eventChannel` is `data:<name>`, waarbij `<name>` is de naam van de winkel.
* De `storeDataKey` is `/store/<name>`, waarbij `<name>` is de naam van de winkel.

##### Parameters {#parameters-init}

* **`name`:** De naam van de winkel.
* **`config`:** Een object dat configuratie-eigenschappen bevat:
   * `eventDeferring`: De standaardwaarde is 32.
   * `eventing`: De [ContextHub.Utils.Event](#contexthub-utils-eventing) object voor deze winkel. De standaardwaarde is `ContextHub.eventing` gebruikt.
   * `persistence`: De `ContextHub.Utils.Persistence` object voor deze winkel. De standaardwaarde is `ContextHub.persistence` object.

#### isEventPaused() {#iseventingpaused}

Bepaalt of de gebeurtenis voor deze opslag wordt gepauzeerd.

##### Retourneert {#returns-iseventingpaused}

Een Booleaanse waarde:

* `true`: De gebeurtenis wordt gepauzeerd zodat geen gebeurtenissen voor deze opslag worden teweeggebracht.
* `false`: De gebeurtenis wordt niet gepauzeerd zodat de gebeurtenissen voor deze opslag worden teweeggebracht.

#### pauseEvent() {#pauseeventing}

Pauzeert het voorkomen voor de opslag zodat geen gebeurtenissen worden teweeggebracht. Deze functie vereist geen parameters en retourneert geen waarde.

#### removeItem(sleutel, opties) {#removeitem-key-options}

Hiermee verwijdert u een sleutel-/waardepaar uit de winkel.

Wanneer een toets wordt verwijderd, activeert de functie het `data` gebeurtenis. De gebeurtenisgegevens omvatten de opslagnaam, de naam van de sleutel die is verwijderd, de waarde die is verwijderd, de nieuwe waarde voor de sleutel (null) en het actietype &quot;remove&quot;.

U kunt desgewenst het activeren van de `data` gebeurtenis.

##### Parameters {#parameters-removeitem}

* **`key`:** (String) De naam van de toets die moet worden verwijderd.
* **`options`:** (Object) Een object met opties. De volgende objecteigenschappen zijn geldig:
   * stil: Een waarde van `true` voorkomt dat de `data` gebeurtenis. De standaardwaarde is `false`.

##### Retourneert {#returns-removeitem}

A `boolean` waarde:

* Een waarde van `true` Geeft aan dat het sleutelwaardepaar is verwijderd.
* Een waarde van `false` Hiermee wordt aangegeven dat de gegevensopslag ongewijzigd blijft omdat de sleutel niet in de opslag is gevonden.

#### removeReference(key) {#removereference-key}

Hiermee verwijdert u een verwijzing uit de winkel.

##### Parameters {#parameters-removereference}

* **`key`:** De belangrijkste verwijzing om te verwijderen. Deze parameter komt overeen met `key` parameter van de `addReference` functie.

##### Retourneert {#returns-removereference}

A `boolean` waarde:

* Een waarde van `true` Geeft aan dat de verwijzing is verwijderd.
* Een waarde van `false` geeft aan dat de sleutel niet geldig was en dat de winkel ongewijzigd is.

#### reset(keepRestatingData) {#reset-keepremainingdata}

Herstelt de aanvankelijke waarden van de blijvende gegevens van de opslag. U kunt desgewenst alle andere gegevens uit de winkel verwijderen. De gebeurtenis wordt gepauzeerd voor deze opslag terwijl de opslag wordt teruggesteld. Deze functie retourneert geen waarde.

De beginwaarden worden vermeld in het gedeelte `initialValues` bezit van het config voorwerp dat wordt gebruikt om het opslagvoorwerp te concretiseren.

##### Parameters {#parameters-reset}

* **`keepRemainingData`**: (Boolean) Bij de waarde true blijven niet-initiële gegevens behouden. Bij de waarde false worden alle gegevens verwijderd, behalve de beginwaarden.

#### resolveReference(key, retry) {#resolvereference-key-retry}

Hiermee wordt een toets waarnaar wordt verwezen, opgehaald. U kunt desgewenst het aantal herhalingen opgeven dat moet worden gebruikt om de beste overeenkomst op te lossen.

##### Parameters {#parameters-resolvereference}

* **`key`:** (String) De sleutel waarvoor de verwijzing moet worden opgelost. Dit `key` parameter komt overeen met `key` parameter van de `addReference` functie.
* **`retry`:** (Number) Het aantal herhalingen dat moet worden gebruikt.

##### Retourneert {#returns-resolvereference}

A `string` waarde die de referenced sleutel vertegenwoordigt. Als er geen verwijzing wordt gevonden, wordt de waarde van de optie `key` parameter wordt geretourneerd.

#### resumeEvent() {#resumeeventing}

Hervat de gebeurtenis voor deze opslag zodat de gebeurtenissen worden teweeggebracht. Deze functie definieert geen parameters en retourneert geen waarde.

#### setItem(key, value, options) {#setitem-key-value-options}

Voegt een sleutel/waardepaar aan de opslag toe.

Hiermee wordt het dialoogvenster `data` alleen als de waarde voor de toets anders is dan de waarde die momenteel voor de toets is opgeslagen. U kunt desgewenst voorkomen dat het `data` gebeurtenis.

De gebeurtenisgegevens omvatten de opslagnaam, de sleutel, de vorige waarde, de nieuwe waarde en het actietype van `set`.

##### Parameters {#parameters-setitem}

* **`key`:** (String) De naam van de toets.
* **`options`:** (Object) Een object met opties. De volgende objecteigenschappen zijn geldig:
   * `silent`: Een waarde van `true` voorkomt dat de `data` gebeurtenis. De standaardwaarde is `false`.
* **`value`:** (Object) De waarde die aan de sleutel moet worden gekoppeld.

##### Retourneert {#returns-setitem}

A `boolean` waarde:

* Een waarde van `true` Hiermee wordt aangegeven dat het gegevensobject is opgeslagen.
* Een waarde van `false` Hiermee wordt aangegeven dat de gegevensopslag ongewijzigd blijft.

## ContextHub.Store.JSONPStore {#contexthub-store-jsonpstore}

Een opslag die JSON-gegevens bevat. De gegevens worden teruggewonnen van de externe dienst JSONP, of naar keuze van de dienst die JSON- gegevens terugkeert. Geef de servicedetails op met de [`init`](#init-name-config) wanneer u een instantie van deze klasse maakt.

De opslag gebruikt in-geheugenpersistentie (variabele Javascript). De gegevens van de opslag zijn beschikbaar slechts tijdens het leven van de pagina.

ContextHub.Store.JSONPStore extends [ContextHub.Store.Core](#contexthub-store-core) en neemt de functies van die klasse over.

### Functies (ContextHub.Store.JSONPStore) {#functions-contexthub-store-jsonpstore}

#### configureService(serviceConfig, override) {#configureservice-serviceconfig-override}

Vormt de details voor het verbinden met de dienst JSONP die dit voorwerp gebruikt. U kunt de bestaande configuratie bijwerken of vervangen. De functie retourneert geen waarde.

##### Parameters {#parameters-configureservice}

* **`serviceConfig`:** Een object dat de volgende eigenschappen bevat:
   * `host`: (Tekenreeks) De servernaam of het IP-adres.
   * `jsonp`: (Boolean) De waarde true geeft aan dat de service een JSONP-service is, anders false. Indien waar (true), wordt de callback: &quot;ContextHub.Callbacks.*Object.name*}-object wordt toegevoegd aan het object service.params.
   * `params`: (Object) URL-parameters vertegenwoordigd als objecteigenschappen. Parameternamen zijn eigenschapnamen en parameterwaarden zijn eigenschapswaarden.
   * `path`: (Tekenreeks) Het pad naar de service.
   * `port`: (Aantal) het havenaantal van de dienst.
   * `secure`: (String of Boolean) Bepaalt het protocol dat voor de service-URL moet worden gebruikt:
      * `auto`: //
      * `true`: https://
      * `false`: http://
* **overschrijven:** (Booleaans). Een waarde van `true` veroorzaakt de bestaande de dienstconfiguratie om door de eigenschappen van te worden vervangen `serviceConfig`. Een waarde van `false` veroorzaakt de bestaande eigenschappen van de de dienstconfiguratie om met de eigenschappen van worden samengevoegd: `serviceConfig`.

#### getRawResponse() {#getrawresponse}

Keert de ruwe reactie terug die sinds de laatste vraag aan de dienst JSONP in het voorgeheugen ondergebracht is. De functie vereist geen parameters.

##### Retourneert {#returns-getrawresponse}

Een object dat de onbewerkte reactie vertegenwoordigt.

#### getServiceDetails() {#getservicedetails}

Hiermee wordt het serviceobject voor dit ContextHub.Store.JSONPStore-object opgehaald. Het serviceobject bevat alle informatie die nodig is om de service-URL te maken.

##### Retourneert {#returns-getservicedetails}

Een object met de volgende eigenschappen:

* **`host`:** (Tekenreeks) De servernaam of het IP-adres.
* **`jsonp`:** (Boolean) De waarde true geeft aan dat de service een JSONP-service is, anders false. Indien waar (true), wordt de callback: &quot;ContextHub.Callbacks.*Object.name*}-object wordt toegevoegd aan het object service.params.
* **`params`:** (Object) URL-parameters vertegenwoordigd als objecteigenschappen. Parameternamen zijn eigenschapnamen en parameterwaarden zijn eigenschapswaarden.
* **`path`:** (Tekenreeks) Het pad naar de service.
* **`port`:** (Aantal) het havenaantal van de dienst.
* **`secure`:** (String of Boolean) Bepaalt het protocol dat voor de service-URL moet worden gebruikt:
   * `auto`: //
   * `true`: https://
   * `false`: http://

#### getServiceURL(resolve) {#getserviceurl-resolve}

Haalt URL van de dienst JSONP op.

##### Parameters {#parameters-getserviceurl}

* **`resolve`:** (Boolean) Hiermee wordt bepaald of omgezette parameters in de URL moeten worden opgenomen. Een waarde van `true` stelt parameters op, en `false` niet.

##### Retourneert {#returns-getserviceurl}

A `string` waarde die de service-URL vertegenwoordigt.

#### init(name, config) {#init-name-config-1}

initialiseert de `ContextHub.Store.JSONPStore` object.

##### Parameters {#parameters-init-1}

* **`name`:** (Tekenreeks) De naam van de winkel.
* **`config`:** (Object) Een object dat de eigenschap service bevat. Het JSONPStore-object gebruikt de eigenschappen van de `service` object voor het samenstellen van de URL van de JSONP-service:
   * `eventDeferring`: 32.
   * `eventing`: Het object ContextHub.Utils.Event voor deze winkel. De standaardwaarde is `ContextHub.eventing` object.
   * `persistence`: Het object ContextHub.Utils.Persistence voor deze winkel. Standaard wordt geheugenpersistentie gebruikt (Javascript-object).
   * `service`: (Object)
      * `host`: (Tekenreeks) De servernaam of het IP-adres.
      * `jsonp`: (Boolean) De waarde true geeft aan dat de service een JSONP-service is, anders false. Indien waar (true), wordt `{callback: "ContextHub.Callbacks.*Object.name*}`object wordt toegevoegd aan `service.params`.
      * `params`: (Object) URL-parameters vertegenwoordigd als objecteigenschappen. Parameternamen en -waarden zijn respectievelijk namen en waarden van objecteigenschappen.
      * `path`: (Tekenreeks) Het pad naar de service.
      * `port`: (Aantal) het havenaantal van de dienst.
      * `secure`: (String of Boolean) Bepaalt het protocol dat voor de service-URL moet worden gebruikt:
         * `auto`: //
         * `true`: https://
         * `false`: http://
      * `timeout`: (Aantal) de hoeveelheid tijd op de dienst JSONP te wachten om vóór timing uit, in milliseconden te antwoorden.
         * `ttl`: De minimumhoeveelheid tijd in milliseconden die tussen vraag tot de dienst JSONP overgaat. (Zie de [queryService](#queryservice-reload) functie).

#### queryService(reload) {#queryservice-reload}

Zoekt de verre dienst JSONP en caches de reactie. Als de hoeveelheid tijd sinds de vorige aanroep van deze functie kleiner is dan de waarde van `config.service.ttl`, wordt de dienst niet geroepen en de caching reactie wordt niet veranderd. Naar keuze, kunt u de dienst dwingen om worden geroepen. De `config.service.ttl`eigenschap wordt ingesteld wanneer het aanroepen van de [init](#init-name-config) om de winkel te initialiseren.

De gebeurtenis ready wordt geactiveerd wanneer de query is voltooid. Wanneer de URL van de JSONP-service niet is ingesteld, doet de functie niets.

##### Parameters {#parameters-queryservice}

* **`reload`:** (Boolean) De waarde true verwijdert de reactie in de cache en dwingt de JSONP-service aan te roepen.

#### reset {#reset}

Herstelt de aanvankelijke waarden van de opslag persisted gegevens en roept dan de dienst JSONP. U kunt desgewenst alle andere gegevens uit de winkel verwijderen. De gebeurtenis wordt gepauzeerd voor deze opslag terwijl de aanvankelijke waarden worden teruggesteld. Deze functie retourneert geen waarde.

De aanvankelijke waarden worden verstrekt in het initialValues bezit van het config voorwerp dat wordt gebruikt om het archiefvoorwerp te concretiseren.

##### Parameters {#parameters-reset-1}

* **`keepRemainingData`:** (Boolean) Bij de waarde true blijven niet-initiële gegevens behouden. Bij de waarde false worden alle gegevens verwijderd, behalve de beginwaarden.

#### resolveParameter(f) {#resolveparameter-f}

Hiermee wordt de opgegeven parameter omgezet.

## ContextHub.Store.PersistedJSONPStore {#contexthub-store-persistedjsonpstore}

`ContextHub.Store.PersistedJSONPStore` extends [ContextHub.Store.JSONPStore](#contexthub-store-jsonpstore) dus neemt het alle functies van die klasse over. Nochtans, worden de gegevens die van de dienst JSONP worden teruggewonnen voortgeduurd volgens de configuratie van persistentie ContextHub. (Zie [Persistentiemodi:](adding-contexthub.md#persistence-modes))

## ContextHub.Store.PersistedStore {#contexthub-store-persistedstore}

`ContextHub.Store.PersistedStore` extends [ContextHub.Store.Core](#contexthub-store-core) dus neemt het alle functies van die klasse over. De gegevens in deze opslag worden voortgeduurd volgens de configuratie van persistentie ContextHub.

## ContextHub.Store.SessionStore {#contexthub-store-sessionstore}

`ContextHub.Store.SessionStore` extends [ContextHub.Store.Core](#contexthub-store-core) dus neemt het alle functies van die klasse over. De gegevens in deze opslag blijven behouden met in-memory persistance (Javascript-object).

## ContextHub.UI {#contexthub-ui}

Beheert UI-modules en UI-moduleurs.

### Functies (ContextHub.UI) {#functions-contexthub-ui}

#### registerRenderer(moduleType, renderer, dontRender) {#registerrenderer-moduletype-renderer-dontrender}

Registreert een UI modulerenderer met ContextHub. Nadat de renderer is geregistreerd, kan deze worden gebruikt om [UI-modules maken](configuring-contexthub.md#adding-a-ui-module). Gebruik deze functie wanneer u [verlenging `ContextHub.UI.BaseModuleRenderer`](extending-contexthub.md#creating-contexthub-ui-module-types) om een aangepaste UI Module-renderer te maken.

##### Parameters {#parameters-registerrenderer}

* **`moduleType`:** (Tekenreeks) De id voor de renderer van de module UI. Als een renderer al is geregistreerd met de opgegeven waarde, is de bestaande renderer niet geregistreerd voordat deze renderer is geregistreerd.
* **`renderer`:** (String) De naam van de klasse die de module UI rendert.
* **`dontRender`:** (Boolean) Ingesteld op `true` om ContextHub UI te verhinderen worden teruggegeven nadat renderer wordt geregistreerd. De standaardwaarde is `false`.

##### Voorbeeld {#example-registerrenderer}

In het volgende voorbeeld wordt een renderer geregistreerd als de `contexthub.browserinfo` moduletype.

```javascript
ContextHub.UI.registerRenderer('contexthub.browserinfo', new SurferinfoRenderer());
```

## ContextHub.Utils.Cookie {#contexthub-utils-cookie}

Een hulpprogrammaklasse voor interactie met cookies.

### Functies (ContextHub.Utils.Cookie) {#functions-contexthub-utils-cookie}

#### exists(key) {#exists-key}

Hiermee wordt bepaald of een cookie bestaat.

##### Parameters {#parameters-exists}

* **`key`:** A `String` die de sleutel bevat van het cookie waarvoor u test.

##### Retourneert {#returns-exists}

A `boolean` De waarde true geeft aan dat het cookie bestaat.

##### Voorbeeld {#example-exists}

```javascript
if (ContextHub.Utils.Cookie.exists("name")) {
   // conditionally-executed code
}
```

#### getAllItems(filter) {#getallitems-filter}

Retourneert alle cookies met sleutels die overeenkomen met een filter.

##### Parameters {#parameters-getallitems}

* **`filter`:** (Optioneel) Criteria voor het afstemmen van cookies. Geef geen waarde op om alle cookies te retourneren. De volgende typen worden ondersteund:
   * Tekenreeks: De tekenreeks wordt vergeleken met de cookie-toets.
   * Array: Elk item in de array is een filter.
   * Een RegExp-object: De testfunctie van het object wordt gebruikt om cookies aan te passen.
   * Een functie: Een functie die een koekjessleutel voor een gelijke test. De functie moet de koekjessleutel als parameter nemen en waar terugkeren als de test een gelijke bevestigt.

##### Retourneert {#returns-getallitems}

Een object van cookies. Objecteigenschappen zijn cookie sleutels en sleutelwaarden zijn cookie waarden.

##### Voorbeeld {#example-getallitems}

```javascript
ContextHub.Utils.Cookie.getAllItems([/^cq-authoring/, /^cq-editor/])
```

#### getItem(key) {#getitem-key-1}

Retourneert een cookiewaarde.

##### Parameters {#parameters-getitem-1}

* **`key`:** De sleutel van het koekje waarvoor u de waarde wilt.

##### Retourneert {#returns-getitem-1}

De waarde van het cookie, of `null` als er geen cookie is gevonden voor de toets.

##### Voorbeeld {#example-getitem-1}

```javascript
ContextHub.Utils.Cookie.getItem("name");
```

#### getKeys (filter) {#getkeys-filter}

Retourneert een array met de sleutels van bestaande cookies die overeenkomen met een filter.

##### Parameters {#parameters-getkeys-1}

* **`filter`:** Criteria voor het afstemmen van cookies. De volgende typen worden ondersteund:
   * Tekenreeks: De tekenreeks wordt vergeleken met de cookie-toets.
   * Array: Elk item in de array is een filter.
   * Een RegExp-object: De testfunctie van het object wordt gebruikt om cookies aan te passen.
   * Een functie: Een functie die een koekjessleutel voor een gelijke test. De functie moet de cookiesleutel als parameter nemen en terugkeren `true` als de test een gelijke bevestigt.

##### Retourneert {#returns-getkeys-1}

Een array van tekenreeksen waarbij elke tekenreeks de sleutel is van een cookie die overeenkomt met het filter.

##### Voorbeeld {#example-getkeys-1}

```javascript
ContextHub.Utils.Cookie.getKeys([/^cq-authoring/, /^cq-editor/])
```

#### removeItem(sleutel, opties) {#removeitem-key-options-1}

Hiermee verwijdert u een cookie. Als u het cookie wilt verwijderen, wordt de waarde ingesteld op een lege tekenreeks en wordt de vervaldatum ingesteld op de dag vóór de huidige datum.

##### Parameters {#parameters-removeitem-1}

* **`key`:** A `String` waarde die staat voor de sleutel van het cookie dat moet worden verwijderd.
* **`options`:** Een object dat eigenschapwaarden bevat voor het configureren van de cookie-kenmerken. Zie de [`setItem`](#setitem-key-value-options) functie voor informatie. De `expires` eigenschap heeft geen effect.

##### Retourneert {#returns-removeitem-1}

Deze functie retourneert geen waarde.

##### Voorbeeld {#example-removeitem-1}

```javascript
ContextHub.Utils.Cookie.vanish([/^cq-authoring/, 'cq-scrollpos']);
```

#### setItem(key, value, options) {#setitem-key-value-options-1}

Hiermee maakt u een cookie van de opgegeven sleutel en waarde en voegt u het cookie toe aan het huidige document. U kunt desgewenst opties opgeven waarmee de kenmerken van het cookie worden geconfigureerd.

##### Parameters {#parameters-setitem-1}

* **`key`:** Een tekenreeks die de sleutel van het cookie bevat.
* **`value`:** Een tekenreeks die de cookiewaarde bevat.
* **`options`:** (Optioneel) Een object dat een van de volgende eigenschappen bevat waarmee de cookie-kenmerken worden geconfigureerd:
   * `expires`: A `date` of `number` waarde die aangeeft wanneer het cookie vervalt. Een datumwaarde geeft de absolute vervaltijd aan. Een getal (in dagen) stelt de vervaltijd in op de huidige tijd plus het getal. De standaardwaarde is `undefined`.
   * `secure`: A `boolean` waarde die de `Secure` kenmerk van de cookie. De standaardwaarde is `false`.
   * `path`: A `String` te gebruiken waarde als de `Path` kenmerk van de cookie. De standaardwaarde is `undefined`.

##### Retourneert {#returns-setitem-1}

Het cookie met de ingestelde waarde.

##### Voorbeeld {#example-setitem-1}

```javascript
ContextHub.Utils.Cookie.setItem("name", "mycookie", {
    expires: 3,
    domain: 'localhost',
    path: '/some/directory',
    secure: true
});
```

#### verdwijnt(filter, opties) {#vanish-filter-options}

Hiermee verwijdert u alle cookies die overeenkomen met een opgegeven filter. Cookies komen overeen met `getKeys` functie en verwijderd met behulp van de `removeItem` functie.

##### Parameters {#parameters-vanish}

* **`filter`:** De `filter` in de oproep tot [`getKeys`](#getkeys-filter) functie.
* **`options`:** De `options` in de oproep tot [`removeItem`](#removeitem-key-options) functie.

##### Retourneert {#returns-vanish}

Deze functie retourneert geen waarde.

## ContextHub.Utils.Eventing {#contexthub-utils-eventing}

Laat u toe om functies aan ContextHub archiefgebeurtenissen te binden en los te maken. Toegang `ContextHub.Utils.Eventing` objecten voor een winkel die de [voorkomen](#eventing) eigenschap van de winkel.

### Functies (ContextHub.Utils.Event) {#functions-contexthub-utils-eventing}

#### off (naam, kiezer) {#off-name-selector}

Hiermee wordt de binding van een functie met een gebeurtenis opgeheven.

##### Parameters {#parameters-off}

* **`name`:** De [naam van de gebeurtenis](#contexthub-utils-eventing) waarvoor u de binding van de functie ongedaan maakt.
* **`selector`:** De kiezer die de binding aangeeft. (Zie de `selector` parameter voor de [`on`](#on-name-handler-selector-triggerforpastevents) en [`once`](#once-name-handler-selector-triggerforpastevents) functies).

##### Retourneert {#returns-off}

Deze functie retourneert geen waarde.

#### on(naam, handler, kiezer, triggerForPastEvents) {#on-name-handler-selector-triggerforpastevents}

Bindt een functie aan een gebeurtenis. De functie wordt aangeroepen telkens wanneer de gebeurtenis plaatsvindt. De functie kan optioneel worden aangeroepen voor gebeurtenissen die zich in het verleden hebben voorgedaan, voordat de binding wordt ingesteld.

##### Parameters {#parameters-on}

* **`name`:** (String) De [naam van de gebeurtenis](#contexthub-utils-eventing) waaraan u de functie bindt.
* **`handler`:** (Functie) De functie die aan de gebeurtenis wordt gebonden.
* **`selector`:** (Tekenreeks) Een unieke id voor de binding. U hebt de kiezer nodig om de binding te identificeren als u de `off` functie om de binding te verwijderen.
* **`triggerForPastEvents`:** (Boolean) Geeft aan of de handler moet worden uitgevoerd voor gebeurtenissen die zich in het verleden hebben voorgedaan. Een waarde van `true` roept de manager voor vroegere gebeurtenissen aan. Een waarde van `false` roept de manager voor toekomstige gebeurtenissen aan. De standaardwaarde is `true`.

##### Retourneert {#returns-on}

Wanneer de `triggerForPastEvents` argument is `true`Deze functie retourneert een `boolean` waarde die aangeeft of de gebeurtenis in het verleden heeft plaatsgevonden:

* `true`: De gebeurtenis vond in het verleden plaats en de manager wordt geroepen.
* `false`: De gebeurtenis heeft zich in het verleden niet voorgedaan.

Indien `triggerForPastEvents` is `false`, retourneert deze functie geen waarde.

##### Voorbeeld {#example-on}

In het volgende voorbeeld wordt een functie gebonden aan de gebeurtenis data van de geolocation store. De functie vult een element op de pagina met de waarde voor het latitude-gegevensitem uit de winkel.

```html
<div class="location">
    <p>latitude: <span id="lat"></span></p>
</div>

<script>
    var geostore = ContextHub.getStore("geolocation");
    geostore.eventing.on(ContextHub.Constants.EVENT_DATA_UPDATE,getlat,"getlat");

    function getlat(){
       latitude = geostore.getItem("latitude");
       $("#lat").html(latitude);
    }
</script>
```

#### once(naam, handler, kiezer, triggerForPastEvents) {#once-name-handler-selector-triggerforpastevents}

Bindt een functie aan een gebeurtenis. De functie wordt slechts eenmaal aangeroepen voor het eerste exemplaar van de gebeurtenis. De functie kan optioneel worden aangeroepen voor de gebeurtenis die in het verleden heeft plaatsgevonden, voordat de binding wordt ingesteld.

##### Parameters {#parameters-once}

* **`name`:** (String) De [naam van de gebeurtenis](#contexthub-utils-eventing) waaraan u de functie bindt.
* **`handler`:** (Functie) De functie die aan de gebeurtenis wordt gebonden.
* **`selector`:** (Tekenreeks) Een unieke id voor de binding. U hebt de kiezer nodig om de binding te identificeren als u de `off` functie om de binding te verwijderen.
* **`triggerForPastEvents`:** (Boolean) Geeft aan of de handler moet worden uitgevoerd voor gebeurtenissen die zich in het verleden hebben voorgedaan. Een waarde van `true` roept de manager voor vroegere gebeurtenissen aan. Een waarde van `false` roept de manager voor toekomstige gebeurtenissen aan. De standaardwaarde is `true`.

##### Retourneert {#returns-once}

Wanneer de `triggerForPastEvents` argument is `true`Deze functie retourneert een `boolean` waarde die aangeeft of de gebeurtenis in het verleden heeft plaatsgevonden:

* `true`: De gebeurtenis vond in het verleden plaats en de manager wordt geroepen.
* `false`: De gebeurtenis heeft zich in het verleden niet voorgedaan.

Indien `triggerForPastEvents` is `false`, retourneert deze functie geen waarde.

## ContextHub.Utils.inheritance {#contexthub-utils-inheritance}

Een hulpprogrammaklasse waarmee een object de eigenschappen en methoden van een ander object kan overnemen.

### Functies (ContextHub.Utils.inheritance) {#functions-contexthub-utils-inheritance}

#### inherit (child, parent) {#inherit-child-parent}

Causes an object to inherit the properties and methods of another object.

##### Parameters {#parameters-inherit}

* **`child`:** (Object) Het object dat overerft.
* **`parent`:** (Object) Het object dat de eigenschappen en methoden definieert die worden overgeërfd.

## ContextHub.Utils.JSON {#contexthub-utils-json}

Biedt functies voor het serialiseren van objecten in JSON-indeling en het deserialiseren van JSON-tekenreeksen in objecten.

### Functies (ContextHub.Utils.JSON) {#functions-contexthub-utils-json}

#### parse(data) {#parse-data}

Parseert een tekenreekswaarde als JSON en zet deze om in een javascript-object.

##### Parameters {#parameters-parse}

* **`data`:** Een tekenreekswaarde in JSON-indeling.

##### Retourneert {#returns-parse}

Een JavaScript-object.

##### Voorbeeld {#example-parse}

De code:

```javascript
ContextHub.Utils.JSON.parse("{'city':'Basel','country':'Switzerland','population':'173330'}");
```

Retourneert het volgende object:

```javascript
Object {
   city: "Basel",
   country: "Switzerland",
   population: 173330
}
```

#### stringify(data) {#stringify-data}

Serializes Javascript-waarden en -objecten in tekenreekswaarden in de JSON-indeling.

##### Parameters {#parameters-stringify}

* **`data`:** De waarde of het object waarop serienummering moet worden toegepast. Deze functie ondersteunt booleaanse waarden, arrays, getallen, tekenreeksen en datumwaarden.

##### Retourneert {#returns-stringify}

De geserialiseerde tekenreekswaarde. Wanneer `data` is een R `egExp` waarde, retourneert deze functie een leeg object. Wanneer `data` is een functie, retourneert `undefined`.

##### Voorbeeld {#example-stringify}

De volgende code:

```javascript
ContextHub.Utils.JSON.stringify({
   city: "Basel",
   country: "Switzerland",
   population: 173330
});
```

Retourneert:

```javascript
"{'city':'Basel','country':'Switzerland','population':'173330'}":
```

## ContextHub.Utils.JSON.tree {#contexthub-utils-json-tree}

Deze klasse vergemakkelijkt de manipulatie van gegevensvoorwerpen die moeten worden opgeslagen of van opslag ContextHub worden teruggewonnen.

### Functies (ContextHub.Utils.JSON.tree) {#functions-contexthub-utils-json-tree}

#### addAllItems() {#addallitems}

Maakt een kopie van een gegevensobject en voegt er vanuit een tweede object de gegevensstructuur aan toe. De functie retourneert de kopie en wijzigt geen van de oorspronkelijke objecten. Wanneer de gegevensstructuren van de twee objecten identieke sleutels bevatten, overschrijft de waarde van het tweede object de waarde van het eerste object.

##### Parameters {#parameters-addallitems-1}

* **`tree`:** Het object dat wordt gekopieerd.
* **`secondTree`:** Het object dat wordt samengevoegd met de kopie van het dialoogvenster `tree` object.

##### Retourneert {#returns-addallitems-1}

Een object dat de samengevoegde gegevens bevat.

#### Cleup() {#cleanup}

Maakt een kopie van een object, zoekt en verwijdert items in de gegevensstructuur die geen waarden, null-waarden of ongedefinieerde waarden bevatten en retourneert de kopie.

##### Parameters {#parameters-cleanup}

* **`tree`:** Het object dat moet worden gewist.

##### Retourneert {#returns-cleanup}

Een kopie van de boom die is schoongemaakt.

#### getItem() {#getitem}

Hiermee wordt de waarde opgehaald van een object voor de toets A.

##### Parameters {#parameters-getitem-2}

* **`tree`:** Het gegevensobject.
* **`key`:** De sleutel voor de waarde die u wilt terugwinnen.

##### Retourneert {#returns-getitem-2}

De waarde die overeenkomt met de toets. Wanneer de toets onderliggende toetsen heeft, retourneert deze functie een complex object. Wanneer het type van de waarde voor de toets `undefined`, `null` wordt geretourneerd.

##### Voorbeeld {#example-getitem-2}

Bekijk het volgende JavaScript-object:

```javascript
myObject {
  user: {
    location: {
      city: "Basel",
        details: {
          population: 173330,
          elevation: 260
        }
      }
    }
  }
```

De volgende voorbeeldcode retourneert de waarde `260`:

```javascript
ContextHub.Utils.JSON.tree.getItem(myObject, "/user/location/details/elevation");
```

De volgende voorbeeldcode wint de waarde voor een sleutel terug die kindsleutels heeft:

```javascript
ContextHub.Utils.JSON.tree.getItem(myObject, "/user");
```

De functie retourneert het volgende object:

```javascript
Object {
  location: {
    city: "Basel",
    details: {
      population: 173330,
      elevation: 260
    }
  }
}
```

#### getKeys() {#getkeys}

Hiermee worden alle sleutels opgehaald uit de gegevensstructuur van een object. U kunt desgewenst alleen de toetsen van de onderliggende toetsen van een specifieke toets ophalen. U kunt desgewenst ook een sorteervolgorde van de opgehaalde toetsen opgeven.

##### Parameters {#parameters-getkeys-2}

* **`tree`:** Het object waarvan de sleutels van de gegevensstructuur moeten worden opgehaald.
* **`parent`:** (Optioneel) De sleutel van een item in de gegevensstructuur waarvoor u de sleutels van de onderliggende items wilt ophalen.
* **`order`:** (Optioneel) Een functie die de sorteervolgorde van de geretourneerde toetsen bepaalt. (Zie [`Array.prototype.sort`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) op het Mozilla Developer Network.)

##### Retourneert {#returns-getkeys-2}

Een array met sleutels.

##### Voorbeeld {#example-getkeys-2}

Bekijk het volgende object:

```javascript
myObject {
  location: {
    weather: {
      temperature: "28C",
      humidity: "77%",
      precipitation: "10%",
      wind: "8km/h"
    },
    city: "Basel",
    country: "Switzerland",
    longitude: 7.5925727,
    latitude: 47.557421
  }
}
```

De `ContextHub.Utils.JSON.tree.getKeys(myObject);` script retourneert de volgende array:

```javascript
["/location", "/location/city", "/location/country", "/location/latitude", "/location/longitude", "/location/weather", "/location/weather/humidity", "/location/weather/precipitation", "/location/weather/temperature", "/location/weather/wind"]
```

#### removeItem() {#removeitem}

Maakt een kopie van een bepaald object, verwijdert de opgegeven vertakking uit de gegevensstructuur en retourneert de gewijzigde kopie.

##### Parameters {#parameters-removeitem-2}

* **`tree`:** Een gegevensobject.
* **`key`:** De toets die moet worden verwijderd.

##### Retourneert {#returns-removeitem-2}

Een kopie van het oorspronkelijke gegevensobject waarbij de toets is verwijderd.

##### Voorbeeld {#example-removeitem-2}

Bekijk het volgende object:

```javascript
myObject {
  one: {
    foo: "bar",
    two: {
      three: {
        four: {
          five: 5,
          six: 6
        }
      }
    }
  }
}
```

Het volgende voorbeeldmanuscript verwijdert /one/two/three/four tak uit de gegevensboom:

```javascript
myObject = ContextHub.Utils.JSON.tree.removeItem(myObject, "/one/two/three/four");
```

De functie retourneert het volgende object:

```javascript
myObject {
  one: {
    foo: "bar"
  }
}
```

#### sanitizeKey(key) {#sanitizekey-key}

Hiermee worden tekenreekswaarden gesimuleerd zodat deze als toetsen kunnen worden gebruikt. Om een tekenreeks te ontsmetten, voert deze functie de volgende handelingen uit:

* Hiermee worden meerdere opeenvolgende slashes tot één schuine streep verkleind.
* Verwijdert witruimte aan het begin en einde van de tekenreeks.
* Splitst het resultaat in een array van tekenreeksen die worden afgebakend door slashes.

Gebruik de resulterende array om een bruikbare sleutel te maken.

##### Parameters {#parameters-sanitizekey}

* **`key`:** De `string` om te ontsmetten.

##### Retourneert {#returns-sanitizekey}

Een array van `string` waarden waarbij elke tekenreeks het deel van de `key` dat werd afgebakend door slashes . vertegenwoordigt de geanimeerde sleutel. Als de geanimeerde array een lengte van nul heeft, retourneert deze functie `null`.

##### Voorbeeld {#example-sanitizekey}

Met de volgende code wordt een tekenreeks gesimuleerd om de array te produceren `["this", "is", "a", "path"]`en genereert vervolgens de toets `"/this/is/a/path"` uit de array:

```javascript
var key = " / this////is/a/path ";
ContextHub.Utils.JSON.tree.sanitizeKey(key)
"/" + ContextHub.Utils.JSON.tree.sanitizeKey(key).join("/");
```

#### setItem(tree, key, value) {#setitem-tree-key-value}

Hiermee voegt u een sleutel-/waardepaar toe aan de gegevensstructuur van een kopie van een object. Voor informatie over gegevensbomen raadpleegt u [Persistentie.](contexthub.md#persistence)

##### Parameters {#parameters-setitem-2}

* **`tree`:** Een gegevensobject.
* **`key`:** De sleutel die moet worden gekoppeld aan de waarde die u toevoegt. De sleutel is het pad naar het item in de gegevensstructuur. Deze functie roept `ContextHub.Utils.JSON.tree.sanitize` om de toets te ontsmetten voordat u deze toevoegt.
* **`value`:** De waarde die aan de gegevensstructuur moet worden toegevoegd.

##### Retourneert {#returns-setitem-2}

Een kopie van de `tree` object dat het `key`/ `value` paar.

##### Voorbeeld {#example-setitem-2}

Overweeg de volgende Javascript-code:

```javascript
var myObject = {
     user: {
        location: {
           city: "Basel"
           }
        }
     };

var myKey = "/user/location/details";

var myValue = {
      population: 173330,
      elevation: 260
     };

myObject = ContextHub.Utils.JSON.tree.setItem(myObject, myKey, myValue);
```

## ContextHub.Utils.storeCandidates {#contexthub-utils-storecandidates}

Hiermee kunt u winkelkandidaten registreren en geregistreerde winkelkandidaten aanvragen.

### Functies (ContextHub.Utils.storeCandidates) {#functions-contexthub-utils-storecandidates}

#### getRegisteredCandidates(storeType) {#getregisteredcandidates-storetype}

Retourneert de winkeltypen die zijn geregistreerd als opslagkandidaten. Of wint de geregistreerde kandidaten van een specifiek archieftype of van alle archieftypes terug.

##### Parameters {#parameters-getregisteredcandidates}

* **`storeType`:** (String) De naam van het winkeltype. Zie de `storeType` parameter van de [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#contexthub-utils-storecandidates) functie.

##### Retourneert {#returns-getregisteredcandidates}

Een object van winkeltypen. De objecteigenschappen zijn de namen van opslagtypen en de eigenschapswaarden zijn een array van geregistreerde opslagkandidaten.

#### getStoreFromCandidates(storeType) {#getstorefromcandidates-storetype}

Retourneert een winkeltype van de geregistreerde kandidaten. Als meer dan één opslagtype van de zelfde naam wordt geregistreerd, keert de functie het archieftype met de hoogste prioriteit terug.

##### Parameters {#parameters-getstorefromcandidates}

* `storeType`: (String) De naam van de opslagkandidaat. Zie de `storeType` parameter van de [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#registerstorecandidate-store-storetype-priority-applies) functie.

##### Retourneert {#returns-getstorefromcandidates}

Een object dat de geregistreerde opslagkandidaat vertegenwoordigt. Als het gewenste opslagtype niet is geregistreerd, wordt een fout gegenereerd.

#### getSupportedStoreTypes() {#getsupportedstoretypes}

Retourneert de namen van de winkeltypen die als opslagkandidaten zijn geregistreerd. Deze functie vereist geen parameters.

##### Retourneert {#returns-getsupportedstoretypes}

Een array van tekenreekswaarden, waarbij elke tekenreeks het opslagtype is waarmee een opslagkandidaat is geregistreerd. Zie de `storeType` parameter van de [`ContextHub.Utils.storeCandidates.registerStoreCandidate`](#contexthub-utils-storecandidates) functie.

#### registerStoreCandidate(store, storeType, priority, apply) {#registerstorecandidate-store-storetype-priority-applies}

Registreert een opslagvoorwerp als opslagkandidaat gebruikend een naam en een prioriteit.

De prioriteit is een aantal dat op het belang van de zelfde-genoemde opslag wijst. Wanneer een opslagkandidaat met dezelfde naam als een reeds geregistreerde opslagkandidaat wordt geregistreerd, wordt de kandidaat met de hogere prioriteit gebruikt. Wanneer het registreren van een opslagkandidaat, wordt de opslag geregistreerd slechts als de prioriteit hoger is dan de zelfde-genoemde geregistreerde opslagkandidaten.

##### Parameters {#parameters-registerstorecandidate}

* **`store`:** (Object) Het opslagobject dat moet worden geregistreerd als opslagkandidaat.
* **`storeType`:** (String) De naam van de opslagkandidaat. Deze waarde wordt vereist wanneer het creëren van een geval van de opslagkandidaat.
* **`priority`:** (Aantal) De prioriteit van de opslagkandidaat.
* **`applies`:** (Functie) De functie die moet worden aangeroepen die de toepasselijkheid van de opslag in de huidige omgeving evalueert. De functie moet worden geretourneerd `true` indien de opslagplaats van toepassing is, en `false` anders. De standaardwaarde is een functie die waar retourneert: `function() {return true;}`

##### Voorbeeld {#example-registerstorecandidate}

```javascript
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandiate', 0);
```
