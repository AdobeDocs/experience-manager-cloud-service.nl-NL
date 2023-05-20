---
title: Voorinstellingen afbeelding beheren
description: Meer informatie over voorinstellingen voor afbeeldingen en over het maken, wijzigen en beheren van voorinstellingen voor afbeeldingen.
contentOwner: Rick Brough
feature: Image Presets,Viewers,Renditions
role: User
exl-id: a53f40ab-0e27-45f8-9142-781c077a04cc
source-git-commit: b37ff72dbcf85e5558eb3421b5168dc48e063b47
workflow-type: tm+mt
source-wordcount: '3499'
ht-degree: 6%

---

# Voorinstellingen afbeelding beheren{#managing-image-presets}

Met voorinstellingen voor afbeeldingen kunnen Adobe Experience Manager-elementen dynamisch afbeeldingen van verschillende grootten, in verschillende indelingen of met andere afbeeldingseigenschappen leveren die dynamisch worden gegenereerd. Elke voorinstelling voor afbeeldingen vertegenwoordigt een vooraf gedefinieerde verzameling opdrachten voor het vergroten of verkleinen en opmaken van afbeeldingen. Wanneer u een voorinstelling voor afbeeldingen maakt, kiest u een grootte voor het leveren van de afbeelding. U kiest ook opmaakopdrachten, zodat de weergave van de afbeelding wordt geoptimaliseerd wanneer de afbeelding wordt geleverd voor weergave.

Beheerders kunnen voorinstellingen maken voor het exporteren van elementen. Gebruikers kunnen bij het exporteren van afbeeldingen een voorinstelling kiezen die de afbeeldingen opnieuw opmaakt volgens de specificaties die de beheerder heeft opgegeven.

U kunt ook voorinstellingen voor afbeeldingen maken die reageren. Als u een voorinstelling voor een responsieve afbeelding toepast op uw elementen, worden deze afhankelijk van het apparaat of de schermgrootte waarop ze worden weergegeven. U kunt afbeeldingsvoorinstellingen zo configureren dat naast RGB of Grijs ook CMYK in de kleurruimte wordt gebruikt.

In deze sectie wordt beschreven hoe u voorinstellingen voor afbeeldingen maakt, wijzigt en over het algemeen beheert. U kunt een voorinstelling voor afbeeldingen op elk gewenst moment op een afbeelding toepassen. Zie [Voorinstellingen afbeelding toepassen](/help/assets/dynamic-media/image-presets.md).

>[!NOTE]
>
>Slimme beeldverwerking werkt met bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie tijdens de laatste milliseconde van levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding. Zie [Slimme afbeeldingen](/help/assets/dynamic-media/imaging-faq.md) voor meer informatie .

## Meer informatie over voorinstellingen voor afbeeldingen {#understanding-image-presets}

Net als bij een macro is een voorinstelling voor afbeeldingen een vooraf gedefinieerde verzameling opdrachten voor het vergroten of verkleinen en opmaken van de grootte die onder een naam zijn opgeslagen. Als u wilt weten hoe Voorinstellingen afbeelding werken, veronderstelt u dat elke productafbeelding op uw website moet worden weergegeven in verschillende formaten, formaten en compressiesnelheden voor levering op het bureaublad en op mobiele apparatuur.

U kunt twee voorinstellingen voor afbeeldingen maken: één met 500 x 500 pixels voor desktopversie en 150 x 150 pixels voor de mobiele versie. U maakt twee voorinstellingen voor afbeeldingen, die u één voorinstelling noemt `Enlarge` om afbeeldingen weer te geven op 500 x 500 pixels en één aangeroepen afbeelding `Thumbnail` om afbeeldingen weer te geven op 150 x 150 pixels. Als u afbeeldingen wilt leveren op de `Enlarge` en `Thumbnail` grootte, vindt de Experience Manager de definitie van de Voorinstelling Afbeelding vergroten en Voorinstelling miniatuurafbeelding. Vervolgens genereert Experience Manager dynamisch een afbeelding met de grootte en opmaakspecificaties van elke voorinstelling voor afbeeldingen.

Afbeeldingen die bij dynamische levering kleiner worden gemaakt, kunnen scherper en gedetailleerder worden. Daarom bevat elke voorinstelling voor afbeeldingen opmaakbesturingselementen waarmee u een afbeelding kunt optimaliseren wanneer deze met een bepaalde grootte wordt geleverd. Met deze besturingselementen zorgt u ervoor dat uw afbeeldingen scherp en duidelijk zijn wanneer ze aan uw website of toepassing worden geleverd.

Beheerders kunnen voorinstellingen voor afbeeldingen maken. Als u een voorinstelling voor een afbeelding wilt maken, begint u helemaal opnieuw of u kunt een bestaande voorinstelling beginnen en opslaan onder een andere naam.

## Voorinstellingen afbeelding beheren {#managing-image-presets-1}

