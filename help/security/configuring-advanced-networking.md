---
title: Geavanceerde netwerken configureren voor AEM as a Cloud Service
description: Leer hoe te om geavanceerde voorzien van een netwerkeigenschappen zoals VPN of een flexibel of specifiek adres van uitgangIP voor AEM as a Cloud Service te vormen
exl-id: 968cb7be-4ed5-47e5-8586-440710e4aaa9
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '3594'
ht-degree: 0%

---

# Geavanceerde netwerken configureren voor AEM as a Cloud Service {#configuring-advanced-networking}

Dit artikel is bedoeld om u aan de verschillende geavanceerde voorzien van een netwerkeigenschappen in AEM as a Cloud Service, met inbegrip van zelf-serverlevering van VPN, niet-standaardhavens, en specifieke uitgangIP adressen te introduceren.

>[!INFO]
>
>U kunt ook een reeks artikelen vinden die zijn ontworpen om u door elk van de geavanceerde voorzien van een netwerkopties bij dit te laten lopen [locatie](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=en).

## Overzicht {#overview}

AEM as a Cloud Service biedt verschillende soorten geavanceerde netwerkmogelijkheden, die door klanten kunnen worden geconfigureerd met de API&#39;s van Cloud Manager. Deze omvatten:

* [Flexibele poortuitgang](#flexible-port-egress) - vorm as a Cloud Service AEM om uitgaand verkeer uit niet-standaardhavens toe te staan
* [IP-adres van specifiek egress](#dedicated-egress-IP-address) - vorm verkeer uit AEM as a Cloud Service om uit unieke IP voort te komen
* [Virtual Private Network (VPN)](#vpn) - veilig verkeer tussen de infrastructuur van een klant en AEM as a Cloud Service, voor klanten die de technologie van VPN hebben

Dit artikel beschrijft elk van deze opties in detail, met inbegrip van hoe zij kunnen worden gevormd. Als algemene configuratiestrategie `/networkInfrastructures` Het API eindpunt wordt aangehaald op het programmaniveau om het gewenste type van geavanceerd voorzien van een netwerk te verklaren, dat door een vraag aan het `/advancedNetworking` eindpunt voor elke milieu om de infrastructuur toe te laten en milieu-specifieke parameters te vormen. Verwijs naar de desbetreffende eindpunten in de API-documentatie van Cloud Manager voor elke formele syntaxis en naar voorbeeldaanvragen en -antwoorden.

Een programma kan één enkele geavanceerde voorzien van een netwerkvariatie verstrekken. Wanneer het beslissen tussen flexibele havenuitgang en specifiek uitgangIP adres, wordt het geadviseerd u flexibele havenuitgang kiest als een specifiek IP adres niet wordt vereist omdat de Adobe prestaties van flexibel havenuitgang verkeer kan optimaliseren.

>[!INFO]
>
>Geavanceerde netwerken zijn niet beschikbaar voor het sandboxprogramma.
>Bovendien moeten omgevingen worden geüpgraded naar AEM versie 5958 of hoger.

>[!NOTE]
>
>Klanten die al beschikken over een verouderde, toegewijde egress-technologie en die een van deze opties moeten configureren, zouden dat niet moeten doen of de connectiviteit van de site kan hierdoor worden beïnvloed. Neem contact op met de ondersteuning van de Adobe.

## Flexibele poortuitgang {#flexible-port-egress}

Deze geavanceerde voorzien van een netwerkeigenschap laat u AEM as a Cloud Service vormen om verkeer door havens buiten (haven 80) en HTTPS (haven 443) te binnendringen, die door gebrek open zijn.

### Overwegingen {#flexible-port-egress-considerations}

De flexibele havenuitgang is de geadviseerde keus als u geen VPN nodig hebt en geen specifiek uitgangIP adres nodig aangezien het verkeer dat niet op een specifiek uitgang steunt hogere productie kan bereiken.

### Configuratie {#configuring-flexible-port-egress-provision}

Eenmaal per programma, de POST `/program/<programId>/networkInfrastructures` eindpunt wordt aangehaald, eenvoudig overgaand de waarde van `flexiblePortEgress` voor de `kind` parameter en regio. Het eindpunt reageert met het `network_id`en andere informatie, waaronder de status. De volledige set parameters en de exacte syntaxis en belangrijke informatie zoals welke parameters later niet kunnen worden gewijzigd, [kan worden verwezen in de API-documenten.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)

Eenmaal geroepen, duurt het typisch ongeveer 15 minuten voor de voorzien van een netwerkinfrastructuur. Een oproep aan de Cloud Manager [GET netwerkinfrastructuur](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getNetworkInfrastructure) zou de status &quot;ready&quot; aangeven.

Als de programma-scoped flexibele configuratie van de havenuitgang klaar is, `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` het eindpunt moet per milieu worden aangehaald om voorzien van een netwerk op het milieuniveau toe te laten en naar keuze om het even welke haven te verklaren die regels door:sturen. De parameters zijn configureerbaar per milieu om flexibiliteit aan te bieden.

De haven die regels door:sturen zou voor om het even welke bestemmingshavens buiten 80/443, maar slechts als het gebruiken van het protocol van http of https, door de reeks bestemmingsgastheren (namen of IP, en met havens) te specificeren moeten worden verklaard. De cliëntverbinding die haven 80/443 over http/https gebruikt moet volmachtsmontages in hun verbinding nog gebruiken om de eigenschappen van geavanceerd voorzien van een netwerk toe te passen op de verbinding. Voor elke bestemmingsgastheer, moeten de klanten de voorgenomen bestemmingshaven aan een haven van 30000 door 30999 in kaart brengen.

De API moet binnen een paar seconden reageren. Dit geeft aan dat het bijwerken is voltooid en dat het eindpunt na ongeveer 10 minuten `GET` de methode zou erop moeten wijzen dat het geavanceerde voorzien van een netwerk wordt toegelaten.

### Updates {#updating-flexible-port-egress-provision}

De configuratie op programmaniveau kan worden bijgewerkt door de `PUT /api/program/<program_id>/network/<network_id>` en zal binnen een paar minuten van kracht worden.

>[!NOTE]
>
> De parameter &quot;kind&quot; (`flexiblePortEgress`, `dedicatedEgressIP` of `VPN`) kan niet worden gewijzigd. Neem voor hulp contact op met de klantenondersteuning en beschrijf wat er al is gemaakt en de reden voor de wijziging.

De per milieuhaven die regels door:sturen kan opnieuw worden bijgewerkt door opnieuw het aanhalen van `PUT /program/{programId}/environment/{environmentId}/advancedNetworking` eindpunt, ervoor zorgen om de volledige reeks configuratieparameters, eerder dan een ondergroep te omvatten.

### Flexibele poortuitgang uitschakelen {#disabling-flexible-port-egress-provision}

Naar **disable** flexibele havenuitgang uit een bepaalde omgeving, roep `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()`.

Zie voor meer informatie over de API&#39;s de [Documentatie voor API voor cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

### Verkeer dat {#flexible-port-egress-traffic-routing}

Voor HTTP of https verkeer die naar havens buiten 80 of 443 gaan zou een volmacht moeten worden gevormd gebruikend de volgende gastheer en havenmilieuvariabelen:

* voor HTTP: `AEM_PROXY_HOST` / `AEM_HTTP_PROXY_PORT ` (standaard `proxy.tunnel:3128` AEM lozingen &lt; 6094)
* voor HTTPS: `AEM_PROXY_HOST` / `AEM_HTTPS_PROXY_PORT ` (standaard `proxy.tunnel:3128` AEM lozingen &lt; 6094)

Hier ziet u bijvoorbeeld een voorbeeldcode voor het verzenden van een aanvraag naar `www.example.com:8443`:

```java
String url = "www.example.com:8443"
String proxyHost = System.getenv().getOrDefault("AEM_PROXY_HOST", "proxy.tunnel");
int proxyPort = Integer.parseInt(System.getenv().getOrDefault("AEM_HTTPS_PROXY_PORT", "3128"));
HttpClient client = HttpClient.newBuilder()
      .proxy(ProxySelector.of(new InetSocketAddress(proxyHost, proxyPort)))
      .build();
 
HttpRequest request = HttpRequest.newBuilder().uri(URI.create(url)).build();
HttpResponse<String> response = client.send(request, BodyHandlers.ofString());
```

Als het gebruiken van niet-standaard het voorzien van een netwerkbibliotheken van Java, vorm volmachten gebruikend de eigenschappen hierboven, voor al verkeer.

Niet-http/s verkeer met bestemmingen door havens die in worden verklaard `portForwards` parameter moet verwijzen naar een eigenschap met de naam `AEM_PROXY_HOST`en de toegewezen poort. Bijvoorbeeld:

```java
DriverManager.getConnection("jdbc:mysql://" + System.getenv("AEM_PROXY_HOST") + ":53306/test");
```

De lijst hieronder beschrijft verkeer dat verplettert:

<table>
<thead>
  <tr>
    <th>Verkeer</th>
    <th>Doelvoorwaarde</th>
    <th>Poort</th>
    <th>Verbinding</th>
    <th>Voorbeeld van externe bestemming</th>
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
    <td>Niet-standaardverkeer (op andere havens buiten 80 of 443) door http volmacht die gebruikend de volgende omgevingsvariabele en het aantal van de volmachtshaven wordt gevormd. Declareer niet de bestemmingshaven in de de vraag portForwards van de API van de Manager van de Wolk parameter:<br><ul>
     <li>AEM_PROXY_HOST (gebrek aan ` proxy.tunnel ` in AEM versies &lt; 6094)</li>
     <li>AEM_HTTPS_PROXY_PORT (standaard poort 3128 in AEM releases &lt; 6094)</li>
    </ul>
    <td>Poorten buiten 80 of 443</td>
    <td>Toegestaan</td>
    <td>example.com:8443</td>
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
    <td>Client maakt verbinding met de <code>AEM_PROXY_HOST</code> omgevingsvariabele die een <code>portOrig</code> gedeclareerd in de <code>portForwards</code> API-parameter.</td>
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

De AEM Cloud Service Apache/Dispatcher-laag `mod_proxy` de richtlijn kan worden gevormd gebruikend de hierboven beschreven eigenschappen.

```
ProxyRemote "http://example.com:8080" "http://${AEM_PROXY_HOST}:3128"
ProxyPass "/somepath" "http://example.com:8080"
ProxyPassReverse "/somepath" "http://example.com:8080"
```

```
SSLProxyEngine on //needed for https backends
 
ProxyRemote "https://example.com:8443" "http://${AEM_PROXY_HOST}:3128"
ProxyPass "/somepath" "https://example.com:8443"
ProxyPassReverse "/somepath" "https://example.com:8443"
```

## IP-adres van speciale egress {#dedicated-egress-IP-address}

>[!NOTE]
>
>Als u van een specifieke uitgang IP vóór de versie van september 2021 (10/6/21) bent voorzien, zie [Verouderde, specifieke klanten van het Adres van de Afstuwing](#legacy-dedicated-egress-address-customers).

### Voordelen {#benefits}

Dit specifieke IP adres kan veiligheid verbeteren wanneer het integreren met verkopers SaaS (als een verkoper van CRM) of andere integratie buiten AEM as a Cloud Service die een lijst van gewenste personen van IP adressen aanbieden. Door het specifieke IP adres aan de lijst van gewenste personen toe te voegen, zorgt het ervoor dat slechts het verkeer van AEM Cloud Service van de klant wordt toegelaten om in de externe dienst te stromen. Dit is naast verkeer van om het even welke andere toegestane IPs.

Zonder de specifieke IP toegelaten adreseigenschap, verkeer dat uit AEM as a Cloud Service stromen door een reeks IPs komt die met andere klanten wordt gedeeld.

### Configuratie {#configuring-dedicated-egress-provision}

>[!INFO]
>
>Het Splunk door:sturen vermogen is niet mogelijk van een specifiek uitgangIP adres.

Het vormen van specifiek uitgang IP adres is identiek aan [flexibel poortbereik](#configuring-flexible-port-egress-provision).

Het belangrijkste verschil is dat het verkeer altijd van specifieke, unieke IP zal weggaan. Om dat IP te vinden, gebruik een DNS resolver om het IP adres te identificeren verbonden aan `p{PROGRAM_ID}.external.adobeaemcloud.com`. Het IP adres wordt verwacht niet te veranderen, maar als het in de toekomst moet veranderen, wordt het geavanceerde bericht verstrekt.

Naast de verpletterende regels die door flexibele havenuitgang in worden gesteund `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` eindpunt, specifiek uitgangIP adres steunt a `nonProxyHosts` parameter. Dit laat u een reeks gastheren verklaren die door een gedeelde IPs adreswaaier eerder dan specifieke IP zou moeten leiden, die nuttig kan zijn aangezien het verkeer dat door gedeelde IPs wordt behandeld verder kan worden geoptimaliseerd. De `nonProxyHost` URL&#39;s kunnen de patronen volgen van `example.com` of `*.example.com`, waarbij het jokerteken alleen wordt ondersteund aan het begin van het domein.

Wanneer het beslissen tussen flexibele havenuitgang en specifiek uitgangIP adres, zouden de klanten flexibele havenuitgang moeten kiezen als een specifiek IP adres niet wordt vereist aangezien de Adobe prestaties van flexibel havenuitgang verkeer kan optimaliseren.

### Het onbruikbaar maken van toegewezen IP van de Eis Adres {#disabling-dedicated-egress-IP-address}

Naar **disable** Het specifieke IP van de Eis Adres van een bepaald milieu, haalt aan `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()`.

Zie voor meer informatie over de API&#39;s de [Documentatie voor API voor cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

### Verkeer dat {#dedcated-egress-ip-traffic-routing}

Het HTTP- of https-verkeer zal door een vooraf geconfigureerde proxy gaan, op voorwaarde dat deze standaard Java-systeemeigenschappen voor proxyconfiguraties gebruiken.

Niet-http/s verkeer met bestemmingen door havens die in worden verklaard `portForwards` parameter moet verwijzen naar een eigenschap met de naam `AEM_PROXY_HOST`en de toegewezen poort. Bijvoorbeeld:

```java
DriverManager.getConnection("jdbc:mysql://" + System.getenv("AEM_PROXY_HOST") + ":53306/test");
```

<table>
<thead>
  <tr>
    <th>Verkeer</th>
    <th>Doelvoorwaarde</th>
    <th>Poort</th>
    <th>Verbinding</th>
    <th>Voorbeeld van externe bestemming</th>
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
    <td>Host die overeenkomt met <code>nonProxyHosts</code> parameter</td>
    <td>80 of 443</td>
    <td>Via de gedeelde cluster-IP's</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Host die overeenkomt met <code>nonProxyHosts</code> parameter</td>
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
    <td>De client maakt verbinding met <code>AEM_PROXY_HOST</code> env-variabele met een <code>portOrig</code> gedeclareerd in de <code>portForwards</code> API-parameter</td>
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

## Functiegebruik {#feature-usage}

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

### Foutopsporingsoverwegingen {#debugging-considerations}

Om te bevestigen dat het verkeer inderdaad op het verwachte specifieke IP adres, controlelogboeken binnen de bestemmingsdienst, als beschikbaar gaat. Anders, kan het nuttig zijn om aan de het zuiveren dienst zoals te roepen [https://ifconfig.me/IP](https://ifconfig.me/IP), die het roepende IP adres zal terugkeren.

## Verouderde, specifieke klanten van het Adres van de Afstuwing {#legacy-dedicated-egress-address-customers}

Als u van een specifieke uitgang IP vóór 2021.09.30 bent voorzien, steunt uw specifieke uitgangIP eigenschap slechts havens HTTP en HTTPS.
Dit omvat HTTP/1.1 en HTTP/2 wanneer gecodeerd. Ook, kan één specifiek uitgang eindpunt met om het even welk doel slechts over HTTP/HTTPS op havens 80/443 spreken respectievelijk.

## Virtual Private Network (VPN) {#vpn}

VPN staat voor het verbinden met een infrastructuur op-gebouw of datacenter van auteur, publiceren, of voorproef toe. Bijvoorbeeld voor de manier om tot een gegevensbestand toegang te hebben.

Het staat ook het Verbinden met verkopers SaaS zoals een verkoper van CRM toe die VPN steunt of het verbinden van een collectief netwerk met AEM as a Cloud Service auteur, voorproef, of publiceert.

De meeste apparaten van VPN met technologie IPSec worden gesteund. Raadpleeg de lijst met apparaten op [deze pagina](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-devices#devicetable)op basis van de informatie in de **RouteBased-configuratieinstructies** kolom. Configureer het apparaat zoals beschreven in de tabel.

### Algemene overwegingen {#general-vpn-considerations}

* De steun wordt beperkt tot één enkele verbinding van VPN
* Het Splunk door:sturen vermogen is niet mogelijk over een verbinding van VPN.

### Maken {#vpn-creation}

Eenmaal per programma, de POST `/program/<programId>/networkInfrastructures` het eindpunt wordt aangehaald, die in een lading van configuratieinformatie overgaan met inbegrip van: de waarde van &quot;vpn&quot;voor &quot;vpn&quot;voor `kind` parameter, gebied, adresruimte (lijst van CIDRs - merk op dat dit niet later kan worden gewijzigd), DNS oplossers (voor het oplossen van namen in het netwerk van de klant), en de verbindingsinformatie van VPN zoals gatewayconfiguratie, gedeelde sleutel van VPN, en het IP Veiligheidsbeleid. Het eindpunt reageert met het `network_id`en andere informatie, waaronder de status. Naar de volledige set parameters en de exacte syntaxis moet worden verwezen in de [API-documentatie](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure).

Zodra geroepen, zal het typisch tussen 45 en 60 minuten voor de voorzien van een netwerkinfrastructuur duren. De methode van de GET van de API kan worden geroepen om de huidige status terug te keren, die uiteindelijk zal draaien van `creating` tot `ready`. Raadpleeg de API-documentatie voor alle staten.

Als de programma-scoped configuratie van VPN in klaar is, `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` het eindpunt moet per milieu worden aangehaald om voorzien van een netwerk op het milieuniveau toe te laten en om het even welke haven te verklaren door:sturen regels. De parameters zijn configureerbaar per milieu om flexibiliteit aan te bieden.

Zie de [API-documentatie](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/enableEnvironmentAdvancedNetworkingConfiguration) voor meer informatie .

De haven die regels door:sturen zou voor om het even welk niet-http/s protocolTCP verkeer moeten worden verklaard dat door VPN zou moeten worden verpletterd door de reeks bestemmingsgastheren (namen of IP, en met havens) te specificeren. Voor elke bestemmingsgastheer, moeten de klanten de voorgenomen bestemmingshaven aan een haven van 30000 tot 30999 in kaart brengen, waar de waarden over milieu&#39;s in het programma uniek moeten zijn. Klanten kunnen ook een set URL&#39;s weergeven in het dialoogvenster `nonProxyHosts` parameter, die URL verklaart waarvoor het verkeer VPN zou moeten mijden verpletterend, maar in plaats daarvan door een gedeelde IP waaier. Het volgt de patronen van `example.com` of `*.example.com`, waarbij het jokerteken alleen wordt ondersteund aan het begin van het domein.

De API moet binnen een paar seconden reageren, wat een status aangeeft van `updating` en na ongeveer 10 minuten, zou een vraag aan het milieu GET van de Manager van de Wolk een status van tonen `ready`, die aangeeft dat de update van de omgeving is toegepast.

Merk op dat zelfs als er geen milieuverkeer is dat regels (gastheren of bypasses) verplettert, `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` moet nog worden geroepen, enkel met een lege lading.

### VPN bijwerken {#updating-the-vpn}

De programma-vlakke configuratie van VPN kan worden bijgewerkt door het aanhalen van `PUT /api/program/<program_id>/network/<network_id>` eindpunt.

De adresruimte kan niet na de aanvankelijke levering van VPN worden veranderd. Neem indien nodig contact op met de klantenondersteuning. Bovendien `kind` parameter (`flexiblePortEgress`, `dedicatedEgressIP` of `VPN`) kan niet worden gewijzigd. Neem voor hulp contact op met de klantenondersteuning en beschrijf wat er al is gemaakt en de reden voor de wijziging.

Het per-milieu dat regels verplettert kan worden bijgewerkt door opnieuw het aanhalen van `PUT /program/{programId}/environment/{environmentId}/advancedNetworking` eindpunt, ervoor zorgen om de volledige reeks configuratieparameter, eerder dan een ondergroep te omvatten. Het duurt doorgaans 5 tot 10 minuten om omgevingsupdates toe te passen.

### Het onbruikbaar maken VPN {#disabling-the-vpn}

Om VPN voor een bepaald milieu onbruikbaar te maken, roep aan `DELETE /program/{programId}/environment/{environmentId}/advancedNetworking`. Meer informatie in het dialoogvenster [API-documentatie](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

### Verkeer dat {#vpn-traffic-routing}

De lijst beschrijft hieronder verkeer dat verplettert.

<table>
<thead>
  <tr>
    <th>Verkeer</th>
    <th>Doelvoorwaarde</th>
    <th>Poort</th>
    <th>Verbinding</th>
    <th>Voorbeeld van externe bestemming</th>
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
    <td>Host die overeenkomt met <code>nonProxyHosts</code> parameter</td>
    <td>80 of 443</td>
    <td>Via de gedeelde cluster-IP's</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Host die overeenkomt met <code>nonProxyHosts</code> parameter</td>
    <td>Poorten buiten 80 of 443</td>
    <td>Geblokkeerd</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Als het OT in <i>VPN-gatewayadres</i> ruimtewaaier, en door de volmachtsconfiguratie van http (die door gebrek voor verkeer http/s gebruikend standaard de cliëntbibliotheek van HTTP van Java wordt gevormd)</td>
    <td>Alle</td>
    <td>Door VPN</td>
    <td><code>10.0.0.1:443</code><br>Het kan ook een hostname zijn.</td>
  </tr>
  <tr>
    <td></td>
    <td>Als het OT niet in het <i>VPN-gatewayadresruimte</i> waaier, en door de volmachtsconfiguratie van http (die door gebrek voor verkeer http/s gebruikend standaard de cliëntbibliotheek van HTTP van Java wordt gevormd)</td>
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
    <td>Als het OT in <i>VPN-gatewayadresruimte</i> bereik en de client maakt verbinding met <code>AEM_PROXY_HOST</code> env-variabele met een <code>portOrig</code> gedeclareerd in de <code>portForwards</code> API-parameter</td>
    <td>Alle</td>
    <td>Door VPN</td>
    <td><code>10.0.0.1:3306</code><br>Het kan ook een hostname zijn.</td>
  </tr>
  <tr>
    <td></td>
    <td>Als het OT niet in het <i>VPN-gatewayadresruimte</i> bereik en clientverbinding met <code>AEM_PROXY_HOST</code> env-variabele met een <code>portOrig</code> gedeclareerd in de <code>portForwards</code> API-parameter</td>
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
    <td><code>p{PROGRAM_ID}.{REGION}-gateway.external.adobeaemcloud.com</code></td>
    <td>NVT</td>
    <td>IP van de gateway van VPN op de AEM kant. Het team van de het netwerktechniek van een klant kan dit gebruiken om slechts de verbindingen van VPN aan hun gateway van VPN van een specifiek IP adres toe te staan. </td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}.{REGION}.inner.adobeaemcloud.net</code></td>
    <td>IP van verkeer dat van de AEM kant van VPN aan de klantenkant komt. Dit kan in de configuratie van de klant worden gevoegd op lijst van gewenste personen om ervoor te zorgen dat de verbindingen slechts van AEM kunnen worden gemaakt.</td>
    <td>Als de klant de toegang van VPN tot AEM wil toestaan, zouden zij DNS CNAME ingangen moeten vormen om hun douanedomein en/of in kaart te brengen <code>author-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> en/of <code>publish-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> en dit.</td>
  </tr>
</tbody>
</table>

### VPN beperken tot Ingress-verbindingen {#restrict-vpn-to-ingress-connections}

Als u slechts de toegang van VPN tot AEM wilt toestaan, kunnen de milieu lijsten van gewenste personen in de Manager van de Wolk worden gevormd zodat slechts IP door wordt bepaald `p{PROGRAM_ID}.external.adobeaemcloud.com` mag spreken met het milieu. Dit kan op dezelfde manier als elke andere op IP gebaseerde lijst van gewenste personen in de Manager van de Wolk worden gedaan.

Als de regels op weg-gebaseerd moeten zijn, gebruik standaardHTTP richtlijnen op het verzendersniveau om bepaalde IPs te ontkennen of toe te staan. Zij zouden ervoor moeten zorgen dat de gewenste wegen bij CDN ook niet cacheable zijn zodat het verzoek altijd aan oorsprong krijgt.

**Voorbeeld van HTTP-configuratie**

```
Order deny,allow
Deny from all
Allow from 192.168.0.1
Header always set Cache-Control private
```

## De netwerkinfrastructuur van een programma verwijderen {#deleting-network-infrastructure}

Naar **delete** de netwerkinfrastructuur voor een programma, roept `DELETE /program/{program ID}/networkinfrastructure/{networkinfrastructureID}`.

>[!NOTE]
>
> Met Verwijderen wordt de infrastructuur alleen verwijderd als de geavanceerde netwerken van alle omgevingen zijn uitgeschakeld.
> 

## Overgang tussen de Geavanceerde Types van Voorzien van een netwerk {#transitioning-between-advanced-networking-types}

Het is mogelijk om tussen geavanceerde voorzien van een netwerktypes te migreren door de volgende procedure te volgen:

* geavanceerd netwerken in alle omgevingen uitschakelen
* verwijder de geavanceerde netwerkinfrastructuur
* ontspant de geavanceerde voorzien van een netwerkinfras met de correcte waarden
* geavanceerde netwerken op milieuniveau opnieuw inschakelen

>[!WARNING]
>
> Deze procedure zal in een onderbreking van de geavanceerde voorzien van een netwerkdiensten tussen schrapping en recreatie resulteren
> 

Als de onderbreking significante bedrijfsgevolgen zou veroorzaken, contacteer klantensteun voor hulp, beschrijvend wat reeds is gecreeerd en de reden voor de verandering.

## Geavanceerde netwerkconfiguratie voor extra publicatiegebieden {#advanced-networking-configuration-for-additional-publish-regions}

Wanneer een extra gebied aan een milieu wordt toegevoegd dat reeds gevormd geavanceerd voorzien van een netwerk heeft, zal het verkeer van het extra publiceer gebied dat de geavanceerde voorzien van een netwerkregels aanpast door standaardroute door het primaire gebied. Nochtans, als het primaire gebied niet beschikbaar wordt, wordt het geavanceerde voorzien van een netwerkverkeer gelaten vallen als het geavanceerde voorzien van een netwerk niet in het extra gebied is toegelaten. Als u de latentie wilt optimaliseren en de beschikbaarheid wilt verhogen in het geval dat een van de regio&#39;s een onderbreking ondergaat, is het noodzakelijk geavanceerde netwerken in te schakelen voor de extra publicatiegebieden. In de volgende secties worden twee verschillende scenario&#39;s beschreven.

>[!NOTE]
>
>Alle regio&#39;s delen hetzelfde [omgeving geavanceerde netwerkconfiguratie](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Environment-Advanced-Networking-Configuration), zodat is het niet mogelijk om verkeer aan verschillende bestemmingen te leiden die op het gebied worden gebaseerd het verkeer uit wegglijdt.

### Specifieke IP van de Eis Adressen {#additional-publish-regions-dedicated-egress}

#### Geavanceerde netwerken zijn al ingeschakeld in het primaire gebied {#already-enabled}

Als een geavanceerde voorzien van een netwerkconfiguratie reeds in het primaire gebied wordt toegelaten, volg deze stappen:

1. Als u uw infrastructuur zodanig hebt vergrendeld dat het toegewezen AEM IP-adres is toegestaan in de lijst, wordt aanbevolen om regels in die infrastructuur tijdelijk uit te schakelen. Als dit niet wordt gedaan, is er een korte periode waarin de verzoeken van de IP van het nieuwe gebied adressen door uw eigen infrastructuur worden ontkend. Merk op dat dit niet noodzakelijk is als u onderaan uw infrastructuur door middel van een FQDN (FullyQualified Domain Name) hebt gesloten, (`p1234.external.adobeaemcloud.com`, bijvoorbeeld), omdat alle AEM regio&#39;s geavanceerd netwerkverkeer vanaf dezelfde FQDN overschrijven
1. Creeer programma-scoped voorzien van een netwerkinfrastructuur voor het secundaire gebied door een vraag van de POST aan de Manager van de Wolk creeert de Infrastructuur API van het Netwerk, zoals die in geavanceerde voorzien van een netwerkdocumentatie wordt beschreven. Het enige verschil in de configuratie JSON van de nuttige lading met betrekking tot primair gebied is het gebiedsbezit
1. Als uw infrastructuur door IP moet worden gesloten om AEM verkeer toe te staan, voeg IPs toe die aanpassen `p1234.external.adobeaemcloud.com`. Er zou één per regio moeten zijn.

#### Geavanceerde netwerken nog niet geconfigureerd in een regio {#not-yet-configured}

De procedure is grotendeels vergelijkbaar met de voorgaande instructies. Nochtans, als het productiemilieu nog niet voor geavanceerd voorzien van een netwerk is toegelaten, is er een kans om de configuratie te testen door het in een het opvoeren milieu eerst toe te laten:

1. Maak voorzien van een netwerkinfrastructuur voor alle gebieden door de vraag van de POST aan [Cloud Manager API voor netwerkinfrastructuur maken](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Network-infrastructure/operation/createNetworkInfrastructure). Het enige verschil in de configuratie JSON van de nuttige lading met betrekking tot primair gebied is het gebiedbezit.
1. Voor het opvoeren milieu, laat en vormt het milieu binnen bereik geavanceerd voorzien van een netwerk toe door te lopen `PUT api/program/{programId}/environment/{environmentId}/advancedNetworking`. Zie de API-documentatie voor meer informatie [hier](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Environment-Advanced-Networking-Configuration/operation/enableEnvironmentAdvancedNetworkingConfiguration)
1. Indien nodig, externe infrastructuur vergrendelen, bij voorkeur met een FQDN (bijvoorbeeld `p1234.external.adobeaemcloud.com`). U kunt het anders doen door IP adres
1. Als het het opvoeren milieu zoals verwacht werkt, laat en vormt de milieu-scoped geavanceerde voorzien van een netwerkconfiguratie voor productie toe.

#### VPN {#vpn-regions}

De procedure is bijna identiek aan de specifieke IP van de uitgang adresinstructies. Het enige verschil is dat naast het gebiedsbezit dat verschillend van het primaire gebied wordt gevormd, `connections.gateway` Het gebied kan naar keuze aan route aan een verschillend eindpunt worden gevormd dat van VPN door uw organisatie wordt in werking gesteld, misschien geografisch dichter aan het nieuwe gebied.
