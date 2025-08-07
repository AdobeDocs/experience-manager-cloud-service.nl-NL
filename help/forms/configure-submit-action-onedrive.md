---
Title: How to submit data from an Adaptive Form to Microsoft&reg; OneDrive?
Description: Explore the streamlined process of connecting AEM Forms with Microsoft&reg; OneDrive using the Submit to OneDrive Submit Action. Learn the step-by-step guide to configure OneDrive and set up submission actions for efficient data storage and retrieval
keywords: AEM Forms OneDrive-integratie, verbinding maken met Microsoft OneDrive, OneDrive-configuratie met AEM-formulieren
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
exl-id: dbfa4094-1b92-4a7c-a799-f66973d27054
title: Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?
role: User, Developer
source-git-commit: dabf8029577c5fb6bb5eebdbf10d77f3d4d95a5d
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 1%

---

# Een adaptief formulier verzenden naar Microsoft® OneDrive

Met de handeling **[!UICONTROL Submit to OneDrive]** Verzenden wordt een adaptief formulier verbonden met een Microsoft® OneDrive. U kunt de formuliergegevens, bestanden, bijlagen of het Document of Record verzenden naar de aangesloten Microsoft® OneDrive-opslag.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. U kunt meer over deze opties leren in het [ AanpassingsVorm voorlegt Artikel van de Actie ](/help/forms/aem-forms-submit-action.md).

## Voordelen

Een aantal voordelen van een naadloze integratie van AEM Forms en Microsoft® OneDrive zijn:

* De toegankelijkheid van OneDrive voor verschillende apparaten zorgt ervoor dat opgeslagen formuliergegevens gemakkelijk beschikbaar zijn op verschillende platforms. Gebruikers kunnen toegang krijgen tot de verzonden gegevens, bijlagen en documenten van desktops, laptops, tablets en mobiele apparaten, waardoor de toegankelijkheid en flexibiliteit worden verbeterd.
* OneDrive-integratie met AEM-formulieren biedt een betrouwbare en schaalbare oplossing voor efficiënte gegevensopslag. Alle verzendingen met een adaptief formulier, zoals bestanden, bijlagen en Document of Record, kunnen eenvoudig in OneDrive worden opgeslagen en zo georganiseerde en toegankelijke gegevens garanderen.

## OneDrive aansluiten op een adaptief formulier

