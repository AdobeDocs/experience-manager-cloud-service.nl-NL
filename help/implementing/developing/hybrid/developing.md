---
title: SPA ontwikkelen voor AEM
description: Dit artikel stelt belangrijke vragen om te overwegen wanneer het in dienst nemen van een front-end ontwikkelaar om een SPA voor AEM te ontwikkelen. Het geeft ook een overzicht van de architectuur van AEM betreffende SPA om in mening te houden wanneer het opstellen van een ontwikkelde SPA op AEM.
exl-id: f6c6f31a-69ad-48f6-b995-e6d0930074df
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '2028'
ht-degree: 0%

---

# SPA ontwikkelen voor AEM {#developing-spas-for-aem}

Toepassingen op één pagina (SPA) kunnen aantrekkelijke ervaringen bieden voor websitegebruikers. Ontwikkelaars willen sites kunnen maken met behulp van SPA frameworks en auteurs willen inhoud naadloos bewerken binnen AEM voor een site die is gebouwd met behulp van dergelijke frameworks.

Dit artikel stelt belangrijke vragen om te overwegen wanneer het in dienst nemen van een front-end ontwikkelaar om een SPA voor AEM te ontwikkelen en geeft een overzicht van de architectuur van AEM betreffende het opstellen van SPA op AEM.

## SPA ontwikkelingsbeginselen voor AEM {#spa-development-principles-for-aem}

