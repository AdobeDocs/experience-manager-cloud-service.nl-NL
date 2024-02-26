---
title: Thema en stijl aanpassen voor een AEM Forms Edge Delivery Service-formulier
description: Thema en stijl aanpassen voor een AEM Forms Edge Delivery Service-formulier
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 59ed012f10a20939c846c8fff088534c5638f3db
workflow-type: tm+mt
source-wordcount: '1268'
ht-degree: 0%

---


# Formuliervelden opmaken

Forms is van cruciaal belang voor gebruikersinteractie op websites, zodat deze gegevens kunnen invoeren. Deze handleiding behandelt de basisbeginselen van het opmaken van verschillende formuliervelden in de [Formulierblok](/help/edge/docs/forms/create-forms.md)en helpt u visueel aantrekkelijke en gebruiksvriendelijke formulieren te maken.

## Werken met formulierveldtypen

Voordat u naar de stijl gaat, bekijkt u eerst de algemene formulierveldtypen die worden ondersteund door het formulierblok:

* Invoervelden: dit zijn tekstinvoer, e-mailinvoer, wachtwoordinvoer en meer.
* Selectievakjesgroepen: wordt gebruikt voor het selecteren van meerdere opties.
* Keuzerondjes: wordt gebruikt voor het selecteren van slechts één optie in een groep.
* Vervolgkeuzelijsten: ook wel selectiekaders genoemd. Deze worden gebruikt voor het selecteren van een optie in een lijst.
* Deelvensters/containers: gebruikt om gerelateerde formulierelementen samen te groeperen.

## Basisbeginselen voor stijlen

Kennis van de fundamentele CSS-concepten is van cruciaal belang voordat u specifieke formuliervelden opmaakt:

* Kiezers: Met CSS-kiezers kunt u specifieke HTML-elementen instellen voor opmaak. U kunt elementkiezers, klassekiezers of id-kiezers gebruiken.
* Eigenschappen: CSS-eigenschappen definiëren de visuele weergave van elementen. Veelvoorkomende eigenschappen voor het opmaken van formuliervelden zijn kleur, achtergrondkleur, rand, opvulling, marge en meer.
* Vakmodel: in het CSS-kadermodel wordt de structuur van HTML-elementen beschreven als een inhoudsgebied dat wordt omgeven door opvulling, randen en marges.
* Flexbox/Grid: CSS-lay-outs Flexbox en Raster zijn krachtige gereedschappen voor het maken van responsieve en flexibele ontwerpen.

## Een formulier opmaken voor formulierblok

Het formulierblok biedt een gestandaardiseerde HTML-structuur, waardoor het selecteren en opmaken van formulieronderdelen wordt vereenvoudigd:

* **Standaardstijlen bijwerken**: U kunt de standaardstijlen van een formulier wijzigen door de `/blocks/form/form.css file`. Dit bestand biedt uitgebreide opmaak voor een formulier, met ondersteuning voor uit meerdere stappen bestaande wizardformulieren. Het benadrukt het gebruiken van douaneCSS variabelen voor gemakkelijke aanpassing, onderhoud, en het eenvormige formatteren over vormen. Voor instructies bij het toevoegen van het Blok van de Vorm aan uw project, verwijs naar [een formulier maken](/help/edge/docs/forms/create-forms.md).

* **Aanpassing**: De standaardwaarde gebruiken `forms.css` als basis en pas deze aan om de vormgeving van uw formuliercomponenten te wijzigen, zodat het visueel aantrekkelijk en gebruiksvriendelijk wordt. De bestandsstructuur stimuleert de organisatie en handhaaft stijlen voor formulieren, waardoor consistente ontwerpen op uw website worden bevorderd.

## Indeling van de structuur van forms.css

* **Algemene variabelen:** Gedefinieerd bij de `:root` niveau, deze variabelen (`--variable-name`) slaat waarden op die in de hele stijlpagina worden gebruikt voor consistentie en gemak van updates. Deze variabelen definiëren kleuren, tekengrootten, opvulling en andere eigenschappen. U kunt uw eigen globale variabelen declareren of bestaande variabelen wijzigen om de stijl van het formulier te wijzigen.

* **Stijlen voor universele kiezer:** De `*` kiezer komt overeen met elk element in het formulier. De stijlen worden dan standaard op alle componenten toegepast, inclusief het instellen van de `box-sizing` eigenschap aan `border-box`.

* **Formulierstijl:** Deze sectie richt zich op het stileren van vormcomponenten gebruikend selecteurs om specifieke HTML elementen te richten. Hiermee worden stijlen gedefinieerd voor invoervelden, tekstgebieden, selectievakjes, keuzerondjes, bestandsinvoer, formulierlabels en beschrijvingen.

