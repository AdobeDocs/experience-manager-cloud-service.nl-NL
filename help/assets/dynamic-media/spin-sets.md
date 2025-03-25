---
title: Sets draaien
description: Leer hoe u met centrifuges werkt in Dynamic Media.
contentOwner: Rick Brough
feature: Spin Sets
role: User
exl-id: ed470472-62d9-4684-971b-30df3919c180
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '1892'
ht-degree: 7%

---

# Sets draaien{#spin-sets}

Een centrifugeerset simuleert de echte handeling waarbij een object wordt omgedraaid om het te onderzoeken. Met centrifuges kunt u items vanuit elke hoek bekijken en de belangrijkste visuele details vanuit elke hoek ophalen.

Een centrifugeerset simuleert een kijkervaring van 360°. Dynamische media biedt centrifugesets met één as waarin gebruikers een item kunnen roteren. Bovendien kunnen gebruikers met een paar eenvoudige muisklikken in- en uitzoomen op een vrije vorm en een willekeurige weergave pannen. Op deze manier kunnen gebruikers een item vanuit een bepaald gezichtspunt nader onderzoeken.

De Reeksen van de draaien worden aangewezen door een banner met het woord **[!UICONTROL SPINSET]**. Als de Spin-set is gepubliceerd, staat bovendien de publicatiedatum (aangegeven door het pictogram **[!UICONTROL World]** ) op de banner samen met de laatste wijzigingsdatum die wordt aangegeven door het pictogram **[!UICONTROL Pencil]** .

![ chlimage_1- ](assets/chlimage_1-380.png)

>[!NOTE]
>
>Voor informatie over het gebruikersinterface van Assets, zie [ Leidend activa met Aanraakinterface ](/help/assets/manage-digital-assets.md) en pas het op een nieuwe omslag toe waar uw beeldreeks activa worden geupload.

Als u een Spin-set maakt, raadt Adobe de volgende aanbevolen procedures aan en past het de volgende limiet toe:

| Type limiet | Beste praktijken | Oplegde limiet |
| --- | --- | --- |
| Maximumaantal rijen/kolommen per 2D-set | 12-18 afbeeldingen per set | 1000 |

Zie ook [ Dynamische beperkingen van Media ](/help/assets/dynamic-media/limitations.md).

## Snel starten: centrifuges {#quick-start-spin-sets}

Ga als volgt te werk om snel aan de slag te gaan met centrifuges:

1. Optioneel. [ creeer een partijreeks vooraf ingesteld ](/help/assets/dynamic-media/batch-set-presets-dm.md) en pas het op een nieuwe activaomslag toe.

   Met een voorinstelling voor een batch-set kunt u het maken van de centrifugeset automatiseren.

   >[!IMPORTANT]
   >
   >De reeksen van de partij worden gecreeerd door IPS (het Systeem van de Productie van het Beeld) als deel van activa opnemen.

