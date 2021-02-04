---
title: De RemotePage-component
description: De component RemotePage is een aangepaste pagina-component voor het bewerken van SPA op afstand in AEM.
translation-type: tm+mt
source-git-commit: 6a88b93a4005b858eec222fd7ae15df9db269d31
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 1%

---

# De RemotePage-component {#remote-page-component}

Wanneer het beslissen van [welk niveau van integratie](/help/implementing/developing/headful-headless.md) u tussen uw externe SPA en AEM zou willen hebben, is het vaak duidelijk dat u de SPA binnen AEM moet kunnen bekijken en uitgeven. De component RemotePage is alleen voor dit doel een aangepaste pagina-component.

## Overzicht {#overview}

De component RemotePage haalt alle noodzakelijke activa van de geproduceerde `asset-manifest.json` van de toepassing en gebruikt dit voor het teruggeven van de SPA binnen AEM.

## Vereisten {#requirements}

* CORS in ontwikkeling inschakelen
* Externe URL configureren in Pagina-eigenschappen
* De SPA renderen in AEM

## Beperkingen {#limitations}

* De huidige implementatie van de component RemotePage ondersteunt alleen externe React-toepassingen.
* Interne CSS die is gedefinieerd in het HTML-hoofdbestand van de toepassing en inline CSS op het DOM-hoofdknooppunt zijn niet beschikbaar bij externe rendering in AEM.

## Technische details {#technical-details}

Net als de rest van het AEM SPA-project is de RemotePage-component een open bron. Voor de volledige technische details van de Component RemotePage, [te zien gelieve de bewaarplaats GitHub.](https://github.com/adobe/aem-spa-project-core/tree/master/ui.apps/src/main/content/jcr_root/apps/spa-project-core/components/remotepage)
