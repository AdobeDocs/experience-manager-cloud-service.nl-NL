---
title: Hoe te om standalone AanpassingsForms tot stand te brengen gebruikend Universele Redacteur?
description: In dit artikel wordt uitgelegd hoe u Adaptive Forms kunt maken met de wizard Formulier maken in de AEM-ontwerpinstantie en hoe u formulieren kunt publiceren naar AEM Edge Delivery Services.
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: a95b0d4dd6db92e68bdb7059bdd4e0e5be936195
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 0%

---

# Zelfstandige formulieren van auteurs met de Universal Editor (WYSIWYG)

<span class="preview"> Deze functie is beschikbaar via het programma voor vroege toegang. Om toegang te verzoeken, verzend een e-mail met uw GitHub organisatienaam en bewaarplaatsnaam van uw officieel adres aan <a href="mailto:aem-forms-ea@adobe.com"> aem-forms-ea@adobe.com </a>. Bijvoorbeeld, als de bewaarplaats URL https://github.com/adobe/abc is, is de organisatienaam adobe en de bewaarplaatsnaam abc.</span>

Dit artikel begeleidt u door het ontwerpen van de zelfstandige formulieren met de Universal Editor door een op Edge Delivery Services gebaseerde sjabloon te selecteren in de wizard Formulier maken. U kunt de geschreven formulieren ook publiceren met Universal Editor naar AEM Edge Delivery Services.

<!--To publish forms to Edge Delivery Services, you must first establish a connection between your AEM environment and your GitHub repository. Once connected, you can author the forms using the Universal Editor, which follows a WYSIWYG (What You See Is What You Get) approach for a seamless and consistent user experience with Sites.-->

Voordat u begint, moet u meer weten over het type Forms-componenten waarover u beschikt:

* [ Edge Delivery Services voor AEM Forms ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) is een composable reeks diensten die een snelle ontwikkelomgeving toelaat waar de auteurs, nieuwe vormen kunnen bijwerken publiceren en snel lanceren gebruikend Universele Redacteur. De Universal Editor vereenvoudigt het maken van formulieren voor Adobe Edge Delivery Services met een gebruiksvriendelijke, visuele WYSIWYG-interface.

