---
title: Hoe kan ik JSON-schema ontwerpen voor een adaptief formulier?
description: Leer een JSON-schema voor een adaptief formulier te maken en een adaptief formulier te maken op basis van het schema om klachtengegevens over het schema te produceren.
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Beginner, Intermediate
exl-id: 8eeb9c5e-6866-4bfe-b922-1f028728ef0d
source-git-commit: 494e90bd5822495f0619e8ebf55f373a26a3ffe6
workflow-type: tm+mt
source-wordcount: '1377'
ht-degree: 0%

---

# JSON-schema ontwerpen voor een adaptief formulier {#creating-adaptive-forms-using-json-schema}


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| Kernonderdelen | [Klik hier](/help/forms/adaptive-form-core-components-json-schema-form-model.md) |
| Stichting | Dit artikel |

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/creating-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adaptive-form-json-schema-form-model.html) |
| AEM as a Cloud Service | Dit artikel |


## Vereisten {#prerequisites}

Voor het ontwerpen van een adaptief formulier met behulp van een JSON-schema als formuliermodel is basiskennis van het JSON-schema vereist. Het wordt aanbevolen de volgende inhoud vóór dit artikel te lezen.

* [Een adaptief formulier maken](creating-adaptive-form.md)
* [JSON Schema](https://json-schema.org/)

## Een JSON-schema gebruiken als formuliermodel  {#using-a-json-schema-as-form-model}

Adobe Experience Manager Forms ondersteunt het maken van een adaptief formulier met een bestaand JSON-schema als formuliermodel. Dit JSON-schema vertegenwoordigt de structuur waarin gegevens worden geproduceerd of verbruikt door het back-end systeem in uw organisatie. Het JSON-schema dat u gebruikt, moet compatibel zijn met [v4-specificaties](https://json-schema.org/draft-04/schema).

De belangrijkste eigenschappen van het gebruiken van een Schema JSON zijn:

* De structuur van JSON wordt als een structuur weergegeven op het tabblad Inhoudszoeker in de ontwerpmodus voor een adaptief formulier. U kunt een element slepen van de JSON-hiërarchie naar het adaptieve formulier.
* U kunt het formulier vooraf invullen met JSON dat voldoet aan het bijbehorende schema.
* Bij verzending worden de gegevens die door de gebruiker zijn ingevoerd, verzonden als JSON die wordt uitgelijnd met het bijbehorende schema.
* U kunt het formulier ook maken op basis van het JSON-schema volgens de specificaties van het dialoogvenster [Versie 2012-20](https://json-schema.org/draft/2020-12/release-notes).

Een JSON-schema bestaat uit eenvoudige en complexe elementtypen. De elementen hebben attributen die regels aan het element toevoegen. Wanneer deze elementen en kenmerken naar een adaptief formulier worden gesleept, worden ze automatisch toegewezen aan de corresponderende component Adaptief formulier.

Deze toewijzing van JSON-elementen met componenten Adaptief formulier ziet er als volgt uit:

```json
"birthDate": {
              "type": "string",
              "format": "date",
              "pattern": "date{DD MMMM, YYYY}",
              "aem:affKeyword": [
                "DOB",
                "Date of Birth"
              ],
              "description": "Date of birth in DD MMMM, YYYY",
              "aem:afProperties": {
                "displayPictureClause": "date{DD MMMM, YYYY}",
                "displayPatternType": "date{DD MMMM, YYYY}",
                "validationPatternType": "date{DD MMMM, YYYY}",
                "validatePictureClause": "date{DD MMMM, YYYY}",
                "validatePictureClauseMessage": "Date must be in DD MMMM, YYYY format."
              }
  }
```

<table>
 <tbody>
  <tr>
   <th><strong>JSON-element, -eigenschappen of -kenmerken</strong></th>
   <th><strong>Component Adaptief formulier</strong></th>
  </tr>
  <tr>
   <td><p>Tekenreekseigenschappen met de beperking enum en enumNames</p> <p>Syntaxis,</p> <p> <code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"enum" : ["M", "F"]</code></p> <p><code>"enumNames" : ["Male", "Female"]</code></p> <p><code>}</code></p> <p> </p> </td>
   <td><p>Onderdeel vervolgkeuzelijst:</p>
    <ul>
     <li>Waarden die worden vermeld in enumNames, worden weergegeven in het vak drop.</li>
     <li>Waarden die in de opsomming staan, worden gebruikt voor de berekening.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Tekenreekseigenschap met indelingsbeperking. Bijvoorbeeld e-mail en datum.</p> <p>Syntaxis,</p> <p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"format" : "email"</code></p> <p><code>}</code></p> <p> </p> </td>
   <td>
    <ul>
     <li>E-mailcomponent wordt toegewezen wanneer het type tekenreeks en indeling e-mail is.</li>
     <li>TextBox-component met validatie wordt toegewezen wanneer het type tekenreeks en notatie hostnaam is.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>}</code></p> </td>
   <td><br /> <br /> Tekstveld<br /> <br /> <br /> </td>
  </tr>
  <tr>
   <td>number, eigenschap<br /> </td>
   <td>Numeriek veld met subtype ingesteld op zwevend<br /> </td>
  </tr>
  <tr>
   <td>integer, eigenschap<br /> </td>
   <td>Numeriek veld met subtype ingesteld op geheel getal<br /> </td>
  </tr>
  <tr>
   <td>boolean, eigenschap<br /> </td>
   <td>Overschakelen<br /> </td>
  </tr>
  <tr>
   <td>objecteigenschap<br /> </td>
   <td>Deelvenster<br /> </td>
  </tr>
  <tr>
   <td>array, eigenschap</td>
   <td>Herhaalbaar deelvenster met min en max. gelijk aan minItems respectievelijk maxItems. Alleen homogene arrays worden ondersteund. De itembeperking moet dus een object zijn en geen array.<br /> </td>
  </tr>
 </tbody>
