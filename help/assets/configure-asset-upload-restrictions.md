---
title: Beperkingen voor het uploaden van middelen configureren
description: Configureer Adobe Experience Manager Assets om het type elementen te beperken dat gebruikers op basis van het MIME-type kunnen uploaden. Zo voorkomt u ongewenste uploads in de gewenste indeling en schadelijke bestanden.
exl-id: 094c31f3-f2e9-4b44-9995-c76fb78ca458
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Beperkingen voor het uploaden van middelen configureren {#configure-asset-upload-restrictions}

U kunt Adobe Experience Manager Assets configureren om het type elementen te beperken dat gebruikers kunnen uploaden op basis van het MIME-type.

>[!IMPORTANT]
>
>Standaard kunnen gebruikers met Experience Manager Assets elementen van alle MIME-typen uploaden. U kunt de instellingen echter zo configureren dat gebruikers alleen bestanden van bepaalde MIME-typen kunnen uploaden.

## Vereisten {#prerequisites-asset-upload-restrictions}

U moet beheerdersrechten hebben om beperkingen voor het uploaden van elementen te configureren.

## Beperkingen toepassen voor het uploaden van middelen {#apply-restrictions-asset-uploadsssssss}

Om te vormen [!DNL Experience Manager] om gebruikers te beperken tot het uploaden van bestanden van specifieke MIME-typen:

1. Navigeren naar **[!UICONTROL Tools > Assets > Assets Configurations]**.

1. Klik op **[!UICONTROL Upload Restrictions]**.

1. Klikken **[!UICONTROL Add]** om de toegestane MIME-typen te definiëren.

1. Geef het MIME-type op in het tekstvak. U kunt op **[!UICONTROL Add]** nogmaals om meer toegestane MIME-typen op te geven. U kunt ook op ![verwijderpictogram](assets/delete-icon.svg) om een MIME-type uit de lijst te verwijderen.

1. Klik op **[!UICONTROL Save]**.

**Voorbeeld 1: het uploaden van alle afbeeldingen en PDF-bestanden naar Experience Manager Assets toestaan**

Voer de volgende instellingen uit om het uploaden van afbeeldingen in alle indelingen en PDF-bestanden naar Experience Manager Assets toe te staan:

![Beperkingen voor het uploaden van middelen](assets/asset-upload-restrictions.png)

`image/*` aangezien het MIME-type het uploaden van afbeeldingen in alle indelingen toestaat. `application/pdf` aangezien het MIME-type het uploaden van PDF-bestanden naar Experience Manager Assets toestaat.

Als u probeert een bestand te uploaden dat niet is opgenomen in de lijst met toegestane MIME-typen, geeft Experience Manager Assets het volgende foutbericht weer:

![Beperkte bestanden](assets/asset-upload-restricted-files.png)

`Screen Recording 2022-08-31 at 3.36.09 PM.mov` verwijst naar een bestandsnaam die niet is opgenomen in de toegestane MIME-typen.

**Voorbeeld 2: uploaden van specifieke afbeeldingsindelingen naar Experience Manager Assets toestaan**

Voer de volgende instellingen uit om specifieke afbeeldingsindelingen toe te voegen aan de toegestane MIME-typen en het uploaden van alle andere elementindelingen te beperken:

![Beperkingen op activa](assets/asset-restrictions.png)

Op basis van de instellingen in de afbeelding kunt u afbeeldingen in de indelingen .JPG, .PNG en .GIF uploaden naar Experience Manager Assets.

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Middelen publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
