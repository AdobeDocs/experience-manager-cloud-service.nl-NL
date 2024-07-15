---
title: Verificatie voor externe AEM GraphQL-query's op inhoudsfragmenten
description: Begrijp de vereiste verificatie voor externe Adobe Experience Manager GraphQL-query's om de levering van inhoud zonder kop te beveiligen.
feature: Headless, Content Fragments,GraphQL API
exl-id: dfeae661-06a1-4001-af24-b52ae12d625f
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Verificatie voor externe AEM GraphQL-query&#39;s op inhoudsfragmenten {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Een primair gebruiksgeval voor [ Adobe Experience Manager as a Cloud Service (AEM) GraphQL API voor de Levering van het Fragment van de Inhoud ](/help/headless/graphql-api/content-fragments.md) moet verre vragen van derdetoepassingen of de diensten goedkeuren. Deze externe query&#39;s vereisen mogelijk geverifieerde API-toegang om de levering van inhoud zonder kop te beveiligen.

>[!NOTE]
>
>Voor het testen en de ontwikkeling, kunt u tot de AEM GraphQL API direct ook toegang hebben gebruikend de [ interface GraphiQL ](/help/headless/graphql-api/graphiql-ide.md).

Voor authentificatie, moet de derdedienst [ een Symbolisch van de Toegang ](#retrieving-access-token) terugwinnen dat dan [ in het Verzoek van GraphQL ](#use-access-token-in-graphql-request) kan worden gebruikt.

## Een toegangstoken ophalen {#retrieving-access-token}

Zie [ Genererend de Tokens van de Toegang voor server-Kant APIs ](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) voor volledige details.

## Het gebruiken van het Token van de Toegang in een GraphQL- Verzoek {#use-access-token-in-graphql-request}

Voor de derdedienst om met een AEM instantie te verbinden moet het een *Symbolisch van de Toegang* hebben. De service moet dit token vervolgens toevoegen aan de header `Authorization` als de POST wordt aangevraagd.

Een GraphQL-autorisatieheader bijvoorbeeld:

```xml
Authorization: Bearer <access_token>
```

## Machtigingsvereisten {#permission-requirements}

Alle die verzoeken worden gemaakt gebruikend het toegangstoken worden gemaakt *door de gebruikersrekening die het teken* produceerde.

Dit gebruikersaccount houdt in dat u moet controleren of de account de machtigingen heeft die vereist zijn om GraphQL-query&#39;s uit te voeren.

U kunt deze toestemmingen controleren door GraphiQL op de lokale instantie te gebruiken. Meer details over [ toestemmingen kunnen hier ](/help/headless/security/permissions.md) worden gevonden.
