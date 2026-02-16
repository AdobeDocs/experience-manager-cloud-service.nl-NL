---
title: Dynamische media instellen
description: Als u dynamische media wilt instellen, moet u Dynamische media configureren en voorinstellingen voor afbeeldingen en viewers beheren.
contentOwner: Rick Brough
feature: Configuration,Viewer Presets,Image Presets,Dynamic Media
role: Admin,User
exl-id: 83b70b17-7ee3-41cb-be90-c92ca161660e
source-git-commit: 8a8f3d7b17d79791a3ebf6b583ffcccfcf214470
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# Dynamische media instellen {#setting-up-dynamic-media}

{{work-with-dynamic-media}}

[&#x200B; Dynamische Media &#x200B;](https://business.adobe.com/products/experience-manager/assets/dynamic-media.html) helpt u activa beheren door rijke visuele handel en marketing activa op bestelling te leveren, automatisch geschraapt voor consumptie op Web, mobiele, en sociale plaatsen. Met behulp van een set primaire bronelementen genereert Dynamic Media meerdere variaties van rijke inhoud in real-time via het algemene, schaalbare, voor prestaties geoptimaliseerde netwerk.

<!-- OBSOLETE UNTIL THE INTEGRATING SCENE7 TOPIC GETS A MAJOR UPDATE

>[!NOTE]
>
>This documentation describes Dynamic Media capabilites, which are integrated directly into [!DNL Experience Manager]. If you are using Dynamic Media Classic (previously called Scene7) integrated into [!DNL Experience Manager], see [Dynamic Media Classic integration documentation](/help/sites-cloud/administering/integrating-scene7.md).
>
>See [Dual Use Scenario](/help/sites-cloud/administering/integrating-scene7.md#dual-use-scenario) for times when you may want to use [!DNL Experience Manager] integrated with Dynamic Media Classic along with Dynamic Media.

-->

Als u Dynamische Media beheert, zijn de volgende onderwerpen van belang:

* [Dynamische media configureren](config-dm.md)
* [Voorinstellingen afbeelding beheren](managing-image-presets.md)
* [Viewer-voorinstellingen beheren](managing-viewer-presets.md)
* [Problemen met dynamische media oplossen](troubleshoot-dm.md)

Zie ook de volgende onderwerpen:

* [Videocodering en videoprofielen](video-profiles.md)
* [Afbeeldingsprofielen](image-profiles.md)

>[!NOTE]
>
>**als u bevordert:**
>
>* Nadat u Adobe [!DNL Experience Manager] hebt gestart en uitgevoerd, wordt Dynamische media automatisch ingeschakeld voor elk element dat u uploadt (tenzij dit expliciet is uitgeschakeld door de systeembeheerder). Als u zich op een geüpgrade instantie van [!DNL Experience Manager] en een nieuwe versie van Dynamic Media bevindt, moet u uw elementen waarschijnlijk opnieuw verwerken om ze voor Dynamic Media in te schakelen. Zie [&#x200B; activa in een omslag &#x200B;](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) opnieuw verwerken.


## Eenmalige DNS-update vereist voor dynamische vernieuwing van mediacertificaten {#dns-update-dynamic-media-certificate-renewals}

Als uw domein een DNS-record van de CAA (Certificate Authority Authorization) gebruikt, moet u DigiCert toestaan om verdere vernieuwing van TLS/SSL-certificaten toe te staan die worden gebruikt door Dynamic Media hostnames.

Voeg de volgende CAA-record toe aan de hoofdmap (apex) van uw domein:

```
<yourdomain> CAA 0 issue "digicert.com"
```

Dit is een eenmalige wijziging.

U kunt verifiëren of een verslag van de CAA gebruikend uw DNS leveranciershulpmiddelen of a [&#x200B; opzoeknut van de CAA &#x200B;](https://caatest.co.uk/) bestaat.

Als een CAA-record bestaat en DigiCert niet is geautoriseerd, mislukt het vernieuwen van het certificaat wanneer het huidige certificaat verloopt. Dit kan downtime veroorzaken voor het afspelen van afbeeldingen en video. Als er geen CAA-record voor uw domein bestaat, is geen actie vereist.
