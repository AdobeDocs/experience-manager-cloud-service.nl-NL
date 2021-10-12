---
title: as a Cloud Service veelgestelde vragen weergeven
description: Deze pagina beschrijft de as a Cloud Service veelgestelde vragen voor schermen.
exl-id: 93f2144c-0e64-4012-88c6-86972d8cad9f
source-git-commit: cf091056bdb96917a6d22bf1197d9b34ebbf9610
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# as a Cloud Service veelgestelde vragen weergeven {#screens-cloud-faqs}

De volgende sectie geeft antwoorden op Veelgestelde vragen (FAQs) met betrekking tot het as a Cloud Service project van Screens.

## Wat moet ik doen als AEM Screens Player die naar de as a Cloud Service schermen wijst, de aangepaste clientlibs niet plukt met de indeling /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css?

AEM as a Cloud Service verandert de lange geheim voorgeheugensleutels met elke plaatsing. AEM Screens genereert de offline caches wanneer de inhoud wordt gewijzigd, in plaats van wanneer Cloud Manager de implementatie uitvoert. Deze lange geheim voorgeheugensleutels in manifests zijn ongeldig, zodat kan de speler deze *clientlibs* niet downloaden.

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

## Welke afbeeldingsindelingen worden aanbevolen voor een naadloze uitvoering van afbeeldingen in een as a Cloud Service AEM Screens-kanaal?{#screens-cloud-image-format}

Het wordt aanbevolen om afbeeldingen in de notatie `.png` en `.jpeg` in een as a Cloud Service AEM Screens-kanaal te gebruiken voor de beste digitale signaalervaring.
Afbeeldingen in de indeling `*.tif` (bestandsindeling Tagafbeelding) worden niet ondersteund in as a Cloud Service AEM Screens. Als een kanaal deze afbeeldingsindeling heeft, wordt de afbeelding aan de afspeelzijde niet weergegeven.