* **Tovenaar het stileren (indien van toepassing):** Deze sectie is gewijd aan het stileren van de tovenaar lay-out, een multi-step vorm waar elke stap tegelijkertijd wordt getoond. Hiermee worden stijlen gedefinieerd voor de tovenaarscontainer, veldsets, legenda&#39;s, navigatieknoppen en responsieve lay-outs.

* **Mediaquery&#39;s:** Deze stijlen bieden stijlen voor verschillende schermgrootten, waarbij de lay-out en de stijl op basis daarvan worden aangepast.

* **Diverse stijlen:**: In deze sectie worden stijlen beschreven voor geluids- of foutberichten, gebieden voor het uploaden van bestanden en andere elementen die u in een formulier tegenkomt.


## Structuur van componenten

Het formulierblok biedt een consistente HTML-structuur voor verschillende formulierelementen, zodat u eenvoudig kunt opmaken en beheren. U kunt de componenten manipuleren met CSS voor opmaakdoeleinden.

### Algemene componenten (behalve dropdowns, radiegroepen, en checkbox groepen):

Alle formuliervelden, met uitzondering van vervolgkeuzelijsten, groepen keuzerondjes en groepen selectievakjes, hebben de volgende HTML-structuur:

#### HTML-structuur

```HTML
<div class="form-{Type}-wrapper form-{Name} field-wrapper" data-required={Required}>
  <label for="{FieldId}" class="field-label">Field Label</label>
  <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id="{FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Description of the field.
  </div>
</div>
```

* Klassen: het div-element heeft verschillende klassen voor het aanwijzen van specifieke elementen en opmaak. U hebt de opdracht `form-{Type}-wrapper` of `form-{Name}` klassen voor het ontwikkelen van een CSS-kiezer voor het opmaken van een formulierveld:
   * {Type}: Identificeert de component op veldtype. Bijvoorbeeld tekst (form-text-wrapper), nummer (form-number-wrapper), datum (form-date-wrapper).
   * {Name}: Identificeert de component op naam. De naam van het veld mag alleen alfanumerieke tekens bevatten, de opeenvolgende streepjes in de naam worden vervangen door één streepje `(-)`en de begin- en eindstreepjes in een veldnaam worden verwijderd. Voornaam (form-first-name field-wrapper).
   * {FieldId}: Het is een unieke id voor het veld, die automatisch wordt gegenereerd.
   * {Required}: Het is een Booleaanse waarde die aangeeft of het veld verplicht is.
* Label: De `label` Het element biedt een beschrijvende tekst voor het veld en koppelt deze aan het invoerelement met behulp van het `for` kenmerk.
* Invoer: De `input` element definieert het type gegevens dat moet worden ingevoerd. Bijvoorbeeld tekst, nummer, e-mail.
* Beschrijving (optioneel): De `div` with, klasse `field-description` geeft aanvullende informatie of instructies voor de gebruiker.

**Voorbeeld van een HTML-structuur**

```HTML
<div class="form-text-wrapper form-first-name field-wrapper" data-required="true">
  <label for="firstName" class="field-label">First Name</label>
  <input type="text" placeholder="Enter your first name" maxlength="50" id="firstName" name="firstName" aria-describedby="firstName-description">
  <div class="field-description" aria-live="polite" id="firstName-description">
    Please enter your legal first name.
  </div>
</div>
```

**CSS-kiezer voor algemene componenten**

```CSS
.form-{Type}-wrapper input {
  /* Add your styles here */
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}


.form-{Name} input {
  /* Add your styles here */
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}
```

* `.form-{Type}-wrapper`: Hiermee wordt de buitenzijde geactiveerd `div` element dat op het gebiedstype wordt gebaseerd. Bijvoorbeeld: `.form-text-wrapper` richt alle gebieden van de tekstinput.
* `.form-{Name}`: Hiermee selecteert u het element verder op basis van de specifieke veldnaam. Bijvoorbeeld: `.form-first-name` wordt het tekstveld Voornaam gebruikt.

**Voorbeeld-CSS-kiezers voor algemene componenten**

```CSS
/*Target all text input fields */

.form-text-wrapper input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/*Target all fields with name first-name*/

.form-first-name input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}
```


### Onderdeeltje

Voor vervolgkeuzemenu&#39;s kunt u de opdracht `select` element wordt gebruikt in plaats van een `input` element:


#### HTML-structuur

```HTML
<div class="form-drop-down-wrapper form-{Name} field-wrapper" data-required={required}>
  <label for="{FieldId}" class="field-label">First Name</label>
  <select id="{FieldId}" name="{Name}"><option></option><option></option></select>
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
  </div>
</div>
```

**Voorbeeld van HTML-structuur**

