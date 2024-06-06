---
title: Aangepaste functies maken en toevoegen in een adaptief formulier
description: AEM Forms ondersteunt aangepaste functies, waarmee gebruikers hun eigen functies in de regeleditor kunnen maken en gebruiken.
keywords: Voeg een douanefunctie toe, gebruik een douanefunctie, creeer een douanefunctie, gebruik douanefunctie in regel redacteur.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 24607dd1-2d65-480b-a831-9071e20c473d
source-git-commit: 8730383d26c6f4fbe31a25a43d33bf314251d267
workflow-type: tm+mt
source-wordcount: '4340'
ht-degree: 0%

---


<span class="preview"> Dit artikel bevat `Override form submission success and error handlers` als een pre-releasefunctie. De pre-release functie is alleen toegankelijk via onze [pre-releasekanaal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features).

# Aangepaste functies in Adaptive Forms (Core Components)

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/adaptive-forms-core-components/create-and-use-custom-functions) |
| AEM as a Cloud Service | Dit artikel |

## Inleiding

AEM Forms ondersteunt aangepaste functies, waardoor gebruikers JavaScript-functies kunnen definiëren voor het implementeren van complexe bedrijfsregels. Deze aangepaste functies vergroten de mogelijkheden van formulieren door het bewerken en verwerken van ingevoerde gegevens te vergemakkelijken, zodat aan bepaalde vereisten wordt voldaan. Ze maken het ook mogelijk het formuliergedrag dynamisch te wijzigen op basis van vooraf gedefinieerde criteria.

