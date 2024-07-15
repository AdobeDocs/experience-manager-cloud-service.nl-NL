---
title: Hoofdletters en headless in AEM
description: AEM projecten kunnen worden geïmplementeerd in een krachtig en zonder kop, maar de keuze is niet binair. AEM biedt de flexibiliteit om de voordelen van beide modellen in één project te benutten.
exl-id: 709850ca-7757-47ab-9625-f411121cde2c
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1024'
ht-degree: 0%

---

# Hoofdletters en headless in AEM {#headful-headless}

Adobe Experience Manager-projecten kunnen worden geïmplementeerd in zowel headful als headless modellen, maar de keuze is niet binair. AEM biedt de flexibiliteit om de voordelen van beide modellen in één project te benutten. Dit document biedt een overzicht van de verschillende modellen en beschrijft de niveaus van SPA integratie.

## Overzicht {#overview}

AEM biedt krachtige tools om zowel de creatie van inhoud als de levering ervan in één platform te beheren. Dit is een traditioneel &#39;krachtig&#39; model van contentbeheer, waarbij de auteurs en ontwikkelaars van inhoud op hetzelfde platform werken om de ervaringen aan de gebruikers van de inhoud te leveren.

AEM kan ook worden gebruikt om inhoud eenvoudig te beheren, zodat de presentatie en levering van de inhoud door een ander platform kunnen worden beheerd. Dit is het &#39;headless&#39;-model van contentbeheer, waarbij de auteurs en ontwikkelaars van inhoud op verschillende platforms werken om de gebruikers van inhoud ervaring te bieden.

Maar dit hoeft geen binaire keuze te zijn. AEM biedt ongekende flexibiliteit, die u toestaat om de voordelen van beide modellen voor uw project te exploiteren.

![ AEM de Modellen van de Implementatie ](/help/headless/assets/aem-implementation-models.png)

In een krachtig of volledig-stapelmodel, wordt de inhoud beheerd in de AEM bewaarplaats en AEM componenten die op Java, HTML worden gebaseerd, etc. worden gebruikt om de inhoud voor de gebruikerservaring terug te geven. In dit model gebeurt het maken van de inhoud, het vormgeven, het presenteren en het leveren ervan allemaal in AEM.

In een headless model, wordt de inhoud beheerd in de AEM bewaarplaats, maar geleverd via APIs zoals REST en GraphQL aan een ander systeem om de inhoud voor de gebruikerservaring terug te geven. In dit model wordt inhoud gemaakt in AEM, maar wordt de inhoud vormgegeven, gepresenteerd en geleverd op een ander platform.

Toepassingen op één pagina (SPA) zijn vaak de bestemming voor inhoud die zonder kop door AEM wordt geleverd. Deze SPA hoeven echter niet geheel buiten de AEM te liggen. AEM kunt u bepalen in welke mate uw SPA in AEM wordt geïntegreerd. Laten we een voorbeeld nemen.

## Voorbeeld van webwinkel {#web-shop-example}

Laten we zeggen dat u een bestaande webshop hebt voor uw bedrijf als SPA. Hierin staan al uw productdetails en afbeeldingen. Vervolgens introduceert u AEM om uw marketingactiviteiten, zoals promotiesites, blogs en inhoud van campagnes, kracht bij te zetten. Hoe integreer je deze twee? AEM maakt een spectrum van opties mogelijk:

* **sta de systemen toe om onafhankelijk te werken.**
* **leverde de Webshop met beperkte inhoud van AEM via GraphQL.** Inhoud kan door auteurs in AEM worden gemaakt, maar kan alleen via de SPA van de webshop worden bekeken.
* **bedt de Webshop SPA in AEM.** Inhoud kan door auteurs in AEM worden gemaakt en in AEM in de context van de webshop worden weergegeven, maar kan niet worden gemanipuleerd.
* **bedt de Webshop SPA in AEM, en laat editable punten toe.** Inhoud kan door auteurs in AEM worden gemaakt en in AEM in de context van de webshop worden weergegeven. De auteurs hebben slechts beperkte mogelijkheden om de inhoud van de webshop SPA binnen AEM te manipuleren.
* **bedt Webs in SPA in AEM, en laat volledige streken voor het uitgeven toe.** Inhoud kan door auteurs in AEM worden gemaakt en in AEM in de context van de webshop worden weergegeven. De auteurs hebben slechts beperkte mogelijkheden om de inhoud van de webshop SPA binnen AEM te manipuleren.

