---
title: AEM- en Adobe Commerce-integratie met behulp van Commerce Integration Framework
description: AEM en Adobe Commerce zijn naadloos geïntegreerd met behulp van het Commerce Integration Framework (CIF). CIF laat AEM toe om tot een instantie van Adobe Commerce toegang te hebben en met Adobe Commerce via GraphQL te communiceren. AEM-auteurs kunnen ook Product- en rubriekkiezers en de productconsole gebruiken om producten en categoriegegevens op aanvraag van Adobe Commerce te doorzoeken. Bovendien verstrekt CIF een out-of-the-box opslag die handelsprojecten kan versnellen.
thumbnail: aem-magento-architecture.jpg
exl-id: 110ceef5-2c35-4b81-8e89-26929c0da91b,1cdfda88-a728-432f-b24a-f81347572bcf
source-git-commit: e304b49b44cf871f3c47120fad7899407c573234
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# AEM en Adobe Commerce Integration Using Commerce Integration Framework {#aem-framework}

De Experience Manager en Adobe Commerce zijn naadloos geïntegreerd met behulp van het Commerce Integration Framework (CIF). CIF laat AEM toe om tot de handelinstantie direct toegang te hebben en met Adobe Commerce te communiceren [GraphQL API&#39;s](https://devdocs.magento.com/guides/v2.4/graphql/).

>[!NOTE]
>
> De minimaal ondersteunde GraphQL API-versie is 2.3.5. Bepaalde functies worden alleen ondersteund in nieuwere versies of alleen in de Adobe Commerce-editie.

>[!NOTE]
>
>GraphQL wordt momenteel gebruikt in twee (afzonderlijke) scenario&#39;s in as a Cloud Service Adobe Experience Manager (AEM):
>
>* Dit scenario, waar CIF met handel via GraphQL communiceert.
>* [AEM de Fragmenten van de Inhoud werken samen met AEM GraphQL API (een aangepaste implementatie, die op standaard GraphQL wordt gebaseerd), om gestructureerde inhoud voor gebruik in uw toepassingen te leveren](/help/headless/graphql-api/content-fragments.md).


## Overzicht van architectuur {#overview}

De architectuur ziet er als volgt uit:

![Overzicht van CIF-architectuur](../assets/AEM_Magento_Architecture.png)

Binnen CIF, is er steun voor server-kant en cliënt-zijcommunicatie patronen.
Server-kant APIs vraag wordt uitgevoerd gebruikend ingebouwde, generische [GraphQL-client](https://github.com/adobe/commerce-cif-graphql-client) in combinatie met een [reeks gegenereerde gegevensmodellen](https://github.com/adobe/commerce-cif-magento-graphql) voor de handel GrafiekQL schema. Bovendien kan elke GraphQL-query of -mutatie in GQL-indeling worden gebruikt.

Voor de client-side componenten, die zijn gebouwd met [Reageren](https://reactjs.org/)de [Apollo-client](https://www.apollographql.com/docs/react/) wordt gebruikt.

## AEM CIF Core Component Architecture {#cif-core-components}

![AEM CIF Core Component Architecture](../assets/cif-component-architecture.jpg)

[AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components) zeer gelijkaardige ontwerppatronen en beste praktijken volgen als [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components).

De bedrijfslogica en de achtergrondcommunicatie met Adobe Commerce voor de AEM CIF de Componenten van de Kern worden uitgevoerd in het Verdelen Modellen. Als deze logica moet worden aangepast om aan projectspecifieke vereisten te voldoen, kan het delegatiepatroon voor Sling Models worden gebruikt.

>[!TIP]
>
>De [Aanpassen AEM CIF Core-componenten](../customizing/customize-cif-components.md) Deze pagina bevat een gedetailleerd voorbeeld en aanbevolen methoden voor het aanpassen van CIF Core Components.

Binnen projecten, AEM de Componenten van de Kern van CIF en de componenten van het douaneproject kunnen de gevormde cliënt voor een opslag van Adobe Commerce gemakkelijk terugwinnen verbonden aan een AEM pagina via het Verdelen van context-Aware configuratie.
