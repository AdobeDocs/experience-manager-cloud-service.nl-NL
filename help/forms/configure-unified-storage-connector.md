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

### [!DNL Azure] opslagconfiguratie maken {#create-azure-storage-configuration}

Controleer voordat u deze stappen uitvoert of u een [!DNL Azure] opslagaccount en een toegangstoets hebt om de toegang tot de [!DNL Azure] -opslagaccount te autoriseren.

Voer de volgende stappen uit om een [!DNL Azure] opslagconfiguratie te maken:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure Storage]** .
1. Selecteer een map om de configuratie te maken en selecteer **[!UICONTROL Create]** .
1. Geef een titel voor de configuratie op in het veld **[!UICONTROL Title]** .
1. Geef de naam van de [!DNL Azure] -opslagaccount op in het veld **[!UICONTROL Azure Storage Account]** .
1. Geef in het veld **[!UICONTROL Azure Access Key]** de sleutel op voor toegang tot Azure-opslagaccount en selecteer **[!UICONTROL Save]** .

### Unified Storage Connector (USC) voor AEM workflows configureren {#configure-unified-storage-connector-workflows}

Voer de volgende stappen uit om Verenigde Verbinding van de Opslag (USC) voor AEM Workflows te vormen:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Unified Storage Connector]** .

1. Selecteer in de sectie **[!UICONTROL Workflow]** de optie **[!UICONTROL Azure]** in de vervolgkeuzelijst Opslag.
1. Specificeer de [ configuratieweg voor de Azure opslagconfiguratie ](#create-azure-storage-configuration) op het **[!UICONTROL Storage Configuration Path]** gebied.
1. Selecteer **[!UICONTROL Publish]** en selecteer vervolgens **[!UICONTROL Save]** om de configuratie op te slaan.

### Een AEM workflowmodel voor externe gegevensopslag configureren {#configure-workflow-external-data-storage}

Voer de volgende stappen uit om een AEM workflowmodel voor een externe gegevensopslag te configureren:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .
1. Selecteer een modelnaam en selecteer **[!UICONTROL Edit]** .
1. Selecteer het pictogram Pagina-informatie en selecteer **[!UICONTROL Open Properties]** .
1. Selecteer **[!UICONTROL Externalize workflow data storage]** .
1. Selecteer **[!UICONTROL Save & Close]** om de eigenschappen op te slaan.

>[!NOTE]
>
>De opties om de Assign stap van de Taak als ontwerp te bewaren en de geschiedenis van de Assign stap van de Taak terug te winnen worden onbruikbaar gemaakt wanneer u een AEM werkschemamodel voor externe gegevensopslag vormt.

### Richtlijnen voor AEM werkstromen voor externe gegevensopslag {#guidelines-workflows-external-data-storage}

Hieronder volgen de richtlijnen voor het gebruik van AEM Workflows en het opslaan van gegevens naar externe gegevensopslagsystemen, zoals Microsoft Azure-opslagserver:

* Gebruik variabelen om gegevens op te slaan tijdens het definiëren van invoer- en uitvoergegevensbestanden en bijlagen in stappen van het workflowmodel. Selecteer geen opties **[!UICONTROL Relative to Payload]** en **[!UICONTROL Available at an absolute path]** . De **[!UICONTROL Relative to Payload]** en **[!UICONTROL Available at an absolute path]** opties tonen automatisch niet zodra u [ een model van het Werkschema van de AEM voor externe gegevensopslag ](#configure-workflow-external-data-storage) vormt.

* Gebruik variabelen om gegevensbestand en gehechtheid op te slaan terwijl het voorleggen van een adaptief formulier aan een AEMWerkstroom. Selecteer de optie **[!UICONTROL Relative to Payload]** niet als u een adaptief formulier naar een AEM workflow verzendt. De **[!UICONTROL Relative to Payload]** optie toont automatisch niet zodra u [ een model van het Werkschema van de AEM voor externe gegevensopslag ](#configure-workflow-external-data-storage) vormt.

* Gebruik geen aangepaste AEM Workflowstap in een workflowmodel voor het opslaan van gegevens in de CRX DE-opslagplaats.

* Wanneer u [ een model van het Werkschema van de AEM voor externe gegevensopslag ](#configure-workflow-external-data-storage) vormt, creeer geen douanekolommen voor AEM Inbox aangezien de waarden van de douanekolommen niet worden gehaald als het werkpunt in AEM Inbox tot een werkschema behoort dat voor externe opslag duidelijk is.

>[!MORELIKETHIS]
>
>* [ vorm gegevensbronnen voor AEM Forms ](/help/forms/configure-data-sources.md)
>* [ vorm Azure opslag voor AEM Forms ](/help/forms/configure-azure-storage.md)
>* [ integreer de Dynamiek 365 van Microsoft en Salesforce met Aanpassings Forms ](/help/forms/configure-msdynamics-salesforce.md)
>  [Forms Portal toevoegen aan een AEM Sites-pagina ](/help/forms/configure-forms-portal.md)
