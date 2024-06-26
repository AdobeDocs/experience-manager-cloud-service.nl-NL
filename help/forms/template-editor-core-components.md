---
title: Hoe te om een Aangepast malplaatje van de Vorm tot stand te brengen dat op kerncomponent wordt gebaseerd?
description: Maak adaptieve formuliersjablonen op basis van de kerncomponent om de basisstructuur en eerste inhoud te definiëren met de Sjablooneditor.
feature: Adaptive Forms, Core Components
Keywords: create adaptive form template, create adaptive form template based on core components, Use template to create adpative form.
exl-id: c1c050d3-953e-4e56-a96b-d84f2ec05e5e
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '1884'
ht-degree: 0%

---

# Een adaptieve formuliersjabloon maken op basis van kerncomponenten {#adaptive-form-templates}

Wanneer u een formulier ontwerpt, voegt u velden en componenten toe om de formulierstructuur, inhoud en handelingen in de editor te definiëren. U voegt velden en componenten toe in het dialoogvenster `guideRootPanel` van de formuliercontainer. Met de Sjablooneditor kunt u een sjabloon maken met een basisstructuur en eerste inhoud die auteurs kunnen gebruiken om formulieren te maken.

U wilt bijvoorbeeld dat alle formulierauteurs bepaalde tekstvakken, navigatieknoppen en een verzendknop in een inschrijvingsformulier hebben. U kunt een sjabloon maken met de componenten die auteurs kunnen gebruiken om een formulier te maken dat consistent is met andere inschrijvingsformulieren. Wanneer auteurs de sjabloon gebruiken om een adaptief formulier te maken, overerft het nieuwe formulier de structuur en de componenten die u in de sjabloon hebt opgegeven. Met de Sjablooneditor kunt u:

* Voeg kop- en voettekstcomponenten van een formulier toe aan de structuurlaag.
* Geef de initiële inhoud voor het formulier op.
* Geef een thema op, namelijk Handelingen verzenden.

<!--
You can download and install [!DNL AEM Forms] reference content package from [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) portal to import reference themes and templates to your environment.
-->

## Voorwaarde

**Adaptieve Forms Core-componenten inschakelen voor uw omgeving**: Wanneer u een programma maakt, zijn de Adaptive Forms Core Components al ingeschakeld voor uw omgeving. Als u een Form as a Cloud Service-omgeving hebt die is gebaseerd op [Archetype 39 of eerder AEM](https://github.com/adobe/aem-project-archetype), [Adaptieve Forms Core-componenten inschakelen voor uw omgeving](enable-adaptive-forms-core-components.md).

>[!NOTE]
>
> Bij de implementatie van de as a Cloud Service Forms-omgeving op basis van Archetype 45, **Adaptieve Forms (Core Component)** sjablonen en kernthema&#39;s die op componenten zijn gebaseerd, worden aan uw omgeving toegevoegd.

## Werken met een sjabloon {#working-with-templates}

U kunt tot malplaatjeredacteur van het menu van Hulpmiddelen toegang hebben door aan te navigeren **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Templates]**. Hier worden de sjablonen ingedeeld in mappen die zijn ingeschakeld voor bewerkbare sjablonen.

>[!NOTE]
>
> U kunt de op de kerncomponent gebaseerde bewerkbare sjablonen vinden in de kernmappen voor componenten.

