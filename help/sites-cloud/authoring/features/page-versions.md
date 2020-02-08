---
title: Werken met paginaversies
description: Versies van een pagina maken, vergelijken en herstellen
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Werken met paginaversies {#working-with-page-versions}

Met Versioning maakt u een &quot;momentopname&quot; van een pagina op een bepaald tijdstip. Met versioning kunt u de volgende handelingen uitvoeren:

* Maak een versie van een pagina.
* Herstel een pagina naar een vorige versie om bijvoorbeeld een wijziging in een pagina ongedaan te maken.
* Vergelijk de huidige versie van een pagina met een vorige versie met verschillen in de gemarkeerde tekst en afbeeldingen.

## Een nieuwe versie maken {#creating-a-new-version}

U kunt een versie van uw bron maken op basis van:

* De [tijdlijn](#creating-a-new-version-timeline)
* De optie [Maken](#creating-a-new-version-create-with-a-selected-resource) (wanneer een bron is geselecteerd)

### Nieuwe versie maken - tijdlijn {#creating-a-new-version-timeline}

1. Navigeer naar de pagina waarvoor u een versie wilt maken.
1. Selecteer de pagina in de [selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Open de **tijdlijn** .
1. Klik/tik op de ellips door het commentaargebied om de opties te tonen:

   ![Versies in de tijdlijn](/help/sites-cloud/authoring/assets/versions-timeline-rail.png)

1. Selecteer **Opslaan als versie**.
1. Voer desgewenst een **label** en **opmerking** in.

   ![Label toevoegen voor een versie](/help/sites-cloud/authoring/assets/versions-add-label.png)

1. Bevestig de nieuwe versie met **Maken**.

   De informatie in de tijdlijn wordt bijgewerkt om de nieuwe versie aan te geven.

### Een nieuwe versie maken - Maken met een geselecteerde bron {#creating-a-new-version-create-with-a-selected-resource}

1. Navigeer naar de pagina waarvoor u een versie wilt maken.
1. Selecteer de pagina in de [selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Selecteer de optie **Maken** op de werkbalk.
1. Hetzelfde dialoogvenster wordt geopend. U kunt desgewenst een **label** en een **opmerking** invoeren.
1. Bevestig de nieuwe versie met **Maken**.

De tijdlijn wordt geopend met de informatie die wordt bijgewerkt om de nieuwe versie aan te geven.

## Terugkeren naar een paginaversie {#reverting-to-a-page-version}

Als er eenmaal een versie is gemaakt, kunt u desgewenst terugkeren naar die versie.

>[!NOTE]
>
>Bij het herstellen van een pagina wordt de gemaakte versie onderdeel van een nieuwe vertakking.
>
>Ter illustratie:
>
>1. Maak versies van een willekeurige pagina.
>1. De initiële labels en namen van versieknooppunten zijn 1.0, 1.1, 1.2 enzovoort.
>1. Herstel de eerste versie; d.w.z. 1.0.
>1. Maak opnieuw nieuwe versies.
>1. De gegenereerde labels en knooppuntnamen zijn nu 1.0.0, 1.0.1, 1.0.2 enzovoort.


Een vorige versie herstellen:

1. Navigeer om de pagina weer te geven die u naar een vorige versie wilt terugkeren.
1. Selecteer de pagina in de [selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Open de kolom **Tijdlijn** en selecteer Alle **of** Versies **** tonen. De paginaversies voor de geselecteerde pagina worden weergegeven.
1. Selecteer de versie waarnaar u wilt terugkeren. De mogelijke opties worden weergegeven:

   ![Vorige versie](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Selecteer **Terugkeren naar deze versie**. De geselecteerde versie wordt hersteld en de informatie in de tijdlijn wordt bijgewerkt.

## Een voorbeeld van een versie bekijken {#previewing-a-version}

U kunt een voorvertoning van een specifieke versie weergeven:

1. Navigeer om de pagina weer te geven die u wilt vergelijken.
1. Selecteer de pagina in de [selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Open de kolom **Tijdlijn** en selecteer Alle **of** Versies **** tonen.
1. De paginaversies worden weergegeven. Selecteer de versie die u wilt voorvertonen:

   ![Voorvertoning versie](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Selecteer **Voorvertoning**. De pagina wordt weergegeven op een nieuw tabblad.

   >[!CAUTION]
   >
   >Als een pagina is verplaatst, kunt u geen voorvertoning meer weergeven van versies die vóór de verplaatsing zijn gemaakt.
   >
   >Als u problemen ondervindt met een voorvertoning, controleert u de [tijdlijn](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) op de pagina om te zien of de pagina is verplaatst.

## Een versie vergelijken met de huidige pagina {#comparing-a-version-with-current-page}

Een vorige versie vergelijken met de huidige pagina:

1. Navigeer om de pagina weer te geven die u wilt vergelijken.
1. Selecteer de pagina in de [selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources).
1. Open de kolom **Tijdlijn** en selecteer Alle **of** Versies **** tonen.
1. De paginaversies worden weergegeven. Selecteer de versie die u wilt vergelijken:

   ![Versies vergelijken](/help/sites-cloud/authoring/assets/versions-revert.png)

1. Selecteer **Vergelijken met huidige** versie. Het [paginascheidingsteken](/help/sites-cloud/authoring/features/page-diff.md) opent en toont de verschillen.

## Timewarp {#timewarp}

Timewarp is een eigenschap die wordt ontworpen om de *gepubliceerde* staat van een pagina op specifieke tijden in het verleden te simuleren.

Omdat content creation een doorlopend en gezamenlijk proces is, is het doel van Timewarp om auteurs in staat te stellen de gepubliceerde website in de loop van de tijd bij te houden om te begrijpen hoe de inhoud is gewijzigd. Deze functie gebruikt de paginaversies om de status van de publicatieomgeving te bepalen.

Dit doet u als volgt:

* Het systeem zoekt naar de paginaversie die op het geselecteerde tijdstip actief was.
* Dit betekent de getoonde versie werd gecreeerd/geactiveerd *vóór* het punt in tijd die in Timewarp wordt geselecteerd.
* Wanneer u naar een verwijderde pagina navigeert, wordt deze ook weergegeven, zolang de oude versies van de pagina nog beschikbaar zijn in de opslagplaats.
* Als geen gepubliceerde versie wordt gevonden, dan zal Timewarp aan de huidige staat van de pagina op het auteursmilieu terugkeren (dit is om een fout/404 pagina te verhinderen, die het doorbladeren zou verhinderen).

### Tijdverdraaiing gebruiken {#using-timewarp}

Timewarp is een [modus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) van de pagina-editor. Om het te beginnen, eenvoudig schakelaar het zoals u een andere wijze.

1. Start de editor voor de pagina waarop u Timewarp wilt starten en selecteer vervolgens **Timewarp** in de modusselectie.

   ![Modus Tijdlijn verdraaien](/help/sites-cloud/authoring/assets/versions-timewarp-mode.png)

1. Stel in het dialoogvenster een doeldatum en -tijd in en klik of tik op Datum **** instellen. Als u geen tijd selecteert, wordt de huidige tijd standaard ingesteld.

   ![Tijdlijndatum tijdverdraaiingsdoel](/help/sites-cloud/authoring/assets/versions-timewarp-target.png)

1. De pagina wordt weergegeven op basis van de datumset. De modus Tijdlijn verdraaien wordt aangegeven via de blauwe statusbalk boven in het venster. Gebruik de koppelingen op de statusbalk om een nieuwe doeldatum of einddatum voor de tijdverdraaiingsmodus te selecteren.

   ![In de modus Tijdlijn verdraaien](/help/sites-cloud/authoring/assets/versions-timewarp.png)

### Beperkingen voor tijdverdraaiing {#timewarp-limitations}

Met Timewarp wordt het best geprobeerd een pagina op een geselecteerd punt in de tijd te reproduceren. Vanwege de complexiteit van het voortdurend ontwerpen van inhoud in AEM is dit echter niet altijd mogelijk. Deze beperkingen moeten in gedachten worden gehouden wanneer u Tijdverdraaiing gebruikt.

* **Tijdlijnverdraaiing werkt op basis van gepubliceerde pagina** &#39;s. Tijdverdraaiing werkt alleen volledig als u de pagina eerder hebt gepubliceerd. Als dat niet het geval is, wordt de huidige pagina in de auteursomgeving weergegeven.
* **Time-warp gebruikt paginaversies** - Als u naar een pagina navigeert die is verwijderd of verwijderd uit de opslagplaats, wordt deze correct weergegeven als de oude versies van de pagina nog steeds beschikbaar zijn in de opslagplaats.
* **Verwijderde versies hebben invloed op Timewarp** - Als versies uit de opslagplaats worden verwijderd, kan Timewarp de juiste weergave niet weergeven.
* **Tijdlijnverdraaiing is alleen** -lezen - U kunt de oude versie van de pagina niet bewerken. Deze kan alleen worden weergegeven. Als u de oudere versie wilt herstellen, moet u dat handmatig doen met [terugzetten](#reverting-to-a-page-version).
* **De tijdverdraaiing is alleen gebaseerd op pagina-inhoud** . Als elementen (zoals code, css, assets/images, enz.) voor het renderen van de website zijn gewijzigd, verschilt de weergave van wat deze oorspronkelijk was, aangezien deze items niet zijn geversieerd in de opslagplaats.

>[!CAUTION]
>
>Timewarp is ontworpen als een hulpmiddel om auteurs te helpen bij het begrijpen en creëren van hun inhoud. Het is niet bedoeld als controlelogboek of voor juridische doeleinden.
