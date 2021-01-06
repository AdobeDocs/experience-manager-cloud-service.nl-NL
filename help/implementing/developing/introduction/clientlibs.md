---
title: Client-Side bibliotheken gebruiken op AEM als Cloud Service
description: AEM biedt clientbibliotheekmappen, waarmee u uw clientcode (clientlibs) in de opslagplaats kunt opslaan, in categorieën kunt indelen en kunt bepalen wanneer en hoe elke categorie code aan de client moet worden verzonden
translation-type: tm+mt
source-git-commit: d4c031e17c0c83e44b687474502252c89ed37922
workflow-type: tm+mt
source-wordcount: '2571'
ht-degree: 0%

---


# Client-Side bibliotheken gebruiken op AEM als een Cloud Service {#using-client-side-libraries}

Digitale ervaringen zijn sterk afhankelijk van verwerking op de client door complexe JavaScript- en CSS-code. AEM Client-Side Libraries (clientlibs) kunt u deze clientbibliotheken organiseren en centraal opslaan in de opslagplaats. Gekoppeld aan [front-end bouwt proces in het AEM archetype van het Project, ](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/uifrontend.html) wordt het beheren van uw front-end code voor uw AEM project eenvoudig.

Tot de voordelen van het gebruik van clientlibs in AEM behoren:

* Client-side code wordt net als alle andere toepassingscode en inhoud in de repository opgeslagen
* Clientlibs in AEM kunnen alle CSS en JS in één bestand samenvoegen
* Clips toegankelijk maken via een pad dat toegankelijk is via de [dispatcher](/help/implementing/dispatcher/disp-overview.md)
* Hiermee kunt u paden herschrijven voor bestanden of afbeeldingen waarnaar wordt verwezen

Clientlibs zijn de ingebouwde oplossing voor het leveren van CSS en JavaScript van AEM.

>[!TIP]
>
>Voor-eindontwikkelaars die CSS en Javascript voor AEM projecten creëren zouden zich met [AEM het Archetype van het Project en zijn geautomatiseerd front-end bouwstijlproces ook moeten vertrouwd maken.](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/uifrontend.html)

## Wat zijn clientbibliotheken {#what-are-clientlibs}

Voor sites moeten JavaScript en CSS en statische bronnen zoals pictogrammen en weblettertypen op de client worden verwerkt. Een clientlib is AEM mechanisme om (per categorie indien vereist) naar dergelijke middelen te verwijzen en te dienen.

AEM verzamelt de CSS en Javascript van de site in één bestand, op een centrale locatie, om ervoor te zorgen dat slechts één kopie van een bron wordt opgenomen in de HTML-uitvoer. Hierdoor wordt de efficiëntie van de levering gemaximaliseerd en kunnen dergelijke bronnen centraal in de opslagplaats worden onderhouden via proxy, zodat de toegang veilig blijft.

## Front-end ontwikkeling voor AEM als Cloud Service {#fed-for-aemaacs}

Alle JavaScript, CSS, en andere front-end activa zouden in [ui.frontend module van het Archetype van het Project van de AEM moeten worden gehandhaafd.](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/uifrontend.html) Dankzij de flexibiliteit van het archetype kunt u uw moderne webgereedschappen gebruiken om deze bronnen te maken en te beheren.

Het archetype kan de bronnen vervolgens compileren in één CSS- en JS-bestand, en deze automatisch insluiten in een `cq:clientLibraryFolder` in de opslagplaats.

## Structuur van bibliotheekmap aan clientzijde {#clientlib-folders}

