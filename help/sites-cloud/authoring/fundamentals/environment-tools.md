---
title: Ontwerpomgeving en -gereedschappen
description: De ontwerpomgeving van AEM biedt verschillende mechanismen voor het organiseren en bewerken van uw inhoud
exl-id: cc3bd4cf-93bd-429d-9a2a-4a02a7b42f7c
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '2161'
ht-degree: 8%

---


# Ontwerpomgeving en -gereedschappen {#authoring-the-environment-and-tools}

De ontwerpomgeving van AEM biedt verschillende mechanismen voor het organiseren en bewerken van uw inhoud. De beschikbare gereedschappen zijn toegankelijk via de verschillende consoles en pagina-editors.

{{edge-delivery-authoring}}

## Uw site beheren {#managing-your-site}

De **console van Plaatsen** laat u uw website navigeren en beheren, gebruikend de kopbalbar, de toolbar, actiepictogrammen (van toepassing op het geselecteerde middel), broodkruimels, en, wanneer geselecteerd, secundaire sporen (bijvoorbeeld, chronologie en verwijzingen).

Bijvoorbeeld, kolommening:

![ mening van de Kolom ](/help/sites-cloud/authoring/assets/column-view.png)

## Pagina-inhoud bewerken {#editing-page-content}

U kunt een pagina bewerken met de pagina-editor. Bijvoorbeeld:

`http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

![ Redacteur van de Pagina ](/help/sites-cloud/authoring/assets/page-editor.png)

>[!NOTE]
>
>De eerste keer dat u een pagina opent om te bewerken, wordt in een reeks dia&#39;s een overzicht van de functies weergegeven.
>
>U kunt reis overslaan als gewenst en het op elk ogenblik herhalen door van het **menu van de Informatie van de Pagina** te selecteren.

## Toegang tot Help {#accessing-help}

Wanneer het uitgeven van een pagina, **Hulp** kan van worden betreden:

* De [**selecteur van de Informatie van de Pagina**](/help/sites-cloud/authoring/fundamentals/page-properties.md#page-properties) die de inleidende dia&#39;s (zoals getoond de eerste keer u tot de redacteur toegang hebt) toont
* De [ dialoog van de configuratie ](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-toolbar) voor specifieke componenten (gebruikend? pictogram in de dialoogtoolbar), die contextgevoelige hulp toont

Verdere [ op hulp betrekking hebbende middelen zijn beschikbaar bij consoles ](/help/sites-cloud/authoring/getting-started/basic-handling.md#accessing-help).

## Browser voor componenten {#components-browser}

Componenten zijn de bouwstenen van AEM inhoud. U plaatst veelvoudige componenten op een pagina en vormt hun opties om uw inhoudspagina met AEM te bouwen.

De componentenbrowser toont alle componenten die voor gebruik op uw huidige pagina beschikbaar zijn. U kunt deze naar de juiste locatie slepen en vervolgens bewerken om uw inhoud toe te voegen.

De componentenbrowser is een tabblad in het zijpaneel (samen met de [assetbrowser](#assets-browser) en de [contentstructuur](#content-tree)). Als u het zijpaneel wilt openen (of sluiten), gebruikt u het pictogram linksboven op de werkbalk:

![ Kneep van het Zijpaneel ](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

Wanneer u het zijpaneel opent zal het van de linkerkant (selecteer het **Componenten** lusje indien nodig) openen. Wanneer u deze optie opent, kunt u door alle componenten bladeren die beschikbaar zijn voor de pagina.

De daadwerkelijke verschijning en behandeling zijn afhankelijk van het apparatentype u gebruikt:

* **Mobiel apparaat (bijvoorbeeld, iPad)**

  De componentbrowser beslaat volledig de pagina die wordt bewerkt.

  Als u een component aan de pagina wilt toevoegen, houdt u de vereiste component ingedrukt en verplaatst u deze naar rechts (de componentbrowser wordt dan gesloten om de pagina weer weer te geven), waar u de component kunt plaatsen.

  ![ Browser van de Component op mobiele ](/help/sites-cloud/authoring/assets/component-browser-mobile.png)

* **apparaat van de Desktop**

  De componentbrowser wordt links in het venster geopend.

  Als u een component aan de pagina wilt toevoegen, klikt u op de gewenste component en sleept u deze naar de gewenste locatie.

  ![ Browser van de Component op Desktop ](/help/sites-cloud/authoring/assets/component-browser-desktop.png)

  Componenten worden vertegenwoordigd door

   * Componentnaam
   * Componentgroep (grijs)
   * Pictogram of afkorting
      * De standaardcomponentpictogrammen zijn monochroom.
      * Afkortingen zijn altijd de eerste twee tekens van de componentnaam.

  Van de hoogste toolbar in **Componenten** browser kunt u:

   * Componenten filteren op naam.
   * Beperk de weergave tot een specifieke groep met behulp van de vervolgkeuzelijst.

  Voor een meer gedetailleerde beschrijving van de component, kunt u het informatiepictogram naast de component in **selecteren Componenten** browser (als beschikbaar). Bijvoorbeeld, voor het **Fragment van de Inhoud**:

  ![ Browser van de Component informatie ](/help/sites-cloud/authoring/assets/component-browser-information.png)

  Voor zelfs meer informatie over de componenten beschikbaar aan u ziet de [ Console van de Component ](/help/sites-cloud/authoring/features/components-console.md).

>[!NOTE]
>
>Een mobiel apparaat wordt gedetecteerd wanneer de breedte minder dan 1024 px is. Dit kan ook het geval zijn voor een klein bureaubladvenster.

## Assets Browser {#assets-browser}

De activa browser toont alle [ activa ](/help/assets/overview.md) die voor direct gebruik op uw huidige pagina beschikbaar zijn.

De assetbrowser is een tabblad in het zijpaneel, samen met de [componentenbrowser](#components-browser) en de [contentstructuur](#content-tree). Als u het zijpaneel wilt openen of sluiten, gebruikt u het pictogram linksboven op de werkbalk:

![ Kneep van het Zijpaneel ](/help/sites-cloud/authoring/assets/side-panel-toggle.png)

Wanneer u het zijpaneel opent, schuift het van de linkerkant open. Selecteer indien nodig het **Assets** lusje.

![ Browser van Assets knoop ](/help/sites-cloud/authoring/assets/assets-browser-button.png)

Wanneer de middelenbrowser is geopend, kunt u door alle elementen bladeren die beschikbaar zijn voor uw pagina. Met oneindig schuiven wordt de lijst indien nodig uitgebreid.

![ Browser van Assets ](/help/sites-cloud/authoring/assets/assets-browser.png)

Als u een element aan de pagina wilt toevoegen, selecteert u het element en sleept u het naar de gewenste locatie. Dit kan zijn:

* Een bestaand onderdeel van het desbetreffende type.
   * U kunt bijvoorbeeld een element van het type afbeelding naar een afbeeldingscomponent slepen.
* A [ placeholder ](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-placeholder) in het paragraafsysteem om een component van het aangewezen type tot stand te brengen.
   * U kunt bijvoorbeeld een element van het type afbeelding naar het alineasysteem slepen om een component Image te maken.

>[!NOTE]
>
>Dit is beschikbaar voor specifieke elementen en componenttypen. Zie [ Invoegend een Component gebruikend Browser van Assets ](/help/sites-cloud/authoring/fundamentals/editing-content.md#inserting-a-component-using-the-assets-browser) voor meer details.

Vanuit de bovenste werkbalk van de middelenbrowser kunt u de elementen filteren op:

* Naam
* Pad
* Elementtype zoals afbeeldingen, video&#39;s, documenten, alinea&#39;s, inhoudsfragmenten en ervaringsfragmenten
* Elementkenmerken zoals oriëntatie en stijl
   * Alleen beschikbaar voor bepaalde typen elementen

De daadwerkelijke verschijning en behandeling zijn afhankelijk van het apparatentype u gebruikt:

* **Mobiel Apparaat**

  De elementenbrowser beslaat volledig de pagina die wordt bewerkt.

  Als u een element aan uw pagina wilt toevoegen, houdt u het vereiste element ingedrukt en verplaatst u het naar rechts. De elementenbrowser wordt dan gesloten en geeft de pagina weer, waar u het element aan de gewenste component kunt toevoegen.

  ![ Browser van Assets op mobiele ](/help/sites-cloud/authoring/assets/assets-browser-mobile.png)

* **Apparaat van de Desktop**

  De middelenbrowser wordt links in het venster geopend.

  Als u een element aan uw pagina wilt toevoegen, klikt u op het gewenste element en sleept u het naar de gewenste component of locatie.

  ![ Browser van Assets op Desktop ](/help/sites-cloud/authoring/assets/assets-browser-desktop.png)

>[!NOTE]
>
>Een mobiel apparaat wordt gedetecteerd wanneer de breedte minder dan 1024 px is, dat wil zeggen ook in een klein bureaubladvenster.

Als u een verandering in activa moet snel aanbrengen, kunt u de [ activaredacteur ](/help/assets/manage-digital-assets.md) van activa direct van activabrowser beginnen door het Edit pictogram naast de naam van activa te klikken wordt getoond die.

![ Activa geeft knoop uit ](/help/sites-cloud/authoring/assets/asset-edit-button.png)

## Inhoudsstructuur {#content-tree}

De **Boom van de Inhoud** geeft een overzicht van alle componenten op de pagina in een hiërarchie zodat kunt u in een blik zien hoe de pagina wordt samengesteld.

De inhoudsstructuur is een tabblad in het zijpaneel (samen met de browser met componenten en elementen). Als u het zijpaneel wilt openen (of sluiten), gebruikt u het pictogram linksboven op de werkbalk:

![ knoop van de Boom van de Inhoud ](/help/sites-cloud/authoring/assets/content-tree-button.png)

Als u het zijpaneel opent, wordt het geopend (van de linkerkant). Selecteer indien nodig het **lusje van de Boom van de Inhoud**. Wanneer open kunt u een vertegenwoordiging van de boommening van uw pagina of malplaatje zien, zodat het gemakkelijker is om te begrijpen hoe zijn inhoud hiërarchisch gestructureerd is. Op een complexe pagina is het bovendien gemakkelijker om tussen componenten van de pagina te schakelen.

![ de Boom van de Inhoud ](/help/sites-cloud/authoring/assets/content-tree-editor.png)

Een pagina kan eenvoudig uit veel van hetzelfde type componenten bestaan, zodat in de structuur van de inhoud (component) beschrijvende tekst (grijs) wordt weergegeven achter de naam van het componenttype (in zwart). De beschrijvende tekst is afkomstig uit gemeenschappelijke eigenschappen van de component, zoals titel of tekst.

Componenttypen worden weergegeven in de taal van de gebruiker, terwijl de tekst van de componentbeschrijving uit de paginataal komt.

Als u klikt op het chevron naast een component, wordt dat niveau samengevouwen of uitgevouwen.

![ de uitbreiding van de Boomboom van de Inhoud ](/help/sites-cloud/authoring/assets/content-tree-chevron.png)

Wanneer u op de component klikt, wordt de component in de pagina-editor gemarkeerd. Welke acties beschikbaar zijn, is afhankelijk van de paginastatus:

* Bijvoorbeeld een basispagina:

  ![ benadrukte de Boom van de Inhoud ](/help/sites-cloud/authoring/assets/content-tree-highlighted.png)

  De componenten van een basispagina hebben de gebruikelijke opties.

  Als de component waarop u klikt in de structuur bewerkbaar is, wordt er een moersleutelpictogram rechts van de naam weergegeven. Wanneer u op dit pictogram klikt, wordt het dialoogvenster Bewerken voor de component gestart.

  ![ de Boom van de Inhoud geeft knoop uit ](/help/sites-cloud/authoring/assets/content-tree-edit.png)

* Een pagina die deel van a [ livecopy ](/help/sites-cloud/administering/msm/overview.md) uitmaakt, waar de componenten van een andere pagina worden geërft.

>[!NOTE]
>
>De inhoudsstructuur is niet beschikbaar als u een pagina bewerkt op een mobiel apparaat (als de breedte van de browser minder dan 1024 px is).

## Fragmenten - gekoppelde inhoudsbrowser {#fragments-associated-content-browser}

Als uw pagina de Fragmenten van de Inhoud bevat dan zult u ook toegang tot [ browser voor Verwante Inhoud ](/help/sites-cloud/authoring/fundamentals/content-fragments.md#using-associated-content) hebben.

## Verwijzingen {#references}

**Verwijzingen** toont verbindingen aan de geselecteerde pagina:

* Blauwdrukken
* Lanceringen
* Live kopieën
* Taalkopieën
* Binnenkomende koppelingen
* Gebruik van de referentiecomponent: geleend en geleend inhoud

Open de vereiste console, dan navigeer aan het vereiste middel en open **Verwijzingen** gebruikend:

![ optie van Verwijzingen ](/help/sites-cloud/authoring/assets/references.png)

[ selecteer uw vereist middel ](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) om een lijst van verwijzingstypes relevant voor dat middel te tonen:

![ details van Verwijzingen ](/help/sites-cloud/authoring/assets/references-detail.png)

Selecteer het juiste referentietype voor meer informatie. In bepaalde situaties zijn aanvullende acties beschikbaar wanneer u een specifieke verwijzing selecteert, zoals:

* **Binnenkomende Verbindingen**, verstrekt een lijst van pagina&#39;s die de pagina van verwijzingen voorzien, samen met directe toegang tot **geeft** één van die pagina&#39;s uit wanneer u een specifieke verbinding selecteert.

   * Dit kan alleen statische koppelingen weergeven, niet dynamisch gegenereerde koppelingen, bijvoorbeeld vanuit de component List.

* Instanties van geleende en geleende inhoud gebruikend de **component van de Verwijzing**, van hier kunt u aan het van verwijzingen voorzien/van verwijzingen voorzien pagina navigeren
* [ Lanceringen ](/help/sites-cloud/authoring/launches/overview.md), verleent toegang tot verwante lanceringen
* [ Levende Exemplaren ](/help/sites-cloud/administering/msm/overview.md) toont de wegen van alle levende exemplaren die op het geselecteerde middel gebaseerd zijn.
* [ Vervaging ](/help/sites-cloud/administering/msm/best-practices.md), verstrekt details en diverse acties
* [ Exemplaren van Talen ](/help/sites-cloud/administering/translation/managing-projects.md#creating-translation-projects-using-the-references-panel), verstrekt details en diverse acties

## Gebeurtenissen - tijdlijn {#events-timeline}

Voor aangewezen middelen (bijvoorbeeld, kunnen de pagina&#39;s van de **console van Plaatsen**, of activa van de **Assets** console) de [ chronologie worden gebruikt om de recente activiteit op om het even welke geselecteerde punten ](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) te tonen.

Open de vereiste console, dan navigeer aan het vereiste middel en open **Chronologie**, gebruikend:

![ optie van de Chronologie ](/help/sites-cloud/authoring/assets/timeline.png)

[ selecteer uw vereist middel ](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources), dan of **toon Alle** of **Activiteiten** om van om het even welke recente acties op de geselecteerde middelen een lijst te maken:

![ details van de Chronologie ](/help/sites-cloud/authoring/assets/timeline-detail.png)

## Pagina-informatie {#page-information}

Met het pictogram Pagina-informatie (equalizer) opent u een menu dat ook informatie bevat over de laatste bewerking en de laatste publicatie. Afhankelijk van de kenmerken van de pagina, de site en uw exemplaar, zijn mogelijk meer of minder opties beschikbaar:

![ optie van de Informatie van de Pagina ](/help/sites-cloud/authoring/assets/page-information.png)

* [Eigenschappen openen](/help/sites-cloud/authoring/fundamentals/page-properties.md)
* [Uitrolpagina](/help/sites-cloud/administering/msm/overview.md#msm-from-the-ui)
* [Workflow starten](/help/sites-cloud/authoring/workflows/applying.md#starting-a-workflow-from-the-page-editor)
* [Pagina vergrendelen](/help/sites-cloud/authoring/fundamentals/editing-content.md#locking-a-page)
* [Publish-pagina](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#publishing-pages-1)
* [Publicatie van pagina ongedaan maken](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#unpublishing-pages)
* [Sjabloon bewerken](/help/sites-cloud/authoring/features/templates.md)
* [Weergeven als gepubliceerd](/help/sites-cloud/authoring/fundamentals/editing-content.md#view-as-published)
* [Weergeven in Admin](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)
* [Help](/help/sites-cloud/authoring/getting-started/basic-handling.md#accessing-help)
* [ bevorderen Lanceer ](/help/sites-cloud/authoring/launches/promoting.md) (slechts als de pagina een lancering is)

Bovendien **de Informatie van de Pagina** kan toegang tot analyses en aanbevelingen, wanneer aangewezen verlenen.

## Paginamodi {#page-modes}

Er zijn verschillende modi voor het bewerken van een pagina die verschillende handelingen mogelijk maken:

* [ geeft ](/help/sites-cloud/authoring/fundamentals/editing-content.md) uit - de wijze om te gebruiken wanneer het uitgeven van de paginainhoud.
* [ Lay-out ](/help/sites-cloud/authoring/features/responsive-layout.md) - laat u uw ontvankelijke lay-out afhankelijk van apparaat tot stand brengen en uitgeven (als de pagina op een lay-outcontainer gebaseerd is)
* [ het richten ](/help/sites-cloud/authoring/personalization/targeted-content.md) - vergroot inhoudsrelevantie door zich te richten en over alle kanalen te meten.
* [ Timewarp ](/help/sites-cloud/authoring/features/page-versions.md#timewarp) - laat u een paginastaat op een bepaald punt in tijd bekijken.
* [ Levende Status van het Exemplaar ](/help/sites-cloud/authoring/fundamentals/editing-content.md#live-copy-status) - staat een snel overzicht van de levende exemplaarstatus toe en welke componenten niet worden/worden geërft.
* [Modus voor ontwikkelaars](/help/implementing/developing/tools/developer-mode.md)
* [ Voorproef ](/help/sites-cloud/authoring/fundamentals/editing-content.md#previewing-pages) - wordt gebruikt om de pagina te bekijken aangezien het op publiceert milieu wordt getoond; of het navigeren gebruikend verbindingen in de inhoud.
* [ annoteert ](/help/sites-cloud/authoring/fundamentals/annotations.md) - wordt gebruikt om annotaties op de pagina toe te voegen of te bekijken.

U kunt deze openen met de pictogrammen in de rechterbovenhoek. Het werkelijke pictogram verandert in de modus die u momenteel gebruikt:

![ wijzen van de Pagina ](/help/sites-cloud/authoring/assets/page-modes.png)

>[!NOTE]
>
>* Afhankelijk van de kenmerken van de pagina zijn sommige modi mogelijk niet beschikbaar.
>* Voor toegang tot bepaalde modi zijn de juiste machtigingen/bevoegdheden vereist.
>* De modus Ontwikkelaar is niet beschikbaar op mobiele apparaten vanwege ruimtebeperkingen.
>* Er is a [ toetsenbordkortere weg ](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) ( `Ctrl-Shift-M`) om tussen **Voorproef** en momenteel geselecteerde wijze (bijvoorbeeld, **uitgeeft**, **Lay-out**, etc.) van een knevel te voorzien.
>

## Padselectie {#path-selection}

Vaak is het tijdens het ontwerpen nodig een andere bron te selecteren, bijvoorbeeld wanneer u een koppeling naar een andere pagina of bron definieert of een afbeelding selecteert. Om een weg gemakkelijk te selecteren, [ weggebieden ](#path-fields) aanbieden auto-volledig en [ wegbrowser ](#path-browser) staat voor robuustere selectie toe.

### Padvelden {#path-fields}

Het voorbeeld dat hier wordt gebruikt om te illustreren is de afbeeldingscomponent. Voor meer informatie over het gebruiken van en het uitgeven van componenten zie [ Componenten voor de Authoring van de Pagina ](/help/sites-cloud/authoring/fundamentals/components.md).

Padvelden beschikken nu over de functionaliteit voor automatisch aanvullen en vooruitkijken, zodat u een resource gemakkelijker kunt vinden.

Het klikken van de **Open Dialoog van de Selectie** knoop op het weggebied opent [ wegbrowser ](#path-browser) dialoog om voor meer gedetailleerde selectieopties toe te staan.

![ Open de knoop van de Dialoog van de Selectie ](/help/sites-cloud/authoring/assets/open-selection-dialog-button.png)

U kunt ook beginnen te typen in het veld Pad en AEM biedt overeenkomende paden terwijl u typt.

![ Open de knoop van de Dialoog van de Selectie ](/help/sites-cloud/authoring/assets/path-selection-completion.png)

### Padbrowser {#path-browser}

De wegbrowser wordt georganiseerd als de [ kolommening ](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) van de plaatsenconsole, die voor meer gedetailleerde selectie van middelen toestaat.

![ Browser van de Weg ](/help/sites-cloud/authoring/assets/path-browser.png)

* Zodra een middel wordt geselecteerd, wordt de **Uitgezochte** knoop bij het hoger-recht van de dialoogdoos actief. Selecteer om de selectie te bevestigen of **annuleert** om te aborteren.
* Als de selectie van meerdere assets is toegestaan binnen de context, activeert het selecteren van een resource ook de knop **Selecteren**, maar wordt er ook een telling van het aantal geselecteerde resources in de rechterbovenhoek van het venster toegevoegd. Klik op de **X** naast het getal om de selectie op te heffen.
* Wanneer u door de boom navigeert, wordt uw plaats weerspiegeld in de broodkruimels bij de bovenkant van de dialoog. Deze broodkruimels kunnen ook worden gebruikt om snel binnen de middelhiërarchie te springen.
* U kunt op elk gewenst moment het zoekveld boven in het dialoogvenster gebruiken. Klik **X** op het onderzoeksgebied om het onderzoek te ontruimen.
* Als u uw zoekopdracht wilt beperken, kunt u de filteropties zichtbaar maken en de resultaten filteren op basis van een bepaald pad.

  ![ de optie van Filters ](/help/sites-cloud/authoring/assets/filters-option.png)

## Sneltoetsen {#keyboard-shortcuts}

Diverse [ toetsenbordkortere weg ](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md) is beschikbaar.
