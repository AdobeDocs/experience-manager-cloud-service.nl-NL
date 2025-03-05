---
title: Universal Editor voor Edge Delivery Services voor Forms
description: Met Universal Editor voor Edge Delivery Services for Forms kunt u Adaptive Forms maken.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: d711e0d1-a2fc-4aa6-af87-6e77a7bc5d2e
source-git-commit: babddee34b486960536ce7075684bbe660b6e120
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 0%

---


# Universal Editor voor Edge Delivery Services voor Forms

<span class="preview"> Deze functie is beschikbaar via het programma voor vroege toegang. Om toegang te verzoeken, verzend een e-mail van uw officieel adres naar <a href="mailto:aem-forms-ea@adobe.com"> aem-forms-ea@adobe.com </a> met uw GitHub organisatienaam en bewaarplaatsnaam. Bijvoorbeeld, als de bewaarplaats URL https://github.com/adobe/abc is, is de organisatienaam adobe en de bewaarplaatsnaam abc.</span>

De Universal Editor zorgt voor een revolutie in het maken van formulieren voor Adobe Edge Delivery Services door een eenvoudige, visuele en intuïtieve What You See Is What You Get-interface (WYSIWYG) aan te bieden. Deze indeling is ontworpen voor makers van inhoud en formulierauteurs en voorkomt de complexiteit van traditionele processen voor het maken van formulieren, waardoor deze zelfs toegankelijk is voor niet-technische gebruikers.

Met de Universal Editor kunt u snel responsieve, interactieve formulieren ontwerpen met vooraf gebouwde componenten, zoals tekstvelden, selectievakjes en keuzerondjes. De robuuste functieset ondersteunt dynamische regels, naadloze gegevensintegratie en geavanceerde personalisatie, zodat elk formulier op maat van uw behoeften is gemaakt.

Of u nu lichtgewicht weergave op de client beheert, compatibiliteit tussen browsers garandeert of voldoet aan strenge toegankelijkheidsnormen, de Universal Editor biedt een gestroomlijnde oplossing voor het maken en beheren van formulieren.

![ Universele Redacteur ](/help/edge/docs/forms/universal-editor/assets/universal-editor.png) {width=80%, richten-centrum}

## Belangrijke functies van de Universal Editor voor Edge Delivery Services for Forms



| ![ Interface van WYSIWYG ](/help/edge/docs/forms/universal-editor/assets/generate-forms.svg) | ![ Redacteur van de Regel ](/help/edge/docs/forms/universal-editor/assets/rule-editor.svg) | ![ legt Acties ](/help/edge/docs/forms/universal-editor/assets/submit-actions.svg) voor |
|:-------------:|:-------------:|:-------------:|
| [**Interface van WYSIWYG**](/help/edge/docs/forms/universal-editor/universal-editor-user-interface.md) | [**Redacteur van de Regel**](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md) | [**legt Acties**](/help/edge/docs/forms/universal-editor/submit-action.md) voor |
| De Universal Editor biedt een WYSIWYG-interface voor formulierontwerp met een vooraf gebouwde componentbibliotheek, een responsief ontwerp, een op een sjabloon gebaseerd ontwerp en realtime veldwijzigingen. | Met de regeleditor kunnen gebruikers dynamische formulierinteracties maken aan de hand van gebeurtenisgestuurde regels, directe validatie en foutafhandeling via lichtgewichtJavaScript en JSON. | Verstuur Acties steunen achterste integratie, voorwaardelijke voorleggingslogica, veilige eindpunten, en pre-bewerkers, stroomlijnend voorleggingswerkschema&#39;s. |

