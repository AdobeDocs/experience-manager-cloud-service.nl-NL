---
title: Ondersteunde HTML-opmaaktags in Verzending PDF (voorheen Document of Record)
description: Referentiegids voor HTML-opmaaktags die worden ondersteund bij het genereren van een Verzending PDF (voorheen Document of Record), inclusief het rendergedrag en toegankelijkheidsoverwegingen.
feature: Adaptive Forms
role: Developer, User
exl-id: 8481b0dc-aae7-4bd2-acfe-1f1b6d747683
source-git-commit: 0b112a5a1830fac9d0170771e052bbb2ef3cadbf
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---


# Ondersteunde HTML-opmaaktags in Verzending PDF (voorheen Document of Record)

## Waar gaat het om?

AEM Forms ondersteunt nu HTML-opmaaktags in RTF-velden wanneer een PDF-verzending (voorheen Document of Record) PDF wordt gegenereerd. In deze handleiding wordt uitgelegd welke HTML-opmaaktags u veilig kunt gebruiken in Adaptive Forms en hoe deze worden weergegeven in de gegenereerde Verzending PDF.

Als u RTF-inhoud (zoals vet opmaken, lijsten of koppelingen) toevoegt aan uw formulieren, is het belangrijk dat u weet welke tags worden ondersteund en welke beperkingen ze kunnen hebben. Met deze verwijzing kunt u de juiste codes kiezen om ervoor te zorgen dat de inhoud correct wordt weergegeven en toegankelijk blijft in de verzendende PDF.

## Voordat u begint

### Vereisten

U zou vertrouwd met moeten zijn:

- Standaard HTML-markeringssyntaxis
- [Basisprincipes van het verzenden van PDF (voorheen Document of Record)](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
- Toegankelijkheidsbeginselen en WCAG-richtsnoeren
- Toegankelijkheidsvereisten voor PDF
- Aangepaste formuliercomponenten die HTML-opmaak accepteren

### Overwegingen

De PDF voor verzending (voorheen Document of Record) kan een gelabelde PDF zijn, die de toegankelijkheid en juiste structuur voor ondersteunende hulpmiddelen helpt te garanderen. Om geëtiketteerde output van PDF toe te laten, [ plaats het bezit XCI `config/present/pdf/tagged` aan `true`](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#use-a-custom-xci-file). Nadat u de PDF hebt gegenereerd, is het belangrijk te controleren of toegankelijkheidstags correct zijn toegepast. U kunt [ Adobe Acrobat gebruiken om toegankelijkheidstags ](https://helpx.adobe.com/in/acrobat/using/create-verify-pdf-accessibility.html) te controleren en uw document te verzekeren voldoet aan toegankelijkheidsnormen.

### Nieuwe functies

RTF-ondersteuning in Verzending PDF is een recente verbetering. Eerder werd RTF-inhoud weergegeven als onbewerkte tekst in gegenereerde documenten. Dankzij deze nieuwe functie kan geformatteerde inhoud op de juiste wijze worden weergegeven in PDF-uitvoerbestanden.

## Referentie voor HTML-ondersteuning

### Volledig ondersteunde tags

Deze codes worden volledig ondersteund en het maken van toegankelijkheidsknooppunten is correct:

| HTML-tag | Beschrijving | PDF-ondersteuning voor verzending | Toegankelijkheid | Voorbeeld |
|----------|-------------|-------------|---------------|---------|
| `<p>` | Alinea | Ja | Volledig ondersteund - knooppunt corrigeren `<P>` | `<p>This is a paragraph.</p>` |
| `<br/>` | Regeleinde | Ja | Volledig ondersteund - binnen knooppunt `<P>` | `<p>Line 1<br/>Line 2</p>` |
| `<b>` | Vette tekst | Ja | Volledig ondersteund - binnen knooppunt `<P>` | `<b>bold text</b>` |
| `<i>` | Cursieve tekst | Ja | Volledig ondersteund - binnen knooppunt `<P>` | `<i>italic text</i>` |
| `<span>` | Algemene inline-container | Ja | binnen blokelementen | `<span>styled text</span>` |
| `<sub>` | Subscript | Ja | Volledig ondersteund - binnen blokelementen | `H<sub>2</sub>O` |
| `<sup>` | Superscript | Ja | Volledig ondersteund - binnen blokelementen | `E=mc<sup>2</sup>` |
| `<a>` | Hyperlink | Ja | Beperkte ondersteuning - vereist correct nesten | `<a href="url">link text</a>` |


#### Toegankelijkheidsprobleem voor lijst

Bij de huidige rendering van lijsten worden `<P>` knooppunten gemaakt in plaats van de juiste lijststructuur:

```
Current: <P>1. First item
Current: <P>2. Second item

Expected: <L>
Expected:   <LI>
Expected:     <LBL>1.
Expected:     <LBody>First item
```

### Niet-ondersteunde tags

Deze tags worden niet ondersteund en worden niet correct weergegeven:

| HTML-tag | Beschrijving | Alternatieve oplossing |
|----------|-------------|---------------------|
| `<h1>` - `<h6>` | Koptags | Gestileerde `<p>` -tags of koppen op ontwerpniveau gebruiken |
| `<img>` | Afbeeldingen | Afzonderlijke afbeeldingsvelden of ontwerpsjablonen gebruiken |
| `<code>` | Codeblokken | Niet-proportionele lettertypen gebruiken met `<span>` opmaak |
| `<blockquote>` | Aanhalingstekens blokkeren | Gestileerde `<p>` -tags met inspringing gebruiken |
| `<table>` | Tabellen | Aangepaste formuliertabelcomponenten gebruiken |

## Codevoorbeelden

### Basistekstopmaak

```html
<!--  Supported - renders correctly -->
<p>This paragraph contains <b>bold text</b> and <i>italic text</i>.</p>

<!--  Supported - combined formatting -->
<p>This text is <i><b>bold and italic</b></i>.</p>

<!--  Unsupported - headings don't work -->
<h1>This won't render as a heading</h1>
```

### Lijsten

```html
<!-- ⚠️ Partially supported - renders but not accessible -->
<ol>
  <li>First numbered item</li>
  <li>Second numbered item</li>
</ol>

<ul>
  <li>First bullet point</li>
  <li>Second bullet point</li>
</ul>
```

### Koppelingen

```html
<!--  Supported - but must be within block elements -->
<p>Visit our <a href="https://example.com">website</a> for more information.</p>

<!--  Incorrect - link not properly nested -->
<a href="https://example.com">Standalone link</a>
```

### Wetenschappelijke notatie

```html
<!--  Supported - but limited accessibility -->
<p>Water formula: H<sub>2</sub>O</p>
<p>Einstein's equation: E=mc<sup>2</sup></p>
```

## Gerelateerde inhoud


- [PDF (voorheen Document of Record) verzenden voor Adaptive Forms genereren](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
- [PDF voor kerncomponenten verzenden genereren](/help/forms/generate-document-of-record-core-components.md)
- [Aanpassing PDF-sjabloon verzenden](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#customize-the-branding-information-in-document-of-record)

