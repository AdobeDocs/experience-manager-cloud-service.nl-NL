---
title: Het dashboard voor het realiseren van waarden gebruiken om trends in het gebruik van formulieren en documenten te analyseren
description: Leer hoe u het dashboard Gebruiksinzichten van Forms gebruikt om de prestaties van uw formulieren en formulierfragmenten te controleren en te begrijpen.
role: User, Developer
level: Intermediate
feature: Adaptive Forms, Foundation Components, Core Components
hide: true
hidefromtoc: true
source-git-commit: 09d383638d6caba596d22a7c6b544768de5245a0
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 0%

---

# Het dashboard voor het realiseren van waarden gebruiken om trends in het gebruik van formulieren en documenten te analyseren

<span class="preview"> Deze functie is beschikbaar via het programma voor vroege toegang. Als u toegang wilt aanvragen, stuurt u een e-mail van uw officiële adres naar aem-forms-ea@adobe.com. <span>

![ Dashboard van de Realisatie van de Waarde ](/help/edge/docs/forms/universal-editor/assets/forms-insights-banner.svg)

Door regelmatig de metriek te controleren die in het dashboard van de Inzichten van het Gebruik van Forms wordt voorgesteld, kunt u waardevolle inzichten in de prestaties van uw vormen, documenten, en vormfragmenten verkrijgen. Gebruik deze gegevens om geïnformeerde beslissingen te nemen over formulierontwerp, fragmentbeheer en algemene formulierstrategie.

Dit artikel bevat gedetailleerde gebruiksinstructies en metrische interpretatie voor het dashboard voor waardetoewijzing. Voor een conceptueel overzicht en voordelen van het dashboard, zie [ begrip van uw dashboard van de waardeverwezenlijking ](/help/forms/aem-forms-value-realization-dashboard.md).


## Het dashboard met gebruiksinzichten openen

Zo opent u het dashboard met Forms-gebruiksinzichten:

1. Navigeer aan **Forms** > **Forms en Documenten**
1. Klik **Dashboard InProduct**. Het dashboard wordt in een nieuw venster geopend.

   ![ Dashboard van de Realisatie van de Waarde ](/help/forms/assets/forms-usage-insights.png)

## Overzicht

Het dashboard bestaat uit twee hoofdsecties:

- **Vorm &amp; activiteit van Documenten in tijd:** Deze sectie verstrekt inzicht in het gebruik en de evolutie van uw vormen over een geselecteerde periode.
- **gebruik van het Fragment:** Deze sectie staat u toe om de goedkeuring en het hergebruik van vormfragmenten te controleren.

## Formulier- en documentactiviteiten in de loop van de tijd

Deze sectie bevat vier grafieken, die elk een verschillend aspect van vormactiviteit volgen. Alle grafieken hebben dezelfde structuur:

- **Type van Grafiek:** Grafiek van de Lijn &amp; Grafiek van de Bar
- **x-as:** Datum (tonend dagelijkse activiteit)
- **y-as:** Telling (die het aantal voorkomen van de gevolgde activiteit vertegenwoordigt)
- **Periode van de Tijd:** Aanpasbaar via een dropdown menu (opties: &quot;Laatste 30 dagen&quot;, &quot;Laatste 12 maanden&quot;)




### Formulierverzendingen

- **Doel:** Dit diagram toont het aantal tijden de vormen met succes over de geselecteerde tijdspanne zijn voorgelegd.

  ![ Forms legt Grafiek voor ](/help/forms/assets/forms-submissions-vr-dashboard-form-insights.png)
- **Informatie aan Uittreksel:**
   - **Analyse van de Trend:** neem de algemene trend van vormverklaringen waar. Is het aantal stijgend, verminderend, of blijft relatief constant?
   - **Piekperiodes:** identificeer dagen of periodes met ongebruikelijk hoge voorleggingspercentages. Onderzoek de mogelijke redenen voor deze pieken (bijvoorbeeld marketingcampagnes, specifieke gebeurtenissen).
   - **Lage Periodes van de Activiteit:** identificeer periodes met lage voorleggingspercentages en onderzoek potentiële oorzaken (b.v., vormonderbreking, bruikbaarheidskwesties).
   - **Vergelijkende Analyse:** vergelijk indieningstarieven over verschillende tijdsperioden (b.v., de laatste 30 dagen tegenover de vorige 30 dagen) om prestatiesveranderingen te beoordelen.

### Documentuitvoeringen

- **Doel:** Deze grafiek volgt het aantal documenten die als resultaat van vormvoorlegging worden geproduceerd. Dit is relevant als uw formulieren het maken van documenten (bijvoorbeeld contracten, rapporten) activeren.

  ![ Grafiek van de Teruggaven van het Document ](/help/forms/assets/document-rendetions-vr-dashboard-form-insights.png)


