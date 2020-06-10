---
title: Cloud Readiness Analyzer gebruiken
description: Cloud Readiness Analyzer gebruiken
translation-type: tm+mt
source-git-commit: 3d818278c53f3d3b4c5b53aa5b78d06d876bf05f
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 5%

---


# Cloud Readiness Analyzer gebruiken {#using-cloud-readiness-analyzer}

## Belangrijke overwegingen voor het gebruik van Cloud Readiness Analyzer {#imp-considerations}

Volg de onderstaande sectie om inzicht te krijgen in de belangrijke overwegingen bij het uitvoeren van de Cloud Readiness Analyzer (CRA):

* CRA wordt ondersteund op AEM-broninstanties met versie 6.1 en hoger.
* CRA kan op om het even welk milieu lopen.

   >[!NOTE]
   >Om het ontdekkingstarief te verhogen en om het even welke vertragingen op bedrijfskritieke instanties te vermijden, wordt het geadviseerd om CRA op de bronauteur het opvoeren milieu&#39;s in werking te stellen die zo dicht mogelijk aan productiegroepen op de gebieden van aanpassingen, configuraties, inhoud en gebruikerstoepassingen zijn. Het kan ook worden uitgevoerd op een kloon van de publicatieomgeving.

## Beschikbaarheid {#availability}

De Cloud Readiness Analyzer (CRA) kan als zip- dossier van het portaal van de Distributie van de Software worden gedownload. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager).

>[!NOTE]
>Download de Cloud Readiness Analyzer (CRA) van *in behandeling*.

## De Cloud Readiness Analyzer uitvoeren {#running-tool}

Ga als volgt te werk om Cloud Readiness Analyzer uit te voeren:

1. Select the Adobe Experience Manager and navigate to tools -> **Operations** -> **Cloud Readiness Analyzer**.

### De resultaten bekijken {#viewing-the-results}

Er zijn twee manieren om de output van CRA te bekijken:

1. Het georganiseerde rapport gebruiken

   >[!NOTE]
   >Het georganiseerde rapport is beschikbaar op AEM versie 6.3 en hoger.

Verwijs naar de Planning en Status van het Document van CRA om belangrijkheidsniveaus in het rapport te beschrijven

1. De uitvoer van het CRA (kan worden gebruikt met AEM versie 6.1 en hoger) weergeven:

   1. Navigeer naar de AEM-webconsole door ernaar te bladeren.

   1. Selecteer Status - Cloud Readiness Analyzer zoals in de onderstaande afbeelding wordt getoond.

#### Belangrijkste niveaus in het rapport {#importance-levels}

In de volgende tabel wordt de betekenis van de verschillende belangrijke niveaus voor de analyse van patroondetectoren en gereedheid voor cloud beschreven.

| Importniveau | Beschrijving |
|--- |--- |
| INFO/0 | Deze bevinding wordt ter informatie verstrekt. |
| ADVISORY/1 | Deze bevinding is mogelijk een upgradeprobleem. Verdere onderzoeken worden aanbevolen. |
| MAJOR/2 | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt. |
| KRITIEK/3 | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt om functieverlies of prestatieverlies te voorkomen. |