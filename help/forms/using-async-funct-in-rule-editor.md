---
title: Hoe te om asynchrone functievraag in de Visuele Redacteur van de Regel te gebruiken?
description: Asynchrone functievraag in Visuele regeleditor
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: a240ba26-a6d8-4643-8acb-1d8812dac61f
source-git-commit: 2cae8bb1050bc4538f4645d9f064b227fb947d75
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 0%

---

# Asynchrone functies gebruiken in een adaptief formulier op basis van kerncomponenten

De [&#x200B; regelredacteur in Adaptieve Forms &#x200B;](/help/forms/rule-editor-core-components.md) steunt asynchrone functies, die u toestaan om verrichtingen te integreren en te beheren die wachten op externe processen of gegevensherwinning vereisen zonder de interactie van de gebruiker met de vorm te onderbreken.

## Welke factoren bepalen het gebruik van asynchrone of synchrone functies?

Het effectief beheren van gebruikersinteractie is van cruciaal belang voor het creëren van een vloeiende ervaring. Twee veelvoorkomende benaderingen voor de afhandeling van bewerkingen zijn synchrone en asynchrone functies.

**Synchrone functies** voeren taken één na een andere uit, veroorzakend de toepassing op elke verrichting te wachten alvorens te werk te gaan. Dit kan tot vertragingen en een minder boeiende gebruikerservaring leiden, vooral wanneer de taken het wachten op externe middelen, zoals het uploaden van dossiers of het halen van gegevens impliceren.

Neem bijvoorbeeld een scenario waarin een gebruiker een afbeelding uploadt, het volledige formulier stopt, in afwachting van het uploaden. Deze pauze zorgt ervoor dat de gebruiker niet kan communiceren met andere velden, wat frustratie en vertragingen veroorzaakt. Tijdens het verwerken van de afbeelding kunnen ingevoerde gegevens verloren gaan wanneer ze weggaan of geduld verliezen, waardoor de ervaring omslachtig en inefficiënt wordt.

**Asynchrone functies**, anderzijds, staan taken toe om gelijktijdig te lopen. Dit betekent dat gebruikers kunnen blijven communiceren met de toepassing terwijl achtergrondprocessen worden uitgevoerd. Asynchrone bewerkingen verbeteren de reactiesnelheid, waardoor gebruikers direct feedback kunnen ontvangen en hun betrokkenheid zonder onderbrekingen kunnen behouden.

Met een asynchrone aanpak kunnen gebruikers daarentegen afbeeldingen uploaden op de achtergrond en tegelijkertijd de rest van het formulier naadloos invullen. De interface blijft reageren, zodat updates in real time mogelijk zijn en direct feedback wanneer het uploaden vordert. Het verbetert de betrokkenheid van gebruikers en zorgt voor een vloeiende ervaring zonder onderbrekingen.

![&#x200B; Asynchrone en synchrone functies &#x200B;](/help/forms/assets/sync-async.png){align=center}

## Asynchrone functies implementeren voor Adaptive Forms

U kunt de asynchrone functies voor Aangepast Forms uitvoeren gebruikend de volgende regeltypes in de regelredacteur:

* [Async Function-aanroep](#using-asynchronous-function-calls-in-the-visual-rule-editor)
* [Functie-uitvoer](#how-to-use-function-output-rule-type)

## Hoe te om het de regeltype van de Vraag van de Functie te gebruiken Async?

U kunt de [&#x200B; douanefuncties &#x200B;](/help/forms/custom-function-core-component-create-function.md) voor asynchrone verrichtingen schrijven en de asynchrone functies vormen gebruikend het **[!UICONTROL Async Function Call]** regeltype in de regelredacteur.

### Het onderzoeken van het de regeltype van de Vraag van de Functie Async door een gebruiksgeval

Neem bijvoorbeeld een registratieformulier op een website waar gebruikers een eenmalig wachtwoord (OTP) invoeren. Het deelvenster voor het toevoegen van gebruikersdetails wordt alleen weergegeven nadat u de juiste OTP hebt ingevoerd. Als de OTP onjuist is, blijft het paneel verborgen en verschijnt een foutbericht op het scherm.

![&#x200B; Login-vorm &#x200B;](/help/forms/assets/rule-editor-login-form.png) {breedte-50%}

In een registratieformulier, wanneer de gebruiker **klikt bevestigt** knoop, wordt de `matchOTP()` functie geroepen asynchroon om ingegaan OTP te verifiëren. De `matchOTP()` functie wordt uitgevoerd als a [&#x200B; douanefunctie &#x200B;](/help/forms/custom-function-core-component-create-function.md). Met het **[!UICONTROL Async Function Call]** -regeltype in de regeleditor kunt u de functie `matchOTP()` configureren in de regeleditor van een adaptief formulier. U kunt de succes en mislukkingscallbacks in de regelredacteur ook uitvoeren.

In de volgende afbeelding ziet u hoe u het regeltype **[!UICONTROL Async Function Call]** gebruikt om asynchrone functies voor Adaptive Forms aan te roepen:

![&#x200B; Werkschema om asynchrone functies toe te voegen &#x200B;](/help/forms/assets/workflow-to-add-async-func.png){width=50%, align=center}

### 1. Schrijf een aangepaste functie voor de asynchrone bewerking in het JS-bestand

>[!NOTE]
>
> * De regelredacteur van een vorm toont slechts functies met een terugkeertype van `Promise` wanneer u het **Async 2&rbrace; regeltype van de Vraag van de Functie &lbrace;selecteert.**
> * Leren hoe te om een douanefunctie tot stand te brengen, verwijs naar het artikel genoemd [&#x200B; creeer een Functie van de Douane voor een Aangepaste Vorm die op de Componenten van de Kern &#x200B;](/help/forms/custom-function-core-component-create-function.md) wordt gebaseerd.

De functie `matchOTP()` wordt geïmplementeerd als een aangepaste functie. De onderstaande code wordt toegevoegd aan het JS-bestand van de aangepaste functie:

```JavaScript
/**
 * generates the otp for success use case
 * @param {string} otp
 * @return {PROMISE}
 */
function matchOTP(otp) {
     return new Promise((resolve, reject) => {
        // Perform some asynchronous operation here
         asyncOperationForOTPMatch(otp, (error, result) => {
            if (error) {
                // On failure, call reject(error)
                reject(error);
            } else {
                // On success, call resolve(result)
                resolve(result);
            }
        });
    });
}

/**
 * generates the otp
 */
function asyncOperationForOTPMatch(otp, callback) {
    setTimeout(() => {
        if(otp === '111') {
            callback( null, {'valid':'true'});    
        } else {
            callback( {'valid':'false'}, null);
        }
    }, 1000);
}
```

De code definieert een functie `matchOTP()` die een belofte genereert om een eenmalig wachtwoord (OTP) asynchroon te valideren. Er wordt een functie `asyncOperationForOTPMatch()` gebruikt om het overeenkomende OTP-proces te simuleren. De functie controleert of de opgegeven OTP gelijk is aan `111` . Als ingegaan OTP correct is, roept het callback met ongeldig voor de fout en een voorwerp die op OTP wijzen geldig `({'valid':'true'})` is. Als OTP ongeldig is, roept het callback met een foutenvoorwerp `({'valid':'false'})` en ongeldig voor het resultaat.

### 2. Vorm de asynchrone functie in de regeleditor

Voer de volgende stappen uit om asynchrone functie in regelredacteur te vormen:

1. [Creeer een regel om asynchrone functie te gebruiken gebruikend het type van de vraagregel van de Functie Async](#21-create-a-rule-to-use-asynchronous-function-using-the-async-function-call-rule-type)
1. [Voer callbacks voor de asynchrone functie uit](#22-implement-the-callbacks-for-asynchronous-function)

#### 2.1 creeer een regel om asynchrone functie te gebruiken gebruikend het type van de de vraagregel van de Functie Async

Voer de volgende stappen uit om een regel te maken voor het gebruik van asynchrone bewerkingen met behulp van het **[!UICONTROL Async Function Call]** -regeltype:

1. Open een adaptief formulier in de ontwerpmodus, selecteer een formuliercomponent en selecteer **[!UICONTROL Rule Editor]** om de regeleditor te openen.
1. Selecteer **[!UICONTROL Create]** .
1. Creeer een voorwaarde in **wanneer** sectie van de regel voor een klik van knoop. Bijvoorbeeld, **wanneer [ bevestigt]** wordt geklikt.
1. In **toen** sectie, selecteer **[!UICONTROL Async Function call]** van **Uitgezochte de drop-down lijst van de Actie**.
Wanneer u **[!UICONTROL Async Function call]** selecteert en de functies met het retourneringstype `Promise` worden weergegeven.
1. Selecteer de asynchrone functie in de lijst. Selecteer bijvoorbeeld de functie `matchOTP()` en de callbacks ervan zoals `Add success callback` en `add failure callback` worden weergegeven.
1. Selecteer nu de bindingen van **[!UICONTROL Input]** . Selecteer bijvoorbeeld **[!UICONTROL Input]** as `Form Object` en vergelijk dit met het veld `OTP` .

In de onderstaande schermafbeelding wordt de regel weergegeven:

![&#x200B; regeltype &#x200B;](/help/forms/assets/asyn-function-rule-type.png)

Nu kunt u doorgaan met de implementatie van de callbacks: `Success` en `Failure` for the `matchOTP` functie.

#### 2.2 Voer callbacks voor de asynchrone functie uit

Voer de succes en mislukkingscallback methodes voor de asynchrone functie uit gebruikend de visuele regelredacteur.

**creeer een regel voor `Add Success callback` methode**

Laten we een regel maken om het deelvenster `userdetails` weer te geven als de OTP overeenkomt met de waarde `111` .

1. Klik op **[!UICONTROL Add success callback]**.
1. Klik op **[!UICONTROL Add Statement]** om de regel te maken.
1. Creeer een voorwaarde in **wanneer** sectie van de regel.
1. Selecteer **[!UICONTROL Function Output]** > **[!UICONTROL Get Event Payload]** .

   >[!NOTE]
   >
   > De functie **[!UICONTROL Get Event Payload]** haalt gegevens op die zijn gekoppeld aan een specifieke gebeurtenis om gebruikersinteracties dynamisch te beheren.

1. Selecteer zijn overeenkomstige banden van de **sectie van de Input**. Selecteer bijvoorbeeld **[!UICONTROL String]** en voer `valid` in. Vergelijk de ingevoerde tekenreeks met `true` .
1. In **toen** sectie, selecteer **[!UICONTROL Show]** van **Uitgezochte de drop-down lijst van de Actie**. Geef bijvoorbeeld het deelvenster `userdetails` weer.
1. Klik op **[!UICONTROL Add Statement]**.
1. Selecteer **[!UICONTROL Hide]** van de **Uitgezochte drop-down lijst van de Actie**. Verberg bijvoorbeeld het tekstvak `error message` .
1. Klik op **[!UICONTROL Done]**.

![&#x200B; vraag van het Succes &#x200B;](/help/forms/assets/rule-editor-success-callback.png){width=50%, height=50%}

Raadpleeg de onderstaande schermafbeelding, waarin de gebruiker de OTP invoert als `111` . Het deelvenster `User Details` verschijnt wanneer op de knop `Confirm` wordt geklikt.

![&#x200B; Succes &#x200B;](/help/forms/assets/success.gif)

**creeer een regel voor `Add Failure callback` methode**

Laten we een regel maken om een foutbericht weer te geven als de OTP niet overeenkomt met de waarde `111` .

1. Klik op **[!UICONTROL Add failure callback]**.

1. Klik op **[!UICONTROL Add Statement]** om de regel te maken.
1. Creeer een voorwaarde in **wanneer** sectie van de regel.
1. Selecteer **[!UICONTROL Function Output]** > **[!UICONTROL Get Event Payload]** .
1. Selecteer zijn overeenkomstige banden van de **sectie van de Input**. Selecteer bijvoorbeeld **[!UICONTROL String]** en voer `valid` in. Vergelijk de ingevoerde tekenreeks met `false` .
1. In **toen** sectie, selecteer **[!UICONTROL Show]** van **Uitgezochte de drop-down lijst van de Actie**. Geef bijvoorbeeld het tekstvak `error message` weer.
1. Klik op **[!UICONTROL Add Statement]**.
1. Selecteer **[!UICONTROL Hide]** van de **Uitgezochte drop-down lijst van de Actie**. Verberg bijvoorbeeld het deelvenster `userdetails` .
1. Klik op **[!UICONTROL Done]**.

![&#x200B; callback methode van de Mislukking &#x200B;](/help/forms/assets/rule-editor-failure-callback.png){width=50%, height=50%}

Raadpleeg de onderstaande schermafbeelding, waarin de gebruiker de OTP invoert als `123` . De foutmelding verschijnt wanneer op de knop `Confirm` wordt geklikt.

![&#x200B; Mislukking &#x200B;](/help/forms/assets/failure.gif)

In de onderstaande schermafbeelding wordt de volledige regel weergegeven voor het gebruik van **[!UICONTROL Async Function Call]** voor het implementeren van een asynchrone functie:

![&#x200B; Regel voor asynchrone functievraag &#x200B;](/help/forms/assets/rule-editor-async-callbacks.png)

U kunt de callbacks ook bewerken door op **[!UICONTROL Edit success callback]** en **[!UICONTROL Edit failure callback]** te klikken.

## Hoe te om het regeltype van de Output van de Functie te gebruiken?

U kunt de asynchrone functies ook indirect aanroepen met behulp van de synchrone functies. De synchrone functies worden uitgevoerd met het **[!UICONTROL Function Output]** regeltype in de regeleditor van een adaptief formulier.

Bekijk de onderstaande code om te zien hoe u asynchrone functies kunt aanroepen met behulp van het **[!UICONTROL Function Output]** regeltype:

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

Om zijn het werken te zien, voegen een knoop toe en creëren een regel voor de knoop die de asynchrone functie na een knoop klikt.

![&#x200B; creërend regel voor async functie &#x200B;](/help/forms/assets/rule-for-async-funct.png){width=50%}

Raadpleeg de schermafbeelding van het consolevenster hieronder om aan te tonen dat wanneer de gebruiker op de knop `Fetch` klikt, de aangepaste functie `callAsyncFunction` wordt aangeroepen, die op zijn beurt een asynchrone functie `asyncFunction` aanroept. Inspecteer het consolevenster om de reactie op de knoop te bekijken klik:

![&#x200B; venster van de Console &#x200B;](/help/forms/assets/async-custom-funct-console.png)

## Zie ook

{{see-also-rule-editor}}
