---
title: Aan de slag met Forms Experience Builder
description: Leer hoe u met de Forms Experience Builder formulieren met progressieve openbaarmaking kunt maken en beheren voor alle gebruikerstypen
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: 9996bc602ae6169dd1aade622d5dbc5b1addeb54
workflow-type: tm+mt
source-wordcount: '1737'
ht-degree: 0%

---


# Aan de slag met Forms Experience Builder

>[!NOTE]
>
> Het vermogen van de Bouwer van de Ervaring van Forms is beschikbaar onder het **vroege adoptieprogramma**. Als u geïnteresseerd bent, stuurt u een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang tot de functie te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze documentatie wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De eigenschappen, de bevelen, en de voorbeelden kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

Deze uitgebreide handleiding helpt u om aan de slag te gaan met het maken en beheren van formulieren met behulp van conversationele AI-technologie. Of u nu een beginner bent die uw eerste formulier wil maken of een ervaren gebruiker die geavanceerde functies wil gebruiken, u vindt gedetailleerde informatie en praktische voorbeelden om uw reis door de mogelijkheden van Forms Experience Builder te begeleiden.

## Vereisten en Setup

### &#x200B;1. Toegang aanvragen

Als u geen toegang hebt tot de Forms Experience Builder:

1. **Toegang van het Verzoek**: Verzend een e-mail naar [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com) van uw werk e-mail
2. **omvat Informatie**: De naam van de organisatie en projectdetails
3. **wacht op Goedkeuring**: Adobe zal onboarding instructies herzien en verstrekken

### &#x200B;2. Controleer of Forms is ingeschakeld

Alvorens de Bouwer van de Ervaring van Forms te gebruiken, zorg ervoor [ AEM Forms voor uw milieu ](/help/forms/setup-forms-cloud-service.md) wordt toegelaten.


### &#x200B;3. Uw omgeving instellen


