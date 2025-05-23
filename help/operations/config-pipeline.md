---
title: Config Pipelines gebruiken
description: Leer hoe u config pijpleidingen kunt gebruiken om verschillende configuraties in AEM as a Cloud Service zoals logboek op te stellen door:sturen montages, zuivert-verwante onderhoudstaken, en diverse configuraties CDN.
feature: Operations
role: Admin
exl-id: bd121d31-811f-400b-b3b8-04cdee5fe8fa
source-git-commit: 4c166193ec464bb66fe00ff648c2c449ab5b3eab
workflow-type: tm+mt
source-wordcount: '1024'
ht-degree: 0%

---

# Config Pipelines gebruiken {#config-pipelines}

Leer hoe u config pijpleidingen kunt gebruiken om verschillende configuraties in AEM as a Cloud Service zoals logboek op te stellen door:sturen montages, zuivert-verwante onderhoudstaken, en diverse configuraties CDN.

## Overzicht {#overview}

Een Cloud Manager config pijpleiding stelt configuratiedossiers (die in formaat YAML worden gecreeerd) aan een doelmilieu op. Een aantal eigenschappen in AEM as a Cloud Service kan op deze manier worden gevormd, met inbegrip van logboek het door:sturen, zuivert-verwante onderhoudstaken, en verscheidene eigenschappen CDN.

Config-pijpleidingen kunnen via Cloud Manager worden geïmplementeerd om omgevingstypen te ontwikkelen, te testen en te produceren. De configuratiedossiers kunnen aan Snelle Milieu&#39;s van de Ontwikkeling (RDEs) worden opgesteld gebruikend [ het hulpmiddel van de bevellijn van de bevellijn ](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline).

Deze volgende secties van dit document geven een overzicht van belangrijke informatie betreffende hoe config de pijpleidingen kunnen worden gebruikt en hoe de configuraties voor hen zouden moeten worden gestructureerd. Het beschrijft algemene concepten die over of allen of een ondergroep van de eigenschappen worden gedeeld die door config pijpleidingen worden gesteund.

