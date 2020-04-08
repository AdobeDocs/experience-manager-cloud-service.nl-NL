---
title: Opmerkingen bij de release 2020.3.0
description: Opmerkingen bij de release 2020.3.0
translation-type: tm+mt
source-git-commit: 27225bf4b918f39892ac9ab6f46deb97479f08e8

---


# Opmerkingen bij de release van AEM als Cloud Service 2020.3.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor Experience Manager weergegeven als Cloud Service 2020.3.0.


## Releasedatum {#release-date}

De releasedatum voor Experience Manager als Cloud Service 2020.3.0 is 5 maart 2020.

## Cloud Manager {#cloud-manager}

Volg deze sectie om te weten te komen wat nieuw is en de updates voor Cloud Manager in AEM als Cloud Service Release 2020.3.0.

### Nieuwe functies {#what-is-new}

* Het logboek voor de bouwstijlstap is nu beschikbaar terwijl de bouwstijlstap loopt.
* Sommige berichten op de pagina van de details van de pijpleidingsuitvoering zijn uitgegeven voor duidelijkheid.

### Opgeloste problemen {#bug-fixes}

* Logbestanden voor de aangepaste teststappen en de functionele teststappen voor het product kunnen niet worden gedownload via de gebruikersinterface.
* Wanneer de opslagruimte voor een Cloud Service-programma niet kon worden gemaakt, konden gebruikers met de rol van Deployment Manager zich soms niet herstellen van deze fout.
* Bepaalde gebruikersactiviteiten tijdens het maken van een sandboxprogramma kunnen ertoe leiden dat het maken van het programma mislukt voordat de niet-productiepijplijn is gemaakt.
* De voorlopige SonarQube-instantie die in de stap build werd gebruikt, kon niet zo nu en dan starten binnen de geconfigureerde time-out.
* Bij het gelijktijdig maken van ontwikkelomgevingen in hetzelfde Cloud Service-programma kan er een voorwaarde optreden waarbij slechts één hiervan met succes kon worden gemaakt.
* Experience Cloud-meldingen voor Cloud Service-programma&#39;s zijn niet altijd ontvangen.
* In specifieke projecten, zouden de voorwerpen *ResourceResolver altijd moeten worden gesloten* een Null Uitzondering van de Aanwijzer veroorzaken; dit had echter geen invloed op de uitvoering van de pijpleiding .

