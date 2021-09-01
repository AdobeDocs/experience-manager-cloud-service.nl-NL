---
title: Schermen als veelgestelde vragen over Cloud Servicen
description: Deze pagina beschrijft de schermen als veelgestelde vragen over Cloud Servicen.
source-git-commit: 7a26bb50a8b95a2358912249e21daeb9c5e9c1a3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Schermen als veelgestelde vragen over Cloud Servicen {#screens-cloud-faqs}

De volgende sectie verstrekt antwoorden aan Veelgestelde Vragen (FAQs) met betrekking tot Schermen als project van de Cloud Service.

## Wat moet ik doen als AEM Screens-speler die schermen aanwijst als een Cloud Service, de aangepaste clientlibs niet plukt met /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css formaat?

AEM als Cloud Service verandert de lange geheim voorgeheugensleutels met elke plaatsing. AEM Screens genereert de offline caches wanneer de inhoud wordt gewijzigd, in plaats van wanneer Cloud Manager de implementatie uitvoert. Deze lange geheim voorgeheugensleutels in manifests zijn ongeldig, zodat kan de speler deze *clientlibs* niet downloaden.

Als u `longCacheKey="none"` in uw `clientlib`-map gebruikt, worden de lange cachemoetsen volledig verwijderd voor deze *clientlibs*.


## Wat moeten wij doen als off-line manifest niet alle middelen zoals bedoeld omvat? {#offline-manifest}

Offline caches worden gegenereerd met **bulk-offline-update-screens-service** servicegebruiker. Bepaalde paden die niet toegankelijk zijn voor `bulk-offline-update-screens-service`, leiden tot ontbrekende inhoud in offlinemanifesten.

In uw code, namelijk `ui.config or ui.apps`, creeer een configuratie OSGi in configuratiemap, met de volgende inhoud, en titel het dossier - noem als `org.apache.sling.jcr.repoinit.RepositoryInitializer-serviceusersandacls-content.config`

```
scripts=[
        "
        set principal ACL for bulk-offline-update-screens-service
                allow jcr:read on /content/mysite
                allow jcr:read on /apps/my-resources
        end
        "] 
```
