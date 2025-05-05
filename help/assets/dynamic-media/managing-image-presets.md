---
title: Voorinstellingen afbeelding beheren
description: Leer over Voorinstellingen voor afbeeldingen en hoe u deze kunt maken, wijzigen en beheren.
contentOwner: Rick Brough
feature: Image Presets,Viewers,Renditions
role: User
exl-id: a53f40ab-0e27-45f8-9142-781c077a04cc
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '3420'
ht-degree: 5%

---

# Voorinstellingen afbeelding beheren{#managing-image-presets}

Met Voorinstellingen voor afbeeldingen kan Adobe Experience Manager Assets afbeeldingen dynamisch leveren in verschillende formaten, in verschillende indelingen of met andere afbeeldingseigenschappen die dynamisch worden gegenereerd. Elke voorinstelling voor afbeeldingen vertegenwoordigt een vooraf gedefinieerde verzameling opdrachten voor het vergroten of verkleinen en opmaken van afbeeldingen. Wanneer u een voorinstelling voor afbeeldingen maakt, kiest u een grootte voor het leveren van de afbeelding. U kiest ook opmaakopdrachten, zodat de weergave van de afbeelding wordt geoptimaliseerd wanneer de afbeelding wordt geleverd voor weergave.

Beheerders kunnen voorinstellingen maken voor het exporteren van elementen. Gebruikers kunnen bij het exporteren van afbeeldingen een voorinstelling kiezen die de afbeeldingen opnieuw opmaakt volgens de specificaties die de beheerder heeft opgegeven.

U kunt ook voorinstellingen voor afbeeldingen maken die reageren. Als u een voorinstelling voor een responsieve afbeelding toepast op uw elementen, worden deze afhankelijk van het apparaat of de schermgrootte waarop ze worden weergegeven. U kunt Voorinstellingen voor afbeeldingen zodanig configureren dat naast RGB of Grijs ook CMYK in de kleurruimte wordt gebruikt.

In deze sectie wordt beschreven hoe u voorinstellingen voor afbeeldingen maakt, wijzigt en over het algemeen beheert. U kunt een voorinstelling voor afbeeldingen op elk gewenst moment op een afbeelding toepassen. Zie [ Beeld toepassen vooraf instelt ](/help/assets/dynamic-media/image-presets.md).

>[!NOTE]
>
>Slimme beeldverwerking werkt met uw bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie bij de laatste milliseconde van de levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding. Zie [ Slimme Beeldvorming ](/help/assets/dynamic-media/imaging-faq.md) voor meer informatie.

## Meer informatie over voorinstellingen voor afbeeldingen {#understanding-image-presets}

Net als bij een macro is een voorinstelling voor afbeeldingen een vooraf gedefinieerde verzameling opdrachten voor het vergroten of verkleinen en opmaken van de grootte die onder een naam zijn opgeslagen. Als u wilt weten hoe Voorinstellingen afbeelding werken, veronderstelt u dat elke productafbeelding op uw website moet worden weergegeven in verschillende formaten, formaten en compressiesnelheden voor levering op het bureaublad en in mobiele apparaten.

U kunt twee voorinstellingen voor afbeeldingen maken: 500 x 500 pixels voor het bureaublad en 150 x 150 pixels voor mobiele apparaten. U maakt twee voorinstellingen voor afbeeldingen, een voorinstelling die `Enlarge` wordt genoemd, om afbeeldingen met 500 x 500 pixels weer te geven en een voorinstelling die `Thumbnail` wordt aangeroepen om afbeeldingen met 150 x 150 pixels weer te geven. Experience Manager zoekt naar de definitie van `Enlarge Image Preset` en `Thumbnail Image Preset` om afbeeldingen op `Enlarge` - en `Thumbnail` -grootte te leveren. Vervolgens genereert Experience Manager dynamisch een afbeelding met de grootte en opmaakspecificaties van elke voorinstelling voor afbeeldingen.

