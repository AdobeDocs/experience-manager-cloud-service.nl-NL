---
title: Responsieve Forms maken met Universal Editor
description: Leer responsieve formulieren voor alle apparaten ontwerpen, testen en optimaliseren met de Universal Editor. Masterapparaat testen, layout patronen en mobiele optimalisatietechnieken voor AEM Forms met Edge Delivery Services.
keywords: responsieve formulieren, mobiele formulieren, apparaattests, universele editor, adaptieve indeling, formulieroptimalisatie, mobiel ontwerp, responsief ontwerp, formulierindelingen, apparaatemulator
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: ccfb85da187e828b5f7e8b1a8bae3f483209368d
workflow-type: tm+mt
source-wordcount: '1815'
ht-degree: 0%

---


# Responsieve Forms maken met Universal Editor

Gebruikers kunnen formulieren openen op een groot aantal apparaten, zoals desktops, tablets en smartphones. Het ontwerpen van responsieve formulieren zorgt voor een optimale ervaring voor alle gebruikers, ongeacht het apparaat. In deze handleiding wordt uitgelegd hoe u formulieren voor elke schermgrootte ontwerpt, test en optimaliseert met de Universal Editor.


Bij het maken van responsieve formulieren zijn twee hoofdactiviteiten betrokken:

- **Responsief het Testen:** Voorproef en test uw vormen over diverse het schermgrootte gebruikend apparatenmededingers.
- **Responsief Ontwerp:** selecteer en voer lay-outpatronen uit die naadloos aan verschillende apparaten aanpassen.

**In deze gids, zult u leren hoe te:**

- Formulieren testen op computers, tablets en mobiele apparaten
- Selecteer de juiste layoutpatronen voor uw inhoud
- Aanbevolen werkwijzen voor responsief ontwerp toepassen
- Algemene problemen met formulieren oplossen
- Formulieren optimaliseren voor mobiele prestaties

## Waarom responsieve Forms belangrijk is

**Gevolgen van de Ervaring van de Gebruiker:**

- Meer dan 60% van de gebruikers heeft toegang tot formulieren op mobiele apparaten
- Slechte mobiele ervaringen leiden tot een 67% hogere wachttijd
- Met responsieve formulieren kunt u de voltooiingstarieven met maximaal 25% verhogen

**BedrijfsVoordelen:**

- Hogere voltooiingssnelheden voor formulieren
- Verbeterde gebruikerstevredenheid
- Verbeterde toegankelijkheidscompatibiliteit
- Lagere ontwikkelings- en onderhoudskosten

>[!TIP]
>
> **mobiel-eerste Benadering:** Begin met het ontwerpen voor mobiele apparaten, dan verbetert voor grotere schermen. Dit verzekert kernfunctionaliteit in het meest beperkte milieu werkt.

## Deel 1: Forms testen op apparaten

Door uw formulieren op verschillende apparaten te testen, kunt u problemen die op een probleem reageren, opsporen en oplossen voordat gebruikers deze tegenkomen. De Universal Editor biedt een emulatormodus om verschillende schermgrootten en -oriëntaties te simuleren.

### Je Forms testen

**Stap 1: Open de Mededinger van het Apparaat**

1. Open het formulier in de Universal Editor.
2. Klik het ![ pictogram van de Mededinger ](/help/edge/docs/forms/universal-editor/assets/emulator.png) {height=2%,width=2%} **Emulator** pictogram in de toolbar.
3. Het menu van de apparaatkiezer wordt weergegeven.

