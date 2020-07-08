---
title: Een AMS converteren naar een Adobe Experience Manager as a Cloud Service Dispatcher-configuratie
description: Een AMS converteren naar een Adobe Experience Manager as a Cloud Service Dispatcher-configuratie
translation-type: tm+mt
source-git-commit: 23349f3350631f61f80b54b69104e5a19841272f
workflow-type: tm+mt
source-wordcount: '1342'
ht-degree: 100%

---


# Een AMS converteren naar een Adobe Experience Manager (AEM) as a Cloud Service Dispatcher-configuratie

## Inleiding {#introduction}

Deze sectie biedt stapsgewijze instructies voor het omzetten van een AMS-configuratie.

>[!NOTE]
>Hierbij wordt ervan uitgegaan dat u een archief hebt met een structuur die vergelijkbaar is met de structuur die wordt beschreven in [Uw Dispatcher-configuraties beheren](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html).

## Stappen voor het omzetten van een AMS in AEM as a Cloud Service Dispatcher-configuratie

1. **Het archief extraheren en een eventueel voorvoegsel verwijderen**

   Extraheer het archief naar een map en zorg ervoor dat de directe submappen beginnen met conf, conf.d, conf.dispatcher.d en conf.modules.d. Als dat niet zo is, plaatst u ze hoger in de hiërarchie.

