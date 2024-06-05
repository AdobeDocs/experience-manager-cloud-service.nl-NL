---
title: Log doorsturen voor AEM as a Cloud Service
description: Leer over het door:sturen van logboeken aan Splunk en andere registrerenverkopers in AEM as a Cloud Service
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 0%

---

# Log doorsturen {#log-forwarding}

>[!NOTE]
>
>Deze eigenschap wordt nog niet vrijgegeven en sommige registrerenbestemmingen kunnen niet op het tijdstip van versie beschikbaar zijn. Ondertussen kunt u een ondersteuningsticket openen om logbestanden door te sturen naar **Splunk**, zoals beschreven in de [logboekartikel](/help/implementing/developing/introduction/logging.md).

Klanten die een vergunning voor een registrerenverkoper hebben of een registrerenproduct ontvangen kunnen AEM, Apache/Dispatcher, en CDN- logboeken hebben door:sturen aan de bijbehorende registrerenbestemmingen. AEM as a Cloud Service steunt de volgende registrerenbestemmingen:

* Azure Blob Storage
* DataDog
* Elasticsearch of OpenSearch
* HTTPS
* Splunk

Het door:sturen van het logboek wordt gevormd op een zelfbediening manier door een configuratie in Git te verklaren, en het op te stellen via de Pijpleiding van de Configuratie van de Manager van de Wolk om, stadium, en de types van productiemilieu in productie (niet-zandbak) programma&#39;s te ontwikkelen.

Merk op dat de netwerkbandbreedte verbonden aan logboeken die naar de logboekbestemming worden verzonden als deel van het I/O gebruik van het Netwerk van uw organisatie worden beschouwd.


## Hoe dit artikel is georganiseerd {#how-organized}

Dit artikel is als volgt geordend:

* Opstelling - gemeenschappelijk voor alle registrerenbestemmingen
* Logboekdoelconfiguraties - elke bestemming heeft een lichtjes verschillende indeling
* Het geavanceerde voorzien van een netwerk - verzendend AEM en Apache/Dispatcher logboeken door een specifiek uitgang of door VPN


## Instellen {#setup}

1. Maak de volgende map- en bestandsstructuur in de map op hoofdniveau in uw project in Git:

   ```
   config/
        logForwarding.yaml
   ```

1. logForwarding.yaml zou meta-gegevens en een configuratie gelijkend op het volgende formaat (wij gebruiken Splunk als voorbeeld) moeten bevatten.

   ```
   kind: "LogForwarding"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     splunk:
       default:
         enabled: true
         host: "splunk-host.example.com"
         token: "${{SPLUNK_TOKEN}}"
         index: "AEMaaCS"
   ```

   De **aardig** parameter zou aan LogForwarding moeten worden geplaatst de versie aan de schemaversie, die 1 is.

   Tokens in de configuratie (zoals `${{SPLUNK_TOKEN}}`) vertegenwoordigen geheimen, die niet in Git moeten worden opgeslagen. In plaats daarvan declareren als Cloud Manager  [Omgevingsvariabelen](/help/implementing/cloud-manager/environment-variables.md) van het type **geheim**. Zorg ervoor dat u **Alles** als de vervolgkeuzelijst voor het veld Service Applied, zodat de logbestanden naar de auteur-, publicatie- en voorvertoningslagen kunnen worden doorgestuurd.

   Het is mogelijk verschillende waarden in te stellen tussen cdn- en alle andere logbestanden (AEM- en apache-logbestanden) door een extra waarde op te nemen **cdn** en/of **aem** blok na de **default** blok, waarbij eigenschappen de eigenschappen kunnen overschrijven die in het dialoogvenster **default** blok; slechts wordt het toegelaten bezit vereist. Een mogelijk gebruiksgeval zou kunnen zijn om een verschillende index van de Splunk voor CDN- logboeken te gebruiken, zoals het hieronder voorbeeld illustreert.

   ```
      kind: "LogForwarding"
      version: "1"
      metadata:
        envTypes: ["dev"]
      data:
        splunk:
          default:
            enabled: true
            host: "splunk-host.example.com"
            token: "${{SPLUNK_TOKEN}}"
            index: "AEMaaCS"
          cdn:
            enabled: true
            token: "${{SPLUNK_TOKEN_CDN}}"
            index: "AEMaaCS_CDN"   
   ```

   Een ander scenario is of het door:sturen van de CDN- logboeken of alles (AEM en apache logboeken) onbruikbaar te maken. Als u bijvoorbeeld alleen de CDN-logboeken wilt doorsturen, kunt u het volgende configureren:

   ```
      kind: "LogForwarding"
      version: "1"
      metadata:
        envTypes: ["dev"]
      data:
        splunk:
          default:
            enabled: true
            host: "splunk-host.example.com"
            token: "${{SPLUNK_TOKEN}}"
            index: "AEMaaCS"
          aem:
            enabled: false
   ```

