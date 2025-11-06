---
title: Toegang tot uw inhoud via API's voor levering via AEM
description: In dit deel van de AEM Headless Developer Journey leert u hoe u GraphQL-query's kunt gebruiken om toegang te krijgen tot inhoud van Content Fragments.
exl-id: 1adecc69-5f92-4007-8a2a-65bf1e960645
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1320'
ht-degree: 0%

---

# Toegang tot uw inhoud via API&#39;s voor levering via AEM {#access-your-content}

In dit deel van de [&#x200B; Hoofdloze Reis van de Ontwikkelaar van AEM &#x200B;](overview.md), kunt u leren hoe te om de vragen van GraphQL te gebruiken om tot de inhoud van uw Fragments van de Inhoud toegang te hebben en het te voeren aan uw app (koploze levering).

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de hoofdloze reis van AEM, [&#x200B; hoe te om Uw Inhoud &#x200B;](model-your-content.md) te modelleren leerde u de grondbeginselen van inhoud modellerend in AEM, zodat zou u nu moeten begrijpen hoe te om uw inhoudsstructuur te modelleren, dan realiseer die structuur gebruikend de Modellen van het Fragment van de Inhoud van AEM en de Fragments van de Inhoud:

* De concepten en terminologie met betrekking tot inhoudsmodellen herkennen.
* Begrijp waarom de inhoud modellering voor de levering van de Inhoud zonder Zwaartepunt nodig is.
* Begrijp hoe u deze structuur kunt realiseren met AEM Content Fragment Models (en inhoud met Content Fragments schrijven).
* Begrijp hoe u uw inhoud modelleert; principes met basismonsters.

Dit artikel bouwt verder op deze basisbeginselen, zodat u begrijpt hoe u met de AEM GraphQL-API toegang krijgt tot inhoud zonder kop in AEM.

* **Publiek**: Begin
* **Doelstelling**: Leer hoe te om tot de inhoud van uw Fragmenten van de Inhoud toegang te hebben gebruikend de vragen van AEM GraphQL:
   * Introduceer GraphQL en de AEM GraphQL API.
   * Dive into the details of the AEM GraphQL API.
   * Bekijk sommige steekproefvragen om te zien hoe de dingen in praktijk werken.

## Wilt u dus toegang tot uw inhoud? {#so-youd-like-to-access-your-content}

Dus...u hebt al deze inhoud, netjes gestructureerd (in inhoudsfragmenten), en gewoon wachtend om uw nieuwe app te voeden. De vraag is: hoe kan het daar komen?

U hebt een manier nodig om specifieke inhoud als doel in te stellen, te selecteren wat u nodig hebt en terug te sturen naar uw app voor verdere verwerking.

Met Adobe Experience Manager (AEM) as a Cloud Service hebt u selectief toegang tot uw inhoudsfragmenten, met de AEM GraphQL API, om alleen de inhoud te retourneren die u nodig hebt. Dit betekent dat u zonder kop gestructureerde inhoud kunt leveren voor gebruik in uw toepassingen.

>[!NOTE]
>
>AEM GraphQL API is een aangepaste implementatie, gebaseerd op de standaard GraphQL API-specificatie.

## GraphQL - Een inleiding {#graphql-introduction}

GraphQL is een open-source-specificatie die het volgende biedt:

* een querytaal waarmee u specifieke inhoud van gestructureerde objecten kunt selecteren.
* een runtime om deze query&#39;s uit te voeren met uw gestructureerde inhoud.

GraphQL is een sterk getypeerde API. Dit betekent dat *alle* inhoud duidelijk door type moet worden gestructureerd en worden georganiseerd, zodat GraphQL ** begrijpt wat om toegang te hebben en hoe. De gegevensvelden zijn gedefinieerd in GraphQL-schema&#39;s, die de structuur van de inhoudsobjecten definiëren.

De eindpunten van GraphQL verstrekken dan de wegen die aan de vragen van GraphQL antwoorden.

Dit alles betekent dat uw app de inhoud die nodig is nauwkeurig, betrouwbaar en efficiënt kan selecteren - precies wat u nodig hebt bij gebruik met AEM.

>[!NOTE]
>
>Zie *GraphQL*.org en *GraphQL*.com.

<!--
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
-->

## AEM GRAPHQL API {#aem-graphql-api}

De AEM GraphQL API is een aangepaste versie gebaseerd op de standaard GraphQL API-specificatie, speciaal geconfigureerd om (complexe) query&#39;s uit te voeren op uw Content Fragments.

Inhoudsfragmenten worden gebruikt, omdat de inhoud is gestructureerd volgens Modellen van inhoudsfragmenten. Dit voldoet aan een basisvereiste van GraphQL.

* Een inhoudsfragmentmodel is samengesteld uit een of meer velden.
   * Elk veld wordt gedefinieerd op basis van een gegevenstype.
* Met Content Fragment Models worden de overeenkomstige AEM GraphQL-schema&#39;s gegenereerd.

Om tot GraphQL voor AEM (en de inhoud) eigenlijk toegang te hebben wordt een eindpunt gebruikt om de toegangspad te verstrekken.

De inhoud die wordt geretourneerd via de AEM GraphQL API kan vervolgens door uw toepassingen worden gebruikt.

Om u direct te helpen input, en testvragen, is een implementatie van de standaard interface GraphiQL ook beschikbaar voor gebruik met AEM GraphQL (dit kan met AEM worden geïnstalleerd). Het biedt functies zoals syntaxismarkering, automatisch aanvullen, automatisch suggereren, samen met een geschiedenis en online documentatie.

>[!NOTE]
>
>De AEM GraphQL API-implementatie is gebaseerd op de GraphQL Java-bibliotheken.

<!--
### Use Cases for Author and Publish Environments {#use-cases-author-publish-environments}

The use cases for the AEM GraphQL API can depend on the type of AEM as a Cloud Service environment:

* Publish environment; used to: 
  * Query content for JS application (standard use-case)

* Author environment; used to: 
  * Query content for "content management purposes":
    * GraphQL in AEM as a Cloud Service is currently a read-only API.
    * The REST API can be used for CR(u)D operations.
-->

## Inhoudsfragmenten voor gebruik met de AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

Inhoudsfragmenten kunnen worden gebruikt als basis voor GraphQL for AEM-schema&#39;s en -query&#39;s als:

* Zo kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren die zonder kop kan worden geleverd.
* Ze zijn gebaseerd op een Content Fragment Model, dat de structuur voor het resulterende fragment vooraf definieert met behulp van een selectie van gegevenstypen.
* Er kunnen extra structuurlagen worden bereikt met het gegevenstype Fragmentverwijzing, dat beschikbaar is wanneer u een model definieert.

### Modellen van inhoudsfragmenten {#content-fragments-models}

Deze modellen van inhoudsfragmenten:

* Wordt gebruikt om de Schema&#39;s te produceren, zodra **Toegelaten**.
* Geef de gegevenstypen en velden op die vereist zijn voor GraphQL. Ze zorgen ervoor dat uw toepassing alleen vraagt wat mogelijk is en wat wordt verwacht ontvangt.
* Het gegevenstype **Verwijzingen van het Fragment** kan in uw model worden gebruikt om een ander Fragment van de Inhoud van verwijzingen te voorzien, en zo extra niveaus van structuur introduceren.

### Fragmentverwijzingen {#fragment-references}

**Verwijzing van het fragment** en **Verwijzing UUID van het Fragment**:

* Zijn specifieke gegevenstypen beschikbaar wanneer u een inhoudsfragmentmodel definieert.
* Verwijst naar een ander fragment, afhankelijk van een specifiek inhoudsfragmentmodel.
* Hiermee kunt u gestructureerde gegevens maken en ophalen.

   * Wanneer bepaald als a **multifeed**, kunnen de veelvoudige sub-fragmenten (teruggewonnen) door het eerste fragment van verwijzingen worden voorzien.

## De AEM GraphQL API daadwerkelijk gebruiken {#actually-using-aem-graphiql}

### Eerste instelling {#initial-setup}

Voordat u begint met query&#39;s op uw inhoud, moet u:

* Uw eindpunt inschakelen
   * Extra > Algemeen > GraphQL
   * [GraphQL Endpoint inschakelen](/help/headless/graphql-api/graphql-endpoint.md)
      * Dit zal ook GrahiQL winde toelaten.

### Voorbeeldstructuur {#sample-structure}

Als u de AEM GraphQL API daadwerkelijk in een query wilt gebruiken, kunt u de twee basisstructuren van het Content Fragment Model gebruiken:

* Bedrijf
   * Naam - tekst
   * CEO (Persoon) - Fragmentverwijzing
   * Werknemers (personen) - Fragmentverwijzing(en)
* Persoon
   * Naam - tekst
   * Voornaam - tekst

Zoals u kunt zien, verwijzen de gebieden CEO en Werknemers, naar de fragmenten van de Persoon.

De fragmentmodellen worden gebruikt:

* wanneer u de inhoud maakt in de Content Fragment Editor
* om de GraphQL-schema&#39;s te genereren waarop u een query uitvoert

### Waar kan ik uw query&#39;s testen? {#where-to-test-your-queries}

De vragen kunnen in de interface worden ingegaan GraphiQL. U kunt tot de vraagredacteur van één van beiden toegang hebben:

* **Hulpmiddelen** > **Algemeen** > **de Redacteur van de Vraag van GraphQL**
* direct; bijvoorbeeld `http://localhost:4502/aem/graphiql.html`

![&#x200B; GraphiQL Interface &#x200B;](assets/graphiql-interface.png " GraphiQL Interface ")

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

Voor de volledige informatie over het gebruik van de AEM GraphQL API, samen met het configureren van de benodigde elementen, kunt u verwijzen naar:

* GraphQL leren gebruiken met AEM
* De structuur van het voorbeeldinhoudsfragment
* GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s

## Volgende functies {#whats-next}

Nu u hebt geleerd om tot uw hoofdloze inhoud toegang te hebben en te vragen gebruikend AEM GraphQL API kunt u nu [&#x200B; leren hoe te om REST API te gebruiken om tot de inhoud van uw Fragments van de Inhoud toegang te hebben en bij te werken &#x200B;](update-your-content.md).

## Aanvullende bronnen {#additional-resources}

* [&#x200B; Adobe Experience Manager as a Cloud Service APIs &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/)
* [&#x200B; GraphQL.org &#x200B;](https://graphql.org)
   * [&#x200B; Schemas &#x200B;](https://graphql.org/learn/schema/)
   * [&#x200B; Variabelen &#x200B;](https://graphql.org/learn/queries/#variables)
   * [&#x200B; de bibliotheken van GraphQL Java &#x200B;](https://graphql.org/code/#java)
* [&#x200B; GraphiQL &#x200B;](https://graphql.org/learn/serving-over-http/#graphiql)
* [GraphQL leren gebruiken met AEM](/help/headless/graphql-api/content-fragments.md)
   * [GraphQL Endpoint inschakelen](/help/headless/graphql-api/graphql-endpoint.md)
   * [De AEM GraphiQL-interface installeren](/help/headless/graphql-api/graphiql-ide.md)
* [De structuur van het voorbeeldinhoudsfragment](/help/headless/graphql-api/sample-queries.md#content-fragment-structure-graphql)
* [GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s](/help/headless/graphql-api/sample-queries.md)
   * [Voorbeeldquery - één specifiek stedenfragment](/help/headless/graphql-api/sample-queries.md#sample-single-specific-city-fragment)
   * [Voorbeeldquery voor metagegevens - Lijst met metagegevens voor onderscheidingen: GB](/help/headless/graphql-api/sample-queries.md#sample-metadata-awards-gb)
   * [Voorbeeldquery - Alle steden met een benoemde variatie](/help/headless/graphql-api/sample-queries.md#sample-cities-named-variation)
* [Functionaliteit van inhoudsfragment inschakelen in configuratievenster](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser)
* [Werken met inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)
   * [Modellen van inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md)
   * [JSON-uitvoer](/help/assets/content-fragments/content-fragments-json-preview.md)
* [&#x200B; Begrijp het Middel dat van de dwars-Oorsprong (CORS) deelt &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html#understand-cross-origin-resource-sharing-(cors))
* [GraphQL Persisted Queries - caching inschakelen in Dispatcher](/help/headless/deployment/dispatcher-caching.md)
* [Toegangstokens genereren voor server-side API&#39;s](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md)
* [&#x200B; Begonnen het Worden met de Zetel van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) - een korte videolesreeks die een overzicht geeft van het gebruiken van AEM hoofdloze eigenschappen, met inbegrip van inhoud modellering en GraphQL.
