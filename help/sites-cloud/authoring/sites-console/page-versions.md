---
title: Werken met paginaversies
description: Leer hoe u in AEM versies van uw pagina's maakt, vergelijkt en terugzet.
exl-id: 33d8e43c-594d-4bba-9631-b2c42a1e910f
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: ebbf38563be65c28384276f7a0baa100f9f384b2
workflow-type: tm+mt
source-wordcount: '1620'
ht-degree: 2%

---

# Werken met paginaversies {#working-with-page-versions}

Met Versioning maakt u een &quot;momentopname&quot; van een pagina op een bepaald tijdstip. Met versioning kunt u de volgende handelingen uitvoeren:

* Maak een versie van een pagina.
* Een vorige versie van een of meer pagina&#39;s opnieuw instellen op:
   * Wijzigingen in de pagina&#39;s ongedaan maken.
   * Verwijderde pagina&#39;s herstellen.
   * Een structuur herstellen (op een opgegeven datum en tijd).
* Een voorvertoning van een versie weergeven.
* Vergelijk de huidige versie van een pagina met een vorige versie.
   * Verschillen in de tekst en afbeeldingen worden gemarkeerd.
* Timewarp gebruikt de paginaversies om de staat van het publicatiemilieu te bepalen.

>[!NOTE]
>
>Alleen inhoud wordt versioned in de AEM-opslagplaats. Dynamische bronnen zoals code, CSS en JavaScript hebben geen versiebeheer.
>
>* Wanneer u versies weergeeft, wordt de inhoud weergegeven met de huidige code, CSS en JavaScript van de opslagplaats.
>* Bij het herstellen van versies wordt alleen de inhoud hersteld en worden de huidige code, CSS en JavaScript van de opslagplaats erop toegepast.

## Een nieuwe versie maken {#creating-a-new-version}

U kunt een versie van uw bron maken op basis van:

