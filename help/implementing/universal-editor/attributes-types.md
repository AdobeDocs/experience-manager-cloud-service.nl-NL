---
title: Kenmerken en itemtypen
description: Leer over de gegevensattributen en de punttypes die de Universele Redacteur vereist.
exl-id: 02795a31-244a-42b4-8297-2649125d7777
source-git-commit: 36be262a7949bc66f97f5483ff463d755f5f78e5
workflow-type: tm+mt
source-wordcount: '686'
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
| `data-aue-resource` | URL aan het middel, zie de sectie [Instrueer de Pagina van het document die Begonnen met de Universele Redacteur in AEM worden](getting-started.md#instrument-thepage) |
| `data-aue-prop` | Kenmerk van de bron, zie de sectie [Instrueer de Pagina van het document die Begonnen met de Universele Redacteur in AEM worden](getting-started.md#instrument-thepage) |
| `data-aue-type` | [Type van het bewerkbare item](#item-types) (bijvoorbeeld tekst, afbeelding en verwijzing) |
| `data-aue-filter` | Definieert welke verwijzingen kunnen worden gebruikt |
| `data-aue-label` | Hiermee definieert u een aangepast label voor een selecteerbaar item dat in de editor wordt weergegeven <br>In geval van `data-aue-model` is ingesteld, wordt het label opgehaald via het model |
| `data-aue-model` | Definieert een model dat wordt gebruikt voor bewerkingen op basis van formulieren in de rail Eigenschappen |
| `data-aue-behavior` | Definieert de [gedrag van een instrumentatie](#behaviors)In een zelfstandige tekst of afbeelding kan een component bijvoorbeeld ook worden nagebootst om deze te verplaatsen of te verwijderen |

## Itemtypen {#item-types}

| `data-aue-type` | Beschrijving | `data-aue-resource` | `data-aue-prop` | `data-aue-filter` | `data-aue-label` | `data-aue-model` | `data-aue-behavior` |
|---|---|---|---|---|---|---|---|
| `text` | Tekst kan worden bewerkt binnen de HTML-tags, maar alleen in de eenvoudige tekstopmaak, zonder tekstopmaak, wordt deze doorgaans gebruikt voor titelcomponenten, bijvoorbeeld | Optioneel | Vereist | nvt | Optioneel | nvt | Optioneel |
| `richtext` | Tekst kan worden bewerkt met volledige tekstopties. RTE wordt weergegeven in het rechterdeelvenster | Optioneel | Vereist | nvt | Optioneel | nvt | Optioneel |
| `media` | Het bewerkbare element is bijvoorbeeld een afbeelding of video | Optioneel | Vereist | Optioneel<br>lijst met afbeeldings- of videofiltercriteria die worden doorgegeven aan de elementenkiezer | Optioneel | nvt | Optioneel |
| `container` | Het bewerkbare gedrag gedraagt zich als container voor componenten o.a. het Systeem van de Paragraaf. | Afhankelijkheden <br>zie hieronder | Afhankelijkheden <br>zie hieronder | Optioneel<br>een lijst met toegestane componenten | Optioneel | nvt | nvt |
| `component` | Het bewerkbare item is een component. Er wordt geen extra functionaliteit aan toegevoegd. Het is verplicht beweegbare/verhandelbare delen van het DOM aan te geven en de spoorstaaf en de velden ervan te openen. | Vereist | nvt | nvt | Optioneel | Optioneel | nvt |
| `reference` | Bewerkbaar is een verwijzing, bijvoorbeeld Inhoudsfragment, Ervaring Fragment of Product | Afhankelijkheden <br>zie hieronder | Afhankelijkheden <br>zie hieronder | Optioneel<br>lijst met filtercriteria voor Content Fragment, Product of Experience Fragment die worden doorgegeven aan de referentiekiezer | Optioneel | Optioneel | nvt |

Afhankelijk van het gebruiksgeval `data-aue-prop` of `data-aue-resource` al dan niet verplicht zijn. Bijvoorbeeld:

* `data-aue-resource` is vereist als u Content Fragments via GraphQL opvraagt en u de lijst in context bewerkbaar wilt maken.
* `data-aue-prop` is vereist voor het geval u een component hebt die de inhoud van een Content Fragment waarnaar wordt verwezen, rendert en u de verwijzing in de component wilt bijwerken.

## Gedrag {#behaviors}

| `data-aue-behavior` | Beschrijving |
|---|---|
| `component` | Wordt gebruikt om zelfstandige tekst, richtext en mediamimicomponenten toe te staan, zodat deze ook kunnen worden verplaatst en verplaatst op de pagina |
| `container` | Gebruikt om containers te laten behandelen als hun eigen componenten zodat zij beweegbaar en verhandelbaar op de pagina zijn |

## Aanvullende bronnen {#additional-resources}

Zie deze documenten voor meer informatie over de Universal Editor.

* [Introductie van Universal Editor](introduction.md) - Leer hoe u met de Universal Editor elk aspect van elke inhoud in een implementatie kunt bewerken, zodat u uitzonderlijke ervaringen kunt opdoen, de snelheid van de inhoud kunt verhogen en een geavanceerde ontwikkelaarservaring kunt bieden.
* [Inhoud ontwerpen met de Universal Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) - Leer hoe eenvoudig en intuïtief het is voor inhoudsauteurs om inhoud te maken met de Universal Editor.
* [Inhoud publiceren met de Universal Editor](/help/sites-cloud/authoring/universal-editor/publishing.md) - Leer hoe de Universal Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.
* [Aan de slag met de Universal Editor in AEM](getting-started.md) - Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.
* [Architectuur van Universal Editor](architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [Universal Editor-verificatie](authentication.md) - Leer hoe de Universal Editor wordt geverifieerd.
