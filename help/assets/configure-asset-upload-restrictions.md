---
title: Beperkingen voor het uploaden van middelen configureren
description: Configureer Adobe Experience Manager Assets om het type elementen te beperken dat gebruikers op basis van het MIME-type kunnen uploaden. Zo voorkomt u ongewenste uploads in de gewenste indeling en schadelijke bestanden.
exl-id: 094c31f3-f2e9-4b44-9995-c76fb78ca458
feature: Upload, Asset Ingestion
role: User, Admin, Developer
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
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

Om [!DNL Experience Manager] te vormen om gebruikers te beperken om dossiers van specifieke types te uploaden MIME:

1. Navigeer naar **[!UICONTROL Tools > Assets > Assets Configurations]** .

1. Klik op **[!UICONTROL Upload Restrictions]**.

1. Klik op **[!UICONTROL Add]** om de toegestane MIME-typen te definiëren.

1. Geef het MIME-type op in het tekstvak. U kunt nogmaals op **[!UICONTROL Add]** klikken om meer toegestane MIME-typen op te geven. U kunt ![ schrappingspictogram ](assets/delete-icon.svg) ook klikken om het even welk type MIME van de lijst te schrappen.

1. Klik op **[!UICONTROL Save]**.

**Voorbeeld 1: Toestaan uploadt van alle beelden en dossiers van PDF aan Experience Manager Assets**

Voer de volgende instellingen uit om het uploaden van afbeeldingen in alle indelingen en PDF-bestanden naar Experience Manager Assets toe te staan:

![ Activa uploadt beperkingen ](assets/asset-upload-restrictions.png)

`image/*` als het MIME-type het uploaden van afbeeldingen in alle indelingen toestaat. `application/pdf` als het MIME-type het uploaden van PDF-bestanden naar Experience Manager Assets toestaat.

Als u probeert een bestand te uploaden dat niet is opgenomen in de lijst met toegestane MIME-typen, geeft Experience Manager Assets het volgende foutbericht weer:

![ Beperkte dossiers ](assets/asset-upload-restricted-files.png)

`Screen Recording 2022-08-31 at 3.36.09 PM.mov` verwijst naar een bestandsnaam die niet is opgenomen in de toegestane MIME-typen.

**Voorbeeld 2: Toestaan upload van specifieke beeldformaten aan Experience Manager Assets**

Voer de volgende instellingen uit om specifieke afbeeldingsindelingen toe te voegen aan de toegestane MIME-typen en het uploaden van alle andere elementindelingen te beperken:

![ de beperkingen van Activa ](assets/asset-restrictions.png)

Op basis van de instellingen in de afbeelding kunt u afbeeldingen in de indelingen .JPG, .PNG en .GIF uploaden naar Experience Manager Assets.

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
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
