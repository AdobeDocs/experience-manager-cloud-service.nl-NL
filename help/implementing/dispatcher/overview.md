---
title: Dispatcher in de cloud
description: 'Dispatcher in de cloud '
translation-type: tm+mt
source-git-commit: b7bb84b026c9187cb633e9ccfdc17aa5ec930aff
workflow-type: tm+mt
source-wordcount: '3916'
ht-degree: 1%

---


# Dispatcher in de cloud {#Dispatcher-in-the-cloud}

## Configuratie en testen van Apache en Dispatcher {#apache-and-dispatcher-configuration-and-testing}

In deze sectie wordt beschreven hoe u de AEM kunt structureren als een Apache- en Dispatcher-configuratie voor cloudservice en hoe u de AEM lokaal kunt valideren en uitvoeren voordat u deze implementeert in een cloud-omgeving. Hierin wordt ook foutopsporing in Cloud-omgevingen beschreven. Raadpleeg de documentatie bij [AEM Dispatcher voor meer informatie over Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/dispatcher.html).

>[!NOTE]
>Windows-gebruikers moeten Windows 10 Professional of andere distributies gebruiken die Docker ondersteunen. Dit is een vereiste voor het uitvoeren van en het zuiveren van Dispatcher op een lokale computer. De onderstaande secties bevatten opdrachten met behulp van de Mac- of Linux-versies van de SDK, maar de Windows SDK kan op dezelfde manier worden gebruikt.

