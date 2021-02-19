---
title: Logboekregistratie
description: Leer hoe te om globale parameters voor de centrale registrerendienst, specifieke montages voor de individuele diensten te vormen of hoe te om gegevensregistreren te verzoeken.
translation-type: tm+mt
source-git-commit: 17ba5068b0df0724bcebeecb2323b7dcdc8d8cfa
workflow-type: tm+mt
source-wordcount: '2314'
ht-degree: 2%

---


# Logboekregistratie {#logging}

AEM als Cloud Service is een platform voor klanten om douanecode te omvatten om unieke ervaringen voor hun klantenbasis tot stand te brengen. Met dit in mening, is het registreren een kritieke functie om code uitvoering op lokale ontwikkeling, en wolkenmilieu&#39;s, in het bijzonder de AEM als milieu&#39;s van de Ontwikkelaar van een Cloud Service te zuiveren en te begrijpen.

AEM het registreren en het logboekniveaus worden beheerd in configuratiedossiers die als deel van het AEM project in Git worden opgeslagen, en als deel van het AEM project via de Manager van de Wolk worden opgesteld. Het aanmelden AEM als Cloud Service kan in twee logische reeksen worden opgedeeld:

* AEM registreren, die registreren op het niveau van de AEM toepassing uitvoert
* Apache HTTPD Web Server/Dispatcher registreren, die het registreren van de Webserver en de Verzender op de Publish rij uitvoert.

## Logboekregistratie AEM {#aem-loggin}

Het registreren op het AEM toepassingsniveau, wordt behandeld door drie logboeken:

1. AEM Java-logboeken, die Java-logboekinstructies voor de AEM toepassing weergeven.
1. De logboeken van het Verzoek van HTTP, die logboekinformatie over HTTP- verzoeken en hun antwoorden registreren die door AEM worden gediend
1. De logboeken van de Toegang van HTTP, die logboek samenvatte informatie en HTTP- verzoeken die door AEM worden gediend

>[!NOTE]
>
>De HTTP- verzoeken die van het Publish geheime voorgeheugen van de Verzender van de rij of upstream CDN worden gediend worden niet weerspiegeld in deze logboeken.

## Java-logboekregistratie AEM {#aem-java-logging}

AEM als Cloud Service biedt toegang tot Java-loginstructies. Ontwikkelaars van toepassingen voor AEM moeten de algemene Java-logboekbest practices volgen en relevante instructies over de uitvoering van aangepaste code registreren op de volgende logniveaus:

<table>
<tr>
<td>
<b>AEM</b></td>
<td>
<b>Logboekniveau</b></td>
<td>
<b>Beschrijving</b></td>
<td>
<b>Beschikbaarheid van logboekverklaring</b></td>
</tr>
<tr>
<td>
Ontwikkeling</td>
<td>
DEBUG</td>
<td>
Beschrijft wat in de toepassing gebeurt.<br>
Wanneer het DEBUG registreren actief is, worden de verklaringen die een duidelijk beeld van verstrekken welke activiteiten voorkomen evenals om het even welke zeer belangrijke parameters die verwerking beïnvloeden geregistreerd.</td>
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

Hoewel Java-logboekregistratie verschillende andere niveaus van granulariteit voor logboekregistratie ondersteunt, AEM een Cloud Service het gebruik van de drie hierboven beschreven niveaus aanbeveelt.

AEM de niveaus van het Logboek worden geplaatst per milieutype via configuratie OSGi, die beurtelings aan Git wordt geëngageerd, en via de Manager van de Wolk aan AEM als Cloud Service worden opgesteld. Wegens dit, is het best om logboekverklaringen verenigbaar en bekend voor omgevingstypes te houden, om de logboeken beschikbaar via AEM als Cloud Service te verzekeren zijn beschikbaar op het optimale logboekniveau zonder herplaatsing van toepassing met de bijgewerkte configuratie van het logboekniveau te vereisen.

**Uitvoer voorbeeldlog**

