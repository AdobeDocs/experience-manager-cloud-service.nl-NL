---
title: Intelligente import en conversie
description: Leer hoe u bestaande documenten, PDF's en afbeeldingen transformeert naar interactieve digitale formulieren met de intelligente import- en conversiemogelijkheden van Forms Experience Builder.
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---


# Intelligente import en conversie

>[!NOTE]
>
> De Forms Experience Builder is beschikbaar via een programma voor vroege toegang. Controleer voordat u begint of u toegang hebt aangevraagd en gekregen.

Met de intelligente functie voor importeren en converteren van Forms Experience Builder kunt u bestaande documenten, PDF&#39;s en afbeeldingen met behulp van AI-analyse en -conversie transformeren in moderne, interactieve digitale formulieren.

## Ondersteunde bronindelingen

### PDF-documenten

**AcroForm PDFs:**

- Interactieve PDF forms met formuliervelden
- Statische PDF&#39;s met formulierachtige indelingen
- Documenten met meerdere pagina&#39;s met gestructureerde inhoud

**op XFA-Gebaseerde PDFs:**

- Legacy XFA-formulieren (XML Forms Architecture)
- Complexe bedrijfsformulieren met geavanceerde indelingen
- Overheid- en ondernemingsvormen

**Statische PDFs:**

- Gescande documenten en formulieren
- Formulieren voor afdrukken zonder interactieve elementen
- Documenten met formulierachtige structuren

### Afbeeldingsbestanden

**Gesteunde formaten:**

- PNG, JPG, JPEG, GIF
- Scans met hoge resolutie van papieren formulieren
- Screenshots van digitale formulieren
- Met de hand getekende schetsen en draadframes

**de kwaliteitsvereisten van het Beeld:**

- Minimaal 300 DPI voor tekstherkenning
- Tekst en formulierelementen wissen, leesbaar
- Goed contrast tussen tekst en achtergrond
- Correcte oriëntatie (niet geroteerd)

### Ontwerpbestanden

**de ontwerpen van Figma:**

- Formuliermodellen en prototypen
- UI/UX-ontwerpbestanden
- Formulierindelingen op basis van componenten

**Andere ontwerpformaten:**

- Adobe XD-bestanden
- Schetsontwerpen
- Draadframe-documenten

## Importeren en converteren

### Stap 1: Toegang tot de functie Importeren

1. Forms Experience Builder openen
2. Klik op het pictogram voor bijlagen in de interface
3. Selecteer de optie Importeren en converteren
4. Kies uw bronbestand

### Stap 2: Uw document uploaden

**voor de dossiers van PDF:**

1. PDF-document selecteren
2. Wacht tot AI de structuur analyseert
3. De gedetecteerde formulierelementen controleren
4. De conversie-instellingen bevestigen

**voor beelddossiers:**

1. Upload uw afbeelding (PNG, JPG, enz.)
2. De AI analyseert de layout en tekst
3. De gedetecteerde formuliervelden controleren
4. Breng indien nodig aanpassingen aan

**voor ontwerpdossiers:**

1. Uw ontwerpbestand uploaden
2. De AI zal formuliercomponenten extraheren
3. De omgezette elementen controleren
4. De formulierstructuur aanpassen

### Stap 3: Reviseren en aanpassen

Na de eerste conversie:

1. **Overzicht ontdekte gebieden**: Controle dat alle vormelementen correct worden geïdentificeerd
2. **pas gebiedstypes** aan: wijzig gebiedstypes (tekst, dropdown, checkbox, enz.)
3. **voeg bevestiging** toe: De regels van de het gebiedsbevestiging van de opstelling
4. **pas het stileren** aan: Pas thema&#39;s en branding toe
5. **functionaliteit van de Test**: Verifieer vormgedrag en logica

## Conversievoorbeelden

### PDF-formulierconversie

**Oorspronkelijke vorm van PDF:**

- Statisch contactformulier met naam, e-mail, telefoonvelden
- Sectie Bedrijfsgegevens
- Opmerkingen, gebied

**Omgezette adaptieve vorm:**

- Interactieve tekstvelden met validatie
- Vervolgkeuzelijst voor bedrijfsgrootte
- Tekstgebied met meerdere regels voor opmerkingen
- Knop Verzenden met e-mailintegratie

### Afbeelding omzetten in formulier

**Origineel beeld:**

- Foto van een papieren registratieformulier
- Handgeschreven formulier met selectievakjes
- Meerdere secties voor verschillende informatie

**Omgezette adaptieve vorm:**

- Digitale tekstvelden die overeenkomen met de indeling
- Interactieve selectievakjes en keuzerondjes
- Georganiseerde secties met juiste tussenruimte
- Mobiel responsief ontwerp