1. **Ongebruikte submappen en bestanden verwijderen**

   Verwijder de submappen conf en conf.modules.d en de bestanden die overeenkomen met conf.d/*.conf.

1. **Alle niet-gepubliceerde virtuele hosts verwijderen**

1. **Een virtueel hostbestand verwijderen**

   In conf.d/enabled_vhosts met author, unhealthy, health, lc of flush in de naam. Alle virtuele hostbestanden in conf.d/available_vhosts die niet zijn gekoppeld, kunnen ook worden verwijderd.

1. Verwijder of becommentarieer virtuele hostsecties die niet verwijzen naar poort 80

   Als u nog secties in uw virtuele hostbestanden hebt die uitsluitend verwijzen naar andere poorten dan poort 80, b.v.

   `<VirtualHost *:443>`
   `...`
   `</VirtualHost>`
verwijder deze dan of plaats een opmerking. Instructies in deze secties worden niet verwerkt, maar als u ze niet verwijdert, kan het gebeuren dat u ze alsnog bewerkt, zonder effect. En dat kan verwarrend zijn.

1. **Herschrijvingen controleren**

   * Open de directory conf.d/rewrites.

   * Verwijder alle bestanden met de naam base_rewrite.rules en xforwarded_forcessl_rewrite.rules en verwijder alle Include-instructies in de virtuele hostbestanden die hiernaar verwijzen.

   * Als conf.d/rewrites nu een enkel bestand bevat, moet dit worden hernoemd naar rewrite.rules. Vergeet niet om de Include-instructies die naar dat bestand verwijzen in de virtuele hostbestanden aan te passen.

   * Als de map echter meerdere, virtuele hostspecifieke bestanden bevat, moet de inhoud ervan worden gekopieerd naar de Include-instructie in de virtuele hostbestanden die naar deze specifieke bestanden verwijst.

1. **Variabelen controleren**

   1. Open de directory conf.d/variables.

   1. Verwijder alle bestanden met de naam ams_default.vars en verwijder alle Include-instructies in de virtuele hostbestanden die hiernaar verwijzen.

   1. Als conf.d/variables nu een enkel bestand bevat, moet dit worden hernoemd naar custom.vars. Vergeet niet om de Include-instructies die naar dat bestand verwijzen in de virtuele hostbestanden aan te passen.

   1. Als de map echter meerdere, virtuele hostspecifieke bestanden bevat, moet de inhoud ervan worden gekopieerd naar de Include-instructie in de virtuele hostbestanden die naar deze specifieke bestanden verwijst.

1. **Whitelists verwijderen**

   Verwijder de map conf.d/whitelists en verwijder Include-instructies in de virtuele hostbestanden die verwijzen naar een bestand in die submap.

1. **Variabelen vervangen die niet meer beschikbaar zijn**

   In alle virtuele hostbestanden:

   Wijzig de naam van PUBLISH_DOCROOT naar DOCROOT
Verwijder de secties die verwijzen naar variabelen met de naam DISP_ID, PUBLISH_FORCE_SSL of PUBLISH_WHITELIST_ENABLED

1. **Uw status controleren door de validatietool uit te voeren**

   Voer de dispatcher-validator in uw directory uit met de httpd-subopdracht:

   `$ validator httpd`
Als er fouten optreden over ontbrekende Include-bestanden, controleert u of de naam van die bestanden correct is gewijzigd.

   Als u Apache-instructies ziet die op de whitelist staan, verwijdert u deze.

1. **Alle niet-publicatiefarms verwijderen**

   Verwijder elk farmbestand in conf.dispatcher.d/enabled_farms waarbij author, unhealthy, health, lc of flush in de naam voorkomt. Alle farmbestanden in conf.dispatcher.d/available_farms die niet zijn gekoppeld, kunnen ook worden verwijderd.

1. **De naam van farmbestanden wijzigen**

   Alle farms in conf.dispatcher.d/enabled_farms moeten worden hernoemd, zodat ze overeenkomen met het patroon *.farm. Als een farmbestand bijvoorbeeld customerX_farm.any heet, moet u dit hernoemen naar customerX.farm.

1. **Cache controleren**

   Open de directory conf.dispatcher.d/cache.

   Verwijder alle bestanden met het voorvoegsel ams_.

   Als conf.dispatcher.d/cache nu leeg is, kopieert u het bestand conf.dispatcher.d/cache/rules.any vanuit de standaard Dispatcher-configuratie naar deze map. De standaard Dispatcher-configuratie staat in de map src van deze SDK. Vergeet niet om de $include-instructies die verwijzen naar de ams_*_cache.any-regelbestanden in de farmbestanden ook aan te passen.

   Als conf.dispatcher.d/cache nu echter een enkel bestand bevat met het achtervoegsel _cache.any, moet dit worden hernoemd naar rules.any. Vergeet niet om de $include-instructies die naar dat bestand verwijzen in de farmbestanden ook aan te passen.

   Als de map echter meerdere, farmspecifieke bestanden met dat patroon bevat, moet hun inhoud worden gekopieerd naar de $include-instructie in de farmbestanden die naar deze specifieke bestanden verwijst.

   Verwijder elk bestand met het achtervoegsel _invalidate_allowed.any.

   Kopieer het bestand conf.dispatcher.d/cache/default_invalidate_any vanuit de standaard Dispatcher-configuratie naar die locatie.

   Verwijder alle inhoud in de sectie cache/allowedClients voor elk farmbestand en vervang deze door:

   $include &quot;../cache/default_invalidate.any&quot;

1. **Clientheaders controleren**

   Open de directory conf.dispatcher.d/clientheaders.

   Verwijder alle bestanden met het voorvoegsel ams_.

   Als conf.dispatcher.d/clientheaders nu een enkel bestand bevat met het achtervoegsel _clientheaders.any, moet dit worden hernoemd naar clientheaders.any. Vergeet niet om de $include-instructies die naar dat bestand verwijzen in de farmbestanden ook aan te passen.

   Als de map echter meerdere, farmspecifieke bestanden met dat patroon bevat, moet hun inhoud worden gekopieerd naar de $include-instructie in de farmbestanden die naar deze specifieke bestanden verwijst.

   Kopieer het bestand conf.dispatcher/clientheaders/default_clientheaders.any vanuit de standaard Dispatcher-configuratie naar die locatie.

   In elk farmbestand vervangt u elke include-instructie voor clientheaders die er als volgt uitziet:

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"`

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"`

   met de instructie:

   `$include "../clientheaders/default_clientheaders.any"`

1. **Filter controleren**

   * Open de directory conf.dispatcher.d/filters.

   * Verwijder alle bestanden met het voorvoegsel ams_.

   * Als conf.dispatcher.d/filters nu een enkel bestand bevat, moet dit worden hernoemd naar filters.any. Vergeet niet om de $include-instructies die naar dat bestand verwijzen in de farmbestanden ook aan te passen.

   * Als de map echter meerdere, farmspecifieke bestanden met dat patroon bevat, moet hun inhoud worden gekopieerd naar de $include-instructie in de farmbestanden die naar deze specifieke bestanden verwijst.

   * Kopieer het bestand conf.dispatcher/filters/default_filters.any vanuit de standaard Dispatcher-configuratie naar die locatie.

   * In elk farmbestand vervangt u elke include-instructie voor filters die er als volgt uitziet:

   * $include `"/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"`
met de instructie:

      `$include "../filters/default_filters.any"`

1. **Renderingen controleren**

   * Open de directory conf.dispatcher.d/renders.

   * Verwijder alle bestanden in die map.

   * Kopieer het bestand conf.dispatcher.d/renders/default_renders.any vanuit de standaard Dispatcher-configuratie naar die locatie.

   * Verwijder alle inhoud in de sectie renders voor elk farmbestand en vervang deze door:

      `$include "../renders/default_renders.any"`

1. **Virtuele hosts controleren**

   * Wijzig de naam van de directory `conf.dispatcher.d/vhosts to conf.dispatcher.d/virtualhosts` en open de directory.

   * Verwijder alle bestanden met het voorvoegsel `ams_`.

   * Als conf.dispatcher.d/virtualhosts nu een enkel bestand bevat, moet dit worden hernoemd naar virtualhosts .any. Vergeet niet om de $include-instructies die naar dat bestand verwijzen in de farmbestanden ook aan te passen.

   * Als de map echter meerdere, farmspecifieke bestanden met dat patroon bevat, moet hun inhoud worden gekopieerd naar de $include-instructie in de farmbestanden die naar deze specifieke bestanden verwijst.

   * Kopieer het bestand conf.dispatcher/virtualhosts/default_virtualhosts.any vanuit de standaard Dispatcher-configuratie naar die locatie.

   * In elk farmbestand vervangt u elke include-instructie voor filters die er als volgt uitziet:

      `$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"`
met de instructie:

      `$include "../virtualhosts/default_virtualhosts.any"`


1. **Uw status controleren door de validatietool uit te voeren**

   * Voer de dispatcher-validator in uw directory uit met de dispatcher-subopdracht:

      `$ validator dispatcher`

   * Als er fouten optreden over ontbrekende Include-bestanden, controleert u of de naam van die bestanden correct is gewijzigd.

   * Als er fouten optreden met betrekking tot een niet-gedefinieerde variabele `PUBLISH_DOCROOT`, wijzigt u de naam hiervan naar `DOCROOT`.

   * Bij andere fouten bekijkt u de sectie Problemen oplossen in de documentatie over de validatietool.

## Uw configuratie testen met een lokale implementatie {#testing-config-local-deployment}

>[!IMPORTANT]
>
>Voor het testen van uw configuratie met een lokale implementatie is de installatie van Docker vereist.

Met het script `docker_run.sh` in de Dispatcher SDK kunt u testen dat uw configuratie geen andere fouten bevat die pas bij de implementatie optreden:

1. Implementatiegegevens genereren met de validatietool

   `validator full -d out`
Hiermee wordt de volledige configuratie gevalideerd en worden implementatiegegevens gegeneerd

1. Start de Dispatcher in een docker-image met die implementatiegegevens

   Als uw AEM-publicatieserver op uw MacOS-computer wordt uitgevoerd en u luistert naar poort 4503, kunt u de Dispatcher als volgt voor die server starten:

   `$ docker_run.sh out docker.for.mac.localhost:4503 8080`

   Hierdoor wordt de container gestart en is Apache beschikbaar op de lokale poort 8080.

## Uw nieuwe Dispatcher-configuratie gebruiken {#using-dispatcher-config}

Als de validatietool geen problemen meer rapporteert en de dockercontainer wordt gestart zonder fouten of waarschuwingen, kunt u uw configuratie verplaatsen naar een d`ispatcher/src`-submap van uw Git-repository.