Afbeeldingen die bij dynamische levering kleiner worden gemaakt, kunnen scherper en gedetailleerder worden. Daarom bevat elke voorinstelling voor afbeeldingen opmaakbesturingselementen waarmee u een afbeelding kunt optimaliseren wanneer deze met een bepaalde grootte wordt geleverd. Met deze besturingselementen zorgt u ervoor dat uw afbeeldingen scherp en duidelijk zijn wanneer ze aan uw website of toepassing worden geleverd.

Beheerders kunnen voorinstellingen voor afbeeldingen maken. Als u een voorinstelling voor afbeeldingen wilt maken, begint u helemaal opnieuw of u kunt een bestaande voorinstelling opnieuw gebruiken en opslaan onder een andere naam.

## Voorinstellingen afbeelding beheren {#managing-image-presets-1}

U beheert uw Voorinstellingen voor afbeeldingen in Experience Manager door het Experience Manager-logo te selecteren voor toegang tot de algemene navigatieconsole en vervolgens het pictogram Extra te selecteren en naar **[!UICONTROL Assets]** > **[!UICONTROL Image Presets]** te navigeren.

![ 6_5_tools-assets-imagepresets ](assets/6_5_tools-assets-imagepresets.png)

>[!NOTE]
>
>Alle voorinstellingen voor afbeeldingen die u maakt, zijn ook beschikbaar als dynamische uitvoeringen wanneer u elementen voorvertoont of levert.
>
>U *niet* te hoeven om Beeld te publiceren vooraf instelt aangezien het Beeld automatisch wordt gepubliceerd.
>
>Zie [ publiceren Beeld vooraf instelt ](#publishing-image-presets).

>[!NOTE]
>
>Het systeem geeft verschillende uitvoeringen weer wanneer u **[!UICONTROL Renditions]** selecteert in de Gedetailleerde weergave van een element. U kunt het aantal voorinstellingen voor afbeeldingen dat wordt weergegeven, verhogen of verlagen. Zie [ Verhoog het aantal beeld vooraf instelt die ](#increasing-or-decreasing-the-number-of-image-presets-that-display) worden getoond.

### Bestandsindelingen Adobe Illustrator (AI), PostScript® (EPS) en PDF {#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats}

Als u de opname van AI-, EPS- en PDF-bestanden wilt ondersteunen, zodat u dynamische uitvoeringen van deze bestandsindelingen kunt genereren, bekijkt u de volgende informatie voordat u Voorinstellingen voor afbeeldingen maakt.

Adobe Illustrator-bestandsindeling is een variant van PDF. De belangrijkste verschillen in de context van Experience Manager Assets zijn:

* Adobe Illustrator-documenten bestaan uit één pagina met meerdere lagen. Elke laag wordt geëxtraheerd als een PNG-subelement onder het Illustrator-hoofdelement.
* PDF-documenten bestaan uit een of meer pagina&#39;s. Elke pagina wordt uitgepakt als een PDF-subelement van één pagina onder het PDF-hoofddocument met meerdere pagina&#39;s.

De component `Create Sub Asset process` maakt de subelementen binnen de algemene `DAM Update Asset` -workflow. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** > **[!UICONTROL DAM Update Asset]** > **[!UICONTROL Edit]** om deze procescomponent weer te geven in de workflow.

<!-- See also [Viewing pages of a multi-page file](/help/assets/manage-linked-subassets.md#view-pages-of-a-multi-page-file). -->

U kunt de subelementen of de pagina&#39;s weergeven wanneer u het element opent, het menu Inhoud selecteert en **[!UICONTROL Subassets]** of **[!UICONTROL Pages]** selecteert. De subelementen zijn echte elementen. De workflowcomponent `Create Sub Asset` extraheert de PDF-pagina&#39;s. Deze worden vervolgens opgeslagen als `page1.pdf` , `page2.pdf` , enzovoort, onder het hoofdelement. Nadat ze zijn opgeslagen, verwerkt de `DAM Update Asset` -workflow ze.

Als u Dynamic Media wilt gebruiken om dynamische uitvoeringen voor AI-, EPS- of PDF-bestanden voor te vertonen en te genereren, moet u de volgende verwerkingsstappen uitvoeren:

1. In de `DAM Update Asset` -workflow rasterizes de `Rasterize PDF/AI Image Preview Rendition` -procescomponent de eerste pagina van het oorspronkelijke element (met de geconfigureerde resolutie) in een `cqdam.preview.png` -uitvoering.

1. De `Dynamic Media Process Image Assets` -procescomponent in de workflow optimaliseert de `cqdam.preview.png` -uitvoering in een PTIFF-bestand.

>[!NOTE]
>
>In de workflow Asset-updates van DAM worden miniaturen voor EPS-bestanden gegenereerd in de stap **[!UICONTROL EPS thumbnails]**.

#### Eigenschappen van metagegevens van PDF/AI/EPS-elementen {#pdf-ai-eps-asset-metadata-properties}

| **bezit van Meta-gegevens** | **Beschrijving** |
|---|---|
| `dam:Physicalwidthininches` | Documentbreedte in inches. |
| `dam:Physicalheightininches` | Documenthoogte in inches. |

Via de `DAM Update Asset` -workflow hebt u toegang tot de opties voor procescomponenten van `Rasterize PDF/AI Image Preview Rendition` .

Selecteer Adobe Experience Manager linksboven en klik op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** . Selecteer op de pagina Workflowmodellen **[!UICONTROL DAM Update Asset]** en selecteer vervolgens op de werkbalk **[!UICONTROL Edit]** . Dubbelselecteer op de pagina met DAM-updategegevens de procescomponent `Rasterize PDF/AI Image Preview Rendition` om het dialoogvenster Step Properties te openen.

#### Opties PDF/AI Voorvertoning afbeelding omzetten in pixels {#rasterize-pdf-ai-image-preview-rendition-options}

![ Argumenten om het werkschema van PDF of AI ](assets/rasterize_pdf_ai_image_preview.png) om te zetten in pixels

Argumenten voor het rasteren van PDF- of AI-workflow

| Procesargument | Standaardinstelling | Beschrijving |
|---|---|---|
| MIME-typen | application/pdf <br> toepassing/postscript <br> toepassing/illustrator | Lijst met documenttypen die worden beschouwd als PDF- of Illustrator-documenten. |
| Max. breedte | 2048 | Maximale breedte van de gegenereerde voorvertoning, in pixels. |
| Max. hoogte | 2048 | Maximumhoogte van de gegenereerde voorvertoning, in pixels. |
| Resolutie | 72 | Resolutie voor het rasteren van de eerste pagina, in ppi (pixels per inch). |

Met de standaardprocesargumenten wordt de eerste pagina van een PDF/AI-document gerasterd met 72 ppi en de gegenereerde voorvertoning met een grootte van 2048 x 2048 pixels. Voor een gebruikelijke implementatie kunt u de resolutie verhogen tot minimaal 150 ppi of meer. Een document met een tekengrootte van 300 ppi in de VS vereist bijvoorbeeld een maximale breedte en hoogte van respectievelijk 2550 x 3300 pixels.

Met Maximale breedte en Maximumhoogte kunt u de resolutie beperken waarbij u de afbeelding wilt rasteren. Als de maximale waarden bijvoorbeeld ongewijzigd blijven en de resolutie is ingesteld op 300 ppi, wordt een US Letter-document gerasterd naar 186 ppi. Het document is dus 1581 x 2046 pixels.

In de procescomponent `Rasterize PDF/AI Image Preview Rendition` is een maximum gedefinieerd om te voorkomen dat er te grote afbeeldingen in het geheugen worden gemaakt. Zulke grote afbeeldingen kunnen het geheugen overlopen dat aan de JVM (Java™ Virtual Machine) wordt geleverd. Er moet op worden gelet dat de JVM over voldoende geheugen beschikt om het geconfigureerde aantal parallelle workflows te beheren, waarbij elk van beide de mogelijkheid heeft om een image op de maximaal geconfigureerde grootte te maken.

### InDesign-bestandsindeling (INDD) {#indesign-indd-file-format}

Als u de opname van INDD-bestanden wilt ondersteunen, zodat u dynamische uitvoering van deze bestandsindeling kunt genereren, controleert u de volgende informatie voordat u Voorinstellingen afbeelding maakt.

Voor InDesign-bestanden worden subelementen alleen geëxtraheerd als de Adobe InDesign Server is geïntegreerd met Experience Manager. Elementen waarnaar wordt verwezen, zijn gekoppeld op basis van hun metagegevens. InDesign Server is niet vereist voor koppelingen. De middelen waarnaar wordt verwezen, moeten echter aanwezig zijn in Experience Manager voordat de InDesign-bestanden worden verwerkt, zodat de koppelingen tussen de InDesign-bestanden en de middelen waarnaar wordt verwezen, kunnen worden gemaakt.

<!-- See [Integrate Experience Manager Assets with InDesign Server](/help/assets/indesign.md). -->

Met de component Media Extraction Process in de `DAM Update Asset` -workflow worden verschillende vooraf geconfigureerde Extend Scripts uitgevoerd voor het verwerken van InDesign-bestanden.

![ de wegen ExtendScript in de argumenten van het proces van de Extractie van Media ](/help/assets/dynamic-media/assets/6_5_mediaextractionprocess.png)

De ExtendScript-paden in de argumenten van de procescomponent Media Extraction in de DAM Update Asset-workflow.

De volgende scripts worden gebruikt door Dynamic Media-integratie:


| ExtendScript-naam | Standaard | Beschrijving |
|---|---|---|
| ThumbnailExport.jsx | Ja | Genereert een 300 PPI `thumbnail.jpg` -uitvoering die is geoptimaliseerd en door `Dynamic Media Process Image Assets` -procescomponent is omgezet in een PTIFF-uitvoering. |
| JPEGPagesExport.jsx | Ja | Genereert een 300 PPI JPEG-subelement voor elke pagina. Het JPEG-submiddel is een echt middel dat is opgeslagen onder het InDesign-element. De `DAM Update Asset` -workflow wordt geoptimaliseerd en omgezet in een PTIFF-bestand. |
| PDFPagesExport.jsx | Nee | Genereert een PDF-subelement voor elke pagina. Het PDF-subelement wordt verwerkt zoals eerder beschreven. Omdat de PDF slechts één pagina bevat, worden geen subelementen gegenereerd. |

### De miniatuurgrootte van de afbeelding configureren {#configuring-image-thumbnail-size}

U kunt de grootte van miniaturen configureren door deze instellingen te configureren in de **[!UICONTROL DAM Update Asset]** -workflow. De workflow bevat twee stappen waarmee u de miniatuurgrootte van afbeeldingselementen kunt configureren. Één (**[!UICONTROL Dynamic Media Process Image Assets]**) wordt gebruikt voor dynamische beeldactiva. Het andere (**[!UICONTROL Process Thumbnails]**) wordt gebruikt voor het genereren van statische miniaturen of wanneer alle andere processen geen miniaturen genereren. Ongeacht, *allebei* moeten de zelfde montages hebben.

In de stap **[!UICONTROL Dynamic Media Process Image Assets]** wordt de afbeeldingsserver gebruikt om miniaturen te genereren, onafhankelijk van de configuratie die op de stap **[!UICONTROL Process Thumbnails]** is toegepast. Het genereren van miniaturen via de stap **[!UICONTROL Process Thumbnails]** is de langzaamste en meest geheugenintensieve manier om miniaturen te maken.

Miniatuurgrootte wordt als volgt gedefinieerd: **[!UICONTROL width:height:center]** bijvoorbeeld `80:80:false` . De breedte en hoogte bepalen de grootte in pixels van de miniatuur. De middelste waarde is false of true. Indien true, geeft dit aan dat de miniatuurafbeelding exact de grootte heeft die in de configuratie is opgegeven. Als de gewijzigde afbeelding kleiner is, wordt deze gecentreerd in de miniatuur.

>[!NOTE]
>
>* Miniatuurgrootten voor EPS-bestanden worden geconfigureerd in de stap **[!UICONTROL EPS thumbnails]** op het tabblad **[!UICONTROL Arguments]** onder Miniaturen.
>
>* Miniatuurgrootten voor video&#39;s worden geconfigureerd in de stap **[!UICONTROL FFmpeg thumbnails]** op het tabblad **[!UICONTROL Process]** onder **[!UICONTROL Arguments]** .
>

**om de grootte van de beeldduimnagel te vormen:**

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** > **[!UICONTROL DAM Update Asset]** > **[!UICONTROL Edit]** .
1. Selecteer de stap **[!UICONTROL Dynamic Media Process Image Assets]** en selecteer de tab **[!UICONTROL Thumbnails]** . Wijzig desgewenst de miniatuurgrootte en selecteer **[!UICONTROL OK]** .

   ![ 6_5_dynamicmediaprocessimageassets-duimnailstab ](assets/6_5_dynamicmediaprocessimageassets-thumbnailstab.png)

1. Selecteer de stap **[!UICONTROL Process Thumbnails]** en selecteer vervolgens de tab **[!UICONTROL Thumbnails]** . Wijzig desgewenst de miniatuurgrootte en selecteer **[!UICONTROL OK]** .

   >[!NOTE]
   >
   >De waarden in het argument voor miniaturen in de stap **[!UICONTROL Process Thumbnails]** moeten overeenkomen met het argument voor miniaturen in de stap **[!UICONTROL Dynamic Media Process Image Assets]**.

1. Selecteer **[!UICONTROL Save]** om de wijzigingen in de workflow op te slaan.

### Het aantal weergegeven voorinstellingen voor afbeeldingen vergroten of verkleinen {#increasing-or-decreasing-the-number-of-image-presets-that-display}

Afbeeldingsvoorinstellingen die u maakt, zijn beschikbaar als dynamische uitvoeringen wanneer u een voorvertoning van elementen weergeeft. Experience Manager geeft verschillende dynamische uitvoeringen weer wanneer een element wordt weergegeven vanuit **[!UICONTROL Detail View > Renditions]** . U kunt de limiet van weergegeven uitvoeringen verhogen of verlagen.

**om het aantal beeld te verhogen of te verminderen stelt die worden getoond:**

1. Navigeer aan CRXDE Lite ([ https://localhost:4502/crx/de ](https://localhost:4502/crx/de)).
1. Navigeer naar het knooppunt met vooraf ingestelde lijsten voor afbeeldingen op `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist`

   ![ verhogings_reduction ethenumberofimagepresetsthatdisplay ](assets/increase_decreasethenumberofimagepresetsthatdisplay.png)

1. Wijzig in de eigenschap **[!UICONTROL limit]** de **[!UICONTROL Value]**, die standaard op 15 is ingesteld, in het gewenste getal.
1. Navigeer naar de gegevensbron voor de afbeeldingsvoorinstelling op `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist/datasource`

   ![ chlimage_1-495 ](assets/chlimage_1-495.png)

1. Wijzig in de eigenschap limit het getal in het gewenste getal, bijvoorbeeld `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. Selecteer **[!UICONTROL Save All]** .

### Voorinstellingen afbeelding maken {#creating-image-presets}

Maak voorinstellingen voor afbeeldingen, zodat u instellingen consistent kunt toepassen op alle afbeeldingen wanneer u een voorvertoning weergeeft of publiceert.

>[!NOTE]
>
>Als u Internet Explorer 9 gebruikt, wordt het maken van een voorinstelling niet meteen na het opslaan weergegeven in de lijst met voorinstellingen. U kunt dit probleem omzeilen door de cache voor IE9 uit te schakelen.

Als u de opname van AI-, PDF- en EPS-bestanden wilt ondersteunen, zodat u een dynamische uitvoering van deze bestandsindelingen kunt genereren, bekijkt u de volgende informatie voordat u Voorinstellingen voor afbeeldingen maakt.

Zie [ Adobe Illustrator (AI), PostScript® (EPS), en de dossierformaten van PDF ](#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats).

Als u de opname van INDD-bestanden wilt ondersteunen, zodat u dynamische uitvoering van deze bestandsindeling kunt genereren, controleert u de volgende informatie voordat u Voorinstellingen afbeelding maakt.

Zie [ InDesign (INDD) dossierformaat ](#indesign-indd-file-format).

**om beeld tot stand te brengen vooraf instelt:**

1. Selecteer in Experience Manager het Experience Manager-logo voor toegang tot de algemene navigatieconsole en ga vervolgens naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Presets]** .
1. Selecteer **[!UICONTROL Create]** .

   ![ chlimage_1-496 ](assets/chlimage_1-496.png)

   >[!NOTE]
   >
   >Als u deze voorinstelling afbeelding responsief wilt maken, wist u de waarden in de velden **[!UICONTROL width]** en **[!UICONTROL height]** en laat u deze leeg.

1. Voer in het venster **[!UICONTROL Edit Image Preset]** waar nodig waarden in op de tabbladen **[!UICONTROL Basic]** en **[!UICONTROL Advanced]** , inclusief een naam. De opties worden beschreven in [Opties voor afbeeldingsvoorinstellingen](#image-preset-options). Voorinstellingen worden weergegeven in het linkerdeelvenster en kunnen direct samen met andere assets worden gebruikt.

   ![ 6_5_imagepreset-geef uit ](assets/6_5_imagepreset-edit.png)

1. Selecteer **[!UICONTROL Save]** .

### Een responsieve voorinstelling voor afbeeldingen maken {#creating-a-responsive-image-preset}

Om een ontvankelijke Vooraf ingesteld Beeld tot stand te brengen, voer de stappen in [ tot beeld uit vooraf instelt ](#creating-image-presets). Wanneer u de hoogte en breedte in het **[!UICONTROL Edit Image Preset]** -venster invoert, wist u de waarden en laat u deze leeg.

Als u deze leeg laat, weet Experience Manager dat op deze voorinstelling kan worden gereageerd. U kunt de andere waarden desgewenst aanpassen.

>[!NOTE]
>
>Als u de knoppen **[!UICONTROL URL]** en **[!UICONTROL RESS]** wilt zien wanneer u een voorinstelling voor afbeelding op een element toepast, moet het element worden gepubliceerd.
>
>![ chlimage_1-79 ](assets/chlimage_1-498.png)
>
>Voorinstellingen voor afbeeldingen en afbeeldingselementen worden automatisch gepubliceerd.

### Voorinstellingsopties voor afbeelding {#image-preset-options}

Wanneer u voorinstellingen voor afbeeldingen maakt of bewerkt, worden de opties in deze sectie beschreven. Daarnaast raadt Adobe aan om de volgende opties voor best practices te kiezen:

* **[!UICONTROL Format]** (**[!UICONTROL Basic]** tab) - Selecteer **[!UICONTROL JPEG]** of een andere indeling die aan uw vereisten voldoet. Alle webbrowsers ondersteunen de JPEG-afbeeldingsindeling. Deze biedt een goede balans tussen kleine bestandsgrootten en afbeeldingskwaliteit. JPEG-afbeeldingen gebruiken echter een compressieschema met dataverlies dat ongewenste afbeeldingsartefacten kan veroorzaken als de compressie-instelling te laag is. Daarom raadt Adobe aan de compressiekwaliteit in te stellen op 75. Deze instelling biedt een goede balans tussen afbeeldingskwaliteit en kleine bestandsgrootte.

* **[!UICONTROL Enable Simple Sharpening]** - Niet selecteren **[!UICONTROL Enable Simple Sharpening]** (dit verscherpingsfilter biedt minder controle dan de instellingen voor onscherpe maskering).

* **[!UICONTROL Sharpening: Resampling Mode]** - Selecteer **[!UICONTROL Sharp2]** .

#### Opties op het tabblad Standaard {#basic-tab-options}

| Veld | Beschrijving |
| --- | --- |
| **Naam** | Voer een beschrijvende naam in zonder spaties. Als u gebruikers wilt helpen deze voorinstelling voor afbeeldingen te identificeren, neemt u de specificatie voor de afbeeldingsgrootte op in de naam. |
| **Breedte en Hoogte** | Voer in pixels de grootte in waarmee de afbeelding wordt geleverd. De breedte en hoogte moeten groter zijn dan 0 pixels. Als een van deze waarden 0 is, wordt geen voorinstelling gemaakt. Als beide waarden leeg zijn, wordt een responsieve voorinstelling voor afbeeldingen gemaakt. |
| **Formaat** | Kies een indeling in het menu.<br> het kiezen van **JPEG** biedt de volgende andere opties aan:<br>・ **Kwaliteit** - de de kwaliteitsschaal van JPEG is 1-100. De schaal is zichtbaar wanneer u de schuifregelaar versleept.<br>・ **laat de Downsampling van de Chrominantie van JPG** toe - omdat het oog minder gevoelig aan high-frequency kleureninformatie dan high-frequency luminantie is, verdelen de beelden van JPEG beeldinformatie in helderheid en kleurencomponenten. Wanneer een JPEG-afbeelding wordt gecomprimeerd, blijft de luminantiecomponent op volledige resolutie staan, terwijl de kleurcomponenten worden gedownsampled door het gemiddelde te nemen van groepen pixels. Met downsampling verlaagt u het gegevensvolume tot een halve of een derde, met minimale gevolgen voor de waargenomen kwaliteit. Downsampling is niet van toepassing op grijswaardenafbeeldingen. Met deze techniek vermindert u de hoeveelheid compressie die handig is voor afbeeldingen met veel contrast (bijvoorbeeld afbeeldingen met overlappende tekst).<br><br> het kiezen van **GIF** of **GIF met alpha** verstrekt deze extra **Kwantiserings van de Kleur van GIF** opties:<br>・ **Type** - Uitgezocht **Aangepast** (gebrek), **Web**, of **Macintosh**. Als u **GIF met Alpha** selecteert, is de optie van Macintosh niet beschikbaar.<br>・ **Dithering** - selecteer **Onscherp** of **weg**.<br>・ **Aantal Kleuren** - ga een aantal 2 in - 256.<br>・ **Lijst van de Kleur** - ga een komma-gescheiden lijst in. Voer bijvoorbeeld voor wit, grijs en zwart `000000,888888,ffffff` in.<br><br> het kiezen van **PDF**, **TIFF**, of **TIFF met alpha** verstrekt deze extra optie:<br>・ **Compressie** - selecteer een compressiealgoritme. De opties van het algoritme voor PDF zijn **niets**, **Zip**, en **Jpeg**; voor TIFF zijn zij **niets**, **LZW**, **Jpeg**, en **Zip**; en voor TIFF met Alpha zijn **niets. 5&rbrace;,** LZW **, en** Zip **.**<br><br> het kiezen van **PNG**, **PNG met Alpha**, of **EPS** verstrekt geen extra opties. |
| **Verscherpen** | Selecteer **toelaten Eenvoudig het Verscherpen** om een basis het scherpen filter op het beeld toe te passen nadat al het schrapen plaatsvindt. Verscherpen kan helpen de vervaging te compenseren die kan optreden wanneer u een afbeelding met een andere grootte weergeeft. |

#### Opties op het tabblad Geavanceerd {#advanced-tab-options}

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
     <a href="https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use#dynamic-media"> Gebruikend Beeld dat met Experience Manager Dynamische Media </a> video verscherpt, in <a href="https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/master-files/sharpening-image#master-files"> het verscherpen van een beeld </a> online Help onderwerp, en in <a href="https://experienceleague.adobe.com/docs/dynamic-media-classic/assets/s7_sharpening_images.pdf"> Beste praktijken voor het verscherpen van beelden in Dynamic Media Classic </a> downloadbare PDF.
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
   <td><p>Buiten de gemeenschappelijke beeldmontages beschikbaar in UI, steunt de Dynamische Media talrijke geavanceerde beeldwijzigingen die u in het <strong> gebied van de Modifiers van het Beeld </strong> kunt specificeren. Deze parameters worden bepaald in de <a href="https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/syntax-and-features/image-serving-http/c-command-overview"> het bevelverwijzing van het Protocol van de Server van het Beeld </a>.</p> <p>Belangrijk: de volgende functionaliteit die in de API wordt vermeld, wordt niet ondersteund:</p>
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

### Voorinstellingsopties voor afbeeldingen definiëren met afbeeldingsopties {#defining-image-preset-options-with-image-modifiers}

Naast de opties op de tabbladen Standaard en Geavanceerd kunt u ook afbeeldingsopties definiëren waarmee u meer opties hebt bij het definiëren van voorinstellingen voor afbeeldingen. Het beeld dat op het Dynamische Beeld teruggeeft van Media baseert API en in detail in de [ Verwijzing van het Protocol van HTTP ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-rendering-api/http-protocol-reference/c-ir-introduction#image-rendering-api) wordt bepaald.

Hieronder volgen enkele basisvoorbeelden van wat u kunt doen met wijzigingstoetsen voor afbeeldingen.

>[!NOTE]
>
>Sommige beeldbepalingen [ kunnen niet in Experience Manager ](#advanced-tab-options) worden gebruikt.

* [ op_invert ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-invert) - keert elke kleurencomponent voor een negatief beeldeffect om.

  ```xml {.line-numbers}
  &op_invert=1
  ```

  ![ 6_5_imagepreset-edit-invert ](assets/6_5_imagepreset-edit-invert.png)

* [ op_blur ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-blur) - past een vervagend filter op het beeld toe.

  ```xml {.line-numbers}
  &op_blur=7
  ```

  ![ 6_5_imagepreset-geef-onduidelijk ](assets/6_5_imagepreset-edit-blur.png)

* Gecombineerde opdrachten - op_vervagen en op-omkeren

  ```xml {.line-numbers}
  &op_invert=1&op_blur=7
  ```

  ![ chlimage_1-80 ](assets/chlimage_1-501.png)

* [ op_brightness ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-brightness) - vermindert of verhoogt de helderheid.

  ```xml {.line-numbers}
  &op_brightness=58
  ```

  ![ 6_5_imagepreset-geef-helderheid uit ](assets/6_5_imagepreset-edit-brightness.png)

* [ opac ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-opac) - Past beelddekking aan. Hiermee kunt u de dekking van de voorgrond verlagen.

  ```xml {.line-numbers}
  opac=29
  ```

  ![ 6_5_imagepreset-geef-opacity ](assets/6_5_imagepreset-edit-opacity.png)

### Voorinstellingen voor afbeeldingen bewerken {#modifying-image-presets}

1. Selecteer in Experience Manager het Experience Manager-logo voor toegang tot de algemene navigatieconsole en ga vervolgens naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Presets]** .

   ![ 6_5_imagepreset-editpreset ](assets/6_5_imagepreset-editpreset.png)

1. Selecteer een voorinstelling en selecteer vervolgens **[!UICONTROL Edit]** . Het venster **[!UICONTROL Edit Image Preset]** wordt geopend.
1. Breng de wijzigingen aan en selecteer **[!UICONTROL Save]** om de wijzigingen op te slaan of **[!UICONTROL Cancel]** om de wijzigingen te annuleren.

### Voorinstellingen voor afbeeldingen publiceren {#publishing-image-presets}

Voorinstellingen voor afbeeldingen worden automatisch voor u gepubliceerd.

### Afbeeldingsvoorinstellingen verwijderen {#deleting-image-presets}

1. Selecteer in Experience Manager het Experience Manager-logo voor toegang tot de algemene navigatieconsole en selecteer het pictogram Extra.
1. Ga naar **[!UICONTROL Assets]** > **[!UICONTROL Image Presets]**.
1. Selecteer een voorinstelling en selecteer vervolgens **[!UICONTROL Delete]** . Dynamische media bevestigen dat u deze wilt verwijderen. Selecteer **[!UICONTROL Delete]** om **[!UICONTROL Cancel]** te verwijderen of te selecteren om terug te keren naar Voorinstellingen afbeelding.
