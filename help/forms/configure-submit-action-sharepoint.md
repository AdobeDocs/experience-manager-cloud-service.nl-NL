---
Title: How to send data to a SharePoint storage on submission of an Adaptive Form?
Description: Learn how to send data from your Adaptive Form to a SharePoint storage like a SharePoint list or Document library when you submit the form.
keywords: Hoe verbindt u SharePoint-lijst met een adaptief formulier?, Hoe verbindt u een SharePoint-documentbibliotheek met een adaptief formulier, Verzenden naar SharePoint, Een SharePoint-documentbibliotheekconfiguratie maken, Verzenden naar SharePoint gebruiken in een adaptief formulier, Een adaptief formulier verbinden met Microsoft&reg; SharePoint-lijst.
feature: Adaptive Forms, Core Components
exl-id: e925a750-5fb5-4950-afd3-78551eec985d
title: "Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?"
role: User, Developer
source-git-commit: 5e1d08e82cafc3a8a715653727f42ce0048f2b1f
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 0%

---

# Een adaptief formulier aansluiten op Microsoft® SharePoint

Met de verzendactie van **[!UICONTROL Submit to SharePoint]** kunt u uw Adaptief formulier naadloos verbinden met een Microsoft® SharePoint-opslag. Nadat u het formulier hebt verzonden, worden de formuliergegevens naar de SharePoint-opslagruimte van uw keuze verzonden.

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. U kunt meer over deze opties leren in het [ AanpassingsVorm voorlegt Artikel van de Actie ](/help/forms/configure-submit-actions-core-components.md).

## Voordelen

Enkele voordelen van het verzenden van gegevens van een adaptief formulier naar de SharePoint-opslag zijn:

* Het vergemakkelijkt de directe verzending van formuliergegevens naar SharePoint, waardoor een gecentraliseerde locatie voor het opslaan en beheren van informatie wordt geboden.
* Door de SharePoint toegangsbeheer en toestemmingseigenschappen toe te passen, zorgt het ervoor dat slechts de gemachtigde individuen de voorgelegde gegevens kunnen bekijken of wijzigen.

Met **[!UICONTROL Submit to SharePoint]** kunt u:

* [Een adaptief formulier aansluiten op de SharePoint-documentbibliotheek](#connect-af-sharepoint-doc-library)
* [Een adaptief formulier verbinden met de SharePoint-lijst](#connect-af-sharepoint-list)

## Een adaptief formulier aansluiten op de SharePoint-documentbibliotheek {#connect-af-sharepoint-doc-library}

U kunt als volgt de **[!UICONTROL Submit to SharePoint Document Library]** Handeling verzenden in een adaptieve vorm gebruiken:

1. [ creeer een Configuratie van de Bibliotheek van het Document van SharePoint ](#create-a-sharepoint-configuration-create-sharepoint-configuration): Het verbindt AEM Forms met uw Opslag van SharePoint Microsoft®.
2. [ gebruik Submit aan SharePoint verzendt actie in een AanpassingsVorm ](#use-sharepoint-configuartion-in-af): Het verbindt uw AanpassingsVorm met gevormde SharePoint Microsoft®.

### Een SharePoint-documentbibliotheekconfiguratie maken {#create-sharepoint-configuration}

AEM Forms verbinden met uw Microsoft® SharePoint Document Library-opslagruimte:

1. Ga naar uw **1} instantie van de Auteur van AEM Forms >**[!UICONTROL Tools]**>**[!UICONTROL Cloud Services]**>**[!UICONTROL Microsoft® SharePoint]**.**
1. Nadat u de **[!UICONTROL Microsoft® SharePoint]** hebt geselecteerd, wordt u omgeleid naar **[!UICONTROL SharePoint Browser]** .
1. Selecteer de Container van de a **Configuratie**. De configuratie wordt opgeslagen in de geselecteerde Container van de Configuratie.
1. Klik op **[!UICONTROL Create]** > **[!UICONTROL SharePoint Document Library]** in de vervolgkeuzelijst. De configuratietovenaar van SharePoint verschijnt.

   ![ configuratie van SharePoint ](/help/forms/assets/sharepoint_configuration.png)
1. Geef de waarden **[!UICONTROL Title]** , **[!UICONTROL Client ID]** , **[!UICONTROL Client Secret]** en **[!UICONTROL OAuth URL]** op. Voor informatie over hoe te om identiteitskaart van de Cliënt terug te winnen, Geheime cliënt, identiteitskaart van de Aannemer voor OAuth URL, zie [ Documentatie Microsoft® ](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
   * U kunt de `Client ID` en `Client Secret` van uw app ophalen via de Microsoft® Azure-portal.
   * Voeg in de Microsoft® Azure-portal de Redirect URI toe als `https://[author-instance]/libs/cq/sharepoint/content/configurations/wizard.html` . Vervang `[author-instance]` door de URL van de instantie Auteur.
   * Voeg de API-machtigingen `offline_access` en `Sites.Manage.All` toe om lees- en schrijfmachtigingen te bieden. `Sites.Manage.All` is een machtigingsbereik in de Microsoft Graph-API waarmee een toepassing alle aspecten van SharePoint-sites kan beheren, zoals het verwijderen of wijzigen van sites.

     >[!NOTE]
     >
     > U kunt de Plaatsen van SharePoint met beperkte toegang ](/help/forms/configure-sharepoint-site-limited-access.md) ook vormen door het `Sites.Selected` toestemmingswerkingsgebied in de Grafiek API van Microsoft te gebruiken. [ `Sites.Selected` is een machtigingsbereik in de Microsoft Graph API die gedetailleerdere en beperkte toegang tot SharePoint-sites toestaat.

   * Gebruik OAuth URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Vervang `<tenant-id>` door `tenant-id` van uw app via de Microsoft® Azure-portal.

   >[!NOTE]
   >
   > Het **cliënt geheime** gebied is verplicht of facultatief hangt van uw Azure Actieve de toepassingsconfiguratie van de Folder af. Als uw toepassing wordt gevormd om een cliëntgeheim te gebruiken, is het verplicht om het cliëntgeheim te verstrekken.

1. Klik op **[!UICONTROL Connect]**. Bij een geslaagde verbinding wordt het bericht `Connection Successful` weergegeven.

1. Nu, uitgezochte **>** de Bibliotheek van het Document van SharePoint **>** de Omslag van SharePoint **, om de gegevens te bewaren.**

   >[!NOTE]
   >
   >* Standaard is `forms-ootb-storage-adaptive-forms-submission` aanwezig op geselecteerde SharePoint-site.
   >* Creeer een omslag als `forms-ootb-storage-adaptive-forms-submission`, als niet reeds aanwezig in de `Documents` bibliotheek van de geselecteerde Plaats van SharePoint door **te klikken creeer Omslag**.

U kunt deze configuratie voor SharePoint-sites nu gebruiken voor de verzendactie in een adaptief formulier.

### SharePoint Document Library Configuration gebruiken in een adaptief formulier {#use-sharepoint-configuartion-in-af}

U kunt de gemaakte SharePoint Document Library-configuratie in een adaptief formulier gebruiken om gegevens of gegenereerd Document of Record in een SharePoint-map op te slaan. Voer de volgende stappen uit om een opslagconfiguratie voor SharePoint Document Library in een adaptief formulier te gebruiken als:

1. Creeer een [ Aangepaste Vorm ](/help/forms/creating-adaptive-form-core-components.md).

   >[!NOTE]
   >
   > * Selecteer hetzelfde [!UICONTROL Configuration Container] voor een adaptief formulier, waar u de opslagruimte van de SharePoint-documentbibliotheek hebt gemaakt.
   > * Als er geen [!UICONTROL Configuration Container] is geselecteerd, worden de algemene [!UICONTROL Storage Configuration] -mappen weergegeven in het eigenschappenvenster Handeling verzenden.

1. Selecteer **voorleggen Actie** als **[!UICONTROL Submit to SharePoint]**.
   ![ GIF SharePoint ](/help/forms/assets/sharedrive-video.gif)
1. Selecteer **[!UICONTROL Storage Configuration]** waar u de gegevens wilt opslaan.
1. Klik op **[!UICONTROL Save]** om de verzendinstellingen op te slaan.

Wanneer u het formulier verzendt, worden de gegevens opgeslagen in de opgegeven Microsoft® Sharepoint Document Library Storage.
De mapstructuur voor het opslaan van gegevens is `/folder_name/form_name/year/month/date/submission_id/data` .

## Een adaptief formulier verbinden met de Microsoft® SharePoint-lijst {#connect-af-sharepoint-list}

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

U kunt als volgt de [!UICONTROL Submit to SharePoint List] Handeling verzenden in een adaptieve vorm gebruiken:

1. [ creeer een Configuratie van de Lijst van SharePoint ](#create-sharepoint-list-configuration): Het verbindt AEM Forms met uw Opslag van de Lijst van SharePoint Microsoft®.
1. [ gebruik Submit gebruikend het Model van de Gegevens van de Vorm (FDM) in een Aangepaste Vorm ](#use-submit-using-fdm): Het verbindt uw AanpassingsVorm met gevormde Microsoft® SharePoint.

### Een SharePoint List-configuratie maken {#create-sharepoint-list-configuration}

AEM Forms verbinden met uw Microsoft® SharePoint-lijst:

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® SharePoint]** .
1. Selecteer de Container van de a **Configuratie**. De configuratie wordt opgeslagen in de geselecteerde Container van de Configuratie.
1. Klik op **[!UICONTROL Create]** > **[!UICONTROL SharePoint List]** in de vervolgkeuzelijst. De configuratietovenaar van SharePoint verschijnt.
1. Geef de waarden **[!UICONTROL Title]** , **[!UICONTROL Client ID]** , **[!UICONTROL Client Secret]** en **[!UICONTROL OAuth URL]** op. Voor informatie over hoe te om identiteitskaart van de Cliënt terug te winnen, Geheime cliënt, identiteitskaart van de Aannemer voor OAuth URL, zie [ Documentatie Microsoft® ](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
   * U kunt de `Client ID` en `Client Secret` van uw app ophalen via de Microsoft® Azure-portal.
   * Voeg in de Microsoft® Azure-portal de Redirect URI toe als `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html` . Vervang `[author-instance]` door de URL van de instantie Auteur.
   * Voeg de API toestemmingen `offline_access` en `Sites.Manage.All` in het **Microsoft® Grafiek** lusje toe om lees-schrijftoestemmingen te verstrekken. Voeg `AllSites.Manage` toestemming in het **SharePoint** lusje toe om ver met de gegevens van SharePoint in wisselwerking te staan.
   * Gebruik OAuth URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Vervang `<tenant-id>` door `tenant-id` van uw app via de Microsoft® Azure-portal.

     >[!NOTE]
     >
     > Het **cliënt geheime** gebied is verplicht of facultatief hangt van uw Azure Actieve de toepassingsconfiguratie van de Folder af. Als uw toepassing wordt gevormd om een cliëntgeheim te gebruiken, is het verplicht om het cliëntgeheim te verstrekken.

1. Klik op **[!UICONTROL Connect]**. Bij een geslaagde verbinding wordt het bericht `Connection Successful` weergegeven.
1. Selecteer **[!UICONTROL SharePoint Site]** en **[!UICONTROL SharePoint List]** in de vervolgkeuzelijst.
1. Selecteer **[!UICONTROL Create]** om de wolkenconfiguratie voor Microsoft® SharePointList tot stand te brengen.


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
