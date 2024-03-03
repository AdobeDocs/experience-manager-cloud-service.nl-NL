---
title: Formuliercomponenten en -eigenschappen
description: Dit document biedt een overzicht van de formuliercomponenten en hun eigenschappen die beschikbaar zijn in AEM Forms Edge Delivery Service.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: fd2e5df72e965ea6f9ad09b37983f815954f915c
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 0%

---


# Formulieronderdelen en -eigenschappen: AEM Forms Edge Delivery-service

Met de AEM Forms Edge Delivery Service kunt u gebruikersvriendelijke en interactieve formulieren maken met behulp van verschillende componenten. Deze componenten zijn geschikt voor verschillende soorten gegevensverzameling en kunnen eenvoudig aan uw specifieke behoeften worden aangepast.


![Een voorbeeldspreadsheet met enkele componenten en eigenschappen](/help/edge/assets/sample-form-in-spreadsheet.png)

Het adaptieve formulierblok genereert een [uniforme HTML-structuur](/help/edge/docs/forms/style-theme-forms.md) voor alle veldtypen en -containers (panelen) die de consistentie waarborgen. Deze consistente structuur maakt het eenvoudiger om [een formulier opmaken](/help/edge/docs/forms/style-theme-forms.md).

## Beschikbare componenten

Hier volgt een overzicht van de beschikbare componenten:

### Invoervelden

- Alle geldige HTML5 [invoertypen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types) en [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea). Bijvoorbeeld knop, selectievakje, kleur, datum, datum, lokale datum, e-mail, bestand, verborgen, afbeelding, maand, nummer, wachtwoord, radio, bereik, reset, submit, tel, text, time, url en week.

### Selectie-elementen