* Het [ spoor van de Chronologie ](#creating-a-new-version-timeline)
* [ creeer ](#creating-a-new-version-create-with-a-selected-resource) optie (wanneer een middel wordt geselecteerd)

### Nieuwe versie maken - tijdlijn {#creating-a-new-version-timeline}

1. Navigeer naar de pagina waarvoor u een versie wilt maken.
1. Selecteer de pagina op [ selectiemodus ](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open het **spoor van de Chronologie**.
1. Selecteer de ellips op het commentaarveld om de opties weer te geven:

   ![ Versies in de chronologiespoorstaaf ](/help/sites-cloud/authoring/assets/versions-timeline-rail.png)

1. Selecteer **sparen als Versie**.
1. Ga a **Etiket** en **Commentaar** in, indien nodig.

   ![ voeg etiket voor een versie ](/help/sites-cloud/authoring/assets/versions-add-label.png) toe

1. Bevestig de nieuwe versie met **creeer**.

   De informatie in de tijdlijn wordt bijgewerkt om de nieuwe versie aan te geven.

### Een nieuwe versie maken - Maken met een geselecteerde bron {#creating-a-new-version-create-with-a-selected-resource}

1. Navigeer naar de pagina waarvoor u een versie wilt maken.
1. Selecteer de pagina op [ selectiemodus ](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Selecteer **creeer** optie van de toolbar.
1. Hetzelfde dialoogvenster wordt geopend. U kunt a **Etiket** en a **Commentaar** ingaan, indien nodig.
1. Bevestig de nieuwe versie met **creeer**.

De tijdlijn wordt geopend met de informatie die wordt bijgewerkt om de nieuwe versie aan te geven.

## Versies opnieuw installeren {#reinstating-versions}

Nadat u een versie van de pagina hebt gemaakt, kunt u een eerdere versie op verschillende manieren opnieuw installeren:

* **keert aan deze optie van Versie** van de [ Chronologie ](/help/sites-cloud/authoring/basic-handling.md#timeline) spoor terug

  Vorige versie van geselecteerde pagina opnieuw installeren.

* **herstel** opties van de hoogste [ actiestoolbar ](/help/sites-cloud/authoring/basic-handling.md#actions-toolbar)

   * **herstelt Versie**

     Hiermee herstelt u versies van opgegeven pagina&#39;s in de geselecteerde map. Het kan ook het terugzetten van pagina&#39;s omvatten die eerder zijn geschrapt.

   * **herstelt Boom**

     Zet een versie van een volledige boom op een gespecificeerde datum en tijd opnieuw op. Het kan ook pagina&#39;s bevatten die eerder zijn verwijderd.

>[!NOTE]
>
>Wanneer u een pagina opnieuw invoegt, maakt de gemaakte versie deel uit van een nieuwe vertakking.
>
>Ter illustratie:
>
>1. Maak versies van een willekeurige pagina.
>1. De initiële labels en namen van versieknooppunten zijn 1.0, 1.1, 1.2 enzovoort.
>1. Zet de eerste versie opnieuw in, dat wil zeggen 1.0.
>1. Maak opnieuw versies.
>1. De gegenereerde labels en knooppuntnamen zijn nu 1.0.0, 1.0.1, 1.0.2 enzovoort.

### Versie herstellen {#revert-to-a-version}

Om **terug te keren** de geselecteerde pagina aan een vorige versie:

1. Navigeer om de pagina weer te geven die u naar een vorige versie wilt terugkeren.
1. Selecteer de pagina op [ selectiemodus ](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open de kolom **Tijdlijn** en selecteer **Alles weergeven** of **Versies**. De paginaversies voor de geselecteerde pagina worden weergegeven.
1. Selecteer de versie waarnaar u wilt terugkeren. De mogelijke opties worden weergegeven:

   ![ keert aan deze Versie ](/help/sites-cloud/authoring/assets/versions-revert.png) terug

1. Selecteer **terugkeren aan deze Versie**. De geselecteerde versie wordt hersteld en de informatie in de tijdlijn wordt bijgewerkt.

### Versie herstellen {#restore-version}

Deze methode kan worden gebruikt om versies van opgegeven pagina&#39;s in de huidige map te herstellen. Het kan ook het terugzetten van pagina&#39;s omvatten die eerder zijn geschrapt:

1. Navigeer aan, en [ selecteer ](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources), de vereiste omslag.

1. Selecteer **herstellen**, dan **herstelt Versie** van de hoogste [ actiestoolbar ](/help/sites-cloud/authoring/basic-handling.md#actions-toolbar).

   >[!NOTE]
   >
   >Als u één van beiden hebt:
   >
   >* één pagina heeft geselecteerd die nooit onderliggende pagina&#39;s heeft gehad,
   >* of geen van de pagina&#39;s in de map een versie heeft,
   >
   >De weergave wordt leeg omdat er geen toepasselijke versies zijn.

1. De beschikbare versies worden weergegeven:

   ![ herstelt Versie - Lijst van alle pagina&#39;s in omslag ](/help/sites-cloud/authoring/assets/versions-restore-version-01.png)

1. Voor een specifieke pagina, gebruik de drop-down selecteur onder **HERSTEL AAN VERSIE** om de vereiste versie voor die pagina te selecteren.

   ![ herstelt Versie - Uitgezochte Versie ](/help/sites-cloud/authoring/assets/versions-restore-version-02.png)

1. Selecteer in het hoofdscherm de pagina die u wilt herstellen:

   ![ herstelt Versie - selecteer Pagina ](/help/sites-cloud/authoring/assets/versions-restore-version-03.png)

1. Selecteer **Herstel** voor de geselecteerde versie, van de geselecteerde pagina, die als huidige versie moet worden hersteld.

>[!NOTE]
>
>De volgorde waarin u een vereiste pagina en de bijbehorende versie selecteert, is uitwisselbaar.

### Boom herstellen {#restore-tree}

Deze methode kan worden gebruikt om een versie van een boom op een gespecificeerde datum en tijd te herstellen. Deze pagina kan pagina&#39;s bevatten die eerder zijn verwijderd:

1. Navigeer aan, en [ selecteer ](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources), de vereiste omslag.

1. Selecteer **herstellen**, dan **herstellen Boom** van de hoogste [ actiestoolbar ](/help/sites-cloud/authoring/basic-handling.md#actions-toolbar). De meest recente versie van de boomstructuur wordt weergegeven:

   ![ herstelt Boom ](/help/sites-cloud/authoring/assets/versions-restore-tree-01.png)

1. Gebruik de datum en tijdselecteur bij **Latest Versies bij Datum** zodat kunt u een andere versie van de boom selecteren - te herstellen.

1. Plaats de vlag **Bewaarde Niet Versioned Pagina&#39;s** zoals vereist:

   * Als deze optie actief is (geselecteerd), blijven niet-versioned pagina&#39;s behouden en worden deze niet beïnvloed door het terugzetten.

   * Als de optie inactief (niet geselecteerd) is, worden niet-versioned pagina&#39;s verwijderd, omdat deze niet in de versioned boom bestonden.

1. Selecteer **herstellen** voor de geselecteerde versie van de boom die als *huidige* versie moet worden hersteld.

## Een voorbeeld van een versie bekijken {#previewing-a-version}

U kunt een voorvertoning van een specifieke versie weergeven:

1. Navigeer om de pagina weer te geven die u wilt vergelijken.
1. Selecteer de pagina op [ selectiemodus ](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open de kolom **Tijdlijn** en selecteer **Alles weergeven** of **Versies**.
1. De paginaversies worden weergegeven. Selecteer de versie die u wilt voorvertonen:

   ![ versie van de Voorproef ](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Selecteer **Voorproef**. De pagina wordt weergegeven op een nieuw tabblad.

   >[!CAUTION]
   >
   >Als een pagina is verplaatst, kunt u geen voorvertoning meer weergeven van versies die vóór de verplaatsing zijn gemaakt.
   >
   >Als u problemen met een voorproef ervaart, controleer de [ Chronologie ](/help/sites-cloud/authoring/basic-handling.md#timeline) voor de pagina om te zien of de pagina is bewogen.

## Een versie vergelijken met de huidige pagina {#comparing-a-version-with-current-page}

Een vorige versie vergelijken met de huidige pagina:

1. Navigeer om de pagina weer te geven die u wilt vergelijken.
1. Selecteer de pagina op [ selectiemodus ](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open de kolom **Tijdlijn** en selecteer **Alles weergeven** of **Versies**.
1. De paginaversies worden weergegeven. Selecteer de versie die u wilt vergelijken:

   ![ vergelijkt versies ](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Selecteer **vergelijken met Huidige**. Het [ pagina diff ](/help/sites-cloud/authoring/sites-console/page-diff.md) opent en toont de verschillen.

## Timewarp {#timewarp}

De tijdverdraaiing is een eigenschap die wordt ontworpen om de *gepubliceerde* staat van een pagina op specifieke tijden in het verleden te simuleren.

Omdat content creation een doorlopend en gezamenlijk proces is, is het doel van Timewarp om auteurs in staat te stellen de gepubliceerde website in de loop van de tijd bij te houden, zodat ze kunnen begrijpen hoe de inhoud is gewijzigd. Deze functie gebruikt de paginaversies om de status van de publicatieomgeving te bepalen.

Deze functie gebruiken:

* Het systeem zoekt naar de paginaversie die op het geselecteerde tijdstip actief was.
* Het betekent de getoonde versie werd gecreeerd/geactiveerd *vóór* het punt in tijd die in Tijdverdraaiing wordt geselecteerd.
* Wanneer u naar een pagina navigeert die is verwijderd, wordt deze ook weergegeven, zolang de oude versies van de pagina nog beschikbaar zijn in de opslagplaats.
* Als geen gepubliceerde versie wordt gevonden, keert Timewarp aan de huidige staat van de pagina op het auteursmilieu terug (de reden is om een fout/404 pagina te verhinderen, die het doorbladeren zou verhinderen).

>[!NOTE]
>
>Timewarp werkt en is bedoeld om te worden gebruikt voor AEM-pagina&#39;s - versies voor geschiedenis en lanceringen voor toekomstige inhoudstatussen.
>
>De functie werkt niet bij geneste opstarts of wanneer er fragmenten worden gebruikt.

>[!TIP]
>
>[ de Tijd van de Onderbreking kan ook met Lanceringen worden gebruikt om de toekomst ](/help/sites-cloud/authoring/launches/preview.md) voor te vertonen.

### Tijdverdraaiing gebruiken {#using-timewarp}

De tijdverdraaiing is a [ wijze ](/help/sites-cloud/authoring/page-editor/introduction.md#page-modes) van de paginaredacteur. Om het te beginnen, eenvoudig schakelaar het zoals u een andere wijze.

1. Begin de redacteur voor de pagina waar u Tijdverdraaiing wilt beginnen en dan **Tijdverdraaiing** op de wijzeselectie selecteren.

   ![ wijze Tijdverdraaiing ](/help/sites-cloud/authoring/assets/versions-timewarp-mode.png)

1. In de dialoogdoos, plaats een doeldatum en tijd en klik **Vastgestelde Datum**. Als u geen tijd selecteert, wordt standaard de huidige tijd gebruikt.

   ![ de doeldatum van de tijdverdraaiing ](/help/sites-cloud/authoring/assets/versions-timewarp-target.png)

1. De pagina wordt weergegeven op basis van de datumset. De modus Tijdlijn verdraaien wordt aangegeven met de blauwe statusbalk boven in het venster. Gebruik de koppelingen op de statusbalk, zodat u een nieuwe doeldatum kunt selecteren of de modus Tijdwijziging kunt afsluiten.

   ![ op wijze Timewarp ](/help/sites-cloud/authoring/assets/versions-timewarp.png)

### Beperkingen voor tijdwijziging {#timewarp-limitations}

Met Timewarp wordt het best geprobeerd een pagina op een geselecteerd punt in de tijd te reproduceren. Vanwege de complexiteit van het voortdurend ontwerpen van inhoud in AEM is deze reproductie echter niet altijd mogelijk. Houd deze beperkingen in mening aangezien u Timewarp gebruikt.

* **de werken van de Onderbreking van de Onderbreking die op gepubliceerde pagina&#39;s** worden gebaseerd - de Onderbreking werkt slechts volledig als u eerder de pagina hebt gepubliceerd. Als dat niet het geval is, wordt bij Timewarp de huidige pagina in de auteursomgeving weergegeven.
* **Tijdverdraaiing gebruikt paginaversies** - als u aan een pagina navigeert die is verwijderd/geschrapt uit de bewaarplaats het behoorlijk teruggegeven als de oude versies van de pagina nog in de bewaarplaats beschikbaar zijn.
* **Verwijderde versies beïnvloeden Timewarp** - als de versies uit de bewaarplaats dan worden verwijderd kan de Timewarp niet de correcte mening tonen.
* **Tijdverdraaiing is read-only** - u kunt niet de oude versie van de pagina uitgeven. Deze kan alleen worden weergegeven. Als u de oudere versie wilt herstellen, moet u dat manueel doen gebruikend [ herstellen ](#revert-to-a-version).
* **Tijdverdraaiing is gebaseerd op paginacontent** - als de elementen voor het teruggeven van de website, zoals code, css, en activa veranderden, verschilt de mening van wat het oorspronkelijk was. Deze items zijn niet in de gegevensopslagruimte geversiveerd.
* Timewarp werkt niet voor geneste lanceringen of wanneer ervaringsfragmenten worden gebruikt.

>[!CAUTION]
>
>Timewarp is ontworpen als een hulpmiddel om auteurs te helpen bij het begrijpen en creëren van hun inhoud. Het is niet bedoeld als controlelogboek of voor juridische doeleinden.
