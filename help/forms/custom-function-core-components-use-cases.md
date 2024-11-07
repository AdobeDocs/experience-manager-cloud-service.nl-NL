---
title: In dit artikel worden verschillende gebruiksgevallen beschreven voor een aangepaste functie in een adaptief formulier dat is gebaseerd op kerncomponenten.
description: Het artikel beschrijft verschillende gebruiksgevallen voor een aangepaste functie in een adaptief formulier dat is gebaseerd op kerncomponenten. Aangepaste functies worden gebruikt in de regeleditor om aangepaste regels voor het formulier te maken.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: df92b91e-f3b0-4a08-bd40-e99edc9a50a5
source-git-commit: 88b9686a1ceec6729d9657d4bb6f458d9c411065
workflow-type: tm+mt
source-wordcount: '2134'
ht-degree: 0%

---

# Voorbeelden van het ontwikkelen en gebruiken van douanefunctie

Het artikel bevat de gedetailleerde voorbeelden van aangepaste functies voor een adaptief formulier dat is gebaseerd op kerncomponenten en dat waardevolle inzichten biedt in de effectieve implementatie ervan in verschillende scenario&#39;s. De functies van de douane worden gebruikt in de regelredacteur van AEM Forms, laten ontwikkelaars toe om de logica te bepalen en te controleren die vormgedrag beheerst.
In dit artikel worden verschillende implementaties van aangepaste functies besproken, waarbij wordt getoond hoe deze kunnen worden gebruikt om formulieren af te stemmen op specifieke vereisten en de algemene functionaliteit te verbeteren.

## De opties in de vervolgkeuzelijst vullen met aangepaste functies

De Redacteur van de Regel in de Componenten van de Kern steunt niet het **Vastgestelde bezit van Opties** om dropdown lijstopties dynamisch bij runtime te bevolken. U kunt de opties in de vervolgkeuzelijst echter vullen met behulp van aangepaste functies, waarmee u opties kunt ophalen op basis van specifieke logica. Aangepaste functies bieden meer flexibiliteit en controle over de manier waarop en wanneer de vervolgkeuzemogelijkheden worden gevuld. Hierdoor wordt de gebruikerservaring verbeterd.

Om de opties van de dropdown lijst te bevolken gebruikend een douanefunctie, voeg de volgende code toe zoals die in [ wordt beschreven creeer-douane-functie ](/help/forms/custom-function-core-component-create-function.md) sectie:


```javascript
    /**
    * @name setEnums
    * @returns {string[]}
    **/
    function setEnums() {
    return ["0","1","2","3","4","5","6"];   
    }

    /**
    * @name setEnumNames
    * @returns {string[]}
    **/
    function setEnumNames() {
    return ["Sunday","Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
    }
```

In de bovenstaande code wordt `setEnums` gebruikt om de eigenschap `enum` in te stellen en wordt `setEnumNames` gebruikt om de eigenschap `enumNames` van het vervolgkeuzemenu in te stellen.

Maak een regel voor de knop `Next` , die de waarde van de keuzelijst instelt wanneer de gebruiker op de knop `Next` klikt:

![ drop-down lijstopties ](/help/forms/assets/drop-down-list-options.png)

Raadpleeg de onderstaande afbeelding om aan te tonen waar de opties van de vervolgkeuzelijst zijn ingesteld wanneer u op de knop Weergeven klikt:

![ drop-down opties in de regeleditor ](/help/forms/assets/drop-down-option-rule-editor.png)

## Een deelvenster tonen met de regel `SetProperty`

Laten we leren hoe aangepaste functies veld- en globale objecten gebruiken met behulp van een `Contact Us` -formulier.

![ Vorm van het Contact ons ](/help/forms/assets/contact-us-form.png)

Voeg de volgende code in de douanefunctie toe zoals die in [ wordt verklaard creeer-douane-functie ](/help/forms/custom-function-core-component-create-function.md) sectie, om het vormgebied als `Required` te plaatsen.

