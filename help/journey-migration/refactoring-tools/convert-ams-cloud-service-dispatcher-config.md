---
title: Een AMS converteren naar een Adobe Experience Manager as a Cloud Service Dispatcher-configuratie
description: Een AMS converteren naar een Adobe Experience Manager as a Cloud Service Dispatcher-configuratie
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '1262'
ht-degree: 37%

---


# Een AMS converteren naar een Adobe Experience Manager (AEM) as a Cloud Service Dispatcher-configuratie

## Inleiding {#introduction}

Deze sectie biedt stapsgewijze instructies voor het omzetten van een AMS-configuratie.

>[!NOTE]
>Hierbij wordt ervan uitgegaan dat u een archief hebt met een structuur die vergelijkbaar is met de structuur die wordt beschreven in [Uw Dispatcher-configuraties beheren](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/getting-started/dispatcher-configurations.html).

## Stappen voor het omzetten van een AMS in AEM as a Cloud Service Dispatcher-configuratie

1. **Het archief extraheren en een eventueel voorvoegsel verwijderen**

   Extraheer het archief naar een map en zorg ervoor dat de directe submappen beginnen met conf, conf.d, conf.dispatcher.d en conf.modules.d. Als ze dat niet doen, verplaatst u ze omhoog in de hiërarchie.

