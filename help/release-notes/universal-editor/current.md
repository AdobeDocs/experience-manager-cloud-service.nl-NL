---
title: Opmerkingen bij de release van Universal Editor 2054.01.16
description: Dit zijn de releaseopmerkingen voor de release 2025.01.16 van de Universal Editor.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 14bc45917f56ecf358278848e7e830afb1fedccd
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# Opmerkingen bij de release van Universal Editor 2025.01.16 {#release-notes}

Dit zijn de releaseopmerkingen voor de release van 16 januari 2025 van de Universal Editor.

>[!TIP]
>
>Voor de huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service, gelieve te zien [ deze pagina.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Nieuwe functies {#what-is-new}

* **Verdringing van de Bibliotheek CORS &lt; 3.0.0** - om toekomstige verenigbaarheid te verzekeren en veiligheid te verbeteren, steunt de Universele Redacteur nu exclusief versie 3.0.0 of hoger van
  `@Adobe Express/universal-editor-cors` -bibliotheek.
   * De bibliotheek wordt nu alleen via [`universal-editor-service.adobe.io/cors.js` geleverd.](http://universal-editor-service.adobe.io/cors.js)
   * Gebruikers krijgen een melding van een veroudering te zien wanneer ze een pagina openen die oudere versies van de CORS-bibliotheek gebruikt en hen vragen om bij te werken.
* **Punt van de Uitbreiding voor het Bestaan van de Pagina** - [ Een nieuw uitbreidingspunt ](/help/implementing/universal-editor/customizing.md#extending) is geïntroduceerd voor uitbreidingen om in de zijspoor van de Universele het landen pagina van de Redacteur te verschijnen.
   * Ontwikkelaars kunnen nu opgeven of extensies van toepassing zijn op de editor, de bestemmingspagina of beide, en bieden meer mogelijkheden voor aanpassen en gebruiken.

## Overige verbeteringen {#other-improvements}

* **Vaste ongeldige URLs in Recente punten op de het landen pagina** - een kwesties werd opgelost waar URLs in de &quot;Recenten&quot;lijst op de Universele het landen pagina van de Redacteur werd getoond werd gebroken.
* **Synchronisatie van het Thema in Verenigde Shell** - De Universele Redacteur synchroniseert nu dynamisch het thema met de Verenigde montages van Shell van het systeem en past automatisch tussen lichte en donkere wijzen aan.
   * Dit zorgt voor een consistente visuele weergave aan de microvoorkanten, inclusief fragment- en assetselectoren.
