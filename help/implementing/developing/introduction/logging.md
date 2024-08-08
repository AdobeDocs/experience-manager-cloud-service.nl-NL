---
title: Aanmelden voor AEM as a Cloud Service
description: Leer hoe te om het Registreren voor AEM as a Cloud Service te gebruiken om globale parameters voor de centrale registrerendienst, specifieke montages voor de individuele diensten te vormen of hoe te om gegevensregistreren te verzoeken.
exl-id: 262939cc-05a5-41c9-86ef-68718d2cd6a9
feature: Log Files, Developing
role: Admin, Architect, Developer
source-git-commit: 6f658c5e991c89ff4129352444ba9960d83c8884
workflow-type: tm+mt
source-wordcount: '2829'
ht-degree: 0%

---

# Aanmelden voor AEM as a Cloud Service {#logging-for-aem-as-a-cloud-service}

AEM as a Cloud Service is een platform waarop klanten aangepaste code kunnen opnemen om unieke ervaringen voor hun klanten te creëren. Met dit in mening, is de registrerendienst een kritieke functie om code uitvoering op lokale ontwikkeling, en wolkenmilieu&#39;s, in het bijzonder de milieu&#39;s van AEM as a Cloud Service te zuiveren en te begrijpen Dev.

AEM as a Cloud Service het registreren montages en logboekniveaus worden beheerd in configuratiedossiers die als deel van het AEM project in Git, worden opgeslagen en als deel van het AEM project via Cloud Manager worden opgesteld. Logboekregistratie in AEM as a Cloud Service kan worden opgedeeld in twee logische sets:

* AEM registreren, die registreren op het niveau van de AEM toepassing uitvoert
* Apache HTTPD Web Server/Dispatcher-logboekregistratie, die het registreren van de webserver en Dispatcher op de Publish-laag uitvoert.
* Het registreren CDN, die als zijn naam wijst, voert het registreren bij CDN uit. Deze functie wordt begin september geleidelijk aan aan aan de klanten aangeboden.

## AEM vastleggen {#aem-logging}

Het registreren op het AEM toepassingsniveau, wordt behandeld door drie logboeken:

1. AEM Java-logboeken, die Java-logboekinstructies voor de AEM toepassing weergeven.
1. De logboeken van het Verzoek van HTTP, die logboekinformatie over HTTP- verzoeken en hun antwoorden registreren die door AEM worden gediend
1. De logboeken van de Toegang van HTTP, die logboek samenvatte informatie en HTTP- verzoeken die door AEM worden gediend

>[!NOTE]
>
>De HTTP- verzoeken die van het geheime voorgeheugen van Dispatcher van de rij van Publish of upstream CDN worden gediend worden niet weerspiegeld in deze logboeken.

## Java-aanmelding AEM {#aem-java-logging}

AEM as a Cloud Service biedt toegang tot Java-loginstructies. Ontwikkelaars van toepassingen voor AEM moeten de algemene Java-logboekbest practices volgen en relevante instructies over de uitvoering van aangepaste code registreren op de volgende logniveaus:

<table>
<tr>
<td>
<b> AEM Milieu </b></td>
<td>
<b> Niveau van het Logboek </b></td>
<td>
<b> Beschrijving </b></td>
<td>
<b> Beschikbaarheid van de Verklaring van het Logboek </b></td>
</tr>
<tr>
<td>
Ontwikkeling</td>
<td>
DEBUG</td>
<td>
Beschrijft wat in de toepassing gebeurt.<br>
Wanneer het DEBUG registreren actief is, worden de verklaringen die een duidelijk beeld verstrekken van welke activiteiten voorkomen en om het even welke zeer belangrijke parameters die verwerking beïnvloeden geregistreerd.</td>
<td>
<ul>
<li> Lokale ontwikkeling</li>
<li>Ontwikkeling</li>
</ul></td>
</tr>
<tr>
<td>
Werkgebied</td>
<td>
WAARSCHUWING</td>
<td>
Beschrijft voorwaarden die het potentieel hebben om fouten te worden.<br>
Wanneer het registreren WARN actief is, slechts worden de verklaringen die op voorwaarden wijzen die sub-optimaliteit naderen geregistreerd.</td>
<td>
<ul>
<li> Lokale ontwikkeling</li>
<li>Ontwikkeling</li>
<li>Werkgebied</li>
</ul></td>
</tr>
<tr>
<td>
Productie</td>
<td>
FOUT</td>
<td>
Beschrijft voorwaarden die op een mislukking wijzen, en behoefte om op te lossen.<br>
Wanneer het registreren van de FOUT actief is, slechts worden de verklaringen die op mislukkingen wijzen geregistreerd. FOUTloginstructies geven een ernstig probleem aan dat zo snel mogelijk moet worden opgelost.</td>
<td>
<ul>
<li> Lokale ontwikkeling</li>
<li>Ontwikkeling</li>
<li>Werkgebied</li>
<li>Productie</li>
</ul></td>
</tr>
</table>

