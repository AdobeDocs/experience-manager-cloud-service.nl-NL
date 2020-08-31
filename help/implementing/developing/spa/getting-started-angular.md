---
title: Begonnen het worden met SPAs in AEM Gebruikend Hoekig
description: Dit artikel stelt een toepassing van steekproefSPA voor, verklaart hoe het wordt samengesteld, en staat u toe om met uw eigen SPA snel in werking te stellen gebruikend het Hoekkader.
translation-type: tm+mt
source-git-commit: ccde1459090bb9f801d753cb7314e2bc7249f72e
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 0%

---


# Begonnen het worden met SPAs in AEM Gebruikend Hoekig {#getting-started-with-spas-in-aem-using-angular}

Toepassingen van één pagina (SPAs) kunnen dwingende ervaringen voor websitegebruikers aanbieden. De ontwikkelaars willen plaatsen kunnen bouwen gebruikend het kader van het KUUROORD en de auteurs willen inhoud binnen AEM voor een plaats foutloos uitgeven die gebruikend het kader van het KUUROORD wordt gebouwd.

De auteurseigenschap van het KUUROORD biedt een uitvoerige oplossing voor het steunen van SPAs binnen AEM aan. Dit artikel stelt een vereenvoudigde toepassing van het KUUROORD op het Hoekkader voor, verklaart hoe het wordt samengesteld, toestaand u om snel met uw eigen KUUROORD in werking te stellen.

>[!NOTE]
>
>Dit artikel is gebaseerd op het Hoekkader. Voor het overeenkomstige document voor het kader van de Reactie zie [Begonnen met SPAs in AEM - Reageren](getting-started-react.md).

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
>Een SPA die buiten AEM wordt ontwikkeld zal niet authorable zijn als het niet het contract van het inhoudsmodel eerbiedigt.

Dit document zal door de structuur van een vereenvoudigde KUUROORD lopen en zal illustreren hoe het werkt zodat kunt u dit begrip op uw eigen KUUROORD toepassen.

## Afhankelijkheden, configuratie en gebouwen {#dependencies-configuration-and-building}

Naast de verwachte Hoekafhankelijkheid, kan de steekproefSPA extra bibliotheken hefboomwerking maken om de verwezenlijking van het KUUROORD efficiënter te maken.

### Afhankelijkheden {#dependencies}

Het `package.json` dossier bepaalt de vereisten van het algemene pakket van SPA. De minimum vereiste AEM gebiedsdelen zijn hier vermeld.

```
"dependencies": {
  "@adobe/cq-angular-editable-components": "~1.0.3",
  "@adobe/cq-spa-component-mapping": "~1.0.3",
  "@adobe/cq-spa-page-model-manager": "~1.0.4"
}
```

Het `aem-clientlib-generator` is gebruikt om het maken van clientbibliotheken automatisch te maken als onderdeel van het ontwikkelproces.

`"aem-clientlib-generator": "^1.4.1",`

