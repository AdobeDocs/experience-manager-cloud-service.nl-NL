---
title: De RemotePage-component
description: De component RemotePage is een component van de douanepagina voor het uitgeven van ver React SPA binnen AEM.
exl-id: d3465592-0392-49b0-b49d-de93983c1d6e
feature: Developing
role: Admin, Architect, Developer
index: false
source-git-commit: 7a9d947761b0473f5ddac3c4d19dfe5bed5b97fe
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---


# De RemotePage-component {#remote-page-component}

Wanneer het beslissen van [ welk niveau van integratie ](/help/implementing/developing/headful-headless.md) u tussen uw externe SPA en AEM zou willen hebben, is het vaak duidelijk dat u het KUUROORD binnen AEM moet kunnen bekijken en uitgeven. De component RemotePage is alleen voor dit doel een aangepaste pagina-component.

{{ue-over-spa}}

## Overzicht {#overview}

De component RemotePage haalt alle noodzakelijke activa van de geproduceerde toepassing `asset-manifest.json` en gebruikt dit voor het teruggeven van het KUUROORD binnen AEM.

* Met RemotePage kunt u de scripts en opmaakmodellen van een SPA in de hoofdtekst van een AEM Page-component injecteren.
* Met de Virtual Front Components kunt u secties markeren als bewerkbaar in de AEM SPA Editor.
* Samen, kan een SPA die op een verschillend domein wordt ontvangen editable in AEM worden gemaakt.

Zie het artikel [ Uitgevend een Externe KUUROORD binnen AEM ](editing-external-spa.md) voor meer details over editable, externe SPAs in AEM.

## Vereisten {#requirements}

* CORS in ontwikkeling inschakelen
* Externe URL configureren in Pagina-eigenschappen
* De SPA renderen in AEM
* De webtoepassing moet een bundler-elementmanifest gebruiken, zoals een van de volgende, en een `asset-manifest.json` -bestand in de hoofdmap van het domein weergeven dat in een `entrypoints property` alle CSS- en JS-bestanden vermeldt die moeten worden geladen:
   * https://github.com/shellscape/webpack-manifest-plugin
   * https://github.com/webdeveric/webpack-assets-manifest
   * https://github.com/mugi-uno/parcel-plugin-bundle-manifest

     ![ entrypoints bezitsvoorbeeld ](assets/asset-manifest-entrypoints.png)
* De toepassing moet kunnen initialiseren in een `<div id="root"></div>` onder het `body` -element. Als er een andere opmaak wordt verwacht voor de app om te instantiëren, moet deze dienovereenkomstig worden aangepast in de HTML-scripts van de proxycomponent met een `sling:resourceSuperType="spa-project-core/components/remotepage` .

## Beperkingen {#limitations}

* De component RemotePage verwacht dat de implementatie activa-manifest zoals hier gevonden [&#128279;](https://github.com/shellscape/webpack-manifest-plugin) verstrekt. De component RemotePage is echter alleen getest om te werken met het React-framework (en Next.js als de volgende component op afstand) en biedt daarom geen ondersteuning voor het extern laden van toepassingen vanuit andere frameworks, zoals Angular.
* Interne CSS die is gedefinieerd in het HTML-hoofdbestand van de toepassing en inline CSS op het DOM-hoofdknooppunt zijn niet beschikbaar bij externe rendering in AEM.

## Technische details {#technical-details}

Zoals de rest van het project van AEM SPA, is de Component RemotePage open bron. Voor de volledige technische details van de Component RemotePage, [ zie de bewaarplaats GitHub ](https://github.com/adobe/aem-spa-project-core/tree/master/ui.apps/src/main/content/jcr_root/apps/spa-project-core/components/remotepage).
