---
title: Wat zijn adaptieve formulierexpressies?
description: Met Adaptieve Forms-expressies kunt u automatische validatie, berekening en de zichtbaarheid van een sectie in- of uitschakelen.
feature: Adaptive Forms, Foundation Components
role: User
hide: true
hidefromtoc: true
exl-id: e5b77cc1-5fb1-4f73-afe6-64f1c407e42b
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '2682'
ht-degree: 0%

---

# Adaptieve formulierexpressies {#adaptive-form-expressions}

Adaptief Forms biedt geoptimaliseerde en vereenvoudigde ervaring voor het invullen van formulieren voor eindgebruikers met dynamische scriptmogelijkheden. Hiermee kunt u expressies schrijven om verschillende gedragingen toe te voegen, zoals velden en deelvensters voor dynamisch tonen/verbergen. Ook kunt u berekende velden toevoegen, velden alleen-lezen maken, validatielogica toevoegen en nog veel meer. Het dynamische gedrag is gebaseerd op de gebruikersinvoer of voorgevulde gegevens.

JavaScript™ is de expressietaal van Adaptive Forms. Alle expressies zijn geldige JavaScript™-expressies en gebruiken API&#39;s van het Adaptive Forms-scriptmodel. Deze expressies retourneren waarden van bepaalde typen. Voor de volledige lijst van de Adaptieve klassen van Forms, de gebeurtenissen, de voorwerpen, en openbare APIs, zie [ JavaScript™ API van de Bibliotheek voor Aanpassings Forms ](https://helpx.adobe.com/experience-manager/6-5/forms/javascript-api/index.html).

## Aanbevolen werkwijzen voor het schrijven van expressies {#best-practices-for-writing-expressions}

* Wanneer u expressies schrijft, kunt u de naam van een veld of deelvenster gebruiken om velden en deelvensters te openen. Gebruik de eigenschap value om toegang te krijgen tot de waarde van een veld. Bijvoorbeeld: `field1.value`
* Gebruik unieke namen voor velden en deelvensters in het formulier. Hiermee voorkomt u mogelijke conflicten met veldnamen die tijdens het schrijven van expressies worden gebruikt.
* Gebruik tijdens het schrijven van expressies met meerdere regels een puntkomma om een instructie te beëindigen.

## Aanbevolen werkwijzen voor expressies waarbij het deelvenster wordt herhaald {#best-practices-for-expressions-involving-repeating-panel}

Herhalende deelvensters zijn instanties van een deelvenster die dynamisch worden toegevoegd of verwijderd met behulp van API voor scripts of vooraf ingevulde gegevens. <!--  For detailed information about using repeating panel, see [creating forms with repeatable sections](creating-forms-repeatable-sections.md). -->

