---
title: Dynamisch model naar componenttoewijzing voor SPA
description: In dit artikel wordt beschreven hoe het dynamische model naar componenttoewijzing wordt uitgevoerd in de Javascript SPA SDK voor AEM.
translation-type: tm+mt
source-git-commit: cdd92032c627740c66de7b2f3836fa1dcd2ee2ca
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---


# Dynamisch model naar componenttoewijzing voor SPA {#dynamic-model-to-component-mapping-for-spas}

In dit document wordt beschreven hoe het dynamische model naar componenttoewijzing wordt uitgevoerd in de Javascript SPA SDK voor AEM.

## ComponentMapping Module {#componentmapping-module}

De `ComponentMapping` module wordt verstrekt als pakket NPM aan het front-end project. Het slaat front-end componenten op en verstrekt een manier voor de Enige Toepassing van de Pagina om front-end componenten aan AEM middeltypes in kaart te brengen. Hierdoor wordt een dynamische resolutie van componenten ingeschakeld bij het parseren van het JSON-model van de toepassing.

Elke punten in het model bevatten een `:type` gebied dat een AEM middeltype blootstelt. Als de front-end component is gekoppeld, kan deze zichzelf renderen met behulp van het fragment van het model dat is ontvangen van de onderliggende bibliotheken.

Raadpleeg het document [SPA Blueprint](blueprint.md) voor meer informatie over modelparsering en de front-end componenttoegang tot het model.

Zie ook het npm-pakket: [@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modelgestuurde toepassing voor één pagina {#model-driven-single-page-application}

Toepassingen met één pagina die gebruikmaken van de Javascript SPA SDK voor AEM, worden modelgestuurd:

1. De front-end componenten registreren zich aan [de Winkel van de Afbeelding van de Component](#componentmapping-module).
1. Dan [Container](blueprint.md#container), eens voorzien van een model door [ModelLeverancier](blueprint.md#the-model-provider), herhaalt over zijn modelinhoud (`:items`).

1. In het geval van een pagina, krijgen zijn kinderen (`:children`) eerst een componentenklasse van [Component Mapping](blueprint.md#componentmapping) en dan concretiseren het.

## Initialisatie van toepassingen {#app-initialization}

Elke component wordt uitgebreid met de mogelijkheden van [`ModelProvider`](blueprint.md#the-model-provider). Initialisatie heeft derhalve de volgende algemene vorm:

1. Elke modelleverancier initialiseert zich en luistert naar veranderingen die aan het stuk van model worden aangebracht dat aan zijn binnencomponent beantwoordt.
1. [`PageModelManager`](blueprint.md#pagemodelmanager) moet worden geïnitialiseerd zoals vertegenwoordigd door [initialisatiestroom](blueprint.md).

1. Nadat het paginamodel is opgeslagen, retourneert de paginamodelbeheerder het volledige model van de app.
1. Dit model wordt dan overgegaan tot de front-end wortel [Container](blueprint.md#container) component van de toepassing.
1. Stukken van het model worden uiteindelijk doorgegeven aan elke afzonderlijke onderliggende component.

![Initialisatie toepassingsmodel](assets/app-model-initialization.png)
