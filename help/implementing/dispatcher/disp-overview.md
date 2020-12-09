---
title: Dispatcher in de cloud
description: 'Dispatcher in de cloud '
translation-type: tm+mt
source-git-commit: 38a589297caf3b28c7be569a819bd104a5079066
workflow-type: tm+mt
source-wordcount: '4050'
ht-degree: 9%

---


# Dispatcher in de cloud {#Dispatcher-in-the-cloud}

## Configuratie en testen van Apache en Dispatcher {#apache-and-dispatcher-configuration-and-testing}

In deze sectie wordt beschreven hoe u de AEM structureert als Apache- en Dispatcher-configuraties voor Cloud Servicen, en hoe u deze lokaal kunt valideren en uitvoeren voordat u de software implementeert in een cloud-omgeving. Hierin wordt ook foutopsporing in Cloud-omgevingen beschreven. Raadpleeg de [AEM Dispatcher documentation](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/dispatcher.html) voor meer informatie over Dispatcher.

>[!NOTE]
>Windows-gebruikers moeten Windows 10 Professional of andere distributies gebruiken die Docker ondersteunen. Dit is een vereiste voor het uitvoeren van en het zuiveren van Dispatcher op een lokale computer. De onderstaande secties bevatten opdrachten met behulp van de Mac- of Linux-versies van de SDK, maar de Windows SDK kan op dezelfde manier worden gebruikt.

## Verzendgereedschappen {#dispatcher-sdk}

De Dispatcher Tools maken deel uit van de algemene AEM als Cloud Service SDK en verstrekken:

* Een vanilla-bestandsstructuur met de configuratiebestanden die moeten worden opgenomen in een toegewezen project voor dispatcher.
* Tooling voor klanten om te bevestigen dat de verzender configuratie slechts AEM als Cloud Service gesteunde richtlijnen omvat.        Bovendien controleert het gereedschap ook of de syntaxis correct is, zodat de pijn correct kan beginnen.
* Een Docker-afbeelding waarmee de verzender lokaal wordt opgehaald.

## De gereedschappen downloaden en uitpakken {#extracting-the-sdk}

De Dispatcher Tools, onderdeel van [AEM als Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md), kunnen van een ZIP dossier bij [de portal van de Distributie van de Software worden gedownload ](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html). Elke nieuwe configuratie die beschikbaar is in die nieuwe versie van Dispatcher Tools, kan worden gebruikt om te worden geïmplementeerd in Cloud-omgevingen waarop die versie van AEM in de cloud of hoger wordt uitgevoerd.

Pak de SDK uit, die de Dispatcher Tools voor zowel MacOS/Linux als Windows bundelt.

**Voor MacOS/Linux** moet u het artefact van het verzendprogramma uitvoerbaar maken en uitvoeren. De Dispatcher Tools-bestanden worden automatisch uitgepakt onder de map waarin u de Dispatcher Tools hebt opgeslagen (waarbij `version` de versie van de Dispatcher Tools is).

```bash
$ chmod +x aem-sdk-dispatcher-tools-<version>-unix.sh
$ ./aem-sdk-dispatcher-tools-<version>-unix.sh
Verifying archive integrity...  100%   All good.
Uncompressing aem-sdk-dispatcher-tools-<version>-unix.sh 100%
```

**Voor Windows** pakt u het ZIP-archief van Dispatcher Tooling uit.

## Bestandsstructuur {#file-structure}

De structuur van de submap van de verzender van het project wordt hieronder beschreven en moet naar de toegewezen map van de projectverzender worden gekopieerd:

```bash
./
├── conf.d
│   ├── available_vhosts
│   │   └── default.vhost
│   ├── dispatcher_vhost.conf
│   ├── enabled_vhosts
│   │   ├── README
│   │   └── default.vhost -> ../available_vhosts/default.vhost
│   └── rewrites
│   │   ├── default_rewrite.rules
│   │   └── rewrite.rules
│   └── variables
|       ├── custom.vars
│       └── global.vars
└── conf.dispatcher.d
    ├── available_farms
    │   └── default.farm
    ├── cache
    │   ├── default_invalidate.any
    │   ├── default_rules.any
    │   └── rules.any
    ├── clientheaders
    │   ├── clientheaders.any
    │   └── default_clientheaders.any
    ├── dispatcher.any
    ├── enabled_farms
    │   ├── README
    │   └── default.farm -> ../available_farms/default.farm
    ├── filters
    │   ├── default_filters.any
    │   └── filters.any
    ├── renders
    │   └── default_renders.any
    └── virtualhosts
        ├── default_virtualhosts.any
        └── virtualhosts.any
```

Hieronder vindt u een uitleg van belangrijke bestanden die kunnen worden gewijzigd:

**Aanpasbare bestanden**

De volgende bestanden kunnen worden aangepast en worden bij de implementatie overgebracht naar uw Cloud-instantie:

* `conf.d/available_vhosts/<CUSTOMER_CHOICE>.vhost`

U kunt een of meer van deze bestanden hebben. Zij bevatten `<VirtualHost>` ingangen die gastheernamen aanpassen en Apache toestaan om elk domeinverkeer met verschillende regels te behandelen. Bestanden worden gemaakt in de map `available_vhosts` en ingeschakeld met een symbolische koppeling in de map `enabled_vhosts`. Van de `.vhost` dossiers, zullen andere dossiers zoals herschrijft en variabelen worden omvat.