1. [ uploadt uw beelden voor veelvoudige meningen ](#uploading-assets-for-spin-sets).

   U hebt minstens 8-12 opnamen van een item nodig voor een eendimensionale centrifugeset en 16-24 voor een tweedimensionale centrifugeset. De opnamen moeten regelmatig worden gemaakt om de indruk te wekken dat het item draait en wordt gespiegeld. Als een eendimensionale centrifugeset bijvoorbeeld 12 opnamen bevat, roteert u het item 30° (360/12) voor elke opname.

   Zie [ Dynamische Media - de Ondersteunde formaten van het roosterbeeld ](/help/assets/file-format-support.md#image-support-dynamic-media) voor een lijst van formaten die door de Reeksen van de Rotatie worden gesteund.

1. [ creeer de Reeksen van de Rotatie ](#creating-spin-sets).

   Als u een centrifugeset wilt maken, selecteert u **[!UICONTROL Create]** > **[!UICONTROL Spin Set]** en geeft u de set een naam, kiest u de elementen en kiest u de volgorde waarin de afbeeldingen worden weergegeven.

   Zie [ Werk met Kiezers ](/help/assets/dynamic-media/working-with-selectors.md).

1. Opstelling [ de Vastgestelde Kijker van de Rotatie stelt ](/help/assets/dynamic-media/managing-viewer-presets.md) vooraf in, zoals nodig.

   Beheerders kunnen viewervoorinstellingen voor spinsets maken of wijzigen. Als u uw spinset wilt weergeven met een viewervoorinstelling, selecteert u de spinset en selecteert u **Viewers** in het vervolgkeuzemenu voor het linkerspoor.

   Zie **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]** voor informatie over het maken of bewerken van voorinstellingen voor viewers.

   Zie [ vooraf instelt van de kijker toevoegen en uitgeven ](/help/assets/dynamic-media/managing-viewer-presets.md).

   U kunt sets die zijn gemaakt met voorinstellingen voor batchsets op drie verschillende manieren weergeven en openen. (De Reeksen die gebruikend batch worden gecreeerd stellen vooraf in, verschijnen *niet* in het gebruikersinterface.)

1. [ reeksen van de Voorproef centreert ](/help/assets/dynamic-media/previewing-assets.md).

   Selecteer de centrifugeset en u kunt er een voorvertoning van weergeven. Roteer de centrifugeset. U kunt verschillende viewers kiezen in het menu **[!UICONTROL Viewers]** , dat beschikbaar is in het keuzemenu voor de linkertrack.

1. [ publiceer de Reeksen van de Rotatie ](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

   Als u een centrifugeerset publiceert, worden de URL- en insluitreeks geactiveerd. Bovendien moet u [ de vooraf ingestelde kijker ](/help/assets/dynamic-media/managing-viewer-presets.md) publiceren.

1. [ Verbinding URLs aan uw Toepassing van het Web ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) of [ bed de Video of Kijker van het Beeld ](/help/assets/dynamic-media/embed-code.md) in.

   Adobe Experience Manager Assets maakt URL-aanroepen voor centrifuges en activeert deze nadat u de centrifuges hebt gepubliceerd. U kunt deze URL&#39;s kopiëren wanneer u elementen voorvertoont. U kunt ze ook insluiten op uw website.

   Selecteer eerst de spinset en selecteer vervolgens **[!UICONTROL Viewers]** in het vervolgkeuzemenu voor het linkerspoor.

   Zie [ Verbinding een Rek die aan een Web-pagina ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) wordt geplaatst en [ bed de Video of Kijker van het Beeld ](/help/assets/dynamic-media/embed-code.md) in.

Indien nodig, kunt u [ uitgeven de Reeksen van de Rotatie ](#editing-spin-sets). Bovendien kunt u [ Vastgestelde eigenschappen van de Spin bekijken en wijzigen ](/help/assets/manage-digital-assets.md#editing-properties).

## Elementen uploaden voor centrifuges {#uploading-assets-for-spin-sets}

U hebt minstens 8-12 opnamen van een item nodig voor een eendimensionale centrifugeset. De opnamen moeten regelmatig worden gemaakt om de indruk te wekken dat het item draait en wordt gespiegeld. Als een eendimensionale centrifugeset bijvoorbeeld 12 opnamen bevat, roteert u het item 30° (360/12) voor elke opname.

Zie [ Dynamische Media - de Ondersteunde formaten van het roosterbeeld ](/help/assets/file-format-support.md#image-support-dynamic-media) voor een lijst van formaten die door de Reeksen van de Rotatie worden gesteund.

U kunt beelden voor de Reeksen van de Rotatie zoals u [ om het even welke andere activa in Experience Manager Assets ](/help/assets/manage-digital-assets.md) uploaden.

### Richtlijnen voor het vastleggen van afbeeldingen voor uw centrifugeset {#guidelines-for-shooting-spin-set-images}

Hieronder vindt u een aantal aanbevolen procedures voor het uitvoeren van gecentreerde afbeeldingen. Over het algemeen geldt dat hoe meer afbeeldingen u in een centrifugeset hebt, hoe beter het effect van het draaien van de afbeelding is. Als u echter veel afbeeldingen in de set opneemt, neemt de laadtijd van de afbeeldingen toe. Experience Manager raadt de volgende richtlijnen aan voor het maken van foto&#39;s voor gebruik in centrifuges:

* Gebruik minimaal 8-12 afbeeldingen in een eendimensionale centrifuge en 16-24 afbeeldingen in een tweedimensionale centrifugeset. U hebt minimaal 8 afbeeldingen nodig om 360 graden te kunnen draaien. Eendimensionale centrifuges komen vaker voor omdat het maken van tweedimensionale centrifuges arbeidsintensief is.
* Gebruik een indeling zonder verlies. TIFF en PNG worden aanbevolen.
* Masker alle afbeeldingen zodat het item op een zuiver witte of andere achtergrond met veel contrast wordt weergegeven. Voeg desgewenst schaduwen toe.
* Zorg ervoor dat de productdetails goed verlicht en in nadruk zijn.
* Neem spin beelden voor modekleding met een mannequin of een model. Vaak wordt de mannequin gemaskeerd (met behulp van een glazen mannequin) of wordt in de afbeelding een gestileerde mannequin/dressform weergegeven. U kunt een op-model spin-reeks tot stand brengen door het aantal hoeken te bepalen. Markeer elke hoek met band op de vloer zodat u het model kunt begeleiden en in de richting van elke opname kunt kijken.

## Spin-sets maken {#creating-spin-sets}

In deze sectie wordt beschreven hoe u centrifuges kunt maken.

>[!NOTE]
>
>U kunt ook automatisch spinsets maken via [voorinstellingen voor batchsets](/help/assets/dynamic-media/config-dm.md). **Belangrijk:** Batchsets worden gecreëerd door IPS (Image Production System) als onderdeel van assetopname.
>
>Zie &quot;Creërend partij vastgestelde vooraf instelt om de Reeksen van het Beeld en de Reeksen van de Draai&quot;in [ Dynamische Media ](/help/assets/dynamic-media/config-dm.md) te produceren.

>[!NOTE]
>
>De volgorde waarin afbeeldingen worden weergegeven in een draaiset. Zorg ervoor dat u ze zo bestelt dat de centrifuge een vloeiende weergave van 360° heeft.

Als u een Spin-set maakt, raadt Adobe de volgende aanbevolen procedures aan en past het de volgende limiet toe:

| Type limiet | Beste praktijken | Oplegde limiet |
| --- | --- | --- |
| Maximumaantal rijen/kolommen per 2D-set | 12-18 afbeeldingen per set | 1000 |

Zie ook [ Dynamische beperkingen van Media ](/help/assets/dynamic-media/limitations.md).

**om de Reeksen van de Rotatie tot stand te brengen:**

1. Navigeer in Assets naar de plaats waar u een centrifugeset wilt maken, selecteer **[!UICONTROL Create]** en selecteer vervolgens **[!UICONTROL Spin Set]** . U kunt de set ook maken vanuit een map die uw elementen bevat.

   ![ 6_5_spinset-createpulldownmenu ](assets/6_5_spinset-createpulldownmenu.png)

1. Voer in het veld **[!UICONTROL Title]** in de Editor voor de centrifugeset een naam in voor de centrifugeset. De naam wordt weergegeven in de banner over de centrifugeset. Voer eventueel een beschrijving in.

   ![ 6_5_spinset-spinseteditortitle ](assets/6_5_spinset-spinseteditortitle.png)

   >[!NOTE]
   >
   >Wanneer u de centrifugeset maakt, kunt u de miniatuur van de centrifugeset wijzigen of Experience Manager toestaan de miniatuur automatisch te selecteren op basis van de elementen in de centrifugeset. Als u een miniatuur wilt selecteren, selecteert u **[!UICONTROL Change thumbnail]** en selecteert u een willekeurige afbeelding (u kunt ook naar andere mappen navigeren om afbeeldingen te zoeken). Selecteer **[!UICONTROL Switch to Automatic thumbnail]** als u een miniatuur hebt geselecteerd en vervolgens wilt bepalen dat Experience Manager een miniatuur moet genereren op basis van de centrifugeset.

1. Voer een van de volgende handelingen uit:

   * Selecteer **[!UICONTROL Add Asset]** in de linkerbovenhoek van de pagina van de Editor voor de centrifugeset.

   * Selecteer **[!UICONTROL Select to open Asset Selector]** in het midden van de pagina van de Editor voor de centrifugeset.

   Selecteer elementen die u in de centrifugeset wilt opnemen. Geselecteerde assets hebben een vinkje. Wanneer u klaar bent, selecteert u **[!UICONTROL Select]** in de rechterbovenhoek van de pagina.

   Met de assetkiezer kunt u naar assets zoeken door een trefwoord te typen en op **[!UICONTROL Return]** te tikken. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en selecteer vervolgens het pictogram **[!UICONTROL Filter]** op de werkbalk. Wijzig de weergave door te tikken op het pictogram Weergave en **[!UICONTROL Column View]**, **[!UICONTROL Card View]** of **[!UICONTROL List View]** te selecteren.

   Zie [ Werk met Kiezers ](/help/assets/dynamic-media/working-with-selectors.md).

   ![ chlimage_1-383 ](assets/chlimage_1-383.png)

1. Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. Nadat u elementen hebt toegevoegd, kunt u deze handmatig opnieuw rangschikken of sorteren.

   Sleep indien nodig het pictogram Opnieuw ordenen van een element naar de rechterkant van de bestandsnaam van het element om de volgorde van de afbeeldingen in de lijst met sets te wijzigen.

   ![ herordeer Kader 11 in de spin die door het aan een nieuwe plaats ](assets/6_5_spinset-reorderassets.png) te slepen wordt geplaatst

   De volgorde van frame 11 in de centrifugeerset wijzigen door deze naar een nieuwe locatie te slepen.

1. (Optioneel) Voer een van de volgende handelingen uit:

   * Als u een afbeelding wilt verwijderen, selecteert u de afbeelding en selecteert u **[!UICONTROL Delete Asset]** .

   * Als u een voorinstelling wilt toepassen, selecteert u **[!UICONTROL Preset]** in de rechterbovenhoek van de pagina en selecteert u vervolgens een voorinstelling die u op alle elementen tegelijk wilt toepassen.

1. Selecteer **[!UICONTROL Save]**. De door u gemaakte centrifugeset wordt weergegeven in de map waarin u deze hebt gemaakt.

## Spin-sets weergeven {#viewing-spin-sets}

U kunt spin reeksen of in het gebruikersinterface of het gebruiken van [ partij tot stand brengen vooraf instelt ](/help/assets/dynamic-media/config-dm.md). Nochtans, verschijnen de reeksen die gebruikend partij worden gecreeerd vooraf instelt, *niet* in het gebruikersinterface. U hebt op drie verschillende manieren toegang tot sets die zijn gemaakt met voorinstellingen voor batchsets. (Deze methoden zijn ook beschikbaar als u de centrifuges in de gebruikersinterface hebt gemaakt.)

>[!NOTE]
>
>U kunt reeksen als gebruikersinterface ook bekijken zoals die in [ worden beschreven geeft de Reeksen van de Rotatie ](#editing-spin-sets) uit.

**om de Reeksen van de Rotatie te bekijken:**

1. Bij het openen van de eigenschappen van een afzonderlijk element. Eigenschappen geven aan welke sets het geselecteerde element lid zijn van (onder **[!UICONTROL Member of Sets]**). Selecteer de naam van de set als u de volledige set wilt zien.

   ![ chlimage_1-156 ](assets/chlimage_1-384.png)

1. Van een lidafbeelding van om het even welke set. Selecteer het menu **[!UICONTROL Sets]** om de sets weer te geven waarvan het element lid is.

   ![ chlimage_1-157 ](assets/chlimage_1-385.png)

1. Vanuit de zoekopdracht kunt u **[!UICONTROL Filters]** selecteren, **[!UICONTROL Dynamic Media]** uitvouwen en **[!UICONTROL Sets]** selecteren.

   De zoekopdracht retourneert overeenkomende sets die handmatig in de gebruikersinterface zijn gemaakt of die automatisch zijn gemaakt met voorinstellingen voor batchsets. Voor automatische sets wordt de zoekquery uitgevoerd met behulp van `Starts with` zoekcriteria die verschillen van Experience Manager-zoekopdrachten die zijn gebaseerd op het gebruik van `Contains` -zoekcriteria. Het instellen van het filter op **[!UICONTROL Sets]** is de enige manier om geautomatiseerde sets te doorzoeken.

   ![ chlimage_1-158 ](assets/chlimage_1-386.png)

## Dradensets bewerken {#editing-spin-sets}

U kunt verschillende bewerkingstaken uitvoeren op centrifuges, zoals:

* Voeg afbeeldingen toe aan de centrifugeset.
* Wijzig de volgorde van de afbeeldingen in de centrifugeset.
* Elementen in de centrifugeset verwijderen.
* Voorinstellingen voor viewers toepassen.
* Verwijder de centrifugeset.

**om de Reeksen van de Rotatie uit te geven:**

1. Voer een van de volgende handelingen uit:

   * Houd de muisaanwijzer boven een gecentreerd element en selecteer vervolgens **[!UICONTROL Edit]** (potloodpictogram).
   * Houd de muisaanwijzer boven een gecentreerd element, selecteer **[!UICONTROL Select]** (vinkpictogram) en selecteer vervolgens **[!UICONTROL Edit]** op de werkbalk.

   * Selecteer een set met centrifuges en selecteer vervolgens **[!UICONTROL Edit]** (potloodpictogram) op de werkbalk.

1. Voer een van de volgende handelingen uit om de centrifugeset te bewerken:

   * Als u de volgorde van afbeeldingen wilt wijzigen, sleept u een afbeelding naar een nieuwe locatie (selecteer het pictogram voor herschikken om items te verplaatsen).
   * Als u items in oplopende of aflopende volgorde wilt sorteren, selecteert u de kolomkop.
   * Selecteer **[!UICONTROL Add Asset]** als u een element wilt toevoegen of een bestaand element wilt bijwerken. Navigeer naar een element, selecteer het en selecteer vervolgens **[!UICONTROL Select]** in de rechterbovenhoek.
Als u de afbeelding verwijdert die Experience Manager voor de miniatuur gebruikt door deze te vervangen door een andere afbeelding, wordt het oorspronkelijke element nog steeds weergegeven.
   * Als u een element wilt verwijderen, selecteert u het en selecteert u **[!UICONTROL Delete Asset]** .
   * Als u een voorinstelling wilt toepassen, selecteert u het pictogram Voorinstelling en selecteert u een voorinstelling.
   * Als u een volledige centrifugeset wilt verwijderen, navigeert u naar de centrifugeset, selecteert u deze en selecteert u **[!UICONTROL Delete]**
   >[!NOTE]
   >
   >U kunt de afbeeldingen in een centrifugeset bewerken door naar de set te navigeren, **[!UICONTROL Set Members]** in de linkertrack te selecteren en vervolgens het potloodpictogram op een afzonderlijk element te selecteren om het bewerkingsvenster te openen.

1. Selecteer **[!UICONTROL Save]** wanneer u klaar bent met bewerken.

## Voorvertoning van centrifuges {#previewing-spin-sets}

Zie [ activa van de Voorproef ](/help/assets/dynamic-media/previewing-assets.md).

## Rotatiesets publiceren {#publishing-spin-sets}

Zie [ activa ](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) publiceren.
