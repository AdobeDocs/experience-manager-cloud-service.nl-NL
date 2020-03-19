---
title: Logbestanden beheren - Cloud Service
description: Logbestanden beheren - Cloud Service
translation-type: tm+mt
source-git-commit: 5913151c4e2bebb84bd68377d64f43e07caaf2dd

---


# Logbestanden openen en beheren {#manage-logs}

Gebruikers kunnen een lijst met beschikbare logbestanden voor de geselecteerde omgeving openen met de milieucaart.  Gebruikers hebben toegang tot een lijst met beschikbare logbestanden voor de geselecteerde omgeving.

Deze bestanden kunnen worden gedownload via de gebruikersinterface van de pagina **Overzicht** .

![](assets/manage-logs1.png)

Of op de pagina **Omgevingen** :

![](assets/manage-logs2.png)

>[!Nofferte]
>Ongeacht waar het wordt geopend, verschijnt hetzelfde dialoogvenster en kan een afzonderlijk logbestand worden gedownload.

![](assets/manage-logs3.png)


## Logbestanden via API {#logs-thorugh-api}

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

>[!Nofferte]
>Hoewel **Logboekdownloads** beschikbaar blijven via zowel de gebruikersinterface als de API, is **Logboektailing** alleen beschikbaar via API/CLI.

### Additional Resources {#resources}

Raadpleeg de volgende aanvullende bronnen voor meer informatie over de Cloud Manager API en Adobe I/O CLI:

* [Documentatie voor API voor cloud Manager](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html)
* [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager)