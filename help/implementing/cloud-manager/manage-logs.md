---
title: Logbestanden beheren - Cloud Service
description: Logbestanden beheren - Cloud Service
exl-id: f17274ce-acf5-4e7d-b875-75d4938806cd
source-git-commit: 8a70a343be8a6843436f1df26adae5b1935ad4c3
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 13%

---

# Logbestanden openen en beheren {#manage-logs}

Gebruikers kunnen een lijst met beschikbare logbestanden voor de geselecteerde omgeving openen met de milieucaart. Gebruikers hebben toegang tot een lijst met beschikbare logbestanden voor de geselecteerde omgeving.

## Logbestanden {#download-logs} downloaden

Deze bestanden kunnen worden gedownload via de gebruikersinterface, via de **Environment**-kaart op de pagina **Overview**:

![](assets/download-logs1.png)

Of, van de pagina van de Details van het Milieu:

![](assets/download-logs.png)

>[!NOTE]
>Ongeacht waar het wordt geopend, verschijnt hetzelfde dialoogvenster en kan een afzonderlijk logbestand worden gedownload.

![](assets/download-logs2.png)

## Logbestanden voor voorvertoningsservice downloaden {#download-preview-service}

Volg de onderstaande stappen om logbestanden voor de Voorvertoningsservice te downloaden

1. Navigeer naar **Environment**-kaart op de pagina **Overzicht** van Cloud Manager.

1. Selecteer **Logbestanden downloaden** in **..**-menu.

1. Selecteer **Voorvertoning** of **Voorvertoning Dispatcher** in het vervolgkeuzemenu **Service**, gevolgd door een klik op het downloadpictogram.

   >[!NOTE]
   >Deze actie kan ook van de de detailpagina van het Milieu worden verwezenlijkt.

   ![](assets/download-preview.png)


## Hiermee wordt de API {#logs-through-api} doorlopen

Naast het downloaden van logboeken door UI, zullen de logboeken door API en de Interface van de Lijn van het Bevel beschikbaar zijn.

Als u bijvoorbeeld de logbestanden voor een specifieke omgeving wilt downloaden, is de opdracht iets apart van de regels van

```java
$ aio cloudmanager:download-logs --programId 5 1884 author aemerror
```

Met de volgende opdracht kunt u logboeken trappen:

```java
$ aio cloudmanager:tail-log --programId 5 1884 author aemerror
```

Voor het verkrijgen van de milieu-id (in dit geval 1884) en de beschikbare service- of lognaamoties kunt u het volgende gebruiken:

```java
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

>[!NOTE]
>Hoewel **Logboekdownloads** beschikbaar blijven via zowel de gebruikersinterface als de API, is **Logboektailing** alleen beschikbaar via API/CLI.

### Aanvullende bronnen {#resources}

Raadpleeg de volgende aanvullende bronnen voor meer informatie over de API en Adobe I/O CLI van Cloud Manager:

* [Documentatie voor API voor cloud Manager](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html)
* [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager)
