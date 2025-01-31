---
title: Hoe kan ik formulieren publiceren of verwijderen bij voorvertoningen of publicatie-exemplaren?
description: Leer het publiceren of het unpublishing van het AEM auteursmilieu aan voorproef of publiceer instanties. Of u uw formulieren nu test op een testomgeving of ze live implementeert voor eindgebruikers, AEM beschikt over gestroomlijnde tools om dit proces efficiënt te beheren.
Keywords: Manage publication, Forms Manage publication, AF Manage publication, Adaptive Forms Manage publication, Cloud Manage publication
feature: Adaptive Forms
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
role: User, Developer
level: Intermediate
source-git-commit: d3c089dcca80255f53c0888d46ee1b4b6246741e
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 0%

---


# &#x200B; Publicatie beheren in Experience Manager Forms

Als Adobe Experience Manager Forms-beheerder kunt u formulieren publiceren van uw auteur naar Experience Manager Forms. U kunt plannen om een formulier of map op een latere datum of tijd te publiceren. Na publicatie kunnen gebruikers de formulieren openen en invullen.

In de Experience Manager Forms-interface kunt u een formulier publiceren met:
* [ optie van Publish ](#publish-forms-using-the-publish-option)
* [Publicatie beheren, optie](#publish-forms-using-the-manage-publication-option)

Als u verdere wijzigingen in de originele vormen of de omslag in Experience Manager Forms aanbrengt, worden de veranderingen niet weerspiegeld in de **instantie van Publish** tot u van Experience Manager Forms opnieuw publiceert. Het zorgt ervoor dat het werk-in-vooruitgang veranderingen niet beschikbaar in de **instantie van Publish** zijn. Slechts zijn de veranderingen die door een beheerder worden gepubliceerd beschikbaar in **Publish** instantie.

## Publish-formulieren met de optie Publish

De **optie van Publish** laat u onmiddellijk een vorm publiceren. Om een Vorm van de Experience Manager te publiceren gebruikend de **Publish** knoop op de toolbar. U kunt als volgt formulieren publiceren met de optie Publish:

1. Navigeer in de Experience Manager Forms-console naar de bovenliggende map en selecteer een formulier dat u wilt publiceren.
1. Klik **Publish** optie van de toolbar, neem een blik bij alle verwijzingsactiva die met vorm zouden worden gepubliceerd.
1. Klik op **[!UICONTROL Publish]**.

   ![ Publish en unpublish vorm ](/help/edge/docs/forms/assets/publish-form-option.png)

   Zodra de vorm en zijn verwante activa met succes worden gepubliceerd, verschijnt de dialoog van het Succes van a ****. Klik **dicht** om de dialoogdoos te sluiten.

   ![ de dialoog van het Succes ](/help/forms/assets/publish-success.png)

### Publicatie van het formulier ongedaan maken

Na met succes het publiceren van de vorm gebruikend de **optie van Publish** en zijn verwante activa, kunt u hen zelfs unpublish gebruikend de **[!UICONTROL Unpublish]** knoop op de toolbar. Het publiceren van het formulier ongedaan maken:

1. Als u de publicatie van het formulier en de bijbehorende elementen ongedaan wilt maken, selecteert u het formulier en klikt u op **[!UICONTROL Unpublish]** op de werkbalk

   Wanneer u de **[!UICONTROL Unpublish]** knoop klikt, verschijnt de **Unpublish dialoog van Activa**.
1. Klik op **[!UICONTROL Unpublish]** om het publicatieproces te starten

   ![ Unplish dialoog ](/help/forms/assets/unpublish-asset.png)

   Zodra de vorm en zijn verwante activa met succes unpublished zijn, verschijnt de dialoog van het Succes van a ****. Klik **dicht** om de dialoogdoos te sluiten.

   ![ unpublish succesvol ](/help/forms/assets/unpublishing-start.png)

## Publish-formulieren met de optie Publicatie beheren

Met Publicatie beheren kunt u inhoud publiceren of de publicatie van en naar het geselecteerde doel ongedaan maken, inhoud vanuit de map Formulieren en documenten aan de publicatielijst toevoegen, referenties selecteren om te publiceren en de publicatie naar een latere datum of tijd plannen.  U kunt als volgt formulieren publiceren met de optie Publicatie beheren:

1. Navigeer in de Experience Manager Forms-console naar de bovenliggende map en selecteer een formulier dat u wilt publiceren.
1. Klik op de optie **[!UICONTROL Manage Publication]** op de werkbalk.

   ![ beheer de optie van de Publicatie ](/help/forms/assets/manage-publication-option.png)

   De **beheert 1} interface van de Publicatie {verschijnt:**

   ![ beheer publicatie ](/help/forms/assets/manage-publication.png)

   De volgende opties zijn beschikbaar in **leiden Publicatie** interface:

   * **Acties**

      * **Publish**: De vormen van Publish aan de geselecteerde bestemming
      * **unpublish**: Unpublish vormen van de bestemming

   * **Doel**

      * **Publish**: De vormen van Publish aan de instantie van Experience Manager Forms (AEM) Publish.
      * **Voorproef**: De vormen van Publish aan (AEM) voorproefinstantie van Experience Manager Forms.

   * **Plannend**

      * **nu**: De vormen van Publish onmiddellijk
      * **later**: De vormen van Publish die op de **datum van de Activering** of tijd worden gebaseerd

1. Klik **daarna** om verder te gaan.
1. In het **lusje van het Bereik**, gebruik [ voeg Inhoud ](#add-content) optie toe om meer inhoud voor het publiceren toe te voegen. U kunt bijvoorbeeld meer Forms- of Document met recordbestanden toevoegen.
   ![ werkingsgebied tabel ](/help/forms/assets/scope-tab.png)
1. Klik op **[!UICONTROL Publish]** om de formulieren en gerelateerde elementen te publiceren en het bericht verschijnt als een bericht dat is gelukt.
   ![ publiceer succesvol bericht ](/help/forms/assets/publish-successful.png)

### Inhoud toevoegen

Als u publiceert naar Experience Manager Forms, kunt u meer inhoud (formulieren en mappen) toevoegen aan de publicatielijst. U kunt meer formulieren of mappen aan de lijst toevoegen vanuit de map `formsanddocuments` . U kunt echter geen formulieren uit meerdere mappen tegelijk toevoegen. Meer formulieren toevoegen voor publicatie:

1. Klik **toevoegen Inhoud** knoop om meer inhoud toe te voegen.

   ![ voeg inhoud ](/help/forms/assets/add-content.png) toe

1. Selecteer de vorm van het **Uitgezochte 1} scherm van de Weg.** U kunt meerdere formulieren uit een map toevoegen of meerdere mappen tegelijk toevoegen. U kunt echter geen formulieren uit meerdere mappen tegelijk toevoegen.

   ![ voeg inhoud ](/help/forms/assets/add-assets.png) toe

1. Selecteer het formulier en klik op **[!UICONTROL Published References]** om de referenties te configureren die u wilt publiceren voor een formulier.

   ![ gepubliceerde verwijzingen ](/help/forms/assets/published-references.png)

1. In het **Gepubliceerde de dialoogvakje van Verwijzingen**, uncheck de activa u van plan bent niet-te publiceren en te klikken **[!UICONTROL Done]**.
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


### Publish of publiceer het formulier later

Met de optie Later publiceren of publiceren kunt u niet alleen formulieren op een latere datum en tijd publiceren, maar kunt u ook een workflow configureren. De formulieren worden gepubliceerd of gepubliceerd nadat de workflow is voltooid. Een formulier plannen voor publiceren of verwijderen:

1. Navigeer in de Experience Manager Forms-console naar de bovenliggende map en selecteer het formulier dat u wilt plannen voor publicatie.
1. Klik op de optie **[!UICONTROL Manage Publication]** op de werkbalk.

   ![ beheer publicatie ](/help/forms/assets/manage-publication.png)

1. Klik **Publish** of **unpublish** van **[!UICONTROL Action]**, en selecteer dan **[!UICONTROL Destination]** waar u de inhoud wilt publiceren of unpublish.
   * **Voorproef**: Gebruik de **3} optie van de Voorproef {om aan een de voorproefmilieu van Experience Manager Forms te publiceren of unpublish.** De Experience Manager Forms-voorbeeldomgevingen worden gebruikt om formulieren te testen onder ontwikkelaars.
   * **Publish**: Gebruik de optie van Publish van Experience Manager Forms om de vorm naar Experience Manager Forms te verzenden publiceert milieu nadat de vorm aan gebruik in een productiemilieu klaar is.

1. Selecteer **[!UICONTROL Later]** uit planning.

   ![ beheer Publicatie later ](/help/forms/assets/manage-publication-later.png)

1. Selecteer een **[!UICONTROL Activation date]** en geef de datum en tijd op.
1. Klik op **[!UICONTROL Next]** .
1. In het **lusje 0} van het Toepassingsgebied **[!UICONTROL Add Content]**(indien nodig).**
   ![ beheer Publicatie toevoegen later inhoud ](/help/forms/assets/publish-later-add-content.png)
1. Klik op **[!UICONTROL Next]**.
1. (Facultatief) in de **Werkschema&#39;s** tabel, specificeer a **[!UICONTROL Workflow title]**.
1. Klik op **[!UICONTROL Publish Later]** .

   ![ beheer het werkschema van de Publicatie ](/help/forms/assets/manage-publication-workflows.png)

## Publicatiestatus bepalen

Er zijn meerdere manieren om de publicatiestatus te bepalen:

* Meld u aan bij de doelinstantie om de gepubliceerde formulieren en andere elementen te controleren (afhankelijk van de geplande datum of tijd).

* Gebruik de tijdlijnweergave om de publicatiestatus te bepalen.

* Gebruik het menu met pagina-informatie in de Adaptieve Forms-editor.
