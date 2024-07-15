---
title: Dynamisch model naar componenttoewijzing voor SPA
description: In dit artikel wordt beschreven hoe het dynamische model naar componenttoewijzing plaatsvindt in de JavaScript SPA SDK voor AEM.
exl-id: 3a7b3f26-4a09-40c1-af03-bb8408a68e57
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Dynamisch model naar componenttoewijzing voor SPA {#dynamic-model-to-component-mapping-for-spas}

In dit document wordt beschreven hoe het dynamische model wordt toegewezen aan componenttoewijzing in de JavaScript SPA SDK voor AEM.

## ComponentMapping-module {#componentmapping-module}

De module `ComponentMapping` wordt verstrekt als pakket NPM aan het front-end project. Het slaat front-end componenten op en verstrekt een manier voor de Enige Toepassing van de Pagina om front-end componenten aan AEM middeltypes in kaart te brengen. De module laat een dynamische resolutie van componenten toe wanneer het ontleden van het model JSON van de toepassing.

Elk item in het model bevat een `:type` -veld dat een AEM-brontype weergeeft. Als de front-end component is gekoppeld, kan deze zichzelf renderen met behulp van het fragment van het model dat is ontvangen van de onderliggende bibliotheken.

Zie [ SPA het document van de Vervaging ](blueprint.md) voor meer informatie over model het ontleden en de front-end componententoegang tot het model.

Zie ook het npm-pakket: [@adobe/aem-spa-component-mapping ](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modelgestuurde toepassing voor één pagina {#model-driven-single-page-application}

Toepassingen op één pagina die de JavaScript SPA SDK voor AEM gebruiken, zijn op een model gebaseerd:

1. De front-end componenten registreren zich aan de [ Opslag van de Afbeelding van de Component ](#componentmapping-module).
1. Dan de [ Container ](blueprint.md#container), eens voorzien van een model door de [ ModelLeverancier ](blueprint.md#the-model-provider), herhaalt over zijn modelinhoud (`:items`).

1. Als er een pagina is, krijgen zijn kinderen (`:children`) eerst een componentenklasse van de [ Afbeelding van de Component ](blueprint.md#componentmapping) en dan het concretiseren.

## Toepassingsinitialisatie {#app-initialization}

Elke component wordt uitgebreid met de mogelijkheden van [`ModelProvider`](blueprint.md#the-model-provider). Initialisatie heeft derhalve de volgende algemene vorm:

1. Elke modelleverancier initialiseert zich en luistert naar veranderingen die aan het stuk van model worden aangebracht dat aan zijn binnencomponent beantwoordt.
1. [`PageModelManager`](blueprint.md#pagemodelmanager) moet worden geïnitialiseerd zoals vertegenwoordigd door de [ initialiseringsstroom ](blueprint.md).

1. Nadat het paginamodel is opgeslagen, retourneert de paginamodelbeheerder het volledige model van de app.
1. Dit model wordt dan overgegaan tot de front-end wortel [ component van de Container ](blueprint.md#container) van de toepassing.
1. Stukken van het model worden uiteindelijk doorgegeven aan elke afzonderlijke onderliggende component.

![ het modelinitialisering van de app ](assets/app-model-initialization.png)
