---
title: Thema en stijl aanpassen voor een Edge Delivery Services for AEM Forms
description: Pas het thema en de stijl voor AEM Forms die via Edge Delivery Services worden geleverd, effectief aan en zorg voor een consistente en merkbare gebruikerservaring.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: ac780399-34fe-457d-aaf4-b675656c024d
source-git-commit: 9127c58a72dc4942312907f9e8f0cdcc8de9aa4b
workflow-type: tm+mt
source-wordcount: '1876'
ht-degree: 0%

---

# Het uiterlijk van uw formulieren aanpassen

<span class="preview"> Deze functie is beschikbaar via het programma voor vroege toegang. Om toegang te verzoeken, verzend een e-mail met uw GitHub organisatienaam en bewaarplaatsnaam van uw officieel adres aan <a href="mailto:aem-forms-ea@adobe.com"> aem-forms-ea@adobe.com </a>. Bijvoorbeeld, als de bewaarplaats URL https://github.com/adobe/abc is, is de organisatienaam adobe en de bewaarplaatsnaam abc.</span>


Forms is van cruciaal belang voor gebruikersinteractie op websites, zodat deze gegevens kunnen invoeren. Met CSS (Cascading Style Sheets) kunt u velden van een formulier opmaken, de visuele presentatie van formulieren verbeteren en de gebruikerservaring verbeteren.

Het Adaptive Forms Block produceert een consistente structuur voor alle formuliervelden. De consistente structuur maakt het gemakkelijker om CSS-kiezers te ontwikkelen om formuliervelden te selecteren en op te maken op basis van veldtype- en veldnamen.

In dit document wordt de HTML-structuur voor verschillende formuliercomponenten beschreven. Op deze manier krijgt u inzicht in de manier waarop u CSS-kiezers voor verschillende formuliervelden kunt maken om formuliervelden van een adaptief Forms-blok op te maken.

Aan het einde van het artikel:

* U krijgt inzicht in de structuur van het standaard CSS-bestand dat wordt opgenomen in Adaptive Forms Block.
* U maakt inzicht in de HTML-structuur van de formuliercomponenten die worden geleverd door het Adaptief Forms-blok, inclusief algemene componenten en specifieke componenten zoals downloads, groepen keuzerondjes en groepen selectievakjes.
* U leert hoe u formuliervelden kunt opmaken op basis van veldtype- en veldnamen met CSS-kiezers, zodat u consistent of uniek kunt opmaken op basis van vereisten.

## Werken met formulierveldtypen

