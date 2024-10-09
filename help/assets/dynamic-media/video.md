---
title: Video in Dynamic Media
description: Leer hoe u met video werkt in Dynamic Media. U kunt de beste werkwijzen bekijken voor het coderen van video's, het publiceren van video's naar YouTube, het weergeven van videoverslagen en het toevoegen van ondertitels of hoofdstukmarkeringen aan video's.
contentOwner: Rick Brough
feature: Video Profiles,Best Practices
role: User
exl-id: 0d5fbb3e-b763-415f-8c69-ea36445f882b
source-git-commit: 7a370ee0ab77046d128ae260af2575d50e655254
workflow-type: tm+mt
source-wordcount: '10320'
ht-degree: 0%

---

# Video {#video}

In deze sectie wordt het werken met video in Dynamic Media beschreven.

## Snel starten: Video&#39;s {#quick-start-videos}

De volgende stapsgewijze beschrijving van de workflow is ontworpen om u te helpen snel aan de slag te gaan met Adaptive Video Sets in Dynamic Media. Na elke stap, zijn er verwijzingen naar onderwerprubrieken waar u meer informatie kunt vinden.

>[!NOTE]
>
>Voordat u in Dynamic Media met video werkt, moet u controleren of uw Adobe Experience Manager-beheerder Dynamic Media-Cloud Servicen al heeft ingeschakeld en geconfigureerd.
>
>* Zie [ vormen de Cloud Servicen van Dynamic Media ](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services) in het Vormen Dynamic Media en [ problemen oplossen Dynamic Media ](/help/assets/dynamic-media/troubleshoot-dm.md).
>

