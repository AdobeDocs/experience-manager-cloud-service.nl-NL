---
title: Aangepaste functies maken en toevoegen in een adaptief formulier
description: AEM Forms ondersteunt aangepaste functies, waarmee gebruikers hun eigen functies in de regeleditor kunnen maken en gebruiken.
keywords: Voeg een douanefunctie toe, gebruik een douanefunctie, creeer een douanefunctie, gebruik douanefunctie in regel redacteur.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 24607dd1-2d65-480b-a831-9071e20c473d
role: User, Developer
source-git-commit: 52b87073cad84705b5dc0c6530aff44d1e686609
workflow-type: tm+mt
source-wordcount: '4322'
ht-degree: 0%

---


# Aangepaste functies in Adaptive Forms (Core Components)

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/adaptive-forms-core-components/create-and-use-custom-functions) |
| AEM as a Cloud Service | Dit artikel |

## Inleiding

AEM Forms ondersteunt aangepaste functies, zodat gebruikers JavaScript-functies kunnen definiëren voor het implementeren van complexe bedrijfsregels. Deze aangepaste functies vergroten de mogelijkheden van formulieren door het bewerken en verwerken van ingevoerde gegevens te vergemakkelijken, zodat aan bepaalde vereisten wordt voldaan. Ze maken het ook mogelijk het formuliergedrag dynamisch te wijzigen op basis van vooraf gedefinieerde criteria.

