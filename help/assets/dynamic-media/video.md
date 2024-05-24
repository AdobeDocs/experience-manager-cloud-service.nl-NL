---
title: Video in Dynamic Media
description: Leer hoe u met video werkt in Dynamic Media. De beste werkwijzen voor het coderen van video's, het publiceren van video's naar YouTube, het bekijken van videoverslagen en het toevoegen van ondertitelings- of hoofdstukmarkeringen aan video's bekijken.
contentOwner: Rick Brough
feature: Video Profiles
role: User
exl-id: 0d5fbb3e-b763-415f-8c69-ea36445f882b
source-git-commit: 7a80f68f71475b2bdb6b5559354d7248208a3819
workflow-type: tm+mt
source-wordcount: '9237'
ht-degree: 0%

---

# Video {#video}

In deze sectie wordt het werken met video in Dynamic Media beschreven.

## Snel starten: Video&#39;s {#quick-start-videos}

De volgende stapsgewijze workflowbeschrijving is ontworpen om u te helpen snel aan de slag te gaan met adaptieve videosets in Dynamic Media. Na elke stap, zijn er verwijzingen naar onderwerprubrieken waar u meer informatie kunt vinden.

>[!NOTE]
>
>Voordat u in Dynamic Media met video werkt, moet u controleren of uw Adobe Experience Manager-beheerder Dynamic Media-Cloud Servicen al heeft ingeschakeld en geconfigureerd.
>
>* Zie [Dynamic Media-Cloud Servicen configureren](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services) in Configureer Dynamic Media en [Problemen met Dynamic Media oplossen](/help/assets/dynamic-media/troubleshoot-dm.md).
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

      * [Voorinstellingen voor viewers beheren](/help/assets/dynamic-media/managing-viewer-presets.md)
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

* Video uploaden van video-indelingen en audio-indelingen die ondersteuning bieden voor een groot aantal apparaten en het coderen van video naar de MP4 H.264-indeling, zodat deze op meerdere schermen kan worden afgespeeld. U kunt vooraf gedefinieerde adaptieve videovoorinstellingen gebruiken, voorinstellingen voor één videocodering gebruiken of uw eigen codering aanpassen om de kwaliteit en de grootte van de video te bepalen.

   * Wanneer een adaptieve videoset wordt gegenereerd, bevat deze MP4-video&#39;s.
   * **Opmerking**: Primaire video&#39;s en bronvideo&#39;s worden niet toegevoegd aan een adaptieve videoset.

* ondertiteling in alle HTML5-videoviewers.
* Video organiseren, doorbladeren en doorzoeken met volledige metagegevensondersteuning voor een efficiënt beheer van video-elementen.
* Lever Adaptieve videosets naar het web en desktops, tablets en mobiele apparaten.

Adaptieve videostreaming wordt ondersteund op verschillende iOS-platforms. Zie [Referentiehandleiding voor Dynamic Media Viewers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-reference.html).

