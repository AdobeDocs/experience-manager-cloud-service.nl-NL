---
title: Gemengde mediasets
description: Leer hoe u met gemengde mediasets werkt in Dynamic Media.
contentOwner: Rick Brough
feature: Mixed Media Sets
role: User
exl-id: 7ccde741-38d2-44c9-9378-f2721384aab7
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 11%

---

# Gemengde mediasets{#mixed-media-sets}

Met gemengde mediasets kunt u afbeeldingen, afbeeldingssets, centrifuges en video&#39;s in één presentatie laten overvloeien.

Gemengde mediasets worden aangegeven door een banner met het woord **[!UICONTROL MixedMediaSet]**. Als de gemengde mediaset wordt gepubliceerd, wordt bovendien de publicatiedatum, die door het pictogram **[!UICONTROL World]** wordt aangegeven, samen met de laatste wijzigingsdatum op de banner weergegeven. Dit wordt aangegeven door het pictogram **[!UICONTROL Pencil]**.

![ chlimage_1-137 ](assets/chlimage_1-348.png)

>[!NOTE]
>
>Voor informatie over het gebruikersinterface van Assets, zie [ activa met Aanraakinterface beheren ](/help/assets/manage-digital-assets.md).

## Snel starten: gemengde mediasets {#quick-start-mixed-media-sets}

Ga als volgt te werk om snel aan de slag te gaan met gemengde mediasets:

1. [ uploadt uw activa ](#uploading-assets).

   Begin door de afbeeldingen en video&#39;s voor uw gemengde mediasets te uploaden. Maak indien nodig uw eigen [afbeeldingsets](/help/assets/dynamic-media/image-sets.md) en [spinsets](/help/assets/dynamic-media/spin-sets.md). Omdat gebruikers kunnen inzoomen op afbeeldingen in de gemengde Media Set Viewer, moet u er rekening mee houden dat u kunt zoomen wanneer u afbeeldingen kiest. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn.

   Zie [ Dynamic Media - de Ondersteunde formaten van het roosterbeeld ](/help/assets/file-format-support.md#image-support-dynamic-media) voor een lijst van formaten die door Gemengde Reeksen van Media worden gesteund.

1. [ creeer Gemengde Reeksen van Media ](#creating-mixed-media-sets).

   Als u een gemengde mediaset wilt maken, gaat u op de Assets-pagina naar **[!UICONTROL Create]** > **[!UICONTROL Mixed Media Set]** en geeft u een naam op voor de set, kiest u de elementen en kiest u de volgorde waarin de afbeeldingen worden weergegeven.

   Zie [ Werk met Kiezers ](/help/assets/dynamic-media/working-with-selectors.md).

1. Opstelling [ Gemengde de Kijker van Media stelt ](/help/assets/dynamic-media/managing-viewer-presets.md) vooraf in, zoals nodig.

   Beheerders kunnen viewervoorinstellingen voor gemengde mediasets maken of wijzigen. Als u de gemengde media met een viewervoorinstelling wilt weergeven, selecteert u de gemengde mediaset en selecteert u **[!UICONTROL Viewers]** in de vervolgkeuzelijst van het linkerspoor.

   Als u viewervoorinstellingen wilt maken of bewerken, navigeert u naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]** .

   Zie [ vooraf instelt van de kijker toevoegen en uitgeven ](/help/assets/dynamic-media/managing-viewer-presets.md).

1. [ Voorproef Gemengde Plaatsen van Media ](#previewing-mixed-media-sets).

   Selecteer de gemengde Mediaset en u kunt er een voorvertoning van weergeven. Als u de gemengde mediaset in de geselecteerde viewer wilt bekijken, selecteert u de miniatuurpictogrammen. U kunt verschillende Viewers kiezen in het **[!UICONTROL Viewers]** -menu, dat beschikbaar is in het linkervervolgkeuzemenu.

1. [ Publish Gemengde Plaatsen van Media ](#publishing-mixed-media-sets).

   Wanneer u een gemengde mediaset publiceert, worden de URL en de insluitreeks geactiveerd. Bovendien moet u [ de vooraf ingestelde kijker ](/help/assets/dynamic-media/managing-viewer-presets.md#publishing-viewer-presets) publiceren.

1. [ Verbinding URLs aan uw Toepassing van het Web ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) of [ bed de Video of Kijker van het Beeld ](/help/assets/dynamic-media/embed-code.md) in.

   Adobe Experience Manager Assets maakt URL-aanroepen voor gemengde mediasets en activeert deze nadat u de gemengde mediasets hebt gepubliceerd. U kunt deze URL&#39;s kopiëren wanneer u elementen voorvertoont. U kunt ze ook insluiten op uw website.

   Selecteer de gemengde Mediaset en selecteer vervolgens **[!UICONTROL Viewers]** in het keuzemenu voor de linkertrack.

   Zie [ Verbinding een Gemengde Media die aan een Web-pagina ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) wordt geplaatst en [ bed de Video of Kijker van het Beeld ](/help/assets/dynamic-media/embed-code.md) in.

Indien noodzakelijk, kunt u [ Gemengde Reeksen van Media ](#editing-mixed-media-sets) uitgeven. Bovendien kunt u [ Gemengde Media bekijken en wijzigen vastgestelde eigenschappen ](/help/assets/manage-digital-assets.md#editing-properties).

>[!NOTE]
>
>Als u kwesties hebt die reeksen creëren, zie [ problemen oplossen Dynamic Media ](/help/assets/dynamic-media/troubleshoot-dm.md).

## Elementen uploaden {#uploading-assets}

Begin door de afbeeldingen en video&#39;s voor uw gemengde mediasets te uploaden. Vergeet niet dat gebruikers op afbeeldingen kunnen inzoomen in de viewer voor gemengde mediaset. Kies daarom afbeeldingen met deze zoomfunctie voor ogen. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn.

Als u bovendien centrifuges of afbeeldingssets wilt toevoegen aan de gemengde mediaset, maakt u deze ook.

Zie [ Dynamic Media - de Ondersteunde formaten van het roosterbeeld ](/help/assets/file-format-support.md#image-support-dynamic-media) voor een lijst van formaten die door Gemengde Reeksen van Media worden gesteund.

## Gemengde mediasets maken {#creating-mixed-media-sets}

U kunt afbeeldingen, afbeeldingssets, centrifuges en video&#39;s toevoegen aan de gemengde mediaset. Zorg ervoor dat de bestanden, afbeeldingssets en centrifuges klaar zijn om te worden gepubliceerd voordat u ze aan de gemengde mediaset toevoegt.

Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. U kunt elementen handmatig opnieuw ordenen of sorteren nadat u ze hebt toegevoegd.

**om Gemengde Reeksen van Media tot stand te brengen:**

1. Navigeer in Assets naar de plaats waar u een gemengde mediaset wilt maken, selecteer **[!UICONTROL Create]** en selecteer **[!UICONTROL Mixed Media Set]** . U kunt de set ook maken vanuit een map die uw assets bevat. De editor voor gemengde mediasets wordt weergegeven.

   ![ chlimage_1-138 ](assets/chlimage_1-349.png)

1. Voer in de Editor gemengde mediaset in **[!UICONTROL Title]** een naam in voor de gemengde mediaset. De naam wordt in de banner weergegeven in de gemengde mediaset. Voer eventueel een beschrijving in.

   ![ chlimage_1-139 ](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Wanneer u de gemengde mediaset maakt, kunt u de miniatuur van de gemengde mediaset wijzigen of Experience Manager toestaan de miniatuur automatisch te selecteren op basis van de elementen in de gemengde mediaset. Als u een miniatuur wilt selecteren, selecteert u **[!UICONTROL Change thumbnail]** en selecteert u een willekeurige afbeelding (u kunt ook naar andere mappen navigeren om afbeeldingen te zoeken). Als u een miniatuur hebt geselecteerd, kiest u **[!UICONTROL Switch to Automatic thumbnail]** en wilt u dat Experience Manager een miniatuur maakt van de gemengde mediaset.

1. Selecteer Elementkiezer om elementen te selecteren die u in de gemengde mediaset wilt opnemen. Selecteer ze en selecteer **[!UICONTROL Select]** .

   Met de Asset Selector kunt u naar elementen zoeken door een trefwoord in te voeren en **[!UICONTROL Return]** te selecteren. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en selecteer vervolgens het pictogram **[!UICONTROL Filter]** op de werkbalk. Wijzig de weergave door het pictogram **[!UICONTROL View]** te selecteren en **[!UICONTROL List View]**, **[!UICONTROL Column View]** of **[!UICONTROL Card View]** te selecteren.

   Zie [ Werkend met Kiezers ](/help/assets/dynamic-media/working-with-selectors.md).

   ![ chlimage_1-140 ](assets/chlimage_1-351.png)

1. Wijzig de volgorde van de elementen door deze omhoog of omlaag te slepen (selecteer het pictogram **[!UICONTROL Reorder]** ).

   ![ chlimage_1-141 ](assets/chlimage_1-352.png)

   Als u miniaturen wilt toevoegen, selecteert u het pictogram **+** **[!UICONTROL thumbnail]** naast de afbeelding en navigeert u naar de gewenste miniatuur. Selecteer **[!UICONTROL Save]** wanneer u klaar bent met het selecteren van alle miniatuurafbeeldingen.

   >[!NOTE]
   >
   >Selecteer **[!UICONTROL Add Asset]** als u elementen wilt toevoegen.

1. Als u een element wilt verwijderen, schakelt u het desbetreffende selectievakje in en selecteert u **[!UICONTROL Delete Asset]** .
1. Als u een voorinstelling wilt toepassen, selecteert u **[!UICONTROL Preset]** in de rechterbovenhoek en selecteert u een voorinstelling die u op de elementen wilt toepassen.
1. Selecteer **[!UICONTROL Save]**. De gemaakte gemengde mediaset wordt weergegeven in de map waarin u deze hebt gemaakt.

## Gemengde mediasets bewerken {#editing-mixed-media-sets}

U kunt diverse het uitgeven taken aan activa in Gemengde Reeksen van Media direct in het gebruikersinterface [ uitvoeren aangezien u om het even welke activa in Assets ](/help/assets/manage-digital-assets.md). U kunt ook de volgende handelingen uitvoeren in Gemengde Mediasets:

* Voeg elementen toe aan de gemengde mediaset.
* Elementen opnieuw rangschikken in de gemengde mediaset.
* Elementen verwijderen uit de gemengde mediaset.
* Voorinstellingen voor viewers toepassen.
* Wijzig de standaardminiatuur.

**om Gemengde Reeksen van Media uit te geven:**

1. Voer een van de volgende handelingen uit:

   * Houd de cursor boven een element in een gemengde mediaset en selecteer vervolgens **[!UICONTROL Edit]** (potloodpictogram).
   * Houd de cursor boven een element in een gemengde mediaset, selecteer **[!UICONTROL Select]** (vinkpictogram) en selecteer vervolgens **[!UICONTROL Edit]** op de werkbalk.

   * Selecteer een gemengde mediaset en selecteer vervolgens **[!UICONTROL Edit]** (potloodpictogram) op de werkbalk.

1. Voer in de Editor gemengde mediaset een van de volgende handelingen uit:

   * Als u elementen opnieuw wilt rangschikken, selecteert u **[!UICONTROL Assets]** (afbeeldingspictogram) in het linkerdeelvenster en sleept u een element naar een nieuwe locatie.
   * Als u elementen wilt toevoegen, selecteert u **[!UICONTROL Add Asset]** op de werkbalk. Navigeer naar de elementen. Voor elk element dat u wilt toevoegen, beweegt u de muisaanwijzer over de afbeelding van het element (niet over de naam van het element) en selecteert u het pictogram van het vinkje. Selecteer **[!UICONTROL Select]** in de rechterbovenhoek.

   * Als u een element wilt verwijderen, selecteert u **[!UICONTROL Assets]** (afbeeldingspictogram) in het linkerdeelvenster en selecteert u vervolgens het element. Selecteer **[!UICONTROL Delete Asset]** op de werkbalkbalk.

   * Selecteer **[!UICONTROL Assets]** (afbeeldingspictogram) in het linkerdeelvenster als u elementen op naam in oplopende of aflopende volgorde wilt sorteren. Rechts van de kop **[!UICONTROL Assets]** selecteert u de pictogrammen voor de pijl-omhoog of -omlaag.

     >[!NOTE]
     >
     >* Als u een volledige gemengde mediaset wilt verwijderen, navigeert u vanuit elke weergavemodus (zoals **[!UICONTROL Card View]** of **[!UICONTROL Column View]** ) naar de gemengde mediaset. Houd de muisaanwijzer boven het element en selecteer het vinkje zodat u het kunt selecteren. Druk op **[!UICONTROL Backspace]** op het toetsenbord of selecteer **[!UICONTROL More]** (drie punten) op de werkbalk en selecteer vervolgens **[!UICONTROL Delete]** .
     >
     >* U kunt de elementen in een gemengde mediaset bewerken door naar de set te navigeren. Selecteer **[!UICONTROL Set Members]** in het linkerspoor en selecteer vervolgens het pictogram **[!UICONTROL Pencil]** op een afzonderlijk element om het bewerkingsvenster te openen.

1. Selecteer **[!UICONTROL Save]** wanneer u klaar bent met bewerken.

   >[!NOTE]
   >
   >* Als u de elementen in een gemengde mediaset wilt bewerken, navigeert u naar de gemengde mediaset. Selecteer de set (niet selecteren), zodat u deze kunt openen op de pagina Voorvertoning Experience Manager instellen. Selecteer in de linkertrack het inlasteken omlaag om de vervolgkeuzelijst te openen en selecteer vervolgens **[!UICONTROL Set Members]** . Houd de muisaanwijzer op een element op de pagina Leden instellen en selecteer **[!UICONTROL Edit]** (potloodpictogram) om de bewerkingspagina te openen.
   >
   >* Als u een volledige gemengde mediaset wilt verwijderen, gaat u vanuit elke weergavemodus (zoals de Kaart- of kolomweergave) naar de gemengde mediaset. Houd de muisaanwijzer boven de set en selecteer vervolgens **[!UICONTROL Select]** (vinkje). Druk op **[!UICONTROL Backspace]** op het toetsenbord of selecteer **[!UICONTROL More]** (rij van drie stippen) en selecteer vervolgens **[!UICONTROL Delete]** .

## Voorvertoning van gemengde mediasets {#previewing-mixed-media-sets}

Zie [ activa van de Voorproef ](/help/assets/dynamic-media/previewing-assets.md) voor details op hoe te voorproef Gemengde Reeksen van Media.

## Gemengde Publish-mediasets {#publishing-mixed-media-sets}

Zie {de activa van 0} Publish ](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) voor details op hoe te om Gemengde Reeksen van Media te publiceren.[

>[!NOTE]
>
>Als de gemengde mediaset de eerste keer dat u deze publiceert niet volledig in de leveringsservice terechtkomt, publiceert u de gemengde mediaset een tweede keer.
