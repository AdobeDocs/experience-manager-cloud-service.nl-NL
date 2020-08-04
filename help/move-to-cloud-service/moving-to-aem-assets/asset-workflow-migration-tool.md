---
title: De tool Asset Workflow Migration
description: 'De tool Asset Workflow Migration '
translation-type: tm+mt
source-git-commit: 3a438de3c460d4dc5a8b8617f0ec0eefc56f1665
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 46%

---


# De tool Asset Workflow Migration {#asset-workflow-migration}

Met de Asset Workflow Migration-tool kunt u workflows voor de verwerking van assets automatisch migreren van on-premise- of AMS-implementaties van AEM naar verwerkingsprofielen en OSGi-configuraties voor gebruik in AEM Assets as a Cloud Service.

## Inleiding {#introduction}

In deze sectie worden de bronnen en implementatiegegevens over de tool Asset Workflow Migration beschreven.

Met dit hulpprogramma kunnen AEM-ontwikkelaars bestaande AEM-workflows voor de verwerking van assets migreren naar AEM as a Cloud Service.

## Ondersteunde workflows {#migration-support-for-workflows}

De workflows hebben een verschillend niveau van migratieondersteuning. Zie deze [lijst met specifieke workflows](https://github.com/adobe/aem-cloud-migration/blob/master/src/main/resources/workflowSteps.properties). De workflows worden ingedeeld in de volgende categorieën op basis van de geleverde ondersteuning. Adobe ondersteunt de migratie van de workflows die in `SUPPORTED`, `REQUIRED`of `OPTIONAL` categorieën worden vermeld. De workflowstappen die in de andere categorieën worden vermeld, worden niet ondersteund.

* `SUPPORTED`: Ondersteunde functionaliteit in [!DNL Experience Manager Assets] de vorm van een Cloud Service.
* `OPTIONAL`: Optionele functionaliteit in [!DNL Experience Manager Assets] de vorm van een Cloud Service.
* `REQUIRED`: Een vereiste stap die wordt toegevoegd aan de workflow.
* `UNNECESSARY`: Functionaliteit is niet nodig in [!DNL Experience Manager Assets] de vorm van een Cloud Service.
* `NUI_OOTB`: Functionaliteit die wordt geboden door [Asset Compute Service](/help/assets/asset-microservices-configure-and-use.md).
* `DMS7_OOTB`: Functionaliteit die door standaardconnectors wordt verstrekt. [!DNL Dynamic Media]
* `NUI_MIGRATED`: Gemigreerd naar een [verwerkingsprofiel voor de Asset Compute Service](/help/assets/asset-microservices-configure-and-use.md).
* `UNSUPPORTED`: Momenteel niet ondersteund in [!DNL Experience Manager Assets] de vorm van een Cloud Service.

## De tool Asset Workflow Migration installeren {#installing-tool}

Zie **[Git Resource: AEM Assets as a Cloud Service - Workflowmigratie](https://github.com/adobe/aem-cloud-migration)**voor meer informatie over het installeren en samenstellen van code van de bron.
