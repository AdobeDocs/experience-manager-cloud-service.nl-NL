---
title: Forms for Edge Delivery Services publiceren
description: Leer hoe formulieren die publiceren werken met Edge Delivery Services en hoe u AEM formulieren publiceert met Edge Delivery Services.
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
source-git-commit: bdc0e51a8b16df432f1f1aeabed11135fb8c8e0c
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 0%

---


# Forms for Edge Delivery Services publiceren

Dit artikel begeleidt u door het proces van het publiceren van formulieren naar AEM Edge Delivery Services.
Als u formulieren naar Edge Delivery Services wilt publiceren, moet u eerst een verbinding tot stand brengen tussen uw AEM en uw GitHub-opslagplaats. Als de verbinding tot stand is gebracht, kunt u de formulieren ontwerpen met de Universal Editor. Deze editor volgt een WYSIWYG-benadering (What You See Is What You Get) voor een naadloze en consistente gebruikerservaring met sites.

## Voorwaarden

* Nieuw bij Adaptive Forms? Opstelling uw bewaarplaats GitHub na het verstrekte [ leerprogramma ](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project).
* Als u reeds Edge Delivery Services gebruikt, voeg de recentste versie van het [ Aangepaste blok van Forms ](/help/edge/docs/forms/tutorial.md#) aan uw bewaarplaats GitHub toe.
* De AEM Forms-instantie Auteur bevat een sjabloon op basis van Edge Delivery Services. Verzeker de [ recentste versie van de Componenten van de Kern ](https://github.com/adobe/aem-core-forms-components) in uw milieu geïnstalleerd is.
* Houd URL van uw as a Cloud Service auteursinstantie van AEM Forms en uw Bewaarplaats GitHub handig.

## Publish Forms voor Edge Delivery Services

Voer de volgende stappen uit om formulieren voor Edge Delivery Services te publiceren:

[1. Link GitHub Repository naar AEM instantie](#link-github-repository-to-aem-instance)

[2. Link AEM instantie naar GitHub Repository](#link-aem-instance-to-github-repository)

### GitHub Repository koppelen aan AEM instantie

Om [ uw project op het Bewaarplaats GitHub ](/help/edge/docs/forms/tutorial.md) aan de instantie van de Auteur van AEM Forms te verbinden, voer de volgende stappen uit:

1. Ga naar uw bewaarplaats GitHub die u voor uw Edge Delivery Services hebt gecreeerd of gevormd.
1. Open het `fstab.yaml` -bestand om het te bewerken.
1. Werk het `fstab.yaml` dossier in uw bewaarplaats GitHub met URL van uw as a Cloud Service instantie van AEM Forms bij.

   ```javascript
    mountpoints:
    /:
        url: [author-instance-url]/bin/franklin.delivery/[Github owner]/[Github Repository]/[Github branch] 
        type: "markup"
        suffix: ".html"
   ```

   Bijvoorbeeld, als uw bewaarplaats GitHub &quot;aemcrosswalk&quot;wordt genoemd, wordt het gevestigd onder de rekening &quot;wkndform&quot;, en u gebruikt de &quot;belangrijkste&quot;tak, kijkt de auteursinstantie URL als het volgende:

   ```
        mountpoints:
            /:
            url: https://author-p133911-e1313554.adobeaemcloud.com/bin/franklin.delivery/wkndform/aemcrosswalk/main
            type: "markup"
            suffix: ".html"
   ```

1. Leg de wijzigingen in het `fstab.yaml` -bestand vast.

### AEM instantie koppelen aan GitHub Repository

Om de instantie van de Auteur van AEM Forms aan [ te verbinden uw project op het Bewaarplaats GitHub ](/help/edge/docs/forms/tutorial.md), voer de volgende stappen uit:

[1. Maak een adaptief formulier op basis van de sjabloon Edge Delivery Services](#1-create-an-adaptive-form-based-on-the-edge-delivery-services-template)

[2. Zoek de configuratiecontainer van het formulier in AEM auteurinstantie](#2-locate-your-forms-configuration-container-in-aem-author-instance)

[3. Auteur van het formulier in de universele editor](#3-author-the-form-in-the-universal-editor)

[4. Publish en voorbeeld van het formulier](#4-publish-and-preview-the-form)

#### 1. Maak een adaptief formulier op basis van de sjabloon Edge Delivery Services

1. Open uw AEM Forms as a Cloud Service auteur-exemplaar.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Adaptive Forms]** . De wizard wordt geopend. Selecteer op het tabblad Source een op Edge Delivery Services gebaseerde formuliersjabloon:

   ![ creeer EDS Forms ](/help/edge/assets/create-eds-forms.png) {width=50%, richt-centrum}

1. Klik **[!UICONTROL Create]** en de **creeer 2} tovenaar van de Vorm {verschijnt.**
1. Specificeer **GitHub URL**. Bijvoorbeeld, als uw bewaarplaats GitHub &quot;aemcrosswalk&quot;wordt genoemd, wordt het gevestigd onder de rekening &quot;wkndform&quot;, is URL:
   `https://github.com/wkndform/aemcrosswalk`
1. Klik op **[!UICONTROL Create]**.

   ![ creeer de tovenaar van de Vorm ](/help/edge/assets/create-form-wizard.png) {width=50%, richten-centrum}

   Zodra u op **[!UICONTROL Create]** klikt, wordt het formulier in de Universal Editor geopend voor ontwerpen.

   ![ auteur de vorm ](/help/edge/assets/author-form.png) {width=50%, richten-centrum}

   >[!NOTE]
   >
   > De configuratie Edge Delivery Services voor de formulieren op basis van de sjabloon Edge Delivery Services wordt automatisch gemaakt in de configuratiecontainer van het formulier.

#### 2. Zoek de configuratiecontainer van het formulier in AEM auteurinstantie

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Edge Delivery Services Configuration]** op uw AEM Forms as a Cloud Service auteurinstantie.
1. Selecteer de map met de naam van het formulier. Als uw formulier bijvoorbeeld &#39;contact-us&#39; wordt genoemd, kiest u de map `forms/contact-us` en selecteert u de configuratie en publiceert u de configuratie:

   ![ Configuratie van Edge Delivery Services ](/help/forms/assets/aem-instance-eds-configuration.png) {width=50%, richten-centrum}

1. Klik op **[!UICONTROL Properties]** om de configuratie weer te geven.\
   ![ creeerde automatisch configuratie ](/help/edge/assets/aem-forms-create-configuration-github.png) {width=50%, richt-centrum}

   U kunt de optie Edge Host ongewijzigd laten. Het formulier wordt gepubliceerd naar zowel een voorbeeldomgeving (.page) als een live-omgeving (.live).

1. Klik op **[!UICONTROL Save and Close]**. De configuratie wordt opgeslagen.

#### 3. Auteur van het formulier in de universele editor

Wanneer u op **[!UICONTROL Create]** klikt, wordt het formulier in de Universal Editor geopend voor ontwerpen.

1. Open Inhoudsbrowser, en navigeer aan de **[!UICONTROL Adaptive Form]** component in de **boom van de Inhoud**.

   ![ inhoudsboom ](/help/edge/assets/content-tree.png) {width=50%, richten-centrum}

1. Klik het **[!UICONTROL Add]** pictogram en voeg de gewenste componenten van de **Adaptieve lijst van Componenten van de Vorm** toe.

   ![ voeg component ](/help/edge/assets/add-component.png) {width=50% toe, richt-centrum}

1. Selecteer de toegevoegde component Adaptief formulier en werk de eigenschappen ervan bij met **[!UICONTROL Properties]** .

   ![ open eigenschappen ](/help/edge/assets/component-properties.png) {width=50%, richten-centrum}

   In de onderstaande schermafbeelding ziet u het eenvoudige &#39;Contact opnemen&#39;-formulier dat in de Universal Editor is geschreven:

   ![ contacteer ons vorm ](/help/edge/assets/contact-us.png) {width=50%, richten-centrum}

#### 4. Publish en voorbeeld van het formulier

Publiceer het formulier nu naar Edge Delivery Services door op de knop **[!UICONTROL Publish]** in de rechterbovenhoek van de Universal Editor te klikken.

![ publiceer vorm ](/help/edge/assets/publish-form.png) {width=50%, richten-centrum}


Hieronder wordt beschreven hoe u het formulier kunt openen op Edge Delivery Services:

* **Gelaagde Versie (voor het testen)**: De gestagte versie toont de niet gepubliceerde, werkende versie van de vorm voor het testen doeleinden. Gebruik de volgende URL-indeling om een voorbeeld van het formulier te bekijken voordat het live gaat:

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`

  Als de gegevensopslagruimte van uw project bijvoorbeeld &quot;aemcrosswalk&quot; heet, bevindt deze zich onder de account &quot;wkndform&quot; en gebruikt u de &quot;main&quot;-vertakking en het formulier als &quot;contact met ons&quot;, ziet de gefaseerde versie-URL er als volgt uit:
https://main—aemcrosswalk—wkndform.aem.page/content/forms/af/contact-us

* **Levende Versie (gepubliceerde vorm)**:   In de live versie wordt de meest recente gepubliceerde versie van het formulier weergegeven, die toegankelijk is voor eindgebruikers. Gebruik de volgende URL-indeling om toegang te krijgen tot de gepubliceerde, live versie van het formulier:

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  Als de gegevensopslagruimte van uw project bijvoorbeeld &quot;aemcrosswalk&quot; heet, bevindt deze zich onder de account &quot;wkndform&quot; en gebruikt u de &quot;main&quot;-vertakking en het formulier als &quot;contact met ons&quot;, ziet de gefaseerde versie-URL er als volgt uit:
https://main—aemcrosswalk—wkndform.aem.live/content/forms/af/contact-us

De URL-structuur blijft hetzelfde voor zowel gefaseerde als actieve versies. De inhoud die u ziet, verschilt echter op basis van de context:

![ Mening gepubliceerde vorm ](/help/edge/assets/eds-view-publish-form.png) {width=50%, richt-centrum}

## Problemen oplossen

Problemen met het laden van uw formulier? Hier volgen enkele veelvoorkomende problemen en hoe deze kunnen worden verholpen:

* **Vorm URL**: Controle tweemaal dat URL van uw vorm niet de uitbreiding &quot;.html&quot;aan het eind omvat. Voor Edge Deliver Service is deze extensie niet vereist.

* **AEM auteur UR** L: Zorg ervoor AEM Auteur URL in uw `fstab.yaml` dossier wordt vermeld correct geformatteerd. Het moet de volgende gegevens bevatten:

   * De juiste GitHub-eigenaar
   * De juiste naam van de opslagplaats
   * De specifieke vertakking die u voor Edge Delivery Services gebruikt

<!-- * **JSON Display**: If you see only JSON data instead of the actual form, your form block might be outdated. You can update it to the latest version available on https://github.com/adobe-rnd/aem-boilerplate-forms.
-->

## Zie ook

{{see-more-forms-eds}}