---
title: SBZ's voor AEM ontwikkelen
description: Dit artikel stelt belangrijke vragen om te overwegen wanneer het aanhalen van een front-end ontwikkelaar om een SPA voor AEM te ontwikkelen. Het geeft ook een overzicht van de architectuur van AEM betreffende SPAs in mening te houden wanneer het opstellen van een ontwikkelde SPA op AEM.
exl-id: f6c6f31a-69ad-48f6-b995-e6d0930074df
feature: Developing
role: Admin, Architect, Developer
index: false
source-git-commit: 7a9d947761b0473f5ddac3c4d19dfe5bed5b97fe
workflow-type: tm+mt
source-wordcount: '2028'
ht-degree: 0%

---


# SBZ&#39;s voor AEM ontwikkelen {#developing-spas-for-aem}

Toepassingen van één pagina (SPAs) kunnen dwingende ervaringen voor websitegebruikers aanbieden. De ontwikkelaars willen plaatsen kunnen bouwen gebruikend het kader van het KUUROORD en de auteurs willen de inhoud binnen AEM voor een plaats foutloos uitgeven die gebruikend dergelijke kaders wordt gebouwd.

Dit artikel stelt belangrijke vragen om te overwegen wanneer het in dienst nemen van een front-end ontwikkelaar om een SPA voor AEM te ontwikkelen en geeft een overzicht van de architectuur van AEM betreffende het opstellen van SPAs op AEM.

{{ue-over-spa}}

## SBO-ontwikkelingsbeginselen voor AEM {#spa-development-principles-for-aem}

