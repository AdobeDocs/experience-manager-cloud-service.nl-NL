---
title: Ondersteunde bestandsindelingen
description: Ondersteunde bestandsindelingen voor de verschillende gebruiksgevallen van [!DNL Assets view]
role: User, Leader, Admin, Architect, Developer
contentOwner: AG
exl-id: 5936ace2-318e-4888-9ad4-23e6f6bfb857
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# Bestandsindelingen worden ondersteund in [!DNL Assets view] {#file-format-support}

[!DNL Assets view] ondersteunt een groot aantal bestandsindelingen en elke functie biedt verschillende ondersteuning voor verschillende bestandstypen.

* ![pictogram type afbeeldingsbestand](assets/image-icon.svg) Afbeeldingen: JPG, PNG, GIF, TIFF en andere
* ![creative cloudtype, pictogram](assets/creative-cloud-files.svg) Creative Cloud-bestanden: PSD, AI en INDD
* ![cameratype, pictogram](assets/camera-icon.svg) Camera Raw bestanden: CR2/CR3, NEF, SRW/SRF en andere
* ![pictogram documenttype](assets/document-icon.svg) Documenten: DOCX, PDF, PPTX en XLSX
* ![pictogram videobestandstype](assets/video-icon.svg) Video&#39;s: MP4

[!DNL Assets view] ondersteunt elke binaire bestandsindeling met basisservices, zoals opslaan, uploaden, kopiëren, verplaatsen, verwijderen en toevoegen van metagegevens.

[!DNL Assets view] ondersteunt ook Camera RAW-bestanden van een groot aantal toonaangevende camerafabrikanten, waaronder Canon (CR2/CR3), Nikon (NEF), Sony (SRW/SRF), Fujifilm (RAF), Olympus (ORF) en andere, aangedreven door Adobe Camera Raw.

De verschillende bestandstypen bieden verschillende mate van ondersteuning voor de gebruiksgevallen en -functies, zoals hieronder wordt beschreven. Gebruik de legenda om het steunniveau te begrijpen.

| Ondersteuningsniveau | Beschrijving |
|-------------------|-------------------------|
| ✓ | Ondersteund |
| ✓ ‡ | Voorwaardelijk ondersteund |
| - | Niet van toepassing |

## Elementen toevoegen, uploaden en weergeven {#support-to-upload-view}

<!-- TBD: For AEM, AI files require the PDF option to be selected when saving the AI file.
-->