U beheert de voorinstellingen voor afbeeldingen in Experience Manager door het logo van de Experience Manager te selecteren voor toegang tot de algemene navigatieconsole en vervolgens het pictogram Extra te selecteren en naar **[!UICONTROL Assets]** > **[!UICONTROL Image Presets]**.

![6_5_tools-assets-imagepresets](assets/6_5_tools-assets-imagepresets.png)

>[!NOTE]
>
>Alle afbeeldingsvoorinstellingen die u maakt, zijn ook beschikbaar als dynamische uitvoeringen wanneer u elementen voorvertoont of levert.
>
>U doet dat *niet* moeten voorinstellingen voor afbeeldingen publiceren als voorinstellingen voor afbeeldingen automatisch worden gepubliceerd.
>
>Zie [Voorinstellingen afbeelding publiceren](#publishing-image-presets).

>[!NOTE]
>
>Het systeem toont verschillende vertoningen wanneer u selecteert **[!UICONTROL Renditions]** in de detailweergave van een element. U kunt het aantal voorinstellingen voor afbeeldingen dat wordt weergegeven, verhogen of verlagen. Zie [Het aantal weergegeven voorinstellingen voor afbeeldingen vergroten](#increasing-or-decreasing-the-number-of-image-presets-that-display).

### Adobe Illustrator- (AI), PostScript®- (EPS) en PDF-bestandsindelingen {#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats}

Als u de opname van AI-, EPS- en PDF-bestanden wilt ondersteunen, zodat u dynamische uitvoeringen van deze bestandsindelingen kunt genereren, controleert u de volgende informatie voordat u voorinstellingen voor afbeeldingen maakt.

Adobe Illustrator-bestandsindeling is een variant van PDF. De belangrijkste verschillen in Experience Manager Assets zijn:

* Adobe Illustrator-documenten bestaan uit één pagina met meerdere lagen. Elke laag wordt geëxtraheerd als een PNG-subelement onder het Illustrator-hoofdelement.
* PDF-documenten bestaan uit een of meer pagina&#39;s. Elke pagina wordt geëxtraheerd als een PDF-subelement van één pagina onder het PDF-hoofddocument met meerdere pagina&#39;s.

De subassets worden gemaakt door de `Create Sub Asset process` binnen het algemene `DAM Update Asset` workflow. Als u deze procescomponent wilt weergeven in de workflow, navigeert u naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** > **[!UICONTROL DAM Update Asset]** > **[!UICONTROL Edit]**.

<!-- See also [Viewing pages of a multi-page file](/help/assets/manage-linked-subassets.md#view-pages-of-a-multi-page-file). -->

U kunt de submiddelen of de pagina&#39;s bekijken wanneer u het element opent, het menu Inhoud selecteert en **[!UICONTROL Subassets]** of **[!UICONTROL Pages]**. De subelementen zijn echte elementen. Met andere woorden: PDF-pagina&#39;s worden geëxtraheerd door de `Create Sub Asset` workflowcomponent. Zij worden dan opgeslagen zoals `page1.pdf`, `page2.pdf`, enzovoort, onder het hoofdactief. Nadat de `DAM Update Asset` deze werkstromen verwerken.

Als u Dynamic Media wilt gebruiken om dynamische uitvoeringen voor AI-, EPS- of PDF-bestanden voor te vertonen en te genereren, moet u de volgende verwerkingsstappen uitvoeren:

1. In de `DAM Update Asset` werkschema, de `Rasterize PDF/AI Image Preview Rendition` procescomponent rasterizes de eerste pagina van origineel element-gebruikend gevormde resolutie-in `cqdam.preview.png` uitvoering.

1. De `cqdam.preview.png` uitvoering wordt vervolgens geoptimaliseerd in een PTIFF door de `Dynamic Media Process Image Assets` in de workflow.

>[!NOTE]
>
>In de workflow Asset-updates van DAM worden miniaturen voor EPS-bestanden gegenereerd in de stap **[!UICONTROL EPS thumbnails]**.

#### Eigenschappen van PDF/AI/EPS-metagegevens {#pdf-ai-eps-asset-metadata-properties}

| **Eigenschap Metadata** | **Beschrijving** |
|---|---|
| dam:Physicalwidthinches | Documentbreedte in inches. |
| dam:Physicalheightininches | Documenthoogte in inches. |

U hebt toegang tot `Rasterize PDF/AI Image Preview Rendition` procescomponentopties als `DAM Update Asset` workflow.

Selecteer Adobe Experience Manager in de linkerbovenhoek, navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**. Selecteer op de pagina Workflowmodellen **[!UICONTROL DAM Update Asset]** selecteert u vervolgens op de werkbalk **[!UICONTROL Edit]**. Dubbeltik op de pagina met DAM Update Asset-workflows op `Rasterize PDF/AI Image Preview Rendition` procescomponent om het dialoogvenster Step Properties te openen.

#### Opties van PDF/AI-voorvertoning van afbeelding omzetten in pixels {#rasterize-pdf-ai-image-preview-rendition-options}

![Argumenten voor het rasteren van PDF- of AI-workflow](assets/rasterize_pdf_ai_image_preview.png)

Argumenten voor het rasteren van PDF- of AI-workflow

| Procesargument | Standaardinstelling | Beschrijving |
|---|---|---|
| MIME-typen | application/pdf<br>application/postscript<br>toepassing/illustrator | Lijst met documentmime-typen die worden beschouwd als PDF- of Illustrator-documenten. |
| Max. breedte | 2048 | Maximale breedte van de gegenereerde voorvertoning, in pixels. |
| Max. hoogte | 2048 | Maximumhoogte van de gegenereerde voorvertoning, in pixels. |
| Resolutie | 72 | Resolutie voor het rasteren van de eerste pagina, in ppi (pixels per inch). |

Met de standaardprocesargumenten wordt de eerste pagina van een PDF/AI-document gerasterd met 72 ppi en de gegenereerde voorvertoning met een grootte van 2048 x 2048 pixels. Voor een gebruikelijke implementatie kunt u de resolutie verhogen tot minimaal 150 ppi of meer. Een document met een tekengrootte van 300 ppi in de VS vereist bijvoorbeeld een maximale breedte en hoogte van respectievelijk 2550 x 3300 pixels.

Met Maximale breedte en Maximumhoogte kunt u de resolutie beperken waarbij rasteren wordt beperkt. Als de maximale waarden bijvoorbeeld ongewijzigd blijven en de resolutie is ingesteld op 300 ppi, wordt een US Letter-document gerasterd naar 186 ppi. Het document is dus 1581 x 2046 pixels.

De `Rasterize PDF/AI Image Preview Rendition` procescomponent heeft een maximum gedefinieerd om ervoor te zorgen dat er geen te grote afbeeldingen in het geheugen worden gemaakt. Zulke grote afbeeldingen kunnen het geheugen overlopen dat aan de JVM (Java™ Virtual Machine) wordt geleverd. Er moet op worden gelet dat de JVM over voldoende geheugen beschikt om het geconfigureerde aantal parallelle workflows te beheren, waarbij elk van beide de mogelijkheid heeft om een image op de maximaal geconfigureerde grootte te maken.

### InDesign-bestandsindeling (INDD) {#indesign-indd-file-format}

Als u de opname van INDD-bestanden wilt ondersteunen, zodat u dynamische uitvoering van deze bestandsindeling kunt genereren, controleert u de volgende informatie voordat u voorinstellingen voor afbeeldingen maakt.

Voor InDesign-bestanden worden subelementen alleen geëxtraheerd als de Adobe InDesign Server is geïntegreerd met Experience Manager. Elementen waarnaar wordt verwezen, zijn gekoppeld op basis van hun metagegevens. InDesign Server is niet vereist voor koppelingen. De middelen waarnaar wordt verwezen, moeten echter aanwezig zijn in de Experience Manager voordat de InDesign-bestanden worden verwerkt, zodat de koppelingen tussen de InDesign-bestanden en de bestanden waarnaar wordt verwezen, worden gemaakt.

<!-- See [Integrate Experience Manager Assets with InDesign Server](/help/assets/indesign.md). -->

De procescomponent Media Extraction in het dialoogvenster `DAM Update Asset` in de werkstroom worden verschillende vooraf geconfigureerde Extend Scripts uitgevoerd om InDesign-bestanden te verwerken.

![De ExtendScript-paden in de argumenten van Media Extraction-proces](/help/assets/dynamic-media/assets/6_5_mediaextractionprocess.png)

De ExtendScript-paden in de argumenten van Media Extraction Process-component in de DAM Update Asset-workflow.

De volgende scripts worden door Dynamic Media-integratie gebruikt:


| ExtendScript-naam | Standaard | Beschrijving |
|---|---|---|
| ThumbnailExport.jsx | Ja | Genereert een 300 PPI `thumbnail.jpg` uitvoering die is geoptimaliseerd en door `Dynamic Media Process Image Assets` procescomponent. |
| JPEGPagesExport.jsx | Ja | Genereert een subelement van 300 ppi JPEG voor elke pagina. Het JPEG-subelement is een echt middel dat is opgeslagen onder het InDesign-element. Het wordt ook geoptimaliseerd en door de `DAM Update Asset` workflow. |
| PDFPagesExport.jsx | Nee | Hiermee genereert u een PDF-subelement voor elke pagina. Het PDF-subelement wordt verwerkt zoals eerder beschreven. Omdat de PDF slechts één pagina bevat, worden geen subelementen gegenereerd. |

### Miniatuurgrootte van afbeelding configureren {#configuring-image-thumbnail-size}

U kunt de grootte van miniaturen configureren door deze instellingen te configureren in het dialoogvenster **[!UICONTROL DAM Update Asset]** workflow. De workflow bevat twee stappen waarmee u de miniatuurgrootte van afbeeldingselementen kunt configureren. Eén (**[!UICONTROL Dynamic Media Process Image Assets]**) wordt gebruikt voor dynamische afbeeldingselementen. De andere (**[!UICONTROL Process Thumbnails]**) wordt gebruikt voor het genereren van statische miniaturen of wanneer bij alle andere processen geen miniaturen worden gegenereerd. Ongeacht de instelling *beide* moeten dezelfde instellingen hebben.

Met de stap **[!UICONTROL Dynamic Media Process Image Assets]** worden miniaturen gegenereerd door de afbeeldingsserver en deze configuratie is onafhankelijk van de configuratie die op de stap **[!UICONTROL Process Thumbnails]** is toegepast. Het genereren van miniaturen via de stap **[!UICONTROL Process Thumbnails]** is de langzaamste en meest geheugenintensieve manier om miniaturen te maken.

Miniatuurgrootte wordt gedefinieerd in de volgende indeling: **[!UICONTROL width:height:center]** bijvoorbeeld `80:80:false`. De breedte en hoogte bepalen de grootte in pixels van de miniatuur. De middelste waarde is onwaar of onwaar. Indien true, geeft dit aan dat de miniatuurafbeelding exact de grootte heeft die in de configuratie is opgegeven. Als de gewijzigde afbeelding kleiner is, wordt deze gecentreerd in de miniatuur.

>[!NOTE]
>
>* Miniatuurgrootten voor EPS-bestanden worden geconfigureerd in het dialoogvenster **[!UICONTROL EPS thumbnails]** stap, in de **[!UICONTROL Arguments]** onder Miniaturen.
>
>* Miniatuurgrootten voor video&#39;s worden geconfigureerd in het dialoogvenster **[!UICONTROL FFmpeg thumbnails]** stap, in de **[!UICONTROL Process]** tab onder **[!UICONTROL Arguments]**.
>


**De grootte van afbeeldingsminiaturen configureren:**

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** > **[!UICONTROL DAM Update Asset]** > **[!UICONTROL Edit]**.
1. Selecteer **[!UICONTROL Dynamic Media Process Image Assets]** stap en selecteer de **[!UICONTROL Thumbnails]** tab. Wijzig desgewenst de miniatuurgrootte en selecteer **[!UICONTROL OK]**.

   ![6_5_dynamicmediaprocessimageassets-thumbnailstab](assets/6_5_dynamicmediaprocessimageassets-thumbnailstab.png)

1. Selecteer **[!UICONTROL Process Thumbnails]** stap selecteert u vervolgens de **[!UICONTROL Thumbnails]** tab. Wijzig desgewenst de miniatuurgrootte en selecteer **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >De waarden in het argument voor miniaturen in de stap **[!UICONTROL Process Thumbnails]** moeten overeenkomen met het argument voor miniaturen in de stap **[!UICONTROL Dynamic Media Process Image Assets]**.

1. Selecteren **[!UICONTROL Save]** om de wijzigingen in de workflow op te slaan.

### Het aantal weergegeven voorinstellingen voor afbeeldingen vergroten of verkleinen {#increasing-or-decreasing-the-number-of-image-presets-that-display}

Afbeeldingsvoorinstellingen die u maakt, zijn beschikbaar als dynamische uitvoeringen wanneer u een voorvertoning van elementen weergeeft. Experience Manager geeft verschillende dynamische uitvoeringen weer wanneer een element wordt weergegeven vanuit **[!UICONTROL Detail View > Renditions]**. U kunt de limiet van weergegeven uitvoeringen verhogen of verlagen.

**Het aantal weergegeven voorinstellingen voor afbeeldingen vergroten of verkleinen:**

1. Navigeren naar CRXDE Lite ([https://localhost:4502/crx/de](https://localhost:4502/crx/de)).
1. Navigeer naar het knooppunt met vooraf ingestelde lijsten voor afbeeldingen op `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist`

   ![rise_reduction ethenumberofimagepresetsthatdisplay](assets/increase_decreasethenumberofimagepresetsthatdisplay.png)

1. Wijzig in de eigenschap **[!UICONTROL limit]** de **[!UICONTROL Value]**, die standaard op 15 is ingesteld, in het gewenste getal.
1. Navigeer naar de gegevensbron voor de afbeeldingsvoorinstelling op `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist/datasource`

   ![chlimage_1-495](assets/chlimage_1-495.png)

1. Wijzig in de eigenschap limit het getal in het gewenste getal, bijvoorbeeld `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. Selecteer **[!UICONTROL Save All]**.

### Voorinstellingen voor afbeeldingen maken {#creating-image-presets}

Maak afbeeldingsvoorinstellingen, zodat u instellingen consistent kunt toepassen op alle afbeeldingen wanneer u een voorvertoning weergeeft of publiceert.

>[!NOTE]
>
>Als u Internet Explorer 9 gebruikt, wordt het maken van een voorinstelling niet meteen na het opslaan weergegeven in de lijst met voorinstellingen. U kunt dit probleem omzeilen door de cache voor IE9 uit te schakelen.

Als u de opname van AI-, PDF- en EPS-bestanden wilt ondersteunen, zodat u een dynamische uitvoering van deze bestandsindelingen kunt genereren, bekijkt u de volgende informatie voordat u voorinstellingen voor afbeeldingen maakt.

Zie [Adobe Illustrator- (AI), PostScript®- (EPS) en PDF-bestandsindelingen](#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats).

Als u de opname van INDD-bestanden wilt ondersteunen, zodat u dynamische uitvoering van deze bestandsindeling kunt genereren, controleert u de volgende informatie voordat u voorinstellingen voor afbeeldingen maakt.

Zie [InDesign-bestandsindeling (INDD)](#indesign-indd-file-format).

**Voorinstellingen voor afbeeldingen maken:**

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben, dan ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Presets]**.
1. Selecteer **[!UICONTROL Create]**.

   ![chlimage_1-496](assets/chlimage_1-496.png)

   >[!NOTE]
   >
   >Als u deze voorinstelling responsief wilt maken, wist u de waarden in de velden **[!UICONTROL width]** en **[!UICONTROL height]** en laat u deze leeg.

1. In de **[!UICONTROL Edit Image Preset]** venster, voert u waarden in in de **[!UICONTROL Basic]** en **[!UICONTROL Advanced]** de juiste tabbladen, inclusief een naam. De opties worden beschreven in [Opties voor afbeeldingsvoorinstellingen](#image-preset-options). Voorinstellingen worden weergegeven in het linkerdeelvenster en kunnen direct samen met andere assets worden gebruikt.

   ![6_5_imagepreset-edit](assets/6_5_imagepreset-edit.png)

1. Selecteer **[!UICONTROL Save]**.

### Een responsieve voorinstelling voor afbeeldingen maken {#creating-a-responsive-image-preset}

Voer de stappen uit in [Voorinstellingen voor afbeeldingen maken](#creating-image-presets). Bij het invoeren van de hoogte en breedte in het dialoogvenster **[!UICONTROL Edit Image Preset]** , wist de waarden en laat ze leeg.

Als u deze leeg laat, krijgt de Experience Manager de melding dat deze voorinstelling reageert. U kunt de andere waarden desgewenst aanpassen.

>[!NOTE]
>
>Als u de knoppen **[!UICONTROL URL]** en **[!UICONTROL RESS]** wilt zien wanneer u een voorinstelling voor een afbeelding op een asset toepast, moet de asset worden gepubliceerd.
>
>![chlimage_1-79](assets/chlimage_1-498.png)
>
>Voorinstellingen voor afbeeldingen en afbeeldingselementen worden automatisch gepubliceerd.

### Opties voor voorinstellingen afbeelding {#image-preset-options}

Wanneer u voorinstellingen voor afbeeldingen maakt of bewerkt, worden de opties in deze sectie beschreven. Daarnaast raadt Adobe aan om de volgende opties voor best practices te kiezen:

* **[!UICONTROL Format]** (**[!UICONTROL Basic]** tab) - Selecteren **[!UICONTROL JPEG]** of een andere indeling die aan uw vereisten voldoet. Alle webbrowsers ondersteunen de JPEG-afbeeldingsindeling. Deze biedt een goede balans tussen kleine bestandsgrootten en afbeeldingskwaliteit. JPEG-afbeeldingen gebruiken echter een compressieschema met dataverlies dat ongewenste afbeeldingsartefacten kan veroorzaken als de compressie-instelling te laag is. Daarom raadt Adobe aan de compressiekwaliteit in te stellen op 75. Deze instelling biedt een goede balans tussen afbeeldingskwaliteit en kleine bestandsgrootte.

* **[!UICONTROL Enable Simple Sharpening]** - Niet selecteren **[!UICONTROL Enable Simple Sharpening]** (dit verscherpingsfilter biedt minder controle dan de instellingen voor onscherpe maskering).

* **[!UICONTROL Sharpening: Resampling Mode]** - Selecteer **[!UICONTROL Sharp2]**.

#### Opties op het tabblad Standaard {#basic-tab-options}

| Veld | Beschrijving |
| --- | --- |
| **Naam** | Voer een beschrijvende naam in zonder spaties. Als u gebruikers wilt helpen deze voorinstelling voor afbeeldingen te identificeren, neemt u de specificatie voor de afbeeldingsgrootte op in de naam. |
| **Breedte en Hoogte** | Voer in pixels de grootte in waarmee de afbeelding wordt geleverd. De breedte en hoogte moeten groter zijn dan 0 pixels. Als een van deze waarden 0 is, wordt geen voorinstelling gemaakt. Als beide waarden leeg zijn, wordt een responsieve voorinstelling voor de afbeelding gemaakt. |
| **Indeling** | Kies een indeling in het menu.<br>Kiezen **JPEG** biedt de volgende andere opties aan:<br>・ **Kwaliteit** - De schaal van de kwaliteit van de JPEG is 1-100. De schaal is zichtbaar wanneer u de schuifregelaar versleept.<br>・ **Downsampling van JPG-chrominantie inschakelen** - Omdat het oog minder gevoelig is voor hoogfrequente kleurinformatie dan hoogfrequente luminantie, verdelen JPEG-afbeeldingen de afbeeldingsgegevens in luminantie en kleurcomponenten. Wanneer een JPEG-afbeelding wordt gecomprimeerd, blijft de luminantiecomponent op volledige resolutie staan, terwijl de kleurcomponenten worden gedownsampled door het gemiddelde te nemen van pixelgroepen. Door downsampling wordt het gegevensvolume met de helft of met een derde verminderd, zonder dat dit van invloed is op de waargenomen kwaliteit. Downsampling is niet van toepassing op grijswaardenafbeeldingen. Met deze techniek vermindert u de hoeveelheid compressie die handig is voor afbeeldingen met veel contrast (bijvoorbeeld afbeeldingen met overlappende tekst).<br><br>Kiezen **GIF** of **GIF met alfa** verstrekt extra **Kwantisering kleur GIF** opties:<br>・ **Type** - Selecteer **Aangepast** (standaard), **Web**, of **Macintosh**. Als u **GIF met alfa**, is de optie Macintosh niet beschikbaar.<br>・ **Dithering** - Selecteer **Onscherp** of **Uit**.<br>・ **Aantal kleuren** - Voer het getal 2 - 256 in.<br>・ **Kleurenlijst** - Voer een door komma&#39;s gescheiden lijst in. Voor wit, grijs en zwart voert u bijvoorbeeld de volgende gegevens in: `000000,888888,ffffff`.<br><br>Kiezen **PDF**, **TIFF**, of **TIFF met alpha** biedt deze extra optie:<br>・ **Compressie** - Selecteer een compressiealgoritme. Algoritmeopties voor PDF zijn **Geen**, **Postcode**, en **Jpeg**; voor TIFF zijn ze **Geen**, **LZW**, **Jpeg**, en **Postcode**; en voor TIFF met alfa **Geen**, **LZW**, en **Postcode**.<br><br>Kiezen **PNG**, **PNG met alfa**, of **EPS** biedt geen aanvullende opties. |
| **Verscherpen** | Selecteren **Eenvoudig verscherpen inschakelen** om een standaard verscherpingsfilter toe te passen op de afbeelding nadat alle schaling heeft plaatsgevonden. Verscherpen kan helpen de vervaging te compenseren die kan optreden wanneer u een afbeelding met een andere grootte weergeeft. |

#### Opties op het tabblad Geavanceerd {#advanced-tab-options}

<table>
 <tbody>
  <tr>
   <td><strong>Veld</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td><strong>Kleurruimte</strong></td>
   <td>Selecteren <strong>RGB, CMYK,</strong> of <strong>Grijswaarden</strong> voor de kleurruimte.</td>
  </tr>
  <tr>
   <td><strong>Kleurprofiel</strong></td>
   <td>Selecteer het kleurruimteprofiel van de uitvoer waarnaar u het element wilt converteren als dit afwijkt van het werkprofiel.</td>
  </tr>
  <tr>
   <td><strong>Render-intentie</strong></td>
   <td>U kunt de standaard rendering intent overschrijven. Render-intenties bepalen wat er gebeurt met kleuren die niet in het doelkleurprofiel kunnen worden gereproduceerd (buiten kleuromvang). De render-intentie wordt genegeerd als deze niet compatibel is met het ICC-profiel.
    <ul>
     <li>Selecteren <strong>Perceptueel</strong> om de totale kleuromvang van de ene kleurruimte naar een andere kleurruimte te comprimeren wanneer een of meer kleuren in de oorspronkelijke afbeelding buiten de kleuromvang van de doelkleurruimte vallen.</li>
     <li>Selecteren <strong>Relatief colorimetrisch</strong> wanneer een kleur in de huidige kleurruimte buiten de kleuromvang valt in de doelkleurruimte. En u wilt deze toewijzen aan de dichtstbijzijnde mogelijke kleur binnen de kleuromvang van de doelkleurruimte zonder dat dit van invloed is op andere kleuren. </li>
     <li>Selecteren <strong>Verzadiging</strong> als u de oorspronkelijke kleurverzadiging van de afbeelding wilt reproduceren wanneer u de afbeelding omzet in de doelkleurruimte. </li>
     <li>Selecteren <strong>Absoluut colorimetrisch</strong> om kleuren exact overeen te laten komen zonder aanpassing voor het witpunt of zwartpunt waardoor de helderheid van de afbeelding wordt gewijzigd.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Compensatie zwartpunt</strong></td>
   <td>Selecteer deze optie als het uitvoerprofiel deze functie ondersteunt. Zwartpuntcompensatie wordt genegeerd als deze niet compatibel is met het opgegeven ICC-profiel.</td>
  </tr>
  <tr>
   <td><strong>Dithering</strong></td>
   <td>Selecteer deze optie als u kleurstreepvorming mogelijk wilt voorkomen of verminderen. </td>
  </tr>
  <tr>
   <td><strong>Verscherpingstype</strong></td>
   <td><p>Selecteren <strong>Geen</strong>, <strong>Verscherpen</strong>, of <strong>Onscherp masker</strong>. </p>
    <ul>
     <li>Selecteren <strong>Geen</strong> als u verscherpen wilt uitschakelen.</li>
     <li>Selecteren <strong>Verscherpen </strong>om een standaard verscherpingsfilter toe te passen op de afbeelding nadat alle schaling heeft plaatsgevonden. Verscherpen kan helpen de vervaging te compenseren die kan optreden wanneer u een afbeelding met een andere grootte weergeeft. </li>
     <li>Selecteren<strong> Onscherp masker</strong> als u een verscherpingsfiltereffect wilt perfectioneren op de uiteindelijke gedownsampelde afbeelding. U kunt de intensiteit van het effect, de straal van het effect (gemeten in pixels) en een drempel voor het contrast instellen die wordt genegeerd. Voor dit effect worden dezelfde opties gebruikt als voor het filter Onscherp masker in Photoshop.</li>
    </ul> <p>In <strong>Onscherp masker</strong>hebt u de volgende opties:</p>
    <ul>
     <li><strong>Hoeveelheid</strong> - Hiermee bepaalt u de hoeveelheid contrast die wordt toegepast op de randpixels. De standaardwaarde voor het reële getal is 1,0. Voor afbeeldingen met hoge resolutie kunt u de resolutie verhogen tot 5,0. Beschouw Hoeveelheid als een maat voor de filterintensiteit.</li>
     <li><strong>Straal</strong> - Hiermee bepaalt u het aantal pixels rondom de randpixels dat invloed heeft op de verscherping. Voer voor afbeeldingen met een hoge resolutie een getal in tussen 1 en 2. Bij een lage waarde worden alleen de randpixels verscherpt. met een hoge waarde wordt een grotere reeks pixels verscherpt . De juiste waarde is afhankelijk van de grootte van de afbeelding.</li>
     <li><strong>Drempel</strong> - Hiermee bepaalt u het contrastbereik dat moet worden genegeerd wanneer het filter Onscherp masker wordt toegepast. Met andere woorden, met deze optie bepaalt u hoe verschillend de verscherpte pixels moeten zijn van het omringende gebied voordat ze als randpixels worden beschouwd en worden verscherpt. Experimenteer met gehele getallen tussen 2 en 20 om ruis te voorkomen. </li>
     <li><strong>Toepassen op</strong> - Hiermee wordt bepaald of de verscherping wordt toegepast op elke kleur of helderheid.</li>
    </ul>
    <div>
      Verscherpen wordt beschreven in
     <a href="https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-image-sharpening-feature-video-use.html#dynamic-media">Afbeelding verscherpen gebruiken met Experience Manager Dynamic Media</a> video, in <a href="https://experienceleague.adobe.com/docs/dynamic-media-classic/using/master-files/sharpening-image.html#master-files">Een afbeelding verscherpen</a> online Help-onderwerp en in <a href="https://experienceleague.adobe.com/docs/dynamic-media-classic/assets/s7_sharpening_images.pdf">Aanbevolen procedures voor het verscherpen van afbeeldingen in Dynamic Media Classic</a> downloadbare PDF.
    </div> </td>
  </tr>
  <tr>
   <td><strong>Modus voor nieuwe pixels</strong></td>
   <td>Selecteer een <strong>Modus voor nieuwe pixels</strong> optie. Met deze opties verscherpt u de afbeelding wanneer deze wordt gedownsampled:
    <ul>
     <li><strong>Bi-Lineair</strong> - De snelste methode voor het berekenen van nieuwe beeldpixels. Sommige aliasingartefacten zijn waarneembaar.</li>
     <li><strong>Bi-Cubic</strong> - Verhoogt het CPU-gebruik, maar geeft scherpere afbeeldingen met minder merkbare aliasing artefacten.</li>
     <li><strong>Scherp2</strong> - De resultaten kunnen iets scherper zijn dan die van Bi-Cubic, maar tegen nog hogere CPU-kosten.</li>
     <li><strong>Bi-Sharp</strong> - Hiermee selecteert u Photoshop standaardresampler voor het verkleinen van de afbeeldingsgrootte, die wordt aangeroepen <strong>bicubisch scherper</strong> in Adobe Photoshop.</li>
     <li><strong>Elke kleur</strong> en <strong>Helderheid</strong> - elke methode kan gebaseerd zijn op kleur of helderheid. Standaard <strong>Elke kleur</strong> is geselecteerd.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Afdrukresolutie</strong></td>
   <td>Selecteer een resolutie voor het afdrukken van deze afbeelding. 72 pixels is de standaardinstelling.</td>
  </tr>
  <tr>
   <td><strong>Afbeelding wijzigen</strong></td>
   <td><p>Naast de algemene afbeeldingsinstellingen die beschikbaar zijn in de gebruikersinterface, ondersteunt Dynamic Media een groot aantal geavanceerde afbeeldingswijzigingen die u kunt opgeven in het dialoogvenster <strong>Afbeeldingsaanpassingen</strong> veld. Deze parameters worden gedefinieerd in het dialoogvenster <a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/syntax-and-features/image-serving-http/c-command-overview.html">Verwijzing naar de opdracht Protocol van Image Server</a>.</p> <p>Belangrijk: De volgende functionaliteit in de API wordt niet ondersteund:</p>
    <ul>
     <li>Standaardopdrachten voor sjablonen en tekstrendering: <code>text= textAngle= textAttr= textFlowPath= textFlowXPath= textPath=</code> en <code>textPs=</code></li>
     <li>Localisatie-opdrachten: <code>locale=</code> en <code>req=xlate</code></li>
     <li><code>req=set</code> is niet beschikbaar voor algemeen gebruik.</li>
     <li><code>req=mbrset</code></li>
     <li><code>req=saveToFile</code></li>
     <li><code>req=targets</code></li>
     <li><code>template=</code></li>
     <li>Niet-kernservices van Dynamic Media: SVG, Afbeelding renderen en Web-to-Print</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Voorinstellingsopties voor afbeeldingen definiëren met afbeeldingsopties {#defining-image-preset-options-with-image-modifiers}

Naast de opties op de tabbladen Standaard en Geavanceerd kunt u ook opties voor het wijzigen van afbeeldingen definiëren voor het definiëren van voorinstellingen voor afbeeldingen. Rendering van afbeeldingen is afhankelijk van de Dynamic Media Image Rendering API en wordt in detail gedefinieerd in het dialoogvenster [HTTP-protocolreferentie](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-rendering-api/http-protocol-reference/c-ir-introduction.html#image-rendering-api).

Hieronder volgen enkele basisvoorbeelden van wat u kunt doen met wijzigingstoetsen voor afbeeldingen.

>[!NOTE]
>
>Bepaalde afbeeldingsopties [kan niet worden gebruikt in Experience Manager](#advanced-tab-options).

* [op_invert](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-invert.html) - Hiermee wordt elke kleurcomponent omgekeerd voor een negatief afbeeldingseffect.

   ```xml {.line-numbers}
   &op_invert=1
   ```

   ![6_5_imagepreset-edit-invert](assets/6_5_imagepreset-edit-invert.png)

* [op_vervagen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-blur.html) - Hiermee past u een vervagend filter toe op de afbeelding.

   ```xml {.line-numbers}
   &op_blur=7
   ```

   ![6_5_imagepreset-edit-blur](assets/6_5_imagepreset-edit-blur.png)

* Gecombineerde opdrachten - op_vervagen en op-omkeren

   ```xml {.line-numbers}
   &op_invert=1&op_blur=7
   ```

   ![chlimage_1-80](assets/chlimage_1-501.png)

* [op_brightness](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-brightness.html) - Vermindert of verhoogt de helderheid.

   ```xml {.line-numbers}
   &op_brightness=58
   ```

   ![6_5_imagepreset-edit-brightness](assets/6_5_imagepreset-edit-brightness.png)

* [opac](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-opac.html) - Hiermee past u de dekking van de afbeelding aan. Hiermee kunt u de dekking van de voorgrond verlagen.

   ```xml {.line-numbers}
   opac=29
   ```

   ![6_5_imagepreset-edit-opacity](assets/6_5_imagepreset-edit-opacity.png)

### Voorinstellingen voor afbeeldingen bewerken {#modifying-image-presets}

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben, dan ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Presets]**.

   ![6_5_imagepreset-editpreset](assets/6_5_imagepreset-editpreset.png)

1. Selecteer een voorinstelling en selecteer vervolgens **[!UICONTROL Edit]**. De **[!UICONTROL Edit Image Preset]** wordt geopend.
1. Wijzigingen aanbrengen en selecteren **[!UICONTROL Save]** om uw wijzigingen op te slaan of **[!UICONTROL Cancel]** om uw wijzigingen te annuleren.

### Voorinstellingen voor afbeeldingen publiceren {#publishing-image-presets}

Voorinstellingen voor afbeeldingen worden automatisch voor u gepubliceerd.

### Afbeeldingsvoorinstellingen verwijderen {#deleting-image-presets}

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben en het pictogram van Hulpmiddelen te selecteren.
1. Ga naar **[!UICONTROL Assets]** > **[!UICONTROL Image Presets]**.
1. Selecteer een voorinstelling en selecteer **[!UICONTROL Delete]**. Dynamic Media bevestigt dat je het wilt verwijderen. Selecteren **[!UICONTROL Delete]** om te verwijderen of te selecteren **[!UICONTROL Cancel]** om terug te keren naar Voorinstellingen afbeelding.
