---
title: Thema en stijlen aanpassen voor Edge Delivery Services for AEM Forms
description: Thema en stijlen aanpassen voor Edge Delivery Services for AEM Forms
feature: Edge Delivery Services
exl-id: c214711c-979b-4833-9541-8e35b2aa8e09
role: Admin, Architect, Developer
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '1901'
ht-degree: 0%

---


# Het uiterlijk van uw formulieren aanpassen

Forms is van cruciaal belang voor gebruikersinteractie op websites, zodat deze gegevens kunnen invoeren. Met CSS (Cascading Style Sheets) kunt u formuliervelden opmaken, de visuele presentatie van formulieren verbeteren en de gebruikerservaring verbeteren.

Het Adaptive Forms Block produceert een consistente structuur voor alle formuliervelden. Dankzij deze consistente structuur is het eenvoudiger om CSS-kiezers te ontwikkelen voor het selecteren en opmaken van formuliervelden op basis van veldtype en veldnamen.

In dit document wordt de HTML-structuur voor verschillende formuliercomponenten beschreven en krijgt u inzicht in de manier waarop u CSS-kiezers voor verschillende formuliervelden kunt maken om formuliervelden van een adaptief Forms-blok op te maken.

Aan het einde van het artikel zult u:

- Begrijpen wat de structuur is van het standaard CSS-bestand dat is opgenomen in Adaptive Forms Block
- Inzicht in de HTML-structuur van formuliercomponenten die worden geleverd door het Adaptief Forms-blok, inclusief algemene componenten en specifieke componenten zoals dropdowns, radiogroepen en selectievakjesgroepen
- Leer hoe u formuliervelden kunt opmaken op basis van veldtype- en veldnamen met CSS-kiezers, zodat u consistent of uniek kunt opmaken op basis van vereisten


## Werken met formulierveldtypen

Alvorens in het stileren te duiken, herzien de gemeenschappelijke vorm [ gebiedstypes ](/help/edge/docs/forms/form-components.md) die door het AanpassingsBlok van Forms worden gesteund:

- Invoervelden: dit zijn tekstinvoer, e-mailinvoer, wachtwoordinvoer en meer
- Selectievakjesgroepen: gebruikt voor het selecteren van meerdere opties
- Keuzerondjes: wordt gebruikt voor het selecteren van slechts één optie in een groep
- Vervolgkeuzelijsten: ook wel selectiekaders genoemd, die worden gebruikt voor het selecteren van een optie in een lijst
- Deelvensters/containers: gebruikt om gerelateerde formulierelementen te groeperen

## Basisbeginselen voor stijlen