In de volgende sectie worden deze integratieniveaus nader beschreven.

>[!NOTE]
>
>Natuurlijk kon u de Webshop SPA als volledig functionerende AEM ook re-uitvoeren SPA [ gebruikend het kader van de SPA van de Redacteur AEM ](/help/implementing/developing/hybrid/introduction.md). Als u al een webshop of andere SPA hebt AEM en wilt maken, is dit de aanbevolen methode, maar valt deze buiten het bereik van dit document.

## SPA integratieniveaus {#integration-levels}

SPA integratie ligt op een spectrum van vier niveaus in AEM.

* **Niveau 0: Geen integratie**
   * De SPA en AEM bestaan afzonderlijk en wisselen geen informatie uit.
   * Inhoud wordt in twee aparte systemen gemaakt, beheerd en afzonderlijk geleverd.
* **Niveau 1: De integratie van het fragmentintegratie van de inhoud**
   * [ de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/overview.md) worden gebruikt in AEM om beperkte inhoud voor de SPA tot stand te brengen en te beheren.
   * De SPA wint deze inhoud via AEM [ GraphQL API ](/help/headless/graphql-api/content-fragments.md) terug.
   * Sommige inhoud wordt beheerd in AEM en sommige in een extern systeem.
   * Inhoud kan alleen in de SPA worden weergegeven.
* **Niveau 2: Sluit de SPA in AEM** in
   * [ de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/overview.md) worden gebruikt in AEM om inhoud voor de SPA tot stand te brengen en te beheren.
   * De SPA wint deze inhoud via AEM [ GraphQL API ](/help/headless/graphql-api/content-fragments.md) terug.
   * Sommige inhoud wordt beheerd in AEM en sommige in een extern systeem.
   * Inhoud kan binnen AEM in context worden weergegeven.
   * Beperkte inhoud kan binnen AEM worden bewerkt.
* **Niveau 3: Sluit en laat volledig SPA in AEM** in
   * [ de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/overview.md) worden gebruikt in AEM om inhoud voor de SPA tot stand te brengen en te beheren.
   * De SPA wint deze inhoud via AEM [ GraphQL API ](/help/headless/graphql-api/content-fragments.md) terug.
   * Inhoud kan binnen AEM in context worden weergegeven.
   * De meeste inhoud kan worden bewerkt in AEM.

Niveau 1 is een voorbeeld van een typische implementatie zonder kop. Inhoudsauteurs kunnen hun inhoud echter alleen in-context binnen de SPA bekijken. AEM is slechts een ontwerpgereedschap.

Het voordeel en de flexibiliteit van AEM worden duidelijk met niveaus 2 en 3, terwijl de voordelen van SPA behouden blijven. Inhoudsauteurs kunnen hun inhoud in AEM maken, maar zien deze ook in context binnen AEM. De SPA krijgt het vermogen om in AEM te worden ontworpen, maar nog als SPA worden geleverd.

## Implementatie van de integratieniveaus {#implementing}

Er zijn verschillende gereedschappen in AEM beschikbaar, afhankelijk van het integratieniveau dat u kiest. Elk niveau bouwt op de hulpmiddelen voort die in het vorige worden gebruikt. De volgende lijst verwijst naar de relevante bronnen.

* **Niveau 1:** de Fragmenten van de Inhoud en [ AEM headless kader ](/help/headless/introduction.md) kunnen worden gebruikt om AEM inhoud aan de SPA te leveren.
* **Niveau 2:** naast niveau één:
   * [ de component RemotePage ](/help/implementing/developing/hybrid/remote-page.md) kan worden gebruikt om de externe SPA in AEM in te bedden waar de AEM inhoud in-context kan worden bekeken.
   * Bepaalde punten op het SPA kunnen ook worden toegelaten [ beperkt het uitgeven in AEM ](/help/implementing/developing/hybrid/editing-external-spa.md) toestaan.
* **Niveau 3:** naast niveau twee:
   * Volledige zones van de SPA kunnen worden ingeschakeld om uitgebreide bewerkingen in AEM toe te staan.
