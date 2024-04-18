---
title: Real-time gebruikerscontrole voor Edge Delivery Services Forms
description: In real time gebruikerscontrole voor Edge Delivery Services Forms omvat het aan de gang zijnde volgen en analyse van gebruikersinteractie met vormen.
feature: Edge Delivery Services
exl-id: 184fc7dc-d583-4a63-9e30-80d324ec9d7e
source-git-commit: 2affe155b285986128487043fcc4f2938fc15842
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---


# Real-time gebruikerscontrole voor Edge Delivery Services Forms

Adobe Experience Manager gebruikt Real User Monitoring (RUM) om de interactie van bezoekers met Adobe Experience Manager-gestuurde sites te begrijpen. Het helpt bij het diagnosticeren van de prestatieproblemen en de doeltreffendheid van het testprogramma voor gaging. De echte Controle van de Gebruiker handhaaft de bezoekersprivacy door de steekproeftechnieken te gebruiken, die ervoor zorgen dat geen persoonlijke informatie wordt verzameld door de plaatsen u bezoekt. Het is niet toegestaan persoonsgegevens toe te voegen aan de gegevensverzameling op het RUM. Real User Monitoring in Adobe Experience Manager is ontworpen om de privacy van bezoekers te behouden en gegevensverzameling tot een minimum te beperken.

## Voordelen van het gebruik van Real-time gebruikerscontrole voor Edge Delivery Services Forms {#advantages}

AEM gebruikt real time gebruikerscontrole voor het volgende:

* Om prestatiesknelpunten op plaatsen te identificeren en te bevestigen.
* Om het aantal paginameningen aan klantenplaatsen te schatten
* Als u de interactie van Adobe Experience Manager met analyses, doelbibliotheken of externe bibliotheken op dezelfde pagina wilt begrijpen, verbetert u de compatibiliteit.

## Voorwaarden

U kunt het dashboard voor realtime gebruikerscontrole voor Edge Delivery Services Forms weergeven door de volgende URL te openen: https://data.aem.live/?ext=forms

![Aanmeldingsscherm RUM voor Edge Delivery Services Forms ](/help/edge/assets/rum-login-screen.png)

Voer het volgende in om u aan te melden bij het dashboard voor realtime gebruikersbewaking voor Edge Delivery Services Forms:
* **URL**: De URL is specifiek voor de gebruikerssite of het domein. De gebruikers hebben de optie om de site of het domein te filteren en het dashboard volgens hun vereisten weer te geven.
* **Domeinsleutel**: De gebruiker genereert handmatig de domeinsleutel. Voor hulp of vragen raadpleegt u de [Sleutel RUM-domein genereren](https://aemcs-workspace.adobe.com/rum/generate-domain-key) documentatie.

### Real time user monitoring dashboard voor Edge Delivery Services Forms

Nadat u de URL en de domeinsleutel hebt ingevoerd in het aanmeldingsscherm, krijgt u toegang tot het dashboard voor realtime gebruikerscontrole voor Edge Delivery Services Forms.

In de onderstaande afbeelding ziet u het RUM-dashboard voor Edge Delivery Services Forms:

![RUM Forms-dashboard](/help/edge/assets/rum-forms-dashboard.png)

### Verschillende maatstaven van RUM-dashboard voor Forms {#different-metrics-rum-dashboard-forms}

U kunt de interactie van de bezoeker met Adobe Experience Manager-gedreven plaatsen beoordelen gebruikend de volgende belangrijkste metriek:

* **Formviews**: Dit is het totale aantal formulieren dat is gegenereerd voor een URL binnen het opgegeven datumbereik.
* **Formulier**: Dit is het totale aantal formulieren dat voor een URL binnen het opgegeven datumbereik wordt verzonden.
* **Grootste inhoudelijke verf**: De URL geeft de snelheid weer waarmee de URL wordt geladen. De tijd die nodig is om het grootste inhoudselement dat zichtbaar is in de viewport, te renderen vanaf het moment dat de gebruiker de URL aanvraagt. Dit grootste inhoudselement kan een afbeelding, video of een aanzienlijk tekstelement op blokniveau zijn. De prestatiesclassificaties voor URL ladingssnelheid zijn gecategoriseerd als volgt:
   * **Goed**: Als de laadtijd 2,5 seconden of minder is.
   * **Oké**: Wanneer de laadtijd meer dan 2,5 maar niet meer dan 4 seconden bedraagt.
   * **Slecht**: Als de laadtijd meer dan 4 seconden bedraagt

* **Cumulatieve layoutverschuiving**: Hiermee wordt de totale som van alle afzonderlijke scores voor de layoutverschuiving gemeten voor elke onverwachte verschuiving van de layout die plaatsvindt gedurende de volledige levensduur van de pagina. Het speelt een cruciale rol bij het identificeren van de prestaties van een pagina omdat pagina-elementen verschuiven wanneer een gebruiker met hen probeert te communiceren, dit tot een slechte gebruikerservaring leidt. Deze score varieert van nul tot een positief getal: nul geeft aan dat er niets wordt verschoven, terwijl een hoger getal meer layoutverschuivingen op de pagina aangeeft. De prestatiemetriek die wordt gebruikt om de scores van de lay-outverschuiving te beoordelen zijn als volgt gecategoriseerd:

   * **Goed**: Als de score voor de verschuiving van de layout 0,1 of minder is.
   * **Oké**: Als de verschuivingsscore voor de layout groter is dan 0,1 maar niet groter dan 0,25.
   * **Slecht**: Als de shift-score van de lay-out hoger is dan 0,25.

* **Interactie met volgende verf**: Hiermee wordt geëvalueerd hoe snel een pagina reageert op gebruikersinteracties, rekening houdend met de tijd die de pagina nodig heeft om te reageren op klikken, tikken en toetsenbordinvoer tijdens het bezoek van een gebruiker aan de pagina. De uiteindelijke waarde is de langste waargenomen interactie, waarbij eventuele anomalieën buiten beschouwing worden gelaten. De prestatiesmetriek voor Interactie aan Volgende Verf worden gecategoriseerd als volgt:
   * **Goed**: Als de duur tussen gebruikersacties 200 milliseconden (ms) of minder is.
   * **Oké**: Als de duur meer dan 200 ms maar niet meer dan 500 ms bedraagt.
   * **Slecht**: Als de duur langer is dan 500 ms.
