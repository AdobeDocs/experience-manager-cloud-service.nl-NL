---
title: Logbestanden openen en beheren
description: Leer hoe u logboeken kunt openen en beheren om uw ontwikkelingsproces in AEM as a Cloud Service te ondersteunen.
exl-id: f17274ce-acf5-4e7d-b875-75d4938806cd
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 3%

---


# Logbestanden openen en beheren {#manage-logs}

Leer hoe u logboeken kunt openen en beheren om uw ontwikkelingsproces in AEM as a Cloud Service te ondersteunen.

U kunt een lijst met beschikbare logbestanden voor de geselecteerde omgeving openen met de opdracht **Omgevingen** kaart van **Overzicht** pagina of pagina Omgevingsdetails.

## Logbestanden downloaden {#download-logs}

Ga als volgt te werk om logbestanden te downloaden.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Omgevingen** kaart van **Overzicht** pagina.

1. Selecteren **Logbestanden downloaden** in het ovaalmenu.

   ![Menu-item voor logbestanden downloaden](assets/download-logs1.png)

1. In de **Logbestanden downloaden** selecteert u de gewenste **Service** in het keuzemenu

   ![Het dialoogvenster Logbestanden downloaden](assets/download-preview.png)

1. Nadat u de service hebt geselecteerd, klikt u op het downloadpictogram naast het logbestand dat u wilt ophalen.

U kunt uw logbestanden ook openen via het dialoogvenster **Omgevingen** pagina.

![Logbestanden van het scherm Environment](assets/download-logs.png)

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

Zie de volgende aanvullende bronnen voor meer informatie over de API en Adobe I/O CLI van Cloud Manager:

* [Documentatie voor API voor cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/)
* [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager)
