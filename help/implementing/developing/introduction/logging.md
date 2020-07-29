---
title: Logboekregistratie
description: Leer hoe te om globale parameters voor de centrale registrerendienst, specifieke montages voor de individuele diensten te vormen of hoe te om gegevensregistreren te verzoeken.
translation-type: tm+mt
source-git-commit: bbcadf29dbac89191a3a1ad31ee6721f8f57ef95
workflow-type: tm+mt
source-wordcount: '1081'
ht-degree: 2%

---


# Logboekregistratie {#logging}

AEM als Cloud Service is een platform voor klanten om douanecode te omvatten om unieke ervaringen voor hun klantenbasis tot stand te brengen. Met dit in mening, is het registreren een kritieke functie om code uitvoering op lokale ontwikkeling, en wolkenmilieu&#39;s, in het bijzonder de AEM als milieu&#39;s van de Ontwikkelaar van een Cloud Service te zuiveren en te begrijpen.

AEM het registreren en het logboekniveaus worden beheerd in configuratiedossiers die als deel van het AEM project in Git worden opgeslagen, en als deel van het AEM project via de Manager van de Wolk worden opgesteld. Het aanmelden AEM als Cloud Service kan in twee logische reeksen worden opgedeeld:

* AEM registreren, die registreren op het niveau van de AEM toepassing uitvoert
* Apache HTTPD Web Server/Dispatcher-logboekregistratie, die het registreren van de webserver en Dispatcher op de publicatielijst uitvoert.

## AEM {#aem-loggin}

Het registreren op het AEM toepassingsniveau, wordt behandeld door drie logboeken:

1. AEM Java-logboeken, die Java-logboekinstructies voor de AEM toepassing weergeven.
1. De logboeken van het Verzoek van HTTP, die logboekinformatie over HTTP- verzoeken en hun antwoorden registreren die door AEM worden gediend
1. De logboeken van de Toegang van HTTP, die logboek samenvatte informatie en HTTP- verzoeken die door AEM worden gediend

Merk op dat HTTP- verzoeken die van het geheime voorgeheugen van Dispatcher van de Publish rij of upstream CDN worden gediend niet in deze logboeken worden weerspiegeld.

## Java-registratie AEM {#aem-java-logging}

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

### Logbestandsindeling {#log-format}

| Datum en tijd | AEM als Cloud Service dode-id | Logboekniveau | Thread | Java-klasse | Logbericht |
|---|---|---|---|---|---|
| 29.04.2020 21:50:13.398 | `[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]` | `*DEBUG*` | qtp2130572036-1472 | com.example.approval.workflow.impl.CustomApprovalWorkflow | `No specified approver, defaulting to [ Creative Approvers user group ]` |

**Voorbeeld van loguitvoer**

```
22.06.2020 18:33:30.120 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *ERROR* [qtp501076283-1809] io.prometheus.client.dropwizard.DropwizardExports Failed to get value from Gauge
22.06.2020 18:33:30.229 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [qtp501076283-1805] org.apache.sling.auth.core.impl.SlingAuthenticator getAnonymousResolver: Anonymous access not allowed by configuration - requesting credentials
22.06.2020 18:33:30.370 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] org.apache.sling.i18n.impl.JcrResourceBundle Finished loading 0 entries for 'en_US' (basename: <none>) in 4ms
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [FelixLogListener] org.apache.sling.i18n Service [5126, [java.util.ResourceBundle]] ServiceEvent REGISTERED
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *WARN* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] libs.granite.core.components.login.login$jsp j_reason param value 'unknown' cannot be mapped to a valid reason message: ignoring
```

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

## Logboekregistratie HTTP-aanvraag AEM {#aem-http-request-logging}

AEM als het verzoekregistreren van HTTP van een Cloud Service verstrekt inzicht in de HTTP- verzoeken die aan AEM en hun reacties van HTTP in tijdorde worden gemaakt. Dit logboek is nuttig om de Verzoeken van HTTP te begrijpen die aan AEM worden gemaakt en de orde zij worden verwerkt en aan geantwoord.

De sleutel tot het begrip van dit logboek is het in kaart brengen van de HTTP- verzoek en antwoordparen door hun IDs, die door de numerieke waarde in de steunen wordt aangegeven. Merk op dat vaak de verzoeken en hun overeenkomstige reacties andere HTTP- verzoeken en reacties tussen hen in het logboek worden geworpen.

