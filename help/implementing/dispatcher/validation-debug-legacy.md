---
title: Validatie en foutopsporing met Dispatcher Tools (verouderd)
description: Validatie en foutopsporing met Dispatcher Tools (verouderd)
feature: Dispatcher
hidefromtoc: true
exl-id: dc04d035-f002-42ef-9c2e-77602910c2ec
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '2337'
ht-degree: 0%

---

# Validatie en foutopsporing met Dispatcher Tools (verouderd)  {#Dispatcher-tools-legacy}

## Inleiding {#apache-and-dispatcher-configuration-and-testing}

>[!NOTE]
>Voor meer informatie over Dispatcher in de Wolk en hoe te om de Hulpmiddelen van Dispatcher te downloaden zie [ Dispatcher in de Cloud ](/help/implementing/dispatcher/disp-overview.md) pagina.

De volgende secties beschrijven de structuur van het dossier van de erfeniswijze, lokale bevestiging, het zuiveren en hoe te van de erfeniswijze aan de [ flexibele wijze ](/help/implementing/dispatcher/validation-debug.md) migreren.

In dit artikel wordt ervan uitgegaan dat de Dispatcher-configuratie van uw project niet de bestandsindeling opt-in/USE_SOURCES_DIRECTLY bevat. Hierdoor zijn er beperkingen met betrekking tot het aantal en de grootte van bestanden, zoals:

* één herschrijfbestand dat moet worden gebruikt in plaats van bestanden die specifiek zijn voor de site.
* de som van de inhoud van de aanpasbare bestanden moet kleiner zijn dan 1 MB.

Vanaf de Cloud Manager 2021.7.0-release genereren nieuwe Cloud Manager-programma&#39;s gefabriceerde projectstructuren met AEM archetype 28 en hoger, waaronder het eerder genoemde bestand.

