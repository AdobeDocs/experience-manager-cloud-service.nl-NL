---
title: Operationele telemetrie voor Edge Delivery Services voor AEM Forms as a Cloud Service
description: Operationele telemetrie voor Edge Delivery Services for AEM Forms as a Cloud Service omvat de doorlopende tracering en analyse van gebruikersinteracties met formulieren.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: 184fc7dc-d583-4a63-9e30-80d324ec9d7e
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '787'
ht-degree: 0%

---

# Operationele telemetrie voor Edge Delivery Services voor AEM Forms as a Cloud Service

Met de operationele telemetrie kunt u in de praktijk inzicht krijgen in de manier waarop bezoekers communiceren met uw Adobe Experience Manager-websites (AEM). Dit ingebouwde hulpmiddel verstrekt waardevolle gegevens om gebruikersgedrag te begrijpen, prestatieskwesties te diagnostiseren, en de doeltreffendheid van websiteexperimenten te meten. Operationele telemetrie gaat verder dan synthetische tests door interacties voor echt gebruik vast te leggen en biedt een nauwkeuriger beeld van de prestaties van uw site.

Operationele telemetrie geeft echter voorrang aan de privacy van bezoekers. Hierbij worden steekproeftechnieken gebruikt om gegevens te verzamelen van een representatieve subgroep van gebruikers, zodat er nooit persoonlijk identificeerbare informatie (PII) wordt vastgelegd. Bovendien is de operationele telemetrie ontworpen met het oog op het minimaliseren van gegevens, waarbij alleen de essentiële gegevens worden verzameld die vereist zijn voor prestatieanalyse. Op deze manier kunt u uw AEM-sites optimaliseren en het vertrouwen van de gebruiker behouden.


## Voorwaarden

U kunt het dashboard voor toezicht op Edge Delivery Services for AEM Forms as a Cloud Service weergeven door de volgende URL te openen:

https://data.aem.live/?ext=forms

![ het Operationele Login van de Telemetrie Scherm voor Edge Delivery Services voor Forms ](/help/edge/assets/rum-login-screen.png)

Voer de volgende gegevens in om u aan te melden bij het dashboard voor Edge Delivery Services for AEM Forms as a Cloud Service:

- **URL**: URL is specifiek voor gebruikersplaats of domein. De gebruikers hebben de optie om de site of het domein te filteren en het dashboard volgens hun vereisten weer te geven.

- **Sleutel van het Domein**: De gebruiker produceert manueel de domeinsleutel. Neem contact op met uw Adobe-vertegenwoordiger voor het verkrijgen van domeinsleutels voor uw formulieren.

### Monitoringdashboard voor Edge Delivery Services voor AEM Forms as a Cloud Service

Nadat u de URL- en domeinsleutels hebt ingevoerd in het aanmeldingsscherm, krijgt u toegang tot het dashboard voor Edge Delivery Services for AEM Forms as a Cloud Service.

In de onderstaande afbeelding ziet u het dashboard voor Edge Delivery Services for AEM Forms as a Cloud Service:

![ Operationeel het dashboard van de Telemetrie Forms ](/help/edge/assets/rum-forms-dashboard.png)

### Verschillende maatstaven van het dashboard voor Forms {#different-metrics-operational-telemetry-dashboard-forms}

Dit dashboard biedt belangrijke inzichten in de manier waarop bezoekers werken met formulieren op uw Adobe Experience Manager-website (AEM). Door deze gegevens te controleren, kunt u gebieden voor verbetering identificeren en uw formulieren optimaliseren voor een betere gebruikerservaring en conversiesnelheden:

- **de Weergaven van de Vorm**: Spoor het totale aantal tijden de vormen worden getoond
- **de Indieningen van de Vorm**: Houd het totale aantal voltooide voorlegging bij

- **de Grootste Inhoud Verf**: Het toont de snelheid waarbij URL laadt, die op de tijd wordt genomen om het grootste inhoudselement terug te geven zichtbaar in viewport van het ogenblik de gebruiker om URL verzoekt. Dit grootste inhoudselement kan een afbeelding, video of een aanzienlijk tekstelement op blokniveau zijn. De prestatiesclassificaties voor URL ladingssnelheid zijn gecategoriseerd als volgt:
   - **Goed**: Als de ladingstijd 2.5 seconden of minder is.
   - **Oke**: Als de ladingstijd meer dan 2.5 seconden maar 4 seconden of minder is.
   - **Slecht**: Als de ladingstijd 4 seconden overschrijdt

- **Cumulatieve Verschuiving van de Lay-out**: Het meet de totale som alle individuele scores van de lay-outverschuiving voor elke onverwachte lay-outverschuiving die door de volledige levensduur van de pagina voorkomt. Het speelt een cruciale rol bij het identificeren van de prestaties van een pagina omdat pagina-elementen verschuiven wanneer een gebruiker met hen probeert te communiceren, dit tot een slechte gebruikerservaring leidt. Deze score varieert van nul tot een positief getal: nul geeft aan dat er niets wordt verschoven, terwijl een hoger getal meer layoutverschuivingen op de pagina aangeeft. De prestatiemetriek die wordt gebruikt om de scores van de lay-outverschuiving te beoordelen zijn als volgt gecategoriseerd:

   - **Goed**: Als de score van de lay-outverschuiving 0.1 of minder is.
   - **oké**: Als de score van de lay-outverschuiving groter is dan 0.1 maar 0.25 of minder.
   - **Slecht**: Als de score van de lay-outverschuiving 0.25 overschrijdt.

- **Interactie aan Volgende Verf**: Het evalueert hoe snel een pagina op gebruikersinteractie reageert, rekening houdend met de tijd het voor de pagina neemt om aan kliks, tikken, en toetsenbordinput tijdens het bezoek van een gebruiker aan de pagina te antwoorden. De uiteindelijke waarde is de langste waargenomen interactie, waarbij eventuele anomalieën buiten beschouwing worden gelaten. De prestatiesmetriek voor Interactie aan Volgende Verf worden gecategoriseerd als volgt:
   - **Goed**: Als de duur tussen gebruikersacties 200 milliseconden (ms) of minder is.
   - **oké**: Als de duur meer dan 200 ms maar 500 ms of minder is.
   - **Slecht**: Als de duur 500 ms overschrijdt.

## Handelbare inzichten

Door deze metriek te analyseren, kunt u kansen identificeren aan:

- Formulieren vereenvoudigen en het aantal velden verminderen.
- Verbeter de duidelijkheid van formulieren met duidelijke instructies en labels.
- Formulierindeling optimaliseren voor mobiele reacties.
- Technische problemen verhelpen die het laden van formulieren vertragen.

Door u op deze gebieden te concentreren, kunt u formulieren maken die gemakkelijker te gebruiken zijn en bezoekers aanmoedigen om ze te voltooien, wat uiteindelijk leidt tot hogere conversietarieven.


