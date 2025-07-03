---
title: AEM- en Adobe Commerce-integratie met Commerce integration framework
description: AEM en Adobe Commerce zijn naadloos geïntegreerd met Commerce integration framework (CIF). CIF stelt AEM in staat toegang te krijgen tot een Adobe Commerce-exemplaar en te communiceren met Adobe Commerce via GraphQL. Ook kunnen AEM-auteurs producten- en rubriekkiezers en de productconsole gebruiken om producten- en categoriegegevens op aanvraag van Adobe Commerce te doorzoeken. Daarnaast biedt CIF een winkel die de handelsprojecten kan versnellen.
thumbnail: aem-magento-architecture.jpg
exl-id: 110ceef5-2c35-4b81-8e89-26929c0da91b
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# AEM- en Adobe Commerce-integratie met Commerce integration framework {#aem-framework}

De Experience Manager en Adobe Commerce zijn naadloos geïntegreerd met Commerce integration framework (CIF). CIF laat AEM toe om tot direct toegang te hebben en met de handelsinstantie te communiceren gebruikend Adobe Commerce [ GraphQL APIs ](https://devdocs.magento.com/guides/v2.4/graphql/).

>[!NOTE]
>
> De minimaal ondersteunde GraphQL API-versie is 2.3.5. Bepaalde functies worden alleen ondersteund in nieuwere versies of alleen in de Adobe Commerce-editie.

>[!NOTE]
>
>GraphQL wordt momenteel gebruikt in twee (afzonderlijke) scenario&#39;s in Adobe Experience Manager (AEM) as a Cloud Service:
>
>* Dit scenario, waar CIF met handel via GraphQL communiceert.
>* [ de Inhoudsfragmenten van AEM werken samen met AEM GraphQL API (een aangepaste implementatie, die op standaardGraphQL wordt gebaseerd), om gestructureerde inhoud voor gebruik in uw toepassingen ](/help/headless/graphql-api/content-fragments.md) te leveren.

## Overzicht van architectuur {#overview}

De architectuur ziet er als volgt uit:

![ het Overzicht van de Architectuur van CIF ](../assets/AEM_Magento_Architecture.png)

Binnen CIF is er ondersteuning voor communicatiepatronen aan de serverzijde en de client.
De server-kant APIs vraag wordt uitgevoerd gebruikend ingebouwde, generische [ cliënt van GraphQL ](https://github.com/adobe/commerce-cif-graphql-client) in combinatie met a [ reeks geproduceerde gegevensmodellen ](https://github.com/adobe/commerce-cif-magento-graphql) voor het schema van handelsGraphQL. Ook kan elke GraphQL-query of -mutatie in GQL-indeling worden gebruikt.

Voor de cliënt-zijcomponenten, die gebruikend [ Reageer ](https://reactjs.org/) worden gebouwd, wordt de [ Cliënt van Apollo ](https://www.apollographql.com/docs/react/) gebruikt.

## AEM CIF Core-componentarchitectuur {#cif-core-components}

![ de Architectuur van de Component van de Kern van AEM CIF ](../assets/cif-component-architecture.jpg)

{de Componenten van de Kern van AEM CIF van 0} [ volgen zeer gelijkaardige ontwerppatronen en beste praktijken zoals ](https://github.com/adobe/aem-core-cif-components) de Componenten van de Kern van AEM WCM [.](https://github.com/adobe/aem-core-wcm-components)

De bedrijfslogica en de achtergrondcommunicatie met Adobe Commerce voor de AEM CIF Core Components worden geïmplementeerd in Sling Models. Als deze logica moet worden aangepast om aan projectspecifieke vereisten te voldoen, kan het delegatiepatroon voor Sling Models worden gebruikt.

>[!TIP]
>
>[ het Aanpassen van de Componenten van de Kern van AEM CIF ](../customizing/customize-cif-components.md) pagina heeft een gedetailleerd voorbeeld en beste praktijken op hoe te om de Componenten van de Kern van CIF aan te passen.

Binnen projecten, kunnen de Componenten van de Kern van AEM CIF en de componenten van het douaneproject de gevormde cliënt voor een opslag van Adobe Commerce gemakkelijk terugwinnen verbonden aan een pagina van AEM via het Verdelen van context-Aware configuratie.

## Zoeken {#search}

CIF verstrekt uit-van-de-doos de Component van de Kern van het a [ Onderzoek ](https://www.aemcomponents.dev/content/core-components-examples/library/commerce/search.html) die een server-kant teruggegeven onderzoekservaring is die op [ GraphQL API van Commerce ](https://developer.adobe.com/commerce/webapi/graphql/) wordt gebaseerd. De klanten van Commerce hebben de optie om [ Levend Onderzoek ](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/guide-overview.html?lang=nl-NL) in plaats daarvan te gebruiken. Volg deze [ verbinding ](/help/commerce-cloud/integrating/live-search-plp.md) om meer over CIF te leren - Levende integratie van het Onderzoek.

