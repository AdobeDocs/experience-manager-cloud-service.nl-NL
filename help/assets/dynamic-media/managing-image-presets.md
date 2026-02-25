---
title: Voorinstellingen afbeelding beheren
description: Leer over Voorinstellingen voor afbeeldingen en hoe u deze kunt maken, wijzigen en beheren.
contentOwner: Rick Brough
feature: Image Presets,Viewers,Renditions
role: User
exl-id: a53f40ab-0e27-45f8-9142-781c077a04cc
source-git-commit: 012ce93f65d26d7f59fc874d1b225fbd458cf098
workflow-type: tm+mt
source-wordcount: '2540'
ht-degree: 4%

---

# Voorinstellingen afbeelding beheren{#managing-image-presets}

Met Voorinstellingen voor afbeeldingen kan Adobe Experience Manager Assets afbeeldingen dynamisch leveren in verschillende formaten, in verschillende indelingen of met andere afbeeldingseigenschappen die dynamisch worden gegenereerd. Elke voorinstelling voor afbeeldingen vertegenwoordigt een vooraf gedefinieerde verzameling opdrachten voor het vergroten of verkleinen en opmaken van afbeeldingen. Wanneer u een voorinstelling voor afbeeldingen maakt, kiest u een grootte voor het leveren van de afbeelding. U kiest ook opmaakopdrachten, zodat de weergave van de afbeelding wordt geoptimaliseerd wanneer de afbeelding wordt geleverd voor weergave.

Beheerders kunnen voorinstellingen maken voor het exporteren van elementen. Gebruikers kunnen bij het exporteren van afbeeldingen een voorinstelling kiezen die de afbeeldingen opnieuw opmaakt volgens de specificaties die de beheerder heeft opgegeven.

U kunt ook voorinstellingen voor afbeeldingen maken die reageren. Als u een voorinstelling voor een responsieve afbeelding toepast op uw elementen, worden deze afhankelijk van het apparaat of de schermgrootte waarop ze worden weergegeven. U kunt Voorinstellingen voor afbeeldingen zodanig configureren dat naast RGB of Grijs ook CMYK in de kleurruimte wordt gebruikt.

