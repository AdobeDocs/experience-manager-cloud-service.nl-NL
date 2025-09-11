---
title: Aangepaste componenten maken voor een EDS-formulier
description: Aangepaste componenten maken voor een EDS-formulier
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 2bbe3f95-d5d0-4dc7-a983-7a20c93e2906
source-git-commit: 6a63b4f839516a2ebc1eec641eb36315efca6dd5
workflow-type: tm+mt
source-wordcount: '2120'
ht-degree: 0%

---


# Aangepaste formuliercomponent maken in adaptief formulierblok

Edge Delivery Services Forms biedt aanpassing, waardoor ontwikkelaars aan de voorzijde op maat aangepaste formulieronderdelen kunnen maken. Deze aangepaste componenten worden naadloos geïntegreerd in de WYSIWYG-ontwerpervaring, zodat formulierauteurs ze eenvoudig kunnen toevoegen, configureren en beheren in de formuliereditor. Met aangepaste componenten kunnen auteurs de functionaliteit verbeteren en tegelijkertijd zorgen voor een vloeiend en intuïtief ontwerpproces.

In dit document worden de stappen beschreven waarmee u aangepaste componenten kunt maken door de native HTML-formuliercomponenten op te maken om de gebruikerservaring te verbeteren en de visuele aantrekkingskracht van het formulier te vergroten.

## Overzicht van architectuur

De component van de douane voor het Blok van Forms volgt een **MVC (model-mening-Controlemechanisme)** architectuurpatroon:

### Model

- Gedefinieerd door het JSON-schema voor elke `field/component` .

- Authorable properties are specified in the corresponding JSON file (see block/form/models/form-components).

- Deze eigenschappen zijn beschikbaar voor auteurs in de formulierbuilder en worden doorgegeven aan de component als onderdeel van de velddefinitie (fd).

### Weergave

- De HTML-structuur voor elk veldtype wordt beschreven in formulierveldtypen.

- Dit is de basisstructuur voor de component die kan worden uitgebreid of gewijzigd.

- De basis-HTML-structuur voor elke OOTB-component wordt beschreven in formulierveldtypen.

### Controller/Component Logic

- Geïmplementeerd in JavaScript als OOTB (out-of-the-box) of aangepaste componenten.  - bevindt zich in `blocks/form/components` voor aangepaste componenten.

## OOTB-componenten

**OOTB (uit-van-de-doos)** componenten verstrekken de stichting voor douaneontwikkeling:

- OOTB-componenten bevinden zich in `blocks/form/models/form-components` .

- Elke component OOTB heeft een JSON- dossier bepalend zijn authorable eigenschappen (b.v., ` _text-input.json`, `_drop-down.json`).

- Deze eigenschappen zijn beschikbaar voor auteurs in de formulierbuilder en worden doorgegeven aan de component als onderdeel van de velddefinitie (fd).

- De basis-HTML-structuur voor elke OOTB-component wordt beschreven in formulierveldtypen.

Door een bestaande OOTB-component uit te breiden, kunt u de basisstructuur, het gedrag en de eigenschappen ervan opnieuw gebruiken en deze aan uw wensen aanpassen.

- Aangepaste componenten moeten een vooraf gedefinieerde set OOTB-componenten hebben.

- Het systeem identificeert welke OOTB-component wordt uitgebreid op basis van de eigenschap `viewType` in JSON van het veld.

- Het systeem houdt een register bij van toegestane aangepaste componentvarianten. Alleen variabelen in dit register kunnen worden gebruikt, bijvoorbeeld `customComponents[]` in `mappings.js` .

- Bij het weergeven van een formulier controleert het systeem de eigenschap variant of `:type/fd:viewType` en worden de corresponderende JS- en CSS-bestanden vanuit de map `blocks/form/components` geladen als deze overeenkomen met een geregistreerde aangepaste component.

- De aangepaste component wordt vervolgens toegepast op de basis-HTML-structuur van de OOTB-component, zodat u het gedrag en de weergave ervan kunt verbeteren of overschrijven.

## Structuur van aangepaste component

Om douanecomponenten tot stand te brengen, kunt u **folder CLI** gebruiken aan opstelling de dossiers en de omslagen die voor uw component worden vereist en dan code voor uw douanecomponent toevoegen.

- Aangepaste componenten bevinden zich in de map `blocks/form/components` .

