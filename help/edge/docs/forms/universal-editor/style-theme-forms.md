---
title: Thema en stijl aanpassen voor een Edge Delivery Services for AEM Forms
description: Pas het thema en de stijl voor AEM Forms die via Edge Delivery Services worden geleverd, effectief aan en zorg voor een consistente en merkbare gebruikerservaring.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: ac780399-34fe-457d-aaf4-b675656c024d
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '2493'
ht-degree: 0%

---

# Het uiterlijk van uw formulieren aanpassen

Formulierstyling in Edge Delivery Services for AEM Forms vereist een geavanceerd inzicht in CSS-aangepaste eigenschappen, blokgebaseerde architectuur en componentspecifieke doelstrategieën. In tegenstelling tot de traditionele benaderingen van formulierstijlen, implementeert het Adaptive Forms Block een systematisch ontwerptokensysteem dat consistent ontwerp mogelijk maakt en tegelijkertijd de prestaties en toegankelijkheidsvoordelen van Edge Delivery Services behoudt.

De Adaptive Forms Block-architectuur genereert gestandaardiseerde HTML-structuren voor alle formuliercomponenten, waardoor voorspelbare patronen ontstaan voor CSS-gerichtheid en -aanpassing. Dankzij deze consistentie kunnen ontwikkelaars uitgebreide opmaaksystemen implementeren die geschaald kunnen worden uitgebreid in complexe formulierimplementaties, terwijl de blokgebaseerde optimalisaties die Edge Delivery Services uitzonderlijk snel maken, behouden blijven.

Deze uitgebreide handleiding heeft betrekking op de technische grondslagen van formulieropmaak in het Edge Delivery Services-ecosysteem, waaronder CSS-systemen voor aangepaste eigenschappen, HTML-structuurpatronen van componenten en geavanceerde opmaaktechnieken. De documentatie biedt zowel theoretische kennis als praktische implementatierichtlijnen voor het maken van geavanceerde, merkgebonden formulierervaringen.

## Wat u gaat meemaken

**CSS het Beheer van de Eigenschappen van de Douane**: Begrijp het volledige veranderlijke systeem dat vormverschijning, met inbegrip van kleurenschema&#39;s, typografieschalen, het uit elkaar plaatsen systemen, en lay-outparameters controleert. Leer hoe u deze eigenschappen kunt overschrijven en uitbreiden om uitgebreide merkthema&#39;s te implementeren.

**Begrip van de Architectuur van de Component**: Verkrijg diepe kennis van de de structuurpatronen van HTML die door elk type van vormcomponent worden gebruikt, toelatend nauwkeurige CSS het richten en aanpassing zonder de onderliggende functionaliteit of toegankelijkheidseigenschappen te breken.

**Geavanceerde het Stijlen Technieken**: Voer geavanceerde het stileren patronen met inbegrip van op staat-gebaseerd het stileren uit, ontvankelijke ontwerpintegratie, en prestaties-geoptimaliseerde aanpassingsstrategieën die de snel-ladende kenmerken van Edge Delivery Services handhaven.

**Professionele Strategieën van de Implementatie**: Leer industrie-standaardbenaderingen om vorm het stileren met inbegrip van de integratie van het ontwerpsysteem, onderhoudsbare CSS architectuur, en het oplossen van problementechnieken voor complexe het stileren scenario&#39;s.

## Werken met formulierveldtypen

