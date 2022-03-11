---
title: Overzicht van de inhoudsleveringsstroom
description: Overzicht van de inhoudsleveringsstroom
exl-id: fe42fb9e-cdf4-43e1-b688-7cecf4124fa5
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 1%

---

# Workflow voor contentlevering {#content-delivery}

Op de huidige pagina vindt u details van de publicatieservice in AEM as a Cloud Service. De levering van de de dienstinhoud van de publicatie omvat:

* CDN
* AEM
* AEM publiceren

De gegevensstroom is als volgt:

1. De URL wordt toegevoegd in de browser
1. Verzoek dat aan CDN wordt gemaakt die in DNS aan dat domein wordt toegewezen
1. Als de inhoud volledig in het cachegeheugen is opgeslagen op CDN, geeft CDN deze aan de browser
1. Als de inhoud niet volledig in het cachegeheugen is opgeslagen, roept de CDN (reverse-proxy) de dispatcher aan
1. Als de inhoud volledig in het cachegeheugen is opgeslagen op de verzender, wordt deze naar de CDN verzonden
1. Als de inhoud niet volledig in het cachegeheugen is opgeslagen, roept de verzender (reverse-proxy) de AEM aan om te publiceren
1. De inhoud wordt gerenderd door de browser, die de inhoud mogelijk ook in cache plaatst, afhankelijk van de kopteksten

Standaard is het inhoudstype HTML/tekst ingesteld op verlopen na 300 seconden (5 minuten) op de verzendingslaag, een drempel die zowel door de verzendercache als door de CDN wordt nageleefd. Tijdens herplaatsingen van de publicatiedienst, wordt het verzendechergeheime voorgeheugen ontruimd en daarna opgewarmd alvorens nieuwe publicatieknooppunten verkeer goedkeuren.

De secties hieronder verstrekken meer detail over inhoudslevering, met inbegrip van configuratie CDN en caching.

Er is informatie beschikbaar over de replicatie van de auteurservice naar de publicatieservice [hier](/help/operations/replication.md).
