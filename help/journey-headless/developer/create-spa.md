---
title: Optioneel - Hoe kan ik toepassingen voor één pagina maken met Adobe Experience Manager (AEM)?
description: In deze facultatieve voortzetting van de Reis van de Ontwikkelaar van AEM Headless, leert u hoe AEM koploze levering met traditionele full-stack eigenschappen van CMS kan combineren en hoe u editable SPAs kunt tot stand brengen gebruikend het kader van de Redacteur van het KUUROORD van AEM.
exl-id: d74848f2-683e-49e1-9374-32596ca5d7d7
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 0%

---

# Hoe te om de Toepassingen van de Enige Pagina (SPAs) met AEM te creëren {#create-spa}

In deze facultatieve voortzetting van de [&#x200B; Hoofdloze Reis van de Ontwikkelaar van AEM &#x200B;](overview.md), leert u hoe AEM koploze levering met traditionele full-stack eigenschappen van CMS kan combineren. U leert ook hoe u editable SPAs kunt tot stand brengen gebruikend het kader van de Redacteur van het KUUROORD van AEM, en externe SPAs integreren, toelatend het uitgeven mogelijkheden zoals vereist.

## Het verhaal tot nu toe {#story-so-far}

Op dit punt, zou u de volledige [&#x200B; Reis van de Ontwikkelaar van AEM Headless &#x200B;](overview.md) moeten voltooien en de grondbeginselen van hoofdloze levering in AEM begrijpen met inbegrip van het begrip van:

* Het verschil tussen koploze en koprijke levering van inhoud.
* AEM-functies zonder kop.
* Hoe organiseren en AEM Headless-project.
* Hoe u inhoud zonder kop maakt in AEM.
* Inhoud zonder kop ophalen en bijwerken in AEM.
* Hoe ga je leven met een AEM Headless-project.

Tot nu toe hebt u ofwel gewoond met uw eerste AEM Headless-project, ofwel hebt u de kennis om dat te doen. Gefeliciteerd!

Waarom lees je deze extra, optionele voortzetting van de reis? U herinnert zich dat in [&#x200B; Begonnen &#x200B;](getting-started.md#integration-levels), het werd besproken hoe AEM niet alleen hoofdloze levering en traditionele full-stack modellen steunt, maar hybride modellen steunt die de voordelen van allebei combineren. Hoewel niet het traditionele model zonder kop, kunnen dergelijke hybride modellen ongekende flexibiliteit aan bepaalde projecten aanbieden.

Dit artikel bouwt op uw kennis van AEM Headless voort door diepgaand te onderzoeken hoe u uw eigen single-page toepassingen (SPAs) kunt tot stand brengen die in AEM editable zijn. Op deze manier, kunt u inhoud tot stand brengen en het leiden tot een KUUROORD, maar dat KUUROORD editable in AEM blijft.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe Toepassingen van de Enige Pagina gebruikend het kader van de Redacteur van AEM SPA worden ontwikkeld. Nadat u dit document hebt gelezen, moet u:

* Begrijp de basisfunctie van de Redacteur van het KUUROORD.
* Weet de vereisten voor de bouw van volledig editable SPA voor AEM.
* Begrijp hoe externe SPAs in AEM kan worden geïntegreerd.
* Begrijp hoe rendering aan de serverzijde wel of niet kan worden geïmplementeerd.

## Eisen en voorwaarden {#requirements-prerequisites}

Er zijn verscheidene vereisten alvorens u met SPAs in AEM begint te werken.

### Kennis {#knowledge}

* Ervaring met het maken van SPA&#39;s met React- of Angular-frameworks
* Basisvaardigheden van AEM die tot de Fragmenten van de Inhoud leiden en redacteur gebruiken
* Ben zeker om het document [&#x200B; te herzien Kopieer en Zwaartepunt in AEM &#x200B;](/help/implementing/developing/headful-headless.md) zodat kunt u de diverse niveaus van de integratie van het KUUROORD mogelijk begrijpen.

### Gereedschappen {#tools}

* Sandbox-toegang voor het testen van de implementatie van uw project
* Local development instance for data modelling and testing
* Bestaande externe SPA (facultatief, afhankelijk van welk integratiemodel wordt gekozen)
* AEM Project Archetype

## Wat is een SPA? {#what-is-a-spa}

Een single-page toepassing (SPA) verschilt van een conventionele pagina in die zin dat het cliënt-kant wordt teruggegeven en hoofdzakelijk JavaScript-gedreven, die op Ajax vraag baseert om gegevens te laden en dynamisch de pagina bij te werken. De meeste of alle inhoud wordt één keer opgehaald in één pagina die wordt geladen met extra bronnen die indien nodig asynchroon worden geladen, op basis van gebruikersinteractie met de pagina.

Deze functionaliteit vermindert de behoefte aan pagina&#39;s te vernieuwen en biedt de gebruiker een ervaring die naadloos, snel is en meer als een native app-ervaring voelt.

De redacteur van AEM SPA staat front-end ontwikkelaars toe om SPAs tot stand te brengen die in een plaats van AEM kan worden geïntegreerd, toestaand de inhoudsauteurs om de inhoud van het KUUROORD zo gemakkelijk als om het even welke andere inhoud van AEM uit te geven.

## Waarom een SPA? {#why-spa}

Door sneller, dynamisch, en meer als een inheemse toepassing te zijn, wordt een KUUROORD een aantrekkelijke ervaring. Het is niet alleen goed voor de bezoeker van de webpagina, maar ook voor marketers en ontwikkelaars vanwege de aard van de manier waarop SPA&#39;s werken.

Voor een volledige beschrijving van SPAs en waarom u hen zou gebruiken, zie de [&#x200B; extra middelen &#x200B;](#additional-resources) sectie voor verbindingen aan diepgaandere documentatie.

## Hoe AEM SPA&#39;s afhandelt

Het ontwikkelen van enige paginatoepassingen op AEM veronderstelt dat de front-end ontwikkelaar standaardbeste praktijken wanneer het creëren van een SPA naleeft. Als front-end ontwikkelaar, als u deze algemene beste praktijken en een paar AEM-specifieke principes volgt, wordt uw SPA functioneel met AEM en zijn inhoud-creatie mogelijkheden.

* **Portability** - zoals met om het even welke componenten, zouden de componenten van het KUUROORD moeten worden gebouwd om zo draagbaar mogelijk te zijn. Het KUUROORD zou met draaglijk en herbruikbare componenten moeten worden gebouwd.
* **AEM drijft de Structuur van de Plaats van de Plaats** - de front-end ontwikkelaar leidt tot componenten en bezit hun interne structuur, maar baseert zich op AEM om de inhoudsstructuur van de plaats te bepalen.
* **Dynamische Rendering** - allen zou het teruggeven dynamisch moeten zijn.
* **Dynamisch Verpletterend** - het KUUROORD is verantwoordelijk voor het verpletteren en AEM luistert aan het en haalt die op het wordt gebaseerd. Om het even welk verpletteren zou ook dynamisch moeten zijn.

Voor een volledige beschrijving van hoe AEM SPAs behandelt, zie de [&#x200B; extra middelen &#x200B;](#additional-resources) sectie voor verbindingen aan diepgaande documentatie.

## De AEM SPA-editor {#aem-spa-editor}

De plaatsen die gebruikend gemeenschappelijke kaders van het KUUROORD, zoals React en Angular worden gebouwd, laden hun inhoud als dynamische JSON. Ze beschikken niet over de HTML-structuur die nodig is voor de AEM Page Editor om bewerkingsbesturingselementen te kunnen plaatsen.

Om het uitgeven van SPAs binnen AEM toe te laten, is een afbeelding tussen de output JSON van het KUUROORD en het inhoudsmodel in de bewaarplaats van AEM noodzakelijk zodat kunt u veranderingen in de inhoud bewaren.

De steun van het KUUROORD in AEM introduceert een dunne laag van JavaScript die met de code van JavaScript van het KUUROORD wanneer geladen in de Redacteur van de Pagina in wisselwerking staat waarmee de gebeurtenissen kunnen worden verzonden. De locatie voor de bewerkingsbesturingselementen kan worden geactiveerd om in-context bewerken toe te staan. Deze eigenschap bouwt op het concept van het Eindpunt van de Diensten van de Inhoud API voort omdat de inhoud van het KUUROORD als Diensten van de Inhoud moet worden geladen.

Voor een volledige beschrijving van de Redacteur van AEM SPA, zie de [&#x200B; extra middelen &#x200B;](#additional-resources) sectie voor verbindingen aan diepgaandere documentatie.

## Bestaande SPA&#39;s aanpassen {#existing-spas}

Als u een bestaande SPA hebt, biedt AEM ondersteuning voor het insluiten van de SPA in AEM, zodat deze zichtbaar is voor de auteurs van de inhoud in de AEM Editor. Deze mogelijkheid kan nuttig zijn om de inhoud die ze maken, weer te geven door middel van Content Fragments in de context van de eindtoepassing waarin deze wordt gebruikt.

Ook, met slechts kleine veranderingen, kunt u bepaalde het uitgeven capaciteit aan het externe KUUROORD binnen de Redacteur van AEM toelaten.

De component RemotePage staat het teruggeven van een externe SPA in AEM toe.

Voor een volledige beschrijving van hoe te om een externe KUUROORD editable in AEM te maken, zie de [&#x200B; extra middelen &#x200B;](#additional-resources) sectie voor verbindingen aan diepgaandere documentatie.

## Volgende functies {#what-is-next}

Ga als volgt te werk om uw eigen SPA&#39;s voor AEM te gaan ontwikkelen:

* [SPA WKND-zelfstudie](/help/implementing/developing/hybrid/wknd-tutorial.md)
* [Aan de slag met Reageren](/help/implementing/developing/hybrid/getting-started-react.md)
* [Aan de slag met Angular](/help/implementing/developing/hybrid/getting-started-angular.md)

Als u bestaande SPA moet aanpassen om het in AEM te gebruiken, herzie de volgende documenten:

* [De RemotePage-component](/help/implementing/developing/hybrid/remote-page.md)
* [Een externe SPA bewerken in AEM](/help/implementing/developing/hybrid/editing-external-spa.md)

Zie hieronder voor [&#x200B; extra middelen &#x200B;](#additional-resources) die u dieper in de onderwerpen van het KUUROORD in AEM kunnen nemen.

## Aanvullende bronnen {#additional-resources}

Hieronder vindt u een aantal aanvullende bronnen die dieper ingaan op bepaalde concepten die in dit document worden genoemd.

* [&#x200B; Kopieerbaar en Hoofdloos in AEM &#x200B;](/help/implementing/developing/headful-headless.md) - een beschrijving van de verschillende leveringsmodellen beschikbaar in AEM
* [&#x200B; Inleiding van het KUUROORD en Analyse &#x200B;](/help/implementing/developing/hybrid/introduction.md) - een goede inleiding aan SPAs in AEM.
* [&#x200B; het Ontwikkelen SPAs voor AEM &#x200B;](/help/implementing/developing/hybrid/developing.md) - Richtlijnen op hoe te om SPAs voor AEM te ontwikkelen
* [&#x200B; Overzicht van de Redacteur van het KUUROORD &#x200B;](/help/implementing/developing/hybrid/editor-overview.md) - Details van hoe de Redacteur van het KUUROORD werkt
* [&#x200B; Documenten van de Verwijzing van het KUUROORD &#x200B;](/help/implementing/developing/hybrid/reference-materials.md) - de verwijzingen van JavaScript API en verbindingen aan de open-bron projecten van AEM SPA GitHub
* [&#x200B; Fragmenten van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments) - hoe te om de Fragmenten van de Inhoud tot stand te brengen
* [&#x200B; Archetype van het Project van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=nl-NL) - Geweven malplaatje dat tot een minimaal, best-practices-gebaseerd project van Adobe Experience Manager (AEM) als uitgangspunt voor uw website leidt