Alvorens in het stileren te duiken, herzien de gemeenschappelijke vorm [ gebiedstypes ](/help/edge/docs/forms/universal-editor/create-custom-component.md#supported-fieldtypes) die door het AanpassingsBlok van Forms worden gesteund:

- Invoervelden: dit zijn tekstinvoer, e-mailinvoer, wachtwoordinvoer en meer.
- Selectievakjesgroepen: wordt gebruikt voor het selecteren van meerdere opties.
- Keuzerondjes: wordt gebruikt voor het selecteren van slechts één optie in een groep.
- Vervolgkeuzelijsten: ook wel selectiekaders genoemd. Deze worden gebruikt voor het selecteren van een optie in een lijst.
- Deelvensters/containers: gebruikt om gerelateerde formulierelementen samen te groeperen.

## Basisbeginselen voor stijlen

Het begrip van [ fundamentele CSS concepten ](https://www.w3schools.com/css/css_intro.asp) is essentieel alvorens specifieke vormgebieden te stileren:

- [ Kiezers ](https://www.w3schools.com/css/css_selectors.asp): CSS de Kiezers staan u toe om specifieke elementen van HTML voor het stileren te richten. U kunt elementkiezers, klassekiezers of id-kiezers gebruiken.
- [ Eigenschappen ](https://www.w3schools.com/css/css_syntax.asp): CSS de eigenschappen bepalen de visuele verschijning van elementen. Veelvoorkomende eigenschappen voor het opmaken van formuliervelden zijn kleur, achtergrondkleur, rand, opvulling, marge en meer.
- [ Model van de Doos ](https://www.w3schools.com/css/css_boxmodel.asp): Het CSS kadermodel beschrijft de structuur van de elementen van HTML als inhoudsgebied dat door het opvullen, grenzen, en marges wordt omringd.
- Flexbox/Net: CSS [ Flexbox ](https://www.w3schools.com/css/css3_flexbox.asp) en [ lay-outs van het Net ](https://www.w3schools.com/css/css_grid.asp) zijn krachtige hulpmiddelen om ontvankelijke en flexibele ontwerpen tot stand te brengen.




## Uitgebreide formulieropmaak met aangepaste CSS-eigenschappen

Het blok Adaptive Forms maakt gebruik van een geavanceerde CSS-architectuur die is gebaseerd op aangepaste eigenschappen (CSS-variabelen) en die systematische opmaak en consistente opmaak mogelijk maakt voor alle formuliercomponenten. Kennis van deze structuur is van essentieel belang voor een effectieve aanpassing en branding van formulieren.

### De architectuur forms.css

De standaardformulierstijlen bevinden zich in de projectopslagplaats op `/blocks/form/form.css` en volgen een gestructureerde aanpak waarbij prioriteit wordt toegekend aan het behoud, de consistentie en de aanpassingsflexibiliteit. De architectuur bestaat uit verschillende belangrijke componenten:

**CSS de Stichting van Eigenschappen van de Douane**: Het het stileren systeem wordt voortgebouwd op CSS douaneeigenschappen die op het `:root` niveau worden bepaald, die een gecentraliseerd het thema systeem verstrekken dat door alle vormcomponenten cascades. Deze variabelen stellen ontwerptokens voor kleuren, typografie, spatiëring en layout-eigenschappen vast.

**op blok-Gebaseerde CSS Structuur**: Edge Delivery Services gebruikt een op blok-gebaseerde architectuur waar de `.form` klasse als primaire namespace voor alle op vorm betrekking hebbende stijlen dient, die juiste werkingsgebiedisolatie verzekeren en CSS conflicten met andere paginacomponenten verhinderen.

**Component-Specifieke het Stijlen**: De individuele vormcomponenten worden gestileerd gebruikend verenigbare omslagpatronen (`.{Type}-wrapper`) die voorspelbare het richten voor verschillende gebiedstypes terwijl het handhaven van de algemene integriteit van het ontwerpsysteem verstrekken.

### Referentie en aanpassing van aangepaste CSS-eigenschappen

Het formulieropmaaksysteem bevat meer dan 50 aangepaste CSS-eigenschappen die elk aspect van de vormgeving en het gedrag van het formulier bepalen. Als u deze eigenschappen begrijpt, is uitgebreide aanpassing mogelijk en blijft de consistentie van het ontwerp behouden.

+++ Variabelen voor kleur en thema

Met het kleurensysteem legt u een volledige visuele basis voor formulieren vast aan de hand van zorgvuldig georganiseerde aangepaste eigenschappen:

```css
:root {
    /* Primary color system */
    --background-color-primary: #fff;
    --label-color: #666;
    --border-color: #818a91;
    --form-error-color: #ff5f3f;
    
    /* Button color system */
    --button-primary-color: #5F8DDA;
    --button-secondary-color: #666;
    --button-primary-hover-color: #035fe6;
    
    /* Form-specific color applications */
    --form-background-color: var(--background-color-primary);
    --form-input-border-color: var(--border-color);
    --form-invalid-border-color: #ff5f3f;
    --form-label-color: var(--label-color);
}
```

**Praktisch Voorbeeld van de Aanpassing**: Om een donker thema voor uw vormen uit te voeren, treedt de variabelen van de basiskleur met voeten:

```css
:root {
    --background-color-primary: #1a1a1a;
    --label-color: #e0e0e0;
    --border-color: #404040;
    --form-error-color: #ff6b6b;
    --button-primary-color: #4a9eff;
}
```

Deze enkele wijziging doorloopt alle formuliercomponenten omdat het systeem variabele verwijzingen gebruikt in plaats van geharde waarden.

+++

+++ Variabelen voor typografie en spatiëring

Variabelen voor typografie en spatiëring bieden uitgebreide controle over de tekstpresentatie en de spatiëring van de layout:

```css
:root {
    /* Font size system */
    --form-font-size-m: 22px;
    --form-font-size-s: 18px;
    --form-font-size-xs: 16px;
    
    /* Component-specific typography */
    --form-label-font-size: var(--form-font-size-s);
    --form-label-font-weight: 400;
    --form-title-font-weight: 600;
    --form-input-font-size: 1rem;
    
    /* Spacing system */
    --form-field-horz-gap: 40px;
    --form-field-vert-gap: 20px;
    --form-input-padding: 0.75rem 0.6rem;
    --form-padding: 0 10px;
}
```

**Praktisch Voorbeeld van de Aanpassing**: Om tot een compactere vormlay-out met kleinere typografie te leiden:

```css
:root {
    --form-font-size-m: 18px;
    --form-font-size-s: 14px;
    --form-font-size-xs: 12px;
    --form-field-horz-gap: 20px;
    --form-field-vert-gap: 15px;
    --form-input-padding: 0.5rem 0.4rem;
}
```

+++

+++ Lay-out- en structuurvariabelen

Indelingsvariabelen bepalen de formulierafmetingen, het rastergedrag en de indeling van de component:

```css
:root {
    /* Form layout */
    --form-width: 100%;
    --form-columns: 12;
    --form-submit-width: 100%;
    
    /* Card-based components */
    --form-card-border-radius: 4px;
    --form-card-padding: 0.6rem 0.8rem;
    --form-card-shadow: 0 1px 2px rgb(0 0 0 / 3%);
    --form-card-hover-shadow: 0 2px 4px rgb(0 0 0 / 6%);
    
    /* Wizard-specific layout */
    --form-wizard-padding: 0px;
    --form-wizard-padding-bottom: 160px;
    --form-wizard-step-legend-padding: 10px;
}
```

**Praktisch Voorbeeld van de Aanpassing**: Om een kaart-stijl vorm met verbeterde visuele diepte tot stand te brengen:

```css
:root {
    --form-card-border-radius: 12px;
    --form-card-padding: 1.5rem 2rem;
    --form-card-shadow: 0 4px 12px rgb(0 0 0 / 8%);
    --form-card-hover-shadow: 0 8px 24px rgb(0 0 0 / 12%);
    --form-background-color: #f8f9fa;
}

.form {
    background: var(--form-background-color);
    border-radius: var(--form-card-border-radius);
    box-shadow: var(--form-card-shadow);
    padding: var(--form-card-padding);
    max-width: 600px;
    margin: 2rem auto;
}
```

+++

### CSS-stijlpatronen en aanbevolen procedures

Het Adaptive Forms Block volgt specifieke CSS-patronen die zorgen voor onderhoud, prestaties en consistente opmaak voor alle componenten.

+++ Primaire stijlpatronen

**blok-Vlakke de Container van de Vorm**: Richt de primaire vormcontainer voor algemene lay-out en achtergrond het stileren:

```css
.form {
    /* Form-wide styles */
    max-width: 800px;
    margin: 0 auto;
    background-color: var(--form-background-color);
    padding: var(--form-padding);
    border-radius: var(--form-card-border-radius);
}
```

**Patronen van de Omsluitend van de Component**: De specifieke gebiedstypes van het doel die verenigbare omslagklassen gebruiken:

```css
/* Text input fields */
.form .text-wrapper input {
    padding: var(--form-input-padding);
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    font-size: var(--form-input-font-size);
    border-radius: 4px;
    width: 100%;
}

/* Email input fields */
.form .email-wrapper input {
    padding: var(--form-input-padding);
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    font-size: var(--form-input-font-size);
}

/* Button styling */
.form .button-wrapper button {
    background-color: var(--form-button-background-color);
    color: var(--form-button-color);
    padding: var(--form-button-padding);
    border: var(--form-button-border);
    font-size: var(--form-button-font-size);
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.2s ease;
}

.form .button-wrapper button:hover {
    background-color: var(--form-button-background-hover-color);
}
```

+++

+++ Geavanceerde aanpassingspatronen

**gebied-Specifieke het richten**: De individuele gebieden van het doel door naam voor unieke het stileren vereisten:

```css
/* Style specific fields */
.form .field-email input {
    background-image: url('data:image/svg+xml;...'); /* Email icon */
    background-repeat: no-repeat;
    background-position: right 12px center;
    padding-right: 40px;
}

.form .field-phone input {
    text-align: center;
    letter-spacing: 1px;
    font-family: monospace;
}
```

**op staat-Gebaseerde het Stileren**: Voer bevestiging en interactiestatus uit:

```css
/* Validation states */
.form .field-wrapper[data-valid="false"] input {
    border-color: var(--form-error-color);
    box-shadow: 0 0 0 2px rgba(255, 95, 63, 0.1);
}

.form .field-wrapper[data-valid="true"] input {
    border-color: #28a745;
    box-shadow: 0 0 0 2px rgba(40, 167, 69, 0.1);
}

/* Focus states */
.form .text-wrapper input:focus,
.form .email-wrapper input:focus {
    outline: none;
    border-color: var(--button-primary-color);
    box-shadow: 0 0 0 2px rgba(95, 141, 218, 0.2);
}
```

+++


## Structuur van componenten

Het Adaptive Forms Block biedt een consistente HTML-structuur voor verschillende formulierelementen, waardoor de opmaak en het beheer worden vereenvoudigd. U kunt de componenten manipuleren met CSS voor opmaakdoeleinden.

+++ Algemene componenten (behalve dropdowns, radiegroepen, en checkbox groepen):

Alle formuliervelden, met uitzondering van vervolgkeuzelijsten, groepen keuzerondjes en groepen selectievakjes, hebben de volgende HTML-structuur:

#### HTML-structuur van algemene componenten

```HTML
  <div class="{Type}-wrapper field-{Name}   field-wrapper" data-required={Required}>
     <label for="{FieldId}" class="field-label">First   Name</label>
     <input type="{Type}" placeholder="{Placeholder}"   maxlength="{Max}" id={FieldId}" name="{Name}"   aria-describedby="{FieldId}-description">
     <div class="field-description" aria-live="polite"  id="{FieldId}-description">
      Hint - First name should be minimum 3 characters  and a maximum of 10 characters.
     </div>
  </div>
```

- Klassen: het div-element heeft verschillende klassen voor het aanwijzen van specifieke elementen en opmaak. U hebt de klassen `{Type}-wrapper` of `field-{Name}` nodig om een CSS-kiezer te ontwikkelen waarmee u een formulierveld kunt opmaken:
- {Type}: identificeert de component op veldtype. Bijvoorbeeld tekst (tekstomloop), getal (nummeromloop), datum (datumomloop).
- {Name}: identificeert de component op naam. De naam van het veld mag alleen alfanumerieke tekens bevatten, de opeenvolgende streepjes in de naam worden vervangen door één streepje `(-)` en de begin- en eindstreepjes in een veldnaam worden verwijderd. Voornaam (veld-voornaam veld-wrapper).
- {FieldId}: het is een unieke id voor het veld, die automatisch wordt gegenereerd.
- {Required}: een Booleaanse waarde die aangeeft of het veld verplicht is.
- Label: het element `label` verschaft een beschrijvende tekst voor het veld en koppelt deze aan het invoerelement met behulp van het kenmerk `for` .
- Invoer: het element `input` definieert het type gegevens dat moet worden ingevoerd. Bijvoorbeeld tekst, nummer, e-mail.
- Beschrijving (optioneel): De `div` with class `field-description` biedt extra informatie of instructies voor de gebruiker.

**Voorbeeld van de Structuur van HTML**

```HTML
<div class="text-wrapper field-first-name field-wrapper" data-required="true">
  <label for="firstName" class="field-label">First Name</label>
  <input type="text" placeholder="Enter your first name" maxlength="50" id="firstName" name="firstName" aria-describedby="firstName-description">
  <div class="field-description" aria-live="polite" id="firstName-description">
    Please enter your legal first name.
  </div>
</div>
```

#### CSS-kiezer voor algemene componenten

```css
/* Primary Pattern: Target field wrapper by type */
.form .{Type}-wrapper {
    /* Container styling for specific field types */
    margin-bottom: 1rem;
    border-radius: 4px;
}

/* Primary Pattern: Target input fields within wrapper */
.form .{Type}-wrapper input {
    /* Input field styling using CSS custom properties */
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    width: 100%;
    font-size: var(--form-input-font-size);
}

/* Context-specific: Target element by field name when higher specificity needed */
.form .field-{Name} input {
    /* Field-specific customizations */
    /* Use this pattern for unique styling requirements */
}
```

- `.form .{Type}-wrapper`: hiermee wordt het element met de veldomloop geactiveerd op basis van het veldtype. `.form .text-wrapper` richt zich bijvoorbeeld op alle tekstveldcontainers.
- `.form .{Type}-wrapper input`: hiermee wordt de werkelijke invoer-elementen in de omslag aangegeven. Dit is het aanbevolen patroon voor het opmaken van formulierinvoer.
- `.form .field-{Name}`: richt elementen op basis van de specifieke veldnaam. `.form .field-first-name` is bijvoorbeeld gericht op de veldcontainer Voornaam. Gebruik `.form .field-{Name} input` om het invoerelement specifiek als doel in te stellen.
- **vermijd**: `main .form form .{Type}-wrapper` - dit leidt tot onnodige CSS specificiteit en is moeilijker te handhaven.

**CSS van het Voorbeeld Selectors voor Algemene Componenten**

```css
/* Primary Pattern: Target all text input fields */
.form .text-wrapper input {
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    width: 100%;
    font-size: var(--form-input-font-size);
    background-color: var(--form-input-background-color);
}

/* Context-specific: Target field by name when higher specificity needed */
.form .field-first-name input {
    text-transform: capitalize;
    border-color: var(--button-primary-color);
}

/* Alternative with main context if needed */
main .form .text-wrapper input {
    /* Use only when you need higher specificity */
    color: var(--form-label-color);
}
```

+++

+++ Onderdeeltje

Voor vervolgkeuzemenu&#39;s wordt het element `select` gebruikt in plaats van het element `input` :

#### HTML-structuur van vervolgkeuzecomponent

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>
```

**de Structuur van HTML van het Voorbeeld**

```HTML
<div class="drop-down-wrapper field-country field-wrapper" data-required="true">
  <label for="country" class="field-label">Country</label>
  <select id="country" name="country">
    <option value="">Select Country</option>
    <option value="US">United States</option>
    <option value="CA">Canada</option>
  </select>
  <div class="field-description" aria-live="polite" id="country-description">
    Please select your country of residence.
  </div>
</div>
```

#### CSS-kiezers voor vervolgkeuzecomponent

In de volgende CSS-code worden enkele voorbeelden van CSS-kiezers voor vervolgkeuzecomponenten weergegeven.

```css
/* Primary Pattern: Target the dropdown wrapper */
.form .drop-down-wrapper {
    /* Container layout using flexbox */
    display: flex;
    flex-direction: column;
    margin-bottom: var(--form-field-vert-gap);
}

/* Target the select element */
.form .drop-down-wrapper select {
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    background-color: var(--form-input-background-color);
    font-size: var(--form-input-font-size);
    color: var(--form-label-color);
}

/* Style the label */
.form .drop-down-wrapper .field-label {
    margin-bottom: 5px;
    font-weight: var(--form-label-font-weight);
    color: var(--form-label-color);
    font-size: var(--form-label-font-size);
}
```

- Richt op Wrapper: De eerste selecteur (`.drop-down-wrapper`) richt het buitenomslagelement, die ervoor zorgt dat de stijlen op de volledige dropdown component van toepassing zijn.
- Flexbox Layout: in Flexbox worden het label, de vervolgkeuzelijst en de beschrijving verticaal gerangschikt voor een zuivere lay-out.
- Labelstijlen: het label wordt weergegeven met een grotere tekendikte en een kleine marge.
- Vervolgkeuzestijl: het element `select` ontvangt een rand, opvulling en afgeronde hoeken voor een gepolijst uiterlijk.
- Achtergrondkleur: er is een consistente achtergrondkleur ingesteld voor visuele harmonie.
- Pijl-aanpassing: optionele stijlen verbergen de standaardvervolgkeuzepijl en maken een aangepaste pijl met een Unicode-teken en -positie.

+++

+++ Keuzerondjes

Keuzerondjes hebben een eigen HTML-structuur en CSS-structuur, net als vervolgkeuzecomponenten:

#### HTML-structuur van groep keuzerondjes

```HTML
<fieldset class="radio-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   <legend for="{FieldId}" class="field-label">....</legend>
   <% for each radio in Group %>
   <div class="radio-wrapper field-{Name}">
      <input type="radio" value="" id="{UniqueId}" data-field-type="radio-group" name="{FieldId}">
      <label for="{UniqueId}" class="field-label">...</label>
   </div>
   <% end for %>
</fieldset>
```

**de Structuur van HTML van het Voorbeeld**

```HTML
<fieldset class="radio-group-wrapper field-color field-wrapper" id="color_preference" name="color_preference" data-required="true">
  <legend for="color_preference" class="field-label">Favorite Color:</legend>
  <% for each radio in Group %>
    <div class="radio-wrapper field-color">
      <input type="radio" value="red" id="color_red" data-field-type="radio-group" name="color_preference">
      <label for="color_red" class="field-label">Red</label>
    </div>
    <div class="radio-wrapper field-color">
      <input type="radio" value="green" id="color_green" data-field-type="radio-group" name="color_preference">
      <label for="color_green" class="field-label">Green</label>
    </div>
    <div class="radio-wrapper field-color">
      <input type="radio" value="blue" id="color_blue" data-field-type="radio-group" name="color_preference">
      <label for="color_blue" class="field-label">Blue</label>
    </div>
  <% end for %>
</fieldset>
```

#### CSS-kiezers voor keuzerondjes

- Doelstelling van de veldset

```css
/* Target radio group container */
.form .radio-group-wrapper {
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    margin-bottom: var(--form-field-vert-gap);
}
```

Deze kiezer richt zich op elk veld dat met de klasse Radio-group-wrapper is ingesteld. Dit is handig als u algemene stijlen wilt toepassen op de hele groep keuzerondjes.

- Labels voor keuzerondjes als doel instellen

```css
/* Target radio button labels */
.form .radio-wrapper label {
    font-weight: var(--form-label-font-weight);
    margin-right: 10px;
    color: var(--form-label-color);
    font-size: var(--form-label-font-size);
    cursor: pointer;
}
```

- Alle keuzerondjes in een specifieke veldset op basis van de naam ervan als doel instellen

```css
/* Target all radio button labels within a specific fieldset based on its name */
.form .field-color .radio-wrapper label {
    /* Field-specific radio label customizations */
    /* Add your custom styles here */
}
```

+++

+++ Selectievakjesgroepen

#### HTML-structuur van Checkbox-groep

```HTML
<fieldset class="checkbox-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   <legend for="{FieldId}" class="field-label">....</legend>
   <% for each radio in Group %>
   <div class="checkbox-wrapper field-{Name}">
      <input type="checkbox" value="" id="{UniqueId}" data-field-type="checkbox-group" name="{FieldId}">
      <label for="{UniqueId}" class="field-label">...</label>
   </div>
   <% end for %>
</fieldset>
```

**de Structuur van HTML van het Voorbeeld**

```HTML
<fieldset class="checkbox-group-wrapper field-topping field-wrapper" id="topping_preference" name="topping_preference" data-required="false">
  <legend for="topping_preference" class="field-label">Pizza Toppings:</legend>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="pepperoni" id="topping_pepperoni" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_pepperoni" class="field-label">Pepperoni</label>
  </div>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="mushrooms" id="topping_mushrooms" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_mushrooms" class="field-label">Mushrooms</label>
  </div>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="onions" id="topping_onions" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_onions" class="field-label">Onions</label>
  </div>
</fieldset>
```

#### CSS-kiezers voor groepen selectievakjes

- De buitenomloop instellen: deze kiezers richten zich op de buitenste containers van groepen keuzerondjes en selectievakjes, zodat u algemene stijlen kunt toepassen op de volledige groepsstructuur. Dit is handig voor het instellen van spatiëring, uitlijning of andere aan de layout gerelateerde eigenschappen.

```css
/* Primary Pattern: Targets radio group wrappers */
.form .radio-group-wrapper {
    margin-bottom: var(--form-field-vert-gap); /* Adds space between radio groups */
    display: flex;
    flex-direction: column;
    border: var(--form-fieldset-border);
    padding: var(--form-input-padding);
}

/* Primary Pattern: Targets checkbox group wrappers */
.form .checkbox-group-wrapper {
    margin-bottom: var(--form-field-vert-gap); /* Adds space between checkbox groups */
    display: flex;
    flex-direction: column;
    border: var(--form-fieldset-border);
    padding: var(--form-input-padding);
}
```

- Doelgroeplabels: deze kiezer richt zich op het `.field-label` -element binnen zowel de groepsomvattende items voor keuzerondjes als voor selectievakjes. Hierdoor kunt u de labels specifiek voor deze groepen opmaken, waardoor deze beter opvallen.

```css
/* Primary Pattern: Target group labels */
.form .radio-group-wrapper legend,
.form .checkbox-group-wrapper legend {
    font-weight: var(--form-title-font-weight); /* Makes the group label bold */
    margin-bottom: 0.5rem;
    font-size: var(--form-fieldset-legend-font-size);
    color: var(--form-fieldset-legend-color);
    padding: var(--form-fieldset-legend-padding);
    border: var(--form-fieldset-legend-border);
}
```

- Afzonderlijke invoer en labels als doel instellen: deze kiezers bieden meer korrelige controle over afzonderlijke keuzerondjes, selectievakjes en de bijbehorende labels. U kunt deze stijlen gebruiken om het formaat, de spatiëring of de verschillende visuele stijlen aan te passen.

```css
/* Primary Pattern: Styling radio buttons */
.form .radio-group-wrapper input[type="radio"] {
    margin-right: 8px; /* Adds space between the input and its label */
    margin-bottom: 4px;
    cursor: pointer;
}

/* Primary Pattern: Styling radio button labels */
.form .radio-group-wrapper label {
    font-size: var(--form-label-font-size); /* Changes the label font size */
    color: var(--form-label-color);
    font-weight: var(--form-label-font-weight);
    display: flex;
    align-items: center;
    cursor: pointer;
}

/* Primary Pattern: Styling checkboxes */
.form .checkbox-group-wrapper input[type="checkbox"] {
    margin-right: 8px; /* Adds space between the input and its label */
    margin-bottom: 4px;
    cursor: pointer;
}

/* Primary Pattern: Styling checkbox labels */
.form .checkbox-group-wrapper label {
    font-size: var(--form-label-font-size); /* Changes the label font size */
    color: var(--form-label-color);
    font-weight: var(--form-label-font-weight);
    display: flex;
    align-items: center;
    cursor: pointer;
}
```

- De weergave van keuzerondjes en selectievakjes aanpassen: hiermee wordt de standaardinvoer verborgen en worden `:before` en `:after` pseudo-elementen gebruikt om aangepaste visuele elementen te maken die de weergave wijzigen op basis van de status &#39;checked&#39;.

```css
/* Hide the default radio button or checkbox */
.form .radio-group-wrapper input[type="radio"],
.form .checkbox-group-wrapper input[type="checkbox"] {
    opacity: 0;
    position: absolute;
    width: 1px;
    height: 1px;
}

/* Create a custom radio button */
.form .radio-group-wrapper input[type="radio"] + label::before {
    content: '';
    display: inline-block;
    width: 16px;
    height: 16px;
    border: 2px solid var(--form-input-border-color);
    border-radius: 50%;
    margin-right: 8px;
    background-color: var(--form-input-background-color);
    transition: all 0.2s ease;
}

.form .radio-group-wrapper input[type="radio"]:checked + label::before {
    background-color: var(--button-primary-color);
    border-color: var(--button-primary-color);
    box-shadow: inset 0 0 0 3px var(--form-input-background-color);
}

/* Create a custom checkbox */
.form .checkbox-group-wrapper input[type="checkbox"] + label::before {
    content: '';
    display: inline-block;
    width: 16px;
    height: 16px;
    border: 2px solid var(--form-input-border-color);
    border-radius: 2px;
    margin-right: 8px;
    background-color: var(--form-input-background-color);
    transition: all 0.2s ease;
}

.form .checkbox-group-wrapper input[type="checkbox"]:checked + label::before {
    background-color: var(--button-primary-color);
    border-color: var(--button-primary-color);
    background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16"><path fill="white" d="M13.854 3.646a.5.5 0 0 1 0 .708l-7 7a.5.5 0 0 1-.708 0l-3.5-3.5a.5.5 0 1 1 .708-.708L6.5 10.293l6.646-6.647a.5.5 0 0 1 .708 0z"/></svg>');
    background-repeat: no-repeat;
    background-position: center;
}
```

+++

+++ Deelvenster/Containercomponenten

#### HTML-structuur van deelvenster-/containercomponenten

```HTML
<fieldset class="panel-wrapper field-{PanelName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false">bannerComponent</legend>
  <div class="{Type}-wrapper field-{Name} field-wrapper">
    <label for="{FieldId}" class="field-label">First Name</label>
    <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}">
    <div class="field-description" aria-live="polite" id="{FieldId}-description">
      Hint - First name should be minimum 3 characters and a maximum of 10 characters.
    </div>
  </div>
</fieldset>
```

**de Structuur van HTML van het Voorbeeld**

```HTML
<fieldset class="panel-wrapper field-login field-wrapper">
  <legend for="login" class="field-label" data-visible="false">Login Information</legend>
  <div class="text-wrapper field-username field-wrapper">
    <label for="username" class="field-label">Username</label>
    <input type="text" placeholder="Enter your username" maxlength="50" id="username" name="username">
    <div class="field-description" aria-live="polite" id="username-description">
      Please enter your username or email address.
    </div>
  </div>
  <div class="password-wrapper field-password field-wrapper">
    <label for="password" class="field-label">Password</label>
    <input type="password" placeholder="Enter your password" maxlength="20" id="password" name="password">
    <div class="field-description" aria-live="polite" id="password-description">
      Your password must be at least 8 characters long.
    </div>
  </div>
</fieldset>
```

- Het veldsetelement fungeert als de deelvenstercontainer met de klassepaneel-wrapper en aanvullende klassen voor opmaak op basis van de naam van het deelvenster (veldaanmelding).
- Het legenda-element (`<legend>`) fungeert als de titel van het deelvenster met de tekst &quot;Aanmeldingsgegevens&quot; en de veldlabel voor de klasse. Het attribuut data-visible=&quot;false&quot; kan met JavaScript worden gebruikt om de zichtbaarheid van de titel te regelen.
- Binnen de veldset, meerdere.{Type} -wrapper-elementen (.text-wrapper en .password-wrapper in dit geval) vertegenwoordigen afzonderlijke formuliervelden in het deelvenster.
- Elke omslag bevat een etiket, een inputgebied, en een beschrijving, gelijkend op de vorige voorbeelden.


#### Voorbeeld-CSS-kiezers voor component Panel/Container

1. Doelstelling voor deelvenster:

```CSS
  /- Target the entire panel container */
  main .form form .panel-wrapper {
    /- Add your styles here (e.g., border, padding, background color) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
 }
```

- De kiezer van `.panel-wrapper` maakt alle elementen met de omloop van het klassepaneel, zodat alle deelvensters er consistent uitzien.

1. Richting geven aan de titel van het deelvenster:

```CSS
  /- Target the legend element (panel title) */
  .panel-wrapper legend {
    /- Add your styles here (e.g., font-weight, font-size) */
    font-weight: bold;
    font-size: 16px;
    padding-bottom: 5px;
    margin-bottom: 10px;
    border-bottom: 1px solid #ddd; /- Optional: create a separation line */
  }
```

- De kiezer van `.panel-wrapper legend` maakt een stijl van het legenda-element in het deelvenster, zodat de titel visueel opvalt.


1. Afzonderlijke velden aanwijzen in het deelvenster:

```CSS
/- Target all form field wrappers within a panel */
main .form form .panel-wrapper .{Type}-wrapper {
  /- Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

- De `.panel-wrapper .{Type}-wrapper` -kiezer richt zich op alle omslagen met de `.{Type}-wrapper` -klasse in het deelvenster, zodat u de ruimte tussen formuliervelden kunt opmaken.

1. Specifieke velden instellen (optioneel):

```CSS
  /- Target the username field wrapper */
  main .form form .panel-wrapper .text-wrapper.field-username {
    /- Add your styles here (specific to username field) */
  }

  /- Target the password field wrapper */
  main .form form .panel-wrapper .password-wrapper.field-password {
    /- Add your styles here (specific to password field) */
  }
```

- Met deze optionele kiezers kunt u specifieke veldwrappers in het deelvenster gebruiken voor unieke opmaak, zoals het markeren van het veld gebruikersnaam.


+++

+++ Herhalbaar deelvenster

#### HTML-structuur van een herhalbaar deelvenster

```HTML
<fieldset class="panel-wrapper field-{PanelName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false">bannerComponent</legend>
  <div class="{Type}-wrapper field-{Name} field-wrapper">
    <label for="{FieldId}" class="field-label">First Name</label>
    <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}">
    <div class="field-description" aria-live="polite" id="{FieldId}-description">
      Hint - First name should be minimum 3 characters and a maximum of 10 characters.
    </div>
</fieldset>
```

**de Structuur van HTML van het Voorbeeld**

```HTML
<fieldset class="panel-wrapper field-contact field-wrapper" data-repeatable="true">
  <legend for="contact-1" class="field-label" data-visible="false">Contact Information</legend>
  <div class="text-wrapper field-name field-wrapper">
    <label for="name-1" class="field-label">Name</label>
    <input type="text" placeholder="Enter your name" maxlength="50" id="name-1" name="contacts[0].name">
    <div class="field-description" aria-live="polite" id="name-1-description">
      Please enter your full name.
    </div>
  </div>
  <div class="email-wrapper field-email field-wrapper">
    <label for="email-1" class="field-label">Email</label>
    <input type="email" placeholder="Enter your email address" maxlength="100" id="email-1" name="contacts[0].email">
    <div class="field-description" aria-live="polite" id="email-1-description">
      Please enter a valid email address.
    </div>
  </div>
</fieldset>

<fieldset class="panel-wrapper field-contact field-wrapper" data-repeatable="true">
  <legend for="contact-2" class="field-label" data-visible="false">Contact Information</legend>
  <div class="text-wrapper field-name field-wrapper">
    <label for="name-2" class="field-label">Name</label>
    <input type="text" placeholder="Enter your name" maxlength="50" id="name-2" name="contacts[1].name">
    <div class="field-description" aria-live="polite" id="name-2-description">
      Please enter your full name.
    </div>
  </div>
  <div class="email-wrapper field-email field-wrapper">
    <label for="email-2" class="field-label">Email</label>
    <input type="email" placeholder="Enter your email address" maxlength="100" id="email-2" name="contacts[1].email">
    <div class="field-description" aria-live="polite" id="email-2-description">
      Please enter a valid email address.
    </div>
  </div>
</fieldset>
```

Elk deelvenster heeft dezelfde structuur als het voorbeeld van één deelvenster, met extra kenmerken:

- data-herhaalable=&quot;true&quot;: dit kenmerk geeft aan dat het deelvenster dynamisch kan worden herhaald met JavaScript of een framework.

- Unieke IDs en namen: Elk element binnen het paneel heeft een unieke identiteitskaart (bijvoorbeeld, naam-1, e-mail-1) en naamattributen die op de index van het paneel (bijvoorbeeld, name= &quot;contacten [ 0 ].name&quot;) worden gebaseerd. Op deze manier kunnen de gegevens correct worden verzameld wanneer meerdere deelvensters worden verzonden.


#### CSS-kiezers voor een herhaalbaar deelvenster

- Alle herhalende deelvensters als doel instellen:

```CSS
  /- Target all panels with the repeatable attribute */
 main .form form .panel-wrapper[data-repeatable="true"] {
    /- Add your styles here (e.g., border, margin) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
  }
```

De kiezer maakt stijlen van alle deelvensters die kunnen worden herhaald, zodat de vormgeving consistent blijft.


- Afzonderlijke velden in een deelvenster aanwijzen:

```CSS
/- Target all form field wrappers within a repeatable panel */
main .form form .panel-wrapper[data-repeatable="true"] .{Type}-wrapper {
  /- Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

Met deze kiezer worden alle veldomlooptekens binnen een herhaalbaar deelvenster geplaatst, waarbij een consistente afstand tussen velden behouden blijft.

- Specifieke velden activeren (binnen een deelvenster):

```CSS
/- Target the name field wrapper within the first panel */
main .form form .panel-wrapper[data-repeatable="true"][data-index="0"] .text-wrapper.field-name {
  /- Add your styles here (specific to first name field) */
}

/- Target all
```


+++


+++ Bestandsbijlage

#### HTML-structuur voor bestandsbijlage

```HTML
<div class="file-wrapper field-{FileName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false"> File Attachment </legend>
  <div class="file-drag-area">
    <div class="file-dragIcon"></div>
    <div class="file-dragText">Drag and Drop To Upload</div>
    <button class="file-attachButton" type="button">Attach</button>
    <input type="file" accept="audio/*, video/*, image/*, text/*, application/pdf" id="{id}" name="{FileName}" autocomplete="off" multiple="" required="required">
  </div>
  <div class="files-list">
    <div data-index="0" class="file-description">
      <span class="file-description-name">ClaimForm.pdf</span>
      <span class="file-description-size">26 kb</span>
      <button class="file-description-remove" type="button"></button>
    </div>
  </div>
</div>
```

**de Structuur van HTML van het Voorbeeld**


```HTML
<div class="file-wrapper field-claim_form field-wrapper">
  <legend for="claim_form" class="field-label" data-visible="false">File Attachment</legend>
  <div class="file-drag-area">
    <div class="file-dragIcon"></div>
    <div class="file-dragText">Drag and Drop To Upload</div>
    <button class="file-attachButton" type="button">Attach</button>
  </div>
  <input type="file" accept="audio/*, video/*, image/*, text/*, application/pdf" id="claim_form"
         name="claim_form" autocomplete="off" multiple="" required="required" data-max-file-size="2MB">
  <div class="files-list">
    </div>
</div>
```

- Het klassenkenmerk gebruikt de opgegeven naam voor de bestandsbijlage (claim_form).
- De id- en naamkenmerken van het invoerelement komen overeen met de naam van de bestandsbijlage (claim_form).
- De sectie voor de bestandenlijst is aanvankelijk leeg. Deze wordt dynamisch gevuld met JavaScript wanneer bestanden worden geüpload.


#### CSS-kiezers voor de component Bestandsbijlage

- De volledige component Bestandsbijlage als doel instellen:

```CSS
/- Target the entire file attachment component */
main .form form .file-wrapper {
  /- Add your styles here (e.g., border, padding) */
  border: 1px solid #ccc;
  padding: 15px;
  border-radius: 4px;
  margin-bottom: 20px;
}
```

Met deze kiezer wordt de gehele bestandsbijlage geschaald, inclusief de legenda, het sleepgebied, het invoerveld en de lijst.

- Specifieke elementen:

```CSS
/- Target the drag and drop area */
main .form form .file-wrapper .file-drag-area {
  /- Add your styles here (e.g., background color, border) */
  background-color: #f0f0f0;
  border: 1px dashed #ddd;
  padding: 10px;
  text-align: center;
}

/- Target the file input element */
main .form form .file-wrapper input[type="file"] {
  /- Add your styles here (e.g., hide the default input) */
  display: none;
}

/- Target individual file descriptions within the list (populated dynamically) */
main .form form .file-wrapper .files-list .file-description {
  /- Add your styles here (e.g., margin, display) */
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
}

/- Target the file name within the description */
main .form form .file-wrapper .files-list .file-description .file-description-name {
  /- Add your styles here (e.g., font-weight) */
  font-weight: bold;
}
```

Met deze kiezers kunt u verschillende onderdelen van de bestandsbijlage afzonderlijk opmaken. U kunt de stijlen aanpassen aan uw ontwerpvoorkeuren.

+++



## Stijlcomponenten

U kunt formuliervelden opmaken op basis van het specifieke type (`{Type}-wrapper`) of de afzonderlijke namen (`field-{Name}`). Hierdoor kunt u de weergave van het formulier korter beheren en aanpassen.

+++ Stijlen op basis van veldtype

U kunt CSS-kiezers gebruiken om specifieke veldtypen als doel in te stellen en stijlen consistent toe te passen.

#### HTML-structuur

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>
```

**de Structuur van HTML van het Voorbeeld**

```HTML
<div class="text-wrapper field-name field-wrapper" data-required="true">
  <label for="name" class="field-label">Name</label>
  <input type="text" placeholder="Enter your name" maxlength="50" id="name" name="name">
</div>

<div class="number-wrapper field-age field-wrapper" data-required="true">
  <label for="age" class="field-label">Age</label>
  <input type="number" placeholder="Enter your age" id="age" name="age">
</div>

<div class="email-wrapper field-email field-wrapper" data-required="true">
  <label for="email" class="field-label">Email Address</label>
  <input type="email" placeholder="Enter your email" id="email" name="email">
</div>
```

- Elk veld wordt opgenomen in een element `div` met verschillende klassen:
   - `{Type}-wrapper` - Hiermee wordt het type veld aangegeven. Bijvoorbeeld `form-text-wrapper` , `form-number-wrapper` , `form-email-wrapper` .
   - `field-{Name}` - Identificeert het veld met de naam. Bijvoorbeeld `form-name` , `form-age` , `form-email` .
   - `field-wrapper`: Een algemene klasse voor alle veldwrappers.
- Het kenmerk `data-required` geeft aan of het veld verplicht of optioneel is.
- Elk veld heeft een overeenkomstig label, invoerelement en mogelijke aanvullende elementen, zoals plaatsaanduidingen en beschrijvingen.




#### Voorbeeld-CSS-kiezers

```CSS
/- Primary Pattern: Target all text input fields */
.form .text-wrapper input {
  /- Add your styles here */
  width: 100%;
  padding: var(--form-input-padding);
}

/- Primary Pattern: Target all number input fields */
.form .number-wrapper input {
  /- Add your styles here */
  letter-spacing: 2px; /- Example for adding letter spacing to all number fields */
  text-align: center;
}
```

+++

+++ Stijlen op basis van veldnaam

U kunt afzonderlijke velden ook op naam als doel instellen om unieke stijlen toe te passen.

#### HTML-structuur

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id="{FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Enter the 6 digit number sent to your mobile number.
   </div>
</div>
```

**de Structuur van HTML van het Voorbeeld**

```HTML
<div class="number-wrapper field-otp field-wrapper" data-required="true">
  <label for="otp" class="field-label">OTP</label>
  <input type="number" placeholder="Enter your OTP" maxlength="6" id="otp" name="otp" aria-describedby="otp-description">
  <div class="field-description" aria-live="polite" id="otp-description">
    Hint - Enter the 6 digit number sent to your mobile number.
   </div>
</div>
```


#### Voorbeeld-CSS-kiezer

```CSS
/- Primary Pattern: Target specific field by name */
.form .field-otp input {
   letter-spacing: 2px;
   text-align: center;
   font-family: monospace;
}

/- Context-specific: Use higher specificity when needed */
main .form .field-otp input {
   /- Use only when you need to override other styles */
   font-weight: bold;
}
```

Deze CSS richt zich op alle inputelementen die binnen een element worden gevestigd dat de klasse `field-otp` heeft. De Edge Delivery Services-formulierstructuur volgt de conventies van het Adaptive Forms Block, waarbij containers worden gemarkeerd met veldspecifieke klassen zoals &#39;field-otp&#39; voor velden met de naam &#39;otp&#39;.


## CSS-bestandsstructuur en -implementatie

### **Implementatie van de Verwijzing**

De volledige naslaggids voor formulierstijlen is beschikbaar in de AEM Forms Boilerplate-opslagplaats:

```
https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/blocks/form/form.css
```

Dit bestand fungeert als de canonieke implementatie van het systeem met aangepaste CSS-eigenschappen en vormt de basis voor alle formulieropmaak. Het omvat uitvoerige definities voor alle CSS variabelen, component het stileren patronen, en ontvankelijke ontwerpimplementaties.

+++

+++ Projectintegratie

In uw Edge Delivery Services-project implementeert u formulierstijlen via deze gestructureerde aanpak:

```
/blocks/form/form.css          // Core form block styles (copied from boilerplate)
/styles/styles.css             // Global site styles and CSS variable overrides
/styles/lazy-styles.css        // Additional component enhancements
```

+++

+++ Uitvoeringsstrategie

**met voeten treedt het Bezit van de Douane CSS met voeten**: Overschrijf vormvariabelen in uw globale stijlen om merkspecifiek het thema uit te voeren:

```css
/* In /styles/styles.css */
:root {
    /* Brand-specific overrides */
    --button-primary-color: #your-brand-color;
    --form-background-color: #your-background;
    --label-color: #your-text-color;
}
```

**Component-Specifieke Aanpassingen**:
Componentspecifieke opmaak toevoegen terwijl het CSS-variabele systeem behouden blijft:

```css
/* Enhanced component styling */
.form .text-wrapper input {
    border-radius: var(--form-card-border-radius);
    transition: all 0.2s ease;
}

.form .text-wrapper input:focus {
    transform: translateY(-1px);
    box-shadow: 0 0 0 3px rgba(var(--button-primary-color), 0.1);
}
```

**Responsieve Integratie van het Ontwerp**: Gebruik CSS douaneeigenschappen binnen media vragen voor verenigbaar ontvankelijk gedrag:

```css
@media (max-width: 768px) {
    :root {
        --form-input-padding: 0.875rem;
        --form-field-vert-gap: 1rem;
        --form-padding: 1rem;
    }
}
```

+++

### Voorbeeld van complete stijlimplementatie

In deze sectie ziet u hoe u een modern formulier met een merk maakt met aangepaste CSS-eigenschappen. De implementatie is onderverdeeld in duidelijke subsecties voor gemakkelijker begrip en navigatie.



+++ &#x200B;1. Merkthema-variabelen

Definieer het kleurenpalet, de spatiëring en de typografie van uw merk met gebruik van aangepaste CSS-eigenschappen.

```css
/* Custom brand theme */
:root {
  /* Brand color system */
  --brand-primary: #2563eb;
  --brand-secondary: #64748b;
  --brand-success: #059669;
  --brand-error: #dc2626;
  --brand-background: #f8fafc;
  
  /* Override form variables */
  --background-color-primary: #ffffff;
  --button-primary-color: var(--brand-primary);
  --button-primary-hover-color: #1d4ed8;
  --form-error-color: var(--brand-error);
  --form-background-color: var(--brand-background);
  --label-color: var(--brand-secondary);
  --border-color: #d1d5db;
  
  /* Enhanced spacing */
  --form-input-padding: 1rem;
  --form-field-vert-gap: 1.5rem;
  --form-padding: 2rem;
  
  /* Modern typography */
  --form-font-size-s: 16px;
  --form-label-font-weight: 500;
}
```


+++

+++ &#x200B;2. Stijl van formuliercontainers

Pas een moderne achtergrond, randstraal en schaduw toe op de formuliercontainer voor een visueel aantrekkelijke indeling.


```css
/* Enhanced form container */
.form {
    background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 100%);
    border-radius: 12px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.05);
    max-width: 600px;
    margin: 2rem auto;
    overflow: hidden;
}
```




+++

+++ &#x200B;3. Invoerveldstijlen

Stijl tekst, e-mail en nummerinvoervelden voor een schone, moderne vormgeving.


```css
/* Modern input styling */
.form .text-wrapper input,
.form .email-wrapper input,
.form .number-wrapper input {
    background: white;
    border: 2px solid var(--border-color);
    border-radius: 8px;
    padding: var(--form-input-padding);
    font-size: 16px;
    transition: all 0.2s ease;
    width: 100%;
}
```


+++

+++ &#x200B;4. Aanvullende aanpassingen

U kunt de formulieropmaak verder uitbreiden door zich te richten op specifieke velden, frames of componenten. Verwijs naar vroegere secties voor geavanceerde patronen.

```css
/* Custom brand theme */
:root {
    /* Brand color system */
    --brand-primary: #2563eb;
    --brand-secondary: #64748b;
    --brand-success: #059669;
    --brand-error: #dc2626;
    --brand-background: #f8fafc;
    
    /* Override form variables */
    --background-color-primary: #ffffff;
    --button-primary-color: var(--brand-primary);
    --button-primary-hover-color: #1d4ed8;
    --form-error-color: var(--brand-error);
    --form-background-color: var(--brand-background);
    --label-color: var(--brand-secondary);
    --border-color: #d1d5db;
    
    /* Enhanced spacing */
    --form-input-padding: 1rem;
    --form-field-vert-gap: 1.5rem;
    --form-padding: 2rem;
    
    /* Modern typography */
    --form-font-size-s: 16px;
    --form-label-font-weight: 500;
}

/* Enhanced form container */
.form {
    background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 100%);
    border-radius: 12px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.05);
    max-width: 600px;
    margin: 2rem auto;
    overflow: hidden;
}

/* Modern input styling */
.form .text-wrapper input,
.form .email-wrapper input,
.form .number-wrapper input {
    background: white;
    border: 2px solid var(--border-color);
    border-radius: 8px;
    padding: var(--form-input-padding);
    font-size: 16px;
    transition: all 0.2s ease;
    width: 100%;
}

.form .text-wrapper input:focus,
.form .email-wrapper input:focus,
.form .number-wrapper input:focus {
    border-color: var(--brand-primary);
    box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
    transform: translateY(-1px);
}

/* Enhanced button styling */
.form .button-wrapper button[type="submit"] {
    background: linear-gradient(135deg, var(--brand-primary) 0%, #1d4ed8 100%);
    color: white;
    border: none;
    border-radius: 8px;
    padding: 1rem 2rem;
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s ease;
    width: 100%;
    box-shadow: 0 4px 12px rgba(37, 99, 235, 0.3);
}

.form .button-wrapper button[type="submit"]:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(37, 99, 235, 0.4);
}
```

Deze uitgebreide aanpak laat zien hoe aangepaste CSS-eigenschappen geavanceerd ontwerp mogelijk maken terwijl de structurele integriteit en toegankelijkheidsfuncties van het Adaptive Forms Block-systeem behouden blijven.

+++

## Problemen met CSS oplossen

+++ CSS-specificatieproblemen

```css
/- ❌ Problem: Styles not applying */
.text-wrapper input {
  color: red;
}

/- ✅ Solution: Match or exceed existing specificity */
.form .text-wrapper input {
  color: red;
}

/- ✅ Alternative: Use higher specificity when needed */
main .form .text-wrapper input {
  color: red;
}
```

+++

+++ Problemen met overschrijven van CSS-variabele

```css
/- ❌ Problem: Variables not working */
.form {
  --form-border-color: blue; /- Local scope only */
}

/- ✅ Solution: Define in root scope */
:root {
  --form-border-color: blue; /- Global scope */
}
```

+++

+++ Stijl formulierstatus

```css
/- Validation states */
.form .field-wrapper.error input {
  border-color: var(--form-error-color);
}

.form .field-wrapper.success input {
  border-color: var(--form-success-color);
}

/- Loading state */
.form[data-submitting="true"] {
  opacity: 0.7;
  pointer-events: none;
}

/- Disabled state */
.form input:disabled {
  background-color: var(--form-input-disabled-background);
  cursor: not-allowed;
}
```

+++

+++ Algemene fouten in kiezer

```css
/- ❌ Incorrect: Assumes direct nesting */
.form form input {
  /- This might miss inputs in wrappers */
}

/- ✅ Correct: Target actual structure */
.form .text-wrapper input {
  /- Targets actual HTML structure */
}

/- ❌ Avoid: Unnecessary specificity */
main .form form .text-wrapper input {
  /- Too specific, harder to override */
}

/- ✅ Preferred: Balanced specificity */
.form .text-wrapper input {
  /- Easier to maintain and override */
}
```

+++



### **Component-Specifieke Beste praktijken**


+++ Knopstijl

```css
/- Primary buttons */
.form .button-wrapper button[type="submit"] {
  background-color: var(--form-focus-color);
  color: white;
  border: none;
  padding: var(--form-input-padding);
  border-radius: var(--form-border-radius);
}

/- Secondary buttons */
.form .button-wrapper button[type="reset"] {
  background-color: transparent;
  color: var(--form-text-color);
  border: 1px solid var(--form-border-color);
}
```

+++

+++ Responsief formulierontwerp

```css
/- Mobile-first approach */
.form {
  width: 100%;
  padding: 1rem;
}

/- Tablet and up */
@media (min-width: 768px) {
  .form {
    max-width: var(--form-max-width);
    padding: var(--form-padding);
  }
}
```

+++

## Overzicht van best practices

1. **Eigenschappen van de Douane van het Gebruik CSS**: De variabelen van de hefboomwerking voor verenigbaar het thema
2. **volg op blok-Gebaseerde Architectuur**: Gebruik `.form` als primaire blokselecteur
3. **vermijd over-specificiteit**: Gebruik niet `main .form form` tenzij noodzakelijk
4. **Wrappers van het Doel**: Gebruik `.{Type}-wrapper` patronen voor component het richten
5. **handhaaf Consistentie**: Gebruik de zelfde selecteerspatronen door uw project
6. **Test over Apparaten**: Verzeker het werk van vormen goed op mobiel, tablet, en Desktop
7. **bevestigt Toegankelijkheid**: Zorg ervoor stijlen zich niet in het schermlezers of toetsenbordnavigatie mengen


