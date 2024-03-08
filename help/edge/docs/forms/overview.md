---
title: Overzicht AEM Forms Edge Delivery Services
description: AEM Forms-Edge Delivery Services zijn gebouwd voor optimale prestaties, waardoor u de toekomst van gestroomlijnde gegevensverzameling en de betrokkenheid van gebruikers kunt inzien.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
source-git-commit: 53a66eac5ca49183221a1d61b825401d4645859e
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---

# AEM Forms Edge Delivery Services

Het maken van formulieren stroomlijnen en hogere voltooiingssnelheden mogelijk maken met de AEM Forms-Edge Delivery Services van de Adobe. Deze krachtige, composable service biedt u de mogelijkheid om formulieren van bedrijfsniveau te maken met uitzonderlijke prestaties en een visueel aantrekkingskracht. AEM geeft prioriteit aan zowel de gebruikerservaring als aan uw bedrijfsdoelstellingen, waardoor u bliksemsnelle laadtijden en meer conversies van formulieren krijgt.

U kunt de service gebruiken om:

* **Uitzonderlijke inschrijvingservaringen opbouwen**: Bouw een inschrijvingservaring op die snel kan worden geladen en weergegeven, zelfs bij trage internetverbindingen. Snellere laadtijden en geoptimaliseerde gebruikerservaring dragen bij tot hogere voltooiingssnelheden en betere conversiesnelheden.

* **Inschrijvvaringen maken met de gewenste gereedschappen**: Verhoog de efficiëntie bij het ontwerpen door inhoudsbronnen te ontkoppelen. Buiten het vak kunt u beide gebruiken **op documenten gebaseerd schrijven** (Microsoft SharePoint of Google Drive) en **AEM maken** (AEM Editors). Als zodanig kunt u met meerdere inhoudsbronnen werken op hetzelfde formulier en de gewenste ontwerpgereedschappen gebruiken, zoals Microsoft Excel, Google Sheets of de Adaptive Forms Editor.

* **Gebruik een ontwikkelaarsvriendelijke gereedschapset:** AEM Forms maakt gebruik van onbewerkte HTML, moderne CSS en vanilla JavaScript om buitengewone ervaringen te creëren zonder de gebruikelijke overhead. Elke ontwikkelaar met basiskennis van HTML, CSS en JS zou zijn eigen componenten moeten kunnen bouwen en geen specifieke taal of kader hoeven te leren. U hebt geen pijpleiding nodig of wacht, check uw code in bij Github en uw wijzigingen zijn live. Bovendien, is er geen behoefte aan om het even welke pijpleiding of wacht, controleer uw code in Github en uw veranderingen zijn levend.


## Digitale inschrijving maken

AEM Forms biedt beide **op documenten gebaseerd schrijven** (Microsoft SharePoint of Google Drive) en **AEM maken** (AEM Editors). U kunt de [Adaptief Forms-blok](/help/edge/docs/forms/create-forms.md) om een formulier toe te voegen aan uw site met Edge Delivery Services.


>[!BEGINTABS]

>[!TAB Op documenten gebaseerde ontwerpfuncties]

Op documenten gebaseerde ontwerpen is een veelzijdige optie die geschikt is voor het maken van eenvoudige formulieren met essentiële functies. Hiermee kunt u verschillende invoertypen integreren, zoals tekstvelden, vervolgkeuzemenu&#39;s en keuzerondjes, zodat u gebruikersgegevens op effectieve wijze kunt verzamelen. Het biedt een basisversie van regels om dynamisch gedrag aan formulieren toe te voegen. Belangrijke kenmerken van op documenten gebaseerde ontwerpen zijn:

* **[Op HTML5 gebaseerde componenten van het Gebied van de Vorm](/help/edge/docs/forms/form-components.md)**: Met AEM Forms-Edge Delivery Services kunt u gebruikersvriendelijke en interactieve formulieren maken met behulp van formuliercomponenten op basis van HTML 5 [invoertypen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">selecteren</a>, en <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">veldset</a>  elementen. Deze componenten zijn geschikt voor verschillende soorten gegevensverzameling en kunnen eenvoudig aan uw specifieke behoeften worden aangepast.

* **Toegankelijkheid**: De velden in het formulierblok zijn toegankelijk. Elk label is gekoppeld aan het desbetreffende invoerelement en id&#39;s worden automatisch gegenereerd voor koppelingen. Beschrijvingen die aan velden zijn gekoppeld, worden gekoppeld via het kenmerk aria-beschreven door. Toetsenbordnavigatie met de standaardTab/Shift + Tab-toetsen wordt ondersteund.

* **[Stijlen](/help/edge/docs/forms/style-theme-forms.md)**: Elk formulierveld heeft een vaste HTML-structuur die eenvoudig kan worden versierd met behulp van aangepaste CSS- of JavaScript-bestanden. Kiezers voor velden in CSS en JS worden opgegeven op basis van type en naam. U kunt eenvoudig nieuwe kiezers maken vanwege de gestandaardiseerde structuur en stijl van het formulier.

* **Basisregels**: Maak eenvoudig logica die de zichtbaarheid, validatie en functionaliteit van velden aanpast op basis van gebruikersinvoer of vooraf gedefinieerde voorwaarden. Regels bieden een flexibele en intuïtieve manier om intelligentie toe te voegen aan uw formulieren, zodat deze zich naadloos kunnen aanpassen op basis van gebruikersinvoer.

* **Validaties**: Voordat het formulier wordt verzonden, wordt het gevalideerd en worden ongeldige velden gemarkeerd met foutberichten die aan de gebruiker worden weergegeven. Adaptief Forms-blok ondersteunt alle validatie van het HTML-formulier, ondersteund door moderne browsers, en biedt een aanvullend validatiemechanisme, zoals validatiescript, bestandsgrootte, bestandstype, bestandsgrootte en meer.

* **Bestand uploaden**: U kunt mogelijkheden voor bestandsbijlagen toevoegen aan uw formulieren. Of u nu documenten, afbeeldingen of andere bestanden van uw gebruikers moet verzamelen, de functie voor het uploaden van bestanden is een handige manier. Als er aangepaste afhandelingsopties beschikbaar zijn, kunt u het uploadproces voor het bestand aanpassen aan uw specifieke vereisten.

* **reCAPTCHA**: Profiteer van de naadloze integratie van Google reCAPTCHA in uw formulieren met onze OOTB-ondersteuning (out-of-the-box). Bescherm uw formulieren tegen frauduleuze activiteiten, spam en misbruik, terwijl u een soepele en ononderbroken gebruikerservaring behoudt. Adaptief Forms-blok ondersteunt reCaptcha V3 en reCaptcha Enterprise.

* **E-mailbericht verzenden bij het verzenden van het formulier**: Elimineer de gedoe met handmatige follow-ups en zorg voor tijdige communicatie met onze ingebouwde e-mailautomatisering voor het verzenden van formulieren. Met deze geïntegreerde oplossing kunt u eenvoudig relevante partijen op de hoogte stellen, inclusief het verzenden van formuliergegevens, wanneer iemand een formulier op uw website invult. Geen behoefte aan complexe configuraties of extra hulpmiddelen - het is klaar om uit de doos te gebruiken.

>[!TAB AEM maken]

AEM Authoring ontgrendelt aanvullende mogelijkheden naast het schrijven van documenten, waardoor u complexere en interactieve formulieren kunt maken. Naast de functies van op documenten gebaseerde ontwerpen, biedt AEM ontwerp de volgende extra functies:

* Geavanceerde regels: definieer op logica gebaseerde handelingen in uw formulieren. U kunt regels gebruiken om formuliersecties voorwaardelijk weer te geven of te verbergen, velden vooraf in te vullen op basis van gebruikersinvoer en verschillende validaties uit te voeren om de gegevensintegriteit te waarborgen.

* Uitbreidbaarheid aan de serverzijde: breid de functionaliteit van uw formulieren uit door deze te integreren met logica aan de serverzijde. Hierdoor kunt u complexe berekeningen uitvoeren, communiceren met externe systemen en specifieke taken automatiseren op basis van gebruikersacties in het formulier.
* Stroomlijn workflows en gegevensbeheer: gebruik de kracht van AEM om:
   * Ontwerp gebruikersvriendelijke formulieren met AEM editors.
   * Genereer een &quot;Document of Record&quot; voor een veilige en onvervalsbare archivering van verzonden gegevens.
   * E-signing met Adobe Sign vergemakkelijken voor een vloeiende en veilige ondertekeningservaring.
   * Automatiseer bedrijfsprocessen via AEM workflows en activeer acties op basis van formulierverzendingen.
   * Efficiënte integratie met verschillende gegevensbronnen, zodat gegevens naadloos kunnen worden doorgestuurd en uitgewisseld.

>[!ENDTABS]








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
