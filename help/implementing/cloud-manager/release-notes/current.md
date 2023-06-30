---
title: Opmerkingen bij de release Cloud Manager 2023.7.0 in Adobe Experience Manager as a Cloud Service
description: Dit zijn de opmerkingen bij de release voor Cloud Manager 2023.7.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 1b46f763903a1b103837ed7e8cc498ad08ce64f1
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---


# Opmerkingen bij de release Cloud Manager 2023.7.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Op deze pagina worden de opmerkingen bij de release 2023.7.0 van Cloud Manager in AEM as a Cloud Service gedocumenteerd.

>[!NOTE]
>
>Zie [deze pagina](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de actuele releaseopmerkingen voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager versie 2023.7.0 in AEM as a Cloud Service is 29 juni 2023. De volgende release is gepland voor 10 augustus 2023.

## Wat is er nieuw? {#what-is-new}

* Kaarten op de landingspagina van Cloud Manager geven nu aan of [verbeterde beveiliging](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) is ingeschakeld voor hun programma&#39;s.
* Indien een ontwikkeling [pijpleiding](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) bevat geen teststappen. Gebruikers kunnen nu teststappen opnemen als ze [start de pijpleiding.](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines)
   * Dit zal gefaseerd worden uitgevoerd.
* Wanneer [annulering van de uitvoering,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) in de goedkeuringsstap voor de uitvoering van de pijpleiding wordt de gebruiker nu verzocht een reden voor annulering te geven .
   * Dit zal gefaseerd worden uitgevoerd.

## Opgeloste problemen {#bug-fixes}

* Navigeer aan auteursUI van de Manager van de Wolk niet meer om in Verenigde Shell na login opnieuw te richten.
* Als u de datum van de go-live via de go-live widget bewerkt, gaat u nu naar de **Live gaan** in plaats van de **Uitgebreide beveiliging** tab.
* Wanneer een kopieerbewerking wordt gestart, kan een gebruiker niet langer een omgeving selecteren waarin al een kopieerbewerking is aangeroepen.
