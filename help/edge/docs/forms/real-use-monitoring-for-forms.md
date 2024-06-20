---
title: Realtime User Monitoring (RUM) voor Edge Delivery Services voor AEM Forms as a Cloud Service
description: Real Use Monitoring (RUM) voor Edge Delivery Services voor AEM Forms as a Cloud Service omvat het doorlopend volgen en analyseren van gebruikersinteracties met formulieren.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 184fc7dc-d583-4a63-9e30-80d324ec9d7e
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---


# Real Use Monitoring (RUM) for Edge Delivery Services for AEM Forms as a Cloud Service

Met Real Use Monitoring (RUM) kunt u inzicht krijgen in de manier waarop bezoekers met uw Adobe Experience Manager-websites (AEM) communiceren. Dit ingebouwde hulpmiddel verstrekt waardevolle gegevens om gebruikersgedrag te begrijpen, prestatieskwesties te diagnostiseren, en de doeltreffendheid van websiteexperimenten te meten. RUM gaat verder dan synthetisch testen door interacties voor echt gebruik vast te leggen en biedt een nauwkeuriger beeld van de prestaties van uw site.

Het RUM geeft echter prioriteit aan de privacy van bezoekers. Hierbij worden steekproeftechnieken gebruikt om gegevens te verzamelen van een representatieve subgroep van gebruikers, zodat er nooit persoonlijk identificeerbare informatie (PII) wordt vastgelegd. Bovendien, wordt RUM ontworpen met gegevensminimalisering in mening, die slechts de essentiële metriek verzamelen die voor prestatiesanalyse wordt vereist. Op deze manier kunt u uw AEM optimaliseren en het vertrouwen van de gebruiker behouden.


## Voorwaarden

U kunt het controledashboard voor Edge Delivery Services voor AEM Forms as a Cloud Service bekijken door tot het volgende URL toegang te hebben:

https://data.aem.live/?ext=forms

![Scherm met inloggegevens RUM voor Edge Delivery Services voor Forms](/help/edge/assets/rum-login-screen.png)

Als u zich wilt aanmelden bij het dashboard voor bewaking van Edge Delivery Services voor as a Cloud Service AEM Forms, voert u het volgende in:

* **URL**: De URL is specifiek voor de gebruikerssite of het domein. De gebruikers hebben de optie om de site of het domein te filteren en het dashboard volgens hun vereisten weer te geven.

* **Domeinsleutel**: De gebruiker genereert handmatig de domeinsleutel. Neem contact op met uw Adobe als u domeinsleutels voor uw formulieren wilt opvragen.

### Monitoringdashboard voor Edge Delivery Services voor AEM Forms as a Cloud Service

Nadat u de URL- en domeinsleutels hebt ingevoerd in het aanmeldingsscherm, krijgt u toegang tot het dashboard voor de bewaking van Edge Delivery Services voor AEM Forms as a Cloud Service.

In de onderstaande afbeelding ziet u het dashboard voor Edge Delivery Services voor as a Cloud Service AEM Forms:

![RUM Forms-dashboard](/help/edge/assets/rum-forms-dashboard.png)

### Verschillende maatstaven van het dashboard voor Forms {#different-metrics-rum-dashboard-forms}

Dit dashboard biedt belangrijke inzichten in de manier waarop bezoekers werken met formulieren op uw Adobe Experience Manager-website (AEM). Door deze gegevens te controleren, kunt u gebieden voor verbetering identificeren en uw formulieren optimaliseren voor een betere gebruikerservaring en conversiesnelheden:

* **Formulierweergaven**: Houd het totale aantal keren bij dat formulieren worden weergegeven
* **Formulierverzendingen**: Traceer het totale aantal ingevulde aanvragen

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

## Handelbare inzichten

Door deze metriek te analyseren, kunt u kansen identificeren aan:

* Formulieren vereenvoudigen en het aantal velden verminderen.
* Verbeter de duidelijkheid van formulieren met duidelijke instructies en labels.
* Formulierindeling optimaliseren voor mobiele reacties.
* Technische problemen verhelpen die het laden van formulieren vertragen.

Door u op deze gebieden te concentreren, kunt u formulieren maken die gemakkelijker te gebruiken zijn en bezoekers aanmoedigen om ze te voltooien, wat uiteindelijk leidt tot hogere conversietarieven.

## Zie ook

{{see-more-forms-eds}}