>[!WARNING]
> Windows-gebruikers: De huidige versie van AEM als lokale Dispatcher Tools voor cloudservice (v2.0.20) is niet compatibel met Windows. Neem contact op met de ondersteuning [van](https://daycare.day.com/home.html) Adobe voor updates over Windows-compatibiliteit.

## Verzendgereedschappen {#dispatcher-sdk}

De Dispatcher Tools maken deel uit van de algemene AEM als Cloud Service SDK en bieden:

* Een vanilla-bestandsstructuur met de configuratiebestanden die moeten worden opgenomen in een bepaald project voor dispatcher.
* Klanten kunnen kiezen voor lokale validatie van een verzendersconfiguratie.
* Een Docker-afbeelding waarmee de verzender lokaal wordt opgehaald.

## De gereedschappen downloaden en extraheren {#extracting-the-sdk}

De Dispatcher Tools kan worden gedownload van een ZIP-bestand op de [Software Distribution](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html) Portal. De toegang tot de SDK-aanbiedingen is beperkt tot gebruikers met AEM Managed Services of AEM als een Cloud Service-omgeving. Elke nieuwe configuratie die beschikbaar is in die nieuwe versie van Dispatcher Tools kan worden gebruikt voor implementatie in cloudomgevingen met die versie van AEM in de cloud of hoger.

**Voor MacOS en Linux** downloadt u het shellscript naar een map op uw computer, maakt u het uitvoerbaar en voert u het uit. De Dispatcher Tools-bestanden worden zelf uitgepakt onder de map waarin u de toepassing hebt opgeslagen (waar `version` is de versie van de Dispatcher Tools).

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
>De AEM als een door de Cloud Service toegewezen archetype zal de zelfde structuur van het de configuratiedossier van de verzender produceren.

In de onderstaande secties wordt beschreven hoe u de configuratie lokaal kunt valideren zodat deze de bijbehorende kwaliteitspoort in Cloud Manager kan doorgeven bij het implementeren van een interne release.

## Lokale validatie van configuratie Dispatcher {#local-validation-of-dispatcher-configuration}

Het validatieprogramma is beschikbaar in de SDK `bin/validator` als binair bestand voor Mac OS, Linux of Windows, zodat klanten dezelfde validatie kunnen uitvoeren als Cloud Manager bij het maken en implementeren van een release.

Deze wordt aangeroepen als: `validator full [-d folder] [-w whitelist] zip-file | src folder`

Het gereedschap valideert de configuratie van Apache en dispatcher. Alle bestanden worden gescand met een patroon `conf.d/enabled_vhosts/*.vhost` en er wordt gecontroleerd of alleen de richtlijnen met een whitelist worden gebruikt. De instructies die zijn toegestaan in Apache-configuratiebestanden, kunnen worden weergegeven door de whitelist-opdracht van de validator uit te voeren:

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

Klanten kunnen geen arbitraire modules toevoegen, maar in de toekomst kunnen wel extra modules in het product worden opgenomen. Klanten kunnen de lijst met instructies vinden die beschikbaar is voor een bepaalde versie van Dispatcher door &#39;validator whitelist&#39; uit te voeren in de SDK, zoals beschreven in de documentatie van Dispatcher Tools.

De whitelist bevat een lijst met Apache-instructies die zijn toegestaan in een klantconfiguratie. Als een instructie niet wordt gewhitelisteerd, wordt een fout geregistreerd en wordt een afsluitcode van niet nul geretourneerd. Als er geen whitelist op de opdrachtregel staat (zoals deze moet worden aangeroepen), gebruikt het programma een standaardwhitelist die Cloud Manager voor validatie gebruikt voordat het programma wordt geïmplementeerd in Cloud-omgevingen.

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

Let op: het validatiehulpmiddel rapporteert alleen het verboden gebruik van Apache-instructies die niet zijn gewhitelliseerd. Er worden geen syntactische of semantische problemen met uw Apache-configuratie gemeld, aangezien deze informatie alleen beschikbaar is voor Apache-modules in een actieve omgeving.

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

## De configuratie van Apache en Dispatcher lokaal testen {#testing-apache-and-dispatcher-configuration-locally}

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

Wanneer de Dispatcher plaatselijk in werking stelt, worden de logboeken ook direct gedrukt aan de eindoutput. Meestal, zouden deze logboeken in DEBUG moeten zijn, die kan worden verwezenlijkt door in Debug niveau als parameter over te gaan wanneer het runnen van Docker. Bijvoorbeeld:

`DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`

Logbestanden voor cloudomgevingen worden weergegeven via de logservice die beschikbaar is in Cloud Manager.

## Verschillende Dispatcher-configuraties per omgeving {#different-dispatcher-configurations-per-environment}

Op dit moment wordt dezelfde configuratie van de verzender toegepast op alle AEM-omgevingen als een Cloud Service-omgeving. De runtime heeft een omgevingsvariabele `ENVIRONMENT_TYPE` die de huidige uitvoermodus (dev, stage of prod) en een definitie bevat. De definitie kan zijn `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE` of `ENVIRONMENT_PROD`. In de Apache-configuratie kan de variabele rechtstreeks in een expressie worden gebruikt. U kunt ook de definitie gebruiken om logica op te bouwen:

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

Wanneer het testen van uw configuratie plaatselijk, kunt u verschillende milieutypes simuleren door de variabele `DISP_RUN_MODE` aan het `docker_run.sh` manuscript direct over te gaan:

```
$ DISP_RUN_MODE=stage docker_run.sh out docker.for.mac.localhost:4503 8080
```

De standaardrunmode wanneer het overgaan niet in een waarde voor DISP_RUN_MODE is &quot;dev&quot;.
Voor een volledige lijst van beschikbare opties en variabelen, stel het manuscript `docker_run.sh` zonder argumenten in werking.

## De Dispatcher-configuratie bekijken die door de Docker-container wordt gebruikt {#viewing-dispatcher-configuration-in-use-by-docker-container}

Met milieu-specifieke configuraties, kan het moeilijk zijn om te bepalen hoe de daadwerkelijke configuratie van de Verzender kijkt als. Nadat u de docker container met `docker_run.sh` deze heeft gestart, kan deze als volgt worden gedumpt:

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

## Belangrijkste verschillen tussen AMS Dispatcher en AEM als cloudservice {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service}

Zoals hierboven op de referentiepagina is beschreven, lijkt de Apache- en Dispatcher-configuratie in AEM als cloudservice sterk op die van AMS. De belangrijkste verschillen zijn:

* In AEM als Cloud Service worden sommige Apache-instructies mogelijk niet gebruikt (bijvoorbeeld `Listen` of `LogLevel`)
* In AEM als Cloud Service kunnen alleen bepaalde onderdelen van de Dispatcher-configuratie in include-bestanden worden geplaatst en is de naamgeving ervan belangrijk. Zo moeten filterregels die u op verschillende hosts opnieuw wilt gebruiken, in een bestand met de naam `filters/filters.any`worden geplaatst. Zie de referentiepagina voor meer informatie.
* In AEM als Cloud Service is er extra validatie voor het uitschakelen van filterregels die zijn geschreven met behulp `/glob` om beveiligingsproblemen te voorkomen. Omdat `deny *` eerder dan `allow *` (dat niet kan worden gebruikt) zal worden gebruikt, zullen de klanten van het runnen van de Verzender plaatselijk profiteren en het doen van proef en fout, die de logboeken bekijken om precies te weten welke wegen de filters van de Verzender blokkeren opdat die kunnen worden toegevoegd.

## Richtlijnen voor het migreren van de configuratie van de verzender van AMS naar AEM als Cloud Service

De configuratiestructuur van de verzender heeft verschillen tussen Beheerde services en AEM als Cloud Service. Hieronder wordt een stapsgewijze handleiding gepresenteerd voor het migreren van AMS Dispatcher Configuration versie 2 naar AEM als Cloud Service.

## Een AMS converteren naar een AEM als configuratie voor een serviceverzender in de cloud

In de volgende sectie vindt u stapsgewijze instructies voor het omzetten van een AMS-configuratie. Hierbij wordt ervan uitgegaan dat u een archief hebt met een structuur die vergelijkbaar is met de structuur die wordt beschreven in de configuratie van [Cloud Manager-dispatcher](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html)

### Het archief extraheren en een eventueel voorvoegsel verwijderen

Extraheer het archief naar een map en zorg ervoor dat de directe submappen beginnen met `conf`, `conf.d`en`conf.dispatcher.d` `conf.modules.d`. Als ze dat niet doen, verplaats ze omhoog in de hiërarchie.

### Ongebruikte submappen en bestanden verwijderen

Submappen `conf` en `conf.modules.d`bestanden die overeenkomen verwijderen `conf.d/*.conf`.

### Alle niet-gepubliceerde virtuele hosts verwijderen

Verwijder een virtueel hostbestand in `conf.d/enabled_vhosts` dat `author`, `unhealthy`, `health``lc` of `flush` in de naam ervan heeft. Alle virtuele hostbestanden in `conf.d/available_vhosts` die niet zijn gekoppeld, kunnen ook worden verwijderd.

### Verwijder of becommentariër virtuele gastheersecties die niet naar haven 80 verwijzen

Als u nog secties in uw virtuele gastheerdossiers hebt die uitsluitend naar andere havens dan haven 80 verwijzen, b.v.

```
<VirtualHost *:443>
...
</VirtualHost>
```

verwijderen of opmerkingen maken. Instructies in deze secties worden niet verwerkt, maar als u ze rond houdt, kunt u ze waarschijnlijk nog steeds zonder effect bewerken. Dat is verwarrend.

### Herschrijvingen controleren

Map invoeren `conf.d/rewrites`.

Verwijder een bestand met de naam `base_rewrite.rules` en `xforwarded_forcessl_rewrite.rules` vergeet niet `Include` instructies in de virtuele hostbestanden die naar de bestanden verwijzen, te verwijderen.

Als er `conf.d/rewrites` nu één bestand is, moet u de naam ervan wijzigen en de `rewrite.rules` `Include` instructies met betrekking tot dat bestand ook in de virtuele hostbestanden aanpassen.

Als de map echter meerdere, virtuele hostspecifieke bestanden bevat, moet de inhoud ervan worden gekopieerd naar de `Include` instructie die ernaar verwijst in de virtuele hostbestanden.

### Variabelen controleren

Map invoeren `conf.d/variables`.

Verwijder een bestand met de naam `ams_default.vars` en vergeet niet `Include` instructies in de virtuele-hostbestanden te verwijderen die naar de bestanden verwijzen.

Als er `conf.d/variables` nu één bestand is, moet u de naam ervan wijzigen en de `custom.vars` `Include` instructies met betrekking tot dat bestand ook in de virtuele hostbestanden aanpassen.

Als de map echter meerdere, virtuele hostspecifieke bestanden bevat, moet de inhoud ervan worden gekopieerd naar de `Include` instructie die ernaar verwijst in de virtuele hostbestanden.

### Witlijsten verwijderen

Verwijder de map `conf.d/whitelists` en verwijder `Include` instructies in de virtuele hostbestanden die verwijzen naar een bestand in die submap.

### Variabelen vervangen die niet meer beschikbaar zijn

In alle virtuele hostbestanden:

Naam wijzigen `PUBLISH_DOCROOT` om secties te `DOCROOT`verwijderen die verwijzen naar benoemde variabelen `DISP_ID`, `PUBLISH_FORCE_SSL` of `PUBLISH_WHITELIST_ENABLED`

### Controleer uw status door validator uit te voeren

Voer de verzender-validator in uw map uit, met de `httpd` subopdracht:

```
$ validator httpd .
```

Als er fouten optreden bij ontbrekende include-bestanden, controleert u of de naam van deze bestanden correct is gewijzigd.

Als u Apache-instructies ziet die niet zijn gewhitelist, verwijdert u deze.

### Alle niet-publicatiebedrijven verwijderen

Verwijder om het even welk landbouwbedrijfdossier in `conf.dispatcher.d/enabled_farms` die heeft `author`, `unhealthy`, `health`of`lc` `flush` in zijn naam. Alle landbouwbedrijfdossiers in `conf.dispatcher.d/available_farms` die niet met worden verbonden kunnen eveneens worden verwijderd.

### Namen van landbouwbestanden wijzigen

Alle boerderijen in `conf.d/enabled_farms` moeten een andere naam krijgen om overeen te komen met het patroon, `*.farm`dus de naam van het afarmbestand `customerX_farm.any` moet worden gewijzigd `customerX.farm`.

### Cache controleren

Map invoeren `conf.dispatcher.d/cache`.

Verwijder alle vooraf ingestelde bestanden `ams_`.

Als het bestand nu leeg `conf.dispatcher.d/cache` is, kopieert u het bestand `conf.dispatcher.d/cache/rules.any`van de standaardconfiguratie van de verzender naar deze map. De standaardconfiguratie voor verzendingen vindt u in de map `src` van deze SDK. Vergeet niet om de verklaringen aan te passen die`$include` `ams_*_cache.any` naar de regeldossiers in de landbouwbedrijfdossiers verwijzen.

Als in plaats daarvan `conf.dispatcher.d/cache` nu één enkel dossier met achtervoegsel `_cache.any`bevat, zou het moeten worden anders genoemd aan `rules.any` `$include` en vergeet niet om de verklaringen aan te passen die naar dat dossier in de landbouwbedrijfdossiers verwijzen.

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, zou hun inhoud aan de `$include` verklaring moeten worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

Verwijder elk bestand met het achtervoegsel `_invalidate_allowed.any`.

Kopieer het bestand `conf.dispatcher.d/cache/default_invalidate_any` van de standaardAEM in de configuratie van de Cloud-dispatcher naar die locatie.

In elk landbouwbedrijfdossier, verwijder om het even welke inhoud in de `cache/allowedClients` sectie en vervang het door:

```
$include "../cache/default_invalidate.any"
```

### Clientkoppen controleren

Map invoeren `conf.dispatcher.d/clientheaders`.

Verwijder alle vooraf ingestelde bestanden `ams_`.

Als `conf.dispatcher.d/clientheaders` nu één enkel dossier met achtervoegsel `_clientheaders.any`bevat, zou het moeten worden anders genoemd aan `clientheaders.any` `$include` en vergeet niet om de verklaringen aan te passen die naar dat dossier in de landbouwbedrijfdossiers verwijzen.

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, zou hun inhoud aan de `$include` verklaring moeten worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

Kopieer het bestand `conf.dispatcher/clientheaders/default_clientheaders.any` van de standaardAEM als een configuratie van een serviceverzender naar die locatie.

In elk landbouwbedrijfdossier, vervang om het even welke cliënt omvat verklaringen die als volgt kijken:

```
$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"
$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"
```

met de verklaring:

```
$include "../clientheaders/default_clientheaders.any"
```

### Filter controleren

Map invoeren `conf.dispatcher.d/filters`.

Verwijder alle vooraf ingestelde bestanden `ams_`.

Als `conf.dispatcher.d/filters` nu één enkel dossier bevat zou het moeten worden anders genoemd aan`filters.any` en vergeet niet om de `$include` verklaringen aan te passen verwijzend naar dat dossier in de landbouwbedrijfdossiers eveneens.

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, zou hun inhoud aan de `$include` verklaring moeten worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

Kopieer het bestand `conf.dispatcher/filters/default_filters.any` van de standaardAEM als een configuratie van een serviceverzender naar die locatie.

In elk landbouwbedrijfdossier, vervang om het even welke filter omvat verklaringen die als volgt kijken:

```
$include "/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"
```

met de verklaring:

```
$include "../filters/default_filters.any"
```

### Renderingen controleren

Map invoeren `conf.dispatcher.d/renders`.

Verwijder alle bestanden in die map.

Kopieer het bestand `conf.dispatcher.d/renders/default_renders.any` van de standaardAEM als een configuratie van een serviceverzender naar die locatie.

In elk landbouwbedrijfdossier, verwijder om het even welke inhoud in de `renders` sectie en vervang het door:

```
$include "../renders/default_renders.any"
```

### Virtuele hosts controleren

Wijzig de naam van de map `conf.dispatcher.d/vhosts` in `conf.dispatcher.d/virtualhosts` en voer deze in.

Verwijder alle vooraf ingestelde bestanden `ams_`.

Als `conf.dispatcher.d/virtualhosts` nu één enkel dossier bevat zou het moeten worden anders genoemd aan`virtualhosts.any` en vergeet niet om de `$include` verklaringen aan te passen verwijzend naar dat dossier in de landbouwbedrijfdossiers eveneens.

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, zou hun inhoud aan de `$include` verklaring moeten worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

Kopieer het bestand `conf.dispatcher/virtualhosts/default_virtualhosts.any` van de standaardAEM als een configuratie van een serviceverzender naar die locatie.

In elk landbouwbedrijfdossier, vervang om het even welke filter omvat verklaringen die als volgt kijken:

```
$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"
```

met de verklaring:

```
$include "../virtualhosts/default_virtualhosts.any"
```

### Controleer uw status door validator uit te voeren

Voer de AEM als validator van de verzender van de Cloud-service uit in uw directory, met de `dispatcher` subopdracht:

```
$ validator dispatcher .
```

Als er fouten optreden bij ontbrekende include-bestanden, controleert u of de naam van deze bestanden correct is gewijzigd.

Als er fouten optreden met betrekking tot een niet-gedefinieerde variabele, wijzigt u de naam `PUBLISH_DOCROOT`in `DOCROOT`.

Zie de sectie Problemen oplossen in de documentatie over het validatieprogramma voor elke andere fout.

### Test uw configuratie met een lokale plaatsing (vereist de installatie van Docker)

Gebruikend het manuscript `docker_run.sh` in AEM als Hulpmiddelen van de Verzender van de Dienst van de Wolk, kunt u testen dat uw configuratie geen andere fout bevat die slechts inplaatsing zou tonen:

### Stap 1: Implementatiegegevens genereren met de validator

```
validator full -d out .
```

Dit bevestigt de volledige configuratie en produceert plaatsingsinformatie binnen `out`

### Stap 2: Start de dispatcher in een docker-image met die implementatiegegevens

Als uw AEM-publicatieserver op uw MacOS-computer wordt uitgevoerd en u luistert naar poort 4503, kunt u de dispatcher als volgt voor die server starten:

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

Dit zal de container beginnen en Apache op lokale haven 8080 blootstellen.

### De nieuwe configuratie van de verzender gebruiken

Gefeliciteerd! Als de validator geen probleem meer rapporteert en de dockercontainer wordt gestart zonder fouten of waarschuwingen, kunt u uw configuratie verplaatsen naar een `dispatcher/src` subdirectory van uw it-opslagplaats.

**Klanten die AMS Dispatcher Configuration versie 1 gebruiken, dienen contact op te nemen met de klantenondersteuning om hen te helpen bij de migratie van versie 1 naar versie 2, zodat bovenstaande instructies kunnen worden opgevolgd.**
