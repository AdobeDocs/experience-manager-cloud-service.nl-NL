---
title: Hoe kan ik Adaptive Forms of PDF forms importeren, exporteren en organiseren op een AEM Forms-exemplaar?
description: Leer Adaptief Forms, PDF forms, thema's en andere ondersteunende middelen migreren van en naar AEM-instanties.
topic-tags: forms-manager
role: Admin, User
feature: Adaptive Forms
exl-id: f5105fb7-b8c0-4656-8095-b21d392746c0
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '1025'
ht-degree: 1%

---

# Adaptieve Forms- en AEM Forms-middelen importeren of exporteren {#importing-and-exporting-assets-to-aem-forms}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/forms/manage-administer-aem-forms/import-export-forms-templates) |
| AEM as a Cloud Service | Dit artikel |

U kunt Adaptief Forms en gerelateerde elementen, zoals Adaptief formulierthema&#39;s, Formuliergegevensmodel (FDM), Aangepaste formuliersjablonen, Fragmenten en PDF forms, tussen [!DNL AEM Forms] -instanties verplaatsen.

## Adaptieve Forms, PDF forms of verwante middelen downloaden {#download-forms-amp-documents-assets}

Formulieren of gerelateerde elementen downloaden:

1. Meld u aan bij uw [!DNL Experience Manager Forms] -instantie.
1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .

   ![ Uitgezochte Forms ](/help/forms/assets/select-forms.png)

1. Selecteer de elementen en klik op het pictogram **[!UICONTROL Download]** in de bovenste track.

   ![ Download Forms ](/help/forms/assets/download-form.png)

   Wanneer u het formulier downloadt, wordt het dialoogvenster **[!UICONTROL Download Asset(s)]** weergegeven.

   ![ Download vormenactiva ](/help/forms/assets/download-form-assets.png)

1. Klik op **[!UICONTROL Download]**.

De geselecteerde elementen worden gedownload als een archief (.zip-bestand).

## Adaptieve Forms, PDF forms of verwante middelen uploaden {#upload-forms-amp-documents-assets}

U kunt de ondersteunde elementtypen afzonderlijk of als ZIP-archief uploaden. Voor een ZIP-bestand worden de relatieve paden van alle ondersteunde elementen weergegeven. Niet-ondersteunde elementen in het ZIP-bestand worden genegeerd en niet vermeld. Als het ZIP-archief echter alleen de niet-ondersteunde elementen bevat, wordt een foutbericht weergegeven in plaats van het pop-updialoogvenster.
Een formulier of een verwant element uploaden:

1. Meld u aan bij uw [!DNL Experience Manager Forms] -instantie.
1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .

   ![ Uitgezochte Forms ](/help/forms/assets/select-forms.png)

1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL File Upload]** . Er wordt een dialoogvenster weergegeven.

   ![ upload Forms ](/help/forms/assets/form-upload.png)

1. Blader in het dialoogvenster naar het pakket of het archief dat u wilt importeren en selecteer dit. U kunt ook andere ondersteunde bestandstypen selecteren. Selecteer **[!UICONTROL Open]**. De map of de bestandsnaam die u selecteert, mag geen speciale tekens bevatten.

   Controleer in het dialoogvenster de details van de elementen die worden geüpload en selecteer **[!UICONTROL Upload]** .

   Als u een bestaand formulierelement uploadt, wordt het element bijgewerkt.

   >[!NOTE]
   >
   > Wanneer een naamconflict optreedt met verschillende typen bronnen, wordt de bestaande maphiërarchie niet vervangen door een pakket te uploaden. Als u bijvoorbeeld een adaptief formulier hebt met de naam &#39;Training&#39; op locatie `/content/dam/formsanddocuments` op één server. U kunt het adaptieve formulier downloaden en uploaden naar een andere server. De tweede server heeft ook een map met de naam &#39;Training&#39; op dezelfde locatie `/content/dam/formsanddocuments` . Het uploaden mislukt.

## Een thema downloaden

U kunt thema&#39;s in [!DNL AEM Forms] exporteren die u kunt gebruiken in andere projecten of instanties. Met AEM kunt u thema&#39;s downloaden als ZIP-bestand. U kunt dit bestand op dat moment uploaden.
Een thema downloaden:

1. Meld u aan bij de [!DNL Experience Manager Forms] Author-instantie.
1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Themes]** .

   ![ Uitgezochte Thema ](/help/forms/assets/select-theme.png)

