---
title: Modeldefinities, velden en componenttypen
description: In deze video ziet u voorbeelden van velden en componenttypen die de Universal Editor kan bewerken in de eigenschappentrack. Begrijp hoe u uw eigen app kunt instrumenteren door een modeldefinitie te maken en aan de component te koppelen.
exl-id: cb4567b8-ebec-477c-b7b9-53f25b533192
source-git-commit: 9f0a3bf5c8d839fa2ab6744c6fa7f97cc5fe8684
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 1%

---


# Modeldefinities, velden en componenttypen {#field-types}

In deze video ziet u voorbeelden van velden en componenttypen die de Universal Editor kan bewerken in de eigenschappentrack. Begrijp hoe u uw eigen app kunt instrumenteren door een modeldefinitie te maken en aan de component te koppelen.

## Overzicht {#overview}

Wanneer u uw eigen toepassingen aanpast voor gebruik met de Universal Editor, moet u de componenten instrumenten en definiëren welke velden en componenttypen zij kunnen manipuleren in de eigenschappentrack van de editor. U doet dit door een model te creëren en met dat van de component te verbinden.

Dit document biedt een overzicht van een modeldefinitie en van de velden en componenttypen waarover u beschikt, samen met voorbeeldconfiguraties.

>[!TIP]
>
>Als u niet bekend bent met het instrumenteren van uw app voor de Universal Editor, raadpleegt u het document [Overzicht van de Universal Editor voor AEM ontwikkelaars.](/help/implementing/universal-editor/developer-overview.md)

## Modeldefinitiestructuur {#model-structure}

Om een component te configureren via de eigenschappen rail in de Universal Editor moet een modeldefinitie bestaan en aan de component zijn gekoppeld.

De modeldefinitie is een JSON-structuur, te beginnen met een array van modellen.

```json
[
  {
    "id": "model-id",        // must be unique
    "fields": []             // array of fields which shall be rendered in the properties rail
  }
]
```