</table>

### Algemene schemaeigenschappen {#common-schema-properties}

Het adaptieve formulier gebruikt informatie die beschikbaar is in het JSON-schema om elk gegenereerd veld in kaart te brengen. Met name:

* De `title` Deze eigenschap fungeert als label voor de componenten Adaptief formulier.
* De `description` wordt ingesteld als lange beschrijving voor een component Adaptief formulier.
* De `default` Deze eigenschap fungeert als de beginwaarde van een veld Adaptief formulier.
* De `maxLength` eigenschap is ingesteld als `maxlength` kenmerk van de tekstveldcomponent.
* De `minimum`, `maximum`, `exclusiveMinimum`, en `exclusiveMaximum` worden gebruikt voor de component Numeriek vak.
* Om waaier voor te steunen `DatePicker component` aanvullende JSON-schemaeigenschappen `minDate` en `maxDate` worden opgegeven.
* De `minItems` en `maxItems` worden gebruikt om het aantal items/velden te beperken dat kan worden toegevoegd aan of verwijderd uit een deelvenstercomponent.
* De `readOnly` eigenschap stelt de `readonly` kenmerk van een component Adaptief formulier.
* De `required` geeft de eigenschap aan dat het veld Adaptief formulier verplicht is, terwijl in het deelvenster (waar het type object is) de uiteindelijke JSON-gegevens velden hebben met een lege waarde die overeenkomt met dat object.
* De `pattern` Deze eigenschap wordt ingesteld als het validatiepatroon (reguliere expressie) in Adaptief formulier.
* De extensie van het JSON-schemabestand moet .schema.json blijven. Bijvoorbeeld: &lt;filename>.schema.json.

## Voorbeeld JSON-schema {#sample-json-schema}

>[!BEGINTABS]

>[!TAB JSON Schema v4]

