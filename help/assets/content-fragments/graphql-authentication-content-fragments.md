---
title: Verificatie voor externe AEM GraphQL-query's op inhoudsfragmenten
description: Begrijp de authentificatie die voor Verre AEM vragen GraphQL wordt vereist om uw inhoud zonder kop te beveiligen.
feature: Inhoudsfragmenten,GrafiekQL API
exl-id: dfeae661-06a1-4001-af24-b52ae12d625f
translation-type: tm+mt
source-git-commit: dab4c9393c26f5c3473e96fa96bf7ec51e81c6c5
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Verificatie voor externe AEM GraphQL-query&#39;s op inhoudsfragmenten {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Een primair gebruiksgeval voor [Adobe Experience Manager als Cloud Service (AEM) GraphQL API voor de Levering van het Fragment van de Inhoud ](/help/assets/content-fragments/graphql-api-content-fragments.md) moet verre vragen van derdetoepassingen of de diensten goedkeuren. Deze externe query&#39;s vereisen mogelijk geverifieerde API-toegang om de levering van inhoud zonder kop te beveiligen.

>[!NOTE]
>
>Voor het testen en de ontwikkeling kunt u tot de AEM API ook direct toegang hebben GraphQL gebruikend [GraphiQL interface](/help/assets/content-fragments/graphql-api-content-fragments.md#graphiql-interface) interface.

Voor authentificatie moet de derdedienst [een Token van de Toegang terugwinnen](#retrieving-access-token), die dan [in het Vraag GraphQL](#use-access-token-in-graphql-request) kan worden gebruikt.

## Een toegangstoken {#retrieving-access-token} ophalen

Zie [Toegangstokens genereren voor server-side API&#39;s](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) voor volledige informatie.

## Het gebruiken van het Token van de Toegang in een Vraag GraphQL {#use-access-token-in-graphql-request}

Voor een derdedienst om met een AEM instantie te verbinden moet het *Token van de Toegang* hebben. De dienst moet dit teken aan `Authorization` kopbal op het verzoek van de POST dan toevoegen.

Bijvoorbeeld een GraphQL-autorisatieheader:

```xml
Authorization: Bearer <access_token>
```

## Machtigingsvereisten {#permission-requirements}

Alle verzoeken die worden gedaan gebruikend het toegangstoken zullen *eigenlijk door de gebruikersrekening worden gemaakt die het token* produceerde.

Dit betekent dat u moet controleren dat de rekening de toestemmingen heeft die worden vereist om vragen in werking te stellen GraphQL.

U kunt dit controleren door GraphiQL op de lokale instantie te gebruiken.
