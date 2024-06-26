---
Title: How to send data to a SharePoint storage on submission of an Adaptive Form?
Description: Learn how to send data from your Adaptive Form to a SharePoint storage like a SharePoint list or Document library when you submit the form.
keywords: Hoe verbindt u SharePoint-lijst met een adaptief formulier?, Hoe verbindt u een SharePoint-documentbibliotheek met een adaptief formulier, Verzenden naar SharePoint, Een SharePoint-documentbibliotheek maken, Verzenden naar SharePoint gebruiken in een adaptief formulier, Een adaptief formulier verbinden met Microsoft&reg, SharePoint List.
feature: Adaptive Forms, Core Components
exl-id: e925a750-5fb5-4950-afd3-78551eec985d
title: "Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?"
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Een adaptief formulier aansluiten op Microsoft® SharePoint

De **[!UICONTROL Submit to SharePoint]** Met deze verzendactie kunt u uw Adaptief formulier naadloos verbinden met een Microsoft® SharePoint-opslagsysteem. Nadat u het formulier hebt verzonden, worden de formuliergegevens naar de SharePoint-opslagruimte van uw keuze verzonden.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. Meer informatie over deze opties vindt u in het gedeelte [Handeling Adaptief verzenden van formulier](/help/forms/configure-submit-actions-core-components.md)  artikel.

## Voordelen

Enkele voordelen van het verzenden van gegevens van een adaptief formulier naar de SharePoint-opslag zijn:

* Het vergemakkelijkt de directe verzending van formuliergegevens naar SharePoint, waardoor een gecentraliseerde locatie voor het opslaan en beheren van informatie wordt geboden.
* Door de SharePoint toegangsbeheer en toestemmingseigenschappen toe te passen, zorgt het ervoor dat slechts de gemachtigde individuen de voorgelegde gegevens kunnen bekijken of wijzigen.

Gebruiken **[!UICONTROL Submit to SharePoint]** kunt u:

