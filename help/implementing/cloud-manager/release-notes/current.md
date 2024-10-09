---
title: Opmerkingen bij de release van Cloud Manager 2024.10.0 in Adobe Experience Manager as a Cloud Service
description: Meer informatie over de opmerkingen bij de release voor Cloud Manager 2024.10.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: 9cde6e63ec452161dbeb1e1bfb10c75f89e2692c
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2024.10.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Deze pagina documenteert de releaseopmerkingen voor Cloud Manager versie 2024.10.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Zie de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager release 2024.10.0 in AEM as a Cloud Service is 3 oktober 2024.

De volgende release is gepland voor 14 november 2024.

## Nieuwe functies {#what-is-new}

* <!-- BOTH CS & AMS --> De in Cloud Manager gebruikte versie van AEM Archetype wordt nu bijgewerkt naar versie 26. Zie [ https://github.com/adobe/aem-project-archetype/releases](https://github.com/adobe/aem-project-archetype/releases)

<!-- (CMGR-59817) -->

* <!-- CS ONLY --> Bij het toevoegen van een nieuw aangepast domein maakte de vorige verificatiemethode een langdurig DNS-validatieproces nodig. Adobe heeft dit proces voor klanten vereenvoudigd. Nu hoeft u alleen een geldig SSL-certificaat (EV of OV) op te geven dat als bewijs van eigendom dient. Het is niet langer nodig om TXT-records in de DNS bij te werken.

  >[!NOTE]
  >
  >Deze functie is alleen van toepassing op EV- en OV-certificaten die door de klant worden beheerd. DV-certificaten die door Adobe worden beheerd, vereisen nog steeds de aanwezigheid van een CNAME-record.

  Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen.

  ![ verifieer domein voor een klant beheerd EV/OV- certificaat ](/help/implementing/cloud-manager/assets/verify-domain-customer-managed-step.png)

* <!-- CS ONLY --> Wanneer u netwerkinfrastructuur toevoegt of bewerkt, worden de waarden in de IP-adres- en netwerkmaskervelden gevalideerd volgens de volgende regels:

   * De adresruimte mag de adressen die in de verbindingsadresruimte zijn gedefinieerd, niet overlappen.
   * DNS de adressen moeten of tot het netwerkmasker behoren dat in de ruimte van het verbindingsadres wordt bepaald of openbaar zijn.

  ![ voeg de dialoogdoos van de netwerkinfrastructuur toe ](/help/implementing/cloud-manager/release-notes/assets/network-infrastructure-add.png)

* <!-- CS ONLY --> Wijzigingen worden aangebracht in de indeling van de logbestanden voor omgevingsimplementatie voor het indexeren, installeren van veranderbare inhoud en transformatietaken.

  >[!NOTE]
  >
  >Deze wijziging is gepland voor geleidelijke uitrol met een verwachte einddatum in december 2024.

  ![ opstellen aan productiekaart ](/help/implementing/cloud-manager/release-notes/assets/deploy-to-production-card.png)

  Het formaat van het logboek zal van een eenvoudige ingang veranderen die in het volgende wordt gezien:

  ![ dossier van het Logboek dat eenvoudige ingangen toont ](/help/implementing/cloud-manager/release-notes/assets/log-file-simple-entry.png)

  Op een JSON-vermelding in het volgende voorbeeld:

  ![ dossier van het Logboek dat json ingangen ](/help/implementing/cloud-manager/release-notes/assets/log-file-json-entry.png) toont


## Programma voor vroegtijdige goedkeuring {#early-adoption}

Maak deel uit van het Cloud Manager-programma voor vroege adoptie en heb de kans om toekomstige functies te testen.

### Kies voor uw eigen git - nu met ondersteuning voor GitLab en Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**breng Uw Eigen eigenschap van het Git** is uitgebreid om steun voor externe bewaarplaatsen zoals GitLab en Bitbucket te omvatten. Deze nieuwe steun is naast reeds bestaande steun voor privé en ondernemingsbewaarplaatsen GitHub. Wanneer u deze nieuwe repo&#39;s toevoegt, kunt u deze ook rechtstreeks aan uw pijpleidingen koppelen. U kunt deze opslagruimten hosten op openbare cloudplatforms of binnen uw privécloud of infrastructuur. Deze integratie verwijdert ook de behoefte aan constante codesynchronisatie met de opslagplaats van de Adobe en verstrekt de capaciteit om trekkingsverzoeken te bevestigen alvorens hen in een hoofdtak samen te voegen.

Zie [ externe bewaarplaatsen in Cloud Manager ](/help/implementing/cloud-manager/managing-code/external-repositories.md) toevoegen.

![ voeg de dialoogdoos van de Bewaarplaats ](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png) toe

>[!NOTE]
>
>Momenteel, zijn de uit-van-de-doos controles van de trekkingsverzoekcodekwaliteit exclusief aan GitHub-ontvangen bewaarplaatsen, maar een update om deze functionaliteit tot andere verkopers van het Git uit te breiden is in de werken.

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ Grp-CloudManager_BYOG@adobe.com ](mailto:Grp-CloudManager_BYOG@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Zorg ervoor dat u ook het Git-platform opgeeft dat u wilt gebruiken en dat u zich in een opslagstructuur van een privéserver, een openbare opslagruimte of een bedrijfsopslagruimte bevindt.


<!-- ## Bug fixes




## Known issues {#known-issues} -->
