---
title: Logboekregistratie
description: Leer hoe te om globale parameters voor de centrale registrerendienst, specifieke montages voor de individuele diensten te vormen of hoe te om gegevensregistreren te verzoeken.
translation-type: tm+mt
source-git-commit: a7c8e1ab8e0196a3a79d8e0963192775e64a2400
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 3%

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

### Java-registratie AEM {#aem-java-logging}

AEM als Cloud Service biedt toegang tot Java-loginstructies. Ontwikkelaars van toepassingen voor AEM moeten de algemene Java-logboekbest practices volgen en relevante instructies over de uitvoering van aangepaste code registreren op de volgende logniveaus:

<table>
<tbody>
<tr>
<td> <b>AEM</b></td>
<td> <b>Logboekniveau</b></td>
<td> <b>Beschrijving</b></td>
<td> <b>Beschikbaarheid van logboekverklaring</b></td>
</tr>
<tr>
<td> Ontwikkeling</td>
<td> DEBUG</td>
<td> Beschrijft wat in de toepassing gebeurt.

Wanneer het DEBUG registreren actief is, worden de verklaringen die een duidelijk beeld van verstrekken welke activiteiten voorkomen evenals om het even welke zeer belangrijke parameters die verwerking beïnvloeden geregistreerd.</td>
<td> <ul>
<li> Lokale ontwikkeling</li>
<li>Ontwikkeling</li>
</ul></td>
</tr>
<tr>
<td> Werkgebied</td>
<td> WAARSCHUWING</td>
<td> Beschrijft voorwaarden die het potentieel hebben om fouten te worden.

Wanneer het registreren WARN actief is, slechts worden de verklaringen die op voorwaarden wijzen die sub-optimaliteit naderen geregistreerd.</td>
<td> <ul>
<li> Lokale ontwikkeling</li>
<li>Ontwikkeling</li>
<li>Werkgebied</li>
</ul></td>
</tr>
<tr>
<td> Productie</td>
<td> FOUT</td>
<td> Beschrijft voorwaarden die op een mislukking wijzen, en behoefte om op te lossen.

Wanneer het registreren van de FOUT actief is, slechts worden de verklaringen die op mislukkingen wijzen geregistreerd. FOUTloginstructies geven een ernstig probleem aan dat zo snel mogelijk moet worden opgelost.</td>
<td> <ul>
<li> Lokale ontwikkeling</li>
<li>Ontwikkeling</li>
<li>Werkgebied</li>
<li>Productie</li>
</ul></td>
</tr>
</tbody>
</table>