```json
{
"$schema": "https://json-schema.org/draft-04/schema#",
"definitions": {
  "employee": {
  "type": "object",
  "properties": {
    "userName": {
     "type": "string"
   },
    "dateOfBirth": {
     "type": "string",
     "format": "date"
    },
    "email": {
    "type": "string",
    "format": "email"
    },
    "language": {
     "type": "string"
   },
    "personalDetails": {
     "$ref": "#/definitions/personalDetails"
   },
    "projectDetails": {
     "$ref": "#/definitions/projectDetails"
    }
  },
  "required": [
   "userName",
   "dateOfBirth",
   "language"
  ]
  },
    "personalDetails": {
   "type": "object",
  "properties": {
     "GeneralDetails": {
    "$ref": "#/definitions/GeneralDetails"
   },
    "Family": {
     "$ref": "#/definitions/Family"
    },
    "Income": {
     "$ref": "#/definitions/Income"
   }
   }
     },
  "projectDetails": {
   "type": "array",
   "items": {
   "properties": {
   "name": {
    "type": "string"
   },
   "age": {
    "type": "number"
   },
   "projects": {
    "$ref": "#/definitions/projects"
   }
  }
 },
 "minItems": 1,
 "maxItems": 4
},
"projects": {
 "type": "array",
 "items": {
  "properties": {
   "name": {
    "type": "string"
   },
   "age": {
    "type": "number"
   },
   "projectsAdditional": {
    "$ref": "#/definitions/projectsAdditional"
   }
  }
 },
 "minItems": 1,
 "maxItems": 4
},
"projectsAdditional": {
 "type": "array",
 "items": {
  "properties": {
   "Additional_name": {
    "type": "string"
   },
   "Additional_areacode": {
    "type": "number"
   }
  }
 },
 "minItems": 1,
 "maxItems": 4
},
"GeneralDetails": {
 "type": "object",
 "properties": {
  "age": {
   "type": "number"
  },
  "married": {
   "type": "boolean"
  },
  "phone": {
   "type": "number",
   "aem:afProperties": {
    "sling:resourceType": "/libs/fd/af/components/guidetelephone",
    "guideNodeClass": "guideTelephone"
   }
  },
  "address": {
   "type": "string"
  }
 }
},
"Family": {
 "type": "object",
 "properties": {
  "spouse": {
   "$ref": "#/definitions/spouse"
  },
  "kids": {
   "$ref": "#/definitions/kids"
  }
 }
},
"Income": {
 "type": "object",
 "properties": {
  "monthly": {
   "type": "number"
  },
  "yearly": {
   "type": "number"
  }
 }
},
"spouse": {
 "type": "object",
 "properties": {
  "name": {
   "type": "string"
  },
  "Income": {
   "$ref": "#/definitions/Income"
  }
 }
},
"kids": {
 "type": "array",
 "items": {
  "properties": {
   "name": {
    "type": "string"
   },
   "age": {
    "type": "number"
   }
  }
 },
 "minItems": 1,
 "maxItems": 4
}
},
"type": "object",
"properties": {
"employee": {
 "$ref": "#/definitions/employee"
}
}
}
```


>[!TAB JSON Schema 2012-20]


```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://example.com/employee.schema.json",
  "$defs": {
    "employee": {
      "type": "object",
      "properties": {
        "userName": {
          "type": "string"
        },
        "dateOfBirth": {
          "type": "string",
          "format": "date"
        },
        "email": {
          "type": "string",
          "format": "email"
        },
        "language": {
          "type": "string"
        },
        "personalDetails": {
          "$ref": "#/$defs/personalDetails"
        },
        "projectDetails": {
          "$ref": "#/$defs/projectDetails"
        }
      },
      "required": [
        "userName",
        "dateOfBirth",
        "language"
      ]
    },
    "personalDetails": {
      "type": "object",
      "properties": {
        "GeneralDetails": {
          "$ref": "#/$defs/GeneralDetails"
        },
        "Family": {
          "$ref": "#/$defs/Family"
        },
        "Income": {
          "$ref": "#/$defs/Income"
        }
      }
    },
    "projectDetails": {
      "type": "array",
      "items": {
        "properties": {
          "name": {
            "type": "string"
          },
          "age": {
            "type": "number"
          },
          "projects": {
            "$ref": "#/$defs/projects"
          }
        }
      },
      "minItems": 1,
      "maxItems": 4
    },
    "projects": {
      "type": "array",
      "items": {
        "properties": {
          "name": {
            "type": "string"
          },
          "age": {
            "type": "number"
          },
          "projectsAdditional": {
            "$ref": "#/$defs/projectsAdditional"
          }
        }
      },
      "minItems": 1,
      "maxItems": 4
    },
    "projectsAdditional": {
      "type": "array",
      "items": {
        "properties": {
          "Additional_name": {
            "type": "string"
          },
          "Additional_areacode": {
            "type": "number"
          }
        }
      },
      "minItems": 1,
      "maxItems": 4
    },
    "GeneralDetails": {
      "type": "object",
      "properties": {
        "age": {
          "type": "number"
        },
        "married": {
          "type": "boolean"
        },
        "phone": {
          "type": "number",
          "aem:afProperties": {
            "sling:resourceType": "/libs/fd/af/components/guidetelephone",
            "guideNodeClass": "guideTelephone"
          }
        },
        "address": {
          "type": "string"
        }
      }
      }
  }
  }
```

