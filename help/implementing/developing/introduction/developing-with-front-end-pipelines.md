---
title: Sites ontwikkelen met de voorste pijplijn
description: De front-end pijpleiding verbetert de onafhankelijkheid van de ontwikkelaar en versnelt het ontwikkelingsproces. In dit artikel worden de belangrijkste overwegingen voor het 'front-end' constructieproces beschreven om optimale prestaties en efficiëntie te garanderen.
exl-id: 996fb39d-1bb1-4dda-a418-77cdf8b307c5
feature: Developing
role: Admin, Architect, Developer
recommendations: display, noCatalog
source-git-commit: 0a458616afad836efae27e67dbe145fc44bee968
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 0%

---


# Sites ontwikkelen met de front-end pijplijn {#developing-site-with-front-end-pipeline}

{{traditional-aem}}

De [&#x200B; front-end pijpleiding &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) geeft front-end ontwikkelaars grotere onafhankelijkheid en versnelt beduidend ontwikkeling. In dit artikel wordt uitgelegd hoe het proces werkt en worden belangrijke overwegingen gemarkeerd om u te helpen er optimaal van te profiteren.

>[!TIP]
>
>Als u nog niet vertrouwd met bent hoe te om de front-end pijpleiding en zijn voordelen te gebruiken, zie de [&#x200B; gids van de Reis van de Aanmaak van de Snel van de Plaats &#x200B;](/help/journey-sites/quick-site/overview.md). Het verstrekt een voorbeeld van hoe te om een nieuwe plaats snel op te stellen en zijn thema onafhankelijk van achterste-eindontwikkeling aan te passen.

## Begrijp de front-end pijpleiding opstelling en bouwstijlproces in AEM Cloud Manager {#front-end-build-contract}

Gelijkaardig aan [&#x200B; volledig-stapel bouwt milieu &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md), heeft de front-end pijpleiding zijn eigen milieu. Ontwikkelaars hebben enige flexibiliteit met deze pijpleiding, op voorwaarde dat ze het front-end bouwcontract volgen.

De front-end pijpleiding vereist het front-end `Node.js` project om de `build` manuscriptrichtlijn te gebruiken om de bouwstijl te produceren die het opstelt. Deze vereiste bestaat omdat Cloud Manager het bevel `npm run build` gebruikt om het plaatsbare project voor front-end bouwt te produceren.

De resulterende inhoud van de `dist` -map is wat Cloud Manager uiteindelijk implementeert en deze als statische bestanden aanbiedt. Deze bestanden worden extern gehost op AEM, maar worden via een `/content/...` URL beschikbaar gesteld in de geïmplementeerde omgeving.

## Ondersteunde Node.js-versies {#node-versions}

De front-end build-omgeving ondersteunt de volgende `Node.js` versies:

* 23
* 22
* 20
* 18
* 16
* 14 (standaard)
* 12

U kunt de `NODE_VERSION` [&#x200B; milieuvariabele &#x200B;](/help/implementing/cloud-manager/environment-variables.md) gebruiken om de gewenste versie te plaatsen.

## Aanbevolen procedures voor de naamgeving en het beheer van pijpleidingen aan de voorzijde in AEM {#single-source-of-truth}

Een goede praktijk voor AEM-implementaties is het handhaven van één duidelijke bron van waarheid. Cloud Manager is bedoeld om dit beginsel te versterken. Nochtans, omdat de front-end pijpleiding delen van de code om toelaat worden losgemaakt, is de juiste opstelling essentieel. Om conflicten te vermijden, zorg ervoor dat de veelvoudige front-end pijpleidingen niet aan de zelfde plaats binnen het zelfde milieu opstellen.

Daarom, en met name wanneer er meerdere pijpleidingen aan de voorzijde worden aangelegd, raadt Adobe u aan een conventie voor systematische naamgeving te handhaven. U kunt de volgende aanbevelingen gebruiken:

* De naam van de front-end module, die wordt gedefinieerd door de eigenschap `name` van het `package.json` -bestand, moet de naam bevatten van de site waarop deze van toepassing is. Voor een site in `/content/wknd` zou de naam van de front-end module bijvoorbeeld ongeveer gelijk zijn aan `wknd-theme` .
* Als een front-end module dezelfde Git-opslagplaats deelt met andere modules, moet de naam van de bijbehorende map gelijk zijn aan of dezelfde naam van de front-end module bevatten. Als de front-end module bijvoorbeeld de naam `wknd-theme` heeft, zou de omsluitende mapnaam ongeveer `wknd-theme-sources` zijn.
* De naam van de Cloud Manager front-end pijpleiding zou ook de naam van de front-end module moeten bevatten en ook het milieu toevoegen waarop het (productie of ontwikkeling) opstelt. Voor de front-end module met de naam `wknd-theme` zou de pijpleiding bijvoorbeeld een naam kunnen krijgen zoals `wknd-theme-prod` .

Een dergelijke conventie voorkomt de volgende implementatiefouten:

* Een front-end module toepassen op de verkeerde site.
* Het creëren van veelvoudige front-end modules die de zelfde plaats toepassen, die elkaar zouden beschrijven.
* Het creëren van veelvoudige front-end pijpleidingen voor de zelfde bronnen, die rasvoorwaarden kunnen veroorzaken, die de orde van plaatsingen niet verzekeren.

## Coördinatie van front-end en back-end ontwikkeling voor stabiliteit in AEM {#separation-of-concerns}

Een belangrijke beste praktijk voor om het even welke scheiding van zorgen is het contract zorgvuldig te ontwerpen en te beheren dat de grenzen tussen hen bepaalt. In de front-end pijpleiding, is dit contract de HTML en JSON output die door de plaats wordt teruggegeven. Het handhaven van de stabiliteit van deze output zorgt ervoor dat de front-end pijpleiding maximumwaarde levert, toestaand het front-end team om onafhankelijk te werken.

Er is momenteel geen ingebouwde capaciteit om de full-stack pijpleiding synchroon met de front-end pijpleidingen in werking te stellen. Daarom wanneer het scheiden van front-end ontwikkeling van de full-stack pijpleiding, is het essentieel om het contract zorgvuldig te beheren dat hun grenzen bepaalt. Dit contract bestaat gewoonlijk uit de HTML of JSON, of beide, die door Experience Manager worden gegeven. Elke wijziging van dit contract moet zorgvuldig worden gecoördineerd tussen teams die verschillende pijpleidingen beheren om een soepele overgang en een juiste volgorde van updates te garanderen.

De volgende stappen worden over het algemeen aanbevolen wanneer u wijzigingen aanbrengt in de HTML- of JSON-uitvoer, vooral als beide gebieden worden beïnvloed.

1. Het back-end team stelt eerst een ontwikkelomgeving in met de nieuwe HTML- of JSON-uitvoer.
   1. Als full-stack pijpleiding, voeren zij de code op die wordt vereist om de nieuwe HTML of JSON output, of allebei terug te geven, die gewenst is.
   1. Als dat aan een milieu is dat het front-end team niet eerder toegang tot had, dan moeten de volgende stappen worden uitgevoerd.
      1. URL: Het front-end team moet URL van die ontwikkelomgeving kennen.
      1. ACL: Het front-end team moet een lokale gebruiker van AEM met iets gelijkend op &quot;Medewerkers&quot;rechten worden gegeven.
      1. Git: Het front-end team moet een afzonderlijke plaats van het Git voor de front-end module hebben die specifiek die ontwikkelomgeving richt.

         Vaak wordt een `dev` -vertakking gemaakt voor het beheer van wijzigingen die in de ontwikkelomgeving zijn aangebracht. Deze praktijk staat voor een gemakkelijkere samenvoeging terug in de `main` tak toe, die voor plaatsing aan het productiemilieu wordt gebruikt.

      1. Pijpleiding: Het front-end team moet een front-end pijpleiding hebben die aan de ontwikkelomgeving opstelt. Die pijpleiding zou de front-end module opstellen die typisch in de `dev` tak, zoals die in het vorige punt wordt beschreven wordt gevestigd.
1. Het front-end team maakt dan CSS en JS code werk met zowel oude als nieuwe output.
   1. Ga als volgt te werk om zich op uw lokale computer te ontwikkelen:
      1. Met de opdracht `npx aem-site-theme-builder proxy` wordt een proxyserver gestart die inhoud uit een AEM-omgeving ophaalt. De CSS- en JS-bestanden van de front-end module worden vervangen door de bestanden uit de lokale `dist` -map.
      1. Wanneer u de variabele `AEM_URL` in het verborgen `.env` -bestand configureert, kunt u bepalen vanuit welke AEM-omgeving de lokale proxyserver de inhoud gebruikt.
      1. Als u de waarde van `AEM_URL` wijzigt, kunt u daarom schakelen tussen de productie- en ontwikkelomgevingen om de CSS en JS aan te passen aan beide omgevingen.
      1. Het moet met de ontwikkelomgeving werken die de nieuwe output teruggeeft en met het productiemilieu dat de oude output teruggeeft.
   1. Het front-end werk wordt voltooid wanneer de bijgewerkte front-end module voor beide milieu&#39;s werkt, en aan allebei wordt opgesteld.
1. Het back-end team kan de productieomgeving dan bijwerken door de code in te voeren die de nieuwe HTML- of JSON-uitvoer, of beide, via de full-stack-pijplijn rendert.
1. Het front-end team kan hun CSS en JS opschonen, elementen verwijderen nodig slechts voor de oude output, en de definitieve update aan productie opstellen gebruikend de front-end pijpleiding.

## Aanvullende bronnen {#additional-resources}

* Leer hoe u met AEM-sitethema&#39;s de stijl en het ontwerp van uw site kunt aanpassen.

  Zie [&#x200B; Thema&#39;s van de Plaats &#x200B;](/help/sites-cloud/administering/site-creation/site-themes.md).

* Adobe biedt een AEM Site Theme Builder als een set scripts voor het maken van nieuwe sitethema&#39;s.

  Zie [&#x200B; de Bouwer van het Thema van de Plaats van AEM &#x200B;](https://github.com/adobe/aem-site-theme-builder)



