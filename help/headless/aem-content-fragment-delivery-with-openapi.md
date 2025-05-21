---
title: AEM Content Fragment Delivery with OpenAPI
description: Meer informatie over de levering van tAEM-inhoudsfragmenten met OpenAPI
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
exl-id: b298db37-1033-4849-bc12-7db29fb77777
source-git-commit: 7f7ed3adcbd01f688f48f3ba4a0c25293b8b1551
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# AEM Content Fragment Delivery with OpenAPI {#aem-content-fragment-delivery-with-openapi}

In Adobe Experience Manager (AEM) as a Cloud Service wordt de AEM OpenAPI voor het leveren van inhoudsfragmenten:

* is een OpenAPI die is geoptimaliseerd voor live levering van AEM Content Fragments in JSON-indeling
* biedt een moderne CDN-integratie die het mogelijk maakt actieve inhoud te valideren
* richt zich op de levering van inhoud (prestaties, scalability, integratie CDN, geoptimaliseerde controle JSON en output)
* bevat de mogelijkheid om JSON te hydrateren voor fragmenten en elementen waarnaar wordt verwezen

Deze API:

* is de opvolger aan [ Steun van de Fragmenten van de Inhoud in AEM Assets HTTP API ](/help/assets/content-fragments/assets-api-content-fragments.md)

* supplementeert de [ Fragmenten van de Inhoud en Modellen van het Fragment van de Inhoud OpenAPIs ](/help/headless/content-fragment-openapis.md), die u toestaan om de Fragmenten van de Inhoud en Modellen van het Fragment van de Inhoud (CRUD) te beheren

* is een alternatief van HTTP REST aan [ AEM GraphQL API voor gebruik met de Fragmenten van de Inhoud ](/help/headless/graphql-api/content-fragments.md)

Voor volledige documentatie zie [ de Levering van het Fragment van de Inhoud van AEM met OpenAPI ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/contentfragments/delivery/).

>[!NOTE]
>
>Zie [ AEM APIs voor Gestructureerde Inhoudslevering en Beheer ](/help/headless/apis-headless-and-content-fragments.md) voor een overzicht van diverse beschikbare APIs en vergelijking van sommige betrokken concepten.

## Caching {#caching}

AEM kan snel worden geïntegreerd met de AEM CDN. Dit betekent dat JSON-reacties die op de publicatielaag worden aangeboden, op het snelst niveau in de cache worden geplaatst.

De reacties worden dan caching, gebaseerd op vooraf bepaalde caching kopballen (kan niet worden gevormd):

* Reacties worden gedurende 5 minuten in cache geplaatst in de cache van de browser/client
   * `max-age`=`300`
* Reacties worden gedurende 1 uur in cache geplaatst in de CDN-cache
   * `s-maxage`=`3600`
* Stale inhoud kan gedurende maximaal 1 uur worden gebruikt voor het opnieuw valideren van nieuwe aanvragen
   * `stale-while-revalidate`=`3600`
* Stale inhoud kan per fout maximaal 1 dag worden aangeboden
   * `stale-on-error`=`86400`

AEM wordt ook geleverd met actieve CDN-cachevalidatie. Dit betekent dat wanneer inhoud wordt bijgewerkt of gepubliceerd, de corresponderende JSON OpenAPI-reacties automatisch ongeldig worden gemaakt via een aanvraag voor het snel wissen van inhoud. Dit staat u toe om veranderingen te zien die in de output JSON worden weerspiegeld, alvorens de daadwerkelijke CDN geheim voorgeheugenpagina (`s-maxage`) wordt bereikt.
