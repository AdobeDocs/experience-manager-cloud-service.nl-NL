---
title: De complexiteit van de overstap naar de cloudservice beoordelen
description: De complexiteit van de overstap naar de cloudservice beoordelen
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# Cloud Readiness Analyzer {#accesing-complexity}

## Overzicht {#overview}

Met de Cloud Readiness Analyzer (CRA) kunt u bestaande AEM-instanties controleren op hun bereidheid om over te stappen op de Cloud Service door patronen te detecteren die:

* Gebruik een AEM 6.x-functie die momenteel niet wordt ondersteund op de Cloud Service

* Overtreden van bepaalde regels die worden beïnvloed door de overstap naar Cloud Service

>[!NOTE]
>De resultaten van de CRA versnellen de beoordeling van de ontwikkelingsinspanning die zal worden vereist om naar de Dienst van de Wolk over te gaan.

## Cloud Readiness Analyzer instellen {#setting-up-cra}

Het CRA wordt vrijgegeven als een pakket dat werkt aan om het even welke bronAEM versies van XX en hierboven, die een beweging aan de Dienst van de Wolk onderzoeken.

Het is beschikbaar op het Portaal van de Distributie van de Software en kan worden geïnstalleerd gebruikend de Manager van het Pakket.

### Cloud Readiness Analyzer gebruiken {#using-cra}

>[!NOTE]
> CRA kan op om het even welke milieu, met inbegrip van lokale ontwikkelingsinstanties lopen.

>[BELANGRIJK]
>Nochtans om het ontdekkingstarief te verhogen en om het even welke vertragingen op bedrijfskritieke instanties te vermijden, wordt het geadviseerd om het op het opvoeren milieu&#39;s in werking te stellen die aan productiegerichten op de gebieden van gebruikerstoepassingen, inhoud en configuraties zo dicht mogelijk zijn

### Uitvoer weergeven op Cloud Readiness Analyzer {#viewing-output-cra}


1. Navigeer naar de AEM-webconsole door naar de webconsoleconfiguratie **van** Adobe Experience Manager te bladeren `https://serveraddress:serverport/system/console/configMgr`.

1. Selecteer Status - Cloud Readiness Analyzer zoals in de onderstaande afbeelding wordt getoond.

1. U kunt de uitvoer ook weergeven via een reactieve tekst of een gewone JSON-interface.

>[!NOTE]
> Zie [Patroondetector](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html) voor meer informatie over deze methoden). Moet deze sectie toevoegen zodra CRA klaar is voor gebruik.

## Volgende stappen voor gereedheid voor de cloud {#the-next-steps}

Voor meer informatie over uw gereedheid voor de cloudservice moet Adobe de uitvoer van de CRA evalueren.

Voer de onderstaande stappen uit om het bestand terug te sturen:

1. Navigeer naar de AEM-webconsole en download het xx-bestand, zoals in de onderstaande afbeelding wordt getoond.

1. Open een DayCare-ticket om het bestand naar Adobe te verzenden door:
   1. Logboekregistratie van een ondersteuningsticket in de Dagverzorging, getiteld **Cloud Readiness Analyzer Output**
   1. Een uitvoerbestand aan het ticket koppelen

