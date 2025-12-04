---
title: Config Pipelines gebruiken
description: Leer hoe u config pijpleidingen kunt gebruiken om verschillende configuraties in AEM as a Cloud Service zoals logboek op te stellen door:sturen montages, zuivert-verwante onderhoudstaken, en diverse configuraties CDN.
feature: Operations
role: Admin
exl-id: bd121d31-811f-400b-b3b8-04cdee5fe8fa
source-git-commit: ac04829b63ca5e2fee71f6c71d0730f21c576382
workflow-type: tm+mt
source-wordcount: '1405'
ht-degree: 0%

---

# Configuratiepijpleidingen gebruiken {#config-pipelines}

Leer hoe u config pijpleidingen kunt gebruiken om verschillende configuraties in AEM as a Cloud Service zoals logboek op te stellen door:sturen montages, zuivert-verwante onderhoudstaken, en diverse configuraties CDN.

## Overzicht {#overview}

Een Cloud Manager config pijpleiding stelt configuratiedossiers (die in formaat YAML worden gecreeerd) aan een doelmilieu op. Een aantal eigenschappen in AEM as a Cloud Service kan op deze manier worden gevormd, met inbegrip van logboek het door:sturen, zuivert-verwante onderhoudstaken, en verscheidene eigenschappen CDN.

Voor **publiceer de Projecten van de Levering**, config de pijpleidingen kunnen via Cloud Manager worden opgesteld om, stadium, en de types van productiemilieu te ontwikkelen. De configuratiedossiers kunnen aan Snelle Milieu&#39;s van de Ontwikkeling (RDEs) worden opgesteld gebruikend [ het hulpmiddel van de bevellijn van de bevellijn ](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline).

De pijpleidingen van config kunnen ook door Cloud Manager voor **Edge Delivery** Projecten worden opgesteld.

Deze volgende secties van dit document geven een overzicht van belangrijke informatie betreffende hoe config de pijpleidingen kunnen worden gebruikt en hoe de configuraties voor hen zouden moeten worden gestructureerd. Het beschrijft algemene concepten die over of allen of een ondergroep van de eigenschappen worden gedeeld die door config pijpleidingen worden gesteund.

