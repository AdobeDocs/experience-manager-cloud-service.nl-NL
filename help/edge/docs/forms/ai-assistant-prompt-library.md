---
title: AEM Forms AI Assistant - Promptbibliotheek
description: Verzameling van bewezen snelle patronen en voorbeelden voor het bouwen van formulieren met AI-hulp in de gebruikersinterface van Forms Management, de Adaptive Forms Editor en de Universal Editor.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: d3ade6ee9216b44b55d6808d8acffe83f1e263c9
workflow-type: tm+mt
source-wordcount: '1613'
ht-degree: 0%

---



# AEM Forms AI Assistant - Promptbibliotheek

Verzameling van herbruikbare snelle patronen en voorbeelden voor algemene scenario&#39;s voor het bouwen van formulieren. U kunt deze sjablonen beschouwen als sjablonen die u aan uw specifieke behoeften kunt aanpassen. In elke sectie wordt een bepaald gebruiksgeval beschreven met aanwijzingen voor het gebruik ervan en beproefde voorbeelden.

>[!NOTE]
>
> De AI Assistant voor AEM Forms is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar mailto:aem-forms-ea@adobe.com om toegang aan te vragen.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze snelle bibliotheek wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De herinneringen, de voorbeelden, en de beste praktijken kunnen veranderen aangezien AI Medewerker voor AEM Forms zich tijdens het vroege adoptieprogramma blijft ontwikkelen.

## Beste praktijken voor Optimale Resultaten

Houd rekening met de volgende tips als u de AI Assistant optimaal wilt benutten:

### Eenvoudig starten, stapsgewijs samenstellen

Begin met kleinere, specifieke opdrachten (bijv. &quot;Voeg tekstinvoer toe voor Voornaam&quot;) in plaats van eerst te complexe meerstapsverzoeken. Deze benadering helpt nauwkeurigheid verzekeren en maakt het gemakkelijker om problemen op te lossen als iets niet zoals verwacht werkt.

**Voorbeeld van Eenvoudig Begin:**

```
Add a text input field for "First Name" with placeholder "Enter your first name"
```

**bouwt dan Stapsgewijs:**

```
Make @firstName mandatory and add validation message "First name is mandatory"
```

### AEM Forms-terminologie gebruiken

Gebruik termen als &quot;paneel&quot;, &quot;tekstinvoerveld&quot;, &quot;checkbox group&quot;, &quot;submit action&quot;, &quot;rule&quot;, enz. voor een beter begrip door de assistent. Zo zorgt u ervoor dat de AI uw verzoeken correct interpreteert binnen de AEM Forms-context.

**Voorkeur Termen:**

- &quot;tekstinvoerveld&quot; in plaats van &quot;tekstvak&quot;
- &quot;checkbox group&quot; in plaats van &quot;checkboxes&quot;
- &quot;dropdown&quot; in plaats van &quot;select list&quot;
- &quot;panel&quot; in plaats van &quot;section&quot; of &quot;container&quot;
- &quot;actie verzenden&quot; in plaats van &quot;formulierverzending&quot;
- &quot;rule&quot; in plaats van &quot;logic&quot; of &quot;condition&quot;

### Referentievelden duidelijk

Gebruik bij het configureren van bestaande velden de notatie @fieldName (bijv. &quot;@firstName verplicht maken&quot;). Hierdoor kan de AI precies bepalen naar welk veld u verwijst, vooral in complexe formulieren met veel velden.

**Voorbeelden:**

- `Make @email mandatory with real-time validation`
- `Show @spouseInfo panel when @maritalStatus equals "Married"`
- `Set @country default value to "United States"`

### Plannen altijd bekijken

Herzie altijd zorgvuldig plannen voor veranderingen die door de medewerker in de Universele Redacteur worden voorgesteld alvorens &quot;van toepassing te klikken.&quot; De AI zal u tonen wat het van plan is te doen - neem een ogenblik om te verifiëren dit uw verwachtingen aanpast.

### Handmatig valideren

Nadat de assistent wijzigingen heeft aangebracht, moet u altijd een voorbeeld van het formulier bekijken en het formulier testen om te controleren of het zich gedraagt en er naar behoren uitziet. AI is een krachtig hulpmiddel, maar definitieve bevestiging is zeer belangrijk om kwaliteit te verzekeren.

