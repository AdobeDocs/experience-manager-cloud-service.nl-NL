---
title: Bestandsindelingen en MIME-typen die door Experience Manager Assets als Cloud Service worden ondersteund
description: Bestandsindelingen en MIME-typen die door Experience Manager Assets als Cloud Service worden ondersteund.
contentOwner: AG
translation-type: tm+mt
source-git-commit: b44e6a522b6f2363daa40c6c6f9640ba2fadd35e
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 5%

---


# Assets supported file formats {#supported-file-formats}

Adobe Experience Manager als Cloud Service ondersteunt basismogelijkheden voor inhoudsbeheer — opslag, beheer van metagegevens online, versioning, uploaden en downloaden, enzovoort — voor elk binair bestand, onafhankelijk van de indeling. Adobe Experience Manager Assets ondersteunt een groot aantal bestandsindelingen en elke productfunctie biedt verschillende ondersteuning voor verschillende indelingen.

Daarnaast biedt Experience Manager Assets uitgebreide ondersteuning voor het genereren van voorvertoningen en vertoningen en voor het extraheren van metagegevens en tekst voor full-text indexering. Deze uitgebreide ondersteuning wordt geleverd met behulp van [asset microservices](asset-microservices-configure-and-use.md).

De hoogtepunten voor de omzetting van Activa die de microservices van activa gebruiken omvatten:

* Belangrijke [Adobe-bestandsindelingen](#adobe-formats) die zijn gemaakt door Adobe-toepassingen en -services, zoals Adobe Photoshop, Adobe InDesign, Adobe Illustrator, Adobe XD, Adobe Dimension en Adobe Acrobat of PDF.
* Belangrijke bestandsindelingen voor [beeldbewerking](#image-formats).
* [Camera Raw-bestandsindelingen](#camera-raw-formats) voor een groot aantal camera&#39;s, waaronder Canon, Nikon, Fujifilm, Olympus en andere fabrikanten (aangedreven door Adobe Camera Raw).
* Algemene [documentindelingen](#document-formats), waaronder Microsoft Office- en Open Document-indelingen.
* Breed scala aan [video](#video-formats)- en [audio](#audio-formats)-indelingen.

De volgende legenda beschrijft het steunniveau.

| Ondersteuningsniveau | Beschrijving |
| ------------- | --------------------------- |
| ✓ | Ondersteund |
| * | Zie de opmerkingen onder de tabel |
| - | Niet van toepassing |

## Adobe-indelingen {#adobe-formats}

| Bestandsindeling | Miniaturen genereren | Volledige tekstextractie | Metagegevensextractie | Breedte/Hoogte |
| ----------- | -------------------- | ------------------- | ------------------- | ------------ |
| AI | ✓ | - | ✓ | ✓ |
| KLLAGE | - | - | ✓ | - |
| DN | ✓ |  | ✓ | ✓ |
| IDEAS | - | - | ✓ | - |
| INDD | ✓ | - | ✓ | ✓ * |
| INDT | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | ✓ | - |
| PSB | ✓ | - | ✓ | ✓ |
| PSD | ✓ | - | ✓ | ✓ |
| XD | ✓ | - | ✓ | ✓ |

\* Voor [!DNL Adobe InDesign] bestanden (INDD) wordt de grootte van de uitvoering bepaald door de voorvertoning die is ingesloten in het INDD-bestand. Configureer de voorkeuren in [!DNL InDesign] (**[!UICONTROL Preferences > File Handling > Always Save Preview Images with Documents, Preview Size]**) om een grotere uitvoering in te sluiten.

## Afbeeldingsindelingen {#image-formats}

| Bestandsindeling | Miniaturen genereren | Metagegevensextractie | Breedte/Hoogte | Uitsnijden |
| ----------- | -------------------- | ------------------- | ------------ | -------- |
| BMP | ✓ | - | ✓ | ✓ |
| EPS | - | ✓ | - | - |
| GIF | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ |
| SVG | - | ✓ | - | - |
| TIFF | ✓ | ✓ | ✓ | - |

## Afbeeldingsindelingen in [!DNL Dynamic Media] {#image-support-dynamic-media}

| Format | Uploaden (invoerindeling) | Afbeeldingsvoorinstelling maken (uitvoerindeling) | Dynamische vertoning voorvertonen | Dynamische uitvoering leveren | Dynamische uitvoering downloaden |
| ------- | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ | - | - | - | - |
| PSD ‡ | ✓ | - | - | - | - |
| EPS | ✓ | ✓ | ✓ | ✓ | ✓ |
| PICT | ✓ | - | - | - | - |

‡ De samengevoegde afbeelding wordt uit het PSD-bestand geëxtraheerd. Het is een afbeelding die wordt gegenereerd door [!DNL Adobe Photoshop] en die wordt opgenomen in het PSD-bestand. Afhankelijk van de instellingen kan de samengevoegde afbeelding wel of niet de werkelijke afbeelding zijn.

De volgende subtypen van bestandsindelingen voor rasterafbeeldingen die niet worden ondersteund in [!DNL Dynamic Media]:

* PNG-bestanden met een IDAT-segmentgrootte groter dan 100 MB.
* PSB-bestanden.
* PSD-bestanden met een andere kleurruimte dan CMYK, RGB, Grijswaarden of Bitmap worden niet ondersteund. DuoTone-, Lab- en Geïndexeerde kleurruimten worden niet ondersteund.
* PSD-bestanden met een bitdiepte groter dan 16.
* TIFF-bestanden met zwevende-kommagegevens.
* TIFF-bestanden met LAB-kleurruimte.

## Ondersteunde 3D-indelingen {#support-3d-formats}

De volgende lijst met 3D-indelingen wordt ondersteund.

Zie [Werken met 3D-elementen in Dynamic Media.](/help/assets/dynamic-media/assets-3d.md)

| Format | Opslag | Versioning | Workflow | Publiceren | Toegangsbeheer | Voorvertoning miniatuur | 3D-voorvertoning | Levering Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | ✓ | ✓ | ✓ |  | ✓ | ✓ |  |  |
| gLB | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| gLTF | ✓ | ✓ | ✓ |  | ✓ |  | ✓ |  |
| OBJ | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| STL | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| USDz | ✓ | ✓ | ✓ | ✓ | ✓ |  |  | ✓ |

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

| Bestandsindeling | Miniaturen genereren | Volledige tekstextractie | Breedte/Hoogte | Metagegevensbeheer | [Gekoppelde assets](use-assets-across-connected-assets-instances.md) |
| ----------- | -------------------- | ------------------- | ------------ | ------------------- | ---------------- |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ |
| DOC | - | - | - | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPT | - | - | - | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ |
| XLS | - | - | - | ✓ | ✓ |
| ODF | ✓ | ✓ | ✓ | - | - |
| UIT | ✓ | ✓ | ✓ | - | - |
| ODM | ✓ | ✓ | ✓ | - | - |
| ODP | ✓ | ✓ | ✓ | - | - |
| ODS | ✓ | ✓ | ✓ | - | - |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ |
| EPUB | - | ✓ | - | - | - |
| HTML | - | ✓ | - | ✓ | ✓ |
| PS | - | - | ✓ | - | - |
| RTF | - | ✓ | - | ✓ | ✓ |
| TXT | - | ✓ | - | ✓ | ✓ |
| XML | - | ✓ | - | - | - |

## Documentindelingen in [!DNL Dynamic Media] {#document-support-dynamic-media}

| Format | Uploaden (invoerindeling) | Afbeeldingsvoorinstelling maken (uitvoerindeling) | Dynamische vertoning voorvertonen | Dynamische uitvoering leveren | Dynamische uitvoering downloaden |
| ------ | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| AI | ✓ | - | - | - | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ |
| INDD | ✓ | - | - | - | - |

## Video-indelingen {#video-formats}

| Bestandsindeling | Miniaturen genereren | Metagegevensextractie | Breedte/Hoogte |
| ----------- | -------------------- | ------------------- | ------------ |
| 3G2 | - | ✓ | - |
| 3GP | - | ✓ | - |
| AVI | ✓ | ✓ | ✓ |
| DIVX | ✓ |  | ✓ |
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
| OGV | ✓ | - | ✓ |
| QT | ✓ | - | ✓ |
| R3D | ✓ | - | ✓ |
| SWF | ✓ | - | ✓ |
| WEBM | ✓ | - | ✓ |
| WMV | ✓ | ✓ | ✓ |

## Video-indelingen in [!DNL Dynamic Media] voor transcodering {#video-dynamic-media-transcoding}

| Videobestandsextensie | Container | Aanbevolen videocodecs | Niet-ondersteunde video-codecs |
|------------------------|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|
| MP4 | MPEG-4 | H264/AVC (alle profielen) |  |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (vectoranimatiebestanden) |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen (MSS2), Microsoft Photo Story (WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 |  |
| M4V | Apple iTunes | H264/AVC |  |
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| WebM | WebM | Google VP8 |  |
| OGV, OGG | Ogg | Theora, VP3, Dirac |  |
| MXF | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | Matroska | H264/AVC |  |
| R3D, RM | Raw-video, rood | MJPEG 2000 |  |
| RAM, RM | RealVideo | Niet ondersteund | Real G2 (RV20), Real 8 (RV30), Real 10 (RV40) |
| FLAC | Native Flac | Vrije, verliesvrije audiocodec |  |
| MJ2 | Beweging JPEG 2000 | Motion JPEG 2000-codec |  |

## Audio-indelingen {#audio-formats}

Middelen als Cloud Service bieden ondersteuning voor het ophalen van XMP-metagegevens voor de audio-indelingen AIF, ASF, M4A, MP3, WAV en WMA.

>[!MORELIKETHIS]
>
>* [Verwerking van bedrijfsmiddelen met behulp van asset-microservices](asset-microservices-overview.md)

