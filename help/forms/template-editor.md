---
title: Hoe kunnen we een adaptieve formuliersjabloon maken?
description: Maak adaptieve formuliersjablonen om de basisstructuur en eerste inhoud te definiëren met de Sjablooneditor.
feature: Adaptive Forms, Foundation Components
exl-id: a882cba2-c621-4ff7-a972-c504641b5639
role: User, Developer, Admin
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '1994'
ht-degree: 0%

---

# Een adaptieve formuliersjabloon maken {#adaptive-form-templates}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/creating-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/template-editor.html) |
| AEM as a Cloud Service | Dit artikel |

Wanneer u een formulier ontwerpt, voegt u velden en componenten toe om de formulierstructuur, inhoud en handelingen in de editor te definiëren. U voegt velden en componenten toe in `guideRootPanel` van de formuliercontainer. Met de Sjablooneditor kunt u een sjabloon maken met een basisstructuur en eerste inhoud die auteurs kunnen gebruiken om formulieren te maken.

U wilt bijvoorbeeld dat alle formulierauteurs bepaalde tekstvakken, navigatieknoppen en een verzendknop in een inschrijvingsformulier hebben. U kunt een sjabloon maken met de componenten die auteurs kunnen gebruiken om een formulier te maken dat consistent is met andere inschrijvingsformulieren. Wanneer auteurs de sjabloon gebruiken om een adaptief formulier te maken, neemt het nieuwe formulier de structuur en componenten over die u in de sjabloon hebt opgegeven. Met de Sjablooneditor kunt u:

* Voeg kop- en voettekstcomponenten van een formulier toe aan de structuurlaag.
* Geef de initiële inhoud voor het formulier op.
* Geef een thema op, namelijk Handelingen verzenden.

U kunt [!DNL AEM Forms] pakket van de verwijzingsinhoud van [ het portaal van de Distributie van de Software downloaden en installeren ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) om verwijzingsthema&#39;s en malplaatjes in uw milieu in te voeren.

## Werken met sjablonen {#working-with-templates}

U kunt de sjablooneditor openen via het menu Gereedschappen door te navigeren naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Templates]** . Hier worden de sjablonen ingedeeld in mappen die zijn ingeschakeld voor bewerkbare sjablonen.

Experience Manager biedt een algemene map voor het organiseren van sjablonen. Deze optie is echter niet standaard ingeschakeld. U kunt de beheerder vragen de algemene map in te schakelen of een map voor sjablonen te maken. Voor meer informatie over hoe te om omslagen tot stand te brengen, zie {de Mappen van het 0} Malplaatje ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/templates.html#editing-templates-template-authors).[

### Een sjabloon maken {#create-template}

Nadat u een map hebt gemaakt, opent u de map en voert u de volgende stappen uit om een sjabloon te maken:

1. Selecteer **[!UICONTROL Create]** in de map die u hebt gemaakt.
1. Selecteer **[!UICONTROL Adaptive Form template]** in de sectie Sjabloontype kiezen en selecteer **[!UICONTROL Next]** .

1. Geef in de sectie Sjabloondetails een sjabloontitel op en selecteer **[!UICONTROL Create]** .
U kunt ook een beschrijving opgeven.

1. Selecteer **[!UICONTROL Done]** om terug te keren naar de console of selecteer **[!UICONTROL Open]** om de sjabloon te openen in de editor.

### UI voor sjablooneditor {#template-editor-ui}

Wanneer u een sjabloon opent voor bewerking, kunt u de volgende AEM Editor-componenten zien:

* **de toolbar van de Pagina**
Bevat de volgende opties:

   * **Knevel Zijpaneel**: Laat u sidebar tonen of verbergen.
   * **Informatie van de Pagina**: Laat u informatie zoals publiceren/unpublish tijd, duimnagels, cliënt-zijbibliotheken, paginabeleid, en cliënt-zijbibliotheek van het paginaontwerp specificeren.
     <!-- * **Emulator**: Lets you simulate and customize the look for different devices.-->
   * **de selecteur van de Wijze:** laat u de wijze veranderen.U kunt **[!UICONTROL Structure]** wijze, **[!UICONTROL Initial Content]**, **[!UICONTROL Layout Control]** wijze kiezen. In de structuurmodus kunt u de kop- en voettekst toevoegen en aanpassen. In de modus Initiële inhoud kunt u de inhoud van het formulier aanpassen.
   * **Voorproef:** laat u voorproef hoe het malplaatje kijkt wanneer u het publiceert. U kunt Laagkiezer en Voorvertoning gebruiken om de bewerkings- en voorvertoningsmodi in en uit te schakelen.
