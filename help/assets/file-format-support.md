---
title: Bestandsindelingen en MIME-typen die door Experience Manager Assets als Cloud Service worden ondersteund
description: Bestandsindelingen en MIME-typen die door Experience Manager Assets worden ondersteund als Cloud Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 4729f0bdd3cf7e2c6fc80e52bf2f70d689956296

---


# Assets supported file formats {#supported-file-formats}

Adobe Experience Manager als Cloud Service ondersteunt basismogelijkheden voor inhoudsbeheer — opslag, beheer van metagegevens online, versioning, upload en download, enzovoort — voor elk binair bestand, onafhankelijk van de indeling. Adobe Experience Manager Assets ondersteunt een groot aantal bestandsindelingen en elke productfunctie biedt verschillende ondersteuning voor verschillende indelingen.

Daarnaast biedt Experience Manager Assets uitgebreide ondersteuning voor het genereren van voorvertoningen en vertoningen en voor het extraheren van metagegevens en tekst voor full-text indexering. Deze uitgebreide ondersteuning wordt geleverd met behulp van [asset microservices](asset-microservices-configure-and-use.md).

De volgende legenda beschrijft het steunniveau.

| Ondersteuningsniveau | Beschrijving |
| ------------- | --------------------------- |
| ✓ | Ondersteund |
| * | Zie de opmerkingen onder de tabel |
| - | Niet van toepassing |

## Omzetting van bedrijfsmiddelen met behulp van asset microservices {#asset-microservices-supported-formats}

De hooglichten omvatten:

* Belangrijke [Adobe-bestandsindelingen](#adobe-formats) die zijn gemaakt door Adobe-toepassingen en -services, zoals Adobe Photoshop, Adobe InDesign, Adobe Illustrator, Adobe XD, Adobe Dimension en Adobe Acrobat of PDF.
* Belangrijke bestandsindelingen voor [beeldbewerking](#image-formats).
* [Camera Raw-bestandsindelingen](#camera-raw-formats) voor een groot aantal camera&#39;s, waaronder Canon, Nikon, Fujifilm, Olympus en andere fabrikanten (aangedreven door Adobe Camera Raw).
* Algemene [documentindelingen](#document-formats), waaronder Microsoft Office- en Open Document-indelingen.
* Breed scala aan [video](#video-formats)- en [audio](#audio-formats)-indelingen.

Kolommen van de volgende tabellen bevatten de volgende informatie:

| Kolom | Beschrijving |
| ------------ | --------------------------------------------------------------- |
| Format | Bestandsindeling (bestandsextensie) van het oorspronkelijke binaire bestand van het element. |
| GIF | GIF-indeling voor genereren van vertoning. |
| JPEG | JPEG-indeling voor genereren van vertoning. |
| PNG | PNG-indeling voor genereren van vertoning. |
| Breedte/Hoogte | Ondersteuning voor het definiëren van de breedte en hoogte van een vertoning in pixels. |

### Adobe-indelingen {#adobe-formats}

| Bestandsindeling | GIF | JPEG | PNG | Volledige tekstextractie | TIFF | Metagegevensextractie | Breedte/Hoogte |
| ----------- | -------- | -------- | -------- | ------------------- | -------- | ------------------- | ------------ |
| AI | ✓ | ✓ | ✓ | - | ✓ | ✓ | ✓ |
| KLLAGE | - | - | - | - | - | ✓ | - |
| DN | ✓ | ✓ | ✓ |  | ✓ | ✓ | ✓ |
| IDEAS | - | - | - | - | - | ✓ | - |
| INDD | ✓ | ✓ | ✓ | - | ✓ | ✓ | ✓* |
| INDT | - | - | - | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | - | - | - | ✓ | - |
| PSB | ✓ | ✓ | ✓ | - | ✓ | ✓ | ✓ |
| PSD | ✓ | ✓ | ✓ | - | ✓ | ✓ | ✓ |
| XD | ✓ | ✓ | ✓ | - | ✓ | ✓ | ✓ |

\* Voor INDD (InDesign-bestanden) wordt de grootte van de uitvoering bepaald door de voorvertoning die is ingesloten in het INDD-bestand. Configureer de voorkeuren in InDesign (**[!UICONTROL Voorkeuren > Bestandsafhandeling > Voorvertoningsafbeeldingen altijd opslaan met documenten, Grootte]** voorvertoning) om een grotere uitvoering in te sluiten.

### Afbeeldingsindelingen {#image-formats}

| Bestandsindeling | GIF | JPEG | PNG | TIFF | Metagegevensextractie | Breedte/Hoogte | Uitsnijden |
| ----------- | -------- | -------- | -------- | -------- | ------------------- | ------------ | -------- |
| BMP | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| EPS | - | - | - | - | ✓ | - | - |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| SVG | - | - | - | - | ✓ | - | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - |

### Camera RAW-indelingen {#camera-raw-formats}

| Bestandsindeling | GIF | JPEG | PNG | TIFF | Metagegevensextractie | Breedte/Hoogte |
| ----------- | -------- | -------- | -------- | -------- | ------------------- | ------------ |
| 3FR | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| ARW | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| CR2 | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| CR3 | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| CRW | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| DCR | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| DNG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| ERF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| FFF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| GPR | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| IIQ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| KDC | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| MEF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| MFW | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| MOS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| MRW | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| NEF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| NRW | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| ORF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PEF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAW | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| RW2 | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| RWL | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| SRF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| SRW | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| X3F | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

### Documentindelingen {#document-formats}

De volgende documentindelingen worden ondersteund voor functies voor middelenbeheer:

|  | GIF | JPEG | PNG | Volledige tekstextractie | TIFF | Breedte/Hoogte | Metagegevensbeheer | [Gekoppelde assets](use-assets-across-connected-assets-instances.md) |
| ---- | -------- | -------- | -------- | ------------------- | -------- | ------------ | ------------------- | ------------------------------------------------------------------- |
| PDF | ✓ | ✓ | ✓ | ✓ | - | ✓ | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| DOC | - | - | - | - | - | - | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPT | - | - | - | - | - | - | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XLS | - | - | - | - | - | - | ✓ | ✓ |
| ODF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| UIT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| ODM | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| ODP | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| ODS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EPUB | - | - | - | ✓ | - | - | - | - |
| HTML | - | - | - | ✓ | - | - | ✓ | ✓ |
| PS | - | - | - | - | - | ✓ | - | - |
| RTF | - | - | - | ✓ | - | - | ✓ | ✓ |
| TXT | - | - | - | ✓ | - | - | ✓ | ✓ |
| XML | - | - | - | ✓ | - | - | - | - |

### Video-indelingen {#video-formats}

| Bestandsindeling | GIF | JPEG | PNG | Metagegevensextractie | Breedte/Hoogte |
| ----------- | -------- | -------- | -------- | ------------------- | ------------ |
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

Middelen als Cloud Service bieden ondersteuning voor het ophalen van XMP-metagegevens voor AIF-, ASF-, M4A-, MP3-, WAV- en WMA-audio-indelingen.

>[!MORELIKETHIS]
>
>* [Verwerking van bedrijfsmiddelen met behulp van asset-microservices](asset-microservices-overview.md)

