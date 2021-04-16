---
title: AEM en Adobe Commerce (Magento) Integratie die het Kader van de Integratie van de Handel gebruikt
description: AEM en Adobe Commerce (Magento) zijn naadloos geïntegreerd met behulp van het Commerce Integration Framework (CIF). CIF laat AEM toe om tot een instantie van de Magento toegang te hebben en met Magento via GraphQL te communiceren. AEM-auteurs kunnen ook Product- en rubriekkiezers en de productconsole gebruiken om door product- en categoriegegevens te bladeren die op verzoek van Magento zijn opgehaald. Bovendien verstrekt CIF een out-of-the-box opslag die handelsprojecten kan versnellen.
thumbnail: aem-magento-architecture.jpg
exl-id: 1cdfda88-a728-432f-b24a-f81347572bcf
translation-type: tm+mt
source-git-commit: a4e53fdcb33eab8afabcb13d651155cd247bda1f
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Integratie van AEM en Adobe Commerce (Magento) met gebruik van Commerce Integration Framework {#aem-magento-framework}

De Experience Manager en de Handel van de Adobe (Magento) zijn naadloos geïntegreerd gebruikend het Kader van de Integratie van de Handel (CIF). CIF laat AEM toe om tot en met de handelsinstantie direct toegang te hebben gebruikend Adobe Commerce [GraphQL APIs](https://devdocs.magento.com/guides/v2.4/graphql/).

>[!NOTE]
>
>GraphQL wordt momenteel gebruikt in twee (afzonderlijke) scenario&#39;s in Adobe Experience Manager (AEM) als Cloud Service:
>
>* Dit scenario, waar CIF met handel via GraphQL communiceert.
>* [AEM Inhoudsfragmenten werken samen met de AEM GraphQL API (een aangepaste implementatie op basis van standaard GraphQL) voor gestructureerde inhoud voor gebruik in uw toepassingen](/help/assets/content-fragments/graphql-api-content-fragments.md).


## Overzicht architectuur {#overview}

De architectuur ziet er als volgt uit:

![Overzicht van CIF-architectuur](../assets/AEM_Magento_Architecture.png)

Binnen CIF is er steun voor server-kant en cliënt-zijcommunicatie patronen.
Server-side APIs vraag wordt uitgevoerd gebruikend ingebouwde, generische [GraphQL cliënt](https://github.com/adobe/commerce-cif-graphql-client) in combinatie met een [reeks geproduceerde gegevensmodellen](https://github.com/adobe/commerce-cif-magento-graphql) voor het schema van GraphQL van de handel Bovendien, om het even welke vraag GraphQL of mutatie in formaat GQL kunnen worden gebruikt.

Voor de client-side componenten, die worden gebouwd met [React](https://reactjs.org/), wordt [Apollo Client](https://www.apollographql.com/docs/react/) gebruikt.

## AEM CIF Core Component Architecture {#cif-core-components}

![AEM CIF Core Component Architecture](../assets/cif-component-architecture.jpg)

[AEM CIF de ](https://github.com/adobe/aem-core-cif-components) Componenten van de Kern volgen zeer gelijkaardige ontwerppatronen en beste praktijken zoals de  [AEM Componenten](https://github.com/adobe/aem-core-wcm-components) van de Kern WCM.

De bedrijfslogica en de achterwaartse communicatie met de Handel van Adobe voor de AEMKern van CIF Componenten wordt uitgevoerd in het Verdelen Modellen. Als deze logica moet worden aangepast om aan projectspecifieke vereisten te voldoen, kan het delegatiepatroon voor Sling Models worden gebruikt.

>[!TIP]
>
>De [Aanpassen AEM CIF Core Components](../customizing/customize-cif-components.md) pagina heeft een gedetailleerd voorbeeld en beste praktijken op hoe te om de Componenten van de Kern aan te passen CIF.

Binnen projecten, AEM de Componenten van de Kern van CIF en de componenten van het douaneproject kunnen de gevormde cliënt voor een opslag van de Handel van Adobe gemakkelijk terugwinnen verbonden aan een AEM pagina via het Verdelen van context-Aware configuratie.
