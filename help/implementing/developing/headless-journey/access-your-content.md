---
title: Hoe te om tot Uw Inhoud via AEM levering APIs toegang te hebben
description: In dit deel van de AEM Headless Ontwikkelaarsreis, leer hoe te om vragen te gebruiken GraphQL om tot uw inhoud van de Fragmenten van de Inhoud toegang te hebben.
hide: true
hidefromtoc: true
index: false
exl-id: 5ef557ff-e299-4910-bf8c-81c5154ea03f
translation-type: tm+mt
source-git-commit: c9b8e14a3beca11b6f81f2d5e5983d6fd801bf3f
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 1%

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

<!--
## GraphQL - An Introduction {#graphql-introduction}

GraphQL is an open-source specification that provides:

* a query language that enables you to select specific content from structured objects.
* a runtime to fulfill these queries with your structured content.

GraphQL is a *strongly* typed API. This means that *all* content must be clearly structured and organized by type, so that GraphQL *understands* what to access and how. The data fields are defined within GraphQL schemas, that define the structure of your content objects. 

GraphQL endpoints then provide the paths that respond to the GraphQL queries.

All this means that your app can accurately, reliably and efficiently select the content that it needs - just what you need when used with AEM.

>[!NOTE]
>
>See *GraphQL*.org and *GraphQL*.com.

## AEM and GraphQL {#aem-graphql}

GraphQL is used in various locations in AEM; for example:

* Content Fragments
  * A customized API has been developed for this use-case (Headless Delivery to your app).
    * This is the AEM GraphQL API.
* Commerce
  * AEM Commerce consumes data from a Commerce platform via GraphQL.
  * There are GraphQL integrations between AEM and various third-party commerce solutions, used with the extension hooks provided by the CIF Core Components.
    * This does not use the AEM GraphQL API.

>[!NOTE]
>
>This step of the Headless Journey is only concerned with the AEM GraphQL API and Content Fragments.

## AEM GraphQL API {#aem-graphql-api}

The AEM GraphQL API is a customized version based on the standard GraphQL API specification, specially configured to allow you to perform (complex) queries on your Content Fragments.

Content Fragments are used, as the content is structured according to Content Fragment Models. This fulfills a basic requirement of GraphQL.

* A Content Fragment Model is built up of one, or more, fields. 
  * Each field is defined according to a Data Type.
* Content Fragment Models are used to generate the corresponding AEM GraphQL Schemas.

To actually access GraphQL for AEM (and the content) an endpoint is used to provide the access path. 

The content returned, via the AEM GraphQL API, can then be used by your applications. 

>[!NOTE]
>
>The AEM GraphQL API implementation is based on the GraphQL Java libraries.

### Use Cases for Author and Publish Environments {#use-cases-author-publish-environments}

The use cases for the AEM GraphQL API can depend on the type of AEM as a Cloud Service environment:

* Publish environment; used to: 
  * Query content for JS application (standard use-case)

* Author environment; used to: 
  * Query content for "content management purposes":
    * GraphQL in AEM as a Cloud Service is currently a read-only API.
    * The REST API can be used for CR(u)D operations.

## Content Fragments for use with the AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

Content Fragments can be used as a basis for GraphQL for AEM schemas and queries as:

* They enable you to design, create, curate and publish page-independent content.
* They are based on a Content Fragment Model, which pre-defines the structure for the resulting fragment by means of defined data types.
* Additional layers of structure can be achieved with the Fragment Reference data type, available when defining a model.
 
### Content Fragment Models {#content-fragments-models}

These Content Fragment Models:

* Are used to generate the Schemas, once **Enabled**.

* Provide the data types and fields required for GraphQL. They ensure that your application only requests what is possible, and receives what is expected.

* The data type **Fragment References** can be used in your model to reference another Content Fragment, and so introduce additional levels of structure.

### Fragment References {#fragment-references}

The **Fragment Reference**:

* Is a specific data type available when defining a Content Fragment Model.

* References another fragment, dependent on a specific Content Fragment Model.

* Allows you to create, and then retrieve, structured data.

  * When defined as a **multifeed**, multiple sub-fragments can be referenced (retrieved) by the prime fragment.

### JSON Preview {#json-preview}

To help with designing and developing your Content Fragment Models, you can preview JSON output in the Content Fragment Editor.

## GraphQL Schema Generation from Content Fragments {#graphql-schema-generation-content-fragments}

GraphQL is a strongly typed API, which means that content must be clearly structured and organized by type. The GraphQL specification provides a series of guidelines on how to create a robust API for interrogating content on a certain instance. To do this, a client needs to fetch the Schema, which contains all the types necessary for a query. 

For Content Fragments, the GraphQL schemas (structure and types) are based on **Enabled** Content Fragment Models and their data types.

>[!CAUTION]
>
>All the GraphQL schemas (derived from Content Fragment Models that have been **Enabled**) are readable through the GraphQL endpoint.
>
>This means that you need to ensure that no sensitive content is available, to ensure that no sensitive data is exposed via GraphQL endpoints; for example, this includes information that could be present as field names in the model definition.

