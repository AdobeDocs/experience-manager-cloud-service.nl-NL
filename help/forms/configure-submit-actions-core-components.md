---
title: Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?
description: Een adaptief formulier biedt meerdere verzendhandelingen. Met een handeling Verzenden wordt gedefinieerd hoe een adaptief formulier wordt verwerkt na verzending. U kunt ingebouwde verzendhandelingen gebruiken of uw eigen handelingen maken
keywords: hoe u verzendactie voor een adaptief formulier selecteert, een adaptief formulier koppelt aan een SharePoint-lijst, een adaptief formulier aansluit op een SharePoint-documentbibliotheek, een adaptief formulier aansluit op een formuliergegevensmodel
exl-id: 495948e8-30a7-4e7c-952f-c71de15520f0
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '3449'
ht-degree: 0%

---

# Handeling Adaptief verzenden van formulier {#configuring-the-submit-action}

<span class="preview"> Adobe raadt u aan Core Components te gebruiken voor [Adaptieve Forms toevoegen aan een AEM Sites-pagina](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) of aan [standalone adaptieve Forms maken](/help/forms/creating-adaptive-form-core-components.md). </span>


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/configuring-submit-actions.html) |
| AEM as a Cloud Service | Dit artikel |
| Van toepassing op | ✅ adaptieve Form Core-componenten, ❎ [Aangepaste componenten van de Stichting van vormen](/help/forms/configuring-submit-actions.md) |


Met een handeling Verzenden kunt u de bestemming kiezen van gegevens die zijn vastgelegd via een adaptief formulier. Deze wordt geactiveerd wanneer een gebruiker op de knop **[!UICONTROL Submit]** op een adaptief formulier. Forms as a Cloud Service, voor Adaptive Forms op basis van Core Components, biedt een array van vooraf gebouwde verzendhandelingen. Met deze verzendacties kunt u:

* U kunt formuliergegevens eenvoudig verzenden via e-mail.
* Start Microsoft Power Automate-stromen of AEM Workflows tijdens het verzenden van de gegevens.
* Verzend de formuliergegevens rechtstreeks naar Microsoft SharePoint Server, Microsoft Azure Blob Storage of Microsoft OneDrive.
* Verzend naadloos de gegevens naar een gevormde gegevensbron gebruikend het Model van de Gegevens van de Vorm.
* Verzend de gegevens gemakkelijk naar een REST-eindpunt.

U kunt [De standaardverzendhandelingen uitbreiden](custom-submit-action-form.md) om zelf een handeling Verzenden te maken.

## Een handeling voor verzenden selecteren en configureren voor een adaptief formulier {#select-and-configure-submit-action}

Een handeling voor verzenden selecteren en configureren voor uw formulier:

1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.

1. Klik op de knop  **[!UICONTROL Submission]** tab.

   ![Klik op het pictogram Sleutel om het dialoogvenster Aangepaste formuliercontainer te openen om een verzendactie te configureren](/help/forms/assets/adaptive-forms-submit-message.png)

