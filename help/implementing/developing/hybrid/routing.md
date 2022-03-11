---
title: SPA
description: Voor toepassingen van één pagina in AEM, is app verantwoordelijk voor het verpletteren. Dit document beschrijft het verpletterende mechanisme, het contract, en beschikbare opties.
exl-id: 1186b64e-11f8-43a6-bc75-450c4d7587ec
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# SPA{#spa-model-routing}

Voor toepassingen van één pagina in AEM, is app verantwoordelijk voor het verpletteren. Dit document beschrijft het verpletterende mechanisme, het contract, en beschikbare opties.

## Project routeren {#project-routing}

The App owns the routing and is then implemented by the project front end developers. Dit document beschrijft specifiek het verpletteren voor het model dat door de AEM server is teruggekeerd. De gegevensstructuur van het paginamodel stelt URL van het onderliggende middel bloot. The front end project can use any custom or third-party library providing routing functionalities. Zodra een route een fragment van model, een vraag aan verwacht `PageModelManager.getData()` kan worden uitgevoerd. Wanneer een modelroute is veranderd moet een gebeurtenis worden teweeggebracht om luisterbibliotheken zoals de Redacteur van de Pagina te waarschuwen.

## Architectuur {#architecture}

Voor een gedetailleerde beschrijving raadpleegt u de [PageModelManager](blueprint.md#pagemodelmanager) van het document SPA blauwdruk.

## ModelRouter {#modelrouter}

De `ModelRouter` - indien ingeschakeld - kapselt de API-functies van HTML5 History in `pushState` en `replaceState` om ervoor te zorgen dat een bepaald fragment van het model vooraf wordt opgehaald en toegankelijk is. It then notifies the registered front end component that the model has been modified.

## Manual vs Automatic Model Routing {#manual-vs-automatic-model-routing}

The `ModelRouter` automates the fetching of fragments of the model. Maar zoals elk geautomatiseerd gereedschap ook met beperkingen gepaard gaat. When needed the `ModelRouter` can be disabled or configured to ignore paths using meta properties (See the Meta Properties section of the [SPA Page Component](page-component.md) document). Front end developers can then implement their own model routing layer by requesting the `PageModelManager` to load any given fragment of model using the `getData()` function.

>[!CAUTION]
>
>De huidige versie van de `ModelRouter` alleen ondersteuning voor het gebruik van URL&#39;s die verwijzen naar het feitelijke bronnenpad van verzendmodel-entry-punten. Het steunt niet het gebruik van Vanity URLs of aliassen.

## Routeringscontract {#routing-contract}

De huidige implementatie is gebaseerd op de veronderstelling dat het SPA project HTML5 Geschiedenis API voor het verpletteren aan de verschillende toepassingspagina&#39;s gebruikt.

### Configuratie {#configuration}

De `ModelRouter` steunt het concept model verpletterend aangezien het op let `pushState` en `replaceState` aanroepen van vooraf ingestelde modelfragmenten. Intern activeert het de `PageModelManager` om het model te laden dat overeenkomt met een opgegeven URL en voert een `cq-pagemodel-route-changed` gebeurtenis waaraan andere modules kunnen luisteren.

Dit gedrag wordt standaard automatisch ingeschakeld. Om het onbruikbaar te maken, zou de SPA het volgende meta-bezit moeten teruggeven:

```
<meta property="cq:pagemodel_router" content="disable"\>
```

Note that every route of the SPA should correspond to an accessible resource in AEM (e.g., &quot; `/content/mysite/mypage"`) since the `PageModelManager` will automatically try to load the corresponding page model once the route is selected. Desondanks kan de SPA, indien nodig, ook een &quot;lijst van gewezen personen&quot;van routes bepalen die door `PageModelManager`:

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
