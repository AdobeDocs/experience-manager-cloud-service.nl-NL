---
title: Mixed Media Sets
description: Leer hoe u met gemengde mediasets werkt in Dynamic Media
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 27%

---


# Mixed Media Sets{#mixed-media-sets}

Met gemengde mediasets kunt u in één presentatie een combinatie van afbeeldingen, afbeeldingssets, centrifuges en video&#39;s aanbieden.

Gemengde mediasets worden aangegeven door een banner met het woord **[!UICONTROL MixedMediaSet]**. Als de gemengde mediaset wordt gepubliceerd, wordt bovendien de publicatiedatum, die door het pictogram **[!UICONTROL World]** wordt aangegeven, samen met de laatste wijzigingsdatum op de banner weergegeven. Dit wordt aangegeven door het pictogram **[!UICONTROL Pencil]**.

![chlimage_1-137](assets/chlimage_1-348.png)

>[!NOTE]
>
>Zie Elementen [beheren met de aanraakinterface](/help/assets/manage-digital-assets.md)voor informatie over de gebruikersinterface van Elementen.

## Snel starten: Gemengde mediasets {#quick-start-mixed-media-sets}

Ga als volgt te werk om snel aan de slag te gaan met gemengde mediasets:

1. [Upload uw elementen](#uploading-assets).

   Begin door de afbeeldingen en video&#39;s voor uw gemengde mediasets te uploaden. Maak indien nodig uw eigen [afbeeldingsets](/help/assets/dynamic-media/image-sets.md) en [spinsets](/help/assets/dynamic-media/spin-sets.md). Omdat gebruikers kunnen inzoomen op afbeeldingen in de viewer voor gemengde mediasets, moet u rekening houden met zoomen wanneer u afbeeldingen kiest. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn in de grootste dimensie.

1. [Gemengde mediasets maken.](#creating-mixed-media-sets)

   Als u een gemengde mediaset wilt maken, tikt u op de pagina Assets op **[!UICONTROL Create > Mixed Media Set]** en geeft u de set een naam, kiest u de assets en kiest u de volgorde waarin de afbeeldingen worden weergegeven.

   See [Working with Selectors.](/help/assets/dynamic-media/working-with-selectors.md)

1. Stel indien nodig [gemengde voorinstellingen](/help/assets/dynamic-media/managing-viewer-presets.md)voor de Media Viewer in.

   Beheerders kunnen viewervoorinstellingen voor gemengde mediasets maken of wijzigen. Als u de gemengde media met een viewervoorinstelling wilt weergeven, selecteert u de gemengde mediaset en selecteert u **[!UICONTROL Viewers]** in de vervolgkeuzelijst van het linkerspoor.

   Zie **[!UICONTROL Tools > Assets > Viewer Presets]** viewervoorinstellingen maken of bewerken.

   Zie Voorinstellingen voor viewers [toevoegen en bewerken.](/help/assets/dynamic-media/managing-viewer-presets.md)

1. [Voorvertoning gemengde mediasets.](#previewing-mixed-media-sets)

   Selecteer de gemengde Mediaset en u kunt er een voorvertoning van weergeven. Klik op de miniatuurpictogrammen om de gemengde mediaset in de geselecteerde viewer te bekijken. U kunt verschillende Viewers van het **[!UICONTROL Viewers]** menu kiezen, beschikbaar van het linkerspoordrop-down menu.

1. [Gemengde mediasets publiceren.](#publishing-mixed-media-sets)

   Wanneer u een gemengde mediaset publiceert, worden de URL en de insluitreeks geactiveerd. Bovendien moet u de voorinstelling [van de viewer](/help/assets/dynamic-media/managing-viewer-presets.md#publishing-viewer-presets)publiceren.

1. [Koppel URL&#39;s aan uw webtoepassing](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) of [sluit de video- of afbeeldingsviewer](/help/assets/dynamic-media/embed-code.md)in.

   Met AEM-elementen worden URL-aanroepen voor gemengde mediasets gemaakt en geactiveerd nadat u de gemengde mediasets hebt gepubliceerd. U kunt deze URL&#39;s kopiëren wanneer u elementen voorvertoont. U kunt ze ook insluiten op uw website.

   Select the Mixed Media Set, then in the left rail drop-down menu, select **[!UICONTROL Viewers]**.

   Zie [Een gemengde mediaset koppelen aan een webpagina](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) en [De video- of afbeeldingsviewer insluiten](/help/assets/dynamic-media/embed-code.md).

Indien nodig kunt u [gemengde mediasets](#editing-mixed-media-sets)bewerken. Daarnaast kunt u de eigenschappen [van](/help/assets/manage-digital-assets.md#editing-properties)gemengde mediaset weergeven en wijzigen.

>[!NOTE]
>
>Als u problemen hebt met het maken van sets, raadpleegt u [Problemen met dynamische media](/help/assets/dynamic-media/troubleshoot-dm.md)oplossen.

## Elementen uploaden {#uploading-assets}

Begin door de afbeeldingen en video&#39;s voor uw gemengde mediasets te uploaden. Omdat gebruikers kunnen inzoomen op afbeeldingen in de gemengde Media Set Viewer, dient u rekening te houden met zoomen wanneer u afbeeldingen kiest. Zorg ervoor dat de afbeeldingen ten minste 2000 pixels groot zijn in de grootste dimensie.

Als u bovendien centrifuges of afbeeldingssets wilt toevoegen aan de gemengde mediaset, maakt u deze ook.

## Gemengde mediasets maken {#creating-mixed-media-sets}

U kunt afbeeldingen, afbeeldingssets, centrifuges en video&#39;s toevoegen aan de gemengde mediaset. Zorg ervoor dat de bestanden, afbeeldingssets en centrifuges klaar zijn om te worden gepubliceerd voordat u ze aan de gemengde mediaset toevoegt.

Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. U kunt elementen handmatig opnieuw ordenen of sorteren nadat u ze hebt toegevoegd.

**Een gemengde mediaset maken**

1. Ga in Assets naar de plaats waar u een gemengde mediaset wilt maken, klik op **[!UICONTROL Create]** en selecteer **[!UICONTROL Mixed Media Set]**. U kunt de set ook maken vanuit een map die uw assets bevat. De editor voor gemengde mediasets wordt weergegeven.

   ![chlimage_1-138](assets/chlimage_1-349.png)

1. Voer in de Editor gemengde mediaset een naam in voor de gemengde mediaset. **[!UICONTROL Title]** De naam wordt in de banner weergegeven in de gemengde mediaset. Voer eventueel een beschrijving in.

   ![chlimage_1-139](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Wanneer u de gemengde mediaset maakt, kunt u de miniatuur van de gemengde mediaset wijzigen of AEM toestaan de miniatuur automatisch te selecteren op basis van de elementen in de gemengde mediaset. Als u een miniatuur wilt selecteren, klikt u op een willekeurige afbeelding **[!UICONTROL Change thumbnail]** en selecteert u deze (u kunt ook naar andere mappen navigeren om afbeeldingen te zoeken). If you have selected a thumbnail and then decide that you want AEM to generate one from the mixed media set, select **[!UICONTROL Switch to Automatic thumbnail]**.

1. Tik op de Asset Selector om de elementen te selecteren die u in de gemengde mediaset wilt opnemen. Select them and click **[!UICONTROL Select]**.

   Met de assetkiezer kunt u naar assets zoeken door een trefwoord te typen en op **[!UICONTROL Return]** te tikken. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en tik op het pictogram **[!UICONTROL Filter]** op de werkbalk. Wijzig de weergave door het pictogram **[!UICONTROL View]** te selecteren en **[!UICONTROL List View]**, **[!UICONTROL Column View]** of **[!UICONTROL Card View]** te selecteren.

   See [Working with Selectors](/help/assets/dynamic-media/working-with-selectors.md).

   ![chlimage_1-140](assets/chlimage_1-351.png)

1. Wijzig de volgorde van de elementen door deze omhoog of omlaag te slepen (selecteer het **[!UICONTROL Reorder]** pictogram).

   ![chlimage_1-141](assets/chlimage_1-352.png)

   Als u miniaturen wilt toevoegen, klikt u op het pictogram **+** **[!UICONTROL thumbnail]** naast de afbeelding en gaat u naar de gewenste miniatuur. Klik wanneer u alle miniatuurafbeeldingen hebt geselecteerd op **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Tik op **[!UICONTROL Add Asset]** als u elementen wilt toevoegen.

1. Als u een element wilt verwijderen, schakelt u het desbetreffende selectievakje in en tikt u op **[!UICONTROL Delete Asset]**.
1. Tik in de rechterbovenhoek op een voorinstelling om deze toe te passen. Selecteer vervolgens de voorinstelling die u op de elementen wilt toepassen. **[!UICONTROL Preset]**
1. Klik op **[!UICONTROL Save]**. De nieuwe gemengde mediaset wordt weergegeven in de map waarin u deze hebt gemaakt.

## Gemengde mediasets bewerken {#editing-mixed-media-sets}

U kunt diverse bewerkingstaken rechtstreeks in de gebruikersinterface uitvoeren op elementen in gemengde mediasets, [net als op elementen](/help/assets/manage-digital-assets.md). U kunt ook de volgende handelingen uitvoeren in Gemengde Mediasets:

* Voeg elementen toe aan de gemengde mediaset.
* Wijzig de volgorde van elementen in de gemengde mediaset.
* Elementen verwijderen uit de gemengde mediaset.
* Voorinstellingen voor viewers toepassen.
* Wijzig de standaardminiatuur.

**Een gemengde mediaset bewerken**

1. Voer een van de volgende handelingen uit:

   * Houd de muisaanwijzer boven een element uit een gemengde mediaset en tik op **[!UICONTROL Edit]** (potloodpictogram).
   * Houd de muisaanwijzer boven een element uit een gemengde mediaset, tik op **[!UICONTROL Select]** (vinkpictogram) en tik vervolgens op **[!UICONTROL Edit]** de werkbalk.

   * Tik op een element uit een gemengde mediaset en tik vervolgens op **[!UICONTROL Edit]** (potloodpictogram) op de werkbalk.

1. Voer in de Editor gemengde mediaset een van de volgende handelingen uit:

   * Tik in het linkerdeelvenster op **[!UICONTROL Assets]** (afbeeldingspictogram) en sleep een element naar een nieuwe locatie om de volgorde van de elementen te wijzigen.
   * Tik op **[!UICONTROL Add Asset]** de werkbalk om elementen toe te voegen. Navigeer naar de elementen. Tik op het pictogram van het vinkje voor elk element dat u wilt toevoegen. Houd de muisaanwijzer boven de afbeelding van het element (niet de naam van het element). Tik in de rechterbovenhoek op **[!UICONTROL Select]**.

   * Tik op **[!UICONTROL Assets]** (afbeeldingspictogram) en selecteer het element om een element te verwijderen. Tik op de werkbalk **[!UICONTROL Delete Asset]**.

   * Tik in het linkerdeelvenster op **[!UICONTROL Assets]** (afbeeldingspictogram) om elementen op naam in oplopende of aflopende volgorde te sorteren. Tik rechts van de **[!UICONTROL Assets]** kop op of omlaag de invoegpictogrammen.

      >[!NOTE]
      >
      >    * To delete an entire Mixed Media Set, from any viewing mode (such as **[!UICONTROL Card View]** or **[!UICONTROL Column View]**) navigate to the Mixed Media Set. Wijs de asset aan en tik op het vinkje om deze te selecteren. Druk op **[!UICONTROL Backspace]** het toetsenbord of klik op **[!UICONTROL More]** (drie punten) op de werkbalk en tik vervolgens op **[!UICONTROL Delete]**.
         >
         >    
      * You can edit the assets in a Mixed Media Set by navigating to the set, clicking **Set Members]** in the left rail, and then tapping the **[!UICONTROL Pencil]** icon on an individual asset to open the editing window.


1. Tik **[!UICONTROL Save]** wanneer u klaar bent met bewerken.

   >[!NOTE]
   >
   >* Als u de assets in een gemengde mediaset wilt bewerken, gaat u naar de gemengde mediaset. Tik (niet selecteren) op de set om deze te openen op de pagina Voorvertoning van AEM-set. In the left rail, click the down caret to open the drop-down list, then tap **[!UICONTROL Set Members]**. In the Set Members page, hover on an asset, then tap **[!UICONTROL Edit]** (pencil icon) to open the editing page.
      >
      >
   * Als u een volledige gemengde mediaset wilt verwijderen, gaat u vanuit een willekeurige weergavemodus (zoals kaart- of kolomweergave) naar de gemengde mediaset. Hover on the set, then tap **Select]** (checkmark icon). Druk op **[!UICONTROL Backspace]** het toetsenbord of tik op **[!UICONTROL More]** (rij met drie punten) en tik vervolgens op **[!UICONTROL Delete]**.


## Voorvertoning van gemengde mediasets {#previewing-mixed-media-sets}

Zie Elementen [](/help/assets/dynamic-media/previewing-assets.md) voorvertonen voor meer informatie over het voorvertonen van gemengde mediasets.

## Gemengde mediasets publiceren {#publishing-mixed-media-sets}

Zie Elementen [](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) publiceren voor meer informatie over het publiceren van gemengde mediasets.

>[!NOTE]
>
>Als de gemengde mediaset de eerste keer dat u deze publiceert niet volledig in de leveringsservice terechtkomt, moet u de gemengde mediaset mogelijk nog een keer publiceren.

