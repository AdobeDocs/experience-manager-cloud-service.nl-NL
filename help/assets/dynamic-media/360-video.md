---
title: 360/VR-video
description: Leer hoe u met 360 en VR-video (Virtual Reality) werkt in Dynamic Media.
contentOwner: Rick Brough
feature: 360 VR Video
role: User
exl-id: ffd092d3-2188-47b0-a475-8bfa660c03c1
source-git-commit: 35caac30887f17077d82f3370f1948e33d7f1530
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---

# 360/VR-video {#vr-video}

In video&#39;s van 360° wordt een weergave in elke richting tegelijkertijd vastgelegd. Ze worden opgenomen met een omnidirectionele camera of een verzameling camera&#39;s. Tijdens het afspelen, op een plat beeldscherm, heeft de gebruiker controle over de kijkhoek; Bij het afspelen op mobiele apparaten worden doorgaans de ingebouwde gyroscopische besturingselementen toegepast.

Dynamic Media biedt native ondersteuning voor de levering van 360 video-elementen. Standaard is geen aanvullende configuratie nodig voor weergave of afspelen. U levert 360 Video gebruikend standaardvideouitbreidingen zoals .mp4, .mkv, en .mov. De meest algemene codec is H.264.

Met de 360/VR-videoviewer kunt u rechthoekige video renderen. Het resultaat is een indrukwekkende kijkervaring van een kamer, eigenschap, locatie, landschap, medische procedure enzovoort.

Ruimtelijke audio wordt momenteel niet ondersteund. als audio in stereo wordt gemengd, verandert de balans (L/R) niet aangezien de klant de kijkhoek van de camera verandert.

