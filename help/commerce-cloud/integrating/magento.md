---
title: AEM en Adobe Commerce Integration met Commerce integration framework
description: AEM en Adobe Commerce zijn naadloos geïntegreerd met behulp van het Commerce integration framework (CIF). CIF biedt AEM toegang tot een Adobe Commerce-exemplaar en communiceert met Adobe Commerce via GraphQL. Ook kunnen AEM auteurs product- en rubriekkiezers en de productconsole gebruiken om door product- en categoriegegevens te bladeren die op verzoek van Adobe Commerce zijn opgehaald. Bovendien verstrekt CIF een out-of-the-box opslag die handelsprojecten kan versnellen.
thumbnail: aem-magento-architecture.jpg
exl-id: 110ceef5-2c35-4b81-8e89-26929c0da91b
feature: Commerce Integration Framework
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# AEM en Adobe Commerce Integration Using Commerce integration framework {#aem-framework}

De Experience Manager en Adobe Commerce zijn naadloos geïntegreerd met het Commerce integration framework (CIF). CIF laat AEM toe om tot direct toegang te hebben en met de handelsinstantie te communiceren gebruikend Adobe Commerce [GraphQL API&#39;s](https://devdocs.magento.com/guides/v2.4/graphql/).

>[!NOTE]
>
> De minimaal ondersteunde GraphQL API-versie is 2.3.5. Bepaalde functies worden alleen ondersteund in nieuwere versies of alleen in de Adobe Commerce-editie.

>[!NOTE]
>
>GraphQL wordt momenteel gebruikt in twee (afzonderlijke) scenario&#39;s in Adobe Experience Manager (AEM) as a Cloud Service:
>
>* Dit scenario, waar CIF met handel via GraphQL communiceert.
>* [AEM Content Fragments werken samen met de AEM GraphQL API (een aangepaste implementatie, gebaseerd op standaard GraphQL) om gestructureerde inhoud te leveren voor gebruik in uw toepassingen](/help/headless/graphql-api/content-fragments.md).

## Overzicht van architectuur {#overview}

De architectuur ziet er als volgt uit:

![Overzicht CIF architectuur](../assets/AEM_Magento_Architecture.png)

Binnen CIF, is er steun voor server-kant en cliënt-zijcommunicatie patronen.
Server-kant APIs vraag wordt uitgevoerd gebruikend ingebouwde, generische [GraphQL-client](https://github.com/adobe/commerce-cif-graphql-client) in combinatie met een [reeks gegenereerde gegevensmodellen](https://github.com/adobe/commerce-cif-magento-graphql) voor de handel GraphQL schema. Ook kan elke GraphQL-query of -mutatie in GQL-indeling worden gebruikt.

Voor de client-side componenten, die zijn gebouwd met [Reageren](https://reactjs.org/)de [Apollo-client](https://www.apollographql.com/docs/react/) wordt gebruikt.

## AEM CIF Core Component Architecture {#cif-core-components}

![AEM CIF Core Component Architecture](../assets/cif-component-architecture.jpg)

[CIF kerncomponenten AEM](https://github.com/adobe/aem-core-cif-components) zeer gelijkaardige ontwerppatronen en beste praktijken volgen als [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components).

De bedrijfslogica en de achtergrondcommunicatie met Adobe Commerce voor de AEM CIF Core Components wordt geïmplementeerd in Sling Models. Als deze logica moet worden aangepast om aan projectspecifieke vereisten te voldoen, kan het delegatiepatroon voor Sling Models worden gebruikt.

>[!TIP]
>
>De [Aanpassen AEM kerncomponenten](../customizing/customize-cif-components.md) Deze pagina bevat een gedetailleerd voorbeeld en aanbevolen methoden voor het aanpassen van CIF Core Components.

Binnen projecten, AEM CIF de Componenten van de Kern en de componenten van het douaneproject gemakkelijk de gevormde cliënt voor een opslag van Adobe Commerce verbonden aan een AEM pagina via het Verdelen van context-Aware configuratie terugwinnen.

## Zoeken {#search}

CIF biedt een [Core-component zoeken](https://www.aemcomponents.dev/content/core-components-examples/library/commerce/search.html) dat een gerenderde zoekervaring op de server is op basis van [COMMERCE GRAPHQL API](https://developer.adobe.com/commerce/webapi/graphql/). Commerce-klanten hebben de mogelijkheid om [Live zoeken](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/guide-overview.html?lang=en) in plaats daarvan. Hierna volgen [link](/help/commerce-cloud/integrating/live-search-plp.md) voor meer informatie over de integratie CIF - Live zoeken.

