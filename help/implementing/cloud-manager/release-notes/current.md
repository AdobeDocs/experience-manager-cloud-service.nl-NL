---
title: Opmerkingen bij de release voor Cloud Manager 2024.12.0 in Adobe Experience Manager as a Cloud Service
description: Meer informatie over de release van Cloud Manager 2024.12.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: ea1aa471a4fcb2ace6e4079715ac88af2d296e18
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2024.12.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Meer informatie over de release van Cloud Manager 2024.12.0 in AEM (Adobe Experience Manager) as a Cloud Service.

>[!NOTE]
>
>Zie de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Releasedatums {#release-date}

De releasedatum voor Cloud Manager 2024.12.0 in AEM as a Cloud Service is donderdag 5 december 2024.

De volgende geplande release is januari 2024.

## Nieuwe functies {#what-is-new}

* **Java 21 steun:** de klanten kunnen nu naar keuze met Java 17 of Java 21 bouwen, die van prestatiesverbeteringen en nieuwe taaleigenschappen profiteren. Zie [ milieu bouwen ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) voor configuratiestappen, met inbegrip van het bijwerken van uw Maven projectbeschrijving, en bepaalde bibliotheekversies. Wanneer de versie voor samenstellen is ingesteld op Java 17 of Java 21, wordt voor de runtime standaard Java 21 gebruikt.

  Vanaf februari 2025 upgraden sandboxen en ontwikkelomgevingen naar de Java 21-runtime, ongeacht de versie van de build (Java 8, 11, 17 of 21). Productieomgevingen volgen met een upgrade in april 2025.

* **de verslagtypes van A:** Steun voor A verslagtypes is toegevoegd om Go Live Gereedheid voor domeinen te verbeteren gebruikend configuraties CDN in AEM Cloud Manager. U hebt nu de optie om levend te gaan door of een CNAME- verslagtype of een A- verslagtype toe te voegen dat IPs van Fastly vertegenwoordigt, die domein het verpletteren vereenvoudigen. Deze verbetering elimineert de beperking om zich alleen op CNAME- verslagen voor domeinopstelling met Fastly te baseren.

  Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen. <!-- CMGR-63076 -->

* **voeg veelvoudige domeinen aan een Plaats van Edge Delivery toe:** u kunt veelvoudige domeinen, met inbegrip van zowel apex als niet-apex domeinen, aan een Plaats van Edge Delivery (EDS) in AEM Cloud Manager nu toevoegen. Deze verhoging verhelpt vroegere beperkingen die de capaciteit beperkten om veelvoudige domeinen met een oorsprong te associëren EDS. De update zorgt voor betere flexibiliteit voor het beheer van domeinconfiguraties en vereenvoudigt de Go Live-processen voor sites met complexe domeininstellingen. <!-- CMGR-63007 -->

* **Geavanceerde het filtreren opties:** Geavanceerde het filtreren opties zijn geïntroduceerd op de uitvoeringspagina&#39;s van de Pijpleiding en SSL certificaatpagina&#39;s in AEM Cloud Manager. U kunt nu filteren op meerdere criteria, zodat u sneller toegang hebt tot relevante gegevens en de efficiëntie van de implementatie verbetert. <!-- CMGR-26263 -->

   * **activiteiten die van de Pijpleiding filtreren:** omvat pijpleidingsactiviteit het filtreren, latend u onderzoeksresultaten voor specifieke pijpleidingsactiviteiten verfijnen. Beschikbare filters omvatten pijpleiding, actie, en status.
     ![ Activiteiten die van de Pijpleiding ](/help/implementing/cloud-manager/assets/filters-pipeline.png) filtreren


   * **SSL certificaten het fileren:** omvat SSL certificaten het filtreren, latend u onderzoeksresultaten voor specifieke certificaten verfijnen. Beschikbare filters zijn SSL-certificaatnaam, -eigendom en -status.
     ![ SSL certificaat het filtreren ](/help/implementing/cloud-manager/assets/filters-ssl-certificates.png)

## Programma voor vroegtijdige goedkeuring {#early-adoption}

Maak deel uit van het Cloud Manager-programma voor vroege adoptie en heb de kans om toekomstige functies te testen.

### Kies voor uw eigen git - nu met ondersteuning voor GitLab en Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**breng Uw Eigen eigenschap van het Git** is uitgebreid om steun voor externe bewaarplaatsen, zoals GitLab en Bitbucket te omvatten. Deze nieuwe steun is naast reeds bestaande steun voor privé en ondernemingsbewaarplaatsen GitHub. Wanneer u deze nieuwe repo&#39;s toevoegt, kunt u deze ook rechtstreeks aan uw pijpleidingen koppelen. U kunt deze opslagruimten hosten op openbare cloudplatforms of binnen uw privécloud of infrastructuur. Deze integratie verwijdert ook de behoefte aan constante codesynchronisatie met de opslagplaats van de Adobe en verstrekt de capaciteit om trekkingsverzoeken te bevestigen alvorens hen in een hoofdtak samen te voegen.

De pijpleidingen die externe bewaarplaatsen gebruiken (exclusief GitHub-ontvangen degenen) en de **Trekker van de Plaatsing** aan **wordt geplaatst op de Veranderingen van het Git** beginnen nu automatisch.

Zie [ externe bewaarplaatsen in Cloud Manager ](/help/implementing/cloud-manager/managing-code/external-repositories.md) toevoegen.

![ voeg de dialoogdoos van de Bewaarplaats ](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png) toe

>[!NOTE]
>
>Momenteel, zijn de uit-van-de-doos controles van de trekkingsverzoekcodekwaliteit exclusief aan GitHub-ontvangen bewaarplaatsen, maar een update om deze functionaliteit tot andere verkopers van het Git uit te breiden is in de werken.

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ Grp-CloudManager_BYOG@adobe.com ](mailto:Grp-CloudManager_BYOG@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Zorg ervoor dat u ook het Git-platform opgeeft dat u wilt gebruiken en dat u zich in een opslagstructuur van een privéserver, een openbare opslagruimte of een bedrijfsopslagruimte bevindt.

## Bugfixes

* Er is een beveiliging toegevoegd om te voorkomen dat domeinen met actieve domeintoewijzingen in AEM Cloud Manager worden verwijderd. Gebruikers die dergelijke domeinen proberen te verwijderen, ontvangen nu een foutbericht waarin ze worden opgedragen eerst de domeintoewijzing te verwijderen voordat ze verdergaan met de domeinverwijdering. Deze workflow zorgt voor domeinintegriteit en voorkomt onbedoelde onjuiste configuraties. <!-- CMGR-63033 -->
* Zelden konden gebruikers geen domeinnaam toevoegen of een SSL-certificaat bijwerken vanwege een onjuiste status die was gekoppeld in de betreffende gevallen. <!-- CMGR-62816 -->


<!-- ## Known issues {#known-issues} -->