Hoewel Java-logboekregistratie verschillende andere niveaus van granulariteit voor logboekregistratie ondersteunt, raadt AEM as a Cloud Service aan de drie hierboven beschreven niveaus te gebruiken.

AEM de niveaus van het Logboek worden geplaatst per milieutype via configuratie OSGi, die beurtelings aan Git wordt geëngageerd, en via Cloud Manager aan AEM as a Cloud Service wordt opgesteld. Wegens dit, is het best om logboekverklaringen verenigbaar en goed gekend voor omgevingstypes te houden om de logboeken beschikbaar via AEM als Cloud Service te verzekeren zijn beschikbaar op het optimale logboekniveau zonder herplaatsing van toepassing met de bijgewerkte configuratie van het logboekniveau te vereisen.

**Uitvoer van het Logboek van het Voorbeeld**

```
22.06.2020 18:33:30.120 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *ERROR* [qtp501076283-1809] io.prometheus.client.dropwizard.DropwizardExports Failed to get value from Gauge
22.06.2020 18:33:30.229 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [qtp501076283-1805] org.apache.sling.auth.core.impl.SlingAuthenticator getAnonymousResolver: Anonymous access not allowed by configuration - requesting credentials
22.06.2020 18:33:30.370 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] org.apache.sling.i18n.impl.JcrResourceBundle Finished loading 0 entries for 'en_US' (basename: <none>) in 4ms
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [FelixLogListener] org.apache.sling.i18n Service [5126, [java.util.ResourceBundle]] ServiceEvent REGISTERED
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *WARN* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] libs.granite.core.components.login.login$jsp j_reason param value 'unknown' cannot be mapped to a valid reason message: ignoring
```

**Formaat van het Logboek**

<table>
<tbody>
<tr>
<td>Datum en tijd</td>
<td>29.04.2020 21 :50: 13.398</td>
</tr>
<tr>
<td>AEM as a Cloud Service node ID</td>
<td>[cm-p1234-e5678-aem-auteur-59555cb5b8-q7l9s]</td>
</tr>
<tr>
<td>Logboekniveau</td>
<td>DEBUG</td>
</tr>
<tr>
<td>Thread</td>
<td>qtp2130572036-1472</td>
</tr>
<tr>
<td>Java-klasse</td>
<td>com.example.approval.workflow.impl.CustomApprovalWorkflow</td>
</tr>
<tr>
<td>Logbericht</td>
<td>Geen opgegeven fiatteur, standaard ingesteld op [ Creative Approvers-gebruikersgroep ]</td>
</tr>
</tbody>
</table>

### Configuratieloggers {#configuration-loggers}

AEM Java-logboeken worden gedefinieerd als OSGi-configuratie en richten zich dus op specifieke AEM as a Cloud Service-omgevingen met behulp van runmode-mappen.

Configureer Java-logboekregistratie voor aangepaste Java-pakketten via OSGi-configuraties voor de Sling LogManager-fabriek. Er zijn twee ondersteunde configuratie-eigenschappen:

| OSGi Configuration, eigenschap | Beschrijving |
|---|---|
| org.apache.sling.commons.log.names | De Java-pakketten waarvoor loginstructies moeten worden verzameld. |
| org.apache.sling.commons.log.level | Het logniveau waarop de Java-pakketten moeten worden geregistreerd, opgegeven door org.apache.sling.commons.log.names |

Het veranderen van andere Logmanager OSGi configuratieeigenschappen kan in beschikbaarheidskwesties in AEM as a Cloud Service resulteren.

Hieronder volgen voorbeelden van de aanbevolen logboekconfiguraties (met behulp van het tijdelijke Java-pakket van `com.example` ) voor de drie AEM as a Cloud Service-omgevingstypen.

### Ontwikkeling {#development}

/apps/my-app/config/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "debug"
}
```

### Werkgebied {#stage}

/apps/my-app/config.stage/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "warn"
}
```

### Productie {#productiomn}

