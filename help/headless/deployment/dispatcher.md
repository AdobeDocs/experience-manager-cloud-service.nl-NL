---
title: Dispatcher-eindpuntconfiguratie met AEM headless
description: De Dispatcher is een caching- en beveiligingslaag voor Adobe Experience Manager Publish-omgevingen. Verschillende configuraties worden gebruikt om GraphQL-eindpunten te openen voor toepassingen zonder kop.
feature: Headless, Dispatcher, GraphQL API
exl-id: 78a20021-910f-4cf0-87bf-6e2223994f76
role: Admin, Developer
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# Dispatcher - Eindpuntconfiguratie met AEM headless

[&#x200B; Dispatcher &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=nl-NL) is een caching en veiligheidslaag voor de milieu&#39;s van Adobe Experience Manager Publish. Verschillende configuraties zijn standaard inbegrepen bij het openen van GraphQL-eindpunten voor toepassingen zonder kop.

>[!NOTE]
>
>Voor gedetailleerde documentatie over Dispatcher, zie de [&#x200B; Gids van Dispatcher &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=nl-NL).

Als deel van een AEM Project is een module van Dispatcher inbegrepen die configuraties voor Dispatcher bevat. Nieuw geproduceerde projecten van het [&#x200B; AEM Archetype van het Project &#x200B;](https://github.com/adobe/aem-project-archetype) omvatten automatisch [&#x200B; filters &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=nl-NL&#defining-a-filter) die eindpunten van GraphQL toelaten.

## GraphQL-eindpunten

Als deel van de standaardfilters, [&#x200B; GraphQL endpoints &#x200B;](/help/headless/graphql-api/graphql-endpoint.md) worden geopend met de volgende regel:

```
/0060 { /type "allow" /method '(POST|OPTIONS)' /url "/content/_cq_graphql/*/endpoint.json" }
```

Het jokerteken `*` opent meerdere eindpunten van de AEM. Het vragen gebruikend een eindpunt van GraphQL wordt gemaakt gebruikend `POST` en de reactie is **niet** caching.

## Aangehouden GraphQL-query&#39;s

Het verzoek om Persisted query wordt ingediend tegen een verschillend eindpunt. Als deel van de standaardfilterconfiguratie, wordt url voor [&#x200B; Gepersisteerde vragen &#x200B;](/help/headless/graphql-api/persisted-queries.md) geopend met de volgende regel:

```
/0061 { /type "allow" /method '(GET|POST|OPTIONS)' /url "/graphql/execute.json*" }
```

U kunt blijvende query&#39;s aanvragen met `GET` door de reactie in de cache op Dispatcher- en CDN-niveau te plaatsen. Meer details over caching en geheim voorgeheugenongeldigverklaring kunnen onder [&#x200B; worden gevonden Inleiding aan Caching in AEM as a Cloud Service &#x200B;](/help/implementing/dispatcher/caching.md).
