---
Title: How to connect AEM Adaptive Forms with Azure Blob Storage?
Description: Learn how to create an Azure Blob Storage Configuration in AEM Forms and use it within your Adaptive Forms for efficient data storage.
keywords: Azure Blob Storage-integratie met AEM Forms, gegevens verzenden naar Azure Storage, Azure Storage Configuration in AEM Forms maken, Azure Blob Storage gebruiken in Adaptive Forms Submit Action
feature: Adaptive Forms, Core Components
exl-id: 0c9f8f85-c4e9-4c79-bd0b-abdcac99a2d4
title: "Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?"
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# Een adaptief formulier verzenden naar Azure Blob Storage

Met de **[!UICONTROL Submit to Azure Blob Storage]** -actie Verzenden wordt een adaptief formulier verbonden met een Microsoft® Azure-portal. U kunt de formuliergegevens, bestanden, bijlagen of Document of Record verzenden naar de aangesloten Azure Storage-containers.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. U kunt meer over deze opties leren in het [ AanpassingsVorm voorlegt Artikel van de Actie ](/help/forms/configure-submit-actions-core-components.md).

## Voordelen

De voordelen van de integratie van Azure Blob Storage met AEM Forms zijn:

* Het helpt bij het stroomlijnen van het proces voor het verzenden van adaptieve formuliergegevens, bestanden, bijlagen en Document of Record naar Azure Storage-containers.
* Het gebruikt Azure Blob Storage voor gecentraliseerde en georganiseerde opslag van Adaptive Form-verzendingen.

## AEM Forms verbinden met Microsoft® Azure Blob Storage

Om Azure Blob Storage te gebruiken in Adaptive Forms Submit Action:

1. [ creeer een Azure BlobContainer van de Opslag ](#create-a-azure-blob-storage-container-create-azure-configuration): Het verbindt AEM Forms met de containers van de Azure Opslag.
2. [ Gebruik de Azure Configuratie van de Opslag in een AanpassingsVorm ](#use-azure-storage-configuration-in-an-adaptive-form-use-azure-storage-configuartion-in-af): Het verbindt uw AanpassingsVorm met gevormde de containers van de Opslag Azure.

### Een Azure Blob Storage Container maken {#create-azure-configuration}

AEM Forms aansluiten op uw Azure Storage-containers:
1. Ga naar uw **1&rbrace; instantie van de Auteur van AEM Forms >**&#x200B;[!UICONTROL Tools]&#x200B;**>**&#x200B;[!UICONTROL Cloud Services]&#x200B;**>**&#x200B;[!UICONTROL Azure Storage]&#x200B;**.**
1. Nadat u de **[!UICONTROL Azure Storage]** hebt geselecteerd, wordt u omgeleid naar **[!UICONTROL Azure Storage Browser]** .
1. Selecteer de Container van de a **Configuratie**. De configuratie wordt opgeslagen in de geselecteerde Container van de Configuratie.
1. Klik op **[!UICONTROL Create]**. De wizard Azure Storage Configuration wordt weergegeven.

   ![ Azure Configuratie van de Opslag ](/help/forms/assets/azure-storage-configuration.png)

1. Geef de waarden **[!UICONTROL Title]** , **[!UICONTROL Azure Storage Account]** en **[!UICONTROL Azure Access key]** op.

   * U kunt `Azure Storage Account` name and `Azure Access key` ophalen van Storage Accounts in de Microsoft® Azure-portal.
<!--

    >[!NOTE]
    >
    > The URL for **[!UICONTROL Azure Blob Endpoint]** is automatically appended to the textbox when a value is entered for **[!UICONTROL Azure Storage Account]**. You can update the Azure Blob End Point URL with your custom domain. Steps to update URL for **[!UICONTROL Azure Blob End Point]**:
    > 1. [Enable the AEM Advance Networking VPN support](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html)
    > 1. [Enable dedicated egress IP link](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html)
    > 1. [Map custom domain to azure blob storage](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-custom-domain-name?tabs=azure-portal)
-->

1. Klik op **[!UICONTROL Save]**.

Nu kunt u deze Azure Storage Container-configuratie gebruiken voor de verzendactie in een adaptief formulier.

### Azure Storage Configuration in een Adaptive Form gebruiken {#use-azure-storage-configuartion-in-af}

U kunt de gemaakte Azure Storage Container-configuratie in een Adaptief formulier gebruiken om gegevens of gegenereerd Document of Record in Azure Storage-container op te slaan. Voer de volgende stappen uit om de configuratie van de Azure Storage container in een Adaptief formulier te gebruiken als:
1. Creeer een [ Aangepaste Vorm ](/help/forms/creating-adaptive-form-core-components.md).

   >[!NOTE]
   >
   > * Selecteer hetzelfde [!UICONTROL Configuration Container] voor een adaptief formulier, waar u OneDrive-opslagruimte hebt gemaakt.
   > * Als er geen [!UICONTROL Configuration Container] is geselecteerd, worden de algemene [!UICONTROL Storage Configuration] -mappen weergegeven in het eigenschappenvenster Handeling verzenden.

1. Selecteer **voorleggen Actie** als **[!UICONTROL Submit to Azure Blob Storage]**.
   ![ Azure Blob Storage GIF ](/help/forms/assets/azure-submit-video.gif)

1. Selecteer **[!UICONTROL Storage Configuration]** waar u de gegevens wilt opslaan.
1. Klik op **[!UICONTROL Save]** om de verzendinstellingen op te slaan.

Wanneer u het formulier verzendt, worden de gegevens opgeslagen in de opgegeven configuratie van de Azure Storage Container.
De mapstructuur voor het opslaan van gegevens is `/configuration_container/form_name/year/month/date/submission_id/data` .

## Verwante artikelen

{{af-submit-action}}
