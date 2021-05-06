---
title: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2021.4.0
description: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2021.4.0
feature: Geen informatie
translation-type: tm+mt
source-git-commit: e2d4bb7649fad3ee172c6f049ecfdedc71417ee2
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---


# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager als Cloud Service 2021.4.0 {#release-notes}

Deze pagina bevat de releaseopmerkingen voor Cloud Manager in AEM als Cloud Service 2021.4.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.4.0 is 8 april 2021.
De volgende release is gepland voor 6 mei 2021.

### Wat is er nieuw?{#what-is-new-april}

* UI werkt aan de Add en Edit de werkschema&#39;s van het Programma om het intuïtiever te maken.

* Een gebruiker met vereiste toestemmingen kan het commerciële eindpunt via UI nu voorleggen.

* De variabelen van het milieu kunnen nu aan de specifieke dienst, of auteur of publiceren worden onderworpen. Vereist AEM versie `2021.03.5104.20210328T185548Z` of hoger.

* De **Manage knoop van Git** wordt getoond op de kaart van Pijpleidingen zelfs wanneer geen pijpleidingen zijn gevormd.

* De versie van het AEM projectarchetype dat door de Manager van de Wolk wordt gebruikt is bijgewerkt aan versie 27.

* Projecten in de Adobe I/O Developer Console die door Cloud Manager zijn gemaakt, kunnen niet langer per ongeluk worden bewerkt of verwijderd.

* Wanneer een gebruiker een nieuwe omgeving toevoegt, wordt hem meegedeeld dat een nieuwe omgeving niet naar een andere regio kan worden verplaatst.

* De variabelen van het milieu kunnen nu aan de specifieke dienst, of auteur of publiceren worden onderworpen. Vereist AEM versie 2021.03.5104.20210328T185548Z of hoger.

* Het foutbericht bij het starten van een pijpleiding wanneer een omgeving werd verwijderd, is verduidelijkt.

* OSGi-bundels die door Eclipse-projecten worden geleverd, zijn nu uitgesloten van regel `CQBP-84--dependencies`.

### Opgeloste problemen {#bug-fixes-cm-april}

* Wanneer het uitgeven van de de controlepagina van de Ervaring van een pijpleiding, zal een inputweg die met een schuine streep `( / )` begint niet meer resulteren in het plakken van de stap in wachtende status.

* Wanneer een nieuwe productiepijplijn wordt gecreeerd, als geen de opheffing van de inhoudscontrole door de gebruiker wordt toegevoegd, werd de standaardhomepage niet gecontroleerd.

* De kwesties voor `CloudServiceIncompatibleWorkflowProcess` hadden de onjuiste strengheid in het downloadbare dossier van de uitgave CSV.

* De `Runmode` controle produceerde valse positieven op niet omslagknopen.