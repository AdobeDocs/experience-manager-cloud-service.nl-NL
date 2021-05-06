---
title: Hoe te om tot Uw Inhoud via AEM levering APIs toegang te hebben
description: In dit deel van de AEM Headless Ontwikkelaarsreis, leer hoe te om vragen te gebruiken GraphQL om tot uw inhoud van de Fragmenten van de Inhoud toegang te hebben.
hide: true
hidefromtoc: true
index: false
exl-id: 5ef557ff-e299-4910-bf8c-81c5154ea03f
translation-type: tm+mt
source-git-commit: dd30bbb57d2746a7b16cb0546b90df0758fc3740
workflow-type: tm+mt
source-wordcount: '2120'
ht-degree: 0%

---

# Hoe te om tot Uw Inhoud via AEM levering APIs {#access-your-content} toegang te hebben

>[!CAUTION]
>
>WERK IN VOORTGANG - De opstelling van dit document is aan de gang en mag niet worden opgevat als volledig of definitief en mag niet worden gebruikt voor productiedoeleinden.

In dit deel van [AEM Headless Developer Journey,](overview.md) kunt u leren hoe u GraphQL-query&#39;s kunt gebruiken om toegang te krijgen tot de inhoud van uw Content Fragments en deze te verzenden naar uw app (headless delivery).

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM headless reis, [Hoe te om Uw Inhoud te Model](model-your-content.md) leerde u de grondbeginselen van inhoud modelleren in AEM, zodat zou u nu moeten begrijpen hoe te om uw inhoudsstructuur te modelleren, dan realiseer die structuur gebruikend AEM Modellen van het Fragment van de Inhoud en de Fragments van de Inhoud:

