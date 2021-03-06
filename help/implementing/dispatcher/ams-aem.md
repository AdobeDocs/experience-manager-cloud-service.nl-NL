---
title: De Dispatcher-configuratie migreren van AMS naar AEM as a Cloud Service
description: De Dispatcher-configuratie migreren van AMS naar AEM as a Cloud Service
feature: Dispatcher
exl-id: ff7397dd-b6e1-4d08-8e2d-d613af6b81b3
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: tm+mt
source-wordcount: '1446'
ht-degree: 14%

---

# De Dispatcher-configuratie migreren van AMS naar AEM as a Cloud Service {#Dispatcher-in-the-cloud}

## Belangrijkste verschillen tussen AMS Dispatcher en AEM as a Cloud Service {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service}

De Apache- en Dispatcher-configuratie in AEM as a Cloud Service lijkt sterk op de AMS-configuratie. De belangrijkste verschillen zijn:

* In AEM as a Cloud Service kunnen sommige Apache-richtlijnen niet worden gebruikt (bijvoorbeeld `Listen` of `LogLevel`)
* In AEM as a Cloud Service, slechts kunnen sommige stukken van de configuratie van de Verzender in omvat dossiers worden gezet en hun het noemen is belangrijk. Bijvoorbeeld, moeten de filterregels die u over verschillende gastheren wilt hergebruiken in een dossier worden gezet genoemd `filters/filters.any`. Zie de referentiepagina voor meer informatie.
* In AEM as a Cloud Service is er extra validatie om filterregels die zijn geschreven met `/glob` om beveiligingsproblemen te voorkomen. Sinds `deny *` wordt gebruikt in plaats van `allow *` (wat niet kan worden gebruikt), zullen de klanten van het runnen van de Verzender plaatselijk profiteren en het doen van proef en fout, die de logboeken bekijken om precies te weten welke wegen de filters van de Verzender blokkeren opdat die kunnen worden toegevoegd.

## Richtlijnen voor het migreren van de configuratie van de verzender van AMS naar AEM as a Cloud Service

De Dispatcher-configuratiestructuur heeft verschillen tussen Managed Services en AEM as a Cloud Service. Hieronder wordt een stapsgewijze handleiding gepresenteerd voor het migreren van AMS Dispatcher Configuration versie 2 naar AEM as a Cloud Service.

## Een AMS converteren naar een AEM als configuratie voor een cloudservice-verzender

In de volgende sectie vindt u stapsgewijze instructies voor het omzetten van een AMS-configuratie. Hierbij wordt ervan uitgegaan dat u een archief hebt met een structuur die vergelijkbaar is met de structuur die in [Configuratie van Cloud Manager-verzending](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html)

### Het archief extraheren en een eventueel voorvoegsel verwijderen

Het archief naar een map extraheren en controleren of de directe submappen beginnen met `conf`, `conf.d`,
`conf.dispatcher.d` en `conf.modules.d`. Als ze dat niet doen, verplaats ze omhoog in de hi??rarchie.

### Ongebruikte submappen en bestanden verwijderen

Submappen verwijderen `conf` en `conf.modules.d`en bestanden die overeenkomen `conf.d/*.conf`.

### Alle niet-gepubliceerde virtuele hosts verwijderen

Verwijder een virtueel hostbestand in `conf.d/enabled_vhosts` dat `author`, `unhealthy`, `health`,
`lc` of `flush` in zijn naam. Alle virtuele hostbestanden in `conf.d/available_vhosts` die niet zijn gekoppeld aan, kunnen ook worden verwijderd.

### Verwijder of becommentarieer virtuele hostsecties die niet verwijzen naar poort 80

Als u nog secties in uw virtuele gastheerdossiers hebt die uitsluitend naar andere havens dan haven 80 verwijzen, bijvoorbeeld:

```
<VirtualHost *:443>
...
</VirtualHost>
```

verwijder deze dan of plaats een opmerking. Instructies in deze secties worden niet verwerkt, maar als u ze niet verwijdert, kan het gebeuren dat u ze alsnog bewerkt, zonder effect. En dat kan verwarrend zijn.

### Herschrijvingen controleren

Map invoeren `conf.d/rewrites`.

Bestandsnaam verwijderen `base_rewrite.rules` en `xforwarded_forcessl_rewrite.rules` en vergeet niet te verwijderen `Include` instructies in de virtuele hostbestanden die naar deze bestanden verwijzen.

Indien `conf.d/rewrites` bevat nu ????n bestand. Wijzig de naam van dit bestand in `rewrite.rules` en vergeet niet om de `Include` instructies die naar dat bestand verwijzen, ook in de virtuele hostbestanden.

