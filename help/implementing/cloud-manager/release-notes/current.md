---
title: Opmerkingen bij de release Cloud Manager 2023.6.0 in Adobe Experience Manager as a Cloud Service
description: Dit zijn de opmerkingen bij de release voor Cloud Manager 2023.6.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: deef27dd90be22669b2328f6e394b8d3df99b4b9
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---


# Opmerkingen bij de release Cloud Manager 2023.6.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Op deze pagina worden de opmerkingen bij de release 2023.6.0 van Cloud Manager in AEM as a Cloud Service gedocumenteerd.

>[!NOTE]
>
>Zie [deze pagina](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de actuele releaseopmerkingen voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager versie 2023.6.0 in AEM as a Cloud Service is 8 juni 2023. De volgende release is gepland voor 6 juli 2023.

## Wat is er nieuw? {#what-is-new}

* Klanten kunnen naast het primaire gebied aanvullende secundaire publicatiegebieden aanschaffen, wat voordelen oplevert als gevolg van een lagere latentie en een hogere beschikbaarheid. Opmerking: Bepaalde beperkingen kunnen van toepassing zijn.
* Bij het maken van een nieuwe [programma of milieu;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) de naam mag nu alleen alfanumerieke tekens en een beperkte set speciale tekens bevatten .
* Bij het hervatten van een [productiepijpleiding,](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) er wordt nu een bevestigingsvenster weergegeven bij de stap Goedkeuren.
* Voor de **[Functionele tests van de klant](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)** en **[Aangepaste UI-tests](/help/implementing/cloud-manager/ui-testing.md)** pijpleidingstappen, een nieuwe `INCOMPLETE` de status is nu mogelijk , hetgeen erop wijst dat dergelijke tests niet aanwezig waren en dus niet werden uitgevoerd .
   * In dergelijke gevallen mislukt de pijpleiding niet en gaat deze verder naar de volgende stap.

## Opgeloste problemen {#bug-fixes}

* De [configuratiepijplijn voor webniveau](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) zijn niet meer onjuist ingeschakeld voor programma&#39;s met alleen elementen.
* Er is een robuustere validatie toegevoegd om bepaalde typen fouten tijdens de levering van omgevingen te voorkomen.
