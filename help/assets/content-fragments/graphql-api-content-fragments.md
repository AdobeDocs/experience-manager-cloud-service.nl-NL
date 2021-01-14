---
title: Inhoudslevering met behulp van inhoudsfragmenten met de Adobe Experience Manager als Cloud Service GraphQL API
description: Leer hoe u Content Fragments in Adobe Experience Manager (AEM) gebruikt als Cloud Service met de AEM GraphQL API voor levering van inhoud zonder kop.
translation-type: tm+mt
source-git-commit: da8fcf1288482d406657876b5d4c00b413461b21
workflow-type: tm+mt
source-wordcount: '2506'
ht-degree: 1%

---


# AEM GraphQL API voor gebruik met Content Fragments {#graphql-api-for-use-with-content-fragments}

>[!CAUTION]
>
>De AEM GraphQL API voor de Levering van Inhoudsfragmenten is op verzoek beschikbaar.
>
>Neem contact op met [Adobe Support](https://experienceleague.adobe.com/?lang=en&amp;support-solution=General#support) om de API voor uw AEM in te schakelen als een programma voor Cloud Servicen.

De Adobe Experience Manager als Cloud Service (AEM) GraphQL API die wordt gebruikt met Content Fragments is sterk gebaseerd op de standaard, open-source GraphQL API.

Door de GraphQL API in AEM te gebruiken, kunt u inhoudsfragmenten efficiënt aan JavaScript-clients leveren in CMS-implementaties zonder hoofd:

* Herhalende API-aanvragen voorkomen, zoals REST,
* ervoor zorgen dat de levering beperkt blijft tot de specifieke eisen;
* Het toestaan voor bulklevering van precies wat voor het teruggeven als antwoord op één enkele API vraag nodig is.

## De GraphQL API {#graphql-api}

*&quot;GraphQL is een taal en specificatie voor gegevensquery die in 2012 intern door Facebook zijn ontwikkeld voordat het in 2015 openbaar werd uitbesteed. Het biedt een alternatief voor op REST gebaseerde architecturen met als doel de productiviteit van ontwikkelaars te verhogen en de hoeveelheden overgedragen gegevens te minimaliseren. GraphQL wordt gebruikt in productie door honderden organisaties van om het even welke grootte..&quot;* Zie [GraphQL Foundation](https://foundation.graphql.org/).

Zie de volgende secties (onder andere bronnen) voor meer informatie over de GraphQL API:

* Bij [graphql.org](https://graphql.org):

   * [Inleiding tot GraphQL](https://graphql.org/learn)

   * [De GraphQL-specificatie](http://spec.graphql.org/)

* Op [graphql.com](https://graphql.com):

   * [Hulplijnen](https://www.graphql.com/guides/)

   * [Tutorials](https://www.graphql.com/tutorials/)

   * [Casestudy&#39;s](https://www.graphql.com/case-studies/)

GraphQL voor AEM implementatie is gebaseerd op de standaard Java Library GraphQL. Zie:

* [graphQL.org - Java](https://graphql.org/code/#java)

* [GraphQL Java bij GitHub](https://github.com/graphql-java)

## GraphiQL Interface {#graphiql-interface}

AEM Graph API omvat een implementatie van de standaard [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) interface. Hierdoor kunt u query&#39;s rechtstreeks invoeren en testen.

Bijvoorbeeld:

* `http://localhost:4502/content/graphiql.html`

Dit biedt functies zoals syntaxismarkering, automatisch aanvullen, automatisch voorstellen, samen met een geschiedenis en online documentatie:

![GraphiQL ](assets/cfm-graphiql-interface.png "InterfaceGraphiQL Interface")

## Gevallen gebruiken voor auteur- en publicatie-omgevingen {#use-cases-author-publish-environments}

De gebruiksgevallen kunnen van het type van AEM als Cloud Service milieu afhangen:

* Publicatie-omgeving; gebruikt voor:
   * Query-gegevens voor JS-toepassing (standaardgebruikscenario)

* Auteursomgeving; gebruikt voor:
   * Query-gegevens voor &quot;inhoudsbeheerdoeleinden&quot;:
      * GraphQL in AEM als Cloud Service is momenteel een alleen-lezen API.
      * De REST-API kan worden gebruikt voor CR(u)D-bewerkingen.

## Schema genereren {#schema-generation}

GraphQL is een sterk getypte API, wat betekent dat de gegevens duidelijk gestructureerd en georganiseerd moeten zijn door type.

De specificatie GraphQL verstrekt een reeks richtlijnen op hoe te om tot een robuuste API voor het ondervragen van gegevens over een bepaalde instantie te leiden. Om dit te doen, moet een cliënt [Schema](#schema-generation) halen, die alle types noodzakelijk voor een vraag bevat.

Voor Inhoudsfragmenten zijn de GraphQL-schema&#39;s (structuur en typen) gebaseerd op [Inhoudsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md) en hun gegevenstypen.

Als een gebruiker bijvoorbeeld een Content Fragment Model met de naam `Article` heeft gemaakt, AEM het object `article` van het type `ArticleModel` genereren. De velden in dit type komen overeen met de velden en gegevenstypen die in het model zijn gedefinieerd.

1. A Content Fragment Model:

   ![Inhoudsfragmentmodel voor gebruik met ](assets/cfm-graphqlapi-01.png "GraphQLContent-fragmentmodel voor gebruik met GraphQL")

1. Het corresponderende GraphQL-schema (uitvoer van de automatische documentatie GraphiQL):
   ![GrafiekQL-schema gebaseerd op ](assets/cfm-graphqlapi-02.png "ModelGraphQL-schema van inhoudsfragment op basis van model van inhoudsfragment")

   Dit toont aan dat het geproduceerde type `ArticleModel` verscheidene [gebieden](#fields) bevat.

   * Drie van hen zijn gecontroleerd door de gebruiker: `author`, `main` en `linked_article`.

   * De andere velden zijn automatisch toegevoegd door AEM en zijn nuttige methoden voor het verschaffen van informatie over een bepaald inhoudsfragment. in dit voorbeeld, `_path`, `_metadata`, `_variations`. Deze [helpergebieden](#helper-fields) zijn duidelijk met een voorafgaande `_` om tussen wat door de gebruiker is bepaald en wat auto-geproduceerd te onderscheiden.

1. Nadat een gebruiker tot een Fragment van de Inhoud leidt dat op het model van het Artikel wordt gebaseerd, kan het dan door GraphQL worden ondervraagd. Zie [Samplequery&#39;s](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-sample-queries) (gebaseerd op een [voorbeeldstructuur van inhoudsfragment voor gebruik met GraphQL](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)) voor voorbeelden.

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

Het schema wordt gediend door het zelfde eindpunt zoals de vragen GraphQL, met de cliënt die het feit behandelt dat het schema met de uitbreiding `GQLschema` wordt geroepen. Als u bijvoorbeeld een eenvoudig `GET`-verzoek uitvoert op `/content/graphql/endpoint.GQLschema`, wordt het schema uitgevoerd met het inhoudstype: `text/x-graphql-schema;charset=iso-8859-1`.

## Fields {#fields}

Binnen het schema zijn er afzonderlijke velden, van twee basiscategorieën:

* Velden die u genereert.

   Een selectie van [Veldtypen](#field-types) worden gebruikt om velden te maken op basis van de manier waarop u het model voor inhoudsfragmenten configureert. De veldnamen zijn afkomstig uit het veld **Eigenschapnaam** van het **Gegevenstype**.

   * Er is ook de **Render als** bezit om in overweging te nemen, omdat de gebruikers bepaalde gegevenstypes kunnen vormen; bijvoorbeeld als tekst met één regel of als een tekstveld met meerdere regels.

* GraphQL voor AEM genereert ook een aantal [helpervelden](#helper-fields).

   Deze worden gebruikt om een inhoudsfragment te identificeren of om meer informatie over een inhoudsfragment te krijgen.

### Veldtypen {#field-types}

GraphQL voor AEM ondersteunt een lijst met typen. Alle ondersteunde gegevenstypen van het Content Fragment Model en de corresponderende typen GraphQL worden weergegeven:

| Inhoudsfragmentmodel - Gegevenstype | Type GraphQL | Beschrijving |
|--- |--- |--- |
| Tekst met één regel | Tekenreeks, [String] |  Wordt gebruikt voor eenvoudige tekenreeksen, zoals namen van auteurs, locaties, enz. |
| Tekst met meerdere regels | Tekenreeks |  Wordt gebruikt voor het uitvoeren van tekst, zoals de hoofdtekst van een artikel |
| Getal |  Float, [Float] | Wordt gebruikt om het zwevende-kommagetal en de reguliere getallen weer te geven |
| Boolean |  Boolean |  Gebruikt om selectievakjes weer te geven → eenvoudige true/false-instructies |
| Datum en tijd | Kalender |  Wordt gebruikt om datum en tijd weer te geven in een ISO 8086-indeling |
| Opsomming |  Tekenreeks |  Wordt gebruikt om een optie weer te geven uit een lijst met opties die bij het maken van het model zijn gedefinieerd |
|  Tags |  [Tekenreeks] |  Wordt gebruikt om een lijst weer te geven met tekenreeksen die tags vertegenwoordigen die in AEM worden gebruikt |
| Content Reference |  Tekenreeks |  Wordt gebruikt om het pad naar een ander element in AEM weer te geven |
| Fragmentverwijzing |  *Een modeltype* |  Wordt gebruikt om te verwijzen naar een ander inhoudsfragment van een bepaald modeltype, dat is gedefinieerd toen het model werd gemaakt. |

### Helpvelden {#helper-fields}

Naast de gegevenstypen voor door de gebruiker gegenereerde velden, genereert GraphQL voor AEM ook een aantal *helper* velden om een inhoudsfragment beter te kunnen identificeren of om aanvullende informatie over een inhoudsfragment te kunnen verstrekken.

#### Pad {#path}

Het padveld wordt gebruikt als id in GraphQL. Het vertegenwoordigt het pad van het Content Fragment-element in de AEM opslagplaats. Dit is de id van een inhoudsfragment, omdat dit:

* uniek is binnen AEM,
* kan gemakkelijk worden opgehaald.

In de volgende code worden de paden weergegeven van alle inhoudsfragmenten die zijn gemaakt op basis van het inhoudsfragmentmodel `Person`.

```xml
{
  persons {
    items {
      _path
    }
  }
}
```

Als u één inhoudsfragment van een bepaald type wilt ophalen, moet u ook eerst het pad bepalen. bijvoorbeeld:

```xml
{
    person(_path="/content/dam/path/to/fragment/john-doe") {
        _path
        name
        first-name
    }
}
```

Zie [Voorbeeldquery - Een enkel City-fragment](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-single-city-fragment).

#### Metagegevens {#metadata}

Via GraphQL stelt AEM ook de metagegevens van een inhoudsfragment beschikbaar. Metagegevens zijn de informatie die een inhoudsfragment beschrijft, zoals de titel van een inhoudsfragment, het miniatuurpad, de beschrijving van een inhoudsfragment en de datum waarop het is gemaakt.

Aangezien metagegevens worden gegenereerd via de Schema-editor en als zodanig geen specifieke structuur hebben, is het GraphQL-type `TypedMetaData` geïmplementeerd om de metagegevens van een Content Fragment beschikbaar te maken. `TypedMetaData` stelt de informatie bloot die door de volgende scalaire types wordt gegroepeerd:

| Veld |
|--- |
| `stringMetadata:[StringMetadata]!` |
| `stringArrayMetadata:[StringArrayMetadata]!` |
| `intMetadata:[IntMetadata]!` |
| `intArrayMetadata:[IntArrayMetadata]!` |
| `floatMetadata:[FloatMetadata]!` |
| `floatArrayMetadata:[FloatArrayMetadata]!` |
| `booleanMetadata:[BooleanMetadata]!` |
| `booleanArrayMetadata:[booleanArrayMetadata]!`  |
| `calendarMetadata:[CalendarMetadata]!` |
| `calendarArrayMetadata:[CalendarArrayMetadata]!` |

Elk scalair type vertegenwoordigt of één enkel naam-waarde paar of een serie van naam-waarde paren, waar de waarde van dat paar van het type is het werd gegroepeerd.

Als u bijvoorbeeld de titel van een inhoudsfragment wilt ophalen, weten we dat deze eigenschap een String-eigenschap is, zodat we een query voor alle String-metagegevens uitvoeren:

Ga als volgt te werk om te zoeken naar metagegevens:

```xml
{
  person(_path: "/content/dam/path/to/fragment/john-doe") {
    _path
    _metadata {
      stringMetadata {
        name
        value
      }
    }
  }
}
```

U kunt alle types van meta-gegevensGrafiekQL bekijken als u het Gegenereerde schema GraphQL bekijkt. Alle modeltypes hebben het zelfde `TypedMetaData`.

>[!NOTE]
>
>**Verschil tussen normale metagegevens en arraymetagegevens**
>Onthoud dat `StringMetadata` en `StringArrayMetadata` beide verwijzen naar wat in de opslagplaats wordt opgeslagen, niet hoe u hen terugwint.
>
>Als u bijvoorbeeld het veld `stringMetadata` aanroept, ontvangt u een array van alle metagegevens die in de opslagplaats zijn opgeslagen als een `String`. Als u `stringArrayMetadata` aanroept, ontvangt u een array van alle metagegevens die in de opslagplaats zijn opgeslagen als `String[]`.

Zie [Voorbeeldquery voor metagegevens - Geef de metagegevens weer voor onderscheidingen met de naam GB](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-metadata-awards-gb).

#### Variaties {#variations}

Het veld `_variations` is geïmplementeerd om het opvragen van de variaties in een inhoudsfragment te vereenvoudigen. Bijvoorbeeld:

```xml
{
  person(_path: "/content/dam/path/to/fragment/john-doe") {
    _variations
  }
}
```

Zie [Voorbeeldquery - Alle steden met een benoemde variatie](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-cities-named-variation).

<!--
## Security Considerations {#security-considerations}
-->

## GrafiekQL-variabelen {#graphql-variables}

GraphQL laat variabelen toe om in de vraag worden geplaatst. Voor meer informatie kunt u de [documentatie GraphQL voor GraphiQL](https://graphql.org/learn/queries/#variables) zien.

Als u bijvoorbeeld alle inhoudsfragmenten van het type `Article` wilt ophalen die een specifieke variatie hebben, kunt u de variabele `variation` in GraphiQL opgeven:

![GraphQL ](assets/cfm-graphqlapi-03.png "VariablesGraphQL Variables")

```xml
### query
query GetArticlesByVariation($variation: String!) {
    articles(variation: $variation) {
        items {
            _path
            author
        }
    }
}
 
### in query variables
{
    "variation": "uk"
}
```

## GraphQL-richtlijnen {#graphql-directives}

In GraphQL is er een mogelijkheid om de vraag te veranderen die op variabelen wordt gebaseerd, genoemd Richtlijnen GraphQL.

Zo kunt u bijvoorbeeld het veld `adventurePrice` opnemen in een query voor alle `AdventureModels`, op basis van een variabele `includePrice`.

![GraphQL-](assets/cfm-graphqlapi-04.png "RichtlijnenGraphQL-richtlijnen")

```xml
query getAdventureByType($includePrice: Boolean!) {
  adventures {
    items {
      adventureType
      adventurePrice @include(if: $includePrice)
    }
  }
}
 
### in query variables
{
    "includePrice": true
}
```

## Blijvende query&#39;s (cache) {#persisted-queries-caching}

Na het voorbereiden van een vraag met een verzoek van de POST, kan het met een verzoek van de GET worden uitgevoerd dat door de geheime voorgeheugens van HTTP of een CDN kan worden in het voorgeheugen ondergebracht.

Dit wordt vereist aangezien de vragen van de POST gewoonlijk niet in het voorgeheugen ondergebracht zijn, en als het gebruiken van GET met de vraag als parameter er een significant risico is dat de parameter voor de diensten en tussenpersonen van HTTP te groot wordt.

Hier zijn de stappen die worden vereist om een bepaalde vraag voort te zetten:

>[!NOTE]
>Vóór dit moet **GraphQL Persistence Queries** worden toegelaten, voor de aangewezen configuratie. Zie [Functionaliteit van inhoudsfragment inschakelen in configuratievenster](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser) voor meer informatie.

1. Bereid de vraag door PUTing het aan het nieuwe eindpunt URL `/graphql/persist.json/<config>/<persisted-label>` voor.

   Maak bijvoorbeeld een doorlopende query:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
       }
     }
   }'
   ```

1. Controleer nu het antwoord.

   Controleer bijvoorbeeld of het programma is gelukt:

   ```xml
   {
     "action": "create",
     "configurationName": "wknd",
     "name": "plain-article-query",
     "shortPath": "/wknd/plain-article-query",
     "path": "/conf/wknd/settings/graphql/persistentQueries/plain-article-query"
   }
   ```

1. U kunt de voortgezette vraag dan opnieuw spelen door URL `/graphql/execute.json/<shortPath>` te KRIJGEN.

   Gebruik bijvoorbeeld de voortgezette query:

   ```xml
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Werk een voortgezette vraag door POSTing aan een reeds bestaand vraagweg bij.

   Gebruik bijvoorbeeld de voortgezette query:

   ```xml
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
         referencearticle {
           _path
         }
       }
     }
   }'
   ```

1. Een onbewerkte query maken.

   Bijvoorbeeld:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-wrapped" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }"}'
   ```

1. Creeer een verpakte onbewerkte vraag met geheim voorgeheugencontrole.

   Bijvoorbeeld:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
   ```

1. Maak een doorlopende query met parameters:

   Bijvoorbeeld:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-parameters" \
       -d \
   'query GetAsGraphqlModelTestByPath($apath: String!, $withReference: Boolean = true) {
     articleByPath(_path: $apath) {
       item {
         _path
           author
           main {
           plaintext
           }
           referencearticle @include(if: $withReference) {
           _path
           }
         }
       }
     }'
   ```

1. Een query uitvoeren met parameters.

   Bijvoorbeeld:

   ```xml
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   
   $ curl -X GET \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   ```

1. Als u de query wilt uitvoeren bij publiceren, moet de verwante boomstructuur worden gerepliceerd

   * Een POST voor replicatie gebruiken:

      ```xml
      $curl -X POST   http://localhost:4502/bin/replicate.json \
        -H 'authorization: Basic YWRtaW46YWRtaW4=' \
        -F path=/conf/wknd/settings/graphql/persistentQueries/plain-article-query \
        -F cmd=activate
      ```

   * Een pakket gebruiken:
      1. Maak een nieuwe pakketdefinitie.
      1. Neem de configuratie op (bijvoorbeeld `/conf/wknd/settings/graphql/persistentQueries`).
      1. Maak het pakket.
      1. Herhaal het pakket.
   * Het replicatie-/distributiehulpmiddel gebruiken.
      1. Ga naar het gereedschap Distributie.
      1. Selecteer boomactivering voor de configuratie (bijvoorbeeld `/conf/wknd/settings/graphql/persistentQueries`).
   * Een workflow gebruiken (via workflowstartconfiguratie):
      1. Definieer een workflowstartregel voor het uitvoeren van een workflowmodel dat de configuratie van verschillende gebeurtenissen zou repliceren (bijvoorbeeld, maken, wijzigen, enz.).



1. Zodra de vraagconfiguratie is op publiceren, zijn de zelfde principes van toepassing, enkel gebruikend het publiceereindpunt.

   >[!NOTE]
   >
   >Voor anonieme toegang veronderstelt het systeem dat ACL &quot;iedereen&quot;toestaat om toegang tot de vraagconfiguratie te hebben.
   >
   >Als dat niet het geval is, zal het niet kunnen uitvoeren.

   >[!NOTE]
   >
   >Eventuele puntkomma&#39;s (&quot;;&quot;) in de URL&#39;s moeten worden gecodeerd.
   >
   >Bijvoorbeeld, zoals in het verzoek om een voortgezette vraag uit te voeren:
   >
   >
   ```xml
   >curl -X GET \ "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3bapath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   >```

## Het vragen van het eindpunt GraphQL van een Externe Website {#query-graphql-endpoint-from-external-website}

>[!NOTE]
>
>Voor een gedetailleerd overzicht van het CORS middel delend beleid in AEM zie [Begrijpen het Middelen van het Middel van de Verkeer van Herkomst (CORS)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=en#understand-cross-origin-resource-sharing-(cors)).

Om een website van derden in staat te stellen JSON-uitvoer te gebruiken, moet een CORS-beleid worden geconfigureerd in de Git-opslagplaats van de klant. Dit wordt gedaan door een aangewezen OSGi CORS configuratiedossier voor het gewenste eindpunt toe te voegen. In deze configuratie moet een vertrouwde websitenaam (of regex) worden opgegeven waarvoor toegang moet worden verleend.

* Toegang tot het eindpunt GraphQL:

   * legering: [uw domein] of alloworiginregexp: [uw domeinregex]
   * Ondersteunde methoden: [POST]
   * toegestane paden: [&quot;/apps/graphql-enablement/content/endpoint.gql(/persisted)?&quot;]

* De toegang tot van GraphQL stelde vragen eindpunt voort:

   * legering: [uw domein] of alloworiginregexp: [uw domeinregex]
   * Ondersteunde methoden: [GET]
   * toegestane paden: [&quot;/graphql/execute.json/.*&quot;]

>[!CAUTION]
>
>Het blijft de verantwoordelijkheid van de klant om:
>
>* alleen toegang verlenen tot vertrouwde domeinen
>* geen jokerteken [*] syntaxis gebruiken; die de eindpunten GraphQL aan de volledige wereld zal blootstellen.



## Filteren {#filtering}

U kunt het filtreren in uw vragen gebruiken GraphQL om specifieke gegevens terug te keren.

Bij het filteren wordt een syntaxis gebruikt die is gebaseerd op logische operatoren en expressies.

Zie voor voorbeelden:

* details van [GraphQL voor AEM extensies](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-some-extensions)

* [Voorbeeldinhoud en -](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql) structuur voorbereid voor gebruik in voorbeeldquery&#39;s

* [Voorbeeldquery&#39;s met deze voorbeeldinhoud en -structuur](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-sample-queries-sample-content-fragment-structure)

* [Voorbeeldquery&#39;s op basis van het WKND-project](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-queries-using-wknd-project)

## Machtigingen {#permission}

De machtigingen zijn vereist voor toegang tot middelen.

<!-- to be addressed later -->

<!-- 
## Authentication {#authentication}
-->

<!-- to be addressed later -->

<!-- 
## Caching {#caching}
-->

<!-- to be addressed later -->

<!--
## Sorting {#sorting}
-->

<!-- to be addressed later -->

<!--
## Paging {#paging}
-->

## Eindpunten {#end-points}

Het eindpunt is de weg die wordt gebruikt om tot GraphQL voor AEM toegang te hebben. Met dit pad kunt u (of uw app) het volgende doen:

* toegang tot het GraphQL-schema;
* verzend uw vragen GraphQL,
* ontvangt de reacties (op uw vragen GraphQL).

Om toegang tot servers te hebben GraphQL in AEM moet u een eindpunt vormen. Dit omvat ook twee configuraties OSGi.

1. Het het Verdelen schema servlet die op verzoeken antwoordt om het GrafiekQL- schema terug te winnen:

   ![AEM Sites GraphQL Schema Servlet](assets/cfm-endpoint-01.png)

   * **Kiezers** (`sling.servlet.selectors`) moeten leeg blijven.

   * **De Types**  van middel (`sling.servlet.resourceTypes`) bepalen het middeltype dat servlet GraphQL zou moeten luisteren aan.
Bijvoorbeeld:
      `graphql-enablement/components/endpoint`.

   * **Methoden** (&#39;sling.servlet.methods^)

      De HTTP-methode waarnaar de servlet moet luisteren; gewoonlijk `GET`.

   * **Extensies** (`sling.servlet.extensions`)

      Geef de extensie op waarop de Schema Servlet moet reageren. In dit geval is het `GQLschema`, compatibel met de specificaties GraphQL.

2. servlet die aan grafische verzoeken beantwoordt:

   ![Apache Sling GraphQL Servlet](assets/cfm-endpoint-02.png)

   * **Kiezers** (`sling.servlet.selectors`) moeten leeg blijven.

   * **Het Type**  van middel (`sling.servlet.resourceTypes`) het middeltype de servlet GraphQL zou moeten antwoorden aan.
Bijvoorbeeld, `graphql-enablement/components/endpoint`.

   * **Methoden** (`sling.servlet.methods`) De HTTP-methoden waarop het GraphQL-servlet moet reageren, meestal  `GET` en  `POST`.

   * **Extensies** (`sling.servlet.extensions`) De extensie die luistert naar GraphQL-verzoeken, meestal  `gql`.

3. U moet nu een eindpunt tot stand brengen - een knoop van het verbinden:resourceType die in deze configuraties wordt bepaald.
Bijvoorbeeld, om een eindpunt tot stand te brengen voor het terugwinnen van het Schema GraphQL creeer een nieuw knooppunt onder `/apps/<my-site>/graphql`:

   * Naam: `endpoint`
   * Primair type: `nt:unstructured`
   * sling:resourceType: `graphql-enablement/components/endpoint`

## Veelgestelde vragen {#faqs}

De gerezen vragen:

1. **V**: &quot;*Hoe is GraphQL API voor AEM anders dan de API van de Bouwer van de Vraag?*&quot;

   * **A**: &quot;*De AEM GraphQL API biedt volledige controle op de JSON-uitvoer en is een industriestandaard voor het opvragen van inhoud.
Als u verder gaat, is AEM van plan te investeren in de AEM GraphQL API.*&quot;

## Zelfstudie - Aan de slag met AEM zonder kop en GraphQL {#tutorial}

Op zoek naar een praktische zelfstudie? Ontdek [Aan de slag met AEM Headless en GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) de zelfstudie van begin tot eind waarin wordt geïllustreerd hoe u in een CMS-scenario inhoud kunt ontwikkelen en beschikbaar maken met de GraphQL-API&#39;s van AEM en die door een externe toepassing wordt verbruikt.