```HTML
    <div class="form-drop-down-wrapper form-country field-wrapper" data-required="true">
      <label for="country" class="field-label">Country</label>
      <select id="country" name="country">
         <option value="">Select Country</option>
         <option value="US">United States</option>
         <option value="CA">Canada</option>
    </select>
   <div class="field-description" aria-live="polite" id="country-description">Please select your country of residence.</div>
   </div>
```

#### Voorbeeld-CSS-kiezers voor vervolgkeuzelijst

```CSS
/* Target the outer wrapper */
.form-drop-down-wrapper {
  /* Add your styles here */
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
}

/* Style the label */
.form-drop-down-wrapper .field-label {
  margin-bottom: 5px;
  font-weight: bold;
}

/* Style the dropdown itself */
.form-drop-down-wrapper select {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
  background-color: white; /* Ensure a consistent background */
  /* Adjust arrow appearance as needed */
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}

/* Optional: Style the dropdown arrow */
.form-drop-down-wrapper select::-ms-expand {
  display: none; /* Hide the default arrow for IE11 */
}

.form-drop-down-wrapper select::after {
  content: "\25BC";
  font-size: 12px;
  color: #ccc;
  /* Adjust positioning as needed */
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
}
```

* Doel van omsluitend item: de eerste kiezer (`.form-drop-down-wrapper`) is gericht op het buitenste omslagelement, waarbij de stijlen worden toegepast op de gehele vervolgkeuzecomponent.
* Flexbox Layout: in Flexbox worden het label, de vervolgkeuzelijst en de beschrijving verticaal gerangschikt voor een zuivere lay-out.
* Labelstijlen: het label wordt weergegeven met een grotere tekendikte en een kleine marge.
* Vervolgkeuzestijl: het geselecteerde element ontvangt een rand, opvulling en afgeronde hoeken voor een gepolijst uiterlijk.
* Achtergrondkleur: er is een consistente achtergrondkleur ingesteld voor visuele harmonie.
* Pijl-aanpassing: optionele stijlen verbergen de standaardvervolgkeuzepijl en maken een aangepaste pijl met een Unicode-teken en -positie.

### Groepen keuzerondjes en selectievakjes

Net als vervolgkeuzecomponenten hebben groepen keuzerondjes en selectievakjes hun eigen HTML-structuur en CSS-aspecten:

#### HTML-structuur van groep keuzerondjes

```HTML
<div class="form-checkbox-group-wrapper form-{Name} field-wrapper" data-required={required}>
  <label class="field-label">{Label Text}</label>
  <div class="checkbox-group">
    <input type="checkbox" id="{FieldId}-1" name="{Name}" value="{Value1}">
    <label for="{FieldId}-1">{Option 1 Text}</label>
    <input type="checkbox" id="{FieldId}-2" name="{Name}" value="{Value2}">
    <label for="{FieldId}-2">{Option 2 Text}</label>
    </div>
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Select multiple options (if applicable).
  </div>
</div>
```


#### HTML-structuur van groep keuzerondjes

```HTML
<div class="form-checkbox-group-wrapper form-{Name} field-wrapper" data-required={required}>
  <label class="field-label">{Label Text}</label>
  <div class="checkbox-group">
    <input type="checkbox" id="{FieldId}-1" name="{Name}" value="{Value1}">
    <label for="{FieldId}-1">{Option 1 Text}</label>
    <input type="checkbox" id="{FieldId}-2" name="{Name}" value="{Value2}">
    <label for="{FieldId}-2">{Option 2 Text}</label>
    </div>
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Select multiple options (if applicable).
  </div>
</div>
```

**Voorbeeld-CSS-kiezers voor groepen keuzerondjes en selectievakjes**

* Doelstelling voor de buitenomsluitend omsluitend kader: deze kiezers richten zich op de buitenste containers van groepen keuzerondjes en selectievakjes, zodat u algemene stijlen kunt toepassen op de volledige groepsstructuur. Dit is handig voor het instellen van spatiëring, uitlijning of andere aan de layout gerelateerde eigenschappen.


  ```CSS
     /* Targets all radio group wrappers */
  .form-radio-group-wrapper {
    margin-bottom: 20px; /* Adds space between radio groups */
  }
  
  /* Targets all checkbox group wrappers */
  .form-checkbox-group-wrapper {
    margin-bottom: 20px; /* Adds space between checkbox groups */
  }
  ```


* Doelgroeplabels: deze kiezer richt zich op de `.field-label` element binnen zowel keuzerondjes als groepslappen voor selectievakjes. Hierdoor kunt u de labels specifiek voor deze groepen opmaken, waardoor deze beter opvallen.

  ```CSS
  .form-radio-group-wrapper .field-label,
  .form-checkbox-group-wrapper .field-label {
   font-weight: bold; /* Makes the group label bold */
  }
  ```



