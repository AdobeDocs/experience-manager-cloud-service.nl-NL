---
title: Levering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL
description: Leer de basisconcepten van het realiseren van een AEM CMS zonder kop met behulp van Content Fragments met GraphQL voor de levering van inhoud zonder kop.
feature: Content Fragments, GraphQL API
role: Developer, Architect
exl-id: 3aa7073a-6c6b-47b7-99d8-bba2d9a00af5
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '737'
ht-degree: 0%

---

# Levering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}

Met Content Fragments en de GraphQL API kunt u Adobe Experience Manager (AEM) as a Cloud Service gebruiken als een CMS (Headless Content Management System).

Dit wordt bereikt door gebruik te maken van Content Fragments, samen met de AEM GraphQL API (een aangepaste implementatie die is gebaseerd op standaard-GraphQL), voor het zonder problemen aanbieden van gestructureerde inhoud voor gebruik in uw toepassingen. Dankzij de mogelijkheid om één API-query aan te passen, kunt u de specifieke inhoud ophalen en leveren die u wilt/moet renderen (als antwoord op de enkele API-query).

>[!NOTE]
>
>Zie ook:
>
>* [Wat is Headless?](/help/headless/what-is-headless.md) voor een inleiding op de concepten en terminologie zonder koppen.
>
>* [Koploos en AEM](/help/headless/introduction.md) voor een inleiding op Headless Development voor AEM Sites as a Cloud Service.

>[!NOTE]
>
>GraphQL wordt momenteel gebruikt in twee (afzonderlijke) scenario&#39;s in Adobe Experience Manager (AEM) as a Cloud Service:
>
>* [AEM Commerce gebruikt gegevens van een handelsplatform via GraphQL](/help/commerce-cloud/integrating/magento.md).
>* [AEM Content Fragments werken samen met de AEM GraphQL API (een aangepaste implementatie, gebaseerd op standaard GraphQL) om gestructureerde inhoud te leveren voor gebruik in uw toepassingen](/help/headless/graphql-api/content-fragments.md).

## CMS zonder hoofd {#headless-cms}

Een CMS (Headless Content Management System) is een back-end alleen inhoudsbeheersysteem dat expliciet is ontworpen en gebouwd als een opslagplaats voor inhoud die inhoud toegankelijk maakt via een API, voor weergave op elk apparaat.

Wat het ontwerpen van inhoudsfragmenten in AEM betekent dit:

* U kunt Content Fragments gebruiken om inhoud te schrijven die niet in de eerste plaats bedoeld is om rechtstreeks (1:1) te worden gepubliceerd op opgemaakte pagina&#39;s.

* De inhoud van de inhoudsfragmenten wordt vooraf gestructureerd volgens de modellen van het inhoudsfragment. Hierdoor wordt de toegang voor uw toepassingen vereenvoudigd, waardoor uw inhoud verder wordt verwerkt.

## GraphQL - Een overzicht {#graphql-overview}

GraphQL is:

* &quot;*...een querytaal voor API&#39;s en een runtime voor het uitvoeren van deze query&#39;s met uw bestaande gegevens.*&quot;.

  Zie [GraphQL.org](https://graphql.org)

De [GRAPHQL API AEM](#aem-graphql-api) staat u toe om (complexe) vragen op uw uit te voeren [Inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md); met elke vraag die volgens een specifiek modeltype is. De geretourneerde inhoud kan vervolgens door uw toepassingen worden gebruikt.

## GRAPHQL API AEM {#aem-graphql-api}

Voor Adobe Experience as a Cloud Experience is een aangepaste implementatie van de standaard GraphQL API ontwikkeld. Zie [GraphQL API AEM voor gebruik met inhoudsfragmenten](/help/headless/graphql-api/content-fragments.md) voor meer informatie.

De AEM GraphQL API-implementatie is gebaseerd op de [GraphQL Java-bibliotheken](https://graphql.org/code/#java).

## Inhoudsfragmenten voor gebruik met de AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

[Inhoudsfragmenten](#content-fragments) kan als basis voor GraphQL voor AEM vragen worden gebruikt als:

* Hiermee kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren.
* De [Modellen van inhoudsfragmenten](#content-fragments-models) voorzien in de vereiste structuur door middel van gedefinieerde gegevenstypen.
* De [Fragmentverwijzing](#fragment-references), die beschikbaar zijn bij het definiëren van een model, kunnen worden gebruikt om extra structuurlagen te definiëren.

![Inhoudsfragmenten voor gebruik met GraphQL](assets/cf-contentdelivery-cf-use-with-graphql.png "Inhoudsfragmenten voor gebruik met GraphQL")

### Inhoudsfragmenten {#content-fragments}

Content Fragments:

* Bevat gestructureerde inhoud.

* Zij zijn gebaseerd op een [Inhoudsfragmentmodel](#content-fragments-models), waarin de structuur voor het resulterende fragment vooraf wordt gedefinieerd.

### Modellen van inhoudsfragmenten {#content-fragments-models}

Deze [Modellen van inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragment-models.md):

* worden gebruikt om de [Schemas](https://graphql.org/learn/schema/), eenmaal **Ingeschakeld**.

* Geef de gegevenstypen en velden op die vereist zijn voor GraphQL. Ze zorgen ervoor dat uw toepassing alleen vraagt wat mogelijk is en wat wordt verwacht ontvangt.

* Het gegevenstype **[Fragmentverwijzingen](#fragment-references)** U kunt in uw model worden gebruikt om naar een ander inhoudsfragment te verwijzen en zo extra structuurniveaus te introduceren.

### Fragmentverwijzingen {#fragment-references}

De **[Fragmentverwijzing](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#fragment-reference-nested-fragments)**:

* Is in samenwerking met GraphQL van bijzonder belang.

* Dit is een specifiek gegevenstype dat kan worden gebruikt bij het definiëren van een inhoudsfragmentmodel.

* Verwijst naar een ander fragment, afhankelijk van een specifiek inhoudsfragmentmodel.

* Hiermee kunt u gestructureerde gegevens ophalen.

   * Wanneer gedefinieerd als een **multifeed** Er kan door het primaire fragment naar meerdere subfragmenten worden verwezen (opgehaald).

## Structuur van inhoudsfragment analyseren {#analyzing-content-fragments-structure}

AEM biedt verschillende methoden om de structuur van uw fragmenten vanuit de [Inhoudsfragmenteditor](/help/sites-cloud/administering/content-fragments/authoring.md).

Zie [Structuur van inhoudsfragment analyseren](/help/sites-cloud/administering/content-fragments/analysis.md) voor meer informatie :

* [Structuurelboom](/help/sites-cloud/administering/content-fragments/analysis.md#structure-tree)

## GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s {#learn-graphql-with-aem-sample-content-queries}

Zie [GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s](/help/headless/graphql-api/sample-queries.md) voor een inleiding op het gebruik van de AEM GraphQL API.

## Zelfstudie - Aan de slag met AEM Headless en GraphQL

Op zoek naar een praktische zelfstudie? Uitchecken [Aan de slag met AEM Headless en GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) end-to-end zelfstudie waarin wordt geïllustreerd hoe u in een CMS-scenario inhoud kunt ontwikkelen en beschikbaar maken met de GraphQL-API&#39;s van AEM en die door een externe toepassing wordt verbruikt.