* **Sidebar:** verstrekt de Inhoud, Eigenschappen, Assets, en de browsers van Componenten.
* **de toolbar van de Component:** wanneer u een component selecteert, ziet u een toolbar die u de component laat aanpassen.
* **Pagina**: Het gebied waar u inhoud toevoegt om het malplaatje tot stand te brengen.

<!-- See [Introduction to authoring Adaptive Forms](introduction-forms-authoring.md) to understand the Touch UI editor. -->

### Een sjabloon bewerken {#editing-a-template}

Er wordt een adaptieve formuliersjabloon gemaakt op basis van twee lagen:

* Structuur
* Oorspronkelijke inhoud

De laagkiezer is beschikbaar naast de optie Voorvertoning in de rechterbovenhoek van het scherm.

### Structuur {#structure}

Wanneer u de structuurlaag selecteert in de Sjablooneditor, ziet u de lay-outcontainers boven en onder de container voor adaptieve formulieren. Auteurs kunnen deze lay-outcontainers voor kopbal en footer gebruiken. U kunt de kop- en voettekst toevoegen, bewerken of aanpassen. Sleep de component Adaptief koptekst van formulier naar de lay-outcontainer boven de container voor adaptieve formulieren om de sjabloonkoptekst aan te passen. Sleep de component Aangepaste formuliervoettekst naar de lay-outcontainer onder de container voor adaptieve formulieren om de sjabloonvoettekst aan te passen.

![ container van de Lay-out in de structuurlaag ](assets/header-layer-selector.png)

Lay-outcontainers in de structuurlaag

**A.** container van de Lay-out voor de component van de Kopbal **B.** container van de Lay-out voor de component van de Voettekst

Sleep de component Adaptief koptekst van formulier naar de lay-outcontainer boven de container voor adaptieve formulieren. Nadat u de component hebt toegevoegd, kunt u de eigenschappen ervan opgeven waarmee u een logo kunt toevoegen en de titel kunt opgeven.

Op dezelfde manier kunt u de copyrightinformatie en bedrijfsgegevens opgeven wanneer u de voettekstcomponent in de lay-outcontainer onder de container voor adaptieve formulieren sleept.

![ Kopbal en footer die in de laag van de Structuur wordt toegevoegd ](assets/header-and-footer.png)

Koptekst en voettekst toegevoegd aan de laag Structuur

#### Componenten in de structuurlaag vergrendelen/ontgrendelen {#locking-unlocking-components-in-the-structure-layer}

Wanneer u de sjabloon bewerkt terwijl de structuurlaag is geselecteerd, kunt u de kop- en voettekst van de sjabloon ontgrendelen. Als een component ontgrendeld is in de sjabloon, kunnen formulierauteurs de component bewerken in het adaptieve formulier waarin de sjabloon wordt gebruikt. Door een component te vergrendelen voorkomt u dat auteurs van formulieren deze bewerken in het adaptieve formulier. De optie Vergrendelen is beschikbaar op de werkbalk van de component.

U voegt bijvoorbeeld de koptekstcomponent in de sjabloon toe. Wanneer u de component selecteert, ziet u een vergrendelingsoptie op de werkbalk van de component. Koptekst bevat doorgaans een bedrijfsnaam en een logo en u wilt niet dat auteurs van formulieren het logo en de koptekst in een sjabloon wijzigen. In een adaptief formulier dat is gemaakt met de sjabloon met de koptekstcomponent vergrendeld, kunnen auteurs van formulieren het logo en de bedrijfsnaam niet wijzigen.

>[!NOTE]
>
>Het wordt niet aanbevolen de afbeelding of het logo in de koptekstcomponent afzonderlijk te vergrendelen of te ontgrendelen. U kunt de koptekstcomponent ontgrendelen.

### Oorspronkelijke inhoud {#initial-content}

Als de optie Begininhoud is geselecteerd, wordt de container van het adaptieve formulier van de sjabloon geopend als een adaptief formulier voor bewerking. Net als bij het ontwerpen van een adaptief formulier kunt u initiële instellingen opgeven, zoals een thema selecteren en Handelingen verzenden.

Formulierauteurs gebruiken het als basis om een formulier te maken. De structuur van de inhoudsstroom wordt opgegeven in de laag Begininhoud van de sjabloon. Om aan het uitgeven van aanvankelijke inhoud van het vormmalplaatje, vóór Voorproef in de paginagoolbar, uitgezochte ![ canvas-drop-down ](assets/canvas-drop-down.png) **>** **[!UICONTROL Initial Content]** te schakelen.


In de Eerste laag van de Inhoud, creeert u het Adaptieve malplaatje van de Vorm dat uw auteurs als basis gebruiken. Het ontwerpen van een sjabloon lijkt op het ontwerpen van een formulier. U gebruikt de opties in de zijbalk. Sidebar verstrekt inhoud, eigenschappen, activa, en componentenbrowsers.