Het wordt **hoogst geadviseerd** dat u van erfeniswijze aan flexibele wijze zoals geschetst in de migratiesectie [ migrerend van erfeniswijze aan flexibele wijze ](#migrating-flexible) migreert. Het gebruik van de flexibele modus zorgt er ook voor dat de SDK en de runtime de configuratie op een verbeterde manier valideren en implementeren.

## Bestandsstructuur {#legacy-mode-file-structure}

De structuur van de submap Dispatcher van het project (in de verouderde modus) is als volgt:

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
    │   ├── marketing_query_parameters.any
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

**Aanpasbare Dossiers**

De volgende bestanden kunnen worden aangepast en worden tijdens de implementatie overgebracht naar uw Cloud-instantie:

* `conf.d/available_vhosts/<CUSTOMER_CHOICE>.vhost`

U kunt een of meer van deze bestanden hebben. Ze bevatten `<VirtualHost>` -items die overeenkomen met hostnamen en staan Apache toe elk domeinverkeer met verschillende regels af te handelen. Bestanden worden gemaakt in de map `available_vhosts` en ingeschakeld met een symbolische koppeling in de map `enabled_vhosts` . Van de `.vhost` dossiers, zijn andere dossiers, zoals herschrijft en variabelen, inbegrepen.

* `conf.d/rewrites/rewrite.rules`

Dit bestand wordt opgenomen vanuit uw `.vhost` -bestanden. Deze heeft een set herschrijfregels voor `mod_rewrite` .

>[!NOTE]
>
>Momenteel moet één herschrijfbestand worden gebruikt in plaats van bestanden die specifiek zijn voor de site. In de regel moet de som van de inhoud van de aanpasbare bestanden kleiner zijn dan 1 MB.

* `conf.d/variables/custom.vars`

Dit bestand wordt opgenomen vanuit uw `.vhost` -bestanden. U kunt op deze locatie definities voor Apache-variabelen toevoegen.

* `conf.d/variables/global.vars`

Dit bestand wordt opgenomen vanuit het `dispatcher_vhost.conf` -bestand. U kunt uw Dispatcher wijzigen en het logniveau in dit bestand herschrijven.

* `conf.dispatcher.d/available_farms/<CUSTOMER_CHOICE>.farm`

U kunt één of meerdere van deze dossiers hebben, en zij bevatten landbouwbedrijven om gastheernamen aan te passen en de module van Dispatcher toe te staan om elk landbouwbedrijf met verschillende regels te behandelen. Bestanden worden gemaakt in de map `available_farms` en ingeschakeld met een symbolische koppeling in de map `enabled_farms` . Van de `.farm` dossiers, zijn andere dossiers zoals filters, geheim voorgeheugenregels, en anderen, inbegrepen.

* `conf.dispatcher.d/cache/rules.any`

Dit bestand wordt opgenomen vanuit uw `.farm` -bestanden. Hiermee geeft u voorkeuren voor het in cache plaatsen op.

* `conf.dispatcher.d/clientheaders/clientheaders.any`

Dit bestand wordt opgenomen vanuit uw `.farm` -bestanden. Het specificeert welke verzoekkopballen aan het achtereind door:sturen.

* `conf.dispatcher.d/filters/filters.any`

Dit bestand wordt opgenomen vanuit uw `.farm` -bestanden. Het heeft een reeks regels die veranderen welk verkeer uit zou moeten worden gefiltreerd en niet het aan het achterste eind maken.

* `conf.dispatcher.d/virtualhosts/virtualhosts.any`

Dit bestand wordt opgenomen vanuit uw `.farm` -bestanden. Het heeft een lijst van gastheernamen of de wegen van URI die door glob aanpassing moeten worden aangepast. Deze overeenkomst bepaalt welke achtergrond om een verzoek te dienen.

De bovenstaande bestanden verwijzen naar de onderstaande onveranderlijke configuratiebestanden. Wijzigingen in de onveranderbare bestanden worden niet verwerkt door Dispatchers in Cloud-omgevingen.

**Immuable Dossiers van de Configuratie**

Deze bestanden maken deel uit van het basiskader en zorgen ervoor dat standaarden en beste praktijken worden nageleefd. De bestanden worden als onveranderlijk beschouwd, omdat het wijzigen of verwijderen ervan lokaal geen invloed heeft op uw implementatie, omdat ze niet worden overgebracht naar uw Cloud-instantie.

Het wordt aanbevolen dat de bovenstaande bestanden verwijzen naar de hieronder vermelde onveranderlijke bestanden, gevolgd door aanvullende instructies of overschrijvingen. Wanneer de configuratie van Dispatcher aan een wolkenmilieu wordt opgesteld, wordt de recentste versie van de onveranderlijke dossiers gebruikt, ongeacht welke versie in lokale ontwikkeling werd gebruikt.

* `conf.d/available_vhosts/default.vhost`

Bevat een virtuele voorbeeldhost. Voor uw eigen virtuele host maakt u een kopie van dit bestand, past u het aan, gaat u naar `conf.d/enabled_vhosts` en maakt u een symbolische koppeling naar uw aangepaste kopie.

* `conf.d/dispatcher_vhost.conf`

Deel van het basisframework dat wordt gebruikt om te illustreren hoe uw virtuele hosts en globale variabelen worden opgenomen.

* `conf.d/rewrites/default_rewrite.rules`

Standaardregels voor herschrijven die geschikt zijn voor een standaardproject. Bewerk `rewrite.rules` als u aanpassingen nodig hebt. In uw aanpassing, kunt u nog de standaardregels eerst omvatten, als zij uw behoeften aanpassen.

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

## Lokale validatie {#local-validation-legacy-mode}

>[!NOTE]
>De onderstaande secties bevatten opdrachten die gebruikmaken van de Mac- of Linux®-versies van de SDK, maar de Windows SDK kan ook op dezelfde manier worden gebruikt.

Gebruik het script `validate.sh` zoals hieronder wordt getoond:

```
$ validate.sh src/dispatcher
Phase 1: Dispatcher validator
Cloud manager validator 2.0.32
Phase 1 finished
Phase 2: httpd -t validation in docker image
values.csv found in deployment folder: /tmp/dispatcher_validation_1625150390 - using files listed there
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

Het script doet het volgende:

1. De validator wordt uitgevoerd. Als de configuratie ongeldig is, ontbreekt het manuscript.
2. De methode voert de opdracht `httpd -t` uit om te testen of de syntaxis correct is, zodat Apache httpd kan starten. Indien succesvol, zou de configuratie voor plaatsing klaar moeten zijn.
3. Controleert dat de ondergroep van de de configuratiedossiers van SDK van Dispatcher, die om zoals beschreven in de [ de structuursectie van het Dossier ](##legacy-mode-file-structure) moeten zijn onveranderlijk, niet is uitgegeven. Deze controle is nieuw en is geïntroduceerd met AEM SDK-versie 2021.1.4738 die ook Dispatcher Tools versie 2.0.36 bevat. Vóór deze update hebben klanten mogelijk ten onrechte aangenomen dat eventuele lokale SDK-wijzigingen van die onveranderlijke bestanden ook worden toegepast op de cloud-omgeving.

Tijdens een Cloud Manager-implementatie wordt de syntaxiscontrole van `httpd -t` ook uitgevoerd en worden eventuele fouten opgenomen in het Cloud Manager `Build Images step failure` -logboek.

### Fase 1 {#first-phase}

Als een instructie niet is gevoegd op lijst van gewenste personen, wordt een fout geregistreerd en wordt een afsluitcode van niet nul geretourneerd. Bovendien worden alle bestanden met patroon `conf.dispatcher.d/enabled_farms/*.farm` gescand en wordt gecontroleerd of:

* Geen filterregel bestaat die het gebruik via `/glob` toestaat (zie [ CVE-2016-0957 ](https://nvd.nist.gov/vuln/detail/CVE-2016-0957) voor meer details.
* Er wordt geen beheerfunctie weergegeven. Bijvoorbeeld toegang tot paden zoals `/crx/de or /system/console` .

Het validatiehulpmiddel rapporteert alleen het verboden gebruik van Apache-instructies die niet zijn gevoegd op lijst van gewenste personen. Er worden geen syntactische of semantische problemen gerapporteerd met uw Apache-configuratie, aangezien deze informatie alleen beschikbaar is voor Apache-modules in een actieve omgeving.

Hieronder vindt u technieken voor het oplossen van problemen waarmee algemene validatiefouten kunnen worden opgespoord die door het programma worden uitgevoerd:

**Onbekwaam om van a `conf.dispatcher.d` subfolder in het archief** de plaats te bepalen

Uw archief moet mappen `conf.d` en `conf.dispatcher.d` bevatten. Let op: gebruik het voorvoegsel `etc/httpd` **niet** in uw archief.

**Kon geen landbouwbedrijf in`conf.dispatcher.d/enabled_farms`** vinden

Uw ingeschakelde landbouwbedrijven zouden in bovengenoemde subfolder moeten zijn.

**inbegrepen Dossier (...) moet worden genoemd: ...**

Er zijn twee secties in uw landbouwbedrijfconfiguratie die **** moet omvatten
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

Er zijn vier secties in uw landbouwbedrijfconfiguratie waar u uw eigen dossier kunt omvatten: `/clientheaders`, `filters`, `/rules` in `/cache` sectie en `/virtualhosts`. De namen van de opgenomen bestanden moeten als volgt luiden:

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

Uw virtuele Apache-hostconfiguratie bevat twee typen bestanden die u kunt opgeven als include-bestanden: herschrijft en variabelen.
De namen van de opgenomen bestanden moeten als volgt luiden:

| Type | Bestandsnaam opnemen |
|-----------|---------------------------------|
| Herschrijven | `conf.d/rewrites/rewrite.rules` |
| Variabelen | `conf.d/variables/custom.vars` |

>[!TIP]
>
>Als u meer bestanden op een veel minder beperkte manier wilt opnemen, kunt u overschakelen naar de flexibele Dispatcher-configuratiemodus. Zie [ Valideren en het Zuiveren gebruikend de Hulpmiddelen van Dispatcher ](/help/implementing/dispatcher/validation-debug.md) voor meer details op flexibele wijze.

Alternatief, kunt u de **standaard** versie van omvatten herschrijft regels, de waarvan naam `conf.d/rewrites/default_rewrite.rules` is.
Er is geen standaardversie van de variabelebestanden.

**Vervangen configuratielay-out ontdekt, toelatend verenigbaarheidswijze**

Dit bericht wijst erop dat uw configuratie verouderde versie 1 lay-out heeft, die een volledige bevat
Apache-configuratie en bestanden met `ams_` voorvoegsels. Terwijl deze configuratie nog steeds voor achteruit wordt ondersteund
moet u overschakelen naar de nieuwe indeling.

De eerste fase kan ook **afzonderlijk** in werking worden gesteld, eerder dan van het omslag `validate.sh` manuscript.

Wanneer dit wordt uitgevoerd tegen uw vastgelegde artefact of de submap `dispatcher/src` , worden validatiefouten gerapporteerd:

```
$ validator full dispatcher/src
Cloud manager validator 1.0.4
2019/06/19 15:41:37 Apache configuration uses non-allowlisted directives:
  conf.d/enabled_vhosts/aem_publish.vhost:46: LogLevel
2019/06/19 15:41:37 Dispatcher configuration validation failed:
  conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any: filter allows access to CRXDE
```

In Windows is de Dispatcher-validator hoofdlettergevoelig. Als dusdanig, kan het er niet in slagen om de configuratie te bevestigen als u niet de kapitalisatie van de weg respecteert waar uw configuratie, bijvoorbeeld verblijft:

```
bin\validator.exe full src
Cloud manager validator 2.0.xx
2021/03/15 18:15:40 Dispatcher configuration validation failed:
  conf.dispatcher.d\available_farms\default.farm:15: parent directory outside server root: c:\k\a\aem-dispatcher-sdk-windows-symlinks-testing3\dispatcher\src
  
```

Vermijd deze fout door de weg van de Ontdekkingsreiziger van Vensters en dan op de bevelherinnering te kopiëren en te kleven gebruikend een `cd` bevel in die weg.

### Fase 2 {#second-phase}

In deze fase wordt de Apache-syntaxis gecontroleerd door Docker in een afbeelding te starten. Docker moet lokaal zijn geïnstalleerd, maar AEM hoeft niet te worden uitgevoerd.

>[!NOTE]
>Windows-gebruikers moeten Windows 10 Professional of andere distributies gebruiken die Docker ondersteunen. Deze voorwaarde is vereist om Dispatcher op een lokale computer uit te voeren en te debuggen.

Deze fase kan ook onafhankelijk door `validator full -d out src/dispatcher` worden uitgevoerd, die een map &quot;out&quot; genereert die nodig is voor de volgende opdracht `bin/docker_run.sh out host.docker.internal:4503 8080` .

Tijdens een Cloud Manager-implementatie wordt de syntaxiscontrole van `httpd -t` uitgevoerd en worden eventuele fouten opgenomen in het foutenlogboek van de stap Cloud Manager Build Images.

### Fase 3 {#third-phase}

Als er in deze fase een fout optreedt, houdt dit in dat de Adobe een of meer onveranderlijke bestanden heeft gewijzigd. In dat geval moet u de overeenkomstige onveranderlijke bestanden vervangen door de nieuwe versie die wordt geleverd in de map `src` van de SDK. Dit wordt in het volgende logboekvoorbeeld geïllustreerd:

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

Deze fase kan ook onafhankelijk door `validator full -d out src/dispatcher` worden uitgevoerd, die een map &quot;uit&quot;produceert, nodig door het volgende bevel `bin/docker_immutability_check.sh out`.

## Fouten opsporen in uw Apache- en Dispatcher-configuratie {#debugging-apache-and-dispatcher-configuration}

U kunt Apache Dispatcher lokaal uitvoeren met `./bin/docker_run.sh out docker.for.mac.localhost:4503 8080` .

Zoals eerder vermeld, moet Docker plaatselijk worden geïnstalleerd en het is niet noodzakelijk voor AEM in werking te stellen. Windows-gebruikers moeten Windows 10 Professional of andere distributies gebruiken die Docker ondersteunen. Deze voorwaarde is vereist om Dispatcher op een lokale computer uit te voeren en te debuggen.

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

Wanneer Dispatcher lokaal wordt uitgevoerd, worden logbestanden rechtstreeks naar de einduitvoer afgedrukt. Meestal, wilt u deze logboeken in DEBUG zijn, die kan worden gedaan door het Debug niveau als parameter over te gaan wanneer het runnen van Docker. Bijvoorbeeld: `DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080` .

Logbestanden voor cloudomgevingen worden weergegeven via de logbestandsservice die beschikbaar is in Cloud Manager.

## Verschillende Dispatcher-configuraties per omgeving {#different-dispatcher-configurations-per-environment}

Momenteel wordt dezelfde Dispatcher-configuratie toegepast op alle omgevingen in AEM as a Cloud Service. De runtime heeft een omgevingsvariabele `ENVIRONMENT_TYPE` die de huidige uitvoermodus bevat (dev, stag of prod) en een definitie. De definitie kan `ENVIRONMENT_DEV`, `ENVIRONMENT_STAGE` of `ENVIRONMENT_PROD` zijn. In de Apache-configuratie kan de variabele rechtstreeks in een expressie worden gebruikt. U kunt ook de definitie gebruiken om logica op te bouwen:

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

Wanneer u uw configuratie lokaal test, kunt u verschillende omgevingstypen simuleren door de variabele `DISP_RUN_MODE` rechtstreeks door te geven aan het `docker_run.sh` -script:

```
$ DISP_RUN_MODE=stage docker_run.sh out docker.for.mac.localhost:4503 8080
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

## Migreren van oude modus naar flexibele modus {#migrating-flexible}

Met de versie van Cloud Manager 2021.7.0, produceren de nieuwe programma&#39;s van Cloud Manager gemodelleerde projectstructuren met AEM archetype 28 of hoger, die het dossier **opt-in/USE_SOURCES_DIRECTLY** omvat. Eerdere beperkingen van de verouderde modus met betrekking tot het aantal en de grootte van bestanden worden verwijderd, waardoor de SDK en de runtime de configuratie op een verbeterde manier valideren en implementeren. Als dit bestand niet beschikbaar is in uw Dispatcher-configuratie, wordt u ten zeerste aangeraden te migreren. Gebruik de methodes die in de [ worden beschreven flexibele wijze ](/help/implementing/dispatcher/validation-debug.md#migrating) pagina.