Het begrip van [ fundamentele CSS concepten ](https://www.w3schools.com/css/css_intro.asp) is essentieel alvorens specifieke vormgebieden te stileren:

- [ Kiezers ](https://www.w3schools.com/css/css_selectors.asp): CSS de Kiezers staan u toe om specifieke elementen van HTML voor het stileren te richten. U kunt elementkiezers, klassekiezers of id-kiezers gebruiken
- [ Eigenschappen ](https://www.w3schools.com/css/css_syntax.asp): CSS de eigenschappen bepalen de visuele verschijning van elementen. Veelvoorkomende eigenschappen voor het opmaken van formuliervelden zijn kleur, achtergrondkleur, rand, opvulling, marge en meer
- [ Model van de Doos ](https://www.w3schools.com/css/css_boxmodel.asp): Het CSS kadermodel beschrijft de structuur van de elementen van HTML als inhoudsgebied dat door het opvullen, grenzen, en marges wordt omringd
- Flexbox/Net: CSS [ Flexbox ](https://www.w3schools.com/css/css3_flexbox.asp) en [ de lay-outs van het Net ](https://www.w3schools.com/css/css_grid.asp) zijn krachtige hulpmiddelen om ontvankelijke en flexibele ontwerpen te creëren

## Een formulier opmaken voor Adaptief Forms-blok

Het Adaptive Forms Block biedt een gestandaardiseerde HTML-structuur waarmee het selecteren en opmaken van formulieronderdelen wordt vereenvoudigd:

- **Update standaardstijlen**: U kunt de standaardstijlen van een vorm wijzigen door het `/blocks/form/form.css` dossier uit te geven. Dit bestand biedt uitgebreide opmaak voor een formulier, met ondersteuning voor uit meerdere stappen bestaande wizardformulieren. Het benadrukt het gebruiken van douaneCSS variabelen voor gemakkelijke aanpassing, onderhoud, en het eenvormige formatteren over vormen. Voor instructies bij het toevoegen van het AanpassingsBlok van Forms aan uw project, verwijs naar [ creeer een vorm ](/help/edge/docs/forms/create-forms.md).

- **Aanpassing**: Gebruik het gebrek `forms.css` als basis en pas het aan om de blik en het gevoel van uw vormcomponenten te wijzigen, die hen visueel aantrekkelijk en gebruikersvriendelijk maken. De bestandsstructuur stimuleert de organisatie en handhaaft stijlen voor formulieren, waardoor consistente ontwerpen op uw website worden bevorderd.

## Indeling van de structuur forms.css

- **Globale variabelen:** die op het `:root` niveau wordt bepaald, slaan deze variabelen (`--variable-name`) waarden op die door het stijlblad voor consistentie en gemak van updates worden gebruikt. Deze variabelen definiëren kleuren, tekengrootten, opvulling en andere eigenschappen. U kunt uw eigen globale variabelen declareren of bestaande variabelen wijzigen om de stijl van het formulier te wijzigen.

- **Universele selecteurstijlen:** de `*` selecteur past elk element in de vorm aan, die ervoor zorgen de stijlen worden toegepast op alle componenten door gebrek, met inbegrip van het plaatsen van het `box-sizing` bezit aan `border-box`.

- **Formulier het stileren:** Deze sectie concentreert zich bij het stileren van vormcomponenten gebruikend selecteurs om specifieke elementen van HTML te richten. Hiermee worden stijlen gedefinieerd voor invoervelden, tekstgebieden, selectievakjes, keuzerondjes, bestandsinvoer, formulierlabels en beschrijvingen.

- **de stileren van de Tovenaar (als toepasselijk):** Deze sectie wordt gewijd aan het stileren van de tovenaar lay-out, een multi-step vorm waar elke stap tegelijkertijd wordt getoond. Hiermee worden stijlen gedefinieerd voor de tovenaarscontainer, veldsets, legenda&#39;s, navigatieknoppen en responsieve lay-outs.

- **vragen van Media:** Deze verstrekken stijlen voor verschillende het schermgrootte, die lay-out aanpassen en dienovereenkomstig stileren.

- **Diverse het stileren:** Deze sectie behandelt stijlen voor succes of foutenmeldingen, dossier uploadt gebieden, en andere elementen u in een vorm zou kunnen ontmoeten.


## Structuur van componenten

Het Adaptive Forms Block biedt een consistente HTML-structuur voor verschillende formulierelementen, waardoor de opmaak en het beheer worden vereenvoudigd. U kunt de componenten manipuleren met CSS voor opmaakdoeleinden.

### Algemene componenten (behalve dropdowns, radiegroepen, en checkbox groepen):

Alle formuliervelden, met uitzondering van vervolgkeuzelijsten, groepen keuzerondjes en groepen selectievakjes, hebben de volgende HTML-structuur:

+++ HTML-structuur van algemene componenten

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id="{FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be a minimum of 3 characters and a maximum of 10 characters.
   </div>
</div>
```

- Klassen: het div-element heeft verschillende klassen voor het aanwijzen van specifieke elementen en opmaak. U hebt de klassen `{Type}-wrapper` of `field-{Name}` nodig om een CSS-kiezer te ontwikkelen waarmee u een formulierveld kunt opmaken:
   - {Type}: identificeert de component op veldtype. Bijvoorbeeld tekst (tekstomloop), getal (nummeromloop), datum (datumomloop)
   - {Name}: identificeert de component op naam. De naam van het veld mag alleen alfanumerieke tekens bevatten; meerdere opeenvolgende streepjes in de naam worden vervangen door één streepje `(-)` en de begin- en eindstreep in een veldnaam worden verwijderd. Voornaam (field-first-name field-wrapper) bijvoorbeeld
   - {FieldId}: het is een unieke id voor het veld, die automatisch wordt gegenereerd
   - {Required}: Het is een Booleaanse waarde die aangeeft of het veld vereist is
- Label: het element `label` biedt beschrijvende tekst voor het veld en koppelt deze aan het invoerelement met het kenmerk `for` .
- Invoer: het element `input` definieert het type gegevens dat moet worden ingevoerd. Bijvoorbeeld tekst, nummer, e-mail
- Beschrijving (optioneel): De `div` with-klasse `field-description` biedt extra informatie of instructies voor de gebruiker

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

+++

+++ CSS-kiezer voor algemene componenten

```CSS
/* Target all input fields within any .{Type}-wrapper */
.{Type}-wrapper {
  /* Add your styles here */
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/* Target all input fields within any .{Type}-wrapper */
.{Type}-wrapper input {
  /* Add your styles here */
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/* Target any element with the class field-{Name} */
.field-{Name} {
  /* Add your styles here */
  /* This could be used for styles specific to all elements with field-{Name} class, not just inputs */
}
```

- `.{Type}-wrapper`: hiermee wordt het buitenste `div` -element opgegeven op basis van het veldtype. `.text-wrapper` richt zich bijvoorbeeld op alle tekstvelden
- `.field-{Name}`: hiermee selecteert u het element verder op basis van de specifieke veldnaam. `.field-first-name` verwijst bijvoorbeeld naar het tekstveld Voornaam. Terwijl deze selecteur voor het richten van elementen met de gebied {Name} klasse kan worden gebruikt, is het belangrijk om voorzichtig te zijn. In dit specifieke geval zou het niet nuttig zijn voor het opmaken van invoervelden omdat het niet alleen de invoer zelf, maar ook de label- en beschrijvingselementen betreft. Het is raadzaam specifiekere kiezers te gebruiken, zoals de kiezers die u hebt voor tekstinvoervelden (.text-wrapper input)

**CSS van het Voorbeeld Selectors voor Algemene Componenten**

```CSS
/* Target all text input fields */
.text-wrapper input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/* Target all fields with name first-name */
.field-first-name input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}
```

+++

### Onderdeeltje

Voor vervolgkeuzemenu&#39;s wordt het element `select` gebruikt in plaats van het element `input` :

+++ HTML-structuur van vervolgkeuzecomponent

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">Country</label>
   <select id="{FieldId}" name="{Name}"><option></option><option></option></select>
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Please select your country from the list.
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

+++

+++ CSS-kiezers voor vervolgkeuzecomponent

```CSS
/* Target the outer wrapper */
.drop-down-wrapper {
  /* Add your styles here */
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
}

/* Style the label */
.drop-down-wrapper .field-label {
  margin-bottom: 5px;
  font-weight: bold;
}

/* Style the dropdown itself */
.drop-down-wrapper select {
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
.drop-down-wrapper select::-ms-expand {
  display: none; /* Hide the default arrow for IE11 */
}

.drop-down-wrapper select::after {
  content: "\25BC";
}
```

+++

### Keuzerondjes

Keuzerondjes hebben een eigen HTML-structuur en CSS-structuur, net als vervolgkeuzecomponenten:

+++ HTML-structuur van groep keuzerondjes

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

#### Voorbeeld van HTML-structuur

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

+++

+++ CSS-kiezers voor keuzerondjes

- Doelstelling van de veldset

```CSS
  .radio-group-wrapper {
    border: 1px solid #ccc;
    padding: 10px;
  }
```

Deze kiezer richt zich op elk veld dat met de klasse Radio-group-wrapper is ingesteld. Dit is handig als u algemene stijlen wilt toepassen op de hele groep keuzerondjes.

- Labels voor keuzerondjes als doel instellen

```CSS
.radio-wrapper label {
    font-weight: normal;
    margin-right: 10px;
  }
```

- Alle keuzerondjes in een specifieke veldset op basis van de naam ervan als doel instellen

```CSS
.field-color .radio-wrapper label {
  /* Your styles here */
}
```

+++

### Selectievakjesgroepen

+++ HTML-structuur van Checkbox-groep

```HTML
<fieldset class="checkbox-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   <legend for="{FieldId}" class="field-label">....</legend>
   <% for each radio in Group %>
   <div class="radio-wrapper field-{Name}">
      <input type="checkbox" value="" id="{UniqueId}" data-field-type="checkbox-group" name="{FieldId}">
      <label for="{UniqueId}" class="field-label">...</label>
   </div>
   <% end for %>
</fieldset>
```

#### Voorbeeld van HTML-structuur

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

+++

+++ CSS-kiezers voor groepen selectievakjes

- Doelstelling voor de buitenomsluitend omsluitend kader: deze kiezers richten zich op de buitenste containers van groepen keuzerondjes en selectievakjes, zodat u algemene stijlen kunt toepassen op de volledige groepsstructuur. Dit is handig voor het instellen van spatiëring, uitlijning of andere aan de layout gerelateerde eigenschappen.


  ```CSS
     /* Targets radio group wrappers */
       .radio-group-wrapper {
       margin-bottom: 20px; /* Adds space between radio groups */  
     }
  
     /* Targets checkbox group wrappers */
     .checkbox-group-wrapper {
     margin-bottom: 20px; /* Adds space between checkbox groups */
     }
  ```


- Doelgroeplabels: deze kiezer richt zich op het `.field-label` -element binnen zowel de groepsomvattende items voor keuzerondjes als voor selectievakjes. Hierdoor kunt u de labels specifiek voor deze groepen opmaken, waardoor deze beter opvallen.

  ```CSS
   .radio-group-wrapper legend,
   .checkbox-group-wrapper legend {
     font-weight: bold; /* Makes the group label bold */
   }
  ```



- Afzonderlijke invoer en labels als doel instellen: deze kiezers bieden meer korrelige controle over afzonderlijke keuzerondjes, selectievakjes en de bijbehorende labels. U kunt deze stijlen gebruiken om het formaat, de spatiëring of de verschillende visuele stijlen aan te passen.

  ```CSS
  /* Styling radio buttons */
   .radio-group-wrapper input[type="radio"] {
     margin-right: 5px; /* Adds space between the input and its label */
   }
  
   /* Styling radio button labels */
   .radio-group-wrapper label {
     font-size: 15px; /* Changes the label font size */
   }
  
  /* Styling checkboxes */
   .checkbox-group-wrapper input[type="checkbox"] {
     margin-right: 5px; /* Adds space between the input and its label */
   }
  
   /* Styling checkbox labels */
   .checkbox-group-wrapper label {
     font-size: 15px; /* Changes the label font size */
   }
  ```




- De weergave van keuzerondjes en selectievakjes aanpassen: hiermee wordt de standaardinvoer verborgen en worden `:before` en `:after` pseudo-elementen gebruikt om aangepaste visuele elementen te maken die de weergave wijzigen op basis van de status &#39;checked&#39;.

  ```CSS
  /* Hide the default radio button or checkbox */
     .radio-group-wrapper input[type="radio"],
     .checkbox-group-wrapper input[type="checkbox"] {
       opacity: 0;
       position: absolute;
     }
  
     /* Create a custom radio button */
     .radio-group-wrapper input[type="radio"] + label::before {
       /* ... styles for custom radio button ... */
     }
  
     .radio-group-wrapper input[type="radio"]:checked + label::before {
       /* ... styles for checked radio button ... */
     }
  
     /* Create a custom checkbox */
     /* Similar styling as above, with adjustments for a square shape  */
     .checkbox-group-wrapper input[type="checkbox"] + label::before {
       /* ... styles for custom checkbox ... */
     }
  
     .checkbox-group-wrapper input[type="checkbox"]:checked + label::before {
       /* ... styles for checked checkbox ... */
     }
  ```

+++

### Deelvenster/Containercomponenten

+++ HTML-structuur van deelvenster-/containercomponenten

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

+++

+++ Voorbeeld-CSS-kiezers voor component Panel/Container

1. Doelstelling voor deelvenster:

```CSS
  /* Target the entire panel container */
  .panel-wrapper {
    /* Add your styles here (e.g., border, padding, background color) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
 }
```

- De kiezer van `.panel-wrapper` maakt alle elementen met de omloop van het klassepaneel, zodat alle deelvensters er consistent uitzien.

1. Richting geven aan de titel van het deelvenster:

```CSS
  /* Target the legend element (panel title) */
  .panel-wrapper legend {
    /* Add your styles here (e.g., font-weight, font-size) */
    font-weight: bold;
    font-size: 16px;
    padding-bottom: 5px;
    margin-bottom: 10px;
    border-bottom: 1px solid #ddd; /* Optional: create a separation line */
  }
```

- De kiezer van `.panel-wrapper legend` maakt een stijl van het legenda-element in het deelvenster, zodat de titel visueel opvalt.


1. Afzonderlijke velden aanwijzen in het deelvenster:

```CSS
/* Target all form field wrappers within a panel */
.panel-wrapper .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

- De `.panel-wrapper .{Type}-wrapper` -kiezer richt zich op alle omslagen met de `.{Type}-wrapper` -klasse in het deelvenster, zodat u de ruimte tussen formuliervelden kunt opmaken.

1. Specifieke velden instellen (optioneel):

```CSS
  /* Target the username field wrapper */
  .panel-wrapper .text-wrapper.field-username {
    /* Add your styles here (specific to username field) */
  }

  /* Target the password field wrapper */
  .panel-wrapper .password-wrapper.field-password {
    /* Add your styles here (specific to password field) */
  }
```

- Met deze optionele kiezers kunt u specifieke veldwrappers in het deelvenster gebruiken voor unieke opmaak, zoals het markeren van het veld gebruikersnaam.

+++

### Herhalbaar deelvenster

+++ HTML-structuur van een herhalbaar deelvenster

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

+++

+++ CSS-kiezers voor een herhaalbaar deelvenster

- Alle herhalende deelvensters als doel instellen:

```CSS
  /* Target all panels with the repeatable attribute */
  .panel-wrapper[data-repeatable="true"] {
    /* Add your styles here (e.g., border, margin) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
  }
```

De kiezer maakt stijlen van alle deelvensters die kunnen worden herhaald, zodat de vormgeving consistent blijft.


- Afzonderlijke velden in een deelvenster aanwijzen:

```CSS
/* Target all form field wrappers within a repeatable panel */
.panel-wrapper[data-repeatable="true"] .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

Met deze kiezer worden alle veldomlooptekens binnen een herhaalbaar deelvenster geplaatst, waarbij een consistente afstand tussen velden behouden blijft.

- Specifieke velden activeren (binnen een deelvenster):

```CSS
/* Target the name field wrapper within the first panel */
.panel-wrapper[data-repeatable="true"][data-index="0"] .text-wrapper.field-name {
  /* Add your styles here (specific to first name field) */
}

/* Target all
```

+++

### Bestandsbijlage

+++ HTML-structuur voor bestandsbijlage

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

+++

+++ CSS-kiezers voor de component Bestandsbijlage

- De volledige component Bestandsbijlage als doel instellen:

```CSS
/* Target the entire file attachment component */
.file-wrapper {
  /* Add your styles here (e.g., border, padding) */
  border: 1px solid #ccc;
  padding: 15px;
  border-radius: 4px;
  margin-bottom: 20px;
}
```

Met deze kiezer wordt de gehele bestandsbijlage geschaald, inclusief de legenda, het sleepgebied, het invoerveld en de lijst.

- Specifieke elementen:

```CSS
/* Target the drag and drop area */
.file-wrapper .file-drag-area {
  /* Add your styles here (e.g., background color, border) */
  background-color: #f0f0f0;
  border: 1px dashed #ddd;
  padding: 10px;
  text-align: center;
}

/* Target the file input element */
.file-wrapper input[type="file"] {
  /* Add your styles here (e.g., hide the default input) */
  display: none;
}

/* Target individual file descriptions within the list (populated dynamically) */
.file-wrapper .files-list .file-description {
  /* Add your styles here (e.g., margin, display) */
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
}

/* Target the file name within the description */
.file-wrapper .files-list .file-description .file-description-name {
  /* Add your styles here (e.g., font-weight) */
  font-weight: bold;
}

/* Target the file size within the description */
.file-wrapper .files-list .file-description .file-description-size {
  /* Add your styles here (e.g., font-size) */
  font-size: 0.8em;
}

/* Target the remove button within the description */
.file-wrapper .files-list .file-description .file-description-remove {
  /* Add your styles here (e.g., background color, hover effect) */
  background-color: transparent;
  border: none;
  cursor: pointer;
}
```

Met deze kiezers kunt u verschillende onderdelen van de bestandsbijlage afzonderlijk opmaken. U kunt de stijlen aanpassen aan uw ontwerpvoorkeuren.

+++


## Stijlcomponenten

U kunt formuliervelden opmaken op basis van het specifieke type (`{Type}-wrapper`) of de afzonderlijke namen (`field-{Name}`). Hierdoor kunt u de weergave van het formulier korter beheren en aanpassen.

### Stijlen op basis van veldtype

U kunt CSS-kiezers gebruiken om specifieke veldtypen als doel in te stellen en stijlen consistent toe te passen.

+++ HTML-structuur

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


+++


+++ Voorbeeld-CSS-kiezers

```CSS
/* Target all text input fields */
.text-wrapper input {
  /* Add your styles here */
}

/* Target all number input fields */
.number-wrapper input {
  /* Add your styles here */
  letter-spacing: 2px; /* Example for adding letter spacing to all number fields */
}
```

+++

### Stijlen op basis van veldnaam

U kunt afzonderlijke velden ook op naam als doel instellen om unieke stijlen toe te passen.

+++ HTML-structuur

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

+++

+++ Voorbeeld-CSS-kiezer

```CSS
.field-otp input {
   letter-spacing: 2px
}
```



Deze CSS richt zich op alle inputelementen die binnen een element worden gevestigd dat de klasse `field-otp` heeft. De HTML-structuur van uw formulier volgt de conventies van het Adaptive Forms Block. Dit houdt in dat er een container is gemarkeerd met de klasse &quot;field-otp&quot; die het veld bevat met de naam &quot;otp&quot;.

+++

