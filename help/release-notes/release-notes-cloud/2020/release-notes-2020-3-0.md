---
title: Opmerkingen bij de release 2020.3.0
description: Opmerkingen bij de release 2020.3.0
exl-id: 0393c789-3999-4e51-be83-269d6eabd3f3
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 1%

---

# Opmerkingen bij de release voor AEM as a Cloud Service versie 2020.3.0 {#release-notes}

Deze pagina schetst de algemene opmerkingen bij de release voor Experience Manager as a Cloud Service 2020.3.0.

## Releasedatum {#release-date}

De Releasedatum voor Experience Manager as a Cloud Service 2020.3.0 is 5 maart 2020.

## Cloud Manager {#cloud-manager}

Volg deze sectie voor meer informatie over nieuwe functies en de updates voor Cloud Manager in AEM as a Cloud Service release 2020.3.0.

### Wat is er nieuw? {#what-is-new}

* Het logboek voor de bouwstijlstap is nu beschikbaar terwijl de bouwstijlstap loopt.
* Sommige berichten op de pagina van de details van de pijpleidingsuitvoering zijn uitgegeven voor duidelijkheid.

### Opgeloste problemen  {#bug-fixes}

* Logbestanden voor de aangepaste teststappen en de functionele teststappen voor het product kunnen niet worden gedownload via de gebruikersinterface.
* Toen de git-opslagplaats voor een Cloud Service-programma niet kon worden gemaakt, konden gebruikers met de rol van Implementatiebeheer zich soms niet herstellen van deze fout.
* Bepaalde gebruikersactiviteiten tijdens het maken van een sandboxprogramma kunnen ertoe leiden dat het maken van het programma mislukt voordat de niet-productiepijplijn is gemaakt.
* De voorlopige SonarQube-instantie die in de bouwstap wordt gebruikt, kon soms niet binnen de geconfigureerde time-out worden gestart.
* Bij het gelijktijdig maken van ontwikkelomgevingen in hetzelfde Cloud Service-programma kan er een voorwaarde optreden waarbij slechts één hiervan met succes kan worden gemaakt.
* Experience Cloud-meldingen voor programma&#39;s voor Cloud Service werden niet altijd ontvangen.
* Bij specifieke projecten *ResourceResolver-objecten moeten altijd worden gesloten* een Null-aanwijzeruitzondering zou veroorzaken; dit had echter geen invloed op de uitvoering van de pijpleiding .
