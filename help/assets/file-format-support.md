---
title: Bestandsindelingen en MIME-typen die door Experience Manager Assets als Cloud Service worden ondersteund
description: Bestandsindelingen en MIME-typen die door Experience Manager Assets worden ondersteund als Cloud Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 776b089a322cc4f86fdcb9ddf1c3cc207fc85d39

---


# Ondersteunde bestandsindelingen {#supported-file-formats}

Adobe Experience Manager als Cloud Service ondersteunt basismogelijkheden voor inhoudsbeheer - opslag, beheer van metagegevens online, versioning, upload en download enzovoort - voor elk binair bestand, onafhankelijk van de indeling. Voor de veelgebruikte bestandsindelingen, zoals afbeeldingen, eigen documenten, documenten en video van Adobe, biedt deze indeling bovendien uitgebreide ondersteuning voor het genereren van voorvertoningen en vertoningen en voor het extraheren van metagegevens en tekst voor full-text indexering. Deze uitgebreide ondersteuning wordt geleverd met behulp van [asset microservices](asset-microservices-configure-and-use.md).

Enkele markeringen van dossierformaten met uitgebreide steun omvatten:

* Belangrijke [Adobe-bestandsindelingen](#adobe-formats) die zijn gemaakt door Adobe-toepassingen en -services, zoals Adobe Photoshop, InDesign, Illustrator, XD, Dimension en Acrobat / PDF.
* Belangrijke indelingen voor [afbeeldingsbestanden](#image-formats)
* [Camera Raw-bestandsindelingen](#camera-raw-formats) voor een groot aantal camera&#39;s, zoals Canon, Nikon, Fujifilm, Olympus en andere fabrikanten (aangedreven door Adobe Camera Raw)
* Algemene [documentindelingen](#document-formats), waaronder [Microsoft Office](#microsoft-office-formats) (Word, Excel, PowerPoint) en [Open Document](#opendocument-formats) -indelingen
* Brede reeks [video](#video-formats) - en [audio](#audio-formats) -indelingen

## Legenda voor uitgebreide ondersteuningsinformatie {#legend-for-detailed-support-information}

In de volgende legenda wordt het ondersteuningsniveau voor een functie beschreven:

| Ondersteuningsniveau | Beschrijving |
| ------------------------------------------------------------ | --------------------------- |
| ✓ | Ondersteund |
| * | Zie de opmerkingen onder de tabel |
| - | Niet van toepassing |

Kolommen van de steunlijsten verstrekken de volgende informatie:

| Kolom | Beschrijving |
| ------------ | --------------------------------------------------------------- |
| Format | Bestandsindeling (bestandsextensie) van het element voor het oorspronkelijke binaire bestand |
| GIF | GIF-indeling voor genereren van vertoning |
| JPEG | JPEG-indeling voor genereren van vertoning |
| PNG | PNG-indeling voor genereren van vertoning |
| XMP | Extractie van metagegevens van het oorspronkelijke binaire bestand |
| TXT | Tekst uit document extraheren voor indexering |
| Breedte/Hoogte | Ondersteuning voor het definiëren van de breedte en hoogte van een uitvoering (pixels) |

<!-- Adding this checkmark icon ✓ does not look good in table. The icon's shade and size has to be toned down for good readability and less clutter.
@gklebus: I suggest using a checkmark character, either U+2713 ✓ CHECK MARK or U+2714 ✔ HEAVY CHECK MARK
-->

## Adobe-indelingen {#adobe-formats}

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

## Afbeeldingsindelingen {#image-formats}

| Bestandsindeling | GIF | JPEG | PNG | XMP | Breedte/Hoogte |
| ----------- | --- | ---- | --- | --- | ------------ |
| BMP | ✓ | ✓ | ✓ | - | ✓ |
| EPS | - | - | - | ✓ | - |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| SVG | - | - | - | ✓ | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |


## Camera RAW-indelingen {#camera-raw-formats}

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

## Documentindelingen {#document-formats}

| Bestandsindeling | TXT | XMP |
| ----------- | --- | --- |
| EPUB | ✓ | - |
| HTML | ✓ | - |
| PS | - | ✓ |
| RTF | ✓ | - |
| TEXT | ✓ | - |
| XML | ✓ | - |

## Microsoft Office-indelingen {#microsoft-office-formats}

| Bestandsindeling | GIF | JPEG | PNG | TEXT | Breedte/Hoogte |
| ----------- | --- | ---- | --- | ---- | ------------ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ |

## OpenDocument-indelingen {#opendocument-formats}

| Bestandsindeling | GIF | JPEG | PNG | TEXT | Hoogte |
| ----------- | --- | ---- | --- | ---- | ------ |
| ODF | ✓ | ✓ | ✓ | ✓ | ✓ |
| UIT | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODM | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODP | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODS | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ |

## Video-indelingen {#video-formats}

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

## Audio-indelingen {#audio-formats}

Middelen als Cloud Service biedt XMP-ondersteuning voor deze audio-indelingen: AIF, ASF, M4A, MP3, WAV en WMA.

<!-- TBD: Some items from https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-formats.html#SupportedinputvideoformatsforDynamicMediatranscoding may be applicable.

Bring more parity with https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-formats.html#SupportedMIMEtypes.
https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-formats.html#Supportedmultimediaformats
-->

>[!MORELIKETHIS]
>
>* [Verwerking van bedrijfsmiddelen met behulp van asset-microservices](asset-microservices-overview.md)