1. Selecteer het thema op de pagina Thema&#39;s en klik op het pictogram **[!UICONTROL Download]** in de bovenste track.

   ![ Thema van de Download ](/help/forms/assets/download-theme.png)

   Wanneer u het thema downloadt, verschijnt het dialoogvenster **[!UICONTROL Download Asset(s)]** .

   ![ Download themaactiva ](/help/forms/assets/download-theme-asset.png)

1. Klik op **[!UICONTROL Download]**.

De geselecteerde elementen worden gedownload als een archief (.zip-bestand).

## Een thema uploaden {#uploading-a-theme}

U kunt thema&#39;s die anderen in uw formulieren maken, uploaden en gebruiken.
Een thema uploaden:

1. Meld u aan bij uw [!DNL Experience Manager Forms] -instantie.
1. Navigeer in Experience Manager naar **[!UICONTROL Forms]** > **[!UICONTROL Themes]** .

   ![ Uitgezochte Thema ](/help/forms/assets/select-theme.png)

1. Klik op de pagina Themes op **[!UICONTROL Create]** > **[!UICONTROL File Upload]** .

   ![ upload Thema ](/help/forms/assets/theme-upload.png)

1. Blader naar een themapakket op uw computer en selecteer dit pakket. Klik vervolgens op **[!UICONTROL Upload]** . Het geüploade thema wordt beschikbaar op de pagina Themes.

## Mappen gebruiken om Adaptief Forms, PDF forms en gerelateerde elementen te ordenen  {#folders-and-organizing-assets}

U kunt mappen gebruiken om elementen te rangschikken en te ordenen. Door documenten en elementen in een map te ordenen, kunt u de bestanden groeperen voor eenvoudig beheer. U kunt een map selecteren en deze downloaden of verwijderen.

### Een map maken {#create-a-folder}

Een map maken:

1. Meld u aan bij uw [!DNL Experience Manager Forms] -instantie.
1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .

   ![ Uitgezochte Vorm ](/help/forms/assets/select-forms.png)

1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Folder]** .

   ![ creeer Omslag ](/help/forms/assets/create-folder.png)

   Het dialoogvenster **[!UICONTROL Add Folder]** wordt weergegeven.
1. Voer de **[!UICONTROL Title]** in. De **[!UICONTROL Name]** wordt automatisch gevuld wanneer u de **[!UICONTROL Title]** typt.

   ![ voeg Omslag ](/help/forms/assets/add-folder.png) toe

1. Klik op **[!UICONTROL Create]**.

   >[!NOTE]
   >
   >Standaard wordt de waarde van het naamveld automatisch ingevuld vanaf de titel. De naam mag alleen alfanumerieke tekens bevatten of speciale tekens voor het koppelteken (-) en het onderstrepingsteken (_). Eventuele andere speciale tekens die in de titel worden ingevoerd, worden automatisch vervangen door een afbreekstreepje en u wordt gevraagd de nieuwe naam te bevestigen. U kunt doorgaan met de voorgestelde naam of deze verder bewerken.

Er wordt een nieuwe map met de door u gedefinieerde titel weergegeven op de huidige locatie in de lijst met elementen.

Als een map met de opgegeven naam bestaat, mislukt het verzenden met een fout. U kunt het foutenbericht bekijken door over het fout ![ aem6forms_error_alert ](assets/Smock_Alert_18_N.svg) pictogram te bewegen dat naast het naamgebied verschijnt.

U kunt de gemaakte map selecteren om naar de map te gaan en elementen of mappen in de map te maken. Bovendien kunt u een map selecteren en ervoor kiezen deze in de wachtrij te plaatsen voor downloaden, te verwijderen of de naam ervan te bewerken.

### Kopieën maken van een of meer elementen {#create-copies-of-one-or-more-assets-or-letters}

U kunt bestaande elementen gebruiken om snel een element met vergelijkbare eigenschappen, inhoud en overgeërfde elementen te maken.

Kopieën van elementen maken:

