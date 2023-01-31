---
title: Dynamic Media-middelen leveren
description: Leer hoe u Dynamic Media-middelen kunt leveren.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 4557b561-b3c4-4d6f-8044-2069bda41613
source-git-commit: 35caac30887f17077d82f3370f1948e33d7f1530
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Dynamic Media-middelen leveren{#delivering-dynamic-media-assets}

Hoe u uw Dynamic Media-middelen kunt leveren - zowel video als afbeeldingen - hangt af van de manier waarop uw website is geïmplementeerd.

Met Dynamic Media hebt u verschillende opties:

* Als uw website op Adobe Experience Manager wordt gehost, wilt u de Dynamic Media-elementen rechtstreeks aan uw pagina toevoegen.
* Als uw website niet op Experience Manager is, kunt u kiezen uit:

   * Uw video of afbeelding insluiten op uw website.
   * Koppel URL&#39;s aan uw webtoepassing. Gebruik koppelingen wanneer u een videospeler wilt leveren als een pop-up- of modaal venster.
   * Als uw site reageert, kunt u [geoptimaliseerde afbeeldingen leveren](/help/assets/dynamic-media/responsive-site.md).

>[!NOTE]
>
>Slimme beeldbewerking werkt met uw bestaande voorinstellingen voor afbeeldingen. Het gebruikt intelligentie bij de laatste milliseconde van levering om beelddossiergrootte verder te verminderen die op browser of netwerkverbindingssnelheid wordt gebaseerd. Zie [Slimme afbeeldingen](/help/assets/dynamic-media/imaging-faq.md) voor meer informatie .

Raadpleeg de volgende onderwerpen voor meer informatie:

* [Dynamic Media-elementen toevoegen aan webpagina&#39;s](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)
* [De video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/dynamic-media/embed-code.md)
* [Hotlink-beveiliging activeren in Dynamic Media](/help/assets/dynamic-media/hotlink-protection.md)
* [URL&#39;s koppelen aan uw webtoepassing](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)
* [Geoptimaliseerde afbeeldingen leveren voor een responsieve site](/help/assets/dynamic-media/responsive-site.md)
* [HTTP2 Levering van inhoud](/help/assets/dynamic-media/http2faq.md)
* [De CDN-cache ongeldig maken via Dynamic Media](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)
* [De CDN-cache ongeldig maken via Dynamic Media Classic](/help/assets/dynamic-media/invalidate-cdn-cache-dm-classic.md)
* [Regels gebruiken om URL&#39;s te transformeren](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md)

## HTTP/2 levering van Dynamic Media-middelen {#http-delivery-of-dynamic-media-assets}

Experience Manager ondersteunt nu de levering van alle Dynamic Media-inhoud (afbeeldingen en video) via HTTP/2. Dit wil zeggen dat er een gepubliceerde URL of insluitcode voor de afbeelding of video beschikbaar is om te worden geïntegreerd met elke toepassing die een gehoste element accepteert. Dat gepubliceerde element wordt vervolgens geleverd via het HTTP/2-protocol. Deze leveringsmethode verbetert de manier waarop browsers en servers communiceren, waardoor u betere responstijd en laadtijden voor al uw Dynamic Media-middelen krijgt.

Zie voor meer informatie [HTTP/2 Levering van inhoud Veelgestelde Vragen](/help/assets/dynamic-media/http2faq.md).
