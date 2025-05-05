---
title: Validatie en foutopsporing met Dispatcher Tools
description: Leer meer over lokale validatie, foutopsporing, de bestandsstructuur in de flexibele modus en hoe u van de oude modus naar de flexibele modus kunt migreren.
feature: Dispatcher
exl-id: 9e8cff20-f897-4901-8638-b1dbd85f44bf
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '3028'
ht-degree: 0%

---

# Validatie en foutopsporing met Dispatcher Tools {#Dispatcher-in-the-cloud}

## Inleiding {#apache-and-dispatcher-configuration-and-testing}

>[!NOTE]
>Voor meer informatie over Dispatcher in de Wolk en hoe te om de Hulpmiddelen van Dispatcher te downloaden, zie [ Dispatcher in de Cloud ](/help/implementing/dispatcher/disp-overview.md) pagina. Als uw configuratie van Dispatcher op erfeniswijze is, zie [ documentatie van de erfeniswijze ](/help/implementing/dispatcher/validation-debug-legacy.md).

In de volgende secties wordt de structuur van het bestand in de flexibele modus beschreven, evenals lokale validatie, foutopsporing en migratie van de oude modus naar de flexibele modus.

In dit artikel wordt ervan uitgegaan dat het bestand `opt-in/USE_SOURCES_DIRECTLY` is opgenomen in de Dispatcher-configuratie van uw project. Dit bestand zorgt ervoor dat de SDK en de runtime de configuratie op een betere manier valideren en implementeren dan in de verouderde modus, waarbij beperkingen rond het aantal en de grootte van bestanden worden verwijderd.