**Controlelijst van de Bevestiging:**

- Formulierfunctionaliteit testen in de voorbeeldmodus
- Controleren of voorwaardelijke logica correct werkt
- Mobiele reactiesnelheid controleren
- Indiening van testformulieren
- Toegankelijkheidsfuncties valideren

### Itereren en verfijnen

Als de eerste herinnering niet het nauwkeurige resultaat oplevert, probeer rephrasing of onderdruk het verzoek in kleinere stappen. De AI leert van context, zodat het verstrekken van specifiekere details vaak verbetert resultaten.

**Voorbeeld van de Herhaling:**

1. Eerste poging: &quot;Maak het formulier gebruiksvriendelijk&quot;
2. Verfijnd: &quot;De formulierindeling optimaliseren voor mobiele schermen met een lay-out van één kolom en grotere aanraakdoelen&quot;

### Feedback geven

Gebruik het ingebouwde terugkoppel mechanisme om de medewerker te helpen leren en verbeteren. Uw feedback helpt iedereen een betere AI te geven.


## Voorbeelden van incrementele ontwikkeling

In deze voorbeelden ziet u hoe u stapsgewijs formulieren maakt, eenvoudig begint en geleidelijk complexiteit toevoegt:

### Voorbeeld 1: Een contactformulier stapsgewijs samenstellen

**Stap 1 - Begin Eenvoudig:**

```
Create a basic contact form with name, email, and message fields
```

**Stap 2 - voeg Bevestiging toe:**

```
Make @name and @email mandatory fields with appropriate validation
```

**Stap 3 - verbeter de Ervaring van de Gebruiker:**

```
Add placeholder text: @name "Your full name", @email "your.email@company.com", @message "Tell us how we can help"
```

**Stap 4 - voeg Geavanceerde Eigenschappen toe:**

```
Add a dropdown @inquiryType with options: "General Question", "Support Request", "Sales Inquiry", "Partnership"
```

**Stap 5 - voer Voorwaardelijke Logica uit:**

```
Show @urgencyLevel dropdown (Low, Medium, High) only when @inquiryType equals "Support Request"
```

### Voorbeeld 2: Een registratieformulier stapsgewijs samenstellen

**Stap 1 - Basisstructuur:**

```
Create a user registration form with personal information panel
```

**Stap 2 - voeg de Gebieden van de Kern toe:**

```
Add text input fields: @firstName, @lastName, @email, @phone to the personal information panel
```

**Stap 3 - voeg Bevestiging toe:**

```
Make @firstName, @lastName, and @email mandatory with real-time validation
```

**Stap 4 - voeg de Informatie van de Rekening toe:**

```
Create a new panel "Account Information" with @username and @password fields
```

**Stap 5 - verbeter Veiligheid:**

```
Add password confirmation field @confirmPassword with validation to match @password
```

**Stap 6 - voeg Voorkeur toe:**

```
Create "Preferences" panel with @newsletter checkbox and @communicationMethod radio group (Email, SMS, Phone)
```

Deze incrementele aanpak helpt u:

- Problemen vroegtijdig opvangen voordat ze worden samengesteld
- Elk onderdeel grondig testen
- Aanpassingen maken op basis van feedback van gebruikers
- Betere controle over het ontwikkelingsproces behouden

## Nieuwe Forms starten

**wanneer te gebruiken:** aan het begin van om het even welk vormproject. Deze vraag helpt AI uw vereisten begrijpen en de stichtingsstructuur bouwen.

**hoe te gebruiken:** Begin met basisstructuur en kernvereisten. Geef het formuliertype, het doelpubliek en het primaire doel op. Voeg complexiteit toe aan volgende vragen.

**Vraag van het Voorbeeld - Beginnend Eenvoudig:**

```
Create a **customer onboarding form** for new bank account applications with:

**Purpose:** Collect personal information for account setup
**Target Users:** New customers applying for checking/savings accounts
**Basic Structure:** Single panel with essential fields
**Core Fields:** Name, email, phone, account type selection

Start with a simple layout that we can enhance step by step.
```

**bouwt dan Stapsgewijs:**

```
Add an address panel to @customerOnboardingForm with street address, city, state, and zip code fields
```

