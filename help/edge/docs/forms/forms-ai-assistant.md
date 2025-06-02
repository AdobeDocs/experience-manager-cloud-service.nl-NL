---
title: AI Assistant voor AEM Forms (Forms Experience Builder)
description: Krachtige formulieren sneller maken met formulierfragmenten
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: 67416999d068af6350748d610e7c1c7b1d991bc4
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 0%

---

# AI Assistant voor AEM Forms (Forms Experience Builder)

>[!NOTE]
>
>
> De AI Assistant voor AEM Forms (Forms Experience Builder)-functionaliteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Als u geïnteresseerd bent, stuurt u een e-mail van uw werkadres naar mailto:aem-forms-ea@adobe.com om toegang tot de functie te vragen.


De AI Assistant voor AEM Forms (Forms Experience Builder) verbetert uw ontwerpervaring door veelvoorkomende taken voor het maken van formulieren te stroomlijnen met instructies voor natuurlijke talen. Met Forms Manager, de Adaptive Forms Editor en de Universal Editor kunt u slimmer en sneller bouwen door zowel ontwerp- als configuratiehandelingen te ondersteunen. Deze handleiding helpt u aan de slag te gaan en optimaal gebruik te maken van de mogelijkheden die deze biedt.

## Aan de slag

Alvorens u diep duikt, behandelen wij de grondbeginselen van de toegang tot van en het in wisselwerking staan met de Medewerker AI.

### De AI-assistent openen

U hebt toegang tot de AI Assistant vanaf drie verschillende locaties in AEM Forms:

1. **de Manager van Forms**
   - Ga naar: Adobe Experience Manager > Forms > Forms &amp; Documents
   - Zoeken naar het AI-assistent-pictogram links van de interface
   - Klik op het pictogram om het deelvenster AI Assistant te openen

   ![ AI Hulp pictogram* ](/help/edge/docs/forms/assets/forms-manager.gif)

2. **de AanpassingsRedacteur van Forms**
   - Ga naar: Adobe Experience Manager > Forms > Forms &amp; Documents
   - Een formulier selecteren en openen om te bewerken
   - Klik op het pictogram AI Assistant in de editor-interface

   ![ AI Hulp pictogram* ](/help/edge/docs/forms/assets/adaptive-forms-editor.gif)

3. **Universele Redacteur**

   - Ga naar: Adobe Experience Manager > Forms > Forms &amp; Documents
   - Zoeken naar het AI-assistent-pictogram links van de interface
   - Klik op het pictogram AI Assistant in de editor-interface

De AI Assistant past zijn functionaliteit aan op basis van uw huidige locatie en taak en biedt relevante ondersteuning voor elke context.

### Hoe reageert u op:

- Typ gewoon uw verzoek in de natuurlijke taal.
- Gebruik `/` om een lijst met beschikbare opdrachten of snelle handelingen weer te geven.
- Verwijs naar specifieke formuliervelden met `@fieldName` (bijvoorbeeld `@firstName` , `@emailAddress` ) als u wilt dat de assistent dat veld configureert of bijwerkt.


### Snel starten

Ga snel aan de slag door onze inleidende video te bekijken:

>[!VIDEO](https://video.tv.adobe.com/v/3463164/)


Deze video behandelt het lanceren van de medewerker in alle milieu&#39;s, basisinteractie, en een overzicht van zijn mogelijkheden.

## Referentie AI-assistent-opdracht

| Opdracht | Beschrijving | Doel | Gebruikscontext | Voorbeelden | Belangrijkste kenmerken |
|---------|-------------|---------|---------------|----------|--------------|
| /create-form | Een nieuw formulier starten in Forms Manager of Forms Editor | Hiermee wordt het maken van een geheel nieuw formulier gestart | Forms Manager, Adaptive Forms Editor | /create-form klant feedback survey | Hier vindt u opties voor de formulierstructuur en het maken van het formulier |
| /add-form | Een nieuw formulier toevoegen in de Universal Editor | Hiermee wordt een nieuw formulierblok of een nieuwe formuliercomponent toegevoegd in de universele editor | Universele editor voor Edge Delivery Services | /add-form contactformulier met naam en e-mail | Hiermee voegt u formulierblokken in, werkt u met blokbewerking |
| /update-layout | De indeling van een formulier wijzigen in accordeon, op tabbladen gebaseerd, wizards of een responsief ontwerp voor één pagina | Hiermee wijzigt u de algemene structuurindeling en het navigatiepatroon | Alle bewerkingsomgevingen | /update-layout, wizard met 3 stappen | Accordeon, tabbladen, wizard, responsieve opties voor één pagina |
| /update-field | Eigenschappen en configuratie van bestaande formuliervelden wijzigen | Hiermee wijzigt u veldkenmerken zoals labels, validatie, opmaak, gedrag | Alle bewerkingsomgevingen | /update-field @email vereist voor validatie | Labels, validatieregels, veldtypen, standaardwaarden, zichtbaarheid |
| /create-rule | Dynamisch gedrag en voorwaardelijke logica voor formulieren maken | Implementeert bedrijfslogica, berekeningen, voorwaardelijke interactie | Alle bewerkingsomgevingen | /create-rule show @spouseName if @maritalStatus equals &quot;Gehuwd&quot; | Voorwaardelijke zichtbaarheid, berekeningen, validatie, waarde instellen |
| /create-panel | Een nieuw deelvenster maken (container voor het groeperen van gerelateerde velden) | Hiermee voegt u structurele containers toe om formuliervelden logisch te ordenen | Alle bewerkingsomgevingen | /create-panel Persoonlijke Informatie met naam, e-mail, telefoon | Veldgroepering, titels, layoutopties, inklapbare secties |
| /add-panel | Een afbeelding converteren naar een formuliervenster in de Universal Editor | Gebruikt AI om geüploade afbeeldingen te analyseren en om te zetten in gestructureerde formulierdeelvensters | Universele editor | /add-panel van geüploade formulierafbeelding | Afbeeldingsherkenning, visueel-naar-functionele conversie, behoud van layout |
| /configure-submit | Formulierverzendacties en gegevensverwerking instellen | Hiermee definieert u wat er gebeurt wanneer gebruikers het ingevulde formulier verzenden | Alle bewerkingsomgevingen | /configure-submit om e-mail naar te verzenden `support@company.com` | E-mail, REST API, workflows, spreadsheets, databases, Power Automated |
| /help | Toegang tot bijstand en documentatie binnen de AI Assistant | Biedt contextuele hulp, begeleiding en antwoorden over AEM Forms | Alle bewerkingsomgevingen | /help hoe maak ik formulieren die uit meerdere stappen bestaan? | Functieuitleg, handleidingen, aanbevolen procedures, problemen oplossen |

### Opdrachtcategorieën

| Categorie | Opdrachten | Primaire gebruikskwesties |
|----------|----------|-------------------|
| Formulier maken | /create-form, /add-form | Nieuwe formulieren starten, formulierblokken toevoegen |
| Structuur en lay-out | /update-layout, /create-panel, /add-panel | Formulierstructuur ordenen, visueel ontwerp |
| Veldbeheer | /update-field | Afzonderlijke formulierelementen configureren |
| Logica en regels | /create-rule | Dynamisch gedrag en validatie toevoegen |
| Indiening | /configure-submit | Gegevensverwerking en workflows instellen |
| Ondersteuning | /help | Hulp en documentatie opvragen |

### Syntaxisrichtlijnen

| Element | Indeling | Voorbeeld | Notities |
|---------|--------|---------|-------|
| Opdrachten | /command-name | /create-form | Altijd beginnen met slash |
| Veldverwijzingen | @fieldName | @email, @firstName | @-symbool gebruiken voor bestaande velden |
| Natuurlijke taal | Command + beschrijving | /create-rule show field if condition | Opdrachten combineren met beschrijvende tekst |
| Meerdere handelingen | Afzonderlijke opdrachten | /create-panel then /update-layout | Eén opdracht tegelijk toepassen |


### Omgevingsspecifieke kenmerken

| Omgeving | Beschikbare opdrachten | Speciale functies |
|-------------|-------------------|------------------|
| Forms Manager | /create-form, /help | Creatie en beheer op formulierniveau |
| Adaptieve Forms Editor en Universal Editor | Alle opdrachten | Volledige functieset, gedetailleerde configuratie |



### Veldverwijzingssyntaxis (contextuele elementen)

Gebruik `@fieldName` om te verwijzen naar bestaande velden:

- `@firstName` - veld Voornaam
- `@email` - Veld voor e-mail
- `@phoneNumber` - Veld voor telefoonnummer
- `@dateOfBirth` - Geboortedatum

### Componenttypen

In deze lijst worden algemene componenttypen besproken. De AI kan variaties of meer gespecialiseerde typen herkennen, maar het gebruik van deze precieze termen levert de beste resultaten op:

- `text input` - Tekstveld met één regel
- `text area` - Tekstveld met meerdere regels
- `dropdown` - Lijst selecteren
- `checkbox` - Eén selectievakje
- `checkbox group` - Meerdere selectievakjes
- `radio group` - Groep keuzerondjes
- `date picker` - Datumselectie
- `file upload` - Bestandsbijlage
- `panel` - Container voor het groeperen van velden


## Kernmogelijkheden en uitgebreide snelle voorbeelden

De AI-assistent begrijpt een breed scala aan opdrachten. Hier zijn een paar voorbeelden om zijn macht te illustreren. Denk eraan exacte termen te gebruiken voor componenten zoals &#39;deelvenster&#39;, &#39;tekstinvoer&#39;, &#39;selectievakje&#39; enzovoort.

| Functiecategorie | Beschrijving | Voorbeeld vragen |
| ------------------------- | --------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **de Making van de Vorm** | Start een nieuw formulier helemaal opnieuw of op basis van een beschrijving. | `Create a new form titled 'Employee Onboarding'.` <br> `Generate a customer feedback form with fields for name, email, rating (1-5 stars), and comments.` <br> `Start a simple contact form with name, email, and message fields.` <br> `Design a multi-page registration form for an event.` |
| **het Ontwerp van de Invoer** | Zet een bestaand ontwerp (image, Figma, PDF) om in een AEM-formulier. | `Import the form design from this uploaded PDF file.` <br> `Convert the uploaded Figma design into an adaptive form, focusing on the 'User Profile' frame.` <br> `Use this JPEG image of our old paper form to create a new digital version.` <br> `Create a form based on the layout of the attached PNG.` |
| **Toevoegend Componenten &amp; Comités** | Voeg diverse formuliervelden en structuurcontainers (deelvensters) toe. | `Add a text input field for 'First Name'.` <br> `Add a 'Personal Details' panel with fields for full name, date of birth, and phone number.` <br> `Insert a checkbox group for 'Interests' with options: Technology, Sports, Music.` <br> `Add a file upload component for 'Resume'.` <br> `Create a repeatable panel named 'WorkExperience' with fields for company, title, and dates.` |
| **Aanpassingen van de Lay-out** | De structuur en weergave van de indeling van het formulier wijzigen. | `Change the 'Personal Details' panel to a two-column layout.` <br> `Set the overall form layout to a wizard (multi-step) navigation.` <br> `Make the header section span the full width of the form.` <br> `Adjust the spacing between fields in the 'Address' panel to be compact.` <br> `Align all field labels to the left.` |
| **de Creatie van de Regel &amp; Logica** | Voer dynamisch gedrag, berekeningen, en voorwaardelijk zicht uit. | `Make the 'Spouse Name' field visible only if 'Marital Status' is selected as 'Married'.` <br> `Calculate the 'Total Amount' by multiplying @quantity and @price.` <br> `Enable the submit button only when the @termsAndConditions checkbox is checked.` <br> `Set the value of @countryCode to '+1' if @country is 'United States'.` <br> `If @age is less than 18, show a message 'Must be 18 or older'.` |
| **Update van de Eigenschappen van het Gebied** | Kenmerken van specifieke formuliervelden wijzigen, zoals labels, plaatsaanduidingen, enz. | `Change the label of @email to 'Primary Email Address'.` <br> `Set the @comment field to be a multi-line text area.` <br> `Make the @phoneNumber field mandatory.` <br> `Add placeholder text 'Enter your ZIP code' to the @zipCode field.` <br> `Change the @country field to a dropdown and populate it with: USA, Canada, UK, Germany.` <br> `Update the help description for @password to 'Must include an uppercase letter, a number, and be at least 8 characters long.'` <br> `Set the maximum length of the @username field to 15 characters.` <br> `Configure the @dateOfBirth field to use a date picker.` |
| **legt Acties** voor | Bepaal wat er gebeurt wanneer een gebruiker het formulier verzendt. | `Configure the form to submit data to the REST endpoint /api/v2/application-submit.` <br> `Set up an email submission to hr@example.com and sales@example.com on successful submission.` <br> `Trigger an AEM workflow named 'NewLeadProcessing' when this form is submitted.` <br> `On submit, redirect the user to a thank you page at /content/thankyou.html.` |
| **Thema** | Bestaande AEM Forms-thema&#39;s toepassen om uw formulier op te maken. | `Apply the 'Modern Business' theme to this form.` <br> `Switch to the 'Accessible Dark' theme.` <br> `Revert to the default canvas theme.` |
| **Navigatie &amp; Structuur** | Navigatie-elementen toevoegen of delen van het formulier opnieuw ordenen. | `Add a 'Next' button to the current panel and a 'Previous' button to the next panel.` <br> `Create a Table of Contents based on the form's panels.` <br> `Move the 'Address' panel to be before the 'Contact Information' panel.` |
| **Bevestiging** | Stel specifieke validatieregels in voor velden. | `Set a regex pattern for the @employeeID field to be 'EMP\d{5}'.` <br> `Ensure the @age field only accepts numeric values between 18 and 99.` <br> `Validate the @email field to ensure it is a valid email format.` |
| **Plan van het Overzicht** (Universele Redacteur) | Bekijk de voorgestelde wijzigingen van de assistent voor de uitvoering. | `Add a contact form with fields for name, email, subject, and message.` (De medewerker zal een plan van componenten en eigenschappen tonen het zal creëren, dan klikt u &quot;van toepassing zijn&quot;). |

## Beste praktijken voor Optimale Resultaten

Houd rekening met de volgende tips als u de AI Assistant optimaal wilt benutten:

- **Eenvoudig Begin, bouwt Stapsgewijs:** Begin met kleinere, specifieke bevelen (bijvoorbeeld, &quot;voeg een tekstinput voor &quot;Voornaam&quot;toe&quot;) eerder dan overdreven complexe multi-step verzoeken aanvankelijk.
- **de Terminologie van AEM Forms van het Gebruik:** zet termijnen zoals &quot;paneel,&quot;het gebied van de tekstinput,&quot;checkbox groep,&quot;actie,&quot;regel,&quot;enz. in werking, voor beter begrip door de medewerker.
- **De Gebieden van de Verwijzing duidelijk:** wanneer het vormen van bestaande gebieden, gebruik de `@fieldName` aantekening (b.v., `Make @firstName mandatory`).
- **Plan van het Overzicht** herzien altijd zorgvuldig plannen voor veranderingen die door de medewerker in de Universele Redacteur worden voorgesteld alvorens &quot;van toepassing te klikken.&quot;
- **bevestigt manueel:** nadat de medewerker veranderingen aanbrengt, voorproef en test altijd uw vorm om ervoor te zorgen het zich gedraagt en kijkt zoals verwacht. AI is een krachtig hulpmiddel, maar de uiteindelijke validatie is van wezenlijk belang.
- **herhaalt en verfijnen:** als de eerste herinnering niet het nauwkeurige resultaat oplevert, probeer het rephrasing of het breken van het verzoek in kleinere stappen.
- **verstrek Terugkoppeling:** gebruik ingebouwde terugkoppel mechanisme om de medewerker te helpen leren en verbeteren (zie &quot;Terugkoppeling &amp; de sectie van de Steun&quot;).

## Help bij het product met de AI Assistant

De AI-assistent voor AEM Forms is niet alleen bedoeld voor gebouwen, maar kan u ook helpen bij het leren, begrijpen en gebruiken van verschillende functies van AEM Forms.

### Ondersteunde Help-onderwerpen

U kunt de hulpvragen als stellen:

- &quot;Hoe maak ik een geheel nieuw adaptief formulier?&quot;
- &quot;Wat is een panel in Adaptive Forms en hoe wordt het gebruikt?&quot;
- &quot;Uitleggen hoe u een thema op een formulier kunt toepassen.&quot;
- &quot;Welke indelingstypen worden ondersteund voor formulieren en deelvensters?&quot;
- &quot;Hoe kan ik verschillende verzendhandelingen configureren, zoals het verzenden van een e-mail?&quot;
- &quot;Kunt u mij begeleiden bij het gebruik van een Figma-ontwerp om een formulier te maken?&quot;
- &quot;Wat is de beste manier om een formulier met meerdere stappen te maken?&quot;

### Hoe om hulp te vragen:

1. Open de AI Assistant in Forms Manager of de Adaptive Forms Editor.
2. Typ uw vraag in natuurlijke taal (bijvoorbeeld &quot;Hoe voeg ik een herhaalbaar paneel toe?&quot;).
3. De assistent reageert met:
   - Stapsgewijze instructies.
   - Uitleg van AEM Forms-concepten.
   - Koppelingen naar relevante documentatie van Adobe Experience League, indien van toepassing.

### Tips voor betere Help:

- **ben specifiek:** stel één duidelijke vraag tegelijkertijd.
- **Trefwoorden van het Gebruik:** omvat sleutelwoorden relevant voor de eigenschappen van AEM Forms of elementen UI (b.v., &quot;adaptieve vormredacteur,&quot;regelredacteur,&quot;thema&quot;).
- **herhaal indien nodig:** als de medewerker niet de gewenste informatie begrijpt of verstrekt, probeer vereenvoudigend uw vraag of gebruikend verschillende termijnen.


## Veelvoorkomende problemen oplossen

- **Medewerker antwoordt niet:**
   - Zorg ervoor dat u actief werkt binnen een ondersteunde omgeving (Forms Manager, Adaptive Forms Editor of Universal Editor).
   - Controleer uw internetverbinding.
   - Sluit het deelvenster AI-assistent en open het opnieuw.

- **Onnauwkeurige of Onverwachte Reacties:**
   - Herhaal uw verzoek om specifieker of eenvoudiger te zijn.
   - Verdeel een complex verzoek in kleinere, individuele bevelen.
   - Zorg ervoor dat u de standaardterminologie van AEM Forms gebruikt.

- **de Kwesties van de Invoer van het Ontwerp (PDF/Figma/Beeld):**
   - Controleer of het ontwerpbestand duidelijk, goed gestructureerd en leesbaar is.
   - Zorg ervoor dat de bestandsindeling wordt ondersteund (PDF, Figma-koppeling, gangbare afbeeldingstypen, zoals PNG, JPG).
   - Voor Figma, zorg ervoor het kader u zich richt duidelijk wordt bepaald en toegankelijk is.

- **Gebied `@fieldName` niet erkend:**
   - Controleer de exacte naam van het veld in het formulier. Veldnamen zijn hoofdlettergevoelig en moeten exact overeenkomen.
   - Zorg ervoor dat het veld al bestaat als u probeert het te wijzigen.


## Feedback en ondersteuning

Uw input is van onschatbare waarde voor de voortdurende verbetering van AI Medewerker.

- **verstrek Terugkoppeling:** gebruik het ingebouwde **&quot;verstrekken Terugkoppeling&quot;bevel of knoop** binnen de AI Hulp interface om uw ervaringen te delen, kwesties te melden, of verhogingen voor te stellen. (U kunt bijvoorbeeld `/feedback` typen of op een feedbackpictogram zoeken).
- **Officiële Steun:** voor kritieke kwesties of verdere hulp, te bereiken gelieve door de officiële de steunkanalen van Adobe of de aangewezen steuncontacten van uw organisatie te bereiken.


## Gerelateerde inhoud

[AEM Forms AI Assistant - Promptbibliotheek](/help/edge/docs/forms/ai-assistant-prompt-library.md)