<!-- See [Sidebar](introduction-forms-authoring.md#sidebar). -->

>[!NOTE]
>
>Wanneer u Inhoud opslaan of PDF opslaan selecteert als Verzendhandeling, kunt u het opslagpad opgeven. Als u een pad opgeeft in een sjabloon, hebben alle formulieren die ermee worden gemaakt hetzelfde pad. U kunt het juiste opslagpad opgeven of formulierauteurs de opslaglocatie laten bijwerken om te voorkomen dat gegevens in elk formulier op dezelfde locatie worden opgeslagen.

#### Een adaptieve formuliersjabloon maken met tabbladen en deelvensters {#creating-an-adaptive-form-template-with-tabs-and-panels-nbsp}

U wilt bijvoorbeeld een sjabloon maken met de volgende tabbladen:

* Algemene informatie
* Professionele informatie

U hebt een logo toegevoegd, een titel opgegeven en een voettekst toegevoegd aan de structuurlaag. Vergrendel de kop- en voettekst om te voorkomen dat auteurs van formulieren deze bewerken wanneer ze de sjabloon gebruiken om formulieren te maken.

Wijzig de laag van Structuur in Begininhoud en voeg inhoud toe aan het formulier. Als u een structuur met tabbladen wilt maken, voegt u een onderliggend deelvenster toe in het guideRootPanel van de container van het adaptieve formulier. Een deelvenster toevoegen:

* U kunt een deelvenster toevoegen door op de knop **[!UICONTROL +]** te tikken wanneer u de optie **[!UICONTROL Drag components here]** selecteert.

* U kunt de deelvenstercomponent slepen en neerzetten vanuit de deelvensterbrowser in de zijbalk.
* U kunt onderliggende deelvensters van de `guideRootPanel` toevoegen vanaf de componentwerkbalk.

Als u de tabbladen Algemene informatie en Professionele informatie wilt maken, voegt u twee deelvensters toe in het deelvenster Onderliggend item van het dialoogvenster `guideRootPanel` . Selecteer de panelen en selecteer ![ cmp ](assets/configure-icon.svg) om de eigenschappen in sidebar te openen. Wijzig de elementnamen als `general-info` en `professional-info` , en de titels als Algemene informatie en Professionele informatie. Selecteer in het zijpaneel de inhoud die u wilt openen in de inhoudbrowser. Selecteer op het tabblad Formulierobjecten de optie `guideRootPanel` . In de redacteur, wordt guideRootPanel geselecteerd. Selecteer ![ cmp ](assets/configure-icon.svg) in de componententoolbar om zijn eigenschappen te openen. Selecteer **[!UICONTROL Tabs on Top]** in het veld Indeling deelvenster en selecteer **[!UICONTROL Done]** . De sjabloonstructuur met tabs wordt toegepast.

#### Inhoud toevoegen op tabbladen {#adding-content-in-tabs}

Nadat u deelvensters hebt toegevoegd en deze hebt gestructureerd als tabbladen, kunt u velden toevoegen binnen de tabbladen. Wanneer u een tabblad selecteert in de editor, wordt de optie **[!UICONTROL Drag components here]** weergegeven. U kunt componenten zoals tekstvakken, lijstitems en knoppen slepen en neerzetten. U kunt componenten slepen-dalingscomponenten van componentenbrowser in sidebar.

Elke component bevat eigenschappen die het vastleggen en bewerken van gegevens verbeteren. U kunt bijvoorbeeld de eigenschap **[!UICONTROL Required field]** van een component inschakelen. Uw auteurs kunnen een bericht specificeren dat uw klanten zien wanneer zij het vullen van een vereist gebied overslaan. Geef het bericht op in de eigenschap **[!UICONTROL Required Field Message]** .

In de voorbeeldsjabloon worden de velden Naam, Telefoonnummer en Geboortedatum toegevoegd op het tabblad Algemene informatie. Op het tabblad Professionele informatie, momenteel gebruikt, worden het werkgelegenheidstype en de kwalificatievelden voor het onderwijs toegevoegd.

Nadat u velden hebt toegevoegd, kunt u knoppen toevoegen, zoals Verzenden en Herstellen.

### De sjabloon inschakelen {#enabling-the-template}

Wanneer u een sjabloon maakt, wordt deze toegevoegd als concept. Schakel de sjabloon in om deze te gebruiken voor het maken van Adaptive Forms. Een sjabloon inschakelen:

1. Navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Templates]** en open de map waarin u de sjabloon hebt gemaakt.

1. De sjabloon die u hebt gemaakt, is gemarkeerd als Concept.
1. Selecteer de sjabloon en selecteer **[!UICONTROL Enable]** op de werkbalk.
Wanneer u een adaptief formulier maakt, wordt de sjabloon weergegeven wanneer u wordt gevraagd een sjabloon te kiezen.