```
Add employment information panel with @employer, @jobTitle, and @annualIncome fields
```

```
Add file upload field @identityDocuments for identity verification (Accept: .pdf,.jpg,.png)
```

**Alternatieve Eenvoudige Beginnende Herinneringen:**

```
Create a basic **event registration form** with name, email, and event selection fields
```

```
Build a simple **contact form** with name, email, and message fields
```

```
Design a basic **feedback survey** with rating scale and comments field
```

## Formulierstructuur en indeling

**wanneer te gebruiken:** wanneer u complexe vormen moet organiseren of gebruikerservaring door beter lay-outontwerp verbeteren.

**hoe te gebruiken:** concentreer zich op de gebruikersreis en logische groepering van informatie. Geef layoutvoorkeuren en navigatiepatronen op.

**Vraag van het Voorbeeld - multi-Step Structuur van de Vorm:**

```
Convert this single-page form into a **3-step wizard** with:

**Step 1: Personal Information**
- Name, email, phone, address fields
- Progress indicator showing "Step 1 of 3"
- "Next" button (validate mandatory fields before proceeding)

**Step 2: Preferences & Requirements** 
- Service selection (checkbox group)
- Budget range (dropdown)
- Timeline preferences (radio group)
- Special requirements (text input field)

**Step 3: Review & Submit**
- Summary of all entered information
- Edit links to go back to specific steps
- Terms and conditions checkbox
- Submit button with confirmation

Include "Previous" and "Next" buttons, allow users to jump between completed steps, save progress automatically.
```

**Herinneringsherinneringen van de Lay-out:**

```
Reorganize this form using a **wizard layout** for desktop and single column for mobile. 
```

```
Convert this long form into an **accordion layout** where users can expand/collapse sections.
```

```
Create a **vertical tabbed interface** for this form with tabs for: Basic Info, Contact Details, Preferences, and Review.
```

## Veldbeheer en -validatie

**wanneer te gebruiken:** wanneer u, formuliergebieden met specifieke bevestigingsregels en gedrag moet toevoegen wijzigen of verbeteren.

**hoe te gebruiken:** ben specifiek over gebiedstypes, bevestigingsvereisten, en gebruikerservaringsverwachtingen. Verwijs naar bestaande velden met syntaxis @fieldName.

**Vraag van het Voorbeeld - de Verbetering van het Gebied:**

```
Enhance the form fields with these specific requirements:

**Email Field (@email):**
- Make mandatory with real-time validation
- Show green checkmark when valid format entered
- Display helpful error message: "Please enter a valid email address"
- Add placeholder: "your.email@company.com"

**Phone Number (@phone):**
- Type: tel for mobile optimization
- Make mandatory for business customers, optional for personal
- Add placeholder: "Enter your phone number"

**Date of Birth (@dateOfBirth):**
- Type: date with date picker
- Validate age is 18+ for account opening
- Show error if under 18: "Must be 18 or older to open account"

**File Upload (@documents):**
- Accept: .pdf,.doc,.docx
- Multiple: true for multiple document upload
- Show upload progress and file names after upload
```

**gebied-Specifieke herinneringen:**

```
Add a **file upload field** for resume with these specs: Accept only PDF/DOC/DOCX files, allow multiple files, show upload progress, display file names after upload.
```

```
Create a **dropdown field** for country selection with all countries listed. Set default value based on user's location if available.
```

```
Build a **repeatable panel** for work experience where users can add/remove multiple jobs. Each entry needs: company, title, start date, end date, description.
```

## Voorwaardelijke logica en regels

**wanneer te gebruiken:** wanneer u dynamisch vormgedrag nodig hebt dat op gebruikersinput of bedrijfsregels wordt gebaseerd.

**hoe te gebruiken:** bepaalt duidelijk de voorwaarden en de resulterende acties. Gebruik specifieke veldverwijzingen en logische operatoren.

**Vraag van het Voorbeeld - Complex Voorwaardelijke Logica:**

