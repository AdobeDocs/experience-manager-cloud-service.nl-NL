---
title: Forms Experience Builder - Veelgestelde vragen
description: Vind antwoorden op algemene vragen over de Bouwer van de Ervaring van Forms, met inbegrip van opstelling, gebruik, oplossen van problemen, en beste praktijken.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
exl-id: f43c2586-9075-47dc-aa45-5ed2d2979b6d
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 0%

---

# Forms Experience Builder - Veelgestelde vragen

>[!NOTE]
>
> De Forms Experience Builder is beschikbaar via een programma voor vroege toegang. Controleer voordat u begint of u toegang hebt aangevraagd en gekregen.

In deze veelgestelde vragen worden de meest voorkomende vragen over Forms Experience Builder behandeld, van basisconfiguratie tot geavanceerde functies en probleemoplossing.

## Algemene vragen

### Wat is Forms Experience Builder?

Forms Experience Builder is een door AI aangedreven programma voor het maken van formulieren waarmee u geavanceerde digitale formulieren kunt maken met behulp van een conversatietaal. In plaats van traditionele interfaces voor slepen en neerzetten of complexe codering beschrijft u gewoon wat u wilt en maakt de AI het formulier voor u.

### Wie kan Forms Experience Builder gebruiken?

Forms Experience Builder is ontworpen voor:

- **creators van de Vorm** die vormen snel en efficiënt willen bouwen
- **Bedrijfs gebruikers** die vormen zonder technische deskundigheid moeten tot stand brengen
- **Ontwikkelaars** die hefboomwerking AI voor snelle vorm het prototypen willen
- **Beheerders** die de werkschema&#39;s van de vormverwezenlijking moeten vormen en beheren

### Is Forms Experience Builder beschikbaar voor alle AEM Forms-klanten?

Forms Experience Builder is momenteel beschikbaar via een programma voor vroege toegang. Neem contact op met uw Adobe-medewerker om toegang aan te vragen en te weten te komen over de beschikbaarheid voor uw organisatie.

## Instellen en configureren

### Wat zijn de eerste vereisten voor het gebruik van Forms Experience Builder?

Voordat u Forms Experience Builder gaat gebruiken, moet u controleren of:

- Toegang tot Forms Experience Builder via het programma voor vroege toegang
- AEM Forms as a Cloud Service met Adaptive Forms Core-componenten
- Basiskennis van formulierconcepten en bedrijfsvereisten

