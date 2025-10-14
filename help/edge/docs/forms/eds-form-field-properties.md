---
title: Eigenschappen van adaptieve Forms-blokvelden beheren
description: Krachtige formulieren sneller maken met spreadsheets en Adaptieve eigenschappen van Forms-blokvelden! In deze handleiding worden alle eigenschappen weergegeven die door EDS Forms Block worden ondersteund.
feature: Edge Delivery Services
source-git-commit: ccc6439f68d8199154d4cd664b9cdb6428460a64
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 0%

---


# Eigenschappen van Adaptief Forms-blokveld

In dit document wordt een overzicht gegeven van de manier waarop JSON-schema wordt toegewezen aan weergegeven HTML in `blocks/form/form.js` . Hierbij wordt de nadruk gelegd op de manier waarop velden worden geïdentificeerd en weergegeven, op algemene patronen en op veldspecifieke verschillen.

## Hoe worden velden (`fieldType`) geïdentificeerd?

Elk veld in het JSON-schema heeft een `fieldType` -eigenschap die bepaalt hoe het wordt gerenderd. De `fieldType` kan zijn:

- **een speciaal type van A**\
  Voorbeelden: `drop-down` , `radio-group` , `checkbox-group` , `panel` , `plain-text` , `image` , `heading` , enzovoort.
- **Een geldig HTML inputtype**\
  Voorbeelden: `text` , `number` , `email` , `date` , `password` , `tel` , `range` , `file` , enzovoort.
- **Type A met a `-input` achtervoegsel**\
  Voorbeelden: `text-input` , `number-input` , enzovoort. (genormaliseerd voor het basistype, zoals `text` , `number` ).

Als `fieldType` een speciaal type aanpast, wordt a **douanerenderer** gebruikt. Anders, wordt het behandeld als a **standaardinputtype**.

