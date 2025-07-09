---
title: Overzicht Edge Delivery Services for AEM Forms
description: Edge Delivery Services for AEM Forms is gebouwd voor optimale prestaties, waardoor u de toekomst van gestroomlijnde gegevensverzameling en betrokkenheid van gebruikers kunt inzien.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: bca160763fdd1e96f1350ac74eb76ff7c26ac00b
workflow-type: tm+mt
source-wordcount: '1874'
ht-degree: 0%

---


# Aan de slag met Forms op AEM Edge Delivery Services

<span class="preview"> Dit is een pre-versieeigenschap en toegankelijk door ons [ pre-vrijgavekanaal ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>

Deze handleiding helpt u formulieren te begrijpen en implementeren met Adobe Experience Manager (AEM) Edge Delivery Services (EDS). Of u nu een eenvoudig contactformulier of een complex gereedschap voor gegevensverzameling maakt, op deze pagina worden uw opties weergegeven.

## Forms begrijpen in Edge Delivery Services

Edge Delivery Services is een moderne Adobe-oplossing voor het aanbieden van webinhoud, waaronder formulieren, met uitzonderlijke prestaties en flexibiliteit. Als u Edge Delivery Services voor uw formulieren gebruikt, kunt u:

* **lever Snellere Ervaring:** de lading van Forms laadt ongelooflijk snel omdat zij van een globaal netwerk van randservers (CDNs) dicht bij uw gebruikers worden gediend. Dit verbetert de tevredenheid van de gebruiker en kan de voltooiingssnelheden verhogen.
* **Werk Forms gemakkelijker bij:** de benadering van Edge Delivery Services staat vaak voor snellere ontwikkelingscycli en inhoudsupdates toe, zodat kunt u uw vormen snel aanpassen.
* **bouwt Modern, Responsieve Forms:** creeer vormen die groot kijken en foutloos op om het even welk apparaat werken.
* **Voordeel van Schaalbaarheid en Betrouwbaarheid:** Uw vormen zullen zo robuust en scalable zijn zoals de onderliggende randinfrastructuur.

Deze handleiding zal:

* Beschrijf de verschillende manieren waarop u (auteur) formulieren voor uw Edge Delivery-sites kunt maken.
* Toon u hoe te om te vormen wat gebeurt nadat een gebruiker een vorm (voorleggingsacties) indient.
* Help u de beste methoden te kiezen voor uw specifieke behoeften en teamvaardigheden.
* Zorg voor architectuurdiagrammen en aanbevolen procedures.

## Belangrijke termen die u moet weten

* **Edge Delivery Services (EDS):** Adobe prestaties-eerste architectuur voor het leveren van de inhoud van AEM via CDNs. Ook bekend als Project Franklin.
* **AEM Forms:** oplossing van Adobe voor het creëren van, het leiden van, en de verwerkingsvormen.
* **Universele Redacteur (UE):** Een visuele, redacteur van WYSIWYG voor de inhoud van AEM, met inbegrip van vormen.
* **op document-Gebaseerde Authoring:** Creërend vormen gebruikend Microsoft Word of Google Docs/Sheets.
* **Document Authoring (DA):** Een door Adobe gehoste service voor het schrijven van inhoud (inclusief pagina&#39;s die formulieren kunnen hosten) voor Edge Delivery Services.
* **de Dienst van de Verzending van Forms (FSS):** de dienst van Adobe die het verzenden van vormgegevens naar spreadsheets of e-mail vereenvoudigt.
* **AEM publiceert Instantie:** het levende milieu van AEM dat complexe vormvoorlegging kan verwerken.
* **CORS (het Delen van het Middel van de Cross-Origin):** de eigenschap van de browser van de veiligheid die configuratie wanneer het inbedden van vormen van verschillende domeinen vereist.
* **CDN (het Netwerk van de Levering van de Inhoud):** een netwerk van servers dat Web inhoud snel aan gebruikers levert die op hun geografische plaats wordt gebaseerd.


**Conceptueel Diagram van de Interactie van de Vorm van Edge Delivery Services**

<!--  
```mermaid
graph LR
    User[User on Device] >|Interacts| EdgeForm[Edge-Delivered Form Page]
    EdgeForm >|Loads Instantly| CDN[CDN Edge Server]
    CDN >|Serves Content| User
    EdgeForm >|Submits Data| Backend[Backend Processing - e.g. Forms Submission Service / AEM Publish]
    style User fill:#f9f,stroke:#333,stroke-width:2px
    style EdgeForm fill:#ccf,stroke:#333,stroke-width:2px
    style CDN fill:#9cf,stroke:#333,stroke-width:2px
    style Backend fill:#fca,stroke:#333,stroke-width:2px
``` -->

![ Interactie van de Vorm ](/help/forms/assets/eds-form-interaction.png)
Dit diagram toont een gebruiker die met een vorm interactie aangaat die snel via een CDN wordt geleverd. De gegevens die ze verzenden, worden vervolgens verwerkt door een back-end systeem.

## Hoe werkt Forms op de Edge?

Met EDS kan de inhoud van uw website (inclusief de structuur van uw formulieren) afkomstig zijn van verschillende bronnen, zoals AEM as a Cloud Service, SharePoint, Google Drive of de Document Authoring (DA)-service. Deze inhoud wordt vervolgens gepubliceerd naar een algemene CDN. Wanneer een gebruiker uw site bezoekt, wordt de inhoud rechtstreeks vanaf de dichtstbijzijnde CDN-Edge-server aangeboden, waardoor de maximale snelheid wordt gegarandeerd.

<!--*   **Where AEM Forms Fit In**
    Forms in an EDS architecture are designed to be:
    *   **Fast Loading:** Form structures are often simple HTML rendered client-side.
    *   **Decoupled:** The visual part of the form (frontend) is separate from where the data goes after submission (backend).
    *   **Flexible to Create:** You have different tools to build your forms.
    *   **Configurable for Submission:** You can send data to simple services or powerful AEM backends.-->

**Vereenvoudigde Architectuur van Edge Delivery Services met Forms**

<!--
```mermaid
    graph TD
        UserStart[<img src='https://img.icons8.com/ios-filled/50/000000/user.png' width='30' /> User on Device] >|Interacts| EdgeForm[Edge-Delivered Form Page]
        EdgeForm >|Loads Instantly| CDN[CDN Edge Server]
        CDN >|Serves Content| UserEnd[<img src='https://img.icons8.com/ios-filled/50/000000/user.png' width='30' /> User on Device]
        EdgeForm >|Submits Data| Backend[Backend Processing - Form Submission Service / AEM Publish]

        style UserStart fill:#f9f,stroke:#333,stroke-width:2px
        style UserEnd fill:#f9f,stroke:#333,stroke-width:2px
        style EdgeForm fill:#ccf,stroke:#333,stroke-width:2px
        style CDN fill:#9cf,stroke:#333,stroke-width:2px
        style Backend fill:#fca,stroke:#333,stroke-width:2px
``` -->

![ Architectuur ](/help/forms/assets/eds-simplified-architecture.png)
Dit diagram toont de reis: de formulieren worden bepaald in een auteurssysteem, gepubliceerd aan de rand, aan gebruikers worden gediend, en de voorgelegde gegevens worden verwerkt door een backend.

## De methode voor het schrijven van formulieren kiezen

U hebt drie manieren om formulieren te maken voor uw Edge Delivery Services-sites. Uw keuze hangt af van de vaardigheden van uw team, de complexiteit van het formulier en uw projectbehoeften.

### Welke Authoring-aanpak is geschikt voor u?

Gebruik deze beslissingsstructuur om u te helpen kiezen:

**de Boom van het Beslissingsbesluit van de Authoring van de Vorm**
<!--    
```mermaid
    graph TD
        A{Start: I need to create a form for an Edge Delivery Services site} > B{What are my team's primary content creation tools & skills?}
        B -- "We mainly use Word / Google Docs / Sheets" > C{How complex is the form and where does the data need to go?}
        B -- "We use AEM and prefer visual tools (Marketers or Designers)" > D[Use Universal Editor - WYSIWYG]
        B -- "Our site content is managed in Document Authoring (DA)" > E[Use Document Authoring - Embed Forms]
        C -- "Simple to moderate form, data to a spreadsheet or email" > F[Use Document-Based Authoring]
        C -- "More complex logic or needs AEM backend integration" > D
        E > G[Create form using Document-Based Authoring or Universal Editor, then embed in your DA page]

        style A fill:#f9f,stroke:#333,stroke-width:2px
        style F fill:#ccf,stroke:#333,stroke-width:2px
        style D fill:#ccf,stroke:#333,stroke-width:2px
        style G fill:#ccf,stroke:#333,stroke-width:2px
``` -->

![ Selecterend juiste platform ](/help/forms/assets/eds-authoring-selection.png)

Deze beslissingsstructuur helpt u een ontwerpmethode te selecteren op basis van uw team- en formulierbehoeften.

### Forms maken met documenten (Word/Google Docs)

Deze methode is groot voor snel [ creërend vormen als uw team met Microsoft Word of Google Docs/Sheets ](/help/edge/docs/forms/create-forms.md) comfortabel is.

**hoe het werkt: Van Document aan de Vorm van het Web**

U definieert de velden, labels en typen van uw formulier rechtstreeks in een Word-document of een Google-blad met een speciale tabelindeling of een &quot;Formulierblok&quot;. Wanneer u dit document publiceert, zet Edge Delivery Services het automatisch om in een internetklaar HTML-formulier waarmee gebruikers op uw site kunnen werken.

**Mogelijkheden &amp; Eigenschappen**

* Auteur in vertrouwde gereedschappen: Word, Google Docs, Google Sheets.
* Velden definiëren: tekstinvoer, e-mail, vervolgkeuzelijsten, selectievakjes, keuzerondjes, tekstgebieden.
* Voeg labels, plaatsaanduidingen en Help-berichten toe.
* Standaardvalidatieregels instellen: vereiste velden, e-mailindeling.
* reCAPTCHA integreren voor spambescherming.
* Uploaden van bestanden toestaan
* Direct publiceren: wijzigingen in uw document weerspiegelen zich snel op de livesite.
* Breid met douanecode uit: de gevorderde gebruikers kunnen de componenten van de douanevorm en het stileren via GitHub toevoegen.

**Overwegingen**

* Uw team gebruikt regelmatig Word of Google Docs/Sheets voor inhoud.
* U moet snel eenvoudige tot matig complexe formulieren maken.
* U wilt formuliergegevens rechtstreeks naar een spreadsheet of een e-mailadres verzenden met minimale instellingen.

**hoe de Indieningen werken (hoofdzakelijk de Dienst van de Verzending van Forms)**

Forms creeerde deze manier gewoonlijk [ verzendt hun gegevens naar de Dienst van de Verzending van AEM Forms ](/help/forms/forms-submission-service.md). U configureert dit (vaak in het brondocument zelf) voor het verzenden van gegevens naar een Google Sheet, een Excel-bestand op OneDrive/SharePoint of als e-mail.

**op document-Gebaseerd Authoring Concept**
<!--    
```mermaid
    graph LR
        subgraph Authoring["You define your form in a Google Sheet or Word Document"]
        Sheet[Spreadsheet or Document with field definitions:\nField Name - Type - Label\nemail - email - Email Address\nmessage - textarea - Your Message]
    end

        Sheet >|Edge Delivery Services automatically converts it| JSON[Internal Form Definition as JSON]
    JSON >|A 'Form Block' on your page renders it as| HTMLForm[Live HTML Form on Your Website]

        style Sheet fill:#e6ffe6,stroke:#333
        style JSON fill:#e6e6ff,stroke:#333
        style HTMLForm fill:#ffe6e6,stroke:#333
```-->

![ Gebaseerd op Document ](/help/forms/assets/eds-doc-based.png)
In dit diagram ziet u hoe een formulier dat in een document is gedefinieerd, een live webformulier wordt.

### Forms visueel met Universal Editor

De [ Universele Redacteur ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) biedt een moderne, belemmering-en-dalingsinterface voor de bouw van vormen direct in uw Webbrowser aan.

**hoe het werkt: belemmering-en-Daling de Bouw van de Vorm**

U gebruikt een visuele interface om formuliercomponenten (zoals invoervelden, knoppen en vervolgkeuzelijsten) naar de pagina te slepen. Vervolgens kunt u de eigenschappen van elke component (labels, validatie, enz.) configureren via een deelvenster met eigenschappen. In de Universal Editor ziet u een real-time voorvertoning van uw formulier.

**Mogelijkheden &amp; Eigenschappen**

* Visuele formulieren maken met een bibliotheek van vooraf gebouwde componenten.
* Validatie in real time en bedrijfslogica configureren (bijvoorbeeld velden weergeven/verbergen op basis van selecties).
* Live voorvertoningen weergeven voor verschillende apparaten (voor desktopcomputers en mobiele apparaten).
* Integreer met AEM-functies zoals Content Fragments, AEM Workflows en gebruikersmachtigingen.
* Met de &#39;Experience Builder&#39; kunt u AI-ondersteuning verkrijgen voor het maken of bewerken van formulieren met behulp van aanwijzingen.

**Overwegingen**

* U moet complexe formulieren maken met voorwaardelijke logica, deelvensters met meerdere stappen of personalisatie.
* Uw team (bijvoorbeeld marketers, zakelijke gebruikers) geeft de voorkeur aan visuele hulpmiddelen.
* U hebt een sterke integratie met AEM as a Cloud Service nodig voor bestuur, workflows of het gebruik van AEM-middelen in uw formulieren.

**hoe de Indieningen werken (de Dienst van de Indiening van Forms of AEM publiceren)**

Forms gebouwd met Universal Editor kan:

* Gebruik de eenvoudige [ Dienst van de Verzending van Forms ](/help/forms/forms-submission-service.md) (voor het verzenden van gegevens naar spreadsheets of e-mail).
* Gegevens naar uw AEM-publicatieexemplaar verzenden voor geavanceerdere verwerking (zoals het starten van een AEM-workflow, het gebruik van het formuliergegevensmodel of integratie met andere bedrijfssystemen).

**Universal Editor Concept**

<!--    
```mermaid
    graph TD
    subgraph UE_Interface["Universal Editor Interface in your Browser"]
        Toolbar[Editor Toolbar and Asset Finder]
        Canvas[Your Page with the Form Being Built]
        ComponentPalette[Available Form Components:\nInput / Dropdown / Button\nDrag and drop]
        PropertiesPanel[Configure Selected Component:\nLabel / Validation / Rules]
    end
    ComponentPalette >|Drag & Drop onto| Canvas
    Canvas >|Select a component to edit its| PropertiesPanel
    UE_Interface >|Creates| RenderedForm[Live Form on Your Website]

    style UE_Interface fill:#f0f8ff,stroke:#333
    style RenderedForm fill:#ffe6e6,stroke:#333
```-->

![ Universele Redacteur ](/help/forms/assets/eds-ue-based.png)

Dit diagram toont de belangrijkste delen van de Universele Redacteur die voor vormbouw worden gebruikt.

### Forms gebruiken met Document Authoring (DA)

[ Document Authoring (DA) ](https://www.aem.live/developer/da-tutorial) is een door Adobe gehoste service voor het maken en beheren van uw belangrijkste website-inhoud (pagina&#39;s, artikelen) die via Edge Delivery Services zal worden geleverd. Het is een alternatief voor het gebruik van SharePoint of Google Drive voor uw Edge Delivery Services-broninhoud.

**Begrijpend Document Authoring (DA) voor de Inhoud van Edge Delivery Services**

Document Authoring biedt een professionele ontwerpomgeving met behulp van het Adobe-ontwerpsysteem (Spectrum) en het AEM-documentmodel (Blokken, Secties). Het is ontworpen voor gestructureerd contentbeheer voor EDS.

**hoe DA Forms behandelt (het inbedden, niet Directe Authoring)**

DA zelf is **geen hulpmiddel om vormen van kras te bouwen**. In plaats daarvan, gebruikt u DA om uw Web-pagina&#39;s tot stand te brengen, en dan u *inbedt* vormen (die gebruikend op document-Gebaseerde Authoring of de Universele Redacteur) in die DA-authored pagina&#39;s werden gecreeerd.

**Stappen om Forms in Uw Pagina&#39;s van DA in te bedden**

1. **creeer Uw Vorm:** bouw uw vorm gebruikend één van beiden:
   * Authoring op basis van documenten (Word/Google Docs)
   * Universele editor

1. **publiceer Uw Vorm:** zorg ervoor dit vorm wordt gepubliceerd en via zijn eigen Edge Delivery URL (b.v., `https://your-eds-project.hlx.page/forms/contact-us`) toegankelijk is.
1. **Auteur Uw Pagina in DA:** creeer of geef de pagina in Document Authoring uit waar u de vorm wilt verschijnen.
1. **bedt de Vorm in:** gebruik een specifiek &quot;blok&quot;of een component binnen uw pagina van DA om de vorm van zijn URL van verwijzingen te voorzien en in te bedden. Op de pagina DA wordt dit extern gemaakte formulier opgehaald en weergegeven.

**Document Authoring met Ingesloten Vorm**
<!--
```mermaid
    graph TD
    subgraph FormCreation["1. Create Form using other methods"]
        UE_Form[Universal Editor Form] >|Published to| FormLocation[Form lives at its own Edge Delivery Services URL:\nfor example: /forms/my-contact-form]
        DocBased_Form[Document-Based Form] >|Published to| FormLocation
    end

    subgraph DA_Content["2. Author Page in Document Authoring"]
        DAPage[Your Web Page Authored in DA\nExample: /main-site/landing-page]
        EmbedBlock[On DA Page, add 'Embed Form' Block\nPoints to /forms/my-contact-form]
    end

    DAPage > EmbedBlock
    User[User visits your DA Page] > DAPage
    EmbedBlock >|DA Page fetches and displays| FormLocation[The Form appears on your DA Page]

    style FormCreation fill:#e6ffe6,stroke:#333
    style DA_Content fill:#ffe6cc,stroke:#333
    style FormLocation fill:#ccf,stroke:#333
```-->

![ Document Authoring ](/help/forms/assets/eds-da-based.png)

In dit diagram ziet u dat u eerst een formulier maakt met UE of Docs en het vervolgens insluit in een pagina die u maakt in Document Authoring.


### Ontwerpopties vergelijken

| Criteria | Authoring op basis van documenten | Universele editor (WYSIWYG) | Forms in Document Authoring (DA) |
|----------------------------------|---------------------------------------|-----------------------------------------|-------------------------------------------|
| **Primair Authoring Hulpmiddel** | Word/Google Docs/Sheets | Browser (AEM Universal Editor) | N/A (Forms is *ingebed*) |
| **Niveau van de Vaardigheid van het Team** | Kennis hebben van documenteditors | Compatibel met visuele webgereedschappen | Gebruikt DA voor pagina-inhoud |
| **Typische Complexiteit van de Vorm** | Eenvoudig tot matig | Modern tot complex, op bedrijfsniveau | Afhankelijk van het ingesloten formulier |
| **Optie 1 van de Verzending (Eenvoudig)** | Forms-verzendservice (naar blad/e-mail) | Forms-verzendservice (naar blad/e-mail) | Ingesloten formulier als volgt instellen |
| **Optie 2 van de Verzending (Geavanceerd)** | NVT | AEM-publicatie (workflow, FDM, enz.) | Ingesloten formulier als volgt instellen |
| **AEM Backend Integratie** | Minimaal | Hoog (met publicatie in AEM) | Indirect, via ingesloten Universal Editor-formulier |
| **Best voor...** | Snelle gegevensvastlegging bij het maken van eenvoudige formulieren door inhoudteams. | Marketers, zakelijke gebruikers die behoefte hebben aan visuele controle, complexe formulieren of diepgaande AEM-integratie. | Sites waar de primaire inhoud in DA wordt beheerd, die vormen van andere bronnen vereisen. |

**Verbeterde Beslissingsboom**
<!--
```mermaid
    graph TD
    A{Start Here: I need a form on my Edge Delivery Services Site} > B{What's my team's main authoring tool & skill for form content?};
    B -- "Word/Google Docs" > C{How complex is the form & data destination?};
    C -- "Simple form, data to Sheet/Email" > Sol1[CHOOSE: Document-Based Authoring + Forms Submission Service];
    C -- "Needs more logic OR AEM backend\nlike Workflow or FDM" > Sol2[CONSIDER: Can Universal Editor meet this need better?];

    B -- "AEM User / Visual Editor needed\nMarketer or Designer" > D{Where does the form data need to go?};
    D -- "Simple - to Sheet/Email" > Sol3[CHOOSE: Universal Editor + Forms Submission Service];
    D -- "Advanced - AEM Workflow, FDM,\n3rd Party via AEM" > Sol4[CHOOSE: Universal Editor + AEM Publish Submissions\nRequires additional setup];

    B -- "Our main site content is in Document Authoring (DA)" > Sol5[STRATEGY: Author form using Sol1, Sol2, Sol3 or Sol4 first\nTHEN embed that form into your DA page];

    A > F{Will this form be embedded or fetched from another site or domain?};
    F -- "Yes" > G[IMPORTANT: Configure CORS on the site hosting the form.\nEnsure any form JavaScript blocks are available where the form is displayed];

    style Sol1 fill:#90ee90,stroke:#333
    style Sol2 fill:#fffacd,stroke:#333
    style Sol3 fill:#90ee90,stroke:#333
    style Sol4 fill:#90ee90,stroke:#333
    style Sol5 fill:#add8e6,stroke:#333
    style G fill:#ffb6c1,stroke:#333
```-->

![ Beslissingsboom ](/help/forms/assets/eds-enhanced-decision.png)

## Vergelijking van ontwerpmethoden

In de volgende tabel vindt u een gedetailleerde vergelijking van de belangrijkste functies van de verschillende AEM-methoden voor het schrijven van formulieren. Zo kunt u de meest geschikte aanpak voor uw vereisten kiezen. &#x200B;

| **Capability** | **Universele Redacteur (WYSIWYG)** | **op document-gebaseerde Authoring** | **Document Authoring (DA)** |
|-----------------------------------------|-------------------------------|-----------------------------|-----------------------------|
| **Verenigde Samenstelling met Plaatsen** | ✅ |                              | ✅ (met ingesloten formulieren) |
| **Inbedend de Steun van de Vorm** | ✅ | ✅ | ✅ (Insluiten vanuit Universal Editor of Docs) |
| **Regels (Dynamisch Gedrag)** | Geavanceerde regeleditor met aangepaste functies | Beperkt: tonen/verbergen, waarde berekenen, aangepaste functies | Afhankelijk van ingesloten formulier |
| **Steun van de Bijlage** | ✅ | ℹ️ (Vroege toegang) | Afhankelijk van ingesloten formulier |
| **steun CAPTCHA** | reCAPTCHA Enterprise | reCAPTCHA Enterprise | Afhankelijk van ingesloten formulier |
| **Eigenschappen van de Verzending** | REST, Email, FDM, Workflow, SharePoint, OneDrive, Azure Blob, Power Automate, Workfront Fusion (EA) | Alleen werkblad | Ingesloten formulier als volgt instellen |
| **Schema van Gegevens** | FDM, aangepast | Aangepast | Gebaseerd op ingesloten formulier |
| **pre-fill** | 💡 (via wizard) | ✅ | Afhankelijk van ingesloten formulier |
| **Fragments** | ✅ | ✅ | Afhankelijk van ingesloten formulier |
| **Visuele Redacteur van de Regel** | ✅ |                              |                              |
| **Localization** | 💡 (via sites) | ℹ️ (Excel/Sheets-handleiding) | Afhankelijk van ingesloten formulier |
| **Schema van Gegevens (de Boom van Gegevens)** | 💡 (via UI-extensie) |                              |                              |
| **de Steun van het Malplaatje** | Alleen eerste inhoud |                              |                              |
| **Portaal** |                               |                              |                              |
| **Thema** | ℹ️ (op projectniveau) | ℹ️ (op projectniveau) | ℹ️ (op basis van de hostsite) |
| **Component van de Douane** | ✅ | ✅ | ✅ (als de ingesloten component dit ondersteunt) |
| **OOTB &amp; de Functies van de Douane** | ✅ | ✅ | ✅ (in ingesloten formulier) |
| **Verwijzing van het Fragment** |                               |                              |                              |
| **Integratie van het Teken** |                               |                              |                              |
| **Experimentatie** | ✅ | ✅ | Afhankelijk van de ingesloten context |
| **Het Beheer van de Taak via Workfront** | ✅ |                              |                              |
| **Uitbreiding van Personalization** | 💡 |                              |                              |
| **de Aanpassing van de Redacteur** | ✅ (via UI-extensie) |                              |                              |
| **legt Actie** voor | ✅ | Alleen werkblad | Gebaseerd op ingesloten formulier |

<!--

## Best Practices for Creating Forms

Building great forms goes beyond just the technology. Here's how to ensure your forms are user-friendly and achieve their goals:

* **Designing User-Friendly and Accessible Forms**

  *   **Use Clear, Visible Labels:** Every form field needs a `<label>`. Don't rely only on placeholder text (text inside the input field), as it disappears when users type and is bad for accessibility.
        *   *Good:* `<label for="email">Email Address:</label> <input type="email" id="email" placeholder="you@example.com">`
        *   *Bad:* `<input type="email" placeholder="Email Address">`
  *   **Keep it Simple:** Use standard HTML input types (`<input type="date">`, `<input type="tel">`) where possible. They often have better mobile support and accessibility than complex custom widgets.
  *   **Logical Order and Grouping:** Arrange fields in a way that makes sense to the user. Group related fields together using `<fieldset>` and `<legend>`.
  *   **Provide Clear Instructions:** For any fields that might be confusing, offer concise help text or tooltips.
  *   **Keyboard Navigation:** Ensure users can navigate through your entire form using only the keyboard (Tab, Shift+Tab, Enter, Spacebar).
  *   **Error Handling:** Make errors obvious and easy to correct. Display error messages next to the relevant field and explain what needs to be fixed.

* **Ensuring Your Forms Load Quickly and Are Visible**

  *   **Place Forms Prominently:** If a form is important, make sure users can see it easily without too much scrolling ("above the fold" if possible). Adobe's research shows many forms get low interaction because they are hidden.
  *   **Optimize Assets:** Keep any custom JavaScript or CSS for your forms as small as possible to ensure fast load times. Edge Delivery Services helps with the base page load, but heavy form scripts can still slow things down.

* **Handling User Data Responsibly**
  *   **Ask Only What You Need:** The less Personal Identifiable Information (PII) you ask for, the better. Every field is a potential reason for a user to abandon the form.
  *   **Be Transparent:** Clearly explain *why* you need certain information and *how it will be used*. Link to your privacy policy. This builds trust.

* **Improving User Experience: Captcha Alternatives**

  * **Rethink Visible Captchas:** Those "type the wavy text" or "click all the traffic lights" tests can be very frustrating for users, especially those with disabilities, and often lead to high drop-off rates.

*   **Consider Alternatives:**
    *   **Honeypot Fields:** Add a hidden field that only bots would fill out. If it has data, the submission is likely spam.
    *   **Time-Based Checks:** Measure how quickly a form is submitted. Submissions that are too fast are often bots.
    *   **Invisible reCAPTCHA (v3):** This Google service analyzes user behavior in the background and only presents a challenge if the user seems suspicious. This is often a much better user experience.

**Form Design Do's and Don'ts**

```mermaid
    graph LR
subgraph GoodFormUX [Do ✅ - For Better Forms]
    direction LR
    ClearLabels[Use Visible <label> Tags for All Fields]
    SimpleInputs[Prefer Standard HTML Input Types]
    KeyboardNav[Ensure Full Keyboard Navigation]
    ClearErrors[Show Clear, Actionable Error Messages]
    MinimalPII[Ask Only for Necessary Information]
    TransparentUse[Explain How Data is Used - Privacy Info]
    InvisibleCaptcha[Use Invisible or Behavioral CAPTCHA]
    ProminentPlacement[Make Form Easy to Find on Page]
end

subgraph BadFormUX [Don't ❌ - Avoid These]
    direction LR
    PlaceholderOnly[Only Use Placeholder Text for Labels]
    ComplexWidgets[Use Overly Complex Custom Widgets]
    PoorErrors[Vague or Missing Error Messages]
    ExcessivePII[Request Excessive Personal Data]
    VisibleHardCaptcha[Use Hard-to-Solve Visible CAPTCHAs]
    HiddenForm[Hide the Form Deep in the Page]
end

style GoodFormUX fill:#e6ffe6,stroke:#333
style BadFormUX fill:#ffe6e6,stroke:#333
```

## Quick Decision Guide: Choosing the Right Form Strategy

Let's bring it all together to help you decide on the best approach for your forms.

*   **Matching Form Features to Your Project Goals**
    *   **For speed and simplicity with basic data capture (to spreadsheets/email):** Document-Based Authoring with the Forms Submission Service is often your fastest route.
    *   **For visually rich forms with potential for AEM backend integration:** Universal Editor is your tool. You can start with the Forms Submission Service for simple needs and scale to full AEM Publish submissions for complex workflows.
    *   **If your site content is managed in Document Authoring (DA):** You'll create forms using one of the above methods and then embed them into your DA pages. The submission logic will be tied to how the original embedded form was configured.-->

Om voort te bouwen op wat u hebt geleerd, is hier hoe u zich kunt voortbewegen:

[ kies uw voorleggingsstrategie ](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md) besluit of uw project de eenvoud van de Dienst van de Verzending van Forms (ideaal voor spreadsheet/e-mailoutput) of de flexibiliteit en achterstandsintegratie vereist die door AEM wordt aangeboden publiceert Voorlegt Acties.

Verwijs naar de [ Beste praktijken voor het Creëren van Forms ](/help/edge/docs/forms/universal-editor/best-pratices-eds-forms.md) artikel om te leren hoe te om efficiënte, toegankelijke, en gebruikersvriendelijke vormen te ontwerpen.

## Volgende stappen

Deze handleiding bevat een overzicht van het gebruik van formulieren met AEM Edge Delivery Services. Raadpleeg de officiële documentatie bij Adobe Experience Manager voor gedetailleerde, stapsgewijze instructies over specifieke configuraties:

* [Authoring op basis van documenten met Edge Delivery Services Forms](/help/edge/docs/forms/tutorial.md)
* [Universele editor met Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [ Document Authoring (DA) en het Inbedden Inhoud ](https://www.aem.live/developer/da-tutorial)
* [AEM Forms-verzendservice](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)


<!-- 
# Edge Delivery Services for AEM Forms
 

Edge Delivery Services for AEM Forms is a composable set of services that enables a rapid development environment where authors can update, publish, and launch new forms rapidly. These services deliver exceptional and high impact forms experiences that drive engagement and conversions. These forms experiences are easy to author and develop.

These services enable you to:

* **Create enrolment experiences with tools of your choice:** Increase authoring efficiency by decoupling content sources. Out of the box you can use Document-based Authoring (Microsoft SharePoint or Google Drive), WYSIWYG Authoring (Universal Editor or Adaptive Forms Editor). You can work with multiple content sources on the same forms site and use your preferred authoring tools, such as Microsoft Excel, Google Sheets, Universal Editor, or Adaptive Forms Editor.

* **Deliver exceptional Digital Enrolment experiences:** Deliver Digital Enrolment experiences that load and render quickly and continuously monitor your forms performance through Operational Telemetry. Faster loading times and optimized user experience contribute to higher form completion and conversion rates. 

* **Use developer friendly toolset:** Edge Delivery Services for AEM Forms
 uses plain HTML, modern CSS, and vanilla JavaScript to create exceptional experiences, avoiding the steep learning curve of a specific framework. A developer with basic web development skills can customize and easily build form components and experiences. There is no need to wait for a pipeline to run, just check-in your code into GitHub and your changes are live.

## Edge Delivery Services for AEM Forms Overview {#edge-overview}

Edge Delivery Services for AEM Forms allows for a high degree of flexibility in how you author forms on your website. You can author content and forms with [WYSIWYG Authoring](/help/forms/creating-adaptive-form-core-components.md) as well as [Document-based Authoring](/help/edge/docs/forms/create-forms.md). Edge Delivery Services for AEM Forms
 provide a forms block, known as [Adaptive Forms Block](/help/edge/docs/forms/create-forms.md) to add a form to your Edge Delivery Services site.

For example, you author forms directly in Microsoft Excel or Google Sheets and these spreadsheets are transformed into forms for your website. Any new form or form content, such as a new form field, is instantly available on your website without requiring a rebuild process.

The following diagram illustrates how you can edit forms in Microsoft Excel or Google Sheets (Document-based Authoring) and publish to Edge Delivery Services. It also shows the AEM publishing method using the WYSIWYG Authoring (Universal Editor or Adaptive Forms Editor).

![Publish to Edge Delivery Services and AEM](/help/edge/docs/forms/assets/AEM-forms-with-EDS-publishing.png)

Edge Delivery Services for AEM Forms uses GitHub so customers can manage and deploy code directly from their GitHub repository. For example, you can write forms in either [Google Sheets](/help/edge/docs/forms/create-forms.md) or [Microsoft Excel](/help/edge/docs/forms/create-forms.md) and the components of your forms can be developed by using CSS and JavaScript in a GitHub repository.

When your forms are ready, you can use the [AEM Sidekick](/help/edge/docs/forms/tutorial.md#preview-and-publish-your-content), a chrome browser extension, to preview and publish content updates.

![Install AEM SideKick](/help/edge/assets/aem-sidekick-preview-publish-forms.png)

The choice between the [Document-based Authoring ](#document-based-authoring-features) and [WYSIWYG Authoring](#wysiwyg-authoring-features) depends on your specific requirements:

* For simple forms that just collect basic information with a few fields (think contact us forms, lead generation forms, or service request forms), and where you need quick data connectivity using a spreadsheet, the [Document-based Authoring](#document-based-authoring-features) is a good fit. You can build these forms like you would build a document in Google Sheets or Microsoft Excel. 

* For complex forms, like forms requiring multiple panels, complex rules and business logic, data manipulation, integration with external systems, or streamlined workflows using AEM features, then [WYSIWYG Authoring](#wysiwyg-authoring-features) is a better option. 


### Key Features of Document-based Authoring and WYSIWYG Authoring

Document-based Authoring offers a basic set of features and WYSIWYG Authoring unlocks additional capabilities beyond the Document-based Authoring, empowering you to build more complex and interactive forms. The key features of both Document-based Authoring and WYSIWYG Authoring are:

#### Document-based Authoring features

Document-based Authoring  allows you to create forms using familiar tools like Microsoft Excel or Google Sheets. These forms offer the following functionalities:

* Accessible components for a user-friendly experience.
* Standardized HTML structure for consistent rendering.
* Rules and validations to ensure data accuracy.
* File attachment options for collecting additional information.
* Google reCAPTCHA integration for spam protection.
* Ability to create custom form components for specific needs.
* Submit form data directly to Microsoft Excel or Google Sheets or email addresses.
* Monitor your forms performance through Operational Telemetry

#### WYSIWYG Authoring features

WYSIWYG Authoring provides WYSIWYG interfaces (Universal Editor and Adaptive Forms Editor) for building forms and offers all the capabilities of Document-based Authoring, plus a wide range of additional features:

* Advanced rules editor for creating complex logic.
* Server-side extensibility for custom functionalities.
* WYSIWYG editing experience for easy form creation and visualization.
* Document of record functionality to create tamper-proof archives of submitted data.
* Integration with Adobe Sign for electronic signatures.
* Integration with Adobe Workfront Fusion to triggering Adobe Workfront Fusion scenarios upon form submission.
* Integration with various data sources for pre-populating forms and submitting data.
* Form Data Model (FDM) for defining data structure and interactions with various data sources.
* Ability to choose from multiple submit actions for handling form submissions, including submitting data to Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics, many more data sources.

The all above features are also available via Adaptive Forms Editor. 

In essence, WYSIWYG Authoring (Universal Editor and [Adaptive Forms Editor](/help/forms/creating-adaptive-form-core-components.md)) builds upon the foundation of [Document-based Authoring](/help/edge/docs/forms/create-forms.md), providing a more advanced toolkit for creating and managing complex forms. 

>[!NOTE]
>
>
> The WYSIWYG Authoring capability is available under the early-adopter program. If you are interested, send a quick email from your work address to aem-forms-ea@adobe.com to request access to the capability.

### Edge Delivery Services for AEM Forms

: Authoring, Publishing, and Submission of Forms  

The following diagrams illustrate the process of creating, publishing, and submitting forms using Document-based Authoring and WYSIWYG Authoring.

![Document-based Authoring](/help/edge/assets/document-based-authoring-workflow.png)

![WYSIWYG Authoring](/help/edge/assets/wysiwyg-authoring-workflow.png)

## Start creating forms

* [Get started with Edge Delivery Services for AEM Forms](/help/edge/docs/forms/tutorial.md)
* [Create a form using Google Sheets or Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Set up your Google Sheets or Microsoft Excel files to start accepting data​](/help/edge/docs/forms/submit-forms.md)
* [Publish your form and start collecting data](/help/edge/docs/forms/publish-forms.md)
* [Customize the look of your forms​](/help/edge/docs/forms/style-theme-forms.md)
* [Add repeatable sections to a form​](/help/edge/docs/forms/repeatable-forms.md)
* [Show a custom thank you message after form submission​](/help/edge/docs/forms/thank-you-page-form.md)
* [Adaptive Form Block components and their properties](/help/edge/docs/forms/form-components.md)
* [Real Use Monitoring](https://www.aem.live/developer/rum#authentication)

<!-- 

## Start creating forms

<div>

  <style>
    .card-container {
        width: calc(33.33% - 10px);;
        margin: 5px;
        border: 1px solid #ccc;
        border-radius: 5px;
        padding: 5px;
        box-sizing: border-box;
        transition: background-color 0.3s ease; /* Adding transition effect */
    }
    .card-container:hover {
        background-color: #f0f0f0; /* Changing background color on hover */
    }
</style>

<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: -5px;">
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md">
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="Create a form using Edge Delivery Services forms" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Create a form using Google Sheets or Microsoft Excel</b>
        </a>
        <p>Create forms that load and render quickly and automatically reflows on mobile devices.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Submit form" alt="Use Form Fragments in an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Submit form to spreadsheet</b>
        </a>
        <p>Submit forms directly to your Microsoft Excel or Google Sheets.</p>
    </div>
     <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Apply styles or themes to an Edge Delivery Services form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Customize a theme</b>
        </a>
        <p>Create a consistent brand image by applying the same theme across forms.</p>
    </div>
      <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="Add validations to form fields" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Apply field validations</b>
        </a>
        <p>Reduce errors and frustration by checking form inputs for proper formatting.</p>
    </div> 
            <div class="card-container">
        <a href="/help/edge/docs/forms/rules-forms.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="Use rules to add dynamic behaviour to a form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Use rules to add dynamic behaviour to a form</b>
        </a>
        <p>Reuse preconfigured fragments across multiple forms.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/translate-forms.md">  
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="Translate an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Translate a form</b>
        </a>
        <p>Extend the reach of your forms while keeping costs in check.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Add repeatable sections to an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Add repeatable sections</b>
        </a>
        <p>Effortlessly create and add repeatable sections to a form.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/custom-components-forms.md"> 
            <img src="/help/edge/assets/smock_userdeveloper_18_n.svg" alt="Create custom forms components using standard JavaScript and CSS"  style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Create custom components</b>
        </a>
        <p>Use standard JavaScript and CSS to create components and themes.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/recaptacha-forms.md">  
            <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="Use reCAPTCHA in an Edge Delivery Services Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Use reCAPTCHA</b>
        </a>
        <p>Use OOTB reCAPTCHA integration for robust spam and bot protection.</p>
    </div>


</div>


</br>


-->
