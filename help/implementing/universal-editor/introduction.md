---
title: Introductie van Universal Editor
description: Leer hoe u met de Universal Editor het bewerken van 'what-you-see-is-what-you-get' (WYSIWYG) mogelijk maakt voor een headless- en headful-ervaring. Begrijp hoe het inhoudsauteurs kan helpen uitzonderlijke ervaringen te leveren, hun inhoudssnelheid te verhogen en hoe een geavanceerde ontwikkelaarservaring biedt.
exl-id: d4fc2384-a0f5-4a6f-9572-62749786be4c
feature: Developing
role: Admin, Architect, Developer
source-git-commit: b8d56873b7bc23295fefc35a826b8047c626649e
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---


# Introductie van Universal Editor {#introduction}

De Universal Editor is een veelzijdige visuele editor die deel uitmaakt van Adobe Experience Manager Sites. Auteurs kunnen hiermee &#39;what-you-see-is-what-you-get&#39; (WYSIWYG)-bewerkingen uitvoeren van elke headless- of headful-ervaring. Begrijp hoe het inhoudsauteurs kan helpen uitzonderlijke ervaringen en hoe het ongeëvenaarde vrijheid voor ontwikkelaars biedt.

## Achtergrond {#background}

De Universele Redacteur verstrekt een efficiënte en intuïtieve in-context auteurservaring die minimale opleiding vereist. Met deze functie kunnen auteurs hun inhoud rechtstreeks beheren in de context van de webervaring en exact aangeven hoe deze wordt weergegeven aan de bezoekers. Aangezien het een ware redacteur als dienst en over het algemeen flexibeler is, is het van plan uiteindelijk de Redacteur van de Pagina te vervangen.

Auteurs profiteren van de flexibiliteit van de Universal Editor, omdat deze ondersteuning biedt voor dezelfde visuele bewerking voor alle vormen van AEM inhoud: bewerking op plaats en compositie van de layout is mogelijk op dezelfde manier voor zowel inhoudfragmenten als paginacomponenten. De twee vormen van inhoud kunnen zelfs worden uitgegeven wanneer het tonen zij aan zij in een Webervaring, zonder auteurs te moeten van context veranderen. Dit is een enorme verbetering in vergelijking met vorige editors in AEM slechts één type inhoud.

Ontwikkelaars profiteren van de veelzijdigheid van de Universal Editor, omdat deze ook werkelijke ontkoppeling van de implementatie ondersteunt. Het stelt ontwikkelaars in staat om vrijwel elk kader of architectuur van hun keuze te gebruiken, zonder enige SDK of technologiebeperkingen op te leggen. Deze flexibiliteit maakt het zelfs gemakkelijk om bestaande Web-apps voor de universele redacteur zonder het moeten te moeten opnieuw opbouwen.

## True Universal {#universal}

De Universal Editor kan van instrumenten worden voorzien voor elke implementatie, voor elke inhoud en voor elk aspect van de inhoud.

![ wat maakt het universeel ](assets/universal.png)

### Willekeurige implementatie {#any-implementation}

Omdat de ervaringen op vele verschillende manieren kunnen worden gebouwd, kan om het even welke implementatie de Universele Redacteur gebruiken zodat kunnen de auteurs in-context het uitgeven uitvoeren.

Gebruikers denken vaak dat een implementatie zonder kop de auteurs beperkt tot het bewerken van alle inhoud in een op formulieren gebaseerde gebruikersinterface, maar dit is niet het geval met de universele editor

De vereisten voor een implementatie om de Universele Redacteur te gebruiken zijn recht-voorwaarts en steunen het volgende:

* **Om het even welke Architectuur** - server-kant teruggeven, rand-kant teruggeven, cliënt-kant teruggeven, etc.
* **Om het even welk Kader** - Vanilla AEM, of om het even welk derdekader zoals React, Next.js, Angular, etc.
* **om het even welk Hosting** - kan plaatselijk aan AEM, of op een ver domein worden ontvangen

### Willekeurige inhoud {#any-content}

De auteur van een inhoud moet dezelfde krachtige bewerkingservaring hebben als de AEM pagina-editor. Maar de Universele Redacteur staat inhoudsauteurs toe om **om het even welke** inhoud visueel en in context uit te geven en steunt:

* **AEM de Structuren van de Pagina** - genestelde `cq:Components` van `cq:Pages`, met inbegrip van de Fragmenten van de Ervaring
* **AEM de Fragmenten van de Inhoud** - geef inhoud van de Fragmenten van de Inhoud uit aangezien zij in-context van de ervaring verschijnen.
* **Documenten** - het Bewijs van concepten heeft getoond dat ook Word, Excel, de Documenten van Google of de documenten van de Prijsverhoging de zelfde manier (dit is WIP) kunnen ook worden uitgegeven.

