---
title: Dynamische media Assets leveren
description: Leer hoe u dynamische media-elementen op uw webpagina's kunt aanbieden via ingesloten video en afbeeldingen of door URL's aan uw webtoepassing te koppelen.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 4557b561-b3c4-4d6f-8044-2069bda41613
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Dynamische media Assets leveren{#delivering-dynamic-media-assets}

De manier waarop u uw dynamische media-elementen - zowel video als afbeeldingen - kunt leveren, is afhankelijk van de manier waarop uw website is geïmplementeerd.

Met Dynamische media hebt u verschillende opties:

* Als uw website wordt gehost op Adobe Experience Manager, wilt u de Dynamic Media-elementen rechtstreeks aan uw pagina toevoegen.
* Als uw website zich niet op Experience Manager bevindt, kunt u kiezen uit:

   * Uw video of afbeelding insluiten op uw website.
   * Koppel URL&#39;s aan uw webtoepassing. Gebruik koppelingen wanneer u een videospeler wilt leveren als een pop-up- of modaal venster.
   * Als uw plaats ontvankelijk is, kunt u [ geoptimaliseerde beelden ](/help/assets/dynamic-media/responsive-site.md) leveren.

>[!NOTE]
>
>Slimme beeldbewerking werkt met uw bestaande voorinstellingen voor afbeeldingen. Het gebruikt intelligentie bij de laatste milliseconde van levering om beelddossiergrootte verder te verminderen die op browser of netwerkverbindingssnelheid wordt gebaseerd. Zie [ Slimme Beeldvorming ](/help/assets/dynamic-media/imaging-faq.md) voor meer informatie.

Raadpleeg de volgende onderwerpen voor meer informatie:

* [Dynamische media Assets toevoegen aan webpagina&#39;s](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)
* [De video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/dynamic-media/embed-code.md)
* [Hotlink-beveiliging activeren in Dynamic Media](/help/assets/dynamic-media/hotlink-protection.md)
* [URL&#39;s koppelen aan uw webtoepassing](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)
* [Geoptimaliseerde afbeeldingen leveren voor een responsieve site](/help/assets/dynamic-media/responsive-site.md)
* [HTTP2 Levering van inhoud](/help/assets/dynamic-media/http2faq.md)
* [De CDN-cache ongeldig maken via Dynamic Media](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)
* [De CDN-cache ongeldig maken via Dynamic Media Classic](/help/assets/dynamic-media/invalidate-cdn-cache-dm-classic.md)
* [Regels gebruiken om URL&#39;s te transformeren](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md)

## HTTP/2-levering van Dynamic Media-elementen {#http-delivery-of-dynamic-media-assets}

Experience Manager ondersteunt nu de levering van alle Dynamic Media-inhoud (afbeeldingen en video) via HTTP/2. Dit wil zeggen dat er een gepubliceerde URL of insluitcode voor de afbeelding of video beschikbaar is om te worden geïntegreerd met elke toepassing die een gehoste element accepteert. Dat gepubliceerde element wordt vervolgens geleverd via het HTTP/2-protocol. Deze methode van levering verbetert de manier browsers en servers communiceren, die voor betere reactie en ladingstijden van al uw Dynamische activa van Media toestaan.

Meer leren, zie [ HTTP/2 Levering van Inhoud Veelgestelde Vragen ](/help/assets/dynamic-media/http2faq.md).
