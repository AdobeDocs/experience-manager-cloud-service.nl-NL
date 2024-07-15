---
title: De tool Asset Workflow Migration
description: De tool Asset Workflow Migration
exl-id: a95caf5e-e6b2-463f-bebd-b791104fd25c
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 30%

---

# De tool Asset Workflow Migration {#asset-workflow-migration}

Met de Asset Workflow Migration-tool kunt u workflows voor de verwerking van assets automatisch migreren van on-premise- of AMS-implementaties van AEM naar verwerkingsprofielen en OSGi-configuraties voor gebruik in AEM Assets as a Cloud Service.

## Inleiding {#introduction}

In deze sectie worden de bronnen en implementatiegegevens over de tool Asset Workflow Migration beschreven.

Met dit hulpprogramma kunnen AEM-ontwikkelaars bestaande AEM-workflows voor de verwerking van assets migreren naar AEM as a Cloud Service.

## Ondersteunde workflows {#migration-support-for-workflows}

De workflows hebben een verschillend niveau van migratieondersteuning. Zie deze [ lijst van specifieke werkschema&#39;s ](https://github.com/adobe/aem-cloud-migration/blob/master/src/main/resources/workflowSteps.properties). De workflows worden ingedeeld in de volgende categorieën op basis van de geleverde ondersteuning. Adobe ondersteunt de migratie van de workflows die in de categorieën `SUPPORTED` , `REQUIRED` of `OPTIONAL` worden vermeld. De workflowstappen die in de andere categorieën worden vermeld, worden niet ondersteund.

* `SUPPORTED`: ondersteunde functionaliteit in [!DNL Experience Manager Assets] as a Cloud Service.
* `OPTIONAL`: optionele functionaliteit in [!DNL Experience Manager Assets] as a Cloud Service.
* `REQUIRED`: Een vereiste stap die wordt toegevoegd aan de workflow.
* `UNNECESSARY`: functionaliteit is niet nodig in [!DNL Experience Manager Assets] as a Cloud Service.
* `NUI_OOTB`: Functionaliteit die door [ wordt verstrekt de Dienst van de Asset compute ](/help/assets/asset-microservices-configure-and-use.md).
* `DMS7_OOTB`: Functionaliteit die wordt geboden door standaard [!DNL Dynamic Media] -connectors.
* `NUI_MIGRATED`: Gegigreerd aan a [ verwerkingsprofiel voor de Dienst van de Asset compute ](/help/assets/asset-microservices-configure-and-use.md).
* `UNSUPPORTED`: wordt momenteel niet ondersteund in [!DNL Experience Manager Assets] as a Cloud Service.

## Hulpprogramma voor migratie van bedrijfsmiddelen gebruiken {#use-workflow-migrator}

* **[!DNL Adobe I/O]CLI**: Adobe raadt u aan het hulpmiddel Asset Workflow Migration te gebruiken via `aio-cli-plugin-aem-cloud-service-migration` ([!DNL Experience Manager] als een [!DNL Cloud Service] code refactoring plugin voor de [!DNL Adobe I/O] CLI). Leren om de stop te installeren en te gebruiken, zie [ middel van de it: ao-cli-stop-aem-wolk-dienst-migratie ](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction).

* **Standalone nut**: Het hulpmiddel van de Migratie van het Werkschema van Activa kan ook als standalone nut worden uitgevoerd. Om over het installeren van en het bouwen van code van de bron te leren, zie [ middel van de Git: [!DNL Experience Manager Assets]  als a  [!DNL Cloud Service]  - werkschemamigratie ](https://github.com/adobe/aem-cloud-migration).
