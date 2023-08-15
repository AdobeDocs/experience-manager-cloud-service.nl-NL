---
title: Image Sets
description: Leer hoe u in Dynamic Media werkt met sets afbeeldingen.
contentOwner: Rick Brough
feature: Image Sets
role: User
exl-id: 2eb71f24-73d9-4b5c-8605-923a0e3d1505
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '2067'
ht-degree: 5%

---

# Image Sets {#image-sets}

Afbeeldingssets bieden gebruikers een geïntegreerde weergave, waarbij gebruikers verschillende weergaven van een item kunnen zien door op een miniatuurafbeelding te klikken. Met Afbeeldingssets kunt u alternatieve weergaven van een item presenteren en de viewer beschikt over zoomgereedschappen waarmee u afbeeldingen op de juiste wijze kunt bekijken.

Afbeeldingsets worden aangegeven door een banner met het woord `IMAGESET`. Als de Afbeeldingsset is gepubliceerd, wordt bovendien de publicatiedatum vermeld door de **[!UICONTROL World]** op de banner. De laatste wijzigingsdatum die wordt aangegeven door de **[!UICONTROL Pencil]** wordt weergegeven.

![chlimage_1-133](assets/chlimage_1-339.png)

In de afbeeldingsset kunt u ook stalen maken door een afbeeldingsset te maken en miniaturen toe te voegen.

Deze toepassing is handig wanneer u een item in een andere kleur, in een ander patroon of in een ander patroon wilt weergeven. Als u een afbeeldingsset met kleurstalen wilt maken, hebt u één afbeelding nodig voor elke andere kleur, elk patroon of elke afwerking die u aan de gebruikers wilt presenteren. Voor elke kleur, elk patroon of elke afwerking hebt u ook één kleur-, patroon- of eindstaal nodig.

Stel dat u afbeeldingen van uiteinden met verschillende kleurrekeningen wilt weergeven. De rekeningen zijn rood, groen en blauw. In dit geval hebt u drie opnamen van hetzelfde kapje nodig. Je hebt een opname nodig met een rood, een met een groen en een met een blauwe rekening. U hebt ook een rood, groen en blauw kleurenstaal nodig. De kleurstalen fungeren als de miniaturen die gebruikers in de Staalset-viewer klikken om het rode, groene of blauwe kader met vulling weer te geven.

>[!NOTE]
>
>Voor informatie over de gebruikersinterface van Middelen raadpleegt u [Elementen beheren met de Touch UI](/help/assets/manage-digital-assets.md).

Wanneer u een Reeks van het Beeld creeert, beveelt de Adobe de volgende beste praktijken aan en handhaaft de volgende grenzen:

| Type limiet | Beste praktijken | Oplegde limiet |
| --- | --- | --- |
| Aantal dubbele elementen per set | Geen duplicaten | 20 |
| Maximumaantal afbeeldingen per set | 5-10 afbeeldingen per set | 1000 |

Zie ook [Dynamic Media-beperkingen](/help/assets/dynamic-media/limitations.md).

## Snel starten: Afbeeldingssets {#quick-start-image-sets}

Zo kunt u snel aan de slag:

1. Optioneel. [Een voorinstelling voor een batchset maken](/help/assets/dynamic-media/batch-set-presets-dm.md) en pas het toe op een nieuwe omslag waar uw spin vastgestelde beelden worden geupload.

   Met een voorinstelling voor een batch-set kunt u het maken van de afbeeldingsset automatiseren.

   >[!IMPORTANT]
   >
   >De reeksen van de partij worden gecreeerd door IPS (het Systeem van de Productie van het Beeld) als deel van activa opnemen.

