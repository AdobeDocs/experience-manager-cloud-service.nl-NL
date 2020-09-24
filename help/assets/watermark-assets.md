---
title: Watermerk uw elementen
description: Voeg een watermerk toe aan uw digitale elementen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f1fcddf196a1a2bfa2629dbd6a8fe0ac057a3d07
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Watermerk uw elementen {#watermark-assets}

[!DNL Adobe Experience Manager Assets] Hiermee kunt u een digitaal watermerk aan afbeeldingen toevoegen. [!DNL Assets] ondersteunt het toepassen van een afbeelding als watermerk op andere afbeeldingsbestanden. Met watermerken kunnen gebruikers de authenticiteit en de copyrighteigendom van de elementen controleren. Een watermerk kan ook worden gebruikt om de status van een document aan te geven als vertrouwelijk, concept, geldigheid enzovoort.

Voer de volgende stappen uit om Experience Manager te configureren naar watermerkelementen:

1. Een PNG-bestand wordt toegepast als een watermerk. Upload dit bestand in uw DAM-opslagplaats.

1. Open de Git-opslagplaats voor Cloud Manager die aan uw omgeving is gekoppeld. Leg een bestand met de naam `com.adobe.cq.assetcompute.impl.profile.WatermarkingProfileServiceImpl.json` in de Git-opslagplaats van Cloud Manager vast met de volgende inhoud. Voor meer details, zie [hoe te configuratie OSGi in Experience Manager als Cloud Service](/help/implementing/deploying/configuring-osgi.md)doen.

   ```json
   {
   "watermark": "/content/dam/<path-to-watermark-image.png>",
    "width": 100
   }
   ```

1. [Maak een verwerkingsprofiel](/help/assets/asset-microservices-configure-and-use.md#create-custom-profile) om de assetmicroservices te gebruiken voor het toepassen van het watermerk.

   ![Middelverwerkingsprofiel om watermerk te maken](assets/watermark-processing-profile.png)

1. [Pas de verwerkingsprofielen toe op een map](/help/assets/asset-microservices-configure-and-use.md#use-profiles) om elementen met een watermerk te maken.

## Tips en beperkingen {#tips-limitations-bestpractices}

* U kunt één configuratie gebruiken om al uw elementen te voorzien van een watermerk. Er wordt slechts één afbeelding gebruikt voor watermerken en de breedte is vast.
* U kunt het watermerk in het midden plaatsen zonder het watermerk naast elkaar te plaatsen.
* Watermerken op basis van tekst worden niet ondersteund.

>[!MORELIKETHIS]
>
>* [Overzicht](/help/assets/asset-microservices-overview.md)van Asset microservices.
>* [Gebruik assetmicroservices met verwerkingsprofielen](/help/assets/asset-microservices-configure-and-use.md).

