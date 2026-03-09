---
title: Prompted Guide for Experience Modernization Agent
description: Deze gids verstrekt uiteinden voor efficiënte het veroorzaken van de Agent van de Modernisering van de Ervaring en beschrijft wat zijn vaardigheden doen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: e2a9c55644c0d9542f6a299f0df30a3dfd4a55de
workflow-type: tm+mt
source-wordcount: '2696'
ht-degree: 0%

---


# Prompted Guide for Experience Modernization Agent {#prompting-guide}

De agent van de Modernisering van de Ervaring selecteert automatisch de aangewezen vaardigheid die op natuurlijk-taalverzoeken wordt gebaseerd. Deze gids verstrekt uiteinden voor effectief het vragen en beschrijft wat de vaardigheden doen.

## Algemene tips {#general-tips}

### Sommige vaardigheden hangen van output van andere vaardigheden af. {#dependency}

* Omdat voor bulkimport de importinfrastructuur nodig is die door paginamigratie wordt gemaakt, migreert u ten minste één pagina voordat u bulkimport uitvoert.
* Aangezien blok-CSS verwijst naar de algemene ontwerptokens, voltooit u het ontwerp voor de hele site voordat u afzonderlijke blokken stileert.

### De AI volgt gestructureerde workflows en zal verduidelijkende vragen stellen wanneer zij meer informatie nodig heeft. {#workflows}

* Vertrouw op het proces en beantwoord deze kwalificerende vragen terwijl ze verschijnen.
* Probeer niet alle vereisten vooraf te laden in de eerste prompt.

### Maak markeringsbestanden in het project om projectspecifieke regels, richtlijnen, ontwerpbeslissingen of beperkingen te documenteren. {#markdown-files}

* Deze markeringsbestanden (bijvoorbeeld INSTRUCTIONS.md, CONTEXT.md) kunnen conventies voor het benoemen van bestanden, regels voor het toewijzen van inhoud of richtlijnen voor het merk bevatten.
* Wanneer het beginnen van een nieuw gesprek, vraag de agent om &quot;op te warmen door de projectdocumentatie&quot;te lezen zodat laadt het deze context alvorens met taken te werk te gaan.

### Het de contextvenster van de agent is niet oneindig. {#limited-window}

* Tijdens lange gesprekken kunnen eerdere instructies gecomprimeerd of vergeten worden.
* Als de agent context schijnt te hebben verloren, of het herinneren aan de belangrijkste punten of ontruim de praatje en begin vers met een opwarmingsherinnering om projectdocumentatie te lezen.

### Gebruik iteratieve aanwijzingen om resultaten te verfijnen. {#iterate}

* Als iets niet goed kijkt (bijvoorbeeld, verkeerde achtergrondkleur op een blok), vraag de agent om de specifieke kwestie te bevestigen eerder dan over te beginnen.

## Vaardigheden voor het maken en migreren van sites {#site-migration}

De Site Modernization Agent biedt veel vaardigheden voor het maken van nieuwe Edge Delivery Services-sites en het migreren van bestaande websites. Elke nieuwe Edge Delivery-site of migratieproject moet deze vaardigheden benutten.

### Een site of pagina migreren naar AEM {#migrate-a-site}

Gebruik deze prompt wanneer u inhoud van een bestaande website naar Edge Delivery Services migreert.

#### Voorbeeld vragen {#example-migrate}

* &quot;Deze pagina migreren: `https://example.com/about`
* &quot;Deze pagina&#39;s migreren: URL1, URL2, URL3&quot;

#### Wat u moet weten {#wtk-migrate}

* Migratie volgt een workflow in zeven stappen:
   1. De agent schrapt bronpagina.
   1. Het identificeert sectiestructuur.
   1. Het voert ontwerpanalyse uit.
   1. De inhoud wordt toegewezen aan blokvarianten.
   1. Er wordt een markeringseffect gegenereerd.
   1. Er wordt importinfrastructuur gemaakt.
   1. Het geeft een voorvertoning van het resultaat.
