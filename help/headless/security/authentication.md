---
title: Verificatie voor externe AEM GraphQL-query's op inhoudsfragmenten
description: Begrijp de authentificatie die voor Verre AEM vragen GraphQL wordt vereist om uw inhoud zonder kop te beveiligen.
feature: Content Fragments,GraphQL API
exl-id: dfeae661-06a1-4001-af24-b52ae12d625f
source-git-commit: 4e37db128aa31d6e8e950be0d077eae921a27468
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Verificatie voor externe AEM GraphQL-query&#39;s op inhoudsfragmenten {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Een hoofdgebruik voor het [Adobe Experience Manager as a Cloud Service (AEM) GraphQL API voor levering van inhoudsfragmenten](/help/headless/graphql-api/content-fragments.md) moet verre vragen van derdetoepassingen of de diensten goedkeuren. Deze externe query&#39;s vereisen mogelijk geverifieerde API-toegang om de levering van inhoud zonder kop te beveiligen.

>[!NOTE]
>
>Voor testen en ontwikkeling kunt u ook rechtstreeks toegang krijgen tot de AEM GraphQL API [GraphiQL-interface](/help/headless/graphql-api/graphiql-ide.md) interface.

Voor verificatie moet de service van derden [een toegangstoken ophalen](#retrieving-access-token), die dan [gebruikt in het GraphQL-verzoek](#use-access-token-in-graphql-request).

## Een toegangstoken ophalen {#retrieving-access-token}

Zie [Toegangstokens genereren voor server-side API&#39;s](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) voor volledige informatie.

## Het gebruiken van het Token van de Toegang in een Vraag GraphQL {#use-access-token-in-graphql-request}

Een service van derden kan alleen verbinding maken met een AEM instantie als deze een *Toegangstoken*. De dienst moet dit teken aan de `Authorization` header on the POST request.

Bijvoorbeeld een GraphQL-autorisatieheader:

```xml
Authorization: Bearer <access_token>
```

## Machtigingsvereisten {#permission-requirements}

Alle verzoeken die met behulp van het toegangstoken worden gedaan zullen eigenlijk worden gemaakt *door de gebruikersaccount die het token heeft gegenereerd*.

Dit betekent dat u moet controleren dat de rekening de toestemmingen heeft die worden vereist om vragen in werking te stellen GraphQL.

U kunt dit controleren door GraphiQL op de lokale instantie te gebruiken. Meer informatie over [hier kunt u rechten vinden](/help/headless/security/permissions.md).
