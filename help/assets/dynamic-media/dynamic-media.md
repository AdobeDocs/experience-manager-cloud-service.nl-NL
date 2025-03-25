---
title: Werken met dynamische media
description: Leer wat Dynamic Media is en u kunt Dynamic Media gebruiken om middelen te leveren die u kunt gebruiken op internet, mobiele en sociale sites.
contentOwner: Rick Brough
feature: Dynamic Media,Asset Management
role: Admin,User
exl-id: 3ec3cb85-88ce-4277-a45c-30e52c75ed42
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 0%

---

# Werken met dynamische media {#working-with-dynamic-media}

[ de Dynamische hulp van Media ](https://business.adobe.com/products/experience-manager/assets/dynamic-media.html) levert rijke visuele handel en marketing activa op bestelling, automatisch geschraapt voor consumptie op Web, mobiele, en sociale plaatsen. Met behulp van een set primaire bronelementen genereert Dynamic Media meerdere variaties van rijke inhoud in real-time via het algemene, schaalbare, voor prestaties geoptimaliseerde netwerk.

Dynamic Media biedt interactieve kijkervaringen, zoals zoomen, 360° draaien en video. Dynamic Media integreert op unieke wijze de workflows van de Adobe Experience Manager Digital Asset Management (Assets)-oplossing om het beheerproces voor digitale campagnes te vereenvoudigen en te stroomlijnen.

<!-- >[!NOTE]
>
>A Community article is available on [Working with Adobe Experience Manager and Dynamic Media](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html). -->

## Wat is Dynamic Media?

Dynamic Media in Adobe Experience Manager (AEM) as a Cloud Service is een krachtige oplossing die u helpt bij het beheren, leveren en optimaliseren van veelzijdige media-elementen, zoals afbeeldingen en video&#39;s op verschillende digitale platforms. Het transformeert statische media in dynamische, boeiende ervaringen door aanpassingen in real time toe te staan, zoals het resizing, het bebouwen, en het aanpassen van kwaliteit gebaseerd op het apparaat of het schermgrootte van de gebruiker. Met Dynamische media worden uw middelen automatisch aangepast voor de beste visuele ervaring, of gebruikers zich op een desktop, mobiel of tablet bevinden.

Een groot voordeel van Dynamic Media is de mogelijkheid om mediabeheer te stroomlijnen. U te hoeven om veelvoudige versies van beelden of video-Dynamische Media niet te creëren behandelt het allen door het meest aangewezen formaat voor elke situatie te leveren. E-commercebedrijven kunnen bijvoorbeeld profiteren van productweergaven van 360 graden of zoombare afbeeldingen om interactieve ervaringen te creëren, terwijl websites met veel inhoud snelle videostreaming van hoge kwaliteit kunnen garanderen. Dit resulteert in snellere ladingstijden en boeiende gebruikerservaring, die uiteindelijk tot hogere klantentevredenheid en betere omzettingspercentages leidt.

Dynamic Media integreert naadloos met uw DAM-systeem (Digital Asset Management) in AEM, zodat u één platform hebt voor het opslaan, organiseren en implementeren van uw media. Deze gecentraliseerde aanpak vereenvoudigt samenwerking tussen verschillende teams en biedt realtime inzicht in de prestaties van bedrijfsmiddelen. Of u nu uw aandacht richt op het aanbieden van fascinerende beelden of het verbeteren van media-gedreven gebruikersinteractie, de hulp van de Media helpt uw inhoud voor om het even welk kanaal optimaliseren, die het een essentieel hulpmiddel voor ondernemingen maken die hun digitale aanwezigheid willen verhogen.

## Wat u met Dynamische Media kunt doen {#what-you-can-do-with-dynamic-media}

Met Dynamische media kunt u uw elementen beheren voordat u ze publiceert. Hoe te met activa in het algemeen te werken is in detail behandeld in [ Werkend met Digitale Assets ](/help/assets/manage-digital-assets.md). Algemene onderwerpen zijn het uploaden, downloaden, bewerken en publiceren van elementen, het weergeven en bewerken van eigenschappen en het zoeken naar elementen.

De dynamische Media-enige eigenschappen omvatten het volgende:

* [Carousel Banners](carousel-banners.md)
* [Afbeeldingssets](image-sets.md)
* [Interactieve afbeeldingen](interactive-images.md)
* [Interactieve video&#39;s](interactive-videos.md)
* [Gemengde mediasets](mixed-media-sets.md)
* [Panoramische afbeeldingen](panoramic-images.md)
* [Sets draaien](spin-sets.md)
* [Video](video.md)
* [Dynamische media Assets leveren](delivering-dynamic-media-assets.md)
* [Assets beheren](managing-assets.md)
* [Snelle weergaven gebruiken om aangepaste pop-upvensters te maken](custom-pop-ups.md)

Zie ook [ Opstelling Dynamische Media ](administering-dynamic-media.md).

<!-- 

OBSOLETE UNTIL INTEGRATING SCENE7 TOPIC GETS A MAJOR UPDATE
>[!NOTE]
>
>To understand the differences between using Dynamic Media and integrating Dynamic Media Classic with AEM, see [Dynamic Media Classic integration versus Dynamic Media](/help/sites-cloud/administering/integrating-scene7.md#aem-scene-integration-versus-dynamic-media).

-->

## Dynamische media ingeschakeld en Dynamische media uitgeschakeld {#dynamic-media-on-versus-dynamic-media-off}

U kunt zien of Dynamische media is ingeschakeld (ingeschakeld) door de volgende kenmerken:

* Dynamische uitvoeringen zijn beschikbaar wanneer u elementen downloadt of een voorvertoning weergeeft.
* Afbeeldingssets, centrifuges en gemengde mediasets zijn beschikbaar.
* PTIFF-uitvoeringen worden gemaakt.

Wanneer u op een afbeeldingselement klikt, is de weergave van het element anders en Dynamische media ingeschakeld. Dynamic Media gebruikt de HTML5-viewers op aanvraag.

### Dynamische uitvoeringen {#dynamic-renditions}

Dynamische uitvoeringen zoals voorinstellingen voor afbeeldingen en viewers (onder **[!UICONTROL Dynamic]** ) zijn beschikbaar wanneer Dynamische media is ingeschakeld.

![ chlimage_1-358 ](assets/chlimage_1-358.png)

### Dynamische mediafobeeldingssets, spelersets, gemengde mediasets {#image-sets-spins-sets-mixed-media-sets}

Afbeeldingssets, centrifuges en gemengde mediasets zijn beschikbaar als Dynamische media is ingeschakeld.

![ chlimage_1-359 ](assets/chlimage_1-359.png)

### Dynamische PTIFF-uitvoeringen waarvoor media is ingeschakeld {#ptiff-renditions}

Dynamische media-ingeschakelde elementen omvatten `pyramid.tiffs`.

![ chlimage_1-360 ](assets/chlimage_1-360.png)

### Weergave van dynamische media-elementen wijzigen {#asset-views-change}

Als Dynamische media is ingeschakeld, kunt u in- en uitzoomen door op de knoppen `+` en `-` te klikken. U kunt ook selecteren om in bepaalde gebieden in te zoomen. Met Omkeren gaat u naar de oorspronkelijke versie en u kunt de afbeelding op het volledige scherm weergeven door op de diagonale pijlen te klikken. Dynamische media ingeschakeld wordt als volgt weergegeven:

![ chlimage_1-361 ](assets/chlimage_1-361.png)

Als Dynamische media is uitgeschakeld, kunt u in- en uitzoomen en terugkeren naar de oorspronkelijke grootte:

![ chlimage_1-362 ](assets/chlimage_1-362.png)
