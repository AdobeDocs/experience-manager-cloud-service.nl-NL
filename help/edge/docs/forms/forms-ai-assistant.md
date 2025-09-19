---
title: AI Assistant voor AEM Forms (Forms Experience Builder)
description: Krachtige formulieren sneller maken met formulierfragmenten
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 0%

---


# Aan de slag met AI Assistant voor AEM Forms (Forms Experience Builder)

>[!NOTE]
>
>
> De Medewerker van AI voor AEM Forms (de Bouwer van de Ervaring van Forms) is beschikbaar onder het **vroege adoptieprogramma**. Als u geïnteresseerd bent, stuurt u een e-mail van uw werkadres naar mailto :aem-forms-ea@adobe.com om toegang tot de mogelijkheid te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze documentatie wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De eigenschappen, de bevelen, en de voorbeelden kunnen veranderen aangezien AI Medewerker voor AEM Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

De AI Assistant voor AEM Forms transformeert hoe u formulieren maakt. Hierin wordt beschreven wat u nodig hebt in de natuurlijke taal en hoe uw formulieren tot leven komen. Beschikbaar in Forms Management UI, de Adaptive Forms Editor en de Universal Editor, begrijpt het uw intentie en bouwt precies wat u zoekt.

## Aan de slag: gewoon erover praten

De AI Assistant werkt als een gesprek met een goed geïnformeerde collega. In plaats van complexe menu&#39;s en instellingen te leren, beschrijft u gewoon wat u wilt maken.

### Snel starten

Ga snel aan de slag door onze inleidende video te bekijken:

>[!VIDEO](https://video.tv.adobe.com/v/3463164/)

### De AI-assistent openen

U hebt toegang tot de AI Assistant vanaf drie verschillende locaties in AEM Forms:

1. **het Beheer UI van Forms**
   - Ga naar: Adobe Experience Manager > Forms > Forms &amp; Documents
   - Zoeken naar het AI-assistent-pictogram links van de interface
   - Klik op het pictogram om het deelvenster AI Assistant te openen

   ![ AI Hulp pictogram* ](/help/edge/docs/forms/assets/forms-manager.gif){width="50%"}

2. **de AanpassingsRedacteur van Forms**
   - Ga naar: Adobe Experience Manager > Forms > Forms &amp; Documents
   - Een formulier selecteren en openen om te bewerken
   - Klik op het pictogram AI Assistant in de editor-interface

   ![ AI Hulp pictogram* ](/help/edge/docs/forms/assets/adaptive-forms-editor.gif){width="75%"}

3. **Universele Redacteur**

   - Ga naar: Adobe Experience Manager > Forms > Forms &amp; Documents
   - Zoeken naar het AI-assistent-pictogram links van de interface
   - Klik op het pictogram AI Assistant in de editor-interface

### Hoe te om te beginnen: Eenvoudige gesprekken

De beste manier om met de AI Medewerker te beginnen is door natuurlijke taal. Hieronder wordt beschreven hoe:

**beschrijft enkel wat u nodig hebt:**

- &quot;Een contactformulier voor mijn website maken&quot;
- &quot;Ik heb een feedbackformulier voor klanten nodig met ratingschalen.&quot;
- &quot;Een registratieformulier maken voor mijn aanstaande gebeurtenis&quot;
- &quot;Maak een eenvoudig onderzoek over producttevredenheid&quot;

**voegt details toe aangezien u gaat:**

- &quot;Een contactformulier maken met naam-, e-mail-, telefoon- en berichtvelden&quot;
- &quot;Ik heb een uit meerdere stappen bestaand registratieformulier voor een conferentie nodig&quot;
- &quot;Maak een feedbackformulier voor klanten met 5 sterren beoordelingen en commentaarsecties&quot;

**Verwijzing uw bestaande gebieden:**

- &quot;Maak het e-mailveld vereist&quot; (voor @email)
- &quot;Voeg bevestiging aan het gebied van het telefoonaantal&quot;toe (voor @phoneNumber)
- &quot;Alleen de informatie over de echtgenoot weergeven als getrouwd is geselecteerd&quot; (voor @spouseInfo en @maritalStatus)

### Wat u ook kunt doen

Naast de natuurlijke taal biedt de AI Assistant extra manieren om te werken:

- **uploadt dossiers**: Verbind beelden, PDFs, of de ontwerpen van Figma om AI te tonen wat u plaatst.
- **Snelle bevelen van het Gebruik**: Type `/` om beschikbare kortere weg voor gemeenschappelijke acties te zien
- **Verwijzing specifieke gebieden**: Gebruik `@fieldName` om bestaande vormgebieden (b.v., `@firstName`, `@emailAddress`) te wijzigen

## Wat u kunt maken: voorbeelden die werken

Hier zijn echte voorbeelden van wat u met eenvoudige, natuurlijke taal kunt verwezenlijken:

### Een nieuw formulier starten

**Eenvoudige benadering:**

```
"Create a contact form"
```

**meer gedetailleerde benadering:**

```
"Create a professional contact form for a law firm with fields for name, email, phone, case type, and message. Make it mobile-friendly."
```

**met ontwerpverwijzing:**

```
"Create a contact form based on the attached design mockup. Include all the fields shown in the layout."
```

### Formulierelementen toevoegen

**Basistoevoegingen:**

```
"Add a section for personal information"
"Include a file upload for resume"
"Add a dropdown for country selection"
```

**Gedetailleerde specificaties:**

```
"Add a personal information panel with fields for full name, date of birth, phone number, and email address"
"Include a secure file upload component for documents, limited to PDF files under 5MB"
"Add a country dropdown with options for USA, Canada, UK, and Germany"
```

### Dynamisch gedrag maken

**Eenvoudige logica:**

```
"Show additional fields when 'Other' is selected"
"Make the email field required"
"Calculate the total automatically"
```

**Complexe bedrijfsregels:**

```
"Show the spouse information fields only when marital status is set to 'Married'"
"Calculate the total cost by multiplying quantity and price, then add 10% tax"
"Enable the submit button only when all required fields are completed and terms are accepted"
```

### Formulierindeling en -ontwerp

**de veranderingen van de Lay-out:**

```
"Make this a multi-step form"
"Organize fields in two columns"
"Convert to an accordion layout"
```

**de verbeteringen van het Ontwerp:**

```
"Create a wizard-style form with 3 steps: personal info, preferences, and review"
"Arrange the address fields in a compact two-column layout"
"Update the layout to match the attached wireframe"
```

### Indiening en integratie

**Basisvoorlegging:**

```
"Send form data to our email"
"Save responses to a spreadsheet"
"Redirect to a thank you page"
```

**Geavanceerde integratie:**

```
"Send form submissions to hr@company.com and create a case in our CRM system"
"Submit data to our REST API endpoint and trigger the new customer workflow"
"Email responses to the sales team and add the lead to our marketing automation platform"
```

## Werken met bijlagen

Upload bestanden om AI te helpen precies te begrijpen wat u zoekt:

### Ondersteunde bestandstypen

| Bestandstype | Best voor | Voorbeeld |
|-----------|----------|-------------|
| **Beelden** (PNG, JPG, GIF) | Formulierindelingen, UI-modellen, scannen op papieren formulieren | &quot;Een formulier maken dat overeenkomt met deze indeling&quot; |
| **de Dossiers van PDF** | Bestaande formulieren die moeten worden geconverteerd, specificaties | &quot;Dit PDF-formulier converteren naar digitaal&quot; |
| **Dossiers van Figma** | Ontwerpprototypen, richtlijnen voor merken | &quot;Dit formulier maken op basis van mijn figuurontwerp&quot; |
| **Dossiers van het Ontwerp** | Visuele referenties, stijlhulplijnen | &quot;De stijl in dit ontwerp afstemmen&quot; |

### Bijlagen gebruiken

1. **klik het gehechtheidspictogram** in de AI Hulp interface
2. **selecteer uw dossier** van uw apparaat
3. **beschrijf wat u** van het in bijlage dossier van verwijzingen voorziet:
   - &quot;Een formulier maken op basis van deze bijgevoegde PDF&quot;
   - &quot;Een contactformulier maken dat overeenkomt met de indeling in deze afbeelding&quot;
   - &quot;Dit papieren formulier converteren naar een digitale versie&quot;

### Aanbevolen werkwijzen met bijlagen

- **Gebruik duidelijke, kwalitatief hoogstaande beelden** voor betere analyse AI
- **nadruk op één concept per gehechtheid** (lay-out, het stileren, enz.)
- **beschrijf wat u** samen met de gehechtheid wilt
- **houd dossiers onder 10MB** voor optimale verwerking

## Tips voor beste resultaten

### Eenvoudig starten, opbouwen

- Begin met basisverzoeken: &quot;Een contactformulier maken&quot;
- Voeg geleidelijk details toe: &quot;Voeg bevestiging aan het e-mailgebied toe&quot;
- Testen en verfijnen: &quot;Maak het telefoonveld optioneel&quot;

### Indien nodig specifiek zijn

- In plaats van: &quot;Laat het er goed uitzien&quot;
- Probeer: &quot;Gebruik professionele kleuren en schone typografie&quot;

### Natuurlijke taal gebruiken

- In plaats van: &quot;Voeg tekstinvoercomponent toe&quot;
- Probeer: &#39;&#39;Een veld toevoegen voor voornaam&#39;&#39;

### Verwijzing naar bestaande elementen

- Gebruik `@fieldName` voor bestaande velden: &quot;Maak @email vereist&quot;
- Wees specifiek over veldnamen: &quot;Werk het veld @phoneNumber bij&quot;

### Complexe verzoeken onderbreken

- Probeer in plaats van één grote aanvraag meerdere kleinere aanvragen
- Uw formulier stap voor stap samenstellen
- Elke wijziging testen voordat naar de volgende wijziging wordt gegaan

## Help en training voor producten

De AI Assistant kan u ook leren over AEM Forms-functies:

### Stel vragen zoals:

- &quot;Hoe maak ik een formulier met meerdere stappen?&quot;
- &quot;Wat is het verschil tussen deelvensters en secties?&quot;
- &quot;Hoe kan ik e-mailmeldingen instellen?&quot;
- &quot;Wat zijn de beste praktijken voor mobiele vriendschappelijke vormen?&quot;
- &quot;Hoe kan ik thema&#39;s toepassen op mijn formulieren?&quot;

### Hulp vragen bij:

- Concepten en terminologie van AEM Forms
- Stapsgewijze instructies voor complexe functies
- Aanbevolen werkwijzen en aanbevelingen
- Problemen met algemene problemen oplossen

## Verwijzing naar geavanceerde functies

Voor gebruikers die geavanceerde mogelijkheden willen verkennen:

### Snelle opdrachten

Typ `/` om de beschikbare sneltoetsen weer te geven:

| Opdracht | Doel | Voorbeeld |
|---------|---------|---------|
| `/create-form` | Een nieuw formulier starten | `/create-form customer survey` |
| `/add-form` | Formulier toevoegen in Universal Editor | `/add-form contact form` |
| `/update-layout` | De formulierstructuur wijzigen | `/update-layout wizard with 3 steps` |
| `/update-field` | Veldeigenschappen wijzigen | `/update-field @email to be required` |
| `/create-rule` | Dynamisch gedrag toevoegen | `/create-rule show @spouse if married` |
| `/create-panel` | Veldcontainers toevoegen | `/create-panel Personal Information` |
| `/configure-submit` | Formulierverzending instellen | `/configure-submit to email support` |
| `/help` | Hulp vragen | `/help multi-step forms` |

### Veldverwijzingssyntaxis

Gebruik `@fieldName` om te verwijzen naar bestaande velden:

- `@firstName` - veld Voornaam
- `@email` - Veld voor e-mail
- `@phoneNumber` - Veld voor telefoonnummer
- `@dateOfBirth` - Geboortedatum

### Componenttypen

Gebruik deze termen voor de beste resultaten:

- `text input` - Tekstveld met één regel
- `text area` - Tekstveld met meerdere regels
- `dropdown` - Lijst selecteren
- `checkbox` - Eén selectievakje
- `checkbox group` - Meerdere selectievakjes
- `radio group` - Groep keuzerondjes
- `date picker` - Datumselectie
- `file upload` - Bestandsbijlage
- `panel` - Container voor het groeperen van velden

## Problemen oplossen

### Veelvoorkomende problemen en oplossingen

**Medewerker AI antwoordt niet:**

- Controleer uw internetverbinding
- Zorg ervoor dat u zich in een ondersteunde omgeving bevindt
- Het deelvenster AI-assistent sluiten en opnieuw openen

**Onverwachte Resultaten:**

- Probeer uw verzoek specifieker te herformuleren
- Complexe aanvragen onderverdelen in kleinere stappen
- Standaardterminologie voor AEM Forms gebruiken

**het Werken van de Verwijzingen van het Gebied niet:**

- Veldnamen controleren zijn precies zo gespeld als ze worden weergegeven
- `@fieldName` syntaxis gebruiken voor bestaande velden
- Controleer of het veld bestaat voordat u ernaar verwijst

**de Invoer van het Ontwerp Kwesties:**

- Controleren of bestanden duidelijk en goed gestructureerd zijn
- Ondersteunde indelingen gebruiken (PDF, PNG, JPG, Figma)
- Zorg ervoor dat de bestandsgrootte kleiner is dan 10 MB

## Feedback en ondersteuning

Help ons de AI-assistent te verbeteren:

- **verstrekken Terugkoppeling**: Gebruik terugkoppelen knoop in de AI Hulp interface
- **Kwesties van het Rapport**: De steun van Adobe van het contact door officiële kanalen
- **Ervaringen van het Aandeel**: Uw inputhulp maakt de medewerker beter voor iedereen

## Gerelateerde bronnen

[AEM Forms AI Assistant - Promptbibliotheek](help/forms/experience-builder/forms-experience-builder-prompt-examples-library.md)
