---
title: Log Forwarding for AEM as a Cloud Service
description: Leer over het door:sturen van logboeken aan Splunk en andere registrerenverkopers in AEM as a Cloud Service
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 4116f63c4a19b90849e4b55f0c10409530be7d3e
workflow-type: tm+mt
source-wordcount: '1278'
ht-degree: 0%

---

# Log doorsturen {#log-forwarding}

>[!NOTE]
>
>Deze eigenschap wordt nog niet vrijgegeven, en sommige registrerenbestemmingen kunnen niet op het tijdstip van versie beschikbaar zijn. In de tussentijd, kunt u een steunkaartje openen om logboeken aan **Splunk** door:sturen, zoals die in het [ registreren artikel ](/help/implementing/developing/introduction/logging.md) wordt beschreven.

Klanten die een vergunning voor een registrerenverkoper hebben of een registrerenproduct ontvangen kunnen AEM logboeken (met inbegrip van Apache/Dispatcher) en CDN- logboeken hebben die aan de bijbehorende registrerenbestemmingen door:sturen. AEM as a Cloud Service ondersteunt de volgende logbestemmingen:

* Azure Blob Storage
* DataDog
* Elasticsearch of OpenSearch
* HTTPS
* Splunk

Het door:sturen van het logboek wordt gevormd op een zelfbediening manier door een configuratie in Git te verklaren, en het op te stellen via de Pijpleiding van de Configuratie van Cloud Manager om, stadium, en de types van productiemilieu in productie (niet-zandbak) programma&#39;s te ontwikkelen.

Er is een optie voor de logboeken van de AEM en van Apache/Dispatcher om door AEM geavanceerde voorzien van een netwerkinfrastructuur, zoals specifieke uitgang IP worden verpletterd.

Merk op dat de netwerkbandbreedte verbonden aan logboeken die naar de logboekbestemming worden verzonden als deel van het I/O gebruik van het Netwerk van uw organisatie worden beschouwd.


## Hoe dit artikel is georganiseerd {#how-organized}

Dit artikel is als volgt geordend:

* Opstelling - gemeenschappelijk voor alle registrerenbestemmingen
* Logboekdoelconfiguraties - elke bestemming heeft een lichtjes verschillende indeling
* Indelingen voor logberichten - informatie over de indelingen van logberichten
* Geavanceerde netwerken - het verzenden van AEM en Apache/Dispatcher logboeken door een specifiek uitgang of door VPN


## Instellen {#setup}

1. Maak de volgende map- en bestandsstructuur in de map op hoofdniveau in uw project in Git:

   ```
   config/
        logForwarding.yaml
   ```

