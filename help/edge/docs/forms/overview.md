---
title: AEM Forms Edge Delivery Service - Overzicht
description: De AEM Forms Edge Delivery Service is gebouwd voor maximale prestaties en stelt u in staat de toekomst van gestroomlijnde gegevensverzameling en de betrokkenheid van gebruikers in de gaten te houden.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 6fbeb94d3547d50e93ab80aee5d6458e51edb1da
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---


# AEM Forms Edge Delivery-service

AEM Forms Edge Delivery Service is een composable service die door Adobe wordt aangeboden en waarmee u snel presterende webformulieren kunt maken en leveren.

![EDS Forms Key-functies](/help/edge/assets/eds-forms-key-features.png)

U kunt de service gebruiken om:

* **Captivate gebruikers met verbluffende formulieren**: Ontwikkel eenvoudig complexe en aantrekkelijke formulieren met behulp van een bibliotheek met vooraf gebouwde componenten. Eenvoudig reCAPTCHA te integreren, formulieren rechtstreeks naar e-mail te verzenden en bestanden naadloos te uploaden om opslagoplossingen zoals Sharepoint, Azure Storage en Amazon S3 te beveiligen. Creëer zelfs uw eigen componenten van douaneformulieren om uw unieke visie tot leven te brengen.

* **Maak digitale inschrijvingen met de tools die u kiest**: Verhoog de efficiëntie bij het ontwerpen door inhoudsbronnen te ontkoppelen. U kunt zowel op documenten gebaseerde ontwerpfuncties (Microsoft 365 en Google Workspace) als AEM ontwerpfuncties (AEM Editors) gebruiken. Als zodanig kunt u met meerdere inhoudsbronnen op dezelfde website werken en de gewenste ontwerpgereedschappen gebruiken, zoals Microsoft Excel, Google Sheets of de Adaptive Forms Editor.

* **Formulieren samenstellen met de perfecte Lighthouse-score**: Formulieren maken die snel kunnen worden geladen en gegenereerd, zelfs bij trage internetverbindingen. Snellere laadtijden en geoptimaliseerde gebruikerservaring dragen bij tot hogere voltooiingssnelheden en betere conversiesnelheden.


<!-- >
* **Captivate users with stunning forms**: 
Build complex and engaging forms with ease using a library of pre-built components. Easily integrate reCAPTCHA, submit forms directly to email, and allow seamless file uploads to secure storage solutions like Sharepoint, Azure Storage, and Amazon S3. Even create your own custom forms components to bring your unique vision to life. 

    ![Enrollment forms](/help/edge/assets/enrollment-form.png)

* **Build forms with perfect lighthouse score**: Build forms that load and render quickly, even on slow internet connections. Faster loading times and optimized user experience contribute to higher form completion rates and improved conversion rates.

    ![perfect lighthouse score for your forms](/help/edge/assets/lighthouse-forms.png)

* **Create digital enrollment experiences with tools of your choice**: Increase authoring efficiency by decoupling content sources. Out of the box you can use both AEM authoring and document-based authoring. As such, you can work with multiple content sources on the same website and use your preferred authoring tools, such as Microsoft Excel, Google Sheets, or AEM Editors.

    ![Edge Delivery forms authoring tools](/help/edge/assets/edge-delivery-forms-authoring-tools.png)
    
<!--
* **Measure customer impact and deliver effective forms**: Use our RUM dashboards to visualize form performance and identify areas for improvement. Experiment with different versions and continuously optimize your forms for maximum effectiveness, ensuring you capture the data you need and drive better business outcomes.

* **Use Integrated services:** Use integrated services to streamline and empowers your users with a one-stop shop for managing their digital enrollment journeys. Use e-signatures, automated workflows, document of record (DoR), and seamless data integration, simplify the entire digital enrollment process, accelerate approvals, and optimizes your business workflows. 

    
>[!NOTE]
    >
    >
    > WYSIWYG authoring capability, integrated services, and customer impact measuring features are available under early adopter program. You can write to aem-forms-early-adopter-program@adobe.com from your official email id to join the early adopter program and request access to the capability.

    -->

## Formulieren maken

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
            <img src="/help/edge/assets/smock_devices_18_n.svg" alt="Een formulier maken met een formulier met het type eds" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Een formulier maken met Google Sheets of Microsoft Excel</b>
        </a>
        <p>Formulieren maken die snel en automatisch opnieuw worden geladen en gegenereerd op mobiele apparaten.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Formulier verzenden" alt="Formulierfragmenten in een EDS-formulier gebruiken" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Formulier verzenden naar werkblad</b>
        </a>
        <p>Verzend formulieren rechtstreeks naar uw Microsoft Excel- of Google-werkbladen.</p>
    </div>
     <div class="card-container">
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Stijlen of thema&apos;s toepassen op een bewerkingsformulier" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Een thema aanpassen</b>
        </a>
        <p>Maak een consistente merkafbeelding door hetzelfde thema toe te passen op verschillende formulieren.</p>
    </div>
      <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="Validaties toevoegen aan formuliervelden" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Veldvalidaties toepassen</b>
        </a>
        <p>Verminder fouten en frustratie door de invoer van het formulier te controleren op een juiste opmaak.</p>
    </div> 
            <div class="card-container">
        <a href="/help/edge/docs/forms/rules-forms.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="Regels gebruiken om dynamisch gedrag aan een formulier toe te voegen" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Regels gebruiken om dynamisch gedrag aan een formulier toe te voegen</b>
        </a>
        <p>Vooraf geconfigureerde fragmenten opnieuw gebruiken in meerdere formulieren.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/translate-forms.md">  
            <img src="/help/edge/assets/smock_abc_18_n.svg" alt="Een EDS-formulier vertalen" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Een formulier vertalen</b>
        </a>
        <p>Vergroot het bereik van uw formulieren en houd de kosten in de gaten.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/repeatable-forms.md">  
            <img src="/help/edge/assets/smock_addto_18_n.svg" alt="Herhaalbare secties toevoegen aan een EDS-formulier" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Herhaalbare secties toevoegen</b>
        </a>
        <p>U kunt gemakkelijk herhaalbare secties maken en toevoegen aan een formulier.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/custom-components-forms.md"> 
            <img src="/help/edge/assets/smock_userdeveloper_18_n.svg" alt="Aangepaste formuliercomponenten maken met standaard JavaScript en CSS"  style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Aangepaste componenten maken</b>
        </a>
        <p>Gebruik standaard JavaScript en CSS om componenten en thema's te maken.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/recaptacha-forms.md">  
            <img src="/help//edge/assets/smock_keyclock_18_n.svg" alt="reCAPTCHA gebruiken in een EDS-formulier" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">reCAPTCHA gebruiken</b>
        </a>
        <p>Gebruik OOTB reCAPTCHA-integratie voor robuuste bescherming van spam en bot.</p>
    </div>


</div>


</br>









