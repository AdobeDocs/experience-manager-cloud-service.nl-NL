---
title: Forms Experience Builder - aanbevolen procedures
description: Uitgebreide best practices voor het maken van effectieve formulieren met Forms Experience Builder, inclusief ontwerp, gebruikerservaring, prestaties en consistentie van merken.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: 9996bc602ae6169dd1aade622d5dbc5b1addeb54
workflow-type: tm+mt
source-wordcount: '2072'
ht-degree: 0%

---


# Forms Experience Builder - aanbevolen procedures

>[!NOTE]
>
> De Forms Experience Builder is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie die aan Verandering** wordt onderworpen: Deze gids van beste praktijken wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. Beste praktijken, aanbevelingen, en voorbeelden kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

Deze uitgebreide handleiding bevat beproefde best practices voor het maken van effectieve, gebruiksvriendelijke formulieren met de Forms Experience Builder. Deze praktijken worden afgeleid uit succesvolle implementaties en gebruikersterugkoppel over diverse industrieën en gebruiksgevallen.

## Aanbevolen werkwijzen voor formulierontwerp

### Eenvoudig houden

**Begin met Essentiële Gebieden**

- Begin met slechts de meest noodzakelijke informatie om gebruikersoverweldigende
- Voeg geleidelijk complexiteit toe op basis van gebruikersbehoeften en zakelijke vereisten
- Vermijd het vragen naar informatie die u niet echt nodig hebt of gebruikt
- Houd rekening met de tijd en cognitieve belasting van de gebruiker bij het ontwerpen van formulieren

**Gebruik Duidelijke, Omschrijvende Etiketten**

- Velddoeleinden direct zichtbaar maken met beschrijvende labels
- Vermijd technische jargon of interne terminologie die gebruikers niet begrijpen
- Gebruik consistente labelconventies in alle formulieren
- Context opgeven wanneer veldvereisten mogelijk niet voor de hand liggen

**verstrekken Nuttige Begeleiding**

- Inclusief Help-tekst voor complexe velden met voorbeelden en opmaakvereisten
- Plaatsaanduidingstekst gebruiken om verwachte invoerindelingen weer te geven
- Geef duidelijke instructies voor het uploaden van bestanden, waaronder geaccepteerde indelingen en grootten
- Gebruikers begeleiden door processen die uit meerdere stappen bestaan, met voortgangsindicatoren

**Test grondig**

- Valideer alle gebruikerspaden en -scenario&#39;s vóór de implementatie
- Formulieren testen met echte gebruikers van uw doelgroep
- Controleren of alle voorwaardelijke logica werkt zoals verwacht
- Zorg ervoor dat foutafhandeling duidelijke, activeerbare feedback biedt

### Progressieve openbaarmaking

**toon Relevante Gebieden die op Context** worden gebaseerd

- Aanvullende velden alleen weergeven als deze relevant worden voor gebruikersselecties
- Voorwaardelijke logica gebruiken om cognitieve belasting en formulierlengte te beperken
- Gerelateerde velden groeperen in logische secties
- Geavanceerde opties verbergen totdat gebruikers aangeven dat ze deze nodig hebben

**Implementatie van het Voorbeeld:**

     creeer een regel die @spouseInformation paneel toont slechts wanneer @maritalStatus &quot;Gehuwd&quot;evenaart 

**Duidelijke Navigatie en Voortgang**

- Gebruikers helpen te begrijpen waar ze zich in formulieren met meerdere stappen bevinden
- Zorg voor duidelijke navigatie tussen formuliersecties
- Voortgangsindicatoren voor langere formulieren weergeven
- Gebruikers toestaan om de voortgang op te slaan en later terug te keren

## Aanbevolen werkwijzen voor gebruikerservaring

### Mobiel eerste ontwerp

**Responsieve Optimalisering van de Lay-out**

- Formulieren ontwerpen met mobiele gebruikers als eerste overweging
- Lay-outs met één kolom gebruiken voor mobiele apparaten
- Zorg ervoor dat de grootte van de aanraakdoelen correct is (minimaal 44 px)
- Formulieren testen op verschillende formaten en standen van apparaten

**aanraak-Vriendelijke Interacties**

