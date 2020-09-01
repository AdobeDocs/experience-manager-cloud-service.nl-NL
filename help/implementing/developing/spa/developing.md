---
title: Het ontwikkelen van SPAs voor AEM
description: Dit artikel stelt belangrijke vragen in overweging wanneer het in dienst nemen van een front-end ontwikkelaar om een KUUROORD voor AEM te ontwikkelen evenals geeft een overzicht van de architectuur van AEM met betrekking tot SPAs om in mening te houden wanneer het opstellen van een ontwikkelde KUUROORD op AEM.
translation-type: tm+mt
source-git-commit: 0799a817095558edd49b53ddc915c9474181fef7
workflow-type: tm+mt
source-wordcount: '2078'
ht-degree: 0%

---


# Het ontwikkelen van SPAs voor AEM {#developing-spas-for-aem}

Toepassingen van één pagina (SPAs) kunnen dwingende ervaringen voor websitegebruikers aanbieden. De ontwikkelaars willen plaatsen kunnen bouwen gebruikend het kader van het KUUROORD en de auteurs willen inhoud binnen AEM voor een plaats foutloos uitgeven die gebruikend dergelijke kaders wordt gebouwd.

Dit artikel stelt belangrijke vragen om te overwegen wanneer het in dienst nemen van een front-end ontwikkelaar om een SPA voor AEM te ontwikkelen en geeft een overzicht van de architectuur van AEM met betrekking tot het opstellen van SPAs op AEM.

## SBO-ontwikkelingsbeginselen voor AEM {#spa-development-principles-for-aem}

