---
title: Sites ontwikkelen met behulp van de voorste pijplijn
description: Met de front-end pijpleiding wordt meer onafhankelijkheid gegeven aan front-end ontwikkelaars en het ontwikkelingsproces kan aanzienlijk sneller worden. In dit document worden enkele specifieke aspecten beschreven van het constructieproces aan de voorzijde die moeten worden vermeld.
exl-id: 996fb39d-1bb1-4dda-a418-77cdf8b307c5
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1169'
ht-degree: 0%

---


# Sites ontwikkelen met behulp van de voorste pijplijn {#developing-site-with-front-end-pipeline}

[Met de front-end pijplijn,](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) meer onafhankelijkheid wordt gegeven aan de front-end ontwikkelaars en het ontwikkelingsproces kan aanzienlijk sneller verlopen. In dit document wordt beschreven hoe dit proces werkt, samen met een aantal overwegingen, zodat u optimaal kunt profiteren van dit proces.

>[!TIP]
>
>Als u nog niet vertrouwd bent met hoe te om de front-end pijpleiding en de voordelen te gebruiken het kan brengen, controleer uit [Reis voor snel maken van site](/help/journey-sites/quick-site/overview.md) voor een voorbeeld van hoe te om een nieuwe plaats snel op te stellen en zijn thema volledig los van achterste-eindontwikkeling aan te passen.

## Front-end bouwcontract {#front-end-build-contract}

Vergelijkbaar met de [volledige-stapelomgeving,](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) de front-end pijpleiding heeft een eigen omgeving. De ontwikkelaars hebben wat flexibiliteit gebruikend deze pijpleiding zolang het volgende front-end bouwcontract wordt waargenomen.

De front-end pijpleiding vereist het front-end project Node.js om het te gebruiken `build` manuscriptrichtlijn om de bouwstijl te produceren die het opstelt. Dit komt omdat Cloud Manager de opdracht gebruikt `npm run build` om het plaatsbare project voor de front-end bouwt te produceren.

De daaruit voortvloeiende inhoud van de `dist` Deze map wordt uiteindelijk geïmplementeerd door Cloud Manager en fungeert als statische bestanden. Deze bestanden worden extern naar AEM gehost, maar worden via een `/content/...` URL op de geïmplementeerde omgeving.

## Node-versies {#node-versions}

De front-end bouwt milieu steunt de volgende versies Node.js.

* 12
* 14 (standaard)
* 16
* 18

U kunt de `NODE_VERSION` [omgevingsvariabele](/help/implementing/cloud-manager/environment-variables.md) om de gewenste versie in te stellen.

## Eén betrouwbare bron {#single-source-of-truth}

Een algemene goede praktijk is één enkele bron van waarheid te handhaven voor wat wordt ingezet aan AEM. Cloud Manager heeft als doel die ene bron van waarheid voor de hand te leggen. Aangezien de front-end pijplijn echter de ontkoppeling van de locatie voor delen van de code mogelijk maakt, ligt een extra verantwoordelijkheid in de correcte installatie van de front-end pijpleidingen. Er moet voorzichtig worden omgesprongen met het aanmaken van meerdere front-end pijpleidingen die op dezelfde locatie in dezelfde omgeving worden geïmplementeerd.

Daarom, en met name wanneer meerdere voorste pijpleidingen worden aangelegd, wordt aanbevolen een conventie voor systematische naamgeving te handhaven, zoals:

* De naam van de front-end module, die door `name` eigendom van de `package.json` moet de naam bevatten van de site waarop deze van toepassing is. Bijvoorbeeld voor een site die zich bevindt op `/content/wknd`De naam van de front-end module zou er ongeveer als volgt uitzien `wknd-theme`.
* Als een front-end module dezelfde Git-opslagplaats deelt met andere modules, moet de naam van de bijbehorende map gelijk zijn aan of dezelfde naam van de front-end module bevatten. Als de voorste module bijvoorbeeld een naam heeft `wknd-theme`zou de omsluitende mapnaam er ongeveer zo uitzien `wknd-theme-sources`.
* De naam van de front-end pijpleiding van de Manager van de Wolk zou ook de naam van de front-end module moeten bevatten en ook het milieu toevoegen waarop het (productie of ontwikkeling) opstelt. Bijvoorbeeld voor de genoemde front-end module `wknd-theme`, de pijpleiding zou kunnen worden genoemd iets als `wknd-theme-prod`.

Een dergelijke conventie moet op efficiënte wijze de volgende implementatiefouten voorkomen:

* Een front-end module toepassen op de verkeerde site
* Het creëren van veelvoudige front-end modules die de zelfde plaats toepassen, die elkaar zouden beschrijven
* Het creëren van veelvoudige front-end pijpleidingen voor de zelfde bronnen, die rasvoorwaarden kunnen veroorzaken, die de orde van plaatsingen niet waarborgen

