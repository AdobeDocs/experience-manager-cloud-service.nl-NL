---
title: SPA-paginacomponent
description: In een KUUROORD verstrekt de paginacomponent niet de elementen van HTML van zijn kindcomponenten, maar in plaats daarvan delegeert dit aan het kader van het KUUROORD. Dit document verklaart hoe dit tot de paginacomponent van een SPA uniek maakt.
translation-type: tm+mt
source-git-commit: c075bcc415b68ba0deaeca61d6d179bd7263ca5f
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 0%

---


# SPA-paginacomponent {#spa-page-component}

De paginacomponent voor een SPA verstrekt niet de elementen van HTML van zijn kindcomponenten via een JSP of HTML- dossier en middelvoorwerpen. Deze verrichting wordt gedelegeerd aan het kader van het KUUROORD. De representatie van onderliggende componenten wordt opgehaald als een JSON-gegevensstructuur (dat wil zeggen het model). De componenten van het KUUROORD worden dan toegevoegd aan de pagina volgens het verstrekte model JSON. De oorspronkelijke compositie van de hoofdtekst van de paginacomponent verschilt daarom van de vooraf weergegeven HTML-tegenhangers.

## Paginamodel beheren {#page-model-management}

De resolutie en het beheer van het paginamodel worden gedelegeerd aan een opgegeven [`PageModelManager`](blueprint.md#pagemodelmanager) module. Het KUUROORD moet met de `PageModelManager` module in wisselwerking staan wanneer het initialiseert om het aanvankelijke paginamodel en register voor modelupdates te halen - meestal geproduceerd wanneer de auteur de pagina via de Redacteur van de Pagina uitgeeft. Het `PageModelManager` is toegankelijk door het project van het KUUUROORD als npm pakket. Als tolk tussen AEM en de SPA, `PageModelManager` is het bedoeld om de SPA te begeleiden.

Om toe te staan dat de pagina wordt geschreven, `cq.authoring.pagemodel.messaging` moet een genoemde cliëntbibliotheek worden toegevoegd om een communicatie kanaal tussen het KUUROORD en de paginaredacteur te verstrekken. Als de de paginacomponent van het KUUROORD van de pagina wcm/kerncomponent erft dan zijn er de volgende opties om de categorie van de `cq.authoring.pagemodel.messaging` cliëntbibliotheek beschikbaar te maken:

* Als de sjabloon bewerkbaar is, voegt u de categorie van de clientbibliotheek toe aan het paginabeleid.
* Voeg de categorie van de cliëntbibliotheek toe gebruikend de `customfooterlibs.html` component van de pagina.

Vergeet niet de opname van de `cq.authoring.pagemodel.messaging` categorie te beperken tot de context van de pagina-editor.

## Gegevenstype communicatie {#communication-data-type}

Het gegevenstype voor communicatie wordt ingesteld als een HTML-element binnen de component AEM pagina met behulp van het `data-cq-datatype` kenmerk. Wanneer het gegevenstype van communicatiegegevens is ingesteld op JSON, bereiken de aanvragen van de GET de eindpunten van het verzendmodel van een component. Nadat een update in de pagina-editor plaatsvindt, wordt de JSON-representatie van de bijgewerkte component verzonden naar de bibliotheek Paginamodel. De bibliotheek van het Model van de Pagina waarschuwt dan het KUUROORD van updates.

**SPA-paginacomponent -`body.html`**

```
<div id="page"></div>
```

Naast het zijn goede praktijken om de generatie van DOM niet uit te stellen, vereist het kader van het KUUROORD dat de manuscripten aan het eind van het lichaam worden toegevoegd.

**SPA-paginacomponent -`customfooterlibs.html`**

```
<sly data-sly-use.clientLib="${'/libs/granite/sightly/templates/clientlib.html'}"></sly>
<sly data-sly-test="${wcmmode.edit || wcmmode.preview}"
     data-sly-call="${clientLib.js @ categories='cq.authoring.pagemodel.messaging'}"></sly>
<sly data-sly-call="${clientLib.js @ categories='we-retail-journal-react'}"></sly>
```

De eigenschappen van het meta-middel die de inhoud van het KUUROORD beschrijven:

**SPA-paginacomponent -`customheaderlibs.html`**

```
<meta property="cq:datatype" data-sly-test="${wcmmode.edit || wcmmode.preview}" content="JSON"/>
<meta property="cq:wcmmode" data-sly-test="${wcmmode.edit}" content="edit"/>
<meta property="cq:wcmmode" data-sly-test="${wcmmode.preview}" content="preview"/>
<meta property="cq:pagemodel_root_url" data-sly-use.page="com.adobe.cq.sample.spa.journal.models.AppPage" content="${page.rootUrl}"/>
<sly data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html">
    <sly data-sly-call="${clientlib.css @ categories='we-retail-journal-react'}"/>
</sly>
```

>[!NOTE]
>
>De standaardmodelkiezer wordt statisch ingesteld bij het aanvragen van de representatie van een component in het verkoopmodel.

## Eigenschappen van meta {#meta-properties}

* `cq:wcmmode`: WCM-modus van de editors (bijvoorbeeld pagina, sjabloon)
* `cq:pagemodel_root_url`: URL van het basismodel van de app. Cruciaal bij directe toegang tot een onderliggende pagina, aangezien het onderliggende paginamodel een fragment is van het basismodel van de app. Vervolgens stelt de toepassing het oorspronkelijke model systematisch opnieuw samen, zodat de toepassing vanaf het hoofdinvoerpunt wordt ingevoerd. `PageModelManager`
* `cq:pagemodel_router`: Het inschakelen of uitschakelen [`ModelRouter`](routing.md) van de `PageModelManager` bibliotheek
* `cq:pagemodel_route_filters`: Door komma&#39;s gescheiden lijsten of reguliere expressies om routes te bieden die de gebruiker [`ModelRouter`](routing.md) moet negeren.

## Overlaysynchronisatie van paginaeditor {#page-editor-overlay-synchronization}

De synchronisatie van de overlays wordt gegarandeerd door dezelfde Mutation Observer die de `cq.authoring.page` categorie biedt.

## Sling Model JSON Geëxporteerde structuurconfiguratie {#sling-model-json-exported-structure-configuration}

Wanneer de verpletterende mogelijkheden worden toegelaten, is de veronderstelling dat de uitvoer JSON van SPA de verschillende routes van de toepassing dankzij de uitvoer JSON van de AEM navigatiecomponent bevat. De output JSON van de AEM navigatiecomponent kan in het de inhoudbeleid van de wortelpagina van het KUUROORD door de volgende twee eigenschappen worden gevormd:

* `structureDepth`: Aantal dat overeenkomt met de diepte van de geëxporteerde structuur
* `structurePatterns`: Regex van array van regexes die overeenkomt met de pagina die geëxporteerd moet worden
