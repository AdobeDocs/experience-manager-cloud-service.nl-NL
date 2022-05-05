---
title: Het gebruiken van GrahiQL winde in AEM
description: Leer hoe u de GraphiQL IDE in Adobe Experience Manager gebruikt.
feature: Content Fragments,GraphQL API
exl-id: be2ebd1b-e492-4d77-b6ef-ffdea9a9c775
source-git-commit: 5f0221fad6086f8d5c5e9bd5164d05ea8d6e7d2c
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 0%

---

# GraphiQL IDE gebruiken {#graphiql-ide}

Tenuitvoerlegging van de norm [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) IDE is beschikbaar voor gebruik met de GraphQL API van Adobe Experience Manager (AEM) as a Cloud Service.

>[!NOTE]
>
>Een deel van de functionaliteit van deze functie is beschikbaar in het prereleasekanaal. Met name functionaliteit met betrekking tot doorlopende query&#39;s.
> 
>Zie de [Prerelease Channel-documentatie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#enable-prerelease) voor informatie over hoe u de functie voor uw omgeving kunt inschakelen.

>[!NOTE]
>
>GraphiQL is inbegrepen in AEM, maar door gebrek wordt het slechts toegelaten op `dev-authors` omgevingen.

>[!NOTE]
>U moet [Uw eindpunten geconfigureerd](/help/headless/graphql-api/graphql-endpoint.md) in de [configuratievenster](/help/assets/content-fragments/content-fragments-configuration-browser.md) voordat u GraphiQL IDE gebruikt.


De **GraphiQL** het hulpmiddel staat u toe om uw vragen te testen en te zuiveren GraphQL door u toe te laten:
* Selecteer de **Endpoint** aangewezen aan de configuratie van Plaatsen die u voor uw vragen wilt gebruiken
* direct nieuwe query&#39;s invoeren
* creëren en openen, **[Blijvende query&#39;s](/help/headless/graphql-api/persisted-queries.md)**
* stel uw vragen in werking om de resultaten onmiddellijk te zien
* beheren **Query-variabelen**
* opslaan en beheren **Blijvende query&#39;s**
* publiceren of publiceren ongedaan maken, **Blijvende query&#39;s** (van `dev-publish`)
* zie **Historie** van uw vorige vragen
* gebruiken **Documentatieverkenner** toegang tot de documentatie; helpen u te leren en te begrijpen welke methoden beschikbaar zijn.

U kunt tot de vraagredacteur van één van beiden toegang hebben:

* **Gereedschappen** -> **Algemeen** -> **GraphQL Query Editor**
* rechtstreeks; bijvoorbeeld: `http://localhost:4502/aem/graphiql.html`

![GraphiQL Interface](assets/cfm-graphiql-interface.png "GraphiQL Interface")

U kunt GraphiQL op uw systeem van de ontwikkelauteur gebruiken zodat zij door uw cliënttoepassing kunnen worden gevraagd gebruikend verzoeken, en het publiceren vragen. Voor productiegebruik moet u vervolgens [verplaats uw vragen naar uw productieomgeving](/help/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production). Aanvankelijk aan productieauteur voor het bevestigen van onlangs authored inhoud met de vragen, en productie publiceren voor levende consumptie.

## Het selecteren van uw eindpunt {#selecting-endpoint}

Als eerste stap moet u de **[Endpoint](/help/headless/graphql-api/graphql-endpoint.md)** die u voor de vragen wilt gebruiken. Het eindpunt is aangewezen aan de configuratie van Plaatsen die u voor uw vragen wilt gebruiken.

Dit is beschikbaar in de vervolgkeuzelijst rechtsboven.

## Een nieuwe query maken en doorgaan {#creating-new-query}

U kunt uw nieuwe vraag in de redacteur ingaan - die in het midden-linkerpaneel, direct onder het logo GraphiQL is.

>[!NOTE]
>
>Als u al een aanhoudende query hebt geselecteerd en in het deelvenster Editor wordt weergegeven, selecteert u `+` (naast **Blijvende query&#39;s**) om de editor leeg te maken voor de nieuwe query.

Begin gewoon te typen, de redacteur ook:

* gebruikt mouseOver om aanvullende informatie over elementen weer te geven
* biedt functies zoals syntaxismarkering, automatisch aanvullen en automatisch voorstellen

>[!NOTE]
>
>GraphQL-query&#39;s beginnen doorgaans met een `{` teken.
>
>Lijnen die beginnen met een `#` worden genegeerd.

Gebruiken **Opslaan als** om uw nieuwe vraag voort te zetten.

## Uw voortgezette query bijwerken {#updating-persisted-query}

Selecteer de query die u wilt bijwerken in de lijst in het dialoogvenster **Blijvende query&#39;s** (helemaal links).

De query wordt weergegeven in het deelvenster Editor. Breng de gewenste wijzigingen aan en gebruik vervolgens **Opslaan** om uw updates aan de persisted query vast te leggen.

## Bezig met uitvoeren van query&#39;s {#running-queries}

U kunt een nieuwe vraag in werking stellen onmiddellijk, of u kunt een voortgezette vraag laden en in werking stellen. Als u een blijvende query wilt laden, selecteert u deze in de lijst. De query wordt dan weergegeven in het editorpaneel.

In beide gevallen is de query die wordt weergegeven in het editorpaneel de query die wordt uitgevoerd wanneer u een van de volgende twee doet:

* klikken/tikken op de **Query uitvoeren** pictogram
* de toetsenbordcombinatie gebruiken `Control-Enter`

## Query-variabelen {#query-variables}

<!-- more details needed here? -->

Met GraphiQL IDE kunt u ook uw [Query-variabelen](/help/headless/graphql-api/content-fragments.md#graphql-variables).

Bijvoorbeeld:

![GrafiekQL-variabelen](assets/cfm-graphqlapi-03.png "GrafiekQL-variabelen")

## Doorlopende query&#39;s publiceren (dev-publish) {#publishing-persisted-queries}

Als u de doorlopende query in de lijst hebt geselecteerd (linkerdeelvenster), kunt u de opdracht **Publiceren** en **Publiceren ongedaan maken** handelingen. Hiermee worden ze geactiveerd in uw ontwikkelings-publicatieomgeving (`dev-publish`) voor eenvoudige toegang door uw toepassingen tijdens het testen.

>[!NOTE]
>
>De definitie van het voorgeheugen van de persisted query `Time To Live` {&quot;cache-control&quot;:&quot;parameter&quot;:value} heeft een standaardwaarde van 2 uur (7200 seconden).

## Door uw doorlopende query&#39;s in cache te plaatsen {#caching-persisted-queries}

AEM maakt de CDN-cache (Content Delivery Network) ongeldig op basis van een standaardtijd om te leven (TTL).

Deze waarde is ingesteld op:

* 7200 seconden is standaardTTL voor de Verzender en CDN; ook bekend als *gedeelde cache*
   * standaard: s-maxage=7200
* 60 is standaard TTL voor de cliënt (bijvoorbeeld, browser)
   * standaard: maxage=60

AEM vragen GraphQL die met GraphiQL UI werden voortgeduurd zullen standaardTTL op uitvoering gebruiken. Als u TTL voor uw vraag wilt veranderen GraphLQ, dan moet de vraag in plaats daarvan voortbestaan gebruikend de API methode. Dit impliceert het posten van de vraag aan AEM gebruikend CURL in uw interface van de bevellijn.

Een voorbeeld:

```xml
curl -X PUT \
    -H 'authorization: Basic YWRtaW46YWRtaW4=' \
    -H "Content-Type: application/json" \
    "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
    -d \
'{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
```

De `cache-control` kan worden ingesteld tijdens het maken (PUT) of later (bijvoorbeeld via een aanvraag voor een POST). Het cache-control is optioneel wanneer u de aanhoudend query maakt, omdat AEM de standaardwaarde kan opgeven. Zie [Hoe te om een vraag te handhaven GraphQL](/help/headless/graphql-api/persisted-queries.md#how-to-persist-query), bijvoorbeeld om een vraag voort te zetten gebruikend krullen.

## URL kopiëren om rechtstreeks toegang te krijgen tot de query {#copy-url}

De **URL kopiëren** Met deze optie kunt u een query simuleren door de URL te kopiëren die wordt gebruikt voor directe toegang tot de voortgezette query en de resultaten te bekijken. Dit kan vervolgens voor tests worden gebruikt; bijvoorbeeld door toegang te krijgen tot een browser:

<!--
  >[!NOTE]
  >
  >The URL will need [encoding before using programmatically](/help/headless/graphql-api/persisted-queries.md#encoding-query-url).
  >
  >The target environment might need adjusting, depending on your requirements.
-->

Bijvoorbeeld:

`http://localhost:4502/graphql/execute.json/global/article-list-01`

Door deze URL in browser te gebruiken, kunt u de resultaten bevestigen:

![GraphiQL - URL kopiëren](assets/cfm-graphiql-copy-url.png "GraphiQL - URL kopiëren")

De **URL kopiëren** Deze optie is toegankelijk via de drie verticale stippen rechts van de naam van de voortgezette query (het linkerdeelvenster):

![GraphiQL - URL kopiëren](assets/cfm-graphiql-persisted-query-options.png "GraphiQL - URL kopiëren")

## Doorlopende query&#39;s verwijderen {#deleting-persisted-queries}

De **Verwijderen** Deze optie is ook toegankelijk via de drie verticale stippen rechts van de naam van de blijvend query (het linkerdeelvenster).

<!-- what happens if you try to delete something that is still published? -->


## Uw blijvende query installeren op productie {#installing-persisted-query-production}

Na het ontwikkelen van en het testen van uw persistente vraag met GraphiQL, is het definitieve doel: [deze naar uw productieomgeving overbrengen](/help/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production) voor gebruik door uw toepassingen.

## Sneltoetsen {#keyboard-shortcuts}

Er zijn een selectie van toetsenbordkortere weg die directe toegang tot actiepictogrammen in winde verlenen:

* Query uitvoeren:  `Shift-Control-P`
* Query samenvoegen:  `Shift-Control-M`
* Query uitvoeren:  `Control-Enter`
* Automatisch aanvullen:  `Control-Space`

>[!NOTE]
>
>Op sommige toetsenborden `Control` key is gelabeld als `Ctrl`.
