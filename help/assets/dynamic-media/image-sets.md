---
title: Image Sets
description: Leer hoe u in Dynamic Media werkt met sets afbeeldingen.
translation-type: tm+mt
source-git-commit: a11ce4c60ddfa345a3be20e3cc4f99ce86d1e84b
workflow-type: tm+mt
source-wordcount: '1980'
ht-degree: 9%

---


# Image Sets {#image-sets}

Afbeeldingssets bieden gebruikers een geïntegreerde weergave, waarbij gebruikers verschillende weergaven van een item kunnen zien door op een miniatuurafbeelding te klikken. Met Afbeeldingssets kunt u alternatieve weergaven van een item presenteren en de viewer beschikt over zoomgereedschappen waarmee u afbeeldingen op de juiste wijze kunt bekijken.

Afbeeldingsets worden aangegeven door een banner met het woord `IMAGESET`. Als de Afbeeldingsset is gepubliceerd, staat bovendien de publicatiedatum die wordt aangegeven door het pictogram **[!UICONTROL World]** op de banner. De laatste wijzigingsdatum die wordt aangegeven door het pictogram **[!UICONTROL Pencil]**, wordt ook weergegeven.

![chlimage_1-133](assets/chlimage_1-339.png)

In de afbeeldingsset kunt u ook stalen maken door een afbeeldingsset te maken en miniaturen toe te voegen.

Deze toepassing is handig wanneer u een item in een andere kleur, in een ander patroon of in een ander patroon wilt weergeven. Als u een afbeeldingsset met kleurstalen wilt maken, hebt u één afbeelding nodig voor elke andere kleur, elk patroon of elke afwerking die u aan de gebruikers wilt presenteren. Voor elke kleur, elk patroon of elke afwerking hebt u ook één kleur-, patroon- of eindstaal nodig.

Stel dat u afbeeldingen van uiteinden met verschillende kleurrekeningen wilt weergeven. de rekeningen zijn rood , groen en blauw . In dit geval hebt u drie opnamen van hetzelfde kapje nodig. Je hebt een opname nodig met een rood, een met een groen en een met een blauwe rekening. U hebt ook een rood, groen en blauw kleurenstaal nodig. De kleurstalen fungeren als de miniaturen die gebruikers in de Staalset-viewer klikken om het rode, groene of blauwe kader met vulling weer te geven.

>[!NOTE]
>
>Zie [Elementen beheren met de aanraakinterface](/help/assets/manage-digital-assets.md) voor informatie over de gebruikersinterface van Elementen.

## Snel starten: Afbeeldingssets {#quick-start-image-sets}

Zo kunt u snel aan de slag:

1. Optioneel. [Maak een voorinstelling voor een batchset en pas deze toe op een nieuwe map waar uw centrifugeafbeeldingen worden geüpload. ](/help/assets/dynamic-media/batch-set-presets-dm.md) 

   Met een voorinstelling voor een batch-set kunt u het maken van de afbeeldingsset automatiseren.

   >[!IMPORTANT]
   >
   >De reeksen van de partij worden gecreeerd door IPS (het Systeem van de Productie van het Beeld) als deel van activa opnemen.

