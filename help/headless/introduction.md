---
title: Inleiding tot AEM zonder kop
description: Meer informatie over Adobe Experience Manager (AEM) als een headless CMS met een combinatie van gedetailleerde documentatie en ritten zonder kop. Leer hoe u functies als Content Models, Content Fragments en een GraphQL-API kunt gebruiken om een headless-ervaring in te schakelen.
landing-page-description: Begrijp hoe u Experience Manager zonder hoofd as a Cloud Service kunt gebruiken en toedienen.
exl-id: 24300499-ae9c-49d0-aa25-f51e14d9cf79
source-git-commit: 30272a4729bc2e2b5213796789eb1422ba105074
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 0%

---


# Inleiding tot Adobe Experience Manager als een headless CMS {#introduction-aem-headless}

Leer hoe u Adobe Experience Manager (AEM) gebruikt als een headless CMS met functies zoals Content Models, Content Fragments en een GraphQL API die ervoor zorgen dat headless ervaringen op schaal worden uitgevoerd.

U kunt gedetailleerde documentatie van de verschillende betrokken eigenschappen lezen en/of de selectie volgen [Headless Reizen voor een overzicht van de eerste stappen](#first-steps).

## Overzicht {#overview}

AEM Headless is een CMS-oplossing van Experience Manager waarmee gestructureerde inhoud (Content Fragments) in AEM kan worden verbruikt door een toepassing via HTTP met behulp van GraphQL. Met een headless-implementatie kunt u ervaringen op verschillende platforms en kanalen op schaal aanbieden.

Bij implementatie zonder kop gaan pagina- en componentbeheer verloren, zoals gebruikelijk is in oplossingen voor volledige stapels en hybride oplossingen, en wordt de nadruk gelegd op het maken van kanaalneutrale, herbruikbare fragmenten van inhoud en hun levering over het kanaal. Het is een modern en dynamisch ontwikkelingspatroon voor het implementeren van webervaringen.

![Implementatiemodellen AEM](assets/aem-implementation-models.png)

## Functies van AEM zonder kop {#aem-headless-features}

AEM as a Cloud Service is een flexibel hulpmiddel voor het implementatiemodel zonder kop door drie krachtige functies te bieden:

1. **Inhoudsmodellen**
   * Inhoudsmodellen zijn een gestructureerde weergave van inhoud.
   * Inhoudsmodellen worden gedefinieerd door informatiearchitecten in de AEM Content Fragment Model-editor.
   * Inhoudsmodellen dienen als basis voor inhoudsfragmenten.
1. **Contentfragmenten**
   * Inhoudsfragmenten worden gemaakt op basis van een inhoudsmodel.
   * Gemaakt door auteurs van inhoud met de AEM Content Fragment-editor.
   * Inhoudsfragmenten worden opgeslagen in AEM Assets en beheerd in de interface voor middelenbeheer.
1. **Inhoud-API voor levering**
   * De AEM GraphQL API ondersteunt de levering van contentfragmenten.
   * De AEM Assets REST-API ondersteunt CRUD-bewerkingen voor inhoudsfragmenten.
   * Directe levering van inhoud is ook mogelijk met de [JSON-export van de Content Fragment Core-component](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html).

## Uw eerste stappen met AEM zonder kop {#first-steps}

Er zijn verschillende bronnen beschikbaar om aan de slag te gaan met AEM functies zonder kop. Elke hulplijn is op maat gemaakt voor verschillende gebruiksgevallen en verschillende soorten publiek.

| Resource | Beschrijving | Type | Publiek | Oost. Time |
|---|---|---|---|---|
| [Headless Developer Journey](/help/journey-headless/developer/overview.md) | **Voor nieuwe ontwikkelaars AEM en zonder kop** technologieën, begin hier voor een uitvoerige inleiding aan AEM en zijn headless eigenschappen van de theorie van headless door met uw eerste hoofdloze project te leven. | Hulplijn | Ontwikkelaars **nieuw tot AEM en zonder kop** | 1 uur |
| [Installatie zonder koppen](/help/headless/setup/introduction.md) | **Voor ervaren AEM** Voor een kort overzicht van de belangrijkste functies voor het AEM zonder kop, bekijkt u dit snelstartoverzicht. | Referentie-instelling | Ontwikkelaars, beheerders **met AEM ervaring** | 20 minuten |
| [Zelfstudie over headless hands-on](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) | **Als u een hands-on benadering verkiest en met AEM vertrouwd bent** Deze zelfstudie leidt rechtstreeks tot de implementatie van een eenvoudige app zonder koppen. | Zelfstudie | Ontwikkelaars | 2 uur |
| [Architect zonder hoofd](/help/journey-headless/architect/overview.md) | **Voor architecten die nieuw zijn voor AEM en zonder kop** -technologieën, begint hier voor een introductie van de krachtige, flexibele, eindeloze functies van Adobe Experience Manager as a Cloud Service en hoe u inhoud voor uw project kunt modelleren. | Hulplijn | Architecten | 1 uur |
| [Papierreis zonder koppen](/help/journey-headless/author/overview.md) | **Voor zakelijke gebruikers die nog niet AEM en zonder kop** -technologieën, begint hier voor een introductie van de krachtige, flexibele, eindeloze functies van Adobe Experience Manager as a Cloud Service en hoe u inhoud voor uw project kunt modelleren. | Hulplijn | Inhoudsmakers | 1 uur |
| [Dagboekreis zonder hoofd](/help/journey-headless/translation/overview.md) | Voor die **geïnteresseerd in AEM vertaalbenadering van krantenkoppen**. Leer over headless technologieën en hoe te om vertaalprojecten in AEM van A tot Z te creëren en bij te werken. | Hulplijn | Vertaalspecialisten | 1 uur |

## Bezig met vergelijken van hoofdletters en hoofdletters {#headful-headless}

Deze handleiding is gericht op het volledige implementatiemodel zonder kop van AEM. Nochtans moet de macht tegenover de zonder kop geen binaire keus in AEM zijn. U kunt headless-functies gebruiken om inhoud te beheren en aan meerdere aanraakpunten te leveren, en tegelijkertijd inhoudsauteurs de mogelijkheid bieden om toepassingen van één pagina te bewerken. Alles in AEM.

>[!TIP]
>
>Zie het document [Hoofdletters en headless in AEM](/help/implementing/developing/headful-headless.md) voor meer informatie .