## Scheiding van bezorgdheid {#separation-of-concerns}

Een andere goede praktijk die van toepassing is op elke scheiding van zorgen, is speciale aandacht te besteden aan de wijze waarop het contract dat de zorgen scheidt, wordt ontworpen en beheerd. In het geval van de front-end pijpleiding is het contract dat deze code scheidt van de rest de HTML en JSON die door de locatie worden weergegeven. Als die HTML en JSON stabiel blijven, dan levert de front-end pijpleiding zijn maximumwaarde door het front-end team volledig onafhankelijk te maken.

Er is momenteel geen specifiek vermogen om de full-stack pijpleiding synchroon met de front-end pijpleiding(en) in werking te stellen. Daarom moet bij de ontkoppeling van de ontwikkeling aan de voorzijde van de volledige stapelleiding extra aandacht worden besteed aan het contract dat deze twee aandachtsgebieden van elkaar scheidt. Dat contract is doorgaans de HTML en/of JSON die de Experience Manager afgeeft. Wijzigingen in dat contract moeten daarom goed worden gepland tussen de teams die de verschillende pijpleidingen exploiteren, zodat zij het eens worden over de wijze waarop de overeenkomstige wijzigingen moeten worden gesequenceerd.

De volgende stappen worden over het algemeen aanbevolen wanneer het nodig is om wijzigingen in de HTML en/of JSON-uitvoer uit te voeren die van invloed zijn op beide aandachtsgebieden.

1. Het back-end team stelt eerst een ontwikkelomgeving in met de nieuwe HTML en/of JSON-uitvoer.
   1. Via de full-stack pijplijn, voeren zij de code op die wordt vereist om de nieuwe HTML en/of output terug te geven JSON die gewenst is.
   1. Als dat aan een milieu is dat het front-end team niet eerder toegang tot had, dan moeten de volgende stappen worden uitgevoerd.
      1. URL: Het front-end team moet URL van die ontwikkelomgeving kennen.
      1. ACL: Het front-end team moet een lokale AEM gebruiker met iets gelijkend op &quot;Medewerkers&quot;rechten worden gegeven.
      1. Git: Het front-end team moet een afzonderlijke plaats van het Git voor de front-end module hebben die specifiek die ontwikkelomgeving richt.
         * Een gebruikelijke praktijk is het creëren van een `dev` vertakking, zodat de veranderingen die voor het ontwikkelmilieu worden gedaan dan gemakkelijk terug in het `main` tak die aan het productiemilieu moet worden opgesteld.
      1. Pijpleiding: Het front-end team moet een front-end pijpleiding hebben die aan de ontwikkelomgeving opstelt. Die pijpleiding zou de front-end module opstellen die typisch in wordt gevestigd `dev` vertakking, zoals beschreven in het vorige punt.
1. Het front-end team maakt dan CSS en JS code werk met zowel oude als nieuwe output.
   1. Zoals gebruikelijk, om plaatselijk te ontwikkelen:
      1. De `npx aem-site-theme-builder proxy` wordt uitgevoerd binnen de front-end module begint een volmachtsserver die om de inhoud van een AEM milieu verzoekt, terwijl het vervangen van de CSS en JS dossiers van de front-end module met degenen van de lokale `dist` map.
      1. Het vormen van `AEM_URL` variabele in het verborgen `.env` kan het bestand bepalen vanuit welke AEM omgeving de lokale proxyserver de inhoud gebruikt.
      1. De waarde van dit wijzigen `AEM_URL` kunt u daarom schakelen tussen de productie- en ontwikkelomgevingen om de CSS en JS aan te passen aan beide omgevingen.
      1. Het moet met de ontwikkelomgeving werken die de nieuwe output teruggeeft en met het productiemilieu dat de oude output teruggeeft.
   1. Het front-end werk wordt voltooid wanneer de bijgewerkte front-end module voor beide milieu&#39;s werkt, en aan allebei wordt opgesteld.
1. Het back-end team kan de productieomgeving dan bijwerken door de code in te voeren die de nieuwe HTML en/of JSON-uitvoer via de full-stack pijplijn rendert.
1. Het front-end team kan dan hun CSS en JS opschonen en verwijderen wat slechts door de oude output nodig was, die laatste update aan productie via de front-end pijpleiding opstelt.

## Aanvullende bronnen {#additional-resources}

* [Sitethema&#39;s](/help/sites-cloud/administering/site-creation/site-themes.md) - Leer hoe AEM sitethema&#39;s kunnen worden gebruikt om de stijl en het ontwerp van uw site aan te passen.
* [Sitemenu AEM maken](https://github.com/adobe/aem-site-theme-builder) - Adobe biedt een AEM Site Theme Builder als een set scripts voor het maken van nieuwe sitethema&#39;s.