1. Selecteer en vorm een **[!UICONTROL Submit action]**, op basis van uw vereisten. Zie voor meer informatie over de geselecteerde handeling Verzenden:

   * [E-mail verzenden](#send-email)
   * [Verzenden naar SharePoint](#submit-to-sharedrive)
   * [Verzenden met gebruik van formuliergegevensmodel](#submit-using-form-data-model)
   * [Verzenden naar Azure Blob Storage](#azure-blob-storage)
   * [Verzenden naar REST-eindpunt](#submit-to-rest-endpoint)
   * [Verzenden naar OneDrive](#submit-to-onedrive)
   * [Een AEM-workflow aanroepen](#invoke-an-aem-workflow)
   * [Verzenden naar Power Automate](#microsoft-power-automate)

## E-mail verzenden {#send-email}

Als u een e-mail naar een of meer ontvangers wilt verzenden nadat het formulier is verzonden, kunt u de opdracht **[!UICONTROL Send Email]** Handeling verzenden. Met deze handeling kunt u een e-mail maken die formuliergegevens in een vooraf gedefinieerde indeling bevat. Neem bijvoorbeeld de volgende sjabloon waar de naam van de klant, het verzendadres, de naam van de staat en de postcode worden opgehaald uit de ingediende formuliergegevens:

    &quot;
    
    Hallo ${customer_Name},
    
    Het volgende is ingesteld als je standaard verzendadres:
    ${customer_Name},
    ${customer_Shipping_Address},
    ${customer_State},
    ${customer_ZIPCode}
    
    met betrekking tot
    WKND
    
    &quot;

>[!NOTE]
>
> * Het is van cruciaal belang dat alle formuliervelden unieke elementnamen hebben, zelfs als ze op verschillende deelvensters in een adaptief formulier zijn geplaatst.
> * Wanneer u AEM as a Cloud Service gebruikt, is codering vereist voor uitgaande e-mail. Standaard is de functie voor uitgaande e-mail uitgeschakeld. Als u het wilt activeren, verzendt u een ondersteuningsticket naar [Toegang aanvragen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#sending-email).

Bovendien **[!UICONTROL Send Email]** Met Actie verzenden kunt u bijlagen en een Document of Record (DoR) bij het e-mailbericht opnemen.

Om het [!UICONTROL Attach Document of Record] Raadpleeg de documentatie bij [Het adaptieve formulier configureren om een Document of Record (DoR) te genereren](generate-document-of-record-core-components.md). U kunt deze optie inschakelen in de eigenschappen van het adaptieve formulier.

<!-- [!NOTE]
>
>Send PDF via Email Submit Action is applicable only to Adaptive Forms that use XFA template as form model. 

>[!NOTE]
>
>Ensure that the [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder
>exists. The directory is required to temporarily store attachments. If the directory does not exist, create it. -->

<!--

>[!CAUTION]
>
>If you  [prefill](prepopulate-adaptive-form-fields.md) a form template,  a Form Data Model or schema based Adaptive Form with XML or JSON data complaint to a schema (XML schema, JSON schema , form template, or form data model) that is data does not contain &lt;afData&gt;, &lt;afBoundData&gt;, and &lt;/afUnboundData&gt; tags, then the data of unbounded fields (Unbounded fields are Adaptive Form fields without [bindref](prepopulate-adaptive-form-fields.md) property) of the Adaptive Form is lost. 

>[!CAUTION]
>
>If you [prefill](prepopulate-adaptive-form-fields.md) a form template, a Form Data Model or schema based Adaptive Form with XML or JSON data complaint to a schema (XML schema, JSON schema, or form data model) that does not contain &lt;afData&gt;, &lt;afBoundData&gt;, and &lt;/afUnboundData&gt; tags, then the data of unbounded fields (Unbounded fields are Adaptive Form fields without [bindref](prepopulate-adaptive-form-fields.md) property) of the Adaptive Form is lost.


-->

## Verzenden naar SharePoint {#submit-to-sharedrive}

De **[!UICONTROL Submit to SharePoint]** Met Actie verzenden wordt een adaptief formulier verbonden met een Microsoft® SharePoint-opslag. U kunt het bestand met formuliergegevens, bijlagen of het document met records verzenden naar de aangesloten Microsoft® SharePoint-opslag.

<!--
Using Submit to SharePoint, you can:
* [Connect an Adaptive Form to SharePoint Document Library](#connect-af-sharepoint-doc-library)
* [Connect an Adaptive Form to SharePoint List](#connect-af-sharepoint-list)
-->

### Een adaptief formulier aansluiten op de SharePoint-documentbibliotheek {#connect-af-sharepoint-doc-library}

Als u de opdracht **[!UICONTROL Submit to SharePoint Document Library]** Actie verzenden in een adaptieve vorm:

1. [Een SharePoint-documentbibliotheekconfiguratie maken](#create-a-sharepoint-configuration-create-sharepoint-configuration): AEM Forms wordt aangesloten op uw Microsoft® SharePoint-opslag.
2. [De verzendactie Verzenden naar SharePoint gebruiken in een adaptief formulier](#use-sharepoint-configuartion-in-af): Het maakt een verbinding tussen uw Adaptief formulier en de geconfigureerde Microsoft® SharePoint.

#### Een SharePoint-documentbibliotheekconfiguratie maken {#create-sharepoint-configuration}

AEM Forms verbinden met uw Microsoft® Sharepoint Document Library Storage:

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

#### SharePoint Document Library Configuration gebruiken in een adaptief formulier {#use-sharepoint-configuartion-in-af}

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

<!--

### Connect an Adaptive Form to Microsoft® SharePoint List {#connect-af-sharepoint-list}

<span class="preview"> This is a pre-release feature and accessible through our [pre-release channel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

To use the [!UICONTROL Submit to SharePoint List] Submit Action in an Adaptive Form:

1. [Create a SharePoint List Configuration](#create-sharepoint-list-configuration): It connects AEM Forms to your Microsoft® Sharepoint List Storage.
1. [Use the Submit using Form Data Model in an Adaptive Form](#use-submit-using-fdm): It connects your Adaptive Form to configured Microsoft® SharePoint.

#### Create a SharePoint List Configuration {#create-sharepoint-list-configuration}

To connect AEM Forms to your Microsoft&reg; Sharepoint List:

1. Go to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Microsoft® SharePoint]**.   
1. Select a **Configuration Container**. The configuration is stored in the selected Configuration Container. 
1. Click **[!UICONTROL Create]** > **[!UICONTROL SharePoint List]** from the drop-down list. The SharePoint configuration wizard appears.  
1. Specify the **[!UICONTROL Title]**, **[!UICONTROL Client ID]**, **[!UICONTROL Client Secret]** and **[!UICONTROL OAuth URL]**. For information on how to retrieve Client ID, Client Secret, Tenant ID for OAuth URL, see [Microsoft&reg; Documentation](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
    * You can retrieve the `Client ID` and `Client Secret` of your app from the Microsoft&reg; Azure portal.
    * In the Microsoft&reg; Azure portal, add the Redirect URI as `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html`. Replace `[author-instance]` with the URL of your Author instance.
    * Add the API permissions `offline_access` and `Sites.Manage.All` in the **Microsoft® Graph** tab to provide read/write permissions. Add `AllSites.Manage` permission in the **Sharepoint** tab to interact remotely with SharePoint data.
    * Use OAuth URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Replace `<tenant-id>` with the `tenant-id` of your app from the Microsoft&reg; Azure portal.

      >[!NOTE]
      >
      > The **client secret** field is mandatory or optional depends upon your Azure Active Directory application configuration. If your application is configured to use a client secret, it is mandatory to provide the client secret.

1. Click **[!UICONTROL Connect]**. On a successful connection, the `Connection Successful` message appears.
1. Select **[!UICONTROL SharePoint Site]** and **[!UICONTROL SharePoint List]** from the drop-down list.
1. Tap **[!UICONTROL Create]** to create the cloud configuration for the Microsoft® SharePointList.


#### Use the Submit using Form Data Model in an Adaptive Form {#use-submit-using-fdm}

You can use the created SharePoint List configuration in an Adaptive Form, to save data or generated Document of Record in a SharePoint List folder. Perform the following steps to use a SharePoint List storage configuration in an Adaptive Form as:

1. [Create a Form Data Model using Microsoft® SharePoint List configuration](/help/forms/create-form-data-models.md)
1. [Configure the Form Data Model to retrieve and send data](/help/forms/work-with-form-data-model.md#configure-services)
1. [Create an Adaptive Form](/help/forms/creating-adaptive-form-core-components.md)
1. [Configure Submit action using a Form Data Model](/help/forms/configuring-submit-actions.md#submit-using-form-data-model)

When you submit the form, the data is saved in the specified Microsoft&reg; Sharepoint List Storage. 

>[!NOTE]
>
> In Microsoft® SharePoint List, the following column types are not supported:
> * image column
> * metadata column
> * person column
> * external data column

-->

## Verzenden met gebruik van formuliergegevensmodel {#submit-using-form-data-model}

De **[!UICONTROL Submit using Form Data Model]** Met Actie verzenden worden verzonden Adaptieve formuliergegevens voor het opgegeven gegevensmodelobject in een formuliergegevensmodel naar de gegevensbron. Wanneer u de handeling Verzenden configureert, kunt u een gegevensmodelobject kiezen waarvan de verzonden gegevens u naar de gegevensbron wilt schrijven.

U kunt een adaptief formulier verbinden met een Microsoft SharePoint-lijst door de handeling Verzenden van het formuliergegevensmodel te gebruiken.

Daarnaast kunt u een formulierbijlage verzenden met behulp van een formuliergegevensmodel en een Document of Record (DoR) naar de gegevensbron. Zie voor informatie over het formuliergegevensmodel [[!DNL AEM Forms] Gegevensintegratie](data-integration.md).

## Verzenden naar REST-eindpunt {#submit-to-rest-endpoint}

Gebruik de **[!UICONTROL Submit to REST Endpoint]** actie om de verzonden gegevens op een rest-URL te plaatsen. De URL kan van een interne (de server waarop het formulier wordt gegenereerd) of van een externe server zijn.

Om gegevens aan een interne server te posten, verstrek weg van het middel. De gegevens worden gepost de weg van het middel. Bijvoorbeeld /content/restEndPoint. Voor dergelijke postverzoeken wordt de authenticatieinformatie van het verzendverzoek gebruikt.

Geef een URL op om gegevens naar een externe server te posten. De opmaak van de URL is `https://host:port/path_to_rest_end_point`. Zorg ervoor dat u de weg vormt om het verzoek van de POST anoniem te behandelen.

![Toewijzing voor veldwaarden die zijn doorgegeven als parameters voor de pagina Bedankt](assets/post-enabled-actionconfig.png)

In het bovenstaande voorbeeld heeft de gebruiker informatie ingevoerd in `textbox` wordt vastgelegd met parameter `param1`. Syntaxis om gegevens te posten die zijn vastgelegd met `param1` is:

`String data=request.getParameter("param1");`

Ook parameters die u gebruikt voor het posten van XML-gegevens en -bijlagen zijn `dataXml` en `attachments`.

U gebruikt deze twee parameters in uw script bijvoorbeeld om gegevens te parseren op een eindpunt in de rest. U gebruikt de volgende syntaxis om de gegevens op te slaan en te ontleden:

`String data=request.getParameter("dataXml");`
`String att=request.getParameter("attachments");`

In dit voorbeeld: `data` de XML-gegevens worden opgeslagen, en `att` slaat gehechtheidsgegevens op.

De **[!UICONTROL Submit to REST endpoint]** Met Handeling verzenden worden de gegevens die in het formulier zijn ingevuld, als onderdeel van de HTTP-aanvraag naar een geconfigureerde bevestigingspagina verzonden. U kunt de naam toevoegen van de velden die u wilt aanvragen. De indeling van het verzoek is:

`{fieldName}={request parameter name}`

Zoals in de onderstaande afbeelding wordt getoond: `param1` en `param2` worden doorgegeven als parameters met waarden die zijn gekopieerd uit de **textbox** en **numericbox** velden voor de volgende actie.

![Rest Endpoint-verzendhandeling configureren](assets/action-config.png)

U kunt **[!UICONTROL Enable POST request]** en geef een URL op om de aanvraag te posten. Als u gegevens wilt verzenden naar de AEM server waarop het formulier zich bevindt, gebruikt u een relatief pad dat overeenkomt met het hoofdpad van de AEM server. Bijvoorbeeld, `/content/forms/af/SampleForm.html`. Gebruik absoluut pad om gegevens naar een andere server te verzenden.

>[!NOTE]
>
>Als u de velden als parameters in een REST-URL wilt doorgeven, moeten alle velden verschillende elementnamen hebben, zelfs als de velden op verschillende deelvensters zijn geplaatst.

<!-- ## Send PDF via Email {#send-pdf-via-email}

The **Send PDF via Email** Submit Action sends an email with a PDF containing form data, to one or more recipients on successful submission of the form.

>[!NOTE]
>
>This Submit Action is available for XFA-based Adaptive Forms and XSD-based adaption forms that have the Document of Record template. -->

<!-- ## Invoke a forms workflow {#invoke-a-forms-workflow}

The **Submit to Forms workflow** submit option sends a data xml and file attachments (if any) to an existing Adobe LiveCycle or [!DNL AEM Forms] on JEE process.

For information about how to configure the Submit to forms workflow Submit Action, see [Submitting and processing your form data using forms workflows](submit-form-data-livecycle-process.md). -->



<!--
## Forms Portal Submit Action {#forms-portal-submit-action}

The **Forms Portal Submit Action** option makes form data available through an [!DNL AEM Forms] portal.

For more information about the Forms Portal and Submit Action, see [Drafts and submissions component](draft-submission-component.md). -->

## Een AEM-workflow aanroepen {#invoke-an-aem-workflow}

De **[!UICONTROL Invoke an AEM Workflow]** Een adaptief formulier wordt gekoppeld aan een [AEM](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem). Wanneer een formulier wordt verzonden, wordt de bijbehorende workflow automatisch gestart bij de instantie Auteur. U kunt het gegevensbestand, de gehechtheid, en Document van Verslag aan de ladingsplaats van het werkschema of aan een variabele opslaan. Als de workflow is gemarkeerd voor externe gegevensopslag en geconfigureerd voor externe gegevensopslag, is alleen de optie Variabele beschikbaar. U kunt uit de lijst van variabelen selecteren beschikbaar voor het werkschemamodel. Als de workflow later wordt gemarkeerd voor externe gegevensopslag en niet op het moment dat de workflow wordt gemaakt, moet u ervoor zorgen dat de vereiste variabele configuraties aanwezig zijn.

Met de handeling Verzenden wordt het volgende geplaatst op de laadlocatie van de werkstroom, of de variabele als de werkstroom is gemarkeerd voor externe gegevensopslag:

* **Gegevensbestand**: Het bevat gegevens die naar het adaptieve formulier worden verzonden. U kunt de **[!UICONTROL Data File Path]** om de naam van het bestand en het pad van het bestand ten opzichte van de laadbewerking op te geven. Bijvoorbeeld de `/addresschange/data.xml` pad maakt een map met de naam `addresschange` en plaatst deze ten opzichte van de lading. U kunt ook alleen `data.xml` om alleen verzonden gegevens te verzenden zonder een maphiërarchie te maken. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

* **Bijlagen**: U kunt de opdracht **[!UICONTROL Attachment Path]** om de mapnaam op te geven waarin de bijlagen worden opgeslagen die naar het adaptieve formulier zijn geüpload. De map wordt gemaakt ten opzichte van de lading. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

* **Document van record**: Het bevat het Document of Record dat is gegenereerd voor het adaptieve formulier. U kunt de **[!UICONTROL Document of Record Path]** Hiermee geeft u de naam op van het bestand Document of Record en het pad van het bestand ten opzichte van de laadbewerking. Bijvoorbeeld de `/addresschange/DoR.pdf` pad maakt een map met de naam `addresschange` ten opzichte van de lading en plaatst het `DoR.pdf` ten opzichte van de lading. U kunt ook alleen `DoR.pdf` alleen Document of Record opslaan zonder een mappenhiërarchie te maken. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

Voordat u de **[!UICONTROL Invoke an AEM Workflow]** Met Handeling verzenden wordt het volgende geconfigureerd voor de **[!UICONTROL AEM DS settings service]** configuratie:

* **[!UICONTROL Processing Server URL]**: De Verwerkingsserver is de server waarop de Forms- of AEM-workflow wordt geactiveerd. Dit kan gelijk zijn aan de URL van de AEM auteurinstantie of een andere server.

* **[!UICONTROL Processing Server User Name]**: Gebruikersnaam van workflowgebruiker

* **[!UICONTROL Processing Server Password]**: Wachtwoord van workflowgebruiker



## Verzenden naar OneDrive {#submit-to-onedrive}

De **[!UICONTROL Submit to OneDrive]** Met Actie verzenden wordt een adaptief formulier verbonden met een Microsoft® OneDrive. U kunt de formuliergegevens, het bestand, de bijlagen of het document met records verzenden naar de aangesloten Microsoft® OneDrive-opslag.

>[!VIDEO](https://video.tv.adobe.com/v/3424864/connect-aem-adaptive-form-to-onedrive/?quality=12&learn=on)

Als u de opdracht [!UICONTROL Submit to OneDrive] Actie verzenden in een adaptieve vorm:

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

## Verzenden naar Azure Blob Storage {#submit-to-azure-blob-storage}

De **[!UICONTROL Submit to Azure Blob Storage]**  Met Actie verzenden wordt een adaptief formulier verbonden met een Microsoft® Azure-portal. U kunt de formuliergegevens, het bestand, de bijlagen of het document met records verzenden naar de aangesloten Azure Storage-containers. De handeling Verzenden voor Azure Blob Storage gebruiken:

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

Om waarden van een configuratie te plaatsen, [OSGi-configuraties genereren met de AEM SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), en [stel de configuratie op](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) naar de instantie Cloud Service.




## Verzenden naar Power Automate {#microsoft-power-automate}

U kunt een adaptief formulier configureren om een Microsoft® Power Automate Cloud Flow uit te voeren bij verzending. Met het geconfigureerde adaptieve formulier worden vastgelegde gegevens, bijlagen en het document met records naar Power Automate Cloud Flow verzonden voor verwerking. Het helpt u om een aangepaste ervaring op het gebied van gegevensvastlegging op te bouwen en tegelijk de kracht van Microsoft® Power Automate te benutten om bedrijfslogics rond vastgelegde gegevens te bouwen en de workflows van klanten te automatiseren. Hier volgen enkele voorbeelden van wat u kunt doen na de integratie van een adaptief formulier met Microsoft® Power Automate:

* Adaptieve Forms-gegevens gebruiken in een Power Automate-bedrijfsprocessen
* Gebruik Power Automate om vastgelegde gegevens naar meer dan 500 gegevensbronnen of een openbaar beschikbare API te verzenden
* Complexe berekeningen uitvoeren op vastgelegde gegevens
* Adaptieve Forms-gegevens opslaan naar opslagsystemen volgens een vooraf bepaald schema

De Adaptive Forms-editor biedt de **Een Microsoft® Power Automate-flow aanroepen** verzenden actie om adaptieve formuliergegevens, bijlagen en Document of Record naar Power Automate Cloud Flow te verzenden. De handeling Verzenden gebruiken om vastgelegde gegevens naar Microsoft® Power Automate te verzenden, [Sluit uw as a Cloud Service Forms-exemplaar aan met Microsoft® Power Automate](forms-microsoft-power-automate-integration.md)

Na een succesvolle configuratie, gebruik [Een Microsoft® Power Automate-flow aanroepen](forms-microsoft-power-automate-integration.md#use-the-invoke-a-microsoft&reg;-power-automate-flow-submit-action-to-send-data-to-a-power-automate-flow-use-the-invoke-microsoft-power-automate-flow-submit-action) verzenden actie om gegevens naar een Power Automate Flow te verzenden.

## Synchrone of asynchrone verzending gebruiken {#use-synchronous-or-asynchronous-submission}

Een verzendactie kan synchrone of asynchrone verzending gebruiken.

**Synchrone verzending**: Webformulieren zijn traditioneel geconfigureerd voor synchroon verzenden. Wanneer gebruikers een formulier verzenden in een synchrone verzending, worden ze omgeleid naar een bevestigingspagina, een pagina om u te bedanken of een pagina om een fout op te lossen. U kunt de **[!UICONTROL Use asynchronous submission]** om de gebruikers om te leiden naar een webpagina of een bericht te tonen bij verzending.

![Verzendhandeling configureren](assets/thank-you-setting.png)

**Asynchrone verzending**: Moderne webervaringen zoals toepassingen van één pagina krijgen steeds meer populariteit, waarbij de webpagina statisch blijft terwijl interactie tussen client en server plaatsvindt op de achtergrond. U kunt deze ervaring nu aanbieden met Adaptive Forms via [asynchrone verzending configureren](asynchronous-submissions-adaptive-forms.md).

## Revalidatie op de server in adaptieve vorm {#server-side-revalidation-in-adaptive-form}

In elk onlinesysteem voor gegevensvastlegging plaatsen ontwikkelaars doorgaans bepaalde JavaScript-validaties op de client om een aantal bedrijfsregels af te dwingen. Maar in moderne browsers, moeten de eindgebruikers die bevestigingen omzeilen en manueel bijdragen gebruikend diverse technieken, zoals Browser van het Web DevTools Console indienen. Deze technieken gelden ook voor Adaptive Forms. Een formulierontwikkelaar kan verschillende validatielogboeken maken, maar technisch kunnen eindgebruikers die validatielogboeken omzeilen en ongeldige gegevens naar de server verzenden. Ongeldige gegevens zouden de bedrijfsregels overtreden die een auteur van formulieren heeft afgedwongen.

Met de functie voor validatie aan de serverzijde kunt u ook de validaties uitvoeren die een Adaptive Forms-auteur heeft verstrekt tijdens het ontwerpen van een adaptief formulier op de server. Hierdoor wordt voorkomen dat bij het verzenden van gegevens en bij het valideren van formulieren inbreuk wordt gemaakt op de bedrijfsregels.

### Wat moet u op de server valideren? {#what-to-validate-on-server-br}

Alle OOTB-veldvalidaties (out-of-box) van een adaptief formulier die opnieuw worden uitgevoerd op de server zijn:

* Vereist
* Clausule voor validatie
* Validatie-expressie

### Validatie op de server inschakelen {#enabling-server-side-validation-br}

Gebruik de **[!UICONTROL Revalidate on server]** onder Adaptieve formuliercontainer in de zijbalk om validatie aan de serverzijde voor het huidige formulier in of uit te schakelen.

![Validatie op de server inschakelen](assets/revalidate-on-server.png)

Validatie op de server inschakelen

Als de eindgebruiker deze validaties overslaat en de formulieren verzendt, wordt de validatie opnieuw uitgevoerd door de server. Als de validatie aan het einde van de server mislukt, wordt de verzendtransactie gestopt. De gebruiker krijgt het oorspronkelijke formulier opnieuw te zien. De vastgelegde gegevens en verzonden gegevens worden als een fout aan de gebruiker gepresenteerd.

>[!NOTE]
>
>Servervalidatie valideert het formuliermodel. U wordt aangeraden een aparte clientbibliotheek voor validaties te maken en deze niet te mengen met andere elementen, zoals HTML styling en DOM-bewerking in dezelfde clientbibliotheek.

### Aangepaste functies ondersteunen in validatie-expressies {#supporting-custom-functions-in-validation-expressions-br}

Als er soms **complexe validatieregels** Het exacte validatiescript bevindt zich in aangepaste functies en de auteur roept deze aangepaste functies aan vanuit de expressie voor veldvalidatie. Als u deze aangepaste functiebibliotheek bekend en beschikbaar wilt maken tijdens het uitvoeren van validaties aan de serverzijde, kan de auteur van het formulier de naam van AEM clientbibliotheek configureren onder de **[!UICONTROL Basic]** tabblad Adaptieve formuliercontainereigenschappen, zoals hieronder weergegeven.

![Aangepaste functies ondersteunen in validatie-expressies](assets/clientlib-cat.png)

Aangepaste functies ondersteunen in validatie-expressies

Auteurs kunnen de aangepaste JavaScript-bibliotheek configureren per adaptief formulier. Houd in de bibliotheek alleen de herbruikbare functies die afhankelijk zijn van bibliotheken van derden jquery en underscore.js.

## Foutafhandeling bij verzenden van handeling {#error-handling-on-submit-action}

Als deel van AEM veiligheid en het verharden richtlijnen, vorm de pagina&#39;s van de douanefout zoals 400.jsp, 404.jsp, en 500.jsp. Deze handlers worden aangeroepen wanneer bij het verzenden van een formulier 400, 404 of 500 fouten worden weergegeven. De handlers worden ook geroepen wanneer deze foutencodes op de Publish knoop worden teweeggebracht. U kunt ook JSP-pagina&#39;s maken voor andere HTTP-foutcodes.

Wanneer u een formuliergegevensmodel of een op schema gebaseerde adaptieve vorm met XML- of JSON-gegevensklacht vooraf instelt op een schema dat geen gegevens bevat `<afData>`, `<afBoundData>`, en `</afUnboundData>` -tags, gaan de gegevens van niet-begrensde velden van het adaptieve formulier verloren. Het schema kan een XML-schema, JSON-schema of een formuliergegevensmodel zijn. Niet-begrensde velden zijn adaptieve formuliervelden zonder de `bindref` eigenschap.

<!-- For more information, see [Customizing Pages shown by the Error Handler](/help/sites-developing/customizing-errorhandler-pages.md). -->


<!--
## See next

* [Create style or themes for your forms](using-themes-in-core-components.md)
* [Create an Adaptive Form (core components)](/help/forms/creating-adaptive-form-core-components.md)
* [Create a custom Submit Action for Adaptive Forms](/help/forms/custom-submit-action-form.md)

-->

## Zie ook {#see-also}

{{see-also}}

