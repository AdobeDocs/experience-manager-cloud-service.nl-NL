---
title: Client-Side Libraries gebruiken op AEM as a Cloud Service
description: AEM biedt clientbibliotheekmappen, waarmee u uw clientcode (clientlibs) in de opslagplaats kunt opslaan, in categorieën kunt indelen en kunt bepalen wanneer en hoe elke categorie code aan de client moet worden verzonden
exl-id: 370db625-09bf-43fb-919d-4699edaac7c8
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2428'
ht-degree: 0%

---


# Client-Side Libraries gebruiken op AEM as a Cloud Service {#using-client-side-libraries}

Digitale ervaringen zijn sterk afhankelijk van verwerking op de client door complexe JavaScript- en CSS-code. Met AEM Client-Side Libraries (clientlibs) kunt u deze clientbibliotheken organiseren en centraal opslaan in de opslagplaats. Gekoppeld aan [&#x200B; front-end bouwt proces in het archetype van het Project van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html?lang=nl-NL), wordt het beheren van uw front-end code voor uw project van AEM eenvoudig.

Tot de voordelen van het gebruik van clientlibs in AEM behoren:

* Client-side code wordt net als alle andere toepassingscode en inhoud in de repository opgeslagen
* Clientlibs in AEM kunnen alle CSS en JS in één bestand samenvoegen
* Maak clientlibs via een weg bloot die door [&#x200B; verzender &#x200B;](/help/implementing/dispatcher/disp-overview.md) toegankelijk is
* Hiermee kunt u paden herschrijven voor bestanden of afbeeldingen waarnaar wordt verwezen

Clientlibs zijn de ingebouwde oplossing voor het leveren van CSS en JavaScript vanuit AEM.

>[!TIP]
>
>De ontwikkelaars van het front-end die CSS en JavaScript voor de projecten van AEM creëren zouden zich met het [&#x200B; Archetype van het Project van AEM en zijn geautomatiseerd front-end bouwstijlproces &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html?lang=nl-NL) ook moeten vertrouwd maken.

## Wat zijn clientbibliotheken? {#what-are-clientlibs}

Voor sites moeten JavaScript- en CSS-bronnen en statische bronnen, zoals pictogrammen en weblettertypen, op de client worden verwerkt. Een client is een AEM-mechanisme dat naar deze bronnen verwijst (zo nodig per categorie) en deze middelen aanbiedt.

AEM verzamelt de CSS en JavaScript van de site in één bestand, op een centrale locatie, om ervoor te zorgen dat er maar één kopie van een bron wordt opgenomen in de HTML-uitvoer. Hierdoor wordt de efficiëntie van de levering gemaximaliseerd en kunnen dergelijke bronnen centraal in de opslagplaats worden onderhouden via proxy, zodat de toegang veilig blijft.

## Front-end ontwikkeling voor AEM as a Cloud Service {#fed-for-aemaacs}

Alle JavaScript, CSS, en andere front-end activa zouden in de {[&#x200B; moeten worden gehandhaafd module 0} ui.frontend van het Archetype van het Project van AEM. &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html?lang=nl-NL) Dankzij de flexibiliteit van het archetype kunt u uw moderne webgereedschappen gebruiken om deze bronnen te maken en te beheren.

Het archetype kan de bronnen vervolgens compileren in één CSS- en JS-bestand en deze automatisch insluiten in een `cq:clientLibraryFolder` in de opslagplaats.

## Structuur van bibliotheekmap op de client {#clientlib-folders}

Een bibliotheekmap op de client is een opslagplaats van het type `cq:ClientLibraryFolder` . Zijn definitie in [&#x200B; aantekening CND &#x200B;](https://jackrabbit.apache.org/node-type-notation.html) is

```text
[cq:ClientLibraryFolder] > sling:Folder
  - dependencies (string) multiple
  - categories (string) multiple
  - embed (string) multiple
  - channels (string) multiple
```

* `cq:ClientLibraryFolder` -knooppunten kunnen overal in de `/apps` -substructuur van de opslagplaats worden geplaatst.
* Gebruik de eigenschap `categories` van het knooppunt om de bibliotheekcategorieën te identificeren waartoe het behoort.

Elke `cq:ClientLibraryFolder` wordt gevuld met een set JS- en/of CSS-bestanden, samen met enkele ondersteunende bestanden (zie hieronder). Belangrijke eigenschappen van de `cq:ClientLibraryFolder` zijn als volgt geconfigureerd:

* `allowProxy`: Aangezien alle clientlibs moeten worden opgeslagen onder `apps` , biedt deze eigenschap toegang tot clientbibliotheken via proxyservlet. Zie de sectie [&#x200B; van een Omslag van de Bibliotheek van de Cliënt van de Cliënt van de Volmacht hieronder het lokaliseren en het Gebruiken van Servlet van de Bibliotheken van de Cliënt van de Volmacht &#x200B;](#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet).
* `categories`: identificeert de categorieën waarin de set JS- en/of CSS-bestanden in deze `cq:ClientLibraryFolder` valt. Met de eigenschap `categories` , die meerdere waarden heeft, kan een bibliotheekmap deel uitmaken van meerdere categorieën (zie hieronder voor meer informatie over de bruikbaarheid).

Als de map met clientbibliotheken een of meer bronbestanden bevat die tijdens runtime worden samengevoegd tot één JS- en/of CSS-bestand. De naam van het gegenereerde bestand is de knooppuntnaam met de bestandsnaamextensie `.js` of `.css` . Het bibliotheekknooppunt `cq.jquery` resulteert bijvoorbeeld in het gegenereerde bestand met de naam `cq.jquery.js` of `cq.jquery.css` .

Clientbibliotheekmappen bevatten de volgende items:

* JS- en/of CSS-bronbestanden
* Statische bronnen die CSS-stijlen ondersteunen, zoals pictogrammen, weblettertypen, enzovoort.
* Eén `js.txt` -bestand en/of één `css.txt` -bestand met de bronbestanden die moeten worden samengevoegd in de gegenereerde JS- en/of CSS-bestanden

![&#x200B; Clientlib architectuur &#x200B;](assets/clientlib-architecture.drawio.png)

## Clientzijbibliotheekmappen maken {#creating-clientlib-folders}

Clientbibliotheken moeten zich onder `/apps` bevinden. Deze regel is nodig om code beter te isoleren van inhoud en configuratie.

De clientbibliotheken onder `/apps` zijn alleen toegankelijk als er een proxyserver wordt gebruikt. ACLs wordt nog afgedwongen op de omslag van de cliëntbibliotheek, maar servlet staat voor de inhoud toe om via `/etc.clientlibs/` worden gelezen als het `allowProxy` bezit aan `true` wordt geplaatst.

1. Open CRXDE Lite in Webbrowser (`https://<host>:<port>/crx/de`).
1. Selecteer de `/apps` omslag en klik **creëren > Node** creëren.
1. Ga een naam voor de bibliotheekomslag in, en in de **Uitgezochte lijst van het Type** `cq:ClientLibraryFolder`. Klik **O.K.** en klik dan **sparen allen**.
1. Om de categorie of de categorieën te specificeren dat de bibliotheek tot behoort, selecteer de `cq:ClientLibraryFolder` knoop, voeg het volgende bezit toe, en klik dan **sparen allen**:
   * Naam: `categories`
   * Type: String
   * Waarde: de categorienaam
   * Meerdere: geselecteerd
1. Opdat de cliëntbibliotheken via volmacht onder `/etc.clientlibs` toegankelijk zijn, selecteer de `cq:ClientLibraryFolder` knoop, voeg het volgende bezit toe, en klik dan **sparen allen**:
   * Naam: `allowProxy`
   * Type: Boolean
   * Waarde: `true`
1. Als u statische bronnen moet beheren, maakt u een submap met de naam `resources` onder de clientbibliotheekmap.
   * Als u statische bronnen ergens anders opslaat dan in de map `resources` , kan er niet naar worden verwezen op een publicatie-instantie.
1. Bronbestanden toevoegen aan de bibliotheekmap.
   * Dit wordt typisch gedaan door front-end bouwt proces van het [&#x200B; Archetype van het Project van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html?lang=nl-NL).
   * U kunt bronbestanden desgewenst in submappen ordenen.
1. Selecteer de omslag van de cliëntbibliotheek en klik **creëren > dossier** creëren.
1. Typ in het vak Bestandsnaam een van de volgende bestandsnamen en klik op OK:
   * **`js.txt`:** gebruik deze bestandsnaam om een JavaScript-bestand te genereren.
   * **`css.txt`:** gebruik deze bestandsnaam om een trapsgewijs opmaakmodel te genereren.
1. Open het bestand en typ de volgende tekst om de hoofdmap van het pad van de bronbestanden te identificeren:
   * `#base=*[root]*`
   * Vervang `[root]` door het pad naar de map met de bronbestanden, relatief ten opzichte van het TXT-bestand. Gebruik bijvoorbeeld de volgende tekst wanneer de bronbestanden zich in dezelfde map bevinden als het TXT-bestand:
      * `#base=.`
   * Met de volgende code wordt de hoofdmap ingesteld als de map met de naam mobile onder het knooppunt `cq:ClientLibraryFolder` :
      * `#base=mobile`
1. Typ op de onderstaande regels `#base=[root]` de paden van de bronbestanden ten opzichte van het hoofdbestand. Plaats elke bestandsnaam op een aparte regel.
1. Klik **sparen allen**.

## Client-Side bibliotheken bedienen {#serving-clientlibs}

Zodra uw omslag van de cliëntbibliotheek [&#x200B; zoals vereist &#x200B;](#creating-clientlib-folders) wordt gevormd, kunnen uw clientlibs via volmacht worden gevraagd. Als voorbeeld:

* U hebt een clientlib in `/apps/myproject/clientlibs/foo`
* U hebt een statische afbeelding in `/apps/myprojects/clientlibs/foo/resources/icon.png`

Met de eigenschap `allowProxy` kunt u het volgende aanvragen:

* Clientlib via `/etc.clientlibs/myprojects/clientlibs/foo.js`
* De statische afbeelding via `/etc.clientlibs/myprojects/clientlibs/foo/resources/icon.png`

### Clientbibliotheken laden via HTML {#loading-via-htl}

Zodra uw clientbibliotheken zijn opgeslagen en beheerd in hun clientbibliotheekmap, kunnen ze toegang krijgen via HTML.

Clientbibliotheken worden geladen via een door AEM verschafte helpersjabloon, die toegankelijk is via `data-sly-use` . De hulpmalplaatjes zijn beschikbaar in dit dossier, dat door `data-sly-call` kan worden geroepen.

Elke hulpsjabloon verwacht een `categories` optie voor het verwijzen naar de gewenste clientbibliotheken. Deze optie kan ofwel een array van tekenreekswaarden zijn, ofwel een tekenreeks met een lijst met door komma&#39;s gescheiden waarden.

[&#x200B; zie de documentatie HTML &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-htl/using/getting-started/getting-started.html?lang=nl-NL#loading-client-libraries) voor meer details bij het laden van clientlibs via HTML.

<!--
### Setting Cache Timestamps {#setting-cache-timestamps}

This is possible. Still need detail.
-->

## Clientbibliotheken op auteur versus publiceren {#clientlibs-author-publish}

De meeste clientlibs zijn vereist voor het AEM-publicatieexemplaar. Dat wil zeggen dat de meeste clientlibs-doeleinden de eindgebruikerservaring van de inhoud moeten opleveren. Voor clientlibs op publiceer instanties, [&#x200B; front-end bouwt hulpmiddelen &#x200B;](#fed-for-aemaacs) kan worden gebruikt en via [&#x200B; omslagen van de cliëntbibliotheek zoals hierboven beschreven &#x200B;](#creating-clientlib-folders) worden opgesteld.

Er zijn echter momenten waarop clientbibliotheken nodig kunnen zijn om de ontwerpervaring aan te passen. Als u bijvoorbeeld een dialoogvenster aanpast, moet u mogelijk kleine bits CSS of JS naar de AEM-ontwerpinstantie implementeren.

### Clientbibliotheken beheren op auteur {#clientlibs-on-author}

Als u clientbibliotheken op de auteur wilt gebruiken, kunt u onder `/apps` uw clientbibliotheken maken met dezelfde methoden als voor publiceren, maar deze rechtstreeks onder `/apps/.../clientlibs/foo` schrijven in plaats van een geheel project te maken om het te beheren.

U kunt dan &quot;haken&quot;in auteursJS door uw cliëntbibliotheken aan een uit-van-de-doos categorie van de cliëntbibliotheek toe te voegen.

## Foutopsporingsgereedschappen {#debugging-tools}

AEM biedt verschillende gereedschappen voor foutopsporing en het testen van clientbibliotheekmappen.

### Clientbibliotheken detecteren {#discover-client-libraries}

De component `/libs/cq/granite/components/dumplibs/dumplibs` genereert een pagina met informatie over alle clientbibliotheekmappen op het systeem. Het knooppunt `/libs/granite/ui/content/dumplibs` heeft de component als een brontype. Als u de pagina wilt openen, gebruikt u de volgende URL (waarbij u de host en poort naar wens wijzigt):

`https://<host>:<port>/libs/granite/ui/content/dumplibs.test.html`

Tot de gegevens behoren het bibliotheekpad en -type (CSS of JS) en de waarden van de bibliotheekkenmerken, zoals categorieën en afhankelijkheden. In de volgende tabellen op de pagina worden de bibliotheken in elke categorie en elk kanaal weergegeven.

### Zie Gegenereerde uitvoer {#see-generated-output}

De component `dumplibs` bevat een testkiezer die de broncode weergeeft die voor `ui:includeClientLib` -tags wordt gegenereerd. De pagina bevat code voor verschillende combinaties van js-, css- en themakenmerken.

1. Gebruik een van de volgende methoden om de pagina Uitvoer testen te openen:
   * Van de `dumplibs.html` pagina, klik de verbinding in **klik hier voor output het testen** tekst.
   * Open de volgende URL in uw webbrowser (gebruik indien nodig een andere host en poort):
      * `http://<host>:<port>/libs/granite/ui/content/dumplibs.html`
   * Op de standaardpagina wordt uitvoer weergegeven voor tags zonder waarde voor het categoriekenmerk.
1. Om de output voor een categorie te zien, typ de waarde van het bezit van de cliëntbibliotheek `categories` en klik **voorleggen Vraag**.

## Extra functies voor clientbibliotheekmappen {#additional-features}

Er zijn verschillende andere functies die door clientbibliotheekmappen in AEM worden ondersteund. Deze zijn echter niet verplicht voor AEM as a Cloud Service en daarom wordt het gebruik ervan afgeraden. Zij worden hier vermeld voor volledigheid.

>[!WARNING]
>
>Deze extra functies van clientbibliotheekmappen zijn niet vereist op AEM as a Cloud Service en daarom wordt het gebruik ervan afgeraden. Zij worden hier vermeld voor volledigheid.

### Adobe Granite HTML Library Manager {#html-library-manager}

De extra montages van de cliëntbibliotheek kunnen door **Adobe Granite HTML van de Bibliotheek van de Manager** paneel van de Console van het Systeem bij `https://<host>:<port>/system/console/configMgr` worden gecontroleerd).

### Extra mapeigenschappen {#additional-folder-properties}

De extra omslageigenschappen omvatten staan controle van gebiedsdelen en bedden toe, maar zijn over het algemeen niet meer nodig en hun gebruik wordt ontmoedigd:

* `dependencies`: Dit is een lijst met andere categorieën in de clientbibliotheek waarvan deze bibliotheekmap afhankelijk is. Als een bestand in `cq:ClientLibraryFolder` bijvoorbeeld een ander bestand in `F` nodig heeft om correct te werken, moet op basis van twee `G` nodes `F` en `G` ten minste een van de `categories` of `G` -knooppunten deel uitmaken van de `dependencies` of `F` -lus.
* `embed`: wordt gebruikt om code uit andere bibliotheken in te sluiten. Als node `F` knooppunten `G` en `H` insluit, is de resulterende HTML een samenvoeging van inhoud van knooppunten `G` en `H` .

### Koppeling naar afhankelijke instellingen {#linking-to-dependencies}

Wanneer de code in de map met clientbibliotheken verwijst naar andere bibliotheken, identificeert u de andere bibliotheken als afhankelijkheden. De tag `ui:includeClientLib` die verwijst naar de map van de clientbibliotheek zorgt ervoor dat de HTML-code een koppeling bevat naar het gegenereerde bibliotheekbestand en de afhankelijkheden.

De afhankelijkheden moeten een andere `cq:ClientLibraryFolder` zijn. Om gebiedsdelen te identificeren, voeg een bezit aan uw `cq:ClientLibraryFolder` knoop met de volgende attributen toe:

* **Naam:** gebiedsdelen
* **Type:** Koord []
* **Waarden:** de waarde van het categoriereigenschap van de cq :ClientLibraryFolder knoop die de huidige bibliotheekomslag van afhangt.

De `/etc/clientlibs/myclientlibs/publicmain` is bijvoorbeeld afhankelijk van de `cq.jquery` -bibliotheek. De pagina die verwijst naar de hoofdclientbibliotheek genereert een HTML met de volgende code:

```xml
<script src="/etc/clientlibs/foundation/cq.jquery.js" type="text/javascript">
<script src="/etc/clientlibs/mylibs/publicmain.js" type="text/javascript">
```

### Code van andere bibliotheken insluiten {#embedding-code-from-other-libraries}

U kunt code van een clientbibliotheek insluiten in een andere clientbibliotheek. Tijdens de runtime bevatten de gegenereerde JS- en CSS-bestanden van de insluitingsbibliotheek de code van de ingesloten bibliotheek.

Het insluiten van code is handig voor het verschaffen van toegang tot bibliotheken die zijn opgeslagen in beveiligde gebieden van de opslagplaats.

#### Toepassingsspecifieke clientbibliotheekmappen {#app-specific-client-library-folders}

U kunt het beste alle toepassingsgerelateerde bestanden in hun toepassingsmap onder `/apps` houden. Het wordt ook aanbevolen bezoekers van websites toegang tot de map `/apps` te weigeren. Voor beide aanbevolen procedures maakt u een clientbibliotheekmap onder de map `/etc` die de clientbibliotheek onder `/apps` insluit.

Gebruik de eigenschap Categorieën om de clientbibliotheekmap te identificeren die u wilt insluiten. Als u de bibliotheek wilt insluiten, voegt u een eigenschap toe aan het insluitingsknooppunt `cq:ClientLibraryFolder` en gebruikt u de volgende eigenschapkenmerken:

* **Naam:** bed in
* **Type:** Koord []
* **Waarde:** de waarde van het categoriebezit van de `cq:ClientLibraryFolder` knoop in te bedden.

#### Insluiten gebruiken om verzoeken te minimaliseren {#using-embedding-to-minimize-requests}

In sommige gevallen zult u zien dat de uiteindelijke HTML die door uw publicatie-instantie wordt gegenereerd voor een standaardpagina, een relatief groot aantal `<script>` -elementen bevat.

In dergelijke gevallen kan het handig zijn om alle vereiste code van de clientbibliotheek te combineren in één bestand, zodat het aantal heen en weer aanvragen bij het laden van de pagina wordt verminderd. Hiervoor kunt u `embed` de vereiste bibliotheken in uw toepassingsspecifieke clientbibliotheek plaatsen met de eigenschap embed van het knooppunt `cq:ClientLibraryFolder` .

#### Paden in CSS-bestanden {#paths-in-css-files}

Wanneer u CSS-bestanden insluit, gebruikt de gegenereerde CSS-code paden naar bronnen die relatief zijn ten opzichte van de insluitingsbibliotheek. De openbaar toegankelijke bibliotheek `/etc/client/libraries/myclientlibs/publicmain` sluit bijvoorbeeld de `/apps/myapp/clientlib` -clientbibliotheek in:

Het bestand `main.css` bevat de volgende stijl:

```javascript
body {
  padding: 0;
  margin: 0;
  background: url(images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

Het CSS-bestand dat de node `publicmain` genereert, bevat de volgende stijl met behulp van de URL van de oorspronkelijke afbeelding:

```javascript
body {
  padding: 0;
  margin: 0;
  background: url(../../../apps/myapp/clientlib/styles/images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

#### Zie Ingesloten bestanden in HTML-uitvoer {#see-embedded-files}

Als u de oorsprong van ingesloten code wilt traceren of wilt controleren of ingesloten clientbibliotheken de verwachte resultaten opleveren, kunt u de namen zien van de bestanden die bij uitvoering worden ingesloten. Als u de bestandsnamen wilt zien, voegt u de parameter `debugClientLibs=true` toe aan de URL van de webpagina. De gegenereerde bibliotheek bevat `@import` -instructies in plaats van de ingesloten code.

In het voorbeeld in het vorige [&#x200B; Inbedden Code van Andere Bibliotheken &#x200B;](#embedding-code-from-other-libraries) sectie, sluit de `/etc/client/libraries/myclientlibs/publicmain` omslag van de cliëntbibliotheek de `/apps/myapp/clientlib` omslag van de cliëntbibliotheek in. Als u de parameter aan de webpagina toevoegt, wordt de volgende koppeling in de broncode van de webpagina gemaakt:

```xml
<link rel="stylesheet" href="/etc/clientlibs/mycientlibs/publicmain.css">
```

Wanneer u het `publicmain.css` -bestand opent, wordt de volgende code weergegeven:

```javascript
@import url("/apps/myapp/clientlib/styles/main.css");
```

1. Voeg in het adresvak van uw webbrowser de volgende tekst toe aan de URL van uw HTML:
   * `?debugClientLibs=true`
1. Bekijk de paginabron wanneer de pagina wordt geladen.
1. Klik op de koppeling die wordt opgegeven als de href voor het koppelingselement om het bestand te openen en de broncode weer te geven.

### Voorprocessors gebruiken {#using-preprocessors}

AEM staat voor pluggable preprocessoren en schepen met steun voor [&#x200B; Compressor YUI &#x200B;](https://github.com/yui/yuicompressor#yui-compressor---the-yahoo-javascript-and-css-compressor) voor CSS en JavaScript toe en [&#x200B; de Compiler van de Sluiting van Google (GCC) &#x200B;](https://developers.google.com/closure/compiler/) voor JavaScript met YUI die als AEM standaard preprocessor wordt geplaatst.

Met de aanpasbare voorprocessoren kunt u flexibel gebruik maken, waaronder:

* ScriptProcessors definiëren die scriptbronnen kunnen verwerken
* Processors kunnen worden geconfigureerd met opties
* Processors kunnen worden gebruikt voor minificatie, maar ook voor niet-minieme gevallen
* Clientlib kan bepalen welke processor moet worden gebruikt

>[!NOTE]
>
>Standaard gebruikt AEM de GCC-compressor voor het miniaturen van Javascript en voor het transpileren van code naar `ECMASCRIPT_2018` .

>[!CAUTION]
>
>Plaats geen geminiateerde bibliotheek in een clientbibliotheek. Geef in plaats daarvan de onbewerkte bibliotheek op en gebruik de opties van de voorprocessoren als miniatuurafbeelding vereist is.

#### Gebruik {#usage}

U kunt kiezen om de configuratie van preprocessoren per clientbibliotheek of systeembreed te configureren.

* De eigenschappen multivalue `cssProcessor` en `jsProcessor` toevoegen aan het clientbibliotheekknooppunt

Het bepalen van de systeem standaardconfiguratie via de **configuratie OSGi van de Manager van de Bibliotheek van 0&rbrace; HTML wordt niet gesteund.** Het zal slechts op de lokale SDK en niet op volledig-stapel pijpleiding executies van toepassing zijn.

#### Indeling en voorbeelden {#format-and-examples}

##### Indeling {#format}

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
languageOut (defaults to "ECMASCRIPT_2018" as of release 21994, was previously "ECMASCRIPT5" )
compilationLevel (defaults to "simple") (can be "whitespace", "simple", "advanced")
```

Voor meer details op opties GCC, zie {de documentatie van 0} GCC [.](https://developers.google.com/closure/compiler/docs/compilation_levels)

#### Systeemstandaardminiatuur instellen {#set-system-default-minifier}

Het instellen van de standaardminiatuur van het systeem wordt niet ondersteund in AEM as a Cloud Service.