### Willekeurig aspect {#any-aspect}

Voor de auteur van inhoud gaat de inhoud niet alleen over de informatie in de inhoud, maar ook over de manier waarop deze wordt gerenderd en ontvangen. De inhoud wordt geleverd met extra meta-gegevens en instrumentatieregels, die de Universele Redacteur kan begrijpen en uitgeven met inbegrip van:

* **Toepassend Lay-out &amp; Stijl** - door een stijlsysteem te gebruiken, kunnen de marketing deskundige en de inhoudauteur verschillende stijlen op hun inhoud toepassen en verschillende lay-outs voor de inhoud zoals kolommen, carrousels, lusjes, accordeons, etc. tot stand brengen.

## Waarde {#value}

Door de ervaring voor het bewerken van inhoud los te koppelen van een bepaald systeem voor het leveren van inhoud, wordt de editor echt universeel en flexibel, zodat de auteur van de inhoud uitzonderlijke ervaringen kan opdoen, de snelheid van de inhoud kan verhogen en een geavanceerde ontwikkelaarservaring kan bieden.

![ de waarde van de Universele Redacteur ](assets/value.png)

* **lever Uitzonderlijke Ervaringen** - om artsen toe te laten om een dwingende ervaring voor bezoekers tot stand te brengen, staat de Universele Redacteur artsen toe om de inhoud in de context van de voorproef tot stand te brengen en uit te geven. Hierdoor kunnen ze inhoud maken die past bij het ontwerp van de ervaring en die een zinvolle reis voor bezoekers is.
* **Verhoog de Snelheid van de Inhoud** - om het beheerswerkschema van artsen te stroomlijnen, staat de Universele Redacteur het uitgeven inhoud binnen de voorproef toe om artsen te begeleiden door slechts de opties te tonen die voor die context relevant zijn en het werkschema onafhankelijk van de inhoudsbronnen maakt.
* **Van de meest recente Ervaring van de Ontwikkelaar van 0} - om echt-wereld heterogeen toepassingslandschap te steunen, is de Universele Redacteur volledig ontkoppeld en technologie-agnostisch, toestaand ontwikkelaars om hun aangewezen technologiestapel te gebruiken om de ervaring uit te voeren.**

## De Universal Editor en de Content Fragment Editor {#universal-editor-content-fragment-editor}

Op het eerste gezicht lijken de Universal Editor en de Content Fragment Editor vergelijkbare bewerkingsmogelijkheden. Deze editors bieden echter zeer verschillende mogelijkheden en vervullen verschillende taken van de marketingdeskundige.

### Inhoudsfragmenteditor {#content-fragment-editor}

Een marketingdeskundige wil inhoud maken zonder de layout ervan te hoeven omschrijven, zodat deze in een groot aantal contexten opnieuw kan worden gebruikt.

* De onderliggende taak die moet worden uitgevoerd, is het schalen van de inhoudsstrategie.

### Universele editor {#universal-editor}

Een marketingdeskundige wil inhoud maken die is toegesneden op de lay-out van een bepaalde context en die een uitzonderlijke ervaring biedt.

* De onderliggende taak die u moet uitvoeren, is op overtuigende wijze verbinding maken met de lezers.

## Beperkingen {#limitations}

Houd rekening met de volgende beperkingen wanneer u de Universal Editor verkent en de implementatie ervan in uw eigen projecten doorvoert.

* Niet meer dan 25 AEM bronnen (Content Fragments, pages, Experience Fragments, Assets, enz.) moeten verwijzingen zijn als instrumentatie op één pagina.
* AEM as a Cloud Service en [ AEM 6.5 ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction) zijn de enige gesteunde AEM achtergronden.
* AEM as a Cloud Service-release `2023.8.13099` of hoger is vereist.
* Inhoudsauteurs moeten hun eigen individuele Experience Cloud-accounts hebben.
* Als onderdeel van AEM ondersteunt de Universal Editor dezelfde desktopbrowsers als AEM.
   * Mobiele versies van deze browsers worden niet ondersteund.

{{ue-ip-allow-lists}}

## Volgende stappen {#next-steps}

Gelieve te zien het document [ Universele Gevallen van het Gebruik van de Redacteur en het Leren Wegen ](/help/implementing/universal-editor/use-cases.md) om meer over gemeenschappelijke gebruiksgevallen voor de Universele Redacteur te leren en de juiste documentatiemiddelen te ontdekken om u in uw project te steunen.
