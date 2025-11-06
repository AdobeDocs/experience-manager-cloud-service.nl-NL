---
title: Het vormen van RTE voor de Universele Redacteur
description: Begrijp hoe u de rijke tekstredacteur (RTE) in de Universele Redacteur kunt vormen.
feature: Developing
role: Admin, Developer
exl-id: 350eab0a-f5bc-49c0-8e4d-4a36a12030a1
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# Het vormen van RTE voor de Universele Redacteur {#configure-rte}

Begrijp hoe u de rijke tekstredacteur (RTE) in de Universele Redacteur kunt vormen.

>[!NOTE]
>
>Deze documentatie is op nieuwe RTE voor de Universele Redacteur van toepassing, die als vroege adoptereigenschap beschikbaar is. Als u in het testen van deze nieuwe eigenschap geinteresseerd bent, [ te zien gelieve de versienota&#39;s voor details.](/help/release-notes/universal-editor/current.md#new-rte)

## Overzicht {#overview}

De Universele Redacteur verstrekt een rijke tekstredacteur (RTE) zowel op zijn plaats als in het eigenschappenpaneel om auteurs toe te staan om het formatteren veranderingen toe te passen aangezien zij hun tekst uitgeven.

Dit RTE is configureerbaar gebruikend [ componentenfilters.](/help/implementing/universal-editor/filtering.md) In dit document wordt beschreven welke configuratieopties beschikbaar zijn en worden voorbeelden gegeven.

## Configuratiestructuur {#structure}

De configuratie van RTE bestaat uit twee delen:

* [`toolbar`](#toolbar): In de werkbalkconfiguratie wordt bepaald welke bewerkingsopties beschikbaar zijn in de gebruikersinterface en hoe deze zijn ingedeeld.
* [`actions`](#actions): Met de configuratie van handelingen kunt u het gedrag en de weergave van afzonderlijke bewerkingsacties aanpassen.

Deze configuraties kunnen als deel van a [ componentenfilter ](/help/implementing/universal-editor/filtering.md) met het bezit `rte` worden bepaald.

```json
[
  {
    "id": "richtext",
    "rte": {
      "toolbar": {
        // Toolbar configuration
      },
      "actions": {
        // Action-specific configurations
      }
    },
    "components": [
      "richtext"
    ]
  }
]
```

## Werkbalkconfiguratie {#toolbar}

De controles van de toolbarconfiguratie die het uitgeven opties in UI beschikbaar zijn en hoe zij worden georganiseerd. Dit zijn de beschikbare secties

```json
{
  "toolbar": {
    // Text formatting options
    "format": ["bold", "italic", "underline", "strike"],
    // Text alignment options
    "alignment": ["left", "center", "right", "justify"],
    // Text direction options, right-to-left or left-to-right
    "direction": ["rtl", "ltr"],
    // Indentation controls
    "indentation": ["indent", "outdent"],
    // Block-level elements
    "blocks": ["paragraph", "h1", "h2", "h3", "h4", "h5", "h6", "code_block"],
    // List options
    "list": ["bullet_list", "ordered_list"],
    // Content insertion
    "insert": ["link", "unlink", "image"],
    // Superscript/subscript
    "sr_script": ["superscript", "subscript"],
    // Editor utilities
    "editor": ["removeformat"],
    // Section ordering (optional)
    "sections": ["format", "alignment", "list"]
  }
}
```

## Configuratie van handelingen {#actions}

Met de configuratie van handelingen kunt u het gedrag en de weergave van afzonderlijke bewerkingsacties aanpassen. Dit zijn de beschikbare secties.

### Handelingen opmaken {#format}

Opmaakacties worden gebruikt om opmaak toe te passen en om HTML-tags te ondersteunen die schakelen tussen semantische varianten. De volgende secties zijn beschikbaar.

```json
{
  "actions": {
    "bold": {
      "tag": "strong",      // Use <strong> instead of <b>
      "shortcut": "Mod-B",  // Custom keyboard shortcut
      "label": "Make Bold"  // Custom button label 
    },
    "italic": {
      "tag": "em",          // Use <em> instead of <i>
      "shortcut": "Mod-I",
      "label": "Italicize"
    },
    "strike": {
      "tag": "del"          // Use <del> instead of <s>
    }
  }
}
```

### Handelingen weergeven {#list}

De acties van de lijst steunen inhoud het verpakken om de structuur van HTML te controleren. De volgende secties zijn beschikbaar.

```json
{
  "actions": {
    "bullet_list": {
      "wrapInParagraphs": true,    // <ul><li><p>content</p></li></ul>
      "shortcut": "Mod-Shift-8",   // Custom shortcut
      "label": "Bullet List"       // Custom label
    },
    "ordered_list": {
      "wrapInParagraphs": false,   // <ol><li>content</li></ol> (default)
      "shortcut": "Mod-Shift-9"
    }
  }
}
```

### Handelingen koppelen {#link}

De acties van de verbinding steunen de controle van doelattributen om verbindingsgedrag te beheren. De volgende secties zijn beschikbaar.

```json
{
  "actions": {
    "link": {
      "hideTarget": false,       // Show target attribute options (default)
      "shortcut": "Mod-K",       // Custom keyboard shortcut
      "label": "Insert Link"     // Custom button label
    },
    "unlink": {
      "shortcut": "Mod-Shift-K", // Custom keyboard shortcut
      "label": "Remove Link"     // Custom button label
    }
  }
}
```

#### Opties voor configuratie koppelen {#link-options}

* `hideTarget`: `false` (standaardwaarde) - Doelkenmerk opnemen in koppelingen, toestaan `_self` , `_blank` , enzovoort.
* `hideTarget`: `true` - Doelkenmerk uitsluiten van koppelingen

De handeling `unlink` wordt alleen weergegeven wanneer de cursor zich binnen een bestaande koppeling bevindt. De koppelingsopmaak wordt verwijderd terwijl de tekstinhoud behouden blijft.

### Afbeeldingshandelingen {#image}

Afbeeldingsacties ondersteunen de onmiddellijke omloop van afbeeldingselementen om responsieve afbeeldingsmarkeringen te genereren. De volgende secties zijn beschikbaar.

```json
{
  "actions": {
    "image": {
      "wrapInPicture": false,     // Use <img> tag (default)
      "shortcut": "Mod-Shift-I",  // Custom keyboard shortcut
      "label": "Insert Image"     // Custom button label
    }
  }
}
```

#### Opties voor configuratie van images {#image-options}

* `wrapInPicture`: `false` (standaardwaarde) - Eenvoudige `<img>` elementen genereren
* `wrapInPicture`: `true` - Afbeeldingen laten omlopen in `<picture>` -elementen voor responsief ontwerp

### Overige handelingen {#other}

Alle andere acties ondersteunen basisaanpassingen. De volgende secties zijn beschikbaar.

```json
{
  "actions": {
    "h1": {
      "shortcut": "Mod-Alt-1",
      "label": "Large Heading"
    },
    "paragraph": {
      "shortcut": "Mod-Alt-0",
      "label": "Normal Text"
    },
    "link": {
      "shortcut": "Mod-K",
      "label": "Insert Link",
      "hideTarget": false    // Show target attribute options (default: false)
    }
  }
}
```

## Volledig voorbeeld {#example}

Hieronder ziet u een voorbeeld van een volledige configuratie.

```json
[
  {
    "id": "richtext",
    "rte": {
      // Configure which tools appear in toolbar
      "toolbar": {
        "format": [
          "bold",
          "italic"
        ],
        "blocks": [
          "paragraph",
          "h1",
          "h2"
        ],
        "list": [
          "bullet_list",
          "ordered_list"
        ],
        "insert": [
          "link",
          "unlink"
        ],
        "sections": [
          "format",
          "blocks",
          "list",
          "insert"
        ]
      },
      // Customize individual action behavior
      "actions": {
        // Format actions with HTML tag choices
        "bold": {
          "tag": "strong",
          "shortcut": "Mod-B",
          "label": "Bold"
        },
        "italic": {
          "tag": "em",
          "shortcut": "Mod-I"
        },
        // List actions with content wrapping
        "bullet_list": {
          "wrapInParagraphs": true,
          "label": "Bullet List"
        },
        "ordered_list": {
          "wrapInParagraphs": false
        },
        // Link actions with target control
        "link": {
          "hideTarget": false,
          "shortcut": "Mod-K",
          "label": "Add Link"
        },
        "unlink": {
          "label": "Remove Link"
        },
        // Other actions with basic customization
        "h1": {
          "shortcut": "Mod-Alt-1",
          "label": "Main Heading"
        }
      }
    },
    "components": [
      "richtext"
    ]
  }
]
```

## Details van handelingsoptie {#action-details}

Verschillende opties bevatten aanvullende details die belangrijk zijn om in gedachten te houden.

### `wrapInParagraphs` {#wrapInParagraphs}

De optie `wrapInParagraphs` voor lijsten bepaalt de HTML-structuur.

#### `wrapInParagraphs: false` (standaardwaarde) {#wrapInParagraphs-false}

```html
<ul>
  <li>Simple text content</li>
  <li>Another item</li>
</ul>
```

#### `wrapInParagraphs: true` {#wrapInParagraphs-true}

```html
<ul>
  <li><p>Text wrapped in paragraphs</p></li>
  <li><p>Supports rich formatting within items</p></li>
</ul>
```

Gebruik `wrapInParagraphs: true` wanneer dat nodig is:

* Rijke opmaak binnen lijstitems
* Meerdere alinea&#39;s per lijstitem
* Consistente stijl op blokniveau

### Opties koppelingsdoel {#link-target}

Met de optie `hideTarget` voor koppelingen wordt bepaald of het kenmerk `target` is opgenomen in gegenereerde koppelingen en of het dialoogvenster voor het maken van koppelingen een veld voor doelselectie bevat.

#### `hideTarget: false` (standaardwaarde) {#hideTarget-false}

```html
<a href="https://example.com" target="_self">Link text</a>
<a href="https://example.com" target="_blank">External link</a>
```

### `hideTarget: true` {#hideTarget-true}

```html
<a href="https://example.com">Link text</a>
```

### Labelopties {#tag}

Met opmaakacties kunt u schakelen tussen HTML-varianten.

| Handeling | Standaardtag | Alternatieve tags | Hoofdletters gebruiken |
|---|---|---|---|
| `bold` | `<strong>` | `<b>` | Semantische versus visuele nadruk |
| `italic` | `<em>` | `<i>` | Semantische versus visuele stijlen |
| `strike` | `<del>` | `<s>` | Visuele versus semantische verwijdering |

Kies semantische tags (`<strong>`, `<em>`, `<del>` ) voor betere toegankelijkheid en SEO.

### Sneltoetsen {#keyboard-shortcuts}

Sneltoetsen gebruiken de notatie `Mod-Key`(s) waarbij:

* `Mod` = `Cmd` op Mac, `Ctrl` op Windows/Linux
* Voorbeelden: `Mod-B` , `Mod-Shift-8` , `Mod-Alt-1`