<!-- OUTDATED 2/28/22 BASED ON CQDOC-18692 Dynamic Media supports mobile video playback for MP4 H.264 video. You can find BlackBerry&reg; devices that support this video format at the following: [Supported video formats on BlackBerry&reg;](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

OUTDATED 2/28/22 BASED ON CQDOC-18692 You can find Windows&reg; devices that support this video format at the following [Supported video formats on Windows&reg; Phone](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/supported-codecs). -->

* Speel de video terug gebruikend de Voorinstellingen van de VideoKijker van Dynamic Media, met inbegrip van:

   * Enkele videoviewers.
   * Gemengde Media-viewers die zowel video- als afbeeldingsinhoud combineren.

* Configureer videospelers om aan uw brandingbehoeften te voldoen.
* Video met een eenvoudige URL of insluitcode integreren in uw website, mobiele site of mobiele toepassing.

Zie [Dynamische videoweergave](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&amp;config=GeoRetail/Universal_Video1&amp;stageSize=640,480) monster nemen.

Zie ook [Viewers voor Experience Manager Assets en Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers.html#viewers-aem-assets-dmc) en [Alleen viewers voor Experience Manager Assets](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html#viewers-for-aem-assets-only) in de [Referentiehandleiding voor Dynamic Media Viewers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html).

## Tips en trucs: De HTML5-videoviewer gebruiken {#best-practice-using-the-html-video-viewer}

De Dynamic Media HTML5 Video viewer-voorinstellingen zijn robuuste videospelers. U kunt ze gebruiken om veel voorkomende problemen te voorkomen die te maken hebben met het afspelen van HTML5-video en met problemen die te maken hebben met mobiele apparaten. Bijvoorbeeld een gebrek aan adaptieve streaminglevering met bitsnelheid en een beperkt bereik van de desktopbrowser.

Aan de ontwerpkant van de speler, kunt u de functionaliteit van de videospeler ontwerpen gebruikend standaardWeb ontwikkelingshulpmiddelen. U kunt bijvoorbeeld de knoppen, besturingselementen en de achtergrond van een aangepaste posterafbeelding ontwerpen met behulp van HTML5 en CSS om u te helpen uw klanten te bereiken met een aangepaste weergave.

Aan de afspeelzijde van de viewer wordt automatisch de videocapaciteit van de browser gedetecteerd. Vervolgens wordt de video afgespeeld met HLS of DASH, ook wel adaptieve videostreaming genoemd. Of als deze leveringsmethoden niet aanwezig zijn, wordt in plaats daarvan HTML5 progressief gebruikt.

>[!NOTE]
>
>Als u DASH wilt gebruiken voor uw video&#39;s, moet u deze eerst inschakelen via de Adobe Technical Support op uw account. Zie [DASH inschakelen voor uw account](#enable-dash).

U kunt de mogelijkheid om de afspeelcomponenten te ontwerpen met behulp van HTML5 en CSS combineren tot één speler. Het kan het afspelen ingesloten hebben en adaptief en progressief streamen gebruiken, afhankelijk van de mogelijkheden van de browser. Met al deze functionaliteit kunt u het bereik van uw uitgebreide media-inhoud uitbreiden voor zowel gebruikers op het bureaublad als mobiele apparaten en een gestroomlijnde videobeleving garanderen.

Zie ook [Alleen viewers voor Experience Manager Assets](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html#viewers-for-aem-assets-only) in de [Referentiehandleiding voor Dynamic Media Viewers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html).


### Video afspelen op bureaubladcomputers en mobiele apparaten met de HTML5-videoviewer {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

Voor adaptieve videostreaming op het bureaublad en mobiele apparaten zijn de video&#39;s die worden gebruikt voor het schakelen naar een andere bitsnelheid, gebaseerd op alle MP4-video&#39;s in de adaptieve videoset.

Het afspelen van video vindt plaats met HLS of DASH of met progressieve videodownload. In eerdere versies van Experience Manager, zoals 6.0, 6.1 en 6.2, werden video&#39;s gestreamd via HTTP.

In Experience Manager 6.3 en hoger worden video&#39;s nu gestreamd via HTTPS (dat wil zeggen, HLS of DASH) omdat de URL van de DM-gatewayservice altijd HTTPS gebruikt. Dit standaardgedrag heeft geen gevolgen voor de klant. Videostreaming vindt altijd plaats via HTTPS, tenzij dit niet door de browser wordt ondersteund. Zie de volgende tabel.

Daarom

* Als u een HTTPS-website met HTTPS-videostreaming hebt, is streaming prima.
* Als u een HTTP-website met HTTPS-videostreaming hebt, is streaming prima en zijn er geen problemen met gemengde inhoud in de webbrowser.

DASH is de internationale standaard en HLS is een Apple-standaard. Beide worden gebruikt voor adaptieve videostreaming. En, passen beide technologieën automatisch playback aan die op de capaciteit van de netwerkbandbreedte wordt gebaseerd. Het laat de klant ook &quot;zoeken&quot;aan om het even welk punt in de video zonder de behoefte om op de rest van de video te wachten te downloaden.

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
   <td>In Windows® 8 en Windows® 10 - Gebruik HTTPS geforceerd wanneer DASH of HLS wordt aangevraagd. Bekende beperking: HTTP op DASH of HLS werkt niet in deze combinatie van browser en besturingssysteem<br /> <br /> In Windows® 7 - Progressief downloaden. Gebruikt de standaardlogica voor het selecteren van het protocol HTTP versus HTTPS.</td>
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
   <td>Chroom</td>
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
>*Als u DASH wilt gebruiken voor uw video&#39;s, moet u deze eerst inschakelen via de Adobe Technical Support op uw account. Zie [DASH inschakelen voor uw account](#enable-dash).)

<!--  THIS LINE WAS REMOVED FROM THE TABLE ABOVE ON FEB 28, 2022 BASED ON CQDOC 18692 -RSB <tr>
   <td>Mobile</td>
   <td>BlackBerry&reg;</td>
   <td>HLS or DASH</td>
  </tr>
 -->

## Architectuur van Dynamic Media-videooplossing {#architecture-of-dynamic-media-video-solution}

In de volgende afbeelding ziet u de algemene ontwerpworkflow voor video&#39;s die via DMGateway (in de Dynamic Media Hybrid-modus) worden geüpload en gecodeerd en die voor openbare consumptie beschikbaar worden gesteld.

![chlimage_1-427](assets/chlimage_1-427.png)

## Hybride publicatiearchitectuur voor video&#39;s {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## Aanbevolen werkwijzen voor het coderen van video&#39;s {#best-practices-for-encoding-videos}

De **Dynamic Media-video coderen** de workflow codeert video als u Dynamic Media hebt ingeschakeld en video-Cloud Servicen hebt ingesteld. In deze workflow worden de historie en informatie over fouten van het workflowproces vastgelegd. Als u Dynamic Media hebt ingeschakeld en video-Cloud Servicen hebt ingesteld, **[!UICONTROL Dynamic Media Encode Video]** de workflow wordt automatisch van kracht wanneer u een video uploadt. (Als u Dynamic Media niet gebruikt, wordt **[!UICONTROL DAM Update Asset]** workflow wordt van kracht.)

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

U kunt de metagegevens van een bestand verkrijgen door de metagegevens van het bestand te bekijken met een bewerkgereedschap voor video&#39;s of met een toepassing die is ontworpen voor het verkrijgen van metagegevens. Hieronder vindt u instructies voor het gebruik van MediaInfo, een toepassing van derden, voor het verkrijgen van de metagegevens van een videobestand:

1. Ga naar [MediaInfo downloaden](https://mediaarea.net/en/MediaInfo/Download).
1. Selecteer en download het installatieprogramma voor de GUI-versie en volg de installatie-instructies.
1. Klik na de installatie met de rechtermuisknop op het videobestand (alleen Windows®) en selecteer MediaInfo, of open MediaInfo en sleep het videobestand naar de toepassing. U ziet alle metagegevens die aan het videobestand zijn gekoppeld, inclusief de breedte, hoogte en fps.

### Hoogte-breedteverhouding {#aspect-ratio}

Wanneer u een voorinstelling voor videocodering kiest of maakt voor uw primaire bronvideobestand, moet u ervoor zorgen dat de voorinstelling dezelfde hoogte-breedteverhouding heeft als het primaire bronvideobestand. De hoogte-breedteverhouding is de verhouding tussen de breedte en de hoogte van de video.

Als u de hoogte-breedteverhouding van een videobestand wilt bepalen, vraagt u de metagegevens van het bestand op en noteert u de breedte en hoogte van het bestand (zie De metagegevens van het bestand hierboven verkrijgen). Gebruik vervolgens deze formule om de hoogte-breedteverhouding te bepalen:

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

Bitsnelheid is de hoeveelheid gegevens die wordt gecodeerd om één seconde video af te spelen. De bitsnelheid wordt gemeten in kilobits per seconde (Kbps).

>[!NOTE]
>
>Omdat in alle codecs compressie met verlies wordt gebruikt, is bitsnelheid de belangrijkste factor voor de videokwaliteit. Bij compressie met verlies neemt de kwaliteit af naarmate u een videobestand comprimeert. Daarom zijn alle andere eigenschappen gelijk (de resolutie, framesnelheid en codec), hoe lager de bitsnelheid, hoe lager de kwaliteit van het gecomprimeerde bestand.

Wanneer u een codering voor bitsnelheden selecteert, kunt u kiezen uit twee typen:

* **[!UICONTROL Constant Bitrate Encoding]** (CBR) - Tijdens CBR-codering blijft de bitsnelheid of het aantal bits per seconde tijdens het coderingsproces ongewijzigd. Bij CBR-codering blijft de gegevenssnelheid van de set behouden voor de instelling van de gehele video. Bij CBR-codering worden mediabestanden niet geoptimaliseerd voor kwaliteit, maar wordt opslagruimte bespaard.
Gebruik CBR als uw video een vergelijkbaar bewegingsniveau in de gehele video bevat. CBR wordt meestal gebruikt voor het streamen van video-inhoud. Zie ook [Parameters voor aangepaste videocodering gebruiken](/help/assets/dynamic-media/video-profiles.md#using-custom-added-video-encoding-parameters).

* **[!UICONTROL Variable Bitrate Encoding]** (VBR) - VBR-codering past de gegevenssnelheid naar beneden en naar de bovenste limiet die u instelt, aan op basis van de gegevens die de compressor nodig heeft. Deze functionaliteit houdt in dat de bitsnelheid van het mediabestand tijdens een VBR-coderingsproces dynamisch wordt verhoogd of verlaagd, afhankelijk van de behoeften aan bitsnelheid van mediabestanden.
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

**Resolutie** Hiermee worden de hoogte en breedte van een videobestand in pixels beschreven. De meeste bronvideo wordt opgeslagen met een hoge resolutie (bijvoorbeeld 1920 x 1080). Voor streamingdoeleinden wordt bronvideo gecomprimeerd tot een lagere resolutie (640 x 480 of lager).

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
| 480p | 480 | Standaardscherm |
| 720p | 720 | Groot scherm |
| 1080p | 1080 | High-definition groot scherm |

### FPS (frames per seconde) {#fps-frames-per-second}

In de Verenigde Staten en Japan wordt de meeste video met 29,97 frames per seconde (fps) opgenomen; in Europa wordt de meeste video met 25 fps opgenomen. Film wordt opgenomen bij 24 fps.

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

## Videorapporten weergeven {#viewing-video-reports}

>[!NOTE]
>
>Videorapporten zijn alleen beschikbaar wanneer u de modus Dynamic Media - Hybride uitvoert.

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
>
>Het bijhouden en rapporteren van gegevens is uitsluitend gebaseerd op het gebruik van de eigen videospeler van Dynamic Media en de bijbehorende voorinstelling van de videospeler. U kunt dus geen video&#39;s bijhouden en rapporteren die door andere videospelers worden afgespeeld.

Door gebrek, de eerste keer u VideoRapporten ingaat, toont het rapport videogegevens die bij de eerste van de huidige maand beginnen en met de datum van de huidige maand beëindigen. U kunt het standaarddatumbereik echter overschrijven door uw eigen datumbereik op te geven. De volgende keer dat u Video-rapporten invoert, wordt het opgegeven datumbereik gebruikt.

Voor het correct werken van videorapporten, wordt een identiteitskaart van de Reeks van het Rapport automatisch gecreeerd wanneer de Cloud Servicen van Dynamic Media wordt gevormd. Tegelijkertijd wordt de rapportsuite-id doorgegeven aan de publicatieserver, zodat deze beschikbaar is voor de functie URL kopiëren wanneer u een voorvertoning van elementen weergeeft. Voor deze functionaliteit is echter vereist dat de publicatieserver al is ingesteld. Als de publicatieserver niet is ingesteld, kunt u toch publiceren om het videoverslag te zien. U moet echter terugkeren naar de Dynamic Media Cloud Configuration en **[!UICONTROL OK]**.

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





## Ondersteuning voor DASH-, multi-caption- en multi-audiotracks inschakelen voor uw Dynamic Media-account {#enable-dash}

**Informatie over het inschakelen van DASH-ondersteuning voor uw account**
DASH (Digital Adaptive Streaming via HTTP) is de internationale standaard voor videostreaming en wordt op grote schaal toegepast door verschillende videoviewers. Als DASH op uw account is ingeschakeld, kunt u kiezen uit DASH of HLS voor adaptieve videostreaming. Of u kunt kiezen voor beide opties met automatische schakeling tussen spelers wanneer **[!UICONTROL auto]** is geselecteerd als het afspeeltype in de voorinstelling Viewer.

Enkele belangrijke voordelen van het inschakelen van DASH voor uw account zijn:

* Pakketvideo voor aangepaste bitsnelheidstreaming. Deze methode leidt tot een efficiëntere levering. Adaptieve streaming zorgt voor de beste kijkervaring voor uw klanten.
* Bij voor browsers geoptimaliseerde streaming met Dynamic Media-spelers wordt geschakeld tussen HLS- en DASH-streaming voor de beste kwaliteit van de service. Wanneer een Safari-browser wordt gebruikt, schakelt de videospeler automatisch over naar HLS.
* U kunt uw voorkeursstreammethode (HLS of DASH) configureren door de voorinstelling voor de videoviewer te bewerken.
* Geoptimaliseerde videocodering zorgt ervoor dat er geen extra opslagruimte wordt gebruikt terwijl DASH-mogelijkheden worden ingeschakeld. Er wordt één set videocoderingscodes gemaakt voor zowel HLS als DASH om de opslagkosten voor video te optimaliseren.
* Helpt de levering van video toegankelijker te maken voor uw klanten.
* U kunt de URL voor streaming ook ophalen via API&#39;s.

Het inschakelen van DASH-ondersteuning voor uw account gebeurt via een Adobe voor klantenondersteuning die u maakt en verzendt.

**Ondersteuning voor meerdere bijschriften en audiotracks voor uw account inschakelen**

Als u een Adobe Support-case maakt voor DASH ingeschakeld op uw account, kunt u er ook van profiteren dat ondersteuning voor meerdere bijschriften en audiotracks automatisch wordt ingeschakeld. Nadat u deze optie hebt ingeschakeld, worden alle volgende video&#39;s die u uploadt, verwerkt met een nieuwe back-endarchitectuur die ondersteuning biedt voor het toevoegen van meerdere bijschriften en audiotracks aan uw video&#39;s.

>[!IMPORTANT]
>
>Alle video&#39;s die u hebt geüpload *voor* het inschakelen van ondersteuning voor meerdere bijschriften en audiotracks op uw Dynamic Media-account, [moet worden opgewerkt](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). Deze videoopwerkingsstap is nodig om ervoor te zorgen dat meerdere bijschriften en audiotrackmogelijkheden beschikbaar zijn. De video-URL&#39;s blijven werken en worden na de opwerking op de gebruikelijke wijze afgespeeld.

**U kunt als volgt ondersteuning voor DASH-, multi-caption- en multi-audiotracks inschakelen op uw Dynamic Media-account:**

1. [Gebruik de Admin Console om een nieuwe steungeval te beginnen](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).
1. Als u een ondersteuningsgeval wilt maken, volgt u de instructies en zorgt u ervoor dat u de volgende informatie opgeeft:

   * Primaire contactpersoon, e-mail, telefoon.
   * De omgeving van uw Cloud Servicen (programma-id en milieu-id).
   * De naam van je Dynamic Media-bedrijfsaccount.
   * Uw Dynamic Media-regio: Noord-Amerika (NA), Azië-Stille Oceaan (APAC) of Europa-Midden-Oost-Azië (EMEA).
   * Geef op of u ondersteuning voor DASH-, multi-caption- en multi-audiotracks wilt inschakelen voor uw Dynamic Media-account, op Experience Manager 6.5.

1. De Steun van de Klant van de Adobe voegt u aan de klant toe wachtlijst die op de orde wordt gebaseerd waarin de verzoeken worden voorgelegd.
1. Wanneer de Adobe klaar is om uw verzoek te behandelen, contacteert de Steun van de Klant u om een doeldatum voor enablement te coördineren en te plaatsen.
1. Klantenondersteuning stuurt u een melding nadat de service is voltooid.
1. U kunt nu een van de volgende twee handelingen uitvoeren:

   * Maak uw [videoviewervoorinstelling](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset) zoals gebruikelijk.
   * [Meerdere bijschriften en audiotracks toevoegen](#add-msma) naar uw video.


## Ondersteuning voor meerdere bijschriften en audiotracks voor video&#39;s in Dynamic Media{#about-msma}

Met de mogelijkheden voor meerdere bijschriften en audiotracks in Dynamic Media kunt u eenvoudig meerdere bijschriften en audiotracks toevoegen aan een primaire video. Dit betekent dat uw video&#39;s toegankelijk zijn voor een breed publiek. U kunt één gepubliceerde primaire video aanpassen aan een wereldwijd publiek in meerdere talen en de richtlijnen voor toegankelijkheid voor verschillende geografische regio&#39;s naleven. Auteurs kunnen de bijschriften en audiotracks ook beheren vanaf één tabblad in de gebruikersinterface.

![Het tabblad Bijschriften en audiotracks in Dynamic Media en een tabel met geüploade .VTT-bijschriftbestanden en geüploade .MP3-audiotrackbestanden voor een video.](/help/assets/dynamic-media/assets/msma-subtitle-audiotracks-tab.png)

Een aantal van de gebruiksscenario&#39;s die u moet overwegen om meerdere bijschriften en audiotracks toe te voegen aan uw primaire video, zijn onder andere:

| Type | Hoofdletters gebruiken |
|--- |--- |
| **Bijschriften** | Ondersteuning voor meerdere talen |
|  | Beschrijvende tekst voor toegankelijkheid |
| **Audiotracks** | Ondersteuning voor meerdere talen |
|  | Commentaartracks |
|  | Beschrijvende audio |

Alles [video-indelingen ondersteund in Dynamic Media](/help/assets/file-format-support.md) en alle Dynamic Media-videoviewers, behalve de Dynamic Media *Video_360* viewer: wordt ondersteund voor gebruik met meerdere bijschriften en audiotracks.

Mogelijkheid voor meerdere bijschriften en audiotracks is beschikbaar voor uw Dynamic Media-account via een functiewissel die moet worden ingeschakeld (ingeschakeld) door de Adobe Klantenondersteuning.

### Meerdere bijschriften en audiotracks toevoegen aan uw video {#add-msma}

Voordat u meerdere bijschriften en audiotracks aan uw video toevoegt, moet u controleren of u al over het volgende beschikt:

* Dynamic Media wordt ingesteld in een AEM omgeving.
* A [Dynamic Media-videoprofiel wordt toegepast op de map waarin uw video&#39;s worden opgenomen](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).
* [Multi-caption en multi-audio track is ingeschakeld voor uw Dynamic Media-account](#enable-dash).

Toegevoegde bijschriften en bijschriften worden ondersteund met de indelingen WebVTT en Adobe VTT. Toegevoegde audiotrackbestanden worden ook ondersteund in de MP3-indeling.

>[!IMPORTANT]
>
>Alle video&#39;s die u hebt geüpload *voor* het inschakelen van ondersteuning voor meerdere bijschriften en audiotracks op uw Dynamic Media-account, [moet worden opgewerkt](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). Deze videoopwerkingsstap is nodig om ervoor te zorgen dat meerdere bijschriften en audiotrackmogelijkheden beschikbaar zijn. De video-URL&#39;s blijven werken en worden na de opwerking op de gebruikelijke wijze afgespeeld.

**Meerdere bijschriften en audiotracks toevoegen aan uw video:**

1. [Uw primaire video uploaden naar een map](/help/assets/manage-video-assets.md#upload-and-preview-video-assets) waaraan al een videoprofiel is toegewezen.
1. Navigeer naar het geüploade video-element waaraan u meerdere bijschriften en audiotracks wilt toevoegen.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram Eigenschappen (een cirkel met een &quot;i&quot; erin).
   ![Geselecteerd video-element met vinkje boven de miniatuurafbeelding van de video en Weergave-eigenschappen gemarkeerd op de werkbalk.](/help/assets/dynamic-media/assets/msma-selectedasset-propertiesbutton.png)*Geselecteerd video-element in de kaartweergave.*
1. Selecteer op de pagina Eigenschappen van video de optie **[!UICONTROL Captions & Audio Tracks]** tab.

   >[!TIP]
   >Als u het geneesmiddel niet ziet **[!UICONTROL Captions & Audio Tracks]** tab, betekent dit een van de volgende twee dingen:
   >
   >* Aan de map waarin de geselecteerde video zich bevindt, is geen videoprofiel toegewezen. In dat geval, zie [Een videoprofiel toepassen op de map](/help/assets/dynamic-media/video-profiles.md#applying-video-profiles-to-specific-folders)
   >* Of de video moet opnieuw worden verwerkt door Dynamic Media. In dat geval, zie [Dynamic Media-elementen in een map opnieuw verwerken](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).
   >
   >Als u een van de bovenstaande taken hebt uitgevoerd, gaat u terug naar deze stappen.

   ![Het tabblad Bijschriften en Audiotracks op de pagina Eigenschappen.](/help/assets/dynamic-media/assets/msma-audiotracks.png)*Het tabblad Bijschriften en audiotracks op de pagina Eigenschappen van de video.*

1. (Optioneel) Ga als volgt te werk om een of meer bijschriftbestanden aan een video toe te voegen:
   * Selecteren **[!UICONTROL Upload Captions]**.
   * Navigeer naar en selecteer een of meer .vtt-bestanden (videoteksttracks) en open deze.
   * Als bijschriften zichtbaar moeten zijn op de mediaspeler, kunt u *moet* vereiste details (metagegevens) toevoegen over *elk* Het bijschriftbestand dat u hebt geüpload. Selecteer het potloodpictogram rechts van de bestandsnaam van een bijschrift. In de **Bijschrift bewerken** voert u de volgende vereiste gegevens over het bestand in en selecteert u **[!UICONTROL Save]**. Herhaal dit proces voor elk bijschriftbestand dat u hebt geüpload:

     | Metagegevens bijschrift | Beschrijving |
     |--- |--- |
     | Bestandsnaam | De standaardbestandsnaam wordt afgeleid van de oorspronkelijke bestandsnaam. De bestandsnaam kan alleen tijdens het uploaden worden gewijzigd en kan later niet worden gewijzigd. De vereisten voor bestandsnaamtekens zijn gelijk aan die voor AEM Assets.<br>Dezelfde bestandsnaam kan niet worden gebruikt voor extra bijschriftbestanden en audiotrackbestanden. |
     | Taal | Selecteer de taal van het bijschrift. |
     | Type | Selecteer het type bijschrift dat u gebruikt.<br>**Bijschrift** - De bijschrifttekst die wordt weergegeven bij de video waarmee het dialoogvenster wordt getransformeerd of getransformeerd.<br>**Bijschrift** - De bijschrifttekst bevat ook achtergrondgeluiden, sprekersdifferentiatie en andere relevante informatie, samen met de vertaling of transcriptie van de dialoog, waardoor de inhoud toegankelijker wordt voor doven of slechthorenden. |
     | Label | De tekst die voor de naam van het bijschrift wordt weergegeven in het dialoogvenster **[!UICONTROL Select audio or caption]** in de mediaspeler. Het label is wat een klant ziet die met een bijschrift of bijschrifttrack correspondeert. Bijvoorbeeld: `English (CC)`. |

     U kunt de metagegevens van bijschriften indien nodig later wijzigen of bewerken. Wanneer de video wordt gepubliceerd, worden deze details weerspiegeld op openbare URLs in gepubliceerde video&#39;s.

1. (Optioneel) Ga als volgt te werk om een of meer audiotracks aan een video toe te voegen:
   * Selecteren **[!UICONTROL Upload Audio Tracks]**.
   * Navigeer naar en selecteer een of meer MP3-bestanden en open deze.
   * Voor audiotracks die zichtbaar moeten zijn in het dialoogvenster **[!UICONTROL Select audio or caption]** op de mediaspeler, kunt u *moet* vereiste gegevens toevoegen over *elk* audiotrackbestand dat u hebt toegevoegd. Selecteer het potloodpictogram rechts van de bestandsnaam van een audiotrack. In de **Audiotrack bewerken** voert u de volgende vereiste gegevens in en selecteert u **[!UICONTROL Save]**. Herhaal dit proces voor elk audiospoordossier dat u uploadde.

     | Metagegevens audiotrack | Beschrijving |
     |--- |--- |
     | Bestandsnaam | De standaardbestandsnaam wordt afgeleid van de oorspronkelijke bestandsnaam. De bestandsnaam kan alleen tijdens het uploaden worden gewijzigd en kan later niet worden gewijzigd. De vereisten voor bestandsnaamtekens zijn gelijk aan die voor AEM Assets.<br>Dezelfde bestandsnaam kan niet worden gebruikt voor extra audiotrackbestanden of bijschriftbestanden. |
     | Taal | Selecteer de taal van de audiotrack. |
     | Type | Selecteer het type audiotrack dat u gebruikt.<br>**Origineel** - De audiotrack die oorspronkelijk aan de video was gekoppeld en die werd weergegeven als `[Original]` op het etiket met `English` taal die standaard is geselecteerd. while **[!UICONTROL Label]** en **[!UICONTROL Language]** kan worden gewijzigd in het dialoogvenster **[!UICONTROL Edit Audio Track]** de oorspronkelijke waarden als de primaire video opnieuw wordt verwerkt.<br>**Standaard** - Een add-on audiotrack voor een andere taal dan het origineel.<br>**Audiobeschrijving** - Een audiotrack die ook een beschrijvende beschrijving van niet-verbale handelingen en bewegingen in de video bevat, waardoor inhoud toegankelijker wordt voor personen met een visuele handicap. |
     | Label | De tekst die als naam van de audiotrack wordt weergegeven in het dialoogvenster **[!UICONTROL Select audio or caption]** in de mediaspeler. Het label is wat een klant ziet die met een audiotrack correspondeert. Bijvoorbeeld: `English [Original]`. Het label van de audio die aan een video is gekoppeld, is ingesteld op `[Original]` standaard. |

     U kunt deze metagegevens van de audiotrack indien nodig later wijzigen of bewerken. Wanneer de video wordt gepubliceerd, worden deze details weerspiegeld op openbare URLs in gepubliceerde video&#39;s.

1. In de rechterbovenhoek van de pagina, vanaf de **[!UICONTROL Save & Close]** vervolgkeuzelijst, selecteert u **[!UICONTROL Save]**. De bestanden worden geüpload en de verwerking van metagegevens wordt gestart, zoals in het dialoogvenster **Status** kolom van de interface.

   >[!NOTE]
   >
   >Op basis van de cacheinstellingen van uw instantie kan het verwerken van metagegevens enkele minuten duren voordat dit effect wordt weerspiegeld in de voorvertoning en in gepubliceerde URL&#39;s.

1. (Optioneel) Als u **[!UICONTROL Save & Close]** in de vorige stap in plaats van **[!UICONTROL Save]** kunt u nog steeds de verwerkingsstatus van de geüploade bestanden bekijken. Zie [De levenscyclusstatus van geüploade bijschriften en audiotrackbestanden weergeven](#lifecycle-status-video).
1. (Optioneel) Geef een voorvertoning van de video weer voordat u de video publiceert, zodat de bijschriften en audio naar behoren werken. Zie [Een voorvertoning weergeven van een video met meerdere bijschriften en audiotracks](#preview-video-audio-subtitle)
1. Publiceer de video. Zie [Elementen publiceren](publishing-dynamicmedia-assets.md).

#### Bijschrift- en audiotrackbestanden toevoegen aan een video die al is gepubliceerd

Wanneer u aanvullende bijschriftbestanden of audiotrackbestanden uploadt naar een video die al is gepubliceerd, betekent dit dat deze bestanden een `Processed` status nadat ze zijn voorbereid, na uploaden. Op dat moment kunt u de video voorvertonen in Dynamic Media om de nieuw geüploade bestanden te bekijken of te horen.

Na de voorvertoning moet u echter *publish* de video opnieuw voor de nieuw toegevoegde dossiers van de titel of van het audiospoor te publiceren. Na publicatie worden de bijschriften of audio beschikbaar via de openbare Dynamic Media-URL.

>[!NOTE]
>
>Op basis van de cacheinstellingen van uw instantie kunnen updates van metagegevens enkele minuten duren voordat deze worden weergegeven in de voorvertoning en in gepubliceerde URL&#39;s.

In het scenario waarin u Dynamic Media hebt geconfigureerd voor direct publiceren, wordt door het uploaden van extra bijschrift- of audiobestanden direct een publicatie van de video gestart na het uploaden van bijschrift- of audiobestanden.

>[!CAUTION]
>
>Wanneer u bijschriftbestanden of audiobestanden uploadt naar een video die gepubliceerd of niet gepubliceerd is, worden de bestanden verwijderd als u [*herverwerken*](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) de video. Alleen de oorspronkelijke audio van de video blijft intact. In dergelijke gevallen moet u de bijschriftbestanden en audiotrackbestanden opnieuw uploaden naar de video.

#### Meerdere bijschriften toevoegen aan een video met een bestaande URL met bijschriftoptie

Dynamic Media ondersteunt het toevoegen van één bijschrift met video via een URL-modifier. Zie [Bijschriften toevoegen aan video](#adding-captions-to-video).

Meerdere bijschriftwijzigingen hebben voorrang op een bijschrift dat is toegevoegd via een URL-modifier voor gepubliceerde video&#39;s.

**Meerdere bijschriften toevoegen aan een video met een bestaande URL met bijschriftoptie:**

1. Upload het bijschriftbestand dat al als een modifier aan de video is toegevoegd, zodat u het bestand expliciet kunt beheren.
1. U kunt desgewenst aanvullende bijschriftbestanden uploaden.
1. Publiceer de video op de gebruikelijke wijze.
De bestaande URL met de optie caption kan nu meerdere bijschriften laden.

### De levenscyclusstatus van geüploade bijschriften en audiotrackbestanden weergeven{#lifecycle-status-video}

U kunt de levenscyclusstatus bekijken van elk bijschrift of audiotrackbestand dat vanuit het **Bijschriften en audiotracks** tabblad van **Eigenschappen**.

**De levenscyclusstatus van een video weergeven:**

1. Navigeer naar het video-element waarvan u de levenscyclusstatus wilt weergeven.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram Eigenschappen (een cirkel met een &quot;i&quot; erin).
1. Selecteer op de pagina Eigenschappen de optie **[!UICONTROL Captions & Audio Tracks]** tab. Noteer in de kolom Status de status van elk bijschrift of audiobestand.

| Status bijschrift of audiotrack | Beschrijving |
| --- | --- |
| Verwerking | Wanneer een nieuw bijschrift of audiotrackbestand wordt toegevoegd en opgeslagen, verandert dit in de status &quot;Verwerking&quot;. Dynamic Media verwerkt het bestand door het streamingmanifest aan de primaire video te koppelen. |
| Verwerkt | Nadat de verwerking is voltooid, wordt het bijschrift of audiotrackbestand, of de oorspronkelijke audiotrack die is gekoppeld aan de primaire video, weergegeven in de status &quot;Verwerkt&quot;. U kunt een voorvertoning weergeven van bijschriften en audiotrackbestanden die als &quot;Verwerkt&quot; worden weergegeven *voor* u publiceert de video live. |
| Gepubliceerd | De status &quot;Gepubliceerd&quot; vertegenwoordigt een vergelijkbare status als &quot;Gepubliceerd&quot; voor een primaire video. Elementen worden gepubliceerd wanneer de primaire video wordt gepubliceerd en zijn beschikbaar via de openbare URL van Dynamic Media. |
| Mislukt | De status &quot;Mislukt&quot; betekent dat de verwerking van een bijschrift of audiotrackbestand niet is voltooid. Verwijder het bijschrift of het audiotrackbestand en upload het opnieuw. |
| Ongepubliceerd | Wanneer een gepubliceerde primaire video niet expliciet wordt gepubliceerd, worden alle bijschriften of audiotrackbestanden die u aan de video hebt toegevoegd, ook niet gepubliceerd. |

![De statuskolom die is gemarkeerd voor de velden Bijschriften en Audiotracks.](/help/assets/dynamic-media/assets/msma-lifecycle-status.png)*Levenscyclusstatus van elk geüpload bijschrift en audiotrackbestand.*

### De standaardaudio instellen voor een video met meerdere audiotracks

Standaard wordt de oorspronkelijke audio van een video ingesteld als de standaardaudio die moet worden afgespeeld.

Geüploade audiotrackbestanden kunnen echter worden ingesteld als de standaardaudio die moet worden afgespeeld nadat een video in de viewer is geladen. In de gebruikersinterface van Eigenschappen, onder **Bijschriften en audiotracks** de `Default` label wordt rechts van het audiotrackbestand toegepast voor het afspelen van video.

>[!NOTE]
>
>Het afspelen van standaardaudio kan ook afhankelijk zijn van de instelling in de volgende browsers:
>
>* Chrome - De standaardaudio die in de video is ingesteld, wordt afgespeeld.
>* Safari - Als de standaardtaal in Safari wordt geplaatst, wordt de audio gespeeld met de vastgestelde standaardtaal, als beschikbaar met manifest van de video. Anders wordt de standaardaudio afgespeeld die is ingesteld als onderdeel van de eigenschappen van een video.

**U kunt als volgt de standaardaudio instellen voor een video met meerdere audiotracks:**

1. Navigeer naar het video-element waarvan u de standaardaudiotrack wilt instellen.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram Eigenschappen (een cirkel met een &quot;i&quot; erin).
1. Selecteer op de pagina Eigenschappen de optie **[!UICONTROL Captions & Audio Tracks]** tab.
1. Onder de **Audiotracks** Selecteer het audiotrackbestand dat u wilt instellen als de standaardnaam van de video.
1. Selecteren **[!UICONTROL Set as default]**.
In de **Instellen als standaard** dialoogvenster selecteert u **[!UICONTROL Replace]**.

   ![De kop Audiotracks bevat een geselecteerde naam voor het audiotrackbestand en de gemarkeerde knop &quot;Instellen als standaard&quot;.](/help/assets/dynamic-media/assets/msma-defaultaudiotrack.png)*De standaardaudiotrack voor een video instellen.*

1. Selecteer in de rechterbovenhoek de optie **[!UICONTROL Save & Close]**.
1. Publiceer de video. Zie [Elementen publiceren](publishing-dynamicmedia-assets.md).

### Een voorvertoning weergeven van een video met meerdere bijschriften en audiotracks{#preview-video-audio-subtitle}

Nadat bijschriftbestanden en audiotrackbestanden naar een video zijn geüpload en zijn verwerkt, kunt u met de Dynamic Media-videoviewer een voorvertoning van alle verschillende tracks weergeven. Zo kunt u zien hoe de video er uitziet en hoe de video er voor de klant uitziet en zorgt u ervoor dat de video zich naar behoren gedraagt.

Wanneer u tevreden bent met de video, kunt u [publiceren](publishing-dynamicmedia-assets.md) met een van de volgende methoden.

Zie [De video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/dynamic-media/embed-code.md).
Zie [URL&#39;s koppelen aan uw webtoepassing](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.
Zie [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

>[!NOTE]
>
>Het standaardtabblad voor voorvertoningen van Experience Managers bevat geen bijschrift en audiotracks. De reden hiervoor is dat deze tracks zijn gekoppeld aan Dynamic Media en alleen kunnen worden weergegeven met de voorvertoning van de Dynamic Media Viewer.

**Een voorvertoning weergeven van een video met meerdere bijschriften en audiotracks:**

1. In **[!UICONTROL Assets]** Navigeer naar een bestaande video waaraan u meerdere bijschriften en audiotracks hebt toegevoegd.
1. Klik op het video-element zodat u dit kunt openen in de voorvertoningsmodus.
1. Selecteer op de voorvertoningspagina, linksboven op de pagina, de vervolgkeuzelijst en selecteer **[!UICONTROL Viewers]**.

   ![Vervolgkeuzelijst met de optie Viewers.](/help/assets/dynamic-media/assets/msma-selectviewers.png)

1. Selecteer in de lijst Viewers een viewer die u wilt gebruiken voor de videovoorvertoning. In de volgende schermafbeelding ziet u bijvoorbeeld de **[!UICONTROL Video]** de geselecteerde viewer.

   ![Selectie van de videoviewer in de vervolgkeuzelijst Viewers.](/help/assets/dynamic-media/assets/msma-dmviewerselected.png)

1. Selecteer bij de rechterbenedenhoek, links van het volumepictogram, het pictogram van de spraakballon en selecteer vervolgens de audio of het bijschrift die u wilt horen, of zien of beide. U kunt desgewenst onder Bijschriften de optie **[!UICONTROL Off]** om geen bijschriften of bijschriften weer te geven.

   ![De pop-uplijst Audio en Bijschriften in de videoviewer.](/help/assets/dynamic-media/assets/msma-selectaudiosubtitle.png)*Simulatie van een gebruiker die de audio en het bijschrift voor het afspelen van video selecteert.*

1. Selecteer de video&#39;s om het afspelen te starten **[!UICONTROL Play]** knop.
Noteer de **[!UICONTROL URL]** en **[!UICONTROL Embed]** in de linkerbenedenhoek. Gebruik deze knoppen om [de URL van de video koppelen aan uw webtoepassing](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) of aan [de video insluiten op een webpagina](/help/assets/dynamic-media/embed-code.md), respectievelijk.
1. Selecteer in de rechterbovenhoek van de voorvertoningspagina de optie **[!UICONTROL Close]**.

### Bijschrift- of audiotrackbestanden verwijderen uit een video

U kunt bijschrift- of audiotrackbestanden verwijderen uit een video. Het verwijderen van gepubliceerde bijschriften of audiotrackbestanden wordt automatisch weerspiegeld in de gepubliceerde URL van de video.

De oorspronkelijke audiotrack die uit een primaire video is geëxtraheerd, kan niet worden verwijderd.

**Bijschrift- of audiotrackbestanden verwijderen uit een video:**

1. Navigeer naar het video-element waarvan u de standaardaudiotrack wilt instellen.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram Eigenschappen (een cirkel met een &quot;i&quot; erin).
1. Selecteer op de pagina Eigenschappen de optie **[!UICONTROL Captions & Audio Tracks]** tab.
1. Voer een van de volgende handelingen uit:

   * Bijschriften—Onder de **Bijschriften** , selecteert u een of meer bijschriftbestanden die u uit de video wilt verwijderen en selecteert u vervolgens **[!UICONTROL Delete]**.
   * Audiotracks—Onder de **Audiotracks** , selecteert u een of meer audiotrackbestanden die u uit de video wilt verwijderen en selecteert u **[!UICONTROL Delete]**.

1. Selecteer in het dialoogvenster Verwijderen **[!UICONTROL OK]**.
1. Publiceer de video.

### Bijschrift- of audiotrackbestanden downloaden die naar een video zijn geüpload

U kunt een of meer bijschrift- of audiotrackbestanden downloaden die u hebt geüpload voor gebruik met een video. U kunt alle geselecteerde bestanden downloaden als ZIP-bestand of een aparte downloadmap maken voor elk bestand.

De oorspronkelijke audiotrack die uit een primair bestand is gehaald, kan niet worden gedownload.

**Bijschrift- of audiotrackbestanden downloaden van een video:**

1. Navigeer naar het video-element waarvan u de standaardaudiotrack wilt instellen.
1. Selecteer het video-element in de modus voor selectie van elementen in de lijstweergave of de kaartweergave.
1. Selecteer op de werkbalk het pictogram Eigenschappen (een cirkel met een &quot;i&quot; erin).
1. Selecteer op de pagina Eigenschappen de optie **[!UICONTROL Captions & Audio Tracks]** tab.
1. Voer een van de volgende handelingen uit:

   * Bijschriften—Onder de **Bijschriften** , selecteert u een of meer bijschriftbestanden die u van de video wilt downloaden en selecteert u vervolgens **[!UICONTROL Download]**.
   * Audiotracks—Onder de **Audiotracks** Selecteer een of meer audiotrackbestanden die u van de video wilt downloaden en selecteer vervolgens **[!UICONTROL Download]**.

1. Stel in het dialoogvenster Downloaden de volgende opties in:

   | Optie | Beschrijving |
   |--- |--- |
   | Opslaan als | Gebruik de standaardbestandsnaam die u in het tekstveld Opslaan als hebt opgegeven of geef uw eigen naam op. |
   | Een aparte map maken voor elk element | Maak een map voor elk bijschriftbestand of audiotrackbestand dat u hebt geselecteerd om te downloaden. |
   | E-mail | Gebruik uw standaard e-mailprogramma om het .zip-bestand naar een opgegeven e-mailadres te verzenden. |
   | Assets | Hiermee geeft u het aantal bestanden op dat u downloadt en de gecombineerde totale grootte van alle geselecteerde bestanden. Als u deze optie uitschakelt, wordt het dialoogvenster **[!UICONTROL Download]** , zodat u geen bestanden kunt downloaden. |
1. Selecteren **[!UICONTROL Download]**.
1. Publiceer de video. Zie [Elementen publiceren](publishing-dynamicmedia-assets.md).




## Gesloten bijschriften toevoegen aan video {#adding-captions-to-video}

>[!IMPORTANT]
>
>Adobe beveelt aan [mogelijkheid voor meerdere bijschriften en audiotracks inschakelen](#enable-dash) op je Dynamic Media-account. Zo kunt u profiteren van de nieuwste Dynamic Media-backendarchitectuur en een vereenvoudigde workflow voor het toevoegen van bijschriften, bijschriften en audiotracks aan uw video&#39;s.

U kunt het bereik van uw video&#39;s uitbreiden naar wereldwijde markten door ondertiteling toe te voegen aan enkele video&#39;s of aan Adaptive Video Sets. Door ondertiteling toe te voegen, vermijdt u de behoefte om de audio te duwen, of de behoefte om inheemse sprekers te gebruiken om de audio voor elke verschillende taal opnieuw op te nemen. De video wordt afgespeeld in de taal waarin deze is opgenomen. Bijschriften in vreemde talen worden weergegeven zodat mensen in verschillende talen het audiogedeelte nog steeds kunnen begrijpen.

Ondertiteling met gesloten deuren zorgt ook voor betere toegankelijkheid voor doven of slechthorenden.

>[!NOTE]
>
>De videospeler die u gebruikt moet de vertoning van gesloten titels steunen.

Zie ook [Toegankelijkheid in Dynamic Media](/help/assets/dynamic-media/accessibility-dm.md).

Dynamic Media kan bijschriftbestanden omzetten in de indeling JSON (JavaScript Object Notation). Met deze conversie kunt u de JSON-tekst insluiten in een webpagina als een verborgen, maar volledige transcriptie van de video. Zoekprogramma&#39;s kunnen de inhoud dan verkennen of indexeren, zodat de video&#39;s gemakkelijker te vinden zijn en klanten meer informatie krijgen over de video-inhoud.

Zie [Statische (niet-afbeeldings) inhoud bedienen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents.html#image-serving-api) voor meer informatie over het gebruik van de functie JSON in een URL.

**Bijschriften toevoegen aan video:**

1. U kunt een toepassing of service van derden gebruiken om uw videobijschriftbestand te maken.

   Zorg ervoor dat het bestand dat u maakt, voldoet aan de WebVTT-standaard (Web Video Text Tracks). De bestandsnaamextensie voor ondertiteling is .VTT. U kunt meer informatie over de WebVTT ondertitelingsnorm leren.

   Zie [WebVTT: De indeling Web Video Text Tracks](https://w3c.github.io/webvtt/).

   Er zijn veel websites die zowel gratis als premiumtools en -services bieden die u kunt gebruiken om WebVTT-bijschriftbestanden te maken buiten Dynamic Media. <!-- THE FOLLOWING LINK IS NO LONGER LIVE. CHECKED DECEMBER 13, 2023 For example, to create a simple video caption file with no styling, you can use the following free online caption authoring and editing tool: -->

   <!-- [WebVTT Caption Maker](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   For best results, use the tool in Internet Explorer 9 or above, Google Chrome, or Safari.

   In the tool, in the **[!UICONTROL Enter URL of video file]** field, paste the copied URL of your video file and then select **[!UICONTROL Load]**. See [Obtain a URL for an Asset](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset) to get the URL to the video file itself which you can then paste into the **[!UICONTROL Enter URL of video file field]**. Internet Explorer, Chrome, or Safari can then natively play back the video.-->

Volg de aanwijzingen op het scherm van een site om het WebVTT-bestand te ontwerpen en op te slaan. Wanneer u klaar bent, kopieert u de inhoud van het bijschriftbestand en plakt u deze in een teksteditor zonder opmaak en slaat u het bestand op met de bestandsnaamextensie VTT.

>[!NOTE]
>
>Voor algemene ondersteuning van videobijschriften in meerdere talen, vereist de WebVTT-standaard dat u afzonderlijke .vtt-bestanden maakt en dat u elke taal die u wilt ondersteunen, aanroept.

Over het algemeen wilt u het VTT-bestand van het bijschrift dezelfde naam geven als het videobestand en dit bestand toevoegen met de landinstelling van de taal, zoals -EN, of -FR of -DE. Op deze manier kunt u het genereren van video-URL&#39;s automatiseren met behulp van uw bestaande systeem voor webcontentbeheer.

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

In het bovenstaande voorbeeld: `Chapter 1` is de cue-id en is optioneel. De actieduur van `00:00:000 --> 01:04:364` geeft de begin- en eindtijd van het hoofdstuk aan, in `00:00:000` gebruiken. De laatste drie cijfers zijn milliseconden en kunnen als volgt worden verlaten `000`, indien gewenst. De titel van het hoofdstuk `The bicycle store behind it all` Dit is de feitelijke beschrijving van de inhoud van het hoofdstuk. De actidentificator, de begintijd en de hoofdstuktitel worden allemaal in een pop-up in de videospeler weergegeven wanneer een gebruiker de muisaanwijzer boven een visueel actiepunt in de tijdlijn plaatst.

Omdat u een HTML5-videoviewer gebruikt, moet u ervoor zorgen dat het hoofdstukbestand dat u maakt, voldoet aan de WebVTT-standaard (Web Video Text Tracks). De bestandsextensie van het hoofdstuk is .VTT. U kunt meer informatie over de WebVTT ondertitelingsnorm leren.

Zie [WebVTT: De indeling Web Video Text Tracks](https://w3c.github.io/webvtt/).

**Hoofdstukmarkeringen aan video toevoegen:**

1. Sla het VTT-bestand op in UTF8-codering, zodat u problemen met tekenuitvoering in de hoofdstuktiteltekst voorkomt.

   Over het algemeen wilt u het hoofdstuk VTT-bestand dezelfde naam geven als het videobestand en het toevoegen met hoofdstukken. Op deze manier kunt u het genereren van video-URL&#39;s automatiseren met behulp van uw bestaande systeem voor webcontentbeheer.
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



## Videominiaturen {#about-video-thumbnails}

Een videominiatuur is een verkleinde versie van een videoframe of een afbeeldingselement dat de video voor de klant vertegenwoordigt. De miniatuur moet de klant aanmoedigen om de video te selecteren.

Aan alle video&#39;s in de Experience Manager moet een miniatuur zijn gekoppeld. U kunt een miniatuur niet verwijderen zonder deze te vervangen. Wanneer u een video uploadt naar Experience Manager, wordt standaard het eerste frame gebruikt als miniatuur. U kunt de miniatuur echter aanpassen voor bijvoorbeeld branding of visuele zoekopdracht. Wanneer u een videominiatuur aanpast, kunt u de video afspelen en pauzeren op het frame dat u wilt gebruiken. U kunt ook een afbeeldingselement selecteren dat u al hebt geüpload en *gepubliceerd* in uw Digital Asset Manager.

Wanneer de miniatuur voor een video wordt gewijzigd, wordt het genereren van miniaturen via de Asset compute Service bij het opnieuw verwerken van de video overgeslagen.

De mogelijkheid om een videominiatuur aan te passen is alleen beschikbaar nadat u een videoprofiel hebt toegepast op de map waarin de video zich bevindt.

### Een aangepaste videominiatuur toevoegen {#adding-a-custom-video-thumbnail}

1. Zorg ervoor dat u al het volgende hebt gedaan:

   * Er is een map gemaakt voor uw video-elementen.
   * [Een videoprofiel op de map toepassen](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).

   * [Uw video&#39;s zijn geüpload naar de map](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).

1. Navigeer naar een geüpload video-element waarvan u de miniatuurafbeelding wilt wijzigen.
1. In de modus voor selectie van middelen **[!UICONTROL List View]** of **[!UICONTROL Card View]** selecteert u het video-element.
1. Selecteer op de werkbalk de optie **[!UICONTROL Properties]** pictogram (een cirkel met een &quot;i&quot; erin).
1. Selecteer op de pagina Eigenschappen van video de optie **[!UICONTROL Change Thumbnail]**.
1. Voer een van de volgende handelingen uit op de pagina Miniatuur wijzigen:

   * Een frame uit de video gebruiken als de nieuwe miniatuur:

      * Selecteer op de werkbalk de optie **[!UICONTROL Select Frame from video]**.
      * Selecteer de knop Afspelen en selecteer vervolgens de knop Pauzeren in het frame dat u wilt vastleggen als de nieuwe miniatuur van de video.

   * Een afbeeldingselement gebruiken als de nieuwe miniatuur:

      * Selecteer op de werkbalk de optie **[!UICONTROL Select Thumbnail from Assets]**.
      * Selecteren **[!UICONTROL Select Thumbnail]**.
      * Navigeer naar een eerder geüpload en gepubliceerd afbeeldingselement dat u wilt gebruiken. De grootte van het element wordt automatisch gewijzigd om te dienen als miniatuurafbeelding voor de video.
      * Selecteer het afbeeldingselement en selecteer vervolgens **[!UICONTROL Select]**.

1. Selecteer op de pagina Miniatuur wijzigen de optie **[!UICONTROL Save Change]**.
1. Selecteer in de rechterbovenhoek van de pagina Eigenschappen van video de optie **[!UICONTROL Save & Close]**.



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

Video&#39;s die in Dynamic Media worden verwerkt, kunnen worden gebruikt in de vorm van verouderde viewers en ook door rechtstreeks toegang te krijgen tot de manifest-URL&#39;s en deze af te spelen via uw eigen aangepaste viewers. Hier volgt de API voor het ophalen van manifest-URL&#39;s voor een video.

### Over de getVideoManifestURI-API

De `getVideoManifestURI`API is beschikbaar via c`q-scene7-api:com.day.cq.dam.scene7.api` en kan worden gebruikt om de volgende manifest-URL&#39;s te genereren:

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
| `manifestType` | Kan `ManifestType.DASH` of `ManifestType.HLS` |
| `onlyIfPublished` | Ingesteld op true voor het geval dat de manifest-uri alleen wordt gegenereerd als deze wordt gepubliceerd en beschikbaar is op de leveringslaag. |

Als u de manifest-URL&#39;s voor video&#39;s wilt ophalen met de bovenstaande methode, voegt u een [videocoderingsprofiel](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) naar de map &quot;upload videos&quot;. Dynamic Media verwerkt deze video&#39;s op basis van de coderingen in het videocoderingsbestand dat aan de map is toegewezen. Nu kunt u de bovenstaande API aanroepen om manifest-URL&#39;s voor de geüploade video&#39;s op te halen.

### Foutscenario&#39;s

De API retourneert null als er fouten zijn. Uitzonderingen worden geregistreerd in foutenlogboeken voor Experience Managers. Al dergelijke geregistreerde fouten beginnen met `Could not generate Video Manifest URI`. Dergelijke fouten kunnen in de volgende scenario&#39;s optreden:

* An `IllegalArgumentException` wordt geregistreerd voor om het even welk van het volgende:

   * De `resource` doorgegeven parameter is null.
   * De `resource` doorgegeven parameter is geen video.
   * De `manifestType` doorgegeven parameter is null.
   * De `onlyIfPublished` parameter wordt doorgegeven als true, maar de video wordt niet gepubliceerd.
   * De video is niet opgenomen met een adaptieve videoset van Dynamic Media.

* `IOException` wordt geregistreerd als er een probleem is dat verbinding maakt met Dynamic Media.
* `UnsupportedOperationException` wordt geregistreerd wanneer een `manifestType` doorgegeven parameter is `ManifestType.DASH`, terwijl de video niet is verwerkt met de indeling DASH.

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





