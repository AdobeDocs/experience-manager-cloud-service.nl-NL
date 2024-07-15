---
title: AEM Forms Edge Delivery Services-formuliercomponenten
description: AEM Forms-Edge Delivery Services zijn gebouwd voor optimale prestaties, waardoor u de toekomst van gestroomlijnde gegevensverzameling en de betrokkenheid van gebruikers kunt inzien. In het artikel worden alle formuliercomponenten weergegeven die in het vak voor EDD-formulieren beschikbaar zijn.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: bae9a5178c025b3bafa8ac2da75a1203206c16e1
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 0%

---




# HTML-componenten ondersteund in Form Block Edge Delivery

AEM Forms Edge Delivery bevat een formulierblok. Met het formulierblok kunt u eenvoudig formulieren maken voor het vastleggen en opslaan van vastgelegde gegevens.

Het formulierblok ondersteunt OTB HTML-5-componenten zoals tekst, e-mail, nummer, datum en nog veel meer. De klasse biedt ook ondersteuning voor tekstgebied-, selectie- en veldsetelementen en bevat functies voor invoervalidatie die eigen zijn aan HTML-5. Met het formulierblok wordt een uniforme HTML-structuur gemaakt voor alle veldtypen en -containers, zodat de consistentie wordt gewaarborgd. U ook [ stijl de gebiedstypes ](https://adobe-rnd.github.io/form-block/customization/styling_form) gebruikend het `form.css` dossier.

## Ondersteunde invoertypen voor HTML 5 in formulierblok

Het formulierblok ondersteunt een reeks invoertypen van HTML 5 en het geeft ook formulieren die zijn gemaakt met AEM kerncomponenten naadloos weer.

Hier volgt de tabel waarin wordt beschreven hoe de kerncomponenten overeenkomen met hun invoertypen HTML-5 in Edge Delivery:

<table>
 <tbody>
  <tr>
   <td><b> Componenten van de Kern </b> </td>
   <td><b> HTML 5 inputtype </b> </td>
   <td><b>Details</b></td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/form-container.html">Formuliercontainer</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#form">formulier </td>
   <td> Maak een formulier om gebruikersinvoer vast te leggen.
   </td>
  </tr>
  <tr>
   <td><a herf="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text-input.html">Tekstinvoer</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/text">text</a></td>
   <td> Definieert een invoerveld voor één regel tekst. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/number-input.html">Nummerinvoer</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/number">getal</a></td>
   <td>Hiermee kan de gebruiker een getalinvoer invoeren. U kunt ook ingebouwde validatie toevoegen om niet-numerieke invoer af te wijzen. Hiermee kan de gebruiker een getalinvoer invoeren. U kunt ook ingebouwde validatie toevoegen om niet-numerieke invoer af te wijzen. In eerste instantie wordt het invoerveld weergegeven als invoer van een getal. Als een gebruiker een weergavepatroon toepast, wordt de tekst gewijzigd zodat de auteur getalnotatie kan toepassen, aangezien HTML 5 geen ondersteuning biedt voor weergavepatronen. Wanneer de gebruiker er echter op klikt, wordt er weer een getal getypt.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-picker.html">Datumkiezer</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/date">date </a></td>
   <td> Maak een invoerveld voor het invoeren van een datum. U kunt de datum invoeren via een tekstvak, dat de invoer valideert, of via een speciale datumkiezerinterface. In eerste instantie wordt het invoerveld voor de native datum weergegeven. Als een gebruiker een weergavepatroon toepast, wordt de tekst gewijzigd zodat de gebruiker opmaak kan toepassen, aangezien HTML 5 geen ondersteuning voor weergavepatronen biedt. Wanneer de gebruiker er echter op klikt, wordt de datum weer getypt.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment.html">Bestandsbijlage</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/file">file</a></td>
   <td> Hiermee kan de gebruiker een of meer bestanden kiezen in de apparaatopslag. Verbeterde validaties voor bestandsinvoer worden ondersteund, zoals geaccepteerde bestandstypen, beperkingen voor bestandsgrootte en minimum- en maximumwaarden voor bestandsselectie. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/drop-down.html"> Vervolgkeuzelijst</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">selecteren</a></td>
   <td> Hiermee kunnen gebruikers een of meer opties selecteren in een lijst met vooraf gedefinieerde opties. De opties kunnen van het type String, Number of Boolean zijn.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox-group.html">Groep selectievakjes</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox">meerdere selectievakjes</a></td>
   <td> Gebruikers toestaan een of meer opties in een lijst te selecteren. Er worden meerdere selectievakjes gegenereerd met identieke namen, die elk overeenkomen met een item in de opsomming. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/radio-button.html">Groep keuzerondjes</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio">meerdere radio's</a></td>
   <td> Hiermee kan een gebruiker een optie selecteren in een groep gerelateerde opties. Er worden meerdere keuzerondjes gegenereerd met identieke namen, die elk overeenkomen met een item in de opsomming.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/button.html">Knop</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/button">knop</a></td>
   <td>A UI element that allows users to trigger an action when clicked. </td>
  </tr>
  <tr>
   <td><a href="" https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html">Deelvenster</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">veldset met legenda</a></td>
   <td> Groepeer secties in een formulier, waarbij een genest *legend*-element een bijschrift toevoegt voor het formulier.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html">Wizard</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">veldset</a></td>
   <td>Groepeert gerelateerde secties in een formulier. Het regelt ook de rangschikking en ondersteunt weergaveopties om ze boven of links te plaatsen. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text.html">Tekst</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p">p</a></td>
   <td>Een tag p markeert een alinea. In visuele inhoud zijn alinea's tekstblokken gescheiden door lege regels of een ingesprongen eerste regel</td>
  </tr>
     <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">Verzenden, knop</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/submit">indienen</a></td>
   <td> A UI element that enables users to submit a form to the server upon click. Als een gebruiker een verzendregel aan een knop toevoegt, functioneert deze als verzendknop. </td>
  </tr>
     <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/reset-button.html">Knop Opnieuw instellen</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/reset">reset</a></td>
   <td>A UI element that resets a form when clicking. Als een gebruiker een terugstellingsregel aan een knoop toevoegt, functioneert het als terugstellenknoop. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/email-input.html">E-mailinvoer</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/email">email</a></td>
   <td> Hiermee kan de gebruiker een e-mailadres invoeren en bewerken. Als de gebruiker de meerdere kenmerken toevoegt, kan een lijst met e-mailadressen worden toegevoegd of bewerkt.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/telephone-input.html">Telefooninvoer</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/tel">tel</a></td>
   <td>Hiermee kan de gebruiker een telefoonnummer invoeren en bewerken.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/header.html">Koptekst</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/header"> header</a></td>
   <td>Het omvat inleidende inhoud, typisch een groep inleidende of navigatiehulpmiddelen. De functie wordt ondersteund buiten de formuliercontainer. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/footer.html">Voettekst</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/footer">voettekst</a></td>
   <td> Bevat informatie zoals copyrightgegevens of koppelingen naar verwante documenten. De functie wordt ondersteund buiten de formuliercontainer.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html">Accordeon<a></td>
   <td><i>Nog niet ondersteund in formulierblok</i></td>
   <td> Hiermee kunnen gebruikers uitbreidbare en inklapbare secties in een formulier maken. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html">Horizontale tabbladen</a></td>
   <td><i>Nog niet ondersteund in formulierblok</i></td>
   <td>Hiermee plaatst u meerdere secties van een formulier in afzonderlijke tabbladen die horizontaal worden weergegeven.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/image.html">Afbeelding</a></td>
   <td><i>Nog niet ondersteund in formulierblok</i></td>
   <td> Hiermee kunnen gebruikers afbeeldingen in een formulier opnemen.</td>
  </tr><tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/title.html">Titel</a></td>
   <td><i>Nog niet ondersteund in formulierblok</i></td>
   <td> Verwijst naar de tekst die boven aan het formulier wordt weergegeven. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">Overschakelen</td>
   <td><i>Nog niet ondersteund in formulierblok</i></td>
   <td> Een schakeloptie met twee statussen waarmee de gebruiker twee statussen kan selecteren, zoals het in- of uitschakelen van een functie, instelling of functionaliteit.</td>
  </tr>
 </tbody>
</table>


