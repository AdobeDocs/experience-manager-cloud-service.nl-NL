---
title: Werken met Dynamic Media
description: Meer informatie over wat Dynamic Media is en Dynamic Media kunt u gebruiken om middelen te leveren die u kunt gebruiken op internet, mobiele apparaten en sociale sites.
contentOwner: Rick Brough
feature: Dynamic Media,Asset Management
role: Admin,User
exl-id: 3ec3cb85-88ce-4277-a45c-30e52c75ed42
source-git-commit: 57fb7a011cb2da853cdca4f3233cd56775f4a459
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 0%

---

# Werken met Dynamic Media {#working-with-dynamic-media}

[ Dynamic Media ](https://business.adobe.com/products/experience-manager/assets/dynamic-media.html) hulp levert rijke visuele handel en marketing activa op bestelling, automatisch geschraapt voor consumptie op Web, mobiele, en sociale plaatsen. Met behulp van een set primaire bronelementen genereert en levert Dynamic Media in real-time meerdere variaties van rijke inhoud via het wereldwijde, schaalbare, voor prestaties geoptimaliseerde netwerk.

Dynamic Media biedt interactieve kijkervaringen, zoals zoomen, 360° draaien en video. Dynamic Media integreert op unieke wijze de workflows van de Adobe Experience Manager Digital Asset Management (Assets)-oplossing om het beheerproces voor digitale campagnes te vereenvoudigen en te stroomlijnen.

<!-- >[!NOTE]
>
>A Community article is available on [Working with Adobe Experience Manager and Dynamic Media](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html). -->

## Wat is Dynamic Media?

Dynamic Media in Adobe Experience Manager (AEM) as a Cloud Service is een krachtige oplossing die u helpt bij het beheren, leveren en optimaliseren van veelzijdige media-elementen, zoals afbeeldingen en video&#39;s op verschillende digitale platforms. Het transformeert statische media in dynamische, boeiende ervaringen door aanpassingen in real time toe te staan, zoals het resizing, het bebouwen, en het aanpassen van kwaliteit gebaseerd op het apparaat of het schermgrootte van de gebruiker. Met Dynamic Media worden uw middelen automatisch aangepast voor de beste visuele ervaring, of gebruikers nu op een desktop, mobiel of tablet staan.

Een groot voordeel van Dynamic Media is het stroomlijnen van het mediabeheer. U hoeft niet meerdere versies van afbeeldingen of video&#39;s te maken. Dynamic Media verwerkt dit alles door de meest geschikte indeling voor elke situatie te bieden. E-commercebedrijven kunnen bijvoorbeeld profiteren van productweergaven van 360 graden of zoombare afbeeldingen om interactieve ervaringen te creëren, terwijl websites met veel inhoud snelle videostreaming van hoge kwaliteit kunnen garanderen. Dit resulteert in snellere ladingstijden en boeiende gebruikerservaring, die uiteindelijk tot hogere klantentevredenheid en betere omzettingspercentages leidt.

Dynamic Media kan naadloos worden geïntegreerd met uw DAM-systeem (Digital Asset Management) in AEM, zodat u één platform hebt voor het opslaan, organiseren en implementeren van uw media. Deze gecentraliseerde aanpak vereenvoudigt samenwerking tussen verschillende teams en biedt realtime inzicht in de prestaties van bedrijfsmiddelen. Of u nu uw aandacht richt op het aanbieden van fascinerende beelden of het verbeteren van media-gedreven gebruikersinteractie, helpt Dynamic Media uw inhoud voor om het even welk kanaal te optimaliseren, die het een essentieel hulpmiddel voor ondernemingen maken die hun digitale aanwezigheid willen verhogen.

## Wat u met Dynamic Media kunt doen {#what-you-can-do-with-dynamic-media}

Met Dynamic Media kunt u uw elementen beheren voordat u ze publiceert. Hoe te met activa in het algemeen te werken is in detail behandeld in [ Werkend met Digitale Assets ](/help/assets/manage-digital-assets.md). Algemene onderwerpen zijn het uploaden, downloaden, bewerken en publiceren van elementen, het weergeven en bewerken van eigenschappen en het zoeken naar elementen.

Alleen Dynamic Media biedt de volgende functies:

* [Carousel Banners](carousel-banners.md)
* [Afbeeldingssets](image-sets.md)
* [Interactieve afbeeldingen](interactive-images.md)
* [Interactieve video&#39;s](interactive-videos.md)
* [Gemengde mediasets](mixed-media-sets.md)
* [Panoramische afbeeldingen](panoramic-images.md)
* [Sets draaien](spin-sets.md)
* [Video](video.md)
* [Dynamic Media Assets leveren](delivering-dynamic-media-assets.md)
* [Assets beheren](managing-assets.md)
* [Snelle weergaven gebruiken om aangepaste pop-upvensters te maken](custom-pop-ups.md)

Zie ook [ Opstelling Dynamic Media ](administering-dynamic-media.md).

<!-- 

OBSOLETE UNTIL INTEGRATING SCENE7 TOPIC GETS A MAJOR UPDATE
>[!NOTE]
>
>To understand the differences between using Dynamic Media and integrating Dynamic Media Classic with AEM, see [Dynamic Media Classic integration versus Dynamic Media](/help/sites-cloud/administering/integrating-scene7.md#aem-scene-integration-versus-dynamic-media).

-->

## Dynamic Media ingeschakeld en Dynamic Media uitgeschakeld {#dynamic-media-on-versus-dynamic-media-off}

U kunt zien of Dynamic Media is ingeschakeld (ingeschakeld) door de volgende kenmerken:

* Dynamische uitvoeringen zijn beschikbaar wanneer u elementen downloadt of een voorvertoning weergeeft.
* Afbeeldingssets, centrifuges en gemengde mediasets zijn beschikbaar.
* PTIFF-uitvoeringen worden gemaakt.

Wanneer u op een afbeeldingselement klikt, is de weergave van het element anders en is Dynamic Media ingeschakeld. Dynamic Media gebruikt de HTML5-viewers op aanvraag.

### Dynamische uitvoeringen {#dynamic-renditions}

Dynamische uitvoeringen zoals voorinstellingen voor afbeeldingen en viewers (onder **[!UICONTROL Dynamic]** ) zijn beschikbaar wanneer Dynamic Media is ingeschakeld.

![ chlimage_1-358 ](assets/chlimage_1-358.png)

### Dynamic Media-afbeeldingensets, spins-sets, gemengde mediasets {#image-sets-spins-sets-mixed-media-sets}

Afbeeldingssets, centrifuges en gemengde mediasets zijn beschikbaar als Dynamic Media is ingeschakeld.

![ chlimage_1-359 ](assets/chlimage_1-359.png)

### PTIFF-uitvoeringen voor Dynamic Media {#ptiff-renditions}

Tot de elementen die geschikt zijn voor Dynamic Media behoren `pyramid.tiffs` .

![ chlimage_1-360 ](assets/chlimage_1-360.png)

### Weergave van Dynamic Media-elementen wijzigen {#asset-views-change}

Als Dynamic Media is ingeschakeld, kunt u in- en uitzoomen door op de knoppen `+` en `-` te klikken. U kunt ook selecteren om in bepaalde gebieden in te zoomen. Met Omkeren gaat u naar de oorspronkelijke versie en u kunt de afbeelding op het volledige scherm weergeven door op de diagonale pijlen te klikken. Dynamic Media ingeschakeld wordt als volgt weergegeven:

![ chlimage_1-361 ](assets/chlimage_1-361.png)

Met Dynamic Media uitgeschakeld kunt u in- en uitzoomen en terugkeren naar de oorspronkelijke grootte:

![ chlimage_1-362 ](assets/chlimage_1-362.png)
