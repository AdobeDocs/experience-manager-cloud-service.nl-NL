---
title: Screens as a Cloud Service veelgestelde vragen
description: Op deze pagina worden as a Cloud Service vragen beschreven die vaak worden gesteld door Screens.
exl-id: 93f2144c-0e64-4012-88c6-86972d8cad9f
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Screens as a Cloud Service veelgestelde vragen {#screens-cloud-faqs}

In de volgende sectie worden antwoorden gegeven op veelgestelde vragen (FAQ&#39;s) over Screens as a Cloud Service-projecten.

## Wat moet ik doen als AEM Screens Player die naar Screens as a Cloud Service wijst, de aangepaste clientlibs niet plukt met de indeling /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css?

AEM as a Cloud Service wijzigt de lange cachetoetsen bij elke implementatie. AEM Screens genereert de offline caches wanneer de inhoud wordt gewijzigd, in plaats van wanneer de Cloud Manager de implementatie uitvoert. Deze lange geheim voorgeheugensleutels in manifests zijn ongeldig, zodat ontbreekt de speler om *clientlibs* te downloaden.

Het gebruiken `longCacheKey="none"` in uw `clientlib` omslag verwijdert de lange geheim voorgeheugensleutels volledig voor *clientlibs*.


## Wat zou ik moeten doen als off-line manifest niet alle middelen zoals bedoeld omvat? {#offline-manifest}

De off-line geheime voorgeheugens worden geproduceerd gebruikend **bulk-off-line-update-schermen-dienst** de dienstgebruiker. Bepaalde paden, die niet toegankelijk zijn voor `bulk-offline-update-screens-service` , leiden tot ontbrekende inhoud in offline manifesten.

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

## Welke afbeeldingsindelingen worden aanbevolen voor een naadloze uitvoering van afbeeldingen in een AEM Screens as a Cloud Service kanaal?{#screens-cloud-image-format}

Adobe raadt u aan afbeeldingen in de indeling `.png` en `.jpeg` in een AEM Screens as a Cloud Service kanaal te gebruiken voor de beste digitale handtekening.
De afbeeldingen in de indeling `*.tif` (Tagafbeeldingsbestandsindeling) worden niet ondersteund in AEM Screens as a Cloud Service. Als een kanaal deze afbeeldingsindeling heeft, wordt de afbeelding aan de afspeelzijde niet weergegeven.

## Wat moet ik doen als een Kanaal in de modus Ontwikkelaar (online) niet wordt weergegeven op AEM Screens Player?{#screens-cloud-online-channel-blank-iframe}

Adobe raadt u aan om AEM Screens-caching-mogelijkheden te gebruiken. Als u uw Channel echter in de modus Ontwikkelaar moet uitvoeren en de AEM Screens Player een leeg scherm weergeeft, controleert u de ontwikkelaarsgereedschappen van uw speler en zoekt u naar `X-Frame-Options` - of `frame-ancestors` -fouten. De resolutie is om de Dispatcher zodanig te configureren dat inhoud in iFrames kan worden uitgevoerd. Meestal werkt de volgende configuratie:

```
Header set Content-Security-Policy "frame-ancestors 'self' file: localhost:*;"
```

## Wat is het gebruik van de grens van de Registratiecode?

U kunt het gebruik van de registratiecode het beste beperken. Als een registratiecode gecompromitteerd is, maar een grens van 100 registraties heeft, dan kan de aanvaller slechts tot dat aantal, maar niet meer registreren. U kunt de gebruikslimiet altijd bijwerken nadat de registratiecode is gemaakt en enkele spelers van de klant al zijn geregistreerd. Als de klant ongebruikelijke registratieactiviteit voor een specifieke registratiecode opmerkt, kunnen zij de grens in real time verminderen terwijl zij onderzoeken. Zij kunnen het aantal verhogen als het een vals alarm was, zonder de reeds geregistreerde spelers te beïnvloeden.