```javascript
    
    /**
    * enablePanel
    * @name enablePanel
    * @param {object} field1
    * @param {object} field2
    * @param {scope} globals 
    */

    function enablePanel(field1,field2, globals)
    {
       if(globals.functions.validate(field1).length === 0)
       {
       globals.functions.setProperty(field2, {visible: true});
       }
    }
```

>[!NOTE]
>
> * U kunt de veldeigenschappen vormen gebruikend de beschikbare eigenschappen die in `[form-path]/jcr:content/guideContainer.model.json` worden gevestigd.
> * Wijzigingen die u met de methode `setProperty` van het object Globals in het formulier aanbrengt, zijn asynchroon van aard en worden niet doorgevoerd tijdens het uitvoeren van de aangepaste functie.

In dit voorbeeld wordt de validatie van het deelvenster `personaldetails` uitgevoerd wanneer u op de knop klikt. Als er geen fouten worden gedetecteerd in het deelvenster, wordt een ander deelvenster, het deelvenster `feedback` , weergegeven wanneer u op de knop klikt.

Laten we een regel voor de knop `Next` maken, die het deelvenster `personaldetails` valideert en het deelvenster `feedback` zichtbaar maakt wanneer de gebruiker op de knop `Next` klikt.

![ plaats Bezit ](/help/forms/assets/custom-function-set-property.png)

Raadpleeg de onderstaande afbeelding om aan te tonen waar het deelvenster `personaldetails` wordt gevalideerd wanneer u op de knop `Next` klikt. Als alle velden in de `personaldetails` worden gevalideerd, wordt het deelvenster `feedback` weergegeven.

![ plaats de Voorproef van de Vorm van het Bezit ](/help/forms/assets/set-property-form-preview.png)

Als er fouten voorkomen in de velden van het deelvenster `personaldetails` , worden deze in het veld weergegeven wanneer op de knop `Next` wordt geklikt. Het deelvenster `feedback` blijft dan onzichtbaar.

![ plaats de Voorproef van de Vorm van het Bezit ](/help/forms/assets/set-property-panel.png)

## Het veld valideren

Laten we leren hoe aangepaste functies veld- en globale objecten gebruiken om het veld te valideren met behulp van een `Contact Us` -formulier.

Voeg de volgende code in de douanefunctie toe zoals die in [ wordt verklaard creeer-douane-functie ](/help/forms/custom-function-core-component-create-function.md) sectie, om het gebied te bevestigen.

```javascript
    /**
    * validateField
    * @name validateField
    * @param {object} field
    * @param {scope} globals
    */
    function validateField(field,globals)
    {
    
        globals.functions.validate(field);
    
    }   
```

>[!NOTE]
>
> Als er geen argument wordt doorgegeven in de functie `validate()` , wordt het formulier gevalideerd.

In dit voorbeeld wordt een aangepast validatiepatroon toegepast op het veld `contact` . Gebruikers moeten een telefoonnummer invoeren dat begint met `10` gevolgd door `8` cijfers. Als de gebruiker een telefoonnummer invoert dat niet begint met `10` of meer of minder dan `8` cijfers bevat, verschijnt er een foutbericht bij de klik op de knop:

![ Patroon van de Bevestiging van het E-mailAdres ](/help/forms/assets/custom-function-validation-pattern.png)

De volgende stap bestaat uit het maken van een regel voor de knop `Next` die het veld `contact` in het klikveld valideert.

![ Patroon van de Bevestiging ](/help/forms/assets/custom-function-validate.png)

Verwijs naar de illustratie hieronder om aan te tonen dat als de gebruiker een telefoonaantal ingaat dat niet met `10` begint, een foutenmelding op het gebiedsniveau verschijnt:

![ Patroon van de Bevestiging van het E-mailAdres ](/help/forms/assets/custom-function-validate-error-message.png)

Als de gebruiker een geldig telefoonnummer invoert en alle velden in het deelvenster `personaldetails` zijn gevalideerd, wordt het deelvenster `feedback` op het scherm weergegeven:

![ Patroon van de Bevestiging van het E-mailAdres ](/help/forms/assets/validate-form-preview-form.png)

## Een deelvenster opnieuw instellen

Laten we leren hoe aangepaste functies veld- en globale objecten gebruiken om het veld opnieuw in te stellen met behulp van een `Contact Us` -formulier.

Voeg de volgende code in de douanefunctie toe zoals die in [ wordt verklaard creeer-douane-functie ](/help/forms/custom-function-core-component-create-function.md) sectie, om het paneel terug te stellen.

```javascript
    /**
    * resetField
    * @name  resetField
    * @param {string} input1
    * @param {object} field
    * @param {scope} globals 
    */
    function  resetField(field,globals)
    {
    
        globals.functions.reset(field);
    
    }
```

>[!NOTE]
>
> Als er geen argument wordt doorgegeven in de functie `reset()` , wordt het formulier gevalideerd.

In dit voorbeeld wordt het deelvenster `personaldetails` opnieuw ingesteld wanneer u op de knop `Clear` klikt. In de volgende stap wordt een regel gemaakt voor de knop `Clear` die het deelvenster opnieuw instelt wanneer op de knop wordt geklikt.

![ Duidelijke knoop ](/help/forms/assets/custom-function-reset-field.png)

Zie de onderstaande afbeelding om weer te geven dat als de gebruiker op de knop `clear` klikt, het deelvenster `personaldetails` opnieuw wordt ingesteld:

![ Vorm van het Terugstellen ](/help/forms/assets/custom-function-reset-form.png)

## Een aangepast bericht weergeven op veldniveau en het veld markeren als ongeldig

Laten we leren hoe aangepaste functies veld- en globale objecten gebruiken om een aangepast bericht op veldniveau weer te geven en het veld als ongeldig te markeren met behulp van een `Contact Us` -formulier.

Met de functie `markFieldAsInvalid()` kunt u een veld definiëren als ongeldig en een aangepast foutbericht instellen op veldniveau. De `fieldIdentifier` -waarde kan `fieldId` , `field qualifiedName` of `field dataRef` zijn. De waarde van het object met de naam `option` kan `{useId: true}` , `{useQualifiedName: true}` of `{useDataRef: true}` zijn.
De syntaxis die wordt gebruikt om een veld als ongeldig te markeren en een aangepast bericht in te stellen is:

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Voeg de volgende code in de douanefunctie toe zoals die in [ wordt verklaard creeer-douane-functie ](/help/forms/custom-function-core-component-create-function.md) sectie, om een douanebericht op het gebiedsniveau toe te laten.

```javascript
    /**
    * customMessage
    * @name customMessage
    * @param {object} field
    * @param {scope} globals 
    */
    function customMessage(field, globals) {
    const minLength = 15;
    const comments = field.$value.trim();
    if (comments.length < minLength) {
        globals.functions.markFieldAsInvalid(field.$id, "Comments must be at least 15 characters long.", { useId: true });
    }
}
```

In dit voorbeeld wordt een aangepast bericht weergegeven op veldniveau als de gebruiker minder dan 15 tekens invoert in het tekstvak Opmerkingen.

In de volgende stap wordt een regel voor het veld `comments` gemaakt:

![ gebied van het Teken als Ongeldig ](/help/forms/assets/custom-function-invalid-field.png)

Zie de onderstaande demonstratie om te tonen dat het invoeren van negatieve feedback in het veld `comments` de weergave van een aangepast bericht op veldniveau activeert:

![ gebied van het Teken als Ongeldige vorm van de Voorproef ](/help/forms/assets/custom-function-invalidfield-form.png)

Als de gebruiker meer dan 15 tekens in het tekstvak Opmerkingen invoert, wordt het veld gevalideerd en wordt het formulier verzonden:

![ gebied van het Teken als geldige vorm van de Voorproef ](/help/forms/assets/custom-function-validfield-form.png)

## Gewijzigde gegevens naar de server verzenden

