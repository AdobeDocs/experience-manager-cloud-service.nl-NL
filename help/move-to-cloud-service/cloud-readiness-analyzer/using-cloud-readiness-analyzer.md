---
title: Cloud Readiness Analyzer gebruiken
description: Cloud Readiness Analyzer gebruiken
translation-type: tm+mt
source-git-commit: 47773a56f8bb24342281068a8c4d03d6edfb9277
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 4%

---


# Cloud Readiness Analyzer gebruiken {#using-cloud-readiness-analyzer}

## Belangrijke overwegingen voor het gebruik van Cloud Readiness Analyzer {#imp-considerations}

Volg de onderstaande sectie om inzicht te krijgen in de belangrijke overwegingen bij het uitvoeren van de Cloud Readiness Analyzer (CRA):

* CRA wordt ondersteund op AEM-broninstanties met versie 6.1 en hoger
* CRA kan in elke omgeving worden uitgevoerd (bij voorkeur in *een werkgebiedomgeving* )

   >[!NOTE]
   >Om het ontdekkingstarief te verhogen en om het even welke vertragingen op bedrijfskritieke instanties te vermijden, wordt het geadviseerd om CRA op de bronauteur het opvoeren milieu&#39;s in werking te stellen die zo dicht mogelijk aan productiegroepen op de gebieden van aanpassingen, configuraties, inhoud en gebruikerstoepassingen zijn. Het kan ook worden uitgevoerd op een kloon van de *publicatieomgeving* .

## Beschikbaarheid {#availability}

De Cloud Readiness Analyzer kan als zip- dossier van het portaal van de Distributie van de Software worden gedownload. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager).

>[!NOTE]
>Download de Cloud Readiness Analyzer van het Portaal van de Distributie van de Software *hangend*.

## De Cloud Readiness Analyzer uitvoeren {#running-tool}

Ga als volgt te werk om Cloud Readiness Analyzer uit te voeren:

1. Select the Adobe Experience Manager and navigate to tools -> **Operations** -> **Cloud Readiness Analyzer**.

### De resultaten bekijken {#viewing-the-results}

>[!IMPORTANT]
>The reports generated from Cloud Readiness Analyzer are based on Pattern Detectors. Raadpleeg [Patroondetectoren](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html) voor meer informatie.

There are two ways to view the output from the Cloud Readiness Analyzer:

1. **Using the Organized Report**

   >[!NOTE]
   >Het georganiseerde rapport is beschikbaar op AEM versie 6.3 en hoger.

   Of

1. **Viewing the output of the CRA**

   Voer de onderstaande stappen uit om de uitvoer van de Cloud Readiness Analyzer weer te geven:

   >[!NOTE]
   >De onderstaande stappen zijn van toepassing op AEM versie 6.1 en hoger.

   1. Navigeer naar de **AEM-webconsole** met `https://serveraddress:serverport/system/console/configMgr`.

   1. Selecteer **Status - Patroondetector** , zoals in de onderstaande afbeelding wordt getoond.

#### Het rapport bekijken in AEM 6.1 Instanties {#aem-instances-report}

U kunt het CSV-rapport voor AEM 6.1 downloaden. Dit is in behandeling.

#### Belangrijkste niveaus in het rapport {#importance-levels}

In de volgende tabel wordt de betekenis van de verschillende belangrijke niveaus voor de analyse van patroondetectoren en gereedheid voor cloud beschreven.

| Importniveau | Beschrijving |
|--- |--- |
| INFO/0 | Deze bevinding wordt ter informatie verstrekt. |
| ADVISORY/1 | Deze bevinding is mogelijk een upgradeprobleem. Verdere onderzoeken worden aanbevolen. |
| MAJOR/2 | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt. |
| KRITIEK/3 | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt om functieverlies of prestatieverlies te voorkomen. |