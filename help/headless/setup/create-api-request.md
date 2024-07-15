---
title: Een API-verzoek maken - headless Setup
description: Leer hoe u de GraphQL API kunt gebruiken voor koploze levering van inhoud met fragmenten en hoe u de Assets REST API AEM voor het beheer van inhoudsfragmenten.
exl-id: 2b72f222-2ba5-4a21-86e4-40c763679c32
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 0%

---

# Een API-verzoek maken - headless Setup {#accessing-delivering-content-fragments}

Leer hoe u de GraphQL API kunt gebruiken voor koploze levering van inhoud met fragmenten en hoe u de Assets REST API AEM voor het beheer van inhoudsfragmenten.

## Wat zijn GraphQL en Assets REST API&#39;s? {#what-are-the-apis}

[ nu dat u sommige inhoudsfragmenten hebt gecreeerd, ](create-content-fragment.md) kunt u AEM gebruiken APIs om hen zonder kop te leveren.

* [ GraphQL API ](/help/headless/graphql-api/content-fragments.md) laat u verzoeken tot toegang tot en levering van de Fragmenten van de Inhoud tot stand brengen. Deze API biedt de meest robuuste set mogelijkheden voor het opvragen en gebruiken van inhoud met fragmentinhoud.
   * Om API te gebruiken, [ bepaalt en laat eindpunten in AEM ](/help/headless/graphql-api/graphql-endpoint.md) toe, en indien nodig, de [ geïnstalleerde interface GraphiQL ](/help/headless/graphql-api/graphiql-ide.md).
* [ Assets REST API ](/help/assets/content-fragments/assets-api-content-fragments.md) laat u tot stand brengen en wijzigen de Fragmenten van de Inhoud (en andere activa).

>[!NOTE]
>
>Het [ Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.

De rest van deze handleiding is gericht op GraphQL-toegang en levering van inhoudsfragmenten.

## GraphQL-eindpunt inschakelen {#enable-graphql-endpoint}

Voordat de GraphQL API&#39;s kunnen worden gebruikt, moet een GraphQL-eindpunt worden gemaakt.

1. Navigeer aan **Hulpmiddelen**, **Algemeen**, dan uitgezocht **GraphQL**.
1. Selecteer **creeer**.
1. **creeer nieuwe de dialoogdoos van het Eindpunt van GraphQL** opent. Hier kunt u opgeven:
   * **Naam**: naam van het eindpunt; u kunt om het even welke tekst ingaan.
   * **schema van GraphQL van het Gebruik door** wordt verstrekt: gebruik de drop-down lijst om de vereiste configuratie te selecteren die.
1. Bevestig met **creeer**.
1. In de console, wordt de Weg van a **** getoond gebaseerd op de eerder gemaakte configuratie. Dit pad wordt gebruikt om GraphQL-query&#39;s uit te voeren.

   ```
   /content/cq:graphql/<configuration-name>/endpoint
   ```

Meer details over het toelaten van [ eindpunten van GraphQL kunnen hier ](/help/headless/graphql-api/graphql-endpoint.md) worden gevonden.

## Inhoud opvragen met GraphQL met GraphiQL

De architecten van informatie ontwerpen vragen voor hun kanaal eindpunten om inhoud te leveren. Overweeg deze vragen slechts eenmaal per eindpunt, per model. In deze gids Aan de slag hoeft u slechts één gids te maken.

GraphiQL is winde, inbegrepen in uw AEM milieu; het is toegankelijk/zichtbaar nadat u [ uw eindpunten ](#enable-graphql-endpoint) vormt.

1. Meld u aan bij AEM as a Cloud Service en open de GraphiQL-interface:

   U kunt tot de vraagredacteur van één van beiden toegang hebben:

   * **Hulpmiddelen** > **Algemeen** > **de Redacteur van de Vraag van GraphQL**
   * direct; bijvoorbeeld `http://localhost:4502/aem/graphiql.html`

1. GraphiQL winde is een in-browser vraagredacteur voor GraphQL. U kunt het gebruiken om vragen te bouwen om de Fragmenten van de Inhoud terug te winnen om hen zonder hoofd als JSON te leveren.
   * Met de vervolgkeuzelijst rechtsboven kunt u het eindpunt selecteren.
   * Een uiterst linker paneel maakt een lijst van de voortgezette vragen (indien beschikbaar)
   * In het linkerdeelvenster van het midden kunt u een query maken.
   * De resultaten worden weergegeven in het rechtermiddelste deelvenster.
   * De vraagredacteur kenmerkt codevoltooiing en hotkeys om de vraag gemakkelijk uit te voeren.

   ![ GraphiQL redacteur ](../assets/graphiql.png)

1. Ervan uitgaande dat het model dat u hebt gemaakt `person` is aangeroepen met velden `firstName` , `lastName` en `position` , kunt u een eenvoudige query maken om de inhoud van het inhoudsfragment op te halen.

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
   ![ GraphiQL vraag ](../assets/graphiql-query.png)

1. Klik de **Uitvoeren knoop van de Vraag** of gebruik `Ctrl-Enter` hotkey en de resultaten worden getoond als JSON in het juiste paneel.
   ![ GraphiQL resultaten ](../assets/graphiql-results.png)

1. In de hoger-juiste hoek van de pagina, klik de **verbinding van Dokken** om in-context documentatie te tonen zodat kunt u uw vragen bouwen die aan uw eigen modellen aanpassen.
   ![ documentatie GraphiQL ](../assets/graphiql-documentation.png)

GraphQL laat gestructureerde vragen toe die niet alleen specifieke gegevensreeksen of individuele gegevensvoorwerpen kunnen richten, maar ook specifieke elementen van de voorwerpen, genestelde resultaten, biedt steun voor vraagvariabelen, en veel meer kunnen leveren.

GraphQL kan herhalende API-aanvragen en overlevering voorkomen en maakt het in plaats daarvan mogelijk om in grote hoeveelheden te leveren wat precies nodig is voor rendering als reactie op één API-query. De resulterende JSON kan worden gebruikt om gegevens te leveren aan andere sites of apps.

## Volgende stappen {#next-steps}

Dat is het! U hebt nu een basiskennis van beheer van inhoud zonder kop in AEM. Er zijn veel meer bronnen waar u dieper kunt duiken voor een volledig begrip van de beschikbare functies.

* **[Fragmenten van de Inhoud](/help/sites-cloud/administering/content-fragments/managing.md)** - voor details over het creëren van en het beheren van de Fragmenten van de Inhoud
* **[de Steun van de Fragmenten van de Inhoud in HTTP API van AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)** - voor details bij de toegang tot van AEM inhoud direct over HTTP API, via de verrichtingen van CRUD (creeer, las, Update, schrap)
* **[GraphQL API](/help/headless/graphql-api/content-fragments.md)** - voor details op hoe te om de Fragmenten van de Inhoud zonder kop te leveren

>[!NOTE]
>
>Het [ Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.
