---
title: AEM REST OpenAPI voor levering van inhoudsfragmenten
description: Meer informatie over de AEM REST OpenAPI voor het leveren van inhoudsfragmenten
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
source-git-commit: d98aa9d206486022d465ca19c8888088562d56c3
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# AEM REST OpenAPI voor levering van inhoudsfragmenten {#aem-rest-openapi-for-content-fragment-delivery}

>[!IMPORTANT]
>
>Deze API is beschikbaar via het programma voor vroege adoptie.
>
>Om de status te zien, en hoe te om toe te passen als u geinteresseerd bent, controleer de [ Nota&#39;s van de Versie ](/help/release-notes/release-notes-cloud/release-notes-current.md).

In Adobe Experience Manager (AEM) as a Cloud Service, AEM REST OpenAPI voor het leveren van inhoudsfragmenten:

* is een VERTONING API van HTTP op [ AEM Edge Delivery Services ](/help/edge/overview.md), die wordt ontworpen om gestructureerde inhoud van de Fragmenten van de Inhoud in formaat te leveren JSON
* biedt een moderne CDN-integratie die het mogelijk maakt actieve inhoud te valideren
* richt zich op de levering van inhoud (prestaties, scalability, integratie CDN, geoptimaliseerde controle JSON en output)
* bevat de mogelijkheid om JSON te hydrateren voor fragmenten en elementen waarnaar wordt verwezen

Deze API:

* is de opvolger aan [ Steun van de Fragmenten van de Inhoud in AEM Assets HTTP API ](/help/assets/content-fragments/assets-api-content-fragments.md)

* supplementeert de [ Fragmenten van de Inhoud en Modellen van het Fragment van de Inhoud OpenAPIs ](/help/headless/content-fragment-openapis.md), die u toestaan om de Fragmenten van de Inhoud en Modellen van het Fragment van de Inhoud (CRUD) te beheren

* is een alternatief van HTTP REST aan [ AEM GraphQL API voor gebruik met de Fragmenten van de Inhoud ](/help/headless/graphql-api/content-fragments.md)

Voor volledige documentatie zie [ AEM Sites API Schemas - de Levering API van de Fragmenten van de Inhoud (2024.07-experimenteel) ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/sites/delivery/).

>[!NOTE]
>
>Zie [ AEM APIs voor Gestructureerde Inhoudslevering en Beheer ](/help/headless/apis-headless-and-content-fragments.md) voor een overzicht van diverse beschikbare APIs en vergelijking van sommige betrokken concepten.

## Caching {#caching}

AEM integreert snel met de AEM CDN. Dit betekent dat JSON-reacties die op de publicatielaag worden aangeboden, op het snelst niveau in de cache worden geplaatst.

De reacties worden dan caching, gebaseerd op vooraf bepaalde caching kopballen (kan niet worden gevormd):

* Reacties worden gedurende 5 minuten in cache geplaatst in de cache van de browser/client
   * `max-age`=`300`
* Reacties worden gedurende 1 uur in cache geplaatst in de CDN-cache
   * `s-maxage`=`3600`
* Stale inhoud kan gedurende maximaal 1 uur worden gebruikt voor het opnieuw valideren van nieuwe aanvragen
   * `stale-while-revalidate`=`3600`
* Stale inhoud kan per fout maximaal 1 dag worden aangeboden
   * `stale-on-error`=`86400`

AEM wordt ook de actieve CDN-cachevalidatie ondersteund. Dit betekent dat wanneer inhoud wordt bijgewerkt of gepubliceerd, de corresponderende JSON OpenAPI-reacties automatisch ongeldig worden gemaakt via een aanvraag voor het snel wissen van inhoud. Dit staat u toe om veranderingen te zien die in de output JSON worden weerspiegeld, alvorens de daadwerkelijke CDN geheim voorgeheugenpagina (`s-maxage`) wordt bereikt.