- Grotere knoppen en invoervelden implementeren voor aanraakinterfaces
- Gebruik de juiste invoertypen om correcte mobiele toetsenborden te activeren
- Vermijd aanraakgevoelige interactie die niet werkt op aanraakapparaten
- Zorg voor duidelijke visuele feedback voor gebruikersinteracties

### Toegankelijkheidscompatibiliteit

**WCAG 2.1 Richtlijnen**

- Volg de richtlijnen voor webinhoudtoegankelijkheid voor een inclusief ontwerp
- Ervoor zorgen dat de kleurcontrastverhoudingen juist zijn (minimaal 4,5 :1 voor normale tekst)
- Alternatieve tekst bieden voor alle afbeeldingen en pictogrammen
- De juiste kopstructuur en semantische HTML implementeren

**de Navigatie van 0&rbrace; Keyboard**

- Zorg ervoor dat alle formulierelementen toegankelijk zijn via toetsenbordnavigatie
- Duidelijke focusindicatoren bieden voor alle interactieve elementen
- Logische tabvolgorde implementeren door formuliervelden
- Navigatiekoppelingen voor complexe formulieren overslaan

**de Steun van Reader van het Scherm**

- Gebruik juiste ARIA-labels en -beschrijvingen voor formuliervelden
- Geef duidelijke foutberichten op die aan schermlezers worden aangekondigd
- Zorgen dat wijzigingen in dynamische inhoud correct worden aangekondigd
- Formulieren testen met schermlezersoftware

### Optimalisatie van prestaties

**het laden Snelheid**

- De laadtijden van formulieren optimaliseren door de aanvankelijke bundelgrootte te minimaliseren
- Lazy laden implementeren voor niet-kritieke formuliersecties
- Afbeeldingen en middelen optimaliseren voor weergave op het web
- Geschikte cachingstrategieën voor statische bronnen inschakelen

**Runtime Prestaties**

- Gebruik de juiste validatietiming om de gebruikerservaring en -prestaties op elkaar af te stemmen
- Implementeer debouncing voor realtime validatie om serververzoeken te verminderen
- Veelgebruikte gegevens en validatieresultaten in cache plaatsen
- Voorwaardelijke logische uitvoering voor complexe formulieren optimaliseren

**auto-sparen en de Bescherming van Gegevens**

- Automatisch opslaan van formuliervoortgang implementeren om gegevensverlies te voorkomen
- Offline mogelijkheden bieden waar mogelijk voor het invullen van formulieren
- Opnieuw proberen logica opnemen voor mislukte verzendingen
- Opties voor gegevensexport aanbieden als back-up voor gebruikers

## Aanbevolen werkwijzen voor consistentie merk

### Merk Assets vooraf voorbereiden

**creeer de Malplaatjes van het Merk**

- Standaardformuliersjablonen ontwikkelen met de visuele identiteit van uw organisatie
- Inclusief consistente kleurenschema&#39;s, typografie en layoutpatronen
- Herbruikbare componenten voorbereiden die voldoen aan de richtlijnen van uw merk
- Documentstijlstandaarden voor consistente implementatie in verschillende teams

**bepalen de Richtlijnen van de Stijl**

- Consistente veldstijlen, knopontwerpen en spatiëringsstandaarden vaststellen
- Een stijlhulplijn maken die kleurcodes, lettertypespecificaties en indelingsregels bevat
- Richtlijnen voor interactie en animatie definiëren
- merkspecifieke foutberichten en Help-tekst voorbereiden

**bouwt de Bibliotheek van de Component**

- Herbruikbare formuliercomponenten maken die overeenkomen met uw merkidentiteit
- Consistente navigatiepatronen en gebruikersinterface-elementen ontwikkelen
- Pictogrammen, logo&#39;s en visuele elementen van brandmerken voorbereiden voor formulierintegratie
- Sjablonen maken voor algemene formuliertypen (contact, registratie, feedback)

### Handelsuitvoeringsstrategieën

**Prompts van de Stijl voor Consistentie**

