---
title: Overzicht van de inhoudsleveringsstroom
description: Overzicht van de inhoudsleveringsstroom
exl-id: fe42fb9e-cdf4-43e1-b688-7cecf4124fa5
source-git-commit: f0edd0e3deeba89dcbd2dc1a07859138b24e2220
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 1%

---

# Workflow voor contentlevering {#content-delivery}

Op de huidige pagina vindt u details van de publicatieservice in AEM as a Cloud Service. De levering van de de dienstinhoud van de publicatie omvat:

* CDN
* AEM Dispatcher
* AEM uitgever

De gegevensstroom is als volgt:

1. De URL wordt toegevoegd in de browser
1. Verzoek dat aan CDN wordt gemaakt die in DNS aan dat domein wordt toegewezen
1. Als de inhoud volledig in het cachegeheugen is opgeslagen op CDN, geeft CDN deze aan de browser
1. Als de inhoud niet volledig in het cachegeheugen is opgeslagen, roept de CDN (reverse-proxy) de Dispatcher aan
1. Als de inhoud volledig in het cachegeheugen is opgeslagen op Dispatcher, wordt deze door Dispatcher aan de CDN verzonden
1. Als de inhoud niet volledig in het cachegeheugen is opgeslagen, roept de Dispatcher (reverse-proxy) de AEM uit om te publiceren
1. De inhoud wordt gerenderd door de browser, die de inhoud mogelijk ook in cache plaatst, afhankelijk van de kopteksten

Standaard is het inhoudstype HTML/tekst ingesteld op verlopen na 300 seconden (5 minuten) op de laag Dispatcher, een drempel die door de cache van de Dispatcher en de CDN wordt gerespecteerd. Tijdens herplaatsingen van de publicatiedienst, wordt het geheime voorgeheugen van de Verzender ontruimd en dan opgewarmd alvorens nieuwe publicatieknooppunten verkeer goedkeuren.

In de volgende secties vindt u meer informatie over de levering van inhoud:
* [CDN-configuratie](/help/implementing/dispatcher/cdn.md)
* [Caching](/help/implementing/dispatcher/caching.md)


Er is informatie beschikbaar over de replicatie van de auteurservice naar de publicatieservice [hier](/help/operations/replication.md).