Als de map echter meerdere, virtuele hostspecifieke bestanden bevat, moet de inhoud ervan naar de `Include` in de virtuele hostbestanden.

### Variabelen controleren

Map invoeren `conf.d/variables`.

Bestandsnaam verwijderen `ams_default.vars` en vergeet niet te verwijderen `Include` instructies in de virtuele hostbestanden die naar deze bestanden verwijzen.

Indien `conf.d/variables` bevat nu ????n bestand. Wijzig de naam van dit bestand in `custom.vars` en vergeet niet om de `Include` instructies die naar dat bestand verwijzen, ook in de virtuele hostbestanden.

Als de map echter meerdere, virtuele hostspecifieke bestanden bevat, moet de inhoud ervan naar de `Include` in de virtuele hostbestanden.

### Lijsten van gewenste personen verwijderen

De map verwijderen `conf.d/whitelists` en verwijderen `Include` instructies in de virtuele-hostbestanden die verwijzen naar een bestand in die submap.

### Variabelen vervangen die niet meer beschikbaar zijn

In alle virtuele hostbestanden:

Naam wijzigen `PUBLISH_DOCROOT` tot `DOCROOT`
Secties verwijderen die verwijzen naar benoemde variabelen `DISP_ID`, `PUBLISH_FORCE_SSL` of `PUBLISH_WHITELIST_ENABLED`

### Uw status controleren door de validatietool uit te voeren

Voer de Dispatcher-validator in uw map uit, met de `httpd` subopdracht:

```
$ validator httpd .
```

Als er fouten optreden over ontbrekende Include-bestanden, controleert u of de naam van die bestanden correct is gewijzigd.

Als u Apache-instructies ziet die niet zijn gevoegd op lijst van gewenste personen, verwijdert u deze.

### Alle niet-publicatiefarms verwijderen

Verwijder alle bestanden uit een farm in `conf.dispatcher.d/enabled_farms` dat `author`, `unhealthy`, `health`,
`lc` of `flush` in zijn naam. Alle landbouwbedrijfdossiers in `conf.dispatcher.d/available_farms` die niet zijn gekoppeld aan, kunnen ook worden verwijderd.

### De naam van farmbestanden wijzigen

Alle bedrijven in `conf.d/enabled_farms` moet worden hernoemd om overeen te komen met het patroon `*.farm`, dus bijvoorbeeld een landbouwbedrijfsdossier genoemd `customerX_farm.any` naam wijzigen `customerX.farm`.

### Cache controleren

Map invoeren `conf.dispatcher.d/cache`.

Verwijder alle bestanden met het voorvoegsel `ams_`.

Indien `conf.dispatcher.d/cache` is nu leeg, kopieert u het bestand `conf.dispatcher.d/cache/rules.any`
vanuit de standaardconfiguratie voor Dispatcher naar deze map. De standaardconfiguratie voor Dispatcher vindt u in de map `src` van deze SDK. Vergeet niet de
`$include` verklaringen die verwijzen naar de `ams_*_cache.any` ook regelbestanden in de bestanden van de farm.

Indien in `conf.dispatcher.d/cache` bevat nu ????n bestand met achtervoegsel `_cache.any`, moet de naam worden gewijzigd in `rules.any` en vergeet niet om de `$include` verklaringen die naar dat dossier in de landbouwbedrijfdossiers eveneens verwijzen.

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, zou hun inhoud aan moeten worden gekopieerd `$include` verklaring die naar hen in de landbouwbedrijfdossiers verwijst.

Alle bestanden met het achtervoegsel verwijderen `_invalidate_allowed.any`.

Het bestand kopi??ren `conf.dispatcher.d/cache/default_invalidate_any` van de AEM in de configuratie van Cloud Dispatcher naar die locatie.

In elk landbouwbedrijfdossier, verwijder om het even welke inhoud in `cache/allowedClients` en vervangen door:

```
$include "../cache/default_invalidate.any"
```

### Clientheaders controleren

Map invoeren `conf.dispatcher.d/clientheaders`.

Verwijder alle bestanden met het voorvoegsel `ams_`.

Indien `conf.dispatcher.d/clientheaders` bevat nu ????n bestand met achtervoegsel `_clientheaders.any`, moet de naam worden gewijzigd in `clientheaders.any` en vergeet niet om de `$include` verklaringen die naar dat dossier in de landbouwbedrijfdossiers eveneens verwijzen.

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, zou hun inhoud aan moeten worden gekopieerd `$include` verklaring die naar hen in de landbouwbedrijfdossiers verwijst.

