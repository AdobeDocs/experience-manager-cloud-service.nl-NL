---
title: Hoe te om Aangepast Forms of PDF forms op een instantie van AEM Forms in te voeren, uit te voeren en te organiseren?
description: Leer Adaptieve Forms, PDF forms, thema's en andere ondersteunende middelen migreren van en naar AEM instanties.
topic-tags: forms-manager
role: Admin, User
feature: Adaptive Forms
exl-id: f5105fb7-b8c0-4656-8095-b21d392746c0
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 0%

---

# Adaptieve Forms- en AEM Forms-middelen importeren of exporteren {#importing-and-exporting-assets-to-aem-forms}

U kunt Adaptive Forms en gerelateerde elementen, zoals Adaptive Form-thema&#39;s, Form Data Model (FDM), Adaptive Form-sjablonen, documentfragmenten en PDF forms verplaatsen tussen [!DNL AEM Forms] instanties. U kunt elementen importeren en exporteren in CRX-pakket of binaire bestandsindelingen.

Wanneer u een adaptief formulier exporteert, worden het inhoudsbeleid en de sjablonen niet geëxporteerd. Gebruiken [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#how-rolling-deployments-work) om dergelijke activa uit te voeren.

## Adaptieve Forms, PDF forms of verwante middelen downloaden {#download-forms-amp-documents-assets}

Formulieren of gerelateerde elementen downloaden:

1. Aanmelden bij uw [!DNL AEM Forms] -instantie.
1. Selecteren **[!UICONTROL Adobe Experience Manager]** ![adobeexperienceManager](assets/adobeexperiencemanager.png) pictogram > **[!UICONTROL Navigation]** ![kompas](assets/Smock_Compass_18_N.svg) pictogram > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteer de elementen en selecteer de **[!UICONTROL Download]** pictogram.
1. Kies in het (de) downloadmiddel(en) een van de volgende opties en selecteer **[!UICONTROL Download]**.

   * **Downloaden als CRX-pakket:** Gebruik de optie om alle geselecteerde elementen en gerelateerde afhankelijkheden te downloaden en verplaatsen vanuit een [!DNL AEM Forms] aan een andere instantie. Alle bestanden en mappen worden gedownload als een CRX-pakket, inclusief de formulieren die zijn geschreven in AEM (Adaptive Forms and Adaptive Form Fragments), formuliersets, formuliergegevensmodel (FDM), formuliersjablonen, PDF-documenten en bronnen waarnaar wordt verwezen (XSD&#39;s en afbeeldingen).
Het voordeel van het downloaden van elementen als een pakket is dat deze ook worden gedownload waarnaar wordt verwezen door geselecteerde elementen. Als u bijvoorbeeld een adaptief formulier hebt dat gebruikmaakt van een formuliersjabloon, XSD en een afbeelding. Wanneer u dit adaptieve formulier selecteert en het als een pakket downloadt, bevat het gedownloade pakket ook de formuliersjabloon, XSD en de afbeelding. Alle metagegevenseigenschappen (inclusief aangepaste eigenschappen) die aan het element zijn gekoppeld, worden ook gedownload.

   * **Elementen downloaden als binaire bestanden:** Gebruik de optie om alleen formuliersjablonen (XDP), PDF forms (PDF), documenten (PDF) en bronnen (afbeeldingen, schema&#39;s, opmaakmodellen) te downloaden. U kunt deze elementen bewerken met externe toepassingen. De elementen met binaire elementen, zoals afbeeldingen, PDF en andere ondersteunde indelingen, worden als ZIP-bestand gedownload.
U kunt geen adaptieve Forms, adaptieve formulierfragmenten, thema&#39;s en formuliersets downloaden met **[!UICONTROL Download assets as binary files]** -optie. Als u deze middelen wilt downloaden, kunt u het beste **[!UICONTROL Download as CRX Package]** -optie.

   De geselecteerde elementen worden gedownload als een archief (.zip-bestand).

   >[!NOTE]
   >
   >Zowel AEM pakket- als binaire bestanden worden gedownload als een archief (.zip-bestand). De sjablonen voor de elementen worden niet samen met de elementen gedownload. U moet de elementsjablonen afzonderlijk exporteren.

## Adaptieve Forms, PDF forms of verwante elementen uploaden {#upload-forms-amp-documents-assets}

U kunt de ondersteunde elementtypen afzonderlijk of als ZIP-archief uploaden. Voor een ZIP-bestand worden de relatieve paden van alle ondersteunde elementen weergegeven. Niet-ondersteunde elementen in het ZIP-bestand worden genegeerd en niet vermeld. Als het ZIP-archief echter alleen de niet-ondersteunde elementen bevat, wordt een foutbericht weergegeven in plaats van het pop-updialoogvenster.
Een formulier of een verwant element uploaden:

1. Aanmelden bij uw [!DNL AEM Forms] -instantie.
1. Selecteren **[!UICONTROL Adobe Experience Manager]** ![adobeexperienceManager](assets/adobeexperiencemanager.png) pictogram > **[!UICONTROL Navigation]** ![kompas](assets/Smock_Compass_18_N.svg) pictogram > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteren **[!UICONTROL Create]** > **[!UICONTROL File Upload]**. Er wordt een dialoogvenster weergegeven.
1. Blader in het dialoogvenster naar het pakket of het archief dat u wilt importeren en selecteer dit. U kunt ook andere ondersteunde bestandstypen selecteren. Selecteer **[!UICONTROL Open]**. De map of de bestandsnaam die u selecteert, mag geen speciale tekens bevatten.

   Controleer in het dialoogvenster de details van de elementen die worden geüpload en selecteer **[!UICONTROL Upload]**.

   Als u een bestaand formulierelement uploadt, wordt het element bijgewerkt.

   >[!NOTE]
   >
   > * Wanneer een naamconflict optreedt met verschillende typen bronnen, wordt de bestaande maphiërarchie niet vervangen door een pakket te uploaden. Als u bijvoorbeeld een adaptief formulier hebt met de naam &#39;Training&#39; op de locatie /content/dam/formsanddocuments op één server. U downloadt het adaptieve formulier en uploadt het formulier naar een andere server. De tweede server heeft ook een map met de naam &#39;Training&#39; op dezelfde locatie/content/dam/formsanddocuments. Het uploaden mislukt.
   > * Alleen een lid van de `form-power-user` kan XDP-bestanden uploaden.


## Een thema downloaden {#downloading-a-theme}

U kunt thema&#39;s exporteren in [!DNL AEM Forms] die u kunt gebruiken in andere projecten of instanties. Met AEM kunt u thema&#39;s downloaden als ZIP-bestand, dat u kunt uploaden bij de instantie.

Een thema downloaden:

1. Aanmelden bij uw [!DNL AEM Forms] -instantie.
1. Selecteren **[!UICONTROL Adobe Experience Manager]** ![adobeexperienceManager](assets/adobeexperiencemanager.png) pictogram > **[!UICONTROL Navigation]** ![kompas](assets/Smock_Compass_18_N.svg) pictogram > **[!UICONTROL Forms]** > **[!UICONTROL Themes]**.
1. Selecteer het thema en selecteer **[!UICONTROL Download]**. Het thema wordt gedownload als een archief (.zip-bestand).

## Een thema uploaden {#uploading-a-theme}

U kunt thema&#39;s die anderen in uw formulieren maken, uploaden en gebruiken. Een thema uploaden:

1. Navigeer in Experience Manager naar **[!UICONTROL Forms]** > **[!UICONTROL Themes]**.
1. Klik op de pagina Themes op **[!UICONTROL Create]** > **[!UICONTROL File Upload]**.
1. Blader in de vraag Bestand uploaden naar en selecteer een themapakket op uw computer en klik op **[!UICONTROL Upload]**. Het geüploade thema is beschikbaar op de themapagina.

<!-- ## Import and export assets in Correspondence Management {#import-and-export-assets-in-correspondence-management}

To share assets, such as data dictionaries, letters, and document fragments, between two different implementations of Correspondence Management, you can create and share .cmp files. A .cmp file can include one or more data dictionaries, letters, document fragments, and forms.

### Export Document Fragments, Letters, and/or Data Dictionaries {#export-document-fragments-letters-and-or-data-dictionaries}

1. In the letters, document fragments, or data dictionary pages, select and select the assets you want to export to a single package, and then select Queue For Download. The assets are lined-up for export.
1. As required, repeat the above step to add letters, document fragments, and data dictionaries.
1. Select **Download**.
1. Correspondence Management displays Download Asset(s) dialog with a list of assets in the export list.

   ![export](assets/export.png)

1. To view the dependencies that are exported, Select Resolve. Or skip to the next step. Even if you do not select resolve, the dependencies are still exported.
1. To download the .cmp file, select **OK**.
1. Correspondence Management downloads a .cmp file to your computer.

   The .cmp file includes the exported assets. You can share the .cmp file with others. Other users can import the .cmp file in a different server to get all the assets in the new server.

### Export all the Correspondence Management assets as a package {#export-all-the-correspondence-management-assets-as-a-package}

Use this option to download all the Correspondence Management assets and related dependencies as a package from an [!DNL AEM Forms] instance.

For example, if Correspondence Management has a letter that uses an image and text, the downloaded package also contains the image and the text related to the letter. All the metadata properties (including custom properties) associated with the asset are also downloaded. Once you have downloaded the package (.cmp), you can [import the package to a different [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

To download all the Correspondence Management assets and related dependencies as a package, complete the following steps:

1. Log in to [!DNL AEM Forms] server as a forms user.
1. Select **Adobe Experience Manager** in the Global Navigation bar.
1. Select tools ( ![tools](assets/tools.png)) and then select **Forms**.
1. Select **Export Correspondence Management Assets**.

   ![publish-cmp-assets-1](assets/publish-cmp-assets-1.png)

   ( ``The Export All Correspondence Management Assets page appears and displays the information about the last time the Export process was attempted and a link to download the last successfully exported package.

   ![export-last-run-details](assets/export-last-run-details.png)

1. Select **Export** and, in the confirm message, select **OK**.

   After a batch process is complete, the last run details and the link to download the package are updated. This includes information such as the Administrator login and if the batch run successfully or failed. The assets are exported to a package and the Download Exported Package link appears.

   >[!NOTE]
   >
   >The Export All Assets process cannot be canceled once initiated. Also, while the export all operation is in process, do not create, delete, modify, or publish any assets or initiate Publish All Assets process.a

1. Select the **Download Exported Package** link to download the package file.

   To add the assets in the package to another instance of Correspondence Management, [import the package to an [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

<!-- ### Import Document Fragments, Letters and/or Data Dictionaries into Correspondence Management {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

You can import assets that are exported into a .cmp file. A .cmp file can have one or more letters, data dictionaries, document fragments, and dependent assets.

>[!NOTE]
>
>While importing old Correspondence Management assets for migration, log in using an Admin account. For more information on Migrating old Correspondence Management assets, see [Migrate Correspondence Management assets to AEM 6.1 forms](migration-utility.md).

1. On the data dictionary, letters, or document fragments page, select **Create &gt; File Upload** and select the .cmp file.
1. Correspondence Management displays the Import Assets dialog with the list of assets that are imported. Select **Import**.

   After importing the assets, the following properties of the assets are updated while the other properties remain the same:

    * Author: Displays the ID of the user that imported the asset to the server
    * Modified: The time when the asset was imported to the server

   >[!NOTE]
   >
   >For you to be able to upload XDPs (as part of the cmp file or otherwise), you need to be a part of forms-power-users group. For access rights, contact the administrator. -->

## Een workflowtoepassing exporteren {#export-a-workflow-application}

Met pakketbeheer kunt u workflowtoepassingen exporteren. De procedure is als volgt:

1. Openen [!DNL AEM Forms] pakketbeheer. URL van pakketbeheer is `https://[server]:[port]/crx/packmgr`.
1. Klik op **[!UICONTROL Create Package]**. De **[!UICONTROL New Package]** wordt weergegeven.
1. Geef de naam, versie en groep voor het pakket op. Klik op **[!UICONTROL OK]**.
1. Klikken **[!UICONTROL Edit]** en opent u de **[!UICONTROL Filters]** tab. Klik op **[!UICONTROL Add Filter]**. Geef het pad van de workflowtoepassing op. Bijvoorbeeld /etc/fd/dashboard/startpoints/homemortgauge. Klik op **[!UICONTROL Add rule]**.

1. Open de **[!UICONTROL Advanced]** tab. Selecteren **[!UICONTROL Merge]** of **[!UICONTROL Overwrite]** in ACL Behandelend gebied. Klik op **[!UICONTROL Save]**.
1. Klikken **[!UICONTROL Build]** om het pakket te maken.

   Nadat het pakket is gemaakt, kunt u het pakket downloaden en naar de andere server importeren. De workflowtoepassing wordt weergegeven op de server waarop het pakket is geüpload.

   >[!NOTE]
   >
   >De workflowtoepassing werkt alleen naar behoren als u ook het bijbehorende adaptieve formulier- en workflowmodel exporteert met de werktoepassing.

## Mappen gebruiken om Adaptief Forms, PDF forms en gerelateerde elementen te ordenen  {#folders-and-organizing-assets}

U kunt mappen gebruiken om elementen te rangschikken en te ordenen. Door documenten en elementen in een map te ordenen, kunt u de bestanden groeperen voor eenvoudig beheer. U kunt een map selecteren en deze downloaden of verwijderen. Voer de volgende stappen uit om een map te maken:

### Een map maken {#create-a-folder}

1. Aanmelden bij uw [!DNL AEM Forms] -instantie.
1. Experience Manager selecteren ![adobeexperienceManager](assets/adobeexperiencemanager.png) pictogram > navigatie ![kompas](assets/Smock_Compass_18_N.svg) pictogram> **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteren **[!UICONTROL Create]** > **[!UICONTROL Folder]**.
1. Voer de volgende gegevens in:

   * **[!UICONTROL Title]**: Naam weergeven voor de map
   * **[!UICONTROL Name]**: *(Verplicht)* De knooppuntnaam waaronder u de map in de opslagplaats wilt opslaan

   >[!NOTE]
   >
   >Standaard wordt de waarde van het naamveld automatisch ingevuld vanaf de titel. De naam mag alleen alfanumerieke tekens bevatten of speciale tekens voor het koppelteken (-) en het onderstrepingsteken (_). Eventuele andere speciale tekens die in de titel worden ingevoerd, worden automatisch vervangen door een afbreekstreepje en u wordt gevraagd de nieuwe naam te bevestigen. U kunt doorgaan met de voorgestelde naam of deze verder bewerken.

1. Er wordt een nieuwe map met de door u gedefinieerde titel weergegeven op de huidige locatie in de lijst met elementen.

   Als een map met de opgegeven naam bestaat, mislukt het verzenden met een fout. U kunt het foutbericht weergeven door de muisaanwijzer op de fout te plaatsen ![aem6forms_error_alert](assets/Smock_Alert_18_N.svg) pictogram dat naast het naamveld wordt weergegeven.

   U kunt de gemaakte map selecteren om naar de map te gaan en elementen of mappen in de map te maken. Bovendien kunt u een map selecteren en ervoor kiezen deze in de wachtrij te plaatsen voor downloaden, te verwijderen of de naam ervan te bewerken.


<!-- ### Create copies of one or more assets or letters {#create-copies-of-one-or-more-assets-or-letters}

You can use an existing assets to quickly create an asset with similar properties, content, and inherited assets.

Complete the following steps to create copies of assets and letters:

1. On the relevant assets page, select one or more assets. The UI displays the Copy icon.
1. Select **[!UICONTROL Copy]**. The UI displays the **[!UICONTROL Paste]** icon. You can also choose to go/navigate inside a folder before you paste. Different folders can contain assets with same names. For more information on folders, see [Folders and organizing assets](#folders-and-organizing-assets).
1. Select **[!UICONTROL Paste]**. The **[!UICONTROL Paste]** dialog appears. The system auto generates names and titles to the new copies of assets/letters, but you can edit the titles and names of the assets/letters.

   If you are copying and pasting the assets/letters at the same place, a suffix "-CopyXX" gets added to the existing name of the asset/letter. If no title existed for the copied asset/letter, the auto generated title field remains blank.

1. If necessary, edit the Title and Name with which you want to save the copy of the asset/letter.
1. Select **[!UICONTROL Paste]**. New copies of the copied assets are created.

## Search {#search-forms}

You ca use the top bar **[A]** to search your content. When you search for assets, a side panel is displayed. You can also select ![assets-browser-content-only](assets/assets-browser-content-only.png) &gt; Filter **[B]** to invoke the side panel. Using the various filters in the side panel, you can narrow down your search. The side panel also lets you save your searches.

![search_topbar](assets/search_topbar.png)

**A.** Search **B.** Filter

![Side panel - Filters](assets/search_sidepanel.png)

Side panel - Filters

On the side panel, you can use the following to narrow down your search results:

* Search Directory
* Tags
* Search Criteria; for example, Modified Dates, Publish Status, LiveCopy Status.

The side panel also lets you save your search settings with names of your choice.

For more information and instructions on using search, filters, saved search, and side panel, see [Search](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html). -->

>[!MORELIKETHIS]
>
>* [Thema&#39;s gebruiken in Adaptief formulier Core-componenten](/help/forms/using-themes-in-core-components.md)
