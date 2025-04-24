---
title: Het vormen van Verkeer bij CDN
description: Leer hoe te om verkeer te vormen CDN door regels en filters in een configuratiedossier te verklaren en hen op te stellen aan CDN door een Cloud Manager config pijpleiding te gebruiken.
feature: Dispatcher
exl-id: e0b3dc34-170a-47ec-8607-d3b351a8658e
role: Admin
source-git-commit: 9e0217a4cbbbca1816b47f74a9f327add3a8882d
workflow-type: tm+mt
source-wordcount: '1493'
ht-degree: 0%

---


# Het vormen van Verkeer bij CDN {#cdn-configuring-cloud}

AEM as a Cloud Service biedt een inzameling van eigenschappen aan configureerbaar bij de [ Adobe-Beheerde CDN ](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) laag die de aard van of inkomende verzoeken of uitgaande reacties wijzigen. De volgende regels, die in detail in deze pagina worden beschreven, kunnen worden verklaard om het volgende gedrag te bereiken:

* [ de transformaties van het Verzoek ](#request-transformations) - wijzig aspecten van inkomende verzoeken, met inbegrip van kopballen, wegen en parameters.
* [ transformaties van de Reactie ](#response-transformations) - wijzig kopballen die op de manier terug naar de cliënt (bijvoorbeeld, Webbrowser) zijn.
* [ server-kant richt ](#server-side-redirectors) opnieuw - teweegbrengt browser omleiding.
* [ de selecteurs van de Oorsprong ](#origin-selectors) - volmacht aan een verschillende oorsprong achterkant.

Ook configureerbaar bij CDN zijn de Regels van de Filter van het Verkeer (met inbegrip van WAF), die controleert welk verkeer door CDN wordt toegestaan of wordt ontkend. Deze eigenschap wordt reeds vrijgegeven en u kunt meer over het in de [ Regels van de Filter van het Verkeer leren met inbegrip van WAF regels ](/help/security/traffic-filter-rules-including-waf.md) pagina.

Bovendien, als CDN niet zijn oorsprong kan contacteren, kunt u een regel schrijven die verwijzingen een zelf-ontvangen pagina van de douanefout (die dan wordt teruggegeven). Leer meer over dit door [ te lezen Vormend CDN foutenpagina&#39;s ](/help/implementing/dispatcher/cdn-error-pages.md) artikel.

Al deze regels, die in een configuratiedossier in broncontrole worden verklaard, worden opgesteld door de Cloud Manager [ te gebruiken config pijpleiding ](/help/operations/config-pipeline.md). Houd er rekening mee dat de cumulatieve grootte van het configuratiebestand, inclusief de regels voor verkeersfilters, niet groter kan zijn dan 100 kB.

## Evaluatievolgorde {#order-of-evaluation}

Functioneel worden de verschillende eerder vermelde functies in de volgende volgorde geëvalueerd:

![ Orde van evaluatie ](/help/implementing/dispatcher/assets/order.png)

## Instellen {#initial-setup}

Alvorens u verkeer bij CDN kunt vormen moet u het volgende doen:

1. Maak een bestand met de naam `cdn.yaml` of een vergelijkbaar bestand, waarbij u verwijst naar de verschillende configuratiefragmenten in de onderstaande secties.

   Alle fragmenten hebben deze gemeenschappelijke eigenschappen, die onder [ worden beschreven Config Pijpleiding ](/help/operations/config-pipeline.md#common-syntax). De `kind` bezitswaarde zou *CDN* moeten zijn en het `version` bezit zou aan *1* moeten worden geplaatst.

   ```
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev"]
   ```

1. Plaats het dossier ergens onder een top niveauomslag genoemd *config* of gelijkaardig, zoals die onder [ wordt beschreven Pijpleiding Config ](/help/operations/config-pipeline.md#folder-structure).

1. Creeer een Pijpleiding Config in Cloud Manager, zoals die onder [ wordt beschreven Config Pijpleiding ](/help/operations/config-pipeline.md#managing-in-cloud-manager).

1. Implementeer de configuratie.

## Syntaxis regels {#configuration-syntax}

De regeltypen in de onderstaande secties hebben dezelfde syntaxis.

Een regel wordt van verwijzingen voorzien door een naam, een voorwaardelijk &quot;wanneer clausule&quot;, en acties.

De clausule Wanneer bepaalt of een regel zal worden geëvalueerd, gebaseerd op eigenschappen zoals domein, weg, vraagkoorden, kopballen, en koekjes. De syntaxis is het zelfde over regeltypes; voor details, zie de ](/help/security/traffic-filter-rules-including-waf.md#condition-structure) sectie van de Structuur van de Voorwaarde in het artikel van de Regels van de Filter van het Verkeer.[

De details van het actieknooppunt verschillen per regeltype en worden in de afzonderlijke secties hieronder beschreven.

## Transformaties aanvragen {#request-transformations}

De de transformatieregels van het verzoek staan u toe om inkomende verzoeken te wijzigen. De regels ondersteunen het instellen, ongedaan maken en wijzigen van paden, queryparameters en headers (inclusief cookies) op basis van verschillende overeenkomende voorwaarden, waaronder reguliere expressies. U kunt ook variabelen instellen, waarnaar later in de evaluatiereeks kan worden verwezen.

Gebruiksscenario&#39;s zijn verschillend en bevatten URL-herschrijvingen voor het vereenvoudigen van toepassingen of het toewijzen van verouderde URL&#39;s.

Zoals eerder vermeld, is er een groottegrens aan het configuratiedossier zodat zouden de organisaties met grotere vereisten regels in de `apache/dispatcher` laag moeten bepalen.

Voorbeeld van configuratie:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev", "stage", "prod"]
data:
  requestTransformations:
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
      - name: set-header-with-reqproperty-rule
        when:
          reqProperty: path
          like: /set-header
        actions:
          - type: set
            reqHeader: x-some-header
            value: {reqProperty: path}
      - name: unset-header-rule
        when:
          reqProperty: path
          like: /unset-header
        actions:
          - type: unset
            reqHeader: x-some-header
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
      - name: replace-html
        when:
          reqProperty: path
          like: /mypath
        actions:
          - type: transform
            reqProperty: path
            op: replace
            match: \.html$
            replacement: ""
      - name: log-on-request
        when: "*"
        actions:
          - type: set
            logProperty: forwarded_host
            value:
              reqHeader: x-forwarded-host
```

**Acties**

In de onderstaande tabel worden de beschikbare acties beschreven.

| Naam | Eigenschappen | Betekenis |
|-----------|--------------------------|-------------|
| **plaats** | reqProperty, value | Hiermee wordt een opgegeven parameter request ingesteld (alleen eigenschap &quot;path&quot; wordt ondersteund) |
|     | reqHeader, waarde | Stelt een opgegeven aanvraagheader in op een bepaalde waarde. |
|     | queryParam, waarde | Stelt een opgegeven queryparameter in op een bepaalde waarde. |
|     | reqCookie, waarde | Stelt een opgegeven aanvraagcookie in op een bepaalde waarde. |
|     | logProperty, value | Stelt een opgegeven CDN-logeigenschap in op een bepaalde waarde. |
|     | var, value | Stelt een opgegeven variabele in op een bepaalde waarde. |
| **unset** | reqProperty | Hiermee wordt een opgegeven parameter request verwijderd (alleen eigenschap &quot;path&quot; wordt ondersteund) |
|     | reqHeader, waarde | Hiermee wordt een opgegeven aanvraagheader verwijderd. |
|     | queryParam, waarde | Hiermee wordt een opgegeven queryparameter verwijderd. |
|     | reqCookie, waarde | Hiermee wordt een opgegeven cookie verwijderd. |
|     | logProperty, value | Hiermee wordt een opgegeven CDN-logeigenschap verwijderd. |
|     | var | Hiermee wordt een opgegeven variabele verwijderd. |
|     | queryParamMatch | Verwijdert alle queryparameters die overeenkomen met een opgegeven reguliere expressie. |
|     | queryParamDoesNotMatch | Verwijdert alle queryparameters die niet overeenkomen met een opgegeven reguliere expressie. |
| **transformatie** | op:replace, (reqProperty of reqHeader of queryParam of reqCookie of var), match, replacement | Vervangt een deel van de aanvraagparameter (alleen eigenschap &quot;path&quot; ondersteund), of verzoek header, of query parameter, cookie of variabele door een nieuwe waarde. |
|              | op:tolower, (reqProperty of reqHeader of queryParam of reqCookie of var) | Stelt de parameter request (alleen eigenschap &quot;path&quot; ondersteund), of aanvraagheader, queryparameter, cookie of variabele in op de waarde in kleine letters. |

Vervang acties om vastgelegde groepen te ondersteunen, zoals hieronder wordt geïllustreerd:

```
      - name: extract-country-code-from-path
        when:
          reqProperty: path
          matches: ^/([a-zA-Z]{2})(/.*|$)
        actions:
          - type: set
            var: country-code
            value:
              reqProperty: path
          - type: transform
            var: country-code
            op: replace
            match: ^/([a-zA-Z]{2})(/.*|$)
            replacement: \1
      - name: replace-jpg-with-jpeg
        when:
          reqProperty: path
          like: /mypath
        actions:
          - type: transform
            reqProperty: path
            op: replace
            match: (.*)(\.jpg)$
            replacement: "\1\.jpeg"
```

Handelingen kunnen aan elkaar worden gekoppeld. Bijvoorbeeld:

```
actions:
    - type: transform
      reqProperty: path
      op: replace
      match: \.html$
      replacement: ""
    - type: transform
      reqProperty: path
      op: tolower
```

### Variabelen {#variables}

U kunt variabelen tijdens de verzoektransformatie plaatsen en dan van verwijzingen voorzien hen later in de evaluatiereeks. Zie de [ orde van evaluatie ](#order-of-evaluation) diagram voor verdere details.

Voorbeeld van configuratie:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:
  requestTransformations:
    rules:
      - name: set-variable-rule
        when:
          reqProperty: path
          equals: /set-variable
        actions:
          - type: set
            var: some_var_name
            value: some_value

  responseTransformations:
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

### Log, eigenschap {#logproperty}

U kunt uw eigen logboekeigenschappen in uw CDN- logboeken toevoegen gebruikend verzoek en reactietransformaties.

Voorbeeld van configuratie:

```
requestTransformations:
  rules:
    - name: log-on-request
      when: "*"
      actions:
        - type: set
          logProperty: forwarded_host
          value:
            reqHeader: x-forwarded-host
responseTransformations:
  rules:
    - name: log-on-response
      when: '*'
      actions:
        - type: set
          logProperty: cache_control
          value:
            respHeader: cache-control
```

Logboekvoorbeeld:

```
{
"timestamp": "2025-03-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"rid": "974e67f6",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"host": "example.com",
"url": "/content/hello.png",
"method": "GET",
"res_ctype": "image/png",
"cache": "PASS",
"status": 200,
"res_age": 0,
"pop": "PAR",
"rules": "",
"forwarded_host": "example.com",
"cache_control": "max-age=300"
}
```

## Responstransformaties {#response-transformations}

Met de regels voor het transformeren van reacties kunt u kop- en cookies en de status van de uitgaande reacties van de CDN instellen en ongedaan maken. Zie ook het bovenstaande voorbeeld voor het verwijzen naar een variabele die eerder is ingesteld in een aanvraagtransformatieregel.

Voorbeeld van configuratie:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:
  responseTransformations:
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
      - name: status-code-rule
        when:
          reqProperty: path
          like: status-code
        actions:
          - type: set
            respProperty: status
            value: '410'
      - name: set-response-cookie-with-attributes-as-object
        when: '*'
        actions:
          - type: set
            respCookie: first-name
            value: first-value
            attributes:
              expires: '2025-08-29T10:00:00'
              domain: example.com
              path: /some-path
              secure: true
              httpOnly: true
              extension: ANYTHING
      - name: unset-response-cookie
        when: '*'
        actions:
          - type: unset
            respCookie: third-name
```

**Acties**

In de onderstaande tabel worden de beschikbare acties beschreven.

| Naam | Eigenschappen | Betekenis |
|-----------|--------------------------|-------------|
| **plaats** | respProperty, value | Hiermee wordt een eigenschap response ingesteld. Ondersteunt alleen de eigenschap &quot;status&quot; om de statuscode in te stellen. |
|     | respHeader, waarde | Hiermee wordt een opgegeven antwoordheader ingesteld op een bepaalde waarde. |
|     | respCookie, kenmerken (verloopt, domein, weg, veilig, httpOnly, extension), waarde | Stelt een opgegeven aanvraagcookie met specifieke kenmerken in op een bepaalde waarde. |
|     | logProperty, value | Stelt een opgegeven CDN-logeigenschap in op een bepaalde waarde. |
|     | var, value | Stelt een opgegeven variabele in op een bepaalde waarde. |
| **unset** | respHeader | Hiermee verwijdert u een opgegeven koptekst uit het antwoord. |
|     | respCookie, waarde | Hiermee wordt een opgegeven cookie verwijderd. |
|     | logProperty, value | Hiermee wordt een opgegeven CDN-logeigenschap verwijderd. |
|     | var | Hiermee wordt een opgegeven variabele verwijderd. |

## Oorspronkelijke kiezers {#origin-selectors}

U kunt hefboomwerking AEM CDN aan routeverkeer aan verschillende achtergronden, met inbegrip van toepassingen niet-Adobe (misschien op een per-weg of subdomain basis).

Voorbeeld van configuratie:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  originSelectors:
    rules:
      - name: example-com
        when: { reqProperty: path, like: /proxy* }
        action:
          type: selectOrigin
          originName: example-com
          # skipCache: true
    origins:
      - name: example-com
        domain: www.example.com
        # ip: '1.1.1.1'
        # forwardHost: true
        # forwardCookie: true
        # forwardAuthorization: true
        # timeout: 20
```

**Acties**

Uitleg in de onderstaande tabel is de beschikbare handeling.

| Naam | Eigenschappen | Betekenis |
|-----------|--------------------------|-------------|
| **selectOrigin** | originName | Naam van een van de gedefinieerde oorsprong. |
|     | skipCache (optioneel, standaard is false) | Vlag of om caching voor verzoeken te gebruiken die deze regel aanpassen. De reacties worden standaard in de cache geplaatst op basis van de header voor het in cache plaatsen van reacties (bijvoorbeeld Cache-Control of Expires) |

**Oorsprong**

Verbindingen met oorsprong zijn alleen SSL en gebruiken poort 443.

| Eigenschap | Betekenis |
|------------------|--------------------------------------|
| **naam** | Naam waarnaar kan worden verwezen door &quot;action.originName&quot;. |
| **domein** | Domeinnaam gebruikt om verbinding te maken met de aangepaste achtergrond. Het wordt ook gebruikt voor SSL SNI en bevestiging. |
| **ip** (facultatief, gesteund iv4 en ipv6) | Indien opgegeven, wordt deze gebruikt om verbinding te maken met de backend in plaats van met &quot;domain&quot;. Stilstaand &quot;domein&quot; wordt gebruikt voor SSL SNI en validatie. |
| **forwardHost** (facultatief, gebrek is vals) | Indien ingesteld op true, wordt de header &quot;Host&quot; van de clientaanvraag doorgegeven aan de backend, anders wordt de waarde &quot;domain&quot; doorgegeven in de header &quot;Host&quot;. |
| **forwardCookie** (facultatief, gebrek is vals) | Als de waarde true is, wordt de koptekst &#39;Cookie&#39; uit de clientaanvraag doorgegeven aan de achterkant. Als dit niet het geval is, wordt de koptekst Cookie verwijderd. |
| **forwardAuthorization** (facultatief, gebrek is vals) | Als de waarde true is, wordt de header &quot;Authorization&quot; van de clientaanvraag doorgegeven aan de back-end, anders wordt de machtigingsheader verwijderd. |
| **onderbreking** (facultatief, in seconden, gebrek is 60) | Aantal seconden dat CDN op een backendserver moet wachten om de eerste byte van een HTTP-antwoordinstantie te leveren. Deze waarde wordt ook gebruikt als een tussenliggende time-out naar de backend-server. |

### Proxeren naar Edge Delivery Services {#proxying-to-edge-delivery}

Er zijn scenario&#39;s waar de oorsprongsselecteurs zouden moeten worden gebruikt om verkeer door AEM te leiden publiceer aan AEM Edge Delivery Services:

* Sommige inhoud wordt geleverd door een domein dat wordt beheerd door AEM Publish, terwijl andere inhoud van hetzelfde domein door Edge Delivery Services wordt geleverd
* De inhoud die door Edge Delivery Services wordt geleverd zou van regels profiteren die via config pijpleiding worden opgesteld, met inbegrip van de regels van de verkeersfilter of verzoek/reactietransformaties

Hier volgt een voorbeeld van een regel voor de oorspronkelijke kiezer waarmee u dit kunt bereiken:

```
kind: CDN
version: '1'
data:
  originSelectors:
    rules:
      - name: select-edge-delivery-services-origin
        when:
          allOf:
            - reqProperty: tier
              equals: publish
            - reqProperty: domain
              equals: <Production Host>
            - reqProperty: path
              matches: "^(/scripts/.*|/styles/.*|/fonts/.*|/blocks/.*|/icons/.*|.*/media_.*|/favicon.ico)"
        action:
          type: selectOrigin
          originName: aem-live
    origins:
      - name: aem-live
        domain: main--repo--owner.aem.live
```

>[!NOTE]
> Aangezien Adobe Beheerde CDN wordt gebruikt, zorg ervoor om pushongeldigheid op **beheerde** wijze te vormen, door de de duw van de Opstelling van Edge Delivery Services [ documentatie van de ongeldigverklaring ](https://www.aem.live/docs/byo-dns#setup-push-invalidation) te volgen.


## Server-side omleidingen {#server-side-redirectors}

U kunt de omleidingsregels aan de clientzijde gebruiken voor 301, 302 en vergelijkbare omleidingen aan de clientzijde. Als een regel overeenkomt, reageert de CDN met een statusregel die de statuscode en het bericht bevat (bijvoorbeeld HTTP/1.1 301 Permanent verplaatst) en met de locatiekoptekenset.

Zowel absolute als relatieve locaties met vaste waarden zijn toegestaan.

Houd er rekening mee dat de cumulatieve grootte van het configuratiebestand, inclusief de regels voor verkeersfilters, niet groter kan zijn dan 100 kB.

Voorbeeld van configuratie:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  redirects:
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
| **redirect** | locatie | Waarde voor de koptekst &#39;Locatie&#39;. |
|     | status (optioneel, standaard is 301) | De HTTP-status die standaard moet worden gebruikt in het omleidingsbericht, is 301. De toegestane waarden zijn: 301, 302, 303, 307, 308. |

De locaties van een omleiding kunnen letterlijke tekenreeksen zijn (bijvoorbeeld https://www.example.com/page) of het resultaat van een eigenschap (bijvoorbeeld pad) die optioneel wordt getransformeerd, met de volgende syntaxis:

```
redirects:
  rules:
    - name: country-code-redirect
      when: { reqProperty: path, like: "/" }
      action:
        type: redirect
        location:
          reqProperty: clientCountry
          transform:
            - op: replace
              match: '^(.*)$'
              replacement: 'https://www.example.com/\1/home'
            - op: tolower
    - name: www-redirect
      when: { reqProperty: domain, equals: "example.com" }
      action:
        type: redirect
        location:
          reqProperty: url
          transform:
            - op: replace
              match: '^/(.*)$'
              replacement: 'https://www.example.com/\1'
```
