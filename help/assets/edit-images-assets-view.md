---
title: Afbeeldingen bewerken
description: Afbeeldingen bewerken met [!DNL Adobe Express] Aangedreven opties en sparen bijgewerkte beelden als versies.
role: User
exl-id: cfc4c7b7-da8c-4902-9935-0e3d4388b975
feature: Best Practices, Interactive Images, Smart Crop, Smart Imaging
source-git-commit: 23b43f22b62451c9d0a5460999fcd43479438d7e
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 0%

---

# Afbeeldingen bewerken in [!DNL Assets view] {#edit-images-in-assets-view}

In de Assets-weergave kunt u basisafbeeldingen bewerken, zoals vergroten/verkleinen, verwijderen van de achtergrond, uitsnijden en omzetten tussen de JPEG- en PNG-indeling. Bovendien is geavanceerde bewerking mogelijk dankzij integratie met Adobe Express. Nadat u een afbeelding hebt bewerkt, kunt u de nieuwe afbeelding opslaan als een nieuwe versie. Met Versioning kunt u het oorspronkelijke element later herstellen als dat nodig is. Als u een afbeelding wilt bewerken, [zijn voorvertoning openen](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/navigate-view#preview-assets) en klik op **Afbeelding bewerken**.

>[!NOTE]
>
>U kunt afbeeldingen van de bestandstypen PNG en JPEG bewerken met [!DNL Adobe Express].

<!--The editing actions that are available are Spot healing, Crop and straighten, Resize image, and Adjust image.-->

## Afbeelding bewerken {#edit-image}

Land op Assets View, met de link - [Assets View](https://experience.adobe.com/#/assets) en het selecteren van de juiste opslagplaats. Neem contact op met de beheerder van uw organisatie om toegang te krijgen.
Zie voor aanvullende informatie: [Ga aan de slag met de Adobe Experience Manager Assets-weergave](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/get-started-assets-view), [De gebruikersinterface van de Assets-weergave begrijpen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/navigate-assets-view#understand-interface-navigation), en [Assets View-gebruikerskwesties](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/get-started-assets-view#use-cases).
<!--
>[!CONTEXTUALHELP]
>id="assets_express_integration"
>title="Adobe Express Integration"
>abstract="Easy and intuitive image-editing tools powered by Adobe Express available directly within AEM Assets to increase content reuse and accelerate content velocity."-->

### Afbeelding bewerken in Assets-weergave met Adobe Express {#edit-image-on-assets-view-using-adobe-express}

Na het landen in de weergave Assets klikt u op **Assets** selecteert u een afbeelding en klikt u op **Bewerken** vanaf de bovenste spoorstaaf. In het nieuwe scherm worden de beschikbare bewerkingsopties weergegeven, zoals vergroten/verkleinen, verwijderen van de achtergrond, uitsnijden en omzetten tussen de JPEG- en PNG-indeling.

#### Grootte afbeelding wijzigen {#resize-image-using-express}

Een afbeelding vergroten of verkleinen tot een bepaalde grootte is een veelgebruikte optie. Met de Assets-weergave kunt u snel de grootte van afbeeldingen aanpassen aan de gangbare fotoformaten door vooraf berekende nieuwe resoluties voor specifieke fotoformaten te bieden. Voer de onderstaande stappen uit als u het formaat van de afbeelding wilt wijzigen met Assets View:

1. Klikken **Formaat afbeelding wijzigen** in het linkerdeelvenster.
1. Selecteer het juiste sociale-mediaplatform in de vervolgkeuzelijst Formaat wijzigen en selecteer de afbeeldingsgrootte in de weergegeven opties.
1. De afbeelding indien nodig schalen met de **Schaal van afbeelding** veld.
1. Klikken **[!UICONTROL Apply]** om uw wijzigingen toe te passen.
   ![Afbeeldingen bewerken met Adobe Express](assets/adobe-express-resize-image.png)

   De bewerkte afbeelding kan worden gedownload. U kunt het bewerkte element opslaan als een nieuwe versie van hetzelfde element of het opslaan als een nieuw element.
   ![Afbeelding opslaan met Adobe Express](assets/adobe-express-resize-save.png)

#### Achtergrond verwijderen {#remove-background-using-express}

U kunt de achtergrond uit een afbeelding verwijderen door de onderstaande stappen te volgen:

1. Klikken **Achtergrond verwijderen** in het linkerdeelvenster. Experience Manager Assets geeft de afbeelding zonder achtergrond weer.
1. Klikken **[!UICONTROL Apply]** om uw wijzigingen toe te passen.
   ![Afbeelding opslaan met Adobe Express](assets/adobe-express-remove-background.png)

   De bewerkte afbeelding kan worden gedownload. U kunt het bewerkte element opslaan als een nieuwe versie van hetzelfde element of het opslaan als een nieuw element.

#### Afbeelding uitsnijden {#crop-image-using-express}

Een afbeelding transformeren tot een perfecte grootte is eenvoudig met ingesloten [!DNL Adobe Express] snelle acties.

1. Klikken **[!UICONTROL Crop Image]** in het linkerdeelvenster.
2. Sleep de grepen op de hoeken van de afbeelding om de gewenste uitsnijding te maken.
3. Klik op **[!UICONTROL Apply]**.
   ![Afbeelding opslaan met Adobe Express](assets/adobe-express-crop-image.png)
De uitgesneden afbeelding kan worden gedownload. U kunt het bewerkte element opslaan als een nieuwe versie van hetzelfde element of het opslaan als een nieuw element.

#### Omzetten tussen afbeeldingsbestandstypen {#convert-image-types-using-express}

U kunt met Adobe Express snel JPEG- en PNG-afbeeldingsindelingen omzetten. Voer de volgende stappen uit:

1. Klikken **JPEG naar PNG** of **PNG naar JPEG** in het linkerdeelvenster.
   <!--![Convert to PNG with Adobe Express](/help/using/assets/adobe-express-convert-image.png)-->
1. Klik op **[!UICONTROL Download]**.

#### Beperkingen {#limitations-adobe-express}

* Ondersteunde afbeeldingsresolutie: minimaal - 50 pixels, maximaal - 6000 pixels per afmeting.

* Maximale ondersteunde bestandsgrootte: 17 MB.

### Afbeeldingen bewerken in ingesloten Adobe Express-editor {#edit-images-in-adobe-express-embedded-editor}

Gebruikers met Express-machtiging kunnen de ingesloten Express-editor vanuit de Assets-weergave gebruiken om inhoud eenvoudig te bewerken en nieuwe inhoud te maken met GenAI vanaf de Adobe Firefly. Hiermee verbetert u het hergebruik van inhoud en versnelt u de snelheid van de inhoud. U kunt ook vooraf gedefinieerde elementen gebruiken om uw elementen er verbluffend uit te laten zien of snelle acties uitvoeren om uw afbeelding met slechts een paar klikken te bewerken.
![UI voor het uitdrukken in essentiële gegevens](/help/assets/assets/express-in-essentials-ui.jpg)
Afbeeldingen bewerken met [!DNL Adobe Express] ingesloten editor, voert u de onderstaande stappen uit:

1. Ga naar AEM Assets View met behulp van link - [AEM Assets View](https://experience.adobe.com/#/assets) en selecteer de juiste opslagplaats.
1. Klikken **Assets**, voert u een map in en selecteert u een afbeelding.
1. Klikken **Openen in Adobe Express**. De afbeelding wordt geopend op een express canvas.
1. Breng de gewenste wijzigingen in de afbeelding aan.
1. Als voor uw project meer pagina&#39;s moeten worden toegevoegd, klikt u op **Toevoegen** selecteert u elementen, voert u een map in, selecteert u een afbeelding die u naar de canvaspagina wilt brengen en voert u de vereiste bewerkingen uit op de afbeelding.
1. Klik op **Opslaan**. Het dialoogvenster Opslaan wordt weergegeven.

   >[!NOTE]
   >
   > **1. Voor één pagina**
   >
   > **Opslaan als versie:** Deze functie ondersteunt het opslaan van slechts één element. Selecteer deze optie om de afbeelding als een nieuwe versie te exporteren (met behoud van de oorspronkelijke indeling) en deze op te slaan in dezelfde map.
   > **Opslaan als nieuw element:** Selecteer deze optie als u het element in een andere indeling wilt exporteren dan het origineel en het als nieuw element wilt opslaan in een willekeurige map.
   >  
   > **2. Voor meerdere pagina&#39;s**
   >
   > **Opslaan als versie:** Deze functie ondersteunt het opslaan van slechts één element. Als u één pagina van veelvoudige pagina&#39;s wilt bewaren, selecteer deze optie om het middel in zijn originele formaat en plaats op te slaan.\
   > **Opslaan als nieuw element:** Met deze optie exporteert u meerdere elementen of één element naar een willekeurige map en slaat u deze op als nieuwe elementen met hun bestandsindeling als origineel of anders.

1. In het dialoogvenster Opslaan:
   1. Voer een naam in voor het bestand in het dialoogvenster **Opslaan als** veld.
   1. Selecteer een doelmap.
   1. Optioneel: geef details op, zoals de naam van het project of de campagne, trefwoorden, kanalen, het tijdframe en het gebied.
1. Klikken **Opslaan als versie** of **Opslaan als nieuw element** om de elementen op te slaan.

#### Beperkingen bij het bewerken van afbeeldingen in de Express Editor {#limitations-of-editing-images-in-the-express-editor}

* Ondersteund bestandstype: JPEG of PNG.
* Maximale ondersteunde bestandsgrootte: 40 MB.
* Ondersteund breedte- en hoogtebereik: tussen 50 en 8000 pixels.
* Laad de pagina opnieuw om het laatst opgeslagen nieuwe element in de bronmap weer te geven.

### Nieuwe elementen maken met Adobe Express {#create-new-embedded-editor}

[!DNL Assets view] kunt u een nieuwe sjabloon maken met [!DNL Adobe Express] ingesloten editor. Een nieuw element maken met [!DNL Adobe Express]Voer de volgende stappen uit:

1. Navigeren naar **[!UICONTROL My Workspace]** en klik op **[!UICONTROL Create]** in de Adobe Express-banner die bovenaan wordt weergegeven. [!DNL Adobe Express] leeg canvas wordt weergegeven in het dialoogvenster [!DNL Assets view] gebruikersinterface.
1. Uw inhoud maken met [Sjablonen](https://helpx.adobe.com/in/express/using/work-with-templates.html). Anders navigeert u naar **[!UICONTROL Your Stuff]** bestaande inhoud wijzigen.
1. Als u klaar bent met bewerken, klikt u op **[!UICONTROL Save]**.
1. Doelpad opgeven voor het gemaakte element en klikken **[!UICONTROL Save as new asset]**.

#### Beperkingen {#limitations}

* U kunt alleen afbeeldingen wijzigen van `JPEG` en `PNG` opmaaktypen.
* De grootte van het element moet kleiner zijn dan 40 MB.
* U kunt een afbeelding opslaan in `PDF`, `JPEG`, of `PNG` indelingen.

<!--
## Edit images using [!DNL Adobe Photoshop Express] {#edit-using-photoshop-express}

<!--
After editing an image, you can save the new image as a new version. Versioning helps you to revert to the original asset later, if needed. To edit an image, [open its preview](navigate-assets-view.md#preview-assets) and click **[!UICONTROL Edit Image]** ![edit icon](assets/do-not-localize/edit-icon.png) from the rail on the right.

![Options to edit an image](assets/edit-image2.png)

*Figure: The options to edit images are powered by [!DNL Adobe Photoshop Express].*
-->
<!--
### Touch up images {#spot-heal-images-using-photoshop-express}

If there are minor spots or small objects on an image, you can edit and remove the spots using the spot healing feature provided by Adobe Photoshop.

The brush samples the retouched area and makes the repaired pixels blend seamlessly into the rest of the image. Use a brush size that is only slightly larger than the spot you want to fix.

![Spot healing edit option](assets/edit-spot-healing.png)

<!-- 
TBD: See if we should give backlinks to PS docs for these concepts.
For more information about how Spot Healing works in Photoshop, see [retouching and repairing photos](https://helpx.adobe.com/photoshop/using/retouching-repairing-images.html). 
-->
<!-- 
### Crop and straighten images {#crop-straighten-images-using-photoshop-express}

Using the crop and straighten option that you can do basic cropping, rotate image, flip it horizontally or vertically, and crop it to dimensions suitable for popular social media websites.

To save your edits, click **[!UICONTROL Crop Image]**. After editing, you can save the new image as a version.

![Option to crop and straighten](assets/edit-crop-straighten.png)

Many default options let you crop your image to the best proportions that fit various social media profiles and posts.

### Resize image {#resize-image-using-photoshop-express}

You can view the common photo sizes in centimeters or inches to know the dimensions. By default, the resizing method retains the aspect ratio. To manually override the aspect ratio, click ![](assets/do-not-localize/lock-closed-icon.png).

Enter the dimensions and click **[!UICONTROL Resize Image]** to resize the image. Before you save the changes as a version, you can either undo all the changes done before saving by clicking [!UICONTROL Undo] or you can change the specific step in the editing process by clicking [!UICONTROL Revert].

![Options when resizing an image](assets/resize-image.png)

### Adjust image {#adjust-image-using-photoshop-express}

[!DNL Assets view] lets you adjust the color, tone, contrast, and more, with just a few clicks. Click **[!UICONTROL Adjust image]** in the edit window. The following options are available in the right sidebar:

* **Popular**: [!UICONTROL High Contrast & Detail], [!UICONTROL Desaturated Contrast], [!UICONTROL Aged Photo], [!UICONTROL B&W Soft], and [!UICONTROL B&W Sepia Tone].
* **Color**: [!UICONTROL Natural], [!UICONTROL Bright], [!UICONTROL High Contrast], [!UICONTROL High Contrast & Detail], [!UICONTROL Vivid], and [!UICONTROL Matte].
* **Creative**: [!UICONTROL Desaturated Contrast], [!UICONTROL Cool Light], [!UICONTROL Turquoise & Red], [!UICONTROL Soft Mist], [!UICONTROL Vintage Instant], [!UICONTROL Warm Contrast], [!UICONTROL Flat & Green], [!UICONTROL Red Lift Matte], [!UICONTROL Warm Shadows], and [!UICONTROL Aged Photo].
* **B&W**: [!UICONTROL B&W Landscape], [!UICONTROL B&W High Contrast], [!UICONTROL B&W Punch], [!UICONTROL B&W Low Contrast], [!UICONTROL B&W Flat], [!UICONTROL B&W Soft], [!UICONTROL B&W Infrared], [!UICONTROL B&W Selenium Tone], [!UICONTROL B&W Sepia Tone], and [!UICONTROL B&W Split Tone].
* **Vignetting**: [!UICONTROL None], [!UICONTROL Light], [!UICONTROL Medium], and [!UICONTROL Heavy].

![Adjust image by editing](assets/adjust-image.png)

<!--
TBD: Insert a video of the available social media options.
-->

### Volgende stappen {#next-steps}

* Feedback geven op het product met de [!UICONTROL Feedback] beschikbaar in de gebruikersinterface van de Assets-weergave.

* Documentfeedback geven met [!UICONTROL Edit this page] ![de pagina bewerken](assets/do-not-localize/edit-page.png) of [!UICONTROL Log an issue] ![een GitHub-probleem maken](assets/do-not-localize/github-issue.png) beschikbaar op de rechterzijbalk.

* Contact [Klantenservice](https://experienceleague.adobe.com/?support-solution=General#support)

>[!MORELIKETHIS]
>
>* [Snelle acties in Adobe Express](https://helpx.adobe.com/in/express/using/resize-image.html)
>* [De versiegeschiedenis van een element weergeven](navigate-assets-view.md)
