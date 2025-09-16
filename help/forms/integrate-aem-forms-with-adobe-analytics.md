---
title: Formulieranalyse met Adobe Analytics en AEM Forms - Volledige handleiding
seo-title: "Form Analytics: Track Performance, Boost Conversions with Adobe Analytics & AEM Forms"
description: Volledige handleiding voor formulieranalyses met Adobe Analytics en AEM Forms. Traceer de prestaties van formulieren, analyseer het gebruikersgedrag, verlaag het aantal gebruikers en optimaliseer de conversies.
keywords: formulieranalyse, formulierprestaties bijhouden, analyse van formulierlocaties, optimalisatie van conversie, analyse van gebruikersgedrag, Adobe Analytics-formulieren, AEM Forms-analyse
exl-id: 0730432e-75b8-4b35-a377-ae4a2bee6c9f
feature: Adaptive Forms, Acrobat Sign
role: User, Developer
source-git-commit: ab84a96d0e206395063442457a61f274ad9bed23
workflow-type: tm+mt
source-wordcount: '7697'
ht-degree: 0%

---


# Formulieranalyse met Adobe Analytics en AEM Forms - Volledige handleiding {#integrate-aem-forms-with-adobe-analytics}

## Wat is Form Analytics?

Formulieranalyses zijn het verzamelen, meten en analyseren van gegevens over de interactie van gebruikers met uw formulieren. Het biedt inzicht in het gedrag van gebruikers, identificeert knelpunten in het proces van het invullen van formulieren en helpt formulieren te optimaliseren voor betere conversietarieven.

De analyse van formulieren gaat verder dan het bijhouden van eenvoudige verzendingen en biedt uitgebreide inzichten in elk aspect van de gebruikerservaring. Door te analyseren hoe de gebruikers met individuele vormgebieden, navigatiepatronen, en voltooiingsgedrag in wisselwerking staan, kunnen de organisaties gegevens-gedreven verbeteringen aanbrengen die beduidend bedrijfsresultaten beïnvloeden.

### Concepten van kernformulieranalyse

**het Volgen van de Interactie van de Gebruiker**
Met formulieranalyses wordt gedetailleerde informatie vastgelegd over de manier waarop gebruikers omgaan met formulieren, zoals de tijd die ze aan elk veld besteden, muisbewegingen, schuifgedrag en interactiepatronen. Deze korrelige gegevens helpen bruikbaarheidsproblemen en optimalisatiemogelijkheden te identificeren.

**Analyse van het Patroon van het Gedrag**
Door gebruikerspatronen in meerdere formuliersessies te analyseren, kunnen organisaties veelvoorkomende gebruikersreizen, standaardonderbrekingspunten en voltooide paden identificeren. Deze analyse laat gerichte verbeteringen toe die echte gebruikersbehoeften richten.

**Meting van Prestaties**
De analysegegevens van de vorm verstrekken kwantitatieve metriek die vormdoeltreffendheid, met inbegrip van omzettingspercentages, voltooiingstijden, foutenfrequenties, en indicatoren van de gebruikerstevredenheid meten. Met deze maatstaven kunt u de prestaties van het formulier op objectieve wijze beoordelen en het effect ervan optimaliseren.

### Waarom Form Analytics belangrijk is voor bedrijven

Formulieranalyse transformeert onbewerkte gebruikersinteractiegegevens naar zakelijke inzichten die meetbare verbeteringen in de belangrijkste bedrijfsmetingen stimuleren:

**Optimalisering van het Tarief van de Omzetting**
Het verlaten van de vorm is een kritieke bedrijfsuitdaging die directe opbrengst en het leiden opwekking beïnvloedt. Uit onderzoek blijkt dat 68% van de gebruikers formulieren afgeeft voordat ze het formulier invullen, waardoor formulieranalyses essentieel zijn voor het identificeren van vervolgpunten. Met de functie Formulieranalyse kunt u doelgerichte optimalisatiestrategieën voor conversie maken die de prestaties van het formulier aanzienlijk kunnen verbeteren. Effectieve optimalisatie van conversie door middel van formulieranalyse levert meetbare verbeteringen in het genereren van leads en het aanschaffen van klanten.

**de Verbetering van de Ervaring van de Gebruiker**
Als u goed begrijpt waar gebruikers mee worstelen en waar ze pijn ondervinden, kunnen organisaties vloeiender en intuïtiever formulieren maken. Dit leidt tot hogere klantentevredenheid, lagere steunkosten, en betere merkperceptie.

**gegevens-gedreven het Beslissen Maken**
In plaats van te vertrouwen op veronderstellingen of beste praktijken, verstrekt de vormanalyse concrete gegevens over de analyse van het gebruikersgedrag. Dit maakt op feiten gebaseerde optimalisatie van conversie mogelijk die aanzienlijk betere resultaten oplevert dan op intuïtie gebaseerde wijzigingen. Analyse van het gebruikersgedrag via het bijhouden van formulierprestaties zorgt ervoor dat de optimalisatie-inspanningen zich richten op de werkelijke gebruikersbehoeften in plaats van op veronderstellingen.

**Meting en Justification van het ROI**
De analysegegevens van de vorm kwantificeren het effect van optimaliseringsinspanningen, die duidelijke metriek verstrekken die bedrijfswaarde aantonen. Organisaties kunnen de directe correlatie meten tussen formulierverbeteringen en bedrijfsresultaten, zoals het genereren van leads, omzetconversie en kosten voor het aanschaffen van klanten.

**Concurrerend Voordeel**
De superieure vormervaringen worden een concurrerende differentiator in klantenverwerving. Organisaties die formulieranalyses gebruiken, kunnen de beste gebruikerservaring in hun klasse creëren die beter presteert dan concurrenten en de groei van het marktaandeel bevordert.

### Metrische gegevens van belangrijkste formulieranalyse

Effectieve formulieranalyses zijn gericht op meetwaarden die direct van invloed zijn op bedrijfsresultaten en activeerbare inzichten bieden voor optimalisatie:

**Primaire Metriek van het Succes**

- **Tarief van de Omzetting van de Vorm**: Het percentage vormmeningen die in succesvolle voorlegging resulteren - de uiteindelijke maatregel van vormdoeltreffendheid
- **Tarief van de Afschaffing van de Vorm**: Waar en waarom de gebruikers weggaan, die directe insight verstrekken in kwesties van de gebruikerservaring
- **Tijd van de Voltooiing**: Hoe lang de gebruikers nemen om vormen te voltooien, die op ingewikkeldheid en gebruikerservaring kwaliteit wijzen

**Gedetailleerde Indicatoren van Prestaties**

- **gebied-Vlakke Analytics**: Welke specifieke gebieden problemen veroorzaken, toelatend gerichte optimaliseringsinspanningen
- **Analyse van het Tarief van de Fout**: De kwesties van de Bevestiging en gebruikersfouten die succesvolle vormvoltooiing verhinderen
- **Patronen van het Gebruik van de Hulp**: Wanneer en waar de gebruikers hulp nodig hebben, wijzend op gebieden voor verbetering

**Geavanceerde Metriek van het Gedrag**

- **Analyse van het Kanaal van de Omzetting**: De reis van de gebruiker door multi-step vormen, die progressie en drop-off patronen tonen
- **Prestaties van het Apparaat en Browser**: Technische factoren die voltooiing over verschillende gebruikersmilieu&#39;s beïnvloeden
- **Diepte van de Betrokkenheid van de Gebruiker**: Tijd besteed aan vormen, de patronen van de gebiedsinteractie, en de indicatoren van de gebruikersaandacht

**BedrijfsGevolgen Metriek**

- **de Correlatie van de Kwaliteit van de Lood**: Hoe het gedrag van de vormvoltooiing op loodomzetting en klantenwaarde betrekking heeft
- **Prestaties van Source van het Verkeer**: Welke marketing kanalen drijven de high-quality vormvoorlegging
- **seizoensgebonden en Gevolgen van de Campagne**: Hoe de vormprestaties met marketing activiteiten en externe factoren variëren

## Bedrijfsvoordelen van Form Analytics

De implementatie van formulieranalyses biedt meetbare bedrijfswaarde in verschillende dimensies. Organisaties die gebruikmaken van formulieranalyses zien doorgaans aanzienlijke verbeteringen in de conversiesnelheden, de tevredenheid van de gebruiker en de operationele efficiëntie.

### &#x200B;1. Verminder de functie Formulier afbreken en verhoog de conversie

Het verlaten van de vorm is een kritieke bedrijfsuitdaging die direct opbrengst en het leiden opwekking beïnvloedt:

- **identificeer Vervolgpunten**: Spoor precies waar de gebruikers vormen verlaten om problematische gebieden of secties te identificeren
- **optimaliseer de Stroom van de Vorm**: Herschik, vereenvoudig, of verwijder gebieden die de hoogste verlaten tarieven veroorzaken
- **Verbeteringen van de Test A/B**: Test verschillende vormvariaties en meet hun effect op voltooiingstarieven
- **Mobiele Optimalisering**: Identificeer mobiele-specifieke kwesties die vormvoltooiing verhinderen
- **Real-time Controle**: Krijg direct alarm wanneer de vormprestaties degraderen

**BedrijfsEffect**: De bedrijven zien typisch significante verbetering in de tarieven van de vormomzetting na het uitvoeren van analytisch-gedreven optimalisaties.

### &#x200B;2. Ervaring en tevredenheid van gebruikers verbeteren

De analyse van formulieren biedt diepgaande inzichten in het gedrag en de pijnpunten van gebruikers:

- **Verminder de Tijd van de Voltooiing**: Identificeer gebieden die te lang duren om het proces te voltooien en te stroomlijnen
- **minimaliseer de Eigenschap van de Gebruiker**: De de foutenpatronen van het spoor en bevestigingskwesties om vormbruikbaarheid te verbeteren
- **optimaliseer de Orde van het Gebied**: Rangschik gebieden in de meest logische en gebruikersvriendelijke opeenvolging
- **verbeter Hulp en Begeleiding**: Identificeer waar de gebruikers hulp nodig hebben en verstrek gerichte hulp
- **Ervaring van 0} dwars-apparaat: Verzeker verenigbare prestaties over Desktop, tablet, en mobiele apparaten**

**BedrijfsEffect**: De betere gebruikerservaring leidt tot hogere scores van de klantentevredenheid en verhoogde merkloyaliteit.

### &#x200B;3. Maak gegevensgestuurde formulierverbeteringen

Vervang giswerk door concrete gegevens bij het optimaliseren van formulieren:

- **op bewijsmateriaal-Gebaseerde Besluiten**: Gebruik daadwerkelijke gegevens van het gebruikersgedrag eerder dan veronderstellingen om verbeteringen te begeleiden
- **Effect van de Optimalisering van de Maatregel**: Kwanteer de resultaten van vormveranderingen met voor/na analyses
- **Prioriteit Verbeteringen**: Focus op veranderingen die het grootste effect op bedrijfsmetriek zullen hebben
- **Ononderbroken Optimalisering**: Vestig aan de gang zijnde verbeteringscycli die op prestatiesgegevens worden gebaseerd
- **Belanghebbenden die** melden: Verstrek concrete metriek om vormprestaties en ROI aan te tonen

