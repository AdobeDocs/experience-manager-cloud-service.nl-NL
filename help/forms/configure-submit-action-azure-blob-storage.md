---
title: Hoe kan ik AEM Adaptive Forms verbinden met Azure Blob Storage?
description: Leer hoe u een Azure Blob Storage Configuration in AEM Forms maakt en deze in uw Adaptive Forms gebruikt voor efficiënte gegevensopslag.
keywords: Azure Blob Storage integratie met AEM Forms, gegevens verzenden naar Azure Storage, Azure Storage Configuration maken in AEM Forms, Azure Blob Storage gebruiken in Adaptive Forms Submit Action
feature: Adaptive Forms, Foundation Components, Edge Delivery Services, Core Components
badgeSaas: label="AEM Forms" type="Positive" tooltip="van toepassing op AEM Forms)."
exl-id: 0c9f8f85-c4e9-4c79-bd0b-abdcac99a2d4
role: User, Developer
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 1%

---

# Een adaptief formulier verzenden naar Azure Blob Storage

Met de handeling **[!UICONTROL Submit to Azure Blob Storage]** Verzenden wordt een adaptief formulier verbonden met een Microsoft® Azure-portal. U kunt de formuliergegevens, bestanden, bijlagen of Document of Record verzenden naar de aangesloten Azure Storage-containers.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. U kunt meer over deze opties leren in het [&#x200B; AanpassingsVorm voorlegt Artikel van de Actie &#x200B;](/help/forms/aem-forms-submit-action.md).

## Voordelen

De integratie van Azure Blob Storage met AEM Forms biedt onder andere de volgende voordelen:

* Hiermee kunt u het verzenden van adaptieve formuliergegevens, bestanden, bijlagen en Document of Record naar Azure Storage-containers stroomlijnen.
* Het gebruikt Azure Blob Storage voor gecentraliseerde en georganiseerde opslag van Adaptive Form-verzendingen.

## AEM Forms verbinden met Microsoft® Azure Blob Storage

Azure Blob-opslag gebruiken in Adaptive Forms Submit-actie:

1. [&#x200B; creeer een Container van de Opslag van Azure Blob &#x200B;](#create-a-azure-blob-storage-container-create-azure-configuration): Het verbindt AEM Forms met de containers van de Opslag van Azure.
2. [&#x200B; de Configuratie van de Opslag van Azure van het gebruik in een AanpassingsVorm &#x200B;](#use-azure-storage-configuration-in-an-adaptive-form-use-azure-storage-configuartion-in-af): Het verbindt uw AanpassingsVorm met de gevormde containers van de Opslag van Azure.

### Een Azure Blob Storage Container maken {#create-azure-configuration}

AEM Forms aansluiten op uw Azure Storage containers:

1. Ga naar uw **1&rbrace; instantie van de Auteur van AEM Forms >** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]**.**[!UICONTROL Azure Storage]**
1. Nadat u de **[!UICONTROL Azure Storage]** hebt geselecteerd, wordt u omgeleid naar **[!UICONTROL Azure Storage Browser]** .
1. Selecteer de Container van de a **Configuratie**. De configuratie wordt opgeslagen in de geselecteerde Container van de Configuratie.
1. Klik op **[!UICONTROL Create]**. De wizard Azure Storage Configuration maken wordt weergegeven.

   ![&#x200B; de Configuratie van de Opslag van Azure &#x200B;](/help/forms/assets/azure-storage-configuration.png)

1. Geef de waarden **[!UICONTROL Title]** , **[!UICONTROL Azure Storage Account]** en **[!UICONTROL Azure Access key]** op.

   * U kunt `Azure Storage Account` name and `Azure Access key` ophalen van Storage Accounts in de Microsoft® Azure portal.
<!--

    >[!NOTE]
    >
    > The URL for **[!UICONTROL Azure Blob Endpoint]** is automatically appended to the textbox when a value is entered for **[!UICONTROL Azure Storage Account]**. You can update the Azure Blob End Point URL with your custom domain. Steps to update URL for **[!UICONTROL Azure Blob End Point]**:
    > 1. [Enable the AEM Advance Networking VPN support](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=nl-NL)
    > 1. [Enable dedicated egress IP link](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=nl-NL)
    > 1. [Map custom domain to azure blob storage](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-custom-domain-name?tabs=azure-portal)
-->

1. Klik op **[!UICONTROL Save]**.

U kunt deze Azure Storage-containerconfiguratie nu gebruiken voor de verzendactie in een adaptief formulier.

### Azure Storage Configuration gebruiken in een adaptief formulier {#use-azure-storage-configuartion-in-af}

U kunt de gemaakte Azure Storage Container-configuratie in een adaptief formulier gebruiken om gegevens of gegenereerd Document of Record in Azure Storage-container op te slaan.

>[!NOTE]
>
> * Selecteer hetzelfde [!UICONTROL Configuration Container] voor een adaptief formulier, waar u OneDrive-opslagruimte hebt gemaakt.
> * Als er geen [!UICONTROL Configuration Container] is geselecteerd, worden de algemene [!UICONTROL Storage Configuration] -mappen weergegeven in het eigenschappenvenster Handeling verzenden.

>[!BEGINTABS]

>[!TAB  Component van de Stichting ]

Voer de volgende stappen uit om de containerconfiguratie van de Opslag van Azure in een AanpassingsVorm te gebruiken die op de Componenten van de Stichting wordt gebaseerd als:

1. Open het Adaptief formulier voor bewerking en ga naar de sectie **[!UICONTROL Submission]** van de eigenschappen van de container van adaptieve formulieren.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Submit to Azure Blob Storage]**.

   ![&#x200B; Azure Blob Storage GIF &#x200B;](/help/forms/assets/submit-to-azure-blob-fc.png) {width=50%,height=50%}

   U kunt Document of Record (DoR) ook opslaan in de Azure Blob-opslag.

1. Selecteer **[!UICONTROL Storage Configuration]** waar u de gegevens wilt opslaan.
1. Klik op **[!UICONTROL Save]** om de verzendinstellingen op te slaan.

Wanneer u het formulier verzendt, worden de gegevens opgeslagen in de opgegeven configuratie van de Azure Storage-container.
De mapstructuur voor het opslaan van gegevens is `/configuration_container/form_name/year/month/date/submission_id/data` .

>[!TAB  Component van de Kern ]

Voer de volgende stappen uit om Azure Storage containerconfiguratie te gebruiken in een adaptief formulier op basis van Core Components als:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![&#x200B; eigenschappen van de Gids &#x200B;](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de tab **[!UICONTROL Submission]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Submit to Azure Blob Storage]**.

   ![&#x200B; Azure Blob Storage GIF &#x200B;](/help/forms/assets/azure-submit-video.gif)

   U kunt Document of Record (DoR) ook opslaan in de Azure Blob-opslag.

1. Selecteer **[!UICONTROL Storage Configuration]** waar u de gegevens wilt opslaan.
1. Klik op **[!UICONTROL Save]** om de verzendinstellingen op te slaan.

Wanneer u het formulier verzendt, worden de gegevens opgeslagen in de opgegeven configuratie van de Azure Storage-container.
De mapstructuur voor het opslaan van gegevens is `/configuration_container/form_name/year/month/date/submission_id/data` .

>[!TAB  Universele Redacteur ]

Voer de volgende stappen uit om Azure Storage containerconfiguratie te gebruiken in een adaptief formulier dat is geschreven in Universal Editor:

1. Open het adaptieve formulier voor bewerking.
1. Klik **uitgeven de uitbreiding van de Eigenschappen van de Vorm** op de redacteur.
Het **de dialoogvakje van de Eigenschappen van de Vorm** verschijnt.

   >[!NOTE]
   >
   > * Als u niet **ziet geef de Eigenschappen van de Vorm** pictogram in uw Universele interface van de Redacteur uit, laat **toe geef de 3&rbrace; uitbreiding van de Eigenschappen van de Vorm &lbrace;in Extension Manager uit.**
   > * Verwijs naar het [&#x200B; artikel van de Hoogtepunten van de Eigenschap van 0&rbrace; Extension Manager om te leren hoe te om uitbreidingen in of onbruikbaar te maken in de Universele Redacteur.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

1. Klik **Verzending** lusje en selecteer **[!UICONTROL Submit to Azure Blob Storage]** voorlegt actie.
   ![&#x200B; Azure Blob Storage &#x200B;](/help/forms/assets/azure-blob-storage-ue.png)

   Als u **sparen Bijlagen met Oorspronkelijke Naam** selecteert, worden de gehechtheid opgeslagen in de omslag gebruikend hun originele filenames. U kunt Document of Record (DoR) ook opslaan in de Azure Blob-opslag.

1. Selecteer **[!UICONTROL Storage Configuration]** waar u de gegevens wilt opslaan.
1. Klik op **[!UICONTROL Save&Close]** om de verzendinstellingen op te slaan.

Wanneer u het formulier verzendt, worden de gegevens opgeslagen in de opgegeven configuratie van de Azure Storage-container.
De mapstructuur voor het opslaan van gegevens is `/configuration_container/form_name/year/month/date/submission_id/data` .

>[!ENDTABS]

## Verwante artikelen

{{af-submit-action}}