Zie de **[Velden](#fields)** voor meer informatie over het definiëren van uw `fields` array.

Als u de modeldefinitie met een component wilt gebruiken, `data-aue-model` kan worden gebruikt.

```html
<div data-aue-resource="urn:datasource:/content/path" data-aue-type="component"  data-aue-model="model-id">Click me</div>
```

## Modeldefinitie laden {#loading-model}

Wanneer een model is gemaakt, kan ernaar worden verwezen als een extern bestand.

```html
<script type="application/vnd.adobe.aue.model+json" src="<url-of-model-definition>"></script>
```

U kunt het model ook inline definiëren.

```html
<script type="application/vnd.adobe.aue.model+json">
  { ... model definition ... }
</script>
```

## Velden {#fields}

Een veldobject heeft de volgende typedefinitie.

| Configuratie | Type waarde | Beschrijving | Vereist |
|---|---|---|---|
| `component` | `ComponentType` | Renderer van de component | Ja |
| `name` | `string` | Eigenschap waar de gegevens moeten worden gecontinueerd | Ja |
| `label` | `FieldLabel` | Label van het veld | Ja |
| `description` | `FieldDescription` | Beschrijving van het veld | Nee |
| `placeholder` | `string` | Plaatsaanduiding voor het veld | Nee |
| `value` | `FieldValue` | Standaardwaarde | Nee |
| `valueType` | `ValueType` | Standaardvalidatie, kan `string`, `string[]`, `number`, `date`, `boolean` | Nee |
| `required` | `boolean` | Is het vereiste veld | Nee |
| `readOnly` | `boolean` | Is het veld alleen-lezen | Nee |
| `hidden` | `boolean` | Is het veld standaard verborgen | Nee |
| `condition` | `RulesLogic` | Regel om het gebied te tonen of te verbergen dat op een [conditie](/help/implementing/universal-editor/customizing.md#conditionally-hide) | Nee |
| `multi` | `boolean` | Is het veld een veld met meerdere velden | Nee |
| `validation` | `ValidationType` | Validatieregel(s) voor het veld | Nee |
| `raw` | `unknown` | Onbewerkte gegevens die door de component kunnen worden gebruikt | Nee |

### Componenttypen {#component-types}

Hieronder vindt u de componenttypen die u kunt gebruiken voor het weergeven van velden.

| Beschrijving | Componenttype |
|---|---|
| [AEM](#aem-tag) | `aem-tag` |
| [Inhoud AEM](#aem-content) | `aem-content` |
| [Boolean](#boolean) | `boolean` |
| [Groep selectievakjes](#checkbox-group) | `checkbox-group` |
| [Container](#container) | `container` |
| [Datum en tijd](#date-time) | `date-time` |
| [Multiselect](#multiselect) | `multiselect` |
| [Getal](#number) | `number` |
| [Groep keuzerondjes](#radio-group) | `radio-group` |
| [Referentie](#reference) | `reference` |
| [RTF](#rich-text) | `rich-text` |
| [Selecteren](#select) | `select` |
| [Tab](#tab) | `tab` |
| [Tekst](#text) | `text` |

#### AEM {#aem-tag}

Een AEM-tagcomponenttype maakt een AEM tagkiezer mogelijk, die kan worden gebruikt om tags aan de component te koppelen.

>[!BEGINTABS]

>[!TAB Monster]

```json
{
  "id": "aem-tag-picker",
  "fields": [
    {
      "component": "aem-tag",
      "label": "AEM Tag Picker",
      "name": "cq:tags",
      "valueType": "string"
    }
  ]
}
```

>[!TAB Schermafbeelding]

![Screenshot van AEM type tagcomponent](assets/component-types/aem-tag-picker.png)

>[!ENDTABS]

#### Inhoud AEM {#aem-content}

Een AEM type inhoudcomponent laat een AEM inhoudkiezer toe, die kan worden gebruikt om inhoudsverwijzingen te plaatsen.

>[!BEGINTABS]

>[!TAB Monster]

```json
{
  "id": "aem-content-picker",
  "fields": [
    {
      "component": "aem-content",
      "name": "reference",
      "value": "",
      "label": "AEM Content Picker",
      "valueType": "string"
    }
  ]
}
```

>[!TAB Schermafbeelding]

![Screenshot van AEM type inhoudcomponent](assets/component-types/aem-content-picker.png)

>[!ENDTABS]

#### Boolean {#boolean}

Een type van booleaanse component slaat een eenvoudige waar/vals waarde op die als knevel wordt teruggegeven. Het biedt een aanvullend validatietype aan.

| Validatietype | Type waarde | Beschrijving | Vereist |
|---|---|---|---|
| `customErrorMsg` | `string` | Bericht dat zal tonen als de ingevoerde waarde geen booleaanse waarde is | Nee |

>[!BEGINTABS]

>[!TAB Voorbeeld 1]

```json
{
  "id": "boolean",
  "fields": [
    {
      "component": "boolean",
      "label": "Boolean",
      "name": "boolean",
      "valueType": "boolean"
    }
  ]
}
```

>[!TAB Voorbeeld 2]

```json
{
  "id": "another-boolean",
  "fields": [
    {
      "component": "boolean",
      "label": "Boolean",
      "name": "boolean",
      "valueType": "boolean",
      "validation": {
        "customErrorMsg": "Think, McFly. Think!"
      }
    }
  ]
}
```

>[!TAB Schermafbeelding]

![Screenshot van het type Boolean-component](assets/component-types/boolean.png)

>[!ENDTABS]

#### Groep selectievakjes {#checkbox-group}

Net als bij een booleaanse component staat een componenttype voor selectievakjes het selecteren van meerdere true/false-items toe, die als meerdere selectievakjes worden weergegeven.

>[!BEGINTABS]

>[!TAB Monster]

```json
{
  "id": "checkbox-group",
  "fields": [
    {
      "component": "checkbox-group",
      "label": "Checkbox Group",
      "name": "checkbox",
      "valueType": "string[]",
      "options": [
        { "name": "Option 1", "value": "option1" },
        { "name": "Option 2", "value": "option2" }
      ]
    }
  ]
}
```

>[!TAB Schermafbeelding]

![Screenshot van het componenttype van de checkbox groep](assets/component-types/checkbox-group.png)

>[!ENDTABS]

#### Container {#container}

Met een containercomponenttype kunnen componenten worden gegroepeerd. Het biedt een extra configuratie aan.

| Configuratie | Type waarde | Beschrijving | Vereist |
|---|---|---|---|
| `collapsible` | `boolean` | Is de container inklapbaar | Nee |

>[!BEGINTABS]

>[!TAB Monster]

```json
 {
  "id": "container",
  "fields": [
    {
      "component": "container",
      "label": "Container",
      "name": "container",
      "valueType": "string",
      "collapsible": true,
      "fields": [
        {
          "component": "text-input",
          "label": "Simple Text 1",
          "name": "text",
          "valueType": "string"
        },
        {
          "component": "text-input",
          "label": "Simple Text 2",
          "name": "text2",
          "valueType": "string"
        }
      ]
    }
  ]
}
```

>[!TAB Schermafbeelding]

![Screenshot van het type containercomponent](assets/component-types/container.png)

#### Inhoudsfragment {#content-fragment}

De kiezer voor het inhoudsfragment kan worden gebruikt om een [Inhoudsfragment](/help/sites-cloud/authoring/fragments/content-fragments.md) en de variaties ervan (indien nodig). Het biedt een extra configuratie aan.

| Configuratie | Type waarde | Beschrijving | Vereist |
|---|---|---|---|
| `variationName` | `string` | Naam variabele waarin de geselecteerde variatie wordt opgeslagen. Indien ongedefinieerd, wordt geen variatietekiezer weergegeven | Nee |

>[!BEGINTABS]

>[!TAB Voorbeeld 1]

```json
[
  {
    "id": "aem-content-fragment",
    "fields": [
      {
        "component": "aem-content-fragment",
        "name": "picker",
        "label": "Content Fragment Picker",
        "valueType": "string",
        "variationName": "contentFragmentVariation"
      }
    ]
  }
]
```

>[!TAB Schermafbeelding]

![Screenshot van de kiezer voor inhoudsfragment](assets/component-types/aem-content-fragment.png)

>[!ENDTABS]

#### Datum en tijd {#date-time}

Met een componenttype voor datumtijd kunt u een datum, tijd of combinatie daarvan opgeven. Het biedt extra configuraties aan.

| Configuratie | Type waarde | Beschrijving | Vereist |
|---|---|---|---|
| `displayFormat` | `string` | Indeling waarmee de datumtekenreeks moet worden weergegeven | Ja |
| `valueFormat` | `string` | Indeling waarin de datumtekenreeks moet worden opgeslagen | Ja |

Het biedt ook een aanvullend validatietype.

| Validatietype | Type waarde | Beschrijving | Vereist |
|---|---|---|---|
| `customErrorMsg` | `string` | Bericht dat wordt weergegeven als `valueFormat` is niet voldaan | Nee |

>[!BEGINTABS]

>[!TAB Voorbeeld 1]

```json
{
  "id": "date-time",
  "fields": [
    {
      "component": "date-time",
      "label": "Date & Time",
      "name": "date",
      "valueType": "date"
    }
  ]
}
```

>[!TAB Voorbeeld 2]

```json
{
  "id": "another-date-time",
  "fields": [
    {
      "component": "date-time",
       "valueType": "date-time",
      "name": "field1",
      "label": "Date Time",
      "description": "This is a date time field that stores both date and time.",
      "required": true,
      "placeholder": "YYYY-MM-DD HH:mm:ss",
      "displayFormat": null,
      "valueFormat": null,
      "validation": {
        "customErrorMsg": "Marty! You have to come back with me!"
      }
    },
    {
      "component": "date-time",
      "valueType": "date",
      "name": "field2",
      "label": "Another Date Time",
      "description": "This is another date time field that only stores the date.",
      "required": true,
      "placeholder": "YYYY-MM-DD",
      "displayFormat": null,
      "valueFormat": null,
      "validation": {
        "customErrorMsg": "Back to the future!"
      }
    },
    {
      "component": "date-time",
      "valueType": "time",
      "name": "field3",
      "label": "Yet Another Date Time",
      "description": "This is another date time field that only stores the time.",
      "required": true,
      "placeholder": "HH:mm:ss",
      "displayFormat": null,
      "valueFormat": null,
      "validation": {
        "customErrorMsg": "Great Scott!"
      }
    }
  ]
}
```

>[!TAB Schermafbeelding]

![Screenshot van componenttype voor datumtijd](assets/component-types/date-time.png)

>[!ENDTABS]

#### Ervaar fragment {#experience-fragment}

Met de fragmentkiezer voor ervaring kunt u een [Ervaar fragment](/help/sites-cloud/authoring/fragments/experience-fragments.md) en de variaties ervan (indien nodig). Het biedt een extra configuratie aan.

| Configuratie | Type waarde | Beschrijving | Vereist |
|---|---|---|---|
| `variationName` | `string` | Naam variabele waarin de geselecteerde variatie wordt opgeslagen. Indien ongedefinieerd, wordt geen variatietekiezer weergegeven | Nee |

>[!BEGINTABS]

>[!TAB Voorbeeld 1]

```json
[
  {
    "id": "aem-experience-fragment",
    "fields": [
      {
        "component": "aem-experience-fragment",
        "name": "picker",
        "label": "Experience Fragment Picker",
        "valueType": "string",
        "variationName": "experienceFragmentVariation"
      }
    ]
  }
]
```

>[!TAB Schermafbeelding]

![Schermafbeelding van de fragmentkiezer van Experience](assets/component-types/aem-experience-fragment.png)

>[!ENDTABS]


#### Multiselect {#multiselect}

Een multiselect componenttype stelt veelvoudige punten voor selectie in een drop-down met inbegrip van de capaciteit voor om de selecteerbare elementen te groeperen.

>[!BEGINTABS]

>[!TAB Voorbeeld 1]

```json
{
  "id": "multiselect",
  "fields": [
    {
      "component": "multiselect",
      "name": "multiselect",
      "label": "Multi Select",
      "valueType": "string",
      "options": [
        { "name": "Option 1", "value": "option1" },
        { "name": "Option 2", "value": "option2" }
      ]
    }
  ]
}
```

>[!TAB Voorbeeld 2]

```json
{
  "id": "multiselect-grouped",
  "fields": [
    {
      "component": "multiselect",
      "name": "property",
      "label": "Multiselect field",
      "valueType": "string",
      "required": true,
      "maxSize": 2,
      "options": [
        {
          "name": "Theme",
          "children": [
            { "name": "Light", "value": "light" },
            { "name": "Dark",  "value": "dark" }
          ]
        },
        {
          "name": "Type",
          "children": [
            { "name": "Alpha", "value": "alpha" },
            { "name": "Beta", "value": "beta" },
            { "name": "Gamma", "value": "gamma" }
          ]
        }
      ]
    }
  ]
}
```

>[!TAB Screenshots]

![Screenshot van multiselect componenttype](assets/component-types/multiselect.png)
![Screenshot van multiselect componenttype met groepering](assets/component-types/multiselect-group.png)

>[!ENDTABS]

#### Getal {#number}

Een type van aantalcomponent staat voor de input van een aantal toe. Er zijn aanvullende validatietypen.

| Validatietype | Type waarde | Beschrijving | Vereist |
|---|---|---|---|
| `numberMin` | `number` | Minimaal toegestane aantal | Nee |
| `numberMax` | `number` | Maximaal toegestaan aantal | Nee |
| `customErrorMsg` | `string` | Bericht dat wordt weergegeven als `numberMin` of `numberMax` is niet voldaan | Nee |

>[!BEGINTABS]

>[!TAB Voorbeeld 1]

```json
{
  "id": "number",
  "fields": [
    {
      "component": "number",
      "name": "number",
      "label": "Number",
      "valueType": "number",
      "value": 0
    }
  ]
}
```

>[!TAB Voorbeeld 2]

```json
{
  "id": "another-number",
  "fields": [
   {
      "component": "number",
      "valueType": "number",
      "name": "field1",
      "label": "Number Field",
      "description": "This is a number field.",
      "required": true,
      "placeholder": null,
      "validation": {
        "numberMin": 0,
        "numberMax": 88,
        "customErrorMsg": "You also need 1.21 gigawatts."
      }
    }
  ]
}
```

>[!TAB Schermafbeelding]

![Screenshot van type Number-component](assets/component-types/number.png)

>[!ENDTABS]

#### Groep keuzerondjes {#radio-group}

Een componenttype voor een groep keuzerondjes maakt het mogelijk om meerdere opties die als een groep worden gerenderd, uit te sluiten, net als een groep selectievakjes.

>[!BEGINTABS]

>[!TAB Monster]

```json
{
  "id": "radio-group",
  "fields": [
    {
      "component": "radio-group",
      "label": "Radio Group",
      "name": "radio",
      "valueType": "string",
      "options": [
        { "name": "Option 1", "value": "option1" },
        { "name": "Option 2", "value": "option2" }
      ]
    }
  ]
}
```

>[!TAB Schermafbeelding]

![Screenshot van het componenttype van de groep keuzerondjes](assets/component-types/radio.png)

>[!ENDTABS]

#### Referentie {#reference}

Een type referentiecomponent maakt een verwijzing naar een ander gegevensobject van het huidige object mogelijk.

>[!BEGINTABS]

>[!TAB Monster]

```json
{
  "id": "reference",
  "fields": [
    {
      "component": "reference",
      "label": "Reference",
      "name": "reference",
      "valueType": "string"
    }
  ]
}
```

>[!TAB Schermafbeelding]

![Screenshot van referentiecomponenttype](assets/component-types/reference.png)

>[!ENDTABS]

#### RTF {#rich-text}

RTF-tekst staat toe dat tekst met meerdere regels wordt ingevoerd. Er zijn aanvullende validatietypen.

| Validatietype | Type waarde | Beschrijving | Vereist |
|---|---|---|---|
| `maxSize` | `number` | Maximum aantal toegestane tekens | Nee |
| `customErrorMsg` | `string` | Bericht dat wordt weergegeven als `maxSize` is overschreden | Nee |

>[!BEGINTABS]

>[!TAB Voorbeeld 1]

```json
{
  "id": "richtext",
  "fields": [
    {
      "component": "richtext",
      "name": "rte",
      "label": "Rich Text",
      "valueType": "string"
    }
  ]
}
```

>[!TAB Voorbeeld 2]

```json
{
  "id": "another-richtext",
  "fields": [
    {
      "component": "richtext",
      "name": "rte",
      "label": "Rich Text",
      "valueType": "string",
      "validation": {
        "maxSize": 1000,
        "customErrorMsg": "That's about as funny as a screen door on a battleship."
      }
    }
  ]
}
```

>[!TAB Schermafbeelding]

![Screenshot van het type tekstgebiedcomponent](assets/component-types/richtext.png)

>[!ENDTABS]

#### Selecteren {#select}

Met een componenttype select kunt u één optie selecteren in een lijst met vooraf gedefinieerde opties in een vervolgkeuzemenu.

>[!BEGINTABS]

>[!TAB Monster]

```json
{
  "id": "select",
  "fields": [
    {
      "component": "select",
      "label": "Select",
      "name": "select",
      "valueType": "string",
      "options": [
        { "name": "Option 1", "value": "option1" },
        { "name": "Option 2", "value": "option2" }
      ]
    }
  ]
}
```

>[!TAB Schermafbeelding]

![Screenshot van select componenttype](assets/component-types/select.png)

>[!ENDTABS]

#### Tab {#tab}

Met een componenttype tab kunt u andere invoervelden groeperen op meerdere tabbladen om de indeling van de auteurs te verbeteren.

A `tab` definitie kan worden beschouwd als een scheidingsteken in de array van `fields`. Alles wat na een `tab` wordt op dat tabblad geplaatst totdat er een nieuwe `tab` aangetroffen, waarbij de volgende items op het nieuwe tabblad worden geplaatst.

Als u items boven alle tabbladen wilt weergeven, moet u deze vóór alle tabbladen definiëren.

>[!BEGINTABS]

>[!TAB Monster]

```json
{
  "id": "tab",
  "fields": [
    {
      "component": "tab",
      "label": "Tab 1",
      "name": "tab1"
    },
    {
      "component": "text-input",
      "label": "Text 1",
      "name": "text1",
      "valueType": "string"
    },
    {
      "component": "tab",
      "label": "Tab 2",
      "name": "tab2"
    },
    {
      "component": "text-input",
      "label": "Text 2",
      "name": "text2",
      "valueType": "string"
    }
  ]
}
```

>[!TAB Schermafbeelding]

![Screenshot van type component tab](assets/component-types/tab.png)

>[!ENDTABS]

#### Tekst {#text}

Met tekst kunt u één regel tekst invoeren.  Het bevat aanvullende validatietypen.

| Validatietype | Type waarde | Beschrijving | Vereist |
|---|---|---|---|
| `minLength` | `number` | Minimum aantal toegestane tekens | Nee |
| `maxLength` | `number` | Maximaal aantal tekens toegestaan | Nee |
| `regExp` | `string` | Gewone expressie die moet overeenkomen met de invoertekst | Nee |
| `customErrorMsg` | `string` | Bericht dat wordt weergegeven als `minLength`, `maxLength`, en/of `regExp` is/is overtreden | Nee |

>[!BEGINTABS]

>[!TAB Voorbeeld 1]

```json
{
  "id": "simpletext",
  "fields": [
    {
      "component": "text",
      "name": "text",
      "label": "Simple Text",
      "valueType": "string"
    }
  ]
}
```

>[!TAB Voorbeeld 2]

```json
{
  "id": "another simpletext",
  "fields": [
    {
      "component": "text",
      "name": "text",
      "label": "Simple Text",
      "valueType": "string",
      "description": "This is a text input with validation.",
      "required": true,
      "validation": {
        "minLength": 1955,
        "maxLength": 1985,
        "regExp": "^foo:.*",
        "customErrorMsg": "Why don't you make like a tree and get outta here?"
      }
    }
  ]
}
```

>[!TAB Schermafbeelding]

![Schermafbeelding van type tekstcomponent](assets/component-types/simpletext.png)

>[!ENDTABS]