>[!NOTE]
>
> Zorg ervoor dat de [ kerncomponent ](https://github.com/adobe/aem-core-forms-components) aan de recentste versie wordt geplaatst om de recentste eigenschappen te gebruiken.

### Gebruik van aangepaste functies {#uses-of-custom-function}

De voordelen van het gebruik van aangepaste functies in Adaptive Forms zijn:
* **Verwerking van gegevens**: De functies van de douane verwerken gegevens ingegaan in de vormgebieden.
* **Bevestiging van gegevens**: De functies van de douane laten u toe om douanecontroles op vorminput uit te voeren en gespecificeerde foutenmeldingen te verstrekken.
* **Dynamisch gedrag**: De functies van de douane staan u toe om het dynamische gedrag van uw vormen te controleren die op specifieke voorwaarden worden gebaseerd. U kunt bijvoorbeeld velden weergeven/verbergen, veldwaarden wijzigen of de logica van het formulier dynamisch aanpassen.
* **Integratie**: U kunt douanefuncties gebruiken om met externe APIs of de diensten te integreren. Het helpt in het halen van gegevens uit externe bronnen, het verzenden van gegevens naar externe rustpunten, of het uitvoeren van douaneacties die op externe gebeurtenissen worden gebaseerd.

Aangepaste functies zijn in wezen clientbibliotheken die in het JavaScript-bestand worden toegevoegd. Zodra u een douanefunctie creeert, wordt het beschikbaar in de regelredacteur voor selectie door de gebruiker in een Aangepast Vorm. De douanefuncties worden geïdentificeerd door de aantekeningen van JavaScript in de regelredacteur.

### Ondersteunde JavaScript-annotaties voor aangepaste functies {#js-annotations}

JavaScript-annotaties worden gebruikt om metagegevens voor JavaScript-code te verschaffen. Het bevat opmerkingen die beginnen met specifieke symbolen, bijvoorbeeld /** en @. De annotaties bevatten belangrijke informatie over functies, variabelen en andere elementen in de code. Het adaptieve formulier ondersteunt de volgende JavaScript-annotaties voor aangepaste functies:

#### Naam

De naam wordt gebruikt om de douanefunctie in de regelredacteur van een Aangepast Vorm te identificeren. De volgende syntaxis wordt gebruikt om een douanefunctie te noemen:

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`.
  `functionName` is de naam van de functie. Spaties zijn niet toegestaan.
  `<Function Name>` is de weergavenaam van de functie in de regeleditor van een adaptief formulier.
Als de functienaam identiek is aan de naam van de functie zelf, kunt u `[functionName]` weglaten uit de syntaxis.

#### Parameter

De parameter is een lijst met argumenten die door aangepaste functies worden gebruikt. Een functie kan meerdere parameters ondersteunen. De volgende syntaxis wordt gebruikt om een parameter in een douanefunctie te bepalen:

* `@param {type} name <Parameter Description>`
* `@argument` `{type} name <Parameter Description>`
* `@arg` `{type}` `name <Parameter Description>` .
  `{type}` staat voor het parametertype.  De toegestane parametertypen zijn:

   * tekenreeks: vertegenwoordigt één tekenreekswaarde.
   * getal: vertegenwoordigt één numerieke waarde.
   * boolean: vertegenwoordigt één booleaanse waarde (waar of onwaar).
   * string []: Geeft een array van tekenreekswaarden aan.
   * getal []: vertegenwoordigt een array van numerieke waarden.
   * boolean [] : vertegenwoordigt een array van Booleaanse waarden.
   * date: vertegenwoordigt één datumwaarde.
   * date []: Vertegenwoordigt een serie van datumwaarden.
   * array: vertegenwoordigt een algemene array met waarden van verschillende typen.
   * object: vertegenwoordigt een formulierobject dat aan een aangepaste functie wordt doorgegeven in plaats van dat de waarde rechtstreeks wordt doorgegeven.
   * bereik: vertegenwoordigt het globals object, dat alleen-lezen variabelen bevat, zoals formulierinstanties, doelveldinstanties en methoden voor het uitvoeren van formulierwijzigingen binnen aangepaste functies. Deze wordt gedeclareerd als de laatste parameter in JavaScript-annotaties en is niet zichtbaar in de regeleditor van een adaptief formulier. De bereikparameter benadert het object van het formulier of de component om de regel of gebeurtenis te activeren die vereist is voor formulierverwerking. Voor verdere informatie over het voorwerp Globals en hoe te om het te gebruiken, [ klik hier ](/help/forms/create-and-use-custom-functions.md#support-field-and-global-objects).

Het parametertype is niet hoofdlettergevoelig en spaties zijn niet toegestaan in de parameternaam.

`<Parameter Description>` bevat details over het doel van de parameter. Het kan meerdere woorden hebben.

**Facultatieve Parameters**
Standaard zijn alle parameters verplicht. U kunt een parameter als optioneel definiëren door `=` toe te voegen achter het parametertype of door de parameternaam in `[]` te plaatsen. Parameters die in JavaScript-annotaties als optioneel worden gedefinieerd, worden in de regeleditor als optioneel weergegeven.
Als u een variabele wilt definiëren als een optionele parameter, kunt u een van de volgende syntaxis gebruiken:

* `@param {type=} Input1`

In de bovenstaande coderegel is `Input1` een optionele parameter zonder standaardwaarde. Optionele parameter met standaardwaarde declareren:
`@param {string=<value>} input1`

`input1` als een optionele parameter met de standaardwaarde ingesteld op `value` .

* `@param {type} [Input1]`

In de bovenstaande coderegel is `Input1` een optionele parameter zonder standaardwaarde. Optionele parameter met standaardwaarde declareren:
`@param {array} [input1=<value>]`
`input1` is een optionele parameter van het type array met de standaardwaarde `value` .
Zorg ervoor dat het parametertype wordt ingesloten door accolades {} en dat de parameternaam wordt ingesloten door vierkante haakjes.

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

De volgende illustratie wordt weergegeven met behulp van de aangepaste functie `OptionalParameterFunction` in de regeleditor:

![ Optionele of vereiste parameters ](/help/forms/assets/optional-default-params.png)

U kunt de regel opslaan zonder een waarde voor de vereiste parameters op te geven, maar de regel wordt niet uitgevoerd en er wordt een waarschuwingsbericht weergegeven als:

![ onvolledige regelwaarschuwing ](/help/forms/assets/incomplete-rule.png)

Wanneer de gebruiker de optionele parameter leeg laat, wordt de &#39;Undefined&#39;-waarde doorgegeven aan de aangepaste functie voor de optionele parameter.

Meer over leren hoe te om facultatieve parameters in JSDocs te bepalen, [ klik hier ](https://jsdoc.app/tags-param).

#### Retourtype

Het retourneringstype geeft het type waarde op dat de aangepaste functie na de uitvoering retourneert. De volgende syntaxis wordt gebruikt om een terugkeertype in een douanefunctie te bepalen:

* `@return {type}`
* `@returns {type}`
  `{type}` staat voor het retourneringstype van de functie. De toegestane retourtypen zijn:
   * tekenreeks: vertegenwoordigt één tekenreekswaarde.
   * getal: vertegenwoordigt één numerieke waarde.
   * boolean: vertegenwoordigt één booleaanse waarde (waar of onwaar).
   * string []: Geeft een array van tekenreekswaarden aan.
   * getal []: vertegenwoordigt een array van numerieke waarden.
   * boolean [] : vertegenwoordigt een array van Booleaanse waarden.
   * date: vertegenwoordigt één datumwaarde.
   * date []: Vertegenwoordigt een serie van datumwaarden.
   * array: vertegenwoordigt een algemene array met waarden van verschillende typen.
   * object: vertegenwoordigt een formulierobject in plaats van de waarde rechtstreeks.

  Het terugkeertype is niet case-sensitive.

#### Persoonlijk

De aangepaste functie die als private is gedeclareerd, komt niet voor in de lijst met aangepaste functies in de regeleditor van een adaptief formulier. Aangepaste functies zijn standaard openbaar. De syntaxis voor het declareren van een aangepaste functie als private is `@private` .


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
Als de gebruiker geen JavaScript-annotaties toevoegt aan de aangepaste functie, wordt deze door de functienaam in de regeleditor weergegeven. Het wordt echter aanbevolen JavaScript-annotaties op te nemen om de leesbaarheid van de aangepaste functies te verbeteren.

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

### Functie-expressie met verplichte JavaScript-annotaties of -commentaar

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

Creeer een cliëntbibliotheek om douanefuncties in de regelredacteur te roepen. Voor meer informatie, zie [ Gebruikend cliënt-Kant Bibliotheken ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html#developing).

Stappen voor het maken van aangepaste functies zijn:
1. [Een clientbibliotheek maken](#create-client-library)
1. [Clientbibliotheek toevoegen aan een adaptief formulier](#use-custom-function)


### Vereisten om een aangepaste functie te maken

Voordat u een aangepaste functie toevoegt aan de Adaptive Forms, moet u het volgende doen:

**Software:**

* **Onbewerkte Redacteur van de Tekst (winde)**: Terwijl om het even welke duidelijke tekstredacteur kan werken, biedt een Geïntegreerde Milieu van de Ontwikkeling (winde) zoals de Code van Microsoft Visual Studio geavanceerde eigenschappen voor het gemakkelijkere uitgeven aan.

* **Git:** Dit systeem van de versiecontrole wordt vereist voor het beheren van codeveranderingen. Als u deze niet hebt geïnstalleerd, kunt u deze downloaden van https://git-scm.com.

### Een clientbibliotheek maken {#create-client-library}

U kunt aangepaste functies toevoegen door een clientbibliotheek toe te voegen. Voer de volgende stappen uit om een clientbibliotheek te maken:

**Kloon de Bewaarplaats**

Kloon uw [ as a Cloud Service Bewaarplaats van AEM Forms ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git):

1. Open de opdrachtregel of het terminalvenster.

1. Navigeer naar de gewenste locatie op uw computer waar u de opslagplaats wilt opslaan.

1. Voer de volgende opdracht uit om de gegevensopslagruimte te klonen:

   `git clone [Git Repository URL]`

Met deze opdracht downloadt u de opslagplaats en maakt u een lokale map van de gekloonde opslagplaats op uw computer. Door deze gids, verwijzen wij naar deze omslag als [ AEMaaCS projectfolder ].

**voeg een Omslag van de Bibliotheek van de Cliënt toe**

Om nieuwe omslag van de cliëntbibliotheek aan de [ AEMaaCS projectfolder ] toe te voegen, volg deze stappen:

1. Open de [ AEMaaCS projectfolder ] in een redacteur.

   ![ de omslagstructuur van de douanefunctie ](/help/forms/assets/custom-library-folder-structure.png)

1. Zoek `ui.apps` .
1. Nieuwe map toevoegen. Voeg bijvoorbeeld een map toe met de naam `experience-league` .
1. Navigeer naar de map `/experience-league/` en voeg een `ClientLibraryFolder` toe. Maak bijvoorbeeld een clientbibliotheekmap met de naam `customclientlibs` .

   `Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/`

**voegt dossiers en omslagen aan de omslag van de Bibliotheek van de Cliënt toe**

Voeg het volgende toe aan de toegevoegde omslag van de cliëntbibliotheek:

* .content.xml, bestand
* js.txt, bestand
* map js

`Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/experience-league/customclientlibs/`

1. Voeg in `.content.xml` de volgende coderegels toe:

   ```javascript
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="cq:ClientLibraryFolder"
   categories="[customfunctionscategory]"/>
   ```

   >[!NOTE]
   >
   > U kunt een willekeurige naam kiezen voor de eigenschappen `client library folder` en `categories` .

1. Voeg in `js.txt` de volgende coderegels toe:

   ```javascript
         #base=js
       function.js
   ```
1. Voeg in de map `js` het javascript-bestand toe als `function.js` dat de aangepaste functies bevat:

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

![ de omslagstructuur van de douanefunctie ](/help/forms/assets/custom-function-added-files.png)

**omvat de nieuwe omslag in filter.xml**:

1. Navigeer aan het `/ui.apps/src/main/content/META-INF/vault/filter.xml` dossier in uw [ AEMaaCS projectfolder ].

1. Open het bestand en voeg de volgende regel aan het einde toe:

   `<filter root="/apps/experience-league" />`
1. Sla het bestand op.

![ de filter xml van de douanefunctie {](/help/forms/assets/custom-function-filterxml.png)

**stel de pas gecreëerde de bibliotheekomslag van de Cliënt aan uw AEM milieu** op

Stel AEM as a Cloud Service, [ AEMaaCS projectfolder ], aan uw milieu van de Cloud Service op. Implementeren in uw Cloud Service-omgeving:

1. De wijzigingen vastleggen

   1. U kunt de wijzigingen in de opslagplaats toevoegen, vastleggen en doorvoeren met behulp van de onderstaande opdrachten:

   ```javascript
       git add .
       git commit -a -m "Adding custom functions"
       git push
   ```

1. De bijgewerkte code implementeren:

   1. Trigger een plaatsing van uw code door de bestaande full-stack pijpleiding. Hiermee wordt de bijgewerkte code automatisch samengesteld en geïmplementeerd.

Als u niet reeds opstelling een pijpleiding hebt, verwijs naar de gids op [ hoe te opstelling een pijpleiding voor AEM Forms as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline).

Zodra de pijpleiding met succes wordt uitgevoerd, wordt de douanefunctie die in de cliëntbibliotheek wordt toegevoegd beschikbaar in uw [ Aangepaste redacteur van de Regel van de Vorm ](/help/forms/rule-editor-core-components.md).

### Clientbibliotheek toevoegen aan een adaptief formulier{#use-custom-function}

Zodra u de clientbibliotheek hebt geïmplementeerd in uw Forms CS-omgeving, gebruikt u de mogelijkheden van de clientbibliotheek in uw adaptieve formulier. De clientbibliotheek toevoegen aan uw adaptieve formulier

1. Open het formulier in de bewerkingsmodus. Als u een formulier wilt openen in de bewerkingsmodus, selecteert u een formulier en selecteert u **[!UICONTROL Edit]** .
1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open het tabblad **[!UICONTROL Basic]** en selecteer de naam van de **[!UICONTROL client library category]** in de vervolgkeuzelijst (in dit geval selecteert u `customfunctionscategory` ).

   ![ Toevoegend de de cliëntbibliotheek van de douanefunctie ](/help/forms/assets/clientlib-custom-function.png)

   >[!NOTE]
   >
   > U kunt meerdere categorieën toevoegen door een door komma&#39;s gescheiden lijst op te geven in het veld **[!UICONTROL Client library category]** .

1. Klik op **[!UICONTROL Done]**.

U kunt de douanefunctie in de [ regelredacteur van een Aangepaste Vorm ](/help/forms/rule-editor-core-components.md) gebruiken gebruikend de [ annotaties van JavaScript ](##js-annotations).

## Een aangepaste functie gebruiken in een adaptief formulier

In een AanpassingsVorm, kunt u [ douanefuncties binnen de regelredacteur ](/help/forms/rule-editor-core-components.md) gebruiken. Voeg de volgende code toe aan het JavaScript-bestand (`Function.js` ) om de leeftijd te berekenen op basis van de geboortedatum (JJJJ-MM-DD). Maak een aangepaste functie als `calculateAge()` die de geboortedatum als invoer neemt en de leeftijd retourneert:

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

In het bovenstaande voorbeeld wordt de aangepaste functie `calculateAge` aangeroepen en wordt de leeftijd geretourneerd wanneer de gebruiker de geboortedatum in de notatie invoert (JJJJ-MM-DD).

![ Calcualte tegen douanefunctie in de Redacteur van de Regel ](/help/forms/assets/custom-function-calculate-age.png)

Bekijk een voorbeeld van het formulier om te zien hoe de aangepaste functies worden geïmplementeerd via de regeleditor:

![ berekent tegen douanefunctie in de Voorproef van de Vorm van de Redacteur van de Regel ](/help/forms/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> U kunt naar de volgende [ omslag van de douanefunctie ](/help/forms/assets//customfunctions.zip) verwijzen. Download en installeer deze omslag in uw AEM instantie gebruikend de [ Manager van het Pakket ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).


### Opties voor vervolgkeuzelijsten instellen met behulp van aangepaste functies

De Redacteur van de regel in de Componenten van de Kern steunt niet de **Vastgestelde Opties van** bezit om de opties van de dropdown lijst bij runtime te plaatsen. U kunt de opties voor de vervolgkeuzelijst echter instellen met behulp van aangepaste functies.

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

In de bovenstaande code wordt `setEnums` gebruikt om de eigenschap `enum` in te stellen en wordt `setEnumNames` gebruikt om de eigenschap `enumNames` van het vervolgkeuzemenu in te stellen.

Maak een regel voor de knop `Next` , die de waarde van de keuzelijst instelt wanneer de gebruiker op de knop `Next` klikt:

![ drop-down lijstopties ](/help/forms/assets/drop-down-list-options.png)

Raadpleeg de onderstaande afbeelding om aan te tonen waar de opties van de vervolgkeuzelijst zijn ingesteld wanneer u op de knop Weergeven klikt:

![ drop-down opties in de regeleditor ](/help/forms/assets/drop-down-option-rule-editor.png)



### Ondersteuning voor asynchrone functies in aangepaste functies {#support-of-async-functions}

De asynchrone douanefuncties verschijnen niet in de lijst van de regelredacteur. Het is echter mogelijk om asynchrone functies aan te roepen binnen aangepaste functies die zijn gemaakt met synchrone functie-expressies.

![ Synchronisatie en async douanefunctie ](/help/forms/assets/workflow-for-sync-async-custom-fumction.png)

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

In het bovenstaande voorbeeld is de functie asyncFunction een `asynchronous function` . De toepassing voert een asynchrone bewerking uit door een `GET` -aanvraag in te dienen bij `https://petstore.swagger.io/v2/store/inventory` . Het wacht op de reactie met `await`, parseert de hoofdtekst van de reactie met JSON met de `response.json()` en retourneert de gegevens. De functie `callAsyncFunction` is een synchrone aangepaste functie die de functie `asyncFunction` aanroept en de reactiegegevens in de console weergeeft. Hoewel de functie `callAsyncFunction` synchroon is, roept deze de asynchrone functie asynchrone functie asyncFunction aan en verwerkt deze het resultaat met `then` - en `catch` -instructies.

Om zijn het werken te zien, laten wij een knoop toevoegen en een regel voor de knoop creëren die de asynchrone functie na een knoop klikt.

![ creërend regel voor async functie ](/help/forms/assets/rule-for-async-funct.png)

Raadpleeg de illustratie van het onderstaande consolevenster om aan te tonen dat wanneer de gebruiker op de knop `Fetch` klikt, de aangepaste functie `callAsyncFunction` wordt aangeroepen, die op zijn beurt een asynchrone functie `asyncFunction` aanroept. Inspect het consolevenster om de reactie op de knoop te bekijken klik:

![ venster van de Console ](/help/forms/assets/async-custom-funct-console.png)

Laten we eens kijken naar de functies van aangepaste functies.

## Verschillende functies voor Aangepaste functies

U kunt aangepaste functies gebruiken om aangepaste functies toe te voegen aan formulieren. Deze functies ondersteunen diverse mogelijkheden, zoals het werken met specifieke velden, het gebruik van globale velden of caching. Dankzij deze flexibiliteit kunt u formulieren aanpassen aan de vereisten van uw organisatie.

### Veld- en globale bereikobjecten in aangepaste functies {#support-field-and-global-objects}

Veldobjecten verwijzen naar de afzonderlijke componenten of elementen in een formulier, zoals tekstvelden, selectievakjes. Het object Globals bevat alleen-lezen variabelen, zoals formulierinstantie, doelveldinstantie en methoden voor het uitvoeren van formulierwijzigingen binnen aangepaste functies.

>[!NOTE]
>
> `param {scope} globals` moet de laatste parameter zijn en wordt niet weergegeven in de regeleditor van een adaptief formulier.

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

Laten we leren hoe aangepaste functies veld- en globale objecten gebruiken met behulp van een `Contact Us` -formulier. Hierbij wordt gebruikgemaakt van verschillende gebruiksgevallen.

![ Vorm van het Contact ons ](/help/forms/assets/contact-us-form.png)

+++ **Geval van het Gebruik**: toon een paneel gebruikend de `SetProperty` regel

Voeg de volgende code in de douanefunctie toe zoals die in [ wordt verklaard creeer-douane-functie ](#create-custom-function) sectie, om het vormgebied als `Required` te plaatsen.

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

+++

+++ **Geval van het Gebruik**: Valideer het gebied.

Voeg de volgende code in de douanefunctie toe zoals die in [ wordt verklaard creeer-douane-functie ](#create-custom-function) sectie, om het gebied te bevestigen.

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

+++

+++ **Geval van het Gebruik**: Herstel een paneel

Voeg de volgende code in de douanefunctie toe zoals die in [ wordt verklaard creeer-douane-functie ](#create-custom-function) sectie, om het paneel terug te stellen.

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

+++

+++ **Geval van het Gebruik**: Om een douanebericht op het gebiedsniveau te tonen en het gebied als ongeldig te merken

Met de functie `markFieldAsInvalid()` kunt u een veld definiëren als ongeldig en een aangepast foutbericht instellen op veldniveau. De `fieldIdentifier` -waarde kan `fieldId` , `field qualifiedName` of `field dataRef` zijn. De waarde van het object met de naam `option` kan `{useId: true}` , `{useQualifiedName: true}` of `{useDataRef: true}` zijn.
De syntaxis die wordt gebruikt om een veld als ongeldig te markeren en een aangepast bericht in te stellen is:

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Voeg de volgende code in de douanefunctie toe zoals die in [ wordt verklaard creeer-douane-functie ](#create-custom-function) sectie, om een douanebericht op het gebiedsniveau toe te laten.

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

+++

+++ **Geval van het Gebruik**: Verzend veranderde gegevens aan de server

De volgende regel code:
`globals.functions.submitForm(globals.functions.exportData(), false);` wordt gebruikt om de formuliergegevens te verzenden na manipulatie.
* Het eerste argument betreft de gegevens die moeten worden ingediend.
* Het tweede argument geeft aan of het formulier moet worden gevalideerd voordat het wordt verzonden. Deze is `optional` en wordt standaard ingesteld op `true` .
* Het derde argument is de `contentType` van de verzending, die ook optioneel is met de standaardwaarde `multipart/form-data` . De andere waarden kunnen `application/json` en `application/x-www-form-urlencoded` zijn.

Voeg de volgende code in de douanefunctie toe zoals die in [ wordt verklaard creeer-douane-functie ](#create-custom-function) sectie, om de gemanipuleerde gegevens bij de server voor te leggen:

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

+++

+++ **Geval van het Gebruik**: Het succes van de vormvoorlegging en foutenmanagers van de met voeten treden

Voeg de volgende lijn van code toe zoals die in [ wordt verklaard creeer-douane-functie ](#create-custom-function) sectie, om de voorlegging of het mislukkingsbericht voor vormvoorlegging aan te passen en de berichten van de vormvoorlegging in een modaal vakje te tonen:

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

+++

+++ **Geval van het Gebruik**: Voer acties in een specifieke instantie van het herhaalbare paneel uit

Regels die u met de visuele regeleditor in een herhaalbaar deelvenster hebt gemaakt, worden toegepast op de laatste instantie van het herhaalbare deelvenster. Om een regel voor een specifieke instantie van het herhaalbare paneel te schrijven, kunnen wij een douanefunctie gebruiken.

Laten we een ander formulier maken om informatie te verzamelen over reizigers die naar een bestemming gaan. Er wordt een deelvenster voor reizigers toegevoegd als een herhaalbaar deelvenster, waar de gebruiker met de knop `Add Traveler` details voor 5 reizigers kan toevoegen.

![ Informatie van de reiziger ](/help/forms/assets/traveler-info-form.png)

Voeg de volgende lijn van code toe zoals die in [ wordt verklaard creeer-douane-functie ](#create-custom-function) sectie, om acties in een specifieke instantie van het herhaalbare paneel, buiten laatste uit te voeren:

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

+++

+++ **gebruik**: Vul het gebied met een waarde vooraf in wanneer de vorm laadt

Voeg de volgende lijn van code, zoals die in [ wordt verklaard creeer-douane-functie ](#create-custom-function) sectie, toe om de vooraf ingevulde waarde op een gebied te laden wanneer de vorm wordt geïnitialiseerd:

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

+++

+++ **Gebruik**: Plaats nadruk op het specifieke gebied

Voeg de volgende lijn van code, zoals die in [ wordt verklaard creeer-douane-functie ](#create-custom-function) sectie, toe om nadruk op het gespecificeerde gebied te plaatsen wanneer de `Submit` knoop wordt geklikt.:

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

+++

+++ **Gebruik**: voeg of schrap herhaalbaar paneel toe gebruikend het `dispatchEvent` bezit

Voeg de volgende lijn van code, zoals die in [ wordt verklaard creeer-douane-functie ](#create-custom-function) sectie, toe om een paneel toe te voegen wanneer de `Add Traveler` knoop gebruikend het `dispatchEvent` bezit wordt geklikt:

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

+++

## Ondersteuning voor caching van aangepaste functies

De adaptieve Forms voert caching voor douanefuncties uit om reactietijd te verbeteren terwijl het terugwinnen van de lijst van de douanefunctie in de regelredacteur. Er verschijnt een bericht als `Fetched following custom functions list from cache` in het `error.log` -bestand.

![ douanefunctie met geheim voorgeheugensteun ](/help/forms/assets/custom-function-cache-error.png)

Als de aangepaste functies worden gewijzigd, wordt het in cache plaatsen ongeldig en wordt het geparseerd.

## Problemen oplossen {#troubleshooting}

* Als de manager van de douanevoorlegging niet zoals verwacht in bestaande AEM Projecten of vormen uitvoert, voer de volgende stappen uit:
   * Zorg ervoor dat de [ versie van de kerncomponenten aan 3.0.18 en later ](https://github.com/adobe/aem-core-forms-components) wordt bijgewerkt. Voor bestaande AEM projecten en formulieren moeten echter aanvullende stappen worden ondernomen:

   * Voor het AEM project moet de gebruiker alle instanties van `submitForm('custom:submitSuccess', 'custom:submitError')` vervangen door `submitForm()` en het project implementeren via de Cloud Manager-pijplijn.

   * Voor bestaande vormen, als de managers van de douanevoorlegging niet correct functioneren, moet de gebruiker de `submitForm` regel op **openen en bewaren** knoop gebruikend de Redacteur van de Regel. Deze handeling vervangt de bestaande regel van `submitForm('custom:submitSuccess', 'custom:submitError')` door `submitForm()` in het formulier.


* Als het JavaScript-bestand met code voor aangepaste functies een fout bevat, worden de aangepaste functies niet vermeld in de regeleditor van een adaptief formulier. Als u de lijst met aangepaste functies wilt controleren, navigeert u naar het `error.log` -bestand voor de fout. In het geval van een fout wordt de lijst met aangepaste functies leeg weergegeven:

  ![ dossier van het foutenlogboek ](/help/forms/assets/custom-function-list-error-file.png)

  Als er geen fout optreedt, wordt de aangepaste functie opgehaald en in het `error.log` -bestand weergegeven. Er verschijnt een bericht als `Fetched following custom functions list` in het `error.log` -bestand:

  ![ dossier van het foutenlogboek met juiste douanefunctie ](/help/forms/assets/custom-function-list-fetched-in-error.png)

## Overwegingen

* De `parameter type` en `return type` bieden geen ondersteuning voor `None` .

* De functies die niet worden ondersteund in de lijst met aangepaste functies zijn:
   * Generatorfuncties
   * Functies Async/Await
   * Methodedefinities
   * Methoden van Class
   * Standaardparameters
   * Rustparameters

## Zie ook {#see-also}

{{see-also}}


