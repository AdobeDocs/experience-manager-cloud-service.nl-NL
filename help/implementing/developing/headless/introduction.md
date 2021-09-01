---
title: Headless Development voor AEM Sites als Cloud Service
description: Leer hoe AEM als krachtige headless mogelijkheden van een Cloud Service zoals de Modellen van de Inhoud, de Fragments van de Inhoud, en GraphQL API samenwerken om u toe te laten om uw ervaringen centraal te beheren en hen te dienen over kanalen.
exl-id: 24300499-ae9c-49d0-aa25-f51e14d9cf79
source-git-commit: 387e75faeccb0671a32a54ff0c12f05219844311
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 1%

---


# Headless Development voor AEM Sites als Cloud Service {#headless-development}

Leer hoe AEM als krachtige headless mogelijkheden van een Cloud Service zoals de Modellen van de Inhoud, de Fragments van de Inhoud, en GraphQL API samenwerken om u toe te laten om uw ervaringen centraal te beheren en hen te dienen over kanalen.

## Overzicht {#overview}

De implementatie zonder hoofd wordt steeds belangrijker om ervaringen aan uw publiek te kunnen bieden, waar ze zich ook bevinden en ongeacht het kanaal.

Bij implementatie zonder kop gaan pagina- en componentbeheer verloren, zoals gebruikelijk is in oplossingen voor volledige stapels en hybride oplossingen, en wordt de nadruk gelegd op het maken van kanaalneutrale, herbruikbare fragmenten van inhoud en hun levering over het kanaal. Het is een modern en dynamisch ontwikkelingspatroon voor het implementeren van webervaringen.

![AEM implementatiemodellen](assets/aem-implementation-models.png)

## Bezig met vergelijken van hoofdletters en hoofdletters {#headful-headless}

Dit document richt zich op het volledige implementatiemodel zonder kop van AEM. Nochtans moet de macht tegenover de zonder kop geen binaire keus in AEM zijn. U kunt de functies zonder koppen gebruiken om uw inhoud te beheren en aan verschillende eindpunten te leveren, terwijl u de auteurs van de inhoud ook in staat stelt toepassingen op één pagina te bewerken. Alles in AEM.

>[!TIP]
>
>Zie het document [Headful en Headless in AEM](/help/implementing/developing/headful-headless.md) voor meer informatie.

## AEM als Cloud Service en zonder kop {#aem-headless}

AEM als Cloud Service is een flexibel instrument voor het model van de implementatie zonder kop door drie krachtige services aan te bieden:

1. Inhoudsmodellen
   * Inhoudsmodellen zijn een gestructureerde weergave van inhoud.
   * Deze worden gedefinieerd door informatiearchitecten in de AEM Content Fragment Model-editor.
   * Inhoudsmodellen dienen als basis voor inhoudsfragmenten.
1. Contentfragmenten
   * Inhoudsfragmenten zijn instantiaties van inhoudsmodellen.
   * Deze worden gemaakt door auteurs van inhoud met de AEM Content Fragment-editor.
   * Ze worden opgeslagen in AEM Assets en beheerd in de interface voor middelenbeheer.
1. Inhoud-API voor levering
   * De AEM GraphQL API ondersteunt de levering van contentfragmenten.
   * De AEM Assets REST-API ondersteunt CRUD-bewerkingen voor inhoudsfragmenten.
   * Directe inhoudlevering is ook mogelijk met de JSON-export van de [Content Fragment Core Component.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html)

## Uw eerste stappen met AEM zonder kop {#first-steps}

Er zijn een aantal bronnen beschikbaar waarmee u aan de slag kunt met AEM functies zonder kop. Ze zijn bedoeld voor verschillende gebruiksgevallen, maar bieden allemaal een stevig overzicht van AEM hoofdloze kenmerken.

| Resource | Beschrijving | Type | Publiek | Oost. Time |
|---|---|---|---|---|
| [Headless Developer Journey](/help/journey-headless/developer/overview.md) | **Voor gebruikers die niet vertrouwd zijn met AEM en** headlesstechnologieën, begin hier voor een uitvoerige inleiding aan AEM en zijn headless eigenschappen van de theorie van headless door met uw eerste hoofdloze project te leven. | Hulplijn | Ontwikkelaars **nieuw voor AEM en zonder kop** | 1 uur |
| [Aan de slag met koppen](/help/implementing/developing/headless/getting-started/introduction.md) | **Voor ervaren AEM** gebruikers die een korte samenvatting van de belangrijkste AEM functies nodig hebben, bekijkt u dit snelstartoverzicht. | Snel starten | Ontwikkelaars, beheerders **met AEM ervaring** | 20 minuten |
| [Aan de slag met AEM praktische zelfstudie zonder hoofd](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) | **Als u een hands-on benadering verkiest en met AEM** vertrouwd bent, duikt dit leerprogramma direct in het creëren van een eenvoudig headless project. | Zelfstudie | Ontwikkelaars | 2 uur |