>[!NOTE]
>
> Zorg ervoor dat de [kerncomponent](https://github.com/adobe/aem-core-forms-components) is ingesteld op de meest recente versie om de nieuwste functies te gebruiken.

### Gebruik van aangepaste functies {#uses-of-custom-function}

De voordelen van het gebruik van aangepaste functies in Adaptive Forms zijn:
* **Verwerking van gegevens**: Met aangepaste functies kunt u gegevens verwerken die zijn ingevoerd in de formuliervelden.
* **Validatie van gegevens**: Met aangepaste functies kunt u aangepaste controles uitvoeren op de invoer van formulieren en opgegeven foutberichten weergeven.
* **Dynamisch gedrag**: Met aangepaste functies kunt u het dynamische gedrag van uw formulieren bepalen op basis van specifieke omstandigheden. U kunt bijvoorbeeld velden weergeven/verbergen, veldwaarden wijzigen of de logica van het formulier dynamisch aanpassen.
* **Integratie**: U kunt aangepaste functies gebruiken om te integreren met externe API&#39;s of services. Het helpt in het halen van gegevens uit externe bronnen, het verzenden van gegevens naar externe rustpunten, of het uitvoeren van douaneacties die op externe gebeurtenissen worden gebaseerd.

Aangepaste functies zijn in wezen clientbibliotheken die in het JavaScript-bestand worden toegevoegd. Zodra u een douanefunctie creeert, wordt het beschikbaar in de regelredacteur voor selectie door de gebruiker in een Aangepast Vorm. De aangepaste functies worden geïdentificeerd door de JavaScript-annotaties in de regeleditor.

### Ondersteunde JavaScript-annotaties voor aangepaste functies {#js-annotations}

JavaScript-annotaties worden gebruikt om metagegevens voor JavaScript-code op te geven. Het bevat opmerkingen die beginnen met specifieke symbolen, bijvoorbeeld /** en @. De annotaties bevatten belangrijke informatie over functies, variabelen en andere elementen in de code. Het adaptieve formulier ondersteunt de volgende JavaScript-aantekeningen voor aangepaste functies:

#### Naam

De naam wordt gebruikt om de douanefunctie in de regelredacteur van een Aangepast Vorm te identificeren. De volgende syntaxis wordt gebruikt om een douanefunctie te noemen:

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`.
  `functionName` is de naam van de functie. Spaties zijn niet toegestaan.
  `<Function Name>` is de weergavenaam van de functie in de regeleditor van een adaptief formulier.
Als de functienaam identiek is aan de naam van de functie zelf, kunt u weglaten `[functionName]` in de syntaxis.

#### Parameter

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
   * bereik: vertegenwoordigt het globals object, dat alleen-lezen variabelen bevat, zoals formulierinstanties, doelveldinstanties en methoden voor het uitvoeren van formulierwijzigingen binnen aangepaste functies. Deze wordt gedeclareerd als de laatste parameter in JavaScript-annotaties en is niet zichtbaar in de regeleditor van een adaptief formulier. De bereikparameter benadert het object van het formulier of de component om de regel of gebeurtenis te activeren die vereist is voor formulierverwerking. Voor meer informatie over het object Globals en hoe het te gebruiken, [klik hier](/help/forms/create-and-use-custom-functions.md#support-field-and-global-objects).

Het parametertype is niet hoofdlettergevoelig en spaties zijn niet toegestaan in de parameternaam.

`<Parameter Description>` bevat details over het doel van de parameter. Het kan meerdere woorden hebben.

**Optionele parameters**
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
Zorg ervoor dat het parametertype tussen accolades staat {} en de parameternaam staat tussen vierkante haken.

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

![Optionele of vereiste parameters ](/help/forms/assets/optional-default-params.png)

U kunt de regel opslaan zonder een waarde voor de vereiste parameters op te geven, maar de regel wordt niet uitgevoerd en er wordt een waarschuwingsbericht weergegeven als:

![onvolledige regelwaarschuwing](/help/forms/assets/incomplete-rule.png)

Wanneer de gebruiker de optionele parameter leeg laat, wordt de &#39;Undefined&#39;-waarde doorgegeven aan de aangepaste functie voor de optionele parameter.

Meer informatie over het definiëren van optionele parameters in JSDocs [klik hier](https://jsdoc.app/tags-param).

#### Retourtype

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

#### Persoonlijk

De aangepaste functie die als private is gedeclareerd, komt niet voor in de lijst met aangepaste functies in de regeleditor van een adaptief formulier. Aangepaste functies zijn standaard openbaar. De syntaxis voor het declareren van een aangepaste functie als private is `@private`.


## Richtlijnen tijdens het maken van aangepaste functies

Om van de douanefuncties in de regelredacteur een lijst te maken, kunt u om het even welke volgende formaten gebruiken:

### Functie-instructie met of zonder jsdoc-opmerkingen

U kunt een aangepaste functie maken met of zonder jsdoc-opmerkingen.

```javascript
    function functionName(parameters) 
        {
            // code to be executed
        }
```
Als de gebruiker geen JavaScript-annotaties toevoegt aan de aangepaste functie, wordt deze door de functienaam in de regeleditor weergegeven. Het wordt echter aanbevolen JavaScript-aantekeningen op te nemen om de leesbaarheid van de aangepaste functies te verbeteren.

### Pijlfunctie met verplichte JavaScript-annotaties of -opmerkingen

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

Als de gebruiker geen JavaScript-annotaties toevoegt aan de aangepaste functie, wordt de aangepaste functie niet vermeld in de regeleditor van een adaptief formulier.

### Functie-expressie met verplichte JavaScript-aantekeningen of -opmerkingen

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

Als de gebruiker geen JavaScript-annotaties toevoegt aan de aangepaste functie, wordt de aangepaste functie niet vermeld in de regeleditor van een adaptief formulier.

## Een aangepaste functie maken {#create-custom-function}

Creeer een cliëntbibliotheek om douanefuncties in de regelredacteur te roepen. Zie voor meer informatie [Client-Side bibliotheken gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html#developing).

Stappen voor het maken van aangepaste functies zijn:
1. [Een clientbibliotheek maken](#create-client-library)
1. [Clientbibliotheek toevoegen aan een adaptief formulier](#use-custom-function)


### Vereisten om een aangepaste functie te maken

Voordat u een aangepaste functie toevoegt aan de Adaptive Forms, moet u het volgende doen:

**Software:**

* **Onbewerkte teksteditor (IDE)**: Terwijl om het even welke duidelijke tekstredacteur kan werken, biedt een Geïntegreerde Milieu van de Ontwikkeling (winde) zoals de Code van Microsoft Visual Studio geavanceerde eigenschappen voor het gemakkelijker uitgeven aan.

* **Git:** Dit versiebeheersysteem is vereist voor het beheer van codewijzigingen. Als u deze niet hebt geïnstalleerd, kunt u deze downloaden van https://git-scm.com.

### Een clientbibliotheek maken {#create-client-library}

U kunt aangepaste functies toevoegen door een clientbibliotheek toe te voegen. Voer de volgende stappen uit om een clientbibliotheek te maken:

**De opslagplaats klonen**

Klonen uw [AEM Forms as a Cloud Service opslagplaats](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git):

1. Open de opdrachtregel of het terminalvenster.

1. Navigeer naar de gewenste locatie op uw computer waar u de opslagplaats wilt opslaan.

1. Voer de volgende opdracht uit om de gegevensopslagruimte te klonen:

   `git clone [Git Repository URL]`

Met deze opdracht downloadt u de opslagplaats en maakt u een lokale map van de gekloonde opslagplaats op uw computer. In deze handleiding wordt deze map de [AEMaaCS-projectmap].

**Een clientbibliotheekmap toevoegen**

Nieuwe clientbibliotheekmap toevoegen aan de [AEMaaCS-projectmap]Voer de volgende stappen uit:

1. Open de [AEMaaCS-projectmap] in een editor.

   ![aangepaste mapstructuur voor functies](/help/forms/assets/custom-library-folder-structure.png)

1. Zoeken `ui.apps`.
1. Nieuwe map toevoegen. Voeg bijvoorbeeld een map toe met de naam `experience-league`.
1. Navigeren naar `/experience-league/` en voeg een `ClientLibraryFolder`. Maak bijvoorbeeld een clientbibliotheekmap met de naam `customclientlibs`.

   `Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/`

**Bestanden en mappen toevoegen aan de map Client Library**

Voeg het volgende toe aan de toegevoegde omslag van de cliëntbibliotheek:

* .content.xml, bestand
* js.txt, bestand
* map js

`Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/experience-league/customclientlibs/`

1. In de `.content.xml` Voeg de volgende coderegels toe:

   ```javascript
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="cq:ClientLibraryFolder"
   categories="[customfunctionscategory]"/>
   ```

   >[!NOTE]
   >
   > U kunt elke naam kiezen voor `client library folder` en `categories` eigenschap.

1. In de `js.txt` Voeg de volgende coderegels toe:

   ```javascript
         #base=js
       function.js
   ```
1. In de `js` map, voeg het javascript-bestand toe als `function.js` Dit omvat de aangepaste functies:

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
1. Sla de bestanden op.

![aangepaste mapstructuur voor functies](/help/forms/assets/custom-function-added-files.png)

**De nieuwe map opnemen in filter.xml**:

1. Ga naar de `/ui.apps/src/main/content/META-INF/vault/filter.xml` bestand in uw [AEMaaCS-projectmap].

1. Open het bestand en voeg de volgende regel aan het einde toe:

   `<filter root="/apps/experience-league" />`
1. Sla het bestand op.

![xml, filter aangepaste functies](/help/forms/assets/custom-function-filterxml.png)

**Implementeer de nieuwe clientbibliotheekmap in uw AEM omgeving**

Implementeer de AEM as a Cloud Service, [AEMaaCS-projectmap]aan uw Cloud Service-omgeving. Implementeren in uw Cloud Service-omgeving:

1. De wijzigingen vastleggen

   1. U kunt de wijzigingen in de opslagplaats toevoegen, vastleggen en doorvoeren met behulp van de onderstaande opdrachten:

   ```javascript
       git add .
       git commit -a -m "Adding custom functions"
       git push
   ```

1. De bijgewerkte code implementeren:

   1. Trigger een plaatsing van uw code door de bestaande full-stack pijpleiding. Hiermee wordt de bijgewerkte code automatisch samengesteld en geïmplementeerd.

Als u niet reeds opstelling een pijpleiding hebt, verwijs naar de gids op [hoe een pijpleiding voor AEM Forms as a Cloud Service op te zetten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline).

Zodra de pijpleiding met succes wordt uitgevoerd, wordt de douanefunctie die in de cliëntbibliotheek wordt toegevoegd beschikbaar in uw [Editor voor adaptieve formulierregels](/help/forms/rule-editor-core-components.md).

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

U kunt de aangepaste functie gebruiken in het dialoogvenster [regel-editor van een adaptief formulier](/help/forms/rule-editor-core-components.md) met de [JavaScript-annotaties](##js-annotations).

## Een aangepaste functie gebruiken in een adaptief formulier

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


### Opties voor vervolgkeuzelijsten instellen met behulp van aangepaste functies

De Redacteur van de regel in de Componenten van de Kern steunt niet **Opties instellen voor** om de opties voor de vervolgkeuzelijst tijdens runtime in te stellen. U kunt de opties voor de vervolgkeuzelijst echter instellen met behulp van aangepaste functies.

Bekijk de onderstaande code om te zien hoe u de opties voor de vervolgkeuzelijst kunt instellen met behulp van aangepaste functies:

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

In de bovenstaande code: `setEnums` wordt gebruikt om de `enum` eigendom en `setEnumNames` wordt gebruikt om de `enumNames` eigenschap van dropdown.

Laten we een regel maken voor de `Next` , waarmee de waarde van de keuzelijst wordt ingesteld wanneer de gebruiker op de knop `Next` knop:

![Opties vervolgkeuzelijst](/help/forms/assets/drop-down-list-options.png)

Raadpleeg de onderstaande afbeelding om aan te tonen waar de opties van de vervolgkeuzelijst zijn ingesteld wanneer u op de knop Weergeven klikt:

![Opties voor vervolgkeuzelijsten in de regeleditor](/help/forms/assets/drop-down-option-rule-editor.png)



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

Verwijs naar de illustratie van het consolevenster hieronder om aan te tonen dat wanneer de gebruiker klikt `Fetch` knop, de aangepaste functie `callAsyncFunction` wordt aangeroepen, die op zijn beurt een asynchrone functie aanroept `asyncFunction`. Inspect het consolevenster om de reactie op de knoop te bekijken klik:

![Console-venster](/help/forms/assets/async-custom-funct-console.png)

Laten we eens kijken naar de functies van aangepaste functies.

## Verschillende functies voor Aangepaste functies

U kunt aangepaste functies gebruiken om aangepaste functies toe te voegen aan formulieren. Deze functies ondersteunen diverse mogelijkheden, zoals het werken met specifieke velden, het gebruik van globale velden of caching. Dankzij deze flexibiliteit kunt u formulieren aanpassen aan de vereisten van uw organisatie.

### Veld- en globale bereikobjecten in aangepaste functies {#support-field-and-global-objects}

Veldobjecten verwijzen naar de afzonderlijke componenten of elementen in een formulier, zoals tekstvelden, selectievakjes. Het object Globals bevat alleen-lezen variabelen, zoals formulierinstantie, doelveldinstantie en methoden voor het uitvoeren van formulierwijzigingen binnen aangepaste functies.

>[!NOTE]
>
> De `param {scope} globals` moet de laatste parameter zijn en deze wordt niet weergegeven in de regeleditor van een adaptief formulier.

<!-- Let us look at the following code snippet:

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
    // Updating the field value with the formatted date and time using setProperty.
    globals.functions.setProperty(field, {value: formattedDateTime});
    }
```

In the above code snippet, a custom function named `updateDateTime` takes parameters such as a field object and a global object. The field represents the textbox object where the formatted date and time value is displayed within the form. -->

Laten we leren hoe aangepaste functies veld- en globale objecten gebruiken met behulp van een `Contact Us` formulier met verschillende gebruiksgevallen.

![Contactformulier](/help/forms/assets/contact-us-form.png)

+++ **Hoofdletters gebruiken**: Een deelvenster tonen met de opdracht `SetProperty` regel

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
> * U kunt de veldeigenschappen vormen gebruikend beschikbare eigenschappen die in worden gevestigd `[form-path]/jcr:content/guideContainer.model.json`.
> * Wijzigingen in het formulier met het `setProperty` De methode van het object Globals is asynchroon van aard en wordt niet weerspiegeld tijdens de uitvoering van de aangepaste functie.

In dit voorbeeld, bevestiging van `personaldetails` wordt weergegeven wanneer u op de knop klikt. Als er geen fouten worden gedetecteerd in het deelvenster, wordt een ander deelvenster `feedback` wordt zichtbaar als u op een knop klikt.

Laten we een regel maken voor de `Next` knop, waarmee het `personaldetails` en maakt het `feedback`  wordt weergegeven wanneer de gebruiker op de knop `Next` knop.

![Eigenschap instellen](/help/forms/assets/custom-function-set-property.png)

Raadpleeg de onderstaande afbeelding om aan te tonen waar de `personaldetails` wordt gevalideerd als u op het `Next` knop. In het geval dat alle velden binnen de `personaldetails` worden gevalideerd, `feedback` wordt zichtbaar.

![Voorvertoning van eigenschappenformulier instellen](/help/forms/assets/set-property-form-preview.png)

Als er fouten voorkomen in de velden van het `personaldetails` worden deze weergegeven op veldniveau wanneer u op het tabblad `Next` en de `feedback` blijft onzichtbaar.

![Voorvertoning van eigenschappenformulier instellen](/help/forms/assets/set-property-panel.png)

+++

+++ **Hoofdletters gebruiken**: Valideer het veld.

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

+++

+++ **Hoofdletters gebruiken**: Een deelvenster opnieuw instellen

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

+++

+++ **Hoofdletters gebruiken**: Een aangepast bericht weergeven op veldniveau en het veld markeren als ongeldig

U kunt de `markFieldAsInvalid()` gebruiken om een veld als ongeldig te definiëren en een aangepast foutbericht op veldniveau in te stellen. De `fieldIdentifier` waarde kan `fieldId`, of `field qualifiedName`, of `field dataRef`. De waarde van het genoemde object `option` kan `{useId: true}`, `{useQualifiedName: true}`, of `{useDataRef: true}`.
De syntaxis die wordt gebruikt om een veld als ongeldig te markeren en een aangepast bericht in te stellen is:

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Voeg de volgende code in de douanefunctie toe zoals die in [create-custom-function](#create-custom-function) om een aangepast bericht in te schakelen op veldniveau.

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

+++

+++ **Hoofdletters gebruiken**: Verzenden van gewijzigde gegevens naar de server

De volgende regel code:
`globals.functions.submitForm(globals.functions.exportData(), false);` wordt gebruikt om de formuliergegevens te verzenden na manipulatie.
* Het eerste argument betreft de gegevens die moeten worden ingediend.
* Het tweede argument geeft aan of het formulier moet worden gevalideerd voordat het wordt verzonden. Het is `optional` en instellen als `true` standaard.
* Het derde argument is de `contentType` van de indiening, die ook optioneel is met de standaardwaarde als `multipart/form-data`. De andere waarden kunnen `application/json` en `application/x-www-form-urlencoded`.

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

+++

+++ **Hoofdletters gebruiken**: Vervang het succes van het verzenden van formulieren en fouthandlers

Voeg de volgende coderegel toe, zoals wordt uitgelegd in het dialoogvenster [create-custom-function](#create-custom-function) om het verzenden of mislukken van een formulier voor verzending aan te passen en de berichten voor het verzenden van het formulier in een modaal vak weer te geven:

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

In dit voorbeeld wanneer de gebruiker de opdracht `customSubmitSuccessHandler` en `customSubmitErrorHandler` de douanefuncties, de succes en mislukkingsberichten worden getoond in modaal. De JavaScript-functie `showModal(type, message)` wordt gebruikt om dynamisch een modaal dialoogvenster op het scherm te maken en weer te geven.

Maak nu een regel voor het succesvol verzenden van formulieren:

![Formulierverzending geslaagd](/help/forms/assets/form-submission-success.png)

Raadpleeg de onderstaande illustratie om aan te tonen dat wanneer het formulier is verzonden, het succesbericht wordt weergegeven in een modaal formulier:

![Bericht met succes bij verzenden van formulier](/help/forms/assets/form-submission-success-message.png)

Laten we ook een regel maken voor mislukte formulierverzendingen:

![Formulierverzending mislukt](/help/forms/assets/form-submission-fail.png)

Raadpleeg de onderstaande afbeelding om aan te tonen dat wanneer het verzenden van het formulier mislukt, het foutbericht wordt weergegeven in een modaal:

![Bericht van mislukte verzending van formulier](/help/forms/assets/form-submission-fail-message.png)

Als u het voltooien en mislukken van het verzenden van formulieren standaard wilt weergeven, `Default submit Form Success Handler` en `Default submit Form Error Handler` functies zijn beschikbaar in het vak.

Als de aangepaste verzender niet kan uitvoeren zoals wordt verwacht in bestaande AEM Projecten of formulieren, raadpleegt u [problemen oplossen](#troubleshooting) sectie.

+++

+++ **Hoofdletters gebruiken**: Voer handelingen uit in een specifieke instantie van het herhaalbare deelvenster

Regels die u met de visuele regeleditor in een herhaalbaar deelvenster hebt gemaakt, worden toegepast op de laatste instantie van het herhaalbare deelvenster. Om een regel voor een specifieke instantie van het herhaalbare paneel te schrijven, kunnen wij een douanefunctie gebruiken.

Laten we een ander formulier maken om informatie te verzamelen over reizigers die naar een bestemming gaan. Er wordt een deelvenster voor reizigers toegevoegd als een herhaalbaar deelvenster, waar de gebruiker details voor 5 reizigers kan toevoegen met behulp van de `Add Traveler` knop.

![Informatie reizigers](/help/forms/assets/traveler-info-form.png)

Voeg de volgende coderegel toe, zoals wordt uitgelegd in het dialoogvenster [create-custom-function](#create-custom-function) om acties uit te voeren in een specifieke instantie van het herhaalbare deelvenster, anders dan de laatste:

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

In dit voorbeeld wordt `hidePanelInRepeatablePanel` aangepaste functies voeren een handeling uit in een specifieke instantie van het herhaalbare deelvenster. In de bovenstaande code: `travelerinfo` vertegenwoordigt het herhaalbare paneel. De `repeatablePanel[1].traveler, {visible: false}` code verbergt het deelvenster in de tweede instantie van het herhaalbare deelvenster.

Laten we een knop toevoegen met het label `Hide` en voeg een regel toe om de tweede instantie van een herhaalbaar deelvenster te verbergen.

![Deelvensterregel verbergen](/help/forms/assets/custom-function-hidepanel-rule.png)

In de onderstaande video ziet u hoe `Hide` Wanneer op het deelvenster in de tweede herhaalbare instantie wordt geklikt, wordt het volgende verborgen:

>[!VIDEO](https://video.tv.adobe.com/v/3429554?quality=12&learn=on)

+++

+++ **Usecase**: Vul het veld vooraf met een waarde in wanneer het formulier wordt geladen

Voeg de volgende coderegel toe, zoals wordt uitgelegd in de [create-custom-function](#create-custom-function) om de vooraf ingevulde waarde in een veld te laden wanneer het formulier wordt geïnitialiseerd:

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

In de bovenstaande code `testImportData` functie vult de `Booking Amount` tekstveld wanneer het formulier wordt geladen. Laten we ervan uitgaan dat het boekingsformulier het minimumboekingsbedrag vereist `10,000`.

Laten we een regel maken bij het initialiseren van formulieren, waarbij de waarde in het dialoogvenster `Booking Amount` Het tekstvakveld wordt vooraf gevuld met een opgegeven waarde wanneer het formulier wordt geladen:

![Gegevensregel importeren](/help/forms/assets/custom-function-import-data.png)

Raadpleeg de onderstaande schermafbeelding om aan te tonen dat bij het laden van het formulier de waarde in het dialoogvenster `Booking Amount` Tekstvak is vooraf gevuld met een opgegeven waarde:

![Formulier gegevensregel importeren](/help/forms/assets/custom-function-prefill-form.png)

+++

+++ **Usecase**: Focus instellen op het specifieke veld

Voeg de volgende coderegel toe, zoals wordt uitgelegd in de [create-custom-function](#create-custom-function) -sectie, om focus in te stellen op het opgegeven veld wanneer de `Submit` wordt geklikt.:

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

Laten we een regel toevoegen aan de `Submit` knop om focus in te stellen op de `Email ID` textbox-veld wanneer erop wordt geklikt:

![Focusregel instellen](/help/forms/assets/custom-function-set-focus.png)

Raadpleeg de onderstaande schermafbeelding om aan te tonen dat wanneer de `Submit` wordt geklikt, wordt de focus ingesteld op de knop `Email ID` veld:

![Focusregel instellen](/help/forms/assets/custom-function-set-focus-form.png)

>[!NOTE]
>
> U kunt de optionele `$focusOption` parameter, als u zich op het volgende of vorige gebied met betrekking tot wilt concentreren `email` veld.

+++

+++ **Usecase**: Voeg een herhaalbaar deelvenster toe of verwijder dit met het gereedschap `dispatchEvent` eigenschap

Voeg de volgende coderegel toe, zoals wordt uitgelegd in de [create-custom-function](#create-custom-function) om een deelvenster toe te voegen wanneer de `Add Traveler` op de knop wordt geklikt met de `dispatchEvent` eigenschap:

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

Laten we een regel toevoegen aan de `Add Traveler` om het herhaalbare deelvenster toe te voegen wanneer erop wordt geklikt:

![Deelvensterregel toevoegen](/help/forms/assets/custom-function-add-panel.png)

Verwijs naar gif hieronder, die aantoont dat wanneer `Add Traveler` als erop wordt geklikt, wordt het deelvenster toegevoegd met de `dispatchEvent` eigenschap:

![Deelvenster toevoegen](/help/forms/assets/custom-function-add-panel.gif)

Voeg op dezelfde manier de volgende coderegel toe, zoals uitgelegd in de [create-custom-function](#create-custom-function) om een deelvenster te verwijderen als de `Delete Traveler` op de knop wordt geklikt met de `dispatchEvent` eigenschap:

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

Laten we een regel toevoegen aan de `Delete Traveler` om het herhaalbare deelvenster te verwijderen wanneer erop wordt geklikt:

![Deelvensterregel verwijderen](/help/forms/assets/custom-function-delete-panel.png)

Verwijs naar gif hieronder, die aantoont dat wanneer `Delete Traveler` wanneer op de knop wordt geklikt, wordt het deelvenster Reiser verwijderd met de opdracht `dispatchEvent` eigenschap:

![Deelvenster verwijderen](/help/forms/assets/custom-function-delete-panel.gif)

+++

## Ondersteuning voor caching van aangepaste functies

De adaptieve Forms voert caching voor douanefuncties uit om reactietijd te verbeteren terwijl het terugwinnen van de lijst van de douanefunctie in de regelredacteur. Een bericht als `Fetched following custom functions list from cache` in het dialoogvenster `error.log` bestand.

![aangepaste functie met cacheondersteuning](/help/forms/assets/custom-function-cache-error.png)

Als de aangepaste functies worden gewijzigd, wordt het in cache plaatsen ongeldig en wordt het geparseerd.

## Problemen oplossen {#troubleshooting}

* Als de manager van de douanevoorlegging niet zoals verwacht in bestaande AEM Projecten of vormen uitvoert, voer de volgende stappen uit:
   * Zorg ervoor dat de [kerncomponentenversie wordt bijgewerkt naar 3.0.18 en hoger](https://github.com/adobe/aem-core-forms-components). Voor bestaande AEM projecten en formulieren moeten echter aanvullende stappen worden ondernomen:

   * Voor het AEM project moet de gebruiker alle instanties van `submitForm('custom:submitSuccess', 'custom:submitError')` with `submitForm()` en implementeer het project via de Cloud Manager-pijplijn.

   * Voor bestaande formulieren moet de gebruiker, als de aangepaste verzendingsafhandelingen niet correct werken, de `submitForm` de regels inzake **Verzenden** gebruiken van de Redacteur van de Regel. Deze handeling vervangt de bestaande regel door `submitForm('custom:submitSuccess', 'custom:submitError')` with `submitForm()` in het formulier.


* Als het JavaScript-bestand met code voor aangepaste functies een fout bevat, worden de aangepaste functies niet vermeld in de regeleditor van een adaptief formulier. Als u de lijst met aangepaste functies wilt controleren, navigeert u naar de `error.log` bestand voor de fout. In het geval van een fout wordt de lijst met aangepaste functies leeg weergegeven:

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


