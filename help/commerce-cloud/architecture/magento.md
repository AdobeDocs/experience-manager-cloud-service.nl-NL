---
title: AEM- en Magento-integratie met behulp van Commerce Integration Framework
description: AEM en Magento zijn naadloos geïntegreerd met behulp van het Commerce Integration Framework (CIF). CIF laat AEM toe om tot een instantie van de Magento toegang te hebben en met Magento via GraphQL te communiceren. AEM-auteurs kunnen ook Product- en rubriekkiezers en de productconsole gebruiken om door product- en categoriegegevens te bladeren die op verzoek van Magento zijn opgehaald. Bovendien verstrekt CIF een out-of-the-box opslag die handelsprojecten kan versnellen.
thumbnail: aem-magento-architecture.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---


# AEM- en Magento-integratie met behulp van Commerce Integration Framework {#aem-magento-framework}

AEM en Magento zijn naadloos geïntegreerd met behulp van het Commerce Integration Framework (CIF). CIF laat AEM toe om tot een instantie van de Magento toegang te hebben en met Magento via GraphQL te communiceren. AEM-auteurs kunnen ook Product- en rubriekkiezers en de productconsole gebruiken om door product- en categoriegegevens te bladeren die op verzoek van Magento zijn opgehaald. Bovendien verstrekt CIF een out-of-the-box opslag die handelsprojecten kan versnellen.

## Overzicht van architectuur {#overview}

De architectuur ziet er als volgt uit:

![Overzicht van CIF-architectuur](../assets/AEM_Magento_Architecture.JPG)

CIF bouwt op steun GraphQL voort. Het belangrijkste communicatiekanaal en de Magento zijn Magento tussen [GraphQAPI](https://devdocs.magento.com/guides/v2.4/graphql/) API. Er zijn verschillende manieren om de communicatie tussen AEM als Cloud Service en Magento te vormen, zie [Begonnen](../getting-started.md) pagina voor details.

Binnen CIF is er steun voor server-kant en cliënt-zijcommunicatie patronen.
Server-kant APIs vraag wordt uitgevoerd gebruikend de bouwstijl-binnen, generische cliënt [](https://github.com/adobe/commerce-cif-graphql-client) GraphQL in combinatie met een [reeks geproduceerde gegevensmodellen](https://github.com/adobe/commerce-cif-magento-graphql) voor het schema van Magento GraphQL. Bovendien kan elke GraphQL-query of -mutatie in GQL-indeling worden gebruikt.

Voor de cliënt-zijcomponenten, die gebruikend [React](https://reactjs.org/)bouwen, wordt de Cliënt [](https://www.apollographql.com/docs/react/) Apollo gebruikt.

## AEM CIF Core Component Architecture {#cif-core-components}

![AEM CIF Core Component Architecture](../assets/cif-component-architecture.jpg)

[AEM CIF Core Components](https://github.com/adobe/aem-core-cif-components) volgen zeer gelijkaardige ontwerppatronen en beste praktijken zoals de [AEM Core Componenten](https://github.com/adobe/aem-core-wcm-components)WCM.

De bedrijfslogica en de achterste mededeling met Magento voor de AEMComponenten van de Kern van CIF wordt uitgevoerd in het Verdelen Modellen. Indien deze logica moet worden aangepast om te voldoen aan projectspecifieke vereisten, kan het delegatiepatroon voor Sling Models worden gebruikt.

>[!TIP]
>
>De pagina [Aanpassen AEM CIF Core Components](../customizing/customize-cif-components.md) bevat een gedetailleerd voorbeeld en aanbevolen methoden voor het aanpassen van CIF Core Components.

Binnen projecten, AEM de Componenten van de Kern van CIF en de componenten van het douaneproject kunnen de gevormde cliënt voor een opslag van Magento gemakkelijk terugwinnen verbonden aan een AEM pagina via het Verdelen van context-Aware configuratie.
