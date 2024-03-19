---
title: Het vormen van Verkeer bij CDN
description: Leer hoe te om verkeer te vormen CDN door regels en filters in een configuratiedossier te verklaren en hen op te stellen aan CDN door de Pijpleiding van de Configuratie van de Manager van de Wolk te gebruiken.
feature: Dispatcher
source-git-commit: 0a0c9aa68b192e8e2a612f50a58ba5f9057c862d
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 0%

---


# Het vormen van Verkeer bij CDN {#cdn-configuring-cloud}

>[!NOTE]
>Deze functie is nog niet algemeen beschikbaar. Als u wilt deelnemen aan het programma voor vroegtijdige adoptie, kunt u een e-mail sturen `aemcs-cdn-config-adopter@adobe.com` en beschrijf uw gebruiksgeval.

AEM as a Cloud Service biedt een inzameling van eigenschappen die bij [CDN met beheerde Adobe](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) laag die de aard van of inkomende verzoeken of uitgaande reacties wijzigt. De volgende regels, die in detail in deze pagina worden beschreven, kunnen worden verklaard om het volgende gedrag te bereiken:

* [Transformaties aanvragen](#request-transformations) - aspecten van binnenkomende aanvragen, zoals kopteksten, paden en parameters, wijzigen.
* [Responstransformaties](#response-transformations) - wijzigt kopteksten die op weg terug naar de cliënt (bijvoorbeeld, Webbrowser) zijn.
* [Clientdirecteuren](#client-side-redirectors) - een omleiding door de browser activeren.
* [Oorspronkelijke kiezers](#origin-selectors) - een vervangende waarde naar een andere achterkant van de oorsprong.

Ook configureerbaar bij CDN zijn de Regels van de Filter van het Verkeer (met inbegrip van WAF), die controleert welk verkeer door CDN wordt toegestaan of wordt ontkend. Deze functie is al uitgebracht en u kunt er meer over leren in het dialoogvenster [Verkeersfilterregels inclusief WAF-regels](/help/security/traffic-filter-rules-including-waf.md) pagina.

Bovendien, als CDN niet zijn oorsprong kan contacteren, kunt u een regel schrijven die verwijzingen een zelf-ontvangen pagina van de douanefout (die dan wordt teruggegeven). Lees hier meer over door het [CDN-foutpagina&#39;s configureren](/help/implementing/dispatcher/cdn-error-pages.md) artikel.

Al deze regels, die in een configuratiedossier in broncontrole worden verklaard, worden opgesteld door te gebruiken [Configuratie-pijplijn van Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline). Houd er rekening mee dat de cumulatieve grootte van het configuratiebestand niet groter kan zijn dan 100 kB.

## Evaluatievolgorde {#order-of-evaluation}

Functioneel worden de verschillende eerder vermelde functies in de volgende volgorde geëvalueerd:

![afbeelding](/help/implementing/dispatcher/assets/order.png)

## Instellen {#initial-setup}

Alvorens u verkeer bij CDN kunt vormen moet u het volgende doen:

* Maak eerst deze map en bestandsstructuur in de map op hoofdniveau van het Git-project:

```
config/
     cdn.yaml
```

* Ten tweede, de `cdn.yaml` Het configuratiebestand moet zowel metagegevens als de regels bevatten die in de onderstaande voorbeelden worden beschreven.

## Transformaties aanvragen {#request-transformations}

De de transformatieregels van het verzoek staan u toe om inkomende verzoeken te wijzigen. De regels ondersteunen het instellen, ongedaan maken en wijzigen van paden, queryparameters en headers (inclusief cookies) op basis van verschillende overeenkomende voorwaarden, waaronder reguliere expressies. U kunt ook variabelen instellen, waarnaar later in de evaluatiereeks kan worden verwezen.

Gebruiksscenario&#39;s zijn verschillend en bevatten URL-herschrijvingen voor het vereenvoudigen van toepassingen of het toewijzen van verouderde URL&#39;s.

Zoals eerder vermeld, is er een groottebeperking voor het configuratiebestand, zodat organisaties met grotere vereisten regels moeten definiëren in het dialoogvenster `apache/dispatcher` laag.

Voorbeeld van configuratie:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:  
  experimental_requestTransformations:
    removeMarketingParams: true
    rules:
      - name: set-header-rule
        when:
          reqProperty: path
          like: /set-header
        actions:
          - type: set
            reqHeader: x-some-header
            value: some value
 
      - name: unset-header-rule
        when:
          reqProperty: path
          like: /unset-header
        actions:
          - type: unset
            reqHeader: x-some-header
 
      - name: set-query-param-rule
        when:
          reqProperty: path
          equals: /set-query-param
        actions:
          - type: set
            queryParam: someParam
            value: someValue
 
      - name: unset-query-param-rule
        when:
          reqProperty: path
          equals: /unset-query-param
        actions:
          - type: unset
            queryParam: someParam
 
      - name: unset-matching-query-params-rule
        when:
          reqProperty: path
          equals: /unset-matching-query-params
        actions:
          - type: unset
            queryParamMatch: ^removeMe_.*$
 
      - name: unset-all-query-params-except-exact-two-rule
        when:
          reqProperty: path
          equals: /unset-all-query-params-except-exact-two
        actions:
          - type: unset
            queryParamMatch: ^(?!leaveMe$|leaveMeToo$).*$
 
      - name: set-req-cookie-rule
        when:
          reqProperty: path
          equals: /set-req-cookie
        actions:
          - type: set
            reqCookie: someParam
            value: someValue
 
      - name: unset-req-cookie-rule
        when:
          reqProperty: path
          equals: /unset-req-cookie
        actions:
          - type: unset
            reqCookie: someParam
 
      - name: set-variable-rule
        when:
          reqProperty: path
          equals: /set-variable
        actions:
          - type: set
            var: some_var_name
            value: some value
 
      - name: unset-variable-rule
        when:
          reqProperty: path
          equals: /unset-variable
        actions:
          - type: unset
            var: some_var_name
 
      - name: replace-segment
        when:
          reqProperty: path
          like: /replace-segment/*
        actions:
          - type: replace
            reqProperty: path
            match: /replace-segment/
            value: /segment-was-replaced/
 
      - name: replace-extension
        when:
          reqProperty: path
          like: /replace-extension/*.html
        actions:
          - type: replace
            reqProperty: path
            match: \.html
            value: ''
 
      - name: multi-action
        when:
          reqProperty: path
          like: /multi-action
        actions:
          - type: set
            reqHeader: x-header1
            value: body set by transformation rule
          - type: set
            reqHeader: x-header2
            value: '201'
```

**Handelingen**

In de onderstaande tabel worden de beschikbare acties beschreven.

| Naam | Eigenschappen | Betekenis |
|-----------|--------------------------|-------------|
| **set** | reqHeader, waarde | Hiermee wordt een opgegeven header ingesteld op een bepaalde waarde. |
|     | queryParam, waarde | Stelt een opgegeven queryparameter in op een bepaalde waarde. |
|     | reqCookie, waarde | Hiermee wordt een opgegeven cookie ingesteld op een bepaalde waarde. |
|     | var, value | Stelt een opgegeven variabele in op een bepaalde waarde. |
| **vrijmaken** | reqHeader | Hiermee wordt een opgegeven koptekst verwijderd. |
|         | queryParam | Hiermee wordt een opgegeven queryparameter verwijderd. |
|         | reqCookie | Hiermee wordt een opgegeven cookie verwijderd. |
|         | var | Hiermee wordt een opgegeven variabele verwijderd. |
|         | queryParamMatch | Verwijdert alle queryparameters die overeenkomen met een opgegeven reguliere expressie. |
| **vervangen** | reqProperty, match, value | Hiermee wordt een deel van de eigenschap request vervangen door een nieuwe waarde. Momenteel wordt alleen de eigenschap &quot;path&quot; ondersteund. |

### Variabelen {#variables}

U kunt variabelen tijdens de verzoektransformatie plaatsen en dan van verwijzingen voorzien hen later in de evaluatiereeks. Zie de [volgorde van beoordeling](#order-of-evaluation) schema voor nadere bijzonderheden.

Voorbeeld van configuratie:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:   
  experimental_requestTransformations:
    rules:
      - name: set-variable-rule
        when:
          reqProperty: path
          equals: /set-variable
        actions:
          - type: set
            var: some_var_name
            value: some_value
 
  experimental_responseTransformations:
    rules:
      - name: set-response-header-while-variable
        when:
          var: some_var_name
          equals: some_value
        actions:
          - type: set
            respHeader: x-some-header
            value: some header value
```

## Responstransformaties {#response-transformations}

De de transformatieregels van de Reactie staan u toe om kopballen van de uitgaande reacties van CDN te plaatsen en unset. Zie ook het bovenstaande voorbeeld voor het verwijzen naar een variabele die eerder is ingesteld in een aanvraagtransformatieregel.

Voorbeeld van configuratie:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:
  experimental_responseTransformations:
    rules:
      - name: set-response-header-rule
        when:
          reqProperty: path
          like: /set-response-header
        actions:
          - type: set
            value: value-set-by-resp-rule
            respHeader: x-resp-header
 
      - name: unset-response-header-rule
        when:
          reqProperty: path
          like: /unset-response-header
        actions:
          - type: unset
            respHeader: x-header1
 
      # Example: Multi-action on response header
      - name: multi-action-response-header-rule
        when:
          reqProperty: path
          like: /multi-action-response-header
        actions:
          - type: set
            respHeader: x-resp-header-1
            value: value-set-by-resp-rule-1
          - type: set
            respHeader: x-resp-header-2
            value: value-set-by-resp-rule-2
```

**Handelingen**

In de onderstaande tabel worden de beschikbare acties beschreven.

| Naam | Eigenschappen | Betekenis |
|-----------|--------------------------|-------------|
| **set** | reqHeader, waarde | Stelt een opgegeven header in op een bepaalde waarde in de reactie. |
| **vrijmaken** | respHeader | Hiermee verwijdert u een opgegeven koptekst uit het antwoord. |

## Oorspronkelijke kiezers {#origin-selectors}

U kunt hefboomwerking AEM CDN aan routeverkeer aan verschillende achtergronden, met inbegrip van toepassingen niet-Adobe (misschien op een per-weg of subdomain basis).

Voorbeeld van configuratie:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_originSelectors:
    rules:
      - name: example-com
        when: { reqProperty: path, like: /proxy-me* }
        action:
          type: selectOrigin
          originName: example-com
          # useCache: false
    origins:
      - name: example-com
        domain: www.example.com
        # ip: '1.1.1.1'
        # forwardHost: true
        # forwardCookie: true 
        # forwardAuthorization: true
        # timeout: 20
```

**Handelingen**

Uitleg in de onderstaande tabel is de beschikbare handeling.

| Naam | Eigenschappen | Betekenis |
|-----------|--------------------------|-------------|
| **selectOrigin** | originName | Naam van een van de gedefinieerde oorsprong. |
|     | useCache (optioneel, standaard true) | Vlag of om caching voor verzoeken te gebruiken die deze regel aanpassen. |

**Oorsprong**

Verbindingen met oorsprong zijn alleen SSL en gebruiken poort 443.

| Eigenschap | Betekenis |
|------------------|--------------------------------------|
| **name** | Naam waarnaar kan worden verwezen door &quot;action.originName&quot;. |
| **domein** | Domeinnaam gebruikt om verbinding te maken met de aangepaste achtergrond. Het wordt ook gebruikt voor SSL SNI en bevestiging. |
| **ip** (optioneel, ondersteund iv4 en ipv6) | Indien opgegeven, wordt deze gebruikt om verbinding te maken met de backend in plaats van met &quot;domain&quot;. Stilstaand &quot;domein&quot; wordt gebruikt voor SSL SNI en validatie. |
| **forwardHost** (optioneel, standaard is false) | Indien ingesteld op true, wordt de header &quot;Host&quot; van de clientaanvraag doorgegeven aan de backend, anders wordt de waarde &quot;domain&quot; doorgegeven in de header &quot;Host&quot;. |
| **forwardCookie** (optioneel, standaard is false) | Als de waarde true is, wordt de koptekst &#39;Cookie&#39; uit de clientaanvraag doorgegeven aan de achterkant. Als dit niet het geval is, wordt de koptekst Cookie verwijderd. |
| **forwardAuthorization** (optioneel, standaard is false) | Als de waarde true is, wordt de header &quot;Authorization&quot; van de clientaanvraag doorgegeven aan de back-end, anders wordt de machtigingsheader verwijderd. |
| **timeout** (optioneel, in seconden, standaard is 60) | Aantal seconden dat CDN op een backendserver moet wachten om de eerste byte van een HTTP-antwoordinstantie te leveren. Deze waarde wordt ook gebruikt als een tussenliggende time-out naar de backend-server. |

## Clientbestuurders {#client-side-redirectors}

U kunt de omleidingsregels aan de clientzijde gebruiken voor 301, 302 en vergelijkbare omleidingen aan de clientzijde. Als een regel overeenkomt, reageert de CDN met een statusregel die de statuscode en het bericht bevat (bijvoorbeeld HTTP/1.1 301 Permanent verplaatst) en met de locatiekoptekenset.

Zowel absolute als relatieve locaties met vaste waarden zijn toegestaan.

Voorbeeld van configuratie:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_redirects:
    rules:
      - name: redirect-absolute
        when: { reqProperty: path, equals: "/page.html" }
        action:
          type: redirect
          status: 301
          location: https://example.com/page
      - name: redirect-relative
        when: { reqProperty: path, equals: "/anotherpage.html" }
        action:
          type: redirect
          location: /anotherpage
```

| Naam | Eigenschappen | Betekenis |
|-----------|--------------------------|-------------|
| **omleiden** | locatie | Waarde voor de koptekst &#39;Locatie&#39;. |
|     | status (optioneel, standaard is 301) | De HTTP-status die standaard moet worden gebruikt in het omleidingsbericht, is 301. De toegestane waarden zijn: 301, 302, 303, 307, 308. |
