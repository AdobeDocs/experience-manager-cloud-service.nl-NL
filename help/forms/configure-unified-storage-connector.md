---
title: Hoe te om Verenigde Schakelaar van de Opslag (USC) voor AEM Forms te vormen?
description: Leer hoe te om Verenigde Schakelaar van de Opslag (USC) voor AEM Forms te beheren. Gebruik de Unified Storage Connector (USC) om AEM Forms te verbinden met externe gegevensopslag.
role: Admin, Developer, User
feature: Adaptive Forms, Workflow
exl-id: c93d0242-0c15-4d69-82a1-d6fcc7da4bae
source-git-commit: c17e4e70fa8cec176c908983230b03f2899bc1ca
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Unified Storage Connector (USC) voor AEM Forms beheren {#manage-unified-storage-connector}

U kunt Unified Storage Connector (USC) gebruiken om AEM Forms te verbinden met externe gegevensopslag.

U kunt bijvoorbeeld waarden invullen voor velden in een adaptief formulier en deze verzenden naar een AEM Workflow. U kunt AEM Workflows verder configureren om gegevens op te slaan in een externe opslagruimte, zoals de Microsoft Azure-opslagserver. Gebruik de Unified Storage Connector (USC) om een verbinding tot stand te brengen tussen AEM Workflows en de externe opslag.

## AEM Workflows verbinden met een Microsoft Azure-opslagserver {#connect-workflows-with-azure}

Creeer een Azure opslagconfiguratie en verwijs naar die configuratie gebruikend de Verenigde Schakelaar van de Opslag (USC). Vervolgens kunt u AEM Workflow-modellen configureren om de gegevensopslag te extern te maken en deze aan te sluiten op een Azure-opslagserver.

### [!DNL Azure] opslagconfiguratie maken {#create-azure-storage-configuration}

Controleer voordat u deze stappen uitvoert of u een [!DNL Azure] opslagaccount en een toegangstoets hebt om de toegang tot de [!DNL Azure] -opslagaccount te autoriseren.

Voer de volgende stappen uit om een [!DNL Azure] opslagconfiguratie te maken:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure Storage]** .
1. Selecteer een map om de configuratie te maken en selecteer **[!UICONTROL Create]** .
1. Geef een titel voor de configuratie op in het veld **[!UICONTROL Title]** .
1. Geef de naam van de [!DNL Azure] -opslagaccount op in het veld **[!UICONTROL Azure Storage Account]** .
1. Geef in het veld **[!UICONTROL Azure Access Key]** de sleutel op voor toegang tot Azure-opslagaccount en selecteer **[!UICONTROL Save]** .

### Unified Storage Connector (USC) voor AEM Workflows configureren {#configure-unified-storage-connector-workflows}

Voer de volgende stappen uit om Unified Storage Connector (USC) voor AEM Workflows te configureren:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Unified Storage Connector]** .

1. Selecteer in de sectie **[!UICONTROL Workflow]** de optie **[!UICONTROL Azure]** in de vervolgkeuzelijst Opslag.
1. Specificeer de [&#x200B; configuratieweg voor de Azure opslagconfiguratie &#x200B;](#create-azure-storage-configuration) op het **[!UICONTROL Storage Configuration Path]** gebied.
1. Selecteer **[!UICONTROL Publish]** en selecteer vervolgens **[!UICONTROL Save]** om de configuratie op te slaan.

### Een AEM-workflowmodel configureren voor externe gegevensopslag {#configure-workflow-external-data-storage}

Voer de volgende stappen uit om een AEM Workflowmodel voor externe gegevensopslag te configureren:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .
1. Selecteer een modelnaam en selecteer **[!UICONTROL Edit]** .
1. Selecteer het pictogram Pagina-informatie en selecteer **[!UICONTROL Open Properties]** .
1. Selecteer **[!UICONTROL Externalize workflow data storage]** .
1. Selecteer **[!UICONTROL Save & Close]** om de eigenschappen op te slaan.

>[!NOTE]
>
>De opties om de stap Taak toewijzen als concept op te slaan en de geschiedenis van de stap Taak toewijzen op te halen, zijn uitgeschakeld wanneer u een AEM-workflowmodel voor externe gegevensopslag configureert.

### Richtlijnen voor AEM-workflows voor externe gegevensopslag {#guidelines-workflows-external-data-storage}

Hieronder volgen de richtlijnen voor het gebruik van AEM Workflows en het opslaan van gegevens naar externe gegevensopslagsystemen, zoals Microsoft Azure-opslagserver:

* Gebruik variabelen om gegevens op te slaan tijdens het definiëren van invoer- en uitvoergegevensbestanden en bijlagen in stappen van het workflowmodel. Selecteer geen opties **[!UICONTROL Relative to Payload]** en **[!UICONTROL Available at an absolute path]** . De **[!UICONTROL Relative to Payload]** en **[!UICONTROL Available at an absolute path]** opties tonen automatisch niet zodra u [&#x200B; een model van het Werkschema van AEM voor externe gegevensopslag &#x200B;](#configure-workflow-external-data-storage) vormt.

* Gebruik variabelen om gegevensbestanden en bijlagen op te slaan wanneer u een adaptief formulier naar een AEM Workflow verzendt. Selecteer de optie **[!UICONTROL Relative to Payload]** niet als u een adaptief formulier naar een AEM-workflow verzendt. De **[!UICONTROL Relative to Payload]** optie toont automatisch niet zodra u [&#x200B; een model van het Werkschema van AEM voor externe gegevensopslag &#x200B;](#configure-workflow-external-data-storage) vormt.

* Gebruik geen aangepaste AEM Workflow-stap in een workflowmodel voor het opslaan van gegevens in de CRX DE-opslagruimte.

* Wanneer u [&#x200B; een model van het Werkschema van AEM voor externe gegevensopslag &#x200B;](#configure-workflow-external-data-storage) vormt, creeer geen douanekolommen voor AEM Inbox aangezien de waarden van de douanekolommen niet worden gehaald als het werkpunt in AEM Inbox tot een werkschema behoort dat voor externe opslag duidelijk is.

>[!MORELIKETHIS]
>
>* [&#x200B; vorm gegevensbronnen voor AEM Forms &#x200B;](/help/forms/configure-data-sources.md)
>* [&#x200B; vorm Azure opslag voor AEM Forms &#x200B;](/help/forms/configure-azure-storage.md)
>* [&#x200B; integreer Microsoft Dynamics 365 &#x200B;](/help/forms/configure-msdynamics.md)
>  [Forms Portal toevoegen aan een AEM Sites-pagina &#x200B;](/help/forms/configure-forms-portal.md)
