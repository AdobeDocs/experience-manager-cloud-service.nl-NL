---
title: Hoe te om Verenigde Verbinding van de Opslag voor AEM Forms te vormen?
description: Leer hoe u Unified Storage Connector voor AEM Forms beheert. Gebruik de Unified Storage-connector om AEM Forms aan te sluiten op externe gegevensopslagsystemen.
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 1%

---


# Unified Storage-connector beheren voor AEM Forms {#manage-unified-storage-connector}

Met Unified Storage Connector kunt u AEM Forms verbinden met externe gegevensopslag.

U kunt bijvoorbeeld waarden invullen voor velden in een adaptief formulier en deze verzenden naar een AEM Workflow. U kunt AEM Workflows verder configureren om gegevens op te slaan in een externe opslag, zoals de Microsoft Azure-opslagserver. Gebruik de Unified Storage-connector om een verbinding tot stand te brengen tussen AEM Workflows en de externe opslag.

## Connect AEM Workflows met een Microsoft Azure-opslagserver {#connect-workflows-with-azure}

Creeer een Azure opslagconfiguratie en verwijs naar die configuratie gebruikend de Verenigde Schakelaar van de Opslag. Vervolgens kunt u AEM workflowmodellen configureren om de gegevensopslag te extern te maken en deze aan te sluiten op een Azure-opslagserver.

### Maken [!DNL Azure] opslagconfiguratie {#create-azure-storage-configuration}

Controleer voordat u deze stappen uitvoert of u een [!DNL Azure] opslagaccount en een toegangstoets om de toegang tot de [!DNL Azure] opslagaccount.

Voer de volgende stappen uit om een [!DNL Azure] opslagconfiguratie:

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure Storage]**.
1. Selecteer een map om de configuratie te maken en tik op **[!UICONTROL Create]**.
1. Geef een titel voor de configuratie op in het dialoogvenster **[!UICONTROL Title]** veld.
1. Geef de naam van de [!DNL Azure] opslagaccount in de **[!UICONTROL Azure Storage Account]** veld.
1. Geef de sleutel op voor toegang tot Azure-opslagaccount in het dialoogvenster **[!UICONTROL Azure Access Key]** veld en tik **[!UICONTROL Save]**.

### Unified Storage-connector configureren voor AEM workflows {#configure-unified-storage-connector-workflows}

Voer de volgende stappen uit om de Verenigde Verbinding van de Opslag voor AEM Workflows te vormen:

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Unified Storage Connector]**.

1. In de **[!UICONTROL Workflow]** sectie, selecteren **[!UICONTROL Azure]** in de vervolgkeuzelijst Opslag.
1. Geef de [configuratiepad voor de Azure-opslagconfiguratie](#create-azure-storage-configuration) in de **[!UICONTROL Storage Configuration Path]** veld.
1. Tikken **[!UICONTROL Publish]** en tik vervolgens op **[!UICONTROL Save]** om de configuratie op te slaan.

### Een AEM workflowmodel voor externe gegevensopslag configureren {#configure-workflow-external-data-storage}

Voer de volgende stappen uit om een AEM workflowmodel voor een externe gegevensopslag te configureren:

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteer een modelnaam en tik op **[!UICONTROL Edit]**.
1. Tik op het pictogram Pagina-informatie en tik op **[!UICONTROL Open Properties]**.
1. Selecteer **[!UICONTROL Externalize workflow data storage]**.
1. Tikken **[!UICONTROL Save & Close]** om de eigenschappen op te slaan.

>[!NOTE]
>
>De opties om de Assign stap van de Taak als ontwerp te bewaren en de geschiedenis van de Assign stap van de Taak terug te winnen zijn niet beschikbaar wanneer u een AEM werkschemamodel voor externe gegevensopslag vormt.

### Richtlijnen voor AEM werkstromen voor externe gegevensopslag {#guidelines-workflows-external-data-storage}

Hieronder volgen de richtlijnen voor het gebruik van AEM Workflows en het opslaan van gegevens naar externe gegevensopslagsystemen, zoals Microsoft Azure-opslagserver:

* Gebruik variabelen om gegevens op te slaan tijdens het definiëren van invoer- en uitvoergegevensbestanden en bijlagen in stappen van het workflowmodel. Niet selecteren **[!UICONTROL Relative to Payload]** en **[!UICONTROL Available at an absolute path]** opties. De **[!UICONTROL Relative to Payload]** en **Beschikbaar op een absoluut pad** opties worden niet automatisch weergegeven als u [configureren van een AEM workflowmodel voor externe gegevensopslag](#configure-workflow-external-data-storage).

* Gebruik variabelen om gegevensbestand en gehechtheid op te slaan terwijl het voorleggen van een adaptief formulier aan een AEMWerkstroom. Niet selecteren **[!UICONTROL Relative to Payload]** en een aangepast formulier naar een AEM workflow te verzenden. De **[!UICONTROL Relative to Payload]** Deze optie wordt niet automatisch weergegeven als u [configureren van een AEM workflowmodel voor externe gegevensopslag](#configure-workflow-external-data-storage).

* Gebruik geen aangepaste AEM Workflowstap in een workflowmodel voor het opslaan van gegevens in de CRX DE-opslagplaats.

* Wanneer u [configureren van een AEM workflowmodel voor externe gegevensopslag](#configure-workflow-external-data-storage)Maak geen aangepaste kolommen voor AEM Inbox op basis van de gegevens van een workflow.
