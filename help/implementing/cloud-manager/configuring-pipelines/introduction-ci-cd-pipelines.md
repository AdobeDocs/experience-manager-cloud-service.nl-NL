---
title: CI-CD-pijpleidingen
description: CI-CD-pijpleidingen
index: false
source-git-commit: 1887cc7374ece840b2dcca4482924b14c4793567
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---


# Cloud Manager CI-CD Pipelines {#intro-cicd}

## Inleiding {#introduction}

Een CI/CD pijpleiding in de Manager van de Wolk kan door één of andere soort gebeurtenis, zoals een trekkingsverzoek van een broncodebewaarplaats worden teweeggebracht, namelijk een codeverandering, of één of ander soort regelmatig programma om een versiecadence aan te passen.

>[!NOTE]
>Om uw pijpleiding te vormen, moet u:
>* bepaal de trekker die de pijpleiding zal beginnen
>* de parameters definiëren die de productie-implementatie beheersen
>* configureren van de testparameters voor de prestaties


In Cloud Manager zijn er twee typen pijplijn:

* [Productiepijpleiding](#prod-pipeline)
* [Niet-productiepijpleiding](#non-prod-pipeline)

## Productiepijpleiding {#prod-pipeline}

Een productiepijpleiding is een doelpijpleiding die een reeks georkestreerde stappen omvat om broncode helemaal in productie te nemen. De stappen omvatten eerst het bouwen, verpakken, testen, valideren en implementeren in alle Stage-omgeving. Een productiepijpleiding kan natuurlijk alleen worden toegevoegd als een productie- en werkgebiedomgeving is ingesteld.

Verwijs naar het Vormen van de Pijpleiding van de Productie voor meer details.


## Niet-productiepijpleiding {#non-prod-pipeline}

Een pijpleiding van de niet-Productie richt code-kwaliteit scans in werking te stellen of broncode in een ontwikkelomgeving op te stellen.

Raadpleeg de pijplijnen Niet-productie en Alleen kwaliteit van code voor meer informatie.
