---
title: Aan de slag met SPA in AEM Angular gebruiken
description: Dit artikel presenteert een voorbeeld SPA toepassing, legt uit hoe het wordt samengesteld, en staat u toe om met uw eigen SPA snel het kader van de Angular in gebruik te nemen.
exl-id: 8013ac2c-d1a7-4940-bb65-15e3ed7652d6
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 0%

---

# Aan de slag met SPA in AEM Angular gebruiken {#getting-started-with-spas-in-aem-using-angular}

Toepassingen op één pagina (SPA) kunnen aantrekkelijke ervaringen bieden voor websitegebruikers. Ontwikkelaars willen sites kunnen maken met behulp van SPA frameworks en auteurs willen inhoud naadloos bewerken binnen AEM voor een site die is gebouwd met behulp van SPA frameworks.

De SPA ontwerpfunctie biedt een uitgebreide oplossing voor het ondersteunen van SPA binnen AEM. Dit artikel presenteert een vereenvoudigde SPA toepassing over het kader van de Angular, verklaart hoe het wordt samengesteld, die u toestaat om met uw eigen SPA snel in werking te stellen.

>[!NOTE]
>
>Dit artikel is gebaseerd op het kader van de Angular. Zie voor het bijbehorende document voor het React-framework [Aan de slag met SPA in AEM - Reageren](getting-started-react.md).

## Inleiding {#introduction}

Dit artikel vat het basisfunctioneren van een eenvoudige SPA en het minimum samen dat u moet weten om van u lopend te krijgen.

Raadpleeg de volgende documenten voor meer informatie over SPA werken in AEM:

* [SPA Inleiding en Analyse](introduction.md)
* [Overzicht SPA Editor](editor-overview.md)
* [SPA](blueprint.md)

>[!NOTE]
>
>Om inhoud binnen een SPA te kunnen schrijven, moet de inhoud in AEM worden opgeslagen en door het inhoudsmodel worden vrijgegeven.
>
>Een SPA die buiten AEM is ontwikkeld, is niet aanvaardbaar als het contract voor het inhoudsmodel niet wordt nageleefd.

Dit document loopt door de structuur van een vereenvoudigde SPA en illustreert hoe het werkt zodat u deze interpretatie op uw eigen SPA kunt toepassen.

## Afhankelijkheden, configuratie en gebouwen {#dependencies-configuration-and-building}

Naast de verwachte afhankelijkheid van Angulars, kan de steekproef SPA extra bibliotheken gebruiken om de verwezenlijking van SPA efficiënter te maken.

### Afhankelijkheden {#dependencies}

De `package.json` het dossier bepaalt de vereisten van het algemene SPA pakket. De minimum vereiste AEM gebiedsdelen zijn hier vermeld.

```
"dependencies": {
  "@adobe/aem-angular-editable-components": "~1.0.3",
  "@adobe/aem-spa-component-mapping": "~1.0.5",
  "@adobe/aem-spa-page-model-manager": "~1.0.3"
}
```

De `aem-clientlib-generator` wordt gebruikt om het maken van clientbibliotheken automatisch te maken als onderdeel van het ontwikkelproces.

`"aem-clientlib-generator": "^1.4.1",`

