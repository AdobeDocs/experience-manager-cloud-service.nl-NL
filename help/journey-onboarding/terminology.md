---
title: as a Cloud Service terminologie AEM
description: Voordat u zich aanmeldt bij AEMaaCS, is het handig om enkele terminologie van het systeem en de basisstructuur te begrijpen.
exl-id: d02776a7-836a-4894-a5d5-ae88cc7e4e76
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# as a Cloud Service terminologie AEM {#terminology}

In dit deel van het [aan boord gaan,](overview.md) u leert wat van de terminologie van AEM as a Cloud Service en zijn basisstructuur.

## Doelstelling {#objective}

Nu begrijpt u wat tot het onboarding proces heeft geleid door het document te lezen [Voorbereiding aan boord,](preparation.md) het is nuttig om enkele terminologie van het systeem en zijn basisstructuur te begrijpen alvorens het programma te openen.

AEM as a Cloud Service is een krachtig en flexibel hulpmiddel en om om het even welk hulpmiddel te gebruiken zou u met zijn organisatie en de terminologie en de taal vertrouwd moeten zijn om het te beschrijven. Dit document bevat een overzicht van enkele belangrijke termen die u moet begrijpen voordat u het systeem gaat gebruiken.

Nadat u dit document hebt gelezen, moet u

* De verschillende lagen waaruit AEMaaCS bestaat.
* De basisbeginselen van wat elke laag doet.

## AEMaaCS-structuur {#structure}

Voor deze instapreis is een volledig begrip van de structuur van AEM as a Cloud Service niet nodig. Maar door de kennis van de volgende concepten is het gemakkelijker om later op de reis verder te gaan.

![Cloud Manager-structuur](/help/journey-sites/quick-site/assets/cloud-manager-structure.png)

* **TENANT** - Elke klant wordt voorzien van een huurder. Een huurder wordt ook wel IMS org genoemd (meer op IMS later in deze reis)
* **PROGRAMMA&#39;S** - Elke huurder heeft één of meerdere programma&#39;s, die vaak de gelicentieerde oplossingen van de klant weerspiegelen.
* **OMGEVINGEN** - Elk programma heeft meerdere omgevingen, zoals productie voor live-inhoud, één voor staging en één voor ontwikkelingsdoeleinden.
* **BEVESTIGING** - De omgevingen beschikken over een of meer git-opslagruimten waar de toepassing en front-end code worden onderhouden.
* **GEREEDSCHAPPEN EN WORKFLOWS** - De pijpleidingen beheren de implementatie van code van de gegevensbanken aan de milieu&#39;s.

Een voorbeeld is vaak handig bij het contextualiseren van deze hiërarchie.

* WKND Travel and Adventure Enterprises zou een **huurder** die zich richt op reisgerelateerde media.
* De huurder van WKND Reizen en Adventure Enterprises zou twee kunnen hebben **programma&#39;s**:
   * Één programma van Plaatsen voor zijn afdeling van het Tijdschrift WKND
   * One Assets program for WKND Media Division
* De programma&#39;s WKND Magazine en WKND Media zouden zowel ontwikkeling, het opvoeren als productie hebben **omgevingen**.
* **Opslagplaatsen** worden gebruikt om de douanecode en de toepassingen voor het Tijdschrift van WKND en Media te handhaven WKND.
* Diversen **gereedschappen en workflows** het werk over de repo&#39;s om code op te stellen gebruikend CI/CD pijpleidingen, toegangslogboeken, AEM, etc.

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM onboarding trip hebt voltooid, moet u begrijpen:

* De verschillende lagen waaruit AEMaaCS bestaat.
* De basisbeginselen van wat elke laag doet.

Gebaseerd op deze kennis en doorgaan met uw AEM instapreis bij volgende lezing van het document [De Admin Console openen](admin-console.md), waar u leert hoe toegang tot de console en uw status als systeembeheerder verifieert.