```
22.06.2020 18:33:30.120 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *ERROR* [qtp501076283-1809] io.prometheus.client.dropwizard.DropwizardExports Failed to get value from Gauge
22.06.2020 18:33:30.229 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [qtp501076283-1805] org.apache.sling.auth.core.impl.SlingAuthenticator getAnonymousResolver: Anonymous access not allowed by configuration - requesting credentials
22.06.2020 18:33:30.370 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] org.apache.sling.i18n.impl.JcrResourceBundle Finished loading 0 entries for 'en_US' (basename: <none>) in 4ms
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [FelixLogListener] org.apache.sling.i18n Service [5126, [java.util.ResourceBundle]] ServiceEvent REGISTERED
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *WARN* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] libs.granite.core.components.login.login$jsp j_reason param value 'unknown' cannot be mapped to a valid reason message: ignoring
```

**Logbestandsindeling**

<table>
<tbody>
<tr>
<td>Datum en tijd</td>
<td>29.04.2020 21:50:13.398</td>
</tr>
<tr>
<td>AEM als knooppunt-id voor Cloud Service</td>
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

AEM Java-logboeken worden gedefinieerd als OSGi-configuratie en richten zich dus op specifieke AEM als een Cloud Service-omgeving met behulp van runmode-mappen.

Configureer Java-logboekregistratie voor aangepaste Java-pakketten via OSGi-configuraties voor de Sling LogManager-fabriek. Er zijn twee ondersteunde configuratie-eigenschappen:

| OSGi Configuration, eigenschap | Beschrijving |
|---|---|
| org.apache.sling.commons.log.names | De Java-pakketten waarvoor loginstructies moeten worden verzameld. |
| org.apache.sling.commons.log.level | Het logniveau waarop de Java-pakketten moeten worden geregistreerd, opgegeven door org.apache.sling.commons.log.names |

Het veranderen van andere Logmanager OSGi configuratieeigenschappen kan in beschikbaarheidskwesties in AEM als Cloud Service resulteren.

Hieronder volgen voorbeelden van de aanbevolen logboekconfiguraties (met behulp van het tijdelijke Java-pakket van `com.example`) voor de drie AEM als omgevingstypen voor Cloud Servicen.

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

## Logboekregistratie van HTTP-aanvragen AEM {#aem-http-request-logging}

AEM als het verzoekregistreren van HTTP van een Cloud Service verstrekt inzicht in de HTTP- verzoeken die aan AEM en hun reacties van HTTP in tijdorde worden gemaakt. Dit logboek is nuttig om de Verzoeken van HTTP te begrijpen die aan AEM worden gemaakt en de orde zij worden verwerkt en aan geantwoord.

De sleutel tot het begrip van dit logboek is het in kaart brengen van de HTTP- verzoek en antwoordparen door hun IDs, die door de numerieke waarde in de steunen wordt aangegeven. Merk op dat vaak de verzoeken en hun overeenkomstige reacties andere HTTP- verzoeken en reacties tussen hen in het logboek worden geworpen.

**Voorbeeldlogboek**

```
29/Apr/2020:19:14:21 +0000 [137] -> POST /conf/global/settings/dam/adminui-extension/metadataprofile/ HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:22 +0000 [139] -> GET /mnt/overlay/dam/gui/content/processingprofilepage/metadataprofiles/editor.html/conf/global/settings/dam/adminui-extension/metadataprofile/main HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:21 +0000 [137] <- 201 text/html 111ms [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:22 +0000 [139] <- 200 text/html;charset=utf-8 637ms [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
```

**Logbestandsindeling**

<table>
<tbody>
<tr>
<td>Datum en tijd</td>
<td>29/apr/2020:19:14:21 +0000</td>
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
<td>AEM als knooppunt-id voor Cloud Service</td>
<td>[cm-p1234-e5678-aem-auteur-59555cb5b8-q7l9s]</td>
</tr>
</tbody>
</table>

### Logboek {#configuring-the-log} configureren

Het AEM HTTP- verzoeklogboek is niet configureerbaar in AEM als Cloud Service.

## Logboekregistratie van HTTP-toegang AEM {#aem-http-access-logging}

AEM als het de toegangslogboek van HTTP van de Cloud Service toont HTTP- verzoeken in tijdorde. Elke logingang vertegenwoordigt het Verzoek van HTTP dat tot AEM toegang heeft.

