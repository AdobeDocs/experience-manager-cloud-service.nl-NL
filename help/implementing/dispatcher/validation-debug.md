---
title: Validatie en foutopsporing met Dispatcher Tools
description: Validatie en foutopsporing met Dispatcher Tools
feature: Dispatcher
exl-id: 9e8cff20-f897-4901-8638-b1dbd85f44bf
source-git-commit: 37c948b8906bcf6dd7ee3acdc6c6b7d211a33058
workflow-type: tm+mt
source-wordcount: '2701'
ht-degree: 0%

---

# Validatie en foutopsporing met Dispatcher Tools {#Dispatcher-in-the-cloud}

## Inleiding {#apache-and-dispatcher-configuration-and-testing}

>[!NOTE]
>Raadpleeg voor meer informatie over Dispatcher in de cloud en over het downloaden van Dispatcher Tools de [Dispatcher in de cloud](/help/implementing/dispatcher/disp-overview.md) pagina. Als de configuratie van de verzender in verouderde modus is, raadpleegt u de [documentatie over oudere modus](/help/implementing/dispatcher/validation-debug-legacy.md).

In de volgende secties wordt de structuur van het bestand in de flexibele modus beschreven, evenals lokale validatie, foutopsporing en migratie van de oude modus naar de flexibele modus.

In dit artikel wordt ervan uitgegaan dat het bestand is opgenomen in de configuratie van de dispatcher van uw project `opt-in/USE_SOURCES_DIRECTLY`, waardoor de SDK en de runtime de configuratie beter kunnen valideren en implementeren dan in de verouderde modus, waarbij beperkingen rond het aantal en de grootte van bestanden worden verwijderd.

