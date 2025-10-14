---
title: Aangepaste componenten maken voor een EDS-formulier
description: Aangepaste componenten maken voor een EDS-formulier
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: 77e90657-38db-4a49-9aac-3f3774b62624
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 1%

---

# Aangepaste componenten maken

Edge Delivery Services voor AEM Forms staat u toe om de [&#x200B; inheemse de vormcomponenten van HTML &#x200B;](/help/edge/docs/forms/form-components.md) aan te passen en gebruikersvriendelijke en interactieve vormen tot stand te brengen. Het laat u toe om de vormcomponenten met vooraf bepaalde prijsverhoging te wijzigen, zoals die in [&#x200B; wordt verklaard het Stijlen van vormgebieden &#x200B;](/help/edge/docs/forms/style-theme-forms.md) gebruikend douane CSS (Cascading Style Sheets) en douanecode voor het versieren van de component, zo verbeterend de verschijning van vormgebieden binnen een Aangepast Blok van Forms.

![&#x200B; de component van de Douane &#x200B;](/help/edge/assets/custom-component-image.png)

In dit document worden de stappen beschreven waarmee u aangepaste componenten kunt maken door de native HTML-formuliercomponenten op te maken om de gebruikerservaring te verbeteren en de visuele aantrekkingskracht van het formulier te vergroten.

Neem een voorbeeld van een `range` -component die de `Estimated trip cost` op een formulier weergeeft. De component `range` wordt weergegeven als een rechte lijn, zonder waarden als minimum, maximum of geselecteerde waarde weer te geven.

![&#x200B; Inheemse component van de Waaier &#x200B;](/help/edge/assets/native-range-component.png)

Laten we beginnen met het aanpassen van het veld `range` om de minimale, maximale en geselecteerde waarden op de regel weer te geven door stijl toe te voegen met CSS en een aangepaste functie toe te voegen om een component te decoreren.

![&#x200B; de component van de Waaier van de Douane &#x200B;](/help/edge/assets/custom-range-component.png)

Aan het einde van dit artikel leert u aangepaste componenten te maken door stijlen toe te voegen in het CSS-bestand en de aangepaste functie.

## Voorwaarden

Voordat u een aangepaste component gaat maken, moet u:

- Heb een basiskennis van [&#x200B; inheemse componenten van HTML &#x200B;](/help/edge/docs/forms/form-components.md).
- Weet hoe te [&#x200B; de gebieden van de stijlvorm die op gebiedstype worden gebaseerd CSS selecteurs gebruiken &#x200B;](/help/edge/docs/forms/style-theme-forms.md)


## Een aangepaste component maken


![&#x200B; stappen om douanecomponent &#x200B;](/help/edge/docs/forms/assets/steps-to-create-custom-component.png) te creëren

Laten we nu elke stap in detail begrijpen.

<!--Refer to the [enquiry spreadsheet](/help/edge/docs/forms/assets/enquiry.xlsx) to customize the `range` component, by following the steps as explained below.-->

### Een aangepaste functie toevoegen om de component te decoreren

De aangepaste functie die in `[../Form Block/components]` wordt toegevoegd, bestaat uit:

- **verklaring van de Functie**: Bepaal de functienaam en zijn parameters.
- **Logische implementatie**: Schrijf de logica om het douanegedrag voor de component toe te voegen.
- **de uitvoer van de Functie**: Maak de functie toegankelijk in `[Form Block]`.

Een aangepaste functie toevoegen:

1. Navigeer naar `[../Form Block/components]` .
1. Zoek een bestand met de naam `range.js` . als deze niet aanwezig is, maakt u deze.
1. Voeg de volgende coderegel toe:

   ```javascript
   function updateBubble(input, element) {
   const step = input.step || 1;
   const max = input.max || 0;
   const min = input.min || 1;
   const value = input.value || 1;
   const current = Math.ceil((value - min) / step);
   const total = Math.ceil((max - min) / step);
   const bubble = element.querySelector('.range-bubble');
   // during initial render the width is 0. Hence using a default here.
   const bubbleWidth = bubble.getBoundingClientRect().width || 31;
   const left = `${(current / total) * 100}% - ${(current / total) * bubbleWidth}px`;
   bubble.innerText = `${value}`;
   const steps = {
   '--total-steps': Math.ceil((max - min) /    step),
   '--current-steps': Math.ceil((value - min) / step),
   };
   const style = Object.entries(steps).map(([varName, varValue]) => `${varName}:${varValue}`).join(';');
   bubble.style.left = `calc(${left})`;
   element.setAttribute('style', style);
   }
   // eslint-disable-next-line no-unused-vars
   export default function decorateRange(fieldDiv, field) {
   loadCSS('/blocks/form/components/range/range.css');
   const input = fieldDiv.querySelector('input');
   // modify the type in case it is not range.
   input.type = 'range';
   input.min = input.min || 1;
   // create a wrapper div to provide the min/max and current value
   const div = document.createElement('div');
   div.className = 'range-widget-wrapper';
   input.after(div);
   const hover = document.createElement('span');
   hover.className = 'range-bubble';
   const rangeMinEl = document.createElement('span');
   rangeMinEl.className = 'range-min';
   const rangeMaxEl = document.createElement('span');
   rangeMaxEl.className = 'range-max';
   rangeMinEl.innerText = `${input.min || 1}`;
   rangeMaxEl.innerText = `${input.max}`;
   div.appendChild(hover);
   // move the input element within the wrapper div
   div.appendChild(input);
   div.appendChild(rangeMinEl);
   div.appendChild(rangeMaxEl);
   input.addEventListener('input', (e) => {
       updateBubble(e.target, div);
   });
   updateBubble(input, div);
   // as a best practice add a custom css class to apply custom styling
   fieldDiv.classList.add('decorated');
   return fieldDiv;    
   }
   ```

1. Sla de wijzigingen op.

### Injecteer de decorator in het Formulierblok

In `[Form Block]` worden semantische HTML gebruikt om formuliervelden, waaronder invoervelden, labels en Help-tekst, te genereren met standaardkenmerken voor toegankelijkheid. Als u wilt dat de `[Form Block]` aangepaste decorator voor een opgegeven component gebruikt, definieert u deze in het `mappings.js` -bestand. Het bestand `mappings.js` importeert een functie die de module retourneert die verantwoordelijk is voor het versieren van een bepaalde component. De functie neemt de veldeigenschappen en keert een decoratorfunctie voor het vormgebied terug.

In ons geval controleert de functie de eigenschap `fieldType` van het veld en retourneert de functie de aangepaste bereikdecorator uit het `range.js` -bestand dat zich in `[../Form Block/components]` bevindt.

Injecteer de decorator in het Formulierblok:

1. Ga naar `[../Form Block/]` en open `mapping.js` .
1. Voeg de volgende coderegel toe:

   ```javascript
   export default async function componentDecorator(fd) {
   const { ':type': type = '', fieldType } = fd;
   .... existing code ....
   if (fieldType === 'range') {
   const module = await import('./components/range.js');
   return module.default(element,fd);
   }
    return null; // null should be returned to use the original markup
   }
   ```

1. Sla de wijzigingen op.

### Stijl toevoegen voor de component in het CSS-bestand

U kunt de weergave van formuliervelden wijzigen op basis van veldtype- en veldnamen met CSS-kiezers, zodat op basis van vereisten een consistente of unieke opmaak mogelijk is. Als u de component wilt opmaken, voegt u code toe in het `form.css` -bestand om de vormgeving van de component van het formulier te wijzigen.

Als u de stijl voor de component `range` wilt aanpassen, neemt u een CSS-codefragment op dat een `range` -invoerelement en de bijbehorende componenten in een formulier opmaakt. Hierbij wordt uitgegaan van een gestructureerde HTML-indeling met klassen zoals `.form` en `.range-wrapper` .

Stijl toevoegen voor een component in het CSS-bestand:

1. Ga naar `[../Form Block/]` en open `form.css` .
1. Voeg de volgende coderegel toe:

   ```javascript
       /** styling for range */
   main .form .range-wrapper.decorated input[type="range"] {
   margin: unset;
   padding: unset;
   appearance: none;
   height: 5px;
   border-radius: 5px;
   border: none;
   background-image: linear-gradient(to right, var(--button-primary-color) calc(100% * var(--current-steps)/var(--total-steps)), #C5C5C5 calc(100% * var(--current-steps)/var(--total-steps)));
   }
   
   main .form .range-wrapper.decorated input[type="range"]:focus {
   outline: none;
   }
   
   .range-wrapper.decorated input[type="range"]::-webkit-slider-thumb {
   appearance: none;
   width: 25px;
   height: 25px;
   border-radius: 50%;
   background: #fff;
   border: 3px solid var(--button-primary-color);
   cursor: pointer;
   outline: 3px solid #fff;
   }
   
   .range-wrapper.decorated input[type="range"]:focus::-webkit-slider-thumb {
   border-color: var(--button-primary-color);
   }
   
   .range-wrapper.decorated .range-bubble {
   color: #17252e;
   font-size: 20px;
   line-height: 28px;
   position: relative;
   display: inline-block;
   padding-bottom: 12px;
   }
   
   .range-wrapper.decorated .range-min,
   .range-wrapper.decorated .range-max {
   font-size: 14px;
   line-height: 22px;
   color: #494f50;
   margin-top: 16px;
   display: inline-block;
   }
   
   .range-wrapper.decorated .range-max {
   float: right;
   }
   ```

1. Sla de wijzigingen op.

### De bestanden implementeren en het project bouwen

Stel de bijgewerkte `range.js`, `mapping.js` en `form.css` dossiers aan uw project GitHub op en verifieer een succesvolle bouwstijl.

### Een voorbeeld van het formulier weergeven met AEM sidekick

Geef een voorbeeld van het formulier weer met de nieuw geïmplementeerde functie die de component `range` opmaakt.

![&#x200B; de componentenvorm van de Douane &#x200B;](/help/edge/assets/custom-componet-form.png)

De nieuwe opmaak voor de component `range` geeft de minimale, maximale en geselecteerde waarden op de regel weer door stijlen toe te voegen met CSS en een aangepaste functie die een decorator voor de component bevat.