1. [Upload uw primaire bronafbeeldingen voor meerdere weergaven.](#uploading-assets-in-image-sets)

   Upload de afbeeldingen voor uw afbeeldingssets. Vergeet niet dat gebruikers op afbeeldingen kunnen inzoomen in de viewer voor de afbeeldingsset. Kies uw afbeeldingen daarom zorgvuldig. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn in de grootste dimensie. Experience Manager-elementen ondersteunen een groot aantal bestandsindelingen voor afbeeldingen, maar het wordt aanbevolen afbeeldingen zonder verlies in de indeling TIFF, PNG en EPS te gebruiken.

1. [Afbeeldingssets maken.](#creating-image-sets)

   In de Reeksen van het Beeld, klikken de gebruikers duimnagelbeelden in de Vastgestelde Kijker van het Beeld.

   Tik of klik op **[!UICONTROL Create > Image Sets]** om een Afbeeldingsset in elementen te maken. Voeg vervolgens afbeeldingen toe en klik op **[!UICONTROL Save]**.

   Zie [Afbeeldingsset-elementen voorbereiden voor het uploaden en uploaden van uw bestanden](#uploading-assets-in-image-sets).

   Zie [Werken met kiezers.](/help/assets/dynamic-media/working-with-selectors.md)

1. Voeg [Voorinstellingen voor de afbeeldingsset Viewer toe](/help/assets/dynamic-media/managing-viewer-presets.md), indien nodig.

   Beheerders kunnen voorinstellingen voor de afbeeldingsset Viewer maken of wijzigen. Als u de afbeeldingsset wilt weergeven met een viewer-voorinstelling, selecteert u de afbeeldingsset en selecteert u **[!UICONTROL Viewers]** in de vervolgkeuzelijst met linkerrails.

   Zie **[!UICONTROL Tools > Assets > Viewer Presets]** voor informatie over het maken of bewerken van voorinstellingen voor viewers.

1. (Optioneel) [Afbeeldingssets weergeven](/help/assets/dynamic-media/image-sets.md#viewing-image-sets) die zijn gemaakt met behulp van voorinstellingen voor batchsets.
1. [Voorvertoning van afbeeldingssets.](/help/assets/dynamic-media/previewing-assets.md)

   Selecteer de Afbeeldingsset en u kunt er een voorvertoning van weergeven. Tik op de miniatuurpictogrammen om de Afbeeldingsset in de geselecteerde viewer te bekijken. U kunt verschillende kijkers van **[!UICONTROL Viewers]** menu kiezen, beschikbaar van de linkerspoordrop-down lijst.

1. [Afbeeldingssets publiceren.](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)

   Als u een Afbeeldingsset publiceert, wordt de URL- en insluitreeks geactiveerd. Daarnaast moet u [een aangepaste viewer-voorinstelling](/help/assets/dynamic-media/managing-viewer-presets.md) publiceren die u hebt gemaakt. Voorinstellingen voor viewers buiten de box zijn al gepubliceerd.

1. [Koppel URL&#39;s aan uw webtoepassing ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) of  [sluit de video- of afbeeldingsviewer](/help/assets/dynamic-media/embed-code.md) in.

   Experience Manager Assets maakt URL-aanroepen voor afbeeldingssets en activeert deze nadat u de afbeeldingssets hebt gepubliceerd. U kunt deze URL&#39;s kopiëren wanneer u elementen voorvertoont. U kunt ze ook insluiten op uw website.

   Selecteer de Afbeeldingsset en selecteer **[!UICONTROL Viewers]** in de vervolgkeuzelijst voor het linkerspoor.

   Zie [Een afbeeldingset koppelen aan een webpagina](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) en [De video- of afbeeldingsviewer insluiten](/help/assets/dynamic-media/embed-code.md).

Zie [Afbeeldingssets bewerken als u Afbeeldingssets wilt bewerken.](#editing-image-sets) Bovendien kunt u de eigenschappen [ van de ](/help/assets/manage-digital-assets.md#editing-properties)Afbeeldingsset weergeven en bewerken.

Als u problemen hebt met het maken van sets, raadpleegt u Afbeeldingen en sets in [Problemen met Dynamic Media](/help/assets/dynamic-media/troubleshoot-dm.md#images-and-sets) oplossen.

## Elementen uploaden voor afbeeldingssets {#uploading-assets-in-image-sets}

Begin door de beeldactiva voor uw Reeksen van het Beeld te uploaden. Vergeet niet dat gebruikers op afbeeldingen kunnen inzoomen in de viewer voor de afbeeldingsset. Kies uw afbeeldingen daarom zorgvuldig. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn voor optimale zoomdetails. Dynamic Media kan afbeeldingen renderen tot 25 megapixels per pixel. U kunt bijvoorbeeld een afbeelding van 5000 x 5000 megapixel of een andere formaatcombinatie van maximaal 25 megapixels gebruiken.

Afbeeldingssets ondersteunen veel bestandsindelingen voor afbeeldingen, maar afbeeldingen zonder verlies van de indeling TIFF, PNG en EPS worden aanbevolen.

U kunt afbeeldingen voor Afbeeldingssets uploaden zoals u [andere elementen in Elementen uploadt](/help/assets/manage-digital-assets.md#uploading-assets).

### Afbeeldingsset-elementen voorbereiden voor uploaden {#preparing-image-set-assets-for-upload}

Voordat u Afbeeldingssets maakt, moet u ervoor zorgen dat de afbeeldingen de juiste grootte en indeling hebben.

Als u een Afbeeldingsset met meerdere weergaven wilt maken, hebt u afbeeldingen nodig die een item vanuit verschillende gezichtspunten weergeven of verschillende aspecten van hetzelfde item weergeven. Het doel is om de belangrijke kenmerken van een item te benadrukken, zodat gebruikers een volledig beeld hebben van hoe het eruit ziet of werkt.

Omdat gebruikers kunnen inzoomen op afbeeldingen in Afbeeldingssets, moet u ervoor zorgen dat de afbeeldingen ten minste 2000 pixels groot zijn. Experience Manager-elementen ondersteunen een groot aantal bestandsindelingen voor afbeeldingen, maar het wordt aanbevolen afbeeldingen zonder verlies in de indeling TIFF, PNG en EPS te gebruiken.

>[!NOTE]
>
>Ga als volgt te werk als u miniaturen gebruikt om productstalen aan te geven:
>
>Maak vignetten of verschillende opnamen van dezelfde afbeelding, zodat deze in verschillende kleuren, patronen of afwerkingen worden weergegeven. U hebt ook miniatuurbestanden nodig die overeenkomen met de verschillende kleuren, patronen of afwerkingen. Als u bijvoorbeeld miniaturen wilt weergeven met een Afbeeldingsset die hetzelfde jasje in zwart, bruin en groen toont, hebt u het volgende nodig:
>
>* Een zwarte, bruine en groene opname van hetzelfde jasje.
>* Een zwarte, bruine en groene kleurminiatuur.


## Afbeeldingssets {#creating-image-sets} maken

U kunt Afbeeldingssets maken via de gebruikersinterface of via de API.

>[!NOTE]
>
>U kunt ook automatisch afbeeldingssets maken via [voorinstellingen voor batchsets](/help/assets/dynamic-media/batch-set-presets-dm.md).
>**Belangrijk:** Batchsets worden gecreëerd door IPS (Image Production System) als onderdeel van assetopname.

Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. U kunt elementen handmatig opnieuw ordenen of sorteren nadat u ze hebt toegevoegd.

>[!NOTE]
>
>Afbeeldingssets worden niet ondersteund voor elementen met &quot;,&quot; (komma) in de bestandsnaam.

**Een afbeeldingsset maken**

1. Tik in Adobe Experience Manager op het logo van de Experience Manager om toegang te krijgen tot de algemene navigatieconsole.
1. Tik op **[!UICONTROL Navigation > Assets]**. Ga naar de plaats waar u een afbeeldingset wilt maken en tik vervolgens op **[!UICONTROL Create > Image Set]** om de pagina Editor van afbeeldingset te openen.

   U kunt de set ook maken vanuit een map die uw assets bevat.

   ![6_5_imagesets-createpulldown](assets/6_5_imagesets-createpulldown.png)

1. Voer op de pagina Editor afbeeldingsset in het veld **[!UICONTROL Title]** een naam in voor de afbeeldingsset. De naam wordt weergegeven in de banner in de Afbeeldingsset. Voer eventueel een beschrijving in.

   ![6_5_imageset-creatingnewset](assets/6_5_imageset-creatingnewset.png)

1. Voer een van de volgende handelingen uit:

   * Tik op **[!UICONTROL Add Asset]** in de linkerbovenhoek van de pagina Editor afbeeldingsset.

   * Tik in het midden van de pagina Editor afbeeldingsset op **[!UICONTROL Tap to open Asset Selector]**.
   Tik om elementen te selecteren die u in de afbeeldingsset wilt opnemen. Geselecteerde elementen hebben een vinkje. Tik **[!UICONTROL Select]** bij de rechterbovenhoek van de pagina als u klaar bent.

   Met de assetkiezer kunt u naar assets zoeken door een trefwoord te typen en op **[!UICONTROL Return]** te tikken of klikken. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en tik op het pictogram **[!UICONTROL Filter]** op de werkbalk. Wijzig de weergave door te tikken op het pictogram Weergave en **[!UICONTROL Column View]**, **[!UICONTROL Card View]** of **[!UICONTROL List View]** te selecteren.

   Zie [Werken met kiezers.](/help/assets/dynamic-media/working-with-selectors.md)

   ![6_5_imageset-addingassets](assets/6_5_imageset-addingassets.png)

1. Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. Nadat u elementen hebt toegevoegd, kunt u deze handmatig opnieuw rangschikken of sorteren.

   Sleep indien nodig het pictogram Opnieuw ordenen van een element naar de rechterkant van de bestandsnaam van het element om de volgorde van de afbeeldingen in de lijst met sets te wijzigen.

   ![6_5_imageset-reorderassets](assets/6_5_imageset-reorderassets.png)

   Als u een miniatuur of staal wilt wijzigen, klikt u op het pictogram **+** **miniatuur** naast de afbeelding en gaat u naar de gewenste miniatuur of staal. Klik wanneer u alle afbeeldingen hebt geselecteerd op **[!UICONTROL Save]**.

1. (Optioneel) Voer een van de volgende handelingen uit:

   * Als u een afbeelding wilt verwijderen, selecteert u de afbeelding en tikt u op **[!UICONTROL Delete Asset]**.

   * Tik op **[!UICONTROL Preset]** en selecteer vervolgens een voorinstelling die u op alle elementen tegelijk wilt toepassen om een voorinstelling toe te passen in de rechterbovenhoek van de pagina.
   >[!NOTE]
   >
   >Wanneer u de afbeeldingsset maakt, kunt u de miniatuur van de afbeeldingsset wijzigen. Of u kunt Experience Managers de miniatuur automatisch laten selecteren op basis van de elementen in de afbeeldingsset. Tik op **[!UICONTROL Change thumbnail]** boven het veld Titel op de pagina Editor afbeeldingsset om een miniatuur te selecteren. Selecteer vervolgens een willekeurige afbeelding (u kunt ook naar andere mappen navigeren om afbeeldingen te zoeken). Als u een miniatuur hebt geselecteerd, kiest u **[!UICONTROL Switch to]** **[!UICONTROL Automatic thumbnail]** als u wilt dat Experience Manager een miniatuur genereert uit de afbeeldingsset.

1. Klik op **[!UICONTROL Save]**. De nieuwe afbeeldingsset wordt weergegeven in de map waarin u deze hebt gemaakt.

## Afbeeldingssets {#viewing-image-sets} weergeven

U kunt afbeeldingssets maken in de gebruikersinterface of automatisch met [voorinstellingen voor batchsets](/help/assets/dynamic-media/batch-set-presets-dm.md).

>[!IMPORTANT]
>
>Batchsets worden door het IPS [Image Production System] gemaakt als onderdeel van het opnemen van elementen.

Sets die zijn gemaakt met voorinstellingen voor batchsets, worden echter *niet* weergegeven in de gebruikersinterface. U kunt deze sets op drie verschillende manieren weergeven. (Deze methoden zijn ook beschikbaar als u de afbeeldingssets in de gebruikersinterface hebt gemaakt.)

* Open de eigenschappen van een element. Eigenschappen geven aan naar welke sets van het geselecteerde element wordt verwezen of een lid van. Tik op de naam van de set om de volledige set weer te geven.

   ![6_5_imageset-assetproperties](assets/6_5_imageset-assetproperties.png)

* Van een lidafbeelding van om het even welke set. Selecteer het menu **[!UICONTROL Sets]** om de sets weer te geven waarvan het element lid is.

   ![6_5_imageset-set-pushDownmenu](assets/6_5_imageset-setspulldownmenu.png)

* Bij het zoeken kunt u **[!UICONTROL Filter]** selecteren, vervolgens **[!UICONTROL Dynamic Media]** uitvouwen en **[!UICONTROL Sets]** selecteren.

   De zoekopdracht retourneert overeenkomende sets die handmatig in de gebruikersinterface zijn gemaakt of die automatisch zijn gemaakt met voorinstellingen voor batchsets. Voor geautomatiseerde reeksen wordt de zoekquery uitgevoerd met &quot;Begint met&quot;. Deze zoekcriteria verschillen van Experience Manager die is gebaseerd op het gebruik van Bevat. Het instellen van het filter op **[!UICONTROL Sets]** is de enige manier om geautomatiseerde sets te doorzoeken.

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>U kunt sets weergeven in de gebruikersinterface zoals wordt beschreven in [Afbeeldingssets bewerken](#editing-image-sets).

## Afbeeldingssets {#editing-image-sets} bewerken

U kunt verschillende bewerkingstaken uitvoeren op Afbeeldingssets, zoals:

* Voeg afbeeldingen toe aan de Afbeeldingsset.
* Wijzig de volgorde van de afbeeldingen in de afbeeldingsset.
* Elementen in de afbeeldingsset verwijderen.
* Voorinstellingen voor viewers toepassen.
* Verwijder de afbeeldingsset.

**Afbeeldingssets bewerken**

1. Voer een van de volgende handelingen uit:

   * Houd de muisaanwijzer boven een afbeeldingsset en tik op **[!UICONTROL Edit]** (potloodpictogram).
   * Tik met de muis over een afbeeldingsset op **[!UICONTROL Select]** (vinkpictogram) en tik op **[!UICONTROL Edit]** in de werkbalk.
   * Tik op een afbeeldingsset en tik op **[!UICONTROL Edit]** (potloodpictogram) in de werkbalk.

1. Voer een van de volgende handelingen uit om de afbeeldingen in de Afbeeldingsset te bewerken:

   * Als u elementen opnieuw wilt rangschikken, sleept u een afbeelding naar een nieuwe locatie (selecteer het pictogram voor opnieuw ordenen om items te verplaatsen).
   * Als u items in oplopende of aflopende volgorde wilt sorteren, klikt u op de kolomkop.
   * Als u een element wilt toevoegen of een bestaand element wilt bijwerken, klikt u op **[!UICONTROL Add Asset]**. Navigeer naar een element, selecteer het en tik op **[!UICONTROL Select]** in de rechterbovenhoek van de pagina.

      >[!NOTE]
      >
      >Als u de afbeelding verwijdert die de Experience Manager voor de miniatuur gebruikt door deze te vervangen door een andere afbeelding, wordt het oorspronkelijke element nog steeds weergegeven.
   * Als u een element wilt verwijderen, selecteert u het en tikt u op **[!UICONTROL Delete Asset]** of klikt u op .
   * Tik op **[!UICONTROL Preset]** en selecteer een viewervoorinstelling om een voorinstelling toe te passen in de rechterbovenhoek van de pagina.
   * Als u een miniatuur wilt toevoegen of wijzigen, selecteert u het miniatuurpictogram rechts van het element. Navigeer naar de nieuwe miniatuur of het nieuwe staalelement, selecteer het en tik op **[!UICONTROL Select]**.
   * Als u een volledige afbeeldingsset wilt verwijderen, navigeert u naar de Afbeeldingsset, selecteert u deze en tikt u op **[!UICONTROL Delete]**.

   >[!NOTE]
   >
   >U kunt de afbeeldingen in een Afbeeldingsset bewerken. Navigeer naar de set en tik **[!UICONTROL Set Members]** in de linkertrack. Tik op het potloodpictogram op een element om het bewerkingsvenster te openen.

1. Tik **[!UICONTROL Save]** wanneer u klaar bent met bewerken.

## Voorvertoning van afbeeldingssets {#previewing-image-sets}

Zie [Elementen voorvertonen](/help/assets/dynamic-media/previewing-assets.md).

## Afbeeldingssets {#publishing-image-sets} publiceren

Zie [Elementen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).