- **Informatie aan Uittreksel:**
   - **Correlatie met de Verzending van de Vorm:** vergelijk de trend van documentvertoningen met de trend van vormindieningen. In het ideale geval moeten deze nauw met elkaar verweven zijn. Verschillen kunnen problemen met het genereren van documenten aangeven.
   - **Volume van de Generatie van het Document:** beoordeelt het algemene volume van documenten die worden geproduceerd om de werklast op uw systeem van de documentgeneratie te begrijpen.

### Forms Created


- **Doel:** Deze grafiek toont het aantal nieuwe vormen die binnen de geselecteerde tijdspanne worden gecreeerd.

  ![ Forms creeerde Grafiek ](/help/forms/assets/forms-created-vr-dashboard-form-insights.png)

- **Informatie aan Uittreksel:**
   - **Tarief van de Making van de Vorm:** spoor het tarief waaraan de nieuwe vormen worden gecreeerd. Dit biedt inzicht in de vraag naar nieuwe formulieren binnen de organisatie.
   - **Spikes in Creatie:** identificeer periodes met ongebruikelijk hoge activiteit van de vormverwezenlijking. Dit kan specifieke projecten of initiatieven aangeven waarvoor nieuwe formulieren nodig zijn.

### Forms gepubliceerd

- **Doel:** Dit diagram volgt het aantal vormen die (beschikbaar voor gebruik gemaakt) binnen de geselecteerde tijdspanne zijn gepubliceerd.

  ![ Forms Gepubliceerde Grafiek ](/help/forms/assets/forms-publish-vr-dashboard-form-insights.png)


- **Informatie aan Uittreksel:**
   - **het Tarief van de Plaatsing van de Vorm:** controleert het tarief waaraan de nieuwe vormen aan gebruikers worden opgesteld.
   - **Lag tussen Creatie en Publicatie:** Analyseer het tijdverschil tussen de &quot;Forms Gecreeerde&quot;grafiek en de &quot;Forms Gepubliceerde&quot;grafiek. Een aanzienlijke vertraging kan wijzen op knelpunten in het goedkeurings- of inzetproces van het formulier.

## Fragmentgebruik

Deze sectie biedt inzicht in het gebruik van formulierfragmenten. Dit zijn herbruikbare componenten die in meerdere formulieren kunnen worden opgenomen.

![ Forms Gepubliceerde Grafiek ](/help/forms/assets/fragment-usage-vr-dashboard-form-insights.png)

### Aantal gebruikte formulierfragmenten

- **Type van Grafiek:** Numerieke Vertoning (die één enkele waarde toont)
- **Doel:** dit toont het totale aantal unieke vormfragmenten die momenteel in actieve vormen worden gebruikt.
- **Informatie aan Uittreksel:**
   - **de Goedkeuring van het Fragment:** beoordeelt de algemene goedkeuring van vormfragmenten binnen de organisatie. Een hoger getal geeft een groter gebruik van herbruikbare componenten aan.

### Formulierfragment opnieuw gebruiken

- **Type van Grafiek:** Numerieke Vertoning (die één enkele waarde toont)
- **Doel:** dit toont het totale aantal tijden de fragmenten van de vorm zijn opnieuw gebruikt over verschillende vormen. Deze maatstaf geeft aan hoe effectief fragmenten worden gebruikt om dubbel werk te voorkomen en consistentie te behouden.
- **Informatie aan Uittreksel:**
   - **het Tarief van het Hergebruik van het fragment:** controleert het tarief waaraan de bestaande fragmenten in nieuwe vormen opnieuw worden gebruikt. Een hoger getal geeft een betere benutting van herbruikbare onderdelen en een verbeterde efficiëntie aan.

## Voorbeeldscenario&#39;s

- **Scenario:** u merkt een plotselinge daling in &quot;Voorlegging van de Vorm.&quot;
   - **Actie:** onderzoekt potentiële oorzaken zoals vormonderbreking, bruikbaarheidskwesties, of een daling in verkeer aan de het landen pagina van de vorm.
- **Scenario:** De waarde &quot;van het Fragment van de Vorm hergebruikt&quot;is laag.
   - **Actie:** bevordert de voordelen om vormfragmenten aan uw team te gebruiken, ervoor te zorgen dat de fragmenten goed-georganiseerd en gemakkelijk te vinden zijn, en opleiding te verstrekken over hoe te om fragmenten effectief tot stand te brengen en te hergebruiken.
- **Scenario:** Er is een significant verschil tussen &quot;Forms Gecreeerd&quot;en &quot;Forms Gepubliceerd.&quot;
   - **Actie:** herzie uw vormgoedkeuring en plaatsingsproces om knelpunten te identificeren en te elimineren.



## Zie ook

- [Het dashboard voor het realiseren van waarden](/help/forms/aem-forms-value-realization-dashboard.md)
