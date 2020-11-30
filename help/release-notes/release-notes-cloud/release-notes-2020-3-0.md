---
title: Opmerkingen bij de release 2020.3.0
description: Opmerkingen bij de release 2020.3.0
translation-type: tm+mt
source-git-commit: 3dc0d1d77595f7b3e890fb4b390eef5bcf84ecd8
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 1%

---


# Opmerkingen bij de release voor AEM als Cloud Service 2020.3.0 {#release-notes}

Deze pagina schetst de algemene opmerkingen bij de release voor Experience Manager als Cloud Service 2020.3.0.

## Releasedatum {#release-date}

De datum van de Versie voor Experience Manager als Cloud Service 2020.3.0 is Maart 05, 2020.

## Cloud Manager {#cloud-manager}

Volg deze sectie voor meer informatie over nieuwe functies en de updates voor Cloud Manager in AEM als Cloud Service Release 2020.3.0.

### Wat is er nieuw?{#what-is-new}

* Het logboek voor de bouwstijlstap is nu beschikbaar terwijl de bouwstijlstap loopt.
* Sommige berichten op de pagina van de details van de pijpleidingsuitvoering zijn uitgegeven voor duidelijkheid.

### Bug Fixes  {#bug-fixes}

* Logbestanden voor de aangepaste teststappen en de functionele teststappen voor het product kunnen niet worden gedownload via de gebruikersinterface.
* Toen de git-opslagplaats voor een Cloud Service-programma niet kon worden gemaakt, konden gebruikers met de rol van Implementatiebeheer zich soms niet herstellen van deze fout.
* Bepaalde gebruikersactiviteiten tijdens het maken van een sandboxprogramma kunnen ertoe leiden dat het programma niet wordt gemaakt voordat de niet-productiepijplijn is gemaakt.
* De voorlopige SonarQube-instantie die in de bouwstap wordt gebruikt, kon soms niet binnen de geconfigureerde time-out worden gestart.
* Bij het gelijktijdig maken van ontwikkelomgevingen in hetzelfde Cloud Service-programma kan er een voorwaarde optreden waarbij slechts één hiervan met succes kan worden gemaakt.
* Experience Cloud-meldingen voor programma&#39;s voor Cloud Service werden niet altijd ontvangen.
* In specifieke projecten, zouden de voorwerpen *ResourceResolver altijd moeten worden gesloten* een Null Uitzondering van de Aanwijzer veroorzaken; dit had echter geen invloed op de uitvoering van de pijpleiding .

