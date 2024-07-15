---
title: Hoe kunnen we problemen met betrekking tot caching oplossen voor AEM Forms as a Cloud Service?
description: Problemen met caching oplossen voor AEM Forms as a Cloud Service.
contentOwner: khsingh
feature: Adaptive Forms
role: User
exl-id: eae44a6f-25b4-46e9-b38b-5cec57b6772c
source-git-commit: 0b693cb51a96011235fa87a5899426c6b0c2509a
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Caching prestaties {#caching-performance}

U kunt enkele van de volgende problemen tegenkomen tijdens het configureren of gebruiken van Adaptive Forms-cache in een Cloud Service-omgeving:

## Sommige Adaptive Forms-afbeeldingen of video&#39;s worden niet automatisch ongeldig gemaakt in de Dispatcher-cache {#images-videos-not-invalidated}

U kunt afbeeldingen of video&#39;s vanuit de middelenbrowser selecteren en toevoegen aan een adaptief formulier. Wanneer deze afbeeldingen worden bewerkt in de Assets-editor, wordt de versie in de cache van een adaptief formulier met dergelijke afbeeldingen niet ongeldig gemaakt. In het adaptieve formulier worden nog steeds oudere afbeeldingen weergegeven.

Als u dit probleem wilt oplossen, maakt u na publicatie van de afbeeldingen en video de publicatie van de Adaptive Forms die naar deze elementen verwijzen, expliciet ongedaan en publiceert u deze.

## Bepaalde adaptieve Forms die inhoudsfragmenten of ervaringsfragmenten bevatten, worden niet automatisch ongeldig gemaakt vanuit de Dispatcher-cache {#content-fragments-experience-fragments-not-invalidated}

U kunt een inhoudsfragment of een ervaringsfragment toevoegen aan een adaptief formulier. Wanneer deze fragmenten onafhankelijk worden bewerkt en gepubliceerd, wordt de versie in de cache van een adaptief formulier met deze fragmenten niet ongeldig gemaakt. In het adaptieve formulier worden nog steeds oudere fragmenten weergegeven.

Als u dit probleem wilt oplossen, maakt u na publicatie van het bijgewerkte inhoudsfragment of Experience Fragment de publicatie van de Adaptive Forms die deze elementen gebruikt, expliciet ongedaan en publiceert u deze.

## Alleen de eerste instantie van Adaptive Forms wordt in cache geplaatst {#only-first-instance-cached}

Wanneer de URL van het adaptieve formulier geen lokalisatiegegevens bevat en de optie Landinstelling browser gebruiken in configuratiebeheer is ingeschakeld, wordt een gelokaliseerde versie van het adaptieve formulier verzonden en wordt op basis van het eerste verzoek (landinstelling browser aangevraagd) een instantie van het adaptieve formulier in de cache geplaatst en aan elke volgende gebruiker bezorgd.

Voer de volgende stappen uit om het probleem op te lossen:

1. Open uw project van de Experience Manager.
1. Open de `dispatcher/scr/conf.d/rewrites/rewrite.rules` voor bewerking.
1. Open het `conf.d/httpd-dispatcher.conf` -configuratiebestand of een ander configuratiebestand dat is geconfigureerd om tijdens de runtime te laden.
1. Voeg de volgende code toe aan het bestand en sla deze op. Dit is een voorbeeldcode die u kunt aanpassen aan uw omgeving.

```shellscript
    # Handle actual URL convention (just pass through)
    RewriteRule "^/content/forms/af/(.*)[.](.*).html$" "/content/forms/af/$1.$2.html" [PT]
    
    # Handle selector-based redirection based on browser language
    <VirtualHost *:80>
            # Handle actual URL convention (just pass through)
    RewriteRule "^/content/forms/af/(.*)[.](.*).html$" "/content/forms/af/$1.$2.html" [PT]

    # Handle selector based redirection basded on browser language
    # The Rewrite Condition is looking for the Accept-Language header and if found takes the first two characters which most likely are the desired language selector.
    RewriteCond %{HTTP:Accept-Language} ^(..).*$ [NC]
    RewriteRule "^/content/forms/af/(.*).html$" "/content/forms/af/$1.%1.html" [R]
    RewriteRule "^/content/forms/af/(.*).html$" "/content/forms/af/$1.%1.html" [R]
```

## CDN-caching werkt niet meer na 300 seconden {#cdn-caching-stops-working-after-300-seconds}

CDN-caching werkt niet meer na 300 seconden en alle aanvragen om CDN in cache te plaatsen worden omgeleid naar Dispatcher.

Stel de pagina-header in op 0 om het probleem op te lossen:

1. Een bestand maken bij `src\conf.d\available_vhosts`

1. Het volgende toevoegen aan het bestand om de paginakoptekst in te stellen

   ```shellscript
       <IfModule mod_headers.c>
               Header add X-Vhost "publish"
               Header set age 0
       </IfModule>
   ```

1. Sla het bestand op en sluit het.
1. Wijzig de zachte verbinding voor `src\conf.d\enabled_vhosts\default.vhost` om aan nieuw dossier te richten.