1. `logForwarding.yaml` moet metagegevens en een configuratie bevatten die vergelijkbaar is met de volgende indeling (we gebruiken Splunk als voorbeeld).

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

   De **soort** parameter zou aan `LogForwarding` de versie aan de schemaversie moeten worden geplaatst, die 1 is.

   Tokens in de configuratie (zoals `${{SPLUNK_TOKEN}}` ) vertegenwoordigen geheimen, die niet in Git moeten worden opgeslagen. In plaats daarvan, verklaar hen als de Variabelen van het Milieu van Cloud Manager ](/help/implementing/cloud-manager/environment-variables.md) van type **geheim**. [ Zorg ervoor om **allen** als dropdown waarde voor de Dienst Toegepaste gebied te selecteren, zodat kunnen de logboeken aan auteur door:sturen, publiceren, en voorproefrijen.

   Het is mogelijk om verschillende waarden tussen CDN- logboeken en AEM (met inbegrip van Apache/Dispatcher) te plaatsen, door extra **cdn** en/of **a** blok na het **gebrek** blok te omvatten, waar de eigenschappen die in het **standaard** blok worden bepaald kunnen met voeten treden; slechts wordt het toegelaten bezit vereist. Een mogelijk gebruiksgeval zou kunnen zijn om een verschillende index van de Splunk voor CDN- logboeken te gebruiken, zoals het hieronder voorbeeld illustreert.

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

1. Voor milieutypes buiten RDE (die momenteel niet wordt gesteund), creeer een gerichte plaatsing config pijpleiding in Cloud Manager.

   * [ zie het vormen productiepijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).
   * [ zie het vormen niet-productiepijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

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

![ Azure Blob SAS symbolische configuratie ](/help/implementing/developing/introduction/assets/azureblob-sas-token-config.png)

#### Azure Blob Storage CDN-logs {#azureblob-cdn}

Elke globaal gedistribueerde logbestandsserver produceert elke paar seconden een nieuw bestand onder de map `aemcdn` . Nadat het bestand is gemaakt, wordt het niet meer toegevoegd aan het bestand. Het filename formaat is JJJ-MM-DDThh :mm: ss.sss-uniqueid.log. Bijvoorbeeld, 2024-03-04T10 :00: 00.000-WnFWYN9BpOUs2aOVn4ee.log.

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

Elk bestand bevat meerdere logitems van de zoon, elk op een aparte regel. De formaten van de logboekingang worden beschreven in het [ registrerenartikel ](/help/implementing/developing/introduction/logging.md), en elke logboekingang omvat ook de extra eigenschappen die in de [ hieronder vermelde sectie van de Formaten van de Ingang van het Logboek ](#log-format) worden vermeld.

#### Azure Blob Storage AEM logs {#azureblob-aem}

AEM logbestanden (inclusief Apache/Dispatcher) worden weergegeven onder een map met de volgende naamgevingsconventie:

* amusement
* aemfout
* amemdispatcher
* httpdaccess
* httpderror

Onder elke map wordt één bestand gemaakt en toegevoegd. Klanten zijn verantwoordelijk voor de verwerking en het beheer van dit bestand, zodat het niet te groot wordt.

Zie de formaten van de logboekingang in het [ registrerend artikel ](/help/implementing/developing/introduction/logging.md). De logboekingangen zullen ook de extra eigenschappen omvatten die in de [ hieronder sectie van de Formaten van het Ingang van het Logboek ](#log-formats) worden vermeld.


### Datahond {#datadog}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  datadog:
    default:
      enabled: true       
      host: "http-intake.logs.datadoghq.eu"
      token: "${{DATADOG_API_KEY}}"
      tags:
         tag1: value1
         tag2: value2
      
```

Overwegingen:

* Maak een API-sleutel zonder integratie met een specifieke cloud provider.
* de eigenschap tags is optioneel


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
      pipeline: "ingest pipeline name"
```

Overwegingen:

* Voor geloofsbrieven, zorg ervoor om plaatsingsgeloofsbrieven te gebruiken, eerder dan rekeningsgeloofsbrieven. Dit zijn de referenties die worden gegenereerd in een scherm dat op deze afbeelding lijkt:

![ Elastische plaatsingsgeloofsbrieven ](/help/implementing/developing/introduction/assets/ec-creds.png)

* Het facultatieve pijpleidingsbezit zou aan de naam van de Elasticsearch of OpenSearch moeten worden geplaatst ingest pijpleiding, die kan worden gevormd om de logboekingang aan de aangewezen index te leiden. Het type van Bewerker van de pijpleiding moet aan *manuscript* worden geplaatst en de manuscripttaal zou aan *pijnloos* moeten worden geplaatst. Hier is een fragment van het steekproefmanuscript om logboekingangen in een index zoals aemaccess_dev_26_06_2024 te leiden:

```
def envType = ctx.aem_env_type != null ? ctx.aem_env_type : 'unknown';
def sourceType = ctx._index;
def date = new SimpleDateFormat('dd_MM_yyyy').format(new Date());
ctx._index = sourceType + "_" + envType + "_" + date;
```

### HTTPS {#https}

```
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  https:
    default:
      enabled: true
      url: "https://example.com/aem_logs/aem"
      authHeaderName: "X-AEMaaCS-Log-Forwarding-Token"
      authHeaderValue: "${{HTTPS_LOG_FORWARDING_TOKEN}}"
```

#### HTTPS CDN-logbestanden {#https-cdn}

De verzoeken van het Web (POSTs) zullen onophoudelijk, met een json nuttige lading worden verzonden die een serie van logboekingangen is, met het formaat van de logboekingang dat in het [ registrerenartikel ](/help/implementing/developing/introduction/logging.md#cdn-log) wordt beschreven. De extra eigenschappen worden vermeld in de ](#log-formats) hieronder sectie van de Formaten van de Ingang van het Logboek van 0}.[

Er is ook een eigenschap met de naam `sourcetype` die is ingesteld op de waarde `aemcdn` .

>[!NOTE]
>
> Voordat de eerste CDN-logbestandvermelding wordt verzonden, moet de HTTP-server een eenmalige controle uitvoeren: een aanvraag die naar het pad ``wellknownpath`` wordt verzonden, moet reageren met ``*`` .


#### HTTPS-AEM {#https-aem}

Voor AEM logboeken (met inbegrip van apache/dispacher), zullen de Webverzoeken (POSTs) onophoudelijk, met een json nuttige lading worden verzonden die een serie van logboekingangen is, met de diverse formaten van de logboekingang zoals die in het [ registreren artikel ](/help/implementing/developing/introduction/logging.md) worden beschreven. De extra eigenschappen worden vermeld in de ](#log-format) hieronder sectie van de Formaten van de Ingang van het Logboek van 0}.[

Er is ook een eigenschap met de naam `sourcetype` die op een van de volgende waarden is ingesteld:

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

Zie het algemene [ registrerenartikel ](/help/implementing/developing/introduction/logging.md) voor het formaat van elk respectieve logboektype (CDN logboeken, en AEM logboeken met inbegrip van Apache/Dispatcher).

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

Voor het logboek CDN, kunt u toestaan-lijst van de IP adressen, zoals die in [ wordt beschreven dit artikel ](https://www.fastly.com/documentation/reference/api/utils/public-ip-list/). Als die lijst van gedeelde IP adressen te groot is, denk na verzendend verkeer naar (niet-Adobe) Azure Blob Store waar de logica kan worden geschreven om de logboeken van specifieke IP naar hun uiteindelijke bestemming te verzenden.

Voor AEM logboeken (met inbegrip van Apache/Dispatcher), kunt u logboek vormen door:sturen om door [ geavanceerd voorzien van een netwerk ](/help/security/configuring-advanced-networking.md) te gaan. Zie de patronen voor de drie onderstaande geavanceerde netwerktypen, waarbij gebruik wordt gemaakt van een optionele parameter `port` , samen met de parameter `host` .

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
