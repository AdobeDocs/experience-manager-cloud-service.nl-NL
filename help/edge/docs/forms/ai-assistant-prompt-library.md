---
title: Forms Experience Builder - Snelle bibliotheek
description: Verzameling van bewezen snelle patronen en voorbeelden voor het bouwen van formulieren met AI-hulp in de gebruikersinterface van Forms Management, de Adaptive Forms Editor en de Universal Editor.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: c8f64082-a23f-4919-ad66-042faad77d31
source-git-commit: 9996bc602ae6169dd1aade622d5dbc5b1addeb54
workflow-type: tm+mt
source-wordcount: '1338'
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

- **Malplaatjes van het Merk** - creeer gestandaardiseerde vormmalplaatjes met de kleuren, de doopvonten, en lay-outpatronen van uw organisatie
- **de Richtlijnen van de Stijl** - bepalen verenigbaar gebied het stileren, knoopontwerpen, en het uit elkaar plaatsen normen
- **Bibliotheek van de Component** - bouw herbruikbare vormcomponenten die uw merkidentiteit aanpassen
- **Visuele Assets** - bereidt logo&#39;s, pictogrammen, en achtergrondelementen voor vormintegratie voor

**Prompt van het Malplaatje van het Voorbeeld:**

```
Create a brand template for financial services forms with:
- Corporate blue (#003366) and silver (#C0C0C0) color scheme
- Open Sans font family for all text
- 16px minimum font size for accessibility
- Consistent 24px spacing between sections
- Corporate logo in header with proper sizing
- Professional button styling with hover effects
```

>[!NOTE]
>
>**Componenten van de Douane**: Controle met uw ontwikkelingsteam over het gebruiken van organisatie-specifieke componenten en hun verenigbaarheid met de Bouwer van de Ervaring van Forms alvorens de elementen van het douanemerk uit te voeren.

>[!NOTE]
>
> Deze snelle bibliotheek is bijgewerkt met de gestroomlijnde mogelijkheden van Forms Experience Builder. Voor sommige geavanceerde integratie- en testfuncties die in voorbeelden worden getoond, is mogelijk aanvullende configuratie vereist.



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

**Stap 2 - voeg Vereiste Gebieden toe:**

```
Add fields for @firstName, @lastName, @email, @phoneNumber with appropriate validation
```

**Stap 3 - voeg BedrijfsLogica toe:**

```
Create a rule: if @age is under 18, show parent/guardian information section
```

**Stap 4 - verbeter met Voorkeur:**

```
Add a preferences panel with @newsletterSubscription, @marketingConsent, @termsAccepted
```

**Stap 5 - voeg Dossier toe uploadt:**

```
Include a file upload field for @profilePicture with size limit of 5MB
```

## Formulier maken en beheren

**wanneer te gebruiken:** wanneer u nieuwe vormen moet creëren of bestaande degenen wijzigen.

