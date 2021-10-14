---
title: CI-CD-pijpleidingen
description: CI-CD-pijpleidingen
index: false
source-git-commit: 16e3280d7eaf53d8f944a60ec93b21c6676f0133
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---


# Cloud Manager CI-CD Pipelines {#intro-cicd}

## Inleiding {#introduction}

>[!NOTE]
>Een CI/CD pijpleiding in de Manager van de Wolk wordt teweeggebracht door een gebeurtenis, zoals een trekkingsverzoek van een broncodebewaarplaats die, een codeverandering, of een regelmatig programma is om een versieaanhouding aan te passen.

Om uw pijpleiding te vormen, moet u:
* bepaal de trekker die de pijpleiding zal beginnen
* de parameters definiëren die de productie-implementatie beheersen
* configureren van de testparameters voor de prestaties

In Cloud Manager zijn er twee typen pijplijn:

* [Productiepijpleiding](#prod-pipeline)
* [Niet-productiepijpleiding](#non-prod-pipeline)

## Productiepijpleiding {#prod-pipeline}

Een productiepijpleiding is een doelpijpleiding die een reeks georkestreerde stappen omvat om broncode helemaal in productie te nemen. De stappen omvatten eerst het bouwen, verpakken, testen, valideren en implementeren in alle Stage-omgeving. Een productiepijpleiding kan natuurlijk alleen worden toegevoegd als een productie- en werkgebiedomgeving is ingesteld.

>[!NOTE]
>Verwijs naar het Vormen van de Pijpleiding van de Productie voor meer details.


## Niet-productiepijpleiding {#non-prod-pipeline}

Een pijpleiding van de niet-Productie richt code-kwaliteit scans in werking te stellen of broncode in een ontwikkelomgeving op te stellen.

>[!NOTE]
>Raadpleeg de pijplijnen Niet-productie en Alleen kwaliteit van code voor meer informatie.