* Als u een herhalend deelvenster wilt maken, opent u in het dialoogvenster van het deelvenster de instellingen en stelt u de waarde van het maximale telveld in op meer dan 1.
* De minimale telwaarde van de herhalingsinstellingen van het deelvenster kan een of meer zijn, maar mag niet meer zijn dan de maximale telwaarde.
* Wanneer een expressie verwijst naar een veld van een herhalend deelvenster, worden de veldnamen in de expressie omgezet naar het dichtstbijzijnde herhalende element.
* Adaptief Forms biedt een aantal speciale functies om de berekening voor herhaalbare deelvensters, zoals som, telling, min, max, filter en nog veel meer, te vereenvoudigen. Voor de volledige lijst van functies, zie [ JavaScript™ API van de Bibliotheek verwijzing voor Adaptieve Forms ](https://helpx.adobe.com/aem-forms/6/javascript-api/af.html)
* API&#39;s voor het manipuleren van instanties van herhalende deelvensters zijn:

   * Een deelvensterinstantie toevoegen: `panel1.instanceManager.addInstance()`
   * Een herhalingsindex van een deelvenster ophalen: `panel1.instanceIndex`
   * De instanceManager van een deelvenster ophalen: `_panel1 or panel1.instanceManager`
   * Een instantie van een deelvenster verwijderen: `_panel1.removeInstance(panel1.instanceIndex)`

## Expressietypen {#expression-types}

In Adaptief Forms kunt u expressies schrijven om gedrag toe te voegen, zoals velden en deelvensters voor dynamisch tonen/verbergen. U kunt ook expressies schrijven om berekende velden toe te voegen, velden alleen-lezen te maken, validatielogica toe te voegen en nog veel meer. Adaptive Forms biedt ondersteuning voor de volgende expressies:

* **[de uitdrukkingen van de Toegang](#access-expression-enablement-expression)**: om een gebied toe te laten/onbruikbaar te maken.
* **[berekent uitdrukkingen](#calculate-expression)**: aan auto-compute waarde van een gebied.
* **[klik uitdrukking](#click-expression)**: om acties op klikgebeurtenis van een knoop te behandelen.
* **[Manuscript van de Initialisatie ](#initialization-script):** voer een actie op initialisering van een gebied uit.
* **[uitdrukking van Opties](#options-expression)**: een drop-down lijst dynamisch vullen.
* **[Summiere uitdrukking](#summary)**: om de titel van een accordeon dynamisch gegevens te verwerken.
* **[bevestigt uitdrukkingen](#validate-expression)**: om een gebied te bevestigen.
* **[de Waarde verbindt Manuscript ](#value-commit-script):** om de componenten van een vorm te veranderen nadat de waarde van een gebied wordt veranderd.
* **[de uitdrukking van het Zichtbaarheid](#visibility-expression)**: om zicht van een gebied en een paneel te controleren.
* **[de voltooiingsuitdrukking van de Stap](#step-completion-expression)**: om een gebruiker te verhinderen naar volgende stap van een tovenaar te gaan.

### Access Expression (Enablement Expression) {#access-expression-enablement-expression}

U kunt de toegangsuitdrukking gebruiken om een gebied toe te laten of onbruikbaar te maken. Als de expressie de waarde van een veld gebruikt, wordt de expressie opnieuw geactiveerd wanneer de waarde van het veld verandert.

**is op** van toepassing: gebieden

**Type van Terugkeer**: De uitdrukking keert een waarde Van Boole terug, die of het gebied wordt toegelaten of onbruikbaar gemaakt. **waar** vertegenwoordigt dat het gebied wordt toegelaten en **vals** vertegenwoordigt het gebied wordt onbruikbaar gemaakt.

**Voorbeeld**: Om een gebied slechts toe te laten wanneer de waarde van **field1** aan **X** wordt geplaatst, is de toegangsuitdrukking: `field1.value == "X"`

### Expressie berekenen {#calculate-expression}

De expressie calculate wordt gebruikt om de waarde van een veld automatisch te berekenen met behulp van een expressie. In dergelijke expressies wordt doorgaans de eigenschap value van een ander veld gebruikt. Bijvoorbeeld `field2.value + field3.value` . Wanneer de waarde van `field2` of `field3` verandert, wordt de uitdrukking opnieuw teweeggebracht en de waarde wordt opnieuw berekend.

**is op** van toepassing: gebieden

**Type van Terugkeer**: De uitdrukking keert een waarde terug die met het gebied compatibel is waar het uitdrukkingsresultaat (bijvoorbeeld, decimaal) wordt getoond.

**Voorbeeld**: De berekeningsuitdrukking om som twee gebieden in **field1** te tonen is:
`field2.value + field3.value`

### Klikken op uitdrukking {#click-expression}

De klikuitdrukking behandelt de acties die op de klikgebeurtenis van een knoop worden uitgevoerd. GuideBridge beschikt over API&#39;s die verschillende functies kunnen uitvoeren, zoals verzenden, valideren die samen met de klikexpressie worden gebruikt. Voor volledige lijst van APIs, zie [ GuideBridge APIs ](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.html).

**is op** van toepassing: De gebieden van de knoop

**Type van Terugkeer**: De klikuitdrukking keert geen waarde terug. Als een expressie een waarde retourneert, wordt de waarde genegeerd.

**Voorbeeld**: Om een tekstvakje **textbox1** op de klikactie van een knoop met waarde **AEM Forms** te bevolken, is de klikuitdrukking van de knoop `textbox1.value="AEM Forms"`

### Initialisatiescript {#initialization-script}

Het initialisatiescript wordt geactiveerd wanneer een Adaptief formulier wordt geïnitialiseerd. Afhankelijk van scenario&#39;s, gedraagt het initialisatiescript zich op de volgende manier:

* Wanneer een adaptief formulier wordt gegenereerd zonder dat er een gegevensprefulling is, wordt het initialisatiescript uitgevoerd nadat het formulier is geïnitialiseerd.
* Wanneer een adaptief formulier wordt weergegeven met een gegevensvoorvoegsel, wordt het script uitgevoerd nadat de voorvulbewerking is voltooid.
* Wanneer de validatie van een adaptief formulier aan de serverzijde wordt geactiveerd, wordt het initialisatiescript uitgevoerd.

**is op van toepassing:** gebieden en paneel

**Type van Terugkeer:** de het manuscriptuitdrukking van de Initialisatie keert geen waarde terug. Als een expressie een waarde retourneert, wordt de waarde genegeerd.

**Voorbeeld:** In een gegevens pre-vult scenario, om gebieden met standaardwaarde `'Adaptive Forms'` te bevolken wanneer hun waarde als ongeldig wordt bewaard, is de uitdrukking van het initialisatiescript:
`if(this.value==null) this.value='Adaptive Forms';`

### Opties voor expressie {#options-expression}

De optiesuitdrukking wordt gebruikt om opties van een drop-down lijstgebied dynamisch te vullen.

**is op** van toepassing: drop-down lijstgebieden

**Type van Terugkeer**: De optiesuitdrukking keert een serie van koordwaarden terug. Elke waarde kan een eenvoudig koord, zoals **Male** zijn, of in een key=value paarformaat, zoals **1=Male**

**Voorbeeld**: Om waarde van een gebied te bevolken, die op de waarde van een ander gebied wordt gebaseerd, verstrek een eenvoudige optiesuitdrukking. Bijvoorbeeld, om een gebied te bevolken, **Aantal Kinderen**, dat op de **Samengestelde Status** wordt gebaseerd die op een ander gebied wordt uitgedrukt, is de uitdrukking:

**`marital_status.value == "married" ? ["1=One", "2=two"] : ["0=Zero"]`.**

Wanneer de waarde van **marital_status** gebiedsveranderingen, de uitdrukking wordt opnieuw teweeggebracht. U kunt de drop-down lijst van de dienst van REST ook bevolken. <!-- For detailed information, see [Dynamically populating dropdowns](dynamically-populate-dropdowns.md). -->

### Samenvattingsexpressie {#summary}

Met de expressie Samenvatting wordt de titel van een onderliggend deelvenster van een accordeonlay-outdeelvenster dynamisch berekend. U kunt de expressie Samenvatting opgeven in een regel, die een formulierveld of een aangepaste logica gebruikt om de titel te evalueren. De expressie wordt uitgevoerd wanneer het formulier wordt geïnitialiseerd. Als u een formulier vooraf invult, wordt de expressie uitgevoerd nadat de gegevens zijn voorgevuld of wanneer de waarde van afhankelijke velden die in de expressie worden gebruikt, verandert.

De expressie Samenvatting wordt doorgaans gebruikt voor het herhalen van onderliggende items van een accordeonlay-outdeelvenster, zodat elk onderliggend deelvenster een betekenisvolle titel krijgt.

**is op van toepassing:** Panelen die directe kinderen van een paneel zijn de waarvan lay-out als Accordeon wordt gevormd.

**Type van Terugkeer:** de uitdrukking keert een Koord terug dat de titel van de accordeon wordt.

**Voorbeeld:** &quot;Rekeningnummer: &quot; + textbox1.value

### Expressie valideren {#validate-expression}

De expressie validate wordt gebruikt om de velden te valideren met de opgegeven expressie. Dergelijke expressies gebruiken doorgaans reguliere expressies samen met de veldwaarde om een veld te valideren. De expressie wordt opnieuw geactiveerd en de validatiestatus van het veld wordt opnieuw berekend bij elke wijziging in de waarde van een veld.

**is op** van toepassing: gebieden

**Type van Terugkeer**: De uitdrukking keert een waarde Van Boole terug, die de bevestigingsstatus van het gebied vertegenwoordigt. De waarde **vals** vertegenwoordigt dat het gebied ongeldig is en **waar** vertegenwoordigt dat het gebied geldig is.
**Voorbeeld**: Voor een gebied dat postcode van UK vertegenwoordigt, is de bevestigingsuitdrukking:

(**this.value** &amp;&amp; `this.value.match(/^(GIR 0AA|[A-Z]{1,2}\d[A-Z0-9]? ?[0-9][A-Z]{2}\s*)$/i) == null) ? false : true`

In het bovenstaande voorbeeld, als de niet-lege waarde niet het patroon aanpast, keert de uitdrukking **vals** terug om erop te wijzen dat het gebied niet geldig is.

>[!NOTE]
>
>Als u een validatie-expressie schrijft voor een niet-verplicht of verplicht veld, wordt de expressie geëvalueerd, ongeacht de zichtbaarheidsstatus van het veld. Als u de validatie voor de verborgen velden wilt stoppen, stelt u de eigenschap validationsDisabled in het script Initialization of Value Commit in op true. Bijvoorbeeld: `this.validationsDisabled=true`

### Waarde script vastleggen {#value-commit-script}

Het script voor vastleggen van waarde wordt geactiveerd wanneer:

* Een gebruiker wijzigt de waarde van een veld in de gebruikersinterface.
* De waarde van een veld verandert via de programmacode als gevolg van een wijziging in een ander veld.

**is op van toepassing:** gebieden

**Type van Terugkeer:** de waarde begaat manuscriptuitdrukking geen waarde terugkeert. Als een expressie een waarde retourneert, wordt de waarde genegeerd.

**Voorbeeld:** om het geval van alfabeten ingegaan op het gebied in hoofdletters om te zetten bij begaat, begaat de waarde uitdrukking:
`this.value=this.value.toUpperCase()`

>[!NOTE]
>
>U kunt de uitvoering van het Script van het Vastleggen van de Waarde onbruikbaar maken wanneer de waarde van een gebied programmatically wordt veranderd. Om dit te doen, ga naar https://&#39; [ server ]:[ haven ]&#39;/system/console/configMgr en verander **Aangepaste Versie van Forms voor Verenigbaarheid** aan **AEM Forms 6.1**. Vervolgens wordt het script voor vastleggen van waarde alleen uitgevoerd wanneer de gebruiker de waarde van het veld wijzigt in de gebruikersinterface.

### Zichtbaarheidsexpressie {#visibility-expression}

De uitdrukking van de Zichtbaarheid wordt gebruikt om de zichtbaarheid van gebied/paneel te controleren. De zichtbaarheidsexpressie gebruikt doorgaans de eigenschap value van een veld en wordt opnieuw geactiveerd wanneer die waarde verandert.

**is op** van toepassing: gebieden en paneel

**Type van Terugkeer**: De uitdrukking keert een waarde Van Boole terug, die het gebied/paneel vertegenwoordigt is zichtbaar of niet. **vals** vertegenwoordigt dat het gebied of het paneel niet zichtbaar en waar vertegenwoordigt dat het gebied of het paneel zichtbaar is.

**Voorbeeld**: Voor een paneel dat zichtbaar wordt slechts als de waarde van **field1** aan **Mannelijke** wordt geplaatst, is de zichtbaarheidsuitdrukking: `field1.value == "Male"`

### Uitdrukking voor stapvoltooiing {#step-completion-expression}

De expressie voor het voltooien van de stap wordt gebruikt om te voorkomen dat een gebruiker naar de volgende stap van een wizardlay-out gaat. Deze expressies worden gebruikt wanneer deelvensters een wizardlay-out hebben (een formulier dat uit meerdere stappen bestaat en één stap tegelijk weergeeft). De gebruiker kan alleen naar de volgende stap, het volgende deelvenster of de volgende subsectie gaan als alle vereiste waarden in de huidige sectie zijn ingevuld en geldig zijn.

**is op** van toepassing: Panelen met lay-out van punt dat aan tovenaar wordt geplaatst.

**Type van Terugkeer**: De uitdrukking keert een waarde Van Boole terug, die het huidige paneel vertegenwoordigt is geldig of niet. **Waar** vertegenwoordigt dat het huidige paneel geldig is en de gebruiker aan volgend paneel kan navigeren.

**Voorbeeld**: In een vorm die in diverse panelen wordt georganiseerd, alvorens aan het volgende paneel te navigeren wordt het huidige paneel bevestigd. In dergelijke gevallen worden de expressies voor stapvoltooiing gebruikt. Over het algemeen maken deze expressies gebruik van de GuideBridge-API voor validatie. Een voorbeeld van een expressie voor het voltooien van stappen is:
`window.guideBridge.validate([],this.panel.navigationContext.currentItem.somExpression)`

## Validaties in adaptieve vorm {#validations-in-adaptive-form}

Er zijn meerdere methoden om veldvalidatie toe te voegen aan een adaptief formulier. Als een bevestigingscontrole op een gebied wordt toegevoegd, **Waar** vertegenwoordigt dat de waarde ingegaan op het gebied geldig is. **Vals** vertegenwoordigt dat de waarde ongeldig is. Als u in- en uitgaat van een veld, wordt het foutbericht niet gegenereerd.

De methoden om validaties toe te voegen aan een veld zijn:

### Vereist {#required}

Om een component verplicht te maken, in **geeft** dialoog van de component uit, kunt u optie **Titel en Tekst > Vereist** selecteren. U kunt ook het juiste vereiste bericht toevoegen (optioneel).

### Validatiepatronen {#validation-patterns}

Er zijn meerdere validatiepatronen beschikbaar voor een veld. Om een validatiepatroon, in **te selecteren geef** dialoog van de component uit, bepaal de plaats van de **sectie van de Patronen** en selecteer **patronen**. U kunt uw eigen patroon van de douanebevestiging in de tekstvakje van het a **Patroon** tot stand brengen. De validatiestatus is teruggekeerd **Waar** slechts als het gevulde gegeven aan het bevestigingspatroon volgzaam is, anders **Vals** is teruggekeerd. <!-- To write your own custom validation pattern, see [Picture clause support for HTML5 forms](picture-clause-support.md). -->

### Validatie-expressies {#validation-expressions}

De validatie van een veld kan ook worden berekend met behulp van expressies in verschillende velden. Deze uitdrukkingen worden geschreven binnen **gebied van het Manuscript van de Bevestiging** van het **3} lusje van het Manuscript van** geeft **dialoog van de component uit.** De validatiestatus van een veld is afhankelijk van de waarde die de expressie retourneert. Voor informatie over hoe te om dergelijke uitdrukkingen te schrijven, zie [ Uitdrukking ](adaptive-form-expressions.md#p-validate-expression-p) bevestigen.

## Aanvullende informatie {#additional-information}

### Veldweergave-indeling gebruiken {#using-field-display-format}

U kunt de indeling weergeven gebruiken om de gegevens in verschillende indelingen weer te geven. U kunt bijvoorbeeld de weergave-indeling gebruiken om een telefoonnummer met afbreekstreepjes, ZIP-code of datumkiezer weer te geven. Deze vertoningspatronen kunnen van de **sectie van Patronen** van de Edit dialoog van een component worden geselecteerd. U kunt aangepaste weergavepatronen schrijven, vergelijkbaar met de hierboven vermelde validatiepatronen.

### GuideBridge - API&#39;s en gebeurtenissen {#guidebridge-apis-and-events}

GuideBridge is een verzameling API&#39;s die kunnen worden gebruikt voor interactie met Adaptive Forms in het geheugenmodel in een browser. Voor gedetailleerde inleiding aan Gids Bridge API, klassenmethodes, blootgestelde gebeurtenissen, zie [ JavaScript™ API van de Bibliotheek voor Aanpassings Forms ](https://helpx.adobe.com/aem-forms/6/javascript-api/).

>[!NOTE]
>
>Het wordt aanbevolen de gebeurtenislisteners GuideBridge niet te gebruiken in expressies.

#### Gebruik van GuideBridge in verschillende expressies {#guidebridge-usage-in-various-expressions}

* Als u formuliervelden opnieuw wilt instellen, kunt u de `guideBridge.reset()` API activeren op de klikexpressie van een knop. Er is ook een API voor verzenden die kan worden aangeroepen als een klikexpressie `guideBridge.submit()` .

* U kunt de API van `setFocus()` gebruiken om de focus in te stellen op verschillende velden of deelvensters (voor de vensterfocus wordt automatisch ingesteld op het eerste veld). `setFocus()` biedt een breed scala aan opties voor navigatie, zoals navigatie tussen deelvensters, Vorige/Volgende verplaatsing, focus instellen op een bepaald veld en nog veel meer. Als u bijvoorbeeld naar het volgende deelvenster wilt gaan, kunt u het volgende gebruiken: `guideBridge.setFocus(this.panel.somExpression, 'nextItem')` .

* Gebruik `guideBridge.validate(errorList, somExpression).` om een adaptief formulier of de specifieke deelvensters te valideren

#### GuideBridge gebruiken buiten expressies  {#using-guidebridge-outside-expressions-nbsp}

U kunt ook de GuideBridge-API&#39;s buiten de expressies gebruiken. U kunt bijvoorbeeld de GuideBridge-API gebruiken om communicatie in te stellen tussen de pagina HTML die als host fungeert voor het adaptieve formulier en het formuliermodel. Bovendien kunt u de waarde instellen die afkomstig is van het bovenliggende item van het Iframe-bestand dat het formulier host.

Als u GuideBridge API wilt gebruiken voor het bovenstaande voorbeeld, neemt u een instantie van GuideBridge op. Om de instantie te vangen, luister aan `bridgeInitializeStart` gebeurtenis van a `window` voorwerp:

```javascript
window.addEventListener("bridgeInitializeStart", function(evnt) {

     // get hold of the guideBridge object

     var gb = evnt.detail.guideBridge;

     //wait for the completion of AF

     gb.connect(function (){

        //this function is called after Adaptive Form is initialized

     })

})
```

>[!NOTE]
>
>In AEM is het een goede gewoonte om code te schrijven in een clientLib en deze op te nemen in uw pagina (header.jsp of footer.jsp van de pagina).

Als u GuideBridge wilt gebruiken nadat het formulier is geïnitialiseerd (de gebeurtenis `bridgeInitializeComplete` wordt verzonden), haalt u de GuideBridge-instantie op met `window.guideBridge` . U kunt de GuideBridge-initialisatiestatus controleren met de `guideBride.isConnected` API.

#### GuideBridge-gebeurtenissen {#guidebridge-events}

GuideBridge biedt ook bepaalde gebeurtenissen voor externe scripts op de hostpagina. Externe scripts kunnen naar deze gebeurtenissen luisteren en verschillende bewerkingen uitvoeren. Als de gebruikersnaam in een formulier bijvoorbeeld wordt gewijzigd, verandert ook de naam die in de koptekst van de pagina wordt weergegeven. Voor meer details over dergelijke gebeurtenissen, zie [ JavaScript™ API van de Bibliotheek voor Adaptieve Forms ](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.html).

Gebruik de volgende code om handlers te registreren:

```javascript
guideBridge.on("elementValueChanged", function (event, data)  {

      // execute some logic when value of a field is changed

});
```

### Aangepaste patronen maken voor een veld {#creating-custom-patterns-for-a-field}

Zoals hierboven is vermeld, kan de auteur met Adaptive Forms patronen voor validatie- of weergaveindelingen opgeven. U kunt niet alleen patronen uit de vakken gebruiken, maar ook herbruikbare aangepaste patronen definiëren voor een component Adaptief formulier. U kunt bijvoorbeeld een tekstveld of een numeriek veld definiëren. Als u deze patronen eenmaal hebt gedefinieerd, kunt u deze patronen in alle formulieren gebruiken voor het opgegeven type component. U kunt bijvoorbeeld een aangepast patroon maken voor een tekstveld en dit gebruiken in de tekstvelden in de Adaptief Forms. U kunt het aangepaste patroon selecteren door de patroonsectie te openen in het dialoogvenster Bewerken van een component. <!-- For details about Pattern definition or format, see [Picture clause support for HTML5 forms](picture-clause-support.md).-->

Voer de volgende stappen uit om een aangepast patroon te maken voor een specifiek veldtype en dit opnieuw te gebruiken voor andere velden van hetzelfde type:

1. Navigeer naar CRXDE Lite op de ontwerpinstantie.
1. Maak een map om uw aangepaste patronen te behouden. Creëer onder de map /apps een knooppunt van het type sling :folder. Maak bijvoorbeeld een knooppunt met de naam `customPatterns` . Onder dit knooppunt maakt u een ander knooppunt van het type `nt:unstructed` en geeft u het een naam `textboxpatterns` . Dit knooppunt bevat de verschillende aangepaste patronen die u wilt toevoegen.
1. Open het tabblad Eigenschappen van het gemaakte knooppunt. Open bijvoorbeeld het tabblad Eigenschappen van `textboxpatterns` . Voeg het `guideComponentType` bezit aan deze knoop toe en plaats zijn waarde aan *fd/af/components/formatter/guideTextBox*.

1. De waarde van deze eigenschap is afhankelijk van het veld waarvoor u de patronen wilt definiëren. Voor numeriek gebied, is de waarde van het `guideComponentType` bezit *fd/af/components/formatter/guideNumericBox*. De waarde voor het gebied Datepicker is *fd/af/components/formatter/guideDatepicker*.
&quot;
1. U kunt een aangepast patroon toevoegen door een eigenschap toe te wijzen aan het knooppunt `textboxpatterns` . Voeg een eigenschap met een naam toe (bijvoorbeeld `pattern1` ) en stel de waarde ervan in op het patroon dat u wilt toevoegen. Bijvoorbeeld, voeg een bezit `pattern1` met waarde Fax=text {99-999- 9999999} toe. Het patroon is beschikbaar voor alle tekstvakken die u in Adaptief Forms gebruikt.

   ![ Creërend douanepatronen voor gebieden in CrxDe ](assets/creating-custom-patterns.png)

   Aangepaste patronen maken