1. **krijg van ongebruikte subfolders en dossiers**

   Verwijder submappen conf en conf.modules.d en bestanden die overeenkomen met conf.d/*.conf.

1. **Alle niet-gepubliceerde virtuele hosts verwijderen**

1. **Een virtueel hostbestand verwijderen**

   In conf.d/enabled_hosts die de naam auteur, ongezond, gezondheid, lc, of flush heeft. Alle virtuele hostbestanden in conf.d/available_vhosts die niet zijn gekoppeld, kunnen ook worden verwijderd.

1. Verwijder of becommentarieer virtuele hostsecties die niet verwijzen naar poort 80

   Als u nog secties in uw virtuele gastheerdossiers hebt die uitsluitend naar andere havens dan haven 80 verwijzen, bijvoorbeeld:

   `<VirtualHost *:443>`
   `...`
   `</VirtualHost>`
verwijder deze dan of plaats een opmerking. Instructies in deze secties worden niet verwerkt, maar als u ze in de buurt houdt, kunt u ze waarschijnlijk nog steeds zonder effect bewerken. Dat is verwarrend.

1. **Herschrijvingen controleren**

   * Open de directory conf.d/rewrites.

   * Verwijder alle bestanden met de naam base_rewrite.rules en xforwarded_forcessl_rewrite.rules en verwijder alle Include-instructies in de virtuele hostbestanden die hiernaar verwijzen.

   * Als conf.d/rewrites nu één enkel dossier bevat, zou het moeten worden anders genoemd om.rules te herschrijven en vergeet niet ook om de Include verklaringen aan te passen die naar dat dossier in de virtuele gastheerdossiers verwijzen.

   * Als de map echter meerdere, virtuele hostspecifieke bestanden bevat, moet de inhoud ervan worden gekopieerd naar de instructie Include die naar deze bestanden in de virtuele hostbestanden verwijst.

1. **Variabelen controleren**

   1. Open de directory conf.d/variables.

   1. Verwijder alle bestanden met de naam ams_default.vars en verwijder alle Include-instructies in de virtuele hostbestanden die hiernaar verwijzen.

   1. Als conf.d/variables nu één enkel dossier bevat, zou het aan custom.vars moeten worden anders genoemd en vergeet niet ook om de Include verklaringen aan te passen die naar dat dossier in de virtuele gastheerdossiers verwijzen.

   1. Als de map echter meerdere, virtuele hostspecifieke bestanden bevat, moet de inhoud ervan worden gekopieerd naar de instructie Include die naar deze bestanden in de virtuele hostbestanden verwijst.

1. **Whitelists verwijderen**

   Verwijder de map conf.d/whitelists en verwijder Include-instructies in de virtuele hostbestanden die verwijzen naar een bestand in die submap.

1. **Variabelen vervangen die niet meer beschikbaar zijn**

   In alle virtuele hostbestanden:

   Wijzig de naam van PUBLISH_DOCROOT naar DOCROOT
Verwijder de secties die verwijzen naar variabelen met de naam DISP_ID, PUBLISH_FORCE_SSL of PUBLISH_WHITELIST_ENABLED

1. **Uw status controleren door de validatietool uit te voeren**

   Voer de Dispatcher-validator in uw map uit met de httpd-subopdracht:

   `$ validator httpd`
Als er fouten optreden die betrekking hebben op ontbrekende include-bestanden, controleert u of de naam van die bestanden correct is gewijzigd.

   Als u Apache-instructies ziet die op de whitelist staan, verwijdert u deze.

1. **Alle niet-publicatiefarms verwijderen**

   Verwijder om het even welk landbouwbedrijfdossier in conf.dispatcher.d/enabled_farm die auteur, ongezond, gezondheid, lc, of flush in zijn naam heeft. Alle farmbestanden in conf.dispatcher.d/available_farms die niet zijn gekoppeld, kunnen ook worden verwijderd.

1. **De naam van farmbestanden wijzigen**

   Alle landbouwbedrijven in conf.dispatcher.d/enabled_farm moeten worden anders genoemd om het patroon *.farm aan te passen. Wijzig bijvoorbeeld de naam `customerX_farm.any` in `customerX.farm` .

1. **Cache controleren**

   Open de directory conf.dispatcher.d/cache.

   Verwijder alle bestanden met het voorvoegsel `ams_`.

   Als conf.dispatcher.d/cache nu leeg is, kopieert u het bestand `conf.dispatcher.d/cache/rules.any` van de standaard Dispatcher-configuratie naar deze map. De standaard Dispatcher-configuratie vindt u in de mapbron van deze SDK. Vergeet niet om $include verklaringen aan te passen die naar de `ams_*_cache.any` regeldossiers in de landbouwbedrijfdossiers verwijzen.

   Als conf.dispatcher.d/cache nu één bestand met achtervoegsel `_cache.any` bevat, moet de naam worden gewijzigd in `rules.any` . Herinner me om $include verklaringen aan te passen die naar dat dossier in de landbouwbedrijfdossiers verwijzen eveneens.

   Als de omslag echter veelvoudige, landbouwbedrijf-specifieke dossiers met dat patroon bevat, zou hun inhoud aan $include verklaring moeten worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

   Verwijder elk bestand met het achtervoegsel `_invalidate_allowed.any` .

   Kopieer het bestand conf.dispatcher.d/cache/default_invalidate_any van de standaard Dispatcher-configuratie naar die locatie.

   Verwijder alle inhoud in de sectie cache/allowedClients voor elk farmbestand en vervang deze door:

   $include &quot;../cache/default_invalidate.any&quot;

1. **Clientheaders controleren**

   Open de directory conf.dispatcher.d/clientheaders.

   Verwijder alle bestanden met het voorvoegsel `ams_`.

   Als conf.dispatcher.d/clientheaders één bestand met achtervoegsel `_clientheaders.any` bevat, wijzigt u de naam in `clientheaders.any` . Herinner me om $include verklaringen aan te passen die naar dat dossier in de landbouwbedrijfdossiers verwijzen eveneens.

   Als de omslag echter veelvoudige, landbouwbedrijf-specifieke dossiers met dat patroon bevat, zou hun inhoud aan $include verklaring moeten worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

   Kopieer het bestand `conf.dispatcher/clientheaders/default_clientheaders.any` van de standaard Dispatcher-configuratie naar die locatie.

   Vervang in elk farm-bestand `clientheader` &quot;include&quot;-instructies die als volgt worden weergegeven:

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"`

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"`

   met de instructie:

   `$include "../clientheaders/default_clientheaders.any"`

1. **Filter controleren**

   * Open de directory conf.dispatcher.d/filters.

   * Verwijder alle bestanden met het voorvoegsel `ams_`.

   * Als conf.dispatcher.d/filters nu één bestand bevat, wijzigt u de naam in `filters.any` . Herinner me om $include verklaringen aan te passen die naar dat dossier in de landbouwbedrijfdossiers verwijzen eveneens.

   * Als de omslag echter veelvoudige, landbouwbedrijf-specifieke dossiers met dat patroon bevat, zou hun inhoud aan $include verklaring moeten worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

   * Kopieer het bestand `conf.dispatcher/filters/default_filters.any` van de standaard Dispatcher-configuratie naar die locatie.

   * In elk landbouwbedrijfdossier, vervang om het even welke filter &quot;omvat&quot;verklaringen die als het volgende verschijnen:

   * $include `"/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"`
met de instructie:

     `$include "../filters/default_filters.any"`

1. **Renderingen controleren**

   * Open de directory conf.dispatcher.d/renders.

   * Verwijder alle bestanden in die map.

   * Kopieer het bestand `conf.dispatcher.d/renders/default_renders.any` van de standaard Dispatcher-configuratie naar die locatie.

   * Verwijder alle inhoud in de sectie renders voor elk farmbestand en vervang deze door:

     `$include "../renders/default_renders.any"`

1. **Virtuele hosts controleren**

   * Wijzig de naam van de directory `conf.dispatcher.d/vhosts to conf.dispatcher.d/virtualhosts` en open de directory.

   * Verwijder alle bestanden met het voorvoegsel `ams_`.

   * Als conf.dispatcher.d/virtualhosts nu één bestand bevat, wijzigt u de naam in `virtualhosts.any` . Herinner me om $include verklaringen aan te passen die naar dat dossier in de landbouwbedrijfdossiers verwijzen eveneens.

   * Als de omslag echter veelvoudige, landbouwbedrijf-specifieke dossiers met dat patroon bevat, zou hun inhoud aan $include verklaring moeten worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

   * Kopieer het bestand `conf.dispatcher/virtualhosts/default_virtualhosts.any` van de standaard Dispatcher-configuratie naar die locatie.

   * In elk landbouwbedrijfdossier, vervang om het even welke filter &quot;omvat&quot;verklaringen die als het volgende verschijnen:

     `$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"`
met de instructie:

     `$include "../virtualhosts/default_virtualhosts.any"`


1. **Uw status controleren door de validatietool uit te voeren**

   * Voer de Dispatcher-validator in uw directory uit met de Dispatcher-subopdracht:

     `$ validator dispatcher`

   * Als er fouten optreden die betrekking hebben op ontbrekende include-bestanden, controleert u of de naam van die bestanden correct is gewijzigd.

   * Als er fouten optreden met betrekking tot een niet-gedefinieerde variabele `PUBLISH_DOCROOT`, wijzigt u de naam hiervan naar `DOCROOT`.

   * Bij andere fouten bekijkt u de sectie Problemen oplossen in de documentatie over de validatietool.

## Uw configuratie testen met een lokale implementatie {#testing-config-local-deployment}

>[!IMPORTANT]
>
>Voor het testen van uw configuratie met een lokale implementatie is de installatie van Docker vereist.

Met het script `docker_run.sh` in de Dispatcher SDK kunt u testen dat uw configuratie geen andere fouten bevat die pas bij de implementatie optreden:

1. Implementatiegegevens genereren met de validator.

   `validator full -d out`
Valideert de volledige configuratie en genereert implementatiegegevens in.

1. Start de Dispatcher in een docker image met die implementatiegegevens.

   Wanneer uw AEM publicatieserver op uw macOS-computer wordt uitgevoerd en u luistert naar poort 4503, kunt u de Dispatcher als volgt voor die server starten:

   `$ docker_run.sh out docker.for.mac.localhost:4503 8080`

   Start de container en stel Apache beschikbaar op lokale poort 8080.

## De nieuwe Dispatcher-configuratie gebruiken {#using-dispatcher-config}

Als de validatietool geen problemen meer rapporteert en de dockercontainer wordt gestart zonder fouten of waarschuwingen, kunt u uw configuratie verplaatsen naar een d`ispatcher/src`-submap van uw Git-repository.