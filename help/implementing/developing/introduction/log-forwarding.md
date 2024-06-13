---
title: Log doorsturen voor AEM as a Cloud Service
description: Leer over het door:sturen van logboeken aan Splunk en andere registrerenverkopers in AEM as a Cloud Service
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: e007f2e3713d334787446305872020367169e6a2
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 0%

---

# Log doorsturen {#log-forwarding}

>[!NOTE]
>
>Deze eigenschap wordt nog niet vrijgegeven, en sommige registrerenbestemmingen kunnen niet op het tijdstip van versie beschikbaar zijn. Ondertussen kunt u een ondersteuningsticket openen om logbestanden door te sturen naar **Splunk**, zoals beschreven in de [logboekartikel](/help/implementing/developing/introduction/logging.md).

Klanten die een vergunning voor een registrerenverkoper hebben of een registrerenproduct ontvangen kunnen AEM logboeken (met inbegrip van Apache/Dispatcher) en CDN- logboeken hebben die aan de bijbehorende registrerenbestemmingen door:sturen. AEM as a Cloud Service steunt de volgende registrerenbestemmingen:

* Azure Blob Storage
* DataDog
* Elasticsearch of OpenSearch
* HTTPS
* Splunk

Het door:sturen van het logboek wordt gevormd op een zelfbediening manier door een configuratie in Git te verklaren, en het op te stellen via de Pijpleiding van de Configuratie van de Manager van de Wolk om, stadium, en de types van productiemilieu in productie (niet-zandbak) programma&#39;s te ontwikkelen.

Er is een optie voor de logboeken van de AEM en van Apache/van de Verzender om door AEM geavanceerde voorzien van een netwerkinfrastructuur, zoals specifieke uitgang IP worden verpletterd.

Merk op dat de netwerkbandbreedte verbonden aan logboeken die naar de logboekbestemming worden verzonden als deel van het I/O gebruik van het Netwerk van uw organisatie worden beschouwd.


## Hoe dit artikel is georganiseerd {#how-organized}

Dit artikel is als volgt geordend:

* Opstelling - gemeenschappelijk voor alle registrerenbestemmingen
* Logboekdoelconfiguraties - elke bestemming heeft een lichtjes verschillende indeling
* Indelingen voor logberichten - informatie over de indelingen van logberichten
* Het geavanceerde voorzien van een netwerk - verzendend AEM en Apache/Dispatcher logboeken door een specifiek uitgang of door VPN


## Instellen {#setup}

1. Maak de volgende map- en bestandsstructuur in de map op hoofdniveau in uw project in Git:

   ```
   config/
        logForwarding.yaml
   ```

1. `logForwarding.yaml` moeten metagegevens en een configuratie bevatten die lijkt op de volgende indeling (wij gebruiken Splunk als voorbeeld).

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

   De **aardig** parameter moet worden ingesteld op `LogForwarding` de versie zou aan de schemaversie moeten worden geplaatst, die 1 is.

   Tokens in de configuratie (zoals `${{SPLUNK_TOKEN}}`) vertegenwoordigen geheimen, die niet in Git moeten worden opgeslagen. In plaats daarvan declareren als Cloud Manager  [Omgevingsvariabelen](/help/implementing/cloud-manager/environment-variables.md) van het type **geheim**. Zorg ervoor dat u **Alles** als de vervolgkeuzelijst voor het veld Service Applied, zodat de logbestanden naar de auteur-, publicatie- en voorvertoningslagen kunnen worden doorgestuurd.

   Het is mogelijk verschillende waarden in te stellen tussen CDN-logbestanden en AEM-logbestanden (inclusief Apache/Dispatcher) door een extra waarde op te nemen **cdn** en/of **aem** blok na de **default** blok, waarbij eigenschappen de eigenschappen kunnen overschrijven die in het dialoogvenster **default** blok; slechts wordt het toegelaten bezit vereist. Een mogelijk gebruiksgeval zou kunnen zijn om een verschillende index van de Splunk voor CDN- logboeken te gebruiken, zoals het hieronder voorbeeld illustreert.

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

   Een ander scenario moet of het door:sturen van de logboeken onbruikbaar maken CDN of AEM (met inbegrip van Apache/Dispatcher). Als u bijvoorbeeld alleen de CDN-logboeken wilt doorsturen, kunt u het volgende configureren:

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

