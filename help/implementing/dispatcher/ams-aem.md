---
title: De Dispatcher-configuratie migreren van AMS naar AEM als Cloud Service
description: 'De Dispatcher-configuratie migreren van AMS naar AEM als Cloud Service '
feature: Dispatcher
source-git-commit: 19444aacbb86f93e7a5ea8bda2ca3c03a0a44f98
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 14%

---

# De Dispatcher-configuratie migreren van AMS naar AEM als Cloud Service {#Dispatcher-in-the-cloud}

## Belangrijkste verschillen tussen AMS Dispatcher en AEM als Cloud Service {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service}

De Apache- en Dispatcher-configuratie in AEM als een Cloud Service lijkt sterk op de AMS-configuratie. De belangrijkste verschillen zijn:

* In AEM als Cloud Service kunnen sommige Apache-instructies niet worden gebruikt (bijvoorbeeld `Listen` of `LogLevel`)
* In AEM als Cloud Service, slechts kunnen sommige stukken van de configuratie van de Verzender in omvat dossiers worden gezet en hun het noemen is belangrijk. Zo moeten filterregels die u op verschillende hosts opnieuw wilt gebruiken, in een bestand met de naam `filters/filters.any` worden geplaatst. Zie de referentiepagina voor meer informatie.
* In AEM als Cloud Service is er extra bevestiging om filterregels te verbieden die worden geschreven gebruikend `/glob` om veiligheidskwesties te verhinderen. Aangezien `deny *` eerder dan `allow *` (die niet kan worden gebruikt) zal worden gebruikt, zullen klanten van het uitvoeren van de Dispatcher plaatselijk profiteren en het doen van proef en fout, bekijkend de logboeken om precies te weten welke wegen de filters van de Verzender blokkeren opdat die kunnen worden toegevoegd.

## Richtlijnen voor het migreren van de configuratie van de verzender van AMS naar AEM als Cloud Service

De Dispatcher-configuratiestructuur heeft verschillen tussen Managed Services en AEM als Cloud Service. Hieronder wordt een stapsgewijze handleiding gepresenteerd voor het migreren van AMS Dispatcher Configuration versie 2 naar AEM als Cloud Service.

## Een AMS converteren naar een AEM als configuratie voor een cloudservice-verzender

In de volgende sectie vindt u stapsgewijze instructies voor het omzetten van een AMS-configuratie. Het veronderstelt
dat u een archief hebt met een structuur die lijkt op de structuur die wordt beschreven in [Configuratie van de Verzender van de Manager van de Wolk](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html)

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

Als u nog secties in uw virtuele gastheerdossiers hebt die uitsluitend naar andere havens dan haven 80 verwijzen, bijvoorbeeld:

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

Voer de Dispatcher-validator in uw map uit met de subopdracht `httpd`:

```
$ validator httpd .
```

Als er fouten optreden over ontbrekende Include-bestanden, controleert u of de naam van die bestanden correct is gewijzigd.

Als u Apache-instructies ziet die niet zijn gevoegd op lijst van gewenste personen, verwijdert u deze.

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
vanuit de standaardconfiguratie voor Dispatcher naar deze map. De standaardverzender
Deze configuratie vindt u in de map `src` van deze SDK. Vergeet niet de
`$include` instructies die verwijzen naar de `ams_*_cache.any`-regelbestanden in de landbouwbedrijfsbestanden
ook.

Als `conf.dispatcher.d/cache` nu een enkel bestand bevat met achtervoegsel `_cache.any`,
moet de naam van het bestand worden gewijzigd in `rules.any` en vergeet niet om de `$include`-instructies aan te passen
die ook verwijzen naar dat dossier in de landbouwbedrijfdossiers.

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, hun inhoud
moet naar de `$include` verklaring worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

Verwijder elk bestand met het achtervoegsel `_invalidate_allowed.any`.

Het bestand `conf.dispatcher.d/cache/default_invalidate_any` kopiëren uit de standaardmap
AEM in de configuratie van Cloud Dispatcher naar die locatie.

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

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, hun inhoud
moet naar de `$include` verklaring worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

Het bestand `conf.dispatcher/clientheaders/default_clientheaders.any` kopiëren uit de standaardmap
AEM als configuratie van de Verzender van de Cloud Service aan die plaats.

In elk landbouwbedrijfdossier, vervang om het even welke cliënt omvat verklaring die als volgt kijkt:

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

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, hun inhoud
moet naar de `$include` verklaring worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

Het bestand `conf.dispatcher/filters/default_filters.any` kopiëren uit de standaardmap
AEM als configuratie van de Verzender van de Cloud Service aan die plaats.

In elk landbouwbedrijfdossier, vervang om het even welke filter omvat verklaringen die als volgt kijken:

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
AEM als configuratie van de Verzender van de Cloud Service aan die plaats.

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

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, hun inhoud
moet naar de `$include` verklaring worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

Het bestand `conf.dispatcher/virtualhosts/default_virtualhosts.any` kopiëren uit de standaardmap
AEM als configuratie van de Verzender van de Cloud Service aan die plaats.

In elk landbouwbedrijfdossier, vervang om het even welke filter omvat verklaringen die als volgt kijken:

```
$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"
```

met de instructie:

```
$include "../virtualhosts/default_virtualhosts.any"
```

### Uw status controleren door de validatietool uit te voeren

Voer de AEM als validator van de Verzender van de Cloud Service in uw folder, met `dispatcher` subcommand in werking:

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

### Stap 2: De Dispatcher starten in een dockerafbeelding met die implementatiegegevens

Wanneer uw AEM publicatieserver op uw MacOS-computer wordt uitgevoerd, luistert u naar poort 4503,
u kunt de Dispatcher als volgt voor die server starten:

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

Hierdoor wordt de container gestart en is Apache beschikbaar op de lokale poort 8080.

### De nieuwe Dispatcher-configuratie gebruiken

Gefeliciteerd! Als de validator geen problemen meer rapporteert en als de
dockercontainer wordt gestart zonder fouten of waarschuwingen, u bent
klaar om uw configuratie aan `dispatcher/src` subdirectory te bewegen
van uw it-opslagplaats.

**Klanten die AMS Dispatcher Configuration versie 1 gebruiken, dienen contact op te nemen met de klantenondersteuning om hen te helpen bij de migratie van versie 1 naar versie 2, zodat bovenstaande instructies kunnen worden opgevolgd.**
