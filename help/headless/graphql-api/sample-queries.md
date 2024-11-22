---
title: GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query's
description: Leer GraphQL met AEM te gebruiken, zodat u inhoud zonder problemen kunt bedienen door voorbeeldinhoud en query's te verkennen.
feature: Headless, Content Fragments,GraphQL API
exl-id: b60fcf97-4736-4606-8b41-4051b8b0c8a7
role: Admin, Developer
source-git-commit: 83bc4e09cc7b6c420eee64091fab773ee1dcbd85
workflow-type: tm+mt
source-wordcount: '1940'
ht-degree: 0%

---

# GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s {#learn-graphql-with-aem-sample-content-queries}

Leer GraphQL met AEM te gebruiken, zodat u inhoud zonder problemen kunt bedienen door voorbeeldinhoud en query&#39;s te verkennen.

>[!IMPORTANT]
>
>Verschillende functies van de GraphQL API voor gebruik met inhoudsfragmenten zijn beschikbaar via het programma Vroege adopter.
>
>Om de status te zien, en hoe te om toe te passen als u geinteresseerd bent, controleer de [ Nota&#39;s van de Versie ](/help/release-notes/release-notes-cloud/release-notes-current.md).

>[!NOTE]
>
>Lees deze pagina samen met het volgende:
>
>* [Contentfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)
>* [Modellen van contentfragmenten](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)
>* [ AEM GraphQL API voor gebruik met de Fragmenten van de Inhoud ](/help/headless/graphql-api/content-fragments.md)

Om aan de slag te gaan met GraphQL query&#39;s en hoe ze werken met AEM Content Fragments, is het nuttig om enkele praktische voorbeelden te zien.

Zie voor hulp bij dit:

* A [ structuur van het Fragment van de steekproefinhoud ](#content-fragment-structure-graphql)

* En sommige [ vragen van de steekproefGraphQL ](#graphql-sample-queries), die op de structuur van het Fragment van de steekproefinhoud (de Modellen van het Fragment van de Inhoud en verwante Fragments van de Inhoud) wordt gebaseerd.

>[!CONTEXTUALHELP]
>id="aemcloud_headless_graphql_sample"
>title="GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s"
>abstract="Leer GraphQL met AEM gebruiken om inhoud zonder problemen te bedienen door voorbeeldinhoud en query&#39;s te verkennen."

## GraphQL - Voorbeeldquery&#39;s met de structuur van het voorbeeldinhoudsfragment {#graphql-sample-queries-sample-content-fragment-structure}

Zie deze steekproefvragen voor illustraties van creeer vragen, samen met steekproefresultaten.

>[!NOTE]
>
>Afhankelijk van uw instantie, kunt u tot de [ interface toegang hebben GraphiQL inbegrepen met AEM GraphQL API ](/help/headless/graphql-api/graphiql-ide.md) voor het voorleggen en het testen van vragen.
>
>U kunt tot de vraagredacteur van één van beiden toegang hebben:
>
>* **Hulpmiddelen** > **Algemeen** > **de Redacteur van de Vraag van GraphQL**
>* direct; bijvoorbeeld `http://localhost:4502/aem/graphiql.html`

>[!NOTE]
>
>De steekproefvragen zijn gebaseerd op de [ Structuur van het Fragment van de Inhoud van de Steekproef voor gebruik met GraphQL ](#content-fragment-structure-graphql)

### Voorbeeldquery - Alle beschikbare schema&#39;s en datatypen {#sample-all-schemes-datatypes}

Retourneert alle `types` voor alle beschikbare schema&#39;s.

**de Vraag van de Steekproef**

```graphql
{
  __schema {
    types {
      name
      description
    }
  }
}
```

**Resultaat van de Steekproef**

```json
{
  "data": {
    "__schema": {
      "types": [
        {
          "name": "AdventureModel",
          "description": null
        },
        {
          "name": "AdventureModelArrayFilter",
          "description": null
        },
        {
          "name": "AdventureModelFilter",
          "description": null
        },
        {
          "name": "AdventureModelResult",
          "description": null
        },
        {
          "name": "AdventureModelResults",
          "description": null
        },
        {
          "name": "AllFragmentModels",
          "description": null
        },
        {
          "name": "ArchiveRef",
          "description": null
        },
        {
          "name": "ArrayMode",
          "description": null
        },
        {
          "name": "ArticleModel",
          "description": null
        },

...more results...

        {
          "name": "__EnumValue",
          "description": null
        },
        {
          "name": "__Field",
          "description": null
        },
        {
          "name": "__InputValue",
          "description": null
        },
        {
          "name": "__Schema",
          "description": "A GraphQL Introspection defines the capabilities of a GraphQL server. It exposes all available types and directives on the server, the entry points for query, mutation, and subscription operations."
        },
        {
          "name": "__Type",
          "description": null
        },
        {
          "name": "__TypeKind",
          "description": "An enum describing what kind of type a given __Type is"
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Alle informatie over alle steden {#sample-all-information-all-cities}

Om alle informatie over alle steden terug te winnen, kunt u de volgende basisvraag gebruiken:
**de Vraag van de Steekproef**

```graphql
{
  cityList {
    items
  }
}
```

Bij uitvoering wordt de query automatisch uitgebreid met alle velden:

```graphql
{
  cityList {
    items {
      _path
      name
      country
      population
    }
  }
}
```

**Resultaten van de Steekproef**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "_path": "/content/dam/sample-content-fragments/cities/basel",
          "name": "Basel",
          "country": "Switzerland",
          "population": 172258
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/berlin",
          "name": "Berlin",
          "country": "Germany",
          "population": 3669491
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/bucharest",
          "name": "Bucharest",
          "country": "Romania",
          "population": 1821000
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/san-francisco",
          "name": "San Francisco",
          "country": "USA",
          "population": 883306
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/san-jose",
          "name": "San Jose",
          "country": "USA",
          "population": 1026350
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/stuttgart",
          "name": "Stuttgart",
          "country": "Germany",
          "population": 634830
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/zurich",
          "name": "Zurich",
          "country": "Switzerland",
          "population": 415367
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Namen van alle steden {#sample-names-all-cities}

Een duidelijke vraag om `name` van alle ingangen in het `city` schema terug te keren.

**de Vraag van de Steekproef**

```graphql
query {
  cityList {
    items {
      name
    }
  }
}
```

**Resultaten van de Steekproef**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Basel"
        },
        {
          "name": "Berlin"
        },
        {
          "name": "Bucharest"
        },
        {
          "name": "San Francisco"
        },
        {
          "name": "San Jose"
        },
        {
          "name": "Stuttgart"
        },
        {
          "name": "Zurich"
        }
      ]
    }
  }
}
```

### Voorbeeldquery - één specifiek stedenfragment {#sample-single-specific-city-fragment}

Een query om de details van één fragmentitem te retourneren op een specifieke locatie in de opslagplaats.

**de Vraag van de Steekproef**

```graphql
{
  cityByPath (_path: "/content/dam/sample-content-fragments/cities/berlin") {
    item {
      _path
      name
      country
      population
     categories
    }
  }
}
```

**Resultaten van de Steekproef**

```json
{
  "data": {
    "cityByPath": {
      "item": {
        "_path": "/content/dam/sample-content-fragments/cities/berlin",
        "name": "Berlin",
        "country": "Germany",
        "population": 3669491,
        "categories": [
          "city:capital",
          "city:emea"
        ]
      }
    }
  }
}
```

### Voorbeeldquery - Alle steden met een benoemde variatie {#sample-cities-named-variation}

Als u een variatie, genoemd &quot;Centrum van Berlijn&quot;(`berlin_centre`), voor `city` Berlijn creeert, dan kunt u een vraag gebruiken om details van de variatie terug te keren.

**de Vraag van de Steekproef**

```graphql
{
  cityList (variation: "berlin_center") {
    items {
      _path
      name
      country
      population
      categories
    }
  }
}
```

**Resultaten van de Steekproef**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "_path": "/content/dam/sample-content-fragments/cities/berlin",
          "name": "Berlin",
          "country": "Germany",
          "population": 3669491,
          "categories": [
            "city:capital",
            "city:emea"
          ]
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Namen van alle steden die zijn getagd als stadseinden {#sample-names-all-cities-tagged-city-breaks}

Als u:

* verschillende tags maken met de naam `Tourism` : `Business` , `City Break` , `Holiday`
* en toewijzen aan de Master-variatie van verschillende `City` -varianten

Dan kunt u een vraag gebruiken om details van `name` en `tags` van alle ingangen terug te keren die als Onderbreking van de Stad in het `city` schema worden geëtiketteerd.

**de Vraag van de Steekproef**

```xml
query {
  cityList(
    includeVariations: true,
    filter: {_tags: {_expressions: [{value: "tourism:city-break", _operator: CONTAINS}]}}
  ){
    items {
      name,
      _tags
    }
  }
}
```

**Resultaten van de Steekproef**

```xml
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Berlin",
          "_tags": [
            "tourism:city-break",
            "tourism:business"
          ]
        },
        {
          "name": "Zurich",
          "_tags": [
            "tourism:city-break",
            "tourism:business"
          ]
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Volledige details van de CEO en medewerkers van een bedrijf {#sample-full-details-company-ceos-employees}

Gebruikend de structuur van de genestelde fragmenten, keert deze vraag de volledige details van CEO van een bedrijf en al zijn werknemers terug.

**de Vraag van de Steekproef**

```graphql
query {
  companyList {
    items {
      name
      ceo {
        _path
        name
        firstName
        awards {
        id
          title
        }
      }
      employees {
       name
        firstName
       awards {
         id
          title
        }
      }
    }
  }
}
```

**Resultaten van de Steekproef**

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "Apple Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/steve-jobs",
            "name": "Jobs",
            "firstName": "Steve",
            "awards": []
          },
          "employees": [
            {
              "name": "Marsh",
              "firstName": "Duke",
              "awards": []
            },
            {
              "name": "Caulfield",
              "firstName": "Max",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                }
              ]
            }
          ]
        },
        {
          "name": "Little Pony, Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/adam-smith",
            "name": "Smith",
            "firstName": "Adam",
            "awards": []
          },
          "employees": [
            {
              "name": "Croft",
              "firstName": "Lara",
              "awards": [
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            },
            {
              "name": "Slade",
              "firstName": "Cutter",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                },
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            }
          ]
        },
        {
          "name": "NextStep Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/steve-jobs",
            "name": "Jobs",
            "firstName": "Steve",
            "awards": []
          },
          "employees": [
            {
              "name": "Smith",
              "firstName": "Joe",
              "awards": []
            },
            {
              "name": "Lincoln",
              "firstName": "Abraham",
              "awards": []
            }
          ]
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Alle personen met de naam &quot;Jobs&quot; of &quot;Smith&quot; {#sample-all-persons-jobs-smith}

Een query die alle `persons` filtert voor alle items met de naam `Jobs` of `Smith` .

**de Vraag van de Steekproef**

```graphql
query {
  personList(filter: {
    name: {
      _logOp: OR
      _expressions: [
        {
          value: "Jobs"
        },
        {
          value: "Smith"
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

**Resultaten van de Steekproef**

```json
{
  "data": {
    "personList": {
      "items": [
        {
          "name": "Smith",
          "firstName": "Adam"
        },
        {
          "name": "Smith",
          "firstName": "Joe"
        },
        {
          "name": "Jobs",
          "firstName": "Steve"
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Alle personen die geen naam hebben van &quot;Taken&quot; {#sample-all-persons-not-jobs}

Een query die alle `persons` filtert voor alle items met de naam `Jobs` of `Smith` .

**de Vraag van de Steekproef**

```graphql
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

**Resultaten van de Steekproef**

```json
{
  "data": {
    "personList": {
      "items": [
        {
          "name": "Lincoln",
          "firstName": "Abraham"
        },
        {
          "name": "Smith",
          "firstName": "Adam"
        },
        {
          "name": "Slade",
          "firstName": "Cutter"
        },
        {
          "name": "Marsh",
          "firstName": "Duke"
        },
        {
          "name": "Smith",
          "firstName": "Joe"
        },
        {
          "name": "Croft",
          "firstName": "Lara"
        },
        {
          "name": "Caulfield",
          "firstName": "Max"
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Alle avonturen waarvan `_path` begint met een bepaald voorvoegsel {#sample-wknd-all-adventures-cycling-path-filter}

Alle `adventures` waarbij `_path` begint met een specifiek voorvoegsel (`/content/dam/wknd/en/adventures/cycling`).

**de Vraag van de Steekproef**

```graphql
query {
  adventureList(
    filter: {
      _path: {
        _expressions: [
        {
          value: "/content/dam/wknd/en/adventures/cycling"
         _operator: STARTS_WITH
        }]
       }
    })
    {
    items {
      _path
    }
  }
}
```

**Resultaten van de Steekproef**

```json
{
  "data": {
    "adventureList": {
      "items": [
        {
          "_path": "/content/dam/wknd/en/adventures/cycling-southern-utah/cycling-southern-utah"
        },
        {
          "_path": "/content/dam/wknd/en/adventures/cycling-tuscany/cycling-tuscany"
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Alle steden in Duitsland of Zwitserland met een bevolking tussen 400000 en 999999 {#sample-all-cities-d-ch-population}

Hier wordt een combinatie van velden gefilterd. `AND` (impliciet) wordt gebruikt om de `population` waaier te selecteren, terwijl `OR` (uitdrukkelijk) wordt gebruikt om de vereiste steden te selecteren.

**de Vraag van de Steekproef**

```graphql
query {
  cityList(filter: {
    population: {
      _expressions: [
        {
          value: 400000
          _operator: GREATER_EQUAL
        }, {
          value: 1000000
          _operator: LOWER
        }
      ]
    },
    country: {
      _logOp: OR
      _expressions: [
        {
          value: "Germany"
        }, {
          value: "Switzerland"
        }
      ]
    }
  }) {
    items {
      name
      population
      country
    }
  }
}
```

**Resultaten van de Steekproef**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Stuttgart",
          "population": 634830,
          "country": "Germany"
        },
        {
          "name": "Zurich",
          "population": 415367,
          "country": "Switzerland"
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Alle steden met SAN in naam, ongeacht het geval {#sample-all-cities-san-ignore-case}

Deze zoekopdracht wordt uitgevoerd voor alle steden die `SAN` in de naam hebben, ongeacht het geval.

**de Vraag van de Steekproef**

```graphql
query {
  cityList(filter: {
    name: {
      _expressions: [
        {
          value: "SAN"
          _operator: CONTAINS
          _ignoreCase: true
        }
      ]
    }
  }) {
    items {
      name
      population
      country
    }
  }
}
```

**Resultaten van de Steekproef**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA"
        },
        {
          "name": "San Jose",
          "population": 1026350,
          "country": "USA"
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Filter op een array met een item dat minstens één keer moet voorkomen {#sample-array-item-occur-at-least-once}

Deze vraagfilters op een serie met een punt (`city:na`) dat minstens eens moet voorkomen.

**de Vraag van de Steekproef**

```graphql
query {
  cityList(filter: {
    categories: {
      _expressions: [
        {
          value: "city:na"
          _apply: AT_LEAST_ONCE
        }
      ]
    }
  }) {
    items {
      name
      population
      country
      categories
    }
  }
}
```

**Resultaten van de Steekproef**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA",
          "categories": [
            "city:beach",
            "city:na"
          ]
        },
        {
          "name": "San Jose",
          "population": 1026350,
          "country": "USA",
          "categories": [
            "city:na"
          ]
        }
      ]
    }
  }
}
```

### Voorbeeldquery - Filter op een exacte arraywaarde {#sample-array-exact-value}

Deze query filtert op een exacte arraywaarde.

**de Vraag van de Steekproef**

```graphql
query {
  cityList(filter: {
    categories: {
      _expressions: [
        {
          values: [
            "city:beach",
            "city:na"
          ]
        }
      ]
    }
  }) {
    items {
      name
      population
      country
      categories
    }
  }
}
```

**Resultaten van de Steekproef**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA",
          "categories": [
            "city:beach",
            "city:na"
          ]
        }
      ]
    }
  }
}
```

### Voorbeeldquery voor geneste inhoudsfragmenten - Alle bedrijven met ten minste één werknemer met de naam &quot;Smith&quot; {#sample-companies-employee-smith}

Deze query illustreert het filteren op een `person` van `name` &quot;Smith&quot;, waarbij informatie wordt geretourneerd uit twee geneste fragmenten - `company` en `employee` .

**de Vraag van de Steekproef**

```graphql
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

**Resultaten van de Steekproef**

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "NextStep Inc.",
          "ceo": {
            "name": "Jobs",
            "firstName": "Steve"
          },
          "employees": [
            {
              "name": "Smith",
              "firstName": "Joe"
            },
            {
              "name": "Lincoln",
              "firstName": "Abraham"
            }
          ]
        }
      ]
    }
  }
}
```

### Voorbeeldquery voor geneste inhoudsfragmenten - Alle bedrijven waar alle werknemers de &quot;Gamestar&quot;-prijs hebben gewonnen {#sample-all-companies-employee-gamestar-award}

Deze query illustreert het filteren op drie geneste fragmenten - `company` , `employee` en `award` .

**de Vraag van de Steekproef**

```graphql
query {
  companyList(filter: {
    employees: {
      _apply: ALL
      _match: {
        awards: {
          _match: {
            id: {
              _expressions: [
                {
                  value: "GS"
                  _operator:EQUALS
                }
              ]
            }
          }
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
        awards {
          id
          title
        }
      }
    }
  }
}
```

**Resultaten van de Steekproef**

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "Little Pony, Inc.",
          "ceo": {
            "name": "Smith",
            "firstName": "Adam"
          },
          "employees": [
            {
              "name": "Croft",
              "firstName": "Lara",
              "awards": [
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            },
            {
              "name": "Slade",
              "firstName": "Cutter",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                },
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            }
          ]
        }
      ]
    }
  }
}
```

### Voorbeeldquery voor metagegevens - Lijst met metagegevens voor onderscheidingen: GB {#sample-metadata-awards-gb}

Deze query illustreert het filteren op drie geneste fragmenten - `company` , `employee` en `award` .

**de Vraag van de Steekproef**

```graphql
query {
  awardList(filter: {
      id: {
        _expressions: [
          {
            value:"GB"
          }
        ]
    }
  }) {
    items {
      _metadata {
        stringMetadata {
          name,
          value
        }
      }
      id
      title
    }
  }
}
```

**Resultaten van de Steekproef**

```json
{
  "data": {
    "awardList": {
      "items": [
        {
          "_metadata": {
            "stringMetadata": [
              {
                "name": "title",
                "value": "Gameblitz Award"
              },
              {
                "name": "description",
                "value": ""
              }
            ]
          },
          "id": "GB",
          "title": "Gameblitz"
        }
      ]
    }
  }
}
```

## Voorbeeldquery&#39;s met het WKND-project {#sample-queries-using-wknd-project}

Deze steekproefvragen zijn gebaseerd op het project WKND. Het heeft het volgende:

* Modellen voor inhoudsfragmenten zijn beschikbaar onder:
  `http://<hostname>:<port>/libs/dam/cfm/models/console/content/models.html/conf/wknd`

* Inhoudsfragmenten (en andere inhoud) beschikbaar onder:
  `http://<hostname>:<port>/assets.html/content/dam/wknd/en`
  `http://<hostname>:<port>/assets.html/content/dam/wknd-shared/en`

>[!NOTE]
>
>Omdat de resultaten extensief kunnen zijn, worden ze hier niet gereproduceerd.

### Voorbeeldquery voor alle inhoudsfragmenten van een bepaald model met de opgegeven eigenschappen {#sample-wknd-all-model-properties}

Met deze voorbeeldquery wordt het volgende gevraagd:

* voor alle inhoudsfragmenten van het type `article`
* met de `_path` en eigenschappen van de `authorFragment` .

**de Vraag van de Steekproef**

```graphql
{
  articleList {
    items {
      _path
      authorFragment {
        _path
        firstName
        lastName
        birthDay
      }
    }
 }
}
```

### Voorbeeldquery voor metagegevens {#sample-wknd-metadata}

Deze query vraagt om:

* voor alle inhoudsfragmenten van het type `adventure`
* metagegevens

**de Vraag van de Steekproef**

```graphql
{
  adventureList {
    items {
      _path,
      _metadata {
        stringMetadata {
          name,
          value
        }
        stringArrayMetadata {
          name,
          value
        }
        intMetadata {
          name,
          value
        }
        intArrayMetadata {
          name,
          value
        }
        floatMetadata {
          name,
          value
        }
        floatArrayMetadata {
          name,
          value
        }
        booleanMetadata {
          name,
          value
        }
        booleanArrayMetadata {
          name,
          value
        }
        calendarMetadata {
          name,
          value
        }
        calendarArrayMetadata {
          name,
          value
        }
      }
    }
  }
}
```

### Voorbeeldquery voor één inhoudsfragment van een bepaald model {#sample-wknd-single-content-fragment-of-given-model}

Met deze voorbeeldquery wordt het volgende gevraagd:

* voor één inhoudsfragment van tekst `article` op een specifiek pad
   * in dat fragment, alle indelingen van inhoud:
      * HTML
      * Markering
      * Onbewerkte tekst
      * JSON

**de Vraag van de Steekproef**

```graphql
{
  articleByPath(_path: "/content/dam/wknd-shared/en/magazine/alaska-adventure/alaskan-adventures") {
    item {
        _path
        authorFragment {
          _path
          firstName
          lastName
          birthDay
        }
        main {
          html
          markdown
          plaintext
          json
        }
    }
  }
}
```

### Voorbeeldquery voor een inhoudsfragmentmodel op basis van een model {#sample-wknd-content-fragment-model-from-model}

Met deze voorbeeldquery wordt het volgende gevraagd:

* voor één inhoudsfragment
   * details van het onderliggende inhoudsfragmentmodel

**de Vraag van de Steekproef**

```graphql
{
  adventureByPath(_path: "/content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van") {
    item {
      _path
      title
      _model {
        _path
        title
      }
    }
  }
}
```

### Voorbeeldquery voor een geneste inhoudsfragment - Type model{#sample-wknd-nested-fragment-single-model}

Deze query vraagt om:

* voor één inhoudsfragment van tekst `article` op een specifiek pad
   * binnen dat fragment, het pad en de auteur van het fragment waarnaar wordt verwezen (geneste fragment)

>[!NOTE]
>
>Het veld `referencearticle` heeft het gegevenstype `fragment-reference` .

**de Vraag van de Steekproef**

```graphql
{
  adventureByPath(_path: "/content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van") {
    item {
      _path
      title
      _model {
        _path
        title
      }
    }
  }
}
```

### Voorbeeldquery voor een geneste inhoudsfragment - Meerdere modeltypen{#sample-wknd-nested-fragment-multiple-model}

#### Type model waarnaar wordt verwezen

Deze query vraagt om:

* voor meerdere inhoudsfragmenten van het type `bookmark`
   * met fragmentverwijzingen naar andere fragmenten van het specifieke modeltype `Article`

>[!NOTE]
>
>Het veld `fragments` heeft het gegevenstype Data `fragment-reference` en het model `Article` is geselecteerd. Query levert `fragments` als een array van `[Article]` .

```graphql
{
  bookmarkList {
    items {
        fragments {
          _path
          author
        }
     }
  }
}
```

#### Meerdere modeltypen waarnaar wordt verwezen

Deze query vraagt om:

* voor meerdere inhoudsfragmenten van het type `bookmark`
   * met fragmentverwijzingen naar andere fragmenten van de specifieke modeltypen `Article` en `Adventure`

>[!NOTE]
>
>Het veld `fragments` heeft het gegevenstype `fragment-reference` , met de modellen `Article` en `Adventure` geselecteerd. Query levert `fragments` als een array van `[AllFragmentModels]` , die wordt verwijderd met het samenvoegingstype.

```graphql
{
  bookmarkList {
    items {
        fragments {
          ... on ArticleModel {
            _path
            author
          }
          ... on AdventureModel {
            _path
            adventureTitle
          }
        }
     }
  }
}
```

### Voorbeeldquery voor een inhoudsfragment van een specifiek model met inhoudsverwijzingen{#sample-wknd-fragment-specific-model-content-reference}

Deze query heeft twee voordelen:

1. Alle inhoudsverwijzingen retourneren.
1. De specifieke inhoudsverwijzingen van het type `attachments` retourneren.

Deze vragen worden ondervraagd:

* voor meerdere inhoudsfragmenten van het type `bookmark`
   * met Content Reference to other fragments

#### Voorbeeldquery voor meerdere inhoudfragmenten met vooraf ingestelde verwijzingen {#sample-wknd-multiple-fragments-prefetched-references}

Met de volgende query worden alle inhoudsverwijzingen geretourneerd met `_references` :

<!-- need replacement query -->

```graphql
{
  bookmarkList {
     _references {
         ... on ImageRef {
          _path
          type
          height
        }
        ... on MultimediaRef {
          _path
          type
          size
        }
        ... on DocumentRef {
          _path
          type
          author
        }
        ... on ArchiveRef {
          _path
          type
          format
        }
    }
    items {
        _path
    }
  }
}
```

#### Voorbeeldquery voor meerdere inhoudsfragmenten met bijlagen {#sample-wknd-multiple-fragments-attachments}

Met de volgende query worden alle `attachments` - een specifiek veld (subgroep) van het type `content-reference` geretourneerd:

>[!NOTE]
>
>Het veld `attachments` heeft het gegevenstype `content-reference` , met verschillende formulieren geselecteerd.

<!-- need replacement query -->

```graphql
{
  bookmarkList {
    items {
      attachments {
        ... on PageRef {
          _path
          type
        }
        ... on ImageRef {
          _path
          width
        }
        ... on MultimediaRef {
          _path
          size
        }
        ... on DocumentRef {
          _path
          author
        }
        ... on ArchiveRef {
          _path
          format
        }
      }
    }
  }
}
```

### Voorbeeldquery&#39;s voor een inhoudsfragment van een specifiek model met UUID-verwijzingen {#sample-wknd-fragment-specific-model-uuid-references}

Deze vragen worden ondervraagd:

* de UUID voor een inhoudsfragment en voor inhoudsfragmenten of -elementen waarnaar wordt verwezen
* het resultaat wordt geretourneerd via de JSON-eigenschap `_id`

#### Voorbeeldquery voor een inhoudsfragment van een specifiek model dat een UUID-verwijzing gebruikt {#sample-wknd-fragment-specific-model-using-a-uuid-reference}

De volgende query retourneert alle inhoudsverwijzingen met `_id` en `_path` :

```graphql
{
  articleList {
    items {
        _id
        _path
        title
        featuredImage {
          ... on ImageRef {
            _id
            _path           
          }
        }
        authorFragment {
          firstName
          lastName
          profilePicture {
            ... on ImageRef {
              _id
              _path
            }
          }
        }
      }
  }
}
```

#### Voorbeeldquery voor inhoudsfragmenten op UUID-verwijzing {#sample-wknd-fragment-specific-model-by-uuid-reference}

De volgende query retourneert alle inhoudsverwijzingen die betrekking hebben op een specifieke `_id` :

```graphql
{
  articleById(_id: "3ce2bf53-7436-4d3e-b19a-2793bc2ca63e") {
    item {
      _id
      _path
      title
      featuredImage {
        ... on ImageRef {
          _id
          _path
        }
      }
      authorFragment {
        firstName
        lastName
        profilePicture {
          ... on ImageRef {
            _id
            _path
          }
        }
      }
    }
  }
}
```

### Voorbeeldquery voor één inhoudsfragment met RTE Inline-verwijzing {#sample-wknd-single-fragment-rte-inline-reference}

Deze query vraagt om:

* voor één inhoudsfragment van tekst `bookmark` op een specifiek pad
   * binnen dat, de gealigneerde verwijzingen van RTE

>[!NOTE]
>
>De inline RTE-verwijzingen worden gehydrateerd in `_references` .

<!-- need replacement query -->

**de Vraag van de Steekproef**

```graphql
{
  bookmarkByPath(_path: "/content/dam/wknd/en/bookmarks/skitouring") {
    item {
      _path
      description {
        json
      }
    }
    _references {
      ... on ArticleModel {
        _path
      }
      ... on AdventureModel {
        _path
      }
      ... on ImageRef {
        _path
      }
      ... on MultimediaRef {
        _path
      }
      ... on DocumentRef {
        _path
      }
      ... on ArchiveRef {
        _path
      }
    }
  }
}
```

### Voorbeeldquery voor één variatie van inhoudsfragment van een bepaald model {#sample-wknd-single-fragment-given-model}

Deze query vraagt om:

* voor één inhoudsfragment van tekst `author` op een specifiek pad
   * binnen dat fragment, de gegevens met betrekking tot de variatie: `another`

**de Vraag van de Steekproef**

```graphql
{
  authorByPath(_path: "/content/dam/wknd-shared/en/contributors/ian-provo", variation: "another") {
    item {
        _path
        _variation
        firstName
        lastName
        birthDay
    }
  }
}
```

### Voorbeeldquery voor een benoemde variatie van meerdere inhoudsfragmenten van een bepaald model {#sample-wknd-variation-multiple-fragment-given-model}

Deze query vraagt om:

* voor inhoudfragmenten van het type `author` met een specifieke variatie: `another`

>[!NOTE]
>
>Deze vraag toont reserve voor de Fragmenten van de Inhoud aan die a [ Variatie ](/help/headless/graphql-api/content-fragments.md#variations) van de gespecificeerde naam niet hebben.

**de Vraag van de Steekproef**

```graphql
{
  authorList(variation: "another") {
    items {
        _path
        _variation
        firstName
        lastName
        birthDay
    }
  }
}
```

### Voorbeeldquery voor meerdere inhoudsfragmenten en de bijbehorende variaties van een bepaald model {#sample-wknd-multiple-fragment-variations-given-model}

Deze query vraagt om:

* voor inhoudfragmenten van het type `article` en alle variaties

**de Vraag van de Steekproef**

```xml
query {
  articleList(
    includeVariations: true  ){
    items {
      _variation
      _path
      _tags
      _metadata {
        stringArrayMetadata {
          name
          value
        }
      }
    }
  }
}
```

### Voorbeeldquery voor variaties van inhoudsfragmenten van een bepaald model waaraan een specifieke tag is gekoppeld{#sample-wknd-fragment-variations-given-model-specific-tag}

Deze query vraagt om:

* voor Inhoudsfragmenten van het type `article` met een of meer variaties met het label `WKND : Activity / Hiking`

**de Vraag van de Steekproef**

```xml
{
  articleList(
    includeVariations: true,
    filter: {_tags: {_expressions: [{value: "wknd:activity/hiking", _operator: CONTAINS}]}}
  ){
    items {
      _variation
      _path
      _tags
      _metadata {
        stringArrayMetadata {
          name
          value
        }
      }
    }
  }
}
```

### Voorbeeldquery voor meerdere inhoudsfragmenten van een bepaalde landinstelling {#sample-wknd-multiple-fragments-given-locale}

Deze query vraagt om:

* voor tekstfragmenten met inhoud `article` binnen de landinstelling `fr`

**de Vraag van de Steekproef**

```graphql
{ 
  articleList(_locale: "fr") {
    items {
      _path
      authorFragment {
        _path
        firstName
        lastName
        birthDay
      }
      main {
        html
        markdown
        plaintext
        json
      }
    }
  }
}
```

### Voorbeeldlijstquery met offset en limiet {#sample-list-offset-limit}

Deze query vraagt om:

* voor de pagina van resultaten die tot vijf artikelen bevatten, die van het vijfde artikel van de *volledige* resultatenlijst beginnen

**de Vraag van de Steekproef**

```graphql
{
   articleList(offset: 5, limit: 5) {
    items {
      authorFragment {
        _path
        firstName
        lastName
        birthDay
      }
      _path
    }
  }
}
```

### Voorbeeld van pagineringsquery met eerste en volgende  {#sample-pagination-first-after}

Deze query vraagt om:

* voor de pagina van resultaten die tot vijf avonturen bevatten, die van het bepaalde cursorpunt in *beginnen volledige* resultatenlijst

**de Vraag van de Steekproef**

```graphql
{
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

### Voorbeeldquery met filtering op _tags-id en exclusief variaties {#sample-filtering-tag-not-variations}

Deze query vraagt om:

* voor inhoudfragmenten van het type `vehicle` met het label `big-block`
* uitsluiten, variaties

**de Vraag van de Steekproef**

```graphql
query {
  vehicleList(
    filter: {
    _tags: {
      _expressions: [
        {
          value: "vehicles:big-block"
          _operator: CONTAINS
        }
      ]
    }
  }) {
    items {
      _variation
      _path
      type
      name
      model
      fuel
      _tags
    }
  }
} 
```

### Voorbeeldquery met filteren op _tags-id en inclusief variaties {#sample-filtering-tag-with-variations}

Deze query vraagt om:

* voor inhoudfragmenten van het type `vehicle` met het label `big-block`
* inclusief variaties

**de Vraag van de Steekproef**

```graphql
{
  enginePaginated(after: "SjkKNmVkODFmMGQtNTQyYy00NmQ4LTljMzktMjhlNzQwZTY1YWI2Cmo5", first: 9 ,includeVariations:true, sort: "name",
    filter: {
    _tags: {
      _expressions: [
        {
          value: "vehicles:big-block"
          _operator: CONTAINS
        }
      ]
    }
  }) {
    edges{
    node {
        _variation
        _path
        name
        type
        size
        _tags
        _metadata {
          stringArrayMetadata {
            name
            value
          }
        }
    }
      cursor
    }
  }
} 
```

## Voorbeeldquery&#39;s voor levering DAM en Dynamic Media Assets {#sample-queries-delivery-DAM-DM}

Voor voor het web geoptimaliseerde afbeeldingslevering (van DAM-middelen):

* [Voorbeeldquery voor voor voor het web geoptimaliseerde levering van afbeeldingen met volledige parameters](/help/headless/graphql-api/content-fragments.md#web-optimized-image-delivery-full-parameters)

* [Voorbeeldquery voor voor voor het web geoptimaliseerde afbeeldingslevering met één opgegeven parameter](/help/headless/graphql-api/content-fragments.md#web-optimized-image-delivery-single-query-variable)

Voor de levering van de URL aan een Dynamic Media-element

* Zie [ vraag van de Steekproef voor Dynamic Media activalevering door URL - de Verwijzing van het Beeld ](/help/headless/graphql-api/content-fragments.md#sample-query-dynamic-media-asset-delivery-by-url-imageref)

* Zie [ vraag van de Steekproef voor Dynamic Media activalevering door URL - Veelvoudige Verwijzingen ](/help/headless/graphql-api/content-fragments.md#sample-query-dynamic-media-asset-delivery-by-url-multiple-refs)

## De structuur voor het voorbeeldinhoudfragment (wordt gebruikt met GraphQL) {#content-fragment-structure-graphql}

De steekproefvragen zijn gebaseerd op de volgende structuur, die gebruikt:

* Één, of meer, [ Modellen van het Fragment van de Inhoud van de Steekproef ](#sample-content-fragment-models-schemas) - vorm de basis voor de schema&#39;s van GraphQL

* [ de Fragmenten van de Inhoud van de Steekproef ](#sample-content-fragments) die op de bovengenoemde modellen worden gebaseerd

### Voorbeeld van modellen van inhoudsfragmenten (schema&#39;s) {#sample-content-fragment-models-schemas}

Voor de steekproefvragen, gebruikt u de volgende Modellen van Inhoud, en hun onderlinge relaties (verwijzingen ->):

* [ Bedrijf ](#model-company)
-> [ Persoon ](#model-person)
    -> [ Uitreiking ](#model-award)

* [Plaats](#model-city)

#### Bedrijf {#model-company}

De basisvelden voor het bedrijf zijn:

| Veldnaam | Gegevenstype | Referentie |
|--- |--- |--- |
| Bedrijfsnaam | Tekst met één regel | |
| CEO | Fragmentverwijzing (enkele) | [ Persoon ](#model-person) |
| Werknemers | Fragmentverwijzing (meerdere velden) | [ Persoon ](#model-person) |

#### Persoon {#model-person}

De velden waarin een persoon wordt gedefinieerd, die ook een werknemer kan zijn:

| Veldnaam | Gegevenstype | Referentie |
|--- |--- |--- |
| Naam | Tekst met één regel | |
| Voornaam | Tekst met één regel | |
| Uitreiking | Fragmentverwijzing (meerdere velden) | [ Uitreiking ](#model-award) |

#### Uitreiking {#model-award}

De velden waarin een onderscheiding wordt gedefinieerd, zijn:

| Veldnaam | Gegevenstype | Referentie |
|--- |--- |--- |
| Sneltoets/id | Tekst met één regel | |
| Titel | Tekst met één regel | |

#### Plaats {#model-city}

De velden voor het definiëren van een stad zijn:

| Veldnaam | Gegevenstype | Referentie |
|--- |--- |--- |
| Naam | Tekst met één regel | |
| Land | Tekst met één regel | |
| Bevolking | Getal | |
| Categorieën | Tags | |

### Voorbeeldinhoudsfragmenten {#sample-content-fragments}

De volgende fragmenten worden gebruikt voor het juiste model.

#### Bedrijf {#fragment-company}

| Bedrijfsnaam | CEO | Werknemers |
|--- |--- |--- |
| Apple | Steve Jobs | Duke Marsh <br> Max Caulfield |
| Little Pony Inc. | Adam Smith | Lara Croft <br> Uitsnijdschaal |
| NextStep Inc. | Steve Jobs | Joe Smith <br> Abe Lincoln |

#### Persoon {#fragment-person}

| Naam | Voornaam | Uitreiking |
|--- |--- |--- |
| Lincoln | Abe | |
| Smith | Adam | |
| Slade | Tussenruimte | Gameblitz <br> Gamestar |
| Marsh | Duke | |
| Smith | Joe | |
| Uitsnijden | Lara | Gamestar |
| Caulfield | Max | Gameblitz |
| Taken | Steve | |

#### Uitreiking {#fragment-award}

| Sneltoets/id | Titel |
|--- |--- |
| GB | Gameblitz |
| GS | Gamestar |
| OSC | Oscar |

#### Plaats {#fragment-city}

| Naam | Land | Bevolking | Categorieën |
|--- |--- |--- |--- |
| Bazel | Zwitserland | 172258 | stad:emea |
| Berlin | Duitsland | 3669491 | stad:kapitaal <br> stad:emea |
| Boekarest | Roemenië | 1821000 | stad:kapitaal <br> stad:emea |
| San Francisco | VS | 883306 | stad:strand <br> stad:na |
| San Jose | VS | 102635 | plaats:na |
| Stuttgart | Duitsland | 634830 | stad:emea |
| Zurich | Zwitserland | 415367 | stad:kapitaal <br> stad:emea |
