---
title: Aan de slag met Forms Experience Builder
description: Leer hoe u met de Forms Experience Builder formulieren met progressieve openbaarmaking kunt maken en beheren voor alle gebruikerstypen
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: tm+mt
source-wordcount: '2013'
ht-degree: 0%

---


# Aan de slag met Forms Experience Builder

>[!NOTE]
>
> Het vermogen van de Bouwer van de Ervaring van Forms is beschikbaar onder het **Vroege programma van de Toegang (EA)**. Als u geïnteresseerd bent, stuurt u een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang tot de functie te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze documentatie wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De eigenschappen, de bevelen, en de voorbeelden kunnen veranderen aangezien de Bouwer van de Ervaring van Forms tijdens het Vroege programma van de Toegang blijft evolueren.

Deze uitgebreide handleiding helpt u om aan de slag te gaan met het maken en beheren van formulieren met behulp van conversationele AI-technologie. Of u nu een beginner bent die uw eerste formulier wil maken of een ervaren gebruiker die geavanceerde functies wil gebruiken, u vindt gedetailleerde informatie en praktische voorbeelden om uw reis door de mogelijkheden van Forms Experience Builder te begeleiden.

## Vereisten en Setup

### &#x200B;1. Toegang aanvragen

De Forms Experience Builder is momenteel beschikbaar als onderdeel van het programma Early Access (EA). Om deel te nemen en toegang te krijgen, zult u de volgende informatie nodig hebben:

**Vereiste Informatie**

- **identiteitskaart van de Organisatie IMS**: Uw organisatie van Adobe herkenningsteken
- **identiteitskaart van het Programma**: Uw specifiek programma herkenningsteken binnen Adobe Experience Cloud
- **Details van het Project**: Chronologie, werkingsgebied, en voorgenomen gebruiksgevallen
- **Officiële E-mail van het Werk**: Verwante met de rekening van Adobe van uw organisatie

**hoe te identiteitskaart van de Organisatie IMS en identiteitskaart van het Programma verkrijgen**

Ga voor gedetailleerde stappen naar de locatie van uw IMS-organisatie-id en programma-id naar:

- [Adobe Experience Cloud Organization Setup Guide](/help/onboarding/cloud-manager-introduction.md)
- [Programma- en milieubeheer](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

**Toegang van het Verzoek**

1. Verzamel uw IMS-organisatie-id en programma-id met de bovenstaande hulplijnen
2. Verzend een e-mail naar [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com) verzoekend toegang
3. Opnemen in uw verzoek:
   - Naam van organisatie en IMS-organisatie-id
   - Programma-id
   - Tijdlijn en bereik van project
   - Beoogde gebruiksgevallen en bedrijfsdoelstellingen

>[!IMPORTANT]
>
> **Beperkt Programma van de Beschikbaarheid**: De toegang tot de Bouwer van de Ervaring van Forms is onderworpen aan goedkeuring van interne belanghebbenden. Adobe zal uw verzoek beoordelen op basis van de programmacapaciteit en de aanpassing aan de criteria voor vroege toegang. Goedkeuring is niet gegarandeerd en is afhankelijk van de beschikbaarheid van het huidige programma.

### &#x200B;2. Controleer of Forms is ingeschakeld

Alvorens de Bouwer van de Ervaring van Forms te gebruiken, zorg ervoor [ AEM Forms voor uw milieu ](/help/forms/setup-forms-cloud-service.md) wordt toegelaten.


### &#x200B;3. Uw omgeving instellen


- **voor Edge Delivery Services (EDS):**

   - [Installatieomgeving voor Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
   - [Een nieuw formulier maken met de Edge Delivery Forms-sjabloon](/help/edge/docs/forms/universal-editor/create-forms.md)

- **voor op componenten gebaseerde vormen van de Kern:**

   - Ga naar Forms > Forms &amp; Documents op je Adobe Experience Manager-exemplaar
   - [Een nieuwe pagina maken met de sjabloon Core Components](/help/forms/creating-adaptive-form-core-components.md)


## Snel starten

### Ga naar de Forms Experience Builder

Forms Experience Builder is beschikbaar in de gebruikersinterface voor Forms-beheer, de Universal Editor en de Adaptive Forms Editor. U kunt elk van de volgende methoden gebruiken om toegang te krijgen tot het formulier:

**het Beheer UI van Forms (voor de Componenten van de Kern)**

1. **ga aan Forms**: Ga naar AEM > Forms > Forms &amp; Documenten
1. Klik op het Forms Experience Builder-pictogram op de werkbalk. De interface bevindt zich linksboven.
   ![ AI Hulp pictogram* ](/help/edge/docs/forms/assets/forms-manager.gif){width="50%"}
1. Beginnen met het maken van conversaties


**Aangepaste Redacteur van Forms (voor de Componenten van de Kern)**

1. Ga naar AEM > Forms > Forms &amp; Documents
2. [Een nieuw formulier maken met de sjabloon Core Components](/help/forms/creating-adaptive-form-core-components.md)
3. Uw formulier openen om te bewerken
4. Klik op het pictogram van de Forms Experience Builder op de editor-werkbalk
   ![ AI Hulp pictogram* ](/help/edge/docs/forms/assets/adaptive-forms-editor.gif){width="75%"}

5. Beginnen met het maken van conversaties


**Universele Redacteur (voor de Diensten Forms van de Levering van Edge)**

1. Volg de [ de opstellingsgids van Edge Delivery Services ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md) om uw pagina te creëren EDS
1. Ga naar uw EDS-pagina in de Universal Editor
1. Ga naar het Forms Experience Builder-pictogram in het rechterdeelvenster
1. Klik om de conversatie-interface te openen



### Uw eerste formulier

| Voorbeeld van gesprek |   |
|--------------------------------------------------------------------------------------------------------------------------------------------|---|
| **probeer dit gesprek om een uitvoerige contactvorm tot stand te brengen (die op de demo van de Top wordt gebaseerd):**<br><br>**u:** &quot;creeer een contactvorm om persoonlijke informatie met inbegrip van volledige naam, e-mailadres, telefoonaantal, bedrijfsnaam, baantitel, en een berichtgebied voor onderzoeken&quot;AI te vangen:<br><br>**selecteer een malplaatje**    Een drop-down om een malplaatje <br> AI te selecteren:<br><br>**selecteer een thema**    Een drop-down om een thema <br> AI te selecteren:<br><br>**creeer Vorm** | ![ Uw Eerste Vorm ](/help/edge/docs/forms/assets/create-form.png) |
| <br>**AI:** Open Gemaakt Vorm | </br> Het formulier wordt gemaakt en geopend in de editor |


### Essentiële opdrachten

| Symbool | Doel | Voorbeeldengebruik |
|--------|---------|---------------|
| `/` | Snelle handelingen en sneltoetsen | `/create-form contact form`, `/help validation rules`, `/update-layout wizard` |
| `@` | Verwijzing naar bestaande formuliervelden | `@email`, `@firstName`, `Make @phoneNumber required` |
| Onbewerkte tekst | Natuurlijk gesprek | &quot;Voeg een vereist veld voor het telefoonnummer toe&quot;, &quot;Create validation for email&quot; |

**Specifieke Voorbeelden van het Bevel:**

- `/create-form customer survey` - Hiermee maakt u een nieuw formulier voor klantonderzoek
- `/add-field @email validation` - Hiermee voegt u validatie toe aan bestaand e-mailveld
- `/create-rule show @spouse if @maritalStatus equals married` - Maakt voorwaardelijke logica
- `/configure-submit to email support@company.com` - Hiermee wordt verzending via e-mail ingesteld
- `/help multi-step forms` - Haalt hulp op bij het maken van formulieren in meerdere stappen

### Tips voor succes

- **ben specifiek**: &quot;voeg een vereist e-mailgebied met bevestiging&quot;toe werkt beter dan &quot;voeg e-mail toe&quot;
- **Verwijzing bestaande gebieden**: Gebruik `@fieldName` wanneer het wijzigen van vormen
- **Vraag om hulp**: Type `/help` gevolgd door uw vraag
- **herhaalt**: Maak één verandering in een tijd voor beste resultaten


## Manieren om een formulier te maken

### &#x200B;1. Begin met vragen over natuurlijke talen

Beschrijf uw formuliervereisten in natuurlijke taal en de Forms Experience Builder genereert de volledige formulierstructuur:

**Voorbeelden:**

- &quot;Een aanvraagformulier voor een lening maken met persoonlijke gegevens, financiële gegevens en het uploaden van documenten&quot;
- &quot;Maak een feedbackformulier voor klanten met beoordelingen, opmerkingen en productcategorieën&quot;
- &quot;Ik heb een meertrapsgewijs registratieformulier nodig voor een conferentie met betalingsverwerking&quot;

### &#x200B;2. Invoer en Omzetten

Bestaande formulieren en documenten omzetten in moderne, interactieve ervaringen:

**Gesteunde Bronnen:**

- **PDF forms**: Upload statische PDFs om deze in interactieve digitale vormen met bevestigingen om te zetten.
- **Screenshots of Beelden**: Upload foto van papierformulieren om functionele digitale versies te produceren
- **XFA Forms**: Comvert erfenis op XFA-Gebaseerde vormen aan moderne responsieve vormen

**hoe te om in te voeren:**

1. Klik op het pictogram voor bijlagen in de Forms Experience Builder-interface
2. Upload uw bestand (PDF, afbeelding, Figma-ontwerp, enz.)
3. Beschrijf uw vereisten:
   - &quot;Dit PDF-formulier converteren naar een digitale versie&quot;
   - &quot;Een formulier maken dat overeenkomt met deze schermopnamelay-out
   - &quot;Dit formulier maken op basis van mijn figuurontwerp&quot;

**Gesteunde Types van Dossier:**

- **Beelden** (PNG, JPG, GIF): De lay-outs van de vorm, UI mockups, gescande vormen, handgetekende schetsen
- **de Dossiers van PDF**: Bestaande vormen, specificaties, documenten, Acroforms, XFA vormen
- **Screenshots**: Desktop/mobiele app schermafbeeldingen, de foto&#39;s van de papiervorm, whiteboardschetsen
- **Hand-getekende Schetsen**: De schetsen van de Napkin, draadframes, (gefotografeerde) conceptafbeeldingen

### Belangrijkste interacties

#### Formulierelementen toevoegen

**Basistoevoegingen:**

    👤 U: &quot;voeg een sectie voor persoonlijke informatie toe&quot;
    👤 U: &quot;omvat een dossierupload voor hervat&quot;
    👤 U: &quot;voeg een dropdown voor landselectie toe&quot;

**Gedetailleerde specificaties:**

    👤 U: &quot;Voeg een persoonlijk informatiepaneel met gebieden voor volledige naam, geboortedatum, telefoonaantal, en e-mailadres toe&quot;
    👤 U: &quot;omvat een veilige component van de dossierupload voor documenten, beperkt tot de dossiers van PDF onder 5MB&quot;
    👤 U: &quot;voeg een landdropdown met opties voor V.S., Canada, VK, en Duitsland toe&quot;

#### Dynamisch gedrag maken

**Eenvoudige logica:**

    👤 U: &quot;toon extra gebieden wanneer &quot;Andere&quot;wordt geselecteerd&quot;AI: &quot;Created a conditional rule that shows additional fields when &quot;Other&quot; is selected&quot;
    🤖 U: &quot;Make the email field required&quot;
    
    👤 AI: &quot;Updated the email field to be required with validation&quot;
    🤖 You: &quot;calculate the total automatically&quot;
    
    👤 AI: &quot;Added calculation logic to automatically compute totals&quot;
    🤖

**Complexe bedrijfsregels:**

    👤 U: &quot;toon de gebieden van de partnerinformatie slechts wanneer de huwelijksstatus aan &quot;Gehuwd&quot;wordt geplaatst:&quot;AI: &quot;creeerde een voorwaardelijke regel die de gebieden toont van de echtgeno(o)t op huwelijkse status wordt gebaseerd&quot;
    🤖 U: &quot;berekent de totale kosten door hoeveelheid en prijs te vermenigvuldigen, dan voeg 10% belasting&quot;dan toe AI: &quot;Toegevoegde berekeningslogica met hoeveelheid, prijs, en belastingberekening&quot;
    
    👤: Laat de verzendknoop toe slechts wanneer alle vereiste gebieden worden voltooid en de termijnen worden goedgekeurd&quot;
    🤖 AI: &quot;Gemaakt bevestigingslogica die voorlegging toelaat slechts wanneer alle voorwaarden worden voldaan aan&quot;
    
    👤
    🤖

#### Formulierindeling en -ontwerp

**de veranderingen van de Lay-out:**

    👤 U: &quot;maak dit een multi-step vorm&quot;
    🤖 AI: &quot;zette de vorm in een progressieve lay-out met navigatie&quot;om&quot;
    
    👤 U: &quot;organiseer gebieden in twee kolommen&quot;
    🤖 AI: &quot;werkte de lay-out aan vertoningsgebieden in een twee-kolomregeling&quot;bij 
    
    👤 U: &quot;Omzetten in een harmonielay-out&quot;
    🤖 AI: &quot;transformeerde de vorm om sectie in stijl te gebruiken 

**de verbeteringen van het Ontwerp:**

    👤 U: &quot;creeerde een tovenaar-stijl vorm met 3 stappen: persoonlijke info, voorkeur, en overzicht&quot;
    🤖 AI: &quot;creeerde een tovenaar vorm met drie verschillende stappen en navigatie&quot;
    
    👤 U: &quot;Rangschik de adresgebieden in een compacte twee-kolomlay-out&quot;
    🤖 AI: &quot;Georganiseerde adresgebieden in een compacte twee-kolomformaat&quot;
    
    👤 u: &quot;Werk de lay-out in aan 
    🤖 AI: &quot;Gewijzigd de lay-out om de verstrekte ontwerpverwijzing aan te passen&quot;

### Configuratie verzenden

De Forms Experience Builder kan verschillende verzendeindpunten configureren om uw formulieren te verbinden met externe systemen en services:

| Type handeling verzenden | Opdracht Instellen | Hoofdletters gebruiken |
|------------------|---------------|----------|
| **E-mail** | &quot;Formulier verzenden naar e-mail&quot; | Meldingen en bevestigingen voor het indienen van formulieren |
| **REST API** | &quot;Verzenden naar REST-eindpunt&quot; | Aangepaste toepassingen en systemen van derden |
| **Opslag van de Wolk** | &quot;Opslaan in Azure/SharePoint&quot; | Documentopslag en bestandsbeheer |
| **Workflow** | &quot;Verbinding maken met Power Automate&quot; | Automatisering en goedkeuring van bedrijfsprocessen |
| **Marketing** | &quot;Integreren met Marketo&quot; | Beheer van leads en automatisering van marketing |

**Geavanceerde voorlegt configuratievoorbeelden voor:**

    👤 U: &quot;Verzend vormverzendingen naar hr@company.com en creeer een geval in ons systeem van CRM&quot;
    🤖 AI: &quot;gevormde e-mail voorlegging en CRM voorlegt actie&quot;
    
    👤 U: &quot;voorlegt gegevens aan ons REST API eindpunt en teweegbrengt het nieuwe klantenwerkschema&quot;
    🤖 AI: &quot;De voorlegging van de Reparatie API van de Opstelling met werkschematriggers&quot;
    
    👤 U: &quot;E-reacties aan het verkoopteam en voegt de lood aan ons aan ons op aan ons marketing automatiseringsplatform toe&quot;
    🤖 AI: &quot;Gevormde multi-kanaals voorlegging met e-mail en marketing automatisering&quot;





## Geavanceerde formulierbewerkingen


### Complexe regel maken

Maak geavanceerde validatie- en bedrijfslogica die reageert op gebruikersinteracties en zorgt voor gegevensintegriteit:

    👤 U: &quot;toon de adressectie slechts als de gebruiker &quot;Schip aan verschillend adres&quot;selecteert \&quot;
    🤖 AI: &quot;creeerde een voorwaardelijke regel die het adrespaneel toont/verbergt dat op checkbox selectie wordt gebaseerd&quot;

### Meerdere stappen voor het maken van formulieren

    👤 U: &quot;creeer een progressieve vorm met 3 stappen: persoonlijke info, voorkeur, bevestiging&quot;
    🤖 AI: &quot;creeerde een progressieve vorm met navigatie tussen stappen en bevestiging in elk stadium&quot;

### Geavanceerde veldtypen

- Het uploaden van bestanden met validatie- en groottebeperkingen voor documentbeheer
- Datumkiezers met beperkingen en bedrijfsregels voor het plannen
- Vervolgkeuzelijsten met dynamische opties die worden gewijzigd op basis van gebruikersselecties
- Keuzerondjes met voorwaardelijke logica voor complexe beslissingsstructuren


### PDF naar formulier converteren

    👤 U: &quot;Convert this PDF into an interactive form&quot;
    🤖 AI: &quot;Analyzed the PDF and created a form with appropriate field types and validation&quot;





## Help en training voor producten

De Forms Experience Builder kan u ook leren over AEM Forms-functies:

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

## Aanbevolen procedures

### Formulierontwerp

- **houd het eenvoudig**: Begin met essentiële gebieden en voeg ingewikkeldheid slechts toe wanneer noodzakelijk om overweldigende gebruikers te vermijden
- **Gebruik duidelijke etiketten**: Maak gebiedsdoeleinden duidelijk met beschrijvende etiketten die gebruikers door de vorm begeleiden
- **verstrekt hulptekst**: De gebruikers van de gids door complexe gebieden met contextuele hulp en voorbeelden
- **Test grondig**: Valideer alle gebruikerspaden om ervoor te zorgen dat de formulieren in alle scenario&#39;s correct werken

### Gebruikerservaring

- **Progressieve mededeling**: toon relevante die gebieden op context worden gebaseerd om cognitieve lading te verminderen en voltooiingstarieven te verbeteren
- **Duidelijke navigatie**: De gebruikers van de hulp begrijpen waar zij in de vorm zijn en welke stappen blijven
- **Responsief ontwerp**: Zorg het werk van vormen op alle apparaten en schermgrootte voor maximumtoegankelijkheid ervoor
- **Toegankelijkheid**: volg de richtlijnen van WCAG om vormen bruikbaar te maken door mensen met handicaps

### Prestaties

- **optimaliseer gebiedstelling**: slechts om noodzakelijke informatie vragen om vormbeëindiging te verminderen en voltooiingstarieven te verbeteren
- **Gebruik aangewezen bevestiging**: Vermijd fouten alvorens voorlegging om directe te verstrekken terugkoppel en begeleiding
- **de voltooiingspercentages van de Test**: De doeltreffendheid van de monitor en verbetert vorm door analyses en gebruiker terugkoppelen
- **Regelmatige updates**: Houd formulieren huidig met bedrijfsbehoeften en gebruikersverwachtingen voor optimale prestaties

### Brand Consistency

- **creeer merkmalplaatjes**: Bereid branded vormmalplaatjes met de kleuren, de doopvonten van uw organisatie, en het stileren voor de aanvang van vormverwezenlijking voor
- **bepaalt stijlnormen**: Vestig verenigbare knoopstijlen, gebiedslay-outs, en het uit elkaar plaatsen van richtlijnen die in herinneringen kunnen worden van verwijzingen voorzien
- **de merkactiva van het Gebruik**: Bereid logo&#39;s, kleurencodes, en merkrichtlijnen voor gemakkelijke verwijzing wanneer het creëren van vormen voor
- **bibliotheek van het Malplaatje**: Bouw een inzameling van brandde vormmalplaatjes voor gemeenschappelijke gebruiksgevallen (contact, registratie, terugkoppelt)
- **de herinneringen van de Stijl**: Omvat brand-specifieke instructies: &quot;bedrijfblauw van het gebruik (#1234AB) voor knopen en collectieve doopvont Helvetica&quot;



## Problemen oplossen

| Probleem | Snel repareren |
|-------|-----------|
| **Interface niet ladend** | Browser vernieuwen, internetverbinding controleren |
| **Bevelen het werken niet** | Probeer `/help` of gebruik in plaats daarvan een natuurlijke taal |
| **@fieldName niet herkend** | Spelling controleren, controleren of veld bestaat |
| **uploadt van het Dossier ontbreekt** | PDF/JPG/PNG gebruiken bij 10 MB |
| **de blik van de Vorm verkeerd** | Meer specifiek: &quot;Maak het mobiel&quot; |
| **verzendt configuratie ontbreekt** | API-referenties en -machtigingen controleren |

**nog hulp nodig?** Typ `/help` gevolgd door uw specifieke vraag of neem contact op met de systeembeheerder.

Voor extra steun, verwijs naar de belangrijkste [ Snelle Bibliotheek van de Bouwer van de Ervaring van Forms ](ai-assistant-prompt-library.md) of contacteer uw systeembeheerder voor technische bijstand.
