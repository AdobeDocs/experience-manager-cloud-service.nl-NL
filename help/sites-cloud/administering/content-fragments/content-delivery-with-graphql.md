---
title: Levering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL
description: Leer de basisbeginselen van het realiseren van een AEM Headless CMS met behulp van Content Fragments met GraphQL voor het leveren van inhoud zonder kop.
feature: Content Fragments, GraphQL API
role: Developer, Architect
exl-id: 3aa7073a-6c6b-47b7-99d8-bba2d9a00af5
solution: Experience Manager Sites
source-git-commit: 0664e5dc4a7619a52cd28c171a44ba02c592ea3d
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 0%

---

# Levering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}

Met Content Fragments en de GraphQL API kunt u Adobe Experience Manager (AEM) as a Cloud Service gebruiken als een Headless Content Management System (CMS).

Dit wordt bereikt door gebruik te maken van Content Fragments, samen met de AEM GraphQL API (een aangepaste implementatie die is gebaseerd op standaard GraphQL), voor het zonder problemen aanbieden van gestructureerde inhoud voor gebruik in uw toepassingen. Dankzij de mogelijkheid om één API-query aan te passen, kunt u de specifieke inhoud ophalen en leveren die u wilt/moet renderen (als antwoord op de enkele API-query).

>[!NOTE]
>
>Zie ook:
>
>* [&#x200B; wat is Headless?](/help/headless/what-is-headless.md) voor een inleiding aan de concepten en de terminologie zonder kop.
>
>* [&#x200B; Zwaartepunt en AEM &#x200B;](/help/headless/introduction.md) voor een inleiding aan Zwaardeloze Ontwikkeling voor AEM Sites as a Cloud Service.

>[!NOTE]
>
>GraphQL wordt momenteel gebruikt in twee (afzonderlijke) scenario&#39;s in Adobe Experience Manager (AEM) as a Cloud Service:
>
>* [&#x200B; AEM Commerce verbruikt gegevens van een handelsplatform via GraphQL.](/help/commerce-cloud/cif-storefront/integrating/magento.md)
>* [&#x200B; de Inhoudsfragmenten van AEM werken samen met AEM GraphQL API (een aangepaste implementatie, die op standaardGraphQL wordt gebaseerd), om gestructureerde inhoud voor gebruik in uw toepassingen &#x200B;](/help/headless/graphql-api/content-fragments.md) te leveren.

## Headless CMS {#headless-cms}

Een Headless Content Management System (CMS) is een back-end alleen inhoudsbeheersysteem dat expliciet is ontworpen en gebouwd als een opslagplaats voor inhoud die inhoud toegankelijk maakt via een API, voor weergave op elk apparaat.

Met betrekking tot het ontwerpen van inhoudsfragmenten in AEM betekent dit dat:

* U kunt de Fragmenten van de Inhoud aan auteursinhoud gebruiken die niet hoofdzakelijk bedoeld is om (1 :1) op geformatteerde pagina&#39;s direct te worden gepubliceerd.

* De inhoud van de inhoudsfragmenten wordt vooraf gestructureerd volgens de modellen van het inhoudsfragment. Hierdoor wordt de toegang voor uw toepassingen vereenvoudigd, waardoor uw inhoud verder wordt verwerkt.

## GraphQL - Een overzicht {#graphql-overview}

GraphQL is:

* &quot;*...een vraagtaal voor APIs en runtime voor het vervullen van die vragen met uw bestaande gegevens.*&quot;.

  Zie [&#x200B; GraphQL.org &#x200B;](https://graphql.org)

[&#x200B; AEM GraphQL API &#x200B;](#aem-graphql-api) staat u toe om (complexe) vragen op uw [&#x200B; Fragmenten van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/overview.md) uit te voeren; met elke vraag die volgens een specifiek modeltype is. De geretourneerde inhoud kan vervolgens door uw toepassingen worden gebruikt.

## AEM GRAPHQL API {#aem-graphql-api}

Voor Adobe Experience as a Cloud Experience is een aangepaste implementatie van de standaard GraphQL API ontwikkeld. Zie [&#x200B; AEM GraphQL API voor gebruik met de Fragmenten van de Inhoud &#x200B;](/help/headless/graphql-api/content-fragments.md) voor details.

De implementatie van AEM GraphQL API is gebaseerd op de [&#x200B; bibliotheken van GraphQL Java &#x200B;](https://graphql.org/code/#java).

## Inhoudsfragmenten voor gebruik met de AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

[&#x200B; de Fragmenten van de Inhoud &#x200B;](#content-fragments) kunnen als basis voor GraphQL voor AEM vragen als worden gebruikt:

* Hiermee kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren.
* De [&#x200B; Modellen van het Fragment van de Inhoud &#x200B;](#content-fragments-models) verstrekken de vereiste structuur door middel van bepaalde gegevenstypes.
* De [&#x200B; Verwijzing van het Fragment &#x200B;](#fragment-references), beschikbaar wanneer het bepalen van een model, kan worden gebruikt om extra lagen van structuur te bepalen.

![&#x200B; de Fragmenten van de Inhoud voor gebruik met de Fragmenten van de Inhoud van GraphQL &#x200B;](assets/cf-contentdelivery-cf-use-with-graphql.png " voor gebruik met GraphQL ")

### Inhoudsfragmenten {#content-fragments}

Content Fragments:

* Bevat gestructureerde inhoud.

* Zij zijn gebaseerd op het Model van het Fragment van de a [&#x200B; Inhoud &#x200B;](#content-fragments-models), dat de structuur voor het resulterende fragment vooraf bepaalt.

### Modellen van inhoudsfragmenten {#content-fragments-models}

Deze [&#x200B; Modellen van het Fragment van Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/content-fragment-models.md):

* Wordt gebruikt om de [&#x200B; Schema&#39;s &#x200B;](https://graphql.org/learn/schema/) te produceren, eens **Toegelaten**.

* Geef de gegevenstypen en velden op die vereist zijn voor GraphQL. Ze zorgen ervoor dat uw toepassing alleen vraagt wat mogelijk is en wat wordt verwacht ontvangt.

* Het gegevenstype **[Verwijzingen van het Fragment](#fragment-references)** kan in uw model worden gebruikt om een ander Fragment van de Inhoud van verwijzingen te voorzien, en zo extra niveaus van structuur introduceren.

### Fragmentverwijzingen {#fragment-references}

De **[Verwijzing van het Fragment](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#fragment-reference-nested-fragments)**:

* Is in samenwerking met GraphQL van bijzonder belang.

* Dit is een specifiek gegevenstype dat kan worden gebruikt bij het definiëren van een inhoudsfragmentmodel.

* Verwijst naar een ander fragment, afhankelijk van een specifiek inhoudsfragmentmodel.

* Hiermee kunt u gestructureerde gegevens ophalen.

   * Wanneer bepaald als a **multifeed**, kunnen de veelvoudige sub-fragmenten (teruggewonnen) door het eerste fragment van verwijzingen worden voorzien.

## Structuur van inhoudsfragment analyseren {#analyzing-content-fragments-structure}

Om met analyse te helpen, verstrekt AEM verscheidene methodes om de structuur van uw fragmenten van de [&#x200B; redacteur van het Fragment van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/authoring.md) te bekijken.

Zie [&#x200B; Analyserend de Structuur van het Fragment van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/analysis.md) voor meer details:

* [Structuurelboom](/help/sites-cloud/administering/content-fragments/analysis.md#structure-tree)

## GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s {#learn-graphql-with-aem-sample-content-queries}

Zie [&#x200B; Lerend om GraphQL met AEM te gebruiken - de Inhoud en Vragen van de Steekproef &#x200B;](/help/headless/graphql-api/sample-queries.md) voor een inleiding aan het gebruiken van AEM GraphQL API.

## Zelfstudie - Aan de slag met AEM Headless en GraphQL

Op zoek naar een praktische zelfstudie? Controle uit [&#x200B; Begonnen het Worden met de Hoofdloze AEM en GraphQL &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=nl-NL) leerprogramma van begin tot eind illustrerend hoe te om inhoud op te bouwen en bloot te stellen gebruikend GraphQL APIs van AEM en verbruikt door een externe app, in een headless scenario van CMS.
