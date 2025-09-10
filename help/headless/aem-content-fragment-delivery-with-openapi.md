---
title: AEM Content Fragment Delivery with OpenAPI
description: Meer informatie over de levering van tAEM-inhoudsfragmenten met OpenAPI
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
exl-id: b298db37-1033-4849-bc12-7db29fb77777
source-git-commit: de161d6707dcb8cedf032ee1f286d79e733be94d
workflow-type: tm+mt
source-wordcount: '607'
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

>[!IMPORTANT]
>
>Om de Levering van het Fragment van de Inhoud met OpenAPI op AEM as a Cloud Service toe te laten gelieve ervoor te zorgen dat het niet reeds wordt toegelaten, dan een kaartje van de Steun van Adobe met de titel **laat de Levering van het Fragment van de Inhoud met OpenAPI** toe en het specificeren:
>
>* het Cloud Service-programma en de milieu-id(&#39;s)
>* details van de gebruikscase die u wilt oplossen met de Content Fragment Delivery OpenAPI
>* details van al uw contacten waarop Adobe zou moeten antwoorden, en van het verzoek op de hoogte houden, en project (indien vereist)

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

Inhoudsfragmentlevering met OpenAPI ondersteunt actieve CDN-cachevalidatie. Dit betekent dat wanneer inhoud wordt bijgewerkt of gepubliceerd, de corresponderende JSON OpenAPI-reacties automatisch ongeldig worden gemaakt via een aanvraag voor het snel wissen van inhoud. Dit staat u toe om veranderingen te zien die in de output JSON worden weerspiegeld, alvorens de daadwerkelijke CDN geheim voorgeheugenpagina (`s-maxage`) wordt bereikt.

## Beschikbaarheid {#availability}

De levering van inhoudsfragmenten met OpenAPI is beschikbaar op de niveaus Voorbeeld en Publiceren. De OpenAPI biedt Content Fragments in JSON-indeling, voor zowel voorvertoning als live levering.

Voor een voorvertoning kan de levering van inhoudsfragmenten met OpenAPI:

* publiceren naar voorvertoning
* laat toegang tot voorproef met IP lijst van gewenste personen toe
* URL voorvertoning ophalen

## CORS {#cors}

[ CORS toegestane oorsprong ](/help/headless/deployment/cross-origin-resource-sharing.md) bepaalt de oorsprong die API kan roepen.

De toegestane oorsprong van CORS aan de kant van de verzendersconfiguratie, specifiek voor GraphQL, wordt niet in aanmerking genomen door deze API.

## Limieten voor API-snelheden {#api-rate-limits}

De API maakt nieuwe aanvragen mogelijk met een snelheid van maximaal 200 aanvragen per seconde, per omgeving.

Zodra deze grens wordt overschreden, begint API [ 429 fout ](https://www.rfc-editor.org/rfc/rfc6585#section-4) reacties te verzenden. Deze fouten moeten door om het even welke cliënttoepassingen worden behandeld, en ontbroken verzoeken die na een exponentiële backoff opnieuw worden geprobeerd. De HTTP-reactie wordt geleverd met een specifieke header, `Retry-After` , die aan de client aangeeft hoelang ze moeten wachten voordat ze de aanvraag opnieuw verzenden.

## Voor authentiek verklaarde Verzoeken {#authenticated-requests}

De steun voor voor authentiek verklaarde verzoeken kan met de [ sleutel van AEM CDN Edge ](/help/implementing/dispatcher/cdn-credentials-authentication.md) worden uitgevoerd. Met de AEM CDN Edge-sleutel kunt u vertrouwen op de AEM CDN en ervoor zorgen dat alleen specifieke aanvragen toegang hebben tot de API, op basis van de opgegeven Edge-sleutelheader.

>[!NOTE]
>
>De vergunning die op bewaarplaats-specifieke ACLs wordt gebaseerd wordt momenteel niet gesteund.

<!-- 
## Limitations {#limitations}
-->