1. [Upload uw primaire bronafbeeldingen voor meerdere weergaven](#uploading-assets-in-image-sets).

   Upload de afbeeldingen voor uw afbeeldingssets. Vergeet niet dat gebruikers op afbeeldingen kunnen inzoomen in de viewer voor de afbeeldingsset. Kies uw afbeeldingen daarom zorgvuldig. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn.

   Zie [Dynamic Media - Ondersteunde rasterafbeeldingsindelingen](/help/assets/file-format-support.md#image-support-dynamic-media) voor een lijst met indelingen die worden ondersteund door Afbeeldingssets.

1. [Afbeeldingssets maken](#creating-image-sets).

   In de Reeksen van het Beeld, klikken de gebruikers duimnagelbeelden in de Vastgestelde Kijker van het Beeld.

   Als u een Afbeeldingsset in elementen wilt maken, selecteert u **[!UICONTROL Create]** > **[!UICONTROL Image Sets]**. Voeg vervolgens afbeeldingen toe en klik op **[!UICONTROL Save]**.

   Zie [Afbeeldingssets voorbereiden voor het uploaden en uploaden van uw bestanden](#uploading-assets-in-image-sets).

   Zie [Werken met kiezers](/help/assets/dynamic-media/working-with-selectors.md).

1. Toevoegen [Voorinstellingen voor Afbeeldingsset viewer](/help/assets/dynamic-media/managing-viewer-presets.md), indien nodig.

   Beheerders kunnen voorinstellingen voor de afbeeldingsset Viewer maken of wijzigen. Als u de afbeeldingsset wilt weergeven met een viewervoorinstelling, selecteert u de afbeeldingsset en selecteert u in de vervolgkeuzelijst voor het linkerspoor de optie **[!UICONTROL Viewers]**.

   Als u viewervoorinstellingen wilt maken of bewerken, raadpleegt u **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]**.

1. (Optioneel) [Afbeeldingssets weergeven](/help/assets/dynamic-media/image-sets.md#viewing-image-sets) die zijn gemaakt met behulp van voorinstellingen voor batchsets.
1. [Voorvertoning van afbeeldingssets](/help/assets/dynamic-media/previewing-assets.md).

   Selecteer de Afbeeldingsset en u kunt er een voorvertoning van weergeven. Selecteer de miniatuurpictogrammen om de Afbeeldingsset in de geselecteerde viewer te bekijken. U kunt verschillende viewers kiezen in het menu **[!UICONTROL Viewers]** , beschikbaar in de linkervervolgkeuzelijst.

1. [Afbeeldingssets publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

   Als u een Afbeeldingsset publiceert, wordt de URL- en insluitreeks geactiveerd. Bovendien moet u [een aangepaste viewervoorinstelling publiceren](/help/assets/dynamic-media/managing-viewer-presets.md) die u hebt gemaakt. Voorinstellingen voor viewers buiten de box zijn al gepubliceerd.

1. [URL&#39;s koppelen aan uw webtoepassing](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) of [De video- of afbeeldingsviewer insluiten](/help/assets/dynamic-media/embed-code.md).

   Experience Manager Assets maakt URL-aanroepen voor afbeeldingssets en activeert deze nadat u de afbeeldingssets hebt gepubliceerd. U kunt deze URL&#39;s kopiëren wanneer u elementen voorvertoont. U kunt ze ook insluiten op uw website.

   Selecteer de Afbeeldingsset en selecteer vervolgens in de vervolgkeuzelijst voor het linkerspoor de optie **[!UICONTROL Viewers]**.

   Zie [Een Afbeeldingsset koppelen aan een webpagina](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) en [De video- of afbeeldingsviewer insluiten](/help/assets/dynamic-media/embed-code.md).

Zie voor informatie over het bewerken van afbeeldingssets [Beeldsets bewerken](#editing-image-sets). Bovendien kunt u [Eigenschappen van Afbeeldingsset](/help/assets/manage-digital-assets.md#editing-properties).

Als u problemen ondervindt bij het maken van sets, raadpleegt u Afbeeldingen en sets in [Problemen met Dynamic Media oplossen](/help/assets/dynamic-media/troubleshoot-dm.md#images-and-sets).

## Elementen uploaden voor afbeeldingssets {#uploading-assets-in-image-sets}

Begin door de beeldactiva voor uw Reeksen van het Beeld te uploaden. Vergeet niet dat gebruikers op afbeeldingen kunnen inzoomen in de viewer voor de afbeeldingsset. Kies uw afbeeldingen daarom zorgvuldig. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn voor optimale zoomdetails. Dynamic Media kan afbeeldingen renderen tot 25 megapixels per pixel. U kunt bijvoorbeeld een afbeelding van 5000 x 5000 megapixel of een andere formaatcombinatie van maximaal 25 megapixels gebruiken.

<!-- Image Sets supports many image file formats, but lossless TIFF, PNG, and EPS images are recommended. -->

Zie [Dynamic Media - Ondersteunde rasterafbeeldingsindelingen](/help/assets/file-format-support.md#image-support-dynamic-media) voor een lijst met indelingen die worden ondersteund door Afbeeldingssets.

U kunt afbeeldingen voor afbeeldingssets uploaden zoals u dat zou doen [andere elementen in Elementen uploaden](/help/assets/manage-digital-assets.md#uploading-assets).

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
>U kunt ook automatisch afbeeldingssets maken via [voorinstellingen voor batchsets](/help/assets/dynamic-media/batch-set-presets-dm.md).
>**Belangrijk:** Batchsets worden gecreëerd door IPS (Image Production System) als onderdeel van assetopname.

Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. U kunt elementen handmatig opnieuw ordenen of sorteren nadat u ze hebt toegevoegd.

>[!NOTE]
>
>Afbeeldingssets worden niet ondersteund voor elementen met &quot;,&quot; (komma) in de bestandsnaam.

Wanneer u een Reeks van het Beeld creeert, beveelt de Adobe de volgende beste praktijken aan en handhaaft de volgende grenzen:

| Type limiet | Beste praktijken | Oplegde limiet |
| --- | --- | --- |
| Aantal dubbele elementen per set | Geen duplicaten | 20 |
| Maximumaantal afbeeldingen per set | 5-10 afbeeldingen per set | 1000 |

Zie ook [Dynamic Media-beperkingen](/help/assets/dynamic-media/limitations.md).

**Afbeeldingssets maken:**

1. Selecteer in Adobe Experience Manager het logo van de Experience Manager voor toegang tot de algemene navigatieconsole.
1. Tik op **[!UICONTROL Navigation]** > **[!UICONTROL Assets]**. Navigeer naar de plaats waar u een afbeeldingsset wilt maken en ga vervolgens naar **[!UICONTROL Create]** > **[!UICONTROL Image Set]** om de pagina van de Editor van de set Afbeeldingen te openen.

   U kunt de set ook maken vanuit een map die uw assets bevat.

   ![6_5_imagesets-createpulldown](assets/6_5_imagesets-createpulldown.png)

1. Op de pagina van de Editor voor de set afbeeldingen, in het dialoogvenster **[!UICONTROL Title]** voert u een naam in voor de afbeeldingsset. De naam wordt weergegeven in de banner in de Afbeeldingsset. Voer eventueel een beschrijving in.

   ![6_5_imageset-creatingnewset](assets/6_5_imageset-creatingnewset.png)

1. Voer een van de volgende handelingen uit:

   * Selecteer in de linkerbovenhoek van de pagina Editor afbeeldingsset de optie **[!UICONTROL Add Asset]**.

   * Selecteer in het midden van de pagina Editor afbeeldingsset de optie **[!UICONTROL Tap to open Asset Selector]**.

   Tik om elementen te selecteren die u in de afbeeldingsset wilt opnemen. Geselecteerde elementen hebben een vinkje. Als u klaar bent, selecteert u in de rechterbovenhoek van de pagina de optie **[!UICONTROL Select]**.

   Met de Asset Selector kunt u naar elementen zoeken door een trefwoord in te voeren en **[!UICONTROL Return]**. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en selecteer vervolgens het filter **[!UICONTROL Filter]** in de werkbalk. De weergave wijzigen door het pictogram Weergave te selecteren en **[!UICONTROL Column View]**, **[!UICONTROL Card View]**, of **[!UICONTROL List View]**.

   Zie [Werken met kiezers](/help/assets/dynamic-media/working-with-selectors.md).

   ![6_5_imageset-addingassets](assets/6_5_imageset-addingassets.png)

1. Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. Nadat u elementen hebt toegevoegd, kunt u deze handmatig opnieuw rangschikken of sorteren.

   Sleep indien nodig het pictogram Opnieuw ordenen van een element naar de rechterkant van de bestandsnaam van het element om de volgorde van de afbeeldingen in de lijst met sets te wijzigen.

   ![6_5_imageset-reorderassets](assets/6_5_imageset-reorderassets.png)

   Als u een miniatuur of staal wilt wijzigen, klikt u op het pictogram **+** **miniatuur** naast de afbeelding en gaat u naar de gewenste miniatuur of staal. Klik wanneer u alle afbeeldingen hebt geselecteerd op **[!UICONTROL Save]**.

1. (Optioneel) Voer een van de volgende handelingen uit:

   * Als u een afbeelding wilt verwijderen, selecteert u de afbeelding en **[!UICONTROL Delete Asset]**.

   * Selecteer **[!UICONTROL Preset]** Selecteer vervolgens een voorinstelling die u op alle elementen tegelijk wilt toepassen.

   >[!NOTE]
   >
   >Wanneer u de afbeeldingsset maakt, kunt u de miniatuur van de afbeeldingsset wijzigen. Of u kunt Experience Managers de miniatuur automatisch laten selecteren op basis van de elementen in de afbeeldingsset. Selecteer een miniatuur door **[!UICONTROL Change thumbnail]** boven het veld Titel op de pagina Editor afbeeldingsset. Selecteer vervolgens een willekeurige afbeelding (u kunt ook naar andere mappen navigeren om afbeeldingen te zoeken). Als u een miniatuur hebt geselecteerd, kunt u desgewenst een Experience Manager genereren op basis van de set afbeeldingen. Selecteer **[!UICONTROL Switch to]** **[!UICONTROL Automatic thumbnail]**.

1. Klik op **[!UICONTROL Save]**. De nieuwe afbeeldingsset wordt weergegeven in de map waarin u deze hebt gemaakt.

## Afbeeldingssets weergeven {#viewing-image-sets}

U kunt afbeeldingssets maken in de gebruikersinterface of automatisch met [voorinstellingen voor batchsets](/help/assets/dynamic-media/batch-set-presets-dm.md).

>[!IMPORTANT]
>
>De reeksen van de partij worden gecreeerd door IPS [Afbeeldingsproductiesysteem] als onderdeel van de opname van activa.

sets die zijn gemaakt met voorinstellingen voor batchsets, doen *niet* in de gebruikersinterface. U kunt deze sets op drie verschillende manieren weergeven. (Deze methoden zijn beschikbaar, zelfs als u de afbeeldingssets in de gebruikersinterface hebt gemaakt.)

* Open de eigenschappen van een element. Eigenschappen geven aan naar welke sets van het geselecteerde element wordt verwezen of een lid van. Selecteer de naam van de set om de volledige set weer te geven.

  ![6_5_imageset-assetproperties](assets/6_5_imageset-assetproperties.png)

* Van een lidafbeelding van om het even welke set. Selecteer de **[!UICONTROL Sets]** om de sets weer te geven waarvan het element lid is.

  ![6_5_imageset-set-pushDownmenu](assets/6_5_imageset-setspulldownmenu.png)

* Van onderzoek, kunt u selecteren **[!UICONTROL Filter]** vervolgens uitvouwen **[!UICONTROL Dynamic Media]** en selecteert u **[!UICONTROL Sets]**.

  De zoekopdracht retourneert overeenkomende sets die handmatig in de gebruikersinterface zijn gemaakt of die automatisch zijn gemaakt met voorinstellingen voor batchsets. Voor geautomatiseerde reeksen wordt de zoekquery uitgevoerd met &quot;Begint met&quot;. Deze zoekcriteria verschillen van Experience Manager die is gebaseerd op het gebruik van Bevat. Het filter instellen op **[!UICONTROL Sets]** is de enige manier om geautomatiseerde reeksen te zoeken.

  ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>U kunt sets weergeven in de gebruikersinterface zoals beschreven in [Afbeeldingssets bewerken](#editing-image-sets).

## Afbeeldingssets bewerken {#editing-image-sets}

U kunt verschillende bewerkingstaken uitvoeren op Afbeeldingssets, zoals:

* Voeg afbeeldingen toe aan de Afbeeldingsset.
* Wijzig de volgorde van de afbeeldingen in de afbeeldingsset.
* Elementen in de afbeeldingsset verwijderen.
* Voorinstellingen voor viewers toepassen.
* Verwijder de afbeeldingsset.

**Afbeeldingssets bewerken:**

1. Voer een van de volgende handelingen uit:

   * Houd de cursor boven een afbeeldingsset-element en selecteer **[!UICONTROL Edit]** (potloodpictogram).
   * Als u de cursor op een afbeeldingsset plaatst, selecteert u **[!UICONTROL Select]** (pictogram vinkje), selecteert u vervolgens **[!UICONTROL Edit]** in de werkbalk.
   * Tik op een afbeeldingsset-element en selecteer **[!UICONTROL Edit]** (potloodpictogram) op de werkbalk.

1. Voer een van de volgende handelingen uit om de afbeeldingen in de Afbeeldingsset te bewerken:

   * Als u elementen opnieuw wilt rangschikken, sleept u een afbeelding naar een nieuwe locatie (selecteer het pictogram voor opnieuw ordenen om items te verplaatsen).
   * Als u items in oplopende of aflopende volgorde wilt sorteren, klikt u op de kolomkop.
   * Als u een element wilt toevoegen of een bestaand element wilt bijwerken, klikt u op de knop **[!UICONTROL Add Asset]**. Navigeer naar een element, selecteer het en selecteer het **[!UICONTROL Select]** in de rechterbovenhoek van de pagina.
     >[!NOTE]
     >
     >Als u de afbeelding verwijdert die de Experience Manager voor de miniatuur gebruikt door deze te vervangen door een andere afbeelding, wordt het oorspronkelijke element nog steeds weergegeven.
   * Als u een element wilt verwijderen, selecteert u het en selecteert u het **[!UICONTROL Delete Asset]**.
   * Selecteer **[!UICONTROL Preset]** selecteert u vervolgens een viewervoorinstelling.
   * Als u een miniatuur wilt toevoegen of wijzigen, selecteert u het miniatuurpictogram rechts van het element. Navigeer naar de nieuwe miniatuur of het nieuwe stalenelement, selecteer het en selecteer het **[!UICONTROL Select]**.
   * Als u een hele afbeeldingsset wilt verwijderen, navigeert u naar de afbeeldingsset, selecteert u deze en selecteert u **[!UICONTROL Delete]**.

   >[!NOTE]
   >
   >U kunt de afbeeldingen in een Afbeeldingsset bewerken. Ga naar de set en selecteer **[!UICONTROL Set Members]** in het linkerspoor. Als u het bewerkingsvenster wilt openen, selecteert u het potloodpictogram op een element.

1. Tikken **[!UICONTROL Save]** wanneer u klaar bent met bewerken.

## Voorvertoning van afbeeldingssets {#previewing-image-sets}

Zie [Elementen voorvertonen](/help/assets/dynamic-media/previewing-assets.md).

## Afbeeldingssets publiceren {#publishing-image-sets}

Zie [Elementen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).