Het bestand kopi??ren `conf.dispatcher/clientheaders/default_clientheaders.any` van het gebrek AEM as a Cloud Service configuratie van de Verzender aan die plaats.

In elk landbouwbedrijfdossier, vervang om het even welke cli??nt omvat verklaring die als volgt kijkt:

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

Indien `conf.dispatcher.d/filters` bevat nu ????n bestand waarnaar de naam moet worden gewijzigd
`filters.any` en vergeet niet om de `$include` verklaringen die naar dat dossier in de landbouwbedrijfdossiers eveneens verwijzen.

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, zou hun inhoud aan moeten worden gekopieerd `$include` verklaring die naar hen in de landbouwbedrijfdossiers verwijst.

Het bestand kopi??ren `conf.dispatcher/filters/default_filters.any` van het gebrek AEM as a Cloud Service configuratie van de Verzender aan die plaats.

In elk landbouwbedrijfdossier, vervang om het even welke filter omvat verklaringen die als volgt kijken:

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

Het bestand kopi??ren `conf.dispatcher.d/renders/default_renders.any` van het gebrek AEM as a Cloud Service configuratie van de Verzender aan die plaats.

In elk landbouwbedrijfdossier, verwijder om het even welke inhoud in `renders` en vervangen door:

```
$include "../renders/default_renders.any"
```

### Virtuele hosts controleren

De naam van de map wijzigen `conf.dispatcher.d/vhosts` tot `conf.dispatcher.d/virtualhosts` en voert u deze in.

Verwijder alle bestanden met het voorvoegsel `ams_`.

Indien `conf.dispatcher.d/virtualhosts` bevat nu ????n bestand waarnaar de naam moet worden gewijzigd
`virtualhosts.any` en vergeet niet om de `$include` verklaringen die naar dat dossier in de landbouwbedrijfdossiers eveneens verwijzen.

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, zou hun inhoud aan moeten worden gekopieerd `$include` verklaring die naar hen in de landbouwbedrijfdossiers verwijst.

Het bestand kopi??ren `conf.dispatcher/virtualhosts/default_virtualhosts.any` van het gebrek AEM as a Cloud Service configuratie van de Verzender aan die plaats.

In elk landbouwbedrijfdossier, vervang om het even welke filter omvat verklaringen die als volgt kijken:

```
$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"
```

met de instructie:

```
$include "../virtualhosts/default_virtualhosts.any"
```

### Uw status controleren door de validatietool uit te voeren

Voer de AEM as a Cloud Service Dispatcher-validator in uw directory uit met de `dispatcher` subopdracht:

```
$ validator dispatcher .
```

Als er fouten optreden over ontbrekende Include-bestanden, controleert u of de naam van die bestanden correct is gewijzigd.

Als er fouten optreden met betrekking tot een niet-gedefinieerde variabele `PUBLISH_DOCROOT`, wijzigt u de naam hiervan naar `DOCROOT`.

Bij andere fouten bekijkt u de sectie Problemen oplossen in de documentatie over de validatietool.

### Test uw configuratie met een lokale plaatsing (vereist de installatie van Docker)

Het script gebruiken `docker_run.sh` in de AEM as a Cloud Service Hulpmiddelen van de Verzender, kunt u testen dat uw configuratie geen andere fout bevat die slechts in plaatsing zou verschijnen:

### Stap 1: Implementatiegegevens genereren met de validator

```
validator full -d out .
```

Dit bevestigt de volledige configuratie en produceert plaatsingsinformatie binnen `out`

### Stap 2: De Dispatcher starten in een dockerafbeelding met die implementatiegegevens

Wanneer uw AEM publicatieserver op uw macOS-computer wordt uitgevoerd en u luistert naar poort 4503, kunt u de Dispatcher als volgt voor die server starten:

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

Hierdoor wordt de container gestart en is Apache beschikbaar op de lokale poort 8080.

### De nieuwe Dispatcher-configuratie gebruiken

Gefeliciteerd! Als de validator geen probleem meer rapporteert en de dockercontainer wordt gestart zonder fouten of waarschuwingen, kunt u de configuratie verplaatsen naar een `dispatcher/src` subdirectory van uw it-opslagplaats.

**Klanten die AMS Dispatcher Configuration versie 1 gebruiken, dienen contact op te nemen met de klantenondersteuning om hen te helpen bij de migratie van versie 1 naar versie 2, zodat bovenstaande instructies kunnen worden opgevolgd.**
