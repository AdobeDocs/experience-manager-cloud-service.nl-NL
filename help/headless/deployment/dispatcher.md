---
title: Dispatcher-configuratie met AEM headless
description: De Dispatcher is een caching- en beveiligingslaag voor Adobe Experience Manager-publicatieomgevingen. Verscheidene configuraties worden gebruikt om eindpunten GraphQL aan toepassingen zonder kop te openen.
feature: Dispatcher, GraphQL API
exl-id: 78a20021-910f-4cf0-87bf-6e2223994f76
source-git-commit: 9bfb5bc4b340439fcc34e97f4e87d711805c0d82
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Dispatcher-configuratie met AEM headless

De [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) is een caching- en beveiligingslaag voor Adobe Experience Manager Publish-omgevingen. Verscheidene configuraties zijn inbegrepen door gebrek om eindpunten GraphQL aan toepassingen zonder kop te openen.

>[!NOTE]
>
>Voor gedetailleerde documentatie over de Dispatcher raadpleegt u de [Handleiding voor verzending](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html)

Als deel van een AEM Project is een verzender module inbegrepen die configuraties voor de verzender bevat. Nieuw gegenereerde projecten van de [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype) automatisch opnemen [filters](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?#defining-a-filter) dat de eindpunten GraphQL toelaat.

## GraphQL-eindpunt(en)

Als onderdeel van de standaardfilters, [GraphQL-eindpunten](/help/headless/graphql-api/graphql-endpoint.md) worden geopend met de volgende regel:

```
/0060 { /type "allow" /method '(POST|OPTIONS)' /url "/content/_cq_graphql/*/endpoint.json" }
```

De `*` jokerteken opent meerdere eindpunten van de AEM-instantie. Het vragen gebruikend een eindpunt GraphQL zal worden gemaakt gebruikend `POST` en de reactie **niet** in cache worden geplaatst.

## GrafiekQL Blijvende query&#39;s

Het verzoek om Persisted vragen wordt gemaakt tegen een verschillend eindpunt. Als deel van de standaardfilterconfiguratie, url voor [Blijvende query&#39;s](/help/headless/graphql-api/persisted-queries.md) worden geopend met de volgende regel:

```
/0061 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
```

U kunt blijvende query&#39;s aanvragen met `GET`, waarbij de reactie op Dispatcher- en CDN-niveau in de cache wordt geplaatst. Meer informatie over caching en cachevalidatie vindt u [hier](/help/implementing/dispatcher/caching.md).
