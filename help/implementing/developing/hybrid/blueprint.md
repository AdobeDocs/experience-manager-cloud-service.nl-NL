---
title: SPA-blauwdruk
description: Dit document beschrijft het algemene, kader-onafhankelijke contract dat om het even welk kader van het KUUROORD zou moeten vervullen zodat kunt u editable componenten van het KUUROORD binnen AEM uitvoeren.
exl-id: 9d47c0e9-600c-4f45-9169-b3c9bbee9152
feature: Developing
role: Admin, Architect, Developer
index: false
source-git-commit: 7a9d947761b0473f5ddac3c4d19dfe5bed5b97fe
workflow-type: tm+mt
source-wordcount: '2022'
ht-degree: 0%

---


# SPA-blauwdruk {#spa-blueprint}

Om de auteur toe te laten om de Redacteur van AEM te gebruiken SPA om de inhoud van een KUUROORD uit te geven, zijn er vereisten die het KUUROORD moet vervullen.

{{ue-over-spa}}

## Inleiding {#introduction}

Dit document beschrijft het algemene contract dat om het even welk kader van het KUUROORD (namelijk het soort de steunlaag van AEM) zou moeten vervullen zodat kunt u editable componenten van het KUUROORD binnen AEM uitvoeren.

Om de auteur in staat te stellen de Redacteur van de Pagina van AEM te gebruiken om de gegevens uit te geven die door een enig kader van de Toepassing van de Pagina worden blootgesteld, moet een project de structuur van het model kunnen interpreteren die de semantische die gegevens vertegenwoordigt voor een toepassing binnen de bewaarplaats van AEM worden opgeslagen. Hiervoor zijn twee raamwerk-agnostische bibliotheken beschikbaar: de `PageModelManager` en de `ComponentMapping` .

>[!NOTE]
>
>De volgende vereisten zijn onafhankelijk van het framework. Als aan deze vereisten wordt voldaan, kan een kader-specifieke laag worden verstrekt die uit modules, componenten, en de diensten wordt samengesteld.
>
>**Deze vereisten worden reeds voldaan aan voor React en het kader van Angular in AEM.** De vereisten in deze blauwdruk zijn alleen relevant als u een ander framework wilt implementeren voor gebruik met AEM.

>[!CAUTION]
>
>Hoewel de mogelijkheden van het KUUROORD van AEM kader-onafhankelijk zijn, momenteel slechts worden het React en kader van Angular gesteund.

## PageModelManager {#pagemodelmanager}

De `PageModelManager` bibliotheek wordt verstrekt als pakket NPM dat door een project van het KUUROORD wordt gebruikt. Het begeleidt SPA en dient als manager van het gegevensmodel.

Namens het KUUROORD, onttrekt het de herwinning en het beheer van de structuur JSON die de daadwerkelijke inhoudsstructuur vertegenwoordigt. Het is ook verantwoordelijk voor het synchroniseren met het KUUROORD om het te laten weten wanneer het zijn componenten moet opnieuw teruggeven.

