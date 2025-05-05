---
title: Introductie tot headless voor AEM
description: Meer informatie over Headless in Adobe Experience Manager (AEM) met een combinatie van gedetailleerde documentatie en headless reizen. Ontdek hoe functies zoals Content Fragment Models, Content Fragments en een GraphQL API worden gebruikt om headless-ervaringen mogelijk te maken.
landing-page-description: Inzicht in gebruik en beheer van Headless in Adobe Experience Manager as a Cloud Service.
exl-id: 24300499-ae9c-49d0-aa25-f51e14d9cf79
feature: Headless
role: Admin, Developer
source-git-commit: 920045ab4e79dc223706219bf64347649af14125
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 8%

---


# Inleiding tot Adobe Experience Manager als een CMS zonder kop {#introduction-aem-headless}

Leer hoe u Adobe Experience Manager (AEM) gebruikt als een Headless CMS (Content Management System), met functies zoals Content Fragment Models, Content Fragments en een GraphQL API die samen een krachtige ervaring zonder inhoud op schaal bieden.

U kunt gedetailleerde documentatie van de diverse betrokken eigenschappen lezen en/of de selectie van [ Dagloze Reizen volgen om een overzicht van de eerste stappen ](#first-steps) te krijgen.

>[!NOTE]
>
>Zie ook [ wat zonder hoofd is?](/help/headless/what-is-headless.md) voor een inleiding aan de concepten en de terminologie zonder kop.

## Overzicht {#overview}

AEM Headless is een CMS-oplossing van Experience Manager waarmee gestructureerde inhoud (Content Fragments) in AEM kan worden gebruikt door elke toepassing via HTTP via GraphQL. Met een headless-implementatie kunt u ervaringen op verschillende platforms en kanalen op schaal aanbieden.

Bij implementatie zonder kop gaat het beheer van pagina&#39;s en componenten verloren, zoals gebruikelijk is bij oplossingen met volledige stapel en hybride oplossingen. In plaats daarvan richt het programma zich op het maken van kanaalneutrale, herbruikbare fragmenten van inhoud en de levering van deze fragmenten over het kanaal. Het is een modern en dynamisch ontwikkelingspatroon voor het implementeren van webervaringen.

![ Modellen van de Implementatie van AEM ](assets/aem-implementation-models.png)

## Functies {#aem-headless-features}

AEM as a Cloud Service is een flexibel hulpmiddel voor het implementatiemodel zonder kop door drie krachtige functies te bieden:

1. **Modellen van contentfragmenten**
   * Content Fragment Models is gestructureerde representaties van inhoud.
   * Modellen van inhoudsfragmenten worden gedefinieerd door informatiearchitecten in de AEM Content Fragment Model Editor.
   * Modellen van inhoudsfragmenten dienen als basis voor inhoudsfragmenten.
1. **Contentfragmenten**
   * Er wordt een inhoudsfragment gemaakt op basis van een inhoudsfragmentmodel.
   * Inhoudsfragmenten worden gemaakt door auteurs van inhoud met de AEM Content Fragment-editor.
   * De Fragmenten van de inhoud worden opgeslagen als AEM Assets, maar kunnen door of de Console van Assets, of de [ Console van de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/overview.md#content-fragments-console) worden beheerd.
1. **Inhoud API voor levering**
   * Zie [ AEM APIs voor Gestructureerde Inhoudslevering en Beheer ](/help/headless/apis-headless-and-content-fragments.md) voor een overzicht van diverse beschikbare APIs en vergelijking van sommige betrokken concepten.

   * De directe inhoudslevering is ook mogelijk met de [ uitvoer JSON van de Component van de Kern van het Fragment van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=nl-NL).

## Uw eerste stappen {#first-steps}

Er zijn verschillende bronnen beschikbaar om aan de slag te gaan met functies zonder koppen van AEM. Elke hulplijn is op maat gemaakt voor verschillende gebruiksgevallen en verschillende soorten publiek.

| Bron | Beschrijving | Type | Publiek | Oost. Tijd |
|---|---|---|---|---|
| [ Zwaardeloze Reis van de Ontwikkelaar ](/help/journey-headless/developer/overview.md) | **voor ontwikkelaars nieuw aan AEM en headless** technologieën, begin hier voor een uitvoerige inleiding aan AEM en zijn headless eigenschappen van de theorie van headless door met uw eerste headless project te leven te gaan. | Hulplijn | Ontwikkelaars **nieuw aan AEM en zonder kop** | 1 uur |
| [ Hoofdloze Opstelling ](/help/headless/setup/introduction.md) | **voor ervaren gebruikers van AEM** die een korte samenvatting van de belangrijkste eigenschappen van AEM nodig hebben, controleer dit snelle beginoverzicht. | Referentie-instelling | De ontwikkelaars, Beheerders **met de ervaring van AEM** | 20 minuten |
| [ Hoofdloze hands-on leerprogramma ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=nl-NL) | **als u een hands-on benadering verkiest en met AEM** vertrouwd bent, duikt dit leerprogramma direct in het uitvoeren van een eenvoudige headless app. | Zelfstudie | Ontwikkelaars | 2 uur |
| [ Evolutie van de Architect zonder hoofd ](/help/journey-headless/architect/overview.md) | **voor architecten nieuw aan AEM en headless** technologieën, begin hier voor een inleiding aan krachtige, en flexibele, headless eigenschappen van Adobe Experience Manager as a Cloud Service, en hoe te om inhoud voor uw project te modelleren. | Hulplijn | Architecten | 1 uur |
| [ Headless Authoring Reis ](/help/journey-headless/author/overview.md) | **voor bedrijfsgebruikers nieuw aan AEM en headless** technologieën, begin hier voor een inleiding aan krachtige, en flexibele, headless eigenschappen van Adobe Experience Manager as a Cloud Service, en hoe te om inhoud voor uw project te modelleren. | Hulplijn | Inhoudsmakers | 1 uur |
| [ Zwaardeloze Vertaalreis ](/help/journey-headless/translation/overview.md) | Voor die **geinteresseerd in de vertaalbenadering van AEM aan headless**. Leer meer over technologieën zonder kop en hoe u vertaalprojecten in AEM kunt maken en bijwerken van A naar Z. | Hulplijn | Vertaalspecialisten | 1 uur |

## Bezig met vergelijken van hoofdletters en hoofdletters {#headful-headless}

Deze handleiding is gericht op het volledige implementatiemodel zonder kop van AEM. Maar kop versus kop hoeft geen binaire keuze te zijn in AEM. U kunt headless-functies gebruiken om inhoud te beheren en aan meerdere aanraakpunten te leveren, en tegelijkertijd inhoudsauteurs de mogelijkheid bieden om toepassingen van één pagina te bewerken. Alles in AEM.

>[!TIP]
>
>Zie het document [ Kopieerbaar en Hoofdloos in AEM ](/help/implementing/developing/headful-headless.md) voor meer informatie.