Meer details over het kunnen [op GitHub hier](https://github.com/wcm-io-frontend/aem-clientlib-generator)worden gevonden.

Het `aem-clientlib-generator` bestand is als volgt geconfigureerd in het `clientlib.config.js` bestand.

```
module.exports = {
    // default working directory (can be changed per 'cwd' in every asset option)
    context: __dirname,

    // path to the clientlib root folder (output)
    clientLibRoot: "./../content/jcr_root/apps/my-angular-app/clientlibs",

    libs: {
        name: "my-angular-app",
        allowProxy: true,
        categories: ["my-angular-app"],
        embed: ["my-angular-app.responsivegrid"],
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

Bij het ontwikkelen van de app wordt [Webpack](https://webpack.js.org/) gebruikt voor transplantatie naast de aem-clientlib-generator voor het automatisch maken van clientbibliotheken. Daarom zal het bouwstijlbevel op lijken:

`"build": "ng build --build-optimizer=false && clientlib",`

Nadat het pakket is gemaakt, kan het naar een AEM-instantie worden geüpload.

### Projectarchetype AEM {#aem-project-archetype}

Om het even welk AEM project zou hefboomwerking het [AEM Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)van het Project, dat de projecten van het KUUROORD gebruikend React of Angular steunt en hefboomwerkingen SDK van het KUUROORD.

## Toepassingsstructuur {#application-structure}

Als u de afhankelijkheden opneemt en uw app maakt zoals eerder beschreven, blijft er een werkende SPA-pakket over dat u kunt uploaden naar uw AEM-instantie.

De volgende sectie van dit document zal u door hoe een KUUROORD in AEM gestructureerd is, de belangrijke dossiers die de toepassing drijven, en hoe zij samenwerken.

Een vereenvoudigde afbeeldingscomponent wordt als voorbeeld gebruikt, maar alle componenten van de toepassing zijn op hetzelfde concept gebaseerd.

### app.module.ts {#app-module-ts}

Het ingangspunt in het KUUROORD is het `app.module.ts` dossier hier wordt getoond vereenvoudigd om zich op de belangrijke inhoud te concentreren die.

```
// app.module.ts
import { BrowserModule, BrowserTransferStateModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { SpaAngularEditableComponentsModule } from '@adobe/cq-angular-editable-components';
import { AppRoutingModule } from './app-routing.module';

@NgModule({
  imports: [ BrowserModule.withServerTransition({ appId: 'my-angular-app' }),
    SpaAngularEditableComponentsModule,
    AppRoutingModule,
    BrowserTransferStateModule ],
  providers: ...,
  declarations: [ ... ],
  entryComponents: [ ... ],
  bootstrap: [ AppComponent ]
})
export class AppModule {}
```

Het `app.module.ts` bestand is het beginpunt van de app en bevat de initiële projectconfiguratie en gebruikt `AppComponent` om de app op te starten.

#### Statische instantie {#static-instantiation}

Wanneer de component statisch wordt geconcretiseerd gebruikend het componentenmalplaatje, moet de waarde van het model tot de eigenschappen van de component worden overgegaan. De waarden van het model worden doorgegeven als kenmerken die later beschikbaar moeten zijn als componenteigenschappen.

### app.component.ts {#app-component-ts}

Zodra `app.module.ts` bootstraps `AppComponent`, kan het dan de App initialiseren, die hier in een vereenvoudigde versie wordt getoond om zich op de belangrijke inhoud te concentreren.

```
// app.component.ts
import { Component } from '@angular/core';
import { ModelManager } from '@adobe/cq-spa-page-model-manager';
import { Constants } from "@adobe/cq-angular-editable-components";

@Component({
  selector: 'app-root',
  template: `
    <router-outlet></router-outlet>
  `
})

export class AppComponent {
  items;
  itemsOrder;
  path;

  constructor() {
    ModelManager.initialize().then(this.updateData.bind(this));
  }

  private updateData(model) {
    this.path = model[Constants.PATH_PROP];
    this.items = model[Constants.ITEMS_PROP];
    this.itemsOrder = model[Constants.ITEMS_ORDER_PROP];
  }
}
```

### main-content.component.ts {#main-content-component-ts}

Door de pagina te verwerken, `app.component.ts` vraag `main-content.component.ts` hier in een vereenvoudigde versie wordt vermeld die.

```
import { Component } from '@angular/core';
import { ModelManagerService }     from '../model-manager.service';
import { ActivatedRoute } from '@angular/router';
import { Constants } from "@adobe/cq-angular-editable-components";

@Component({
  selector: 'app-main',
  template: `
    <aem-page class="structure-page" [attr.data-cq-page-path]="path" [cqPath]="path" [cqItems]="items" [cqItemsOrder]="itemsOrder" ></aem-page>
  `
})

export class MainContentComponent {
  items;
  itemsOrder;
  path;

  constructor( private route: ActivatedRoute,
    private modelManagerService: ModelManagerService) {
    this.modelManagerService.getData({ path: this.route.snapshot.data.path }).then((data) => {
      this.path = data[Constants.PATH_PROP];
      this.items = data[Constants.ITEMS_PROP];
      this.itemsOrder = data[Constants.ITEMS_ORDER_PROP];
    });
  }
}
```

De code `MainComponent` voegt de JSON-representatie van het paginamodel in en verwerkt de inhoud om elk element van de pagina in te pakken of te versieren. Nadere details over het `Page` kunnen in het document [SPA Blueprint](blueprint.md)worden gevonden.

### image.component.ts {#image-component-ts}

Het `Page` bestaat uit componenten. Met JSON ingebed, `Page` kan de component die componenten zoals `image.component.ts` zoals hier getoond verwerken.

```
/// image.component.ts
import { Component, Input } from '@angular/core';

const ImageEditConfig = {

    emptyLabel: 'Image',

    isEmpty: function(cqModel) {
        return !cqModel || !cqModel.src || cqModel.src.trim().length < 1;
    }
};

@Component({
  selector: 'app-image',
  templateUrl: './image.component.html',
})

export class ImageComponent {
  @Input() src: string;
  @Input() alt: string;
  @Input() title: string;
}

MapTo('my-angular-app/components/image')(ImageComponent, ImageEditConfig);
```

Het centrale idee van SPAs in AEM is het idee om de componenten van SPA aan AEM componenten in kaart te brengen en de component bij te werken wanneer de inhoud (en vice versa) wordt gewijzigd. Zie het Overzicht [van de Redacteur van het document](editor-overview.md) SPA van dit communicatie model.

`MapTo('my-angular-app/components/image')(Image, ImageEditConfig);`

De `MapTo` methode brengt de component van het KUUROORD aan de AEM in kaart. Het ondersteunt het gebruik van één tekenreeks of een array van tekenreeksen.

`ImageEditConfig` is een configuratievoorwerp dat tot het toelaten van de auteursmogelijkheden van een component bijdraagt door de noodzakelijke meta-gegevens voor de redacteur te verstrekken om placeholders te produceren

Als er geen inhoud is, worden etiketten verstrekt als placeholders om de lege inhoud te vertegenwoordigen.

#### Dynamisch doorgegeven eigenschappen {#dynamically-passed-properties}

De gegevens uit het model worden dynamisch doorgegeven als eigenschappen van de component.

### image.component.html {#image-component-html}

Tot slot kan de afbeelding worden weergegeven in `image.component.html`.

```
// image.component.html
<img [src]="src" [alt]="alt" [title]="title"/>
```

## Informatie delen tussen SPA-componenten {#sharing-information-between-spa-components}

Componenten in een toepassing van één pagina moeten regelmatig informatie uitwisselen. Er zijn verschillende aanbevolen manieren om dit te doen, die als volgt worden opgesomd in toenemende mate van complexiteit.

* **Optie 1:** Centraliseer de logica en uitzending aan de noodzakelijke componenten bijvoorbeeld door een util klasse als zuivere object-oriented oplossing te gebruiken.
* **Optie 2:** De componentenstaten van het aandeel door een staatsbibliotheek zoals NgRx te gebruiken.
* **Optie 3:** Gebruik de objecthiërarchie door de containercomponent aan te passen en uit te breiden.

## Volgende stappen {#next-steps}

* [Begonnen het worden met SPAs in AEM gebruiken van Reageren](getting-started-react.md) toont hoe een basisKUUROORD wordt gebouwd om met de Redacteur van het KUUROORD in AEM te werken gebruikend Reageren.
* [Het Overzicht](editor-overview.md) van de Redacteur van het KUUROORD gaat in meer diepte in het communicatie model tussen AEM en het KUUROORD.
* [Het Project](wknd-tutorial.md) van het KND SPA is een geleidelijke leerprogramma die een eenvoudig project van het KUUROORD in AEM uitvoeren.
* [Het dynamische Model aan de Afbeelding van de Component voor SPAs](model-to-component-mapping.md) verklaart het dynamische model aan componentenafbeelding en hoe het binnen SPAs in AEM werkt.
* [Het Vervagen](blueprint.md) van het KUUROORD biedt een diepe duik in hoe het KUUROORD SDK voor AEM werkt voor het geval u wenst om SPAs in AEM voor een kader buiten React of Angular uit te voeren of eenvoudig een dieper begrip zou willen.