>[!ENDTABS]

De belangrijkste wijzigingen van de specificaties van JSON Schema V4 naar versie 2020-12 zijn:
* Id is gedeclareerd als `$id`
* definities worden gedeclareerd als `$defs`

### Herbruikbare schemadefinities {#reusable-schema-definitions}

De sleutels van de definitie worden gebruikt om herbruikbare schema&#39;s te identificeren. De herbruikbare schemadefinities worden gebruikt om fragmenten tot stand te brengen. <!-- It is similar to identifying complex types in XSD.--> Hieronder volgt een voorbeeld van een JSON-schema met definities:

```json
{
  "$schema": "https://json-schema.org/draft-04/schema#",

  "definitions": {
    "address": {
      "type": "object",
      "properties": {
        "street_address": { "type": "string" },
        "city":           { "type": "string" },
        "state":          { "type": "string" }
      },
      "required": ["street_address", "city", "state"]
    }
  },

  "type": "object",

  "properties": {
    "billing_address": { "$ref": "#/definitions/address" },
    "shipping_address": { "$ref": "#/definitions/address" }
  }
}
```

In het bovenstaande voorbeeld wordt een klantrecord gedefinieerd, waarbij elke klant zowel een verzendadres als een factuuradres heeft. De structuur van beide adressen is zelfde-adressen heeft een straatadres, een stad en een staat— zodat is het een goed idee om de adressen niet te dupliceren. Het maakt het toevoegen en schrappen van gebieden voor om het even welke toekomstige veranderingen gemakkelijk.

## Velden vooraf configureren in JSON-schemadefinitie {#pre-configuring-fields-in-json-schema-definition}

U kunt de **aem:afProperties** eigenschap om het veld JSON-schema vooraf te configureren voor toewijzing aan een aangepaste component Adaptief formulier. Hieronder ziet u een voorbeeld:

```json
{
    "properties": {
        "sizeInMB": {
            "type": "integer",
            "minimum": 16,
            "maximum": 512,
            "aem:afProperties" : {
                 "sling:resourceType" : "/apps/fd/af/components/guideTextBox",
                 "guideNodeClass" : "guideTextBox"
             }
        }
    },
    "required": [ "sizeInMB" ],
    "additionalProperties": false
}
```

<!--- ## Configure scripts or expressions for form objects  {#configure-scripts-or-expressions-for-form-objects}

JavaScript is the expression language of Adaptive Forms. All the expressions are valid JavaScript expressions and use Adaptive Forms scripting model APIs. You can pre-configure form objects to [evaluate an expression](adaptive-form-expressions.md) on a form event.

Use the aem:afproperties property to preconfigure Adaptive Form expressions or scripts for Adaptive Form components. For example, when the initialize event is triggered, the below code sets value of telephone field and prints a value to the log :

```json
"telephone": {
  "type": "string",
  "pattern": "/\\d{10}/",
  "aem:affKeyword": ["phone", "telephone","mobile phone", "work phone", "home phone", "telephone number", "telephone no", "phone number"],
  "description": "Telephone Number",
  "aem:afProperties" : {
    "sling:resourceType" : "fd/af/components/guidetelephone",
    "guideNodeClass" : "guideTelephone",
    "events": {
      "Initialize" : "this.value = \"1234567890\"; console.log(\"ef:gh\") "
    }
  }
}
```

