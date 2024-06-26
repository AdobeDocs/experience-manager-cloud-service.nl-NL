---
title: Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?
description: Een adaptief formulier biedt meerdere verzendhandelingen. Met een handeling Verzenden wordt gedefinieerd hoe een adaptief formulier wordt verwerkt na verzending. U kunt ingebouwde verzendhandelingen gebruiken of uw eigen handelingen maken
keywords: hoe u verzendactie voor een adaptief formulier selecteert, een adaptief formulier koppelt aan een SharePoint-lijst, een adaptief formulier aansluit op een SharePoint-documentbibliotheek, een adaptief formulier aansluit op het formuliergegevensmodel (FDM)
feature: Adaptive Forms, Core Components
exl-id: 495948e8-30a7-4e7c-952f-c71de15520f0
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---


# Handeling Adaptief verzenden van formulier {#configuring-the-submit-action}

<span class="preview"> Adobe raadt u aan Core Components te gebruiken voor [Adaptieve Forms toevoegen aan een AEM Sites-pagina](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) of aan [standalone adaptieve Forms maken](/help/forms/creating-adaptive-form-core-components.md). </span>


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/configuring-submit-actions.html) |
| AEM as a Cloud Service | Dit artikel |

Met een handeling Verzenden kunt u de bestemming kiezen van gegevens die zijn vastgelegd via een adaptief formulier. Deze wordt geactiveerd wanneer een gebruiker op de knop **[!UICONTROL Submit]** op een adaptief formulier. Forms as a Cloud Service biedt voor Adaptive Forms op basis van Core Components een array van vooraf gebouwde verzendhandelingen. Met deze verzendacties kunt u:

* U kunt formuliergegevens eenvoudig verzenden via e-mail.
* Start Microsoft® Power Automate-stromen of AEM Workflows tijdens het verzenden van de gegevens.
* Verzend de formuliergegevens rechtstreeks naar Microsoft® SharePoint Server, Microsoft® Azure Blob Storage of Microsoft® OneDrive.
* Verzend naadloos de gegevens naar een gevormde gegevensbron gebruikend het Model van de Gegevens van de Vorm (FDM).
* Verzend de gegevens gemakkelijk naar een REST-eindpunt.

U kunt [De standaardverzendhandelingen uitbreiden](custom-submit-action-form.md). U kunt de Submit Acties voor organisatie-specifieke vereisten ook aanpassen.

Als u een handeling Verzenden voor een adaptief wilt definiëren, gebruikt u het dialoogvenster Configureren van een **Aangepaste formuliercontainer** component. Het dialoogvenster voor configureren van een **Aangepaste formuliercontainer** omvat:
* Tabblad Standaard
* Tabblad Gegevensmodel formulier
* Tabblad Verzending

U kunt de eigenschappen van de Container van de Vorm bepalen gebruikend de Configure Dialoog. Meer over Configure Dialog van een component van de Container van de Vorm leren, [klik hier.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/form-container.html)

## Een handeling voor verzenden selecteren en configureren voor een adaptief formulier {#select-and-configure-submit-action}

Een handeling voor verzenden selecteren en configureren voor uw formulier:

1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.

1. Klik op de knop  **[!UICONTROL Submission]** tab.

   ![Klik op het pictogram Sleutel om het dialoogvenster Aangepaste formuliercontainer te openen om een verzendactie te configureren](/help/forms/assets/adaptive-forms-submit-message.png)

1. Selecteer en vorm een **[!UICONTROL Submit action]**, op basis van uw vereisten.

U kunt ook verschillende handelingen configureren voor het verzenden van een adaptief formulier.
* **URL/pad omleiden** - Met deze optie kan de gebruiker een pagina configureren voor elk formulier, waarnaar de gebruikers van het formulier worden omgeleid na het verzenden van een adaptief formulier.
* **Bericht tonen** - Met deze optie kunnen gebruikers een bericht toevoegen dat wordt weergegeven wanneer het Adaptief formulier is verzonden. De vooraf gedefinieerde tekst wordt opgenomen in het dialoogvenster en kan door de gebruiker worden gewijzigd.

Zie voor meer informatie over de volgende verzendhandelingen:

* [E-mail verzenden](/help/forms/configure-submit-action-send-email.md)
* [Een automatische stroomvoorziening aanroepen](/help/forms/forms-microsoft-power-automate-integration.md)
* [Verzenden naar SharePoint](/help/forms/configure-submit-action-sharepoint.md)
* [Een Workfront Fusion aanroepen](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [Verzenden met gebruik van FDM (Form Data Model)](/help/forms/using-form-data-model.md)
* [Verzenden naar Azure Blob Storage](/help/forms/configure-submit-action-azure-blob-storage.md)
* [Verzenden naar REST-eindpunt](/help/forms/configure-submit-action-restpoint.md)
* [Verzenden naar OneDrive](/help/forms/configure-submit-action-onedrive.md)
* [Een AEM-workflow aanroepen](/help/forms/configure-submit-action-workflow.md)

U kunt ook een adaptief formulier verzenden naar andere opslagconfiguraties:

* [Aangepast formulier verbinden met Salesforce-toepassing](/help/forms/aem-forms-salesforce-integration.md)
* [Een adaptief formulier aansluiten op Microsoft® Dynamics OData](/help/forms/ms-dynamics-odata-configuration.md)

U kunt [de standaardverzendhandelingen aanpassen](custom-submit-action-form.md). Daarnaast kunt u de optie Handelingen verzenden aanpassen om deze aan te passen aan specifieke organisatorische vereisten.


<!--
## Send Email {#send-email}

To send an email to one or more recipients upon successful submission of the form, you can use the **[!UICONTROL Send Email]** Submit Action. 

Refer to [configure the send email submit action for an Adaptive Form](/help/forms/configure-submit-action-send-email.md) to learn how to set up an Adaptive Form to send an email upon successful submission.
[!NOTE]
>
>Send PDF via Email Submit Action is applicable only to Adaptive Forms that use XFA template as form model. 

>[!NOTE]
>
>Ensure that the [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder
>exists. The directory is required to temporarily store attachments. If the directory does not exist, create it.


>[!CAUTION]
>
>If you  [prefill](prepopulate-adaptive-form-fields.md) a form template,  a Form Data Model (FDM) or schema based Adaptive Form with XML or JSON data complaint to a schema (XML schema, JSON schema , form template, or form data model (FDM)) that is data does not contain &lt;afData&gt;, &lt;afBoundData&gt;, and &lt;/afUnboundData&gt; tags, then the data of unbounded fields (Unbounded fields are Adaptive Form fields without [bindref](prepopulate-adaptive-form-fields.md) property) of the Adaptive Form is lost. 

>[!CAUTION]
>
>If you [prefill](prepopulate-adaptive-form-fields.md) a form template, a Form Data Model (FDM) or schema based Adaptive Form with XML or JSON data complaint to a schema (XML schema, JSON schema, or form data model(FDM)) that does not contain &lt;afData&gt;, &lt;afBoundData&gt;, and &lt;/afUnboundData&gt; tags, then the data of unbounded fields (Unbounded fields are Adaptive Form fields without [bindref](prepopulate-adaptive-form-fields.md) property) of the Adaptive Form is lost.

## Submit to Microsoft® SharePoint {#submit-to-sharedrive}

The **[!UICONTROL Submit to SharePoint]** Submit Action connects an Adaptive Form with a Microsoft&reg; SharePoint Storage. You can submit the form data files, attachments, or Document of Record to the connected Microsoft&reg; Sharepoint Storage. 

Integration of AEM Adaptive Form with Microsoft® SharePoint enables the submission, retrieval, or storage of data, files, and other relevant information within the SharePoint storage. To learn how to configure submit to SharePoint submit action for an Adaptive Form, [click here.](/help/forms/configure-submit-action-sharepoint.md) 

## Submit using Form Data Model (FDM) {#submit-using-form-data-model}

The **[!UICONTROL Submit using Form Data Model (FDM)]** Submit Action writes submitted Adaptive Form data for the specified data model object in a Form Data Model (FDM) to its data source. When configuring the Submit Action, you can choose a data model object whose submitted data you want to write back to its data source.

When a user submits a form based on a form data model (FDM), you can [configure the form to write the submitted data to the data sources associated with the data model object.](/help/forms/using-form-data-model.md#write-submitted-adaptive-form-data-into-data-sources-write-af)

## Submit to REST endpoint {#submit-to-rest-endpoint}

The **[!UICONTROL Submit to REST Endpoint]** submit action sends the submitted data to a REST URL. This URL can be either an internal server (the server where the form is displayed) or an external server. The data of an Adaptive Form is submitted to a REST URL using the **[!UICONTROL Submit to REST endpoint]** Submit Action.

For a comprehensive guide on the detailed steps to post or submit data to a REST URL, refer to [configure submit to REST Endpoint submit action for Adaptive Forms.](/help/forms/configure-submit-action-restpoint.md)

## Invoke an AEM Workflow {#invoke-an-aem-workflow}

The **[!UICONTROL Invoke an AEM Workflow]** Submit Action integrates an Adaptive Form with an [AEM Workflow](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem). When a form is submitted, the selected workflow starts automatically. 

 [Integrate AEM Adaptive Form with AEM Workflow: Streamlining Business Processes](/help/forms/configure-submit-action-workflow.md) provides step-by-step instructions to seamlessly integrate AEM Workflow with Adaptive Forms, optimizing business processes and enhancing workflow automation.

## Submit to OneDrive {#submit-to-onedrive}

The **[!UICONTROL Submit to OneDrive]** Submit Action connects an Adaptive Form with a Microsoft&reg; OneDrive. You can submit the form data, files, attachments, or Document of Record to the connected Microsoft&reg; OneDrive Storage. 

AEM Forms Cloud Service with Microsoft® OneDrive helps in optimize data submission. Explore the steps of [integrating OneDrive with AEM Forms](/help/forms/configure-submit-action-onedrive.md) for streamlined and secure storage.

## Submit to Azure Blob Storage {#submit-to-azure-blob-storage}

The **[!UICONTROL Submit to Azure Blob Storage]** Submit Action connects an Adaptive Form with a Microsoft® Azure portal and allows you to submit various elements such as form data, files, attachments, or Document of Record to the associated Azure Storage containers.

AEM as a Cloud Service allows submitting data to Azure Storage from AEM Adaptive Forms. Learn how to [create and use Azure Blob Storage configuration in AEM Forms](/help/forms/configure-submit-action-azure-blob-storage.md) for efficient data storage. 

To set values of a configuration, [Generate OSGi Configurations using the AEM SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), and [deploy the configuration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) to your Cloud Service instance.

## Submit to Power Automate {#microsoft-power-automate}

You can configure an Adaptive Form to run a Microsoft&reg; Power Automate Cloud Flow on submission. The configured Adaptive Form sends captured data, attachments, and Document Of Record to Power Automate Cloud Flow for processing. It helps you build custom data capture experience while harnessing the power of Microsoft&reg; Power Automate to build business logics around captured data and automate customer workflows. 
Adaptive Forms editor provides the **Invoke a Microsoft&reg; Power Automate flow** submit action to send adaptive forms data, attachments, and Document Of Record to Power Automate Cloud Flow. To use the Submit action to send captured data to Microsoft&reg; Power Automate, [Connect your Forms as a Cloud Service instance with Microsoft&reg; Power Automate](forms-microsoft-power-automate-integration.md)  

After a successful configuration, use the [Invoke a Microsoft&reg; Power Automate flow](forms-microsoft-power-automate-integration.md#use-the-invoke-a-microsoft&reg;-power-automate-flow-submit-action-to-send-data-to-a-power-automate-flow-use-the-invoke-microsoft-power-automate-flow-submit-action) submit action to send data to a Power Automate Flow.  

## Submit to Workfront Fusion {#workfront-fusion}

You can configure an Adaptive Form to submit data to Workfront Fusion on submission. Workfront Fusion allows automation of processes so that user can concentrate on new tasks rather than repeating the same tasks again and again. It automates both simple and complex tasks, saving time and ensuring consistent process execution.

The Adaptive Forms editor provides the **Invoke a WorkFront Fusion Scenario** submit action to send Adaptive Forms data or attachments to a Workfront Fusion scenario. To use the submit action for sending captured data to a Workfront Fusion scenario, refer to [Submit an Adaptive Form to Adobe Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md).

## Send PDF via Email {#send-pdf-via-email}

The **Send PDF via Email** Submit Action sends an email with a PDF containing form data, to one or more recipients on successful submission of the form.

>[!NOTE]
>
>This Submit Action is available for XFA-based Adaptive Forms and XSD-based adaption forms that have the Document of Record template. 
## Invoke a forms workflow {#invoke-a-forms-workflow}

The **Submit to Forms workflow** submit option sends a data xml and file attachments (if any) to an existing Adobe LiveCycle or [!DNL AEM Forms] on JEE process.

For information about how to configure the Submit to forms workflow Submit Action, see [Submitting and processing your form data using forms workflows](submit-form-data-livecycle-process.md). 
## Forms Portal Submit Action {#forms-portal-submit-action}

The **Forms Portal Submit Action** option makes form data available through an [!DNL AEM Forms] portal.

For more information about the Forms Portal and Submit Action, see [Drafts and submissions component](draft-submission-component.md). 

## Use synchronous or asynchronous submission {#use-synchronous-or-asynchronous-submission}

A Submit Action can use synchronous or asynchronous submission.

**Synchronous submission**: Traditionally, web forms are configured to submit synchronously. In a synchronous submission, when users submit a form, they are redirected to an acknowledgment page, a thank you page, or if there is submission failure, an error page. You can select the **[!UICONTROL Use asynchronous submission]** option to redirect the users to a webpage or show a message on submission.  

![Configure Submit Action](assets/thank-you-setting.png)

**Asynchronous submission**: Modern web experiences like single page applications are gaining popularity where the web page remains static while client-server interaction happens in the background. You can now provide this experience with Adaptive Forms by [configuring asynchronous submission](asynchronous-submissions-adaptive-forms.md).

## Server-Side Revalidation in Adaptive Form {#server-side-revalidation-in-adaptive-form}

Typically, in any online data capture system, developers place someJavaScript validations on client side to enforce a few business rules. But in modern browsers, end users have way to bypass those validations and manually do submissions using various techniques, Such as Web Browser DevTools Console. Such techniques are also valid for Adaptive Forms. A forms developer can create various validation logics, but technically, end users can bypass those validation logics and submit invalid data to the server. Invalid data would break the business rules that a form author has enforced.

The server-side revalidation feature provides the ability to run the validations that an Adaptive Forms author has provided while designing an Adaptive Form on the server. It prevents any possible compromise of data submissions and business rules violations represented in terms of form validations.

### What to validate on Server? {#what-to-validate-on-server-br}

All out of the box (OOTB) field validations of an Adaptive Form that are rerun at the server are:

* Required
* Validation Picture Clause
* Validation Expression

### Enabling Server-side Validation {#enabling-server-side-validation-br}

Use the **[!UICONTROL Revalidate on server]** under Adaptive Form Container in the sidebar to enable or disable server-side validation for the current form.

![Enabling Server-Side Validation](assets/revalidate-on-server.png)

Enabling Server-Side Validation

If end-user bypass those validations and submit the forms, the server again performs the validation. If the validation fails at server end, then the submit transaction is stopped. The user is presented with the original form again. The captured data and submitted data are presented to the user as an error.

>[!NOTE]
>
>Server-side validation validates the form model. You are recommended to create a separate client library for validations and not mix it with other things like HTML styling and DOM manipulation in the same client library.
-->

## Foutafhandeling bij verzenden van handeling {#error-handling-on-submit-action}

Als deel van AEM veiligheid en het verharden richtlijnen, vorm de pagina&#39;s van de douanefout zoals 400.jsp, 404.jsp, en 500.jsp. Deze handlers worden aangeroepen wanneer bij het verzenden van een formulier 400, 404 of 500 fouten worden weergegeven. De handlers worden ook geroepen wanneer deze foutencodes op de knoop van Publish worden teweeggebracht. U kunt ook JSP-pagina&#39;s maken voor andere HTTP-foutcodes.

Wanneer u een model van vormgegevens (FDM), of schema gebaseerde Aangepaste Vorm met XML of JSON gegevensklacht aan een schema vooraf instelt dat geen gegevens bevat `<afData>`, `<afBoundData>`, en `</afUnboundData>` -tags, gaan de gegevens van niet-begrensde velden van het adaptieve formulier verloren. Het schema kan een XML-schema, JSON-schema of een formuliergegevensmodel (FDM) zijn. Niet-begrensde velden zijn adaptieve formuliervelden zonder de `bindref` eigenschap.

<!-- For more information, see [Customizing Pages shown by the Error Handler](/help/sites-developing/customizing-errorhandler-pages.md). -->


<!--
## See next

* [Create style or themes for your forms](using-themes-in-core-components.md)
* [Create an Adaptive Form (core components)](/help/forms/creating-adaptive-form-core-components.md)
* [Create a custom Submit Action for Adaptive Forms](/help/forms/custom-submit-action-form.md)

-->

## Zie ook {#see-also}

{{see-also}}