Als uw configuratie van Dispatcher niet het eerder vermelde dossier omvat, adviseert de Adobe dat u van erfeniswijze aan de flexibele wijze zoals die in [ wordt geschetst migrerend van erfeniswijze aan flexibele wijze ](#migrating) sectie migreert.

## Bestandsstructuur {#flexible-mode-file-structure}

De submap Dispatcher van het project heeft de volgende structuur:

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

**Aanpasbare Dossiers**

De volgende bestanden kunnen worden aangepast en worden tijdens de implementatie overgebracht naar uw Cloud-instantie:

* `conf.d/available_vhosts/<CUSTOMER_CHOICE>.vhost`

U kunt een of meer van deze bestanden hebben. Ze bevatten `<VirtualHost>` -items die overeenkomen met hostnamen en staan Apache toe elk domeinverkeer met verschillende regels af te handelen. Bestanden worden gemaakt in de map `available_vhosts` en ingeschakeld met een symbolische koppeling in de map `enabled_vhosts` . Van de `.vhost` dossiers, zijn andere dossiers, zoals herschrijft en variabelen, inbegrepen.

>[!NOTE]
>
>In de flexibele modus moet u relatieve paden gebruiken in plaats van absolute paden.

Zorg ervoor dat er altijd ten minste één virtuele host beschikbaar is die overeenkomt met ServerAlias `\*.local` , `localhost` en `127.0.0.1` die nodig zijn voor de Dispatcher-validatie. De serveraliassen `*.adobeaemcloud.net` en `*.adobeaemcloud.com` zijn ook vereist in ten minste één hostconfiguratie en zijn nodig voor interne Adobe.

Als u precies de gastheer wilt aanpassen omdat u veelvoudige vhost dossiers hebt, kunt u het volgende voorbeeld volgen:

```
<VirtualHost *:80>
    ServerName    "example.com"
    # Put names of which domains are used for your published site/content here
    ServerAlias     "*example.com" "\*.local" "localhost" "127.0.0.1" "*.adobeaemcloud.net" "*.adobeaemcloud.com"
    # Use a document root that matches the one in conf.dispatcher.d/default.farm
    DocumentRoot "${DOCROOT}"
    # URI dereferencing algorithm is applied at Sling's level, do not decode parameters here
    AllowEncodedSlashes NoDecode
    # Add header breadcrumbs for help in troubleshooting which vhost file is chosen
    <IfModule mod_headers.c>
        Header add X-Vhost "publish-example-com"
    </IfModule>
  ...
</VirtualHost>
```

* `conf.d/enabled_vhosts/<CUSTOMER_CHOICE>.vhost`

Deze map bevat relatieve symbolische koppelingen naar bestanden onder conf.dispatcher.d/available_hosts.

Voorbeeldopdrachten vereist om deze symbolische koppelingen te maken:

Apple macOS, Linux en WSL

```
ln -s ../available_vhosts/wknd.vhost wknd.vhost
```

Microsoft Windows

```
mklink wknd.vhost ..\available_vhosts\wknd.vhost
```

>[!NOTE]
>
> Wanneer het werken met symbolische verbindingen onder Vensters, zou u in een opgeheven bevelherinnering, in het Subsysteem van Vensters voor Linux moeten lopen of [ hebben creeer symbolische toegewezen verbindingen ](https://learn.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/create-symbolic-links) voorrecht.

* `conf.d/rewrites/rewrite.rules`

Het bestand wordt opgenomen vanuit uw `.vhost` -bestanden. Deze heeft een set herschrijfregels voor `mod_rewrite` .

* `conf.d/variables/custom.vars`

Het bestand wordt opgenomen vanuit uw `.vhost` -bestanden. U kunt op deze locatie definities voor Apache-variabelen toevoegen.

* `conf.d/variables/global.vars`

Het bestand wordt opgenomen vanuit het `dispatcher_vhost.conf` -bestand. U kunt uw Dispatcher wijzigen en het logniveau in dit bestand herschrijven.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

U kunt één of meerdere van deze dossiers hebben, en zij bevatten landbouwbedrijven om gastheernamen aan te passen en de module van Dispatcher toe te staan om elk landbouwbedrijf met verschillende regels te behandelen. Bestanden worden gemaakt in de map `available_farms` en ingeschakeld met een symbolische koppeling in de map `enabled_farms` . Van de `.farm` dossiers, zijn andere dossiers zoals filters, geheim voorgeheugenregels, en anderen inbegrepen.

* `conf.dispatcher.d/enabled_farms/<CUSTOMER_CHOICE>.farm`

Deze map bevat relatieve symbolische koppelingen naar bestanden onder conf.dispatcher.d/available_farm.

Voorbeeldopdrachten vereist om deze symbolische koppelingen te maken:

Apple macOS, Linux en WSL

```
ln -s ../available_farms/wknd.farm wknd.farm
```

Microsoft Windows

```
mklink wknd.farm ..\available_farms\wknd.farm
```

>[!NOTE]
>
> Wanneer het werken met symbolische verbindingen onder Vensters, zou u in een opgeheven bevelherinnering, in het Subsysteem van Vensters voor Linux moeten lopen of [ hebben creeer symbolische toegewezen verbindingen ](https://learn.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/create-symbolic-links) voorrecht.

* `conf.dispatcher.d/cache/rules.any`

Het bestand wordt opgenomen vanuit uw `.farm` -bestanden. Hiermee geeft u voorkeuren voor het in cache plaatsen op.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

Het bestand wordt opgenomen vanuit uw `.farm` -bestanden. Het specificeert welke verzoekkopballen aan het achtereind door:sturen.

* `conf.dispatcher.d/filters/filters.any`

Het bestand wordt opgenomen vanuit uw `.farm` -bestanden. Het heeft een reeks regels die veranderen welk verkeer uit zou moeten worden gefiltreerd en niet het aan het achterste eind maken.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

Het bestand wordt opgenomen vanuit uw `.farm` -bestanden. Het heeft een lijst van gastheernamen of de wegen van URI die door glob aanpassing moeten worden aangepast. Deze overeenkomst bepaalt welke achtergrond om een verzoek te dienen.

* `opt-in/USE_SOURCES_DIRECTLY`

Dit bestand maakt een flexibelere Dispatcher-configuratie mogelijk en verwijdert eerdere beperkingen met betrekking tot het aantal en de grootte van bestanden. De SDK en de runtime zorgen er ook voor dat de configuratie op een verbeterde manier wordt gevalideerd en geïmplementeerd.

De bovenstaande bestanden verwijzen naar de onderstaande onveranderlijke configuratiebestanden. Wijzigingen in de onveranderbare bestanden worden niet verwerkt door Dispatchers in Cloud-omgevingen.

**Immuable Dossiers van de Configuratie**

Deze bestanden maken deel uit van het basiskader en zorgen ervoor dat standaarden en beste praktijken worden nageleefd. De bestanden worden als onveranderlijk beschouwd, omdat het wijzigen of verwijderen ervan lokaal geen invloed heeft op uw implementatie, omdat ze niet worden overgebracht naar uw Cloud-instantie.

Het wordt aanbevolen dat de bovenstaande bestanden verwijzen naar de hieronder vermelde onveranderlijke bestanden, gevolgd door aanvullende instructies of overschrijvingen. Wanneer de configuratie van Dispatcher aan een wolkenmilieu wordt opgesteld, wordt de recentste versie van de onveranderlijke dossiers gebruikt, ongeacht welke versie in lokale ontwikkeling werd gebruikt.

* `conf.d/available_vhosts/default.vhost`

Bevat een virtuele voorbeeldhost. Voor uw eigen virtuele host maakt u een kopie van dit bestand, past u het aan, gaat u naar `conf.d/enabled_vhosts` en maakt u een symbolische koppeling naar uw aangepaste kopie.
Kopieer het bestand default.vhost niet rechtstreeks naar `conf.d/enabled_vhosts` .

Zorg ervoor dat er altijd een virtuele host beschikbaar is die overeenkomt met ServerAlias `\*.local` , `localhost` en `127.0.0.1` die nodig zijn voor de Dispatcher-validatie. De serveraliassen `*.adobeaemcloud.net` en `*.adobeaemcloud.com` zijn nodig voor interne Adobe processen.

* `conf.d/dispatcher_vhost.conf`

Deel van het basisframework dat wordt gebruikt om te illustreren hoe uw virtuele hosts en globale variabelen worden opgenomen.

* `conf.d/rewrites/default_rewrite.rules`

Herschrijf regels die gebrek zijn zijn geschikt voor een standaardproject. Wijzig `rewrite.rules` als u aanpassingen nodig hebt. In uw aanpassing, kunt u nog de standaardregels eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/available_farms/default.farm`

Bevat een voorbeeld van een Dispatcher-farm. Voor uw eigen landbouwbedrijf, creeer een exemplaar van dit dossier, pas het aan, ga naar `conf.d/enabled_farms` en creeer een symbolische verbinding aan uw aangepaste exemplaar.

* `conf.dispatcher.d/cache/default_invalidate.any`

Een deel van het basiskader, wordt geproduceerd bij opstarten. U wordt **vereist** om dit dossier in elk landbouwbedrijf te omvatten u, in de `cache/allowedClients` sectie bepaalt.

* `conf.dispatcher.d/cache/default_rules.any`

De standaard geheim voorgeheugenregels geschikt voor een standaardproject. Wijzig `conf.dispatcher.d/cache/rules.any` als u aanpassingen nodig hebt. In uw aanpassing, kunt u nog de standaardregels eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/clientheaders/default_clientheaders.any`

De standaard verzoekkopballen om aan het achterste deel door:sturen, geschikt voor een standaardproject. Wijzig `clientheaders.any` als u aanpassingen nodig hebt. In uw aanpassing, kunt u nog de standaardverzoekkopballen eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/dispatcher.any`

Deel van basisframework, gebruikt om te illustreren hoe je Dispatcher-boerderijen worden opgenomen.

* `conf.dispatcher.d/filters/default_filters.any`

Standaardfilters die geschikt zijn voor een standaardproject. Wijzig `filters.any` als u aanpassingen nodig hebt. In uw aanpassing, kunt u nog de standaardfilters eerst omvatten, als zij uw behoeften aanpassen.

* `conf.dispatcher.d/renders/default_renders.any`

Als onderdeel van het basisframework wordt dit bestand bij het opstarten gegenereerd. U wordt **vereist** om dit dossier in elk landbouwbedrijf te omvatten u, in de `renders` sectie bepaalt.

* `conf.dispatcher.d/virtualhosts/default_virtualhosts.any`

Standaardhostglobing geschikt voor een standaardproject. Wijzig `virtualhosts.any` als u aanpassingen nodig hebt. In uw aanpassing, zou u niet het standaard gastheer globbing moeten omvatten, aangezien het **elk** inkomend verzoek aanpast.

## Ondersteunde Apache-modules {#apache-modules}

Zie [ Ondersteunde modules Apache ](/help/implementing/dispatcher/disp-overview.md#supported-directives).

## Lokale validatie {#local-validation-flexible-mode}

>[!NOTE]
>
>De onderstaande secties bevatten opdrachten die gebruikmaken van de Mac- of Linux®-versies van de SDK, maar de Windows SDK kan ook op dezelfde manier worden gebruikt.

Gebruik het script `validate.sh` zoals hieronder wordt getoond:

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
2. De methode voert de opdracht `httpd -t` uit om te testen of de syntaxis correct is, zodat Apache httpd kan starten. Indien succesvol, zou de configuratie voor plaatsing klaar moeten zijn.
3. Controleert dat de ondergroep van de de configuratiedossiers van SDK van Dispatcher, die om zoals beschreven in de [ de structuursectie van het Dossier ](##flexible-mode-file-structure) moeten zijn onveranderlijk zijn, niet is gewijzigd en de huidige versie van SDK aanpast.

Tijdens een Cloud Manager-implementatie wordt de syntaxiscontrole van `httpd -t` ook uitgevoerd en worden eventuele fouten opgenomen in het Cloud Manager `Build Images step failure` -logboek.

>[!NOTE]
>
>Zie [ Automatisch het herladen en bevestiging ](#automatic-loading) sectie voor een efficiënt alternatief aan het lopen `validate.sh` na elke configuratiewijziging.

### Fase 1 {#first-phase}

Als een instructie niet is gevoegd op lijst van gewenste personen, wordt een fout geregistreerd en wordt een afsluitcode van niet nul geretourneerd. Bovendien worden alle bestanden met patroon `conf.dispatcher.d/enabled_farms/*.farm` gescand en wordt gecontroleerd of:

* Geen filterregel bestaat die het gebruik via `/glob` toestaat (zie [ CVE-2016-0957 ](https://nvd.nist.gov/vuln/detail/CVE-2016-0957)) voor meer details.
* Er wordt geen beheerfunctie weergegeven. Bijvoorbeeld toegang tot paden zoals `/crx/de or /system/console` .

Het validatiehulpmiddel rapporteert alleen het verboden gebruik van Apache-instructies die niet zijn gevoegd op lijst van gewenste personen. Er worden geen syntactische of semantische problemen gerapporteerd met uw Apache-configuratie, aangezien deze informatie alleen beschikbaar is voor Apache-modules in een actieve omgeving.

Hieronder vindt u technieken voor het oplossen van problemen waarmee algemene validatiefouten kunnen worden opgespoord die door het programma worden uitgevoerd:

**Onbekwaam om van a `conf.dispatcher.d` subfolder in het archief** de plaats te bepalen

Uw archief moet mappen `conf.d` en `conf.dispatcher.d` bevatten. Let op: gebruik het voorvoegsel `etc/httpd` **niet** in uw archief.

**Kon geen landbouwbedrijf in`conf.dispatcher.d/enabled_farms`** vinden

Uw ingeschakelde landbouwbedrijven zouden in bovengenoemde subfolder moeten zijn.

**inbegrepen Dossier (...) moet worden genoemd: ...**

Er zijn twee secties in uw landbouwbedrijfconfiguratie die **&#x200B;**&#x200B;moet omvatten
specifiek bestand: `/renders` en `/allowedClients` in de sectie `/cache` . Die
de secties moeten er als volgt uitzien:

```
/renders {
    $include "../renders/default_renders.any"
}
```

En:

```
/allowedClients {
    $include "../cache/default_invalidate.any"
}
```

**Dossier inbegrepen bij onbekende plaats: ...**

Er zijn vier secties in uw landbouwbedrijfconfiguratie waar u uw eigen dossiers kunt omvatten: `/clientheaders`, `filters`, `/rules` in `/cache` sectie en `/virtualhosts`. De namen van de opgenomen bestanden moeten als volgt luiden:

| Sectie | Bestandsnaam opnemen |
|------------------|--------------------------------------|
| `/clientheaders` | `../clientheaders/clientheaders.any` |
| `/filters` | `../filters/filters.any` |
| `/rules` | `../cache/rules.any` |
| `/virtualhosts` | `../virtualhosts/virtualhosts.any` |

Alternatief, kunt u de **standaard** versie van die dossiers omvatten, de waarvan namen met het woord `default_` worden voorafgegaan, bijvoorbeeld, `../filters/default_filters.any`.

**omvat verklaring bij (...), buiten om het even welke bekende plaats: ...**

Behalve de zes secties die in de bovenstaande paragrafen worden vermeld, bent u niet toegestaan
Als u bijvoorbeeld de instructie `$include` wilt gebruiken, wordt deze fout gegenereerd:

```
/invalidate {
    $include "../cache/invalidate.any"
}
```

**Toegestane cliënten/renders zijn niet inbegrepen van: ...**

Deze fout wordt gegenereerd wanneer u geen include-bestand voor `/renders` en `/allowedClients` opgeeft in de sectie `/cache` . Zie de
**inbegrepen dossier (...) moet worden genoemd: ...** sectie voor meer informatie.

**de Filter moet geen globpatroon gebruiken om verzoeken** toe te staan

Het is niet veilig om verzoeken met een `/glob` stijlregel toe te staan, die met de volledige verzoeklijn, bijvoorbeeld, wordt aangepast

```
/0100 {
    /type "allow" /glob "GET *.css *"
}
```

Deze verklaring wordt bedoeld om verzoeken voor `css` dossiers toe te staan, maar het staat ook verzoeken **toe om het even welk** middel dat door het vraagkoord `?a=.css` wordt gevolgd. Het is daarom verboden dergelijke filters te gebruiken (zie ook CVE-2016-0957).

**Opgenomen dossier (...) past geen bekend dossier** aan

Standaard kunnen twee typen bestanden in uw virtuele Apache-hostconfiguratie worden opgegeven als include-bestanden: herschreven en variabelen.

| Type | Bestandsnaam opnemen |
|-----------|---------------------------------|
| Herschrijven | `conf.d/rewrites/rewrite.rules` |
| Variabelen | `conf.d/variables/custom.vars` |

In de flexibele modus kunnen ook andere bestanden worden opgenomen, mits deze zich in submappen (op elk niveau) van de map `conf.d` bevinden, die als volgt vooraf is ingesteld.

| Voorvoegsel van bovenste map van bestand opnemen |
|-------------------------------------|
| `conf.d/includes` |
| `conf.d/modsec` |
| `conf.d/rewrites` |

U kunt bijvoorbeeld als volgt een bestand in een gemaakte map opnemen onder de map `conf.d/includes` :

```
Include conf.d/includes/mynewdirectory/myincludefile.conf
```

Alternatief, kunt u de **standaard** versie van omvatten herschrijft regels, de waarvan naam `conf.d/rewrites/default_rewrite.rules` is.
Er is geen standaardversie van de variabelebestanden.

**Vervangen configuratielay-out ontdekt, toelatend verenigbaarheidswijze**

Dit bericht wijst erop dat uw configuratie verouderde versie 1 lay-out heeft, die een volledige bevat
Apache-configuratie en bestanden met `ams_` voorvoegsels. Terwijl deze configuratie nog steeds voor achteruit wordt ondersteund
moet u overschakelen naar de nieuwe indeling.

De eerste fase kan ook **afzonderlijk** in werking worden gesteld, eerder dan van het omslag `validate.sh` manuscript.

Wanneer dit wordt uitgevoerd tegen uw vastgelegde artefact of de submap `dispatcher/src` , worden validatiefouten gerapporteerd:

```
$ validator full -relaxed dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-allowlisted directives:
  conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
  conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

In Windows is de Dispatcher-validator hoofdlettergevoelig. Als dusdanig, kan het er niet in slagen om de configuratie te bevestigen als u niet de kapitalisatie van de weg respecteert waar uw configuratie, bijvoorbeeld verblijft:

```
bin\validator.exe -relaxed full src
Cloud manager validator 2.0.xx
2021/03/15 18:15:40 Dispatcher configuration validation failed:
  conf.dispatcher.d\available_farms\default.farm:15: parent directory outside server root: c:\k\a\aem-dispatcher-sdk-windows-symlinks-testing3\dispatcher\src
```

Vermijd deze fout door de weg van de Ontdekkingsreiziger van Vensters en dan op de bevelherinnering te kopiëren en te kleven gebruikend een `cd` bevel in die weg.

### Fase 2 {#second-phase}

Deze fase controleert de Apache syntaxis door Apache HTTPD in een docker container te beginnen. Docker moet lokaal zijn geïnstalleerd, maar AEM hoeft niet te worden uitgevoerd.

>[!NOTE]
>
>Windows-gebruikers moeten Windows 10 Professional of andere distributies gebruiken die Docker ondersteunen. Deze vereiste is een vereiste voor het uitvoeren en opsporen van fouten in Dispatcher op een lokale computer.
>Voor zowel Windows als macOS raadt Adobe u aan Docker Desktop te gebruiken.

Deze fase kan ook onafhankelijk door `bin/docker_run.sh src/dispatcher host.docker.internal:4503 8080` worden uitgevoerd.

Tijdens een Cloud Manager-implementatie wordt de syntaxiscontrole van `httpd -t` ook uitgevoerd en worden eventuele fouten opgenomen in het foutenlogboek van de stap Cloud Manager Build Images.

### Fase 3 {#third-phase}

Als er in deze fase een fout optreedt, houdt dit in dat de Adobe een of meer onveranderlijke bestanden heeft gewijzigd. In dat geval moet u de overeenkomstige onveranderlijke bestanden vervangen door de nieuwe versie die wordt geleverd in de map `src` van de SDK. In het onderstaande logboekvoorbeeld wordt dit probleem geïllustreerd:

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

Deze fase kan ook onafhankelijk door `bin/docker_immutability_check.sh src/dispatcher` worden uitgevoerd.

Uw lokale, onveranderlijke bestanden kunnen worden bijgewerkt door het script `bin/update_maven.sh src/dispatcher` uit te voeren in uw Dispatcher-map, waar `src/dispatcher` de configuratiemap van Dispatcher is. Met dit script wordt ook elk `pom.xml` -bestand in de bovenliggende map bijgewerkt, zodat de ingestelde controles op de imutabiliteit ook worden bijgewerkt.

## Fouten opsporen in uw Apache- en Dispatcher-configuratie {#debugging-apache-and-dispatcher-configuration}

U kunt Apache Dispatcher lokaal uitvoeren met `./bin/docker_run.sh src/dispatcher docker.for.mac.localhost:4503 8080` .

Zoals eerder vermeld, moet Docker plaatselijk worden geïnstalleerd en het is niet noodzakelijk voor AEM in werking te stellen. Windows-gebruikers moeten Windows 10 Professional of andere distributies gebruiken die Docker ondersteunen. Deze vereiste is een vereiste voor het uitvoeren en opsporen van fouten in Dispatcher op een lokale computer.

De volgende strategie kan worden gebruikt om de logoutput voor de module van Dispatcher te verhogen en de resultaten van de `RewriteRule` evaluatie in zowel lokale als wolkenmilieu&#39;s te zien.

Logniveaus voor deze modules worden gedefinieerd door de variabelen `DISP_LOG_LEVEL` en `REWRITE_LOG_LEVEL` . Deze kunnen worden ingesteld in het bestand `conf.d/variables/global.vars` . Het relevante deel is als volgt:

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

Wanneer Dispatcher lokaal wordt uitgevoerd, worden logbestanden rechtstreeks naar de einduitvoer afgedrukt. Meestal, wilt u deze logboeken in DEBUG zijn, die kan worden gedaan door het Debug niveau als parameter over te gaan wanneer het runnen van Docker. Bijvoorbeeld: `DISP_LOG_LEVEL=Debug ./bin/docker_run.sh src docker.for.mac.localhost:4503 8080` .

Logbestanden voor cloudomgevingen worden weergegeven via de logbestandsservice die beschikbaar is in Cloud Manager.

>[!NOTE]
>
>Voor omgevingen op AEM as a Cloud Service is foutopsporing het maximale breedtepunt. Het niveau van het spoorlogboek wordt niet gesteund zodat zou u moeten vermijden plaatsend het wanneer het werken in wolkenmilieu&#39;s.

### Automatisch opnieuw laden en valideren {#automatic-reloading}

>[!NOTE]
>
>Vanwege een beperking van het Windows-besturingssysteem is deze functie alleen beschikbaar voor macOS- en Linux®-gebruikers.

In plaats van lokale bevestiging (`validate.sh`) in werking te stellen en de dockercontainer (`docker_run.sh`) te beginnen telkens als de configuratie wordt gewijzigd, kunt u het `docker_run_hot_reload.sh` manuscript Alternatief in werking stellen. Het script controleert op wijzigingen in de configuratie en laadt deze automatisch opnieuw en start de validatie opnieuw. Met deze optie kunt u veel tijd besparen tijdens het opsporen van fouten.

U kunt het script uitvoeren met de volgende opdracht: `./bin/docker_run_hot_reload.sh src/dispatcher host.docker.internal:4503 8080`

De eerste regels uitvoer zien er ongeveer hetzelfde uit als wat er zou worden uitgevoerd voor `docker_run.sh` . Bijvoorbeeld:

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

### Aangepaste omgevingsvariabelen inspringen {#environment-variables}

Aangepaste omgevingsvariabelen kunnen worden gebruikt met de verzender SDK door deze in een afzonderlijk bestand in te stellen en ernaar te verwijzen in de `ENV_FILE` -omgevingsvariabele voordat de lokale verzender wordt gestart.

Een bestand met aangepaste omgevingsvariabelen ziet er als volgt uit:

```
COMMERCE_ENDPOINT=commerce-host
AEM_HTTP_PROXY_HOST=host.docker.internal
AEM_HTTP_PROXY_PORT=8000
```

En het kan in lokale verzender SDK met de volgende bevelen worden gebruikt:

```
export ENV_FILE=custom.env
./bin/docker_run.sh src/dispatcher docker.for.mac.localhost:4503 8080
```

## Verschillende Dispatcher-configuraties per omgeving {#different-dispatcher-configurations-per-environment}

Momenteel wordt dezelfde Dispatcher-configuratie toegepast op alle omgevingen in AEM as a Cloud Service. De runtime heeft een omgevingsvariabele `ENVIRONMENT_TYPE` die de huidige uitvoermodus (ontwikkeling, werkgebied of productie) en een definitie bevat. De waarde &quot;define&quot; kan `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE` of `ENVIRONMENT_PROD` zijn. In de Apache-configuratie kan de variabele rechtstreeks in een expressie worden gebruikt. U kunt ook &#39;define&#39; gebruiken om logica op te bouwen:

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

U kunt ook Cloud Manager-omgevingsvariabelen gebruiken in uw httpd/dispatcher-configuratie, maar geen omgevingsgeheimen. Deze methode is vooral belangrijk als een programma meerdere ontwikkelomgevingen heeft en sommige van deze ontwikkelomgevingen verschillende waarden hebben voor de httpd/dispatcherconfiguratie. De zelfde $ {VIRTUALHOST} syntaxis zou worden gebruikt zoals in het voorbeeld hierboven, nochtans zou Define verklaringen in het bovengenoemde variabelendossier niet worden gebruikt. Lees de [ documentatie van Cloud Manager ](/help/implementing/cloud-manager/environment-variables.md) voor instructies bij het vormen van de milieuvariabelen van Cloud Manager.

Wanneer u uw configuratie lokaal test, kunt u verschillende omgevingstypen simuleren door de variabele `DISP_RUN_MODE` rechtstreeks door te geven aan het `docker_run.sh` -script:

```
$ DISP_RUN_MODE=stage docker_run.sh src docker.for.mac.localhost:4503 8080
```

De standaardlooppaswijze wanneer niet het overgaan in een waarde voor DISP_RUN_MODE is &quot;dev&quot;.
Voer het script `docker_run.sh` zonder argumenten uit voor een volledige lijst met beschikbare opties en variabelen.

## De Dispatcher-configuratie bekijken die door uw Docker-container wordt gebruikt {#viewing-dispatcher-configuration-in-use-by-docker-container}

Met milieu-specifieke configuraties, kan het moeilijk zijn om te bepalen hoe de daadwerkelijke configuratie van Dispatcher eruit ziet. Nadat u de dockercontainer met `docker_run.sh` hebt gestart, kan deze als volgt worden gedumpt:

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

Met de versie van Cloud Manager 2021.7.0, produceren de nieuwe programma&#39;s van Cloud Manager gemodelleerde projectstructuren met [ AEM archetype 28 ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=nl-NL) of hoger, die het dossier **opt-in/USE_SOURCES_DIRECTLY** omvat. Het verwijdert vorige beperkingen van de [ erfeniswijze ](/help/implementing/dispatcher/validation-debug-legacy.md) rond het aantal en de grootte van dossiers, ook veroorzakend SDK en runtime om de configuratie op een betere manier te bevestigen en op te stellen. Als dit bestand niet beschikbaar is in uw Dispatcher-configuratie, wordt u ten zeerste aangeraden te migreren. Gebruik de volgende stappen om een veilige overgang te garanderen:

1. **Lokale het testen.** Voeg de map en het bestand toe met de meest recente SDK voor Dispatcher-gereedschappen `opt-in/USE_SOURCES_DIRECTLY` . Volg de instructies voor lokale validatie in dit artikel, zodat u kunt testen of de Dispatcher lokaal werkt.
1. **het ontwikkelingstests van de Wolk:**
   * Leg het bestand `opt-in/USE_SOURCES_DIRECTLY` vast aan een git-vertakking die wordt geïmplementeerd door de niet-productiepijpleiding naar een Cloud-ontwikkelomgeving.
   * Gebruik Cloud Manager om te implementeren in een Cloud-ontwikkelomgeving.
   * Test grondig. Het is van essentieel belang om te controleren of uw Apache- en Dispatcher-configuratie zich gedraagt zoals u verwacht voordat u wijzigingen in hogere omgevingen implementeert. Controleer al gedrag met betrekking tot uw douaneconfiguratie. Bestand een ticket voor klantenondersteuning als u denkt dat de configuratie van de geïmplementeerde Dispatcher uw aangepaste configuratie niet weerspiegelt.

   >[!NOTE]
   >
   >In de flexibele modus moet u relatieve paden gebruiken in plaats van absolute paden.
1. **opstellen aan productie:**
   * Leg het bestand `opt-in/USE_SOURCES_DIRECTLY` vast op een git-vertakking die wordt geïmplementeerd door de productiepijpleiding naar het werkgebied en de productieomgeving van de cloud.
   * Gebruik Cloud Manager om te implementeren in testfasen.
   * Test grondig. Het is van essentieel belang om te controleren of uw Apache- en Dispatcher-configuratie zich gedraagt zoals u verwacht voordat u wijzigingen in hogere omgevingen implementeert. Controleer al gedrag met betrekking tot uw douaneconfiguratie. Bestand een ticket voor klantenondersteuning als u denkt dat de configuratie van de geïmplementeerde Dispatcher uw aangepaste configuratie niet weerspiegelt.
   * Gebruik Cloud Manager om de implementatie naar productie voort te zetten.