Meer informatie hierover is te vinden [op GitHub hier](https://github.com/wcm-io-frontend/aem-clientlib-generator).

De `aem-clientlib-generator` is geconfigureerd in de `clientlib.config.js` bestand als volgt.

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

Eigenlijk de app-functies ontwikkelen [Webpack](https://webpack.js.org/) voor de omzetting in aanvulling op de aem-clientlib-generator voor het automatisch maken van clientbibliotheken. Daarom zal het bouwstijlbevel op lijken:

`"build": "ng build --build-optimizer=false && clientlib",`

Nadat het pakket is gemaakt, kan het naar een AEM-instantie worden geüpload.

### Projectarchetype AEM {#aem-project-archetype}

Elk AEM project moet [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html), die SPA projecten met React of Angular steunt en hefboomwerkingen de SPA SDK.

## Toepassingsstructuur {#application-structure}

Als u de afhankelijkheden opneemt en uw app samenstelt zoals eerder beschreven, blijft er een werkende SPA over die u kunt uploaden naar uw AEM.

In het volgende gedeelte van dit document wordt uitgelegd hoe een SPA in AEM is gestructureerd, welke belangrijke bestanden de toepassing sturen en hoe deze samenwerken.

Een vereenvoudigde afbeeldingscomponent wordt als voorbeeld gebruikt, maar alle componenten van de toepassing zijn op hetzelfde concept gebaseerd.

### app.module.ts {#app-module-ts}

Het ingangspunt in de SPA is de `app.module.ts` bestand dat hier wordt weergegeven, is vereenvoudigd zodat u zich kunt concentreren op de belangrijke inhoud.

```
// app.module.ts
import { BrowserModule, BrowserTransferStateModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { SpaAngularEditableComponentsModule } from '@adobe/aem-angular-editable-components';
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

De `app.module.ts` het dossier is het uitgangspunt van app en bevat de aanvankelijke projectconfiguratie en het gebruik `AppComponent` om de app op te starten.

#### Statische instantie {#static-instantiation}

Wanneer de component statisch wordt geconcretiseerd gebruikend het componentenmalplaatje, moet de waarde van het model tot de eigenschappen van de component worden overgegaan. De waarden van het model worden doorgegeven als kenmerken die later beschikbaar moeten zijn als componenteigenschappen.

### app.component.ts {#app-component-ts}

Eenmaal `app.module.ts` bootstraps `AppComponent`kan de toepassing vervolgens worden geïnitialiseerd. Deze versie wordt hier in een vereenvoudigde versie weergegeven en richt zich op de belangrijke inhoud.

```
// app.component.ts
import { Component } from '@angular/core';
import { ModelManager } from '@adobe/aem-spa-page-model-manager';
import { Constants } from "@adobe/aem-angular-editable-components";

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

Door de pagina te verwerken, `app.component.ts` oproepen `main-content.component.ts` hier in een vereenvoudigde versie vermeld.

```
import { Component } from '@angular/core';
import { ModelManagerService }     from '../model-manager.service';
import { ActivatedRoute } from '@angular/router';
import { Constants } from "@adobe/aem-angular-editable-components";

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

De `MainComponent` Voert de JSON-representatie van het paginamodel in en verwerkt de inhoud om elk element van de pagina om te buigen of te versieren. Meer informatie over de `Page` te vinden in het document [SPA](blueprint.md).

### image.component.ts {#image-component-ts}

De `Page` bestaat uit componenten. Met de JSON ingepakt, `Page` kan componenten zoals `image.component.ts` zoals u hier ziet.

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

Het centrale idee van SPA in AEM is het idee om SPA componenten aan AEM componenten in kaart te brengen en de component bij te werken wanneer de inhoud wordt gewijzigd (en vice versa). Zie het document [Overzicht SPA Editor](editor-overview.md) voor een samenvatting van dit communicatiemodel.

`MapTo('my-angular-app/components/image')(Image, ImageEditConfig);`

De `MapTo` methode wijst de SPA component aan de AEM component toe. Het ondersteunt het gebruik van één tekenreeks of een array van tekenreeksen.

`ImageEditConfig` is een configuratievoorwerp dat tot het toelaten van de auteursmogelijkheden van een component bijdraagt door de noodzakelijke meta-gegevens voor de redacteur te verstrekken om placeholders te produceren

Als er geen inhoud is, worden etiketten verstrekt als placeholders om de lege inhoud te vertegenwoordigen.

#### Dynamisch doorgegeven eigenschappen {#dynamically-passed-properties}

De gegevens uit het model worden dynamisch doorgegeven als eigenschappen van de component.

### image.component.html {#image-component-html}

Ten slotte kan de afbeelding worden gerenderd in `image.component.html`.

```
// image.component.html
<img [src]="src" [alt]="alt" [title]="title"/>
```

## Informatie delen tussen SPA componenten {#sharing-information-between-spa-components}

Componenten in een toepassing van één pagina moeten regelmatig informatie uitwisselen. Er zijn verschillende aanbevolen manieren om dit te doen, die als volgt worden opgesomd in toenemende mate van complexiteit.

* **Optie 1:** Centraliseer de logica en uitzending aan de noodzakelijke componenten bijvoorbeeld door een util klasse als zuivere object-oriented oplossing te gebruiken.
* **Optie 2:** De componentenstaten van het aandeel door een staatsbibliotheek zoals NgRx te gebruiken.
* **Optie 3:** Gebruik de objecthiërarchie door de containercomponent aan te passen en uit te breiden.

## Volgende stappen {#next-steps}

* [Aan de slag met SPA in AEM met Reageren](getting-started-react.md) toont hoe een basis SPA wordt gebouwd om met de SPARedacteur in AEM te werken die Reageren gebruiken.
* [Overzicht SPA Editor](editor-overview.md) gaat dieper in het communicatie model tussen AEM en de SPA.
* [WKND SPA Project](wknd-tutorial.md) is een geleidelijke zelfstudie die een eenvoudig SPA project in AEM implementeert.
* [Dynamisch model naar componenttoewijzing voor SPA](model-to-component-mapping.md) verklaart het dynamische model aan componentenafbeelding en hoe het binnen SPA in AEM werkt.
* [SPA](blueprint.md) biedt een diepgaande duik in hoe de SPA SDK voor AEM werkt voor het geval u SPA in AEM voor een kader buiten React of Angular wilt uitvoeren of eenvoudig een dieper begrip zou willen.