You should be a member of the [forms-power-user group](forms-groups-privileges-tasks.md) to configure scripts or expressions for form object. The below table lists all the script events supported for an Adaptive Form component.

<table>
 <tbody>
  <tr>
   <th><strong></strong>Component \ Event</th>
   <th>initialize <br /> </th>
   <td>Calculate</td>
   <td>Visibility</td>
   <td>Validate</td>
   <td>Enabled</td>
   <td>Value Commit</td>
   <td>Click </td>
   <td>Options</td>
  </tr>
  <tr>
   <td>Text Field</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Numeric Field</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Numeric Stepper</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Radio Button</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Telephone</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Switch</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Button</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
  </tr>
  <tr>
   <td>Check Box</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Drop-down</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Image Choice</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Date Input Field</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Date Picker</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Email</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>File Attachment</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Image</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Draw</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Panel</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

Some examples of using events in a JSON are hiding a field on initialize event and configure value of another field on value commit event. For detailed information about creating expressions for the script events, see [Adaptive Form Expressions](adaptive-form-expressions.md).

Here is the sample JSON code for previously mentioned examples.

### Hiding a field on initialize event {#hiding-a-field-on-initialize-event}

```json

"name": {
    "type": "string",
    "aem:afProperties": {
        "events" : {
            "Initialize" : "this.visible = false;"
        }
    }
}
```

#### Configure value of another field on value commit event {#configure-value-of-another-field-on-value-commit-event}

```json
"Income": {
    "type": "object",
    "properties": {
        "monthly": {
            "type": "number",
            "aem:afProperties": {
                "events" : {
                    "Value Commit" : "IncomeYearly.value = this.value * 12;"
                }
            }
        },
        "yearly": {
            "type": "number",
            "aem:afProperties": {
                "name": "IncomeYearly"
            }
        }
    }
}

```
-->

## Acceptabele waarden voor een adaptieve formuliercomponent beperken {#limit-acceptable-values-for-an-adaptive-form-component}

U kunt de volgende beperkingen toevoegen aan JSON-schemaelementen om de waarden te beperken die acceptabel zijn voor een adaptieve formuliercomponent:

<table>
 <tbody>
  <tr>
   <td><p><strong> Schema, eigenschap</strong></p> </td>
   <td><p><strong>Gegevenstype</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
   <td><p><strong>Component</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>maximum</code></p> </td>
   <td><p>String</p> </td>
   <td><p>Hiermee geeft u de bovengrens voor numerieke waarden en datums op. Standaard wordt de maximumwaarde opgenomen.</p> </td>
   <td>
    <ul>
     <li>Numeriek vak</li>
     <li>Numerieke stap<br /> </li>
     <li>Datumkiezer</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>minimum</code></p> </td>
   <td><p>String</p> </td>
   <td><p>Hiermee geeft u de ondergrens voor numerieke waarden en datums op. Standaard wordt de minimumwaarde opgenomen.</p> </td>
   <td>
    <ul>
     <li>Numeriek vak</li>
     <li>Numerieke stap</li>
     <li>Datumkiezer</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>exclusiveMaximum</code></p> </td>
   <td><p>Boolean</p> </td>
   <td><p>Indien waar (true), moet de numerieke waarde of datum die in de component van het formulier is opgegeven, kleiner zijn dan de numerieke waarde of datum die voor de eigenschap maximum is opgegeven.</p> <p>Indien onwaar, moet de numerieke waarde of datum die in de component van de vorm wordt gespecificeerd minder dan of gelijk aan de numerieke waarde of de datum zijn die voor het maximumbezit wordt gespecificeerd.</p> </td>
   <td>
    <ul>
     <li>Numeriek vak</li>
     <li>Numerieke stap</li>
     <li>Datumkiezer</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>exclusiveMinimum</code></p> </td>
   <td><p>Boolean</p> </td>
   <td><p>Indien waar (true), moet de numerieke waarde of datum die in de component van het formulier is opgegeven, groter zijn dan de numerieke waarde of datum die voor de eigenschap minimum is opgegeven.</p> <p>Indien onwaar, moet de numerieke waarde of datum die in de component van de vorm wordt gespecificeerd groter zijn dan of gelijk aan de numerieke waarde of de datum die voor het minimumbezit wordt gespecificeerd.</p> </td>
   <td>
    <ul>
     <li>Numeriek vak</li>
     <li>Numerieke stap</li>
     <li>Datumkiezer</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>minLength</code></p> </td>
   <td><p>String</p> </td>
   <td><p>Hiermee wordt het minimale aantal tekens opgegeven dat in een component is toegestaan. De minimumlengte moet gelijk zijn aan of groter zijn dan nul.</p> </td>
   <td>
    <ul>
     <li>Tekstvak</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>maxLength</code></td>
   <td>String</td>
   <td>Hiermee wordt het maximale aantal tekens opgegeven dat in een component is toegestaan. De maximumlengte moet gelijk zijn aan of groter zijn dan nul.</td>
   <td>
    <ul>
     <li>Tekstvak</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>pattern</code></p> </td>
   <td><p>String</p> </td>
   <td><p>Hiermee geeft u de volgorde van de tekens op. Een component accepteert de tekens als de tekens overeenkomen met het opgegeven patroon.</p> <p>De eigenschap pattern verwijst naar het validatiepatroon van de overeenkomstige component Adaptief formulier.</p> </td>
   <td>
    <ul>
     <li>Alle adaptieve Forms-componenten die zijn toegewezen aan een XSD-schema </li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>maxItems</code></td>
   <td>String</td>
   <td>Geeft het maximale aantal items in een array op. De maximale items moeten gelijk zijn aan of groter zijn dan nul.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>minItems</code></td>
   <td>String</td>
   <td>Geeft het minimale aantal items in een array op. De minimale items moeten gelijk zijn aan of groter zijn dan nul.</td>
   <td> </td>
  </tr>
 </tbody>