Bij het ontwikkelen van toepassingen voor één pagina op AEM wordt ervan uitgegaan dat de ontwikkelaar aan de voorzijde de aanbevolen standaardprocedures voor het maken van een SPA in acht neemt. Als als front-end ontwikkelaar u deze algemene beste praktijken en een paar AEM-specifieke principes volgt, is uw SPA functioneel met [ AEM en zijn inhoud-creatie mogelijkheden ](introduction.md#content-editing-experience-with-spa).

* **[Portability](#portability)** - zoals met om het even welke componenten, zouden de componenten moeten worden gebouwd om zo draagbaar mogelijk te zijn. De SPA moet met draagbare en herbruikbare onderdelen worden gebouwd.
* **[AEM de Structuur van de Plaats van de Stations](#aem-drives-site-structure)** - de front-end ontwikkelaar leidt tot componenten en bezit hun interne structuur, maar baseert zich op AEM om de inhoudsstructuur van de plaats te bepalen.
* **[Dynamische Rendering](#dynamic-rendering)** - allen zou het teruggeven dynamisch moeten zijn.
* **[Dynamisch Verpletteren](#dynamic-routing)** - de SPA is verantwoordelijk voor het verpletteren en AEM luistert aan het en haalt die op het worden gebaseerd. Om het even welk verpletteren zou ook dynamisch moeten zijn.

Als u deze principes in gedachten houdt bij het ontwikkelen van uw SPA, wordt deze zo flexibel en zo toekomstbestendig mogelijk, terwijl alle ondersteunde AEM ontwerpfunctionaliteit wordt ingeschakeld.

Als u niet AEM auteurseigenschappen moet steunen, overweeg een verschillend [ SPA ontwerpmodel ](#spa-design-models).

### Overdraagbaarheid {#portability}

Zoals bij het ontwikkelen van om het even welke component, zouden uw componenten op een zodanige manier moeten worden ontworpen dat hun draagbaarheid wordt gemaximaliseerd. Patronen die de draagbaarheid of herbruikbaarheid van de onderdelen in de weg staan, moeten worden vermeden om ervoor te zorgen dat de onderdelen compatibel, flexibel en duurzaam zijn.

De resulterende SPA moet worden gebouwd met zeer draagbare en herbruikbare onderdelen.

### Sitestructuur AEM stations {#aem-drives-site-structure}

De front-end ontwikkelaar moet zichzelf zien als verantwoordelijk voor het maken van een bibliotheek met SPA componenten die worden gebruikt om de app te maken. De front-end ontwikkelaar heeft volledige controle over de interne structuur van de componenten. [ Nochtans, bezit AEM altijd de structuur van de plaats ](editor-overview.md).

Deze controle betekent dat de front-end ontwikkelaar klanteninhoud vóór of na het ingangspunt van de componenten kan toevoegen en een derdevraag binnen de component kan ook maken. De front-end ontwikkelaar heeft echter geen volledige controle over hoe de componenten bijvoorbeeld nesten.

### Dynamische rendering {#dynamic-rendering}

De SPA mag alleen vertrouwen op dynamische rendering van inhoud. Deze verwachting is het gebrek waar AEM alle kinderen van de inhoudsstructuur terugkrijgt en teruggeeft.

Elke expliciete rendering die naar specifieke inhoud verwijst, wordt beschouwd als statische rendering en wordt wel ondersteund, maar is compatibel met AEM ontwerpfuncties voor inhoud. Het gaat ook tegen het beginsel van [ portability ](#portability).

### Dynamische routering {#dynamic-routing}

Zoals met het teruggeven, zou al het verpletteren ook dynamisch moeten zijn. In AEM, [ zou de SPA altijd het verpletteren ](routing.md) moeten bezitten en AEM luistert aan het en haalt inhoud die op het wordt gebaseerd.

Om het even welk statisch verpletterend werk tegen het [ beginsel van portability ](#portability) en beperkt de auteur door niet compatibel met inhoud te zijn creërend eigenschappen van AEM. Bijvoorbeeld, met het statische verpletteren, als de inhoudsauteur een route wil veranderen of een pagina veranderen, moeten zij de front-end ontwikkelaar vragen om het te doen.

## Projectarchetype AEM {#aem-project-archetype}

Om het even welk AEM project zou [ AEM Archetype van het Project ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) moeten gebruiken, dat SPA projecten gebruikend React of Angular steunt en SPA SDK gebruikt.

## SPA ontwerpmodellen {#spa-design-models}

Als de [ principes van het ontwikkelen van SPA in AEM ](#spa-development-principles-for-aem) worden gevolgd, dan is uw SPA functioneel met alle gesteunde AEM tevreden auteurseigenschappen.

Er kunnen zich echter gevallen voordoen waarin deze functionaliteit niet volledig noodzakelijk is. In de volgende tabel vindt u een overzicht van de verschillende ontwerpmodellen, hun voordelen en hun nadelen.

<table>
 <tbody>
  <tr>
   <th><strong>Ontwerpmodel<br /> </strong></th>
   <th><strong>Voordelen</strong></th>
   <th><strong>Nadelen</strong></th>
  </tr>
  <tr>
   <td>AEM wordt gebruikt als hoofdCMS zonder het <a href="/help/implementing/developing/hybrid/reference-materials.md"> kader van SDK van SPA Redacteur te gebruiken.</a></td>
   <td>De front-end ontwikkelaar heeft volledige controle over de app.</td>
   <td><p>Inhoudsauteurs kunnen geen AEM gebruiken voor het schrijven van inhoud.</p> <p>De code is niet draagbaar of herbruikbaar als het statische verwijzingen of het verpletteren bevat.</p> <p>Hiermee wordt het gebruik van de sjablooneditor niet toegestaan, zodat de ontwikkelaar aan de voorzijde bewerkbare sjablonen moet bijhouden via het JCR.</p> </td>
  </tr>
  <tr>
   <td>De front-end ontwikkelaar gebruikt het SPA Editor SDK-framework, maar opent slechts enkele gebieden voor de auteur van de inhoud.</td>
   <td>De ontwikkelaar behoudt de controle over de app door alleen authoring in beperkte delen van de app in te schakelen.</td>
   <td><p>Inhoudsauteurs hebben slechts een beperkte AEM ervaring bij het schrijven van inhoud.</p> <p>De code riskeert niet draagbaar of herbruikbaar als het statische verwijzingen of het verpletteren bevat.</p> <p>Hiermee wordt het gebruik van de sjablooneditor niet toegestaan, zodat de ontwikkelaar aan de voorzijde bewerkbare sjablonen moet bijhouden via het JCR.</p> </td>
  </tr>
  <tr>
   <td>Het project gebruikt volledig de SPA Editor SDK en de frontend componenten worden ontwikkeld als bibliotheek en de inhoudsstructuur van de app wordt gedelegeerd aan AEM.</td>
   <td><p>De app is herbruikbaar en draagbaar.</p> <p>De auteur van de inhoud kan de app bewerken via AEM ontwerpervaring voor inhoud.<br /> </p> <p>De SPA is compatibel met de sjablooneditor.</p> </td>
   <td><p>De ontwikkelaar heeft geen controle over de structuur van de app en het gedeelte van de inhoud dat aan AEM is gedelegeerd.</p> <p>De ontwikkelaar kan gedeelten van de app nog steeds reserveren voor de inhoud die niet is bedoeld om te worden gemaakt met AEM.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Hoewel alle modellen in AEM worden gesteund, slechts door de derde (en na de geadviseerde [ SPA ontwikkelingsbeginselen ](#spa-development-principles-for-aem)) uit te voeren zijn de inhoudsauteurs in staat om met, en uit te geven, de inhoud van de SPA in AEM in wisselwerking te staan.

## Bestaande SPA migreren naar AEM {#migrating-existing-spas-to-aem}

Over het algemeen als uw SPA de [ SPA Beginselen van de Ontwikkeling voor AEM ](#spa-development-principles-for-aem) volgt, dan werkt uw SPA in AEM en is editable gebruikend de AEM Redacteur SPA.

Voer de volgende stappen uit zodat u uw bestaande SPA klaar hebt om met AEM te werken.

1. **maak uw componenten JS modulair.** - Zorg ervoor dat ze kunnen worden gerenderd in elke volgorde, positie en grootte.
1. **gebruik de containers die door SDK worden verstrekt om uw componenten op het scherm te plaatsen.** - AEM biedt een pagina- en alineasysteem voor gebruik.
1. **creeer een AEM component voor elke component JS.** - De AEM componenten definiëren het dialoogvenster en de JSON-uitvoer.

## Instructies voor front-end ontwikkelaars {#instructions-for-front-end-developers}

De belangrijkste taak bij het in dienst nemen van een front-end ontwikkelaar om een SPA voor AEM tot stand te brengen is akkoord te gaan over de componenten en hun modellen JSON.

Hieronder volgt een overzicht van de stappen die een front-end ontwikkelaar moet volgen bij het ontwikkelen van een SPA voor AEM.

1. **ga op componenten en hun JSON model** akkoord

   Front-end ontwikkelaars en achterste-AEM ontwikkelaars moeten het eens zijn over welke componenten noodzakelijk en een model zodat is er één-op-één gelijke van SPA componenten aan de achterste-eindcomponenten.

   AEM componenten zijn nog steeds nodig, vooral om te zorgen voor bewerkingsdialoogvensters en om het componentmodel te exporteren.

1. **In React componenten, toegang het model via`this.props.cqModel`**

   Zodra componenten zijn overeengekomen en het JSON-model is geïmplementeerd, kan de front-end ontwikkelaar de SPA vrij ontwikkelen en eenvoudig toegang krijgen tot het JSON-model via `this.props.cqModel` .

1. `render()` methode van de component van 0} uitvoeren ****

   De front-end ontwikkelaar implementeert de `render()` -methode naar eigen inzicht en kan de velden van de `cqModel` -eigenschap gebruiken. Deze methode geeft het DOM en de HTML-fragmenten uit die in de pagina worden ingevoegd. Deze methode is ook de standaardmanier om een app te maken in React.

1. **Kaart de component aan het AEM middeltype via`MapTo()`**

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

## AEM-agnost {#aem-agnostic}

Deze codeblokken illustreren hoe uw React- en Angular-componenten niets nodig hebben dat specifiek is voor Adobe of AEM.

* Alles wat zich in de JavaScript-component bevindt, is AEM-agnostisch.
* Wat echter specifiek aan AEM is, is dat de component JS aan een AEM component met de hulp moet worden in kaart gebracht MapTo.

![ AEM Akoestische benadering ](assets/aem-agnostic.png)

De `MapTo` helper is de &quot;lijm&quot;die de achterkant en de voorste componenten om samen toelaat worden aangepast:

* Het vertelt de container JS (of JS paragraafsysteem) welke component JS voor het teruggeven van elk van de componenten verantwoordelijk is die in JSON aanwezig zijn.
* Er wordt een HTML-gegevenskenmerk toegevoegd aan de HTML die de JS-component rendert, zodat de SPA Editor weet welk dialoogvenster aan de auteur moet worden weergegeven wanneer de component wordt bewerkt.

Zie de handleiding Aan de slag voor het door u gekozen framework voor meer informatie over het gebruik van `MapTo` en het samenstellen van SPA voor AEM in het algemeen.

* [Aan de slag met SPA in AEM Reageren gebruiken](getting-started-react.md)
* [Aan de slag met SPA in AEM Angular gebruiken](getting-started-angular.md)

## AEM Architectuur en SPA {#aem-architecture-and-spas}

De algemene architectuur van AEM, inclusief ontwikkelings-, auteurs- en publicatieomgevingen, verandert niet wanneer u SPA gebruikt. Het is echter nuttig te begrijpen hoe SPA ontwikkeling in deze architectuur past.

![AEM architectuur en SPA ](assets/aem-architecture.png)

* **bouwt Milieu**

  In deze omgeving is de bron van de SPA toepassing en de componentbron uitgecheckt.

   * De NPM clientlib generator leidt tot een cliëntbibliotheek van het SPA project.
   * Deze bibliotheek is afkomstig van Maven en wordt samen met de component geïmplementeerd door de plug-in Maven Build bij de AEM Auteur.

* **AEM Auteur**

  Inhoud wordt gemaakt op de AEM auteur, inclusief SPA.

  Wanneer een SPA wordt bewerkt met de SPA Editor in de ontwerpomgeving:

   1. De SPA vraagt om de buitenste HTML.
   1. De CSS is geladen.
   1. De JavaScript van de SPA toepassing wordt geladen.
   1. Wanneer de SPA toepassing wordt uitgevoerd, wordt de JSON opgevraagd, zodat de app het DOM van de pagina kan maken met de kenmerken `cq-data` .
   1. Met de `cq-data` -kenmerken kan de editor aanvullende pagina-informatie laden, zodat deze weet welke bewerkingsconfiguraties beschikbaar zijn voor de componenten.

* **AEM Publish**

  Waar de geschreven inhoud en de gecompileerde bibliotheken, inclusief SPA toepassingsartefacten, cliëntbibliotheken, en componenten voor openbare consumptie worden gepubliceerd.

* **Dispatcher / CDN**

  De Dispatcher fungeert als de cachelaag van AEM voor bezoekers van de site.
   * Verzoeken worden op dezelfde manier verwerkt als AEM auteur. Er is echter geen verzoek om de pagina-informatie, omdat deze alleen nodig is voor de editor.
   * JavaScript, CSS, JSON en HTML worden in cache geplaatst, waardoor de pagina wordt geoptimaliseerd voor snelle levering.

>[!NOTE]
>
>Binnen AEM is het niet nodig JavaScript-constructiemechanismen uit te voeren of de JavaScript zelf uit te voeren. AEM alleen de gecompileerde artefacten van de SPA toepassing.

## Volgende stappen {#next-steps}

* [ Begonnen het Worden met SPA in AEM gebruiken Reageert ](getting-started-react.md) toont hoe een basisSPA wordt gebouwd om met de SPA Redacteur in AEM te werken gebruikend Reageren.
* [ Begonnen het Worden met SPA in AEM gebruikend Angular ](getting-started-angular.md) toont hoe een basis SPA wordt gebouwd om met de SPA Redacteur in AEM te werken gebruikend Angular.
* [ SPA het Overzicht van de Redacteur ](editor-overview.md) gaat in meer diepte in het communicatie model tussen AEM en de SPA.
* [ WKND SPA Project ](wknd-tutorial.md) is een geleidelijke leerprogramma die een eenvoudig SPA project in AEM uitvoeren.
* [ Dynamisch Model aan de Toewijzing van de Component voor SPA ](model-to-component-mapping.md) verklaart het dynamische model aan componentenafbeelding en hoe het binnen SPA in AEM werkt.
* [ SPA Vervagen ](blueprint.md) biedt een diepe duik in hoe SPA SDK voor AEM werkt voor het geval u SPA in AEM voor een kader buiten Reageren of Angular wilt uitvoeren. Of je zou gewoon graag een dieper begrip willen.
