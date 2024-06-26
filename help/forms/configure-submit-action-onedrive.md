---
Title: How to submit data from an Adaptive Form to Microsoft® OneDrive?
Description: Explore the streamlined process of connecting AEM Forms with Microsoft® OneDrive using the Submit to OneDrive Submit Action. Learn the step-by-step guide to configure OneDrive and set up submission actions for efficient data storage and retrieval
keywords: AEM Forms OneDrive-integratie, verbinding maken met Microsoft OneDrive, OneDrive-configuratie instellen met AEM formulieren
feature: Adaptive Forms, Core Components
exl-id: dbfa4094-1b92-4a7c-a799-f66973d27054
title: "Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?"
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# Een adaptief formulier verzenden naar Microsoft® OneDrive

De **[!UICONTROL Submit to OneDrive]** Met Actie verzenden wordt een adaptief formulier verbonden met een Microsoft® OneDrive. U kunt de formuliergegevens, bestanden, bijlagen of het Document of Record verzenden naar de aangesloten Microsoft® OneDrive-opslag.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. Meer informatie over deze opties vindt u in het gedeelte [Handeling Adaptief verzenden van formulier](/help/forms/configure-submit-actions-core-components.md)  artikel.

## Voordelen

Een aantal voordelen van een naadloze integratie van AEM Forms en Microsoft® OneDrive zijn:

* De toegankelijkheid van OneDrive voor verschillende apparaten zorgt ervoor dat opgeslagen formuliergegevens gemakkelijk beschikbaar zijn op verschillende platforms. Gebruikers kunnen toegang krijgen tot de verzonden gegevens, bijlagen en documenten van desktops, laptops, tablets en mobiele apparaten, waardoor de toegankelijkheid en flexibiliteit worden verbeterd.
* OneDrive-integratie met AEM vormen biedt een betrouwbare en schaalbare oplossing voor efficiënte gegevensopslag. Alle verzendingen met een adaptief formulier, zoals bestanden, bijlagen en Document of Record, kunnen eenvoudig in OneDrive worden opgeslagen en zo georganiseerde en toegankelijke gegevens garanderen.

## OneDrive aansluiten op een adaptief formulier

>[!VIDEO](https://video.tv.adobe.com/v/3424864/connect-aem-adaptive-form-to-onedrive/?quality=12&learn=on)

Voer de volgende stappen uit als OneDrive wordt geconfigureerd voor AEM Forms-verzending:

1. [Een OneDrive-configuratie maken](#create-a-onedrive-configuration-create-onedrive-configuration): AEM Forms wordt aangesloten op uw Microsoft® OneDrive-opslag.
2. [De verzendactie Verzenden naar OneDrive gebruiken in een adaptief formulier](#use-onedrive-configuration-in-an-adaptive-form-use-onedrive-configuartion-in-af): Het maakt een verbinding tussen uw Adaptief formulier en de geconfigureerde Microsoft® OneDrive.

### Een OneDrive-configuratie maken {#create-onedrice-configuration}

AEM Forms aansluiten op uw Microsoft® OneDrive-opslag:

1. Ga naar uw **AEM Forms-auteur** instance > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Microsoft® OneDrive]**.
1. Wanneer u de **[!UICONTROL Microsoft® OneDrive]**, u wordt doorgestuurd naar **[!UICONTROL OneDrive Browser]**.
1. Selecteer een **Configuratie-container**. De configuratie wordt opgeslagen in de geselecteerde Container van de Configuratie.
1. Klik op **[!UICONTROL Create]**. De OneDrive-configuratietovenaar wordt weergegeven.

   ![OneDrive-configuratiescherm](/help/forms/assets/onedrive-configuration.png)

1. Geef de **[!UICONTROL Title]**, **[!UICONTROL Client ID]**, **[!UICONTROL Client Secret]** en **[!UICONTROL OAuth URL]**. Voor informatie over hoe te om identiteitskaart van de Cliënt terug te winnen, Geheim, identiteitskaart van de Aannemer voor OAuth URL, zie [Microsoft®-documentatie](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
   * U kunt de `Client ID` en `Client Secret` van uw app via de Microsoft® Azure-portal.
   * Voeg in de Microsoft® Azure-portal de Redirect URI toe als `https://[author-instance]/libs/cq/onedrive/content/configurations/wizard.html`. Vervangen `[author-instance]` met de URL van uw instantie Auteur.
   * API-machtigingen toevoegen `offline_access` en `Files.ReadWrite.All` om lees-/schrijfmachtigingen te bieden.
   * OAuth-URL gebruiken: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Vervangen `<tenant-id>` met de `tenant-id` van uw app via de Microsoft® Azure-portal.

   >[!NOTE]
   >
   > De **clientgeheim** het gebied is verplicht of facultatief hangt van uw Azure Actieve de toepassingsconfiguratie van de Folder af. Als uw toepassing wordt gevormd om een cliëntgeheim te gebruiken, is het verplicht om het cliëntgeheim te verstrekken.

1. Klik op **[!UICONTROL Connect]**. Bij een geslaagde verbinding wordt de `Connection Successful` wordt weergegeven.

1. Nu selecteert u **[!UICONTROL OneDrive Container]** > **[Map OneDrive]**  de gegevens opslaan.

   >[!NOTE]
   >
   >* Standaard, `forms-ootb-storage-adaptive-forms-submission` is aanwezig in OneDrive Container.
   > * Een map maken als `forms-ootb-storage-adaptive-forms-submission`, indien nog niet aanwezig, klikt u op **Map maken**.

U kunt deze OneDrive-opslagconfiguratie nu gebruiken voor de verzendactie in een adaptief formulier.

### OneDrive-configuratie gebruiken in een adaptief formulier {#use-onedrive-configuartion-in-af}

U kunt de gemaakte OneDrive-opslagconfiguratie in een adaptief formulier gebruiken om gegevens of gegenereerd document met record op te slaan in een OneDrive-map. Voer de volgende stappen uit om de OneDrive-opslagconfiguratie in een adaptief formulier te gebruiken als:
1. Een [Adaptief formulier](/help/forms/creating-adaptive-form.md).

   >[!NOTE]
   >
   > * Hetzelfde selecteren [!UICONTROL Configuration Container] voor een adaptief formulier, waar u uw OneDrive-opslag hebt gemaakt.
   > * Indien niet [!UICONTROL Configuration Container] is geselecteerd, dan is de globale [!UICONTROL Storage Configuration] worden weergegeven in het eigenschappenvenster Handeling verzenden.

1. Selecteren **Handeling verzenden** als **[!UICONTROL Submit to OneDrive]**.
   ![OneDrive-GIF](/help/forms/assets/onedrive-video.gif)
1. Selecteer de **[!UICONTROL Storage Configuration]**, waar u de gegevens wilt opslaan.
1. Klikken **[!UICONTROL Save]** om de verzendinstellingen op te slaan.

Wanneer u het formulier verzendt, worden de gegevens opgeslagen in de opgegeven Microsoft® OneDrive-opslag.
De mapstructuur voor het opslaan van gegevens is `/folder_name/form_name/year/month/date/submission_id/data`.

## Verwante artikelen

{{af-submit-action}}
