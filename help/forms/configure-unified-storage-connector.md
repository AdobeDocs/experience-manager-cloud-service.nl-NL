---
title: Hoe te om Verenigde Schakelaar van de Opslag (USC) voor AEM Forms te vormen?
description: Leer hoe te om Verenigde Schakelaar van de Opslag (USC) voor AEM Forms te beheren. Gebruik de Unified Storage Connector (USC) om AEM Forms te verbinden met externe gegevensopslag.
role: Admin, Developer, User
feature: Adaptive Forms, Workflow
exl-id: c93d0242-0c15-4d69-82a1-d6fcc7da4bae
source-git-commit: 527c9944929c28a0ef7f3e617ef6185bfed0d536
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# Unified Storage Connector (USC) voor AEM Forms beheren {#manage-unified-storage-connector}

U kunt Unified Storage Connector (USC) gebruiken om AEM Forms te verbinden met externe gegevensopslag.

U kunt bijvoorbeeld waarden invullen voor velden in een adaptief formulier en deze verzenden naar een AEM Workflow. U kunt AEM Workflows verder configureren om gegevens op te slaan in een externe opslag, zoals de Microsoft Azure-opslagserver. Gebruik de Unified Storage Connector (USC) om een verbinding tot stand te brengen tussen AEM Workflows en de externe opslag.

## Connect AEM Workflows met een Microsoft Azure-opslagserver {#connect-workflows-with-azure}

Creeer een Azure opslagconfiguratie en verwijs naar die configuratie gebruikend de Verenigde Schakelaar van de Opslag (USC). Vervolgens kunt u AEM workflowmodellen configureren om de gegevensopslag te extern te maken en deze aan te sluiten op een Azure-opslagserver.

### Maken [!DNL Azure] opslagconfiguratie {#create-azure-storage-configuration}

Controleer voordat u deze stappen uitvoert of u een [!DNL Azure] opslagaccount en een toegangstoets om de toegang tot de [!DNL Azure] opslagaccount.

Voer de volgende stappen uit om een [!DNL Azure] opslagconfiguratie:

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure Storage]**.
1. Selecteer een map om de configuratie te maken en selecteer **[!UICONTROL Create]**.
1. Geef een titel voor de configuratie op in het dialoogvenster **[!UICONTROL Title]** veld.
1. Geef de naam van de [!DNL Azure] opslagaccount in de **[!UICONTROL Azure Storage Account]** veld.
1. Geef de sleutel op voor toegang tot Azure-opslagaccount in het dialoogvenster **[!UICONTROL Azure Access Key]** veld en selecteer **[!UICONTROL Save]**.

### Unified Storage Connector (USC) voor AEM workflows configureren {#configure-unified-storage-connector-workflows}

Voer de volgende stappen uit om Verenigde Verbinding van de Opslag (USC) voor AEM Workflows te vormen:

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Unified Storage Connector]**.

1. In de **[!UICONTROL Workflow]** sectie, selecteren **[!UICONTROL Azure]** in de vervolgkeuzelijst Opslag.
1. Geef de [configuratiepad voor de Azure-opslagconfiguratie](#create-azure-storage-configuration) in de **[!UICONTROL Storage Configuration Path]** veld.
1. Selecteren **[!UICONTROL Publish]** en selecteer vervolgens **[!UICONTROL Save]** om de configuratie op te slaan.

### Een AEM workflowmodel voor externe gegevensopslag configureren {#configure-workflow-external-data-storage}

Voer de volgende stappen uit om een AEM workflowmodel voor een externe gegevensopslag te configureren:

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteer een modelnaam en selecteer **[!UICONTROL Edit]**.
1. Selecteer het pictogram Pagina-informatie en selecteer **[!UICONTROL Open Properties]**.
1. Selecteren **[!UICONTROL Externalize workflow data storage]**.
1. Selecteren **[!UICONTROL Save & Close]** om de eigenschappen op te slaan.

>[!NOTE]
>
>De opties om de Assign stap van de Taak als ontwerp te bewaren en de geschiedenis van de Assign stap van de Taak terug te winnen worden onbruikbaar gemaakt wanneer u een AEM werkschemamodel voor externe gegevensopslag vormt.

### Richtlijnen voor AEM werkstromen voor externe gegevensopslag {#guidelines-workflows-external-data-storage}

Hieronder volgen de richtlijnen voor het gebruik van AEM Workflows en het opslaan van gegevens naar externe gegevensopslagsystemen, zoals Microsoft Azure-opslagserver:

* Gebruik variabelen om gegevens op te slaan tijdens het definiëren van invoer- en uitvoergegevensbestanden en bijlagen in stappen van het workflowmodel. Niet selecteren **[!UICONTROL Relative to Payload]** en **[!UICONTROL Available at an absolute path]** opties. De **[!UICONTROL Relative to Payload]** en **[!UICONTROL Available at an absolute path]** opties worden niet automatisch weergegeven als u [configureren van een AEM workflowmodel voor externe gegevensopslag](#configure-workflow-external-data-storage).

* Gebruik variabelen om gegevensbestand en gehechtheid op te slaan terwijl het voorleggen van een adaptief formulier aan een AEMWerkstroom. Niet selecteren **[!UICONTROL Relative to Payload]** en een aangepast formulier naar een AEM workflow te verzenden. De **[!UICONTROL Relative to Payload]** Deze optie wordt niet automatisch weergegeven als u [configureren van een AEM workflowmodel voor externe gegevensopslag](#configure-workflow-external-data-storage).

* Gebruik geen aangepaste AEM Workflowstap in een workflowmodel voor het opslaan van gegevens in de CRX DE-opslagplaats.

* Wanneer u [configureren van een AEM workflowmodel voor externe gegevensopslag](#configure-workflow-external-data-storage)Creëer geen aangepaste kolommen voor AEM Inbox, aangezien de waarden van de aangepaste kolommen niet worden opgehaald als het werkitem in AEM Inbox tot een workflow behoort die is gemarkeerd voor externe opslag.

>[!MORELIKETHIS]
>
>* [Gegevensbronnen configureren voor AEM Forms](/help/forms/configure-data-sources.md)
>* [Azure-opslag voor AEM Forms configureren](/help/forms/configure-azure-storage.md)
>* [Integreer Microsoft Dynamics 365 en Salesforce met Adaptive Forms](/help/forms/configure-msdynamics-salesforce.md)
>  [Forms Portal toevoegen aan een AEM Sites-pagina](/help/forms/configure-forms-portal.md)
