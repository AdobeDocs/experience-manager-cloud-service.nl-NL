---
title: SPA
description: Voor toepassingen van één pagina in AEM, is app verantwoordelijk voor het verpletteren. Dit document beschrijft het verpletterende mechanisme, het contract, en beschikbare opties.
exl-id: 1186b64e-11f8-43a6-bc75-450c4d7587ec
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# SPA{#spa-model-routing}

Voor toepassingen van één pagina in AEM, is app verantwoordelijk voor het verpletteren. Dit document beschrijft het verpletterende mechanisme, het contract, en beschikbare opties.

## Project routeren {#project-routing}

App bezit het verpletteren en dan uitgevoerd door de ontwikkelaars van het projectfront. Dit document beschrijft specifiek het verpletteren voor het model dat door de AEM server is teruggekeerd. De gegevensstructuur van het paginamodel stelt URL van het onderliggende middel bloot. Het front-end project kan om het even welke douane of derdebibliotheek gebruiken die verpletterende functionaliteit verstrekt. Zodra een route een fragment van model, een vraag aan verwacht `PageModelManager.getData()` kan worden uitgevoerd. Wanneer een modelroute is veranderd moet een gebeurtenis worden teweeggebracht om luisterbibliotheken zoals de Redacteur van de Pagina te waarschuwen.

## Architectuur {#architecture}

Zie voor een gedetailleerde beschrijving [PageModelManager](blueprint.md#pagemodelmanager) van het document SPA blauwdruk.

## ModelRouter {#modelrouter}

De `ModelRouter` - indien ingeschakeld - kapselt de API-functies van HTML5 History in `pushState` en `replaceState` om ervoor te zorgen dat een bepaald fragment van het model vooraf wordt opgehaald en toegankelijk is. Vervolgens wordt de geregistreerde front-end component meegedeeld dat het model is gewijzigd.

## Handmatig versus automatisch model routeren {#manual-vs-automatic-model-routing}

De `ModelRouter` automatiseert het ophalen van fragmenten van het model. Maar zoals elk geautomatiseerd gereedschap ook met beperkingen gepaard gaat. Indien nodig `ModelRouter` kan worden uitgeschakeld of geconfigureerd om paden te negeren met gebruik van meta-eigenschappen (zie de sectie Meta-eigenschappen van het dialoogvenster [SPA](page-component.md) document). De voorste eindontwikkelaars kunnen hun eigen model dat laag verplettert dan uitvoeren door om `PageModelManager` om een bepaald fragment van het model te laden met de `getData()` functie.

>[!CAUTION]
>
>De huidige versie van de `ModelRouter` alleen ondersteuning voor het gebruik van URL&#39;s die verwijzen naar het feitelijke bronnenpad van verzendmodel-entry-punten. Het ondersteunt het gebruik van URL&#39;s of aliassen van het type Vanity niet.

## Routeringscontract {#routing-contract}

De huidige implementatie is gebaseerd op de veronderstelling dat het SPA project HTML5 Geschiedenis API voor het verpletteren aan de verschillende toepassingspagina&#39;s gebruikt.

### Configuratie {#configuration}

De `ModelRouter` steunt het concept model verpletterend aangezien het op let `pushState` en `replaceState` aanroepen van vooraf ingestelde modelfragmenten. Intern activeert het de `PageModelManager` om het model te laden dat overeenkomt met een opgegeven URL en voert een `cq-pagemodel-route-changed` gebeurtenis waaraan andere modules kunnen luisteren.

Dit gedrag wordt standaard automatisch ingeschakeld. Om het onbruikbaar te maken, zou de SPA het volgende meta-bezit moeten teruggeven:

```
<meta property="cq:pagemodel_router" content="disabled"\>
```

Elke route van de SPA moet overeenkomen met een toegankelijke bron in AEM (bijvoorbeeld &quot; `/content/mysite/mypage"`) sinds de `PageModelManager` zal automatisch proberen om het overeenkomstige paginamodel te laden zodra de route wordt geselecteerd. Desondanks kan de SPA, indien nodig, ook een &quot;lijst van gewezen personen&quot;van routes bepalen die door `PageModelManager`:

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