1. Voor milieutypes buiten RDE (die momenteel niet wordt gesteund), creeer een gerichte plaatsing config pijpleiding in de Manager van de Wolk.

   * [Zie productiepijpleidingen configureren](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).
   * [Zie niet-productiepijpleidingen configureren](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

## Logboekdoelconfiguratie {#logging-destinations}

De configuraties voor de gesteunde registrerenbestemmingen worden hieronder vermeld, samen met om het even welke specifieke overwegingen.

### Azure Blob Storage {#azureblob}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  azureBlob:
    default:
      enabled: true       
      storageAccountName: "example_acc"
      container: "aem_logs"
      sasToken: "${{AZURE_BLOB_SAS_TOKEN}}
      
```

Een SAS-token moet worden gebruikt voor verificatie. Het zou van de Gedeelde pagina van de toegangshandtekening, eerder dan op de Gedeelde pagina van het toegangstoken moeten worden gecreeerd, en zou met deze montages moeten worden gevormd:

* Toegestane services: klob moet zijn geselecteerd
* Toegestane bronnen: Object moet zijn geselecteerd
* Machtigingen toegestaan: Schrijven, Toevoegen, Maken moet zijn geselecteerd
* Een geldige begin- en vervaldatum/-tijd.

Hier is een schermafbeelding van een voorbeeld van een SAS-tokenconfiguratie:

![Azure Blob SAS-tokenconfiguratie](/help/implementing/developing/introduction/assets/azureblob-sas-token-config.png)


### Datahond {#datadog}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  dataDog:
    default:
      enabled: true       
      host: "http-intake.logs.datadoghq.eu"
      token: "${{DATADOG_API_KEY}}"
      
```

Overwegingen:

* Maak een API-sleutel zonder integratie met een specifieke cloud provider.


### Elasticsearch en OpenSearch {#elastic}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  elasticsearch:
    default:
      enabled: true
      host: "example.com"
      user: "${{ELASTICSEARCH_USER}}"
      password: "${{ELASTICSEARCH_PASSWORD}}"
```

Overwegingen:

* Voor geloofsbrieven, zorg ervoor om plaatsingsgeloofsbrieven te gebruiken, eerder dan rekeningsgeloofsbrieven. Dit zijn de referenties die worden gegenereerd in een scherm dat op deze afbeelding lijkt:

![Elastische implementatiereferenties](/help/implementing/developing/introduction/assets/ec-creds.png)

### HTTPS {#https}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  https:
    default:
      url: "https://example.com/aem_logs/aem"
      authHeaderName: "X-AEMaaCS-Log-Forwarding-Token"
      authHeaderValue: "${{HTTPS_LOG_FORWARDING_TOKEN}}"
```

### Splunk {#splunk}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      token: "${{SPLUNK_TOKEN}}"
      index: "AEMaaCS"
```

<!--
### Sumo Logic {#sumologic}

   ```
   kind: "LogForwarding"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     splunk:
       default:
         enabled: true
         host: "https://collectors.de.sumologic.com"
         uri: "/receiver/v1/http"
         privateKey: "${{SomeOtherToken}}"
   
   ```   
-->

## Geavanceerde netwerken {#advanced-networking}

Als u organisatorische vereisten hebt om verkeer aan uw registrerenbestemming te sluiten, kunt u logboek vormen door:sturen om door te gaan [geavanceerd netwerken](/help/security/configuring-advanced-networking.md). Zie de patronen voor de drie hieronder geavanceerde voorzien van een netwerktypes, die gebruik van facultatief maken `port` samen met de `host` parameter.

### Flexibele poortuitgang {#flex-port}

Als het logboekverkeer naar een haven buiten 443 (b.v., 8443 hieronder) gaat, vorm geavanceerd voorzien van een netwerk als zo:

```
{
    "portForwards": [
        {
            "name": "mylogging.service.logger.com",
            "portDest": 8443, # something other than 443
            "portOrig": 30443
        }    
    ]
}
```

en vorm het yaml dossier als zo:

```
kind: "LogForwarding"
version: "1"
data:
  splunk:
    default:
      host: "proxy.tunnel"
      token: "${{SomeToken}}"
      port: 30443
      index: "index_name"
```

### Speciale IP van de Afstuwing {#dedicated-egress}

Als het logboekverkeer uit een specifiek uitgang IP moet komen, vorm geavanceerde voorzien van een netwerk als zo:

```
{
    "portForwards": [
        {
            "name": "mylogging.service.com",
            "portDest": 443, # something other than 443
            "portOrig": 30443
        }    
    ]
}
```

en vorm het yaml dossier als zo:

```
kind: "LogForwarding"
version: "1"
data:
  splunk:
    default:
      host: "proxy.tunnel"
      token: "${{SomeToken}}"
      port: 30443
      index: "index_name"
```

### VPN {#vpn}

Als het logboekverkeer door VPN moet gaan, vorm geavanceerde voorzien van een netwerk als zo:

```
{
    "portForwards": [
        {
            "name": "mylogging.service.com",
            "portDest": 443, # something other than 443
            "portOrig": 30443
        }    
    ]
}
```

en vorm het yaml dossier als zo:

```
kind: "LogForwarding"
version: "1"
data:
  splunk:
    default:
      host: "mylogging.service.com"
      token: "${{SomeToken}}"
      port: 30443
      index: "index_name"
```
