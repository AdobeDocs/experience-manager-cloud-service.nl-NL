---
title: Ondersteunde bestandsindelingen en MIME-typen
description: De formaten van het dossier en MIME types die door  [!DNL Experience Manager Assets]  als a  [!DNL Cloud Service] worden gesteund.
contentOwner: AG
feature: Asset Management, Renditions
role: User, Admin
exl-id: e848aa77-7829-4adc-8b88-0279791a4525
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '1458'
ht-degree: 0%

---

# [!DNL Assets] ondersteunde bestandsindelingen {#supported-file-formats}

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

[!DNL Adobe Experience Manager] als [!DNL Cloud Service] biedt ondersteuning voor elementaire mogelijkheden voor inhoudsbeheer, zoals online opslag, beheer van metagegevens, versioning, uploaden en downloaden, enzovoort, voor elk binair bestand, onafhankelijk van de indeling. [!DNL Adobe Experience Manager Assets] ondersteunt een groot aantal bestandsindelingen en elke productfunctie biedt verschillende ondersteuning voor verschillende indelingen.

Daarnaast biedt [!DNL Experience Manager Assets] uitgebreide ondersteuning voor het genereren van voorvertoningen en vertoningen en voor het extraheren van metagegevens en tekst voor full-text indexering. Deze uitgebreide steun wordt verleend gebruikend [ activa microservices ](asset-microservices-configure-and-use.md).

De hoogtepunten voor activaomzetting die de diensten van activa microservices gebruiken omvatten:

