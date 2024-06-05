---
title: Licentiedashboard
description: Cloud Manager biedt een dashboard voor het eenvoudig weergeven van AEMaaCS-productrechten die beschikbaar zijn voor uw organisatie of huurder.
exl-id: bf0f54a9-fe86-4bfb-9fa6-03cf0fd5f404
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---

# Licentiedashboard {#license-dashboard}

Cloud Manager biedt een dashboard voor het eenvoudig weergeven van AEMaaCS-productrechten die beschikbaar zijn voor uw organisatie of huurder.

## Overzicht {#overview}

Het licentiedashboard voor Cloud Manager biedt eenvoudige toegang tot de volgende informatie:

1. De rechten van de oplossing zijn beschikbaar aan u over al uw programma&#39;s, met inbegrip van wat wordt gebruikt en wat beschikbaar is
1. De verbruiksmetriek van het Verzoek van de inhoud die door maand voor de oplossing van Plaatsen wordt trendt

## Het licentiedashboard gebruiken {#using-dashboard}

Ga als volgt te werk om het licentiedashboard te openen.

>[!NOTE]
>
>Een gebruiker in het dialoogvenster **Zakelijke eigenaar** rol moet worden aangemeld om het licentiedashboard weer te geven.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Op de **[Mijn programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)** console, schakelaar aan de **Licentie** tab.

![Licentiedashboard](assets/license-dashboard.png)

Het dashboard bestaat uit drie gedeelten die u laten zien:

* **Oplossingen** - In deze sectie wordt een overzicht gegeven van de oplossingen die u hebt gelicentieerd, zoals Sites of Assets.
* **Invoegtoepassingen** - Deze sectie vat welke toe:voegen-ons aan uw vergunning gegeven oplossingen samen die u beschikbaar hebt.
* **Sandbox &amp; Development Environment** - Deze sectie geeft een overzicht van de omgevingen die u hebt.

Elke sectie vat samen wat beschikbaar is en hoe het, als bij allen wordt gebruikt. Momenteel slechts worden de oplossingen van Plaatsen getoond zelfs als andere oplossingen in de huurder bestaan.

* De **Status** in de kolom wordt het aantal niet-gebruikte rechten weergegeven ten opzichte van het totaal dat voor de huurder beschikbaar is.
* De **Gevormd op** de kolom geeft de programma&#39;s aan waarop de oplossingsbevoegdheid is toegepast.
   * Een recht wordt beschouwd als gebruikt slechts wanneer een productiemilieu is gecreeerd of als één bestaat, als een updatepijpleiding op het is in werking gesteld.
* De **Gebruik** in de kolom worden de in de afgelopen 12 maanden verbruikte inhoudsverzoeken als een grafiek weergegeven wanneer erop wordt geklikt.

>[!TIP]
>
>Om te leren hoe te om uw rechten van de Adobe over uw volledige organisatie van Admin Console te beheren, zie [Overzicht van Admin Console](https://helpx.adobe.com/nl/enterprise/using/admin-console.html).

## Veelgestelde vragen {#faq}

### Wat is een inhoudsverzoek? {#what-is-a-content-request}

Een inhoudsverzoek is een verzoek dat in AEM Sites of om het even welk klant-verstrekt in het voorgeheugen onderbrengend systeem zoals een netwerk van de inhoudslevering komt om inhoud of gegevens in één van beide formaat van de HTML als paginamening of in formaat JSON als API vraag te leveren.

Één inhoudsverzoek wordt geteld voor elke paginamening of voor elke vijf API vraag, die bij de ingang van het eerste caching systeem wordt gemeten om een inhoudsverzoek te ontvangen. Inhoudsaanvragen worden alleen in mindering gebracht op productieomgevingen.

Inhoudsverzoeken sluiten verzoeken of activiteiten uit die door of namens Adobe worden geïnitieerd met als enig doel het aanbieden van producten en diensten. Adobe-geïdentificeerd gebruikersagent verkeer van bots, kruiplers, en spinnen met betrekking tot gemeenschappelijke onderzoeksmotoren en sociale media diensten is ook uitgesloten.

Zie ook [Inhoudsverzoeken van Cloud Servicen begrijpen](/help/implementing/cloud-manager/content-requests.md).

### Hoe meet Adobe Experience Manager verzoeken om inhoud? {#how-are-content-requests-measured}

Inhoudsaanvragen worden bijgehouden op Edge-servers van AEM as a Cloud Service. Het verkeer van de oorsprong telt niet op inhoudverzoeken. CDN die in AEM as a Cloud Service sporen geldige HTML en JSON verzoeken wordt ingebouwd.

AEM heeft ook regels om bekende bots uit te sluiten, met inbegrip van bekende diensten die de site regelmatig bezoeken om hun zoekindex of service te vernieuwen.

Zie ook [Inhoudsverzoeken van Cloud Servicen begrijpen](/help/implementing/cloud-manager/content-requests.md).

### Waarom toont mijn Analytics-rapport andere resultaten dan de AEM Content Requests? {#why-are-reports-different}

Aanvragen voor inhoud kunnen variaties hebben met de rapportagehulpprogramma&#39;s Analytics van een organisatie. Zie voor meer informatie [Inhoudsverzoeken van Cloud Servicen begrijpen](/help/implementing/cloud-manager/content-requests.md).

### Wat als ik meer over mijn volume van de inhoudshulp zou willen leren? {#current-request-volumes}

Als u meer inzichten in het volume van de inhoudsaanvraag wilt zien in het Dashboard van de Vergunning, kan uw team van de Adobe een rapport verstrekken dat de hoogste volumebestuurders van inhoudverzoeken toont. Neem contact op met uw Adobe-team of met de Adobe Klantenondersteuning om een rapport met het hoogste verbruik aan te vragen.

### Wat als ik mijn eigen CDN gebruik? {#using-own-cdn}

Op het licentiedashboard worden alleen gegevens weergegeven die door de Cloud Service CDN worden bijgehouden. Als u verkiest om uw eigen CDN (BYOCDN) te brengen, rapporteert u het volume van uw inhoudsverzoek terug aan Adobe op jaarbasis, zoals die in uw contract wordt verklaard.
