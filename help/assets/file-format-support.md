---
title: Bestandsindelingen en MIME-typen die door Experience Manager Assets als Cloud Service worden ondersteund
description: Bestandsindelingen en MIME-typen die door Experience Manager Assets worden ondersteund als Cloud Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 55dd497caaa25cf7c0d8da1c1400b74f7d265d29

---


# Ondersteunde bestandsindelingen {#supported-file-formats}

Adobe Experience Manager als Cloud Service ondersteunt basismogelijkheden voor inhoudsbeheer — opslag, beheer van metagegevens online, versioning, upload en download enzovoort — voor elk binair bestand, onafhankelijk van de indeling. Adobe Experience Manager Assets ondersteunt een groot aantal bestandsindelingen en elke productfunctie biedt verschillende ondersteuning voor verschillende indelingen.

Daarnaast biedt Experience Manager Assets uitgebreide ondersteuning voor het genereren van voorvertoningen en vertoningen en voor het extraheren van metagegevens en tekst voor full-text indexering. Deze uitgebreide ondersteuning wordt geleverd met behulp van [asset microservices](asset-microservices-configure-and-use.md).

De volgende legenda beschrijft het steunniveau.

| Ondersteuningsniveau | Beschrijving |
| ------------------------------------------------------------ | --------------------------- |
| ✓ | Ondersteund |
| * | Zie de opmerkingen onder de tabel |
| - | Niet van toepassing |

## Omzetting van bedrijfsmiddelen met behulp van asset microservices {#asset-microservices-supported-formats}

De hooglichten omvatten:

