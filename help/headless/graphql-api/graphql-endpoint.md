---
title: GrafiekQL-eindpunten beheren in AEM
description: Leer hoe u GraphQL-eindpunten in Adobe Experience Manager as a Cloud Service beheert voor levering van inhoud zonder kop.
feature: Content Fragments,GraphQL API
source-git-commit: 4e37db128aa31d6e8e950be0d077eae921a27468
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---


# GrafiekQL-eindpunten beheren in AEM {#graphql-aem-endpoint}

Het eindpunt is de weg die wordt gebruikt om tot GraphQL voor AEM toegang te hebben. Met dit pad kunt u (of uw app) het volgende doen:

* toegang tot het GraphQL-schema;
* verzend uw vragen GraphQL,
* ontvangt de reacties (op uw vragen GraphQL).

Er zijn twee soorten eindpunten in AEM:

* Algemeen
   * Beschikbaar voor gebruik door alle sites.
   * Dit eindpunt kan alle Modellen van het Fragment van de Inhoud van alle configuraties van Plaatsen gebruiken (die in [Configuratiebrowser](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)).
   * Als er om het even welke Modellen van het Fragment van de Inhoud zijn die onder de configuraties van Plaatsen zouden moeten worden gedeeld, dan zouden deze onder de globale configuraties van Plaatsen moeten worden gecreeerd.
* Siteconfiguraties:
   * Komt overeen met een configuratie Sites, zoals gedefinieerd in het dialoogvenster [Configuratiebrowser](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser).
   * Specifiek voor een opgegeven site/project.
   * Een configuratie-specifiek eindpunt van Plaatsen zal de Modellen van het Fragment van de Inhoud van die specifieke configuratie van Plaatsen samen met die van de globale configuratie van Plaatsen gebruiken.

>[!CAUTION]
>
>Met de Inhoudsfragmenteditor kan een inhoudsfragment van een siteconfiguratie verwijzen naar een inhoudsfragment van een andere siteconfiguratie (via beleid).
>
>In een dergelijk geval zal niet alle inhoud kunnen terugwinnen gebruikend een de configuratie van Plaatsen specifiek eindpunt.
>
>De inhoudauteur zou dit scenario moeten controleren; Het kan bijvoorbeeld handig zijn om gedeelde modellen van inhoudsfragmenten onder de configuratie Algemene sites te plaatsen.

De bewaarplaatspad van GraphQL voor AEM globale eindpunt is:

`/content/cq:graphql/global/endpoint`

Voor welke toepassing uw toepassing het volgende pad in de aanvraag-URL kan gebruiken:

`/content/_cq_graphql/global/endpoint.json`

Om een eindpunt voor GraphQL voor AEM toe te laten moet u:

* [GrafiekQL-eindpunt inschakelen](#enabling-graphql-endpoint)
* [Uw GraphQL-eindpunt publiceren](#publishing-graphql-endpoint)

## GrafiekQL-eindpunt inschakelen {#enabling-graphql-endpoint}

Om een Eindpunt te toelaten GraphQL moet u eerst een aangewezen configuratie hebben. Zie [Inhoudsfragmenten - Configuratiebrowser](/help/assets/content-fragments/content-fragments-configuration-browser.md).

>[!CAUTION]
>
>Als de [gebruik van inhoudsfragmentmodellen is niet ingeschakeld](/help/assets/content-fragments/content-fragments-configuration-browser.md)de **Maken** is niet beschikbaar.

Om het overeenkomstige eindpunt toe te laten:

1. Navigeren naar **Gereedschappen**, **Activa** selecteert u vervolgens **GraphQL**.
1. Selecteer **Maken**.
1. De **Nieuw GraphQL-eindpunt maken** wordt geopend. Hier kunt u opgeven:
   * **Naam**: naam van het eindpunt; U kunt elke gewenste tekst invoeren.
   * **GrafiekQL-schema gebruiken dat is opgegeven door**: Gebruik de vervolgkeuzelijst om de gewenste site of het vereiste project te selecteren.

   >[!NOTE]
   >
   >De volgende waarschuwing wordt weergegeven in het dialoogvenster:
   >
   >* *De eindpunten van GraphQL kunnen gegevensveiligheid en prestatieskwesties introduceren als niet zorgvuldig beheerd. Gelieve te verzekeren om aangewezen toestemmingen te plaatsen na het creëren van een eindpunt.*


1. Bevestigen met **Maken**.
1. De **Volgende stappen** de dialoog zal een directe verbinding aan de console van de Veiligheid verstrekken zodat u kunt ervoor zorgen dat het onlangs gecreeerde eindpunt geschikte toestemmingen heeft.

   >[!CAUTION]
   >
   >Het eindpunt is toegankelijk voor iedereen. Dit kan - vooral bij publiceer instanties - een veiligheidszorg veroorzaken, aangezien de vragen GraphQL een zware lading op de server kunnen opleggen.
   >
   >U kunt opstelling ACLs, aangewezen aan uw gebruiksgeval, op het eindpunt.

## Het Eindpunt GraphQL publiceren {#publishing-graphql-endpoint}

Selecteer het nieuwe eindpunt en **Publiceren** om het volledig beschikbaar te maken in alle milieu&#39;s.

>[!CAUTION]
>
>Het eindpunt is toegankelijk voor iedereen.
>
>Bij het publiceren van instanties kan dit een veiligheidszorg veroorzaken, aangezien de vragen GraphQL een zware lading op de server kunnen opleggen.
>
>U moet instellen [ACLs aangewezen aan uw gebruiksgeval](/help/headless/security/permissions.md) op het eindpunt.