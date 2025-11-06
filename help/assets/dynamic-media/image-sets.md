---
title: Afbeeldingssets
description: Leer hoe u met afbeeldingssets werkt in Dynamische media.
contentOwner: Rick Brough
feature: Image Sets
role: User
exl-id: 2eb71f24-73d9-4b5c-8605-923a0e3d1505
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2078'
ht-degree: 3%

---

# Afbeeldingssets {#image-sets}

Afbeeldingssets bieden gebruikers een geïntegreerde weergave, waarbij gebruikers verschillende weergaven van een item kunnen zien door op een miniatuurafbeelding te klikken. Met Afbeeldingssets kunt u alternatieve weergaven van een item presenteren en de viewer beschikt over zoomgereedschappen waarmee u afbeeldingen op de juiste wijze kunt bekijken.

Afbeeldingsets worden aangegeven door een banner met het woord `IMAGESET`. Als de Afbeeldingsset is gepubliceerd, staat bovendien de publicatiedatum die wordt aangegeven door het pictogram **[!UICONTROL World]** op de banner. De laatste wijzigingsdatum die wordt aangegeven door het pictogram **[!UICONTROL Pencil]** , wordt ook weergegeven.

![&#x200B; chlimage_1-133 &#x200B;](assets/chlimage_1-339.png)

In de afbeeldingsset kunt u ook stalen maken door een afbeeldingsset te maken en miniaturen toe te voegen.

Deze toepassing is handig wanneer u een item in een andere kleur, in een ander patroon of in een ander patroon wilt weergeven. Als u een afbeeldingsset met kleurstalen wilt maken, hebt u één afbeelding nodig voor elke andere kleur, elk patroon of elke afwerking die u aan de gebruikers wilt presenteren. Voor elke kleur, elk patroon of elke afwerking hebt u ook één kleur-, patroon- of eindstaal nodig.

Stel dat u afbeeldingen van uiteinden met verschillende kleurrekeningen wilt weergeven. De rekeningen zijn rood, groen en blauw. In dit geval hebt u drie opnamen van hetzelfde kapje nodig. Je hebt een opname nodig met een rood, een met een groen en een met een blauwe rekening. U hebt ook een rood, groen en blauw kleurenstaal nodig. De kleurstalen fungeren als de miniaturen die gebruikers in de Staalset-viewer klikken om het rode, groene of blauwe kader met vulling weer te geven.

>[!NOTE]
>
>Voor informatie over het gebruikersinterface van Assets, zie [&#x200B; activa met Aanraakinterface beheren &#x200B;](/help/assets/manage-digital-assets.md).

Als u een Afbeeldingsset maakt, raadt Adobe de volgende aanbevolen procedures aan en past het de volgende limieten toe:

| Type limiet | Beste praktijken | Oplegde limiet |
| --- | --- | --- |
| Aantal dubbele elementen per set | Geen duplicaten | 20 |
| Maximumaantal afbeeldingen per set | 5-10 afbeeldingen per set | 1000 |

Zie ook [&#x200B; Dynamische beperkingen van Media &#x200B;](/help/assets/dynamic-media/limitations.md).

## Snel starten: Afbeeldingssets {#quick-start-image-sets}

Zo kunt u snel aan de slag:

1. Optioneel. [&#x200B; creeer een partijreeks vooraf ingesteld &#x200B;](/help/assets/dynamic-media/batch-set-presets-dm.md) en pas het op een nieuwe omslag toe waar uw spin vastgestelde beelden worden geupload.

   Met een voorinstelling voor een batch-set kunt u het maken van de afbeeldingsset automatiseren.

   >[!IMPORTANT]
   >
   >De reeksen van de partij worden gecreeerd door IPS (het Systeem van de Productie van het Beeld) als deel van activa opnemen.

1. [&#x200B; uploadt uw primaire bronbeelden voor veelvoudige meningen &#x200B;](#uploading-assets-in-image-sets).

   Upload de afbeeldingen voor uw afbeeldingssets. Vergeet niet dat gebruikers op afbeeldingen kunnen inzoomen in de viewer voor de afbeeldingsset. Kies uw afbeeldingen daarom zorgvuldig. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn.

   Zie [&#x200B; Dynamische Media - de Ondersteunde formaten van het roosterbeeld &#x200B;](/help/assets/file-format-support.md#image-support-dynamic-media) voor een lijst van formaten die door de Reeksen van het Beeld worden gesteund.

1. [&#x200B; creeer de Reeksen van het Beeld &#x200B;](#creating-image-sets).

   In de Reeksen van het Beeld, klikken de gebruikers duimnagelbeelden in de Vastgestelde Kijker van het Beeld.

   Selecteer **[!UICONTROL Create]** > **[!UICONTROL Image Sets]** om een Afbeeldingsset te maken in Assets. Voeg vervolgens afbeeldingen toe en klik op **[!UICONTROL Save]** .

   Zie [&#x200B; Vastgestelde activa van het Beeld voor upload en het Uploaden van uw dossiers &#x200B;](#uploading-assets-in-image-sets) voorbereiden.

   Zie [&#x200B; Werk met Kiezers &#x200B;](/help/assets/dynamic-media/working-with-selectors.md).

1. Voeg [&#x200B; Voorinstellingen van de Kijker van het Beeld toe Vastgestelde &#x200B;](/help/assets/dynamic-media/managing-viewer-presets.md), zoals nodig.

   Beheerders kunnen voorinstellingen voor de afbeeldingsset Viewer maken of wijzigen. Als u de afbeeldingsset wilt weergeven met een viewervoorinstelling, selecteert u de afbeeldingsset en selecteert u **[!UICONTROL Viewers]** in de vervolgkeuzelijst voor de linkerrails.

   Zie **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]** voor informatie over het maken of bewerken van voorinstellingen voor viewers.

1. (Facultatief) [&#x200B; Reeksen van het Beeld van de Mening &#x200B;](/help/assets/dynamic-media/image-sets.md#viewing-image-sets) die gebruikend partijreeks werden gecreeerd vooraf instelt.
1. [&#x200B; de Reeksen van het Beeld van de Voorproef &#x200B;](/help/assets/dynamic-media/previewing-assets.md).

   Selecteer de Afbeeldingsset en u kunt er een voorvertoning van weergeven. Selecteer de miniatuurpictogrammen om de Afbeeldingsset in de geselecteerde viewer te bekijken. U kunt verschillende viewers kiezen in het menu **[!UICONTROL Viewers]** , dat beschikbaar is in de vervolgkeuzelijst voor de linkertrack.

1. [&#x200B; publiceer de Reeksen van het Beeld &#x200B;](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

   Als u een Afbeeldingsset publiceert, wordt de URL- en insluitreeks geactiveerd. Bovendien moet u [&#x200B; publiceren om het even welke vooraf ingestelde douaneviewer &#x200B;](/help/assets/dynamic-media/managing-viewer-presets.md) die u hebt gecreeerd. Voorinstellingen voor viewers buiten de box zijn al gepubliceerd.

1. [&#x200B; Verbinding URLs aan uw Toepassing van het Web &#x200B;](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) of [&#x200B; bed de Video of Kijker van het Beeld &#x200B;](/help/assets/dynamic-media/embed-code.md) in.

   Experience Manager Assets maakt URL-aanroepen voor afbeeldingssets en activeert deze nadat u de afbeeldingssets hebt gepubliceerd. U kunt deze URL&#39;s kopiëren wanneer u elementen voorvertoont. U kunt ze ook insluiten op uw website.

   Selecteer de Afbeeldingsset en selecteer vervolgens in de vervolgkeuzelijst voor het linkerspoor de optie **[!UICONTROL Viewers]** .

   Zie [&#x200B; Verbinding een Beeld dat aan een Web-pagina &#x200B;](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) wordt geplaatst en [&#x200B; bed de Video of Kijker van het Beeld &#x200B;](/help/assets/dynamic-media/embed-code.md) in.

Om de Reeksen van het Beeld uit te geven, zie [&#x200B; het uitgeven de Reeksen van het Beeld &#x200B;](#editing-image-sets). Bovendien kunt u [&#x200B; Vastgestelde eigenschappen van het Beeld bekijken en uitgeven &#x200B;](/help/assets/manage-digital-assets.md#editing-properties).

Als u kwesties hebt die reeksen creëren, zie Beelden en Reeksen in [&#x200B; problemen oplossen Dynamische Media &#x200B;](/help/assets/dynamic-media/troubleshoot-dm.md#images-and-sets).

## Elementen uploaden voor afbeeldingssets {#uploading-assets-in-image-sets}

Begin door de beeldactiva voor uw Reeksen van het Beeld te uploaden. Vergeet niet dat gebruikers op afbeeldingen kunnen inzoomen in de viewer voor de afbeeldingsset. Kies uw afbeeldingen daarom zorgvuldig. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn voor optimale zoomdetails. Met dynamische media kunnen afbeeldingen tot 25 megapixels worden gerenderd. U kunt bijvoorbeeld een afbeelding van 5000 x 5000 megapixel of een andere formaatcombinatie van maximaal 25 megapixels gebruiken.

<!-- Image Sets supports many image file formats, but lossless TIFF, PNG, and EPS images are recommended. -->

Zie [&#x200B; Dynamische Media - de Ondersteunde formaten van het roosterbeeld &#x200B;](/help/assets/file-format-support.md#image-support-dynamic-media) voor een lijst van formaten die door de Reeksen van het Beeld worden gesteund.

U kunt beelden voor de Reeksen van het Beeld zoals u [&#x200B; om het even welke andere activa in Assets &#x200B;](/help/assets/manage-digital-assets.md#uploading-assets) uploadt.

### Afbeeldingsset-elementen voorbereiden voor uploaden {#preparing-image-set-assets-for-upload}

Voordat u Afbeeldingssets maakt, moet u ervoor zorgen dat de afbeeldingen de juiste grootte en indeling hebben.

Als u een Afbeeldingsset met meerdere weergaven wilt maken, hebt u afbeeldingen nodig die een item vanuit verschillende gezichtspunten weergeven of verschillende aspecten van hetzelfde item weergeven. Het doel is om de belangrijke kenmerken van een item te benadrukken zodat de kijkers een volledig beeld hebben van hoe het wordt weergegeven of wat het doet.

Omdat gebruikers kunnen inzoomen op afbeeldingen in Afbeeldingssets, moet u ervoor zorgen dat de afbeeldingen ten minste 2000 pixels groot zijn. Experience Manager Assets ondersteunt veel bestandsindelingen voor afbeeldingen, maar TIFF-, PNG- en EPS-afbeeldingen zonder gegevensverlies worden aanbevolen.

>[!NOTE]
>
>Ga als volgt te werk als u miniaturen gebruikt om productstalen aan te geven:
>
>Maak vignetten of verschillende opnamen van dezelfde afbeelding, zodat deze in verschillende kleuren, patronen of afwerkingen worden weergegeven. U hebt ook miniatuurbestanden nodig die overeenkomen met de verschillende kleuren, patronen of afwerkingen. Als u bijvoorbeeld miniaturen wilt weergeven met een Afbeeldingsset die hetzelfde jasje in zwart, bruin en groen toont, hebt u het volgende nodig:
>
>* Een zwarte, bruine en groene opname van hetzelfde jasje.
>* Een zwarte, bruine en groene kleurminiatuur.

## Afbeeldingssets maken {#creating-image-sets}

U kunt Afbeeldingssets maken via de gebruikersinterface of via de API.

>[!NOTE]
>
>U kunt beeldreeksen automatisch ook tot stand brengen door [&#x200B; partij vastgestelde vooraf instelt &#x200B;](/help/assets/dynamic-media/batch-set-presets-dm.md).
>**Belangrijk:** de reeksen van de Partij worden gecreeerd door IPS (het Systeem van de Productie van het Beeld) als deel van activa opnemen.

Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. U kunt elementen handmatig opnieuw ordenen of sorteren nadat u ze hebt toegevoegd.

>[!NOTE]
>
>Afbeeldingssets worden niet ondersteund voor elementen met &quot;,&quot; (komma) in de bestandsnaam.

Als u een Afbeeldingsset maakt, raadt Adobe de volgende aanbevolen procedures aan en past het de volgende limieten toe:

| Type limiet | Beste praktijken | Oplegde limiet |
| --- | --- | --- |
| Aantal dubbele elementen per set | Geen duplicaten | 20 |
| Maximumaantal afbeeldingen per set | 5-10 afbeeldingen per set | 1000 |

Zie ook [&#x200B; Dynamische beperkingen van Media &#x200B;](/help/assets/dynamic-media/limitations.md).

**om de Reeksen van het Beeld tot stand te brengen:**

1. Selecteer in Adobe Experience Manager het Experience Manager-logo voor toegang tot de algemene navigatieconsole.
1. Selecteer **[!UICONTROL Navigation]** > **[!UICONTROL Assets]** . Navigeer naar de plaats waar u een afbeeldingsset wilt maken en ga vervolgens naar **[!UICONTROL Create]** > **[!UICONTROL Image Set]** om de pagina Editor afbeeldingsset te openen.

   U kunt de set ook maken vanuit een map die uw elementen bevat.

   ![&#x200B; 6_5_imagesets-createpulldown &#x200B;](assets/6_5_imagesets-createpulldown.png)

1. Voer op de pagina Editor afbeeldingsset in het veld **[!UICONTROL Title]** een naam in voor de afbeeldingsset. De naam wordt weergegeven in de banner in de Afbeeldingsset. Voer eventueel een beschrijving in.

   ![&#x200B; 6_5_imageset-creatingnewset &#x200B;](assets/6_5_imageset-creatingnewset.png)

1. Voer een van de volgende handelingen uit:

   * Selecteer **[!UICONTROL Add Asset]** in de linkerbovenhoek van de pagina Editor afbeeldingsset.

   * Selecteer **[!UICONTROL Tap to open Asset Selector]** in het midden van de pagina Editor afbeeldingsset.

   Selecteer deze optie om elementen te selecteren die u in de afbeeldingsset wilt opnemen. Geselecteerde elementen hebben een vinkje. Wanneer u klaar bent, selecteert u **[!UICONTROL Select]** in de rechterbovenhoek van de pagina.

   Met de Asset Selector kunt u naar elementen zoeken door een trefwoord in te voeren en **[!UICONTROL Return]** te selecteren. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en selecteer vervolgens het pictogram **[!UICONTROL Filter]** op de werkbalk. Wijzig de weergave door het pictogram Weergave te selecteren en **[!UICONTROL Column View]** , **[!UICONTROL Card View]** of **[!UICONTROL List View]** te selecteren.

   Zie [&#x200B; Werkend met Kiezers &#x200B;](/help/assets/dynamic-media/working-with-selectors.md).

   ![&#x200B; 6_5_imageset-addingassets &#x200B;](assets/6_5_imageset-addingassets.png)

1. Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. Nadat u elementen hebt toegevoegd, kunt u deze handmatig opnieuw rangschikken of sorteren.

   Sleep indien nodig het pictogram Opnieuw ordenen van een element naar de rechterkant van de bestandsnaam van het element om de volgorde van de afbeeldingen in de lijst met sets te wijzigen.

   ![&#x200B; 6_5_imageset-reorderassets &#x200B;](assets/6_5_imageset-reorderassets.png)

   Als u een miniatuur of staal wilt wijzigen, klikt u op het pictogram **+** **miniatuur** naast de afbeelding en gaat u naar de gewenste miniatuur of staal. Klik wanneer u alle afbeeldingen hebt geselecteerd op **[!UICONTROL Save]**.

1. (Optioneel) Voer een van de volgende handelingen uit:

   * Als u een afbeelding wilt verwijderen, selecteert u de afbeelding en selecteert u **[!UICONTROL Delete Asset]** .

   * Als u een voorinstelling wilt toepassen, selecteert u **[!UICONTROL Preset]** in de rechterbovenhoek van de pagina en selecteert u vervolgens een voorinstelling die u op alle elementen tegelijk wilt toepassen.

   >[!NOTE]
   >
   >Wanneer u de afbeeldingsset maakt, kunt u de miniatuur van de afbeeldingsset wijzigen. Of u kunt Experience Manager de miniatuur automatisch laten selecteren op basis van de elementen in de afbeeldingsset. Als u een miniatuur wilt selecteren, selecteert u **[!UICONTROL Change thumbnail]** boven het veld Titel op de pagina Editor afbeeldingsset. Selecteer vervolgens een willekeurige afbeelding (u kunt ook naar andere mappen navigeren om afbeeldingen te zoeken). Als u een miniatuur hebt geselecteerd, kiest u **[!UICONTROL Switch to]** **[!UICONTROL Automatic thumbnail]** en wilt u dat Experience Manager een miniatuur genereert op basis van de set afbeeldingen.

1. Klik op **[!UICONTROL Save]**. De gemaakte afbeeldingsset wordt weergegeven in de map waarin u deze hebt gemaakt.

## Afbeeldingssets weergeven {#viewing-image-sets}

U kunt beeldreeksen of in het gebruikersinterface of automatisch tot stand brengen gebruikend [&#x200B; partij vastgestelde vooraf instelt &#x200B;](/help/assets/dynamic-media/batch-set-presets-dm.md).

>[!IMPORTANT]
>
>De reeksen van de partij worden gecreeerd door het IPS [ Systeem van de Productie van het Beeld ] als deel van activaopname.

Nochtans, verschijnen de reeksen die gebruikend partij worden gecreeerd vooraf instelt, *niet* in het gebruikersinterface. U kunt deze sets op drie verschillende manieren weergeven. (Deze methoden zijn beschikbaar, zelfs als u de afbeeldingssets in de gebruikersinterface hebt gemaakt.)

* Open de eigenschappen van een element. Eigenschappen geven aan naar welke sets van het geselecteerde element wordt verwezen of een lid van. Selecteer de naam van de set om de volledige set weer te geven.

  ![&#x200B; 6_5_imageset-assetproperties &#x200B;](assets/6_5_imageset-assetproperties.png)

* Van een lidafbeelding van om het even welke set. Selecteer het menu **[!UICONTROL Sets]** om de sets weer te geven waarvan het element lid is.

  ![&#x200B; 6_5_imageset-setlealdownmenu &#x200B;](assets/6_5_imageset-setspulldownmenu.png)

* Vanuit de zoekopdracht kunt u **[!UICONTROL Filter]** selecteren, vervolgens **[!UICONTROL Dynamic Media]** uitvouwen en **[!UICONTROL Sets]** selecteren.

  De zoekopdracht retourneert overeenkomende sets die handmatig in de gebruikersinterface zijn gemaakt of die automatisch zijn gemaakt met voorinstellingen voor batchsets. Voor geautomatiseerde reeksen wordt de zoekquery uitgevoerd met &quot;Begint met&quot;. Deze zoekcriteria verschillen van Experience Manager, dat is gebaseerd op het gebruik van Bevat. Het instellen van het filter op **[!UICONTROL Sets]** is de enige manier om geautomatiseerde sets te doorzoeken.

  ![&#x200B; chlimage_1-134 &#x200B;](assets/chlimage_1-134.png)

>[!NOTE]
>
>U kunt reeksen als gebruikersinterface bekijken zoals die in [&#x200B; wordt beschreven het Uitgeven Reeksen van het Beeld &#x200B;](#editing-image-sets).

## Afbeeldingssets bewerken {#editing-image-sets}

U kunt verschillende bewerkingstaken uitvoeren op Afbeeldingssets, zoals:

* Voeg afbeeldingen toe aan de Afbeeldingsset.
* Wijzig de volgorde van de afbeeldingen in de afbeeldingsset.
* Elementen in de afbeeldingsset verwijderen.
* Voorinstellingen voor viewers toepassen.
* Verwijder de afbeeldingsset.

**om de Reeksen van het Beeld uit te geven:**

1. Voer een van de volgende handelingen uit:

   * Houd de cursor boven een afbeeldingsset-element en selecteer vervolgens **[!UICONTROL Edit]** (potloodpictogram).
   * Als u de cursor boven een afbeeldingsset plaatst, selecteert u **[!UICONTROL Select]** (vinkje) en selecteert u **[!UICONTROL Edit]** op de werkbalk.
   * Selecteer een afbeeldingsset en selecteer vervolgens **[!UICONTROL Edit]** (potloodpictogram) op de werkbalk.

1. Voer een van de volgende handelingen uit om de afbeeldingen in de Afbeeldingsset te bewerken:

   * Als u elementen opnieuw wilt rangschikken, sleept u een afbeelding naar een nieuwe locatie (selecteer het pictogram voor opnieuw ordenen om items te verplaatsen).
   * Als u items in oplopende of aflopende volgorde wilt sorteren, klikt u op de kolomkop.
   * Als u een element wilt toevoegen of een bestaand element wilt bijwerken, klikt u op **[!UICONTROL Add Asset]** . Navigeer naar een element, selecteer het en selecteer vervolgens **[!UICONTROL Select]** in de rechterbovenhoek van de pagina.

     >[!NOTE]
     >
     >Als u de afbeelding verwijdert die Experience Manager voor de miniatuur gebruikt door deze te vervangen door een andere afbeelding, wordt het oorspronkelijke element nog steeds weergegeven.

   * Als u een element wilt verwijderen, selecteert u het en selecteert u **[!UICONTROL Delete Asset]** .
   * Als u een voorinstelling wilt toepassen, selecteert u **[!UICONTROL Preset]** in de rechterbovenhoek van de pagina en selecteert u vervolgens een voorinstelling voor de viewer.
   * Als u een miniatuur wilt toevoegen of wijzigen, selecteert u het miniatuurpictogram rechts van het element. Navigeer naar de nieuwe miniatuur of het nieuwe staalelement, selecteer het en selecteer vervolgens **[!UICONTROL Select]** .
   * Als u een volledige afbeeldingsset wilt verwijderen, navigeert u naar de afbeeldingsset, selecteert u deze en selecteert u **[!UICONTROL Delete]** .

   >[!NOTE]
   >
   >U kunt de afbeeldingen in een Afbeeldingsset bewerken. Navigeer naar de set en selecteer **[!UICONTROL Set Members]** in de linkertrack. Als u het bewerkingsvenster wilt openen, selecteert u het potloodpictogram op een element.

1. Selecteer **[!UICONTROL Save]** wanneer u klaar bent met bewerken.

## Voorvertoning van afbeeldingssets {#previewing-image-sets}

Zie [&#x200B; activa van de Voorproef &#x200B;](/help/assets/dynamic-media/previewing-assets.md).

## Afbeeldingssets publiceren {#publishing-image-sets}

Zie [&#x200B; publiceren Assets &#x200B;](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).
