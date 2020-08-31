---
title: Dynamisch model aan Component Mapping voor SPAs
description: Dit artikel beschrijft hoe het dynamische model aan componentenafbeelding in Javascript SPA SDK voor AEM voorkomt.
translation-type: tm+mt
source-git-commit: c075bcc415b68ba0deaeca61d6d179bd7263ca5f
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---


# Dynamisch model aan Component Mapping voor SPAs {#dynamic-model-to-component-mapping-for-spas}

Dit document beschrijft hoe het dynamische model aan componentenafbeelding in Javascript SPA SDK voor AEM voorkomt.

## ComponentMapping-module {#componentmapping-module}

De `ComponentMapping` module wordt verstrekt als pakket NPM aan het front-end project. Het slaat front-end componenten op en verstrekt een manier voor de Enige Toepassing van de Pagina om front-end componenten aan AEM middeltypes in kaart te brengen. Hierdoor wordt een dynamische resolutie van componenten ingeschakeld bij het parseren van het JSON-model van de toepassing.

Elke punten in het model bevatten een `:type` gebied dat een AEM middeltype blootstelt. Als de front-end component is gekoppeld, kan deze zichzelf renderen met behulp van het fragment van het model dat is ontvangen van de onderliggende bibliotheken.

Gelieve te verwijzen naar het document van de Blauwdruk [van het](blueprint.md) KUUROORD voor meer informatie over modelontleding en de front-end componententoegang tot het model.

Zie ook het npm-pakket: [@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modelgestuurde toepassing voor één pagina {#model-driven-single-page-application}

Toepassingen van één pagina die gebruikmaken van de Javascript SPA SDK voor AEM zijn modelgestuurd:

1. De front-end componenten registreren zich aan de Opslag van de Toewijzing van de [Component](#componentmapping-module).
1. Dan herhaalt de [Container](blueprint.md#container), zodra voorzien van een model door de [ModelLeverancier](blueprint.md#the-model-provider), over zijn modelinhoud (`:items`).

1. In het geval van een pagina, krijgen zijn kinderen (`:children`) eerst een componentenklasse van de Toewijzing [van de](blueprint.md#componentmapping) Component en dan concretiseren het.

## Toepassingsinitialisatie {#app-initialization}

Elke component wordt uitgebreid met de mogelijkheden van [`ModelProvider`](blueprint.md#the-model-provider). Initialisatie heeft derhalve de volgende algemene vorm:

1. Elke modelleverancier initialiseert zich en luistert naar veranderingen die aan het stuk van model worden aangebracht dat aan zijn binnencomponent beantwoordt.
1. Het [`PageModelManager`](blueprint.md#pagemodelmanager) moet worden geïnitialiseerd zoals wordt vertegenwoordigd door de [initialisatiestroom](blueprint.md).

1. Nadat het paginamodel is opgeslagen, retourneert de paginamodelbeheerder het volledige model van de app.
1. Dit model wordt dan overgegaan tot de front-end [wortelContainer](blueprint.md#container) component van de toepassing.
1. Stukken van het model worden uiteindelijk doorgegeven aan elke afzonderlijke onderliggende component.

![Initialisatie toepassingsmodel](assets/app-model-initialization.png)
