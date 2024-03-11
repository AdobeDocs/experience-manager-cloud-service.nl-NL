---
title: Overzicht AEM Forms Edge Delivery Services
description: AEM Forms-Edge Delivery Services zijn gebouwd voor optimale prestaties, waardoor u de toekomst van gestroomlijnde gegevensverzameling en de betrokkenheid van gebruikers kunt inzien.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
source-git-commit: 67d9eaaf18725403f6a152b04e022cdca6902de0
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 0%

---

# AEM Forms Edge Delivery Services

AEM Forms-Edge Delivery Services zijn een set services die een snelle ontwikkelomgeving mogelijk maken waarin auteurs snel kunnen bijwerken en publiceren en nieuwe formulieren snel kunnen worden gestart.

AEM Forms-Edge Delivery Services bieden buitengewone ervaringen op het gebied van formulieren die betrokkenheid en conversies stimuleren en die een aantrekkelijke ervaring bieden die eenvoudig te ontwerpen en te ontwikkelen is.

Met deze services kunt u:

* **Ervaar zelf welke inschrijvingen u wilt maken met de gereedschappen van uw keuze:** Verhoog de efficiëntie bij het ontwerpen door inhoudsbronnen te ontkoppelen. U kunt zowel op documenten gebaseerde ontwerpfuncties (Microsoft SharePoint of Google Drive) als AEM ontwerpfuncties (Adaptive Forms Editor) gebruiken. Als zodanig kunt u met meerdere inhoudsbronnen werken op hetzelfde formulier en de gewenste ontwerpgereedschappen gebruiken, zoals Microsoft Excel, Google Sheets of de Adaptive Forms Editor.

* **Uitzonderlijke ervaringen met digitaal inschrijven bieden:** Lever Digitale Inschrijving die snel laadt en teruggeeft. Snellere laadtijden en een geoptimaliseerde gebruikerservaring dragen bij tot een hogere snelheid voor het invullen en converteren van formulieren.

* **Gebruik een ontwikkelaarsvriendelijke gereedschapset:** AEM Forms maakt gebruik van onbewerkte HTML, moderne CSS en vanilla JavaScript om uitzonderlijke ervaringen te creëren, waarbij de steile leercurve van een bepaald framework wordt vermeden. Een ontwikkelaar met basisvaardigheden voor webontwikkeling kan formuliercomponenten en -ervaringen aanpassen en eenvoudig bouwen. U hoeft niet te wachten tot een pijplijn wordt uitgevoerd, maar inchecken uw code in Github en uw wijzigingen zijn live.

## Overzicht AEM Forms Edge Delivery Services {#edge-overview}

In het volgende diagram ziet u hoe u formulieren kunt bewerken in Microsoft Excel of Google Sheets (op documenten gebaseerde bewerking) en publiceren naar Edge Delivery Services. Ook wordt de AEM publicatiemethode weergegeven met behulp van de Adaptive Forms Editor.

![Edge Delivery Architecture](/help/edge/assets/AEM-forms-with-EDS-publishing.png)

AEM Forms Edge Delivery-services zijn een set services die samengesteld kunnen worden en die een hoge mate van flexibiliteit mogelijk maken in de manier waarop u formulieren ontwerpt op uw website. U kunt zowel AEM inhoudsbeheer gebruiken met [AEM maken](/help/forms/creating-adaptive-form-core-components.md) alsmede [op documenten gebaseerd schrijven](/help/edge/docs/forms/create-forms.md).

U ontwerpt formulieren bijvoorbeeld rechtstreeks in Microsoft Excel of Google Sheets en deze spreadsheets worden getransformeerd in formulieren voor uw website. Alle nieuwe formulierinhoud, zoals een nieuw formulierveld, is direct beschikbaar op uw website zonder dat u een herbouwingsproces hoeft te ondergaan.

