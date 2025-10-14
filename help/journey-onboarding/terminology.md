---
title: AEM as a Cloud Service Terminologie
description: Voordat u zich aanmeldt bij AEMaaCS, is het handig om enkele terminologie van het systeem en de basisstructuur te begrijpen.
exl-id: d02776a7-836a-4894-a5d5-ae88cc7e4e76
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# AEM as a Cloud Service Terminologie {#terminology}

In dit deel van de [&#x200B; onboarding reis &#x200B;](overview.md), leert u enkele terminologie van AEM as a Cloud Service en zijn basisstructuur.

## Doelstelling {#objective}

Nu u begrijpt wat tot het onboarding proces door het document [&#x200B; onboarding Voorbereiding &#x200B;](preparation.md) heeft geleid te lezen, is het nuttig om enkele terminologie van het systeem en zijn basisstructuur te begrijpen alvorens het programma te openen.

AEM as a Cloud Service is een krachtig en flexibel hulpmiddel en om elk hulpmiddel te gebruiken dat u zou moeten kennen met zijn organisatie en de terminologie en de taal die worden gebruikt om het te beschrijven. Dit document bevat een overzicht van enkele belangrijke termen die u moet begrijpen voordat u het systeem gaat gebruiken.

Nadat u dit document hebt gelezen, moet u

* De verschillende lagen waaruit AEMaaCS bestaat.
* De basisbeginselen van wat elke laag doet.

## AEMaaCS-structuur {#structure}

Voor deze instapreis is een volledig begrip van de structuur van AEM as a Cloud Service niet nodig. Maar door de kennis van de volgende concepten is het gemakkelijker om later op de reis verder te gaan.

![&#x200B; structuur van Cloud Manager &#x200B;](/help/journey-sites/quick-site/assets/cloud-manager-structure.png)

* **TENANT** - elke klant wordt provisioned met een huurder. Een huurder wordt ook wel IMS org genoemd (meer op IMS later in deze reis)
* **PROGRAMMA&#39;S** - elke huurder heeft één of meerdere programma&#39;s, die vaak op de gelicentieerde oplossingen van de klant wijzen.
* **OMGEVINGEN** - Elk programma heeft veelvoudige milieu&#39;s zoals productie voor levende inhoud, voor het opvoeren, en voor ontwikkelingsdoeleinden.
* **REPOSITORY** - de milieu&#39;s hebben één of meerdere git bewaarplaatsen waar toepassing en front-end code wordt gehandhaafd.
* **TOOLS &amp; WORKFLOWS** - de Pijpleidingen beheren de plaatsing van code van de bewaarplaatsen aan de milieu&#39;s.

Een voorbeeld is vaak handig bij het contextualiseren van deze hiërarchie.

* De Onderneming van het Reizen van WKND en van het Avontuur zou a **huurder** kunnen zijn die zich op op reis betrekking hebbende media concentreert.
* De huurder van de Onderneming van het WKND Reizen en van het Adventure van de Onderneming zou twee **programma&#39;s** kunnen hebben:
   * Één programma van Plaatsen voor zijn afdeling van het Tijdschrift WKND
   * Eén Assets-programma voor WKND Media-afdeling
* De programma&#39;s van het Tijdschrift WKND en van Media WKND zouden zowel ontwikkeling, het opvoeren, als productie **milieu&#39;s** hebben.
* **Bewaarplaatsen** worden gebruikt om de douanecode en de toepassingen voor het Tijdschrift van WKND en Media te handhaven WKND.
* Diverse **hulpmiddelen &amp; werkschema&#39;s** werk over de repos om code op te stellen gebruikend pijpleidingen CI/CD, toegangslogboeken, AEM, etc.

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM onboarding trip hebt voltooid, moet u begrijpen:

* De verschillende lagen waaruit AEMaaCS bestaat.
* De basisbeginselen van wat elke laag doet.

Bouw op deze kennis voort en ga uw AEM reis op het instappen door het document [&#x200B; te lezen dat tot de Admin Console &#x200B;](admin-console.md) toegang heeft, waar u leert hoe toegang tot de console en uw status als systeembeheerder verifieert.
