---
title: Licentiedashboard
description: Cloud Manager biedt een dashboard voor het eenvoudig weergeven van AEMaaCS-productrechten die beschikbaar zijn voor uw organisatie of huurder.
exl-id: bf0f54a9-fe86-4bfb-9fa6-03cf0fd5f404
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: ec95438d704568076af045d8933be2125885f482
workflow-type: tm+mt
source-wordcount: '925'
ht-degree: 0%

---


# Licentiedashboard {#license-dashboard}

Cloud Manager biedt een dashboard voor het eenvoudig weergeven van AEMaaCS-productrechten die beschikbaar zijn voor uw organisatie of huurder.

>[!IMPORTANT]
>
>Het licentiedashboard geldt alleen voor de AEM as a Cloud Service-programma&#39;s. [ de programma&#39;s van AMS ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/introduction) zijn niet inbegrepen in het vergunningsdashboard.
>
>Om het type van de dienst te bepalen heeft uw programma (AMS of AEMaaCS), gelieve het document [ te zien navigerend Cloud Manager UI.](/help/implementing/cloud-manager/navigation.md#program-cards)

## Overzicht {#overview}

Het Cloud Manager-licentiedashboard biedt eenvoudige toegang tot de volgende informatie:

1. De rechten van de oplossing zijn beschikbaar aan u over al uw programma&#39;s, met inbegrip van wat wordt gebruikt en wat beschikbaar is
1. De verbruiksmetriek van het Verzoek van de inhoud die door maand voor de oplossing van Plaatsen wordt trendt

## Het licentiedashboard gebruiken {#using-dashboard}

Ga als volgt te werk om het licentiedashboard te openen.

>[!NOTE]
>
>Een gebruiker in de **rol van de BedrijfsEigenaar** moet worden het programma geopend om het Dashboard van de Vergunning te bekijken.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, ontgrendel of klik de hamburger menuknoop op de [ Kopbal van Cloud Manager.](/help/implementing/cloud-manager/navigation.md#cloud-manager-header) De tabbladen worden dan weergegeven.
1. Tik of klik de **optie van de Vergunning** in het lusje.

![ Dashboard van de Vergunning ](assets/license-dashboard.png)

Het dashboard bestaat uit drie gedeelten die u laten zien:

* **Oplossingen** - Deze sectie vat welke oplossingen samen die u zoals Plaatsen of Assets hebt vergunning gegeven.
* **toe:voegen-ons** - Deze sectie vat welke toe:voegen-ons aan uw vergunning gegeven oplossingen samen die u beschikbaar hebt.
* **Andere Entitlements** - Deze sectie vat samen welke zandbak en dev milieu evenals andere rechten die binnen uw huurder kunnen worden verbruikt.

Elke sectie vat samen wat beschikbaar is en hoe het, als bij allen wordt gebruikt. Momenteel slechts worden de Plaatsen en de oplossingen van Assets getoond zelfs als andere oplossingen in de huurder bestaan.

* De **kolom van de Status** toont het aantal ongebruikte rechten tegenover het totaal beschikbaar voor de huurder.
* **die op** wordt gevormd wijst op de programma&#39;s waarop de oplossingsbevoegdheid is toegepast.
   * Een recht wordt beschouwd als gebruikt slechts wanneer een productiemilieu is gecreeerd of als één bestaat, als een updatepijpleiding op het is in werking gesteld.
   * Slechts een beperkt aantal programma&#39;s wordt afzonderlijk vermeld in de kolom, de rest wordt vertegenwoordigd door een `+x` -item.
   * Houd de muisaanwijzer boven het item `+x` voor een pop-up met de details van alle programma&#39;s.
* De **kolom van het Gebruik** {toont a **[het gebruiksdetails van de Mening](#view-usage-details)** knoop om gebruiksstatistieken voor de oplossing te tonen.

>[!TIP]
>
>Leren hoe te om uw rechten van de Adobe over uw volledige organisatie van Admin Console te beheren, zie het [ overzicht van de Admin Console ](https://helpx.adobe.com/nl/enterprise/using/admin-console.html).

## Gebruiksdetails weergeven {#view-usage-details}

<!--
The **View usage details** button gives access to the chosen solution's **Usage Details** window. This window gives a detailed breakdown including charts to show your solution's usage. How that usage is measured depends on the chosen solution. -->

De **knoop van de het gebruikdetails van de Mening** in het gebied van de Vergunning van Cloud Manager verstrekt een gedetailleerde uitsplitsing van uw huidige middelgebruik. Wanneer geklikt, opent het een rapport of dashboard dat belangrijke metriek met betrekking tot uw vergunning toont. <!-- ADD THIS SENTENCE IF ASSETS USAGE DETAILS GETS REINSTATED ", such as the number of users, storage consumption, or bandwidth usage, depending on the type of services you're using." --> Deze functionaliteit helpt u te controleren en ervoor te zorgen dat u binnen de grenzen van uw contract blijft terwijl u inzichten voor betere middelplanning en optimalisering aanbiedt.

### Gebruiksgegevens voor sites {#sites-usage-details}

Het **venster van de het gebruikdetails van Plaatsen**, stelt grafieken voor die een overzicht van het gebruik van uw vergunningen geven van Plaatsen die op [ worden gebaseerd inhoudsverzoeken.](#what-is-a-content-request)

![ het venster van de het gebruikdetails van Plaatsen ](assets/sites-usage-details.png)

De linkerkant van het venster stelt een cirkeldiagram voor dat de contractverdeling voor het contractjaar toont dat in het **het contractjaar van de Mening** dropdown wordt geselecteerd.

De rechterzijde van het venster geeft een vlakgrafiek weer waarin het gebruik per programma in de loop van de tijd voor het geselecteerde contractjaar wordt uitgesplitst. Een muisaanwijzer toont een pop-up met details per programma voor het geselecteerde punt in de tijd.

<!-- REMOVED AS PER CQDOC-21983
### Assets usage details {#assets-usage-details}

The **Assets usage details** window, presents graphs giving an overview of the usage of your Assets licenses based on [storage](#storage) and [standard users.](#standard-users) Select the appropriate tab to toggle between the views.

For both storage and standard users views, you can use the **Environment Type** dropdown to toggle the view between production, stage, and development environments.

#### Storage {#storage}

![Assets usage details window for storage](assets/assets-usage-details-storage.png)

The left side of the window presents a pie chart showing the contract breakdown for the contract year selected in the **View contract year** dropdown.

The right side of the window presents an area chart showing the usage broken down by program over time for the selected contract year. A hover reveals a popup with details per program for the selected point in time.

#### Standard Users {#standard-users}

![Assets usage details window for standard-users](assets/assets-usage-details-standard-users.png)

The left side of the window presents a pie chart showing the contract breakdown for the contract year selected in the **View contract year** dropdown.

The right side of the window presents an area chart showing the usage broken down by program over time for the selected contract year. A hover reveals a popup with details per program for the selected point in time. -->

## Veelgestelde vragen {#faq}

### Wat is een inhoudsverzoek? {#what-is-a-content-request}

Een inhoudsverzoek is een verzoek dat in AEM Sites of om het even welk klant-verstrekt in het voorgeheugen onderbrengend systeem zoals een netwerk van de inhoudslevering komt om inhoud of gegevens in één van beide formaat van de HTML als paginamening of in formaat JSON als API vraag te leveren.

Één inhoudsverzoek wordt geteld voor elke paginamening of voor elke vijf API vraag, die bij de ingang van het eerste caching systeem wordt gemeten om een inhoudsverzoek te ontvangen. Inhoudsaanvragen worden alleen in mindering gebracht op productieomgevingen.

Inhoudsverzoeken sluiten verzoeken of activiteiten uit die door of namens Adobe worden geïnitieerd met als enig doel het aanbieden van producten en diensten. Adobe-geïdentificeerd gebruikersagent verkeer van bots, kruiplers, en spinnen met betrekking tot gemeenschappelijke onderzoeksmotoren en sociale media diensten is ook uitgesloten.

Zie ook [ Begrijpend de Verzoeken van de Inhoud van de Cloud Service ](/help/implementing/cloud-manager/content-requests.md).

### Hoe meet Adobe Experience Manager verzoeken om inhoud? {#how-are-content-requests-measured}

Aanvragen voor inhoud worden bijgehouden op AEM as a Cloud Service Edge-servers. Het verkeer van de oorsprong telt niet op inhoudverzoeken. De CDN die in AEM as a Cloud Service is ingebouwd, houdt geldige HTML- en JSON-aanvragen bij.

AEM heeft ook regels om bekende bots uit te sluiten, met inbegrip van bekende diensten die de site regelmatig bezoeken om hun zoekindex of service te vernieuwen.

Zie ook [ Begrijpend de Verzoeken van de Inhoud van de Cloud Service ](/help/implementing/cloud-manager/content-requests.md).

### Waarom toont mijn Analytics-rapport andere resultaten dan de AEM Content Requests? {#why-are-reports-different}

Aanvragen voor inhoud kunnen variaties hebben met de rapportagehulpprogramma&#39;s Analytics van een organisatie. Voor meer informatie, zie [ Begrijpend de Verzoeken van de Inhoud van de Cloud Service ](/help/implementing/cloud-manager/content-requests.md).

### Wat als ik meer over mijn volume van de inhoudshulp zou willen leren? {#current-request-volumes}

Als u meer inzichten in het volume van de inhoudsaanvraag wilt zien in het Dashboard van de Vergunning, kan uw team van de Adobe een rapport verstrekken dat de hoogste volumebestuurders van inhoudverzoeken toont. Neem contact op met uw Adobe-team of met de Adobe Klantenondersteuning om een rapport met het hoogste verbruik aan te vragen.

### Wat als ik mijn eigen CDN gebruik? {#using-own-cdn}

Op het licentiedashboard worden alleen gegevens weergegeven die door de Cloud Service CDN worden bijgehouden. Als u verkiest om uw eigen CDN (BYOCDN) te brengen, rapporteert u het volume van uw inhoudsverzoek terug aan Adobe op jaarbasis, zoals die in uw contract wordt verklaard.
