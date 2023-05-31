---
title: Inleiding tot headless voor AEM
description: Meer informatie over Headless in Adobe Experience Manager (AEM) met een combinatie van gedetailleerde documentatie en headless reizen. Ontdek hoe functies zoals Content Fragment Models, Content Fragments en een GraphQL API worden gebruikt om headless-ervaringen mogelijk te maken.
landing-page-description: Inzicht in gebruik en beheer van Headless in Adobe Experience Manager as a Cloud Service.
exl-id: 24300499-ae9c-49d0-aa25-f51e14d9cf79
source-git-commit: e03c067f4337bbf0e98cb4015b9be4fc99fc17c1
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 8%

---


# Inleiding tot Adobe Experience Manager als een headless CMS {#introduction-aem-headless}

Leer hoe u Adobe Experience Manager (AEM) kunt gebruiken als een CMS zonder hoofd (Content Management System), met functies zoals modellen van inhoudsfragmenten, contentfragmenten en een GraphQL API die samen een krachtige ervaring zonder hoofd op schaal bieden.

U kunt gedetailleerde documentatie van de verschillende betrokken eigenschappen lezen en/of de selectie volgen [Headless Reizen voor een overzicht van de eerste stappen](#first-steps).

>[!NOTE]
>
>Zie ook [Wat is Headless?](/help/headless/what-is-headless.md) voor een inleiding op de concepten en terminologie zonder koppen.

{{headless-trials-promotion}}

## Overzicht {#overview}

AEM Headless is een CMS-oplossing van Experience Manager waarmee gestructureerde inhoud (Content Fragments) in AEM kan worden verbruikt door elke toepassing via HTTP met GraphQL. Met een headless-implementatie kunt u ervaringen op verschillende platforms en kanalen op schaal aanbieden.

Bij implementatie zonder kop gaat het beheer van pagina&#39;s en componenten verloren, zoals gebruikelijk is bij oplossingen met volledige stapel en hybride oplossingen. In plaats daarvan richt het programma zich op het maken van kanaalneutrale, herbruikbare fragmenten van inhoud en de levering van deze fragmenten over het kanaal. Het is een modern en dynamisch ontwikkelingspatroon voor het implementeren van webervaringen.

![Implementatiemodellen AEM](assets/aem-implementation-models.png)

## Functies {#aem-headless-features}

AEM as a Cloud Service is een flexibel hulpmiddel voor het implementatiemodel zonder kop door drie krachtige functies te bieden:

1. **Modellen van contentfragmenten**
   * Content Fragment Models is gestructureerde representaties van inhoud.
   * Modellen van inhoudsfragmenten worden gedefinieerd door informatiearchitecten in de AEM Content Fragment Model-editor.
   * Modellen van inhoudsfragmenten dienen als basis voor inhoudsfragmenten.
1. **Contentfragmenten**
   * Er wordt een inhoudsfragment gemaakt op basis van een inhoudsfragmentmodel.
   * Inhoudsfragmenten worden gemaakt door auteurs van inhoud met de AEM Content Fragment-editor.
   * Inhoudsfragmenten worden opgeslagen als AEM Assets, maar kunnen worden beheerd via de middelenconsole of via de [Console voor inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragments-console.md).
1. **Inhoud-API voor levering**
   * De AEM GraphQL API ondersteunt de levering van inhoudsfragmenten.
   * De AEM Assets REST-API ondersteunt CRUD-bewerkingen voor inhoudsfragmenten.
   * Directe levering van inhoud is ook mogelijk met de [JSON-export van de Content Fragment Core-component](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html).

## Uw eerste stappen {#first-steps}

Er zijn verschillende bronnen beschikbaar om aan de slag te gaan met AEM functies zonder kop. Elke hulplijn is op maat gemaakt voor verschillende gebruiksgevallen en verschillende soorten publiek.

| Resource | Beschrijving | Type | Publiek | Oost. Tijd |
|---|---|---|---|---|
| [Headless Developer Journey](/help/journey-headless/developer/overview.md) | **Voor nieuwe ontwikkelaars AEM en zonder kop** technologieën, begin hier voor een uitvoerige inleiding aan AEM en zijn headless eigenschappen van de theorie van headless door met uw eerste hoofdloze project te leven. | Handleiding | Ontwikkelaars **nieuw tot AEM en zonder kop** | 1 uur |
| [Installatie zonder koppen](/help/headless/setup/introduction.md) | **Voor ervaren AEM** Voor een kort overzicht van de belangrijkste functies voor het AEM zonder kop, bekijkt u dit snelstartoverzicht. | Referentie-instelling | Ontwikkelaars, beheerders **met AEM ervaring** | 20 minuten |
| [Zelfstudie over headless hands-on](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) | **Als u een hands-on benadering verkiest en met AEM vertrouwd bent** Deze zelfstudie leidt rechtstreeks tot de implementatie van een eenvoudige app zonder koppen. | Zelfstudie | Ontwikkelaars | 2 uur |
| [Architect zonder hoofd](/help/journey-headless/architect/overview.md) | **Voor architecten die nieuw zijn voor AEM en zonder kop** -technologieën, begint hier voor een introductie van de krachtige, flexibele, eindeloze functies van Adobe Experience Manager as a Cloud Service en hoe u inhoud voor uw project kunt modelleren. | Handleiding | Architecten | 1 uur |
| [Papierreis zonder koppen](/help/journey-headless/author/overview.md) | **Voor zakelijke gebruikers die nog niet AEM en zonder kop** -technologieën, begint hier voor een introductie van de krachtige, flexibele, eindeloze functies van Adobe Experience Manager as a Cloud Service en hoe u inhoud voor uw project kunt modelleren. | Handleiding | Inhoudsmakers | 1 uur |
| [Dagboekreis zonder hoofd](/help/journey-headless/translation/overview.md) | Voor die **geïnteresseerd in AEM vertaalbenadering van krantenkoppen**. Leer over headless technologieën en hoe te om vertaalprojecten in AEM van A tot Z te creëren en bij te werken. | Handleiding | Vertaalspecialisten | 1 uur |

## Bezig met vergelijken van hoofdletters en hoofdletters {#headful-headless}

Deze handleiding is gericht op het volledige implementatiemodel zonder kop van AEM. Nochtans moet de macht tegenover de zonder kop geen binaire keus in AEM zijn. U kunt headless-functies gebruiken om inhoud te beheren en aan meerdere aanraakpunten te leveren, en tegelijkertijd inhoudsauteurs de mogelijkheid bieden om toepassingen van één pagina te bewerken. Alles in AEM.

>[!TIP]
>
>Zie het document [Hoofdletters en headless in AEM](/help/implementing/developing/headful-headless.md) voor meer informatie .