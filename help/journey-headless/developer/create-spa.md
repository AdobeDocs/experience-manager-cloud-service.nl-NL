---
title: Optioneel - Hoe kunt u toepassingen voor één pagina maken (SPA) met Adobe Experience Manager (AEM)
description: In deze optionele vervolg van de AEM Headless Developer Journey leert u hoe AEM koploze levering kunt combineren met traditionele full-stack CMS-functies en hoe u bewerkbare SPA kunt maken met AEM Editor-framework.
exl-id: d74848f2-683e-49e1-9374-32596ca5d7d7
solution: Experience Manager
feature: Headless
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1259'
ht-degree: 0%

---

# Procedure voor het maken van toepassingen voor één pagina (SPA) met AEM {#create-spa}

In deze facultatieve voortzetting van de [AEM Headless Developer Journey](overview.md), leert u hoe AEM koploze levering met traditionele full-stack CMS-functies kan combineren. U leert ook hoe u bewerkbare SPA kunt maken met AEM SPA Editor-framework en externe SPA kunt integreren, waardoor bewerkingsmogelijkheden naar wens zijn.

## Het verhaal tot nu toe {#story-so-far}

Op dit punt had u het volledige [AEM Headless Developer Journey](overview.md) en begrijpen de grondbeginselen van de levering zonder kop in AEM, inclusief inzicht in:

* Het verschil tussen koploze en koprijke levering van inhoud.
* AEM functies zonder kop.
* Hoe te om Hoofdloze project te organiseren en te AEM.
* Hoe te om koploze inhoud in AEM te creëren.
* Hoe te om koploze inhoud in AEM terug te winnen en bij te werken.
* Hoe te om met een AEM Zwaardeloos project te leven.

Tot nu toe hebt u of met uw eerste AEM Headless-project gewoond of de kennis gehad dat te doen. Gefeliciteerd!

