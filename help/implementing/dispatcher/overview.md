---
title: Overzicht van de inhoudsleveringsstroom
description: Meer informatie over de gegevensstroom voor de levering van inhoud en hoe u uw inhoud publiceert
exl-id: fe42fb9e-cdf4-43e1-b688-7cecf4124fa5
feature: Dispatcher
role: Admin
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Inhoudsleveringsstroom {#content-delivery}

Op de huidige pagina vindt u details over de inhoud van de publicatieservice in AEM as a Cloud Service. De levering van Publish-service-inhoud omvat:

* CDN
* AEM Dispatcher
* AEM uitgever

De gegevensstroom is als volgt:

1. De URL wordt toegevoegd in de browser
1. Verzoek dat aan CDN wordt gemaakt die in DNS aan dat domein wordt toegewezen
1. Als de inhoud volledig in het cachegeheugen is opgeslagen op CDN, geeft CDN deze aan de browser
1. Als de inhoud niet volledig in het cachegeheugen is opgeslagen, roept de CDN (reverse-proxy) de Dispatcher aan
1. Als de inhoud volledig in de cache van Dispatcher wordt geplaatst, geeft Dispatcher deze aan de CDN
1. Als de inhoud niet volledig in cache is geplaatst, roept de Dispatcher (reverse-proxy) de AEM aan om te publiceren
1. De inhoud wordt gerenderd door de browser, die de inhoud mogelijk ook in cache plaatst, afhankelijk van de kopteksten

Standaard verloopt het inhoudstype HTML/tekst na 300 seconden (5 minuten) op de Dispatcher-laag, een drempel die zowel door de Dispatcher-cache als door de CDN wordt nageleefd. Tijdens herplaatsingen van de publicatiedienst, wordt het geheime voorgeheugen van Dispatcher ontruimd en dan opgewarmd alvorens nieuwe publicatieknooppunten verkeer goedkeuren.

In de volgende secties vindt u meer informatie over de levering van inhoud:
* [CDN-configuratie](/help/implementing/dispatcher/cdn.md)
* [Caching](/help/implementing/dispatcher/caching.md)


De informatie over replicatie van de auteursdienst aan de publicatiedienst is beschikbaar [ hier ](/help/operations/replication.md).
