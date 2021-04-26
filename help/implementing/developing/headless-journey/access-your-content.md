---
title: Hoe te om tot Uw Inhoud via AEM levering APIs toegang te hebben
description: In dit deel van de AEM Headless Ontwikkelaarsreis, leer hoe te om vragen te gebruiken GraphQL om tot uw inhoud van de Fragmenten van de Inhoud toegang te hebben.
hide: true
hidefromtoc: true
index: false
translation-type: tm+mt
source-git-commit: d17583399b6792583e3e210005b62d360b91d05a
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 2%

---


# Hoe te om tot Uw Inhoud via AEM levering APIs {#access-your-content} toegang te hebben

>[!CAUTION]
>
>WERK IN VOORTGANG - De opstelling van dit document is aan de gang en mag niet worden opgevat als volledig of definitief en mag niet worden gebruikt voor productiedoeleinden.

In dit deel van [AEM Koploze Reis van de Ontwikkelaar,](#overview.md) leren hoe te om vragen te gebruiken GraphQL om tot de inhoud van uw Fragments van de Inhoud toegang te hebben.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM headless reis, [How to Model Your Content](model-your-content.md) leerde u de grondbeginselen van gegevensmodellering in AEM en u zou nu moeten:

* Belangrijke planningsoverwegingen voor het ontwerpen van uw inhoud begrijpen.
* Begrijp de stappen om hoofdloos uit te voeren afhankelijk van uw vereisten van het integratieniveau.
* Stel de benodigde gereedschappen en AEM configuraties in.
* Weet de beste praktijken om uw reis zonder kop vlot te maken, efficiënt inhoudsgeneratie te houden, en ervoor te zorgen dat de inhoud snel wordt geleverd.

Dit artikel bouwt verder op deze basisbeginselen, zodat u begrijpt hoe u toegang krijgt tot uw bestaande inhoud zonder kop in AEM via API.

* **Publiek**: Begin
* **Doel**: Leer hoe te om tot de inhoud van uw Fragmenten van de Inhoud toegang te hebben gebruikend AEM vragen GraphQL:
   * Introduceer GraphQL.
   * Introduceer AEM GraphQL API.
   * Dive in de details van AEM GraphQL API.
   * Bekijk sommige steekproefvragen om te zien hoe de dingen in praktijk werken.

Met Adobe Experience Manager (AEM) als Cloud Service, kunt u de Fragments van de Inhoud, samen met AEM GraphQL API, gebruiken om gestructureerde inhoud voor gebruik in uw toepassingen zonder problemen te leveren. Dankzij de mogelijkheid om één API-query aan te passen, kunt u de specifieke inhoud ophalen en leveren die u wilt/moet renderen (als antwoord op de enkele API-query).

>[!NOTE]
>AEM GraphQL API is een aangepaste implementatie, gebaseerd op standaard GraphQL.

## GraphQL - Een inleiding {#graphql-introduction}

GraphQL is:

* &quot;*..een vraagtaal voor APIs en runtime voor het vervullen van die vragen met uw bestaande gegevens.*&quot;.

   Zie *GraphQL*.

### GraphQL - Typen {#graphql-types}

### GraphQL - Schemas {#graphql-schemas}

### GraphQL - Vragen {#graphql-queries}

## AEM en GraphQL {#aem-graphql}

GraphQL wordt gebruikt in diverse plaatsen in AEM:

* Handel
   * Plaatsaanduiding
* Contentfragmenten
   * Er is een aangepaste API ontwikkeld voor dit geval van gebruik.
   * Dit is de AEM GraphQL API.

## AEM GraphQL API {#aem-graphql-api}

Voor Adobe Experience as a Cloud Experience is een aangepaste implementatie van de standaard GraphQL API ontwikkeld.

Met de AEM GraphQL API kunt u (complexe) query&#39;s uitvoeren op uw inhoudsfragmenten; met elke vraag die volgens een specifiek modeltype is. De geretourneerde inhoud kan vervolgens door uw toepassingen worden gebruikt.

>[!NOTE]
>
>De implementatie van AEM GraphQL API is gebaseerd op de Java-bibliotheken GraphQL.

### AEM GraphQL API- en inhoudsfragmenten {#aem-graphql-content-fragments}

## Inhoudsfragmenten voor gebruik met de AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

De Fragments van de inhoud kunnen als basis voor GraphQL voor AEM vragen als worden gebruikt:

* Hiermee kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren.
* De modellen van het Fragment van de Inhoud verstrekken de vereiste structuur door middel van bepaalde gegevenstypes.
* De fragmentverwijzing, die beschikbaar is wanneer u een model definieert, kan worden gebruikt om extra structuurlagen te definiëren.

### Contentfragmenten {#content-fragments}

Contentfragmenten:

* Bevat gestructureerde inhoud.

* Ze zijn gebaseerd op een Content Fragment Model, dat de structuur voor het resulterende fragment vooraf definieert.

### Modellen van contentfragmenten {#content-fragments-models}

Deze modellen van inhoudsfragmenten:

* Wordt gebruikt om de Schema&#39;s te produceren, eens **Enabled**.

* Geef de gegevenstypen en velden op die vereist zijn voor GraphQL. Ze zorgen ervoor dat uw toepassing alleen vraagt wat mogelijk is en wat wordt verwacht ontvangt.

* Het gegevenstype **Fragmentverwijzingen** kan in uw model worden gebruikt om naar een ander Inhoudsfragment te verwijzen, en zo extra niveaus van structuur introduceren.

### Fragmentverwijzingen {#fragment-references}

De **Fragmentverwijzing**:

* Is van bijzonder belang in samenhang met GraphQL.

* Dit is een specifiek gegevenstype dat kan worden gebruikt bij het definiëren van een inhoudsfragmentmodel.

* Verwijst naar een ander fragment, afhankelijk van een specifiek inhoudsfragmentmodel.

* Hiermee kunt u gestructureerde gegevens ophalen.

   * Wanneer gedefinieerd als een **multifeed**, kunnen meerdere subfragmenten door het prime-fragment naar verwezen (opgehaald) worden.

### JSON-voorvertoning {#json-preview}

Om u te helpen bij het ontwerpen en ontwikkelen van uw modellen van inhoudsfragmenten, kunt u een voorvertoning van [JSON-uitvoer](/help/assets/content-fragments/content-fragments-json-preview.md) weergeven.

## Volgende {#whats-next}

[Leer hoe u de REST API kunt gebruiken om de inhoud van de inhoudsfragmenten](/help/implementing/developing/headless-journey/update-your-content.md) te openen en bij te werken.

## Aanvullende bronnen {#additional-resources}

* [Aan de slag met AEM Headless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html)  - Een korte videozelfstudie die een overzicht biedt van het gebruik van AEM functies zonder kop, zoals gegevensmodellering en GraphQL
* [GraphQL.org](https://graphql.org)
   * [Schemas](https://graphql.org/learn/schema/)
   * [GraphQL Java-bibliotheken](https://graphql.org/code/#java)
* [AEM GraphQL API voor gebruik met Content Fragments](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * [Leren gebruiken GraphQL met AEM - Voorbeeldinhoud en query&#39;s](/help/assets/content-fragments/content-fragments-graphql-samples.md)
   * [Verificatie voor externe AEM GraphQL-query&#39;s op inhoudsfragmenten](/help/assets/content-fragments/graphql-authentication-content-fragments.md)
* [Werken met contentfragmenten](/help/assets/content-fragments/content-fragments.md)
   * [Modellen van contentfragmenten](/help/assets/content-fragments/content-fragments-models.md)
   * [JSON-uitvoer](/help/assets/content-fragments/content-fragments-json-preview.md)
