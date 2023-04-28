---
title: Watermerk van de elementen
description: Voeg een watermerk toe aan uw digitale elementen.
contentOwner: AG
feature: Asset Management,Publishing
role: User,Admin
exl-id: 210f8925-bd15-4b4a-8714-5a1486eeb49e
source-git-commit: 8bdd89f0be5fe7c9d4f6ba891d7d108286f823bb
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 5%

---

# Watermerk uw elementen {#watermark-assets}

[!DNL Adobe Experience Manager Assets] Hiermee kunt u een digitaal watermerk aan afbeeldingen toevoegen. [!DNL Assets] ondersteunt het toepassen van een afbeelding als watermerk op andere afbeeldingsbestanden. Met watermerken kunnen gebruikers de authenticiteit en de copyrighteigendom van de elementen controleren. Een watermerk kan ook worden gebruikt om de status van een document aan te geven als vertrouwelijk, concept, geldigheid enzovoort.

Om te vormen [!DNL Experience Manager] op watermerkelementen:

1. Een PNG-bestand wordt toegepast als een watermerk. Upload dit bestand naar uw DAM-opslagplaats.

1. Ga naar **[!UICONTROL Tools > Assets > Assets Configurations]**.

1. Klik op **[!UICONTROL System Watermarking Profile]**.

1. Op de [!UICONTROL System Watermarking Profile page], geeft u het afbeeldingspad op dat in stap 1 naar de DAM-opslagplaats is geüpload.

1. Geef een watermerkschaal op, variërend van 0,0 tot 1,0, ten opzichte van de weergavebreedte in het dialoogvenster **[!UICONTROL Scale]** veld.

1. Klik op **[!UICONTROL Save]**.

   ![Detector van duplicatie van middelen](assets/system-watermarking-profile.png)

   >[!NOTE]
   >
   >Als u een systeemwatermerkingsprofiel hebt geconfigureerd met `com.adobe.cq.assetcompute.impl.profile.WatermarkingProfileServiceImpl.cfg.json` configuratiedossier (configuratie OSGi), kunt u het blijven gebruiken, nochtans, adviseert Adobe om de nieuwe methode te gebruiken.


1. [Een verwerkingsprofiel maken](/help/assets/asset-microservices-configure-and-use.md#create-custom-profile) om gebruik te maken van asset microservices om het watermerk toe te passen.

   ![Middelverwerkingsprofiel om watermerk te maken](assets/watermark-processing-profile.png)

   Zorg ervoor dat u de **[!UICONTROL Watermark]** schakelen tijdens het maken van het verwerkingsprofiel.

1. [De verwerkingsprofielen toepassen op een map](/help/assets/asset-microservices-configure-and-use.md#use-profiles) om elementen met een watermerk te maken.

## Tips en beperkingen {#tips-limitations-bestpractices}

* U kunt één configuratie gebruiken om al uw elementen te voorzien van een watermerk. Er wordt slechts één afbeelding gebruikt voor watermerken en de breedte is vast.
* U kunt het watermerk in het midden plaatsen zonder het watermerk naast elkaar te plaatsen.
* Watermerken op basis van tekst worden niet ondersteund.

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [HTTP-API voor assets](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
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
>* [Overzicht van services voor middelenmicroservices](/help/assets/asset-microservices-overview.md).
>* [Middelenmicroservices gebruiken met verwerkingsprofielen](/help/assets/asset-microservices-configure-and-use.md).

