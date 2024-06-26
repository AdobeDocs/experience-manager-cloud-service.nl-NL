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

De **[!UICONTROL Submit to Azure Blob Storage]**  Met Actie verzenden wordt een adaptief formulier verbonden met een Microsoft® Azure-portal. U kunt de formuliergegevens, bestanden, bijlagen of Document of Record verzenden naar de aangesloten Azure Storage-containers.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. Meer informatie over deze opties vindt u in het gedeelte [Handeling Adaptief verzenden van formulier](/help/forms/configure-submit-actions-core-components.md) artikel.

## Voordelen

De voordelen van de integratie van Azure Blob Storage met AEM Forms zijn:

* Het helpt bij het stroomlijnen van het proces voor het verzenden van adaptieve formuliergegevens, bestanden, bijlagen en Document of Record naar Azure Storage-containers.
* Het gebruikt Azure Blob Storage voor gecentraliseerde en georganiseerde opslag van Adaptive Form-verzendingen.

## AEM Forms verbinden met Microsoft® Azure Blob Storage

Om Azure Blob Storage te gebruiken in Adaptive Forms Submit Action:

1. [Een Azure Blob Storage Container maken](#create-a-azure-blob-storage-container-create-azure-configuration): AEM Forms wordt aangesloten op Azure Storage containers.
2. [Azure Storage Configuration in een Adaptive Form gebruiken](#use-azure-storage-configuration-in-an-adaptive-form-use-azure-storage-configuartion-in-af): Het verbindt uw Adaptief Vorm met gevormde Azure opslagcontainers.

### Een Azure Blob Storage Container maken {#create-azure-configuration}

AEM Forms aansluiten op uw Azure Storage-containers:
1. Ga naar uw **AEM Forms-auteur** instance > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Azure Storage]**.
1. Wanneer u de **[!UICONTROL Azure Storage]**, u wordt doorgestuurd naar **[!UICONTROL Azure Storage Browser]**.
1. Selecteer een **Configuratie-container**. De configuratie wordt opgeslagen in de geselecteerde Container van de Configuratie.
1. Klik op **[!UICONTROL Create]**. De wizard Azure Storage Configuration wordt weergegeven.

   ![Azure Storage Configuration](/help/forms/assets/azure-storage-configuration.png)

1. Geef de **[!UICONTROL Title]**, **[!UICONTROL Azure Storage Account]** en **[!UICONTROL Azure Access key]**.

   * U kunt `Azure Storage Account` naam en `Azure Access key` van de Opslagaccounts in de Microsoft® Azure-portal.
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
1. Een [Adaptief formulier](/help/forms/creating-adaptive-form-core-components.md).

   >[!NOTE]
   >
   > * Hetzelfde selecteren [!UICONTROL Configuration Container] voor een adaptief formulier, waar u uw OneDrive-opslag hebt gemaakt.
   > * Indien niet [!UICONTROL Configuration Container] is geselecteerd, dan is de globale [!UICONTROL Storage Configuration] worden weergegeven in het eigenschappenvenster Handeling verzenden.

1. Selecteren **Handeling verzenden** als **[!UICONTROL Submit to Azure Blob Storage]**.
   ![Azure Blob Storage GIF](/help/forms/assets/azure-submit-video.gif)

1. Selecteer de **[!UICONTROL Storage Configuration]**, waar u de gegevens wilt opslaan.
1. Klikken **[!UICONTROL Save]** om de verzendinstellingen op te slaan.

Wanneer u het formulier verzendt, worden de gegevens opgeslagen in de opgegeven configuratie van de Azure Storage Container.
De mapstructuur voor het opslaan van gegevens is `/configuration_container/form_name/year/month/date/submission_id/data`.

## Verwante artikelen

{{af-submit-action}}
