---
title: Aflevering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL
description: Leer hoe te om de Fragments van de Inhoud in Adobe Experience Manager (AEM) als Cloud Service met GraphQL voor Hoofdloze Levering van Inhoud te gebruiken.
translation-type: tm+mt
source-git-commit: da8fcf1288482d406657876b5d4c00b413461b21
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 0%

---


# Aflevering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}

>[!CAUTION]
>
>De AEM GraphQL API voor de Levering van Inhoudsfragmenten is op verzoek beschikbaar.
>
>Neem contact op met [Adobe Support](https://experienceleague.adobe.com/?lang=en&amp;support-solution=General#support) om de API voor uw AEM in te schakelen als een programma voor Cloud Servicen.

Met Adobe Experience Manager (AEM) als Cloud Service, kunt u de Fragments van de Inhoud, samen met AEM GraphQL API (een aangepaste implementatie, die op standaard GraphQL wordt gebaseerd), gebruiken om gestructureerde inhoud voor gebruik in uw toepassingen te leveren.

## CMS zonder koppen {#headless-cms}

Een CMS (Headless Content Management System) is:

* &quot;*Een systeem voor inhoudsbeheer zonder kop, of CMS zonder kop, is een back-end alleen inhoudsbeheersysteem (CMS) dat vanaf de basis is opgebouwd als een inhoudsopslagplaats die inhoud toegankelijk maakt via een API voor weergave op elk apparaat.*

   *De term &quot;headless&quot; komt uit het concept van het afknippen van de &quot;head&quot; (de front-end, d.w.z. de website) van de &quot;body&quot; (de back-end, d.w.z. de content repository).*&quot;

   Zie [Wikipedia](https://en.wikipedia.org/wiki/Headless_content_management_system).

Wat het ontwerpen van inhoudsfragmenten in AEM betekent dit:

* U kunt Content Fragments gebruiken om inhoud te schrijven die niet in de eerste plaats bedoeld is om rechtstreeks (1:1) te worden gepubliceerd op opgemaakte pagina&#39;s.

* De inhoud van de inhoudsfragmenten wordt vooraf gestructureerd volgens de modellen van het inhoudsfragment. Hierdoor wordt de toegang voor uw toepassingen vereenvoudigd, waardoor uw inhoud verder wordt verwerkt.

>[!NOTE]
>
>Zie [Headless and AEM](/help/implementing/developing/headless/introduction.md) voor een inleiding tot Headless Development voor AEM Sites als Cloud Service.

## GraphQL - een overzicht {#graphql-overview}

GraphQL is:

* &quot;*..een querytaal voor API&#39;s en een runtime voor het uitvoeren van deze query&#39;s met uw bestaande gegevens. GraphQL verstrekt een volledige en begrijpelijke beschrijving van de gegevens in uw API, geeft cliënten de macht om precies te vragen wat zij en niets meer nodig hebben, maakt het gemakkelijker om APIs in tijd te evolueren, en laat krachtige ontwikkelaarshulpmiddelen toe.*&quot;.

   Zie [GraphQL.org](https://graphql.org)

* &quot;*..een open specificatie voor een flexibele API-laag. GrafiekQL op uw bestaande achtergronden plaatsen om producten sneller dan ooit te bouwen....*&quot;.

   Zie [GraphQL](https://www.graphql.com) verkennen. &quot;*Explore GraphQL wordt gehandhaafd door het team van Apollo. Ons doel is om ontwikkelaars en technische leiders over de hele wereld alle instrumenten te geven die zij nodig hebben om GraphQL.* te begrijpen en aan te nemen.&quot;

Met de [AEM GraphQL API](#aem-graphql-api) kunt u (complexe) query&#39;s uitvoeren op uw [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md); met elke vraag die volgens een specifiek modeltype is. De geretourneerde inhoud kan vervolgens door uw toepassingen worden gebruikt.

### GraphQL-terminologie {#graphql-terminology}

GraphQL gebruikt het volgende:

* **[Zoekopdrachten](https://graphql.org/learn/queries/)**

* **[De schema&#39;s en de Types](https://graphql.org/learn/schema/)**  - gebruikend deze, GraphQL presenteert de types en de verrichtingen die voor GraphQL voor AEM implementatie worden toegestaan.

* **[Velden](https://graphql.org/learn/queries/#fields)**

* **Het Eindpunt**  GraphQL - de weg in AEM die aan vragen GraphQL antwoordt, en toegang tot de schema&#39;s GraphQL verleent.

Zie [ (GraphQL.org) Inleiding aan GraphQL](https://graphql.org/learn/) voor uitvoerige details, met inbegrip van [Beste praktijken](https://graphql.org/learn/best-practices/).

### GraphQL-querytypen {#graphql-query-types}

Met GraphQL kunt u vragen voor of uitvoeren:

* **Eén item**

* **[Lijst van vermeldingen](https://graphql.org/learn/schema/#lists-and-non-null)**

## AEM GraphQL API {#aem-graphql-api}

Voor [Adobe Experience as a Cloud Experience is een aangepaste implementatie van de standaard GraphQL API](/help/assets/content-fragments/graphql-api-content-fragments.md) geïmplementeerd.

De implementatie van AEM GraphQL API is gebaseerd op de [GraphQL Java-bibliotheken](https://graphql.org/code/#java).

## Inhoudsfragmenten voor gebruik met de AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

[Inhoud ](#content-fragments) Fragmenteren kan als basis voor GraphQL voor AEM vragen worden gebruikt als:

* Hiermee kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren.
* De [Content Fragment Models](#content-fragments-models) bieden de vereiste structuur door middel van gedefinieerde gegevenstypen.
* De [Fragmentverwijzing](#fragment-references), die beschikbaar is wanneer u een model definieert, kan worden gebruikt om extra structuurlagen te definiëren.

![Inhoudsfragmenten voor gebruik met ](assets/cfm-nested-01.png "GraphQLContent-fragmenten voor gebruik met GraphQL")

### Contentfragmenten {#content-fragments}

Contentfragmenten:

* Bevat gestructureerde inhoud.

* Ze zijn gebaseerd op een [Inhoudsfragmentmodel](#content-fragments-models), dat de structuur voor het resulterende fragment vooraf definieert.

### Modellen van contentfragmenten {#content-fragments-models}

Deze [Content Fragment Models](/help/assets/content-fragments/content-fragments-models.md):

* Geef de gegevenstypen en velden op die vereist zijn voor GraphQL. Ze zorgen ervoor dat uw toepassing alleen vraagt wat mogelijk is en wat wordt verwacht ontvangt.

* Het gegevenstype **[Fragmentverwijzingen](#fragment-references)** kan in uw model worden gebruikt om naar een ander Inhoudsfragment te verwijzen, en zo extra niveaus van structuur introduceren.

### Fragmentverwijzingen {#fragment-references}

De **[Fragmentverwijzing](/help/assets/content-fragments/content-fragments-models.md#fragment-reference-nested-fragments)**:

* Is van bijzonder belang in samenhang met GraphQL.

* Dit is een specifiek gegevenstype dat kan worden gebruikt bij het definiëren van een inhoudsfragmentmodel.

* Verwijst naar een ander fragment, afhankelijk van een specifiek inhoudsfragmentmodel.

* Hiermee kunt u gestructureerde gegevens ophalen.

   * Wanneer gedefinieerd als een **multifeed**, kunnen meerdere subfragmenten door het prime-fragment naar verwezen (opgehaald) worden.

### JSON-voorvertoning {#json-preview}

Om u te helpen bij het ontwerpen en ontwikkelen van de Content Fragment Modesl, kunt u een voorvertoning van [JSON-uitvoer](/help/assets/content-fragments/content-fragments-json-preview.md) weergeven.

## Leren gebruiken GraphQL met AEM - Voorbeeldinhoud en query&#39;s {#learn-graphql-with-aem-sample-content-queries}

Zie [Leren om GraphQL met AEM te gebruiken - de Inhoud van de Steekproef en Vragen](/help/assets/content-fragments/content-fragments-graphql-samples.md) voor een inleiding aan het gebruiken van AEM GraphQL API.

## Zelfstudie - Aan de slag met AEM headless and GraphQL

Op zoek naar een praktische zelfstudie? Ontdek [Aan de slag met AEM Headless en GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) de zelfstudie van begin tot eind waarin wordt geïllustreerd hoe u in een CMS-scenario inhoud kunt ontwikkelen en beschikbaar maken met de GraphQL-API&#39;s van AEM en die door een externe toepassing wordt verbruikt.