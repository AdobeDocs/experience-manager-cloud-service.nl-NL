---
title: Dispatcher-eindpuntconfiguratie met AEM headless
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

[ Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) is een caching en veiligheidslaag voor de milieu&#39;s van Adobe Experience Manager Publish. Verschillende configuraties zijn standaard inbegrepen bij het openen van GraphQL-eindpunten voor toepassingen zonder kop.

>[!NOTE]
>
>Voor gedetailleerde documentatie over Dispatcher, zie de [ Gids van Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html).

Als deel van een AEM Project is een module van Dispatcher inbegrepen die configuraties voor Dispatcher bevat. Nieuw geproduceerde projecten van het [ AEM Archetype van het Project ](https://github.com/adobe/aem-project-archetype) omvatten automatisch [ filters ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?#defining-a-filter) die eindpunten van GraphQL toelaten.

## GraphQL-eindpunten

Als deel van de standaardfilters, [ GraphQL endpoints ](/help/headless/graphql-api/graphql-endpoint.md) worden geopend met de volgende regel:

```
/0060 { /type "allow" /method '(POST|OPTIONS)' /url "/content/_cq_graphql/*/endpoint.json" }
```

Het jokerteken `*` opent meerdere eindpunten van de AEM. Het vragen gebruikend een eindpunt van GraphQL wordt gemaakt gebruikend `POST` en de reactie is **niet** caching.

## Aangehouden GraphQL-query&#39;s

Het verzoek om Persisted query wordt ingediend tegen een verschillend eindpunt. Als deel van de standaardfilterconfiguratie, wordt url voor [ Gepersisteerde vragen ](/help/headless/graphql-api/persisted-queries.md) geopend met de volgende regel:

```
/0061 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
```

U kunt blijvende query&#39;s aanvragen met `GET` door de reactie in de cache op Dispatcher- en CDN-niveau te plaatsen. Meer details over caching en geheim voorgeheugenongeldigverklaring kunnen [ hier ](/help/implementing/dispatcher/caching.md) worden gevonden.
