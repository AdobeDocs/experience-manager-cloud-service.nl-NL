---
title: De tool Asset Workflow Migration
description: De tool Asset Workflow Migration
exl-id: a95caf5e-e6b2-463f-bebd-b791104fd25c
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 29%

---

# De tool Asset Workflow Migration {#asset-workflow-migration}

Met de Asset Workflow Migration-tool kunt u workflows voor de verwerking van assets automatisch migreren van on-premise- of AMS-implementaties van AEM naar verwerkingsprofielen en OSGi-configuraties voor gebruik in AEM Assets as a Cloud Service.

## Inleiding {#introduction}

In deze sectie worden de bronnen en implementatiegegevens over de tool Asset Workflow Migration beschreven.

Met dit hulpprogramma kunnen AEM-ontwikkelaars bestaande AEM-workflows voor de verwerking van assets migreren naar AEM as a Cloud Service.

## Ondersteunde workflows {#migration-support-for-workflows}

De workflows hebben een verschillend niveau van migratieondersteuning. Zie dit [lijst met specifieke workflows](https://github.com/adobe/aem-cloud-migration/blob/master/src/main/resources/workflowSteps.properties). De workflows worden ingedeeld in de volgende categorieën op basis van de geleverde ondersteuning. Adobe ondersteunt migratie van de workflows die worden vermeld in `SUPPORTED`, `REQUIRED`, of `OPTIONAL` categorieën. De workflowstappen die in de andere categorieën worden vermeld, worden niet ondersteund.

* `SUPPORTED`: Ondersteunde functionaliteit in [!DNL Experience Manager Assets] as a Cloud Service.
* `OPTIONAL`: Optionele functionaliteit in [!DNL Experience Manager Assets] as a Cloud Service.
* `REQUIRED`: Een vereiste stap die wordt toegevoegd aan de workflow.
* `UNNECESSARY`: Functionaliteit is niet nodig in [!DNL Experience Manager Assets] as a Cloud Service.
* `NUI_OOTB`: Functionaliteit verstrekt door [asset compute](/help/assets/asset-microservices-configure-and-use.md).
* `DMS7_OOTB`: Door standaard geboden functionaliteit [!DNL Dynamic Media] connectors.
* `NUI_MIGRATED`: Gemigreerd naar een [verwerkingsprofiel voor de Asset compute Service](/help/assets/asset-microservices-configure-and-use.md).
* `UNSUPPORTED`: Momenteel niet ondersteund in [!DNL Experience Manager Assets] as a Cloud Service.

## Hulpprogramma voor migratie van bedrijfsmiddelen gebruiken {#use-workflow-migrator}

* **[!DNL Adobe I/O]CLI**: Adobe raadt u aan het hulpmiddel Asset Workflow Migration te gebruiken via `aio-cli-plugin-aem-cloud-service-migration` ([!DNL Experience Manager] als [!DNL Cloud Service] code refactoring plug-in voor de [!DNL Adobe I/O] CLI). Ga voor meer informatie over het installeren en gebruiken van de plug-in naar [Git-bron: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction).

* **Standalone-hulpprogramma**: Het Hulpprogramma voor migratie van bedrijfsmiddelen kan ook worden uitgevoerd als een zelfstandig hulpprogramma. Ga voor meer informatie over het installeren en samenstellen van code uit de bron naar [Git-bron: [!DNL Experience Manager Assets] als [!DNL Cloud Service] - workflowmigratie](https://github.com/adobe/aem-cloud-migration).
