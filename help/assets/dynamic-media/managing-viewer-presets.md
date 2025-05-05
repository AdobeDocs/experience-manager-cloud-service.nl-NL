---
title: Voorinstellingen voor viewers beheren
description: Leer hoe u viewervoorinstellingen maakt en beheert in Dynamic Media.
contentOwner: Rick Brough
feature: Viewer Presets,Viewers
role: User
exl-id: da2e1a10-f54b-440e-b70c-f04ad4caeac1
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '4184'
ht-degree: 7%

---

# Voorinstellingen voor viewers beheren{#managing-viewer-presets}

Een viewervoorinstelling is een verzameling instellingen die bepalen hoe gebruikers rich-media-elementen op hun computerschermen en mobiele apparaten weergeven. Beheerders kunnen voorinstellingen voor viewers maken. Er zijn instellingen beschikbaar voor een array met viewerconfiguratieopties. U kunt bijvoorbeeld de weergavegrootte of het zoomgedrag van de viewer wijzigen.

<!-- OBSOLETE SDK withdrawn from public view. Available internally only at `http://staging.scene7.com/s7sdk/3.8/docs/jsdoc/symbols/_s7sdk.html` 

For instructions on creating and customizing your own HTML5 viewer presets, see the *Adobe Scene7 HTML5 Viewer SDK*. The SDK is available on the IS publish server embedded in the SDK itself. Each library version has its own SDK documentation included.