Laten we leren hoe aangepaste functies veld- en globale objecten gebruiken om gemanipuleerde gegevens op de server te verzenden met behulp van een `Contact Us` -formulier.

De volgende regel code:
`globals.functions.submitForm(globals.functions.exportData(), false);` wordt gebruikt om de formuliergegevens te verzenden na manipulatie.
* Het eerste argument betreft de gegevens die moeten worden ingediend.
* Het tweede argument geeft aan of het formulier moet worden gevalideerd voordat het wordt verzonden. Deze is `optional` en wordt standaard ingesteld op `true` .
* Het derde argument is de `contentType` van de verzending, die ook optioneel is met de standaardwaarde `multipart/form-data` . De andere waarden kunnen `application/json` en `application/x-www-form-urlencoded` zijn.

Voeg de volgende code in de douanefunctie toe zoals die in [ wordt verklaard creeer-douane-functie ](/help/forms/custom-function-core-component-create-function.md) sectie, om de gemanipuleerde gegevens bij de server voor te leggen:

```javascript
    /**
    * submitData
    * @name submitData
    * @param {object} field
    * @param {scope} globals 
    */
    function submitData(globals)
    {
    
    var data = globals.functions.exportData();
    if(!data.comments) {
    data.comments = 'NA';
    }
    console.log('After update:{}',data);
    globals.functions.submitForm(data, false);
    }
```

In dit voorbeeld wordt `NA` verzonden naar de server wanneer de gebruiker het tekstvak `comments` leeg laat.

Maak nu een regel voor de knop `Submit` die gegevens verzendt:

![ legt gegevens ](/help/forms/assets/custom-function-submit-data.png) voor

Raadpleeg de illustratie van de onderstaande `console window` om aan te tonen dat als de gebruiker het `comments` textbox leeg laat, de waarde zoals `NA` wordt verzonden op de server:

![ legt gegevens bij het consolevenster voor ](/help/forms/assets/custom-function-submit-data-form.png)

U kunt het consolevenster ook inspecteren om de gegevens te bekijken die aan de server worden voorgelegd:

![ gegevens van Inspect bij het consolevenster ](/help/forms/assets/custom-function-submit-data-console-data.png)

## Voltooien van verzenden van formulieren en fouthandlers negeren

Laten we leren hoe aangepaste functies veld- en globale objecten gebruiken om verzendingshandlers te negeren met behulp van een `Contact Us` -formulier.

Voeg de volgende lijn van code toe zoals die in [ wordt verklaard creeer-douane-functionas ](/help/forms/custom-function-core-component-create-function.md) sectie, om de voorlegging of het mislukkingsbericht voor vormvoorlegging aan te passen en de berichten van de vormvoorlegging in een modaal vakje te tonen:

```javascript
/**
 * Handles the success response after a form submission.
 *
 * @param {scope} globals - This object contains a read-only form instance, target field instance, triggered event, and methods for performing form modifications within custom functions.
 * @returns {void}
 */
function customSubmitSuccessHandler(globals) {
    var event = globals.event;
    var submitSuccessResponse = event.payload.body;
    var form = globals.form;

    if (submitSuccessResponse) {
        if (submitSuccessResponse.redirectUrl) {
            window.location.href = encodeURI(submitSuccessResponse.redirectUrl);
        } else if (submitSuccessResponse.thankYouMessage) {
            showModal("success", submitSuccessResponse.thankYouMessage);
        }
    }
}

/**
 * Handles the error response after a form submission.
 *
 * @param {string} customSubmitErrorMessage - The custom error message.
 * @param {scope} globals - This object contains a read-only form instance, target field instance, triggered event, and methods for performing form modifications within custom functions.
 * @returns {void}
 */
function customSubmitErrorHandler(customSubmitErrorMessage, globals) {
    showModal("error", customSubmitErrorMessage);
}
function showModal(type, message) {
    // Remove any existing modals
    var existingModal = document.getElementById("modal");
    if (existingModal) {
        existingModal.remove();
    }

    // Create the modal dialog
    var modal = document.createElement("div");
    modal.setAttribute("id", "modal");
    modal.setAttribute("class", "modal");

    // Create the modal content
    var modalContent = document.createElement("div");
    modalContent.setAttribute("class", "modal-content");

    // Create the modal header
    var modalHeader = document.createElement("div");
    modalHeader.setAttribute("class", "modal-header");
    modalHeader.innerHTML = "<h2>" + (type === "success" ? "Thank You" : "Error") + "</h2>";

    // Create the modal body
    var modalBody = document.createElement("div");
    modalBody.setAttribute("class", "modal-body");
    modalBody.innerHTML = "<p class='" + type + "-message'>" + message + "</p>";

    // Create the modal footer
    var modalFooter = document.createElement("div");
    modalFooter.setAttribute("class", "modal-footer");

    // Create the close button
    var closeButton = document.createElement("button");
    closeButton.setAttribute("class", "close-button");
    closeButton.innerHTML = "Close";
    closeButton.onclick = function() {
        modal.remove();
    };

    // Append the elements to the modal content
    modalFooter.appendChild(closeButton);
    modalContent.appendChild(modalHeader);
    modalContent.appendChild(modalBody);
    modalContent.appendChild(modalFooter);

    // Append the modal content to the modal
    modal.appendChild(modalContent);

    // Append the modal to the document body
    document.body.appendChild(modal);
}
```

Wanneer de gebruiker in dit voorbeeld de aangepaste functies `customSubmitSuccessHandler` en `customSubmitErrorHandler` gebruikt, worden de geluids- en foutberichten in een modaal voorbeeld weergegeven. De JavaScript-functie `showModal(type, message)` wordt gebruikt om dynamisch een modaal dialoogvenster op het scherm te maken en weer te geven.

Maak nu een regel voor het succesvol verzenden van formulieren:

![ succes van de de voorlegging van de Vorm ](/help/forms/assets/form-submission-success.png)

Raadpleeg de onderstaande illustratie om aan te tonen dat wanneer het formulier is verzonden, het succesbericht wordt weergegeven in een modaal formulier:

![ bericht van het de voorlegging van de Vorm succesbericht ](/help/forms/assets/form-submission-success-message.png)

Laten we ook een regel maken voor mislukte formulierverzendingen:

![ de voorlegging van de Vorm ontbreekt ](/help/forms/assets/form-submission-fail.png)

Raadpleeg de onderstaande afbeelding om aan te tonen dat wanneer het verzenden van het formulier mislukt, het foutbericht wordt weergegeven in een modaal:

![ de voorlegging van de Vorm ontbreekt bericht ](/help/forms/assets/form-submission-fail-message.png)

Als u het verzenden van formulieren standaard wilt laten slagen of mislukken, zijn de functies `Default submit Form Success Handler` en `Default submit Form Error Handler` beschikbaar buiten het vak.