Waarom lees je deze extra, optionele voortzetting van de reis? U herinnert zich dat in de [Aan de slag](getting-started.md#integration-levels), werd besproken hoe AEM niet alleen hoofdloze levering en traditionele full-stack modellen steunt, maar hybride modellen steunt die de voordelen van allebei combineren. Hoewel niet het traditionele model zonder kop, kunnen dergelijke hybride modellen ongekende flexibiliteit aan bepaalde projecten aanbieden.

Dit artikel bouwt op uw kennis van AEM Headless voort door diepgaand te onderzoeken hoe u uw eigen single-page toepassingen (SPA) kunt tot stand brengen die in AEM editable zijn. Op deze manier kunt u inhoud maken en deze zonder problemen aan een SPA leveren, maar SPA kunt u deze in AEM bewerken.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe Toepassingen van één pagina worden ontwikkeld gebruikend het kader van AEM SPA Redacteur. Nadat u dit document hebt gelezen, moet u:

* Begrijp de basisfunctie van de SPA Editor.
* Zorg dat u weet aan welke vereisten een volledig bewerkbare SPA voor AEM moet voldoen.
* Begrijp hoe externe SPA in AEM kunnen worden geïntegreerd.
* Begrijp hoe rendering aan de serverzijde wel of niet kan worden geïmplementeerd.

## Eisen en voorwaarden {#requirements-prerequisites}

Er zijn verschillende vereisten voordat u met SPA begint te werken in AEM.

### Kennis {#knowledge}

* Ervaring op het gebied van ontwikkeling die SPA maakt met React of Angular
* Basisvaardigheden AEM het creëren van de Fragmenten van de Inhoud en het gebruiken van de redacteur
* Controleer of het document is gecontroleerd [Hoofdletters en headless in AEM](/help/implementing/developing/headful-headless.md) u kunt dus de verschillende mogelijke niveaus van SPA integratie begrijpen .

### Gereedschappen {#tools}

* Sandbox-toegang voor het testen van de implementatie van uw project
* Local development instance for data modelling and testing
* Bestaande externe SPA (optioneel, afhankelijk van het gekozen integratiemodel)
* Projectarchetype AEM

## Wat is een SPA? {#what-is-a-spa}

Een toepassing van één pagina (SPA) verschilt van een conventionele pagina in die zin dat deze wordt weergegeven op de client en voornamelijk wordt aangedreven door JavaScript. Hierbij wordt uitgegaan van Ajax-aanroepen om gegevens te laden en de pagina dynamisch bij te werken. De meeste of alle inhoud wordt één keer opgehaald in één pagina die wordt geladen met extra bronnen die indien nodig asynchroon worden geladen, op basis van gebruikersinteractie met de pagina.

Deze functionaliteit vermindert de behoefte aan pagina&#39;s te vernieuwen en biedt de gebruiker een ervaring die naadloos, snel is en meer als een native app-ervaring voelt.

Met de AEM SPA Editor kunnen front-end ontwikkelaars SPA maken die in een AEM site kunnen worden geïntegreerd, zodat de auteurs van de inhoud de SPA inhoud net zo gemakkelijk kunnen bewerken als elke andere AEM.

## Waarom een SPA? {#why-spa}

Door sneller, vloeiend en meer als een native toepassing te zijn, wordt een SPA een aantrekkelijke ervaring. Het is niet alleen goed voor de bezoeker van de webpagina, maar ook voor marketeers en ontwikkelaars vanwege de aard van de SPA.

Voor een volledige beschrijving van SPA en waarom u deze zou gebruiken, raadpleegt u de [extra middelen](#additional-resources) voor koppelingen naar uitgebreidere documentatie.

## Hoe AEM handgrepen SPA

Bij het ontwikkelen van toepassingen voor één pagina op AEM wordt ervan uitgegaan dat de ontwikkelaar aan de voorzijde de aanbevolen standaardprocedures voor het maken van een SPA in acht neemt. Als front-end ontwikkelaar, als u deze algemene beste praktijken en een paar AEM-specifieke principes volgt, wordt uw SPA functioneel met AEM en zijn inhoud-creatie mogelijkheden.

* **Overdraagbaarheid** - De onderdelen van de SPA moeten zo draagbaar mogelijk zijn, net als alle andere onderdelen. De SPA moet met draagbare en herbruikbare onderdelen worden gebouwd.
* **Sitestructuur AEM stations** - De front-end ontwikkelaar maakt componenten en bezit hun interne structuur, maar baseert zich op AEM om de inhoudsstructuur van de plaats te bepalen.
* **Dynamische rendering** - Alle rendering moet dynamisch zijn.
* **Dynamische routering** - De SPA is verantwoordelijk voor het verpletteren en AEM luistert aan het en haalt gebaseerd op het. Om het even welk verpletteren zou ook dynamisch moeten zijn.

Voor een volledige beschrijving van hoe AEM handvatten SPA, zie [extra middelen](#additional-resources) voor koppelingen naar uitgebreidere documentatie.

## De AEM SPA Editor {#aem-spa-editor}

Sites die zijn gemaakt met behulp van gemeenschappelijke SPA, zoals React en Angular, laden de inhoud via dynamische JSON. Zij verstrekken niet de structuur van de HTML die voor de AEM Redacteur van de Pagina noodzakelijk is om bewerkingscontroles te kunnen plaatsen.

Om het bewerken van SPA binnen AEM mogelijk te maken, is een toewijzing tussen de JSON-uitvoer van de SPA en het inhoudsmodel in de AEM opslagplaats nodig, zodat u wijzigingen in de inhoud kunt opslaan.

SPA ondersteuning in AEM introduceert een dunne JavaScript-laag die communiceert met de SPA JavaScript-code wanneer deze wordt geladen in de Pagina-editor waarmee gebeurtenissen kunnen worden verzonden. De locatie voor de bewerkingsbesturingselementen kan worden geactiveerd om in-context bewerken toe te staan. Deze eigenschap bouwt op het concept van het Eindpunt van de Diensten van de Inhoud API voort omdat de inhoud van de SPA door als Diensten van de Inhoud moet worden geladen.

Voor een volledige beschrijving van de AEM SPA Editor raadpleegt u de [extra middelen](#additional-resources) voor koppelingen naar uitgebreidere documentatie.

## Bestaande SPA aanpassen {#existing-spas}

Als u een bestaande SPA hebt, AEM ondersteuning voor het insluiten ervan in AEM, zodat deze zichtbaar is voor de auteurs van de inhoud in de AEM Editor. Deze mogelijkheid kan nuttig zijn om de inhoud die ze maken, weer te geven door middel van Content Fragments in de context van de eindtoepassing waarin deze wordt gebruikt.

Bovendien kunt u met slechts kleine wijzigingen bepaalde bewerkingsmogelijkheden voor de externe SPA inschakelen in de AEM Editor.

Met de component RemotePage kan een externe SPA in AEM worden weergegeven.

Voor een volledige beschrijving van hoe u een externe SPA bewerkbaar kunt maken in AEM, raadpleegt u de [extra middelen](#additional-resources) voor koppelingen naar uitgebreidere documentatie.

## Volgende functies {#what-is-next}

Als u wilt beginnen met het ontwikkelen van uw eigen SPA voor AEM, bekijkt u de volgende documenten:

* [SPA WKND-zelfstudie](/help/implementing/developing/hybrid/wknd-tutorial.md)
* [Aan de slag met Reageren](/help/implementing/developing/hybrid/getting-started-react.md)
* [Aan de slag met Angular](/help/implementing/developing/hybrid/getting-started-angular.md)

Als u een bestaande SPA moet aanpassen om het in AEM te gebruiken, herzie de volgende documenten:

* [De RemotePage-component](/help/implementing/developing/hybrid/remote-page.md)
* [Een externe SPA bewerken in AEM](/help/implementing/developing/hybrid/editing-external-spa.md)

Zie hieronder voor [extra middelen](#additional-resources) dat kan u dieper op SPA onderwerpen in AEM brengen.

## Aanvullende bronnen {#additional-resources}

Hieronder vindt u een aantal aanvullende bronnen die dieper ingaan op bepaalde concepten die in dit document worden genoemd.

* [Hoofdletters en headless in AEM](/help/implementing/developing/headful-headless.md) - Een beschrijving van de verschillende leveringsmodellen die in AEM beschikbaar zijn
* [SPA Inleiding en Analyse](/help/implementing/developing/hybrid/introduction.md) - Een goede inleiding tot SPA in AEM.
* [SPA ontwikkelen voor AEM](/help/implementing/developing/hybrid/developing.md) - Richtsnoeren voor de ontwikkeling van SPA voor AEM
* [Overzicht SPA Editor](/help/implementing/developing/hybrid/editor-overview.md) - Bijzonderheden over de werking van de SPA Editor
* [Rendering op de server](/help/implementing/developing/hybrid/ssr.md) - Hoe te om SSR voor AEM SPA te vormen
* [Referentiedocumenten SPA](/help/implementing/developing/hybrid/reference-materials.md) - JavaScript API verwijzingen en verbindingen aan de open-bron AEM SPA projecten GitHub
* [Inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments) - Inhoudsfragmenten maken
* [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) - Gemaakt sjabloon dat een minimaal, op best practices gebaseerd Adobe Experience Manager-project (AEM) maakt als startpunt voor uw website
