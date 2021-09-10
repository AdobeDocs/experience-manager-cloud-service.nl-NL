---
title: Configuraties van Dispatcher in rasters als Cloud Service
description: Deze pagina beschrijft Dispatcher Configurations in Screens als Cloud Service.
source-git-commit: b00856e1be8842c4e9fa6ed4ada9129926c73ef5
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Configuraties van Dispatcher in rasters als Cloud Service{#dispatcher-configurations-screens-cloud}

In deze sectie worden de configuraties van de verzender voor rasters beschreven als een Cloud Service.

## Dispatcher Configurations voor schermen als Cloud Service-implementatie {#deployment}

De volgende filters en cachemijnen in verzenders toestaan voor de publicatie-instanties in rasters als Cloud Service.

### Filters {#filters}

## AEM Screens-filters

```
## # Content Configurations
/0200 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
#/0201 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you're using experience-fragments
## add any other formats required for your project here
/0202 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" }
/0203 { /type "allow" /method 'GET' /url "/screens/channels.json" }
## # Enable clientlibs proxy servlet
/0210 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

## Cacheregels {#cache-rules}

* Voeg `/statfileslevel "10"` aan `/cache` sectie in `publish_farm.any` toe.

   >[!NOTE]
   >Dit steunt caching tot 10 niveaus van cachedocroot en maakt ongeldig wanneer de inhoud wordt gepubliceerd eerder dan alles ongeldig. U kunt dit niveau wijzigen op basis van de diepte van de inhoudsstructuur.

* Voeg het volgende toe aan `/invalidate` sectie in `publish_farm.any`.

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* Voeg de volgende regels aan `/rules` sectie in `/cache` in publish_farm.any of in een dossier toe dat van `publish_farm.any` inbegrepen is.

   ```
   ## Allow Dispatcher Cache for Screens channels
    /0002
        {
        /glob "/content/screens/*.html"
        /type "allow"
            }
   
   ## Allow Dispatcher Cache for Screens offline manifests
   
   /0003
       {
       /glob "/content/screens/*.manifest.json"
       /type "allow"
       }
   
   ## Allow Dispatcher Cache for Assets
   /0004
       {
       /glob "/content/dam/*"
       /type "allow"
       }
   
   ## Deny Screens Channels json
   /0005
       {
       /glob "/screens/channels.json"
       /type "deny"
       }
   ```