Zie [Dynamic Media 360-video&#39;s en aangepaste videominiatuur gebruiken voor AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-360-video-custom-thumbnail-feature-video-use.html#dynamic-media).

Zie ook [Viewer-voorinstellingen beheren](/help/assets/dynamic-media/managing-viewer-presets.md).

## 360 Video in actie {#video-in-action}

Selecteren [Ruimtestation 360](https://s7d1.scene7.com/s7viewers/html5/Video360Viewer.html?asset=Viewers/space_station_360-AVS) om een browservenster te openen en een video van 360° te bekijken. Tijdens het afspelen van video sleept u de aanwijzer naar een nieuwe locatie om de weergavehoek te wijzigen.

![Videoframe van Space Station 360 video](assets/6_5_360videoiss_simplified.png)
*Videoframe vanaf Space Station 360*

## 360/VR-video en Adobe Premiere Pro {#vr-video-and-adobe-premiere-pro}

Met Adobe Premier Pro kunt u 360/VR-beeldmateriaal weergeven en bewerken. U kunt bijvoorbeeld logo&#39;s en tekst op de juiste wijze in een scène plaatsen en effecten en overgangen toepassen die specifiek zijn ontworpen voor rechthoekige media.

Zie [360/VR-video bewerken](https://helpx.adobe.com/premiere-pro/how-to/edit-360-vr-video.html).

## Elementen uploaden voor gebruik met de 360-videoviewer {#uploading-assets-for-use-with-the-video-viewer}

360 video-elementen die worden geüpload naar [!DNL Experience Manager] worden gelabeld als **Multimedia** op een elementpagina, vergelijkbaar met normaal video-element.

![Een geüpload 360-video-element dat in de kaartweergave wordt weergegeven](assets/6_5_360video-selecttopreview.png)
*Een geüpload 360-video element dat in de Kaartweergave wordt weergegeven. Het element wordt aangeduid als Multimedia.*

**Elementen uploaden voor gebruik met de 360 Video-viewer:**

1. Er is een map gemaakt voor uw 360-video-element.
1. [Pas een adaptief videoprofiel toe op de map](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).

   Bij het renderen van 360-video-inhoud worden hogere eisen gesteld aan de resolutie van de bronvideo en aan de resolutie van gecodeerde vertoningen dan aan de standaard niet-360-video-inhoud.

   U kunt het adaptieve videoprofiel gebruiken dat al bij Dynamic Media wordt geleverd. De kwaliteit van 360-video is echter merkbaar lager dan bij niet-360-video die is gecodeerd met dezelfde instellingen die zijn gerenderd met een niet-360-videoviewer. Ga daarom als volgt te werk als u hoogwaardige 360 video nodig hebt:

   * In het ideale geval heeft uw oorspronkelijke 360-video-inhoud een van de volgende resoluties:

      * 1080p - 1920 x 1080, bekend als Full HD- of FHD-resolutie of,
      * 2160p - 3840 x 2160, bekend als 4k, UHD of Ultra HD-resolutie. Deze grote weergaveresolutie wordt meestal aangetroffen op hoogwaardige televisies en computermonitoren. De resolutie van 2160p wordt vaak &#39;4k&#39; genoemd omdat de breedte dichtbij 4000 pixels ligt. Met andere woorden, het biedt vier keer de pixels van 1080p.
   * [Een aangepast adaptief videoprofiel maken](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) met uitvoeringen van hogere kwaliteit. U kunt bijvoorbeeld een adaptief videoprofiel maken dat de volgende drie instellingen bevat:

      * Breedte=automatisch; Hoogte=720; Bitsnelheid=2500 kbps
      * Breedte=automatisch; Height=1080; Bitsnelheid=5000 kbps
      * Breedte=automatisch; Hoogte=1440; Bitsnelheid=6600 kbps
   * Verwerk 360-video-inhoud in een map die exclusief is bestemd voor 360 video-elementen.

   Deze benadering plaatst grotere eisen op het netwerk en cpu van het eind - gebruiker.

1. [Uw video uploaden naar de map](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).

<!--

## Overriding the default aspect ratio of 360 videos  {#overriding-the-default-aspect-ratio-of-videos}

For an uploaded asset to qualify as a 360 video that you intend to use with the 360 Video viewer, the asset must have an aspect ratio of 2.

By default, AEM detects video as "360" if its aspect ratio (width/height) is 2.0. If you are an Administrator, you can override the default aspect ratio setting of 2 by setting the optional `s7video360AR` property in CRXDE Lite at the following:

* `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

  * **Property type**: Double
  * **Value**: floating-point aspect ratio, default 2.0.

After you set this property, it takes effect immediately on both existing videos and newly uploaded videos.

The aspect ratio applies to 360 video assets for the asset details page and the [Video 360 Media WCM component](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#dynamic-media-components).

Start by uploading 360 Videos.

-->

## Voorvertoning 360-video {#previewing-video}

Met Voorvertoning kunt u zien hoe uw 360-video er uitziet voor klanten en kunt u controleren of deze zich gedraagt zoals u had verwacht.

Zie ook [Viewer-voorinstellingen bewerken](/help/assets/dynamic-media/managing-viewer-presets.md#editing-viewer-presets).

Als u tevreden bent met de 360-video, kunt u deze publiceren.

Zie [Video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/dynamic-media/embed-code.md).
Zie [URL&#39;s koppelen aan uw webtoepassing](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met heeft [!DNL Experience Manager Sites] pagina&#39;s.
Zie [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

**Een voorvertoning van 360 video&#39;s weergeven:**

1. In **[!UICONTROL Assets]** navigeer naar een bestaande 360-video die u hebt gemaakt. Selecteer het 360 Video-element om het element te openen in de voorvertoningsmodus.

   ![Screenshot van een geüploade 360 video-asset, zoals deze wordt weergegeven in de Kaartweergave van Experience Manager.](assets/6_5_360video-selecttopreview-1.png)

   Selecteer het 360-video-element om een voorvertoning van de video weer te geven.

1. Selecteer op de voorvertoningspagina, linksboven op de pagina, de vervolgkeuzelijst en selecteer vervolgens **[!UICONTROL Viewers]**.

   ![Screenshot van het selecteren van Viewers om de lijst met beschikbare videoviewers weer te geven.](assets/6_5_360video-preview-viewers.png)

   Selecteer in de lijst Viewers de optie **[!UICONTROL Video360_social]** Voer vervolgens een van de volgende handelingen uit:

   * Als u de kijkhoek van de statische scène wilt wijzigen, sleept u de aanwijzer over de video.
   * Selecteer de video&#39;s om het afspelen te starten **[!UICONTROL Play]** knop. Terwijl de video wordt afgespeeld, sleept u de aanwijzer over de video om de kijkhoek te wijzigen.

   ![Screenshot van een gebruiker die de Video360_Social viewer selecteert om een voorvertoning van een video van 360 graden weer te geven.](assets/6_5_360video-preview-video360-social.png)*Een schermafbeelding van 360 video.*

   * Selecteer in de lijst Viewers de optie **[!UICONTROL Video360VR]**.

      VR-video (Virtual Reality) is overweldigende video-inhoud die wordt benaderd met headsets van virtuele realiteit. Net als bij gewone video&#39;s maakt u aan het begin VR-video&#39;s wanneer een video wordt opgenomen of vastgelegd met videocamera&#39;s van 360°.
   ![Screenshot van een gebruiker die de muisaanwijzer boven de Viewer-optie Video360VR houdt.](assets/6_5_360video-preview-video360vr.png)
   *Een videoschermafbeelding van 360 VR.*

1. Rechtsboven op de voorvertoningspagina selecteert u **[!UICONTROL Close]**.

## 360-video publiceren {#publishing-video}

Als u 360-video wilt gebruiken, moet u deze publiceren. Wanneer u een 360-video publiceert, wordt de URL en de insluitcode geactiveerd. Het publiceert ook de 360 Video aan de wolk van Dynamic Media die met een CDN voor scalable en prestatieslevering geïntegreerd is.

Zie [Dynamic Media-middelen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) voor meer informatie over het publiceren van 360-video.
Zie ook [Video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/dynamic-media/embed-code.md).
Zie ook [URL&#39;s koppelen aan uw webtoepassing](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met heeft [!DNL Experience Manager Sites] pagina&#39;s.
Zie ook [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).
