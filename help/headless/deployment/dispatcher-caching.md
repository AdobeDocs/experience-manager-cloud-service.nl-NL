---
title: GraphQL Persisted Queries - caching inschakelen in Dispatcher
description: De Dispatcher is een caching- en beveiligingslaag voor Adobe Experience Manager Publish-omgevingen. U kunt caching voor Verlengde Vragen in AEM Zwaartepunt toelaten.
feature: Headless, Dispatcher, GraphQL API
exl-id: 30a97e56-6699-41c4-a4eb-fc6236667f8f
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# GraphQL Persisted Queries - caching inschakelen in Dispatcher {#graphql-persisted-queries-enabling-caching-dispatcher}

>[!CAUTION]
>
>Als caching in de Dispatcher wordt toegelaten dan [CORS-filter](/help/headless/deployment/cross-origin-resource-sharing.md) is niet nodig, zodat die sectie kan worden genegeerd.

Caching van persisted query&#39;s wordt niet standaard ingeschakeld in de Dispatcher. De standaard enablement is niet mogelijk aangezien de klanten die CORS (het Delen van het Middel van de Cross-Origin) met veelvoudige oorsprong gebruiken hun configuratie van de Verzender moeten herzien en misschien bijwerken.

>[!NOTE]
>
>De Dispatcher slaat de `Vary` header.
>
>Caching van andere CORS-verwante kopballen kan in de Dispatcher worden toegelaten, maar zou ontoereikend kunnen zijn wanneer er veelvoudige CORS oorsprong zijn.

>[!NOTE]
>
>Voor gedetailleerde documentatie over de Dispatcher raadpleegt u de [Handleiding voor verzending](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html).

## Het in cache plaatsen van doorlopende query&#39;s inschakelen {#enable-caching-persisted-queries}

Om het in cache plaatsen van persistente query&#39;s in te schakelen, definieert u de variabele Dispatcher `CACHE_GRAPHQL_PERSISTED_QUERIES`:

1. De variabele toevoegen aan het Dispatcher-bestand `global.vars`:

   ```xml
   Define CACHE_GRAPHQL_PERSISTED_QUERIES
   ```

>[!NOTE]
>
>Om individuele `ETag` koptekstberekening op de gepresteerde vragen in de cache (voor *elk* reactie die uniek is) `FileETag Digest` het plaatsen moet in de configuratie virtuele gastheer van de verzender configuratie worden gebruikt (als het niet reeds bestaat):
>
>```xml
><Directory />    
>   ...    
>   FileETag Digest
></Directory> 
>```

>[!NOTE]
>
>Als u zich aan de [Vereisten van de verzender voor documenten die in cache kunnen worden geplaatst](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/troubleshooting/dispatcher-faq.html#how-does-the-dispatcher-return-documents%3F), voegt de Dispatcher het achtervoegsel toe `.json` aan alle persisted query-URL&#39;s, zodat het resultaat in de cache kan worden opgeslagen.
>
>Dit achtervoegsel wordt toegevoegd door herschrijft regel, zodra het voortbestaan vraagcaching wordt toegelaten.

## CORS-configuratie in de Dispatcher {#cors-configuration-in-dispatcher}

Klanten die CORS-verzoeken gebruiken, moeten mogelijk hun CORS-configuratie in de Dispatcher controleren en bijwerken.

* De `Origin` header mag niet worden doorgegeven aan AEM publish via Dispatcher:
   * Controleer de `clientheaders.any` bestand.
* In plaats daarvan, moeten de verzoeken CORS voor toegestane oorsprong op het niveau van de Verzender worden geëvalueerd. Deze benadering zorgt er ook voor dat aan CORS gerelateerde koppen in alle gevallen correct worden ingesteld op één plaats.
   * Een dergelijke configuratie moet worden toegevoegd aan de `vhost` bestand. Hieronder wordt een voorbeeldconfiguratie gegeven; voor de eenvoud is alleen het gedeelte met betrekking tot CORS opgenomen. U kunt deze aanpassen voor uw specifieke gebruiksgevallen.

  ```xml
  <VirtualHost *:80>
     ServerName "publish"
  
     # ...
  
     <IfModule mod_headers.c>
         Header add X-Vhost "publish"
  
          ################## Start of the CORS specific configuration ##################
  
          SetEnvIfExpr "req_novary('Origin') == ''"  CORSType=none CORSProcessing=false
          SetEnvIfExpr "req_novary('Origin') != ''"  CORSType=cors CORSProcessing=true CORSTrusted=false
  
          SetEnvIfExpr "req_novary('Access-Control-Request-Method') == '' && %{REQUEST_METHOD} == 'OPTIONS' && req_novary('Origin') != ''  " CORSType=invalidpreflight CORSProcessing=false
          SetEnvIfExpr "req_novary('Access-Control-Request-Method') != '' && %{REQUEST_METHOD} == 'OPTIONS' && req_novary('Origin') != ''  " CORSType=preflight CORSProcessing=true CORSTrusted=false
          SetEnvIfExpr "req_novary('Origin') -strcmatch 'https://%{HTTP_HOST}*'"  CORSType=samedomain CORSProcessing=false
  
          # For requests that require CORS processing, check if the Origin can be trusted
          SetEnvIfExpr "%{HTTP_HOST} =~ /(.*)/ " ParsedHost=$1
  
          ################## Adapt the regex to match CORS origin for your environment
          SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*.your-domain.tld(:\d+)?$)#" CORSTrusted=true
  
          # Extract the Origin header 
          SetEnvIfNoCase ^Origin$ ^https://(.*)$ CORSTrustedOrigin=https://$1
  
          # Flush If already set
          Header unset Access-Control-Allow-Origin
          Header unset Access-Control-Allow-Credentials
  
          # Trusted
          Header always set Access-Control-Allow-Credentials "true" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Origin "%{CORSTrustedOrigin}e" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Methods "GET" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Max-Age 1800 "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Headers "Origin, Accept, X-Requested-With, Content-Type, Access-Control-Request-Method, Access-Control-Request-Headers" "expr=reqenv('CORSTrusted') == 'true'"
  
          # Non-CORS or Not Trusted
          Header unset Access-Control-Allow-Credentials "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Allow-Origin "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Allow-Methods "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Max-Age "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
  
          # Always vary on origin, even if its not there.
          Header merge Vary Origin
  
          # CORS - send 204 for CORS requests which are not trusted
          RewriteCond expr "reqenv('CORSProcessing') == 'true' && reqenv('CORSTrusted') == 'false'"
          RewriteRule "^(.*)" - [R=204,L]
  
          ################## End of the CORS specific configuration ##################
  
     </IfModule>
  
     <Directory />
  
         # ...
  
     </Directory>
  
     # ...
  
  </VirtualHost>
  ```
