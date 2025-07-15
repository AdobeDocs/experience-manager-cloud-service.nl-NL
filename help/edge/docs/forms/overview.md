---
title: Overzicht Edge Delivery Services for AEM Forms
description: Creëer en lever hoogwaardige formulieren op Adobe Experience Manager Edge Delivery Services, met de nadruk op de Universal Editor-ontwerpaanpak.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: 37b20a97942f381b46ce36a6a3f72ac019bba5b7
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 0%

---


# Edge Delivery Services voor AEM Forms


Edge Delivery Services for AEM Forms is een set services die een snelle ontwikkelomgeving mogelijk maakt waarin auteurs snel nieuwe formulieren kunnen bijwerken, publiceren en lanceren. Deze services bieden buitengewone en zeer belangrijke vormen van ervaring die de betrokkenheid en conversies stimuleren. Deze formulieren zijn gemakkelijk te ontwerpen en te ontwikkelen.

Met deze services kunt u:

* **creeer inschrijvingservaringen met hulpmiddelen van uw keus:** verhoog auteursefficiency door inhoudsbronnen te ontkoppelen. U kunt in het vak Document-based Authoring (Microsoft SharePoint of Google Drive), WYSIWYG Authoring (Universal Editor of Adaptive Forms Editor) gebruiken. U kunt met meerdere inhoudsbronnen werken op dezelfde formuliersite en de gewenste ontwerpgereedschappen gebruiken, zoals Microsoft Excel, Google Sheets, Universal Editor of Adaptive Forms Editor.

* **Lever uitzonderlijke Ervaringen Digitale Inschrijving:** Lever de Ervaringen van de Inschrijving Digitale die en snel en onophoudelijk uw vormprestaties door Operationele Telemetrie laden en teruggeven controleren. Snellere laadtijden en een geoptimaliseerde gebruikerservaring dragen bij tot een hogere snelheid voor het invullen en converteren van formulieren.

* **ontwikkelaarsvriendelijke toolset van het Gebruik:** Edge Delivery Services voor AEM Forms
maakt gebruik van gewone HTML, moderne CSS en vanilla JavaScript om uitzonderlijke ervaringen te creëren, waarbij de steile leercurve van een specifiek framework wordt vermeden. Een ontwikkelaar met basisvaardigheden voor webontwikkeling kan formuliercomponenten en -ervaringen aanpassen en eenvoudig bouwen. Er is geen behoefte om op een pijpleiding te wachten om te lopen, enkel controle-binnen uw code in GitHub en uw veranderingen zijn levend.

## Een ontwerpmethode kiezen


Met Adobe Experience Manager (AEM) Edge Delivery Services (EDS) kunt u vanaf de rand genieten van supersnelle, zeer schaalbare webbeleving. Deze gids verklaart **hoe te om vormen voor die ervaringen** te bouwen en te publiceren—met een duidelijke aanbevelingshiërarchie:

* **Universele Redacteur (UE) - Beste keus voor de meeste teams**
* **document-Gebaseerde Authoring (Docs/Sheets) - Uitstekend voor snelle, eenvoudige vormen**
* **Document Authoring (DA) - Gebruik om formulieren in te sluiten in pagina&#39;s die met DA zijn geschreven**

Tegen het einde kunt u de juiste ontwerpmethode kiezen, de verzendopties begrijpen en de volgende stappen volgen in de richting van formulieren die klaar zijn voor productie.


| Team en vereisten | Aanbevolen methode | Waarom |
|--------------------|--------------------|-----|
| Marketers/Ontwerpers hebben visuele controle, voorwaardelijke logica of AEM-integratie nodig | **Universele Redacteur** | Slepen en neerzetten, geavanceerde regels, verzenden naar publicatie in FSS of AEM |
| Inhoudsauteurs die al werken in Word / Google Docs / Sheets; eenvoudige gegevensvastlegging naar spreadsheet/email | **op document-Gebaseerde Authoring** | Vertrouwde gereedschappen, snelste pad voor basisformulieren |
| De pagina&#39;s van de website die in **Document Authoring (DA)** worden gebouwd | **bedt** een UE of op Doc-Gebaseerde vorm in de pagina van DA in | DA bouwt zelf geen formulieren |


## Ontwerpmethoden in detail

### Universele editor

<span class="preview"> Dit is een pre-versieeigenschap beschikbaar door ons <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features"> pre-vrijgavekanaal </a>. </span>

[ Universele Redacteur ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) is een visueel, belemmering-en-dalingsauteursgereedschap voor marketers en ontwerpers die snelheid met onderneming-rang macht combineert:

* WYSIWYG-bewerkingen in realtime en voorvertoningen van apparaten.
* Directe integratie met AEM-elementen, -workflows en -formuliergegevensmodel (FDM).
* Naadloze overdracht aan ontwikkelaars voor aangepaste componenten in vanilla JS/CSS.
* Geavanceerde regeleditor voor het maken van complexe logica.
* Uitbreidbaarheid aan de serverzijde voor aangepaste functies.
* WYSIWYG-bewerkingservaring voor het maken en visualiseren van formulieren.
* Document met recordfunctionaliteit om tamper-proof archieven van verzonden gegevens te maken.
* Integratie met Adobe Sign for Electronic signatures.
* Integratie met Adobe Workfront Fusion om Adobe Workfront Fusion-scenario&#39;s te activeren bij het verzenden van het formulier.
* Integratie met verschillende gegevensbronnen voor het vooraf invullen van formulieren en het verzenden van gegevens.
* Formuliergegevensmodel (FDM) voor het definiëren van gegevensstructuur en interacties met verschillende gegevensbronnen.
* De mogelijkheid om te kiezen uit meerdere verzendacties voor de verwerking van formulierverzendingen, zoals het verzenden van gegevens naar Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics en nog veel meer gegevensbronnen.
* Verzenden met gebruik van verzendacties voor Forms Submission Service (FSS) of AEM Publish

**Aanbeveling**: Begin elk nieuw vormproject met Universele Redacteur tenzij uw team 100 % document-centric is en de vorm zeer fundamenteel is.


### Op documenten gebaseerde ontwerpfuncties (met Microsoft Docs of Google Sheets)

[ op document-Gebaseerde creatie ](/help/edge/docs/forms/tutorial.md) is best geschikt voor het creëren van eenvoudige, laag-ingewikkelde vormen gebruikend vertrouwde hulpmiddelen zoals Microsoft Word, Google Docs, of de Bladen van Google. Deze methode is ideaal voor inhoudsteams die een snelle en eenvoudige manier nodig hebben om formulieren te maken.

* Toegankelijke onderdelen voor een gebruiksvriendelijke ervaring.
* Gestandaardiseerde HTML-structuur voor consistente rendering.
* Regels en validaties om de nauwkeurigheid van de gegevens te garanderen.
* Opties voor bestandsbijlagen voor het verzamelen van aanvullende informatie.
* Google reCAPTCHA-integratie voor spambescherming.
* Mogelijkheid om aangepaste formuliercomponenten te maken voor specifieke behoeften.
* Formuliergegevens rechtstreeks verzenden naar Microsoft Excel of Google-werkbladen of e-mailadressen.
* De prestaties van uw formulieren controleren met behulp van de operationele telemetrie


### Forms insluiten in Document Authoring (DA)

Document Authoring (DA) is ontworpen voor het maken van gestructureerde pagina-inhoud en ondersteunt het maken van native formulieren niet. Om een vorm aan een DA-authored pagina toe te voegen, kunt u de vorm tot stand brengen gebruikend de **Universele Redacteur** (geadviseerd) of op document-Gebaseerd Authoring en de vorm inbedden aan Document Authoring pagina.

## Edge Delivery Services Forms publiceren {#edge-overview}

In het volgende diagram ziet u hoe u formulieren kunt bewerken in Microsoft Excel of Google Sheets (Document-based Authoring) en publiceren naar Edge Delivery Services. Ook wordt de AEM-publicatiemethode weergegeven met behulp van de WYSIWYG Authoring (Universal Editor).

![ publiceer aan Edge Delivery Services en AEM ](/help/edge/docs/forms/assets/AEM-forms-with-EDS-publishing.png)


<!-- 
## Feature Comparison

| Capability | Universal Editor | Document-Based | Document Authoring |
|------------|-----------------|----------------|--------------------|
| Visual drag-and-drop | ✅ | – | – |
| Advanced rules editor | ✅ | Limited | – |
| Attachments | ✅ | EA | – |
| reCAPTCHA Enterprise | ✅ | ✅ | Depends on embed |
| Submit to spreadsheet/email | ✅ (FSS) | ✅ (FSS) | Via embed |
| Submit to AEM workflows/FDM | ✅ | – | Via UE embed |
| Custom components (JS/CSS) | ✅ | ✅ | Via embed |
| Localization via Sites | ✅ | Manual | Via embed |

-->

## Volgende stappen

* [Functies en mogelijkheden van de Universal Editor voor Edge Delivery Services for Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [Uw eerste formulier maken met de Universal Editor](/help/edge/docs/forms/universal-editor/create-forms.md)
* [ creeer uw eerste vorm gebruikend de Bladen van Google of Microsoft Excel ](/help/edge/docs/forms/tutorial.md).
* [ bed Forms in Document Authoring (DA) in ](https://www.aem.live/developer/da-tutorial)


U kunt nu uw eerste krachtige formulier maken met AEM Edge Delivery Services.


<!-- 

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