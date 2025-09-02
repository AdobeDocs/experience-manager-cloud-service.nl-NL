---
title: Forms Experience Builder - Snelle bibliotheek
description: Verzameling van bewezen snelle patronen en voorbeelden voor het bouwen van formulieren met AI-hulp in de gebruikersinterface van Forms Management, de Adaptive Forms Editor en de Universal Editor.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: c8f64082-a23f-4919-ad66-042faad77d31
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: tm+mt
source-wordcount: '2193'
ht-degree: 0%

---


# Forms Experience Builder - Snelle bibliotheek

Verzameling herbruikbare snelle patronen en voorbeelden die zijn geoptimaliseerd voor Forms Experience Builder. Deze gestroomlijnde bibliotheek richt zich op de twee belangrijkste aanmaakmethoden: Maken van werkschijf en importeren en converteren, met verbeterde ondersteuning voor slimme velden met LLM-voeding en consistentie van merken.

>[!NOTE]
>
> De Forms Experience Builder is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien de Bouwer van de Ervaring van Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## Deze Promptbibliotheek gebruiken

Deze bibliotheek verstrekt herbruikbare snelle patronen voor gemeenschappelijke vorm-bouwende scenario&#39;s. Voor uitvoerige beste praktijken, zie de [ Begonnen Gids van de Bouwer van de Ervaring van Forms ](forms-ai-assistant-getting-started.md#best-practices).

### Snelle tips voor deze bibliotheek

- **Begin met voorbeelden** - Gebruik verstrekte herinneringen als malplaatjes en pas aan uw behoeften aan
- **Twee creatiemethodes** - kies creeer van Scratch of de Invoer &amp; zet benaderingen om
- **ben specifiek** - voeg uw eigen details aan generische voorbeelden toe
- **Test grondig** - bevestigt altijd resultaten in uw specifiek milieu

### Merksjablonen en -stijlen

**bereidt merkactiva vooraf voor verenigbare vormverwezenlijking voor:**

- **Malplaatjes van het Merk** - bereidt gestandaardiseerde vormmalplaatjes met de kleuren, de doopvonten, en lay-outpatronen van uw organisatie voor
- **de Richtlijnen van de Stijl** - bepalen verenigbaar gebied het stileren, knoopontwerpen, en het uit elkaar plaatsen normen die de Bouwer van de Ervaring van Forms kan toepassen
- **Bibliotheek van de Component** - het werk met uw ontwikkelingsteam om herbruikbare vormcomponenten voor te bereiden die uw merkidentiteit aanpassen
- **Visuele Assets** - bereidt logo&#39;s, pictogrammen, en achtergrondelementen voor vormintegratie voor

