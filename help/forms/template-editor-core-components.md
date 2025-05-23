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

Wanneer u een formulier ontwerpt, voegt u velden en componenten toe om de formulierstructuur, inhoud en handelingen in de editor te definiëren. U voegt velden en componenten toe in `guideRootPanel` van de formuliercontainer. Met de Sjablooneditor kunt u een sjabloon maken met een basisstructuur en eerste inhoud die auteurs kunnen gebruiken om formulieren te maken.

U wilt bijvoorbeeld dat alle formulierauteurs bepaalde tekstvakken, navigatieknoppen en een verzendknop in een inschrijvingsformulier hebben. U kunt een sjabloon maken met de componenten die auteurs kunnen gebruiken om een formulier te maken dat consistent is met andere inschrijvingsformulieren. Wanneer auteurs de sjabloon gebruiken om een adaptief formulier te maken, overerft het nieuwe formulier de structuur en de componenten die u in de sjabloon hebt opgegeven. Met de Sjablooneditor kunt u:

* Voeg kop- en voettekstcomponenten van een formulier toe aan de structuurlaag.
* Geef de initiële inhoud voor het formulier op.
* Geef een thema op, namelijk Handelingen verzenden.

<!--
You can download and install [!DNL AEM Forms] reference content package from [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) portal to import reference themes and templates to your environment.
-->

## Voorwaarde

**laat de Aangepaste Componenten van de Kern van Forms voor uw milieu** toe: Wanneer u een programma creeert, de Aangepaste Componenten van de Kern van Forms reeds toegelaten voor uw milieu. Als u een as a Cloud Service milieu hebt van de Vorm dat op [ wordt gebaseerd AEM Archetype 39 of vroeger ](https://github.com/adobe/aem-project-archetype), [ laat de Aangepaste Componenten van de Kern van Forms voor uw milieu ](enable-adaptive-forms-core-components.md) toe.

>[!NOTE]
>
> Bij het opstellen van het as a Cloud Service milieu van Forms dat op Archetype 45 wordt gebaseerd, worden de **Aangepaste Forms (de Component van de Kern)** malplaatjes en kern op component-gebaseerde thema&#39;s toegevoegd aan uw milieu.

## Werken met een sjabloon {#working-with-templates}

U kunt de sjablooneditor openen via het menu Gereedschappen door te navigeren naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Templates]** . Hier worden de sjablonen ingedeeld in mappen die zijn ingeschakeld voor bewerkbare sjablonen.

>[!NOTE]
>
> U kunt de op de kerncomponent gebaseerde bewerkbare sjablonen vinden in de kernmappen voor componenten.