* Afzonderlijke invoer en labels als doel instellen: deze kiezers bieden meer korrelige controle over afzonderlijke keuzerondjes, selectievakjes en de bijbehorende labels. U kunt deze stijlen gebruiken om het formaat, de spatiëring of de verschillende visuele stijlen aan te passen.

  ```CSS
  /* Styling radio buttons */
  .form-radio-group-wrapper input[type="radio"] {
    margin-right: 5px; /* Adds space between the input and its   label */
  } 
  
  /* Styling radio button labels */
  .form-radio-group-wrapper label {
    font-size: 15px; /* Changes the label font size */
  }
  
  /* Styling checkboxes */
  .form-checkbox-group-wrapper input[type="checkbox"] {
    margin-right: 5px;  /* Adds space between the input and its  label */ 
  }
  
  /* Styling checkbox labels */
  .form-checkbox-group-wrapper label {
    font-size: 15px; /* Changes the label font size */
  }
  ```




* De weergave van keuzerondjes en selectievakjes aanpassen: hiermee wordt de standaardinvoer verborgen en wordt :before and :after pseudo-elementen gebruikt om aangepaste visuele elementen te maken die de weergave wijzigen op basis van de status &#39;checked&#39;.

  ```CSS
  /* Hide the default radio button or checkbox */
  .form-radio-group-wrapper input[type="radio"],
  .form-checkbox-group-wrapper input[type="checkbox"] {
    opacity: 0; 
    position: absolute; 
  }
  
  /* Create a custom radio button */
  .form-radio-group-wrapper input[type="radio"] + label::before { 
    content: "";
    display: inline-block;
    width: 16px; 
    height: 16px; 
    border: 2px solid #ccc; 
    border-radius: 50%;
    margin-right: 5px;
  }
  
  .form-radio-group-wrapper input[type="radio"]:checked +  label::before {
    background-color: #007bff; 
  }
  
  /* Create a custom checkbox */
  /* Similar styling as above, with adjustments for a square shape  */
  ```


## Stijlcomponenten

U kunt ook formuliervelden opmaken op basis van het specifieke type of de afzonderlijke namen. Hierdoor kunt u de weergave van het formulier korter beheren en aanpassen.

### Stijlen op basis van veldtype

Met CSS-kiezers kunt u specifieke veldtypen als doel instellen en stijlen consistent toepassen.

**Voorbeeld van HTML-structuur**

```HTML
<div class="form-text-wrapper form-name field-wrapper" data-required="true">
  <label for="name" class="field-label">Name</label>
  <input type="text" placeholder="Enter your name" maxlength="50" id="name" name="name">
</div>

<div class="form-number-wrapper form-age field-wrapper" data-required="true">
  <label for="age" class="field-label">Age</label>
  <input type="number" placeholder="Enter your age" id="age" name="age">
</div>

<div class="form-email-wrapper form-email field-wrapper" data-required="true">
  <label for="email" class="field-label">Email Address</label>
  <input type="email" placeholder="Enter your email" id="email" name="email">
</div>
```

* Elk veld wordt opgenomen in een `div` element met verschillende klassen:
   * `form-{Type}-wrapper`: Hiermee wordt het type veld aangegeven. Bijvoorbeeld: `form-text-wrapper`, `form-number-wrapper`, `form-email-wrapper`.
   * `form-{Name}`: Identificeert het veld met de naam. Bijvoorbeeld `form-name`, `form-age`, `form-email`.
   * `field-wrapper`: Een generieke klasse voor alle veldwrappers.
* De `data-required` geeft aan of het veld verplicht of optioneel is.
* Elk veld heeft een overeenkomstig label, invoerelement en mogelijke aanvullende elementen, zoals plaatsaanduidingen en beschrijvingen.

**Voorbeeld-CSS-kiezers**

```CSS
/* Target all text input fields */
.form-text-wrapper input {
  /* Add your styles here */
}

/* Target all number input fields */
.form-number-wrapper input {
  /* Add your styles here */
  letter-spacing: 2px; /* Example for adding letter spacing to all number fields */
}
```

### Stijlen op basis van veldnaam

U kunt afzonderlijke velden ook op naam als doel instellen om unieke stijlen toe te passen.

**Voorbeeld van HTML-structuur**

```HTML
<div class="form-number-wrapper form-otp field-wrapper" data-required="true">
  <label for="otp" class="field-label">OTP</label>
  <input type="number" placeholder="Enter your OTP" maxlength="6" id="otp" name="otp">
</div>
```

**Voorbeeld-CSS-kiezer**

```CSS
.form-otp input {
   letter-spacing: 2px
}
```

Deze CSS richt zich op alle inputelementen die binnen een element worden gevestigd dat de klasse heeft `form-otp`. De HTML-structuur van uw formulier volgt de conventies van het formulierblok. Dit houdt in dat er een container is gemarkeerd met de klasse &quot;form-otp&quot; die het veld bevat met de naam &quot;otp&quot;.


