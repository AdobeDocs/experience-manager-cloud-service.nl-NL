---
title: Client-Side bibliotheken gebruiken op AEM as a Cloud Service
description: AEM biedt clientbibliotheekmappen, waarmee u uw clientcode (clientlibs) in de opslagplaats kunt opslaan, in categorieën kunt indelen en kunt bepalen wanneer en hoe elke categorie code aan de client moet worden verzonden
exl-id: 370db625-09bf-43fb-919d-4699edaac7c8
source-git-commit: ca849bd76e5ac40bc76cf497619a82b238d898fa
workflow-type: tm+mt
source-wordcount: '2566'
ht-degree: 0%

---

# Client-Side bibliotheken gebruiken op AEM as a Cloud Service {#using-client-side-libraries}

Digitale ervaringen zijn sterk afhankelijk van verwerking op de client door complexe JavaScript- en CSS-code. AEM Client-Side Libraries (clientlibs) kunt u deze clientbibliotheken organiseren en centraal opslaan in de opslagplaats. Gekoppeld aan de [front-end constructieproces in het AEM Project archetype;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html) het beheren van uw front-end code voor uw AEM project wordt eenvoudig.

Tot de voordelen van het gebruik van clientlibs in AEM behoren:

* Client-side code wordt net als alle andere toepassingscode en inhoud in de repository opgeslagen
* Clientlibs in AEM kunnen alle CSS en JS in één bestand samenvoegen
* Maak clientlibs toegankelijk via een pad dat toegankelijk is via het [verzender](/help/implementing/dispatcher/disp-overview.md)
* Hiermee kunt u paden herschrijven voor bestanden of afbeeldingen waarnaar wordt verwezen

Clientlibs zijn de ingebouwde oplossing voor het leveren van CSS en JavaScript van AEM.

>[!TIP]
>
>Ontwikkelaars aan de voorzijde die CSS en Javascript voor AEM projecten maken, moeten zich ook vertrouwd maken met de [AEM Project Archetype en zijn geautomatiseerd front-end bouwproces.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html)

## Wat zijn clientbibliotheken? {#what-are-clientlibs}

Voor sites moeten JavaScript en CSS en statische bronnen zoals pictogrammen en weblettertypen op de client worden verwerkt. Een clientlib is AEM mechanisme om (per categorie indien vereist) naar dergelijke middelen te verwijzen en te dienen.

AEM verzamelt de CSS en Javascript van de site in één bestand, op een centrale locatie, om ervoor te zorgen dat slechts één kopie van een bron wordt opgenomen in de HTML-uitvoer. Hierdoor wordt de efficiëntie van de levering gemaximaliseerd en kunnen dergelijke bronnen centraal in de opslagplaats worden onderhouden via proxy, zodat de toegang veilig blijft.

## Front-end ontwikkeling voor AEM as a Cloud Service {#fed-for-aemaacs}

Alle JavaScript-, CSS- en andere front-end elementen moeten in de [ui.frontend module van het Archetype van het Project van de AEM.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html) Dankzij de flexibiliteit van het archetype kunt u uw moderne webgereedschappen gebruiken om deze bronnen te maken en te beheren.

Het archetype kan de bronnen vervolgens compileren in één CSS- en JS-bestand, en deze automatisch insluiten in een `cq:clientLibraryFolder` in de repository.

## Structuur van bibliotheekmap op de client {#clientlib-folders}

