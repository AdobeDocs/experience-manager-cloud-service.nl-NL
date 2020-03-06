---
title: Opmerkingen bij vrijgave 2020.3.0
description: Opmerkingen bij vrijgave 2020.3.0
translation-type: tm+mt
source-git-commit: bcbb50f467a0e3b3047e2bb872a8fe39a9f02a1a

---


# De Nota&#39;s van de versie voor AEM als Dienst van de Wolk 2020.3.0 {#release-notes}

De volgende sectie schetst de algemene Nota&#39;s van de Versie voor de Manager van de Ervaring als Dienst 2020.3.0 van de Wolk.

## Cloud Manager {#cloud-manager}

De datum van de Versie van de Manager van de Wolk 2020.3.0 is Maart 05, 2020.

Volg deze sectie om over te leren wat nieuw is en de updates voor Versie van de Manager van de Wolk 2020.3.0.

### Nieuw {#what-is-new}

* Het logboek voor de bouwstijlstap is nu beschikbaar terwijl de bouwstijlstap loopt.
* Sommige berichten op de de detailpagina van de pijpleidingsuitvoering zijn uitgegeven voor duidelijkheid.

### Bug Fixes {#bug-fixes}

* De dossiers van het logboek voor de douane en product functionele teststappen konden niet door UI worden gedownload.
* Toen de gegevensopslag voor een Cloud Service-programma niet kon worden gemaakt, konden gebruikers in de rol Deployment Manager zich soms niet herstellen van deze fout.
* Bepaalde gebruikersactiviteiten tijdens het creëren van een zandbakprogramma konden de programmaverwezenlijking veroorzaken om te ontbreken alvorens de niet productiepijpleiding werd gecreeerd.
* De tijdelijke instantie SonarQube die in de bouwstijlstap wordt gebruikt was nu en dan verzuimd om binnen de gevormde onderbreking te beginnen.
* Gelijktijdige creatie van ontwikkelomgevingen in hetzelfde Cloud Service-programma kon een voorwaarde krijgen waarbij slechts één omgeving succesvol kon worden gemaakt.
* De Cloudmeldingen voor cloudserviceprogramma&#39;s zijn niet altijd ontvangen.
* In specifieke projecten, zouden de voorwerpen *ResourceResolver altijd moeten worden gesloten* een Volledige Uitzondering van de Wijzer veroorzaken; dit had echter geen gevolgen voor de uitvoering van pijpleidingen .

