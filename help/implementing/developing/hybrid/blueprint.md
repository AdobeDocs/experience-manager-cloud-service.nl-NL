---
title: SPA
description: In dit document wordt het algemene, raamonafhankelijke contract beschreven dat door elk SPA framework moet worden uitgevoerd, zodat u bewerkbare SPA binnen AEM kunt implementeren.
exl-id: 9d47c0e9-600c-4f45-9169-b3c9bbee9152
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '2022'
ht-degree: 0%

---

# SPA {#spa-blueprint}

Om de auteur toe te laten om de AEM SPARedacteur te gebruiken om de inhoud van een SPA uit te geven, zijn er vereisten die de SPA moet vervullen.

## Inleiding {#introduction}

In dit document wordt het algemene contract beschreven dat door elk SPA framework moet worden uitgevoerd (dat wil zeggen, het type AEM supportlaag), zodat u bewerkbare SPA binnen AEM kunt implementeren.

Om de auteur toe te laten om de AEM Redacteur van de Pagina te gebruiken om de gegevens uit te geven die door een Enige Kader van de Toepassing van de Pagina worden blootgesteld, moet een project de structuur van het model kunnen interpreteren die de semantische waarde van de gegevens vertegenwoordigt die voor een toepassing binnen de AEM bewaarplaats worden opgeslagen. Om dit doel te bereiken, worden twee raamwerk-agnostische bibliotheken aangeboden: de `PageModelManager` en de `ComponentMapping`.

>[!NOTE]
>
>De volgende vereisten zijn onafhankelijk van het framework. Als aan deze vereisten wordt voldaan, kan een kader-specifieke laag worden verstrekt die uit modules, componenten, en de diensten wordt samengesteld.
>
>**Aan deze eisen wordt reeds voldaan voor de React and Angular frameworks in AEM.** De vereisten in deze blauwdruk zijn alleen relevant als u een ander kader wilt implementeren voor gebruik met AEM.

>[!CAUTION]
>
>Hoewel de SPA mogelijkheden van AEM frameonafhankelijk zijn, worden momenteel alleen de React- en Angular-frameworks ondersteund.

## PageModelManager {#pagemodelmanager}

De `PageModelManager` De bibliotheek wordt verstrekt als pakket NPM dat door een SPA project moet worden gebruikt. Het begeleidt de SPA en dient als gegevensmodelmanager.

Namens de SPA onttrekt het de herwinning en het beheer van de structuur JSON die de daadwerkelijke inhoudsstructuur vertegenwoordigt. Het is ook verantwoordelijk voor de synchronisatie met de SPA om te laten weten wanneer het zijn componenten opnieuw moet renderen.

