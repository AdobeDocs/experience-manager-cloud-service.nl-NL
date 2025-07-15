---
title: Aangepaste componenten maken voor een EDS-formulier
description: Aangepaste componenten maken voor een EDS-formulier
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 2bbe3f95-d5d0-4dc7-a983-7a20c93e2906
source-git-commit: 9ef4c5638c2275052ce69406f54dda3ea188b0ef
workflow-type: tm+mt
source-wordcount: '1804'
ht-degree: 0%

---

# Aangepaste component maken in WYSIWYG Authoring

<span class="preview"> Dit is een pre-versieeigenschap beschikbaar door ons <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=nl-NL#new-features"> pre-vrijgavekanaal </a>. </span>


Edge Delivery Services Forms biedt aanpassing, waardoor ontwikkelaars aan de voorzijde op maat aangepaste formulieronderdelen kunnen maken. Deze aangepaste componenten worden naadloos geïntegreerd in de WYSIWYG-ontwerpervaring, zodat formulierauteurs ze eenvoudig kunnen toevoegen, configureren en beheren in de formuliereditor. Met aangepaste componenten kunnen auteurs de functionaliteit verbeteren en tegelijkertijd zorgen voor een vloeiend en intuïtief ontwerpproces.

In dit document worden de stappen beschreven waarmee u aangepaste componenten kunt maken door de native HTML-formuliercomponenten op te maken om de gebruikerservaring te verbeteren en de visuele aantrekkingskracht van het formulier te vergroten.

## Voorwaarden

Voordat u een aangepaste component gaat maken, moet u:

* Heb een basiskennis van [ inheemse componenten van HTML ](/help/edge/docs/forms/form-components.md).
* Weet hoe te [ de gebieden van de stijlvorm die op gebiedstype worden gebaseerd CSS selecteurs gebruiken ](/help/edge/docs/forms/style-theme-forms.md)

## Een aangepaste component maken

Als u een aangepaste component toevoegt in de Universal Editor, moet u een nieuwe component beschikbaar stellen zodat formulierauteurs deze kunnen gebruiken tijdens het ontwerpen van formulieren. Dit omvat het registreren van de component, het definiëren van de eigenschappen en het configureren van de locatie waar de component kan worden gebruikt. Aangepaste componenten maken gaat u als volgt te werk:

[1. Structuur toevoegen voor nieuwe aangepaste component ](#1-adding-structure-for-new-custom-component)
[ 2. Het bepalen van de eigenschappen van uw douanecomponent voor creatie ](#2-defining-the-properties-of-your-custom-component-for-authoring)
[ 3.  De aangepaste component zichtbaar maken in de lijst met WYSIWYG-componenten ](#3-making-your-custom-component-visible-in-the-wysiwyg-component-list)
[ 4. Registreren van uw douanecomponent ](#4-registering-your-custom-component)
[ 5. Het runtimegedrag voor uw douanecomponent toevoegen ](#5-adding-the-runtime-behaviour-for-your-custom-component)

Neem een voorbeeld van het creëren van een nieuwe douanecomponent genoemd **waaier**. De bereikcomponent wordt weergegeven als een rechte lijn en geeft waarden weer zoals de minimum-, maximum- of geselecteerde waarde.

![ A visuele vertegenwoordiging van een waaiercomponent die een schuif met minimum en maximumwaarden tonen, en een geselecteerde waardeindicator ](/help/edge/docs/forms/universal-editor/assets/custom-component-range-style.png)

Aan het einde van dit artikel leert u zelf aangepaste componenten te maken.

### &#x200B;1. Structuur toevoegen voor nieuwe aangepaste component

Voordat een aangepaste component kan worden gebruikt, moet deze zijn geregistreerd, zodat de Universal Editor deze herkent als een beschikbare optie. Dit wordt bereikt door een componentdefinitie, die een unieke id, standaardeigenschappen en de structuur van de component bevat. Voer de volgende stappen uit om de aangepaste component beschikbaar te maken voor het ontwerpen van formulieren:

1. **voeg nieuwe omslag en dossiers** toe
Voeg nieuwe map en bestanden toe voor uw nieuwe aangepaste component in uw AEM-project.
   1. Open uw AEM-project en navigeer naar `../blocks/form/components/` .
   1. Voeg een nieuwe map voor uw aangepaste component toe op `../blocks/form/components/<component_name>` . In dit voorbeeld maken we een map met de naam `range` .
   1. Navigeer naar de nieuwe map op `../blocks/form/components/<component_name>` . Navigeer bijvoorbeeld naar `../blocks/form/components/range` en voeg de volgende bestanden toe:
      * `/blocks/form/components/range/_range.json` - Bevat de definitie van de aangepaste component.
      * `../blocks/form/components/range/range.css` - Definieert de opmaak voor de aangepaste component.
      * `../blocks/form/components/range/range.js`: past de aangepaste component bij uitvoering aan.

        ![ Toevoegend de douanecomponent voor creatie ](/help/edge/docs/forms/universal-editor/assets/adding-custom-component.png)

        >[!NOTE]
        >
        > Zorg ervoor dat het JSON-bestand een onderstrepingsteken (_) als voorvoegsel in de bestandsnaam bevat.

1. Navigeer naar het `/blocks/form/components/range/_range.json` -bestand en voeg de componentdefinitie voor de aangepaste component toe.

1. **voeg de componentendefinitie** toe

   Als u de definitie wilt toevoegen, moeten de velden die in het `_range.json` -bestand moeten worden toegevoegd, als volgt worden ingesteld:

   * **titel**: De titel van de component die in de Universele Redacteur wordt getoond.
   * **identiteitskaart**: Een uniek herkenningsteken van de component.
   * **fieldType**: Forms steunt diverse **fieldType** om specifieke soorten gebruikersinput te vangen. U kunt [ gesteunde fieldType in de Extra sectie van de Byte ](#supported-fieldtypes) vinden.
   * **resourceType**: Elke douanecomponent heeft een geassocieerd middeltype dat op zijn fieldType wordt gebaseerd. U kunt [ gesteunde resourceType in de Extra sectie van de Byte ](#supported-resourcetype) vinden.
   * **jcr:titel**: Het is gelijkaardig aan een titel, maar het wordt opgeslagen binnen de structuur van de component.
   * **fd:viewType**: Het vertegenwoordigt de naam van de douanecomponent. Dit is de unieke id voor de component. U moet een aangepaste weergave voor de component maken.

Het bestand `_range.json` ziet er na het toevoegen van de componentdefinitie als volgt uit:

```javascript
{
  "definitions": [
    {
      "title": "Range",
      "id": "range",
      "plugins": {
        "xwalk": {
          "page": {
            "resourceType": "core/fd/components/form/numberinput/v1/numberinput",
            "template": {
              "jcr:title": "Range",
              "fieldType": "number-input",
              "fd:viewType": "range",
              "enabled": true,
              "visible": true
            }
          }
        }
      }
    }
  ]
}
```

>[!NOTE]
>
> Alle componenten met betrekking tot formulieren volgen dezelfde aanpak als Sites wanneer u blokken toevoegt aan de Universal Editor. U kunt naar [ verwijzen Creërend Blokken Instrumented voor gebruik met het Universele artikel van de Redacteur ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/create-block) voor meer informatie.

### &#x200B;2. De eigenschappen van de aangepaste component definiëren voor ontwerpen

De aangepaste component bevat een componentmodel dat aangeeft welke eigenschappen door de auteur van het formulier kunnen worden geconfigureerd. Deze eigenschappen verschijnen in de **dialoog van Eigenschappen** van de Universele Redacteur, toestaand auteurs om montages zoals etiketten, bevestigingsregels, stijlen, en andere attributen aan te passen. Eigenschappen definiëren:

1. Navigeer naar het `/blocks/form/components/range/_range.json` -bestand en voeg het componentmodel voor de aangepaste component toe.

1. **voeg het componentenmodel** toe

   Als u het componentmodel voor uw aangepaste component wilt definiëren, moet u de relevante velden toevoegen aan het `_range.json` -bestand.

   1. **creeer nieuw model**

      * Voeg in de modellenarray een nieuw object toe en stel de `id` van het componentmodel in zodat deze overeenkomt met de eigenschap `fd:viewType` die eerder in de componentdefinitie is geconfigureerd.
      * Neem een array met velden in dit object op.

   2. **bepaalt Gebieden voor de dialoog van het Bezit**

      * Elk voorwerp in de gebiedsserie zou een container-type component moeten zijn, toestaand het om als lusje in de **dialoog van het Bezit** te verschijnen.
      * Sommige velden kunnen verwijzen naar herbruikbare eigenschappen die beschikbaar zijn in `models/form-common` .

   3. **Gebruik een Bestaand Model van de Component als Verwijzing**

      * U kunt de inhoud van een bestaand componentenmodel kopiëren dat aan uw gekozen `fieldType` beantwoordt en het wijzigen zoals nodig. Bijvoorbeeld, wordt de `number-input` component uitgebreid om a **waaier** component tot stand te brengen, zodat kunnen wij de modelserie van `models/form-components/_number-input.json` als verwijzing gebruiken.

   Het bestand `_range.json` ziet er na het toevoegen van het componentmodel als volgt uit:

   ```javascript
   "models": [
   {
     "id": "range",
     "fields": [
       {
         "component": "container",
         "name": "basic",
         "label": "Basic",
         "collapsible": false,
         "...": "../../../../models/form-common/_basic-input-fields.json"
       },
       {
         "...": "../../../../models/form-common/_help-container.json"
       },
       {
         "component": "container",
         "name": "validation",
         "label": "Validation",
         "collapsible": true,
         "...": "../../../../models/form-common/_number-validation-fields.json"
       }
     ]
   }
   ]
   ```

   >[!NOTE]
   >
   > Om een nieuw gebied aan de **dialoog van het Bezit** van een douanecomponent toe te voegen, houd aan het [ bepaalde schema ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/field-types#loading-model).

   U kunt [ douaneeigenschappen ](#adding-custom-properties-for-your-custom-component) aan een douanecomponent ook toevoegen om zijn functionaliteit uit te breiden.

#### Aangepaste eigenschappen voor uw aangepaste component toevoegen

Met aangepaste eigenschappen kunt u specifieke gedragingen definiëren op basis van waarden die zijn ingesteld in het dialoogvenster Eigenschappen van een component. Hierdoor worden de functionaliteit en aanpassingsopties van de component uitgebreid.

In dit voorbeeld, voegen wij de Waarde van de Stap als douanebezit aan de component van de Waaier toe.

![ de waarde van de Stap douanebezit ](/help/edge/docs/forms/universal-editor/assets/customcomponent-stepvalue.png)

Om het de douanebezit van de Waarde van de Stap toe te voegen, voeg het componentenmodel met de volgende lijnen van code in het ` _<component>.json` dossier toe:

```javascript
      {
      "component": "number",
      "name": "stepValue",
      "label": "Step Value",
      "valueType": "number"
      }
```

Het fragment JSON bepaalt een douanebezit genoemd **Waarde van de Stap** voor de component van de Waaier van a **&#x200B;**. Hieronder volgt een uitsplitsing van elk veld:

* **component**: Specificeert het type van inputgebied dat in de dialoog van het Bezit wordt gebruikt. In dit geval geeft `number` aan dat het veld numerieke waarden accepteert.
* **naam**: Het herkenningsteken voor het bezit, dat wordt gebruikt om het in de logica van de component van verwijzingen te voorzien. Hier vertegenwoordigt `stepValue` de step waarde die voor de waaier wordt geplaatst.
* **etiket**: De vertoningsnaam van het bezit zoals gezien in de dialoog van het Bezit.
* **valueType**: Bepaalt het gegevenstype dat voor het bezit wordt verwacht. `number` zorgt ervoor dat alleen numerieke invoer is toegestaan.

U kunt `stepValue` nu gebruiken als een aangepaste eigenschap in de JSON-eigenschappen van `range.js` en dynamisch gedrag implementeren op basis van de waarde ervan bij uitvoering.

Het uiteindelijke bestand van `_range.json` ziet er daarom als volgt uit na het toevoegen van de componentdefinitie, het componentmodel en de aangepaste eigenschappen:

```javascript
 {
  "definitions": [
    {
      "title": "Range",
      "id": "range",
      "plugins": {
        "xwalk": {
          "page": {
            "resourceType": "core/fd/components/form/numberinput/v1/numberinput",
            "template": {
              "jcr:title": "Range",
              "fieldType": "number-input",
              "fd:viewType": "range",
              "enabled": true,
              "visible": true
            }
          }
        }
      }
    }
  ],
  "models": [
    {
      "id": "range",
      "fields": [
        {
          "component": "container",
          "name": "basic",
          "label": "Basic",
          "collapsible": false,
          "...": "../../../../models/form-common/_basic-input-fields.json"
         {
           "component": "number",
           "name": "stepValue",
            "label": "Step Value",
             "valueType": "number"
}
        },
        {
          "...": "../../../../models/form-common/_help-container.json"
        },
        {
          "component": "container",
          "name": "validation",
          "label": "Validation",
          "collapsible": true,
          "...": "../../../../models/form-common/_number-validation-fields.json"
        }
      ]
    }
  ]
}
```

![ componentendefinitie en model ](/help/edge/docs/forms/universal-editor/assets/custom-component-json-file.png)


### &#x200B;3. De aangepaste component zichtbaar maken in de lijst met WYSIWYG-componenten

Een filter bepaalt welke sectie waarin de douanecomponent in Universele Redacteur kan worden gebruikt. Dit zorgt ervoor dat de component alleen in de juiste secties kan worden gebruikt, waarbij de structuur en bruikbaarheid behouden blijven.

Om ervoor te zorgen dat de aangepaste component tijdens het ontwerpen van formulieren in WYSIWYG in de lijst met beschikbare componenten wordt weergegeven:

1. Navigeer naar het `/blocks/form/_form.json` -bestand.
1. Zoek de componentenarray in het object dat `id="form"` heeft.
1. Voeg de `fd:viewType` -waarde van `definitions[]` toe aan de componentenarray van het object met `id="form"` .

```javascript
 "filters": [
    {
      "id": "form",
      "components": [
        "captcha",
        "checkbox",
        "checkbox-group",
        "date-input",
        "drop-down",
        "email",
        "file-input",
        "form-accordion",
        "form-button",
        "form-fragment",
        "form-image",
        "form-modal",
        "form-reset-button",
        "form-submit-button",
        "number-input",
        "panel",
        "plain-text",
        "radio-group",
        "rating",
        "telephone-input",
        "text-input",
        "tnc",
        "wizard",
        "range"
      ]
    }
  ]
```

![ componentenfilter ](/help/edge/docs/forms/universal-editor/assets/custom-component-form-file.png)

### &#x200B;4. Uw aangepaste component registreren

Als u wilt dat het formulierblok de aangepaste component herkent en zijn eigenschappen die in het componentmodel zijn gedefinieerd tijdens het ontwerpen van het formulier laadt, voegt u de `fd:viewType` -waarde van de componentdefinitie toe aan het `mappings.js` -bestand.
Een component registreren:
1. Navigeer naar het `/blocks/form/mappings.js` -bestand.
1. Zoek de array `customComponents[]` .
1. Voeg de `fd:viewType` -waarde van de `definitions[]` -array toe aan de `customComponents[]` -array.

```javascript
let customComponents = ["range"];
const OOTBComponentDecorators = ['file-input',
                                 'wizard', 
                                 'modal', 'tnc',
                                'toggleable-link',
                                'rating',
                                'datetime',
                                'list',
                                'location',
                                'accordion'];
```

![ componentenafbeelding ](/help/edge/docs/forms/universal-editor/assets/custom-component-mapping-file.png)

Nadat u de bovenstaande stappen hebt uitgevoerd, wordt de aangepaste component weergegeven in de lijst met componenten van het formulier in de Universal Editor. U kunt het vervolgens slepen en neerzetten in uw formuliersectie.

![ Screenshot van het Universele de componentenpalet van de Redacteur die de component van de douanewaaier beschikbaar voor belemmering-en-daling in vormen tonen ](/help/edge/docs/forms/universal-editor/assets/custom-component-range.png)

In de onderstaande schermafbeelding worden de eigenschappen getoond van de component `range` die aan het componentmodel is toegevoegd, waarmee de eigenschappen worden opgegeven die de auteur van het formulier kan configureren.:

![ Schermafbeelding van het Universele paneel van de Eigenschappen van de Redacteur die configureerbare montages voor de waaiercomponent met inbegrip van basiseigenschappen, bevestigingsregels, en het stileren opties ](/help/edge/docs/forms/universal-editor/assets/range-properties.png) tonen

U kunt nu het runtimegedrag van uw aangepaste component definiëren door stijlen en functionaliteit toe te voegen.

### &#x200B;5. Het runtimegedrag voor uw aangepaste component toevoegen

U kunt douanecomponenten wijzigen gebruikend vooraf bepaalde prijsverhoging, zoals die in [ wordt verklaard het Stileren van vormgebieden ](/help/edge/docs/forms/style-theme-forms.md). Dit kan worden bereikt met aangepaste CSS (Cascading Style Sheets) en aangepaste code om de vormgeving van de component te verbeteren. Het runtimegedrag voor de component toevoegen:

1. Als u de opmaak wilt toevoegen, navigeert u naar het `/blocks/form/components/range/range.css` -bestand en voegt u de volgende coderegel toe:

   ```javascript
   /** Styling for range */
   main .form .range-widget-wrapper.decorated input[type="range"] {
   margin: unset;
   padding: unset;
   appearance: none;
   height: 5px;
   border-radius: 5px;
   border: none;
   background-image: linear-gradient(to right, #ADD8E6 calc(100% * var(--current-steps)/var(--total-steps)), #C5C5C5 calc(100% * var(--current-steps)/var(--total-steps)));
   }
   
   main .form .range-widget-wrapper.decorated input[type="range"]:focus {
   outline: none;
   }
   
   .range-widget-wrapper.decorated input[type="range"]::-webkit-slider-thumb {
   appearance: none;
   width: 25px;
   height: 25px;
   border-radius: 50%;
   background: #00008B; /* Dark Blue */
   border: 3px solid #00008B; /* Dark Blue */
   cursor: pointer;
   outline: 3px solid #fff;
   }
   
   .range-widget-wrapper.decorated input[type="range"]:focus::-webkit-slider-thumb {
   border-color: #00008B; /* Dark Blue */
   }
   
   .range-widget-wrapper.decorated .range-bubble {
   color: #00008B; /* Dark Blue */
   font-size: 20px;
   line-height: 28px;
   position: relative;
   display: inline-block;
   padding-bottom: 12px;
   font-weight: bold;
   }
   
   .range-widget-wrapper.decorated .range-min,
   .range-widget-wrapper.decorated .range-max {
   font-size: 14px;
   line-height: 22px;
   color: #494f50;
   margin-top: 16px;
   display: inline-block;
   }
   
   .range-widget-wrapper.decorated .range-max {
   float: right;
   }
   ```

   Met de code kunt u de opmaak en visuele weergave van de aangepaste component definiëren.

1. Als u de functionaliteit wilt toevoegen, navigeert u naar het `/blocks/form/components/range/range.js` -bestand en voegt u de volgende coderegel toe:

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
       '--total-steps': Math.ceil((max - min) / step),
       '--current-steps': Math.ceil((value - min) / step),
   };
   const style = Object.entries(steps).map(([varName, varValue]) => `${varName}:${varValue}`).join(';');
   bubble.style.left = `calc(${left})`;
   element.setAttribute('style', style);
   }
   
   export default async function decorate(fieldDiv, fieldJson) {
   console.log('RANGE DIV: ', fieldDiv);
   console.log('RANGE JSON: fieldJson', fieldJson);
    const input = fieldDiv.querySelector('input');
   // modify the type in case it is not range.
   input.type = 'range';
   input.min = input.min || 10;
   input.max = input.max || 1000;
   // create a wrapper div to provide the min/max and current value
   const div = document.createElement('div');
   div.className = 'range-widget-wrapper decorated';
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
   return fieldDiv;
   }
   ```

   Het bepaalt hoe de aangepaste component reageert op gebruikersinvoer, gegevens verwerkt en integreert met het formulierblok in de Universal Editor.

   Nadat u aangepaste stijlen en functionaliteit hebt opgenomen, worden de weergave en het gedrag van de bereikcomponent verbeterd. Het bijgewerkte ontwerp weerspiegelt de toegepaste stijlen, terwijl de toegevoegde functionaliteit een dynamischere en interactieve gebruikerservaring garandeert.
In de onderstaande schermafbeelding ziet u de bijgewerkte bereikcomponent.

![ de definitieve waaiercomponent in actie die een gestileerde schuif met de vertoning van de waardebel en interactieve functionaliteit in de Universele Redacteur tonen ](/help/edge/docs/forms/universal-editor/assets/custom-component-range-1.png)

## Veelgestelde vraag

* **als ik het stileren in zowel component.css als forms.css toevoegt, welke één prioriteit neemt?**
Wanneer de stijlen in zowel `component.css` als **forms.css** worden bepaald, `component.css` neemt prioriteit. Dit komt doordat stijlen op componentniveau specifieker zijn en algemene stijlen uit `forms.css` overschrijven.

* **Mijn douanecomponent is niet zichtbaar in de lijst van beschikbare componenten in Universele Redacteur. Hoe los ik dit op?**
Als uw aangepaste component niet wordt weergegeven, controleert u de volgende bestanden om te controleren of de component correct is geregistreerd:
   * **component-definition.json**: Verifieer dat de component behoorlijk wordt bepaald.
   * **component-filters.json**: verzeker de component in de aangewezen secties wordt toegestaan.
   * **component-models.json**: Bevestig dat het componentenmodel correct wordt gevormd.

## Aanbevolen procedures

* Het wordt geadviseerd aan [ opstelling een lokale ontwikkelomgeving van AEM ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#set-up-local-aem-development-environment) voor het ontwikkelen van douanestijlen en componenten plaatselijk.


## Extra byte

### Supported resourceType

| Veldtype | Resourcetype |
|--------------|------------------------------------------------------------------|
| tekstinvoer | core/fd/components/form/textinput/v1/textinput |
| getal-invoer | core/fd/components/form/numberinput/v1/numberinput |
| date-input | core/fd/components/form/datepicker/v1/datepicker |
| deelvenster | core/fd/components/form/panelcontainer/v1/panelcontainer |
| selectievakje | core/fd/components/form/checkbox/v1/checkbox |
| vervolgkeuzelijst | core/fd/components/form/dropdown/v1/dropdown |
| radiogroep | core/fd/components/form/radiobutton/v1/radiobutton |
| onbewerkte tekst | core/fd/components/form/text/v1/text |
| bestandsinvoer | core/fd/components/form/fileinput/v2/fileinput |
| email | core/fd/components/form/emailinput/v1/emailinput |
| image | core/fd/components/form/image/v1/image |
| knop | core/fd/components/form/button/v1/button |

### Ondersteunde veldtypen

De ondersteunde fieldTypes voor formulieren zijn:
* tekstinvoer
* getal-invoer
* date-input
* deelvenster
* selectievakje
* vervolgkeuzelijst
* radiogroep
* onbewerkte tekst
* bestandsinvoer
* email
* image
* knop

## Zie ook

{{universal-editor-see-also}}