For example, if a user created a Content Fragment Model called `Article`, then AEM generates the object `article` that is of a type `ArticleModel`. The fields within this type correspond to the fields and data types defined in the model.

1. A Content Fragment Model:

   ![Content Fragment Model for use with GraphQL](assets/graphqlapi-cfmodel.png "Content Fragment Model for use with GraphQL")

1. The corresponding GraphQL schema (output from GraphiQL automatic documentation):
   ![GraphQL Schema based on Content Fragment Model](assets/graphqlapi-cfm-schema.png "GraphQL Schema based on Content Fragment Model")

   This shows that the generated type `ArticleModel` contains several [fields](#fields). 
   
   * Three of them have been controlled by the user: `author`, `main` and `referencearticle`.

   * The other fields were added automatically by AEM, and represent helpful methods to provide information about a certain Content Fragment; in this example, `_path`, `_metadata`, `_variations`. These [helper fields](#helper-fields) are marked with a preceding `_` to distinguish between what has been defined by the user and what has been auto-generated.

1. After a user creates a Content Fragment based on the Article model, it can then be interrogated through GraphQL. For examples, see the Sample Queries.md#graphql-sample-queries) (based on a sample Content Fragment structure for use with GraphQL.

In GraphQL for AEM, the schema is flexible. This means that it is auto-generated each and every time a Content Fragment Model is created, updated or deleted. The data schema caches are also refreshed when you update a Content Fragment Model.

The Sites GraphQL service listens (in the background) for any modifications made to a Content Fragment Model. When updates are detected, only that part of the schema is regenerated. This optimization saves time and provides stability.

So for example, if you:

1. Install a package containing `Content-Fragment-Model-1` and `Content-Fragment-Model-2`:
 
   1. GraphQL types for `Model-1` and `Model-2` will be generated.

1. Then modify `Content-Fragment-Model-2`:

   1. Only the `Model-2` GraphQL type will get updated.

   1. Whereas `Model-1` will remain the same. 

>[!NOTE]
>
>This is important to note in case you want to do bulk updates on Content Fragment Models through the REST api, or otherwise.

The schema is served through the same endpoint as the GraphQL queries, with the client handling the fact that the schema is called with the extension `GQLschema`. For example, performing a simple `GET` request on `/content/cq:graphql/global/endpoint.GQLschema` will result in the output of the schema with the Content-type: `text/x-graphql-schema;charset=iso-8859-1`.

### Schema Generation - Unpublished Models {#schema-generation-unpublished-models}

When Content Fragments are nested it can happen that a parent Content Fragment Model is published, but a referenced model is not.

>[!NOTE]
>
>The AEM UI prevents this happening, but if publishing is made programmatically, or with content packages, it can occur.

When this happens, AEM generates an *incomplete* Schema for the parent Content Fragment Model. This means that the Fragment Reference, which is dependent on the unpublished model, is removed from the schema.

## AEM GraphQL Endpoints {#aem-graphql-endpoints}

An endpoint is the path used to access GraphQL for AEM. Using this path you (or your app) can:

* access the GraphQL schemas,
* send your GraphQL queries,
* receive the responses (to your GraphQL queries).

AEM allows for:

* A global endpoint - available for use by all sites.
* Endpoints for specific Sites configurations - that you can configure (in the Configuration Browser), specific to a specified site/project.

## Permissions {#permissions}

The permissions are those required for accessing Assets.

## The AEM GraphiQL Interface {#aem-graphiql-interface}

To help you directly input, and test queries, an implementation of the standard GraphiQL interface is available for use with AEM GraphQL. This can be installed with AEM.

>[!NOTE]
>
>GraphiQL is bound the global endpoint (and does not work with other endpoints for specific Sites configurations).

It provides features such as syntax-highlighting, auto-complete, auto-suggest, together with a history and online documentation.

![GraphiQL Interface](assets/graphiql-interface.png "GraphiQL Interface")
-->

## Eigenlijk de AEM GraphQL API {#actually-using-aem-graphiql} gebruiken

### Eerste instelling {#initial-setup}

Voordat u begint met query&#39;s op uw inhoud, moet u:

* Uw eindpunt inschakelen
   * Gereedschappen gebruiken -> Sites -> GrafiekQL

* GraphiQL installeren (indien vereist)
   * Geïnstalleerd als een toegewezen pakket

### Voorbeeldstructuur {#sample-structure}

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

### Waar moet u uw query&#39;s testen {#where-to-test-your-queries}

De vragen kunnen in de interface GraphiQL, bijvoorbeeld bij zijn ingegaan:

* `http://localhost:4502/content/graphiql.html `

### Aan de slag met query&#39;s {#getting-Started-with-queries}

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
   * [GrafiekQL-eindpunt inschakelen](/help/assets/content-fragments/graphql-api-content-fragments.md#enabling-graphql-endpoint)
   * [De interface AEM GraphiQL installeren](/help/assets/content-fragments/graphql-api-content-fragments.md#installing-graphiql-interface)
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
