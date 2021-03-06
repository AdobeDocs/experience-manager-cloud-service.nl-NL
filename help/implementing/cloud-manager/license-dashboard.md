---
title: Licentiedashboard
description: Cloud Manager biedt een dashboard voor het eenvoudig weergeven van AEMaaCS-productrechten die beschikbaar zijn voor uw organisatie of huurder.
exl-id: bf0f54a9-fe86-4bfb-9fa6-03cf0fd5f404
source-git-commit: 5bf65238ce4d1f619507d9a5f8b7574e58352d51
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---

# Licentiedashboard {#license-dashboard}

Cloud Manager biedt een dashboard voor het eenvoudig weergeven van AEMaaCS-productrechten die beschikbaar zijn voor uw organisatie of huurder.

## Overzicht {#overview}

Het licentiedashboard voor Cloud Manager biedt eenvoudige toegang tot de volgende informatie:

1. De aanspraken van de oplossing beschikbaar aan u over al uw programma&#39;s, met inbegrip van wat wordt gebruikt en wat beschikbaar is
1. De verbruiksmetriek van het Verzoek van de inhoud die door maand voor de oplossing van Plaatsen wordt trendt

## Het licentiedashboard gebruiken {#using-dashboard}

Ga als volgt te werk om het licentiedashboard te openen.

>[!NOTE]
>
>Een gebruiker in **Zakelijke eigenaar** rol moet worden aangemeld om het licentiedashboard weer te geven.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Ga op de pagina met productoverzicht naar de knop **Licentie** tab.

![Licentiedashboard](assets/license-dashboard.png)

Het dashboard bestaat uit drie gedeelten die u tonen:

* **Oplossingen** - In deze sectie wordt een overzicht gegeven van de oplossingen die u hebt gelicentieerd, zoals Sites of Assets.
* **Invoegtoepassingen** - Deze sectie vat welke toe:voegen-ons aan uw vergunning gegeven oplossingen samen die u beschikbaar hebt.
* **Sandbox- en ontwikkelomgevingen** - Deze sectie geeft een overzicht van de omgevingen die u hebt.

Elke sectie vat samen wat beschikbaar is en hoe het momenteel, als bij allen wordt gebruikt. Momenteel slechts worden de oplossingen van Plaatsen getoond zelfs als andere oplossingen in de huurder bestaan.

* De **Status** in de kolom wordt het aantal niet-gebruikte rechten tegenover het totaal dat voor de huurder beschikbaar is, weergegeven.
* De **Gevormd op** de kolom geeft de programma&#39;s aan waarop de oplossingsbevoegdheid is toegepast.
   * Een machtiging wordt alleen als gebruikt beschouwd wanneer een productieomgeving is gemaakt of wanneer er al een bestaat, als er een updatepijpleiding op is uitgevoerd.
* De **Gebruik** in de kolom worden de in de afgelopen 12 maanden verbruikte inhoudsverzoeken als een grafiek weergegeven wanneer erop wordt geklikt.

>[!TIP]
>
>Zie [Overzicht van Admin Console](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) om te leren hoe te om uw rechten van de Adobe over uw volledige organisatie van Admin Console te beheren.

## Veelgestelde vragen {#faq}

### Wat is een inhoudsverzoek? {#what-is-a-content-request}

Een inhoudsverzoek is een verzoek dat in AEM Sites of om het even welk klant-verstrekt in het voorgeheugen onderbrengend systeem zoals een netwerk van de inhoudslevering komt om inhoud of gegevens in ????n van beide formaat van de HTML als paginamening of in formaat JSON als API vraag te leveren.

????n inhoudsverzoek wordt geteld voor elke paginamening of voor elke vijf API vraag, die bij de ingang van het eerste caching systeem wordt gemeten om een inhoudsverzoek te ontvangen. Inhoudsaanvragen worden alleen in mindering gebracht op productieomgevingen.

Inhoudsverzoeken sluiten verzoeken of activiteiten uit die door of namens Adobe worden ge??nitieerd met als enig doel het aanbieden van producten en diensten. Adobe-ge??dentificeerd gebruikersagent verkeer van bots, kruiplers, en spinnen met betrekking tot gemeenschappelijke onderzoeksmotoren en sociale media diensten wordt ook uitgesloten.

### Hoe meet Adobe Experience Manager verzoeken om inhoud? {#how-are-content-requests-measured}

Inhoudsaanvragen worden bijgehouden op Edge-servers van AEM as a Cloud Service. Het verkeer van de oorsprong telt niet op inhoudverzoeken. CDN die in AEM as a Cloud Service sporen geldige HTML en JSON verzoeken wordt ingebouwd.

AEM heeft ook regels om bekende bots uit te sluiten, met inbegrip van bekende diensten die de site regelmatig bezoeken om hun zoekindex of service te vernieuwen.

Hieronder volgt een niet-limitatieve lijst van voorbeelden van uitgesloten bekende diensten.

* AddSearchBot
* AhrefsBot
* Applebot
* Vraag Jeeves Corporate Spider
* Bingbot
* BingPreview
* BLEXBot
* BuiltWith
* Bytespider
* CrawlerKengo
* Facebookexternalhit
* Google AdsBot
* Google AdsBot Mobile

### Waarom toont mijn Analytics-rapport andere resultaten dan de AEM Content Requests? {#why-are-reports-different}

De verzoeken van de inhoud zullen variaties met Analytics van een organisatie hebben rapporteringshulpmiddelen zoals samengevat in deze lijst.

| Reden voor variantie | Toelichting |
|---|---|
| Tags | Alle pagina&#39;s die worden bijgehouden als AEM inhoudsaanvragen, kunnen al dan niet worden gelabeld met Analytics tracking.<br>Alle API-aanroepen die worden bijgehouden als AEM inhoudsaanvragen, worden niet gelabeld door het hulpprogramma Analytics van een organisatie.<br>Pagina&#39;s of API-aanroepen kunnen worden gelabeld om handelingen bij te houden in plaats van weergaven. |
| Tag Management-regels | Instellingen voor regels voor tagbeheer kunnen resulteren in verschillende configuraties voor gegevensverzameling op een pagina, wat resulteert in een combinatie van verschillen met het bijhouden van de inhoudsaanvraag. |
| Bots | Onbekende bots die niet vooraf zijn ge??dentificeerd en door AEM zijn verwijderd, kunnen verschillen in het bijhouden van gegevens veroorzaken. |
| Rapportageopties | Pagina&#39;s die deel uitmaken van hetzelfde AEM exemplaar en domein, kunnen gegevens naar verschillende analytische rapportsuites verzenden. |
| Instrumenten voor toezicht en beveiliging van derden | Met de hulpprogramma&#39;s voor controle en beveiligingsscans kunt u verzoeken om AEM genereren die niet worden bijgehouden in analytische rapporten. |
| Prefetverzoeken | Als u een prefetch-service gebruikt om pagina&#39;s vooraf te laden om de snelheid te verhogen, kan dit leiden tot aanzienlijke toename van het verkeer van inhoudsverzoeken. |
| DDOS | Terwijl Adobe alles in het werk stelt om automatisch verkeer van DDOS-aanvallen te detecteren en eruit te filteren, is er geen garantie dat alle mogelijke DDOS-aanvallen worden gedetecteerd. |

### Wat als ik mijn eigen CDN gebruik? {#using-own-cdn}

Het dashboard voor aanvragen voor inhoud in Cloud Manager geeft geen tracering voor uw eigen CDN weer.