* [Een adaptief formulier aansluiten op de SharePoint-documentbibliotheek](#connect-af-sharepoint-doc-library)
* [Een adaptief formulier verbinden met de SharePoint-lijst](#connect-af-sharepoint-list)

## Een adaptief formulier aansluiten op de SharePoint-documentbibliotheek {#connect-af-sharepoint-doc-library}

Als u de opdracht **[!UICONTROL Submit to SharePoint Document Library]** Actie verzenden in een adaptieve vorm:

1. [Een SharePoint-documentbibliotheekconfiguratie maken](#create-a-sharepoint-configuration-create-sharepoint-configuration): AEM Forms wordt aangesloten op uw Microsoft® SharePoint-opslag.
2. [De verzendactie Verzenden naar SharePoint gebruiken in een adaptief formulier](#use-sharepoint-configuartion-in-af): Het maakt een verbinding tussen uw Adaptief formulier en de geconfigureerde Microsoft® SharePoint.

### Een SharePoint-documentbibliotheekconfiguratie maken {#create-sharepoint-configuration}

AEM Forms verbinden met uw Microsoft® SharePoint Document Library-opslagruimte:

1. Ga naar uw **AEM Forms-auteur** instance > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Microsoft® SharePoint]**.
1. Wanneer u de **[!UICONTROL Microsoft® SharePoint]**, u wordt doorgestuurd naar **[!UICONTROL SharePoint Browser]**.
1. Selecteer een **Configuratie-container**. De configuratie wordt opgeslagen in de geselecteerde Container van de Configuratie.
1. Klikken **[!UICONTROL Create]** > **[!UICONTROL SharePoint Document Library]** in de vervolgkeuzelijst. De configuratietovenaar van SharePoint verschijnt.

   ![SharePoint-configuratie](/help/forms/assets/sharepoint_configuration.png)
1. Geef de **[!UICONTROL Title]**, **[!UICONTROL Client ID]**, **[!UICONTROL Client Secret]** en **[!UICONTROL OAuth URL]**. Voor informatie over hoe te om identiteitskaart van de Cliënt terug te winnen, Geheim, identiteitskaart van de Aannemer voor OAuth URL, zie [Microsoft®-documentatie](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
   * U kunt de `Client ID` en `Client Secret` van uw app via de Microsoft® Azure-portal.
   * Voeg in de Microsoft® Azure-portal de Redirect URI toe als `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html`. Vervangen `[author-instance]` met de URL van uw instantie Auteur.
   * API-machtigingen toevoegen `offline_access` en `Sites.Manage.All` om lees-/schrijfmachtigingen te bieden.
   * OAuth-URL gebruiken: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Vervangen `<tenant-id>` met de `tenant-id` van uw app via de Microsoft® Azure-portal.

   >[!NOTE]
   >
   > De **clientgeheim** het gebied is verplicht of facultatief hangt van uw Azure Actieve de toepassingsconfiguratie van de Folder af. Als uw toepassing wordt gevormd om een cliëntgeheim te gebruiken, is het verplicht om het cliëntgeheim te verstrekken.

1. Klik op **[!UICONTROL Connect]**. Bij een geslaagde verbinding wordt de `Connection Successful` wordt weergegeven.

1. Nu selecteert u **SharePoint-site** > **Documentbibliotheek** > **SharePoint-map** om de gegevens op te slaan.

   >[!NOTE]
   >
   >* Standaard, `forms-ootb-storage-adaptive-forms-submission` is aanwezig op geselecteerde SharePoint-site.
   >* Een map maken als `forms-ootb-storage-adaptive-forms-submission`, indien niet reeds aanwezig in de `Documents` bibliotheek van de geselecteerde SharePoint-site door op **Map maken**.

U kunt deze configuratie voor SharePoint-sites nu gebruiken voor de verzendactie in een adaptief formulier.

### SharePoint Document Library Configuration gebruiken in een adaptief formulier {#use-sharepoint-configuartion-in-af}

U kunt de gemaakte SharePoint Document Library-configuratie in een adaptief formulier gebruiken om gegevens of gegenereerd Document of Record in een SharePoint-map op te slaan. Voer de volgende stappen uit om een opslagconfiguratie voor SharePoint Document Library in een adaptief formulier te gebruiken als:

1. Een [Adaptief formulier](/help/forms/creating-adaptive-form-core-components.md).

   >[!NOTE]
   >
   > * Hetzelfde selecteren [!UICONTROL Configuration Container] voor een adaptief formulier, waar u de opslag van uw SharePoint-documentbibliotheek hebt gemaakt.
   > * Indien niet [!UICONTROL Configuration Container] is geselecteerd, dan is de globale [!UICONTROL Storage Configuration] worden weergegeven in het eigenschappenvenster Handeling verzenden.

1. Selecteren **Handeling verzenden** als **[!UICONTROL Submit to SharePoint]**.
   ![SharePoint-GIF](/help/forms/assets/sharedrive-video.gif)
1. Selecteer de **[!UICONTROL Storage Configuration]**, waar u de gegevens wilt opslaan.
1. Klikken **[!UICONTROL Save]** om de verzendinstellingen op te slaan.

Wanneer u het formulier verzendt, worden de gegevens opgeslagen in de opgegeven Microsoft® Sharepoint Document Library Storage.
De mapstructuur voor het opslaan van gegevens is `/folder_name/form_name/year/month/date/submission_id/data`.

## Een adaptief formulier verbinden met de Microsoft® SharePoint-lijst {#connect-af-sharepoint-list}

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

Als u de opdracht [!UICONTROL Submit to SharePoint List] Actie verzenden in een adaptieve vorm:

1. [Een SharePoint List-configuratie maken](#create-sharepoint-list-configuration): AEM Forms wordt aangesloten op uw Microsoft® Sharepoint List Storage.
1. [Verzenden met gebruik van FDM (Form Data Model) in een adaptief formulier](#use-submit-using-fdm): Het maakt een verbinding tussen uw Adaptief formulier en de geconfigureerde Microsoft® SharePoint.

### Een SharePoint List-configuratie maken {#create-sharepoint-list-configuration}

AEM Forms verbinden met uw Microsoft® SharePoint-lijst:

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Microsoft® SharePoint]**.
1. Selecteer een **Configuratie-container**. De configuratie wordt opgeslagen in de geselecteerde Container van de Configuratie.
1. Klikken **[!UICONTROL Create]** > **[!UICONTROL SharePoint List]** in de vervolgkeuzelijst. De configuratietovenaar van SharePoint verschijnt.
1. Geef de **[!UICONTROL Title]**, **[!UICONTROL Client ID]**, **[!UICONTROL Client Secret]** en **[!UICONTROL OAuth URL]**. Voor informatie over hoe te om identiteitskaart van de Cliënt terug te winnen, Geheim, identiteitskaart van de Aannemer voor OAuth URL, zie [Microsoft®-documentatie](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
   * U kunt de `Client ID` en `Client Secret` van uw app via de Microsoft® Azure-portal.
   * Voeg in de Microsoft® Azure-portal de Redirect URI toe als `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html`. Vervangen `[author-instance]` met de URL van uw instantie Auteur.
   * API-machtigingen toevoegen `offline_access` en `Sites.Manage.All` in de **Microsoft® Graph** om lees-/schrijfmachtigingen te bieden. Toevoegen `AllSites.Manage` toestemming in de **Sharepoint** -tabbladen gebruiken om op afstand te werken met SharePoint-gegevens.
   * OAuth-URL gebruiken: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Vervangen `<tenant-id>` met de `tenant-id` van uw app via de Microsoft® Azure-portal.

     >[!NOTE]
     >
     > De **clientgeheim** het gebied is verplicht of facultatief hangt van uw Azure Actieve de toepassingsconfiguratie van de Folder af. Als uw toepassing wordt gevormd om een cliëntgeheim te gebruiken, is het verplicht om het cliëntgeheim te verstrekken.

1. Klik op **[!UICONTROL Connect]**. Bij een geslaagde verbinding wordt de `Connection Successful` wordt weergegeven.
1. Selecteren **[!UICONTROL SharePoint Site]** en **[!UICONTROL SharePoint List]** in de vervolgkeuzelijst.
1. Selecteren **[!UICONTROL Create]** om de cloudconfiguratie voor de Microsoft® SharePointList te maken.


### Verzenden met gebruik van FDM (Form Data Model) in een adaptief formulier {#use-submit-using-fdm}

U kunt de gemaakte SharePoint List-configuratie in een adaptief formulier gebruiken om gegevens of het gegenereerde Document of Record in een SharePoint-lijst op te slaan. Voer de volgende stappen uit om een SharePoint-lijst in een adaptief formulier te gebruiken als:

1. [Een formuliergegevensmodel (FDM) maken met Microsoft](/help/forms/create-form-data-models.md)
1. [Vorm het Model van de Gegevens van de Vorm (FDM) om gegevens terug te winnen en te verzenden](/help/forms/work-with-form-data-model.md#configure-services)
1. [Een adaptief formulier maken](/help/forms/creating-adaptive-form-core-components.md)
1. [Verzendactie configureren met een FDM (Form Data Model)](/help/forms/using-form-data-model.md)

Wanneer u het formulier verzendt, worden de gegevens opgeslagen in de opgegeven Microsoft® Sharepoint List Storage.

>[!NOTE]
>
> In Microsoft® SharePoint List worden de volgende kolomtypen niet ondersteund:
> * afbeeldingskolom
> * metagegevenskolom
> * persoonlijke kolom
> * kolom externe gegevens

## Verwante artikelen

{{af-submit-action}}