**BedrijfsEffect**: De gegevens-gedreven optimalisering levert typisch beduidend betere resultaten dan op intuïtie-gebaseerde veranderingen.

### &#x200B;4. Laadkwaliteit en verkoopefficiëntie verhogen

Met de functie Formulieranalyse kunt u niet alleen het aantal ingevulde formulieren optimaliseren, maar ook de kwaliteit van de ingevulde formulieren:

- **Lood het Scoren Integratie**: Correleer vormgedrag met loodkwaliteit en omzettingspotentieel
- **de Attributie van Source**: Begrijp welke verkeersbronnen de van de hoogste-kwaliteit vormvoorlegging produceren
- **Progressieve het Profileren**: Optimaliseer multi-step vormen om meer gekwalificeerde lood te verzamelen
- **de Inzichten van de Segmentatie**: Identificeer patronen in high-value het gedrag van de klantenvorm
- **Optimalisering van de Afhandeling van de Verkoop**: Verstrek verkoopteams van context over loodvorminteractie

**BedrijfsEffect**: De hogere kwaliteit leidt tot betere verkoopprijzen omrekeningskoersen en lagere kosten van de klantenverwerving.

### &#x200B;5. Operationele efficiëntie en kostenvermindering

Formulieranalyses zorgen voor operationele verbeteringen in de hele organisatie:

- **vermindert de Tickets van de Steun**: Identificeer en verhelpt gemeenschappelijke vormkwesties die de vraag van de klantendienst produceren
- **automatiseer Optimalisering**: Opstelling geautomatiseerde alarm en optimaliseringsregels die op prestatiesdrempels worden gebaseerd
- **Toewijzing van het Middel**: De ontwikkelingsmiddelen van de nadruk op vormen en gebieden met het hoogste bedrijfseffect
- **Controle van de Naleving**: De vormprestaties van het spoor voor regelgevende en toegankelijkheidsnaleving
- **Efficiëntie van de Integratie**: Optimaliseer vorm-aan-systeem integratie die op voorleggingspatronen wordt gebaseerd

**BedrijfsEffect**: De operationele verbeteringen kunnen vorm-gerelateerde steunkosten beduidend drukken.

### &#x200B;6. Concurrentievoordeel door superieure Forms

Met behulp van formulieranalyses kunnen organisaties hoogwaardige formulierervaringen creëren:

- **Benchmark Prestaties**: Vergelijk vormprestaties met de industriestandaarden en concurrenten
- **de Kansen van de Innovatie**: Identificeer unieke optimaliseringskansen die de concurrenten kunnen missen
- **Behoud van de Klant**: De superieure vormervaringen dragen aan algemene klantentevredenheid en behoud bij
- **Marktdifferentiatie**: De inzichten van de vormanalyse van het gebruik om concurrerende voordelen in gebruikerservaring tot stand te brengen
- **Schaalbare Optimalisering**: Pas succesvolle vormpatronen over veelvoudige producten en campagnes toe

**BedrijfsEffect**: De superieure vormervaringen kunnen een significante concurrerende differentiator in klantenverwerving worden.

## Gebruiksscenario&#39;s en voorbeelden voor formulieranalyse

Als u begrijpt hoe formulieranalyses worden toegepast op realistische scenario&#39;s, kunnen organisaties optimalisatiemogelijkheden identificeren en effectieve meetstrategieën implementeren. Hier volgen veel voorbeelden van gebruik in verschillende bedrijfstakken en typen formulieren.

### E-commerce en Retail Forms

**Afhandeling en Betaling Forms**

- **Uitdaging**: De hoge kar verlaten tijdens controleproces beïnvloedt direct inkomsten
- **Oplossing van de Analyse van de Vorm**: Het gebied van het spoor door gebied-gebied voltooiingstarieven en vormprestaties om wrijvingspunten te identificeren
- **Gemeenschappelijke Bevindingen**: De gebieden van de creditcard, de bevestiging van het verzendadres, en de stappen van de rekeningsverwezenlijking veroorzaken vaak vormbeëindiging
- **Resultaten van de Optimalisering van de Omzetting van de Omzetting**: De detailhandelaars zien typisch significante verbetering in controlevoltooiing na analytisch-gedreven optimalisering van de vormprestaties
- **Analyse van het Gedrag van de Gebruiker**: De patronen van de het verlaten van het winkelwagentje van het spoor om te begrijpen wanneer en waarom de klanten tijdens controle verlaten
- **BedrijfsEffect**: Verminderde vorm verlaten vertaalt direct aan verhoogde opbrengst en betere kosten van de klantenverwerving

**de Registratie en Garantie Forms van het Product**

- **Uitdaging**: De lage tarieven van de productregistratie die klantensteun en marketing beïnvloeden
- **Oplossing van de Analyse**: De voltooiingstarieven van de monitor en identificeert facultatieve versus vereist gebiedseffect
- **Strategie van de Optimalisering**: Verminder vereiste gebieden en verbeter mobiele ervaring
- **BedrijfsEffect**: De hogere registratiecijfers verbeteren de waarde van het klantenleven en steunen efficiency

### Loodgeneratie en B2B Forms

**Forms van het Verzoek van het Contact en van de Demo**

- **Uitdaging**: Het in evenwicht brengen van loodkwaliteit met de tarieven van de vormvoltooiing en het minimaliseren van vormbeëindiging
- **Oplossing van de Analyse van de Vorm**: De correlatie van het spoor tussen vormprestaties, vormlengte, en de kwaliteit van de loodomzetting
- **Zeer belangrijke Inzichten**: Het progressieve profileren presteert vaak lange enig-paginavormen voor omzetoptimalisering
- **Analyse van het Gedrag van de Gebruiker**: Monitor hoe de vormlengte voltooiingstarieven en de scores van de loodkwaliteit beïnvloedt
- **Resultaten van de Optimalisering van de Omzetting van de Omzetting**: De bedrijven B2B zien significante verbetering in gekwalificeerde loodgeneratie door de optimalisering van vormprestaties
- **BedrijfsEffect**: De betere vormanalyses leiden tot betere kwaliteit lood en betere tarieven van de verkoopomzetting

**Webinar en Registratie van de Gebeurtenis**

- **Uitdaging**: Het maximaliseren van gebeurtenisaanwezigheid terwijl het verzamelen van noodzakelijke informatie
- **Oplossing van de Analyse**: De registratievoltooiing van de monitor versus daadwerkelijke aanwezigheidstarieven
- **Gemeenschappelijke Patronen**: De kortere vormen verhogen registraties maar kunnen aanwezigheidskwaliteit verminderen
- **Beste praktijken**: Analyses van het gebruik om optimaal evenwicht tussen vormlengte en deelnemerkwaliteit te vinden

### Financial Services Forms

**Leningen en Krediettoepassingen**

- **Uitdaging**: Complexe multi-step toepassingen met hoge verlaten tarieven
- **Oplossing van de Analyse**: De voltooiingstarieven van het spoor bij elke stap en identificeert drop-off punten
- **Kritieke Inzichten**: Het uploaden van het document en de stappen van de inkomenscontrole veroorzaken vaak verlaten
- **Strategie van de Optimalisering**: Verstrek duidelijke voortgangsindicatoren en sparen-en-hervat functionaliteit
- **Regelgevende Overwegingen**: De analyse moet aan de vereisten van de financiële gegevensprivacy voldoen

**Citaat van de Verzekering en Vorderingen Forms**

- **Uitdaging**: Het verzamelen van gedetailleerde informatie terwijl het handhaven van gebruikersovereenkomst
- **Oplossing van Analytics**: De tijd-aan-voltooiing van de monitor en gebied-vlakke overeenkomst
- **Zeer belangrijke Bevindingen**: Auto-populatie en slimme gebreken verbeteren beduidend voltooiingstarieven
- **BedrijfsEffect**: De betere vormvoltooiing correleert direct met de tarieven van de beleidsomzetting

### Gezondheidszorg en medische Forms

**De Registratie en Inname van de Patiënt Forms**

- **Uitdaging**: Verzamel efficiënte uitvoerige medische informatie
- **Oplossing van de Analyse**: De voltooiingstarieven van het spoor over verschillende patiëntendemografie
- **Focus van de Toegankelijkheid**: De prestaties van de monitor over verschillende apparaten en toegankelijkheidshulpmiddelen
- **Prioriteit van de Optimalisering**: Mobiele optimalisering kritiek voor patiëntentevredenheid
- **Vereisten van de Naleving van de Naleving**: De naleving van HIPAA essentieel voor alle analytische implementaties

**Benoeming die Forms** plant

- **Uitdaging**: Het verminderen van no-shows terwijl het vereenvoudigen van het boeken proces
- **Oplossing van Analytics**: Correleer gedrag van de vormvoltooiing met benoeming aanwezigheid
- **Zeer belangrijke Inzichten**: De bevestiging en de herinneringsvoorkeur beïnvloedt beduidend aanwezigheid
- **de Kans van de Integratie**: Verbind vormanalyses met de systemen van het benoemingsbeheer

### Onderwijsinstelling Forms

**Toepassing en Inschrijving Forms**

- **Uitdaging**: Het beheren van complexe multi-step toepassingen met documentvereisten
- **Oplossing van Analytics**: De voltooiingstarieven van het spoor over verschillende toepassingsstadia
- **Kritieke Metriek**: Tijd-aan-voltooiing en sparen-en-hervat gebruikspatronen
- **Nadruk van de Optimalisering**: De mobiele ervaring belangrijker voor studententstoepassingen
- **Seizoensgebonden Overwegingen**: De prestaties variëren beduidend tijdens toepassingsperiodes

**Registratie van de cursus en Terugkoppeling Forms**

- **Uitdaging**: Het maximaliseren van studentenbetrokkenheid met administratieve processen
- **Oplossing van Analytics**: De voltooiingstarieven van de monitor en identificeert de kwesties van de gebruikerservaring
- **Zeer belangrijke Inzichten**: De integratie met studentenportals verbetert voltooiingstarieven
- **Ononderbroken Verbetering**: Regelmatige analytische overzicht essentieel voor semester-over-semester optimalisering

### Algemene scenario&#39;s voor formulieranalyse

**multi-Step Optimalisering van de Vorm**

Formulieren die uit meerdere stappen bestaan, hebben doorgaans een conversiesnelheid die 86% hoger ligt dan formulieren die uit één pagina bestaan, mits deze correct zijn geoptimaliseerd:

- **Step-by-Step Analyse**: De voltooiingstarieven van het spoor bij elke vormstap
- **Effect van de Indicator van de Voortgang**: Maatregel hoe de vooruitgangsbars voltooiingstarieven beïnvloeden
- **sparen-en-hervat Gebruik**: Monitor hoe het ontwerp sparen definitieve voltooiing beïnvloedt
- **Mobiele versus de Prestaties van de Desktop**: Vergelijk voltooiingstarieven over apparaten

**gebied-Vlakke Analyse van Prestaties**

- **Vereiste vs. Facultatieve Gebieden**: Analyseer effect van gebiedsvereisten op voltooiing
- **Optimalisering van de Orde van het Gebied**: Test verschillende gebiedsopeenvolgingen voor optimale stroom
- **Patronen van de Fout van de Bevestiging**: Identificeer gemeenschappelijke gebruikersfouten en verbeter bevestiging
- **de Doeltreffendheid van de Tekst van de Hulp**: Het effect van de maatregel van gebiedsbegeleiding op voltooiingstarieven