Experience Manager biedt een algemene map voor het organiseren van sjablonen. Deze optie is echter niet standaard ingeschakeld. U kunt de beheerder vragen de algemene map in te schakelen of een map voor sjablonen te maken. Voor meer informatie over hoe te om omslagen tot stand te brengen, zie {de Mappen van het 0} Malplaatje [&#128279;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/templates.html?lang=nl-NL#editing-templates-template-authors).

## Een sjabloon maken {#create-template}

Nadat u een map hebt gemaakt, opent u de map en voert u de volgende stappen uit om een sjabloon te maken:

1. Selecteer **[!UICONTROL Create]** in de map die u hebt gemaakt.
1. Selecteer in de sectie **[!UICONTROL Pick a Template Type]** de optie **[!UICONTROL Adaptive Form (Core Component) template]** en selecteer **[!UICONTROL Next]** .

1. In de **[!UICONTROL Template Details]** sectie, verstrek a **Titel van het Malplaatje** en selecteer **[!UICONTROL Create]**.
U kunt ook een beschrijving opgeven.

1. Selecteer **[!UICONTROL Done]** om terug te keren naar de console of selecteer **[!UICONTROL Open]** om de sjabloon te openen in de editor.

## UI voor sjablooneditor {#template-editor-ui}

Wanneer u een sjabloon opent voor bewerking, kunt u de volgende AEM Editor-componenten zien:

* **de toolbar van de Pagina**
Bevat de volgende opties:

   * **Knevel Zijpaneel**: Laat u sidebar tonen of verbergen.
   * **Informatie van de Pagina**: Laat u informatie zoals publiceren/unpublish tijd, duimnagels, cliënt-zijbibliotheken, paginabeleid, en cliënt-zijbibliotheek van het paginaontwerp specificeren.
     <!-- * **Emulator**: Lets you simulate and customize the look for different devices.-->
   * **selecteur van de Wijze:** laat u de wijze veranderen. U kunt de modus **[!UICONTROL Structure]** , **[!UICONTROL Initial Content]** en **[!UICONTROL Layout Control]** kiezen. In de structuurmodus kunt u de kop- en voettekst toevoegen en aanpassen. In de modus Initiële inhoud kunt u de inhoud van het formulier aanpassen.
   * **Voorproef:** laat u voorproef hoe het malplaatje kijkt wanneer u het publiceert. U kunt Laagkiezer en Voorvertoning gebruiken om de bewerkings- en voorvertoningsmodi in en uit te schakelen.
* **Sidebar:** verstrekt de Inhoud, Eigenschappen, Assets, en de browsers van Componenten.
* **de toolbar van de Component:** wanneer u een component selecteert, ziet u een toolbar die u de component laat aanpassen.
* **Pagina**: Het gebied waar u inhoud toevoegt om het malplaatje tot stand te brengen.

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


![ container van de Lay-out in de structuurlaag ](/help/forms/assets/header-layer-selector-core-component.png)

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

Formulierauteurs gebruiken het als basis om een formulier te maken. De structuur van de inhoudsstroom wordt opgegeven in de laag Begininhoud van de sjabloon. Om aan het uitgeven van aanvankelijke inhoud van het vormmalplaatje, vóór Voorproef in de paginagoolbar, uitgezochte ![ canvas-drop-down ](assets/canvas-drop-down.png) **>** **[!UICONTROL Initial Content]** te schakelen.

![ Kopbal en footer die in de Aanvankelijke laag van de Inhoud wordt toegevoegd ](assets/header-and-footer.png)

In de Eerste laag van de Inhoud, creeert u het Adaptieve malplaatje van de Vorm dat uw auteurs als basis gebruiken. Het ontwerpen van een sjabloon lijkt op het ontwerpen van een formulier. U gebruikt de opties in de zijbalk. Sidebar verstrekt inhoud, eigenschappen, activa, en componentenbrowsers.

<!-- See [Sidebar](introduction-forms-authoring.md#sidebar). -->

>[!NOTE]
>
>Wanneer u Inhoud opslaan of PDF opslaan selecteert als Verzendhandeling, kunt u het opslagpad opgeven. Als u een pad opgeeft in een sjabloon, hebben alle formulieren die ermee worden gemaakt hetzelfde pad. U kunt het juiste opslagpad opgeven of formulierauteurs de opslaglocatie laten bijwerken om te voorkomen dat gegevens in elk formulier op dezelfde locatie worden opgeslagen.

### Layout {#layout}

Wanneer u een sjabloon bewerkt, kunt u de lay-out definiëren, gebruikt dit de standaard responsieve lay-out. De indeling helpt bij het beheer van de breedte van een component op basis van apparaatbreedte om een responsief adaptief formulierontwerp mogelijk te maken.

![ container van de Lay-out in de structuurlaag ](/help/forms/assets/layout-template-core-component.png)

Verwijs naar het artikel [ begrip responsieve lay-out ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/responsive-layout-feature-video-understand.html?lang=nl-NL) voor extra informatie.

## De sjabloon inschakelen {#enabling-the-template}

Wanneer u een sjabloon maakt, wordt deze toegevoegd als concept. Schakel de sjabloon in om deze te gebruiken voor het maken van Adaptive Forms. Een sjabloon inschakelen:

1. Navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Templates]** en open de map waarin u de sjabloon hebt gemaakt.
De sjabloon die u hebt gemaakt, is gemarkeerd als Concept.
1. Selecteer de sjabloon en selecteer **[!UICONTROL Enable]** op de werkbalk.
Wanneer u een adaptief formulier maakt, wordt de sjabloon weergegeven wanneer u wordt gevraagd een sjabloon te kiezen.

## Een sjabloon importeren of exporteren {#importing-or-exporting-a-template}

Een formulier werkt met de sjabloon. Wanneer u een adaptief formulier downloadt dat is gemaakt met een aangepaste sjabloon, wordt de sjabloon niet gedownload. Wanneer u het formulier in een ander [!DNL AEM Forms] -exemplaar importeert, wordt het zonder de sjabloon geïmporteerd. Als een formulier wordt geïmporteerd maar de sjabloon ervan niet beschikbaar is, wordt het formulier niet gegenereerd. U kunt de aangepaste sjabloon verpakken vanuit het knooppunt `/conf` in `https://<server>:<port>/crx/packmgr` en deze poort in het exemplaar [!DNL AEM Forms] plaatsen waar u het formulier wilt uploaden. U kunt [ een malplaatje ook creëren gebruikend AEM Archetype en het opstellen aan uw instantie van Cloud Servicen ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/pages-templates.html?lang=nl-NL#prerequisites).

>[!NOTE]
>
> * U kunt de sjabloon [!UICONTROL Document of Record] ook rechtstreeks configureren vanuit de editor voor adaptieve formulieren of de sjablooneditor voor adaptieve formulieren. Voor meer informatie, zie [ Document van Verslag voor Aanpassings Forms ](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform) produceren.

## Een formuliergegevensmodelschema koppelen aan een sjabloon {#associating-form-data-model-schema-in-template}

Auteurs kunnen een [!UICONTROL Form Data Model Schema] koppelen aan een sjabloon voor een adaptief formulier in de sjablooneditor. Auteurs kunnen een schema in de sjablooneditor selecteren. Wanneer u een schema aan een sjabloon koppelt en een auteur van een formulier een formulier maakt op basis van de sjabloon, wordt het schema vooraf geselecteerd voor het formulier. Hiermee kunnen auteurs van formulieren het gebruik van schema&#39;s reguleren en besparen ze ook tijd voor auteurs van formulieren. Een formuliergegevensmodelschema selecteren in een sjablooneditor:

1. Selecteer **[!UICONTROL Content Browser]** aan de linkerkant.
1. Ga naar de formuliercontainer **[!UICONTROL Setting]** .
1. Selecteer **[!UICONTROL Data Model]** .
1. Kies het formuliergegevensmodel (FDM) tot en met **[!UICONTROL Select Form Data Model]** en sla de configuratie op.

![ vorm-gegevens-model-vereniging-in-Forms ](/help/forms/assets/select-form-data-model-img-core-component.png)

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

Met aangepaste eigenschappen kunt u aangepaste kenmerken (sleutelwaardeparen) aan een Adaptief kernonderdeel van een formulier koppelen met behulp van de formuliersjabloon. De aangepaste eigenschappen worden weergegeven in de sectie **[!UICONTROL properties]** van de koploze uitvoering van de component. Hiermee kunt u dynamisch formuliergedrag maken dat wordt aangepast op basis van de waarden van aangepaste kenmerken. Ontwikkelaars kunnen bijvoorbeeld verschillende uitvoeringen van een Forms-component zonder koptekst ontwerpen voor mobiele apparaten, desktops of webplatforms, waardoor de gebruikerservaring op een groot aantal apparaten aanzienlijk wordt verbeterd.

Aangepaste eigenschappen worden toegevoegd aan de kerndeelvelden van het Adaptief formulier:

1. [Een naam van een aangepaste groep toevoegen aan het beleid van een sjablooneditor](#add-a-custom-group-name)
1. [ selecteer een naam van de douanegroep in uitgeeft dialoog van de component van een AanpassingsVorm ](#select-a-custom-group-name)

#### Een aangepaste groepsnaam toevoegen aan het beleid van een sjablooneditor {#add-a-custom-group-name}

1. Ga naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Templates]** .
1. Selecteer de sjabloon op basis van kerncomponenten en open deze in de bewerkingsmodus.
1. Klik het **[!UICONTROL Policy]** ![ 2&rbrace; pictogram van het Beleid &lbrace;van een Adaptief gebied van de Component van de Kern van de Vorm waarop de douaneeigenschappen moeten worden bepaald. ](/help/forms/assets/Smock_FeedManagement_18_N.svg) Het dialoogvenster **[!UICONTROL Adaptive Form Field]** wordt weergegeven.
1. Selecteer de tab **[!UICONTROL Custom Properties]** .
1. Geef de waarde **[!UICONTROL Policy Title]** op onder de sectie **[!UICONTROL Policy]** .
1. Geef het **[!UICONTROL Group name]** op en voeg sleutelwaardepaar toe dat aan een specifieke groep is gekoppeld. De groepsnaam is zichtbaar voor formulierauteurs in het dialoogvenster Bewerken van een component. Als u de groepsnaam selecteert, is elk bijbehorend sleutel-waardepaar van toepassing op een component.
1. Klik **[Gedaan]**.

![ Toevoegend de naam van de groep van douaneeigenschappen in malplaatjeredacteur ](/help/forms/assets/custom-properties-core-component.png)

Wanneer u ten minste één aangepaste groep eigenschappen toevoegt met behulp van het sjabloonbeleid, wordt het tabblad **[!UICONTROL Advanced]** weergegeven in het dialoogvenster Bewerken van een corresponderende kerncomponent.

#### Een aangepaste groepsnaam selecteren in het dialoogvenster voor bewerken van een kerncomponent {#select-a-custom-group-name}

1. Open een adaptief formulier in de bewerkingsmodus.
1. Selecteer de component waarvoor de douaneeigenschappen in de malplaatjeredacteur zijn bepaald en uitgezocht ![ settings_icon ](assets/configure-icon.svg) om de Edit dialoog van de component te openen.
1. Selecteer de tab **[!UICONTROL Advanced]** .
1. Selecteer de naam van de aangepaste groep eigenschappen in de vervolgkeuzelijst **[!UICONTROL Custom Property Select]** . Alle gedefinieerde aangepaste groepnamen worden automatisch ingevuld in de vervolgkeuzelijst.
1. Selecteer **[!UICONTROL Done]** om de eigenschappen op te slaan.

![ uitgezochte naam van de groep van het douanebezit ](/help/forms/assets/select-custom-properties-group-name.png)

>[!NOTE]
>
> * Met het selectievakje **[!UICONTROL Additional Custom Properties]** kunt u op dynamische wijze componentspecifieke aangepaste eigenschappen toevoegen, naast de eigenschappen die in het sjabloonbeleid worden geboden. Het douanebezit van de specifieke component neemt belangrijkheid over het douanebezit dat bij het malplaatjebeleid wordt geplaatst wanneer de waarden van de zeer belangrijke naam aanpassen.

## Een adaptief formulier maken met de sjabloon {#creating-an-adaptive-form-using-the-template}

Nadat u een sjabloon hebt gemaakt en ingeschakeld, is deze beschikbaar in Formulierbeheer wanneer u een adaptief formulier maakt. Om een malplaatje te gebruiken en een AanpassingsVorm tot stand te brengen, zie [ Creërend een AanpassingsVorm die op de Componenten van de Kern ](/help/forms/creating-adaptive-form-core-components.md) wordt gebaseerd.
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

* Maak sjablonen met gebruik van de componenten die zijn gebaseerd op kerncomponenten, zoals Adaptieve formuliertekst, Adaptieve formuliercontainer en meer. Om informatie over de AanpassingsComponenten van de Kern van Forms te krijgen, [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL).
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

