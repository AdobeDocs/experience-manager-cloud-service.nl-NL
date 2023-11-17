---
title: Elementen importeren en exporteren naar [!DNL AEM Forms]?
description: Leer hoe u DocuSign met een adaptief formulier kunt gebruiken om e-handtekeningen te verzamelen.
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 0%

---


# Elementen importeren en exporteren {#importing-and-exporting-assets-to-aem-forms}

U kunt formulieren, thema&#39;s, sjablonen, documentfragmenten, thema&#39;s en andere elementen verplaatsen tussen verschillende [!DNL AEM Forms] instanties. Een dergelijke verplaatsing is vereist wanneer u systemen migreert of formulieren verplaatst van een ontwikkelings- of staging-server naar een productieserver.

Voor de activa waarvoor uploaden en importeren via de [!DNL AEM Forms] UI wordt gesteund, is het gebruiken van de UI van Forms de geadviseerde manier voor uitvoer of invoer. Het wordt niet aanbevolen om AEM pakketbeheer te gebruiken voor het exporteren of importeren van dergelijke elementen.

## Forms- en documentmiddelen downloaden of uploaden {#download-or-upload-forms-amp-documents-assets}

[!DNL AEM Forms] Met de gebruikersinterface kunt u elementen van een AEM-instantie exporteren door deze te downloaden als een AEM CRX-pakket of binaire bestanden. U kunt het gedownloade AEM CRX-pakket of het binaire bestand vervolgens importeren in een andere AEM.

Exporteren en importeren via [!DNL AEM Forms] De gebruikersinterface wordt ondersteund voor alle elementen, met uitzondering van sjablonen voor adaptieve formulieren en beleid voor adaptieve formulierinhoud. Bij het exporteren van een adaptief formulier uit [!DNL AEM Forms] UI, worden de gerelateerde adaptieve formuliersjabloon en het inhoudsbeleid niet automatisch geëxporteerd als andere gerelateerde elementen.

Voor deze elementtypen moet u AEM Package Manager gebruiken om een CRX-pakket te maken op de bron- AEM server en het pakket op de doelserver te installeren. Zie voor informatie over het maken en installeren van pakketten [Distribueren naar AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html).

### Forms- en Documenten downloaden {#download-forms-amp-documents-assets}

Forms en Documenten downloaden:

1. Aanmelden bij de [!DNL AEM Forms] -instantie.
1. Tikken, Experience Manager ![adobeexperienceManager](assets/adobeexperiencemanager.png) pictogram > navigatie ![kompas](assets/Smock_Compass_18_N.svg) pictogram> **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteer de formulierelementen en tik op de **[!UICONTROL Download]** pictogram.
1. Kies in het (de) downloadmiddel(en) een van de volgende opties en tik **[!UICONTROL Download]**.

   * **Downloaden als CRX-pakket:** Gebruik de optie om alle geselecteerde elementen en gerelateerde afhankelijkheden te downloaden en verplaatsen vanuit een [!DNL AEM Forms] aan een andere instantie. Alle elementen en mappen worden als crx-pakket gedownload. Alle formulierelementen, zoals de formulieren die zijn geschreven in AEM (Adaptieve Forms en Adaptieve formulierfragmenten), PDF-documenten en bronnen (XSD&#39;s, XFS, afbeeldingen) kunnen worden gedownload als pakket van [!DNL AEM Forms] UI.
Het voordeel van het downloaden van elementen als pakket is dat ook elementen worden gedownload die door het geselecteerde element zijn gebruikt om te downloaden. Als u bijvoorbeeld een adaptief formulier hebt waarin een formuliersjabloon, XSD en een afbeelding worden gebruikt. Wanneer u dit adaptieve formulier selecteert en het als pakket downloadt, bevat het gedownloade pakket ook de formuliersjabloon, XSD en de afbeelding. Alle metagegevenseigenschappen (inclusief aangepaste eigenschappen) die aan het element zijn gekoppeld, worden ook gedownload.

   * **Elementen downloaden als binaire bestanden:** Gebruik de optie om alleen formuliersjablonen (XDP), PDF forms (PDF), documenten (PDF) en bronnen (afbeeldingen, schema&#39;s, opmaakmodellen) te downloaden. U kunt deze elementen bewerken met externe toepassingen. De formulierbestanden met binaire bestanden, zoals XSD&#39;s, XDP&#39;s, afbeeldingen, PDF en XDP&#39;s, worden gedownload als ZIP-bestand.
U kunt geen adaptieve Forms, adaptieve formulierfragmenten en thema&#39;s downloaden met **[!UICONTROL Download asset(s) as binary files]** -optie. Als u deze middelen wilt downloaden, kunt u het beste **[!UICONTROL Download as CRX Package]** -optie.

   De geselecteerde elementen worden gedownload als een archief (.zip-bestand).

   >[!NOTE]
   >
   >Zowel AEM pakket- als binaire bestanden worden gedownload als een archief (.zip-bestand). De sjablonen voor de elementen worden niet samen met de elementen gedownload. U moet de elementsjablonen afzonderlijk exporteren.

### Elementen uploaden {#upload-forms-amp-documents-assets}

Forms en Documenten uploaden:

1. Aanmelden bij de [!DNL AEM Forms] -instantie.
1. Tikken, Experience Manager ![adobeexperienceManager](assets/adobeexperiencemanager.png) pictogram > navigatie ![kompas](assets/Smock_Compass_18_N.svg) pictogram> **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Tikken **Maken** >**Bestand uploaden**. Er wordt een dialoogvenster voor het uploaden of verpakken weergegeven.
1. Blader in het dialoogvenster naar het pakket of het archief dat u wilt importeren en selecteer dit. U kunt ook PDF-documenten, XSD&#39;s, afbeeldingen, stijlpagina&#39;s en XDP-formulieren selecteren. Tik op **[!UICONTROL Open]**. De map of de bestandsnaam die u selecteert, mag geen speciale tekens bevatten.

   Controleer in het dialoogvenster de details van de te uploaden middelen en tik op **[!UICONTROL Upload]**.

   Als u een bestaand formulierelement uploadt, wordt het element bijgewerkt.

   >[!NOTE]
   >
   >Het uploaden van een pakket vervangt de bestaande maphiërarchie niet. Als u bijvoorbeeld een adaptief formulier hebt met de naam &#39;Training&#39; op de locatie /content/dam/formsanddocuments op één server. U downloadt het adaptieve formulier en uploadt het formulier naar een andere server. De tweede server heeft ook een map met de naam &#39;Training&#39; op dezelfde locatie/content/dam/formsanddocuments. Het uploaden mislukt.

## Een thema downloaden of uploaden {#downloading-or-uploading-a-theme}

Met [!DNL AEM Forms]kunt u thema&#39;s maken, downloaden of uploaden. Net als andere elementen, zoals formulieren, documenten en letters, wordt een thema gemaakt. U kunt een thema maken, dit downloaden en uploaden naar een aparte versie om het opnieuw te gebruiken. Zie voor meer informatie over thema&#39;s [Thema&#39;s](themes.md) in [!DNL AEM Forms].

### Een thema downloaden {#downloading-a-theme}

U kunt thema&#39;s exporteren in [!DNL AEM Forms] die u kunt gebruiken in andere projecten of instanties. AEM kunt u thema downloaden als een ZIP-bestand dat u kunt uploaden op het exemplaar.

Een thema downloaden:

1. Aanmelden bij de [!DNL AEM Forms] -instantie.
1. Tikken, Experience Manager ![adobeexperienceManager](assets/adobeexperiencemanager.png) pictogram > navigatie ![kompas](assets/Smock_Compass_18_N.svg) pictogram> **[!UICONTROL Forms]** > **[!UICONTROL Themes]**.
1. Selecteer het thema en tik op **[!UICONTROL Download]**. Het thema wordt gedownload als een archief (.zip-bestand).

### Een thema uploaden {#uploading-a-theme}

U kunt gemaakte thema&#39;s gebruiken met voorinstellingen voor stijlen voor uw project. U kunt themapakketten die anderen maken, importeren door deze te uploaden naar uw project.

Een thema uploaden:

1. Navigeer in Experience Manager naar **[!UICONTROL Forms]** > **[!UICONTROL Forms Themes]**.
1. Klik op de pagina Thema&#39;s op **[!UICONTROL Forms Create]** > **[!UICONTROL Forms File Upload]**.
1. Blader in de vraag Bestand uploaden naar en selecteer een themapakket op uw computer en klik op **[!UICONTROL Forms Upload]**. Het thema wordt geüpload.

<!--

## Import and export assets in Correspondence Management {#import-and-export-assets-in-correspondence-management}

To share assets, such as data dictionaries, letters, and document fragments, between two different implementations of Correspondence Management, you can create and share .cmp files. A .cmp file can include one or more data dictionaries, letters, document fragments, and forms.

### Export Document Fragments, Letters, and/or Data Dictionaries {#export-document-fragments-letters-and-or-data-dictionaries}

1. In the letters, document fragments, or data dictionary pages, tap and select the assets you want to export to a single package, and then tap Queue For Download. The assets are lined-up for export.
1. As required, repeat the above step to add letters, document fragments, and data dictionaries.
1. Tap **Download**.
1. Correspondence Management displays Download Asset(s) dialog with a list of assets in the export list.

   ![export](assets/export.png)

1. To view the dependencies that are exported, Tap Resolve. Or skip to the next step. Even if you do not tap resolve, the dependencies are still exported.
1. To download the .cmp file, tap **OK**.
1. Correspondence Management downloads a .cmp file to your computer.

   The .cmp file includes the exported assets. You can share the .cmp file with others. Other users can import the .cmp file in a different server to get all the assets in the new server.

### Export all the Correspondence Management assets as a package {#export-all-the-correspondence-management-assets-as-a-package}

Use this option to download all the Correspondence Management assets and related dependencies as a package from an [!DNL AEM Forms] instance.

For example, if Correspondence Management has a letter that uses an image and text, the downloaded package also contains the image and the text related to the letter. All the metadata properties (including custom properties) associated with the asset are also downloaded. Once you have downloaded the package (.cmp), you can [import the package to a different [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

To download all the Correspondence Management assets and related dependencies as a package, complete the following steps:

1. Log in to [!DNL AEM Forms] server as a forms user.
1. Tap **Adobe Experience Manager** in the Global Navigation bar.
1. Tap tools ( ![tools](assets/tools.png)) and then tap **Forms**.
1. Tap **Export Correspondence Management Assets**.

   ![publish-cmp-assets-1](assets/publish-cmp-assets-1.png)

   ( ``The Export All Correspondence Management Assets page appears and displays the information about the last time the Export process was attempted and a link to download the last successfully exported package.

   ![export-last-run-details](assets/export-last-run-details.png)

1. Tap **Export** and, in the confirm message, tap **OK**.

   After a batch process is complete, the last run details and the link to download the package are updated. This includes information such as the Administrator login and if the batch run successfully or failed. The assets are exported to a package and the Download Exported Package link appears.

   >[!NOTE]
   >
   >The Export All Assets process cannot be canceled once initiated. Also, while the export all operation is in process, do not create, delete, modify, or publish any assets or initiate Publish All Assets process.a

1. Tap the **Download Exported Package** link to download the package file.

   To add the assets in the package to another instance of Correspondence Management, [import the package to an [!DNL AEM Forms] instance](import-export-forms-templates.md#p-upload-forms-documents-assets-p).

### Import Document Fragments, Letters and/or Data Dictionaries into Correspondence Management {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

You can import assets that are exported into a .cmp file. A .cmp file can have one or more letters, data dictionaries, document fragments, and dependent assets.

>[!NOTE]
>
>While importing old Correspondence Management assets for migration, log in using an Admin account. For more information on Migrating old Correspondence Management assets, see [Migrate Correspondence Management assets to AEM 6.1 forms](migration-utility.md).

1. On the data dictionary, letters, or document fragments page, tap **Create &gt; File Upload** and select the .cmp file.
1. Correspondence Management displays the Import Assets dialog with the list of assets that are imported. Tap **Import**.

   After importing the assets, the following properties of the assets are updated while the other properties remain the same:

    * Author: Displays the ID of the user that imported the asset to the server
    * Modified: The time when the asset was imported to the server

   >[!NOTE]
   >
   >For you to be able to upload XDPs (as part of the cmp file or otherwise), you need to be a part of forms-power-users group. For access rights, contact the administrator.
-->

## Een workflowtoepassing exporteren {#export-a-workflow-application}

U kunt AEM pakketbeheer gebruiken om workflowtoepassingen te exporteren. De procedure is als volgt:

1. Openen [!DNL AEM Forms] pakketbeheer.
1. Klik op **[!UICONTROL Create Package]**. De **[!UICONTROL New Package]** wordt weergegeven.
1. Geef een naam, versie en groep voor het pakket op. Klik op **[!UICONTROL OK]**.
1. Klikken **[!UICONTROL Edit]** en opent u de **[!UICONTROL Filters]** tab. Klik op **[!UICONTROL Add Filter]**. Geef het pad van de workflowtoepassing op. Bijvoorbeeld /etc/fd/dashboard/startpoints/homemortgauge. Klik op **[!UICONTROL Add rule]**.

1. Open de **[!UICONTROL Advanced]** tab. Selecteren **[!UICONTROL Merge]** of **[!UICONTROL Overwrite]** in ACL Behandelend gebied. Klik op **[!UICONTROL Save]**.
1. Klikken **[!UICONTROL Build]** om het pakket te maken.

   Nadat het pakket is gemaakt, kunt u het pakket downloaden en naar de andere server importeren. De workflowtoepassing wordt weergegeven op de server waarop het pakket is geüpload.

   >[!NOTE]
   >
   >De workflowtoepassing werkt alleen correct als u het bijbehorende adaptieve formulier- en workflowmodel exporteert met de werktoepassing.

## Mappen en elementen ordenen {#folders-and-organizing-assets}

[!DNL AEM Forms] gebruikersinterface gebruikt mappen om elementen te rangschikken. Deze mappen worden gebruikt voor het rangschikken van elementen die zijn gemaakt in [!DNL AEM Forms] gebruikersinterface. U kunt de naam van submappen wijzigen, submappen maken en elementen en documenten in deze mappen opslaan. Door documenten en elementen in een map te ordenen, kunt u de bestanden groeperen voor eenvoudig beheer. U kunt een map selecteren en deze downloaden of verwijderen.

Voer de volgende stappen uit om een map te maken:

### Een map maken {#create-a-folder}

1. Aanmelden bij de [!DNL AEM Forms] gebruikersinterface op `https://<server>:<port>/aem/forms.html`.
1. Navigeer naar de locatie waaronder u een map wilt maken.
1. Tik op **[!UICONTROL Create]** > **[!UICONTROL Folder]**.
1. Voer de volgende gegevens in:

   * **Titel:** Naam voor de map weergeven
   * **Naam:** *(Verplicht)* De knooppuntnaam waaronder u de map in de opslagplaats wilt opslaan

   >[!NOTE]
   >
   >Standaard wordt de waarde van het naamveld automatisch ingevuld vanuit de titel. De naam mag alleen alfanumerieke tekens bevatten of speciale tekens voor het koppelteken (-) en het onderstrepingsteken (_). Eventuele andere speciale tekens die in de titel worden ingevoerd, worden automatisch vervangen door een afbreekstreepje en u wordt gevraagd de nieuwe naam te bevestigen. U kunt doorgaan met de voorgestelde naam of deze verder bewerken.

1. Er wordt een nieuwe map met de door u gedefinieerde titel weergegeven op de huidige locatie in de lijst met elementen.

   Als een map met de opgegeven naam bestaat, mislukt het verzenden met een fout. U kunt het foutbericht weergeven door de muisaanwijzer op de fout te plaatsen ![aem6forms_error_alert](assets/Smock_Alert_18_N.svg) pictogram dat naast het naamveld wordt weergegeven.

   Tik op de nieuwe map om naar de map te gaan en elementen of mappen in de map te maken. Bovendien kunt u een map selecteren en ervoor kiezen deze in de wachtrij te plaatsen voor downloaden, te verwijderen of de naam ervan te bewerken.

<!-- ### Create copies of one or more assets or letters {#create-copies-of-one-or-more-assets-or-letters}

You can use an existing assets and letters to quickly create a assets and letters with similar properties, content, and inherited assets. You can copy and paste data dictionaries, document fragments, and letters.

Complete the following steps to create copies of assets and letters:

1. In the relevant Assets or Letters page, select one or more assets/letters. The UI displays the Copy icon.
1. Tap Copy. The UI displays the Paste icon. You can also choose to go/navigate inside a folder before you paste. Different folders can contain assets with same names. For more information on folders, see [Folders and organizing assets](#folders-and-organizing-assets).
1. Tap Paste. The Paste dialog appears. The system auto generates names and titles to the new copies of assets/letters, but you can edit the titles and names of the assets/letters.

   If you are copying and pasting the assets/letters at the same place, a suffix "-CopyXX" gets added to the existing name of the asset/letter. If no title existed for the copied asset/letter, the auto generated title field remains blank.

1. If required, edit the Title and Name with which you want to save the copy of the asset/letter.
1. Tap Paste. New copies of the copied assets are created.

## Search {#search-forms}

[!DNL AEM Forms] UI lets you search your content. Using the top bar, you can tap Search **[A]** to search your content for resources such as assets and documents.

When you search for assets, [!DNL AEM Forms] displays the side panel. You can also tap ![assets-browser-content-only](assets/assets-browser-content-only.png) &gt; Filter **[B]** to invoke the side panel. Using the various filters in the side panel, you can narrow down your search. The side panel also lets you save your searches.

![search_topbar](assets/search_topbar.png)

**A.** Search **B.** Filter

![Side panel - Filters](assets/search_sidepanel.png)

Side panel - Filters

On the side panel, you can use the following to narrow down your search results:

* Search Directory
* Tags
* Search Criteria; for example, Modified Dates, Publish Status, LiveCopy Status.

The side panel also lets you save your search settings with names of your choice.

For more information and instructions on using search, filters, saved search, and side panel, see [Search](/help/sites-authoring/search.md).

-->

>[!MORELIKETHIS]
>
>* [Exportformuliersjablonen importeren](/help/forms/import-export-forms-templates.md)
>* [Thema&#39;s gebruiken in Adaptief formulier Core-componenten](/help/forms/using-themes-in-core-components.md)