Dit logboek is nuttig om snel te begrijpen welke HTTP- verzoeken aan AEM worden gemaakt, als zij door de begeleidende code van de de reactiestatus van HTTP te bekijken slagen, en hoe lang het HTTP- verzoek duurde om te voltooien. Dit logboek kan ook nuttig zijn om de activiteit van een specifieke gebruiker te zuiveren door logboekingangen door Gebruikers te filtreren.

**Uitvoer voorbeeldlog**

```
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css HTTP/1.1" 200 1141 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/customthumb/clientlibs.lc-60e4443805c37afa0c74b674b141f1df-lc.min.css HTTP/1.1" 200 809 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/metadataeditor/clientlibs/metadataeditor.lc-4a2226d8232f8b7ab27d24820b9ddd64-lc.min.js HTTP/1.1" 200 7965 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
```

**Logbestandsindeling**

<table>
<tbody>
<tr>
<td>AEM als knooppunt-id voor Cloud Service</td>
<td>cm-p1235-e2644-aem-auteur-59555cb5b8-8kgr2</td>
</tr>
<tr>
<td>IP-adres van de client</td>
<td>-</td>
</tr>
<tr>
<td>Gebruiker</td>
<td>myuser@adobe.com</td>
</tr>
<tr>
<td>Datum en tijd</td>
<td>30/apr/2020:17:37:14 +0000</td>
</tr>
<tr>
<td>HTTP-methode</td>
<td>GET</td>
</tr>
<tr>
<td>URL</td>
<td>/libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css</td>
</tr>
<tr>
<td>Protocol</td>
<td>HTTP/1.1</td>
</tr>
<tr>
<td>HTTP-reactiestatus</td>
<td>200</td>
</tr>
<tr>
<td>HTTP-aanvraagtijd in milliseconden</td>
<td>1141</td>
</tr>
<tr>
<td>Referenter</td>
<td><code>"https://author-p1234-e4444.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/wknd/en/adventures/surf-camp-in-costa-rica/adobestock_266405335.jpeg&_charset_=utf8"</code></td>
</tr>
<tr>
<td>Gebruikersagent</td>
<td>"Mozilla/5.0 (Macintosh); Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"</td>
</tr>
</tbody>
</table>

### Het vormen van het Logboek van de Toegang van HTTP {#configuring-the-http-access-log}

Het logboek van de Toegang van HTTP is niet configureerbaar in AEM als Cloud Service.

## Logboekregistratie voor Apache Web Server en Dispatcher {#apache-web-server-and-dispatcher-logging}

AEM als Cloud Service verstrekt drie logboeken voor de servers van het Web Apache en verzender laag op Publish:

* Apache HTTPD Web Server Access-logboek
* Apache HTTPD Web Server Error log
* Verzendlogboek

Deze logbestanden zijn alleen beschikbaar voor de publicatielijst.

Deze reeks logboeken verstrekt inzichten in HTTP- verzoeken aan de AEM als Cloud Service publiceren rij voorafgaand aan die verzoeken die de AEM toepassing bereiken. Dit is belangrijk om te begrijpen aangezien, idealiter, de meeste HTTP- verzoeken aan de Publish rijservers door inhoud worden gediend die door de Server van het Web van Apache HTTPD en AEM Dispatcher in de cache wordt opgeslagen, en nooit de AEM toepassing zelf bereiken. Er zijn dus geen loginstructies voor deze aanvragen in AEM Java-, verzoek- of toegangslogboeken.

### Apache HTTPD Web Server Access Log {#apache-httpd-web-server-access-log}

Het toegangslogboek van de Server van het Web van Apache HTTP verstrekt verklaringen voor elke HTTP- aanvraag die de Publish server/de Verzender van het Web van de rij bereikt. Merk op dat de verzoeken die van upstream CDN worden gediend niet in deze logboeken worden weerspiegeld.