/apps/my-app/config.prod/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "error"
}
```

## Logboekregistratie HTTP-aanvraag AEM {#aem-http-request-logging}

AEM as a Cloud Service die HTTP- verzoekregistreren verstrekt inzicht in de HTTP- verzoeken die aan AEM en hun reacties van HTTP in tijdorde worden gemaakt. Dit logboek is nuttig om de Verzoeken van HTTP te begrijpen die aan AEM worden gemaakt en de orde zij worden verwerkt en aan geantwoord.

De sleutel tot het begrip van dit logboek is het in kaart brengen van de HTTP- verzoek en antwoordparen door hun IDs, die door de numerieke waarde in de steunen wordt aangegeven. Vaak hebben verzoeken en hun overeenkomstige reacties andere HTTP- verzoeken en reacties tussen hen in het logboek worden geworpen.

**Logboek van het Voorbeeld**

```
29/Apr/2020:19:14:21 +0000 [137] > POST /conf/global/settings/dam/adminui-extension/metadataprofile/ HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:22 +0000 [139] > GET /mnt/overlay/dam/gui/content/processingprofilepage/metadataprofiles/editor.html/conf/global/settings/dam/adminui-extension/metadataprofile/main HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:21 +0000 [137] <- 201 text/html 111ms [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:22 +0000 [139] <- 200 text/html;charset=utf-8 637ms [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
```

**Formaat van het Logboek**

<table>
<tbody>
<tr>
<td>Datum en tijd</td>
<td>29/apr/2020 :19: 14:21 +0000</td>
</tr>
<tr>
<td>ID Vragen/beantwoorden</td>
<td><code>[137]</code></td>
</tr>
<tr>
<td>HTTP-methode</td>
<td>POST</td>
</tr>
<tr>
<td>URL</td>
<td>/conf/global/settings/dam/adminui-extension/metadataprofile/</td>
</tr>
<tr>
<td>Protocol</td>
<td>HTTP/1.1
</td>
</tr>
<tr>
<td>AEM as a Cloud Service node ID</td>
<td>[cm-p1234-e5678-aem-auteur-59555cb5b8-q7l9s]</td>
</tr>
</tbody>
</table>

### Logboek configureren {#configuring-the-log}

Het AEM HTTP-aanvraaglogboek kan niet worden geconfigureerd in AEM as a Cloud Service.

## HTTP-toegangsregistratie AEM {#aem-http-access-logging}

AEM als het de toegangslogboek van HTTP van de Cloud Service toont HTTP- verzoeken in tijdorde. Elke logingang vertegenwoordigt het Verzoek van HTTP dat tot AEM toegang heeft.

Dit logboek is nuttig om snel te begrijpen welke HTTP- verzoeken aan AEM worden gemaakt, als zij door de begeleidende code van de de reactiestatus van HTTP te bekijken slagen, en hoe lang het HTTP- verzoek duurde om te voltooien. Dit logboek kan ook nuttig zijn om de activiteit van een specifieke gebruiker te zuiveren door logboekingangen door Gebruikers te filtreren.

**Uitvoer van het Logboek van het Voorbeeld**

```
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css HTTP/1.1" 200 1141 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/customthumb/clientlibs.lc-60e4443805c37afa0c74b674b141f1df-lc.min.css HTTP/1.1" 200 809 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/metadataeditor/clientlibs/metadataeditor.lc-4a2226d8232f8b7ab27d24820b9ddd64-lc.min.js HTTP/1.1" 200 7965 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
```

| AEM as a Cloud Service Node-id | cm-p1235-e2644-aem-auteur-59555cb5b8-8kgr2 |
|---|---|
| IP-adres van de client | - |
| Gebruiker | myuser@adobe.com |
| Datum en tijd | 30/apr/2020 :17: 37:14 +0000 |
| HTTP-methode | GET |
| URL | `/libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css` |
| Protocol | HTTP/1.1 |
| HTTP-reactiestatus | 200 |
| Grootte van de hoofdtekst van de reactie in bytes | 1141 |
| Referenter | `"https://author-p1234-e4444.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/wknd/en/adventures/surf-camp-in-costa-rica/adobestock_266405335.jpeg&_charset_=utf8"` |
| Gebruikersagent | `"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"` |

### Het HTTP Access-logboek configureren {#configuring-the-http-access-log}

Het HTTP Access-logboek kan niet worden geconfigureerd in AEM as a Cloud Service.

## Apache Web Server en Dispatcher Logging {#apache-web-server-and-dispatcher-logging}

AEM as a Cloud Service biedt drie logboeken voor de Apache Web Servers en de verzender-laag op de Publish:

* Apache HTTPD Web Server Access-logboek
* Apache HTTPD Web Server Error log
* Dispatcher-logboek

Deze logboeken zijn alleen beschikbaar voor de Publish-laag.

Deze set logbestanden biedt inzichten in HTTP-aanvragen bij de AEM as a Cloud Service Publish-laag voordat deze aanvragen bij de AEM toepassing worden ingediend. Dit is belangrijk om te begrijpen aangezien, idealiter, de meeste HTTP- verzoeken aan de de rijservers van Publish door inhoud worden gediend die door de Server van het Web van Apache HTTPD en AEM Dispatcher in de cache wordt opgeslagen, en nooit de AEM toepassing zelf bereiken. Er zijn dus geen loginstructies voor deze aanvragen in AEM Java-, verzoek- of toegangslogboeken.

### Apache HTTPD Web Server Access Log {#apache-httpd-web-server-access-log}

Het toegangslogboek van de Server van Apache HTTP van het Web bevat verklaringen voor elke HTTP- aanvraag die de server/Dispatcher van het Web van de rij van Publish bereikt. De verzoeken die van upstream CDN worden gediend worden niet weerspiegeld in deze logboeken.

Zie informatie over het formaat van het foutenlogboek in de [ officiële documentatie van de pijn ](https://httpd.apache.org/docs/2.4/logs.html#accesslog).

**Uitvoer van het Logboek van het Voorbeeld**

```
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:41 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/favicons/favicon-32.png HTTP/1.1" 200 715 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:41 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/favicons/favicon-512.png HTTP/1.1" 200 9631 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:42 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/country-flags/US.svg HTTP/1.1" 200 810 "https://publish-p6902-e30226.adobeaemcloud.com/content/wknd/us/en.html" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
```

**Formaat van het Logboek**

<table>
<tbody>
<tr>
<td>AEM als Cloud Service-knooppunt-id</td>
<td>cm-p1234-e26813-aem-publish-5c787687c-lqlxr</td>
</tr>
<tr>
<td>IP Adres van de cliënt</td>
<td>-</td>
</tr>
<tr>
<td>Gebruiker</td>
<td>-</td>
</tr>
<tr>
<td>Datum en tijd</td>
<td>01/Mei/2020 :00: 09:46 +000</td>
</tr>
<tr>
<td>HTTP-methode</td>
<td>GET</td>
</tr>
<tr>
<td>URL</td>
<td>/content/example.html</td>
</tr>
<tr>
<td>Protocol</td>
<td>HTTP/1.1</td>
</tr>
<tr>
<td>HTTP-responsstatus</td>
<td>200</td>
</tr>
<tr>
<td>Grootte</td>
<td>310</td>
</tr>
<tr>
<td>Verwijzing</td>
<td>-</td>
</tr>
<tr>
<td>Gebruikersagent</td>
<td>"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"</td>
</tr>
</tbody>
</table>

### Het Apache HTTPD Web Server Access Log configureren {#configuring-the-apache-httpd-webs-server-access-log}

Dit logboek kan niet worden geconfigureerd in AEM as a Cloud Service.

## Apache HTTPD Web Server Error Log {#apache-httpd-web-server-error-log}

Het foutenlogboek van de Server van Apache HTTP van het Web bevat verklaringen voor elke fout in de server/Dispatcher van het Web van Publish rij.

Zie informatie over het formaat van het foutenlogboek in de [ officiële documentatie van de pijn ](https://httpd.apache.org/docs/2.4/logs.html#errorlog).

**Uitvoer van het Logboek van het Voorbeeld**

```
Fri Jul 17 02:19:48.093820 2020 [mpm_worker:notice] [pid 1:tid 140272153361288] [cm-p1234-e30226-aem-publish-b86c6b466-b9427] AH00292: Apache/2.4.43 (Unix) Communique/4.3.4-20200424 mod_qos/11.63 configured -- resuming normal operations
Fri Jul 17 02:19:48.093874 2020 [core:notice] [pid 1:tid 140272153361288] [cm-p1234-e30226-aem-publish-b86c6b466-b9427] AH00094: Command line: 'httpd -d /etc/httpd -f /etc/httpd/conf/httpd.conf -D FOREGROUND -D ENVIRONMENT_PROD'
Fri Jul 17 02:29:34.517189 2020 [mpm_worker:notice] [pid 1:tid 140293638175624] [cm-p1234-e30226-aem-publish-b496f64bf-5vckp] AH00295: caught SIGTERM, shutting down
```

**Formaat van het Logboek**

<table>
<tbody>
<tr>
<td>Datum en tijd</td>
<td>17 jul. 02 :16: 42.608913 2020</td>
</tr>
<tr>
<td>Gebeurtenisniveau</td>
<td>[mpm_worker:notice]</td>
</tr>
<tr>
<td>Proces-id</td>
<td>[pid 1:tid 140715149343624]</td>
</tr>
<tr>
<td>Naam pod</td>
<td>[cm-p1234-e56789-aem-publish-b86c6b466-qpfvp]</td>
</tr>
<tr>
<td>Bericht</td>
<td>AH00094: Opdrachtregel: 'httpd -d /etc/httpd -f /etc/httpd/conf/httpd.conf -D FOREGROUND -D </td>
</tr>
</tbody>
</table>

### Het Apache HTTPD Web Server Error Log configureren {#configuring-the-apache-httpd-web-server-error-log}

De mod_rewrite logboekniveaus worden bepaald door veranderlijke REWRITE_LOG_LEVEL in het dossier `conf.d/variables/global.var`.

Het kan aan fout worden geplaatst, waarschuwen, info, zuiveren en spoor1 - trace8, met een standaardwaarde van waarschuwen. Om uw te zuiveren RewriteRules, wordt het geadviseerd om het logboekniveau aan trace2 op te heffen. Het wordt geadviseerd om te zuiveren herschrijft regels gebruikend [ Dispatcher SDK ](../../dispatcher/validation-debug.md). Het maximale logniveau voor AEM as a Cloud Service is `debug` . Op dit moment is het dus niet effectief mogelijk om fouten op te sporen in herschrijfregels in de cloud.

Zie [ mod_rewrite moduledocumentatie ](https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging) voor meer informatie.

Als u het logniveau per omgeving wilt instellen, gebruikt u de desbetreffende voorwaardelijke vertakking in het bestand global.var, zoals hieronder wordt beschreven:

```
Define REWRITE_LOG_LEVEL debug
  
<IfDefine ENVIRONMENT_STAGE>
  ...
  Define REWRITE_LOG_LEVEL warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define REWRITE_LOG_LEVEL error
  ...
</IfDefine>
```

## Dispatcher Log {#dispatcher-log}

**Voorbeeld**

```
[17/Jul/2020:23:48:06 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures.html" - 475ms [publishfarm/0] [action miss] "publish-p12904-e25628.adobeaemcloud.com"
[17/Jul/2020:23:48:07 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures/climbing-new-zealand/_jcr_content/root/responsivegrid/carousel/item_1571266094599.coreimg.jpeg/1473680817282/sport-climbing.jpeg" 302 10ms [publishfarm/0] [action none] "publish-p12904-e25628.adobeaemcloud.com"
[17/Jul/2020:23:48:07 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures/ski-touring-mont-blanc/_jcr_content/root/responsivegrid/carousel/item_1571168419252.coreimg.jpeg/1572047288089/adobestock-238230356.jpeg" 302 11ms [publishfarm/0] [action none] "publish-p12904-e25628.adobeaemcloud.com"
```

**Formaat van het Logboek**

<table>
<tbody>
<tr>
<td>Datum en tijd</td>
<td>[17/jul/2020 :23: 48:16 +0000]</td>
</tr>
<tr>
<td>Podnaam</td>
<td>[cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr]</td>
</tr>
<tr>
<td>Protocol</td>
<td>GET</td>
</tr>
<tr>
<td>URL</td>
<td>/content/experience-fragments/wknd/language-masters/en/contributors/sofia-sjoeberg/master/_jcr_content/root/responsivegrid/image.coreimg.100.500.jpeg/1572236359031/ayo-ogunseinde-237739.jpeg</td>
</tr>
<tr>
<td>Dispatcher-antwoordstatuscode</td>
<td>/content/experience-fragments/wknd/language-masters/en/contributors/sofia-sjoeberg/master/_jcr_content/root/responsivegrid/image.coreimg.100.500.jpeg/1572236359031/ayo-ogunseinde-237739.jpeg</td>
</tr>
<tr>
<td>Duur</td>
<td>1949 ms</td>
</tr>
<tr>
<td>Landbouwbedrijf</td>
<td>[uitgeverij/0]</td>
</tr>
<tr>
<td>Cachestatus</td>
<td>[actie missen]</td>
</tr>
<tr>
<td>Host</td>
<td>"publish-p12904-e25628.adobeaemcloud.com"</td>
</tr>
</tbody>
</table>

### Het Dispatcher-foutenlogboek configureren {#configuring-the-dispatcher-error-log}

De verzenderslogniveaus worden gedefinieerd door de variabele DISP_LOG_LEVEL in het bestand `conf.d/variables/global.var` .

Het kan aan fout worden geplaatst, waarschuwen, info, zuiveren en spoor1, met een standaardwaarde om te waarschuwen.

Hoewel het registreren van Dispatcher verscheidene andere niveaus van het registreren granulariteit steunt, adviseert AEM as a Cloud Service gebruikend de hieronder beschreven niveaus.

Als u het logniveau per omgeving wilt instellen, gebruikt u de desbetreffende voorwaardelijke vertakking in het `global.var` -bestand, zoals hieronder wordt beschreven:

```
Define DISP_LOG_LEVEL debug
  
<IfDefine ENVIRONMENT_STAGE>
  ...
  Define DISP_LOG_LEVEL warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define DISP_LOG_LEVEL error
  ...
</IfDefine>
```

>[!NOTE]
>
>Voor AEM as a Cloud Service-omgevingen is foutopsporing het maximale breedbeeldniveau. Het niveau van het spoorlogboek wordt niet gesteund zodat zou u moeten vermijden plaatsend het wanneer het werken in wolkenmilieu&#39;s.

## CDN-logboek {#cdn-log}

AEM as a Cloud Service biedt toegang tot CDN-logboeken. Deze zijn handig voor het gebruik van gevallen zoals optimalisatie van de cache-raakverhouding. De CDN-logindeling kan niet worden aangepast en er bestaat geen concept om de indeling in te stellen op verschillende modi, zoals info, warn of error.

CDN de logboeken zullen aan Splunk voor nieuwe Splunk door:sturen de verzoeken van het steunkaartje worden door:sturen; de klanten die reeds Splunk hebben toegelaten zullen CDN- logboeken in de toekomst kunnen toevoegen.

**Voorbeeld**

```
{
"timestamp": "2023-05-26T09:20:01+0000",
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
"rules": "match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked"
}
```

**Formaat van het Logboek**

De logboeken CDN zijn verschillend van de andere logboeken in die dat het aan een json formaat volgt.

| **Naam van het Gebied** | **Beschrijving** |
|---|---|
| *timestamp* | De tijd waarop de aanvraag is gestart, na beëindiging van TLS |
| *ttfb* | Afkorting voor *Tijd aan Eerste Byte*. Het tijdinterval tussen het verzoek begon tot het punt alvorens het reactiekarakter begon te worden gestroomd. |
| *cli_ip* | Het client-IP-adres. |
| *cli_country* | Twee-brief [ ISO 3166-1 ](https://en.wikipedia.org/wiki/ISO_3166-1) alpha-2 landcode voor het cliëntland. |
| *rid* | De waarde van de verzoekkopbal die wordt gebruikt om het verzoek uniek te identificeren. |
| *req_ua* | De gebruikersagent die verantwoordelijk is voor het indienen van een bepaalde HTTP-aanvraag. |
| *gastheer* | De autoriteit waarvoor het verzoek is bestemd. |
| *url* | Het volledige pad, inclusief queryparameters. |
| *methode* | HTTP-methode die door de client wordt verzonden, zoals &quot;GET&quot; of &quot;POST&quot;. |
| *res_ctype* | Het Content-Type dat wordt gebruikt om het oorspronkelijke mediatype van de bron aan te geven. |
| *geheime voorgeheugen* | Status van de cache. Mogelijke waarden zijn HIT, MISS of PASS |
| *status* | De HTTP-statuscode als een geheel getal. |
| *res_age* | De hoeveelheid tijd (in seconden) dat een reactie in de cache is geplaatst (in alle knooppunten). |
| *pop* | Datacenter van de CDN-cacheserver. |
| *regels* | De namen van om het even welke passende [ regels van de verkeersfilter ](/help/security/traffic-filter-rules-including-waf.md) en de vlaggen van WAF, die ook erop wijzen als de gelijke in een blok resulteerde. Leeg als geen regels overeenkomen. |


## Hoe te om Logs toegang te hebben {#how-to-access-logs}

### Cloud-omgevingen {#cloud-environments}

AEM as a Cloud Service-logbestanden voor cloudservices kunnen worden geopend door de Cloud Manager-interface te downloaden of door logbestanden op de opdrachtregel via de opdrachtregelinterface van Adobe I/O te downloaden. Voor meer informatie, zie de [ het registreren van Cloud Manager documentatie ](/help/implementing/cloud-manager/manage-logs.md).

### Logbestanden voor extra Publish-regio&#39;s {#logs-for-additional-publish-regions}

Als voor een bepaalde omgeving extra publicatiegebieden zijn ingeschakeld, kunnen de logbestanden voor elke regio worden gedownload van Cloud Manager, zoals hierboven vermeld.

De AEM logboeken en de verzender logboeken voor extra publiceren gebieden zullen het gebied in de eerste 3 brieven na milieu identiteitskaart specificeren, zoals die door **wordt geïllustreerd nld2** in de steekproef hieronder, die naar een extra AEM verwijst publiceer instantie die in Nederland wordt gevestigd:

```
cm-p7613-e12700-nld2-aem-publish-bcbb77549-5qmmt 127.0.0.1 - 07/Nov/2023:23:57:11 +0000 "HEAD /libs/granite/security/currentuser.json HTTP/1.1" 200 - "-" "Java/11.0.19"
```

### Lokale SDK {#local-sdk}

AEM as a Cloud Service SDK biedt logbestanden ter ondersteuning van lokale ontwikkeling.

AEM logboeken bevinden zich in de map `crx-quickstart/logs` , waar de volgende logbestanden kunnen worden weergegeven:

* Java-logbestand AEM: `error.log`
* Logbestand HTTP-aanvraag AEM: `request.log`
* AEM HTTP Access-logboek: `access.log`

Logbestanden van Apache-lagen, inclusief dispatcher, bevinden zich in de Docker-container die de Dispatcher bevat. Zie de [ documentatie van Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html) voor informatie over hoe te om Dispatcher te beginnen.

De logbestanden ophalen:

1. Typ op de opdrachtregel `docker ps` om de containers weer te geven
1. Als u zich wilt aanmelden bij de container, typt u &quot;`docker exec -it <container> /bin/sh`&quot;, waarbij `<container>` de verzenderscontainer-id van de vorige stap is
1. Navigeer naar de cachroot onder `/mnt/var/www/html`
1. De logbestanden zijn kleiner dan `/etc/httpd/logs`
1. Inspect the logs: they can be access under the folder XYZ, where the following logs can view:
   * Apache HTTPD Web server access log - `httpd_access.log`
   * Logboeken van fouten op de Apache HTTPD-webserver - `httpd_error.log`
   * Dispatcher-logboeken - `dispatcher.log`

Logbestanden worden ook rechtstreeks afgedrukt op de einduitvoer. Meestal, zouden deze logboeken DEBUG moeten zijn, die kan worden verwezenlijkt door in het Debug niveau als parameter over te gaan wanneer het runnen van Docker. Bijvoorbeeld:

`DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`

## Fouten opsporen in productie en werkgebied {#debugging-production-and-stage}

In uitzonderlijke omstandigheden moeten de logniveaus worden gewijzigd om zich bij een fijnere granulariteit in het werkgebied of de productieomgeving aan te melden.

Terwijl dit mogelijk is, vereist het veranderingen in de logboekniveaus in de configuratiedossiers in Git van Waarschuwen en Fout aan Zuiver, en het uitvoeren van een plaatsing aan AEM as a Cloud Service om deze configuratieveranderingen met de milieu&#39;s te registreren.

Afhankelijk van het verkeer en de hoeveelheid logboekverklaring die door Debug wordt geschreven, kan dit in een negatief prestatieseffect op het milieu resulteren, daarom wordt geadviseerd dat de veranderingen in Stadium en Productie zuivert niveaus zijn:

* Op een verstandige manier en alleen wanneer dat absoluut noodzakelijk is
* Omgekeerd naar de juiste niveaus en zo snel mogelijk opnieuw ingezet

## Logbestanden splitsen {#splunk-logs}

Klanten die Splunk-accounts hebben, kunnen via een ticket voor klantenondersteuning aanvragen dat hun AEM Cloud Service-logbestanden naar de juiste index worden doorgestuurd. De logboekgegevens zijn gelijkwaardig aan wat door het logboekdownloads van Cloud Manager beschikbaar is, maar de klanten kunnen het geschikt vinden om de vraageigenschappen te gebruiken beschikbaar in het product van de Splunk.

De netwerkbandbreedte verbonden aan logboeken die naar Splunk worden verzonden wordt beschouwd als deel van het I/O gebruik van het Netwerk van de klant.

CDN de logboeken zullen aan Splunk voor nieuwe verzoeken van het steunkaartje door:sturen worden doorgestuurd; de klanten die reeds Splunk hebben toegelaten zullen CDN- logboeken in de toekomst kunnen toevoegen.

>[!NOTE]
>
>*Specifieke* logboeken, en *specifieke* Logboeken van de Gebruiker, kunnen niet aan Splunk door:sturen.
>
>**Alle** logboeken zullen aan Splunk door:sturen, waar om het even welk verder filtreren door de klant kan worden gedaan die op hun vereisten wordt gebaseerd.

### Splunk Forwarding inschakelen {#enabling-splunk-forwarding}

In het supportverzoek moeten klanten aangeven:

* Splunk HEC eindpuntadres. Dit eindpunt moet een geldig SSL certificaat hebben en openbaar toegankelijk zijn.
* De segmentindex
* De segmentpoort
* De Splunk HEC-token. Zie [ deze pagina ](https://docs.splunk.com/Documentation/Splunk/8.0.4/Data/HECExamples) voor meer informatie.

De bovenstaande eigenschappen moeten voor elke relevante combinatie van programma/omgevingstype worden gespecificeerd. Als een klant bijvoorbeeld ontwikkelings-, staging- en productieomgevingen wilde, moeten deze drie informatiesets leveren, zoals hieronder wordt aangegeven.

>[!NOTE]
>
>Splunk forward for sandbox program environment is not supported.

>[!NOTE]
>
>Het Splunk door:sturen vermogen is niet mogelijk van een specifiek uitgangIP adres.

Zorg ervoor dat het eerste verzoek alle ontwikkelomgeving bevat die moet worden ingeschakeld, in aanvulling op de fase-/prodomgevingen. Splunk moet een SSL-certificaat hebben en openbaar zijn.

Als om het even welke nieuwe dev milieu&#39;s na het aanvankelijke verzoek worden gecreeerd om Splunk te hebben door:sturen, maar het niet toegelaten hebben, zou een extra verzoek moeten worden gemaakt.

Merk ook op dat als de ontwikkelmilieu&#39;s zijn gevraagd, het mogelijk is dat andere ontwikkelmilieu&#39;s niet in het verzoek of zelfs zandbakmilieu&#39;s toegelaten Splunk door:sturen zullen hebben en een index van het Splunk zullen delen. Klanten kunnen het veld `aem_env_id` gebruiken om een onderscheid te maken tussen deze omgevingen.

Hieronder vindt u een voorbeeld van een verzoek voor klantenondersteuning:

Programma 123, Production Env

* Splunk HEC-eindpuntadres: `splunk-hec-ext.acme.com`
* Splunk-index: acme_123prod (de klant kan kiezen welke naamgevingsconventie hij wil)
* Splondepoort: 443
* Splunk HEC token: ABC123

Programma 123, Stage Env

* Splunk HEC-eindpuntadres: `splunk-hec-ext.acme.com`
* Splonindex: acme_123stage
* Splondepoort: 443
* Splunk HEC token: ABC123

Programma 123, Dev Envs

* Splunk HEC-eindpuntadres: `splunk-hec-ext.acme.com`
* Splonindex: acme_123dev
* Splondepoort: 443
* Splunk HEC token: ABC123

Het kan voldoende zijn dat dezelfde segmentindex wordt gebruikt voor elke omgeving. In dat geval kan het veld `aem_env_type` worden gebruikt om onderscheid te maken op basis van de waarden dev, stage en prod. Als er meerdere ontwikkelomgevingen zijn, kan het veld `aem_env_id` ook worden gebruikt. Sommige organisaties kunnen een afzonderlijke index voor de logboeken van het productiemilieu kiezen als de bijbehorende index toegang tot een verminderde reeks gebruikers van de Splunk beperkt.

Hier volgt een voorbeeld van een logbestandvermelding:

```
aem_env_id: 1242
aem_env_type: dev
aem_program_id: 12314
aem_tier: author
file_path: /var/log/aem/error.log
host: 172.34.200.12 
level: INFO
msg: [FelixLogListener] com.adobe.granite.repository Service [5091, [org.apache.jackrabbit.oak.api.jmx.SessionMBean]] ServiceEvent REGISTERED
orig_time: 16.07.2020 08:35:32.346
pod_name: aemloggingall-aem-author-77797d55d4-74zvt
splunk_customer: true
```
