---
title: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.3.0
description: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.3.0
translation-type: tm+mt
source-git-commit: ca690144a8254d5ffba354f0f96d9ef1c5202533
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager als Cloud Service 2020.3.0 {#release-notes}

Deze pagina bevat de releaseopmerkingen voor Cloud Manager in AEM als Cloud Service 2020.3.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2020.3.0 is 5 maart 2020.

### Wat is er nieuw?{#what-is-new}

* Het logboek voor de bouwstijlstap is nu beschikbaar terwijl de bouwstijlstap loopt.
* Sommige berichten op de pagina van de details van de pijpleidingsuitvoering zijn uitgegeven voor duidelijkheid.

### Opgeloste problemen {#bug-fixes}

* Logbestanden voor de aangepaste teststappen en de functionele teststappen voor het product kunnen niet worden gedownload via de gebruikersinterface.
* Toen de git-opslagplaats voor een Cloud Service-programma niet kon worden gemaakt, konden gebruikers met de rol van Implementatiebeheer zich soms niet herstellen van deze fout.
* Bepaalde gebruikersactiviteiten tijdens het maken van een sandboxprogramma kunnen ertoe leiden dat het programma niet wordt gemaakt voordat de niet-productiepijplijn is gemaakt.
* De voorlopige SonarQube-instantie die in de bouwstap wordt gebruikt, kon soms niet binnen de geconfigureerde time-out worden gestart.
* Bij het gelijktijdig maken van ontwikkelomgevingen in hetzelfde Cloud Service-programma kan er een voorwaarde optreden waarbij slechts één hiervan met succes kan worden gemaakt.
* Experience Cloud-meldingen voor programma&#39;s voor Cloud Service werden niet altijd ontvangen.
* In specifieke projecten, zouden de *voorwerpen ResourceResolver altijd moeten worden gesloten* een Uitzondering van de Wijzerplaat van de Null veroorzaken; dit had echter geen invloed op de uitvoering van de pijpleiding .