---
title: Push Invalidation instellen
description: Leer over hoe te om dupbevestiging voor de bouw van uw eigen productieCDN te vormen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
source-git-commit: 3941b7f97d434946a3cb796633f306b89e68c0a4
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# Pushvalidatie instellen

De duwen ongeldigverklaring zorgt ervoor dat de inhoudsupdates die door auteurs worden gemaakt automatisch uit het beheerde Netwerk van de Levering van de Inhoud (CDN) worden verwijderd wanneer gepubliceerd, zodat slechts de recentste inhoud wordt gediend.

Het systeem wist de inhoud die op specifieke URLs en geheim voorgeheugenmarkeringen of sleutels wordt gebaseerd, die ervoor zorgen dat verouderde versies worden gezuiverd.

Als u pushvalidatie wilt inschakelen, moeten specifieke eigenschappen worden toegevoegd aan het configuratiebestand van het project. Bijvoorbeeld een Microsoft Excel-werkmap met de naam `.helix/config.xlsx` in SharePoint of een Google-werkbladnaam `.helix/config` in Google Drive.

De volgende configuratieeigenschappen bepalen de naam van de productiegastheer en het type van beheer CDN:

| key | value | opmerking |
| --- | --- | --- |
| `cdn.prod.host` | `<Production Host>` | Hostnaam van de productiesite. Bijvoorbeeld `www.example.com` . |
| `cdn.prod.type` | beheerd |   |

Zodra de veranderingen in het configuratieblad worden aangebracht, moeten de gebruikers voorproef en hen activeren gebruikend het [ hulpmiddel van de Sidekick ](/help/edge/docs/sidekick.md) om de updates toe te passen.
