---
title: AEM API's voor gestructureerde levering van inhoud en beheer van contentfragmenten
description: Meer informatie over de API's die beschikbaar zijn voor Gestructureerde levering van inhoud en beheer van contentfragmenten
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
exl-id: 95aecd30-566a-42a9-b97a-7efe45fd389c
source-git-commit: d9db32110e1e0aaa5bdc20bd6b4bff6da6a3a3a3
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# AEM API&#39;s voor gestructureerde levering en beheer van inhoud {#aem-apis-structured-content-delivery-and-management}

Adobe Experience Manager (AEM) as a Cloud Service biedt meerdere API&#39;s voor zowel gestructureerde inhoudslevering vanuit Content Fragments als contentfragmentbeheer. Zie de afzonderlijke pagina&#39;s voor meer informatie over de specifieke API&#39;s.

* [AEM Content Fragment Delivery with OpenAPI](/help/headless/aem-content-fragment-delivery-with-openapi.md)
   * Deze API maakt JSON-reacties voor het leveren van gestructureerde inhoud van Content Fragments in AEM.
   * Er wordt een pad naar een inhoudsfragment gebruikt als eindpunt.
   * Deze API is gebaseerd op REST.
   * Deze is geoptimaliseerd voor de levering van inhoud, inclusief CDN-integratie.
* [AEM GraphQL API voor levering van inhoudsfragmenten](/help/headless/graphql-api/content-fragments.md)
   * Deze API is gebaseerd op een schema. API-schema&#39;s worden vertegenwoordigd door Content Fragment Models, die de inhoudsstructuur definiëren.
   * Deze API is gebaseerd op GraphQL.
* [Content Fragments and Content Fragment Models OpenAPIs](/help/headless/content-fragment-openapis.md)
   * Deze API&#39;s zijn bedoeld voor gestructureerd inhoudsbeheer.
   * De respectievelijke GET-operatoren zijn niet geoptimaliseerd voor de levering van inhoud.
   * Deze API is gebaseerd op REST.
* [Ondersteuning voor inhoudsfragmenten in de AEM Assets HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md)
   * De oorspronkelijke API voor de JSON-uitvoer voor gestructureerde levering van inhoud in AEM.
      * Terwijl robuust en bewezen, levert dit API *volledig gehydrateerde* output JSON niet. Verwijzingen worden alleen uitgevoerd als paden, waarvoor secundaire API-aanvragen nodig zijn om verdere inhoud op te halen.
   * De Assets HTTP-API kan ook worden gebruikt voor het beheer van Content Fragments en Content Fragment Models (CRUD).
   * Deze API is gebaseerd op REST.
   * Ondersteuning voor inhoudsfragmenten in Assets HTTP API wordt in de toekomst vervangen, omdat dit wordt opgevolgd door de Edge Delivery Services JSON REST API. Het tijdschema is nog niet vastgesteld.

<!--
## JSON vs HTML {#json-vs-HTML}

The content delivery format used is driven by frontend implementation. Unstructured content/HTML for full-stack implementations, structured content/JSON for headless implementations, or a combination of both in hybrid implementations. 

Key considerations include:

* Definition
  * JSON (JavaScript Object Notation) - used to represent, access and process structured data. 
  * HTML (HyperText Markup Language) - a markup language of tags and elements in a hierarchical structure.
* Primary Purpose
  * JSON is often used for transferring structure content between the server and client app.
  * HTML is the standard markup language for creating and rendering web pages in a browser.
-->

## REST vs GraphQL {#rest-vs-graphql}

De gebruikte API is een beslissing voor de ontwikkelaars - AEM ondersteunt beide.

Er zijn veel vergelijkingen online beschikbaar, maar een aantal hooglichten en voordelen van REST zijn onder meer:

* Eenvoud

   * Ontwikkelaars zijn (vaak) vertrouwd met HTTP en REST. Volgens de [ Staat van Postman van het APIs- rapport ](https://www.postman.com/state-of-api/), gebruikt een hoog percentage ontwikkelaars REST.

   * Met eenvoud komt vertrouwdheid. Met REST zijn er geen organisatorische vragen over wie de query&#39;s bezit en wie de app bezit, terwijl deze vragen bij GraphQL kunnen rijzen.

   * Met (typisch) vertrouwdheid komt een brede gemeenschap en toolend landschap. Geen inherent nadeel van GraphQL, maar waarschijnlijk breder en dieper voor REST.

   * De eenvoudigere benadering kan de veiligheidsimplementatie ook vergemakkelijken. Met REST gebeurt het filteren om te bepalen welke inhoud moet worden gerenderd in de client-app. Met GraphQL gebeurt dit in een op schema gebaseerde query tussen client en server.

* Flexibiliteit

   * Met REST kan de ontwikkelaar `GET` elke bron. Met GraphQL zijn ze beperkt tot resources die binnen een schema zijn gedefinieerd.

* Caching

   * JSON-reacties op REST `GET` -verzoeken kunnen van nature in cache worden geplaatst. GraphQL `POST` verzoeken zijn niet cacheable, tenzij zij worden gemaakt; bijvoorbeeld, door AEM te gebruiken Persisted Vragen die op de server worden opgeslagen en met REST-als `GET` verzoeken worden gevraagd.

De voordelen van GraphQL zijn onder meer:

* Efficiëntie van de levering van inhoud

   * Focus

      * Met GraphQL-clienttoepassingen kunnen ze exact de inhoud aanvragen die ze nodig hebben voor rendering, en niet meer. Deze benadering voorkomt overlevering van inhoud, met bovenmatige opslagkosten van inhoud en onnodig bandbreedteverbruik.

   * Enkel eindpunt

      * Terwijl in REST is elk API verzoek een eindpunt, in GraphQL is er slechts één gemeenschappelijk eindpunt, en de verschillende inhoudsverzoeken worden uitgedrukt als vragen gebruikend dat gemeenschappelijke eindpunt.

* Snelle prototypen

   * Met GraphQL is dit een proces in één stap, samengebracht in de GraphQL query, en kan het maken van prototypen eenvoudiger maken. REST daarentegen is een proces in twee stappen:

      1. Inhoud ophalen met API.
      2. In het JSON-antwoord bepaalt u wat u wilt gebruiken voor rendering in de client-app.
