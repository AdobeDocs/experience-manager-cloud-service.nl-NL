---
title: Hoe te om de kern component gebaseerde Aangepaste Vorm als ontwerp te bewaren?
description: Leer hoe u op basiscomponenten gebaseerde adaptieve formulieren als concept opslaat en een Forms Portal maakt en kerncomponenten buiten de box op een AEM Sites-pagina gebruikt.
feature: Adaptive Forms, Core Components
source-git-commit: 494e90bd5822495f0619e8ebf55f373a26a3ffe6
workflow-type: tm+mt
source-wordcount: '1011'
ht-degree: 0%

---


<span class="preview"> Dit artikel bevat inhoud voor de functie voor pre-release. De pre-release functie is alleen toegankelijk via onze [pre-releasekanaal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features).

# Adaptief formulier op basis van kerncomponent opslaan als concept {#save-af-form}

Het opslaan van een adaptief formulier als concept is een essentiële functie die de efficiëntie en nauwkeurigheid van de gebruiker verbetert. Met deze functionaliteit kunnen gebruikers de voortgang opslaan en de taken later voltooien zonder dat ze ingevoerde informatie verliezen. Een  `save-as-draft` deze optie garandeert flexibiliteit bij het beheer van de tijd, vermindert het risico op gegevensverlies en handhaaft de nauwkeurigheid van de ingediende gegevens. U kunt formulieren opslaan als concepten en deze later voltooien.

## Overwegingen

* [Aangepaste Forms-kerncomponenten voor uw omgeving inschakelen.](/help/forms/enable-adaptive-forms-core-components.md)