</table>


## Schema-compatibele gegevens inschakelen {#enablig-schema-compliant-data}

Voer de volgende stappen uit om alle op JSON-schema&#39;s gebaseerde Adaptieve Forms in staat te stellen schema-compatibele gegevens te genereren bij het verzenden van formulieren:

1. Ga naar Experience Manager webconsole op `https://server:host/system/console/configMgr`.
1. Zoeken **[!UICONTROL Adaptive Form and Interactice Communication Web Channel Configuration]**.
1. Selecteer deze optie om de configuratie te openen in de bewerkingsmodus.
1. Selecteer de **[!UICONTROL Generate Schema Compliant Data]** selectievakje.
1. Sla de instellingen op.

![adaptieve vorm en interactieve communicatie webkanaalconfiguratie](/help/forms/assets/af-ic-web-channel-configuration.png)


## Niet-ondersteunde constructies  {#non-supported-constructs}

Adaptive Forms biedt geen ondersteuning voor de volgende JSON-schemaconstructies:

* Null-tekst
* Unietypen zoals alle, en
* OneOf, anyOf, allOf, and not
* Alleen homogene arrays worden ondersteund. De itembeperking moet dus een object zijn en geen array.
* URI-verwijzingen in $ref

## Veelgestelde vragen {#frequently-asked-questions}

**Waarom kan ik geen afzonderlijke elementen van een subformulier (structuur gegenereerd van een complex type) slepen voor herhaalbare subformulieren (waarden voor minOccurs of maxOccurs zijn groter dan 1)?**

In een herhaalbaar subformulier moet u het volledige subformulier gebruiken. Als u alleen selectieve velden wilt, gebruikt u de volledige structuur en verwijdert u de ongewenste velden.

**Ik heb een lange complexe structuur in de Inhoudszoeker. Hoe kan ik een specifiek element vinden?**

U hebt twee opties:

* Door de boomstructuur schuiven
* Gebruik het vak Zoeken om een element te zoeken

**Wat moet de extensie van het JSON-schemabestand zijn?**

De extensie van het JSON-schemabestand moet .schema.json zijn. Bijvoorbeeld: &lt;filename>.schema.json.

## Zie ook {#see-also}

{{see-also}}

<!--

>[!MORELIKETHIS]
>
>* [Design XML Schema for an Adaptive Form](/help/forms/adaptive-form-xml-schema-form-model.md)

-->
