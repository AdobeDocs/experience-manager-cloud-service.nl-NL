---
title: Ondersteunde bestandsindelingen
description: Ondersteunde bestandsindelingen voor de verschillende gebruiksgevallen van  [!DNL Assets view]
role: User, Leader, Admin, Developer
contentOwner: AG
exl-id: 5936ace2-318e-4888-9ad4-23e6f6bfb857
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: 2e257634313d3097db770211fe635b348ffb36cf
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Ondersteuning voor bestandsindelingen in [!DNL Assets view] {#file-format-support}

[!DNL Assets view] ondersteunt een groot aantal bestandsindelingen en elke functie biedt verschillende ondersteuning voor verschillende bestandstypen.

* ![&#x200B; het type van beelddossier pictogram &#x200B;](assets/image-icon.svg) Beelden: JPG, PNG, GIF, TIFF, en anderen
* ![&#x200B; creatief wolkentypepictogram &#x200B;](assets/creative-cloud-files.svg) de dossiers van Creative Cloud: PSD, PSB, AI, en INDD
* ![&#x200B; het pictogram van het cameratype &#x200B;](assets/camera-icon.svg) Camera Raw dossiers: CR2/CR3, NEF, SRW/SRF, en anderen
* ![&#x200B; pictogram van het documenttype &#x200B;](assets/document-icon.svg) Documenten: DOCX, PDF, PPTX, en XLSX
* ![&#x200B; het type van videodossier pictogram &#x200B;](assets/video-icon.svg) Video&#39;s: MP4

[!DNL Assets view] ondersteunt elke binaire bestandsindeling met basisservices, zoals opslag, uploaden, kopiëren, verplaatsen, verwijderen en toevoegen van metagegevens.

[!DNL Assets view] biedt ook ondersteuning voor Camera RAW-bestanden van een groot aantal toonaangevende camerafabrikanten, waaronder Canon (CR2/CR3), Nikon (NEF), Sony (SRW/SRF), Fujifilm (RAF), Olympus (ORF) en andere, aangedreven door Adobe Camera Raw.

De verschillende bestandstypen bieden verschillende mate van ondersteuning voor de gebruiksgevallen en -functies, zoals hieronder wordt beschreven. Gebruik de legenda om het steunniveau te begrijpen.

| Ondersteuningsniveau | Beschrijving |
|-------------------|-------------------------|
| ✓ | Ondersteund |
| ✓ ‡ | Voorwaardelijk ondersteund |
| - | Niet van toepassing |

## Elementen toevoegen, uploaden en weergeven {#support-to-upload-view}

<!-- TBD: For AEM, AI files require the PDF option to be selected when saving the AI file.
-->

| Type element | [&#x200B; doorbladeren &#x200B;](/help/assets/navigate-assets-view.md) | Kopiëren | [&#x200B; uploadt &#x200B;](/help/assets/add-delete-assets-view.md) | Maken | [&#x200B; Schrapping &#x200B;](/help/assets/add-delete-assets-view.md#delete-assets) | Details | Zoomen op afbeelding | [&#x200B; onlangs Bekeken &#x200B;](/help/assets/navigate-assets-view.md) |
|-------------------|----------|----------|----------|----------|----------|-------------------|------------|-----------------|
| Rasterafbeeldingen | ✓ | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ |
| RAW-bestanden | ✓ | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ |
| Mappen | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| MP4-video&#39;s | ✓ | ✓ | ✓ | - | ✓ | ✓ ‡ | - | ✓ |
| PDF | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | ✓ |
| PSD, PSB, AI en INDD | ✓ | ✓ | ✓ | - | ✓ | ✓ ‡ | - | ✓ |
| Overige binaire bestanden | ✓ | ✓ | ✓ | - | ✓ | ✓ | - | ✓ |

<!-- Hiding CC Libraries (considered beta) as per PM feedback.
| CC Libraries  | &#10003; | &minus;  | &#10003; | &#10003; | &#10003; | &#10003; | &minus;    | &minus;         |
-->

## Elementen zoeken, gebruiken en bewerken {#support-to-search-use-edit}

<!--writer - please check RAW files row below. There was an extra column, so I deleted a duplicate section. I think I did it right. -->

| Type element | [&#x200B; Download &#x200B;](/help/assets/manage-organize-assets-view.md#download) | Slepen en slepen | [&#x200B; redacteur van het Beeld &#x200B;](/help/assets/edit-images-assets-view.md) | [Zoeken](/help/assets/search-assets-view.md) | [&#x200B; Slimme Markeringen &#x200B;](/help/assets/metadata-assets-view.md#tags) | [&#x200B; anders noemen &#x200B;](/help/assets/manage-organize-assets-view.md) | [&#x200B; Versies &#x200B;](/help/assets/manage-organize-assets-view.md#versions-of-assets) |
|---------------|----------|---------------|--------------|----------|------------|----------|----------|
| Rasterafbeeldingen | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAW-bestanden | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Mappen | ✓ | ✓ | - | ✓ | - | ✓ | ✓ |
| Video&#39;s | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ |
| CC Libraries | - | - | - | - | - | ✓ | ✓ |
| PDF | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ |
| PSD en PSB | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ |
| AI en INDD | ✓ | ✓ | - | ✓ | - | ✓ | ✓ |
| Overige binaire bestanden | ✓ | ✓ | - | ✓ | - | ✓ | ✓ |


## Elementen controleren en samenwerken {#support-to-review-collaborate}

| Type element | Annoteren | Opmerking | Taken maken en revisie uitvoeren |
|---------------|----------|----------|-------------------------|
| Rasterafbeeldingen | ✓ | ✓ | ✓ |
| RAW-bestanden | ✓ | ✓ | ✓ |
| Mappen | - | - | - |
| Video&#39;s | - | ✓ | ✓ |
| CC Libraries | - | - | - |
| PDF | - | ✓ | ✓ |
| PSD, PSB, AI en INDD | - | ✓ | ✓ |
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

| Type element | [&#x200B; Metagegevens &#x200B;](/help/assets/metadata-assets-view.md) | [&#x200B; Vertoningen &#x200B;](/help/assets/add-delete-assets-view.md#renditions) | [&#x200B; Afval &#x200B;](/help/assets/add-delete-assets-view.md#delete-assets) | Kopiëren | Verplaatsen |
|---------------|-------------------|------------|----------|----------|----------|
| Rasterafbeeldingen | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAW-bestanden | ✓ | ✓ | ✓ | ✓ | ✓ |
| Mappen | ✓ | - | ✓ | ✓ | ✓ |
| Video&#39;s | ✓ | - | ✓ | ✓ | ✓ |
| CC Libraries | ✓ | - | - | - | - |
| PDF | ✓ | - | ✓ | ✓ | ✓ |
| AI en INDD | ✓ | - | ✓ | ✓ | ✓ |
| PSD en PSB | ✓ | ✓ | ✓ | ✓ | ✓ |
| Overige binaire bestanden | ✓ | - | ✓ | ✓ | ✓ |

Gebruikers van [!DNL Adobe Asset Link] kunnen bestanden uploaden en inchecken (een nieuwe versie uploaden) in de [!DNL Assets view] -opslagplaats vanuit de ondersteunde [!DNL Adobe Creative Cloud] -bureaubladtoepassingen.

<!-- TBD: Saving the template table separately for later use.
| Asset type    | Features |
|---------------|----------|
| Raster images |          |
| Folders       |          |
| Videos        |          |
| CC Libraries  |          |
| PDF files     |          |
| PSD, PSB           |          |
| AI            |          |
| INDD          |          |

>[!MORELIKETHIS]
>
>* []()
-->

## Volgende stappen {#next-steps}

* Feedback geven op het product met de optie [!UICONTROL Feedback] die beschikbaar is in de gebruikersinterface van de Assets-weergave

* Verstrek documentatie terugkoppelt gebruikend [!UICONTROL Edit this page] ![&#x200B; uitgeeft de pagina &#x200B;](assets/do-not-localize/edit-page.png) of [!UICONTROL Log an issue] ![&#x200B; creeer een kwestie GitHub &#x200B;](assets/do-not-localize/github-issue.png) beschikbaar op juiste sidebar

* De Zorg van de Klant van het contact [&#128279;](https://experienceleague.adobe.com/nl?support-solution=General#support)
