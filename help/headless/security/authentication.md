---
title: Verificatie voor externe AEM GraphQL-query's op inhoudsfragmenten
description: Begrijp de vereiste verificatie voor externe Adobe Experience Manager GraphQL-query's om de levering van inhoud zonder kop te beveiligen.
feature: Content Fragments,GraphQL API
exl-id: dfeae661-06a1-4001-af24-b52ae12d625f
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Verificatie voor externe AEM GraphQL-query&#39;s op inhoudsfragmenten {#authentication-for-remote-aem-graphql-queries-on-content-fragments}

Een hoofdgebruik voor het [Adobe Experience Manager as a Cloud Service (AEM) GraphQL API voor levering van inhoudsfragmenten](/help/headless/graphql-api/content-fragments.md) moet verre vragen van derdetoepassingen of de diensten goedkeuren. Deze externe query&#39;s vereisen mogelijk geverifieerde API-toegang om de levering van inhoud zonder kop te beveiligen.

>[!NOTE]
>
>Voor test- en ontwikkelingsdoeleinden hebt u ook rechtstreeks toegang tot de AEM GraphQL API via de [GraphiQL-interface](/help/headless/graphql-api/graphiql-ide.md).

Voor authentificatie, moet de derdedienst [een toegangstoken ophalen](#retrieving-access-token) dat kan [gebruikt in de GraphQL-aanvraag](#use-access-token-in-graphql-request).

## Een toegangstoken ophalen {#retrieving-access-token}

Zie [Toegangstokens genereren voor server-side API&#39;s](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) voor volledige informatie.

## Het gebruiken van het Token van de Toegang in een GraphQL- Verzoek {#use-access-token-in-graphql-request}

Een service van derden kan alleen verbinding maken met een AEM instantie als deze een *Toegangstoken*. De dienst moet dit teken aan de `Authorization` header on the POST request.

Een GraphQL-autorisatieheader bijvoorbeeld:

```xml
Authorization: Bearer <access_token>
```

## Machtigingsvereisten {#permission-requirements}

Alle verzoeken die met behulp van het toegangstoken worden gedaan worden gemaakt *door de gebruikersaccount die het token heeft gegenereerd*.

Dit gebruikersaccount houdt in dat u moet controleren of de account de machtigingen heeft die vereist zijn om GraphQL-query&#39;s uit te voeren.

U kunt deze toestemmingen controleren door GraphiQL op de lokale instantie te gebruiken. Meer informatie over [hier kunt u rechten vinden](/help/headless/security/permissions.md).
