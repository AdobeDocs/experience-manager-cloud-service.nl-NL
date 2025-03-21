---
title: Toegankelijkheid in dynamische media
description: Leer hoe u met video werkt in Dynamic Media, zoals aanbevolen procedures voor het coderen van video's, het publiceren van video's naar YouTube en het weergeven van videoverslagen. Leer ook hoe u ondertiteling, ondertitels of hoofdstukmarkeringen aan video's kunt toevoegen.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
feature: Accessibility
role: Admin,User
exl-id: f8d2dcbf-f61a-4b27-a3fc-406e3662adcb
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---

# Toegankelijkheid in dynamische media {#accessibility-in-dm}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

{{work-with-dynamic-media}}

Dynamische media ondersteunt toetsenbordbesturing en ondersteunende technologieën, zoals JAWS en NVDA-schermlezers, in de hele ontwerpgebruikersinterface.

## Ondersteuning voor toetsenbordtoegankelijkheid in dynamische media {#keyboard-support-in-dm}

Omdat Dynamische media een plug-in in [!DNL Experience Manager Assets] is, is het meeste toetsenbordbesturingsgedrag hetzelfde als in [!DNL Experience Manager Assets] . De knop `Cancel` in Dynamische media heeft bijvoorbeeld dezelfde focusmarkering als in [!DNL Experience Manager Assets] . Deze reageert ook op de `Spacebar` -toets zoals in [!DNL Experience Manager Assets] . Zie [ toetsenbordkortere weg in Assets ](/help/assets/accessibility.md#keyboard-shortcuts).

Toetsen die worden ondersteund door afzonderlijke gebruikersinterface-elementen in dynamische media zijn meestal duidelijk en gemakkelijk te vinden. Het besturingselement Keyboard in Dynamic Media heeft betrekking op het volgende:

* De mogelijkheid om `Tab` - en `Shift+Tab` -toetsaanslagen te gebruiken om te navigeren tussen interactieve elementen op de pagina.
Als u `Tab` gebruikt, wordt de invoerfocus op het volgende interface-element in de tabvolgorde gebracht. Als u `Shift+Tab` gebruikt, wordt de invoerfocus weer op het vorige gebruikersinterface-element geplaatst.
Het focustraversal volgt de natuurlijke locatie van het interface-element op het scherm en beweegt van links naar rechts en vervolgens van boven naar beneden. Als een veld een fout bevat, kunt u bovendien op `Tab` drukken om de focus naar het veld te verplaatsen.
* Mogelijkheid om de toetsen `Spacebar` en `Enter` te gebruiken om standaardelementen van de gebruikersinterface te activeren, zoals knoppen en vervolgkeuzelijsten.
* Mogelijkheid om de toetsenbordfocus te zien op het actieve element. Het element van de gebruikersinterface dat inputnadruk heeft ontving een visuele nadrukaanwijzing als grens die rond het gebruikersinterface element wordt teruggegeven.
* In de Hotspot-editor kunt u bepaalde aangepaste toetsaanslagen gebruiken, zoals pijltoetsen, om te communiceren met complexe gebruikersinterface-elementen om hotspots te verplaatsen.
* In de Interactieve Video redacteur, kunt u `Spacebar` gebruiken om een beeld te selecteren en het toe te voegen aan een segment. Daarnaast kunt u de `Backspace` -toets gebruiken om het geselecteerde item van het tabblad **[!UICONTROL Content]** te verwijderen. Als u op `Tab` drukt, kunt u ook naar wens navigeren tussen interactieve elementen op de pagina.
* In de redacteur van het Gewas van het Beeld/van het Slim Gewas, kunt u het volgende doen:
   * Gebruik de pijltoetsen om de framegrootte bij te snijden, of om de positie van de afbeelding te wijzigen, of beide.
   * Bij de eerste stop van `Tab` wordt het hele afbeeldingskader gemarkeerd. Vervolgens kunt u het kader verplaatsen met de pijltoetsen op het toetsenbord.
   * De volgende vier `Tab` stops zijn de vier hoeken van het frame. Wanneer de focus op een kaderhoek wordt geplaatst, wordt de hoek gemarkeerd. U kunt ook de pijltoetsen op het toetsenbord gebruiken om de gefocuste hoek te verplaatsen.
Zie [ Uitgevend het slimme gewas of slim monster van één enkel beeld ](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (Experience Manager 6.5) or Coral Spectrum (in Skyline)) as entire Experience Manager Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Ondersteuning voor ondersteunende technologie in Dynamic Media {#assistive-technology=support-for-dm}

Dynamische media-gebruikersinterface-elementen werken met ondersteunende hulpmiddelen, zoals schermlezers. De code herkent bijvoorbeeld markeringen op een pagina wanneer u door markeringen navigeert met sneltoetsen `D` of gebieden met sneltoetsen `R` . De kop wordt ook van commentaar voorzien wanneer u navigeert met de sneltoets voor koppen `H` .

## Ondersteuning voor toetsenbordtoegankelijkheid in Dynamic Media-viewers {#keyboard-accessibility-for-dm-viewers}

Alle dynamische media-viewercomponenten die niet in de verpakking staan, ondersteunen toetsenbordtoegankelijkheid voor uw klanten.

Zie [ de toegankelijkheid van het Toetsenbord en navigatie ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html) in de Dynamische Gids van de Verwijzing van de Kijkers van Media.

## Technische ondersteuning in Dynamic Media-viewers {#assistive-technology=support-for-dm-viewers}

Alle Dynamic Media Viewer-componenten ondersteunen de rollen en kenmerken van ARIA (Accessible Rich Internet Applications) om de integratie met ondersteunende hulpmiddelen, zoals schermlezers, te verbeteren.
Zie het **onderwerp van de Hulp van de technologiesteun 0} {in om het even welk het aanpassen kijkersonderwerp in de Dynamische Gids van de Verwijzing van de Kijkers van Media.** Bijvoorbeeld, zie ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html) de technologiesteun van 0} Hulpmiddelen {voor de Videokijker, of [ de technologiesteun van de Hulp ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html#viewers-for-aem-assets-only) voor de Interactieve kijker van het Beeld.[

## Ondersteuning voor Closed Caption in [!DNL Dynamic Media] {#closed-caption-support}

Dynamische media ondersteunt de levering van video&#39;s en adaptieve videosets met ondertiteling. De bijschriften moeten vóór de video-inhoud worden weergegeven.

Zie [ Video in Dynamische Media - voeg gesloten titels aan video ](/help/assets/dynamic-media/video.md#adding-captions-to-video) toe.


>[!MORELIKETHIS]
>
>* [ Toegankelijkheid voor de oplossingen van Adobe ](https://www.adobe.com/accessibility.html)
>* [ Toegankelijkheid in Experience Manager Assets ](/help/assets/dynamic-media/accessibility-dm.md)