Als uw configuratie van de dispatcher het bovengenoemde bestand niet bevat, is het **aanbevolen** dat u van erfeniswijze aan de flexibele wijze zoals die in wordt geschetst migreert [Migreren van oude modus naar flexibele modus](#migrating) sectie.

## Bestandsstructuur {#flexible-mode-file-structure}

De structuur van de submap Dispatcher van het project is als volgt:

```bash
./
├── conf.d
│   ├── available_vhosts
│   │   ├── my_site.vhost # Created by customer
│   │   └── default.vhost
│   ├── dispatcher_vhost.conf
│   ├── enabled_vhosts
│   │   ├── README
│   │   └── my_site.vhost -> ../available_vhosts/my_site.vhost  # Created by customer
│   └── rewrites
│   │   ├── default_rewrite.rules
│   │   └── rewrite.rules
│   └── variables
|       ├── custom.vars
│       └── global.vars
│── opt-in
│   └── USE_SOURCES_DIRECTLY
└── conf.dispatcher.d
    ├── available_farms
    │   ├── my_farm.farm # Created by customer
    │   └── default.farm
    ├── cache
    │   ├── default_invalidate.any
    │   ├── default_rules.any
    │   ├── marketing_query_parameters.any
    │   └── rules.any
    ├── clientheaders
    │   ├── clientheaders.any
    │   └── default_clientheaders.any
    ├── dispatcher.any
    ├── enabled_farms
    │   ├── README
    │   └── my_farm.farm -> ../available_farms/my_farm.farm  # Created by customer
    ├── filters
    │   ├── default_filters.any
    │   └── filters.any
    ├── renders
    │   └── default_renders.any
    └── virtualhosts
    │   ├── default_virtualhosts.any
    │   └── virtualhosts.any
    
```

Hieronder vindt u een uitleg van belangrijke bestanden die kunnen worden gewijzigd:

**Aanpasbare bestanden**

De volgende bestanden kunnen worden aangepast en worden bij de implementatie overgebracht naar uw Cloud-instantie:

* `conf.d/available_vhosts/<CUSTOMER_CHOICE>.vhost`

U kunt een of meer van deze bestanden hebben. Zij bevatten `<VirtualHost>` vermeldingen die de namen van de gastheer aanpassen en Apache toestaan om elk domeinverkeer met verschillende regels te behandelen. Bestanden worden gemaakt in het dialoogvenster `available_vhosts` en ingeschakeld met een symbolische koppeling in het dialoogvenster `enabled_vhosts` directory. Van de `.vhost` bestanden, andere bestanden zoals herschreven en variabelen worden opgenomen.

>[!NOTE]
>
>In de flexibele modus moet u relatieve paden gebruiken in plaats van absolute paden.

* `conf.d/rewrites/rewrite.rules`

Dit bestand wordt vanuit uw `.vhost` bestanden. Er is een set herschrijfregels voor `mod_rewrite`.

* `conf.d/variables/custom.vars`

Dit bestand wordt vanuit uw `.vhost` bestanden. U kunt op deze locatie definities voor Apache-variabelen toevoegen.

* `conf.d/variables/global.vars`

Dit bestand wordt opgenomen vanuit de `dispatcher_vhost.conf` bestand. U kunt de Dispatcher wijzigen en het logniveau in dit bestand herschrijven.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

U kunt één of meerdere van deze dossiers hebben, en zij bevatten landbouwbedrijven om gastheernamen aan te passen en de module van de Verzender toe te staan om elk landbouwbedrijf met verschillende regels te behandelen. Bestanden worden gemaakt in het dialoogvenster `available_farms` en ingeschakeld met een symbolische koppeling in het dialoogvenster `enabled_farms` directory. Van de `.farm` bestanden, andere bestanden zoals filters, cacheregels en andere bestanden worden opgenomen.

* `conf.dispatcher.d/cache/rules.any`

Dit bestand wordt vanuit uw `.farm` bestanden. Hiermee geeft u voorkeuren voor caching op.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

Dit bestand wordt vanuit uw `.farm` bestanden. Het specificeert welke verzoekkopballen aan het achtereind door:sturen.

* `conf.dispatcher.d/filters/filters.any`

Dit bestand wordt vanuit uw `.farm` bestanden. Het heeft een reeks regels die veranderen welk verkeer uit zou moeten worden gefiltreerd en niet het aan het achterste eind maken.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

Dit bestand wordt vanuit uw `.farm` bestanden. Het heeft een lijst van gastheernamen of de wegen van URI die door glob aanpassing moeten worden aangepast. Dit bepaalt welke achtergrond om een verzoek te dienen.

* `opt-in/USE_SOURCES_DIRECTLY`

Dit bestand maakt een flexibelere configuratie van de verzender mogelijk en verwijdert eerdere beperkingen met betrekking tot het aantal en de grootte van bestanden. De SDK en de runtime zorgen er ook voor dat de configuratie op een verbeterde manier wordt gevalideerd en geïmplementeerd.

De bovenstaande bestanden verwijzen naar de onderstaande onveranderlijke configuratiebestanden. Wijzigingen in de onveranderbare bestanden worden niet verwerkt door Dispatchers in Cloud-omgevingen.

**Immuable Configuration Files**

Deze bestanden maken deel uit van het basiskader en zorgen ervoor dat standaarden en beste praktijken worden nageleefd. De bestanden worden als onveranderlijk beschouwd, omdat het wijzigen of verwijderen ervan lokaal geen invloed heeft op uw implementatie, omdat deze bestanden niet worden overgedragen naar uw Cloud-instantie.

Het wordt aanbevolen dat de bovenstaande bestanden verwijzen naar de hieronder vermelde onveranderlijke bestanden, gevolgd door aanvullende instructies of overschrijvingen. Wanneer de configuratie van de Verzender aan een wolkenmilieu wordt opgesteld, zal de recentste versie van de onveranderlijke dossiers worden gebruikt, ongeacht welke versie in lokale ontwikkeling werd gebruikt.

* `conf.d/available_vhosts/default.vhost`

Bevat een virtuele voorbeeldhost. Voor uw eigen virtuele host maakt u een kopie van dit bestand, past u het aan, gaat u naar `conf.d/enabled_vhosts` en maak een symbolische koppeling naar uw aangepaste kopie.
Kopieer het bestand default.vhost niet rechtstreeks naar `conf.d/enabled_vhosts`.

Zorg ervoor dat er altijd een virtuele host beschikbaar is die overeenkomt met ServerAlias `\*.local` en ook localhost, nodig voor interne Adobe-processen.

* `conf.d/dispatcher_vhost.conf`

Deel van het basisframework dat wordt gebruikt om te illustreren hoe uw virtuele hosts en globale variabelen worden opgenomen.

* `conf.d/rewrites/default_rewrite.rules`

Standaard herschrijft regels geschikt voor een standaardproject. Als u aanpassingen nodig hebt, wijzigt u `rewrite.rules`. In uw aanpassing, kunt u nog de standaardregels eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/available_farms/default.farm`

Bevat een bedrijf van de steekproefDispatcher. Voor uw eigen landbouwbedrijf, creeer een exemplaar van dit dossier, pas het aan, ga naar `conf.d/enabled_farms` en maak een symbolische koppeling naar uw aangepaste kopie.

* `conf.dispatcher.d/cache/default_invalidate.any`

Een deel van het basiskader, wordt geproduceerd bij opstarten. U bent **vereist** om dit dossier in elk landbouwbedrijf te omvatten u bepaalt, in `cache/allowedClients` sectie.

* `conf.dispatcher.d/cache/default_rules.any`

De standaard geheim voorgeheugenregels geschikt voor een standaardproject. Als u aanpassingen nodig hebt, wijzigt u `conf.dispatcher.d/cache/rules.any`. In uw aanpassing, kunt u nog de standaardregels eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/clientheaders/default_clientheaders.any`

De standaard verzoekkopballen om aan het achterste deel door:sturen, geschikt voor een standaardproject. Als u aanpassingen nodig hebt, wijzigt u `clientheaders.any`. In uw aanpassing, kunt u nog de standaardverzoekkopballen eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/dispatcher.any`

Deel van basisframework dat wordt gebruikt om te illustreren hoe uw Dispatcher-boerderijen worden opgenomen.

* `conf.dispatcher.d/filters/default_filters.any`

Standaardfilters die geschikt zijn voor een standaardproject. Als u aanpassingen nodig hebt, wijzigt u `filters.any`. In uw aanpassing, kunt u nog de standaardfilters eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/renders/default_renders.any`

Als onderdeel van het basisframework wordt dit bestand bij het opstarten gegenereerd. U bent **vereist** om dit dossier in elk landbouwbedrijf te omvatten u bepaalt, in `renders` sectie.

* `conf.dispatcher.d/virtualhosts/default_virtualhosts.any`

Standaardhostglobing geschikt voor een standaardproject. Als u aanpassingen nodig hebt, wijzigt u `virtualhosts.any`. In uw aanpassing, zou u niet het standaard gastheer globbings, aangezien het aanpast **elke** binnenkomend verzoek.

## Ondersteunde Apache-modules {#apache-modules}

Zie [Ondersteunde Apache-modules](/help/implementing/dispatcher/disp-overview.md#supported-directives).

## Lokale validatie {#local-validation-flexible-mode}

>[!NOTE]
>
>De onderstaande secties bevatten opdrachten met behulp van de Mac- of Linux-versies van de SDK, maar de Windows SDK kan ook op dezelfde manier worden gebruikt.

Gebruik de `validate.sh` script zoals hieronder weergegeven:

```
$ validate.sh src/dispatcher
opt-in USE_SOURCES_DIRECTLY marker file detected
Phase 1: Dispatcher validator
Cloud manager validator 2.0.32
Phase 1 finished
Phase 2: httpd -t validation in docker image
values.csv not found in deployment folder: /Users/foo/src - using files in 'conf.d' and 'conf.dispatcher.d' subfolders directly
processing configuration subfolder: conf.d
processing configuration subfolder: conf.dispatcher.d
Running script /docker_entrypoint.d/10-check-environment.sh
Running script /docker_entrypoint.d/20-create-docroots.sh
Running script /docker_entrypoint.d/30-wait-for-backend.sh
Waiting until localhost is available
localhost resolves to ::1
Running script /docker_entrypoint.d/40-generate-allowed-clients.sh
Running script /docker_entrypoint.d/50-check-expiration.sh
Running script /docker_entrypoint.d/60-check-loglevel.sh
Running script /docker_entrypoint.d/70-check-forwarded-host-secret.sh
# Dispatcher configuration: (/etc/httpd/conf.dispatcher.d/dispatcher.any)
/farms {

... 

}
Syntax OK
Phase 2 finished
Phase 3: Immutability check
reading immutable file list from /etc/httpd/immutable.files.txt

...

no immutable file has been changed - check is SUCCESSFUL
Phase 3 finished
```

Het script heeft de volgende drie fasen:

1. De validator wordt uitgevoerd. Als de configuratie ongeldig is, ontbreekt het manuscript.
2. Het voert het `httpd -t` om te testen of de syntaxis correct is, zodat apache httpd kan starten. Indien succesvol, zou de configuratie voor plaatsing klaar moeten zijn.
3. Controleert of de subset van de Dispatcher SDK-configuratiebestanden, die zijn bedoeld om onveranderbaar te zijn zoals beschreven in het dialoogvenster [Sectie Bestandsstructuur](##flexible-mode-file-structure), niet gewijzigd.

Tijdens een implementatie van Cloud Manager kunt u de `httpd -t` syntaxiscontrole wordt ook uitgevoerd en eventuele fouten worden opgenomen in Cloud Manager `Build Images step failure` log.

>[!NOTE]
>
>Zie de [Automatisch opnieuw laden en valideren](#automatic-loading) voor een efficiënt alternatief voor het uitvoeren `validate.sh` na elke configuratiewijziging.

### Fase 1 {#first-phase}

Als een instructie niet is gevoegd op lijst van gewenste personen, wordt een fout geregistreerd en wordt een afsluitcode van niet nul geretourneerd. Bovendien worden alle bestanden met een patroon gescand `conf.dispatcher.d/enabled_farms/*.farm` en controleert of:

* Er bestaat geen filterregel die via `/glob` (zie [CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957) voor meer informatie .
* Er wordt geen beheerfunctie weergegeven. Toegang tot bijvoorbeeld paden `/crx/de or /system/console`.

Let op: het validatiehulpmiddel rapporteert alleen het verboden gebruik van Apache-instructies die niet zijn gevoegd op lijst van gewenste personen. Er worden geen syntactische of semantische problemen met uw Apache-configuratie gemeld, aangezien deze informatie alleen beschikbaar is voor Apache-modules in een actieve omgeving.

Hieronder vindt u technieken voor het oplossen van problemen waarmee algemene validatiefouten kunnen worden opgespoord die door het programma worden uitgevoerd:

**kan een `conf.dispatcher.d` submap in het archief**

Uw archief moet mappen `conf.d` en `conf.dispatcher.d` bevatten. Let op: gebruik het voorvoegsel `etc/httpd` **niet** in uw archief.

**geen bedrijf kunnen vinden in`conf.dispatcher.d/enabled_farms`**

Uw ingeschakelde landbouwbedrijven zouden in bovengenoemde subfolder moeten worden gevestigd.

**Ingesloten bestand (...) moet een naam hebben: ...**

Er zijn twee secties in uw landbouwbedrijfconfiguratie die **moet** een specifiek bestand opnemen: `/renders` en `/allowedClients` in de `/cache` sectie. Deze delen moeten er als volgt uitzien:

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

Er zijn vier secties in uw landbouwbedrijfconfiguratie waar u uw eigen dossier mag omvatten: `/clientheaders`, `filters`, `/rules` in `/cache` en `/virtualhosts`. De opgenomen bestanden moeten als volgt worden benoemd:

| Sectie | Bestandsnaam opnemen |
|------------------|--------------------------------------|
| `/clientheaders` | `../clientheaders/clientheaders.any` |
| `/filters` | `../filters/filters.any` |
| `/rules` | `../cache/rules.any` |
| `/virtualhosts` | `../virtualhosts/virtualhosts.any` |

U kunt ook de opdracht **default** versie van deze bestanden waarvan de namen worden voorafgegaan door het woord `default_`, bijvoorbeeld `../filters/default_filters.any`.

**include statement at (...), outside any known location: ...**

Behalve de zes secties die in de bovenstaande paragrafen worden vermeld, bent u niet toegestaan om `$include` Deze fout wordt bijvoorbeeld gegenereerd door de volgende instructie:

```
/invalidate {
    $include "../cache/invalidate.any"
}
```

**toegestane clients/renderingen zijn niet inbegrepen bij: ...**

Deze fout wordt gegenereerd wanneer u geen include-bestand opgeeft voor `/renders` en `/allowedClients` in de `/cache` sectie. Zie de
**Ingesloten bestand (...) moet een naam hebben: ...** voor meer informatie.

**filter mag geen globpatroon gebruiken om verzoeken toe te staan**

Het is niet veilig om verzoeken toe te staan met een `/glob` stijlregel, die wordt aangepast aan de volledige aanvraagregel, bijvoorbeeld

```
/0100 {
    /type "allow" /glob "GET *.css *"
}
```

Deze verklaring moet verzoeken om `css` bestanden, maar ook verzoeken om **alle** resource gevolgd door de queryreeks `?a=.css`. Het is daarom verboden dergelijke filters te gebruiken (zie ook CVE-2016-0957).

**opgenomen bestand (...) komt niet overeen met een bekend bestand**

Standaard kunnen twee typen bestanden in uw virtuele Apache-hostconfiguratie worden opgegeven als: herschrijft en variabelen.

| Type | Bestandsnaam opnemen |
|-----------|---------------------------------|
| Herschrijven | `conf.d/rewrites/rewrite.rules` |
| Variabelen | `conf.d/variables/custom.vars` |

In de flexibele modus kunnen ook andere bestanden worden opgenomen, mits deze zich in submappen (op elk niveau) van `conf.d` directory vooraf ingesteld als volgt.

| Voorvoegsel van bovenste map van bestand opnemen |
|-------------------------------------|
| `conf.d/includes` |
| `conf.d/modsec` |
| `conf.d/rewrites` |

U kunt bijvoorbeeld een bestand opnemen in een nieuwe map onder `conf.d/includes` map als volgt:

```
Include conf.d/includes/mynewdirectory/myincludefile.conf
```

U kunt ook de opdracht **default** versie van de herschrijfregels, waarvan de naam is `conf.d/rewrites/default_rewrite.rules`.
Er is geen standaardversie van de variabelebestanden.

**Verouderde configuratielay-out gedetecteerd, compatibiliteitsmodus ingeschakeld**

Dit bericht geeft aan dat uw configuratie de verouderde versie 1-indeling heeft, die een volledige Apache-configuratie bevat en bestanden bevat met `ams_` voorvoegsels. Hoewel dit nog steeds wordt ondersteund voor achterwaartse compatibiliteit, dient u over te schakelen op de nieuwe indeling.

De eerste fase kan ook **afzonderlijk uitvoeren**, in plaats van uit de verpakking `validate.sh` script.

Als je in strijd bent met je beven artefact of je `dispatcher/src` subdirectory, zal het bevestigingsmislukkingen melden:

```
$ validator full -relaxed dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-allowlisted directives:
  conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
  conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

In Windows is de validator van de verzender hoofdlettergevoelig. Als dusdanig, kan het er niet in slagen om de configuratie te bevestigen als u niet de kapitalisatie van de weg respecteert waar uw configuratie, bijvoorbeeld verblijft:

```
bin\validator.exe -relaxed full src
Cloud manager validator 2.0.xx
2021/03/15 18:15:40 Dispatcher configuration validation failed:
  conf.dispatcher.d\available_farms\default.farm:15: parent directory outside server root: c:\k\a\aem-dispatcher-sdk-windows-symlinks-testing3\dispatcher\src
```

Vermijd deze fout door de weg van de Ontdekkingsreiziger van Vensters en dan op de bevelherinnering te kopiëren en te kleven gebruikend `cd` in dat pad.

### Fase 2 {#second-phase}

Deze fase controleert de pijnsyntaxis door Docker in een beeld te beginnen. Docker moet lokaal zijn geïnstalleerd, maar AEM hoeft niet te worden uitgevoerd.

>[!NOTE]
>
>Windows-gebruikers moeten Windows 10 Professional of andere distributies gebruiken die Docker ondersteunen. Dit is een vereiste voor het uitvoeren van en het zuiveren van Dispatcher op een lokale computer.

Deze fase kan ook onafhankelijk worden uitgevoerd `bin/docker_run.sh src/dispatcher host.docker.internal:4503 8080`.

Tijdens een implementatie van Cloud Manager kunt u de `httpd -t` syntaxiscontrole wordt ook uitgevoerd en eventuele fouten worden opgenomen in het foutenlogboek voor de stap Build Images in Cloud Manager.

### Fase 3 {#third-phase}

Als er een fout optreedt in deze fase, betekent dit dat Adobe een of meer onveranderbare bestanden heeft gewijzigd en dat u de overeenkomstige onveranderlijke bestanden moet vervangen door de nieuwe versie die wordt geleverd in het dialoogvenster `src` directory van de SDK. In het onderstaande logboekvoorbeeld ziet u dit probleem:

```
Phase 3: Immutability check
reading immutable file list from /etc/httpd/immutable.files.txt
(...)
checking existing 'conf.dispatcher.d/clientheaders/default_clientheaders.any' for changes
immutable file 'conf.dispatcher.d/clientheaders/default_clientheaders.any' has been changed:
--- /etc/httpd/conf.dispatcher.d/clientheaders/default_clientheaders.any
+++ /etc/httpd-actual/conf.dispatcher.d/clientheaders/default_clientheaders.any
@@ -40,4 +40,3 @@
"Sling-uploadmode"
"x-requested-with"
"If-Modified-Since"
-"Authorization"
** error: immutable file 'conf.dispatcher.d/clientheaders/default_clientheaders.any' has been changed!
  
```

Deze fase kan ook onafhankelijk worden uitgevoerd `bin/docker_immutability_check.sh src/dispatcher`.

## Fouten opsporen in uw Apache- en Dispatcher-configuratie {#debugging-apache-and-dispatcher-configuration}

Houd er rekening mee dat u een dispatcher lokaal kunt uitvoeren met `./bin/docker_run.sh src/dispatcher docker.for.mac.localhost:4503 8080`.

Zoals eerder vermeld, moet Docker plaatselijk worden geïnstalleerd en het is niet noodzakelijk voor AEM in werking te stellen. Windows-gebruikers moeten Windows 10 Professional of andere distributies gebruiken die Docker ondersteunen. Dit is een vereiste voor het uitvoeren van en het zuiveren van Dispatcher op een lokale computer.

De volgende strategie kan worden gebruikt om de logboekoutput voor de module van de Verzender te verhogen en de resultaten van te zien `RewriteRule` evaluatie in zowel lokale als cloudomgevingen.

De logbestandniveaus voor deze modules worden bepaald door de variabelen `DISP_LOG_LEVEL` en `REWRITE_LOG_LEVEL`. Deze kunnen in het bestand worden ingesteld `conf.d/variables/global.vars`. Het relevante deel is als volgt:

```
# Log level for the dispatcher
#
# Possible values are: error, warn, info, debug and trace1
# Default value: warn
#
# Define DISP_LOG_LEVEL warn
 
# Log level for mod_rewrite
#
# Possible values are: error, warn, info, debug and trace1 - trace8
# Default value: warn
#
# To debug your RewriteRules, it is recommended to raise your log
# level to trace2.
#
# More information can be found at:
# https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging
#
# Define REWRITE_LOG_LEVEL warn
```

Wanneer het runnen van Verzender plaatselijk, worden de logboeken gedrukt direct aan de eindoutput. Meestal, wilt u deze logboeken in DEBUG zijn, die kan worden gedaan door het Debug niveau als parameter over te gaan wanneer het runnen van Docker. Bijvoorbeeld: `DISP_LOG_LEVEL=Debug ./bin/docker_run.sh src docker.for.mac.localhost:4503 8080`.

Logbestanden voor cloudomgevingen worden weergegeven via de logbestandsservice die beschikbaar is in Cloud Manager.

### Automatisch opnieuw laden en valideren {#automatic-reloading}

>[!NOTE]
>
>Vanwege een beperking van het Windows-besturingssysteem is deze functie alleen beschikbaar voor macOS- en Linux-gebruikers.

In plaats van lokale validatie uit te voeren (`validate.sh`) en het starten van de dockercontainer (`docker_run.sh`) telkens als de configuratie wordt gewijzigd, kunt u anders in werking stellen `docker_run_hot_reload.sh` script.  Het script controleert op wijzigingen in de configuratie en laadt deze automatisch opnieuw en voert de validatie opnieuw uit. Met deze optie kunt u veel tijd besparen tijdens het opsporen van fouten.

U kunt het script uitvoeren met de volgende opdracht: `./bin/docker_run_hot_reload.sh src/dispatcher host.docker.internal:4503 8080`

Merk op dat de eerste lijnen van output gelijkaardig aan zullen kijken wat zou lopen voor `docker_run.sh`, bijvoorbeeld:

```
~ bin/docker_run_hot_reload.sh src host.docker.internal:8081 8082
opt-in USE_SOURCES_DIRECTLY marker file detected
Running script /docker_entrypoint.d/10-check-environment.sh
Running script /docker_entrypoint.d/15-check-pod-name.sh
Running script /docker_entrypoint.d/20-create-docroots.sh
Running script /docker_entrypoint.d/30-wait-for-backend.sh
Waiting until host.docker.internal is available
host.docker.internal resolves to 192.168.65.2
Running script /docker_entrypoint.d/40-generate-allowed-clients.sh
Running script /docker_entrypoint.d/50-check-expiration.sh
Running script /docker_entrypoint.d/60-check-loglevel.sh
Running script /docker_entrypoint.d/70-check-forwarded-host-secret.sh
Running script /docker_entrypoint.d/80-frontend-domain.sh
Running script /docker_entrypoint.d/zzz-import-sdk-config.sh
WARN Mon Jul  4 09:53:54 UTC 2022: Pseudo symlink conf.d seems to point to a non-existing file!
INFO Mon Jul  4 09:53:55 UTC 2022: Copied customer configuration to /etc/httpd.
INFO Mon Jul  4 09:53:55 UTC 2022: Start testing
Cloud manager validator 2.0.43
2022/07/04 09:53:55 No issues found
INFO Mon Jul  4 09:53:55 UTC 2022: Testing with fresh base configuration files.
INFO Mon Jul  4 09:53:55 UTC 2022: Apache httpd informationServer version: Apache/2.4.54 (Unix)
```

## Verschillende Dispatcher-configuraties per omgeving {#different-dispatcher-configurations-per-environment}

Momenteel wordt dezelfde Dispatcher-configuratie toegepast op alle AEM as a Cloud Service omgevingen. De runtime heeft een omgevingsvariabele `ENVIRONMENT_TYPE` die de huidige uitvoeringsmodus (dev, werkgebied of pod) en een definitie bevat. De definitie kan `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE` of `ENVIRONMENT_PROD`. In de Apache-configuratie kan de variabele rechtstreeks in een expressie worden gebruikt. U kunt ook de definitie gebruiken om logica op te bouwen:

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

U kunt ook omgevingsvariabelen van Cloud Manager gebruiken in uw httpd/dispatcher-configuratie, maar geen omgevingsgeheimen. Deze methode is vooral belangrijk als een programma meerdere ontwikkelomgevingen heeft en sommige van deze ontwikkelomgevingen verschillende waarden hebben voor de httpd/dispatcherconfiguratie. Dezelfde syntaxis ${VIRTUALHOST} wordt gebruikt als in het bovenstaande voorbeeld, maar de declaraties Definiëren in het bovenstaande variabelenbestand worden niet gebruikt. Lees de [Documentatie van Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) voor instructies over het configureren van omgevingsvariabelen van Cloud Manager.

Wanneer het testen van uw configuratie plaatselijk, kunt u verschillende milieutypes simuleren door de variabele over te gaan `DISP_RUN_MODE` aan de `docker_run.sh` script rechtstreeks:

```
$ DISP_RUN_MODE=stage docker_run.sh src docker.for.mac.localhost:4503 8080
```

De standaardrunmode wanneer het overgaan niet in een waarde voor DISP_RUN_MODE is &quot;dev&quot;.
Voer het script uit voor een volledige lijst met beschikbare opties en variabelen `docker_run.sh` zonder argumenten.

## De Dispatcher-configuratie bekijken die door de Docker-container wordt gebruikt {#viewing-dispatcher-configuration-in-use-by-docker-container}

Met milieu-specifieke configuraties, kan het moeilijk zijn om te bepalen hoe de daadwerkelijke configuratie van de Verzender kijkt als. Na het starten van de docker container met `docker_run.sh` het kan als volgt met dumping worden ingevoerd :

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

## Migreren van oude modus naar flexibele modus {#migrating}

Met de release van Cloud Manager 2021.7.0 genereren nieuwe programma&#39;s van Cloud Manager gemaven projectstructuren met [AEM archetype 28](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=en) of hoger, inclusief het bestand **opt-in/USE_SOURCES_DIRECTLY**. Hiermee worden eerdere beperkingen van het dialoogvenster [verouderde modus](/help/implementing/dispatcher/validation-debug-legacy.md) rond het aantal en de grootte van dossiers, die ook SDK en runtime ertoe brengen om de configuratie op een betere manier te bevestigen en op te stellen. Als dit bestand niet in de configuratie van de verzender staat, wordt u ten zeerste aangeraden te migreren. Gebruik de volgende stappen om een veilige overgang te garanderen:

1. **Lokaal testen.** Voeg de map en het bestand toe met behulp van de meest recente SDK voor verzendprogramma&#39;s `opt-in/USE_SOURCES_DIRECTLY`. Volg de instructies voor lokale validatie in dit artikel om te testen of de verzender lokaal werkt.
1. **Testen voor ontwikkeling van cloud:**
   * Het bestand vastleggen `opt-in/USE_SOURCES_DIRECTLY` aan een git tak die door de niet-productiepijpleiding aan een de ontwikkelomgeving van de Wolk wordt opgesteld.
   * Gebruik Cloud Manager om te implementeren in een Cloud-ontwikkelomgeving.
   * Test grondig. Het is essentieel om te controleren of uw apache- en dispatcherconfiguratie zich gedraagt zoals u verwacht voordat u wijzigingen in hogere omgevingen implementeert. Controleer al gedrag met betrekking tot uw douaneconfiguratie! Bestand een ondersteuningsticket voor de klant als u denkt dat de configuratie van de geïmplementeerde dispatcher uw aangepaste configuratie niet weerspiegelt.

   >[!NOTE]
   >
   >In de flexibele modus moet u relatieve paden gebruiken in plaats van absolute paden.
1. **Distribueren naar productie:**
   * Het bestand vastleggen `opt-in/USE_SOURCES_DIRECTLY` aan een git tak die door de productiepijpleiding aan het stadium van de Wolk en productiemilieu&#39;s wordt opgesteld.
   * Gebruik Cloud Manager om te implementeren in testfasen.
   * Test grondig. Het is essentieel om te controleren of uw apache- en dispatcherconfiguratie zich gedraagt zoals u verwacht voordat u wijzigingen in hogere omgevingen implementeert. Controleer al gedrag met betrekking tot uw douaneconfiguratie! Bestand een ondersteuningsticket voor de klant als u denkt dat de configuratie van de geïmplementeerde dispatcher uw aangepaste configuratie niet weerspiegelt.
   * Gebruik Cloud Manager om de implementatie naar productie voort te zetten.
