---
title: Instelbare pushvalidatie voor een Edge Delivery-site
description: Ontdek hoe u pushvalidatie voor een Edge Delivery-site configureert voor efficiënte updates van inhoud en caching.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 7cded93c-325c-4a4b-8644-e6a2379d5179
source-git-commit: bb149cd43158bfd1ceb43b04cc536c8c8291f968
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Pushvalidatie instellen

De duwen ongeldigverklaring zorgt ervoor dat de inhoudsupdates die door auteurs worden gemaakt automatisch uit het beheerde Netwerk van de Levering van de Inhoud (CDN) worden verwijderd wanneer gepubliceerd. Zo zorgt u ervoor dat alleen de nieuwste inhoud wordt weergegeven.

Het systeem wist de inhoud die op specifieke URLs en geheim voorgeheugenmarkeringen of sleutels wordt gebaseerd, die ervoor zorgen dat verouderde versies worden gezuiverd.

Als u pushvalidatie wilt inschakelen, moeten specifieke eigenschappen worden toegevoegd aan het configuratiebestand van het project. Bijvoorbeeld een Microsoft Excel-werkmap met de naam `.helix/config.xlsx` in SharePoint of een Google-werkbladnaam `.helix/config` in Google Drive.

De volgende configuratieeigenschappen bepalen de naam van de productiegastheer en het type van beheer CDN:

| key | value | opmerking |
| --- | --- | --- |
| `cdn.prod.host` | `<Production Host>` | Hostnaam van de productiesite. Bijvoorbeeld `www.example.com` . |
| `cdn.prod.type` | beheerd |   |

Zodra de veranderingen in het configuratieblad worden aangebracht, moeten de gebruikers hen voorproef en activeren gebruikend het [ hulpmiddel van Sidekick ](https://www.aem.live/docs/sidekick) om de updates toe te passen.

Zie ook [ Ongeveer Edge Delivery om lijst in Cloud Manager ](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md#ed-todo-list) te doen.
