---
Title: How to send data to a SharePoint List storage on submission of an Adaptive Form?
Description: Learn how to send data from your Adaptive Form to a SharePoint storage like a SharePoint list when you submit the form.
keywords: Hoe te om de lijst van SharePoint voor een toevoegend formulier te verbinden?, voorleggen aan SharePoint, creeer een Configuratie van de Lijst van SharePoint, gebruik de Verzenden aan SharePoint actie in een Aangepast Vorm, verbind een Aangepast Formulier met Microsoft&reg; de Lijst van SharePoint.
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
title: Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?
role: User, Developer
exl-id: 9ac3e7be-c6fa-4dbc-9aba-b81741ba6c55
source-git-commit: 64edcfe1bf94638ae5d9510a5a6ac660cf1bcd0a
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# Een adaptief formulier verbinden met de Microsoft® SharePoint-lijst {#connect-af-sharepoint-list}

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

U kunt als volgt de [!UICONTROL Submit to SharePoint List] Handeling verzenden in een adaptieve vorm gebruiken:

1. [ creeer een Configuratie van de Lijst van SharePoint ](#1-create-a-sharepoint-list-configuration): Het verbindt AEM Forms met uw Opslag van de Lijst van SharePoint Microsoft®.
1. [ gebruik Submit gebruikend het Model van de Gegevens van de Vorm (FDM) in een Aangepaste Vorm ](#2-use-the-submit-using-form-data-model-fdm-in-an-adaptive-form-use-submit-using-fdm): Het verbindt uw AanpassingsVorm met gevormde Microsoft® SharePoint.

## &#x200B;1. Een SharePoint List-configuratie maken

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


## &#x200B;2. Gebruik de optie Verzenden met gebruik van het formuliergegevensmodel (FDM) in een adaptief formulier {#use-submit-using-fdm}

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