* Zeer belangrijke [ Adobe dossierformaten ](#adobe-formats) die door de toepassingen en de diensten van Adobe, met inbegrip van [!DNL Adobe Photoshop], [!DNL Adobe InDesign], [!DNL Adobe Illustrator], [!DNL Adobe XD], [!DNL Adobe Dimension], en [!DNL Adobe Acrobat] of PDF worden geproduceerd.
* Belangrijke [ beeldende dossierformaten ](#image-formats).
* [ Camera Raw dossierformaten ](#camera-raw-formats) voor een brede waaier van camera&#39;s, met inbegrip van Canon, Nikon, Fujifilm, Olympus, en andere fabrikanten (aangedreven door Adobe Camera Raw).
* Gemeenschappelijke [ documentformaten ](#document-formats), met inbegrip van Microsoft® Office en Open formaten van het Document.
* Brede waaier van [ video ](#video-formats) en [ audio ](#audio-formats) formaten.

De volgende legenda beschrijft het niveau van steun voor elk formaat.

| Ondersteuningsniveau | Beschrijving |
| ------------- | --------------------------- |
| ✓ | Ondersteund |
| * | Zie de opmerkingen onder de tabel |
| - | Niet van toepassing |

## Adobe-indelingen {#adobe-formats}

| Bestandsindeling | Miniaturen genereren | Volledige tekst extraheren | Metagegevensextractie | Breedte/Hoogte |
| ----------- | -------------------- | ------------------- | ------------------- | ------------ |
| AI | ✓ | - | ✓ | ✓ |
| KLLAGE | - | - | ✓ | - |
| DN | ✓ | - | ✓ | ✓ |
| SBSAR | ✓ | - | ✓ | ✓ |
| IDEAS | - | - | ✓ | - |
| INDD | ✓ | - | ✓ | ✓ * |
| INDT | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | ✓ | - |
| PSB | ✓ | - | ✓ | ✓ |
| PSD | ✓ | - | ✓ | ✓ |
| XD | ✓ | - | ✓ | ✓ |

\* Voor [!DNL Adobe InDesign] bestanden (INDD) wordt de grootte van uitvoeringen bepaald door de voorvertoning die is ingesloten in het INDD-bestand. Configureer de voorkeuren in [!DNL InDesign] (**[!UICONTROL Preferences > File Handling > Always Save Preview Images with Documents, Preview Size]** ), zodat u grotere uitvoeringen kunt insluiten.

## Afbeeldingsindelingen {#image-formats}

| Bestandsindeling | Miniaturen genereren | Metagegevensextractie | Breedte/Hoogte | Uitsnijden |
| ----------- | -------------------- | ------------------- | ------------ | -------- |
| BMP | ✓ | - | ✓ | ✓ |
| EPS | ✓ | ✓ | - | - |
| GIF | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ |
| RGB | ✓ | ✓ | ✓ | ✓ |
| RGBA | ✓ | ✓ | ✓ | ✓ |
| SGI™ | ✓ | ✓ | ✓ | ✓ |
| SVG | ✓ | - | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | - |
| WebP | ✓ | ✓ | ✓ | ✓ |

## 3D-indelingen {#support-3d-formats}

De volgende 3D-indelingen worden ondersteund.

Zie ook [ Werk met 3D activa in Dynamische Media ](/help/assets/dynamic-media/assets-3d.md).

| Indeling | Opslag | Versioning | Workflow | Publiceren | Toegangsbeheer | Voorvertoning miniatuur | 3D-voorvertoning | Dynamische media-levering |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | - |
| gLB | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| gLTF | ✓ | ✓ | ✓ | - | ✓ | - | ✓ | - |
| OBJ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| STL | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| FBX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| 3DS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| USDz | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ |
| SBSAR | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | - |

## [!DNL Camera Raw] indelingen {#camera-raw-formats}

| Bestandsindeling | Miniaturen genereren | Metagegevensextractie | Breedte/Hoogte |
| ----------- | -------------------- | ------------------- | ------------ |
| 3FR | ✓ | ✓ | ✓ |
| ARW | ✓ | ✓ | ✓ |
| CR2 | ✓ | ✓ | ✓ |
| CR3 | ✓ | ✓ | ✓ |
| CRW | ✓ | ✓ | ✓ |
| DCR | ✓ | ✓ | ✓ |
| DNG | ✓ | ✓ | ✓ |
| ERF | ✓ | ✓ | ✓ |
| FFF | ✓ | ✓ | ✓ |
| GPR | ✓ | ✓ | ✓ |
| IIQ | ✓ | ✓ | ✓ |
| KDC | ✓ | ✓ | ✓ |
| MEF | ✓ | ✓ | ✓ |
| MFW | ✓ | ✓ | ✓ |
| MOS | ✓ | ✓ | ✓ |
| MRW | ✓ | ✓ | ✓ |
| NEF | ✓ | ✓ | ✓ |
| NRW | ✓ | ✓ | ✓ |
| ORF | ✓ | ✓ | ✓ |
| PEF | ✓ | ✓ | ✓ |
| RAF | ✓ | ✓ | ✓ |
| RAW | ✓ | ✓ | ✓ |
| RW2 | ✓ | ✓ | ✓ |
| RWL | ✓ | ✓ | ✓ |
| SRF | ✓ | ✓ | ✓ |
| SRW | ✓ | ✓ | ✓ |
| X3F | ✓ | ✓ | ✓ |

## Documentindelingen {#document-formats}

De volgende documentindelingen worden ondersteund voor functies voor middelenbeheer:

| Bestandsindeling | Miniaturen genereren | Volledige tekst extraheren | Breedte/Hoogte | Metagegevensbeheer | [Gekoppelde assets](use-assets-across-connected-assets-instances.md) | Voorvertoning van volledig document |
| ----------- | -------------------- | ------------------- | ------------ | ------------------- | ---------------- |--------|
| DOC | - | - | - | ✓ | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EPUB | - | ✓ | - | - | - | - |
| HTML | - | ✓ | - | ✓ | ✓ | - |
| ODF | ✓ | ✓ | ✓ | - | - | - |
| ODM | ✓ | ✓ | ✓ | - | - | - |
| ODP | ✓ | ✓ | ✓ | - | - | - |
| ODS | ✓ | ✓ | ✓ | - | - | - |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| UIT | ✓ | ✓ | ✓ | - | - | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPT | - | - | - | ✓ | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PS | - | - | ✓ | - | - | - |
| RTF | - | ✓ | - | ✓ | ✓ | ✓ |
| TXT | ✓ | ✓ | - | ✓ | ✓ | ✓ |
| XLS | - | - | - | ✓ | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | - | ✓ | - | - | - | - |

## Video-indelingen {#video-formats}

| Bestandsindeling | Miniaturen genereren | Metagegevensextractie | Breedte/Hoogte | Voorvertoning | Uitvoer |
| ----------- | -------------------- | ------------------- | ------------ | ------- | ------- |
| 3G2 | - | ✓ | - | - | - |
| 3GP | - | ✓ | - | - | - |
| AVI | ✓ | ✓ | ✓ | ✓ | - |
| DIVX | ✓ | - | ✓ | ✓ | - |
| F4V | ✓ | ✓ | ✓ | ✓ | - |
| FLV | ✓ | ✓ | ✓ | ✓ | - |
| M2T | ✓ | - | ✓ | ✓ | - |
| M2TS | ✓ | - | ✓ | ✓ | - |
| M2V | ✓ | - | ✓ | ✓ | - |
| M4V | ✓ | ✓ | ✓ | ✓ | - |
| MKV | ✓ | - | ✓ | ✓ | - |
| MOV | ✓ | ✓ | ✓ | ✓ | - |
| MP4 | ✓ | ✓ | ✓ | ✓ | ✓ |
| MPEG | ✓ | ✓ | ✓ | ✓ | - |
| MPG | ✓ | ✓ | ✓ | ✓ | - |
| MTS | ✓ | - | ✓ | ✓ | - |
| MXF | ✓ | - | ✓ | ✓ | - |
| OGV | ✓ | - | ✓ | ✓ | - |
| QT | ✓ | - | ✓ | ✓ | - |
| R3D | - | ✓ | ✓ | ✓ | - |
| SWF | ✓ | - | ✓ | ✓ | - |
| WebM | ✓ | - | ✓ | ✓ | ✓ |
| WMV | ✓ | ✓ | ✓ | ✓ | - |

## Audio-indelingen {#audio-formats}

[!DNL Assets] als [!DNL Cloud Service] biedt ondersteuning voor het ophalen van XMP-metagegevens voor AIF-, ASF-, M4A-, MP3-, WAV- en WMA-audio-indelingen.

## Ondersteunde indelingen voor audio- en video-transcriptie {#audio-video-transcription-formats}

* FLV (met H.264- en AAC-codecs) (.flv)
* MXF (.mxf)
* MPEG2-PS, MPEG2-TS, 3GP (.ts, .ps, .3gp, .3gpp, .mpg)
* Windows Media Video (WMV)/ASF (.wmv, .asf)
* AVI (niet-gecomprimeerd 8 bits/10 bits) (.avi)
* MP4 (.mp4, .m4a, .m4v)
* Microsoft® Digital Video Recording (DVR-MS) (.dvr-ms)
* Matroska/WebM (.mkv)
* WAVE/WAV (.wav)
* QuickTime (.mov)

## Tips en beperkingen {#limitations-and-tips}

* De maximale bestandsgrootte voor het uitnemen van metagegevens is momenteel ongeveer 15 GB. Wanneer u grote elementen uploadt, mislukt het uitnemen van metagegevens soms.

## Dynamische media - Ondersteunde invoervideo-indelingen voor transcodering {#video-dynamic-media-transcoding}

| Videobestandsextensie | Container | Aanbevolen videocodecs | Niet-ondersteunde video-codecs |
| --- | --- | --- | --- |
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft® Video 1 (MS-CRAM) |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (vectoranimatiebestanden) |
| M4V | Apple iTunes | H264/AVC | - |
| MKV | Matroska | H264/AVC | - |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| MP4 | MPEG-4 | H264/AVC (alle profielen) | - |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 | - |
| MXF ‡ | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro | - |
| OGV, OGG | OGG | Theora, VP3, Dirac | - |
| WebM | WebM | Google VP8 | - |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft® Screen (MSS2), Microsoft® Photo Story (WVP2) |

‡ Deze video-indeling wordt nog niet ondersteund voor gebruik met interactieve video&#39;s in dynamische media of voor gebruik met annotatie in Experience Manager Assets.

## Dynamische media - Ondersteunde documentindelingen {#document-support-dynamic-media}

| Indeling | Uploaden (invoerindeling) | Afbeeldingsvoorinstelling maken (uitvoerindeling) | Dynamische vertoning voorvertonen | Dynamische uitvoering leveren | Dynamische uitvoering downloaden |
| ------ | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| AI | ✓ | - | - | - | - |
| INDD | ✓ | - | - | - | - |
| PDF (zie onderstaande opmerking) | ✓ | ✓ | ✓ | ✓ | ✓ |

>[!NOTE]
>
>Voor beveiligde PDF&#39;s wordt alleen Uploaden ondersteund.

## Dynamische media - Ondersteunde rasterafbeeldingsindelingen {#image-support-dynamic-media}

| Indeling | Uploaden (invoerindeling) | Afbeeldingsvoorinstelling maken (uitvoerindeling) | Dynamische vertoning voorvertonen | Dynamische uitvoering leveren | Dynamische uitvoering downloaden | Typen instellen die deze indeling ondersteunen |
|---|:---:|:---:|:---:|:---:|:---:| --- |
| AVIF | - | - | - | ✓ | - | - |
| BMP | ✓ | - | - | - | - | [ Beeld ](/help/assets/dynamic-media/image-sets.md), [ Gemengde Media ](/help/assets/dynamic-media/mixed-media-sets.md), en [ Spin ](/help/assets/dynamic-media/spin-sets.md) |
| [ EPS ](/help/assets/dynamic-media/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| HEIC | - | - | - | ✓ | - | - |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | [ Beeld ](/help/assets/dynamic-media/image-sets.md), [ Gemengde Media ](/help/assets/dynamic-media/mixed-media-sets.md), en [ Spin ](/help/assets/dynamic-media/spin-sets.md) |
| PICT | ✓ | - | - | - | - | - |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | [ Beeld ](/help/assets/dynamic-media/image-sets.md), [ Gemengde Media ](/help/assets/dynamic-media/mixed-media-sets.md), en [ Spin ](/help/assets/dynamic-media/spin-sets.md) |
| PSD ‡ | ✓ | - | - | - | - | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ | [ Beeld ](/help/assets/dynamic-media/image-sets.md), [ Gemengde Media ](/help/assets/dynamic-media/mixed-media-sets.md), en [ Spin ](/help/assets/dynamic-media/spin-sets.md) |
| WEBP | - | - | - | ✓ | - | - |

<!-- AVIF, HEIC, and WebP added to table above on March 4, 2024 based on CQDOC-21294 -->

‡ De samengevoegde afbeelding wordt uit het PSD-bestand geëxtraheerd. Het is een afbeelding die wordt gegenereerd door [!DNL Adobe Photoshop] en die wordt opgenomen in het PSD-bestand. Afhankelijk van de instellingen kan de samengevoegde afbeelding wel of niet de werkelijke afbeelding zijn.

## Dynamische media - Niet-ondersteunde rasterafbeeldingsindelingen {#unsupported-raster-image-formats-dm}

De volgende subtypes van het dossierformaten van het roosterbeeld die *niet* in [!DNL Dynamic Media] worden gesteund:

* PNG-bestanden met een IDAT-segmentgrootte groter dan 100 MB.
* PSB-bestanden
* PSD-bestanden met een andere kleurruimte dan CMYK, RGB, Grijswaarden of Bitmap worden niet ondersteund. DuoTone-, Lab- en Geïndexeerde kleurruimten worden niet ondersteund.
* PSD-bestanden met een bitdiepte groter dan 16.
* TIFF-bestanden met zwevende-kommagegevens.
* TIFF-bestanden met Lab-kleurruimte.

## Dynamische media - Ondersteunde 3D-bestandsindelingen {#support-3d-formats-dynamic-media}

Zie ook [ 3D gesteunde formaten ](/help/assets/file-format-support.md#support-3d-formats)

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Notities |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair | Hiermee neemt u de materialen en structuren op als één enkel element. |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif | |
| STL | Stereolithografie | application/vnd.ms-pki.stl | |
| USDZ | Universal Scene Description Zip-archief | model/vnd.usdz+zip | *Steun voor opname en duimnagelgeneratie; 3D voorproeven nog niet gesteund.* USDZ is een 3D-indeling die door Safari of iOS kan worden weergegeven. |

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [ verwerking van Activa gebruikend activa microservices ](asset-microservices-overview.md).
>* [ Gesteunde dossierformaten voor slimme het etiketteren van op tekst-gebaseerde activa ](/help/assets/smart-tags.md#smart-tags-supported-file-formats)
