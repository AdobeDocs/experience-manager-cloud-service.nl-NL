---
title: Dynamische mediavideoprofielen
description: Dynamische media wordt al geleverd met een vooraf gedefinieerd adaptief videocoderingsprofiel. De instellingen in dit out-of-the-box profiel zijn geoptimaliseerd om uw klanten de beste kijkervaring mogelijk te maken. U kunt ook slimme uitsnijdingen toevoegen aan uw video's.
contentOwner: Rick Brough
feature: Asset Management,Video Profiles,Renditions,Best Practices
role: User
exl-id: 07bfd353-c105-4677-a094-b70c1098fb7f
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '3517'
ht-degree: 3%

---

# Dynamische mediavideoprofielen{#video-profiles}

Dynamische media wordt al geleverd met een vooraf gedefinieerd adaptief videocoderingsprofiel. De instellingen in dit out-of-the-box profiel zijn geoptimaliseerd om uw klanten de beste kijkervaring mogelijk te maken. Wanneer u tijdens het afspelen uw primaire bronvideo&#39;s codeert met het profiel Adaptieve videocodering, past de videospeler automatisch de kwaliteit van de videostream aan op basis van de snelheid van de internetverbinding van uw klanten. Deze handeling wordt &#39;adaptieve bitsnelheidstreaming&#39; genoemd.

Hier volgen nog andere factoren die de kwaliteit van uw video&#39;s bepalen:

* **Resolutie van de geuploade primaire bronvideo**

  Als de MP4-video met een lagere resolutie, zoals 240p of 360p, is opgenomen, kan deze niet in HD worden gestreamd.

* **de grootte van de videospeler**

  Standaard is de breedte in het profiel Adaptieve videocodering ingesteld op Automatisch. Ook tijdens het afspelen wordt de beste kwaliteit gebruikt op basis van de grootte van de speler.