```
Implement these conditional rules for the application form:

**Business vs Personal Account Logic:**
- If @accountType equals "Business", show:
  - Business name field (mandatory)
  - Tax ID field (mandatory)
  - Business address section
  - Number of employees dropdown
- If @accountType equals "Personal", hide all business fields

**Income-Based Requirements:**
- If @annualIncome is less than 25000:
  - Show additional verification section
  - Make co-signer information mandatory
  - Display message: "Additional documentation may be required"
- If @annualIncome is greater than 100000:
  - Show premium services options
  - Enable priority processing checkbox

**Age-Based Validation:**
- If @age is under 18:
  - Show parent/guardian information section
  - Make parent signature upload mandatory
  - Change submit button text to "Submit for Review"
- If @age is 65 or older:
  - Show senior discount options
  - Add accessibility preferences section
```

**regel-Specifieke herinneringen:**

```
Create a **visibility rule** that shows @spouseInformation panel only when @maritalStatus equals "Married" or "Domestic Partnership".
```

```
Add **progressive disclosure** where additional questions appear based on previous answers. Start with basic info, then show relevant follow-ups.
```

```
Implement **smart defaults** where @country selection auto-sets related fields. Allow manual override.
```

## Gegevensintegratie en -verzending

**wanneer te gebruiken:** wanneer u vormen met achterste deelsystemen, gegevensbestanden, of de externe diensten moet verbinden.

**hoe te gebruiken:** Begin met basisvoorleggingsopstelling, dan voeg extra integratie incrementeel toe. Geef het integratietype, de vereisten voor de gegevensindeling en de voorkeuren voor foutafhandeling op.

**Vragen van het Voorbeeld - Begin met BasisVerzending:**

```
Configure basic form submission for @applicationForm:

**Primary Submission:**
- Send form data to REST endpoint: `/api/v1/applications`
- Format data as JSON
- Show success message: "Application submitted successfully"
- Show error message if submission fails: "Submission failed, please try again"
```

**dan voeg geleidelijk Secundaire Acties toe:**

```
Add email notification to @applicationForm: Send confirmation email to @email address with application reference number
```

```
Add CRM integration to @applicationForm: Create new lead record with @firstName, @lastName, @email, and set Status to "New Application"
```

**Vraag van het Voorbeeld - Geavanceerde multi-kanaalverzending:**

```
Configure form submission with multiple data destinations:

**Primary Submission:**
- Send form data to REST endpoint: `/api/v1/applications`
- Include authentication header with API key
- Format data as JSON with nested objects for address and employment
- Handle success response (201) by showing thank you message

**Secondary Actions:**
- Send notification email to applicant at @email address
- Copy application data to tracking system
- Trigger workflow for approval process
- Create record in CRM with lead status "New Application"

**Error Handling:**
- If primary submission fails, save data locally and retry
- Show user-friendly error message: "Submission temporarily unavailable"
- Provide option to download form data as backup
- Send alert email to admin team about failed submission

**Success Flow:**
- Redirect to confirmation page with application reference number
- Send confirmation email with next steps
- Display estimated processing timeline
```

**integratie-Specifieke herinneringen:**

```
Connect this form to **CRM system** to create new leads. Map @firstName to FirstName, @email to Email, set LeadSource to "Web Form", and Status to "New".
```

```
Set up **workflow trigger** when form is submitted. Pass all form data and trigger approval workflow with manager notification.
```

```
Configure **database integration** to save form submissions as records. Create new folder for each submission with uploaded documents.
```

## Design importeren en omzetten

**wanneer te gebruiken:** wanneer u bestaande vormontwerpen (PDF, Cijfer, beelden) hebt die in de functionele vormen van AEM moeten worden omgezet.

**hoe te gebruiken:** verstrek duidelijke context over het bronontwerp en specificeer om het even welke noodzakelijke wijzigingen of verhogingen.

**Vraag van het Voorbeeld - de Omzetting van de Vorm van PDF:**

```
Convert this uploaded **PDF application form** into a functional AEM adaptive form:

**Source Analysis:**
- Analyze the PDF layout and identify all form fields
- Preserve the visual hierarchy and grouping
- Maintain the professional appearance and branding

**Field Mapping:**
- Convert PDF text fields to adaptive form text inputs
- Transform checkboxes to checkbox components
- Convert dropdown lists to AEM dropdown components
- Map signature areas to digital signature fields

**Enhancements:**
- Add real-time validation that wasn't possible in PDF
- Implement conditional logic for dependent fields
- Make the form responsive for mobile devices
- Add progress saving capability
- Include accessibility improvements (ARIA labels, keyboard navigation)

**Styling:**
- Match the original color scheme and fonts
- Maintain professional business appearance
- Ensure consistent spacing and alignment
- Add subtle animations for better user experience

Preserve all original field labels and help text, but improve the user experience with modern form interactions.
```

