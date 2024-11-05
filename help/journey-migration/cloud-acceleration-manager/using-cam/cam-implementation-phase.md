---
title: Implementatiefase in Cloud Acceleration Manager
description: Deze pagina biedt een overzicht van de implementatiefase in Cloud Acceleration Manager.
exl-id: e6ac88f0-4b3f-43a1-98bc-8c6608713784
feature: Migration
role: Admin
source-git-commit: f86d681c8f8cb6d602058ef30b648c53ff7bad69
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%

---

# Implementatiefase in Cloud Acceleration Manager {#implementation-phase-cam}

De implementatiefase omvat:

* [Lokale ontwikkeling](#local-development)
* [Code Refactoring](#code-refactoring)
* [AEM as a Cloud Service-implementatie](#aem-as-a-cloud-service-deployment)
* [Inhoud overbrengen](#content-transfer)


Klik uw projectkaart zodat kunt u het project openen die pagina landen en aan de **sectie van de Implementatie** navigeren, zoals aangetoond in het volgende cijfer.

![ het landen van het Project pagina - Implementatie ](/help/journey-migration/cloud-acceleration-manager/assets/implementation-1.png)

>[!NOTE]
>Zie [ Creërend en het Leiden een Project in Cloud Acceleration Manager ](getting-started-cam.md#create-project) om meer te leren.


## Lokale ontwikkelingskaart gebruiken {#local-development}

De kaart voor lokale ontwikkeling biedt alle relevante inhoud die u kan helpen uw lokale AEM ontwikkelomgeving in te stellen wanneer u de implementatiefase van uw migratiereis start.

Volg deze sectie zodat u de de activiteitenkaart van de Lokale Ontwikkeling kunt onderzoeken:

1. Klik **Mening** van de **Lokale kaart van de Ontwikkeling**.

   ![ Lokale kaart van de Ontwikkeling ](/help/journey-migration/cloud-acceleration-manager/assets/implementation-2.png)

1. Een inhoudscarrousel geeft de relevante informatie voor deze fase van de migratiereis weer.

   ![ Lokale de carrousel van de Ontwikkeling ](/help/journey-migration/cloud-acceleration-manager/assets/implementation-3.png)


## Code Refactoring Card gebruiken {#code-refactoring}

De Activiteitenkaart van de Refactoring van de Code verstrekt alle relevante informatie en benadrukt de code refactoring gebieden om te herzien en op te lossen wanneer zich aan AEM as a Cloud Service beweegt.

Volg deze sectie zodat kunt u de Activiteitenkaart van de Refactoring van de Code onderzoeken:

1. Klik **Overzicht** van de **Refactoring van de Code** activiteitenkaart.

   ![ het refactoring van de Code kaart ](/help/journey-migration/cloud-acceleration-manager/assets/implementation-4.png)

1. De pagina toont de lijst van code refactoring activiteiten die door het strengheidsniveau worden georganiseerd. Klik op de twee gemarkeerde pictogrammen voor meer informatie.

   Op de pagina worden de overwegingen voor het wijzigen van code in drie verschillende tabbladen weergegeven:

   * Overzicht
   * Dispatcher
   * Testen

>[!NOTE]
>Bekijk de inhoud op deze tabbladen om een aantal extra gebieden te begrijpen die niet worden bestreken door de Analysator voor beste praktijken.

Het **Dispatcher** lusje verstrekt informatie over hoe te om de configuraties van AEM as a Cloud Service Apache en van Dispatcher te structureren, en hoe te om het plaatselijk te bevestigen en in werking te stellen alvorens aan de milieu&#39;s van de Wolk op te stellen. Hierin wordt ook foutopsporing in Cloud-omgevingen beschreven.

![ Dispatcher tabel ](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-2.png)

Het **Testen** lusje verstrekt informatie over functioneel, de Controle van de Ervaring, en het testen UI.

![ het Testen lusje ](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-3.png)


## AEM as a Cloud Service-implementatiekaart gebruiken {#aem-as-a-cloud-service-deployment}

AEM as a Cloud Service Deployment-kaart biedt alle relevante inhoud die u helpt uw code te implementeren in AEM as a Cloud Service.

Volg deze sectie zodat kunt u de activiteitenkaart van AEM as a Cloud Service Deployment Card bekijken:

1. Klik **Mening** van de **3} activiteitenkaart van de Plaatsing van AEM as a Cloud Service.**

   ![ Plaatsing AEM as a Cloud Service - kaart ](/help/journey-migration/cloud-acceleration-manager/assets/implementation-6.png)

1. Een inhoudscarrousel geeft de relevante informatie voor deze fase van de migratiereis weer.

   ![ Plaatsing AEM as a Cloud Service - carrousel ](/help/journey-migration/cloud-acceleration-manager/assets/aem-deployment-card.png)


## Inhoudsoverdrachtkaart gebruiken {#content-transfer}

Met de kaart voor inhoudsoverdracht kunt u de overdracht van inhoud van uw huidige AEM naar AEM as a Cloud Service starten en beheren.

Volg deze sectie zodat u de activiteitenkaart van de Overdracht van de Inhoud kunt onderzoeken:

1. Klik **Overzicht** van de **Vervoerkaart van de Inhoud** activiteit.

   ![ Overdracht van de Inhoud - Overzicht ](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-1.png)

1. Als u een inhoudsoverdracht wilt starten, moet u een migratieset maken. Klik **creeer migratieset**. Met een migratieset kan inhoud worden overgebracht naar AEM as a Cloud Service.

   ![ creeer migratieset ](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-2.png)

   >[!NOTE]
   >Een migratieset verloopt na een langdurige periode van inactiviteit. Zie [ Verval van de Reeks van de Migratie ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) voor details.

   >[!NOTE]
   >Zie [ eerste vereisten ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html) en [ beste praktijken en richtlijnen ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) alvorens het Hulpmiddel van de Overdracht van de Inhoud te gebruiken.

1. Download en installeer het gereedschap Inhoud overbrengen om de migratieset te vullen en de extractiefase van de overdracht van inhoud te voltooien. Het overzicht [ Begonnen Worden met het Hulpmiddel van de Overdracht van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html) om te leren hoe te om het Hulpmiddel van de Overdracht van de Inhoud te gebruiken.

1. Als u inhoud uit de Migratie-set wilt opnemen in een omgeving op AEM as a Cloud Service, moet u een opname starten. Navigeer aan **IngestieBanen** en klik **Nieuwe opname**. Het overzicht [ Ingesting Inhoud in Doel ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) zodat kunt u leren hoe te om de fase van de Ingestie van inhoudoverdracht te voltooien.

   ![ Ingestietaken ](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-3.png)

<!--### Estimating Content Transfer Time {#calculating}

A Content Transfer Tool calculator has been provided to estimate how long it could take to complete the content transfer activity. You can use the content repository size slider to select the size that applies to your project. The transfer times vary for the extraction and ingestion phases. 

   ![Content Transfer Tool calculator](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-4.png)

   >[!NOTE]
   >These times are estimates only. Factor such as network speeds and time to scale up instances have not been accounted for in these estimates.

To estimate the size of the AEM Repository, you can run the Disk Usage report under `http://HOST:PORT/etc/reports/diskusage.html`. 

You can also estimate the size of specific repository paths by using the `path` parameter, for example, `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`. -->

## Volgende functies {#whats-next}

Nadat u hebt geleerd hoe te aan login aan Cloud Acceleration Manager en hoe te om de fase van de Implementatie te gebruiken, bent u bereid om op het herzien van de volgende stap in [ te gaan Levende Fase ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-golive-phase.html).