Edge Delivery Services gebruiken GitHub zodat kunnen de klanten code van hun bewaarplaats beheren en opstellen GitHub direct. U kunt bijvoorbeeld formulieren schrijven in [Google Sheets of Microsoft Excel](/help/edge/docs/forms/create-forms.md) en de componenten van uw formulieren kunnen worden ontwikkeld met CSS en JavaScript in GitHub. Wanneer u klaar bent, kunt u de [AEM Sidekick](/help/edge/docs/forms/tutorial.md#preview-and-publish-your-content) browserextensie om updates van inhoud voor te vertonen en te publiceren.

![AEM Sidekick installeren](/help/edge/assets/install-aem-sidekick.png)

AEM Forms-Edge Delivery Services bieden een formulierblok, ook wel bekend als [Adaptief Forms-blok](/help/edge/docs/forms/create-forms.md) om een formulier toe te voegen aan uw site met Edge Delivery Services.

De keuze tussen [op documenten gebaseerd schrijven](#document-based-authoring-features) en [AEM maken](#aem-authoring-features) is afhankelijk van uw specifieke vereisten.

Voor eenvoudige formulieren die alleen basisinformatie verzamelen, zoals namen en e-mails (neem contact met ons op, genereren formulieren voor leads of formulieren voor serviceaanvragen) en wanneer u alleen de gegevens nodig hebt om naar een spreadsheet te gaan, gaat u naar [Authoring op basis van documenten](/help/edge/docs/forms/create-forms.md) is een perfecte pasvorm. U kunt deze formulieren op dezelfde manier maken als een document in Google Docs.

Als uw formulieren complexer worden, zoals het vereisen van meerdere deelvensters, complexe regels en bedrijfslogica, gegevensmanipulatie, integratie met externe systemen of gestroomlijnde workflows met AEM functies, dan [AEM maken](/help/forms/creating-adaptive-form-core-components.md) is een betere optie.


### Belangrijkste kenmerken van op documenten gebaseerde ontwerpen en AEM ontwerpen

Document-based Authoring biedt een basisreeks eigenschappen en AEM Authoring ontgrendelt extra mogelijkheden buiten het document-based authoring, die u machtigt om complexere en interactieve vormen te bouwen. De belangrijkste kenmerken van zowel Document-Gebaseerde Authoring als AEM Authoring zijn:

<!-- 

>[!BEGINTABS]

>[!TAB Document-based authoring]

Document-based authoring is a versatile option suitable for creating simple forms with essential functionalities. It allows you to integrate various input types like text fields, dropdown menus, and radio buttons, enabling you to collect user data effectively. It offers a basic version of rules to add dynamic behaviour to forms. Key features of Document-based authoring are: 

* **[HTML5-based Form Field components](/help/edge/docs/forms/form-components.md)**: AEM Forms Edge Delivery Services allow you to create user-friendly and interactive forms using form components based on HTML5 [input types](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a>, and <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a>  elements. These components cater to different types of data collection and can be easily customized to fit your specific needs.  

* **Accessibility**: The fields in the form block are accessible. Each label is linked with its respective input element, and IDs are auto-generated for linking. Descriptions associated with fields are linked via the aria-describedby attribute. Keyboard navigation using the standard Tab/Shift + Tab keys is supported.

* **[Styling](/help/edge/docs/forms/style-theme-forms.md)**: Each form field has a fixed HTML structure that can be easily decorated using custom CSS or JavaScript files. Selectors for targeting fields in CSS and JS are provided based on type and name. You can easily create new selectors due to the standradized structure and style your form. 

* **Basic Rules**: Easily create logic that adjusts field visibility, validation, and behavior based on user input or predefined conditions. Rules offer a flexible and intuitive way to add intelligence to your forms, ensuring they adapt seamlessly based on user inputs.

* **Validations**: Before submission, the form is validated, and invalid fields are appropriately marked with error messages displayed to the user. Adaptive Forms Block support all the HTML form validation, supported by modern browsers, and provide additional validation mechanism like validation script, file size, file type, overall file size, and more. 

* **File Uploads**: You can add file attachment capabilities to your forms. Whether you need to gather documents, images, or other files from your users, file upload functionality serves you effortlessly. With custom handling options available, you can tailor the file upload process to suit your specific requirements.

* **reCAPTCHA**: Benefit from seamless integration of Google reCAPTCHA into your forms with our out-of-the-box (OOTB) support. Safeguard your forms against fraudulent activities, spam, and abuse, while maintaining a smooth and uninterrupted user experience. Adaptive Forms Block supports reCaptcha V3 and reCaptcha Enterprise. 

* **Send email notification on form submission**: Eliminate the hassle of manual follow-ups and ensure timely communication with our built-in email automation for form submissions. This integrated solution lets you effortlessly notify relevant parties, including sending form data, whenever someone fills out a form on your website. No need for complex configurations or additional tools – it's ready to use out of the box.

>[!TAB AEM Authoring]

AEM Authoring unlocks additional capabilities beyond the document-based authoring, empowering you to build more complex and interactive forms. In additon to the features of Document-based authoring, AEM authoring offers the following additional features:  

* Advanced Rules: Define logic-based actions within your forms. You can use rules to conditionally show or hide form sections, pre-populate fields based on user input, and perform various validations to ensure data integrity.

* Server-side extensibility: Extend the functionalities of your forms by integrating them with server-side logic. This allows you to perform complex calculations, interact with external systems, and automate specific tasks based on user actions within the form.
* Streamline workflows and data management: Leverage the power of AEM to:
    * Design user-friendly forms using AEM editors.
    * Generate a "Document of Record" for secure and tamper-proof archiving of submitted data.
    * Facilitate e-signing with Adobe Sign for a smooth and secure signing experience.
    * Automate business processes through AEM workflows, triggering actions based on form submissions.
    * Effortlessly integrate with various data sources, enabling seamless data flow and exchange.

>[!ENDTABS]



## Start creating forms

-->

#### Ontwerpfuncties op basis van documenten

Met Document-gebaseerde Authoring kunt u formulieren maken met vertrouwde gereedschappen, zoals Microsoft Excel of Google Sheets. Deze formulieren bieden de volgende functies:

* Toegankelijke onderdelen voor een gebruiksvriendelijke ervaring.
* Gestandaardiseerde HTML-structuur voor consistente rendering.
* Regels en validaties om de nauwkeurigheid van de gegevens te garanderen.
* Opties voor bestandsbijlagen voor het verzamelen van aanvullende informatie.
* Google reCAPTCHA-integratie voor spambescherming.
* Mogelijkheid om aangepaste formuliercomponenten te maken voor specifieke behoeften.
* Formuliergegevens rechtstreeks verzenden naar Microsoft Excel of Google-werkbladen of e-mailadressen.

#### AEM ontwerpfuncties

AEM Authoring (met behulp van de Adaptive Forms Editor) biedt een WYSIWYG-interface voor het samenstellen van formulieren en biedt alle mogelijkheden van Document-Based Authoring, plus een groot aantal extra functies:

* Geavanceerde regeleditor voor het maken van complexe logica.
* Uitbreidbaarheid aan de serverzijde voor aangepaste functies.
* WYSIWYG-bewerkingservaring voor het maken en visualiseren van formulieren.
* Document met recordfunctionaliteit om tamper-proof archieven van verzonden gegevens te maken.
* Integratie met Adobe Sign voor elektronische handtekeningen.
* Integratie met Adobe Workfront Fusion om Adobe Workfront Fusion-scenario&#39;s te activeren bij het verzenden van het formulier.
* Integratie met verschillende gegevensbronnen voor het vooraf invullen van formulieren en het verzenden van gegevens.
* Formuliergegevensmodel voor het definiëren van gegevensstructuur en interacties met verschillende gegevensbronnen.
* Mogelijkheid om meerdere verzendacties te configureren voor de verwerking van formulierverzendingen, zoals het verzenden van gegevens naar Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics en nog veel meer gegevensbronnen.

In wezen bouwt AEM Authoring voort op de basis van op documenten gebaseerde authoring, die een geavanceerdere toolkit biedt voor het maken en beheren van complexe formulieren.

### Ontwerpworkflow

![Op documenten gebaseerde ontwerpfuncties](/help/edge/assets/document-based-authoring-workflow.png)

![AEM maken](/help/edge/assets/aem-authoring-workflow.png)


## Formulieren maken

* [Aan de slag met AEM Forms-Edge Delivery Services](/help/edge/docs/forms/tutorial.md)
* [Een formulier maken met Google Sheets of Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Stel uw Google-werkbladen of Microsoft Excel-bestanden in om te beginnen met het accepteren van &#x200B;](/help/edge/docs/forms/submit-forms.md)
* [Uw formulier publiceren en gegevens verzamelen](/help/edge/docs/forms/publish-forms.md)
* [De weergave van uw formulieren aanpassen &#x200B;](/help/edge/docs/forms/style-theme-forms.md)
* [Herhaalbare secties toevoegen aan een &#x200B;](/help/edge/docs/forms/repeatable-forms.md)
* [Een aangepast bedankbericht weergeven na &#x200B; verzenden van formulier](/help/edge/docs/forms/thank-you-page-form.md)
* [Aangepaste componenten van het Blok van de Vorm en hun eigenschappen](/help/edge/docs/forms/form-components.md)



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
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="Create a form using eds forms" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Create a form using Google Sheets or Microsoft Excel</b>
        </a>
        <p>Create forms that load and render quickly and automatically reflows on mobile devices.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Submit form" alt="Use Form Fragments in an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Submit form to spreadsheet</b>
        </a>
        <p>Submit forms directly to your Microsoft Excel or Google Sheets.</p>
    </div>
     <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Apply styles or themes to an eds form" style="border-radius: 5px;"> </b>
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
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="Translate an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Translate a form</b>
        </a>
        <p>Extend the reach of your forms while keeping costs in check.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Add repeatable sections to an EDS Form" style="border-radius: 5px;"> </b>
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
            <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="Use reCAPTCHA in an EDS Form" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Use reCAPTCHA</b>
        </a>
        <p>Use OOTB reCAPTCHA integration for robust spam and bot protection.</p>
    </div>


</div>


</br>


-->