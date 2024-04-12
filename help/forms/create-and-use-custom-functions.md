---
title: Aangepaste functies maken en toevoegen in een adaptief formulier
description: AEM Forms ondersteunt aangepaste functies waarmee gebruikers hun eigen functies in de regeleditor kunnen maken en gebruiken.
keywords: Voeg een douanefunctie toe, gebruik een douanefunctie, creeer een douanefunctie, gebruik douanefunctie in regel redacteur.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 24607dd1-2d65-480b-a831-9071e20c473d
source-git-commit: a22ecddf7c97c5894cb03eb44296e0562ac46ddb
workflow-type: tm+mt
source-wordcount: '3028'
ht-degree: 0%

---


<span class="preview"> Dit artikel bevat inhoud voor enkele functies die aan de release zijn toegevoegd. Deze pre-releasefuncties zijn alleen toegankelijk via onze [pre-releasekanaal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). Het pre-releaseprogramma heeft de volgende kenmerken:
* Optionele parameterondersteuning in aangepaste functies
* Caching-functie voor aangepaste functies
* Algemene bereikobjecten en veldobjecten ondersteunen aangepaste functies
* Ondersteuning voor moderne JavaScript-functies zoals let- en pijlfuncties (ES10-ondersteuning).
Zorg ervoor dat de [kerncomponent is ingesteld op versie 3.0.8](https://github.com/adobe/aem-core-forms-components) om pre-releasefuncties in douanefunctie te gebruiken. </span>

# Aangepaste functies in Adaptive Forms (Core Components)

## Inleiding

AEM Forms ondersteunt aangepaste functies, waardoor gebruikers JavaScript-functies kunnen definiëren voor het implementeren van complexe bedrijfsregels. Deze aangepaste functies vergroten de mogelijkheden van formulieren door het bewerken en verwerken van ingevoerde gegevens te vergemakkelijken, zodat aan bepaalde vereisten wordt voldaan. Ze maken het ook mogelijk het formuliergedrag dynamisch te wijzigen op basis van vooraf gedefinieerde criteria.

### Gebruik van aangepaste functies {#uses-of-custom-function}

De voordelen van het gebruik van aangepaste functies in Adaptive Forms zijn:

* **Verwerking van gegevens**: Met aangepaste functies kunt u gegevens verwerken die zijn ingevoerd in de formuliervelden.
* **Validatie van gegevens**: Met aangepaste functies kunt u aangepaste controles uitvoeren op de invoer van formulieren en opgegeven foutberichten weergeven.
* **Dynamisch gedrag**: Met aangepaste functies kunt u het dynamische gedrag van uw formulieren bepalen op basis van specifieke omstandigheden. U kunt bijvoorbeeld velden weergeven/verbergen, veldwaarden wijzigen of de logica van het formulier dynamisch aanpassen.
* **Integratie**: U kunt aangepaste functies gebruiken om te integreren met externe API&#39;s of services. Het helpt in het halen van gegevens uit externe bronnen, het verzenden van gegevens naar externe rustpunten, of het uitvoeren van douaneacties die op externe gebeurtenissen worden gebaseerd.

Aangepaste functies zijn in wezen clientbibliotheken die in het JavaScript-bestand worden toegevoegd. Zodra u een douanefunctie creeert, wordt het beschikbaar in de regelredacteur voor selectie door de gebruiker in een Aangepast Vorm. De aangepaste functies worden geïdentificeerd door de JavaScript-annotaties in de regeleditor.

### Ondersteunde JavaScript-annotaties voor aangepaste functies {#js-annotations}

JavaScript-annotaties worden gebruikt om metagegevens voor JavaScript-code op te geven. Het bevat opmerkingen die beginnen met specifieke symbolen, bijvoorbeeld /** en @. De annotaties bevatten belangrijke informatie over functies, variabelen en andere elementen in de code. Het adaptieve formulier ondersteunt de volgende JavaScript-aantekeningen voor aangepaste functies:

* **Naam**
De naam wordt gebruikt om de douanefunctie in de regelredacteur van een Adaptief vorm te identificeren. De volgende syntaxis wordt gebruikt om een douanefunctie te noemen:
   * `@name [functionName] <Function Name>`
   * `@function [functionName] <Function Name>`
   * `@func [functionName] <Function Name>`.
     `functionName` is de naam van de functie. Spaties zijn niet toegestaan.
     `<Function Name>` is de weergavenaam van de functie in de regeleditor van een adaptief formulier.
Als de functienaam identiek is aan de naam van de functie zelf, kunt u weglaten `[functionName]` in de syntaxis. <!-- For example,  in the `calculateAge` custom function, the name is defined as:
`* @name calculateAge` -->

* **Parameter**
De parameter is een lijst met argumenten die door aangepaste functies worden gebruikt. Een functie kan meerdere parameters ondersteunen. De volgende syntaxis wordt gebruikt om een parameter in een douanefunctie te bepalen:
   * `@param {type} name <Parameter Description>`
   * `@argument` `{type} name <Parameter Description>`
   * `@arg` `{type}` `name <Parameter Description>`.
     `{type}` vertegenwoordigt het parametertype.  De toegestane parametertypen zijn:
      * tekenreeks: vertegenwoordigt één tekenreekswaarde.
      * getal: vertegenwoordigt één numerieke waarde.
      * boolean: vertegenwoordigt één booleaanse waarde (waar of onwaar).
      * string[]: Vertegenwoordigt een array van tekenreekswaarden.
      * getal[]: Vertegenwoordigt een array van numerieke waarden.
      * boolean[]: Vertegenwoordigt een array van Booleaanse waarden.
      * date: vertegenwoordigt één datumwaarde.
      * date[]: Vertegenwoordigt een array met datumwaarden.
      * array: vertegenwoordigt een algemene array met waarden van verschillende typen.
      * object: vertegenwoordigt een formulierobject dat aan een aangepaste functie wordt doorgegeven in plaats van dat de waarde rechtstreeks wordt doorgegeven.
      * bereik: vertegenwoordigt het algemene object dat door aangepaste functies in de runtime wordt gebruikt. Deze wordt gedeclareerd als de laatste parameter in JavaScript-annotaties en is niet zichtbaar in de regeleditor van een adaptief formulier. De bereikparameter benadert het object van het formulier of de component om de regel of gebeurtenis te activeren die vereist is voor formulierverwerking.

  Het parametertype is niet hoofdlettergevoelig en spaties zijn niet toegestaan in de parameternaam.

  `<Parameter Description>` bevat details over het doel van de parameter. Het kan meerdere woorden hebben.

  Standaard zijn alle parameters verplicht. U kunt een parameter als optioneel definiëren door `=` na het parametertype of de parameternaam insluiten  `[]`. Parameters die in JavaScript-annotaties als optioneel worden gedefinieerd, worden in de regeleditor als optioneel weergegeven.
Als u een variabele wilt definiëren als een optionele parameter, kunt u een van de volgende syntaxis gebruiken:

   * `@param {type=} Input1`
In de bovenstaande coderegel: `Input1` is een optionele parameter zonder standaardwaarde. Optionele parameter met standaardwaarde declareren:
     `@param {string=<value>} input1`

     `input1` als een optionele parameter met als standaardwaarde `value`.

   * `@param {type} [Input1]`
In de bovenstaande coderegel: `Input1` is een optionele parameter zonder standaardwaarde. Optionele parameter met standaardwaarde declareren:
     `@param {array} [input1=<value>]`
     `input1` is een optionele parameter van het type array met de standaardwaarde ingesteld op `value`.
Zorg ervoor dat het parametertype tussen accolades staat {} en de parameternaam staat tussen vierkante haakjes [].

     Overweeg het volgende codefragment, waar input2 als facultatieve parameter wordt bepaald:

     ```javascript
          /**
          * optional parameter function
          * @name OptionalParameterFunction
          * @param {string} input1 
          * @param {string=} input2 
          * @return {string}
         */
         function OptionalParameterFunction(input1, input2) {
         let result = "Result: ";
         result += input1;
         if (input2 !== null) {
             result += " " + input2;
         }
         return result;
         }
     ```

     De volgende illustratie wordt weergegeven met de `OptionalParameterFunction` aangepaste functie in de regeleditor:

     ![Optionele of vereiste parameters](/help/forms/assets/optional-default-params.png)

     U kunt de regel opslaan zonder een waarde voor vereiste parameters op te geven, maar de regel wordt niet uitgevoerd en er wordt een waarschuwingsbericht weergegeven als:

     ![onvolledige regelwaarschuwing](/help/forms/assets/incomplete-rule.png)

     Wanneer de gebruiker de optionele parameter leeg laat, wordt de &#39;Undefined&#39;-waarde doorgegeven aan de aangepaste functie voor de optionele parameter.

* **Retourtype**
Het retourneringstype geeft het type waarde op dat de aangepaste functie na de uitvoering retourneert. De volgende syntaxis wordt gebruikt om een terugkeertype in een douanefunctie te bepalen:
   * `@return {type}`
   * `@returns {type}`
     `{type}` vertegenwoordigt het terugkeertype van de functie. De toegestane retourtypen zijn:
      * tekenreeks: vertegenwoordigt één tekenreekswaarde.
      * getal: vertegenwoordigt één numerieke waarde.
      * boolean: vertegenwoordigt één booleaanse waarde (waar of onwaar).
      * string[]: Vertegenwoordigt een array van tekenreekswaarden.
      * getal[]: Vertegenwoordigt een array van numerieke waarden.
      * boolean[]: Vertegenwoordigt een array van Booleaanse waarden.
      * date: vertegenwoordigt één datumwaarde.
      * date[]: Vertegenwoordigt een array met datumwaarden.
      * array: vertegenwoordigt een algemene array met waarden van verschillende typen.
      * object: vertegenwoordigt een formulierobject in plaats van de waarde rechtstreeks.

     Het terugkeertype is niet case-sensitive.

* **Persoonlijk**
De aangepaste functie, gedeclareerd als private, komt niet voor in de lijst met aangepaste functies in de regeleditor van een adaptief formulier. Aangepaste functies zijn standaard openbaar. De syntaxis voor het declareren van een aangepaste functie als private is `@private`.

Meer informatie over het definiëren van optionele parameters in JSDocs [klik hier](https://jsdoc.app/tags-param).

## Richtlijnen tijdens het maken van aangepaste functies {#considerations}

Om van de douanefuncties in de regelredacteur een lijst te maken, kunt u om het even welke volgende formaten gebruiken:

* **Functie-instructie met of zonder jsdoc-opmerkingen**

U kunt een aangepaste functie maken met of zonder jsdoc-opmerkingen.

```javascript
    function functionName(parameters) 
        {
            // code to be executed
        }
```
Als de gebruiker geen JavaScript-annotaties toevoegt aan de aangepaste functie, wordt deze door de functienaam in de regeleditor weergegeven. Het wordt echter aanbevolen JavaScript-aantekeningen op te nemen om de leesbaarheid van de aangepaste functies te verbeteren.

* **Pijlfunctie met verplichte JavaScript-annotaties of -opmerkingen**

U kunt een aangepaste functie maken met een syntaxis voor een pijlfunctie:

```javascript
    /**
    * test function
    * @name testFunction 
    * @param {string} a parameter description
    * @param {string=} b parameter description
    * @return {string}
    */
    testFunction = (a, b) => {
    return a + b;
    };
    /** */
    testFunction1=(a) => (return a)
    /** */
    testFunction2 = a => a + 100;
    
```

* **Functie-expressie met verplichte JavaScript-aantekeningen of -opmerkingen**

Als u aangepaste functies wilt weergeven in de regeleditor van een adaptief formulier, maakt u aangepaste functies in de volgende indeling:

```javascript
    /**
    * test function
    * @name testFunction 
    * @param {string} input1 parameter description
    * @param {string=} input2 parameter description
    * @return {string}
    */
    testFunction = function(input1,input2)
        {
            // code to be executed
        }
```

## Een aangepaste functie maken {#create-custom-function}

Creeer een cliëntbibliotheek om douanefuncties in de regelredacteur te roepen. Zie voor meer informatie [Client-Side bibliotheken gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html#developing).

Stappen voor het maken van aangepaste functies zijn:
1. [Een clientbibliotheek maken](#create-client-library)
1. [Clientbibliotheek toevoegen aan een adaptief formulier](#use-custom-function)

### Een clientbibliotheek maken {#create-client-library}

U kunt aangepaste functies toevoegen door een clientbibliotheek toe te voegen. Voer de volgende stappen uit om een clientbibliotheek te maken:

1. [Clone your AEM Forms as a Cloud Service Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git).
1. Een map maken onder de `[AEM Forms as a Cloud Service repository folder]/apps/` map. Maak bijvoorbeeld een map met de naam `experience-league`.
1. Navigeren naar `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/` en een `ClientLibraryFolder`. Maak bijvoorbeeld een clientbibliotheekmap als `customclientlibs`.
1. Een eigenschap toevoegen `categories` met tekenreekstype. Wijs bijvoorbeeld de waarde toe `customfunctionscategory` aan de `categories` eigenschap voor de `customclientlibs` map.

   >[!NOTE]
   >
   > U kunt elke naam kiezen voor `client library folder` en `categories` eigenschap.

1. Een map maken met de naam `js`.
1. Ga naar de `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/customclientlibs/js` map.
1. Voeg bijvoorbeeld een JavaScript-bestand toe. `function.js`. Het bestand bevat de code voor een aangepaste functie.
1. Sla de `function.js` bestand.
1. Ga naar de `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/customclientlibs/js` map.
1. Een tekstbestand toevoegen als `js.txt`. Het bestand bevat:

   ```javascript
       #base=js
       functions.js
   ```

1. Sla de `js.txt` bestand.
1. U kunt de wijzigingen in de opslagplaats toevoegen, vastleggen en doorvoeren met behulp van de onderstaande opdrachten:

   ```javascript
       git add .
       git commit -a -m "Adding custom functions"
       git push
   ```

1. [De pijplijn uitvoeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline) om de aangepaste functie te implementeren.

Zodra de pijpleiding met succes wordt uitgevoerd, wordt de douanefunctie die in cliëntbibliotheek wordt toegevoegd beschikbaar in uw [Editor voor adaptieve formulierregels](/help/forms/rule-editor-core-components.md).

### Clientbibliotheek toevoegen aan een adaptief formulier{#use-custom-function}

Zodra u de clientbibliotheek hebt geïmplementeerd in uw Forms CS-omgeving, gebruikt u de mogelijkheden van de clientbibliotheek in uw adaptieve formulier. De clientbibliotheek toevoegen aan uw adaptieve formulier

1. Open het formulier in de bewerkingsmodus. Als u een formulier wilt openen in de bewerkingsmodus, selecteert u een formulier en selecteert u **[!UICONTROL Edit]**.
1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open de **[!UICONTROL Basic]** en selecteert u de naam van de **[!UICONTROL client library category]** in de vervolgkeuzelijst (in dit geval selecteert u `customfunctionscategory`).

   ![De aangepaste clientbibliotheek van de functie toevoegen](/help/forms/assets/clientlib-custom-function.png)

   >[!NOTE]
   >
   > U kunt meerdere categorieën toevoegen door een door komma&#39;s gescheiden lijst op te geven in het dialoogvenster **[!UICONTROL Client library category]** veld.

1. Klik op **[!UICONTROL Done]**.

U kunt de aangepaste functie gebruiken in het dialoogvenster [regel-editor van een adaptief formulier](/help/forms/rule-editor-core-components.md) met de [Javascript-annotaties](##js-annotations).

## Aangepaste functies in een adaptief formulier gebruiken

In een adaptief formulier kunt u [aangepaste functies in de regeleditor](/help/forms/rule-editor-core-components.md). Voeg de volgende code toe aan het JavaScript-bestand (`Function.js` bestand) om de leeftijd te berekenen op basis van de geboortedatum (JJJJ-MM-DD). Een aangepaste functie maken als `calculateAge()` die de geboortedatum als input neemt en de leeftijd retourneert:

```javascript
    /**
        * Calculates Age
        * @name calculateAge
        * @param {object} field
        * @return {string} 
    */

    function calculateAge(field) {
    var dob = new Date(field);
    var now = new Date();

    var age = now.getFullYear() - dob.getFullYear();
    var monthDiff = now.getMonth() - dob.getMonth();

    if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
    age--;
    }

    return age;
    }