### Logbestandsindeling {#http-request-logging-format}

| Datum en tijd | ID Vragen/beantwoorden |  | HTTP-methode | URL | Protocol | AEM als knooppunt-id voor Cloud Service |
|---|---|---|---|---|---|---|
| 29/apr/2020:19:14:21 +0000 | `[137]` | -> | POST | /conf/global/settings/dam/adminui-extension/metadataprofile/ | HTTP/1.1 | `[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]` |

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

### Logboek configureren {#configuring-the-log}

Het AEM HTTP- verzoeklogboek is niet configureerbaar in AEM als Cloud Service.

## HTTP-toegangsregistratie AEM {#aem-http-access-logging}

AEM als het de toegangslogboek van HTTP van de Cloud Service toont HTTP- verzoeken in tijdorde. Elke logingang vertegenwoordigt het Verzoek van HTTP dat tot AEM toegang heeft.

Dit logboek is nuttig om snel te begrijpen welke HTTP- verzoeken aan AEM worden gemaakt, als zij door de begeleidende code van de de reactiestatus van HTTP te bekijken slagen, en hoe lang het HTTP- verzoek duurde om te voltooien. Dit logboek kan ook nuttig zijn om de activiteit van een specifieke gebruiker te zuiveren door logboekingangen door Gebruikers te filtreren.

### Logbestandsindeling {#access-log-format}

<table>
<tbody>
<tr>
<td><b>AEM als knooppunt-id voor Cloud Service</b></td>
<td><b>IP-adres van de client</b></td>
<td><b>Gebruiker</b></td>
<td><b>Datum en tijd</b></td>
<td><b>Leeg</b></td>
<td><b>HTTP-methode</b></td>
<td><b>URL</b></td>
<td><b>Protocol</b></td>
<td><b>Leeg</b></td>
<td><b>HTTP-reactiestatus</b></td>
<td><b>HTTP-responstijd in milliseconden</b></td>
<td><b>Referenter</b></td>
<td><b>Gebruikersagent</b></td>
</tr>
<tr>
<td>cm-p1235-e2644-aem-auteur-59555cb5b8-8kgr2</td>
<td>-</td>
<td>myuser@adobe.com</td>
<td>30/apr/2020:17:37:14 +0000</td>
<td>"</td>
<td>GET</td>
<td>/libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css</td>
<td>HTTP/1.1</td>
<td>"</td>
<td>200</td>
<td>1141</td>
<td><code>"https://author-p1234-e4444.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/wknd/en/adventures/surf-camp-in-costa-rica/adobestock_266405335.jpeg&_charset_=utf8"</code></td>
<td>"Mozilla/5.0 (Macintosh); Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"</td>
</tr>
</tbody>
</table>


**Voorbeeld**

```
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css HTTP/1.1" 200 1141 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/customthumb/clientlibs.lc-60e4443805c37afa0c74b674b141f1df-lc.min.css HTTP/1.1" 200 809 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/metadataeditor/clientlibs/metadataeditor.lc-4a2226d8232f8b7ab27d24820b9ddd64-lc.min.js HTTP/1.1" 200 7965 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
```

### Het HTTP Access-logboek configureren {#configuring-the-http-access-log}

Het logboek van de Toegang van HTTP is niet configureerbaar in AEM als Cloud Service.

## Apache-webserver/Dispatcher-aanmelding {#dispatcher-logging}

AEM als Cloud Service verstrekt drie logboeken voor de servers van het Web Apache en verzender laag op Publish:

* Apache HTTPD Web Server Access-logboek
* Apache HTTPD Web Server Error log
* Dispatcher-logboek

Deze logbestanden zijn alleen beschikbaar voor de publicatielijst.

Deze reeks logboeken verstrekt inzichten in HTTP- verzoeken aan de AEM als Cloud Service publiceren rij voorafgaand aan die verzoeken die de AEM toepassing bereiken. Dit is belangrijk om te begrijpen aangezien, idealiter, de meeste HTTP- verzoeken aan de Publish rijservers door caching inhoud door de Server van het Web Apache HTTPD en AEM Dispatcher worden gediend, en nooit de AEM toepassing zelf bereiken, zodat zijn er geen logboekverklaringen voor deze verzoeken in AEM Java, Verzoek of Logboeken van de Toegang.