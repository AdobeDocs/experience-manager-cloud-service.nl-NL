---
title: Hoe kan ik formulieren publiceren of verwijderen bij voorvertoningen of publicatie-exemplaren?
description: Leer het publiceren of het ongedaan maken van het publiceren van formulieren vanuit de AEM-auteursomgeving om instanties voor te vertonen of te publiceren. Of u uw formulieren nu test op een testomgeving of ze live implementeert voor eindgebruikers, AEM biedt gestroomlijnde tools om dit proces efficiënt te beheren.
Keywords: Manage publication, Forms Manage publication, AF Manage publication, Adaptive Forms Manage publication, Cloud Manage publication
feature: Adaptive Forms
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
role: User, Developer
level: Intermediate
exl-id: 6ade40f1-bad5-4f5e-aa0e-84b7c6a82e02
source-git-commit: dab2b94d1e456622f061741ba1b5192c9163c295
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 0%

---

# &#x200B; Publicatie beheren in Experience Manager Forms

Als Adobe Experience Manager (AEM) Forms-beheerder kunt u formulieren publiceren van uw auteur naar Experience Manager Forms. U kunt de publicatie van een formulier of map ook voor een latere datum of tijd plannen. Na publicatie kunnen gebruikers de formulieren openen en invullen.

In Experience Manager Forms kunt u een formulier op een van de volgende manieren publiceren:
* [ publiceer optie ](#publish-forms-using-the-publish-option)
* [Publicatie beheren, optie](#publish-forms-using-the-manage-publication-option)

## Onthouden

* Slechts kunnen de leden van de `forms-users` groep de **gebruiken leiden Publicatie** optie om de vormen te publiceren.
* De veranderingen die aan vormen of omslagen in Experience Manager Forms worden aangebracht verschijnen niet in **publiceren** instantie tot opnieuw gepubliceerd. Dit zorgt ervoor dat het werk-in-vooruitgang updates in **niet beschikbaar blijven publiceert** instantie. Slechts worden de veranderingen die uitdrukkelijk door een beheerder worden gepubliceerd weerspiegeld in **publiceren** instantie.

## Formulieren publiceren met de optie Publiceren

De **publiceer** optie laat u onmiddellijk een vorm publiceren. Om een Vorm van Experience Manager te publiceren gebruikend **publiceer** knoop op de toolbar. U kunt als volgt formulieren publiceren met de optie Publiceren:

1. Navigeer in de Experience Manager Forms-console naar de bovenliggende map en selecteer een formulier dat u wilt publiceren.
1. Klik **publiceren** optie van de toolbar, neem een blik bij alle verwijzingsactiva die met vorm zouden worden gepubliceerd.
1. Klik op **[!UICONTROL Publish]**.

   ![ publiceer en maak vorm ](/help/edge/docs/forms/assets/publish-form-option.png) ongedaan

   Zodra de vorm en zijn verwante activa met succes worden gepubliceerd, verschijnt de dialoog van het Succes van a ****.
1. Klik **dicht**.

   ![ de dialoog van het Succes ](/help/forms/assets/publish-success1.png)

### Publicatie van het formulier ongedaan maken

Na met succes het publiceren van de vorm gebruikend **publiceer** optie en zijn verwante activa, kunt u hen zelfs unpublish gebruikend de **[!UICONTROL Unpublish]** knoop beschikbaar op de toolbar. Het publiceren van het formulier ongedaan maken:

1. Als u de publicatie van het formulier en de bijbehorende elementen ongedaan wilt maken, selecteert u het formulier en klikt u op **[!UICONTROL Unpublish]** op de werkbalk

   Wanneer u de **[!UICONTROL Unpublish]** knoop klikt, verschijnt de **Unpublish dialoog van Activa**.
1. Klik op **[!UICONTROL Unpublish]** om het publicatieproces te starten

   ![ Unplish dialoog ](/help/forms/assets/unpublish-asset.png)

   Zodra de vorm en zijn verwante activa met succes unpublished zijn, verschijnt de dialoog van het Succes van a ****.
1. Klik **dicht**.

   ![ unpublish succesvol ](/help/forms/assets/unpublishing-start.png)

## Formulieren publiceren met de optie Publicatie beheren

Met Publicatie beheren kunt u inhoud publiceren naar of verwijderen uit het geselecteerde doel, inhoud vanuit de map `forms&documents` toevoegen aan de publicatielijst, verwijzingen selecteren voor publicatie en publiceren plannen naar een latere datum of tijd.  Om vormen te publiceren die **gebruiken leidt de optie van de Publicatie**:

1. Navigeer in de Experience Manager Forms-console naar de bovenliggende map en selecteer een formulier dat u wilt publiceren.
1. Klik op de optie **[!UICONTROL Manage Publication]** op de werkbalk.

   ![ beheer de optie van de Publicatie ](/help/forms/assets/manage-publication-option.png)

   **leidt Publicatie** UI verschijnt:

   ![ beheer publicatie ](/help/forms/assets/manage-publication.png)

   De volgende opties zijn beschikbaar in **leiden Publicatie** UI:

   * **Acties**

      * **publiceer**: Publiceer vormen aan de geselecteerde bestemming
      * **unpublish**: Unpublish vormen van de bestemming

   * **Doel**

      * **publiceer**: Publiceer vormen aan Experience Manager Forms (AEM) publiceer instantie.
      * **Voorproef**: Publiceer vormen aan de instantie van de Voorproef van Experience Manager Forms (AEM).

   * **Plannend**

      * **nu**: Publiceer onmiddellijk vormen
      * **later**: Publiceer vormen die op de **datum van de Activering** of tijd worden gebaseerd

1. Klik **daarna** om verder te gaan.
1. (Facultatief) in het **Gebied** lusje, gebruik [ voeg Inhoud ](#add-content) optie toe om meer inhoud voor het publiceren toe te voegen. U kunt bijvoorbeeld meer Forms- of Document met recordbestanden toevoegen.
   ![ werkingsgebied tabel ](/help/forms/assets/scope-tab.png)
1. Klik op **[!UICONTROL Publish]** om de formulieren en gerelateerde elementen te publiceren en het bericht verschijnt als een bericht dat is gelukt.
   ![ publiceer succesvol bericht ](/help/forms/assets/publish-successful.png)

### Inhoud toevoegen

Als u publiceert naar Experience Manager Forms, kunt u meer inhoud (formulieren) toevoegen aan de publicatielijst.
Meer formulieren toevoegen voor publicatie:

1. Klik **toevoegen Inhoud** knoop om meer inhoud toe te voegen.

   ![ voeg inhoud ](/help/forms/assets/add-content.png) toe

2. Selecteer de vorm van het **Uitgezochte 1} scherm van de Weg.**

   ![ voeg inhoud ](/help/forms/assets/add-assets.png) toe

   >[!NOTE]
   >
   > U kunt meer formulieren of mappen aan de lijst toevoegen vanuit de map `formsanddocuments` . U kunt echter geen formulieren uit meerdere mappen tegelijk toevoegen.

3. Selecteer het formulier en klik op **[!UICONTROL Published References]** om de referenties te configureren die u wilt publiceren voor een formulier.

   ![ gepubliceerde verwijzingen ](/help/forms/assets/published-references.png)

4. In het **Gepubliceerde de dialoogvakje van Verwijzingen**, uncheck de activa u van plan bent niet-te publiceren en te klikken **[!UICONTROL Done]**.
   ![ gepubliceerde verwijzingendialoog ](/help/forms/assets/published-references-dialog.png)

<!--
### Include Folder Settings
By default, publishing a folder to Experience Manager Forms publishes all the assets, subfolders, and their references. To filter the folder for publishing:

1. Click **[Include Folder Settings]** to filter the folder.

    ![Include folder](/help/forms/assets/include-folder.png)

    The **[UICONTROL Include Folder Settings]** dialog appears. 
    
    ![Include folder dialog](/help/forms/assets/include-folder-dialog.png)
    
    The **[UICONTROL Include Folder Settings]** includes following options:

    * **[!UICONTROL Include folder contents]** checkbox. 
        * If selected, all forms and assets in the chosen folder, its subfolders (including all forms and assets within them), and references are published.
        * If not selected, only the forms and assets in the selected folder are published, while subfolder forms and assets are not.

    * **[!UICONTROL Include only immediate folder contents]** checkbox
        Selecting the **[!UICONTROL Include folder contents]** checkbox enables the **[!UICONTROL Include only immediate folder contents]** checkbox for selection.

        * If you select both options, all the forms and assets of the selected folder, subfolders (empty), and references are published. The forms and assets of the subfolders are not published.
        * -->


### Een formulier later publiceren of de publicatie ervan ongedaan maken

Met de optie Later publiceren of publiceren kunt u niet alleen formulieren op een latere datum en tijd publiceren, maar kunt u ook een workflow configureren. De formulieren worden gepubliceerd of gepubliceerd nadat de workflow is voltooid.

Een formulier plannen voor publiceren of verwijderen:

1. Navigeer in de Experience Manager Forms-console naar de bovenliggende map en selecteer het formulier dat u wilt plannen voor publicatie.
1. Klik op de optie **[!UICONTROL Manage Publication]** op de werkbalk.

   ![ beheer publicatie ](/help/forms/assets/manage-publication.png)

1. Klik **publiceren** of **unpublish** van **[!UICONTROL Action]**.
1. Selecteer de locatie **[!UICONTROL Destination]** waar u de inhoud wilt publiceren of de publicatie ervan wilt opheffen.
   * **Voorproef**: Gebruik de **3} optie van de Voorproef {om aan een de voorproefmilieu van Experience Manager Forms te publiceren of unpublish.** De Experience Manager Forms-voorbeeldomgevingen worden gebruikt om formulieren te testen onder ontwikkelaars.
   * **publiceer**: Gebruik Experience Manager Forms **publiceren** optie om de vorm naar Experience Manager Forms te verzenden publiceert milieu nadat de vorm klaar is om in een productiemilieu te gebruiken.

1. Selecteer **[!UICONTROL Later]** van **Plannend**.

   ![ beheer Publicatie later ](/help/forms/assets/manage-publication-later.png)

1. Selecteer een **[!UICONTROL Activation date]** en geef de datum en tijd op.
1. Klik op **[!UICONTROL Next]** .
1. (Facultatief) in het **Reikwijdte** lusje, voeg inhoud toe gebruikend **[!UICONTROL Add Content]**.
   ![ beheer Publicatie toevoegen later inhoud ](/help/forms/assets/publish-later-add-content.png)
1. Klik op **[!UICONTROL Next]**.
1. In het **lusje van Werkschema&#39;s**, specificeer a **[!UICONTROL Workflow title]**.
1. Klik op **[!UICONTROL Publish Later]** .

   ![ beheer het werkschema van de Publicatie ](/help/forms/assets/manage-publication-workflows.png)

## Publicatiestatus bepalen

Er zijn meerdere manieren om de publicatiestatus te bepalen:

* Meld u aan bij de doelinstantie om de gepubliceerde formulieren en andere elementen te controleren (afhankelijk van de geplande datum of tijd).

* Gebruik de tijdlijnweergave om de publicatiestatus te bepalen.

* Gebruik het menu met pagina-informatie in de Adaptieve Forms-editor.
