---
title: Kenmerken en itemtypen
description: Leer over de gegevensattributen en de punttypes die de Universele Redacteur vereist.
exl-id: 02795a31-244a-42b4-8297-2649125d7777
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 1%

---


# Kenmerken en typen {#attributes-types}

Leer over de gegevensattributen en de punttypes die de Universele Redacteur vereist.

## Inleiding {#introduction}

Een toepassing kan alleen worden bewerkt met de Universal Editor als deze correct van instrumenten is voorzien. Dit omvat onder andere de juiste metagegevens, zodat de editor de inhoud van de app kan bewerken. In dit document worden de kenmerken en itemtypen van deze metagegevens beschreven.

>[!NOTE]
>
>De validatie van de inhoud wordt uitgevoerd op de server. De Universele Redacteur werkt eenvoudig met de gegevensattributen. De bevestiging dat zij het model/de structuur passen moet op het API niveau worden gericht.

## Gegevenseigenschappen {#data-properties}

| Eigenschap gegevens | Beschrijving |
|---|---|
| `data-aue-resource` | URL aan het middel, zie het sectie [ Instrument de Pagina van het document dat met de Universele Redacteur in AEM ](getting-started.md#instrument-thepage) wordt begonnen |
| `data-aue-prop` | Attribuut van het middel, zie het sectie [ Instrument de Pagina van het document dat met de Universele Redacteur in AEM ](getting-started.md#instrument-thepage) wordt begonnen |
| `data-aue-type` | [ Type van het editable punt ](#item-types) (bijvoorbeeld, tekst, beeld, en verwijzing) |
| `data-aue-filter` | Definieert welke verwijzingen kunnen worden gebruikt |
| `data-aue-label` | Bepaalt een douanelabel voor een selecteerbaar punt dat in de redacteur <br> wordt getoond Voor het geval `data-aue-model` wordt geplaatst, wordt het etiket teruggewonnen als model |
| `data-aue-model` | Definieert een model dat wordt gebruikt voor bewerkingen op basis van formulieren in de rail Eigenschappen |
| `data-aue-behavior` | Bepaalt het [ gedrag van een instrumentatie ](#behaviors), bijvoorbeeld, kan de stand-alone tekst of het beeld een component ook simuleren om het te bewegen of te schrappen |

## Itemtypen {#item-types}

| `data-aue-type` | Beschrijving | `data-aue-resource` | `data-aue-prop` | `data-aue-filter` | `data-aue-label` | `data-aue-model` | `data-aue-behavior` |
|---|---|---|---|---|---|---|---|
| `text` | Tekst kan worden bewerkt binnen de HTML-tags, maar alleen in de eenvoudige tekstopmaak, zonder tekstopmaak, wordt deze doorgaans gebruikt voor titelcomponenten, bijvoorbeeld | Optioneel | Vereist | nvt | Optioneel | nvt | Optioneel |
| `richtext` | Tekst kan worden bewerkt met volledige tekstopties. RTE wordt weergegeven in het rechterdeelvenster | Optioneel | Vereist | nvt | Optioneel | nvt | Optioneel |
| `media` | Het bewerkbare element is bijvoorbeeld een afbeelding of video | Optioneel | Vereist | Facultatieve <br> lijst van beeld of videofiltercriteria die tot de activaselecteur wordt overgegaan | Optioneel | nvt | Optioneel |
| `container` | Het bewerkbare gedrag gedraagt zich als container voor componenten o.a. het Systeem van de Paragraaf. | Afhankelijkheden <br> zie hieronder | Afhankelijkheden <br> zie hieronder | Facultatieve <br> een lijst van toegestane componenten | Optioneel | nvt | nvt |
| `component` | Het bewerkbare item is een component. Er wordt geen extra functionaliteit aan toegevoegd. Het is verplicht beweegbare/verhandelbare delen van het DOM aan te geven en de spoorstaaf en de velden ervan te openen. | Vereist | nvt | nvt | Optioneel | Optioneel | nvt |
| `reference` | Bewerkbaar is een verwijzing, bijvoorbeeld Inhoudsfragment, Ervaring Fragment of Product | Afhankelijkheden <br> zie hieronder | Afhankelijkheden <br> zie hieronder | Facultatieve <br> lijst van het de filtercriteria van het Fragment van de Inhoud, van het Product, of van het Fragment van de Ervaring die tot de verwijzingsselecteur wordt overgegaan | Optioneel | Optioneel | nvt |

Afhankelijk van het gebruiksgeval `data-aue-prop` of `data-aue-resource` kan vereist zijn of niet. Bijvoorbeeld:

* `data-aue-resource` is vereist als u een query uitvoert op Inhoudsfragmenten via GraphQL en u de lijst in de context bewerkbaar wilt maken.
* `data-aue-prop` is vereist als u een component hebt die de inhoud van een Content Fragment waarnaar wordt verwezen, rendert en u de verwijzing in de component wilt bijwerken.

## Gedrag {#behaviors}

| `data-aue-behavior` | Beschrijving |
|---|---|
| `component` | Wordt gebruikt om zelfstandige tekst, richtext en mediamimicomponenten toe te staan, zodat deze ook kunnen worden verplaatst en verplaatst op de pagina |
| `container` | Gebruikt om containers te laten behandelen als hun eigen componenten zodat zij beweegbaar en verhandelbaar op de pagina zijn |
