---
title: Dispatcher in de cloud
description: 'Dispatcher in de cloud '
translation-type: tm+mt
source-git-commit: 6951b6ff255513f5865e1f92a09c5ac439271a26
workflow-type: tm+mt
source-wordcount: '3914'
ht-degree: 9%

---


# Dispatcher in de cloud {#Dispatcher-in-the-cloud}

## Apache and Dispatcher configuration and testing {#apache-and-dispatcher-configuration-and-testing}

In deze sectie wordt beschreven hoe u de AEM kunt structureren als Apache- en Dispatcher-configuraties voor Cloud Servicen en hoe u de AEM lokaal kunt valideren en uitvoeren voordat u de AEM implementeert in een cloud-omgeving. Hierin wordt ook foutopsporing in Cloud-omgevingen beschreven. Raadpleeg de documentatie bij [AEM Dispatcher voor meer informatie over Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/dispatcher.html).

>[!NOTE]
>Windows-gebruikers moeten Windows 10 Professional of andere distributies gebruiken die Docker ondersteunen. Dit is een vereiste voor het uitvoeren van en het opsporen van fouten in Dispatcher op een lokale computer. De onderstaande secties bevatten opdrachten met behulp van de Mac- of Linux-versies van de SDK, maar de Windows SDK kan op dezelfde manier worden gebruikt.