<!-- **Example Brand Application Prompt:**

    Apply our financial services brand template with:
    - Corporate blue (#003366) and silver (#C0C0C0) color scheme
    - Open Sans font family for all text
    - 16px minimum font size for accessibility
    - Consistent 24px spacing between sections
    - Corporate logo in header with proper sizing
    - Professional button styling with hover effects

>[!NOTE]
>
>**Custom Components**: Check with your development team about using organization-specific components and their compatibility with Forms Experience Builder before implementing custom brand elements.

>[!NOTE]
>
> This prompt library has been updated to reflect the streamlined Forms Experience Builder capabilities. Some advanced integration and testing features shown in examples may require additional configuration.

-->


## Voorbeelden van incrementele ontwikkeling

In deze voorbeelden ziet u hoe u stapsgewijs formulieren maakt, eenvoudig begint en geleidelijk complexiteit toevoegt:

### Voorbeeld 1: Een contactformulier stapsgewijs samenstellen

**Stap 1 - Begin Eenvoudig:**

     creeer een basiscontactvorm met naam, e-mail, en berichtgebieden 

**Stap 2 - voeg Bevestiging toe:**

     maak @name en @email verplichte gebieden met aangewezen bevestiging 

**Stap 3 - verbeter de Ervaring van de Gebruiker:**

     voegt placeholder tekst toe: @name &quot;Uw volledige naam&quot;, @email &quot;your.email@company.com&quot;, @message &quot;vertelt ons hoe wij kunnen helpen&quot;

**Stap 4 - voeg Geavanceerde Eigenschappen toe:**

     voegt een dropdown vraagType met opties toe: &quot;Algemene Vraag&quot;, &quot;Verzoek van de Steun&quot;, &quot;Onderzoek van de Verkoop&quot;, &quot;Partnerschap&quot;

**Stap 5 - voer Voorwaardelijke Logica uit:**

    /create-rule toon @priorityLevel dropdown (Laag, Medium, Hoog) slechts wanneer @vraagType &quot;Verzoek van de Steun&quot;evenaart 

### Voorbeeld 2: Een registratieformulier stapsgewijs samenstellen

**Stap 1 - Basisstructuur:**

     creeer een vorm van de gebruikersregistratie met persoonlijk informatiepaneel 

**Stap 2 - voeg Vereiste Gebieden toe:**

     voegt gebieden voor @firstName, @lastName, @email, @phoneNumber met aangewezen bevestiging 
 toe
**Stap 3 - voeg BedrijfsLogica toe:**

     creeer een regel: als @age onder 18 is, toon ouder/de sectie van de de informatieinformatie van de hoedster 

**Stap 4 - verbeter met Voorkeur:**

     voeg een voorkeurenpaneel met @newsletterSubscription, @marketingConsent, @termsAccepted 
 toe
**Stap 5 - voeg Dossier toe uploadt:**

     omvat een dossier uploadt gebied voor @profilePicture met groottelimiet van 5MB 

## Formulier maken en beheren

**wanneer te gebruiken:** wanneer u nieuwe vormen moet creëren of bestaande degenen wijzigen.

**hoe te gebruiken:** kies één van twee benaderingen: creeer van Scratch of de Invoer &amp; zet (zie [ Begonnen Gids ](forms-ai-assistant-getting-started.md#two-ways-to-create-forms)) om.

**Vragen van het Voorbeeld - Eenvoudige Making van de Vorm:**

     creeer een klant terugkoppelt vorm met:
     - de Rating van het Product (1-5 sterren) 
     - het gebied van de Commentaar voor gedetailleerde terugkoppelt 
     - de e-mail van de Klant (facultatief) 
     - voorlegt aan e-mailbericht 

**Voorbeeldprompt - Complex formulier maken:**

    Maak een uitgebreid onboardingformulier voor werknemers met:
    
    **Sectie persoonlijke informatie:**
    - Volledige naam (voor-, midden, achterlaatste)
    - Geboortedatum met leeftijdsvalidatie
    - Contactgegevens (e-mail, telefoon, adres)
    - Contactgegevens
    
     voor noodgevallen&#x200B;**Arbeidsgegevens:**
    - Functie- Functie- Functie-
     Startdatum met validatie
     op werkdag- Salarisinformatie met vertrouwelijkheidskennisgeving
    - Rapportagestructuur
    
    **Document uploaden:**
    - CV uploaden (PDF, DOC, DOCX)-
     ID-VERIFICATIEDOCUMENTEN
    - Belastingformulieren en bankgegevens
    - Ondertekende arbeidsovereenkomst
    
    **Voorkeuren:**
    - Selectie van voordelen met kostencalculator
    - Voorkeuren voor werkschema- Trainingsvereisten
    
    - Apparatuurbehoeften
    
    **Validatieregels:**
    - Validatie
     van e-mailindeling- Validatie
     van telefoonnummerindeling- Leeftijd moet 18 jaar of ouder
     zijn- Alle vereiste documenten moeten worden geüpload
    - Algemene voorwaarden moeten worden geaccepteerd
    
    **Acties indienen:**
    - Stuur een bevestigingsmail naar de nieuwe werknemer
    - Breng de HR-afdeling
     op de hoogte- Maak een personeelsdossier aan in het HR-systeem
    - Plan een oriëntatiegesprek

**Aanwijzingen voor formulierbeheer:**

     de Invoer dit de toepassingsvorm van PDF en zet het in een adaptieve vorm met verbeterde bevestiging 
    
     bij Werk de bestaande contactvorm om sociale media handvatten en aangewezen contactmethode te omvatten 
    
     reorganize de registratieformulier in een 3-stap tovenaar: persoonlijke info, voorkeur, bevestiging 

## Veld beheren en configureren

**wanneer te gebruiken:** wanneer u, vormgebieden moet toevoegen wijzigen of vormen.

**hoe te gebruiken:** ben specifiek over gebiedstypes, bevestigingsregels, en gebruikerservaringsvereisten.

**Vraag van het Voorbeeld - de Basis Toevoeging van het Gebied:**

     voeg een gebied van de tekstinput voor &quot;Naam van het Bedrijf&quot;met placeholder toe &quot;ga uw bedrijfnaam in&quot;

**Vraag van het Voorbeeld - Geavanceerde Configuratie van het Gebied:**

     voeg een uitvoerige adressectie met toe:
    
    **Adres:** 
     - de lijn van het Adres 1 (vereist, maximum 100 karakters) 
     - de lijn van het Adres 2 (facultatief, maximum 100 karakters) 
     - Stad (vereist, dropdown met gemeenschappelijke steden) 
     - Staat/Provincie (vereist, drop-down) 
     - Postal code (vereiste, formaatbevestiging) 
     
    
     - Land (vereist, gebrek aan &quot;Verenigde Staten&quot;) 
     **de Regels van de Bevestiging:** 
     - de Postcode moet staatsselectie aanpassen 
     - de Lijn van het Adres 1 kan niet leeg zijn 
    
     - Stad moet een geldige stad voor geselecteerde staat zijn 
    **Ervaring van de Gebruiker:** 
     - auto-volledig voor adresgebieden 
     - Duidelijke etiketten en hulptekst {11 5} - Mobiele-vriendelijke invoervelden 
     - Compatibiliteit met toegankelijkheid 

**Vragen van de Configuratie van het Gebied:**

     maak @email gebied met bevestiging in real time en douanefoutenmelding 
    
     wordt vereist een drop-down voor @country met opties voor V.S., Canada, VK, Duitsland, Frankrijk, en &quot;Andere&quot;
    
     vorm @phoneNumber gebied met formaat (XXX) XXX-XXXX en bevestiging 
    
     voeg een dossier toe uploadt gebied voor @resume met PDF en DOC beperkingen, maximum 5MB 

## Verbeterde slimme velden in LLM

**wanneer te gebruiken:** wanneer u gebieden met pre-bevolkte opties nodig hebt die hefboomwerking de kennisbasis van AI.

**hoe te gebruiken:** gebieden van het Verzoek die uitvoerige gegevensreeksen vereisen - AI kan opties automatisch bevolken gebruikend zijn ingebouwde kennis.

### Geografische en locatievelden

**Luchthavens en Vervoer:**

     voeg een drop-down voor vertrekluchthavens met alle belangrijke internationale luchthavens 
     toe toevoegt het gebied van de aankomstLuchthaven met IATA codes en volledige namen 
     creeer een gebied voor dichtstbijzijnde luchthaven aan gebruikersplaats 
     voeg een selectie van treinstations voor Europese steden 
 toe
**Administratieve Gebieden:**

     voeg een volledige lijst van de staten van de V.S. met afkortingen 
     tot een landdrop-down met de codes van ISO en volledige namen 
     toe voeg een gebied voor grote wereldsteden met tijdzones 
     omvat een daling van Canadese provincies en gebieden 
     een gebied voor de districten van het VK en postgebieden 
 toe

### Gegevens voor bedrijven en de industrie

**Classificaties van het Bedrijf:**

     voeg een gebied voor de industrieclassificatie met de codes van NAICS 
     toe leidt tot een daling van bedrijfentiteit types (LLC, Bedrijf, Partnerschap, enz.)
     voeg een gebied voor de categorieën van de bedrijfgrootte (opstarten, KMO, onderneming) toe 
     omvat afdelingsselectie voor grote organisaties 
     een gebied voor de professionele diensttypes 
 toevoegen
**Professionele classificaties:**

     voeg een gebied voor baantitels met gemeenschappelijke industriefollen 
     toe leidt tot een daling van professionele certificatie door gebied 
     omvat onderwijsniveaus met gradentypen 
     voeg een gebied voor jaren van ervaringswaaiers 
     tot een selectie voor programmeertalen en kaders 

### Normen en regelgeving

**Financiële en Juridische:**

     voeg een gebied voor muntcodes met symbolen en wisselkoersen 
     toe leidt tot een daling van de types van fiscale identiteitskaart door land 
     omvat een gebied voor wettelijke documenttypes 
     toevoegt de opties van de betalingsmethode met veiligheidseigenschappen 
     tot een selectie voor bancaire instellingen door land 

**Technische Normen:**

     voeg een daling van dossierformaattypes met uitbreidingen 
     toe omvat netwerkprotocolopties 
     een gebied voor gegevensbestandtypes en versies 
     creeer een selectie voor API authentificatiemethodes 

### Gezondheidszorg en medische zorg

**Medische Classificaties:**

     voeg een gebied voor medische specialiteiten 
     toe leidt tot een daling van gemeenschappelijke geneesmiddelen met generische namen 
     omvat een gebied voor de types van verzekeringsleverancier 
     toevoegen een selectie voor de medische verhoudingen van het noodcontact 
     tot een gebied voor dieetbeperkingen en allergieën 

### Intelligentie tijd en kalender

**Datum en de Gebieden van de Tijd:**

     voeg een gebied voor kantooruren met tijdzone behandeling 
     toe creeert een daling van openbare vakanties door land 
     seizoensgebonden opties met datumwaaiers 
     voegt een gebied voor conferentiezaal het boeken met beschikbaarheid 
     tot een selectie voor terugkomende vergaderingspatronen 
 toe

### Product- en servicecategorieën

**E-commerce Classificaties:**

     voeg een gebied voor productcategorieën met subcategorieën 
     toe leidt tot een daling van het verschepen methodes met leveringsramingen 
     omvat een gebied voor de opties van het terugkeerbeleid 
     een selectie voor klant prioritaire niveaus 
     tot een gebied voor het factureren van abonnementen cycli 

**Prompts van het Voorbeeld Slimme Gebied:**

     &quot;voeg een gebied van de vertrekluchthaven met alle belangrijke luchthavens wereldwijd met inbegrip van IATA- codes en stadsnamen&quot;toe 
    
     &quot;creeer een uitvoerig industrieterrein gebruikend standaardNAICS classificatie met technologiesubcategorieën&quot;
    
     &quot;omvat een professionele certificatiestrijdvervolgkeuzelijst die op het geselecteerde baangebied&quot;wordt gebaseerd 
    
     &quot;voeg een internationaal telefoonnummergebied toe dat formaten die op het geselecteerde land worden gebaseerd&quot;
    
     &quot;creeer een universitair selectieveld 

## Regels maken en bedrijfslogica

**wanneer te gebruiken:** wanneer u voorwaardelijke logica, bevestigingsregels, of bedrijfsprocessen moet uitvoeren.

**hoe te gebruiken:** beschrijf duidelijk de bedrijfslogica, specificerend voorwaarden en acties.

**Vragen van het Voorbeeld - Eenvoudige Voorwaardelijke Logische:**

     creeer een regel die @spouseInformation paneel toont slechts wanneer @maritalStatus &quot;Gehuwd&quot;evenaart 

**Vraag van het Voorbeeld - Complexe BedrijfsRegels:**

     voer uitvoerige de toepassingsbevestiging van de leningstoepassing uit:
    
    **Inkomensbevestiging:** 
     - als @annualIncome minder dan 30000 is:
     - toon waarschuwingsbericht: &quot;Inkomsten kunnen voor gevraagd leningsbedrag ontoereikend zijn&quot;
     - Vereis extra inkomensdocumentatie 
     - Vertoning bericht: &quot;De extra documentatie kan worden vereist&quot;
     - als @annualIncome groter is 100000:
     - toon de opties van de premieservices 
     - laat prioritaire verwerkingscontroledoos 
    
    **Leeftijd-Gebaseerde Bevestiging toe:** 
     - als @age minder dan 18 is:
     - toon de sectie van ouder/van de Bewaakzame informatie 
     - maak ouder handtekeningupload verplicht 
     - vervang- Verzenden de Verandert de tekst aan &quot;Voorlegt knooptekst voor Overzicht&quot; 14&rbrace; - als @age 65 of ouder is:
     - toon senior kortingsopties 
     - voeg de sectie van toegankelijkheidsvoorkeuren toe 
    

**regel-Specifieke herinneringen:**

     creeer a **zichtregel** die @spouseInformation paneel toont slechts wanneer @maritalStatus &quot;Gehuwd&quot;of &quot;Binnenlands Partnerschap&quot;evenaart 
    
     **progressieve onthulling** toevoegt waar de extra vragen gebaseerd op vorige antwoorden verschijnen. Begin met basisinfo, dan toon relevante follow-ups 
    
     voert **smart gebreken** uit waar @country selectie verwante gebieden automatisch-plaatst. Handmatige overschrijving toestaan 

## Gegevensintegratie en -verzending

**wanneer te gebruiken:** wanneer u vormen met achterste deelsystemen, gegevensbestanden, of de externe diensten moet verbinden.

**hoe te gebruiken:** Begin met basisvoorleggingsopstelling, dan voeg extra integratie incrementeel toe. Geef het integratietype, de vereisten voor de gegevensindeling en de voorkeuren voor foutafhandeling op.

**Vragen van het Voorbeeld - Begin met BasisVerzending:**

     vorm basisvormvoorlegging voor @applicationForm:
    
    **Primaire Verzending:** 
     - verzend vormgegevens naar het eindpunt REST: `/api/v1/toepassingen ` 
     - de gegevens van het Formaat als JSON 
     - toon succesbericht: &quot;De met succes voorgelegde Toepassing&quot;
     - toon foutenmelding als de voorlegging ontbreekt: &quot;Verzending, gelieve opnieuw te proberen&quot;

**dan voeg geleidelijk Secundaire Acties toe:**

     voegt e-mailbericht aan @applicationForm toe: Verzend bevestigingsmail naar @email adres met het aantal van de toepassingsverwijzing 
    
     toevoegt de integratie van CRM aan @applicationForm: Creeer nieuw loodverslag met @firstName, @lastName, @email, en plaats Status aan &quot;Nieuwe Toepassing&quot;

**Voorbeeld prompt - standaard multi-channel inzending:**

    Configureer formulierverzending met meerdere gegevensbestemmingen:
    
    **Primaire inzending:**
    - Verzend formuliergegevens naar het REST-eindpunt: &#39;/api/v1/applications&#39;
    - Voeg authenticatieheader toe met API-sleutel
    - Formatteer gegevens als JSON met geneste objecten voor adres en dienstverband
    - Behandel succesvolle respons (201) door een bedankbericht
    
     weer te geven&#x200B;**Secundaire acties:**
    - Stuur een e-mail met meldingen naar de aanvrager op @email adres
    - Kopieer aanvraaggegevens naar het volgsysteem
    - Activeer de workflow voor het goedkeuringsproces
     - Maak een record in CRM met de leadstatus &quot;Nieuwe toepassing&quot;
    
    **Foutafhandeling:**
    - Als de primaire inzending mislukt, sla dan de gegevens lokaal op en probeer het
     opnieuw- Toon gebruiksvriendelijke foutmelding: &quot;Inzending tijdelijk niet beschikbaar&quot;
    - Bied de optie om formuliergegevens als back-up
     te downloaden - Stuur een waarschuwingsmail naar het beheerdersteam over mislukte indiening
    
    **Successtroom:**
    - Omleiden naar de bevestigingspagina met het referentienummer
     van de toepassing- Stuur een bevestigingsmail met de volgende stappen
    - Geef de geschatte verwerkingstijdlijn weer

**integratie-Specifieke herinneringen:**

     verbind dit formulier met **CRM systeem** om nieuwe leads te maken. Wijs @firstName aan FirstName, @email aan E-mail toe, plaats LeadSource aan &quot;de Vorm van het Web&quot;, en Status aan &quot;Nieuwe&quot;
    
     Opstelling **werkschemamarkering** wanneer de vorm wordt voorgelegd. Geef alle vormgegevens door en teweegbrengt goedkeuringswerkschema met managerbericht 
    
     vormen **gegevensbestand integratie** om vormvoorlegging als verslagen te bewaren. Nieuwe map maken voor elke verzending met geüploade documenten 

<!-- ## Import & Convert Existing Forms

**When to use:** When you have existing forms, documents, or designs to transform into modern AEM forms.

**How to use:** Upload your source file and describe the conversion requirements (see [Import Guide](forms-ai-assistant-getting-started.md#2-import-and-convert)).


**Design Import Prompts:**

    Import this **design mockup** and convert it into an adaptive form. Maintain the exact visual design but add proper validation and mobile responsiveness

    Analyze this **image of a paper form** and recreate it digitally. Improve the layout for better mobile experience while keeping all mandatory fields

    Convert this **existing HTML form** to AEM adaptive form format. Preserve all functionality but add AEM-specific features like rules and themes

## Mobile Optimization & Responsiveness

**When to use:** When forms need to work seamlessly across all device types and screen sizes.

**How to use:** Start with basic mobile optimization, then enhance with advanced features. Emphasize mobile-first approach and specify breakpoint behaviors incrementally.

**Example Prompt - Start with Basic Mobile Optimization:**

    Make @contactForm mobile-friendly with:
    
    **Basic Mobile Layout:**
    - Single column layout for all form sections
    - Larger touch targets for buttons and inputs
    - Responsive design that works on phones and tablets

**Then Add Advanced Mobile Features:**

    Enhance @contactForm mobile experience with:
    - Sticky submit button at bottom of screen
    - Touch-friendly date pickers
    - Swipe gestures for multi-step navigation

**Example Prompt - Comprehensive Mobile-First Optimization:**

    Optimize this form for **mobile-first responsive design**:
    
    **Mobile Layout (320px - 768px):**
    - Single column layout for all form sections
    - Larger touch targets (minimum 44px height)
    - Simplified navigation with collapsible sections
    - Sticky submit button at bottom of screen
    - Auto-zoom disabled on input focus
    
    **Tablet Layout (768px - 1024px):**
    - Two-column layout for shorter fields (name, email)
    - Single column for complex fields (address, comments)
    - Side navigation for multi-step forms
    - Optimized for both portrait and landscape
    
    **Desktop Layout (1024px+):**
    - Multi-column layouts where appropriate
    - Horizontal form sections for related fields
    - Sidebar navigation for long forms
    - Hover states and advanced interactions

**Mobile-Specific Prompts:**

    Make this form **touch-friendly** with larger buttons and simplified navigation for mobile users

    Optimize form for **tablet users** with appropriate field sizes and navigation patterns

    Add **swipe gestures** for multi-step form navigation on mobile devices

## Accessibility & Compliance

**When to use:** When forms need to meet accessibility standards (WCAG) or compliance requirements.

**How to use:** Specify the required compliance level and any specific accessibility features needed.

**Example Prompt - Basic Accessibility:**

    Make @contactForm accessible with:
    
    **Basic Accessibility:**
    - Proper ARIA labels for all form fields
    - Keyboard navigation support
    - High contrast color scheme
    - Screen reader compatibility
    - Focus indicators for all interactive elements

**Example Prompt - Advanced Accessibility:**

    Implement comprehensive accessibility for @applicationForm:
    
    **WCAG 2.1 AA Compliance:**
    
    - Semantic HTML structure with proper headings
    - ARIA landmarks and roles for navigation
    - Color contrast ratio of at least 4.5:1
    - Keyboard-only navigation support
    - Screen reader announcements for dynamic content
    
    **Form-Specific Accessibility:**
    
    - Error messages announced to screen readers
    - Field validation with clear error descriptions
    - Progress indicators for multi-step forms
    - Skip navigation links for keyboard users
    - Alternative text for all images and icons
    
    **User Experience:**
    
    - Clear focus indicators on all interactive elements
    - Logical tab order through form fields
    - Descriptive link text and button labels
    - Help text available for complex fields
    - Timeout warnings for session expiration

**Accessibility-Specific Prompts:**

    Add **screen reader support** to this form with proper ARIA labels and announcements

    Implement **keyboard navigation** for all form interactions and navigation elements

    Ensure **color contrast** meets WCAG AA standards for all text and interactive elements  

## Performance Optimization

**When to use:** When forms need to load quickly and perform well under various conditions.

**How to use:** Specify performance requirements and optimization strategies.

**Example Prompt - Basic Performance:**

    
Optimize @contactForm for performance:

**Loading Optimization:**

- Lazy load non-critical form sections
- Minimize initial bundle size
- Optimize images and assets
- Enable caching for static resources
    

**Example Prompt - Advanced Performance:**

    
Implement comprehensive performance optimization for @applicationForm:

**Loading Performance:**

- Progressive loading of form sections
- Optimize images with WebP format
- Minimize JavaScript bundle size
- Enable gzip compression for all assets

**Runtime Performance:**

- Debounce validation calls to reduce API requests
- Optimize conditional logic execution
- Cache frequently used data
- Implement virtual scrolling for long lists

**User Experience:**

- Show loading indicators for async operations
- Provide offline capability for form data
- Auto-save form progress every 30 seconds
- Optimize form submission with retry logic

**Monitoring:**

- Track form load times and user interactions
- Monitor validation performance
- Measure submission success rates
- Alert on performance degradation
    

**Performance-Specific Prompts:**

    
Optimize form **loading speed** by implementing progressive loading and asset optimization
    

    
Add **auto-save functionality** to prevent data loss during form completion
    

    
Implement **offline support** so users can complete forms without internet connection
    

## Testing & Quality Assurance

**When to use:** When forms need comprehensive testing to ensure reliability and user satisfaction.

**How to use:** Specify testing scenarios, validation requirements, and quality metrics.

**Example Prompt - Basic Testing:**

    
Add comprehensive testing for @contactForm:

**Functional Testing:**

- Test all form field validations
- Verify submit functionality works correctly
- Test error handling and user feedback
- Validate conditional logic and rules
    

**Example Prompt - Advanced Testing:**

    
Implement comprehensive testing strategy for @applicationForm:

**Functional Testing:**

- Unit tests for all validation rules
- Integration tests for submit actions
- End-to-end testing for complete user flows
- Cross-browser compatibility testing

**User Experience Testing:**

- Usability testing with target user groups
- Accessibility testing with screen readers
- Mobile device testing on various screen sizes
- Performance testing under load conditions

**Quality Assurance:**

- Automated testing for regression prevention
- Manual testing for edge cases and scenarios
- Security testing for data protection
- Compliance testing for regulatory requirements

**Monitoring:**

- Track form completion rates and abandonment
- Monitor error rates and user feedback
- Measure performance metrics and load times
- Analyze user behavior and interaction patterns
    

**Testing-Specific Prompts:**

    
Add **automated testing** for all form validations and submit functionality
    

    
Implement **user acceptance testing** scenarios for complete form workflows
    

    
Set up **performance monitoring** to track form load times and user interactions
    
-->

## Opdrachtverwijzing

### Essentiële opdrachten

| Opdracht | Hoofd-/kleine letters | Voorbeeld |
|---------|---------------|---------|
| `/create-form` | Nieuwe formulieren starten | `/create-form employee onboarding with personal info and benefits selection` |
| `/add-form` | Formulieren toevoegen aan pagina&#39;s | `/add-form newsletter signup with email and preferences` |
| `/update-layout` | De formulierstructuur wijzigen | `/update-layout wizard with 4 steps: info, preferences, review, confirm` |
| `/update-field` | Veldeigenschappen wijzigen | `/update-field @email to be mandatory with real-time validation` |
| `/create-rule` | Dynamisch gedrag toevoegen | `/create-rule show @spouseInfo if @maritalStatus equals "Married"` |
| `/create-panel` | Formuliersecties ordenen | `/create-panel Employment Details with job title, company, salary fields` |
| `/add-panel` | Ontwerpen converteren | `/add-panel from uploaded form image with field recognition` |
| `/help` | Hulp krijgen | `/help how to implement multi-step validation?` |

### Veldverwijzingen

Gebruik de syntaxis `@fieldName` om te verwijzen naar bestaande velden in uw vragen:

- `@email` - Referentie-e-mailveld
- `@firstName` - Referentie, voornaamveld
- `@maritalStatus` - Referentieveld voor burgerlijke staat

### Componenttypen

**de Componenten van de Input:**

- `text`, `email`, `number`, `tel`, `date`, `checkbox`, `radio`, `dropdown`, `file`, `textarea`

**Componenten van de Container:**

- `fieldset`, `panel`, `repeatable`, `wizard`

### Componenteigenschappen

**Universele Eigenschappen (Alle Componenten):**

- **Type**: Het type van component
- **Naam**: Het herkenningsteken van het gebied voor vormvoorlegging
- **Etiket**: De tekst van de vertoning voor het gebied
- **Beschrijving**: De tekst van de hulp voor het gebied
- **Zichtbaar**: Van Boole voor aanvankelijke zicht
- **Verplicht**: Van Boole voor vereiste gebieden

**Eigenschappen van het Gebied van de Input:**

- **Waarde**: Gebrek/aanvankelijke waarde
- **Placeholder**: De tekst van de tip voor inputgebieden
- **Min**: Minimumwaarde (voor aantallen/data)
- **Max**: Maximumwaarde (voor aantallen/data)

**Dossier uploadt Eigenschappen:**

- **keurt** goed: De types van dossier (.pdf, .doc, .docx, .jpg, .png, enz.)
- **Veelvoud**: Van Boole voor veelvoudige dossierselectie

**Eigenschappen van de Controle van de Selectie:**

- **Opties**: Keuzen voor dropdowns (komma-gescheiden lijst)
- **Gecontroleerd**: Standaard selectie voor checkboxes/radio

**Eigenschappen van de Container:**

- **Veldset**: Groepering verwante gebieden
- **Herhalbaar**: Van Boole voor herhaalbare secties

**Geavanceerde Eigenschappen:**

- **Zichtbare Uitdrukking**: Formule voor voorwaardelijk zicht (=formule)
- **Uitdrukking van de Waarde**: Formule voor berekende waarden (=formule)

### Integratieopdrachten

**legt Acties voor:**

- E-mailmeldingen
- REST API-verzendingen
- Cloudopslag (Azure, SharePoint)
- Workflowautomatisering (Power Automate, Workfront Fusion)
- Marketing platformen (Marketo)
- CRM-integraties

### Richtlijnen voor snelle syntaxis

- **Verwijzingen van het Gebied**: Gebruik `@fieldName` voor bestaande gebieden
- **Bevelen**: Gebruik `/command` voor specifieke acties
- **Natuurlijke Taal**: Beschrijf vereisten duidelijk en specifiek

### Controlelijst voor validatie

Voor uitvoerige beste praktijken en bevestigingsrichtlijnen, zie de [ Begonnen Gids van de Bouwer van de Ervaring van Forms ](forms-ai-assistant-getting-started.md#best-practices).

*Deze snelle bibliotheek wordt onophoudelijk bijgewerkt gebaseerd op gebruiker terugkoppelt en de nieuwe mogelijkheden van de Bouwer van de Ervaring van Forms. Voor de recentste eigenschappen en de voorbeelden, controleer de [ documentatie van AEM Forms ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html).*