```

In het bovenstaande voorbeeld, wanneer de gebruiker de geboortedatum in de notatie (JJJJ-MM-DD) invoert, de aangepaste functie `calculateAge` wordt aangeroepen en retourneert de leeftijd.

![Calcualte Agae, aangepaste functie in Regeleditor](/help/forms/assets/custom-function-calculate-age.png)

Bekijk een voorbeeld van het formulier om te zien hoe de aangepaste functies worden geïmplementeerd via de regeleditor:

![Opnieuw berekenen, aangepaste functie in Voorvertoning van formulier in lijn-editor](/help/forms/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> U kunt naar het volgende verwijzen [aangepaste functie](/help/forms/assets//customfunctions.zip) map. Download en installeer deze map in uw AEM [Pakketbeheer](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).

### Ondersteuning voor asynchrone functies in aangepaste functies {#support-of-async-functions}

De asynchrone douanefuncties verschijnen niet in de lijst van de regelredacteur. Het is echter mogelijk om asynchrone functies aan te roepen binnen aangepaste functies die zijn gemaakt met synchrone functie-expressies.

![Aangepaste functies synchroniseren en asynchroon](/help/forms/assets/workflow-for-sync-async-custom-fumction.png)

>[!NOTE]
>
> Het voordeel van het aanroepen van asynchrone functies in aangepaste functies is dat asynchrone functies gelijktijdige uitvoering van meerdere taken mogelijk maken, met het resultaat van elke functie die binnen de aangepaste functies wordt gebruikt.

Bekijk de code hieronder om te zien hoe we asynchrone functies kunnen aanroepen met behulp van aangepaste functies:

```javascript
    
    async function asyncFunction() {
    const response = await fetch('https://petstore.swagger.io/v2/store/inventory');
    const data = await response.json();
    return data;
    }

    /**
    * callAsyncFunction
    * @name callAsyncFunction callAsyncFunction
    */
    function callAsyncFunction() {
    asyncFunction()
        .then(responseData => {
        console.log('Response data:', responseData);
        })
        .catch(error => {
         console.error('Error:', error);
    });
}
```

In het bovenstaande voorbeeld is de functie asyncFunction een `asynchronous function`. De toepassing voert een asynchrone bewerking uit door een `GET` verzoek om `https://petstore.swagger.io/v2/store/inventory`. Het wacht op de reactie met `await`parseert de responsinstantie als JSON met behulp van de `response.json()`en retourneert vervolgens de gegevens. De `callAsyncFunction` functie is een synchrone aangepaste functie die de `asyncFunction` en geeft de reactiegegevens weer in de console. Hoewel de `callAsyncFunction` De functie is synchroon, roept de asynchrone functie asynchrone asyncFunction aan en behandelt zijn resultaat met `then` en `catch` instructies.