Het ontwikkelen van enige paginatoepassingen op AEM veronderstelt dat de front-end ontwikkelaar standaardbeste praktijken wanneer het creëren van een KUUROORD waarneemt. Als als front-end ontwikkelaar u deze algemene beste praktijken evenals weinig AEM-specifieke principes volgt, zal uw SPA functioneel met [AEM en zijn inhoud-creatie mogelijkheden](introduction.md#content-editing-experience-with-spa)zijn.

* **[Draagbaarheid](#portability)** - De onderdelen moeten net als alle andere onderdelen zo draagbaar mogelijk zijn. Het KUUROORD zou met draaglijk en herbruikbare componenten moeten worden gebouwd.
* **[AEM de Structuur](#aem-drives-site-structure)** van de Plaats van Drives - de voorste eindontwikkelaar leidt tot componenten en bezit hun interne structuur, maar baseert zich op AEM om de inhoudsstructuur van de plaats te bepalen.
* **[Dynamische rendering](#dynamic-rendering)** - Alle rendering moet dynamisch zijn.
* **[Het dynamische Verpletteren](#dynamic-routing)** - SPA is verantwoordelijk voor het verpletteren en AEM luistert aan het en haalt gebaseerd op het. Om het even welk verpletteren zou ook dynamisch moeten zijn.

Als u deze principes in mening houdt aangezien u uw SPA ontwikkelt, zal het zo flexibel en zo toekomstig bewijs mogelijk zijn terwijl het toelaten van alle gesteunde AEM auteursfunctionaliteit.

Als u niet AEM auteurseigenschappen te hoeven steunen, kunt u een verschillend het ontwerpmodel [van het](#spa-design-models)SPA moeten overwegen.

### Overdraagbaarheid {#portability}

Zoals bij het ontwikkelen van om het even welke component, zouden uw componenten op een zodanige manier moeten worden ontworpen dat hun draagbaarheid wordt gemaximaliseerd. Patronen die de draagbaarheid of herbruikbaarheid van de onderdelen in de weg staan, moeten worden vermeden om ervoor te zorgen dat de onderdelen compatibel, flexibel en duurzaam zijn.

Het resulterende KUUROORD zou met hoogst draagbare en herbruikbare componenten moeten worden gebouwd.

### Sitestructuur AEM stations {#aem-drives-site-structure}

De front-end ontwikkelaar moet zichzelf als verantwoordelijke voor het creëren van een bibliotheek van componenten van het KUUROORD zien die worden gebruikt om app te bouwen. De front-end ontwikkelaar heeft volledige controle over de interne structuur van de componenten. [AEM bezit echter altijd de structuur van de site.](editor-overview.md)

Dit betekent dat de front-end ontwikkelaar klanteninhoud vóór of na het ingangspunt van de componenten kan toevoegen en derde vraag binnen de component kan ook maken. De front-end ontwikkelaar heeft echter geen volledige controle over hoe de componenten bijvoorbeeld nesten.

### Dynamische rendering {#dynamic-rendering}

Het SPA zou zich slechts op dynamische teruggeven van inhoud moeten baseren. Dit is de standaardverwachting waarbij AEM alle onderliggende elementen van de inhoudsstructuur ophaalt en rendert.

Elke expliciete rendering die naar specifieke inhoud verwijst, wordt als statische rendering beschouwd en wordt wel ondersteund, maar is niet compatibel met AEM functies voor het schrijven van inhoud. Dit druist ook in tegen het beginsel van [portabiliteit](#portability).

### Dynamische routering {#dynamic-routing}

Zoals met het teruggeven, zou al het verpletteren ook dynamisch moeten zijn. In AEM, zou [het KUUROORD altijd het verpletteren](routing.md) moeten bezitten en AEM luistert aan het en haalt inhoud die op het wordt gebaseerd.

Om het even welke statische verpletterende werken tegen het [beginsel van portabiliteit](#portability) en beperkt de auteur door niet compatibel te zijn met inhoud auteurseigenschappen van AEM. Bijvoorbeeld, met het statische verpletteren, als de inhoudsauteur een route zou willen veranderen of een pagina zou veranderen, zou hij of zij de front eindontwikkelaar moeten vragen om het te doen.

## Projectarchetype AEM {#aem-project-archetype}

Om het even welk AEM project zou hefboomwerking het [AEM Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)van het Project, dat de projecten van het KUUROORD gebruikend React of Angular steunt en hefboomwerkingen SDK van het KUUROORD.

## SPA-ontwerpmodellen {#spa-design-models}

Als de [principes van het ontwikkelen van SPAs in AEM](#spa-development-principles-for-aem) worden gevolgd, dan zal uw SPA functioneel met alle gesteunde AEM tevreden auteurseigenschappen zijn.

Er kunnen zich echter gevallen voordoen waarin dit niet volledig noodzakelijk is. In de volgende tabel vindt u een overzicht van de verschillende ontwerpmodellen, hun voordelen en hun nadelen.

<table>
 <tbody>
  <tr>
   <th><strong>Ontwerpmodel<br /> </strong></th>
   <th><strong>Voordelen</strong></th>
   <th><strong>Nadelen</strong></th>
  </tr>
  <tr>
   <td>AEM wordt gebruikt als headless CMS zonder het kader van SDK van de Redacteur van het <a href="/help/implementing/developing/spa/reference-materials.md">KUUROORD te gebruiken.</a></td>
   <td>De front-end ontwikkelaar heeft volledige controle over de app.</td>
   <td><p>Inhoudsauteurs kunnen geen gebruik maken van AEM ervaring voor het schrijven van inhoud.</p> <p>De code is noch draagbaar noch herbruikbaar als het statische verwijzingen of het verpletteren bevat.</p> <p>Hiermee wordt het gebruik van de sjablooneditor niet toegestaan, zodat de ontwikkelaar van de front-end via het JCR bewerkbare sjablonen moet bijhouden.</p> </td>
  </tr>
  <tr>
   <td>De voorste eindontwikkelaar gebruikt het kader van SDK van de Redacteur van het KUUROORD maar opent slechts enkele gebieden aan de inhoudauteur.</td>
   <td>De ontwikkelaar behoudt de controle over de app door alleen authoring in beperkte delen van de app in te schakelen.</td>
   <td><p>Inhoudsauteurs zijn beperkt tot een beperkt aantal AEM toepassingen voor het schrijven van inhoud.</p> <p>De code riskeert noch draagbaar noch herbruikbaar als het statische verwijzingen of het verpletteren bevat.</p> <p>Hiermee wordt het gebruik van de sjablooneditor niet toegestaan, zodat de ontwikkelaar van de front-end via het JCR bewerkbare sjablonen moet bijhouden.</p> </td>
  </tr>
  <tr>
   <td>Het project hefboomwerkingen volledig de Redacteur SDK van het KUUROORD en de frontend componenten worden ontwikkeld als bibliotheek en de inhoudsstructuur van app wordt gedelegeerd aan AEM.</td>
   <td><p>De app is herbruikbaar en draagbaar.</p> <p>De auteur van de inhoud kan de app bewerken met AEM ervaring voor het schrijven van inhoud.<br /> </p> <p>Het KUUROORD is compatibel met de malplaatjeredacteur.</p> </td>
   <td><p>De ontwikkelaar heeft geen controle over de structuur van de app en het gedeelte van de inhoud dat aan AEM is gedelegeerd.</p> <p>De ontwikkelaar kan gedeelten van de app nog steeds reserveren voor de inhoud die niet is bedoeld om te worden gemaakt met AEM.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Hoewel alle modellen in AEM worden gesteund, slechts door de derde uit te voeren (en daardoor na de geadviseerde ontwikkelingsbeginselen van het [KUUROORD in AEM](#spa-development-principles-for-aem)) zullen de inhoudsauteurs met de inhoud van het KUUROORD in AEM kunnen in wisselwerking staan en uitgeven aangezien zij gewend zijn.

## Het migreren van Bestaande SPAs aan AEM {#migrating-existing-spas-to-aem}

Over het algemeen als uw SPA de Beginselen van de Ontwikkeling van het [KUUROORD voor AEM](#spa-development-principles-for-aem)volgt, dan zal uw KUUROORD in AEM werken en editable zijn gebruikend de Redacteur van het AEM KUUROORD.

Volg deze stappen om uw bestaande SPA klaar te krijgen om met AEM te werken.

1. **Maak uw componenten JS modulair.** - Maak ze in staat om te worden gerenderd in elke volgorde, positie en grootte.
1. **Gebruik de containers die worden geleverd door de SDK om uw componenten op het scherm te plaatsen.** - AEM biedt een pagina- en alineasysteem voor gebruik.
1. **Maak een AEM component voor elke JS-component.** - De AEM componenten definiëren het dialoogvenster en de JSON-uitvoer.

## Instructies voor front-end ontwikkelaars {#instructions-for-front-end-developers}

De belangrijkste taak bij het in dienst nemen van een front-end ontwikkelaar om een KUUROORD voor AEM tot stand te brengen is op de componenten en hun modellen JSON in te stemmen.

Het volgende is een overzicht van de stappen een front-end ontwikkelaar moet volgen wanneer het ontwikkelen van een KUUROORD voor AEM.

1. **Onderdelen en hun JSON-model overeenkomen**

   Voor-eind ontwikkelaars en achterste AEM ontwikkelaars moeten het eens zijn over welke componenten noodzakelijk zijn en een model zodat is er een één-op-één gelijke van de componenten van het KUUROORD aan de achterste eindcomponenten.

   AEM componenten zijn nog steeds nodig, vooral om te zorgen voor bewerkingsdialoogvensters en om het componentmodel te exporteren.

1. **In React componenten, heb toegang tot het model via`this.props.cqModel`**

   Zodra de componenten worden overeengekomen en het model JSON op zijn plaats is, is de front-end ontwikkelaar vrij om het KUUROORD te ontwikkelen en kan eenvoudig tot het model toegang hebben JSON via `this.props.cqModel`.

1. **De`render()`methode van de component implementeren**

   De front-end ontwikkelaar voert de `render()` methode uit zoals zij passen zien en kan de gebieden van het `cqModel` bezit gebruiken. Hiermee worden het DOM en de HTML-fragmenten uitgevoerd die in de pagina worden ingevoegd. Dit is de standaardmanier om een app te maken in React.

1. **Wijs de component aan het AEM middeltype via toe`MapTo()`**

   De afbeelding slaat componentenklassen op en wordt intern door de verstrekte `Container` component gebruikt om componenten terug te winnen en dynamisch te concretiseren die op het bepaalde middeltype worden gebaseerd.

   Dit dient als de &quot;lijm&quot;tussen voorkant en achtereind zodat weet de redacteur aan welke componenten de reactiecomponenten beantwoorden.

   Het `Page` en `ResponsiveGrid` zijn goede voorbeelden van klassen die de basis uitbreiden `Container`.

1. **De parameter van de component definiëren`EditConfig`als parameter voor`MapTo()`**

   Deze parameter is noodzakelijk om de redacteur te vertellen hoe de component zou moeten worden genoemd zolang bij nog niet wordt teruggegeven of geen inhoud heeft om terug te geven.

1. **De opgegeven`Container`klasse voor pagina&#39;s en containers uitbreiden**

   Pagina- en alineasystemen moeten deze klasse uitbreiden, zodat delegatie naar binnencomponenten naar behoren werkt.

1. **Voer een verpletterende oplossing uit die het gebruiken van HTML5`History`API.**

   Als de optie `ModelRouter` is ingeschakeld, wordt bij het aanroepen van de `pushState` en `replaceState` functies een verzoek aan de gebruiker geactiveerd `PageModelManager` om een ontbrekend fragment van het model op te halen.

   De huidige versie van het model ondersteunt `ModelRouter` alleen het gebruik van URL&#39;s die verwijzen naar het feitelijke bronnenpad van de entry-punten Sling Model. Het steunt niet het gebruik van vanity URLs of aliassen.

   De instructies `ModelRouter` kunnen worden uitgeschakeld of geconfigureerd om een lijst met reguliere expressies te negeren.

## AEM-agnost {#aem-agnostic}

Deze codeblokken illustreren hoe uw React- en Hoekcomponenten niets nodig hebben dat specifiek is voor Adobe of AEM.

* Alles wat zich in de JavaScript-component bevindt, is AEM-agnostisch.
* Nochtans specifiek voor AEM is dat de component JS aan een AEM component met de hulp moet worden in kaart gebracht MapTo.

![Agnostische aanpak AEM](assets/aem-agnostic.png)

De `MapTo` hulplijn is de &quot;lijm&quot; die het mogelijk maakt de achterkant en de voorkant van de onderdelen aan elkaar te koppelen:

* Het vertelt de container JS (of JS paragraafsysteem) welke component JS voor het teruggeven van elk van de componenten verantwoordelijk is die in JSON aanwezig zijn.
* Het voegt een de gegevensattribuut van HTML aan HTML toe die de component JS teruggeeft, zodat de redacteur van het KUUROORD weet welke dialoog aan de auteur wanneer het uitgeven van de component te tonen.

Voor meer informatie over het gebruiken `MapTo` en het bouwen van SPAs voor AEM in het algemeen, zie de Begonnen gids Aan de slag voor uw gekozen kader.

* [Begonnen het worden met SPAs in AEM Gebruikend Reageren](getting-started-react.md)
* [Begonnen het worden met SPAs in AEM Gebruikend Hoekig](getting-started-angular.md)

## AEM Architectuur en SPA&#39;s {#aem-architecture-and-spas}

De algemene architectuur van AEM met inbegrip van ontwikkeling, creatie, en het publiceren milieu&#39;s verandert niet wanneer het gebruiken van SPAs. Nochtans is het nuttig om te begrijpen hoe de ontwikkeling van het KUUROORD in deze architectuur past.

![AEM architectuur en SPA&#39;s](assets/aem-architecture.png)

* **Build-omgeving**

   Dit is waar de bron voor de de toepassingsbron en componentenbron van het KUUROORD uitgecheckt zijn.

   * De NPM clientlib generator leidt tot een cliëntbibliotheek van het project van het KUUROORD.
   * Deze bibliotheek wordt door Maven genomen en samen met de component geïmplementeerd door de Maven Build-plug-in bij de AEM-auteur.

* **AEM-auteur**

   De inhoud wordt gecreeerd op de AEM auteur, met inbegrip van creatieve SPAs.

   Wanneer een KUUROORD gebruikend de Redacteur van het KUUROORD op het auteursmilieu wordt uitgegeven:

   1. De SPA vraagt om de buitenste HTML.
   1. De CSS is geladen.
   1. Javascript van de toepassing van het KUUROORD wordt geladen.
   1. Wanneer de toepassing van het KUUROORD wordt uitgevoerd, wordt JSON gevraagd, toestaand app om DOM van de pagina met inbegrip van de `cq-data` attributen te bouwen.
   1. Met deze `cq-data` kenmerken kan de editor aanvullende pagina-informatie laden, zodat deze weet welke bewerkingsconfiguraties beschikbaar zijn voor de componenten.

* **AEM-publicatie**

   Dit is waar de geschreven inhoud en de gecompileerde bibliotheken met inbegrip van de toepassingsartefacten van het KUUROORD, clientlibs, en de componenten voor openbare consumptie worden gepubliceerd.

* **Dispatcher/CDN**

   De verzender fungeert als de cachelaag van AEM voor bezoekers van de site.
   * Verzoeken worden op dezelfde manier verwerkt als aanvragen bij de AEM-auteur. Er is echter geen verzoek om de pagina-informatie, omdat dit alleen nodig is voor de editor.
   * JavaScript, CSS, JSON en HTML worden in cache geplaatst, waardoor de pagina wordt geoptimaliseerd voor snelle levering.

>[!NOTE]
>
>In AEM is het niet nodig om JavaScript-bouwmechanismen uit te voeren of om JavaScript zelf uit te voeren. AEM slechts gastheren de gecompileerde artefacten van de toepassing van het KUUROORD.

## Volgende stappen {#next-steps}

* [Begonnen het worden met SPAs in AEM gebruiken van Reageren](getting-started-react.md) toont hoe een basisKUUROORD wordt gebouwd om met de Redacteur van het KUUROORD in AEM te werken gebruikend Reageren.
* [Begonnen het worden met SPAs in AEM het gebruiken van Hoekig](getting-started-angular.md) toont hoe een basisKUUROORD wordt gebouwd om met de Redacteur van het KUUROORD in AEM te werken gebruikend Hoekig.
* [Het Overzicht](editor-overview.md) van de Redacteur van het KUUROORD gaat in meer diepte in het communicatie model tussen AEM en het KUUROORD.
* [Het Project](wknd-tutorial.md) van het KND SPA is een geleidelijke leerprogramma die een eenvoudig project van het KUUROORD in AEM uitvoeren.
* [Het dynamische Model aan de Afbeelding van de Component voor SPAs](model-to-component-mapping.md) verklaart het dynamische model aan componentenafbeelding en hoe het binnen SPAs in AEM werkt.
* [Het Vervagen](blueprint.md) van het KUUROORD biedt een diepe duik in hoe het KUUROORD SDK voor AEM werkt voor het geval u wenst om SPAs in AEM voor een kader buiten React of Angular uit te voeren of eenvoudig een dieper begrip zou willen.