1. Meld u aan bij uw [!DNL Experience Manager Forms] -instantie.
1. Selecteer een of meer elementen op de relevante elementenpagina. In de gebruikersinterface wordt het pictogram **[!UICONTROL Copy]** weergegeven.
1. Selecteer **[!UICONTROL Copy]**. UI toont het ![ pictogram van het Deeg ](/help/forms/assets/Smock_Paste_18_N.svg) pictogram.

   ![ activa van het Exemplaar ](/help/forms/assets/copy-asset.png)

   U kunt er ook voor kiezen om in een map te navigeren voordat u gaat plakken. Verschillende mappen kunnen elementen met dezelfde naam bevatten. Voor meer informatie over omslagen, zie [ Omslagen en het organiseren van activa ](#folders-and-organizing-assets).
1. Selecteer **[!UICONTROL Paste]** .

   ![ activa van het Deeg ](/help/forms/assets/paste-asset.png)

1. Het dialoogvenster **[!UICONTROL Paste]** wordt weergegeven. Het systeem genereert automatisch namen en titels voor de nieuwe exemplaren van elementen, maar u kunt de titels en namen van de elementen bewerken.

   Als u de elementen op dezelfde plaats kopieert en plakt, wordt het achtervoegsel &quot;-CopyXX&quot; toegevoegd aan de bestaande naam van de `asset` . Als er geen titel voor het gekopieerde element bestaat, blijft het automatisch gegenereerde titelveld leeg.

   ![ Deeg activa bij nieuwe plaats ](/help/forms/assets/paste-click-asset.png)

   Bewerk indien nodig de **[!UICONTROL Title]** waarmee u de kopie van het element wilt opslaan. De **[!UICONTROL Name]** wordt automatisch gevuld wanneer u de **[!UICONTROL Title]** typt.
1. Selecteer **[!UICONTROL Paste]**. Er worden nieuwe kopieën van de gekopieerde elementen gemaakt.

## Zoeken {#search-forms}

Als u een groot aantal middelen hebt, kost het veel tijd om naar het juiste middel te zoeken. U kunt een op tekst gebaseerde zoekopdracht naar een specifiek element op de elementpagina uitvoeren.

Het element doorzoeken:

1. Meld u aan bij uw [!DNL Experience Manager Forms] -instantie.
1. Klik het ![ pictogram van het onderzoekspictogram ](assets/folder-search-icon.svg) onderzoekspictogram.

   ![ Vorm van het Onderzoek ](/help/forms/assets/search-form.png)

1. Voer in de zoekbalk de naam in van het element dat u wilt zoeken.

1. Er wordt een lijst met verwante elementen weergegeven. Selecteer het gewenste element in de lijst met weergegeven elementen.

   ![Assets doorzoeken](/help/forms/assets/search-bar.png)

Voor meer informatie en instructies bij het gebruiken van onderzoek, zie [ Onderzoek ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=nl-NL).

<!--
## Export or create a package {#export-a-workflow-application}

You can use packages to install new content, install new functionality, transfer content between instances, and back up content.
To export or create a package:

1. Log in to your [!DNL Experience Manager Forms] instance.
1. Navigate to **[!UICONTROL Tools]** ![hammer](assets/hammer.png) &gt; **[!UICONTROL Deployment]** &gt; **[!UICONTROL Packages]**.

   ![Package Manager](/help/forms/assets/package-manager.png)

1. Click **[!UICONTROL Create Package]**.

   ![Create package](/help/forms/assets/create-package.png)   
   
   When **[!UICONTROL Create Package]** is clicked, the **[!UICONTROL New Package]** dialog box appears.
1. Specify the package name, version, and group for the package. 
   
   ![New package](/help/forms/assets/new-package.png)  

   * **Package Name** - Select a descriptive name to help you identify the contents of the package.

   * **Version** - It is a textual field to indicate a version. This is appended to the package name to form the name of the zip file.

   * **Group** - This is the target group (or folder) name. Groups help you organize your packages. A folder is created for the group if it does not already exist. If you leave the group name blank, it creates the package in the main package list.

1. Click **[!UICONTROL OK]**.

   Once the package is created, it appears at the top of the list of packages.

1. Click **[!UICONTROL Edit]**.
   
   ![Edit Package](/help/forms/assets/edit-package.png)
    
1. Open the **[!UICONTROL Filters]** tab.
   
   ![Open filter tab](/help/forms/assets/add-filter-package.png)
   
1.  Click **[!UICONTROL Add Filter]**. 
   
      ![Add filter](/help/forms/assets/add-filter.png)

      You can specify the path of the package. You can also add rules and other validations for the package.

      ![Add path](/help/forms/assets/add-path.png)

1. Click **[!UICONTROL Save]** after you are finished editing the settings.
1. Click **[!UICONTROL Build]** to create the package.
    
     ![Build path](/help/forms/assets/build-package.png)

   After the package is built, you can download the package and import it to the other server. The workflow application appears on the server where the package is uploaded.

   >[!NOTE]
   >
   >For the workflow application to work properly, also export the corresponding Adaptive Form and workflow model with the work application.

   Once a package is uploaded to AEM, you can modify its settings. You can also download or delete the package.

## Import and export assets in Correspondence Management {#import-and-export-assets-in-correspondence-management}

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

## Zie ook {#see-also}

{{see-also}}
