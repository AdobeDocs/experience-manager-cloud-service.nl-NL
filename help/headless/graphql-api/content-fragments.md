---
title: GraphQL API AEM voor gebruik met inhoudsfragmenten
description: Leer hoe u inhoudsfragmenten in Adobe Experience Manager (AEM) kunt gebruiken die as a Cloud Service zijn met de AEM GraphQL API voor het leveren van inhoud zonder kop.
feature: Headless, Content Fragments,GraphQL API
exl-id: bdd60e7b-4ab9-4aa5-add9-01c1847f37f6
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '5400'
ht-degree: 0%

---


# GraphQL API AEM voor gebruik met inhoudsfragmenten {#graphql-api-for-use-with-content-fragments}

Leer hoe u inhoudsfragmenten in Adobe Experience Manager (AEM) kunt gebruiken die as a Cloud Service zijn met de AEM GraphQL API voor het leveren van inhoud zonder kop.

AEM as a Cloud Service GraphQL API die wordt gebruikt met Content Fragments is sterk gebaseerd op de standaard, open-source GraphQL API.

Door de GraphQL API in AEM te gebruiken, kunt u inhoudsfragmenten efficiënt aan JavaScript-clients leveren in CMS-implementaties zonder kop:

* Herhalende API-aanvragen voorkomen, zoals REST,
* ervoor zorgen dat de levering beperkt blijft tot de specifieke eisen;
* Het toestaan voor bulklevering van precies wat voor het teruggeven als antwoord op één enkele API vraag nodig is.

>[!NOTE]
>
>GraphQL wordt momenteel gebruikt in twee (afzonderlijke) scenario&#39;s in Adobe Experience Manager (AEM) as a Cloud Service:
>
>* [AEM Commerce gebruikt gegevens van een Commerce-platform via GraphQL](/help/commerce-cloud/integrating/magento.md).
>* AEM Content Fragments werken samen met de AEM GraphQL API (een aangepaste implementatie op basis van standaard GraphQL) voor gestructureerde inhoud voor gebruik in uw toepassingen.

>[!NOTE]
>
>Voor de meest recente informatie over Experience Manager-API&#39;s gaat u ook naar [Adobe Experience Manager as a Cloud Service API&#39;s](https://developer.adobe.com/experience-cloud/experience-manager-apis/).

## De GraphQL API {#graphql-api}

GraphQL is:

* &quot;*...een querytaal voor API&#39;s en een runtime voor het uitvoeren van deze query&#39;s met uw bestaande gegevens. GraphQL biedt een volledige en begrijpelijke beschrijving van de gegevens in uw API, geeft clients de mogelijkheid om precies te vragen wat ze nodig hebben en niets meer, maakt het gemakkelijker om API&#39;s in de loop der tijd te ontwikkelen en maakt krachtige ontwikkelaarsgereedschappen mogelijk.*&quot;.

  Zie [GraphQL.org](https://graphql.org)

* &quot;*...een open specificatie voor een flexibele API-laag. Plaats GraphQL over uw bestaande achtergronden om producten sneller dan ooit te bouwen...*&quot;.

  Zie [GraphQL verkennen](https://www.graphql.com).

* *&quot;...een taal en specificatie voor gegevensquery die in 2012 intern door Facebook zijn ontwikkeld, voordat deze in 2015 openbaar is gemaakt. Het biedt een alternatief voor op REST gebaseerde architecturen met als doel de productiviteit van ontwikkelaars te verhogen en de hoeveelheden overgedragen gegevens te minimaliseren. GraphQL wordt gebruikt in productie door honderden organisaties van elke omvang...&quot;*

  Zie [GraphQL Foundation](https://foundation.graphql.org/).

<!--
"*Explore GraphQL is maintained by the Apollo team. Our goal is to give developers and technical leaders around the world the tools they need to understand and adopt GraphQL.*". 
-->

Raadpleeg de volgende secties (onder andere over veel andere bronnen) voor informatie over de GraphQL API:

* At [graphql.org](https://graphql.org):

   * [Inleiding tot GraphQL](https://graphql.org/learn)

   * [De GraphQL-specificatie](https://spec.graphql.org/)

* At [graphql.com](https://graphql.com):

   * [Hulplijnen](https://www.graphql.com/guides/)

   * [Tutorials](https://www.graphql.com/tutorials/)

   * [Casestudy&#39;s](https://www.graphql.com/case-studies/)

De GraphQL for AEM-implementatie is gebaseerd op de standaard GraphQL Java Library. Zie:

* [graphQL.org - Java](https://graphql.org/code/#java)

* [GraphQL Java bij GitHub](https://github.com/graphql-java)

### GraphQL Terminologie {#graphql-terminology}

GraphQL gebruikt het volgende:

* **[Zoekopdrachten](https://graphql.org/learn/queries/)**

* **[Schema&#39;s en typen](https://graphql.org/learn/schema/)**:

   * Schema&#39;s worden gegenereerd door AEM op basis van de modellen van inhoudsfragmenten.
   * Met behulp van uw schema&#39;s geeft GraphQL de typen en bewerkingen weer die zijn toegestaan voor de GraphQL voor AEM implementatie.

* **[Velden](https://graphql.org/learn/queries/#fields)**

* **[GraphQL Endpoint](graphql-endpoint.md)**
   * Het pad in AEM dat reageert op GraphQL-query&#39;s en toegang biedt tot de GraphQL-schema&#39;s.

   * Zie [GraphQL Endpoint inschakelen](graphql-endpoint.md) voor nadere bijzonderheden.

Zie de [(GraphQL.org) Inleiding tot GraphQL](https://graphql.org/learn/) voor uitvoerige informatie, waaronder de [Aanbevolen procedures](https://graphql.org/learn/best-practices/).

### GraphQL-querytypen {#graphql-query-types}

Met GraphQL kunt u query&#39;s uitvoeren die worden geretourneerd:

* A **enkel item**

* A **[lijst van vermeldingen](https://graphql.org/learn/schema/#lists-and-non-null)**

AEM biedt mogelijkheden om query&#39;s (beide typen) om te zetten in [Blijvende query&#39;s, die in cache kunnen worden geplaatst](/help/headless/graphql-api/persisted-queries.md) door Dispatcher en de CDN.

### Best practices voor GraphQL-query (Dispatcher en CDN) {#graphql-query-best-practices}

De [Blijvende query&#39;s](/help/headless/graphql-api/persisted-queries.md) zijn de aanbevolen methode voor het publiceren van exemplaren als:

* ze zijn in cache geplaatst
* zij worden centraal beheerd door AEM as a Cloud Service

>[!NOTE]
>
>Gewoonlijk is er geen verzender/CDN op auteur, zodat is er geen aanwinst in het gebruiken van persisted query&#39;s daar; behalve het testen van hen.

GraphQL-query&#39;s die gebruikmaken van POST-aanvragen worden niet aanbevolen omdat ze niet in de cache zijn opgeslagen, zodat in een standaardinstantie de Dispatcher is geconfigureerd om dergelijke query&#39;s te blokkeren.

Hoewel GraphQL ook GET-aanvragen ondersteunt, kunnen deze limieten bereiken (bijvoorbeeld de lengte van de URL) die kunnen worden vermeden door middel van permanente query&#39;s.

Zie [Het in cache plaatsen van doorlopende query&#39;s inschakelen](/help/headless/deployment/dispatcher-caching.md) voor nadere bijzonderheden.

>[!NOTE]
>
>Om directe, en/of POST toe te staan, kunt de vragen in de Dispatcher u uw Beheerder van het Systeem vragen:
>
>* Een [Omgevingsvariabele Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) gebeld `ENABLE_GRAPHQL_ENDPOINT`
>* met de waarde `true`

>[!NOTE]
>
>De capaciteit om directe vragen uit te voeren kan op een bepaald punt in de toekomst worden verouderd.

### GraphiQL IDE {#graphiql-ide}

U kunt GraphQL-query&#39;s testen en fouten opsporen met de opdracht [GraphiQL IDE](/help/headless/graphql-api/graphiql-ide.md).

## Kwesties gebruiken voor auteur, voorvertoning en publicatie {#use-cases-author-preview-publish}

De gebruiksgevallen kunnen afhankelijk zijn van het type AEM as a Cloud Service omgeving:

* Publicatie-omgeving; wordt gebruikt voor:
   * Query-gegevens voor JS-toepassing (standaardgebruikscenario)

* Voorvertoningsomgeving; wordt gebruikt voor:
   * Vragen voorvertonen voorafgaand aan implementatie in de publicatieomgeving
      * Query-gegevens voor JS-toepassing (standaardgebruikscenario)

* Auteursomgeving; gebruikt voor:
   * Query-gegevens voor &quot;inhoudsbeheerdoeleinden&quot;:
      * GraphQL in AEM as a Cloud Service is momenteel een alleen-lezen API.
      * De REST-API kan worden gebruikt voor CR(u)D-bewerkingen.

## Machtigingen {#permission}

De machtigingen zijn vereist voor toegang tot middelen.

GraphQL query&#39;s worden uitgevoerd met toestemming van de AEM gebruiker van het onderliggende verzoek. Als de gebruiker geen leestoegang heeft tot bepaalde fragmenten (die als Elementen worden opgeslagen), zullen zij geen deel van de resultaatreeks worden.

Ook, moet de gebruiker toegang tot een eindpunt van GraphQL hebben om de vragen van GraphQL kunnen uitvoeren.

## Schema genereren {#schema-generation}

GraphQL is een sterk getypeerde API, wat betekent dat de gegevens duidelijk gestructureerd en ingedeeld moeten zijn per type.

De GraphQL-specificatie biedt een aantal richtlijnen voor het maken van een robuuste API voor het ondervragen van gegevens over een bepaalde instantie. Een client moet hiervoor de opdracht [Schema](#schema-generation), die alle typen bevat die nodig zijn voor een query.

Voor inhoudsfragmenten zijn de GraphQL-schema&#39;s (structuur en typen) gebaseerd op **Ingeschakeld** [Modellen van inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) en hun gegevenstypen.

>[!CAUTION]
>
>Alle GraphQL-schema&#39;s (afgeleid van Content Fragment Models) die zijn **Ingeschakeld**) zijn leesbaar via het GraphQL-eindpunt.
>
>Dit betekent dat u ervoor moet zorgen dat er geen gevoelige gegevens beschikbaar zijn, omdat deze op deze manier kunnen worden uitgelekt; dit omvat bijvoorbeeld informatie die als veldnamen in de modeldefinitie aanwezig kan zijn.

Als een gebruiker bijvoorbeeld een Content Fragment Model heeft gemaakt, genaamd `Article`AEM vervolgens een GraphQL-type genereert `ArticleModel`. De velden in dit type komen overeen met de velden en gegevenstypen die in het model zijn gedefinieerd. Bovendien leidt het tot sommige ingangspunten voor de vragen die op dit type werken, zoals `articleByPath` of `articleList`.

1. A Content Fragment Model:

   ![Inhoudsfragmentmodel voor gebruik met GraphQL](assets/cfm-graphqlapi-01.png "Inhoudsfragmentmodel voor gebruik met GraphQL")

1. Het corresponderende GraphQL-schema (uitvoer van de automatische documentatie GraphiQL):
   ![GraphQL-schema gebaseerd op inhoudsfragmentmodel](assets/cfm-graphqlapi-02.png "GraphQL-schema gebaseerd op inhoudsfragmentmodel")

   Dit toont aan dat het geproduceerde type `ArticleModel` bevat diverse [velden](#fields).

   * Drie van hen zijn gecontroleerd door de gebruiker: `author`, `main` en `referencearticle`.

   * De andere velden zijn automatisch AEM toegevoegd en zijn nuttige methoden voor het verschaffen van informatie over een bepaald inhoudsfragment, in dit voorbeeld (de [helpervelden](#helper-fields)) `_path`, `_metadata`, `_variations`.

1. Nadat een gebruiker een inhoudsfragment heeft gemaakt op basis van het artikelmodel, kan het vervolgens worden ondervraagd via GraphQL. Zie voor voorbeelden de [Voorbeeldquery&#39;s](/help/headless/graphql-api/sample-queries.md#graphql-sample-queries) (op basis van een [voorbeeldstructuur van inhoudsfragment voor gebruik met GraphQL](/help/headless/graphql-api/sample-queries.md#content-fragment-structure-graphql)).

In GraphQL for AEM is het schema flexibel. Dit betekent dat deze telkens automatisch wordt gegenereerd wanneer een inhoudsfragmentmodel wordt gemaakt, bijgewerkt of verwijderd. De caches voor het gegevensschema worden ook vernieuwd wanneer u een model van het inhoudsfragment bijwerkt.

<!-- move the following to a separate "in depth" page -->

De caches voor het gegevensschema worden ook vernieuwd wanneer u een model van het inhoudsfragment bijwerkt.

De service Sites GraphQL luistert (op de achtergrond) naar eventuele wijzigingen die zijn aangebracht in een inhoudsfragmentmodel. Wanneer updates worden ontdekt, slechts wordt dat deel van het schema opnieuw geproduceerd. Deze optimalisatie bespaart tijd en zorgt voor stabiliteit.

Als u bijvoorbeeld:

1. Een pakket installeren met `Content-Fragment-Model-1` en `Content-Fragment-Model-2`:

   1. GraphQL-typen voor `Model-1` en `Model-2` worden gegenereerd.

1. Vervolgens wijzigen `Content-Fragment-Model-2`:

   1. Alleen de `Model-2` GraphQL-type wordt bijgewerkt.

   1. Overwegende dat `Model-1` blijft hetzelfde.

>[!NOTE]
>
>Dit is belangrijk om op te merken voor het geval u bulkupdates op de Modellen van het Fragment van de Inhoud door REST api, of anders wilt doen.

Het schema wordt gediend door het zelfde eindpunt zoals de vragen van GraphQL, met de cliënt die het feit behandelt dat het schema met de uitbreiding wordt geroepen `GQLschema`. U kunt bijvoorbeeld een eenvoudige `GET` verzoek op `/content/cq:graphql/global/endpoint.GQLschema` resulteert in de uitvoer van het schema met het inhoudstype: `text/x-graphql-schema;charset=iso-8859-1`.

<!-- move through to here to a separate "in depth" page -->

### Schema genereren - Niet-gepubliceerde modellen {#schema-generation-unpublished-models}

Wanneer Inhoudsfragmenten zijn genest, kan een bovenliggend inhoudsfragmentmodel worden gepubliceerd, maar een model waarnaar wordt verwezen, niet.

>[!NOTE]
>
>De AEM UI verhindert dit gebeurt, maar als het publiceren programmatically, of met inhoudspakketten wordt gemaakt, kan het voorkomen.

Wanneer dit gebeurt, AEM een *onvolledig* Schema voor het bovenliggende inhoudsfragmentmodel. Dit betekent dat de fragmentverwijzing, die afhankelijk is van het niet-gepubliceerde model, uit het schema wordt verwijderd.

## Velden {#fields}

Binnen het schema zijn er afzonderlijke velden, van twee basiscategorieën:

* Velden die u genereert.

  Een selectie van [Gegevenstypen](#Data-types) worden gebruikt om velden te maken die zijn gebaseerd op de manier waarop u het inhoudsfragmentmodel configureert. De veldnamen zijn afkomstig uit het **Eigenschapnaam** van het **Gegevenstype** tab.

   * Er is ook **Renderen als** rekening houden met de instelling, aangezien gebruikers bepaalde gegevenstypen kunnen configureren. U kunt bijvoorbeeld een tekstveld bestaande uit een enkele regel zo configureren dat het meerdere tekstregels bevat door `multifield` in de vervolgkeuzelijst.

* GraphQL for AEM genereert ook een aantal [helpervelden](#helper-fields).

### Gegevenstypen {#data-types}

GraphQL for AEM ondersteunt een lijst met typen. Alle ondersteunde gegevenstypen van het inhoudsfragmentmodel en de bijbehorende GraphQL-typen worden weergegeven:

| Inhoudsfragmentmodel - Gegevenstype | GraphQL-type | Beschrijving |
|--- |--- |--- |
| Tekst met één regel | `String`, `[String]` | Wordt gebruikt voor eenvoudige tekenreeksen, zoals namen van auteurs, namen van locaties, enzovoort. |
| Tekst met meerdere regels | `String`, `[String]` | Wordt gebruikt voor het uitvoeren van tekst, zoals de hoofdtekst van een artikel |
| Getal | `Float`, `[Float]` | Wordt gebruikt om het zwevende-kommanummer en de reguliere getallen weer te geven |
| Boolean | `Boolean` | Gebruikt om selectievakjes weer te geven → eenvoudige true/false-instructies |
| Datum en tijd | `Calendar` | Wordt gebruikt om datum en tijd weer te geven in de indeling ISO 8601. Afhankelijk van het geselecteerde type zijn er drie kleuren beschikbaar voor gebruik in AEM GraphQL: `onlyDate`, `onlyTime`, `dateTime` |
| Opsomming | `String` | Wordt gebruikt om een optie weer te geven uit een lijst met opties die bij het maken van het model zijn gedefinieerd |
| Tags | `[String]` | Wordt gebruikt om een lijst weer te geven met tekenreeksen die tags vertegenwoordigen die in AEM worden gebruikt |
| Content Reference | `String`, `[String]` | Wordt gebruikt om het pad naar een ander element in AEM weer te geven |
| Fragmentverwijzing |  *Een modeltype* <br><br>Enkel veld: `Model` - Modeltype, rechtstreeks verwezen <br><br>Meerdere velden, met één type waarnaar wordt verwezen: `[Model]` - Array van type `Model`, rechtstreeks vanaf een array <br><br>Meerdere velden, met meerdere typen waarnaar wordt verwezen: `[AllFragmentModels]` - Array van alle modeltypen, met verwijzing van array met type union |  Gebruikt om één, of meer, de Fragmenten van de Inhoud van bepaalde ModelTypes van Verwijzing te voorzien, die toen het model werd gecreeerd |

{style="table-layout:auto"}

### Helpervelden {#helper-fields}

Naast de gegevenstypen voor door de gebruiker gegenereerde velden, genereert GraphQL for AEM ook verschillende *helper* velden voor het herkennen van een inhoudsfragment of voor aanvullende informatie over een inhoudsfragment.

Deze [helpervelden](#helper-fields) zijn gemarkeerd met een voorgaande `_` om onderscheid te maken tussen wat door de gebruiker is gedefinieerd en wat automatisch is gegenereerd.

#### Pad {#path}

Het padveld wordt gebruikt als een identifier in AEM GraphQL. Het vertegenwoordigt het pad van het Content Fragment-element in de AEM opslagplaats. Dit is de id van een inhoudsfragment, omdat dit:

* uniek is binnen AEM,
* kan gemakkelijk worden opgehaald.

De volgende code geeft de paden weer van alle inhoudsfragmenten die zijn gemaakt op basis van het model van het inhoudsfragment `Author`, zoals verstrekt door de WKND zelfstudie.

```graphql
{
  authorList {
    items {
      _path
    }
  }
}
```

Als u één inhoudsfragment van een bepaald type wilt ophalen, moet u ook eerst het pad bepalen. Bijvoorbeeld:

```graphql
{
  authorByPath(_path: "/content/dam/wknd-shared/en/contributors/sofia-sj-berg") {
    item {
      _path
      firstName
      lastName
    }
  }
}
```

Zie [Voorbeeldquery - één specifiek stedenfragment](/help/headless/graphql-api/sample-queries.md#sample-single-specific-city-fragment).

#### Metagegevens {#metadata}

Via GraphQL worden AEM ook de metagegevens van een inhoudsfragment beschikbaar gemaakt. Metagegevens zijn de informatie die een inhoudsfragment beschrijft, zoals de titel van een inhoudsfragment, het miniatuurpad, de beschrijving van een inhoudsfragment en de datum waarop het is gemaakt.

Omdat metagegevens worden gegenereerd via de Schema-editor en als zodanig geen specifieke structuur hebben, `TypedMetaData` Het GraphQL-type is geïmplementeerd om de metagegevens van een inhoudsfragment beschikbaar te maken. `TypedMetaData` stelt de informatie bloot die door de volgende scalaire types wordt gegroepeerd:

| Veld |
|--- |
| `stringMetadata:[StringMetadata]!` |
| `stringArrayMetadata:[StringArrayMetadata]!` |
| `intMetadata:[IntMetadata]!` |
| `intArrayMetadata:[IntArrayMetadata]!` |
| `floatMetadata:[FloatMetadata]!` |
| `floatArrayMetadata:[FloatArrayMetadata]!` |
| `booleanMetadata:[BooleanMetadata]!` |
| `booleanArrayMetadata:[booleanArrayMetadata]!` |
| `calendarMetadata:[CalendarMetadata]!` |
| `calendarArrayMetadata:[CalendarArrayMetadata]!` |

Elk scalair type vertegenwoordigt of één enkel naam-waarde paar of een serie van naam-waarde paren, waar de waarde van dat paar van het type is het werd gegroepeerd.

Als u bijvoorbeeld de titel van een inhoudsfragment wilt ophalen, weten we dat deze eigenschap een String-eigenschap is, zodat we een query voor alle String-metagegevens uitvoeren:

Ga als volgt te werk om te zoeken naar metagegevens:

```graphql
{
  authorByPath(_path: "/content/dam/wknd-shared/en/contributors/sofia-sj-berg") {
    item {
      _metadata {
        stringMetadata {
          name
          value
        }
      }
    }
  }
}
```

U kunt alle GraphQL-typen voor metagegevens weergeven als u het schema Gegenereerde GraphQL weergeeft. Alle modeltypen hebben dezelfde `TypedMetaData`.

>[!NOTE]
>
>**Verschil tussen normale en arraymetagegevens**
>Houd er rekening mee dat `StringMetadata` en `StringArrayMetadata` beide verwijzen naar wat in de bewaarplaats wordt opgeslagen, niet hoe u hen terugwint.
>
>Bijvoorbeeld door de `stringMetadata` veld, ontvangt u een array van alle metagegevens die in de repository zijn opgeslagen als een `String` en als u `stringArrayMetadata` u ontvangt dan een array met alle metagegevens die in de repository zijn opgeslagen als `String[]`.

Zie [Voorbeeldquery voor metagegevens - Lijst met metagegevens voor onderscheidingen: GB](/help/headless/graphql-api/sample-queries.md#sample-metadata-awards-gb).

#### Variaties {#variations}

De `_variations` is geïmplementeerd om het opvragen van variaties in een inhoudsfragment te vereenvoudigen. Bijvoorbeeld:

```graphql
{
  authorByPath(_path: "/content/dam/wknd-shared/en/contributors/ian-provo") {
    item {
      _variations
    }
  }
}
```

>[!NOTE]
>
>De `_variations` veld bevat geen `master` variatie, als technisch gezien de oorspronkelijke gegevens (als *Master* in de gebruikersinterface) wordt niet als een expliciete wijziging beschouwd.

Zie [Voorbeeldquery - Alle steden met een benoemde variatie](/help/headless/graphql-api/sample-queries.md#sample-cities-named-variation).

>[!NOTE]
>
>Als de opgegeven variatie niet bestaat voor een inhoudsfragment, worden de oorspronkelijke gegevens (ook wel de hoofdvariatie genoemd) geretourneerd als een standaardinstelling (fallback).

<!--
## Security Considerations {#security-considerations}
-->

## GraphQL-variabelen {#graphql-variables}

GraphQL staat toe dat variabelen in de query worden geplaatst. Zie voor meer informatie [GraphQL-documentatie voor variabelen](https://graphql.org/learn/queries/#variables).

Als u bijvoorbeeld alle inhoudsfragmenten van het type wilt ophalen `Author` in een specifieke variatie (indien beschikbaar), kunt u het argument specificeren `variation` in GraphiQL.

![GraphQL-variabelen](assets/cfm-graphqlapi-03.png "GraphQL-variabelen")

**Query**:

```graphql
query($variation: String!) {
  authorList(variation: $variation) {
    items {
      _variation
      lastName
      firstName
    }
  }
}
```

**Query-variabelen**:

```json
{
  "variation": "another"
}
```

Deze query retourneert de volledige lijst met auteurs. Auteurs zonder de `another` de wijziging wordt teruggebracht naar de oorspronkelijke gegevens (`_variation` rapporteren `master` in dit geval).

Een [filter](#filtering), als u de lijst wilt beperken tot auteurs die de opgegeven variatie leveren (en auteurs overslaan die terugvallen naar de oorspronkelijke gegevens):

```graphql
query($variation: String!) {
  authorList(variation: $variation, filter: {
    _variation: {
      _expressions: {
        value: $variation
      }
    }
  }) {
    items {
      _variation
      lastName
      firstName
    }
  }
}
```

## GraphQL-richtlijnen {#graphql-directives}

In GraphQL bestaat de mogelijkheid om de query te wijzigen op basis van variabelen, de zogenaamde GraphQL-richtlijnen.

Hier kunt u bijvoorbeeld de opdracht `adventurePrice` veld in een query voor alle `AdventureModels`, gebaseerd op een variabele `includePrice`.

![GraphQL-richtlijnen](assets/cfm-graphqlapi-04.png "GraphQL-richtlijnen")

**Query**:

```graphql
query GetAdventureByType($includePrice: Boolean!) {
  adventureList {
    items {
      title
      price @include(if: $includePrice)
    }
  }
}
```

**Query-variabelen**:

```json
{
    "includePrice": true
}
```

## Filteren {#filtering}

U kunt filteren ook gebruiken in uw GraphQL-query&#39;s om specifieke gegevens te retourneren.

Bij het filteren wordt een syntaxis gebruikt die is gebaseerd op logische operatoren en expressies.

Het meest atomische deel bestaat uit één expressie die kan worden toegepast op de inhoud van een bepaald veld. De inhoud van het veld wordt vergeleken met een bepaalde constante waarde.

De expressie

```graphql
{
  value: "some text"
  _op: EQUALS
}
```

zou de inhoud van het veld vergelijken met de waarde `some text` en slaagt als de inhoud de waarde evenaart. Anders zal de expressie mislukken.

De volgende operatoren kunnen worden gebruikt om velden met een bepaalde waarde te vergelijken:

| Operator | Type(n) | De expressie slaagt als ... |
|--- |--- |--- |
| `EQUALS` | `String`, `ID`, `Boolean` | ... de waarde is exact dezelfde als de inhoud van het veld |
| `EQUALS_NOT` | `String`, `ID` | ... de waarde is *niet* gelijk aan de inhoud van het veld |
| `CONTAINS` | `String` | ... de inhoud van het veld bevat de waarde (`{ value: "mas", _op: CONTAINS }` komt overeen `Christmas`, `Xmas`, `master`, ...) |
| `CONTAINS_NOT` | `String` | ... de inhoud van het veld *niet* bevatten de waarde |
| `STARTS_WITH` | `ID` | ... de id begint met een bepaalde waarde (`{ value: "/content/dam/", _op: STARTS_WITH` komt overeen `/content/dam/path/to/fragment`, maar niet `/namespace/content/dam/something` |
| `EQUAL` | `Int`, `Float` | ... de waarde is exact dezelfde als de inhoud van het veld |
| `UNEQUAL` | `Int`, `Float` | ... de waarde is *niet* gelijk aan de inhoud van het veld |
| `GREATER` | `Int`, `Float` | ... de inhoud van het veld is groter dan de waarde |
| `GREATER_EQUAL` | `Int`, `Float` | ... de inhoud van het veld is groter dan of gelijk aan de waarde |
| `LOWER` | `Int`, `Float` | ... de inhoud van het veld is lager dan de waarde |
| `LOWER_EQUAL` | `Int`, `Float` | ... de inhoud van het veld is lager dan of gelijk aan de waarde |
| `AT` | `Calendar`, `Date`, `Time` | ... de inhoud van het veld is exact dezelfde als de waarde (inclusief tijdzone-instelling) |
| `NOT_AT` | `Calendar`, `Date`, `Time` | ... de inhoud van het veld is *niet* gelijk aan de waarde |
| `BEFORE` | `Calendar`, `Date`, `Time` | ... het tijdpunt dat door de waarde wordt aangegeven, ligt vóór het tijdpunt dat door de inhoud van het veld wordt aangegeven |
| `AT_OR_BEFORE` | `Calendar`, `Date`, `Time` | ... het tijdpunt dat door de waarde wordt aangegeven, zich vóór of op hetzelfde tijdpunt bevindt dat door de inhoud van het veld wordt aangegeven |
| `AFTER` | `Calendar`, `Date`, `Time` | ... het punt in de tijd dat door de waarde wordt aangegeven, is na het punt in de tijd dat door de inhoud van het veld wordt aangegeven |
| `AT_OR_AFTER` | `Calendar`, `Date`, `Time` | ... het tijdpunt dat door de waarde wordt aangegeven, is na of op hetzelfde tijdpunt dat door de inhoud van het veld wordt aangegeven |

Bij sommige typen kunt u ook aanvullende opties opgeven die wijzigen hoe een expressie wordt geëvalueerd:

| Optie | Type(n) | Beschrijving |
|--- |--- |--- |
| `_ignoreCase` | `String` | Negeert het geval van een tekenreeks, bijvoorbeeld een waarde van `time` overeenkomsten `TIME`, `time`, `tImE`, ... |
| `_sensitiveness` | `Float` | Hiermee wordt een bepaalde marge toegestaan voor `float` als hetzelfde te beschouwen waarden (om technische beperkingen te omzeilen als gevolg van de interne representatie van `float` waarden; moet worden vermeden, aangezien deze optie een negatief effect kan hebben op de prestaties |

Expressies kunnen met behulp van een logische operator worden gecombineerd tot een set (`_logOp`):

* `OR` - de reeks expressies zal slagen als ten minste één expressie slaagt
* `AND` - de reeks expressies zal slagen als alle expressies slagen (standaardwaarde)

Elk veld kan met een eigen set expressies worden gefilterd. De expressiesets van alle velden die in het filterargument worden vermeld, worden uiteindelijk gecombineerd door de eigen logische operator.

Een filterdefinitie (doorgegeven als de `filter` argument voor een query) bevat:

* Een subdefinitie voor elk gebied (het gebied kan door zijn naam worden betreden, bijvoorbeeld, is er een `lastName` veld in het filter voor de `lastName` veld in het gegevenstype (veld)
* Elke subdefinitie bevat de `_expressions` array, die de expressieset en de `_logOp` veld waarin de logische operator wordt gedefinieerd, moeten de expressies worden gecombineerd met
* Elke expressie wordt gedefinieerd door de waarde (`value` veld) en de operator (`_operator` veld) de inhoud van een veld moet worden vergeleken met

U kunt weglaten `_logOp` als je objecten wilt combineren met `AND` en `_operator` als u op gelijkheid wilt controleren, aangezien dit de standaardwaarden zijn.

Het volgende voorbeeld toont een volledige vraag aan die alle personen filtert die een `lastName` van `Provo` of die `sjö`onafhankelijk van de zaak:

```graphql
{
  authorList(filter: {
    lastname: {
      _logOp: OR
      _expressions: [
        {
          value: "sjö",
          _operator: CONTAINS,
          _ignoreCase: true
        },
        {
          value: "Provo"
        }
      ]
    }
  }) {
    items {
      lastName
      firstName
    }
  }
}
```

U kunt ook filteren op geneste velden, maar dit wordt afgeraden omdat dit tot prestatieproblemen kan leiden.

Zie voor meer voorbeelden:

* nadere gegevens over de [GraphQL for AEM extensions](#graphql-extensions)

* [Voorbeeldquery&#39;s met deze voorbeeldinhoud en -structuur](/help/headless/graphql-api/sample-queries.md#graphql-sample-queries-sample-content-fragment-structure)

   * En de [Voorbeeldinhoud en -structuur](/help/headless/graphql-api/sample-queries.md#content-fragment-structure-graphql) voorbereid voor gebruik in voorbeeldquery&#39;s

* [Voorbeeldquery&#39;s op basis van het WKND-project](/help/headless/graphql-api/sample-queries.md#sample-queries-using-wknd-project)

## Sorteren {#sorting}

>[!NOTE]
>
>Voor de beste prestaties moet u [Inhoudsfragmenten bijwerken voor pagineren en sorteren in GraphQL-filters](/help/headless/graphql-api/graphql-optimized-filtering-content-update.md).

Met deze functie kunt u de zoekresultaten sorteren op basis van een opgegeven veld.

De sorteercriteria:

* is een door komma&#39;s gescheiden lijst met waarden die het veldpad aangeven
   * het eerste veld in de lijst definieert de primaire sorteervolgorde, het tweede veld wordt gebruikt als twee waarden van het primaire sorteercriterium gelijk zijn, het derde als de eerste twee criteria gelijk zijn, enzovoort.
   * puntnotatie, dat wil zeggen veld1.subfield.subfield enzovoort..
* met een optionele bestelrichting
   * ASC (oplopend) of DESC (aflopend); als standaard ASC wordt toegepast
   * De richting kan per veld worden opgegeven. Dit betekent dat u één veld in oplopende volgorde kunt sorteren, een ander veld in aflopende volgorde (naam, voornaam DESC)

Bijvoorbeeld:

```graphql
query {
  authorList(sort: "lastName, firstName") {
    items {
      firstName
      lastName
    }
  }
}
```

En ook:

```graphql
{
  authorList(sort: "lastName DESC, firstName DESC") {
    items {
        lastName
        firstName
    }
  }
}
```

U kunt ook sorteren op een veld in een genest fragment in de notatie `nestedFragmentname.fieldname`.

>[!NOTE]
>
>Dit kan negatieve gevolgen hebben voor de prestaties.

Bijvoorbeeld:

```graphql
query {
  articleList(sort: "authorFragment.lastName")  {
    items {
      title
      authorFragment {
        firstName
        lastName
        birthDay
      }
      slug
    }
  }
}
```

## Paginering {#paging}

>[!NOTE]
>
>Voor de beste prestaties moet u [Inhoudsfragmenten bijwerken voor pagineren en sorteren in GraphQL-filters](/help/headless/graphql-api/graphql-optimized-filtering-content-update.md).

Met deze functie kunt u pagineren uitvoeren op querytypen die een lijst retourneren. Er zijn twee methoden:

* `offset` en `limit` in een `List` query
* `first` en `after` in een `Paginated` query

### Lijstquery - Verschuiven en beperken {#list-offset-limit}

In een `...List`query die u kunt gebruiken `offset` en `limit` om een specifieke subset van resultaten te retourneren:

* `offset`: Geeft de eerste gegevensset aan die moet worden geretourneerd
* `limit`: Geeft het maximale aantal gegevenssets op dat moet worden geretourneerd

Als u bijvoorbeeld de resultatenpagina wilt weergeven met maximaal vijf artikelen, te beginnen bij het vijfde artikel van het dialoogvenster *complete* resultatenlijst:

```graphql
query {
   articleList(offset: 5, limit: 5) {
    items {
      authorFragment {
        lastName
        firstName
      }
    }
  }
}
```

<!-- When available link to BP and replace "JCR query level" with a more neutral term. -->

<!-- When available link to BP and replace "JCR query result set" with a more neutral term. -->

>[!NOTE]
>
>* De paginering vereist een stabiele soortorde om correct over veelvoudige vragen te werken die verschillende pagina&#39;s van de zelfde resultaatreeks vragen. Standaard wordt het pad naar de opslagplaats van elk item van de resultaatset gebruikt om ervoor te zorgen dat de volgorde altijd gelijk is. Als een verschillende sorteervolgorde wordt gebruikt en als die sortering niet kan worden uitgevoerd op JCR-queryniveau, heeft dit een negatief effect op de prestaties omdat de volledige resultaatset in het geheugen moet worden geladen voordat de pagina&#39;s kunnen worden bepaald.
>
>* Hoe hoger de verschuiving, des te meer tijd neemt het om de items van de volledige set JCR-queryresultaten over te slaan. Een alternatieve oplossing voor grote resultaatreeksen is de gepagineerde vraag met te gebruiken `first` en `after` methode.

### Gepagineerde query - eerste en volgende {#paginated-first-after}

De `...Paginated` het vraagtype gebruikt het grootste deel van `...List` functies voor querytypen (filteren, sorteren), maar in plaats van `offset`/`limit` argumenten, gebruikt het de `first`/`after` argumenten zoals gedefinieerd door [de GraphQL Cursor Connections Specification](https://relay.dev/graphql/connections.htm). U vindt een minder formele introductie in het dialoogvenster [Inleiding GraphQL](https://graphql.org/learn/pagination/#pagination-and-edges).

* `first`: De `n` eerste objecten die moeten worden geretourneerd.
De standaardwaarde is `50`.
Het maximum is `100`.
* `after`: De cursor die het begin van de opgevraagde pagina bepaalt; het item dat door de cursor wordt vertegenwoordigd, wordt niet opgenomen in de resultatenset; de cursor van een item wordt bepaald door de `cursor` van het `edges` structuur.

Voer bijvoorbeeld de resultatenpagina uit met maximaal vijf avonturen, te beginnen bij het opgegeven cursoritem in het dialoogvenster *complete* resultatenlijst:

```graphql
query {
    adventurePaginated(first: 5, after: "ODg1MmMyMmEtZTAzMy00MTNjLThiMzMtZGQyMzY5ZTNjN2M1") {
        edges {
          cursor
          node {
            title
          }
        }
        pageInfo {
          endCursor
          hasNextPage
        }
    }
}
```

<!-- When available link to BP -->
<!-- Due to internal technical constraints, performance will degrade if sorting and filtering is applied on nested fields. Therefore it is recommended to use filter/sort fields stored at root level. For more information, see the [Best Practices document](link). -->

>[!NOTE]
>
>* Standaard wordt bij paginering de UUID gebruikt van het opslagplaats-knooppunt dat het fragment vertegenwoordigt voor de volgorde van de resultaten, zodat altijd dezelfde volgorde wordt gebruikt. Wanneer `sort` wordt gebruikt, wordt UUID impliciet gebruikt om een unieke soort te verzekeren; zelfs voor twee punten met identieke soortsleutels.
>
>* Vanwege interne technische beperkingen zullen de prestaties afnemen als sorteren en filteren wordt toegepast op geneste velden. Daarom wordt aangeraden filter-/sorteervelden te gebruiken die op hoofdniveau zijn opgeslagen. Dit is ook de geadviseerde manier als u grote gepagineerde resultaatreeksen wilt vragen.

## Webgeoptimaliseerde afbeeldingslevering in GraphQL-query&#39;s {#web-optimized-image-delivery-in-graphql-queries}

Met webgeoptimaliseerde afbeeldingslevering kunt u een grafische query gebruiken:

* Een URL aanvragen naar een DAM-elementafbeelding (waarnaar wordt verwezen door een **Content Reference**)

* Geef parameters door met de query, zodat er automatisch een specifieke uitvoering van de afbeelding wordt gegenereerd en geretourneerd

  >[!NOTE]
  >
  >De opgegeven vertoning wordt niet opgeslagen in AEM Assets. De vertoning wordt geproduceerd en in geheim voorgeheugen voor een korte periode gehouden.

* De URL retourneren als onderdeel van de JSON-levering

U kunt AEM gebruiken om:

* Voldoende [Webgeoptimaliseerde afbeeldingslevering](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html) in GraphQL-query&#39;s.

Dit betekent dat de opdrachten worden toegepast tijdens de uitvoering van de query, op dezelfde manier als URL-parameters bij GET-aanvragen voor die afbeeldingen.

Hierdoor kunt u dynamisch afbeeldingsuitvoeringen maken voor JSON-levering, zodat u deze uitvoeringen niet handmatig hoeft te maken en op te slaan in de opslagplaats.

Met de oplossing in GraphQL kunt u:

* Een URL aanvragen: gebruik `_dynamicUrl` op de `ImageRef` referentie

* Parameters doorgeven: toevoegen `_assetTransform` aan de lijstkopbal waar uw filters worden bepaald

>[!NOTE]
>
>A **Content Reference** kan zowel voor DAM-middelen als voor Dynamic Media-middelen worden gebruikt. Voor het ophalen van de juiste URL worden verschillende parameters gebruikt:
>* `_dynamicUrl` : een DAM-middel
>* `_dmS7Url` : een Dynamic Media-element
> 
>Als het element waarnaar wordt verwezen een DAM-element is, is de waarde voor `_dmS7Url` wordt `null`. Zie [Dynamic Media-levering van middelen via URL in GraphQL-query&#39;s](#dynamic-media-asset-delivery-by-url).

### Structuur van het transformatieverzoek {#structure-transformation-request}

`AssetTransform` (`_assetTransform`) wordt gebruikt om de URL-transformatieaanvragen in te dienen.

De structuur en syntaxis zijn:

* `format`: een opsomming met alle ondersteunde indelingen, zoals GIF, PNG, PNG8, JPG, PJPG, BJPG, WEBP, WEBPLL of WEBPLY
* `seoName`: een tekenreeks die wordt gebruikt als bestandsnaam in plaats van de knooppuntnaam
* `crop`: een substructuur van het frame, als breedte of hoogte wordt weggelaten, wordt de hoogte of breedte gebruikt als dezelfde waarde
   * `xOrigin`: de x-oorsprong van het frame en is verplicht
   * `yOrigin`: de y-oorsprong van het frame en is verplicht
   * `width`: de breedte van het kader
   * `height`: de hoogte van het frame
* `size`: een dimensiesubstructuur, als breedte of hoogte wordt weggelaten, wordt de hoogte of breedte gebruikt als dezelfde waarde
   * `width`: de breedte van de dimensie
   * `height`: de hoogte van de dimensie
* `rotation`: een opsomming van alle ondersteunde rotaties: R90, R180, R270
* `flip`: een opsomming van HORIZONTAL, VERTICAL, HORIZONTAL_AND_VERTICAL
* `quality`: een geheel getal van 1-100 dat het percentage van de afbeeldingskwaliteit aangeeft
* `width`: een geheel getal dat de breedte van de uitvoerafbeelding definieert, maar door de afbeeldingsgenerator wordt genegeerd
* `preferWebp`: een Booleaanse waarde die aangeeft of de voorkeur wordt gegeven aan een webpagina (de standaardwaarde is false)

De transformatie URL is beschikbaar voor alle vraagtypes: door weg, lijst of gepagineerd.

### Voor het web geoptimaliseerde afbeeldingslevering met volledige parameters {#web-optimized-image-delivery-full-parameters}

Hier volgt een voorbeeldquery met een volledige set parameters:

```graphql
{
  articleList(
    _assetTransform: {
      format:GIF
      seoName:"test"
      crop:{
        xOrigin:10
        yOrigin:20
        width:50
        height:45
      }
      size:{
        height:100
        width:200
      }
      rotation:R90
      flip:HORIZONTAL_AND_VERTICAL
      quality:55
      width:123
      preferWebp:true
    }
  ) {
    items {
      _path
      featuredImage {
        ... on ImageRef {
          _dynamicUrl
        }
      }
    }
  }
}
```

### Web-geoptimaliseerde beeldlevering met één enkele vraagvariabele {#web-optimized-image-delivery-single-query-variable}

In het volgende voorbeeld wordt het gebruik van één queryvariabele getoond:

```graphql
query ($seoName: String!) {
  articleList(
    _assetTransform: {
      format:GIF
      seoName:$seoName
      crop:{
        xOrigin:10
        yOrigin:20
        width:50
        height:45
      }
      size:{
        height:100
        width:200
      }
      rotation:R90
      flip:HORIZONTAL_AND_VERTICAL
      quality:55
      width:123
      preferWebp:true
    }
  ) {
    items {
      _path
      featuredImage {
        ... on ImageRef {
          _dynamicUrl
        }
      }
    }
  }
}
```

### Webgeoptimaliseerde afbeeldingslevering met meerdere queryvariabelen {#web-optimized-image-delivery-multiple-query-variables}

In het volgende voorbeeld wordt het gebruik van meerdere queryvariabelen getoond:

```graphql
query ($seoName: String!, $format: AssetTransformFormat!) {
  articleList(
    _assetTransform: {
      format:$format
      seoName:$seoName
      crop:{
        xOrigin:10
        yOrigin:20
        width:50
        height:45
      }
      size:{
        height:100
        width:200
      }
      rotation:R90
      flip:HORIZONTAL_AND_VERTICAL
      quality:55
      width:123
      preferWebp:true
    }
  ) {
    items {
      _path
      featuredImage {
        ... on ImageRef {
          _dynamicUrl
        }
      }
    }
  }
}
```

### Voor het web geoptimaliseerde aanvraag voor het leveren van afbeeldingen via URL {#web-optimized-image-delivery-request-url}

Als u de query opslaat als een doorlopende query (bijvoorbeeld met de naam `dynamic-url-x`) kunt u vervolgens [De voortgezette query rechtstreeks uitvoeren](/help/headless/graphql-api/persisted-queries.md#execute-persisted-query).

Gebruik bijvoorbeeld de volgende URL&#39;s om de vorige voorbeelden (opgeslagen als voortgeduurde query&#39;s) rechtstreeks uit te voeren:

* [Enkele parameter](#dynamic-image-delivery-single-specified-parameter); Blijvende query genaamd `dynamic-url-x`

   * `http://localhost:4502/graphql/execute.json/wknd-shared/dynamic-url-x;seoName=xxx`

     Het antwoord ziet er als volgt uit:

     ![Afbeeldingen leveren met behulp van parameters](assets/cfm-graphiql-sample-image-delivery.png "Afbeeldingen leveren met behulp van parameters")

* [Meerdere parameters](#dynamic-image-delivery-multiple-specified-parameters); Blijvende query genaamd `dynamic`

   * `http://localhost:4502/graphql/execute.json/wknd-shared/dynamic;seoName=billiboy;format=GIF;`

     >[!CAUTION]
     >
     >De navolgende `;`is verplicht de lijst met parameters zorgvuldig te beëindigen.

### Beperkingen voor de levering van webgeoptimaliseerde afbeeldingen {#web-optimized-image-delivery-limitations}

De volgende beperkingen bestaan:

* Modifiers die worden toegepast op alle afbeeldingen die deel uitmaken van de query (globale parameters)

* Koppen in cache plaatsen

   * Geen caching op auteur
   * Caching bij publicatie - maximale leeftijd van 10 minuten (kan niet worden gewijzigd door client)

## Dynamic Media-levering van middelen via URL in GraphQL-query&#39;s{#dynamic-media-asset-delivery-by-url}

Met GraphQL for AEM Content Fragments kunt u een URL aanvragen naar een AEM Dynamic Media-element (Scene7) (waarnaar wordt verwezen door een **Content Reference**).

Met de oplossing in GraphQL kunt u:

* gebruiken `_dmS7Url` op de `ImageRef` referentie

>[!NOTE]
>
>Hiervoor hebt u een [Dynamic Media Cloud Configuration](/help/assets/dynamic-media/config-dm.md).
>
>Dit voegt de `dam:scene7File` en `dam:scene7Domain` kenmerken op de metagegevens van het element wanneer het wordt gemaakt.

>[!NOTE]
>
>A **Content Reference** kan zowel voor DAM-middelen als voor Dynamic Media-middelen worden gebruikt. Voor het ophalen van de juiste URL worden verschillende parameters gebruikt:
>
>* `_dmS7Url` : een Dynamic Media-element
>* `_dynamicUrl` : een DAM-middel
> 
>Als het element waarnaar wordt verwezen een Dynamic Media-element is, is de waarde voor `_dynamicURL` wordt `null`. Zie [voor het web geoptimaliseerde afbeeldingslevering in GraphQL-query&#39;s](#web-optimized-image-delivery-in-graphql-queries).

### Voorbeeldquery voor levering van Dynamic Media-elementen via URL - Afbeeldingsverwijzing{#sample-query-dynamic-media-asset-delivery-by-url-imageref}

Hier volgt een voorbeeldquery:
* voor meerdere inhoudsfragmenten van het type `team` en `person`, een `ImageRef`

```graphql
query allTeams {
  teamList {
    items {
      _path
      title
      teamMembers {
        fullName
        profilePicture {
          __typename
          ... on ImageRef{
            _dmS7Url
            height
            width
          }
        }
      }
    }
  }
} 
```

### Voorbeeldquery voor levering van Dynamic Media-elementen via URL - Meerdere verwijzingen{#sample-query-dynamic-media-asset-delivery-by-url-multiple-refs}

Hier volgt een voorbeeldquery:
* voor meerdere inhoudsfragmenten van het type `team` en `person`, een `ImageRef`, `MultimediaRef` en `DocumentRef`:

```graphql
query allTeams {
  teamList {
    items {
      _path
      title
      teamMembers {
        fullName
        profilePicture {
          __typename
          ... on ImageRef{
            _dmS7Url
            height
            width
          }
        }
       featureVideo {
          __typename
          ... on MultimediaRef{
            _dmS7Url
            size
          }
        }
      about-me {
          __typename
          ... on DocumentRef{
            _dmS7Url
            _path
          }
        }
      }
    }
  }
}
```

## GraphQL for AEM - Overzicht van extensies {#graphql-extensions}

De basisverrichting van vragen met GraphQL voor AEM voldoet aan de standaardspecificatie van GraphQL. Voor GraphQL-query&#39;s met AEM zijn er een paar extensies:

* Als u één resultaat nodig hebt:
   * gebruik de modelnaam; bijvoorbeeld stad

* Als u een lijst met resultaten verwacht:
   * toevoegen `List` op de modelnaam, bijvoorbeeld  `cityList`
   * Zie [Voorbeeldquery - Alle informatie over alle steden](/help/headless/graphql-api/sample-queries.md#sample-all-information-all-cities)

  U kunt dan:

   * [De resultaten sorteren](#sorting)

      * `ASC` : oplopend
      * `DESC` : aflopend

   * Retourneer een pagina met resultaten met:

      * [Een lijstvraag met compensatie en grens](#list-offset-limit)
      * [Een gepagineerde query met eerste en volgende](#paginated-first-after)

   * Zie [Voorbeeldquery - Alle informatie over alle steden](/help/headless/graphql-api/sample-queries.md#sample-all-information-all-cities)

* Het filter `includeVariations` is opgenomen in de `List` en `Paginated` querytypen.  Als u Variaties in inhoudsfragmenten wilt ophalen in de queryresultaten, voert u de opdracht `includeVariations` filter moet worden ingesteld op `true`.

   * Zie [Voorbeeldquery voor meerdere inhoudsfragmenten en de bijbehorende variaties van een bepaald model](/help/headless/graphql-api/sample-queries.md#sample-wknd-multiple-fragment-variations-given-model)

  >[!CAUTION]
  >Het filter `includeVariations` en het door het systeem gegenereerde veld `_variation` kan niet samen in de zelfde vraagdefinitie worden gebruikt.

* Als u logische OR wilt gebruiken:
   * gebruiken ` _logOp: OR`
   * Zie [Voorbeeldquery - Alle personen met de naam &quot;Jobs&quot; of &quot;Smith&quot;](/help/headless/graphql-api/sample-queries.md#sample-all-persons-jobs-smith)

* Logische AND bestaat ook, maar is (vaak) impliciet

* U kunt zoeken naar veldnamen die overeenkomen met de velden in het model van het inhoudsfragment
   * Zie [Voorbeeldquery - Volledige details van de CEO en medewerkers van een bedrijf](/help/headless/graphql-api/sample-queries.md#sample-full-details-company-ceos-employees)

* Naast de velden van uw model zijn er velden die door het systeem worden gegenereerd (voorafgegaan door een onderstrepingsteken):

   * Voor inhoud:

      * `_locale` : om de taal te onthullen; gebaseerd op Taalbeheer
         * Zie [Voorbeeldquery voor meerdere inhoudsfragmenten van een bepaalde landinstelling](/help/headless/graphql-api/sample-queries.md#sample-wknd-multiple-fragments-given-locale)

      * `_metadata` : om metagegevens voor het fragment weer te geven
         * Zie [Voorbeeldquery voor metagegevens - Lijst met metagegevens voor onderscheidingen: GB](/help/headless/graphql-api/sample-queries.md#sample-metadata-awards-gb)

      * `_model` : Vragen naar een inhoudsfragmentmodel toestaan (pad en titel)
         * Zie [Voorbeeldquery voor een inhoudsfragmentmodel op basis van een model](/help/headless/graphql-api/sample-queries.md#sample-wknd-content-fragment-model-from-model)

      * `_path` : het pad naar het inhoudsfragment in de opslagplaats
         * Zie [Voorbeeldquery - één specifiek stedenfragment](/help/headless/graphql-api/sample-queries.md#sample-single-specific-city-fragment)

      * `_reference` : om verwijzingen weer te geven; inline-verwijzingen opnemen in de Rich Text Editor
         * Zie [Voorbeeldquery voor meerdere inhoudfragmenten met vooraf ingestelde verwijzingen](/help/headless/graphql-api/sample-queries.md#sample-wknd-multiple-fragments-prefetched-references)

      * `_variation` : om specifieke variaties in het inhoudsfragment weer te geven

        >[!NOTE]
        >
        >Als de opgegeven variatie niet bestaat voor een inhoudsfragment, wordt de hoofdvariatie geretourneerd als een standaardinstelling (fallback).

        >[!CAUTION]
        >
        >Het systeemgegenereerde veld `_variation` kan niet samen met het filter worden gebruikt `includeVariations`.

         * Zie [Voorbeeldquery - Alle steden met een benoemde variatie](/help/headless/graphql-api/sample-queries.md#sample-cities-named-variation)

   * Voor levering van de afbeelding:

      * `_authorURL`: de volledige URL naar het afbeeldingselement op AEM auteur
      * `_publishURL`: de volledige URL naar het afbeeldingselement bij AEM Publiceren

      * Voor [voor het web geoptimaliseerde afbeeldingslevering](#web-optimized-image-delivery-in-graphql-queries) (van DAM-activa):

         * `_dynamicUrl`: de volledige URL naar het voor het web geoptimaliseerde DAM-element op het tabblad `ImageRef` referentie

           >[!NOTE]
           >
           >`_dynamicUrl` is de voorkeurs-URL die u wilt gebruiken voor voor het web geoptimaliseerde DAM-middelen en moet het gebruik van `_path`, `_authorUrl`, en `_publishUrl` waar mogelijk.

         * `_assetTransform`: om parameters door te geven op de lijstkop waar de filters zijn gedefinieerd

         * Zie:

            * [Voorbeeldquery voor voor voor het web geoptimaliseerde levering van afbeeldingen met volledige parameters](#web-optimized-image-delivery-full-parameters)

            * [Voorbeeldquery voor voor voor het web geoptimaliseerde afbeeldingslevering met één opgegeven parameter](#web-optimized-image-delivery-single-query-variable)

      * `_dmS7Url`: over de `ImageRef` referentie voor de levering van de URL aan een [Dynamic Media-middelen](#dynamic-media-asset-delivery-by-url)

         * Zie [Voorbeeldquery voor levering van Dynamic Media-elementen via URL - ImageRef](#sample-query-dynamic-media-asset-delivery-by-url-imageref)

         * Zie [Voorbeeldquery voor levering van Dynamic Media-elementen via URL - Meerdere verwijzingen](#sample-query-dynamic-media-asset-delivery-by-url-multiple-refs)

   * `_tags`: om de id&#39;s weer te geven van inhoudsfragmenten of variaties die tags bevatten; dit is een array van `cq:tags` id&#39;s.

      * Zie [Voorbeeldquery - Namen van alle steden die zijn getagd als stadseinden](/help/headless/graphql-api/sample-queries.md#sample-names-all-cities-tagged-city-breaks)
      * Zie [Voorbeeldquery voor variaties van inhoudsfragmenten van een bepaald model waaraan een specifieke tag is gekoppeld](/help/headless/graphql-api/sample-queries.md#sample-wknd-fragment-variations-given-model-specific-tag)
      * Zie [Voorbeeldquery met filtering op _tags-id en exclusief variaties](/help/headless/graphql-api/sample-queries.md#sample-filtering-tag-not-variations)
      * Zie [Voorbeeldquery met filteren op _tags-id en inclusief variaties](/help/headless/graphql-api/sample-queries.md#sample-filtering-tag-with-variations)

     >[!NOTE]
     >
     >Tags kunnen ook worden opgevraagd door de metagegevens van een inhoudsfragment weer te geven.

   * En bewerkingen:

      * `_operator` : specifieke exploitanten toepassen; `EQUALS`, `EQUALS_NOT`, `GREATER_EQUAL`, `LOWER`, `CONTAINS`, `STARTS_WITH`
         * Zie [Voorbeeldquery - Alle personen die geen naam hebben van &quot;Taken&quot;](/help/headless/graphql-api/sample-queries.md#sample-all-persons-not-jobs)
         * Zie [Voorbeeldquery - Alle avonturen waar de `_path` begint met een bepaald voorvoegsel](/help/headless/graphql-api/sample-queries.md#sample-wknd-all-adventures-cycling-path-filter)

      * `_apply` : specifieke voorwaarden toepassen, bijvoorbeeld  `AT_LEAST_ONCE`
         * Zie [Voorbeeldquery - Filter op een array met een item dat minstens één keer moet voorkomen](/help/headless/graphql-api/sample-queries.md#sample-array-item-occur-at-least-once)

      * `_ignoreCase` : om de zaak te negeren bij het vragen
         * Zie [Voorbeeldquery - Alle steden met SAN in naam, ongeacht het geval](/help/headless/graphql-api/sample-queries.md#sample-all-cities-san-ignore-case)

* GraphQL-union-typen worden ondersteund:

   * gebruiken `... on`
      * Zie [Voorbeeldquery voor een inhoudsfragment van een specifiek model met een inhoudsverwijzing](/help/headless/graphql-api/sample-queries.md#sample-wknd-fragment-specific-model-content-reference)

* Extra fallback bij het opvragen van geneste fragmenten:

   * Als een bepaalde variatie niet bestaat in een genest fragment, wordt de **Master** variatie wordt geretourneerd.

## Het GraphQL-eindpunt van een externe website opvragen {#query-graphql-endpoint-from-external-website}

Om tot het eindpunt van GraphQL van een externe website toegang te hebben moet u vormen:

* [CORS-filter](/help/headless/deployment/cross-origin-resource-sharing.md)
* [Refererfilter](/help/headless/deployment/referrer-filter.md)

## Verificatie {#authentication}

Zie [Verificatie voor externe AEM GraphQL-query&#39;s op inhoudsfragmenten](/help/headless/security/authentication.md).

## Beperkingen {#limitations}

Om tegen potentiële problemen te beschermen worden er standaardbeperkingen opgelegd aan uw vragen:

* De query mag niet meer dan 1M (1024 * 1024) tekens bevatten
* De query mag niet meer dan 15000 tokens bevatten
* De query mag niet meer dan 200000 whitespace-tokens bevatten

U moet zich ook bewust zijn van:

* Er wordt een fout in een veldconflict geretourneerd wanneer uw GraphQL-query velden met dezelfde naam bevat in twee (of meer) modellen en aan de volgende voorwaarden wordt voldaan:

   * Dus waar:

      * Twee (of meer modellen) worden gebruikt als mogelijke verwijzingen; wanneer zij als toegestaan worden gedefinieerd **Modeltype** in de Content Fragment reference.

     en:

      * Deze twee modellen hebben gebieden met een gemeenschappelijke naam; dat betekent de zelfde naam voorkomt in beide modellen.

     en

      * Deze velden zijn van verschillende gegevenstypen.

   * Bijvoorbeeld:

      * Wanneer twee (of meer) fragmenten met verschillende modellen (bijvoorbeeld `M1`, `M2`) worden gebruikt als mogelijke verwijzingen (Content Reference of Fragment Reference) uit een ander fragment, bijvoorbeeld `Fragment1` `MultiField/List`
      * Deze twee fragmenten met verschillende modellen (`M1`, `M2`) hebben velden met dezelfde naam, maar verschillende typen.
Ter illustratie:
         * `M1.Title` als `Text`
         * `M2.Title` als `Text/MultiField`
      * Dan zal een fout van het gebiedsconflict voorkomen als de vraag van GraphQL bevat `Title` veld.

## Veelgestelde vragen {#faqs}

De gerezen vragen:

1. **Q**: &quot;*Hoe verschilt de GraphQL API voor AEM van de Query Builder-API?*&quot;

   * **A**: &quot;*De AEM GraphQL API biedt volledige controle op de JSON-uitvoer en is een industriestandaard voor het opvragen van inhoud.
AEM is van plan om in de AEM GraphQL API te investeren.*&quot;

## Zelfstudie - Aan de slag met AEM Headless en GraphQL {#tutorial}

Op zoek naar een praktische zelfstudie? Uitchecken [Aan de slag met AEM Headless en GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) end-to-end zelfstudie waarin wordt geïllustreerd hoe u in een CMS-scenario inhoud kunt ontwikkelen en beschikbaar maken met behulp van AEM GraphQL API&#39;s en die door een externe toepassing wordt verbruikt.
