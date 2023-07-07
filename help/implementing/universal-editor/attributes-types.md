---
title: Kenmerken en typen
description: Leer over de gegevensattributen en de types die de Universele Redacteur vereist.
exl-id: 02795a31-244a-42b4-8297-2649125d7777
source-git-commit: 0f62245d31074ab7a64d86b97ef3b1a8d7533001
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 3%

---

# Kenmerken en typen {#attributes-types}

Leer over de gegevensattributen en de types die de Universele Redacteur vereist.

## Inleiding {#introduction}

Een toepassing kan alleen worden bewerkt met de Universal Editor als deze correct van instrumenten is voorzien. Dit omvat onder andere de juiste metagegevens, zodat de editor de inhoud van de app kan bewerken. In dit document worden de kenmerken en typen van deze metagegevens beschreven.

>[!NOTE]
>
>De validatie van de inhoud wordt uitgevoerd aan de serverzijde. De Universele Redacteur werkt eenvoudig met de gegevensattributen. De validatie dat deze in het model/de structuur passen, moet op API-niveau worden uitgevoerd.

## Gegevenseigenschappen {#data-properties}

| Eigenschap gegevens | Beschrijving |
|---|---|
| `itemid` | URL aan het middel, zie de sectie [Instrueer de Pagina van het document die Begonnen met de Universele Redacteur in AEM worden](getting-started.md#instrument-thepage) |
| `itemprop` | Kenmerk van de bron, zie de sectie [Instrueer de Pagina van het document die Begonnen met de Universele Redacteur in AEM worden](getting-started.md#instrument-thepage) |
| `itemtype` | Type van het bewerkbare item (bijvoorbeeld tekst, afbeelding en verwijzing) |
| `data-editor-itemfilter` | Definieert welke verwijzingen kunnen worden gebruikt |
| `data-editor-itemlabel` | Hiermee definieert u een aangepast label voor een selecteerbaar item dat in de editor wordt weergegeven <br>In geval van `itemmodel` is ingesteld, wordt het label opgehaald via het model |
| `data-editor-itemmodel` | Definieert een model dat wordt gebruikt voor bewerkingen op basis van formulieren in de rail Eigenschappen |
| `data-editor-behavior` | Definieert het gedrag van een instrumentatie, bijvoorbeeld tekst of afbeelding die op zichzelf staat en die een component kan simuleren om deze verplaatsbaar of verplaatsbaar te maken |

## Itemtypen {#item-types}

| `itemtype` | Beschrijving | `itemid` | `itemprop` | `data-editor-itemfilter` | `data-editor-itemlabel` | `data-editor-itemmodel` | `data-editor-behvior` |
|---|---|---|---|---|---|---|---|
| `text` | Tekst kan worden bewerkt binnen de HTML-tags, maar alleen in eenvoudige tekstopmaak, zonder tekstopmaak, wordt deze doorgaans gebruikt voor titelcomponenten, bijvoorbeeld | Optioneel | Vereist | n.v.t. | Optioneel | n.v.t. | Optioneel |
| `richtext` | Tekst kan worden bewerkt met volledige tekstopties. RTE wordt weergegeven in het rechterdeelvenster | Optioneel | Vereist | n.v.t. | Optioneel | n.v.t. | Optioneel |
| `media` | Het bewerkbare element is een element, bijvoorbeeld een afbeelding of video | Optioneel | Vereist | Optioneel<br>lijst met afbeeldings- of videofiltercriteria die worden doorgegeven aan de elementenkiezer | Optioneel | n.v.t. | Optioneel |
| `container` | Het bewerkbare gedrag gedraagt zich als container voor componenten o.a. het Systeem van de Paragraaf. | Afhankelijkheden <br>zie hieronder | Afhankelijkheden <br>zie hieronder | Optioneel<br>een lijst met toegestane componenten | Optioneel | n.v.t. | n.v.t. |
| `component` | Het bewerkbare item is een component. Er wordt geen extra functionaliteit aan toegevoegd. Het is verplicht beweegbare/verhandelbare delen van het DOM aan te geven en de spoorstaaf en de velden ervan te openen. | Vereist | n.v.t. | n.v.t. | Optioneel | Optioneel | n.v.t. |
| `reference` | Het bewerkbare item is een verwijzing, bijvoorbeeld een inhoudsfragment, een ervaringsfragment of een product | Afhankelijkheden <br>zie hieronder | Afhankelijkheden <br>zie hieronder | Optioneel<br>lijst met filtercriteria voor Content Fragment, Product of Experience Fragment die worden doorgegeven aan de referentiekiezer | Optioneel | Optioneel | n.v.t. |

Afhankelijk van het gebruiksgeval `itemprop` of `itemid` al dan niet verplicht zijn. Bijvoorbeeld:

* `itemid` is vereist als u Content Fragments via GraphQL opvraagt en u de lijst in context bewerkbaar wilt maken.
* `itemprop` is vereist als u een component hebt die de inhoud van een Content Fragment waarnaar wordt verwezen, rendert en u de verwijzing in de component wilt bijwerken.

## Gedrag {#behaviors}

| `data-editor-behavior` | Beschrijving |
|---|---|
| `component` | Kan standalone tekst, richtext, en media simuleren componenten zo te laten zij ook beweegbaar en verwijderbaar op de pagina zijn |

## Aanvullende bronnen {#additional-resources}

Zie deze documenten voor meer informatie over de Universal Editor.

* [Introductie van Universal Editor](introduction.md) - Leer hoe u met de Universal Editor elk aspect van elke inhoud in een implementatie kunt bewerken, zodat u uitzonderlijke ervaringen kunt opdoen, de snelheid van de inhoud kunt verhogen en een geavanceerde ontwikkelaarservaring kunt bieden.
* [Inhoud ontwerpen met de Universal Editor](authoring.md) - Leer hoe eenvoudig en intuïtief het is voor inhoudsauteurs om inhoud te maken met de Universal Editor.
* [Inhoud publiceren met de Universal Editor](publishing.md) - Leer hoe de Universal Visual Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.
* [Aan de slag met de Universal Editor in AEM](getting-started.md) - Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.
* [Architectuur van Universal Editor](architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [Universal Editor-verificatie](authentication.md) - Leer hoe de Universal Editor wordt geverifieerd.
