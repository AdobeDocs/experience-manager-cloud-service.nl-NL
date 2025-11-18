---
title: Afbeeldingen bewerken
description: Bewerk afbeeldingen met [!DNL Adobe Express] powered options en sla bijgewerkte afbeeldingen op als versies.
role: User
exl-id: cfc4c7b7-da8c-4902-9935-0e3d4388b975
feature: Best Practices, Interactive Images, Smart Crop, Smart Imaging
source-git-commit: 744c76f29a37610313835074f2f13fdd8f098465
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 0%

---

# Afbeeldingen bewerken in [!DNL Assets view] {#edit-images-in-assets-view}

De Assets-weergave UI maakt basisbeeldbewerking mogelijk die wordt aangedreven door Adobe Express, geïntegreerd in de gebruikersinterface. Deze bewerking omvat het aanpassen van de grootte, het verwijderen van de achtergrond, bijsnijden en het converteren tussen JPEG- en PNG-formaten. Daarnaast maakt het geavanceerde bewerking mogelijk via de Adobe Express-interface, ingebed in de Assets-weergave-UI.

Na het bewerken van een afbeelding kun je de nieuwe afbeelding als een nieuwe versie opslaan. Versiebeheer helpt je om later terug te keren naar de originele asset indien nodig. Om een afbeelding te bewerken, [open je de preview](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/navigate-view#preview-assets) en klik je op **Afbeelding** bewerken.

>[!NOTE]
>
>Je kunt afbeeldingen van PNG- en JPEG-bestandstypen bewerken met [!DNL Adobe Express].

<!--The editing actions that are available are Spot healing, Crop and straighten, Resize image, and Adjust image.-->

## Afbeelding bewerken {#edit-image}

Ga naar de gebruikersinterface van Assets View, gebruik de link - Assets View[&#x200B; en &#x200B;](https://experience.adobe.com/#/assets)selecteer de juiste repository. Neem contact op met de beheerder van uw organisatie om toegang te krijgen.
Voor aanvullende referentiegegevens zie - [Begin met Adobe Experience Manager Assets View](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/get-started-assets-view), [Understand the Assets view gebruikersinterface](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/navigate-assets-view#understand-interface-navigation) en [Assets View use cases](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/get-started-assets-view#use-cases).
<!--
>[!CONTEXTUALHELP]
>id="assets_express_integration"
>title="Adobe Express Integration"
>abstract="Easy and intuitive image-editing tools powered by Adobe Express available directly within AEM Assets to increase content reuse and accelerate content velocity."-->

### Afbeelding bewerken in Assets View met Adobe Express {#edit-image-on-assets-view-using-adobe-express}

Na het navigeren naar Assets View klik **je op Assets**, selecteer je een afbeelding en klik **je vervolgens op Bewerken** vanaf de bovenste rail. Het nieuwe scherm toont de beschikbare bewerkingsopties die worden aangedreven door Adobe Express, waaronder het wijzigen van grootte, het verwijderen van achtergronden, bijsnijden en het converteren tussen JPEG- en PNG-formaten.

#### Afbeelding verkleinen {#resize-image-using-express}

Het aanpassen van een afbeelding tot een specifieke grootte is een populaire gebruikssituatie. Met Assets View kun je afbeeldingen snel aanpassen aan de gangbare fotogroottes door vooraf berekende nieuwe resoluties voor specifieke fotogroottes te bieden. Om de afbeelding te vergroten met Assets View, volg je de onderstaande stappen:

1. Klik op **Afbeelding wijzigen** in het linker venster. Een dialoogvenster toont de mogelijkheden voor het aanpassen van afbeeldingen die worden aangedreven door Adobe Express.
1. Selecteer het juiste sociale mediaplatform uit de keuzelijst voor het aanpassen van grootte en selecteer de afbeeldingsgrootte in de weergegeven opties.
1. Schaal het beeld indien nodig met het **veld Image Scale** .
1. Klik **[!UICONTROL Apply]** om je wijzigingen toe te passen.
   ![Beeldbewerking met Adobe Express](assets/adobe-express-resize-image.png)

   Je bewerkte afbeelding is beschikbaar om te downloaden. Je kunt het bewerkte asset opslaan als een nieuwe versie van hetzelfde asset of als een nieuw asset opslaan.
   ![Afbeelding opslaan met Adobe Express](assets/adobe-express-resize-save.png)

#### Achtergrond verwijderen {#remove-background-using-express}

Je kunt de achtergrond van een afbeelding verwijderen door de onderstaande stappen te volgen:

1. Klik op **Achtergrond** verwijderen in het linkerpaneel. Experience Manager Assets toont de afbeelding zonder achtergrond.
1. Klik **[!UICONTROL Apply]** om je wijzigingen toe te passen.
   ![Afbeelding opslaan met Adobe Express](assets/adobe-express-remove-background.png)

   Je bewerkte afbeelding is beschikbaar om te downloaden. Je kunt het bewerkte asset opslaan als een nieuwe versie van hetzelfde asset of als een nieuw asset opslaan.

#### Bijsnijd afbeelding {#crop-image-using-express}

Het transformeren van een afbeelding naar een perfecte grootte is eenvoudig met ingebedde [!DNL Adobe Express] snelle acties.

1. Klik **[!UICONTROL Crop Image]** vanuit het linkerpaneel.
2. Sleep de handvatten op de hoeken van de afbeelding om de gewenste crop te maken.
3. Klik op **[!UICONTROL Apply]**.
   ![Afbeelding opslaan met Adobe Express](assets/adobe-express-crop-image.png)
De bijgesneden afbeelding is beschikbaar om te downloaden. Je kunt het bewerkte asset opslaan als een nieuwe versie van hetzelfde asset of als een nieuw asset opslaan.

#### JPEG omzetten naar PNG {#convert-image-types-using-express}

Je kunt snel converteren tussen JPEG- en PNG-afbeeldingsformaten met Adobe Express. Voer de volgende stappen uit:

1. Klik **op JPEG naar PNG** of **PNG naar JPEG** vanuit het linker paneel.
   <!--![Convert to PNG with Adobe Express](/help/using/assets/adobe-express-convert-image.png)-->
1. Klik op **[!UICONTROL Download]**.

#### Beperkingen {#limitations-adobe-express}

* Ondersteunde beeldresolutie: Minimaal - 50 pixels, Maximum - 6000 pixels per dimensie.
* Maximale ondersteunde bestandsgrootte: 17 MB.

### Afbeeldingen bewerken in Adobe Express embedded editor {#edit-images-in-adobe-express-embedded-editor}

Gebruikers met Express-recht kunnen de ingebouwde Express-editor vanuit de Assets View gebruiken om eenvoudig inhoud te bewerken en nieuwe content te maken met GenAI van Adobe Firefly. Deze functie verbetert het hergebruik van content en versnelt de snelheid van content. Je kunt ook vooraf gedefinieerde elementen gebruiken om je asset er prachtig uit te laten zien of snelle acties uitvoeren om je afbeelding met slechts een paar klikken te bewerken.

![express in essentials UI](/help/assets/assets/express-in-essentials-ui.jpg)
Om afbeeldingen te bewerken met [!DNL Adobe Express] een ingebedde editor, volgt u de onderstaande stappen:

1. Ga naar AEM Assets View via de link - AEM Assets View[&#x200B; en &#x200B;](https://experience.adobe.com/#/assets)selecteer de juiste repository.
1. Klik op **Assets**, open een map en selecteer een afbeelding.
1. Klik op **Openen in Adobe Express**. Het beeld opent op een expressdoek.
1. Maak de vereiste aanpassingen aan de afbeelding.
1. Als je project vereist dat je meer pagina&#39;s toevoegt, klik **dan op Toevoegen**, selecteer assets, open een map, selecteer een afbeelding om op de canvaspagina te zetten en voer vervolgens de vereiste bewerkingen aan de afbeelding uit.
1. Om één of meer assets op te slaan, klik op **Opslaan**. Het opslaan-dialoogvenster toont de opslaanopties. Om te kiezen tussen de opslagopties, volg je een van de onderstaande instructies die aansluit bij jouw wensen:
   1. Om één pagina op te slaan, klik **je op Opgeslagen als versie** om de afbeelding als nieuwe versie te exporteren (waarbij het originele formaat behouden blijft), en sla deze op in dezelfde map.

   1. Om een enkele pagina op te slaan, klik je **op Opslaan als nieuw asset** om het asset naar een ander formaat te exporteren en sla het op in een map als een nieuw asset.

   1. Om één pagina van meerdere pagina&#39;s op te slaan, klik **je op Opgeslagen als versie** om het asset in het oorspronkelijke formaat en op de locatie op te slaan.

   1. Om meerdere pagina&#39;s of één pagina tussen meerdere pagina&#39;s op te slaan, klik je **op Opslaan als Nieuw Object**. Deze actie exporteert de enkele of meerdere assets naar een map en slaat ze op als nieuw asset of assets in het origineel of een ander formaat.

1. In het opslaan-dialoogvenster:
   1. Voer een naam van het bestand in het **veld &#39;Opgeslagen als** &#39;.
   1. Selecteer een bestemmingsmap.
   1. Optioneel: Geef details zoals project- of campagnenaam, trefwoorden, kanalen, tijdschema en regio.
1. Klik op **Sla op Sla op als versie** of **Sla op als nieuw asset** om het asset(en) op te slaan.

#### Beperkingen van het bewerken van afbeeldingen in de Express Editor {#limitations-of-editing-images-in-the-express-editor}

* Ondersteund bestandstype: JPEG of PNG.
* Maximale ondersteunde bestandsgrootte: 40 MB.
* Ondersteund breedte- en hoogtebereik: 65MP (bijvoorbeeld 8K x 8K of 16K x 4K).
* Herlaad de pagina om het laatst opgeslagen nieuwe asset in de bronmap te zien.

### Maak nieuwe assets aan met Adobe Express {#create-new-embedded-editor}

[!DNL Assets view] Stelt je in staat om een nieuw sjabloon vanaf nul te maken met behulp van [!DNL Adobe Express] een embedded editor. Om een nieuw asset te creëren met [!DNL Adobe Express], voer je de onderstaande stappen uit:

1. Navigeer naar **[!UICONTROL My Workspace]** en klik **[!UICONTROL Create]** binnen de Adobe Express-banner die bovenaan wordt weergegeven. [!DNL Adobe Express] Leeg canvas wordt weergegeven binnen de [!DNL Assets view] gebruikersinterface.
1. Maak je content met behulp van [&#128279;](https://helpx.adobe.com/in/express/using/work-with-templates.html)sjablonen. Anders navigeer naar **[!UICONTROL Your Stuff]** om bestaande inhoud aan te passen.
1. Zodra je het bewerken hebt afgerond, klik **[!UICONTROL Save]** je op .
1. Geef het bestemmingspad voor het aangemaakte asset aan en klik **[!UICONTROL Save as new asset]** op .

#### Beperkingen {#limitations}

* Je kunt alleen afbeeldingen van `JPEG` en `PNG` formateertypen wijzigen.
* De assetgrootte moet minder dan 80 MB zijn voor desktopapparaten en 40 MB voor mobiele apparaten.
* De ondersteunde breedte- en hoogtebereik ligt tussen 50 en 8000 pixels.
* Je kunt een afbeelding opslaan in `PDF`, `JPEG`, of `PNG` formaat.

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

* Geef productfeedback via de [!UICONTROL Feedback] optie die beschikbaar is in de gebruikersinterface van de Assets-weergave.

* Geef feedback op documentatie via [!UICONTROL Edit this page] ![&#39;edit the page&#39;](assets/do-not-localize/edit-page.png) of [!UICONTROL Log an issue] ![maak een GitHub-issue](assets/do-not-localize/github-issue.png) beschikbaar in de rechterzijbalk.

* Neem contact op met [de klantenservice](https://experienceleague.adobe.com/?support-solution=General#support)

>[!MORELIKETHIS]
>
>* [Snelle acties in Adobe Express](https://helpx.adobe.com/in/express/using/resize-image.html)
>* [Bekijk de versiegeschiedenis van een asset](navigate-assets-view.md)
