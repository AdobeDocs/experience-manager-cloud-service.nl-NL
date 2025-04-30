---
title: Zelfstandige formulieren maken op basis van Core Component- of Edge Delivery Services-sjablonen en deze publiceren op Edge Delivery Services
description: In dit artikel wordt uitgelegd hoe u Adaptive Forms kunt maken door in de wizard Formulier maken een op Core-componenten of Edge Delivery Services gebaseerde sjabloon te selecteren. U kunt de formulieren ook publiceren naar AEM Edge Delivery Services.
feature: Edge Delivery Services
role: User
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: c68e98cfe442d0b5a928fde596e193073d5cac21
workflow-type: tm+mt
source-wordcount: '1586'
ht-degree: 0%

---


# Van authoring tot publicatie: AEM Forms op Edge Delivery Services

<span class="preview"> Deze functie is beschikbaar via het programma voor vroege toegang. Om toegang te verzoeken, verzend een e-mail met uw GitHub organisatienaam en bewaarplaatsnaam van uw officieel adres aan <a href="mailto:aem-forms-ea@adobe.com"> aem-forms-ea@adobe.com </a>. Bijvoorbeeld, als de bewaarplaats URL https://github.com/adobe/abc is, is de organisatienaam adobe en de bewaarplaatsnaam abc.</span>

Met Adobe Experience Manager (AEM) kunt u aantrekkelijke, responsieve en dynamische formulieren maken. Het biedt veelvoudige auteursmethodes aan, elk geschikt aan verschillende vereisten en niveaus van gebruikersdeskundigheid. &#x200B;

Dit artikel richt zich op de aanpak waarbij formulieren worden geschreven in de AEM-omgeving en gepubliceerd via Edge Delivery Services. Forms die is gebouwd met Core Component-sjablonen kan zowel op AEM als op Edge Delivery Services worden gepubliceerd en biedt flexibiliteit bij de implementatie. Formulieren die zijn gemaakt met op Edge Delivery Services gebaseerde sjablonen kunnen daarentegen alleen worden gepubliceerd op Edge Delivery Services. &#x200B;

![ Auteur en publiceer Aangepaste Vorm ](/help/edge/docs/forms/universal-editor/assets/author-publish-af.png){width=50% align=center}

## Voordelen van het ontwerpen van formulieren in AEM en het publiceren met Edge Delivery Services:

* **Behoud van bestaande werkschema&#39;s van AEM**: De organisaties kunnen hun gevestigde werkschema&#39;s en governancestructuren van AEM blijven gebruiken, die consistentie en controle over inhoudsverwezenlijking verzekeren. &#x200B;

* **Verbeterde prestaties**: Het publiceren door Edge Delivery Services resulteert in snellere teruggevende tijden, die de gebruikerservaring verbeteren en de tijden van de paginalading verminderen. &#x200B;

* **Verbeterde SEO**: Edge Delivery Services wordt ontworpen om inhoud met de hoge scores van de Lighthouse van Google te leveren, die tot betere optimalisering van de onderzoeksmotor en verhoogde zichtbaarheid kunnen leiden. &#x200B;

* **Flexibele plaatsingsopties**: Forms die met de Componenten van de Kern wordt gebouwd kan op zowel AEM als Edge Delivery Services worden gepubliceerd, die flexibiliteit in plaatsingsstrategieën aanbieden. &#x200B;

## Voordat u begint

Voordat u begint met het ontwerpen van formulieren in AEM en deze publiceert via Edge Delivery Services, moet u controleren of aan de volgende voorwaarden is voldaan:

* Zorg ervoor dat u een gegevensopslagruimte van Github hebt geconfigureerd voor Edge Delivery Services.
   * Als u geen bewaarplaats hebt, [ het nieuwe project van AEM preconfigured met het Adaptieve Blok van Forms ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block).
   * Als u een opslagplaats hebt, voegt u het Adaptive Forms Block toe aan uw bestaande opslagplaats. De gedetailleerde instructies zijn beschikbaar in [ Begonnen het worden met Edge Delivery Services voor AEM Forms ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project).
* Vestig een verbinding tussen uw milieu van AEM en bewaarplaats GitHub. [ hoe te om het te doen?](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template)

Een schema van de beslissingsstroom om de opstelling en de publicatie van Adaptive Forms te begeleiden:

![ Github het Werkschema van de Bewaarplaats ](/help/forms/assets/repo-workflow.png){width=auto}

## Formulieren ontwerpen in AEM en publiceren naar Edge Delivery Services