* [ Gesteunde Configuraties ](#configurations) - een lijst van configuraties die met config pijpleidingen kunnen worden opgesteld
* [ Creërend en Leidend Pijpleidingen Config ](#creating-and-managing) - hoe te om een config pijpleiding tot stand te brengen.
* [ Gemeenschappelijke Syntaxis ](#common-syntax) - Syntaxis die over configuraties wordt gedeeld
* [ Structuur van de Omslag ](#folder-structure) - Beschrijft de structuur config pijpleidingen verwachten voor de configuraties
* [ Geheime omgevingsvariabelen ](#secret-env-vars) - Voorbeelden van het gebruiken van omgevingsvariabelen om geheimen in uw configuraties niet openbaar te maken

## Ondersteunde configuraties {#configurations}

De volgende lijst biedt een uitvoerige lijst van dergelijke configuraties met verbindingen aan specifieke documentatie die zijn verschillende configuratiesyntaxis en andere informatie beschrijft.

| Type | YAML `kind` Waarde | Beschrijving |
|---|---|---|
| [ Regels van de Filter van het Verkeer, met inbegrip van WAF ](/help/security/traffic-filter-rules-including-waf.md) | `CDN` | Declareer regels om kwaadwillig verkeer te blokkeren |
| [ Transformaties van het Verzoek ](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) | `CDN` | Declareer regels om de vorm van het verkeersverzoek om te zetten |
| [ Transformaties van de Reactie ](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) | `CDN` | Declareer regels om de vorm van de reactie voor een bepaald verzoek om te zetten |
| [ Server-kant richt ](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors) opnieuw | `CDN` | Declareer serveromleidingen van 301/302 stijl |
| [ de Selecteurs van de Oorsprong ](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) | `CDN` | Declareer regels om verkeer aan verschillende achtergronden, met inbegrip van toepassingen te leiden niet Adobe |
| [ CDN foutenpagina&#39;s ](/help/implementing/dispatcher/cdn-error-pages.md) | `CDN` | Overschrijf de standaardfoutpagina als de AEM-oorsprong niet kan worden bereikt. Hierbij wordt verwezen naar de locatie van zelfgehoste statische inhoud in het configuratiebestand |
| [ CDN zuiveren ](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) | `CDN` | Declareer de Leegmaken API-sleutels die worden gebruikt om de CDN op te lossen |
| [ Klantbeheerd het teken van HTTP CDN ](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#CDN-HTTP-value) | `CDN` | Declareer de waarde van de x-AEM-Edge-Sleutel nodig om Adobe CDN van een CDN van de Klant te roepen |
| [ Basisauthentificatie ](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#basic-auth) | `CDN` | Declareer de gebruikersnamen en de wachtwoorden voor een basisautwiedialoog die bepaalde URLs beschermen. |
| [ Taak van het Onderhoud van de Opruiming van de Versie ](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimaliseer de AEM-opslagplaats door regels te declareren over het tijdstip waarop versies van inhoud moeten worden gewist |
| [ Taak van het Onderhoud van de Aanzuivering van het Logboek van de Controle ](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimaliseer het AEM controlelogboek voor verhoogde prestaties door regels rond te verklaren wanneer het logboek zou moeten worden gezuiverd |
| [ Logboek door:sturen ](/help/implementing/developing/introduction/log-forwarding.md) | `LogForwarding` | Vorm de eindpunten en de geloofsbrieven voor het door:sturen van logboeken aan diverse bestemmingen, met inbegrip van Azure Blob Storage, Datadog, HTTPS, Elasticsearch, Splunk |
| [ registrerend een identiteitskaart van de Cliënt ](/help/implementing/developing/open-api-based-apis.md) | `API` | Bereik Adobe Developer Console API-projecten voor een specifieke AEM-omgeving door de client-id te registreren. Dit is nodig voor gebruik van op OpenAPI gebaseerde API&#39;s die verificatie vereisen |

## Config-pijplijnen maken en beheren {#creating-and-managing}

Voor informatie over om pijpleidingen tot stand te brengen en te vormen, zie [ CI/CD Pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline).

Wanneer het creëren van een config pijpleiding in Cloud Manager, ben zeker om a **gerichte Plaatsing** eerder dan **Volledige Code van de Stapel** te selecteren wanneer het vormen van de pijpleiding.

Zoals vroeger genoteerd, wordt de configuratie voor RDEs opgesteld gebruikend [ het hulpmiddel van de bevellijn ](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline) eerder dan een pijpleiding.


## Algemene syntaxis {#common-syntax}

Elk configuratiebestand begint met eigenschappen die op het volgende voorbeeldfragment lijken:

```yaml
  kind: "LogForwarding"
  version: "1"
  metadata:
    envTypes: ["dev"]
```

| Eigenschap | Beschrijving | Standaard |
|---|---|---|
| `kind` | Een koord dat bepaalt welk type van configuratie, zoals logboek het door:sturen, de regels van de verkeersfilter, of verzoektransformaties | Vereist, geen standaard |
| `version` | Een tekenreeks die de schemaversie vertegenwoordigt | Vereist, geen standaard |
| `envTypes` | Deze array van tekenreeksen is een onderliggende eigenschap van het knooppunt `metadata` . Mogelijke waarden zijn dev, stage, prod of een willekeurige combinatie en het bepaalt voor welke omgevingstypen de configuratie wordt verwerkt. Als de array bijvoorbeeld alleen `dev` bevat, wordt de configuratie niet geladen in werkgebied- of prodomgevingen, zelfs niet als de configuratie daar wordt geïmplementeerd. | Alle omgevingstypen (dev, stage, prod) |

U kunt het hulpprogramma `yq` gebruiken om de YAML-opmaak van uw configuratiebestand lokaal te valideren (bijvoorbeeld `yq cdn.yaml` ).

## Mapstructuur {#folder-structure}

Een map met de naam `/config` of een vergelijkbare map moet zich boven aan de structuur bevinden, met nog een YAML-bestand ergens in een boomstructuur eronder.

Bijvoorbeeld:

```text
/config
  cdn.yaml
```

of

```text
/config
  /dev
    cdn.yaml
```

De mapnamen en bestandsnamen onder `/config` zijn willekeurig. Het YAML-bestand moet echter een geldige [`kind` eigenschapswaarde ](#configurations) bevatten.

Configuraties worden doorgaans in alle omgevingen geïmplementeerd. Als alle bezitswaarden voor elk milieu identiek zijn, zal één enkel dossier YAML voldoende zijn. Het is echter gebruikelijk dat eigenschapswaarden verschillen tussen omgevingen, bijvoorbeeld tijdens het testen van een lagere omgeving.

In de volgende secties ziet u enkele strategieën voor het structureren van uw bestanden.

### Eén configuratiebestand voor alle omgevingen {#single-file}

De bestandsstructuur lijkt op het volgende:

```text
/config
  cdn.yaml
  logForwarding.yaml
```

Gebruik deze structuur wanneer de zelfde configuratie voor alle milieu&#39;s en voor alle types van configuratie (CDN, logboek het door:sturen, etc.) voldoende is. In dit scenario zou de array-eigenschap `envTypes` alle omgevingstypen bevatten.

```yaml
   kind: "cdn"
   version: "1"
   metadata:
     envTypes: ["dev", "stage", "prod"]
```

Gebruikend geheim-type milieuvariabelen, is het mogelijk voor [ geheime eigenschappen ](#secret-env-vars) per milieu te variëren, zoals die door de `${{SPLUNK_TOKEN}}` verwijzing wordt geïllustreerd

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

### Een afzonderlijk bestand per omgevingstype {#file-per-env}

De bestandsstructuur lijkt op het volgende:

```text
/config
  cdn-dev.yaml
  cdn-stage.yaml
  cdn-prod.yaml
  logForwarding-dev.yaml
  logForwarding-stage.yaml
  logForwarding-prod.yaml
```

Gebruik deze structuur wanneer er verschillen in eigenschapswaarden kunnen zijn. In de bestanden wordt verwacht dat de arraywaarde `envTypes` overeenkomt met het achtervoegsel, bijvoorbeeld
`cdn-dev.yaml` en `logForwarding-dev.yaml` met de waarde `["dev"]` , `cdn-stage.yaml` en `logForwarding-stage.yaml` met de waarde `["stage"]` , enzovoort.

### Een map per omgeving {#folder-per-env}

In deze strategie, is er een afzonderlijke `config` omslag per milieu, met een afzonderlijke pijpleiding die in Cloud Manager voor elk wordt verklaard.

Deze benadering is vooral nuttig als u veelvoudige ontwikkelomgevingen hebt, waar elk unieke bezitswaarden heeft.

De bestandsstructuur lijkt op het volgende:

```text
/config/dev1
  cdn.yaml
  logForwarding.yaml
/config/dev2
  cdn.yaml
  logForwarding.yaml
/config/prod  
  cdn.yaml
  logForwarding.yaml
```

Een variatie van deze benadering is het handhaven van een afzonderlijke tak per milieu.

## Geheime omgevingsvariabelen {#secret-env-vars}

Zo dat de gevoelige informatie niet in broncontrole moet worden opgeslagen, steunen de configuratiedossiers de milieu variabelen van Cloud Manager van type **geheim**. Voor sommige configuraties, met inbegrip van logdoor:sturen, zijn de geheime omgevingsvariabelen verplicht voor bepaalde eigenschappen.

Het onderstaande fragment is een voorbeeld van hoe de geheime omgevingsvariabele `${{SPLUNK_TOKEN}}` in de configuratie wordt gebruikt.

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

Gelieve te zien het document [ de Variabelen van het Milieu van Cloud Manager ](/help/implementing/cloud-manager/environment-variables.md) voor details op hoe te om omgevingsvariabelen te gebruiken.
