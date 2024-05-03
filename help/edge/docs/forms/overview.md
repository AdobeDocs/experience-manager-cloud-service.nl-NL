---
title: Overzicht AEM Forms Edge Delivery Services
description: AEM Forms-Edge Delivery Services zijn gebouwd voor optimale prestaties, waardoor u de toekomst van gestroomlijnde gegevensverzameling en de betrokkenheid van gebruikers kunt inzien.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '1018'
ht-degree: 0%

---

# AEM Forms Edge Delivery Services

AEM Forms-Edge Delivery Services zijn een set services die een snelle ontwikkelomgeving mogelijk maakt waarin auteurs snel nieuwe formulieren kunnen bijwerken, publiceren en lanceren. Deze services bieden buitengewone en zeer belangrijke vormen van ervaring die de betrokkenheid en conversies stimuleren. Deze formulieren zijn gemakkelijk te ontwerpen en te ontwikkelen.

Met deze services kunt u:

* **Ervaar zelf welke inschrijvingen u wilt maken met de gereedschappen van uw keuze:** Verhoog de efficiëntie bij het ontwerpen door inhoudsbronnen te ontkoppelen. U kunt zowel Document-based Authoring (Microsoft SharePoint of Google Drive) als AEM Authoring (Adaptive Forms Editor) gebruiken. U kunt met meerdere inhoudsbronnen werken op dezelfde formuliersite en de gewenste ontwerpgereedschappen gebruiken, zoals Microsoft Excel, Google Sheets of de Adaptive Forms Editor.

* **Uitzonderlijke ervaringen met digitaal inschrijven bieden:** Lever de Digitale Inschrijving Ervaringen die snel en onophoudelijk uw vormprestaties door echte gebruiker controle (RUM) laden en teruggeven controleren. Snellere laadtijden en een geoptimaliseerde gebruikerservaring dragen bij tot een hogere snelheid voor het invullen en converteren van formulieren.

* **Gebruik een ontwikkelaarsvriendelijke gereedschapset:** AEM Forms-Edge Delivery Services maken gebruik van normale HTML, moderne CSS en vanilla JavaScript om uitzonderlijke ervaringen te creëren, waarbij de steile leercurve van een bepaald framework wordt vermeden. Een ontwikkelaar met basisvaardigheden voor webontwikkeling kan formuliercomponenten en -ervaringen aanpassen en eenvoudig bouwen. Er is geen behoefte om op een pijpleiding te wachten om te lopen, enkel controle-binnen uw code in GitHub en uw veranderingen zijn levend.

## Overzicht AEM Forms Edge Delivery Services {#edge-overview}

Met de AEM Forms Edge Delivery-services kunt u zeer flexibel omgaan met de manier waarop u formulieren ontwerpt op uw website. U kunt inhoud en formulieren ontwerpen met [AEM maken](/help/forms/creating-adaptive-form-core-components.md) alsmede [Authoring op basis van documenten](/help/edge/docs/forms/create-forms.md). AEM Forms-Edge Delivery Services bieden een formulierblok, ook wel bekend als [Adaptief Forms-blok](/help/edge/docs/forms/create-forms.md) om een formulier toe te voegen aan uw site met Edge Delivery Services.

U ontwerpt formulieren bijvoorbeeld rechtstreeks in Microsoft Excel of Google Sheets en deze spreadsheets worden getransformeerd in formulieren voor uw website. Alle nieuwe formulieren of formulierinhoud, zoals een nieuw formulierveld, zijn direct beschikbaar op uw website zonder dat u een proces voor het opnieuw samenstellen van de formulieren hoeft te gebruiken.

In het volgende diagram ziet u hoe u formulieren kunt bewerken in Microsoft Excel of Google Sheets (Document-based Authoring) en publiceren naar Edge Delivery Services. Ook wordt de AEM publicatiemethode weergegeven met de Adaptive Forms Editor (AEM Authoring).

![Publiceren naar Edge Delivery Services en AEM](/help/edge/assets/AEM-forms-with-EDS-publishing.png)

De Edge Delivery Services van AEM Forms gebruiken GitHub zodat kunnen de klanten code direct van hun bewaarplaats beheren en opstellen GitHub. U kunt bijvoorbeeld formulieren schrijven in [Google Sheets](/help/edge/docs/forms/create-forms.md) of [Microsoft Excel](/help/edge/docs/forms/create-forms.md) en de componenten van uw formulieren kunnen worden ontwikkeld met behulp van CSS en JavaScript in een GitHub-opslagplaats.

