---
title: Een API-verzoek maken - headless Setup
description: Leer hoe u de GraphQL API kunt gebruiken voor koploze levering van inhoud van inhoudsfragmenten en AEM middelen REST API voor het beheer van inhoudsfragmenten.
exl-id: 2b72f222-2ba5-4a21-86e4-40c763679c32
source-git-commit: 674db680f46a4fd4772cb10fe7cb396652354dfe
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 0%

---

# Een API-verzoek maken - headless Setup {#accessing-delivering-content-fragments}

Leer hoe u de GraphQL API kunt gebruiken voor koploze levering van inhoud van inhoudsfragmenten en AEM middelen REST API voor het beheer van inhoudsfragmenten.

## Wat zijn GraphQL en Assets REST API&#39;s? {#what-are-the-apis}

[Nu u enkele inhoudsfragmenten hebt gemaakt,](create-content-fragment.md) u kunt AEM API&#39;s gebruiken om ze zonder koppen te leveren.

* [De GraphQL API](/help/headless/graphql-api/content-fragments.md) Hiermee kunt u aanvragen maken voor toegang tot en levering van inhoudsfragmenten. Deze API biedt de meest robuuste set mogelijkheden voor het opvragen en gebruiken van inhoud met fragmentinhoud.
   * De API gebruiken [eindpunten definiëren en inschakelen in AEM](/help/headless/graphql-api/graphql-endpoint.md)en, indien nodig, de [GraphiQL-interface geïnstalleerd](/help/headless/graphql-api/graphiql-ide.md).
* [De REST-API voor middelen](/help/assets/content-fragments/assets-api-content-fragments.md) Hiermee kunt u inhoudsfragmenten (en andere elementen) maken en wijzigen.

>[!NOTE]
>
>De [Inhoudsfragment en Inhoudsfragmentmodel OpenAPI&#39;s](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

De rest van deze handleiding is gericht op GraphQL-toegang en levering van inhoudsfragmenten.

## GraphQL-eindpunt inschakelen {#enable-graphql-endpoint}

Voordat de GraphQL API&#39;s kunnen worden gebruikt, moet een GraphQL-eindpunt worden gemaakt.

1. Navigeren naar **Gereedschappen**, **Algemeen** selecteert u vervolgens **GraphQL**.
1. Selecteren **Maken**.
1. De **Nieuw GraphQL-eindpunt maken** wordt geopend. Hier kunt u opgeven:
   * **Naam**: naam van het eindpunt; u kunt elke tekst invoeren.
   * **GraphQL-schema gebruiken dat wordt geleverd door**: gebruik de vervolgkeuzelijst om de vereiste configuratie te selecteren.
1. Bevestigen met **Maken**.
1. In de console **Pad** wordt weergegeven op basis van de eerder gemaakte configuratie. Dit pad wordt gebruikt om GraphQL-query&#39;s uit te voeren.

   ```
   /content/cq:graphql/<configuration-name>/endpoint
   ```

Meer informatie over inschakelen [Hier vindt u GraphQL-eindpunten](/help/headless/graphql-api/graphql-endpoint.md).

## Inhoud opvragen met GraphQL met GraphiQL

De architecten van informatie ontwerpen vragen voor hun kanaal eindpunten om inhoud te leveren. Overweeg deze vragen slechts eenmaal per eindpunt, per model. In deze gids Aan de slag hoeft u slechts één gids te maken.

GraphiQL is een IDE die in uw AEM milieu inbegrepen is; het is toegankelijk/zichtbaar na u [uw eindpunten configureren](#enable-graphql-endpoint).

1. Logboek in AEM as a Cloud Service en toegang tot de interface GraphiQL:

   U kunt tot de vraagredacteur van één van beiden toegang hebben:

   * **Gereedschappen** > **Algemeen** > **GraphQL Query Editor**
   * rechtstreeks; bijvoorbeeld `http://localhost:4502/aem/graphiql.html`

1. GraphiQL winde is een in-browser vraagredacteur voor GraphQL. U kunt het gebruiken om vragen te bouwen om de Fragmenten van de Inhoud terug te winnen om hen zonder hoofd als JSON te leveren.
   * Met de vervolgkeuzelijst rechtsboven kunt u het eindpunt selecteren.
   * Een uiterst linker paneel maakt een lijst van de voortgezette vragen (indien beschikbaar)
   * In het linkerdeelvenster van het midden kunt u een query maken.
   * De resultaten worden weergegeven in het rechtermiddelste deelvenster.
   * De vraagredacteur kenmerkt codevoltooiing en hotkeys om de vraag gemakkelijk uit te voeren.

   ![GraphiQL-editor](../assets/graphiql.png)

1. Ervan uitgaande dat het model dat u hebt gemaakt, werd aangeroepen `person` met velden `firstName`, `lastName`, en `position`kunt u een eenvoudige query maken om de inhoud van het inhoudsfragment op te halen.

   ```text
   query 
   {
     personList {
       items {
         _path
         firstName
         lastName
         position
       }
     }
   }
   ```

1. Voer de query in het linkerdeelvenster in.
   ![GraphiQL-query](../assets/graphiql-query.png)

1. Klik op de knop **Query uitvoeren** of de knop `Ctrl-Enter` en de resultaten worden als JSON weergegeven in het rechterdeelvenster.
   ![GraphiQL-resultaten](../assets/graphiql-results.png)

1. Klik in de rechterbovenhoek van de pagina op de knop **Docs** verbinding om in-context documentatie te tonen zodat kunt u uw vragen bouwen die aan uw eigen modellen aanpassen.
   ![GraphiQL-documentatie](../assets/graphiql-documentation.png)

GraphQL laat gestructureerde vragen toe die niet alleen specifieke gegevensreeksen of individuele gegevensvoorwerpen kunnen richten, maar ook specifieke elementen van de voorwerpen, genestelde resultaten, biedt steun voor vraagvariabelen, en veel meer kunnen leveren.

GraphQL kan herhalende API-aanvragen en overlevering voorkomen en maakt het in plaats daarvan mogelijk om in grote hoeveelheden te leveren wat precies nodig is voor rendering als reactie op één API-query. De resulterende JSON kan worden gebruikt om gegevens te leveren aan andere sites of apps.

## Volgende stappen {#next-steps}

Dat is het! U hebt nu een basiskennis van beheer van inhoud zonder kop in AEM. Er zijn veel meer bronnen waar u dieper kunt duiken voor een volledig begrip van de beschikbare functies.

* **[Inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/managing.md)** - Voor meer informatie over het maken en beheren van inhoudsfragmenten
* **[Ondersteuning voor inhoudsfragmenten in AEM Assets HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md)** - Voor meer informatie over het rechtstreeks benaderen van AEM inhoud via de HTTP-API, via CRUD-bewerkingen (Maken, Lezen, Bijwerken, Verwijderen)
* **[GRAPHQL API](/help/headless/graphql-api/content-fragments.md)** - Voor meer informatie over hoe u inhoudsfragmenten zonder problemen kunt leveren

>[!NOTE]
>
>De [Inhoudsfragment en Inhoudsfragmentmodel OpenAPI&#39;s](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.
