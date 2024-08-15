---
title: Aan de slag met SPA in AEM Reageren gebruiken
description: In dit artikel wordt een voorbeeld SPA toepassing gepresenteerd, wordt uitgelegd hoe deze wordt samengesteld en kunt u snel met uw eigen SPA aan de slag met het React-framework.
exl-id: 13998526-65e7-4d1b-bd47-452bad3780a2
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 0%

---

# Aan de slag met SPA in AEM Reageren gebruiken {#getting-started-with-spas-in-aem-using-react}

Toepassingen op één pagina (SPA) kunnen aantrekkelijke ervaringen bieden voor websitegebruikers. Ontwikkelaars willen sites kunnen maken met behulp van SPA frameworks en auteurs willen inhoud naadloos bewerken binnen AEM voor een site die is gebouwd met behulp van SPA frameworks.

De SPA ontwerpfunctie biedt een uitgebreide oplossing voor het ondersteunen van SPA binnen AEM. Dit artikel biedt een vereenvoudigde SPA toepassing voor het React-framework, legt uit hoe het is samengesteld, zodat u snel aan de slag kunt met uw eigen SPA.

>[!NOTE]
>
>Dit artikel is gebaseerd op het React-kader. Voor het overeenkomstige document voor het kader van de Angular zie [ Begonnen het worden met SPA in AEM - Angular ](getting-started-angular.md).

## Inleiding {#introduction}

Dit artikel vat het basisfunctioneren van een eenvoudige SPA en het minimum samen dat u moet weten om van u lopend te krijgen.

Raadpleeg de volgende documenten voor meer informatie over SPA werken in AEM:

* [SPA Inleiding en Analyse](introduction.md)
* [Overzicht SPA Editor](editor-overview.md)
* [SPA](blueprint.md)

>[!NOTE]
>
>Om inhoud binnen een SPA te kunnen ontwerpen, moet de inhoud in AEM worden opgeslagen en door het inhoudsmodel worden blootgesteld.
>
>Een SPA die buiten AEM is ontwikkeld, is niet aanvaardbaar als het contract voor het inhoudsmodel niet wordt nageleefd.

Dit document doorloopt de structuur van een vereenvoudigde SPA die is gemaakt met het React-framework en illustreert hoe het werkt, zodat u deze interpretatie kunt toepassen op uw eigen SPA.

## Afhankelijkheden, configuratie en gebouwen {#dependencies-configuration-and-building}

Naast de verwachte afhankelijkheid van React, kan de steekproef SPA extra bibliotheken gebruiken om de verwezenlijking van SPA efficiënter te maken.

### Afhankelijkheden {#dependencies}

Het bestand `package.json` definieert de vereisten van het algemene SPA. De minimum AEM gebiedsdelen voor een werkende SPA zijn hier vermeld.

```
  "dependencies": {
    "@adobe/aem-react-editable-components": "~1.0.4",
    "@adobe/aem-spa-component-mapping": "~1.0.5",
    "@adobe/aem-spa-page-model-manager": "~1.0.3"
  }
```

Omdat dit voorbeeld is gebaseerd op het React-framework, zijn er twee React-specifieke afhankelijkheden die verplicht zijn in het `package.json` -bestand:

```
 react
 react-dom
```

`aem-clientlib-generator` wordt gebruikt om het maken van clientbibliotheken automatisch te maken als onderdeel van het ontwikkelproces.

`"aem-clientlib-generator": "^1.4.1",`