* Zorg ervoor dat de [kerncomponent is ingesteld op versie 3.0.24 of hoger](https://github.com/adobe/aem-core-forms-components) om deze functie te gebruiken.
* Zorg ervoor dat u een [Azure-opslagaccount en een toegangstoets](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal) om toegang tot de Azure-opslagaccount te verlenen.

## Een adaptief formulier opslaan als concept

[!DNL Experience Manager Forms] Gegevensintegratie (data-integration.md) biedt [!DNL Azure] opslagconfiguratie om formulieren te integreren met [!DNL Azure] opslagservices. Met het formuliergegevensmodel (FDM) kunt u Adaptieve Forms maken die werkt met het [!DNL Azure] server om bedrijfswerkstromen toe te laten.

Als u het formulier wilt opslaan als concept, moet u zorgen dat u beschikt over een Azure-opslagaccount en een toegangstoets om toegang tot het bestand te verlenen [!DNL Azure] opslagaccount. Voer de volgende stappen uit om het formulier op te slaan als concept:

1. [Azure Storage Configuration maken](#create-azure-storage-configuration)
1. [Unified Storage-connector configureren voor Forms Portal](#configure-usc-forms-portal)
1. [Regel maken om een adaptief formulier op te slaan als concept](#rule-to-save-adaptive-form-as-draft)


### 1. Maak een Azure Storage Configuration {#create-azure-storage-configuration}

Eenmaal beschikt u over een Azure-opslagaccount en een toegangstoets om toegang tot de [!DNL Azure] opslagaccount, voer de volgende stappen uit om Azure Storage-configuratie te maken:

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure Storage]**.

   ![Azure Storage Card-selectie](/help/forms/assets/save-form-as-draft-azure-card.png)

1. Selecteer een configuratiemap om de configuratie te maken en selecteer **[!UICONTROL Create]**.

   ![Azure Storage Configuration Folder selecteren](/help/forms/assets/save-form-as-draft-select-config-folder.png)

1. Geef een titel voor de configuratie op in het dialoogvenster **[!UICONTROL Title]** veld.
1. Geef de naam van de [!DNL Azure] opslagaccount in de **[!UICONTROL Azure Storage Account]** en **[!UICONTROL Azure Access Key]** velden.

   ![Azure Storage Configuration](/help/forms/assets/save-form-as-draft-azure-storage.png)

1. Klikken **Opslaan**.

>[!NOTE]
>
> U kunt de **[!UICONTROL Azure Storage Account]** en **[!UICONTROL Azure Access Key]** van de [Microsoft Azure Portal](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).


### 2. Configureer Unified Storage Connector voor Forms Portal {#configure-usc-forms-portal}

Nadat u de Azure Storage Configuration hebt gemaakt, configureert u de Unified Storage Connector voor Forms Portal met de volgende stappen:

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Unified Storage Connector]**.

   ![Unified Connector Storage](/help/forms/assets/save-form-as-draft-unified-connector.png)

1. In de **[!UICONTROL Forms Portal]** sectie, selecteert u **[!UICONTROL Azure]** van de **[!UICONTROL Storage]** vervolgkeuzelijst.
1. Geef de [configuratiepad voor de Azure-opslagconfiguratie](#create-azure-storage-configuration) in de **[!UICONTROL Storage Configuration Path]** veld.

   ![Instelling voor Unified Connector Storage](/help/forms/assets/save-form-as-draft-unified-connector-storage.png)

1. Selecteren **[!UICONTROL Save]** en selecteer vervolgens **[!UICONTROL Publish]** de configuratie publiceren.

### 3. Maak regels om een adaptief formulier op te slaan als concept {#rule-to-save-adaptive-form-as-draft}

Als u een formulier wilt opslaan als concept, maakt u een **Formulier opslaan** regel op een formuliercomponent, zoals een knop. Wanneer op de knop wordt geklikt, wordt de regel geactiveerd en wordt het formulier opgeslagen als concept. Voer de volgende stappen uit om te maken **Formulier opslaan** regel op een knopcomponent:

1. Open in de instantie Auteur een adaptief formulier in de bewerkingsmodus.
1. Selecteer in het linkerdeelvenster de optie ![Pictogram Componenten](assets/components_icon.png) en sleep de **[!UICONTROL Button]** aan het formulier.
1. Selecteer de **[!UICONTROL Button]** en selecteert u vervolgens de ![Pictogram Configureren](assets/configure_icon.png).
1. Selecteer de **[!UICONTROL Edit Rules]** om de Regeleditor te openen.
1. Selecteren **[!UICONTROL Create]** om de regel te vormen en te creëren.
1. In de **[!UICONTROL When]** sectie, selecteert u **is aangeklikt** en in de **[!UICONTROL Then]** selecteert u de **Formulier opslaan** -optie.
1. Selecteren **[!UICONTROL Done]** om de regel op te slaan.

![Regel maken voor knop](/help/forms/assets/save-form-as-drfat-create-rule.png)

Wanneer u een voorbeeld van een adaptief formulier bekijkt, vult u het in en klikt u op de knop **Formulier opslaan** wordt het formulier opgeslagen als een concept dat u later kunt gebruiken.

## Concepten en verzendingen om concepten op de AEM Sites-pagina weer te geven

AEM Forms biedt de **Concepten en verzendingen** portalcomponent uit de doos om opgeslagen formulieren op AEM Sites-pagina&#39;s weer te geven. De **Concepten en verzendingen** toont formulieren die worden opgeslagen als concepten die later kunnen worden ingevuld, en ook verzonden formulieren. Deze component biedt een persoonlijke ervaring voor elke aangemelde gebruiker door concepten en verzendingen weer te geven die betrekking hebben op de Adaptive Forms die door de gebruiker is gemaakt.

U kunt de uit-van-de-doos componenten van het Portaal van Forms gebruiken om vormontwerpen op de pagina van AEM Sites weer te geven. Voer de volgende stappen uit om de **Concepten en verzendingen** portalcomponent:

1. [Concepten en verzenden Forms Portal-component inschakelen](#enable-component)
2. [Concepten en verzendingen toevoegen aan AEM Sites-pagina](#Add-drafts-submissions-component)
3. [Concepten en verzendingen configureren](#configure-drafts-submissions-component)

### 1. Concepten en verzendingen inschakelen Forms Portal-component{#enable-component}

Om het **[!UICONTROL Drafts & Submissions]** voert u de volgende stappen uit in het sjabloonbeleid:

1. Open de AEM Sites-pagina in een **Bewerken** -modus.
1. Ga naar de **[!UICONTROL Page Information]** > **[!UICONTROL Edit Template]**
   ![Sjabloonbeleid bewerken](/help/forms/assets/save-form-as-draft-edit-template.png)

1. Klik op de knop **[!UICONTROL Policy]** en selecteert u de **[!UICONTROL Drafts & Submissions]**  selectievakje onder **[Projectnaam AEM] - Forms- en communicatieportaal**.

   ![Beleidsselectie](/help/forms/assets/save-form-as-draft-enable-policy.png)

1. Klik op **[!UICONTROL Done]**.

Wanneer een portalcomponent is ingeschakeld, kunt u deze gebruiken in de auteurinstantie van uw AEM Sites-pagina.

### 2. Voeg concepten en verzendingen toe aan AEM Sites-pagina{#Add-drafts-submissions-component}

U kunt Forms Portal maken en aanpassen op websites die zijn gemaakt met AEM door de portalcomponenten toe te voegen en te configureren. Zorg ervoor dat de [De component Concepten en verzendingen is ingeschakeld](#enable-component) voordat u ze op de AEM Sites-pagina gebruikt.

Als u een component wilt toevoegen, sleept u de component vanuit de component **Concepten en verzendingen** deelvenster aan de lay-outcontainer op de pagina, of selecteer het pictogram Toevoegen in de lay-outcontainer en voeg de component toe uit de **[!UICONTROL Insert New Component]** in.

![Concept- en verzendcomponent toevoegen](/help/forms/assets/save-form-as-draft-add-dns.png)

### 3. Concepten en verzendingen configureren {#configure-drafts-submissions-component}

De **Concepten en verzendingen** worden formulieren weergegeven die zijn opgeslagen als concept en die later kunnen worden ingevuld. Om te vormen **Concepten en verzendingen** Voer de volgende stappen uit:
1. Selecteer de **Concepten en verzendingen** component.
1. Klik op de knop ![Pictogram Configureren](assets/configure_icon.png) en verschijnt het dialoogvenster.
1. In de **[!UICONTROL Drafts and Submissions]** geeft u het volgende op:
   * **Titel** Als u een component op een sitepagina wilt identificeren, wordt de titel standaard boven op de component weergegeven.
   * **Type**: Hiermee geeft u de formulierlijst aan als concept of als verzonden formulieren.
   * **Layout**: Hiermee kunt u de conceptformulieren of ingediende formulieren in kaart- of lijstindeling weergeven.

   ![Eigenschappen van de component Concept en Verzending](/help/forms/assets/save-form-as-draft-dns-properties.png)

1. Klikken **Gereed**.

Wanneer **[!UICONTROL Select Type]** is geselecteerd zoals **Concept Forms**, worden de als concepten opgeslagen formulieren weergegeven:
![Concepten, pictogram](assets/drafts-component.png)

Wanneer **[!UICONTROL Select Type]** is geselecteerd zoals **Verzonden Forms**, worden de ingediende formulieren weergegeven:

![Verzendpictogram](assets/submission-listing.png)

U kunt het formulier openen door op het desbetreffende formulier te klikken.

<!--

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

## Zie ook {#see-also}

{{see-also}}



<!--

>[!MORELIKETHIS]
>
>* [Configure data sources for AEM Forms](/help/forms/configure-data-sources.md)
>* [Configure Azure storage for AEM Forms](/help/forms/configure-azure-storage.md)
>* [Integrate Microsoft Dynamics 365 and Salesforce with Adaptive Forms](/help/forms/configure-msdynamics-salesforce.md)

-->