Voor gedetailleerde technische opstellingsvereisten, zie [&#x200B; opstellen en vormen de Bouwer van de Ervaring van Forms &#x200B;](deploy-forms-experience-builder.md).

### Hoe kan ik Forms Experience Builder inschakelen in mijn omgeving?

Forms Experience Builder is afhankelijk van uw AEM Forms-implementatie:

**voor Edge Delivery Services:**

- Uw project voorbereiden voor Edge Delivery Services Forms
- De Forms Experience Builder inschakelen in de Universal Editor

**voor op kerncomponenten-gebaseerde vormen:**

- Zorg ervoor dat de adaptieve Forms Core-componenten zijn ingeschakeld
- De Forms Experience Builder configureren in de Adaptive Forms Editor

### Kan ik Forms Experience Builder gebruiken met bestaande formulieren?

Ja, Forms Experience Builder kan op verschillende manieren met bestaande formulieren werken:

- Bestaande PDF forms importeren en converteren
- Bestaande adaptieve formulieren verbeteren met door AI aangedreven functies
- Slimme velden toevoegen aan huidige formulierstructuren

## Formulieren maken

### Hoe maak ik mijn eerste formulier?

Begin met een eenvoudige beschrijving van wat u wilt:

     creeer een contactvorm met naam, e-mail, en berichtgebieden 

De AI genereert de basisformulierstructuur, die u vervolgens kunt verbeteren met extra functies, validatie en opmaak.

### Welke typen formulieren kan ik maken?

Forms Experience Builder ondersteunt verschillende formuliertypen:

- Contactformulieren en feedbackformulieren
- Registratie- en instapformulieren
- Beoordeling- en beoordelingsformulieren
- Formulieren met meerdere stappen met voorwaardelijke logica
- Forms met geüploade bestanden en complexe validatie

### Kan ik formulieren met meerdere stappen maken?

Ja, u kunt formulieren met meerdere stappen maken in de natuurlijke taal:

     creeer een progressieve vorm met 3 stappen: persoonlijke info, voorkeur, bevestiging 

De AI stelt de formulierstructuur automatisch in met navigatie tussen de stappen.

### Hoe voeg ik validatie toe aan formuliervelden?

Validatie toevoegen met opdrachten voor natuurlijke talen:

     maak @email een vereist gebied met e-mailformaatbevestiging 
     toevoegen de formaatbevestiging van het Amerikaanse telefoonaantal aan @phoneNumber 
     vastgestelde leeftijdsbevestiging: moet 18 of ouder voor @dateOfBirth 
 zijn

## Geavanceerde functies

### Wat zijn LLM-Verbeterde slimme gebieden?

Slimme velden met LLM-functionaliteit zijn intelligente formuliervelden die vooraf zijn ingevuld met relevante opties van AI-kennisbanken. Bijvoorbeeld:

- Landneerstortingen met alle wereldlanden
- Industriële classificaties met standaardcodes
- Geografische gegevens met staten, steden en postcodes

### Hoe kan ik bestaande documenten in formulieren importeren?

U kunt verschillende documenttypen importeren:

- **PDF forms**: Upload statische of interactieve PDFs
- **Beelden**: Upload foto&#39;s van papieren vormen of screenshots
- **de dossiers van het Ontwerp**: De ontwerpen van het Cijfer van de invoer of andere ontwerpformaten

Gebruik het bevestigingspictogram in de Bouwer van de Ervaring van Forms om uw document te uploaden en uw omzettingsvereisten te beschrijven.

### Kan ik formulieren integreren met externe systemen?

Ja, Forms Experience Builder ondersteunt verschillende integratieopties:

- E-mailverzendingen met aangepaste sjablonen
- Integratie van REST API met externe services
- Integratie van cloudopslag (Azure, AWS, Google Cloud)
- Workflowintegratie (Power Automate, AEM Workflow)

## Problemen oplossen

### De AI begrijpt mijn verzoek niet. Wat moet ik doen?

Probeer de volgende benaderingen:

- Meer specifiek in je beschrijving
- Complexe aanvragen onderverdelen in kleinere stappen
- Gebruik veldverwijzingen (@fieldName) voor beoogde wijzigingen
- Geef duidelijke voorbeelden van wat u wilt

### Mijn formuliervalidatie werkt niet. Hoe los ik het op?

Controleer deze veelvoorkomende problemen:

- Controleren of de veldnamen exact overeenkomen (hoofdlettergevoelig)
- Controleer of de validatiesyntaxis correct is
- Testvalidatieregels afzonderlijk
- Foutberichten voor specifieke problemen controleren

### Voorwaardelijke logica activeert niet correct. Wat is er mis?

Voorwaardelijke logica oplossen door:

- Ervoor zorgen dat naar veldnamen correct wordt verwezen
- Syntaxis en voorwaarden van regels controleren
- Testen met verschillende invoercombinaties
- Het verifiëren van gebiedstypes past regelvereisten aan

### De interface wordt niet geladen. Wat moet ik doen?

Probeer de volgende oplossingen:

- Browser vernieuwen en cache wissen
- Controleer uw internetverbinding
- Controleren of u beschikt over de juiste toegangsrechten
- Neem contact op met de systeembeheerder als de problemen zich blijven voordoen

## Aanbevolen procedures

### Hoe kan ik betere formulieren maken met Forms Experience Builder?

Volg deze aanbevolen procedures:

- **ben specifiek**: Verstrek gedetailleerde beschrijvingen van wat u wilt
- **Begin eenvoudig**: Begin met basisstructuur en voeg geleidelijk ingewikkeldheid toe
- **Test grondig**: Valideer alle vormfunctionaliteit vóór plaatsing
- **Gebruik stijgende ontwikkeling**: Bouw vormen stap voor stap

### Wat moet ik voorkomen bij het maken van formulieren?

Vermijd deze veelvoorkomende fouten:

- Te vaag zijn in uw beschrijvingen
- Alles tegelijk maken
- Testen en valideren van overslaan
- Houd niet rekening met mobiele reactiesnelheid

### Hoe kan ik ervoor zorgen dat mijn formulieren toegankelijk zijn?

Forms Experience Builder bevat toegankelijkheidsfuncties:

- Automatische WCAG-nalevingscontrole
- Compatibiliteit met schermlezers
- Ondersteuning voor toetsenbordnavigatie
- Opties in de modus Hoog contrast

## Integratie en implementatie

### Hoe implementeer ik formulieren die met Forms Experience Builder zijn gemaakt?

Forms die is gemaakt met Forms Experience Builder volgt de standaard AEM Forms-implementatieprocessen:

- Formulieren publiceren via de ontwerpomgeving van AEM
- Eindpunten voor formulierverzending configureren
- Workflows voor formulierverwerking instellen
- Formulieren testen in de productieomgeving

### Kan ik de AI-reacties en het AI-gedrag aanpassen?

Ja, u kunt verschillende aspecten configureren:

- Stijl van de reactie (beknopt, gedetailleerd, evenwichtig)
- Taalvoorkeuren en -terminologie
- Interface-aanpassingsopties
- Toegankelijkheidsinstellingen

### Hoe krijg ik hulp met Forms Experience Builder?

Voor extra ondersteuning:

- Controle de [&#x200B; Begonnen gids &#x200B;](forms-experience-builder-getting-started.md)
- Herzie [&#x200B; opstellen en gids &#x200B;](deploy-forms-experience-builder.md) vormen
- Neem contact op met de systeembeheerder
- Neem contact op met Adobe voor technische problemen

## Verwante artikelen

- [Overzicht van Forms Experience Builder](product-overview.md)
- [Aan de slag met Forms Experience Builder](forms-experience-builder-getting-started.md)
- [Forms Experience Builder implementeren en configureren](deploy-forms-experience-builder.md)
- [Met LLM verbeterde slimme velden](forms-experience-builder-llm-smart-fields.md)
- [Intelligente import en conversie](intelligent-import-conversion.md)
- [Formulierverzending en integratie](form-submission-integration.md)