Zie [ Beste praktijken voor Video Coderen ](/help/assets/dynamic-media/video.md#best-practices-for-encoding-videos).

Zie ook [ Beste praktijken voor het Organiseren van uw Digitale Assets voor het gebruiken van Profielen van de Verwerking ](/help/assets/organize-assets.md).


>[!NOTE]
>
>Als u de metagegevens van een video en de bijbehorende miniaturen van videoafbeeldingen wilt genereren, moet de video zelf het coderingsproces doorlopen in Dynamische media. In Adobe Experience Manager codeert de **[!UICONTROL Dynamic Media Encode Video]** -workflow video als u Dynamic Media hebt ingeschakeld en Cloud Services voor video hebt ingesteld. In deze workflow worden de historie en informatie over fouten van het workflowproces vastgelegd. Zie [ video het coderen van de Monitor en YouTube het publiceren vooruitgang ](/help/assets/dynamic-media/video.md#monitoring-video-encoding-and-youtube-publishing-progress). Als u Dynamic Media hebt ingeschakeld en Video Cloud Services hebt ingesteld, wordt de workflow van **[!UICONTROL Dynamic Media Encode Video]** automatisch toegepast wanneer u een video uploadt. (Als u geen gebruik maakt van Dynamische media, wordt de **[!UICONTROL DAM Update Asset]** -workflow van kracht.)
>
>Metagegevens zijn handig wanneer u naar elementen zoekt. De miniaturen zijn statische videobeelden die tijdens het coderen worden gegenereerd. Ze zijn vereist door het Experience Manager-systeem en worden gebruikt in de gebruikersinterface om u te helpen video&#39;s visueel te identificeren in de weergave Kaarten, de weergave Zoekresultaten en de weergave Lijst met middelen. De gegenereerde miniaturen worden weergegeven wanneer u het pictogram Uitvoeringen (een palet Painter) van een gecodeerde video selecteert.

Wanneer u klaar bent met het maken van het videoprofiel, past u het toe op een of meerdere mappen. Zie [ een VideoProfiel op omslagen ](#applying-a-video-profile-to-folders) toepassen.

Om geavanceerde verwerkingsparameters voor andere activatypes te bepalen, zie [ activa verwerking ](/help/assets/dynamic-media/config-dm.md#configuring-asset-processing) vormen.

Zie ook [ Profielen voor de Meta-gegevens van de Verwerking, Beelden, en Video&#39;s ](/help/assets/dynamic-media/about-image-video-profiles.md).

## Voorinstellingen voor adaptieve videocodering {#adaptive-video-encoding-presets}

In de volgende tabel worden de aanbevolen procedures aangegeven voor het coderen van profielen voor adaptieve videostreaming naar mobiele apparaten en tablets, en bureaubladcomputers. U kunt deze voorinstellingen gebruiken voor elke video met de hoogte-breedteverhouding.

<table>
 <tbody>
  <tr>
   <td><strong>Video-indelingscodec</strong></td>
   <td><strong>Videogrootte - Breedte (px)</strong></td>
   <td><strong>Videogrootte - Hoogte (px)</strong></td>
   <td><strong>Hoogte-breedteverhouding behouden?</strong></td>
   <td><strong>Videobitsnelheid (Kbps)</strong></td>
   <td><strong>Videoframesnelheid (FPS)</strong></td>
   <td><strong>Audiocodec</strong></td>
   <td><strong>Audiobitsnelheid (Kbps)</strong></td>
  </tr>
  <tr>
   <td><p>MP4 H.264 (mp4)</p> </td>
   <td>auto</td>
   <td>360</td>
   <td>Ja</td>
   <td>730</td>
   <td>30</td>
   <td>Dolby HE-AAC</td>
   <td>128</td>
  </tr>
  <tr>
   <td><p>MP4 H.264 (mp4)</p> </td>
   <td>auto</td>
   <td>540</td>
   <td>Ja</td>
   <td>2000 <br /> </td>
   <td>30</td>
   <td>Dolby HE-AAC</td>
   <td>128</td>
  </tr>
  <tr>
   <td><p>MP4 H.264 (mp4)</p> </td>
   <td>auto</td>
   <td>720 <br /> </td>
   <td>Ja</td>
   <td>3000 <br /> </td>
   <td>30</td>
   <td>Dolby HE-AAC</td>
   <td>128</td>
  </tr>
 </tbody>
</table>

## Informatie over slim uitsnijden in videoprofielen {#about-smart-crop-video}

Slim uitsnijden voor video is een optionele functie die beschikbaar is in videoprofielen. Het is een gereedschap dat Adobe Sensei gebruikt om automatisch het brandpunt te detecteren en uit te snijden in adaptieve video of progressieve video die u hebt geüpload, ongeacht de grootte.

Ondersteunde video-indelingen voor slim uitsnijden zijn MP4, MKV, MOV, AVI, FLV en WMV.

De maximaal ondersteunde videobestandsgrootte voor slim uitsnijden is aan de volgende criteria te voldoen:

* Duur van vijf minuten.
* 30 frames per seconde (FPS).
* Bestandsgrootte van 300 MB.

Adobe Sensei is beperkt tot 9000 frames. Dat wil zeggen, vijf minuten bij 30 FPS. Als uw video een hogere FPS heeft, neemt de maximaal ondersteunde videoduur af. Een video van 60 FPS moet bijvoorbeeld tweeënhalve minuut duren voordat Adobe Sensei en SmartCrop deze ondersteunen.

![ Slim Gewas voor Video ](assets/smart-crop-video.png)

>[!IMPORTANT]
>
>Als u slimme videoclips alleen wilt gebruiken, moet u een of meer voorinstellingen voor videocodering opnemen in uw videoprofiel.

Als u SmartCrop voor video wilt gebruiken, maakt u een adaptief of progressief videocoderingsprofiel. Als onderdeel van uw profiel gebruikt u het gereedschap **[!UICONTROL Smart Crop Ratio]** om vooraf gedefinieerde hoogte-breedteverhoudingen te selecteren. Nadat u bijvoorbeeld de videocoderingsvoorinstellingen hebt gedefinieerd, kunt u een definitie &quot;Mobiel liggend&quot; toevoegen met een hoogte-breedteverhouding van 16 x 9 en een definitie &quot;Mobiel staand&quot; met een hoogte-breedteverhouding van 9 x 16. Andere hoogte-breedteverhoudingen of uitsnijdverhoudingen waaruit u 1x1, 4x3 en 4x5 kunt kiezen.

![ geef een video het coderen profiel met slimme gewas ](assets/edit-smart-crop-video2.png) uit

Met de schuifregelaar helemaal rechts van **[!UICONTROL Smart Crop Ratio]** in de gebruikersinterface kunt u slimme uitsnijden in het videoprofiel in- of uitschakelen.

Nadat u het videoprofiel hebt gemaakt en opgeslagen, kunt u het toepassen op de gewenste mappen.

Zie [ Videoprofielen toepassen op specifieke omslagen ](#applying-video-profiles-to-specific-folders) of [ globaal een VideoProfiel toepassen ](#applying-a-video-profile-globally).

Zie ook [ Slimme uitsnijding voor beelden ](image-profiles.md).

## Een videoprofiel maken voor adaptieve streaming bitsnelheid {#creating-a-video-encoding-profile-for-adaptive-streaming}

Dynamische media wordt al geleverd met een vooraf gedefinieerd adaptief videocoderingsprofiel - een groep video-uploadinstellingen voor MP4 H.264-systeem dat is geoptimaliseerd voor de beste kijkervaring. U kunt dit profiel gebruiken wanneer u uw video&#39;s uploadt.

Als dit vooraf gedefinieerde profiel echter niet aan uw behoeften voldoet, kunt u desgewenst uw eigen adaptieve videocoderingsprofiel maken. Als u de instelling **[!UICONTROL Encode for adaptive streaming]** gebruikt, worden alle coderingsvoorinstellingen die u aan het profiel toevoegt, gevalideerd. Deze functionaliteit zorgt ervoor dat alle video&#39;s dezelfde hoogte-breedteverhouding hebben. Bovendien worden de gecodeerde video&#39;s beschouwd als een multibitsnelheid die is ingesteld voor streaming.

Wanneer u het videocoderingsprofiel maakt, ziet u dat de meeste coderingsopties vooraf zijn gevuld met de aanbevolen standaardinstellingen. Als u echter een andere waarde selecteert dan de aanbevolen standaardwaarde, kan dit resulteren in een slechte videokwaliteit tijdens het afspelen en andere prestatieproblemen.

Voor alle MP4 H.264-videocoderingsvoorinstellingen in het profiel worden dus de volgende waarden gevalideerd om ervoor te zorgen dat deze voor afzonderlijke coderingsvoorinstellingen in het profiel hetzelfde zijn, zodat adaptieve bitsnelheidstreaming mogelijk wordt:

* Video-indelingscodec - MP4 H.264 (.mp4)
* Audiocodec
* Audiobitsnelheid
* Hoogte-breedteverhouding behouden
* Codering met twee controles
* Constante bitsnelheid
* H264-profiel
* Samplingfrequentie audio

Als de waarden niet gelijk zijn, kunt u doorgaan met het maken van het profiel. Adaptieve bitsnelheidstreaming is echter niet mogelijk. In plaats daarvan ervaren gebruikers het streamen met één bitsnelheid. Het wordt aanbevolen de coderingsinstellingen te bewerken om dezelfde waarden te gebruiken voor afzonderlijke coderingsvoorinstellingen in het profiel. (De editor Videoprofiel/Voorinstelling past de pariteit van de aangepaste instellingen voor videocodering toe als &quot;Coderen voor adaptief streamen&quot; is ingeschakeld.)

Zie ook [ een video het coderen profiel voor het progressieve stromen ](#creating-a-video-encoding-profile-for-progressive-streaming) creëren.

Zie ook [ Beste praktijken voor video het coderen ](/help/assets/dynamic-media/video.md#best-practices-for-encoding-videos).

Om geavanceerde verwerkingsparameters voor andere activatypes te bepalen, zie [ activa verwerking ](/help/assets/dynamic-media/config-dm.md#configuring-asset-processing) vormen.

**om een VideoProfiel voor het adaptieve bitrate stromen tot stand te brengen:**

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Video Profiles]** .
1. Selecteer **[!UICONTROL Create]** .
1. Voer een naam en beschrijving in voor het profiel.
1. Selecteer **[!UICONTROL Add Video Encoding Preset]** op de pagina Voorinstellingen voor videocodering maken/bewerken.
1. Stel op het tabblad **[!UICONTROL Basic]** de video- en audio-opties in.
Selecteer het informatiepictogram naast elke optie voor meer beschrijvingen of aanbevolen instellingen op basis van de geselecteerde video-indelingscodec.
1. Controleer of onder de kop Videogrootte de optie **[!UICONTROL Keep aspect ratio]** is ingeschakeld.
1. Stel de resolutie van de videoframegrootte in pixels in. Gebruik de waarde van **[!UICONTROL Auto]** om automatisch te schalen zodat deze overeenkomt met de hoogte-breedteverhouding van de bron (breedte-hoogteverhouding). Bijvoorbeeld Auto x 480 of 640 x Auto.

1. Voer een van de volgende handelingen uit:

   * Typ **[!UICONTROL auto]** in het veld **[!UICONTROL Width]** . Voer in het veld **[!UICONTROL Height]** een waarde in pixels in.

   * Om u te helpen de grootte van de video visualiseren, selecteer het pictogram van de Informatie (i) rechts van **[!UICONTROL Height]** om de pagina van de Rekenmachine van de Grootte te te openen. Gebruik **[!UICONTROL Size Calculator]** om de gewenste videoafmetingen in te stellen (weergegeven door het blauwe vak). Selecteer **[!UICONTROL X]** in de rechterbovenhoek als u klaar bent.

1. (Optioneel) Selecteer de tab **[!UICONTROL Advanced]** en schakel het selectievakje **[!UICONTROL Use Default Values]** in (aanbevolen). U kunt ook geavanceerde video- en audio-instellingen wijzigen.
1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina om de voorinstelling op te slaan.
1. Voer een van de volgende handelingen uit:
   * Herhaal stap 4-10 om meer coderingsvoorinstellingen te maken. (Voor adaptieve videostreaming zijn meerdere videovoorinstellingen vereist.)
   * Ga door met de volgende stap.

1. (Optioneel) Ga als volgt te werk om een slimme videoclip toe te voegen aan de video&#39;s waarop dit profiel is toegepast:
   * Selecteer **[!UICONTROL Add New]** op de pagina Videoprofiel bewerken rechts van de kop Slimme uitsnijdverhouding.
   * Typ in het veld Naam een naam voor de uitsnijdverhouding, zodat u deze gemakkelijk kunt herkennen.
   * Selecteer in de vervolgkeuzelijst **[!UICONTROL Crop Ratio]** de verhouding die u wilt gebruiken.

1. Voer een van de volgende handelingen uit:

   * Voeg desgewenst nieuwe uitsnijdverhoudingen toe.
   * Ga door met de volgende stap.

1. Selecteer in de rechterbovenhoek van de pagina nogmaals **[!UICONTROL Save]** om het profiel op te slaan.

U kunt het profiel nu toepassen op mappen die video&#39;s bevatten. Zie [ Toepassend een VideoProfiel op omslagen ](#applying-a-video-profile-to-folders) of [ Toepassend globaal een VideoProfiel ](#applying-a-video-profile-globally).

## Een videoprofiel maken voor progressieve streaming {#creating-a-video-encoding-profile-for-progressive-streaming}

Als u ervoor kiest de optie **[!UICONTROL Encode for adaptive streaming]** niet te gebruiken, worden alle coderingsvoorinstellingen die u aan het profiel toevoegt, behandeld als afzonderlijke video-uitvoeringen voor streaming met enkele bitsnelheid of progressieve videoverzending. Er is ook geen validatie om ervoor te zorgen dat alle video-uitvoeringen dezelfde hoogte-breedteverhouding hebben.

De ondersteunde video-indelingscodec is H.264 (.mp4). <!-- use to also include WebM but was requested for removal by Riya Midha in email dated October 14, 2024 -->

Zie ook [ een video het coderen profiel voor het adaptieve bitrate stromen ](#creating-a-video-encoding-profile-for-adaptive-streaming) creëren.

Zie ook [ Beste praktijken voor Video Coderen ](/help/assets/dynamic-media/video.md#best-practices-for-encoding-videos).

Om geavanceerde verwerkingsparameters voor andere activa te bepalen types, zie [ Vormend de Verwerking van Activa ](/help/assets/dynamic-media/config-dm.md#configuring-asset-processing).

**om een VideoProfiel voor het progressieve stromen tot stand te brengen:**

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Video Profiles]** .
1. Selecteer **[!UICONTROL Create]** .
1. Voer een naam en beschrijving in voor het profiel.
1. Selecteer **[!UICONTROL Add Video Encoding Preset]** op de pagina Voorinstellingen voor videocodering maken/bewerken.
1. Stel op het tabblad **[!UICONTROL Basic]** de video- en audio-opties in.
Selecteer het informatiepictogram naast elke optie voor meer beschrijvingen of aanbevolen instellingen op basis van de geselecteerde video-indelingscodec.
1. (Optioneel) Schakel **[!UICONTROL Keep aspect ratio]** uit onder de kop Videogrootte.
1. Ga als volgt te werk:
   * Typ **[!UICONTROL auto]** in het veld **[!UICONTROL Width]** .
   * Voer in het veld **[!UICONTROL Height]** een waarde in pixels in.
Om u te helpen de grootte van de video visualiseren, selecteer het de informatiepictogram van de Hoogte om de **[!UICONTROL Size Calculator]** pagina te openen. Gebruik de pagina **[!UICONTROL Size Calculator]** om de gewenste videogrootte (blauw vak) verder in te stellen. Als u klaar bent, selecteert u **[!UICONTROL X]** in de rechterbovenhoek van het dialoogvenster.
1. (Optioneel) Voer een van de volgende handelingen uit:

   * Selecteer de tab **[!UICONTROL Advanced]** en controleer of het selectievakje **[!UICONTROL Use Default Values]** is ingeschakeld (aanbevolen).

   * Schakel het selectievakje **[!UICONTROL Use Default Values]** uit en geef de gewenste video-instellingen en audio-instellingen op.
Selecteer het informatiepictogram naast elke optie voor meer beschrijvingen of aanbevolen instellingen op basis van de geselecteerde video-indelingscodec.

1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina om de voorinstelling op te slaan.
1. Voer een van de volgende handelingen uit:

   * Herhaal stap 4-9 om meer coderingsvoorinstellingen te maken.
   * Ga door met de volgende stap.

1. (Optioneel) Ga als volgt te werk om een slimme videoclip toe te voegen aan de video&#39;s waarop dit profiel is toegepast:

   * Selecteer **[!UICONTROL Add New]** op de pagina Videoprofiel bewerken rechts van de kop Slimme uitsnijdverhouding.
   * Typ in het veld Naam een naam voor de uitsnijdverhouding, zodat u deze gemakkelijk kunt herkennen.
   * Selecteer in de vervolgkeuzelijst **[!UICONTROL Crop Ratio]** de verhouding die u wilt gebruiken.

1. Voer een van de volgende handelingen uit:

   * Voeg desgewenst nieuwe uitsnijdverhoudingen toe.
   * Ga door met de volgende stap.

1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina om het profiel op te slaan.

U kunt het profiel nu toepassen op mappen die video&#39;s bevatten. Zie [ een VideoProfiel op omslagen ](#applying-a-video-profile-to-folders) toepassen of [ globaal een VideoProfiel toepassen ](#applying-a-video-profile-globally).

## Parameters voor aangepaste videocodering gebruiken {#using-custom-added-video-encoding-parameters}

U kunt een bestaand coderingsprofiel voor video bewerken om te profiteren van de geavanceerde parameters voor videocodering die niet in de gebruikersinterface worden gevonden wanneer u een videoprofiel maakt of bewerkt in Experience Manager. U kunt een of meer geavanceerde parameters, zoals minBitrate en maxBitrate, aan uw bestaand profiel toevoegen.

**om douane-toegevoegde video het coderen parameters te gebruiken:**

1. Selecteer het Experience Manager-logo en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]** .
1. Navigeer op de CRXDE Lite-pagina in het paneel Verkenner aan de linkerkant naar het volgende:

   `/conf/global/settings/dam/dm/presets/video/*name_of_video_encoding_profile_to_edit`

1. In het deelvenster in de rechterbenedenhoek van de pagina op het tabblad Eigenschappen geeft u de **[!UICONTROL Name]**, **[!UICONTROL Type]** en **[!UICONTROL Value]** van de parameter op u wilt gebruiken.

   U kunt de volgende geavanceerde parameters gebruiken:

<table>
 <tbody>
  <tr>
   <td><strong>Naam</strong></td>
   <td><strong> Beschrijving </strong><br /> </td>
   <td><strong> Type </strong><br /> </td>
   <td><strong>Waarde</strong></td>
  </tr>
  <tr>
   <td><code>h264Level</code></td>
   <td>H.264-niveau voor codering. Normaal wordt dit niveau automatisch bepaald op basis van de coderingsinstellingen die u gebruikt.</td>
   <td><code>String</code></td>
   <td><p>* h264 niveau</p> <p>3,0 = 30, 1,3 = 13)</p> <p>Geen standaardwaarde.</p> </td>
  </tr>
  <tr>
   <td><code>keyframe</code></td>
   <td>Het doelaantal frames tussen hoofdframes. Bereken deze waarde zodat u een hoofdframe elke 2-10 seconden kunt genereren. Bij 30 frames per seconde is het hoofdframe-interval bijvoorbeeld 60-300.<br /> <br /> Met lagere keyframe-intervallen verbetert u het zoeken naar streams en het schakelen tussen streams voor adaptieve videocoderingen. De kwaliteit van video's met veel beweging wordt ook verbeterd. Omdat hoofdframes de grootte van een bestand echter vergroten, resulteert een lager hoofdframe-interval meestal in een lagere algemene videokwaliteit bij een bepaalde bitsnelheid.</td>
   <td><code>String</code></td>
   <td><p>Positief getal.</p> <p>De standaardwaarde is 300.</p> <p>De aanbevolen waarde voor HLS of DASH (adaptieve bitsnelheidstreaming) is 60-90.</p> </td>
  </tr>
  <tr>
   <td><code>minBitrate</code></td>
   <td><p>Minimale bitsnelheid voor coderingen met variabele bitsnelheid, in Kbps (kilobits per seconde).</p> <p>Deze parameter is alleen van toepassing wanneer <strong> Constante bitsnelheid gebruiken </strong> op het tabblad Geavanceerd is uitgeschakeld wanneer u een videocoderingsprofiel maakt of bewerkt.</p> <p>Zie ook <a href="/help/assets/dynamic-media/video.md#bitrate"> Bitsnelheid </a>.</p> </td>
   <td><code>String</code></td>
   <td><p>Positief getal, in Kbps.</p> <p>Geen standaardwaarde.</p> </td>
  </tr>
  <tr>
   <td><code>maxBitrate</code></td>
   <td><p>Maximale bitsnelheid voor codering van variabele bitsnelheid, in Kbps.</p> <p>Deze parameter is alleen van toepassing wanneer <strong> Constante bitsnelheid gebruiken </strong> op het tabblad Geavanceerd is uitgeschakeld wanneer u een videocoderingsprofiel maakt of bewerkt.</p> <p>Zie ook <a href="/help/assets/dynamic-media/video.md#bitrate"> Bitsnelheid </a>.</p> </td>
   <td><code>String</code></td>
   <td><p>Positief getal, in Kbps.</p> <p>Geen standaardwaarde. De aanbevolen waarde bedraagt echter maximaal twee keer de coderingsbitsnelheid.</p> </td>
  </tr>
  <tr>
   <td><code>audioBitrateCustom</code></td>
   <td>Stel waarde in op <code>true</code> om een constante bitsnelheid voor de audiostream te forceren, indien ondersteund door audiocodec.</td>
   <td><code>String</code></td>
   <td><p><code>true</code>/<code>false</code></p> <p>De standaardwaarde is <code>false</code> .</p> <p>De aanbevolen waarde voor HLS of DASH is <code>false</code> .</p> <p> </p> </td>
  </tr>
 </tbody>
</table>

![ chlimage_1-516 ](assets/chlimage_1-516.png)

1. Selecteer **[!UICONTROL Add]** in de rechterbenedenhoek van de pagina.
1. Voer een van de volgende handelingen uit:

   * Herhaal stap 3 en 4 om een andere parameter toe te voegen aan uw videocoderingsprofiel.
   * Selecteer **[!UICONTROL Save All]** in de linkerbovenhoek van de pagina.

1. Selecteer in de linkerbovenhoek van de CRXDE Lite-pagina het pictogram **[!UICONTROL Back Home]** om terug te keren naar Experience Manager.

### Een videoprofiel bewerken {#editing-a-video-encoding-profile}

U kunt elk videoprofiel bewerken dat u hebt gemaakt om videovoorinstellingen in dat profiel toe te voegen, te bewerken of te verwijderen.

Standaard kunt u het vooraf gedefinieerde, out-of-the-box **[!UICONTROL Adaptive Video Encoding]** -profiel dat bij Dynamische media is geleverd, niet bewerken. In plaats daarvan kunt u het profiel gemakkelijk kopiëren en opslaan met een nieuwe naam. Vervolgens kunt u de gewenste voorinstellingen bewerken in het gekopieerde profiel.

Zie ook [ Beste praktijken voor Video Coderen ](/help/assets/dynamic-media/video.md#best-practices-for-encoding-videos).

Om geavanceerde verwerkingsparameters voor andere activatypes te bepalen, zie [ activa verwerking ](/help/assets/dynamic-media/config-dm.md#configuring-asset-processing) vormen.

**om een VideoProfiel uit te geven:**

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Video Profiles]** .
1. Controleer op de pagina Videoprofielen de naam van één videoprofiel.
1. Selecteer **[!UICONTROL Edit]** op de werkbalk.
1. Bewerk de naam en beschrijving op de pagina Profiel videocodering.
1. U kunt het beste het selectievakje **[!UICONTROL Encode for adaptive streaming]** inschakelen.
Selecteer het informatiepictogram voor een beschrijving van adaptieve bitsnelheidstreaming. (Schakel dit selectievakje niet in als u een progressief videoprofiel bewerkt.)
1. Onder de kop Voorinstellingen videocodering kunt u voorinstellingen voor videocodering die het profiel vormen, toevoegen, bewerken of verwijderen.

   Selecteer het informatiepictogram naast elke optie op de tabbladen **[!UICONTROL Basic]** en **[!UICONTROL Advanced]** voor meer beschrijvingen of aanbevolen instellingen op basis van de geselecteerde video-indelingscodec.

1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina.

### Een videoprofiel kopiëren {#copying-a-video-encoding-profile}

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Video Profiles]** .
1. Controleer op de pagina Videoprofielen de naam van één videoprofiel.
1. Selecteer **[!UICONTROL Copy]** op de werkbalk.
1. Voer op de pagina Profiel videocodering een nieuwe naam in voor het profiel.
1. U kunt het beste het selectievakje **[!UICONTROL Encode for adaptive streaming]** inschakelen. Selecteer het informatiepictogram voor een beschrijving van adaptieve bitsnelheidstreaming. (Als u een progressief videoprofiel kopieert, schakelt u het selectievakje niet in.)

   Als in de modus Dynamische media - hybride een WebM-videovoorinstelling deel uitmaakt van het videoprofiel, is **[!UICONTROL Encode for adaptive streaming]** niet mogelijk omdat alle voorinstellingen MP4 moeten zijn.
1. Onder de kop Voorinstellingen videocodering kunt u voorinstellingen voor videocodering die het profiel vormen, toevoegen, bewerken of verwijderen.

   Selecteer het informatiepictogram naast elke optie op de tabbladen Standaard en Geavanceerd voor aanbevolen instellingen en beschrijvingen.

1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina.

### Een videoprofiel verwijderen {#deleting-a-video-encoding-profile}

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Video Profiles]** .
1. Controleer een of meer namen van videoprofielen op de pagina Videoprofielen.
1. Selecteer **[!UICONTROL Delete]** op de werkbalk.
1. Selecteer **[!UICONTROL OK]** .

## Een videoprofiel toepassen op mappen {#applying-a-video-profile-to-folders}

Wanneer u een videoprofiel toewijst aan een map, nemen eventuele submappen het profiel automatisch over van de bovenliggende map. U kunt daarom slechts één videoprofiel aan een map toewijzen. Denk daarom zorgvuldig na over de mapstructuur van de locatie waar u middelen uploadt, opslaat, gebruikt en archiveert.

Als u een ander videoprofiel aan een omslag toewees, treedt het nieuwe profiel het vorige profiel met voeten. De vorige bestaande mapelementen blijven ongewijzigd. Het nieuwe profiel wordt toegepast op de elementen die later aan de map worden toegevoegd.

Mappen waaraan een profiel is toegewezen, worden in de gebruikersinterface aangegeven met de naam van het profiel dat in de kaartnaam wordt weergegeven.

![ chlimage_1-517 ](assets/chlimage_1-517.png)

U kunt videoprofielen toepassen op specifieke mappen of op alle elementen.

U kunt elementen opnieuw verwerken in een map die al een bestaand videoprofiel heeft dat u later wijzigt. Zie [ het Opverwerken activa in een omslag ](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

### Een videoprofiel toepassen op specifieke mappen {#applying-video-profiles-to-specific-folders}

U kunt een videoprofiel toepassen op een map vanuit het menu **[!UICONTROL Tools]** of vanuit de map **[!UICONTROL Properties]** . In deze sectie wordt beschreven hoe u videoprofielen op beide manieren op mappen kunt toepassen.

Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

Zie ook [ activa in een omslag opnieuw verwerken nadat u zijn verwerkingsprofiel ](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) hebt uitgegeven.

#### Een videoprofiel toepassen op mappen via de gebruikersinterface Profielen {#applying-video-profiles-to-folders-by-way-of-the-profiles-user-interface}

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Video Profiles]** .
1. Selecteer het videoprofiel dat u wilt toepassen op een of meerdere mappen.
1. Selecteer **[!UICONTROL Apply Profile to Folders]** en selecteer de map of meerdere mappen die u wilt gebruiken om de nieuw geüploade elementen te ontvangen en selecteer **[!UICONTROL Apply]** . Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven terwijl u zich in **[!UICONTROL Card View]** bevindt.
U kunt [ de vooruitgang van een Videoverwerkingstaak van het Profiel ](#monitoring-the-progress-of-an-encoding-job) controleren.

#### Een videoprofiel vanuit eigenschappen toepassen op mappen {#applying-video-profiles-to-folders-from-properties}

1. Selecteer het Experience Manager-logo en navigeer naar **[!UICONTROL Assets]** en vervolgens naar de map waarop u een videoprofiel wilt toepassen.
1. Selecteer in de map het vinkje om het te selecteren en selecteer vervolgens **[!UICONTROL Properties]** .
1. Selecteer de tab **[!UICONTROL Video Profiles]** , selecteer het profiel in de vervolgkeuzelijst en selecteer **[!UICONTROL Save & Close]** . Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

   ![ chlimage_1-518 ](assets/chlimage_1-518.png)
U kunt [ de vooruitgang van een Videoverwerkingstaak van het Profiel ](#monitoring-the-progress-of-an-encoding-job) controleren.

### Een videoprofiel algemeen toepassen {#applying-a-video-profile-globally}

Naast het toepassen van een profiel op een map, kunt u er ook een globaal toepassen, zodat het geselecteerde profiel wordt toegepast op inhoud die in Experience Manager-elementen in een map is geüpload.

Zie ook [ activa in een omslag ](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) opnieuw verwerken.

**om een VideoProfiel globaal toe te passen:**

* Navigeer naar CRXDE Lite naar het volgende knooppunt: `/content/dam/jcr:content` . Voeg de eigenschap `videoProfile:/libs/settings/dam/video/dynamicmedia/<name of video encoding profile>` toe en selecteer **[!UICONTROL Save All]** .

  ![ chlimage_1-519 ](assets/chlimage_1-519.png)
* U kunt [ de vooruitgang van een Videoverwerkingstaak van het Profiel ](#monitoring-the-progress-of-an-encoding-job) controleren.

## De voortgang van een verwerkingstaak van een videoprofiel controleren {#monitoring-the-progress-of-an-encoding-job}

Er wordt een verwerkingsindicator (of voortgangsbalk) weergegeven waarmee u de voortgang van een verwerkingstaak van een videoprofiel visueel kunt controleren.

U kunt het `error.log` dossier ook bekijken om de vooruitgang van een het coderen baan te controleren, om te zien of wordt het coderen gebeëindigd, of om het even welke baanfouten te zien. De map `error.log` staat in de map `logs` waarin uw exemplaar van Experience Manager is geïnstalleerd.

## Een videoprofiel uit mappen verwijderen {#removing-a-video-profile-from-folders}

Wanneer u een videoprofiel uit een map verwijdert, wordt het verwijderen van het profiel uit de bovenliggende map automatisch overgenomen in alle submappen. Alle verwerking van bestanden die in de mappen zijn opgetreden, blijft echter intact.

U kunt een videoprofiel uit een map verwijderen vanuit het menu **[!UICONTROL Tools]** of vanuit de map **[!UICONTROL Folder Settings]** . In deze sectie wordt beschreven hoe u videoprofielen op beide manieren uit mappen kunt verwijderen.

### Een videoprofiel uit mappen verwijderen via de gebruikersinterface Profielen {#removing-video-profiles-from-folders-by-way-of-the-profiles-user-interface}

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Video Profiles]** .
1. Selecteer het videoprofiel dat u uit een of meerdere mappen wilt verwijderen.
1. Selecteer **[!UICONTROL Remove Profile from Folders]** en selecteer de map of meerdere mappen waaruit u het profiel wilt verwijderen en selecteer **[!UICONTROL Remove]** .

   U kunt bevestigen dat het videoprofiel niet meer wordt toegepast op een map omdat de naam niet langer onder de mapnaam wordt weergegeven.

### Een videoprofiel uit mappen verwijderen met eigenschappen {#removing-video-profiles-from-folders-by-way-of-properties}

1. Selecteer het Experience Manager-logo en navigeer naar **[!UICONTROL Assets]** en vervolgens naar de map waaruit u een videoprofiel wilt verwijderen.
1. Selecteer in de map het vinkje om het te selecteren en selecteer vervolgens **[!UICONTROL Properties]** .
1. Selecteer de tab **[!UICONTROL Video Profiles]** , selecteer **[!UICONTROL None]** in de vervolgkeuzelijst en selecteer **[!UICONTROL Save & Close]** . Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.