**hoe te gebruiken:** kies één van twee benaderingen: creeer van Scratch of de Invoer &amp; zet (zie [ Begonnen Gids ](forms-ai-assistant-getting-started.md#two-ways-to-create-forms)) om.

**Vragen van het Voorbeeld - Eenvoudige Making van de Vorm:**

```
Create a customer feedback form with:
- Product rating (1-5 stars)
- Comment field for detailed feedback
- Customer email (optional)
- Submit to email notification
```

**Vraag van het Voorbeeld - de Complexe Making van de Vorm:**

```
Create a comprehensive employee onboarding form with:

**Personal Information Section:**
- Full name (first, middle, last)
- Date of birth with age validation
- Contact information (email, phone, address)
- Emergency contact details

**Employment Details:**
- Position and department selection
- Start date with business day validation
- Salary information with confidentiality notice
- Reporting structure

**Document Upload:**
- Resume/CV upload (PDF, DOC, DOCX)
- ID verification documents
- Tax forms and banking information
- Signed employment agreement

**Preferences:**
- Benefits selection with cost calculator
- Work schedule preferences
- Training requirements
- Equipment needs

**Validation Rules:**
- Email format validation
- Phone number format validation
- Age must be 18 or older
- All required documents must be uploaded
- Terms and conditions must be accepted

**Submit Actions:**
- Send confirmation email to new employee
- Notify HR department
- Create employee record in HR system
- Schedule orientation meeting
```

**Prompts van het Beheer van de Vorm:**

```
Import this PDF application form and convert it to an adaptive form with enhanced validation
```

```
Update the existing contact form to include social media handles and preferred contact method
```

```
Reorganize the registration form into a 3-step wizard: personal info, preferences, confirmation
```

## Veld beheren en configureren

**wanneer te gebruiken:** wanneer u, vormgebieden moet toevoegen wijzigen of vormen.

**hoe te gebruiken:** ben specifiek over gebiedstypes, bevestigingsregels, en gebruikerservaringsvereisten.

**Vraag van het Voorbeeld - de Basis Toevoeging van het Gebied:**

```
Add a text input field for "Company Name" with placeholder "Enter your company name"
```

**Vraag van het Voorbeeld - Geavanceerde Configuratie van het Gebied:**

```
Add a comprehensive address section with:

**Street Address:**
- Address line 1 (required, max 100 characters)
- Address line 2 (optional, max 100 characters)
- City (required, dropdown with common cities)
- State/Province (required, dropdown)
- Postal code (required, format validation)
- Country (required, default to "United States")

**Validation Rules:**
- Postal code must match state selection
- Address line 1 cannot be empty
- City must be a valid city for selected state

**User Experience:**
- Auto-complete for address fields
- Clear labels and help text
- Mobile-friendly input fields
- Accessibility compliance
```

**Vragen van de Configuratie van het Gebied:**

```
Make @email field required with real-time validation and custom error message
```

```
Add a dropdown for @country with options for USA, Canada, UK, Germany, France, and "Other"
```

```
Configure @phoneNumber field with format (XXX) XXX-XXXX and validation
```

```
Add a file upload field for @resume with PDF and DOC restrictions, max 5MB
```

## Verbeterde slimme velden in LLM

**wanneer te gebruiken:** wanneer u gebieden met pre-bevolkte opties nodig hebt die hefboomwerking de kennisbasis van AI.

**hoe te gebruiken:** gebieden van het Verzoek die uitvoerige gegevensreeksen vereisen - AI kan opties automatisch bevolken gebruikend zijn ingebouwde kennis.

### Geografische en locatievelden

**Luchthavens en Vervoer:**

```
Add a dropdown for departure airports with all major international airports
Add arrival airport field with IATA codes and full names
Create a field for nearest airport to user location
Add a selection of train stations for European cities
```

**Administratieve Gebieden:**

```
Add a complete list of US states with abbreviations
Create a country dropdown with ISO codes and full names
Add a field for major world cities with time zones
Include a dropdown of Canadian provinces and territories
Add a field for UK counties and postal areas
```

### Gegevens voor bedrijven en de industrie

**Classificaties van het Bedrijf:**

```
Add a field for industry classification with NAICS codes
Create a dropdown of business entity types (LLC, Corporation, Partnership, etc.)
Add a field for company size categories (startup, SME, enterprise)
Include department selection for large organizations
Add a field for professional service types
```

**Professionele classificaties:**

```
Add a field for job titles with common industry roles
Create a dropdown of professional certifications by field
Include education levels with degree types
Add a field for years of experience ranges
Create a selection for programming languages and frameworks
```

### Normen en regelgeving

**Financiële en Juridische:**

```
Add a field for currency codes with symbols and exchange rates
Create a dropdown of tax ID types by country
Include a field for legal document types
Add payment method options with security features
Create a selection for banking institutions by country
```

**Technische Normen:**

```
Add a dropdown of file format types with extensions
Include network protocol options
Add a field for database types and versions
Create a selection for API authentication methods
```

### Gezondheidszorg en medische zorg

**Medische Classificaties:**

```
Add a field for medical specialties
Create a dropdown of common medications with generic names
Include a field for insurance provider types
Add a selection for medical emergency contact relationships
Create a field for dietary restrictions and allergies
```

### Intelligentie tijd en kalender

**Datum en de Gebieden van de Tijd:**

```
Add a field for business hours with time zone handling
Create a dropdown of public holidays by country
Include seasonal options with date ranges
Add a field for conference room booking with availability
Create a selection for recurring meeting patterns
```

### Product- en servicecategorieën

**E-commerce Classificaties:**

```
Add a field for product categories with subcategories
Create a dropdown of shipping methods with delivery estimates
Include a field for return policy options
Add a selection for customer priority levels
Create a field for subscription billing cycles
```

**Prompts van het Voorbeeld Slimme Gebied:**

```
"Add a departure airport field with all major airports worldwide including IATA codes and city names"
```

```
"Create a comprehensive industry field using standard NAICS classification with technology subcategories"
```

```
"Include a professional certification dropdown that adapts based on the selected job field"
```

```
"Add an international phone number field that formats based on the selected country"
```

```
"Create a university selection field with major institutions organized by country and ranking"
```

## Regels maken en bedrijfslogica

**wanneer te gebruiken:** wanneer u voorwaardelijke logica, bevestigingsregels, of bedrijfsprocessen moet uitvoeren.

**hoe te gebruiken:** beschrijf duidelijk de bedrijfslogica, specificerend voorwaarden en acties.

**Vragen van het Voorbeeld - Eenvoudige Voorwaardelijke Logische:**

```
Create a rule that shows @spouseInformation panel only when @maritalStatus equals "Married"
```

**Vraag van het Voorbeeld - Complexe BedrijfsRegels:**

```
Implement comprehensive loan application validation:

**Income Validation:**
- If @annualIncome is less than 30000:
  - Show warning message: "Income may be insufficient for requested loan amount"
  - Require additional income documentation
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
Create a **visibility rule** that shows @spouseInformation panel only when @maritalStatus equals "Married" or "Domestic Partnership"
```

```
Add **progressive disclosure** where additional questions appear based on previous answers. Start with basic info, then show relevant follow-ups
```

```
Implement **smart defaults** where @country selection auto-sets related fields. Allow manual override
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

**Vraag van het Voorbeeld - Standaard multi-kanaalverzending:**

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
Connect this form to **CRM system** to create new leads. Map @firstName to FirstName, @email to Email, set LeadSource to "Web Form", and Status to "New"
```

```
Set up **workflow trigger** when form is submitted. Pass all form data and trigger approval workflow with manager notification
```

```
Configure **database integration** to save form submissions as records. Create new folder for each submission with uploaded documents
```

## Bestaande Forms importeren en converteren

**wanneer te gebruiken:** wanneer u bestaande vormen, documenten, of ontwerpen hebt om in moderne vormen van AEM om te zetten.

**hoe te gebruiken:** upload uw brondossier en beschrijf de omzettingsvereisten (zie [ Gids van de Invoer ](forms-ai-assistant-getting-started.md#2-import-and-convert)).

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

Preserve all original field labels and help text, but improve the user experience with modern form interactions
```

**de Herinneringsherinneringen van het Ontwerp:**

```
Import this **design mockup** and convert it into an adaptive form. Maintain the exact visual design but add proper validation and mobile responsiveness
```

```
Analyze this **image of a paper form** and recreate it digitally. Improve the layout for better mobile experience while keeping all mandatory fields
```

```
Convert this **existing HTML form** to AEM adaptive form format. Preserve all functionality but add AEM-specific features like rules and themes
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
```

**mobiel-Specifieke herinneringen:**

```
Make this form **touch-friendly** with larger buttons and simplified navigation for mobile users
```

```
Optimize form for **tablet users** with appropriate field sizes and navigation patterns
```

```
Add **swipe gestures** for multi-step form navigation on mobile devices
```

## Toegankelijkheid en compatibiliteit

**wanneer te gebruiken:** wanneer de vormen toegankelijkheidsnormen (WCAG) of nalevingsvereisten moeten voldoen.

**hoe te gebruiken:** specificeer het vereiste nalevingsniveau en om het even welke specifieke toegankelijkheidseigenschappen nodig.

**Vraag van het Voorbeeld - Basistoegankelijkheid:**

```
Make @contactForm accessible with:

**Basic Accessibility:**
- Proper ARIA labels for all form fields
- Keyboard navigation support
- High contrast color scheme
- Screen reader compatibility
- Focus indicators for all interactive elements
```

**Vraag van het Voorbeeld - Geavanceerde Toegankelijkheid:**

```
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
```

**toegankelijkheid-Specifieke Vragen:**

```
Add **screen reader support** to this form with proper ARIA labels and announcements
```

```
Implement **keyboard navigation** for all form interactions and navigation elements
```

```
Ensure **color contrast** meets WCAG AA standards for all text and interactive elements
```

## Optimalisatie van prestaties

**wanneer te gebruiken:** wanneer de vormen moeten snel laden en goed onder diverse voorwaarden uitvoeren.

**hoe te gebruiken:** specificeer prestatiesvereisten en optimaliseringsstrategieën.

**Vraag van het Voorbeeld - BasisPrestaties:**

```
Optimize @contactForm for performance:

**Loading Optimization:**
- Lazy load non-critical form sections
- Minimize initial bundle size
- Optimize images and assets
- Enable caching for static resources
```

**Vraag van het Voorbeeld - Geavanceerde Prestaties:**

```
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
```

**prestaties-Specifieke Herinneringen:**

```
Optimize form **loading speed** by implementing progressive loading and asset optimization
```

```
Add **auto-save functionality** to prevent data loss during form completion
```

```
Implement **offline support** so users can complete forms without internet connection
```

## Testen en kwaliteit Assurance

**wanneer te gebruiken:** wanneer de vormen uitvoerige het testen nodig hebben om betrouwbaarheid en gebruikerstevredenheid te verzekeren.

**hoe te gebruiken:** specificeer testende scenario&#39;s, bevestigingsvereisten, en kwaliteitsmetriek.

**Vraag van het Voorbeeld - Basis het Testen:**

```
Add comprehensive testing for @contactForm:

**Functional Testing:**
- Test all form field validations
- Verify submit functionality works correctly
- Test error handling and user feedback
- Validate conditional logic and rules
```

**Vraag van het Voorbeeld - het Geavanceerde Testen:**

```
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
```

**test-Specifieke herinneringen:**

```
Add **automated testing** for all form validations and submit functionality
```

```
Implement **user acceptance testing** scenarios for complete form workflows
```

```
Set up **performance monitoring** to track form load times and user interactions
```

## Problemen oplossen

Snelle oplossingen voor algemene Forms Experience Builder-problemen:

| Probleem | Snel repareren |
|-------|-----------|
| Formulier niet verzenden | Configuratie en validatieregels voor verzenden controleren |
| Validatiefouten worden niet weergegeven | Instellingen voor veldvalidatie en plaatsing van foutberichten controleren |
| Problemen met mobiele lay-out | Responsieve ontwerpinstellingen en veldgroottes controleren |
| Geen velden weergegeven | Voorwaardelijke logica en zichtbaarheidsregels controleren |
| Fouten bij importeren | Compatibiliteit en groottebeperkingen van bestandsindelingen controleren |
| Integratiefouten | API-eindpunten en verificatiegegevens valideren |
| Prestatieproblemen | Aantal velden optimaliseren en overbodige validaties verwijderen |
| Toegankelijkheidsproblemen | Veldlabels, ARIA-kenmerken en tabvolgorde controleren |

**zuivert de Herinnering van de Wijze:**

```
Enable debug mode to identify issues with form submission and field validation
```

**Vraag van de Analyse van de Fout:**

```
Analyze form errors: check validation rules, API responses, and user input patterns
```

## Geavanceerde analyses en inzichten

**wanneer te gebruiken:** wanneer u vormprestaties en gebruikersgedrag moet begrijpen.

**hoe te gebruiken:** specificeer de analysevereisten en de vereiste inzichten.

**Vraag van het Voorbeeld - Basis Analytics:**

```
Add analytics to @contactForm:

**Basic Metrics:**
- Form completion rates
- Field abandonment rates
- Submit success/failure rates
- User session duration
```

**Vraag van het Voorbeeld - Geavanceerde Analytics:**

```
Implement comprehensive analytics for @applicationForm:

**User Behavior Analytics:**
- Track field completion rates and abandonment
- Monitor user session duration and patterns
- Analyze form navigation and user flow
- Identify bottlenecks and friction points

**Performance Analytics:**
- Measure form load times and performance
- Track API response times and failures
- Monitor validation rule effectiveness
- Analyze submission success rates

**Business Intelligence:**
- Generate reports on form effectiveness
- Track conversion rates and ROI
- Monitor user satisfaction and feedback
- Identify opportunities for optimization

**Predictive Analytics:**
- Predict form completion likelihood
- Identify users likely to abandon
- Recommend form improvements
- Optimize user experience based on data
```

**Analytics-Specifieke herinneringen:**

```
Add **conversion tracking** to measure form completion rates and user behavior
```

```
Implement **A/B testing** to compare different form designs and optimize performance
```

```
Create **analytics dashboard** to monitor form performance and user insights
```

## Beveiliging en gegevensbescherming

**wanneer te gebruiken:** wanneer de vormen gevoelige gegevens behandelen en veiligheidsmaatregelen vereisen.

**hoe te gebruiken:** specificeer veiligheidseisen en maatregelen van de gegevensbescherming.

**Vraag van het Voorbeeld - Basisveiligheid:**

```
Add security measures to @contactForm:

**Basic Security:**
- HTTPS encryption for all data transmission
- Input validation and sanitization
- CSRF protection for form submissions
- Secure session management
```

**Vraag van het Voorbeeld - Geavanceerde Veiligheid:**

```
Implement comprehensive security for @applicationForm:

**Data Protection:**
- End-to-end encryption for sensitive data
- PII data masking and anonymization
- Secure file upload with virus scanning
- Data retention and deletion policies

**Access Control:**
- Role-based access control for form data
- Multi-factor authentication for admin access
- Audit logging for all data access
- Secure API authentication and authorization

**Compliance:**
- GDPR compliance for data handling
- HIPAA compliance for health information
- PCI DSS compliance for payment data
- SOC 2 compliance for data security

**Monitoring:**
- Real-time security monitoring and alerts
- Intrusion detection and prevention
- Data breach notification systems
- Regular security audits and assessments
```

**veiligheid-Specifieke herinneringen:**

```
Implement **data encryption** for sensitive form submissions and user information
```

```
Add **access control** to restrict form data access based on user roles and permissions
```

```
Set up **security monitoring** to detect and prevent unauthorized access to form data
```

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
| `/configure-submit` | Gegevensverwerking instellen | `/configure-submit to CRM and send confirmation email` |
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
- Marketingplatforms (Marketo)
- CRM-integratie

### Syntaxisrichtlijnen vragen

- **Verwijzingen van het Gebied**: Gebruik `@fieldName` voor bestaande gebieden
- **Bevelen**: Gebruik `/command` voor specifieke acties
- **Natuurlijke Taal**: Beschrijf vereisten duidelijk en specifiek

### Controlelijst voor validatie

Voor uitvoerige beste praktijken en bevestigingsrichtlijnen, zie de [ Begonnen Gids van de Bouwer van de Ervaring van Forms ](forms-ai-assistant-getting-started.md#best-practices).

*Deze snelle bibliotheek wordt onophoudelijk bijgewerkt gebaseerd op gebruiker terugkoppelt en de nieuwe mogelijkheden van de Bouwer van de Ervaring van Forms. Voor de recentste eigenschappen en de voorbeelden, controleer de [ documentatie van AEM Forms ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=nl-NL).*