Voor verdere details zie [ aem-clientlib-generator op GitHub ](https://github.com/wcm-io-frontend/aem-clientlib-generator).

`aem-clientlib-generator` wordt als volgt geconfigureerd in het `clientlib.config.js` -bestand.

```
module.exports = {
    // default working directory (can be changed per 'cwd' in every asset option)
    context: __dirname,

    // path to the clientlib root folder (output)
    clientLibRoot: "./../content/jcr_root/apps/my-react-app/clientlibs",

    libs: {
        name: "my-react-app",
        allowProxy: true,
        categories: ["my-react-app"],
        embed: ["my-react-app.responsivegrid"],
        jsProcessor: ["min:gcc"],
        serializationFormat: "xml",
        assets: {
            js: [
                "dist/**/*.js"
            ],
            css: [
                "dist/**/*.css"
            ]
        }
    }
};
```

### Gebouw {#building}

Eigenlijk bouwend app gebruikt [ Webpack ](https://webpack.js.org/) voor transpilatie naast aem-client-clientlib-generator voor de automatische verwezenlijking van de cliëntbibliotheek. Daarom zal het bouwstijlbevel op lijken:

`"build": "webpack && clientlib --verbose"`

Nadat het pakket is gemaakt, kan het naar een AEM-instantie worden geüpload.

### Projectarchetype AEM {#aem-project-archetype}

Om het even welk AEM project zou [ AEM Archetype van het Project ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) moeten gebruiken, dat SPA projecten gebruikend React of Angular steunt en SPA SDK gebruikt.

## Toepassingsstructuur {#application-structure}

Als u de afhankelijkheden opneemt en uw app samenstelt zoals eerder beschreven, blijft er een werkende SPA over die u kunt uploaden naar uw AEM-exemplaar.

In het volgende gedeelte van dit document wordt uitgelegd hoe een SPA in AEM is gestructureerd, welke belangrijke bestanden de toepassing sturen en hoe deze samenwerken.

Een vereenvoudigde afbeeldingscomponent wordt als voorbeeld gebruikt, maar alle componenten van de toepassing zijn op hetzelfde concept gebaseerd.

### index.js {#index-js}

Het ingangspunt in de SPA is het `index.js` bestand dat hier wordt weergegeven en dat u zich op de belangrijke inhoud wilt concentreren.

```
import ReactDOM from 'react-dom';
import App from './App';
import { ModelManager, Constants } from "@adobe/aem-spa-page-model-manager";

...

ModelManager.initialize().then((pageModel) => {
ReactDOM.render(
    <App cqChildren={pageModel[Constants.CHILDREN_PROP]} cqItems={pageModel[Constants.ITEMS_PROP]} cqItemsOrder={pageModel[Constants.ITEMS_ORDER_PROP]} cqPath={ModelManager.rootPath} locationPathname={ window.location.pathname }/>
, document.getElementById('page'));

});
```

De hoofdfunctie van `index.js` is om de functie `ReactDOM.render` te gebruiken om te bepalen waar in de DOM de toepassing wordt geïnjecteerd.

Dit is een standaardgebruik van deze functie, niet uniek voor deze voorbeeldapp.

#### Statische instantie {#static-instantiation}

Wanneer de component statisch wordt geconcretiseerd gebruikend het componentenmalplaatje (bijvoorbeeld, JSX), moet de waarde van het model tot de eigenschappen van de component worden overgegaan.

### App.js {#app-js}

Door de app te renderen, roept `index.js` `App.js` aan. Deze wordt hier in een vereenvoudigde versie weergegeven om de focus op de belangrijke inhoud te richten.

```
import {Page, withModel } from '@adobe/aem-react-editable-components';

...

class App extends Page {
...
}

export default withModel(App);
```

`App.js` dient vooral om de basiscomponenten te verpakken waaruit de toepassing is samengesteld. Het ingangspunt van elke toepassing is de pagina.

### Page.js {#page-js}

Door de pagina weer te geven, worden `App.js` aanroepen `Page.js` hier in een vereenvoudigde versie weergegeven.

```
import {Page, MapTo, withComponentMappingContext } from "@adobe/aem-react-editable-components";

...

class AppPage extends Page {
...
}

MapTo('my-react-app/components/structure/page')(withComponentMappingContext(AppPage));
```

In dit voorbeeld breidt de `AppPage` -klasse `Page` uit, die de methoden voor binneninhoud bevat die vervolgens kunnen worden gebruikt.

`Page` neemt de JSON-representatie van het paginamodel op en verwerkt de inhoud om elk element van de pagina te buigen of te versieren. De verdere details op `Page` kunnen in het document [ SPA Vervagen worden gevonden.](blueprint.md)

### Image.js {#image-js}

Als de pagina wordt gerenderd, kunnen de componenten zoals `Image.js` die hier worden weergegeven, worden gerenderd.

```
import React, {Component} from 'react';
import {MapTo} from '@adobe/aem-react-editable-components';

require('./Image.css');

const ImageEditConfig = {

    emptyLabel: 'Image',

    isEmpty: function() {
        return !this.props || !this.props.src || this.props.src.trim().length < 1;
    }
};

class Image extends Component {

    render() {
        return (<img src={this.props.src}>);
    }
}

MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);
```

Het centrale idee van SPA in AEM is het idee om SPA componenten aan AEM componenten in kaart te brengen en de component bij te werken wanneer de inhoud (en omgekeerd) wordt gewijzigd. Zie het document [ SPA het Overzicht van de Redacteur ](editor-overview.md) voor een samenvatting van dit communicatie model.

`MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);`

De methode `MapTo` wijst de SPA component aan de AEM toe. Het ondersteunt het gebruik van één tekenreeks of een array van tekenreeksen.

`ImageEditConfig` is een configuratieobject dat de ontwerpmogelijkheden van een component helpt in te schakelen door de vereiste metagegevens voor de editor op te geven om plaatsaanduidingen te genereren

Als er geen inhoud is, worden etiketten verstrekt als placeholders om de lege inhoud te vertegenwoordigen.

#### Dynamisch doorgegeven eigenschappen {#dynamically-passed-properties}

De gegevens uit het model worden dynamisch doorgegeven als eigenschappen van de component.

## Bewerkbare inhoud exporteren {#exporting-editable-content}

U kunt een component exporteren en bewerkbaar houden.

```
import React, { Component } from 'react';
import { MapTo } from '@adobe/aem-react-editable-components';

...

const EditConfig = {...}

class PageClass extends Component {...};

...

export default MapTo('my-react-app/react/components/structure/page')(PageClass, EditConfig);
```

De functie `MapTo` retourneert een `Component` die het resultaat is van een compositie die de opgegeven `PageClass` uitbreidt met de klassennamen en -kenmerken die het schrijven mogelijk maken. Deze component kan naar later worden uitgevoerd om in de prijsverhoging van uw toepassing worden geconcretiseerd.

Bij het exporteren met de functies `MapTo` of `withModel` , wordt de component `Page` omsloten met een component `ModelProvider` die standaardcomponenten toegang biedt tot de nieuwste versie van het paginamodel of een exacte locatie in dat paginamodel.

Voor meer informatie zie het [ SPA document van de Vervaging ](blueprint.md).

>[!NOTE]
>
>Standaard ontvangt u het gehele model van de component wanneer u de functie `withModel` gebruikt.

## Informatie delen tussen SPA componenten {#sharing-information-between-spa-components}

Componenten in een toepassing van één pagina moeten regelmatig informatie uitwisselen. Er zijn verschillende aanbevolen manieren om dit te doen, die als volgt worden opgesomd in toenemende mate van complexiteit.

* **Optie 1:** centraliseer de logica en uitzending aan de noodzakelijke componenten bijvoorbeeld, door React Context te gebruiken.
* **Optie 2:** de componentenstaten van het Aandeel door een staatsbibliotheek zoals Redux te gebruiken.
* **Optie 3:** hefboomwerking de objecten hiërarchie door de containercomponent aan te passen en uit te breiden.

## Volgende stappen {#next-steps}

* [ Begonnen het Worden met SPA in AEM gebruikend Angular ](getting-started-angular.md) toont hoe een basis SPA wordt gebouwd om met de SPA Redacteur in AEM te werken gebruikend Angular.
* [ SPA het Overzicht van de Redacteur ](editor-overview.md) gaat in meer diepte in het communicatie model tussen AEM en de SPA.
* [ WKND SPA Project ](wknd-tutorial.md) is een geleidelijke leerprogramma die een eenvoudig SPA project in AEM uitvoeren.
* [ Dynamisch Model aan de Toewijzing van de Component voor SPA ](model-to-component-mapping.md) verklaart het dynamische model aan componentenafbeelding en hoe het binnen SPA in AEM werkt.
* [ SPA Vervagen ](blueprint.md) biedt een diepe duik in hoe SPA SDK voor AEM werkt voor het geval u SPA in AEM voor een kader buiten Reageren of Angular wilt uitvoeren of eenvoudig een dieper begrip zou willen.