Geef uw vragen ook merkspecifieke instructies:

     creeer een professionele contactvorm gebruikend:
     - Collectief blauw (#003366) voor primaire knopen en kopballen 
     - Open Sans doopvontfamilie voor alle tekstelementen 
     - 16px minimumdoopvontgrootte voor toegankelijkheidsnaleving 
     - Consistent 24px die tussen vormsecties 
     - het embleem van het Bedrijf in juiste merkpositionering 

**Beheer van de Bibliotheek van het Malplaatje**

- Een verzameling gebrandmerkte formuliersjablonen bijhouden voor veelvoorkomende gebruiksgevallen
- Versiebeheer uw merksjablonen om consistentie te garanderen
- Zorg voor duidelijke documentatie voor sjabloongebruik en aanpassing
- Regelmatige evaluatie en actualisering van merkactiva om de huidige standaarden te handhaven

>[!NOTE]
>
>**Componenten van de Douane**: Coördineer met uw ontwikkelingsteam over het gebruiken van organisatie-specifieke componenten en hun verenigbaarheid met de Bouwer van de Ervaring van Forms alvorens de elementen van het douanemerk uit te voeren.

## Aanbevolen werkwijzen voor inhoud en communicatie

### Aanpak van het maken van formulieren

**Twee Primaire Methoden**

Kies de meest geschikte methode voor het maken van uw behoeften:

1. **creeer van Scratch**: Best voor nieuwe vormen met specifieke vereisten
2. **de Invoer en zet** om: Ideaal voor het moderniseren van bestaande vormen en documenten

**Aantrekken van de Natuurlijke Taal**

- Wees specifiek en gedetailleerd in uw formulierbeschrijvingen
- Gebruik duidelijke, op het bedrijf gerichte taal eerder dan technische termen
- Context weergeven over het doel en het doelpubliek van het formulier
- Vereisten voor validatie en bedrijfsregels opnemen in eerste berichten

### Incrementele ontwikkelingsstrategie

**Eenvoudig Begin, bouwt Complexiteit**

- Beginnen met de basisformulierstructuur en essentiële velden
- Voeg validatieregels en bedrijfslogica incrementeel toe
- Test elke toevoeging voordat u verdergaat met de volgende verbetering
- Feedback van gebruikers verzamelen in elke ontwikkelingsfase

**Incrementele benadering van het Voorbeeld:**

     Stap 1: &quot;Creeer een basiscontactvorm met naam, e-mail, en berichtgebieden&quot;
     Stap 2: &quot;Maak @name en @email verplichte gebieden met aangewezen bevestiging&quot;
     Stap 3: &quot;voeg placeholder tekst en hulptekst voor gebruikersbegeleiding toe&quot;
     Stap 4: &quot;voeg voorwaardelijke logica toe die op vraagtype wordt gebaseerd&quot;

### Aanbevolen werkwijzen voor veldverwijzing

**Consistente noemende Conventies**

- Gebruik duidelijke, beschrijvende veldnamen die overeenkomen met hun doel
- Regelmatige naamgevingspatronen in verschillende formulieren behouden
- CamelCase of slang_case consistent gebruiken in alle formulieren
- Naamconventies voor documentvelden voor teamconsistentie

**Effectieve Verwijzingen van het Gebied**

- `@fieldName` syntaxis gebruiken bij het wijzigen van bestaande velden
- Geef aan naar welke velden u verwijst in complexe formulieren
- Groepeer gerelateerde veldwijzigingen in één aanvraag
- Veldnamen verifiëren voordat ze in voorwaardelijke logica worden gebruikt

## Aanbevolen werkwijzen voor integratie en verzending

### Meerkanaalsstrategie voor verzending

**Primaire en Secundaire Acties**

- Vorm primaire voorleggingseindpunten voor kernbedrijfsprocessen
- Secundaire acties instellen voor meldingen, bevestigingen en back-ups van gegevens
- Foutafhandeling implementeren en logica voor mislukte verzendingen opnieuw proberen
- Geef gebruikersfeedback voor alle verzendstatussen (geslaagd, mislukt, verwerkt)

**Planning van de Integratie**

- Begin met basisconfiguratie voor verzending en voeg incrementele integratie toe
- Test elke integratie afzonderlijk voordat u meerdere eindpunten combineert
- DocumentAPI-vereisten en verificatiemethoden
- Plan voor gegevenstransformatie en kaartvereisten

### Foutafhandeling en herstel

**gebruiker-Vriendelijke de Berichten van de Fout**

- Duidelijke, activeerbare foutmeldingen geven die gebruikers helpen problemen op te lossen
- Vermijd technische foutcodes of systeemberichten in gebruikersgerichte inhoud
- Alternatieve acties aanbieden wanneer primaire verzending mislukt
- Neem contactgegevens op voor gebruikers die extra hulp nodig hebben

**de Bescherming en Terugwinning van Gegevens**

- Lokale gegevensopslag implementeren voor formulierherstel na fouten
- Geef gebruikers opties om hun formuliergegevens als back-up te downloaden
- Bewaking en waarschuwing instellen voor mislukte verzendingen
- Herstelprocedures plannen voor systeemuitval of onderhoud

## Best practices voor prestaties en analyse

### Controle en optimalisatie

**Zeer belangrijke Metriek van Prestaties**

- Voltooiingssnelheden voor formulieren bijhouden en punten voor verlaten formulieren
- De laadtijden van de monitor en de patronen van de gebruikersinteractie
- Efficiëntie en foutenpercentages van de validatie en
- Feedback en tevredenheidsscores van gebruikers analyseren

**Ononderbroken Verbetering**

- Regelmatige evaluatie van formulieranalyses om optimalisatiemogelijkheden te identificeren
- A/B testen van verschillende formulierontwerpen en gebruikersstromen
- Feedbackverzameling en -analyse van gebruikers voor iteratieve verbeteringen
- Prestatiebenchmarking ten opzichte van industriestandaarden

### Gegevenskwaliteit en validatie

**Slimme Strategieën van de Bevestiging**

- Real-time validatie implementeren voor directe feedback van gebruikers
- Gebruik progressieve validatie om gebruikers door complexe vereisten te leiden
- Geef duidelijke validatieberichten op waarin wordt uitgelegd hoe u fouten kunt corrigeren
- De strengheid van de validatie van het evenwicht met gebruikerservaringsoverwegingen

**Integriteit van Gegevens**

- Veldoverschrijdende validatie implementeren voor gegevensconsistentie
- Gebruik de juiste invoertypen en -beperkingen om ongeldige gegevens te voorkomen
- Voorbeelden van gegevensformaten en richtlijnen voor complexe velden opgeven
- Regelmatige controle van de ingediende gegevenskwaliteit en de doeltreffendheid van de validatie

## Aanbevolen werkwijzen voor beveiliging en naleving

### Gegevensbeveiliging

**Privacy door Ontwerp**

- Verzamel slechts de minimumgegevens noodzakelijk voor uw bedrijfsdoel
- Pas het juiste beleid voor het bewaren en verwijderen van gegevens toe
- Duidelijke privacymededelingen en toestemmingsmechanismen verstrekken
- Ervoor zorgen dat de desbetreffende gegevensbeschermingsvoorschriften (GDPR, CCPA, enz.) worden nageleefd

**Implementatie van de Veiligheid**

- HTTPS-versleuteling gebruiken voor alle verzonden formulieren en gegevensoverdracht
- Correcte invoervalidering en ontsmetting implementeren
- Beveiligde bestandsupload instellen met de juiste beperkingen en virusscans
- Regelmatige beveiligingscontroles en kwetsbaarheidsbeoordelingen

### Overwegingen bij naleving

**Regelgevende Vereisten**

- Inzicht in en implementatie van industriespecifieke nalevingsvereisten
- Naleving van documenten voor auditdoeleinden
- Regelmatige herziening van wijzigingen in de regelgeving en de gevolgen ervan voor formulieren
- Opleiding van het personeel inzake nalevingsvereisten en implementatie

**de Naleving van de Toegankelijkheid**

- Volg WCAG 2.1 AA richtlijnen voor toegankelijkheid
- Regelmatige toegankelijkheidstests met ondersteunende hulpmiddelen
- Testen door gebruikers van personen met een handicap
- Documentatie van toegankelijkheidskenmerken en maatregelen om aan de eisen te voldoen

## Beste praktijken van Collaboration van het team

### Documentatie en kennisdeling

**Documentatie van de Vorm**

- Duidelijke documentatie bijhouden van formulierdoeleinden, vereisten en bedrijfsregels
- Eindpunten voor documentintegratie, gegevensstromen en afhankelijkheden
- Versiehistorie behouden en logbestanden wijzigen voor formulierupdates
- Beste praktijken en lessen delen die over teams worden geleerd

**Opleiding en Goedkeuring**

- Teamleden trainen op Forms Experience Builder-mogelijkheden
- Richtlijnen vaststellen voor het maken van consistente formulieren in de hele organisatie
- Regelmatige sessies voor het delen van kennis voor nieuwe functies en beste praktijken
- Bewakingsprogramma&#39;s voor nieuwe gebruikers van het platform

### Assurance-kwaliteit

**Processen van het Overzicht**

- Intercollegiale toetsingsprocessen uitvoeren voor formulierontwerp en -implementatie
- Testprotocollen vaststellen voor formulierfunctionaliteit en gebruikerservaring
- Regelmatige controles van bestaande formulieren voor optimaliseringsmogelijkheden
- Feedbackverzameling van zowel interne gebruikers als eindgebruikers

**Normen en Richtlijnen**

- Organisatienormen ontwikkelen voor formulierontwerp en -implementatie
- Sjablonen en richtlijnen maken voor algemene formuliertypen
- Goedkeuringsprocessen instellen voor nieuwe formulieren en belangrijke wijzigingen
- Regelmatige herziening en actualisering van de organisatorische normen

## Geavanceerde beste praktijken

### Verbeterde slimme velden in LLM

**Leveraging AI Kennis**

- De ingebouwde kennis van de AI gebruiken voor uitgebreide veldopties
- Slimme velden aanvragen voor geografische gegevens, bedrijfsclassificaties en industriestandaarden
- Intelligente veldpopulatie implementeren voor een betere gebruikerservaring
- Precisie en volledigheid van slimme velden testen voor uw specifieke gebruiksgevallen

**Slimme Voorbeelden van het Gebied**

     &quot;voeg een gebied van de vertrekluchthaven met alle belangrijke luchthavens wereldwijd met inbegrip van codes IATA&quot;toe 
     &quot;creeer een uitvoerig industrieterrein gebruikend de standaard classificatie van NAICS&quot;
     &quot;omvat een professionele certificatiedrang die zich op baangebied&quot;aanpast 

### Geavanceerde formulierlogica

**Complexe BedrijfsRegels**

- Breek complexe bedrijfslogica in kleinere, testbare componenten
- De bedrijfsregelvereisten van het document duidelijk vóór implementatie
- Testen van randgevallen en uitzonderingsscenario&#39;s grondig
- Geef duidelijke gebruikersfeedback voor overtredingen van de bedrijfsregels

**Dynamisch Gedrag van de Vorm**

- Gebruik progressieve openbaarmaking om relevante velden weer te geven op basis van gebruikersinvoer
- Voer slimme gebreken uit die door gebruikers kunnen worden met voeten getreden
- Aangepaste formulieren maken die worden aangepast op basis van gebruikersgedrag en -voorkeuren
- Automatisering in balans brengen met gebruikerscontrole en transparantie

## Validatie en tests

### Uitgebreide teststrategie

**het Testen op meerdere niveaus**

- Eenheidstests voor afzonderlijke formuliercomponenten en validatieregels
- Integratietests voor eindpunten voor verzending en gegevensstromen
- Door de gebruiker uitgevoerde acceptatietests met representatieve gebruikersgroepen
- Prestatietests onder verschillende belastingsomstandigheden

**dwars-Platform Bevestiging**

- Formulieren testen in verschillende browsers en versies
- Valideer mobiele beleving op verschillende apparaten en schermformaten
- Toegankelijkheidstests met verschillende ondersteunende hulpmiddelen
- Netwerkconditietests voor verschillende verbindingssnelheden

### Kwaliteitswaarden

**Indicatoren van het Succes**

- Voltooiingscijfers boven de benchmarks van de bedrijfstak
- Lage foutpercentages en hoge score voor gebruikerstevredenheid
- Snelle laadtijden en responsieve gebruikersinteracties
- Succesvolle integratie met back-endsystemen en -processen

**Ononderbroken Controle**

- Regelmatige evaluatie van de prestaties van formulieren en feedback van gebruikers
- Proactieve identificatie en oplossing van problemen
- Trend analysis voor formuliergebruik en effectiviteit
- Benchmarking tegen industriestandaarden en beste praktijken

Voor extra begeleiding en gedetailleerde voorbeelden, verwijs naar de [ Begonnen Gids van de Bouwer van de Ervaring van Forms ](forms-ai-assistant-getting-started.md) en [ Snelle Bibliotheek van de Bouwer van de Ervaring van Forms ](ai-assistant-prompt-library.md).