Alvorens in het stileren te duiken, herzien de gemeenschappelijke vorm [ gebiedstypes ](/help/edge/docs/forms/universal-editor/create-custom-component.md#supported-fieldtypes) die door het AanpassingsBlok van Forms worden gesteund:

* Invoervelden: dit zijn tekstinvoer, e-mailinvoer, wachtwoordinvoer en meer.
* Selectievakjesgroepen: wordt gebruikt voor het selecteren van meerdere opties.
* Keuzerondjes: wordt gebruikt voor het selecteren van slechts één optie in een groep.
* Vervolgkeuzelijsten: ook wel selectiekaders genoemd. Deze worden gebruikt voor het selecteren van een optie in een lijst.
* Deelvensters/containers: gebruikt om gerelateerde formulierelementen samen te groeperen.

## Basisbeginselen voor stijlen

Het begrip van [ fundamentele CSS concepten ](https://www.w3schools.com/css/css_intro.asp) is essentieel alvorens specifieke vormgebieden te stileren:

* [ Kiezers ](https://www.w3schools.com/css/css_selectors.asp): CSS de Kiezers staan u toe om specifieke elementen van HTML voor het stileren te richten. U kunt elementkiezers, klassekiezers of id-kiezers gebruiken.
* [ Eigenschappen ](https://www.w3schools.com/css/css_syntax.asp): CSS de eigenschappen bepalen de visuele verschijning van elementen. Veelvoorkomende eigenschappen voor het opmaken van formuliervelden zijn kleur, achtergrondkleur, rand, opvulling, marge en meer.
* [ Model van de Doos ](https://www.w3schools.com/css/css_boxmodel.asp): Het CSS kadermodel beschrijft de structuur van de elementen van HTML als inhoudsgebied dat door het opvullen, grenzen, en marges wordt omringd.
* Flexbox/Net: CSS [ Flexbox ](https://www.w3schools.com/css/css3_flexbox.asp) en [ lay-outs van het Net ](https://www.w3schools.com/css/css_grid.asp) zijn krachtige hulpmiddelen om ontvankelijke en flexibele ontwerpen tot stand te brengen.


## Een formulier opmaken voor Adaptief Forms-blok

Het Adaptive Forms Block biedt een gestandaardiseerde HTML-structuur waarmee het selecteren en opmaken van formulieronderdelen wordt vereenvoudigd:

* **Update standaardstijlen**: U kunt de standaardstijlen van een vorm wijzigen door `/blocks/form/form.css file` uit te geven. Dit bestand biedt uitgebreide opmaak voor een formulier, met ondersteuning voor uit meerdere stappen bestaande wizardformulieren. Het benadrukt het gebruiken van douaneCSS variabelen voor gemakkelijke aanpassing, onderhoud, en het eenvormige formatteren over vormen.

* **CSS het Stijlen voor Forms**: Om ervoor te zorgen dat uw stijlen correct worden toegepast, verpak uw vorm-specifieke CSS binnen de `main .form form` selecteur. Zo voorkomt u dat er conflicten ontstaan met andere delen van de website en dat uw stijlen alleen zijn bedoeld voor de formulierelementen binnen het hoofdinhoudsgebied.
Voorbeeld:

  ```css
    main .form form input {
        /* Add styles specific to input fields inside the form */
    }
  
    main .form form button {
        /* Add styles specific to buttons inside the form */
    }
  
    main .form form label {
        /* Add styles specific to labels inside the form */
    }
  
## Componentstructuur

Het Adaptive Forms Block biedt een consistente HTML-structuur voor verschillende formulierelementen, waardoor de opmaak en het beheer worden vereenvoudigd. U kunt de componenten manipuleren met CSS voor opmaakdoeleinden.

### Algemene componenten (behalve dropdowns, radiegroepen, en checkbox groepen):

Alle formuliervelden, met uitzondering van vervolgkeuzelijsten, groepen keuzerondjes en groepen selectievakjes, hebben de volgende HTML-structuur:

+++ HTML-structuur van algemene componenten

```HTML

  <div class="{Type}-wrapper field-{Name}   field-wrapper" data-required={Required}>
     &lt;label for="{FieldId}" class="field-label">First   Name&lt;/label>
     &lt;input type="{Type}" placeholder="{Placeholder}"   maxlength="{Max}" id={FieldId}" name="{Name}"   aria-describedby="{FieldId}-description">
     <div class="field-description" aria-live="polite"  id="{FieldId}-description">
      Hint - First name should be minimum 3 characters  and a maximum of 10 characters.
     </div>
  </div>

```

* Klassen: het div-element heeft verschillende klassen voor het aanwijzen van specifieke elementen en opmaak. U hebt de klassen `{Type}-wrapper` of `field-{Name}` nodig om een CSS-kiezer te ontwikkelen waarmee u een formulierveld kunt opmaken:
* {Type}: identificeert de component op veldtype. Bijvoorbeeld tekst (tekstomloop), getal (nummeromloop), datum (datumomloop).
* {Name}: identificeert de component op naam. De naam van het veld mag alleen alfanumerieke tekens bevatten, de opeenvolgende streepjes in de naam worden vervangen door één streepje `(-)` en de begin- en eindstreepjes in een veldnaam worden verwijderd. Voornaam (veld-voornaam veld-wrapper).
* {FieldId}: het is een unieke id voor het veld, die automatisch wordt gegenereerd.
* {Required}: een Booleaanse waarde die aangeeft of het veld verplicht is.
* Label: het element `label` verschaft een beschrijvende tekst voor het veld en koppelt deze aan het invoerelement met behulp van het kenmerk `for` .
* Invoer: het element `input` definieert het type gegevens dat moet worden ingevoerd. Bijvoorbeeld tekst, nummer, e-mail.
* Beschrijving (optioneel): De `div` with class `field-description` biedt extra informatie of instructies voor de gebruiker.

**Voorbeeld van de Structuur van HTML**

```HTML

<div class="text-wrapper field-first-name field-wrapper" data-required="true">
  &lt;label for="firstName" class="field-label">First Name&lt;/label>
  &lt;input type="text" placeholder="Enter your first name" maxlength="50" id="firstName" name="firstName" aria-describedby="firstName-description">
  <div class="field-description" aria-live="polite" id="firstName-description">
    Please enter your legal first name.
  </div>
</div>

```

+++

+++ CSS-kiezer voor algemene componenten

```CSS

  
  /* Target all input fields within any .{Type}-wrapper  */
  main .form form .{Type}-wrapper  &lbrace;
    /* Add your styles here */
    border: 1px solid #ccc;
    padding: 8px;
    border-radius: 4px;
  &rbrace;
  
  /* Target all input fields within any .{Type}-wrapper  */
  main .form form .{Type}-wrapper input &lbrace;
    /* Add your styles here */
    border: 1px solid #ccc;
    padding: 8px;
    border-radius: 4px;
  &rbrace;
  
  /* Target any element with the class field-{Name}  */
  main .form form .field-{Name} &lbrace;
    /* Add your styles here */
    /* This could be used for styles specific to all elements with   field-{Name} class, not just inputs */
  &rbrace;
  
```
* `.{Type}-wrapper`: richt het buitenste `div` -element op basis van    het veldtype. `.text-wrapper` richt bijvoorbeeld alle tekst op    velden.
* `.field-{Name}`: hiermee selecteert u het element verder op basis van de specifieke veldnaam. `.field-first-name` verwijst bijvoorbeeld naar het tekstveld Voornaam. Terwijl deze selecteur voor het richten van elementen met de gebied {Name} klasse kan worden gebruikt, is het belangrijk om voorzichtig te zijn. In dit specifieke geval zou het niet nuttig zijn voor het opmaken van invoervelden omdat het niet alleen de invoer zelf, maar ook de label- en beschrijvingselementen betreft. Het is raadzaam specifiekere kiezers te gebruiken, zoals de kiezers die u hebt voor tekstinvoervelden (.text-wrapper input).

**CSS van het Voorbeeld Selectors voor Algemene Componenten**

```CSS

/*Target all text input fields */
main .form form .text-wrapper input &lbrace;
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
  color: red;
&rbrace;

/*Target all fields with name first-name*/
main .form form .field-first-name input &lbrace;
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
&rbrace;

```

+++

### Onderdeeltje

Voor vervolgkeuzemenu&#39;s wordt het element `select` gebruikt in plaats van het element `input` :

+++ HTML-structuur van vervolgkeuzecomponent

```HTML

<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   &lt;label for="{FieldId}" class="field-label">First Name&lt;/label>
   &lt;input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>

```

**de Structuur van HTML van het Voorbeeld**

```HTML

<div class="drop-down-wrapper field-country field-wrapper" data-required="true">
  &lt;label for="country" class="field-label">Country&lt;/label>
  &lt;select id="country" name="country">
    &lt;option value="">Select Country&lt;/option>
    &lt;option value="US">United States&lt;/option>
    &lt;option value="CA">Canada&lt;/option>
  &lt;/select>
  <div class="field-description" aria-live="polite" id="country-description">
    Please select your country of residence.
  </div>
</div>

```

+++

+++ CSS-kiezers voor vervolgkeuzecomponent

In de volgende CSS-code worden enkele voorbeelden van CSS-kiezers voor vervolgkeuzecomponenten weergegeven.

```CSS

/* Target the outer wrapper */
main .form form .drop-down-wrapper &lbrace;
  /* Add your styles here */
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
&rbrace;

/* Style the label */
main .form form .drop-down-wrapper .field-label &lbrace;
  margin-bottom: 5px;
  font-weight: bold;
&rbrace;

```
* Richt op Wrapper: De eerste selecteur (`.drop-down-wrapper`) richt het buitenomslagelement, die ervoor zorgt dat de stijlen op de volledige dropdown component van toepassing zijn.
* Flexbox Layout: in Flexbox worden het label, de vervolgkeuzelijst en de beschrijving verticaal gerangschikt voor een zuivere lay-out.
* Labelstijlen: het label wordt weergegeven met een grotere tekendikte en een kleine marge.
* Vervolgkeuzestijl: het element `select` ontvangt een rand, opvulling en afgeronde hoeken voor een gepolijst uiterlijk.
* Achtergrondkleur: er is een consistente achtergrondkleur ingesteld voor visuele harmonie.
* Pijl-aanpassing: optionele stijlen verbergen de standaardvervolgkeuzepijl en maken een aangepaste pijl met een Unicode-teken en -positie.

+++

---

### Keuzerondjes

Keuzerondjes hebben een eigen HTML-structuur en CSS-structuur, net als vervolgkeuzecomponenten:

+++ HTML-structuur van groep keuzerondjes

```HTML

&lt;fieldset class="radio-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   &lt;legend for="{FieldId}" class="field-label">....&lt;/legend>
   <% for each radio in Group %>
   <div class="radio-wrapper field-{Name}">
      &lt;input type="radio" value="" id="{UniqueId}" data-field-type="radio-group" name="{FieldId}">
      &lt;label for="{UniqueId}" class="field-label">...&lt;/label>
   </div>
   <% end for %>
&lt;/fieldset>

```

**de Structuur van HTML van het Voorbeeld**

```HTML

&lt;fieldset class="radio-group-wrapper field-color field-wrapper" id="color_preference" name="color_preference" data-required="true">
  &lt;legend for="color_preference" class="field-label">Favorite Color:&lt;/legend>
  <% for each radio in Group %>
    <div class="radio-wrapper field-color">
      &lt;input type="radio" value="red" id="color_red" data-field-type="radio-group" name="color_preference">
      &lt;label for="color_red" class="field-label">Red&lt;/label>
    </div>
    <div class="radio-wrapper field-color">
      &lt;input type="radio" value="green" id="color_green" data-field-type="radio-group" name="color_preference">
      &lt;label for="color_green" class="field-label">Green&lt;/label>
    </div>
    <div class="radio-wrapper field-color">
      &lt;input type="radio" value="blue" id="color_blue" data-field-type="radio-group" name="color_preference">
      &lt;label for="color_blue" class="field-label">Blue&lt;/label>
    </div>
  <% end for %>
&lt;/fieldset>

```

+++

+++ CSS-kiezers voor keuzerondjes

* Doelstelling van de veldset

```CSS

  main .form form .radio-group-wrapper &lbrace;
    border: 1px solid #ccc;
    padding: 10px;
  &rbrace;

```
Deze kiezer richt zich op elk veld dat met de klasse Radio-group-wrapper is ingesteld. Dit is handig als u algemene stijlen wilt toepassen op de hele groep keuzerondjes.

* Labels voor keuzerondjes als doel instellen

```CSS

main .form form .radio-wrapper label &lbrace;
    font-weight: normal;
    margin-right: 10px;
  &rbrace;

```

* Alle keuzerondjes in een specifieke veldset op basis van de naam ervan als doel instellen

```CSS

main .form form .field-color .radio-wrapper label &lbrace;
  /* Your styles here */
&rbrace;

```

+++

### Selectievakjesgroepen

+++ HTML-structuur van Checkbox-groep

```HTML

&lt;fieldset class="checkbox-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   &lt;legend for="{FieldId}" class="field-label">....&lt;/legend>
   <% for each radio in Group %>
   <div class="radio-wrapper field-{Name}">
      &lt;input type="checkbox" value="" id="{UniqueId}" data-field-type="checkbox-group" name="{FieldId}">
      &lt;label for="{UniqueId}" class="field-label">...&lt;/label>
   </div>
   <% end for %>
&lt;/fieldset>

```

**de Structuur van HTML van het Voorbeeld**

```HTML

&lt;fieldset class="checkbox-group-wrapper field-topping field-wrapper" id="topping_preference" name="topping_preference" data-required="false">
  &lt;legend for="topping_preference" class="field-label">Pizza Toppings:&lt;/legend>
  <div class="checkbox-wrapper field-topping">
    &lt;input type="checkbox" value="pepperoni" id="topping_pepperoni" data-field-type="checkbox-group" name="topping_preference">
    &lt;label for="topping_pepperoni" class="field-label">Pepperoni&lt;/label>
  </div>
  <div class="checkbox-wrapper field-topping">
    &lt;input type="checkbox" value="mushrooms" id="topping_mushrooms" data-field-type="checkbox-group" name="topping_preference">
    &lt;label for="topping_mushrooms" class="field-label">Mushrooms&lt;/label>
  </div>
  <div class="checkbox-wrapper field-topping">
    &lt;input type="checkbox" value="onions" id="topping_onions" data-field-type="checkbox-group" name="topping_preference">
    &lt;label for="topping_onions" class="field-label">Onions&lt;/label>
  </div>
&lt;/fieldset>

```

+++

+++ CSS-kiezers voor groepen selectievakjes

* De buitenomloop instellen: deze kiezers richten zich op de buitenste containers van groepen keuzerondjes en selectievakjes, zodat u algemene stijlen kunt toepassen op de volledige groepsstructuur. Dit is handig voor het instellen van spatiëring, uitlijning of andere aan de layout gerelateerde eigenschappen.

```CSS

  
  /* Targets radio group wrappers */
  main .form form .radio-group-wrapper &lbrace;
    margin-bottom: 20px; /* Adds space between radio groups */  
  &rbrace;

  /* Targets checkbox group wrappers */
  main .form form .checkbox-group-wrapper &lbrace;
    margin-bottom: 20px; /* Adds space between checkbox groups */
  &rbrace;

```

* Doelgroeplabels: deze kiezer richt zich op het `.field-label` -element binnen zowel de groepsomvattende items voor keuzerondjes als voor selectievakjes. Hierdoor kunt u de labels specifiek voor deze groepen opmaken, waardoor deze beter opvallen.

```CSS

main .form form .radio-group-wrapper legend,
main .form form .checkbox-group-wrapper legend &lbrace;
  font-weight: bold; /* Makes the group label bold */
&rbrace;

```

* Afzonderlijke invoer en labels als doel instellen: deze kiezers bieden meer korrelige controle over afzonderlijke keuzerondjes, selectievakjes en de bijbehorende labels. U kunt deze stijlen gebruiken om het formaat, de spatiëring of de verschillende visuele stijlen aan te passen.

```CSS

/* Styling radio buttons */
main .form form .radio-group-wrapper input[type="radio"] &lbrace;
  margin-right: 5px; /* Adds space between the input and its label */
&rbrace;

/* Styling radio button labels */
main .form form .radio-group-wrapper label &lbrace;
  font-size: 15px; /* Changes the label font size */
&rbrace;

/* Styling checkboxes */
main .form form .checkbox-group-wrapper input[type="checkbox"] &lbrace;
  margin-right: 5px; /* Adds space between the input and its label */
&rbrace;

/* Styling checkbox labels */
main .form form .checkbox-group-wrapper label &lbrace;
  font-size: 15px; /* Changes the label font size */
&rbrace;

```

* De weergave van keuzerondjes en selectievakjes aanpassen: hiermee wordt de standaardinvoer verborgen en worden `:before` en `:after` pseudo-elementen gebruikt om aangepaste visuele elementen te maken die de weergave wijzigen op basis van de status &#39;checked&#39;.

```CSS

/* Hide the default radio button or checkbox */
main .form form .radio-group-wrapper input[type="radio"],
main .form form .checkbox-group-wrapper input[type="checkbox"] &lbrace;
  opacity: 0;
  position: absolute;
&rbrace;

/* Create a custom radio button */
main .form form .radio-group-wrapper input[type="radio"] + label::before &lbrace;
  /* ... styles for custom radio button ... */
&rbrace;

main .form form .radio-group-wrapper input[type="radio"]:checked + label::before &lbrace;
  /* ... styles for checked radio button ... */
&rbrace;

/* Create a custom checkbox */
main .form form .checkbox-group-wrapper input[type="checkbox"] + label::before &lbrace;
  /* ... styles for custom checkbox ... */
&rbrace;

main .form form .checkbox-group-wrapper input[type="checkbox"]:checked + label::before &lbrace;
  /* ... styles for checked checkbox ... */
&rbrace;

```

+++

### Deelvenster/Containercomponenten

+++ HTML-structuur van deelvenster-/containercomponenten

```HTML

&lt;fieldset class="panel-wrapper field-{PanelName} field-wrapper">
  &lt;legend for="{id}" class="field-label" data-visible="false">bannerComponent&lt;/legend>
  <div class="{Type}-wrapper field-{Name} field-wrapper">
    &lt;label for="{FieldId}" class="field-label">First Name&lt;/label>
    &lt;input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}">
    <div class="field-description" aria-live="polite" id="{FieldId}-description">
      Hint - First name should be minimum 3 characters and a maximum of 10 characters.
    </div>
  </div>
&lt;/fieldset>

```

**de Structuur van HTML van het Voorbeeld**

```HTML

&lt;fieldset class="panel-wrapper field-login field-wrapper">
  &lt;legend for="login" class="field-label" data-visible="false">Login Information&lt;/legend>
  <div class="text-wrapper field-username field-wrapper">
    &lt;label for="username" class="field-label">Username&lt;/label>
    &lt;input type="text" placeholder="Enter your username" maxlength="50" id="username" name="username">
    <div class="field-description" aria-live="polite" id="username-description">
      Please enter your username or email address.
    </div>
  </div>
  <div class="password-wrapper field-password field-wrapper">
    &lt;label for="password" class="field-label">Password&lt;/label>
    &lt;input type="password" placeholder="Enter your password" maxlength="20" id="password" name="password">
    <div class="field-description" aria-live="polite" id="password-description">
      Your password must be at least 8 characters long.
    </div>
  </div>
&lt;/fieldset>

```

* Het veldsetelement fungeert als de deelvenstercontainer met de klassepaneel-wrapper en aanvullende klassen voor opmaak op basis van de naam van het deelvenster (veldaanmelding).
* Het element legenda (<legend>) fungeert als de titel van het deelvenster met de tekst &quot;Aanmeldingsgegevens&quot; en de veldlabel voor de klasse. Het attribuut data-visible=&quot;false&quot; kan met JavaScript worden gebruikt om de zichtbaarheid van de titel te regelen.
* Binnen de veldset, meerdere.{Type} -wrapper-elementen (.text-wrapper en .password-wrapper in dit geval) vertegenwoordigen afzonderlijke formuliervelden in het deelvenster.
* Elke omslag bevat een etiket, een inputgebied, en een beschrijving, gelijkend op de vorige voorbeelden.

+++

+++ Voorbeeld-CSS-kiezers voor component Panel/Container

1. Doelstelling voor deelvenster:

```CSS

  /* Target the entire panel container */
  main .form form .panel-wrapper &lbrace;
    /* Add your styles here (e.g., border, padding, background color) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
 &rbrace;

```

* De kiezer van `.panel-wrapper` maakt alle elementen met de omloop van het klassepaneel, zodat alle deelvensters er consistent uitzien.

1. Richting geven aan de titel van het deelvenster:

```CSS

  /* Target the legend element (panel title) */
  .panel-wrapper legend &lbrace;
    /* Add your styles here (e.g., font-weight, font-size) */
    font-weight: bold;
    font-size: 16px;
    padding-bottom: 5px;
    margin-bottom: 10px;
    border-bottom: 1px solid #ddd; /* Optional: create a separation line */
  &rbrace;

```

* De kiezer van `.panel-wrapper legend` maakt een stijl van het legenda-element in het deelvenster, zodat de titel visueel opvalt.


1. Afzonderlijke velden aanwijzen in het deelvenster:

```CSS

/* Target all form field wrappers within a panel */
main .form form .panel-wrapper .{Type}-wrapper &lbrace;
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
&rbrace;

```

* De `.panel-wrapper .{Type}-wrapper` -kiezer richt zich op alle omslagen met de `.{Type}-wrapper` -klasse in het deelvenster, zodat u de ruimte tussen formuliervelden kunt opmaken.

1. Specifieke velden instellen (optioneel):

```CSS

  /* Target the username field wrapper */
  main .form form .panel-wrapper .text-wrapper.field-username &lbrace;
    /* Add your styles here (specific to username field) */
  &rbrace;

  /* Target the password field wrapper */
  main .form form .panel-wrapper .password-wrapper.field-password &lbrace;
    /* Add your styles here (specific to password field) */
  &rbrace;

```

* Met deze optionele kiezers kunt u specifieke veldwrappers in het deelvenster gebruiken voor unieke opmaak, zoals het markeren van het veld gebruikersnaam.

+++

### Herhalbaar deelvenster

+++ HTML-structuur van een herhalbaar deelvenster

```HTML

&lt;fieldset class="panel-wrapper field-{PanelName} field-wrapper">
  &lt;legend for="{id}" class="field-label" data-visible="false">bannerComponent&lt;/legend>
  <div class="{Type}-wrapper field-{Name} field-wrapper">
    &lt;label for="{FieldId}" class="field-label">First Name&lt;/label>
    &lt;input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}">
    <div class="field-description" aria-live="polite" id="{FieldId}-description">
      Hint - First name should be minimum 3 characters and a maximum of 10 characters.
    </div>
&lt;/fieldset>

```

**de Structuur van HTML van het Voorbeeld**

```HTML

&lt;fieldset class="panel-wrapper field-contact field-wrapper" data-repeatable="true">
  &lt;legend for="contact-1" class="field-label" data-visible="false">Contact Information&lt;/legend>
  <div class="text-wrapper field-name field-wrapper">
    &lt;label for="name-1" class="field-label">Name&lt;/label>
    &lt;input type="text" placeholder="Enter your name" maxlength="50" id="name-1" name="contacts[0].name">
    <div class="field-description" aria-live="polite" id="name-1-description">
      Please enter your full name.
    </div>
  </div>
  <div class="email-wrapper field-email field-wrapper">
    &lt;label for="email-1" class="field-label">Email&lt;/label>
    &lt;input type="email" placeholder="Enter your email address" maxlength="100" id="email-1" name="contacts[0].email">
    <div class="field-description" aria-live="polite" id="email-1-description">
      Please enter a valid email address.
    </div>
  </div>
&lt;/fieldset>

&lt;fieldset class="panel-wrapper field-contact field-wrapper" data-repeatable="true">
  &lt;legend for="contact-2" class="field-label" data-visible="false">Contact Information&lt;/legend>
  <div class="text-wrapper field-name field-wrapper">
    &lt;label for="name-2" class="field-label">Name&lt;/label>
    &lt;input type="text" placeholder="Enter your name" maxlength="50" id="name-2" name="contacts[1].name">
    <div class="field-description" aria-live="polite" id="name-2-description">
      Please enter your full name.
    </div>
  </div>
  <div class="email-wrapper field-email field-wrapper">
    &lt;label for="email-2" class="field-label">Email&lt;/label>
    &lt;input type="email" placeholder="Enter your email address" maxlength="100" id="email-2" name="contacts[1].email">
    <div class="field-description" aria-live="polite" id="email-2-description">
      Please enter a valid email address.
    </div>
  </div>
&lt;/fieldset>

```

Elk deelvenster heeft dezelfde structuur als het voorbeeld van één deelvenster, met extra kenmerken:

* data-herhaalable=&quot;true&quot;: dit kenmerk geeft aan dat het deelvenster dynamisch kan worden herhaald met JavaScript of een framework.

* Unieke IDs en namen: Elk element binnen het paneel heeft een unieke identiteitskaart (bijvoorbeeld, naam-1, e-mail-1) en naamattributen die op de index van het paneel (bijvoorbeeld, name= &quot;contacten [ 0 ].name&quot;) worden gebaseerd. Op deze manier kunnen de gegevens correct worden verzameld wanneer meerdere deelvensters worden verzonden.

+++

+++ CSS-kiezers voor een herhaalbaar deelvenster

* Alle herhalende deelvensters als doel instellen:

```CSS

  /* Target all panels with the repeatable attribute */
 main .form form .panel-wrapper[data-repeatable="true"] &lbrace;
    /* Add your styles here (e.g., border, margin) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
  &rbrace;

```

De kiezer maakt stijlen van alle deelvensters die kunnen worden herhaald, zodat de vormgeving consistent blijft.


* Afzonderlijke velden in een deelvenster aanwijzen:

```CSS

/* Target all form field wrappers within a repeatable panel */
main .form form .panel-wrapper[data-repeatable="true"] .{Type}-wrapper &lbrace;
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
&rbrace;

```
Met deze kiezer worden alle veldomlooptekens binnen een herhaalbaar deelvenster geplaatst, waarbij een consistente afstand tussen velden behouden blijft.

* Specifieke velden activeren (binnen een deelvenster):

```CSS

/* Target the name field wrapper within the first panel */
main .form form .panel-wrapper[data-repeatable="true"][data-index="0"] .text-wrapper.field-name &lbrace;
  /* Add your styles here (specific to first name field) */
&rbrace;

/* Target all

```

+++

### Bestandsbijlage

+++ HTML-structuur voor bestandsbijlage

```HTML

<div class="file-wrapper field-{FileName} field-wrapper">
  &lt;legend for="{id}" class="field-label" data-visible="false"> File Attachment &lt;/legend>
  <div class="file-drag-area">
    <div class="file-dragIcon"></div>
    <div class="file-dragText">Drag and Drop To Upload</div>
    &lt;button class="file-attachButton" type="button">Attach&lt;/button>
    &lt;input type="file" accept="audio/*, video/*, image/*, text/*, application/pdf" id="{id}" name="{FileName}" autocomplete="off" multiple="" required="required">
  </div>
  <div class="files-list">
    <div data-index="0" class="file-description">
      <span class="file-description-name">ClaimForm.pdf</span>
      <span class="file-description-size">26 kb</span>
      &lt;button class="file-description-remove" type="button">&lt;/button>
    </div>
  </div>
</div>

```

**de Structuur van HTML van het Voorbeeld**


```HTML

<div class="file-wrapper field-claim_form field-wrapper">
  &lt;legend for="claim_form" class="field-label" data-visible="false">File Attachment&lt;/legend>
  <div class="file-drag-area">
    <div class="file-dragIcon"></div>
    <div class="file-dragText">Drag and Drop To Upload</div>
    &lt;button class="file-attachButton" type="button">Attach&lt;/button>
  </div>
  <input type="file" accept="audio/*, video/*, image/*, text/*, application/pdf" id="claim_form"
         name="claim_form" autocomplete="off" multiple="" required="required" data-max-file-size="2MB">
  <div class="files-list">
    </div>
</div>

```

* Het klassenkenmerk gebruikt de opgegeven naam voor de bestandsbijlage (claim_form).
* De id- en naamkenmerken van het invoerelement komen overeen met de naam van de bestandsbijlage (claim_form).
* De sectie voor de bestandenlijst is aanvankelijk leeg. Deze wordt dynamisch gevuld met JavaScript wanneer bestanden worden geüpload.

+++

+++ CSS-kiezers voor de component Bestandsbijlage

* De volledige component Bestandsbijlage als doel instellen:

```CSS

/* Target the entire file attachment component */
main .form form .file-wrapper &lbrace;
  /* Add your styles here (e.g., border, padding) */
  border: 1px solid #ccc;
  padding: 15px;
  border-radius: 4px;
  margin-bottom: 20px;
&rbrace;

```

Met deze kiezer wordt de gehele bestandsbijlage geschaald, inclusief de legenda, het sleepgebied, het invoerveld en de lijst.

* Specifieke elementen:

```CSS

/* Target the drag and drop area */
main .form form .file-wrapper .file-drag-area &lbrace;
  /* Add your styles here (e.g., background color, border) */
  background-color: #f0f0f0;
  border: 1px dashed #ddd;
  padding: 10px;
  text-align: center;
&rbrace;

/* Target the file input element */
main .form form .file-wrapper input[type="file"] &lbrace;
  /* Add your styles here (e.g., hide the default input) */
  display: none;
&rbrace;

/* Target individual file descriptions within the list (populated dynamically) */
main .form form .file-wrapper .files-list .file-description &lbrace;
  /* Add your styles here (e.g., margin, display) */
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
&rbrace;

/* Target the file name within the description */
main .form form .file-wrapper .files-list .file-description .file-description-name &lbrace;
  /* Add your styles here (e.g., font-weight) */
  font-weight: bold;
&rbrace;

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
   &lt;label for="{FieldId}" class="field-label">First Name&lt;/label>
   &lt;input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>

```

**de Structuur van HTML van het Voorbeeld**

```HTML

<div class="text-wrapper field-name field-wrapper" data-required="true">
  &lt;label for="name" class="field-label">Name&lt;/label>
  &lt;input type="text" placeholder="Enter your name" maxlength="50" id="name" name="name">
</div>

<div class="number-wrapper field-age field-wrapper" data-required="true">
  &lt;label for="age" class="field-label">Age&lt;/label>
  &lt;input type="number" placeholder="Enter your age" id="age" name="age">
</div>

<div class="email-wrapper field-email field-wrapper" data-required="true">
  &lt;label for="email" class="field-label">Email Address&lt;/label>
  &lt;input type="email" placeholder="Enter your email" id="email" name="email">
</div>

```

* Elk veld wordt opgenomen in een element `div` met verschillende klassen:
   * `{Type}-wrapper` - Hiermee wordt het type veld aangegeven. Bijvoorbeeld `form-text-wrapper` , `form-number-wrapper` , `form-email-wrapper` .
   * `field-{Name}` - Identificeert het veld met de naam. Bijvoorbeeld `form-name` , `form-age` , `form-email` .
   * `field-wrapper`: Een algemene klasse voor alle veldwrappers.
* Het kenmerk `data-required` geeft aan of het veld verplicht of optioneel is.
* Elk veld heeft een overeenkomstig label, invoerelement en mogelijke aanvullende elementen, zoals plaatsaanduidingen en beschrijvingen.


+++


+++ Voorbeeld-CSS-kiezers

```CSS

/* Target all text input fields */
main .form form .text-wrapper input &lbrace;
  /* Add your styles here */
&rbrace;

/* Target all number input fields */
main .form form .number-wrapper input &lbrace;
  /* Add your styles here */
  letter-spacing: 2px; /* Example for adding letter spacing to all number fields */
&rbrace;

```

+++

### Stijlen op basis van veldnaam

U kunt afzonderlijke velden ook op naam als doel instellen om unieke stijlen toe te passen.

+++ HTML-structuur

```HTML

<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   &lt;label for="{FieldId}" class="field-label">First Name&lt;/label>
   &lt;input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id="{FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Enter the 6 digit number sent to your mobile number.
   </div>
</div>

```

**de Structuur van HTML van het Voorbeeld**

```HTML

<div class="number-wrapper field-otp field-wrapper" data-required="true">
  &lt;label for="otp" class="field-label">OTP&lt;/label>
  &lt;input type="number" placeholder="Enter your OTP" maxlength="6" id="otp" name="otp" aria-describedby="otp-description">
  <div class="field-description" aria-live="polite" id="otp-description">
    Hint - Enter the 6 digit number sent to your mobile number.
   </div>
</div>

```

+++

+++ Voorbeeld-CSS-kiezer

```CSS

main .form form .field-otp input &lbrace;
   letter-spacing: 2px
&rbrace;

```

Deze CSS richt zich op alle inputelementen die binnen een element worden gevestigd dat de klasse `field-otp` heeft. De HTML-structuur van uw formulier volgt de conventies van het Adaptive Forms Block. Dit houdt in dat er een container is gemarkeerd met de klasse &quot;field-otp&quot; die het veld bevat met de naam &quot;otp&quot;.

+++




## Zie ook

{{universal-editor-see-also}}