Een bibliotheekmap op de client is een opslagplaats van het type `cq:ClientLibraryFolder`. De definitie in [CND-notatie](https://jackrabbit.apache.org/node-type-notation.html) is

```text
[cq:ClientLibraryFolder] > sling:Folder
  - dependencies (string) multiple
  - categories (string) multiple
  - embed (string) multiple
  - channels (string) multiple
```

* `cq:ClientLibraryFolder` knooppunten kunnen overal in de  `/apps` substructuur van de opslagplaats worden geplaatst.
* Gebruik het `categories` bezit van de knoop om de bibliotheekcategorieën te identificeren waartot het behoort.

Elke `cq:ClientLibraryFolder` wordt gevuld met een set JS- en/of CSS-bestanden, samen met enkele ondersteunende bestanden (zie hieronder). Belangrijke eigenschappen van `cq:ClientLibraryFolder` worden als volgt gevormd:

* `allowProxy`: Aangezien alle clientlibs onder moeten worden opgeslagen, verleent dit bezit toegang tot clientlibraries  `apps`volmachtsservlet. Zie [Een clientbibliotheekmap zoeken en de server Servlet van de bibliotheken van de proxyclient gebruiken](#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet) hieronder.
* `categories`: Hiermee geeft u de categorieën aan waarin de set JS- en/of CSS-bestanden binnen deze  `cq:ClientLibraryFolder` groep vallen. Met de eigenschap `categories`, die meerdere waarden heeft, kan een bibliotheekmap deel uitmaken van meer dan één categorie (zie hieronder voor hoe dit nuttig kan zijn).

Als de map met clientbibliotheken een of meer bronbestanden bevat die tijdens runtime worden samengevoegd tot één JS- en/of CSS-bestand. De naam van het gegenereerde bestand is de knooppuntnaam met de bestandsextensie `.js` of `.css`. Het bibliotheekknooppunt met de naam `cq.jquery` resulteert bijvoorbeeld in het gegenereerde bestand met de naam `cq.jquery.js` of `cq.jquery.css`.

Clientbibliotheekmappen bevatten de volgende items:

* JS- en/of CSS-bronbestanden
* Statische bronnen die CSS-stijlen ondersteunen, zoals pictogrammen, weblettertypen, enz.
* Eén `js.txt`-bestand en/of één `css.txt`-bestand waarin de bronbestanden worden geïdentificeerd die in de gegenereerde JS- en/of CSS-bestanden moeten worden samengevoegd

![Clientlib-architectuur](assets/clientlib-architecture.drawio.png)

## Clientzijbibliotheekmappen maken {#creating-clientlib-folders}

Clientbibliotheken moeten zich onder `/apps` bevinden. Dit is om code beter van inhoud en configuratie te isoleren.

Voor de toegang tot clientbibliotheken onder `/apps` wordt een proxyserver gebruikt. ACLs wordt nog afgedwongen op de omslag van de cliëntbibliotheek, maar servlet staat voor de inhoud toe om via `/etc.clientlibs/` worden gelezen als het `allowProxy` bezit aan `true` wordt geplaatst.

1. Open CRXDE Lite in Webbrowser (`https://<host>:<port>/crx/de`).
1. Selecteer de map `/apps` en klik op **Maken > Knooppunt maken**.
1. Voer een naam in voor de bibliotheekmap en selecteer `cq:ClientLibraryFolder` in de lijst **Type**. Klik **OK** en klik vervolgens op **Alles opslaan**.
1. Als u de categorie of categorieën wilt opgeven waartoe de bibliotheek behoort, selecteert u het knooppunt `cq:ClientLibraryFolder`, voegt u de volgende eigenschap toe en klikt u op **Alles opslaan**:
   * Naam: `categories`
   * Type: String
   * Waarde: De categorienaam
   * Meerdere: Geselecteerd
1. Als u wilt dat de clientbibliotheken toegankelijk zijn via proxy onder `/etc.clientlibs`, selecteert u het `cq:ClientLibraryFolder`-knooppunt, voegt u de volgende eigenschap toe en klikt u op **Alles opslaan**:
   * Naam: `allowProxy`
   * Type: Boolean
   * Waarde: `true`
1. Als u statische bronnen moet beheren, maakt u een submap met de naam `resources` onder de clientbibliotheekmap.
   * Als u statische bronnen opslaat in de map `resources`, kan er niet naar worden verwezen in een publicatie-instantie.
1. Bronbestanden toevoegen aan de bibliotheekmap.
   * Dit wordt typisch gedaan door het front-end bouwstijlproces van [AEM Project Archetype.](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/uifrontend.html)
   * U kunt bronbestanden desgewenst in submappen ordenen.
1. Selecteer de map met de clientbibliotheek en klik op **Maken > Bestand maken**.
1. Typ in het vak Bestandsnaam een van de volgende bestandsnamen en klik op OK:
   * **`js.txt`:** Gebruik deze bestandsnaam om een JavaScript-bestand te genereren.
   * **`css.txt`:** Gebruik deze bestandsnaam om een trapsgewijs opmaakmodel te genereren.
1. Open het bestand en typ de volgende tekst om de hoofdmap van het pad van de bronbestanden te identificeren:
   * `#base=*[root]*`
   * Vervang `[root]` door het pad naar de map met de bronbestanden, relatief ten opzichte van het TXT-bestand. Gebruik bijvoorbeeld de volgende tekst wanneer de bronbestanden zich in dezelfde map bevinden als het TXT-bestand:
      * `#base=.`
   * Met de volgende code wordt de hoofdmap ingesteld als de map met de naam mobile onder het knooppunt `cq:ClientLibraryFolder`:
      * `#base=mobile`
1. Typ op de onderstaande regels de paden van de bronbestanden ten opzichte van de hoofdmap. `#base=[root]` Plaats elke bestandsnaam op een aparte regel.
1. Klik **Alles opslaan**.

## Bezig met bedienen van client-side bibliotheken {#serving-clientlibs}

Zodra uw cliëntbibliotheekomslag [zoals vereist wordt gevormd,](#creating-clientlib-folders) kunnen uw cliënten via volmacht worden gevraagd. Als voorbeeld:

* U hebt een clientlib in `/apps/myproject/clientlibs/foo`
* U hebt een statische afbeelding in `/apps/myprojects/clientlibs/foo/resources/icon.png`

Met de eigenschap `allowProxy` kunt u het volgende aanvragen:

* Clientlib via j`/etc.clientlibs/myprojects/clientlibs/foo.js`
* De statische afbeelding via `/etc.clientlibs/myprojects/clientlibs/foo/resources/icon.png`

### Clientbibliotheken laden via HTML {#loading-via-htl}

Zodra uw clientbibliotheken zijn opgeslagen en beheerd in hun clientbibliotheekmap, kunnen ze toegang krijgen via HTML.

Clientbibliotheken worden geladen via een helpersjabloon die door AEM wordt geboden en die toegankelijk is via `data-sly-use`. De malplaatjes van de hulp zijn beschikbaar in dit dossier, dat door `data-sly-call` kan worden geroepen.

Elke helpermalplaatje verwacht een `categories` optie voor het van verwijzingen voorzien van de gewenste cliëntbibliotheken. Deze optie kan ofwel een array van tekenreekswaarden zijn, ofwel een tekenreeks met een lijst met door komma&#39;s gescheiden waarden.

[Raadpleeg de HTML-](https://docs.adobe.com/content/help/en/experience-manager-htl/using/getting-started/getting-started.html#loading-client-libraries) documentatie voor meer informatie over het laden van clientlibs via HTML.

<!--
### Setting Cache Timestamps {#setting-cache-timestamps}

This is possible. Still need detail.
-->

## Client-bibliotheken op auteur versus publiceren {#clientlibs-author-publish}

De meeste clientlibs zijn vereist voor de AEM-publicatie-instantie. Dat wil zeggen dat de meeste clientlibs-doeleinden de eindgebruikerservaring van de inhoud moeten opleveren. Voor clientlibs op publicatie-instanties kunnen [front-end build tools](#fed-for-aemaacs) worden gebruikt en geïmplementeerd via [clientbibliotheekmappen zoals hierboven beschreven.](#creating-clientlib-folders)

Er zijn echter momenten waarop clientbibliotheken nodig kunnen zijn om de ontwerpervaring aan te passen. Als u bijvoorbeeld een dialoogvenster aanpast, moet u mogelijk kleine CSS- of JS-bits implementeren in de AEM ontwerpinstantie.

### Client-bibliotheken beheren op auteur {#clientlibs-on-author}

Als u clientbibliotheken op auteur moet gebruiken, kunt u uw clientbibliotheken onder `/apps` maken met dezelfde methoden als voor publiceren, maar deze rechtstreeks onder `/apps/.../clientlibs/foo` schrijven in plaats van een volledig project te maken om het te beheren.

U kunt dan &quot;haken&quot;in auteursJS door uw cliëntbibliotheken aan een uit-van-de-doos categorie van de cliëntbibliotheek toe te voegen.

## Foutopsporingsgereedschappen {#debugging-tools}

AEM beschikt over verschillende gereedschappen voor foutopsporing en het testen van clientbibliotheekmappen.

### Clientbibliothekendetecteren {#discover-client-libraries}

De component `/libs/cq/granite/components/dumplibs/dumplibs` genereert een pagina met informatie over alle clientbibliotheekmappen op het systeem. De `/libs/granite/ui/content/dumplibs` knoop heeft de component als middeltype. Als u de pagina wilt openen, gebruikt u de volgende URL (waarbij u de host en poort naar wens wijzigt):

`https://<host>:<port>/libs/granite/ui/content/dumplibs.test.html`

Tot de gegevens behoren het bibliotheekpad en -type (CSS of JS) en de waarden van de bibliotheekkenmerken, zoals categorieën en afhankelijkheden. In de volgende tabellen op de pagina worden de bibliotheken in elke categorie en elk kanaal weergegeven.

### Zie gegenereerde uitvoer {#see-generated-output}

De `dumplibs` component omvat een testselecteur die de broncode toont die voor `ui:includeClientLib` markeringen wordt geproduceerd. De pagina bevat code voor verschillende combinaties van js-, css- en themakenmerken.

1. Gebruik een van de volgende methoden om de pagina Uitvoer testen te openen:
   * Klik op de pagina `dumplibs.html` op de koppeling in **Klik hier voor uitvoertests** tekst.
   * Open de volgende URL in uw webbrowser (gebruik indien nodig een andere host en poort):
      * `http://<host>:<port>/libs/granite/ui/content/dumplibs.html`
   * Op de standaardpagina wordt uitvoer weergegeven voor tags zonder waarde voor het categoriekenmerk.
1. Als u de uitvoer voor een categorie wilt zien, typt u de waarde van de eigenschap `categories` van de clientbibliotheek en klikt u op **Query verzenden**.

## Extra functies voor clientbibliotheekmappen {#additional-features}

Er zijn een aantal andere functies die in AEM door clientbibliotheekmappen worden ondersteund. Deze zijn echter niet vereist voor AEM als Cloud Service en als zodanig wordt het gebruik ervan afgeraden. Ze worden hier ter volledigheid vermeld.

>[!WARNING]
>
>Deze extra functies van clientbibliotheekmappen zijn niet vereist voor AEM als Cloud Service en daarom wordt het gebruik ervan afgeraden. Ze worden hier ter volledigheid vermeld.

### Adobe Granite HTML Library Manager {#html-library-manager}

Extra instellingen voor de clientbibliotheek kunt u beheren via het deelvenster **Adobe Granite HTML Library Manager** van de systeemconsole op `https://<host>:<port>/system/console/configMgr`).

### Aanvullende mapeigenschappen {#additional-folder-properties}

De extra omslageigenschappen omvatten staan controle van gebiedsdelen en bedden toe, maar zijn over het algemeen niet meer nodig en hun gebruik wordt ontmoedigd:

* `dependencies`: Dit is een lijst van andere categorieën van de cliëntbibliotheek waarvan deze bibliotheekomslag afhangt. Als een bestand in `F` bijvoorbeeld een ander bestand in `G` nodig heeft om correct te kunnen functioneren, moet ten minste een van de `categories` van `G` een van de `dependencies` van `F` zijn als er twee `cq:ClientLibraryFolder` knooppunten `F` en &lt;a6/> zijn.`G`
* `embed`: Wordt gebruikt om code uit andere bibliotheken in te sluiten. Als knooppunt `F` knooppunten `G` en `H` insluit, is de resulterende HTML een samenvoeging van inhoud van knooppunten `G` en `H`.

### Koppelen aan afhankelijkheden {#linking-to-dependencies}

Wanneer de code in de map met clientbibliotheken verwijst naar andere bibliotheken, identificeert u de andere bibliotheken als afhankelijkheden. De tag `ui:includeClientLib` die verwijst naar de map van de clientbibliotheek zorgt ervoor dat de HTML-code een koppeling bevat naar het gegenereerde bibliotheekbestand en de afhankelijkheden.

De afhankelijkheden moeten een andere `cq:ClientLibraryFolder` zijn. Om gebiedsdelen te identificeren, voeg een bezit aan uw `cq:ClientLibraryFolder` knoop met de volgende attributen toe:

* **Naam:** afhankelijkheden
* **type:** String[]
* **Waarden:** De waarde van de eigenschap category van het knooppunt cq:ClientLibraryFolder waarvan de huidige bibliotheekmap afhankelijk is.

De `/etc/clientlibs/myclientlibs/publicmain` is bijvoorbeeld afhankelijk van de `cq.jquery`-bibliotheek. De pagina die verwijst naar de hoofdclientbibliotheek genereert HTML met de volgende code:

```xml
<script src="/etc/clientlibs/foundation/cq.jquery.js" type="text/javascript">
<script src="/etc/clientlibs/mylibs/publicmain.js" type="text/javascript">
```

### Code insluiten uit andere bibliotheken {#embedding-code-from-other-libraries}

U kunt code van een clientbibliotheek insluiten in een andere clientbibliotheek. Tijdens de runtime bevatten de gegenereerde JS- en CSS-bestanden van de insluitingsbibliotheek de code van de ingesloten bibliotheek.

Het insluiten van code is handig voor het verschaffen van toegang tot bibliotheken die zijn opgeslagen in beveiligde gebieden van de opslagplaats.

#### Toepassingsspecifieke clientbibliotheekmappen {#app-specific-client-library-folders}

Het wordt aanbevolen alle toepassingsgerelateerde bestanden in hun toepassingsmap onder `/app` te houden. Het is ook raadzaam websitebezoekers de toegang tot de map `/app` te ontzeggen. Om aan beide beste praktijken te voldoen, creeer een omslag van de cliëntbibliotheek onder de `/etc` omslag die de cliëntbibliotheek inbedt die onder `/app` is.

Gebruik de eigenschap Categorieën om de clientbibliotheekmap te identificeren die u wilt insluiten. Als u de bibliotheek wilt insluiten, voegt u een eigenschap toe aan het insluitende `cq:ClientLibraryFolder`-knooppunt en gebruikt u de volgende eigenschapkenmerken:

* **Naam:** insluiten
* **type:** String[]
* **Waarde:** de waarde van de eigenschap category van het  `cq:ClientLibraryFolder` knooppunt dat moet worden ingesloten.

#### Insluiten gebruiken om verzoekente minimaliseren {#using-embedding-to-minimize-requests}

In sommige gevallen zult u zien dat de uiteindelijke HTML die door uw publicatieexemplaar wordt gegenereerd voor een standaardpagina, een relatief groot aantal `<script>`-elementen bevat.

In dergelijke gevallen kan het handig zijn om alle vereiste code van de clientbibliotheek te combineren in één bestand, zodat het aantal heen en weer aanvragen bij het laden van de pagina wordt verminderd. Hiervoor kunt u `embed` de vereiste bibliotheken in uw app-specifieke clientbibliotheek gebruiken met de eigenschap embed van het knooppunt `cq:ClientLibraryFolder`.

#### Paden in CSS-bestanden {#paths-in-css-files}

Wanneer u CSS-bestanden insluit, gebruikt de gegenereerde CSS-code paden naar bronnen die relatief zijn ten opzichte van de insluitingsbibliotheek. In de openbaar toegankelijke bibliotheek `/etc/client/libraries/myclientlibs/publicmain` wordt bijvoorbeeld de clientbibliotheek `/apps/myapp/clientlib` ingesloten:

Het `main.css`-bestand bevat de volgende stijl:

```javascript
body {
  padding: 0;
  margin: 0;
  background: url(images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

Het CSS-bestand dat het knooppunt `publicmain` genereert, bevat de volgende stijl met de URL van de oorspronkelijke afbeelding:

```javascript
body {
  padding: 0;
  margin: 0;
  background: url(../../../apps/myapp/clientlib/styles/images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

#### Zie Ingesloten bestanden in HTML-uitvoer {#see-embedded-files}

Als u de oorsprong van ingesloten code wilt traceren of wilt controleren of ingesloten clientbibliotheken de verwachte resultaten opleveren, kunt u de namen zien van de bestanden die bij uitvoering worden ingesloten. Als u de bestandsnamen wilt zien, voegt u de parameter `debugClientLibs=true` toe aan de URL van de webpagina. De gegenereerde bibliotheek bevat `@import`-instructies in plaats van de ingesloten code.

In het voorbeeld in de vorige [sectie Code insluiten vanuit andere bibliotheken](#embedding-code-from-other-libraries) wordt in de clientbibliotheekmap `/etc/client/libraries/myclientlibs/publicmain` de clientbibliotheekmap `/apps/myapp/clientlib` ingesloten. Als u de parameter aan de webpagina toevoegt, wordt de volgende koppeling in de broncode van de webpagina gemaakt:

```xml
<link rel="stylesheet" href="/etc/clientlibs/mycientlibs/publicmain.css">
```

Wanneer u het bestand `publicmain.css` opent, wordt de volgende code weergegeven:

```javascript
@import url("/apps/myapp/clientlib/styles/main.css");
```

1. Voeg in het adresvak van uw webbrowser de volgende tekst toe aan de URL van uw HTML:
   * `?debugClientLibs=true`
1. Bekijk de paginabron wanneer de pagina wordt geladen.
1. Klik op de koppeling die wordt opgegeven als de href voor het koppelingselement om het bestand te openen en de broncode weer te geven.

### Voorprocessorsgebruiken {#using-preprocessors}

AEM biedt instelbare preprocessoren en meegeleverde pakketten met ondersteuning voor [YUI-compressor](https://github.com/yui/yuicompressor#yui-compressor---the-yahoo-javascript-and-css-compressor) voor CSS en JavaScript en [Google Closure Compiler (GCC)](https://developers.google.com/closure/compiler/) voor JavaScript waarbij YUI is ingesteld als AEM standaardpreprocessor.

Met de aanpasbare voorprocessoren kunt u flexibel gebruik maken, waaronder:

* ScriptProcessors definiëren die scriptbronnen kunnen verwerken
* Processors kunnen worden geconfigureerd met opties
* Processors kunnen worden gebruikt voor minificatie, maar ook voor niet-minieme gevallen
* Clientlib kan bepalen welke processor moet worden gebruikt

>[!NOTE]
>
>AEM gebruikt standaard de YUI-compressor. Zie [YUI Compressor GitHub documentatie](https://github.com/yui/yuicompressor/issues) voor een lijst van bekende kwesties. Het schakelen naar GCC-compressor voor bepaalde clientlibs kan een aantal problemen oplossen die tijdens het gebruik van YUI zijn waargenomen.

>[!CAUTION]
>
>Plaats geen geminiateerde bibliotheek in een clientbibliotheek. Geef in plaats daarvan de onbewerkte bibliotheek op en gebruik de opties van de voorprocessoren als miniaturen vereist zijn.

#### Gebruik {#usage}

U kunt kiezen om de configuratie preprocessoren per clientbibliotheek of systeembreed te configureren.

* Voeg de multivalue-eigenschappen `cssProcessor` en `jsProcessor` toe op het clientbibliotheekknooppunt
* Of definieer de standaardsysteemconfiguratie via de OSGi-configuratie **HTML Library Manager**

Een preprocessorconfiguratie op de clientlib knoop neemt belangrijkheid over de configuratie OSGI.

#### Opmaak en voorbeelden {#format-and-examples}

##### Format {#format}

```javascript
config:= mode ":" processorName options*;
mode:= "default" | "min";
processorName := "none" | <name>;
options := ";" option;
option := name "=" value;
```

##### YUI-compressor voor CSS-minificatie en GCC voor JS {#yui-compressor-for-css-minification-and-gcc-for-js}

```javascript
cssProcessor: ["default:none", "min:yui"]
jsProcessor: ["default:none", "min:gcc;compilationLevel=advanced"]
```

##### Typescript aan preprocess en dan GCC omte kleven en te verduisteren {#typescript-to-preprocess-and-then-gcc-to-minify-and-obfuscate}

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

Raadpleeg de [GCC-documentatie](https://developers.google.com/closure/compiler/docs/compilation_levels) voor meer informatie over GCC-opties.

#### Systeemstandaardminiatuur instellen {#set-system-default-minifier}

YUI wordt geplaatst als standaardminifier in AEM. Voer de volgende stappen uit om dit te wijzigen in GCC.

1. Ga naar Apache Felix Config Manager op (`http://<host>:<portY/system/console/configMgr`)
1. Zoek en bewerk de **Adobe Granite HTML Library Manager**.
1. Schakel de optie **Minify** in (als deze optie nog niet is ingeschakeld).
1. Stel de waarde **Standaardconfiguratie JS-processor in op**.`min:gcc`
   * Opties kunnen worden doorgegeven als deze met een puntkomma worden gescheiden, bijvoorbeeld `min:gcc;obfuscate=true`.
1. Klik **Opslaan** om de wijzigingen op te slaan.
