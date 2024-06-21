---
title: De eindpuntconfiguratie van de verzending met AEM Zwaartepunt
description: De Dispatcher is een caching- en beveiligingslaag voor Adobe Experience Manager Publish-omgevingen. Verschillende configuraties worden gebruikt om GraphQL-eindpunten te openen voor toepassingen zonder kop.
feature: Headless, Dispatcher, GraphQL API
exl-id: 78a20021-910f-4cf0-87bf-6e2223994f76
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---


# Dispatcher - Eindpuntconfiguratie met AEM headless

De [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) is een caching- en beveiligingslaag voor Adobe Experience Manager Publish-omgevingen. Verschillende configuraties zijn standaard inbegrepen bij het openen van GraphQL-eindpunten voor toepassingen zonder kop.

>[!NOTE]
>
>Voor gedetailleerde documentatie over de Dispatcher raadpleegt u de [Handleiding voor verzending](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html).

Als deel van een AEM Project is een module van de Verzender inbegrepen die configuraties voor de Verzender bevat. Nieuw gegenereerde projecten van de [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype) automatisch opnemen [filters](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?#defining-a-filter) die GraphQL-eindpunten mogelijk maken.

## GraphQL-eindpunten

Als onderdeel van de standaardfilters, [GraphQL-eindpunten](/help/headless/graphql-api/graphql-endpoint.md) worden geopend met de volgende regel:

```
/0060 { /type "allow" /method '(POST|OPTIONS)' /url "/content/_cq_graphql/*/endpoint.json" }
```

De `*` jokerteken opent meerdere eindpunten van de AEM-instantie. Het vragen gebruikend een eindpunt van GraphQL wordt gemaakt gebruikend `POST` en de reactie is **niet** in cache geplaatst.

## Aangehouden GraphQL-query&#39;s

Het verzoek om Persisted query wordt ingediend tegen een verschillend eindpunt. Als deel van de standaardfilterconfiguratie, url voor [Blijvende query&#39;s](/help/headless/graphql-api/persisted-queries.md) wordt geopend met de volgende regel:

```
/0061 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
```

U kunt blijvende query&#39;s aanvragen met `GET`, door de reactie op Dispatcher en CDN-niveau in de cache op te nemen. Meer informatie over caching en cachevalidatie vindt u [hier](/help/implementing/dispatcher/caching.md).