* `conf.d/rewrites/rewrite.rules`

Dit bestand wordt opgenomen vanuit uw `.vhost`-bestanden. Het heeft een reeks herschrijfregels voor `mod_rewrite`.

>[!NOTE]
>
>Op dit moment moet één herschrijfbestand worden gebruikt in plaats van sitespecifieke bestanden. De bestandsgrootte moet kleiner zijn dan 1 MB.

* `conf.d/variables/custom.vars`

Dit bestand wordt opgenomen vanuit uw `.vhost`-bestanden. U kunt op deze locatie definities voor Apache-variabelen plaatsen.

* `conf.d/variables/global.vars`

Dit bestand wordt opgenomen vanuit het `dispatcher_vhost.conf`-bestand. U kunt de verzender wijzigen en het logniveau in dit bestand wijzigen.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

U kunt één of meerdere van deze dossiers hebben, en zij bevatten landbouwbedrijven om gastheernamen aan te passen en de dispatchermodule toe te staan om elk landbouwbedrijf met verschillende regels te behandelen. Bestanden worden gemaakt in de map `available_farms` en ingeschakeld met een symbolische koppeling in de map `enabled_farms`. Van de `.farm` dossiers, zullen andere dossiers zoals filters, geheim voorgeheugenregels en anderen worden omvat.

* `conf.dispatcher.d/cache/rules.any`

Dit bestand wordt opgenomen vanuit uw `.farm`-bestanden. Hiermee geeft u voorkeuren voor caching op.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

Dit bestand wordt opgenomen vanuit uw `.farm`-bestanden. Het specificeert welke verzoekkopballen aan het achtereind door:sturen.

* `conf.dispatcher.d/filters/filters.any`

Dit bestand wordt opgenomen vanuit uw `.farm`-bestanden. Het heeft een reeks regels die veranderen welk verkeer uit zou moeten worden gefiltreerd en niet het aan het achterste eind maken.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

Dit bestand wordt opgenomen vanuit uw `.farm`-bestanden. Het heeft een lijst van gastheernamen of de wegen van URI die door glob aanpassing moeten worden aangepast. Dit bepaalt welke achtergrond om een verzoek te dienen.

De bovenstaande bestanden verwijzen naar de onderstaande onveranderlijke configuratiebestanden. Wijzigingen in de onveranderbare bestanden worden niet verwerkt door verzenders in Cloud-omgevingen.

**Immuable Configuration Files**

Deze bestanden maken deel uit van het basiskader en zorgen ervoor dat standaarden en beste praktijken worden nageleefd. De bestanden worden als onveranderlijk beschouwd, omdat het wijzigen of verwijderen ervan lokaal geen invloed heeft op uw implementatie, omdat deze bestanden niet worden overgedragen naar uw Cloud-instantie.

Het wordt aanbevolen dat de bovenstaande bestanden verwijzen naar de hieronder vermelde onveranderlijke bestanden, gevolgd door aanvullende instructies of overschrijvingen. Wanneer de configuratie van de verzender aan een wolkenmilieu wordt opgesteld, zal de recentste versie van de onveranderlijke dossiers worden gebruikt, ongeacht welke versie in lokale ontwikkeling werd gebruikt.

* `conf.d/available_vhosts/default.vhost`

Bevat een virtuele voorbeeldhost. Voor uw eigen virtuele host maakt u een kopie van dit bestand, past u het aan, gaat u naar `conf.d/enabled_vhosts` en maakt u een symbolische koppeling naar uw aangepaste kopie.

* `conf.d/dispatcher_vhost.conf`

Deel van het basisframework dat wordt gebruikt om te illustreren hoe uw virtuele hosts en globale variabelen worden opgenomen.

* `conf.d/rewrites/default_rewrite.rules`

Standaard herschrijft regels geschikt voor een standaardproject. Als u aanpassing nodig hebt, wijzigt u `rewrite.rules`. In uw aanpassing, kunt u nog de standaardregels eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/available_farms/default.farm`

Bevat een bedrijf van de steekproefdispatcher. Voor uw eigen landbouwbedrijf, creeer een exemplaar van dit dossier, pas het aan, ga naar `conf.d/enabled_farms` en creeer een symbolische verbinding aan uw aangepaste exemplaar.

* `conf.dispatcher.d/cache/default_invalidate.any`

Een deel van het basiskader, wordt geproduceerd bij opstarten. U bent **required** om dit dossier in elk landbouwbedrijf te omvatten u, in `cache/allowedClients` sectie bepaalt.

* `conf.dispatcher.d/cache/default_rules.any`

De standaard geheim voorgeheugenregels geschikt voor een standaardproject. Als u aanpassing nodig hebt, wijzigt u `conf.dispatcher.d/cache/rules.any`. In uw aanpassing, kunt u nog de standaardregels eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/clientheaders/default_clientheaders.any`

De standaard verzoekkopballen om aan het achterste deel door:sturen, geschikt voor een standaardproject. Als u aanpassing nodig hebt, wijzigt u `clientheaders.any`. In uw aanpassing, kunt u nog de standaardverzoekkopballen eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/dispatcher.any`

Deel van basisframework dat wordt gebruikt om te illustreren hoe de kwekerijen van de dispatcher worden opgenomen.

* `conf.dispatcher.d/filters/default_filters.any`

Standaardfilters die geschikt zijn voor een standaardproject. Als u aanpassing nodig hebt, wijzigt u `filters.any`. In uw aanpassing, kunt u nog de standaardfilters eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/renders/default_renders.any`

