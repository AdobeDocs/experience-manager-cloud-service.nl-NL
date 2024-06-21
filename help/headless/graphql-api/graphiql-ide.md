---
title: GraphiQL IDE gebruiken in AEM
description: Leer hoe u de GraphiQL IDE in Adobe Experience Manager gebruikt.
feature: Headless, Content Fragments,GraphQL API
exl-id: be2ebd1b-e492-4d77-b6ef-ffdea9a9c775
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 0%

---

# GraphiQL IDE gebruiken {#graphiql-ide}

Tenuitvoerlegging van de norm [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) IDE is beschikbaar voor gebruik met de GraphQL API van as a Cloud Service Adobe Experience Manager (AEM).

>[!NOTE]
>
>GraphiQL is inbegrepen in alle milieu&#39;s van AEM (maar zal slechts toegankelijk/zichtbaar zijn wanneer u uw eindpunten vormt).
>
>In vorige versies was een pakket nodig om de GraphiQL IDE te installeren. Als u deze installatie hebt, kunt u deze nu verwijderen.

>[!NOTE]
>U moet [Uw eindpunten geconfigureerd](/help/headless/graphql-api/graphql-endpoint.md) in de [configuratievenster](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser) voordat u GraphiQL IDE gebruikt.

De **GraphiQL** kunt u testen en fouten opsporen in uw GraphQL-query&#39;s door het volgende in te schakelen:
* Selecteer de **Endpoint** aangewezen aan de configuratie van Plaatsen die u voor uw vragen wilt gebruiken
* direct nieuwe query&#39;s invoeren
* creëren en openen, **[Blijvende query&#39;s](/help/headless/graphql-api/persisted-queries.md)**
* stel uw vragen in werking om de resultaten onmiddellijk te zien
* beheren **Query-variabelen**
* opslaan en beheren **Blijvende query&#39;s**
* publiceren of publiceren ongedaan maken, **Blijvende query&#39;s**, aan of uw **Publiceren** of **Voorvertoning** dienst, bijvoorbeeld van/naar `dev-publish`
* zie **Historie** van uw vorige vragen
* gebruiken **Documentatieverkenner** om toegang te krijgen tot de documentatie, zodat u kunt leren welke methoden beschikbaar zijn en begrijpen.

U kunt tot de vraagredacteur van één van beiden toegang hebben:

* **Gereedschappen** > **Algemeen** > **GraphQL Query Editor**
* rechtstreeks; bijvoorbeeld `http://localhost:4502/aem/graphiql.html`

![GraphiQL Interface](assets/cfm-graphiql-interface.png "GraphiQL Interface")

U kunt GraphiQL op uw systeem gebruiken zodat de vragen door uw cliënttoepassing kunnen worden gevraagd gebruikend verzoeken, en voor het publiceren van vragen. Voor productiegebruik kunt u vervolgens [verplaats uw vragen naar uw productieomgeving](/help/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production). Aanvankelijk aan productieauteur voor het bevestigen van onlangs authored inhoud met de vragen, en productie publiceren voor levende consumptie.

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

De vraag wordt getoond in het redacteurspaneel. Breng de gewenste wijzigingen aan en gebruik vervolgens **Opslaan** om uw updates aan de persisted query vast te leggen.

## Query&#39;s uitvoeren {#running-queries}

U kunt een nieuwe vraag in werking stellen onmiddellijk, of u kunt een voortgezette vraag laden en in werking stellen. Als u een voortgezette query wilt laden, selecteert u deze in de lijst. De query wordt weergegeven in het deelvenster Editor.

In beide gevallen is de query die in het editorpaneel wordt weergegeven, de query die wordt uitgevoerd wanneer u een van de volgende twee doet:

* selecteren op de **Query uitvoeren** pictogram
* de toetsenbordcombinatie gebruiken `Control-Enter`

## Query-variabelen {#query-variables}

Met GraphiQL IDE kunt u ook uw [Query-variabelen](/help/headless/graphql-api/content-fragments.md#graphql-variables).

Bijvoorbeeld:

![GraphQL-variabelen](assets/cfm-graphqlapi-03.png "GraphQL-variabelen")

## Het beheren van geheime voorgeheugen voor uw persistente vragen {#managing-cache}

[Blijvende query&#39;s](/help/headless/graphql-api/persisted-queries.md) worden aanbevolen, omdat deze in de verzender- en CDN-lagen in het cachegeheugen kunnen worden opgeslagen, waardoor de prestaties van de toepassing die de aanvraag indient, uiteindelijk worden verbeterd. Standaard maakt AEM de CDN-cache (Content Delivery Network) ongeldig op basis van een standaardtijd tot live (TTL).

>[!NOTE]
>
>Zie [Door uw doorlopende query&#39;s in cache te plaatsen](/help/headless/graphql-api/persisted-queries.md#caching-persisted-queries).

>[!NOTE]
>
>Aangepaste herschrijfregels voor Dispatcher kunnen de standaardinstellingen van AEM publicatie overschrijven.
>
>Als u op TTL-Gebaseerde cache-control kopballen van de verzender verzendt, die op een patroon van de plaatsovereenkomst wordt gebaseerd, dan als het noodzakelijk is, zou u kunnen willen uitsluiten `/graphql/execute.json/*` van de wedstrijden.

Gebruikend GraphQL kunt u de Kopballen van het Geheime voorgeheugen van HTTP vormen om deze parameters voor uw individuele persisted vraag te controleren.

1. De **Kopteksten** Deze optie is toegankelijk via de drie verticale stippen rechts van de naam van de voortgezette query (het linkerdeelvenster):

   ![Blijvende HTTP-cache-headers van query](assets/cfm-graphqlapi-headers-01.png "Blijvende HTTP-cache-headers van query")

1. Als u dit selecteert, wordt het dialoogvenster **Cacheconfiguratie** dialoogvenster:

   ![Instellingen voor blijvende HTTP-cachekoptekst voor query](assets/cfm-graphqlapi-headers-02.png "Instellingen voor blijvende HTTP-cachekoptekst voor query")

1. Selecteer de gewenste parameter en pas vervolgens de gewenste waarde aan:

   * **cache-control** - **maximale leeftijd**
Deze inhoud kan gedurende een opgegeven aantal seconden in cache worden opgeslagen. Dit is doorgaans de TTL-browser (Time To Live).
   * **surrogaatcontrole** - **s-maxage**
Hetzelfde als maximale leeftijd, maar is specifiek van toepassing op proxycaches.
   * **surrogaatcontrole** - **stale-while-revalidate**
De bussen kunnen een caching reactie blijven dienen nadat het, tot het gespecificeerde aantal seconden stale wordt.
   * **surrogaatcontrole** - **stale-if-error**
In geval van een fout of een fout van de oorsprong kan het optreden van een cache gedurende een opgegeven aantal seconden worden voortgezet.

1. Selecteren **Opslaan** om de wijzigingen voort te zetten.

## Doorlopende query&#39;s publiceren en voorvertonen {#publishing-previewing-persisted-queries}

Als u de doorlopende query in de lijst hebt geselecteerd (linkerdeelvenster), kunt u de opdracht **Publiceren** handeling.

Hierdoor wordt de query geactiveerd naar de omgeving die u selecteert. U kunt kiezen tussen **Publiceren** milieu (bijvoorbeeld `dev-publish`) of uw **Voorvertoning** omgeving voor eenvoudige toegang door uw toepassingen tijdens het testen.

![GraphiQL -Published Persisted Query](assets/cfm-graphiql-publish.png "GraphiQL - Publish Persisted Query")

>[!NOTE]
>
>De definitie van het voorgeheugen van de persisted query `Time To Live` {&quot;cache-control&quot;:&quot;parameter&quot;:value} heeft een standaardwaarde van 2 uur (7200 seconden).

## Publiceren van doorlopende query&#39;s ongedaan maken {#unpublishing-persisted-queries}

Als bij het publiceren, kunt u, zodra u uw voortgezette vraag van de lijst (linkerpaneel) hebt geselecteerd, **Publiceren ongedaan maken** handeling.

Hierdoor wordt de query gedeactiveerd vanuit de omgeving die u selecteert; uw **Publiceren** of uw **Voorvertoning** milieu.

>[!NOTE]
>
>Zorg er ook voor dat u de benodigde wijzigingen in uw clienttoepassing hebt aangebracht om mogelijke problemen te voorkomen.

## URL kopiëren om rechtstreeks toegang te krijgen tot de query {#copy-url}

De **URL kopiëren** Met deze optie kunt u een query simuleren door de URL te kopiëren die wordt gebruikt om rechtstreeks toegang te krijgen tot de voortgezette query en de resultaten te bekijken. Dit kan vervolgens voor testdoeleinden worden gebruikt, bijvoorbeeld door toegang te krijgen tot een browser:

<!--
  >[!NOTE]
  >
  >The URL needs [encoding before using programmatically](/help/headless/graphql-api/persisted-queries.md#encoding-query-url).
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
