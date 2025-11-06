---
title: Aan de slag met SPA's in AEM met Angular
description: Dit artikel stelt een steekproeftoepassing van het KUUROORD voor, verklaart hoe het wordt samengesteld, en laat u met uw eigen KUUROORD snel in werking stellen gebruikend het kader van Angular.
exl-id: 8013ac2c-d1a7-4940-bb65-15e3ed7652d6
feature: Developing
role: Admin, Developer
index: false
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 0%

---


# Aan de slag met SPA&#39;s in AEM met Angular {#getting-started-with-spas-in-aem-using-angular}

Toepassingen van één pagina (SPAs) kunnen dwingende ervaringen voor websitegebruikers aanbieden. De ontwikkelaars willen plaatsen kunnen bouwen gebruikend het kader van het KUUROORD en de auteurs willen inhoud binnen AEM voor een plaats foutloos uitgeven die gebruikend het kader van het KUUROORD wordt gebouwd.

De auteurseigenschap van het KUUROORD biedt een uitvoerige oplossing voor het steunen van SPAs binnen AEM aan. Dit artikel stelt een vereenvoudigde toepassing van het KUUROORD op het kader van Angular voor, verklaart hoe het wordt samengesteld, toestaand u om snel met uw eigen KUUROORD in werking te stellen.