- Elke aangepaste component moet in een eigen map worden geplaatst, die naar de component wordt genoemd, bijvoorbeeld kaarten. In de map moeten de volgende bestanden aanwezig zijn:

   - **_cards.json** - JSON dossier dat de componentendefinitie van een component OTB uitbreidt, bepaalt zijn authorable eigenschappen (modellen []) en inhoudsstructuur op lading (definities []).
   - **cards.js** - het dossier van JavaScript dat de belangrijkste logica omvat.
   - **cards.css** - facultatief, voor stijlen.

- De naam van de map en de JS/CSS-bestanden moeten overeenkomen.

### Velden in aangepaste componenten opnieuw gebruiken en uitbreiden

Volg bij het definiëren van velden in JSON van uw aangepaste component (voor elke veldgroep, basis, validatie, Help, enzovoort) de onderstaande tips en trucs voor onderhoudsgemak en consistentie:

- U kunt standaard-/gedeelde velden opnieuw gebruiken door te verwijzen naar bestaande gedeelde containers of velddefinities (bijvoorbeeld `../form-common/_basic-input-placeholder-fields.json#/fields`, `../form-common/_basic- validation-fields.json#/fields` ). Zo kunt u alle standaardopties overnemen zonder deze te dupliceren.

- Voeg alleen nieuwe of aangepaste velden expliciet toe aan uw container. Zo blijft het schema droog en gericht.

- Verwijder of vermijd het dupliceren van velden die al via verwijzingen zijn opgenomen. Definieer alleen velden die uniek zijn voor de logica van uw component.

- Referentie-Help-containers en andere gedeelde inhoud (bijvoorbeeld `../form-common/_help-container.json`) indien nodig voor consistentie en onderhoudsgemak.

>[!TIP]
>
> - Met dit patroon kunt u de logica in de toekomst eenvoudig bijwerken of uitbreiden en blijven uw aangepaste componenten consistent met de rest van het formuliersysteem.
> - Controleer altijd op bestaande gedeelde containers of velddefinities voordat u nieuwe containers toevoegt.

### Nieuwe eigenschappen definiëren voor aangepaste componenten

- Als u nieuwe eigenschappen voor uw aangepaste component van auteurs moet vastleggen, kunt u dit doen door een veld te definiëren in de `fields[]` -array van de component in de JSON van de component.

- De aangepaste component wordt geïdentificeerd met behulp van de eigenschap :type , die kan worden ingesteld als `fd:viewType` in het JSON-bestand (bijvoorbeeld `fd:viewType: cards` ). Hierdoor kan het systeem de juiste aangepaste component herkennen en laden en is dit dus verplicht voor aangepaste componenten

- Alle nieuwe eigenschappen die in de JSON-definitie worden toegevoegd, zijn in de velddefinitie beschikbaar als eigenschappen. `<propertyName>` in de JS-logica van uw component

## Aangepaste JavaScript-API voor componenten

De API van de Component van de Douane bepaalt hoe te om het gedrag, de verschijning, en de reactiviteit van uw douaneformuliercomponent te controleren.

### Decoratiefunctie

**decoreert** functie is het ingangspunt voor uw douanecomponent. De component wordt geïnitialiseerd, gekoppeld aan de JSON-definitie en u kunt de HTML-structuur en -gedrag van de component bewerken.

>[!NOTE]
>
> Het JavaScript-bestand van de aangepaste component moet een standaardfunctie exporteren als decoratief:

#### Functiehandtekening:

```javascript
export default function decorate(element, fieldJson, container, formId) {
// element: The HTML structure of the OOTB component you are extending
// fieldJson: The JSON field definition (all authorable properties)
// container: The parent element (fieldset or form)
// formId: The id of the form
// ... your logic here ...
}
```

Het kan:

- **wijzig het element**: Voeg gebeurtenisluisteraars toe, werk attributen bij, of injecteer extra prijsverhoging.

- **Toegang JSON eigenschappen**: Gebruik `fd.properties.<propertyName>` om waarden te lezen die in het schema JSON worden bepaald en hen binnen de componentenlogica toe te passen.

## Functie Abonneren

De **subscribe** functie laat uw component toe om op veranderingen in gebiedswaarden of douanegebeurtenissen te reageren. Hierdoor blijft de component synchroon met het gegevensmodel van het formulier en kan de gebruikersinterface van het formulier dynamisch worden bijgewerkt.

### Functiehandtekening:

```JavaScript
import { subscribe } from '../../rules/index.js';

export default function decorate(fieldDiv, fieldJson, container, formId) {
// Access custom properties defined in the JSON
const { initialText, finalText, time } = fieldJson?.properties;
// ... setup logic ...
subscribe(fieldDiv, formId, (_fieldDiv, fieldModel) => { fieldModel.subscribe(() => {
// React to custom event (e.g., resetCardOption)
// ... logic ...
}, 'resetCardOption');
});
}
```

Het kan:

- **Register een callback**: Het roepen **abonneert (element, formId, callback)** registreert uw callback om te lopen wanneer de gebiedsgegevens veranderen.Gebruik twee callback parameters:
   - **element**: Het element van HTML dat het gebied vertegenwoordigt.
   - **fieldModel**: Het voorwerp dat de staat en gebeurtenis APIs van het gebied vertegenwoordigt.

- **let op veranderingen of gebeurtenissen**: Gebruik `fieldModel.subscribe((event) => { ... }, 'eventName')` om logica uit te voeren wanneer een waarde verandert of een douanegebeurtenis wordt teweeggebracht. Het gebeurtenisobject bevat details over wat is gewijzigd.

## Een aangepaste component maken

In deze sectie, zult u het proces leren om de component van de a **kaartendouane** tot stand te brengen door OOTB radioknoopcomponent uit te breiden.

![ Aangepaste Component van de Kaart ](/help/edge/docs/forms/universal-editor/assets/cc-ue-card-component.png)

### &#x200B;1. Code-instelling

#### 1.1 Bestanden en mappen

De eerste stap is de opstelling van de noodzakelijke dossiers van de douanecomponent en het te telegraferen tot de code in de bewaarplaats. Dit proces wordt automatisch gedaan door **AEM Forms Scaffolder CLI**, die het sneller maakt om de noodzakelijke dossiers te scaffold en te telegraferen.

