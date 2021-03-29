---
title: Toegang tot en levering van contentfragmenten zonder kop Handleiding voor snel starten
description: Leer hoe u AEM Assets REST API kunt gebruiken voor het beheer van inhoudsfragmenten en de GraphQL API voor de levering van inhoud zonder kop.
translation-type: tm+mt
source-git-commit: e7ca6dc841ba777384be74021a27d523d530a956
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---


# Koploze gids {#accessing-delivering-content-fragments} openen en leveren van inhoudsfragmenten

Leer hoe u AEM Assets REST API kunt gebruiken voor het beheer van inhoudsfragmenten en de GraphQL API voor de levering van inhoud zonder kop.

## Wat zijn GraphQL- en Assets REST-API&#39;s? {#what-are-the-apis}

[Nu u enkele inhoudsfragmenten hebt gemaakt, kunt ](create-content-fragment.md) u AEM API&#39;s gebruiken om deze zonder kop te leveren.

* [Met de GraphQL ](/help/assets/content-fragments/graphql-api-content-fragments.md) API kunt u aanvragen maken voor toegang tot en levering van inhoudsfragmenten.
* [Met de REST ](/help/assets/content-fragments/assets-api-content-fragments.md) API voor middelen kunt u inhoudsfragmenten (en andere elementen) maken en wijzigen.

De rest van deze gids zal zich op toegang GraphQL en de levering van het Fragment van de Inhoud concentreren.

## Een inhoudsfragment leveren met GraphQL {#how-to-deliver-a-content-fragment}

De architecten van de informatie zullen vragen voor hun kanaaleindpunten moeten ontwerpen om inhoud te leveren. Deze vragen zullen over het algemeen slechts eens per eindpunt per model moeten worden overwogen. Met het oog op deze gids om aan de slag te gaan, zullen wij slechts één gids moeten creëren.

<!-- Not in the UI yet - will need updating when it is -->
<!--
1. Log into AEM as a Cloud Service and from the main menu select **Tools -&gt; Assets -&gt; GraphQL** 
   * Alternatively open the page directly at `https://<host>:<port>/content/graphiql.html`.
-->

1. Logboek in AEM als Cloud Service en toegang tot de interface GraphiQL:
   * Bijvoorbeeld: `https://<host>:<port>/content/graphiql.html`.

1. GraphiQL is een in-browser vraagredacteur voor GraphQL. U kunt het gebruiken om vragen te bouwen om de Fragmenten van de Inhoud terug te winnen om hen hoofdelijk als JSON te leveren.
   * In het linkerdeelvenster kunt u een query maken.
   * De resultaten worden weergegeven in het rechterdeelvenster.
   * De vraagredacteur kenmerkt codevoltooiing en hotkeys om de vraag gemakkelijk uit te voeren.
      ![GraphiQL-editor](../assets/graphiql.png)

1. Ervan uitgaande dat het model dat we hebben gemaakt `person` is aangeroepen met velden `firstName`, `lastName` en `position`, kunnen we een eenvoudige query maken om de inhoud van ons inhoudsfragment op te halen.

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

1. Klik op de knop **Query uitvoeren** of gebruik de `Ctrl-Enter`-sneltoets en de resultaten worden als JSON weergegeven in het rechterdeelvenster.
   ![GraphiQL-resultaten](../assets/graphiql-results.png)

1. Klik op de koppeling **Docs** rechtsboven op de pagina om documentatie in de context weer te geven, zodat u query&#39;s kunt maken die u kunt aanpassen aan uw eigen modellen.
   ![GraphiQL-documentatie](../assets/graphiql-documentation.png)

GraphQL laat gestructureerde vragen toe die niet alleen specifieke gegevensreeksen of individuele gegevensvoorwerpen kunnen richten, maar ook specifieke elementen van de voorwerpen, genestelde resultaten kunnen leveren, biedt steun voor vraagvariabelen, en veel meer.

GraphQL kan iteratieve API-verzoeken en overlevering vermijden en maakt in plaats daarvan bulklevering mogelijk van exact wat nodig is voor rendering als reactie op één API-query. De resulterende JSON kan worden gebruikt om gegevens te leveren aan andere sites of apps.

## Volgende stappen {#next-steps}

Dat is het! U hebt nu een basiskennis van beheer van inhoud zonder kop in AEM. Natuurlijk zijn er veel meer middelen waar u zich verdiept voor een uitgebreid inzicht in de beschikbare functies.

* **De Browser**  van de configuratie - voor details over Browser van de Configuratie van de AEM
* **[Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md)**  - Voor meer informatie over het maken en beheren van inhoudsfragmenten
* **[Ondersteuning voor inhoudsfragmenten in AEM Assets HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md)**  - Voor meer informatie over het rechtstreeks benaderen van AEM inhoud via de HTTP-API via CRUD-bewerkingen (Maken, Lezen, Bijwerken, Verwijderen)
* **[GraphQL API](/help/assets/content-fragments/graphql-api-content-fragments.md)**  - Voor details over hoe te om de Fragmenten van de Inhoud zonder kop te leveren