* **voor Edge Delivery Services (EDS):**

   * [Installatieomgeving voor Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
   * [Een nieuw formulier maken met de Edge Delivery Forms-sjabloon](/help/edge/docs/forms/universal-editor/create-forms.md)

* **voor op componenten gebaseerde vormen van de Kern:**

   * Ga naar Forms > Forms &amp; Documents op je Adobe Experience Manager-exemplaar
   * [Een nieuwe pagina maken met de sjabloon Core Components](/help/forms/creating-adaptive-form-core-components.md)

## Snel starten

### Ga naar de Forms Experience Builder

**Universele Redacteur**

* De EDS-pagina openen in de Universal Editor
* Zoeken naar het Forms Experience Builder-pictogram in het linkerdeelvenster
* Klik om de conversatie-interface te openen

**de AanpassingsRedacteur van Forms**

* Ga naar: AEM > Forms > Forms &amp; Documents
* Een basisformulier voor componenten maken of openen om te bewerken
* Klik op het pictogram van de Forms Experience Builder op de editor-werkbalk

### Uw eerste formulier

Probeer dit eenvoudige gesprek om te beginnen:

```
👤 You: "Create a simple contact form"
🤖 AI: "I'll create a contact form with name, email, and message fields for you."

👤 You: "Make the email field required"
🤖 AI: "Updated the email field to be required with validation."
```

### Essentiële opdrachten

| Symbool | Doel | Hoe wordt het gebruikt |
|--------|---------|------------|
| `/` | Snelle handelingen en sneltoetsen | Type `/create` voor het maken van formulieren, `/help` voor hulp |
| `@` | Verwijzing naar bestaande formuliervelden | Typ `@fieldName` om specifieke velden te wijzigen (bijvoorbeeld `@email` ) |
| Onbewerkte tekst | Natuurlijk gesprek | Beschrijf wat u wilt: &quot;voeg een vereist gebied van het telefoonaantal toe&quot; |

### Tips voor succes

* **ben specifiek**: &quot;voeg een vereist e-mailgebied met bevestiging&quot;toe werkt beter dan &quot;voeg e-mail toe&quot;
* **Verwijzing bestaande gebieden**: Gebruik `@fieldName` wanneer het wijzigen van vormen
* **Vraag om hulp**: Type `/help` gevolgd door uw vraag
* **herhaalt**: Maak één verandering in een tijd voor beste resultaten


## Manieren om een formulier te maken

### &#x200B;1. Begin met vragen over natuurlijke talen

Beschrijf uw formuliervereisten in natuurlijke taal en de Forms Experience Builder genereert de volledige formulierstructuur:

**Voorbeelden:**

* &quot;Een aanvraagformulier voor een lening maken met persoonlijke gegevens, financiële gegevens en het uploaden van documenten&quot;
* &quot;Maak een feedbackformulier voor klanten met beoordelingen, opmerkingen en productcategorieën&quot;
* &quot;Ik heb een meertrapsgewijs registratieformulier nodig voor een conferentie met betalingsverwerking&quot;

### &#x200B;2. Invoer en Omzetten

Bestaande formulieren en documenten omzetten in moderne, interactieve ervaringen:

**Gesteunde Bronnen:**

* **PDF forms**: Upload statische PDFs om deze in interactieve digitale vormen met bevestigingen om te zetten.
* **Screenshots of Beelden**: Upload foto van papierformulieren om functionele digitale versies te produceren
* **HTML Forms**: De invoer en zet basisWebvormen in verbeterde AEM Forms met geavanceerde eigenschappen om
* **XFA Forms**: Comvert erfenis op XFA-Gebaseerde vormen aan moderne responsieve vormen
* **URLs**: Zet bestaande Webvormen in inheemse AEM Forms met betere UX om

**hoe te om in te voeren:**

1. Klik op het pictogram voor bijlagen in de Forms Experience Builder-interface
2. Upload uw bestand (PDF, afbeelding, Figma-ontwerp, enz.)
3. Beschrijf uw vereisten:
   * &quot;Dit PDF-formulier converteren naar een digitale versie&quot;
   * &quot;Een formulier maken dat overeenkomt met deze schermopnamelay-out
   * &quot;Dit formulier maken op basis van mijn figuurontwerp&quot;

**Gesteunde Types van Dossier:**

* **Beelden** (PNG, JPG, GIF): De lay-outs van de vorm, UI mockups, gescande vormen
* **de Dossiers van PDF**: Bestaande vormen, specificaties, documenten
* **Dossiers van Figma**: De prototypen van het ontwerp, merkrichtlijnen
* **Dossiers van het Ontwerp**: Visuele verwijzingen, stijlgidsen

### Belangrijkste interacties

#### Formulierelementen toevoegen

**Basistoevoegingen:**

```
👤 You: "Add a section for personal information"
🤖 AI: "Added a personal information panel with standard fields"

👤 You: "Include a file upload for resume"
🤖 AI: "Added a secure file upload component for documents"

👤 You: "Add a dropdown for country selection"
🤖 AI: "Added a country dropdown with common options"
```

**Gedetailleerde specificaties:**

```
👤 You: "Add a personal information panel with fields for full name, date of birth, phone number, and email address"
🤖 AI: "Created a personal information panel with all requested fields and appropriate validation"

👤 You: "Include a secure file upload component for documents, limited to PDF files under 5MB"
🤖 AI: "Added a file upload field with PDF restriction and 5MB size limit"

👤 You: "Add a country dropdown with options for USA, Canada, UK, and Germany"
🤖 AI: "Added a country dropdown with the specified options"
```

#### Dynamisch gedrag maken

**Eenvoudige logica:**

```
👤 You: "Show additional fields when 'Other' is selected"
🤖 AI: "Created a conditional rule that shows additional fields when 'Other' is chosen"

👤 You: "Make the email field required"
🤖 AI: "Updated the email field to be required with validation"

👤 You: "Calculate the total automatically"
🤖 AI: "Added calculation logic to automatically compute totals"
```

**Complexe bedrijfsregels:**

```
👤 You: "Show the spouse information fields only when marital status is set to 'Married'"
🤖 AI: "Created a conditional rule that displays spouse fields based on marital status"

👤 You: "Calculate the total cost by multiplying quantity and price, then add 10% tax"
🤖 AI: "Added calculation logic with quantity, price, and tax computation"

👤 You: "Enable the submit button only when all required fields are completed and terms are accepted"
🤖 AI: "Created validation logic that enables submission only when all conditions are met"
```

#### Formulierindeling en -ontwerp

**de veranderingen van de Lay-out:**

```
👤 You: "Make this a multi-step form"
🤖 AI: "Converted the form to a progressive layout with navigation"

👤 You: "Organize fields in two columns"
🤖 AI: "Updated the layout to display fields in a two-column arrangement"

👤 You: "Convert to an accordion layout"
🤖 AI: "Transformed the form to use accordion-style sections"
```

**de verbeteringen van het Ontwerp:**

```
👤 You: "Create a wizard-style form with 3 steps: personal info, preferences, and review"
🤖 AI: "Created a wizard form with three distinct steps and navigation"

👤 You: "Arrange the address fields in a compact two-column layout"
🤖 AI: "Organized address fields in a compact two-column format"

👤 You: "Update the layout to match the attached wireframe"
🤖 AI: "Modified the layout to match the provided design reference"
```

### Integratie-instelling

De Forms Experience Builder kan verschillende verzendeindpunten configureren om uw formulieren te verbinden met externe systemen en services:

| Type integratie | Opdracht Instellen | Hoofdletters gebruiken |
|------------------|---------------|----------|
| **E-mail** | &quot;Formulier verzenden naar e-mail&quot; | Meldingen en bevestigingen voor het indienen van formulieren |
| **REST API** | &quot;Verzenden naar REST-eindpunt&quot; | Aangepaste toepassingen en systemen van derden |
| **Opslag van de Wolk** | &quot;Opslaan in Azure/SharePoint&quot; | Documentopslag en bestandsbeheer |
| **Workflow** | &quot;Verbinding maken met Power Automate&quot; | Automatisering en goedkeuring van bedrijfsprocessen |
| **Marketing** | &quot;Integreren met Marketo&quot; | Beheer van leads en automatisering van marketing |

**Geavanceerde integratievoorbeelden:**

```
👤 You: "Send form submissions to hr@company.com and create a case in our CRM system"
🤖 AI: "Configured email submission and CRM integration"

👤 You: "Submit data to our REST API endpoint and trigger the new customer workflow"
🤖 AI: "Set up REST API submission with workflow triggers"

👤 You: "Email responses to the sales team and add the lead to our marketing automation platform"
🤖 AI: "Configured multi-channel submission with email and marketing automation"
```





## Geavanceerde formulierbewerkingen


### Complexe regel maken

Maak geavanceerde validatie- en bedrijfslogica die reageert op gebruikersinteracties en zorgt voor gegevensintegriteit:

```
👤 You: "Show the address section only if the user selects 'Ship to different address'"
🤖 AI: "Created a conditional rule that shows/hides the address panel based on checkbox selection"
```

### Meerdere stappen voor het maken van formulieren

```
👤 You: "Create a progressive form with 3 steps: personal info, preferences, confirmation"
🤖 AI: "Created a progressive form with navigation between steps and validation at each stage"
```

### Geavanceerde veldtypen

* Het uploaden van bestanden met validatie- en groottebeperkingen voor documentbeheer
* Datumkiezers met beperkingen en bedrijfsregels voor het plannen
* Vervolgkeuzelijsten met dynamische opties die worden gewijzigd op basis van gebruikersselecties
* Keuzerondjes met voorwaardelijke logica voor complexe beslissingsstructuren


### PDF naar formulier converteren

```
👤 You: "Convert this PDF into an interactive form"
🤖 AI: "Analyzed the PDF and created a form with appropriate field types and validation"
```

### URL naar formulierconversie

```
👤 You: "Create a form from this website"
🤖 AI: "Extracted form elements and created a native AEM Form with enhanced functionality"
```

### Prestatieanalyse

```
👤 You: "Analyze this form's conversion performance"
🤖 AI: "Provided insights on form effectiveness and suggested optimizations"
```

### Geavanceerde aanpassingen

#### Aangepaste validatieregels

* Veldafhankelijkheden die dynamisch formuliergedrag maken op basis van gebruikersinvoer
* Complexe voorwaardelijke logica die de formulierervaring aanpast aan de behoeften van de gebruiker
* Aangepaste foutberichten die gebruikers duidelijke aanwijzingen geven
* Veldoverschrijdende validatie die zorgt voor gegevensconsistentie tussen meerdere invoeren

#### Layout optimaliseren

* Mobiele reacties die ervoor zorgen dat formulieren naadloos werken op alle apparaten
* Compatibiliteit met toegankelijkheid die formulieren bruikbaar maakt voor mensen met een handicap
* Verbeteringen in het visuele ontwerp die de betrokkenheid van de gebruiker en de voltooiingscijfers verbeteren
* Verbeteringen in de gebruikerservaring die wrijving verminderen en de tevredenheid verbeteren

#### Integratieworkflows

* Goedkeuringsprocessen in meerdere stappen die formulierverzendingen routeren via bedrijfsworkflows
* Gegevenstransformatie waarmee formuliergegevens worden geconverteerd naar indelingen die vereist zijn voor externe systemen
* Aangepaste bedrijfslogica die specifieke regels en berekeningen toepast op het indienen van opmerkingen
* Geavanceerde foutafhandeling die een efficiënt herstel van systeemproblemen mogelijk maakt

## Opdrachtverwijzing

### Essentiële opdrachten

| Symbool | Doel | Hoe wordt het gebruikt |
|--------|---------|------------|
| `/` | Snelle handelingen en sneltoetsen | Type `/create` voor het maken van formulieren, `/help` voor hulp |
| `@` | Verwijzing naar bestaande formuliervelden | Typ `@fieldName` om specifieke velden te wijzigen (bijvoorbeeld `@email` ) |
| Onbewerkte tekst | Natuurlijk gesprek | Beschrijf wat u wilt: &quot;voeg een vereist gebied van het telefoonaantal toe&quot; |

### Opdrachten Slash

| Opdracht | Context | Voorbeeldengebruik |
|---------|---------|---------------|
| `/create-form` | Alle omgevingen | `/create-form customer survey` |
| `/add-form` | Universele editor | `/add-form contact form` |
| `/update-layout` | Formuliereditor | `/update-layout wizard with 3 steps` |
| `/update-field` | Formuliereditor | `/update-field @email to be required` |
| `/create-rule` | Formuliereditor | `/create-rule show @spouse if married` |
| `/create-panel` | Formuliereditor | `/create-panel Personal Information` |
| `/configure-submit` | Formuliereditor | `/configure-submit to email support` |
| `/help` | Alle omgevingen | `/help multi-step forms` |

### Veldverwijzingen

Gebruik `@fieldName` om te verwijzen naar bestaande velden:

* `@firstName`, `@lastName` * Naamvelden
* `@email`, `@phoneNumber` * Contactvelden
* `@address` , `@city` , `@zipCode` * Adresvelden
* `@dateOfBirth`, `@startDate` * Datumvelden

### Componenttypen

Gebruik deze termen bij het beschrijven van formulierelementen:

* `text input` * Tekstveld met één regel
* `text area` * Tekstveld met meerdere regels
* `dropdown` * Selecteer een lijst met opties
* `checkbox` * Enkel selectievakje
* `checkbox group` * Meerdere selectievakjes
* `radio group` * Groep keuzerondjes
* `date picker` * Veld voor datumselectie
* `file upload` * Veld bestandsbijlage
* `panel` * Container voor het groeperen van velden

### Integratieopdrachten

| Service | Opdracht Natuurlijk | Vereisten |
|---------|--------------------------|--------------|
| E-mail | &quot;Verzend bijdragen naar [ e-mail ]&quot; | Geldig e-mailadres |
| REST API | &quot;voorleggen aan REST eindpunt [ URL ]&quot; | API-eindpunt en referenties |
| Azure Storage | &quot;Bestanden opslaan in Azure-opslag&quot; | Configuratie van opslagaccount |
| SharePoint | &quot;Opslag in SharePoint [ plaats ]&quot; | Toegang tot SharePoint-site |
| Power Automate | &quot;Trigger Power Automated Flow&quot; | Stroomconfiguratie |
| Marketo | &quot;Voeg leads toe aan Marketo&quot; | Marketo API-referenties |

### Tips

1. **de natuurlijke taal van het Gebruik**: AI begrijpt complexe verzoeken en kan gedetailleerde vereisten interpreteren
2. **ben specifiek**: De gedetailleerde beschrijvingen produceren betere resultaten en nauwkeurigere vormgeneratie
3. **bevestig**: Verfijn vormen door gesprek om de perfecte gebruikerservaring te bereiken
4. **context van de Leverage**: Verwijzing bestaande vormelementen om op te bouwen wat u reeds hebt
5. **Test grondig**: Bevestig alle gebruikersscenario&#39;s om het werk van vormen te verzekeren zoals verwacht

## Help en training voor producten

De Forms Experience Builder kan u ook leren over AEM Forms-functies:

### Stel vragen zoals:

* &quot;Hoe maak ik een formulier met meerdere stappen?&quot;
* &quot;Wat is het verschil tussen deelvensters en secties?&quot;
* &quot;Hoe kan ik e-mailmeldingen instellen?&quot;
* &quot;Wat zijn de beste praktijken voor mobiele vriendschappelijke vormen?&quot;
* &quot;Hoe kan ik thema&#39;s toepassen op mijn formulieren?&quot;

### Hulp vragen bij:

* Concepten en terminologie van AEM Forms
* Stapsgewijze instructies voor complexe functies
* Aanbevolen werkwijzen en aanbevelingen
* Problemen met algemene problemen oplossen

## Aanbevolen procedures

### Formulierontwerp

* **houd het eenvoudig**: Begin met essentiële gebieden en voeg ingewikkeldheid slechts toe wanneer noodzakelijk om overweldigende gebruikers te vermijden
* **Gebruik duidelijke etiketten**: Maak gebiedsdoeleinden duidelijk met beschrijvende etiketten die gebruikers door de vorm begeleiden
* **verstrekt hulptekst**: De gebruikers van de gids door complexe gebieden met contextuele hulp en voorbeelden
* **Test grondig**: Valideer alle gebruikerspaden om ervoor te zorgen dat de formulieren in alle scenario&#39;s correct werken

### Gebruikerservaring

* **Progressieve mededeling**: toon relevante die gebieden op context worden gebaseerd om cognitieve lading te verminderen en voltooiingstarieven te verbeteren
* **Duidelijke navigatie**: De gebruikers van de hulp begrijpen waar zij in de vorm zijn en welke stappen blijven
* **Responsief ontwerp**: Zorg het werk van vormen op alle apparaten en schermgrootte voor maximumtoegankelijkheid ervoor
* **Toegankelijkheid**: volg de richtlijnen van WCAG om vormen bruikbaar te maken door mensen met handicaps

### Prestaties

* **optimaliseer gebiedstelling**: slechts om noodzakelijke informatie vragen om vormbeëindiging te verminderen en voltooiingstarieven te verbeteren
* **Gebruik aangewezen bevestiging**: Vermijd fouten alvorens voorlegging om directe te verstrekken terugkoppel en begeleiding
* **de voltooiingspercentages van de Test**: De doeltreffendheid van de monitor en verbetert vorm door analyses en gebruiker terugkoppelen
* **Regelmatige updates**: Houd formulieren huidig met bedrijfsbehoeften en gebruikersverwachtingen voor optimale prestaties

### Brand Consistency

* **creeer merkmalplaatjes**: Bereid branded vormmalplaatjes met de kleuren, de doopvonten van uw organisatie, en het stileren voor de aanvang van vormverwezenlijking voor
* **bepaalt stijlnormen**: Vestig verenigbare knoopstijlen, gebiedslay-outs, en het uit elkaar plaatsen van richtlijnen die in herinneringen kunnen worden van verwijzingen voorzien
* **de merkactiva van het Gebruik**: Bereid logo&#39;s, kleurencodes, en merkrichtlijnen voor gemakkelijke verwijzing wanneer het creëren van vormen voor
* **bibliotheek van het Malplaatje**: Bouw een inzameling van brandde vormmalplaatjes voor gemeenschappelijke gebruiksgevallen (contact, registratie, terugkoppelt)
* **de herinneringen van de Stijl**: Omvat brand-specifieke instructies: &quot;bedrijfblauw van het gebruik (#1234AB) voor knopen en collectieve doopvont Helvetica&quot;

### Tips voor beste resultaten

**Begin Eenvoudig, bouwt omhoog**

* Begin met basisverzoeken: &quot;Een contactformulier maken&quot;
* Voeg geleidelijk details toe: &quot;Voeg bevestiging aan het e-mailgebied toe&quot;
* Testen en verfijnen: &quot;Maak het telefoonveld optioneel&quot;

**ben specifiek wanneer nodig**

* In plaats van: &quot;Laat het er goed uitzien&quot;
* Probeer: &quot;Gebruik professionele kleuren en schone typografie&quot;

**Natuurlijke Taal van het Gebruik**

* In plaats van: &quot;Voeg tekstinvoercomponent toe&quot;
* Probeer: &#39;&#39;Een veld toevoegen voor voornaam&#39;&#39;

**Verwijzing Bestaande Elementen**

* Gebruik `@fieldName` voor bestaande velden: &quot;Maak @email vereist&quot;
* Wees specifiek over veldnamen: &quot;Werk het veld @phoneNumber bij&quot;

**onderbreking Complexe Verzoeken**

* Probeer in plaats van één grote aanvraag meerdere kleinere aanvragen
* Uw formulier stap voor stap samenstellen
* Elke wijziging testen voordat naar de volgende wijziging wordt gegaan

## Problemen oplossen

| Probleem | Snel repareren |
|-------|-----------|
| **Interface niet ladend** | Browser vernieuwen, internetverbinding controleren |
| **Bevelen het werken niet** | Probeer `/help` of gebruik in plaats daarvan een natuurlijke taal |
| **@fieldName niet herkend** | Spelling controleren, controleren of veld bestaat |
| **uploadt van het Dossier ontbreekt** | PDF/JPG/PNG gebruiken bij 10 MB |
| **de blik van de Vorm verkeerd** | Meer specifiek: &quot;Maak het mobiel&quot; |
| **de Integratie ontbreekt** | API-referenties en -machtigingen controleren |

**nog hulp nodig?** Typ `/help` gevolgd door uw specifieke vraag of neem contact op met de systeembeheerder.

Voor extra steun, verwijs naar de belangrijkste [ Snelle Bibliotheek van de Bouwer van de Ervaring van Forms ](ai-assistant-prompt-library.md) of contacteer uw systeembeheerder voor technische bijstand.