**de Herinneringsherinneringen van het Ontwerp:**

```
Import this **design mockup** and convert it into an adaptive form. Maintain the exact visual design but add proper validation and mobile responsiveness.
```

```
Analyze this **image of a paper form** and recreate it digitally. Improve the layout for better mobile experience while keeping all mandatory fields.
```

```
Convert this **existing HTML form** to AEM adaptive form format. Preserve all functionality but add AEM-specific features like rules and themes.
```

## Mobiele optimalisatie en responssnelheid

**wanneer om te gebruiken:** wanneer de vormen op alle apparatentypes en het schermgrootte foutloos moeten werken.

**hoe te gebruiken:** Begin met basis mobiele optimalisering, dan verbetert met geavanceerde eigenschappen. Benadruk mobiele-eerste benadering en specificeer incrementeel breekpuntgedrag.

**Vraag van het Voorbeeld - Begin met Basis Mobiele Optimalisering:**

```
Make @contactForm mobile-friendly with:

**Basic Mobile Layout:**
- Single column layout for all form sections
- Larger touch targets for buttons and inputs
- Responsive design that works on phones and tablets
```

**dan voeg Geavanceerde Mobiele Eigenschappen toe:**

```
Enhance @contactForm mobile experience with:
- Sticky submit button at bottom of screen
- Touch-friendly date pickers
- Swipe gestures for multi-step navigation
```

**Vraag van het Voorbeeld - Uitgebreide mobiel-Eerste Optimalisering:**

```
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

**Touch Optimization:**
- Larger checkbox and radio button targets
- Swipe gestures for multi-step navigation
- Pull-to-refresh for saved drafts
- Touch-friendly date/time pickers

**Performance:**
- Lazy load non-critical form sections
- Optimize images and icons for mobile
- Minimize JavaScript for faster loading
- Progressive enhancement approach
```

**mobiel-Specifieke eenvoudige herinneringen:**

```
Make @checkoutForm mobile-optimized with large buttons and one-thumb navigation
```

```
Add touch-friendly controls to @surveyForm for tablet users
```

```
Enable offline functionality for @applicationForm with local data saving
```

## Toegankelijkheid en compatibiliteit

**wanneer te gebruiken:** wanneer de vormen toegankelijkheidsnormen (WCAG 2.1 AA) of nalevingsvereisten moeten voldoen.

**hoe te gebruiken:** specificeer toegankelijkheidseisen en nalevingsnormen die moeten worden voldaan aan.

**Vraag van het Voorbeeld - de Implementatie van de Toegankelijkheid:**

```
Make this form **WCAG 2.1 AA compliant** with these accessibility features:

**Keyboard Navigation:**
- Logical tab order through all form elements
- Skip links to main content and form sections
- Keyboard shortcuts for common actions
- Focus indicators clearly visible on all interactive elements

**Screen Reader Support:**
- Proper ARIA labels for all form fields
- Descriptive error messages announced to screen readers
- Form section headings with proper hierarchy (h1, h2, h3)
- Progress announcements for multi-step forms

**Visual Accessibility:**
- Color contrast ratio minimum 4.5:1 for text
- Don't rely solely on color to convey information
- Text size minimum 16px for body text
- Scalable up to 200% without horizontal scrolling

**Motor Accessibility:**
- Large click targets (minimum 44x44px)
- Generous spacing between interactive elements
- No time limits or provide extension options
- Alternative input methods support

**Cognitive Accessibility:**
- Clear, simple language in all instructions
- Consistent navigation and layout patterns
- Error prevention and clear error recovery
- Help text and examples for complex fields

**Testing Requirements:**
- Test with screen readers (NVDA, JAWS, VoiceOver)
- Verify keyboard-only navigation
- Check color contrast with automated tools
- Validate HTML for semantic correctness
```

**naleving-Specifieke herinneringen:**

```
Ensure this **healthcare form meets HIPAA requirements** with proper data encryption, audit logging, and privacy controls.
```

```
Make this **financial form PCI DSS compliant** with secure payment field handling and data protection measures.
```