>[!WARNING]
> Windows-gebruikers: de huidige versie van AEM als Cloud Service lokale Dispatcher Tools (v2.0.20) is niet compatibel met Windows. Neem contact op met de ondersteuning [van](https://daycare.day.com/home.html) Adobe voor updates over Windows-compatibiliteit.

## Dispatcher Tools {#dispatcher-sdk}

De Dispatcher Tools maakt deel uit van de algemene AEM als Cloud Service SDK en biedt:

* Een vanilla-bestandsstructuur met de configuratiebestanden die moeten worden opgenomen in een bepaald project voor dispatcher.
* Klanten kunnen kiezen voor lokale validatie van een verzendersconfiguratie.
* Een Docker-afbeelding waarmee de verzender lokaal wordt opgehaald.

## De gereedschappen downloaden en extraheren {#extracting-the-sdk}

De Dispatcher Tools kan worden gedownload van een ZIP-bestand op de [Software Distribution](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html) Portal. De toegang tot de SDK-aanbiedingen is beperkt tot gebruikers met AEM Managed Services of AEM als een Cloud Service-omgeving. Elke nieuwe configuratie die beschikbaar is in die nieuwe versie van Dispatcher Tools kan worden gebruikt voor implementatie in cloudomgevingen met die versie van AEM in de cloud of hoger.

**Voor MacOS en Linux** downloadt u het shellscript naar een map op uw computer, maakt u het uitvoerbaar en voert u het uit. De bestanden met Dispatcher Tools worden zelf uitgepakt onder de map waarin u deze hebt opgeslagen (waar `version` is de versie van de verzendprogramma&#39;s).

```bash
$ chmod +x DispatcherSDKv<version>.sh
$ ./DispatcherSDKv<version>.sh
Verifying archive integrity...  100%   All good.
Uncompressing DispatcherSDKv<version>  100% 
```

**Download voor Windows** het zip-archief en extraheer het.

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

U kunt een of meer van deze bestanden hebben. Zij bevatten `<VirtualHost>` ingangen die gastheernamen aanpassen en Apache toestaan om elk domeinverkeer met verschillende regels te behandelen. Bestanden worden gemaakt in de `available_vhosts` map en ingeschakeld met een symbolische koppeling in de `enabled_vhosts` map. Van de `.vhost` bestanden worden andere bestanden opgenomen, zoals herschreven bestanden en variabelen.

* `conf.d/rewrites/rewrite.rules`

Dit bestand wordt vanuit uw `.vhost` bestanden opgenomen. Het heeft een reeks herschrijfregels voor `mod_rewrite`.

>[!NOTE]
>
>Op dit moment moet één herschrijfbestand worden gebruikt in plaats van sitespecifieke bestanden. De bestandsgrootte moet kleiner zijn dan 1 MB.

* `conf.d/variables/custom.vars`

Dit bestand wordt vanuit uw `.vhost` bestanden opgenomen. U kunt op deze locatie definities voor Apache-variabelen plaatsen.

* `conf.d/variables/global.vars`

Dit bestand wordt vanuit het `dispatcher_vhost.conf` bestand opgenomen. U kunt de verzender wijzigen en het logniveau in dit bestand herschrijven.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

U kunt één of meerdere van deze dossiers hebben, en zij bevatten landbouwbedrijven om gastheernamen aan te passen en de dispatchermodule toe te staan om elk landbouwbedrijf met verschillende regels te behandelen. Bestanden worden gemaakt in de `available_farms` map en ingeschakeld met een symbolische koppeling in de `enabled_farms` map. Van de `.farm` dossiers, zullen andere dossiers zoals filters, geheim voorgeheugenregels en anderen worden omvat.

* `conf.dispatcher.d/cache/rules.any`

Dit bestand wordt vanuit uw `.farm` bestanden opgenomen. Hiermee geeft u voorkeuren voor caching op.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

Dit bestand wordt vanuit uw `.farm` bestanden opgenomen. Het specificeert welke verzoekkopballen aan het achtereind door:sturen.

* `conf.dispatcher.d/filters/filters.any`

Dit bestand wordt vanuit uw `.farm` bestanden opgenomen. Het heeft een reeks regels die veranderen welk verkeer uit zou moeten worden gefiltreerd en niet het aan het achterste eind maken.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

Dit bestand wordt vanuit uw `.farm` bestanden opgenomen. Het heeft een lijst van gastheernamen of de wegen van URI die door glob aanpassing moeten worden aangepast. Dit bepaalt welke achtergrond om een verzoek te dienen.

De bovenstaande bestanden verwijzen naar de onderstaande onveranderlijke configuratiebestanden. Wijzigingen in de onveranderbare bestanden worden niet verwerkt door verzenders in Cloud-omgevingen.

**Immuable Configuration Files**

Deze bestanden maken deel uit van het basiskader en zorgen ervoor dat standaarden en beste praktijken worden nageleefd. De bestanden worden als onveranderlijk beschouwd, omdat het wijzigen of verwijderen ervan lokaal geen invloed heeft op uw implementatie, omdat deze bestanden niet worden overgedragen naar uw Cloud-instantie.

Het wordt aanbevolen dat de bovenstaande bestanden verwijzen naar de hieronder vermelde onveranderlijke bestanden, gevolgd door aanvullende instructies of overschrijvingen. Wanneer de configuratie van de verzender aan een wolkenmilieu wordt opgesteld, zal de recentste versie van de onveranderlijke dossiers worden gebruikt, ongeacht welke versie in lokale ontwikkeling werd gebruikt.

* `conf.d/available_vhosts/default.vhost`

Bevat een virtuele voorbeeldhost. Voor uw eigen virtuele host maakt u een kopie van dit bestand, past u het aan, gaat u naar `conf.d/enabled_vhosts` en maakt u een symbolische koppeling naar uw aangepaste kopie.

* `conf.d/dispatcher_vhost.conf`

Deel van het basisframework dat wordt gebruikt om te illustreren hoe uw virtuele hosts en globale variabelen worden opgenomen.

* `conf.d/rewrites/default_rewrite.rules`

Standaard herschrijft regels geschikt voor een standaardproject. Wijzig de instellingen als u deze wilt aanpassen `rewrite.rules`. In uw aanpassing, kunt u nog de standaardregels eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/available_farms/default.farm`

Bevat een bedrijf van de steekproefdispatcher. Voor uw eigen landbouwbedrijf, creeer een exemplaar van dit dossier, pas het aan, ga aan `conf.d/enabled_farms` en creeer een symbolische verbinding aan uw aangepaste exemplaar.

* `conf.dispatcher.d/cache/default_invalidate.any`

Een deel van het basiskader, wordt geproduceerd bij opstarten. U wordt **vereist** om dit dossier in elk landbouwbedrijf te omvatten u, in de `cache/allowedClients` sectie bepaalt.

* `conf.dispatcher.d/cache/default_rules.any`

De standaard geheim voorgeheugenregels geschikt voor een standaardproject. Wijzig de instellingen als u deze wilt aanpassen `conf.dispatcher.d/cache/rules.any`. In uw aanpassing, kunt u nog de standaardregels eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/clientheaders/default_clientheaders.any`

De standaard verzoekkopballen om aan het achterste deel door:sturen, geschikt voor een standaardproject. Wijzig de instellingen als u deze wilt aanpassen `clientheaders.any`. In uw aanpassing, kunt u nog de standaardverzoekkopballen eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/dispatcher.any`

Deel van basisframework dat wordt gebruikt om te illustreren hoe de kwekerijen van de dispatcher worden opgenomen.

* `conf.dispatcher.d/filters/default_filters.any`

Standaardfilters die geschikt zijn voor een standaardproject. Wijzig de instellingen als u deze wilt aanpassen `filters.any`. In uw aanpassing, kunt u nog de standaardfilters eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/renders/default_renders.any`

Als onderdeel van het basisframework wordt dit bestand bij het opstarten gegenereerd. U wordt **vereist** om dit dossier in elk landbouwbedrijf te omvatten u, in de `renders` sectie bepaalt.

* `conf.dispatcher.d/virtualhosts/default_virtualhosts.any`

Standaardhostglobing geschikt voor een standaardproject. Wijzig de instellingen als u deze wilt aanpassen `virtualhosts.any`. In uw aanpassing, zou u niet het standaard gastheer het globbings moeten omvatten, aangezien het **elk** inkomend verzoek aanpast.

>[!NOTE]
>AEM als Cloud Service wordt gemaakt archetype zal de zelfde structuur van het de configuratiedossier van de verzender produceren.

In de onderstaande secties wordt beschreven hoe u de configuratie lokaal kunt valideren zodat deze de bijbehorende kwaliteitspoort in Cloud Manager kan doorgeven bij het implementeren van een interne release.

## Lokale validatie van Dispatcher-configuratie {#local-validation-of-dispatcher-configuration}

Het validatieprogramma is beschikbaar in de SDK `bin/validator` als binair bestand voor Mac OS, Linux of Windows, zodat klanten dezelfde validatie kunnen uitvoeren als Cloud Manager bij het maken en implementeren van een release.

Deze wordt aangeroepen als: `validator full [-d folder] [-w whitelist] zip-file | src folder`

Het gereedschap valideert de configuratie van Apache en dispatcher. Alle bestanden worden gescand met een patroon `conf.d/enabled_vhosts/*.vhost` en er wordt gecontroleerd of alleen toegestane instructies worden gebruikt. De instructies die zijn toegestaan in Apache-configuratiebestanden, kunnen worden weergegeven door de allowlist-opdracht van de validator uit te voeren:

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
| `mod_auth_basic` | [https://httpd.apache.org/docs/2.4/mod/mod_auth_basic.html](https://httpd.apache.org/docs/2.4/mod/mod_auth_basic.html) |
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

Klanten kunnen geen arbitraire modules toevoegen, maar in de toekomst kunnen wel extra modules in het product worden opgenomen. Klanten kunnen de lijst met instructies voor een bepaalde Dispatcher-versie vinden door de allowlist-opdracht van de validator uit te voeren in de SDK, zoals hierboven beschreven.

De allowlist bevat een lijst met Apache-instructies die zijn toegestaan in een klantconfiguratie. Als een instructie niet is toegestaan, wordt een fout geregistreerd en wordt een afsluitcode van niet nul geretourneerd. Als er geen allowlist is opgegeven op de opdrachtregel (zoals deze moet worden aangeroepen), gebruikt het hulpprogramma een standaard allowlist die Cloud Manager zal gebruiken voor validatie voordat het programma wordt geïmplementeerd naar Cloud-omgevingen.

Bovendien worden alle bestanden gescand met een patroon `conf.dispatcher.d/enabled_farms/*.farm` en wordt gecontroleerd of:

* Er bestaat geen filterregel die via `/glob` toestaat (zie [CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957) voor meer informatie)
* Er wordt geen beheerfunctie weergegeven. Bijvoorbeeld toegang tot paden, zoals `/crx/de or /system/console`paden.

Wanneer de looppas tegen uw beven artefact of uw `dispatcher/src` subdirectory, zal het bevestigingsmislukkingen melden:

```
$ validator full dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-whitelisted directives:
 conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
 conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

Let op: het validatiehulpmiddel rapporteert alleen het verboden gebruik van Apache-instructies die niet zijn toegestaan. Er worden geen syntactische of semantische problemen met uw Apache-configuratie gemeld, aangezien deze informatie alleen beschikbaar is voor Apache-modules in een actieve omgeving.

Wanneer geen bevestigingsmislukkingen worden gemeld, is uw configuratie klaar voor plaatsing.

Hieronder vindt u technieken voor het oplossen van problemen waarmee algemene validatiefouten kunnen worden opgespoord die door het programma worden uitgevoerd:

**kan geen`conf.dispatcher.d`submap vinden in het archief**

Uw archief moet mappen `conf.d` en `conf.dispatcher.d` bevatten. Let op: gebruik het voorvoegsel `etc/httpd` **niet** in uw archief.

**geen bedrijf kunnen vinden in`conf.dispatcher.d/enabled_farms`**

Uw ingeschakelde landbouwbedrijven zouden in bovengenoemde subfolder moeten worden gevestigd.

**Ingesloten bestand (...) moet een naam hebben: ...**

Er zijn twee secties in uw landbouwbedrijfconfiguratie die een specifiek dossier **moeten** omvatten: `/renders` en `/allowedClients` in het `/cache` gedeelte. Deze selecties moeten er als volgt uitzien:

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

Er zijn vier secties in uw landbouwbedrijfconfiguratie waar u uw eigen dossier mag omvatten: `/clientheaders`, `filters`, `/rules` in `/cache` afdeling en `/virtualhosts`. De opgenomen bestanden moeten als volgt worden benoemd:

| Sectie | Bestandsnaam opnemen |
|------------------|--------------------------------------|
| `/clientheaders` | `../clientheaders/clientheaders.any` |
| `/filters` | `../filters/filters.any` |
| `/rules` | `../cache/rules.any` |
| `/virtualhosts` | `../virtualhosts/virtualhosts.any` |

U kunt ook de **standaardversie** van deze bestanden opnemen, waarvan de namen worden voorafgegaan door het woord `default_`, bijvoorbeeld `../filters/default_filters.any`.

**include statement at (...), outside any known location: ...**

Naast de zes in de bovenstaande alinea&#39;s vermelde secties kunt u de `$include` instructie niet gebruiken. Deze fout kan bijvoorbeeld worden gegenereerd door:

```
/invalidate {
    $include "../cache/invalidate.any"
}
```

**toegestane clients/renderingen zijn niet inbegrepen bij: ...**

Deze fout wordt geproduceerd wanneer u geen omvat voor `/renders` en `/allowedClients` in de `/cache` sectie specificeert. Zie het **ingesloten bestand (...) met de volgende naam: ...** voor meer informatie.

**filter mag geen globpatroon gebruiken om verzoeken toe te staan**

Het is niet veilig om verzoeken met een `/glob` stijlregel toe te staan, die tegen de volledige verzoeklijn, b.v. wordt aangepast

```
/0100 {
    /type "allow" /glob "GET *.css *"
}
```

Deze verklaring moet verzoeken om `css` dossiers toestaan, maar het staat ook verzoeken aan **om het even welke** middel toe die door het vraagkoord wordt gevolgd `?a=.css`. Het is daarom verboden dergelijke filters te gebruiken (zie ook CVE-2016-0957).

**opgenomen bestand (...) komt niet overeen met een bekend bestand**

Er zijn twee typen bestanden in uw virtuele Apache-hostconfiguratie die als volgt kunnen worden opgegeven: herschrijft en variabelen.
De opgenomen bestanden moeten als volgt worden benoemd:

| Type | Bestandsnaam opnemen |
|-----------|---------------------------------|
| Herschrijven | `conf.d/rewrites/rewrite.rules` |
| Variabelen | `conf.d/variables/custom.vars` |

U kunt ook de **standaardversie** van de herschrijfregels opnemen, waarvan de naam `conf.d/rewrites/default_rewrite.rules`.
Er is geen standaardversie van de variabelebestanden.

**Verouderde configuratielay-out gedetecteerd, compatibiliteitsmodus ingeschakeld**

Dit bericht geeft aan dat uw configuratie de verouderde versie 1-indeling heeft, die een completeApache-configuratie bevat en bestanden met `ams_` voorvoegsels. Hoewel dit nog steeds wordt ondersteund voor achterwaartse compatibiliteit, moet u overschakelen op de nieuwe layout.

## Uw Apache- en Dispatcher-configuratie lokaal testen {#testing-apache-and-dispatcher-configuration-locally}

Het is ook mogelijk om uw Apache- en Dispatcher-configuratie lokaal te testen. Hiervoor moet Docker lokaal zijn geïnstalleerd en moet uw configuratie voldoen aan de bovenstaande validatie.

Door de parameter &quot;`-d`&quot; te gebruiken, voert de validator een map uit met alle configuratiebestanden die de verzender nodig heeft.

Vervolgens kan het `docker_run.sh` script naar die map verwijzen, waarbij de container met uw configuratie wordt gestart.

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

Hierdoor wordt de verzender in een container gestart, waarbij de achtergrond naar een AEM-instantie verwijst die op uw lokale Mac OS-computer op poort 4503 wordt uitgevoerd.

## Fouten opsporen in uw Apache- en Dispatcher-configuratie {#debugging-apache-and-dispatcher-configuration}

De volgende strategie kan worden gebruikt om de logboekoutput voor de verzender module te verhogen en het resultaat van de `RewriteRule` evaluatie in zowel lokale als wolkenmilieu&#39;s te zien.

De logboekniveaus voor deze modules worden bepaald door de variabelen `DISP_LOG_LEVEL` en `REWRITE_LOG_LEVEL`. Deze kunnen in het bestand worden ingesteld `conf.d/variables/global.vars`. Het relevante deel is als volgt:

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

Wanneer u de Dispatcher lokaal uitvoert, worden de logbestanden ook rechtstreeks afgedrukt op de einduitvoer. Meestal, zouden deze logboeken in DEBUG moeten zijn, die kan worden verwezenlijkt door in Debug niveau als parameter over te gaan wanneer het runnen van Docker. Bijvoorbeeld:

`DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`

Logbestanden voor cloudomgevingen worden weergegeven via de logservice die beschikbaar is in Cloud Manager.

## Verschillende Dispatcher-configuraties per omgeving {#different-dispatcher-configurations-per-environment}

Op dit moment wordt dezelfde configuratie van de verzender toegepast op alle AEM als een Cloud Service-omgeving. De runtime heeft een omgevingsvariabele `ENVIRONMENT_TYPE` die de huidige uitvoermodus (dev, stage of prod) en een definitie bevat. De definitie kan zijn `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE` of `ENVIRONMENT_PROD`. In de Apache-configuratie kan de variabele rechtstreeks in een expressie worden gebruikt. U kunt ook de definitie gebruiken om logica op te bouwen:

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

In de Dispatcher-configuratie is dezelfde omgevingsvariabele beschikbaar. Als meer logica wordt vereist, bepaal de variabelen zoals aangetoond in het bovenstaande voorbeeld en gebruik dan hen in de de configuratiesectie van Dispatcher:

```
/virtualhosts {
  { "${VIRTUALHOST}" }
}
```

Wanneer het testen van uw configuratie plaatselijk, kunt u verschillende milieutypes simuleren door de variabele `DISP_RUN_MODE` aan het `docker_run.sh` manuscript direct over te gaan:

```
$ DISP_RUN_MODE=stage docker_run.sh out docker.for.mac.localhost:4503 8080
```

De standaardrunmode wanneer het overgaan niet in een waarde voor DISP_RUN_MODE is &quot;dev&quot;.
Voor een volledige lijst van beschikbare opties en variabelen, stel het manuscript `docker_run.sh` zonder argumenten in werking.

## De Dispatcher-configuratie bekijken die door uw Docker-container wordt gebruikt {#viewing-dispatcher-configuration-in-use-by-docker-container}

Met milieu-specifieke configuraties, kan het moeilijk zijn om te bepalen hoe de daadwerkelijke configuratie van Dispatcher eruit ziet. Nadat u de docker container met `docker_run.sh` deze heeft gestart, kan deze als volgt worden gedumpt:

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

Zoals hierboven op de referentiepagina is beschreven, lijken de Apache- en Dispatcher-configuratie in AEM als Cloud Service sterk op die in AMS. De belangrijkste verschillen zijn:

* In AEM als Cloud Service kunnen sommige Apache-richtlijnen niet worden gebruikt (bijvoorbeeld `Listen` of `LogLevel`)
* In AEM als Cloud Service, kunnen slechts sommige stukken van de configuratie van Dispatcher in omvat dossiers worden gezet en hun het noemen is belangrijk. Zo moeten filterregels die u op verschillende hosts opnieuw wilt gebruiken, in een bestand met de naam `filters/filters.any`worden geplaatst. Zie de referentiepagina voor meer informatie.
* In AEM als Cloud Service is er extra validatie om filterregels te weigeren die worden geschreven met behulp `/glob` om beveiligingsproblemen te voorkomen. Aangezien `deny *` wordt gebruikt in plaats `allow *` (en niet kan worden gebruikt), zullen klanten er baat bij hebben om de Dispatcher lokaal uit te voeren en fouten te maken. In de logboeken wordt precies nagegaan welke paden door de Dispatcher-filters worden geblokkeerd, zodat deze kunnen worden toegevoegd.

## Richtlijnen voor het migreren van de configuratie van de verzender van AMS naar AEM als Cloud Service

De de configuratiestructuur van de verzender heeft verschillen tussen Beheerde Diensten en AEM als Cloud Service. Hieronder wordt een stapsgewijze handleiding gepresenteerd voor het migreren van AMS Dispatcher-configuratieversie 2 naar AEM als Cloud Service.

## Een AMS converteren naar een AEM als configuratie voor een serviceverzender in de cloud

In de volgende sectie vindt u stapsgewijze instructies voor het omzetten van een AMS-configuratie. It assumes
that you have an archive with a structure similar to the one described in [Cloud Manager dispatcher configuration](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html)

### Het archief extraheren en een eventueel voorvoegsel verwijderen

Extraheer het archief naar een map en zorg ervoor dat de directe submappen beginnen met `conf`, `conf.d`en`conf.dispatcher.d` `conf.modules.d`. Als ze dat niet doen, verplaats ze omhoog in de hiërarchie.

### Ongebruikte submappen en bestanden verwijderen

Remove subfolders `conf` and `conf.modules.d`, as well as files matching `conf.d/*.conf`.

### Alle niet-gepubliceerde virtuele hosts verwijderen

Verwijder een virtueel hostbestand in `conf.d/enabled_vhosts` dat `author`, `unhealthy`, `health``lc` of `flush` in de naam ervan heeft. All virtual host files in `conf.d/available_vhosts` that are not
linked to can be removed as well.

### Verwijder of becommentarieer virtuele hostsecties die niet verwijzen naar poort 80

Als u nog secties in uw virtuele hostbestanden hebt die uitsluitend verwijzen naar andere poorten dan poort 80, b.v.

```
<VirtualHost *:443>
...
</VirtualHost>
```

verwijder deze dan of plaats een opmerking. Instructies in deze secties worden niet verwerkt, maar als u ze niet verwijdert, kan het gebeuren dat u ze alsnog bewerkt, zonder effect. En dat kan verwarrend zijn.

### Herschrijvingen controleren

Map invoeren `conf.d/rewrites`.

Remove any file named `base_rewrite.rules` and `xforwarded_forcessl_rewrite.rules` and remember to
remove `Include` statements in the virtual host files referring to them.

If `conf.d/rewrites` now contains a single file, it should be renamed to `rewrite.rules` and don&#39;t
forget to adapt the `Include` statements referring to that file in the virtual host files as well.

If the folder however contains multiple, virtual host specific files, their contents should be
copied to the `Include` statement referring to them in the virtual host files.

### Variabelen controleren

Map invoeren `conf.d/variables`.

Remove any file named `ams_default.vars` and remember to remove `Include` statements in the virtual
host files referring to them.

If `conf.d/variables` now contains a single file, it should be renamed to `custom.vars` and don&#39;t
forget to adapt the `Include` statements referring to that file in the virtual host files as well.

If the folder however contains multiple, virtual host specific files, their contents should be
copied to the `Include` statement referring to them in the virtual host files.

### Toegestane lijsten verwijderen

Remove the folder `conf.d/whitelists` and remove `Include` statements in the virtual host files referring to
some file in that subfolder.

### Variabelen vervangen die niet meer beschikbaar zijn

In alle virtuele hostbestanden:

Naam wijzigen `PUBLISH_DOCROOT` om secties te `DOCROOT`verwijderen die verwijzen naar benoemde variabelen `DISP_ID`, `PUBLISH_FORCE_SSL` of `PUBLISH_WHITELIST_ENABLED`

### Uw status controleren door de validatietool uit te voeren

Run the dispatcher validator in your directory, with the `httpd` subcommand:

```
$ validator httpd .
```

Als er fouten optreden over ontbrekende Include-bestanden, controleert u of de naam van die bestanden correct is gewijzigd.

Als u Apache-instructies ziet die niet zijn toegestaan, verwijdert u deze.

### Alle niet-publicatiefarms verwijderen

Remove any farm file in `conf.dispatcher.d/enabled_farms` that has `author`, `unhealthy`, `health`,
`lc` or `flush` in its name. All farm files in `conf.dispatcher.d/available_farms` that are not
linked to can be removed as well.

### De naam van farmbestanden wijzigen

All farms in `conf.d/enabled_farms` must be renamed to match the pattern `*.farm`, so e.g. a
farm file called `customerX_farm.any` should be renamed `customerX.farm`.

### Cache controleren

Map invoeren `conf.dispatcher.d/cache`.

Verwijder alle bestanden met het voorvoegsel `ams_`.

If `conf.dispatcher.d/cache` is now empty, copy the file `conf.dispatcher.d/cache/rules.any`
from the standard dispatcher configuration to this folder. The standard dispatcher
configuration can be found in the folder `src` of this SDK. Don&#39;t forget to adapt the
`$include` statements referring to the `ams_*_cache.any` rule files  in the farm files
as well.

If instead `conf.dispatcher.d/cache` now contains a single file with suffix `_cache.any`,
it should be renamed to `rules.any` and don&#39;t forget to adapt the `$include` statements
referring to that file in the farm files as well.

If the folder however contains multiple, farm specific files with that pattern, their contents
should be copied to the `$include` statement referring to them in the farm files.

Remove any file that has the suffix `_invalidate_allowed.any`.

Kopieer het bestand `conf.dispatcher.d/cache/default_invalidate_any` van de standaardAEM in de configuratie van de Cloud-dispatcher naar die locatie.

In each farm file, remove any contents in the `cache/allowedClients` section and replace it
with:

```
$include "../cache/default_invalidate.any"
```

### Clientheaders controleren

Map invoeren `conf.dispatcher.d/clientheaders`.

Verwijder alle bestanden met het voorvoegsel `ams_`.

If `conf.dispatcher.d/clientheaders` now contains a single file with suffix `_clientheaders.any`,
it should be renamed to `clientheaders.any` and don&#39;t forget to adapt the `$include` statements
referring to that file in the farm files as well.

If the folder however contains multiple, farm specific files with that pattern, their contents
should be copied to the `$include` statement referring to them in the farm files.

Kopieer het bestand `conf.dispatcher/clientheaders/default_clientheaders.any` van defaultAEM als een Cloud Service dispatcher configuratie naar die locatie.

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

Map invoeren `conf.dispatcher.d/filters`.

Verwijder alle bestanden met het voorvoegsel `ams_`.

If `conf.dispatcher.d/filters` now contains a single file it should be renamed to
`filters.any` and don&#39;t forget to adapt the `$include` statements referring to that
file in the farm files as well.

If the folder however contains multiple, farm specific files with that pattern, their contents
should be copied to the `$include` statement referring to them in the farm files.

Kopieer het bestand `conf.dispatcher/filters/default_filters.any` van defaultAEM als een Cloud Service dispatcher configuratie naar die locatie.

In elk farmbestand vervangt u elke include-instructie voor filters die er als volgt uitziet:

```
$include "/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"
```

met de instructie:

```
$include "../filters/default_filters.any"
```

### Renderingen controleren

Map invoeren `conf.dispatcher.d/renders`.

Verwijder alle bestanden in die map.

Kopieer het bestand `conf.dispatcher.d/renders/default_renders.any` van defaultAEM als een Cloud Service dispatcher configuratie naar die locatie.

In each farm file, remove any contents in the `renders` section and replace it
with:

```
$include "../renders/default_renders.any"
```

### Virtuele hosts controleren

Rename the directory `conf.dispatcher.d/vhosts` to `conf.dispatcher.d/virtualhosts` and enter it.

Verwijder alle bestanden met het voorvoegsel `ams_`.

If `conf.dispatcher.d/virtualhosts` now contains a single file it should be renamed to
`virtualhosts.any` and don&#39;t forget to adapt the `$include` statements referring to that
file in the farm files as well.

If the folder however contains multiple, farm specific files with that pattern, their contents
should be copied to the `$include` statement referring to them in the farm files.

Kopieer het bestand `conf.dispatcher/virtualhosts/default_virtualhosts.any` van defaultAEM als een Cloud Service dispatcher configuratie naar die locatie.

In elk farmbestand vervangt u elke include-instructie voor filters die er als volgt uitziet:

```
$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"
```

met de instructie:

```
$include "../virtualhosts/default_virtualhosts.any"
```

### Uw status controleren door de validatietool uit te voeren

Voer de AEM als Cloud Service dispatcher validator in uw folder, met `dispatcher` subcommand uit:

```
$ validator dispatcher .
```

Als er fouten optreden over ontbrekende Include-bestanden, controleert u of de naam van die bestanden correct is gewijzigd.

Als er fouten optreden met betrekking tot een niet-gedefinieerde variabele `PUBLISH_DOCROOT`, wijzigt u de naam hiervan naar `DOCROOT`.

Bij andere fouten bekijkt u de sectie Problemen oplossen in de documentatie over de validatietool.

### Test uw configuratie met een lokale plaatsing (vereist de installatie van Docker)

Using the script `docker_run.sh` in the AEM as a Cloud Service Dispatcher Tools, you can test that
your configuration does not contain any other error that would only show up in
deployment:

### Stap 1: Implementatiegegevens genereren met de validator

```
validator full -d out .
```

This validates the full configuration and generates deployment information in `out`

### Stap 2: Start de dispatcher in een docker-image met die implementatiegegevens

Als uw AEM-publicatieserver op uw MacOS-computer wordt uitgevoerd en u luistert naar poort 4503, kunt u de Dispatcher als volgt voor die server starten:

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

Hierdoor wordt de container gestart en is Apache beschikbaar op de lokale poort 8080.

### De nieuwe configuratie van de verzender gebruiken

Gefeliciteerd! If the validator no longer reports any issue and the
docker container starts up without any failures or warnings, you&#39;re
ready to move your configuration to a `dispatcher/src` subdirectory
of your git repository.

**Klanten die AMS Dispatcher Configuration versie 1 gebruiken, dienen contact op te nemen met de klantenondersteuning om hen te helpen bij de migratie van versie 1 naar versie 2, zodat bovenstaande instructies kunnen worden opgevolgd.**
