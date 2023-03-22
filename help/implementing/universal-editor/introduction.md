---
title: Universal Visual Editor Introductie
description: Leer hoe de Universele Visuele Redacteur (a.k.a. Met de Universal Editor) kunt u WYSIWYG-bewerkingen (what-you-see-is-what-you-get) zonder kop en met veel titel uitvoeren. Begrijp hoe het inhoudsauteurs kan helpen uitzonderlijke ervaringen te leveren, hun inhoudssnelheid te verhogen en hoe een geavanceerde ontwikkelaarservaring biedt.
source-git-commit: f242abbd7f53c523667d1d56a0f5b913bb26dee0
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 0%

---


# Universal Visual Editor Introductie {#introduction}

Leer hoe de Universele Visuele Redacteur (a.k.a. Met de Universal Editor) kunt u WYSIWYG-bewerkingen (what-you-see-is-what-you-get) zonder kop en met veel titel uitvoeren. Begrijp hoe het inhoudsauteurs kan helpen uitzonderlijke ervaringen te leveren, hun inhoudssnelheid te verhogen en hoe een geavanceerde ontwikkelaarservaring biedt.

## Achtergrond {#background}

Het krachtigste gereedschap voor de auteur van AEM inhoud is de pagina-editor geweest. De paginaredacteur biedt een intuïtieve, visuele, in-context WYSIWYG auteurservaring aan die minimale opleiding vereist en auteurs precies toont hoe de inhoud zal verschijnen.

De pagina-editor kan echter alleen AEM pagina-inhoud, -structuur en de componenten in de pagina bewerken. De huidige inhoud is echter zelden afkomstig van één locatie. De Universele Redacteur biedt de zelfde op-plaats het uitgeven ervaring aan zoals de paginaredacteur maar voor om het even welk aspect van om het even welke inhoud in om het even welke implementatie.

## True Universal {#universal}

De Universal Editor kan van instrumenten worden voorzien voor elke implementatie, voor elke inhoud en voor elk aspect van de inhoud.

![Wat maakt het universeel?](assets/universal.png)

### Willekeurige implementatie {#any-implementation}

Omdat ervaringen op verschillende manieren kunnen worden opgebouwd, kan elke implementatie gebruikmaken van de Universal Editor, zodat ontwerpers in hun context kunnen bewerken.

Gebruikers denken vaak dat een implementatie zonder kop de auteurs beperkt tot het bewerken van alle inhoud in een op formulieren gebaseerde gebruikersinterface, maar dat geldt niet voor de universele editor

De vereisten voor een implementatie om gebruik te maken van de Universal Editor zijn zeer duidelijk en ondersteunen:

* **Elke architectuur** - Server-side rendering, edge-side rendering, client-side rendering, enzovoort.
* **Willekeurig kader** - Vanilla AEM, of een ander raamwerk van derden zoals React, Next.js, Angular, enz.
* **Willekeurig hosten** - Kan lokaal worden gehost op AEM of op een extern domein

### Willekeurige inhoud {#any-content}

De auteur van een inhoud moet dezelfde krachtige bewerkingservaring hebben als de AEM pagina-editor. Maar in de Universal Editor kunnen auteurs van inhoud bewerken **alle** inhoud visueel en in context en ondersteunt:

* **Paginastructuren AEM** - Genest `cq:Components` van `cq:Pages`, met inbegrip van ervaringsfragmenten
* **Inhoudsfragmenten AEM** - Inhoud uit inhoudsfragmenten bewerken zoals deze in de context van de ervaring worden weergegeven.
* **Documenten** - Het bewijs van concepten heeft getoond dat ook Word, Excel, de Documenten van Google of van de Prijsverhoging de zelfde manier (dit is WIP) kunnen worden uitgegeven.

### Willekeurig aspect {#any-aspect}

Voor de auteur van inhoud gaat de inhoud niet alleen over de informatie in de inhoud, maar ook over de manier waarop deze wordt gerenderd en ontvangen. De inhoud wordt geleverd met extra meta-gegevens en instrumentatieregels, die de Universele Redacteur kan begrijpen en uitgeven met inbegrip van:

* **Lay-out en stijl toepassen** - Door gebruik te maken van een stijlsysteem kunnen de marketingdeskundige en de auteur van de inhoud verschillende stijlen toepassen op de inhoud ervan en verschillende lay-outs maken voor de inhoud, zoals kolommen, carrousels, tabs, accordeons, enz.

## Waarde {#value}

Door de ervaring voor het bewerken van inhoud los te koppelen van een bepaald systeem voor het leveren van inhoud, wordt de editor echt universeel en flexibel, zodat de auteur van de inhoud uitzonderlijke ervaringen kan opdoen, de snelheid van de inhoud kan verhogen en een geavanceerde ontwikkelaarservaring kan bieden.

![De waarde van de universele editor](assets/value.png)

* **Uitzonderlijke ervaringen leveren** - Om artsen in staat te stellen een aantrekkelijke ervaring voor bezoekers te creëren, staat de Universele Redacteur artsen toe om de inhoud in de context van de voorproef tot stand te brengen en uit te geven. Hierdoor kunnen ze inhoud maken die past bij het ontwerp van de ervaring en die een zinvolle reis voor bezoekers is.
* **Snelheid inhoud verhogen** - Als u de beheerworkflow van artsen wilt stroomlijnen, kunt u met de Universal Editor inhoud bewerken in de voorvertoning. Zo kunt u artsen begeleiden door alleen de opties weer te geven die relevant zijn voor die context en de workflow onafhankelijk te maken van de inhoudsbronnen.
* **Recentere ontwikkelaarservaring** - Om het heterogene toepassingslandschap in de wereld te ondersteunen, is de Universal Editor volledig ontkoppeld en is hij technologisch gezien niet-afhankelijk, zodat ontwikkelaars hun voorkeurstechnologie kunnen gebruiken om de ervaring te implementeren.

## Universal Visual Editor en de Content Fragment Editor {#universal-editor-content-fragment-editor}

Op het eerste gezicht lijkt het misschien alsof de Universal Visual Editor en de Content Fragment Editor vergelijkbare bewerkingsmogelijkheden bieden. Deze editors bieden echter zeer verschillende mogelijkheden en vervullen verschillende taken van de marketingdeskundige.

### Inhoudsfragmenteditor {#content-fragment-editor}

Een marketingdeskundige wil inhoud maken zonder de layout ervan te hoeven omschrijven, zodat deze in een groot aantal contexten opnieuw kan worden gebruikt.

* De onderliggende taak die moet worden uitgevoerd, is het schalen van de inhoudsstrategie.

### Universal Visual Editor {#universal-editor}

Een marketingdeskundige wil inhoud maken die is toegesneden op de lay-out van een bepaalde context en die een uitzonderlijke ervaring biedt.

* De onderliggende taak die u moet uitvoeren, is op overtuigende wijze verbinding maken met de lezers.

## Wegenkaart {#road-map}

Het is belangrijk om op te merken dat de Universele Redacteur een werk in uitvoering is en sommige van de mogelijkheden die in dit document worden beschreven een visie van de definitieve redacteur zijn en niet noodzakelijk representatief voor zijn huidige mogelijkheden zijn.

Neem contact op met uw Adobe-contactpersoon voor meer informatie over de functies die u voor de Universal Editor wilt gaan gebruiken.

## Aanvullende bronnen {#additional-resources}

Zie deze documenten voor meer informatie over de Universal Editor.

* [Inhoud ontwerpen met de Universal Editor](authoring.md) - Leer hoe eenvoudig en intuïtief het is voor inhoudsauteurs om inhoud te maken met de Universal Editor.
* [Aan de slag met de Universal Editor in AEM](getting-started.md) - Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.
* [Architectuur van Universal Editor](architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [Kenmerken en typen](attributes-types.md) - Meer informatie over de gegevenskenmerken en typen die de Universal Editor nodig heeft.
* [Universal Editor-verificatie](authentication.md) - Leer hoe de Universal Editor wordt geverifieerd.