Voer de volgende stappen uit om formulieren te ontwerpen in AEM en deze te publiceren op Edge Delivery Services:

[1. Kies een sjabloon en maak het formulier](#choose-a-template-and-create-the-form)

[2. Auteur van het formulier](#author-the-form)

[3. Een formulier publiceren](#publish-a-form)

### Een sjabloon kiezen en het formulier maken

U kunt op een AEM-exemplaar formulieren maken voor publicatie naar Edge Delivery Services met:

>[!BEGINTABS]

>[!TAB  op Edge Delivery Services-Gebaseerde malplaatje ]

Voer de volgende stappen uit om de sjabloon te kiezen en het formulier te maken:

1. Meld u aan bij de AEM Forms as a Cloud Service-auteur.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Adaptive Forms]** . De wizard wordt geopend.
1. In het **Source** lusje, selecteer een **op Edge Delivery Services-Gebaseerde malplaatje**:

   ![ creeer EDS Forms ](/help/edge/assets/create-eds-forms.png)

   Wanneer u een **op Edge Delivery Services-Gebaseerde malplaatje** selecteert, wordt de **[!UICONTROL Create]** knoop toegelaten.
1. (Optioneel) Op de tabbladen **[!UICONTROL Data Source]** of **[!UICONTROL Submission]** kunt u een gegevensbron selecteren of een handeling verzenden.
1. (Optioneel) Op het tabblad **[!UICONTROL Delivery]** kunt u een datum voor het publiceren of verwijderen van een formulier opgeven.
1. Klik **[!UICONTROL Create]** en de **Create 2} tovenaar van de Vorm {verschijnt:**

   1. Specificeer de **Naam** en **Titel**.
   1. Specificeer **GitHub URL**. Als uw GitHub-opslagplaats bijvoorbeeld de naam `edsforms` heeft, bevindt deze zich onder de account `wkndforms` , is de URL:
      `https://github.com/wkndforms/edsforms`

   ![ creeer de tovenaar van de Vorm ](/help/edge/assets/create-form-wizard.png)

   Wanneer u op **[!UICONTROL Create]** klikt, wordt het formulier in de Universal Editor geopend voor ontwerpen.

   ![ auteur de vorm ](/help/edge/assets/author-form.png)
1. Klik op **[!UICONTROL Create]** om het formulier te maken. Nu, kunt u [ auteur de vorm gebruikend de Universele Redacteur ](#author-the-form).

>[!TAB  Component-based malplaatje van de Kern ]

Voer de volgende stappen uit om de sjabloon te kiezen en het formulier te maken:

1. Meld u aan bij de AEM Forms as a Cloud Service-auteur.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Adaptive Forms]** . De wizard wordt geopend.
1. In het **Source** lusje, selecteer a **Gebaseerde malplaatje van de Component van de Kern** en a **thema**, wordt de **[!UICONTROL Create]** knoop toegelaten.:

![ Gebaseerde malplaatje van de Component van de Kern ](/help/forms/assets/core-component-based-template.png)

1. (Optioneel) Op de tabbladen **[!UICONTROL Data Source]** of **[!UICONTROL Submission]** kunt u een gegevensbron selecteren of een handeling verzenden.
1. (Optioneel) Op het tabblad **[!UICONTROL Delivery]** kunt u een datum voor het publiceren of verwijderen van een formulier opgeven.
1. Klik **[!UICONTROL Create]** en de **Create 2} tovenaar van de Vorm {verschijnt voor:**
   1. Specificeer de **Naam** en **Titel**.
   2. Specificeer de plaats in het **gebied van de Weg** waar de Aangepaste Vorm moet worden bewaard.

   ![ creeer de Tovenaar van de Vorm ](/help/forms/assets/create-cc-form.png)

   Wanneer u op **[!UICONTROL Create]** klikt, wordt het formulier geopend in de Adaptieve formuliereditor voor ontwerpen.

   ![ de Aanpassings Redacteur van de Vorm ](/help/forms/assets/af-editor-form.png)

1. Klik op **[!UICONTROL Create]** om het formulier te maken. Nu, kunt u [ auteur de vorm gebruikend de Aanpassings Redacteur van de Vorm ](#author-the-form).

>[!ENDTABS]

### Auteur van het formulier

De vormen die gebruikend het op Edge Delivery Services-Gebaseerde malplaatje worden gecreeerd open in de [ Universele Redacteur ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) voor creatie. De formulieren die zijn gemaakt met de sjabloon op basis van een kerncomponent, worden echter geopend in de Adaptieve formuliereditor voor ontwerpen.

Voer de volgende stappen uit om formulieren te ontwerpen met de sjabloon Universal Editor voor Edge Delivery Services of met de sjabloon Adaptive Form Editor voor Core Component:

>[!BEGINTABS]

>[!TAB  op Edge Delivery Services-Gebaseerde malplaatje ]


1. Open Inhoudsbrowser, en navigeer aan de **[!UICONTROL Adaptive Form]** component in de **boom van de Inhoud**.

   ![ inhoudsboom ](/help/edge/assets/content-tree.png)

1. Klik het **[!UICONTROL Add]** pictogram en voeg de gewenste componenten van de **Adaptieve lijst van Componenten van de Vorm** toe.
   ![ voeg component ](/help/edge/assets/add-component.png) toe

   In de onderstaande schermafbeelding wordt de `Registration Form` weergegeven die in de Universal Editor is geschreven:

   ![ contacteer ons vorm ](/help/edge/assets/contact-us.png)

>[!NOTE]
>
> Voor gedetailleerde instructies bij het ontwerpen van een AanpassingsVorm die de Universele Redacteur gebruiken, [ klik hier ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg).

Nu kunt u [ vormen en aanpassen voorlegt acties voor vormen ](/help/edge/docs/forms/universal-editor/submit-action.md).

>[!TAB  Component-based malplaatje van de Kern ]

1. Klik **[!UICONTROL Insert component]** in de **componenten van de Belemmering hier** sectie.

   ![ de componenten van de belemmering hier ](/help/forms/assets/drag-components-af-editor.png)

1. Voeg de gewenste componenten van de **Adaptieve lijst van Componenten van de Vorm** toe.

   ![ voegt componenten ](/help/forms/assets/add-component-af.png) toe

In de onderstaande schermafbeelding wordt de `Enrollment Form` weergegeven die is geschreven in de Adaptieve formuliereditor:

![ de Aanpassings Redacteur van de Vorm ](/help/forms/assets/af-editor-form.png)

>[!NOTE]
>
> Voor gedetailleerde begeleiding bij het creëren van een AanpassingsVorm die op het malplaatje van de Component van de Kern wordt gebaseerd, [ klik hier ](/help/forms/creating-adaptive-form-core-components.md).

Nu kunt u [ vormen voorlegt acties voor vormen ](/help/forms/configure-submit-actions-core-components.md).

>[!ENDTABS]

### Het formulier publiceren

Om een AanpassingsVorm op Edge Delivery Services te publiceren, moet u [ een Configuratie van Edge Delivery Services op een 1} instantie van AEM tot stand brengen.](#create-an-edge-delivery-services-configuration)

#### Een Edge Delivery Services-configuratie maken

Voer de volgende stappen uit om de Edge Delivery Services-configuratie te maken:

>[!BEGINTABS]
>[!TAB  voor gecreeerde vormen gebruikend het op Edge Delivery Services-Gebaseerde malplaatje ]


De Edge Delivery Services-configuratie voor formulieren op basis van de Edge Delivery Services-sjabloon wordt automatisch gemaakt in de configuratiecontainer van het formulier.

![ Configuratie van Edge Delivery Services ](/help/edge/assets/aem-instance-eds-configuration.png)

>[!TAB  voor vormen die gebruikend het op component-Gebaseerde malplaatje van de Kern worden gecreeerd ]

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Edge Delivery Services Configuration]** op de AEM Forms as a Cloud Service-auteurinstantie.

   ![ Uitgezochte Configuratie van Edge Delivery Services ](/help/edge/assets/select-eds-conf.png)

1. Selecteer de map met de naam van het formulier. Als het formulier bijvoorbeeld `enrollment-form` heet, kiest u de map `forms/enrollment-form` en klikt u op **[!UICONTROL Create]** > **[!UICONTROL Configuration]** :

   ![ Configuratie van Edge Delivery Services ](/help/forms/assets/create-eds-conf.png)

1. Klik op **[!UICONTROL Edge Delivery Services Configuration]** en klik op **[!UICONTROL Properties]** om de eigenschappen te openen:

   ![ creeerde automatisch configuratie ](/help/forms/assets/eds-conf.png)

   De Edge Delivery Services-configuratie wordt weergegeven.

1. Geef het volgende op in de Edge Delivery Services-configuratie:

   * **Organisatie**: Specificeer uw GitHub organisatienaam.

   * **Naam van de Plaats**: Specificeer uw bewaarplaatsnaam GitHub.
   * **Tak**: Specificeer de taknaam. Laat het tekstvak leeg als u de hoofdvertakking gebruikt.
   * **(Optioneel) Edge-host** : laat de optie Edge-host ongewijzigd. Het formulier wordt gepubliceerd naar zowel een voorbeeldomgeving (.page) als een live-omgeving (.live).
   * **(Facultatief) Token van de Authentificatie van de Plaats**: Gebruik het Token van de Authentificatie van de Plaats om verzoeken tussen uw AEM instantie en Edge Delivery Services veilig voor authentiek te verklaren.

1. Klik op **[!UICONTROL Save and Close]**. De configuratie wordt gemaakt.

>[!ENDTABS]

#### Het formulier openen op Edge Delivery Services

Als u het formulier wilt openen op Edge Delivery Services, moet u het formulier publiceren. Voer de volgende stappen uit om het formulier te publiceren:

>[!BEGINTABS]
>[!TAB  op Universele Redacteur ]

1. Publiceer het formulier door op de knop **[!UICONTROL Publish]** in de rechterbovenhoek van de Universal Editor te klikken.

![ publiceer vorm ](/help/edge/assets/publish-form.png)

>[!NOTE]
>
> Verwijs naar [ publiceren en stel ](/help/edge/docs/forms/universal-editor/publish-forms.md) artikel op om te leren hoe te om een vorm aan Edge Delivery Services te publiceren.

>[!TAB  op de Adaptieve Redacteur van de Vorm ]

1. Navigeer in de Experience Manager Forms-console naar de bovenliggende map en selecteer een formulier dat u wilt publiceren.

1. Klik op de optie **[!UICONTROL Publish]** op de werkbalk en bekijk alle referentie-elementen die met het formulier worden gepubliceerd.

![ publiceer Vorm op de Adaptieve Redacteur van de Vorm ](/help/forms/assets/publish-af-editor.png)

>[!NOTE]
>
> Verwijs naar [ leiden Publicatie in Experience Manager Forms ](/help/forms/manage-publication.md) artikel om te leren hoe te om een vorm op de Adaptieve Redacteur van de Vorm te publiceren.

>[!ENDTABS]

* **Gelaagde Versie (voor het testen)**: De gestagte versie toont de niet gepubliceerde, werkende versie van de vorm voor het testen doeleinden. Gebruik de volgende URL-indeling om een voorbeeld van het formulier te bekijken voordat het live gaat:

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`



* **Levende Versie (gepubliceerde vorm)**:   In de live versie wordt de meest recente gepubliceerde versie van het formulier weergegeven, die toegankelijk is voor eindgebruikers. Gebruik de volgende URL-indeling om toegang te krijgen tot de gepubliceerde, live versie van het formulier:

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  De URL-structuur blijft hetzelfde voor zowel gefaseerde als actieve versies. De inhoud die u ziet, verschilt echter op basis van de context.

In de onderstaande schermafbeeldingen worden URL&#39;s van gefaseerde en live formulieren vergeleken met visuele voorvertoningen voor formulieren die zijn gemaakt met op Edge Delivery Services gebaseerde en op Core Component gebaseerde sjablonen:

>[!BEGINTABS]
>[!TAB  Toegang hebbend tot vormen die gebruikend op Edge Delivery Services-Gebaseerd Malplaatje ] worden gecreeerd

<table border="1" style="width: 100%; border-collapse: collapse; text-align: left;">
    <thead>
    <tr>
      <th style="width: 20%;"><strong>Versie</strong></th>
      <th style="width: 80%;"><strong>Afbeelding</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr>
      <td>Stage-versie</td>
      <td><img src="/help/forms/assets/registration-form-staged-version.png" alt="Geleidelijke versie van registratieformulier" style="width: 100%; height: auto;" /></td>
    </tr>
    <tr>
      <td>Live versie</td>
      <td><img src="/help/forms/assets/registration-form-live-version.png" alt="Live versie van registratieformulier" style="width: 100%; height: auto;" /></td>
    </tr>
    </tbody>
  </table>

>[!TAB  Toegang hebbend tot tot vormen die gebruikend Op componenten-Gebaseerd Malplaatje van de Kern worden gecreeerd ]

<table border="1" style="width: 100%; border-collapse: collapse; text-align: left;">
  <thead>
    <tr>
      <th style="width: 20%;"><strong>Versie</strong></th>
      <th style="width: 80%;"><strong>Afbeelding</strong></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Stage-versie</td>
      <td><img src="/help/forms/assets/enrollment-form-staged-version.png" alt="Geleidelijke versie van inschrijvingsformulier" style="width: 100%; height: auto;" /></td>
    </tr>
    <tr>
      <td>Live versie</td>
      <td><img src="/help/forms/assets/enrollment-form-live-version.png" alt="Live versie van inschrijvingsformulier" style="width: 100%; height: auto;" /></td>
    </tr>
  </tbody>
  </table>

>[!ENDTABS]

## Problemen oplossen

Problemen met het laden van uw formulier? Hier volgen enkele veelvoorkomende problemen en hoe deze kunnen worden verholpen:

* **Vorm URL**: Controle tweemaal dat URL van uw vorm niet de uitbreiding &quot;.html&quot;aan het eind omvat. Voor Edge Deliver Service is deze extensie niet vereist.

* **URL van de Auteur van AEM van**: Zorg ervoor de Auteur URL van AEM in uw `fstab.yaml` dossier wordt vermeld correct geformatteerd. Het moet de volgende gegevens bevatten:

   * De juiste GitHub-eigenaar
   * De juiste naam van de opslagplaats
   * De specifieke vertakking die je gebruikt voor Edge Delivery Services

## Formulieren maken

{{universal-editor-see-also}}

<!-- * **JSON Display**: If you see only JSON data instead of the actual form, your form block might be outdated. You can update it to the latest version available on https://github.com/adobe-rnd/aem-boilerplate-forms.

### Managing a form

You can perform several operations on form using the AEM Forms user interface.

1. Login into your AEM Forms as a Cloud Service author instance.
1. Select **[!UICONTROL Adobe Experience Manager]** &gt; **[!UICONTROL Forms]** &gt; **[!UICONTROL Forms & Documents]**.

1. Select a form and the toolbar displays the following operations you can perform on the selected form.

<table>
 <tbody>
  <tr>
   <td><p><strong>Operation</strong></p> </td>
   <td><p><strong>Description</strong></p> </td>
  </tr>
  <tr>
   <td><p>Edit</p> </td>
   <td><p>Opens the form in edit mode.<br /> <br /> </p> </td>
  </tr>
    <tr>
   <td><p>Properties</p> </td>
   <td><p>Provides options to modify the properties of the form.<br /> <br /> </p> </td>
  </tr>
  <td><p>Copy</p> </td>
   <td><p> Provides options to copy the form  and paste it at the desired location. <br /> <br /> </p> </td>
  </tr>
   <tr>
   <td><p>Preview</p> </td>
   <td><p>Provides options to preview the form as HTML or perform a custom preview by merging data from an XML file with the form. <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Download</p> </td>
   <td><p>Downloads the selected form.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Start Review/Manage Review</p> </td>
   <td><p>Allows initiating and managing a review of the selected form.<br /> <br /> </p> </td>
  </tr>
  <!--<tr>
   <td><p>Add Dictionary</p> </td>
   <td><p>Generates a dictionary for localizing the selected fragment. For more information, see <a>Localizing Adaptive Forms</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Publish / Unpublish</p> </td>
   <td><p>Publishes / unpublishes the selected form.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Delete</p> </td>
   <td><p>Deletes the selected form.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Compare</p> </td>
   <td><p>Compares two different form for previewing purposes.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table> 


## How Edge Delivery Services Forms Work?

Users can author Edge Delivery Services Forms using document-based authoring tools such as Google Drive, SharePoint, or the Universal Editor (WYSIWYG authoring), while leveraging the basic styling, behaviour and components available in the GitHub repository. Once authored, Edge Delivery Services Forms can send data to any platform using the Forms Submission Service.

![How Edge Delivery Services Forms works](/help/edge/docs/forms/assets/eds-forms-working.png)

### Key components of Edge Delivery Services Forms

The key components of Edge Delivery Servies Forms are:

* **GitHub Repository**: The GitHub repository serves as a boilerplate for creating Edge Delivery Services Forms. The forms leverage basic styling and functionality from the repository and allow users to add customizations and custom components to the Edge Delivery Services Forms.

* **Form Authoring**: Edge Delivery Services Forms support two types of authoring: WYSIWYG and document-based authoring. Document-based authoring enables users to create forms using familiar tools like Google Docs and Microsoft Office. WYSIWYG authoring allows users to design forms visually using the Universal Editor, making it easy for non-technical users to create and manage forms. Universal Editor offers an intuitive form creation experience and provides access to numerous form capabilities.

* **Forms Submission Service**: The Forms Submission Service allows you to store data from forms submissions on any platform, such as OneDrive, SharePoint, or Google Sheets, making it easy to access and manage form data within your preferred system.-->
