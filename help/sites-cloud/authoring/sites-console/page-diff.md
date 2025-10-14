---
title: Pagina grijs
description: Met de functie Pagina's diff kunt u twee pagina's naast elkaar vergelijken met de gemarkeerde verschillen.
exl-id: 6e5c7f14-c980-48e3-8bdd-a7ec10a9e680
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: ae1dedc3d0533205decc08d396c5a844c4525ba2
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Pagina grijs {#page-diff}

## Inleiding {#introduction}

Inhoud maken is een herhalend proces. Om efficiënt te kunnen ontwerpen moet u kunnen zien wat er van de ene iteratie naar de andere is veranderd. Het weergeven van de ene pagina en de andere is inefficiënt en vatbaar voor fouten. Een auteur wil de huidige pagina naast elkaar kunnen vergelijken met een andere versie.

Met de functie Pagina&#39;s diff kunt u twee pagina&#39;s naast elkaar vergelijken met de gemarkeerde verschillen.

>[!NOTE]
>
>De gebruiker moet **hebben wijzigt/creeert/schrapt** toestemming op de knoop `/content/versionhistory` om de eigenschap te gebruiken.
>
>Zie [&#x200B; het Ontwikkelen en Afschuiving van de Pagina &#x200B;](/help/implementing/developing/introduction/page-diff.md#operation-details) voor meer technische details op deze eigenschap.

## Gebruiken {#use}

De zijdelingse scheiding kan het volgende vergelijken:

* [&#x200B; Versies &#x200B;](/help/sites-cloud/authoring/sites-console/page-versions.md#comparing-a-version-with-current-page) - Eerdere versie van een pagina met zijn huidige staat
* [&#x200B; Levende Exemplaren &#x200B;](/help/sites-cloud/administering/msm/creating-live-copies.md#comparing-a-live-copy-page-with-a-blueprint-page) - Levend Exemplaar met zijn Vervaging
* [&#x200B; Lanceringen &#x200B;](/help/sites-cloud/authoring/launches/editing.md#comparing-a-launch-page-to-its-source-page) - Lanceer met zijn Source
* [&#x200B; Kopieën van de Taal &#x200B;](/help/sites-cloud/administering/translation/managing-projects.md#comparing-language-copies) - een pagina vóór en na (re-)vertaling

Zie de respectieve onderwerpen over hoe te om diff binnen die contexten te beginnen.

### Presentatie van de verschillen {#presentation-of-differences}

Ongeacht de inhoud die wordt vergeleken, blijft de presentatie van het diff gelijk.

* De inhoud die u hebt geselecteerd toen u de diff-bewerking hebt gestart, wordt links weergegeven (het diff-ingangspunt).
* De vergelijkingsinhoud wordt rechts weergegeven (ten opzichte van de geselecteerde inhoud).

Als u bijvoorbeeld versies vergelijkt, wordt de huidige versie links weergegeven en wordt de vorige versie rechts weergegeven.

De bron van beide pagina&#39;s wordt duidelijk weergegeven in de koptekstbalk boven in het browservenster.

![&#x200B; Versies zij aan zij mening &#x200B;](/help/sites-cloud/authoring/assets/versions-side-by-side.png)

De diff ontdekt veranderingen op het component en HTML niveau. Items die zijn gewijzigd, worden met verschillende kleuren gemarkeerd.

**de Veranderingen van de Component**

* Lichtgroen - component toegevoegd
* Roze - component verwijderd

**de Veranderingen van HTML**

* Donkergroen - HTML toegevoegd
* Rood - HTML verwijderd

>[!NOTE]
>
>Bij het vergelijken van taalkopieën wordt het markeren gedeactiveerd, omdat in een vertaling alles verandert en het markeren geen nut zou hebben.

### Volledig scherm en afsluiten {#fullscreen-and-exiting}

Als u de focus op bepaalde inhoud wilt plaatsen, klikt u op het pictogram voor een volledig scherm voor een van de twee zijden van het deelvenstervak om dit naar het volledige browservenster te vergroten.

![&#x200B; Volledige het schermknoop &#x200B;](/help/sites-cloud/authoring/assets/versions-full-screen.png)

De geselecteerde zijde vult het gehele venster, maar de balk blijft boven aan de pagina zodat u tussen de twee pagina&#39;s kunt schakelen.

![&#x200B; Volledige het schermwijze &#x200B;](/help/sites-cloud/authoring/assets/versions-full-screen-mode.png)

>[!NOTE]
>
>Als de breedte van de browser niet geschikt is voor beide paginanamen in de volledige schermweergave, wordt alleen de naam van de pagina weergegeven en is de andere naam beschikbaar achter ellips.

U kunt de volledige schermweergave ook sluiten door op het pictogram Volledig scherm afsluiten te klikken.

![&#x200B; Uitgang het volledige schermwijze &#x200B;](/help/sites-cloud/authoring/assets/versions-exit-full-screen.png)

U kunt het schuifregelaar Naast elkaar op elk gewenst moment afsluiten door op de knop Sluiten in de koptekst te klikken.

## Beperkingen {#limitations}

In sommige situaties kan het zijn dat het pagina-diff geen verschil detecteert zoals u had verwacht.

* Wanneer het verschillen van pagina&#39;s voor gebruik met [&#x200B; Edge Delivery Services worden gecreeerd, &#x200B;](/help/edge/overview.md) de pagina&#39;s zullen naast-zij voor gemakkelijke vergelijking worden getoond, maar de verschillen zullen niet worden benadrukt.
* Bij verschillende versies en lanceringen houdt diff geen rekening met dynamische componenten zoals broodkruimels, menu&#39;s, productlijsten of logo&#39;s (componenten die op de plaatsstructuur vertrouwen om hun inhoud terug te geven).
* Voor versies, maakt diff niet het toegangsbeheerbeleid en levende exemplaarverhoudingen opnieuw.
* Als een pagina wordt verplaatst, kunt u geen diff met om het even welke versies meer uitvoeren die vóór de beweging worden gemaakt.
   * Als u problemen met afschuiving ervaart, controleer de [&#x200B; Chronologie &#x200B;](/help/sites-cloud/authoring/basic-handling.md#timeline) voor de pagina om te zien of de pagina is bewogen.

>[!NOTE]
>
>Versies kunnen niet met elkaar worden vergeleken. Alleen de huidige versie kan worden vergeleken met andere versies van de pagina. De huidige versie is altijd de versie die met wijzigingen is gemarkeerd.

>[!NOTE]
>
>Voor meer details over de verrichting van het mechanisme en de beperkingen van de paginascheiding die paginascheiding kunnen beïnvloeden, zie {de documentatie van de 0} ontwikkelaar [&#128279;](/help/implementing/developing/introduction/page-diff.md) van deze eigenschap.