* De agent analyseert pagina&#39;s gebruikend een hiërarchie op twee niveaus:
   * Eerst worden de sectiegrenzen geïdentificeerd (wijzigingen in de achtergrond, verschuivingen in de tussenruimte)
   * Vervolgens worden de inhoudsreeksen binnen elke sectie geïdentificeerd.
* De auteursanalyse volgt [ Model van David.](https://www.aem.live/docs/davidsmodel)
   * voor elke inhoudsequentie controleert het eerst &quot;Kan een auteur dit door normaal typen tot stand brengen?&quot;
   * De standaardinhoud (koppen, alinea&#39;s, lijsten, inline-afbeeldingen) heeft de voorkeur boven blokken.
* De agent probeert bestaande blokken uit de blokbibliotheek van de repository opnieuw te gebruiken voordat er nieuwe worden gemaakt.
   * Wanneer inhoud niet aan een bestaand blok kan worden toegewezen, leidt het tot nieuwe blokvarianten.
   * U kunt vragen om wijzigingen, nieuwe varianten aanvragen of toewijzingen interactief aanpassen.
* Blokelementen worden bijgehouden met metagegevens.
   * Wanneer het migreren van veelvoudige pagina&#39;s, laadt de agent eerst bestaande douanevarianten en hergebruikt hen wanneer het stileren gelijken (70% gelijkenisdrempel die op doel, kleuren, typografie, het uit elkaar plaatsen, lay-out wordt gebaseerd).
* Koptekst, navigatie en voettekst zijn uitgesloten van paginamigratie. Deze worden behandeld door specifieke vaardigheden.
* Elke migratie maakt importinfrastructuur (paginasjablonen, blokparsers, transformatoren) voor toekomstige bulkimport.

### Bulkimport {#bulk-import}

Gebruik deze herinnering om vele pagina&#39;s van het zelfde malplaatje na de voltooiing van een [ aanvankelijke enig-paginamigratie in te voeren.](#migrate-a-site)

#### Voorbeeld vragen {#example-prompts-bulk-import}

* &quot;Voer de bulkimport uit op deze pagina&#39;s: URL1, URL2, URL3.&quot;
* &quot;bulkimport uitvoeren op alle productpagina&#39;s.&quot;
* &quot;Bulk importeert deze blogpagina&#39;s: URL1, URL2.&quot;

#### Wat u moet weten {#wtk-bulk-import}

* Bulkimport is afhankelijk van importinfrastructuur die tijdens een eerdere migratie van één pagina is gemaakt.
   * Dit zijn paginasjablonen (sectiestructuur), transformatoren (DOM-opruiming voor de hele site) en parsers (blokspecifieke HTML naar tabelconversie).
* U moet ten minste één representatieve pagina per sjabloon migreren voordat bulkimport kan worden uitgevoerd.
* Bulkimport gebruikt de structuur en toewijzingen die zijn ingesteld tijdens migratie van één pagina opnieuw.
   * Sjablonen worden niet helemaal opnieuw afgeleid.
* Transformatoren werken op het gehele DOM voor en na het parseren. Parameters werken op het individuele blokniveau.
* Alle parsers worden gevalideerd voordat het bulkimporteren kan worden uitgevoerd.
* Eén sjabloon komt overeen met één configuratie voor bulkimport.
   * Het mengen van sjablonen in één uitvoering wordt niet ondersteund.

#### Normale workflow {#typical-workflow}

De aanbevolen workflow is iteratief: eerst op een kleine set valideren en vervolgens vergroten.

1. **stel eerst een single-page migratie in werking.** - Migreer één representatieve pagina voor het malplaatje u van plan bent om de invoer los te maken.
   * Hierdoor ontstaat de vereiste importinfrastructuur.
1. **stel de bulkinvoer op een kleine reeks pagina&#39;s in werking.** - Vraag de agent om de bulkimport uit te voeren en geef een korte lijst op met URL&#39;s die dezelfde sjabloon volgen.
1. **Overzicht en verfijnen de resultaten.** - Controleer de geïmporteerde pagina&#39;s.
   * Als er iets verkeerd lijkt, vraagt u de agent om parameters, transformatoren of logica voor importeren aan te passen.
1. **Schaal omhoog.** - Wanneer de resultaten er goed uitzien, geeft u de volledige lijst met URL&#39;s op.
   * De agent zal dezelfde importlogica opnieuw gebruiken en bulkimport op schaal uitvoeren.

### Webpagina&#39;s schalen {#scraping-webpages}

Gebruik deze aanwijzing om inhoud, metagegevens en afbeeldingen uit een bron-URL te extraheren voor analyse of migratie.

#### Voorbeeld vragen {#example-scraping}

* &quot;Deze pagina plakken voor analyse: `https://example.com`&quot;
* &quot;Inhoud extraheren uit `https://example.com/product`&quot;

#### Wat u moet weten {#wtk-scraping}

* Deze herinnering wordt gewoonlijk automatisch aangehaald als eerste stap van paginamigratie.
* Inhoud die via CSS is verborgen, wordt ook vastgelegd als deze aanwezig is in het DOM.
* Lazy geladen afbeeldingen en door de client gegenereerde inhoud worden verwerkt door in Chromium zonder kop door de pagina te schuiven en scripts te laten uitvoeren.
* WebP-/AVIF-/SVG-afbeeldingen worden voor compatibiliteit omgezet in PNG.
* Metagegevens worden geëxtraheerd, zoals titel, beschrijving, Open Graph-tags, JSON-LD gestructureerde gegevens, canonieke URL.
* Afbeeldingen in DOM zijn hersteld.
   * background-image wordt omgezet in img.
   * Afbeeldingselementen worden losgekoppeld
   * srcset is omgezet in src
   * Relatieve URL&#39;s worden omgezet in absolute waarden
   * Inline SVG die wordt omgezet in img-bestanden.
* Geanimeerde documentpaden worden gegenereerd (kleine letters zonder `.html` extensie).
* De volgende outputs worden geproduceerd:
   * `screenshot.png`
   * `cleaned.html` (geen scripts/stijlen)
   * `metadata.json`
   * `images/` -map met lokale kopieën
* Gebruikers kunnen vragen naar schermafbeeldingsafmetingen en specifieke apparaatformaten (mobiel, bureaublad) aanvragen voor het extraheren van inhoud.
* Door inhoud op meerdere onderbrekingspunten te extraheren neemt de verwerkingstijd toe.

### Ontwerpmigratie {#design-migration}

Gebruik deze aanwijzing om een visueel ontwerp van een bronsite op Edge Delivery Services te extraheren en toe te passen.

#### Voorbeeld vragen {#example-design}

* &quot;Het ontwerp migreren vanuit `https://example.com`&quot;
* &quot;Ontwerptokens uitnemen&quot;
* &quot;Stijl het hoofdblok&quot;

#### Wat u moet weten {#wtk-design}

* Ontwerpmigratie heeft twee fasen:
   1. Fase 1 (voor de hele site) extraheert het volgende naar `styles/styles.css` :
      * Globaal kleurenpalet en accentkleuren
      * Typografiesysteem (lettertypen, grootten, gewichten)
      * Tussenruimte (opvulling, marges, tussenruimten)
      * Sectieachtergronden (licht, donker, gekleurd)
      * Stijlen van basiscomponenten (knoppen, koppelingen, afbeeldingen)
      * Uitvoer naar
   1. Fase 2 migreert afzonderlijke blokstijlen en maakt blokspecifieke CSS in `/blocks/{name}/{name}.css` .
* Voor blokopmaak (fase 2) moet het ontwerp voor de hele site (fase 1) eerst worden voltooid.
   * Het algemene ontwerpsysteem biedt aangepaste CSS-eigenschappen die referentie blokkeren.
* Geschatte tijd:
   * Fase 1: 5-10 minuten
   * Fase 2: 10-15 minuten
* De dubbelzinnige verzoeken standaard om migratie te voltooien (beide fasen).

### Blokkerkritiek {#block-critique}

Gebruik deze prompt om afzonderlijke gemigreerde blokken te valideren en te verfijnen en ervoor te zorgen dat deze accuraat zijn ten opzichte van de oorspronkelijke website.

#### Voorbeeld vragen {#example-block-critique}

* &quot;Critique hero block&quot;
* &quot;Valideer blok douanekaarten&quot;

#### Wat u moet weten {#wtk-block-critique}

* Blokkritiek vergelijkt een gemigreerd blok met zijn oorspronkelijke bron en past herhaaldelijk CSS-correcties toe totdat een visuele gelijkenis van 85% is bereikt of drie herhalingen zijn voltooid.
* De vaardigheid vereist dat het blok eerst door paginamigratie is gecreeerd.
* Een blokkritiek volgt een zes-stap werkschema:
   1. Het oorspronkelijke blok van de bronpagina wordt vastgelegd met een XPath-kiezer.
   1. De kritische sessie wordt geïnitialiseerd.
   1. Het originele blok wordt geïnspecteerd (screenshots, stijlen, HTML).
   1. Het inspecteert het gemigreerde blok.
   1. Hiermee worden elementen vergeleken en wordt een score voor gelijkenis gegenereerd met CSS-correcties.
   1. Het past fixes toe en herinspecteert tot het doel van 85% wordt bereikt.
* Elke herhaling toont een volledig kritiek rapport met alle verschillen, past alle CSS moeilijke situaties (die door visueel effect worden voorrang gegeven) toe, verifieert in voorproef, herinspecteert, en toont verbeteringsmetriek.
* Gebruik de blokkritiek nadat [ ontwerpmigratie ](#design-migration) volledig is.

### Paginantiek {#page-critique}

Gebruik deze prompt om gehele gemigreerde pagina&#39;s te valideren op basis van visuele getrouwheid van volledige pagina ten opzichte van de oorspronkelijke website.

#### Voorbeeld vragen {#example-page-critique}

* &quot;De pagina &quot;about&quot; kritiseren
* &quot;De gemigreerde pagina valideren op `https://example.com/about`&quot;

#### Wat u moet weten {#wtk-page-critique}

* Paginacritique voert een visuele vergelijking van volledige pagina uit tussen het origineel en de gemigreerde pagina, die zich herhaalt totdat een 85% gelijkenisdoel is bereikt of drie herhalingen zijn voltooid.
* Een paginacritique heeft een workflow in vijf stappen:
   1. Er wordt een kritische sessie geïnitialiseerd.
   1. Alle elementen op de oorspronkelijke pagina worden gecontroleerd.
   1. Alle elementen op de gemigreerde pagina worden gecontroleerd.
   1. De methode vergelijkt en genereert een score voor gelijkenis met geprioriteerde CSS-oplossingen.
   1. Het past fixes toe en herinspecteert tot het doel van 85% wordt bereikt.
* Voor een paginacritique zijn de URL van de bronpagina en het gemigreerde pad (bijvoorbeeld &quot;/about&quot;) vereist als invoer.
* Gebruik paginacritique bij het valideren van de algehele paginafrouwbaarheid of bij het gelijktijdig valideren van meerdere blokken.
* [ blokkritiek van het Gebruik ](#block-critique) voor geconcentreerde bevestiging op specifieke componenten.
* De volgende workflow wordt aanbevolen:
   1. Een pagina migreren.
   1. Pas een ontwerp toe.
   1. Blokkritiek uitvoeren op sleutelblokken
   1. Voer paginacritique uit voor volledige validatie.

### Migratie Figma Block {#figma-block-migration}

Gebruik deze aanwijzing om een blok van Figma-ontwerp naar Edge Delivery Services te migreren.

Merk op dat u opstelling uw details van Figuren in [ de Console van de Modernisering van de Ervaring ](/help/ai-in-aem/agents/brand-experience/modernization/console.md) moet om deze herinnering te gebruiken.

#### Voorbeeld vragen {#example-figma}

* &quot;Het blok migreren `https://figma.com/design/{fileKey}?node-id={nodeId}` naar Edge Delivery Services&quot;
* &quot;Migreren `{blockName}` van `https://figma.com/file/{fileKey}` naar Edge Delivery Services&quot;

#### Wat u moet weten {#wtk-figma}

* Deze vaardigheid migreert één blok tegelijkertijd, niet volledige pagina&#39;s of volledige dossiers van Figma.
* Voor de beste resultaten:
   * Selecteer het specifieke blok dat u wilt migreren in Figma en kopieer de koppeling (met `node-id` ) of naam.
   * Geef de parameter `node-id` op in de URL om het exacte blok als doel in te stellen.
* Wanneer u deze vaardigheid in werking stelt, worden de volgende stappen automatisch uitgevoerd in het ontvangen milieu:
   1. **de structuurontdekking van het Blok** - de agent leest de knoop van Figma om lagen en componenten te begrijpen.
   1. **Globale stijlextractie** - de agent trekt kleuren, typografie, en het uit elkaar plaatsen in `styles/styles.css` als CSS douaneeigenschappen (ontwerptekenen).
   1. **blokspecifieke stijlverwezenlijking** - de agent leidt extra CSS douaneeigenschappen specifiek voor het blok dat wordt gemigreerd.
   1. **Toewijzing aan bestaande blokken** — De agent identificeert het dichtste passende blok in de het blokbibliotheek van uw project en leidt tot een douanevariant.
   1. **CSS generatie** — De agent schrijft stijlen die naar de gehaalde CSS douaneeigenschappen van verwijzingen voorzien, die ontwerpconsistentie verzekeren.
   1. **download van Activa** — De agent bewaart beelden en pictogrammen van Cijfer aan de ontvangen werkruimte van het milieu.
   1. **de inhoudsgeneratie van Edge Delivery Services** — De agent leidt tot het markeringsdossier na het blokstructuur EDS
   1. **bevestiging van de Output** - de agent previews het resultaat en voert visuele vergelijking tegen het originele ontwerp van Figma uit.
* De vaardigheid leest eerst meta-gegevens (stap 1) om structuur te begrijpen, en haalt dan gedetailleerde ontwerpcontext (stappen 2-5) uit.
   * Deze gefaseerde aanpak voorkomt problemen met grote of complexe figuurbestanden.
* Deze vaardigheid neemt een stijl-eerste benadering.
   * Alle stijlen worden geëxtraheerd als aangepaste CSS-eigenschappen (ontwerptokens) voordat er CSS wordt geschreven.
   * Hierdoor blijft het gemigreerde blok consistent met uw ontwerpsysteem.
* Voor de vraag is de figma-URL (met `fileKey` en optioneel `node-id` ) of een figuurbestandssleutel rechtstreeks als invoer vereist.

### Navigatie instellen {#navigation-setup}

Gebruik deze prompt om sitenavigatie in te stellen of te migreren.

#### Voorbeeld vragen {#example-navigation}

* &quot;Navigatie instellen vanuit `https://example.com`&quot;
* &quot;Navigatiemenu herstellen&quot;

#### Wat u moet weten {#wtk-navigation}

* Edge Delivery Services-navigatie dwingt een structuur met drie secties af (afgedwongen door `header.js`):
   1. **Merk** (sectie 1): Logo en primaire branding verbinding
   1. **Secties** (sectie 2): Het belangrijkste navigatiemenu met facultatieve dalingen
   1. **Hulpmiddelen** (sectie 3): De verbindingen van het nut (subscribe, login, kar)
* Navigatie-inhoud woont in `nav.md` in de hoofdmap.
* Secties worden gescheiden door markeringen (`---`).
* Vette items (`**Text**`) met geneste lijsten maken vervolgkeuzelijsten.
* Koppelingen in navigatie kunnen als knoppen worden weergegeven vanwege het gedrag van Document Authoring in automatische omloop.
   * Het headerblok bevat code om knopklassen van navigatiekoppelingen te verwijderen.

## Blokontwikkelingsmogelijkheden {#block-development-capabilities}

Deze herinneringen worden gebruikt voor het creëren van en het evolueren van blokken, die ononderbroken waarde voorbij aanvankelijke plaatsverwezenlijking of migratie verstrekken.

### Blokontwikkeling {#block-development}

Gebruik deze herinnering om nieuwe blokken tot stand te brengen of bestaande te wijzigen.

#### Voorbeeld vragen {#example-block-development}

* &quot;Een blok voor getuigenissen maken&quot;
* &quot;Voeg een videoachtergrondvariant toe aan het hoofdblok&quot;

#### Wat u moet weten {#wtk-block-development}

* De agent volgt Content-Driven Development (CDD), een verplicht proces voor alle Edge Delivery Services-ontwikkeling.
   * Er wordt gevraagd naar inhoudsmodellen en de inhoud wordt getest voordat code wordt geschreven.
* De CDD-filosofie is dat de auteur behoefte heeft voordat ontwikkelaars iets nodig hebben.
   * Inhoudsmodellen moeten intuïtief zijn voor auteurs, ook al betekent dit complexere versiecode.
* Eerst wordt testinhoud gemaakt:
   * Directe testmogelijkheden
   * PR-validatiekoppelingen voor PSI-controles
   * Levende documentatie voor auteurs
   * Detectie van randgevallen waarbij code-first-benaderingen ontbreken
* De agent zal naar gelijkaardige blokken in de [ Inzameling van het Blok ](https://www.aem.live/developer/block-collection) zoeken en [ Partij van het Blok ](https://www.aem.live/developer/block-party/) alvorens uit te voeren, om patronen en herbruikbare code te vinden.
* Sla CDD alleen over voor triviale CSS-alleen-tweaks (maar identificeer nog steeds testinhoud voor validatie).

### Inhoud modelleren {#content-modeling}

Met deze prompt kunt u de tabelstructuur ontwerpen waarmee auteurs werken bij het maken van blokinhoud.

#### Voorbeeld vragen {#example-modeling}

* &quot;Ontwerp een inhoudsmodel voor een blok van getuigenissen&quot;
* &quot;Wat is het beste inhoudsmodel voor deze carrousel?&quot;

#### Wat u moet weten {#wtk-modeling}

* Edge Delivery Services heeft vier canonieke modeltypen:
   * **Zelfstandig:** Afzonderlijke visuele/narratieve elementen (held, blockquote)
      * Eén tabel met blokinhoud
   * **Inzameling:** Herhalende semi-gestructureerde inhoud (kaarten, carrousel)
      * Tabel met patroon van herhalende rijen
   * **Configuratie:** API-gedreven of dynamische inhoud waar de config controles tonen (bloglijst, onderzoeksresultaten)
      * Lijst met sleutel-waarde config rijen.
   * **auto-Geblokkeerd:** Complexe structuren die de auteurs als secties/standaardinhoud tot stand brengen, dan getransformeerd worden (lusjes, sluit YouTube in)
* Er geldt een limiet van vier cellen per rij.
   * Groepeer verwante elementen in cellen.
* Voorkeur voor blokvarianten boven configuratiecellen voor opmaakverschillen.
* [ volg de Wet van Postel ](https://en.wikipedia.org/wiki/Robustness_principle): ben flexibel over inputstructuur.
   * Een hoofdblok moet werken of de inhoud zich in één cel bevindt, over twee cellen wordt gesplitst of in afzonderlijke rijen.
* Deze vaardigheid wordt gewoonlijk aangehaald automatisch door inhoud-gedreven Ontwikkeling tijdens blokverwezenlijking.

### Referentieklokken zoeken {#reference-blocks}

Gebruik deze herinnering om bestaande implementaties te zoeken als uitgangspunt te gebruiken.

#### Voorbeeld vragen {#example-reference}

* &quot;Vind blokken gelijkend op een prijsopgave&quot;
* &quot;Welke blokken zijn beschikbaar voor getuigenissen?&quot;
* &quot;Zoekblokpartij voor een tabimplementatie&quot;

#### Wat u moet weten {#wtk-reference}

* De [ Inzameling van het Blok ](https://www.aem.live/developer/block-collection) is Adobe-gehandhaafd en voor beste praktijken, uitstekende inhoud modellering, hoge prestaties, en toegankelijkheid gecontroleerd.
   * Het is beperkt tot blokken die vaak nodig zijn. Begin hier.
* De [ Partij van het Blok ](https://www.aem.live/developer/block-party/) is gemeenschap-gedreven en biedt een bredere verscheidenheid met inbegrip van experimentele benaderingen aan.
   * Het omvat ook secundaire plug-ins, buildtools (webpack, vite, sass) en integratie.
   * Gebruik wanneer de Inzameling van het Blok niet heeft wat u nodig hebt.
* Denk na over alternatieve namen wanneer het zoeken
   * Veelgestelde vragen = accordeon
   * Galerie = carrousel/presentatie
   * Navigation = menu/header
* De Partij van het Blok keert slechts goedgekeurde/gekromde ingangen terug.

### Documentatie zoeken {#searching-documentation}

Gebruik deze prompt om informatie te zoeken over Edge Delivery Services-functies of implementatierichtsnoeren.

#### Voorbeeld vragen {#example-documentation}

* &quot;Hoe kan ik luie ladingen in Edge Delivery Services implementeren?&quot;
* &quot;Zoeken in de documenten naar sectiemetagegevens&quot;

#### Wat u moet weten {#wtk-documentation}

* Het zoekt specifiek de {[ documentatie 0} aem.live (documenten en blogberichten).](https://aem.live)
* Gebruik specifieke trefwoorden (&quot;block decoration&quot;,&quot;sidekick plugin&quot;,&quot;metadata&quot;) in plaats van algemene termen (&quot;aem&quot;,&quot;website&quot;,&quot;how to build&quot;).
* Voor codevoorbeelden en verwijzingsimplementaties, gebruik &quot;vind verwijzingsblokken&quot;in plaats daarvan.
* De tien belangrijkste resultaten die standaard worden geretourneerd.

### Testen {#testing}

Gebruik deze prompt om wijzigingen in de code te valideren voordat u een pull-verzoek opent.

#### Voorbeeld vragen {#example-testing}

* &quot;Test het nieuwe kaartblok&quot;
* &quot;Voer de tests uit voordat ik een PR open&quot;

#### Wat u moet weten {#wtk-testing}

* Het testen volgt een &quot;waarde vs. kosten&quot;filosofie waar u tests creeert en handhaaft wanneer hun waarde kosten overschrijdt.
   * **de tests van de Houder** (eenheidstests) zijn voor logica-zware nut, gegevensverwerking, API integratie. Deze zijn snel, gemakkelijk te handhaven, en vangst regressies in hergebruikte code.
   * **de tests van de Throwaway** (browser tests) zijn voor de transformaties van DOM en visuele bevestiging. Gebruik om implementatie te valideren, schermafbeeldingen vast te leggen voor PR-revisie en vervolgens te verwijderen.
* De wegtests gaan in `test/tmp/` en testen de inhoud in `drafts/tmp/` (beide opgegeven).
* Controleer voordat u een PR opent of:
   * Bestaande tests geslaagd
   * De tests van de eenheid worden geschreven voor nieuwe logica
   * Browservalidatie is voltooid
   * Alle varianten worden getest
   * Responsief gedrag wordt geverifieerd
   * Linkerpassingen

### Foutopsporing {#debugging}

Gebruik deze prompt om problemen met blokken, afbeeldingen, CSS of voorvertoning op te lossen.

#### Voorbeeld vragen {#example-debugging}

* &quot;Foutopsporing waarom afbeeldingen worden weergegeven als ongeveer :error&quot;
* &quot;Het hoofdblok corrigeren en niet renderen&quot;
* &quot;Waarom worden mijn wijzigingen niet in de voorvertoning weergegeven?&quot;

#### Wat u moet weten {#wtk-debugging}

* Vaak voorkomende problemen zijn bekende patronen:
   * **Beelden die &quot;over :error tonen**: Gewoonlijk ontbrekende `createOptimizedPicture` vraag in blok JS, of geroepen vóór DOM het herstructureren
   * **Blokken niet teruggevend**: Het formaat van de bloknaam van de controle in prijsdaling en verifieert dat het blok zowel `.js` als `.css` dossiers in `blocks/` heeft.
   * **CSS die niet** laadt: De dossierwegen van de controle, verifieert CSS dossier bestaat, en controleert het lusje van het Netwerk in browser.
   * **Veranderingen verschijnen niet**: De synchronisatie van de code neemt 3-5 seconden. Vernieuw de tekst op papier (Ctrl+Shift+R).
* De agent controleert systematisch elke laag:
   1. Source-bestanden
   1. Gerenderde uitvoer
   1. Blokcode
   1. Browserconsole
* De agent kan lokale voorvertoningen bij `http://localhost:3000` controleren.
