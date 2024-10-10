---
title: Config Pipelines gebruiken
description: Leer hoe u config pijpleidingen kunt gebruiken om verschillende configuraties AEM as a Cloud Service zoals logboek op te stellen door:sturen montages, zuivert-verwante onderhoudstaken, en diverse configuraties CDN.
feature: Operations
role: Admin
exl-id: bd121d31-811f-400b-b3b8-04cdee5fe8fa
source-git-commit: 3d0abce117cf94d7bf521e78be2ec019f216aa08
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 0%

---

# Config Pipelines gebruiken {#config-pipelines}

Leer hoe u config pijpleidingen kunt gebruiken om verschillende configuraties AEM as a Cloud Service zoals logboek op te stellen door:sturen montages, zuivert-verwante onderhoudstaken, en diverse configuraties CDN.

## Overzicht {#overview}

Een Cloud Manager config pijpleiding stelt configuratiedossiers (die in formaat YAML worden gecreeerd) aan een doelmilieu op. Een aantal eigenschappen in AEM as a Cloud Service kan op deze manier worden gevormd, met inbegrip van logboek het door:sturen, zuivert-verwante onderhoudstaken, en verscheidene eigenschappen CDN.

Config Pipelines kunnen via Cloud Manager worden geïmplementeerd om omgevingstypen in productieprogramma&#39;s (zonder sandbox) op te zetten, te ontwikkelen en te produceren. RDE&#39;s worden niet ondersteund.

Deze volgende secties van dit document geven een overzicht van belangrijke informatie betreffende hoe de Pijpleidingen Config kunnen worden gebruikt en hoe de configuraties voor hen zouden moeten worden gestructureerd. Het beschrijft algemene concepten die over of allen of een ondergroep van de eigenschappen worden gedeeld die door config pijpleidingen worden gesteund.

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
| [ Cliënt-kant richt ](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) | `CDN` | Declareer 301/302-stijl cliënt-zijomleidingen |
| [ de Selecteurs van de Oorsprong ](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) | `CDN` | Verklaar regels om verkeer aan verschillende achtergronden, met inbegrip van niet Adobe toepassingen te leiden |
| [ CDN foutenpagina&#39;s ](/help/implementing/dispatcher/cdn-error-pages.md) | `CDN` | Overschrijf de standaardfoutenpagina als AEM oorsprong niet kan worden bereikt, verwijzend de plaats van zelf-ontvangen statische inhoud in het configuratiedossier |
| [ CDN zuiveren ](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) | `CDN` | Declareer de Leegmaken API-sleutels die worden gebruikt om de CDN op te lossen |
| [ Klantbeheerd het teken van HTTP CDN ](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#CDN-HTTP-value) | `CDN` | Declareer de waarde van x-AEM-Edge-Sleutel nodig om de Adobe CDN van een Klant CDN te roepen |
| [ Basisauthentificatie ](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#basic-auth) | `CDN` | Declareer de gebruikersnamen en de wachtwoorden voor een basisautwaldialoog die bepaalde URLs beschermen [ (beschikbaar aan vroege adopters slechts) ](/help/release-notes/release-notes-cloud/release-notes-current.md#foundation-early-adopter) |
| [ Taak van het Onderhoud van de Opruiming van de Versie ](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimaliseer de AEM opslagplaats door regels te declareren rond het tijdstip waarop versies van inhoud moeten worden gewist |
| [ Taak van het Onderhoud van de Aanzuivering van het Logboek van de Controle ](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimaliseer het AEM controlelogboek voor verhoogde prestaties door regels rond te verklaren wanneer de logboeken zouden moeten worden gezuiverd |
| [ Logboek door:sturen ](/help/implementing/developing/introduction/log-forwarding.md) | `LogForwarding` | Nog niet beschikbaar - vorm de eindpunten en de geloofsbrieven voor het door:sturen van logboeken aan diverse bestemmingen (b.v., Splunk, Datadog, HTTPS) |

## Config-pijplijnen maken en beheren {#creating-and-managing}

Voor informatie over om pijpleidingen tot stand te brengen en te vormen, te zien gelieve het document [ CI/CD Pijpleidingen.](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline)

Wanneer het creëren van een Pijpleiding Config in Cloud Manager, ben zeker om a **gerichte Plaatsing** eerder dan **Volledige Code van de Stapel** te selecteren wanneer het vormen van de pijpleiding.

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
| `kind` | Een koord dat bepaalt welk type van configuratie, bijvoorbeeld logboek het door:sturen, de regels van de verkeersfilter, of verzoektransformaties | Vereist, geen standaard |
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

De mapnamen en bestandsnamen onder `/config` zijn willekeurig. Het YAML-bestand moet echter een geldige waarde voor de eigenschap [`kind` bevatten.](#configurations)

Configuraties worden doorgaans in alle omgevingen geïmplementeerd. Als alle bezitswaarden voor elk milieu identiek zijn, zal één enkel dossier YAML voldoende zijn. Het is echter gebruikelijk dat eigenschapswaarden verschillen tussen omgevingen, bijvoorbeeld tijdens het testen van een lagere omgeving.

In de volgende secties ziet u enkele strategieën voor het structureren van uw bestanden.

### Eén configuratiebestand voor alle omgevingen {#single-file}

De bestandsstructuur lijkt op het volgende:

```text
/config
  cdn.yaml
  logForwarding.yaml
```

Gebruik deze structuur wanneer de zelfde configuratie voor alle milieu&#39;s en voor alle types van configuratie (CDN, logboek het door:sturen, enz.) voldoende is. In dit scenario zou de array-eigenschap `envTypes` alle omgevingstypen bevatten.

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