In het geval, ontbreekt de manager van de douanevoorlegging om zoals verwacht in bestaande AEM Projecten of vormen uit te voeren, verwijs naar de [ het oplossen van problemen](#troubleshooting) sectie.

## Handelingen uitvoeren in een specifieke instantie van het herhaalbare deelvenster

Regels die u met de visuele regeleditor in een herhaalbaar deelvenster hebt gemaakt, worden toegepast op de laatste instantie van het herhaalbare deelvenster. Om een regel voor een specifieke instantie van het herhaalbare paneel te schrijven, kunnen wij een douanefunctie gebruiken.

Laten we een ander formulier maken als `Booking Form` om informatie te verzamelen over reizigers die naar een bestemming gaan. Er wordt een deelvenster voor reizigers toegevoegd als een herhaalbaar deelvenster, waar de gebruiker met de knop `Add Traveler` details voor 5 reizigers kan toevoegen.

![ Informatie van de reiziger ](/help/forms/assets/traveler-info-form.png)

Voeg de volgende lijn van code toe zoals die in [ wordt verklaard creeer-douane-functie ](/help/forms/custom-function-core-component-create-function.md) sectie, om acties in een specifieke instantie van het herhaalbare paneel, buiten laatste uit te voeren:

```javascript
/**
* @name hidePanelInRepeatablePanel
* @param {scope} globals
*/
function hidePanelInRepeatablePanel(globals)
{    
    var repeatablePanel = globals.form.travelerinfo;
    // hides a panel inside second instance of repeatable panel
    globals.functions.setProperty(repeatablePanel[1].traveler, {visible : false});
}  
```

In dit voorbeeld voert de aangepaste functie `hidePanelInRepeatablePanel` een handeling uit in een specifieke instantie van het herhaalbare deelvenster. In de bovenstaande code staat `travelerinfo` voor het herhaalbare deelvenster. De code `repeatablePanel[1].traveler, {visible: false}` verbergt het deelvenster in de tweede instantie van het herhaalbare deelvenster.

Voeg een knop met het label `Hide` toe en voeg een regel toe om de tweede instantie van een herhaalbaar deelvenster te verbergen.

![ de regel van het Comité van de Huid ](/help/forms/assets/custom-function-hidepanel-rule.png)

In de onderstaande video ziet u hoe u kunt zien dat wanneer op `Hide` wordt geklikt, het deelvenster in de tweede herhaalbare instantie wordt verborgen:

>[!VIDEO](https://video.tv.adobe.com/v/3429554?quality=12&learn=on)

## Vul het veld vooraf met een waarde wanneer het formulier wordt geladen

Laten we leren hoe aangepaste functies veld- en globale objecten gebruiken om velden vooraf in te vullen met behulp van een `Booking Form` .

Voeg de volgende lijn van code, zoals die in [ wordt verklaard creeer-douane-functie ](/help/forms/custom-function-core-component-create-function.md) sectie, toe om de vooraf ingevulde waarde op een gebied te laden wanneer de vorm wordt geïnitialiseerd:

```javascript
/**
 * Tests import data
 * @name testImportData
 * @param {scope} globals
 */
function testImportData(globals)
{
    globals.functions.importData(Object.fromEntries([['amount','10000']]));
} 
```

In de bovenstaande code vult de functie `testImportData` het tekstvak `Booking Amount` vooraf in wanneer het formulier wordt geladen. Laten we ervan uitgaan dat voor het boekingsformulier het minimumboekingsbedrag `10,000` vereist is.

Laten we een regel maken bij de initialisatie van het formulier, waarbij de waarde in het tekstvak `Booking Amount` wordt voorgevuld met een opgegeven waarde wanneer het formulier wordt geladen:

![ de Regel van de Gegevens van de Invoer ](/help/forms/assets/custom-function-import-data.png)

Raadpleeg de onderstaande schermafbeelding, die aantoont dat bij het laden van het formulier de waarde in het tekstvak `Booking Amount` vooraf is ingevuld met een opgegeven waarde:

![ de Vorm van de Regel van Gegevens van de Invoer ](/help/forms/assets/custom-function-prefill-form.png)

## Focus instellen op het specifieke veld

Laten we leren hoe aangepaste functies veld- en globale objecten gebruiken om focus op een specifiek veld in te stellen met behulp van een `Booking Form` .

Voeg de volgende lijn van code, zoals die in [ wordt verklaard creeer-douane-functie ](/help/forms/custom-function-core-component-create-function.md) sectie, toe om nadruk op het gespecificeerde gebied te plaatsen wanneer de `Submit` knoop wordt geklikt.:

```javascript
/**
 * @name testSetFocus
 * @param {object} emailField
 * @param {scope} globals
 */
    function testSetFocus(field, globals)
    {
        globals.functions.setFocus(field);
    }
```

Voeg een regel toe aan de knop `Submit` om de focus in te stellen op het tekstvak `Email ID` wanneer erop wordt geklikt.

![ plaats de Regel van de Focus ](/help/forms/assets/custom-function-set-focus.png)

Raadpleeg de onderstaande schermafbeelding die aantoont dat wanneer op de knop `Submit` wordt geklikt, de focus wordt ingesteld op het veld `Email ID` :

![ plaats de Regel van de Focus ](/help/forms/assets/custom-function-set-focus-form.png)

>[!NOTE]
>
> U kunt de optionele parameter `$focusOption` gebruiken als u de focus wilt richten op het volgende of vorige veld ten opzichte van het `email` -veld.

## Een herhaalbaar deelvenster toevoegen of verwijderen met de eigenschap `dispatchEvent`

Laten we leren hoe aangepaste functies veld- en globale objecten gebruiken om een herhaalbaar deelvenster toe te voegen of te verwijderen met behulp van de eigenschap `dispatchEvent` met behulp van een `Booking Form` .

Voeg de volgende lijn van code, zoals die in [ wordt verklaard creeer-douane-functie ](/help/forms/custom-function-core-component-create-function.md) sectie, toe om een paneel toe te voegen wanneer de `Add Traveler` knoop gebruikend het `dispatchEvent` bezit wordt geklikt:

```javascript
/**
 * Tests add instance with dispatchEvent
 * @name testAddInstance
 * @param {scope} globals
 */
function testAddInstance(globals)
{
    var repeatablePanel = globals.form.traveler;
    globals.functions.dispatchEvent(repeatablePanel,'addInstance');
}
```

Voeg een regel aan de knop `Add Traveler` toe om het herhaalbare deelvenster toe te voegen wanneer erop wordt geklikt:

![ voeg de Regel van het Comité toe ](/help/forms/assets/custom-function-add-panel.png)

Verwijs naar gif hieronder, die aantoont dat wanneer `Add Traveler` wordt geklikt, het paneel gebruikend het `dispatchEvent` bezit wordt toegevoegd:

![ voeg Comité ](/help/forms/assets/custom-function-add-panel.gif) toe

Op dezelfde manier voeg de volgende lijn van code toe, zoals die in [ wordt verklaard creeer-douane-functie ](#create-custom-function) sectie, om een paneel te schrappen wanneer de `Delete Traveler` knoop gebruikend het `dispatchEvent` bezit wordt geklikt:

```javascript
/**
 
 * @name testRemoveInstance
 * @param {scope} globals
 */
function testRemoveInstance(globals)
{
    var repeatablePanel = globals.form.traveler;
    globals.functions.dispatchEvent(repeatablePanel, 'removeInstance');
} 
```

Voeg een regel aan de knop `Delete Traveler` toe om het herhaalbare deelvenster te verwijderen wanneer erop wordt geklikt.

![ de Regel van het Comité van de Schrapping ](/help/forms/assets/custom-function-delete-panel.png)

Zie de onderstaande GIF, die aantoont dat wanneer op de knop `Delete Traveler` wordt geklikt, het deelvenster Reiziger wordt verwijderd met de eigenschap `dispatchEvent` :

![ schrapt Comité ](/help/forms/assets/custom-function-delete-panel.gif)


## Problemen oplossen

* Als de manager van de douanevoorlegging niet zoals verwacht in bestaande AEM Projecten of vormen uitvoert, voer de volgende stappen uit:
   * Zorg ervoor dat de [ versie van de kerncomponenten aan 3.0.18 en later ](https://github.com/adobe/aem-core-forms-components) wordt bijgewerkt. Voor bestaande AEM projecten en formulieren moeten echter aanvullende stappen worden ondernomen:

   * Voor het AEM project moet de gebruiker alle instanties van `submitForm('custom:submitSuccess', 'custom:submitError')` vervangen door `submitForm()` en het project implementeren via de Cloud Manager-pijplijn.

   * Voor bestaande vormen, als de managers van de douanevoorlegging niet correct functioneren, moet de gebruiker de `submitForm` regel op **openen en bewaren** knoop gebruikend de Redacteur van de Regel. Deze handeling vervangt de bestaande regel van `submitForm('custom:submitSuccess', 'custom:submitError')` door `submitForm()` in het formulier.

## Zie ook

{{see-also-rule-editor}}