* Toegestane services: klob moet zijn geselecteerd.
* Toegestane bronnen: Object moet zijn geselecteerd.
* Machtigingen toegestaan: Schrijven, Toevoegen, Maken moet zijn geselecteerd.
* Een geldige begin- en vervaldatum/-tijd.

Hier is een schermafbeelding van een voorbeeld van een SAS-tokenconfiguratie:

![Azure Blob SAS-tokenconfiguratie](/help/implementing/developing/introduction/assets/azureblob-sas-token-config.png)

#### Azure Blob Storage CDN-logs {#azureblob-cdn}

Elke globaal gedistribueerde logboekserver produceert een nieuw bestand elke paar seconden, onder de `aemcdn` map. Nadat het bestand is gemaakt, wordt het niet meer toegevoegd aan het bestand. De bestandsindeling is YYY-MM-DDThh:mm:ss.sss-uniqueid.log. Bijvoorbeeld 2024-03-04T10:00:00.000-WnFWYN9BpOUs2aOVn4ee.log.

Zo kunt u op een bepaald tijdstip bijvoorbeeld:

```
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
```

En dan 30 seconden later:

```
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
   2024-03-04T10:00:30.000-ghi.log
   2024-03-04T10:00:30.000-jkl.log
   2024-03-04T10:00:30.000-mno.log
```