**seizoensgebonden en de Prestaties van de Campagne**

- **Analyse van Source van het Verkeer**: Vergelijk vormprestaties over marketing kanalen
- **seizoensgebonden Variaties**: Spoor hoe de vormprestaties door het jaar veranderen
- **Integratie van de Campagne**: Correleer vormanalyses met de prestaties van de marketing campagne
- **A/B het Testen Integratie**: Analyses van het gebruik om testvariaties te meten en onophoudelijk te optimaliseren

## Implementatiescenario&#39;s voor real-world formulieranalyse

Als u bepaalde implementatiescenario&#39;s begrijpt, kunnen organisaties formulieranalyses effectief toepassen in verschillende zakelijke contexten. Deze voorbeelden uit de praktijk tonen aan hoe het volgen en het omzetten van de vormprestaties meetbare bedrijfsresultaten leveren.

### Optimalisatie van e-commerce-afhandeling

**Scenario**: Online retailer die hoge kartontroeping tijdens controle ervaart

- **de Implementatie van de Analyse van de Vorm**: De verlaten van het karretje van het spoor op vormniveau met gebied-door-gebied analyse
- **Zeer belangrijke Bevindingen**: De voltooiing van de vorm van de betaling daalde beduidend bij de stap van de creditcardcontrole
- **Strategie van de Optimalisering van de Omzetting**: Vereenvoudigde betalingsvorm, toegevoegde voortgangsindicatoren, geoptimaliseerde mobiele ervaring
- **Resultaten**: Aanzienlijk verminderde vormbeëindiging en verhoogde opbrengst
- **Analyse van het Gedrag van de Gebruiker**: De geïdentificeerde mobiele gebruikers hadden hogere verlaten tarieven, die tot mobiel-eerste redesign leiden

### Formulieroptimalisatie voor het genereren van leads

**Scenario**: B2B softwarebedrijf dat met lage kwaliteit leidt van contactvormen worstelt

- **Uitdaging van de Prestaties van de Vorm**: De hoge tarieven van de vormvoltooiing maar slechte lood-aan-klant omzetting
- **Oplossing van Analytics**: Correleer vormvoltooiingsgedrag met loodkwaliteit en verkoopresultaten
- **Benadering van de Optimalisering**: Geïmplementeerde progressieve het profileren en lood het scoren integratie
- **BedrijfsEffect**: De significante verbetering van loodkwaliteit en de verhoging van verkoop-gekwalificeerde lood
- **Optimalisering van de Omzetting**: Verminderde vormbeëindiging terwijl het verbeteren van loodkwalificatie

### Optimalisatie van registratie en aan boord nemen

**Scenario**: Het platform van SaaS met hoge signaleringsmislukking tijdens onboarding proces

- **Analyse van het Gedrag van de Gebruiker**: De tarieven van de de signaalvoltooiing van het spoor en identificeren onboarding knelpunten
- **de Inzichten van de Analyse van de Vorm**: De significante gebruikersafgang kwam tijdens de stap van de rekeningscontrole voor
- **Strategie van de Optimalisering**: Gestroomlijnd verificatieproces, toegevoegde sparen-en-hervat functionaliteit
- **Resultaten**: Aanzienlijk verhoogde signaalvoltooiing en betere tarieven van de gebruikersactivering
- **Gevolgen op lange termijn**: Betere onboarding voltooiing gecorreleerd met hogere waarde van het klantenleven

## Functies voor formulieranalyse in Adobe Analytics

Adobe Analytics biedt organisaties de mogelijkheid om formulieren op bedrijfsniveau te volgen, zodat ze gedetailleerde inzichten kunnen vastleggen over gebruikersinteracties met hun formulieren. De naadloze integratie met AEM Forms biedt zowel krachtige out-of-the-box analyses als geavanceerde aanpassingsopties die geschaald kunnen worden uitgebreid met bedrijfsbehoeften.

### Waarom Adobe Analytics kiezen voor Form Analytics

**onderneming-Schaal Prestaties**
Adobe Analytics verwerkt miljoenen formulierinteracties zonder dat de prestaties afnemen, waardoor het ideaal is voor websites met veel verkeer en complexe bedrijfsomgevingen. De robuuste infrastructuur van het platform zorgt voor betrouwbare gegevensverzameling, zelfs tijdens piekgebruiksperiodes.

**Geavanceerde de Segmenteringsmogelijkheden**
In tegenstelling tot basishulpmiddelen voor formulieranalyse, maakt Adobe Analytics geavanceerde gebruikerssegmentatie mogelijk op basis van gedrag, demografie, verkeersbronnen en aangepaste bedrijfscriteria. Dit staat voor gerichte optimaliseringsstrategieën toe die specifieke gebruikersgroepen en scenario&#39;s richten.

**Echte - tijdInzichten en het Alarm**
Bewaak de prestaties van formulieren op dezelfde manier als bij realtime dashboards en geautomatiseerde waarschuwingen. Identificeer en reageer onmiddellijk op kwesties, die potentiële opbrengstverlies van vormproblemen of prestatiesdegradatie verhinderen.

### Buiten-de-doos het Volgen Mogelijkheden

AEM Forms integreert naadloos met [ Adobe Analytics ](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/overview.html?lang=en) om prestatiesmetriek voor uw gepubliceerde vormen automatisch te vangen en te volgen. U kunt het gedrag van zowel voor authentiek verklaarde als anonieme gebruikers zonder extra configuratie controleren.

Alvorens vormanalyses uit te voeren, zorg ervoor uw [ milieu van AEM Forms behoorlijk wordt gevormd ](/help/forms/setup-forms-cloud-service.md) en u hebt [ uw adaptieve vormen ](/help/forms/creating-adaptive-form-core-components.md) gecreeerd gebruikend of de Componenten van de Kern of [ Componenten van de Stichting ](/help/forms/creating-adaptive-form.md).

**het Uitgebreide Volgen van de Gebeurtenis van de Vorm:**

Adobe Analytics legt automatisch een volledig beeld van de interactie van het gebruikersformulier vast:

- **de Vorm geeft** terug: De beelden en de meningen van het spoor om bereik en aanvankelijke overeenkomst te begrijpen
- **de Indieningen van de Vorm**: De succesvolle voltooiing van de monitor met gedetailleerde voorleggingscontext en gebruikersreisgegevens
- **Analyse van de Afschaffing van de Vorm**: Vang nauwkeurige verlaten punten met gebied-vlakke granulariteit en gebruikerszittingscontext
- **het Volgen van de Fout van de Bevestiging**: De types van de fouten van het verslag, frequentie, en resolutiepatronen om bruikbaarheidskwesties te identificeren
- **Gebruik van de Inhoud van de Hulp**: Monitor wanneer de gebruikers tot hulpmiddelen toegang hebben, wijzend op gebieden van verwarring of ingewikkeldheid
- **gebied-Vlakke Interacties**: De individuele gebiedsbetrokkenheid van het spoor, bestede tijd, en interactiepatronen
- **Ontwerp sparen Gedrag**: Begrijp gebruikersintentie en vormingewikkeldheid door sparen-en-hervat gebruikspatronen
- **het Volgen van de Zitting 1}: Volg gebruikers over veelvoudige vormzittingen om voltooiingsreizen te begrijpen**

**Geavanceerde Inzichten van het Gedrag:**

- **Tijd-op-Gebied Analyse**: Meet hoe lang de gebruikers aan elk vormgebied uitgeven om complexiteitskwesties te identificeren
- **Patronen van de Beweging van de Muis**: De aarzeling van de gebruiker van het spoor en overeenkomst door cursorgedragsanalyse
- **het Volgen van de Diepte van het Schuiven**: Begrijp hoe de gebruikers door lange vormen navigeren en optimale vormlengte identificeren
- **Patronen van de Terugwinning van de Fout**: Analyseer hoe de gebruikers aan antwoorden en van bevestigingsfouten terugkrijgen

### Aangepaste gebeurtenissen bijhouden

Naast standaardformuliergebeurtenissen biedt Adobe Analytics geavanceerde aangepaste tracking:

- **zaken-Specifieke Metriek**: Bepaal douanegebeurtenissen gebruikend de regelredacteur om organisatie-specifieke vorminteractie te volgen
- **Toewijzing van de Reis van de Gebruiker**: Creeer douanegebeurtenissen om complexe gebruikerspaden door multi-step vormen te volgen
- **Analyse van het Kanaal van de Omzetting**: Opstelling douanegebeurtenissen om specifieke omzettingspunten en drop-off stadia te meten
- **Gebeurtenissen van de Integratie**: De vorminteractie van het spoor met externe systemen en APIs

### Geavanceerde rapportfuncties

Adobe Analytics biedt rapporteringsmogelijkheden op bedrijfsniveau voor formulierprestaties:

- **Echt - tijd dashboards**: De prestaties van de vorm en gebruikersinteractie van de monitor aangezien zij gebeuren
- **de Analyse van de Segmentatie**: Analyseer vormprestaties over verschillende gebruikersgroepen, verkeersbronnen, en demografie
- **Visualisatie van de Trechter**: visualiseer gebruikersvooruitgang door multi-step vormen en identificeer optimalisatiemogelijkheden
- **Analyse van de Cohort**: De verbeteringen van de vormprestaties van het spoor in tijd en maatregel optimaliseringseffect
- **kruis-Apparaat het Volgen**: Begrijp hoe de gebruikers met vormen over verschillende apparaten en zittingen in wisselwerking staan

### Voordelen van integratie

De integratie met Adobe Analytics en AEM Forms biedt unieke voordelen:

- **Verenigde Platform van Gegevens**: Combineer vormanalyses met bredere website en marketing analyses
- **de Integratie van Adobe Experience Cloud**: Verbindingen van de hefboomwerking met Adobe Target, Campagne, en andere oplossingen van Experience Cloud
- **Veiligheid van de Onderneming**: Ingebouwde naleving van de verordeningen van de gegevensprivacy en de vereisten van de ondernemingsveiligheid
- **Scalable Architectuur**: Verwerk high-volume vorminteractie zonder prestatieseffect
- **Professionele Steun**: De toegang tot de ondernemingssteun en optimalisatieservices van Adobe

Na het uitvoeren van de integratiestappen die in dit artikel worden beschreven, kunt u uitvoerige rapporten in [!DNL Adobe Analytics] vormen en bekijken, zoals aangetoond in de volgende video:

>[!VIDEO](https://video.tv.adobe.com/v/337262)

## Belangrijke metagegevens voor formulieranalyse die moeten worden bijgehouden

Voor een geslaagde implementatie van formulieranalyses moet u zich richten op meetgegevens die direct van invloed zijn op de bedrijfsresultaten. Als u precies begrijpt welke maatstaven u wilt gebruiken, kunnen organisaties gegevensgestuurde beslissingen nemen en de prestaties van formulieren effectief optimaliseren.

### Primaire prestatiemetingen

**Tarief van de Omzetting van de Vorm**

- **Definitie**: Percentage vormmeningen die in succesvolle voorlegging resulteren
- **Berekening**: (Van de Indieningen van de Vorm/van de Mening van de Vorm) × 100
- **BedrijfsEffect**: Verwant direct met de productie van lood en opbrengstdoelstellingen
- **Doel van de Optimalisering**: Varieert door industrie en vormingewikkeldheid

**het Tarief van de Afschaffing van de Vorm**

- **Definitie**: Percentage gebruikers die beginnen maar geen vormen voltooien
- **Berekening**: (De Begin van de Vorm - de Voltooiingen van de Vorm) / de Begint van de Vorm × 100
- **Kritieke Inzichten**: Identificeert de kwesties van de gebruikerservaring en optimaliseringskansen
- **Benchmark**: De hoge dalingspercentages wijzen typisch op significante bruikbaarheidsproblemen

**Gemiddelde Tijd van de Voltooiing**

- **Definitie**: Gemiddelde tijdgebruikers besteden het voltooien van vormen van begin aan voorlegging
- **Focus van de Analyse**: Identificeer vormen die te lang nemen en gebruikers kunnen frustreren
- **Doel van de Optimalisering**: De grondigheid van het saldo met de efficiency van de gebruikerservaring
- **Segmentatie**: Vergelijk voltooiingstijden over apparaten, gebruikerstypes, en verkeersbronnen

### Analyse op veldniveau

**de Tarieven van de Afschaffing van het Gebied**

- **Meting**: Percentage gebruikers die vormen op specifieke gebieden verlaten
- **de Waarde van de Optimalisering**: Identificeert problematische gebieden die vereenvoudiging of verwijdering vereisen
- **Gemeenschappelijke Kwesties**: De complexe bevestigingsvereisten, onduidelijke instructies, of technische problemen
- **Punten van de Actie**: Geef voorrang aan optimaliseringsinspanningen op gebieden met hoogste verlaten tarieven

**Patronen van de Interactie van het Gebied**

- **klik-door Tarieven**: Percentage gebruikers die met specifieke vormgebieden in dienst nemen
- **Tijd-op-Gebied**: Gemiddelde tijdgebruikers besteden aan individuele gebieden
- **Tarieven van de Fout**: Frequentie van bevestigingsfouten voor specifieke gebieden
- **Gebruik van de Hulp**: Hoe vaak de gebruikers tot hulpinhoud voor bepaalde gebieden toegang hebben

**de Tarieven van de Voltooiing van het Gebied**

- **Progressieve Analyse**: De voltooiingstarieven van het spoor aangezien de gebruikers zich door vormgebieden bewegen
- **Vervalidentificatie**: Identificatie van het Punt nauwkeurige plaatsen waar de gebruikers vormen verlaten
- **Prioriteit van de Optimalisering**: De verbeteringen van de nadruk op gebieden met steepste daling van het voltooiingstarief

### Metrische gegevens gebruikerservaring

**Analyse van het Tarief van de Fout**

- **Fouten van de Bevestiging**: Frequentie en types van mislukkingen van de vormbevestiging
- **Technische Fouten**: Systeem-vlakke kwesties die vormfunctionaliteit beïnvloeden
- **Patronen van de Fout van de Gebruiker**: De gemeenschappelijke fouten maken de gebruikers wanneer het voltooien van vormen
- **het Volgen van de Resolutie**: Monitor hoe de verbeteringen van het foutentarief algemene omzetting beïnvloeden

**Mobiele versus de Prestaties van de Desktop**

Mobiele formulieren maken doorgaans een 30% hogere wachttijd in vergelijking met desktopversies, waardoor apparaatspecifieke optimalisatie van cruciaal belang is:

- **apparaat-Specifieke Tarieven van de Omzetting**: Vergelijk vormprestaties over apparatentypes
- **Responsieve Gevolgen van het Ontwerp**: Meet hoe de mobiele optimalisering voltooiingstarieven beïnvloedt
- **de Bruikbaarheid van de Interface van de Aanraak**: Analyseer mobiele-specifieke interactiepatronen
- **Reizigersreis over apparaat**: De gebruikers van het spoor die vormen op één apparaat beginnen en op een andere voltooien

**Metriek van de Lading en van Prestaties van de Pagina**

Forms die in minder dan 3 seconden laadt, heeft 70% hogere voltooiingssnelheden dan langzamere formulieren:

- **Tijd van de Lading van de Vorm**: Tijd die voor vormen wordt vereist volledig terug te geven en interactief te worden
- **Tijd van de Reactie van het Gebied**: Latentie tussen gebruikersinput en systeemreactie
- **Tijd van de Verwerking van de Verzending**: Duur van vormvoorlegging aan bevestiging
- **Effect van Prestaties**: Correlatie tussen ladingstijden en verlaten tarieven

### Geavanceerde analytische gegevens

**Analyse van de Segmentatie van de Gebruiker**

- **Prestaties van Source van het Verkeer**: Vergelijk de tarieven van de vormomzetting over marketing kanalen
- **Geografische Prestaties**: Analyseer de tarieven van de vormvoltooiing door plaats en taal
- **Analyse van het Type van Gebruiker**: Vergelijk prestaties tussen nieuwe en terugkerende gebruikers
- **Demografische Inzichten**: Begrijp hoe de verschillende gebruikersgroepen met vormen in wisselwerking staan

**Analyse van het Kanaal van de Omzetting**

- **Meerdere-Stap Progressie van de Vorm**: De vooruitgang van de gebruiker van het spoor door complexe vormen
- **stadium-door-Stadium Omzetting**: De voltooiingstarieven van de maatregel bij elke vormstap
- **Optimalisering van de Trechter**: Identificeer en richt knelpunten in vormvooruitgang
- **A/B het Testen Integratie**: Vergelijk de prestaties van de trechter over vormvariaties

**BedrijfsGevolgen Metriek**

- **Scoring van de Kwaliteit van de Lood**: Correleer vormvoltooiingsgedrag met lood omzettingspercentages
- **Attributen van de Opbrengst**: Verbind vormbijdragen met daadwerkelijke bedrijfsresultaten
- **Waarde van het Leven van de Klant**: Analyseer waarde op lange termijn van gebruikers die door verschillende vormen worden verworven
- **Kosten per Verwerving**: Bereken marketing efficiency die op de gegevens van vormprestaties wordt gebaseerd

In de volgende afbeelding ziet u de handelingen die u moet uitvoeren voordat u rapporten kunt weergeven in [!DNL Adobe Analytics] :

![ Overzicht van Analytics ](assets/analytics-workflow.png)

## Formulieranalyse instellen voor AEM Forms

Voor het implementeren van formulieranalyses met Adobe Analytics en AEM Forms is een systematische configuratie voor meerdere componenten vereist. Deze sectie verstrekt uitvoerige opstellingsbegeleiding, eerste vereisten, en beste praktijken voor succesvolle implementatie.

### Vereisten en vereisten

Voordat u begint met de implementatie van de formulieranalyse, moet u controleren of uw omgeving aan de volgende vereisten voldoet:

>[!NOTE]
>
>Als u kwesties tijdens opstelling ontmoet, verwijs naar onze uitvoerige [ het oplossen van problemengids van AEM Forms ](/help/forms/troubleshooting-installation-and-configuration.md) voor installatie en configuratieproblemen.

**Toegang van Adobe Experience Cloud**

- Geldige Adobe Experience Cloud-organisatie met Adobe Analytics-licenties
- Administratieve toegang tot Adobe Analytics- en AEM Forms-omgevingen
- Toegang tot Adobe Launch (gegevensverzameling) voor tagbeheer en configuratie

**het Milieu van AEM Forms**

- [ AEM Forms as a Cloud Service ](/help/forms/setup-forms-cloud-service.md) of AEM Forms 6.5+ (op-gebouw/installaties van AMS)
- Forms-mogelijkheden voor schrijven en publiceren ingeschakeld
- Verzeker {de optie van 0} Forms beschikbaar is [ in uw milieu van AEM](/help/forms/troubleshooting-installation-and-configuration.md#forms-option-is-unavailable)
- [ de Aangepaste Componenten van de Kern van Forms ](/help/forms/creating-adaptive-form-core-components.md) of [ beschikbare Componenten van de Stichting ](/help/forms/creating-adaptive-form.md)

**Technische Vereisten**

- Moderne webbrowsers met JavaScript ingeschakeld voor het bijhouden van formulieranalyses
- HTTPS-protocolimplementatie voor veilige gegevenstransmissie
- Geschikte firewall- en netwerkconfiguraties voor Adobe Analytics-gegevensverzameling

**Toestemmingen en Toegang**

- Adobe Analytics Administrator-rol voor configuratie van rapportsuite
- AEM Forms Author-machtigingen voor formulierconfiguratie en -publicatie
- Adobe Launch Developer-toegang voor het implementeren van tags en het maken van regels

### Step-by-Step Implementation Guide

#### &#x200B;1. Adobe Analytics configureren {#Configure-adobe-analytics}

Maak voordat u [!DNL Adobe Analytics] configureert:

- Een Adobe ID aan login aan [ Adobe Experience Cloud ](https://experience.adobe.com/#/home).
- A [ rapportreeks ](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html).


### AEM Forms- en [!DNL Adobe Analytics] extensies installeren {#install-extensions}

Voer de volgende stappen uit om AEM Forms en [ Adobe Analytics ](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/analytics/overview.html) uitbreidingen te vormen:

1. Meld u aan bij Adobe Experience Cloud en selecteer de gewenste naam voor het bedrijf.

1. Selecteer **[!UICONTROL Launch/Data Collection]** en selecteer **[!UICONTROL Go to Launch/Data Collection]** .

1. Selecteer **[!UICONTROL New property]** en geef een naam op voor de configuratie.

1. Geef een domeinnaam op en selecteer **[!UICONTROL Save]** om de eigenschap op te slaan.

1. Selecteer de configuratienaam die beschikbaar is in de lijst Tageigenschappen.

1. Selecteer **[!UICONTROL Authoring]** in de sectie **[!UICONTROL Extensions]** .

1. Selecteer **[!UICONTROL Catalog]** en selecteer **[!UICONTROL Install]** voor de extensie **[!UICONTROL Adobe Experience Manager Forms]** . **[!UICONTROL Adobe Experience Manager Forms]** vertoningen in de lijst van geïnstalleerde uitbreidingen beschikbaar in het **Geïnstalleerde** lusje.

1. Selecteer **[!UICONTROL Install]** voor de extensie **[!UICONTROL Adobe Analytics]** .
1. Selecteer de naam van de rapportsuite in de vervolgkeuzelijsten **[!UICONTROL Development Report Suites]** , **[!UICONTROL Staging Report Suites]** en **[!UICONTROL Product Report Suites]** en selecteer **[!UICONTROL Save]** om de extensie op te slaan.

### Gegevenselementen configureren {#configure-data-elements}

U kunt om het even welke gevormde gegevenselementen in een regel selecteren die voor een gebeurtenis wordt gecreeerd. Wanneer een gebeurtenis plaatsvindt op een adaptief formulier, stuurt AEM Forms deze gegevenselementen naar [!DNL Adobe Analytics] .

Nadat u de extensie **[!UICONTROL Adobe Experience Manager Forms]** hebt geïnstalleerd, kunt u de volgende gegevenselementen maken:

<table>
 <tbody>
  <tr>
   <td>FieldName</th>
   <td>FieldTitle</th>
   <td>FormInstance</th>
  </tr>
  <tr>
   <td>FormName<br /> </td>
   <td>FormTitle <br /> </td>
   <td>PageName</td>
  </tr>
  <tr>
   <td>PageURL <br /> </td>
   <td>PanelTitle <br /> </td>
   <td>TimeSpent</td>
  </tr>
 </tbody>
</table>

Voer de volgende stappen uit om gegevenselementen te configureren:

1. Selecteer **[!UICONTROL Authoring]** in de sectie **[!UICONTROL Data Elements]** .

1. Selecteer **[!UICONTROL Create New Data Element]** .

1. Geef een naam op voor het gegevenselement. Bijvoorbeeld het gegevenstype Formuliertitel voor het gegevenstype FormTitle.

1. Geef **[!UICONTROL Adobe Experience Manager Forms]** op als de naam van de extensie.

1. Selecteer de **[!UICONTROL Data Element Type]** .

1. Selecteer **[!UICONTROL Save]** om het gegevenselement op te slaan.

>[!VIDEO](https://video.tv.adobe.com/v/337472)

### Regels configureren {#configure-rules}

Voer de volgende stappen uit om regels te maken op basis van de extensie **[!UICONTROL Adobe Experience Manager Forms]** :

1. Selecteer **[!UICONTROL Authoring]** in de sectie **[!UICONTROL Rules]** .

1. Selecteer **[!UICONTROL Create New Rule]** .

1. Geef een naam voor de regel op. Formulier verzenden bijvoorbeeld om formulierverzendingen op te nemen.

1. Selecteer **[!UICONTROL Events]** in de sectie **[!UICONTROL Add]** .

1. Geef **[!UICONTROL Adobe Experience Manager Forms]** op als de naam van de extensie.

1. Selecteer het gebeurtenistype. De invoer voor het veld **[!UICONTROL Name]** wordt automatisch gevuld op basis van het geselecteerde gebeurtenistype.

1. Selecteer **[!UICONTROL Keep Changes]** om de gebeurtenis op te slaan.

1. Selecteer **[!UICONTROL Actions]** in de sectie **[!UICONTROL Add]** .

1. Geef **[!UICONTROL Adobe Analytics]** op als de naam van de extensie.

1. Selecteer **[!UICONTROL Set Variables]** als het handelingstype. De volgende opties zijn beschikbaar in de vervolgkeuzelijst:

   - **[!UICONTROL Set Variables]**: Gebruik dit actietype om het gebeurtenistype te definiëren waarvoor de geselecteerde gegevenselementen van AEM Forms naar [!DNL Adobe Analytics] worden verzonden.

   - **[!UICONTROL Send Beacon]**: Gebruik dit actietype om gegevens van AEM Forms naar [!DNL Adobe Analytics] te verzenden.

   - **[!UICONTROL Clear Variables]**: Gebruik dit actietype om het gegevenstraject te wissen, zodat de gebeurtenis zich slechts eenmaal registreert in [!DNL Adobe Analytics] .

     Het wordt aanbevolen het actietype **[!UICONTROL Set Variables]** te gebruiken om de gebeurtenis en gegevenselementen te configureren, vervolgens **[!UICONTROL Send Beacon]** te gebruiken om gegevens te verzenden en vervolgens **[!UICONTROL Clear Variables]** te gebruiken om het gegevenstraject te wissen.

1. In de **[!UICONTROL Props]** sectie, kaart de opties van de rapportreeks beschikbaar in de drop-down lijst met de gegevenselementen die gebruikend [ worden bepaald gegevenselementen ](#configure-data-elements) vormen.

   Bijvoorbeeld, om **het gegevenselement van de Titel van de Vorm** van AEM Forms naar [!DNL Adobe Analytics] te verzenden wanneer u een vorm voorlegt:
   1. In de **[!UICONTROL Props]** sectie, selecteer een steun voor Titel van de Vorm beschikbaar in de rapportreeks en selecteer dan ![ pictogram van het Gegevensbestand ](assets/database-icon.svg) om het aan Titel in kaart te brengen van de Vorm die in [ wordt gecreeerd vormt gegevenselementen ](#configure-data-elements).

      ![ bepalen-props ](assets/define-props.png)

   1. Selecteer **[!UICONTROL Add Another]** om meer gegevenselementen aan de lijst toe te voegen.

1. Selecteer in de sectie **[!UICONTROL Events]** een gebeurtenis uit de opties in de rapportsuite en selecteer **[!UICONTROL Keep Changes]** .

1. Selecteer + in de sectie **[!UICONTROL Actions]** en geef **[!UICONTROL Adobe Analytics]** op als de naam van de extensie.

1. Selecteer **[!UICONTROL Send Beacon]** als het handelingstype. Selecteer **[!UICONTROL s.t()]** in het rechterdeelvenster om gegevens naar [!DNL Adobe Analytics] te verzenden en behandel deze als een paginaweergave of **[!UICONTROL s.tl()]** om gegevens naar [!DNL Adobe Analytics] te verzenden en behandel deze niet als een paginaweergave. Selecteer **[!UICONTROL Keep Changes]** .

1. Selecteer + in de sectie **[!UICONTROL Actions]** en geef **[!UICONTROL Adobe Analytics]** op als de naam van de extensie.

1. Selecteer **[!UICONTROL Clear Variables]** als het handelingstype. Selecteer **[!UICONTROL Keep Changes]**. Nadat u deze stappen hebt uitgevoerd, wordt de sectie **[!UICONTROL Actions]** weergegeven als:
   ![ Configuratie van Acties ](assets/actions-config.png)

   Pas de sectie **[!UICONTROL Actions]** aan uw wensen aan. Bijvoorbeeld, kunt u twee **verzenden de stappen van het Baken** in een stroom van de Actie bepalen om gegevens naar [!DNL Adobe Analytics] te verzenden en het als paginamening in één stap te behandelen en gegevens naar [!DNL Adobe Analytics] te verzenden en het niet als paginamening in de tweede stap te behandelen.

   ![ Configuratie van Acties ](assets/actions-config-2.png)

1. Selecteer **[!UICONTROL Save]** om de regel op te slaan.

   U kunt regels maken voor alle gebeurtenistypen, zoals Verlaten, Fout, Veldbezoek, Help, Rendering, Opslaan en Verzenden.

>[!VIDEO](https://video.tv.adobe.com/v/337425)


### Stroom publiceren {#publish-flow}

Nadat u de gegevenselementen hebt gemaakt en gebruikt in regels, publiceert u de configuratie voor het verzamelen van formuliergegevens in [!DNL Adobe Analytics] .

Voer de volgende stappen uit om de configuratie te publiceren:

1. Selecteer **[!UICONTROL Publishing]** in de sectie **[!UICONTROL Publishing Flow]** .

1. Selecteer **[!UICONTROL Add Library]** en geef een naam op en selecteer de omgeving voor de bibliotheek.

1. Selecteer **[!UICONTROL Add All Changed Resources]** en selecteer vervolgens **[!UICONTROL Save & Build to Development]** .

1. In de **[!UICONTROL Development]** sectie, selecteer ![ Meer opties ](assets/more-options-icon.svg) en selecteer dan **[!UICONTROL Approve & Publish to Production]**.

1. Controleer of de wijzigingen en de publicatiestroom binnenkort worden weergegeven in de sectie **[!UICONTROL Published]** .

![ publiceer Stroom ](assets/publish-flow.png)

## &#x200B;2. AEM Forms configureren {#configure-aem-forms}

Alvorens een configuratie van de Lancering van Adobe tot stand te brengen, creeer een [ Configuratie van Adobe IMS gebruikend de Lancering van Adobe als Oplossing van de Wolk ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/connect-aem-launch-adobe-io.html).

### Adobe-startconfiguratie maken {#create-adobe-launch-configuration}

Voer de volgende stappen uit om een Adobe-startconfiguratie te maken:

1. Ga in de AEM Forms Author-instantie naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Launch Configurations]** .

1. Selecteer een map om de configuratie te maken en selecteer **[!UICONTROL Create]** .

1. Geef een titel voor de configuratie op in het veld **[!UICONTROL Title]** .

1. Selecteer de [ bijbehorende configuratie van Adobe IMS ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-launch/connect-aem-launch-adobe-io.html).

1. Selecteer de naam van het gebruikte bedrijf terwijl [ het vormen Adobe Analytics ](#Configure-adobe-analytics).

1. Selecteer de naam van het gecreeerde bezit terwijl [ het vormen Adobe Analytics ](#install-extensions).

1. Selecteer **[!UICONTROL Save & Close]** .

1. Publiceer de configuratie.

### [!DNL Adobe Analytics] inschakelen voor een adaptief formulier {#enable-analytics-adaptive-form}

De [!DNL Adobe Launch] -configuratie gebruiken in een bestaand adaptief formulier:

1. Ga in de AEM Forms Author-instantie naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Selecteer het adaptieve formulier en selecteer **[!UICONTROL Properties]** .
1. In het **[!UICONTROL Basic]** lusje, selecteer de [ gebruikte configuratiecontainer ](#create-adobe-launch-configuration) terwijl het creëren van de configuratie van de Lancering van Adobe.
1. Selecteer **[!UICONTROL Save & Close]**. Het adaptieve formulier is ingeschakeld voor [!DNL Adobe Analytics] .
1. Publiceer het formulier.

Nadat u [!DNL Adobe Analytics] voor een adaptieve vorm toelaat, kunt u [ bevestigen ](https://experienceleague.adobe.com/docs/launch-learn/implementing-in-websites-with-launch/implement-solutions/analytics.html?lang=en#validate-the-page-view-beacon) als er een aangewezen stroom van de gegevensgebeurtenis tussen AEM Forms en [!DNL Adobe Analytics] is. De integratie van AEM Forms met Adobe Analytics is voltooid. U kunt nu [ vormen en rapporten in Adobe Analytics ](#view-reports-adobe-analytics) bekijken.

### Regels maken om aangepaste gebeurtenissen vast te leggen (optioneel) {#capture-custom-events}

Maak regels voor specifieke velden van een adaptief formulier met behulp van een regeleditor om analysegegevens van een adaptief formulier te verzenden naar [!DNL Adobe Analytics] .

In een proces in twee fasen definieert u een regel voor een veld in een adaptieve vorm. De regel verzendt een gebeurtenis. De naam van de gebeurtenis wordt toegewezen aan een aangepaste vastleggebeurtenis in Adobe Launch.

U kunt als volgt regels maken met behulp van een regeleditor:

1. Selecteer het gebied en selecteer ![ Redacteur van de Regel ](assets/rule-editor-icon.svg) om de pagina van de regelredacteur te openen.
1. Definieer een voorwaarde in de sectie [!UICONTROL When] van de regel.
1. Selecteer in de sectie [!UICONTROL Then] van de regel de optie **[!UICONTROL Dispatch Event]** in de vervolgkeuzelijst **[!UICONTROL Select Action]** .
1. Geef de naam van de gebeurtenis op in het veld **[!UICONTROL Type Event Name]** .

Bijvoorbeeld, als de geboortedatum vóór een bepaalde datum is, verzendt AEM Forms de **gebeurtenis van de Veiligheid**.

![ de Gebeurtenis van de Verzending ](assets/security-event.png)

U kunt als volgt de gebeurtenis toewijzen aan een aangepaste vastleggebeurtenis in [!DNL Adobe Analytics] :

1. [ creeer een regel ](#configure-rules).

1. Selecteer **[!UICONTROL Events]** in de sectie **[!UICONTROL Add]** .

1. Geef **[!UICONTROL Adobe Experience Manager Forms]** op als de naam van de extensie.

1. Selecteer **[!UICONTROL Capture Custom Event]** in de vervolgkeuzelijst **[!UICONTROL Event Type]** .

1. Geef de naam op van de gebeurtenis die u in stap 4 hebt opgegeven tijdens het maken van een regel met de regeleditor.

1. Selecteer **houden Veranderingen** en voer de rest acties uit die in [ worden gespecificeerd vormen Regels ](#configure-rules).

## &#x200B;3. Configureer en bekijk rapporten in [!DNL Adobe Analytics] {#view-reports-adobe-analytics}

Nadat u een adaptief formulier hebt geconfigureerd om gebeurtenisgegevens naar [!DNL Adobe Analytics] te verzenden, kunt u rapporten weergeven in [!DNL Adobe Analytics] :

1. Selecteer ![ Uitgezochte Product ](assets/select-analytics.png) en selecteer **[!UICONTROL Analytics]**.

1. Selecteer **[!UICONTROL Create Project]** en selecteer **[!UICONTROL Blank project]** .

1. Selecteer de naam van de rapportsuite in de vervolgkeuzelijst rechtsboven in de vrije vorm.

1. Specificeer **Titel van de Vorm** in de **[!UICONTROL Search dimension items]** tekst om alle vormtitels te bekijken.

1. Zet de titel van het aangepaste formulier neer in het tekstvak **[!UICONTROL Drop a segment here (or any other component)]** .

1. Zet vanuit de sectie **[!UICONTROL Metrics]** de gebeurtenissen neer om bij te houden naar het tekstvak **[!UICONTROL Drop a metric here (or any other component)]** .

1. Selecteer ![ Visualisaties ](assets/visualization-icon.svg) en laat vallen een grafiektype aan de sectie Freeform. Op dezelfde manier kunt u veelvoudige grafiektypes aan de sectie van de Vrije vorm toevoegen.

1. Selecteer Ctrl + S en geef een naam op om het project op te slaan.

<!--

## Add AEM Forms and Adobe Analytics integration specific rules to Dispatcher {#forms-specific-rules-to-dispatcher}

Add AEM Forms and Adobe Analytics integration specific rules to filter the data traffic that is sent to the backend.

Perform the following steps to add AEM Forms and Adobe Analytics integration specific rules to Dispatcher for Experience Manager Forms as a Cloud Service:

1. Open your AEM Project and navigate to `\src\conf.dispatcher.d\filters`.
1. Open `filters.any` file for editing and add the following rule at the end of the file:

     ```json
     /00XX { /type "allow" /path "/content/forms/af/*" /method "POST" /selectors '(analyticsconfigparser)' /extension '(jsp|json)' }
     ```

1. Save and close the file.
1. Compile and deploy the project to your [!DNL AEM Forms] as a Cloud Service environment.



## Limitations {#limitations}

* Adobe Analytics can track form metrics only for authenticated users.

-->

## Geavanceerde configuratie voor formulieranalyse

Naast de basisconfiguratie biedt Adobe Analytics geavanceerde configuratieopties die geavanceerde mogelijkheden voor het bijhouden en analyseren van formulieren mogelijk maken. Deze geavanceerde functies helpen organisaties dieper inzicht te krijgen en complexe analysescenario&#39;s te implementeren.

### Aangepaste gebeurtenissen en tracering

**Creërend de Gebeurtenissen van de Vorm van de Douane**

Aangepaste gebeurtenissen maken het bijhouden van bedrijfsspecifieke interacties mogelijk die verder gaan dan standaardformulieranalyses:

- **Gebeurtenissen van het BedrijfsProces**: De vorminteractie van het spoor die zich op specifieke bedrijfswerkschema&#39;s richten
- **Gebeurtenissen van de Betrokkenheid van de Gebruiker**: Maatregel geavanceerd gebruikersgedrag zoals vormvoorproef, het gebruik van de gebiedshulp, of sectieterminrichting
- **Gebeurtenissen van de Integratie**: De vorminteractie van de monitor met externe systemen, APIs, of derdediensten
- **Gebeurtenissen van Prestaties**: De metriek van de douaneprestaties van het spoor zoals de tijden van de vormlading of de tarieven van de gebiedsreactie

**Benadering van de Implementatie**

1. **bepaalt BedrijfsVereisten**: Identificeer specifieke vorminteractie die bedrijfswaarde verstrekken
2. **creeer de Variabelen van de Douane**: Opstelling douanevars en steunen in Adobe Analytics voor zaken-specifieke gegevens
3. **vorm de Redacteur van de Regel**: De regelredacteur van AEM Forms van het gebruik om douanegebeurtenissen teweeg te brengen die op vorminteractie worden gebaseerd
4. **Kaart aan de Gebeurtenissen van Analytics**: Verbind de gebeurtenissen van de douanevorm met de gebeurtenis die van Adobe Analytics volgen
5. **bevestigt Implementatie**: De gebeurtenissen van de douane van de Test om nauwkeurige gegevensinzameling en rapportering te verzekeren

### Geavanceerde rapportinstellingen

**Multidimensionale Configuratie van de Analyse**

- **Cross-Form Analyse**: Vergelijk prestaties over verschillende vormtypes en bedrijfsprocessen
- **Afbeelding van de Reis van de Gebruiker**: De gebruikersinteractie van het spoor over veelvoudige vormen en touchpoints
- **Modellering van de Attributie**: Begrijp hoe de verschillende marketing kanalen tot vormvoltooiing bijdragen
- **Analyse van de Cohort**: Analyseer de verbeteringen van vormprestaties in tijd en gebruikerssegmenten

**Real-Time het Melden van Configuratie**

- **Levende Opstelling van het Dashboard**: Vorm in real time prestaties controle
- **Waakzame Configuratie**: Opstelling geautomatiseerde alarm voor de kwesties of anomalieën van vormprestaties
- **Drempels van Prestaties**: Bepaal aanvaardbare prestatieswaaiers en controletrekkers
- **Belanghebbenden die** melden: Creeer geautomatiseerde rapporten voor verschillende organisatorische rollen en verantwoordelijkheden

### Integratie met andere Adobe-tools

**de Integratie van Adobe Target**

- **Vorm A/B het Testen**: Test verschillende vormvariaties en meet prestatieseffect
- **Personalization**: Lever gepersonaliseerde vormervaringen die op gebruikersgedrag en analysegegevens worden gebaseerd
- **Optimalisering**: De inzichten van de Analytics van het gebruik om de strategieën van de optimalisering van het Doel te informeren
- **Optimalisering van de Omzetting**: Combineer vormanalyses met bredere inspanningen van de omzetoptimalisering

**de Integratie van Adobe Campaign**

- **Lood het Zorgen**: De gegevens van de vormanalyse van het gebruik om e-mail marketing en lood te informeren die campagnes voeden
- **Segmentatie**: Creeer gebruikerssegmenten die op het gedrag van de vormvoltooiing en betrokkenheidspatronen worden gebaseerd
- **Attributie van de Campagne**: Spoor hoe de marketing campagnes vormprestaties en voltooiingstarieven beïnvloeden
- **Levenscyclusmarketing**: Integreer vormanalyses met bredere de marketing van de klantenlevenscyclus strategieën

## Rapporten en inzichten van formulieranalyses

Kennis van de manier waarop u analysegegevens van formulieren kunt interpreteren en bewerken is van cruciaal belang voor een geslaagde optimalisatie. Deze sectie behandelt zeer belangrijke rapporten, dashboardconfiguratie, en actionable inzichten extractie.

### Het dashboard Analytics

**Zeer belangrijke Indicatoren van Prestaties (KPIs) Dashboard**

- **Kanaal van de Omzetting van de Vorm**: visualiseer gebruikersvooruitgang door proces van de vormvoltooiing
- **Analyse van de Omgang**: Identificeer specifieke punten waar de gebruikers vormen onvolledig verlaten
- **Trends van Prestaties**: De veranderingen van de vormprestaties van het spoor in tijd en identificeren patronen
- **Vergelijkende Analyse**: Vergelijk prestaties over verschillende vormen, tijdsperioden, en gebruikerssegmenten

**Operationeel Dashboard van Metriek**

- **Echte-tijd de Activiteit van de Vorm**: De huidige het vormgebruik en voltooiingstarieven van de monitor
- **Controle van het Tarief van de Fout**: De fouten van de bevestiging van het spoor en technische kwesties die vormprestaties beïnvloeden
- **Apparaat en Browser Prestaties**: Analyseer vormprestaties over verschillende technische milieu&#39;s
- **Geografische Prestaties**: Begrijp hoe de vormprestaties door plaats en taal variëren

### Belangrijkste rapporten om te controleren

**Dagelijkse Rapporten van Prestaties**

- **Samenvatting van de Voltooiing van de Vorm**: Dagelijks overzicht van vormvoorlegging, verlaten tarieven, en omzettingsmetriek
- **Analyse van de Fout**: Dagelijkse het volgen van vormfouten, bevestigingskwesties, en technische problemen
- **Prestaties van Source van het Verkeer**: Analyse van hoe de verschillende marketing kanalen vormvoltooiing drijven
- **Mobiele versus de Prestaties van de Desktop**: Vergelijkende analyse van vormprestaties over apparatentypen

**Wekelijks de Analyse van de Trend**

- **Identificatie van de Tendens van Prestaties**: Week-over-week analyse van de verbeteringen of de dalingen van vormprestaties
- **Patronen van het Gedrag van de Gebruiker**: Wekelijkse analyse van de patronen van de gebruikersinteractie en betrokkenheidstendensen
- **Meting van het Effect van de Optimalisering**: Beoordeling van hoe de vormveranderingen prestatiesmetriek beïnvloeden
- **Concurrerende Benchmarking**: Vergelijking van vormprestaties met de industriestandaarden en benchmarks

**Maandelijkse Strategische Rapporten**

- **Analyse van het ROI**: Maandelijkse beoordeling van vormanalytische invloed op bedrijfsresultaten en opbrengst
- **de Inzichten van de Ervaring van de Gebruiker**: Uitgebreide analyse van de verbeteringen van de gebruikerservaring en optimaliseringskansen
- **Prestaties van de Integratie**: Analyse van hoe de integratie van de vormanalyse bredere marketing en bedrijfsprocessen beïnvloedt
- **Strategische Aanbevelingen**: Gegevens-gedreven aanbevelingen voor vormoptimalisering en bedrijfsprocesverbeteringen

### Handelbare uitname van inzichten

**Inzichten van de Optimalisering van Prestaties**

- **gebied-Vlakke Optimalisering**: Identificeer specifieke vormgebieden die verbetering of verwijdering vereisen
- **de Verbetering van de Ervaring van 0} Gebruiker: Ontdek de kwesties van de gebruikerservaring en voer gerichte verbeteringen uit**
- **Optimalisering van het Tarief van de Omzetting**: De analysegegevens van het gebruik om veranderingen uit te voeren die de tarieven van de vormvoltooiing verbeteren
- **Technische Optimalisering van Prestaties**: De technische kwesties van het adres die vormlading en voorstellingsprestaties beïnvloeden

**de Inzichten van het BedrijfsProces**

- **Analyse van de Kwaliteit van de Lood**: Begrijp hoe het gedrag van de vormvoltooiing met loodkwaliteit en omzetting correleert
- **de Attributie van de Marketing**: Identificeer welke marketing kanalen en campagnes de van de hoogste kwaliteit vormvoorlegging drijven
- **Optimalisering van de Reis van de Klant**: Gebruik vormanalyses om bredere processen van de klantenverwerving en van het behoud te verbeteren
- **Toewijzing van het Middel**: Maak gegeven-gedreven besluiten over waar te om de middelen van de vormoptimalisering te investeren

## Problemen met formulieranalyses oplossen

Zelfs met zorgvuldige implementatie, kunnen de configuraties van de vormanalyse kwesties ontmoeten die gegevensinzameling en rapporteringsnauwkeurigheid beïnvloeden. Deze sectie verstrekt systematische het oplossen van problemenbegeleiding voor gemeenschappelijke problemen.

### Algemene instellingsproblemen

**Kwesties van de Inzameling van Gegevens**

- **Ontbrekende Gegevens van de Vorm**: Verifieer de configuratie van de Lancering van Adobe en verzeker juiste markeringsplaatsing
- **Onvolledige Gebeurtenis het Volgen**: De configuratie van de de regelregel van de controle en zorgt ervoor dat alle vormgebeurtenissen behoorlijk in kaart worden gebracht
- **Latentie van Gegevens**: Begrijp normale vertragingen van de gegevensverwerking en identificeer abnormale rapporteringsvertragingen
- **het Volgen van 0} dwars-Domein**: Los kwesties met vormanalyses over verschillende domeinen of subdomeinen op

>[!TIP]
>
>Voor extra het oplossen van problemenbegeleiding, zie onze [ het oplossen van problemeninzameling van AEM Forms ](/help/forms/troubleshooting-installation-and-configuration.md) en [ het oplossen van problemen van de vormverwezenlijking ](/help/forms/form-creation-failing.md) gidsen.

**De Problemen van de Configuratie**

- **de Afbeelding van de Reeks van het Rapport**: Zorg ervoor de vormen gegevens naar de correcte het rapportreeks van Adobe Analytics verzenden
- **Variabele Configuratie**: Verifieer dat de douanevariabelen (eVars, steunen) behoorlijk worden gevormd en in kaart gebracht
- **Logische Kwesties van de Regel**: Zuiver de regels van de Lancering van Adobe die niet correct kunnen teweegbrengen
- **Problemen van de Toestemming**: Los toegangskwesties op die juiste configuratie of gegevens het bekijken verhinderen

### Resolutie van gegevensdiscrepantie

**Analytics vs. de Verschillen van het Systeem van de Vorm**

- **Verschillen van de Telling van de Verzending**: Vergelijk verschillen tussen Adobe Analytics en AEM Forms de indieningstellingen
- **het Gedrag dat van de Gebruiker** volgt: De discrepanties van het adres in gebruikersinteractie het volgen tussen systemen
- **de Uitgave van de Streek van de Tijd en van de Datum**: Los rapporteringsdiscrepanties op die door de verschillen van de tijdzoneconfiguratie worden veroorzaakt
- **Steekproef van Gegevens**: Begrijp wanneer en hoe de gegevensbemonstering van Adobe Analytics de nauwkeurigheid van vormanalyses beïnvloedt

**de Consistentie van Gegevens van het dwars-Platform**

- **Mobiele vs. Desktop die** volgen: Verzeker verenigbare gegevensinzameling over verschillende apparatentypes en platforms
- **Browser Verenigbaarheid**: De volgende kwesties van het adres specifiek voor bepaalde browsers of browser versies
- **Integratie van de Derde**: Los de kwesties van de gegevensconsistentie met externe systemen en integratie op
- **Real-Time vs. Historische Gegevens**: Begrijp en richt verschillen tussen in real time en verwerkte historische gegevens

### Optimalisatie van prestaties

**Effect van Prestaties van Analytics**

- **Prestaties van de Lading van de Pagina**: Minimaliseer het effect van analyses die op de tijden van de vormlading volgen
- **Efficiëntie van de Inzameling van Gegevens**: Optimaliseer gegevensinzameling om bandbreedtegebruik te verminderen en gebruikerservaring te verbeteren
- **Real-Time Verwerking**: Vorm analytische verwerking in real time voor tijd-gevoelige behoeften van de vormanalyse
- **Overwegingen van de Schaalbaarheid**: Zorg de analytische configuratie kan hoog-volume vormgebruik zonder prestatiesdegradatie behandelen

**Prestaties van de Integratie van het Systeem**

- **Prestaties API**: Optimaliseer integratie tussen AEM Forms en Adobe Analytics voor betere prestaties
- **Efficiëntie van de Verwerking van Gegevens**: Verbeter de werkschema&#39;s van de gegevensverwerking om latentie te verminderen en rapporteringschronologie te verbeteren
- **Gebruik van het Middel**: Monitor en optimaliseer systeemmiddelgebruik voor de inzameling en verwerking van analysegegevens
- **Optimalisering van het Netwerk**: Vorm netwerkmontages om gegevenstransmissie tussen systemen te optimaliseren

## Aanbevolen werkwijzen voor formulieranalyse

Voor het met succes implementeren van formulieranalyses moeten de best practices worden gevolgd die nauwkeurige gegevensverzameling, zinvolle inzichten en duurzame optimalisatieprocessen garanderen.

>[!TIP]
>
>Alvorens analyses uit te voeren, zorg ervoor uw vormen behoorlijk worden gevormd gebruikend [ beste praktijken van AEM Forms ](/help/forms/introduction-forms-authoring.md) en aangewezen [ voorlegt acties ](/help/forms/configuring-submit-actions.md).

### Implementatierichtlijnen

**Strategische Planning**

- **Bedrijfs Objectieve Groepering**: Verzeker de implementatie van de vormanalyse richt op specifieke bedrijfsdoelstellingen en KPIs
- **Betrokkenheid van Stakeholder**: Neem zeer belangrijke belanghebbenden in planning op om ervoor te zorgen dat de analyses aan organisatorische behoeften voldoen
- **Geleidelijke Implementatie**: Voer vormanalyses in fasen uit om ingewikkeldheid te beheren en succesvolle plaatsing te verzekeren
- **de Definitie van Metriek van het Succes**: Bepaal duidelijk welk succes als kijkt en hoe het zal worden gemeten

**Technische Implementatie**

- **Documentatie van de Configuratie**: Handhaaf uitvoerige documentatie van analytische configuratie voor toekomstige verwijzing en het oplossen van problemen
- **het Testen Protocollen**: Voer grondig testende procedures uit om nauwkeurige gegevensinzameling vóór productieleiding te verzekeren
- **Controle van de Versie**: De versiecontrole van het gebruik voor de veranderingen van de analyseconfiguratie om terugdraaiing toe te laten als de kwesties zich voordoen
- **Controle van Prestaties**: Ononderbroken de prestaties van de analytische implementatie en effect op vormfunctionaliteit controleren

### Overwegingen met betrekking tot privacy

**de Naleving van de Privacy van Gegevens**

- **Naleving GDPR**: zorg ervoor de implementatie van vormanalyse voldoet aan de Europese regelgeving inzake gegevensbescherming
- **naleving CCPA**: Voer de Vereisten van de Privacy van de consument van Californië voor de inzameling van vormgegevens en gebruikersrechten uit
- **industrie-Specifieke Verordeningen**: De gezondheidszorg van het adres (HIPAA), financiële (PCI DSS), en andere industrie-specifieke privacyvereisten
- **Beheer van de Toestemming van de Gebruiker**: Voer juiste toestemmingsmechanismen voor de inzameling en verwerking van analysegegevens uit

**Veiligheid van Gegevens**

- **de Encryptie van Gegevens**: Zorg ervoor alle gegevens van de vormanalyse in doorvoer en in rust worden gecodeerd
- **Controles van de Toegang**: Voer aangewezen toegangscontroles voor analysegegevens en het melden uit
- **Behoud van Gegevens**: Vestig en handhaaf aangewezen beleid van het gegevensbehoud voor de informatie van de vormanalyse
- **Trails van de Controle**: Handhaaf controletrails voor de toegang van analysegegevens en configuratieveranderingen

### Optimalisatiestrategieën

**Ononderbroken het Proces van de Verbetering**

- **Regelmatige Controle van Prestaties**: Vestig regelmatige overzichtscycli om de prestaties van de vormanalyse te beoordelen en optimalisatiemogelijkheden te identificeren
- **A/B het Testen Integratie**: De gegevens van de vormanalyse van het gebruik om A/B testende strategieën te informeren en optimaliseringseffect te meten
- **Integratie van de Terugkoppeling van de Gebruiker**: Combineer kwantitatieve analysegegevens met kwalitatieve gebruiker terugkoppelt voor uitvoerige optimaliseringsinzichten
- **dwars-Functionele Collaboration**: Foster samenwerking tussen marketing, UX, ontwikkeling, en analytische teams voor holistische optimalisering

**Geavanceerde Gebruik van Analytics**

- **Predictive Analytics**: De historische gegevens van de vormanalyse van het gebruik om gebruikersgedrag te voorspellen en vormervaringen proactively te optimaliseren
- **het Leren van de Machine Integratie**: Het leren van de machine van de hefboomwerking mogelijkheden om patronen en optimalisatiemogelijkheden in de gegevens van de vormanalyse te identificeren
- **Real-Time Optimalisering**: Voer vorm in real time optimalisering uit die op huidige analyseprestaties en gebruikersgedrag wordt gebaseerd
- **Integratie over het Kanaal**: Integreer vormanalyses met bredere klantenreisanalyses voor uitvoerige gebruikerservaring optimalisering

## Veelgestelde vragen (FAQ)

In deze uitgebreide sectie Veelgestelde vragen worden veelgestelde vragen over de implementatie van formulieranalyses, probleemoplossing en optimalisatie besproken, zodat gebruikers op alle ervaringsniveaus kunnen werken.

### Aan de slag-vragen

**Q: Wat is het verschil tussen vormanalyses en algemene websiteanalyses?**

A: De formulieranalyse is specifiek gericht op gebruikersinteracties binnen formulieren, zodat u gedetailleerde inzichten krijgt in het gedrag op veldniveau, de voltooiingspatronen en de afbrekingspunten. Terwijl de algemene websiteanalyse paginaweergaven en algemene gebruikersreizen bijhoudt, biedt formulieranalyse gedetailleerde gegevens over formulierspecifieke gebruikerservaring, validatiefouten, veldvoltooiingstijd en de analyse van conversietrechter binnen formulieren zelf.

**Q: Heb ik technische deskundigheid nodig om vormanalyses met Adobe Analytics uit te voeren?**

A: De basisimplementatie kan met gematigde technische kennis worden verwezenlijkt, maar de geavanceerde configuraties profiteren van technische deskundigheid. Adobe biedt automatische instellingsopties via Experience Cloud Setup Automation voor eenvoudigere implementaties. Voor complexe bedrijfsimplementaties met aangepaste gebeurtenissen en geavanceerde rapportering wordt samenwerking met ontwikkelaars of Adobe-consultants aanbevolen.

**Q: Hoe lang duurt het om zinvolle gegevens van vormanalyses te zien?**

A: De initiële gegevens verschijnen binnen 24-48 uur na implementatie, maar betekenisvolle inzichten vereisen doorgaans 2-4 weken na het verzamelen van gegevens om patronen en trends te identificeren. Voor statistische significantie bij tests en optimalisatiebeslissingen voor A/B, kunt u 4 tot 6 weken gegevens verzamelen, afhankelijk van het volume van het formulierverkeer.

**Q: Wat is het minimumverkeersvolume nodig voor efficiënte vormanalyses?**

A: Formulieranalyses kunnen op elk verkeersniveau waarde opleveren, maar statistische significantie voor optimalisatiebeslissingen vereist doorgaans ten minste 100 formulierverzendingen per week. Voor A/B-tests en geavanceerde analyse bieden 500+ wekelijkse inzendingen betrouwbaardere inzichten. Lagere-verkeersformulieren kunnen nog steeds profiteren van kwalitatieve inzichten in het gedrag van gebruikers en de identificatie van fouten.

### Implementatie- en configuratievragen

**Q: Kan ik vormen over veelvoudige domeinen of subdomeinen volgen?**

A: Ja, Adobe Analytics biedt ondersteuning voor het bijhouden van domeinoverschrijdende formulieren via een correcte configuratie van de code voor het bijhouden van Adobe Analytics en de implementatie van Adobe Launch. Zorg voor consistente configuratie van de rapportsuite en installatie voor het bijhouden van meerdere domeinen om de gegevensintegriteit op verschillende domeinen te handhaven.

**Q: Hoe kan ik vormanalyses voor multi-stap of tovenaar-stijl vormen behandelen?**

A: Formulieren die uit meerdere stappen bestaan, moeten zijn geconfigureerd om de voortgang van elke stap te kunnen volgen. Voer douanegebeurtenissen voor stapvoltooiing uit, vorm kanaalanalyse om drop-off punten tussen stappen te visualiseren, en gebruik douanevariabelen om gebruikerspaden door de vormtovenaar te volgen. Adobe Analytics biedt specifieke richtlijnen voor het bijhouden van formulieren met meerdere pagina&#39;s.

**Q: Wat gebeurt aan analysegegevens als een gebruiker een vorm off-line voltooit of met JavaScript gehandicapt?**

A: Adobe Analytics vereist JavaScript voor gegevensverzameling, dus gebruikers met JavaScript uitgeschakeld worden niet bijgehouden. Voor offlinescenario&#39;s, voer terugval het volgen mechanismen of server-kant analyseinzameling uit. Overweeg het effect op gegevensvolledigheid en voer alternatieve het volgen methodes voor kritieke bedrijfsprocessen uit.

**Q: Hoe volg ik vormprestaties over verschillende apparaten en browsers?**

A: Adobe Analytics legt automatisch apparaat- en browserinformatie vast met formulieranalysegegevens. Configureer aangepaste rapporten om de formulierprestaties te analyseren op apparaattype, browser, besturingssysteem en schermresolutie. Gebruik deze gegevens om apparaatspecifieke optimalisatiemogelijkheden te identificeren en consistente formulierervaringen op verschillende platforms te garanderen.

### Vragen over gegevensanalyse en -optimalisatie

**Q: Welk tarief van de vormbeëindiging zou ik problematisch moeten achten?**

A: Het percentage verlaten van formulieren varieert aanzienlijk per bedrijfstak en vorm complexiteit. Eenvoudige contactformulieren hebben doorgaans een lager percentage voor het verlaten van het bestand, terwijl complexe formulieren met meerdere stappen en processen voor het afrekenen van e-commerce vaak hogere tarieven hebben. Ongebruikelijk hoge wachttijden voor uw specifieke vormtype en industrie wijzen op optimalisatiemogelijkheden.

**Q: Hoe identificeer ik welke vormgebieden de meeste verlaten veroorzaken?**

A: Gebruik Adobe Analytics-tracking op veldniveau om de voltooiingssnelheden voor elk formulierveld te analyseren. Zoek significante drop-offs op specifieke gebieden, langer-dan gemiddelde tijd besteed aan specifieke gebieden, en hoge foutenpercentages voor bepaalde gebiedstypes. De afbeelding van de warmte en opnamen van de gebruikerszitting kunnen extra context voor gebied-vlakke optimalisering verstrekken.

**Q: Moet ik voor snelheid of grondigheid van de vormvoltooiing optimaliseren?**

A: Het evenwicht hangt van uw bedrijfsdoelstellingen af. Voor het genereren van lood optimaliseert u deze voor voltooiing, terwijl de loodkwaliteit behouden blijft. Voor gedetailleerde gegevensverzameling (enquêtes, toepassingen), richt zich op de verbeteringen van de gebruikerservaring die wrijving verminderen zonder de gegevenskwaliteit te offeren. Gebruik een A/B-test om de optimale balans voor uw specifieke gebruikscase te vinden.

**Q: Hoe meet ik ROI van de implementatie van vormanalyse?**

A: Bereken ROI door verbeteringen in omrekeningskoersen, loodkwaliteit, en operationele efficiency te meten. De metriek van het spoor zoals: verhoogde van de vormvoltooiing, verminderde steunkaartjes met betrekking tot vormkwesties, verbeterde lood-aan-klant omzettingspercentages, en dalende klant verwervingskosten. Kwantificeer deze verbeteringen tegen de kosten van de uitvoering van de analyse en de lopende optimaliseringsinspanningen.

### Technische en probleemoplossingsvragen

**Q: Waarom zie ik discrepanties tussen Adobe Analytics en mijn tellingen van de vormsysteemindiening?**

A: Veelvoorkomende oorzaken zijn onder meer: JavaScript-fouten die het bijhouden van analyses voorkomen, gebruikers die formulieren meerdere keren indienen, zowel het verkeer dat het ene systeem beïnvloedt als het andere, tijdzoneverschillen in rapportage en vertragingen bij gegevensverwerking. Implementeer validatieregels, filtert ze, en zorg voor consistente tijdzoneinstellingen tussen systemen.

**Q: Hoe behandelt ik vormanalyses voor enig-paginatoepassingen (SPAs)?**

A: SPAs vereist speciale configuratie voor vormanalyse omdat de traditionele gebeurtenissen van de paginading niet voorkomen. Aangepaste gebeurtenistracering implementeren voor formulierinteracties, Adobe Analytics SPA-trackingmogelijkheden gebruiken, virtuele paginaweergaven configureren voor formulierstappen en zorgen voor correcte gebeurtenisafhandeling voor dynamische formulierelementen.

**Q: Wat zou ik moeten doen als de vormanalyse de prestaties van de paginading beïnvloedt?**

A: Optimaliseer analytische implementatie door: het asynchroon laden van analysescripts, het implementeren van lui laden voor niet-kritieke tracking, het verminderen van het aantal aangepaste variabelen en gebeurtenissen, het gebruik van efficiënte regelconfiguraties in Adobe Launch en het controleren van Core Web Vital om ervoor te zorgen dat analyses geen negatieve invloed hebben op de gebruikerservaring.

**Q: Hoe verzeker ik de naleving van de privacyverordeningen van de vormanalyse?**

A: De naleving van de privacywetgeving implementeren door: de juiste toestemming van de gebruiker verkrijgen voor het bijhouden van analyses, anonimiseren of pseudonimiseren van persoonsgegevens, het voeren van beleid inzake gegevensbewaring, het bieden van opt-outmechanismen, het waarborgen van de naleving van de GDPR/CCPA-regels bij het verzamelen en verwerken van gegevens, en het werken met juridische teams om naleving van de regelgeving te waarborgen.

### Geavanceerde implementatievragen

**Q: Kan ik vormanalyses met andere oplossingen van Adobe Experience Cloud integreren?**

A: Ja, Adobe Analytics kan naadloos worden geïntegreerd met andere Experience Cloud-oplossingen. Verbind met Adobe Target voor het testen en personaliseren van vorm A/B, integreer met Adobe Campaign voor het leiden die op vormgedrag gebaseerd zijn, gebruik Adobe Audience Manager voor geavanceerde segmentatie, en hefboomwerking Adobe Experience Platform voor uitvoerige klantenreisanalyse.

**Q: Hoe opstellings ik voorspellende analyses voor formatiebeëindiging?**

A: Voorspelende analyses uitvoeren door: uitgebreide gegevens over gebruikersgedrag verzamelen, Adobe Analytics-mogelijkheden voor machinaal leren gebruiken, real-time modellen voor scoring implementeren, geautomatiseerde interventies instellen voor scenario&#39;s met hoge risico&#39;s voor het verlaten van het bedrijf, en voortdurend modellen verfijnen op basis van prestatiegegevens.

**Q: Wat is de beste benadering voor het volgen van vormanalyses in een mobiele app?**

A: Voor de analyse van mobiele apps is Adobe Analytics Mobile SDK-implementatie vereist. Configureer specifieke gebeurtenissen en variabelen voor mobiele apparaten, implementeer offlinegegevensverzameling en -synchronisatie, controleer de specifieke interacties voor mobiele apparaten (aanraakgebeurtenissen, apparaatoriëntatie) en zorg voor een juiste toewijzing voor alle toepassingssessies en webinteracties.

**Q: Hoe creeer ik douanedashboards voor verschillende belanghebbenden?**

A: Maak rolspecifieke dashboards door: het identificeren van zeer belangrijke metriek voor elke groep van belanghebbenden (managers, marketers, ontwikkelaars), het gebruiken van Adobe Analytics Workspace om douanvisualisaties te bouwen, het uitvoeren van geautomatiseerde rapporteringsprogramma&#39;s, het creëren van boor-down mogelijkheden voor gedetailleerde analyse, en het verstrekken van opleiding op dashboardinterpretatie en gebruik.

### Problemen in Snel repareren oplossen

**Gemeenschappelijke Kwesties en Oplossingen:**

| Probleem | Snel repareren | Gedetailleerde oplossing |
|-------|-----------|-------------------|
| Geen gegevens weergegeven | Implementatie van Adobe starten controleren | Implementatie van tags en regelconfiguratie controleren |
| Onjuiste aantallen ingediende aanvragen | Gebeurtenisafhandeling valideren | Toewijzing van regellogica en gegevenselementen controleren |
| Ontbrekende gegevens op veldniveau | Veld bijhouden configureren | Aangepaste variabelen instellen voor veldinteracties |
| Problemen met meerdere domeinen | Configuratie bijhouden bijwerken | De juiste instelling voor bijhouden tussen domeinen implementeren |
| Problemen met het bijhouden van mobiele apparatuur | Mobiele implementatie controleren | Responsief ontwerp en mobiele specifieke gebeurtenissen controleren |
| Prestatiegeld | Belastingsstrategie optimaliseren | asynchrone en efficiënte regels implementeren |

>[!MORELIKETHIS]
>
>*[ laat Adobe Analytics aan een Aangepaste Vorm ](/help/forms/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.md) toe
