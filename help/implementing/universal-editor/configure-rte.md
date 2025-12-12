---
title: Het vormen van RTE voor de Universele Redacteur
description: Begrijp hoe u de rijke tekstredacteur (RTE) in de Universele Redacteur kunt vormen.
feature: Developing
role: Admin, Developer
exl-id: 350eab0a-f5bc-49c0-8e4d-4a36a12030a1
source-git-commit: 482c9604bf4dd5e576b560d350361cdc598930e3
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 0%

---

# Het vormen van RTE voor de Universele Redacteur {#configure-rte}

Begrijp hoe u de rijke tekstredacteur (RTE) in de Universele Redacteur kunt vormen.

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

### Inspringingsconfiguratie {#indentation}

De inspringing heeft een eigenschap-vlakke configuratie die het werkingsgebied van inkeping gedrag, plus individuele actieconfigurs voor kortere weg en etiketten controleert.

```json
{
  "actions": {
    // Feature-level configuration
    "indentation": {
      "scope": "all"  // Controls what content can be indented (default: "all")
    },

    // Individual action configurations
    "indent": {
      "shortcut": "Tab",           // Custom keyboard shortcut
      "label": "Increase Indent"   // Custom button label
    },
    "outdent": {
      "shortcut": "Shift-Tab",     // Custom keyboard shortcut
      "label": "Decrease Indent"   // Custom button label
    }
  }
}
```

#### Opties voor inspringingsbereik {#indentation-options}

* `scope`: `all` (standaardwaarde) - Inspringen/uitspringen is van toepassing op alle inhoud:
   * Lijsten: Lijstitems nesten/nesten
   * Alinea&#39;s en koppen: algemene inspringingsniveau verhogen/verlagen
* `scope`: `lists` - Inspringen/uitspringen is alleen van toepassing op lijstitems:
   * Lijsten: Lijstitems nesten/nesten
   * Alinea&#39;s en koppen: Geen inspringing (hiervoor zijn knoppen uitgeschakeld)

>[!NOTE]
>
>Het nesten van lijsten via Tab/Shift+Tab toetsen werkt onafhankelijk van de algemene inspringingsinstellingen.

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
    }
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

### `wrapInPicture`{#wrapinpicture}

De optie `wrapInPicture` voor afbeeldingen bepaalt de HTML-structuur die wordt gegenereerd voor afbeeldingsinhoud.

#### wrapInPicture: false (standaardwaarde) {#wrapinpicture-false}

```html
<img src="image.jpg" alt="Description" />
```

#### wrapInPicture: true {#wrapinpicture-true}

```html
<picture>
  <img src="image.jpg" alt="Description" />
</picture>
```

Gebruik `wrapInPicture: true` wanneer dat nodig is:

* Ondersteuning voor responsieve afbeeldingen met `<source>` -elementen.
* Mogelijkheden voor de richting van illustraties.
* Proofing in de toekomst voor geavanceerde afbeeldingsfuncties.
* Consistente structuur van afbeeldingselementen.

>[!NOTE]
>
>Als `wrapInPicture: true` is ingeschakeld, kunnen afbeeldingen worden uitgebreid met extra `<source>` -elementen voor verschillende mediaquery&#39;s en -indelingen, waardoor ze flexibeler worden voor een responsief ontwerp.

### Opties koppelingsdoel {#link-target}

Met de optie `hideTarget` voor koppelingen wordt bepaald of het kenmerk `target` is opgenomen in gegenereerde koppelingen en of het dialoogvenster voor het maken van koppelingen een veld voor doelselectie bevat.

#### `hideTarget: false` (standaardwaarde) {#hideTarget-false}

```html
<a href="https://example.com" target="_self">Link text</a>
<a href="https://example.com" target="_blank">External link</a>
```

#### `hideTarget: true` {#hideTarget-true}

```html
<a href="https://example.com">Link text</a>
```

### Koppelingen op afbeeldingen uitschakelen {#disableforimages}

Met de optie `disableForImages` voor koppelingen bepaalt u of gebruikers koppelingen kunnen maken op afbeeldingen en afbeeldingselementen. Dit geldt voor inline `<img>` -elementen en blokelementen `<picture>` .

#### `disableForImages: false` (standaardwaarde) {#disableforimages-false}

Gebruikers kunnen afbeeldingen selecteren en deze in koppelingen plaatsen.

```html
<!-- Inline image with link -->
<a href="https://example.com">
  <img src="image.jpg" alt="Description" />
</a>

<!-- Block-level picture with link -->
<a href="https://example.com">
  <picture>
    <img src="image.jpg" alt="Description" />
  </picture>
</a>
```

#### disableForImages: true {#disableforimages-true}

De koppelingsknop wordt uitgeschakeld wanneer een afbeelding of afbeelding wordt geselecteerd. Gebruikers kunnen alleen koppelingen op tekstinhoud maken.

```html
<!-- Images remain standalone without links -->
<img src="image.jpg" alt="Description" />

<picture>
  <img src="image.jpg" alt="Description" />
</picture>

<!-- Links work normally on text -->
<a href="https://example.com">Link text</a>
```

Gebruik `disableForImages: true` wanneer u wilt:

* Houd de visuele consistentie in stand door gekoppelde afbeeldingen te voorkomen.
* Vereenvoudig de inhoudsstructuur door afbeeldingen van de navigatie te scheiden.
* Beleid voor inhoud afdwingen waarmee het koppelen van afbeeldingen wordt beperkt.
* Verminder de toegankelijkheid van uw inhoud.

>[!NOTE]
>
>Deze instelling heeft alleen invloed op de mogelijkheid om nieuwe koppelingen te maken in afbeeldingen. Bestaande koppelingen worden niet verwijderd uit afbeeldingen in de inhoud.

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