>[!VIDEO](https://video.tv.adobe.com/v/3424864/connect-aem-adaptive-form-to-onedrive/?quality=12&learn=on)

<span> Deze video is alleen van toepassing op Core Components. Voor de Componenten van de UE/Foundation, gelieve naar het artikel te verwijzen.</span>

Voer de volgende stappen uit als OneDrive wordt geconfigureerd voor AEM Forms-verzending:

1. [ creeer een Configuratie OneDrive ](#create-a-onedrive-configuration-create-onedrive-configuration): Het verbindt AEM Forms met uw Opslag van Microsoft® OneDrive.
2. [ gebruik Submit aan OneDrive voorlegt actie in een Aangepast Vorm ](#use-onedrive-configuration-in-an-adaptive-form-use-onedrive-configuartion-in-af): Het verbindt uw Aangepast Vorm met gevormde Microsoft® OneDrive.

### Een OneDrive-configuratie maken {#create-onedrice-configuration}

AEM Forms aansluiten op uw Microsoft® OneDrive-opslag:

1. Ga naar uw **1} instantie van de Auteur van AEM Forms >** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]**.**[!UICONTROL Microsoft® OneDrive]**
1. Nadat u de **[!UICONTROL Microsoft® OneDrive]** hebt geselecteerd, wordt u omgeleid naar **[!UICONTROL OneDrive Browser]** .
1. Selecteer de Container van de a **Configuratie**. De configuratie wordt opgeslagen in de geselecteerde Container van de Configuratie.
1. Klik op **[!UICONTROL Create]**. De OneDrive-configuratietovenaar wordt weergegeven.

   ![ het Scherm van de Configuratie OneDrive ](/help/forms/assets/onedrive-configuration.png)

1. Geef de waarden **[!UICONTROL Title]** , **[!UICONTROL Client ID]** , **[!UICONTROL Client Secret]** en **[!UICONTROL OAuth URL]** op. Voor informatie over hoe te om identiteitskaart van de Cliënt terug te winnen, Geheime cliënt, identiteitskaart van de Aannemer voor OAuth URL, zie [ Documentatie Microsoft® ](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
   * U kunt de `Client ID` en `Client Secret` van uw app ophalen via de Microsoft® Azure-portal.
   * Voeg in de Microsoft® Azure-portal de Redirect URI toe als `https://[author-instance]/libs/cq/onedrive/content/configurations/wizard.html` . Vervang `[author-instance]` door de URL van de instantie Auteur.
   * Voeg de API-machtigingen `offline_access` en `Files.ReadWrite.All` toe voor lees- en schrijfmachtigingen.
   * Gebruik OAuth URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Vervang `<tenant-id>` door `tenant-id` van uw app via de Microsoft® Azure-portal.

   >[!NOTE]
   >
   > Het **cliënt geheime** gebied is verplicht of facultatief hangt van uw Azure Actieve de toepassingsconfiguratie van de Folder af. Als uw toepassing wordt gevormd om een cliëntgeheim te gebruiken, is het verplicht om het cliëntgeheim te verstrekken.

1. Klik op **[!UICONTROL Connect]**. Bij een geslaagde verbinding wordt het bericht `Connection Successful` weergegeven.

1. Nu, selecteer **[!UICONTROL OneDrive Container]** > **[Omslag OneDrive]** om de gegevens te bewaren.

   >[!NOTE]
   >
   >* Standaard is `forms-ootb-storage-adaptive-forms-submission` aanwezig in OneDrive-container.
   > * Creeer een omslag als `forms-ootb-storage-adaptive-forms-submission`, als niet reeds aanwezig door **te klikken creeer Omslag**.

U kunt deze OneDrive-opslagconfiguratie nu gebruiken voor de verzendactie in een adaptief formulier.

### OneDrive-configuratie gebruiken in een adaptief formulier {#use-onedrive-configuartion-in-af}

U kunt de gemaakte OneDrive-opslagconfiguratie in een adaptief formulier gebruiken om gegevens of gegenereerd document met record op te slaan in een OneDrive-map.

>[!NOTE]
>
> * Selecteer hetzelfde [!UICONTROL Configuration Container] voor een adaptief formulier, waar u OneDrive-opslagruimte hebt gemaakt.
> * Als er geen [!UICONTROL Configuration Container] is geselecteerd, worden de algemene [!UICONTROL Storage Configuration] -mappen weergegeven in het eigenschappenvenster Handeling verzenden.

>[!BEGINTABS]

>[!TAB  Component van de Stichting ]

Voer de volgende stappen uit om de opslagconfiguratie OneDrive in een AanpassingsVorm te gebruiken die op de Component van de Stichting wordt gebaseerd als:

1. Open het Adaptief formulier voor bewerking en ga naar de sectie **[!UICONTROL Submission]** van de eigenschappen van de container van adaptieve formulieren.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Submit to OneDrive]**.
   ![ OneDrive GIF ](/help/forms/assets/wubmit-to-onedrive-fc.png) {width=50%, height=50%}
U kunt Document of Record (DoR) ook opslaan in OneDrive.
1. Selecteer **[!UICONTROL Storage Configuration]** waar u de gegevens wilt opslaan.
1. Klik op **[!UICONTROL Save]** om de verzendinstellingen op te slaan.

Wanneer u het formulier verzendt, worden de gegevens opgeslagen in de opgegeven Microsoft® OneDrive-opslag.
De mapstructuur voor het opslaan van gegevens is `/folder_name/form_name/year/month/date/submission_id/data` .

>[!TAB  Component van de Kern ]

Voer de volgende stappen uit om de OneDrive-opslagconfiguratie in een adaptief formulier op basis van de Core Component te gebruiken als:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de tab **[!UICONTROL Submission]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Submit to OneDrive]**.
   ![ OneDrive GIF ](/help/forms/assets/onedrive-video.gif)
U kunt Document of Record (DoR) ook opslaan in OneDrive.
1. Selecteer **[!UICONTROL Storage Configuration]** waar u de gegevens wilt opslaan.
1. Klik op **[!UICONTROL Save]** om de verzendinstellingen op te slaan.

>[!TAB  Universele Redacteur ]

Voer de volgende stappen uit om de OneDrive-opslagconfiguratie te gebruiken in een adaptief formulier dat is geschreven in de Universal Editor:

1. Open het adaptieve formulier voor bewerking.
1. Klik **uitgeven de uitbreiding van de Eigenschappen van de Vorm** op de redacteur.
Het **de dialoogvakje van de Eigenschappen van de Vorm** verschijnt.

   >[!NOTE]
   >
   > * Als u niet **ziet geef de Eigenschappen van de Vorm** pictogram in uw Universele interface van de Redacteur uit, laat **toe geef de 3} uitbreiding van de Eigenschappen van de Vorm {in Extension Manager uit.**
   > * Verwijs naar het [ artikel van de Hoogtepunten van de Eigenschap van 0} Extension Manager om te leren hoe te om uitbreidingen in of onbruikbaar te maken in de Universele Redacteur.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)
1. Klik **Verzending** tabel en selecteer **[!UICONTROL Submit to OneDrive]**.
   ![ OneDrive GIF ](/help/forms/assets/submit-to-onedrive-ue.png)
Als u **sparen Bijlagen met Oorspronkelijke Naam** selecteert, worden de gehechtheid opgeslagen in de omslag gebruikend hun originele filenames. U kunt Document of Record (DoR) ook opslaan in de Azure Blob Storage.
1. Selecteer **[!UICONTROL Storage Configuration]** waar u de gegevens wilt opslaan.
1. Klikken **[!UICONTROL Save&Close]**

>[!ENDTABS]

## Verwante artikelen

{{af-submit-action}}