```
Create a **government form meeting Section 508 standards** with full accessibility and plain language requirements.
```

## Testen en kwaliteit Assurance

**wanneer te gebruiken:** wanneer u vormfunctionaliteit, gebruikerservaring, en technische prestaties moet bevestigen.

**hoe te gebruiken:** specificeer het testen scenario&#39;s, randgevallen, en kwaliteitscriteria die moeten worden geverifieerd.

**Vraag van het Voorbeeld - het Uitgebreide Testen van de Vorm:**

```
Create a **comprehensive testing plan** for this application form:

**Functional Testing:**
- Test all field validations with valid and invalid data
- Verify conditional logic shows/hides fields correctly
- Test file upload with various file types and sizes
- Validate calculation fields update correctly
- Test form submission with complete and incomplete data

**User Experience Testing:**
- Test form completion time (target: under 10 minutes)
- Verify error messages are helpful and actionable
- Test progress saving and restoration
- Validate mobile touch interactions
- Check form accessibility with assistive technologies

**Edge Case Testing:**
- Test with extremely long text inputs
- Verify behavior with special characters and emojis
- Test with slow internet connections
- Validate offline functionality if applicable
- Test browser back/forward button behavior

**Performance Testing:**
- Measure form load time (target: under 3 seconds)
- Test with large file uploads
- Verify memory usage with long form sessions
- Test concurrent user submissions
- Validate database performance under load

**Security Testing:**
- Test input sanitization and XSS prevention
- Verify CSRF protection is working
- Test file upload security restrictions
- Validate data encryption in transit and at rest
- Check authentication and authorization controls

**Cross-Browser Testing:**
- Test on Chrome, Firefox, Safari, Edge
- Verify mobile browsers (iOS Safari, Chrome Mobile)
- Test on different operating systems
- Validate older browser fallbacks
- Check print functionality across browsers
```

**test-Specifieke herinneringen:**

```
Create **automated test scripts** for this form's critical user paths: successful submission, validation errors, and conditional logic.
```

```
Design a **user acceptance testing plan** with realistic scenarios and success criteria for business stakeholders.
```

```
Set up **performance monitoring** to track form completion rates, abandonment points, and submission success rates.
```

## Geavanceerde functies en integratie

**wanneer te gebruiken:** wanneer u verfijnde vormmogelijkheden zoals AI hulp, geavanceerde werkschema&#39;s, of complexe integratie nodig hebt.

**hoe te gebruiken:** bepaalt duidelijk de geavanceerde functionaliteit en de integratievereisten.

**Vraag van het Voorbeeld - AI-Verbeterde Vorm:**

```
Add **AI-powered features** to enhance this application form:

**Smart Auto-Complete:**
- Use AI to suggest company names as user types
- Auto-populate address fields from partial input
- Suggest job titles based on industry selection
- Provide intelligent form completion suggestions

**Dynamic Question Generation:**
- Generate follow-up questions based on previous answers
- Adapt form complexity to user's experience level
- Show relevant optional fields based on user profile
- Personalize form sections for different user types

**Intelligent Validation:**
- Use AI to detect potentially incorrect information
- Suggest corrections for common data entry errors
- Validate business information against public databases
- Flag suspicious or inconsistent responses

**Content Optimization:**
- A/B test different form layouts automatically
- Optimize field order based on completion patterns
- Adjust form length based on user engagement
- Personalize help text based on user behavior

**Predictive Analytics:**
- Predict likelihood of form completion
- Identify users who might need assistance
- Suggest optimal times for form completion reminders
- Analyze drop-off points and suggest improvements

**Natural Language Processing:**
- Allow voice input for text fields
- Convert speech to text for accessibility
- Analyze open-text responses for sentiment
- Extract structured data from unstructured input
```

**Geavanceerde Herinneringen van de Integratie:**

```
Integrate with **CRM system** to pre-populate known customer data, update records in real-time, and trigger automated follow-up sequences.
```

```
Connect to **payment gateway** for secure transaction processing with PCI compliance, fraud detection, and multiple payment methods.
```

```
Implement **blockchain verification** for document authenticity, immutable audit trails, and decentralized identity verification.
```

## Problemen oplossen en optimaliseren