Als onderdeel van het basisframework wordt dit bestand bij het opstarten gegenereerd. U bent **required** om dit dossier in elk landbouwbedrijf te omvatten u, in `renders` sectie bepaalt.

* `conf.dispatcher.d/virtualhosts/default_virtualhosts.any`

Standaardhostglobing geschikt voor een standaardproject. Als u aanpassing nodig hebt, wijzigt u `virtualhosts.any`. In uw aanpassing, zou u niet de standaard gastheer het globbings moeten omvatten, aangezien het **elke** inkomend verzoek aanpast.

>[!NOTE]
>
>De AEM als Cloud Service wordt gemaakt archetype zal de zelfde structuur van het dossier van de berichtconfiguratie produceren.

In de onderstaande secties wordt beschreven hoe u de configuratie lokaal kunt valideren zodat deze de bijbehorende kwaliteitspoort in Cloud Manager kan doorgeven bij het implementeren van een interne release.

## Lokale validatie van ondersteunde richtlijnen in Dispatcher-configuratie {#local-validation-of-dispatcher-configuration}

Het validatieprogramma is beschikbaar in de SDK op `bin/validator` als een binaire versie van Mac OS, Linux of Windows, zodat klanten dezelfde validatie kunnen uitvoeren als Cloud Manager bij het maken en implementeren van een release.

Deze wordt aangeroepen als: `validator full [-d folder] [-w whitelist] zip-file | src folder`

Met dit hulpprogramma wordt gecontroleerd of in de configuratie van de dispatcher de juiste instructies worden gebruikt die door AEM als cloudservice worden ondersteund, door alle bestanden te scannen met patroon `conf.d/enabled_vhosts/*.vhost`. De instructies die zijn toegestaan in Apache-configuratiebestanden, kunnen worden weergegeven door de opdracht lijst van gewenste personen van de validator uit te voeren:

```
$ validator whitelist
Cloud manager validator 2.0.4
 
Whitelisted directives:
  <Directory>
  ...
  
```

In de onderstaande tabel staan de ondersteunde apache-modules:

| Modulenaam | Referentiepagina |
|---|---|
| `core` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/core.html) |
| `mod_access_compat` | [https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html) |
| `mod_alias` | [https://httpd.apache.org/docs/2.4/mod/mod_alias.html](https://httpd.apache.org/docs/2.4/mod/mod_alias.html) |
| `mod_allowmethods` | [https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html](https://httpd.apache.org/docs/2.4/mod/mod_allowmethods.html) |
| `mod_authn_core` | [https://httpd.apache.org/docs/2.4/mod/mod_authn_core.html](https://httpd.apache.org/docs/2.4/mod/mod_authn_core.html) |
| `mod_authn_file` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/mod_authn_file.html) |
| `mod_authz_core` | [https://httpd.apache.org/docs/2.4/mod/core.html](https://httpd.apache.org/docs/2.4/mod/mod_authz_core.html) |
| `mod_authz_groupfile` | [https://httpd.apache.org/docs/2.4/mod/mod_authz_groupfile.html](https://httpd.apache.org/docs/2.4/mod/mod_authz_groupfile.html) |
| `mod_deflate` | [https://httpd.apache.org/docs/2.4/mod/mod_deflate.html](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html) |
| `mod_dir` | [https://httpd.apache.org/docs/2.4/mod/mod_dir.html](https://httpd.apache.org/docs/2.4/mod/mod_dir.html) |
| `mod_env` | [https://httpd.apache.org/docs/2.4/mod/mod_env.html](https://httpd.apache.org/docs/2.4/mod/mod_env.html) |
| `mod_filter` | [https://httpd.apache.org/docs/2.4/mod/mod_filter.html](https://httpd.apache.org/docs/2.4/mod/mod_filter.html) |
| `mod_headers` | [https://httpd.apache.org/docs/2.4/mod/mod_headers.html](https://httpd.apache.org/docs/2.4/mod/mod_headers.html) |
| `mod_mime` | [https://httpd.apache.org/docs/2.4/mod/mod_mime.html](https://httpd.apache.org/docs/2.4/mod/mod_mime.html) |
| `mod_remoteip` | [https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html](https://httpd.apache.org/docs/2.4/mod/mod_remoteip.html) |
| `mod_reqtimeout` | [https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html](https://httpd.apache.org/docs/2.4/mod/mod_reqtimeout.html) |
| `mod_rewrite` | [https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html) |
| `mod_security` | [https://modsecurity.org/](https://modsecurity.org/) |
| `mod_setenvif` | [https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html) |
| `mod_substitute` | [https://httpd.apache.org/docs/2.4/mod/mod_substitute.html](https://httpd.apache.org/docs/2.4/mod/mod_substitute.html) |
| `mod_userdir` | [https://httpd.apache.org/docs/2.4/mod/mod_userdir.html](https://httpd.apache.org/docs/2.4/mod/mod_userdir.html) |

Klanten kunnen geen arbitraire modules toevoegen, maar in de toekomst kunnen wel extra modules in het product worden opgenomen. Klanten kunnen de lijst met instructies vinden die beschikbaar is voor een bepaalde versie van Dispatcher door de opdracht lijst van gewenste personen van de validator uit te voeren in de SDK, zoals hierboven beschreven.

De lijst van gewenste personen bevat een lijst met Apache-instructies die zijn toegestaan in een klantconfiguratie. Als een instructie niet is toegevoegd op lijst van gewenste personen, wordt een fout geregistreerd en wordt een afsluitcode van niet nul geretourneerd. Als geen lijst van gewenste personen op de bevellijn wordt gegeven (die de manier is het zou moeten worden aangehaald), gebruikt het hulpmiddel een standaard lijst van gewenste personen die de Manager van de Wolk voor bevestiging alvorens aan milieu&#39;s van de Wolk zal gebruiken te opstellen.

Bovendien worden alle bestanden met patroon `conf.dispatcher.d/enabled_farms/*.farm` gescand en wordt gecontroleerd of:

* Er bestaat geen filterregel die gebruik toestaat via `/glob` (zie [CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957) voor meer informatie)
* Er wordt geen beheerfunctie weergegeven. Bijvoorbeeld toegang tot paden zoals `/crx/de or /system/console`.

Wanneer de looppas tegen uw beven artefact of uw `dispatcher/src` subdirectory, zal het bevestigingsmislukkingen melden:

```
$ validator full dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-whitelisted directives:
  conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
  conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

Let op: het validatiehulpmiddel rapporteert alleen het verboden gebruik van Apache-instructies die niet zijn toegevoegd op lijst van gewenste personen. Er worden geen syntactische of semantische problemen met uw Apache-configuratie gemeld, aangezien deze informatie alleen beschikbaar is voor Apache-modules in een actieve omgeving.

Hieronder vindt u technieken voor het oplossen van problemen waarmee algemene validatiefouten kunnen worden opgespoord die door het programma worden uitgevoerd:

**kan geen  `conf.dispatcher.d` submap vinden in het archief**

Uw archief moet mappen `conf.d` en `conf.dispatcher.d` bevatten. Let op: gebruik het voorvoegsel `etc/httpd` **niet** in uw archief.

**geen bedrijf kunnen vinden in`conf.dispatcher.d/enabled_farms`**

Uw ingeschakelde landbouwbedrijven zouden in bovengenoemde subfolder moeten worden gevestigd.

**Ingesloten bestand (...) moet een naam hebben: ...**

Er zijn twee secties in uw landbouwbedrijfconfiguratie die **must** omvat
specifiek bestand: `/renders` en `/allowedClients` in de sectie `/cache`. Die
de secties moeten er als volgt uitzien:

```
/renders {
    $include "../renders/default_renders.any"
}
```

and:

```
/allowedClients {
    $include "../cache/default_invalidate.any"
}
```

**bestand opgenomen op onbekende locatie: ...**

Er zijn vier secties in uw landbouwbedrijfconfiguratie waar u uw eigen dossier mag omvatten: `/clientheaders`, `filters`, `/rules` in `/cache` sectie en `/virtualhosts`. De opgenomen bestanden moeten als volgt worden benoemd:

| Sectie | Bestandsnaam opnemen |
|------------------|--------------------------------------|
| `/clientheaders` | `../clientheaders/clientheaders.any` |
| `/filters` | `../filters/filters.any` |
| `/rules` | `../cache/rules.any` |
| `/virtualhosts` | `../virtualhosts/virtualhosts.any` |

U kunt ook de **standaardversie** van deze bestanden opnemen, waarvan de namen worden voorafgegaan door het woord `default_`, bijvoorbeeld `../filters/default_filters.any`.

**include statement at (...), outside any known location: ...**

Behalve de zes secties die in de bovenstaande paragrafen worden vermeld, bent u niet toegestaan
als u de instructie `$include` wilt gebruiken, wordt deze fout bijvoorbeeld gegenereerd door:

```
/invalidate {
    $include "../cache/invalidate.any"
}
```

**toegestane clients/renderingen zijn niet inbegrepen bij: ...**

Deze fout wordt geproduceerd wanneer u geen omvat voor `/renders` en `/allowedClients` in `/cache` sectie specificeert. Zie de
**Ingesloten bestand (...) moet een naam hebben: ...** voor meer informatie.

**filter mag geen globpatroon gebruiken om verzoeken toe te staan**

Het is niet veilig om verzoeken met een `/glob` stijlregel toe te staan, die tegen de volledige verzoeklijn, bijvoorbeeld wordt aangepast.

```
/0100 {
    /type "allow" /glob "GET *.css *"
}
```

Deze verklaring is bedoeld om verzoeken om `css` dossiers toe te staan, maar het staat ook verzoeken aan **any** middel toe die door het vraagkoord `?a=.css` wordt gevolgd. Het is daarom verboden dergelijke filters te gebruiken (zie ook CVE-2016-0957).

**opgenomen bestand (...) komt niet overeen met een bekend bestand**

Er zijn twee typen bestanden in uw virtuele Apache-hostconfiguratie die als volgt kunnen worden opgegeven: herschrijft en variabelen.
De opgenomen bestanden moeten als volgt worden benoemd:

| Type | Bestandsnaam opnemen |
|-----------|---------------------------------|
| Herschrijven | `conf.d/rewrites/rewrite.rules` |
| Variabelen | `conf.d/variables/custom.vars` |

U kunt ook de standaardversie **default** van de herschrijfregels opnemen, waarvan de naam `conf.d/rewrites/default_rewrite.rules` is.
Er is geen standaardversie van de variabelebestanden.

**Verouderde configuratielay-out gedetecteerd, compatibiliteitsmodus ingeschakeld**

Dit bericht wijst erop dat uw configuratie verouderde versie 1 lay-out heeft, die een volledige bevat
Apache-configuratie en bestanden met `ams_` voorvoegsels. Hoewel dit nog steeds wordt ondersteund voor achteruit
moet u schakelen naar de nieuwe indeling.

## Lokale validatie van de syntaxis van de verzendersconfiguratie zodat apache httpd {#local-validation} kan starten

Als is vastgesteld dat de configuratie van de verzendmodule alleen ondersteunde instructies bevat, moet u controleren of de syntaxis correct is, zodat apache kan worden gestart. Om dit te testen, moet de docker plaatselijk worden geïnstalleerd. Let op: het is niet nodig dat AEM actief is.

Gebruik het `validate.sh` manuscript zoals hieronder getoond:

```
$ validate.sh src/dispatcher
Phase 1: Dispatcher validator
2019/06/19 16:02:55 No issues found
Phase 1 finished
Phase 2: httpd -t validation in docker image
Running script /docker_entrypoint.d/10-create-docroots.sh
Running script /docker_entrypoint.d/20-wait-for-backend.sh
Waiting until aemhost is available
aemhost resolves to xx.xx.xx.xx
Running script /docker_entrypoint.d/30-allowed-clients.sh
# Dispatcher configuration: (/etc/httpd/conf.dispatcher.d/dispatcher.any)
/farms {
...
}
Syntax OK
Phase 2 finished
```

Het script doet het volgende:

1. De validator wordt uitgevoerd vanuit de vorige sectie om ervoor te zorgen dat alleen de ondersteunde instructies worden opgenomen. Als de configuratie ongeldig is, zal het manuscript ontbreken.
2. De code voert `httpd -t command` uit om te testen of de syntaxis correct is zodat apache httpd kan starten. Indien succesvol, zou de configuratie klaar voor plaatsing moeten zijn

Tijdens de implementatie van Cloud Manager wordt de `httpd -t syntax`-controle ook uitgevoerd en worden eventuele fouten opgenomen in het logbestand voor Cloud Manager `Build Images step failure`.

## Uw Apache- en Dispatcher-configuratie lokaal testen {#testing-apache-and-dispatcher-configuration-locally}

Het is ook mogelijk om uw Apache- en Dispatcher-configuratie lokaal te testen. Hiervoor moet de docker lokaal zijn geïnstalleerd en moet uw configuratie voldoen aan de bovenstaande validatie.

Voer het validatiehulpmiddel uit (merk op dat het van `validator.sh` eerder genoemd) verschillend is, door de `-d` parameter te gebruiken die een omslag met alle de configuratiedossiers van de verzender uitvoert. Voer vervolgens het script `docker_run.sh` uit en geef die map door als een argument. Door het poortnummer op te geven (hier: 8080) om het verzender eindpunt bloot te stellen, is een container van de Dok begonnen, die de verzender met uw configuratie in werking stelt.

```
$ validator full -d out src/dispatcher
2019/06/19 16:02:55 No issues found
$ docker_run.sh out docker.for.mac.localhost:4503 8080
Running script /docker_entrypoint.d/10-create-docroots.sh
Running script /docker_entrypoint.d/20-wait-for-backend.sh
Waiting until aemhost is available
aemhost resolves to xx.xx.xx.xx
Running script /docker_entrypoint.d/30-allowed-clients.sh
Starting httpd server
...
```

Hierdoor start de dispatcher in een container met de achterkant naar een AEM instantie die op uw lokale Mac OS-computer op poort 4503 wordt uitgevoerd.

## Fouten opsporen in uw Apache- en Dispatcher-configuratie {#debugging-apache-and-dispatcher-configuration}

De volgende strategie kan worden gebruikt om de logboekoutput voor de verzender module te verhogen en de resultaten van de `RewriteRule` evaluatie in zowel lokale als wolkenmilieu&#39;s te zien.

Logniveaus voor deze modules worden gedefinieerd door de variabelen `DISP_LOG_LEVEL` en `REWRITE_LOG_LEVEL`. Ze kunnen worden ingesteld in het bestand `conf.d/variables/global.vars`. Het relevante deel is als volgt:

```
# Log level for the dispatcher
#
# Possible values are: Error, Warn, Info, Debug and Trace1
# Default value: Warn
#
# Define DISP_LOG_LEVEL Warn
 
# Log level for mod_rewrite
#
# Possible values are: Error, Warn, Info, Debug and Trace1 - Trace8
# Default value: Warn
#
# To debug your RewriteRules, it is recommended to raise your log
# level to Trace2.
#
# More information can be found at:
# https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging
#
# Define REWRITE_LOG_LEVEL Warn
```

Wanneer het in werking stellen van verzender plaatselijk, worden de logboeken gedrukt direct aan de eindoutput. Meestal, wilt u deze logboeken in DEBUG zijn, die kan worden gedaan door het Debug niveau als parameter over te gaan wanneer het runnen van Docker. Bijvoorbeeld: `DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`.

Logbestanden voor cloudomgevingen worden weergegeven via de logbestandsservice die beschikbaar is in Cloud Manager.

## Verschillende Dispatcher-configuraties per omgeving {#different-dispatcher-configurations-per-environment}

Op dit moment wordt dezelfde configuratie van de verzender toegepast op alle AEM als een Cloud Service-omgeving. De runtime heeft een omgevingsvariabele `ENVIRONMENT_TYPE` die de huidige uitvoermodus (dev, stage of prod) en een definitie bevat. De definitie kan `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE` of `ENVIRONMENT_PROD` zijn. In de Apache-configuratie kan de variabele rechtstreeks in een expressie worden gebruikt. U kunt ook de definitie gebruiken om logica op te bouwen:

```
# Simple usage of the environment variable
ServerName ${ENVIRONMENT_TYPE}.company.com
 
# When more logic is required
<IfDefine ENVIRONMENT_STAGE>
  # These statements are for stage
  Define VIRTUALHOST stage.example.com
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  # These statements are for production
  Define VIRTUALHOST prod.example.com
</IfDefine>
```

In de configuratie van de Verzender, is de zelfde milieuvariabele beschikbaar. Als meer logica wordt vereist, bepaal de variabelen zoals aangetoond in het bovenstaande voorbeeld en gebruik dan hen in de de configuratiesectie van de Verzender:

```
/virtualhosts {
  { "${VIRTUALHOST}" }
}
```

Wanneer u uw configuratie lokaal test, kunt u verschillende omgevingstypen simuleren door de variabele `DISP_RUN_MODE` rechtstreeks door te geven aan het `docker_run.sh`-script:

```
$ DISP_RUN_MODE=stage docker_run.sh out docker.for.mac.localhost:4503 8080
```

De standaardrunmode wanneer het overgaan niet in een waarde voor DISP_RUN_MODE is &quot;dev&quot;.
Voor een volledige lijst van beschikbare opties en variabelen, stel het manuscript `docker_run.sh` zonder argumenten in werking.

## De Dispatcher-configuratie bekijken die wordt gebruikt door uw Docker-container {#viewing-dispatcher-configuration-in-use-by-docker-container}

Met milieu-specifieke configuraties, kan het moeilijk zijn om te bepalen hoe de daadwerkelijke configuratie van de Verzender kijkt als. Nadat u de docker container met `docker_run.sh` hebt gestart, kan deze als volgt worden gedumpt:

* Bepaal de gebruikte dockercontainer-id:

```
$ docker ps
CONTAINER ID       IMAGE
d75fbd23b29        adobe/aem-ethos/dispatcher-publish:...
```

* Voer de volgende bevellijn met die containeridentiteitskaart uit:

```
$ docker exec d75fbd23b29 httpd-test
# Dispatcher configuration: (/etc/httpd/conf.dispatcher.d/dispatcher.any)
/farms {
  /publishfarm {
    /clientheaders {
...
```

## Belangrijkste verschillen tussen AMS Dispatcher en AEM als Cloud Service {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service}

Zoals hierboven op de referentiepagina is beschreven, lijkt de Apache- en Dispatcher-configuratie in AEM als Cloud Service sterk op die van AMS. De belangrijkste verschillen zijn:

* In AEM als Cloud Service kunnen sommige Apache-instructies niet worden gebruikt (bijvoorbeeld `Listen` of `LogLevel`)
* In AEM als Cloud Service, slechts kunnen sommige stukken van de configuratie van de Verzender in omvat dossiers worden gezet en hun het noemen is belangrijk. Zo moeten filterregels die u op verschillende hosts opnieuw wilt gebruiken, in een bestand met de naam `filters/filters.any` worden geplaatst. Zie de referentiepagina voor meer informatie.
* In AEM als Cloud Service is er extra bevestiging om filterregels te verbieden die worden geschreven gebruikend `/glob` om veiligheidskwesties te verhinderen. Aangezien `deny *` eerder dan `allow *` (die niet kan worden gebruikt) zal worden gebruikt, zullen klanten van het uitvoeren van de Dispatcher plaatselijk profiteren en het doen van proef en fout, bekijkend de logboeken om precies te weten welke wegen de filters van de Verzender blokkeren opdat die kunnen worden toegevoegd.

## Richtlijnen voor het migreren van de configuratie van de verzender van AMS naar AEM als Cloud Service

De configuratiestructuur van de verzender heeft verschillen tussen Managed Services en AEM als Cloud Service. Hieronder wordt een stapsgewijze handleiding gepresenteerd voor het migreren van AMS Dispatcher Configuration versie 2 naar AEM als Cloud Service.

## Een AMS converteren naar een AEM als configuratie voor een serviceverzender in de cloud

In de volgende sectie vindt u stapsgewijze instructies voor het omzetten van een AMS-configuratie. Het veronderstelt
dat u een archief hebt met een structuur die vergelijkbaar is met de structuur die wordt beschreven in [Configuratie van de vouwmanager-dispatcher](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html)

### Het archief extraheren en een eventueel voorvoegsel verwijderen

Extraheer het archief naar een map en zorg ervoor dat de directe submappen beginnen met `conf`, `conf.d`,
`conf.dispatcher.d` en `conf.modules.d`. Als ze dat niet doen, verplaats ze omhoog in de hiërarchie.

### Ongebruikte submappen en bestanden verwijderen

Submappen `conf` en `conf.modules.d` verwijderen, evenals bestanden die overeenkomen met `conf.d/*.conf`.

### Alle niet-gepubliceerde virtuele hosts verwijderen

Verwijder elk virtueel hostbestand in `conf.d/enabled_vhosts` met `author`, `unhealthy`, `health`,
`lc` of `flush` in de naam. Alle virtuele hostbestanden in `conf.d/available_vhosts` die niet
kan ook worden verwijderd.

### Verwijder of becommentarieer virtuele hostsecties die niet verwijzen naar poort 80

Als u nog secties in uw virtuele hostbestanden hebt die uitsluitend verwijzen naar andere poorten dan poort 80, b.v.

```
<VirtualHost *:443>
...
</VirtualHost>
```

verwijder deze dan of plaats een opmerking. Instructies in deze secties worden niet verwerkt, maar als u ze niet verwijdert, kan het gebeuren dat u ze alsnog bewerkt, zonder effect. En dat kan verwarrend zijn.

### Herschrijvingen controleren

Voer de map `conf.d/rewrites` in.

Verwijder elk bestand met de naam `base_rewrite.rules` en `xforwarded_forcessl_rewrite.rules` en vergeet niet
`Include`-instructies in de virtuele hostbestanden verwijderen die naar deze instructies verwijzen.

Als `conf.d/rewrites` nu één bestand bevat, moet de naam worden gewijzigd in `rewrite.rules` en niet
vergeet de `Include`-instructies die naar dat bestand verwijzen, ook in de virtuele hostbestanden aan te passen.

Als de map echter meerdere, virtuele hostspecifieke bestanden bevat, moet de inhoud ervan
gekopieerd naar de instructie `Include` die ernaar verwijst in de virtuele hostbestanden.

### Variabelen controleren

Voer de map `conf.d/variables` in.

Verwijder een bestand met de naam `ams_default.vars` en vergeet niet `Include`-instructies in het virtuele bestand te verwijderen
hostbestanden die naar deze bestanden verwijzen.

Als `conf.d/variables` nu één bestand bevat, moet de naam worden gewijzigd in `custom.vars` en niet
vergeet de `Include`-instructies die naar dat bestand verwijzen, ook in de virtuele hostbestanden aan te passen.

Als de map echter meerdere, virtuele hostspecifieke bestanden bevat, moet de inhoud ervan
gekopieerd naar de instructie `Include` die ernaar verwijst in de virtuele hostbestanden.

### Lijsten van gewenste personen verwijderen

Verwijder de map `conf.d/whitelists` en verwijder `Include` instructies in de virtuele hostbestanden die verwijzen naar
een bestand in die submap.

### Variabelen vervangen die niet meer beschikbaar zijn

In alle virtuele hostbestanden:

Naam van `PUBLISH_DOCROOT` wijzigen in `DOCROOT`
Secties verwijderen die verwijzen naar de variabelen `DISP_ID`, `PUBLISH_FORCE_SSL` of `PUBLISH_WHITELIST_ENABLED`

### Uw status controleren door de validatietool uit te voeren

Voer de dispatchervalidator in uw map uit met de subopdracht `httpd`:

```
$ validator httpd .
```

Als er fouten optreden over ontbrekende Include-bestanden, controleert u of de naam van die bestanden correct is gewijzigd.

Als u Apache-instructies ziet die niet zijn toegevoegd op lijst van gewenste personen, verwijdert u deze.

### Alle niet-publicatiefarms verwijderen

Verwijder om het even welk landbouwbedrijfdossier in `conf.dispatcher.d/enabled_farms` dat `author`, `unhealthy`, `health` heeft,
`lc` of `flush` in de naam. Alle landbouwbedrijfdossiers in `conf.dispatcher.d/available_farms` die niet zijn
kan ook worden verwijderd.

### De naam van farmbestanden wijzigen

Alle bedrijven in `conf.d/enabled_farms` moeten een andere naam krijgen om overeen te komen met het patroon `*.farm`, dus bijvoorbeeld een
Het landbouwbedrijfdossier genoemd `customerX_farm.any` zou moeten worden anders genoemd `customerX.farm`.

### Cache controleren

Voer de map `conf.dispatcher.d/cache` in.

Verwijder alle bestanden met het voorvoegsel `ams_`.

Als `conf.dispatcher.d/cache` nu leeg is, kopieert u het bestand `conf.dispatcher.d/cache/rules.any`
vanuit de standaardconfiguratie van de verzender naar deze map. De standaardverzender
Deze configuratie vindt u in de map `src` van deze SDK. Vergeet niet de
`$include` instructies die verwijzen naar de `ams_*_cache.any`-regelbestanden in de landbouwbedrijfsbestanden
ook.

Als `conf.dispatcher.d/cache` nu een enkel bestand bevat met achtervoegsel `_cache.any`,
moet de naam van het bestand worden gewijzigd in `rules.any` en vergeet niet om de `$include`-instructies aan te passen
die ook verwijzen naar dat dossier in de landbouwbedrijfdossiers.

Als de map echter meerdere, boerderspecifieke bestanden met dat patroon bevat, de inhoud ervan
moet naar de `$include` verklaring worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

Verwijder elk bestand met het achtervoegsel `_invalidate_allowed.any`.

Het bestand `conf.dispatcher.d/cache/default_invalidate_any` kopiëren uit de standaardmap
AEM in de configuratie van de Cloud-dispatcher naar die locatie.

In elk landbouwbedrijfdossier, verwijder om het even welke inhoud in `cache/allowedClients` sectie en vervang het
met:

```
$include "../cache/default_invalidate.any"
```

### Clientheaders controleren

Voer de map `conf.dispatcher.d/clientheaders` in.

Verwijder alle bestanden met het voorvoegsel `ams_`.

Als `conf.dispatcher.d/clientheaders` nu één bestand met achtervoegsel `_clientheaders.any` bevat,
moet de naam van het bestand worden gewijzigd in `clientheaders.any` en vergeet niet om de `$include`-instructies aan te passen
die ook verwijzen naar dat dossier in de landbouwbedrijfdossiers.

Als de map echter meerdere, boerderspecifieke bestanden met dat patroon bevat, de inhoud ervan
moet naar de `$include` verklaring worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

Het bestand `conf.dispatcher/clientheaders/default_clientheaders.any` kopiëren uit de standaardmap
AEM als configuratie van de Cloud Service verzender aan die plaats.

In elk farmbestand vervangt u elke include-instructie voor clientheaders die er als volgt uitziet:

```
$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"
$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"
```

met de instructie:

```
$include "../clientheaders/default_clientheaders.any"
```

### Filter controleren

Voer de map `conf.dispatcher.d/filters` in.

Verwijder alle bestanden met het voorvoegsel `ams_`.

Als `conf.dispatcher.d/filters` nu één bestand bevat, moet de naam worden gewijzigd in
`filters.any` en vergeet niet om de `$include`-instructies die daarop betrekking hebben, aan te passen
ook in de landbouwbedrijfdossiers.

Als de map echter meerdere, boerderspecifieke bestanden met dat patroon bevat, de inhoud ervan
moet naar de `$include` verklaring worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

Het bestand `conf.dispatcher/filters/default_filters.any` kopiëren uit de standaardmap
AEM als configuratie van de Cloud Service verzender aan die plaats.

In elk farmbestand vervangt u elke include-instructie voor filters die er als volgt uitziet:

```
$include "/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"
```

met de instructie:

```
$include "../filters/default_filters.any"
```

### Renderingen controleren

Voer de map `conf.dispatcher.d/renders` in.

Verwijder alle bestanden in die map.

Het bestand `conf.dispatcher.d/renders/default_renders.any` kopiëren uit de standaardmap
AEM als configuratie van de Cloud Service verzender aan die plaats.

In elk landbouwbedrijfdossier, verwijder om het even welke inhoud in `renders` sectie en vervang het
met:

```
$include "../renders/default_renders.any"
```

### Virtuele hosts controleren

Wijzig de naam van de map `conf.dispatcher.d/vhosts` in `conf.dispatcher.d/virtualhosts` en voer deze in.

Verwijder alle bestanden met het voorvoegsel `ams_`.

Als `conf.dispatcher.d/virtualhosts` nu één bestand bevat, moet de naam worden gewijzigd in
`virtualhosts.any` en vergeet niet om de `$include`-instructies die daarop betrekking hebben, aan te passen
ook in de landbouwbedrijfdossiers.

Als de map echter meerdere, boerderspecifieke bestanden met dat patroon bevat, de inhoud ervan
moet naar de `$include` verklaring worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

Het bestand `conf.dispatcher/virtualhosts/default_virtualhosts.any` kopiëren uit de standaardmap
AEM als configuratie van de Cloud Service verzender aan die plaats.

In elk farmbestand vervangt u elke include-instructie voor filters die er als volgt uitziet:

```
$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"
```

met de instructie:

```
$include "../virtualhosts/default_virtualhosts.any"
```

### Uw status controleren door de validatietool uit te voeren

Voer de AEM als Cloud Service dispatcher validator in uw folder, met `dispatcher` subcommand in werking:

```
$ validator dispatcher .
```

Als er fouten optreden over ontbrekende Include-bestanden, controleert u of de naam van die bestanden correct is gewijzigd.

Als er fouten optreden met betrekking tot een niet-gedefinieerde variabele `PUBLISH_DOCROOT`, wijzigt u de naam hiervan naar `DOCROOT`.

Bij andere fouten bekijkt u de sectie Problemen oplossen in de documentatie over de validatietool.

### Test uw configuratie met een lokale plaatsing (vereist de installatie van Docker)

Gebruikend het manuscript `docker_run.sh` in de AEM als Hulpmiddelen van de Verzender van de Cloud Service, kunt u dat testen
uw configuratie bevat geen andere fout die alleen wordt weergegeven in
implementatie:

### Stap 1: Implementatiegegevens genereren met de validator

```
validator full -d out .
```

Dit bevestigt de volledige configuratie en produceert plaatsingsinformatie in `out`

### Stap 2: Start de dispatcher in een docker-image met die implementatiegegevens

Als uw AEM-publicatieserver op uw MacOS-computer wordt uitgevoerd en u luistert naar poort 4503, kunt u de Dispatcher als volgt voor die server starten:

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

Hierdoor wordt de container gestart en is Apache beschikbaar op de lokale poort 8080.

### De nieuwe configuratie van de verzender gebruiken

Gefeliciteerd! Als de validator geen problemen meer rapporteert en als de
dockercontainer wordt gestart zonder fouten of waarschuwingen, u bent
klaar om uw configuratie aan `dispatcher/src` subdirectory te bewegen
van uw it-opslagplaats.

**Klanten die AMS Dispatcher Configuration versie 1 gebruiken, dienen contact op te nemen met de klantenondersteuning om hen te helpen bij de migratie van versie 1 naar versie 2, zodat bovenstaande instructies kunnen worden opgevolgd.**
