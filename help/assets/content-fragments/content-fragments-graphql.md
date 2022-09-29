---
title: Aflevering van inhoud zonder kop met behulp van inhoudsfragmenten met GraphQL (elementen - inhoudsfragmenten)
description: Leer de basisconcepten van het realiseren van een AEM CMS zonder kop die Inhoudsfragmenten met GraphQL gebruiken voor de levering van inhoud zonder kop.
feature: Content Fragments, GraphQL API
exl-id: 4a3b030d-ed59-4920-bf94-e00a45f85b51
source-git-commit: 944665bc7cac1f00811187a508a18800c3d73f2a
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# Aflevering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}

Met Inhoudsfragmenten en de GraphQL API kunt u Adobe Experience Manager (AEM) as a Cloud Service gebruiken als een CMS (Headless Content Management System).

Dit wordt bereikt gebruikend de Fragments van de Inhoud, samen met AEM GraphQL API (een aangepaste implementatie, die op standaard GraphQL wordt gebaseerd), om gestructureerde inhoud voor gebruik in uw toepassingen zonder uitzondering te leveren. Dankzij de mogelijkheid om één API-query aan te passen, kunt u de specifieke inhoud ophalen en leveren die u wilt/moet renderen (als antwoord op de enkele API-query).

>[!NOTE]
>
>Zie ook:
>
>* [Wat is Headless?](/help/headless/what-is-headless.md) voor een inleiding op de concepten en terminologie zonder koppen.
>
>* [Koploos en AEM](/help/headless/introduction.md) voor een inleiding op Headless Development voor AEM Sites as a Cloud Service.


>[!NOTE]
>
>GraphQL wordt momenteel gebruikt in twee (afzonderlijke) scenario&#39;s in as a Cloud Service Adobe Experience Manager (AEM):
>
>* [AEM Handel verbruikt gegevens van een handelsplatform via GraphQL](/help/commerce-cloud/integrating/magento.md).
>* [AEM de Fragmenten van de Inhoud werken samen met AEM GraphQL API (een aangepaste implementatie, die op standaard GraphQL wordt gebaseerd), om gestructureerde inhoud voor gebruik in uw toepassingen te leveren](/help/headless/graphql-api/content-fragments.md).


## CMS zonder hoofd {#headless-cms}

Een CMS (Headless Content Management System) is een back-end alleen inhoudsbeheersysteem dat expliciet is ontworpen en gebouwd als een opslagplaats voor inhoud die inhoud toegankelijk maakt via een API, voor weergave op elk apparaat.

Wat het ontwerpen van inhoudsfragmenten in AEM betekent dit:

* U kunt Content Fragments gebruiken om inhoud te schrijven die niet in de eerste plaats bedoeld is om rechtstreeks (1:1) te worden gepubliceerd op opgemaakte pagina&#39;s.

* De inhoud van de inhoudsfragmenten wordt vooraf gestructureerd volgens de modellen van het inhoudsfragment. Hierdoor wordt de toegang voor uw toepassingen vereenvoudigd, waardoor uw inhoud verder wordt verwerkt.

## GraphQL - een overzicht {#graphql-overview}

GraphQL is:

* &quot;*...een querytaal voor API&#39;s en een runtime voor het uitvoeren van deze query&#39;s met uw bestaande gegevens.*&quot;.

   Zie [GraphQL.org](https://graphql.org)

De [AEM GraphQL API](#aem-graphql-api) staat u toe om (complexe) vragen op uw uit te voeren [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md); met elke vraag die volgens een specifiek modeltype is. De geretourneerde inhoud kan vervolgens door uw toepassingen worden gebruikt.

## AEM GraphQL API {#aem-graphql-api}

Voor Adobe Experience as a Cloud Experience is een aangepaste implementatie van de standaard GraphQL API ontwikkeld. Zie [AEM GraphQL API voor gebruik met Content Fragments](/help/headless/graphql-api/content-fragments.md) voor meer informatie.

De AEM GraphQL API-implementatie is gebaseerd op de [GraphQL Java-bibliotheken](https://graphql.org/code/#java).

## Inhoudsfragmenten voor gebruik met de AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

[Inhoudsfragmenten](#content-fragments) kan als basis voor GraphQL voor AEM vragen als worden gebruikt:

* Hiermee kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren.
* De [Modellen van inhoudsfragmenten](#content-fragments-models) voorzien in de vereiste structuur door middel van gedefinieerde gegevenstypen.
* De [Fragmentverwijzing](#fragment-references), die beschikbaar zijn bij het definiëren van een model, kunnen worden gebruikt om extra structuurlagen te definiëren.

![Inhoudsfragmenten voor gebruik met GraphQL](assets/cfm-nested-01.png "Inhoudsfragmenten voor gebruik met GraphQL")

### Contentfragmenten {#content-fragments}

Contentfragmenten:

* Bevat gestructureerde inhoud.

* Zij zijn gebaseerd op een [Inhoudsfragmentmodel](#content-fragments-models), waarin de structuur voor het resulterende fragment vooraf wordt gedefinieerd.

### Modellen van contentfragmenten {#content-fragments-models}

Deze [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md):

* worden gebruikt om de [Schemas](https://graphql.org/learn/schema/), eenmaal **Ingeschakeld**.

* Geef de gegevenstypen en velden op die vereist zijn voor GraphQL. Ze zorgen ervoor dat uw toepassing alleen vraagt wat mogelijk is en wat wordt verwacht ontvangt.

* Het gegevenstype **[Fragmentverwijzingen](#fragment-references)** U kunt in uw model worden gebruikt om naar een ander inhoudsfragment te verwijzen en zo extra structuurniveaus te introduceren.

### Fragmentverwijzingen {#fragment-references}

De **[Fragmentverwijzing](/help/assets/content-fragments/content-fragments-models.md#fragment-reference-nested-fragments)**:

* Is van bijzonder belang in samenhang met GraphQL.

* Dit is een specifiek gegevenstype dat kan worden gebruikt bij het definiëren van een inhoudsfragmentmodel.

* Verwijst naar een ander fragment, afhankelijk van een specifiek inhoudsfragmentmodel.

* Hiermee kunt u gestructureerde gegevens ophalen.

   * Wanneer gedefinieerd als een **multifeed** Er kan door het primaire fragment naar meerdere subfragmenten worden verwezen (opgehaald).

### JSON-voorvertoning {#json-preview}

Om u te helpen bij het ontwerpen en ontwikkelen van uw modellen van inhoudsfragmenten, kunt u een voorvertoning weergeven [JSON-uitvoer](/help/assets/content-fragments/content-fragments-json-preview.md).

## Leren gebruiken GraphQL met AEM - Voorbeeldinhoud en query&#39;s {#learn-graphql-with-aem-sample-content-queries}

Zie [Leren gebruiken GraphQL met AEM - Voorbeeldinhoud en query&#39;s](/help/headless/graphql-api/sample-queries.md) voor een inleiding aan het gebruiken van AEM GraphQL API.

## Zelfstudie - Aan de slag met AEM headless and GraphQL

Op zoek naar een praktische zelfstudie? Uitchecken [Aan de slag met AEM headless en GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) end-to-end zelfstudie waarin wordt geïllustreerd hoe u in een CMS-scenario inhoud kunt samenstellen en beschikbaar maken met behulp van AEM GraphQL-API&#39;s en die door een externe toepassing wordt verbruikt.