* De concepten en terminologie met betrekking tot inhoudsmodellen herkennen.
* Begrijp waarom de inhoud modellering voor de levering van de Inhoud zonder Zwaartepunt nodig is.
* Begrijp hoe te om deze structuur te realiseren gebruikend AEM Modellen van het Fragment van de Inhoud (en auteursinhoud met de Fragmenten van de Inhoud.
* Begrijp hoe u uw inhoud modelleert; beginselen met basismonsters.

Dit artikel bouwt op die grondbeginselen voort zodat begrijpt u hoe te om tot uw bestaande inhoud zonder kop in AEM toegang te hebben gebruikend AEM GraphQL API.

* **Publiek**: Begin
* **Doel**: Leer hoe te om tot de inhoud van uw Fragmenten van de Inhoud toegang te hebben gebruikend AEM vragen GraphQL:
   * Introduceer GraphQL en de AEM GraphQL API.
   * Dive in de details van AEM GraphQL API.
   * Bekijk sommige steekproefvragen om te zien hoe de dingen in praktijk werken.

## Wilt u toegang tot uw inhoud? {#so-youd-like-to-access-your-content}

Dus...u hebt al deze inhoud, netjes gestructureerd (in inhoudsfragmenten), en enkel wachtend om uw nieuwe app te voeren. De vraag is: hoe kan het daar komen?

U hebt een manier nodig om specifieke inhoud als doel in te stellen, te selecteren wat u nodig hebt en terug te sturen naar uw app voor verdere verwerking.

Met Adobe Experience Manager (AEM) als Cloud Service, kunt u tot uw Contentfragmenten selectief toegang hebben, gebruikend AEM GraphQL API, om slechts de inhoud terug te keren die u nodig hebt. Dit betekent dat u zonder kop gestructureerde inhoud kunt leveren voor gebruik in uw toepassingen.

>[!NOTE]
>
>AEM GraphQL API is een aangepaste implementatie op basis van de standaard GraphQL API-specificatie.

## GraphQL - Een inleiding {#graphql-introduction}

GraphQL is een open-bronspecificatie die verstrekt:

* een querytaal waarmee u specifieke inhoud van gestructureerde objecten kunt selecteren.
* een runtime om deze query&#39;s uit te voeren met uw gestructureerde inhoud.

GraphQL is een *strongly* getypte API. Dit betekent dat *all* inhoud duidelijk gestructureerd en georganiseerd door type moet zijn, zodat GraphQL *begrijpt* wat aan toegang en hoe. De gegevensvelden worden gedefinieerd binnen GraphQL-schema&#39;s, die de structuur van de inhoudsobjecten definiëren.

De eindpunten van GraphQL verstrekken dan de wegen die aan de vragen GraphQL antwoorden.

Dit alles betekent dat uw app de inhoud die het nodig heeft nauwkeurig, betrouwbaar en efficiënt kan selecteren - precies wat u nodig hebt bij AEM.

>[!NOTE]
>
>Zie *GraphQL*.org en *GraphQL*.com.

## AEM en GraphQL {#aem-graphql}

GraphQL wordt gebruikt op verschillende locaties in AEM; bijvoorbeeld:

* Contentfragmenten
   * Er is een aangepaste API ontwikkeld voor deze gebruiksrechthoek (levering zonder koppen aan uw app).
      * Dit is de AEM GraphQL API.
* Handel
   * AEM de Handel verbruikt gegevens van een platform van de Handel via GraphQL.
   * Er zijn integratie GraphQL tussen AEM en diverse derde handeloplossingen, die met de uitbreidingshaken worden gebruikt door de Componenten van de Kern van CIF wordt verstrekt.
      * Hierbij wordt de AEM GraphQL API niet gebruikt.

>[!NOTE]
>
>Deze stap van de Headless Journey heeft alleen betrekking op de AEM GraphQL API en Content Fragments.

## AEM GraphQL API {#aem-graphql-api}

De AEM GraphQL API is een aangepaste versie gebaseerd op de standaard GraphQL API specificatie, speciaal gevormd om u toe te staan om (complexe) vragen op uw Contentfragmenten uit te voeren.

Inhoudsfragmenten worden gebruikt, omdat de inhoud is gestructureerd volgens Modellen van inhoudsfragmenten. Dit voldoet aan een basisvereiste van GraphQL.

* Een inhoudsfragmentmodel is samengesteld uit een of meer velden.
   * Elk veld wordt gedefinieerd op basis van een gegevenstype.
* De Modellen van het Fragment van de inhoud worden gebruikt om de overeenkomstige AEM Schema&#39;s te produceren GraphQL.

Om tot GraphQL voor AEM (en de inhoud) eigenlijk toegang te hebben wordt een eindpunt gebruikt om de toegangspad te verstrekken.

De inhoud die wordt geretourneerd via de AEM GraphQL API kan vervolgens door uw toepassingen worden gebruikt.

>[!NOTE]
>
>De implementatie van AEM GraphQL API is gebaseerd op de Java-bibliotheken GraphQL.

### Gevallen gebruiken voor auteur- en publicatie-omgevingen {#use-cases-author-publish-environments}

De gebruiksgevallen voor de AEM GraphQL API kunnen van het type van AEM als Cloud Service milieu afhangen:

* Publicatie-omgeving; gebruikt voor:
   * Inhoud opvragen voor JS-toepassing (standaard gebruikscenario)

* Auteursomgeving; gebruikt voor:
   * Inhoud opvragen voor &quot;inhoudsbeheerdoeleinden&quot;:
      * GraphQL in AEM als Cloud Service is momenteel een alleen-lezen API.
      * De REST-API kan worden gebruikt voor CR(u)D-bewerkingen.

## Inhoudsfragmenten voor gebruik met de AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

De Fragments van de inhoud kunnen als basis voor GraphQL voor AEM schema&#39;s en vragen als worden gebruikt:

* Hiermee kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren.
* Ze zijn gebaseerd op een Content Fragment Model, dat de structuur voor het resulterende fragment vooraf definieert aan de hand van gedefinieerde gegevenstypen.
* Er kunnen extra structuurlagen worden bereikt met het gegevenstype Fragmentverwijzing, dat beschikbaar is wanneer u een model definieert.

### Modellen van contentfragmenten {#content-fragments-models}

Deze modellen van inhoudsfragmenten:

* Wordt gebruikt om de Schema&#39;s te produceren, eens **Enabled**.

* Geef de gegevenstypen en velden op die vereist zijn voor GraphQL. Ze zorgen ervoor dat uw toepassing alleen vraagt wat mogelijk is en wat wordt verwacht ontvangt.

* Het gegevenstype **Fragmentverwijzingen** kan in uw model worden gebruikt om naar een ander Inhoudsfragment te verwijzen, en zo extra niveaus van structuur introduceren.

### Fragmentverwijzingen {#fragment-references}

De **Fragmentverwijzing**:

* Is een specifiek gegevenstype beschikbaar wanneer het bepalen van een Model van het Fragment van de Inhoud.

* Verwijst naar een ander fragment, afhankelijk van een specifiek inhoudsfragmentmodel.

* Hiermee kunt u gestructureerde gegevens maken en ophalen.

   * Wanneer gedefinieerd als een **multifeed**, kunnen meerdere subfragmenten door het prime-fragment naar verwezen (opgehaald) worden.

### JSON-voorvertoning {#json-preview}

Om u te helpen bij het ontwerpen en ontwikkelen van modellen van inhoudsfragmenten, kunt u een voorbeeld van JSON-uitvoer weergeven in de Content Fragment Editor.

## GraphQL-schema genereren op basis van inhoudsfragmenten {#graphql-schema-generation-content-fragments}

GraphQL is een sterk getypte API, wat betekent dat de inhoud duidelijk gestructureerd en georganiseerd moet zijn door type. De specificatie GraphQL verstrekt een reeks richtlijnen op hoe te om tot een robuuste API voor het ondervragen van inhoud op een bepaalde instantie te leiden. Om dit te doen, moet een cliënt het Schema halen, dat alle types noodzakelijk voor een vraag bevat.

Voor Inhoudsfragmenten, zijn de schema&#39;s GraphQL (structuur en types) gebaseerd op **Toegelaten** Modellen van het Fragment van de Inhoud en hun gegevenstypes.

>[!CAUTION]
>
>Alle schema&#39;s GraphQL (die uit de Modellen van het Fragment van de Inhoud worden afgeleid die **Enabled** zijn geweest) zijn leesbaar door het eindpunt GraphQL.
>
>Dit betekent dat u moet ervoor zorgen dat geen gevoelige inhoud beschikbaar is, om ervoor te zorgen dat geen gevoelige gegevens via eindpunten GraphQL worden blootgesteld; Dit omvat bijvoorbeeld informatie die als veldnamen in de modeldefinitie aanwezig kan zijn.

Als een gebruiker bijvoorbeeld een Content Fragment Model met de naam `Article` heeft gemaakt, AEM het object `article` van het type `ArticleModel` genereren. De velden in dit type komen overeen met de velden en gegevenstypen die in het model zijn gedefinieerd.

1. A Content Fragment Model:

   ![Inhoudsfragmentmodel voor gebruik met ](assets/graphqlapi-cfmodel.png "GraphQLContent-fragmentmodel voor gebruik met GraphQL")

1. Het corresponderende GraphQL-schema (uitvoer van de automatische documentatie GraphiQL):
   ![GrafiekQL-schema gebaseerd op ](assets/graphqlapi-cfm-schema.png "ModelGraphQL-schema van inhoudsfragment op basis van model van inhoudsfragment")

   Dit toont aan dat het geproduceerde type `ArticleModel` verscheidene [gebieden](#fields) bevat.

   * Drie van hen zijn gecontroleerd door de gebruiker: `author`, `main` en `referencearticle`.

   * De andere velden zijn automatisch toegevoegd door AEM en zijn nuttige methoden voor het verschaffen van informatie over een bepaald inhoudsfragment. in dit voorbeeld, `_path`, `_metadata`, `_variations`. Deze [helpergebieden](#helper-fields) zijn duidelijk met voorafgaande `_` om tussen wat door de gebruiker is bepaald en wat auto-geproduceerd te onderscheiden.

1. Nadat een gebruiker tot een Fragment van de Inhoud leidt dat op het model van het Artikel wordt gebaseerd, kan het dan door GraphQL worden ondervraagd. Bijvoorbeeld, zie de Steekproef Queries.md#graphql-steekproef-vragen) (die op een structuur van het Fragment van de steekproefinhoud voor gebruik met GraphQL wordt gebaseerd.

In GraphQL voor AEM, is het schema flexibel. Dit betekent dat deze telkens automatisch wordt gegenereerd wanneer een inhoudsfragmentmodel wordt gemaakt, bijgewerkt of verwijderd. De caches voor het gegevensschema worden ook vernieuwd wanneer u een model van het inhoudsfragment bijwerkt.

De dienst van GrafiekQL van Plaatsen luistert (in de achtergrond) naar om het even welke die wijzigingen aan een Model van het Fragment van de Inhoud worden aangebracht. Wanneer updates worden ontdekt, slechts wordt dat deel van het schema opnieuw geproduceerd. Deze optimalisatie bespaart tijd en zorgt voor stabiliteit.

Als u bijvoorbeeld:

1. Installeer een pakket met `Content-Fragment-Model-1` en `Content-Fragment-Model-2`:

   1. GraphQL-typen voor `Model-1` en `Model-2` worden gegenereerd.

1. Wijzig vervolgens `Content-Fragment-Model-2`:

   1. Alleen het type `Model-2` GraphQL wordt bijgewerkt.

   1. Terwijl `Model-1` hetzelfde zal blijven.

>[!NOTE]
>
>Dit is belangrijk om op te merken voor het geval u bulkupdates op de Modellen van het Fragment van de Inhoud door REST api, of anders wilt doen.

Het schema wordt gediend door het zelfde eindpunt zoals de vragen GraphQL, met de cliënt die het feit behandelt dat het schema met de uitbreiding `GQLschema` wordt geroepen. Als u bijvoorbeeld een eenvoudig `GET`-verzoek uitvoert op `/content/cq:graphql/global/endpoint.GQLschema`, wordt het schema uitgevoerd met het inhoudstype: `text/x-graphql-schema;charset=iso-8859-1`.

### Schema genereren - Niet-gepubliceerde modellen {#schema-generation-unpublished-models}

Wanneer Inhoudsfragmenten zijn genest, kan een bovenliggend inhoudsfragmentmodel worden gepubliceerd, maar een model waarnaar wordt verwezen, niet.

>[!NOTE]
>
>De AEM UI verhindert dit gebeurt, maar als het publiceren programmatically, of met inhoudspakketten wordt gemaakt, kan het voorkomen.

Wanneer dit gebeurt, AEM een *incomplete* Schema voor het model van het Fragment van de ouderinhoud produceert. Dit betekent dat de fragmentverwijzing, die afhankelijk is van het niet-gepubliceerde model, uit het schema wordt verwijderd.

## AEM GraphQL-eindpunten {#aem-graphql-endpoints}

<!--
need details/examples
-->

Een eindpunt is de weg die wordt gebruikt om tot GraphQL voor AEM toegang te hebben. Met dit pad kunt u (of uw app) het volgende doen:

* toegang tot de GraphQL-schema&#39;s;
* verzend uw vragen GraphQL,
* ontvangt de reacties (op uw vragen GraphQL).

AEM maakt het mogelijk:

* Een algemeen eindpunt - beschikbaar voor gebruik door alle plaatsen.
* De eindpunten van de huurder - die u kunt vormen, specifiek voor een gespecificeerde plaats/een project.

## Machtigingen {#permissions}

De machtigingen zijn vereist voor toegang tot middelen.

## De AEM GraphiQL-interface {#aem-graphiql-interface}

Om u te helpen direct input, en testvragen, is een implementatie van de standaardinterface GraphiQL beschikbaar voor gebruik met AEM GraphQL. Dit kan met AEM worden geïnstalleerd.

Het biedt functies zoals syntaxismarkering, automatisch aanvullen, automatisch suggereren, samen met een geschiedenis en online documentatie.

![GraphiQL ](assets/graphiql-interface.png "InterfaceGraphiQL Interface")

## Eigenlijk de AEM GraphQL API {#actually-using-aem-graphiql} gebruiken

Om werkelijk AEM GraphQL API in een vraag te gebruiken, kunnen wij de twee zeer basisstructuren van het Model van het Fragment van de Inhoud gebruiken:

* Bedrijf
   * Naam
   * CEO (Persoon)
   * Werknemers (personen)
* Person
   * Naam
   * Voornaam

Zoals u kunt zien, verwijzen de gebieden CEO en Werknemers, naar de fragmenten van de Persoon.

De fragmentmodellen worden gebruikt:

* wanneer u de inhoud maakt in de Content Fragment Editor
* om de schema&#39;s te produceren GraphQL die u zult vragen

De vragen kunnen in de interface GraphiQL, bijvoorbeeld bij zijn ingegaan:

* `http://localhost:4502/content/graphiql.html `

Een duidelijke vraag moet de naam van alle ingangen in het schema van het Bedrijf terugkeren. Hier kunt u een lijst met alle bedrijfsnamen aanvragen:

```xml
query {
  companyList {
    items {
      name
    }
  }
}
```

Een iets complexere vraag is om alle personen te selecteren die geen naam van &quot;Banen&quot;hebben. Hiermee worden alle personen gefilterd voor personen die niet de naam Taken hebben. Dit wordt bereikt met de operator EQUALS_NOT (er zijn nog veel meer):

```xml
query {
  personList(filter: {
    name: {
      _expressions: [
        {
          value: "Jobs"
          _operator: EQUALS_NOT
        }
      ]
    }
  }) {
    items {
      name
      firstName
    }
  }
}
```

U kunt ook complexere query&#39;s maken. Bijvoorbeeld, vraag voor alle bedrijven die minstens één werknemer met de naam van &quot;Smith&quot;hebben. Deze vraag illustreert het filtreren voor om het even welke persoon van naam &quot;Smith&quot;, die informatie van over de genestelde fragmenten terugkeert:

```xml
query {
  companyList(filter: {
    employees: {
      _match: {
        name: {
          _expressions: [
            {
              value: "Smith"
            }
          ]
        }
      }
    }
  }) {
    items {
      name
      ceo {
        name
        firstName
      }
      employees {
        name
        firstName
      }
    }
  }
}
```

<!-- need code / curl / cli examples-->

Voor de volledige details van het gebruiken van AEM GraphQL API, samen met het vormen van de noodzakelijke elementen, kunt u verwijzing:

* Leren gebruiken van GraphQL met AEM
* De structuur van het voorbeeldinhoudsfragment
* Leren gebruiken GraphQL met AEM - Voorbeeldinhoud en query&#39;s

## Volgende {#whats-next}

Nu u hebt geleerd om tot uw hoofdloze inhoud toegang te hebben en te vragen gebruikend AEM GraphQL API kunt u nu [leren hoe te om REST API te gebruiken om tot de inhoud van uw Inhoudsfragmenten](/help/implementing/developing/headless-journey/update-your-content.md) toegang te hebben en bij te werken.

## Aanvullende bronnen {#additional-resources}

* [GraphQL.org](https://graphql.org)
   * [Schemas](https://graphql.org/learn/schema/)
   * [Variabelen](https://graphql.org/learn/queries/#variables)
   * [GraphQL Java-bibliotheken](https://graphql.org/code/#java)
* [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql)
* [Leren gebruiken van GraphQL met AEM](/help/assets/content-fragments/graphql-api-content-fragments.md)
* [De structuur van het voorbeeldinhoudsfragment](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)
* [Leren gebruiken GraphQL met AEM - Voorbeeldinhoud en query&#39;s](/help/assets/content-fragments/content-fragments-graphql-samples.md)
   * [Voorbeeldquery - één specifiek stedenfragment](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-single-specific-city-fragment)
   * [Voorbeeldquery voor metagegevens - Lijst met metagegevens voor onderscheidingen: GB](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-metadata-awards-gb)
   * [Voorbeeldquery - Alle steden met een benoemde variatie](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-cities-named-variation)
* [Functionaliteit van inhoudsfragment inschakelen in configuratievenster](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)
* [Werken met contentfragmenten](/help/assets/content-fragments/content-fragments.md)
   * [Modellen van contentfragmenten](/help/assets/content-fragments/content-fragments-models.md)
   * [JSON-uitvoer](/help/assets/content-fragments/content-fragments-json-preview.md)
* [Werken met het delen van bronnen tussen verschillende bronnen (CORS)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=en#understand-cross-origin-resource-sharing-(cors))
* [Toegangstokens genereren voor server-side API&#39;s](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md)
* [Aan de slag met AEM Headless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html)  - Een korte videozelfstudie waarin een overzicht wordt gegeven van het gebruik van AEM functies zonder kop, zoals het modelleren van inhoud en GraphQL.
