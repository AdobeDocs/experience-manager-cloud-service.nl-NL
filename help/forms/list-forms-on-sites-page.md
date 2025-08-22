---
title: Hoe kan ik formulieren op een Adobe Experience Manager Sites-pagina weergeven met Forms Portal-component?
description: Leer hoe u formulieren kunt weergeven op een AEM Sites-pagina.
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: 37e3ddd9-b20d-4156-b52e-64e36c455184
source-git-commit: 16b1e7ffa4e3812e9207bb283c63029939f7d14e
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# Formulieren weergeven op de pagina Sites

Stel je voor dat een gebruiker de website van de bank bezoekt op zoek naar een formulier voor het openen van een rekening. De bank gebruikt de Forms Portal-component om gebruikers te helpen snel het formulier te vinden door specifieke trefwoorden in te voeren of te filteren op categorieën zoals &#39;Nieuwe accounts&#39; of &#39;Persoonlijk bankieren&#39; en stelt gebruikers in staat het gewenste formulier gemakkelijk te vinden zonder door lange lijsten te hoeven bladeren.

De **Onderzoek &amp; van het Registreren** component van het Portaal van Forms staat u toe om vormen op een pagina van Plaatsen te tonen en te maken. Gebruikers kunnen een uitgebreide lijst met formulieren configureren en presenteren op basis van specifieke criteria om aan de organisatorische vereisten te voldoen. Anonieme gebruikers kunnen de pagina Sites bezoeken om de beschikbare formulieren weer te geven en te bladeren. De vermelde vormen kunnen in stijgende of dalende orde worden gesorteerd gebruikend de **Soort door** drop-down optie die in de hoger-juiste hoek van het scherm wordt gevestigd.

![ Onderzoek en het pictogram van de Registratie ](assets/search-and-lister-component.png)

## Voorwaarde

Voordat u de verschillende mogelijkheden van een Forms Portal-component gaat verkennen, moet u ervoor zorgen dat Core Components geschikt zijn voor uw omgeving. Installeer de nieuwste versie om Adaptive Forms Core Components in te schakelen voor uw AEM Cloud Service-omgeving.

<!--
## Enable Forms Portal components for your existing environment

To enable out-of-the-box Forms Portal components on existing AEM Forms as a Cloud Service, perform the following steps:

1. **Clone Cloud Manager Git repository on your local development instance:**  Your Cloud Manager Git repository contains a default AEM project. It is based on [AEM Archetype](https://github.com/adobe/aem-project-archetype/). Clone your Cloud Manager Git Repository using Self-Service Git Account Management from Cloud Manager UI to bring the project on your local development environment. For details on accessing the repository, see [Accessing Repositories](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/accessing-repos.html?lang=nl-NL).  

1. **Create [!DNL Experience Manager Forms] as a [Cloud Service] project:** Create [!DNL Experience Manager Forms] as a [Cloud Service] project based on [AEM Archetype 50](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-50) or later. The archetype help developers easily start developing for [!DNL AEM Forms] as a Cloud Service. It also includes some sample themes and templates to help you started quickly.

    To create [!DNL Experience Manager Forms] as a Cloud Service project, open the command prompt and run the below command. To include [!DNL Forms] specific configurations, themes, and templates, set `includeForms=y`.  

    ```shell
    mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=30 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
    ```

    Also, change `appTitle`, `appId`, and `groupId`, in the above command to reflect your environment.

    After the project is ready, update the `<core.forms.components.version>x.y.z</core.forms.components.version>` property in the top-level `pom.xml` of the Archetype project to reflect the latest version of [core-forms-components](https://github.com/adobe/aem-core-forms-components) in your `AEM Archetype` project. 
 
1. **Deploy the project to your local development environment:** You can use the following command to deploy to your local development environment

    `mvn -PautoInstallPackage clean install`

    For the complete list of commands, see [Building and Installing](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=nl-NL#building-and-installing)

1. [Deploy the archetype to your [!DNL AEM Forms] as a Cloud Service environment](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=nl-NL#embeddeds). -->

Nadat u de nieuwste Core Components in uw omgeving hebt geïmplementeerd, zijn de Forms Portal-componenten toegankelijk in uw ontwerpomgeving.

## Formulieren weergeven op de sitepagina

Om de **Onderzoek &amp; van het Registreren** poortcomponent aan uw pagina van Plaatsen toe te voegen, voer de volgende stappen uit:

1. Open de pagina van AEM Sites op een **geeft** wijze uit.
1. Ga naar **[!UICONTROL Page Information]** > **[!UICONTROL Edit Template]**
   ![ geef malplaatjebeleid ](/help/forms/assets/save-form-as-draft-edit-template.png) uit

1. Klik **[!UICONTROL Policy]** en selecteer **[!UICONTROL Search & Lister]** checkbox onder de **[Naam van het Project van het Archetype van AEM ] - Forms en Communicatie Portaal**.

   ![ de Selectie van het Beleid ](/help/forms/assets/search-lister-enable-policy.png)

1. Klik op **[!UICONTROL Done]**.
1. Open nu de AEM Sites-pagina opnieuw in de ontwerpmodus.
1. Zoek de sectie in de pagina-editor waarin u de Forms Portal-component kunt toevoegen.

1. Klik **toevoegen** pictogram. Het pictogram is een plusteken (+) waarmee u nieuwe componenten kunt toevoegen.

   Het klikken **voegt** pictogram toe toont een **Nieuwe de dialoogdoos van de Component van het Tussenvoegsel** die diverse componenten voor toevoeging toont.

   >[!NOTE]
   >
   > U kunt ook de component slepen en neerzetten.

1. Blader door de beschikbare componenten in het dialoogvenster en selecteer de gewenste component in de lijst. Bijvoorbeeld, selecteer het **Onderzoek en de component van het Registreren** van de lijst om het **Onderzoek &amp; van het Registreertoestel** Forms Portal component toe te voegen.

   ![ Onderzoek &amp; component van de Registratie ](/help/forms/assets/add-search-lister.png)

Nu, vorm de eigenschappen van het **Onderzoek en de component van het Registreren**.

## De eigenschappen van de component Search en Lister begrijpen

U kunt **Onderzoek en 1&rbrace; componenteneigenschappen gemakkelijk aanpassen Lister gebruikend de Configure Dialoog voor een naadloze gebruikerservaring.** Om te vormen, selecteer de component en selecteer dan ![ pictogram ](assets/configure_icon.png) vormen. Het dialoogvenster **[!UICONTROL Search and Lister]** wordt geopend.

### Tabblad Weergave

![ het Lusje van de Vertoning ](/help/forms/assets/search-and-lister-display-tab.png)

1. Geef in **[!UICONTROL Title]** de titel op voor de component Zoeken &amp; register. Een indicatieve titel biedt de gebruikers de mogelijkheid snel te zoeken in de formulierlijst.
1. Selecteer in de lijst **[!UICONTROL Layout]** de indeling die u wilt gebruiken voor de weergave van de formulieren in de kaart- of lijstindeling.
1. Selecteer **[!UICONTROL Hide Search]** en **[!UICONTROL Hide Sorting]** om de zoekopdracht te verbergen en op functies te sorteren.
1. Geef in **[!UICONTROL Tooltip]** de knopinfo op die wordt weergegeven wanneer u de muisaanwijzer op de component plaatst.

### Tabblad Element

![ het lusje van Activa ](/help/forms/assets/search-and-lister-asset-tab.png)

1. Geef op het tabblad **[!UICONTROL Asset Folder]** de locatie op vanwaar de formulieren worden opgehaald en weergegeven op de pagina.
1. Met de **[!UICONTROL Add another location]** kunt u meerdere maplocaties configureren.

### Resultaten, tabblad

![ het Lusje van de Vertoning ](/help/forms/assets/search-and-lister-result-tab.png)

Configureer op het tabblad **[!UICONTROL Results]** het maximum aantal formulieren dat per pagina wordt weergegeven. Standaard zijn dit acht formulieren per pagina.

## Formulieren op de pagina Sites weergeven met de component Zoeken en register

Om de lijst van vormen te bekijken, gebruik het **Onderzoek &amp; van het Registreren** de Portaalcomponent van Forms. Voorproef de pagina van AEM Sites om de lijst van vormen van de **omslag van Assets** te zien die op het scherm wordt getoond. U kunt ook naar een specifiek formulier zoeken met de zoekbalk.

![ Onderzoek en het pictogram van de Registratie ](assets/search-and-lister-component.png)

<!--
## Configure Azure Storage for Adaptive Forms {#configure-azure-storage-adaptive-forms}

[[!DNL Experience Manager Forms] Data Integration](data-integration.md) provides [!DNL Azure] storage configuration to integrate forms with [!DNL Azure] storage services. The Form Data Model (FDM) can be used to create Adaptive Forms that interact with [!DNL Azure] server to enable business workflows.

### Create Azure Storage Configuration {#create-azure-storage-configuration}

Before executing these steps, ensure that you have an Azure storage account and an access key to authorize access to the [!DNL Azure] storage account.

1. Navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Cloud Services]** &gt; **[!UICONTROL Azure Storage]**.
1. Select a folder to create the configuration and select **[!UICONTROL Create]**.
1. Specify a title for the configuration in the **[!UICONTROL Title]** field.
1. Specify the name of the [!DNL Azure] storage account in the **[!UICONTROL Azure Storage Account]** field.

### Configure Unified Storage Connector for Forms Portal {#configure-usc-forms-portal}

Perform the following steps to configure Unified Storage Connector for AEM Workflows:

1. Navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Forms]** &gt; **[!UICONTROL Unified Storage Connector]**.
1. In the **[!UICONTROL Forms Portal]** section, select **[!UICONTROL Azure]** from the **[!UICONTROL Storage]** drop-down list.
1. Specify the [configuration path for the Azure storage configuration](#create-azure-storage-configuration) in the **[!UICONTROL Storage Configuration Path]** field.
1. Select **[!UICONTROL Publish]** and then select **[!UICONTROL Save]** to save the configuration.

## Enable Forms Portal Components {#enable-forms-portal-components}

To use any core component (including the out-of-the-box portal components) in an Adobe Experience Manager (AEM) site, you must create a proxy component and enable it for your site. For creating a proxy component and enabling portal components, see [Using Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/using.html?lang=nl-NL#create-proxy-components). 

Once a portal component is enabled, you can use it in the author instance of your sites page.

## Add and Configure Forms Portal Components {#configure-forms-portal-components}

You can create and customize Forms Portal on websites authored using AEM by adding and configuring the portal components. Ensure that the [components are enabled](#enable-forms-portal-components) before using them in the Forms Portal.

To add a component, either drag and drop the component from the Components pane to the layout container on the page, or select the add icon on the layout container and add the component from the [!UICONTROL Insert New Component] dialog.

### Configure Drafts & Submissions Component {#configure-drafts-submissions-component}

The Drafts & Submissions component displays forms that are saved as draft for completing later and submitted forms. To configure, select the component and then select the ![Configure icon](assets/configure_icon.png). In the [!UICONTROL Drafts and Submissions] dialog, specify the title to indicate the form listing as draft or submitted forms. Also select whether the component should list draft forms or submitted forms in card or list format.

![Drafts icon](assets/drafts-component.png)

![Submissions icon](assets/submission-listing.png)

### Configure Search & Lister Component {#configure-search-lister-component}

The Search & Lister component is used to list adaptive forms on a page and to implement search on the listed forms. 

![Search and Lister icon](assets/search-and-lister-component.png)

To configure, select the component and then select the ![Configure icon](assets/configure_icon.png). The [!UICONTROL Search and Lister] dialog opens.

1. In the [!UICONTROL Display] tab, configure the following:
    * In **[!UICONTROL Title]**, specify the title for the Search & Lister component. An indicative title enables the users perform quick search across the list of forms.
    * From the **[!UICONTROL Layout]** list, select the layout to represent the forms in card or list format.
    * Select **[!UICONTROL Hide Search]** and **[!UICONTROL Hide Sorting]** to hide the search and sort by features.
    * In **[!UICONTROL Tooltip]**, provide the tooltip that appears when you hover over the component. 
1. In the [!UICONTROL Asset Folder] tab, specify the location from where the forms are pulled and listed on the page. You can configure multiple folder locations.
1. In the [!UICONTROL Results] tab, configure the maximum number of forms to display per page. The default is eight forms per page.

### Configure Link Component {#configure-link-component}

The link component enables you to provide links to an adaptive form on the page. To configure, select the component and then select the ![Configure icon](assets/configure_icon.png). The [!UICONTROL Edit Link Component] dialog opens.

1. In the [!UICONTROL Display] tab, provide the link caption and tooltip to ease identification of the forms represented by the link.
1. In the [!UICONTROL Asset Info] tab, specify the repository path where the asset is stored. 
1. In the [!UICONTROL Query Params] tab, specify the additional parameters in the key-value pair format. When the link is clicked, these additional parameters and passed along with the form.

## Configure Asynchronous Form Submission Using Adobe Sign {#configure-asynchronous-form-submission-using-adobe-sign}

You can configure to submit an adaptive form only when all the recipients have completed the signing ceremony. Follow the steps below to configure the setting using Adobe Sign.

1. In the author instance, open an Adaptive Form in the edit mode.
1. From the left pane, select the Properties icon and expand the **[!UICONTROL ELECTRONIC SIGNTATURE]** option.
1. Select **[!UICONTROL Enable Adobe Sign]**. Various configuration options display. 
1. In the [!UICONTROL Submit the form] section, select the **[!UICONTROL after every recipient completes signing ceremony]** option to configure the Submit Form action, where the form is first sent to all the recipients for signing. Once all the recipients have signed the form, only then the form is submitted. 

## Save Adaptive Forms As Drafts {#save-adaptive-forms-as-drafts}

You can save forms as Drafts for completing them later. There are two ways in which a form is saved as a draft:

* Create a "Save Form" rule on a form component, for example, a button. On clicking the button, the rule triggers and the form are saved a draft.
* Enable Auto-Save feature, which saves the form as per the specified event or after a configured interval of time.

### Create Rules to Save an Adaptive Form as Draft {#rule-to-save-adaptive-form-as-draft}

To create a "Save Form" rule on a form component, for example, a button, follow the steps below:

1. In the author instance, open an Adaptive Form in edit mode.
1. From the left pane, select ![Components icon](assets/components_icon.png) and drag the [!UICONTROL Button] component to the form.
1. Select the [!UICONTROL Button] component and then select the ![Configure icon](assets/configure_icon.png). 
1. Select the [!UICONTROL Edit Rules] icon to open the Rule Editor. 
1. Select **[!UICONTROL Create]** to configure and create the rule.
1. In the [!UICONTROL When] section, select "is clicked" and in the [!UICONTROL Then] section, select the "Save Form" options.
1. Select **[!UICONTROL Done]** to save the rule.

### Enable Auto-save {#enable-auto-save}

You can configure the auto-save feature for an adaptive form as follows:

1. In the author instance, open an Adaptive Form in edit mode.
1. From the left pane, select the ![Properties icon](assets/configure_icon.png) and expand the [!UICONTROL AUTO-SAVE] option.
1. Select the **[!UICONTROL Enable]** check box to enable auto-save of the form. You can configure the following:
* By default, the [!UICONTROL Adaptive Form Event] is set to "true", which implies that the form is auto-saved after every event.
* In [!UICONTROL Trigger], configure to trigger auto-save based on the occurrence of an event or after a specific interval of time.
-->


## Volgende stappen

In het volgende artikel, laat ons [ leren hoe te om vormen als concepten te bewaren en hen op een pagina van Plaatsen te vermelden gebruikend de Concepten &amp; de component van het Portaal van Forms van de Verzending ](/help/forms/save-core-component-based-form-as-draft.md).

## Verwante artikelen

{{forms-portal-see-also}}

## Zie ook {#see-also}

{{see-also}}