Een bibliotheekmap aan de clientzijde is een opslagplaats-knooppunt van het type `cq:ClientLibraryFolder`. De definitie ervan in [CND-notatie](https://jackrabbit.apache.org/node-type-notation.html) is

```text
[cq:ClientLibraryFolder] > sling:Folder
  - dependencies (string) multiple
  - categories (string) multiple
  - embed (string) multiple
  - channels (string) multiple
```

* `cq:ClientLibraryFolder` knooppunten kunnen overal in de `/apps` substructuur van de repository.
* Gebruik de `categories` eigenschap van het knooppunt om de bibliotheekcategorieën te identificeren waartoe het behoort.

Elk `cq:ClientLibraryFolder` wordt gevuld met een set JS- en/of CSS-bestanden, samen met enkele ondersteunende bestanden (zie hieronder). Belangrijke eigenschappen van de `cq:ClientLibraryFolder` zijn als volgt geconfigureerd:

* `allowProxy`: Omdat alle clientlibs onder moeten worden opgeslagen `apps`, biedt deze eigenschap toegang tot clientbibliotheken via proxyservlet. Zie [Een clientbibliotheekmap zoeken en de server Proxy Client Libraries gebruiken](#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet) hieronder.
* `categories`: Identificeert de categorieën waarin de set JS- en/of CSS-bestanden binnen deze set `cq:ClientLibraryFolder` vallen. De `categories` Met een eigenschap met meerdere waarden kan een bibliotheekmap deel uitmaken van meerdere categorieën (zie hieronder voor meer informatie).

Als de map met clientbibliotheken een of meer bronbestanden bevat die tijdens runtime worden samengevoegd tot één JS- en/of CSS-bestand. De naam van het gegenereerde bestand is de knooppuntnaam met een van de `.js` of `.css` bestandsnaamextensie. Het bibliotheekknooppunt genaamd `cq.jquery` resulteert in het gegenereerde bestand met de naam `cq.jquery.js` of `cq.jquery.css`.

Clientbibliotheekmappen bevatten de volgende items:

* JS- en/of CSS-bronbestanden
* Statische bronnen die CSS-stijlen ondersteunen, zoals pictogrammen, weblettertypen, enz.
* Eén `js.txt` bestand en/of één `css.txt` bestand met de bronbestanden die moeten worden samengevoegd in de gegenereerde JS- en/of CSS-bestanden

![Clientlib-architectuur](assets/clientlib-architecture.drawio.png)

## Clientzijbibliotheekmappen maken {#creating-clientlib-folders}

Clientbibliotheken moeten zich onder `/apps`. Dit is om code beter van inhoud en configuratie te isoleren.

Voor de clientbibliotheken onder `/apps` om toegankelijk te zijn, wordt een volmachtsserver gebruikt. ACLs wordt nog afgedwongen op de omslag van de cliëntbibliotheek, maar servlet laat voor de inhoud toe om via worden gelezen `/etc.clientlibs/` als de `allowProxy` eigenschap is ingesteld op `true`.

1. CRXDE Lite openen in een webbrowser (`https://<host>:<port>/crx/de`).
1. Selecteer `/apps` map en klik op **Maken > knooppunt maken**.
1. Voer een naam in voor de bibliotheekmap en in het dialoogvenster **Type** lijst selecteren `cq:ClientLibraryFolder`. Klikken **OK** en klik vervolgens op **Alles opslaan**.
1. Als u de categorie of categorieën wilt opgeven waartoe de bibliotheek behoort, selecteert u de optie `cq:ClientLibraryFolder` knoop, voeg het volgende bezit toe, en klik dan **Alles opslaan**:
   * Naam: `categories`
   * Type: String
   * Waarde: De categorienaam
   * Meerdere: Geselecteerd
1. Om de clientbibliotheken toegankelijk te maken via proxy `/etc.clientlibs`, selecteert u de `cq:ClientLibraryFolder` knoop, voeg het volgende bezit toe, en klik dan **Alles opslaan**:
   * Naam: `allowProxy`
   * Type: Boolean
   * Waarde: `true`
1. Als u statische bronnen moet beheren, maakt u een submap met de naam `resources` onder de clientbibliotheekmap.
   * Als u statische bronnen onder de map opslaat `resources`, kunnen er niet naar worden verwezen in een publicatie-instantie.
1. Bronbestanden toevoegen aan de bibliotheekmap.
   * Dit wordt typisch gedaan door het front-end bouwstijlproces van [AEM Projectarchetype.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html)
   * U kunt bronbestanden desgewenst in submappen ordenen.
1. Selecteer de clientbibliotheekmap en klik op **Maken > Bestand maken**.
1. Typ in het vak Bestandsnaam een van de volgende bestandsnamen en klik op OK:
   * **`js.txt`:** Gebruik deze bestandsnaam om een JavaScript-bestand te genereren.
   * **`css.txt`:** Gebruik deze bestandsnaam om een trapsgewijs opmaakmodel te genereren.
1. Open het bestand en typ de volgende tekst om de hoofdmap van het pad van de bronbestanden te identificeren:
   * `#base=*[root]*`
   * Vervangen `[root]` met het pad naar de map die de bronbestanden bevat, relatief ten opzichte van het TXT-bestand. Gebruik bijvoorbeeld de volgende tekst wanneer de bronbestanden zich in dezelfde map bevinden als het TXT-bestand:
      * `#base=.`
   * Met de volgende code wordt de hoofdmap ingesteld als de map mobile onder de `cq:ClientLibraryFolder` knooppunt:
      * `#base=mobile`
1. Op de onderstaande regels `#base=[root]`Typ de paden van de bronbestanden ten opzichte van het hoofdbestand. Plaats elke bestandsnaam op een aparte regel.
1. Klikken **Alles opslaan**.

## Client-Side bibliotheken bedienen {#serving-clientlibs}

Zodra de clientbibliotheekmap [zo nodig geconfigureerd,](#creating-clientlib-folders) uw clientlibs kan via proxy worden aangevraagd. Als voorbeeld:

* U hebt een clientlib in `/apps/myproject/clientlibs/foo`
* U hebt een statische afbeelding in `/apps/myprojects/clientlibs/foo/resources/icon.png`

De `allowProxy` kunt u het volgende aanvragen:

* Clilib via j`/etc.clientlibs/myprojects/clientlibs/foo.js`
* De statische afbeelding via `/etc.clientlibs/myprojects/clientlibs/foo/resources/icon.png`

### Clientbibliotheken laden via HTML {#loading-via-htl}

Zodra uw clientbibliotheken zijn opgeslagen en beheerd in hun clientbibliotheekmap, kunnen ze toegang krijgen via HTML.

Clientbibliotheken worden geladen via een helpersjabloon die door AEM wordt geleverd en die toegankelijk is via `data-sly-use`. De helpermalplaatjes zijn beschikbaar in dit dossier, dat door kan worden geroepen `data-sly-call`.

Elke hulpsjabloon verwacht een `categories` voor het verwijzen naar de gewenste clientbibliotheken. Deze optie kan ofwel een array van tekenreekswaarden zijn, ofwel een tekenreeks met een lijst met door komma&#39;s gescheiden waarden.

[Zie de HTML-documentatie](https://experienceleague.adobe.com/docs/experience-manager-htl/using/getting-started/getting-started.html#loading-client-libraries) voor meer informatie over het laden van clientlibs via HTL.

<!--
### Setting Cache Timestamps {#setting-cache-timestamps}

This is possible. Still need detail.
-->

## Clientbibliotheken op auteur versus publiceren {#clientlibs-author-publish}

De meeste clientlibs zijn vereist voor de AEM-publicatie-instantie. Dat wil zeggen dat de meeste clientlibs-doeleinden de eindgebruikerservaring van de inhoud moeten opleveren. Voor clientlibs bij publicatie-instanties [front-end constructiegereedschappen](#fed-for-aemaacs) kan worden gebruikt en geïmplementeerd via [clientbibliotheekmappen zoals hierboven beschreven.](#creating-clientlib-folders)

Er zijn echter momenten waarop clientbibliotheken nodig kunnen zijn om de ontwerpervaring aan te passen. Als u bijvoorbeeld een dialoogvenster aanpast, moet u mogelijk kleine CSS- of JS-bits implementeren in de AEM ontwerpinstantie.

### Clientbibliotheken beheren op auteur {#clientlibs-on-author}

Als u clientbibliotheken op de auteur moet gebruiken, kunt u onder `/apps` dezelfde methoden gebruiken als voor publiceren, maar deze rechtstreeks schrijven onder `/apps/.../clientlibs/foo` in plaats van een volledig project te maken om het te beheren.

U kunt dan &quot;haken&quot;in auteursJS door uw cliëntbibliotheken aan een uit-van-de-doos categorie van de cliëntbibliotheek toe te voegen.

## Foutopsporingsgereedschappen {#debugging-tools}

AEM beschikt over verschillende gereedschappen voor foutopsporing en het testen van clientbibliotheekmappen.

### Clientbibliotheken detecteren {#discover-client-libraries}

De `/libs/cq/granite/components/dumplibs/dumplibs` genereert een pagina met informatie over alle clientbibliotheekmappen op het systeem. De `/libs/granite/ui/content/dumplibs` knooppunt heeft de component als een brontype. Als u de pagina wilt openen, gebruikt u de volgende URL (waarbij u de host en poort naar wens wijzigt):

`https://<host>:<port>/libs/granite/ui/content/dumplibs.test.html`

Tot de gegevens behoren het bibliotheekpad en -type (CSS of JS) en de waarden van de bibliotheekkenmerken, zoals categorieën en afhankelijkheden. In de volgende tabellen op de pagina worden de bibliotheken in elke categorie en elk kanaal weergegeven.

### Zie Gegenereerde uitvoer {#see-generated-output}

De `dumplibs` component omvat een testselecteur die de broncode toont die voor wordt geproduceerd `ui:includeClientLib` -tags. De pagina bevat code voor verschillende combinaties van js-, css- en themakenmerken.

1. Gebruik een van de volgende methoden om de pagina Uitvoer testen te openen:
   * Van de `dumplibs.html` pagina, klikt u op de koppeling in het dialoogvenster **Klik hier voor het testen van de uitvoer** tekst.
   * Open de volgende URL in uw webbrowser (gebruik indien nodig een andere host en poort):
      * `http://<host>:<port>/libs/granite/ui/content/dumplibs.html`
   * Op de standaardpagina wordt uitvoer weergegeven voor tags zonder waarde voor het categoriekenmerk.
1. Als u de uitvoer voor een categorie wilt zien, typt u de waarde van de clientbibliotheek `categories` eigenschap en klikken **Query verzenden**.

## Extra functies voor clientbibliotheekmappen {#additional-features}

Er zijn een aantal andere functies die in AEM door clientbibliotheekmappen worden ondersteund. Deze zijn echter niet vereist voor AEM as a Cloud Service en daarom wordt het gebruik ervan afgeraden. Ze worden hier ter volledigheid vermeld.

>[!WARNING]
>
>Deze extra functies van clientbibliotheekmappen zijn niet vereist voor AEM as a Cloud Service en daarom wordt het gebruik ervan afgeraden. Ze worden hier ter volledigheid vermeld.

### Adobe Granite HTML Library Manager {#html-library-manager}

Extra instellingen voor de clientbibliotheek kunt u beheren via de **Adobe Granite HTML Library Manager** deelvenster van de systeemconsole op `https://<host>:<port>/system/console/configMgr`).

### Extra mapeigenschappen {#additional-folder-properties}

De extra omslageigenschappen omvatten staan controle van gebiedsdelen en bedden toe, maar zijn over het algemeen niet meer nodig en hun gebruik wordt ontmoedigd:

* `dependencies`: Dit is een lijst van andere categorieën van de cliëntbibliotheek waarvan deze bibliotheekomslag afhangt. Bijvoorbeeld, gegeven twee `cq:ClientLibraryFolder` knooppunten `F` en `G`, als een bestand zich in `F` vereist een ander bestand in `G` ten minste een van de `categories` van `G` behoort tot de `dependencies` van `F`.
* `embed`: Wordt gebruikt om code uit andere bibliotheken in te sluiten. If node `F` insluiten, knooppunten `G` en `H`, zal de resulterende HTML een aaneenschakeling van inhoud van knopen zijn `G` en `H`.

### Koppeling naar afhankelijke instellingen {#linking-to-dependencies}

Wanneer de code in de map met clientbibliotheken verwijst naar andere bibliotheken, identificeert u de andere bibliotheken als afhankelijkheden. De `ui:includeClientLib` -tag die verwijst naar de map met de clientbibliotheek, bevat de HTML-code een koppeling naar het gegenereerde bibliotheekbestand en de afhankelijkheden.

De afhankelijkheden moeten een andere `cq:ClientLibraryFolder`. Om gebiedsdelen te identificeren, voeg een bezit aan uw toe `cq:ClientLibraryFolder` knooppunt met de volgende kenmerken:

* **Naam:** afhankelijkheden
* **Type:** String[]
* **Waarden:** De waarde van het eigenschap category van het knooppunt cq:ClientLibraryFolder waarvan de huidige bibliotheekmap afhankelijk is.

De `/etc/clientlibs/myclientlibs/publicmain` is afhankelijk van de `cq.jquery` bibliotheek. De pagina die verwijst naar de hoofdclientbibliotheek genereert een HTML die de volgende code bevat:

```xml
<script src="/etc/clientlibs/foundation/cq.jquery.js" type="text/javascript">
<script src="/etc/clientlibs/mylibs/publicmain.js" type="text/javascript">
```

### Code van andere bibliotheken insluiten {#embedding-code-from-other-libraries}

U kunt code van een clientbibliotheek insluiten in een andere clientbibliotheek. Tijdens de runtime bevatten de gegenereerde JS- en CSS-bestanden van de insluitingsbibliotheek de code van de ingesloten bibliotheek.

Het insluiten van code is handig voor het verschaffen van toegang tot bibliotheken die zijn opgeslagen in beveiligde gebieden van de opslagplaats.

#### Toepassingsspecifieke clientbibliotheekmappen {#app-specific-client-library-folders}

U kunt het beste alle toepassingsgerelateerde bestanden in hun toepassingsmap onder /apps opslaan. Het wordt ook aanbevolen bezoekers van websites toegang tot de map /apps te weigeren. Om aan beide beste praktijken te voldoen, creeer een omslag van de cliëntbibliotheek onder de /etc omslag die de cliëntbibliotheek inbedt die onder /apps is.

Gebruik de eigenschap Categorieën om de clientbibliotheekmap te identificeren die u wilt insluiten. Als u de bibliotheek wilt insluiten, voegt u een eigenschap toe aan het insluiten `cq:ClientLibraryFolder` node, met de volgende eigenschapkenmerken:

* **Naam:** insluiten
* **Type:** String[]
* **Waarde:** De waarde van de eigenschap Categorieën van de `cq:ClientLibraryFolder` in te sluiten knooppunt.

#### Insluiten gebruiken om verzoeken te minimaliseren {#using-embedding-to-minimize-requests}

In sommige gevallen zult u zien dat de uiteindelijke HTML die door uw publicatieexemplaar voor een standaardpagina wordt gegenereerd, een relatief groot aantal items bevat `<script>` elementen.

In dergelijke gevallen kan het handig zijn om alle vereiste code van de clientbibliotheek te combineren in één bestand, zodat het aantal heen en weer aanvragen bij het laden van de pagina wordt verminderd. U kunt dit doen `embed` de vereiste bibliotheken in uw toepassingsspecifieke clientbibliotheek met de eigenschap embed van het dialoogvenster `cq:ClientLibraryFolder` knooppunt.

#### Paden in CSS-bestanden {#paths-in-css-files}

Wanneer u CSS-bestanden insluit, gebruikt de gegenereerde CSS-code paden naar bronnen die relatief zijn ten opzichte van de insluitingsbibliotheek. Bijvoorbeeld de openbaar toegankelijke bibliotheek `/etc/client/libraries/myclientlibs/publicmain` sluit het `/apps/myapp/clientlib` clientbibliotheek:

De `main.css` bestand bevat de volgende stijl:

```javascript
body {
  padding: 0;
  margin: 0;
  background: url(images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

Het CSS-bestand dat het `publicmain` node genereert bevat de volgende stijl met behulp van de URL van de oorspronkelijke afbeelding:

```javascript
body {
  padding: 0;
  margin: 0;
  background: url(../../../apps/myapp/clientlib/styles/images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

#### Zie Ingesloten bestanden in HTML-uitvoer {#see-embedded-files}

Als u de oorsprong van ingesloten code wilt traceren of wilt controleren of ingesloten clientbibliotheken de verwachte resultaten opleveren, kunt u de namen zien van de bestanden die bij uitvoering worden ingesloten. Als u de bestandsnamen wilt weergeven, voegt u de opdracht `debugClientLibs=true` aan de URL van uw webpagina. De gegenereerde bibliotheek bevat `@import` in plaats van de ingesloten code.

In het voorbeeld in het vorige [Code van andere bibliotheken insluiten](#embedding-code-from-other-libraries) de `/etc/client/libraries/myclientlibs/publicmain` clientbibliotheekmap sluit de `/apps/myapp/clientlib` clientbibliotheekmap. Als u de parameter aan de webpagina toevoegt, wordt de volgende koppeling in de broncode van de webpagina gemaakt:

```xml
<link rel="stylesheet" href="/etc/clientlibs/mycientlibs/publicmain.css">
```

Het openen van de `publicmain.css` het dossier openbaart de volgende code:

```javascript
@import url("/apps/myapp/clientlib/styles/main.css");
```

1. Voeg in het adresvak van uw webbrowser de volgende tekst toe aan de URL van uw HTML:
   * `?debugClientLibs=true`
1. Bekijk de paginabron wanneer de pagina wordt geladen.
1. Klik op de koppeling die wordt opgegeven als de href voor het koppelingselement om het bestand te openen en de broncode weer te geven.

### Voorprocessors gebruiken {#using-preprocessors}

AEM maakt het mogelijk om af te spelen op preprocessoren en schepen met ondersteuning voor [YUI-compressor](https://github.com/yui/yuicompressor#yui-compressor---the-yahoo-javascript-and-css-compressor) voor CSS en JavaScript en [Google Closure Compiler (GCC)](https://developers.google.com/closure/compiler/) voor JavaScript met YUI ingesteld als AEM standaardvoorprocessor.

Met de aanpasbare voorprocessoren kunt u flexibel gebruik maken, waaronder:

* ScriptProcessors definiëren die scriptbronnen kunnen verwerken
* Processors kunnen worden geconfigureerd met opties
* Processors kunnen worden gebruikt voor minificatie, maar ook voor niet-minieme gevallen
* Clientlib kan bepalen welke processor moet worden gebruikt

>[!NOTE]
>
>AEM gebruikt standaard de YUI-compressor. Zie de [GitHub-documentatie voor YUI-compressor](https://github.com/yui/yuicompressor/issues) voor een lijst van bekende problemen. Het schakelen naar GCC-compressor voor bepaalde clientlibs kan een aantal problemen oplossen die tijdens het gebruik van YUI zijn waargenomen.

>[!CAUTION]
>
>Plaats geen geminiateerde bibliotheek in een clientbibliotheek. Geef in plaats daarvan de onbewerkte bibliotheek op en gebruik de opties van de voorprocessoren als miniaturen vereist zijn.

#### Gebruik {#usage}

U kunt kiezen om de configuratie preprocessoren per clientbibliotheek of systeembreed te configureren.

* Eigenschappen voor meerdere waarden toevoegen `cssProcessor` en `jsProcessor` op het clientbibliotheekknooppunt
* Of definieer de standaardconfiguratie van het systeem via de **HTML Library Manager** OSGi-configuratie

Een preprocessorconfiguratie op de clientlib knoop neemt belangrijkheid over de configuratie OSGI.

#### Indeling en voorbeelden {#format-and-examples}

##### Format {#format}

```javascript
config:= mode ":" processorName options*;
mode:= "default" | "min";
processorName := "none" | <name>;
options := ";" option;
option := name "=" value;
```

##### YUI-compressor voor CSS-miniatuur en GCC voor JS {#yui-compressor-for-css-minification-and-gcc-for-js}

```javascript
cssProcessor: ["default:none", "min:yui"]
jsProcessor: ["default:none", "min:gcc;compilationLevel=advanced"]
```

##### Typescript aan preprocess en dan GCC om te kleven en te verduisteren {#typescript-to-preprocess-and-then-gcc-to-minify-and-obfuscate}

```javascript
jsProcessor: [
   "default:typescript",
   "min:typescript",
   "min:gcc;obfuscate=true"
]
```

##### Aanvullende GCC-opties {#additional-gcc-options}

```javascript
failOnWarning (defaults to "false")
languageIn (defaults to "ECMASCRIPT5")
languageOut (defaults to "ECMASCRIPT5")
compilationLevel (defaults to "simple") (can be "whitespace", "simple", "advanced")
```

Voor meer informatie over GCC-opties raadpleegt u de [GCC-documentatie](https://developers.google.com/closure/compiler/docs/compilation_levels).

#### Systeemstandaardminiatuur instellen {#set-system-default-minifier}

YUI wordt geplaatst als standaardminifier in AEM. Voer de volgende stappen uit om dit te wijzigen in GCC.

1. Ga naar Apache Felix Config Manager op (`http://<host>:<portY/system/console/configMgr`)
1. Zoeken en bewerken **Adobe Granite HTML Library Manager**.
1. De optie **Minieren** (als deze optie nog niet is ingeschakeld).
1. De waarde instellen **Standaardconfiguratie JS-processor** tot `min:gcc`.
   * Opties kunnen worden doorgegeven als deze bijvoorbeeld met een puntkomma worden gescheiden. `min:gcc;obfuscate=true`.
1. Klikken **Opslaan** om de wijzigingen op te slaan.