| ![ het Publiceren/Unpublishing ](/help/edge/docs/forms/universal-editor/assets/publish-unpublish.svg) | ![ Responsieve Wijze ](/help/edge/docs/forms/universal-editor/assets/responsive.svg) | ![ de Componenten van de Douane ](/help/edge/docs/forms/universal-editor/assets/custom-components.svg) |
|:-------------:|:-------------:|:-------------:|
| [**het Publiceren/Unpublishing**](/help/edge/docs/forms/universal-editor/publish-forms.md) | [**Responsieve Wijze**](/help/edge/docs/forms/universal-editor/responsive-layout.md) | [**de Componenten van de Douane**](/help/edge/docs/forms/universal-editor/create-custom-component.md) |
| U kunt gemakkelijk de zichtbaarheid van uw formulieren bepalen door de formulieren te publiceren of de publicatie ervan rechtstreeks vanuit de editor ongedaan te maken met slechts een paar klikken. | Formulieren ontwerpen die zich naadloos aanpassen op verschillende apparaten (desktops, tablets en mobiele apparaten). In de responsieve modus kunt u formulieren voor verschillende schermgrootten voorvertonen en testen. | Met aangepaste componenten kunnen ontwikkelaars de formuliermogelijkheden uitbreiden door unieke elementen te maken die zijn afgestemd op specifieke gevallen van organisatiegebruik. |

