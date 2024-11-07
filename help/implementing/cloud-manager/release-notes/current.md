---
title: Opmerkingen bij de release van Cloud Manager 2024.11.0 in Adobe Experience Manager as a Cloud Service
description: Meer informatie over de release van Cloud Manager 2024.11.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: db661281831dcb07491dca16e73e835b487814a6
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2024.11.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Meer informatie over de release van Cloud Manager 2024.11.0 in AEM (Adobe Experience Manager) as a Cloud Service.

>[!NOTE]
>
>Zie de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Releasedatums {#release-date}

De releasedatum voor Cloud Manager 2024.11.0 in AEM as a Cloud Service is 7 november 2024.

De volgende geplande release is 5 december 2024.

## Nieuwe functies {#what-is-new}

* Ervaar de nieuwste innovaties op het gebied van Edge Delivery Services met AEM Cloud Service-now die u kunt verkennen in uw Sandbox-programma. [ Leer meer ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md#auto-creation) <!-- (CMGR-62319) -->
* De pagina met domeininstellingen in AEM Cloud Manager bevat nu een zoekfunctie waarmee u snel domeinen op naam kunt zoeken. U kunt trefwoorden in het zoekveld invoeren om overeenkomende domeinen te filteren en weer te geven, zodat u meerdere domeinen efficiënter kunt beheren. Bovendien, biedt de pagina statusfilters aan, zoals **Verified** en **niet Verified**, om de onderzoeksresultaten verder te verfijnen. <!-- (CMGR-62615) -->

![ gebied van het Onderzoek in de Montages van het Domein ](/help/implementing/cloud-manager/assets/domain-settings-search.png)

## Programma voor vroegtijdige goedkeuring {#early-adoption}

Maak deel uit van het Cloud Manager-programma voor vroege adoptie en heb de kans om toekomstige functies te testen.

### AEM {#aem-home}

AEM Home is een nieuw, gecentraliseerd startpunt voor het beheer van uw inhoud, middelen en sites in Adobe Experience Manager. AEM Home is ontworpen om gebruikers een persoonlijke ervaring te bieden en helpt hen naadloos door het AEM ecosysteem te navigeren op basis van hun rollen en doelen. Het is ontworpen als uw gids, die zeer belangrijke inzichten en geadviseerde acties aanbieden om gewenste resultaten efficiënt te bereiken. Door een duidelijke, persoonlijke routekaart te presenteren, zorgt AEM Home ervoor dat gebruikers snel kunnen vinden wat ze nodig hebben om hun doelstellingen te bereiken, en zo een gestroomlijnde en effectievere ervaring in alle AEM mogelijkheden ondersteunen.

AEM Home is beschikbaar voor klanten met een vroege adoptie en biedt een eerste blik op een verbeterde ervaring die workflows optimaliseert, prioriteiten stelt aan doelstellingen en resultaten aanstuurt. Door in te gaan, heb je de kans om vorm te geven aan de ontwikkeling van AEM Home, en feedback te geven die zijn evolutie beïnvloedt om de AEM gemeenschap het beste te dienen.

Als u in het testen van dit nieuwe vermogen en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ Grp-AemHome@adobe.com ](mailto:Grp-AemHome@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Zorg ervoor dat u de volgende informatie opneemt:

* De rol die het beste bij uw profiel past: auteur van inhoud, ontwikkelaar, eigenaar van bedrijf, beheerder of andere (geef een beschrijving op).
* Uw primaire AEM toegangsoppervlak: AEM Sites, AEM Assets, AEM Forms, Cloud Manager of Overige (geef een beschrijving op).

### Kies voor uw eigen git - nu met ondersteuning voor GitLab en Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**breng Uw Eigen eigenschap van het Git** is uitgebreid om steun voor externe bewaarplaatsen zoals GitLab en Bitbucket te omvatten. Deze nieuwe steun is naast reeds bestaande steun voor privé en ondernemingsbewaarplaatsen GitHub. Wanneer u deze nieuwe repo&#39;s toevoegt, kunt u deze ook rechtstreeks aan uw pijpleidingen koppelen. U kunt deze opslagruimten hosten op openbare cloudplatforms of binnen uw privécloud of infrastructuur. Deze integratie verwijdert ook de behoefte aan constante codesynchronisatie met de opslagplaats van de Adobe en verstrekt de capaciteit om trekkingsverzoeken te bevestigen alvorens hen in een hoofdtak samen te voegen.

Zie [ externe bewaarplaatsen in Cloud Manager ](/help/implementing/cloud-manager/managing-code/external-repositories.md) toevoegen.

![ voeg de dialoogdoos van de Bewaarplaats ](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png) toe

>[!NOTE]
>
>Momenteel, zijn de uit-van-de-doos controles van de trekkingsverzoekcodekwaliteit exclusief aan GitHub-ontvangen bewaarplaatsen, maar een update om deze functionaliteit tot andere verkopers van het Git uit te breiden is in de werken.

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ Grp-CloudManager_BYOG@adobe.com ](mailto:Grp-CloudManager_BYOG@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Zorg ervoor dat u ook het Git-platform opgeeft dat u wilt gebruiken en dat u zich in een opslagstructuur van een privéserver, een openbare opslagruimte of een bedrijfsopslagruimte bevindt. —>


## Bugfixes

* Een recente update verhelpt een probleem in SonarQube waarbij in bepaalde gevallen hardcoded wachtwoorden niet werden gedetecteerd. De correctie bevat nu een uitgebreide patrooncontrole en wordt uitgelijnd op de standaarddetectienormen in SonarQube. <!-- CMGR-62682 -->
* Wanneer u probeert een SSL-certificaat bij te werken in Cloud Manager, wordt een onbekende fout weergegeven nadat u op **[!UICONTROL Update]** in het dialoogvenster **[!UICONTROL View & Update SSL Certificate]** hebt geklikt. <!-- CMGR-62848 -->
* In Cloud Manager zouden updates van SSL-certificaten mislukken met de fout &quot;Het nieuwe certificaat komt niet overeen met de bestaande domeinen&quot;, zelfs als de domeinen identiek waren maar verschillen in hoofdletters of kleine letters hadden. In de update worden domeinen nu herkend als hoofdlettergevoelig, uitgelijnd op RFC-standaarden. <!-- CMGR-62844 -->
* In Cloud Manager, bleven IP de banden van de Lijst van gewenste personen in een lopende staat vastzitten omdat de buitenlandse zeer belangrijke verbindingen aan domeinconfiguraties ontbraken. De moeilijke situatie verzekert nu IP de bindingen van de Lijst van gewenste personen correct met bijbehorende domeinconfiguraties. <!-- CMGR-62838 -->
* Cloud Manager valideert de OCSP-status (Online Certificate Status Protocol) van een SSL-certificaat. Adobe raadt u aan om de integriteit van uw certificaat ook lokaal te valideren met een hulpprogramma zoals `openssl verify -untrusted intermediate.pem certificate.pem` voordat u het certificaat installeert via Cloud Manager. Voor meer details, zie de [ SSL documentatie van certificaatvereisten ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/introduction-to-ssl-certificates#requirements). <!-- CMGR-62341  -->



<!-- ## Known issues {#known-issues} -->