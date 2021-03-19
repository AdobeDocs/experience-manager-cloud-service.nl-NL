---
title: Toegankelijkheid in Dynamic Media
description: Meer informatie over toegankelijkheid in Dynamic Media en Dynamic Media Viewers.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
topic: Zakelijke praktiserer
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---


# Toegankelijkheid in Dynamic Media {#accessibility-in-dm}

Dynamic Media ondersteunt toetsenbordbesturing en ondersteunende hulpmiddelen, zoals JAWS en NVDA-schermlezers, in de hele gebruikersinterface.

## Ondersteuning voor toetsenbordtoegankelijkheid in Dynamic Media {#keyboard-support-in-dm}

Aangezien Dynamic Media een insteekmodule is voor het Experience Managers van , is het meeste toetsenbordbesturingsgedrag hetzelfde als bij Experience Managers. De knop `Cancel` in Dynamic Media heeft bijvoorbeeld dezelfde focusmarkering als in Experience Manager Assets. Het reageert ook op de `Spacebar` toets zoals in de Elementen van de Experience Manager. Zie [sneltoetsen in Elementen](/help/assets/accessibility.md#keyboard-shortcuts).

Toetsen die door de interface-elementen Individuele gebruikers in Dynamic Media worden ondersteund, zijn meestal duidelijk en gemakkelijk te vinden. Toetsenbordbesturing in Dynamic Media gaat over het volgende:

* Mogelijkheid om met de toetsen `Tab` en `Shift+Tab` te navigeren tussen interactieve elementen op de pagina.
Wanneer u `Tab` gebruikt, wordt de invoerfocus naar het volgende interface-element in de tabvolgorde verplaatst. wanneer u `Shift+Tab` gebruikt, krijgt het vorige gebruikersinterface-element weer focus.
Het focustraversal volgt de natuurlijke locatie van het interface-element op het scherm en beweegt van links naar rechts en vervolgens van boven naar beneden. Als een veld een fout bevat, kunt u bovendien op `Tab` drukken om de focus naar het veld te verplaatsen.
* Mogelijkheid om de `Spacebar` en `Enter` sleutel te gebruiken om standaardelementen van de gebruikersinterface, zoals knopen en drop-down lijsten te activeren.
* Mogelijkheid om de toetsenbordfocus te zien op het actieve element. Het element van de gebruikersinterface dat inputnadruk heeft ontving een visuele nadrukaanwijzing als grens die rond het gebruikersinterface element wordt teruggegeven.
* In de Hotspot-editor kunt u bepaalde aangepaste toetsaanslagen gebruiken, zoals pijltoetsen, om te communiceren met complexe gebruikersinterface-elementen om hotspots te verplaatsen.
* In de Interactieve Video redacteur, kunt u `Spacebar` gebruiken om een beeld te selecteren en het toe te voegen aan een segment. Bovendien kunt u de `Backspace` sleutel gebruiken om het geselecteerde punt van **[!UICONTROL Content]** tabel te schrappen. Als u `Tab` ingedrukt houdt, kunt u ook naar wens navigeren tussen interactieve elementen op de pagina.
* In de redacteur van het Gewas van het Beeld/van het Slim Gewas, kunt u het volgende doen:
   * Gebruik de pijltoetsen om de framegrootte bij te snijden, of om de positie van de afbeelding te wijzigen, of beide.
   * Bij de eerste `Tab`-stop wordt het gehele afbeeldingskader gemarkeerd. Vervolgens kunt u het kader verplaatsen met de pijltoetsen op het toetsenbord.
   * De volgende vier `Tab` einden zijn de vier hoeken van het kader. Wanneer de focus op een kaderhoek wordt geplaatst, wordt de hoek gemarkeerd. U kunt ook de pijltoetsen op het toetsenbord gebruiken om de gefocuste hoek te verplaatsen.
Zie [Het slimme uitsnijdstaal of het slimme staal van één afbeelding bewerken](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Support voor hulpprogramma&#39;s in Dynamic Media {#assistive-technology=support-for-dm}

Dynamic Media-gebruikersinterface-elementen werken met ondersteunende hulpmiddelen, zoals schermlezers. De code herkent bijvoorbeeld markeringen op een pagina wanneer u door landmarkeringen navigeert met de sneltoets `D` of gebieden met de sneltoets `R`. De koptekst wordt ook van commentaar voorzien wanneer u navigeert met de sneltoets `H`.

## Ondersteuning voor toetsenbordtoegankelijkheid in Dynamic Media-viewers {#keyboard-accessibility-for-dm-viewers}

Alle Dynamic Media-viewercomponenten die niet in de verpakking staan, ondersteunen toetsenbordtoegankelijkheid voor uw klanten.

Zie [Toetsenbordtoegankelijkheid en -navigatie](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html) in de handleiding Referentie voor Dynamic Media-viewers.

## Support voor hulpprogramma&#39;s in Dynamic Media-viewers {#assistive-technology=support-for-dm-viewers}

Alle Dynamic Media-viewercomponenten ondersteunen de rollen en kenmerken van ARIA (Accessible Rich Internet Applications) om de integratie met ondersteunende hulpmiddelen, zoals schermlezers, te verbeteren.
Zie het **Technische ondersteuning** Help-onderwerp in een aangepast vieweronderwerp in de handleiding voor Dynamic Media-viewers. Zie bijvoorbeeld [Ondersteuning van hulpprogramma&#39;s](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html) voor de videoviewer of [Ondersteuning van hulpprogramma&#39;s](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html?lang=en#viewers-for-aem-assets-only) voor de Interactieve beeldviewer.

>[!MORELIKETHIS]
>
>* [Toegankelijkheid voor Adobe-oplossingen](https://www.adobe.com/accessibility.html)
>* [Toegankelijkheid in Experience Manager-elementen](/help/assets/dynamic-media/accessibility-dm.md)

