---
title: Video in Dynamic Media
description: Leer hoe u in Dynamic Media met video kunt werken, zoals tips en trucs voor het coderen van video's, het publiceren van video's naar YouTube, het weergeven van videorapporten en het toevoegen van ondertiteling, ondertitels of hoofdstukmarkeringen aan video's.
contentOwner: Rick Brough
feature: Video Profiles
role: User
exl-id: 0d5fbb3e-b763-415f-8c69-ea36445f882b
source-git-commit: 35caac30887f17077d82f3370f1948e33d7f1530
workflow-type: tm+mt
source-wordcount: '8978'
ht-degree: 3%

---

# Video {#video}

In deze sectie wordt het werken met video in Dynamic Media beschreven.

## Snel starten: Video&#39;s {#quick-start-videos}

De volgende stapsgewijze workflowbeschrijving is ontworpen om u te helpen snel aan de slag te gaan met adaptieve videosets in Dynamic Media. Nadat elke stap verwijzingen naar onderwerprubrieken is waar u meer informatie kunt vinden.

>[!NOTE]
>
>Voordat u in Dynamic Media met video werkt, moet u controleren of uw Adobe Experience Manager-beheerder Dynamic Media-Cloud Services al heeft ingeschakeld en geconfigureerd.
>
>* Zie [Dynamic Media-Cloud Services configureren](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services) in Configureer Dynamic Media en [Problemen met Dynamic Media oplossen](/help/assets/dynamic-media/troubleshoot-dm.md).
>