Zie het NPM-pakket [@adobe/aem-spa-model-manager](https://www.npmjs.com/package/@adobe/aem-spa-model-manager)

Bij het initialiseren van de `PageModelManager`, laadt de bibliotheek eerst het verstrekte wortelmodel van App (via parameter, meta bezit, of huidige URL). Als in de bibliotheek wordt aangegeven dat het model van de huidige pagina geen deel uitmaakt van het hoofdmodel, wordt het opgehaald en opgenomen als het model van een onderliggende pagina.

![Consolidatie van paginamodel](assets/page-model-consolidation.png)

### ComponentMapping {#componentmapping}

De `ComponentMapping` wordt verstrekt als pakket NPM aan het front-end project. Het slaat front-end componenten op en verstrekt een manier voor de SPA aan kaart front-end componenten aan AEM middeltypes. Hierdoor wordt een dynamische resolutie van componenten ingeschakeld bij het parseren van het JSON-model van de toepassing.

Elk onderdeel in het model bevat een `:type` veld dat een AEM-brontype weergeeft. Als de front-end component is gekoppeld, kan deze zichzelf renderen met behulp van het fragment van het model dat is ontvangen van de onderliggende bibliotheken.

#### Dynamisch model naar componenttoewijzing {#dynamic-model-to-component-mapping}

Zie het artikel voor meer informatie over de manier waarop het dynamische model wordt toegewezen aan componenttoewijzing in de JavaScript SPA SDK voor AEM [Dynamisch model naar componenttoewijzing voor SPA](model-to-component-mapping.md).

### Framework-specifieke laag {#framework-specific-layer}

Voor elk front-end framework moet een derde laag worden geïmplementeerd. Deze derde bibliotheek is verantwoordelijk voor de interactie met de onderliggende bibliotheken en biedt een reeks goed geïntegreerde en gebruiksvriendelijke ingangspunten voor de interactie met het gegevensmodel.

In de rest van dit document worden de vereisten van deze specifieke laag van het intermediaire kader beschreven en wordt ernaar gestreefd onafhankelijk van het framework te zijn. Door de volgende vereisten na te leven, kan een kader-specifieke laag voor de projectcomponenten worden verstrekt om met de onderliggende bibliotheken in wisselwerking te staan die het gegevensmodel leiden.

## Algemene concepten {#general-concepts}

### Paginamodel {#page-model}

De inhoudsstructuur van de pagina wordt opgeslagen in AEM. Het model van de pagina wordt gebruikt om SPA componenten in kaart te brengen en te concretiseren. De SPA ontwikkelaars creëren SPA componenten die zij aan AEM componenten in kaart brengen. Om dit te doen, gebruiken zij het middeltype (of weg aan de AEM component) als unieke sleutel.

De SPA componenten moeten synchroon zijn met het paginamodel en worden bijgewerkt met eventuele wijzigingen in de inhoud. Een patroon met behulp van dynamische componenten moet worden gebruikt om direct componenten te instantiëren volgens de opgegeven structuur van het paginamodel.

### Meta-velden {#meta-fields}

Het paginamodel gebruikt de JSON Model Exporter, die zelf gebaseerd is op de [Verkoopmodel](https://sling.apache.org/documentation/bundles/models.html) API. De exporteerbare kiesmodellen geven de volgende lijst met velden weer, zodat de onderliggende bibliotheken het gegevensmodel kunnen interpreteren:

* `:type`: Type van de AEM-bron (standaard = type resource)
* `:children`: Hierarchische onderliggende elementen van de huidige bron. Onderliggende items maken geen deel uit van de binneninhoud van de huidige bron (vindt u bij items die een pagina vertegenwoordigen)
* `:hierarchyType`: Hiërarchisch type van een bron. De `PageModelManager` ondersteunt momenteel het paginatype

* `:items`: Bronnen voor onderliggende inhoud van de huidige bron (geneste structuur, alleen aanwezig op containers)
* `:itemsOrder`: Ordered list of the children. Het JSON-toewijzingsobject garandeert de volgorde van de velden niet. Door zowel de kaart als de huidige array te hebben, heeft de consument van de API de voordelen van beide structuren
* `:path`: Inhoudspad van een item (aanwezig op items die een pagina vertegenwoordigen)

Zie ook [Aan de slag met AEM Content Services.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)

### Framework-Specific Module {#framework-specific-module}

Het scheiden van zorgen helpt de uitvoering van het project te vergemakkelijken. Daarom moet een npm-specifiek pakket worden verstrekt. Dit pakket is verantwoordelijk voor het samenvoegen en blootstellen van de basismodules, de diensten, en de componenten. Deze componenten moeten de logica van het gegevensmodelbeheer inkapselen en toegang tot de gegevens verlenen de component van het project verwacht. De module is ook verantwoordelijk voor het tijdelijk blootstellen van nuttige ingangspunten van de onderliggende bibliotheken.

Om de interoperabiliteit van de bibliotheken te vergemakkelijken, adviseert de Adobe de specifieke module voor het kader om de volgende bibliotheken te bundelen. Indien nodig, kan de laag onderliggende APIs inkapselen en aanpassen alvorens hen aan het project bloot te stellen.

* [@adobe/aem-spa-model-manager](https://www.npmjs.com/package/@adobe/aem-spa-model-manager)
* [@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

#### Implementaties {#implementations}

#### Reageren {#react}

npm-module: [@adobe/aem-response-editable-components](https://www.npmjs.com/package/@adobe/aem-react-editable-components)

#### Angular {#angular}

npm-module: [@adobe/aem-angular-editable-components](https://www.npmjs.com/package/@adobe/aem-angular-editable-components)

## Belangrijkste services en componenten {#main-services-and-components}

De volgende entiteiten moeten worden uitgevoerd overeenkomstig de specifieke richtsnoeren voor elk kader. Op basis van de kaderarchitectuur kan de implementatie sterk variëren, maar de beschreven functies moeten worden verstrekt.

### De modelprovider {#the-model-provider}

De componenten van het project moeten toegang tot de fragmenten van een model aan een ModelLeverancier delegeren. De ModelLeverancier is dan verantwoordelijk voor het luisteren naar veranderingen die aan het gespecificeerde fragment van het model worden aangebracht en keert het bijgewerkte model aan de het delegeren component terug.

Hiervoor moet de modelprovider zich registreren bij de [`PageModelManager`](#pagemodelmanager). Dan wanneer een verandering voorkomt ontvangt het en gaat de bijgewerkte gegevens tot de het delegeren component over. Door overeenkomst, wordt het bezit ter beschikking gesteld aan de het delegeren component die het fragment van model zal dragen genoemd `cqModel`. De implementatie is vrij om deze eigenschap aan de component te leveren, maar moet aspecten zoals de integratie met raamarchitectuur, ontdekkbaarheid en gebruiksgemak in overweging nemen.

### De HTML Decorator van de component {#the-component-html-decorator}

De componentdecorator is verantwoordelijk voor het versieren van de buitenste HTML van de elementinstanties met een reeks gegevenskenmerken en klassennamen die door de Pagina-editor worden verwacht.

#### Componentdeclaratie {#component-declaration}

De volgende meta-gegevens moeten aan het buitenelement van HTML worden toegevoegd dat door de component van het project wordt geproduceerd. Hiermee kan de Pagina-editor de corresponderende bewerkingsconfiguratie ophalen.

* `data-cq-data-path`: Het pad naar de bron ten opzichte van de `jcr:content`

#### Bewerkbaarheidsverklaring en plaatsaanduiding {#editing-capability-declaration-and-placeholder}

De volgende meta- gegevens en klassennamen moeten aan het buitenelement van HTML worden toegevoegd dat door de component van het project wordt geproduceerd. Hiermee kan de Pagina-editor gerelateerde functies bieden.

* `cq-placeholder`: Klassenaam die de tijdelijke aanduiding voor een lege component identificeert
* `data-emptytext`: Label dat door de overlay moet worden weergegeven wanneer een componentinstantie leeg is

**Plaatsaanduiding voor lege componenten**

Elke component moet worden uitgebreid met een functionaliteit waarmee het buitenste HTML-element wordt versierd met gegevenskenmerken en klassennamen die specifiek zijn voor plaatsaanduidingen en verwante overlays wanneer de component wordt geïdentificeerd als leeg.

**Informatie over de lege ruimte van een component**

* Is de component logisch leeg?
* Wat moet het label zijn dat door de overlay wordt weergegeven wanneer de component leeg is?

### Container {#container}

Een container is een component die is bedoeld om onderliggende componenten te bevatten en te renderen. De container doorloopt de `:itemsOrder`, `:items` en `:children` eigenschappen van zijn model.

De container krijgt dynamisch de kindcomponenten van de opslag van [`ComponentMapping`](#componentmapping) bibliotheek. De container breidt vervolgens de onderliggende component uit met de mogelijkheden van de ModelProvider en instantieert deze ten slotte.

### Pagina {#page}

De `Page` component breidt de `Container` component. Een container is een component die onderliggende componenten, waaronder onderliggende pagina&#39;s, moet bevatten en weergeven. De container doorloopt de `:itemsOrder`, `:items`, en `:children` eigenschappen van zijn model. De `Page` de component krijgt dynamisch de kindcomponenten van de opslag van [`ComponentMapping`](#componentmapping) bibliotheek. De `Page` is verantwoordelijk voor het instantiëren van onderliggende componenten.

### Responsief raster {#responsive-grid}

De component Responsief raster is een container. Het bevat een specifieke variant van de ModelLeverancier die zijn kolommen vertegenwoordigt. Het responsieve Net en zijn kolommen zijn verantwoordelijk voor het versieren van het buitenste HTML element van de component van het project met de specifieke klassennamen in het model.

De component Responsief raster moet vooraf worden toegewezen aan de AEM tegenhanger omdat deze component complex is en zelden wordt aangepast.

#### Specifieke modelvelden {#specific-model-fields}

* `gridClassNames:` Klassenamen opgegeven voor het responsieve raster
* `columnClassNames:` Klassenamen opgegeven voor de responsieve kolom

Zie ook de npm-bron [@adobe/aem-response-editable-components](https://www.npmjs.com/package/@adobe/aem-react-editable-components)

#### Plaatsaanduiding van het responsieve raster {#placeholder-of-the-responsive-grid}

De SPA component wordt toegewezen aan een grafische container zoals het Responsieve raster en moet een virtuele tijdelijke aanduiding voor onderliggende items toevoegen wanneer de inhoud wordt gemaakt. Wanneer de inhoud van de SPA wordt geschreven door de Pagina-editor, wordt die inhoud ingesloten in de editor met behulp van een iframe en de `data-cq-editor` wordt toegevoegd aan het documentknooppunt van die inhoud. Wanneer de `data-cq-editor` is aanwezig, moet de container een HTMLElement omvatten om het gebied te vertegenwoordigen waarmee de auteur wanneer het opnemen van een nieuwe component in de pagina interactie aangaat.

Bijvoorbeeld:

```html
<div data-cq-data-path={"path/to/the/responsivegrid/*"} className="new section aem-Grid-newComponent"/>
```

>[!NOTE]
>
>De klassenamen die in het voorbeeld worden gebruikt, worden momenteel vereist door de pagina-editor.
>
>* `"new section"`: Geeft aan dat het huidige element de tijdelijke aanduiding van de container is
>* `"aem-Grid-newComponent"`: Normaliseert de component voor het ontwerpen van de lay-out
>

#### Componenttoewijzing {#component-mapping}

De onderliggende waarde [`Component Mapping`](#componentmapping) bibliotheek en `MapTo` Deze functie kan worden ingekapseld en uitgebreid om de functionaliteit met betrekking tot te verstrekken uitgeeft configuratie die naast de huidige componentenklasse wordt verstrekt.

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

In de bovenstaande implementatie wordt de projectcomponent uitgebreid met de lege functionaliteit voordat de component daadwerkelijk in de [Componenttoewijzing](#componentmapping) opslaan. Dit doet u door de [`ComponentMapping`](#componentmapping) bibliotheek om de steun van de `EditConfig` configuratieobject:

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

* `data-cq-data-path`: Relatief pad van de component, opgegeven door de `PageModel` (bijvoorbeeld `"root/responsivegrid/image"`). Dit kenmerk mag niet aan pagina&#39;s worden toegevoegd.

Samengevat, om door de paginaredacteur als editable te worden geïnterpreteerd, moet een projectcomponent het volgende contract in acht nemen:

* Verstrek de verwachte attributen om een front eindcomponenteninstantie aan een AEM middel te associëren.
* Verstrek de verwachte reeks attributen en klassennamen die de verwezenlijking van lege placeholders toelaat.
* Geef de verwachte klassenamen op, zodat u elementen kunt slepen en neerzetten.

### Normale HTML-elementstructuur {#typical-html-element-structure}

Het volgende fragment illustreert de typische HTML-representatie van een pagina-inhoudstructuur. Hier volgen enkele belangrijke punten:

* Het responsieve rasterelement bevat vooraf ingestelde klassenamen `aem-Grid--`
* Het responsieve kolomelement bevat vooraf ingestelde klassenamen `aem-GridColumn--`
* Een responsief raster dat ook de kolom van een bovenliggend raster is, wordt omlopen, zoals de twee vorige voorvoegsels, worden niet op hetzelfde element weergegeven
* Elementen die overeenkomen met bewerkbare bronnen dragen een `data-cq-data-path` eigenschap. Zie de [Slinken met de paginaeditor](#contract-with-the-page-editor) van dit document.

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

App bezit het verpletteren. De front-end ontwikkelaar moet eerst een component van de Navigatie (in kaart gebracht aan een AEM navigatiecomponent) uitvoeren. Deze component zou URL verbindingen teruggeven die samen met een reeks routes moeten worden gebruikt die fragmenten van inhoud tonen of zullen verbergen.

De onderliggende waarde [`PageModelManager`](#pagemodelmanager) bibliotheek en [`ModelRouter`](routing.md) de module (die door gebrek wordt toegelaten) is de oorzaak van het pre-halen en het verlenen van toegang tot het model verbonden aan een bepaalde middelweg.

De twee entiteiten hebben betrekking op het begrip &quot;routering&quot;, maar op [`ModelRouter`](routing.md) alleen verantwoordelijk is voor het laden van de [`PageModelManager`](#pagemodelmanager) met een gegevensmodel dat synchroon is met de huidige status van de toepassing.

Zie het artikel [SPA](routing.md) voor meer informatie .

## SPA in actie {#spa-in-action}

Bekijk hoe een eenvoudige SPA werkt en experimenteer met een SPA zelf door door te gaan met de volgende documenten:

* [Aan de slag met SPA in AEM Reageren gebruiken](getting-started-react.md).
* [Aan de slag met SPA in AEM met Angular](getting-started-angular.md).

## Verdere lezing {#further-reading}

Raadpleeg de volgende documenten voor meer informatie over SPA in AEM:

* [Overzicht SPA Editor](editor-overview.md) voor een overzicht van SPA in AEM en het communicatiemodel
