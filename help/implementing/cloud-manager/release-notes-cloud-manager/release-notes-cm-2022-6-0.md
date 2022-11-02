---
title: Opmerkingen bij de release Cloud Manager 2022.6.0 in Adobe Experience Manager as a Cloud Service
description: Dit zijn de opmerkingen bij de release voor Cloud Manager 2022.6.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 0a348836-74cd-4fd4-aef4-6ffbd6483c24
source-git-commit: e05c2fa2cfb035ed363e2c80d4aac33b022bd435
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Opmerkingen bij de release Cloud Manager 2022.6.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Deze pagina documenteert de opmerkingen bij de release voor Cloud Manager 2022.6.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Zie [deze pagina](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de actuele releaseopmerkingen voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager versie 2022.6.0 in AEM as a Cloud Service is 9 juni 2022. De volgende release is gepland voor 30 juni 2022.

## Wat is er nieuw? {#what-is-new}

* Een nieuwe welkomstkaart op de landingspagina van Cloud Manager biedt gebruikers snel toegang tot zelfstudies aan boord en voortgangsgegevens voor de huurder.
   * Deze functie wordt in de week na de release van 2022.06.0 geleidelijk ingevoerd.
* Gebruikers met de vereiste machtigingen hebben toegang tot een nieuwe [Licentiedashboard](/help/implementing/cloud-manager/license-dashboard.md) op de landingspagina van Cloud Manager om details te bekijken van rechten waarover de huurder beschikt.
   * AEM Sites is de eerste oplossing waarvoor beschikbaarheid en verbruik via het dashboard voor Cloud Manage worden geleverd.
   * Dit onderdeel wordt geleidelijk ingevoerd in de weken na de release van 2022.06.0.
* [Nieuw Relic sub-account en self-service gebruikersbeheer](/help/implementing/cloud-manager/user-access-new-relic.md) is nu beschikbaar via de interface van Cloud Manager.
   * Dit onderdeel wordt geleidelijk ingevoerd in de weken na de release van 2022.06.0.
* Een nieuwe Go Live-widget op de homepage van productieprogramma&#39;s voor Cloud Servicen biedt nu richtlijnen voor het voorbereiden van een geslaagde live-ervaring.
* [Buildartefacten kunnen nu opnieuw worden gebruikt](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) bij gebruik van git spiegelen.

## API-wijzigingen {#api-changes}

* De [`List Programs`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getPrograms) API is vervangen en [`List Programs for Tenant`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getProgramsForTenant) moet worden gebruikt.
   * `List Programs` blijft werken, maar het gebruik ervan zal waarschuwingsberichten in logboeken genereren.
   * Na drie maanden wordt er geen steun meer verleend.
