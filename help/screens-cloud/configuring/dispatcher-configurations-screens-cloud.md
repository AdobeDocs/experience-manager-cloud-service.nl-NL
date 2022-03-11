---
title: Dispatcher Configurations in as a Cloud Service schermen
description: Op deze pagina worden de configuraties van Dispatcher in as a Cloud Service schermen beschreven.
exl-id: cc04b480-9310-4975-a7c2-20682c567fa4
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---

# Dispatcher Configurations in as a Cloud Service schermen {#dispatcher-configurations-screens-cloud}

In deze sectie worden de configuraties van de verzender voor as a Cloud Service schermen beschreven.

## Filters en cacheregels toevoegen in Dispatcher voor as a Cloud Service schermimplementatie {#deployment}

De volgende filters en cachemels in verzenders toestaan voor de publicatie-instanties in as a Cloud Service schermen.

### AEM Screens-filters {#filters}

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

### Cacheregels {#cache-rules}

* Toevoegen `/statfileslevel "10"` tot `/cache` sectie in `publish_farm.any`/.

   >[!NOTE]
   >Deze geheim voorgeheugenregel steunt caching tot 10 niveaus van de geheim voorgeheugendocroot en maakt ongeldig wanneer de inhoud wordt gepubliceerd eerder dan het ongeldig maken van alles. U kunt dit niveau wijzigen op basis van de mate waarin de inhoudsstructuur is ingesteld.

* Voeg het volgende toe aan `/invalidate` sectie in `publish_farm.any`.

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* Voeg de volgende regels toe aan `/rules` sectie in `/cache` in publish_farm.any of in een bestand waarvan `publish_farm.any`.

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
