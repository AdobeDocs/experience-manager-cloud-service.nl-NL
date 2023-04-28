---
title: Ondersteunde bestandsindelingen en MIME-typen
description: Bestandsindelingen en MIME-typen die worden ondersteund door [!DNL Experience Manager Assets] als [!DNL Cloud Service].
contentOwner: AG
feature: Asset Management,Renditions
role: User,Admin
exl-id: e848aa77-7829-4adc-8b88-0279791a4525
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '1014'
ht-degree: 4%

---

# [!DNL Assets] ondersteunde bestandsindelingen {#supported-file-formats}

[!DNL Adobe Experience Manager] als [!DNL Cloud Service] ondersteunt de basismogelijkheden voor inhoudsbeheer — opslag, beheer van metagegevens online, versioning, uploaden en downloaden, enzovoort — voor elk binair bestand, onafhankelijk van de indeling. [!DNL Adobe Experience Manager Assets] ondersteunt een groot aantal bestandsindelingen en elke productfunctie biedt verschillende ondersteuning voor verschillende indelingen.

Daarnaast [!DNL Experience Manager Assets] biedt uitgebreide ondersteuning voor het genereren van voorvertoningen en vertoningen en voor het extraheren van metagegevens en tekst voor full-text indexering. Deze uitgebreide ondersteuning wordt geleverd met [assetmicroservices](asset-microservices-configure-and-use.md).

De hoogtepunten voor activaomzetting die de diensten van activa microservices gebruiken omvatten:

* Sleutel [Adobe-bestandsindelingen](#adobe-formats) geproduceerd door Adobe-toepassingen en -diensten, waaronder [!DNL Adobe Photoshop], [!DNL Adobe InDesign], [!DNL Adobe Illustrator], [!DNL Adobe XD], [!DNL Adobe Dimension], en [!DNL Adobe Acrobat] of PDF.
* Sleutel [afbeeldingsbestandsindelingen](#image-formats).
* [Camera Raw bestandsindelingen](#camera-raw-formats) voor een groot aantal camera&#39;s, waaronder Canon, Nikon, Fujifilm, Olympus en andere fabrikanten (aangedreven door Adobe Camera Raw).
* Vaak [documentindelingen](#document-formats), waaronder Microsoft Office- en Open Document-indelingen.
* Breed scala aan [video](#video-formats)- en [audio](#audio-formats)-indelingen.

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
| IDEAS | - | - | ✓ | - |
| INDD | ✓ | - | ✓ | ✓ * |
| INDT | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | ✓ | - |
| PSB | ✓ | - | ✓ | ✓ |
| PSD | ✓ | - | ✓ | ✓ |
| XD | ✓ | - | ✓ | ✓ |

\* Voor [!DNL Adobe InDesign] bestanden (INDD), wordt de grootte van de vertoning bepaald door de voorvertoning die is ingesloten in het INDD-bestand. Voorkeuren configureren in [!DNL InDesign] (**[!UICONTROL Preferences > File Handling > Always Save Preview Images with Documents, Preview Size]**) om een grotere uitvoering in te sluiten.

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
| SGI | ✓ | ✓ | ✓ | ✓ |
| SVG | ✓ | - | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | - |
| WebP | ✓ | ✓ | ✓ | ✓ |

## 3D-indelingen {#support-3d-formats}

De volgende 3D-indelingen worden ondersteund.

Zie ook [Werken met 3D-middelen in Dynamic Media](/help/assets/dynamic-media/assets-3d.md).

| Indeling | Opslag | Versioning | Workflow | Publiceren | Toegangsbeheer | Voorvertoning miniatuur | 3D-voorvertoning | Dynamic Media-levering |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | - |
| gLB | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| gLTF | ✓ | ✓ | ✓ | - | ✓ | - | ✓ | - |
| OBJ | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| STL | ✓ | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| USDz | ✓ | ✓ | ✓ | ✓ | ✓ | - | - | ✓ |

## [!DNL Camera RAW] formaten {#camera-raw-formats}

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
| ePub | - | ✓ | - | - | - | - |
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

| Bestandsindeling | Miniaturen genereren | Metagegevensextractie | Breedte/Hoogte |
| ----------- | -------------------- | ------------------- | ------------ |
| 3G2 | - | ✓ | - |
| 3GP | - | ✓ | - |
| AVI | ✓ | ✓ | ✓ |
| DIVX | ✓ | - | ✓ |
| F4V | ✓ | ✓ | ✓ |
| FLV | ✓ | ✓ | ✓ |
| M2T | ✓ | - | ✓ |
| M2TS | ✓ | - | ✓ |
| M2V | ✓ | - | ✓ |
| M4V | ✓ | ✓ | ✓ |
| MKV | ✓ | - | ✓ |
| MOV | ✓ | ✓ | ✓ |
| MP4 | ✓ | ✓ | ✓ |
| MPEG | ✓ | ✓ | ✓ |
| MPG | ✓ | ✓ | ✓ |
| MTS | ✓ | - | ✓ |
| MXF | ✓ | - | ✓ |
| OGV | ✓ | - | ✓ |
| QT | ✓ | - | ✓ |
| R3D | - | ✓ | ✓ |
| SWF | ✓ | - | ✓ |
| WebM | ✓ | - | ✓ |
| WMV | ✓ | ✓ | ✓ |

## Audio-indelingen {#audio-formats}

[!DNL Assets] als [!DNL Cloud Service] biedt ondersteuning voor XMP metagegevensextractie voor AIF-, ASF-, M4A-, MP3-, WAV- en WMA-audio-indelingen.

## Ondersteunde indelingen voor audio- en video-transcriptie {#audio-video-transcription-formats}

* FLV (met H.264- en AAC-codecs) (.flv)
* MXF (.mxf)
* MPEG2-PS, MPEG2-TS, 3GP (.ts, .ps, .3gp, .3gpp, .mpg)
* Windows Media Video (WMV)/ASF (.wmv, .asf)
* AVI (niet-gecomprimeerd 8 bits/10 bits) (.avi)
* MP4 (.mp4, .m4a, .m4v)
* Microsoft Digital Video Recording (DVR-MS) (.dvr-ms)
* Matroska/WebM (.mkv)
* WAVE/WAV (.wav)
* QuickTime (.mov)

## Tips en beperkingen {#limitations-and-tips}

* De maximale bestandsgrootte voor het uitnemen van metagegevens is momenteel ongeveer 15 GB. Wanneer u zeer grote elementen uploadt, mislukt het uitnemen van metagegevens soms.

## Dynamic Media - Ondersteunde invoervideo-indelingen voor transcodering {#video-dynamic-media-transcoding}

| Videobestandsextensie | Container | Aanbevolen videocodecs | Niet-ondersteunde video-codecs |
| --- | --- | --- | --- |
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (vectoranimatiebestanden) |
| M4V | Apple iTunes | H264/AVC | − |
| MKV | Matroska | H264/AVC | − |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| MP4 | MPEG-4 | H264/AVC (alle profielen) | − |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 | − |
| MXF ‡ | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro | − |
| OGV, OGG | Ogg | Theora, VP3, Dirac | − |
| WebM | WebM | Google VP8 | − |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen (MSS2), Microsoft Photo Story (WVP2) |

‡ Deze video-indeling wordt nog niet ondersteund voor gebruik met interactieve video&#39;s in Dynamic Media of voor gebruik met annotatie in Experience Manager Assets.

## Dynamic Media - Ondersteunde documentindelingen {#document-support-dynamic-media}

| Indeling | Uploaden (invoerindeling) | Afbeeldingsvoorinstelling maken (uitvoerindeling) | Dynamische vertoning voorvertonen | Dynamische uitvoering leveren | Dynamische uitvoering downloaden |
| ------ | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| AI | ✓ | - | - | - | - |
| INDD | ✓ | - | - | - | - |
| PDF (Zie onderstaande opmerking) | ✓ | ✓ | ✓ | ✓ | ✓ |

>[!NOTE]
>
>Voor beveiligde PDF wordt alleen Uploaden ondersteund.

## Dynamic Media - Ondersteunde rasterafbeeldingsindelingen {#image-support-dynamic-media}

| Indeling | Uploaden (invoerindeling) | Afbeeldingsvoorinstelling maken (uitvoerindeling) | Dynamische vertoning voorvertonen | Dynamische uitvoering leveren | Dynamische uitvoering downloaden | Typen instellen die deze indeling ondersteunen |
| ------- | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- | ---------------------------------- |
| BMP | ✓ | - | - | - | - | [Afbeelding](/help/assets/dynamic-media/image-sets.md), [Gemengde media](/help/assets/dynamic-media/mixed-media-sets.md), en [Draaien](/help/assets/dynamic-media/spin-sets.md) |
| EPS | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ | - |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | [Afbeelding](/help/assets/dynamic-media/image-sets.md), [Gemengde media](/help/assets/dynamic-media/mixed-media-sets.md), en [Draaien](/help/assets/dynamic-media/spin-sets.md) |
| PICT | ✓ | - | - | - | - | - |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | [Afbeelding](/help/assets/dynamic-media/image-sets.md), [Gemengde media](/help/assets/dynamic-media/mixed-media-sets.md), en [Draaien](/help/assets/dynamic-media/spin-sets.md) |
| PSD ‡ | ✓ | - | - | - | - | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ | [Afbeelding](/help/assets/dynamic-media/image-sets.md), [Gemengde media](/help/assets/dynamic-media/mixed-media-sets.md), en [Draaien](/help/assets/dynamic-media/spin-sets.md) |

‡ De samengevoegde afbeelding wordt uit het PSD-bestand geëxtraheerd. Het is een afbeelding die wordt gegenereerd door [!DNL Adobe Photoshop] en wordt opgenomen in het PSD-bestand. Afhankelijk van de instellingen kan de samengevoegde afbeelding wel of niet de werkelijke afbeelding zijn.

## Dynamic Media - Niet-ondersteunde rasterafbeeldingsindelingen {#unsupported-raster-image-formats-dm}

De volgende subtypen van rasterafbeeldingsbestandsindelingen die *niet* ondersteund in [!DNL Dynamic Media]:

* PNG-bestanden met een IDAT-segmentgrootte groter dan 100 MB.
* PSB-bestanden.
* PSD-bestanden met een andere kleurruimte dan CMYK, RGB, Grijswaarden of Bitmap worden niet ondersteund. DuoTone-, Lab- en Geïndexeerde kleurruimten worden niet ondersteund.
* PSD-bestanden met een bitdiepte groter dan 16.
* TIFF-bestanden met zwevende-kommagegevens.
* TIFF-bestanden met Lab-kleurruimte.

## Dynamic Media - Ondersteunde 3D-bestandsindelingen {#support-3d-formats-dynamic-media}

Zie ook [Ondersteunde 3D-indelingen](/help/assets/file-format-support.md#support-3d-formats)

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Notities |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair | Hiermee neemt u de materialen en structuren op als één enkel element. |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| USDZ | Universal Scene Description Zip-archief | model/vnd.usdz+zip | *Alleen ondersteuning voor inname; er is geen weergave of interactie beschikbaar.* USDZ is een eigen 3D-indeling die door Safari of iOS kan worden weergegeven. |

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [HTTP-API voor assets](mac-api-assets.md)
* [Assets doorzoeken](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Rapporten over assets](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Facetten doorzoeken](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)

>[!MORELIKETHIS]
>
>* [Verwerking van bedrijfsmiddelen met behulp van asset-microservices](asset-microservices-overview.md)
>* [Ondersteunde bestandsindelingen voor slimme tags van op tekst gebaseerde elementen](/help/assets/smart-tags.md#smart-tags-supported-file-formats)