Zie de informatie over de indeling van het foutenlogboek in de [officiële documentatie ](https://httpd.apache.org/docs/2.4/logs.html#accesslog).

**Uitvoer voorbeeldlog**

```
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:41 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/favicons/favicon-32.png HTTP/1.1" 200 715 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:41 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/favicons/favicon-512.png HTTP/1.1" 200 9631 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:42 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/country-flags/US.svg HTTP/1.1" 200 810 "https://publish-p6902-e30226.adobeaemcloud.com/content/wknd/us/en.html" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
```

**Logbestandsindeling**

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
<td>01/mei/2020:00:09:46 +000</td>
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
<td>"Mozilla/5.0 (Macintosh); Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"</td>
</tr>
</tbody>
</table>

### Het Apache HTTPD Web Server Access Log {#configuring-the-apache-httpd-webs-server-access-log} configureren

Dit logboek is niet configureerbaar in AEM als Cloud Service.

## Apache HTTPD Web Server Error Log {#apache-httpd-web-server-error-log}

Het foutenlogboek van de Server van het Web van Apache HTTP verstrekt verklaringen voor elke fout in de Publish server/de Verzender van het Web van de rij.

Zie de informatie over de indeling van het foutenlogboek in de [officiële documentatie ](https://httpd.apache.org/docs/2.4/logs.html#errorlog).

**Uitvoer voorbeeldlog**

```
Fri Jul 17 02:19:48.093820 2020 [mpm_worker:notice] [pid 1:tid 140272153361288] [cm-p1234-e30226-aem-publish-b86c6b466-b9427] AH00292: Apache/2.4.43 (Unix) Communique/4.3.4-20200424 mod_qos/11.63 configured -- resuming normal operations
Fri Jul 17 02:19:48.093874 2020 [core:notice] [pid 1:tid 140272153361288] [cm-p1234-e30226-aem-publish-b86c6b466-b9427] AH00094: Command line: 'httpd -d /etc/httpd -f /etc/httpd/conf/httpd.conf -D FOREGROUND -D ENVIRONMENT_PROD'
Fri Jul 17 02:29:34.517189 2020 [mpm_worker:notice] [pid 1:tid 140293638175624] [cm-p1234-e30226-aem-publish-b496f64bf-5vckp] AH00295: caught SIGTERM, shutting down
```

**Logbestandsindeling**

<table>
<tbody>
<tr>
<td>Datum en tijd</td>
<td>17 jul. 02:16:42.608913 2020</td>
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

### Het configureren van het Apache HTTPD Web Server Error Log {#configuring-the-apache-httpd-web-server-error-log}

De mod_rewrite logboekniveaus worden bepaald door veranderlijke REWRITE_LOG_LEVEL in het dossier `conf.d/variables/global.var`.

Deze kan worden ingesteld op Fout, Waarschuwen, Info, Foutopsporing en Traceren1 - Trace8, met de standaardwaarde voor Waarschuwen. Om uw te zuiveren RewriteRules, wordt het geadviseerd om het logboekniveau aan Trace2 op te heffen.

Zie de [mod_rewrite moduledocumentatie](https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging) voor meer informatie.

Als u het logniveau per omgeving wilt instellen, gebruikt u de desbetreffende voorwaardelijke vertakking in het bestand global.var, zoals hieronder wordt beschreven:

```
Define REWRITE_LOG_LEVEL Debug
  
<IfDefine ENVIRONMENT_STAGE>
  ...
  Define REWRITE_LOG_LEVEL Warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define REWRITE_LOG_LEVEL Error
  ...
</IfDefine>
```

## Verzendlogboek {#dispatcher-log}

**Voorbeeld**

```
[17/Jul/2020:23:48:06 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures.html" - 475ms [publishfarm/0] [action miss] "publish-p12904-e25628.adobeaemcloud.com"
[17/Jul/2020:23:48:07 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures/climbing-new-zealand/_jcr_content/root/responsivegrid/carousel/item_1571266094599.coreimg.jpeg/1473680817282/sport-climbing.jpeg" 302 10ms [publishfarm/0] [action none] "publish-p12904-e25628.adobeaemcloud.com"
[17/Jul/2020:23:48:07 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures/ski-touring-mont-blanc/_jcr_content/root/responsivegrid/carousel/item_1571168419252.coreimg.jpeg/1572047288089/adobestock-238230356.jpeg" 302 11ms [publishfarm/0] [action none] "publish-p12904-e25628.adobeaemcloud.com"
```

**Logbestandsindeling**

<table>
<tbody>
<tr>
<td>Datum en tijd</td>
<td>[17/jul/2020:23:48:16 +000]</td>
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
<td>Dispatcher response status code</td>
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

### Het vormen van het Logboek van de Fout van de Verzender {#configuring-the-dispatcher-error-log}

De verzenderslogniveaus worden gedefinieerd door de variabele DISP_LOG_LEVEL in het bestand `conf.d/variables/global.var`.

Deze kan worden ingesteld op Fout, Waarschuwen, Info, Foutopsporing en Traceren1, met de standaardwaarde Waarschuwing.

Hoewel het registreren van de Ontvanger verscheidene andere niveaus van registreren granularity steunt, beveelt de AEM als Cloud Service het gebruiken van de hieronder beschreven niveaus aan.

Als u het logniveau per omgeving wilt instellen, gebruikt u de desbetreffende voorwaardelijke vertakking in het `global.var`-bestand, zoals hieronder wordt beschreven:

```
Define DISP_LOG_LEVEL Debug
  
<IfDefine ENVIRONMENT_STAGE>
  ...
  Define DISP_LOG_LEVEL Warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define DISP_LOG_LEVEL Error
  ...
</IfDefine>
```

## Hoe te om Logs {#how-to-access-logs} tot toegang te hebben

### Cloudomgevingen {#cloud-environments}

AEM als Cloud Service logboeken voor cloudservices kunnen worden geopend door het downloaden via de interface van Cloud Manager of door logbestanden op de opdrachtregel via de opdrachtregelinterface van Adobe I/O te volgen. Raadpleeg de logboekdocumentatie [Cloud Manager](/help/implementing/cloud-manager/manage-logs.md) voor meer informatie.

### Lokale SDK {#local-sdk}

AEM als Cloud Service SDK verstrekt logboekdossiers om lokale ontwikkeling te steunen.

AEM logboeken bevinden zich in de map `crx-quickstart/logs`, waar de volgende logboeken kunnen worden weergegeven:

* Java-logbestand AEM: `error.log`
* Logbestand HTTP-aanvraag AEM: `request.log`
* Logbestand HTTP-toegang AEM: `access.log`

Logbestanden van Apache-lagen, inclusief dispatcher, bevinden zich in de Docker-container die de Dispatcher bevat. Zie de [Dispatcher documentation](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html) voor informatie over hoe te om de Dispatcher te beginnen.

De logbestanden ophalen:

1. Typ `docker ps` op de opdrachtregel om de containers weer te geven
1. Als u zich wilt aanmelden bij de container, typt u &quot;`docker exec -it <container> /bin/sh`&quot;, waarbij `<container>` de verzendingscontainer-id van de vorige stap is
1. Ga naar de cachroot onder `/mnt/var/www/html`
1. De logbestanden zijn onder `/etc/httpd/logs`
1. Inspect the logs: ze zijn toegankelijk in de map XYZ, waar de volgende logbestanden kunnen worden weergegeven:
   * Apache HTTPD Web server access log - `httpd_access.log`
   * Logboekfouten van Apache HTTPD-webserver - `httpd_error.log`
   * Logbestanden van verzending - `dispatcher.log`

Logbestanden worden ook rechtstreeks afgedrukt op de einduitvoer. Meestal, zouden deze logboeken DEBUG moeten zijn, die kan worden verwezenlijkt door in het Debug niveau als parameter over te gaan wanneer het runnen van Docker. Bijvoorbeeld:

`DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`

## Fouten opsporen in productie en werkgebied {#debugging-production-and-stage}

In uitzonderlijke omstandigheden moeten de logniveaus worden gewijzigd om zich bij een fijnere granulariteit in het werkgebied of de productieomgeving aan te melden.

Terwijl dit mogelijk is, vereist het veranderingen in de logboekniveaus in de configuratiedossiers in Git van Waarschuwen en Fout aan Zuiver, en het uitvoeren van een plaatsing aan AEM als Cloud Service om deze configuratieveranderingen met de milieu&#39;s te registreren.

Afhankelijk van het verkeer en de hoeveelheid logboekverklaring die door Debug wordt geschreven, kan dit in een negatief prestatieseffect op het milieu resulteren, daarom wordt geadviseerd dat de veranderingen in Stadium en Productie zuivert niveaus zijn:

* Op een verstandige manier en alleen wanneer dat absoluut noodzakelijk is
* Omgekeerd naar de juiste niveaus en zo snel mogelijk opnieuw ingezet

## Logbestanden splitsen {#splunk-logs}

Klanten die Splunk-accounts hebben, kunnen via het ticket voor klantenondersteuning aanvragen dat hun AEM Cloud Service-logbestanden naar de juiste index worden doorgestuurd. De logboekgegevens zijn gelijk aan de gegevens die beschikbaar zijn via het logbestand van Cloud Manager, maar klanten vinden het wellicht handig om de queryfuncties in het product Splunk te gebruiken.

De netwerkbandbreedte verbonden aan logboeken die naar Splunk worden verzonden wordt beschouwd als deel van het I/O gebruik van het Netwerk van de klant.

### Splunk Forwarding {#enabling-splunk-forwarding} inschakelen

In het supportverzoek moeten klanten aangeven:

* Splunk HEC eindpuntadres
* De segmentindex
* De segmentpoort
* De Splunk HEC-token. Zie [deze pagina](https://docs.splunk.com/Documentation/Splunk/8.0.4/Data/HECExamples) voor meer informatie.

De bovenstaande eigenschappen moeten voor elke relevante combinatie van programma/omgevingstype worden gespecificeerd.  Als een klant bijvoorbeeld ontwikkelings-, staging- en productieomgevingen wilde, moeten deze drie informatiesets leveren, zoals hieronder wordt aangegeven.

>[!NOTE]
>
>Splunk forward for sandbox program environment is not supported.

Zorg ervoor dat het eerste verzoek alle ontwikkelomgeving bevat die moet worden ingeschakeld, in aanvulling op de fase-/prodomgevingen.

Als om het even welke nieuwe dev milieu&#39;s na het aanvankelijke verzoek worden gecreeerd om Splunk te hebben door:sturen, maar het niet toegelaten hebben, zou een extra verzoek moeten worden gemaakt.

Merk ook op dat als de ontwikkelmilieu&#39;s zijn gevraagd, het mogelijk is dat andere ontwikkelmilieu&#39;s niet in het verzoek of zelfs zandbakmilieu&#39;s toegelaten Splunk door:sturen zullen hebben en een index van het Splunk zullen delen. Klanten kunnen het veld `aem_env_id` gebruiken om een onderscheid te maken tussen deze omgevingen.

Hieronder vindt u een voorbeeld van een verzoek voor klantenondersteuning:

Programma 123, Production Env

* Splunk HEC eindpuntadres: `splunk-hec-ext.acme.com`
* Splunk-index: acme_123prod (de klant kan kiezen welke noemende overeenkomst het wenst)
* Splunk-poort: 443
* Splunk HEC-token: ABC123

Programma 123, Stage Env

* Splunk HEC eindpuntadres: `splunk-hec-ext.acme.com`
* Splunk-index: acme_123stage
* Splunk-poort: 443
* Splunk HEC-token: ABC123

Programma 123, Dev Envs

* Splunk HEC eindpuntadres: `splunk-hec-ext.acme.com`
* Splunk-index: acme_123dev
* Splunk-poort: 443
* Splunk HEC-token: ABC123

Het kan voldoende zijn dat dezelfde segmentindex voor elke omgeving wordt gebruikt. In dat geval kan ofwel het veld `aem_env_type` worden gebruikt om onderscheid te maken op basis van de waarden dev, stage en prod. Als er meerdere ontwikkelomgevingen zijn, kan het veld `aem_env_id` ook worden gebruikt. Sommige organisaties kunnen een afzonderlijke index voor de logboeken van het productiemilieu kiezen als de bijbehorende index toegang tot een verminderde reeks gebruikers van de Splunk beperkt.

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