**wanneer te gebruiken:** wanneer de vormen prestatieskwesties, gebruikerservaringsproblemen, of technische moeilijkheden hebben.

**hoe te gebruiken:** beschrijf duidelijk het specifieke probleem en het gewenste resultaat.

**Vraag van het Voorbeeld - de Optimalisering van Prestaties:**

```
Optimize this form for **better performance and user experience**:

**Current Issues:**
- Form takes 8+ seconds to load on mobile
- Users are abandoning at the address section (60% drop-off)
- File uploads frequently fail or timeout
- Validation errors are confusing users

**Performance Improvements:**
- Implement lazy loading for non-critical form sections
- Optimize images and reduce bundle size
- Add progressive loading indicators
- Cache frequently used data (country lists, etc.)
- Minimize JavaScript execution time

**User Experience Fixes:**
- Simplify the address section with auto-complete
- Add inline validation with helpful error messages
- Implement smart defaults based on user location
- Add progress saving every 30 seconds
- Provide clear instructions for each section

**Technical Optimizations:**
- Implement chunked file uploads with resume capability
- Add client-side validation before server submission
- Optimize database queries for faster responses
- Implement proper error handling and retry logic
- Add comprehensive logging for debugging

**Monitoring & Analytics:**
- Set up form analytics to track user behavior
- Monitor completion rates by section
- Track error rates and types
- Measure performance metrics continuously
- A/B test improvements with real users
```

**Vragen van het Oplossen van problemen:**

```
**Debug this form submission error:** Users report getting "500 Internal Server Error" when submitting. Check validation logic, server endpoints, and data formatting.
```

```
**Fix mobile layout issues:** Form fields are overlapping on iPhone screens and submit button is not visible. Ensure proper responsive design.
```

```
**Resolve validation conflicts:** Some users can't submit even with valid data. Review validation rules for conflicts and edge cases.
```

## Aanbevolen werkwijzen op milieugebied

### Gebruikersinterface Forms Management

**wanneer te gebruiken:** voor de verwezenlijking van en beheerstaken op hoog niveau van de vorm.

```
In Forms Management UI, create a new **customer survey template** that can be reused across different departments. Include standard branding, common field types, and configurable sections.
```

### Adaptieve Forms Editor

**wanneer te gebruiken:** voor gedetailleerde vormconfiguratie en complexe regelverwezenlijking.

```
In the Adaptive Forms Editor, configure **advanced business rules** for this loan application: calculate debt-to-income ratio, determine eligibility, and show appropriate next steps.
```

### Universele editor

**wanneer te gebruiken:** voor de vormen van Edge Delivery Services met het visuele uitgeven.

```
In Universal Editor, create a **responsive contact form** for the company website. Ensure it matches the site design and integrates with the existing content management workflow.
```

## Handleiding Naslaggids voor opdrachten

| Opdracht | Hoofd-/kleine letters | Voorbeeld |
|---------|---------------|---------|
| `/create-form` | Nieuwe formulieren starten | `/create-form employee onboarding with personal info and benefits selection` |
| `/add-form` | Formulieren toevoegen aan pagina&#39;s | `/add-form newsletter signup with email and preferences` |
| `/update-layout` | De formulierstructuur wijzigen | `/update-layout wizard with 4 steps: info, preferences, review, confirm` |
| `/update-field` | Veldeigenschappen wijzigen | `/update-field @email to be mandatory with real-time validation` |
| `/create-rule` | Dynamisch gedrag toevoegen | `/create-rule show @spouseInfo if @maritalStatus equals "Married"` |
| `/create-panel` | Formuliersecties ordenen | `/create-panel Employment Details with job title, company, salary fields` |
| `/add-panel` | Ontwerpen converteren | `/add-panel from uploaded form image with field recognition` |
| `/configure-submit` | Gegevensverwerking instellen | `/configure-submit to CRM and send confirmation email` |
| `/help` | Hulp krijgen | `/help how to implement multi-step validation?` |

## Verwijzing naar ondersteunde componenteigenschappen

### Universele eigenschappen (alle componenten)

