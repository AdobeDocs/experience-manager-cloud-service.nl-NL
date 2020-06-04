---
title: Overzicht van de inhoudsleveringsstroom
description: Overzicht van de inhoudsleveringsstroom
translation-type: tm+mt
source-git-commit: 0080ace746f4a7212180d2404b356176d5f2d72c
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---


# Inhoudsleveringsstroom {#content-delivery}

Op de huidige pagina vindt u details van de inhoud van de publicatieservice in AEM als een Cloud Service. De levering van de de dienstinhoud van de publicatie omvat:

* CDN
* AEM-verzender
* AEM-publicatie

De gegevensstroom is als volgt:

1. De URL wordt toegevoegd in de browser
1. Verzoek dat aan CDN wordt gemaakt die in DNS aan dat domein wordt toegewezen
1. Als de inhoud volledig in het cachegeheugen is opgeslagen op CDN, geeft CDN deze aan de browser
1. Als de inhoud niet volledig in het cachegeheugen is opgeslagen, roept de CDN (reverse-proxy) de dispatcher aan
1. Als de inhoud volledig in het cachegeheugen is opgeslagen op de verzender, wordt deze naar de CDN verzonden
1. Als de inhoud niet volledig in het cachegeheugen is opgeslagen, roept de verzender (reverse-proxy) de AEM-publicatie aan
1. De inhoud wordt gerenderd door de browser, die de inhoud mogelijk ook in cache plaatst, afhankelijk van de kopteksten

Standaard verloopt het inhoudstype HTML/tekst na 300 seconden (5 minuten) op de verzendingslaag, een drempel die zowel door de verzendercache als door de CDN wordt nageleefd. Tijdens herplaatsingen van de publicatiedienst, wordt het verzendechergeheime voorgeheugen ontruimd en daarna opgewarmd alvorens nieuwe publicatieknooppunten verkeer goedkeuren.

De secties hieronder verstrekken meer detail over inhoudslevering, met inbegrip van configuratie CDN en caching.

Informatie over replicatie van de auteursdienst aan de publicatieservice is [hier](/help/operations/replication.md)beschikbaar.
