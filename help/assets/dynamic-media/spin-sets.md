---
title: Sets draaien
description: Leer hoe u met centrifuges werkt in Dynamic Media
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Sets draaien{#spin-sets}

Een centrifugeerset simuleert de echte handeling waarbij een object wordt omgedraaid om het te onderzoeken. Met centrifuges kunt u items vanuit elke hoek bekijken en de belangrijkste visuele details vanuit elke hoek verkrijgen.

Een centrifugeerset simuleert een kijkervaring van 360 graden. Dynamische media biedt centrifugesets met één as waarin gebruikers een item kunnen roteren. Bovendien kunnen gebruikers met een paar eenvoudige muisklikken in- en uitzoomen op een vrije vorm en een willekeurige weergave pannen. Op deze manier kunnen gebruikers een item vanuit een bepaald gezichtspunt nader onderzoeken.

De Reeksen van de draaien worden aangewezen door een banner met het woord **[!UICONTROL SPINSET]**. Als de Spin-set wordt gepubliceerd, staat bovendien de publicatiedatum, die wordt aangegeven door het pictogram **[!UICONTROL Wereld]** , op de banner samen met de laatste wijzigingsdatum, die wordt aangegeven door het pictogram **[!UICONTROL Potlood]** .

![chlimage_1-](assets/chlimage_1-380.png)

>[!NOTE]
>
>Zie Elementen [beheren met de aanraakinterface](/help/assets/manage-digital-assets.md)voor informatie over de gebruikersinterface van Elementen.

## Snel starten: Sets draaien {#quick-start-spin-sets}

Ga als volgt te werk om snel aan de slag te gaan met centrifuges:

1. [Upload uw afbeeldingen voor meerdere weergaven.](#uploading-assets-for-spin-sets)

   U hebt minstens 8-12 opnamen van een item nodig voor een eendimensionale centrifugeset en 16-24 voor een tweedimensionale centrifugeset. De opnamen moeten regelmatig worden gemaakt om de indruk te wekken dat het item draait en wordt gespiegeld. Als een eendimensionale centrifugeset bijvoorbeeld 12 opnamen bevat, roteert u het item 30 graden (360/12) voor elke opname.

1. [Spin-sets maken.](#creating-spin-sets)

   Als u een centrifugeset wilt maken, selecteert u **[!UICONTROL Maken > Spin-set]** en geeft u de set een naam, kiest u de elementen en kiest u de volgorde waarin de afbeeldingen worden weergegeven.

   Zie [Werken met kiezers](/help/assets/dynamic-media/working-with-selectors.md).

   >[!NOTE]
   >
   >U kunt ook automatisch spin-sets maken via voorinstellingen voor [batchsets](/help/assets/dynamic-media/config-dm.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets). **** Belangrijk:De reeksen van de partij worden gecreeerd door IPS (het Systeem van de Productie van het Beeld) als deel van activa opnemen.

1. Stel, indien nodig, [voorinstellingen](/help/assets/dynamic-media/managing-viewer-presets.md)voor de draaiende viewer in.

   Beheerders kunnen voorinstellingen voor de voorinstelling van een draaiset-viewer maken of wijzigen. Als u de centrifugeset wilt weergeven met een viewervoorinstelling, selecteert u de centrifugeset en selecteert u **Viewers** in de vervolgkeuzelijst voor de linkertrack.

   Zie **[!UICONTROL Gereedschappen > Middelen > Voorinstellingen]** viewer om voorinstellingen voor viewers te maken of te bewerken.

   Zie Voorinstellingen voor viewers [toevoegen en bewerken.](/help/assets/dynamic-media/managing-viewer-presets.md)

   U kunt sets die zijn gemaakt met voorinstellingen voor batchsets op drie verschillende manieren weergeven en openen. (Sets die zijn gemaakt met behulp van voorinstellingen voor batchsets, worden *niet* weergegeven in de gebruikersinterface.)

1. [Voorvertoning van centrifuges.](/help/assets/dynamic-media/previewing-assets.md)

   Selecteer de centrifugeset en u kunt er een voorvertoning van weergeven. Roteer de centrifugeset. U kunt verschillende viewers kiezen in het menu **[!UICONTROL Viewers]** , beschikbaar in het keuzemenu voor de linkertrack.

1. [Spin-sets publiceren.](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)

   Als u een centrifugeerset publiceert, worden de URL- en insluitreeks geactiveerd. Bovendien moet u de voorinstelling [van de viewer](/help/assets/dynamic-media/managing-viewer-presets.md)publiceren.

1. [Koppel URL&#39;s aan uw webtoepassing](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) of [sluit de video- of afbeeldingsviewer](/help/assets/dynamic-media/embed-code.md)in.

   AEM Assets leidt tot URL vraag naar de Reeksen van de Rotatie en activeert hen nadat u de spin reeksen publiceert. U kunt deze URL&#39;s kopiëren wanneer u elementen voorvertoont. U kunt ze ook insluiten op uw website.

   Selecteer eerst de centrifugeset en vervolgens **[!UICONTROL Viewers]** in het vervolgkeuzemenu voor de linkertrack.

   Zie Een centrifugeerset [koppelen aan een webpagina](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) en de video- of afbeeldingsviewer [](/help/assets/dynamic-media/embed-code.md)insluiten.

Indien nodig kunt u [centrifuges](#editing-spin-sets)bewerken. Bovendien kunt u de eigenschappen [van de](/help/assets/manage-digital-assets.md#editing-properties)Spin-set weergeven en wijzigen.

## Elementen uploaden voor centrifuges {#uploading-assets-for-spin-sets}

U hebt minstens 8-12 opnamen van een item nodig voor een eendimensionale centrifugeset en 16-24 voor een tweedimensionale centrifugeset. De opnamen moeten regelmatig worden gemaakt om de indruk te wekken dat het item draait en wordt gespiegeld. Als een eendimensionale centrifugeset bijvoorbeeld 12 opnamen bevat, roteert u het item 30 graden (360/12) voor elke opname.

U kunt afbeeldingen voor de centrifuges uploaden zoals u elk ander element in AEM-elementen [](/help/assets/manage-digital-assets.md)uploadt.

### Richtlijnen voor het vastleggen van afbeeldingen voor uw centrifugeset {#guidelines-for-shooting-spin-set-images}

Hieronder vindt u een aantal aanbevolen procedures voor het uitvoeren van gecentreerde afbeeldingen. Over het algemeen geldt dat hoe meer afbeeldingen u in een centrifugeset hebt, hoe beter het effect van het draaien van de afbeelding is. Als u echter veel afbeeldingen in de set opneemt, neemt de laadtijd van de afbeeldingen toe. AEM raadt de volgende richtlijnen aan voor het maken van foto&#39;s voor gebruik in centrifuges:

* Gebruik minimaal 8-12 afbeeldingen in een eendimensionale centrifuge en 16-24 afbeeldingen in een tweedimensionale centrifugeset. U hebt minimaal 8 afbeeldingen nodig om 360 graden te kunnen draaien. Eendimensionale centrifuges komen vaker voor omdat het maken van tweedimensionale centrifuges arbeidsintensief is.
* Gebruik een indeling zonder verlies. TIFF en PNG worden aanbevolen.
* Masker alle afbeeldingen zodat het item op een zuiver witte of andere achtergrond met veel contrast wordt weergegeven. Voeg desgewenst schaduwen toe.
* Zorg ervoor dat de productdetails goed verlicht en in nadruk zijn.
* Neem spin beelden voor modekleding met een mannequin of een model. Vaak wordt de mannequin volledig gemaskeerd (met behulp van een glazen mannequin) of wordt in de afbeelding een gestileerde mannequin/dressform weergegeven. U kunt een op-model spin-reeks tot stand brengen door het aantal hoeken te bepalen. Markeer elke hoek met band op de vloer om het model te begeleiden en in de richting van elke opname te kijken.

## Spin-sets maken {#creating-spin-sets}

In deze sectie wordt beschreven hoe u centrifuges kunt maken.

>[!NOTE]
>
>U kunt ook automatisch spin-sets maken via voorinstellingen voor [batchsets](/help/assets/dynamic-media/config-dm.md). **** Belangrijk:De reeksen van de partij worden gecreeerd door IPS (het Systeem van de Productie van het Beeld) als deel van activa opnemen.
>
>Zie &quot;Voorinstellingen voor batchsets maken om automatisch afbeeldingssets en centrifuges te genereren&quot; in Dynamische media [](/help/assets/dynamic-media/config-dm.md)configureren.

>[!NOTE]
>
>De volgorde waarin afbeeldingen worden weergegeven in een draaiset. Zorg ervoor dat u ze zo bestelt dat de centrifuge een vloeiende weergave van 360 graden biedt.

**Draaisets maken**

1. Navigeer in Elementen naar de plaats waar u een centrifugeset wilt maken, klik op **[!UICONTROL Maken]** en selecteer **[!UICONTROL Spin-set]**. U kunt de set ook maken vanuit een map die uw elementen bevat. De Editor voor de centrifugeset wordt weergegeven.

   ![6_5_spinset-createpulldownmenu](assets/6_5_spinset-createpulldownmenu.png)

1. Voer in het veld **[!UICONTROL Titel]** in de Editor van de centrifugeset een naam in voor de centrifugeset. De naam wordt weergegeven in de banner over de centrifugeset. Voer eventueel een beschrijving in.

   ![6_5_spinset-spinseteditortitle](assets/6_5_spinset-spinseteditortitle.png)

   >[!NOTE]
   >
   >Wanneer u de centrifugeset maakt, kunt u de miniatuur van de centrifugeset wijzigen of AEM toestaan de miniatuur automatisch te selecteren op basis van de elementen in de centrifugeset. Als u een miniatuur wilt selecteren, klikt u op de miniatuur **** Wijzigen en selecteert u een willekeurige afbeelding (u kunt ook naar andere mappen navigeren om afbeeldingen te zoeken). Als u een miniatuur hebt geselecteerd en vervolgens besluit dat u een miniatuur van de centrifugeset wilt genereren, selecteert u **[!UICONTROL Schakelen naar automatische miniatuur]**.

1. Voer een van de volgende handelingen uit:

   * Tik in de linkerbovenhoek van de pagina van de Editor voor de centrifugeset op Element **[!UICONTROL toevoegen]**.

   * Tik in het midden van de pagina van de Editor voor de centrifugeset op **[!UICONTROL Tikken om de Asset Selector]** te openen.
   Tik om de elementen te selecteren die u in de centrifugeset wilt opnemen. Geselecteerde elementen hebben een vinkje erboven. Tik op **[!UICONTROL Selecteren]** in de rechterbovenhoek van de pagina als u klaar bent.

   Met de Kiezer van Activa, kunt u naar activa zoeken door in een sleutelwoord te typen en **[!UICONTROL Terugkeer** te tikken. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en tik op het pictogram **[!UICONTROL Filter]** op de werkbalk. Wijzig de weergave door op het pictogram Weergave te tikken en **[!UICONTROL Kolomweergave]**, **[!UICONTROL Kaartweergave]** of **[!UICONTROL Lijstweergave]** te selecteren.

   Zie [Werken met kiezers](/help/assets/dynamic-media/working-with-selectors.md).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Wanneer u elementen aan de set toevoegt, worden deze automatisch in alfanumerieke volgorde toegevoegd. Nadat u elementen hebt toegevoegd, kunt u deze handmatig opnieuw ordenen of sorteren.

   Sleep indien nodig het pictogram Opnieuw ordenen van een element naar de rechterkant van de bestandsnaam van het element om de volgorde van de afbeeldingen in de lijst met sets te wijzigen.

   ![De volgorde van frame 11 in de centrifugeerset wijzigen door deze naar een nieuwe locatie te slepen.](assets/6_5_spinset-reorderassets.png)

   De volgorde van frame 11 in de centrifugeerset wijzigen door deze naar een nieuwe locatie te slepen.

1. (Optioneel) Voer een van de volgende handelingen uit:

   * Als u een afbeelding wilt verwijderen, selecteert u de afbeelding en tikt u op Element **** verwijderen.

   * Tik op **[!UICONTROL Voorinstelling]** en selecteer vervolgens een voorinstelling die u op alle elementen tegelijk wilt toepassen om een voorinstelling toe te passen in de rechterbovenhoek van de pagina.

1. Click **[!UICONTROL Save]**. De nieuwe centrifugeset wordt weergegeven in de map waarin u deze hebt gemaakt.

## Spin-sets weergeven {#viewing-spin-sets}

U kunt spin-sets maken in de gebruikersinterface of automatisch met behulp van voorinstellingen voor [batchsets](/help/assets/dynamic-media/config-dm.md). Set die is gemaakt met voorinstellingen voor batchsets, wordt echter *niet* weergegeven in de gebruikersinterface. U hebt op drie verschillende manieren toegang tot sets die zijn gemaakt met voorinstellingen voor batchsets. (Deze methoden zijn ook beschikbaar als u de centrifuges in de gebruikersinterface hebt gemaakt.)

>[!NOTE]
>
>U kunt sets ook weergeven in de gebruikersinterface, zoals wordt beschreven in [Spin-sets](#editing-spin-sets)bewerken.

**Draaisets weergeven**

1. Bij het openen van de eigenschappen van een afzonderlijk element. Eigenschappen geven aan welke sets het geselecteerde element is ingesteld als lid van (onder **[!UICONTROL Lid van Sets]**). Klik op de naam van de set om de volledige set weer te geven.

   ![chlimage_1-156](assets/chlimage_1-384.png)

1. Van een lidafbeelding van om het even welke reeks. Selecteer het menu **[!UICONTROL Sets]** om de sets weer te geven waarvan het element lid is.

   ![chlimage_1-157](assets/chlimage_1-385.png)

1. Vanuit het zoeken kunt u **[!UICONTROL Filters]** selecteren, vervolgens **[!UICONTROL Dynamische media]** uitvouwen en **[!UICONTROL Sets]** selecteren.

   De zoekopdracht retourneert overeenkomende sets die handmatig in de gebruikersinterface zijn gemaakt of die automatisch zijn gemaakt met voorinstellingen voor batchsets. Voor geautomatiseerde sets wordt de zoekopdracht uitgevoerd aan de hand van `Starts with` zoekcriteria die afwijken van de AEM-zoekopdracht die is gebaseerd op het gebruik van `Contains` zoekcriteria. Het instellen van het filter op **[!UICONTROL Sets]** is de enige manier om geautomatiseerde sets te doorzoeken.

   ![chlimage_1-158](assets/chlimage_1-386.png)

## Bewerken van centrifuges {#editing-spin-sets}

U kunt diverse bewerkingstaken uitvoeren op bijvoorbeeld de volgende centrifuges:

* Voeg afbeeldingen toe aan de centrifugeset.
* Wijzig de volgorde van de afbeeldingen in de centrifugeset.
* Elementen in de centrifugeset verwijderen.
* Voorinstellingen voor viewers toepassen.
* Verwijder de centrifugeset.

**Een centerset bewerken**

1. Voer een van de volgende handelingen uit:

   * Houd de muisaanwijzer boven een gecentreerd element en tik op **[!UICONTROL Bewerken]** (potloodpictogram).
   * Houd de muisaanwijzer boven een gecentreerd element, tik op **[!UICONTROL Selecteren]** (vinkpictogram) en tik vervolgens op **[!UICONTROL Bewerken]** op de werkbalk.

   * Tik op een gecentreerd element en tik vervolgens op **[!UICONTROL Bewerken]** (potloodpictogram) op de werkbalk.

1. Voer een van de volgende handelingen uit om de centrifugeset te bewerken:

   * Als u de volgorde van afbeeldingen wilt wijzigen, sleept u een afbeelding naar een nieuwe locatie (selecteer het pictogram voor herschikken om items te verplaatsen).
   * Als u items in oplopende of aflopende volgorde wilt sorteren, klikt u op de kolomkop.
   * Als u een element wilt toevoegen of een bestaand element wilt bijwerken, klikt u op Element **[!UICONTROL toevoegen]**. Navigeer naar een element, selecteer het en tik op **[!UICONTROL Selecteren]** in de rechterbovenhoek.
Als u de afbeelding verwijdert die AEM voor de miniatuur gebruikt door deze te vervangen door een andere afbeelding, wordt het oorspronkelijke element nog steeds weergegeven.
   * Als u een element wilt verwijderen, selecteert u het en klikt of tikt u op Element **** verwijderen.
   * Tik op het pictogram Voorinstelling of klik op het pictogram Voorinstelling om een voorinstelling toe te passen.
   * Als u een volledige centrifugeset wilt verwijderen, navigeert u naar de centrifugeset, selecteert u deze en selecteert u **[!UICONTROL Verwijderen]**
   >[!NOTE]
   >
   >U kunt de afbeeldingen in een centrifugeset bewerken door naar de set te navigeren, op Leden **** instellen in de linkertrack te tikken en vervolgens op het potloodpictogram op een afzonderlijk element te tikken om het bewerkingsvenster te openen.

1. Klik op **[!UICONTROL Opslaan]** wanneer u klaar bent met bewerken.

## Voorvertoning van centrifuges weergeven {#previewing-spin-sets}

Zie [Voorvertoning van elementen](/help/assets/dynamic-media/previewing-assets.md)weergeven.

## Spin-sets publiceren {#publishing-spin-sets}

Zie Elementen [](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)publiceren.