Het ontwikkelen van enige paginatoepassingen op AEM veronderstelt dat de front-end ontwikkelaar standaardbeste praktijken wanneer het creëren van een SPA naleeft. Als als front-end ontwikkelaar u deze algemene beste praktijken en een paar AEM-specifieke principes volgt, is uw KUUROORD functioneel met [ AEM en zijn inhoud-auteursmogelijkheden ](introduction.md#content-editing-experience-with-spa).

* **[Portability](#portability)** - zoals met om het even welke componenten, zouden de componenten moeten worden gebouwd om zo draagbaar mogelijk te zijn. Het KUUROORD zou met draaglijk en herbruikbare componenten moeten worden gebouwd.
* **[AEM drijft de Structuur van de Plaats van de Plaats](#aem-drives-site-structure)** - de front-end ontwikkelaar leidt tot componenten en bezit hun interne structuur, maar baseert zich op AEM om de inhoudsstructuur van de plaats te bepalen.
* **[Dynamische Rendering](#dynamic-rendering)** - allen zou het teruggeven dynamisch moeten zijn.
* **[Dynamisch Verpletterend](#dynamic-routing)** - het KUUROORD is verantwoordelijk voor het verpletteren en AEM luistert aan het en haalt die op het wordt gebaseerd. Om het even welk verpletteren zou ook dynamisch moeten zijn.

Als u deze principes in mening houdt aangezien u uw SPA ontwikkelt, wordt het zo flexibel en zo toekomstig bewijs mogelijk terwijl het toelaten van alle gesteunde het auteursfunctionaliteit van AEM.

Als u AEM authoring eigenschappen niet moet steunen, overweeg een verschillend [ het ontwerpmodel van het KUUROORD ](#spa-design-models).

### Overdraagbaarheid {#portability}

Zoals bij het ontwikkelen van om het even welke component, zouden uw componenten op een zodanige manier moeten worden ontworpen dat hun draagbaarheid wordt gemaximaliseerd. Patronen die de draagbaarheid of herbruikbaarheid van de onderdelen in de weg staan, moeten worden vermeden om ervoor te zorgen dat de onderdelen compatibel, flexibel en duurzaam zijn.

Het resulterende KUUROORD zou met hoogst draagbare en herbruikbare componenten moeten worden gebouwd.

### AEM Drives Site Structure {#aem-drives-site-structure}

De front-end ontwikkelaar moet zich als verantwoordelijke voor het creëren van een bibliotheek van de componenten van het KUUROORD zien die worden gebruikt om app te bouwen. De front-end ontwikkelaar heeft volledige controle over de interne structuur van de componenten. [ Nochtans, bezit AEM altijd de structuur van de plaats ](editor-overview.md).

Deze controle betekent dat de front-end ontwikkelaar klanteninhoud vóór of na het ingangspunt van de componenten kan toevoegen en een derdevraag binnen de component kan ook maken. De front-end ontwikkelaar heeft echter geen volledige controle over hoe de componenten bijvoorbeeld nesten.

### Dynamische rendering {#dynamic-rendering}

Het SPA zou zich slechts op dynamische teruggeven van inhoud moeten baseren. Dit is de standaardinstelling waarbij AEM alle onderliggende items van de inhoudsstructuur ophaalt en rendert.

Elke expliciete rendering die naar specifieke inhoud verwijst, wordt beschouwd als statische rendering en wordt wel ondersteund, maar is compatibel met de ontwerpfuncties voor AEM-inhoud. Het gaat ook tegen het beginsel van [ portability ](#portability).

### Dynamische routering {#dynamic-routing}

Zoals met het teruggeven, zou al het verpletteren ook dynamisch moeten zijn. In AEM, [ zou het KUUROORD altijd het verpletteren ](routing.md) moeten bezitten en AEM luistert aan het en haalt inhoud die op het wordt gebaseerd.

Om het even welk statisch verpletterend werk tegen het [ beginsel van portability ](#portability) en beperkt de auteur door niet compatibel met inhoud te zijn creërend eigenschappen van AEM. Bijvoorbeeld, met het statische verpletteren, als de inhoudsauteur een route wil veranderen of een pagina veranderen, moeten zij de front-end ontwikkelaar vragen om het te doen.

## AEM Project Archetype {#aem-project-archetype}

Om het even welk project van AEM zou het [ Archetype van het Project van AEM ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) moeten gebruiken, dat de projecten van het KUUROORD gebruikend React of Angular steunt en het KUUROORD SDK gebruikt.

## SPA-ontwerpmodellen {#spa-design-models}

Als de [ principes van het ontwikkelen van SPAs in AEM ](#spa-development-principles-for-aem) worden gevolgd, dan is uw SPA functioneel met alle gesteunde inhoud van AEM auteurseigenschappen.

Er kunnen zich echter gevallen voordoen waarin deze functionaliteit niet volledig noodzakelijk is. In de volgende tabel vindt u een overzicht van de verschillende ontwerpmodellen, hun voordelen en hun nadelen.

<table>
 <tbody>
  <tr>
   <th><strong>Ontwerpmodel<br /> </strong></th>
   <th><strong>Voordelen</strong></th>
   <th><strong>Nadelen</strong></th>
  </tr>
  <tr>
   <td>AEM wordt gebruikt als headless CMS zonder het <a href="/help/implementing/developing/hybrid/reference-materials.md"> kader van SDK van de Redacteur van het KUUROORD te gebruiken.</a></td>
   <td>De front-end ontwikkelaar heeft volledige controle over de app.</td>
   <td><p>Inhoudsauteurs kunnen geen AEM-ervaring gebruiken voor het schrijven van inhoud.</p> <p>De code is niet draagbaar of herbruikbaar als het statische verwijzingen of het verpletteren bevat.</p> <p>Hiermee wordt het gebruik van de sjablooneditor niet toegestaan, zodat de ontwikkelaar aan de voorzijde bewerkbare sjablonen moet bijhouden via het JCR.</p> </td>
  </tr>
  <tr>
   <td>De front-end ontwikkelaar gebruikt het kader van SDK van de Redacteur van het KUUROORD maar opent slechts enkele gebieden aan de inhoudauteur.</td>
   <td>De ontwikkelaar behoudt de controle over de app door alleen authoring in beperkte delen van de app in te schakelen.</td>
   <td><p>Inhoudsauteurs zijn beperkt tot een beperkt aantal AEM-programma's voor het schrijven van inhoud.</p> <p>De code riskeert niet draagbaar of herbruikbaar als het statische verwijzingen of het verpletteren bevat.</p> <p>Hiermee wordt het gebruik van de sjablooneditor niet toegestaan, zodat de ontwikkelaar aan de voorzijde bewerkbare sjablonen moet bijhouden via het JCR.</p> </td>
  </tr>
  <tr>
   <td>Het project gebruikt volledig de Redacteur SDK van het KUUROORD en de frontend componenten worden ontwikkeld als bibliotheek en de inhoudsstructuur van app wordt gedelegeerd aan AEM.</td>
   <td><p>De app is herbruikbaar en draagbaar.</p> <p>De auteur van de inhoud kan de app bewerken met behulp van de AEM-ervaring voor het schrijven van inhoud.<br /> </p> <p>Het KUUROORD is compatibel met de malplaatjeredacteur.</p> </td>
   <td><p>De ontwikkelaar heeft geen controle over de structuur van de app en het gedeelte van de inhoud dat aan AEM is gedelegeerd.</p> <p>De ontwikkelaar kan gedeelten van de app nog steeds reserveren voor de inhoud die niet met AEM kan worden gemaakt.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Hoewel alle modellen in AEM worden gesteund, slechts door de derde uit te voeren (en na de geadviseerde [ de ontwikkelingsbeginselen van het KUUROORD ](#spa-development-principles-for-aem)) zijn de inhoudsauteurs in staat om met, en uit te geven, de inhoud van het KUUUROORD in AEM in wisselwerking te staan.

## Bestaande SPA&#39;s migreren naar AEM {#migrating-existing-spas-to-aem}

Algemeen als uw KUUROORD de [ Beginselen van de Ontwikkeling van het KUUROORD voor AEM ](#spa-development-principles-for-aem) volgt, dan uw werken van het KUUROORD in AEM en editable gebruikend de Redacteur van AEM SPA.

Volg deze stappen zodat kunt u uw bestaande SPA klaar krijgen om met AEM te werken.

1. **maak uw componenten JS modulair.** - Zorg ervoor dat ze kunnen worden gerenderd in elke volgorde, positie en grootte.
1. **gebruik de containers die door SDK worden verstrekt om uw componenten op het scherm te plaatsen.** - AEM biedt een pagina- en alineasysteem voor gebruik.
1. **creeer een component van AEM voor elke component JS.** - De AEM-componenten definiëren het dialoogvenster en de JSON-uitvoer.

## Instructies voor front-end ontwikkelaars {#instructions-for-front-end-developers}

De belangrijkste taak bij het in dienst nemen van een front-end ontwikkelaar om een SPA voor AEM tot stand te brengen is het akkoord te gaan over de componenten en hun modellen JSON.

Hieronder volgt een overzicht van de stappen die een front-end ontwikkelaar moet volgen bij het ontwikkelen van een SPA voor AEM.

1. **ga op componenten en hun JSON model** akkoord

   Voor-eind ontwikkelaars en de achterste-eind AEM ontwikkelaars moeten het eens zijn over welke componenten noodzakelijk en een model zodat is er een één-op-één gelijke van de componenten van het KUUROORD aan de achterste-eindcomponenten.

   AEM-componenten zijn nog steeds vooral nodig om bewerkingsdialoogvensters te bieden en het componentmodel te exporteren.

1. **In React componenten, toegang het model via`this.props.cqModel`**

   Zodra de componenten worden overeengekomen en het model JSON op zijn plaats is, is de front-end ontwikkelaar vrij om het KUUROORD te ontwikkelen en kan eenvoudig tot het model JSON via `this.props.cqModel` toegang hebben.

1. `render()` methode van de component van 0} uitvoeren ****

   De front-end ontwikkelaar implementeert de `render()` -methode naar eigen inzicht en kan de velden van de `cqModel` -eigenschap gebruiken. Deze methode geeft het DOM en de HTML-fragmenten uit die op de pagina worden ingevoegd. Deze methode is ook de standaardmanier om een app te maken in React.

1. **Kaart de component aan het middeltype van AEM via`MapTo()`**

   In de toewijzing worden componentklassen opgeslagen en intern door de opgegeven `Container` -component gebruikt om componenten op basis van het opgegeven brontype op te halen en dynamisch te instantiëren.

   Deze kaart fungeert als de &quot;lijm&quot; tussen front-end en back-end, zodat de editor weet aan welke componenten de reactiecomponenten overeenkomen.

   De `Page` en `ResponsiveGrid` zijn goede voorbeelden van klassen die de basis uitbreiden `Container` .

1. **Bepaal de component `EditConfig` als parameter aan`MapTo()`**

   Deze parameter is noodzakelijk om de redacteur te vertellen hoe de component zou moeten worden genoemd zolang bij nog niet wordt teruggegeven of geen inhoud heeft om terug te geven.

1. **breid de verstrekte `Container` klasse voor pagina&#39;s en containers** uit

   Pagina- en alineasystemen moeten deze klasse uitbreiden, zodat delegatie naar binnencomponenten naar behoren werkt.

1. **voer een verpletterende oplossing uit die HTML5 `History` API gebruikt.**

   Wanneer de functie `ModelRouter` is ingeschakeld, wordt door het aanroepen van de functies `pushState` en `replaceState` een verzoek aan de `PageModelManager` verzonden om een ontbrekend fragment van het model op te halen.

   De huidige versie van `ModelRouter` ondersteunt alleen het gebruik van URL&#39;s die verwijzen naar het feitelijke bronnenpad van verzendmodel-entry-punten. Het ondersteunt het gebruik van vanity-URL&#39;s of aliassen niet.

   `ModelRouter` kan worden onbruikbaar gemaakt of worden gevormd om een lijst van regelmatige uitdrukkingen te negeren.

## AEM-Agnostic {#aem-agnostic}

Deze codeblokken laten zien hoe uw React- en Angular-componenten niets nodig hebben dat specifiek is voor Adobe of AEM.

* Alles wat zich binnen de JavaScript-component bevindt, is AEM-agnostisch.
* Wat echter specifiek voor AEM is, is dat de JS-component moet worden toegewezen aan een AEM-component met de MapTo-hulpfunctie.

![ de Agnostische benadering van AEM ](assets/aem-agnostic.png)

De `MapTo` helper is de &quot;lijm&quot;die de achterkant en de voorste componenten om samen toelaat worden aangepast:

* Het vertelt de container JS (of JS paragraafsysteem) welke component JS voor het teruggeven van elk van de componenten verantwoordelijk is die in JSON aanwezig zijn.
* Het voegt een de gegevensattribuut van HTML aan HTML toe die de component JS teruggeeft, zodat de redacteur van het KUUROORD weet welke dialoog aan de auteur wanneer het uitgeven van de component te tonen.

Zie de gids Aan de slag voor uw gekozen framework voor meer informatie over het gebruik van `MapTo` en het bouwen van SPA&#39;s voor AEM in het algemeen.

* [Begonnen het worden met SPAs in AEM Gebruikend Reageren](getting-started-react.md)
* [Aan de slag met SPA&#39;s in AEM met Angular](getting-started-angular.md)

## AEM Architecture en SPA&#39;s {#aem-architecture-and-spas}

De algemene architectuur van AEM met inbegrip van ontwikkeling, creatie, en het publiceren milieu&#39;s verandert niet wanneer het gebruiken van SPAs. Nochtans is het nuttig om te begrijpen hoe de ontwikkeling van het KUUROORD in deze architectuur past.

![ architectuur van AEM en SPAs ](assets/aem-architecture.png)

* **bouwt Milieu**

  Dit milieu is waar de bron voor de toepassing van het KUUROORD en componentenbron wordt uitgecheckt.

   * De NPM clientlib generator leidt tot een cliëntbibliotheek van het project van het KUUROORD.
   * Deze bibliotheek is afkomstig van Maven en wordt samen met de component geïmplementeerd door de Maven Build-plug-in voor de AEM-auteur.

* **AEM Auteur**

  De inhoud wordt gecreeerd op de auteur van AEM, met inbegrip van authoring SPAs.

  Wanneer een KUUROORD gebruikend de Redacteur van het KUUROORD op het auteursmilieu wordt uitgegeven:

   1. De SPA vraagt de buitenste HTML.
   1. De CSS is geladen.
   1. De JavaScript van de toepassing SPA wordt geladen.
   1. Wanneer de SPA-toepassing wordt uitgevoerd, wordt de JSON-toepassing opgevraagd, zodat de app de DOM van de pagina kan maken, inclusief de `cq-data` -kenmerken.
   1. Met de `cq-data` -kenmerken kan de editor aanvullende pagina-informatie laden, zodat deze weet welke bewerkingsconfiguraties beschikbaar zijn voor de componenten.

* **AEM publiceert**

  Waar de authored inhoud en de gecompileerde bibliotheken met inbegrip van de toepassingsartefacten van het KUUROORD, cliëntbibliotheken, en componenten voor openbare consumptie worden gepubliceerd.

* **Dispatcher / CDN**

  De Dispatcher fungeert als cachelaag van AEM voor bezoekers van de site.
   * Verzoeken worden op dezelfde manier verwerkt als aanvragen voor AEM-auteur. Er is echter geen verzoek om de pagina-informatie, omdat deze alleen nodig is voor de editor.
   * JavaScript, CSS, JSON en HTML worden in cache geplaatst, waardoor de pagina wordt geoptimaliseerd voor snelle levering.

>[!NOTE]
>
>Binnen AEM is het niet nodig JavaScript-constructiemechanismen uit te voeren of de JavaScript zelf uit te voeren. AEM slechts gastheren de gecompileerde artefacten van de toepassing van het KUUROORD.

## Volgende stappen {#next-steps}

* [ Begonnen het Worden met SPAs in AEM die Reageren ](getting-started-react.md) gebruikt toont hoe een basisKUUROORD wordt gebouwd om met de Redacteur van het KUUROORD in AEM te werken gebruikend Reageren.
* [ Begonnen het Worden met SPAs in AEM die Angular gebruiken ](getting-started-angular.md) toont hoe een basisKUUROORD wordt gebouwd om met de Redacteur van het KUUROORD in AEM te werken gebruikend Angular.
* [ het Overzicht van de Redacteur van het KUUROORD ](editor-overview.md) gaat in meer diepte in het communicatie model tussen AEM en het KUUROORD.
* [ WKND Project van het KUUROORD ](wknd-tutorial.md) is een geleidelijke leerprogramma die een eenvoudig project van het KUUROORD in AEM uitvoeren.
* [ Dynamisch Model aan de Afbeelding van de Component voor SPAs ](model-to-component-mapping.md) verklaart het dynamische model aan componentenafbeelding en hoe het binnen SPAs in AEM werkt.
* [ het Vervagen van het KUUROORD ](blueprint.md) biedt een diepe duik in hoe het KUUROORD SDK voor AEM werkt voor het geval u SPAs in AEM voor een kader buiten React of Angular wilt uitvoeren. Of je zou gewoon graag een dieper begrip willen.