Wanneer uw formulieren klaar zijn, kunt u de opdracht [AEM Sidekick](/help/edge/docs/forms/tutorial.md#preview-and-publish-your-content), een chrome browserextensie, voor het voorvertonen en publiceren van inhoudsupdates.

![AEM Sidekick installeren](/help/edge/assets/aem-sidekick-preview-publish-forms.png)

De keuze tussen [Authoring op basis van documenten](#document-based-authoring-features) en [AEM maken](#aem-authoring-features) is afhankelijk van uw specifieke vereisten:

* Voor eenvoudige formulieren die alleen basisinformatie verzamelen met een paar velden (neem contact met ons op, genereren formulieren voor leads of aanvraagformulieren voor services) en voor formulieren waarvoor u snelle gegevensconnectiviteit nodig hebt met behulp van een spreadsheet, gaat u naar [Authoring op basis van documenten](#document-based-authoring-features) is een goede pasvorm. U kunt deze formulieren maken zoals u een document maakt in Google Sheets of Microsoft Excel.

* Voor complexe formulieren, zoals formulieren die meerdere deelvensters vereisen, complexe regels en bedrijfslogica, gegevensmanipulatie, integratie met externe systemen of gestroomlijnde workflows met behulp van AEM functies, en [AEM maken](#aem-authoring-features) is een betere optie.


### Belangrijkste kenmerken van op documenten gebaseerde ontwerpen en AEM ontwerpen

Document-based Authoring biedt een basisreeks eigenschappen en AEM Authoring ontgrendelt extra mogelijkheden naast Document-based Authoring, die u in staat stelt om complexere en interactieve formulieren te bouwen. De belangrijkste kenmerken van zowel Document-Gebaseerde Authoring als AEM Authoring zijn:

#### Ontwerpfuncties op basis van documenten

Met Document-gebaseerde Authoring kunt u formulieren maken met vertrouwde gereedschappen, zoals Microsoft Excel of Google Sheets. Deze formulieren bieden de volgende functies:

* Toegankelijke onderdelen voor een gebruiksvriendelijke ervaring.
* Gestandaardiseerde HTML-structuur voor consistente rendering.
* Regels en validaties om de nauwkeurigheid van de gegevens te garanderen.
* Opties voor bestandsbijlagen voor het verzamelen van aanvullende informatie.
* Google reCAPTCHA-integratie voor spambescherming.
* Mogelijkheid om aangepaste formuliercomponenten te maken voor specifieke behoeften.
* Formuliergegevens rechtstreeks verzenden naar Microsoft Excel of Google-werkbladen of e-mailadressen.
* De prestaties van uw formulieren controleren met behulp van RUM (real user Monitoring)

#### AEM ontwerpfuncties

AEM Authoring biedt een WYSIWYG-interface (Adaptive Forms Editor) voor het samenstellen van formulieren en biedt alle mogelijkheden van op documenten gebaseerde authoring, plus een groot aantal extra functies:

* Geavanceerde regeleditor voor het maken van complexe logica.
* Uitbreidbaarheid aan de serverzijde voor aangepaste functies.
* WYSIWYG-bewerkingservaring voor het maken en visualiseren van formulieren.
* Document met recordfunctionaliteit om tamper-proof archieven van verzonden gegevens te maken.
* Integratie met Adobe Sign voor elektronische handtekeningen.
* Integratie met Adobe Workfront Fusion om Adobe Workfront Fusion-scenario&#39;s te activeren bij het verzenden van het formulier.
* Integratie met verschillende gegevensbronnen voor het vooraf invullen van formulieren en het verzenden van gegevens.
* Formuliergegevensmodel (FDM) voor het definiëren van gegevensstructuur en interacties met verschillende gegevensbronnen.
* Mogelijkheid om te kiezen uit meerdere verzendacties voor de verwerking van formulierverzendingen, zoals het verzenden van gegevens naar Microsoft SharePoint, Microsoft OneDrive, Adobe Workfront Fusion, Salesforce, Microsoft Dynamics en nog veel meer gegevensbronnen.

In wezen [AEM maken](/help/forms/creating-adaptive-form-core-components.md) bouwt voort op de stichting van [Authoring op basis van documenten](/help/edge/docs/forms/create-forms.md), met een geavanceerdere toolkit voor het maken en beheren van complexe formulieren.

>[!NOTE]
>
>
> De AEM-ontwerpcapaciteit is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Als u geïnteresseerd bent, stuurt u een e-mail van uw werkadres naar aem-forms-ea@adobe.com om toegang tot de functie te vragen.

### AEM Forms-Edge Delivery Services: ontwerpen, publiceren en verzenden van Forms

De volgende diagrammen illustreren het proces van het maken, publiceren en verzenden van formulieren met behulp van Document-based Authoring en AEM Authoring.

![Authoring op basis van documenten ](/help/edge/assets/document-based-authoring-workflow.png)

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
* [Realtime gebruikerscontrole](https://www.aem.live/developer/rum#authentication)

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