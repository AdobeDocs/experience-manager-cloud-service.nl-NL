---
title: Geavanceerde netwerken configureren voor AEM as a Cloud Service
description: Leer hoe te om geavanceerde voorzien van een netwerkeigenschappen zoals VPN te vormen of specifiek uitgang IP adres voor AEM as a Cloud Service
source-git-commit: e9fa68869ca92945c44a79b783fbc8a53a875e81
workflow-type: tm+mt
source-wordcount: '2797'
ht-degree: 0%

---


# Geavanceerde netwerken configureren voor AEM as a Cloud Service {#configuring-advanced-networking}

>[!INFO]
>
>De geavanceerde voorzien van een netwerkeigenschap maakt deel uit van de versie 2021.9.0, en zal voor klanten medio oktober worden toegelaten.

AEM as a Cloud Service biedt verschillende soorten geavanceerde netwerkmogelijkheden, die door klanten kunnen worden geconfigureerd met de API&#39;s van Cloud Manager. Deze omvatten:

* [Flexibele havenuitgang](#flexible-port-egress)  - vorm as a Cloud Service AEM om uitgaand verkeer uit niet-standaardhavens toe te staan
* [Het specifieke IP adres](#dedicated-egress-IP-address)  van de uitgang - vormt verkeer uit as a Cloud Service AEM om uit unieke IP voort te komen
* [Het virtuele Privé Netwerk](#vpn)  - veilig verkeer tussen de infrastructuur van een klant en AEM as a Cloud Service, voor klanten die de technologie van VPN hebben

Dit artikel beschrijft elk van deze opties in detail, met inbegrip van hoe zij kunnen worden gevormd. Als algemene configuratiestrategie, wordt het `/networkInfrastructures` API eindpunt aangehaald op het programmaniveau om het gewenste type van geavanceerd voorzien van een netwerk te verklaren, die door een vraag aan het `/advancedNetworking` eindpunt voor elk milieu wordt gevolgd om de infrastructuur toe te laten en milieu-specifieke parameters te vormen. Raadpleeg de desbetreffende eindpunten in de API-documentatie van Cloud Manager voor elke formele syntaxis, evenals voorbeeldaanvragen en reacties.

Wanneer het beslissen tussen flexibele havenuitgang en specifiek uitgangIP adres, wordt het geadviseerd u flexibele havenuitgang kiest als een specifiek IP adres niet wordt vereist omdat Adobe prestaties van flexibel havenuitgang verkeer kan optimaliseren.

>[!INFO]
>
>Geavanceerde netwerken zijn niet beschikbaar voor het sandboxprogramma.

>[!NOTE]
>
>Klanten die al beschikken over een verouderde, toegewijde egress-technologie en die een van deze opties moeten configureren, zouden dat niet moeten doen of de connectiviteit van de site kan hierdoor worden beïnvloed. Neem contact op met de Adobe-ondersteuning voor hulp.

## Flexibele poortuitgang {#flexible-port-egress}

Deze geavanceerde voorzien van een netwerkeigenschap staat u toe om AEM as a Cloud Service te vormen om verkeer door havens buiten (haven 80) en HTTPS (haven 443) te binnendringen, die door gebrek open zijn.

### Overwegingen {#flexible-port-egress-considerations}

De flexibele havenuitgang is de geadviseerde keus als u geen VPN nodig hebt en geen specifiek uitgangIP adres nodig aangezien het verkeer dat niet op een specifiek uitgang steunt hogere productie kan bereiken.

### Configuratie {#configuring-flexible-port-egress-provision}

Eenmaal per programma wordt het eindpunt van de POST `/program/<programId>/networkInfrastructures` aangeroepen, waarbij eenvoudig de waarde van `flexiblePortEgress` voor de parameter en het gebied `kind` wordt doorgegeven. Het eindpunt reageert met `network_id`, evenals andere informatie met inbegrip van de status. In de API-documenten moet naar de volledige set parameters en de exacte syntaxis worden verwezen.

Zodra geroepen, vergt het typisch ongeveer 15 minuten voor de voorzien van een netwerkinfrastructuur om worden provisioned. Een vraag aan het [milieu GET eindpunt ](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getEnvironment) van de Manager van de Wolk zou een status van &quot;klaar&quot;tonen.

Als de programma-scoped flexibele configuratie van de havenuitgang klaar is, moet het `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` eindpunt per milieu worden aangehaald om voorzien van een netwerk op het milieuniveau toe te laten en om het even welke haven door:sturen regels te verklaren. De parameters zijn configureerbaar per milieu om flexibiliteit aan te bieden.

De haven die regels door:sturen zou voor om het even welke havens buiten 80/443 moeten worden verklaard door de reeks bestemmingsgastheren (namen of IP, en met havens te specificeren). Voor elke bestemmingsgastheer, moeten de klanten de voorgenomen bestemmingshaven aan een haven van 30000 door 30999 in kaart brengen.

API zou in slechts een paar seconden moeten antwoorden, wijzend op een status van het bijwerken en na ongeveer 10 minuten, zou de methode `GET` van het eindpunt erop moeten wijzen dat het geavanceerde voorzien van een netwerk wordt toegelaten.

### Updates {#updating-flexible-port-egress-provision}

De configuratie van het programmaniveau kan worden bijgewerkt door het `PUT /api/program/<program_id>/network/<network_id>` eindpunt aan te halen en zal binnen een paar minuten van kracht worden.

>[!NOTE]
>
> De parameter &quot;kind&quot; (`flexiblePortEgress`, `dedicatedEgressIP` of `VPN`) kan niet worden gewijzigd. Neem voor hulp contact op met de klantenondersteuning en beschrijf wat er al is gemaakt en de reden voor de wijziging.

De per milieuhaven die regels door:sturen kan opnieuw worden bijgewerkt door het `PUT /program/{programId}/environment/{environmentId}/advancedNetworking` eindpunt aan te halen, ervoor zorgen om de volledige reeks configuratieparameters, eerder dan een ondergroep te omvatten.

### Het schrappen van of het onbruikbaar maken van de Flexibele Poorten {#deleting-disabling-flexible-port-egress-provision}

Om **delete** de netwerkinfrastructuur te verwijderen, dient u een ticket voor klantenondersteuning in waarin wordt beschreven wat er is gemaakt en waarom het moet worden verwijderd.

Als u **het flexibele poortegres van een bepaalde omgeving wilt uitschakelen, roept u `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()` aan.**

Zie de [Documentatie van de API voor cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration) voor meer informatie.

### Verkeer dat {#flexible-port-egress-traffic-routing}

Het verkeer van HTTP of https die naar bestemmingen door havens 80 of 443 gaan zal door een preconfigured volmacht gaan, veronderstellend de standaard het voorzien van een netwerkbibliotheek van Java wordt gebruikt. Voor HTTP of https verkeer die door andere havens gaan zou een volmacht moeten worden gevormd gebruikend de volgende eigenschappen.

* `AEM_HTTP_PROXY_HOST / AEM_HTTPS_PROXY_HOST`
* `AEM_HTTP_PROXY_PORT / AEM_HTTPS_PROXY_PORT`

Bijvoorbeeld, hier is steekproefcode om een verzoek naar `www.example.com:8443` te verzenden:

```java
HttpsHost target = new HttpsHost("example.com", 8443, "https");
 
HttpHost proxy = new HttpHost(System.getenv("AEM_HTTPS_PROXY_HOST"),
                              Integer.parseInt(System.getenv("AEM_HTTPS_PROXY_PORT")),
                              "https");
 
RequestConfig config = RequestConfig.custom().setProxy(proxy).build();
 
HttpGet request = new HttpGet("/");
request.setConfig(config);
CloseableHttpResponse response = httpclient.execute(target, request);
```

Als het gebruiken van niet-standaard het voorzien van een netwerkbibliotheken van Java, vorm volmachten gebruikend de eigenschappen hierboven, voor al verkeer.

Het niet-http/s verkeer met bestemmingen door havens die in `portForwards` worden verklaard parameter zou een bezit moeten van verwijzingen voorzien genoemd `AEM_PROXY_HOST`, samen met de in kaart gebrachte haven. Bijvoorbeeld:

```java
DriverManager.getConnection("jdbc:mysql://" + System.getenv("AEM_PROXY_HOST") + ":53306/test");
```

De lijst hieronder beschrijft verkeer dat verplettert:

<table>
<thead>
  <tr>
    <th>Verkeer</th>
    <th>Detectievoorwaarde</th>
    <th>Poort</th>
    <th>Verbinding</th>
    <th>Voorbeeld</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>HTTP- of https-protocol</b></td>
    <td>Standaard http/s-verkeer</td>
    <td>80 of 443</td>
    <td>Toegestaan</td>
    <td></td>
  </tr> 
  <tr>
    <td></td>
    <td>Niet-standaardverkeer (op andere havens buiten 80 of 443) door http volmacht die gebruikend deze omgevingsvariabelen wordt gevormd:<br><ul>
     <li>AEM_HTTP_PROXY_HOST / AEM_HTTPS_PROXY_HOST</li>
     <li>AEM_HTTP_PROXY_PORT / AEM_HTTPS_PROXY_PORT</li>
    </ul>
    <td>Poorten buiten 80 of 443</td>
    <td>Toegestaan</td>
  </tr>
  <tr>
    <td></td>
    <td>Niet-standaardverkeer (op andere havens buiten havens 80 of 443) die geen HTTP volmacht gebruiken</td>
    <td>Poorten buiten 80 of 443</td>
    <td>Geblokkeerd</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Niet-http of niet-https</b></td>
    <td>De client maakt verbinding met de omgevingsvariabele <code>AEM_PROXY_HOST</code> met behulp van een <code>portOrig</code> die is gedeclareerd in de API-parameter <code>portForwards</code>.</td>
    <td>Alle</td>
    <td>Toegestaan</td>
    <td><code>mysql.example.com:3306</code></td>
  </tr>
  <tr>
    <td></td>
    <td>Alles</td>
    <td>Alle</td>
    <td>Geblokkeerd</td>
    <td><code>db.example.com:5555</code></td>
  </tr>
</tbody>
</table>

**Configuratie Apache/Dispatcher**

De instructie `mod_proxy` van de AEM Cloud Service Apache/Dispatcher-laag kan worden geconfigureerd met de hierboven beschreven eigenschappen.

```
ProxyRemote "http://example.com" "http://${AEM_HTTP_PROXY_HOST}:${AEM_HTTP_PROXY_PORT}"
ProxyPass "/somepath" "http://example.com"
ProxyPassReverse "/somepath" "http://example.com"
```

```
SSLProxyEngine on //needed for https backends
 
ProxyRemote "https://example.com:8443" "http://${AEM_HTTPS_PROXY_HOST}:${AEM_HTTPS_PROXY_PORT}"
ProxyPass "/somepath" "https://example.com:8443"
ProxyPassReverse "/somepath" "https://example.com:8443"
```

## IP-adres van speciale egress {#dedicated-egress-IP-address}

>[!NOTE]
>
>Als u van een specifieke uitgang IP vóór de versie van September 2021 (10/6/21) bent voorzien, gelieve [Verouderde Afgewijde Klanten van het Adres van de Gastheer ](#legacy-dedicated-egress-address-customers) te verwijzen.

### Voordelen {#benefits}

Dit specifieke IP adres kan veiligheid verbeteren wanneer het integreren met verkopers SaaS (als een verkoper van CRM) of andere integratie buiten AEM as a Cloud Service die een lijst van gewenste personen van IP adressen aanbieden. Door het specifieke IP adres aan de lijst van gewenste personen toe te voegen, zorgt het ervoor dat slechts het verkeer van AEM Cloud Service van de klant wordt toegelaten om in de externe dienst te stromen. Dit is naast verkeer van om het even welke andere toegestane IPs.

Zonder de specifieke IP toegelaten adreseigenschap, verkeer dat uit AEM as a Cloud Service stromen door een reeks IPs komt die met andere klanten wordt gedeeld.

### Configuratie {#configuring-dedicated-egress-provision}

>[!INFO]
>
>Het Splunk door:sturen vermogen is niet mogelijk van een specifiek uitgangIP adres.

Het vormen van specifiek uitgang IP adres is identiek aan [flexibele havenuitgang](#configuring-flexible-port-egress-provision).

Het belangrijkste verschil is dat het verkeer altijd van specifieke, unieke IP zal weggaan. Om dat IP te vinden, gebruik een DNS resolver om het IP adres te identificeren verbonden aan `p{PROGRAM_ID}.external.adobeaemcloud.com`. Het IP adres zal naar verwachting niet veranderen, maar als het in de toekomst moet veranderen, zal het geavanceerde bericht worden verstrekt.

Naast de verpletterende regels die door flexibele havenuitgang op het `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` eindpunt worden gesteund, steunt het specifieke uitgangIP adres een `nonProxyHosts` parameter. Dit staat u toe om een reeks gastheren te verklaren die door een gedeelde IPs adreswaaier eerder dan specifieke IP zou moeten leiden, die nuttig kan zijn aangezien het verkeer dat door gedeelde IPs wordt behandeld verder kan worden geoptimaliseerd. De `nonProxyHost` URLs kan de patronen van `example.com` of `*.example.com` volgen, waar de vervangingskaart slechts bij het begin van het domein wordt gesteund.

Wanneer het beslissen tussen flexibele havenuitgang en specifiek uitgangIP adres, zouden de klanten flexibele havenuitgang moeten kiezen als een specifiek IP adres niet wordt vereist aangezien Adobe prestaties van flexibel havenuitgang verkeer kan optimaliseren.

### Verkeer dat {#dedcated-egress-ip-traffic-routing}

<table>
<thead>
  <tr>
    <th>Verkeer</th>
    <th>Doelvoorwaarde</th>
    <th>Poort</th>
    <th>Verbinding</th>
    <th>Voorbeeld</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>HTTP- of https-protocol</b></td>
    <td>Verkeer naar Azure- of Adobe-services</td>
    <td>Alle</td>
    <td>Via de gedeelde clusterIPs (niet specifieke IP)</td>
    <td>adobe.io<br>api.windows.net</td>
  </tr>
  <tr>
    <td></td>
    <td>Host die overeenkomt met de parameter <code>nonProxyHosts</code></td>
    <td>80 of 443</td>
    <td>Via de gedeelde cluster-IP's</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Host die overeenkomt met de parameter <code>nonProxyHosts</code></td>
    <td>Poorten buiten 80 of 443</td>
    <td>Geblokkeerd</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Door de volmachtsconfiguratie van http, die door gebrek voor verkeer http/s gebruikend standaard de cliëntbibliotheek van HTTP van Java wordt gevormd</td>
    <td>Alle</td>
    <td>Door specifieke uitgang IP</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Hiermee negeert u http-proxyconfiguratie (bijvoorbeeld als deze expliciet wordt verwijderd uit de standaard Java HTTP-clientbibliotheek of als een Java-bibliotheek die de standaardproxyconfiguratie negeert, wordt gebruikt)</td>
    <td>80 of 443</td>
    <td>Via de gedeelde cluster-IP's</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Hiermee negeert u http-proxyconfiguratie (bijvoorbeeld als deze expliciet wordt verwijderd uit de standaard Java HTTP-clientbibliotheek of als een Java-bibliotheek die de standaardproxyconfiguratie negeert, wordt gebruikt)</td>
    <td>Poorten buiten 80 of 443</td>
    <td>Geblokkeerd</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Niet-http of niet-https</b></td>
    <td>De client maakt verbinding met de omwentelingsvariabele <code>AEM_PROXY_HOST</code> met een <code>portOrig</code>-variabele die is gedeclareerd in de API-parameter <code>portForwards</code></td>
    <td>Alle</td>
    <td>Door specifieke uitgang IP</td>
    <td><code>mysql.example.com:3306</code></td>
  </tr>
  <tr>
    <td></td>
    <td>Alles</td>
    <td></td>
    <td>Geblokkeerd</td>
    <td></td>
  </tr>
</tbody>
</table>

## Verouderde, specifieke klanten van het Adres van de Afstuwing {#legacy-dedicated-egress-address-customers}

Als u van een specifieke uitgang IP vóór 2021.09.30 bent voorzien, zal uw specifieke uitgangIP eigenschap werken zoals hieronder beschreven.

### Functiegebruik {#feature-usage}

De functie is compatibel met Java-code of bibliotheken die resulteren in uitgaand verkeer, op voorwaarde dat deze standaard Java-systeemeigenschappen gebruiken voor proxyconfiguraties. In de praktijk moet dit ook de meest gangbare bibliotheken omvatten.

Hieronder ziet u een codevoorbeeld:

```java
public JSONObject getJsonObject(String relativePath, String queryString) throws IOException, JSONException {
  String relativeUri = queryString.isEmpty() ? relativePath : (relativePath + '?' + queryString);
  URL finalUrl = endpointUri.resolve(relativeUri).toURL();
  URLConnection connection = finalUrl.openConnection();
  connection.addRequestProperty("Accept", "application/json");
  connection.addRequestProperty("X-API-KEY", apiKey);

  try (InputStream responseStream = connection.getInputStream(); Reader responseReader = new BufferedReader(new InputStreamReader(responseStream, Charsets.UTF_8))) {
    return new JSONObject(new JSONTokener(responseReader));
  }
}
```

Sommige bibliotheken vereisen expliciete configuratie om standaard het systeemeigenschappen van Java voor volmachtsconfiguraties te gebruiken.

Een voorbeeld dat Apache HttpClient gebruikt, die expliciete vraag aan vereist
[`HttpClientBuilder.useSystemProperties()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClientBuilder.html) of gebruik
[`HttpClients.createSystem()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClients.html#createSystem()):

```java
public JSONObject getJsonObject(String relativePath, String queryString) throws IOException, JSONException {
  String relativeUri = queryString.isEmpty() ? relativePath : (relativePath + '?' + queryString);
  URL finalUrl = endpointUri.resolve(relativeUri).toURL();

  HttpClient httpClient = HttpClientBuilder.create().useSystemProperties().build();
  HttpGet request = new HttpGet(finalUrl.toURI());
  request.setHeader("Accept", "application/json");
  request.setHeader("X-API-KEY", apiKey);
  HttpResponse response = httpClient.execute(request);
  String result = EntityUtils.toString(response.getEntity());
}
```

Het zelfde specifieke IP wordt toegepast op alle programma&#39;s van een klant in hun organisatie van de Adobe en voor alle milieu&#39;s in elk van hun programma&#39;s. Deze is van toepassing op zowel auteur- als publicatieservices.

Alleen HTTP- en HTTPS-poorten worden ondersteund. Dit omvat HTTP/1.1 en HTTP/2 wanneer gecodeerd.

### Foutopsporingsoverwegingen {#debugging-considerations}

Om te bevestigen dat het verkeer inderdaad op het verwachte specifieke IP adres uitgaande is, controlelogboeken in de bestemmingsdienst, als beschikbaar. Anders, kan het nuttig zijn om aan de het zuiveren dienst zoals [https://ifconfig.me/IP](https://ifconfig.me/IP) te roepen, die het roepende IP adres zal terugkeren.

## Virtual Private Network (VPN) {#vpn}

VPN staat voor het verbinden met een infrastructuur op-gebouw of datacenter van auteur, publiceren, of voorproef toe. Bijvoorbeeld voor de manier om tot een gegevensbestand toegang te hebben.

Het staat ook het Verbinden met verkopers SaaS zoals een verkoper van CRM toe die VPN steunt of het verbinden van een collectief netwerk met AEM as a Cloud Service auteur, voorproef, of publiceert.

De meeste apparaten van VPN met technologie IPSec worden gesteund. Raadpleeg de lijst met apparaten op [deze pagina](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-devices#devicetable), op basis van de informatie in de **RouteBased configuratieinstructies** kolom. Configureer het apparaat zoals beschreven in de tabel.

### Algemene overwegingen {#general-vpn-considerations}

* De steun wordt beperkt tot één enkele verbinding van VPN
* Het Splunk door:sturen vermogen is niet mogelijk over een verbinding van VPN.

### Maken {#vpn-creation}

Eenmaal per programma, wordt het eindpunt van de POST `/program/<programId>/networkInfrastructures` aangehaald, die in een lading van configuratieinformatie overgaat die omvat: de waarde van &quot;vpn&quot;voor de `kind` parameter, het gebied, de adresruimte (lijst van CIDRs - merk op dat dit niet later kan worden gewijzigd), DNS oplossers (voor het oplossen van namen in het netwerk van de klant), en de verbindingsinformatie van VPN zoals gatewayconfiguratie, gedeelde sleutel van VPN, en het IP Veiligheidsbeleid. Het eindpunt reageert met `network_id`, evenals andere informatie met inbegrip van de status. Naar de volledige set parameters en de exacte syntaxis moet worden verwezen in de [API-documentatie](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure).

Zodra geroepen, zal het typisch tussen 45 en 60 minuten voor de voorzien van een netwerkinfrastructuur duren. De methode van de GET van de API kan worden geroepen om de huidige status terug te keren, die uiteindelijk van `creating` aan `ready` zal draaien. Raadpleeg de API-documentatie voor alle staten.

Als de programma-scoped configuratie van VPN in klaar, het `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` eindpunt per milieu moet worden aangehaald om voorzien van een netwerk op het milieuniveau toe te laten en om het even welke haven te verklaren door:sturen regels. De parameters zijn configureerbaar per milieu om flexibiliteit aan te bieden.

Zie de [API documentatie](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/enableEnvironmentAdvancedNetworkingConfiguration) voor meer informatie.

De haven die regels door:sturen zou voor om het even welk niet-http/s protocolTCP verkeer moeten worden verklaard dat door VPN zou moeten worden verpletterd door de reeks bestemmingsgastheren (namen of IP, en met havens) te specificeren. Voor elke bestemmingsgastheer, moeten de klanten de voorgenomen bestemmingshaven aan een haven van 30000 tot 30999 in kaart brengen, waar de waarden over milieu&#39;s in het programma uniek moeten zijn. De klanten kunnen een reeks van url in de `nonProxyHosts` parameter ook een lijst maken, die URL verklaart waarvoor het verkeer het verpletteren van VPN zou moeten omzeilen, maar in plaats daarvan door een gedeelde IP waaier. De methode volgt de patronen van `example.com` of `*.example.com`, waarbij het jokerteken alleen aan het begin van het domein wordt ondersteund.

De API zou in slechts een paar seconden moeten antwoorden, wijzend op een status van `updating` en na ongeveer 10 minuten, zou een vraag aan het milieu GET van de Manager van de Wolk een status van `ready` tonen, erop wijzend dat de update aan het milieu is toegepast.

Merk op dat zelfs als er geen milieuverkeer is dat regels (gastheren of omwegen) verplettert, `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` nog moet worden geroepen, enkel met een lege lading.

### VPN bijwerken {#updating-the-vpn}

De programma-vlakke configuratie van VPN kan worden bijgewerkt door het `PUT /api/program/<program_id>/network/<network_id>` eindpunt aan te halen.

Merk op dat de adresruimte niet na de aanvankelijke levering van VPN kan worden veranderd. Neem indien nodig contact op met de klantenondersteuning. Daarnaast kan de parameter `kind` (`flexiblePortEgress`, `dedicatedEgressIP` of `VPN`) niet worden gewijzigd. Neem voor hulp contact op met de klantenondersteuning en beschrijf wat er al is gemaakt en de reden voor de wijziging.

De per-milieu verpletterende regels kunnen worden bijgewerkt door het `PUT /program/{programId}/environment/{environmentId}/advancedNetworking` eindpunt opnieuw aan te halen, ervoor zorgen om de volledige reeks configuratieparameter, eerder dan een ondergroep te omvatten. Het duurt doorgaans 5 tot 10 minuten om omgevingsupdates toe te passen.

### Het schrappen van of het onbruikbaar maken van VPN {#deleting-or-disabling-the-vpn}

Om de netwerkinfrastructuur te schrappen, leg een kaartje van de klantensteun voor, beschrijvend wat is gecreeerd en waarom het moet worden geschrapt.

Om VPN voor een bepaald milieu onbruikbaar te maken, haal `DELETE /program/{programId}/environment/{environmentId}/advancedNetworking` aan. Meer informatie in de [API documentatie](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

### Verkeer dat {#vpn-traffic-routing}

De lijst beschrijft hieronder verkeer dat verplettert.

<table>
<thead>
  <tr>
    <th>Verkeer</th>
    <th>Doelvoorwaarde</th>
    <th>Poort</th>
    <th>Verbinding</th>
    <th>Voorbeeld</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>HTTP- of https-protocol</b></td>
    <td>Verkeer naar Azure- of Adobe-services</td>
    <td>Alle</td>
    <td>Via de gedeelde clusterIPs (niet specifieke IP)</td>
    <td>adobe.io<br>api.windows.net</td>
  </tr>
  <tr>
    <td></td>
    <td>Host die overeenkomt met de parameter <code>nonProxyHosts</code></td>
    <td>80 of 443</td>
    <td>Via de gedeelde cluster-IP's</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Host die overeenkomt met de parameter <code>nonProxyHosts</code></td>
    <td>Poorten buiten 80 of 443</td>
    <td>Geblokkeerd</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Als IP in de <i>de gatewayadres van VPN </i> ruimtewaaier, en door de volmachtsconfiguratie van http valt (die door gebrek voor verkeer http/s gebruikend standaard de cliëntbibliotheek van HTTP van Java wordt gevormd)</td>
    <td>Alle</td>
    <td>Door VPN</td>
    <td><code>10.0.0.1:443</code>Het kan ook een hostname zijn.</td>
  </tr>
  <tr>
    <td></td>
    <td>Als IP niet in de <i>waaier van het gatewayadres van VPN </i> valt, en door de volmachtsconfiguratie van http (die door gebrek voor verkeer http/s gebruikend standaard de cliëntbibliotheek van HTTP van Java wordt gevormd)</td>
    <td>Alle</td>
    <td>Door specifieke uitgang IP</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Hiermee negeert u http-proxyconfiguratie (bijvoorbeeld als deze expliciet wordt verwijderd uit de standaard Java HTTP-clientbibliotheek of als Java-bibliotheek wordt gebruikt die de standaardproxyconfiguratie negeert)
</td>
    <td>80 of 443</td>
    <td>Via de gedeelde cluster-IP's</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Hiermee negeert u http-proxyconfiguratie (bijvoorbeeld als deze expliciet wordt verwijderd uit de standaard Java HTTP-clientbibliotheek of als Java-bibliotheek wordt gebruikt die de standaardproxyconfiguratie negeert)</td>
    <td>Poorten buiten 80 of 443</td>
    <td>Geblokkeerd</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Niet-http of niet-https</b></td>
    <td>Als het IP in de <i>bereik van het de gatewayadres van VPN </i> valt en de cliënt verbindt met <code>AEM_PROXY_HOST</code> env variabele gebruikend <code>portOrig</code> gedeclareerd in de <code>portForwards</code> API parameter</td>
    <td>Alle</td>
    <td>Door VPN</td>
    <td><code>10.0.0.1:3306</code>Het kan ook een hostname zijn.</td>
  </tr>
  <tr>
    <td></td>
    <td>Als IP niet in de <i>gateway van VPN adresruimte</i> waaier valt en de cliënt verbindt met <code>AEM_PROXY_HOST</code> env variabele gebruikend <code>portOrig</code> gedeclareerd in de <code>portForwards</code> API parameter</td>
    <td>Alle</td>
    <td>Door specifieke uitgang IP</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Alles</td>
    <td>Alle</td>
    <td>Geblokkeerd</td>
    <td></td>
  </tr>
</tbody>
</table>

### Nuttige domeinen voor configuratie{#vpn-useful-domains-for-configuration}

Het hieronder diagram verstrekt een visuele vertegenwoordiging van een reeks domeinen en bijbehorende IPs die voor configuratie en ontwikkeling nuttig zijn. De lijst verder onder het diagram beschrijft die domeinen en IPs.

![VPN-domeinconfiguratie](/help/security/assets/AdvancedNetworking.jpg)

<table>
<thead>
  <tr>
    <th>Domeinpatroon</th>
    <th>Onder "AEM" wordt verstaan:</th>
    <th>Ingress (naar AEM) betekent</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><code>p{PROGRAM_ID}.external.adobeaemcloud.com</code></td>
    <td>Specifiek IP van de uitgang adres voor verkeer dat naar Internet eerder dan door privé netwerken gaat </td>
    <td>De verbindingen van VPN zouden bij CDN zoals komend van dit IP tonen. Om verbindingen van VPN slechts toe te staan om in AEM te gaan, vorm de Manager van de Wolk om dit IP slechts toe te staan en alles anders te blokkeren. Zie de "Beperk toegang tot de verbindingen van VPN"sectie voor meer details.</td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}-gateway.external.adobeaemcloud.com</code></td>
    <td>N.v.t.</td>
    <td>IP van de gateway van VPN op de AEM kant. Het team van de het netwerktechniek van een klant kan dit gebruiken om slechts de verbindingen van VPN aan hun gateway van VPN van een specifiek IP adres toe te staan. </td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}.inner.adobeaemcloud.net</code></td>
    <td>IP van verkeer dat van de AEM kant van VPN aan de klantenkant komt. Dit kan in de configuratie van de klant worden gevoegd op lijst van gewenste personen om ervoor te zorgen dat de verbindingen slechts van AEM kunnen worden gemaakt.</td>
    <td>Als de klant slechts de toegang van VPN tot AEM wil toestaan, zouden zij DNS CNAME ingangen moeten vormen om <code>author-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> en/of <code>publish-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> aan dit in kaart te brengen.</td>
  </tr>
</tbody>
</table>

### VPN beperken tot Ingress-verbindingen {#restrict-vpn-to-ingress-connections}

Als u slechts de toegang van VPN tot AEM wilt toestaan, kunnen de milieu lijsten van gewenste personen in de Manager van de Wolk worden gevormd zodat slechts IP door `p{PROGRAM_ID}.external.adobeaemcloud.com` wordt bepaald om met het milieu te spreken. Dit kan op dezelfde manier als elke andere op IP gebaseerde lijst van gewenste personen in de Manager van de Wolk worden gedaan.

Als de regels op weg-gebaseerd moeten zijn, gebruik standaardHTTP richtlijnen op het verzendersniveau om bepaalde IPs te ontkennen of toe te staan. Zij zouden ervoor moeten zorgen dat de gewenste wegen bij CDN ook niet cacheable zijn zodat het verzoek altijd aan oorsprong krijgt.

**Voorbeeld van HTTP-configuratie**

```
Order deny,allow
Deny from all
Allow from 192.168.0.1
Header always set Cache-Control private
```

## Overgang tussen de Geavanceerde Types van Voorzien van een netwerk {#transitioning-between-advanced-networking-types}

Aangezien de parameter `kind` niet kan worden gewijzigd, kunt u contact opnemen met de klantenondersteuning voor assistentie en beschrijven wat al is gemaakt en de reden voor de wijziging.