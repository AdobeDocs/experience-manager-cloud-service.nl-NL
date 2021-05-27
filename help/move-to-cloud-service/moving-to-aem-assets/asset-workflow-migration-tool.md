---
title: De tool Asset Workflow Migration
description: De tool Asset Workflow Migration
exl-id: 18490295-ead6-4691-8983-a6d4054e4264
source-git-commit: a0fb2714bc74c620d90153746930757301e62fd7
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 29%

---

# De tool Asset Workflow Migration {#asset-workflow-migration}

Met de Asset Workflow Migration-tool kunt u workflows voor de verwerking van assets automatisch migreren van on-premise- of AMS-implementaties van AEM naar verwerkingsprofielen en OSGi-configuraties voor gebruik in AEM Assets as a Cloud Service.

## Inleiding {#introduction}

In deze sectie worden de bronnen en implementatiegegevens over de tool Asset Workflow Migration beschreven.

Met dit hulpprogramma kunnen AEM-ontwikkelaars bestaande AEM-workflows voor de verwerking van assets migreren naar AEM as a Cloud Service.

## Ondersteunde workflows {#migration-support-for-workflows}

De workflows hebben een verschillend niveau van migratieondersteuning. Zie deze [lijst met specifieke workflows](https://github.com/adobe/aem-cloud-migration/blob/master/src/main/resources/workflowSteps.properties). De workflows worden ingedeeld in de volgende categorieën op basis van de geleverde ondersteuning. Adobe ondersteunt migratie van de workflows die worden vermeld in `SUPPORTED`, `REQUIRED` of `OPTIONAL` categorieën. De workflowstappen die in de andere categorieën worden vermeld, worden niet ondersteund.

* `SUPPORTED`: Ondersteunde functionaliteit  [!DNL Experience Manager Assets] als Cloud Service.
* `OPTIONAL`: Optionele functionaliteit  [!DNL Experience Manager Assets] als Cloud Service.
* `REQUIRED`: Een vereiste stap die wordt toegevoegd aan de workflow.
* `UNNECESSARY`: Functionaliteit is niet nodig  [!DNL Experience Manager Assets] als Cloud Service.
* `NUI_OOTB`: Functionaliteit van de  [Asset compute](/help/assets/asset-microservices-configure-and-use.md).
* `DMS7_OOTB`: Functionaliteit die door standaard  [!DNL Dynamic Media] connectors wordt verstrekt.
* `NUI_MIGRATED`: Gemigreerd naar een  [verwerkingsprofiel voor de Dienst](/help/assets/asset-microservices-configure-and-use.md) van de Asset compute.
* `UNSUPPORTED`: Momenteel niet ondersteund in  [!DNL Experience Manager Assets] de vorm van een Cloud Service.

## Hulpprogramma {#use-workflow-migrator} voor migratie van bedrijfsmiddelen gebruiken

* **[!DNL Adobe I/O]CLI**: Adobe raadt u aan het hulpmiddel Asset Workflow Migration te gebruiken via  `aio-cli-plugin-aem-cloud-service-migration` ([!DNL Experience Manager] als een  [!DNL Cloud Service] coderefactoring-insteekmodule voor de  [!DNL Adobe I/O] CLI). Zie [Git-bron voor meer informatie over het installeren en gebruiken van de plug-in: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction).

* **Standalone-hulpprogramma**: Het Hulpprogramma voor migratie van bedrijfsmiddelen kan ook worden uitgevoerd als een zelfstandig hulpprogramma. Zie **[Git resource: [!DNL Experience Manager Assets] as a [!DNL Cloud Service] - workflow migration](https://github.com/adobe/aem-cloud-migration)** voor meer informatie over het installeren en samenstellen van code uit de bron.