| ![ het Stijlen ](/help/edge/docs/forms/universal-editor/assets/personalization.svg) | ![ prefill de Diensten ](/help/edge/docs/forms/universal-editor/assets/prefill-services.svg) | ![ het Testen A/B ](/help/edge/docs/forms/universal-editor/assets/experimentation-ab-testing.svg) |
|:-------------:|:-------------:|:-------------:|
| [**het Stijlen**](/help/edge/docs/forms/universal-editor/style-theme-forms.md) | **prefill de Diensten** (Binnenkort komend) | [**het Testen A/B** ](https://github.com/adobe/aem-experimentation/blob/main/documentation/experiments.md) |
| Met CSS opmaken kunnen ontwikkelaars de weergave van formulierelementen aanpassen en een visueel aantrekkelijk ontwerp maken dat wordt uitgelijnd op de esthetiek van de website. | Pre-fill Services vult formuliervelden automatisch met relevante gebruikersgegevens uit verschillende bronnen, waardoor de handmatige invoer wordt verminderd en de gebruikerservaring wordt verbeterd. | Met A/B-tests kunnen organisaties experimenteren met verschillende formulierontwerpen, indelingen en functies om de best presterende varianten te identificeren. |

| ![ Analytics &amp; het Volgen ](/help/edge/docs/forms/universal-editor/assets/analyticsandtracking.svg) | ![ Fragmenten van de Vorm ](/help/edge/docs/forms/universal-editor/assets/form-fragments.svg) | ![ Gegevens die ](/help/edge/docs/forms/universal-editor/assets/data-binding.svg) binden |
|:-------------:|:-------------:|:-------------:|
| [**Analytics &amp; het Volgen** ](https://www.aem.live/developer/martech-integration) | **Fragmenten van de Vorm** (Binnenkort komend) | **Gegevens die** binden (Binnenkort komt) |
| Bekijk meer inzicht in gebruikersgedrag, formulierinteracties en verzendingssnelheden met ingebouwde analyses en tracering om gegevensgestuurde optimalisatie van formulieren mogelijk te maken. | Met formulierfragmenten kunt u hergebruik mogelijk maken door veelgebruikte secties één keer te maken en opnieuw te gebruiken in meerdere formulieren. Dit zorgt voor consistentie en vermindert de onderhoudsinspanning. | Gegevensbinding maakt directe verbindingen mogelijk tussen formuliervelden en achterwaartse gegevensbronnen, met ondersteuning voor realtime updates en geavanceerde gegevenstoewijzing. |

| ![ CAPTCHA ](/help/edge/docs/forms/universal-editor/assets/captcha.svg) | ![ Inbeddend Forms ](/help/edge/docs/forms/universal-editor/assets/embedding-forms.svg) | ![ Dank u Configuratie ](/help/edge/docs/forms/universal-editor/assets/thank-you.svg) |
|:-------------:|:-------------:|:-------------:|
| [**CAPTCHA**](/help/edge/docs/forms/universal-editor/recaptcha-forms.md) | **Inbeddend Forms** (Binnenkort komend) | [**Dank u Configuratie**](/help/edge/docs/forms/universal-editor/submit-action.md#show-a-custom-thank-you-message-on-adaptive-form-submission-submit-action-message-ue) |
| Gebruik reCAPTCHA om formulieren te beschermen tegen geautomatiseerde bots, zodat u verzekerd bent van een veilige en betrouwbare gegevensverzameling. | U kunt formulieren rechtstreeks insluiten in Edge Delivery Services-sitepagina&#39;s met de ingebouwde insluitcomponent van de Universal Editor. | Pas eenvoudig het bevestigingsbericht of de pagina aan die aan gebruikers na succesvolle vormverzending worden getoond. |


<!-- ![Universal Editor](/help/edge/docs/forms/universal-editor/assets/generate-forms.svg)  **WYSIWYG interface for Form creation**: Universal Editor provides a WYSIWYG interface for form design. It provides pre-built component library, responsive design support, and template-based form creation. You can instantly add or remove form fields and modify field properties (like label, data binding, validation). You can also plugin custom form components to Universal Editor.


* **Rule editor**: The rule editor stands out as a powerful mechanism for creating sophisticated form interactions. It supports event-driven rules, instant validation, and error handling through lightweight JavaScript and JSON-based definitions. This allows developers to implement complex form logic, such as conditional field visibility, automatic calculations, and dynamic form behaviour without extensive coding.

* **Submit actions**: Submit Actions enable form submission workflows. These actions provide comprehensive backend integration options, supporting protocols like REST API. The system allows you configure data pre-processors for automatic data transformation, conditional submission logic based on form field values, and secure endpoint connections. Organizations can define complex submission rules that validate data, and manage form responses with granular control.

* **Pre-fill services:** Pre-fill Services enhance user experience by intelligently populating form fields with relevant data. These services connect to various data sources, including user profiles, browser local storage, and external databases. The mechanism supports dynamic data population, enabling automatic completion of form fields based on contextual information. Users benefit from reduced manual data entry, while administrators gain flexibility in configuring pre-fill rules across different form types and scenarios. The pre-fill functionality adapts to different authentication methods, including session-based approaches and token-based systems, ensuring both convenience and security.

* **Data binding capabilities**: Data binding in the Universal Editor enables direct, dynamic connections between form fields and backend data sources. This feature allows real-time synchronization of form data, supporting complex data mapping scenarios. The system supports transforming form inputs into structured database records with minimal configuration. Advanced mapping supports nested data structures, allowing complex form designs to interact seamlessly with intricate data models.

* **Internationalization/localization capabilities**: Internationalization support ensures global accessibility, with multi-language rendering, right-to-left language compatibility, and locale-specific formatting.

* **Analytics and tracking mechanisms**: The built-in analytics and tracking mechanisms provide comprehensive insights into form interactions, submission rates, and user behavior, enabling continuous optimization of form design and performance. 

* **Experimentation (A/B Testing)**: The Universal Editor supports experimentation by allowing organizations to run A/B tests on form designs to identify the best-performing layouts or features.

* **Task Management via Adobe Workfront**: Integration with Adobe Workfront allows teams to manage tasks related to form creation and maintenance, ensuring streamlined collaboration and efficient workflows.

* **Editor Customization via UI Extension**: Developers can extend the functionality of the Universal Editor through UI extensions, enabling tailored solutions that fit specific organizational needs. -->

## Vooraf gebouwde formuliercomponenten

De Universal Editor biedt de volgende formuliercomponenten uit het vak:

<table>
  <thead>
    <tr>
      <th></th> 
      <th>Formuliercomponenten</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="22"><img src="/help/edge/docs/forms/universal-editor/assets/adaptive-forms-components.png" alt="Formuliercomponenten" style="width: 100%;"></td> 
      <td><b>Accordeon</b></td>
      <td>Inklapbare deelvensterstructuur voor het ordenen van inhoud.</td>
    </tr>
    <tr>
      <td><b>Knop</b></td>
      <td>Hiermee voegt u interactieve elementen toe voor handelingen zoals navigatie of aangepaste logica.</td>
    </tr>
    <tr>
      <td><b>Captcha</b></td>
      <td>Hiermee voorkomt u spam door van gebruikers te verlangen dat ze een verificatietaak voor mensen uitvoeren met Google reCaptcha of HCaptcha.</td>
    </tr>
    <tr>
      <td><b>Selectievakje</b></td>
      <td>Hiermee kunnen gebruikers een selectievakje configureren.</td>
    </tr>
    <tr>
      <td><b>Groep selectievakjes</b></td>
      <td>Hiermee kunnen gebruikers meerdere opties in een groep selecteren.</td>
    </tr>
    <tr>
      <td><b>Datumkiezer</b></td>
      <td>Hiermee kunnen gebruikers een datum selecteren via een kalenderinterface.</td>
    </tr>
    <tr>
      <td><b>Vervolgkeuzelijsten</b></td>
      <td>Biedt opties voor één of meerdere selecties in een vooraf gedefinieerde lijst.</td>
    </tr>
    <tr>
      <td><b>E-mail</b></td>
      <td>Hiermee legt u e-mailadressen vast met validatie van de basisindeling.</td>
    </tr>
    <tr>
      <td><b>Bestandsbijlage</b></td>
      <td>Hiermee kunt u documenten, afbeeldingen of andere bestandstypen uploaden.</td>
    </tr>
    <tr>
      <td><b>Formulierfragmenten</b></td>
      <td>Herbruikbare formuliercomponenten voor secties zoals adresvelden of contactgegevens.</td>
    </tr>
    <tr>
      <td><b>Afbeelding</b></td>
      <td>Ondersteunt het uploaden en weergeven van afbeeldingen in formulieren.</td>
    </tr>
    <tr>
      <td><b>Modal</b></td>
      <td>Hiermee geeft u een pop-upvenster weer dat vaak wordt gebruikt voor waarschuwingen, aanvullende informatie of bevestiging.</td>
    </tr>
    <tr>
      <td><b>Numeriek veld</b></td>
      <td>Hiermee legt u numerieke invoer vast, zodat getallen of bereiken kunnen worden gevalideerd.</td>
    </tr>
    <tr>
      <td><b>Deelvenster</b></td>
      <td>Hiermee ordent u formuliersecties met uitbreidbare/inklapbare deelvensters.</td>
    </tr>
    <tr>
      <td><b>Keuzerondjes</b></td>
      <td>Hiermee schakelt u selectie van één keuze uit een groep opties in.</td>
    </tr>
    <tr>
      <td><b>Classificatie</b></td>
      <td>Hiermee kunnen gebruikers een score opgeven die op sterren is gebaseerd.</td>
    </tr>
    <tr>
      <td><b>Knop Opnieuw instellen</b></td>
      <td>Hiermee herstelt u de standaardstatus van de formuliervelden.</td>
    </tr>
    <tr>
      <td><b>Verzendknop</b></td>
      <td>Hiermee activeert u het verzenden van formulieren en start u gedefinieerde workflows.</td>
    </tr>
    <tr>
      <td><b>Veld telefoonnummer</b></td>
      <td>Hiermee legt u telefoonnummers vast met opmaak op basis van land.</td>
    </tr>
    <tr>
      <td><b>Tekst</b></td>
      <td>Verstrekt een specifieke sectie voor het tonen van wettelijke termijnen en het verzamelen van gebruikersovereenkomst door checkboxes.</td>
    </tr>
    <tr>
      <td><b>Tekstveld</b></td>
      <td>DCaptures invoer op één regel, zoals namen of e-mailadressen.</td>
    </tr>
    <tr>
      <td><b>Wizard</b></td>
      <td>Hiermee begeleidt u gebruikers stapsgewijs door een formulierproces met meerdere onderdelen.</td>
    </tr>
  </tbody>
</table>

<!-- * Footer: Adds a footer section for consistent design or additional information.
* Form Container: Wraps all form elements and manages overall form properties.
* Header: Adds a header section for form titles, branding, or instructions.-->
<!-- * 
* Prefillable Fields: Automatically populates form fields with data from predefined sources such as user profiles or APIs. 

* Switches/Toggle Buttons: Provides binary on/off choices for user input.


* Title: Adds a text-based heading or label to improve form clarity and organization.


In-addtion to pre-built form components, the Universal editor also provides support for:

* **Embedding Forms in Another Webpage**: The Universal Editor supports embedding forms directly into Edge Deliver Services Sites pages. This can be done using the embed component provided out of the box.

* **Validation Messages**: Validation messages provide real-time feedback to users when they enter incorrect or incomplete data. Features include:
    * Dynamic Error Display: Instantly alerts users to errors, such as invalid email addresses or missing required fields.
    * Customizable Messages: Allows form authors to define user-friendly error texts.
    * Rule-Based Validation: Supports advanced validation logic, such as checking dependencies between fields or implementing conditional rules.

* **Hidden Fields**: Hidden fields store data invisibly within the form, often for backend processing or prefilled values. Use cases include:
    * Passing contextual information (e.g., user ID or session data) to the backend without displaying it to users.
    * Capturing metadata like timestamps or tracking IDs.
    * Hidden fields are not visible to end-users but can be prefilled, updated dynamically, or used in workflows.

* **Custom Components**: Custom components allow developers to extend the functionality of forms by creating specialized or third-party integrations. Features include:
    * Flexibility: Developers can design unique form elements tailored to specific use cases.
    * Third-Party Integration: Embed widgets or tools like payment gateways, analytics trackers, or AI-driven input fields.
    * Seamless Compatibility: Custom components can integrate with the Universal Editor's drag-and-drop interface and existing features like data binding or validation.

* **Thank you Configuration**: Customize the acknowledgment message or page shown after form submission.
-->


## Onboarding

Om de Universele Redacteur en zijn geavanceerde eigenschappen zoals de Redacteur van de Regel toe te laten schrijven aan ons bij aem-forms-ea@adobe.com van uw officiële e-mailidentiteitskaart Het Adobe-team is hier om u te helpen bij het transformeren van uw ervaring op het gebied van formulieropbouw.

## Veelgestelde vragen (FAQ)

**Q. Wie kan de Universal Editor gebruiken?**
De Universal Editor is ontworpen voor een breed publiek, waaronder:

* Inhoudsmakers die visueel aantrekkelijke formulieren willen maken.
* Ontwikkelaars die geavanceerde mogelijkheden voor aanpassing en integratie nodig hebben.
* Organisaties die op zoek zijn naar schaalbare, veilige en compatibele formulieroplossingen.

**Q: Kan ik vormen integreren die met de Universele Redacteur in mijn bestaande systemen worden gecreeerd?**
Absoluut. De Universele Redacteur steunt naadloze gegevensband met achterste systemen, toelatend updates in real time en geavanceerde gegevensafbeelding. De toepassing kan ook worden geïntegreerd met hulpmiddelen zoals Adobe Workfront voor taakbeheer en ondersteunt veilige eindpunten voor workflows voor gegevensverzending.

**Q: Is het mogelijk om de vormcomponenten aan te passen?**
Ja, de Universele Redacteur staat ontwikkelaars toe om douanecomponenten tot stand te brengen die aan specifieke organisatorische behoeften worden aangepast. Daarnaast kunt u de functionaliteit van de editor uitbreiden via UI-extensies en aangepaste workflows.

**Q: Hoe behandelt de Universele Redacteur toegankelijkheid?**
De Universal Editor is ontworpen met strikte naleving van toegankelijkheidsstandaarden, waaronder WCAG (Web Content Accessibility Guidelines). Dit zorgt ervoor dat de formulieren bruikbaar zijn voor personen met een handicap, en zorgt voor een inclusieve ervaring.

**Q: Welk soort analyses kan ik van de vormen krijgen?**
De Universele Redacteur omvat ingebouwde analytische en het volgen hulpmiddelen om gebruikersinteractie, vormverzendingssnelheden, en omzettingsmetriek te controleren. Deze inzichten helpen uw formulieren te optimaliseren voor betere prestaties.


## Formulieren maken

{{universal-editor-see-also}}

