---
title: Validatie en foutopsporing met Dispatcher Tools
description: Validatie en foutopsporing met Dispatcher Tools
feature: Dispatcher
exl-id: 9e8cff20-f897-4901-8638-b1dbd85f44bf
source-git-commit: a81bd6ee4957f17acb79093f6ed232674fd93d60
workflow-type: tm+mt
source-wordcount: '2413'
ht-degree: 1%

---

# Validatie en foutopsporing met Dispatcher Tools {#Dispatcher-in-the-cloud}

## Inleiding {#apache-and-dispatcher-configuration-and-testing}

>[!NOTE]
>Raadpleeg de [Dispatcher op de pagina Cloud](/help/implementing/dispatcher/disp-overview.md) voor meer informatie over Dispatcher in de cloud en hoe u Dispatcher Tools downloadt. Als de configuratie van de verzender in erfeniswijze is, verwijs naar [verouderde wijzedocumentatie](/help/implementing/dispatcher/validation-debug-legacy.md).

In de volgende secties wordt de structuur van het bestand in de flexibele modus beschreven, evenals lokale validatie, foutopsporing en migratie van de oude modus naar de flexibele modus.

In dit artikel wordt ervan uitgegaan dat de configuratie van de verzender van uw project het bestand `opt-in/USE_SOURCES_DIRECTLY` bevat, waardoor de SDK en de runtime de configuratie beter kunnen valideren en implementeren dan in de verouderde modus, waarbij beperkingen rond het aantal en de grootte van bestanden worden verwijderd.

