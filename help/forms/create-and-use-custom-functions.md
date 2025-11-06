---
title: Aangepaste functies in een adaptief formulier gebruiken
description: AEM Forms ondersteunt aangepaste functies, waarmee gebruikers hun eigen functies in de regeleditor kunnen maken en gebruiken.
keywords: Voeg een douanefunctie toe, gebruik een douanefunctie, creeer een douanefunctie, gebruik douanefunctie in regel redacteur.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 24607dd1-2d65-480b-a831-9071e20c473d
role: User, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1336'
ht-degree: 0%

---


# Inleiding tot aangepaste functies voor adaptieve Forms op basis van kerncomponenten

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/forms/adaptive-forms-core-components/create-and-use-custom-functions-core-components) |
| AEM as a Cloud Service | Dit artikel |

AEM Forms ondersteunt aangepaste functies, zodat gebruikers JavaScript-functies kunnen definiëren voor het implementeren van complexe bedrijfsregels. Deze aangepaste functies vergroten de mogelijkheden van formulieren door het bewerken en verwerken van ingevoerde gegevens te vergemakkelijken, zodat aan bepaalde vereisten wordt voldaan. Met deze opties kunt u het formuliergedrag dynamisch wijzigen op basis van vooraf gedefinieerde criteria. Met aangepaste functies kunnen ontwikkelaars ook complexe validatielogica afdwingen, dynamische berekeningen uitvoeren en de weergave of het gedrag van formulierelementen bepalen op basis van gebruikersinteracties of vooraf gedefinieerde criteria.

>[!NOTE]
>
> Zorg ervoor dat de [&#x200B; kerncomponent &#x200B;](https://github.com/adobe/aem-core-forms-components) aan de recentste versie wordt geplaatst om de recentste eigenschappen te gebruiken.

## Gebruik van aangepaste functies {#uses-of-custom-function}

De voordelen van het gebruik van aangepaste functies in Adaptive Forms zijn:

* **Verwerking van gegevens**: De functies van de douane verwerken gegevens ingegaan in de vormgebieden.
* **Bevestiging van gegevens**: De functies van de douane laten u toe om douanecontroles op vorminput uit te voeren en gespecificeerde foutenmeldingen te verstrekken.
* **Dynamisch gedrag**: De functies van de douane staan u toe om het dynamische gedrag van uw vormen te controleren die op specifieke voorwaarden worden gebaseerd. U kunt bijvoorbeeld velden weergeven/verbergen, veldwaarden wijzigen of de logica van het formulier dynamisch aanpassen.
* **Integratie**: U kunt douanefuncties gebruiken om met externe APIs of de diensten te integreren. Het helpt in het halen van gegevens uit externe bronnen, het verzenden van gegevens naar externe rustpunten, of het uitvoeren van douaneacties die op externe gebeurtenissen worden gebaseerd.

Aangepaste functies zijn in wezen clientbibliotheken die in het JavaScript-bestand worden toegevoegd. Zodra u een douanefunctie creeert, wordt het beschikbaar in de regelredacteur voor selectie door de gebruiker in een Aangepast Vorm. De douanefuncties worden geïdentificeerd door de aantekeningen van JavaScript in de regelredacteur.

## Ondersteunde JavaScript-annotaties voor aangepaste functies {#js-annotations}

JavaScript-annotaties worden gebruikt om metagegevens voor JavaScript-code te verschaffen. Het bevat opmerkingen die beginnen met specifieke symbolen, bijvoorbeeld /** en @. De annotaties bevatten belangrijke informatie over functies, variabelen en andere elementen in de code. Het adaptieve formulier ondersteunt de volgende JavaScript-annotaties voor aangepaste functies:

### Naam

De naam wordt gebruikt om de douanefunctie in de regelredacteur van een Aangepast Vorm te identificeren. De volgende syntaxis wordt gebruikt om een douanefunctie te noemen:

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`.
  `functionName` is de naam van de functie. Spaties zijn niet toegestaan.
  `<Function Name>` is de weergavenaam van de functie in de regeleditor van een adaptief formulier.
Als de functienaam identiek is aan de naam van de functie zelf, kunt u `[functionName]` weglaten uit de syntaxis.

### Parameter

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
   * bereik: vertegenwoordigt het globals object, dat alleen-lezen variabelen bevat, zoals formulierinstanties, doelveldinstanties en methoden voor het uitvoeren van formulierwijzigingen binnen aangepaste functies. Deze wordt gedeclareerd als de laatste parameter in JavaScript-annotaties en is niet zichtbaar in de regeleditor van een adaptief formulier. De bereikparameter benadert het object van het formulier of de component om de regel of gebeurtenis te activeren die vereist is voor formulierverwerking. Voor verdere informatie over het voorwerp Globals en hoe te om het te gebruiken, [&#x200B; klik hier &#x200B;](/help/forms/custom-function-core-component-scope-function.md).

Het parametertype is niet hoofdlettergevoelig en spaties zijn niet toegestaan in de parameternaam.

`<Parameter Description>` bevat details over het doel van de parameter. Het kan meerdere woorden hebben.

#### Optionele parameters

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

![&#x200B; Optionele of vereiste parameters &#x200B;](/help/forms/assets/optional-default-params.png)

U kunt de regel opslaan zonder een waarde voor de vereiste parameters op te geven, maar de regel wordt niet uitgevoerd en er wordt een waarschuwingsbericht weergegeven als:

![&#x200B; onvolledige regelwaarschuwing &#x200B;](/help/forms/assets/incomplete-rule.png)

Wanneer de gebruiker de optionele parameter leeg laat, wordt de &#39;Undefined&#39;-waarde doorgegeven aan de aangepaste functie voor de optionele parameter.

Meer over leren hoe te om facultatieve parameters in JSDocs te bepalen, [&#x200B; klik hier &#x200B;](https://jsdoc.app/tags-param).

### Retourtype

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

### Persoonlijk

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

## Bekend probleem

* Aangepaste functies ondersteunen geen reguliere-expressieliterals van JavaScript. Het gebruik van regex-literals in een aangepaste functie resulteert in fouten tijdens de uitvoering. Bijvoorbeeld:
  `const pattern = /^abc$/;`

  Voor compatibiliteit gebruikt u de constructor RegExp in de aangepaste functies.

  `const pattern = new RegExp("^abc$");`
Reguliere expressies van Refactor om de constructor RegExp te gebruiken voor consistente en betrouwbare uitvoering.

## Volgende stap

Om een douanefunctie in uw AanpassingsVorm tot stand te brengen en te gebruiken, verwijs naar [&#x200B; creeer een Functie van de Douane voor een AanpassingsVorm die op het artikel van de Componenten van de Kern wordt gebaseerd &#x200B;](/help/forms/custom-function-core-component-create-function.md).

## Zie ook

{{see-also-rule-editor}}