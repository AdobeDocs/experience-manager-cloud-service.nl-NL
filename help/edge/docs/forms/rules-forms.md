---
title: Regels gebruiken om dynamisch gedrag aan een formulier toe te voegen
description: Edge Delivery Services for AEM Forms is gebouwd voor optimale prestaties, waardoor u de toekomst van gestroomlijnde gegevensverzameling en betrokkenheid van gebruikers kunt inzien. Gebruik regels om dynamisch gedrag aan uw formulieren toe te voegen.
feature: Edge Delivery Services
exl-id: 58042016-e655-446f-a2bf-83f1811525e3
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '2218'
ht-degree: 0%

---

# Regels gebruiken om dynamisch gedrag aan uw formulieren toe te voegen

Een van de krachtige functies van het maken van formulieren met behulp van een spreadsheet is de mogelijkheid om ingebouwde spreadsheetfuncties te gebruiken om regels te maken, zodat u formuliervelden voorwaardelijk kunt weergeven of verbergen, berekeningen kunt automatiseren op basis van gebruikersinvoer en een meer dynamische gebruikerservaring kunt creëren.

Dit artikel begeleidt u door hoe te om diverse Adaptieve eigenschappen van het Blok van de Vorm hoofdzakelijk [`Visible`](#visible-property), [`Visibility Expression`](#visible-expression-property) en [`Value Expression`](#value-expression-property) eigenschappen samen met [ spreadsheetfuncties ](#spreadsheet-functions-for-rules) te gebruiken om efficiënte regels voor uw vormen tot stand te brengen. We zullen ook enkele voorbeelden bekijken om te illustreren hoe deze regels in de praktijk kunnen worden toegepast.

## Werken met de constructies van een regel

Regels zijn als instructies die ons vertellen wat we in verschillende situaties moeten doen. Een regel heeft over het algemeen de volgende elementen:

- Voorwaarden : Deze bepalen onder welke omstandigheden de regel van toepassing is. Beschouw ze als een vraag die beantwoord moet worden (ja of nee).

- Handelingen: deze definiëren wat er gebeurt wanneer aan de voorwaarde wordt voldaan (true) of wanneer niet (false).


Als u bijvoorbeeld een e-mailvak wilt weergeven, selecteert u een selectievakje:

- Voorwaarde: &quot;Wilt u zich abonneren op Tijdschrift en Activiteiten?&quot; selectievakje is ingeschakeld. (Ja of nee?) Deze voorwaarde wordt ingesteld in de eigenschap `Visible` van het formulier.
- Actie (true): het e-mailvak wordt weergegeven. (Wat gebeurt er als dat het geval is). De `Visibility Expression` gebruikt de voorwaarde die voor de eigenschap `visible` is gedefinieerd om velden dynamisch weer te geven.
- Handeling (Onwaar): Het e-mailvak is verborgen. (Wat gebeurt er als dit niet het geval is). In `Visibility Expression` wordt de gedefinieerde voorwaarde voor `Value` gebruikt om velden dynamisch te verbergen.

Voor gedetailleerde geleidelijke instructies, zie [ tonen/verbergen e-mailgebied dat op een voorwaarde ](#example-1-conditional-email-field) wordt gebaseerd


## Inzicht krijgen in de eigenschappen Waarde, Zichtbaarheid, Weergave en Waardeuitdrukking

### Zichtbare eigenschap

Stel u een lichtschakelaar voor uw formulierveld in. De eigenschap `Visible` lijkt op die switch, die bepaalt of het veld in eerste instantie zichtbaar is op het formulier wanneer het wordt geladen.

- True (like the light switch is &quot;on&quot;): The field is displayed on the form.
- Onwaar (als de lichtschakelaar &quot;weg&quot;is): Het gebied is verborgen op de vorm.

U kunt de Formule SpreadSheet (met inbegrip van = markering) gebruiken om een formule te schrijven gebruikend spreadsheet-als logica om de zicht van het gebied te bepalen. U kunt de waarden van andere velden in het formulier in deze formule gebruiken. Als een gebruiker bijvoorbeeld Individueel selecteert in een registratietype veld, kunt u het e-mailveld verbergen met een formule die die waarde controleert.

### Zichtbare expressie-eigenschap (een veld tonen/verbergen)

Met de eigenschap `Visible Expression` kunt u de regel gebruiken die aan de eigenschap `Visible` is toegevoegd om te bepalen of het veld op basis van gebruikersinteracties moet worden weergegeven of verborgen.

Gebruik `=FORMULATEXT("Address of the corresponding Visible property)` om de formule die in de `Visible` -eigenschap wordt vermeld, als een tekenreeks toe te voegen aan het eigenschapveld `Visible Expression` . Dit is vereist om velden in een gepubliceerd formulier dynamisch weer te geven/te verbergen.

![ Forumaltext ](/help/edge/assets/aem-forms-formulatext.png)

### Waarde, eigenschap (de oorspronkelijke gegevens instellen)

Stel je een vooraf ingestelde waarde voor op een dimere schakelaar voor het licht van een kamer. De eigenschap `Value` is vergelijkbaar en bepaalt de aanvankelijke status van de gegevens die een gebruiker in het veld ziet.  Hiermee worden de huidige gegevens die in het formulierveld worden weergegeven, ingesteld of opgehaald.

Wanneer het formulier voor de eerste keer wordt geladen, bepaalt de eigenschap `Value` wat de gebruiker in het veld ziet voordat hij of zij wijzigingen aanbrengt. In tegenstelling tot de eigenschappen `Visible` en `Visible Expression` die de zichtbaarheid bepalen, heeft de eigenschap Waarde rechtstreeks invloed op de gegevens zelf. Gebruikers kunnen deze waarde wijzigen door opties te typen, te selecteren (vervolgkeuzemenu&#39;s) of door te communiceren met het veld.

U kunt de Formule van Excel (met inbegrip van = markering) gebruiken om een formule te schrijven gebruikend spreadsheet-als logica om de waarde te bepalen die op het gebied wordt getoond. U kunt de waarden van andere velden in het formulier in deze formule gebruiken. U kunt bijvoorbeeld automatisch een korting berekenen op basis van het orderbedrag dat u in een ander veld hebt ingevoerd.


### Eigenschap voor waardexpressie (waarden berekenen die in een veld moeten worden weergegeven)

Met deze eigenschap kunt u de waarde beheren die wordt weergegeven in een veld op basis van een formule, vergelijkbaar met de zichtbare expressie. Stel je een rekenmachine voor die in het veld is ingebouwd.

Gebruik `=FORMULATEXT("Address of the corresponding Value property)` om de formule die in de `Value` -eigenschap wordt vermeld, als een tekenreeks toe te voegen aan het eigenschapveld `Value Expression` . Dit is vereist om berekende waarden dynamisch te berekenen en weer te geven in een gepubliceerde vorm.

![ Forumaltext ](/help/edge/assets/aem-forms-formulatext-value.png)

Hier is een analogie om deze concepten te verharden:

- Zichtbaar: Stel je een vorm voor als een huis. De eigenschap &quot;Visible&quot; is vergelijkbaar met de lichtschakelaar voor elke kamer (veld). U bepaalt of de ruimte aanvankelijk verlicht (zichtbaar) of donker (verborgen) is wanneer iemand het huis binnenkomt (het formulier opent).
- Zichtbare uitdrukking: dit is als een lichtschakelaar van de bewegingssensor. De ruimte (veld) kan aanvankelijk donker (verborgen) zijn, maar een formule (bewegingssensor) kan deze inschakelen (het veld weergeven) als iemand langs loopt (de waarde in een ander veld wijzigt).
- Waarde: dit is als een vooraf ingestelde dimmer-schakelaar voor het licht (initiële gegevens in het veld). Gebruikers kunnen vervolgens de helderheid aanpassen (de waarde wijzigen).
- Waardeuitdrukking: dit is als een mooie rekenmachine die in de prijstag van een product in het huis (vorm) is ingebouwd. De prijstag (veld) toont de uiteindelijke prijs op basis van een formule (bijvoorbeeld door belasting toe te voegen aan de basisprijs) die andere informatie gebruikt, zoals de basisprijs (waarde van een ander veld).

Door deze eigenschappen met [ spreadsheetfuncties ](#spreadsheet-functions-for-rules) te combineren, kunt u een brede waaier van dynamisch gedrag binnen uw vormen bereiken.

## Werkbladfuncties voor regels

Adaptief Forms Block ondersteunt diverse spreadsheetfuncties die kunnen worden gebruikt om regels te maken. Hier zijn functies die beschikbaar zijn buiten de box (OOTB):

### Logische functies

- [ NIET () ](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#__RefHeading__1018452_715980110): Keert de logische staat (WAAR wordt VALS en vice versa) om.
- [ EN () ](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#AND): Keert WAAR terug slechts als alle gespecificeerde voorwaarden WAAR zijn.
- [ OF () ](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#OR): Keert WAAR terug als minstens één van de gespecificeerde voorwaarden WAAR is.

### Voorwaardelijke functies

- [ IF () ](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#__RefHeading__1018446_715980110): Evalueert een voorwaarde en keert een specifieke waarde als WAAR, en een andere waarde als VALS terug.

### Wiskundige functies

- [ SUM () ](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#SUM): Voegt waarden van een gespecificeerde waaier van cellen toe.
- [ ROND () ](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#ROUND): Rondt een aantal aan een gespecificeerd aantal decimalen.
- [ MIN () ](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#MIN): Keert de kleinste waarde van een gespecificeerde waaier van cellen terug.

## Een regel maken

Hier duiken enkele praktische voorbeelden op om te laten zien hoe regels kunnen worden gebruikt om uw formulieren te verbeteren:

## Voorbeeld 1: voorwaardelijk e-mailveld

In dit voorbeeld wordt getoond hoe het selectievakje als voorwaarde werkt. Wanneer deze is geselecteerd (voorwaarde is true), wordt het e-mailvak weergegeven (actie voor true). Als deze optie niet is geselecteerd (voorwaarde is false), blijft het e-mailvak verborgen (actie voor onwaar).

Maak een formulier met een selectievakje en een e-mailvak, zoals wordt weergegeven in de onderstaande afbeelding:

![ Voorwaardelijke E-mailVorm ](/help/edge/assets/aem-forms-conditional-email-form.png)


Hier is hoe te om een regel te gebruiken om het e-mailgebied op de selectie van checkbox te tonen:

1. Stel de eigenschap `Value` van het veld Selectievakje in op `TRUE` .
1. Stel de eigenschap `Checked` van het veld Selectievakje in op `FALSE` . Dit zorgt ervoor dat het selectievakje standaard niet is ingeschakeld.
1. Stel de eigenschap `Visible` van het e-mailveld in op `=[address of Checked property of the checkbox field] = true()` . Bijvoorbeeld `=Q11=TRUE()` . De formule evalueert, als checkbox of niet wordt geselecteerd. Als het selectievakje is ingeschakeld, levert de formule TRUE op. Als het selectievakje niet is ingeschakeld, levert de formule FALSE op.



   De functie `TRUE()` retourneert de logische waarde wanneer u deze instelt op punt naar de eigenschap `Checked` als de eigenschap `checked = false` false retourneert. Als `checked=true` , wordt `true` geretourneerd. Dit zorgt ervoor dat het e-mailveld standaard verborgen is.


1. Stel de eigenschap `Visible Expression` van het veld Selectievakje in op `=FORMULATEXT ((address of Visible property of the checkbox field))` . Bijvoorbeeld `=FORMULATEXT((G12))` . De functie FORMULATEXT() neemt een formule als input en retourneert de formule zelf als een tekstreeks. Het is handig de formule in het formulier te gebruiken.

   ![ Voorwaardelijk E-mailGebied ](/help/edge/assets/aem-forms-visible-expression-formula-text.png)

1. Geef een voorbeeld van het formulier weer en publiceer het. Als u nu het selectievakje inschakelt, wordt het e-mailveld weergegeven en wordt het veld verborgen, wat een dynamische gebruikerservaring oplevert.

   ![ Voorwaardelijke E-mail ](/help/edge/assets/aem-forms-coditional-email.gif)


## Voorbeeld 2: Automatische berekening

In dit voorbeeld wordt getoond hoe een formulier de geschatte kosten voor reiskosten automatisch berekent bij het selecteren van reisdatums in een formulier.

Maak een formulier met een datumveld, een budget voor de ruimte, de velden Geschatte reiskosten zoals hieronder weergegeven en een e-mailvak, zoals in de onderstaande afbeelding wordt weergegeven:

![ Voorwaardelijke E-mailVorm ](/help/edge/assets/aem-forms-automatic-calculations-form.png)

Hieronder wordt beschreven hoe u een automatische berekening kunt uitvoeren om de geschatte kosten van de reis weer te geven:

1. Stel de eigenschap `Value` van het `amount` veld in op `=F6*DAYS(F3,F2)` . Deze formule berekent het aantal dagen vanaf `Start Date` en `End Date` , vermenigvuldigt het aantal dagen met een budget voor ruimte en geeft het resultaat weer in het veld `Estimated Trip Cost` .

1. Stel de eigenschap `Value Expression` van het `Estimated Trip Cost` veld in op `=FORMULATEXT ((address of value property of the amount field))` . Bijvoorbeeld `=FORMULATEXT(F7)` . De functie FORMULATEXT() neemt een formule als input en retourneert de formule zelf als een tekstreeks. Het is handig de formule in het formulier te gebruiken.

1. Geef een voorbeeld van het formulier weer en publiceer het. Nu, bij het specificeren van een `Start Date`, `End Date`, en de Begroting van de Ruimte. De waarde `Estimated Trip Cost` wordt automatisch berekend.

## Voorbeelden van werkbladfuncties


Hier volgen enkele voorbeelden van de meestgebruikte spreadsheetfuncties:

**Logische functies:**

- **NIET ():** keert de logische staat (WAAR wordt VALS en vice versa) om.

  Voorbeeld: Een veld E-mail bevestigen verbergen als het e-mailveld leeg blijft.

   1. Stel de eigenschap `Visible` van het veld E-mail bevestigen in op `=NOT(if('address of email field'=""))` .

      ![ AEM Forms verbergt bevestigt e-mailgebied ](/help/edge/assets/aem-forms-not-function-hide-email-field.png)


   1. Stel de zichtbare expressie van het veld E-mail bevestigen in op `=FORMULATEXT ((address of visible property of the Confirm Email field))`

      ![ AEM Forms zichtbare uitdrukkingsformule ](/help/edge/assets/aem-forms-visible-expression-formula-text.png)


- AND(): retourneert alleen TRUE als alle opgegeven voorwaarden TRUE zijn.

   - Voorbeeld: een knop Verzenden alleen inschakelen als alle vereiste velden zijn ingevuld.

   1. Stel de eigenschap `Visible` van de knop &quot;submit&quot; in op:



      ```JavaScript
      =AND(NOT(address of `value` property of the `name` field = ""), NOT(address of `value` property of the `email` field = ""), NOT(address of `value` property of the `phone` field))
      ```

      Bijvoorbeeld:

      ```JavaScript
      =AND(NOT(F9=""), NOT(F12=""), NOT(F10=""))
      ```

   1. Stel de zichtbare expressie van het veld E-mail bevestigen in op

      ```JavaScript
      =FORMULATEXT ((address of visible property of the Confirm Email field))
      ```

      Bijvoorbeeld:

      ```JavaScript
      =FORMULATEXT(G14)
      ```

      Met deze formule wordt de knop &quot;Verzenden&quot; (TRUE) alleen weergegeven als alle velden (naam, e-mail, telefoon) zijn ingevuld (NOT()) retourneert TRUE voor elke velden). Als dit niet het geval is, wordt de knop verborgen (AND(meerdere FALSES) = FALSE).

- OR(): Geeft TRUE terug als ten minste een van de opgegeven voorwaarden TRUE is.

   - Voorbeeld: een korting toepassen als een gebruiker een van de van toepassing zijnde codes voor het kortingscoupon invoert.

   1. Stel de eigenschap `Visible` van het veld &quot;final amount&quot; in op:


  ```JavaScript
     =IF(OR(F14="BlackFridaySale", F14="NewYearDiscount"), (F6*DAYS(F3,F2)* 0.7) , (F6*DAYS(F3,F2)))
  ```

   1. Stel de waardeexpressie van het veld E-mail bevestigen in op

      ```JavaScript
      =FORMULATEXT ((address of value property of the final amount field))
      ```

      Bijvoorbeeld:

      ```JavaScript
      =FORMULATEXT(F7)
      ```

      Deze formule berekent een korting van 30% als de gebruiker een couponcode invoert (couponCode = &quot;NewYearDiscount&quot;) OF (couponCode = &quot;BlackVrijdagSale&quot;), anders wordt de korting op 0 ingesteld.

**functies van de Tekst:**

- IF(): evalueert een voorwaarde en geeft een specifieke waarde als TRUE, en een andere waarde als FALSE.

   - Voorbeeld: een aangepast bericht weergeven op basis van een gekozen productcategorie.

   1. Stel de eigenschap `Value` van het `message` veld in op `Only upto 7 kg check-in lagguage is allowed!` :

   1. Stel de eigenschap `Visible` van het veld `message` in op:


      ```JavaScript
      =if(address of value property of chosen product category ="Economy", TRUE(), FALSE())
      ```

      Bijvoorbeeld:

      ```JavaScript
      =if(F5="Economy", TRUE(), FALSE())
      ```

   1. Stel de waardeexpressie van het veld `message` in op

      ```JavaScript
      =FORMULATEXT ((address of value property of the final amount field))
      ```

      Bijvoorbeeld:

      ```JavaScript
      =FORMULATEXT(G15)
      ```

      In deze formule wordt het bericht &quot;Alleen inchecken van bagage tot 7 kg is toegestaan!&quot; weergegeven. als de gekozen klasse &quot;Economy&quot;is, anders verlaat het het berichtgebied leeg.

**functies Math:**

- SUM(): voegt waarden uit een opgegeven celbereik toe.

  Voorbeeld: de totale kosten berekenen van artikelen in een winkelwagentje.

  In de waardeexpressie van het veld &quot;totale kosten&quot;:
SUM(prijs * hoeveelheid)

  In deze formule wordt ervan uitgegaan dat je afzonderlijke velden hebt voor &quot;prijs&quot; en &quot;hoeveelheid&quot; van elk object. Het vermenigvuldigt ze en gebruikt SUM() om de totale kosten voor alle artikelen in het winkelwagentje op te tellen.

- ROUND(): rondt een getal af tot een opgegeven aantal decimalen.

  Voorbeeld: het afronden van een berekend kortingsbedrag op twee decimalen.

  In de waardeexpressie van het veld &quot;discontobedrag&quot; (ervan uitgaande dat een korting elders wordt berekend):
ROUND(korting, 2)

  Met deze formule wordt de kortingswaarde afgerond op twee decimalen.

- MIN(): retourneert de laagste waarde van een opgegeven celbereik.

  Voorbeeld: zoeken naar de minimumleeftijd voor een inschrijvingsformulier op basis van een geselecteerd land.

  In de expressie van een veld met de waarde &quot;minimumleeftijd&quot;:
MIN (ageLimits [ &quot;US&quot;], ageLimits [ &quot;VK&quot;], ageLimits [ &quot;Frankrijk&quot;])

  Deze formule veronderstelt u een lijst genoemd &quot;ageLimits&quot;hebt die minimumleeftijdsvereisten voor verschillende landen opslaat. Het gebruikt MIN() om de kleinste waarde onder hen te vinden.


Bovendien laat het Aangepaste Blok van Forms u volledige leiding van uw vormen nemen door [ douanefuncties ](#creating-custom-functions) te creëren. Met aangepaste functies kunt u uw eigen regels en logica definiëren, zodat u volledig zelf kunt bepalen hoe uw formulieren zich gedragen.


## Aangepaste functies maken en implementeren

Het uit-van-de-Doos (OOTB) Aangepaste blok van Forms verstrekt implementaties voor vele [ gemeenschappelijke spreadsheetfuncties ](#spreadsheet-functions-for-rules). Voor meer korrelige controle over uw formulieren kunt u echter alle OOTB-functies gebruiken die beschikbaar zijn in Microsoft® Excel of Google Sheets in uw Adaptive Forms-blokken. Adaptief Forms-blok bevat geen implementatie voor alle OOTB-functies die beschikbaar zijn in Microsoft® Excel of Google Sheets. Als u een van deze functies nodig hebt, kunt u een aangepaste functie met een vergelijkbare syntaxis ontwikkelen voor de functionaliteit die wordt geboden door Microsoft® Excel of Google Sheets. Bijvoorbeeld, kunt u de [ functie van het Jaar van Microsoft® Excel () ](https://support.microsoft.com/en-us/office/calculate-age-113d599f-5fea-448f-a4c3-268927911b37#) uitvoeren om leeftijd van geboortedatum te berekenen.


### Een aangepaste functie maken

Aangepaste functies bevinden zich in het `[Adaptive form block]/functions.js` -bestand. Het aanmaakproces omvat doorgaans de volgende stappen:

- Functiedeclaratie: definieer de functienaam en de parameters ervan (de inputs die deze accepteert).
- Logische implementatie: schrijf de code die de specifieke berekeningen of manipulaties beschrijft die door de functie worden uitgevoerd.
- Functie exporteren: maak de functie toegankelijk binnen uw regels door deze uit het relevante bestand te exporteren.

### Voorbeeld: functie Year

In dit voorbeeld worden twee aangepaste functies getoond die de functie YEAR() van Microsoft® Excel simuleren om de leeftijd te berekenen:


```JavaScript
/**
 - Get the current date and time
 - @name now
 - @returns {Date} The current date and time as a Date object
 */
function now() {
  const today = new Date();
  return today;
}

/**
 - Get the year from a Date object
 - @name year
 - @param {Date} date The date object
 - @throws {TypeError} If the input is not a Date object
 - @returns {number} The year as a number
 */
function year(date) {
  let inputDate = new Date(date)

  if (!(inputDate instanceof Date)) {
    throw new TypeError("Input must be a Date object");
  }

  const year = inputDate.getFullYear();

  return year;
}

// Make the function accessible for use in rules
export { now, year };
```

### Een aangepaste functie in een formulier gebruiken

De aangepaste functie in uw formulier gebruiken:

1. **voeg de Functie** toe: Omvat uw douanefunctie in het `[Adaptive form block]/functions.js` dossier. Vergeet niet deze toe te voegen aan de instructie export in het bestand.
1. **stel het Dossier** op: Stel het bijgewerkte `functions.js` dossier aan uw project GitHub op en verifieer een succesvolle bouwstijl.
1. **Gebruik van de Functie**: Heb toegang tot de functie binnen spreadsheet van uw vorm gebruikend `Value`, `Value Expression`, `Visible`, of `Visible Expression` eigenschappen, gelijkend op een andere spreadsheetfunctie die OOTB wordt gesteund.
1. **Voorproef de Vorm**: Gebruik AEM Sidekick aan voorproef uw vorm met de onlangs uitgevoerde functie.

