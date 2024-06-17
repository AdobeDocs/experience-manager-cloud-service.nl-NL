---
title: Hoe kunt u uw middelen in AEM voorzien van een watermerk?
description: Leer hoe u in AEM een digitaal watermerk aan uw middelen kunt toevoegen. Met watermerken kunnen gebruikers de authenticiteit en de copyrighteigendom van de elementen controleren.
contentOwner: AG
feature: Asset Management,Publishing
role: User, Admin
exl-id: 210f8925-bd15-4b4a-8714-5a1486eeb49e
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 2%

---

# Watermerk uw elementen {#watermark-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/watermarking.html) |
| AEM as a Cloud Service | Dit artikel |

[!DNL Adobe Experience Manager Assets] Hiermee kunt u een digitaal watermerk toevoegen aan afbeeldingen en video&#39;s. [!DNL Assets] ondersteunt het toepassen van een afbeelding als watermerk op andere afbeeldingsbestanden. Met watermerken kunnen gebruikers de authenticiteit en de copyrighteigendom van de elementen controleren. Een watermerk kan ook worden gebruikt om de status van een document aan te geven als vertrouwelijk, concept, geldigheid enzovoort.

Om te vormen [!DNL Experience Manager] op watermerkelementen:

1. Een PNG-bestand wordt toegepast als een watermerk. Upload dit bestand naar uw DAM-opslagplaats.

1. Navigeren naar **[!UICONTROL Tools > Assets > Assets Configurations]**.

1. Klik op **[!UICONTROL System Watermarking Profile]**.

1. Op de [!UICONTROL System Watermarking Profile page], geeft u het afbeeldingspad op dat in stap 1 naar de DAM-opslagplaats is geüpload.

1. Geef een watermerkschaal op, variërend van 0,0 tot 1,0, ten opzichte van de weergavebreedte in het dialoogvenster **[!UICONTROL Scale]** veld.

1. Klik op **[!UICONTROL Save]**.

   ![Detector van duplicatie van middelen](assets/system-watermarking-profile.png)

   >[!NOTE]
   >
   >Als u een systeemwatermerkingsprofiel hebt geconfigureerd met `com.adobe.cq.assetcompute.impl.profile.WatermarkingProfileServiceImpl.cfg.json` configuratiedossier (configuratie OSGi), kunt u het blijven gebruiken, nochtans, adviseert de Adobe het gebruiken van de nieuwe methode.


1. [Een verwerkingsprofiel maken](/help/assets/asset-microservices-configure-and-use.md#create-custom-profile) gebruik te maken van asset microservices om het watermerk toe te passen.

   ![Middelverwerkingsprofiel om watermerk te maken](assets/watermark-processing-profile.png)

   Zorg ervoor dat u de **[!UICONTROL Watermark]** schakelen tijdens het maken van het verwerkingsprofiel.

1. [De verwerkingsprofielen toepassen op een map](/help/assets/asset-microservices-configure-and-use.md#use-profiles) om elementen met een watermerk te maken.

## Tips en beperkingen {#tips-limitations-bestpractices}

* U kunt één configuratie gebruiken om al uw elementen te voorzien van een watermerk. Er wordt slechts één afbeelding gebruikt voor watermerken en de breedte is vast.
* U kunt het watermerk in het midden plaatsen zonder het watermerk naast elkaar te plaatsen.
* Watermerken op basis van tekst worden niet ondersteund.

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

>[!MORELIKETHIS]
>
>* [Overzicht van services voor middelenmicroservices](/help/assets/asset-microservices-overview.md).
>* [Middelenmicroservices gebruiken met verwerkingsprofielen](/help/assets/asset-microservices-configure-and-use.md).