Experience Manager biedt een algemene map voor het organiseren van sjablonen. Deze optie is echter niet standaard ingeschakeld. U kunt de beheerder vragen de algemene map in te schakelen of een map voor sjablonen te maken. Ga voor meer informatie over het maken van mappen naar [Sjabloonmappen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/templates.html#editing-templates-template-authors).

## Een sjabloon maken {#create-template}

Nadat u een map hebt gemaakt, opent u de map en voert u de volgende stappen uit om een sjabloon te maken:

1. Selecteren **[!UICONTROL Create]** in de map die u hebt gemaakt.
1. In de **[!UICONTROL Pick a Template Type]** sectie, selecteert u **[!UICONTROL Adaptive Form (Core Component) template]** en selecteert u **[!UICONTROL Next]**.

1. In de **[!UICONTROL Template Details]** een **Sjabloontitel** en selecteert u **[!UICONTROL Create]**.
U kunt ook een beschrijving opgeven.

1. Selecteren **[!UICONTROL Done]** om naar de console terug te keren, of selecteer **[!UICONTROL Open]** om de sjabloon in de editor te openen.

## UI voor sjablooneditor {#template-editor-ui}

Wanneer u een sjabloon opent voor bewerking, kunt u de volgende AEM Editor-componenten zien:

* **Pagina, werkbalk**
Bevat de volgende opties:

   * **Zijpaneel in-/uitschakelen**: Hiermee kunt u het zijpaneel weergeven of verbergen.
   * **Pagina-informatie**: Hier kunt u informatie opgeven zoals de publicatie-/publicatietijd, miniaturen, bibliotheken aan de clientzijde, het paginabeleid en de clientbibliotheek van het paginaontwerp.
     <!-- * **Emulator**: Lets you simulate and customize the look for different devices.-->
   * **Modus selecteren:** Hiermee kunt u de modus wijzigen. U kunt **[!UICONTROL Structure]** modus, **[!UICONTROL Initial Content]**, **[!UICONTROL Layout Control]** -modus. In de structuurmodus kunt u de kop- en voettekst toevoegen en aanpassen. In de modus Initiële inhoud kunt u de inhoud van het formulier aanpassen.
   * **Voorvertoning:** Hiermee kunt u een voorvertoning weergeven van het uiterlijk van de sjabloon wanneer u de sjabloon publiceert. U kunt Laagkiezer en Voorvertoning gebruiken om de bewerkings- en voorvertoningsmodi in en uit te schakelen.
* **Zijbalk:** Verstrekt de Inhoud, Eigenschappen, Assets, en de browsers van Componenten.
* **Component, werkbalk:** Wanneer u een component selecteert, ziet u een werkbalk waarin u de component kunt aanpassen.
* **Pagina**: Het gebied waar u inhoud toevoegt om de sjabloon te maken.

<!-- See [Introduction to authoring Adaptive Forms](introduction-forms-authoring.md) to understand the Touch UI editor. -->

## Een sjabloon bewerken {#editing-a-template}

De volgende modi zijn van toepassing op het selecteren en bewerken van het juiste aspect van de sjabloon:

* [Structuur](#structure)
* [Oorspronkelijke inhoud](#initial-content)
* [Layout](#layout)

De laagkiezer is beschikbaar naast de optie Voorvertoning in de rechterbovenhoek van het scherm.

### Structuur {#structure}

Wanneer u de structuurlaag selecteert in de Sjablooneditor, kunt u vooraf de inhoud definiëren die niet kan worden gewijzigd tijdens het maken van een adaptieve Forms die is gekoppeld aan de sjabloon.

<!-- you can see the layout containers above and below the Adaptive Form Container. Authors can use these layout containers for header and footer. -->


![Lay-outcontainer in de structuurlaag](/help/forms/assets/header-layer-selector-core-component.png)

<!--

**A. Layout container for Header component**
Drag-drop the Adaptive Form Header component in the layout container above the Adaptive Form Container. After you add the component, you can specify its properties that let you add a logo and provide its title.
**B. Adaptive Form Container component**
Drag-drop the Adaptive Form components in the Adaptive Form Container. You can specify the design and arrangement of fields and components in the template editor. After you add the components, you can specify its properties.
**C. Layout container for Footer component**
Similarly, when you drag-drop the footer component in the layout container below the Adaptive Form Container, you can provide the copyright information and company details. 
You can add, edit, or customize the header and footer. Drag-drop the Adaptive Form Header and Footer component to customize the template. Drag-drop the Adaptive Form components in the Adaptive Form Container. You can specify the design and arrangement of fields and components in the template editor. 


Header and footer are added in the Initial Content layer.
-->

#### Componenten in de structuurlaag vergrendelen/ontgrendelen {#locking-unlocking-components-in-the-structure-layer}

Wanneer u de sjabloon bewerkt terwijl de structuurlaag is geselecteerd, kunt u de kop- en voettekst van de sjabloon ontgrendelen. Als een component ontgrendeld is in de sjabloon, kunnen formulierauteurs de component bewerken in het adaptieve formulier waarin de sjabloon wordt gebruikt. Door een component te vergrendelen voorkomt u dat auteurs van formulieren deze bewerken in het adaptieve formulier. De optie Vergrendelen is beschikbaar op de werkbalk van de component.

U voegt bijvoorbeeld de koptekstcomponent in de sjabloon toe. Wanneer u de component selecteert, ziet u een vergrendelingsoptie op de werkbalk van de component. Koptekst bevat doorgaans een bedrijfsnaam en een logo en u wilt niet dat auteurs van formulieren het logo en de koptekst in een sjabloon wijzigen. In een adaptief formulier dat is gemaakt met de sjabloon met de koptekstcomponent vergrendeld, kunnen auteurs van formulieren het logo en de bedrijfsnaam niet wijzigen.

>[!NOTE]
>
>Het wordt niet aanbevolen de afbeelding of het logo in de koptekstcomponent afzonderlijk te vergrendelen of te ontgrendelen. U kunt de koptekstcomponent ontgrendelen.

### Oorspronkelijke inhoud {#initial-content}

Als de optie Begininhoud is geselecteerd, wordt de container van het adaptieve formulier van de sjabloon geopend als een adaptief formulier voor bewerking. Hiermee kunt u een vooraf gedefinieerde inhoud maken die kan worden gewijzigd wanneer u een adaptieve Forms maakt die aan de sjabloon is gekoppeld. Net als bij het ontwerpen van een adaptief formulier kunt u initiële instellingen opgeven, zoals een thema selecteren en Handelingen verzenden.

Formulierauteurs gebruiken het als basis om een formulier te maken. De structuur van de inhoudsstroom wordt opgegeven in de laag Begininhoud van de sjabloon. Als u wilt overschakelen naar het bewerken van de eerste inhoud van de formuliersjabloon, selecteert u voordat u een voorbeeld weergeeft op de pagina-werkbalk ![canvas-drop-down](assets/canvas-drop-down.png) **>** **[!UICONTROL Initial Content]**.

![Koptekst en voettekst die zijn toegevoegd in de laag Oorspronkelijke inhoud](assets/header-and-footer.png)

In de Eerste laag van de Inhoud, creeert u het Adaptieve malplaatje van de Vorm dat uw auteurs als basis gebruiken. Het ontwerpen van een sjabloon lijkt op het ontwerpen van een formulier. U gebruikt de opties in de zijbalk. Sidebar verstrekt inhoud, eigenschappen, activa, en componentenbrowsers.

<!-- See [Sidebar](introduction-forms-authoring.md#sidebar). -->

>[!NOTE]
>
>Wanneer u Inhoud opslaan of PDF opslaan selecteert als Verzendhandeling, kunt u het opslagpad opgeven. Als u een pad opgeeft in een sjabloon, hebben alle formulieren die ermee worden gemaakt hetzelfde pad. U kunt het juiste opslagpad opgeven of formulierauteurs de opslaglocatie laten bijwerken om te voorkomen dat gegevens in elk formulier op dezelfde locatie worden opgeslagen.

### Layout {#layout}

Wanneer u een sjabloon bewerkt, kunt u de lay-out definiëren, gebruikt dit de standaard responsieve lay-out. De indeling helpt bij het beheer van de breedte van een component op basis van apparaatbreedte om een responsief adaptief formulierontwerp mogelijk te maken.

![Lay-outcontainer in de structuurlaag](/help/forms/assets/layout-template-core-component.png)

Raadpleeg het artikel [responsieve lay-out](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/responsive-layout-feature-video-understand.html?lang=en) voor aanvullende informatie.

## De sjabloon inschakelen {#enabling-the-template}

Wanneer u een sjabloon maakt, wordt deze toegevoegd als concept. Schakel de sjabloon in om deze te gebruiken voor het maken van Adaptive Forms. Een sjabloon inschakelen:

1. Navigeren naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Templates]**en opent u de map waarin u de sjabloon hebt gemaakt.
De sjabloon die u hebt gemaakt, is gemarkeerd als Concept.
1. Selecteer de sjabloon en selecteer **[!UICONTROL Enable]** in de werkbalk.
Wanneer u een adaptief formulier maakt, wordt de sjabloon weergegeven wanneer u wordt gevraagd een sjabloon te kiezen.

## Een sjabloon importeren of exporteren {#importing-or-exporting-a-template}

Een formulier werkt met de sjabloon. Wanneer u een adaptief formulier downloadt dat is gemaakt met een aangepaste sjabloon, wordt de sjabloon niet gedownload. Wanneer u het formulier importeert op een ander formulier [!DNL AEM Forms] wordt geïmporteerd zonder de sjabloon. Als een formulier wordt geïmporteerd maar de sjabloon ervan niet beschikbaar is, wordt het formulier niet gegenereerd. U kunt de aangepaste sjabloon verpakken vanuit `/conf` node in `https://<server>:<port>/crx/packmgr`en deze in de [!DNL AEM Forms] -instantie waarin u het formulier wilt uploaden. U kunt [Een sjabloon maken met AEM Archetype en deze implementeren in uw Cloud Service-instantie](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/pages-templates.html#prerequisites).

>[!NOTE]
>
> * U kunt ook de [!UICONTROL Document of Record] rechtstreeks vanuit de editor voor adaptieve formulieren of de sjablooneditor voor adaptieve formulieren. Zie voor meer informatie [Document met record genereren voor adaptieve Forms](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform).

## Een formuliergegevensmodelschema koppelen aan een sjabloon {#associating-form-data-model-schema-in-template}

Auteurs kunnen een [!UICONTROL Form Data Model Schema] naar een sjabloon voor een adaptief formulier in de sjablooneditor. Auteurs kunnen een schema in de sjablooneditor selecteren. Wanneer u een schema aan een sjabloon koppelt en een auteur van een formulier een formulier maakt op basis van de sjabloon, wordt het schema vooraf geselecteerd voor het formulier. Hiermee kunnen auteurs van formulieren het gebruik van schema&#39;s reguleren en besparen ze ook tijd voor auteurs van formulieren. Een formuliergegevensmodelschema selecteren in een sjablooneditor:

1. Selecteren **[!UICONTROL Content Browser]** aan de linkerkant.
1. Ga naar de formuliercontainer **[!UICONTROL Setting]**.
1. Selecteren **[!UICONTROL Data Model]**.
1. Kies het formuliergegevensmodel (FDM) via **[!UICONTROL Select Form Data Model]** en sla de configuratie op.

![Form-Data-Model-Association-in-Forms](/help/forms/assets/select-form-data-model-img-core-component.png)

<!--

## Creating an Adaptive Form template with tabs and panels {#creating-an-adaptive-form-template-with-tabs-and-panels-nbs}

For example, you want to create a template with the following tabs:

* General Information
* Professional Information

You have added a logo, provided a title, and added a footer in the structure layer. Lock the header and footer to stop form authors from editing them when they use the template to create forms.

Change the layer from **Structure** to **Initial Content**, and start adding content to the form. To create a tabbed structure, add a child Panel in the guideRootPanel of the Adaptive Form container. To add a panel:

* You can add a panel by tapping the **[!UICONTROL +]** button when you select the **[!UICONTROL Drag components here]** option.

* You can drag-drop the panel component from the components browser in the sidebar.
* You can add child panel of the `guideRootPanel` from the component toolbar.

To create the General Information and Professional Information tabs, add two panels in the child panel of the `guideRootPanel`. Select the panels and select ![cmppr](assets/configure-icon.svg) to open the properties in the sidebar. Change the element names as `general-info` and `professional-info`, and titles as General Information and Professional Information respectively. In the sidebar, select content to open the content browser. In the Form Objects tab, select `guideRootPanel`. In the editor, the guideRootPanel is selected. Select ![cmppr](assets/configure-icon.svg) in the component toolbar to open its properties. In the Panel Layout field, select **[!UICONTROL Tabs on Top]** and select **[!UICONTROL Done]**. The tabbed template structure is applied.

### Adding content in tabs {#adding-content-in-tabs}

After you add panels and structure them as tabs, you can add fields inside the tabs. When you select a tab in the editor, you can see the **[!UICONTROL Drag components here]** option. You can drag-drop components such as text-boxes, list items, and buttons. You can drag-drop components from the components browser in the sidebar.

Each component has properties that enhance data capturing and manipulation. For example, you can enable the **[!UICONTROL Required field]** property of a component. Your authors can specify a message that your customers see when they skip filling a required field. Specify the message in **[!UICONTROL Required Field Message]** property.

In the example template, Name, Phone number, and Date of birth fields are added in the General Information tab. In the Professional Information tab, Currently employed, employment type, Educational qualification fields are added.

After you have added fields, you can add buttons such as Submit and Reset.
-->

### Aangepaste eigenschappen toevoegen aan Aangepaste formuliercomponenten met behulp van sjabloonbeleid

Met aangepaste eigenschappen kunt u aangepaste kenmerken (sleutelwaardeparen) aan een Adaptief kernonderdeel van een formulier koppelen met behulp van de formuliersjabloon. De aangepaste eigenschappen worden weergegeven in het dialoogvenster **[!UICONTROL properties]** sectie van de koploze vertoning van de component. Hiermee kunt u dynamisch formuliergedrag maken dat wordt aangepast op basis van de waarden van aangepaste kenmerken. Ontwikkelaars kunnen bijvoorbeeld verschillende uitvoeringen van een Forms-component zonder koptekst ontwerpen voor mobiele apparaten, desktops of webplatforms, waardoor de gebruikerservaring op een groot aantal apparaten aanzienlijk wordt verbeterd.

Aangepaste eigenschappen worden toegevoegd aan de kerndeelvelden van het Adaptief formulier:

1. [Een naam van een aangepaste groep toevoegen aan het beleid van een sjablooneditor](#add-a-custom-group-name)
1. [Een aangepaste groepsnaam selecteren in het dialoogvenster Bewerken van de component van een adaptief formulier](#select-a-custom-group-name)

#### Een aangepaste groepsnaam toevoegen aan het beleid van een sjablooneditor {#add-a-custom-group-name}

1. Ga naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Templates]**.
1. Selecteer de sjabloon op basis van kerncomponenten en open deze in de bewerkingsmodus.
1. Klik op de knop **[!UICONTROL Policy]** ![Beleid](/help/forms/assets/Smock_FeedManagement_18_N.svg) pictogram van een veld Adaptive Form Core Component waarvoor de aangepaste eigenschappen moeten worden gedefinieerd. De **[!UICONTROL Adaptive Form Field]** wordt weergegeven.
1. Selecteer de **[!UICONTROL Custom Properties]** tab.
1. Geef de **[!UICONTROL Policy Title]** onder de **[!UICONTROL Policy]** sectie.
1. Geef de **[!UICONTROL Group name]** en voeg sleutel-waarde paar toe verbonden aan een specifieke groep. De groepsnaam is zichtbaar voor formulierauteurs in het dialoogvenster Bewerken van een component. Als u de groepsnaam selecteert, is elk bijbehorend sleutel-waardepaar van toepassing op een component.
1. Klikken **[Gereed]**.

![Groepsnaam van aangepaste eigenschappen toevoegen in sjablooneditor](/help/forms/assets/custom-properties-core-component.png)

Wanneer u minstens één groep van het douanebezit gebruikend het malplaatjebeleid toevoegt, **[!UICONTROL Advanced]** wordt weergegeven in het dialoogvenster Bewerken van een corresponderende kerncomponent.

#### Een aangepaste groepsnaam selecteren in het dialoogvenster voor bewerken van een kerncomponent {#select-a-custom-group-name}

1. Open een adaptief formulier in de bewerkingsmodus.
1. Selecteer de component waarvoor de aangepaste eigenschappen in de sjablooneditor zijn gedefinieerd en selecteer ![settings_icon](assets/configure-icon.svg) om het dialoogvenster voor bewerken van de component te openen.
1. Selecteer de **[!UICONTROL Advanced]** tab.
1. Selecteer de naam van de aangepaste groep eigenschappen uit **[!UICONTROL Custom Property Select]** vervolgkeuzelijst. Alle gedefinieerde aangepaste groepnamen worden automatisch ingevuld in de vervolgkeuzelijst.
1. Selecteren **[!UICONTROL Done]** om de eigenschappen op te slaan.

![aangepaste naam groep eigenschappen selecteren](/help/forms/assets/select-custom-properties-group-name.png)

>[!NOTE]
>
> * De **[!UICONTROL Additional Custom Properties]** checkbox staat u toe om component-specifieke douaneeigenschappen naast die dynamisch toe te voegen die in het malplaatjebeleid worden verstrekt. Het douanebezit van de specifieke component neemt belangrijkheid over het douanebezit dat bij het malplaatjebeleid wordt geplaatst wanneer de waarden van de zeer belangrijke naam aanpassen.

## Een adaptief formulier maken met de sjabloon {#creating-an-adaptive-form-using-the-template}

Nadat u een sjabloon hebt gemaakt en ingeschakeld, is deze beschikbaar in Formulierbeheer wanneer u een adaptief formulier maakt. Als u een sjabloon wilt gebruiken en een adaptief formulier wilt maken, raadpleegt u [Een adaptief formulier maken op basis van kerncomponenten](/help/forms/creating-adaptive-form-core-components.md).
<!--
## Change display option of out of the box templates  {#change-display-option-of-out-of-the-box-templates}

You can create custom templates for Adaptive Forms to define basic structure and initial content. [!DNL AEM Forms] also provides a set of out of the box template for Adaptive Forms. You can choose to show or hide the templates.

Perform the following steps to show and hide templates:

1. Log in to [!DNL AEM Forms] author instance and navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.

   >[!NOTE]
   >
   >The URL of AEM web console is https://'[server]:[port]'/system/console/configMgr

1. Locate and open the **FormsManager Configuration** settings:

    * To show or hide out of the box Adaptive Forms template, check or uncheck the **Include Out of the box AF and AD Templates** option.
    * To show or hide out of the box Adaptive Form templates that were added in AEM 6.0 Forms or AEM 6.1 Forms releases but are now deprecated, check or uncheck the **Include AEM 6.0 AF Templates** option. If this option is checked, and you want it to take effect, it requires the **Include Out of the box AF and AD Templates** configuration to be enabled.

1. Click **Save**. The display options for the out of the box templates are changed. 

## Save an Adaptive Form as a template {#saving-adaptive-form-as-template}

You can also save an Adaptive Form as a template for future use. To save a Adaptive Form as a template:

1. Select an Adaptive Form to save it as a template.
1. Click **[!UICONTROL Save as Template]**. A dialog box appears.
1. Specify **[!UICONTROL Title]** (mandatory field), **[!UICONTROL Location]** (mandatory field) and **[!UICONTROL Description]** (optional field) for the template. 
1. Click **[!UICONTROL Create]**.

   ![Save as Form as Template](/help/forms/assets/saveformastemplate.png)



>[!NOTE]
>
>To use the same container policy as of the source Adaptive Form, it is recommended to save the template in the same folder as of the source Adaptive Form. In case, the template is saved in any other folder, than the created template uses a default container policy.
-->

## Aanbevolen procedures {#best-practices}

* Maak sjablonen met gebruik van de componenten die zijn gebaseerd op kerncomponenten, zoals Adaptieve formuliertekst, Adaptieve formuliercontainer en meer. Voor meer informatie over Adaptive Forms Core Components, [klik hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html).
* Beperk het aantal sjablonen zodat deze overeenkomen met de fundamenteel verschillende formuliertypen die op de websites beschikbaar zijn
* Verstrek de noodzakelijke flexibiliteit en configuratiemogelijkheden aan uw douanecomponenten die in een malplaatje worden gebruikt.

<!--
## See next

* [Create style or themes for your forms](using-themes-in-core-components.md)
* [Create an Adaptive Form (core components)](/help/forms/creating-adaptive-form-core-components.md)

-->

## Zie ook {#see-also}

{{see-also}}
* [Stijlen of thema&#39;s maken voor uw formulieren](using-themes-in-core-components.md)
* [Een adaptief formulier maken (kerncomponenten)](/help/forms/creating-adaptive-form-core-components.md)