* [ Aangepaste Componenten van de Kern van Forms ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en): Dit zijn gestandaardiseerde gegevens vangen componenten. Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijving. Een ontwikkelaar kan deze componenten eenvoudig aanpassen en opmaken. U kunt [ https://aemcomponents.dev/ ](https://aemcomponents.dev/) bezoeken om beschikbare kerncomponenten in actie **te bekijken Adobe adviseert gebruikend deze moderne en verlengbare componenten om Aangepaste Forms** te ontwikkelen.

* [ Aangepaste Componenten van de Stichting van Forms ](/help/forms/creating-adaptive-form.md): Dit zijn klassieke (oude) gegevens vangen componenten. U kunt deze blijven gebruiken om uw bestaande basiscomponenten te bewerken op basis van adaptief formulier. Als u nieuwe vormen creeert, beveelt Adobe het gebruiken van [ Aangepaste Componenten van de Kern van Forms aan om een Aangepaste Forms ](#create-an-adaptive-form-core-components) tot stand te brengen.

AEM Forms biedt een blok, het Adaptive Forms Block, waarmee u eenvoudig Edge Delivery Services Forms kunt maken om gegevens vast te leggen en op te slaan. U kunt [ een nieuw Project van AEM tot stand brengen dat met het AanpassingsBlok van Forms ](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) wordt gevormd of [ het Aangepaste Blok van Forms aan een bestaand Project van de Plaats van AEM ](#add-adaptive-forms-block-to-your-existing-aem-project) toevoegt.

![ Github het Werkschema van de Bewaarplaats ](/help/edge/assets/repo-workflow.png)

## Voorwaarden

* [ opstelling uw bewaarplaats GitHub ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) om een verbinding tussen uw milieu van AEM en de bewaarplaats te vestigen GitHub.
* Als u reeds Edge Delivery Services gebruikt, voeg de recentste versie van het [ Aangepaste blok van Forms ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) aan uw bewaarplaats GitHub toe.
* De AEM Forms Author-instantie bevat een sjabloon op basis van Edge Delivery Services. Verzeker de [ recentste versie van de Componenten van de Kern ](https://github.com/adobe/aem-core-forms-components) in uw milieu geïnstalleerd is.
* Houd de URL van uw AEM Forms as a Cloud Service-auteurinstantie en uw GitHub Repository handig.

## Een adaptief formulier maken met de Universal Editor

Met de Universal Editor kunt u gemakkelijk responsieve en interactieve zelfstandige formulieren maken met kant-en-klare componenten, zoals tekstvelden, selectievakjes en keuzerondjes. Het biedt krachtige functies, zoals dynamische regels, vloeiende gegevensintegratie en aanpassingsopties, waarmee u formulieren volgens uw vereisten kunt maken.

>[!NOTE]
>
> U kunt ook [ auteur een vorm in de Plaats van AEM gebruiken het malplaatje van de Plaats van Edge Delivery Services in Universele Redacteur en het publiceren aan Edge Delivery Services ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project).

Voer de volgende stappen uit als u een zelfstandig adaptief formulier wilt ontwerpen met de Universal Editor:

1. **creeer een Adaptief Vorm op de auteursinstantie van AEM Forms**

   1. Open de AEM Forms as a Cloud Service-auteurinstantie.
   1. Selecteer **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Adaptive Forms]** . De wizard wordt geopend.
   1. In het **Source** lusje, selecteer een op Edge Delivery Services gebaseerd vormmalplaatje:

      ![ creeer EDS Forms ](/help/edge/assets/create-eds-forms.png)


      Wanneer u een op Edge Delivery Services gebaseerde sjabloon selecteert, wordt de knop **[!UICONTROL Create]** ingeschakeld.
   1. (Optioneel) Op de tabbladen **[!UICONTROL Data Source]** of **[!UICONTROL Submission]** kunt u een gegevensbron selecteren of een handeling verzenden.
   1. (Optioneel) Op het tabblad **[!UICONTROL Delivery]** kunt u een publicatiedatum of een publicatiedatum opgeven voor een adaptief formulier.

   1. Klik **[!UICONTROL Create]** en de **creeer 2} tovenaar van de Vorm {verschijnt.**
   1. Specificeer de **Naam** en **Titel**.
   1. Specificeer **GitHub URL**. Als uw GitHub-opslagplaats bijvoorbeeld de naam `edsforms` heeft, bevindt deze zich onder de account `wkndforms` , is de URL:
      `https://github.com/wkndforms/edsforms`
   1. Klik op **[!UICONTROL Create]**.

      ![ creeer de tovenaar van de Vorm ](/help/edge/assets/create-form-wizard.png)

      Zodra u op **[!UICONTROL Create]** klikt, wordt het formulier in de Universal Editor geopend voor ontwerpen.

      ![ auteur de vorm ](/help/edge/assets/author-form.png)

      <!-- >[!NOTE]
        >
        > The Edge Delivery Services configuration for the forms based on Edge Delivery Services template is created automatically at the form's configuration container.-->

      Wanneer u op **[!UICONTROL Create]** klikt, wordt het formulier in de Universal Editor geopend voor ontwerpen.

1. **Auteur de vorm in de Universele Redacteur**

   1. Open Inhoudsbrowser, en navigeer aan de **[!UICONTROL Adaptive Form]** component in de **boom van de Inhoud**.

      ![ inhoudsboom ](/help/edge/assets/content-tree.png)

   1. Klik het **[!UICONTROL Add]** pictogram en voeg de gewenste componenten van de **Adaptieve lijst van Componenten van de Vorm** toe.

      ![ voeg component ](/help/edge/assets/add-component.png) toe

   1. Selecteer de toegevoegde component Adaptief formulier en werk de eigenschappen ervan bij met **[!UICONTROL Properties]** .

      ![ open eigenschappen ](/help/edge/assets/component-properties.png)

      In de onderstaande schermafbeelding wordt het eenvoudige `Registration Form` -formulier weergegeven dat is geschreven in de Universal Editor:

      ![ contacteer ons vorm ](/help/edge/assets/contact-us.png)

      Nu kunt u [ vormen en Vorm aanpassen voorleggen Acties ](/help/edge/docs/forms/universal-editor/submit-action.md).


<!--
## **Edge Delivery Services configuration of form**



   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Edge Delivery Services Configuration]** on your AEM Forms as a Cloud Service author instance.

        ![Select Edge Delivery Services Configuration](/help/edge/assets/select-eds-conf.png)
   1. Select the folder that matches the form's name. For example, if your form is called 'registration-form' choose the folder `forms/registration-form` and selct the configuration and publish the configuration:

        ![Edge Delivery Services Configuration](/help/edge/assets/aem-instance-eds-configuration.png)

   1. Click **[!UICONTROL Properties]** to see the configuration.   
        ![Automatically created configuration](/help/edge/assets/aem-forms-create-configuration-github.png)

        You can leave the Edge Host option as it is. The form would be published to both preview (.page) and live (.live) environments. 

   1. Click **[!UICONTROL Save and Close]**. The configuration is saved. -->

## Het formulier publiceren

Publiceer nu het zelfstandige formulier naar Edge Delivery Services door op de knop **[!UICONTROL Publish]** in de rechterbovenhoek van de Universal Editor te klikken.

![ publiceer vorm ](/help/edge/assets/publish-form.png)

>[!NOTE]
>
> Verwijs naar [ publiceren en stel ](/help/edge/docs/forms/universal-editor/publish-forms.md) artikel op om te leren hoe te om een vorm aan Edge Delivery Services te publiceren.

Hieronder wordt beschreven hoe u het formulier opent op Edge Delivery Services:

* **Gelaagde Versie (voor het testen)**: De gestagte versie toont de niet gepubliceerde, werkende versie van de vorm voor het testen doeleinden. Gebruik de volgende URL-indeling om een voorbeeld van het formulier te bekijken voordat het live gaat:

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`

  Als de gegevensopslagruimte van uw project bijvoorbeeld &quot;edsforms&quot; heet, bevindt deze zich onder de account &quot;wkndforms&quot; en gebruikt u de &quot;main&quot; vertakking en het formulier als &quot;Registratieformulier&quot;, ziet de gefaseerde versie-URL er als volgt uit:
  `https://main--edsforms--wkndforms.aem.page/content/forms/af/registration-form`

* **Levende Versie (gepubliceerde vorm)**:   In de live versie wordt de meest recente gepubliceerde versie van het formulier weergegeven, die toegankelijk is voor eindgebruikers. Gebruik de volgende URL-indeling om toegang te krijgen tot de gepubliceerde, live versie van het formulier:

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  Als de gegevensopslagruimte van uw project bijvoorbeeld &quot;edsforms&quot; heet, bevindt deze zich onder de account &quot;wkndforms&quot; en gebruikt u de &quot;main&quot; vertakking en het formulier als &quot;Registratieformulier&quot;, ziet de gefaseerde versie-URL er als volgt uit:
  `https://main--edsforms--wkndforms.aem.live/content/forms/af/registration-form`

De URL-structuur blijft hetzelfde voor zowel gefaseerde als actieve versies. De inhoud die u ziet, verschilt echter op basis van de context:

![ Mening gepubliceerde vorm ](/help/edge/assets/eds-view-publish-form.png)

## Problemen oplossen

Problemen met het laden van uw formulier? Hier volgen enkele veelvoorkomende problemen en hoe deze kunnen worden verholpen:

* **Vorm URL**: Controle tweemaal dat URL van uw vorm niet de uitbreiding &quot;.html&quot;aan het eind omvat. Voor Edge Deliver Service is deze extensie niet vereist.

* **URL van de Auteur van AEM van**: Zorg ervoor de Auteur URL van AEM in uw `fstab.yaml` dossier wordt vermeld correct geformatteerd. Het moet de volgende gegevens bevatten:

   * De juiste GitHub-eigenaar
   * De juiste naam van de opslagplaats
   * De specifieke vertakking die je gebruikt voor Edge Delivery Services

<!-- * **JSON Display**: If you see only JSON data instead of the actual form, your form block might be outdated. You can update it to the latest version available on https://github.com/adobe-rnd/aem-boilerplate-forms.
-->

## Formulieren maken

{{universal-editor-see-also}}
