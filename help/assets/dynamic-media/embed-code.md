---
title: De Dynamic Media Video- of Image-viewer insluiten op een webpagina
description: Leer hoe u Dynamic Media-video of afbeeldingselementen op een webpagina insluit.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 76335781-e39f-4aae-967f-5af8634d8f61
source-git-commit: 35caac30887f17077d82f3370f1948e33d7f1530
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 21%

---

# De Dynamic Media Video-, Image Viewer- of Dimensional-viewer insluiten op een webpagina {#embedding-the-video-or-image-viewer-on-a-web-page}

Gebruik de functie **[!UICONTROL Embed Code]** wanneer u de video wilt afspelen of een asset wilt bekijken die op een webpagina is ingesloten. U kopieert de insluitcode naar het klembord, zodat u deze op uw webpagina&#39;s kunt plakken. Het bewerken van de code is niet toegestaan in het dialoogvenster **[!UICONTROL Embed Code]**.

U sluit alleen URL&#39;s in als u _niet_ Adobe Experience Manager gebruiken als uw WCM. Als u Experience Manager als uw WCM gebruikt, [u voegt de elementen rechtstreeks op de pagina toe](adding-dynamic-media-assets-to-pages.md).

Zie [URL&#39;s koppelen aan uw webtoepassing](linking-urls-to-yourwebapplication.md).

Zie [Geoptimaliseerde afbeeldingen leveren voor een responsieve site](responsive-site.md).

>[!NOTE]
>
>De insluitcode kan pas worden gekopieerd nadat u het geselecteerde element hebt gepubliceerd. Daarnaast moet u ook de voorinstelling van de viewer of de voorinstelling van de afbeelding publiceren.
>
>Zie [Elementen publiceren](publishing-dynamicmedia-assets.md).
>
>Zie [Voorinstellingen viewer publiceren](managing-viewer-presets.md#publishing-viewer-presets).
>
>Zie [Voorinstellingen afbeelding publiceren](managing-image-presets.md#publishing-image-presets).

**De Dynamic Media Video- of Image-viewer insluiten op een webpagina:**

1. Ga naar de *gepubliceerd* video of afbeeldingselement waarvan u de insluitcode wilt kopiëren.

   Onthoud dat de insluitcode alleen beschikbaar is om te kopiëren *nadat* u de assets eerst hebt *gepubliceerd*. Bovendien moet de viewervoorinstelling of afbeeldingsvoorinstelling ook worden gepubliceerd.

   Zie [Elementen publiceren](publishing-dynamicmedia-assets.md).

   Zie [Voorinstellingen viewer publiceren](managing-viewer-presets.md#publishing-viewer-presets).

   Zie [Voorinstellingen afbeelding publiceren](managing-image-presets.md#publishing-image-presets).

1. Selecteer in het linkerspoor de vervolgkeuzelijst en selecteer **[!UICONTROL Viewers]**.
1. Selecteer in het linkerspoor een naam voor de viewervoorinstelling. De viewervoorinstelling wordt toegepast op het element.
1. Selecteer **[!UICONTROL Embed]**.
1. In de **[!UICONTROL Embed Code]** , kopieert u de volledige code naar het klembord en selecteert u **[!UICONTROL Close]**.
1. Plak de insluitcode in uw webpagina&#39;s.

## Gebruik HTTP/2 om uw Dynamic Media-middelen te leveren {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van Dynamic Media-middelen kan nu plaatsvinden via HTTP/2, wat betere responstijd en laadtijden biedt.

Zie [HTTP2 Levering van inhoud](http2faq.md) voor volledige informatie over hoe u aan de slag gaat met HTTP/2 met uw Dynamic Media-account.
