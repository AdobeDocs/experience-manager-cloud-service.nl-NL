---
title: De Dynamic Media Video- of Image-viewer insluiten op een webpagina
description: Leer hoe u dynamische media-video of afbeeldingselementen op een webpagina insluit.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 76335781-e39f-4aae-967f-5af8634d8f61
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 20%

---

# Dynamische mediavideo, afbeeldingsviewer of dimensionale viewer insluiten op een webpagina {#embedding-the-video-or-image-viewer-on-a-web-page}

Gebruik de functie **[!UICONTROL Embed Code]** wanneer u de video wilt afspelen of een asset wilt bekijken die op een webpagina is ingesloten. U kopieert de insluitcode naar het klembord, zodat u deze op uw webpagina&#39;s kunt plakken. Het bewerken van de code is niet toegestaan in het dialoogvenster **[!UICONTROL Embed Code]**.

U bedt URLs slechts als u _niet_ gebruikend Adobe Experience Manager als uw WCM bent. Als u Experience Manager als uw WCM gebruikt, [ voegt u de activa direct op uw pagina ](adding-dynamic-media-assets-to-pages.md) toe.

Zie [ Verbinding URLs aan uw Toepassing van het Web ](linking-urls-to-yourwebapplication.md).

Zie [ Geoptimaliseerde Beelden voor een Responsieve Plaats ](responsive-site.md) leveren.

>[!NOTE]
>
>De insluitcode kan pas worden gekopieerd nadat u het geselecteerde element hebt gepubliceerd. Daarnaast moet u ook de voorinstelling van de viewer of de voorinstelling van de afbeelding publiceren.
>
>Zie [ publiceren Assets ](publishing-dynamicmedia-assets.md).
>
>Zie [ Publish Kijker vooraf instelt ](managing-viewer-presets.md#publishing-viewer-presets).
>
>Zie [ publiceren Beeld vooraf instelt ](managing-image-presets.md#publishing-image-presets).

**om de Dynamische Video van Media of kijker van het Beeld op een Web-pagina in te bedden:**

1. Navigeer aan de *gepubliceerde* video of beeldactiva de waarvan inbedcode u wilt kopiëren.

   Onthoud dat de insluitcode alleen beschikbaar is om te kopiëren *nadat* u de assets eerst hebt *gepubliceerd*. Bovendien moet de viewervoorinstelling of afbeeldingsvoorinstelling ook worden gepubliceerd.

   Zie [ publiceren Assets ](publishing-dynamicmedia-assets.md).

   Zie [ Publish Kijker vooraf instelt ](managing-viewer-presets.md#publishing-viewer-presets).

   Zie [ publiceren Beeld vooraf instelt ](managing-image-presets.md#publishing-image-presets).

1. Selecteer in de linkertrack de vervolgkeuzelijst en selecteer **[!UICONTROL Viewers]** .
1. Selecteer in het linkerspoor een naam voor de viewervoorinstelling. De viewervoorinstelling wordt toegepast op het element.
1. Selecteer **[!UICONTROL Embed]** .
1. Kopieer in het dialoogvenster **[!UICONTROL Embed Code]** de gehele code naar het klembord en selecteer vervolgens **[!UICONTROL Close]** .
1. Plak de insluitcode in uw webpagina&#39;s.

## HTTP/2 gebruiken om uw dynamische media-elementen te leveren {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van dynamische media-elementen kan nu plaatsvinden via HTTP/2, wat betere responstijd en laadtijden biedt.

Zie [ HTTP2 Levering van Inhoud ](http2faq.md) voor volledige details bij het worden begonnen HTTP/2 met uw Dynamische rekening van Media te gebruiken.
