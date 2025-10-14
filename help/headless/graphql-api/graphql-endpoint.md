---
title: GraphQL-eindpunten beheren in AEM
description: Leer hoe u GraphQL-eindpunten in Adobe Experience Manager as a Cloud Service beheert voor levering van inhoud zonder kop.
feature: Headless, Content Fragments,GraphQL API
exl-id: f7164ae3-4074-4db7-8c43-a79cc2ef00b1
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# GraphQL-eindpunten beheren in AEM {#graphql-aem-endpoint}

Het eindpunt is het pad dat wordt gebruikt om toegang te krijgen tot GraphQL voor AEM. Met dit pad kunt u (of uw app) het volgende doen:

* toegang tot het GraphQL-schema;
* je GraphQL query&#39;s sturen,
* de antwoorden ontvangen (op je GraphQL-vragen).

Er zijn twee soorten eindpunten in AEM:

* Algemeen
   * Beschikbaar voor gebruik door alle sites.
   * Dit eindpunt kan alle Modellen van het Fragment van de Inhoud van alle configuraties van Plaatsen gebruiken (die in [&#x200B; Browser van de Configuratie &#x200B;](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser) worden bepaald).
   * Als er om het even welke Modellen van het Fragment van de Inhoud zijn die onder de configuraties van Plaatsen zouden moeten worden gedeeld, dan zouden deze onder de globale configuraties van Plaatsen moeten worden gecreeerd.
* Siteconfiguraties:
   * Komt overeen met een configuratie van Plaatsen, zoals die in [&#x200B; Browser van de Configuratie &#x200B;](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser) wordt bepaald.
   * Specifiek voor een opgegeven site/project.
   * Een configuratie-specifiek eindpunt van Plaatsen zal de Modellen van het Fragment van de Inhoud van die specifieke configuratie van Plaatsen samen met die van de globale configuratie van Plaatsen gebruiken.

>[!CAUTION]
>
>Met de Inhoudsfragmenteditor kan een inhoudsfragment van een siteconfiguratie verwijzen naar een inhoudsfragment van een andere siteconfiguratie (via beleid).
>
>In zulk een geval, is niet alle inhoud terugwinnbaar gebruikend een de configuratie van Plaatsen specifiek eindpunt.
>
>De inhoudauteur zou dit scenario moeten controleren; bijvoorbeeld, kan het nuttig zijn om het plaatsen van gedeelde Modellen van het Fragment van de Inhoud onder de Globale configuratie van Plaatsen te overwegen.

Het pad naar de gegevensopslagruimte van de GraphQL voor AEM globale eindpunt is:

`/content/cq:graphql/global/endpoint`

Voor welke toepassing uw toepassing het volgende pad in de aanvraag-URL kan gebruiken:

`/content/_cq_graphql/global/endpoint.json`

Om een eindpunt voor GraphQL voor AEM toe te laten moet u:

* [GraphQL-eindpunt inschakelen](#enabling-graphql-endpoint)
* [Publish your GraphQL Endpoint](#publishing-graphql-endpoint)

## GraphQL Endpoint inschakelen {#enabling-graphql-endpoint}

Om een Eindpunt van GraphQL toe te laten moet u eerst een aangewezen configuratie hebben. Zie [&#x200B; de Fragmenten van de Inhoud - Browser van de Configuratie &#x200B;](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser).

>[!CAUTION]
>
>Als het [&#x200B; gebruik van de modellen van het inhoudsfragment niet &#x200B;](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser) is toegelaten, **creeer** optie zal niet beschikbaar zijn.

Om het overeenkomstige eindpunt toe te laten:

1. Navigeer aan **Hulpmiddelen**, **Algemeen**, dan uitgezocht **GraphQL**.
1. Selecteer **creeer**.
1. **creeer nieuwe de dialoog van het Eindpunt van GraphQL** opent. Hier kunt u opgeven:
   * **Naam**: naam van het eindpunt; u kunt om het even welke tekst ingaan.
   * **schema van GraphQL van het Gebruik door** wordt verstrekt: gebruik de drop-down lijst om de vereiste plaats/het project te selecteren dat.

   >[!NOTE]
   >
   >De volgende waarschuwing wordt weergegeven in het dialoogvenster:
   >
   >* *de eindpunten van GraphQL kunnen gegevensveiligheid en prestatieskwesties introduceren als niet zorgvuldig beheerd. Zorg ervoor dat de aangewezen toestemmingen na het creëren van een eindpunt worden geplaatst.*

1. Bevestig met **creeer**.
1. De **Volgende stappen** dialoog zal een directe verbinding aan de console van de Veiligheid verstrekken zodat u kunt verzekeren dat het gecreeerde eindpunt geschikte toestemmingen heeft.

   >[!CAUTION]
   >
   >Het eindpunt is toegankelijk voor iedereen. Dit kan - vooral bij publicatieinstanties - een veiligheidszorg veroorzaken, aangezien de vragen van GraphQL een zware lading op de server kunnen opleggen.
   >
   >U kunt opstelling ACLs, aangewezen aan uw gebruiksgeval, op het eindpunt.

## GraphQL Endpoint publiceren {#publishing-graphql-endpoint}

Selecteer het nieuwe eindpunt en **Publish** om het volledig beschikbaar te maken in alle milieu&#39;s.

>[!CAUTION]
>
>Het eindpunt is toegankelijk voor iedereen.
>
>Bij het publiceren van instanties kan dit een veiligheidszorg veroorzaken, aangezien de vragen van GraphQL een zware lading op de server kunnen opleggen.
>
>Opstelling [&#x200B; ACLs aangewezen aan uw gebruiksgeval &#x200B;](/help/headless/security/permissions.md) op het eindpunt.