In deze sectie wordt beschreven hoe u voorinstellingen voor afbeeldingen maakt, wijzigt en over het algemeen beheert. U kunt een voorinstelling voor afbeeldingen op elk gewenst moment op een afbeelding toepassen. Zie [&#x200B; Beeld toepassen vooraf instelt &#x200B;](/help/assets/dynamic-media/image-presets.md).

>[!NOTE]
>
>Slimme beeldverwerking werkt met uw bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie bij de laatste milliseconde van de levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding. Zie [&#x200B; Slimme Beeldvorming &#x200B;](/help/assets/dynamic-media/imaging-faq.md) voor meer informatie.

## Meer informatie over voorinstellingen voor afbeeldingen {#understanding-image-presets}

Net als bij een macro is een voorinstelling voor afbeeldingen een vooraf gedefinieerde verzameling opdrachten voor het vergroten of verkleinen en opmaken van de grootte die onder een naam zijn opgeslagen. Als u wilt weten hoe Voorinstellingen afbeelding werken, veronderstelt u dat elke productafbeelding op uw website moet worden weergegeven in verschillende formaten, formaten en compressiesnelheden voor levering op het bureaublad en in mobiele apparaten.

U kunt twee voorinstellingen voor afbeeldingen maken: 500 x 500 pixels voor het bureaublad en 150 x 150 pixels voor mobiele apparaten. U maakt twee voorinstellingen voor afbeeldingen, een voorinstelling die `Enlarge` wordt genoemd, om afbeeldingen met 500 x 500 pixels weer te geven en een voorinstelling die `Thumbnail` wordt aangeroepen om afbeeldingen met 150 x 150 pixels weer te geven. Experience Manager zoekt naar de definitie van `Enlarge` en `Thumbnail` om afbeeldingen op `Enlarge Image Preset` - en `Thumbnail Image Preset` -grootte te leveren. Vervolgens genereert Experience Manager dynamisch een afbeelding met de grootte en opmaakspecificaties van elke voorinstelling voor afbeeldingen.

Afbeeldingen die bij dynamische levering kleiner worden gemaakt, kunnen scherper en gedetailleerder worden. Daarom bevat elke voorinstelling voor afbeeldingen opmaakbesturingselementen waarmee u een afbeelding kunt optimaliseren wanneer deze met een bepaalde grootte wordt geleverd. Met deze besturingselementen zorgt u ervoor dat uw afbeeldingen scherp en duidelijk zijn wanneer ze aan uw website of toepassing worden geleverd.

Beheerders kunnen voorinstellingen voor afbeeldingen maken. Als u een voorinstelling voor afbeeldingen wilt maken, begint u helemaal opnieuw of u kunt een bestaande voorinstelling opnieuw gebruiken en opslaan onder een andere naam.

## Voorinstellingen afbeelding beheren {#managing-image-presets-1}

U beheert uw Voorinstellingen voor afbeeldingen in Experience Manager door het Experience Manager-logo te selecteren voor toegang tot de algemene navigatieconsole en vervolgens het pictogram Extra te selecteren en naar **[!UICONTROL Assets]** > **[!UICONTROL Image Presets]** te navigeren.

![&#x200B; 6_5_tools-assets-imagepresets &#x200B;](assets/6_5_tools-assets-imagepresets.png)

>[!NOTE]
>
>Alle voorinstellingen voor afbeeldingen die u maakt, zijn ook beschikbaar als dynamische uitvoeringen wanneer u elementen voorvertoont of levert.
>
>U *niet* te hoeven om Beeld te publiceren vooraf instelt aangezien het Beeld automatisch wordt gepubliceerd.
>
>Zie [&#x200B; publiceren Beeld vooraf instelt &#x200B;](#publishing-image-presets).

>[!NOTE]
>
>Het systeem geeft verschillende uitvoeringen weer wanneer u **[!UICONTROL Renditions]** selecteert in de Gedetailleerde weergave van een element. U kunt het aantal voorinstellingen voor afbeeldingen dat wordt weergegeven, verhogen of verlagen. Zie [&#x200B; Verhoog het aantal beeld vooraf instelt die &#x200B;](#increasing-or-decreasing-the-number-of-image-presets-that-display) worden getoond.

## Hoe voorinstellingen afbeelding betrekking hebben op uitvoeringen {#how-image-presets-relate-to-renditions}

Met voorinstellingen voor afbeeldingen wordt gedefinieerd hoe Dynamic Media afbeeldingen levert, zoals grootte, opmaak, compressie en andere weergaveparameters. Met voorinstellingen worden geen uitvoeringen zelf gegenereerd. In plaats daarvan vertrouwen ze op uitvoeringen die worden gemaakt wanneer elementen worden verwerkt.

### Vertoning genereren in AEM as a Cloud Service{#rendition-generation-in-aemaacs}

In AEM as a Cloud Service, worden de vertoningen geproduceerd gebruikend [&#x200B; Microservices van Activa &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use#). De DAM Update Asset-workflow is niet beschikbaar voor aanpassing in Cloud Service.

Belangrijke overwegingen zijn onder andere:

* Uitvoeringen worden tijdens het uploaden gegenereerd.
* Wijzigingen in een verwerkingsprofiel zijn van invloed op nieuw geüploade elementen. Bestaande activa moeten opnieuw worden verwerkt indien nieuwe uitvoeringen vereist zijn.
* Aanpassing van workflowmodel wordt niet ondersteund in AEM as a Cloud Service voor het genereren van uitvoeringen.

Voorinstellingen voor afbeeldingen verwijzen naar beschikbare uitvoeringen op het moment van levering. Zorg ervoor dat de vereiste uitvoeringen bestaan voordat u Voorinstellingen afbeelding configureert of gebruikt.

**om te controleren welke vertoningen worden geproduceerd:**

1. Creeer of geef a [&#x200B; het Profiel van de Verwerking &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use#) uit.
2. Configureer de vereiste vertoningsdefinities.
3. Pas het verwerkingsprofiel toe op de juiste map.

Wanneer elementen worden geüpload naar een map waarop een verwerkingsprofiel is toegepast, genereren Asset Microservices automatisch de gedefinieerde uitvoeringen.

<!--
### Adobe Illustrator (AI), PostScript&reg; (EPS), and PDF file formats {#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats}

If you intend to support the ingestion of AI, EPS, and PDF files so that you can generate dynamic renditions of these file formats, review the following information before you create Image Presets.

Adobe Illustrator's file format is a variant of PDF. The main differences, in the context of Experience Manager Assets, are the following:

* Adobe Illustrator documents consist of a single page with multiple layers. Each layer is extracted as a PNG subasset under the main Illustrator asset.
* PDF documents consist of one or more pages. Each page is extracted as a single page PDF subasset under the main multi-page PDF document.

The `Create Sub Asset process` component creates the subassets within the overall `DAM Update Asset` workflow. To see this process component within the workflow, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** > **[!UICONTROL DAM Update Asset]** > **[!UICONTROL Edit]**.

See also [Viewing pages of a multi-page file](/help/assets/manage-linked-subassets.md#view-pages-of-a-multi-page-file).

You can view the subassets or the pages when you open the asset, select the Content menu, and select **[!UICONTROL Subassets]** or **[!UICONTROL Pages]**. The subassets are real assets. The `Create Sub Asset` workflow component extracts the PDF pages. They are then stored as `page1.pdf`, `page2.pdf`, and so on, below the main asset. After they are stored, the `DAM Update Asset` workflow processes them.

To use Dynamic Media to preview and generate dynamic renditions for AI, EPS or PDF files, the following processing steps are required:

1. In the `DAM Update Asset` workflow, the `Rasterize PDF/AI Image Preview Rendition` process component rasterizes the first page of the original asset &ndash; using the configured resolution &ndash; into a `cqdam.preview.png` rendition.

1. The `Dynamic Media Process Image Assets` process component within the workflow optimizes the `cqdam.preview.png` rendition into a PTIFF.

>[!NOTE]
>
>In the DAM Update Asset workflow, the **[!UICONTROL EPS thumbnails]** step generates thumbnails for EPS files.

#### PDF/AI/EPS asset metadata properties {#pdf-ai-eps-asset-metadata-properties}

| **Metadata property** |**Description** |
|---|---|
| `dam:Physicalwidthininches` |Document width in inches. |
| `dam:Physicalheightininches` |Document height in inches. |

You access `Rasterize PDF/AI Image Preview Rendition` process component options by way of the `DAM Update Asset` workflow.

Select Adobe Experience Manager in the upper left, the click **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**. On the Workflow Models page, select **[!UICONTROL DAM Update Asset]**, then on the toolbar select **[!UICONTROL Edit]**. On the DAM Update Asset workflow page, double-select the `Rasterize PDF/AI Image Preview Rendition` process component to open its Step Properties dialog box.

#### Rasterize PDF/AI Image Preview Rendition options {#rasterize-pdf-ai-image-preview-rendition-options}

![Arguments to rasterize PDF or AI workflow](assets/rasterize_pdf_ai_image_preview.png)

Arguments to rasterize PDF or AI workflow

|Process Argument | Default setting | Description |
|---|---|---|
| Mime Types | application/pdf<br>application/postscript<br>application/illustrator| List of document mime-types that are considered to be PDF or Illustrator documents. |
| Max Width | 2048 | Maximum width of the generated preview rendition, in pixels.|
| Max Height | 2048| Maximum height of the generated preview rendition, in pixels. |
| Resolution | 72 | Resolution to rasterize the first page, in ppi (pixels per inch). |

Using the default process arguments, the first page of a PDF/AI document is rasterized at 72 ppi and the generated preview image is sized at 2048 x 2048 pixels. For a typical deployment, you can increase the resolution to a minimum of 150 ppi or more. For example, a US letter size document at 300 ppi requires a maximum width and height of 2550 x 3300 pixels, respectively.

Max Width and Max Height limit the resolution at which to rasterize. For example, if the maximums are unchanged, and Resolution is set to 300 ppi, a US Letter document is rasterized at 186 ppi. That is, the document is 1581 x 2046 pixels.

The `Rasterize PDF/AI Image Preview Rendition` process component has a maximum defined to ensure that it does not create overly large images in memory. Such large images can overflow the memory provided to the JVM (Java&trade; Virtual Machine). Care must be taken to provide the JVM with enough memory to manage the configured number of parallel workflows, with each having the potential to create an image at the maximum configured size. -->

<!--
### InDesign (INDD) file format {#indesign-indd-file-format}

If you intend to support the ingestion of INDD files so that you can generate dynamic rendition of this file format, review the following information before you create Image Presets.

For InDesign files, sub assets are extracted only if the Adobe InDesign Server is integrated with Experience Manager. Referenced assets are linked based on their metadata. InDesign Server is not required for linking. However, the referenced assets must be present within Experience Manager before the InDesign files are processed for the links to be created between the InDesign files and the referenced assets.

See [Integrate Experience Manager Assets with InDesign Server](/help/assets/indesign.md).

The Media Extraction process component in the `DAM Update Asset` workflow runs several pre-configured Extend Scripts to process InDesign files.

![The ExtendScript paths in the arguments of Media Extraction process](/help/assets/dynamic-media/assets/6_5_mediaextractionprocess.png)

The ExtendScript paths in the arguments of the Media Extraction process component in the DAM Update Asset workflow.

The following scripts are used by Dynamic Media integration:


|ExtendScript name | Default | Description |
|---|---|---|
| ThumbnailExport.jsx | Yes  | Generates a 300 PPI `thumbnail.jpg` rendition that is optimized and turned into a PTIFF rendition by `Dynamic Media Process Image Assets` process component.  |
| JPEGPagesExport.jsx | Yes | Generates a 300 PPI JPEG subasset for each page. The JPEG subasset is a real asset stored under the InDesign asset. The `DAM Update Asset` workflow optimizes and converts it into a PTIFF. |
| PDFPagesExport.jsx | No | Generates a PDF subasset for each page. The PDF subasset gets processed as described earlier. Because the PDF contains a single page only, no subassets are generated. |
-->

<!--
### Configure the image thumbnail size {#configuring-image-thumbnail-size}

You can configure the size of thumbnails by configuring those settings in the **[!UICONTROL DAM Update Asset]** workflow. There are two steps in the workflow where you can configure the thumbnail size of image assets. One (**[!UICONTROL Dynamic Media Process Image Assets]**) is used for dynamic image assets. The other (**[!UICONTROL Process Thumbnails]**) is used for static thumbnail generation or when all other processes fail to generate thumbnails. Regardless, *both* must have the same settings.

The **[!UICONTROL Dynamic Media Process Image Assets]** step uses the image server to generate thumbnails, independently of the configuration applied to the **[!UICONTROL Process Thumbnails]** step. Generating thumbnails through the **[!UICONTROL Process Thumbnails]** step is the slowest and most memory intensive way to create thumbnails.

Thumbnail sizing is defined in the following format: **[!UICONTROL width:height:center]**, for example, `80:80:false`. The width and height determine the size in pixels of the thumbnail. The center value is either false or true. If set to true, it indicates that the thumbnail image has exactly the size given in the configuration. If the resized image is smaller, it is centered within the thumbnail.

>[!NOTE]
>
>* Thumbnail sizes for EPS files are configured in the **[!UICONTROL EPS thumbnails]** step, in the **[!UICONTROL Arguments]** tab under Thumbnails.
>
>* Thumbnail sizes for videos are configured in the **[!UICONTROL FFmpeg thumbnails]** step, in the **[!UICONTROL Process]** tab under **[!UICONTROL Arguments]**.
>

**To configure the image thumbnail size:**

1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** > **[!UICONTROL DAM Update Asset]** > **[!UICONTROL Edit]**.
1. Select the **[!UICONTROL Dynamic Media Process Image Assets]** step and select the **[!UICONTROL Thumbnails]** tab. Change the thumbnail size, as needed, then select **[!UICONTROL OK]**.

   ![6_5_dynamicmediaprocessimageassets-thumbnailstab](assets/6_5_dynamicmediaprocessimageassets-thumbnailstab.png)

1. Select the **[!UICONTROL Process Thumbnails]** step, then select the **[!UICONTROL Thumbnails]** tab. Change the thumbnail size, as needed, then select **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >The values in the thumbnails argument in the **[!UICONTROL Process Thumbnails]** step must match the thumbnails argument in the **[!UICONTROL Dynamic Media Process Image Assets]** step.

1. Select **[!UICONTROL Save]** to save the changes to the workflow.
-->

## Het aantal weergegeven voorinstellingen voor afbeeldingen vergroten of verkleinen {#increasing-or-decreasing-the-number-of-image-presets-that-display}

Afbeeldingsvoorinstellingen die u maakt, zijn beschikbaar als dynamische uitvoeringen wanneer u een voorvertoning van elementen weergeeft. Experience Manager geeft verschillende dynamische uitvoeringen weer wanneer een element wordt weergegeven vanuit **[!UICONTROL Detail View > Renditions]** . U kunt de limiet van weergegeven uitvoeringen verhogen of verlagen.

**om het aantal beeld te verhogen of te verminderen stelt die worden getoond:**

1. Navigeer aan CRXDE Lite ([&#x200B; https://localhost :4502/crx/de &#x200B;](https://localhost:4502/crx/de)).
1. Navigeer naar het knooppunt met vooraf ingestelde lijsten voor afbeeldingen op `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist`

   ![&#x200B; verhogings_reduction ethenumberofimagepresetsthatdisplay &#x200B;](assets/increase_decreasethenumberofimagepresetsthatdisplay.png)

1. Wijzig in de eigenschap **[!UICONTROL limit]** de **[!UICONTROL Value]**, die standaard op 15 is ingesteld, in het gewenste getal.
1. Navigeer naar de gegevensbron voor de afbeeldingsvoorinstelling op `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist/datasource`

   ![&#x200B; chlimage_1-495 &#x200B;](assets/chlimage_1-495.png)

1. Wijzig in de eigenschap limit het getal in het gewenste getal, bijvoorbeeld `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. Selecteer **[!UICONTROL Save All]** .

## Voorinstellingen afbeelding maken {#creating-image-presets}

Maak voorinstellingen voor afbeeldingen, zodat u instellingen consistent kunt toepassen op alle afbeeldingen wanneer u een voorvertoning weergeeft of publiceert.

>[!NOTE]
>
>Als u Internet Explorer 9 gebruikt, wordt het maken van een voorinstelling niet meteen na het opslaan weergegeven in de lijst met voorinstellingen. U kunt dit probleem omzeilen door de cache voor IE9 uit te schakelen.

Als u de opname van AI-, PDF- en EPS-bestanden wilt ondersteunen, zodat u een dynamische uitvoering van deze bestandsindelingen kunt genereren, bekijkt u de volgende informatie voordat u Voorinstellingen voor afbeeldingen maakt.

Zie [&#x200B; Adobe Illustrator (AI), PostScript® (EPS), en de dossierformaten van PDF &#x200B;](#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats).

Als u de opname van INDD-bestanden wilt ondersteunen, zodat u dynamische uitvoering van deze bestandsindeling kunt genereren, controleert u de volgende informatie voordat u Voorinstellingen afbeelding maakt.

Zie [&#x200B; InDesign (INDD) dossierformaat &#x200B;](#indesign-indd-file-format).

**om beeld tot stand te brengen vooraf instelt:**

1. Selecteer in Experience Manager het Experience Manager-logo voor toegang tot de algemene navigatieconsole en ga vervolgens naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Presets]** .
1. Selecteer **[!UICONTROL Create]** .

   ![&#x200B; chlimage_1-496 &#x200B;](assets/chlimage_1-496.png)

   >[!NOTE]
   >
   >Als u deze voorinstelling afbeelding responsief wilt maken, wist u de waarden in de velden **[!UICONTROL width]** en **[!UICONTROL height]** en laat u deze leeg.

1. Voer in het venster **[!UICONTROL Edit Image Preset]** waar nodig waarden in op de tabbladen **[!UICONTROL Basic]** en **[!UICONTROL Advanced]** , inclusief een naam. De opties worden beschreven in [Opties voor afbeeldingsvoorinstellingen](#image-preset-options). Voorinstellingen worden weergegeven in het linkerdeelvenster en kunnen direct samen met andere assets worden gebruikt.

   ![&#x200B; 6_5_imagepreset-geef uit &#x200B;](assets/6_5_imagepreset-edit.png)

1. Selecteer **[!UICONTROL Save]** .

## Een responsieve voorinstelling voor afbeeldingen maken {#creating-a-responsive-image-preset}

Om een ontvankelijke Vooraf ingesteld Beeld tot stand te brengen, voer de stappen in [&#x200B; tot beeld uit vooraf instelt &#x200B;](#creating-image-presets). Wanneer u de hoogte en breedte in het **[!UICONTROL Edit Image Preset]** -venster invoert, wist u de waarden en laat u deze leeg.

Als u deze leeg laat, weet Experience Manager dat op deze voorinstelling kan worden gereageerd. U kunt de andere waarden desgewenst aanpassen.

>[!NOTE]
>
>Als u de knoppen **[!UICONTROL URL]** en **[!UICONTROL RESS]** wilt zien wanneer u een voorinstelling voor afbeelding op een element toepast, moet het element worden gepubliceerd.
>
>![&#x200B; chlimage_1-79 &#x200B;](assets/chlimage_1-498.png)
>
>Voorinstellingen voor afbeeldingen en afbeeldingselementen worden automatisch gepubliceerd.

### Voorinstellingsopties voor afbeelding {#image-preset-options}

Wanneer u voorinstellingen voor afbeeldingen maakt of bewerkt, worden de opties in deze sectie beschreven. Daarnaast raadt Adobe aan om de volgende opties voor best practices te kiezen:

* **[!UICONTROL Format]** (**[!UICONTROL Basic]** tab) - Selecteer **[!UICONTROL JPEG]** of een andere indeling die aan uw vereisten voldoet. Alle webbrowsers ondersteunen de JPEG-afbeeldingsindeling. Deze biedt een goede balans tussen kleine bestandsgrootten en afbeeldingskwaliteit. JPEG-afbeeldingen gebruiken echter een compressieschema met dataverlies dat ongewenste afbeeldingsartefacten kan veroorzaken als de compressie-instelling te laag is. Daarom raadt Adobe aan de compressiekwaliteit in te stellen op 75. Deze instelling biedt een goede balans tussen afbeeldingskwaliteit en kleine bestandsgrootte.

* **[!UICONTROL Enable Simple Sharpening]** - Niet selecteren **[!UICONTROL Enable Simple Sharpening]** (dit verscherpingsfilter biedt minder controle dan de instellingen voor onscherpe maskering).

* **[!UICONTROL Sharpening: Resampling Mode]** - Selecteer **[!UICONTROL Sharp2]** .

### Opties op het tabblad Standaard {#basic-tab-options}

| Veld | Beschrijving |
| --- | --- |
| **Naam** | Voer een beschrijvende naam in zonder spaties. Als u gebruikers wilt helpen deze voorinstelling voor afbeeldingen te identificeren, neemt u de specificatie voor de afbeeldingsgrootte op in de naam. |
| **Breedte en Hoogte** | Voer in pixels de grootte in waarmee de afbeelding wordt geleverd. De breedte en hoogte moeten groter zijn dan 0 pixels. Als een van deze waarden 0 is, wordt geen voorinstelling gemaakt. Als beide waarden leeg zijn, wordt een responsieve voorinstelling voor afbeeldingen gemaakt. |
| **Formaat** | Kies een indeling in het menu.<br> het kiezen van **JPEG** biedt de volgende andere opties aan:<br>・ **Kwaliteit** - de de kwaliteitsschaal van JPEG is 1-100. De schaal is zichtbaar wanneer u de schuifregelaar versleept.<br>・ **laat de Downsampling van de Chrominantie van JPG** toe - omdat het oog minder gevoelig aan high-frequency kleureninformatie dan high-frequency luminantie is, verdelen de beelden van JPEG beeldinformatie in helderheid en kleurencomponenten. Wanneer een JPEG-afbeelding wordt gecomprimeerd, blijft de luminantiecomponent op volledige resolutie staan, terwijl de kleurcomponenten worden gedownsampled door het gemiddelde te nemen van groepen pixels. Met downsampling verlaagt u het gegevensvolume tot een halve of een derde, met minimale gevolgen voor de waargenomen kwaliteit. Downsampling is niet van toepassing op grijswaardenafbeeldingen. Met deze techniek vermindert u de hoeveelheid compressie die handig is voor afbeeldingen met veel contrast (bijvoorbeeld afbeeldingen met overlappende tekst).<br><br> het kiezen van **GIF** of **GIF met alpha** verstrekt deze extra **Kwantiserings van de Kleur van GIF** opties:<br>・ **Type** - Uitgezocht **Aangepast** (gebrek), **Web**, of **Macintosh**. Als u **GIF met Alpha** selecteert, is de optie van Macintosh niet beschikbaar.<br>・ **Dithering** - selecteer **Onscherp** of **weg**.<br>・ **Aantal Kleuren** - ga een aantal 2 in - 256.<br>・ **Lijst van de Kleur** - ga een komma-gescheiden lijst in. Voer bijvoorbeeld voor wit, grijs en zwart `000000,888888,ffffff` in.<br><br> het kiezen van **PDF**, **TIFF**, of **TIFF met alpha** verstrekt deze extra optie:<br>・ **Compressie** - selecteer een compressiealgoritme. De opties van het algoritme voor PDF zijn **niets**, **Zip**, en **Jpeg**; voor TIFF zijn zij **niets**, **LZW**, **Jpeg**, en **Zip**; en voor TIFF met Alpha zijn **niets. 5&rbrace;,** LZW **, en** Zip **.**<br><br> het kiezen van **PNG**, **PNG met Alpha**, of **EPS** verstrekt geen extra opties. |
| **Verscherpen** | Selecteer **toelaten Eenvoudig het Verscherpen** om een basis het scherpen filter op het beeld toe te passen nadat al het schrapen plaatsvindt. Verscherpen kan helpen de vervaging te compenseren die kan optreden wanneer u een afbeelding met een andere grootte weergeeft. |

### Opties op het tabblad Geavanceerd {#advanced-tab-options}

<table>
 <tbody>
  <tr>
   <td><strong>Veld</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td><strong>Kleurruimte</strong></td>
   <td>Selecteer <strong> RGB, CMYK, </strong> of <strong> Grijswaarde </strong> voor de kleurenruimte.</td>
  </tr>
  <tr>
   <td><strong>Kleurprofiel</strong></td>
   <td>Selecteer het kleurruimteprofiel van de uitvoer waarnaar u het element wilt converteren als dit afwijkt van het werkprofiel.</td>
  </tr>
  <tr>
   <td><strong>Render-intentie</strong></td>
   <td>U kunt de standaard rendering intent overschrijven. Render-intenties bepalen wat er gebeurt met kleuren die niet in het doelkleurprofiel kunnen worden gereproduceerd (buiten kleuromvang). De render-intentie wordt genegeerd als deze niet compatibel is met het ICC-profiel.
    <ul>
     <li>Selecteer <strong> Perceptueel </strong> om de totale kleuromvang van één kleurenruimte in een andere kleurenruimte te comprimeren wanneer één of meerdere kleuren in het originele beeld uit de kleuromvang van de ruimte van de bestemmingskleur is.</li>
     <li>Selecteer <strong> Relatief colorimetrisch </strong> wanneer een kleur in de huidige kleurenruimte uit gamut in de ruimte van de doelkleur is. En u wilt deze toewijzen aan de dichtstbijzijnde doelkleuromvang zonder andere kleuren te wijzigen. </li>
     <li>Selecteer <strong> Verzadiging </strong> als u de originele verzadiging van de beeldkleur wilt reproduceren wanneer het omzetten in de ruimte van de doelkleur. </li>
     <li>Selecteer <strong> Absoluut colorimetrisch </strong> om kleuren precies met geen aanpassing voor witte punt of zwartpunt aan te passen die de helderheid van het beeld zouden veranderen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Compensatie zwartpunt</strong></td>
   <td>Selecteer deze optie als het uitvoerprofiel deze functie ondersteunt. Zwartpuntcompensatie wordt genegeerd als deze niet compatibel is met het opgegeven ICC-profiel.</td>
  </tr>
  <tr>
   <td><strong>Dithering</strong></td>
   <td>Selecteer deze optie om mogelijke kleurovergangen te voorkomen of te verminderen. </td>
  </tr>
  <tr>
   <td><strong>Verscherpingstype</strong></td>
   <td><p>Selecteer <strong> niets </strong>, <strong> verscherpt </strong>, of <strong> Onscherp Masker </strong>. </p>
    <ul>
     <li>Selecteer <strong> niets </strong> als u het scherpen wilt onbruikbaar maken.</li>
     <li>Selecteer <strong> verscherpen </strong> om een basis het scherpen filter op het beeld toe te passen nadat al het schrapen plaatsvindt. Verscherpen kan helpen de vervaging te compenseren die kan optreden wanneer u een afbeelding met een andere grootte weergeeft. </li>
     <li>Selecteer <strong> Onscherp Masker </strong> als u een het verscherpen filtereffect op het definitieve gedownsampled beeld wilt verfijnen. U kunt de intensiteit van het effect, de straal van het effect (gemeten in pixels) en een drempel voor contrast instellen die wordt genegeerd. Voor dit effect worden dezelfde opties gebruikt als voor het filter Onscherp masker in Photoshop.</li>
    </ul> <p>In <strong> Onscherp Masker </strong>, hebt u de volgende opties:</p>
    <ul>
     <li><strong> Hoeveelheid </strong> - controleert de hoeveelheid contrast die op randpixel wordt toegepast. De standaardwaarde voor het reële getal is 1,0. Voor afbeeldingen met een hoge resolutie kunt u de resolutie verhogen tot 5,0. Beschouw Hoeveelheid als een maat voor de filterintensiteit.</li>
     <li><strong> Straal </strong> - bepaalt het aantal pixel die de randpixel omringen die het scherpen beïnvloeden. Voer voor afbeeldingen met een hoge resolutie een getal in tussen 1 en 2. Met een lage waarde worden alleen de randpixels verscherpt; met een hoge waarde wordt een bredere reeks pixels verscherpt. De juiste waarde is afhankelijk van de grootte van de afbeelding.</li>
     <li><strong> Drempel </strong> - bepaalt de waaier van contrast om te negeren wanneer de filter van het Masker Unsharp wordt toegepast. Met andere woorden, met deze optie bepaalt u hoeveel verscherpte pixels moeten verschillen van het omringende gebied om als randpixels te worden beschouwd en te worden verscherpt. Experimenteer met gehele getallen tussen 2 en 20 om ruis te voorkomen. </li>
     <li><strong> is op </strong> van toepassing - bepaalt of unsharpening op elke kleur of helderheid van toepassing is.</li>
    </ul>
    <div>
      Verscherpen wordt beschreven in
     <a href="https://experienceleague.adobe.com/nl/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use#dynamic-media"> Gebruikend Beeld dat met Experience Manager Dynamische Media </a> video verscherpt, in <a href="https://experienceleague.adobe.com/nl/docs/dynamic-media-classic/using/master-files/sharpening-image#master-files"> het verscherpen van een beeld </a> online Help onderwerp, en in <a href="https://experienceleague.adobe.com/docs/dynamic-media-classic/assets/s7_sharpening_images.pdf?lang=nl-NL"> Beste praktijken voor het verscherpen van beelden in Dynamic Media Classic </a> downloadbare PDF.
    </div> </td>
  </tr>
  <tr>
   <td><strong>Modus voor nieuwe pixels</strong></td>
   <td>Selecteer a <strong> het Nieuw stalen nemen van wijze </strong> optie. Met deze opties verscherpt u de afbeelding wanneer deze wordt gedownsampled:
    <ul>
     <li><strong> bi-Lineair </strong> - de snelste het resampling methode. Sommige aliasingartefacten zijn waarneembaar.</li>
     <li><strong> bi-Cubic </strong> - Verhoogt het gebruik van CPU maar produceert scherpere beelden met minder merkbare aliasing artefacten.</li>
     <li><strong> Sharp2 </strong> - kan lichtjes scherpere resultaten veroorzaken dan bi-Cubic, maar aan een nog hogere kosten van CPU.</li>
     <li><strong> bi-Sharp </strong> - Selecteert Photoshop gebrek resampler voor het verminderen van beeldgrootte, die <strong> bicubische scherper </strong> in Adobe Photoshop wordt genoemd.</li>
     <li><strong> Elke Kleur </strong> en <strong> Helderheid </strong> - elke methode kan op kleur of helderheid worden gebaseerd. Door gebrek <strong> wordt Elke Kleur </strong> geselecteerd.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Afdrukresolutie</strong></td>
   <td>Selecteer een resolutie voor het afdrukken van deze afbeelding; 72 pixels is de standaardinstelling.</td>
  </tr>
  <tr>
   <td><strong>Afbeelding wijzigen</strong></td>
   <td><p>Buiten de gemeenschappelijke beeldmontages beschikbaar in UI, steunt de Dynamische Media talrijke geavanceerde beeldwijzigingen die u in het <strong> gebied van de Modifiers van het Beeld </strong> kunt specificeren. Deze parameters worden bepaald in de <a href="https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/syntax-and-features/image-serving-http/c-command-overview"> het bevelverwijzing van het Protocol van de Server van het Beeld </a>.</p> <p>Belangrijk: de volgende functionaliteit die in de API wordt vermeld, wordt niet ondersteund:</p>
    <ul>
     <li>Standaardopdrachten voor sjablonen en tekstrendering: <code>text= textAngle= textAttr= textFlowPath= textFlowXPath= textPath=</code> en <code>textPs=</code></li>
     <li>Localisatie-opdrachten: <code>locale=</code> en <code>req=xlate</code></li>
     <li><code>req=set</code> is niet beschikbaar voor algemeen gebruik.</li>
     <li><code>req=mbrset</code></li>
     <li><code>req=saveToFile</code></li>
     <li><code>req=targets</code></li>
     <li><code>template=</code></li>
     <li>Niet-core Dynamic Media-services: SVG, Afbeeldingen renderen en Web-to-Print</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Voorinstellingsopties voor afbeeldingen definiëren met afbeeldingsopties {#defining-image-preset-options-with-image-modifiers}

Naast de opties op de tabbladen Standaard en Geavanceerd kunt u ook afbeeldingsopties definiëren waarmee u meer opties hebt bij het definiëren van voorinstellingen voor afbeeldingen. Het beeld dat op het Dynamische Beeld teruggeeft van Media baseert API en in detail in de [&#x200B; Verwijzing van het Protocol van HTTP &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources/image-serving-api/image-rendering-api/http-protocol-reference/c-ir-introduction#image-rendering-api) wordt bepaald.

Hieronder volgen enkele basisvoorbeelden van wat u kunt doen met wijzigingstoetsen voor afbeeldingen.

>[!NOTE]
>
>Sommige beeldbepalingen [&#x200B; kunnen niet in Experience Manager &#x200B;](#advanced-tab-options) worden gebruikt.

* [&#x200B; op_invert &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-invert) - keert elke kleurencomponent voor een negatief beeldeffect om.

  ```xml {.line-numbers}
  &op_invert=1
  ```

  ![&#x200B; 6_5_imagepreset-edit-invert &#x200B;](assets/6_5_imagepreset-edit-invert.png)

* [&#x200B; op_blur &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-blur) - past een vervagend filter op het beeld toe.

  ```xml {.line-numbers}
  &op_blur=7
  ```

  ![&#x200B; 6_5_imagepreset-geef-onduidelijk &#x200B;](assets/6_5_imagepreset-edit-blur.png)

* Gecombineerde opdrachten - op_vervagen en op-omkeren

  ```xml {.line-numbers}
  &op_invert=1&op_blur=7
  ```

  ![&#x200B; chlimage_1-80 &#x200B;](assets/chlimage_1-501.png)

* [&#x200B; op_brightness &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-brightness) - vermindert of verhoogt de helderheid.

  ```xml {.line-numbers}
  &op_brightness=58
  ```

  ![&#x200B; 6_5_imagepreset-geef-helderheid uit &#x200B;](assets/6_5_imagepreset-edit-brightness.png)

* [&#x200B; opac &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-opac) - Past beelddekking aan. Hiermee kunt u de dekking van de voorgrond verlagen.

  ```xml {.line-numbers}
  opac=29
  ```

  ![&#x200B; 6_5_imagepreset-geef-opacity &#x200B;](assets/6_5_imagepreset-edit-opacity.png)

## Voorinstellingen voor afbeeldingen bewerken {#modifying-image-presets}

1. Selecteer in Experience Manager het Experience Manager-logo voor toegang tot de algemene navigatieconsole en ga vervolgens naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Presets]** .

   ![&#x200B; 6_5_imagepreset-editpreset &#x200B;](assets/6_5_imagepreset-editpreset.png)

1. Selecteer een voorinstelling en selecteer vervolgens **[!UICONTROL Edit]** . Het venster **[!UICONTROL Edit Image Preset]** wordt geopend.
1. Breng de wijzigingen aan en selecteer **[!UICONTROL Save]** om de wijzigingen op te slaan of **[!UICONTROL Cancel]** om de wijzigingen te annuleren.

## Voorinstellingen voor afbeeldingen publiceren {#publishing-image-presets}

Voorinstellingen voor afbeeldingen worden automatisch voor u gepubliceerd.

## Afbeeldingsvoorinstellingen verwijderen {#deleting-image-presets}

1. Selecteer in Experience Manager het Experience Manager-logo voor toegang tot de algemene navigatieconsole en selecteer het pictogram Extra.
1. Ga naar **[!UICONTROL Assets]** > **[!UICONTROL Image Presets]**.
1. Selecteer een voorinstelling en selecteer vervolgens **[!UICONTROL Delete]** . Dynamische media bevestigen dat u deze wilt verwijderen. Selecteer **[!UICONTROL Delete]** om **[!UICONTROL Cancel]** te verwijderen of te selecteren om terug te keren naar Voorinstellingen afbeelding.