>[!NOTE]
>
>Dit artikel is gebaseerd op het Angular-kader. Voor het overeenkomstige document voor het Reageren kader zie [&#x200B; Begonnen Worden met SPAs in AEM - Reageer &#x200B;](getting-started-react.md).

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

Dit document zal door de structuur van een vereenvoudigde SPA lopen en zal illustreren hoe het werkt zodat kunt u dit begrip op uw eigen SPA toepassen.

## Afhankelijkheden, configuratie en gebouwen {#dependencies-configuration-and-building}

Naast de verwachte afhankelijkheid van Angular, kan de steekproefSPA extra bibliotheken gebruiken om de verwezenlijking van het KUUROORD efficiënter te maken.

### Afhankelijkheden {#dependencies}

Het `package.json` dossier bepaalt de vereisten van het algemene pakket van het KUUROORD. Hier worden de minimaal vereiste AEM-afhankelijkheden vermeld.

```
"dependencies": {
  "@adobe/aem-angular-editable-components": "~1.0.3",
  "@adobe/aem-spa-component-mapping": "~1.0.5",
  "@adobe/aem-spa-page-model-manager": "~1.0.3"
}
```

`aem-clientlib-generator` wordt gebruikt om het maken van clientbibliotheken automatisch te maken als onderdeel van het ontwikkelproces.

`"aem-clientlib-generator": "^1.4.1",`

Voor verdere details zie [&#x200B; aem-clientlib-generator op GitHub &#x200B;](https://github.com/wcm-io-frontend/aem-clientlib-generator).

`aem-clientlib-generator` wordt als volgt geconfigureerd in het `clientlib.config.js` -bestand.

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

Eigenlijk bouwend app gebruikt [&#x200B; Webpack &#x200B;](https://webpack.js.org/) voor transpilatie naast aem-client-clientlib-generator voor de automatische verwezenlijking van de cliëntbibliotheek. Daarom zal het bouwstijlbevel op lijken:

`"build": "ng build --build-optimizer=false && clientlib",`

Nadat het pakket is gemaakt, kan het worden geüpload naar een AEM-instantie.

### AEM Project Archetype {#aem-project-archetype}

Om het even welk project van AEM zou het [&#x200B; Archetype van het Project van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) moeten gebruiken, dat de projecten van het KUUROORD gebruikend React of Angular steunt en het KUUROORD SDK gebruikt.

## Toepassingsstructuur {#application-structure}

Als u de afhankelijkheden opneemt en uw app maakt zoals eerder beschreven, blijft er een werkende SPA-pakket over dat u kunt uploaden naar uw AEM-instantie.

De volgende sectie van dit document zal u door hoe een KUUROORD in AEM gestructureerd is, de belangrijke dossiers die de toepassing drijven, en hoe zij samenwerken.

Een vereenvoudigde afbeeldingscomponent wordt als voorbeeld gebruikt, maar alle componenten van de toepassing zijn op hetzelfde concept gebaseerd.

### app.module.ts {#app-module-ts}

Het ingangspunt in het SPA is het `app.module.ts` dossier dat hier wordt getoond vereenvoudigd om zich op de belangrijke inhoud te concentreren.

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

Het bestand `app.module.ts` is het beginpunt van de app en bevat de initiële projectconfiguratie en gebruikt `AppComponent` om de app op te starten.

#### Statische instantie {#static-instantiation}

Wanneer de component statisch wordt geconcretiseerd gebruikend het componentenmalplaatje, moet de waarde van het model tot de eigenschappen van de component worden overgegaan. De waarden van het model worden doorgegeven als kenmerken die later beschikbaar moeten zijn als componenteigenschappen.

### app.component.ts {#app-component-ts}

Zodra `app.module.ts` bootstraps `AppComponent` , kan het de app dan initialiseren, die hier in een vereenvoudigde versie wordt getoond om zich op de belangrijke inhoud te concentreren.

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

Door de pagina te verwerken, worden `app.component.ts` aanroepen `main-content.component.ts` hier in een vereenvoudigde versie weergegeven.

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

`MainComponent` neemt de JSON-representatie van het paginamodel op en verwerkt de inhoud om elk element van de pagina te buigen of te versieren. De verdere details op `Page` kunnen in het document [&#x200B; Vervagen van het KUUROORD &#x200B;](blueprint.md) worden gevonden.

### image.component.ts {#image-component-ts}

`Page` bestaat uit componenten. Als de JSON wordt ingesloten, kan de `Page` die componenten zoals `image.component.ts` verwerken, zoals hier wordt getoond.

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

Het centrale idee van SPAs in AEM is het idee om de componenten van SPA aan de componenten van AEM in kaart te brengen en de component bij te werken wanneer de inhoud (en omgekeerd) wordt gewijzigd. Zie het document [&#x200B; Overzicht van de Redacteur van het KUUROORD &#x200B;](editor-overview.md) voor een samenvatting van dit communicatie model.

`MapTo('my-angular-app/components/image')(Image, ImageEditConfig);`

De methode `MapTo` wijst de component SPA aan de component van AEM toe. Het ondersteunt het gebruik van één tekenreeks of een array van tekenreeksen.

`ImageEditConfig` is een configuratieobject dat de ontwerpmogelijkheden van een component helpt in te schakelen door de vereiste metagegevens voor de editor op te geven om plaatsaanduidingen te genereren

Als er geen inhoud is, worden etiketten verstrekt als placeholders om de lege inhoud te vertegenwoordigen.

#### Dynamisch doorgegeven eigenschappen {#dynamically-passed-properties}

De gegevens uit het model worden dynamisch doorgegeven als eigenschappen van de component.

### image.component.html {#image-component-html}

Ten slotte kan de afbeelding worden gerenderd in `image.component.html` .

```
// image.component.html
<img [src]="src" [alt]="alt" [title]="title"/>
```

## Informatie delen tussen SPA-componenten {#sharing-information-between-spa-components}

Componenten in een toepassing van één pagina moeten regelmatig informatie uitwisselen. Er zijn verschillende aanbevolen manieren om dit te doen, die als volgt worden opgesomd in toenemende mate van complexiteit.

* **Optie 1:** centraliseer de logica en uitzending aan de noodzakelijke componenten bijvoorbeeld, door een util klasse als zuivere object-oriented oplossing te gebruiken.
* **Optie 2:** de componentenstaten van het Aandeel door een staatsbibliotheek zoals NgRx te gebruiken.
* **Optie 3:** hefboomwerking de objecten hiërarchie door de containercomponent aan te passen en uit te breiden.

## Volgende stappen {#next-steps}

* [&#x200B; Begonnen het Worden met SPAs in AEM die Reageren &#x200B;](getting-started-react.md) gebruikt toont hoe een basisKUUROORD wordt gebouwd om met de Redacteur van het KUUROORD in AEM te werken gebruikend Reageren.
* [&#x200B; het Overzicht van de Redacteur van het KUUROORD &#x200B;](editor-overview.md) gaat in meer diepte in het communicatie model tussen AEM en het KUUROORD.
* [&#x200B; WKND Project van het KUUROORD &#x200B;](wknd-tutorial.md) is een geleidelijke leerprogramma die een eenvoudig project van het KUUROORD in AEM uitvoeren.
* [&#x200B; Dynamisch Model aan de Afbeelding van de Component voor SPAs &#x200B;](model-to-component-mapping.md) verklaart het dynamische model aan componentenafbeelding en hoe het binnen SPAs in AEM werkt.
* [&#x200B; het Blauwdruk van het KUUROORD &#x200B;](blueprint.md) biedt een diepe duik in hoe het KUUROORD SDK voor de werken van AEM voor het geval u SPAs in AEM voor een kader buiten React of Angular wilt uitvoeren of eenvoudig een dieper begrip zou willen.
