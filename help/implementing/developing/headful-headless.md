---
title: Hoofdletters en headless in AEM
description: AEM projecten kunnen worden uitgevoerd in een krachtig en zonder kop model, maar de keuze is niet binair. AEM offers the flexibility to exploit the advantages of both models in one project.
exl-id: 709850ca-7757-47ab-9625-f411121cde2c
source-git-commit: e592dd7a3a717259493f23943933fe3d0e71b7ab
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 0%

---

# Hoofdletters en headless in AEM {#headful-headless}

Adobe Experience Manager projects can be implemented in both headful and headless models, but the choice isn&#39;t binary. AEM offers the flexibility to exploit the advantages of both models in one project. Dit document biedt een overzicht van de verschillende modellen en beschrijft de niveaus van SPA integratie.

## Overzicht {#overview}

AEM offers powerful tools to manage both the creation of content and its delivery in one platform. This is a traditional &quot;headful&quot; model of content management, where the content authors and developers work on the same platform to deliver the experiences to the content consumers.

AEM kan ook worden gebruikt om inhoud eenvoudig te beheren, zodat de presentatie en levering van de inhoud door een ander platform kunnen worden beheerd. This is the &quot;headless&quot; model of content management, where the content authors and developers work on different platforms to deliver experience to the content consumers.

But this need not be a binary choice. AEM offers unprecedented flexibility, allowing you to exploit the advantages of both models for your project.

![AEM Implementation Models](/help/headless/assets/aem-implementation-models.png)

In a headful or full-stack model, the content is managed in the AEM repository and AEM components based on Java, HTL, etc. worden gebruikt om de inhoud weer te geven voor de gebruikerservaring. In dit model gebeurt het maken van de inhoud, het vormgeven, het presenteren en het leveren ervan allemaal in AEM.

In een headless model, wordt de inhoud beheerd in de AEM bewaarplaats, maar geleverd via APIs zoals REST en GraphQL aan een ander systeem om de inhoud voor de gebruikerservaring terug te geven. In dit model wordt inhoud gemaakt in AEM, maar wordt de inhoud vormgegeven, gepresenteerd en geleverd op een ander platform.

Single Page Applications (SPAs) are often the destination for content delivered headlessly by AEM. Deze SPA hoeven echter niet geheel buiten de AEM te liggen. AEM allows you to decide to what degree your SPAs are integrated into AEM. Let&#39;s take an example.

## Web Shop Example {#web-shop-example}

Stel dat u een bestaande webshop hebt voor uw bedrijf als SPA. In it you have all your product details and images. Vervolgens introduceert u AEM om uw marketingactiviteiten, zoals promotiesites, blogs en inhoud van campagnes, kracht bij te zetten. Hoe integreer je deze twee? AEM enables a spectrum of options:

* **De systemen onafhankelijk laten werken.**
* **Bied de webshop beperkte inhoud van AEM via GraphQL.** Inhoud kan door auteurs in AEM worden gemaakt, maar kan alleen via de SPA van de webshop worden bekeken.
* **Sluit de SPA van de webshop in AEM in.** Content can be created by authors in AEM, and viewed in AEM in the context of the web shop, but not manipulated.
* **Sluit de SPA van de webshop in AEM in en schakel bewerkbare punten in.** Inhoud kan door auteurs in AEM worden gemaakt en in AEM in de context van de webshop worden weergegeven. De auteurs hebben slechts beperkte mogelijkheden om de inhoud van de webshop SPA binnen AEM te manipuleren.
* **Embed the webs shop SPA in AEM, and enable entire zones for editing.** Inhoud kan door auteurs in AEM worden gemaakt en in AEM in de context van de webshop worden weergegeven. De auteurs hebben slechts beperkte mogelijkheden om de inhoud van de webshop SPA binnen AEM te manipuleren.

In de volgende sectie worden deze integratieniveaus nader beschreven.

>[!NOTE]
>
>Natuurlijk kunt u de SPA van de webshop ook opnieuw implementeren als een volledig functionerende AEM SPA [het AEM SPA Editor-framework gebruiken.](/help/implementing/developing/hybrid/introduction.md) Als u al een nieuwe webshop of andere SPA hebt AEM en wilt maken, is dit de aanbevolen methode, maar valt deze buiten het bereik van dit document.

## SPA integratieniveaus {#integration-levels}

SPA integratie ligt op een spectrum van vier niveaus in AEM.

* **Level 0: No integration**
   * De SPA en AEM bestaan afzonderlijk en wisselen geen informatie uit.
   * Inhoud wordt in twee aparte systemen gemaakt, beheerd en afzonderlijk geleverd.
* **Niveau 1: Integratie van inhoudsfragmenten**
   * [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md) worden gebruikt in AEM om beperkte inhoud voor de SPA te maken en te beheren.
   * De SPA haalt deze inhoud op via AEM [GraphQL API.](/help/headless/graphql-api/content-fragments.md)
   * Sommige inhoud wordt beheerd in AEM en sommige in een extern systeem.
   * Inhoud kan alleen in de SPA worden weergegeven.
* **Niveau 2: De SPA insluiten in AEM**
   * [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md) worden gebruikt in AEM om inhoud voor de SPA te maken en te beheren.
   * De SPA haalt deze inhoud op via AEM [GraphQL API.](/help/headless/graphql-api/content-fragments.md)
   * Some content is managed in AEM and some in an external system.
   * Content can be viewed in-context within AEM.
   * Limited content can be edited within AEM.
* **Niveau 3: SPA insluiten en volledig inschakelen in AEM**
   * [Content Fragments](/help/assets/content-fragments/content-fragments.md) are used in AEM to create and manage content for the SPA.
   * The SPA retrieves this content via AEM&#39;s [GraphQL API.](/help/headless/graphql-api/content-fragments.md)
   * Inhoud kan binnen AEM in context worden weergegeven.
   * De meeste inhoud kan worden bewerkt in AEM.

Niveau 1 is een voorbeeld van een typische implementatie zonder kop. However content authors can only view their content in-context within the SPA. AEM is slechts een ontwerpgereedschap.

The advantage and flexibility of AEM becomes apparent with levels 2 and 3 while still retaining the advantages of SPAs. Content authors can create their content in AEM, but also see it in-context within AEM. De SPA krijgt het vermogen om in AEM te worden ontworpen, maar nog als SPA worden geleverd.

## Implementatie van de integratieniveaus {#implementing}

Er zijn verschillende gereedschappen in AEM beschikbaar, afhankelijk van het integratieniveau dat u kiest. Elk niveau bouwt op de hulpmiddelen voort die in het vorige worden gebruikt. De volgende lijst verwijst naar de relevante bronnen.

* **Niveau 1:** Inhoudsfragmenten en de [AEM kader zonder kop](/help/headless/introduction.md) kan worden gebruikt om AEM inhoud aan de SPA te leveren.
* **Niveau 2:** Naast niveau 1:
   * [De component RemotePage](/help/implementing/developing/hybrid/remote-page.md) kan worden gebruikt om de externe SPA in te sluiten in AEM waar AEM inhoud in context kan worden bekeken.
   * Bepaalde punten op de SPA kunnen ook worden ingeschakeld op [beperkte bewerking in AEM toestaan.](/help/implementing/developing/hybrid/editing-external-spa.md)
* **Niveau 3:** Naast niveau 2:
   * Volledige zones van de SPA kunnen worden ingeschakeld om uitgebreide bewerkingen in AEM toe te staan.