- **Type**: Het type van component (tekst, e-mail, aantal, tel, datum, checkbox, radio, dropdown, dossier, enz.)
- **Naam**: Het herkenningsteken van het gebied voor vormvoorlegging
- **Etiket**: De tekst van de vertoning voor het gebied
- **Beschrijving**: De tekst van de hulp voor het gebied
- **Zichtbaar**: Van Boole voor aanvankelijke zicht
- **Verplicht**: Van Boole voor vereiste gebieden

### Eigenschappen van invoerveld

- **Waarde**: Gebrek/aanvankelijke waarde
- **Placeholder**: De tekst van de tip voor inputgebieden
- **Min**: Minimumwaarde (voor aantallen/data)
- **Max**: Maximumwaarde (voor aantallen/data)

### Eigenschappen van bestanden uploaden

- **keurt** goed: De types van dossier (.pdf, .doc, .docx, .jpg, .png, enz.)
- **Veelvoud**: Van Boole voor veelvoudige dossierselectie

### Eigenschappen van besturingselement Selectie

- **Opties**: Keuzen voor dropdowns (komma-gescheiden lijst)
- **Gecontroleerd**: Standaard selectie voor checkboxes/radio

### Containereigenschappen

- **Veldset**: Groepering verwante gebieden
- **Herhalbaar**: Van Boole voor herhaalbare secties

### Geavanceerde eigenschappen

- **Zichtbare Uitdrukking**: Formule voor voorwaardelijk zicht (=formule)
- **Uitdrukking van de Waarde**: Formule voor berekende waarden (=formule)

## Overzicht van best practices

### Technische richtsnoeren

- **Gebruik slechts gesteunde eigenschappen** van de officiële de componentenspecificatie van AEM Forms
- **volg juiste syntaxis** voor gebiedsverwijzingen (@fieldName) en uitdrukkingen (=formule)
- **Test incrementeel** na elke verandering om kwesties vroeg te vangen
- **Plan voor toegankelijkheid** van het begin, niet als nagedachte
- **overweeg mobiele gebruikers** in elk ontwerpbesluit
- **complexe regels van het Document** voor toekomstig onderhoud en teamsamenwerking

### Strategische aanpak

- **Begin met gebruikersbehoeften** - concentreer zich op wat de gebruikers moeten verwezenlijken, niet alleen technische eigenschappen
- **Ontwerp voor voltooiing** - minimaliseer wrijving en cognitieve lading in vormontwerp
- **de gegevensstroom van het Plan** vroeg - overweeg hoe het gegeven zal worden verwerkt, opgeslagen, en gebruikt
- **Bouw voor schaal** - de vormen van het Ontwerp die verwacht gebruikersvolume en gegevensgroei kunnen behandelen
- **voer progressieve verhoging** uit - verzeker basisfunctionaliteit werkt, dan voeg geavanceerde eigenschappen toe

### Veelvoorkomende valkuilen om te voorkomen

- **Te complexe aanvankelijke verzoeken** - Breek grote taken in kleinere, handelbare stappen
- **Gebruikend niet gesteunde eigenschappen** niet in de specificatie van AEM Forms
- **Negerend mobiele ervaring** tot laat in het ontwikkelingsproces
- **het Overslaan van gebruiker het testen** met echte scenario&#39;s en randgevallen
- **veronderstellend AI begrijpt context** zonder duidelijke, specifieke instructies te verstrekken
- **het vergeten over toegankelijkheid** en nalevingsvereisten
- **bevestigt geen veranderingen** alvorens aan de volgende stap te bewegen

### Assurance-kwaliteitsaanpak

1. **Voorproef vaak** - controleer uw werk op voorproefwijze na elke significante verandering
2. **de randgevallen van de Test** - probeer ongebruikelijke input, lange tekst, speciale karakters
3. **bevestigt over apparaten** - Test op mobiel, tablet, en Desktop
4. **Toegankelijkheid van de Controle** - verifieer toetsenbordnavigatie en de verenigbaarheid van de schermlezer
5. **test van Prestaties** - verzeker vormen snel laden en antwoorden regelmatig
6. **de acceptatietests van de Gebruiker** - hebben echte gebruikers de vorm vóór plaatsing testen


*Deze snelle bibliotheek wordt onophoudelijk bijgewerkt gebaseerd op gebruiker terugkoppelt en nieuwe AI Medewerkingsmogelijkheden. Voor de recentste eigenschappen en de voorbeelden, controleer de [ documentatie van AEM Forms ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html).*
