---
title: Inleiding tot headless voor AEM
description: Meer informatie over Headless in Adobe Experience Manager (AEM) met een combinatie van gedetailleerde documentatie en headless reizen. Ontdek hoe functies zoals Content Fragment Models, Content Fragments en een GraphQL API worden gebruikt om headless-ervaringen mogelijk te maken.
landing-page-description: Inzicht in gebruik en beheer van Headless in Adobe Experience Manager as a Cloud Service.
exl-id: 24300499-ae9c-49d0-aa25-f51e14d9cf79
feature: Headless
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 8%

---


# Inleiding tot Adobe Experience Manager als een headless CMS {#introduction-aem-headless}

Leer hoe u Adobe Experience Manager (AEM) kunt gebruiken als een CMS zonder hoofd (Content Management System), met functies zoals modellen van inhoudsfragmenten, contentfragmenten en een GraphQL API die samen een krachtige ervaring zonder hoofd op schaal bieden.

U kunt gedetailleerde documentatie van de diverse betrokken eigenschappen lezen en/of de selectie van [ Dagloze Reizen volgen om een overzicht van de eerste stappen ](#first-steps) te krijgen.

>[!NOTE]
>
>Zie ook [ wat zonder hoofd is?](/help/headless/what-is-headless.md) voor een inleiding aan de concepten en de terminologie zonder kop.

{{headless-trials-promotion}}

## Overzicht {#overview}

AEM Headless is een CMS-oplossing van Experience Manager waarmee gestructureerde inhoud (Content Fragments) in AEM kan worden verbruikt door elke toepassing via HTTP met GraphQL. Met een headless-implementatie kunt u ervaringen op verschillende platforms en kanalen op schaal aanbieden.

Bij implementatie zonder kop gaat het beheer van pagina&#39;s en componenten verloren, zoals gebruikelijk is bij oplossingen met volledige stapel en hybride oplossingen. In plaats daarvan richt het programma zich op het maken van kanaalneutrale, herbruikbare fragmenten van inhoud en de levering van deze fragmenten over het kanaal. Het is een modern en dynamisch ontwikkelingspatroon voor het implementeren van webervaringen.

![ AEM de Modellen van de Implementatie ](assets/aem-implementation-models.png)

## Functies {#aem-headless-features}

AEM as a Cloud Service is een flexibel hulpmiddel voor het implementatiemodel zonder kop door drie krachtige functies te bieden:

1. **Modellen van contentfragmenten**
   * Content Fragment Models is gestructureerde representaties van inhoud.
   * Modellen van inhoudsfragmenten worden gedefinieerd door informatiearchitecten in de AEM Content Fragment Model-editor.
   * Modellen van inhoudsfragmenten dienen als basis voor inhoudsfragmenten.
1. **Contentfragmenten**
   * Er wordt een inhoudsfragment gemaakt op basis van een inhoudsfragmentmodel.
   * Inhoudsfragmenten worden gemaakt door auteurs van inhoud, die de AEM Content Fragment-editor gebruiken.
   * De Fragmenten van de inhoud worden opgeslagen als AEM Assets, maar kunnen door of de Console van Assets, of de [ Console van de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) worden beheerd.
1. **Inhoud API voor levering**
   * De AEM GraphQL API ondersteunt de levering van inhoudsfragmenten.
   * De AEM Assets REST-API ondersteunt CRUD-bewerkingen voor inhoudsfragmenten.
   * De directe inhoudslevering is ook mogelijk met de [ uitvoer JSON van de Component van de Kern van het Fragment van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html).

## Uw eerste stappen {#first-steps}

Er zijn verschillende bronnen beschikbaar om aan de slag te gaan met AEM functies zonder kop. Elke hulplijn is op maat gemaakt voor verschillende gebruiksgevallen en verschillende soorten publiek.

| Bron | Beschrijving | Type | Publiek | Oost. Tijd |
|---|---|---|---|---|
| [ Zwaardeloze Reis van de Ontwikkelaar ](/help/journey-headless/developer/overview.md) | **voor ontwikkelaars nieuw aan AEM en headless** technologieën, begin hier voor een uitvoerige inleiding aan AEM en zijn headless eigenschappen van de theorie van headless door met uw eerste headless project te leven te gaan. | Hulplijn | De ontwikkelaars **nieuw aan AEM en zonder kop** | 1 uur |
| [ Hoofdloze Opstelling ](/help/headless/setup/introduction.md) | **voor ervaren AEM gebruikers** die een korte samenvatting van de belangrijkste AEM zonder kop eigenschappen nodig hebben, controleer dit snelle beginoverzicht. | Referentie-instelling | De ontwikkelaars, Beheerders **met AEM ervaring** | 20 minuten |
| [ Hoofdloze hands-on leerprogramma ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) | **als u een hands-on benadering verkiest en met AEM** vertrouwd bent, duikt dit leerprogramma direct in het uitvoeren van een eenvoudige headless app. | Zelfstudie | Ontwikkelaars | 2 uur |
| [ Evolutie van de Architect zonder hoofd ](/help/journey-headless/architect/overview.md) | **voor architecten nieuw aan AEM en headless** technologieën, begin hier voor een inleiding aan krachtige, en flexibele, headless eigenschappen van Adobe Experience Manager as a Cloud Service, en hoe te om inhoud voor uw project te modelleren. | Hulplijn | Architecten | 1 uur |
| [ Headless Authoring Reis ](/help/journey-headless/author/overview.md) | **voor bedrijfsgebruikers nieuw aan AEM en headless** technologieën, begin hier voor een inleiding aan krachtige, en flexibele, headless eigenschappen van Adobe Experience Manager as a Cloud Service, en hoe te om inhoud voor uw project te modelleren. | Hulplijn | Inhoudsmakers | 1 uur |
| [ Zwaardeloze Vertaalreis ](/help/journey-headless/translation/overview.md) | Voor die **geinteresseerd in AEM vertaalbenadering aan hoofd**. Leer over headless technologieën en hoe te om vertaalprojecten in AEM van A tot Z te creëren en bij te werken. | Hulplijn | Vertaalspecialisten | 1 uur |

## Bezig met vergelijken van hoofdletters en hoofdletters {#headful-headless}

Deze handleiding is gericht op het volledige implementatiemodel zonder kop van AEM. Nochtans, hoeft de kop versus de kop geen binaire keuze in AEM te zijn. U kunt headless-functies gebruiken om inhoud te beheren en aan meerdere aanraakpunten te leveren, en tegelijkertijd inhoudsauteurs de mogelijkheid bieden om toepassingen van één pagina te bewerken. Alles in AEM.

>[!TIP]
>
>Zie het document [ Kopieerbaar en Hoofdloos in AEM ](/help/implementing/developing/headful-headless.md) voor meer informatie.