Zie het NPM-pakket [@adobe/aem-spa-model-manager &#x200B;](https://www.npmjs.com/package/@adobe/aem-spa-model-manager)

Wanneer u `PageModelManager` initialiseert, laadt de bibliotheek eerst het opgegeven hoofdmodel van de app (via parameter, meta-eigenschap of huidige URL). Als in de bibliotheek wordt aangegeven dat het model van de huidige pagina geen deel uitmaakt van het hoofdmodel, wordt het opgehaald en opgenomen als het model van een onderliggende pagina.

![&#x200B; de modelconsolidatie van de Pagina &#x200B;](assets/page-model-consolidation.png)

### ComponentMapping {#componentmapping}

De module `ComponentMapping` wordt verstrekt als pakket NPM aan het front-end project. Het slaat front-end componenten op en verstrekt een manier voor het KUUROORD om front-end componenten aan het middeltypes van AEM in kaart te brengen. Hierdoor wordt een dynamische resolutie van componenten ingeschakeld bij het parseren van het JSON-model van de toepassing.

Elke item in het model bevat een veld `:type` dat een AEM-brontype weergeeft. Als de front-end component is gekoppeld, kan deze zichzelf renderen met behulp van het fragment van het model dat is ontvangen van de onderliggende bibliotheken.

#### Dynamisch model naar componenttoewijzing {#dynamic-model-to-component-mapping}

Voor details over hoe het dynamische model aan componentenafbeelding in JavaScript SPA SDK voor AEM voorkomt zie het artikel [&#x200B; Dynamische Model aan Component Mapping voor SPAs &#x200B;](model-to-component-mapping.md).

### Framework-specifieke laag {#framework-specific-layer}

Voor elk front-end framework moet een derde laag worden geïmplementeerd. Deze derde bibliotheek is verantwoordelijk voor de interactie met de onderliggende bibliotheken en biedt een reeks goed geïntegreerde en gebruiksvriendelijke ingangspunten voor de interactie met het gegevensmodel.

In de rest van dit document worden de vereisten van deze specifieke laag van het intermediaire kader beschreven en wordt ernaar gestreefd onafhankelijk van het framework te zijn. Door de volgende vereisten na te leven, kan een kader-specifieke laag voor de projectcomponenten worden verstrekt om met de onderliggende bibliotheken in wisselwerking te staan die het gegevensmodel leiden.

## Algemene concepten {#general-concepts}

### Paginamodel {#page-model}

De inhoudsstructuur van de pagina wordt opgeslagen in AEM. Het model van de pagina wordt gebruikt om de componenten van het KUUROORD in kaart te brengen en te concretiseren. De ontwikkelaars van het KUUROORD creëren componenten SPA die zij aan de componenten van AEM in kaart brengen. Hiervoor gebruiken ze het brontype (of het pad naar de AEM-component) als een unieke sleutel.

De componenten van het KUUROORD moeten synchroon met het paginamodel zijn en met om het even welke veranderingen in zijn inhoud dienovereenkomstig worden bijgewerkt. Een patroon met behulp van dynamische componenten moet worden gebruikt om direct componenten te instantiëren volgens de opgegeven structuur van het paginamodel.

### Meta-velden {#meta-fields}

Het paginamodel gebruikt de JSON ModelExporter, die zelf op het [&#x200B; Verschuivende Model &#x200B;](https://sling.apache.org/documentation/bundles/models.html) API gebaseerd is. De exporteerbare kiesmodellen geven de volgende lijst met velden weer, zodat de onderliggende bibliotheken het gegevensmodel kunnen interpreteren:

* `:type`: Type van de AEM-bron (standaardwaarde = type resource)
* `:children`: Hierarchische onderliggende elementen van de huidige bron. Onderliggende items maken geen deel uit van de binneninhoud van de huidige bron (vindt u bij items die een pagina vertegenwoordigen)
* `:hierarchyType`: hiërarchisch type van een bron. De `PageModelManager` ondersteunt momenteel het paginatype

* `:items`: onderliggende inhoudsbronnen van de huidige bron (geneste structuur, alleen aanwezig op containers)
* `:itemsOrder`: geordende lijst met de onderliggende items. Het JSON-toewijzingsobject garandeert de volgorde van de velden niet. Door zowel de kaart als de huidige array te hebben, heeft de consument van de API de voordelen van beide structuren
* `:path`: Inhoudspad van een item (aanwezig op items die een pagina vertegenwoordigen)

Zie ook [&#x200B; Begonnen het Worden met de Diensten van de Inhoud van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=nl-NL).

### Framework-Specific Module {#framework-specific-module}

Het scheiden van zorgen helpt de uitvoering van het project te vergemakkelijken. Daarom moet een npm-specifiek pakket worden verstrekt. Dit pakket is verantwoordelijk voor het samenvoegen en blootstellen van de basismodules, de diensten, en de componenten. Deze componenten moeten de logica van het gegevensmodelbeheer inkapselen en toegang tot de gegevens verlenen de component van het project verwacht. De module is ook verantwoordelijk voor het tijdelijk blootstellen van nuttige ingangspunten van de onderliggende bibliotheken.

Om de interoperabiliteit van de bibliotheken te vergemakkelijken, adviseert Adobe de specifieke module voor het framework om de volgende bibliotheken te bundelen. Indien nodig, kan de laag onderliggende APIs inkapselen en aanpassen alvorens hen aan het project bloot te stellen.

* [@adobe/aem-spa-model-manager &#x200B;](https://www.npmjs.com/package/@adobe/aem-spa-model-manager)
* [@adobe/aem-spa-component-mapping &#x200B;](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

#### Implementaties {#implementations}

#### Reageren {#react}

npm-module: [@adobe/aem-response-editable-components &#x200B;](https://www.npmjs.com/package/@adobe/aem-react-editable-components)

#### Angular {#angular}

npm-module: [@adobe/aem-angular-editable-components &#x200B;](https://www.npmjs.com/package/@adobe/aem-angular-editable-components)

## Belangrijkste services en componenten {#main-services-and-components}

De volgende entiteiten moeten worden uitgevoerd overeenkomstig de specifieke richtsnoeren voor elk kader. Op basis van de kaderarchitectuur kan de implementatie sterk variëren, maar de beschreven functies moeten worden verstrekt.

### De modelprovider {#the-model-provider}

De componenten van het project moeten toegang tot de fragmenten van een model aan een ModelLeverancier delegeren. De ModelLeverancier is dan verantwoordelijk voor het luisteren naar veranderingen die aan het gespecificeerde fragment van het model worden aangebracht en keert het bijgewerkte model aan de het delegeren component terug.

Hiervoor moet de modelprovider zich registreren bij de [`PageModelManager`](#pagemodelmanager) . Dan wanneer een verandering voorkomt ontvangt het en gaat de bijgewerkte gegevens tot de het delegeren component over. Door overeenkomst, wordt het bezit ter beschikking gesteld aan de het delegeren component die het fragment van model zal dragen genoemd `cqModel`. De implementatie is vrij om deze eigenschap aan de component te leveren, maar moet aspecten zoals de integratie met raamarchitectuur, ontdekkbaarheid en gebruiksgemak in overweging nemen.

### De HTML-decorator van de component {#the-component-html-decorator}

De componentdecorator is verantwoordelijk voor het versieren van de buitenste HTML van het element van elke componentinstantie met een reeks gegevenskenmerken en klassennamen die door de Pagina-editor worden verwacht.

#### Componentdeclaratie {#component-declaration}

De volgende meta-gegevens moeten aan het buitenelement van HTML worden toegevoegd dat door de component van het project wordt geproduceerd. Hiermee kan de Pagina-editor de corresponderende bewerkingsconfiguratie ophalen.

* `data-cq-data-path`: pad naar de bron ten opzichte van de `jcr:content`

#### Bewerkbaarheidsverklaring en plaatsaanduiding {#editing-capability-declaration-and-placeholder}

De volgende metagegevens en klassennamen moeten worden toegevoegd aan het buitenste HTML-element dat wordt gemaakt door de component van het project. Hiermee kan de Pagina-editor gerelateerde functies bieden.

* `cq-placeholder`: Klassenaam die de tijdelijke aanduiding voor een lege component aanduidt
* `data-emptytext`: Label dat door de overlay moet worden weergegeven wanneer een componentinstantie leeg is

**Placeholder voor Lege Componenten**

Elke component moet worden uitgebreid met een functionaliteit waarmee het buitenste HTML-element wordt versierd met gegevenskenmerken en klassennamen die specifiek zijn voor plaatsaanduidingen en verwante overlays wanneer de component wordt geïdentificeerd als leeg.

**Ongeveer de Legheid van een Component**

* Is de component logisch leeg?
* Wat moet het label zijn dat door de overlay wordt weergegeven wanneer de component leeg is?

### Container {#container}

Een container is een component die is bedoeld om onderliggende componenten te bevatten en te renderen. Hiervoor doorloopt de container de eigenschappen `:itemsOrder` , `:items` en `:children` van het bijbehorende model.

De container haalt dynamisch de onderliggende componenten op uit de opslagruimte van de [`ComponentMapping`](#componentmapping) -bibliotheek. De container breidt vervolgens de onderliggende component uit met de mogelijkheden van de ModelProvider en instantieert deze ten slotte.

### Pagina {#page}

De component `Page` breidt de component `Container` uit. Een container is een component die onderliggende componenten, waaronder onderliggende pagina&#39;s, moet bevatten en weergeven. Hiervoor doorloopt de container de eigenschappen `:itemsOrder` , `:items` en `:children` van het bijbehorende model. De component `Page` haalt de onderliggende componenten dynamisch op uit de opslagruimte van de [`ComponentMapping`](#componentmapping) -bibliotheek. `Page` is verantwoordelijk voor het instantiëren van onderliggende componenten.

### Responsief raster {#responsive-grid}

De component Responsief raster is een container. Het bevat een specifieke variant van de ModelLeverancier die zijn kolommen vertegenwoordigt. Het responsieve Net en zijn kolommen zijn verantwoordelijk voor het versieren van het buitenste element van HTML van de component van het project met de specifieke klassennamen in het model.

De component Responsief raster moet vooraf worden toegewezen aan de AEM-tegenhanger omdat deze component complex is en zelden wordt aangepast.

#### Specifieke modelvelden {#specific-model-fields}

* `gridClassNames:` Klassenamen opgeven voor het responsieve raster
* `columnClassNames:` Geleverde klassennamen voor de responsieve kolom

Zie ook de npm-bron [@adobe/aem-response-editable-components &#x200B;](https://www.npmjs.com/package/@adobe/aem-react-editable-components)

#### Plaatsaanduiding van het responsieve raster {#placeholder-of-the-responsive-grid}

De component van het KUUROORD wordt in kaart gebracht aan een grafische container zoals het Responsieve Net en moet virtuele kindplaceholder toevoegen wanneer de inhoud wordt authored. Wanneer de inhoud van het KUUROORD door de Redacteur van de Pagina wordt ontworpen, wordt die inhoud ingebed in de redacteur gebruikend iframe en het `data-cq-editor` attribuut wordt toegevoegd aan de documentknoop van die inhoud. Wanneer het attribuut `data-cq-editor` aanwezig is, moet de container een HTMLElement omvatten om het gebied te vertegenwoordigen waarmee de auteur wanneer het opnemen van een nieuwe component in de pagina in wisselt.

Bijvoorbeeld:

```html
<div data-cq-data-path={"path/to/the/responsivegrid/*"} className="new section aem-Grid-newComponent"/>
```

>[!NOTE]
>
>De klassenamen die in het voorbeeld worden gebruikt, worden momenteel vereist door de pagina-editor.
>
>* `"new section"`: geeft aan dat het huidige element de tijdelijke aanduiding van de container is
>* `"aem-Grid-newComponent"`: normaliseert de component voor het ontwerpen van de lay-out
>

#### Componenttoewijzing {#component-mapping}

De onderliggende [`Component Mapping`](#componentmapping) bibliotheek en de bijbehorende `MapTo` functie kunnen worden ingekapseld en uitgebreid om de functionaliteit met betrekking tot te verstrekken uitgeeft configuratie die naast de huidige componentenklasse wordt verstrekt.

```javascript
const EditConfig = {

    emptyLabel: 'My Component',

    isEmpty: function() {
        return !this.props || !this.props.cqModel || this.props.cqModel.isEmpty;
    }
};

class MyComponent extends Component {

    render() {
        return <div className={'my-component'}></div>;
    }
}

MapTo('component/resource/path')(MyComponent, EditConfig);
```

In de bovengenoemde implementatie, wordt de projectcomponent uitgebreid met de leegheidsfunctionaliteit alvorens eigenlijk in de [&#x200B; opslag van de Afbeelding van de Component 1&rbrace; wordt geregistreerd. &#x200B;](#componentmapping) Dit gebeurt door de [`ComponentMapping`](#componentmapping) -bibliotheek in te kapselen en uit te breiden en de ondersteuning van het `EditConfig` -configuratieobject te introduceren:

```javascript
/**
 * Configuration object in charge of providing the necessary data expected by the page editor to initiate the authoring. The provided data is decorating the associated component
 *
 * @typedef {{}} EditConfig
 * @property {String} [dragDropName]       If defined, adds a specific class name enabling the drag and drop functionality
 * @property {String} emptyLabel           Label to be displayed by the placeholder when the component is empty. Optionally returns an empty text value
 * @property {function} isEmpty            Should the component be considered empty. The function is called using the context of the wrapper component giving you access to the component model
 */

/**
 * Map a React component with the given resource types. If an {@link EditConfig} is provided the <i>clazz</i> is wrapped to provide edition capabilities on the AEM Page Editor
 *
 * @param {string[]} resourceTypes                      - List of resource types for which to use the given <i>clazz</i>
 * @param {class} clazz                                 - Class to be instantiated for the given resource types
 * @param {EditConfig} [editConfig]                     - Configuration object for enabling the edition capabilities
 * @returns {class}                                     - The resulting decorated Class
 */
ComponentMapping.map = function map (resourceTypes, clazz, editConfig) {};
```

## Slinken met de paginaeditor {#contract-with-the-page-editor}

De projectcomponenten moeten minstens de volgende gegevensattributen produceren om de redacteur toe te staan om met hen in wisselwerking te staan.

* `data-cq-data-path`: relatief pad van de component, zoals opgegeven door `PageModel` (bijvoorbeeld `"root/responsivegrid/image"` ). Dit kenmerk mag niet aan pagina&#39;s worden toegevoegd.

Samengevat, om door de paginaredacteur als editable te worden geïnterpreteerd, moet een projectcomponent het volgende contract in acht nemen:

* Verstrek de verwachte attributen om een front-end componenteninstantie aan een middel van AEM te associëren.
* Verstrek de verwachte reeks attributen en klassennamen die de verwezenlijking van lege placeholders toelaat.
* Geef de verwachte klassenamen op, zodat u elementen kunt slepen en neerzetten.

### Standaard HTML-elementstructuur {#typical-html-element-structure}

Het volgende fragment illustreert de typische HTML-representatie van een pagina-inhoudsstructuur. Hier volgen enkele belangrijke punten:

* Het responsieve rasterelement bevat vooraf gedefinieerde klassenamen `aem-Grid--`
* Het responsieve kolomelement bevat vooraf ingestelde klassenamen `aem-GridColumn--`
* Een responsief raster dat ook de kolom van een bovenliggend raster is, wordt omlopen, zoals de twee vorige voorvoegsels, worden niet op hetzelfde element weergegeven
* Elementen die overeenkomen met bewerkbare bronnen hebben een eigenschap `data-cq-data-path` . Zie [&#x200B; Slinken met de sectie van de Redacteur van de Pagina &#x200B;](#contract-with-the-page-editor) van dit document.

```javascript
<div data-cq-data-path="/content/page">
    <div class="aem-Grid aem-Grid--12 aem-Grid--default--12">
        <div class="aem-container aem-GridColumn aem-GridColumn--default--12" data-cq-data-path="/content/page/jcr:content/root/responsivegrid">
            <div class="aem-Grid aem-Grid--12 aem-Grid--default--12">
                <div class="cmp-image cq-dd-image aem-GridColumn aem-GridColumn--default--12" data-cq-data-path="/root/responsivegrid/image">
                    <img src="/content/we-retail-spa-sample/react/jcr%3acontent/root/responsivegrid/image.img.jpeg/1512113734019.jpeg">
                </div>
            </div>
        </div>
    </div>
</div>
```

## Navigatie en routering {#navigation-and-routing}

App bezit het verpletteren. De front-end ontwikkelaar moet eerst een component van de Navigatie (in kaart gebracht aan een navigatiecomponent van AEM) uitvoeren. Deze component zou URL verbindingen teruggeven die samen met een reeks routes moeten worden gebruikt die fragmenten van inhoud tonen of zullen verbergen.

De onderliggende [`PageModelManager`](#pagemodelmanager) -bibliotheek en de bijbehorende [`ModelRouter`](routing.md) -module (standaard ingeschakeld) zijn verantwoordelijk voor het vooraf ophalen en verlenen van toegang tot het model dat aan een bepaald bronnenpad is gekoppeld.

De twee entiteiten hebben betrekking op het begrip &#39;routering&#39;, maar de [`ModelRouter`](routing.md) is alleen verantwoordelijk voor het laden van de [`PageModelManager`](#pagemodelmanager) met een gegevensmodel dat is gestructureerd in synchronisatie met de huidige toepassingsstatus.

Zie het artikel [&#x200B; Model dat van het KUUROORD &#x200B;](routing.md) voor meer informatie verplettert.

## SPA in actie {#spa-in-action}

Zie hoe een eenvoudige KUUROORD werkt en met een KUUROORD zelf experimenteert door op de volgende documenten verder te gaan:

* [&#x200B; Begonnen het Worden met SPAs in AEM die React &#x200B;](getting-started-react.md) gebruiken.
* [&#x200B; Begonnen het Worden met SPAs in AEM gebruikend Angular &#x200B;](getting-started-angular.md).

## Verdere lezing {#further-reading}

Voor meer informatie over SPAs in AEM, zie de volgende documenten:

* [&#x200B; het Overzicht van de Redacteur van het KUUROORD &#x200B;](editor-overview.md) voor een overzicht van SPAs in AEM en het communicatie model