* [ Gesteunde Configuraties ](#configurations) - een lijst van configuraties die met config pijpleidingen kunnen worden opgesteld.
* [ creeer en beheer config pijpleidingen ](#creating-and-managing) - hoe te om een config pijpleiding tot stand te brengen
* [ Gemeenschappelijke syntaxis ](#common-syntax) - Syntaxis die over configuraties wordt gedeeld.
* [ structuur van de Omslag ](#folder-structure) - Beschrijft de structuur config pijpleidingen die voor de configuraties verwachten.
* [ Geheime omgevingsvariabelen ](#secret-env-vars) - Voorbeelden van het gebruiken van omgevingsvariabelen om geheimen in uw configuraties niet openbaar te maken.
* [ Geheime pijpleidingsvariabelen ](#secret-pipeline-vars) - Voorbeelden om omgevingsvariabelen te gebruiken om geheimen in uw configuraties voor de projecten van Edge Delivery Services niet openbaar te maken.

## Ondersteunde configuraties {#configurations}

De volgende lijst biedt een uitvoerige lijst van dergelijke configuraties met verbindingen aan specifieke documentatie die zijn verschillende configuratiesyntaxis en andere informatie beschrijft.

| Type | YAML `kind` Waarde | Beschrijving | Levering publiceren | Edge Delivery |
|---|---|---|---|---|
| [ Regels van de Filter van het Verkeer, met inbegrip van WAF ](/help/security/traffic-filter-rules-including-waf.md) | `CDN` | Declareer regels om kwaadwillig verkeer te blokkeren | X | X |
| [ Transformaties van het Verzoek ](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) | `CDN` | Declareer regels om de vorm van het verkeersverzoek om te zetten | X | X |
| [ Transformaties van de Reactie ](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) | `CDN` | Declareer regels om de vorm van de reactie voor een bepaald verzoek om te zetten | X | X |
| [ Server-kant richt ](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors) opnieuw | `CDN` | Declareer serveromleidingen van 301/302 stijl | X | X |
| [ de Selecteurs van de Oorsprong ](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) | `CDN` | Declareer regels om verkeer aan verschillende achtergronden, met inbegrip van toepassingen te leiden niet Adobe | X | X |
| [ CDN foutenpagina&#39;s ](/help/implementing/dispatcher/cdn-error-pages.md) | `CDN` | Overschrijf de standaardfoutpagina als de AEM-oorsprong niet kan worden bereikt. Hierbij wordt verwezen naar de locatie van zelfgehoste statische inhoud in het configuratiebestand | X |  |
| [ CDN zuiveren ](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) | `CDN` | Declareer de Leegmaken API-sleutels die worden gebruikt om de CDN op te lossen | X |  |
| [ Klantbeheerd het teken van HTTP CDN ](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#CDN-HTTP-value) | `CDN` | Declareer de waarde van de x-AEM-Edge-Sleutel nodig om Adobe CDN van een CDN van de Klant te roepen | X |  |
| [ Basisauthentificatie ](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token#basic-auth) | `CDN` | Declareer de gebruikersnamen en de wachtwoorden voor een basisautwiedialoog die bepaalde URLs beschermen. | X | X |
| [ Taak van het Onderhoud van de Opruiming van de Versie ](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimaliseer de AEM-opslagplaats door regels te declareren over het tijdstip waarop versies van inhoud moeten worden gewist | X |  |
| [ Taak van het Onderhoud van de Aanzuivering van het Logboek van de Controle ](/help/operations/maintenance.md#purge-tasks) | `MaintenanceTasks` | Optimaliseer het AEM controlelogboek voor verhoogde prestaties door regels rond te verklaren wanneer het logboek zou moeten worden gezuiverd | X |  |
| [ Taak van het Onderhoud van de Opschoonfunctie van het Werkschema ](/help/operations/maintenance.md) | `MaintenanceTasks` | Minimaliseer het aantal werkstroominstanties om de prestaties van de werkstroomengine te helpen verbeteren.<br><br> zie ook [ Regelmatige het Schrappen van de Instanties van het Werkschema ](/help/sites-cloud/administering/workflows-administering.md#regular-purging-of-workflow-instances) | X |  |
| [ Logboek door:sturen ](/help/implementing/developing/introduction/log-forwarding.md) | `LogForwarding` | Vorm de eindpunten en de geloofsbrieven voor het door:sturen van logboeken aan diverse bestemmingen, met inbegrip van Azure Blob Storage, Datadog, HTTPS, Elasticsearch, Splunk | X | X |
| [ registrerend een identiteitskaart van de Cliënt ](/help/implementing/developing/open-api-based-apis.md) | `API` | Bereik Adobe Developer Console API-projecten voor een specifieke AEM-omgeving door de client-id te registreren. Nodig voor gebruik van op OpenAPI gebaseerde API&#39;s die verificatie vereisen | X |  |

## Configuratieleidingen maken en beheren {#creating-and-managing}

Voor informatie over om **te creëren en te vormen publiceer levering** config pijpleidingen, zie [ CI/CD Pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline). Wanneer het creëren van een config pijpleiding in Cloud Manager, ben zeker om a **gerichte Plaatsing** eerder dan **Volledige Code van de Stapel** te selecteren wanneer het vormen van de pijpleiding. Zoals vroeger genoteerd, wordt de configuratie voor RDEs opgesteld gebruikend [ het hulpmiddel van de bevellijn ](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline) eerder dan een pijpleiding.

Voor informatie over om **Edge Delivery** config pijpleidingen tot stand te brengen en te vormen, zie [ een artikel van de Pijpleiding van Edge Delivery ](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md) toevoegen.

## Algemene syntaxis {#common-syntax}

Elk configuratiebestand begint met eigenschappen die op het volgende voorbeeldfragment lijken:

```yaml
   kind: "CDN"
   version: "1"
   metadata: ...
   data: ...
```

| Eigenschap | Beschrijving | Standaard |
|---|---|---|
| `kind` | Een koord dat bepaalt welk type van configuratie, zoals logboek het door:sturen, de regels van de verkeersfilter, of verzoektransformaties | Vereist, geen standaard |
| `version` | Een tekenreeks die de schemaversie vertegenwoordigt | Vereist, geen standaard |
| `metadata` | (Optioneel) Dit bevat een array met tekenreeksen `envTypes` die bepaalt voor welke omgevingstypen de configuratie wordt verwerkt. Voor **publiceer Levering** mogelijke waarden zijn `dev`, `stage` en `prod`. Voor **Edge Delivery**, slechts zou een waarde van `prod` moeten worden gebruikt. Als de array bijvoorbeeld alleen `dev` bevat, wordt de configuratie niet geladen in werkgebied- of prodomgevingen, zelfs niet als de configuratie daar wordt geïmplementeerd. | Alle omgevingstypen, d.w.z. (dev, stage, prod) voor levering publiceren of alleen-prod voor Edge Delivery. |

U kunt het hulpprogramma `yq` gebruiken om de YAML-opmaak van uw configuratiebestand lokaal te valideren (bijvoorbeeld `yq cdn.yaml` ).

## Levering publiceren {#yamls-for-aem}

**publiceer de configuraties van de Levering** zullen aan een doelmilieu worden opgesteld. Wanneer u zich richt op meerdere omgevingen, kunt u de verschillende bestanden op verschillende manieren ordenen. Als de array bijvoorbeeld alleen `dev` bevat, wordt de configuratie niet geladen in werkgebied- of prodomgevingen, zelfs niet als de configuratie daar wordt geïmplementeerd.

```yaml
   kind: "CDN"
   version: "1"
   metadata:
    envType: ["dev"]
```

### Mapstructuur {#folder-structure}

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

Configuraties worden doorgaans in alle omgevingen geïmplementeerd. Als alle bezitswaarden voor elk milieu identiek zijn, volstaat één enkel dossier YAML. Het is echter gebruikelijk dat eigenschapswaarden verschillen tussen omgevingen, bijvoorbeeld tijdens het testen van een lagere omgeving.

In de volgende secties ziet u enkele strategieën voor het structureren van uw bestanden.

### Eén configuratiebestand voor alle omgevingen {#single-file}

De bestandsstructuur ziet er als volgt uit:

```text
/config
  cdn.yaml
  logForwarding.yaml
```

Gebruik deze structuur wanneer de zelfde configuratie voor alle milieu&#39;s en voor alle types van configuratie (CDN, logboek het door:sturen, etc.) voldoende is. In dit scenario zou de array-eigenschap `envTypes` alle omgevingstypen bevatten.

```yaml
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev", "stage", "prod"]
```

Gebruikend geheim-type milieu (of pijpleiding) variabelen, is het mogelijk voor [ geheime eigenschappen ](#secret-env-vars) om per milieu te variëren, zoals geïllustreerd door de volgende `${{SPLUNK_TOKEN}}` verwijzing.

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

De bestandsstructuur ziet er als volgt uit:

```text
/config
  cdn-dev.yaml
  cdn-stage.yaml
  cdn-prod.yaml
  logForwarding-dev.yaml
  logForwarding-stage.yaml
  logForwarding-prod.yaml
```

Gebruik deze structuur wanneer er verschillen in eigenschapswaarden kunnen zijn. In de bestanden wordt verwacht dat de arraywaarde `envTypes` overeenkomt met het achtervoegsel. `cdn-dev.yaml` en `logForwarding-dev.yaml` bijvoorbeeld met de waarde `["dev"]` , `cdn-stage.yaml` en `logForwarding-stage.yaml` met de waarde `["stage"]` , enzovoort.

### Een map per omgeving {#folder-per-env}

In deze strategie, is er een afzonderlijke `config` omslag per milieu, met een afzonderlijke pijpleiding die in Cloud Manager voor elk wordt verklaard.

Deze benadering is vooral nuttig als u veelvoudige ontwikkelomgevingen hebt, waar elk unieke bezitswaarden heeft.

De bestandsstructuur ziet er als volgt uit:

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

## Edge Delivery Services {#yamls-for-eds}

Edge Delivery config-pijpleidingen hebben geen afzonderlijke ontwikkelings-, staging- en productieomgevingen. In de omgeving van Publiceren van de Levering, verandert vooruitgang door dev, stadium, en prod rijen. Een Edge Delivery config-pijplijn past daarentegen de configuratie rechtstreeks toe op alle domeintoewijzingen die in Cloud Manager voor een Edge Delivery-site zijn geregistreerd.


Implementeer dus een eenvoudige bestandsstructuur, zoals:

```text
/config
  cdn.yaml
  logForwarding.yaml
```

Als een regel per plaats van Edge Delivery moet verschillen, gebruik de syntaxis *wanneer* om de regels van elkaar te onderscheiden. Het domein komt bijvoorbeeld overeen met dev.example.com in het onderstaande fragment, dat kan worden onderscheiden van het domein `www.example.com` .

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
    rules:
    # Block simple path
    - name: block-path
      when:
        allOf:
          - reqProperty: domain
            equals: "dev.example.com"
          - reqProperty: path
            equals: '/block/me'
      action: block
```

Als het omvatten van het *envTypes* meta-gegevensgebied, slechts zou de waarde **prod** moeten worden gebruikt (het weglaten van het envTypes meta-gegevensgebied is ook fijn). Voor de *rij* reqProperty, slechts publiceert de waarde **** zou moeten worden gebruikt.

## Geheime omgevingsvariabelen {#secret-env-vars}

Zo dat de gevoelige informatie niet in broncontrole moet worden opgeslagen, steunen de configuratiedossiers de milieu variabelen van Cloud Manager van type **geheim**. Voor sommige configuraties, met inbegrip van logdoor:sturen, zijn de geheime omgevingsvariabelen verplicht voor bepaalde eigenschappen.

Merk op dat de geheime omgevingsvariabelen voor de Publish Projecten van de Levering worden gebruikt; zie de Geheime sectie van de Variabelen van de Pijpleiding voor de projecten van Edge Delivery Services.

Het volgende fragment is een voorbeeld van hoe de geheime omgevingsvariabele `${{SPLUNK_TOKEN}}` in de configuratie wordt gebruikt.

```
kind: "LogForwarding"
version: "1"
data:
  splunk:
    default:
      enabled: true
      host: "splunk-host.example.com"
      token: "${{SPLUNK_TOKEN}}"
      index: "AEMaaCS"
```

Voor details op hoe te om milieuvariabelen te gebruiken, zie [ de Variabelen van het Milieu van Cloud Manager ](/help/implementing/cloud-manager/environment-variables.md).

## Geheime pijpleidingsvariabelen {#secret-pipeline-vars}

Voor de Projecten van Edge Delivery Services, de pijpleidingsvariabelen van gebruiksCloud Manager van type **geheim** zodat moet de gevoelige informatie niet in broncontrole worden opgeslagen. De *Toegepaste Stap* uitgezochte doos zou **gebruiken stelt** optie op.

De syntaxis is identiek aan het fragment dat in de vorige sectie wordt weergegeven.

Voor details op hoe te om pijpleidingsvariabelen te gebruiken, zie [ Variabelen van de Pijpleiding in Cloud Manager ](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).