Als uw configuratie van de verzender het bovengenoemde dossier niet omvat, is het **hoogst geadviseerd** dat u van erfeniswijze aan de flexibele wijze zoals die in [zich van erfeniswijze aan flexibele wijze wordt geschetst ](#migrating) sectie migreert.

## Bestandsstructuur {#flexible-mode-file-structure}

De structuur van de submap Dispatcher van het project is als volgt:

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
│── opt-in
│   └── USE_SOURCES_DIRECTLY
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
    │   ├── default_virtualhosts.any
    │   └── virtualhosts.any
    
```

Hieronder vindt u een uitleg van belangrijke bestanden die kunnen worden gewijzigd:

**Aanpasbare bestanden**

De volgende bestanden kunnen worden aangepast en worden bij de implementatie overgebracht naar uw Cloud-instantie:

* `conf.d/available_vhosts/<CUSTOMER_CHOICE>.vhost`

U kunt een of meer van deze bestanden hebben. Zij bevatten `<VirtualHost>` ingangen die gastheernamen aanpassen en Apache toestaan om elk domeinverkeer met verschillende regels te behandelen. Bestanden worden gemaakt in de map `available_vhosts` en ingeschakeld met een symbolische koppeling in de map `enabled_vhosts`. Van de `.vhost` dossiers, zullen andere dossiers zoals herschrijft en variabelen worden omvat.

* `conf.d/rewrites/rewrite.rules`

Dit bestand wordt opgenomen vanuit uw `.vhost`-bestanden. Het heeft een reeks herschrijfregels voor `mod_rewrite`.

* `conf.d/variables/custom.vars`

Dit bestand wordt opgenomen vanuit uw `.vhost`-bestanden. U kunt op deze locatie definities voor Apache-variabelen toevoegen.

* `conf.d/variables/global.vars`

Dit bestand wordt opgenomen vanuit het `dispatcher_vhost.conf`-bestand. U kunt de Dispatcher wijzigen en het logniveau in dit bestand herschrijven.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

U kunt één of meerdere van deze dossiers hebben, en zij bevatten landbouwbedrijven om gastheernamen aan te passen en de module van de Verzender toe te staan om elk landbouwbedrijf met verschillende regels te behandelen. Bestanden worden gemaakt in de map `available_farms` en ingeschakeld met een symbolische koppeling in de map `enabled_farms`. Van de `.farm` dossiers, zullen andere dossiers zoals filters, geheim voorgeheugenregels en anderen worden omvat.

* `conf.dispatcher.d/cache/rules.any`

Dit bestand wordt opgenomen vanuit uw `.farm`-bestanden. Hiermee geeft u voorkeuren voor caching op.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

Dit bestand wordt opgenomen vanuit uw `.farm`-bestanden. Het specificeert welke verzoekkopballen aan het achtereind door:sturen.

* `conf.dispatcher.d/filters/filters.any`

Dit bestand wordt opgenomen vanuit uw `.farm`-bestanden. Het heeft een reeks regels die veranderen welk verkeer uit zou moeten worden gefiltreerd en niet het aan het achterste eind maken.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

Dit bestand wordt opgenomen vanuit uw `.farm`-bestanden. Het heeft een lijst van gastheernamen of de wegen van URI die door glob aanpassing moeten worden aangepast. Dit bepaalt welke achtergrond om een verzoek te dienen.

* `opt-in/USE_SOURCES_DIRECTLY`

Dit bestand maakt een flexibelere configuratie van de verzender mogelijk en verwijdert eerdere beperkingen met betrekking tot het aantal en de grootte van bestanden. De SDK en de runtime zorgen er ook voor dat de configuratie op een verbeterde manier wordt gevalideerd en geïmplementeerd.

De bovenstaande bestanden verwijzen naar de onderstaande onveranderlijke configuratiebestanden. Wijzigingen in de onveranderbare bestanden worden niet verwerkt door Dispatchers in Cloud-omgevingen.

**Immuable Configuration Files**

Deze bestanden maken deel uit van het basiskader en zorgen ervoor dat standaarden en beste praktijken worden nageleefd. De bestanden worden als onveranderlijk beschouwd, omdat het wijzigen of verwijderen ervan lokaal geen invloed heeft op uw implementatie, omdat deze bestanden niet worden overgedragen naar uw Cloud-instantie.

Het wordt aanbevolen dat de bovenstaande bestanden verwijzen naar de hieronder vermelde onveranderlijke bestanden, gevolgd door aanvullende instructies of overschrijvingen. Wanneer de configuratie van de Verzender aan een wolkenmilieu wordt opgesteld, zal de recentste versie van de onveranderlijke dossiers worden gebruikt, ongeacht welke versie in lokale ontwikkeling werd gebruikt.

* `conf.d/available_vhosts/default.vhost`

Bevat een virtuele voorbeeldhost. Voor uw eigen virtuele host maakt u een kopie van dit bestand, past u het aan, gaat u naar `conf.d/enabled_vhosts` en maakt u een symbolische koppeling naar uw aangepaste kopie.

* `conf.d/dispatcher_vhost.conf`

Deel van het basisframework dat wordt gebruikt om te illustreren hoe uw virtuele hosts en globale variabelen worden opgenomen.

* `conf.d/rewrites/default_rewrite.rules`

Standaard herschrijft regels geschikt voor een standaardproject. Als u aanpassing nodig hebt, wijzigt u `rewrite.rules`. In uw aanpassing, kunt u nog de standaardregels eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/available_farms/default.farm`

Bevat een bedrijf van de steekproefDispatcher. Voor uw eigen landbouwbedrijf, creeer een exemplaar van dit dossier, pas het aan, ga naar `conf.d/enabled_farms` en creeer een symbolische verbinding aan uw aangepaste exemplaar.

* `conf.dispatcher.d/cache/default_invalidate.any`

Een deel van het basiskader, wordt geproduceerd bij opstarten. U bent **required** om dit dossier in elk landbouwbedrijf te omvatten u, in `cache/allowedClients` sectie bepaalt.

* `conf.dispatcher.d/cache/default_rules.any`

De standaard geheim voorgeheugenregels geschikt voor een standaardproject. Als u aanpassing nodig hebt, wijzigt u `conf.dispatcher.d/cache/rules.any`. In uw aanpassing, kunt u nog de standaardregels eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/clientheaders/default_clientheaders.any`

De standaard verzoekkopballen om aan het achterste deel door:sturen, geschikt voor een standaardproject. Als u aanpassing nodig hebt, wijzigt u `clientheaders.any`. In uw aanpassing, kunt u nog de standaardverzoekkopballen eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/dispatcher.any`

Deel van basisframework dat wordt gebruikt om te illustreren hoe uw Dispatcher-boerderijen worden opgenomen.

* `conf.dispatcher.d/filters/default_filters.any`

Standaardfilters die geschikt zijn voor een standaardproject. Als u aanpassing nodig hebt, wijzigt u `filters.any`. In uw aanpassing, kunt u nog de standaardfilters eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/renders/default_renders.any`

Als onderdeel van het basisframework wordt dit bestand bij het opstarten gegenereerd. U bent **required** om dit dossier in elk landbouwbedrijf te omvatten u, in `renders` sectie bepaalt.

* `conf.dispatcher.d/virtualhosts/default_virtualhosts.any`

Standaardhostglobing geschikt voor een standaardproject. Als u aanpassing nodig hebt, wijzigt u `virtualhosts.any`. In uw aanpassing, zou u niet de standaard gastheer het globbings moeten omvatten, aangezien het **elke** inkomend verzoek aanpast.

## Ondersteunde Apache-modules {#apache-modules}

Zie [Ondersteunde Apache-modules](/help/implementing/dispatcher/disp-overview.md#supported-directives).

## Lokale validatie {#local-validation-flexible-mode}

>[!NOTE]
>De onderstaande secties bevatten opdrachten met behulp van de Mac- of Linux-versies van de SDK, maar de Windows SDK kan ook op dezelfde manier worden gebruikt.

Gebruik het `validate.sh` manuscript zoals hieronder getoond:

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
2. Het voert het `httpd -t` bevel uit om te testen als de syntaxis correct is zodat apache httpd kan beginnen. Indien succesvol, zou de configuratie voor plaatsing klaar moeten zijn.
3. Controleert dat de ondergroep van de de configuratiedossiers van SDK van de Dispatcher, die bedoeld zijn om onveranderlijk te zijn zoals die in [de sectie van de Bestandsstructuur](##flexible-mode-file-structure) worden beschreven, niet is gewijzigd.

Tijdens de implementatie van Cloud Manager wordt de syntaxiscontrole `httpd -t` ook uitgevoerd en worden eventuele fouten opgenomen in het logbestand voor Cloud Manager `Build Images step failure`.

### Fase 1 {#first-phase}

Als een instructie niet is gevoegd op lijst van gewenste personen, wordt een fout geregistreerd en wordt een afsluitcode van niet nul geretourneerd. Bovendien worden alle bestanden met patroon `conf.dispatcher.d/enabled_farms/*.farm` gescand en wordt gecontroleerd of:

* Er bestaat geen filterregel die via `/glob` (zie [CVE-2016-0957](https://nvd.nist.gov/vuln/detail/CVE-2016-0957) voor meer informatie toestaat.
* Er wordt geen beheerfunctie weergegeven. Bijvoorbeeld toegang tot paden zoals `/crx/de or /system/console`.

Let op: het validatiehulpmiddel rapporteert alleen het verboden gebruik van Apache-instructies die niet zijn gevoegd op lijst van gewenste personen. Er worden geen syntactische of semantische problemen met uw Apache-configuratie gemeld, aangezien deze informatie alleen beschikbaar is voor Apache-modules in een actieve omgeving.

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
Apache-configuratie en bestanden met `ams_` voorvoegsels. Hoewel dit nog steeds wordt ondersteund
moet u overschakelen naar de nieuwe indeling.

Houd er rekening mee dat de eerste fase ook afzonderlijk **kan worden uitgevoerd** in plaats van vanuit het omvattende `validate.sh`-script.

Wanneer de looppas tegen uw beven artefact of uw `dispatcher/src` subdirectory, zal het bevestigingsmislukkingen melden:

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

Vermijd deze fout door de weg van de Ontdekkingsreiziger van Vensters en dan op de bevelherinnering te kopiëren en te kleven gebruikend een `cd` bevel in die weg.

### Fase 2 {#second-phase}

Deze fase controleert de pijnsyntaxis door Docker in een beeld te beginnen. Docker moet lokaal zijn geïnstalleerd, maar AEM hoeft niet te worden uitgevoerd.

>[!NOTE]
>Windows-gebruikers moeten Windows 10 Professional of andere distributies gebruiken die Docker ondersteunen. Dit is een vereiste voor het uitvoeren van en het zuiveren van Dispatcher op een lokale computer.

Deze fase kan ook onafhankelijk door `bin/docker_run.sh src/dispatcher host.internal.docker:4503 8080` worden in werking gesteld.

Tijdens de implementatie van Cloud Manager wordt de syntaxiscontrole `httpd -t` ook uitgevoerd en worden eventuele fouten opgenomen in het foutenlogboek voor de stap Images maken van Cloud Manager.

### Fase 3 {#third-phase}

Als er een fout in deze fase is, impliceert het dat Adobe één of meerdere onveranderlijke dossiers heeft veranderd en u moet de overeenkomstige onveranderlijke dossiers met de nieuwe versie vervangen die in `src` folder van SDK wordt geleverd. In het onderstaande logboekvoorbeeld ziet u dit probleem:

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

Deze fase kan ook onafhankelijk door `bin/docker_immutability_check.sh src/dispatcher` worden in werking gesteld.

## Fouten opsporen in uw Apache- en Dispatcher-configuratie {#debugging-apache-and-dispatcher-configuration}

Houd er rekening mee dat u apache dispatcher lokaal kunt uitvoeren met `./bin/docker_run.sh src/dispatcher docker.for.mac.localhost:4503 8080`.

Zoals eerder vermeld, moet Docker plaatselijk worden geïnstalleerd en het is niet noodzakelijk voor AEM in werking te stellen. Windows-gebruikers moeten Windows 10 Professional of andere distributies gebruiken die Docker ondersteunen. Dit is een vereiste voor het uitvoeren van en het zuiveren van Dispatcher op een lokale computer.

De volgende strategie kan worden gebruikt om de logboekoutput voor de module van de Verzender te verhogen en de resultaten van de `RewriteRule` evaluatie in zowel lokale als wolkenmilieu&#39;s te zien.

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

Wanneer het runnen van Verzender plaatselijk, worden de logboeken gedrukt direct aan de eindoutput. Meestal, wilt u deze logboeken in DEBUG zijn, die kan worden gedaan door het Debug niveau als parameter over te gaan wanneer het runnen van Docker. Bijvoorbeeld: `DISP_LOG_LEVEL=Debug ./bin/docker_run.sh src docker.for.mac.localhost:4503 8080`.

Logbestanden voor cloudomgevingen worden weergegeven via de logbestandsservice die beschikbaar is in Cloud Manager.

## Verschillende Dispatcher-configuraties per omgeving {#different-dispatcher-configurations-per-environment}

Momenteel wordt dezelfde Dispatcher-configuratie toegepast op alle AEM als een Cloud Service-omgeving. De runtime heeft een omgevingsvariabele `ENVIRONMENT_TYPE` die de huidige uitvoermodus (dev, stage of prod) en een definitie bevat. De definitie kan `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE` of `ENVIRONMENT_PROD` zijn. In de Apache-configuratie kan de variabele rechtstreeks in een expressie worden gebruikt. U kunt ook de definitie gebruiken om logica op te bouwen:

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
$ DISP_RUN_MODE=stage docker_run.sh src docker.for.mac.localhost:4503 8080
```

De standaardrunmode wanneer het overgaan niet in een waarde voor DISP_RUN_MODE is &quot;dev&quot;.
Voor een volledige lijst van beschikbare opties en variabelen, stel het manuscript `docker_run.sh` zonder argumenten in werking.

## De Dispatcher-configuratie bekijken die door de Docker-container wordt gebruikt {#viewing-dispatcher-configuration-in-use-by-docker-container}

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

## Migreren van oude modus naar flexibele modus {#migrating}

Met de release van Cloud Manager 2021.7.0 genereren nieuwe programma&#39;s van Cloud Manager gefundeerde projectstructuren met [AEM archetype 28](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=en) of hoger, waaronder het bestand **opt-in/USE_SOURCES_DIRECTLY**. Hierdoor worden eerdere beperkingen van de [verouderde modus](/help/implementing/dispatcher/validation-debug-legacy.md) met betrekking tot het aantal en de grootte van bestanden verwijderd, waardoor de SDK en de runtime de configuratie op een verbeterde manier valideren en implementeren. Als dit bestand niet in de configuratie van de verzender staat, wordt u ten zeerste aangeraden te migreren. Gebruik de volgende stappen om een veilige overgang te garanderen:

1. **Lokaal testen.** Voeg de map en het bestand toe met de meest recente SDK voor verzendprogramma&#39;s  `opt-in/USE_SOURCES_DIRECTLY`. Volg de instructies voor lokale validatie in dit artikel om te testen of de verzender lokaal werkt.
2. **Testen voor ontwikkeling van cloud:**
   * Leg het bestand `opt-in/USE_SOURCES_DIRECTLY` vast aan een git-vertakking die wordt geïmplementeerd door de niet-productiepijpleiding naar een Cloud-ontwikkelomgeving.
   * Gebruik Cloud Manager om te implementeren in een Cloud-ontwikkelomgeving.
   * Test grondig. Het is essentieel om te controleren of uw apache- en dispatcherconfiguratie zich gedraagt zoals u verwacht voordat u wijzigingen in hogere omgevingen implementeert. Controleer al gedrag met betrekking tot uw douaneconfiguratie! Bestand een ondersteuningsticket voor de klant als u denkt dat de configuratie van de geïmplementeerde dispatcher uw aangepaste configuratie niet weerspiegelt.
3. **Distribueren naar productie:**
   * Leg het bestand `opt-in/USE_SOURCES_DIRECTLY` vast aan een git-vertakking die wordt geïmplementeerd door de productiepijpleiding naar het werkgebied en de productieomgevingen van de cloud.
   * Gebruik Cloud Manager om te implementeren in testfasen.
   * Test grondig. Het is essentieel om te controleren of uw apache- en dispatcherconfiguratie zich gedraagt zoals u verwacht voordat u wijzigingen in hogere omgevingen implementeert. Controleer al gedrag met betrekking tot uw douaneconfiguratie! Bestand een ondersteuningsticket voor de klant als u denkt dat de configuratie van de geïmplementeerde dispatcher uw aangepaste configuratie niet weerspiegelt.
   * Gebruik Cloud Manager om de implementatie naar productie voort te zetten.