Elk bestand bevat meerdere logitems van de zoon, elk op een aparte regel. De notaties voor logberichten worden beschreven in het dialoogvenster [logboekartikel](/help/implementing/developing/introduction/logging.md)en elke logbestandvermelding bevat ook de aanvullende eigenschappen die in de [Indelingen voor logbestandvermelding](#log-format) hieronder.

#### Azure Blob Storage AEM logs {#azureblob-aem}

AEM logbestanden (inclusief Apache/Dispatcher) worden weergegeven onder een map met de volgende naamgevingsconventie:

* amusement
* aemfout
* amemdispatcher
* httpdaccess
* httpderror

Onder elke map wordt één bestand gemaakt en toegevoegd. Klanten zijn verantwoordelijk voor de verwerking en het beheer van dit bestand, zodat het niet te groot wordt.

Zie de notaties voor logberichten in het dialoogvenster [logboekartikel](/help/implementing/developing/introduction/logging.md). De logbestandvermeldingen bevatten ook de aanvullende eigenschappen die in het dialoogvenster [Indelingen voor logbestandvermelding](#log-formats) hieronder.


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

#### HTTPS CDN-logbestanden {#https-cdn}

De verzoeken van het Web (POSTs) zullen onophoudelijk, met een json nuttige lading worden verzonden die een serie van logboekingangen is, met het formaat van de logboekingang dat in wordt beschreven [logboekartikel](/help/implementing/developing/introduction/logging.md#cdn-log). Aanvullende eigenschappen worden vermeld in de [Indelingen voor logbestandvermelding](#log-formats) hieronder.

Er is ook een eigenschap met de naam `sourcetype`, die is ingesteld op de waarde `aemcdn`.

>[!NOTE]
>
> Voordat de eerste CDN-logbestandvermelding wordt verzonden, moet uw HTTP-server een eenmalige controle met succes uitvoeren: een aanvraag die naar het pad wordt verzonden ``wellknownpath`` moet reageren met ``*``.


#### HTTPS-AEM {#https-aem}

Voor AEM logbestanden (inclusief apache/dispacher) worden webaanvragen (POST&#39;s) continu verzonden, met een JSON-lading die een array van logitems is, met de verschillende logbestandsindelingen zoals beschreven in het dialoogvenster [logboekartikel](/help/implementing/developing/introduction/logging.md). Aanvullende eigenschappen worden vermeld in de [Indelingen voor logbestandvermelding](#log-format) hieronder.

Er is ook een eigenschap met de naam `sourcetype`, die op een van de volgende waarden wordt ingesteld:

* amusement
* aemfout
* amemdispatcher
* httpdaccess
* httpderror

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

## Indelingen voor logbestandvermelding {#log-formats}

Zie het algemene gedeelte [logboekartikel](/help/implementing/developing/introduction/logging.md) voor de indeling van elk respectieve logbestandstype (CDN-logboeken en AEM, inclusief Apache/Dispatcher).

Aangezien de logboeken van veelvoudige programma&#39;s en milieu&#39;s aan de zelfde registrerenbestemming kunnen door:sturen, naast de output die in het registrerenartikel wordt beschreven, zullen de volgende eigenschappen in elke logboekingang worden omvat:

* aem_env_id
* aem_env_type
* aem_program_id
* aem_tier

De eigenschappen kunnen bijvoorbeeld de volgende waarden hebben:

```
aem_env_id: 1242
aem_env_type: dev
aem_program_id: 12314
aem_tier: author
```

## Geavanceerde netwerken {#advanced-networking}

>[!NOTE]
>
>Deze functie is nog niet gereed voor vroege gebruikers.


Sommige organisaties verkiezen om te beperken welk verkeer door de registrerenbestemmingen kan worden ontvangen.

Voor het CDN-logboek kunt u de IP-adressen toestaan en weergeven, zoals wordt beschreven in [dit artikel](https://www.fastly.com/documentation/reference/api/utils/public-ip-list/). Als die lijst van gedeelde IP adressen te groot is, denk na verzendend verkeer naar (niet-Adobe) Azure Blob Store waar de logica kan worden geschreven om de logboeken van specifieke IP naar hun uiteindelijke bestemming te verzenden.

Voor AEM logboeken (met inbegrip van Apache/Dispatcher), kunt u logboek vormen door:sturen om te gaan [geavanceerd netwerken](/help/security/configuring-advanced-networking.md). Zie de patronen voor de drie hieronder geavanceerde voorzien van een netwerktypes, die gebruik van facultatief maken `port` samen met de `host` parameter.

### Flexibele poortuitgang {#flex-port}

Als het logboekverkeer naar een haven buiten 443 (b.v., 8443 hieronder) gaat, vorm geavanceerd voorzien van een netwerk als zo:

```
{
    "portForwards": [
        {
            "name": "splunk-host.example.com",
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
      host: "${{AEM_PROXY_HOST}}"
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
            "name": "splunk-host.example.com",
            "portDest": 443, 
            "portOrig": 30443
        }    
    ]
}
```

en vorm het yaml dossier als zo:

```
      
kind: "LogForwarding"
version: "1"
   metadata:
     envTypes: ["dev"]
data:
  splunk:
     default:
       enabled: true
       index: "index_name" 
       token: "${{SPLUNK_TOKEN}}"  
     aem:
       enabled: true
       host: "${{AEM_PROXY_HOST}}"
       port: 30443       
     cdn:
       enabled: true
       host: "splunk-host.example.com"
       port: 443    
```

### VPN {#vpn}

Als het logboekverkeer door VPN moet gaan, vorm geavanceerde voorzien van een netwerk als zo:

```
{
    "portForwards": [
        {
            "name": "splunk-host.example.com",
            "portDest": 443,
            "portOrig": 30443
        }    
    ]
}

kind: "LogForwarding"
version: "1"
   metadata:
     envTypes: ["dev"]
data:
  splunk:
     default:
       enabled: true
       index: "index_name" 
       token: "${{SPLUNK_TOKEN}}"  
     aem:
       enabled: true
       host: "${{AEM_PROXY_HOST}}"
       port: 30443       
     cdn:
       enabled: true
       host: "splunk-host.example.com"
       port: 443     
```
