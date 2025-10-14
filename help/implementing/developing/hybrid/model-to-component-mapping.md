---
title: Dynamisch model aan Component Mapping voor SPAs
description: Dit artikel beschrijft hoe het dynamische model aan componentenafbeelding in JavaScript SPA SDK voor AEM voorkomt.
exl-id: 3a7b3f26-4a09-40c1-af03-bb8408a68e57
feature: Developing
role: Admin, Architect, Developer
index: false
source-git-commit: 7a9d947761b0473f5ddac3c4d19dfe5bed5b97fe
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Dynamisch model aan Component Mapping voor SPAs {#dynamic-model-to-component-mapping-for-spas}

Dit document beschrijft hoe het dynamische model aan componentenafbeelding in JavaScript SPA SDK voor AEM voorkomt.

{{ue-over-spa}}

## ComponentMapping-module {#componentmapping-module}

De module `ComponentMapping` wordt verstrekt als pakket NPM aan het front-end project. Het slaat front-end componenten op en verstrekt een manier voor de Enige Toepassing van de Pagina om front-end componenten aan de middeltypes van AEM in kaart te brengen. De module laat een dynamische resolutie van componenten toe wanneer het ontleden van het model JSON van de toepassing.

Elk item in het model bevat een veld `:type` dat een AEM-brontype weergeeft. Als de front-end component is gekoppeld, kan deze zichzelf renderen met behulp van het fragment van het model dat is ontvangen van de onderliggende bibliotheken.

Zie [&#x200B; het document van het Vervagen van het KUUROORD &#x200B;](blueprint.md) voor meer informatie over model het ontleden en de front-end componententoegang tot het model.

Zie ook het npm-pakket: [@adobe/aem-spa-component-mapping &#x200B;](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modelgestuurde toepassing voor één pagina {#model-driven-single-page-application}

Toepassingen op één pagina die gebruikmaken van de JavaScript SPA SDK voor AEM, zijn gebaseerd op modellen:

1. De front-end componenten registreren zich aan de [&#x200B; Opslag van de Afbeelding van de Component &#x200B;](#componentmapping-module).
1. Dan de [&#x200B; Container &#x200B;](blueprint.md#container), eens voorzien van een model door de [&#x200B; ModelLeverancier &#x200B;](blueprint.md#the-model-provider), herhaalt over zijn modelinhoud (`:items`).

1. Als er een pagina is, krijgen zijn kinderen (`:children`) eerst een componentenklasse van de [&#x200B; Afbeelding van de Component &#x200B;](blueprint.md#componentmapping) en dan het concretiseren.

## Toepassingsinitialisatie {#app-initialization}

Elke component wordt uitgebreid met de mogelijkheden van [`ModelProvider`](blueprint.md#the-model-provider). Initialisatie heeft derhalve de volgende algemene vorm:

1. Elke modelleverancier initialiseert zich en luistert naar veranderingen die aan het stuk van model worden aangebracht dat aan zijn binnencomponent beantwoordt.
1. [`PageModelManager`](blueprint.md#pagemodelmanager) moet worden geïnitialiseerd zoals vertegenwoordigd door de [&#x200B; initialiseringsstroom &#x200B;](blueprint.md).

1. Nadat het paginamodel is opgeslagen, retourneert de paginamodelbeheerder het volledige model van de app.
1. Dit model wordt dan overgegaan tot de front-end wortel [&#x200B; component van de Container &#x200B;](blueprint.md#container) van de toepassing.
1. Stukken van het model worden uiteindelijk doorgegeven aan elke afzonderlijke onderliggende component.

![&#x200B; het modelinitialisering van de app &#x200B;](assets/app-model-initialization.png)