| Type element | [Bladeren](/help/assets/navigate-assets-view.md) | Kopiëren | [Uploaden](/help/assets/add-delete-assets-view.md) | Maken | [Verwijderen](/help/assets/add-delete-assets-view.md#delete-assets) | Details | Zoomen op afbeelding | [Onlangs bekeken](/help/assets/navigate-assets-view.md) |
|-------------------|----------|----------|----------|----------|----------|-------------------|------------|-----------------|
| Rasterafbeeldingen | ✓ | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ |
| RAW-bestanden | ✓ | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ |
| Mappen | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| MP4-video&#39;s | ✓ | ✓ | ✓ | - | ✓ | ✓ ‡ | - | ✓ |
| PDF | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | ✓ |
| PSD, AI en INDD | ✓ | ✓ | ✓ | - | ✓ | ✓ ‡ | - | ✓ |
| Overige binaire bestanden | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | ✓ |

<!-- Hiding CC Libraries (considered beta) as per PM feedback.
| CC Libraries  | &#10003; | &minus;  | &#10003; | &#10003; | &#10003; | &#10003; | &minus;    | &minus;         |
-->

## Elementen zoeken, gebruiken en bewerken {#support-to-search-use-edit}

| Type element | [Downloaden](/help/assets/manage-organize-assets-view.md#download) | Slepen en slepen | [Afbeeldingseditor](/help/assets/edit-images-assets-view.md) | [Zoeken](/help/assets/search-assets-view.md) | [Slimme tags](/help/assets/metadata-assets-view.md#tags) | [Naam wijzigen](/help/assets/manage-organize-assets-view.md) | [Versies](/help/assets/manage-organize-assets-view.md#versions-of-assets) |
|---------------|----------|---------------|--------------|----------|------------|----------|----------|
| Rasterafbeeldingen | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAW-bestanden | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ | ✓ |
| Mappen | ✓ | ✓ | - | ✓ | - | ✓ | ✓ |
| Video&#39;s | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ |
| CC-bibliotheken | - | - | - | - | - | ✓ | ✓ |
| PDF | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ |
| PSD | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ |
| AI en INDD | ✓ | ✓ | - | ✓ | - | ✓ | ✓ |
| Overige binaire bestanden | ✓ | ✓ | - | ✓ | - | ✓ | ✓ |


## Elementen controleren en samenwerken {#support-to-review-collaborate}

| Type element | Annoteren | Opmerking | Taken maken en revisie uitvoeren |
|---------------|----------|----------|-------------------------|
| Rasterafbeeldingen | ✓ | ✓ | ✓ |
| RAW-bestanden | ✓ | ✓ | ✓ |
| Mappen | - | - | - |
| Video&#39;s | - | ✓ | ✓ |
| CC-bibliotheken | - | - | - |
| PDF | - | ✓ | ✓ |
| PSD, AI en INDD | - | ✓ | ✓ |
| Overige binaire bestanden | - | ✓ | ✓ |
| DOC | - | ✓ | ✓ |
| DOCX | - | ✓ | ✓ |
| PPT | - | ✓ | ✓ |
| PPTX | - | ✓ | ✓ |
| XLS | - | ✓ | ✓ |
| XLSX | - | ✓ | ✓ |
| TXT | - | ✓ | ✓ |
| RTF | - | ✓ | ✓ |

## Overige taken voor vermogensbeheer {#support-to-manage-assets}

| Type element | [Metagegevens](/help/assets/metadata-assets-view.md) | [Uitvoeringen](/help/assets/add-delete-assets-view.md#renditions) | [Prullenbak](/help/assets/add-delete-assets-view.md#delete-assets) | Kopiëren | Verplaatsen |
|---------------|-------------------|------------|----------|----------|----------|
| Rasterafbeeldingen | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAW-bestanden | ✓ | ✓ | ✓ | ✓ | ✓ |
| Mappen | ✓ | - | ✓ | ✓ | ✓ |
| Video&#39;s | ✓ | - | ✓ | ✓ | ✓ |
| CC-bibliotheken | ✓ | - | - | - | - |
| PDF | ✓ | - | ✓ | ✓ | ✓ |
| PSD, AI en INDD | ✓ | - | ✓ | ✓ | ✓ |
| Overige binaire bestanden | ✓ | - | ✓ | ✓ | ✓ |

Gebruikers van [!DNL Adobe Asset Link] kan bestanden uploaden en inchecken (een nieuwe versie uploaden) in de [!DNL Assets view] opslagplaats van de ondersteunde [!DNL Adobe Creative Cloud] bureaubladtoepassingen.

<!-- TBD: Saving the template table separately for later use.
| Asset type    | Features |
|---------------|----------|
| Raster images |          |
| Folders       |          |
| Videos        |          |
| CC Libraries  |          |
| PDF files     |          |
| PSD           |          |
| AI            |          |
| INDD          |          |

>[!MORELIKETHIS]
>
>* []()
-->

## Volgende stappen {#next-steps}

* Feedback geven op het product met de [!UICONTROL Feedback] optie beschikbaar in de gebruikersinterface van de weergave Elementen

* Documentfeedback geven met [!UICONTROL Edit this page] ![de pagina bewerken](assets/do-not-localize/edit-page.png) of [!UICONTROL Log an issue] ![een GitHub-probleem maken](assets/do-not-localize/github-issue.png) beschikbaar op de rechterzijbalk

* Contact [Klantenservice](https://experienceleague.adobe.com/?support-solution=General#support)
