---
title: Dynamisch model naar componenttoewijzing voor SPA
description: In dit artikel wordt beschreven hoe het dynamische model naar componenttoewijzing wordt uitgevoerd in de Javascript SPA SDK voor AEM.
exl-id: 3a7b3f26-4a09-40c1-af03-bb8408a68e57
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Dynamisch model naar componenttoewijzing voor SPA {#dynamic-model-to-component-mapping-for-spas}

In dit document wordt beschreven hoe het dynamische model naar componenttoewijzing wordt uitgevoerd in de Javascript SPA SDK voor AEM.

## ComponentMapping-module {#componentmapping-module}

De `ComponentMapping` wordt verstrekt als pakket NPM aan het front-end project. Het slaat front-end componenten op en verstrekt een manier voor de Enige Toepassing van de Pagina om front-end componenten aan AEM middeltypes in kaart te brengen. Hierdoor wordt een dynamische resolutie van componenten ingeschakeld bij het parseren van het JSON-model van de toepassing.

Elk onderdeel in het model bevat een `:type` veld dat een AEM-brontype weergeeft. Als de front-end component is gekoppeld, kan deze zichzelf renderen met behulp van het fragment van het model dat is ontvangen van de onderliggende bibliotheken.

Raadpleeg de [SPA](blueprint.md) document voor meer informatie over modelontleding en de front-end componententoegang tot het model.

Zie ook het npm-pakket: [@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modelgestuurde toepassing voor één pagina {#model-driven-single-page-application}

Toepassingen met één pagina die gebruikmaken van de Javascript SPA SDK voor AEM, worden modelgestuurd:

1. Voorste-end componenten registreren zich aan [Opslag voor componenttoewijzing](#componentmapping-module).
1. Vervolgens worden de [Container](blueprint.md#container), zodra het door de [Modelleverancier](blueprint.md#the-model-provider), herhaalt de modelinhoud (`:items`).

1. In het geval van een pagina, de onderliggende`:children`) krijgt eerst een componentklasse van de [Componenttoewijzing](blueprint.md#componentmapping) en instantiëren.

## Toepassingsinitialisatie {#app-initialization}

Elke component wordt uitgebreid met de mogelijkheden van [`ModelProvider`](blueprint.md#the-model-provider). Initialisatie heeft derhalve de volgende algemene vorm:

1. Elke modelleverancier initialiseert zich en luistert naar veranderingen die aan het stuk van model worden aangebracht dat aan zijn binnencomponent beantwoordt.
1. De [`PageModelManager`](blueprint.md#pagemodelmanager) moet worden geïnitialiseerd als vertegenwoordigd door de [initialisatiestroom](blueprint.md).

1. Nadat het paginamodel is opgeslagen, retourneert de paginamodelbeheerder het volledige model van de app.
1. Dit model wordt dan overgegaan tot de front-end wortel [Container](blueprint.md#container) van de toepassing.
1. Stukken van het model worden uiteindelijk doorgegeven aan elke afzonderlijke onderliggende component.

![Initialisatie toepassingsmodel](assets/app-model-initialization.png)
