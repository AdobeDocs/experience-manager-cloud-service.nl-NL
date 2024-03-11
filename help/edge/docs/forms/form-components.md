---
title: Formuliercomponenten en -eigenschappen
description: Dit document biedt een overzicht van de formuliercomponenten en hun eigenschappen die beschikbaar zijn in AEM Forms Edge Delivery Service.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 7d087d41-9313-482a-a905-8955b0999781
source-git-commit: 4144f9704aaf17ea684be147395adc3aa31641f2
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 0%

---

# Formulieronderdelen en -eigenschappen: AEM Forms Edge Delivery-service

Met AEM Forms Edge Delivery Services kunt u gebruikersvriendelijke en interactieve formulieren maken met behulp van verschillende componenten. Deze componenten zijn geschikt voor verschillende soorten gegevensverzameling en kunnen eenvoudig aan uw specifieke behoeften worden aangepast.


![Een voorbeeldspreadsheet met enkele componenten en eigenschappen](/help/edge/assets/sample-form-in-spreadsheet.png)

Het Adaptive Forms Block genereert een [uniforme HTML-structuur](/help/edge/docs/forms/style-theme-forms.md) voor alle veldtypen en -containers (panelen) die de consistentie waarborgen. Deze consistente structuur maakt het eenvoudiger om [een formulier opmaken](/help/edge/docs/forms/style-theme-forms.md).

## Beschikbare componenten

Hier volgt een overzicht van de beschikbare componenten:

### Invoervelden

* Alle geldige HTML5 [invoertypen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types) en [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea). Bijvoorbeeld knop, selectievakje, kleur, datum, datum, lokale datum, e-mail, bestand, verborgen, afbeelding, maand, nummer, wachtwoord, radio, bereik, reset, submit, tel, text, time, url en week.

### Selectie-elementen

* [Groepen selectievakjes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox): Voor het selecteren van meerdere opties.
* [Keuzerondjes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio): Voor het selecteren van één optie in een groep.
* [Vervolgmenu&#39;s](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select): Een menu met opties weergeven. Bijvoorbeeld vervolgkeuzelijst.

### Containers

* Deelvensters/containers: gerelateerde formulierelementen groeperen voor een betere organisatie. Het is een combinatie van de [veldset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) en [legenda](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/legend).


## Eigenschappen van componenten

Elke formuliercomponent bevat diverse eigenschappen waarmee u het gedrag en de weergave ervan kunt bepalen. Hier worden de eigenschappen ondersteund door Adaptive Forms Block-componenten:


| Eigenschap | Toepasselijke onderdelen | Details |
|--------------|------------------------------|----------------------------------------------------------------------|
| Type | Alles | Hiermee wordt het type component opgegeven. Deze eigenschap bepaalt het gedrag en de weergave van het invoerveld. Voor tekstinvoer kan het type bijvoorbeeld &#39;text&#39;, &#39;email&#39; voor e-mailinvoer en &#39;password&#39; voor wachtwoordinvoer zijn. Adaptief Forms-blok ondersteunt  <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types">alle geldige HTML5-invoertypen</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">selecteren</a>, en <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">veldset</a> als type. |
| Type | Alles | Hiermee wordt het type component opgegeven. Deze eigenschap bepaalt het gedrag en de weergave van het invoerveld. Voor tekstinvoer kan het type bijvoorbeeld &#39;text&#39;, &#39;email&#39; voor e-mailinvoer en &#39;password&#39; voor wachtwoordinvoer zijn. Adaptief Forms-blok ondersteunt  <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types">alle geldige HTML5-invoertypen</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea">textarea</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">selecteren</a>, en <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">veldset</a> als type. |
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