![ Universele Redacteur Responsieve het Testen Interface ](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

**Stap 2: Selecteer een Apparaat voor het Testen**

- **Desktop** (1200px+ breedte): Standaard het uitgeven mening
- **Tablet** (768px-1199px breedte): het schermtesten van Medium
- **Mobiel** (320px-767px breedte): Kleine het schermtesten
- **Douane**: Specificeer nauwkeurige afmetingen voor specifieke apparaten

**Stap 3: De Oriëntaties van het Apparaat van de test**

Gebruik het **pictogram van de Rotator van het 1&rbrace; Scherm** om allebei te testen:

- **Staand wijze**: Standaard mobiele richtlijn
- **Liggende wijze**: Geroteerde tablet of telefoonmening

### Resultaten van testen van apparaten

Elk apparaattype onthult unieke responsieve gedragingen:

| **Type van Apparaat** | **Breedte van het Scherm** | **wat te controleren** | **Gemeenschappelijke Kwesties** |
|-----------------|------------------|-------------------|-------------------|
| **Desktop** | 1200 px+ | Volledige layout, alle functies zichtbaar | Te veel witruimte, te brede lay-outs |
| **Tablet** | 768 px-1199 px | Stapelen van componenten, bruikbaarheid van navigatie | Onhandige grootte, problemen met aanraakdoelen |
| **Mobiel** | 320 px, 767 px | Lay-out met één kolom, duimnavigatie | Kleine tekst, knoppen met weinig tussenruimte |
| **Douane** | Door gebruiker gedefinieerd | Apparaatspecifieke vereisten | Hoekgevallen van onderbrekingspunten |

### Visuele voorbeelden door Apparaat

**Mening van de Desktop (1200px+):**
![ de vormmening van de Desktop ](/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png)
*volledig-breedtelay-out met zij aan zij vormgebieden.*

**Mening van de Tablet (768px-1199px):**
![ de vormmening van Tablet ](/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png)
*Medium-breedte lay-out met aangepaste component uit elkaar plaatsen.*

**Mobiele Mening (320px-767px):**
![ Mobiele vormmening ](/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png)
*enig-kolomlay-out met gestapelde componenten.*

**Mening van het Apparaat van de Douane:**
![ het apparatenmening van de Douane ](/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png)
*Gebruiker-gespecificeerde afmetingen voor het gerichte testen.*

### Testworkflow

**voor Nieuwe Forms:**

1. **bouwt in Desktopmening:** Begin met volledige functionaliteit.
2. **Test op tablet:** controleer aanpassingen voor middelgrote schermen.
3. **Valideer op mobiel:** verzeker bruikbaarheid op kleine schermen.
4. **bevestig ontvankelijke kwesties:** pas lay-outs aan zoals nodig.
5. **herstelt alle apparaten:** bevestig moeilijke situaties over alle grootte.

**voor Bestaande Forms:**

1. **Snelle mobiele controle:** Werkt de vorm aan telefoons?
2. **identificeer probleemgebieden:** de lay-out en bruikbaarheidskwesties van de nota.
3. **Systematisch testen:** test grondig elke apparatengrootte.
4. **de kwesties van het Document:** spoor wat moet worden bevestigd.
5. **voert moeilijke situaties uit:** methodisch de kwesties van het Adres.

## Deel 2: Responsieve layoutpatronen selecteren

Lay-outpatronen bepalen hoe de formulierinhoud wordt aangepast aan verschillende schermgrootten. Het juiste patroon verbetert zowel de gebruikerservaring als de mobiele prestaties.

### Overzicht van het layoutpatroon

| **Type van Lay-out** | **Best voor** | **Mobiele Prestaties** | **Complexiteit** |
|---------------------|-------------------------------------------|------------------------|----------------|
| **Lay-out van het Comité** | Gecategoriseerde inhoud, formulieren in dashboardstijl | Goed | Laag |
| **Lay-out van de Tovenaar** | Meerdere stappen, complexe workflows | Uitstekend | Medium |
| **Lay-out van de Accordeon** | Inhoud in veelgestelde vragen, optionele secties | Uitstekend | Laag |

### Handleiding voor snelle besluitvorming

**Lay-out van het Comité van het Gebruik wanneer:**

- Uw inhoud is verdeeld in verschillende categorieën
- Gebruikers moeten meerdere secties tegelijk weergeven
- De inhoud is relatief eenvoudig

**Lay-out van de Tovenaar van het Gebruik wanneer:**

- Het formulier bevat meerdere logische stappen
- U wilt cognitieve belasting verminderen
- Mobiele gebruikers zijn een primair publiek

**Lay-out van de Accordeon van het Gebruik wanneer:**

- Het formulier bevat optionele of secundaire inhoud
- Ruimtebehoud is belangrijk
- Inhoud kan logisch worden gegroepeerd

### Layout deelvenster

**Doel:** organiseert verwante inhoud in visueel verschillende secties die gelijktijdig kunnen worden bekeken.

![ Voorbeeld van de Lay-out van het Comité ](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

**Responsief Gedrag:**

- **Desktop (1200px+):** de vertoningen van panelen zij aan zij of in een net
- **Tablet (768px-1199px):** stapel van Panelen verticaal met het uit elkaar plaatsen
- **Mobiel (320px-767px):** Enige-kolomlay-out met duidelijke sectieonderbrekingen

**Stappen van de Implementatie:**

1. Gebruik de [ Component van het Comité ](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel).
2. Groepeer verwante velden in elk deelvenster.
3. Voeg duidelijke koppen toe voor elke sectie.
4. Zorg voor voldoende ruimte tussen deelvensters.

**Beste praktijken:**

- Beperk het aantal tot 3-4 deelvensters op het bureaublad om overweldigende gebruikers te voorkomen.
- Gebruik beschrijvende titels voor elk deelvenster.
- Groepeer verwante velden logisch om cognitieve belasting te verminderen.
- Navigatie in het deelvenster Testen op aanraakapparaten.

**Gevallen van het Gebruik van het Voorbeeld:**

- **Toepassing van de Baan:** Persoonlijke Info, Onderwijs, Ervaring, Verwijzingen
- **de Registratie van het Product:** Basisdetails, Technische Specificaties, Info van de Garantie
- **Forms van het Onderzoek:** Demografieën, Voorkeur, Terugkoppeling, Contact

### Wizard Layout

**Doel:** gidst gebruikers door complexe processen stap voor stap, verminderend cognitieve lading en verbeterend voltooiingstarieven.

![ het Voorbeeld van de Lay-out van de Tovenaar ](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

**Responsief Gedrag:**

- **Alle Apparaten:** handhaaft enig-stap nadruk voor optimale mobiele ervaring.
- **Inhoud van de Stap:** past binnen elke stap (het stapelen of zij aan zij) aan.
- **Navigatie:** Aanraakvriendelijke knopen met voldoende het uit elkaar plaatsen.
- **Indicator van de Voortgang:** schrapt geschikt voor het schermgrootte.

**Stappen van de Implementatie:**

1. Gebruik de [ Component van de Tovenaar ](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard).
2. Complexe formulieren onderbrengen in logische stappen (3-7 stappen zijn optimaal).
3. Voeg voortgangsindicatoren toe voor de gebruikersierichting.
4. Zorg voor duidelijke besturingselementen voor navigatie (Volgende, Vorige, Opslaan).

**Mobiele Optimalisering:**

- Gebruik grote aanraakdoelen (minimaal 44 px) voor navigatieknoppen.
- Zorg ervoor dat de step-indicatoren duidelijk en zichtbaar zijn op kleine schermen.
- Beperk het aantal velden per stap om schuiven te beperken.
- Automatisch opslaan inschakelen om gegevensverlies te voorkomen.

**Beste praktijken:**

- Zorg voor logische stapvoortgang. Elke stap moet op de vorige voortbouwen.
- Gebruik heldere staptitels, zodat gebruikers weten wat ze moeten verwachten.
- Valideer de invoer bij elke stap om fouten vroeg af te vangen.
- Gebruikers kunnen terugnavigeren om gegevens te bekijken of te bewerken.

**Gevallen van het Gebruik van het Voorbeeld:**

- **Verzekeringsclaims:** incident → Bewijs → Persoonlijk overzicht
- **de Opstelling van de Rekening:** Basis Info → Voorkeur → Veiligheid → Bevestiging
- **Proces van de Orde:** Producten → Verzending → Betaling → Samenvatting

### Accordeonlay-out

**Doel:** bespaart ruimte door inhoud in doen ineenstorten secties te organiseren, ideaal voor facultatieve of secundaire informatie.

![ het Voorbeeld van de Lay-out van de Accordeon ](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

**Responsief Gedrag:**

- **Uitstekende mobiele prestaties:** slechts relevante inhoud wordt getoond.
- **aanraking-geoptimaliseerde kopballen:** Gemakkelijk om secties te tikken en uit te breiden.
- **Vloeiende animaties:** verstrek visuele terugkoppelen voor interactie.
- **ruimteefficiënt:** minimaliseert het scrollen op alle apparaten.

**Stappen van de Implementatie:**

1. Gebruik de [ Component van de Accordeon ](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion).
2. Groepeer gerelateerde optionele inhoud in elke sectie.
3. Gebruik beschrijvende sectiekoppen.
4. Stel de juiste open/gesloten standaardstatussen in.

**Mobiele Voordelen:**

- Vermindert het schuiven door ongebruikte secties samen te vouwen.
- Aanraakvriendelijke interactie met natuurlijke bewegingen voor uitvouwen/samenvouwen.
- Sneller laden—Alleen actieve inhoud is zichtbaar.
- Verbeterde focus - gebruikers zien alleen wat ze nodig hebben.

**Beste praktijken:**

- Gebruik duidelijke sectiekoppen, zodat gebruikers weten wat er in staat voordat u gaat uitbreiden.
- Gerelateerde inhoud logisch groeperen binnen elke sectie.
- Stel de belangrijke secties in die moeten worden uitgevouwen als dat nodig is.
- Geef korte sectievoorvertoningen weer om gebruikers te helpen beslissen wat ze willen uitbreiden.

**Gevallen van het Gebruik van het Voorbeeld:**

- **de Configuratie van het Product:** Basis → Geavanceerd → Bureau → Steun
- **FAQ Forms:** Rekening → Facturatie → Technisch → Algemeen
- **Forms van Montages:** Privacy → Meldingen → Vorm → Geavanceerd

## Deel 3: Aanbevolen werkwijzen voor responsief ontwerp

### Beste praktijken door Type van Apparaat

+++Mobiele optimalisatie (320 px-767 px)

**Essentiële Praktijken:**

- Gebruik een lay-out met één kolom voor alle inhoud.
- Geef grote, aanraakvriendelijke knoppen (minimale hoogte van 44 px).
- Vereenvoudig navigatie met duidelijke achterkant/volgende opties.
- Minimaliseer het schuiven binnen elke sectie.
- Automatisch focussen op het eerste veld om het toetsenbord weer te geven.

**gebied-Specifieke Richtlijnen:**

- **de input van de Tekst:** Volledige breedte met de veelvoudige opvulling.
- **Dropdowns:** Gebruik inheemse uitgezochte elementen voor betere aanrakingservaring.
- **plukkers van de Datum:** Gebruik inheemse datuminput voor mobiele verenigbaarheid.
- **uploadt het Dossier:** verstrek grote, duidelijke uploadgebieden.

+++

+++Tablet optimaliseren (768 px-1199 px)

**Strategieën van de Lay-out:**

- Gebruik lay-outs met twee kolommen voor verwante velden.
- Test zowel de stand Staand als Liggend.
- Ondersteuning voor aanraak- en muisinteractie.
- Grotere inhoudsgebieden bieden met behoud van leesbaarheid.

+++

+++Desktop Optimization (1200px+)

**Geavanceerde Eigenschappen:**

- Gebruik lay-outs met meerdere kolommen voor efficiënt ruimtegebruik.
- Sneltoetsen voor stroomgebruikers aanbieden.
- Hoverstatussen implementeren voor interactieve feedback.
- Geavanceerde validatie voorzien van gedetailleerde foutberichten.

+++

## Uitgebreide probleemoplossing

### Lay-outproblemen

+++pagina-einden van formulierlay-outs op mobiele apparaten

**Gemeenschappelijke Oorzaken:**

- Elementen met vaste breedte die niet worden geschaald
- CSS die is ontworpen voor eerste lay-outs voor desktops
- Afbeeldingen of inhoud die de containers overlopen

**Oplossingen:**

- Zorg ervoor dat de afbeeldingen en containers worden geschaald naar de schermgrootte.
- Gebruik een mobiel-eerste ontwerp met progressieve verbetering.
- Testen met zowel apparaatemulators als echte apparaten.
- Gebruik flexibele grootten in plaats van vaste afmetingen.

+++

+++Touch-doelen te klein

**Gemeenschappelijke Oorzaken:**

- Knoppen kleiner dan 44px × 44px
- Interactieve elementen die te dicht bij elkaar zijn geplaatst
- Aangepaste CSS-overschrijvingen voor aanraakvriendelijke standaardinstellingen

**Oplossingen:**

- Zorg ervoor dat alle interactieve elementen ten minste 44px × 44px zijn.
- Tussenruimte toevoegen tussen knoppen en koppelingen.
- Testen van aanrakingsinteractie met echte vingers, niet alleen met een muis.
- Gebruik meer aanraakdoelgebieden om gemakkelijker te kunnen tikken.

+++

+++Problemen met overloop van inhoud

**Gemeenschappelijke Oorzaken:**

- Lange tekst of labels die niet omlopen
- Containers met vaste breedte
- Afbeeldingen die niet correct worden geschaald

**Oplossingen:**

- Tekstomloop inschakelen voor lange inhoud.
- Gebruik responsieve afbeeldingen die op de juiste wijze worden geschaald.
- Voer flexibele lay-outs uit die zich aan inhoud aanpassen.
- Testen met verschillende lengte van inhoud.

+++

### Prestatieproblemen

+++ Langzaam laden op mobiel

**Gemeenschappelijke Oorzaken:**

- Grote afbeeldingen zijn niet geoptimaliseerd voor mobiele apparaten
- Buitengewone uitvoering van JavaScript
- Te veel formuliervelden tegelijk laden

**Oplossingen:**

- Optimaliseer afbeeldingen voor verschillende schermgrootten.
- Niet-kritieke inhoud alleen laden wanneer dat nodig is.
- Gebruik technieken om het laden van mobiele apparaten te versnellen.
- Scripts en widgets van derden minimaliseren.

+++

### Problemen met testen en valideren

+++emulator vs. verschillen in echt apparaat

**Gemeenschappelijke Oorzaken:**

- Browserspecifieke renderverschillen
- Verschillen tussen aanraken en muis
- Netwerksnelheidsvariaties

**Oplossingen:**

- Test waar mogelijk op de werkelijke apparaten.
- Gebruik meerdere browsers voor emulatortesten.
- Simuleer verschillende netwerksnelheden tijdens het testen.
- Valideren met echte gebruikers in doelomgevingen.

+++

## Succeswaarden voor responsieve Forms

+++Belangrijkste prestatie-indicatoren

**Metriek van de Ervaring van de Gebruiker:**

- **de voltooiingstarief van de Vorm:** Doel 85%+ op mobiel
- **Te voltooien Tijd:** De mobiele voltooiingstijd zou binnen 20% van Desktop moeten zijn
- **tarief van de Fout:** minder dan 5% bevestigingsfouten
- **Ontbrekingspunten:** identificeer waar de gebruikers weg vallen

**Technische Prestaties:**

- **de ladingstijd van de Pagina:** minder dan 3 seconden op netwerken 3G
- **de Kernwaarden van het Web van de Kern:** ga alle prestaties van Google benchmarks over
- **score van de Toegankelijkheid:** WCAG 2.1 de naleving van AA
- **dwars-browser verenigbaarheid:** 98%+ functionaliteit over belangrijkste browsers

+++

+++Checklist voor testen

**vóór het Publiceren:**

- Test het formulier op mobiele apparaten.
- Zorg ervoor dat alle aanraakdoelen ten minste 44px × 44px zijn.
- Controleer de leesbaarheid van de tekst bij alle schermgrootten.
- Bevestig dat formuliervalidatie werkt op alle apparaten.
- Zorg ervoor dat de laadtijd op mobiele apparaten minder dan 3 seconden is.
- Controleer of alle interactieve elementen toegankelijk zijn.
- Test het formulier verzenden op alle ondersteunde apparaten.

+++

## Volgende stappen

**Onmiddellijke Acties:**

1. **controleer uw huidige vormen:** test bestaande vormen gebruikend de apparatenmededinger.
2. **identificeer snel wint:** bevestig duidelijke mobiele bruikbaarheidskwesties eerst.
3. **voorrang geven aan hoog-verkeersvormen:** concentreer zich op vormen met het meest gebruikereffect.
4. **voer een mobiel-eerste benadering uit:** Begin met het kleinste schermontwerp.

**Geavanceerde Optimalisering:**

- **Prestaties controle:** opstelling analyseert om vormmetriek te volgen.
- **het testen A/B:** Experimenteer met verschillende lay-outs en benaderingen.
- **gebruiker terugkoppelt inzameling:** verzamel inzichten van echte gebruikers.
- **Ononderbroken verbetering:** herzie en optimaliseer regelmatig vormen.