* Belangrijke [Adobe-bestandsindelingen](#adobe-formats) die zijn gemaakt door Adobe-toepassingen en -services, zoals Adobe Photoshop, InDesign, Illustrator, XD, Dimension en Acrobat / PDF.
* Belangrijke bestandsindelingen voor [beeldbewerking](#image-formats).
* [Camera Raw-bestandsindelingen](#camera-raw-formats) voor een groot aantal camera&#39;s, waaronder Canon, Nikon, Fujifilm, Olympus en andere fabrikanten (aangedreven door Adobe Camera Raw).
* Algemene [documentindelingen](#document-formats), waaronder [Microsoft Office](#microsoft-office-formats) (Word, Excel, PowerPoint) en [Document](#opendocument-formats) openen.
* Brede reeks [video](#video-formats) - en [audio](#audio-formats) -indelingen.

Kolommen van de volgende tabellen bevatten de volgende informatie:

| Kolom | Beschrijving |
| ------------ | --------------------------------------------------------------- |
| Format | Bestandsindeling (bestandsextensie) van het element voor het oorspronkelijke binaire bestand |
| GIF | GIF-indeling voor genereren van vertoning |
| JPEG | JPEG-indeling voor genereren van vertoning |
| PNG | PNG-indeling voor genereren van vertoning |
| XMP | Extractie van metagegevens van het oorspronkelijke binaire bestand |
| TXT | Tekst uit document extraheren voor indexering |
| Breedte/Hoogte | Ondersteuning voor het definiëren van de breedte en hoogte van een uitvoering (pixels) |

### Adobe-indelingen {#adobe-formats}

| Bestandsindeling | GIF | JPEG | PNG | TXT | XMP | Breedte/Hoogte |
| ----------- | --- | ---- | --- | --- | --- | ------------ |
| AI | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| KLLAGE | - | - | - | - | ✓ | - |
| DN | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| IDEAS | - | - | - | - | ✓ | - |
| INDD | ✓ | ✓ | ✓ | - | ✓ | ✓* |
| INDT | - | - | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | - | - | ✓ | - |
| PSB | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| PSD | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| XD | ✓ | ✓ | ✓ | - | ✓ | ✓ |

\* Voor INDD (InDesign-bestanden) wordt de grootte van de uitvoering bepaald door de voorvertoning die is ingesloten in het INDD-bestand. Configureer de voorkeuren in InDesign (**[!UICONTROL Voorkeuren > Bestandsafhandeling > Voorvertoningsafbeeldingen altijd opslaan met documenten, Grootte]** voorvertoning) om een grotere uitvoering in te sluiten.

### Afbeeldingsindelingen {#image-formats}

| Bestandsindeling | GIF | JPEG | PNG | XMP | Breedte/Hoogte |
| ----------- | --- | ---- | --- | --- | ------------ |
| BMP | ✓ | ✓ | ✓ | - | ✓ |
| EPS | - | - | - | ✓ | - |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| SVG | - | - | - | ✓ | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |

### Camera RAW-indelingen {#camera-raw-formats}

| Bestandsindeling | GIF | JPEG | PNG | XMP | Breedte/Hoogte |
| ----------- | --- | ---- | --- | --- | ------------ |
| 3FR | ✓ | ✓ | ✓ | ✓ | ✓ |
| ARW | ✓ | ✓ | ✓ | ✓ | ✓ |
| CR2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| CR3 | ✓ | ✓ | ✓ | ✓ | ✓ |
| CRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| DCR | ✓ | ✓ | ✓ | ✓ | ✓ |
| DNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| ERF | ✓ | ✓ | ✓ | ✓ | ✓ |
| FFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| GPR | ✓ | ✓ | ✓ | ✓ | ✓ |
| IIQ | ✓ | ✓ | ✓ | ✓ | ✓ |
| KDC | ✓ | ✓ | ✓ | ✓ | ✓ |
| MEF | ✓ | ✓ | ✓ | ✓ | ✓ |
| MFW | ✓ | ✓ | ✓ | ✓ | ✓ |
| MOS | ✓ | ✓ | ✓ | ✓ | ✓ |
| MRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| NEF | ✓ | ✓ | ✓ | ✓ | ✓ |
| NRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| ORF | ✓ | ✓ | ✓ | ✓ | ✓ |
| PEF | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAF | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAW | ✓ | ✓ | ✓ | ✓ | ✓ |
| RW2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| RWL | ✓ | ✓ | ✓ | ✓ | ✓ |
| SRF | ✓ | ✓ | ✓ | ✓ | ✓ |
| SRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| X3F | ✓ | ✓ | ✓ | ✓ | ✓ |

### Documentindelingen {#document-formats}

| Bestandsindeling | TXT | XMP |
| ----------- | --- | --- |
| EPUB | ✓ | - |
| HTML | ✓ | - |
| PS | - | ✓ |
| RTF | ✓ | - |
| TEXT | ✓ | - |
| XML | ✓ | - |

### Microsoft Office-indelingen {#microsoft-office-formats}

| Bestandsindeling | GIF | JPEG | PNG | TEXT | Breedte/Hoogte |
| ----------- | --- | ---- | --- | ---- | ------------ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ |

### OpenDocument-indelingen {#opendocument-formats}

| Bestandsindeling | GIF | JPEG | PNG | TEXT | Hoogte |
| ----------- | --- | ---- | --- | ---- | ------ |
| ODF | ✓ | ✓ | ✓ | ✓ | ✓ |
| UIT | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODM | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODP | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODS | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ |

### Video-indelingen {#video-formats}

| Bestandsindeling | GIF | JPEG | PNG | XMP | Breedte/Hoogte |
| ----------- | --- | ---- | --- | --- | ------------ |
| 3G2 | - | - | - | ✓ | - |
| 3GP | - | - | - | ✓ | - |
| AVI | ✓ | ✓ | ✓ | ✓ | ✓ |
| DIVX | ✓ | ✓ | ✓ |  | ✓ |
| F4V | ✓ | ✓ | ✓ | ✓ | ✓ |
| FLV | ✓ | ✓ | ✓ | ✓ | ✓ |
| M2T | ✓ | ✓ | ✓ | - | ✓ |
| M2TS | ✓ | ✓ | ✓ | - | ✓ |
| M2V | ✓ | ✓ | ✓ | - | ✓ |
| M4V | ✓ | ✓ | ✓ | ✓ | ✓ |
| MKV | ✓ | ✓ | ✓ | - | ✓ |
| MOV | ✓ | ✓ | ✓ | ✓ | ✓ |
| MP4 | ✓ | ✓ | ✓ | ✓ | ✓ |
| MPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| MPG | ✓ | ✓ | ✓ | ✓ | ✓ |
| MTS | ✓ | ✓ | ✓ | - | ✓ |
| OGV | ✓ | ✓ | ✓ | - | ✓ |
| QT | ✓ | ✓ | ✓ | - | ✓ |
| R3D | ✓ | ✓ | ✓ | - | ✓ |
| SWF | ✓ | ✓ | ✓ | - | ✓ |
| WEBM | ✓ | ✓ | ✓ | - | ✓ |
| WMV | ✓ | ✓ | ✓ | ✓ | ✓ |

### Audio-indelingen {#audio-formats}

Middelen als Cloud Service biedt XMP-ondersteuning voor deze audio-indelingen: AIF, ASF, M4A, MP3, WAV en WMA.

## Ondersteunde documentindelingen {#doc-formats}

De volgende documentindelingen worden ondersteund voor functies voor middelenbeheer.

| Bestandsindeling | [Gekoppelde assets](use-assets-across-connected-assets-instances.md) |
|---|---|
| DOC | ✓ |
| DOCX | ✓ |
| ODT | ✓ |
| PDF | ✓ |
| HTML | ✓ |
| RTF | ✓ |
| TXT | ✓ |
| XLS | ✓ |
| XLSX | ✓ |
| PPT | ✓ |
| PPTX | ✓ |

>[!MORELIKETHIS]
>
>* [Verwerking van bedrijfsmiddelen met behulp van asset-microservices](asset-microservices-overview.md)