1. **Dynamic Media-video&#39;s uploaden** door het volgende te doen:

   * Maak uw eigen videocoderingsprofiel. U kunt ook gewoon de vooraf gedefinieerde _Adaptieve videocodering_ profiel dat bij Dynamic Media wordt geleverd.

      * [Een videocoderingsprofiel maken](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming).
      * Meer informatie over [Aanbevolen procedures voor videocodering](#best-practices-for-encoding-videos).
   * Koppel het videoverwerkingsprofiel aan een of meer mappen waar u de primaire bronvideo&#39;s gaat uploaden.

      * [Een videoprofiel toepassen op mappen](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).
      * Meer informatie over [Digitale elementen ordenen](/help/assets/organize-assets.md).
   * Upload uw primaire bronvideo&#39;s naar de mappen. Wanneer u video&#39;s aan de map toevoegt, worden deze gecodeerd volgens het videoverwerkingsprofiel dat u aan de map hebt toegewezen.

      * Dynamic Media ondersteunt voornamelijk korte video&#39;s met een maximale lengte van 30 minuten en een minimale resolutie van meer dan 25 x 25.
      * U kunt videobestanden uploaden van maximaal 15 GB elk.
      * [Uw video&#39;s uploaden](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).
      * Meer informatie over [Ondersteunde bestandsindelingen voor invoer](/help/assets/file-format-support.md).
   * Controleren hoe [videocodering wordt voortgezet](#monitoring-video-encoding-and-youtube-publishing-progress) vanuit het element of de werkstroomweergave.




1. **Uw Dynamic Media-video&#39;s beheren** door een van de volgende handelingen uit te voeren:

   * Video-elementen organiseren, doorbladeren en zoeken

      * [Digitale elementen ordenen](/help/assets/organize-assets.md)
      * [Video-elementen zoeken](/help/assets/search-assets.md#custompredicates) of [Elementen zoeken](/help/assets/manage-digital-assets.md#search-assets)
   * Video-elementen voorvertonen en publiceren

      * Bekijk de bronvideo en de gecodeerde vertoningen van de video samen met de bijbehorende miniaturen:
         [Video&#39;s voorvertonen](/help/assets/manage-video-assets.md#upload-and-preview-video-assets) of [Elementen voorvertonen](/help/assets/dynamic-media/previewing-assets.md)
         [Video-uitvoeringen beheren](/help/assets/manage-digital-assets.md#managing-renditions)

      * [Viewervoorinstellingen beheren](/help/assets/dynamic-media/managing-viewer-presets.md)
      * [Elementen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)
   * Werken met videometagegevens

      * Bewerk de eigenschappen van video, zoals de titel, beschrijving en tags, aangepaste metagegevensvelden:
         [Video-eigenschappen bewerken](/help/assets/manage-digital-assets.md#editing-properties)

      * [Metagegevens voor digitale elementen beheren](/help/assets/manage-metadata.md)
      * [Metagegevensschema&#39;s](/help/assets/metadata-schemas.md)
   * Video&#39;s bekijken, goedkeuren en annoteren en volledige versiebeheer behouden

      * [Video&#39;s annoteren](/help/assets/manage-video-assets.md#annotate-video-assets) of [Annoteren van elementen](/help/assets/manage-digital-assets.md#annotating)

      * [Een versie maken](/help/assets/manage-digital-assets.md#asset-versioning)
      * [Een workflow starten op een element](/help/assets/manage-digital-assets.md#starting-a-workflow-on-an-asset)

      * [Mapmiddelen controleren](/help/assets/bulk-approval.md)
      * [Projecten](/help/sites-cloud/authoring/projects/overview.md)




1. **Dynamic Media-video&#39;s publiceren** door een van de volgende handelingen uit te voeren:

   * Als u Experience Manager gebruikt als uw WCM-systeem (Web Content Management), kunt u video&#39;s rechtstreeks toevoegen aan uw webpagina&#39;s.

      * [Video&#39;s toevoegen aan uw webpagina&#39;s](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).
   * Als u een systeem voor webcontentbeheer van derden gebruikt, kunt u video&#39;s koppelen aan of insluiten in uw webpagina&#39;s.

      * Video integreren met URL:
         [URL&#39;s koppelen aan uw webtoepassing](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md).

      * Video integreren met gebruik van ingesloten code op webpagina:
         [De videoviewer insluiten op een webpagina](/help/assets/dynamic-media/embed-code.md).
   * [Video&#39;s publiceren naar YouTube](#publishing-videos-to-youtube).
   * [Videorapporten genereren](#viewing-video-reports).

   * [Bijschriften toevoegen aan video](#adding-captions-to-video).



## Werken met video in Dynamic Media {#working-with-video-in-dynamic-media}

Video in Dynamic Media is een end-to-end oplossing waarmee u eenvoudig Adaptieve video van hoge kwaliteit kunt publiceren voor streaming op meerdere schermen, waaronder desktops, tablets en mobiele apparaten. Een adaptieve videoreeks groepeert versies van de zelfde video die bij verschillende beetjetarieven en formaten zoals 400 kbps, 800 kbps, en 1000 kbps worden gecodeerd. De desktopcomputer of het mobiele apparaat detecteert de beschikbare bandbreedte.

Op een mobiel iOS-apparaat wordt bijvoorbeeld een bandbreedte gedetecteerd, zoals 3G, 4G of Wi-Fi. Vervolgens wordt automatisch de naar rechts gecodeerde video geselecteerd bij de verschillende bitsnelheden van de video in de adaptieve videoset. De video wordt gestreamd naar desktops, mobiele apparaten of tablets.

Bovendien wordt de videokwaliteit automatisch dynamisch geschakeld als de netwerkomstandigheden veranderen op het bureaublad of op het mobiele apparaat. Als een klant de modus Volledig scherm op een desktopcomputer inschakelt, reageert de Adaptive Video Set met een betere resolutie, waardoor de kijkervaring van de klant wordt verbeterd. Met Adaptieve videosets kunt u Dynamic Media-video op meerdere schermen en apparaten het best afspelen.

De logica die een videospeler gebruikt om te bepalen welke gecodeerde video moet worden afgespeeld of tijdens het afspelen moet worden geselecteerd, is gebaseerd op het volgende algoritme:

1. Videospeler laadt het eerste videofragment op basis van de bitsnelheid die het dichtst bij de waarde ligt die is ingesteld voor de beginbitsnelheid in de speler zelf.
1. De videospelerschakelaars die op veranderingen in de bandbreedtesnelheid worden gebaseerd die de volgende criteria gebruiken:

   1. De speler kiest de hoogste bandbreedtestroom onder of gelijk aan de geschatte bandbreedte.
   1. De speler overweegt slechts 80% van de beschikbare bandbreedte. Als er echter een overstap wordt gemaakt, is het conservatiever bij slechts 70% om overschatting te voorkomen en onmiddellijk terug te keren.

Voor gedetailleerde technische informatie over het algoritme, zie [https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

Voor het beheren van afzonderlijke video- en adaptieve videosets wordt het volgende ondersteund:

* Video uploaden van diverse ondersteunde video-indelingen en audio-indelingen en video coderen naar MP4 H.264-indeling, zodat deze op meerdere schermen kan worden afgespeeld. U kunt vooraf gedefinieerde adaptieve videovoorinstellingen gebruiken, voorinstellingen voor één videocodering gebruiken of uw eigen codering aanpassen om de kwaliteit en de grootte van de video te bepalen.

   * Wanneer een adaptieve videoset wordt gegenereerd, bevat deze MP4-video&#39;s.
   * **Opmerking**: Primaire video&#39;s en bronvideo&#39;s worden niet toegevoegd aan een adaptieve videoset.

* ondertiteling in alle HTML5-videoviewers.
* Video organiseren, doorbladeren en doorzoeken met volledige metagegevensondersteuning voor een efficiënt beheer van video-elementen.
* Lever Adaptieve videosets naar het web en desktops, tablets en mobiele apparaten.

Adaptieve videostreaming wordt ondersteund op verschillende iOS-platforms. Zie [Dynamic Media Viewers Reference Guide](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-reference.html).

<!-- OUTDATED 2/28/22 BASED ON CQDOC-18692 Dynamic Media supports mobile video playback for MP4 H.264 video. You can find BlackBerry&reg; devices that support this video format at the following: [Supported video formats on BlackBerry&reg;](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

OUTDATED 2/28/22 BASED ON CQDOC-18692 You can find Windows&reg; devices that support this video format at the following [Supported video formats on Windows&reg; Phone](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/supported-codecs). -->

* Speel de video terug gebruikend de Voorinstellingen van de VideoKijker van Dynamic Media, met inbegrip van het volgende:

   * Afzonderlijke videoviewers.
   * Gemengde Media-viewers die zowel video- als afbeeldingsinhoud combineren.

* Configureer videospelers om aan uw brandingbehoeften te voldoen.
* Video met een eenvoudige URL of insluitcode integreren in uw website, mobiele site of mobiele toepassing.

Zie [Dynamische videoweergave](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&amp;config=GeoRetail/Universal_Video1&amp;stageSize=640,480) monster nemen.

Zie ook [Viewers voor Experience Manager Assets en Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers.html#viewers-aem-assets-dmc) en [Alleen viewers voor Experience Manager Assets](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html#viewers-for-aem-assets-only) in de [Dynamic Media Viewers Reference Guide](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html).

## Beste praktijken: De HTML5-videoviewer gebruiken {#best-practice-using-the-html-video-viewer}

De Dynamic Media HTML5 Video viewer-voorinstellingen zijn robuuste videospelers. U kunt ze gebruiken om veel voorkomende problemen te voorkomen die te maken hebben met het afspelen van HTML5-video en met problemen die te maken hebben met mobiele apparaten. Bijvoorbeeld een gebrek aan adaptieve streaminglevering en een beperkt bereik van de desktopbrowser.

Aan de ontwerpkant van de speler, kunt u de functionaliteit van de videospeler ontwerpen gebruikend standaardWeb ontwikkelingshulpmiddelen. U kunt bijvoorbeeld de knoppen, besturingselementen en de achtergrond van een aangepaste posterafbeelding ontwerpen met behulp van HTML5 en CSS om u te helpen uw klanten te bereiken met een aangepaste weergave.

Aan de afspeelzijde van de viewer wordt automatisch de videocapaciteit van de browser gedetecteerd. Vervolgens wordt de video afgespeeld met behulp van HLS (HTTP Live Streaming), ook wel adaptieve videostreaming genoemd. Of als deze leveringsmethoden niet aanwezig zijn, wordt in plaats daarvan HTML5 progressief gebruikt.

U kunt de mogelijkheid om de afspeelcomponenten te ontwerpen met behulp van HTML5 en CSS combineren tot één speler. Het kan het afspelen ingesloten hebben en adaptief en progressief streamen gebruiken, afhankelijk van de mogelijkheden van de browser. Met al deze functionaliteit kunt u het bereik van uw uitgebreide media-inhoud uitbreiden voor zowel gebruikers op het bureaublad als mobiele apparaten en een gestroomlijnde videobeleving garanderen.

Zie ook [Alleen viewers voor Experience Manager Assets](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html#viewers-for-aem-assets-only) in de [Dynamic Media Viewers Reference Guide](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html).

### Video afspelen op bureaubladcomputers en mobiele apparaten met de HTML5-videoviewer {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

Voor adaptieve videostreaming op het bureaublad en mobiele apparaten zijn de video&#39;s die worden gebruikt voor het schakelen naar een andere bitsnelheid, gebaseerd op alle MP4-video&#39;s in de adaptieve videoset.

Het afspelen van video vindt plaats met behulp van HLS of progressieve videodownload. In eerdere versies van Experience Manager, zoals 6.0, 6.1 en 6.2, werden video&#39;s gestreamd via HTTP.

In Experience Manager 6.3 en hoger worden video&#39;s nu gestreamd via HTTPS (dat wil zeggen, HLS), omdat de URL van de DM-gatewayservice altijd HTTPS gebruikt. Dit standaardgedrag heeft geen gevolgen voor de klant. Videostreaming vindt altijd plaats via HTTPS, tenzij dit niet door de browser wordt ondersteund. (zie de volgende tabel). Op grond daarvan wordt met

* Als u een HTTPS-website met HTTPS-videostreaming hebt, is streaming prima.
* Als u een HTTP-website met HTTPS-videostreaming hebt, is streaming prima en zijn er geen problemen met gemengde inhoud in de webbrowser.

HLS is een Apple-standaard voor adaptieve videostreaming die het afspelen automatisch aanpast op basis van de capaciteit van de netwerkbandbreedte. Het laat de klant ook &quot;zoeken&quot;aan om het even welk punt in de video zonder de behoefte om op de rest van de video te wachten te downloaden.

Progressieve video wordt geleverd door de video lokaal te downloaden en op het desktopsysteem of mobiele apparaat van de gebruiker op te slaan.

In de volgende tabel worden het apparaat, de browser en de afspeelmethode beschreven van video&#39;s op bureaubladcomputers en mobiele apparaten met de opdracht [Dynamic Media HTML5 Video Viewer](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video.html#interactive-video).

<table>
 <tbody>
  <tr>
   <td><strong>Apparaat</strong></td>
   <td><strong>Browser</strong></td>
   <td><strong>Video-afspeelmodus</strong></td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Internet Explorer 9 en 10</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Internet Explorer 11+</td>
   <td>In Windows® 8 en Windows® 10 - Gebruik HTTPS geforceerd wanneer om HLS wordt gevraagd. Bekende beperking: HTTP op HLS werkt niet in deze browser/werkend systeemcombinatie<br /> <br /> Windows® 7 - Progressief downloaden. Gebruikt de standaardlogica voor het selecteren van het protocol HTTP versus HTTPS.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Firefox 23-44</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Firefox 45 of hoger</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Chroom</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Safari (Mac)</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Chrome (Android™ 6 of eerder)</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Chrome (Android™ 7 of hoger)</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Android™ (standaardbrowser)</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Safari (iOS)</td>
   <td>HLS</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Chrome (iOS)</td>
   <td>HLS</td>
  </tr>
 </tbody>
</table>

<!--  THIS LINE WAS REMOVED FROM THE TABLE ABOVE ON FEB 28, 2022 BASED ON CQDOC 18692 -RSB <tr>
   <td>Mobile</td>
   <td>BlackBerry&reg;</td>
   <td>HLS</td>
  </tr>
 -->

## Architectuur van Dynamic Media-videooplossing {#architecture-of-dynamic-media-video-solution}

In de volgende afbeelding ziet u de algemene ontwerpworkflow voor video&#39;s die via DMGateway (in de Dynamic Media Hybrid-modus) worden geüpload en gecodeerd en die voor openbare consumptie beschikbaar worden gesteld.

![chlimage_1-427](assets/chlimage_1-427.png)

## Hybride publicatiearchitectuur voor video&#39;s {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## Aanbevolen werkwijzen voor het coderen van video&#39;s {#best-practices-for-encoding-videos}

De **Dynamic Media-video coderen** als u Dynamic Media hebt ingeschakeld en video-Cloud Services hebt ingesteld, codeert de workflow video. In deze workflow worden de historie en informatie over fouten van het workflowproces vastgelegd. Zie [Video-codering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress). Als u Dynamic Media hebt ingeschakeld en video-Cloud Services hebt ingesteld, kunt u **[!UICONTROL Dynamic Media Encode Video]** de workflow wordt automatisch van kracht wanneer u een video uploadt. (Als u Dynamic Media niet gebruikt, wordt **[!UICONTROL DAM Update Asset]** workflow wordt van kracht.)

Hier volgt een overzicht van tips voor het coderen van bronvideobestanden.

<!-- For advice about video encoding, see the following:

* [Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution](https://www.adobe.com/go/learn_s7_streaming101_en).
* [Video Encoding Basics](https://www.adobe.com/go/learn_s7_encoding_en). -->

### Bronvideobestanden {#source-video-files}

Wanneer u een videobestand codeert, gebruikt u een videobronbestand van de hoogst mogelijke kwaliteit. Gebruik geen eerder gecodeerde videobestanden omdat deze bestanden al zijn gecomprimeerd en als u verder codeert, wordt een video van subparkwaliteit gemaakt.

* Dynamic Media ondersteunt voornamelijk korte video&#39;s met een maximale lengte van 30 minuten en een minimale resolutie van meer dan 25 x 25.
* U kunt primaire bronvideobestanden uploaden die elk maximaal 15 GB bedragen.

In de volgende tabel worden de aanbevolen grootte, hoogte-breedteverhouding en minimale bitsnelheid beschreven die uw bronvideobestanden moeten hebben voordat u ze codeert:

| Grootte | Hoogte-breedteverhouding | Minimale bitsnelheid |
|--- |--- |--- |
| 1024 x 768 | 4:3 | 4500 kbps voor de meeste video&#39;s. |
| 1280 x 720 | 16:9 | 3000 - 6000 kbps, afhankelijk van de hoeveelheid beweging in de video. |
| 1920 x 1080 | 16:9 | 6000 - 8000 kbps, afhankelijk van de mate van beweging in de video. |

### De metagegevens van een bestand verkrijgen {#obtaining-a-file-s-metadata}

U kunt de metagegevens van een bestand verkrijgen door de metagegevens van het bestand te bekijken met een programma voor videobewerking of met een toepassing die is ontworpen voor het verkrijgen van metagegevens. Hieronder vindt u instructies voor het gebruik van MediaInfo, een toepassing van derden, voor het verkrijgen van de metagegevens van een videobestand:

1. Ga naar [MediaInfo downloaden](https://mediaarea.net/en/MediaInfo/Download).
1. Selecteer en download het installatieprogramma voor de GUI-versie en volg de installatie-instructies.
1. Klik na de installatie met de rechtermuisknop op het videobestand (alleen Windows®) en selecteer MediaInfo, of open MediaInfo en sleep het videobestand naar de toepassing. U ziet alle metagegevens die aan het videobestand zijn gekoppeld, inclusief de breedte, hoogte en fps.

### Hoogte-breedteverhouding {#aspect-ratio}

Wanneer u een voorinstelling voor videocodering kiest of maakt voor uw primaire bronvideobestand, moet u ervoor zorgen dat de voorinstelling dezelfde hoogte-breedteverhouding heeft als het primaire bronvideobestand. De hoogte-breedteverhouding is de verhouding tussen de breedte en de hoogte van de video.

Als u de hoogte-breedteverhouding van een videobestand wilt bepalen, vraagt u de metagegevens van het bestand op en noteert u de breedte en hoogte van het bestand (zie De metagegevens van een bestand hierboven verkrijgen). Gebruik vervolgens deze formule om de hoogte-breedteverhouding te bepalen:

width/height = hoogte-breedteverhouding

In de volgende tabel wordt beschreven hoe de resultaten van de formule worden omgezet in algemene opties voor de hoogte-breedteverhouding:

| Resultaat van formule | Hoogte-breedteverhouding |
|--- |--- |
| 1.33 | 4:3 |
| 0.75 | 3:4 |
| 1.78 | 16:9 |
| 0.56 | 9:16 |

Een video van 1440 x 1080 hoogte heeft bijvoorbeeld een hoogte-breedteverhouding van 1440/1080 of 1,33. In dit geval kiest u een voorinstelling voor videocodering met een hoogte-breedteverhouding van 4:3 om het videobestand te coderen.

### Bitsnelheid {#bitrate}

Bitsnelheid is de hoeveelheid gegevens die wordt gecodeerd om één seconde video af te spelen. De bitsnelheid wordt gemeten in kilobits per seconde (Kbps).

>[!NOTE]
>
>Omdat in alle codecs compressie met verlies wordt gebruikt, is bitsnelheid de belangrijkste factor voor de videokwaliteit. Bij compressie met verlies neemt de kwaliteit af naarmate u een videobestand comprimeert. Daarom zijn alle andere eigenschappen gelijk (de resolutie, framesnelheid en codec), hoe lager de bitsnelheid, hoe lager de kwaliteit van het gecomprimeerde bestand.

Wanneer u een codering voor bitsnelheden selecteert, kunt u kiezen uit twee typen:

* **[!UICONTROL Constant Bitrate Encoding]** (CBR) - Tijdens CBR-codering blijft de bitsnelheid of het aantal bits per seconde tijdens het coderingsproces ongewijzigd. Bij CBR-codering blijft de gegevenssnelheid van de set behouden voor de instelling van de gehele video. Bij CBR-codering worden mediabestanden niet geoptimaliseerd voor kwaliteit, maar wordt opslagruimte bespaard.
Gebruik CBR als uw video een vergelijkbaar bewegingsniveau in de gehele video bevat. CBR wordt meestal gebruikt voor het streamen van video-inhoud. Zie ook [Parameters voor aangepaste videocodering gebruiken](/help/assets/dynamic-media/video-profiles.md#using-custom-added-video-encoding-parameters).

* **[!UICONTROL Variable Bitrate Encoding]** (VBR) - VBR-codering past de gegevenssnelheid naar beneden en naar de bovenste limiet die u instelt, aan op basis van de gegevens die de compressor nodig heeft. Deze functionaliteit houdt in dat de bitsnelheid van het mediabestand tijdens een VBR-coderingsproces dynamisch wordt verhoogd of verlaagd, afhankelijk van de behoeften aan bitsnelheid van mediabestanden.
VBR duurt langer om te coderen maar produceert de gunstigste resultaten; de kwaliteit van het mediabestand is superieur. VBR wordt het meest meestal gebruikt voor http progressieve levering van video-inhoud.

Wanneer gebruikt u VBR versus CRB?
Als u VBR en CBR selecteert, wordt het bijna altijd aanbevolen VBR te gebruiken voor uw mediabestanden. VBR biedt bestanden van hogere kwaliteit tegen concurrerende bitsnelheden. Wanneer u VBR gebruikt, moet u ervoor zorgen dat u met codering met twee controles gebruikt en de maximale bitsnelheid instellen op 1,5x de bitsnelheid van de doelvideo.

Wanneer u een voorinstelling voor videocodering kiest, moet u rekening houden met de verbindingssnelheid van de eindgebruiker van het doel. Kies een voorinstelling met een gegevenssnelheid van 80 procent van die snelheid. Als de verbindingssnelheid van de eindgebruiker van het doel bijvoorbeeld 1000 Kbps is, is de beste voorinstelling een snelheid met een videogegevenssnelheid van 800 Kbps.

In deze tabel wordt de gegevenssnelheid beschreven van standaardverbindingssnelheden.

| Snelheid (Kbps) | Verbindingstype |
|--- |--- |
| 256 | Inbelverbinding. |
| 800 | Normale mobiele verbinding. Kies hiervoor een gegevenssnelheid tussen 400 en maximaal 800 voor 3G-ervaringen. |
| 2000 | Standaardbreedbandverbinding voor desktops. Voor deze verbinding, richt een gegevenstarief in de waaier 800-2000 Kbps, met de meeste doelstellingen gemiddeld 1200-1500 Kbps. |
| 5000 | Typische breedbandverbinding. Codering in dit bovenste bereik wordt niet aanbevolen, omdat de video bij deze snelheid niet beschikbaar is voor de meeste consumenten. |

### Resolutie {#resolution}

**Resolutie** Hiermee worden de hoogte en breedte van een videobestand in pixels beschreven. De meeste bronvideo wordt opgeslagen met een hoge resolutie (bijvoorbeeld 1920 x 1080). Voor streamingdoeleinden wordt bronvideo gecomprimeerd tot een lagere resolutie (640 x 480 of lager).

Resolutie en gegevenssnelheid zijn twee geïntegreerde gekoppelde factoren die de videokwaliteit bepalen. Als u dezelfde videokwaliteit wilt behouden, geldt dat hoe hoger het aantal pixels in een videobestand (hoe hoger de resolutie), hoe hoger de gegevenssnelheid. Neem bijvoorbeeld het aantal pixels per frame in een videobestand met een resolutie van 320 x 240 en een resolutie van 640 x 480:

| Resolutie | Pixels per frame |
|--- |--- |
| 320 x 240 | 76,800 |
| 640 x 480 | 307,200 |

Het bestand van 640 x 480 heeft vier keer zoveel pixels per frame. Als u voor deze twee voorbeeldresoluties dezelfde gegevenssnelheid wilt bereiken, past u viermaal de compressie toe op het bestand van 640 x 480, waardoor de kwaliteit van de video kan afnemen. Daarom levert een videogegevenssnelheid van 250 Kbps beelden van hoge kwaliteit bij een resolutie van 320 x 240, maar niet bij een resolutie van 640 x 480.

Over het algemeen geldt dat hoe hoger de gegevenssnelheid, hoe beter de video wordt weergegeven en hoe hoger de resolutie die u gebruikt, hoe hoger de gegevenssnelheid waarmee u de weergavekwaliteit wilt behouden (in vergelijking met lagere resoluties).

Omdat de resolutie en de gegevenssnelheid zijn gekoppeld, hebt u twee opties bij het coderen van video:

* Kies een gegevenssnelheid en codeer vervolgens met de hoogste resolutie die bij de gekozen gegevenssnelheid goed lijkt.
* Kies een resolutie en codeer met de gegevenssnelheid die nodig is voor video van hoge kwaliteit met de gekozen resolutie.

Wanneer u een voorinstelling voor videocodering kiest (of maakt) voor uw primaire bronvideobestand, gebruikt u deze tabel om de juiste resolutie in te stellen:

| Resolutie | Hoogte (pixels) | Schermgrootte |
|--- |--- |--- |
| 240p | 240 | Glanzend scherm |
| 300p | 300 | Klein scherm, meestal voor mobiele apparaten |
| 360p | 360 | Klein scherm |
| 480p | 480 | Standaardscherm |
| 720p | 720 | Groot scherm |
| 1080p | 1080 | High-definition groot scherm |

### FPS (frames per seconde) {#fps-frames-per-second}

In de Verenigde Staten en Japan wordt de meeste video opgenomen met een snelheid van 29,97 frames per seconde (fps); in Europa wordt de meeste video opgenomen met 25 fps. Film wordt opgenomen bij 24 fps.

Kies een voorinstelling voor videocodering die overeenkomt met de fps-snelheid van het primaire bronvideobestand. Als uw primaire bronvideo bijvoorbeeld 25 fps is, kiest u een coderingsvoorinstelling met 25 fps. Standaard wordt bij alle aangepaste codering de fps van het primaire bronvideobestand gebruikt. Daarom hoeft u de fps-instelling niet expliciet op te geven wanneer u een voorinstelling voor videocodering maakt.

### Afmetingen videocodering {#video-encoding-dimensions}

Voor optimale resultaten selecteert u de coderingsafmetingen, zodat de bronvideo een volledig veelvoud van alle gecodeerde video&#39;s is.

Als u deze verhouding wilt berekenen, deelt u de bronbreedte door de gecodeerde breedte om de breedteverhouding op te halen. Vervolgens deelt u de bronhoogte door de gecodeerde hoogte om de hoogte-breedteverhouding te bepalen.

Als de resulterende verhouding een geheel geheel getal is, betekent dit dat de video optimaal wordt geschaald. Als de resulterende verhouding geen geheel geheel getal is, is dit van invloed op de videokwaliteit doordat pixelartefacten overblijven op het scherm. Dit effect is vooral opvallend wanneer de video tekst heeft.

Stel dat uw bronvideo bijvoorbeeld 1920 x 1080 is. In de volgende tabel bieden de drie gecodeerde video&#39;s de optimale coderingsinstellingen.

| Videotype | Breedte x hoogte | Breedteverhouding | Hoogteverhouding |
|--- |--- |--- |--- |
| Bron | 1920 x 1080 | 1 | 1 |
| Gecodeerd | 960 x 540 | 2 | 2 |
| Gecodeerd | 640 x 360 | 3 | 3 |
| Gecodeerd | 480 x 270 | 4 | 4 |

### Gecodeerde videobestandsindeling {#encoded-video-file-format}

Dynamic Media raadt u aan voorinstellingen voor MP4 H.264-videocodering te gebruiken. Omdat MP4-bestanden de H.264-videocodec gebruiken, biedt deze video van hoge kwaliteit, maar met een gecomprimeerde bestandsgrootte.

## Video&#39;s publiceren naar YouTube {#publishing-videos-to-youtube}

U kunt video-elementen die in Experience Manager Assets worden beheerd, rechtstreeks publiceren naar een YouTube-kanaal dat u eerder hebt gemaakt.

Als u video-elementen naar YouTube wilt publiceren, kunt u tags toewijzen aan video-elementen in Experience Manager Assets. U koppelt deze tags aan een YouTube-kanaal. Als de tag van een video-element overeenkomt met de tag van een YouTube-kanaal, wordt de video gepubliceerd naar YouTube. Publiceren naar YouTube vindt plaats samen met een normale publicatie van de video zolang een bijbehorende tag wordt gebruikt.

YouTube voert zijn eigen codering uit. Als zodanig wordt het oorspronkelijke videobestand dat naar de Experience Manager is geüpload, gepubliceerd naar YouTube in plaats van een video-uitvoering die door Dynamic Media is gemaakt. Hoewel het niet nodig is om video&#39;s te verwerken met Dynamic Media, wordt verwacht dat dit gebeurt voor het geval dat een viewer-voorinstelling nodig is voor het afspelen.

Wanneer u het videoverwerkingsprofiel overslaat en rechtstreeks naar YouTube publiceert, betekent dit gewoon dat uw video-element in Experience Manager Asset geen zichtbare miniatuur krijgt. Het betekent ook dat video&#39;s die niet zijn gecodeerd, niet werken met Dynamic Media-middelen.

Bij het publiceren van video-elementen naar YouTube-servers moeten de volgende taken worden uitgevoerd om een veilige en veilige server-naar-server verificatie met YouTube te garanderen:

1. [Google Cloud-instellingen configureren](#configuring-google-cloud-settings)
1. [Een YouTube-kanaal maken](#creating-a-youtube-channel)
1. [Codes toevoegen voor publicatie](#adding-tags-for-publishing)
1. [YouTube instellen in Experience Manager](#setting-up-youtube-in-aem)
1. [(Optioneel) Automatiseer de standaardeigenschappen van YouTube voor uw geüploade video&#39;s](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [Video&#39;s publiceren naar uw YouTube-kanaal](#publishing-videos-to-your-youtube-channel)
1. [(Optioneel) Controleer de gepubliceerde video op YouTube](/help/assets/dynamic-media/video.md#optional-verifying-the-published-video-on-youtube)
1. [YouTube-URL&#39;s koppelen aan uw webtoepassing](#linking-youtube-urls-to-your-web-application)

U kunt ook [Publiceren van video&#39;s ongedaan maken om deze uit YouTube te verwijderen](#unpublishing-videos-to-remove-them-from-youtube).

### Google Cloud-instellingen configureren {#configuring-google-cloud-settings}

Als u wilt publiceren naar YouTube, hebt u een Google-account nodig. Als u een GMAIL-account hebt, hebt u al een Google-account. als u geen Google-account hebt, kunt u er eenvoudig een maken. U hebt het account nodig omdat u aanmeldingsgegevens nodig hebt om video-elementen naar YouTube te publiceren. <!-- hidden March 3 2022 If you have an account already created, then skip this task and proceed directly to [Create a YouTube channel](#creating-a-youtube-channel). -->

Het account dat wordt gebruikt met Google Cloud en het Google-account dat wordt gebruikt voor YouTube, hoeft niet hetzelfde te zijn.

Google wijzigt regelmatig de gebruikersinterface. De stappen voor het publiceren van video&#39;s naar YouTube kunnen dan ook enigszins afwijken van wat hieronder wordt beschreven. Dit voorbehoud geldt ook voor YouTube wanneer u probeert te controleren of er video&#39;s naar worden geüpload.

>[!NOTE]
>
>De volgende stappen waren correct op het moment van schrijven. Google werkt echter regelmatig hun cloudwebpagina&#39;s bij zonder dat dit wordt gemeld. Daarom kunnen sommige configuratieopties in de Google-gebruikersinterface iets anders worden genoemd dan de naam die in de stappen wordt gebruikt.

**Google Cloud-instellingen configureren:**

1. Maak een Google-account.
   [https://accounts.google.com/signup/v2?service=mail&amp;flowName=GlifWebSignIn&amp;flowEntry=SignUp](https://accounts.google.com/signup/v2?service=mail&amp;flowName=GlifWebSignIn&amp;flowEntry=SignUp)

   Als u al een Google-account hebt, kunt u de volgende stap overslaan.

1. Ga naar [https://cloud.google.com/](https://cloud.google.com/).
1. Op de **[!UICONTROL Google Cloud]** pagina, bij de rechterbovenhoek, selecteert u **[!UICONTROL Console]**.

   Indien nodig **[!UICONTROL Sign in]** met uw Google-accountgegevens de **[!UICONTROL Console]** optie.

1. Op de **[!UICONTROL Dashboard]** pagina, rechts van **[!UICONTROL Google Cloud Platform]**, selecteert u de **[!UICONTROL Project]** vervolgkeuzelijst om de **[!UICONTROL Select a project]** in.
1. In de **[!UICONTROL Select a project]** dialoogvenster selecteert u **[!UICONTROL New Project]**.
1. In de **[!UICONTROL New Project]** in het dialoogvenster **[!UICONTROL Project name]** veld, typt u de naam van het nieuwe project.

   Uw project-id is gebaseerd op uw projectnaam. Kies daarom de projectnaam zorgvuldig; het kan na het creëren niet worden veranderd. U moet dezelfde project-id opnieuw invoeren wanneer u YouTube later instelt in Experience Manager. Schrijf het daarom op.

1. Selecteer **[!UICONTROL Create]**.

1. Voer een van de volgende handelingen uit:

   * Op het dashboard van uw project, in **[!UICONTROL Getting Started]** kaart, selecteren **[!UICONTROL Explore and enable APIs]**.
   * Op het dashboard van uw project, in **[!UICONTROL APIs]** kaart, selecteren **[!UICONTROL Go to APIs overview]**.

1. In het midden boven **[!UICONTROL APIs & Services]** pagina, selecteert u **[!UICONTROL ENABLE APIS AND SERVICES]**.<!-- NEXT STEP BELOW IS STEP 10 -->
1. Op de **[!UICONTROL API Library]** pagina, links, onder **[!UICONTROL Category]**, selecteert u **[!UICONTROL YouTube]**. Selecteer rechts van de pagina de optie **[!UICONTROL YouTube]**.
1. Op de **[!UICONTROL YouTube]** pagina, selecteert u **[!UICONTROL YouTube Data API v3]**.
1. Op de **[!UICONTROL YouTube Data API v3]** pagina, selecteert u **[!UICONTROL MANAGE]**.

   ![6_5_googleaccount-apis-manage](assets/6_5_googleaccount-apis-manage.png)

1. U hebt referenties nodig om de API te gebruiken. Indien nodig, aan de linkerkant van de **[!UICONTROL APIs & Services]** pagina, selecteert u **[!UICONTROL Credentials]**.
1. Op de **[!UICONTROL Credentials]** pagina, bij de bovenkant, selecteer **[!UICONTROL CREATE CREDENTIALS]** selecteert u vervolgens **[!UICONTROL OAuth client ID]**.
1. Op de **[!UICONTROL Create OAuth client ID]** pagina, in de **[!UICONTROL Application type]** vervolgkeuzelijst, selecteert u **[!UICONTROL Web application]**.

   ![6_5_googleaccount-apis-applicationtype](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-applicationtype.png)

1. Voer een van de volgende handelingen uit:

   * In de **[!UICONTROL Name]** Voer een unieke naam in voor uw OAuth 2.0-client.
   * Gebruik de standaardnaam die Google al heeft opgegeven in het dialoogvenster **[!UICONTROL Name]** veld.

1. Onder de **[!UICONTROL Authorized JavaScript origins]** kop, selecteren **[!UICONTROL ADD URI]**.

   ![6_5_googleaccount-apis-nameAuthorizations](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-nameauthorizations.png)

1. In de **[!UICONTROL URIs]** tekstveld, voer het volgende pad in en vervang uw eigen domein- en poortnummer in het pad. Druk vervolgens op **[!UICONTROL Enter]** om het pad aan de lijst toe te voegen:

   `https://<servername.domain>:<port_number>`

   Bijvoorbeeld, `https://1a2b3c.mycompany.com:4321`

   >[!NOTE]
   >
   >Het bovenstaande URI-padvoorbeeld is hypothetisch en alleen ter uitleg.

1. Onder de **[!UICONTROL Authorized redirect URIs]** Selecteer URI TOEVOEGEN.
1. In de **[!UICONTROL URIs]** tekstveld, voer het volgende pad in en vervang uw eigen domein- en poortnummer in het pad. Druk vervolgens op **[!UICONTROL Enter]** om het pad aan de lijst toe te voegen:

   `https://<servername.domain>:<port_number>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   Bijvoorbeeld, `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   >[!NOTE]
   >
   >Het bovenstaande URI-padvoorbeeld is hypothetisch en alleen ter uitleg.

1. Onder aan de **[!UICONTROL Create OAuth client ID]** pagina, selecteert u **[!UICONTROL Create]**.
1. Op de **[!UICONTROL OAuth client created]** voert u de volgende handelingen uit:

   * (Optioneel) Kopieer de waarden in het dialoogvenster **[!UICONTROL Your Client ID]** en **[!UICONTROL Your Client Secret]** en opslaan.
   * Selecteren **[!UICONTROL DOWNLOAD JSON]** en sla het JSON-bestand op.

   U hebt dit gedownloade JSON-bestand nodig wanneer u YouTube later instelt in Adobe Experience Manager.

   ![6_5_googleaccount-apis-oauthclientcreated](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-oauthclientcreated.png)

1. Op de **[!UICONTROL OAuth client created]** dialoogvenster selecteert u **[!UICONTROL OK]**.
1. Log uit op je Google account. Maak nu een YouTube-kanaal.

### Een YouTube-kanaal maken {#creating-a-youtube-channel}

Voor het publiceren van video&#39;s naar YouTube hebt u een of meer kanalen nodig. Als u al een YouTube-kanaal hebt gemaakt, kunt u deze taak overslaan en naar [Codes toevoegen voor publicatie](/help/assets/dynamic-media/video.md#adding-tags-for-publishing).

>[!CAUTION]
>
>Zorg ervoor dat u al een of meer kanalen hebt ingesteld in YouTube *voor* u voegt kanalen toe onder YouTube Settings in Experience Manager (zie [YouTube instellen in Experience Manager](#setting-up-youtube-in-aem) hieronder). Als u de kanaalinstelling niet kunt uitvoeren, wordt u niet gewaarschuwd dat er geen bestaande kanalen zijn. Google-verificatie vindt echter nog steeds plaats wanneer u een kanaal toevoegt, maar er is geen optie om te kiezen welk kanaal de video wordt verzonden.

**Een YouTube-kanaal maken:**

1. Ga naar [https://www.youtube.com](https://www.youtube.com/) en meld u aan met uw aanmeldingsgegevens van uw Google-account.
1. Selecteer in de rechterbovenhoek van de YouTube-pagina uw profielafbeelding (deze kan ook als een letter binnen een effen gekleurde cirkel worden weergegeven) en selecteer vervolgens **[!UICONTROL YouTube settings]** (rondtandwielpictogram).
1. Selecteer op de pagina Overzicht onder de kop Extra functies de optie **[!UICONTROL See all my channels or create a channel]**.
1. Selecteer op de pagina Kanalen de optie **[!UICONTROL Create a new channel]**.
1. Voer op de pagina Brand Account in het veld Brand Account Name een bedrijfsnaam of een andere kanaalnaam in die u kiest waar u de video-elementen wilt publiceren en selecteer vervolgens **[!UICONTROL Create]**.

   Herinner de naam die u hier ingaat; moet u het opnieuw invoeren wanneer u YouTube in Experience Manager moet instellen.

1. (Optioneel) Voeg desgewenst meer kanalen toe.

   Nu voegt u labels toe voor publicatie.

### Codes toevoegen voor publicatie {#adding-tags-for-publishing}

Als u video&#39;s naar YouTube wilt publiceren, koppelt de Experience Manager de tags aan een of meer YouTube-kanalen. Als u tags wilt toevoegen voor publicatie, raadpleegt u [Tags beheren](/help/sites-cloud/authoring/features/tags.md).

Of als u de standaardlabels in de Experience Manager wilt gebruiken, kunt u deze taak overslaan en naar [YouTube instellen in Experience Manager](#setting-up-youtube-in-aem).

>[!NOTE]
>
>Nadat de Cloud Service wordt gevormd, wordt andere configuratie niet vereist om YouTube toe te laten publiceer replicatieagent op dit punt. De reden is omdat het werd toegelaten toen de configuratie van de Cloud Service werd bewaard.

<!-- ### Enabling the YouTube Publish replication agent {#enabling-the-youtube-publish-replication-agent}

After you enable the YouTube Publish replication agent, if you want to test the connection to the Google Cloud account, select **[!UICONTROL Test Connection]**. A browser tab displays the connection results. If you have added YouTube Channels, then a listing of those is displayed as part of the test.

1. In the upper-left corner of Experience Manager, select the Experience Manager logo, then in the left rail, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on Author]**.
1. On the Agents of Author page, select **[!UICONTROL YouTube Publish (youtube)]**.
1. On the toolbar, to the right of Settings, select **[!UICONTROL Edit]**.
1. Select the **[!UICONTROL Enabled]** checkbox to turn on the replication agent.
1. Select **[!UICONTROL OK]**. -->

### YouTube instellen in Experience Manager {#setting-up-youtube-in-aem}

Vanaf Experience Manager 6.4 is een nieuwe aanraakgebruikersinterfacemethode geïntroduceerd om YouTube-publicaties in Experience Manager in te stellen. Op basis van de geïnstalleerde Experience Manager die u gebruikt, voert u een van de volgende handelingen uit:

* Om YouTube in Experience Manager vóór 6.4 te vormen, zie [YouTube instellen in Experience Manager vóór 6.4](/help/assets/dynamic-media/video.md#setting-up-youtube-in-aem-before).
* Om YouTube in Experience Manager 6.4 of later te vormen, zie [YouTube instellen in Experience Manager 6.4 en hoger](#setting-up-youtube-in-aem-and-later).

#### YouTube instellen in Experience Manager 6.4 en hoger {#setting-up-youtube-in-aem-and-later}

1. Meld u als beheerder aan bij uw exemplaar van Dynamic Media.
1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en navigeer vervolgens in de linkerspoorstaaf naar **[!UICONTROL Tools]**(hamerpictogram) > **[!UICONTROL Cloud Services]** > **[!UICONTROL YouTube Publishing Configuration]**.
1. Selecteren **[!UICONTROL global]** (niet selecteren).

1. Selecteer in de rechterbovenhoek van de algemene pagina de optie **[!UICONTROL Create]**.
1. Voer op de pagina YouTube-configuratie maken onder Google Cloud-platforminstellingen in het veld **[!UICONTROL Application Name]** de Google-project-id in.

   U hebt de project-id opgegeven toen u de Google Cloud-instellingen voor het eerst eerder hebt geconfigureerd.
Laat de pagina YouTube-configuratie maken open. daar kom je zo op terug .

   ![6_5_youtubepublish-createyoutubeconfiguration](assets/6_5_youtubepublish-createyoutubeconfiguration.png)

1. Open met een teksteditor zonder opmaak het JSON-bestand dat u eerder in de taak hebt gedownload en opgeslagen [Google Cloud-instellingen configureren](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings).
1. Selecteer en kopieer de volledige JSON-tekst.
1. Ga terug naar het dialoogvenster YouTube-accountinstellingen. Plak de JSON-tekst in het veld **[!UICONTROL JSON Config]**.
1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Save]**.

   Stel nu YouTube-kanalen in Experience Manager in.

1. Selecteer **[!UICONTROL Add Channel]**.
1. Voer in het veld Kanaalnaam de naam in van het kanaal dat u in de taak hebt gemaakt **[!UICONTROL Adding one or more channels to YouTube]** eerder.

   U kunt desgewenst een beschrijving toevoegen.

1. Selecteer **[!UICONTROL Add]**.
1. YouTube/Google-verificatie wordt weergegeven. Als u zich nog niet hebt aangemeld bij het Google Cloud-account, slaat u deze stap over.

   * Voer de Google-gebruikersnaam en het wachtwoord in die aan de Google Project ID en de JSON-tekst hierboven zijn gekoppeld.
   * Afhankelijk van hoeveel kanalen uw account twee of meer items bevat. Selecteer een kanaal. Selecteer het e-mailadres niet. het is geen kanaal .
   * Selecteer op de volgende pagina de optie **[!UICONTROL Accept]** om toegang tot dit kanaal toe te staan.

1. Selecteer **[!UICONTROL Allow]**.

   Stel nu labels in voor publicatie.

1. **[!UICONTROL Setting up tags for publishing]** - Selecteer op de pagina Cloud Services > YouTube het potloodpictogram om de lijst met tags die u wilt gebruiken te bewerken.
1. Als u de lijst met beschikbare labels in de Experience Manager wilt weergeven, selecteert u het vervolgkeuzelijstpictogram (ondersteboven ingedrukt caret).
1. Selecteer een of meer tags om deze toe te voegen.

   Als u een toegevoegde tag wilt verwijderen, selecteert u de tag en selecteert u **[!UICONTROL X]**.

1. Wanneer u de gewenste tags hebt toegevoegd, selecteert u **[!UICONTROL Save]**.

   Nu publiceert u video&#39;s naar uw YouTube-kanaal.

#### YouTube instellen in Experience Manager vóór 6.4 {#setting-up-youtube-in-aem-before}

1. Meld u als beheerder aan bij uw exemplaar van Dynamic Media.

1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en navigeer vervolgens in de linkerspoorstaaf naar **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]**.
1. Selecteer onder YouTube onder de kop Services van derden de optie **[!UICONTROL Configure now]**.
1. Voer in het dialoogvenster Configuratie maken een titel (verplicht) en een naam (optioneel) in de desbetreffende velden in.
1. Selecteer **[!UICONTROL Create]**.
1. Voer in het veld **[!UICONTROL Application Name]** in het dialoogvenster YouTube-accountinstellingen de Google-project-id in.

   U hebt de project-id opgegeven toen u het eerst [geconfigureerde Google Cloud-instellingen](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings) eerder.
Laat het dialoogvenster YouTube-accountinstellingen open. daar kom je zo op terug .

1. Open met een teksteditor zonder opmaak het JSON-bestand dat u eerder hebt gedownload en opgeslagen in de taak Google Cloud-instellingen configureren.
1. Selecteer en kopieer de volledige JSON-tekst.
1. Ga terug naar het dialoogvenster YouTube-accountinstellingen. Plak de JSON-tekst in het veld **[!UICONTROL JSON Config]**.
1. Selecteer **[!UICONTROL OK]**.

   Stel nu YouTube-kanalen in Experience Manager in.

1. Aan het recht van **[!UICONTROL Available Channels]**, selecteert u **+** (plusteken).
1. Voer in het veld Titel in het dialoogvenster YouTube-kanaalinstellingen de naam in van het kanaal dat u eerder in de taak **[!UICONTROL Adding one or more channels to YouTube]** hebt gemaakt.

   U kunt desgewenst een beschrijving toevoegen.

1. Selecteer **[!UICONTROL OK]**.
1. YouTube/Google-verificatie wordt weergegeven. Als u zich nog niet hebt aangemeld bij het Google Cloud-account, slaat u deze stap over.

   * Voer de Google-gebruikersnaam en het wachtwoord in die aan de Google Project ID en de JSON-tekst hierboven zijn gekoppeld.
   * Afhankelijk van hoeveel kanalen uw account twee of meer items bevat. Selecteer een kanaal. Selecteer het e-mailadres niet. het is geen kanaal .
   * Selecteer op de volgende pagina de optie **[!UICONTROL Accept]** om toegang tot dit kanaal toe te staan.

1. Selecteer **[!UICONTROL Allow]**.

   Stel nu labels in voor publicatie.

1. **[!UICONTROL Setting up tags for publishing]** - Selecteer op de pagina Cloud Services > YouTube het potloodpictogram om de lijst met tags die u wilt gebruiken te bewerken.
1. Als u de lijst met beschikbare labels in de Experience Manager wilt weergeven, selecteert u het vervolgkeuzelijstpictogram (ondersteboven ingedrukt caret).
1. Selecteer een of meer tags om deze toe te voegen.

   Als u een toegevoegde tag wilt verwijderen, selecteert u de tag en selecteert u **X**.

1. Wanneer u de gewenste tags hebt toegevoegd, selecteert u **[!UICONTROL OK]**.

   Nu publiceert u video&#39;s naar uw YouTube-kanaal.

### (Optioneel) Automatiseer de standaardeigenschappen van YouTube voor uw geüploade video&#39;s {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

U kunt desgewenst de instelling van YouTube-eigenschappen automatiseren bij het uploaden van uw video&#39;s. Maak een verwerkingsprofiel voor metagegevens in Experience Manager.

Als u het verwerkingsprofiel voor metadata wilt maken, kopieert u eerst waarden uit de velden **[!UICONTROL Field Label]**, **[!UICONTROL Map to property]** en **[!UICONTROL Choices]** die te vinden zijn in de metadataschema&#39;s voor video. Vervolgens kunt u het verwerkingsprofiel voor YouTube-videometagegevens samenstellen door deze waarden eraan toe te voegen.

**U kunt als volgt de standaardeigenschappen van YouTube voor uw geüploade video&#39;s automatiseren:**

1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en navigeer vervolgens in de linkerspoorstaaf naar **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.
1. Selecteer **[!UICONTROL default]**. (Voeg geen vinkje toe aan het selectievak links van &quot;standaard&quot;.)
1. Op de **[!UICONTROL default]** pagina, schakel het selectievakje links van **[!UICONTROL video]** selecteert u vervolgens **[!UICONTROL Edit]**.
1. Selecteer op de pagina Metadata Schema Editor de optie **[!UICONTROL Advanced]** tab.
1. Selecteer onder YouTube Publishing (Publiceren in) de optie **[!UICONTROL YouTube Category]**.
1. Aan de rechterkant van de pagina, onder de **[!UICONTROL Settings]** doet u het volgende:

   * In de **[!UICONTROL Map to property]** tekstveld, selecteer en kopieer de waarde.
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

   * Onder **[!UICONTROL Choices]**selecteert en kopieert u de standaardwaarde die u wilt gebruiken (zoals Personen en blogs of Wetenschap en Technologie).
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

1. Selecteer onder YouTube Publishing (Publiceren in) de optie **[!UICONTROL YouTube Privacy]**.
1. Aan de rechterkant van de pagina, onder de **[!UICONTROL Settings]** doet u het volgende:

   * In de **[!UICONTROL Map to property]** tekstveld, selecteer en kopieer de waarde.
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

   * Onder **[!UICONTROL Choices]**selecteert en kopieert u de standaardwaarde die u wilt gebruiken. De keuzen zijn gegroepeerd in twee. Het onderste veld in het paar is de standaardwaarde die u wilt kopiëren, bijvoorbeeld public, unlist of private.
Plak de gekopieerde waarde in de geopende teksteditor. Deze waarde hebt u later nodig wanneer u uw verwerkingsprofiel voor metagegevens maakt. Laat de teksteditor geopend.

1. Selecteer in de rechterbovenhoek van de pagina Metadata Schema Editor de optie **[!UICONTROL Cancel]**.
1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en selecteer vervolgens in de linkerspoorstaaf de optie **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]**.

1. Selecteer in de rechterbovenhoek van de pagina Metagegevensprofielen de optie **[!UICONTROL Create]**.
1. In het dialoogvenster Metagegevensprofiel toevoegen vindt u in het dialoogvenster **[!UICONTROL Profile title]** tekstveld, voer de naam in `YouTube Video` Selecteer vervolgens **[!UICONTROL Create]**.
1. Selecteer op de pagina Metadata Profile Editor de optie **[!UICONTROL Advance]** tab.
1. Voeg de gekopieerde YouTube Publishing-waarden als volgt toe aan het profiel:

   * Selecteer rechts van de pagina de optie **[!UICONTROL Build Form]** tab.
   * (Optioneel) Sleep de component met het label **[!UICONTROL Section Header]** naar links en neer in het formuliergebied.
   * (Optioneel) Selecteer **[!UICONTROL Field Label]** om de component te selecteren.
   * (Optioneel) Typ rechts van de pagina onder het tabblad Instellingen in het tekstveld Veld Label de tekst `YouTube Publishing`.
   * Selecteer **[!UICONTROL Build Form]** en sleep de component met het label **[!UICONTROL Multi Value Text]** en laat het onder de **[!UICONTROL YouTube Publishing]** koptekst die u hebt gemaakt.

   * Als u de component wilt selecteren, selecteert u **[!UICONTROL Field Label]**.
   * Plak rechts van de pagina, onder het tabblad Instellingen, de YouTube Publishing-waarden (Field Label value en Map to property value) die u eerder hebt gekopieerd, in hun respectievelijke velden op het formulier. Plak de waarde Keuzen in het veld Standaardwaarde.

1. Voeg de gekopieerde YouTube-privacywaarden als volgt toe aan het profiel:

   * Selecteer rechts van de pagina de optie **[!UICONTROL Build Form]** tab.
   * (Optioneel) Sleep de component met het label **[!UICONTROL Section Header]** naar links en neer in het formuliergebied.
   * (Optioneel) Selecteer **[!UICONTROL Field Label]** om de component te selecteren.
   * (Optioneel) Typ rechts van de pagina onder het tabblad Instellingen in het tekstveld Veld Label de tekst `YouTube Privacy`.
   * Selecteer **[!UICONTROL Build Form]** en sleep de component met het label **[!UICONTROL Multi Value Text]** en laat het onder de **[!UICONTROL YouTube Privacy]** door u gemaakte koptekst.

   * Als u de component wilt selecteren, selecteert u **[!UICONTROL Field Label]**.
   * Plak rechts van de pagina, onder het tabblad Instellingen, de YouTube Publishing-waarden (Field Label value en Map to property value) die u eerder hebt gekopieerd, in hun respectievelijke velden op het formulier. Plak de waarde Keuzen in het veld Standaardwaarde.

1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Save]**.
1. Pas het metagegevensprofiel voor YouTube Publishing toe op de mappen waarin u video&#39;s gaat uploaden. U moet zowel het profiel Metagegevens als het videoprofiel hebben ingesteld.

   Zie [Metadataprofielen](/help/assets/metadata-profiles.md) en [Videoprofielen](/help/assets/dynamic-media/video-profiles.md).

### Video&#39;s publiceren naar uw YouTube-kanaal {#publishing-videos-to-your-youtube-channel}

Nu associeert u de markeringen die u eerder aan videoactiva toevoegde. Dit proces stelt de Experience Manager in kennis van de elementen die naar uw YouTube-kanaal moeten worden gepubliceerd.

>[!NOTE]
>
>Publiceren wordt niet automatisch naar YouTube gepubliceerd. Wanneer Dynamische media is ingesteld, zijn er twee publicatieopties waaruit u kunt kiezen: **[!UICONTROL Immediately]** of **[!UICONTROL Upon Activation]**.
>
>**[!UICONTROL Publish Immediately]** betekent dat het geüploade element-nadat het met IPS-wordt gesynchroniseerd automatisch aan het leveringssysteem wordt gepubliceerd. Dat geldt voor Dynamic Media, maar dat geldt niet voor YouTube. Als u wilt publiceren naar YouTube, moet u publiceren als Experience Manager Auteur.

>[!NOTE]
Voor het publiceren van inhoud vanuit YouTube gebruikt Experience Manager de optie **[!UICONTROL Publish to YouTube]** werkstroom, waarmee u de voortgang kunt controleren en eventuele foutgegevens kunt bekijken.
Zie [Video-codering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress).
Voor gedetailleerdere voortgangsgegevens kunt u het YouTube-logboek onder replicatie controleren. Houd er echter rekening mee dat voor dergelijke bewaking beheerderstoegang vereist is.

**Video&#39;s publiceren naar uw YouTube-kanaal:**

1. Navigeer in Experience Manager naar een video-element dat u naar het YouTube-kanaal wilt publiceren.
1. Selecteer het video-element (de adaptieve videoset).
1. Selecteer op de werkbalk de optie **[!UICONTROL Properties]**.
1. Selecteer op het tabblad Standaard onder de kop Metagegevens de optie **[!UICONTROL Open Selection Dialog]** rechts van het veld Tags.
1. Navigeer op de pagina Codes selecteren naar de gewenste codes en selecteer een of meer codes.

   Vergeet niet dat de tags moeten worden gekoppeld aan het YouTube-kanaal.

1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Select]**.
1. Selecteer in de rechterbovenhoek van de eigenschappenpagina van de video de optie **[!UICONTROL Save and Close]**.
1. Selecteer op de werkbalk de optie **[!UICONTROL Quick Publish]**.

   Zie ook [Publicatiebeheer gebruiken met Experience Manager Sites](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/publication-management-feature-video-use.html#page-authoring).

   U kunt desgewenst de gepubliceerde video op uw YouTube-kanaal verifiëren.

### (Optioneel) Controleer de gepubliceerde video op YouTube {#optional-verifying-the-published-video-on-youtube}

U kunt optioneel de voortgang van het publiceren van YouTube (of het ongedaan maken van het publiceren) volgen.

Zie [Video-codering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress).

De het publiceren tijden kunnen zeer afhankelijk van talrijke factoren variëren die het formaat van uw primaire bronvideo, dossiergrootte, en uploadverkeer omvatten. Het publicatieproces kan een paar minuten tot enkele uren duren. Bovendien worden indelingen met een hogere resolutie veel langzamer gerenderd. Het duurt bijvoorbeeld langer om 720p en 1080p weer te geven dan 480p.

Na acht uur, als u nog een statusbericht ziet dat **[!UICONTROL Uploaded (processing, please wait)]**, verwijdert u de video van uw site en uploadt u deze opnieuw.

### YouTube-URL&#39;s koppelen aan uw webtoepassing {#linking-youtube-urls-to-your-web-application}

U kunt een YouTube URL-tekenreeks verkrijgen die door Dynamic Media wordt gegenereerd nadat u de video hebt gepubliceerd. Wanneer u de YouTube-URL kopieert, wordt deze op het Klembord gedownload, zodat u deze indien nodig kunt plakken naar pagina&#39;s in uw website of toepassing.

>[!NOTE]
De YouTube-URL kan pas worden gekopieerd nadat u het video-element naar YouTube hebt gepubliceerd.

YouTube-URL&#39;s koppelen aan uw webtoepassing:

1. Ga naar de *YouTube gepubliceerd* video-element waarvan u de URL wilt kopiëren en selecteer het.

   Houd er rekening mee dat YouTube-URL&#39;s alleen beschikbaar zijn om te kopiëren *na* u hebt de eerste *gepubliceerd* de video-elementen naar YouTube.

1. Selecteer op de werkbalk de optie **[!UICONTROL Properties]**.
1. Selecteer **[!UICONTROL Advanced]** tab.
1. Selecteer onder YouTube Publishing in de URL-lijst van YouTube de URL-tekst die u naar uw webbrowser wilt kopiëren om een voorvertoning van het element weer te geven of om deze toe te voegen aan uw pagina met webinhoud.

### Publiceren van video&#39;s ongedaan maken zodat u deze kunt verwijderen uit YouTube {#unpublishing-videos-to-remove-them-from-youtube}

Wanneer u de publicatie van een video-element in Experience Manager ongedaan maakt, wordt de video verwijderd uit YouTube.

>[!CAUTION]
Als u een video rechtstreeks uit YouTube verwijdert, is de Experience Manager zich hiervan niet bewust en gedragen deze zich alsof de video nog steeds naar YouTube wordt gepubliceerd. Publiceer de publicatie van een video-element vanuit YouTube altijd ongedaan als Experience Manager.

>[!NOTE]
Om inhoud uit YouTube te verwijderen, gebruikt de Experience Manager **[!UICONTROL Unpublish from YouTube]** werkstroom, waarmee u de voortgang kunt controleren en eventuele foutgegevens kunt bekijken.
Zie [Video-codering en YouTube-publicatievoortgang controleren](#monitoring-video-encoding-and-youtube-publishing-progress).

**Publiceren van video&#39;s ongedaan maken om deze uit YouTube te verwijderen:**

1. Navigeer naar de video-elementen waarvan u de publicatie via uw YouTube-kanaal wilt ongedaan maken.
1. Selecteer in de modus voor middelenselectie een of meer gepubliceerde video-elementen.
1. Selecteer op de werkbalk de optie **[!UICONTROL Manage Publication]**. Selecteer indien nodig het pictogram met drie puntjes (`. . .`) op de werkbalk om te zien **[!UICONTROL Manage Publication]**.
1. Selecteer op de pagina Publicatie beheren de optie **[!UICONTROL Unpublish]**.
1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Next]**.
1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Unpublish]**.

## Video-codering en YouTube-publicatievoortgang controleren {#monitoring-video-encoding-and-youtube-publishing-progress}

Wanneer u een nieuwe video uploadt naar een map waarop videocodering is toegepast of wanneer u uw video publiceert naar YouTube, controleert u hoe de videocodering/YouTube-publicatie vordert (of mislukt). Werkelijke vorderingen bij het publiceren in YouTube zijn alleen beschikbaar via de logboeken. Maar of het ontbreekt of slaagt, is het vermeld op andere manieren die in de volgende procedure worden beschreven. Bovendien ontvangt u e-mailmeldingen wanneer een publicatieworkflow of videocodering van YouTube is voltooid of onderbroken.

### Voortgang van controle {#monitoring-progress}

U kunt de voortgang controleren, inclusief mislukte codering/YouTube-publicatie.

1. Voortgang videocodering weergeven in map met elementen:

   * In de kaartweergave wordt de voortgang van de videocodering met een percentage weergegeven op het element. Als er een fout optreedt, wordt deze informatie ook weergegeven op het element.

   ![chlimage_1-429](assets/chlimage_1-429.png)

   * In de lijstweergave wordt de voortgang van de videocodering weergegeven in het dialoogvenster **[!UICONTROL Processing Status]** kolom. Als er een fout is, wordt dit bericht in dezelfde kolom weergegeven.

   ![chlimage_1-430](assets/chlimage_1-430.png)

   Deze kolom wordt niet standaard weergegeven. Selecteer **[!UICONTROL View Settings]** in het vervolgkeuzemenu Weergaven en voeg de opdracht **[!UICONTROL Processing Status]** kolom en selecteer **[!UICONTROL Update]**.

   ![chlimage_1-431](/help/assets/dynamic-media/assets/chlimage_1-431.png)

1. De voortgang van de elementen weergeven. Wanneer u een element selecteert, opent u het keuzemenu en selecteert u **[!UICONTROL Timeline]**. Selecteer **[!UICONTROL Workflows]**.

   ![chlimage_1-432](assets/chlimage_1-432.png)

   Workflowinformatie, zoals codering, wordt weergegeven in de tijdlijn. Voor YouTube-publicatie bevat de tijdlijn van de workflow ook de naam van het YouTube-kanaal en de YouTube-video-URL. Bovendien ziet u eventuele foutmeldingen in de tijdlijn van de workflow nadat het publiceren is voltooid.

   >[!NOTE]
   Het kan lang duren voordat foutberichten of foutberichten definitief worden opgenomen omdat er meerdere workflowconfiguraties zijn **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** van [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr), bijvoorbeeld:
   * Configuratie Apache Sling-taakwachtrij
   * Adobe Granite-workflow - Externe verwerking van taken
   * Tijdelijke wachtrij voor Granite Workflow

   U kunt de **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** eigenschappen in deze configuraties.

1. Zie Workflowinstanties beschikbaar via **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Instances]** voor actieve workflows.

   >[!NOTE]
   U hebt beheerdersrechten nodig voor toegang tot de **[!UICONTROL Tools]** -menu.

   ![chlimage_1-433](assets/chlimage_1-433.png)

   Selecteer de instantie en selecteer **[!UICONTROL Open History]**.

   ![chlimage_1-434](/help/assets/dynamic-media/assets/chlimage_1-434.png)

   Vanuit het gebied Workflowinstanties kunt u workflows ook opschorten, beëindigen of hernoemen. Zie [Workflows beheren](/help/sites-cloud/authoring/workflows/overview.md) voor meer informatie .

1. Voor mislukte taken raadpleegt u de beschikbare workflowfouten in **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Failures]**. De lijst **[!UICONTROL Workflow Failure]** bevat alle mislukte workflowactiviteiten.

   >[!NOTE]
   U hebt beheerdersrechten nodig voor toegang tot de **[!UICONTROL Tools]** -menu.

   ![chlimage_1-435](assets/chlimage_1-435.png)

   >[!NOTE]
   Het kan lang duren voordat het foutbericht eindelijk is opgenomen omdat er meerdere workflowconfiguraties zijn **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** van [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr), bijvoorbeeld:
   * Configuratie Apache Sling-taakwachtrij
   * Adobe Granite-workflow - Externe verwerking van taken
   * Tijdelijke wachtrij voor Granite Workflow

   U kunt de **[!UICONTROL retries]**, **[!UICONTROL retry delay]**, en **[!UICONTROL timeout]** eigenschappen in deze configuraties.

1. Zie Workflowarchief in **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Archive]** voor voltooide workflows. In **[!UICONTROL Workflow Archive]** vindt u een lijst met alle voltooide workflowactiviteiten.

   >[!NOTE]
   U hebt beheerdersrechten nodig voor toegang tot de **[!UICONTROL Tools]** -menu.

   ![chlimage_1-436](assets/chlimage_1-436.png)

1. U ontvangt e-mailmeldingen over afgebroken of mislukte workflowtaken. Deze e-mailberichten kunnen door een beheerder worden geconfigureerd. Zie [E-mailmeldingen configureren](#configuring-e-mail-notifications).

<!-- EMAIL NOT AVAILABLE IN SKYLINE

#### Configuring e-mail notifications {#configuring-e-mail-notifications}

>[!NOTE]
>
>You may need administrative rights to access the **[!UICONTROL Tools]** menu.

How you configure notification depends on whether you want notifications for YouTube publishing jobs.

* For encoding jobs, you can access the configuration page for all Experience Manager workflow email notifications at **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** and by searching for **[!UICONTROL Day CQ Workflow Email Notification Service]**. You can select or clear the check boxes for **[!UICONTROL Notify on Abort]** or **[!UICONTROL Notify on Complete]** accordingly.

For YouTube publishing jobs, do the following:

1. In Experience Manager, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. On the Workflow Models page, select **[!UICONTROL Publish to YouTube]**, then select **[!UICONTROL Edit]** on the toolbar.
1. Near the upper-right corner of the Publish to YouTube workflow page, select **[!UICONTROL Edit]**.
1. Hover the mouse pointer on the YouTube Upload component, then select once to display the inline toolbar.

   ![6_5_publishtoyoutubeworkflow](assets/6_5_publishtoyoutubeworkflow.png)

1. On the inline toolbar, select the Configuration icon (wrench). Select the **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-configurationicon](assets/6_5_publishtoyoutubeworkflow-configurationicon.png)

1. In the YouTube Upload Process - Step Properties dialog box, select the **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-arguments-tab](assets/6_5_publishtoyoutubeworkflow-arguments-tab.png)

1. You can select or clear the following check boxes:

    * Publish Start
    * Publish Failure
    * Publish Completion - includes information on channels and URLs

   Clearing a check box means that you will not receive the specified email notification from the YouTube Publish workflow.

   >[!NOTE]
   >
   >These emails are specific to YouTube and are in addition to the generic workflow email notifications. As a result, you may receive two sets of email notification - the generic notification available in the **[!UICONTROL Day CQ Workflow Email Notification Service]** and one specific to YouTube depending on your configuration settings.

1. When you are finished, near the upper-right corner of the dialog box, select the **[!UICONTROL Done]** icon (check mark).
1. On the Publish to YouTube workflow page, near the upper-right corner, select **[!UICONTROL Sync]**.

-->

## Videorapporten weergeven {#viewing-video-reports}

>[!NOTE]
Videorapporten zijn alleen beschikbaar wanneer u de modus Dynamic Media - Hybride uitvoert.

Videorapporten geven verschillende statistische gegevens over een bepaalde periode weer, zodat u kunt controleren of *gepubliceerd* individuele en geaggregeerde video&#39;s worden uitgevoerd zoals u had verwacht. De volgende statistische gegevens worden geaggregeerd voor alle gepubliceerde video&#39;s op uw gehele website:

* Video start
* Voltooiingssnelheid
* Gemiddelde tijd op video
* Totale tijd op video
* Video&#39;s per bezoek

Een tabel met alle *gepubliceerd* de video&#39;s worden ook vermeld, zodat u de bovenste weergegeven video&#39;s op uw website kunt bijhouden op basis van het totale aantal video&#39;s dat wordt gestart.

Wanneer u een videonaam in de lijst selecteert, wordt het rapport voor het vasthouden van het publiek van de video (drop-off) weergegeven in de vorm van een lijndiagram. Het diagram toont het aantal weergaven voor een bepaald tijdstip tijdens het afspelen van video. Wanneer u de video afspeelt, wordt de verticale balk gesynchroniseerd met de tijdindicator in de speler. De vallen in de gegevens van het lijndiagram wijzen op waar uw publiek van oninteresse wegvalt.

Als de video buiten Adobe Experience Manager Dynamic Media is gecodeerd, zijn het diagram voor het vasthouden van het publiek (drop-off) en de gegevens voor het afspeelpercentage in de tabel niet beschikbaar.

>[!NOTE]
Het bijhouden en rapporteren van gegevens is uitsluitend gebaseerd op het gebruik van de eigen videospeler van Dynamic Media en de bijbehorende voorinstelling van de videospeler. U kunt dus geen video&#39;s bijhouden en rapporteren die door andere videospelers worden afgespeeld.

Door gebrek, de eerste keer u VideoRapporten ingaat, toont het rapport videogegevens die bij de eerste van de huidige maand beginnen en met de datum van de huidige maand beëindigen. U kunt het standaarddatumbereik echter overschrijven door uw eigen datumbereik op te geven. De volgende keer dat u Video-rapporten invoert, wordt het opgegeven datumbereik gebruikt.

Voor het correct werken van videorapporten, wordt een identiteitskaart van de Reeks van het Rapport automatisch gecreeerd wanneer de Cloud Services van Dynamic Media wordt gevormd. Tegelijkertijd wordt de rapportsuite-id doorgegeven aan de publicatieserver, zodat deze beschikbaar is voor de functie URL kopiëren wanneer u een voorvertoning van elementen weergeeft. Voor deze functionaliteit is echter vereist dat de publicatieserver al is ingesteld. Als de publicatieserver niet is ingesteld, kunt u toch publiceren om het videoverslag te zien. U moet echter terugkeren naar de Dynamic Media Cloud Configuration en **[!UICONTROL OK]**.

**Videorapporten weergeven:**

1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager en navigeer vervolgens in de linkerspoorstaaf naar **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Video Reports]**.
1. Voer een van de volgende handelingen uit op de pagina Videorapporten:

   * Selecteer in de rechterbovenhoek de optie **[!UICONTROL Refresh Video Report]** pictogram.
U gebruikt verfrissen slechts als de einddatum van het rapport de huidige dag is. Deze eigenschap zorgt ervoor dat u video het volgen ziet die sinds de laatste tijd is voorgekomen u het rapport in werking stelde.

   * Selecteer in de rechterbovenhoek de optie **[!UICONTROL Date Picker]** pictogram.
Geef het begin- en einddatumbereik op waarvoor u videogegevens wilt en selecteer **[!UICONTROL Run Report]**.

   Het groepsvak Bovenste metagegevens identificeert verschillende samengestelde metingen voor alle *gepubliceerd* video&#39;s op uw site.

1. Selecteer in de tabel met de bovenste gepubliceerde video&#39;s een videonaam om de video af te spelen en zie ook het rapport voor het vasthouden van het publiek van de video (drop-off).

<!-- OBSOLETE CONTENT OBSOLETE CONTENT - SDK ONLY AVAILABLE INTERNALLY NOW 
### Viewing video reports based on a video viewer that you created using the Dynamic Media HTML5 Viewer SDK {#viewing-video-reports-based-on-a-video-viewer-that-you-created-using-the-scene-hmtl-viewer-sdk}

If you are using an out-of-box video viewer provided by Dynamic Media, or if you created a custom viewer preset based off of an out-of-box video viewer, then no additional steps are required to view video reports. However, if you have created your own video viewer based off the Dynamic Media HTML5 Viewer SDK, then use the following steps to ensure the your video viewer is sending tracking events to Dynamic Media Video Reports.

Use the Dynamic Media Viewers Reference and the Dynamic Media HTML5 Viewers SDK to create your own video viewers.

See [Dynamic Media Viewers Reference Guide](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/home.html).

Download the Scene7 HTML Viewer SDK from Adobe Developer Connection.

See [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html).

**To view Video Reports based on a video viewer that you created using the Dynamic Media HTML5 Viewer SDK:**

1. Navigate to any published video asset.
1. Near the upper-left corner of the asset's page, from the drop-down list, select **[!UICONTROL Viewers]**.
1. Select any video viewer preset and copy the embed code.
1. In the embed code, find the line with the following:

   `videoViewer.setParam("config2", "<value>");`

   The `config2` parameter enables tracking in HTML5 Viewers. It is also a company-specific preset that contains the configuration information for Video Reporting, and for customer-specific Adobe Analytics configurations.

   The correct value for the config2 parameter is found in both the **[!UICONTROL Embed Code]** and in the copy **[!UICONTROL URL]** function. In the URL from the copy **[!UICONTROL URL]** command, the parameter to look for is `&config2=<value>` . The value is almost always `companypreset`, but in some instances it can also be `companypreset-1`, `companypreset-2`, and so forth.

1. In your custom video viewer code, add AppMeasurementBridge .jsp to the viewer page by doing the following:

    * First, determine if you need the `&preset` parameter.
      If the `config2` parameter is `companypreset`, you do *not *need `&preset=parameter`.
      If `config2` is anything else, set the preset parameter the same as the `config2` parameter. For example, if `config2=companypreset-2`, add `&param2=companypreset-2` to the AppMeasurmentBridge.jsp URL.

    * Then, add the AppMeasurementBridge.jsp script:
      `<script language="javascript" type="text/javascript" src="https://s7d1.scene7.com/s7viewers/AppMeasurementBridge.jsp?company=robindallas&preset=companypreset-2"></script>`

1. Create the TrackingManager component by doing the following:

    * After calling `s7sdk.Utils.init();` create a TrackingManager instance to track events by adding the following:
      `var trackingManager = new s7sdk.TrackingManager();`

    * Connect components to TrackingManager by doing the following:
      In the `s7sdk.Event.SDK_READY` event handler, attach the component you want to track to the TrackingManager.
      For example, if the component is `videoPlayer`, add
      `trackingManager.attach(videoPlayer);`
      to attach the component to the trackingManager. To track multiple viewers on a page, use multiple tracking mangaer components.

    * Create the AppMeasurementBridge object by adding the following:

      ```
      var appMeasurementBridge = new AppMeasurementBridge(); appMeasurementBridge.setVideoPlayer(videoPlayer);
      ```

    * Add the tracking function by adding the following:

      ```
      trackingManager.setCallback(appMeasurementBridge.track,
       appMeasurementBridge);
      ```

   The appMeasurementBridge object has a built-in track function. OBSOLETE However, you can provide your own to support multiple tracking systems or other functionality.

   For more information, see *Using the TrackingManager Component* in the *Scene7 HTML5 Viewer SDK User Guide* available for download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html).
 -->

## Gesloten bijschriften of ondertitels toevoegen aan video {#adding-captions-to-video}

U kunt het bereik van uw video&#39;s uitbreiden naar wereldwijde markten door ondertiteling toe te voegen aan enkele video&#39;s of aan Adaptive Video Sets. Door ondertiteling toe te voegen vermijdt u de noodzaak om de audio te dupliceren, of de behoefte om inheemse sprekers te gebruiken om de audio voor elke verschillende taal opnieuw op te nemen. De video wordt afgespeeld in de taal waarin deze is opgenomen. Er verschijnen ondertitels in vreemde talen, zodat mensen in verschillende talen het audiogedeelte nog steeds kunnen begrijpen.

Ondertiteling met gesloten deuren zorgt ook voor betere toegankelijkheid voor doven of slechthorenden.

>[!NOTE]
De videospeler die u gebruikt moet de vertoning van gesloten titels steunen.

Zie ook [Toegankelijkheid in Dynamic Media](/help/assets/dynamic-media/accessibility-dm.md).

Dynamic Media kan bijschriftbestanden omzetten in de indeling JSON (JavaScript Object Notation). Met deze conversie kunt u de JSON-tekst insluiten in een webpagina als een verborgen, maar volledige transcriptie van de video. Zoekprogramma&#39;s kunnen de inhoud dan verkennen of indexeren, zodat de video&#39;s gemakkelijker te vinden zijn en klanten meer informatie krijgen over de video-inhoud.

Zie [Statische (niet-afbeeldings) inhoud bedienen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents.html#image-serving-api) voor meer informatie over het gebruik van de functie JSON in een URL.

**Bijschriften of ondertitels toevoegen aan video:**

1. U kunt een toepassing of service van derden gebruiken om een ondertitelingsbestand of ondertitelingsbestand voor video te maken.

   Zorg ervoor dat het bestand dat u maakt, voldoet aan de WebVTT-standaard (Web Video Text Tracks). De bestandsnaamextensie voor ondertiteling is .VTT. U kunt meer informatie over de WebVTT ondertitelingsnorm leren.

   Zie [WebVTT: De indeling Webvideoteksttracks](https://w3c.github.io/webvtt/).

   Er zijn zowel gratis als premiumtools en -services die u kunt gebruiken voor het schrijven van bijschriften en ondertitelingsbestanden buiten Dynamic Media. Als u bijvoorbeeld een eenvoudig videobijschriftbestand zonder opmaak wilt maken, kunt u de volgende gratis gereedschappen voor het maken en bewerken van bijschriften gebruiken:

   [WebVTT Caption Maker](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   U bereikt het beste resultaat met het gereedschap in Internet Explorer 9 of hoger, Google Chrome of Safari.

   In het hulpmiddel, in **[!UICONTROL Enter URL of video file]** veld, plak de gekopieerde URL van het videobestand en selecteer vervolgens **[!UICONTROL Load]**. Zie [Een URL ophalen voor een element](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) om de URL naar het videobestand zelf op te halen, die u vervolgens in het deelvenster **[!UICONTROL Enter URL of video file field]**. Internet Explorer, Chrome of Safari kunnen de video vervolgens op een native manier afspelen.

   Volg nu de aanwijzingen op het scherm van de site om het WebVTT-bestand te ontwerpen en op te slaan. Wanneer u klaar bent, kopieert u de inhoud van het bijschriftbestand en plakt u deze in een teksteditor zonder opmaak en slaat u het bestand op met de bestandsnaamextensie VTT.

   >[!NOTE]
   Voor algemene ondersteuning van videoondertitels in meerdere talen vereist de WebVTT-standaard dat u afzonderlijke .vtt-bestanden maakt en dat u voor elke taal die u wilt ondersteunen, een oproep doet.

   Over het algemeen wilt u het VTT-bestand van het bijschrift dezelfde naam geven als het videobestand en dit bestand toevoegen met de landinstelling van de taal, zoals -EN, of -FR of -DE. Hierdoor kunt u het genereren van video-URL&#39;s automatiseren met behulp van uw bestaande systeem voor webcontentbeheer.

1. Upload in Experience Manager uw WebVTT-bijschriftbestand naar DAM.
1. Ga naar de *gepubliceerd* video-element dat u wilt koppelen aan het bijschriftbestand dat u hebt geüpload.

   Houd er rekening mee dat URL&#39;s alleen beschikbaar zijn om te kopiëren *nadat* u de assets eerst hebt *gepubliceerd*.

   Zie [Elementen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

1. Voer een van de volgende handelingen uit:

   * Voor een pop-upviewerervaring voor video selecteert u **[!UICONTROL URL]**. Selecteer in het dialoogvenster URL de URL en kopieer deze naar het Klembord en passeer de URL naar een eenvoudige teksteditor. Voeg de gekopieerde URL van de video toe met de volgende syntaxis:

      `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

      Noteer de `,1` aan het einde van het bijschriftpad. Onmiddellijk na de VTT-bestandsnaamextensie in het pad kunt u optioneel de knop voor een gesloten bijschrift op de videospelerbalk in- of uitschakelen (uitschakelen) door in te stellen op `,1` of `,0`, respectievelijk.

   * Voor een ingesloten videoviewerervaring selecteert u **[!UICONTROL Embed Code]**. Selecteer in het dialoogvenster Code insluiten de insluitcode en kopieer deze naar het klembord. Plak de code vervolgens in een eenvoudige teksteditor. Voeg de gekopieerde insluitcode toe met de volgende syntaxis:

      `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

      Noteer de `,1` aan het einde van het bijschriftpad. Onmiddellijk na de VTT-bestandsnaamextensie in het pad kunt u optioneel de knop voor een gesloten bijschrift op de videospelerbalk in- of uitschakelen (uitschakelen) door in te stellen op `,1` of `,0`, respectievelijk.

## Hoofdstukmarkeringen aan video toevoegen {#adding-chapter-markers-to-video}

U kunt uw lange formuliervideo&#39;s beter weergeven en navigeren door hoofdstukmarkeringen toe te voegen aan enkele video&#39;s of aan Adaptieve videosets. Wanneer een gebruiker de video afspeelt, kunnen deze de hoofdstukmarkeringen op de videotijdlijn selecteren (ook wel de videoscrubber genoemd). Ze kunnen gemakkelijk naar hun interesse gaan of meteen naar nieuwe inhoud, training en demonstraties gaan.

>[!NOTE]
De videospeler die wordt gebruikt moet het gebruik van hoofdstukmarkeringen steunen. Dynamic Media-videospelers ondersteunen wel hoofdstukmarkeringen, maar het gebruik van videospelers van derden is mogelijk niet mogelijk.

<!-- OBSOLETE CONTENT OBSOLETE CONTENT If desired, you can create and brand your own custom video viewer with chapters instead of using a video viewer preset. For instructions on creating your own HTML5 viewer with chapter navigation, in the Adobe Scene7 Viewer SDK for HTML5 guide, reference the heading "Customizing Behavior Using Modifiers" under the classes `s7sdk.video.VideoPlayer` and `s7sdk.video.VideoScrubber`. The Adobe Scene7 Viewer SDK is available as a download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->

U maakt een hoofdstuklijst voor uw video op ongeveer dezelfde manier als u bijschriften maakt. U maakt dus een WebVTT-bestand. Dit bestand moet echter gescheiden zijn van elk WebVTT-bijschriftbestand. U kunt geen titels en hoofdstukken in één dossier combineren WebVTT.

U kunt het volgende voorbeeld als voorbeeld van het formaat gebruiken u gebruikt om een dossier WebVTT met hoofdstuknavigatie tot stand te brengen:

### WebVTT-bestand met navigatie in videohoofdstukken {#webvtt-file-with-video-chapter-navigation}

```xml {.line-numbers}
WEBVTT
Chapter 1
00:00.000 --> 01:04.364
The bicycle store behind it all.
Chapter 2
01:04.364 --> 02:00.944
Creative Cloud.
Chapter 3
02:00.944 --> 03:02.937
Ease of management for a working solution.
Chapter 4
03:02.937 --> 03:35.000
Cost-efficient access to rapidly evolving technology.
```

In het bovenstaande voorbeeld: `Chapter 1` is de cue-id en is optioneel. De actieduur van `00:00:000 --> 01:04:364` geeft de begin- en eindtijd van het hoofdstuk aan, in `00:00:000` gebruiken. De laatste drie cijfers zijn milliseconden en kunnen als volgt worden verlaten `000`, indien gewenst. De titel van het hoofdstuk `The bicycle store behind it all` Dit is de feitelijke beschrijving van de inhoud van het hoofdstuk. De actidentificator, de begintijd en de hoofdstuktitel worden allemaal in een pop-up in de videospeler weergegeven wanneer een gebruiker de muisaanwijzer boven een visueel actiepunt in de tijdlijn plaatst.

Omdat u een HTML5-videoviewer gebruikt, moet u ervoor zorgen dat het hoofdstukbestand dat u maakt, voldoet aan de WebVTT-standaard (Web Video Text Tracks). De bestandsextensie van het hoofdstuk is .VTT. U kunt meer informatie over de WebVTT ondertitelingsnorm leren.

Zie [WebVTT: De indeling Webvideoteksttracks](https://w3c.github.io/webvtt/).

**Hoofdstukmarkeringen aan video toevoegen:**

1. Sla het VTT-bestand op in UTF8-codering, zodat u problemen met tekenuitvoering in de hoofdstuktiteltekst voorkomt.

   Over het algemeen wilt u het hoofdstuk VTT-bestand dezelfde naam geven als het videobestand en het toevoegen met hoofdstukken. Hierdoor kunt u het genereren van video-URL&#39;s automatiseren met behulp van uw bestaande systeem voor webcontentbeheer.
1. Upload in Experience Manager uw WebVTT-hoofdstukbestand.

   Zie [Elementen uploaden](/help/assets/manage-digital-assets.md#uploading-assets).

1. Voer een van de volgende handelingen uit:

   <table>
     <tbody>
      <tr>
       <td>Voor een ervaring met een pop-upvideoviewer</td>
       <td>
       <ol>
       <li>Ga naar de <i>gepubliceerd </i>video-element dat u wilt koppelen aan het hoofdstukbestand dat u hebt geüpload. Houd er rekening mee dat URL's alleen beschikbaar zijn om te kopiëren <i>nadat</i> u de assets eerst hebt <i>gepubliceerd</i>. Zie <a href="/help/assets/dynamic-media/publishing-dynamicmedia-assets.md">Middelen publiceren.</a></li>
       <li>Selecteer in het keuzemenu vervolgens <strong>Viewers</strong>.</li>
       <li>Selecteer in de linkertrack de naam van de voorinstelling voor de videoviewer. Er wordt een voorvertoning van de video geopend op een aparte pagina.</li>
       <li>Selecteer in het linkerspoor, onderaan <strong>URL</strong>.</li>
       <li>Selecteer in het dialoogvenster URL de URL en kopieer deze naar het Klembord. Plak vervolgens de URL in een eenvoudige teksteditor.</li>
       <li>Voeg de gekopieerde URL van de video toe aan de volgende syntaxis, zodat u deze kunt koppelen aan de gekopieerde URL naar het hoofdstukbestand:<br /> <br /> <code>&navigation=<<i>full_copied_URL_path_to_chapter_file</i>.vtt></code><br /> </li>
       </ol> </td>
      </tr>
      <tr>
       <td>Voor een ingesloten videoviewerervaring<br /> </td>
       <td>
       <ol>
       <li>Ga naar de <i>gepubliceerd </i>video-element dat u wilt koppelen aan het hoofdstukbestand dat u hebt geüpload. Houd er rekening mee dat URL's alleen beschikbaar zijn om te kopiëren <i>nadat</i> u de assets eerst hebt <i>gepubliceerd</i>. Zie <a href="/help/assets/dynamic-media/publishing-dynamicmedia-assets.md">Middelen publiceren.</a></li>
       <li>Selecteer in het keuzemenu vervolgens <strong>Viewers</strong>.</li>
       <li>Selecteer in de linkertrack de naam van de voorinstelling voor de videoviewer. Er wordt een voorvertoning van de video geopend op een aparte pagina.</li>
       <li>Selecteer in het linkerspoor, onderaan <strong>Insluiten</strong>.</li>
       <li>Selecteer in het dialoogvenster Code insluiten de gehele code en kopieer deze naar het klembord. Plak de code vervolgens in een eenvoudige teksteditor.</li>
       <li>Voeg de insluitcode van de video toe aan de volgende syntaxis, zodat u deze kunt koppelen aan de gekopieerde URL naar het hoofdstukbestand:<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt>"</code></li>
       </ol> </td>
      </tr>
     </tbody>
   </table>

<!--

## About video thumbnails {#about-video-thumbnails}

A video thumbnail is a reduced-size version of a video frame or an image asset representing the video to the customer. The thumbnail should serve to encourage a customer to select the video.

All videos in Experience Manager must have an associated thumbnail; you cannot delete a thumbnail without replacing it. By default, when you upload a video to Experience Manager, the first frame is used as the thumbnail. However, you can customize the thumbnail for branding purposes or visual search, for example. When you customize a video thumbnail, you can either play the video and pause on the frame you want to use, or you can select an image asset that you have already uploaded and *published* in your digital asset manager.

Note that a custom video thumbnail image that you select from a video is not extracted and saved in the DAM as a separate and distinct asset. However, a custom video thumbnail that you select from an existing image asset is saved to the JCR. The path of the selected asset gets stored under the video asset's node as in the following example path:

`/content/dam/*<folder_name*>/<*video_name*>/jcr:content/manualThumbnail`

The ability to customize a video thumbnail is only available after you have applied a video profile to the folder where the video is located.

### Adding a custom video thumbnail {#adding-a-custom-video-thumbnail}

1. Be sure you have already done the following:

    * Created a folder for your video assets.
    * [Applied a video profile to the folder](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).

    * [Uploaded your videos to the folder](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).

1. Navigate to an uploaded video asset whose thumbnail image you want to change.
1. In asset selection mode either from **[!UICONTROL List View]** or **[!UICONTROL Card View]**, select the video asset.
1. On the toolbar, select the **[!UICONTROL Properties** icon (a circle with an "i" in it).
1. On the video's Properties page, select **[!UICONTROL Change Thumbnail]**.
1. On the Change Thumbnail page, do one of the following:

    * To use a frame from the video as the new thumbnail:

        * On the toolbar, select **[!UICONTROL Select Frame from video]**.
        * Select the Play button, then select the Pause button on the frame you want to capture as the video's new thumbnail.

    * To use an image asset as the new thumbnail:

        * On the toolbar, select **[!UICONTROL Select Thumbnail from Assets]**.
        * Select **[!UICONTROL Select Thumbnail]**.
        * Navigate to a previously uploaded and published image asset you want to use. Note that the asset will automatically be resized to serve as a thumbnail image for the video.
        * Select the image asset, then select **[!UICONTROL Select]**.

1. On the Change Thumbnail page, select **[!UICONTROL Save Change]**.
1. On the video's Properties page, in the upper-right corner, select **[!UICONTROL Save & Close]**.

-->

<!--

## About video thumbnails in Dynamic Media Hybrid mode{#about-video-thumbnails-in-dynamic-media-hybrid-mode}

You can choose from one of ten thumbnail images automatically generated by Dynamic Media to add to your video. The video player displays your selected thumbnail when a video asset is used with the Dynamic Media component in the authoring environment of Experience Manager Sites, Experience Manager Mobile, or Experience Manager Screens. The thumbnail serves as a static picture that best represents the contents of your entire video and further encourages users to select the Play button.

Based on the total time of the video, Dynamic Media captures ten (default) thumbnail images at 1%, 11%, 21%, 31%, 41%, 51%, 61%, 71%, 81%, and 91% into the video. The ten thumbnails persist meaning that if you decide to choose a different thumbnail later on, you do not need to regenerate the series. You preview the ten thumbnail images and then select the one you want to use with your video. If you want to change to default you can use CRXDE Lite to configure the time interval that thumbnail images are generated. For example, if you only wanted to generate a series of four evenly spaced thumbnail images from your video, you can configure the interval time at 24%, 49%, 74%, and 99%.

Ideally, you can add a video thumbnail anytime after you upload your video but before you publish the video on your website.

If you prefer, you can choose to upload a custom thumbnail to represent your video instead of using a thumbnail generated by Dynamic Media. For example, you could create a custom thumbnail image that has the title of your video, an eye-catching opening image, or a very specific image captured from your video. The custom video thumbnail image that you upload should have a maximum resolution of 1280 x 720 pixels (minimum width of 640 pixels) and be no larger than 2MB.

See also [About video thumbnails](/help/assets/dynamic-media/video.md#about-video-thumbnails-in-dynamic-media-scene-mode).

-->

<!--

### Adding a video thumbnail {#adding-a-video-thumbnail}

1. Navigate to an uploaded video asset that you want to add a video thumbnail.
1. In asset selection mode either from the List View or the Card View, select the video asset.
1. On the toolbar, select the **[!UICONTROL View Properties]** icon (a circle with an "i" in it).
1. On the video's Properties page, select **[!UICONTROL Change Thumbnail]**.
1. On the Change Thumbnail page, on the toolbar, select **[!UICONTROL Select Frame]**.

   Dynamic Media generates a series thumbnail images from your video, based on the default time interval or time interval you customized.

1. Preview the generated thumbnail images, then select the one you want to add to your video.
1. Select **[!UICONTROL Save Change]**.

   The video's thumbnail image is updated to use the thumbnail you selected. If you later decide to change the thumbnail image, you can return to the **[!UICONTROL Change Thumbnail]** page and select a new one.

   If you configured new default time intervals, or you uploaded a new video to replace the existing video, you will need to have Dynamic Media regenerate the thumbnails.

   See [Configuring the default time interval that video thumbnails are generated](#configuring-the-default-time-interval-that-video-thumbnails-are-generated).

-->

<!--

#### Configuring the default time interval that video thumbnails are generated {#configuring-the-default-time-interval-that-video-thumbnails-are-generated}

When you configure and save the new default time interval, your change automatically applies only to videos that you upload in the future. It does not automatically apply the new default to videos that you previously uploaded. For existing videos, you must regenerate the thumbnails.

See [Adding a video thumbnail](#adding-a-video-thumbnail).

**To configure the default time interval that video thumbnails are generated,**

1. In Experience Manager, navigate to **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.

1. In the CRXDE Lite page, in the directory panel on the left, navigate t `o etc/dam/imageserver/configuration/jcr:content/settings.`

   if the directory panel is not visible, you may need to select the >> icon to the left of the Home tab.

1. On the lower-right panel, in the Properties tab, double-tap `thumbnailtime`.
1. In the Edit thumbnailtime dialog box, use the text fields to enter interval values as percentages.

    * Select the plus sign (+) icon to add one or more interval value fields. You may need to scroll to the bottom of the dialog box to see the icon.
    * Select the minus sign (-) icon to the right of an interval value field to delete it from the list.
    * Select the up arrow icon and the down arrow icon to reorder the interval values.

1. Select **[!UICONTROL OK]** to return to the Properties tab.
1. Near the upper-left corner of the CRXDE Lite page, select **[!UICONTROL Save All]**, then select the Back Home icon in the upper-left corner to return to Experience Manager.

   See [Adding a video thumbnail](#adding-a-video-thumbnail).

-->

<!--

### Adding a custom video thumbnail {#adding-a-custom-video-thumbnail-1}

These steps apply only to Dynamic Media running in Hybrid mode.

T**o add a custom video thumbnail**,

1. Navigate to an uploaded video asset that you want to add a custom video thumbnail.
1. In asset selection mode either from the List View or the Card View, select the video asset.
1. On the toolbar, select the **[!UICONTROL View Properties]** icon (a circle with an "i" in it).
1. On the video's Properties page, select **[!UICONTROL Change Thumbnail]**.
1. On the Change Thumbnail page, on the toolbar, select **[!UICONTROL Upload New Thumbnail]**.
1. Navigate to a thumbnail image you want to use, select it, then select **[!UICONTROL Open]** to begin uploading the image into Experience Manager. Following the upload, be sure you publish the image.
1. After you have successfully uploaded and published the image, in the Change Thumbnail page, select **[!UICONTROL Save Changes]**.

   The custom thumbnail is added to your video.

-->
