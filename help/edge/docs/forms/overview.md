---
title: AEM Forms Edge Delivery Service - Overzicht
description: De AEM Forms Edge Delivery Service is gebouwd voor maximale prestaties en stelt u in staat de toekomst van gestroomlijnde gegevensverzameling en de betrokkenheid van gebruikers in de gaten te houden.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: b94bd6cd70af541444fda1d03f502b4588fd879b
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---


# AEM Forms Edge Delivery-service {#aem-forms-edge-delivery-service-overview}

AEM Forms Edge Delivery Service is een composable service die door Adobe wordt aangeboden en waarmee u snel presterende webformulieren kunt maken en leveren. Deze composable service kan naadloos worden geïntegreerd met Adobe Experience Manager (AEM) om u in staat te stellen geavanceerde, bliksemsnelle webformulieren te ontwerpen, samen te stellen en te implementeren met een intuïtieve en efficiënte workflow.

AEM Forms Edge Delivery Service helpt u:

* **visueel verbluffende formulieren maken**: Ditch de bland, de koekjesvorm-koker ontwerpen en fascineer gebruikers met dynamische, moderne vormen die uw merkidentiteit weerspiegelen. Gebruik kant-en-klare onderdelen of maak uw eigen aangepaste onderdelen om uw visie snel en eenvoudig tot leven te brengen.

* **Formulieren samenstellen met perfecte vuurtorenscore**: Formulieren maken die snel kunnen worden geladen en gegenereerd, zelfs bij trage internetverbindingen. Snellere laadtijden en geoptimaliseerde gebruikerservaring dragen bij tot hogere voltooiingssnelheden en betere conversiesnelheden.

* **Auteurs en verzendingen vereenvoudigen**: Maak formulieren met vertrouwde gereedschappen zoals Microsoft Excel of Google Sheets in plaats van met de traditionele ontwerpomgevingen. Verzend formulieren rechtstreeks naar uw Microsoft Excel- of Google-werkbladen en gebruik hun ecosysteem om verzonden gegevens gemakkelijk te verwerken.

## Aan de slag met de AEM Forms Edge Delivery Service

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
            <br><b style="margin-top: 5px;">Een formulier maken</b>
        </a>
        <p>Formulieren maken die snel en automatisch opnieuw worden geladen en gegenereerd op mobiele apparaten.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/validate-forms.md">
            <img src="/help/edge/assets/smock_condition_18_n.svg" alt="Validaties toevoegen aan formuliervelden" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Veldvalidaties toepassen</b>
        </a>
        <p>Verminder fouten en frustratie door de invoer van het formulier te controleren op een juiste opmaak.</p>
    </div>
    <div class="card-container">
        <a href="/help/edge/docs/forms/form-fragments.md">
            <img src="/help/edge/assets/smock_documentfragment_18_n.svg" alt="Formulierfragmenten in een EDS-formulier gebruiken" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Formulierfragmenten maken</b>
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
        <a href="/help/edge/docs/forms/style-theme-forms.md">
            <img src="/help/edge/assets/smock_imageautomode_18_N.svg" alt="Stijlen of thema&apos;s toepassen op een bewerkingsformulier" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Een thema aanpassen</b>
        </a>
        <p>Maak een consistente merkafbeelding door hetzelfde thema toe te passen op verschillende formulieren.</p>
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
    <div class="card-container">
        <a href="/help/edge/docs/forms/create-forms.md#manually-configure-a-spreadsheet-to-accept-data">   
            <img src="/help/edge/assets/smock_platformdatamapping_18_n.svg" alt="Formulier verzenden" alt="Formulierfragmenten in een EDS-formulier gebruiken" style="border-radius: 5px;"> </b>
            <br><b style="margin-top: 5px;">Formulier verzenden naar werkblad</b>
        </a>
        <p>Verzend formulieren rechtstreeks naar uw Microsoft Excel- of Google-werkbladen.</p>
    </div>
</div>


</br>









