---
title: Implementatiefase in Cloud Acceleration Manager
description: Deze pagina bevat een overzicht van de implementatiefase in Cloud Acceleration Manager.
exl-id: e6ac88f0-4b3f-43a1-98bc-8c6608713784
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 1%

---

# Implementatiefase in Cloud Acceleration Manager {#implementation-phase-cam}

De implementatiefase omvat:

* [Lokale ontwikkeling](#local-development)
* [Code Refactoring](#code-refactoring)
* [as a Cloud Service implementatie AEM](#aem-as-a-cloud-service-deployment)
* [Inhoud overbrengen](#content-transfer)


Klik op de projectkaart zodat u de bestemmingspagina van het project kunt openen en naar de **Implementatie** in de volgende afbeelding.

![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/implementation-1.png)

>[!NOTE]
>Zie [Een project maken en beheren in Cloud Acceleration Manager](getting-started-cam.md#create-project) voor meer informatie.


## Lokale ontwikkelingskaart gebruiken {#local-development}

De kaart voor lokale ontwikkeling biedt alle relevante inhoud die u kan helpen uw lokale AEM ontwikkelomgeving in te stellen wanneer u de implementatiefase van uw migratiereis start.

Volg deze sectie zodat u de de activiteitenkaart van de Lokale Ontwikkeling kunt onderzoeken:

1. Klikken **Weergave** van de **Lokale ontwikkeling** kaart.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/implementation-2.png)

1. Een inhoudscarrousel geeft de relevante informatie voor deze fase van de migratiereis weer.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/implementation-3.png)


## Code Refactoring Card gebruiken {#code-refactoring}

De Activiteitenkaart van de Refactoring van de Code verstrekt alle relevante informatie en benadrukt de code refactoring gebieden om te herzien en op te lossen wanneer het bewegen aan AEM as a Cloud Service.

Volg deze sectie zodat kunt u de Activiteitenkaart van de Refactoring van de Code onderzoeken:

1. Klikken **Controleren** van de **Code Refactoring** activiteitenkaart.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/implementation-4.png)

1. De pagina toont de lijst van code refactoring activiteiten die door het strengheidsniveau worden georganiseerd. Klik op de twee gemarkeerde pictogrammen voor meer informatie.

   Op de pagina worden de overwegingen voor het wijzigen van code in drie verschillende tabbladen weergegeven:

   * Overzicht
   * Dispatcher
   * Testen

>[!NOTE]
>Bekijk de inhoud op deze tabbladen om een aantal extra gebieden te begrijpen die niet worden bestreken door de Analysator voor beste praktijken.

De **Dispatcher** biedt informatie over hoe u de AEM as a Cloud Service Apache- en Dispatcher-configuraties kunt structureren en hoe u deze lokaal kunt valideren en uitvoeren voordat u ze implementeert in Cloud-omgevingen. Hierin wordt ook foutopsporing in Cloud-omgevingen beschreven.

![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-2.png)

De **Testen** biedt informatie over het testen van functies, Experience Audit en UI.

![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/coderefactoring-3.png)


## AEM as a Cloud Service implementatiekaart gebruiken {#aem-as-a-cloud-service-deployment}

AEM as a Cloud Service implementatiekaart biedt alle relevante inhoud die u helpt uw code te implementeren om as a Cloud Service te AEM.

Volg deze sectie zodat u AEM as a Cloud Service de activiteitenkaart van de Kaart van de Plaatsing kunt onderzoeken:

1. Klikken **Weergave** van de **as a Cloud Service implementatie AEM** activiteitenkaart.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/implementation-6.png)

1. Een inhoudscarrousel geeft de relevante informatie voor deze fase van de migratiereis weer.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/aem-deployment-card.png)


## Inhoudsoverdrachtkaart gebruiken {#content-transfer}

Met de kaart voor inhoudsoverdracht kunt u de overdracht van inhoud van uw huidige AEM naar AEM as a Cloud Service starten en beheren.

Volg deze sectie zodat u de activiteitenkaart van de Overdracht van de Inhoud kunt onderzoeken:

1. Klikken **Controleren** van de **Inhoud overbrengen** activiteitenkaart.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-1.png)

1. Als u een inhoudsoverdracht wilt starten, moet u een migratieset maken. Klikken **Migratieset maken**. Met een migratieset kan inhoud worden overgebracht naar AEM as a Cloud Service.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-2.png)

   >[!NOTE]
   >Een migratieset verloopt na een langdurige periode van inactiviteit. Zie [Vervaldatum migratieset](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) voor meer informatie.

   >[!NOTE]
   >Zie [voorwaarden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html) en de [beste praktijken en richtsnoeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) voordat u het gereedschap Inhoud overbrengen gebruikt.

1. Download en installeer het gereedschap Inhoud overbrengen om de migratieset te vullen en de extractiefase van de overdracht van inhoud te voltooien. Controleren [Aan de slag met het gereedschap Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html) voor meer informatie over het gebruik van het gereedschap Inhoud overbrengen.

1. Als u inhoud van de Migratie-set wilt opnemen in een omgeving op AEM as a Cloud Service, moet u een opname starten. Navigeren naar **Ingestietaken** en klik op **Nieuwe opname**. Controleren [Inhoud in doel invoegen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) zodat kunt u leren hoe te om de fase van de Ingestie van inhoudoverdracht te voltooien.

   ![afbeelding](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-3.png)

<!--### Estimating Content Transfer Time {#calculating}

A Content Transfer Tool calculator has been provided to estimate how long it could take to complete the content transfer activity. You can use the content repository size slider to select the size that applies to your project. The transfer times vary for the extraction and ingestion phases. 

   ![image](/help/journey-migration/cloud-acceleration-manager/assets/contenttransfer-4.png)

   >[!NOTE]
   >These times are estimates only. Factor such as network speeds and time to scale up instances have not been accounted for in these estimates.

To estimate the size of the AEM Repository, you can run the Disk Usage report under `http://HOST:PORT/etc/reports/diskusage.html`. 

You can also estimate the size of specific repository paths by using the `path` parameter, for example, `http://HOST:PORT/etc/reports/diskusage.html?path=/content/dam`. -->

## Volgende functies {#whats-next}

Nadat u hebt geleerd hoe u zich kunt aanmelden bij Cloud Acceleration Manager en hoe u de Implementatiefase kunt gebruiken, bent u klaar om door te gaan met de volgende stap in het dialoogvenster [Actieve fase](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-golive-phase.html).
