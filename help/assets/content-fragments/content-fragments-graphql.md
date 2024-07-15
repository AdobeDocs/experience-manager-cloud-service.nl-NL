---
title: Aflevering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL (Assets - Inhoudsfragmenten)
description: Leer de basisconcepten van het realiseren van een AEM CMS zonder kop met behulp van Content Fragments met GraphQL voor de levering van inhoud zonder kop.
feature: Content Fragments
exl-id: 4a3b030d-ed59-4920-bf94-e00a45f85b51
role: User
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---

# Levering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}

Met Content Fragments en de GraphQL API kunt u Adobe Experience Manager (AEM) as a Cloud Service gebruiken als een CMS (Headless Content Management System).

Dit wordt bereikt door gebruik te maken van Content Fragments, samen met de AEM GraphQL API (een aangepaste implementatie die is gebaseerd op standaard-GraphQL), voor het zonder problemen aanbieden van gestructureerde inhoud voor gebruik in uw toepassingen. Met de mogelijkheid om één API-query aan te passen kunt u de specifieke inhoud ophalen en leveren die u wilt/moet renderen (als antwoord op de enkele API-query).

>[!NOTE]
>
>Zie ook:
>
>* [ wat is Headless?](/help/headless/what-is-headless.md) voor een inleiding aan de concepten en de terminologie zonder kop.
>
>* [ Zwaartepunt en AEM ](/help/headless/introduction.md) voor een inleiding aan Zwaardeloze Ontwikkeling voor AEM Sites as a Cloud Service.

>[!NOTE]
>
>GraphQL wordt momenteel gebruikt in twee (afzonderlijke) scenario&#39;s in Adobe Experience Manager (AEM) as a Cloud Service:
>
>* [ AEM Commerce verbruikt gegevens van een handelsplatform via GraphQL ](/help/commerce-cloud/integrating/magento.md).
>* [ AEM de Fragmenten van de Inhoud werken samen met AEM GraphQL API (een aangepaste implementatie, die op standaardGraphQL wordt gebaseerd), om gestructureerde inhoud voor gebruik in uw toepassingen ](/help/headless/graphql-api/content-fragments.md) te leveren.

## CMS zonder hoofd {#headless-cms}

Een CMS (Headless Content Management System) is een back-end alleen inhoudsbeheersysteem dat expliciet is ontworpen en gebouwd als een opslagplaats voor inhoud die inhoud toegankelijk maakt via een API, voor weergave op elk apparaat.

Wat het ontwerpen van inhoudsfragmenten in AEM betekent dit:

* U kunt Content Fragments gebruiken om inhoud te schrijven die niet in de eerste plaats bedoeld is om rechtstreeks (1:1) te worden gepubliceerd op opgemaakte pagina&#39;s.

* De inhoud van de inhoudsfragmenten wordt vooraf gestructureerd volgens de modellen van het inhoudsfragment. Hierdoor wordt de toegang voor uw toepassingen vereenvoudigd, waardoor uw inhoud verder wordt verwerkt.

## GraphQL - Een overzicht {#graphql-overview}

GraphQL is:

* &quot;*...een vraagtaal voor APIs en runtime voor het vervullen van die vragen met uw bestaande gegevens.*&quot;.

  Zie [ GraphQL.org ](https://graphql.org)

[ AEM GraphQL API ](#aem-graphql-api) laat u (complexe) vragen op uw [ Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments.md) uitvoeren; met elke vraag die volgens een specifiek modeltype is. De geretourneerde inhoud kan vervolgens door uw toepassingen worden gebruikt.

## GRAPHQL API AEM {#aem-graphql-api}

Voor Adobe Experience as a Cloud Experience is een aangepaste implementatie van de standaard GraphQL API ontwikkeld. Zie [ AEM GraphQL API voor gebruik met de Fragmenten van de Inhoud ](/help/headless/graphql-api/content-fragments.md) voor details.

De AEM implementatie van GraphQL API is gebaseerd op de [ bibliotheken van GraphQL Java ](https://graphql.org/code/#java).

## Inhoudsfragmenten voor gebruik met de AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

[ de Fragmenten van de Inhoud ](#content-fragments) kunnen als basis voor GraphQL voor AEM vragen als worden gebruikt:

* Hiermee kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren.
* De [ Modellen van het Fragment van de Inhoud ](#content-fragments-models) verstrekken de vereiste structuur door middel van bepaalde gegevenstypes.
* De [ Verwijzing van het Fragment ](#fragment-references), beschikbaar wanneer het bepalen van een model, kan worden gebruikt om extra lagen van structuur te bepalen.

![ de Fragmenten van de Inhoud voor gebruik met de Fragmenten van de Inhoud van GraphQL ](assets/cfm-nested-01.png " voor gebruik met GraphQL ")

### Inhoudsfragmenten {#content-fragments}

Content Fragments:

* Bevat gestructureerde inhoud.

* Zij zijn gebaseerd op het Model van het Fragment van de a [ Inhoud ](#content-fragments-models), dat de structuur voor het resulterende fragment vooraf bepaalt.

### Modellen van inhoudsfragmenten {#content-fragments-models}

Deze [ Modellen van het Fragment van Inhoud ](/help/assets/content-fragments/content-fragments-models.md):

* Wordt gebruikt om de [ Schema&#39;s ](https://graphql.org/learn/schema/) te produceren, eens **Toegelaten**.

* Geef de gegevenstypen en velden op die vereist zijn voor GraphQL. Ze zorgen ervoor dat uw toepassing alleen vraagt wat mogelijk is en wat wordt verwacht ontvangt.

* Het gegevenstype **[Verwijzingen van het Fragment](#fragment-references)** kan in uw model worden gebruikt om een ander Fragment van de Inhoud van verwijzingen te voorzien, en zo extra niveaus van structuur introduceren.

### Fragmentverwijzingen {#fragment-references}

De **[Verwijzing van het Fragment](/help/assets/content-fragments/content-fragments-models.md#fragment-reference-nested-fragments)**:

* Is in samenwerking met GraphQL van bijzonder belang.

* Dit is een specifiek gegevenstype dat kan worden gebruikt bij het definiëren van een inhoudsfragmentmodel.

* Verwijst naar een ander fragment, afhankelijk van een specifiek inhoudsfragmentmodel.

* Hiermee kunt u gestructureerde gegevens ophalen.

   * Wanneer bepaald als a **multifeed**, kunnen de veelvoudige sub-fragmenten (teruggewonnen) door het eerste fragment van verwijzingen worden voorzien.

### JSON-voorvertoning {#json-preview}

Om met het ontwerpen van en het ontwikkelen van uw Modellen van het Fragment van de Inhoud te helpen, kunt u voorproef [ output JSON ](/help/assets/content-fragments/content-fragments-json-preview.md).

## GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s {#learn-graphql-with-aem-sample-content-queries}

Zie [ Lerend om GraphQL met AEM te gebruiken - de Inhoud en Vragen van de Steekproef ](/help/headless/graphql-api/sample-queries.md) voor een inleiding aan het gebruiken van AEM GraphQL API.

## Zelfstudie - Aan de slag met AEM Headless en GraphQL

Op zoek naar een praktische zelfstudie? Controle uit [ Begonnen het Worden met AEM Zwaartepunt en GraphQL ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) leerprogramma van begin tot eind illustrerend hoe te om inhoud op te bouwen en bloot te stellen gebruikend AEM GraphQL APIs en verbruikt door een externe app, in een hoofdCMS scenario.