Zie de secties hieronder voor de [&#x200B; volledige structuur en eigenschappen van HTML &#x200B;](#common-html-structure) voor elk gebiedstype.

## Algemene eigenschappen die door velden worden gebruikt

Hieronder ziet u de eigenschappen die door de meeste velden worden gebruikt:

- `id` - Geeft de element-id op en ondersteunt toegankelijkheid.
- `name`: definieert het kenmerk `name` voor invoer-, selectie- of veldsetelementen.
- `label.value` , `label.richText` , `label.visible` : geeft de label-/legendetekst, HTML-inhoud en zichtbaarheid op.
- `value` - Geeft de huidige waarde van het veld aan.
- `required`: voegt het attribuut `required` of validatiegegevens toe.
- `readOnly`, `enabled`: hiermee bepaalt u of het veld bewerkbaar of uitgeschakeld is.
- `description`: geeft de Help-tekst onder het veld weer.
- `tooltip`: stelt het kenmerk `title` voor invoer in.
- `constraintMessages`: levert aangepaste foutberichten als gegevenskenmerken.

## Algemene HTML-structuur

De meeste velden worden weergegeven in een omslag die een label en optionele Help-tekst bevat. Het volgende fragment demonstreert de structuur:

```html
<div class="<fieldType>-wrapper field-wrapper field-<name>" data-id="<id>">
<label for="<id>" class="field-label">Label</label>
<!-- Field-specific input/element here -->
<div class="field-description" id="<id>-description">Description or error
message</div>
</div>
```

Voor groepen (keuzerondjes/selectievakjes) en deelvensters wordt een `<fieldset>` met een `<legend>` gebruikt in plaats van een `<div>/<label>` . De Help-tekst <div> is alleen aanwezig als er een beschrijving is ingesteld.

## Weergave foutbericht

Foutberichten worden weergegeven in hetzelfde element van het type `.field-description` dat wordt gebruikt voor Help-tekst, dat dynamisch wordt bijgewerkt.

**wanneer een gebied ongeldig is**:

- De wrapper (bijvoorbeeld `.field-wrapper` ) krijgt de klasse `.field-invalid` toegewezen.
- De `.field-description` -inhoud wordt vervangen door het bijbehorende foutbericht.

**wanneer het gebied geldig** wordt:

- De `.field-invalid` -klasse wordt verwijderd.
- De `.field-description` wordt teruggezet naar de originele Help-tekst (indien beschikbaar) of wordt verwijderd als er geen bestaat.

Aangepaste foutberichten kunnen worden gedefinieerd met de eigenschap `constraintMessages` in JSON.\
Deze worden toegevoegd als `data-<constraint>ErrorMessage` -kenmerken op de omslag (bijvoorbeeld `data-requiredErrorMessage` ).

## Standaardinvoertypen (HTML-invoer of `*-input`)

Als `fieldType` geen speciaal type is, wordt het beschouwd als een standaard HTML-invoertype of als `<type>-input` bijvoorbeeld `text` , `number` , `email` , `date` , `text-input` , `number-input` .

- Het achtervoegsel `-input` wordt verwijderd en het basistype wordt gebruikt als het `type` -kenmerk van de invoer.
- Deze typen worden standaard afgehandeld in `renderField()` .
Algemene standaardinvoertypen zijn `text` , `number` , `email` , `date` , `password` , `tel` , `range` , `file` , enzovoort.  Ze accepteren ook `text-input` , `number-input` , enzovoort, die genormaliseerd zijn voor het basistype.

## Restricties voor standaardinvoertypen

Restricties worden toegevoegd als kenmerken op het invoerelement op basis van JSON-eigenschappen.

| JSON-eigenschap | HTML-kenmerk | Van toepassing op |
|--------------|---------------|------------|
| maxLength | maxlength | text, email, password, tel |
| minLength | minlengte | text, email, password, tel |
| patroon | patroon | text, email, password, tel |
| maximum | max | getal, bereik, datum |
| minimum | min | getal, bereik, datum |
| stap | stap | getal, bereik, datum |
| accepteren | accepteren | file |
| meerdere | meerdere | file |
| maxOccur | data-max | deelvenster |
| minOccur | data-min | deelvenster |

>[!NOTE]
>
> `multiple` is een Booleaanse eigenschap. Indien true, wordt het kenmerk `multiple` toegevoegd.

Deze kenmerken worden automatisch ingesteld door de formulierrenderer op basis van de JSON-definitie van het veld.

## Voorbeeld: HTML-structuur met restricties

In het volgende voorbeeld ziet u hoe een nummerveld wordt weergegeven met validatiebeperkingen en foutafhandelingskenmerken.

```html
<div class="number-wrapper field-wrapper field-age" data-id="age"
data-required="true"
data-minimumErrorMessage="Too small" data-maximumErrorMessage="Too large">
<label for="age" class="field-label">Age</label>
<input type="number"
id="age" name="age"
value="30" required min="18"
max="99" step="1"
placeholder="Enter your age" />
<div class="field-description" id="age-description"> Description or error message
</div>
</div>
```

Elk onderdeel van de HTML-structuur speelt een rol in gegevensbinding, -validatie en het weergeven van Help- of foutberichten.

## Veldspecifieke eigenschappen en de bijbehorende HTML-structuren

### Vervolgkeuzelijst

**Extra Eigenschappen:**

- `enum` / `enumNames` : Definieer de optiewaarden en de bijbehorende weergavelabels voor de vervolgkeuzelijst.
- `type`: schakelt meerdere selecties in als deze zijn ingesteld op `array` .
- `placeholder`: Voegt een uitgeschakelde plaatsaanduiding toe om gebruikers vóór de selectie te begeleiden.

Voorbeeld:

```html
<div class="drop-down-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true"
data-requiredErrorMessage="This field is required">
<label for="<id>" class="field-label">Label</label>
<select id="<id>" name="<name>" required title="Tooltip" multiple>
<option disabled selected value="">Placeholder</option>
<option value="opt1">Option 1</option>
<option value="opt2">Option 2</option>
</select>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### Onbewerkte tekst

**Extra Eigenschappen**:

- `richText`: indien waar (true), wordt HTML in de alinea gerenderd.

Voorbeeld:

```html
<div class="plain-text-wrapper field-wrapper field-<name>" data-id="<id>">
<label for="<id>" class="field-label">Label</label>
<p>Text or <a href="..." target="_blank">link</a></p>
</div>
```

### Selectievakje

**Extra Eigenschappen**:

- `enum` - Definieert de waarden voor de ingeschakelde en niet-ingeschakelde status van het selectievakje.
- `properties.variant / properties.alignment` - Geeft de visuele stijl en uitlijning voor selectievakjes in switchstijl aan.

Voorbeeld:

```html
<div class="checkbox-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true"
data-requiredErrorMessage="Please check this box">
<label for="<id>" class="field-label">Label</label>
<input type="checkbox"
id="<id>"
name="<name>" value="on"
required
data-unchecked-value="off" />
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### Knop

**Extra Eigenschappen**:

- `buttonType` - Geeft het gedrag van de knop op door het type van de knop in te stellen (knop, verzenden of opnieuw instellen).

Voorbeeld:

```html
<div class="button-wrapper field-wrapper field-<name>" data-id="<id>">
<button id="<id>" name="<name>" type="submit" class="button"> Label
</button>
</div>
```

### Multiline-invoer

**Extra Eigenschappen**:

- `minLength` - Geeft het minimale aantal tekens op dat is toegestaan in tekstinvoer of tekstveldinvoer.
- `maxLength` - Geeft het maximale aantal tekens op dat is toegestaan in een tekst- of tekstgebiedinvoer.
- `pattern` - Definieert een reguliere expressie die de invoerwaarde moet overeenkomen om als geldig te worden beschouwd.
- `placeholder` - Geeft plaatsaanduidingstekst weer binnen de invoer of het tekstgebied totdat een waarde wordt ingevoerd.

Voorbeeld:

```html
<div class="multiline-wrapper field-wrapper field-<name>" data-id="<id>"
data-minLengthErrorMessage="Too short" data-maxLengthErrorMessage="Too long">
<label for="<id>" class="field-label">Label</label>
<textarea id="<id>"
name="<name>" required
minlength="2"
maxlength="100"
pattern="[A-Za-z]+"
placeholder="Type here..."></textarea>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### Deelvenster

**Extra Eigenschappen**:

- `repeatable` - Geeft op of het deelvenster dynamisch kan worden herhaald.
- `minOccur`: stelt het minimaal vereiste aantal deelvensterinstanties in.   maxOccur: stelt het maximale aantal toegestane deelvensterinstanties in.
- `properties.variant` - Hiermee definieert u de visuele stijl of variant van het deelvenster.
- `properties.colspan` - Geeft aan hoeveel kolommen het deelvenster uitstrekt in een rasterlay-out.
- `index` - Geeft de positie van het deelvenster binnen de bovenliggende container aan.
- `fieldset`: Hiermee groepeert u verwante velden onder een `<fieldset>` -element met een legenda of label.

Voorbeeld:

```html
<fieldset class="panel-wrapper field-wrapper field-<name>" data-id="<id>"
name="<name>"
data-repeatable="true" data-index="0">
<legend class="field-label">Label</legend>
<!-- Nested fields here -->
<button type="button" class="add">Add</button>
<button type="button" class="remove">Remove</button>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</fieldset>
```

### Radio

**Extra Eigenschappen**:

- `enum` - Definieert de set met toegestane waarden voor het keuzerondje, dat wordt gebruikt als het waardekenmerk voor elke keuzerondje-optie.

Voorbeeld:

```html
<div class="radio-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true">
<label for="<id>" class="field-label">Label</label>
<input type="radio" id="<id>" name="<name>" value="opt1" required />
<div class="field-description" id="<id>-description"> Description or error message
</div>
</div>
```

### Groep keuzerondjes

**Extra Eigenschappen**:

- `enum` - Definieert de lijst met optiewaarden voor de groep keuzerondjes, die wordt gebruikt als de waarde van elk keuzerondje.
- `enumNames`: bevat weergavelabels voor de keuzerondjes, in overeenstemming met de volgorde van de opsomming.

Voorbeeld:

```html
<fieldset class="radio-group-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true">
<legend class="field-label">Label</legend>
<div>
<input type="radio" id="<id>-0" name="<name>" value="opt1" required />
<label for="<id>-0">Option 1</label>
</div>
<div>
<input type="radio" id="<id>-1" name="<name>" value="opt2" />
<label for="<id>-1">Option 2</label>
</div>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</fieldset>
```

### **Checkbox Groep**

**Extra Eigenschappen**:

- `enum` - Hiermee definieert u de lijst met optiewaarden voor de groep selectievakjes, die wordt gebruikt als de waarde van elk selectievakje.
- `enumNames`: bevat weergavelabels voor de selectievakjes, in overeenstemming met de volgorde van de opsomming.
- `minItems`: hiermee stelt u het minimale aantal selectievakjes in dat moet worden geselecteerd voor de geldigheid.
- `maxItems` - Hiermee stelt u het maximum aantal selectievakjes in dat kan worden geselecteerd voordat een fout wordt geactiveerd.

Voorbeeld:

```html
<fieldset class="checkbox-group-wrapper field-wrapper field-<name>" data-id="<id>"
data-required="true" data-minItems="1"
data-maxItems="3">
<legend class="field-label">Label</legend>
<div>
<input type="checkbox" id="<id>-0" name="<name>" value="opt1" required />
<label for="<id>-0">Option 1</label>
</div>
<div>
<input type="checkbox" id="<id>-1" name="<name>" value="opt2" />
<label for="<id>-1">Option 2</label>
</div>
<div class="field-description" id="<id>-description"> Description or error message
</div>
</fieldset>
```

### Afbeelding

**Extra Eigenschappen**:

- `value / properties['fd:repoPath']` - Hiermee definieert u het bronpad of het opslagpad van de afbeelding voor het renderen van de afbeelding.
- `altText`: biedt alternatieve tekst voor de afbeelding (alt-kenmerk) om de toegankelijkheid te verbeteren.

Voorbeeld:

```html
<div class="image-wrapper field-wrapper field-<name>" data-id="<id>">
<picture>
<img src="..." alt="..." />
<!-- Optimized sources -->
</picture>
</div>
```

### Kop

**Extra Eigenschappen**:

- `value` - Geeft de tekstinhoud op die binnen het kopelement moet worden weergegeven (bijvoorbeeld `<h2>` ).

Voorbeeld:

```html
<div class="heading-wrapper field-wrapper field-<name>" data-id="<id>">
<h2 id="<id>">Heading Text</h2>
</div>
```

Zie de implementatie in `blocks/form/form.js` en `blocks/form/util.js` voor meer informatie.


<!--Each form field is represented as a dedicated row in the spreadsheet, analogous to fields in a database table. The column headers act as labels for the various properties supported by the form field block.

Think of your form as a table in a spreadsheet, where each line represents a different question or piece of information you want to collect. The table headings tell you what kind of answers you can expect for each section.

The below table lists all the properties that are supported by the Adaptive Forms Block.

**Master Your Forms with These Adaptive Forms Block Field Properties:**

This table details all the properties you can use to customize your Adaptive Forms Block fields:

| Property | Description | Example |
|---|---|---|
| **Type** | [HTML input type](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types) (text, email, number, etc.), [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea), [select](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select), [fieldset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) | `text`, `email`, `radio`, `select` |
| **Name** | This defines the unique identifier for submitted data (e.g., 'email' for an email address field).  Choose a clear and unique name for each field, as the name serves as internal field identifier used for data mapping during submission. | `user_name`, `email_address` |
| **Label** | User-friendly field label | `"Full Name"`, `"Choose your country"` |
| **Value** | Default value displayed | `"John Doe"`, `"United States"` |
| **Placeholder** | Hint text within the field | `"Enter your email address"` |
| **Description** | Help text for users | `"Please enter a valid email address"` |
| **Visible** | Show/hide the field initially | `true`, `false` |
| **Mandatory** | Require a value from the user | `true`, `false` |
| **Min/Max** | Set minimum/maximum values (number, date, text length) | `18` (age), `2025-12-31` (date) |
| **Accept** | Allowed file types for file upload | `"image/jpeg,image/png"` |
| **Multiple** | Allow multiple file selections | `true`, `false` |
| **Options** | Comma-separated list for dropdown menus | `"Option 1, Option 2, Option 3"` |
| **Checked** | Default-selected radio button/checkbox | `true`, `false` |
| **Fieldset** | Group fields together | Fieldset name (e.g., `"Personal Information"`) |-->

