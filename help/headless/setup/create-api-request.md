---
title: Een API-verzoek maken - headless Setup
description: Leer hoe u de GraphQL API kunt gebruiken voor koploze levering van inhoud van inhoudsfragmenten en AEM middelen REST API voor het beheer van inhoudsfragmenten.
exl-id: 2b72f222-2ba5-4a21-86e4-40c763679c32
source-git-commit: c44c58398da3d82be04e22a5e4293e79361a8def
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# Een API-verzoek maken - headless Setup {#accessing-delivering-content-fragments}

Leer hoe u de GraphQL API kunt gebruiken voor koploze levering van inhoud van inhoudsfragmenten en AEM middelen REST API voor het beheer van inhoudsfragmenten.

>[!NOTE]
>
>Een deel van de functionaliteit van deze functie is beschikbaar in het prereleasekanaal. Met name functionaliteit met betrekking tot doorlopende query&#39;s.
> 
>Zie de [Prerelease Channel-documentatie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#enable-prerelease) voor informatie over hoe u de functie voor uw omgeving kunt inschakelen.

## Wat zijn GraphQL- en Assets REST-API&#39;s? {#what-are-the-apis}

[Nu u enkele inhoudsfragmenten hebt gemaakt,](create-content-fragment.md) u kunt AEM API&#39;s gebruiken om ze zonder kop te leveren.

* [De GraphQL API](/help/headless/graphql-api/content-fragments.md) staat u toe om verzoeken tot toegang te creëren en inhoudsfragmenten te leveren. Deze API biedt de meest robuuste set mogelijkheden voor het opvragen en gebruiken van inhoud met fragmentinhoud.
   * Om dit te gebruiken, [eindpunten moeten worden gedefinieerd en ingeschakeld in AEM](/help/headless/graphql-api/graphql-endpoint.md)en, indien nodig, de [GraphiQL-interface geïnstalleerd](/help/headless/graphql-api/graphiql-ide.md).
* [De REST-API voor middelen](/help/assets/content-fragments/assets-api-content-fragments.md) Hiermee kunt u inhoudsfragmenten (en andere elementen) maken en wijzigen.

De rest van deze gids zal zich op toegang GraphQL en de levering van het Fragment van de Inhoud concentreren.

## GraphQL-eindpunt inschakelen

Alvorens GraphQL APIs kan worden gebruikt, moet een eindpunt GraphQL worden gecreeerd.

1. Navigeren naar **Gereedschappen**, **Algemeen** selecteert u vervolgens **GraphQL**.
1. Selecteer **Maken**.
1. De **Nieuw GraphQL-eindpunt maken** wordt geopend. Hier kunt u opgeven:
   * **Naam**: naam van het eindpunt; U kunt elke gewenste tekst invoeren.
   * **GrafiekQL-schema gebruiken dat is opgegeven door**: gebruik dropdown om de vereiste configuratie te selecteren.
1. Bevestigen met **Maken**.
1. In de console a **Pad** wordt nu weergegeven op basis van de eerder gemaakte configuratie. Dit is het pad dat wordt gebruikt om GraphQL-query&#39;s uit te voeren.

   ```
   /content/cq:graphql/<configuration-name>/endpoint
   ```

Meer informatie over inschakelen [De eindpunten van GraphQL zijn hier te vinden](/help/headless/graphql-api/graphql-endpoint.md).

## Vraag inhoud gebruikend GraphQL met GraphiQL

De architecten van de informatie zullen vragen voor hun kanaaleindpunten moeten ontwerpen om inhoud te leveren. Deze vragen zullen over het algemeen slechts eens per eindpunt per model moeten worden overwogen. Met het oog op deze gids om aan de slag te gaan, zullen wij slechts één gids moeten creëren.

GraphiQL is winde die op een AEM milieu kan worden geïnstalleerd. Voer de volgende stappen uit [GraphiQL IDE gebruiken](/help/headless/graphql-api/graphiql-ide.md) om op uw AEM te installeren.

1. Logboek in AEM as a Cloud Service en toegang tot de interface GraphiQL:

   U kunt tot de vraagredacteur van één van beiden toegang hebben:

   * **Gereedschappen** -> **Algemeen** -> **GraphQL Query Editor**
   * rechtstreeks; bijvoorbeeld: `http://localhost:4502/aem/graphiql.html`

1. GrahiQL winde is een in-browser vraagredacteur voor GraphQL. U kunt het gebruiken om vragen te bouwen om de Fragmenten van de Inhoud terug te winnen om hen zonder hoofd als JSON te leveren.
   * Met de vervolgkeuzelijst rechtsboven kunt u het eindpunt selecteren.
   * Een uiterst linker paneel maakt een lijst van de voortgezette vragen (indien beschikbaar)
   * In het deelvenster links in het midden kunt u uw query samenstellen.
   * De resultaten worden weergegeven in het rechtermiddelste deelvenster.
   * De vraagredacteur kenmerkt codevoltooiing en hotkeys om de vraag gemakkelijk uit te voeren.

   ![GraphiQL-editor](../assets/graphiql.png)

1. Ervan uitgaande dat het model dat we hebben gemaakt, werd aangeroepen `person` met velden `firstName`, `lastName`, en `position`, kunnen wij een eenvoudige vraag bouwen om de inhoud van ons Inhoudsfragment terug te winnen.

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

1. Klik op de knop **Docs** Klik op de koppeling rechtsboven op de pagina om documentatie in de context weer te geven waarmee u query&#39;s kunt maken die u kunt aanpassen aan uw eigen modellen.
   ![GraphiQL-documentatie](../assets/graphiql-documentation.png)

GraphQL laat gestructureerde vragen toe die niet alleen specifieke gegevensreeksen of individuele gegevensvoorwerpen kunnen richten, maar ook specifieke elementen van de voorwerpen, genestelde resultaten kunnen leveren, biedt steun voor vraagvariabelen, en veel meer.

GraphQL kan iteratieve API-verzoeken en overlevering vermijden en maakt in plaats daarvan bulklevering mogelijk van exact wat nodig is voor rendering als reactie op één API-query. De resulterende JSON kan worden gebruikt om gegevens te leveren aan andere sites of apps.

## Volgende stappen {#next-steps}

Dat is het! U hebt nu een basiskennis van beheer van inhoud zonder kop in AEM. Natuurlijk zijn er veel meer middelen waar u zich verdiept voor een uitgebreid inzicht in de beschikbare functies.

* **[Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md)** - Meer informatie over het maken en beheren van inhoudsfragmenten
* **[Ondersteuning voor inhoudsfragmenten in AEM Assets HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md)** - Voor meer informatie over het rechtstreeks benaderen van AEM inhoud via de HTTP-API, via CRUD-bewerkingen (Maken, Lezen, Bijwerken, Verwijderen)
* **[GraphQL API](/help/headless/graphql-api/content-fragments.md)** - Voor meer informatie over hoe u inhoudsfragmenten zonder problemen kunt leveren
