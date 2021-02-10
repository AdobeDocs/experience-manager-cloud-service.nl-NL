---
title: AEM- en Magento-integratie met behulp van Commerce Integration Framework
description: AEM en Magento zijn naadloos geïntegreerd met behulp van het Commerce Integration Framework (CIF). CIF laat AEM toe om tot een instantie van de Magento toegang te hebben en met Magento via GraphQL te communiceren. AEM-auteurs kunnen ook Product- en rubriekkiezers en de productconsole gebruiken om door product- en categoriegegevens te bladeren die op verzoek van Magento zijn opgehaald. Bovendien verstrekt CIF een out-of-the-box opslag die handelsprojecten kan versnellen.
thumbnail: aem-magento-architecture.jpg
translation-type: tm+mt
source-git-commit: 36e0fd66c9119571cde5c8791862abed8b552d5a
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---


# AEM en Magento integratie die het Kader van de Integratie van de Handel {#aem-magento-framework} gebruiken

AEM en Magento zijn naadloos geïntegreerd met behulp van het Commerce Integration Framework (CIF). CIF laat AEM toe om tot een instantie van de Magento toegang te hebben en met Magento via GraphQL te communiceren. AEM-auteurs kunnen ook Product- en rubriekkiezers en de productconsole gebruiken om door product- en categoriegegevens te bladeren die op verzoek van Magento zijn opgehaald. Bovendien verstrekt CIF een out-of-the-box opslag die handelsprojecten kan versnellen.

>[!NOTE]
>
>GraphQL wordt momenteel gebruikt in twee (afzonderlijke) scenario&#39;s in Adobe Experience Manager (AEM) als Cloud Service:
>
>* AEM de Handel verbruikt gegevens van een handelsplatform via GraphQL.
>* [AEM Inhoudsfragmenten werken samen met de AEM GraphQL API (een aangepaste implementatie op basis van standaard GraphQL) voor gestructureerde inhoud voor gebruik in uw toepassingen](/help/assets/content-fragments/graphql-api-content-fragments.md).


## Overzicht architectuur {#overview}

De architectuur ziet er als volgt uit:

![Overzicht van CIF-architectuur](../assets/AEM_Magento_Architecture.JPG)

CIF bouwt op steun GraphQL voort. Het belangrijkste communicatiekanaal en de Magento zijn Magento tussen [GraphQL API](https://devdocs.magento.com/guides/v2.4/graphql/) API. Er zijn verschillende manieren om de communicatie tussen AEM als Cloud Service en Magento te vormen, zie [Getting Started](../getting-started.md) pagina voor details.

Binnen CIF is er steun voor server-kant en cliënt-zijcommunicatie patronen.
Server-side APIs vraag wordt uitgevoerd gebruikend ingebouwde, generische [GraphQL cliënt](https://github.com/adobe/commerce-cif-graphql-client) in combinatie met een [reeks geproduceerde gegevensmodellen](https://github.com/adobe/commerce-cif-magento-graphql) voor het schema van Magento GraphQL. Bovendien kan elke GraphQL-query of -mutatie in GQL-indeling worden gebruikt.

Voor de client-side componenten, die worden gebouwd met [React](https://reactjs.org/), wordt [Apollo Client](https://www.apollographql.com/docs/react/) gebruikt.

## AEM CIF Core Component Architecture {#cif-core-components}

![AEM CIF Core Component Architecture](../assets/cif-component-architecture.jpg)

[AEM CIF de ](https://github.com/adobe/aem-core-cif-components) Componenten van de Kern volgen zeer gelijkaardige ontwerppatronen en beste praktijken zoals de  [AEM Componenten](https://github.com/adobe/aem-core-wcm-components) van de Kern WCM.

De bedrijfslogica en de achterste mededeling met Magento voor de AEMComponenten van de Kern van CIF wordt uitgevoerd in het Verdelen Modellen. Indien deze logica moet worden aangepast om te voldoen aan projectspecifieke vereisten, kan het delegatiepatroon voor Sling Models worden gebruikt.

>[!TIP]
>
>De [Aanpassen AEM CIF Core Components](../customizing/customize-cif-components.md) pagina heeft een gedetailleerd voorbeeld en beste praktijken op hoe te om de Componenten van de Kern aan te passen CIF.

Binnen projecten, AEM de Componenten van de Kern van CIF en de componenten van het douaneproject kunnen de gevormde cliënt voor een opslag van Magento gemakkelijk terugwinnen verbonden aan een AEM pagina via het Verdelen van context-Aware configuratie.
