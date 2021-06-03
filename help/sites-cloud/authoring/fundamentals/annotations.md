---
title: Pagina-annotaties toevoegen
description: Annotatiemodus gebruiken om annotaties en schetsen op pagina's te laten zoals u notities gebruikt om het revisieproces van de inhoud te begeleiden
exl-id: a9cb9745-8140-4795-a5f9-fb3a1a299bd8
source-git-commit: 5d533354a29237aeafc00e5570ede3ab00b721fd
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 0%

---

# Pagina-annotaties toevoegen {#adding-page-annotations}

Voor het maken van inhoud voor uw digitale ervaring is vaak overleg en feedback nodig voordat deze wordt gepubliceerd. Voor dit feedbackproces kunt u AEM annotaties toevoegen aan uw inhoud.

Een annotatie plaatst een eenvoudige schets of notitie (denk in real-world kleverige noot) op de pagina. Met de annotatie kunt u opmerkingen of vragen aan andere auteurs en revisoren overlaten.

>[!TIP]
>
>Vergeet niet dat [commentaren](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) ook beschikbaar zijn voor het verstrekken van terugkoppelen op een pagina.

Een speciale [modus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) wordt gebruikt voor het maken en weergeven van annotaties.

>[!TIP]
>
>Afhankelijk van uw vereisten kunt u ook een [workflow](/help/sites-cloud/authoring/workflows/overview.md) ontwikkelen om meldingen te verzenden wanneer annotaties worden toegevoegd, bijgewerkt of verwijderd.

## Annotatie-indicator {#annotation-indicator}

Annotaties worden niet weergegeven in de modus Bewerken, maar het symbool rechtsboven op de werkbalk geeft aan hoeveel annotaties er bestaan voor de huidige pagina. Het pictogram vervangt het standaardpictogram Annotaties, maar werkt nog steeds als een snelle koppeling die van/naar de modus Annotatie schakelt:

![Indicator voor aantekening](/help/sites-cloud/authoring/assets/annotation-indicator.png)

## Annotatiemodus {#annotate-mode}

Annotaties zijn alleen zichtbaar in de modus Annotatie.

1. U gaat de modus Annotatie in met het pictogram op de werkbalk (rechtsboven) bij het bewerken van een pagina:

   ![Knop Annotatie](/help/sites-cloud/authoring/assets/annotations.png)

   U kunt nu bestaande annotaties weergeven.

   ![Voorbeelden van annotaties](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. Klik of tik op de annotatie om het dialoogvenster met annotaties te openen en de details ervan weer te geven.

   ![Details van aantekening](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. Tik op de x-knop rechts van de bovenste werkbalk om de modus Annotatie af te sluiten en terug te keren naar de eerder gebruikte modus.

## Annotaties {#annotating-a-component} toevoegen en bewerken

In de modus Annotatie kunt u niet alleen notities weergeven, maar ook annotaties maken, bewerken, verplaatsen of verwijderen

1. [Start de ](#annotate-mode) modus Annoteren op de pagina.

1. Klik of tik op het pictogram Annotatie toevoegen (plus symbool links op de werkbalk) om annotaties toe te voegen.

1. Klik of tik op de vereiste component (componenten die kunnen worden geannoteerd, worden gemarkeerd met een blauwe rand) om de annotatie toe te voegen en het dialoogvenster te openen:

   ![Een aantekening toevoegen](/help/sites-cloud/authoring/assets/annotation-adding.png)

   Hier kunt u het juiste veld en/of pictogram gebruiken om:

   * Voer de annotatietekst in.
   * Maak een schets (lijnen en vormen) om een gebied van de component te markeren.

      ![Knop Annotatieschets](/help/sites-cloud/authoring/assets/annotation-sketch.png)

      De cursor verandert in een dradenkruis wanneer u een schets maakt. U kunt meerdere afzonderlijke lijnen tekenen. De schetslijn geeft de annotatiekleur weer en kan een pijl, cirkel of ovaal zijn.

   * Kies of wijzig de kleur:

      ![Knop Kleurstaal notitie](/help/sites-cloud/authoring/assets/annotation-color-swatch.png)

1. U kunt het dialoogvenster met annotaties sluiten door buiten het dialoogvenster te klikken of erop te tikken. Er wordt een afgekapte weergave van de annotatie getoond, samen met eventuele schetsen:

   ![Schetsen voor notities](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. Nadat u een specifieke annotatie hebt bewerkt, kunt u:

   * Klik of tik op de tekstmarkering om de annotatie te openen. Nadat u de volledige tekst hebt geopend, kunt u wijzigingen aanbrengen of de annotatie [verwijderen.](#deleting-annotations)
   * Verander de positie van de tekstmarkering.
   * Klik of tik op een schetslijn om die schets te selecteren en sleep deze naar de gewenste positie.
   * Een component verplaatsen of kopiëren
      * Eventuele verwante annotaties en de bijbehorende schetsen worden ook verplaatst of gekopieerd, maar hun positie ten opzichte van de alinea blijft ongewijzigd.


>[!NOTE]
>
>Annotaties kunnen niet worden toegevoegd aan een pagina die is vergrendeld door een andere gebruiker.

>[!NOTE]
>
>De definitie van een afzonderlijk componenttype bepaalt of het toevoegen van een aantekening (ANNOTATION) mogelijk is (of niet) op instanties van die component.

## Annotatie en schetsen {#deleting-annotations} verwijderen

Annotaties en de bijbehorende schetsen kunnen worden verwijderd.

1. [Start de ](#annotate-mode) modus Annoteren op de pagina.

1. Klik of tik op de tekstmarkering om de annotatie te openen.

1. Klik of tik op het pictogram Verwijderen.

   ![Annotatie verwijderen](/help/sites-cloud/authoring/assets/annotation-delete.png)

1. De annotatie en alle bijbehorende schetsen worden verwijderd.

>[!NOTE]
>
>Als u een component verwijdert, worden alle annotaties en schetsen verwijderd die aan die bron zijn gekoppeld, ongeacht de positie op de pagina als geheel.

## Alleen schetsen {#deleting-sketches} verwijderen

U kunt alleen specifieke schetsen verwijderen in plaats van de gehele annotatie met alle gekoppelde schetsen.

1. [Start de ](#annotate-mode) modus Annoteren op de pagina.

1. Klik of tik op de schets. AEM markeert deze met een donkerder blauw vak.

   ![Schets selecteren om te verwijderen](/help/sites-cloud/authoring/assets/annotation-sketch-delete.png)

1. Druk op de toets Delete op het toetsenbord.

1. De schets wordt verwijderd, maar de annotatie blijft behouden.

## Annoteren van andere bronnen {#annotating-other-resources}

Naast componenten kunt u verschillende bronnen van annotatie voorzien:

* Elementen [Annoteren van elementen](/help/assets/manage-digital-assets.md#annotating)
* Video-elementen annoteren [Video-elementen annoteren](/help/assets/manage-video-assets.md#annotate-video-assets)