### Bestandsconversie ontwerpen

**Origineel ontwerp van het Cijfer:**

- Moderne UI-modellen met formuliercomponenten
- Benoemde stijlen en kleuren
- Complexe lay-out met meerdere deelvensters

**Omgezette adaptieve vorm:**

- Pixelperfecte recreatie van het ontwerp
- Interactieve formulierelementen
- Responsief gedrag op verschillende apparaten
- Brand-consistente opmaak

## Geavanceerde conversiefuncties

### Intelligente velddetectie

De AI detecteert en converteert automatisch:

- **gebieden van de Tekst**: Enige-lijn en multi-lijn tekstgebieden
- **gebieden van de Selectie**: Dropdowns, radioknopen, checkboxes
- **gebieden van de Datum**: De plukkers van de datum met juiste het formatteren
- **de gebieden van het Aantal**: Numerieke input met bevestiging
- **het Dossier uploadt**: Het document en het beeld uploadt gebieden

### Indeling behouden

De conversie onderhoudt:

- **Oorspronkelijke structuur**: Behoudt de lay-out en de organisatie
- **Visuele hiërarchie**: Handhaaft rubrieken en sectieonderbrekingen
- **het Tussenruimte en groepering**: Houdt juiste vorm het uit elkaar plaatsen
- **Merk elementen**: Behoudt logo&#39;s en het stileren elementen

### Slimme validatie

Voegt automatisch de juiste validatie toe:

- **E-mailgebieden**: De bevestiging van het E-mailformaat
- **de aantallen van de Telefoon**: De formaatbevestiging van het aantal van de telefoon
- **Vereiste gebieden**: Merken duidelijke vereiste gebieden
- **waaiers van de Datum**: Plaatst aangewezen datumbeperkingen

## Aanbevolen procedures voor importeren en converteren

### Brondocumenten voorbereiden

**voor de dossiers van PDF:**

- Zorg ervoor dat tekst selecteerbaar is (niet alleen afbeeldingen)
- Scans van hoge kwaliteit gebruiken voor statische PDF&#39;s
- Inhoud indelen in logische secties
- Inclusief duidelijke veldlabels

**voor beelden:**

- Afbeeldingen met hoge resolutie gebruiken (300+ DPI)
- Zorg voor goed contrast en goed leesbaarheid
- Vermijd geroteerde of scheefgetrokken afbeeldingen
- Alle formulierelementen in de afbeelding opnemen

**voor ontwerpdossiers:**

- Gebruik consistente naamgeving voor formuliercomponenten
- Lagen logisch ordenen
- Alle benodigde formulierelementen opnemen
- Exporteren in hoge kwaliteit

### Optimalisatie na conversie

**Overzicht en test:**

- Alle formuliervelden en validatie testen
- Mobiele reactiesnelheid controleren
- Toegankelijkheidscontrole
- Functionaliteit voor verzending testen

**pas aan en verbetert:**

- Zakelijke logica en voorwaardelijke regels toevoegen
- Correcte foutafhandeling implementeren
- Verzendeindpunten configureren
- Standaardopmaak en thema&#39;s toepassen

## Problemen met conversie oplossen

### Algemene problemen

**slechte gebiedsopsporing:**

- Afbeeldingskwaliteit of PDF-teksthelderheid verbeteren
- Veldtypen handmatig aanpassen na conversie
- Meer beschrijvende veldlabels gebruiken in bron

**kwesties van de Lay-out:**

- Tussenruimte en uitlijning handmatig aanpassen
- Regelgevende ontwerpprincipes gebruiken
- Testen op verschillende schermgrootten

**Ontbrekende elementen:**

- Ontbrekende velden handmatig toevoegen
- Opnieuw importeren met betere bronkwaliteit
- Incrementele conversiemethode gebruiken

### Hulp krijgen

Voor conversieproblemen:

- Controle [ Veelgestelde vragen van de Bouwer van de Ervaring van Forms ](forms-experience-builder-frequently-asked-questions.md)
- Herzie [ Begonnen gids ](forms-experience-builder-getting-started.md)
- Neem contact op met de systeembeheerder voor technische ondersteuning

## Verwante artikelen

- [Overzicht van Forms Experience Builder](product-overview.md)
- [Aan de slag met Forms Experience Builder](forms-experience-builder-getting-started.md)
- [Forms Experience Builder implementeren en configureren](deploy-forms-experience-builder.md)
- [Formulierverzending en integratie](form-submission-integration.md)
- [Veelgestelde vragen](forms-experience-builder-frequently-asked-questions.md)
