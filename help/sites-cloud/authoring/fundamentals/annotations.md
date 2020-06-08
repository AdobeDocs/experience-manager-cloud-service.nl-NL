---
title: Pagina-annotaties toevoegen
description: Met veel rechtstreeks aan inhoud gerelateerde componenten kunt u een annotatie toevoegen
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 1%

---


# Pagina-annotaties toevoegen {#adding-page-annotations}

Het toevoegen van inhoud aan de pagina&#39;s van uw website is vaak onderwerp van besprekingen alvorens het eigenlijk wordt gepubliceerd. Om dit te helpen, staan vele componenten direct met inhoud verwant (in tegenstelling, bijvoorbeeld, aan lay-out) u toe om een aantekening toe te voegen.

Een annotatie plaatst een gekleurde schets of notitie op de pagina. Met de annotatie kunt u (of andere gebruikers) opmerkingen en/of vragen laten voor andere auteurs/revisoren.

>[!NOTE]
>
>Vergeet niet dat [opmerkingen](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) ook beschikbaar zijn voor het geven van feedback op een pagina.

## Annotaties {#annotations}

Een speciale [modus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) wordt gebruikt voor het maken en weergeven van annotaties.

>[!CAUTION]
>
>Als u een bron verwijdert (bijvoorbeeld een component), worden alle annotaties en schetsen verwijderd die aan die bron zijn gekoppeld, ongeacht de positie op de pagina als geheel.

>[!NOTE]
>
>Afhankelijk van uw vereisten kunt u ook een workflow ontwikkelen om meldingen te verzenden wanneer annotaties worden toegevoegd, bijgewerkt of verwijderd.

### Een component annoteren {#annotating-a-component}

In de modus Annoteren kunt u annotaties voor uw inhoud maken, bewerken, verplaatsen of verwijderen:

1. U kunt de modus Annotatie activeren met het pictogram op de werkbalk (rechtsboven) wanneer u een pagina bewerkt:

   ![Knop Annotatie](/help/sites-cloud/authoring/assets/annotations.png)

   U kunt nu bestaande annotaties weergeven.

   >[!NOTE]
   >
   >Tik op het pictogram Annotatie (x-symbool) rechts van de bovenste werkbalk om de modus Annotatie af te sluiten.

1. Klik of tik op het pictogram Annotatie toevoegen (plus symbool links op de werkbalk) om annotaties toe te voegen.

   >[!NOTE]
   >
   >Tik op of klik op het pictogram Annuleren (x-symbool in een witte cirkel) links van de bovenste werkbalk om het toevoegen van annotaties (en terug te keren naar de weergave) te stoppen.

1. Klik of tik op de vereiste component (componenten die kunnen worden geannoteerd, worden gemarkeerd met een blauwe rand) om de annotatie toe te voegen en het dialoogvenster te openen:

   ![Een aantekening toevoegen](/help/sites-cloud/authoring/assets/annotation-adding.png)

   Hier kunt u het juiste veld en/of pictogram gebruiken om:

   * Voer de annotatietekst in.
   * Maak een schets (lijnen en vormen) om een gebied van de component te markeren.

      ![Knop Annotatieschets](/help/sites-cloud/authoring/assets/annotation-sketch.png)

      De cursor verandert in een dradenkruis wanneer u een schets maakt. U kunt meerdere afzonderlijke lijnen tekenen. De schetslijn geeft de annotatiekleur weer en kan een pijl, cirkel of ovaal zijn.

   * Kies of wijzig de kleur:

      ![Knop Kleurstaal notitie](/help/sites-cloud/authoring/assets/annotation-color-swatch.png)

   * Verwijder de annotatie.

      ![Knop Notitie verwijderen](/help/sites-cloud/authoring/assets/annotation-delete.png)

1. U kunt het dialoogvenster met annotaties sluiten door buiten het dialoogvenster te klikken of erop te tikken. Een afgekapte weergave (het eerste woord) van de annotatie wordt samen met eventuele schetsen weergegeven:

   ![Schetsen voor notities](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. Nadat u een specifieke annotatie hebt bewerkt, kunt u:

   * Klik of tik op de tekstmarkering om de annotatie te openen. Nadat u de volledige tekst hebt geopend, kunt u de annotatie wijzigen of verwijderen.

      * Schetsen kunnen niet onafhankelijk van de annotatie worden verwijderd.
   * Verander de positie van de tekstmarkering.
   * Klik of tik op een schetslijn om die schets te selecteren en sleep deze naar de gewenste positie.
   * Een component verplaatsen of kopiëren

      * Eventuele verwante annotaties en de bijbehorende schetsen worden ook verplaatst of gekopieerd en hun positie ten opzichte van de alinea blijft dezelfde.


1. Tik op het pictogram Annotatie (x-symbool) rechts van de bovenste werkbalk of klik op het pictogram Annotatie om de Annotatiemodus te sluiten en terug te keren naar de eerder gebruikte modus.

>[!NOTE]
>
>Annotaties kunnen niet worden toegevoegd aan een pagina die is vergrendeld door een andere gebruiker.

>[!NOTE]
>
>De definitie van een afzonderlijk componenttype bepaalt of het toevoegen van een aantekening (ANNOTATION) mogelijk is (of niet) op instanties van die component.

## Annotatie-indicator {#annotation-indicator}

Annotaties worden niet weergegeven in de modus Bewerken, maar het symbool rechtsboven op de werkbalk geeft aan hoeveel annotaties er bestaan voor de huidige pagina. Het pictogram vervangt het standaardpictogram Annotaties, maar werkt nog steeds als een snelle koppeling die van/naar de modus Annotatie schakelt:

![Indicator voor aantekening](/help/sites-cloud/authoring/assets/annotation-indicator.png)

## Annoteren van andere bronnen {#annotating-other-resources}

Naast componenten kunt u verschillende bronnen van annotatie voorzien:

* Annoteren van activa [Annoteren van activa](/help/assets/manage-digital-assets.md#annotating)
* Video-elementen annoteren [Video-elementen annoteren](/help/assets/manage-video-assets.md#annotate-video-assets)
