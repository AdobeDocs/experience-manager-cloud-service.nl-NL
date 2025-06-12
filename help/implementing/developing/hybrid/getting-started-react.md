---
title: Begonnen het worden met SPAs in AEM Gebruikend Reageren
description: Dit artikel stelt een steekproeftoepassing van het KUUROORD voor, verklaart hoe het wordt samengesteld, en laat u in werking stellen met uw eigen KUUROORD snel gebruikend het kader van het Reageren.
exl-id: 13998526-65e7-4d1b-bd47-452bad3780a2
feature: Developing
role: Admin, Architect, Developer
index: false
source-git-commit: 7a9d947761b0473f5ddac3c4d19dfe5bed5b97fe
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 0%

---


# Begonnen het worden met SPAs in AEM Gebruikend Reageren {#getting-started-with-spas-in-aem-using-react}

Toepassingen van één pagina (SPAs) kunnen dwingende ervaringen voor websitegebruikers aanbieden. De ontwikkelaars willen plaatsen kunnen bouwen gebruikend het kader van het KUUROORD en de auteurs willen inhoud binnen AEM voor een plaats foutloos uitgeven die gebruikend het kader van het KUUROORD wordt gebouwd.

De auteurseigenschap van het KUUROORD biedt een uitvoerige oplossing voor het steunen van SPAs binnen AEM aan. Dit artikel stelt een vereenvoudigde toepassing van het KUUROORD op het kader van het Reageren voor, verklaart hoe het wordt samengesteld, toestaand u om snel met uw eigen KUUROORD in werking te stellen.

>[!NOTE]
>
>Dit artikel is gebaseerd op het React-kader. Voor het overeenkomstige document voor het kader van Angular zie [ Begonnen Worden met SPAs in AEM - Angular ](getting-started-angular.md).

{{ue-over-spa}}

## Inleiding {#introduction}

Dit artikel vat het basisfunctioneren van een eenvoudige KUUROORD en het minimum samen dat u moet weten om van u lopende te krijgen.

Voor meer detail op hoe SPAs in AEM werkt, zie de volgende documenten:

* [Introductie van het KUUROORD en Analyse](introduction.md)
* [Overzicht van SPA-editor](editor-overview.md)
* [SPA-blauwdruk](blueprint.md)

>[!NOTE]
>
>Om inhoud binnen een SPA te kunnen schrijven, moet de inhoud in AEM worden opgeslagen en door het inhoudsmodel worden blootgesteld.
>
>Een SBZ die buiten AEM is ontwikkeld, is niet toegestaan als het contract voor het inhoudsmodel niet wordt nageleefd.

Dit document zal door de structuur van een vereenvoudigde SPA lopen die gebruikend het React kader wordt gecreeerd en zal illustreren hoe het werkt zodat kunt u dit begrip op uw eigen SPA toepassen.

## Afhankelijkheden, configuratie en gebouwen {#dependencies-configuration-and-building}

Naast de verwachte afhankelijkheid van het Reageren, kan de steekproefSPA extra bibliotheken gebruiken om de verwezenlijking van het KUUROORD efficiënter te maken.

### Afhankelijkheden {#dependencies}

Het `package.json` dossier bepaalt de vereisten van het algemene pakket van het KUUROORD. De minimum AEM gebiedsdelen voor een werkende SPA zijn hier vermeld.

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

Nadat het pakket is gemaakt, kan het worden geüpload naar een AEM-instantie.

### AEM Project Archetype {#aem-project-archetype}

Om het even welk project van AEM zou het [ Archetype van het Project van AEM ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=nl-NL) moeten gebruiken, dat de projecten van het KUUROORD gebruikend React of Angular steunt en het KUUROORD SDK gebruikt.

## Toepassingsstructuur {#application-structure}

Als u de afhankelijkheden opneemt en uw app maakt zoals eerder beschreven, blijft er een werkende SPA-pakket over dat u kunt uploaden naar uw AEM-instantie.

De volgende sectie van dit document zal u door hoe een KUUROORD in AEM gestructureerd is, de belangrijke dossiers die de toepassing drijven, en hoe zij samenwerken.

Een vereenvoudigde afbeeldingscomponent wordt als voorbeeld gebruikt, maar alle componenten van de toepassing zijn op hetzelfde concept gebaseerd.

### index.js {#index-js}

Het ingangspunt in het SPA is het `index.js` dossier dat hier wordt getoond vereenvoudigd om zich op de belangrijke inhoud te concentreren.

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

`Page` neemt de JSON-representatie van het paginamodel op en verwerkt de inhoud om elk element van de pagina te buigen of te versieren. De verdere details op `Page` kunnen in het document [ Vervagen van het KUUROORD ](blueprint.md) worden gevonden.

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

Het centrale idee van SPAs in AEM is het idee om de componenten van SPA aan de componenten van AEM in kaart te brengen en de component bij te werken wanneer de inhoud (en omgekeerd) wordt gewijzigd. Zie het document [ Overzicht van de Redacteur van het KUUROORD ](editor-overview.md) voor een samenvatting van dit communicatie model.

`MapTo('my-react-app/components/content/image')(Image, ImageEditConfig);`

De methode `MapTo` wijst de component SPA aan de component van AEM toe. Het ondersteunt het gebruik van één tekenreeks of een array van tekenreeksen.

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

Voor meer informatie zie het [ document van de Vervaging van het KUUROORD ](blueprint.md).

>[!NOTE]
>
>Standaard ontvangt u het gehele model van de component wanneer u de functie `withModel` gebruikt.

## Informatie delen tussen SPA-componenten {#sharing-information-between-spa-components}

Componenten in een toepassing van één pagina moeten regelmatig informatie uitwisselen. Er zijn verschillende aanbevolen manieren om dit te doen, die als volgt worden opgesomd in toenemende mate van complexiteit.

* **Optie 1:** centraliseer de logica en uitzending aan de noodzakelijke componenten bijvoorbeeld, door React Context te gebruiken.
* **Optie 2:** de componentenstaten van het Aandeel door een staatsbibliotheek zoals Redux te gebruiken.
* **Optie 3:** hefboomwerking de objecten hiërarchie door de containercomponent aan te passen en uit te breiden.

## Volgende stappen {#next-steps}

* [ Begonnen het Worden met SPAs in AEM die Angular gebruiken ](getting-started-angular.md) toont hoe een basisKUUROORD wordt gebouwd om met de Redacteur van het KUUROORD in AEM te werken gebruikend Angular.
* [ het Overzicht van de Redacteur van het KUUROORD ](editor-overview.md) gaat in meer diepte in het communicatie model tussen AEM en het KUUROORD.
* [ WKND Project van het KUUROORD ](wknd-tutorial.md) is een geleidelijke leerprogramma die een eenvoudig project van het KUUROORD in AEM uitvoeren.
* [ Dynamisch Model aan de Afbeelding van de Component voor SPAs ](model-to-component-mapping.md) verklaart het dynamische model aan componentenafbeelding en hoe het binnen SPAs in AEM werkt.
* [ het Blauwdruk van het KUUROORD ](blueprint.md) biedt een diepe duik in hoe het KUUROORD SDK voor de werken van AEM voor het geval u SPAs in AEM voor een kader buiten React of Angular wilt uitvoeren of eenvoudig een dieper begrip zou willen.