1. **upload uw video&#39;s van Dynamic Media** door het volgende te doen:

   * Maak uw eigen videocoderingsprofiel. Of, kunt u het vooraf bepaalde _Aangepaste Video Coderen_ profiel eenvoudig gebruiken dat met Dynamic Media komt.

      * [ creeer een video het coderen profiel ](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming).
      * Leer meer over [ Beste praktijken voor video het coderen ](#best-practices-for-encoding-videos).

   * Koppel het videoverwerkingsprofiel aan een of meer mappen waar u de primaire bronvideo&#39;s gaat uploaden.

      * [ pas een videoprofiel op omslagen ](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders) toe.
      * Leer meer over [ Organiseer digitale activa ](/help/assets/organize-assets.md).

   * Upload uw primaire bronvideo&#39;s naar de toegewezen mappen. Nadat de video&#39;s zijn toegevoegd, worden deze gecodeerd volgens het videoverwerkingsprofiel dat aan de map is toegewezen.

      * Dynamic Media ondersteunt voornamelijk korte video&#39;s met een maximale lengte van 30 minuten en een minimale resolutie van meer dan 25 x 25.
      * U kunt videobestanden uploaden van maximaal 15 GB elk.
      * [ upload uw video&#39;s ](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).
      * Leer meer over [ Ondersteunde formaten van het inputdossier ](/help/assets/file-format-support.md).

   * Monitor hoe [ video het coderen ](#monitoring-video-encoding-and-youtube-publishing-progress) of van de activa of werkschemamening vooruitgaat.

1. **beheer uw video&#39;s van Dynamic Media** door om het even welke volgend te doen:

   * Video-elementen organiseren, doorbladeren en zoeken

      * [Digitale elementen ordenen](/help/assets/organize-assets.md)
      * [ videoactiva van het Onderzoek ](/help/assets/search-assets.md#custompredicates) of [ zoekend activa ](/help/assets/manage-digital-assets.md#search-assets)

   * Video-elementen voorvertonen en publiceren

      * Bekijk de bronvideo en de gecodeerde vertoningen van de video samen met de bijbehorende miniaturen:
        [ de video&#39;s van de Voorproef ](/help/assets/manage-video-assets.md#upload-and-preview-video-assets) of [ activa van de Voorproef ](/help/assets/dynamic-media/previewing-assets.md)
        [ beheer videovertoningen ](/help/assets/manage-digital-assets.md#managing-renditions)

      * [Voorinstellingen voor viewers beheren](/help/assets/dynamic-media/managing-viewer-presets.md)
      * [Elementen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)

   * Werken met videometagegevens

      * Bewerk de eigenschappen van video, zoals de titel, beschrijving en tags, aangepaste metagegevensvelden:
        [ geef videoeigenschappen ](/help/assets/manage-digital-assets.md#editing-properties) uit

      * [Metagegevens voor digitale elementen beheren](/help/assets/manage-metadata.md)
      * [Metagegevensschema&#39;s](/help/assets/metadata-schemas.md)

   * Video&#39;s bekijken, goedkeuren en annoteren en volledige versiebeheer behouden

      * [ Annoteert video&#39;s ](/help/assets/manage-video-assets.md#annotate-video-assets) of [ Annoteren activa ](/help/assets/manage-digital-assets.md#annotating)

      * [Een versie maken](/help/assets/manage-digital-assets.md#asset-versioning)
      * [Een workflow op een element starten](/help/assets/manage-digital-assets.md#starting-a-workflow-on-an-asset)

      * [Mapmiddelen controleren](/help/assets/bulk-approval.md)
      * [Projecten](/help/sites-cloud/authoring/projects/overview.md)

1. **Publish uw video&#39;s van Dynamic Media** door één van het volgende te doen:

   * Als u Experience Manager gebruikt als uw WCM-systeem (Web Content Management), kunt u video&#39;s rechtstreeks toevoegen aan uw webpagina&#39;s.

      * [ voegt video&#39;s aan uw Web-pagina&#39;s ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md) toe.

   * Als u een WCM-systeem van derden gebruikt, kunt u video&#39;s aan uw webpagina&#39;s koppelen of insluiten.

      * Video integreren met URL:
        [ Verbinding URLs aan uw Webtoepassing ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md).

      * Video integreren met behulp van ingesloten code op een webpagina:
        [ bedt de videokijker op een Web-pagina ](/help/assets/dynamic-media/embed-code.md) in.

   * [ produceer videorapporten ](#viewing-video-reports).

   * [ voeg veelvoudige titels en audiosporen aan een video ](#about-msma) toe.

## Werken met video in Dynamic Media {#working-with-video-in-dynamic-media}

Video in Dynamic Media is een end-to-end oplossing die het gemakkelijk maakt om hoogwaardige adaptieve video voor het stromen over veelvoudige schermen, met inbegrip van Desktops, tablets, en mobiele apparaten te publiceren. Een adaptieve videoreeks groepeert versies van de zelfde video die bij verschillende beetjetarieven en formaten zoals 400 kbps, 800 kbps, en 1000 kbps worden gecodeerd. De desktopcomputer of het mobiele apparaat detecteert de beschikbare bandbreedte.

Op een mobiel iOS-apparaat wordt bijvoorbeeld een bandbreedte gedetecteerd, zoals 3G, 4G of Wi-Fi. Vervolgens wordt automatisch de naar rechts gecodeerde video geselecteerd bij de verschillende bitsnelheden van de video in de adaptieve videoset. De video wordt gestreamd naar desktops, mobiele apparaten of tablets.

Bovendien wordt de videokwaliteit automatisch dynamisch geschakeld als de netwerkomstandigheden veranderen op het bureaublad of op het mobiele apparaat. Als een klant de modus Volledig scherm op een desktopcomputer inschakelt, reageert de Adaptive Video Set met een betere resolutie, waardoor de kijkervaring van de klant wordt verbeterd. Met Adaptieve videosets beschikt u over de best mogelijke kijkervaring voor klanten die Dynamic Media-video op meerdere schermen en apparaten afspelen.

De logica die een videospeler gebruikt om te bepalen welke gecodeerde video moet worden afgespeeld of tijdens het afspelen moet worden geselecteerd, is gebaseerd op het volgende algoritme:

1. De videospeler laadt het eerste videofragment op basis van de bitsnelheid die het dichtst bij de waarde ligt die voor de beginbitsnelheid is ingesteld in de speler zelf.
1. De videospelerschakelaars die op veranderingen in de bandbreedtesnelheid worden gebaseerd die de volgende criteria gebruiken:

   1. De speler kiest de hoogste bandbreedtestroom onder of gelijk aan de geschatte bandbreedte.
   1. De speler neemt slechts 80% van de beschikbare bandbreedte in aanmerking. Als er echter een overstap wordt gemaakt, is het conservatiever bij slechts 70% om overschatting te voorkomen en onmiddellijk terug te keren.

Voor gedetailleerde technische informatie over het algoritme, zie [ https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp ](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

Bij het beheren van enkelvoudige video en Adaptieve videosets wordt het volgende ondersteund:

* Video uploaden vanaf een groot aantal ondersteunde video-indelingen en audio-indelingen. Video coderen naar MP4 H.264-indeling om op meerdere schermen te worden afgespeeld. U kunt vooraf gedefinieerde adaptieve videovoorinstellingen gebruiken, voorinstellingen voor één videocodering gebruiken of uw eigen codering aanpassen om de kwaliteit en de grootte van de video te bepalen.

   * Wanneer een adaptieve videoset wordt gegenereerd, bevat deze MP4-video&#39;s.
   * **Nota**: De primaire/bronvideo&#39;s worden niet toegevoegd aan een Aangepaste VideoReeks.

* ondertiteling in alle HTML5-videoviewers.
* Video organiseren, doorbladeren en doorzoeken met volledige metagegevensondersteuning voor een efficiënt beheer van video-elementen.
* Lever Adaptieve videosets naar het web en desktops, tablets en mobiele apparaten.

Adaptieve videostreaming wordt ondersteund op verschillende iOS-platforms. Zie {de Gids van de Verwijzing van de Kijkers van Dynamic Media 0} ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-reference).[

<!-- OUTDATED 2/28/22 BASED ON CQDOC-18692 Dynamic Media supports mobile video playback for MP4 H.264 video. You can find BlackBerry&reg; devices that support this video format at the following: [Supported video formats on BlackBerry&reg;](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

OUTDATED 2/28/22 BASED ON CQDOC-18692 You can find Windows&reg; devices that support this video format at the following [Supported video formats on Windows&reg; Phone](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/supported-codecs). -->

* Speel de video terug gebruikend de Voorinstellingen van de VideoKijker van Dynamic Media, met inbegrip van:

   * Enkele videoviewers.
   * Gemengde Media-viewers die zowel video- als afbeeldingsinhoud combineren.

* Configureer videospelers om aan uw brandingbehoeften te voldoen.
* Video met een eenvoudige URL of insluitcode integreren in uw website, mobiele site of mobiele toepassing.

<!-- GIVES a 404 See [Dynamic video playback](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&config=GeoRetail/Universal_Video1&stageSize=640,480) sample. -->

Zie ook [ Kijkers voor Experience Manager Assets en Dynamic Media Classic ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers#viewers-aem-assets-dmc) en [ Kijkers voor Experience Manager Assets slechts ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers#viewers-for-aem-assets-only) in de [ Gids van de Verwijzing van de Kijkers van Dynamic Media ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources).

## Tips en trucs: De HTML5-videoviewer gebruiken {#best-practice-using-the-html-video-viewer}

De Dynamic Media HTML5-voorinstellingen voor videoviewers zijn robuuste videospelers. U kunt ze gebruiken om veel voorkomende problemen te voorkomen die te maken hebben met het afspelen van HTML5-video en met problemen die te maken hebben met mobiele apparaten. Bijvoorbeeld een gebrek aan adaptieve streaminglevering met bitsnelheid en een beperkt bereik van de desktopbrowser.

Aan de ontwerpkant van de speler, kunt u de functionaliteit van de videospeler ontwerpen gebruikend standaardWeb ontwikkelingshulpmiddelen. U kunt bijvoorbeeld de knoppen, besturingselementen en de achtergrond van een aangepaste posterafbeelding ontwerpen met behulp van HTML5 en CSS om u te helpen uw klanten te bereiken met een aangepaste weergave.

Aan de afspeelzijde van de viewer wordt automatisch de videocapaciteit van de browser gedetecteerd. Vervolgens wordt de video afgespeeld met HLS of DASH, ook wel adaptieve videostreaming genoemd. Of als deze leveringsmethoden niet aanwezig zijn, wordt in plaats daarvan HTML5 progressief gebruikt.

>[!NOTE]
>
>Als u DASH voor uw video&#39;s wilt gebruiken, moet de Technische ondersteuning van de Adobe deze eerst inschakelen op uw account. Zie [ DASH op uw rekening ](#enable-dash) toelaten.

U kunt de mogelijkheid om de afspeelcomponenten te ontwerpen met behulp van HTML5 en CSS combineren tot één speler. Het kan het afspelen ingesloten hebben en adaptief en progressief streamen gebruiken, afhankelijk van de mogelijkheden van de browser. Al deze functionaliteit betekent dat u het bereik van uw rijke media-inhoud kunt uitbreiden naar zowel gebruikers op het bureaublad als mobiele gebruikers en een gestroomlijnde videobeleving kunt garanderen.

Zie ook [ Kijkers voor Experience Manager Assets slechts ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers#viewers-for-aem-assets-only) in de [ Gids van de Verwijzing van de Kijkers van Dynamic Media ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources).


### Video afspelen op bureaubladcomputers en mobiele apparaten met de HTML5-videoviewer {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

Voor adaptieve videostreaming op het bureaublad en mobiele apparaten zijn de video&#39;s die worden gebruikt voor het schakelen naar een andere bitsnelheid, gebaseerd op alle MP4-video&#39;s in de adaptieve videoset.

Het afspelen van video vindt plaats met HLS of DASH of met progressieve videodownload. In eerdere versies van Experience Manager, zoals 6.0, 6.1 en 6.2, werden video&#39;s gestreamd via HTTP.

In Experience Manager 6.3 en hoger worden video&#39;s nu gestreamd via HTTPS (dat wil zeggen, HLS of DASH) omdat de URL van de DM-gatewayservice altijd HTTPS gebruikt. Dit standaardgedrag heeft geen gevolgen voor de klant. Videostreaming vindt altijd plaats via HTTPS als de browser dit ondersteunt. Zie de volgende tabel.

Daarom

* Als u een HTTPS-website met HTTPS-videostreaming hebt, is streaming prima.
* Als u een HTTP-website met HTTPS-videostreaming hebt, is streaming prima en zijn er geen problemen met gemengde inhoud in de webbrowser.

DASH is de internationale standaard en HLS is een Apple-standaard. Beide worden gebruikt voor adaptieve videostreaming. En, passen beide technologieën automatisch playback aan die op de capaciteit van de netwerkbandbreedte wordt gebaseerd. Het laat de klant ook &quot;zoeken&quot;aan om het even welk punt in de video zonder de behoefte om op de rest van de video te wachten te downloaden.

Progressieve video wordt geleverd door de video lokaal te downloaden en op het desktopsysteem of mobiele apparaat van de gebruiker op te slaan.

De volgende lijst beschrijft het apparaat, browser, en playbackmethode van video&#39;s op Desktopcomputers en mobiele apparaten gebruikend de [ Dynamic Media HTML5 VideoKijker ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video#interactive-video).

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
   <td>In Windows® 8 en Windows® 10 - Gebruik HTTPS geforceerd wanneer DASH of HLS wordt aangevraagd. Bekende beperking: HTTP op DASH of HLS werkt niet in deze browser/werkend systeemcombinatie <br /> <br /> op Windows® 7 - Progressieve download. Gebruikt standaardlogica voor HTTP versus HTTPS protocol.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Firefox 23-44</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Firefox 45 of hoger</td>
   <td>HLS of DASH* adaptieve bitsnelheidstreaming</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Chrome</td>
   <td>HLS of DASH* adaptieve bitsnelheidstreaming</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Safari (Mac)</td>
   <td>HLS adaptieve bitsnelheidstreaming</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Chrome (Android™ 6 of eerder)</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Chrome (Android™ 7 of hoger)</td>
   <td>HLS of DASH* adaptieve bitsnelheidstreaming/td&gt;
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Android™ (standaardbrowser)</td>
   <td>Progressieve download.</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Safari (iOS)</td>
   <td>HLS adaptieve bitsnelheidstreaming</td>
  </tr>
  <tr>
   <td>Mobiel</td>
   <td>Chrome (iOS)</td>
   <td>HLS adaptieve bitsnelheidstreaming</td>
  </tr>
 </tbody>
</table>

>[!IMPORTANT]
>
>Als u DASH voor uw video&#39;s wilt gebruiken, moet de Technische ondersteuning van de Adobe deze eerst inschakelen op uw account. Zie [ DASH op uw rekening ](#enable-dash) toelaten.

<!--  THIS LINE WAS REMOVED FROM THE TABLE ABOVE ON FEB 28, 2022 BASED ON CQDOC 18692 -RSB <tr>
   <td>Mobile</td>
   <td>BlackBerry&reg;</td>
   <td>HLS or DASH</td>
  </tr>
 -->

## Architectuur van Dynamic Media-videooplossing {#architecture-of-dynamic-media-video-solution}

In de volgende afbeelding ziet u de algemene ontwerpworkflow voor video&#39;s die via de DMGateway (in de Dynamic Media Hybrid-modus) zijn geüpload en gecodeerd en voor openbare consumptie beschikbaar zijn.

![ chlimage_1-427 ](assets/chlimage_1-427.png)

## Hybride publicatiearchitectuur voor video&#39;s {#hybrid-publishing-architecture-for-videos}

![ chlimage_1-428 ](assets/chlimage_1-428.png)

## Aanbevolen werkwijzen voor het coderen van video&#39;s {#best-practices-for-encoding-videos}

Het **Dynamic Media codeert Video** werkschema codeert video als u Dynamic Media en opstelling Video Cloud Servicen hebt toegelaten. In deze workflow worden de historie en informatie over fouten van het workflowproces vastgelegd. Als u Dynamic Media hebt ingeschakeld en Video-Cloud Servicen hebt ingesteld, wordt de **[!UICONTROL Dynamic Media Encode Video]** -workflow automatisch geactiveerd wanneer u een video uploadt. (Als u Dynamic Media niet gebruikt, wordt de **[!UICONTROL DAM Update Asset]** -workflow van kracht.)

Hier volgt een overzicht van tips voor het coderen van bronvideobestanden.

<!-- For advice about video encoding, see the following:

* [Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution](https://www.adobe.com/go/learn_s7_streaming101_en).
* [Video Encoding Basics](https://www.adobe.com/go/learn_s7_encoding_en). -->

### Source-videobestanden {#source-video-files}

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

U kunt de metagegevens van een bestand verkrijgen door de metagegevens van het bestand te bekijken met een bewerkgereedschap voor video&#39;s of met een toepassing die is ontworpen voor het verkrijgen van metagegevens. Hieronder vindt u instructies voor het gebruik van MediaInfo, een toepassing van derden, voor het verkrijgen van de metagegevens van een videobestand:

1. Ga naar [ Download MediaInfo ](https://mediaarea.net/en/MediaInfo/Download).
1. Selecteer en download het installatieprogramma voor de GUI-versie en volg de installatie-instructies.
1. Klik na de installatie met de rechtermuisknop op het videobestand (alleen Windows®) en selecteer MediaInfo, of open MediaInfo en sleep het videobestand naar de toepassing. U ziet alle metagegevens die aan het videobestand zijn gekoppeld, inclusief de breedte, hoogte en fps.

### Hoogte-breedteverhouding {#aspect-ratio}

Wanneer u een voorinstelling voor videocodering kiest of maakt voor uw primaire bronvideobestand, moet u ervoor zorgen dat de voorinstelling dezelfde hoogte-breedteverhouding heeft. Deze aanpak zorgt voor consistentie met het primaire bronvideobestand. De hoogte-breedteverhouding is de verhouding tussen de breedte en de hoogte van de video.

Verkrijg de metagegevens van het bestand om de hoogte-breedteverhouding van een videobestand te bepalen. Noteer de breedte en hoogte van het bestand (zie De bovenstaande metagegevens van een bestand ophalen). Gebruik vervolgens deze formule om de hoogte-breedteverhouding te bepalen:

width/height = hoogte-breedteverhouding

In de volgende tabel wordt beschreven hoe de resultaten van de formule worden omgezet in algemene opties voor de hoogte-breedteverhouding:

| Formulerresultaat | Hoogte-breedteverhouding |
|--- |--- |
| 1,33 | 4:3 |
| 0,75 | 3:4 |
| 1,78 | 16:9 |
| 0,56 | 9:16 |

Een video van 1440 x 1080 hoogte heeft bijvoorbeeld een hoogte-breedteverhouding van 1440/1080 of 1,33. In dit geval kiest u een voorinstelling voor videocodering met een hoogte-breedteverhouding van 4:3 om het videobestand te coderen.

### Bitsnelheid {#bitrate}

De bitsnelheid is de hoeveelheid gegevens die is gecodeerd om één seconde te kunnen afspelen. De bitsnelheid wordt gemeten in kilobits per seconde (Kbps).

>[!NOTE]
>
>Omdat in alle codecs compressie met verlies wordt gebruikt, is bitsnelheid de belangrijkste factor voor de videokwaliteit. Bij compressie met verlies neemt de kwaliteit af naarmate u een videobestand comprimeert. Daarom zijn alle andere eigenschappen gelijk (de resolutie, framesnelheid en codec), hoe lager de bitsnelheid, hoe lager de kwaliteit van het gecomprimeerde bestand.

Wanneer u een codering voor bitsnelheden selecteert, kunt u kiezen uit twee typen:

* **[!UICONTROL Constant Bitrate Encoding]** (CBR) - Tijdens CBR-codering blijft de bitsnelheid of het aantal bits per seconde tijdens het coderingsproces ongewijzigd. Bij CBR-codering blijft de gegevenssnelheid van de set behouden voor de instelling van de gehele video. Bij CBR-codering worden mediabestanden niet geoptimaliseerd voor kwaliteit, maar wordt opslagruimte bespaard.
Gebruik CBR als uw video een vergelijkbaar bewegingsniveau in de gehele video bevat. CBR wordt meestal gebruikt voor het streamen van video-inhoud. Zie ook [ douane-toegevoegde videocoderingsparameters van het Gebruik ](/help/assets/dynamic-media/video-profiles.md#using-custom-added-video-encoding-parameters).

* **[!UICONTROL Variable Bitrate Encoding]** (VBR) - VBR-codering past de gegevenssnelheid naar beneden en naar de bovenste limiet die u instelt, aan op basis van de gegevens die de compressor nodig heeft. Deze functionaliteit houdt in dat de bitsnelheid van het mediabestand tijdens een VBR-coderingsproces dynamisch wordt verhoogd of verlaagd, afhankelijk van de bitsnelheidbehoeften van het mediabestand.
VBR duurt langer om te coderen, maar geeft de meest gunstige resultaten. De kwaliteit van het mediabestand is superieur. VBR wordt het meest meestal gebruikt voor http progressieve levering van video-inhoud.

Wanneer gebruikt u VBR versus CRB?
Als u VBR en CBR selecteert, wordt het bijna altijd aanbevolen VBR te gebruiken voor uw mediabestanden. VBR biedt bestanden van hogere kwaliteit tegen concurrerende bitsnelheden. Wanneer u VBR gebruikt, moet u ervoor zorgen dat u met codering met twee controles gebruikt en de maximale bitsnelheid instellen op 1,5x de bitsnelheid van de doelvideo.

Wanneer u een voorinstelling voor videocodering kiest, moet u rekening houden met de verbindingssnelheid van de doelgebruiker. Kies een voorinstelling met een gegevenssnelheid van 80 procent van die snelheid. Als de verbindingssnelheid van de doelgebruiker bijvoorbeeld 1000 Kbps is, is de beste voorinstelling een snelheid met een videogegevenssnelheid van 800 Kbps.

In deze tabel wordt de gegevenssnelheid beschreven van standaardverbindingssnelheden.

| Snelheid (Kbps) | Verbindingstype |
|--- |--- |
| 256 | Inbelverbinding. |
| 800 | Normale mobiele verbinding. Kies hiervoor een gegevenssnelheid tussen 400 en maximaal 800 voor 3G-ervaringen. |
| 2000 | Standaardbreedbandverbinding voor desktops. Voor deze verbinding, richt een gegevenstarief in de waaier 800-2000 Kbps, met de meeste doelstellingen gemiddeld 1200-1500 Kbps. |
| 5000 | Typische breedbandverbinding. Codering in dit bovenste bereik wordt niet aanbevolen, omdat de video bij deze snelheid niet beschikbaar is voor de meeste consumenten. |

### Resolutie {#resolution}

**Resolutie** beschrijft de hoogte en de breedte van een videodossier in pixel. De meeste bronvideo wordt opgeslagen met een hoge resolutie (bijvoorbeeld 1920 x 1080). Voor streamingdoeleinden wordt bronvideo gecomprimeerd tot een lagere resolutie (640 x 480 of lager).

Resolutie en gegevenssnelheid zijn twee geïntegreerde gekoppelde factoren die de videokwaliteit bepalen. Als u dezelfde videokwaliteit wilt behouden, geldt dat hoe hoger het aantal pixels in een videobestand (hoe hoger de resolutie), hoe hoger de gegevenssnelheid. Neem bijvoorbeeld het aantal pixels per frame in een videobestand met een resolutie van 320 x 240 en een resolutie van 640 x 480:

| Resolutie | Pixels per frame |
|--- |--- |
| 320 x 240 | 76.800 |
| 640 x 480 | 307.200 |

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
| 480p | 480 | Medium-scherm |
| 720p | 720 | Groot scherm |
| 1080p | 1080 | High-definition groot scherm |

### FPS (frames per seconde) {#fps-frames-per-second}

In de Verenigde Staten en Japan wordt de meeste video met 29,97 fps opgenomen; in Europa wordt de meeste video met 25 fps opgenomen. Een film wordt opgenomen met 24 fps.

Kies een voorinstelling voor videocodering die overeenkomt met de fps-snelheid van het primaire bronvideobestand. Als uw primaire bronvideo bijvoorbeeld 25 fps is, kiest u een coderingsvoorinstelling met 25 fps. Standaard wordt bij alle aangepaste codering de fps van het primaire bronvideobestand gebruikt. Daarom hoeft u de fps-instelling niet expliciet op te geven wanneer u een voorinstelling voor videocodering maakt.

### Afmetingen videocodering {#video-encoding-dimensions}

Voor optimale resultaten selecteert u de coderingsafmetingen, zodat de bronvideo een volledig veelvoud van alle gecodeerde video&#39;s is.

Als u deze verhouding wilt berekenen, deelt u de bronbreedte door de gecodeerde breedte om de breedteverhouding op te halen. Vervolgens deelt u de bronhoogte door de gecodeerde hoogte om de hoogte-breedteverhouding te bepalen.

Als de resulterende verhouding een geheel geheel getal is, betekent dit dat de video optimaal wordt geschaald. Als de resulterende verhouding geen geheel geheel getal is, is dit van invloed op de videokwaliteit doordat pixelartefacten overblijven op het scherm. Dit effect is vooral opvallend wanneer de video tekst heeft.

Stel dat uw bronvideo bijvoorbeeld 1920 x 1080 is. In de volgende tabel bieden de drie gecodeerde video&#39;s de optimale coderingsinstellingen.

| Videotype | Breedte x hoogte | Breedteverhouding | Hoogteverhouding |
|--- |--- |--- |--- |
| Source | 1920 x 1080 | 1 | 1 |
| Gecodeerd | 960 x 540 | 2 | 2 |
| Gecodeerd | 640 x 360 | 3 | 3 |
| Gecodeerd | 480 x 270 | 4 | 4 |

### Gecodeerde videobestandsindeling {#encoded-video-file-format}

Dynamic Media raadt u aan voorinstellingen voor MP4 H.264-videocodering te gebruiken. Omdat MP4-bestanden de H.264-videocodec gebruiken, biedt deze video van hoge kwaliteit, maar met een gecomprimeerde bestandsgrootte.

## Videorapporten weergeven {#viewing-video-reports}

>[!NOTE]
>
>Videorapporten zijn alleen beschikbaar wanneer u de modus Dynamic Media - Hybride uitvoert.

De videoRapporten tonen verscheidene gezamenlijke metriek over een gespecificeerde periode om u te helpen controleren dat *gepubliceerde* individuele en gezamenlijke video&#39;s zoals verwacht presteren. De volgende statistische gegevens worden geaggregeerd voor alle gepubliceerde video&#39;s op uw gehele website:

* Video start
* Voltooiingssnelheid
* Gemiddelde tijd op video
* Totale tijd op video
* Video&#39;s per bezoek

Een lijst van alle *gepubliceerde* video&#39;s is ook vermeld zodat kunt u de hoogste bekeken video&#39;s op uw website volgen die op totale videobegin wordt gebaseerd.

Wanneer u een videonaam in de lijst selecteert, wordt het rapport voor het vasthouden van het publiek van de video (drop-off) weergegeven in de vorm van een lijndiagram. Het diagram toont het aantal weergaven voor een bepaald tijdstip tijdens het afspelen van video. Wanneer u de video afspeelt, wordt de verticale balk gesynchroniseerd met de tijdindicator in de speler. De vallen in de gegevens van het lijndiagram wijzen op waar uw publiek van oninteresse wegvalt.

Als de video buiten Adobe Experience Manager Dynamic Media is gecodeerd, zijn het diagram voor het vasthouden van het publiek (drop-off) en de gegevens voor het afspeelpercentage in de tabel niet beschikbaar.

>[!NOTE]
>
>Het bijhouden en rapporteren van gegevens is uitsluitend gebaseerd op het gebruik van de eigen videospeler van Dynamic Media en de bijbehorende voorinstelling van de videospeler. Daarom kunt u video&#39;s die door andere videospelers worden afgespeeld, niet bijhouden en rapporteren.

Door gebrek, de eerste keer u VideoRapporten ingaat, toont het rapport videogegevens die bij de eerste van de huidige maand beginnen en met de datum van de huidige maand beëindigen. U kunt het standaarddatumbereik echter overschrijven door uw eigen datumbereik op te geven. De volgende keer in VideoRapporten, wordt de datumwaaier gebruikt u specificeerde.

Videorapporten werken alleen correct als er automatisch een rapportsuite-id wordt gemaakt wanneer Dynamic Media-Cloud Servicen zijn geconfigureerd. Tegelijkertijd wordt de rapportsuite-id doorgegeven aan de Publish-server, zodat deze beschikbaar is voor de functie URL kopiëren wanneer u een voorvertoning van elementen weergeeft. Voor deze functionaliteit moet de Publish-server echter al zijn ingesteld. Als de Publish-server niet is ingesteld, kunt u toch publiceren om het videoverslag te bekijken. U moet echter terugkeren naar de Dynamic Media Cloud Configuration en **[!UICONTROL OK]** selecteren.

**aan meningsvideorapporten:**

1. Selecteer in de linkerbovenhoek van de Experience Manager het logo van de Experience Manager. Ga in de linkertrack naar **[!UICONTROL Tools]** (hamerpictogram) > **[!UICONTROL Assets]** > **[!UICONTROL Video Reports]** .
1. Voer een van de volgende handelingen uit op de pagina Videorapporten:

   * Selecteer in de rechterbovenhoek het pictogram **[!UICONTROL Refresh Video Report]** .
U kunt gebruiken verfrist zich slechts als de einddatum van het rapport de huidige dag is. Deze eigenschap zorgt ervoor dat u video het volgen kunt zien die sinds de laatste tijd is voorgekomen u het rapport in werking stelde.

   * Selecteer in de rechterbovenhoek het pictogram **[!UICONTROL Date Picker]** .
Geef het begin- en einddatumbereik op waarvoor u videogegevens wilt en selecteer vervolgens **[!UICONTROL Run Report]** .

   De Hoogste de groepsdoos van Metriek identificeert diverse gezamenlijke metingen voor alle *gepubliceerde* video&#39;s over uw plaats.

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


## Ondersteuning inschakelen voor DASH, meervoudige ondertitels en audiotracks en door AI gegenereerde ondertitels op uw Dynamic Media-account {#enable-dash}

U kunt ondersteuning inschakelen in Dynamic Media voor:

* DASH
* Meerdere bijschriften en audiotracks
* Door AI gegenereerde bijschriften (beperkte beschikbaarheid)

Door een Adobe voor klantenondersteuning te maken en in te dienen.

Als u een van de drie bovengenoemde mogelijkheden inschakelt, kunnen alle mogelijkheden worden benut. Dus als je alleen DASH ingeschakeld wilt hebben, maak je alle drie de mogelijkheden die hierboven zijn vermeld mogelijk.

| Capaciteit | Beschrijving |
| --- | --- |
| DASH | DASH (Digital Adaptive Streaming via HTTP) is de internationale standaard voor videostreaming en wordt op grote schaal toegepast door verschillende videoviewers. Als DASH op uw account is ingeschakeld, kunt u kiezen uit DASH of HLS voor adaptieve videostreaming. U kunt ook kiezen voor beide opties met automatische schakelen tussen spelers als **[!UICONTROL auto]** is geselecteerd als het afspeeltype in de voorinstelling van de viewer.<br> sommige zeer belangrijke voordelen van het toelaten van DASH op uw rekening omvatten het volgende:<br> ・ De stroomvideo van DASH van het Pakket voor het adaptieve bitrate stromen. Deze methode leidt tot een efficiëntere levering. Adaptieve streaming zorgt voor de beste kijkervaring voor uw klanten.<br>・Voor streaming via browser geoptimaliseerd met Dynamic Media-spelers wordt geschakeld tussen HLS- en DASH-streaming om de beste kwaliteit van de service te garanderen. Wanneer een Safari-browser wordt gebruikt, schakelt de videospeler automatisch over naar HLS.<br>・U kunt uw voorkeurstreaming methode (HLS of DASH) configureren door de voorinstelling voor de videoviewer te bewerken.<br>・Geoptimaliseerde videocodering zorgt ervoor dat er geen extra opslagruimte wordt gebruikt terwijl de DASH-mogelijkheid wordt ingeschakeld. Er wordt één set videocoderingen gemaakt voor zowel HLS als DASH om de opslagkosten voor video te optimaliseren.<br>・Helps maakt de levering van video toegankelijker voor uw klanten.<br>・Haal de URL voor streaming ook via API&#39;s op. |
| Meerdere bijschriften en audiotracks | U kunt ervan profiteren dat ondersteuning voor meerdere bijschriften en audiotracks automatisch is ingeschakeld. Nadat u deze optie hebt ingeschakeld, worden alle volgende video&#39;s die u uploadt, verwerkt met een nieuwe back-endarchitectuur die ondersteuning biedt voor het toevoegen van meerdere bijschriften en audiotracks aan uw video&#39;s. |
| Door AI gegenereerde bijschriften (beperkte beschikbaarheid) | Maak bijschriften voor uw video&#39;s die worden aangedreven door AI. Met AI wordt de transcriptie van de video gemaakt en omgezet in bijschriften. Zelfs de tijdlijn is gedefinieerd. |

>[!IMPORTANT]
>
>Om het even welke video&#39;s die u *alvorens* toelatend veelvoudige titel en audiospoorsteun op uw rekening van Dynamic Media uploadde, [ moet worden opnieuw verwerkt ](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). Deze videoopwerkingsstap is nodig om ervoor te zorgen dat meerdere bijschriften en audiotrackmogelijkheden beschikbaar zijn. De video-URL&#39;s blijven werken en worden na de opwerking op de gebruikelijke wijze afgespeeld.

**om DASH, multi-captions en multi-audiosporen, en AI-Gegenereerde ondertitels op uw rekening van Dynamic Media toe te laten:**

1. [ gebruik de Admin Console om de verwezenlijking van een nieuw steungeval ](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) te beginnen.
1. Als u een ondersteuningsgeval wilt maken, volgt u de instructies en zorgt u ervoor dat u de volgende informatie opgeeft:

   * Primaire contactpersoon, e-mail, telefoon.
   * De omgeving van uw Cloud Servicen (programma-id en milieu-id).
   * De naam van je Dynamic Media-bedrijfsaccount.
   * Uw Dynamic Media-regio: Noord-Amerika (NA), Azië-Stille Oceaan (APAC) of Europa-Midden-Oost-Azië (EMEA).
   * Geef op of ondersteuning voor DASH, meervoudige ondertitels en meeraudiotracks en door AI gegenereerde ondertitels (beperkte beschikbaarheid) ingeschakeld moet zijn op uw Dynamic Media-account, op AEM as a Cloud Service.

1. De Steun van de Klant van de Adobe voegt u aan de Klant toe wachtlijst op basis van de orde waarin de verzoeken worden voorgelegd.
1. Wanneer de Adobe klaar is om uw verzoek te behandelen, contacteert de Steun van de Klant u om een doeldatum voor enablement te coördineren en te plaatsen.
1. De Klantenondersteuning van de Adobe brengt u op de hoogte na voltooiing.
1. Voer nu een van de volgende handelingen uit:

   * Creeer uw [ vooraf ingestelde videokijker ](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset) zoals gebruikelijk.
   * Creeer uw [ videoprofiel ](/help/assets/dynamic-media/video-profiles.md) zoals gebruikelijk.
   * [ voeg veelvoudige titels en audiosporen ](#add-msma) aan uw video toe.


<!-- HIDDEN AS OF OCTOBER 7, 2024 AS PER EMAIL REQUEST FROM RIYA MIDHA ON SAME DATE 

## About multiple caption and audio track support for videos in Dynamic Media{#about-msma}

With multiple caption and audio track capability in Dynamic Media, you can easily add multiple captions and audio tracks to a primary video. This capability means that your videos are accessible to a global audience. You can customize a single, published primary video to a global audience in multiple languages and adhere with accessibility guidelines for different geographical regions. Authors can also manage the captions and audio tracks from a single tab in the user interface.

   ![Captions and audio tracks tab in Dynamic Media along with a table showing uploaded .VTT caption files and uploaded .MP3 audio track files for a video.](/help/assets/dynamic-media/assets/msma-caption-audiotracks-tab2.png)


Some of the use cases to consider for adding multiple captions and audio tracks to your primary video include the following:


| Type | Use case | 
| --- | --- |
| Captions | Multiple language support<br>Descriptive text for accessibility |
|Audio tracks | Multiple language support<br>Commentary tracks<br>Descriptive audio |


All [video formats supported in Dynamic Media](/help/assets/file-format-support.md) and all Dynamic Media video viewers-except the Dynamic Media Video_360 viewer-are supported for use with multiple captions and audio tracks.

Multi-caption and multi-audio track capability is available for your Dynamic Media account by way of a feature toggle that must be enabled (turned on) by Adobe Customer Support.

### Add multiple captions and audio tracks to your video {#add-msma}

Before you add multiple caption and audio tracks to your video, be sure you already have the following in-place:

* Dynamic Media is set up in an AEM environment.
* A [Dynamic Media Video profile is applied to the folder where your videos are ingested](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).
* [Multi-caption, and multi-audio track is enabled on your Dynamic Media account](/help/assets/dynamic-media/video.md#enable-dash).

Added captions and captions are supported with WebVTT and Adobe VTT formats. And, added audio track files are supported with MP3 format.

>[!IMPORTANT]
>
>Any videos that you uploaded before enabling multiple caption and audio track support on your Dynamic Media account, [must be reprocessed](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). This video reprocessing step is necessary so that multiple caption and audio track capability is available to them. The video URLs continue to work and play as usual, after reprocessing.

**To add multiple captions and audio tracks to your video:**

1. [Upload your primary video to a folder](/help/assets/manage-video-assets.md#upload-and-preview-video-assets) that already has a video profile assigned to it.
1. Navigate to the uploaded video asset that you want to add multiple caption and audio tracks.
1. In asset selection mode, either from the List View or the Card View, select the video asset.
1. On the toolbar, select the Properties icon (a circle with an "i" in it). 

   ![Asset properties button.](/help/assets/dynamic-media/assets/msma-selectedasset-propertiesbutton.png)*Selected video asset in Card View.*

1. On the video's Properties page, select the **[!UICONTROL Captions & Audio Tracks]** tab.


   >[!TIP]
   >If you do not see the [!UICONTROL Captions & Audio Tracks] tab, it means either one of two things:
   >* The folder in which the selected video resides does not have a video profile assigned to it. In which case, see [Apply a video profile to the folder](/help/assets/dynamic-media/video-profiles.md#applying-video-profiles-to-specific-folders)
   >* Or, Dynamic Media must reprocess the video. In which case, see [Reprocess Dynamic Media assets in a folder](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

    When you have completed either one of the above tasks, return to these steps.

   ![Asset properties](/help/assets/dynamic-media/assets/msma-audiotracks.png)*Captions and audio tracks tab on the video's Properties page.*

1. (Optional) To add one or more caption files to a video, do the following:

    * Select **[!UICONTROL Upload Captions]**.
    * Navigate to, and select, one or more `.vtt` (Video Text Tracks) files and open them.
    * For captions to be visible on the media player, you must add required details (metadata) about each caption file that you uploaded. Select the pencil icon to the right of a caption file name. In the Edit Caption dialog box, enter the following required details about the file, then select **[!UICONTROL Save]**. Repeat this process for each caption file that you uploaded:


    | Caption metadata | Description | 
    | --- | --- | 
    Filename | The default filename is derived from the original filename. The filename can be changed only while uploading and cannot be changed later. Filename character requirements are the same as for AEM Assets.<br>The same filename cannot be used for additional caption files and audio track files. |
    | Language | Select the language of the caption. |
    | Type | Select the type of caption that you are using.<br>**Subtitle** - The caption text displayed with the video that translates or transcribes the dialogue.<br>**Caption** - The caption text includes background noises and speaker identification. It also includes other relevant details alongside the translation or transcription of dialogue. This functionality makes the content more accessible to individuals who are deaf or hard of hearing. |
    | Label | The text that is displayed for the caption's name in the **[!UICONTROL Select audio or caption]** pop-up list in the media player. The label is what a customer sees that corresponds to a subtitle or caption track. For example, English (CC). |

    You can change or edit caption metadata later, if necessary. When the video is published, these details are reflected on public URLs in published videos.

1. (Optional) To add one or more audio tracks to a video, do the following:

    * Select **[!UICONTROL Upload Audio Tracks]**.
    * Navigate to, and select, one or more .mp3 files and open them.
    * To make audio tracks visible in the **[!UICONTROL Select audio or caption]** pop-up list on the media player, add the required details for each audio track file. Ensure you include all necessary information for proper display. Select the pencil icon to the right of an audio track file name. In the Edit Audio Track dialog box, enter the following required details, then select **[!UICONTROL Save]**. Repeat this process for each audio track file that you uploaded.

    | Audio Track metadata | Description |
    | --- | --- |
    | Filename | The default filename is derived from the original filename. The filename can be changed only while uploading and cannot be changed later. Filename character requirements are the same as for AEM Assets.<br>The same filename cannot be used for additional audio track files or caption files.| 
    | Language | Select the language of the audio track. |
    | Type | Select the type of audio track that you are using.<br>**Original** - The audio track originally attached to the video and represented as `[Original]` in the label with English language selected by default. While **[!UICONTROL Label]** and **[!UICONTROL Language]** can be changed in the **[!UICONTROL Edit Audio Track]** dialog box, it defaults to the original values if the primary video is reprocessed.<br>**Standard** - An add-on audio track for a language other than the original.<br>**Audio description** - An audio track that also includes a descriptive narration of non-verbal actions and gestures in the video, making content more accessible for individuals who are visually impaired. |
    | Label | The text that is displayed as the audio track's name in the **[!UICONTROL Select audio or caption]** pop-up list in the media player. The label is what a customer sees that corresponds to an audio track. For example, `English [Original]`. The label of audio attached to a video is set to `[Original]` by default. |

    You can change or edit this audio track metadata later, if necessary. When the video is published, these details are reflected on public URLs in published videos.

1. In the upper-right corner of the page, from the **[!UICONTROL Save & Close]** drop-down list, select **[!UICONTROL Save]**. The files are uploaded and metadata processing begins, as seen in the Status column of the interface.

    >[!NOTE]
    >
    >Based on the caching settings of your instance, the metadata processing can take several minutes before it is reflected in preview and in published URLs.

1. (Optional) If you selected **[!UICONTROL Save & Close]** in the previous step, instead of selecting **[!UICONTROL Save]**, you can still view the processing status of the uploaded files. See [View the lifecycle status of uploaded caption and audio track files](/help/assets/dynamic-media/video.md#lifecycle-status-video).

1. (Optional) Preview the video before publishing to ensure the captions and audio work as expected. See [Preview a video that has multiple captions and audio tracks](/help/assets/dynamic-media/video.md#preview-video-audio-subtitle).

1. Publish the video. See [Publish assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md). -->



## Ondersteuning voor meerdere bijschriften en audiotracks voor video&#39;s in Dynamic Media{#about-msma}

Met de mogelijkheden voor meerdere bijschriften en audiotracks in Dynamic Media kunt u eenvoudig meerdere audiotracks toevoegen. U kunt ook bestanden met meerdere bijschriften toevoegen met behulp van uw eigen `.vtt` (Video Text Track)-bestanden of door AI gegenereerde bijschriftbestanden. Door AI gegenereerde bijschriften in Dynamic Media zijn ontworpen om de toegankelijkheid en betrokkenheid van video te verbeteren door automatisch nauwkeurige en gesynchroniseerde ondertitels te genereren. Deze technologie gebruikt geavanceerde AI algoritmen om gesproken inhoud in tekst om te zetten, die dan als titels op de video wordt getoond. Enkele belangrijke kenmerken van deze technologie zijn:

* **Automatische Transcriptie:** het systeem AI transcripes gesproken woorden in tekst in real time, die ervoor zorgen dat de titels snel en nauwkeurig worden geproduceerd.
* **Meertalige Steun:** de titels kunnen automatisch in meer dan 60 talen worden geleverd, makend het gemakkelijker om een globaal publiek te bereiken.
* **Verbeterde Toegankelijkheid:** door titels te verstrekken, worden de video&#39;s toegankelijker voor kijkers die doof of hard van het horen zijn, of mensen die verkiezen video&#39;s met het geluid weg te letten.
* **Verbeterde Betrokkenheid:** de Bijschriften kunnen helpen kijkeraandacht behouden en begrip verbeteren, vooral in lawaaierige milieu&#39;s of wanneer de inheemse taal van de kijker van de taal van de video verschillend is.

Deze functies maken van door AI aangedreven bijschriften een waardevol hulpmiddel voor makers van inhoud die de toegankelijkheid en betrokkenheid van hun video-inhoud willen verbeteren.

![ Bijschriften en audiosporen lusje in Dynamic Media samen met een lijst die geüploade .VTT titeldossiers en geüploade .MP3 audiospoordossiers voor een video tonen.](/help/assets/dynamic-media/assets/msma-caption-audiotracks-tab2.png)

Een aantal van de gebruiksscenario&#39;s die u moet overwegen om meerdere bijschriften en audiotracks toe te voegen aan uw primaire video, zijn onder andere:

| Type | Hoofdletters gebruiken |
|--- |--- |
| **Bijschriften** | Ondersteuning voor meerdere talen |
|  | Beschrijvende tekst voor toegankelijkheid |
| **Audiosporen** | Ondersteuning voor meerdere talen |
|  | Commentaartracks |
|  | Beschrijvende audio |

Alle [ video formaten die in Dynamic Media ](/help/assets/file-format-support.md) worden gesteund en alle videokijkers van Dynamic Media - behalve de Dynamic Media *Video_360* kijker - worden gesteund voor gebruik met veelvoudige titels en audiosporen.

Mogelijkheid voor meerdere bijschriften en audiotracks is beschikbaar voor uw Dynamic Media-account via een functiewissel die moet worden ingeschakeld (ingeschakeld) door de Adobe Klantenondersteuning.

### Meerdere bijschriften en audiotracks toevoegen aan uw video {#add-msma}

Voordat u meerdere bijschriften en audiotracks aan uw video toevoegt, moet u controleren of u al over het volgende beschikt:

* Dynamic Media wordt ingesteld in een AEM omgeving.
* A [ wordt het Videoprofiel van Dynamic Media toegepast op de omslag waar uw video&#39;s ](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders) worden opgenomen.
* [ de multi-caption/audiosporen en AI-Gegenereerde titels worden toegelaten op uw rekening van Dynamic Media ](#enable-dash).

Toegevoegde bijschriften worden ondersteund met de indelingen WebVTT en Adobe VTT. Toegevoegde audiotrackbestanden worden ook ondersteund in de MP3-indeling.

>[!IMPORTANT]
>
>Voor video&#39;s die *vóór* worden geupload toelatend veelvoudige titel/audiospoorsteun of AI-Gegenereerde titels op uw rekening van Dynamic Media, [ u hen ](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) moet opnieuw verwerken. Deze opwerkingsstap zorgt ervoor dat deze video&#39;s de functies voor meervoudige bijschriften/audiotracks en door AI gegenereerde bijschriften kunnen gebruiken. De video-URL&#39;s werken na het verwerken verder en worden op de gebruikelijke wijze afgespeeld.

**om veelvoudige titels en audiosporen aan uw video toe te voegen:**

1. [ uploadt uw primaire video aan een omslag ](/help/assets/manage-video-assets.md#upload-and-preview-video-assets) die reeds een videoprofiel heeft dat aan het wordt toegewezen.
1. Navigeer naar het geüploade video-element waaraan u meerdere bijschriften en audiotracks wilt toevoegen.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Klik op het pictogram Eigenschappen op de werkbalk (een cirkel met een &quot;i&quot; erin).
   ![ Geselecteerde videoactiva met controleteken over videoduimnagelbeeld en Eigenschappen van de Mening die op de toolbar worden benadrukt.](/help/assets/dynamic-media/assets/msma-selectedasset-propertiesbutton.png)*Geselecteerde videoactiva in de Mening van de Kaart.*
1. Selecteer de tab **[!UICONTROL Captions & Audio Tracks]** op de pagina Eigenschappen van video.

   >[!TIP]
   >Als u het tabblad **[!UICONTROL Captions & Audio Tracks]** niet ziet, betekent dit een van de volgende twee dingen:
   >
   >* Aan de map waarin de geselecteerde video zich bevindt, is geen videoprofiel toegewezen. In welk geval, zie [ een videoprofiel op de omslag ](/help/assets/dynamic-media/video-profiles.md#applying-video-profiles-to-specific-folders) toepassen
   >* Of Dynamic Media moet de video opnieuw verwerken. In welk geval, zie [ de activa van Dynamic Media in een omslag ](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) opnieuw verwerken.
   >
   >Als u een van de bovenstaande taken hebt uitgevoerd, gaat u terug naar deze stappen.

   ![ Bijschriften en Audiosporen lusje op de pagina van Eigenschappen.](/help/assets/dynamic-media/assets/msma-audiotracks.png)
   *Bijschriften en audiosporen lusje op de pagina van de Eigenschappen van de video.*

1. Ga als volgt te werk om een of meer audiotracks aan een video toe te voegen:
   1. Selecteer **[!UICONTROL Upload Audio Tracks]** .
   1. Navigeer naar en selecteer een of meer MP3-bestanden en open deze.
   1. Als u audiotracks wilt weergeven in de pop-uplijst van **[!UICONTROL Select audio or caption]** op de mediaspeler, moet u vereiste gegevens over elk audiotrackbestand toevoegen. Hiermee zorgt u ervoor dat alle audiotracks correct worden weergegeven en toegankelijk zijn. Selecteer het potloodpictogram rechts van de bestandsnaam van een audiotrack. In **geef Audiospoor** dialoogdoos uit, ga de volgende vereiste details in:

      | Metagegevens audiotrack | Beschrijving |
      |--- |--- |
      | Bestandsnaam | De standaardbestandsnaam wordt afgeleid van de oorspronkelijke bestandsnaam. De bestandsnaam kan alleen tijdens het uploaden worden gewijzigd en kan later niet worden gewijzigd. De vereisten voor bestandsnaamtekens zijn gelijk aan die voor AEM Assets.<br> zelfde filename kan niet voor extra audiospoordossiers of titeldossiers worden gebruikt. |
      | Taal | Selecteer de juiste taal van de audiotrack. |
      | Type | Selecteer het type audiotrack dat u gebruikt.<br>**Origineel** - het audiospoor oorspronkelijk in bijlage aan de video en vertegenwoordigd als `[Original]` in het etiket met `English` taal die door gebrek wordt geselecteerd. Hoewel **[!UICONTROL Label]** en **[!UICONTROL Language]** kunnen worden gewijzigd in het dialoogvenster **[!UICONTROL Edit Audio Track]** , worden de oorspronkelijke waarden gebruikt als de primaire video opnieuw wordt verwerkt.<br>**Norm** - een toe:voegen-op audiospoor voor een taal buiten origineel.<br>**audiobeschrijving** - een audiospoor dat ook een beschrijvend verhaal van non-verbale acties en gebaren in de video omvat, die inhoud toegankelijker maken voor individuen die visueel gehandicapt zijn. |
      | Label | De tekst die als naam van de audiotrack in de pop-uplijst **[!UICONTROL Select audio or caption]** in de mediaspeler wordt weergegeven. Het label is wat een klant ziet die met een audiotrack correspondeert. Bijvoorbeeld `English [Original]` . Het label van de audio die aan een video is gekoppeld, wordt standaard ingesteld op `[Original]` . |

      U kunt deze metagegevens van de audiotrack indien nodig later wijzigen of bewerken. Wanneer de video wordt gepubliceerd, worden deze details weerspiegeld op openbare URLs in gepubliceerde video&#39;s.

   1. Klik in de rechterbovenhoek van de pagina in de vervolgkeuzelijst **[!UICONTROL Save & Close]** op **[!UICONTROL Save]** .
   1. Voer een van de volgende handelingen uit:
      * Herhaal dit proces voor elk audiotrackbestand dat u uploadt.
      * Ga verder met de volgende stap om bijschriften toe te voegen aan een video.

1. Als u een of meer bijschriftbestanden aan een video wilt toevoegen, kiest u welke van de volgende gebruiksscenario&#39;s het beste bij uw scenario past:

   |  | Hoofdletters gebruiken | Te gebruiken optie Bijschrift maken |
   | --- | --- | --- |
   | **Optie 1** | Ik heb mijn eigen bestaande bijschriftbestanden die in de talen staan die ik wil gebruiken.<br> zie **Optie 1** hieronder. | **[!UICONTROL Upload Files]** |
   | **Optie 2** | Ik wil dat AI mijn bijschriftbestanden in meerdere talen genereert.<br> zie **Optie 2** hieronder. | **[!UICONTROL Convert audio tracks]** |
   | **Optie 3** | Tekst in een bijschriftbestand (`.vtt`) moet worden gecorrigeerd, opnieuw worden geüpload om het oude `.vtt` -bestand te vervangen en het gecorrigeerde bestand vervolgens door AI laten vertalen.<br> zie **Optie 3** hieronder. | **[!UICONTROL Translate caption]** |

   ![ creeer de opties van Bijschriften.](/help/assets/dynamic-media/assets/msma-createcaption.png)
   *creeer drop-down menu Bijschriften geeft u drie opties: Upload Dossiers, zet audiosporen om, en vertaal titel.*

+++**Optie 1:** *ik heb mijn eigen reeds bestaande titeldossiers die in de talen zijn die ik* (**[!UICONTROL Upload Files]** optie) wil gebruiken

   1. Klik rechtsboven op de pagina op **[!UICONTROL Create Caption]** > **[!UICONTROL Upload files]** .
   1. Navigeer naar en selecteer een of meer van uw bestaande `.vtt` -bestanden en open deze.
   1. Voor titels om op de media speler zichtbaar te zijn, moet u ** de vereiste details over *toevoegen elk* titeldossier dat u uploadt. Selecteer het potloodpictogram rechts van de bestandsnaam van een bijschrift. In **geef de dialoogdoos van de Titel** uit, ga de volgende vereiste details over het dossier in:

      | Metagegevens bijschrift | Beschrijving |
      |--- |--- |
      | Bestandsnaam | De standaardbestandsnaam wordt afgeleid van de oorspronkelijke bestandsnaam. De bestandsnaam kan alleen tijdens het uploaden worden gewijzigd en kan later niet worden gewijzigd. De vereisten voor bestandsnaamtekens zijn gelijk aan die voor AEM Assets.<br> zelfde filename kan niet voor extra titeldossiers en audiospoordossiers worden gebruikt. |
      | Taal | Selecteer de taal van het bijschrift. Nadat een bijschriftbestand is verwerkt, kan dit taalveld niet meer worden bewerkt (grijs weergegeven) |
      | Type | Selecteer het type bijschrift dat u gebruikt.<br>**Ondertitel** - de titeltekst die met de video wordt getoond die vertaalt of de dialoog transcripting.<br>**Titel** - de bijschrifttekst omvat achtergrondgeluiden, sprekersdifferentiatie, en andere relevante details, samen met dialoogvertaling of transcriptie, die toegankelijkheid voor individuen verbeteren die doof of hard zijn om te horen. |
      | Label | De tekst die voor de naam van het bijschrift wordt weergegeven in de pop-uplijst **[!UICONTROL Select audio or caption]** in de mediaspeler. Het label is wat een klant ziet die met een ondertitel of bijschrifttrack correspondeert. Bijvoorbeeld `English (CC)` . |

      U kunt de metagegevens van bijschriften indien nodig later wijzigen of bewerken. Wanneer de video wordt gepubliceerd, worden deze details weerspiegeld op openbare URLs in gepubliceerde video&#39;s.

   1. Klik in de rechterbovenhoek van de pagina in de vervolgkeuzelijst **[!UICONTROL Save & Close]** op **[!UICONTROL Save]** . De dossiers worden geupload en de meta-gegevensverwerking begint, zoals gezien in de **kolom van de Status** van de interface.

      >[!NOTE]
      >
      >Op basis van de cacheinstellingen van uw instantie kan het verwerken van metagegevens enkele minuten duren voordat dit effect wordt weerspiegeld in de voorvertoning en in gepubliceerde URL&#39;s.

   1. Als u **[!UICONTROL Save & Close]** hebt geselecteerd in de vorige stap in plaats van **[!UICONTROL Save]** te selecteren, kunt u nog steeds de verwerkingsstatus van de geüploade bestanden bekijken. Zie [ Mening de levenscyclusstatus van geupload titels en audiospoordossiers ](#lifecycle-status-video).
   1. Ga verder met stap 8.

+++

+++**Optie 2:** *ik wil AI mijn titeldossiers in veelvoudige talen* produceren (**[!UICONTROL Convert audio tracks]** optie)

   1. Klik rechtsboven op de pagina op **[!UICONTROL Create Caption]** > **[!UICONTROL Convert audio tracks]** .

      ![ zet audiosporen dialoogdoos om.](/help/assets/dynamic-media/assets/msma-convertaudiotracks.png)
      *het de dialoogvakje van de Sporen van de Audio van de Bekeerling gebruikt AI om titeldossiers in veelvoudige talen te produceren.*

   1. In **zet Audiosporen** dialoogdoos om, plaats de volgende opties:

      | Optie | Beschrijving |
      |--- |--- |
      | Om te zetten audiotrack | Kies in de vervolgkeuzelijst het geüploade audiotrackbestand waaruit u bijschriften wilt genereren met AI. |
      | Uitvoertalen | Selecteer in de vervolgkeuzelijst een of meer talen waarin u het bijschriftbestand wilt weergeven.<br> om een geselecteerde taal te verwijderen, klik **X**.<br> tijdens videoplayback, verschijnt de lijst van talen in de media speler in de orde dat u hen hier selecteert. |

   1. Klik op **[!UICONTROL Done]**.
   1. Klik in de rechterbovenhoek van de pagina in de vervolgkeuzelijst **[!UICONTROL Save & Close]** op **[!UICONTROL Save]** .
   1. Klik nogmaals op de tab **[!UICONTROL Captions & Audio tracks]** . Één of meerdere titeldossiers worden gecreeerd en de verwerking begint, zoals gezien in de **kolom van de Status** van de interface. Zie ook [ Mening de levenscyclusstatus van geupload titels en audiospoordossiers ](#lifecycle-status-video).

      >[!NOTE]
      >
      >Op basis van de cacheinstellingen van uw instantie kan het verwerken van metagegevens enkele minuten duren voordat dit effect wordt weerspiegeld in de voorvertoning en in gepubliceerde URL&#39;s.

   1. (Optioneel) Selecteer het potloodpictogram rechts van de bestandsnaam van een bijschrift. In **geef de dialoogdoos van de Titel** uit, kunt u de volgende details over het dossier uitgeven:

      | Metagegevens bijschrift | Beschrijving |
      | --- | --- |
      | Type | Selecteer het type bijschrift dat u gebruikt.<br>**Ondertitel** - de titeltekst die met de video wordt getoond die vertaalt of de dialoog transcripting.<br>**Titel** - de bijschrifttekst omvat achtergrondgeluiden en sprekersdifferentiatie. Het omvat ook andere relevante informatie, samen met de vertaling of transcriptie van de dialoog. Deze aanpak maakt de inhoud toegankelijker voor doven of slechthorenden. |
      | Label | De tekst die voor de naam van het bijschrift wordt weergegeven in de pop-uplijst **[!UICONTROL Select audio or caption]** in de mediaspeler. Het label is wat een klant ziet die met een ondertitel of bijschrifttrack correspondeert. Bijvoorbeeld `English (CC)` . |

      U kunt bepaalde metagegevens van bijschriften indien nodig later wijzigen of bewerken. Wanneer de video wordt gepubliceerd, worden deze metagegevens weerspiegeld in openbare URL&#39;s in gepubliceerde video&#39;s.
   1. Ga verder met stap 8.

+++

+++**Optie 3:** *Tekst in een titeldossier (`.vtt`) moet worden verbeterd, opnieuw geüpload om het oude `.vtt` dossier te vervangen, dan AI hebben het gecorrigeerde dossier* vertalen (**[!UICONTROL Translate captions]** optie)

   1. Klik op **[!UICONTROL Create Caption]** > **[!UICONTROL Translate captions]** . Deze optie is beschikbaar als een of meer bijschriftbestanden al zijn toegevoegd en verwerkt.

      ![ vertaal de dialoogdoos van Bijschriften.](/help/assets/dynamic-media/assets/msma-translate-captions.png)
      *het Vertaalde de dialoogvakje van Bijschriften laat u een bestaand bijschriftdossier gebruiken om AI te hebben produceren nieuwe bijschriftdossiers in veelvoudige talen.*

   1. In het **Vertaal caption** dialoogvakje, plaats de volgende opties:

      | Optie | Beschrijving |
      |--- |--- |
      | Te vertalen bijschrift | Kies in de vervolgkeuzelijst een bijschriftbestand waaruit u de bijschriften wilt genereren met behulp van AI. |
      | Uitvoertalen | Selecteer in de vervolgkeuzelijst een of meer talen waarin u het bijschriftbestand wilt weergeven.<br> om een geselecteerde taal te verwijderen, klik **X**.<br> tijdens videoplayback, verschijnt de lijst van talen in de media speler in de orde dat u hen hier selecteert. |

   1. Klik op **[!UICONTROL Done]**.
   1. Klik in de rechterbovenhoek van de pagina in de vervolgkeuzelijst **[!UICONTROL Save & Close]** op **[!UICONTROL Save]** .
   1. Klik nogmaals op de tab **[!UICONTROL Captions & Audio tracks]** . Één of meerdere titeldossiers worden gecreeerd en de verwerking begint, zoals gezien in de **kolom van de Status** van de interface. Zie ook [ Mening de levenscyclusstatus van geupload titels en audiospoordossiers ](#lifecycle-status-video).

      >[!NOTE]
      >
      >Op basis van de cacheinstellingen van uw instantie kan het verwerken van metagegevens enkele minuten duren voordat dit effect wordt weerspiegeld in de voorvertoning en in gepubliceerde URL&#39;s.

   1. (Optioneel) Selecteer het potloodpictogram rechts van de bestandsnaam van een bijschrift. In **geef de dialoogdoos van de Titel** uit, kunt u de volgende details over het dossier uitgeven:

      | Metagegevens bijschrift | Beschrijving |
      | --- | --- |
      | Type | Selecteer het type bijschrift dat u gebruikt.<br>**Ondertitel** - de titeltekst die met de video wordt getoond die vertaalt of de dialoog transcripting.<br>**Titel** - de bijschrifttekst omvat ook achtergrondgeluiden, sprekersdifferentiatie. Het omvat ook andere relevante informatie, samen met de vertaling of transcriptie van de dialoog. Deze aanpak maakt de inhoud toegankelijker voor doven of slechthorenden. |
      | Label | De tekst die voor de naam van het bijschrift wordt weergegeven in de pop-uplijst **[!UICONTROL Select audio or caption]** in de mediaspeler. Het label is wat een klant ziet die met een ondertitel of bijschrifttrack correspondeert. Bijvoorbeeld `English (CC)` . |

      U kunt bepaalde metagegevens van bijschriften indien nodig later wijzigen of bewerken. Wanneer de video wordt gepubliceerd, worden deze metagegevens weerspiegeld in openbare URL&#39;s in gepubliceerde video&#39;s.

   1. Ga verder met stap 8.

+++

1. (Optioneel) Geef een voorvertoning van de video weer voordat u de video publiceert, zodat de bijschriften en audio naar behoren werken. Zie [ Voorproef een video die veelvoudige titels en audiosporen ](#preview-video-audio-subtitle) heeft.
1. Publish the video. Zie [ de activa van Publish ](publishing-dynamicmedia-assets.md).

#### Bijschrift- en audiotrackbestanden toevoegen aan een video die al is gepubliceerd

Na het uploaden van extra bijschrift of audiotrackbestanden naar een gepubliceerde video, hebben deze bestanden de status `Processed` nadat ze zijn voorbereid. Vervolgens kunt u de video voorvertonen in Dynamic Media om de nieuwe bestanden te bekijken of te horen.

Na voorproef, echter, moet u *de video opnieuw voor de onlangs toegevoegde titel of audiospoordossiers publiceren die, ook moeten worden gepubliceerd.* Na publicatie worden de bijschriften of audio beschikbaar via de openbare Dynamic Media-URL.

>[!NOTE]
>
>Op basis van de cacheinstellingen van uw instantie kunnen updates van metagegevens enkele minuten duren voordat deze worden weergegeven in de voorvertoning en in gepubliceerde URL&#39;s.

In het scenario waarin u Dynamic Media hebt geconfigureerd voor direct publiceren, wordt door het uploaden van extra bijschrift- of audiobestanden direct een publicatie van de video gestart na het uploaden van bijschrift- of audiobestanden.

>[!CAUTION]
>
>Wanneer u titeldossiers of audiodossiers aan een video uploadt die of gepubliceerd of unpublished is, worden de dossiers geschrapt als u [**](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) de video opnieuw verwerkt. Alleen de oorspronkelijke audio van de video blijft intact. In dergelijke gevallen moet u de bijschriftbestanden en audiotrackbestanden opnieuw uploaden naar de video.

#### Meerdere bijschriften toevoegen aan een video met een bestaande URL met bijschriftoptie

Dynamic Media ondersteunt het toevoegen van één bijschrift met video via een URL-modifier. Zie [ titels aan video ](#adding-captions-to-video) toevoegen.

Meerdere bijschriftwijzigingen hebben voorrang op een bijschrift dat is toegevoegd via een URL-modifier voor gepubliceerde video&#39;s.

**om veelvoudige titels aan een video toe te voegen die bestaande URL met titelbepaling heeft:**

1. Upload het bijschriftbestand dat al als een modifier aan de video is toegevoegd, zodat u het bestand expliciet kunt beheren.
1. U kunt desgewenst aanvullende bijschriftbestanden uploaden.
1. Publish de video zoals gewoonlijk.
De bestaande URL met de optie caption kan nu meerdere bijschriften laden.

### De levenscyclusstatus van geüploade bijschriften en audiotrackbestanden weergeven {#lifecycle-status-video}

U kunt de levenscyclusstatus bekijken van elk bijschrift of audiotrackbestand dat naar uw primaire video is geüpload. U kunt dit van **Bijschriften &amp; Audiosporen** lusje van **Eigenschappen** doen.

**om de levenscyclusstatus van een video te bekijken:**

1. Navigeer naar het video-element waarvan u de levenscyclusstatus wilt weergeven.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram Eigenschappen (een cirkel met een &quot;i&quot; erin).
1. Selecteer op de pagina Eigenschappen de tab **[!UICONTROL Captions & Audio Tracks]** . Noteer in de kolom Status de status van elk bijschrift of audiobestand.

| Status bijschrift of audiotrack | Beschrijving |
| --- | --- |
| Verwerking | Wanneer een nieuw bijschrift of audiotrackbestand wordt toegevoegd en opgeslagen, verandert dit in de status &quot;Verwerking&quot;. Dynamic Media verwerkt het bestand door het streamingmanifest aan de primaire video te koppelen. |
| Verwerkt | Nadat de verwerking is voltooid, worden het bijschrift of audiotrackbestand, of de oorspronkelijke audiotrack die is gekoppeld aan de primaire video, weergegeven in de status &quot;Verwerkt&quot;. U kunt voorproef titel en audiospoordossiers die als &quot;Bewerkt&quot;*verschijnen alvorens* u de video live publiceert. |
| Gepubliceerd | De status &quot;Gepubliceerd&quot; vertegenwoordigt een vergelijkbare status als &quot;Gepubliceerd&quot; voor een primaire video. Assets wordt gepubliceerd wanneer de primaire video wordt gepubliceerd en is beschikbaar op de openbare URL van Dynamic Media. |
| Mislukt | De status &quot;Mislukt&quot; betekent dat de verwerking van een bijschrift of audiotrackbestand niet is voltooid. Verwijder het bijschrift of het audiotrackbestand en upload het opnieuw. |
| Ongepubliceerd | Wanneer een gepubliceerde primaire video niet expliciet wordt gepubliceerd, worden alle bijschriften of audiotrackbestanden die u aan de video hebt toegevoegd, ook niet gepubliceerd. |

![ de kolom van de Status die voor de gebieden van de Sporen van de Ondertitels en Audio wordt benadrukt.](/help/assets/dynamic-media/assets/msma-lifecycle-status.png)*de status van de levenscyclus van elk geupload caption en audiospoordossier.*

### De standaardaudio instellen voor een video met meerdere audiotracks

Standaard wordt de oorspronkelijke audio van een video ingesteld als de standaardaudio die moet worden afgespeeld.

Geüploade audiotrackbestanden kunnen echter worden ingesteld als de standaardaudio die moet worden afgespeeld nadat een video in de viewer is geladen. In het gebruikersinterface van Eigenschappen, onder het **Bijschriften &amp; Audiosporen** lusje, wordt het `Default` etiket toegepast rechts van het audiospoordossier voor videoplayback.

>[!NOTE]
>
>Het afspelen van standaardaudio kan ook afhankelijk zijn van de instelling in de volgende browsers:
>
>* Chrome - De standaardaudio die in de video is ingesteld, wordt afgespeeld.
>* Safari - Als de standaardtaal in Safari is ingesteld, wordt audio afgespeeld met de ingestelde standaardtaal, mits deze beschikbaar is met het manifest van de video. Anders wordt de standaardaudio afgespeeld die is ingesteld als onderdeel van de eigenschappen van een video.

**om de standaardaudio voor een video te plaatsen die veelvoudige audiosporen heeft:**

1. Navigeer naar het video-element waarvan u de standaardaudiotrack wilt instellen.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram Eigenschappen (een cirkel met een &quot;i&quot; erin).
1. Selecteer op de pagina Eigenschappen de tab **[!UICONTROL Captions & Audio Tracks]** .
1. Onder de **Audiosporen** rubriek, selecteer het audiospoordossier dat u als gebrek van de video wilt plaatsen.
1. Selecteer **[!UICONTROL Set as default]** .
In de **Reeks als standaard** dialoogdoos, uitgezochte **[!UICONTROL Replace]**.

   ![ de rubriek van Audiosporen met een geselecteerde audiospoordossier - naam en benadrukte &quot;Reeks als gebrek&quot;knoop.](/help/assets/dynamic-media/assets/msma-defaultaudiotrack.png)*plaatsend het standaard audiospoor voor een video.*

1. Selecteer **[!UICONTROL Save & Close]** in de rechterbovenhoek.
1. Publish the video. Zie [ de activa van Publish ](publishing-dynamicmedia-assets.md).

### Een voorvertoning weergeven van een video met meerdere bijschriften en audiotracks {#preview-video-audio-subtitle}

Nadat bijschriftbestanden en audiotrackbestanden naar een video zijn geüpload en zijn verwerkt, kunt u met de Dynamic Media-videoviewer een voorvertoning van alle verschillende tracks weergeven. Zo kunt u zien hoe de video er uitziet en hoe de video er voor de klant uitziet en zorgt u ervoor dat de video zich naar behoren gedraagt.

Wanneer u met de video wordt tevreden, kunt u het ](publishing-dynamicmedia-assets.md) publiceren gebruikend om het even welke volgende methodes.[

Zie [ de Video of Kijker van het Beeld op een Web-pagina ](/help/assets/dynamic-media/embed-code.md) inbedden.
Zie [ Verbinding URLs aan uw Webtoepassing ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.
Zie [ Dynamic Media Assets aan pagina&#39;s ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md) toevoegen.

>[!NOTE]
>
>Op het standaardtabblad Voorvertoning van Experience Manager worden niet meerdere bijschriften en audiotracks weergegeven. De reden hiervoor is dat deze tracks zijn gekoppeld aan Dynamic Media en alleen kunnen worden weergegeven met de voorvertoning van de Dynamic Media Viewer.

**aan voorproef een video die veelvoudige titels en audiosporen heeft:**

1. Navigeer in **[!UICONTROL Assets]** naar een bestaande video waaraan u meerdere bijschriften en audiotracks hebt toegevoegd.
1. Klik op het video-element zodat u dit kunt openen in de voorvertoningsmodus.
1. Selecteer op de voorvertoningspagina, linksboven op de pagina, de vervolgkeuzelijst en selecteer vervolgens **[!UICONTROL Viewers]** .

   ![ drop-down lijst die de optie van Kijkers toont.](/help/assets/dynamic-media/assets/msma-selectviewers.png)

1. Selecteer in de lijst Viewers een viewer die u wilt gebruiken voor de videovoorvertoning. In de volgende schermafbeelding ziet u bijvoorbeeld hoe de **[!UICONTROL Video]** -viewer wordt geselecteerd.

   ![ Selectie van de Videokijker van de drop-down lijst van Kijkers.](/help/assets/dynamic-media/assets/msma-dmviewerselected.png)

1. Selecteer bij de rechterbenedenhoek, links van het volumepictogram, het pictogram van de spraakballon en selecteer vervolgens de audio of het bijschrift die u wilt horen, of zien of beide. U kunt desgewenst onder Bijschriften de weergave van bijschriften uitschakelen door op **[!UICONTROL Off]** te klikken.

   ![ de Audio en de Pop-up lijst van Bijschriften in de Videokijker.](/help/assets/dynamic-media/assets/msma-selectaudiosubtitle.png)*Simulatie van een gebruiker die de audio en de titel voor videoplayback selecteren.*

1. Selecteer de knop **[!UICONTROL Play]** van de video om het afspelen te starten.
Noteer de knoppen **[!UICONTROL URL]** en **[!UICONTROL Embed]** in de linkerbenedenhoek. Gebruik deze knopen aan [ verbinding URL van de video aan uw Webtoepassing ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) of [ bed de video op een Web-pagina ](/help/assets/dynamic-media/embed-code.md) in, respectievelijk.
1. Selecteer **[!UICONTROL Close]** in de rechterbovenhoek van de voorvertoningspagina.

### Bijschrift- of audiotrackbestanden verwijderen uit een video

U kunt bijschrift- of audiotrackbestanden verwijderen uit een video. Het verwijderen van gepubliceerde bijschriften of audiotrackbestanden wordt automatisch weerspiegeld in de gepubliceerde URL van de video.

De oorspronkelijke audiotrack die uit een primaire video is geëxtraheerd, kan niet worden verwijderd.

**om titel of audiospoordossiers van een video te schrappen:**

1. Navigeer naar het video-element waarvan u de standaardaudiotrack wilt instellen.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram Eigenschappen (een cirkel met een &quot;i&quot; erin).
1. Selecteer op de pagina Eigenschappen de tab **[!UICONTROL Captions & Audio Tracks]** .
1. Voer een van de volgende handelingen uit:

   * Bijschriften - onder de **rubriek van de Bijschriften**, selecteer één of meerdere titeldossiers die u van de video wilt schrappen, dan **[!UICONTROL Delete]** klikken.
   * De AudioSporen - onder de **AudioKeuren** rubriek, selecteer één of meerdere audiospoordossiers die u van de video wilt schrappen, dan klik **[!UICONTROL Delete]**.

1. Klik in het dialoogvenster Verwijderen op **[!UICONTROL OK]** .
1. Publish the video.

### Bijschrift- of audiotrackbestanden downloaden die naar een video zijn geüpload

U kunt elk bijschrift of elke audiotrack downloaden die u voor een video hebt geüpload. U kunt alle geselecteerde bestanden downloaden als een `.zip` of een aparte downloadmap maken voor elk bestand.

De oorspronkelijke audiotrack die uit een primair videobestand is gehaald, kan niet worden gedownload.

**geval van het Gebruik:** het downloaden van een titeldossier zou noodzakelijk kunnen zijn als u een fout in a `.vtt` dossier vindt. U hoeft alleen het onjuiste `.vtt` -bestand te downloaden, het bestand te openen in een teksteditor zonder opmaak en de correcties aan te brengen. Nadat u het `.vtt` -bestand hebt opgeslagen, uploadt u het opnieuw. Gebruik vervolgens de optie **[!UICONTROL Translate Captions]** om het gecorrigeerde `.vtt` -bestand opnieuw te vertalen.

**om titel of audiospoordossiers te downloaden die aan een video werden geupload:**

1. Navigeer naar het video-element waarvan u de standaardaudiotrack wilt instellen.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram Eigenschappen (een cirkel met een &quot;i&quot; erin).
1. Selecteer op de pagina Eigenschappen de tab **[!UICONTROL Captions & Audio Tracks]** .
1. Voer een van de volgende handelingen uit:

   * Bijschriften - onder de **rubriek van de Bijschriften**, selecteer één of meerdere titeldossiers die u van de video wilt downloaden, dan selecteren **[!UICONTROL Download]**.
   * De AudioSporen - onder de **AudioKeuren** rubriek, selecteer één of meerdere audiospoordossiers die u van de video wilt downloaden, dan selecteren **[!UICONTROL Download]**.

1. Stel in het dialoogvenster Downloaden de volgende opties in:

   | Optie | Beschrijving |
   |--- |--- |
   | Opslaan als | Gebruik de standaardbestandsnaam die u in het tekstveld Opslaan als hebt opgegeven of geef uw eigen naam op. |
   | Een aparte map maken voor elk element | Maak een map voor elk bijschriftbestand of audiotrackbestand dat u hebt geselecteerd om te downloaden. |
   | E-mail | Gebruik uw standaard e-mailprogramma om het .zip-bestand naar een opgegeven e-mailadres te verzenden. |
   | Assets | Hiermee geeft u het aantal bestanden op dat u downloadt en de gecombineerde totale grootte van alle geselecteerde bestanden. Als u deze optie uitschakelt, wordt de knop **[!UICONTROL Download]** gedimd (uitgeschakeld), zodat u geen bestand kunt downloaden. |

1. Selecteer **[!UICONTROL Download]** .
1. Publish the video. Zie [ de activa van Publish ](publishing-dynamicmedia-assets.md).

<!-- ## About AI-generated captions for videos in Dynamic Media

AI-powered captions in Dynamic Media are designed to enhance video accessibility and engagement by automatically generating accurate and synchronized subtitles. This technology uses advanced AI algorithms to transcribe spoken content into text, which is then displayed as captions on the video. Here are some key features.

* **Automatic Transcription:** The AI system transcribes spoken words from an existing audio file into text in real-time, ensuring that captions are generated quickly and accurately.
* **Multilingual Support:** It supports more than 60 languages, making it easier to reach a global audience. You can even translate your existing captions to different languages.
* **Enhanced Accessibility:** By providing captions, videos become more accessible to viewers who are deaf or hard of hearing, as well as those who prefer to watch videos with the sound off.
* **Improved Engagement:** Captions can help retain viewer attention and improve comprehension, especially in noisy environments or when the viewer's native language is different from the video's language.

These features in Dynamic Media make AI-powered video aptions a valuable tool for content creators looking to enhance their video content's accessibility and engagement. -->

## Gesloten bijschriften toevoegen aan video {#adding-captions-to-video}

>[!IMPORTANT]
>
>De Adobe adviseert dat u [ veelvoudige titel en audiospoorvermogen ](#enable-dash) op uw rekening van Dynamic Media toelaat. Zo kunt u profiteren van de nieuwste Dynamic Media-backendarchitectuur en een vereenvoudigde workflow voor het toevoegen van bijschriften, bijschriften en audiotracks aan uw video&#39;s.

U kunt het bereik van uw video&#39;s uitbreiden naar wereldwijde markten door ondertiteling toe te voegen aan enkele video&#39;s of aan Adaptive Video Sets. Door ondertiteling toe te voegen, vermijdt u de behoefte om de audio te duwen, of de behoefte om inheemse sprekers te gebruiken om de audio voor elke verschillende taal opnieuw op te nemen. De video wordt afgespeeld in de taal waarin deze is opgenomen. Bijschriften in vreemde talen worden weergegeven zodat mensen in verschillende talen het audiogedeelte nog steeds kunnen begrijpen.

Ondertiteling met gesloten deuren zorgt ook voor betere toegankelijkheid voor doven of slechthorenden.

>[!NOTE]
>
>De videospeler die u gebruikt moet de vertoning van gesloten titels steunen.

Zie ook [ Toegankelijkheid in Dynamic Media ](/help/assets/dynamic-media/accessibility-dm.md).

Dynamic Media kan bijschriftbestanden omzetten in de indeling JSON (JavaScript Object Notation). Met deze conversie kunt u de JSON-tekst insluiten in een webpagina als een verborgen, maar volledige transcriptie van de video. Zoekprogramma&#39;s kunnen de inhoud dan verkennen of indexeren, zodat de video&#39;s gemakkelijker te vinden zijn en klanten meer informatie krijgen over de video-inhoud.

Zie [ Servend statische (niet beeld) inhoud ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents#image-serving-api) voor meer informatie over het gebruiken van de functie JSON in een URL.

**om titels aan een video toe te voegen:**

1. U kunt een toepassing of service van derden gebruiken om uw videobijschriftbestand te maken.

   Zorg ervoor dat het bestand dat u maakt, voldoet aan de WebVTT-standaard (Web Video Text Track). De bestandsnaamextensie voor ondertiteling is `.vtt` . U kunt meer informatie over de WebVTT ondertitelingsnorm leren.

   Zie [ WebVTT: Het formaat van de Tracks van de Tekst van het Web Video ](https://w3c.github.io/webvtt/).

   Er zijn veel websites die zowel gratis als premiumtools en -services bieden die u kunt gebruiken om WebVTT-bijschriftbestanden te maken buiten Dynamic Media. <!-- THE FOLLOWING LINK IS NO LONGER LIVE. CHECKED DECEMBER 13, 2023 For example, to create a simple video caption file with no styling, you can use the following free online caption authoring and editing tool: -->

   <!-- [WebVTT Caption Maker](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   For best results, use the tool in Internet Explorer 9 or above, Google Chrome, or Safari.

   In the tool, in the **[!UICONTROL Enter URL of video file]** field, paste the copied URL of your video file and then select **[!UICONTROL Load]**. See [Obtain a URL for an Asset](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) to get the URL to the video file itself which you can then paste into the **[!UICONTROL Enter URL of video file field]**. Internet Explorer, Chrome, or Safari can then natively play back the video.-->

Volg de aanwijzingen op het scherm van een site om het WebVTT-bestand te ontwerpen en op te slaan. Wanneer u klaar bent, kopieert u de inhoud van het bijschriftbestand en plakt u deze in een teksteditor zonder opmaak en slaat u het bestand op met de bestandsnaamextensie VTT.

>[!NOTE]
>
>Voor algemene ondersteuning van videobijschriften in meerdere talen vereist de WebVTT-standaard dat u afzonderlijke `.vtt` bestanden maakt en aanroepen voor elke taal die u wilt ondersteunen.

Over het algemeen wilt u het bijschriftbestand `.vtt` dezelfde naam geven als het videobestand en het bestand toevoegen met de landinstelling van de taal, zoals -EN, of -FR of -DE. Hierdoor kunt u de generatie van video-URL&#39;s automatiseren met uw bestaande WCM-systeem.

1. Upload in Experience Manager uw WebVTT-bijschriftbestand naar DAM.
1. Navigeer aan *gepubliceerde* videoactiva om het met het titeldossier te associëren dat u uploadde.

   Houd er rekening mee dat URL&#39;s alleen beschikbaar zijn om te kopiëren *nadat* u de assets eerst hebt *gepubliceerd*.

   Zie [ de activa van Publish ](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

1. Voer een van de volgende handelingen uit:

   * Klik op de knop **[!UICONTROL URL]** voor een pop-upviewerbeleving. Selecteer in het dialoogvenster URL de URL en kopieer deze naar het Klembord en passeer de URL naar een eenvoudige teksteditor. Voeg de gekopieerde URL van de video toe met de volgende syntaxis:

     `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

     Noteer de `,1` aan het einde van het bijschriftpad. Onmiddellijk na de VTT-bestandsnaamextensie in het pad kunt u optioneel de knop voor een gesloten bijschrift op de videospelerbalk in- of uitschakelen (uitschakelen) door deze in te stellen op respectievelijk `,1` of `,0` .

   * Selecteer **[!UICONTROL Embed Code]** voor een ingesloten videoviewerervaring. Selecteer in het dialoogvenster Code insluiten de insluitcode en kopieer deze naar het klembord. Plak de code vervolgens in een eenvoudige teksteditor. Voeg de gekopieerde insluitcode toe met de volgende syntaxis:

     `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

     Noteer de `,1` aan het einde van het bijschriftpad. Onmiddellijk na de VTT-bestandsnaamextensie in het pad kunt u optioneel de knop voor een gesloten bijschrift op de videospelerbalk in- of uitschakelen (uitschakelen) door deze in te stellen op respectievelijk `,1` of `,0` .

## Hoofdstukmarkeringen aan video toevoegen {#adding-chapter-markers-to-video}

U kunt lange-vormvideo&#39;s gemakkelijker bekijken en navigeren door hoofdstukmarkeringen toe te voegen aan enkele video&#39;s of aan Adaptieve videosets. Wanneer een gebruiker de video afspeelt, kunnen deze de hoofdstukmarkeringen op de videotijdlijn selecteren (ook wel de videoscrubber genoemd). Ze kunnen gemakkelijk naar hun interesse gaan of meteen naar nieuwe inhoud, training en demonstraties gaan.

>[!NOTE]
>
>De videospeler die wordt gebruikt moet het gebruik van hoofdstukmarkeringen steunen. Dynamic Media-videospelers ondersteunen wel hoofdstukmarkeringen, maar het gebruik van videospelers van derden is mogelijk niet mogelijk.

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

In het bovenstaande voorbeeld is `Chapter 1` de cue-id en optioneel. De actieduur van `00:00:000 --> 01:04:364` geeft de begin- en eindtijd van het hoofdstuk op in de `00:00:000` -indeling. Deze laatste drie cijfers zijn milliseconden en kunnen desgewenst als `000` worden verlaten. De hoofdstuktitel van `The bicycle store behind it all` is de feitelijke beschrijving van de inhoud van het hoofdstuk. De actidentificator, de begintijd en de hoofdstuktitel worden allemaal in een pop-up in de videospeler weergegeven wanneer een gebruiker de muisaanwijzer boven een visueel actiepunt in de tijdlijn plaatst.

Omdat u een HTML5-videoviewer gebruikt, moet u ervoor zorgen dat het hoofdstukbestand dat u maakt, voldoet aan de WebVTT-standaard (Web Video Text Tracks). De bestandsextensie van het hoofdstuk is `.vtt` . U kunt meer informatie over de WebVTT ondertitelingsnorm leren.

Zie [ WebVTT: Het formaat van de Tracks van de Tekst van het Web Video ](https://w3c.github.io/webvtt/).

**om hoofdstuktellers aan een video toe te voegen:**

1. Sla het `.vtt` -bestand op in UTF8-codering, zodat u problemen met tekenuitvoering in de hoofdstuktiteltekst voorkomt.

   Over het algemeen wilt u het hoofdstuk VTT-bestand dezelfde naam geven als het videobestand en het toevoegen met hoofdstukken. Hierdoor kunt u de generatie van video-URL&#39;s automatiseren met uw bestaande WCM-systeem.
1. Upload in Experience Manager uw WebVTT-hoofdstukbestand.

   Zie [ activa ](/help/assets/manage-digital-assets.md#uploading-assets) uploaden.

1. Voer een van de volgende handelingen uit:

   <table>
     <tbody>
      <tr>
       <td>Voor een viewerervaring voor pop-upvideo's</td>
       <td>
       <ol>
       <li>Navigeer aan <i> gepubliceerde </i> videoactiva om het met het hoofdstukdossier te associëren dat u uploadde. Houd er rekening mee dat URL's alleen beschikbaar zijn om te kopiëren <i>nadat</i> u de assets eerst hebt <i>gepubliceerd</i>. Zie <a href="/help/assets/dynamic-media/publishing-dynamicmedia-assets.md"> het Publiceren Assets.</a></li>
       <li>Van het drop-down menu, dan uitgezochte <strong> Kijkers </strong>.</li>
       <li>Selecteer in de linkertrack de naam van de voorinstelling voor de videoviewer. Er wordt een voorvertoning van de video geopend op een aparte pagina.</li>
       <li>In het linkerspoor, bij de bodem, klik de <strong> URL </strong> knoop.</li>
       <li>Selecteer in het dialoogvenster URL de URL en kopieer deze naar het Klembord. Plak vervolgens de URL in een eenvoudige teksteditor.</li>
       <li>Voeg de gekopieerde URL van de video toe aan de volgende syntaxis, zodat u deze kunt koppelen aan de gekopieerde URL naar het hoofdstukbestand: <br /> <br /> <code>&navigation=<<i>full_copied_URL_path_to_chapter_file</i>.vtt></code><br /> </li>
       </ol> </td>
      </tr>
      <tr>
       <td>Voor een ingebedde videokijkervaring, <br /> </td>
       <td>
       <ol>
       <li>Navigeer aan <i> gepubliceerde </i> videoactiva om het met het hoofdstukdossier te associëren dat u uploadde. Houd er rekening mee dat URL's alleen beschikbaar zijn om te kopiëren <i>nadat</i> u de assets eerst hebt <i>gepubliceerd</i>. Zie <a href="/help/assets/dynamic-media/publishing-dynamicmedia-assets.md"> het Publiceren Assets.</a></li>
       <li>Van het drop-down menu, dan uitgezochte <strong> Kijkers </strong>.</li>
       <li>Selecteer in de linkertrack de naam van de voorinstelling voor de videoviewer. Er wordt een voorvertoning van de video geopend op een aparte pagina.</li>
       <li>In het linkerspoor, bij de bodem, selecteer <strong> bed </strong> in.</li>
       <li>Selecteer in het dialoogvenster Code insluiten de gehele code en kopieer deze naar het klembord. Plak de code vervolgens in een eenvoudige teksteditor.</li>
       <li>Voeg de insluitcode van de video toe aan de volgende syntaxis, zodat u deze kunt koppelen aan de gekopieerde URL naar het hoofdstukbestand:<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt>"</code></li>
       </ol> </td>
      </tr>
     </tbody>
   </table>



## Videominiaturen {#about-video-thumbnails}

Een videominiatuur is een verkleinde versie van een videoframe of een afbeeldingselement dat de video voor de klant vertegenwoordigt. De miniatuur moet de klant aanmoedigen om de video te selecteren.

Aan alle video&#39;s in de Experience Manager moet een miniatuur zijn gekoppeld. Wanneer u een video uploadt naar Experience Manager, wordt standaard het eerste frame gebruikt als miniatuur. U kunt de miniatuur echter aanpassen voor brandingdoeleinden of visuele zoekopdracht. Wanneer u een videominiatuur aanpast, kunt u de video afspelen en pauzeren op het frame dat u wilt gebruiken. Of, kunt u een beeldactiva selecteren die u reeds hebt geupload en *gepubliceerd* in uw digitale activamanager.

Wanneer de miniatuur voor een video wordt gewijzigd, wordt het genereren van miniaturen via de Asset compute Service bij het opnieuw verwerken van de video overgeslagen.

De mogelijkheid om een videominiatuur aan te passen is alleen beschikbaar nadat u een videoprofiel hebt toegepast op de map waarin de video zich bevindt.

### Een aangepaste videominiatuur toevoegen {#adding-a-custom-video-thumbnail}

1. Zorg ervoor dat u al het volgende hebt gedaan:

   * Er is een map gemaakt voor uw video-elementen.
   * [ paste een videoprofiel op de omslag ](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders) toe.

   * [ uploadde uw video&#39;s aan de omslag ](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).

1. Navigeer naar een geüpload video-element waarvan u de miniatuurafbeelding wilt wijzigen.
1. Selecteer het video-element in de modus voor middelenselectie van **[!UICONTROL List View]** of **[!UICONTROL Card View]** .
1. Selecteer op de werkbalk het pictogram **[!UICONTROL Properties]** (een cirkel met een &quot;i&quot; erin).
1. Selecteer **[!UICONTROL Change Thumbnail]** op de pagina Eigenschappen van video.
1. Voer een van de volgende handelingen uit op de pagina Miniatuur wijzigen:

   * Een frame uit de video gebruiken als de nieuwe miniatuur:

      * Klik op de werkbalk op de optie **[!UICONTROL Select Frame from video]** .
      * Selecteer de knop Afspelen en selecteer vervolgens de knop Pauzeren in het frame dat u wilt vastleggen als de nieuwe miniatuur van de video.

   * Een afbeeldingselement gebruiken als de nieuwe miniatuur:

      * Selecteer **[!UICONTROL Select Thumbnail from Assets]** op de werkbalk.
      * Selecteer **[!UICONTROL Select Thumbnail]** .
      * Navigeer naar een eerder geüpload en gepubliceerd afbeeldingselement dat u wilt gebruiken. De grootte van het element wordt automatisch gewijzigd om te dienen als miniatuurafbeelding voor de video.
      * Selecteer het afbeeldingselement en selecteer vervolgens **[!UICONTROL Select]** .

1. Selecteer **[!UICONTROL Save Change]** op de pagina Miniatuur wijzigen.
1. Selecteer **[!UICONTROL Save & Close]** in de rechterbovenhoek van de pagina Eigenschappen van video.



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

   If you configured new default time intervals, or you uploaded a new video to replace the existing video, you need to have Dynamic Media regenerate the thumbnails.

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

1. On the lower-right panel, in the Properties tab, double-select `thumbnailtime`.
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

## De Dynamic Media-URL voor Dynamic Media-elementen wijzigen

Buiten-de-box viewers kunnen video&#39;s afspelen die in Dynamic Media zijn verwerkt. U kunt ze ook afspelen door rechtstreeks toegang te krijgen tot de manifest-URL&#39;s en uw eigen aangepaste viewers te gebruiken. Hier volgt de API voor het ophalen van manifest-URL&#39;s voor een video.

### Over de getVideoManifestURI-API

`getVideoManifestURI` API wordt blootgesteld door c `q-scene7-api:com.day.cq.dam.scene7.api` en kan worden gebruikt om volgende manifest URLs te produceren:

```java
/**   
* Returns the manifest url for videos 
* @param resource video resource 
* @param manifestType type of video streaming manifest being requested 
* @param onlyIfPublished return a manifest only if the video is published 
* @return the manifest url for videos 
* 
* @throws Exception 
*/
@Nullable 
String getVideoManifestURI(Resource resource, ManifestType manifestType, boolean onlyIfPublished) throws Exception;
```

#### getVideoManifestURI API-parameters

Deze API heeft de volgende drie parameters:

| Parameter | Beschrijving |
| --- | --- |
| `resource` | De bron die correspondeert met de video die Dynamic Media heeft gegeten. |
| `manifestType` | Kan `ManifestType.DASH` of `ManifestType.HLS` zijn |
| `onlyIfPublished` | Ingesteld op true voor het geval dat de manifest-uri alleen wordt gegenereerd als deze wordt gepubliceerd en beschikbaar is op de leveringslaag. |

Om manifest URLs voor video&#39;s te halen die de methode hierboven gebruiken, voeg a [ video het coderen profiel ](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) aan een &quot;upload video&quot;omslag toe. Dynamic Media verwerkt deze video&#39;s op basis van de coderingen in het videocoderingsbestand dat aan de map is toegewezen. Nu kunt u de bovenstaande API aanroepen voor het ophalen van manifest-URL&#39;s voor de geüploade video&#39;s.

### Foutscenario&#39;s

De API retourneert null als er fouten zijn. Uitzonderingen worden geregistreerd in foutenlogboeken voor Experience Managers. Dergelijke geregistreerde fouten beginnen met `Could not generate Video Manifest URI`. Dergelijke fouten kunnen in de volgende scenario&#39;s optreden:

* Een `IllegalArgumentException` wordt geregistreerd voor om het even welke volgend:

   * De doorgegeven parameter `resource` is null.
   * De doorgegeven parameter `resource` is geen video.
   * De doorgegeven parameter `manifestType` is null.
   * De parameter `onlyIfPublished` wordt doorgegeven als true, maar de video wordt niet gepubliceerd.
   * De video is niet opgenomen met een adaptieve videoset uit Dynamic Media.

* `IOException` wordt geregistreerd als er een probleem is met de verbinding met Dynamic Media.
* `UnsupportedOperationException` wordt geregistreerd wanneer een doorgegeven `manifestType` parameter `ManifestType.DASH` is, terwijl de video niet is verwerkt met de DASH-indeling.

<!-- THE REMAINING SECTION IS FOR 6.5 ONLY 

The following is an example of the above API using servlets written in *HTTPWhiteBoard* specification. Select each tab for the code syntax.

>[!BEGINTABS]

>[!TAB Add dependency in pom.xml]

+++**Add dependency in pom.xml** 

```java
dependency> 
     <groupId>com.day.cq.dam</groupId> 
     <artifactId>cq-scene7-api</artifactId> 
     <version>5.12.64</version> 
     <scope>provided</scope> 
</dependency> 
```

+++

>[!TAB Sample servlet]

+++**Sample servlet** 

```java
@Component
        service = Servlet.class 
) 
@HttpWhiteboardServletPattern(value = ManifestServlet.SERVLET_PATTERN) 
@HttpWhiteboardContextSelect(value = Constants.SERVLET_CONTEXT_SELECTOR) 
public class ManifestServlet extends HttpServlet { 

   private static final Logger LOGGER = LoggerFactory.getLogger(ManifestServlet.class); 

   private final ObjectMapper objectMapper; 

    @Reference 
    private Scene7Service scene7Service; 

   public static final String SERVLET_PATTERN = Constants.VIDEO_API_PREFIX + "/manifestUrl"; 

   public ManifestServlet() {
         this.objectMapper = new ObjectMapper(); 
         objectMapper.setSerializationInclusion(JsonInclude.Include.NON_NULL); 
   }

   @Override 

   protected void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException {
        final ResourceResolver resolver = getResourceResolver(request); 
        String assetPath = request.getParameter("assetPath"); 
        String manifest = request.getParameter("manifestType"); 
        String onlyIfPublished = request.getParameter("onlyIfPublished"); 
        Resource resource = resolver.getResource(assetPath); 
        response.setCharacterEncoding(StandardCharsets.UTF_8.toString()); 
        response.setContentType("application/json"); 
        if(resource == null) { 
            LOGGER.info("could not retrieve the resource from JCR"); 
            error("could not retrieve the resource from JCR", response); 
            return; 
        }

        String manifestUri = null; 

        try{ 
            ManifestType manifestType =  ManifestType.DASH; 
            if(manifest != null) { 
                manifestType = ManifestType.valueOf(manifest); 
            } 
            manifestUri = scene7Service.getVideoManifestURI(resource, manifestType, onlyIfPublished != null); 
            objectMapper.writeValue(response.getWriter(), new ManifestUrl(manifestUri)); 
            response.setContentType("application/json"); 
        } catch (Exception e) { 
            LOGGER.error(e.getMessage(), e); 
            error(String.format("Unable to get the manifest url for %s. %s", assetPath, e.getMessage()), response); 
        } 
    } 

    private ResourceResolver getResourceResolver(HttpServletRequest request) { 
        Object rr = request.getAttribute(AuthenticationSupport.REQUEST_ATTRIBUTE_RESOLVER); 
        if (!(rr instanceof ResourceResolver)) { 
            throw new IllegalStateException( 
                    "The request does not seem to have been created via Apache Sling's authentication mechanism."); 
        } else { 
            return (ResourceResolver) rr; 
        } 
    } 

    private void error(String errorMessage, HttpServletResponse response) throws IOException { 
        ManifestUrl errorManifest = new ManifestUrl(null); 
        errorManifest.setErrorMessage(errorMessage); 
        response.setStatus(HttpServletResponse.SC_INTERNAL_SERVER_ERROR); 
        objectMapper.writeValue(response.getWriter(), errorManifest); 
    } 
} 
```

+++

>[!TAB Response Class for servlet]

+++**Response Class for servlet** 

```java
public class ManifestUrl extends VideoResponse { 
     String manifestUrl; 
     public ManifestUrl(String manifestUrl) { 
         this.manifestUrl = manifestUrl; 
     } 
     public String getManifestUrl() { 
         return manifestUrl; 
     } 
} 

public abstract class VideoResponse { 
     String errorString; 

     public String getErrorString() { 
         return errorString; 
     } 

     public void setErrorMessage(String errorString) { 
         this.errorString = errorString; 
     } 
} 
```

+++

>[!TAB Constants file referenced in servlet]

+++**Constants file referenced in servlet** 

```java
public final class Constants { 

     private Constants() { 
     } 

     public static final String VIDEO_API_PREFIX = "/dynamicmedia/video"; 
     public static final String SERVLET_CONTEXT_SELECTOR = "(" + HttpWhiteboardConstants.HTTP_WHITEBOARD_CONTEXT_NAME + "=" + 
             DMSampleApiHttpContext.CONTEXT_NAME + ")"; 

 } 
```

+++

>[!TAB ServletContext]

+++**ServletContext** 

Mount the above servlet using a `servletContext`. The following is an example of `servletContext`. 

```java
public class DMSampleApiHttpContext extends ServletContextHelper { 

 public static final String CONTEXT_NAME = "com.adobe.dmSample"; 
 public static final String CONTEXT_PATH = "/dmSample"; 

 private final MimeTypeService mimeTypeService; 

 private final AuthenticationSupport authenticationSupport; 

 /** 
  * Constructs a new context that will use the given dependencies. 
  * 
  * @param mimeTypeService Used when providing mime type of requests. 
  * @param authenticationSupport Used to authenticate requests with sling. 
  */ 
 @Activate 
 public DMSampleApiHttpContext(@Reference final MimeTypeService mimeTypeService, 
                               @Reference final AuthenticationSupport authenticationSupport) { 
     this.mimeTypeService = mimeTypeService; 
     this.authenticationSupport = authenticationSupport; 
 } 

 // ---------- HttpContext interface ---------------------------------------- 
 /** 
  * Returns the MIME type as resolved by the <code>MimeTypeService</code> or 
  * <code>null</code> if the service is not available. 
  */ 
 @Override 
 public String getMimeType(String name) { 
     MimeTypeService mtservice = mimeTypeService; 
     if (mtservice != null) { 
         return mtservice.getMimeType(name); 
     } 
     return null; 
 } 

 /** 
  * Returns the real context path that is used to mount this context. 
  * @param req servlet request 
  * @return the context path 
  */ 
 public static String getRealContextPath(HttpServletRequest req) { 
     final String path = req.getContextPath(); 
     if (path.equals(CONTEXT_PATH)) { 
         return ""; 
     } 
     return path.substring(CONTEXT_PATH.length()); 
 } 

 /** 
  * Returns a request wrapper that transforms the context path back to the original one 
  * @param req request 
  * @return the request wrapper 
  */ 
 public static HttpServletRequest createContextPathAdapterRequest(HttpServletRequest req) { 
     return new HttpServletRequestWrapper(req) { 

         @Override 
         public String getContextPath() { 
             return getRealContextPath((HttpServletRequest) getRequest()); 
         } 

     }; 

 } 

 /** 
  * Always returns <code>null</code> because resources are all provided 
  * through individual endpoint implementations. 
  */ 
 @Override 
 public URL getResource(String name) { 
     return null; 
 } 

 /** 
  * Tries to authenticate the request using the 
  * <code>SlingAuthenticator</code>. If the authenticator or the Repository 
  * is missing this method returns <code>false</code> and sends a 503/SERVICE 
  * UNAVAILABLE status back to the client. 
  */ 
 @Override 
 public boolean handleSecurity(HttpServletRequest request, 
                               HttpServletResponse response) throws IOException { 

     final AuthenticationSupport authenticator = this.authenticationSupport; 
     if (authenticator != null) { 
         return authenticator.handleSecurity(createContextPathAdapterRequest(request), response); 
     } 

     // send 503/SERVICE UNAVAILABLE, flush to ensure delivery 
     response.sendError(HttpServletResponse.SC_SERVICE_UNAVAILABLE, 
             "AuthenticationSupport service missing. Cannot authenticate request."); 
     response.flushBuffer(); 

     // terminate this request now 
     return false; 
 } 
}
```

+++

>[!ENDTABS]



### Use the sample servlet

You invoke the servlet by performing a `GET` operation at `/dmSample/dynamicmedia/video/manifestUrl`. The following query parameters are passed: 

| Query parameter | Description |
| --- | --- |
| `assetPath` | Mandatory. The path to the video for which `manifestUrl` is generated. |
| `manifestType` | Optional. Parameter can be DASH or HLS. If it is not passed, it defaults to DASH. |
| `onlyIfPublished` | Optional. If passed, the `manifestUrl` is returned only if the video is published.  |

In this example, let us assume the following setup: 

* The company is `samplecompany`.
* The authoring instance is `http://sample-aem-author.com`.
* The folder `/content/dam/video-example` has a video encoding profile applied to it. 
* The video `scenery.mp4` is uploaded to the folder `/content/dam/video-example`.

You can invoke the servlet in following ways: 
     
| Type | Description |
| :--- | --- |
| HLS | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=HLS&assetPath=/content/dam/video-example/scenery.mp4`<br><br>In case DASH delivery is enabled:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.m3u8?packagedStreaming=true"}`<br><br>In case DASH delivery is disabled:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.m3u8"}` |
| DASH | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=DASH&assetPath=/content/dam/video-example/scenery.mp4`<br><br>In case DASH delivery is enabled:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.mpd"}`<br><br>In case DASH delivery is disabled:<br>`{}` |
| Error: asset path is wrong | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=DASH&assetPath=/content/dam/video-example/scennnnnnery.mp4`<br><br>`{"errorString":"could not retrieve the resource from JCR"}` |

-->





