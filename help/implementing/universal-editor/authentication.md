---
title: Universal Editor-verificatie
description: Leer hoe de Universele Redacteur het Systeem van Identity Management van de Adobe (IMS) voor authentificatie gebruikt.
exl-id: fb86c510-3c41-4511-81b7-1bdf2f5e7dd3
source-git-commit: 9d88d9b6d3315f34ca6819820b4b4306ba901390
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# Universal Editor-verificatie {#authentication}

Leer hoe de Universal Editor wordt geverifieerd.

{{universal-editor-status}}

## Opties {#options}

De Universele Redacteur gebruikt de authentificatie van het Systeem van Identity Management van de Adobe (IMS), die via Verenigde Shell wordt verstrekt.

Alle toepassingen/externe pagina&#39;s zijn verantwoordelijk voor verificatie op vereiste back-endsystemen. De universele dienst van de Redacteur heeft deze authentificatie aan achterste systemen nodig om verrichtingen CRUD uit te voeren aangezien het een standalone dienst is.

## Standaardstroom {#standard-flow}

Dit is de oplossing voor AEM as a Cloud Service en AMS die IMS gebruiken om de Universele redacteur te gebruiken.

Om de Universele Redacteur te gebruiken, moet de gebruiker in Verenigde Shell worden geregistreerd die tegen IMS voor authentiek verklaart. Het opgegeven IMS-token wordt opgeslagen in de gebruikerssessiewinkel.

Wanneer een gebruiker een CRUD verrichting uitvoert, wordt een vraag verzonden naar de Universele dienst van de Redacteur met het IMS dragerteken in de kopbal van HTTP. De universele dienst van de Redacteur gebruikt dan het dragerteken om het verzoek tegen het AEM achtergrondsysteem voor authentiek te verklaren om verrichtingen in de naam van de gebruiker uit te voeren.

![Standaardverificatiestroom](assets/standard-flow.png)

## Aanvullende bronnen {#additional-resources}

Zie deze documenten voor meer informatie over de Universal Editor.

* [Introductie van Universal Editor](introduction.md) - Leer hoe u met de Universal Editor elk aspect van elke inhoud in een implementatie kunt bewerken, zodat u uitzonderlijke ervaringen kunt opdoen, de snelheid van de inhoud kunt verhogen en een geavanceerde ontwikkelaarservaring kunt bieden.
* [Inhoud ontwerpen met de Universal Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) - Leer hoe eenvoudig en intuïtief het is voor inhoudsauteurs om inhoud te maken met de Universal Editor.
* [Inhoud publiceren met de Universal Editor](/help/sites-cloud/authoring/universal-editor/publishing.md) - Leer hoe de Universal Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.
* [Aan de slag met de Universal Editor in AEM](getting-started.md) - Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.
* [Architectuur van Universal Editor](architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [Kenmerken en typen](attributes-types.md) - Meer informatie over de gegevenskenmerken en typen die de Universal Editor nodig heeft.
