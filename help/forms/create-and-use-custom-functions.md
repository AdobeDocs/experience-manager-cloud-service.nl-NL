---
title: Aangepaste functies maken en toevoegen in een adaptief formulier
description: AEM Forms ondersteunt aangepaste functies waarmee gebruikers hun eigen functies in de regeleditor kunnen maken en gebruiken.
keywords: Voeg een douanefunctie toe, gebruik een douanefunctie, creeer een douanefunctie, gebruik douanefunctie in regel redacteur.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
source-git-commit: 94a290964a92f8c6ed353d9c77f3dd3b8a5598a4
workflow-type: tm+mt
source-wordcount: '774'
ht-degree: 0%

---


# Aangepaste functies in Adaptive Forms (Core Components)

## Inleiding

AEM Forms biedt ondersteuning voor aangepaste functies, zodat gebruikers JavaScript-functies kunnen definiëren voor het implementeren van complexe bedrijfsregels. Deze aangepaste functies vergroten de mogelijkheden van formulieren door het bewerken en verwerken van ingevoerde gegevens te vergemakkelijken, zodat aan bepaalde vereisten wordt voldaan. Ze maken het ook mogelijk het formuliergedrag dynamisch te wijzigen op basis van vooraf gedefinieerde criteria.
In Adaptive Forms kunt u aangepaste functies gebruiken in het dialoogvenster [regel-editor van een adaptief formulier](/help/forms/rule-editor.md#custom-functions) specifieke validatieregels voor formuliervelden te maken.

Laten we begrijpen hoe een aangepaste functie wordt gebruikt waarbij gebruikers het e-mailadres invoeren. Bovendien moet het ingevoerde e-mailadres een specifieke notatie hebben (het bevat een &#39;@&#39;-symbool en een domeinnaam). Maak een aangepaste functie als &quot;ValidateEmail&quot;, die het e-mailadres als invoer gebruikt en waar retourneert als het geldig en anders onwaar is.

```javascript
function ValidateEmail(inputText)
{
    var email = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/;
    if(inputText.value.match(email))
        {
            alert("Valid email address!");
            return true;
        }
    else
    {
        alert("Invalid email address!");
        return false;
    }
}
```

In het bovenstaande voorbeeld wordt de aangepaste functie &quot;ValidateEmail&quot; aangeroepen om te controleren of het ingevoerde e-mailadres geldig is wanneer de gebruiker het formulier probeert te verzenden.

### Gebruik van aangepaste functies {#uses-of-custom-function}

Enkele voordelen van het gebruik van aangepaste functies in Adaptive Forms zijn:

* **Manipulatie van gegevens**: Aangepaste functies bewerken en verwerken de gegevens die in de formuliervelden zijn ingevoerd.
* **Validatie van gegevens**: Met aangepaste functies kunt u aangepaste controles uitvoeren op de invoer van formulieren en opgegeven foutberichten weergeven.
* **Dynamisch gedrag**: Met aangepaste functies kunt u het dynamische gedrag van uw formulieren bepalen op basis van specifieke omstandigheden. U kunt bijvoorbeeld velden weergeven/verbergen, veldwaarden wijzigen of de logica van het formulier dynamisch aanpassen.
* **Integratie**: U kunt aangepaste functies gebruiken om te integreren met externe API&#39;s of services. Het helpt in het halen van gegevens uit externe bronnen, het verzenden van gegevens naar externe rustpunten, of het uitvoeren van douaneacties die op externe gebeurtenissen worden gebaseerd.

## Overwegingen bij het maken van aangepaste functies {#considerations}

Om van de douanefuncties in de regelredacteur een lijst te maken, kunt u hen in om het even welke volgende formaten verklaren:

* **Functie-instructie met of zonder jsdoc-opmerkingen**

U kunt een aangepaste functie maken met of zonder jsdoc-opmerkingen.

```javascript
    function functionName(parameters) 
        {
            // code to be executed
        }
```

* **Pijlfunctie met verplichte jsdoc-opmerking**

Enkele voorbeelden om pijlfuncties te maken zijn:

```javascript
    /**
    * test function
    * @name testFunction test function
    * @param {string} a some parameter description
    * @param {string} b another parameter description
    * @return {string}
    */
    testFunction = (a, b) => {
    return a + b;
    };
```

<!-- 
    * @param {string=} b another parameter description
      /** */
    testFunction1=(a) => (return a)
    /** */
    testFunction2 = a => a + 100;-->

* **Functie-expressie met verplichte jsdoc-commentaar**

Maak aangepaste functies in de volgende indelingen om deze weer te geven in de regeleditor van een adaptief formulier. Bijvoorbeeld:

```javascript
    /**
    * test function
    * @name testFunction test function
    * @param {string} input1 parameter description
    * @param {string} input2 another parameter description
    * @return {string}
    */
    testFunction = function(input1,input2)
        {
            // code to be executed
        }
```

<!--
* @param {string=} input2 another parameter description
The functions that are not supported in the custom function list are:
* Generator functions
* Async/Await functions 
* Method definitions
* Class methods
* Default parameters
* Rest parameters -->

>[!NOTE]
>
> U kunt de `error.log` in het geval van fouten zoals aangepaste functies, worden deze niet weergegeven in de regeleditor.

<!--The `error.log` file also displays the methods and parameters that are not supported for custom functions. -->


## Een aangepaste functie maken {#create-custom-function}

Creeer een cliëntbibliotheek om douanefuncties in de regelredacteur te roepen. Zie voor meer informatie [Client-Side bibliotheken gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html#developing).

Stappen voor het maken van aangepaste functies zijn:
1. [Een clientbibliotheek maken](#create-client-library)
1. [Clientbibliotheek toevoegen in een adaptief formulier](#use-custom-function)

### Een clientbibliotheek maken {#create-client-library}

U kunt aangepaste functies toevoegen door een clientbibliotheek toe te voegen. Voer de volgende stappen uit om een clientbibliotheek te maken:

1. [Clone your AEM Forms as a Cloud Service Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git).
1. Een map maken onder de `[AEM Forms as a Cloud Service repository folder]/apps/` map. Maak bijvoorbeeld een map met de naam `experience-league`
1. Navigeren naar `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/` en een `ClientLibraryFolder` als `es6clientlibs`.
1. Een eigenschap toevoegen `categories`met tekenreekstype als waarde `es6customfunctions` aan de `es6clientlibs` map.

   >[!NOTE]
   >
   >`es6customfunctions`is een voorbeeldcategorie. U kunt elke naam voor de categorie kiezen.

1. Een map maken met de naam `js`.
1. Ga naar de `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/es6clientlibs/js` map.
1. Voeg bijvoorbeeld een JavaScript-bestand toe. `function.js`. Het bestand bevat de code voor een aangepaste functie.

   >[!NOTE]
   >
   >* Als het JavaScript-bestand met code voor aangepaste functies een fout bevat, worden de aangepaste functies niet vermeld in de regeleditor van een adaptief formulier. U kunt ook de `error.log` bestand voor de fout.

   <!-- 
    >* AEM Adaptive Form supports the caching of custom functions. If the JavaScript is modified, the caching becomes invalidated, and it is parsed. You can see a message as `Fetched following custom functions list from cache` in the `error.log` file.  -->

1. Sla de `function.js` bestand.
1. Ga naar de `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/es6clientlibs/js` map.
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

1. [Voer de pijplijn uit.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline)

Zodra de pijpleiding met succes wordt uitgevoerd, wordt de douanefunctie die in cliëntbibliotheek wordt toegevoegd beschikbaar in uw [Editor voor adaptieve formulierregels](/help/forms/rule-editor.md).

### Clientbibliotheek toevoegen in een adaptief formulier{#use-custom-function}

Nadat u de clientbibliotheek hebt toegevoegd, gebruikt u deze in het adaptieve formulier. Hiermee kunt u uw [aangepaste functie als regel in uw formulier](/help/forms/rule-editor.md#custom-functions). Voer de volgende stappen uit om de clientbibliotheek toe te voegen aan uw adaptieve formulier:

1. Open het formulier in de bewerkingsmodus.
Als u een formulier wilt openen in de bewerkingsmodus, selecteert u een formulier en selecteert u **[!UICONTROL Open]**.
1. Selecteer in de bewerkingsmodus een component en selecteer vervolgens ![op veldniveau](assets/select_parent_icon.svg) > **[!UICONTROL Adaptive Form Container]** en selecteer vervolgens ![cmppr](assets/configure-icon.svg).
1. Voeg in het zijpaneel, onder Naam van clientbibliotheek, uw clientbibliotheek toe. ( `es6customfunctions` in het voorbeeld.)

   ![De aangepaste clientbibliotheek van de functie toevoegen](/help/forms/assets/clientlib-custom-function.png)

Creeer een regel om douanefunctie in de regelredacteur te gebruiken.

<!--

### Support for the optional parameters in custom functions{#support-for-optional-parameter}

AEM supports including optional parameters in JSDocs. These parameters are displayed as optional in the rule editor. There are two ways to add optional parameters in JSDocs:
*  `@param {string=abc} b -- some description for b which is optional`

    In the above line of code, `b` is an optional parameter with the default value set to `abc`. 
    Alternatively, you can define `b` as an optional parameter without assigning any default value as `@param {string=} b -- some description for b which is optional`

* `@param {array} [z=[def,xyz]] - - some description for z which is optional`

    In the above line of code, `z` is an optional parameter of array type with the default value set to `[def , xyz]`. 
    Alternatively, you can define `z` as an optional parameter without assigning any default value as `@param {array} [z=] - - some description for z which is optional`

>[!NOTE]
>
> Ensure that the parameter name is enclosed in square brackets [] and the parameter type is enclosed in curly brackets {}. 

To learn more about how to define optional parameters in JSDocs, [click here](https://jsdoc.app/tags-param).

In the rule editor of an Adaptive Form, the parameters are displayed as `required`. By default the parameters are `required`, if not defined as optional in JSDocs.

  ![Optional or required parameters](/help/forms/assets/optional-default-params.png) 

  You can save the rule without specifying a value for required parameters, but the rule is not executed and displays a warning message as:

  ![incomplete rule warning message](/help/forms/assets/incomplete-rule.png) 
  
  The rule is executed even if you do not specify a value for optional parameters. Undefined values are passed for optional parameters on executing the rule.

  ### Support for field and globals objects in custom functions {#support-field-and-global-objects}

  needs to be discussed

  -->

## Zie ook {#see-also}

{{see-also}}