- [Groepen selectievakjes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox): Voor het selecteren van meerdere opties.
- [Keuzerondjes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio): Voor het selecteren van één optie in een groep.
- [Vervolgmenu&#39;s](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select): Een menu met opties weergeven. Bijvoorbeeld vervolgkeuzelijst.

### Containers

- Deelvensters/containers: gerelateerde formulierelementen groeperen voor een betere organisatie. Het is een combinatie van de [veldset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) en [legenda](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/legend).






## Eigenschappen van componenten

Elke formuliercomponent bevat diverse eigenschappen waarmee u het gedrag en de weergave ervan kunt bepalen. Hier worden de eigenschappen ondersteund door de componenten Adaptief formulierblok:


| Eigenschap | Toepasselijke onderdelen | Details |
|--------------|------------------------------|----------------------------------------------------------------------|
| Type | Alles | Hiermee wordt het type component opgegeven. Deze eigenschap bepaalt het gedrag en de weergave van het invoerveld. Voor tekstinvoer kan het type bijvoorbeeld &#39;text&#39;, &#39;email&#39; voor e-mailinvoer en &#39;password&#39; voor wachtwoordinvoer zijn. Ondersteuning voor adaptief formulierblok  <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types">alle geldige HTML5-invoertypen</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">selecteren</a>, en <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">veldset</a> als type. |
| Type | Alles | Hiermee wordt het type component opgegeven. Deze eigenschap bepaalt het gedrag en de weergave van het invoerveld. Voor tekstinvoer kan het type bijvoorbeeld &#39;text&#39;, &#39;email&#39; voor e-mailinvoer en &#39;password&#39; voor wachtwoordinvoer zijn. Ondersteuning voor adaptief formulierblok  <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types">alle geldige HTML5-invoertypen</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">selecteren</a>, en <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">veldset</a> als type. |
| Naam | Alles | Hiermee wordt de component aangegeven voor het verzenden van formulieren. Het kenmerk name wordt gebruikt wanneer de formuliergegevens naar de server worden verzonden, waarbij de gebruikersinvoer aan een specifiek veld wordt gekoppeld. |
| Label | Alles | Biedt contextuele informatie aan gebruikers. Het label is de tekst die naast de component wordt weergegeven en geeft gebruikers aanwijzingen over welke informatie moet worden ingevoerd. |
| Waarde | Tekst, wachtwoord, e-mail, Aantal, Waaier, Datum en zijn varianten (datetime-local, maand, week, tijd), Checkbox, Radio, Verborgen, Verzenden, Knoop | Specifies the initial value of the component. Voor tekstinvoer, tekstgebied en geselecteerde elementen is dit de standaardtekst of -optie die wordt weergegeven. Voor componenten van radio en checkbox, is dit de waarde/de gegevens die worden voorgelegd wanneer zij worden geselecteerd. Het kenmerk value is optioneel, maar moet als verplicht worden beschouwd voor selectievakjes en radio-invoer. |
| Plaatsaanduiding | Tekst, Tel, E-mail, Wachtwoord, Datum (en de varianten zoals maand, week, tijd, datumtime-local), Getal, Bereik | Biedt tips voor verwachte invoer. Het kenmerk placeholder biedt een korte tip die de verwachte waarde van het invoerveld beschrijft. Deze verdwijnt zodra de gebruiker begint te typen. |
| Beschrijving | Alles | Verstrekt extra informatie over de component en dient als hulptekst. In het beschrijvingsveld kunt u het doel of de instructies voor het invullen van het onderdeel nader toelichten. Hiermee kunnen gebruikers de context van het invoerveld beter begrijpen. |
| Zichtbaar | Alles | Bepaalt de zichtbaarheid bij openen. Het kenmerk visible is een Booleaanse eigenschap die bepaalt of de component in eerste instantie zichtbaar of verborgen is wanneer het formulier wordt geladen. Indien ingesteld op true, wordt het veld weergegeven; anders wordt het verborgen. |
| Verplicht | Tekst, Tel, E-mail, Wachtwoord, Datum en de varianten (datum-tijd-lokaal, maand, week, tijd), Number, Checkbox, Radio, File, Select (vervolgkeuzelijst), TextArea | Geeft aan of het veld moet worden ingevuld voordat het wordt verzonden. Het verplichte kenmerk is een Booleaanse eigenschap die wordt gebruikt om op te geven of de gebruiker invoer voor het veld moet opgeven voordat het formulier wordt verzonden. |
| Min | Datum (en zijn varianten zoals maand, week, tijd, datetime-local), Aantal, Waaier | Geeft de minimaal toegestane waarde op. Het kenmerk min stelt de minimale waarde in die de gebruiker in het veld kan invoeren. Voor numerieke invoer wordt bijvoorbeeld het laagste toegestane getal gedefinieerd. |
| Max | Datum (en zijn varianten zoals maand, week, tijd, datetime-local), Aantal, Waaier | Specifies the maximum allowed value. Het kenmerk max stelt de maximumwaarde in die de gebruiker in het veld kan invoeren. Voor datuminvoer wordt bijvoorbeeld de hoogst haalbare datum gedefinieerd. |
| Accepteren | Bestand | Definieert de toegestane bestandstypen. Het kenmerk accept is een door komma&#39;s gescheiden lijst met unieke bestandstype-specificaties die de bestandstypen beperkt die gebruikers kunnen selecteren in een veld voor bestandsinvoer. |
| Meerdere | Bestand | Hiermee worden meerdere selecties toegestaan. Het kenmerk multiple is een Booleaanse eigenschap die wordt gebruikt bij velden voor bestandsinvoer. Als deze optie is ingesteld op true, kunnen gebruikers meer dan één bestand selecteren. |
| Opties | Vervolgkeuzelijst | Hiermee geeft u keuzen op voor vervolgkeuzemenu&#39;s. De eigenschap options is een door komma&#39;s gescheiden lijst met opties voor vervolgkeuzemenu&#39;s, waarmee de selecteerbare opties worden gedefinieerd die aan de gebruiker worden weergegeven. |
| Ingeschakeld | Selectievakje, Radio | Hiermee bepaalt u of het veld standaard is geselecteerd. Het geselecteerde kenmerk is een Booleaanse eigenschap die wordt gebruikt met selectievakje en radio-invoer. Als de waarde true is, wordt hiermee aangegeven dat het veld standaard is geselecteerd wanneer het formulier wordt geladen. |
| Veldset | Alles | Hiermee groepeert u velden om visueel verschillende secties in een formulier te maken. Met de veldsetelementgroepen worden verwante velden in een formulier gegroepeerd, zodat u ze visueel kunt scheiden om de organisatie en gebruikerservaring te verbeteren. </br> Als u een set velden in een veldset wilt ordenen, gebruikt u de opdracht `fieldset` en geeft het naamkenmerk ervan op. In het onderstaande voorbeeld tonen we aan hoe keuzerondjes worden ingekapseld binnen een enkele veldset voor een betere organisatie. ![Voorbeeld van veldset](/help/edge/assets/fieldset-example.png) |



<!--

## Supported HTML 5 input types in Adaptive Form Block

The Adaptive Form Block supports a range of HTML 5 input types, and it also seamlessly renders forms created with AEM core components.
Here is the table which outlines how core components correspond to their HTML-5 input types in Edge Delivery:
<table>
 <tbody>
  <tr>
   <td><b>Core Components</b> </td>
   <td><b>HTML 5 input type</b> </td>
   <td><b>Details</b></td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/form-container.html">Form Container</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#form">form </td>
   <td> Create a form to capture user inputs.
   </td>
  </tr>
  <tr>
   <td><a herf="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text-input.html">Text Input</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/text">text</a></td>
   <td> Defines a single-line text input field. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/number-input.html">Number Input</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/number">number</a></td>
   <td>Lets user  enter a number input. You can also add built-in validation to reject non-numerical inputs. Lets user  enter a number input. You can also add built-in validation to reject non-numerical inputs. Initially, the input field is displayed as a number input. If a user applies a display pattern, it changes to text to allow the author to apply number formatting, since HTML 5 lacks support for display patterns. However, when the user clicks it, it returns to typing numbers.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-picker.html">Date Picker</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/date">date </a></td>
   <td> Create an input field for entering a date. You have the option to input the date either through a text box, which validates the entry, or through a dedicated date picker interface. Initially, the native date input field is displayed. If a user applies a display pattern, it changes to text to allow the user to apply formatting, since HTML 5 lacks support for display patterns. However, when the user clicks it, it returns to typing a date.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment.html">File Attachment</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/file">file</a></td>
   <td> Allows user to choose one or more files from the device storage. It supports enhanced file input validations, such as accepted file types, file size restrictions, and minimum/maximum file selection limits. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/drop-down.html"> Dropdown List</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">select</a></td>
   <td> Allows users to select one or more options from a list of predefined options. The options can be of type String, Number, or Boolean.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox-group.html">Checkbox Group</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox">multiple checkbox</a></td>
   <td> Allow users to select one or more options from a list. Multiple checkboxes are generated with identical names, each corresponding to an item in the enum. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/radio-button.html">Radio Button Group</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio">multiple radio</a></td>
   <td> Allows a user to select one option from a group of related options. Multiple radio buttons are generated with identical names, each corresponding to an item in the enum.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/button.html">Button</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/button">button</a></td>
   <td>A UI element that allows users to trigger an action when clicked. </td>
  </tr>
  <tr>
   <td><a href =""https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html">Panel</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset with legend</a></td>
   <td> Group sections within a form, where a nested *legend* element adds a caption for the form.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html">Wizard</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a></td>
   <td>Groups related sections within a form. It also controls the arrangement, supporting display options for positioning them at the top or at the left side. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text.html">Text</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p">p</a></td>
   <td>A p tag marks a paragraph. In visual content, paragraphs are chunks of text separated by blank lines or an indented first line</td>
  </tr>
     <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">Submit button</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/submit">submit</a></td>
   <td> A UI element that enables users to submit a form to the server upon clicking. If a user adds a submit rule to a button, it functions as the submit button. </td>
  </tr>
     <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/reset-button.html">Reset button</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/reset">reset</a></td>
   <td>A UI element that resets a form upon clicking. If a user adds a reset rule to a button, it functions as the reset button. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/email-input.html">Email Input</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/email">email</a></td>
   <td> Allows the user to enter and edit an email address. If the user adds the multiple attributes, a list of email addresses can be added or edited.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/telephone-input.html">Telephone Input</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/tel">tel</a></td>
   <td>Allows user to enter and edit a telephone number.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/header.html">Header</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/header"> header</a></td>
   <td>It includes introductory content, typically a group of introductory or navigational aids. It is supported outside Form container. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/footer.html">Footer</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/footer">footer</a></td>
   <td> Contains information such as copyright data or links to related documents. It is supported outside Form container.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html">Accordion<a></td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td> Allows user to create expandable and collapsible sections in a form. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html">Horizontal tabs</a></td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td>Organizes multiple sections of a form into separate tabs which are displayed horizontally.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/image.html">Image</a></td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td> Allows user to include images in a form.</td>
  </tr><tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/title.html">Title</a></td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td> Refers to the text that appears at the top of the form. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">Switch</td>
   <td><i>Not yet supported in Adaptive Form Block</i></td>
   <td> A two-state toggle that allows user to select between two states such as enabling or disabling a feature, setting, or functionality.</td>
  </tr>
 </tbody>
</table> -->

## Meer weergeven

- [Een formulier maken en een voorbeeld ervan bekijken](/help/edge/docs/forms/create-forms.md)
- [Formulier verzenden van gegevens inschakelen](/help/edge/docs/forms/submit-forms.md)
- [Een formulier publiceren naar sitepagina](/help/edge/docs/forms/publish-forms.md)
- [Validaties toevoegen aan formuliervelden](/help/edge/docs/forms/validate-forms.md)
- [Thema&#39;s en vormstijl wijzigen](/help/edge/docs/forms/style-theme-forms.md)