## Een sjabloon importeren of exporteren {#importing-or-exporting-a-template}

Een formulier werkt met de sjabloon. Wanneer u een adaptief formulier downloadt dat is gemaakt met een aangepaste sjabloon, wordt de sjabloon niet gedownload. Wanneer u het formulier in een ander [!DNL AEM Forms] -exemplaar importeert, wordt het zonder de sjabloon geïmporteerd. Als een formulier wordt geïmporteerd maar de sjabloon ervan niet beschikbaar is, wordt het formulier niet gegenereerd. U kunt de aangepaste sjabloon verpakken vanuit het knooppunt `/conf` in `https://<server>:<port>/crx/packmgr` en deze poort in het exemplaar [!DNL AEM Forms] plaatsen waar u het formulier wilt uploaden. U kunt [ een malplaatje ook creëren gebruikend AEM Archeype en het aan uw instantie van Cloud Servicen ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/pages-templates.html#prerequisites) opstellen.

>[!NOTE]
>
> * U kunt de sjabloon [!UICONTROL Document of Record] ook rechtstreeks configureren vanuit de editor voor adaptieve formulieren of de sjablooneditor voor adaptieve formulieren. Voor meer informatie, zie [ Document van Verslag voor Aanpassings Forms ](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform) produceren.


## Een formuliergegevensmodelschema koppelen aan een sjabloon {#associating-form-data-model-schema-in-template}

Auteurs kunnen een [!UICONTROL Form Data Model Schema] koppelen aan een sjabloon voor een adaptief formulier in de sjablooneditor. Auteurs kunnen een schema in de sjablooneditor selecteren. Wanneer u een schema aan een sjabloon koppelt en een auteur van een formulier een formulier maakt op basis van de sjabloon, wordt het schema vooraf geselecteerd voor het formulier. Hiermee kunnen auteurs van formulieren het gebruik van schema&#39;s reguleren en besparen ze ook tijd voor de auteur van formulieren. Een formuliergegevensmodelschema selecteren in een sjablooneditor:

1. Selecteer **[!UICONTROL Content Browser]** aan de linkerkant.
1. Ga naar de formuliercontainer **[!UICONTROL Setting]** .
1. Selecteer **[!UICONTROL Data Model]** .
1. Kies het formuliergegevensmodel via **[!UICONTROL Select Form Data Model]** en sla de configuratie op.

![ vorm-gegevens-model-vereniging-in-Forms ](/help/forms/assets/select-form-data-model-img.png)



## Een adaptief formulier maken met de sjabloon {#creating-an-adaptive-form-using-the-template}

Nadat u een sjabloon hebt gemaakt en ingeschakeld, is deze beschikbaar in Formulierbeheer wanneer u een adaptief formulier maakt. Om een malplaatje te gebruiken en een AanpassingsVorm tot stand te brengen, zie [ Creërend een AanpassingsVorm ](creating-adaptive-form.md).


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

1. Click **Save**. The display options for the out of the box templates are changed. -->

## Een adaptief formulier opslaan als sjabloon {#saving-adaptive-form-as-template}

U kunt een adaptief formulier ook opslaan als een sjabloon voor toekomstig gebruik. Een adaptief formulier opslaan als een sjabloon:

1. Selecteer een adaptief formulier om het als sjabloon op te slaan.
1. Klik op **[!UICONTROL Save as Template]**. Er wordt een dialoogvenster weergegeven.
1. Geef **[!UICONTROL Title]** (verplicht veld), **[!UICONTROL Location]** (verplicht veld) en **[!UICONTROL Description]** (optioneel veld) op voor de sjabloon.
1. Klik op **[!UICONTROL Create]**.

   ![ sparen als Vorm als Malplaatje ](/help/forms/assets/saveformastemplate.png)



>[!NOTE]
>
>Als u hetzelfde containerbeleid wilt gebruiken als bij het adaptieve bronformulier, wordt u aangeraden de sjabloon op te slaan in dezelfde map als bij het adaptieve bronformulier. Als de sjabloon in een andere map wordt opgeslagen, gebruikt de gemaakte sjabloon een standaardcontainerbeleid.

## Recommendations {#recommendations}

* Wanneer u eigenschappen van het formulier in de sjablooneditor wijzigt, gebruikt u de eigenschap BindReference niet.
* Als u een onderbrekingspunt wilt toevoegen, creeer het wanneer u een Adaptief malplaatje van de Vorm ontwerpt.
Voor meer informatie over breekpunten, zie [ Responsieve Lay-out ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/responsive-layout.html#authoring).


## Zie ook {#see-also}

{{see-also}}