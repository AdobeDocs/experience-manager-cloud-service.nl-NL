---
title: Page Diff-optie
description: Met de functie Pagina's diff kunt u twee pagina's naast elkaar vergelijken met de gemarkeerde verschillen.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 0%

---


# Page Diff-optie {#page-diff}

## Inleiding {#introduction}

Het maken van inhoud is een herhalend proces. Om efficiënt te kunnen ontwerpen moet u kunnen zien wat er van de ene iteratie naar de andere is veranderd. Het weergeven van de ene pagina en de andere is inefficiënt en vatbaar voor fouten. Een auteur wil de huidige pagina naast elkaar kunnen vergelijken met een andere versie.

Met de functie Pagina&#39;s diff kunt u twee pagina&#39;s naast elkaar vergelijken met de gemarkeerde verschillen.

>[!CAUTION]
>
>De gebruiker moet over de machtiging **Wijzigen/Maken/Verwijderen** op het knooppunt beschikken `/content/versionhistory` om de functie te kunnen gebruiken.
>
>Zie Developing and Page Diff voor meer technische details over deze functie. <!-- See [Developing and Page Diff](/help/sites-developing/pagediff.md#operation-details) for more technical details on this feature.-->

## Use {#use}

De zijdelingse scheiding kan het volgende vergelijken:

* [Versies](/help/sites-cloud/authoring/features/page-versions.md#comparing-a-version-with-current-page) - Eerdere versie van een pagina met de huidige status
* Actieve kopieën - Live kopie met vervaging <!-- [Live Copies](/help/sites-administering/msm-livecopy.md#comparing-a-live-copy-page-with-a-blueprint-page) - Live Copy with its Blueprint-->
* [Starten](/help/sites-cloud/authoring/launches/editing.md#comparing-a-launch-page-to-its-source-page) - Starten met bron
* Taalkopieën - Een pagina voor en na (her)vertaling <!-- [Language Copies](/help/sites-administering/tc-manage.md#comparing-language-copies) - A page before and after (re-)translation-->

Zie de respectieve onderwerpen over hoe te om diff binnen die contexten te beginnen.

### Presentatie van de verschillen {#presentation-of-differences}

Ongeacht de inhoud die wordt vergeleken, blijft de presentatie van het diff gelijk.

* De inhoud die u hebt geselecteerd toen u de diff-bewerking hebt gestart, wordt links weergegeven (het diff-ingangspunt).
* De vergelijkingsinhoud wordt rechts weergegeven (ten opzichte van de geselecteerde inhoud).

Als u bijvoorbeeld versies vergelijkt, wordt de huidige versie links weergegeven en wordt de vorige versie rechts weergegeven.

De bron van beide pagina&#39;s wordt duidelijk weergegeven in de koptekstbalk boven in het browservenster.

![Versies naast elkaar](/help/sites-cloud/authoring/assets/versions-side-by-side.png)

De diff ontdekt veranderingen op het component en HTML niveau. Items die zijn gewijzigd, worden met verschillende kleuren gemarkeerd.

**Componentwijzigingen**

* Lichtgroen - component toegevoegd
* Roze - component verwijderd
* Blauw - component gewijzigd
* Blauw - component verplaatst

De kleuren Gewijzigd en Verplaatst zijn hetzelfde.

**HTML-wijzigingen**

* Donkergroen - HTML toegevoegd
* Rood - HTML verwijderd

>[!NOTE]
>
>Bij het vergelijken van taalkopieën wordt het markeren gedeactiveerd, omdat in een vertaling alles verandert en het markeren geen nut zou hebben.

### Volledig scherm en afsluiten {#fullscreen-and-exiting}

Als u de focus op bepaalde inhoud wilt plaatsen, klikt u op het pictogram voor een volledig scherm voor een van de twee zijden van het deelvenstervak om het venster te vergroten naar het volledige browservenster.

![Knop Volledig scherm](/help/sites-cloud/authoring/assets/versions-full-screen.png)

De geselecteerde zijde vult het gehele venster, maar de balk blijft boven aan de pagina zodat u tussen de twee pagina&#39;s kunt schakelen.

![Modus Volledig scherm](/help/sites-cloud/authoring/assets/versions-full-screen-mode.png)

>[!NOTE]
>
>Als de breedte van de browser niet geschikt is voor beide paginanamen in de volledige schermweergave, wordt alleen de naam van de pagina weergegeven en is de andere naam beschikbaar achter ellips.

U kunt de volledige schermweergave ook sluiten door op het pictogram Volledig scherm afsluiten te klikken.

![Modus Volledig scherm afsluiten](/help/sites-cloud/authoring/assets/versions-exit-full-screen.png)

U kunt het schuifregelaar Naast elkaar op elk gewenst moment afsluiten door op de knop Sluiten in de koptekst te klikken.

## Beperkingen {#limitations}

In sommige situaties kan het zijn dat het pagina-diff geen verschil detecteert zoals u had verwacht.

* Bij verschillende versies en lanceringen houdt diff geen rekening met dynamische componenten zoals broodkruimels, menu&#39;s, productlijsten of logo&#39;s (componenten die op de plaatsstructuur vertrouwen om hun inhoud terug te geven).
* Voor versies maakt diff niet het toegangsbeheerbeleid en levende exemplaarverhoudingen opnieuw.
* Als er wijzigingen worden aangebracht in een afbeelding, zoals het wijzigen van de kenmerken alt, title of src, wordt deze in blauw gemarkeerd als gewijzigd. In sommige gevallen heeft de afbeelding echter een Base64-representatie van het kenmerk src en zelfs als beide afbeeldingen er hetzelfde uitzien, worden ze door het diff als verschillend gemarkeerd vanwege de verschillende src-kenmerken.
* Het diff kan beeldomwenteling niet ontdekken.
* Als een pagina wordt verplaatst, kunt u geen diff met om het even welke versies meer uitvoeren die vóór de beweging worden gemaakt.
   * Als u problemen ondervindt met een diff, controleert u de [tijdlijn](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) voor de pagina om te zien of de pagina is verplaatst.

>[!NOTE]
>
>Versies kunnen niet met elkaar worden vergeleken. Alleen de huidige versie kan worden vergeleken met andere versies van de pagina. De huidige versie is altijd de versie die met wijzigingen is gemarkeerd.

>[!NOTE]
>
>Raadpleeg de documentatie voor ontwikkelaars van deze functie voor meer informatie over de werking van het mechanisme voor paginascheiding en de beperkingen die paginavervorming kunnen beïnvloeden. <!-- For more details about the operation of the page diff mechanism as well as limitations which can affect page diff, please see the [developer documentation](/help/sites-developing/pagediff.md) of this feature.-->