>[!VIDEO](https://video.tv.adobe.com/v/3474752)

1. Open de terminal en navigeer naar de hoofdmap van het formulierproject.
2. Voer de volgende opdrachten uit:

```bash
npm install
npm run create:custom-component
```

![ Scaffolder CLI ](/help/edge/docs/forms/universal-editor/assets/scaffolder-cli.png)

Het zal:

- **Vraag u om** uw nieuwe component te noemen. Gebruik in dit geval bijvoorbeeld kaarten.
- **Vraag u om** een basiscomponent (uitgezochte radiagroep) te kiezen

Hiermee maakt u alle benodigde mappen en bestanden, waaronder:

```
blocks/form/
└── components/
  └── cards/
    ├── cards.js
    └── cards.css
    └── _cards.json
```

En draai het omhoog met de rest code in de bewaarplaats zoals aangetoond in de output van CLI.
De volgende functies worden automatisch uitgevoerd:

- Hiermee voegt u kaarten toe aan de filters, zodat deze kunnen worden toegevoegd in Adaptief formulierblok.
- Werkt de lijst van gewenste personen van `mappings.js` bij om de nieuwe kaartcomponent te omvatten.
- Registreert de definitie van de kaartcomponent onder de **componenten van de Douane** lijst in Universele Redacteur.

>[!NOTE]
>
> U kunt ook een aangepaste component maken met de methode manual (verouderd). Zie de [ Handleiding of Verouderde Methode ](#manual-or-legacy-method-to-create-custom-component) om de sectie van de douanecomponent voor details tot stand te brengen.

#### 1.2 Component gebruiken in Universal Editor

1. **verfrist de Universele Redacteur**: Open uw vorm in de Universele Redacteur en vernieuw de pagina om het de recentste code van de bewaarplaats te verzekeren.

2. **voeg de Component van de Douane toe**

   1. Klik **toevoegen (+)** knoop op het vormcanvas.
   2. Blader naar de sectie Aangepaste componenten.
   3. Selecteer de pas gecreëerde **component van Kaarten** om het in uw vorm op te nemen.

      ![ Uitgezochte Component van de Douane ](/help/edge/docs/forms/universal-editor/assets/select-custom-component.png)

Aangezien er geen code aanwezig is binnen `cards.js` , wordt de aangepaste component weergegeven als een groep keuzerondjes.

#### 1.3 Lokaal voorvertonen en testen

Nu het formulier de aangepaste component bevat, kunt u het formulier als proxy instellen en er lokaal wijzigingen in aanbrengen. De wijzigingen worden dan weergegeven:

1. Ga naar uw terminal en voer `aem up` uit.

2. Open de proxyserver die u hebt gestart op `http://localhost:3000/{path-to-your-form}` (voorbeeld van pad: `/content/forms/af/custom-component-form`)


### &#x200B;2. Aangepast gedrag voor uw aangepaste component implementeren

#### 2.1 De aangepaste component opmaken

Laat een klasse **kaart** aan de component voor het stileren toevoegen en een beeld voor elke radio toevoegen, gebruik de hieronder code voor dit.

**Stijl de Component van de Douane die functie in cards.js gebruikt**

```javascript
import { createOptimizedPicture } from '../../../../scripts/aem.js';

export default function decorate(element, fieldJson, container, formId) { element.classList.add('card');
element.querySelectorAll('.radio-wrapper').forEach((radioWrapper) => { const image = createOptimizedPicture('https://main--afb--
jalagari.hlx.live/lab/images/card.png', 'card-image'); radioWrapper.appendChild(image);
});
return element;
}
```

**voeg RuntimeGedrag voor de Component van de Douane in cards.css** toe

```javascript
.card .radio-wrapper { min-width: 320px;
/* or whatever width fits your design */ max-width: 340px;
background: #fff;
border-radius: 16px;
box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
flex: 0 0 auto;
scroll-snap-align: start; padding: 24px 16px;
margin-bottom: 0;
position: relative;
transition: box-shadow 0.2s; display: flex;
align-items: flex-start; gap: 12px;
}
```

De kaartcomponent ziet er nu als volgt uit:

![ voeg kaart css en js ](/help/edge/docs/forms/universal-editor/assets/add-card-css.png) toe

#### 2.2 Dynamisch gedrag toevoegen met behulp van Abonnementsfunctie

Wanneer de vervolgkeuzelijst wordt gewijzigd, worden de kaarten opgehaald en ingesteld in de opsomming van de groep keuzerondjes. Maar dit wordt momenteel niet in de weergave verwerkt. Het wordt dus weergegeven zoals hieronder wordt getoond:

![ subscribe functie ](/help/edge/docs/forms/universal-editor/assets/card-subscribe.png)

Wanneer API wordt geroepen, plaatst het het gebiedsmodel en moet aan de veranderingen luisteren en dienovereenkomstig de mening teruggeven. Dit wordt bereikt gebruikend **onderteken functie**.

Laten we de weergavecode in de vorige stap omzetten naar een functie en deze binnen de subscribe-functie in `cards.js` aanroepen, zoals hieronder wordt getoond:

```javascript
import { createOptimizedPicture } from '../../../../scripts/aem.js';  

import { subscribe } from '../../rules/index.js';  
function createCard(element, enums) {  

  element.querySelectorAll('.radio-wrapper').forEach((radioWrapper, index) => {  

    if (enums[index]?.name) {  

      let label = radioWrapper.querySelector('label');  

      if (!label) {  

        label = document.createElement('label');  

        radioWrapper.appendChild(label);  

      }  

      label.textContent = enums[index]?.name;  

    }  

    const image = createOptimizedPicture(enums[index].image || 'https://main--afb--jalagari.hlx.page/lab/images/card.png', 'card-image');  

   radioWrapper.appendChild(image);  

  });  

}  
export default function decorate(element, fieldJson, container, formId) {  

    element.classList.add('card');  

    createCard(element, fieldJson.enum);  

    subscribe(element, formId, (fieldDiv, fieldModel) => {  

        fieldModel.subscribe((e) => {  

            const { payload } = e;  

            payload?.changes?.forEach((change) => {  

                if (change?.propertyName === 'enum') {  

                    createCard(element, change.currentValue);  

                }  

            });  

        });  

    });  
    return element;  

} 
```

**Gebruik onderteken Functie om de Veranderingen van de Gebeurtenis in cards.js te luisteren**

Wanneer u het vervolgkeuzemenu wijzigt, worden de kaarten gevuld, zoals hieronder wordt weergegeven:

![ subscribe functie ](/help/edge/docs/forms/universal-editor/assets/card-subscribe-final.png)

#### 2.3 Updates synchroniseren met veldmodel

Als u de weergavewijzigingen wilt synchroniseren met het veldmodel, moet u de waarde van de geselecteerde kaart instellen. Voeg dus de volgende gebeurtenislistener voor een wijziging toe aan cards.js, zoals hieronder wordt weergegeven:

**Gebruikend het ModelAPI van het Gebied in cards.js**

```javascript
 

import { createOptimizedPicture } from '../../../../scripts/aem.js';  

import { subscribe } from '../../rules/index.js';  

  

  

function createCard(element, enums) {  

  element.querySelectorAll('.radio-wrapper').forEach((radioWrapper, index) => {  

    if (enums[index]?.name) {  

      let label = radioWrapper.querySelector('label');  

      if (!label) {  

        label = document.createElement('label');  

        radioWrapper.appendChild(label);  

      }  

      label.textContent = enums[index]?.name;  

    }  

    radioWrapper.querySelector('input').dataset.index = index;  

    const image = createOptimizedPicture(enums[index].image || 'https://main--afb--jalagari.hlx.page/lab/images/card.png', 'card-image');  

   radioWrapper.appendChild(image);  

  });  

}  
export default function decorate(element, fieldJson, container, formId) {  

    element.classList.add('card');  
    createCard(element, fieldJson.enum);  

    subscribe(element, formId, (fieldDiv, fieldModel) => {  

        fieldModel.subscribe((e) => {  

            const { payload } = e;  

            payload?.changes?.forEach((change) => {  

                if (change?.propertyName === 'enum') {  

                    createCard(element, change.currentValue);  

                }  

            });  

        });  
        element.addEventListener('change', (e) => {  

            e.stopPropagation();  

            const value = fieldModel.enum?.[parseInt(e.target.dataset.index, 10)];  

            fieldModel.value = value.name;  

        });  

    });  

    return element;  
} 
```

De aangepaste kaartcomponent wordt nu weergegeven, zoals hieronder wordt getoond:

![ Aangepaste Component van de Kaart ](/help/edge/docs/forms/universal-editor/assets/cc-ue-card-component.png)

## Wijzigingen vastleggen en duwen

Nadat u de JavaScript en CSS voor uw aangepaste component hebt geïmplementeerd en lokaal hebt geverifieerd, past u de wijzigingen toe op uw Git-opslagplaats en drukt u deze door.

```bash
git add . && git commit -m "Add card custom component" && git push
```

U hebt in een paar eenvoudige stappen een complexe component voor de selectie van een aangepaste kaart gemaakt.

## Handmatige of verouderde methode om aangepaste component te maken

De oudere manier om dit te doen is de hieronder beschreven stappen manueel te volgen:

1. **kies een component OTB** om uit te breiden (b.v., knoop, drop-down, tekst-input, enz.). In dit geval breidt u de component Radio uit.

2. **creeer een omslag** in `blocks/form/components` met de naam van uw component (kaarten in dit geval).

3. **voeg een JS- dossier** met de zelfde naam toe:
   - `blocks/form/components/cards/cards.js`.

4. (Facultatief) **voeg een CSS dossier** voor douanestijlen toe:
   - `blocks/form/components/cards/cards.css.`

5. **bepaal een nieuw JSON- dossier** (b.v., ` _cards.json`) in de zelfde omslag zoals uw **component JS- dossier** (`blocks/form/components/cards/_cards.json`). This JSON should extend an existing component and in its definitions, set `fd:viewType` to your component&#39;s name (cards in this case):

   - Voeg voor alle veldgroepen (basis, validatie, Help, enzovoort) expliciet aangepaste velden toe.

6. **voer JS en CSS logica uit:**
   - Exporteer een standaardfunctie zoals hierboven beschreven.
   - Gebruik de **element** parameter om de structuur van basisHTML te wijzigen.
   - Gebruik **fieldJson** parameter indien nodig voor standaardgebiedsgegevens.
   - Het gebruik **onderschrijft** functie om aan gebiedsveranderingen of douanegebeurtenissen te luisteren indien nodig.

     >[!NOTE]
     >
     >Implementeer de logica JS en CSS voor uw aangepaste component zoals hierboven beschreven.

7. Registreer uw component als een variant in de vormbouwer en plaats het variantbezit of
   `fd:viewType/:type` in JSON aan de naam van uw component, bijvoorbeeld, voeg de `fd:viewType` waarde van `definitions[]` als kaarten aan de componentenserie van het voorwerp met `id="form` toe.

   ```javascript
   {
   "definitions": [
   {
   "title": "Cards",
   "id": "cards", "plugins": {
   "xwalk": {
   "page": {
   "resourceType":
   "core/fd/components/form/radiobutton/v1/radiobutton", "template": {
   "jcr:title": "Cards",
   "fieldType": "radio-button", "fd:viewType": "cards",
   "enabled": true, "visible": true}
   }
   } }
   }
   ]}
   ```

8. **Update mappings.js**: Voeg de naam van uw component aan **OOTBComponentDecorators** (voor OTB - stijlcomponenten) of **customComponents** lijst toe zodat wordt het erkend en door het systeem geladen.

   ```javascript
   let customComponents = ["cards"];
   const OOTBComponentDecorators = [];
   ```

9. **Update _form.json**: Voeg de naam van uw component aan de `filters.components` serie toe zodat het in auteursUI kan worden gelaten vallen.

   ```javascript
   "filters": [
   {
       "id": "form",
       "components": [ "cards"]}
       ]
   ```

10. **Update _component-definition.json**: In `models/_component-definition.json` werk de serie binnen de groep met `id custom-components` met een voorwerp op de volgende manier bij:

   ```javascript
   {
   "...":"../blocks/form/components/cards/_cards.json#/definitions"
   }
   ```

   Dit moet de verwijzing naar de nieuwe kaartcomponent verstrekken die met de rest van de componenten moet worden gebouwd

11. **stel het bouwstijl :json manuscript** in werking: voer `npm run build:json` uit om alle componentenJSON definities in één enkel dossier te compileren en samen te voegen dat van de server moet worden gediend. Dit zorgt ervoor dat het schema van uw nieuwe component wordt opgenomen in de samengevoegde uitvoer.

12. Leg uw wijzigingen vast en duw deze naar uw Git-opslagplaats.

Nu kunt u de aangepaste component aan het formulier toevoegen.

## Een samengestelde component maken

Een samengestelde component wordt gecreeerd door veelvoudige componenten te combineren.
Een samengestelde component Voorwaarden en Voorwaarden bestaat bijvoorbeeld uit een bovenliggend deelvenster dat het volgende bevat:

- Een tekstveld zonder opmaak voor het weergeven van de termen

- Een selectievakje voor het vastleggen van de gebruikersovereenkomst

Deze compositiestructuur wordt gedefinieerd als een sjabloon binnen het JSON-bestand van de desbetreffende component. In het volgende voorbeeld wordt getoond hoe u een sjabloon voor een component Voorwaarden definieert:

```javascript
{ 

  "definitions": [ 

    { 

      "title": "Terms and conditions", 

      "id": "tnc", 

      "plugins": { 

        "xwalk": { 

          "page": { 

            "resourceType": "core/fd/components/form/termsandconditions/v1/termsandconditions", 

            "template": { 

              "jcr:title": "Terms and conditions", 

              "fieldType": "panel", 

              "fd:viewType": "tnc", 

              "text": { 

                "value": "Text related to the terms and conditions come here.", 

                "sling:resourceType": "core/fd/components/form/text/v1/text", 

                "fieldType": "plain-text", 

                "textIsRich": true 

              }, 

              "approvalcheckbox": { 

                "name": "approvalcheckbox", 

                "jcr:title": "I agree to the terms & conditions.", 

                "sling:resourceType": "core/fd/components/form/checkbox/v1/checkbox", 

                "fieldType": "checkbox", 

                "required": true, 

                "type": "string", 

                "enum": [ 

                  "true" 

                ] 

              } 

            } 

          } 

        } 

      } 

    } 

  ], 

  ... 

} 
```

## Aanbevolen procedures

Houd rekening met de onderstaande punten voordat u uw eigen aangepaste component maakt:

- **houd uw geconcentreerde componentenlogica**: Slechts voeg/treedt toe met voeten wat noodzakelijk voor uw douanegedrag is

- **Hefboomwerking de basisstructuur**: Gebruik OOTB HTML als uw uitgangspunt

- **Gebruik authorable eigenschappen:** stel configureerbare opties via het schema JSON bloot

- **Namespace uw CSS**: Vermijd stijlbotsingen door unieke klassennamen te gebruiken

## Verwijzingen

- form-field-types: Base HTML-structuren en -eigenschappen voor alle veldtypen. [ klik hier ](/help/edge/docs/forms/eds-form-field-properties) om gedetailleerde structuren en eigenschappen van vormgebied te bekijken.

- **blokken/vorm/modellen/vorm-componenten**: OOTB en de definities van het douanecomponentenbezit.

- **blokken/vorm/componenten**: Plaats voor uw douanecomponenten. `blocks/form/components/countdown-timer/_countdown-timer.json` toont bijvoorbeeld hoe u een basiscomponent kunt uitbreiden en nieuwe eigenschappen kunt toevoegen.
