---
title: SPA
description: Voor toepassingen van één pagina in AEM, is app verantwoordelijk voor het verpletteren. Dit document beschrijft het verpletterende mechanisme, het contract, en beschikbare opties.
translation-type: tm+mt
source-git-commit: c075bcc415b68ba0deaeca61d6d179bd7263ca5f
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---


# SPA{#spa-model-routing}

Voor toepassingen van één pagina in AEM, is app verantwoordelijk voor het verpletteren. Dit document beschrijft het verpletterende mechanisme, het contract, en beschikbare opties.

## Project routeren {#project-routing}

App bezit het verpletteren en dan uitgevoerd door de ontwikkelaars van het projectfront. Dit document beschrijft specifiek het verpletteren voor het model dat door de AEM server is teruggekeerd. De gegevensstructuur van het paginamodel stelt URL van het onderliggende middel bloot. Het front-end project kan om het even welke douane of derdebibliotheek gebruiken die verpletterende functionaliteit verstrekt. Zodra een route een fragment van model verwacht, kan een vraag aan de `PageModelManager.getData()` functie worden gemaakt. Wanneer een modelroute is veranderd moet een gebeurtenis worden teweeggebracht om luisterbibliotheken zoals de Redacteur van de Pagina te waarschuwen.

## Architectuur {#architecture}

Voor een gedetailleerde beschrijving raadpleegt u de sectie [PageModelManager](blueprint.md#pagemodelmanager) van het document SPA.

## ModelRouter {#modelrouter}

De API-functies van HTML5 History worden ingekapseld `ModelRouter` - indien ingeschakeld `pushState` en `replaceState` om te garanderen dat een bepaald fragment van het model vooraf wordt opgehaald en toegankelijk is. Vervolgens wordt de geregistreerde front-end component meegedeeld dat het model is gewijzigd.

## Handmatig versus automatisch model routeren {#manual-vs-automatic-model-routing}

Met de opdracht `ModelRouter` automatiseert u het ophalen van fragmenten van het model. Maar zoals elk geautomatiseerd gereedschap ook met beperkingen gepaard gaat. Indien nodig `ModelRouter` kan de component worden uitgeschakeld of geconfigureerd om paden te negeren met behulp van meta-eigenschappen (zie de sectie Meta-eigenschappen van het document met [SPA paginacomponent](page-component.md) ). De ontwikkelaars van het vooreind kunnen hun eigen model dan uitvoeren die laag verpletteren door te verzoeken om om het even welk bepaald fragment van model te laden gebruikend de `PageModelManager` `getData()` functie.

>[!CAUTION]
>
>De huidige versie van het model ondersteunt `ModelRouter` alleen het gebruik van URL&#39;s die verwijzen naar het feitelijke bronnenpad van de entry-punten Sling Model. Het steunt niet het gebruik van Vanity URLs of aliassen.

## Routeringscontract {#routing-contract}

De huidige implementatie is gebaseerd op de veronderstelling dat het SPA project de HTML5 History API voor het verpletteren aan de verschillende toepassingspagina&#39;s gebruikt.

### Configuratie {#configuration}

Het `ModelRouter` steunt het concept model dat verplettert aangezien het luistert naar `pushState` en `replaceState` vraag om modelfragmenten vooraf in te stellen. Intern activeert het het model `PageModelManager` om het model te laden dat aan een bepaalde URL beantwoordt en brengt een `cq-pagemodel-route-changed` gebeurtenis in brand die andere modules kunnen luisteren aan.

Dit gedrag wordt standaard automatisch ingeschakeld. Om het onbruikbaar te maken, zou de SPA het volgende meta-bezit moeten teruggeven:

```
<meta property="cq:pagemodel_router" content="disable"\>
```

Merk op dat elke route van de SPA aan een toegankelijke bron in AEM (b.v., &quot; `/content/mysite/mypage"`) zou moeten beantwoorden aangezien de `PageModelManager` automatisch zal proberen om het overeenkomstige paginamodel te laden zodra de route wordt geselecteerd. Desondanks, indien nodig, kan de SPA een &quot;lijst van afgewezen personen&quot;van routes ook bepalen die door `PageModelManager`: moeten worden genegeerd:

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
