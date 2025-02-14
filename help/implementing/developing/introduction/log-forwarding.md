---
title: Log Forwarding for AEM as a Cloud Service
description: Meer informatie over het doorsturen van logbestanden naar houtkapselaars in AEM as a Cloud Service
exl-id: 27cdf2e7-192d-4cb2-be7f-8991a72f606d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 9c258e2906c37ee9b91d2faa78f7dfdaa5956dc2
workflow-type: tm+mt
source-wordcount: '1985'
ht-degree: 0%

---

# Log doorsturen {#log-forwarding}

>[!NOTE]
>
>Het door:sturen van het logboek wordt nu gevormd op zelfbediende manier, verschillend van de erfenismethode, die het voorleggen van een kaartje van de Steun van de Adobe vereiste. Zie [ het Migreren ](#legacy-migration) sectie als uw logboek het door:sturen opstelling door Adobe was.

Klanten met een licentie bij een logboekleverancier of die een logproduct hosten, kunnen AEM logboeken (inclusief Apache/Dispatcher) en CDN-logboeken hebben die naar de gekoppelde logbestemming worden doorgestuurd. AEM as a Cloud Service ondersteunt de volgende logbestemmingen:

* Azure Blob Storage
* Datahond
* Elasticsearch of OpenSearch
* HTTPS
* Splunk

Het door:sturen van het logboek wordt gevormd op een zelfbediening manier door een configuratie in Git te verklaren, en kan via Cloud Manager config pijpleidingen worden opgesteld om, stadium, en de types van productiemilieu te ontwikkelen. Het configuratiedossier kan aan de Milieu&#39;s van de Snelle Ontwikkeling (RDEs) worden opgesteld gebruikend bevellijn tooling.

Er is een optie voor de logboeken van de AEM en van Apache/Dispatcher om door AEM geavanceerde voorzien van een netwerkinfrastructuur, zoals specifieke uitgang IP worden verpletterd.

Merk op dat de netwerkbandbreedte verbonden aan logboeken die naar de logboekbestemming worden verzonden als deel van het I/O gebruik van het Netwerk van uw organisatie worden beschouwd.

## Hoe dit artikel is georganiseerd {#how-organized}

Dit artikel is als volgt geordend:

* Opstelling - gemeenschappelijk voor alle registrerenbestemmingen
* Vervoer &amp; Geavanceerde Voorzien van een netwerk - de overweging zou aan netwerkopstelling moeten worden gegeven alvorens registrerenconfiguratie te creëren
* Logboekdoelconfiguraties - elke bestemming heeft een lichtjes verschillende indeling
* Indelingen voor logberichten - informatie over de indelingen van logberichten
* Het migreren van erfenislogboek door:sturen - hoe te zich van logboek door:sturen eerder opstelling door Adobe aan de zelf-serverbenadering te bewegen

## Instellen {#setup}

1. Maak een bestand met de naam `logForwarding.yaml` . Het zou meta-gegevens moeten bevatten, zoals die in het [ worden beschreven config pijpleidingsartikel ](/help/operations/config-pipeline.md#common-syntax) (**soort** zou aan `LogForwarding` moeten worden geplaatst en versie die aan &quot;1&quot;wordt geplaatst), met een configuratie gelijkend op het volgende (wij gebruiken Splunk als voorbeeld).

   ```yaml
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

1. Plaats het dossier ergens onder een top niveauomslag genoemd *config* of gelijkaardig, zoals die in [ wordt beschreven Gebruikend Pijpleidingen Config ](/help/operations/config-pipeline.md#folder-structure).

1. Voor milieutypes buiten RDE (die het hulpmiddel van de bevellijn gebruikt), creeer een gerichte plaatsing config pijpleiding in Cloud Manager, zoals die door [ wordt van verwijzingen voorzien deze sectie ](/help/operations/config-pipeline.md#creating-and-managing); merk op dat de Volledige pijpleidingen van de Stapel en de pijpleidingen van de Rij van het Web niet het configuratiedossier opstellen.

1. Implementeer de configuratie.

Tokens in de configuratie (zoals `${{SPLUNK_TOKEN}}` ) vertegenwoordigen geheimen, die niet in Git moeten worden opgeslagen. In plaats daarvan, verklaar hen als de Variabelen van het Milieu van Cloud Manager [ Geheime ](/help/operations/config-pipeline.md#secret-env-vars). Zorg ervoor om **allen** als dropdown waarde voor de Dienst Toegepaste gebied te selecteren, zodat kunnen de logboeken aan auteur door:sturen, publiceren, en voorproefrijen.

Het is mogelijk om verschillende waarden tussen CDN- logboeken en AEM (met inbegrip van Apache/Dispatcher) te plaatsen, door extra **cdn** en/of **a** blok na het **gebrek** blok te omvatten, waar de eigenschappen die in het **standaard** blok worden bepaald kunnen met voeten treden; slechts wordt het toegelaten bezit vereist. Een mogelijk gebruiksgeval zou kunnen zijn om een verschillende index van de Splunk voor CDN- logboeken te gebruiken, zoals het hieronder voorbeeld illustreert.

```yaml
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

```yaml
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

## Vervoer en geavanceerde netwerken {#transport-advancednetworking}

Sommige organisaties kiezen om te beperken welk verkeer door de registrerenbestemmingen kan worden ontvangen, anderen kunnen vereisen om havens buiten HTTPS (443) te gebruiken.  Als zo [ het Geavanceerde Voorzien van een netwerk ](/help/security/configuring-advanced-networking.md) zal moeten worden gevormd alvorens logboek het door:sturen configuratie op te stellen.

Gebruik de lijst hieronder om te zien wat de vereisten voor Geavanceerde die Voorzien van een netwerk en Logging configuratie zijn op of u haven 443 of niet gebruikt, en of u uw logboeken om van een vast IP adres nodig hebt te verschijnen.
<html>
<style>
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
  text-align: center;
}
</style>
<table>
  <tbody>
    <tr>
      <th>Doelpoort</th>
      <th>Verplichting voor Logs om van Vaste IP te verschijnen?</th>
      <th>Geavanceerde netwerken vereist</th>
      <th>LogForwarding.yaml Poortdefinitie vereist</th>
    </tr>
    <tr>
      <td rowspan="2">HTTPS (443)</td>
      <td>Nee</td>
      <td>Nee</td>
      <td>Nee</td>
    </tr>
    <tr>
      <td>Ja</td>
      <td>Ja, <a href="/help/security/configuring-advanced-networking.md#dedicated-egress-ip-address-dedicated-egress-ip-address"> Dedicated Egress </a></td>
      <td>Nee</td>
    <tr>
    <tr>
      <td rowspan="2">Niet-standaardpoort (bijvoorbeeld 8088)</td>
      <td>Nee</td>
      <td>Ja, <a href="/help/security/configuring-advanced-networking.md#flexible-port-egress-flexible-port-egress"> Flexibele uitgang </a></td>
      <td>Ja</td>
    </tr>
    <tr>
      <td>Ja</td>
      <td>Ja, <a href="/help/security/configuring-advanced-networking.md#dedicated-egress-ip-address-dedicated-egress-ip-address"> Dedicated Egress </a></td>
      <td>Ja</td>
  </tbody>
</table>
</html>

>[!NOTE]
>Of uw logboeken van één enkel IP adres verschijnen wordt bepaald door uw keus van de Geavanceerde configuratie van het Voorzien van een netwerk.  Om dit mogelijk te maken, moet speciale eieren worden gebruikt.
>
> De geavanceerde configuratie van het Voorzien van een netwerk is a [ proces in twee stappen ](/help/security/configuring-advanced-networking.md#configuring-and-enabling-advanced-networking-configuring-enabling) die enablement op programma en milieuniveau vereisen.

Voor AEM logboeken (met inbegrip van Apache/Dispatcher), als u [ Geavanceerd Voorzien van een netwerk ](/help/security/configuring-advanced-networking.md) hebt gevormd, kunt u het `aem.advancedNetworking` bezit gebruiken om hen van een Dedicated IP van de Eenheid of over VPN door:sturen.

In het onderstaande voorbeeld ziet u hoe u het aanmelden op een standaard HTTPS-poort met Advanced Networking configureert.

```yaml
kind: "LogForwarding"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      port: 443
      token: "${{SPLUNK_TOKEN}}"
      index: "aemaacs"
    aem:
      advancedNetworking: true
```

Voor CDN- logboeken, kunt u toestaan-lijst van de IP adressen, zoals die in [ wordt beschreven Snelle documentatie - Openbare IP Lijst ](https://www.fastly.com/documentation/reference/api/utils/public-ip-list/). Als die lijst van gedeelde IP adressen te groot is, denk na verzendend verkeer naar een https server of (niet-Adobe) Azure Blob Store waar de logica kan worden geschreven om de logboeken van bekende IP naar hun uiteindelijke bestemming te verzenden.

>[!NOTE]
>Het is niet mogelijk voor CDN- logboeken om van het zelfde IP adres te verschijnen dat uw AEM logboeken van verschijnen, is dit omdat de logboeken direct van Fastly en niet AEM Cloud Service worden verzonden.

## Logboekdoelconfiguratie {#logging-destinations}

De configuraties voor de gesteunde registrerenbestemmingen worden hieronder vermeld, samen met om het even welke specifieke overwegingen.

### Azure Blob Storage {#azureblob}

```yaml
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

Als de logboeken na eerder correct functionerende niet meer worden geleverd, controleert u of het door u gevormde SAS-token nog geldig is, aangezien het mogelijk verlopen is.

#### Azure Blob Storage CDN-logs {#azureblob-cdn}

Elke globaal gedistribueerde logbestandsserver produceert elke paar seconden een nieuw bestand onder de map `aemcdn` . Nadat het bestand is gemaakt, wordt het niet meer toegevoegd aan het bestand. Het filename formaat is JJJ-MM-DDThh :mm: ss.sss-uniqueid.log. Bijvoorbeeld, 2024-03-04T10 :00: 00.000-WnFWYN9BpOUs2aOVn4ee.log.

Zo kunt u op een bepaald tijdstip bijvoorbeeld:

```text
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
```

En dan 30 seconden later:

```text
aemcdn/
   2024-03-04T10:00:00.000-abc.log
   2024-03-04T10:00:00.000-def.log
   2024-03-04T10:00:30.000-ghi.log
   2024-03-04T10:00:30.000-jkl.log
   2024-03-04T10:00:30.000-mno.log
```

Elk bestand bevat meerdere logitems van de zoon, elk op een aparte regel. De formaten van de logboekingang worden beschreven onder [ het Registreren voor AEM as a Cloud Service ](/help/implementing/developing/introduction/logging.md), en elke logboekingang omvat ook de extra eigenschappen die in de [ hieronder sectie van de Formaten van de Ingang van het Logboek ](#log-formats) worden vermeld.

#### Azure Blob Storage AEM logs {#azureblob-aem}

AEM logbestanden (inclusief Apache/Dispatcher) worden weergegeven onder een map met de volgende naamgevingsconventie:

* amusement
* aemfout
* aemverzoek
* amemdispatcher
* aemhttpdaccess
* aemhttpderror

Onder elke map wordt één bestand gemaakt en toegevoegd. Klanten zijn verantwoordelijk voor de verwerking en het beheer van dit bestand, zodat het niet te groot wordt.

Zie de formaten van de logboekingang onder [ het Registreren voor AEM as a Cloud Service ](/help/implementing/developing/introduction/logging.md). De logboekingangen zullen ook de extra eigenschappen omvatten die in de [ hieronder sectie van de Formaten van het Ingang van het Logboek ](#log-formats) worden vermeld.

### Datahond {#datadog}

```yaml
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
* De eigenschap tags is optioneel
* Voor AEM logs wordt de gegevenshondenbrontag ingesteld op `aemaccess` , `aemerror` , `aemrequest` , `aemdispatcher` , `aemhttpdaccess` of `aemhttpderror`
* Voor CDN-logs wordt de gegevenshondenbrontag ingesteld op `aemcdn`
* De servicetag DataHond is ingesteld op `adobeaemcloud` , maar u kunt deze overschrijven in de sectie Tags
* Als uw innamepijpleiding de markeringen van Datadog gebruikt om de aangewezen index voor het door:sturen van logboeken te bepalen, verifieer dat deze markeringen correct in het Logboek door:sturen YAML- dossier worden gevormd. Het ontbreken van markeringen kan succesvolle logboekopname verhinderen als de pijpleiding van hen afhangt.

### Elasticsearch en OpenSearch {#elastic}

```yaml
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

* standaard is de poort 443 . Optioneel kan deze worden overschreven met de naam `port`
* Voor geloofsbrieven, zorg ervoor om plaatsingsgeloofsbrieven te gebruiken, eerder dan rekeningsgeloofsbrieven. Dit zijn de referenties die worden gegenereerd in een scherm dat op deze afbeelding lijkt:

![ Elastische plaatsingsgeloofsbrieven ](/help/implementing/developing/introduction/assets/ec-creds.png)

* Voor AEM logs wordt `index` ingesteld op een van `aemaccess` , `aemerror` , `aemrequest` , `aemdispatcher` , `aemhttpdaccess` of `aemhttpderror`
* Het facultatieve pijpleidingsbezit zou aan de naam van de Elasticsearch of OpenSearch moeten worden geplaatst ingest pijpleiding, die kan worden gevormd om de logboekingang aan de aangewezen index te leiden. Het type van Bewerker van de pijpleiding moet aan *manuscript* worden geplaatst en de manuscripttaal zou aan *pijnloos* moeten worden geplaatst. Hier is een fragment van het steekproefmanuscript om logboekingangen in een index zoals aemaccess_dev_26_06_2024 te leiden:

```text
def envType = ctx.aem_env_type != null ? ctx.aem_env_type : 'unknown';
def sourceType = ctx._index;
def date = new SimpleDateFormat('dd_MM_yyyy').format(new Date());
ctx._index = sourceType + "_" + envType + "_" + date;
```

### HTTPS {#https}

```yaml
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

Overwegingen:

* Het url koord moet **https://** omvatten of de bevestiging zal ontbreken.
* De URL kan een poort bevatten. Bijvoorbeeld `https://example.com:8443/aem_logs/aem` . Als er geen poort is opgenomen in de URL-tekenreeks, wordt poort 443 (de standaard-HTTPS-poort) gebruikt.

#### HTTPS CDN-logbestanden {#https-cdn}

De verzoeken van het Web (POSTs) zullen onophoudelijk, met een json nuttige lading worden verzonden die een serie van logboekingangen is, met het formaat van de logboekingang dat onder [ het Registreren voor AEM as a Cloud Service ](/help/implementing/developing/introduction/logging.md#cdn-log) wordt beschreven. De extra eigenschappen worden vermeld in de ](#log-formats) hieronder sectie van de Formaten van de Ingang van het Logboek van 0}.[

Er is ook een eigenschap met de naam `sourcetype` die is ingesteld op de waarde `aemcdn` .

>[!NOTE]
>
> Voordat de eerste CDN-logbestandvermelding wordt verzonden, moet uw HTTP-server een eenmalige controle uitvoeren: een aanvraag die naar het pad ``/.well-known/fastly/logging/challenge`` wordt verzonden, moet reageren met een asterisk ``*`` in de hoofdtekst en de statuscode van 200.

#### HTTPS-AEM {#https-aem}

Voor AEM logboeken (met inbegrip van apache/dispacher), zullen de Webverzoeken (POSTs) onophoudelijk, met een json nuttige lading worden verzonden die een serie van logboekingangen is, met de diverse formaten van de logboekingang zoals die onder [ het Registreren voor AEM as a Cloud Service ](/help/implementing/developing/introduction/logging.md) worden beschreven. De extra eigenschappen worden vermeld in de ](#log-formats) hieronder sectie van de Formaten van de Ingang van het Logboek van 0}.[

Er is ook een eigenschap met de naam `Source-Type` die op een van de volgende waarden is ingesteld:

* amusement
* aemfout
* aemverzoek
* amemdispatcher
* aemhttpdaccess
* aemhttpderror

### Splunk {#splunk}

```yaml
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
      index: "aemaacs"
```

Overwegingen:

* Standaard is de poort 443. Optioneel kan deze worden overschreven door een eigenschap met de naam `port` .
* Het sourcetype gebied zal één van de volgende waarden, afhankelijk van het specifieke logboek hebben: *aemaccess*, *aemerror*,
  *verzoek*, *aemdispatcher*, *aemhttpdaccess*, *aemhttpderror*, *aemcdn*
* Als vereiste IPs is gevoegd op lijst van gewenste personen en de logboeken nog niet worden geleverd, verifieer dat er geen firewallregels die de symbolische bevestiging van de Splunk afdwingen zijn. Voert snel een eerste validatiestap uit waarbij een ongeldig token voor segmentering opzettelijk wordt verzonden. Als uw firewall wordt geplaatst om verbindingen met ongeldige tokens van de Splunk te eindigen, zal het bevestigingsproces ontbreken, verhinderend snel logboeken aan uw instantie van de Splunk te leveren.

>[!NOTE]
>
> [ als het migreren ](#legacy-migration) van erfenisLogboek dat aan dit zelf-servermodel door:sturen, kunnen de `sourcetype` waarden van het gebied die naar uw Splunk index worden verzonden veranderd zijn, zo dienovereenkomstig aangepast.

<!--
### Sumo Logic {#sumologic}

   ```yaml
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

Zie [ het Registreren voor AEM as a Cloud Service ](/help/implementing/developing/introduction/logging.md) voor het formaat van elk respectieve logboektype (CDN logboeken, en AEM logboeken met inbegrip van Apache/Dispatcher).

Aangezien de logboeken van veelvoudige programma&#39;s en milieu&#39;s aan de zelfde registrerenbestemming kunnen door:sturen, naast de output die in het registrerenartikel wordt beschreven, zullen de volgende eigenschappen in elke logboekingang worden omvat:

* aem_env_id
* aem_env_type
* aem_program_id
* aem_tier

De eigenschappen kunnen bijvoorbeeld de volgende waarden hebben:

```text
aem_env_id: 1242
aem_env_type: dev
aem_program_id: 12314
aem_tier: author
```

## Migreren van verouderde logbestanden {#legacy-migration}

Voordat de configuratie Log Forwarding via een zelfservermodel werd bereikt, werd klanten gevraagd om supporttickets te openen, waar Adobe de integratie zou starten.

Klanten die op die manier door Adobe waren opgezet, zijn welkom om zich aan het model van het zelfdienen op hun gemak aan te passen. Er zijn verschillende redenen om deze overgang te maken:

* Er is een nieuwe omgeving (bijvoorbeeld een nieuwe dev-server of RDE) ingericht.
* Veranderingen in uw bestaand eindpunt of geloofsbrieven van de Splunk.
* De Adobe had opstelling uw logboek door:sturen alvorens de logboeken CDN beschikbaar waren en u zou CDN logboeken willen ontvangen.
* Een bewust besluit om zich proactief aan het zelf-servermodel aan te passen zodat heeft uw organisatie de kennis zelfs alvorens een tijdgevoelige verandering noodzakelijk is.

Wanneer klaar om te migreren, vorm eenvoudig het dossier YAML zoals die in de voorafgaande secties wordt beschreven. Gebruik de Cloud Manager config pijpleiding om aan elk van de milieu&#39;s op te stellen waar de configuratie zou moeten worden toegepast.

Het wordt geadviseerd, maar niet vereist, dat een configuratie aan alle milieu&#39;s wordt opgesteld zodat zij allen onder zelf-servercontrole zijn. Als niet, kunt u vergeten welke milieu&#39;s door Adobe tegenover die gevormd op een zelf-servermanier zijn gevormd.

>[!NOTE]
>De waarden van het veld `sourcetype` die naar uw verzonken index zijn verzonden, zijn mogelijk gewijzigd, dus pas de waarden dienovereenkomstig aan.
>
>Wanneer het Door:sturen van het Logboek aan een milieu wordt opgesteld dat eerder door de steun van de Adobe wordt gevormd, kunt u dubbele logboeken tot een paar uren ontvangen. Dit zal uiteindelijk automatisch worden opgelost.
