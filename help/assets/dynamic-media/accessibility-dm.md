---
title: Toegankelijkheid in [!DNL Dynamic Media]
description: Leer hoe u met 3D-middelen werkt in Dynamic Media
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
translation-type: tm+mt
source-git-commit: d992b68d4a015f8f947167b5b1d5f0a1ac5c09ec
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---


# Toegankelijkheid in dynamische media {#working-with-three-d-assets-dm}

Dynamische media ondersteunt toetsenbordbesturing en ondersteunende technologieën, zoals JAWS en NVDA-schermlezers, in de hele ontwerpgebruikersinterface.

## Ondersteuning voor toetsenbordtoegankelijkheid in dynamische media

Toetsen die door afzonderlijke elementen van de gebruikersinterface worden ondersteund, zijn meestal duidelijk en gemakkelijk te vinden. Het besturingselement Keyboard in Dynamic Media heeft betrekking op het volgende:

* De mogelijkheid om met `Tab` en `Shift+Tab` toetsaanslagen te navigeren tussen interactieve elementen op de pagina.
Door de invoerfocus naar het volgende gebruikersinterface-element in de tabvolgorde te `Tab` verplaatsen, het gebruiken `Shift+Tab` brengt inputnadruk terug naar het vorige gebruikersinterface element.
Het focustraversal volgt de natuurlijke locatie van het interface-element op het scherm en beweegt van links naar rechts en vervolgens van boven naar beneden.
* De mogelijkheid om de `Spacebar` toets en de `Enter` toets te gebruiken om standaardelementen van de gebruikersinterface te activeren, zoals knoppen, vervolgkeuzelijst, enzovoort.
* De mogelijkheid om bepaalde aangepaste toetsaanslagen te gebruiken voor interactie met complexe UI-elementen, zoals pijltoetsen in de Hot Spot Editor.
* Mogelijkheid om de toetsenbordfocus te zien op het actieve element. Het gebruikersinterface-element dat invoerfocus heeft, krijgt mogelijk een visuele focusindicatie als een rand die rondom het interface-element wordt weergegeven.

Omdat Dynamic Media een insteekmodule voor AEM Assets is, is het meeste toetsenbordbesturingsgedrag hetzelfde als in AEM Assets. De `Cancel` knop in Dynamic Media heeft bijvoorbeeld dezelfde focusmarkering als in AEM Assets en reageert op de `Spacebar` toets als in AEM Assets. Zie [Sneltoetsen in Elementen](/help/assets/accessibility.md#keyboard-shortcuts). Uitzonderingen hierop zijn de hotspot-editor en de editors voor Uitsnijden en Slim uitsnijden van afbeeldingen.

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

In de Hotspot redacteur, laat de Dynamische Media u pijlsleutels gebruiken om de positie van een hete vlek te controleren. Zie [Carousel-banners](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) of [interactieve afbeeldingen](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)

Gebruik de pijltoetsen in de Editor Uitsnijden/Slim uitsnijden van afbeeldingen om de framegrootte bij te snijden of de positie van de afbeelding te wijzigen, of beide. Zie Het slimme uitsnijdstaal of het slimme staal van één afbeelding [bewerken](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Ondersteuning voor toetsenbordtoegankelijkheid voor dynamische mediasviewers {#keyboard-accessibility-for-dm-viewers}

Alle dynamische media-viewercomponenten die niet in de verpakking staan, ondersteunen toetsenbordtoegankelijkheid voor uw klanten.

Zie [Toetsenbordtoegankelijkheid en -navigatie](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/c-keyboard-accessibility.html) in de Naslaggids voor dynamische mediaschermen.

## Ondersteuning voor ondersteunende technologie voor Dynamic Media-viewers {#assistive-technology=support-for-dm-viewers}

Alle viewercomponenten in Dynamic Media ondersteunen de rollen en kenmerken van ARIA (Accessible Rich Internet Applications) om de integratie met ondersteunende hulpmiddelen, zoals schermlezers, te verbeteren.

Zie het onderwerp van de Hulp van de **Technologie van de Steun** in om het even welk het aanpassen kijkersonderwerp in de Dynamische Gids van de Verwijzing van de Kijkers van Media. Zie bijvoorbeeld Ondersteuning [van](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html) ondersteunende hulpmiddelen voor de videoviewer of [ondersteuning](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html?lang=en#viewers-for-aem-assets-only) voor ondersteunende hulpmiddelen voor de interactieve beeldviewer.

>[!MORELIKETHIS]
>
>* [Toegankelijkheid voor Adobe-oplossingen](https://www.adobe.com/accessibility.html)
>* [Toegankelijkheid in Experience Manager-elementen](/help/assets/dynamic-media/accessibility-dm.md)

