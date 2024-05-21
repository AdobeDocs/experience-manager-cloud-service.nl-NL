---
title: Toegankelijkheid in Dynamic Media
description: Leer hoe u in Dynamic Media met video werkt, zoals tips en trucs voor het coderen van video's, het publiceren van video's naar YouTube en het weergeven van videoverslagen. Leer ook hoe u ondertiteling, ondertitels of hoofdstukmarkeringen aan video's kunt toevoegen.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
feature: Accessibility
role: Admin,User
exl-id: f8d2dcbf-f61a-4b27-a3fc-406e3662adcb
source-git-commit: 02ad83eb9fa9ed3bf06cf7fe0ef10fd9577f66a9
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---

# Toegankelijkheid in Dynamic Media {#accessibility-in-dm}

Dynamic Media ondersteunt toetsenbordbesturing en ondersteunende hulpmiddelen, zoals JAWS en NVDA-schermlezers, in de hele gebruikersinterface.

## Ondersteuning voor toetsenbordtoegankelijkheid in Dynamic Media {#keyboard-support-in-dm}

Omdat Dynamic Media een insteekmodule is voor [!DNL Experience Manager Assets], is het meeste toetsenbordbesturingsgedrag hetzelfde als in [!DNL Experience Manager Assets]. Bijvoorbeeld de `Cancel` in Dynamic Media heeft dezelfde focus als in [!DNL Experience Manager Assets]. Het reageert ook op de `Spacebar` key as in [!DNL Experience Manager Assets]. Zie [sneltoetsen in elementen](/help/assets/accessibility.md#keyboard-shortcuts).

Toetsen die door de interface-elementen Individuele gebruikers in Dynamic Media worden ondersteund, zijn meestal duidelijk en gemakkelijk te vinden. Toetsenbordbesturing in Dynamic Media gaat over het volgende:

* Gebruiksmogelijkheden `Tab` en `Shift+Tab` toetsaanslagen om te navigeren tussen interactieve elementen op de pagina.
Gebruiken `Tab` gaat inputnadruk naar het volgende gebruikersinterface element in de lusjeorde vooruit; het gebruiken `Shift+Tab` Hiermee wordt invoerfocus teruggezet naar het vorige gebruikersinterface-element.
Het focustraversal volgt de natuurlijke locatie van het interface-element op het scherm en beweegt van links naar rechts en vervolgens van boven naar beneden. Als een veld een fout bevat, kunt u bovendien op `Tab` om de focus naar de afbeelding te verplaatsen.
* De mogelijkheid om de `Spacebar` en `Enter` toets voor het activeren van standaardelementen van de gebruikersinterface, zoals knoppen en vervolgkeuzelijsten.
* Mogelijkheid om de toetsenbordfocus te zien op het actieve element. Het element van de gebruikersinterface dat inputnadruk heeft ontving een visuele nadrukaanwijzing als grens die rond het gebruikersinterface element wordt teruggegeven.
* In de Hotspot-editor kunt u bepaalde aangepaste toetsaanslagen gebruiken, zoals pijltoetsen, om te communiceren met complexe gebruikersinterface-elementen om hotspots te verplaatsen.
* In de Interactieve Video-editor kunt u de opdracht `Spacebar` om een afbeelding te selecteren en toe te voegen aan een segment. Daarnaast kunt u de opdracht `Backspace` toets om het geselecteerde item uit het menu **[!UICONTROL Content]** tab. Ook, drukken `Tab` functioneert naar wens om te navigeren tussen interactieve elementen op de pagina.
* In de redacteur van het Gewas van het Beeld/van het Slim Gewas, kunt u het volgende doen:
   * Gebruik de pijltoetsen om de framegrootte bij te snijden, of om de positie van de afbeelding te wijzigen, of beide.
   * De eerste `Tab` Met Stoppen wordt het gehele afbeeldingskader gemarkeerd. Vervolgens kunt u het kader verplaatsen met de pijltoetsen op het toetsenbord.
   * De volgende vier `Tab` stops zijn de vier hoeken van het frame. Wanneer de focus op een kaderhoek wordt geplaatst, wordt de hoek gemarkeerd. U kunt ook de pijltoetsen op het toetsenbord gebruiken om de gefocuste hoek te verplaatsen.
Zie [Het slimme uitsnijdstaal of het slimme staal van één afbeelding bewerken](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (Experience Manager 6.5) or Coral Spectrum (in Skyline)) as entire Experience Manager Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Support voor hulpprogramma&#39;s in Dynamic Media {#assistive-technology=support-for-dm}

Dynamic Media-gebruikersinterface-elementen werken met ondersteunende hulpmiddelen, zoals schermlezers. De code herkent bijvoorbeeld markeringen op een pagina wanneer u door markeringen met een sneltoets navigeert `D` of gebieden met sneltoetsen `R`. De kop wordt ook van commentaar voorzien wanneer u navigeert met de sneltoets voor koppen `H`.

## Ondersteuning voor toetsenbordtoegankelijkheid in Dynamic Media-viewers {#keyboard-accessibility-for-dm-viewers}

Alle Dynamic Media-viewercomponenten die niet in de verpakking staan, ondersteunen toetsenbordtoegankelijkheid voor uw klanten.

Zie [Toetsenbordtoegankelijkheid en -navigatie](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html) in de Dynamic Media Viewers Reference Guide.

## Ondersteuning voor hulpprogramma&#39;s in Dynamic Media-viewers {#assistive-technology=support-for-dm-viewers}

Alle Dynamic Media-viewercomponenten ondersteunen de rollen en kenmerken van ARIA (Accessible Rich Internet Applications) om de integratie met ondersteunende hulpmiddelen, zoals schermlezers, te verbeteren.
Zie de **Technische ondersteuning** Help-onderwerp in elk aangepast vieweronderwerp in de Dynamic Media Viewers Reference Guide. Zie bijvoorbeeld [Technische ondersteuning](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html) voor de videoviewer, of [Technische ondersteuning](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html#viewers-for-aem-assets-only) voor de Interactieve kijker van het Beeld.

## Ondersteuning voor Closed Caption in [!DNL Dynamic Media] {#closed-caption-support}

Dynamic Media ondersteunt de levering van video&#39;s en adaptieve videosets met ondertiteling. De bijschriften moeten vóór de video-inhoud worden weergegeven.

Zie [Video in Dynamic Media - Gesloten bijschriften toevoegen aan video](/help/assets/dynamic-media/video.md#adding-captions-to-video).


>[!MORELIKETHIS]
>
>* [Toegankelijkheid voor Adobe-oplossingen](https://www.adobe.com/accessibility.html)
>* [Toegankelijkheid in Experience Manager Assets](/help/assets/dynamic-media/accessibility-dm.md)
