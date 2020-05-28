---
title: Een AMS converteren naar een Adobe Experience Manager als een Cloud Service Dispatcher Configuration
description: Een AMS converteren naar een Adobe Experience Manager als een Cloud Service Dispatcher Configuration
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '1342'
ht-degree: 0%

---


# Een AMS converteren naar een Adobe Experience Manager (AEM) als een Cloud Service Dispatcher Configuration

## Inleiding {#introduction}

Deze sectie biedt stapsgewijze instructies voor het omzetten van een AMS-configuratie.

>[!NOTE]
>Hierbij wordt ervan uitgegaan dat u een archief hebt met een structuur die vergelijkbaar is met de structuur die wordt beschreven in [Uw Dispatcher Configurations](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html)beheren.

## Stappen voor het omzetten van een AMS in AEM als configuratie van een serviceverzender voor de cloud

1. **Het archief extraheren en een eventueel voorvoegsel verwijderen**

   Extraheer het archief naar een map en zorg ervoor dat de directe submappen beginnen met conf, conf.d, conf.dispatcher.d en conf.modules.d. Als ze dat niet doen, verplaats ze omhoog in de hiërarchie.

1. **Ongebruikte submappen en bestanden verwijderen**

   Verwijder de submappen conf en conf.modules.d en de bestanden die overeenkomen met conf.d/*.conf.

1. **Alle niet-gepubliceerde virtuele hosts verwijderen**

1. **Verwijder een virtueel hostbestand**

   In conf.d/enabled_hosts die de naam auteur, ongezond, gezondheid, lc of flush heeft. Alle virtuele hostbestanden in conf.d/available_hosts die niet zijn gekoppeld, kunnen ook worden verwijderd.

1. Verwijder of becommentariër virtuele gastheersecties die niet naar haven 80 verwijzen

   Als u nog secties in uw virtuele gastheerdossiers hebt die uitsluitend naar andere havens dan haven 80 verwijzen, b.v.

   `<VirtualHost *:443>`
   `...`
   `</VirtualHost>`
verwijderen of opmerkingen maken. Instructies in deze secties worden niet verwerkt, maar als u ze in de buurt houdt, kunt u ze waarschijnlijk nog steeds zonder effect bewerken. Dat is verwarrend.

1. **Herschrijvingen controleren**

   * Voer de directory conf.d/rewrites in.

   * Verwijder om het even welk dossier genoemd base_rewrite.rules en xdoor:sturen_forcessl_rewrite.rules en herinner me om omvatten verklaringen in de virtuele gastheerdossiers te verwijderen die naar hen verwijzen.

   * Als conf.d/rewrites nu één enkel dossier bevat, zou het moeten worden anders genoemd om.rules te herschrijven en vergeet niet om de Include verklaringen aan te passen die naar dat dossier verwijzen in de virtuele gastheerdossiers eveneens.

   * Als de map echter meerdere, virtuele hostspecifieke bestanden bevat, moet de inhoud ervan worden gekopieerd naar de instructie Include die naar deze bestanden in de virtuele hostbestanden verwijst.

1. **Variabelen controleren**

   1. Voer de directory conf.d/variables in.

   1. Verwijder alle bestanden met de naam ams_default.vars en vergeet niet om de instructies Include in de virtuele hostbestanden te verwijderen die naar deze instructies verwijzen.

   1. Als conf.d/variables nu één enkel dossier bevat, zou het aan custom.vars moeten worden anders genoemd en vergeet niet ook om de Include verklaringen aan te passen die naar dat dossier in de virtuele gastheerdossiers verwijzen.

   1. Als de map echter meerdere, virtuele hostspecifieke bestanden bevat, moet de inhoud ervan worden gekopieerd naar de instructie Include die naar deze bestanden in de virtuele hostbestanden verwijst.

1. **Witlijsten verwijderen**

   Verwijder de map conf.d/whitelists en verwijder Include-instructies in de virtuele hostbestanden die verwijzen naar een bestand in die submap.

1. **Variabelen vervangen die niet meer beschikbaar zijn**

   In alle virtuele hostbestanden:

   Naam van PUBLISH_DOCROOT wijzigen in DOCROOTRemove-secties die verwijzen naar variabelen met de naam DISP_ID, PUBLISH_FORCE_SSL of PUBLISH_WHITELIST_ENABLED

1. **Controleer uw status door validator uit te voeren**

   Voer de verzender-validator in uw map uit met de httpd-subopdracht:

   `$ validator httpd`
Als er fouten optreden bij ontbrekende include-bestanden, controleert u of de naam van die bestanden correct is gewijzigd.

   Als u Apache-instructies ziet die niet zijn gewhitelist, verwijdert u deze.

1. **Alle niet-publicatiebedrijven verwijderen**

   Verwijder om het even welk landbouwbedrijfdossier in conf.dispatcher.d/enabled_farm die auteur, ongezond, gezondheid, lc of flush in zijn naam heeft. Alle landbouwbedrijfdossiers in conf.dispatcher.d/available_farm die niet met worden verbonden kunnen eveneens worden verwijderd.

1. **Namen van landbouwbestanden wijzigen**

   Alle landbouwbedrijven in conf.dispatcher.d/enabled_farm moeten worden anders genoemd om het patroon *.farm aan te passen, zodat zou een landbouwbedrijfdossier genoemd customerX_farm.any anders moeten worden genoemd customerX.farm.

1. **Cache controleren**

   Voer de map conf.dispatcher.d/cache in.

   Verwijder om het even welk dossier vooraf bevestigde ams_.

   Als conf.dispatcher.d/cache nu leeg is, kopieert u het bestand conf.dispatcher.d/cache/rules.any van de standaardconfiguratie van de verzender naar deze map. De standaardconfiguratie voor de verzender vindt u in de mapbron van deze SDK. Vergeet niet om $include verklaringen aan te passen die naar de ams_*_cache.any regeldossiers in de landbouwbedrijfdossiers verwijzen eveneens.

   Als in plaats daarvan conf.dispatcher.d/cache nu één enkel dossier met achtervoegsel _cache.any bevat, zou het aan rules.any moeten worden anders genoemd en vergeet niet om $include verklaringen aan te passen die naar dat dossier in de landbouwbedrijfdossiers verwijzen eveneens.

   Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, zou hun inhoud aan $include verklaring moeten worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

   Verwijder elk bestand met het achtervoegsel _invalidate_allowed.any.

   Kopieer het bestand conf.dispatcher.d/cache/default_invalidate_any van de standaardconfiguratie van de verzender naar die locatie.

   In elk landbouwbedrijfdossier, verwijder om het even welke inhoud in de cache/allowedClients sectie en vervang het met:

   $include &quot;../cache/default_invalidate.any&quot;

1. **Clientkoppen controleren**

   Voer de map conf.dispatcher.d/clientheaders in.

   Verwijder om het even welk dossier vooraf bevestigde ams_.

   Als conf.dispatcher.d/clientheaders nu één enkel dossier met achtervoegsel _clientheaders.any bevat, zou het aan client.any moeten worden anders genoemd en niet vergeet om $include verklaringen aan te passen die naar dat dossier in de landbouwbedrijfdossiers verwijzen eveneens.

   Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, zou hun inhoud aan $include verklaring moeten worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

   Kopieer de bestandconf.dispatcher/clientheaders/default_clientheaders.any.

   In elk landbouwbedrijfdossier, vervang om het even welke cliënt omvat verklaringen die als volgt kijken:

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"`

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"`

   met de verklaring:

   `$include "../clientheaders/default_clientheaders.any"`

1. **Filter controleren**

   * Voer de map conf.dispatcher.d/filters in.

   * Verwijder om het even welk dossier vooraf bevestigde ams_.

   * Als conf.dispatcher.d/filters nu één enkel dossier bevat zou het aan filters.any moeten worden anders genoemd en vergeet niet om $include verklaringen aan te passen die naar dat dossier in de landbouwbedrijfdossiers verwijzen eveneens.

   * Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, zou hun inhoud aan $include verklaring moeten worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

   * Kopieer de bestandconf.dispatcher/filters/default_filters.any.

   * In elk landbouwbedrijfdossier, vervang om het even welke filter omvat verklaringen die als volgt kijken:

   * $include `"/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"`met de instructie:

      `$include "../filters/default_filters.any"`

1. **Renderingen controleren**

   * Voer de map conf.dispatcher.d/renders in.

   * Verwijder alle bestanden in die map.

   * Kopieer het bestand conf.dispatcher.d/renders/default_renders.any van de standaardconfiguratie van de verzender naar die locatie.

   * In elk landbouwbedrijfdossier, verwijder om het even welke inhoud in de renderensectie en vervang het met:

      `$include "../renders/default_renders.any"`

1. **Virtuele hosts controleren**

   * Wijzig de naam van de map `conf.dispatcher.d/vhosts to conf.dispatcher.d/virtualhosts` en voer deze in.

   * Verwijder alle vooraf ingestelde bestanden `ams_`.

   * Als conf.dispatcher.d/virtualhosts nu één bestand bevat, moet de naam worden gewijzigd in virtueel hosts.any en moet u de $include-instructies die verwijzen naar dat bestand ook in de bestanden op de boerderij aanpassen.

   * Als de omslag echter veelvoudige, landbouwbedrijfspecifieke dossiers met dat patroon bevat, zou hun inhoud aan $include verklaring moeten worden gekopieerd die naar hen in de landbouwbedrijfdossiers verwijst.

   * Kopieer de bestandconf.dispatcher/virtualhosts/default_virtualhosts.any.

   * In elk landbouwbedrijfdossier, vervang om het even welke filter omvat verklaringen die als volgt kijken:

      `$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"`
met de verklaring:

      `$include "../virtualhosts/default_virtualhosts.any"`


1. **Controleer uw status door validator uit te voeren**

   * Voer de verzender-validator in uw map uit met de subopdracht van de verzender:

      `$ validator dispatcher`

   * Als er fouten optreden bij ontbrekende include-bestanden, controleert u of de naam van die bestanden correct is gewijzigd.

   * Als er fouten optreden met betrekking tot een niet-gedefinieerde variabele, wijzigt u de naam `PUBLISH_DOCROOT`in `DOCROOT`.

   * Zie de sectie Problemen oplossen in de documentatie over het validatieprogramma voor elke andere fout.

## Uw configuratie testen met een lokale implementatie {#testing-config-local-deployment}

>[!IMPORTANT]
> Voor het testen van uw configuratie met een lokale implementatie is de installatie van Docker vereist.

Gebruikend het manuscript `docker_run.sh` in Dispatcher SDK, kunt u testen dat uw configuratie geen andere fout bevat die slechts in plaatsing zou verschijnen:

1. Implementatiegegevens genereren met de validator

   `validator full -d out`
Dit bevestigt de volledige configuratie en produceert plaatsingsinformatie binnen uit

1. Start de dispatcher in een docker-image met die implementatiegegevens

   Als uw AEM-publicatieserver op uw MacOS-computer wordt uitgevoerd en u luistert naar poort 4503, kunt u de dispatcher als volgt voor die server starten:

   `$ docker_run.sh out docker.for.mac.localhost:4503 8080`

   Dit zal de container beginnen en Apache op lokale haven 8080 blootstellen.

## De nieuwe configuratie van de verzender gebruiken {#using-dispatcher-config}

Als de validator geen problemen meer rapporteert en de dockercontainer wordt gestart zonder fouten of waarschuwingen, kunt u uw configuratie verplaatsen naar een D`ispatcher/src` -submap van uw it-opslagplaats.