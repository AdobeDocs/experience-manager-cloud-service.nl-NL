---
title: Dispatcher-configuratie migreren van AMS naar AEM as a Cloud Service
description: Dispatcher-configuratie migreren van AMS naar AEM as a Cloud Service
feature: Dispatcher
exl-id: ff7397dd-b6e1-4d08-8e2d-d613af6b81b3
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '1499'
ht-degree: 4%

---

# Dispatcher-configuratie migreren van AMS naar AEM as a Cloud Service {#Dispatcher-in-the-cloud}

## Belangrijkste verschillen tussen AMS Dispatcher en AEM as a Cloud Service {#main-differences-between-ams-dispatcher-configuration-and-aem-as-a-cloud-service}

De Apache- en Dispatcher-configuratie in AEM as a Cloud Service lijkt sterk op die van AMS. De belangrijkste verschillen zijn:

* In AEM as a Cloud Service worden sommige Apache-instructies mogelijk niet gebruikt (bijvoorbeeld `Listen` of `LogLevel` )
* In AEM as a Cloud Service kunnen alleen bepaalde onderdelen van de Dispatcher-configuratie worden opgenomen in include-bestanden en is de naamgeving ervan belangrijk. Zo moeten filterregels die u op verschillende hosts opnieuw wilt gebruiken, in een bestand met de naam `filters/filters.any` worden geplaatst. Zie de referentiepagina voor meer informatie.
* In AEM as a Cloud Service is er een extra validatie om filterregels die met `/glob` zijn geschreven, niet toe te staan om beveiligingsproblemen te voorkomen. Omdat `deny *` wordt gebruikt in plaats van `allow *` (en niet kan worden gebruikt), profiteren klanten van het lokaal uitvoeren van de Dispatcher en het uitvoeren van vallen en fouten. In de logboeken ziet u precies welke paden door de Dispatcher-filters worden geblokkeerd, zodat deze kunnen worden toegevoegd.
* In AEM as a Cloud Service wordt het momenteel hoogst geadviseerd om [ te kiezen binnen om de flexibele bronwijze van verzender config ](/help/implementing/dispatcher/disp-overview.md#validation-debug) te gebruiken bv. om web-tier config pijpleidingen te gebruiken of betere flexibiliteit op aantal en structuur van configuratiedossiers te hebben.

## Richtlijnen voor het migreren van de configuratie van de verzender van AMS naar AEM as a Cloud Service

De Dispatcher-configuratiestructuur is anders tussen Managed Services en AEM as a Cloud Service. Hieronder wordt een stapsgewijze handleiding gepresenteerd voor het migreren van AMS Dispatcher-configuratieversie 2 naar AEM as a Cloud Service.

## Een AMS converteren naar een AEM als Dispatcher-configuratie voor een cloudservice

In de volgende sectie vindt u stapsgewijze instructies voor het omzetten van een AMS-configuratie. Zij gaat ervan uit
dat u een archief met een structuur gelijkend op die in [ wordt beschreven de configuratie van Dispatcher van Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html?lang=nl-NL) hebt

### Het archief extraheren en een eventueel voorvoegsel verwijderen

Extraheer het archief naar een map en zorg ervoor dat de directe submappen beginnen met `conf`, `conf.d` ,
`conf.dispatcher.d` en `conf.modules.d` . Als ze dat niet doen, verplaatst u ze omhoog in de hiërarchie.

### Ongebruikte submappen en bestanden verwijderen

Submappen `conf` en `conf.modules.d` en bestanden die overeenkomen met `conf.d/*.conf` verwijderen.

### Alle niet-gepubliceerde virtuele hosts verwijderen

Verwijder een willekeurig virtueel hostbestand in `conf.d/enabled_vhosts` met `author`, `unhealthy`, `health` .
`lc` of `flush` in de naam. Niet alle virtuele hostbestanden in `conf.d/available_vhosts`
kan ook worden verwijderd.

### Verwijder of becommentarieer virtuele hostsecties die niet verwijzen naar poort 80

Als u nog secties in uw virtuele gastheerdossiers hebt die uitsluitend naar andere havens dan haven 80 verwijzen, bijvoorbeeld:

```
<VirtualHost *:443>
...
</VirtualHost>
```

verwijderen of opmerkingen maken. Instructies in deze secties worden niet verwerkt, maar als u
Als u ze rond houdt, kunt u ze waarschijnlijk nog steeds zonder effect bewerken, wat verwarrend is.

### Herschrijvingen controleren

Voer de map `conf.d/rewrites` in.

Verwijder alle bestanden met de naam `base_rewrite.rules` en `xforwarded_forcessl_rewrite.rules` en vergeet niet om
Verwijder `Include` -instructies uit de virtuele hostbestanden die naar deze bestanden verwijzen.

Als `conf.d/rewrites` nu één bestand bevat, moet u de naam ervan wijzigen in `rewrite.rules` en de naam niet wijzigen
vergeet de instructies `Include` die naar dat bestand verwijzen, ook in de virtuele hostbestanden aan te passen.

Als de map echter meerdere, virtuele hostspecifieke bestanden bevat, moet de inhoud ervan
gekopieerd naar de instructie `Include` die ernaar verwijst in de virtuele hostbestanden.

### Variabelen controleren

Voer de map `conf.d/variables` in.

Verwijder alle bestanden met de naam `ams_default.vars` en vergeet niet `Include` -instructies in het virtuele bestand te verwijderen
hostbestanden die ernaar verwijzen.

Als `conf.d/variables` nu één bestand bevat, moet u de naam ervan wijzigen in `custom.vars` en de naam niet wijzigen
vergeet de instructies `Include` die naar dat bestand verwijzen, ook in de virtuele hostbestanden aan te passen.

Als de map echter meerdere, virtuele hostspecifieke bestanden bevat, moet de inhoud ervan
gekopieerd naar de instructie `Include` die ernaar verwijst in de virtuele hostbestanden.

### Lijsten van gewenste personen verwijderen

Verwijder de map `conf.d/whitelists` en verwijder `Include` -instructies in de virtuele hostbestanden die verwijzen naar
een bestand in die submap.

### Variabelen vervangen die niet meer beschikbaar zijn

In alle virtuele hostbestanden:

Naam van `PUBLISH_DOCROOT` wijzigen in `DOCROOT`
Secties verwijderen die verwijzen naar de variabelen `DISP_ID` , `PUBLISH_FORCE_SSL` of `PUBLISH_WHITELIST_ENABLED`

### Controleer uw status door validator uit te voeren

Voer de Dispatcher-validator in uw map uit met de subopdracht `httpd` :

```
$ validator httpd .
```

Als u fouten ziet over ontbrekende include-bestanden, controleert u of u de namen correct hebt gewijzigd
bestanden.

Als u Apache-instructies ziet die niet zijn gevoegd op lijst van gewenste personen, verwijdert u deze.

### Alle niet-publicatiebedrijven verwijderen

Verwijder een willekeurig landbouwbedrijfsbestand in `conf.dispatcher.d/enabled_farms` dat `author`, `unhealthy`, `health` heeft,
`lc` of `flush` in de naam. Niet alle bestanden op de farm in `conf.dispatcher.d/available_farms`
kan ook worden verwijderd.

### Naam van landbouwhuisbestanden wijzigen

Alle boerderijen in `conf.dispatcher.d/enabled_farms` moeten een andere naam krijgen om overeen te komen met het patroon `*.farm` , dus bijvoorbeeld een
Het bestand met de naam `customerX_farm.any` moet een andere naam krijgen `customerX.farm` .

### Cache controleren

Voer de map `conf.dispatcher.d/cache` in.

Verwijder alle bestanden met het voorvoegsel `ams_`.

Als `conf.dispatcher.d/cache` nu leeg is, kopieert u het bestand `conf.dispatcher.d/cache/rules.any`
van de standaard Dispatcher-configuratie naar deze map. De standaard Dispatcher
Deze configuratie vindt u in de map `src` van deze SDK. Vergeet niet de
`$include` instructies die verwijzen naar de `ams_*_cache.any` -regelbestanden in de landbouwbedrijfsbestanden
ook.

Als in plaats daarvan `conf.dispatcher.d/cache` nu één bestand met achtervoegsel `_cache.any` bevat,
de naam moet worden gewijzigd in `rules.any` en vergeet niet de instructies `$include` aan te passen
die ook verwijzen naar dat dossier in de landbouwbedrijfdossiers.

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, hun inhoud
moet worden gekopieerd naar de instructie `$include` die ernaar verwijst in de bestanden van de farm.

Verwijder elk bestand met het achtervoegsel `_invalidate_allowed.any` .

Bestand `conf.dispatcher.d/cache/default_invalidate_any` kopiëren van de standaardwaarde
AEM in de configuratie van Cloud Dispatcher naar die locatie.

Verwijder in elk landbouwbedrijfdossier om het even welke inhoud in de `cache/allowedClients` sectie en vervang het
met:

```
$include "../cache/default_invalidate.any"
```

### Clientkoppen controleren

Voer de map `conf.dispatcher.d/clientheaders` in.

Verwijder alle bestanden met het voorvoegsel `ams_`.

Als `conf.dispatcher.d/clientheaders` nu één bestand met achtervoegsel `_clientheaders.any` bevat,
de naam moet worden gewijzigd in `clientheaders.any` en vergeet niet de instructies `$include` aan te passen
die ook verwijzen naar dat dossier in de landbouwbedrijfdossiers.

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, hun inhoud
moet worden gekopieerd naar de instructie `$include` die ernaar verwijst in de bestanden van de farm.

Bestand `conf.dispatcher/clientheaders/default_clientheaders.any` kopiëren van de standaardwaarde
AEM as a Cloud Service Dispatcher-configuratie naar die locatie.

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

Als `conf.dispatcher.d/filters` nu één bestand bevat, moet u de naam wijzigen in
`filters.any` en vergeet niet de instructies `$include` die naar dat verwijzen, aan te passen
ook in de landbouwbedrijfdossiers.

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, hun inhoud
moet worden gekopieerd naar de instructie `$include` die ernaar verwijst in de bestanden van de farm.

Bestand `conf.dispatcher/filters/default_filters.any` kopiëren van de standaardwaarde
AEM as a Cloud Service Dispatcher-configuratie naar die locatie.

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

Bestand `conf.dispatcher.d/renders/default_renders.any` kopiëren van de standaardwaarde
AEM as a Cloud Service Dispatcher-configuratie naar die locatie.

Verwijder in elk landbouwbedrijfdossier om het even welke inhoud in de `renders` sectie en vervang het
met:

```
$include "../renders/default_renders.any"
```

### Virtuele hosts controleren

Wijzig de naam van de map `conf.dispatcher.d/vhosts` in `conf.dispatcher.d/virtualhosts` en voer deze in.

Verwijder alle bestanden met het voorvoegsel `ams_`.

Als `conf.dispatcher.d/virtualhosts` nu één bestand bevat, moet u de naam wijzigen in
`virtualhosts.any` en vergeet niet de instructies `$include` die naar dat verwijzen, aan te passen
ook in de landbouwbedrijfdossiers.

Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, hun inhoud
moet worden gekopieerd naar de instructie `$include` die ernaar verwijst in de bestanden van de farm.

Bestand `conf.dispatcher/virtualhosts/default_virtualhosts.any` kopiëren van de standaardwaarde
AEM as a Cloud Service Dispatcher-configuratie naar die locatie.

In elk landbouwbedrijfdossier, vervang om het even welke filter omvat verklaringen die als volgt kijken:

```
$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"
```

met de instructie:

```
$include "../virtualhosts/default_virtualhosts.any"
```

### Controleer uw status door validator uit te voeren

Voer de AEM as a Cloud Service Dispatcher-validator in uw map uit met de subopdracht `dispatcher` :

```
$ validator dispatcher .
```

Als u fouten ziet over ontbrekende include-bestanden, controleert u of u de namen correct hebt gewijzigd
bestanden.

Als er fouten optreden met betrekking tot een niet-gedefinieerde variabele `PUBLISH_DOCROOT`, wijzigt u de naam hiervan naar `DOCROOT`.

Voor elke andere fout, zie de sectie van het Oplossen van problemen van
documentatie bij het validatieprogramma.

### Test uw configuratie met een lokale plaatsing (vereist de installatie van Docker)

Met het script `docker_run.sh` in de AEM as a Cloud Service Dispatcher Tools kunt u testen of
uw configuratie bevat geen andere fout die alleen in
implementatie:

### Stap 1: Genereer plaatsingsinformatie met validator

```
validator full -d out .
```

Hiermee wordt de volledige configuratie gevalideerd en worden implementatiegegevens gegenereerd in `out`

### Stap 2: Start de Dispatcher in een dockerafbeelding met die implementatiegegevens

Wanneer uw AEM publicatieserver op uw macOS-computer wordt uitgevoerd, luistert u naar poort 4503,
u kunt de Dispatcher als volgt voor die server starten:

```
$ docker_run.sh out docker.for.mac.localhost:4503 8080
```

Hierdoor wordt de container gestart en is Apache beschikbaar op de lokale poort 8080.

### De nieuwe Dispatcher-configuratie gebruiken

Gefeliciteerd! Als de validator geen problemen meer rapporteert en als de
de havencontainer begint zonder enige mislukkingen of waarschuwingen, u bent
klaar om uw configuratie naar een submap `dispatcher/src` te verplaatsen
van uw it-opslagplaats.

**Klanten die AMS Dispatcher configuratieversie 1 gebruiken zouden klantensteun moeten contacteren om hen te helpen van versie 1 aan versie 2 migreren zodat kunnen de instructies hierboven worden gevolgd.**
