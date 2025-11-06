---
title: Kenmerken en itemtypen
description: Leer over de gegevensattributen en de punttypes die de Universele Redacteur vereist.
exl-id: 02795a31-244a-42b4-8297-2649125d7777
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

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
| `data-aue-resource` | URL aan het middel, zie het sectie [&#x200B; Instrument de Pagina van het document dat met de Universele Redacteur in AEM &#x200B;](getting-started.md#instrument-thepage) wordt begonnen |
| `data-aue-prop` | Attribuut van het middel, zie het sectie [&#x200B; Instrument de Pagina van het document dat met de Universele Redacteur in AEM &#x200B;](getting-started.md#instrument-thepage) wordt begonnen |
| `data-aue-type` | [&#x200B; Type van het editable punt &#x200B;](#item-types) (bijvoorbeeld, tekst, beeld, en verwijzing) |
| `data-aue-filter` | Bepaalt:<br> - welke functies RTE <br> - welke componenten aan een container <br> kunnen worden toegevoegd - welke activa aan een media type kunnen worden toegevoegd |
| `data-aue-label` | Hiermee definieert u een aangepast label voor een selecteerbaar item dat in de editor wordt weergegeven |
| `data-aue-model` | Definieert een model dat wordt gebruikt voor formulierbewerkingen in het deelvenster Eigenschappen |
| `data-aue-behavior` | Verouderd. Het definieert ooit het gedrag van een instrumentatie om standalone tekst, richtext en media toe te staan om componenten te simuleren zodat ze ook op de pagina konden worden verplaatst en verplaatst, met één potentiële waarde van `component`. Deze eigenschap wordt nu genegeerd en wanneer een item met `data-aue-resource` een rechtstreeks onderliggend item van een container is, wordt het automatisch als een component beschouwd. |

## Itemtypen {#item-types}

| `data-aue-type` | Beschrijving | `data-aue-resource` | `data-aue-prop` | `data-aue-filter` | `data-aue-label` | `data-aue-model` |
|---|---|---|---|---|---|---|
| `text` | Tekst kan worden bewerkt binnen de HTML-tags, maar alleen in eenvoudige tekstopmaak, zonder tekstopmaak, wordt deze doorgaans gebruikt voor titelcomponenten, bijvoorbeeld | Optioneel | Vereist | nvt | Optioneel | nvt |
| `richtext` | Tekst kan worden bewerkt met volledige tekstopties. RTE wordt weergegeven in het rechterdeelvenster | Optioneel | Vereist | nvt | Optioneel | nvt |
| `media` | Het bewerkbare element is bijvoorbeeld een afbeelding of video | Optioneel | Vereist | Facultatieve <br> lijst van beeld of videofiltercriteria die tot de activaselecteur wordt overgegaan | Optioneel | nvt |
| `container` | Het bewerkbare gedrag gedraagt zich als container voor componenten o.a. het Systeem van de Paragraaf. | Afhankelijkheden <br> zie hieronder | Afhankelijkheden <br> zie hieronder | Facultatieve <br> een lijst van toegestane componenten | Optioneel | nvt |
| `component` | Het bewerkbare item is een component. Er wordt geen extra functionaliteit aan toegevoegd. Het is verplicht beweegbare/verhandelbare delen van het DOM aan te geven en het deelvenster Eigenschappen en zijn velden te openen. | Vereist | nvt | nvt | Optioneel | Optioneel |
| `reference` | Bewerkbaar is een verwijzing, bijvoorbeeld Inhoudsfragment, Ervaring Fragment of Product | Afhankelijkheden <br> zie hieronder | Afhankelijkheden <br> zie hieronder | Facultatieve <br> lijst van het de filtercriteria van het Fragment van de Inhoud, van het Product, of van het Fragment van de Ervaring die tot de verwijzingsselecteur wordt overgegaan | Optioneel | Optioneel |

`data-aue-resource` is altijd vereist omdat dit de primaire sleutel is die aangeeft waar wijzigingen in de inhoud worden geschreven.

* Dit is niet rechtstreeks vereist voor de tag waarin de eigenschap `data-aue-type` is ingesteld.
* Als deze niet is ingesteld, wordt het kenmerk `data-aue-resource` van het dichtstbijzijnde bovenliggende element gebruikt.

`data-aue-prop` is vereist wanneer u in context wilt bewerken, behalve in een container waarin dit optioneel is (als de container een inhoudsfragment is en de eigenschap verwijst naar een veld met meerdere referenties).

* `data-aue-prop` is het kenmerk dat moet worden bijgewerkt voor de primaire sleutel van `data-aue-resource` .
