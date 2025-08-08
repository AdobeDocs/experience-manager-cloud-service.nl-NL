---
title: Hoe te om Aangepast Vorm aan een Bibliotheek van het Document van SharePoint te integreren?
Description: This article explains how to send data from your Adaptive Form to a SharePoint  Document library when you submit the form.
keywords: Een verbinding maken met een SharePoint-documentbibliotheek voor een adaptief formulier, Verzenden naar SharePoint, Een SharePoint-documentbibliotheekconfiguratie maken, De verzendactie Verzenden naar SharePoint gebruiken in een adaptief formulier, AEM Forms Data Model SharePoint Document Library, Forms Data Model SharePoint Document Library, Forms Data Model integreren in de SharePoint Document Library
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
role: User, Developer
exl-id: a00b4a93-2324-4c2a-824f-49146dc057b0
source-git-commit: 1be7bafc1d93a65a81eeb2f7e86cac33cde7aa35
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---

# Een adaptief formulier aansluiten op de Microsoft® SharePoint-documentbibliotheek {#connect-af-sharepoint-doc-library}

>[!VIDEO](https://video.tv.adobe.com/v/3444368/formautomation-productivitytools-adaptiveforms--sharepointintegration-documentlibrary/?quality=12&learn=on)

<span> Deze video is alleen van toepassing op Core Components. Voor de Componenten van de UE/Foundation, gelieve naar het artikel te verwijzen.</span>


U kunt als volgt de **[!UICONTROL Submit to SharePoint Document Library]** Handeling verzenden in een adaptieve vorm gebruiken:

1. [ creeer een Configuratie van de Bibliotheek van het Document van SharePoint ](#1-create-a-sharepoint-document-library-configuration): Het verbindt AEM Forms met uw Opslag van SharePoint Microsoft®.
2. [ gebruik Submit aan SharePoint verzendt actie in een AanpassingsVorm ](#2-use-sharepoint-document-library-configuration-in-an-adaptive-form): Het verbindt uw AanpassingsVorm met gevormde SharePoint Microsoft®.

## &#x200B;1. Een SharePoint-documentbibliotheekconfiguratie maken

AEM Forms verbinden met uw Microsoft® SharePoint Document Library-opslagruimte:

1. Ga naar uw **1&rbrace; instantie van de Auteur van AEM Forms >** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]**.**[!UICONTROL Microsoft® SharePoint]**
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
     > U kunt de Plaatsen van SharePoint met beperkte toegang [ ook vormen door het ](/help/forms/configure-sharepoint-site-limited-access.md) toestemmingswerkingsgebied in de Grafiek API van Microsoft te gebruiken. `Sites.Selected` `Sites.Selected` is een machtigingsbereik in de Microsoft Graph API die gedetailleerdere en beperkte toegang tot SharePoint-sites toestaat.

   * Gebruik OAuth URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Vervang `<tenant-id>` door `tenant-id` van uw app via de Microsoft® Azure-portal.

     >[!NOTE]
     >
     > Het **cliënt geheime** gebied is verplicht of facultatief hangt van uw Azure Actieve de toepassingsconfiguratie van de Folder af. Als uw toepassing wordt gevormd om een cliëntgeheim te gebruiken, is het verplicht om het cliëntgeheim te verstrekken.

1. Het machtigingsbereik van `offline_access Sites.Selected` in de Microsoft Graph API voor grafieken dat gedetailleerdere en beperkte toegang tot SharePoint-sites toestaat. Het machtigingsbereik `offline_access Sites.Manage.All` in de Microsoft Graph API dat volledige toegang tot SharePoint-sites toestaat.
1. Klik op **[!UICONTROL Connect]**. Bij een geslaagde verbinding wordt het bericht `Connection Successful` weergegeven.

1. Nu, uitgezochte **>** de Bibliotheek van het Document van SharePoint **>** de Omslag van SharePoint **, om de gegevens te bewaren.**

   >[!NOTE]
   >
   >* Standaard is `forms-ootb-storage-adaptive-forms-submission` aanwezig op geselecteerde SharePoint-site.
   >* Creeer een omslag als `forms-ootb-storage-adaptive-forms-submission`, als niet reeds aanwezig in de `Documents` bibliotheek van de geselecteerde Plaats van SharePoint door **te klikken creeer Omslag**.

U kunt deze configuratie voor SharePoint-sites nu gebruiken voor de verzendactie in een adaptief formulier.

### &#x200B;2. SharePoint Document Library Configuration gebruiken in een adaptief formulier

U kunt de gemaakte SharePoint Document Library-configuratie in een adaptief formulier gebruiken om gegevens of gegenereerd Document of Record in een SharePoint-map op te slaan.

>[!NOTE]
>
> * Selecteer hetzelfde [!UICONTROL Configuration Container] voor een adaptief formulier, waar u de opslagruimte van de SharePoint-documentbibliotheek hebt gemaakt.
> * Als er geen [!UICONTROL Configuration Container] is geselecteerd, worden de algemene [!UICONTROL Storage Configuration] -mappen weergegeven in het eigenschappenvenster Handeling verzenden.

>[!BEGINTABS]

>[!TAB  Component van de Stichting ]

Voer de volgende stappen uit om een opslagconfiguratie van de Bibliotheek van het Document van SharePoint in een AanpassingsVorm te gebruiken die op de Component van de Stichting wordt gebaseerd als:

1. Open het Adaptief formulier voor bewerking en ga naar de sectie **[!UICONTROL Submission]** van de eigenschappen van de container van adaptieve formulieren.
1. Van de **[!UICONTROL Submit Action]** drop-down lijst, uitgezochte **legt Actie** als **[!UICONTROL Submit to SharePoint]** voor.
   ![ SharePoint GIF ](/help/forms/assets/submit-to-sharepoint-fc.png){width=50%}
1. Selecteer **[!UICONTROL Storage Configuration]** waar u de gegevens wilt opslaan.
1. Klik op **[!UICONTROL Save]** om de verzendinstellingen op te slaan.

>[!NOTE]
>
> * Wanneer u het formulier verzendt, worden de gegevens opgeslagen in de opgegeven Microsoft® Sharepoint Document Library Storage. De mapstructuur voor het opslaan van gegevens is `/folder_name/form_name/year/month/date/submission_id/data` .
> * Bijlagen worden ook opgeslagen in de map `/folder_name/form_name/year/month/date/submission_id/data` . Nochtans, als u **sparen Bijlagen met Oorspronkelijke Naam** selecteert, worden de gehechtheid opgeslagen in de omslag gebruikend hun originele filenames.

>[!TAB  Component van de Kern ]

Voer de volgende stappen uit om een opslagconfiguratie van de Documentbibliotheek van SharePoint in een Aangepast Vorm te gebruiken dat op de Component van de Kern wordt gebaseerd als:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de tab **[!UICONTROL Submission]** .
1. Van de **[!UICONTROL Submit Action]** drop-down lijst, uitgezochte **legt Actie** als **[!UICONTROL Submit to SharePoint]** voor.
   ![ SharePoint GIF ](/help/forms/assets/sharedrive-video.gif)
1. Selecteer **[!UICONTROL Storage Configuration]** waar u de gegevens wilt opslaan.
1. Klik op **[!UICONTROL Save]** om de verzendinstellingen op te slaan.

>[!NOTE]
>
> * Wanneer u het formulier verzendt, worden de gegevens opgeslagen in de opgegeven Microsoft® Sharepoint Document Library Storage. De mapstructuur voor het opslaan van gegevens is `/folder_name/form_name/year/month/date/submission_id/data` .
> * Bijlagen worden ook opgeslagen in de map `/folder_name/form_name/year/month/date/submission_id/data` . Nochtans, als u **sparen Bijlagen met Oorspronkelijke Naam** selecteert, worden de gehechtheid opgeslagen in de omslag gebruikend hun originele filenames.

>[!TAB  Universele Redacteur ]

Voer de volgende stappen uit om een opslagconfiguratie van de Bibliotheek van het Document van SharePoint in een Aangepast Formulier te gebruiken dat in Universele Redacteur als wordt ontworpen:

1. Open het adaptieve formulier voor bewerking.
1. Klik **uitgeven de uitbreiding van de Eigenschappen van de Vorm** op de redacteur.
Het **de dialoogvakje van de Eigenschappen van de Vorm** verschijnt.

   >[!NOTE]
   >
   > * Als u niet **ziet geef de Eigenschappen van de Vorm** pictogram in uw Universele interface van de Redacteur uit, laat **toe geef de 3&rbrace; uitbreiding van de Eigenschappen van de Vorm &lbrace;in Extension Manager uit.**
   > * Verwijs naar het [ artikel van de Hoogtepunten van de Eigenschap van 0&rbrace; Extension Manager om te leren hoe te om uitbreidingen in of onbruikbaar te maken in de Universele Redacteur.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

1. Klik **Verzending** lusje en selecteer **[!UICONTROL Submit to SharePoint]** voorlegt actie.
   ![ SharePoint GIF ](/help/forms/assets/submit-to-sharepoint-ue.png)
1. Selecteer **[!UICONTROL Storage Configuration]** waar u de gegevens wilt opslaan.
1. Klik op **[!UICONTROL Save&Close]** om de verzendinstellingen op te slaan.

>[!NOTE]
>
> * Wanneer u het formulier verzendt, worden de gegevens opgeslagen in de opgegeven Microsoft® Sharepoint Document Library Storage. De mapstructuur voor het opslaan van gegevens is `/folder_name/form_name/year/month/date/submission_id/data` .
> * Bijlagen worden ook opgeslagen in de map `/folder_name/form_name/year/month/date/submission_id/data` . Nochtans, als u **sparen Bijlagen met Oorspronkelijke Naam** selecteert, worden de gehechtheid opgeslagen in de omslag gebruikend hun originele filenames.

>[!ENDTABS]

## Verwante artikelen

{{af-submit-action}}