Om zijn het werken te zien, laten wij een knoop toevoegen en een regel voor de knoop creëren die de asynchrone functie na een knoop klikt.

![regel maken voor asynchrone functie](/help/forms/assets/rule-for-async-funct.png)

Verwijs naar de illustratie van het consolevenster hieronder om aan te tonen dat wanneer de gebruiker klikt `Fetch` knop, de aangepaste functie `callAsyncFunction` wordt aangeroepen, die op zijn beurt een asynchrone functie aanroept `asyncFunction`. Inspect het consolevenster om de reactie op de knoop te bekijken klikt:

![Console-venster](/help/forms/assets/async-custom-funct-console.png)

Laten we eens kijken naar de functies van aangepaste functies.

## Verschillende functies voor Aangepaste functies

U kunt aangepaste functies gebruiken om aangepaste functies toe te voegen aan formulieren. Deze functies ondersteunen diverse mogelijkheden, zoals het werken met specifieke velden, het gebruik van globale velden of caching. Dankzij deze flexibiliteit kunt u formulieren aanpassen aan de vereisten van uw organisatie.

### Veld- en globale bereikobjecten in aangepaste functies {#support-field-and-global-objects}

Veldobjecten verwijzen naar de afzonderlijke componenten of elementen in een formulier, zoals tekstvelden, selectievakjes. Globale bereikobjecten verwijzen naar de algemene variabelen of instellingen die toegankelijk zijn voor het hele formulier. Laten we naar het volgende codefragment kijken:

```JavaScript
    /**
    * updateDateTime
    * @name updateDateTime
    * @param {object} field
    * @param {scope} globals 
    */
    function updateDateTime(field, globals) {
    // Accessing the Date object from the global scope
    var currentDate = new Date();
    // Formatting the date and time
    var formattedDateTime = currentDate.toLocaleString();
    // Updating the field value with the formatted date and time
    field.value = formattedDateTime;
    }
```

>[!NOTE]
>
> De `param {scope} globals` moet de laatste parameter zijn en deze wordt niet weergegeven in de regeleditor van een adaptief formulier.

In het bovenstaande codefragment, een aangepaste functie met de naam `updateDateTime` gebruikt parameters zoals een veldobject en een globaal object. De datum- en tijdobjecten worden benaderd via het algemene bereik. Het veld vertegenwoordigt het tekstvakobject waarin de opgemaakte datum- en tijdwaarde in het formulier wordt weergegeven.

Laten we leren hoe aangepaste functies veld- en globale objecten gebruiken met behulp van een `Contact Us` formulier met verschillende gebruiksmogelijkheden.

![Contactformulier](/help/forms/assets/contact-us-form.png)

#### **Hoofdletters gebruiken**: Een deelvenster tonen met de opdracht `SetProperty` regel

Voeg de volgende code in de douanefunctie toe zoals die in [create-custom-function](#create-custom-function) in, om het formulierveld in te stellen als `Required`.

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
> U kunt de veldeigenschappen vormen gebruikend beschikbare eigenschappen die in worden gevestigd `[form-path]/jcr:content/guideContainer.model.json`.

In dit voorbeeld, bevestiging van `personaldetails` wordt weergegeven wanneer u op de knop klikt. Als er geen fouten worden gedetecteerd in het deelvenster, wordt een ander deelvenster `feedback` wordt zichtbaar als u op een knop klikt.

Laten we een regel maken voor de `Next` knop, waarmee het `personaldetails` en maakt het `feedback`  wordt weergegeven wanneer de gebruiker op de knop `Next` knop.

![Eigenschap instellen](/help/forms/assets/custom-function-set-property.png)

Raadpleeg de onderstaande afbeelding om aan te tonen waar de `personaldetails` wordt gevalideerd als u op het `Next` knop. In het geval dat alle velden binnen de `personaldetails` worden gevalideerd, `feedback` wordt zichtbaar.

![Voorvertoning van eigenschappenformulier instellen](/help/forms/assets/set-property-form-preview.png)

Als er fouten voorkomen in de velden van het `personaldetails` worden deze weergegeven op veldniveau wanneer u op het tabblad `Next` en de `feedback` blijft onzichtbaar.

![Voorvertoning van eigenschappenformulier instellen](/help/forms/assets/set-property-panel.png)

#### **Hoofdletters gebruiken**: Valideer het veld.

Voeg de volgende code in de douanefunctie toe zoals die in [create-custom-function](#create-custom-function) te valideren.

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
> Als er geen argument wordt doorgegeven in het dialoogvenster `validate()` , valideert het formulier.

In dit voorbeeld wordt een aangepast validatiepatroon toegepast op de `contact` veld. Gebruikers moeten een telefoonnummer invoeren dat begint met `10` gevolgd door `8` cijfers. Als de gebruiker een telefoonaantal ingaat dat niet met begint `10` of meer of minder dan `8` cijfers, verschijnt een bericht van de bevestigingsfout wanneer de knoop klikt:

![Validatiepatroon e-mailadres](/help/forms/assets/custom-function-validation-pattern.png)

De volgende stap bestaat uit het maken van een regel voor de `Next` knop waarmee het `contact` veld op de knop klikken.

![Validatiepatroon](/help/forms/assets/custom-function-validate.png)

Verwijs naar de illustratie hieronder om aan te tonen dat als de gebruiker een telefoonaantal ingaat dat niet met begint `10`verschijnt er een foutbericht op veldniveau:

![Validatiepatroon e-mailadres](/help/forms/assets/custom-function-validate-error-message.png)

Als de gebruiker een geldig telefoonnummer en alle velden in het dialoogvenster `personaldetails` worden gevalideerd, `feedback` verschijnt op het scherm:

![Validatiepatroon e-mailadres](/help/forms/assets/validate-form-preview-form.png)

#### **Hoofdletters gebruiken**: Een deelvenster opnieuw instellen

Voeg de volgende code in de douanefunctie toe zoals die in [create-custom-function](#create-custom-function) om het deelvenster opnieuw in te stellen.

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
> Als er geen argument wordt doorgegeven in het dialoogvenster `reset()` , valideert het formulier.

In dit voorbeeld wordt `personaldetails` deelvenster wordt opnieuw ingesteld wanneer u op de knop `Clear` knop. De volgende stap bestaat uit het maken van een regel voor de `Clear` knop waarmee het deelvenster opnieuw wordt ingesteld op de knop klikken.

![Knop Wissen](/help/forms/assets/custom-function-reset-field.png)

Zie de onderstaande afbeelding om aan te geven dat als de gebruiker op de knop `clear` de `personaldetails` voorinstellingen deelvenster:

![Formulier opnieuw instellen](/help/forms/assets/custom-function-reset-form.png)

#### **Hoofdletters gebruiken**: Een aangepast bericht weergeven op veldniveau en het veld markeren als ongeldig

U kunt de `markFieldAsInvalid()` gebruiken om een veld als ongeldig te definiëren en een aangepast foutbericht op veldniveau in te stellen. De `fieldIdentifier` waarde kan `fieldId`, of `field qualifiedName`, of `field dataRef`. De waarde van het genoemde object `option` kan `{useId: true}`, `{useQualifiedName: true}`, of `{useDataRef: true}`.
De syntaxis die wordt gebruikt om het veld als ongeldig te markeren en een aangepast bericht in te stellen, is:

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Voeg de volgende code in de douanefunctie toe zoals die in [create-custom-function](#create-custom-function) om aangepaste berichten op veldniveau in te schakelen.

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

De volgende stap bestaat uit het maken van een regel voor de `comments` veld:

![Veld markeren als ongeldig](/help/forms/assets/custom-function-invalid-field.png)

Zie de onderstaande demonstratie voor het weergeven van negatieve feedback in het dialoogvenster `comments` Het veld activeert de weergave van een aangepast bericht op veldniveau:

![Veld markeren als ongeldig voorbeeldformulier](/help/forms/assets/custom-function-invalidfield-form.png)

Als de gebruiker meer dan 15 tekens in het tekstvak Opmerkingen invoert, wordt het veld gevalideerd en wordt het formulier verzonden:

![Veld markeren als geldig voorbeeldformulier](/help/forms/assets/custom-function-validfield-form.png)


#### **Hoofdletters gebruiken**: Verzenden van gewijzigde gegevens naar de server

De volgende regel code:
`globals.functions.submitForm(globals.functions.exportData(), false);` wordt gebruikt om de formuliergegevens te verzenden na manipulatie.
* Het eerste argument betreft de gegevens die moeten worden ingediend.
* Het tweede argument geeft aan of het formulier moet worden gevalideerd voordat het wordt verzonden. Het is `optional` en instellen als `true` standaard.
* Het derde argument is de `contentType` van de indiening, die ook `optional` met de standaardwaarde als `multipart/form-data`.

Voeg de volgende code in de douanefunctie toe zoals die in [create-custom-function](#create-custom-function) om de gemanipuleerde gegevens op de server te verzenden:

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

In dit voorbeeld, als de gebruiker de `comments` textbox leeg, de `NA` wordt bij het verzenden van het formulier naar de server verzonden.

Maak nu een regel voor de `Submit` knop voor het verzenden van gegevens:

![Gegevens verzenden](/help/forms/assets/custom-function-submit-data.png)

Raadpleeg de illustratie van de `console window` om aan te tonen dat de gebruiker de `comments` textbox leeg, vervolgens de waarde als `NA` wordt verzonden op de server:

![Gegevens verzenden in het consolevenster](/help/forms/assets/custom-function-submit-data-form.png)

U kunt het consolevenster ook inspecteren om de gegevens te bekijken die aan de server worden voorgelegd:

![Inspect-gegevens in het consolevenster](/help/forms/assets/custom-function-submit-data-console-data.png)

## Ondersteuning voor caching van aangepaste functies

De adaptieve Forms voert caching voor douanefuncties uit om reactietijd te verbeteren terwijl het terugwinnen van de lijst van de douanefunctie in de regelredacteur. Een bericht als `Fetched following custom functions list from cache` in het dialoogvenster `error.log` bestand.

![aangepaste functie met cacheondersteuning](/help/forms/assets/custom-function-cache-error.png)

Als de aangepaste functies worden gewijzigd, wordt het in cache plaatsen ongeldig en wordt het geparseerd.

## Problemen oplossen

Als het JavaScript-bestand met code voor aangepaste functies een fout bevat, worden de aangepaste functies niet vermeld in de regeleditor van een adaptief formulier. Als u de lijst met aangepaste functies wilt controleren, navigeert u naar de `error.log` bestand voor de fout. In het geval van een fout wordt de lijst met aangepaste functies leeg weergegeven:

![foutenlogbestand](/help/forms/assets/custom-function-list-error-file.png)

Als er geen fout optreedt, wordt de aangepaste functie opgehaald en weergegeven in het dialoogvenster `error.log` bestand. Een bericht als `Fetched following custom functions list` in het dialoogvenster `error.log` bestand:

![foutenlogbestand met juiste aangepaste functie](/help/forms/assets/custom-function-list-fetched-in-error.png)

## Overwegingen

* De `parameter type` en `return type` ondersteunen `None`.

* De functies die niet worden ondersteund in de lijst met aangepaste functies zijn:
   * Generatorfuncties
   * Functies Async/Await
   * Methodedefinities
   * Methoden van Class
   * Standaardparameters
   * Rustparameters

## Zie ook {#see-also}

{{see-also}}


