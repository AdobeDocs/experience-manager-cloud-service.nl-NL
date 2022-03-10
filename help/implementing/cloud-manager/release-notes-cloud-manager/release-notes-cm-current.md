---
title: Opmerkingen bij de release Cloud Manager 2022.3.0 in Adobe Experience Manager as a Cloud Service
description: Dit zijn de opmerkingen bij de release voor Cloud Manager 2022.3.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 428bba062fcfb44ebfbbf3c1d05ce1a4634fb429
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Opmerkingen bij de release Cloud Manager 2022.3.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Deze pagina documenteert de opmerkingen bij de release voor Cloud Manager 2022.3.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Zie [deze pagina](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de actuele releaseopmerkingen voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager versie 2022.3.0 in AEM as a Cloud Service 10 maart 2022. De volgende release is gepland voor 7 april 2022.

## Wat is er nieuw? {#what-is-new}

* Een gebruiker met de **Ontwikkelaar** de rol kan tot het AEM milieulogboek nu toegang hebben.
* [De `reliability_rating` kritisch metrisch](/help/implementing/cloud-manager/code-quality-testing.md) is uitgeschakeld.
* Een gebruiker kan nu sorteren op de kolommen in het dialoogvenster **Pijpleidingen** in Cloud Manager.

## Opgeloste problemen {#bug-fixes}

* Een subset van handmatig gemaakte git-opslagplaatsen had onjuiste naamwaarden die van invloed waren op [de functie voor hergebruik van bouwartefacten.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) De namen van deze opslagruimten zijn gewijzigd en gebruikers zien de gecorrigeerde naam in de API/UI van Cloud Manager.
* [Wanneer het toevoegen van of het uitgeven van een pijpleiding van de codekwaliteit,](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) de **Belangrijk gedrag metrische fouten** worden niet meer weergegeven.
* De onverwachte configuraties van de pijpleidingsvariabele veroorzaken niet meer fouten in de bouwstijlstap.
