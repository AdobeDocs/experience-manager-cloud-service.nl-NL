---
title: Uw inhoud bijwerken via AEM API's
description: In dit gedeelte van de AEM Headless Developer Journey leert u hoe u de beschikbare API's kunt gebruiken om de inhoud van uw Content Fragments te openen en bij te werken.
exl-id: 84120856-fd1d-40f7-8df4-73d4cdfcc43b
solution: Experience Manager
feature: Headless, Content Fragments, GraphQL API
role: Admin, Architect, Developer
source-git-commit: d8e4fdc4f79e40a43a6845ab083dc231444b9c99
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 0%

---

# Uw inhoud bijwerken via AEM API&#39;s {#update-your-content}

In dit deel van de [ Hoofdloze Reis van de Ontwikkelaar van AEM ](overview.md), leer hoe te om beschikbare APIs te gebruiken om tot de inhoud van uw Fragments van de Inhoud toegang te hebben en bij te werken.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de hoofdloze reis van AEM, [ hoe te om tot Uw Inhoud via de Levering APIs van AEM toegang te hebben ](access-your-content.md) leerde u hoe te om tot uw inhoud zonder kop in AEM via AEM GraphQL API toegang te hebben en u zou nu moeten:

* Een goed begrip van GraphQL.
* Begrijp hoe de AEM GraphQL API werkt.
* Begrijp sommige praktische steekproefvragen.

Dit artikel bouwt verder op deze basisbeginselen, zodat u begrijpt hoe u uw bestaande inhoud zonder kop in AEM kunt bijwerken via de beschikbare API&#39;s.

## Doelstelling {#objective}

* **Publiek**: Geavanceerd
* **Doelstelling**: Leer over APIs beschikbaar om tot de inhoud van uw Fragments van de Inhoud toegang te hebben en bij te werken.

## AEM API&#39;s voor gebruik met inhoudsfragmenten {#aem-apis-for-use-with-content-fragments}

Adobe Experience Manager (AEM) as a Cloud Service biedt meerdere API&#39;s voor zowel gestructureerde inhoudslevering vanuit Content Fragments als contentfragmentbeheer. Zie de afzonderlijke pagina&#39;s voor meer informatie over de specifieke API&#39;s.

* AEM REST OpenAPI voor levering van inhoudsfragmenten
   * Deze API maakt JSON-reacties voor het leveren van gestructureerde inhoud van Content Fragments in AEM.
   * Er wordt een pad naar een inhoudsfragment gebruikt als eindpunt.
   * Deze API is gebaseerd op REST.
   * Deze is geoptimaliseerd voor de levering van inhoud, inclusief CDN-integratie.
* AEM GraphQL API voor levering van inhoudsfragmenten
   * Deze API is gebaseerd op een schema. API-schema&#39;s worden vertegenwoordigd door Content Fragment Models, die de inhoudsstructuur definiëren.
   * Deze API is gebaseerd op GraphQL.
* Content Fragments and Content Fragment Models OpenAPIs
   * Deze API&#39;s zijn bedoeld voor gestructureerd inhoudsbeheer.
   * De respectievelijke GET-operatoren zijn niet geoptimaliseerd voor de levering van inhoud.
   * Deze API is gebaseerd op REST.
* Ondersteuning voor inhoudsfragmenten in de AEM Assets HTTP API
   * De oorspronkelijke API voor de JSON-uitvoer voor gestructureerde levering van inhoud in AEM.
      * Terwijl robuust en bewezen, levert dit API *volledig gehydrateerde* output JSON niet. Verwijzingen worden alleen uitgevoerd als paden, waarvoor secundaire API-aanvragen nodig zijn om verdere inhoud op te halen.
   * De Assets HTTP-API kan ook worden gebruikt voor het beheer van Content Fragments en Content Fragment Models (CRUD).
   * Deze API is gebaseerd op REST.
   * Ondersteuning voor inhoudsfragmenten in Assets HTTP API wordt in de toekomst vervangen, omdat dit wordt opgevolgd door de Edge Delivery Services JSON REST API. Het tijdschema is nog niet vastgesteld.

## Volgende functies {#whats-next}

Nu u dit deel van de AEM Headless Developer Journey hebt voltooid, moet u:

* Begrijp de beschikbare AEM API&#39;s.
* Begrijp hoe de Fragments van de Inhoud in deze APIs worden gesteund.

U zou uw reis zonder kop van AEM door het document [ moeten voortzetten te herzien hoe te om het allen samen te zetten - Uw App en Uw Inhoud in de Zetel van AEM ](put-it-all-together.md) waar u met de de architectuurgrondbeginselen en hulpmiddelen vertrouwd zult worden van AEM u moet gebruiken om uw toepassing samen te zetten.

## Aanvullende bronnen {#additional-resources}

* [ Adobe Experience Manager as a Cloud Service APIs ](https://developer.adobe.com/experience-cloud/experience-manager-apis/)
* [AEM API&#39;s voor gestructureerde levering en beheer van inhoud](/help/headless/apis-headless-and-content-fragments.md)
* [AEM REST OpenAPI voor levering van inhoudsfragmenten](/help/headless/aem-rest-openapi-content-fragment-delivery.md)
* [AEM GraphQL API voor levering van inhoudsfragmenten](/help/headless/graphql-api/content-fragments.md)
* [Content Fragments and Content Fragment Models OpenAPIs](/help/headless/content-fragment-openapis.md)
* [Ondersteuning voor inhoudsfragmenten in de AEM Assets HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md)
* [Werken met inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)
* [ de Componenten van de Kern van AEM ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)
* [ CORS/AEM verklaarde ](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
* [ Video - het Ontwikkelen voor CORS met AEM ](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)
* [Inleiding tot AEM als een CMS zonder kop](/help/headless/introduction.md)
* [ AEM Developer Portal ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [ Leerprogramma&#39;s voor Zwaartepunt in AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)
