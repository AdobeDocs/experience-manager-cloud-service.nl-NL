---
title: Logbestanden openen en beheren
description: Leer hoe u logbestanden kunt openen en beheren om uw ontwikkelingsproces in AEM as a Cloud Service te ondersteunen.
exl-id: f17274ce-acf5-4e7d-b875-75d4938806cd
solution: Experience Manager
feature: Log Files, Developing
role: Admin, Architect, Developer
source-git-commit: bc92ed7acefbbd906b0986ea0b6b96fa6d8422de
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---


# Logbestanden openen en beheren {#manage-logs}

Leer hoe u logbestanden kunt openen en beheren om uw ontwikkelingsproces in AEM as a Cloud Service te ondersteunen.

U kunt tot een lijst van beschikbare logboekdossiers voor het geselecteerde milieu toegang hebben gebruikend de **kaart van Milieu** van de **pagina van het Overzicht** of van de Details van het Milieu pagina.

Logboeken worden zeven dagen bewaard.

## Logbestanden downloaden {#download-logs}

Ga als volgt te werk om logbestanden te downloaden:

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Navigeer aan de **kaart van Milieu&#39;s** van de **pagina van het Overzicht**.

1. Selecteer **Logboeken van de Download** van het ellipsmenu.

   ![ Logboekmenupunt van de Download logboeken ](assets/download-logs1.png)

1. In de **Logboeken van de Download** dialoog, selecteer de aangewezen **Dienst** van het drop-down menu

   ![ de dialoog van Logboeken van de Download ](assets/download-preview.png)

   In het geval dat [ de Extra Gebieden van Publish ](/help/operations/additional-publish-regions.md) voor uw milieu worden toegelaten, zult u elk gebied kunnen selecteren en zijn logboeken afzonderlijk downloaden, zoals hieronder getoond:

   ![ Logboeken van de Download voor extra publiceer gebieden ](assets/download-publish-region-logs.png)

1. Nadat u de service hebt geselecteerd, klikt u op het downloadpictogram naast het logbestand dat u wilt ophalen.

U kunt tot uw logboeken van de **pagina van Milieu &lbrace;ook toegang hebben.**

![ Logs van het scherm van Milieu&#39;s ](assets/download-logs.png)

## Logbestanden via API {#logs-through-api}

Naast het downloaden van logboeken door UI, zijn de logboeken beschikbaar door API en bevel-lijn interface.

Als u de logbestanden voor een specifieke omgeving wilt downloaden, lijkt de opdracht op het volgende.

```shell
$ aio cloudmanager:download-logs --programId 5 1884 author aemerror
```

Ook, kunt u logboeken als bevel-lijn interface staart.

```shell
$ aio cloudmanager:tail-log --programId 5 1884 author aemerror
```

U kunt de volgende opdrachten gebruiken om de milieu-id (1884 in dit voorbeeld) en de beschikbare service- of lognaamaopties te verkrijgen.

```shell
$ aio cloudmanager:list-environments
Environment Id Name                     Type  Description                          
1884           FoundationInternal_dev   dev   Foundation Internal Dev environment  
1884           FoundationInternal_stage stage Foundation Internal STAGE environment
1884           FoundationInternal_prod  prod  Foundation Internal Prod environment
 
 
$ aio cloudmanager:list-available-log-options 1884
Environment Id Service    Name         
1884           author     aemerror     
1884           author     aemrequest   
1884           author     aemaccess    
1884           publish    aemerror     
1884           publish    aemrequest   
1884           publish    aemaccess    
1884           dispatcher httpderror   
1884           dispatcher aemdispatcher
1884           dispatcher httpdaccess
```

### Aanvullende bronnen {#resources}

>[!TIP]
>
>Controle uit [ dit videomiddel ](https://app.frame.io/reviews/28cdf463-b7fc-443b-a54a-93cb7da6567e/dbf158f1-568b-4efc-8fbc-3b241561cbab) om meer over het zuiveren van AEM as a Cloud Service te leren.

Zie de volgende aanvullende bronnen voor meer informatie over de Cloud Manager API en de Adobe I/O CLI:

* [ Cloud Manager API Documentatie ](https://developer.adobe.com/experience-cloud/cloud-manager/)
* [ Adobe I/O CLI ](https://github.com/adobe/aio-cli-plugin-cloudmanager)

Zie de volgende aanvullende bronnen voor meer informatie over logbestanden in AEM as a Cloud Service:

* [ Wolk 5 AEM Logdossiers ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/cloud-5/cloud5-aem-log-files.html?lang=nl-NL)
* [ het Zuiveren AEM as a Cloud Service gebruikend logboeken ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=nl-NL)