Path: `<scene7_domain>/s7sdk/<library_version>/docs/jsdocs/index.html`.
For example, 3.5 SDK: [https://s7d1.scene7.com/s7sdk/3.5/docs/jsdoc/index.html](https://s7d1.scene7.com/s7sdk/3.5/docs/jsdoc/index.html)

-->

Zie ook de [ Dynamische Gids van de Verwijzing van de Kijkers van Media ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html).

In deze sectie wordt beschreven hoe u voorinstellingen voor viewers kunt maken, bewerken en beheren. U kunt een viewervoorinstelling op elk gewenst moment op een element toepassen. Zie [ Kijker toepassen vooraf instelt ](#applying-a-viewer-preset-to-an-asset).

>[!NOTE]
>
>Het uitgeven om het even welk *vooraf bepaalde, uit-van-de-doos kijker stelt* vooraf in is geen gesteund scenario. Als u probeert een voorinstelling voor een viewer buiten het vak te bewerken, wordt u gevraagd de voorinstelling van de viewer op te slaan onder een andere naam.

## Toetsenbordtoegankelijkheid voor viewers {#keyboard-accessibility-for-viewers}

Alle viewers die niet in de verpakking zijn opgenomen, ondersteunen toegankelijkheid van het toetsenbord.

Zie ook [ toegankelijkheid van het Toetsenbord en navigatie ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html).

## Voorinstellingen voor viewers beheren {#managing-viewer-presets-1}

U kunt in Adobe Experience Manager voorinstellingen voor viewers toevoegen, bewerken, verwijderen, publiceren, ongedaan maken en voorvertonen door naar **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]>[!UICONTROL Viewer Presets]** te navigeren.

![ 6_5_tools-assets-viewerpresets ](assets/6_5_tools-assets-viewerpresets.png)

>[!NOTE]
>
>Standaard geeft het systeem 15 voorinstellingen voor viewers weer wanneer u Viewers selecteert in de gedetailleerde weergave van elementen. U kunt deze limiet verhogen. Zie [ Verhoog het aantal kijker vooraf instelt die ](#increasing-the-number-of-viewer-presets-that-display) tonen.

### Viewer-ondersteuning voor responsieve webpagina&#39;s {#viewer-support-for-responsive-designed-web-pages}

Verschillende webpagina&#39;s hebben verschillende behoeften. Soms wilt u bijvoorbeeld een webpagina die een koppeling bevat waarmee de HTML5 Viewer in een apart browservenster wordt geopend. In andere gevallen moet u de HTML5 Viewer rechtstreeks insluiten op de hostpagina. In het laatste geval heeft de webpagina een statische indeling. Of de interface reageert op een ander scherm en wordt op verschillende apparaten of voor verschillende venstergrootten van de browser anders weergegeven. Om aan deze behoeften tegemoet te komen, ondersteunen alle vooraf gedefinieerde, kant-en-klare HTML5 Viewers die bij Dynamic Media worden geleverd zowel statische webpagina&#39;s als responsieve webpagina&#39;s.

Zie [ Responsieve Statische bibliotheek van het Beeld ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/responsive-static-image-library/c-about-responsive-static-image-library.html#about-responsive-image-library) in het *Dynamische Beeld van Media die en API Hulp teruggeven* voor meer informatie over hoe te om ontvankelijke kijkers op uw Web-pagina&#39;s in te bedden.

>[!NOTE]
>
>Publiceer alle viewers buiten de box voordat u ze voor het eerst gebruikt.
>Zie [ Publish Kijker vooraf instelt ](#publishing-viewer-presets).

### Compatibiliteit van het systeem met voorinstellingen voor viewers  {#viewer-preset-system-compatibility}

Alle voorinstellingen van de out-of-the-box Viewer die bij Dynamische media worden geleverd, zijn volledig compatibel met de volgende systemen:

* Desktops
* Apple iPhone
* Apple iPad
* Android™ Smartphone
* Android™-tablet
<!-- OUTDATED 2/25/22 * For video, extra support for MP4 playback is provided for [BlackBerry&reg;](https://developer.blackberry.com/devzone/develop/supported_media/bb_media_support_at_a_glance.html#kba1328730952678) and [Windows&reg; Phone](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/supported-codecs). -->

### Rijke mediatypen voor viewervoorinstellingen {#rich-media-types-for-viewer-presets}

Beheerders kunnen de volgende rich media-typen toevoegen en aanpassen bij het maken van voorinstellingen voor viewers.

<table>
 <tbody>
  <tr>
   <td><strong> Reeks Carousel </strong><br /> </td>
   <td><p>Hotspots of afbeeldingen met hyperlinks of beide worden toegevoegd aan een reeks van twee of meer afbeeldingen. Een klant kan de afbeeldingen naar links of rechts pannen en vervolgens een hotspot op een afbeelding selecteren voor meer informatie of voor directe aankoop vanaf de landings-, categorie- of homepages van een website.</p> </td>
  </tr>
    <tr>
   <td><strong> Dimensional </strong><br /> </td>
   <td><p>Hiermee geeft u 3D-scènes weer waarmee u de camera kunt draaien, pannen, zoomen of opnieuw centreren.</p> </td>
  </tr>
  <tr>
   <td><strong>Zoomen met flyout</strong></td>
   <td><p>Hiermee geeft u een tweede afbeelding van het ingezoomde gebied weer naast de oorspronkelijke afbeelding. Er zijn geen besturingselementen om te gebruiken. Gebruikers verplaatsen de selectie over het gebied dat ze willen weergeven.</p> <p>Houd er bij het bepalen van het totale bandbreedtegebruik voor deze viewer rekening mee dat zowel de hoofdafbeelding als de vervolgafbeelding in de viewer worden weergegeven. De grootte van de vervolgafbeelding wordt bepaald door de grootte van de hoofdafbeelding (breedte en hoogte van werkgebied) en de zoomfactor. Als u wilt voorkomen dat het flyout-bestand te groot wordt, brengt u de volgende twee waarden met elkaar in evenwicht: als u een grote hoofdafbeeldingsgrootte hebt, verlaagt u de waarde voor Zoomfactor. (De breedte en hoogte van de Flyout bepalen de grootte van het wegvliegvenster, maar niet de grootte van het vliegend beeld dat aan de kijker wordt gediend.)</p> <p>Als de hoofdafbeelding bijvoorbeeld 350 x 350 pixels groot is, met een zoomfactor van 3, is de resulterende uitvliegafbeelding 1050 x 1050 pixels. Als de hoofdafbeeldingsgrootte 300 x 300 pixels is, met een zoomfactor van 4, is de vervolgafbeelding 1200 x 1200 pixels. Afhankelijk van de kwaliteitsinstelling van JPEG (aanbevolen instellingen liggen tussen 80 en 90), kunt u de bestandsgrootte aanzienlijk verkleinen. De aanbevolen zoomfactoren zijn 2,5 tot 4, afhankelijk van de grootte van de hoofdafbeelding.</p> </td>
  </tr>
  <tr>
   <td><strong>Inline zoomen</strong></td>
   <td>Hiermee geeft u een afbeelding weer van het ingezoomde gebied in de oorspronkelijke viewer. Er zijn geen besturingselementen om te gebruiken. Gebruikers verplaatsen de selectie dus over het gebied dat ze willen weergeven.</td>
  </tr>
  <tr>
   <td><strong>Afbeeldingsset</strong></td>
   <td>In de Vastgestelde kijker van het Beeld, kunnen de gebruikers verschillende meningen of kleurenvariaties van een punt zien door een duimnagelbeeld te selecteren. Deze viewer beschikt ook over zoomgereedschappen waarmee u afbeeldingen nauwkeurig kunt bekijken.</td>
  </tr>
  <tr>
   <td><strong>Interactieve afbeelding</strong></td>
   <td>Hotspots worden toegevoegd aan gedeelten van een afbeelding die een klant vervolgens kan selecteren voor meer informatie of voor directe aankoop vanaf de landings-, categorie- of homepages van een website.</td>
  </tr>
  <tr>
   <td><strong>Interactieve video</strong></td>
   <td>Miniaturen worden toegevoegd aan tijdlijnsegmenten in een video die een klant vervolgens kan selecteren voor meer informatie of voor directe aankoop vanaf de landings-, categorie- of homepages van een website.</td>
  </tr>
  <tr>
   <td><strong>Gemengde media</strong></td>
   <td>Hiermee geeft u verschillende typen media weer in één viewer. U kunt centrifuges, afbeeldingssets, afbeeldingen en video's opnemen.</td>
  </tr>
  <tr>
   <td><strong>Panoramische afbeelding</strong></td>
   <td><p>Met de Panoramische afbeelding en de Panoramische VR-viewers worden bolvormige panoramische afbeeldingen weergegeven zodat gebruikers deze kunnen bekijken in een 360°-kijkervaring van een ruimte, eigenschap, locatie of landschap.</p> <p>Een geüploade afbeelding kan alleen als een bolvormig panorama worden beschouwd als de afbeelding een van de volgende opties of beide heeft:</p>
    <ul>
     <li>Een hoogte-breedteverhouding van 2:1.</li>
     <li>Gelabeld met de trefwoorden <code>equirectangular</code> of <code>spherical</code> en <code>panorama</code> of <code>spherical </code> en <code>panoramic</code> . Zie <a href="/help/sites-cloud/authoring/sites-console/tags.md"> Gebruikend Markeringen </a>.</li>
    </ul> <p>Zowel zijn de aspectverhouding als de sleutelwoordcriteria van toepassing op panoramische activa voor de de detailpagina van activa en de component van "Panoramische Media" WCM.</p></td>
  </tr>
    <tr>
   <td><strong> Slimme Video van het Gewas </strong><br /> </td>
   <td><p>Met deze viewer kunt u automatisch het brandpunt in een video detecteren en uitsnijden.</p> </td>
  </tr>
  <tr>
   <td><strong>Set draaien</strong></td>
   <td>Biedt meerdere weergaven van een afbeelding, zodat gebruikers het object kunnen draaien om de verschillende zijden en hoeken te bekijken.</td>
  </tr>
  <tr>
   <td><strong>360-video</strong></td>
   <td><p>Met de 360/VR-videoviewer kunt u rechthoekige video renderen voor een indrukwekkende kijkervaring van een kamer, eigenschap, locatie, landschap of medische procedure.</p> <p>Tijdens het afspelen op een plat beeldscherm heeft de gebruiker controle over de kijkhoek. Bij afspelen op mobiele apparaten worden de ingebouwde gyroscopische besturingselementen gebruikt.</p> <p>De viewer bevat native ondersteuning voor de levering van 360 video-elementen. Standaard is geen aanvullende configuratie nodig voor weergave of afspelen. U levert 360 Video gebruikend standaardvideouitbreidingen zoals .mp4, .mkv, en .mov. De meest algemene codec is H.264.</p> </td>
  </tr>
  <tr>
   <td><strong>Video</strong></td>
   <td><p>Speelt video af met progressieve of adaptieve bitsnelheidstreaming. Bij adaptieve bitsnelheidstreaming worden automatisch apparaat- en bandbreedtedetectie uitgevoerd voor de juiste videokwaliteit in de juiste indeling.</p> </td>
  </tr>
  <tr>
   <td><strong>Verticaal zoomen</strong></td>
   <td><p>Met de verticale zoomviewer kunt u een productafbeeldingsweergave maximaliseren, zodat uw gebruikers de beste weergave van een product krijgen. De verticale locatie van stalen doet het volgende:</p>
    <ul>
     <li>Hiermee zorgt u ervoor dat stalen zich boven de vouw bevinden.<br/> Bij horizontale stalen zijn, afhankelijk van de schermgrootte van het bureaublad van de gebruiker, de stalen pas zichtbaar wanneer de gebruiker de pagina omlaag schuift. Door de stalen verticaal in de viewer te plaatsen, weet u zeker dat ze zichtbaar zijn, ongeacht de schermgrootte van de gebruiker.</li>
     <li>Maximaliseert de hoofdafbeeldingsgrootte.<br /> Bij horizontale stalen moet ruimte op de pagina worden gereserveerd om ervoor te zorgen dat deze zichtbaar zijn. Hierdoor nam de grootte van de hoofdafbeelding af. Met een verticale staallay-out hoeft u deze ruimte echter niet toe te wijzen. Op die manier kunt u de grootte van de hoofdafbeelding maximaliseren.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Zoomen</strong></td>
   <td>Hiermee kunnen gebruikers inzoomen op het gebied door het te selecteren. Gebruikers kunnen besturingselementen selecteren om in te zoomen, uit te zoomen en de standaardgrootte van de afbeelding te herstellen.</td>
  </tr>
 </tbody>
</table>

### Lijst met voorinstellingen voor viewers buiten de box {#list-of-out-of-the-box-viewer-presets}

In de volgende tabel worden alle vooraf gedefinieerde, kant-en-klare voorinstellingen voor viewers weergegeven die bij Dynamische media worden geleverd.

Zie ook [ Levende Demo&#39;s ](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html).

Voor informatie over ondersteunde webbrowsers en besturingssysteemversies voor Viewers kunt u de Opmerkingen bij de release Viewers bekijken.

Zie &quot;de versiennota&#39;s van Kijkers&quot;in de inhoudstafel van de [ Gids van de Verwijzing van Kijkers ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html).

>[!NOTE]
>
>Alle voorinstellingen van de viewer buiten de box in Dynamic Media worden geactiveerd (ingeschakeld), maar u moet ze publiceren.
>Zie [ publiceren kijkersvoorinstellingen ](#publishing-viewer-presets).
>
>Alle nieuwe viewervoorinstellingen die u maakt en toevoegt, moeten zowel worden geactiveerd *als *gepubliceerd.
>Zie [ kijker activeren of deactiveren vooraf instelt ](#activating-or-deactivating-viewer-presets) en [ het Publiceren kijker vooraf instelt ](#publishing-viewer-presets).

<table>
 <tbody>
  <tr>
   <td><strong>Titel van voorinstelling van viewer</strong></td>
   <td><strong>Type</strong></td>
   <td><strong> CSS dossier - naam </strong><br /> </td>
  </tr>
  <tr>
   <td>Carrousel_Gestippeld_donker</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_dotted_dark.css</code></td>
  </tr>
  <tr>
   <td>Carrousel_Gestippeld_licht</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_dotted_light.css</code></td>
  </tr>
  <tr>
   <td>Carousel_Numeric_dark</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_numeric_dark.css</code></td>
  </tr>
  <tr>
   <td>Carousel_Numeric_light</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_numeric_light.css</code></td>
  </tr>
  <tr>
   <td>Flyout</td>
   <td>Flyout_Zoom</td>
   <td><code>html5_flyoutviewer.css</code></td>
  </tr>
  <tr>
   <td>Afbeeldingsset_donker</td>
   <td>Afbeeldingsset</td>
   <td><code>html5_zoomviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>ImageSet_light</td>
   <td>Afbeeldingsset</td>
   <td><code>html5_zoomviewer_light.css</code></td>
  </tr>
  <tr>
   <td>InlineMixedMedia_donker</td>
   <td>Gemengd_Media</td>
   <td><code>html5_inlinemixedmediaviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>InlineMixedMedia_light</td>
   <td>Gemengd_Media</td>
   <td><code>html5_inlinemixedmediaviewer_light.css</code></td>
  </tr>
  <tr>
   <td>InlineZoom</td>
   <td>Flyout_Zoom</td>
   <td><code>html5_inlinezoomviewer.css</code></td>
  </tr>
  <tr>
   <td>GemengdMedia_donker</td>
   <td>Gemengd_Media</td>
   <td><code>html5_mixedmediaviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>GemengdMedia_licht</td>
   <td>Gemengd_Media</td>
   <td><code>html5_mixedmediaviewer_light.css</code></td>
  </tr>
  <tr>
   <td>PanoramaImage</td>
   <td>Panorama_Afbeelding</td>
   <td><code>html5_panoramicimage.css</code></td>
  </tr>
  <tr>
   <td>PanoramaImageVR</td>
   <td>Panorama_Afbeelding</td>
   <td><code>html5_panoramicimage.css</code></td>
  </tr>
  <tr>
   <td>Shopable_Banner</td>
   <td>Interactive_Image</td>
   <td><code>html5_interactiveimage.css</code></td>
  </tr>
  <tr>
   <td>Shopable_Video_donker</td>
   <td>Interactive_Video</td>
   <td><code>html5_interactivevideoviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>Shopable_Video_light</td>
   <td>Interactive_Video</td>
   <td><code>html5_interactivevideovewer_light.css</code></td>
  </tr>
  <tr>
   <td>SpinSet_donker</td>
   <td>Spin_set</td>
   <td><code>html5_spinviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>SpinSet_light</td>
   <td>Spin_set</td>
   <td><code>html5_spinviewer_light.css</code></td>
  </tr>
  <tr>
   <td><p>Video</p> <p>(Inclusief ondersteuning voor ondertiteling)</p> </td>
   <td>Video</td>
   <td><code>html5_videoviewer.css</code></td>
  </tr>
  <tr>
   <td><p>Video360_social</p> <p>(Inclusief standaardbesturingselementen voor het afspelen van video, videorendering wordt uitgevoerd in de stereomodus, handmatige besturing van het gezichtspunt is uitgeschakeld, maar gyroscopische besturing is ingeschakeld en er zijn geen functies voor sociale media)</p> </td>
   <td>Video_360</td>
   <td><code>html5_video360viewersocial.css</code></td>
  </tr>
  <tr>
   <td><p>Video360VR</p> <p>(Ontworpen voor eindgebruikers die een virtuele realiteitsbril gebruiken. Inclusief standaardbesturingselementen voor het afspelen van video en functies voor sociale media)</p> </td>
   <td>Video_360</td>
   <td><code>html5_video360viewer.css</code></td>
  </tr>
  <tr>
   <td><p>Video_social</p> <p>(Inclusief ondersteuning voor ondertiteling en sociale media)</p> </td>
   <td>Video</td>
   <td><code>html5_videoviewersocial.css</code></td>
  </tr>
  <tr>
   <td>Zoomen_donker<br /> </td>
   <td>Zoomen <br /> </td>
   <td><code>html5_basiczoomviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>Zoom_light <br /> </td>
   <td>Zoomen</td>
   <td><code>html5_basiczoomviewer_light.css</code></td>
  </tr>
  <tr>
   <td>ZoomVertical_black<br /> </td>
   <td>Verticaal_Zoomen</td>
   <td><code>html5_zoomverticalviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>ZoomVertical_light</td>
   <td>Verticaal_Zoomen</td>
   <td><code>html5_zoomverticalviewer_light.css</code></td>
  </tr>
 </tbody>
</table>

### Matrix voor ondersteunde mobiele viewers {#supported-mobile-viewers-gestures-matrix}

In de volgende tabel worden de bewegingen van de mobiele viewer weergegeven die worden ondersteund op iOS-, Android™ 2.x- en Android™ 3.x-apparaten.

<table>
 <tbody>
  <tr>
   <td><strong>Gesture</strong></td>
   <td><strong>Zoomen met flyout</strong></td>
   <td><strong>Zoomen</strong></td>
   <td><strong>Draaien</strong></td>
  </tr>
  <tr>
   <td><p><strong>Slepen</strong></p> </td>
   <td><p>Pannen</p> </td>
   <td><p>Pannen</p> </td>
   <td><p>Pannen</p> </td>
  </tr>
  <tr>
   <td><p><strong>Selecteren</strong></p> </td>
   <td><p>Flyout-venster tonen</p> </td>
   <td><p>De gebruikersinterface weergeven of verbergen</p> </td>
   <td><p>De gebruikersinterface weergeven of verbergen</p> </td>
  </tr>
  <tr>
   <td><p><strong>Dubbelselecteren</strong></p> </td>
   <td><p>Niet van toepassing</p> </td>
   <td><p>Inzoomen of voorinstellingen</p> </td>
   <td><p>Inzoomen of voorinstellingen</p> </td>
  </tr>
  <tr>
   <td><p><strong>Kneep open</strong></p> </td>
   <td><p>Niet van toepassing</p> </td>
   <td><p>Inzoomen (alleen iOS en Android™ 3x)</p> </td>
   <td><p>Inzoomen (alleen iOS en Android™ 3x)</p> </td>
  </tr>
  <tr>
   <td><p><strong>Kneep dicht</strong></p> </td>
   <td><p>Niet van toepassing</p> </td>
   <td><p>Uitzoomen (alleen iOS en Android™ 3x)</p> </td>
   <td><p>Uitzoomen (alleen iOS en Android™ 3x)</p> </td>
  </tr>
  <tr>
   <td><p><strong>Veeggebaar</strong></p> </td>
   <td><p>Schuift de staalbalk</p> </td>
   <td><p>Afbeeldingen schuiven</p> </td>
   <td><p>Spinnen</p> </td>
  </tr>
  <tr>
   <td><p><strong>Vlikken</strong></p> </td>
   <td><p>Schuift de staalbalk</p> </td>
   <td><p>Afbeeldingen schuiven</p> </td>
   <td><p>Spinnen</p> </td>
  </tr>
 </tbody>
</table>

## Het aantal weergegeven viewervoorinstellingen vergroten {#increasing-the-number-of-viewer-presets-that-display}

Experience Manager biedt een groot aantal verschillende viewervoorinstellingen wanneer u elementen weergeeft via **[!UICONTROL Detail View]** > **[!UICONTROL Viewers]** . U kunt het aantal weergegeven viewers verhogen of verlagen.

**om het aantal kijker te verhogen stelt die worden getoond:**

1. Navigeer aan CRXDE Lite ([ https://localhost:4502/crx/de ](https://localhost:4502/crx/de)).
1. Ga naar het keuzerondje met voorinstellingen voor viewer op `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist`

   ![ chlimage_1-221 ](/help/assets/dynamic-media/assets/chlimage_1-221.png)

1. Wijzig in de eigenschap **[!UICONTROL limit]** de **[!UICONTROL Value]**, die standaard op 15 is ingesteld, in het gewenste getal.
1. Navigeer naar de gegevensbron voor de viewervoorinstelling op `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist/datasource`

   ![ chlimage_1-222 ](/help/assets/dynamic-media/assets/chlimage_1-222.png)

1. Wijzig in de eigenschap limit het getal in het gewenste getal, bijvoorbeeld `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. Selecteer **[!UICONTROL Save All]** .

## Voorinstellingen voor viewers maken {#creating-a-new-viewer-preset}

Door viewervoorinstellingen te maken, kunt u verschillende instellingen toepassen op weergave en interactie met elementen. U hoeft echter geen voorinstellingen voor viewers te maken. Desgewenst kunt u de standaardvoorinstellingen voor viewers gebruiken die al bij Experience Manager Assets worden geleverd.

Als u een viewervoorinstelling maakt nadat u deze hebt opgeslagen, wordt de status van de viewer automatisch geactiveerd (ingesteld op **[!UICONTROL On]** ) op de pagina Voorinstellingen viewer. Deze status betekent dat deze zichtbaar is in de component Dynamische media en de component Interactieve media en wanneer u een voorvertoning van een afbeelding of video weergeeft.

Sommige voorinstellingen voor viewers hebben exclusieve instellingen die het gebruik en het algemene gedrag van de viewer kunnen beïnvloeden. Afhankelijk van de viewervoorinstelling die u maakt, wilt u zich bewust zijn van deze speciale overwegingen.

Zie [ Speciale overwegingen voor het creëren van een Interactieve Kijker vooraf ingesteld ](#special-considerations-for-creating-an-interactive-viewer-preset).

Zie [ Speciale overwegingen voor het creëren van een vooraf ingestelde Kijker van de Banner van de Carrousel ](#special-considerations-for-creating-a-carousel-banner-viewer-preset).

**om kijkersvoorinstellingen tot stand te brengen:**

1. Selecteer in de linkerbovenhoek van Experience Manager het Experience Manager-logo en ga vervolgens in de linkerrails naar **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]** .

   ![ 6_5_viewerpresets ](assets/6_5_viewerpresets.png)

1. Selecteer op de pagina Voorinstellingen viewer op de werkbalk de optie **[!UICONTROL Create]** .
1. Voer in het veld **[!UICONTROL Preset Name]** in het dialoogvenster **[!UICONTROL New Viewer Preset]** de naam van de nieuwe voorinstelling in. Kies een zorgvuldig gekozen naam. U kunt deze niet bewerken nadat u **[!UICONTROL Create]** hebt geselecteerd.

   Wanneer u de voorinstelling later in deze stappen opslaat, wordt de naam weergegeven op de pagina Voorinstellingen viewer onder de kolomkop Titel voorinstelling.

1. Selecteer in het vervolgkeuzemenu Type rijke media het type voorinstelling voor de viewer dat u wilt maken en selecteer vervolgens in de rechterbovenhoek van de pagina **[!UICONTROL Create]** .

   Zie [ Rijke Types van Media voor Kijker vooraf instelt ](#rich-media-types-for-viewer-presets).

1. Selecteer op de pagina Viewer Preset Editor de tab **[!UICONTROL Appearance]** .
1. Voer een van de volgende handelingen uit:

   * Selecteer in het keuzemenu **[!UICONTROL Selected Type]** een component waarvan u het visuele ontwerp wilt aanpassen. U kunt ook elk visueel element in de viewer selecteren om het te selecteren voor configuratie.

     Met de visuele editor kunt u zien welk effect een bepaalde eigenschap heeft op een stijl. Stel een eigenschap in of pas deze aan om direct te zien welk effect het heeft op de viewer met behulp van het voorbeeld links van de editor.

     De CSS het stileren eigenschappen voor elk type van vooraf ingesteld kijker worden beschreven in het &quot;Aanpassen *`<viewer name>`* onderwerp van de Hulp van de Kijker&quot;in de [ Gids van de Verwijzing van Kijkers ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html). Bijvoorbeeld, als u een kijker creeert vooraf ingesteld van het type `Mixed_Media`, zie [ Gemengde kijker van Media ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/mixed-media/customing-mixed-media/c-html5-mixedmedia-viewer-customizingviewer.html) voor een lijst en een beschrijving van elk bezit aanpassen.

   * Als u stijlinstellingen hebt gedefinieerd in een afzonderlijk CSS-bestand, kunt u het CSS-bestand uploaden naar Experience Manager Assets. Als u het geüploade CSS-bestand wilt zoeken en dit wilt koppelen aan de viewervoorinstelling, selecteert u **[!UICONTROL Import CSS]** onder het keuzemenu **[!UICONTROL Selected Type]** (schuif zo nodig door de visuele editor omhoog om dit te zien).

     Wanneer u een CSS-bestand importeert, controleert de visuele editor of de CSS de juiste viewermarkeringen gebruikt. Als u bijvoorbeeld een zoomviewer maakt, moeten alle CSS-regels die u importeert, worden gedefinieerd met de viewerklassenaam `.s7mixedmediaviewer` die is gedefinieerd voor een bovenliggend viewerelement.

     U kunt willekeurige, handgemaakte CSS importeren zolang deze de CSS-markeringen voor een bepaalde viewer correct definieert. (CSS de tellers worden beschreven in om het even welk &quot;het Aanpassen *&lt;viewer name>* het onderwerp van de Hulp van de Kijker&quot;in de [ Gids van de Verwijzing van Kijkers ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html). Bijvoorbeeld, als u over CSS tellers voor de Kijker van het Gezoem wilt lezen, zie [ het Aanpassen van de Kijker van het Gezoem ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/zoom/customizing-zoom/c-html5-20-zoom-viewer-customizingviewer.html).) Het is echter mogelijk, dat de visuele redacteur sommige CSS waarden niet begrijpt. In dergelijke gevallen probeert de visuele editor de fouten te negeren zodat de CSS nog steeds werkt.

   >[!NOTE]
   >
   >Als u de CSS liever rechtstreeks in onbewerkte vorm bewerkt, selecteert u **[!UICONTROL Show/Hide CSS]** onder het keuzemenu Geselecteerde tekst (schuif zo nodig de visuele editor omhoog om deze te zien).
   >Net als de visuele editor kunt u direct zien welk effect het heeft op het viewervoorbeeld wanneer u een eigenschap rechtstreeks in de CSS wijzigt. En, wordt dat zelfde bezit automatisch bijgewerkt tezelfdertijd in de visuele redacteur. Als zodanig kunt u de onbewerkte CSS-editor of de visuele editor gebruiken, of beide door elkaar gebruiken.

   >[!NOTE]
   >
   >Voor knopillustraties kiest u de 2x-afbeelding en uploadt u kunstwerk met hoge resolutie. Wanneer u werkt met interactieve afbeeldingen en schopbare banners, kunt u ook verschillende hotspotknoppen uit de doos selecteren.

1. (Optioneel) Selecteer boven aan de pagina Voorinstelling viewer bewerken **[!UICONTROL Desktop]** , **[!UICONTROL Tablet]** of **[!UICONTROL Phone]** om visuele stijlen op unieke wijze te definiëren voor verschillende apparaat- en schermtypen.
1. Selecteer op de pagina Viewer Preset Editor de tab **[!UICONTROL Behavior]** . U kunt ook elk visueel element in de viewer selecteren om het te selecteren voor configuratie.
Bijvoorbeeld, voor het *type 0&rbrace; VideoPlayer, onder **[!UICONTROL Modifiers]**>**[!UICONTROL Playback]**, kunt u uit één van drie adaptieve bitrate het stromen opties selecteren:*

   * **[!UICONTROL dash]** - Video&#39;s worden alleen als DASH gestreamd. Op Safari/iOS-apparaten moet u echter **[!UICONTROL hls]** als het type selecteren.
   * **[!UICONTROL hls]** - Video&#39;s worden alleen als HLS gestreamd.
   * **[!UICONTROL auto]** - Tips en trucs. Het maken van DASH- en HLS-streams is geoptimaliseerd voor opslag. Daarom raadt Adobe u aan **[!UICONTROL auto]** altijd als afspeeltype te selecteren. Video&#39;s worden als strepen, hls of progressief gestreamd, zoals in het volgende voorbeeld:
      * Als de browser DASH ondersteunt, wordt eerst DASH-streaming gebruikt.
      * Als de browser geen ondersteuning biedt voor DASH, wordt vervolgens HLS-streaming gebruikt.
      * Als de browser DASH of HLS niet ondersteunt, wordt progressief afspelen gebruikt.

1. Selecteer in het vervolgkeuzemenu **[!UICONTROL Selected Type]** een component waarvan u het gedrag wilt wijzigen.

   Veel componenten in de visuele editor hebben een gedetailleerde beschrijving. Deze beschrijvingen worden weergegeven in blauwe vakken wanneer u een component uitbreidt om de bijbehorende parameters weer te geven.

   Sommige viewertypen bevatten componenten waarmee u opdrachten voor het leveren van afbeeldingen in een tekstveld **[!UICONTROL IS Command]** kunt opgeven. Zie de [Referentie van de API voor het leveren van afbeeldingen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-is-home.html) voor een lijst met opdrachten die u kunt gebruiken.

   >[!NOTE]
   >
   >**als u een aanrakingsapparaat, zoals een telefoon of een tablet gebruikt...**
   >
   >
   >Nadat u een waarde in het tekstgebied typt, selecteer elders in het gebruikersinterface om de verandering voor te leggen en het virtuele toetsenbord te sluiten. Als u **[!UICONTROL Enter]** selecteert, vindt er geen actie plaats.

1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina.
1. Publiceer uw nieuwe viewervoorinstelling. U moet de voorinstelling publiceren zodat u de resulterende URL op uw website kunt gebruiken.

   Zie [ het Publiceren Kijker stelt ](#publishing-viewer-presets) vooraf in.

   >[!IMPORTANT]
   >
   >Voor oude video&#39;s die een adaptieve bitrate het stromen profiel gebruiken, blijft URL zoals gebruikelijk spelen — met HLS het stromen — tot u [ de videoactiva ](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) opnieuw verwerkt. Na herverwerking, zal zelfde URL blijven werken maar nu met *zowel* toegelaten stromen DASH als HLS.

### Speciale overwegingen voor het maken van een interactieve viewervoorinstelling {#special-considerations-for-creating-an-interactive-viewer-preset}

**Ongeveer Wijzen van de Vertoning voor beeldduimnagels in het paneel:**

Wanneer u een voorinstelling voor een interactieve videoviewer maakt of bewerkt, kunt u kiezen welke instelling voor de weergavemodus u wilt gebruiken. Deze keuze doet zich voor wanneer u `InteractiveSwatches` selecteert in het **[!UICONTROL Selected Component]** keuzemenu onder de tab **[!UICONTROL Behavior]** . De weergavemodus die u kiest, bepaalt hoe en wanneer miniaturen worden weergegeven terwijl de video wordt afgespeeld. U kunt een `segment`-weergavemodus (standaard) of een `continuous`-weergavemodus kiezen.

<table>
 <tbody>
  <tr>
   <td><strong>Weergavemodus</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>Segment</td>
   <td><p><code>Segment </code>is de standaardweergavemodus voor de voorinstellingen voor de uit-van-box Interactive Video Viewer <code>Shoppable_Video_light</code> en <code>Shoppable_Video_dark</code> en alle voorinstellingen voor de Interactieve Video Viewer die u zelf maakt.</p> <p>Stel dat er in deze modus minder miniaturen zijn toegewezen aan een videosegment dan het aantal zichtbare vlekken in het deelvenster. In dergelijke gevallen, worden de duimnagels van volgende of vorige subsegmenten <i> niet </i> getrokken binnen om het even welke lege vlekken in het paneel te vullen. Met andere woorden, het behoudt de weergave van stalen die aan het specifieke videosegment zijn toegewezen.</p> </td>
  </tr>
  <tr>
   <td>Doorlopend</td>
   <td><p>Op <code>continuous </code> vertoningswijze, veronderstel dat het aantal duimnagels in een segment minder dan het aantal is dat in het paneel zichtbaar is. In dergelijke gevallen bevat de viewer automatisch de weergave van miniaturen van het volgende segment of van het vorige segment, waar de laatste miniatuur wordt weergegeven.</p> <p>De <a href="/help/assets/dynamic-media/interactive-videos.md"> video in dit onderwerp </a> is een voorbeeld van de <code>continuous </code> vertoningswijze.</p> </td>
  </tr>
 </tbody>
</table>

**Ongeveer auto-scrollend gedrag in de Interactieve Video kijker:**

Het gedrag voor automatisch schuiven van miniaturen in de Interactieve videoviewer werkt onafhankelijk van de gekozen weergavemodus.

Wanneer u een voorinstelling voor een interactieve videoviewer maakt of bewerkt, hebt u via het tabblad Gedrag toegang tot Automatisch schuiven. Selecteer op het tabblad Gedrag in de vervolgkeuzelijst **[!UICONTROL Selected Components]** de optie **[!UICONTROL InteractiveSwatches]** . Het selectievakje Automatisch schuiven wordt weergegeven onder het tekstveld IS-opdracht.

Als u **[!UICONTROL Auto Scroll]** uitschakelt (het selectievakje wist) in de viewervoorinstelling, wordt tijdens het afspelen van video door de gebruiker in het deelvenster alleen de eerste miniatuurafbeelding voor de volledige lengte van de video weergegeven. Een gebruiker kan echter desgewenst handmatig door de miniaturen bladeren met de pictogrammen pijl-omhoog en pijl-omlaag.

Wanneer u **[!UICONTROL Auto Scroll]** inschakelt (selecteert) in de viewervoorinstelling, schuiven miniatuurafbeeldingen die aan een videosegment zijn toegewezen tijdens het afspelen van de video naar het begin van een segment. Er zijn echter gevallen waarin bepaalde miniaturen in een segment tweemaal zo lang worden weergegeven als andere miniaturen ervoor of erna. Dit gedrag treedt op omdat het aantal miniaturen in een segment groter is dan het aantal dat zichtbaar is in het deelvenster en dat aantal niet gelijkmatig kan worden verdeeld.

Stel dat u een videosegment van 30 seconden hebt om dit te illustreren. En er zijn in totaal negen miniaturen die gedurende de 30 seconden moeten worden weergegeven. De grootte van de browser is zodanig dat er vier zichtbare miniatuurposities in het weergavevenster aanwezig zijn. Het videotijdsegment van 30 seconden wordt verdeeld in drie subsegmenten. In de volgende tabel wordt de verdeling weergegeven van de miniaturen voor een bepaald tijdsubsegment:

| **Video subsegment** | **Subsegment tijd in seconden** | **Duimnagels die in het paneel** zichtbaar zijn |
|---|---|---|
| 1 | 0-10 | 1, 2, 3, 4 |
| 2 | 10-20 | 4, 5, 6, 7 |
| 3 | 20-30 | 6, 7, 8, 9 |

Het videosubsegment 3 reikt niet verder dan de miniaturen die eraan zijn toegewezen. De miniaturen 4, 6 en 7 zijn twee keer zo lang in het deelvenster zichtbaar als de andere miniaturen.

De logica die de viewer gebruikt voor het aantal miniaturen dat in het deelvenster wordt weergegeven op basis van het aantal beschikbare posities is als volgt:

* Aantal subsegmenten = rond tot volgende subsegment (aantal duimnagels/aantal zichtbare groeven in het duimnagelpaneel, gebaseerd op browser venstergrootte).
Aan de hand van het voorbeeld in de bovenstaande tabel worden 9 miniaturen / 4 sleuven = 2,25; de viewerlogica rondt deze rond in maximaal drie subsegmenten.

* Aantal miniaturen = afgerond tot op de volgende miniatuur (aantal miniaturen / aantal videosubsegmenten).
In het bovenstaande voorbeeld worden 9 miniaturen / 3 videosubsegmenten = 3 miniaturen gebruikt.

* Duur van het subsegment = totale videoduur / aantal videosubsegmenten.
Gebruikend het voorbeeld in de bovenstaande lijst, 30 seconden/3 videosubsegments = 10 secondevertoning van elk videosubsegment.

#### Speciale overwegingen voor het maken van voorinstellingen voor de Carousel Banner-viewer {#special-considerations-for-creating-a-carousel-banner-viewer-preset}

Als u voorinstellingen voor de Carousel Banner-viewer maakt, kunt u de stijl van hotspots als volgt wijzigen:

| | **Beschrijving** | **Acties** |
|---|---|---|
| **[!UICONTROL Hotspot Icon]** | Pictogram wijzigen dat wordt gebruikt voor hotspot | Als u de afbeelding van het hotspot-pictogram wilt wijzigen, selecteert u **[!UICONTROL ImageMapEffect]** op het tabblad **[!UICONTROL Appearance]** in **[!UICONTROL Selected Component]** . Selecteer onder **[!UICONTROL Icon]** de optie **[!UICONTROL Background]** en ga in het veld **[!UICONTROL Image]** naar de gewenste achtergrondafbeelding. |

## Voorinstellingen van viewers activeren of deactiveren {#activating-or-deactivating-viewer-presets}

De Viewer-voorinstellingen die beschikbaar zijn in de gebruikersinterface, zijn afhankelijk van de vraag welke voorinstellingen actief zijn in de modus Auteur. Een viewervoorinstelling is standaard ingeschakeld nadat u deze hebt gemaakt. Als u de voorinstelling uitschakelt, wordt deze niet weergegeven in de modus Auteur. Als de voorinstelling wordt gepubliceerd, wordt deze altijd gepubliceerd, ongeacht of deze wordt in- of uitgeschakeld. Deactiveer vooraf instelt van de kijker als de lijst te werkbaar wordt of u geen kijker wilt vooraf ingesteld beschikbaar wordt gemaakt om te gebruiken.

**om kijkersvoorinstellingen te activeren of te deactiveren:**

1. Selecteer in de linkerbovenhoek van Experience Manager het Experience Manager-logo en selecteer vervolgens in de linkertrack **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]** .
1. Selecteer onder de kolomkop **[!UICONTROL State]** op de voorinstellingspagina van de viewer de schakeloptie om een viewervoorinstelling te activeren of deactiveren.

   De voorinstellingen van de viewer die worden geactiveerd, worden rechts, in een blauw vak weergegeven. De schakeloptie wordt links in een lichtgrijs vak weergegeven wanneer de viewer wordt gedeactiveerd.

## Voorinstellingen voor viewers publiceren {#publishing-viewer-presets}

Als u de status van een viewervoorinstelling activeert (of inschakelt), betekent dit dat deze zichtbaar is in de component Dynamische media, de component Interactieve media en wanneer u een element weergeeft.

Nochtans, om *te leveren* een activa met vooraf ingestelde kijker, moet de kijker vooraf ingesteld eveneens worden gepubliceerd. Alle kijkers moeten worden geactiveerd *en* worden gepubliceerd om URL te verkrijgen of code voor een activa in te bedden. Activeer en publiceer alle voorinstellingen van de viewer buiten de box die bij Dynamische media worden geleverd. Aangepaste viewervoorinstellingen die u maakt en toevoegt, worden automatisch geactiveerd, maar moeten ook worden gepubliceerd.

Zie [ het activeren of Deactiveren van Kijker stelt ](#activating-or-deactivating-viewer-presets) vooraf in.

Zie ook [ Previewing Assets ](/help/assets/dynamic-media/previewing-assets.md).

**om kijkersvoorinstellingen te publiceren:**

1. Selecteer in de linkerbovenhoek van Experience Manager het Experience Manager-logo en selecteer vervolgens in de linkertrack **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]>[!UICONTROL Viewer Presets]** .
1. Selecteer een of meer voorinstellingen voor viewers die u wilt publiceren.
1. Selecteer het pictogram **[!UICONTROL Publish]** op de werkbalk.

## Voorinstellingen van viewers sorteren {#sorting-viewer-presets}

1. Selecteer in de linkerbovenhoek van Experience Manager het Experience Manager-logo en selecteer vervolgens in de linkertrack **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]>[!UICONTROL Viewer Presets]** .
1. Selecteer **[!UICONTROL Preset Title]**, **[!UICONTROL Type]**, **[!UICONTROL Published]** of **[!UICONTROL State]** om te sorteren op die kolomkop. Selecteer bijvoorbeeld **[!UICONTROL Type]** om de typen viewervoorinstellingen in alfabetische of omgekeerde alfabetische volgorde te sorteren.

## Voorinstellingen voor viewers bewerken {#editing-viewer-presets}

Het uitgeven om het even welk *vooraf bepaalde, uit-van-de-doos kijker stelt* vooraf in is geen gesteund scenario. Als u een voorinstelling voor een viewer buiten de box bewerkt, wordt u gevraagd deze op te slaan onder een andere naam.

**om kijkersvoorinstellingen uit te geven:**

1. Selecteer in de linkerbovenhoek van Experience Manager het Experience Manager-logo en selecteer vervolgens in de linkertrack **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Asset]** > **[!UICONTROL Viewer Presets]** .
1. Selecteer een voorinstelling door het vakje links van de titel van de voorinstelling voor de viewer in te schakelen.
1. Selecteer **[!UICONTROL Edit]** op de werkbalk.
1. Breng op de pagina **[!UICONTROL Viewer Preset Editor]** de gewenste wijzigingen aan in de viewervoorinstelling met de opties op de tabbladen **[!UICONTROL Appearance]** en **[!UICONTROL Behavior]** .

   Selecteer op het tabblad **[!UICONTROL Appearance]** in de linkerbovenhoek van de pagina Voorinstellingseditor voor viewers de optie **[!UICONTROL Desktop]** , **[!UICONTROL Tablet]** of **[!UICONTROL Phone]** om de presentatiemodus van het element te wijzigen.

1. Voer in de rechterbovenhoek van de pagina een van de volgende handelingen uit:

   * Selecteer **[!UICONTROL Save]** om uw wijzigingen op te slaan en terug te keren naar de pagina met voorinstellingen voor viewer.
   * Selecteer **[!UICONTROL Cancel]** om eventuele wijzigingen die u hebt aangebracht, te voorkomen en terug te keren naar de pagina met voorinstellingen voor viewer.

## Aangepaste voorinstellingen voor viewers verwijderen {#deleting-custom-viewer-presets}

U kunt Viewer-voorinstellingen verwijderen die u hebt gemaakt en toegevoegd aan dynamische media.

**om vooraf instelt van de douaneviewer te schrappen:**

1. Selecteer in de linkerbovenhoek van Experience Manager het Experience Manager-logo en selecteer vervolgens in de linkertrack **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]>[!UICONTROL Viewer Presets]** .
1. Controleer op de pagina Voorinstellingen viewer een voorinstellingstitel en selecteer het pictogram **[!UICONTROL Trash]** .
1. Selecteer **[!UICONTROL Delete]** .

## Een viewervoorinstelling toepassen op een element {#applying-a-viewer-preset-to-an-asset}

Als u zowel de asset als de geselecteerde viewer al hebt gepubliceerd, worden de knoppen **[!UICONTROL URL]** en **[!UICONTROL Embed]** weergegeven nadat u een viewervoorinstelling hebt geselecteerd.

**om een kijker toe te passen vooraf ingesteld op activa:**

1. Open het element en selecteer vervolgens **[!UICONTROL Viewers]** in de linkerbovenhoek van de pagina.

   >[!NOTE]
   >
   >Als u zowel de asset als de geselecteerde viewer al hebt gepubliceerd, worden de knoppen **[!UICONTROL URL]** en **[!UICONTROL Embed]** weergegeven nadat u een viewervoorinstelling hebt geselecteerd.

1. Selecteer een viewervoorinstelling in het linkerdeelvenster om deze toe te passen op het element.

   U kunt [ URL kopiëren om ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) met andere gebruikers te delen.

## Elementen leveren met viewervoorinstellingen {#delivering-assets-with-viewer-presets}

Om URLs voor Kijker te krijgen stelt vooraf in, zie [ Verbinding URLs aan uw toepassing van het Web ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). Zie ook [ bed de VideoKijker op een Web-pagina ](/help/assets/dynamic-media/embed-code.md) in.

Als u Experience Manager als uw WCM gebruikt, kunt u elementen toevoegen met behulp van de voorinstellingen van de viewer rechtstreeks op de pagina. Zie [ Dynamische Media Assets aan Pagina&#39;s ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md) toevoegen.
