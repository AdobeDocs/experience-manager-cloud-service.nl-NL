---
title: Een API-verzoek maken - headless Setup
description: Leer hoe u de GraphQL API kunt gebruiken voor de levering zonder kop van inhoud en AEM Assets REST API voor het beheer van inhoudsfragmenten.
exl-id: 2b72f222-2ba5-4a21-86e4-40c763679c32
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 38a4bf89e099432163163e90e08aa0f47407724f
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# Een API-verzoek maken - headless Setup {#accessing-delivering-content-fragments}

Leer hoe u de GraphQL API kunt gebruiken voor de levering zonder kop van inhoud en AEM Assets REST API voor het beheer van inhoudsfragmenten.

## Wat zijn GraphQL en Assets REST API&#39;s? {#what-are-the-apis}

[&#x200B; nu u sommige inhoudsfragmenten &#x200B;](create-content-fragment.md) hebt gecreeerd, kunt u AEM APIs gebruiken om hen zonder kop te leveren.

* [&#x200B; GraphQL API &#x200B;](/help/headless/graphql-api/content-fragments.md) laat u verzoeken tot toegang tot en levering van de Fragmenten van de Inhoud tot stand brengen. Deze API biedt de meest robuuste set mogelijkheden voor het opvragen en gebruiken van inhoud met fragmentinhoud.
   * Om API te gebruiken, [&#x200B; bepaalt en laat eindpunten in AEM &#x200B;](/help/headless/graphql-api/graphql-endpoint.md) toe, en indien nodig, de [&#x200B; geïnstalleerde interface GraphiQL &#x200B;](/help/headless/graphql-api/graphiql-ide.md).
* Een selectie van [&#x200B; AEM APIs voor Gestructureerde Levering van de Inhoud en Beheer &#x200B;](/help/headless/apis-headless-and-content-fragments.md) zijn beschikbaar voor gebruik met de Fragmenten van de Inhoud.

De rest van deze handleiding is gericht op GraphQL-toegang en levering van inhoudsfragmenten.

## GraphQL-eindpunt inschakelen {#enable-graphql-endpoint}

Voordat de GraphQL API&#39;s kunnen worden gebruikt, moet een GraphQL-eindpunt worden gemaakt.

Voor details zie [&#x200B; GraphQL eindpunten in AEM beheren &#x200B;](/help/headless/graphql-api/graphql-endpoint.md).

## Inhoud opvragen met GraphQL met GraphiQL

De architecten van informatie ontwerpen vragen voor hun kanaal eindpunten om inhoud te leveren. Overweeg deze vragen slechts eenmaal per eindpunt, per model. In deze gids Aan de slag hoeft u slechts één gids te maken.

GraphiQL is winde, inbegrepen in uw milieu van AEM; het is toegankelijk/zichtbaar nadat u [&#x200B; uw eindpunten &#x200B;](#enable-graphql-endpoint) vormt.

Voor details zie [&#x200B; Gebruikend GrahiQL winde &#x200B;](/help/headless/graphql-api/graphiql-ide.md).

GraphQL laat gestructureerde vragen toe die niet alleen specifieke gegevensreeksen of individuele gegevensvoorwerpen kunnen richten, maar ook specifieke elementen van de voorwerpen, genestelde resultaten, biedt steun voor vraagvariabelen, en veel meer kunnen leveren.

GraphQL kan herhalende API-aanvragen en overlevering voorkomen en maakt het in plaats daarvan mogelijk om in grote hoeveelheden te leveren wat precies nodig is voor rendering als reactie op één API-query. De resulterende JSON kan worden gebruikt om gegevens te leveren aan andere sites of apps.

## Volgende stappen {#next-steps}

Dat is het! U hebt nu een basiskennis van beheer van inhoud zonder kop in AEM. Er zijn veel meer bronnen waar u dieper kunt duiken voor een volledig begrip van de beschikbare functies.

* **[Fragmenten van de Inhoud](/help/sites-cloud/administering/content-fragments/managing.md)** - voor details over het creëren van en het beheren van de Fragmenten van de Inhoud
* **[de Steun van de Fragmenten van de Inhoud in HTTP API van AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)** - voor details bij de toegang tot van de inhoud van AEM direct over HTTP API, via de verrichtingen van CRUD (creeer, las, Update, schrap)
* **[GraphQL API](/help/headless/graphql-api/content-fragments.md)** - voor details op hoe te om de Fragmenten van de Inhoud zonder kop te leveren

>[!NOTE]
>
>Het [&#x200B; Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud &#x200B;](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.
