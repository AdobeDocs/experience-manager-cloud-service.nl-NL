---
title: CI-CD-pijpleidingen
description: CI-CD-pijpleidingen
index: false
source-git-commit: e51b995aebb053f38cb99879be70e23447f543c0
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---


# Cloud Manager CI-CD Pipelines {#intro-cicd}

In Cloud Manager zijn er twee typen pijplijn:

* **Productiepijpleiding**
* **Niet-productiepijpleiding**

## Productiepijpleiding {#prod-pipeline}

Een productiepijpleiding is een doelpijpleiding die een reeks georkestreerde stappen omvat om broncode helemaal in productie te nemen. De stappen omvatten eerst het bouwen, verpakken, testen, valideren en implementeren in alle Stage-omgeving. Een productiepijpleiding kan natuurlijk alleen worden toegevoegd als een productie- en werkgebiedomgeving is ingesteld.

>[!NOTE]
>Verwijs naar het Vormen van de Pijpleiding van de Productie voor meer details.


## Niet-productiepijpleiding {#non-prod-pipeline}

Een pijpleiding van de niet-Productie richt code-kwaliteit scans in werking te stellen of broncode in een ontwikkelomgeving op te stellen.

>[!NOTE]
>Raadpleeg de pijplijnen Niet-productie en Alleen kwaliteit van code voor meer informatie.

De plaatsing en de Kwaliteit van de Code die in Productie en Non-Productie pijpleiding in de Manager van de Wolk wordt gesteund zijn gecategoriseerd in twee verschillende types:

* Voorkant
* Volledige stapel

De volgende tabel geeft een overzicht van de pijpleidingen:


>[!NOTE]
>Een CI/CD pijpleiding in de Manager van de Wolk wordt teweeggebracht door een gebeurtenis, zoals een trekkingsverzoek van een broncodebewaarplaats die, een codeverandering, of een regelmatig programma is om een versieaanhouding aan te passen.
>
>Om uw pijpleiding te vormen, moet u:
>* bepaal de trekker die de pijpleiding zal beginnen
>* de parameters definiëren die de productie-implementatie beheersen
>* configureren van de testparameters voor de prestaties