---
title: Bewerkbare sjablonen
description: Leer hoe bewerkbare sjablonen worden gebruikt bij het maken van een pagina, het definiëren van de initiële inhoud, gestructureerde inhoud, het ontwerpbeleid en de lay-out van de pagina.
exl-id: ea42fce9-9af2-4349-a4e4-547e6e8da05c
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '3443'
ht-degree: 0%

---

# Bewerkbare sjablonen {#editable-templates}

Leer hoe bewerkbare sjablonen worden gebruikt bij het maken van een pagina, het definiëren van de initiële inhoud, gestructureerde inhoud, het ontwerpbeleid en de lay-out van de pagina.

## Overzicht {#overview}

Wanneer u een pagina maakt, moet u een sjabloon selecteren. De paginasjabloon wordt gebruikt als basis voor de nieuwe pagina. Met de sjabloon kunt u de structuur van de resulterende pagina, eventuele eerste inhoud en de componenten definiëren die kunnen worden gebruikt (ontwerpeigenschappen).

* Met bewerkbare sjablonen kunnen auteurs sjablonen maken en gebruiken.
* Bewerkbare sjablonen kunnen worden gebruikt om pagina&#39;s te maken die kunnen worden bewerkt met beide
   * [ Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/templates.md) en
   * [Universele editor](/help/sites-cloud/authoring/universal-editor/templates.md)

Met paginasjablonen die worden gebruikt om pagina&#39;s te maken die kunnen worden bewerkt met de Universal Editor, wordt een beperkte subset van bewerkbare sjabloonfunctionaliteit gebruikt. Daarom richt de rest van dit document zich op bewerkbare sjablonen die worden gebruikt om pagina&#39;s te maken die kunnen worden bewerkt met de Pagina-editor.

## Bewerkbare sjablonen en pagina&#39;s bewerkt met de Pagina-editor {#page-editor}

Bij het maken van sjablonen voor het maken van pagina&#39;s die kunnen worden bewerkt met de Pagina-editor, worden gewoonlijk gespecialiseerde auteurs geïdentificeerd.

* Dergelijke gespecialiseerde auteurs worden genoemd **malplaatjeauteurs**
* Sjabloonauteurs moeten lid zijn van de groep `template-authors` .
* Bewerkbare sjablonen behouden een dynamische verbinding met alle pagina&#39;s die ermee zijn gemaakt. Zo zorgt u ervoor dat wijzigingen in de sjabloon ook op de pagina&#39;s zelf worden doorgevoerd.
* Bewerkbare sjablonen maken de paginacomponent generischer, zodat de basispaginacomponent zonder aanpassing kan worden gebruikt.

Met bewerkbare sjablonen worden de onderdelen die een pagina maken, geïsoleerd in componenten. U kunt de noodzakelijke combinaties componenten in een UI vormen, daardoor eliminerend de behoefte aan een nieuwe paginacomponent die voor elke paginariatie moet worden ontwikkeld.

Dit document:

* Geeft een overzicht van het maken van een bewerkbare sjabloon
* Beschrijft de admin/ontwikkelaarstaken die worden vereist om editable malplaatjes tot stand te brengen
* Beschrijft de technische onderbouwing van editable malplaatjes
* Beschrijft hoe AEM de beschikbaarheid van een malplaatje evalueert

>[!NOTE]
>
>In dit document wordt ervan uitgegaan dat u vertrouwd bent met het maken en bewerken van sjablonen. Zie het auteursdocument [ Malplaatjes om Pagina&#39;s tot stand te brengen die met de Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/templates.md) editable zijn, die de mogelijkheden van editable malplaatjes zoals blootgesteld aan de malplaatjeauteur detailleert.

>[!TIP]
>
>[ het leerprogramma WKND ](/help/implementing/developing/introduction/develop-wknd-tutorial.md) gaat diepgaand in hoe te om editable malplaatjes te gebruiken door een voorbeeld uit te voeren en is vrij nuttig voor het begrip hoe te opstelling een malplaatje in een nieuw project

## Een nieuwe bewerkbare sjabloon maken {#creating-a-new-template}

Het creëren van editable malplaatjes wordt hoofdzakelijk gedaan met de [ malplaatjeconsole en malplaatjeredacteur ](/help/sites-cloud/authoring/page-editor/templates.md) door een malplaatjeauteur. In deze paragraaf wordt een overzicht gegeven van dit proces en wordt een beschrijving gegeven van wat er op technisch niveau gebeurt.

Bij het maken van een bewerkbare sjabloon:

1. Creeer a [ omslag voor de malplaatjes ](#template-folders). Dit is niet verplicht, maar aanbevolen beste praktijken.
1. Selecteer a [ malplaatjetype ](#template-type). Dit wordt gekopieerd om de [ malplaatjedefinitie ](#template-definitions) tot stand te brengen.

   >[!NOTE]
   >
   >Een selectie van sjabloontypen is beschikbaar buiten het vak. U kunt ook [ uw eigen plaats-specifieke malplaatjetypes ](#creating-template-types) tot stand brengen indien nodig.

1. Vorm de structuur, inhoudsbeleid, aanvankelijke inhoud, en lay-out van het nieuwe malplaatje.

   **Structuur**

   * Met de structuur kunt u componenten en inhoud voor de sjabloon definiëren.
   * Componenten die in de sjabloonstructuur zijn gedefinieerd, kunnen niet op een resulterende pagina worden verplaatst of uit resulterende pagina&#39;s worden verwijderd.
   * Als u wilt dat auteurs van pagina&#39;s componenten kunnen toevoegen en verwijderen, voegt u een alineasysteem toe aan de sjabloon.
   * Componenten kunnen worden ontgrendeld en opnieuw worden vergrendeld, zodat u de initiële inhoud kunt definiëren.

   Voor details op hoe een malplaatjeauteur de structuur bepaalt, zie [ Malplaatjes om Pagina&#39;s tot stand te brengen die met de Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/templates.md#editing-a-template-structure-template-author) editable zijn.

   Voor technische details van de structuur, zie [ Structuur ](#structure) in dit document.

   **Beleid**

   * Het inhoudsbeleid definieert de ontwerpeigenschappen van een component.

      * Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen.

   * Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

   Voor details op hoe een malplaatjeauteur beleid bepaalt, zie [ Malplaatjes om Pagina&#39;s tot stand te brengen die met de Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/templates.md#editing-a-template-structure-template-author) editable zijn.

   Voor technische details van beleid, zie [ Beleid van de Inhoud ](#content-policies) in dit document.

   **Aanvankelijke Inhoud**

   * Met Eerste inhoud wordt inhoud gedefinieerd die wordt weergegeven wanneer een pagina voor het eerst wordt gemaakt op basis van de sjabloon.
   * De initiële inhoud kan vervolgens worden bewerkt door auteurs van pagina&#39;s.

   Voor details op hoe een malplaatjeauteur de structuur bepaalt, zie [ Malplaatjes om Pagina&#39;s tot stand te brengen die met de Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/templates.md#editing-a-template-initial-content-author) editable zijn.

   Voor technische details op aanvankelijke inhoud, zie [ Aanvankelijke Inhoud ](#initial-content) in dit document.

   **Lay-out**

   * U kunt de sjabloonlay-out voor een reeks apparaten definiëren.
   * De responsieve indeling voor sjablonen werkt op dezelfde manier als voor het ontwerpen van pagina&#39;s.

   Voor details op hoe een malplaatjeauteur de malplaatjelay-out bepaalt, zie [ Malplaatjes om Pagina&#39;s tot stand te brengen die met de Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/templates.md#editing-a-template-layout-template-author) editable zijn.

   Voor technische details op malplaatjelay-out, zie [ Lay-out ](#layout) in dit document.

1. Schakel de sjabloon in en sta deze vervolgens toe voor specifieke inhoudstructuren.

   * U kunt een sjabloon in- of uitschakelen om de sjabloon beschikbaar of niet beschikbaar te maken voor auteurs van pagina&#39;s.
   * Een sjabloon kan beschikbaar worden gesteld of niet beschikbaar zijn voor bepaalde paginasvertakkingen.

   Voor details op hoe een malplaatjeauteur een malplaatje toelaat, zie [ Malplaatjes om Pagina&#39;s tot stand te brengen die met de Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/templates.md#enabling-and-allowing-a-template-template-author) editable zijn.

   Voor technische details bij het toelaten van een malplaatje, zie [ Toelatend en Toestaan een Malplaatje voor Gebruik ](#enabling-and-allowing-a-template-for-use) e in dit document

1. Gebruik dit besturingselement om inhoudspagina&#39;s te maken.

   * Wanneer u een sjabloon gebruikt om een pagina te maken, is er geen zichtbaar verschil en is er geen indicatie tussen statische en bewerkbare sjablonen.
   * Voor de auteur van de pagina is het proces transparant.

   Voor details op hoe een paginaauteur malplaatjes gebruikt om een pagina tot stand te brengen, zie [ Creërend en Organiserend Pagina&#39;s ](/help/sites-cloud/authoring/sites-console/organizing-pages.md#templates).

   Voor technische details bij het creëren van pagina&#39;s met editable malplaatjes, zie [ Resulterende Pagina&#39;s van de Inhoud ](#resultant-content-pages) in dit document.

>[!TIP]
>
>Voer nooit informatie in die geïnternationaliseerd moet worden in een sjabloon. Voor internaliseringsdoeleinden, worden de [ localiseringseigenschappen van de Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html) geadviseerd.

>[!NOTE]
>
>Sjablonen zijn krachtige gereedschappen om de workflow voor het maken van pagina&#39;s te stroomlijnen. Te veel sjablonen kunnen de auteurs echter overweldigen en tot verwarring bij het maken van pagina&#39;s leiden. Een goede regel is om het aantal sjablonen onder de 100 te houden.
>
>Adobe raadt niet aan meer dan 1000 sjablonen te hebben vanwege mogelijke gevolgen voor de prestaties.

>[!NOTE]
>
>In de clientbibliotheek van de editor wordt ervan uitgegaan dat de naamruimte `cq.shared` aanwezig is in inhoudspagina&#39;s. Als deze ontbreekt, treedt de JavaScript-fout `Uncaught TypeError: Cannot read property 'shared' of undefined` op.
>
>Alle pagina&#39;s met voorbeeldinhoud bevatten `cq.shared` , dus alle inhoud die hierop is gebaseerd, bevat automatisch `cq.shared` . Als u echter besluit uw eigen inhoudspagina&#39;s helemaal zelf te maken zonder deze te baseren op voorbeeldinhoud, moet u de naamruimte `cq.shared` wel invoegen.
>
>Zie [ Gebruikend Cliënt-Kant Bibliotheken ](/help/implementing/developing/introduction/clientlibs.md) voor verdere informatie.

## Sjabloonmappen {#template-folders}

Voor het organiseren van uw sjablonen kunt u de volgende mappen gebruiken:

* `global`
* Sitespecifiek

>[!NOTE]
>
>Alhoewel u uw omslagen kunt nesten, wanneer de gebruiker hen in de **console van Malplaatjes** bekijkt worden zij voorgesteld als vlakke structuur.

In een standaard AEM-instantie bestaat de map `global` al in de sjabloonconsole. Dit houdt standaardmalplaatjes vast en doet dienst als reserve als geen beleid en/of malplaatje-types in de huidige omslag worden gevonden. U kunt uw standaardsjablonen toevoegen aan deze map of een map maken (aanbevolen).

>[!NOTE]
>
>Het wordt aanbevolen een map te maken waarin uw aangepaste sjablonen staan en de map `global` niet te gebruiken.

>[!CAUTION]
>
>Mappen moeten worden gemaakt door een gebruiker met `admin` -rechten.

Sjabloontypen en beleid worden in alle mappen overgeërfd volgens de volgende prioriteitsvolgorde:

1. De huidige map
1. Bovenliggend item of bovenliggende items van de huidige map
1. `/conf/global`
1. `/apps`
1. `/libs`

Er wordt een lijst met alle toegestane vermeldingen gemaakt. Als configuraties elkaar overlappen ( `path`/ `label` ), wordt alleen de instantie die zich het dichtst bij de huidige map bevindt, aan de gebruiker getoond.

Als u een map wilt maken, kunt u het volgende doen:

* Programmaticaal of met CRXDE Lite
* Het gebruiken van [ Browser van de Configuratie ](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)

## CRXDE Lite gebruiken {#using-crxde-lite}

1. Een nieuwe omslag (onder /conf) kan voor uw instantie of programmatically of met CRXDE Lite worden gecreeerd.

   De volgende structuur moet worden gebruikt:

   ```xml
   /conf
       <your-folder-name> [sling:Folder]
           settings [sling:Folder]
               wcm [cq:Page]
                   templates [cq:Page]
                   policies [cq:Page]
   ```

1. Vervolgens kunt u de volgende eigenschappen definiëren voor het hoofdknooppunt van de map:

   `<your-folder-name> [sling:Folder]`

   * Naam: `jcr:title`
   * Type: `String`
   * Waarde: De titel (voor de omslag) u in de **console van Malplaatjes** wilt verschijnen.

1. Naast de standaardauteurstoestemmingen en voorrechten (bijvoorbeeld, `content-authors`) moet u nu groep(en) toewijzen en de vereiste toegangsrechten (ACLs) bepalen voor uw auteurs om malplaatjes in de nieuwe omslag te kunnen tot stand brengen.

   De `template-authors` -groep is de standaardgroep die moet worden toegewezen. Zie de sectie [ ACLs en Groepen ](#acls-and-groups) voor details.

   <!--See [Access Right Management](/help/sites-administering/user-group-ac-admin.md#access-right-management) for full details on managing and assigning access rights.-->

### De configuratiebrowser gebruiken {#using-the-configuration-browser}

1. Ga naar **Globale Navigatie** > **Hulpmiddelen** > [**Browser van de Configuratie**](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

   De bestaande mappen worden links weergegeven, inclusief de map `global` .

1. Klik **creëren**.
1. In **creeer de dialoog van de Configuratie** de volgende gebieden moeten worden gevormd:

   * **Titel**: Verstrek een titel voor de configuratiemap
   * **Bewerkbare Malplaatjes**: Tik om voor editable malplaatjes binnen deze omslag toe te staan

1. Klik **creëren**

>[!NOTE]
>
>In Browser van de Configuratie [&#128279;](/help/implementing/developing/introduction/configurations.md#using-configuration-browser), kunt u de globale omslag uitgeven en de **Bewerkbare optie van Malplaatjes** activeren als u malplaatjes binnen deze omslag wilt tot stand brengen, nochtans wordt dit geadviseerde beste praktijken niet.

### ACLs en Groepen {#acls-and-groups}

Zodra uw malplaatjeomslagen (of via CRXDE of met Browser van de Configuratie) worden gecreeerd, moet ACLs voor de aangewezen groepen voor de malplaatjeomslagen worden bepaald om juiste veiligheid te verzekeren.

De malplaatjeomslagen voor het [ WKND leerprogramma ](/help/implementing/developing/introduction/develop-wknd-tutorial.md) kan als voorbeeld worden gebruikt.

#### De groep sjabloonauteurs {#the-template-authors-group}

De `template-authors` -groep is de groep die wordt gebruikt om toegang tot sjablonen te beheren en wordt standaard met AEM geleverd, maar is leeg. Gebruikers moeten worden toegevoegd aan de groep voor het project of de site.

>[!CAUTION]
>
>De `template-authors` -groep is alleen voor gebruikers die nieuwe sjablonen moeten kunnen maken.
>
>Het bewerken van sjablonen is bijzonder krachtig en als dit niet het geval is, kunnen bestaande sjablonen worden verbroken. Daarom moet deze rol worden toegespitst en alleen gekwalificeerde gebruikers omvatten.

In de volgende tabel worden de benodigde machtigingen voor sjabloonbewerking weergegeven.

<table>
 <tbody>
  <tr>
   <th>Pad</th>
   <th>Rol/groep</th>
   <th>Machtigingen <br /> </th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/templates</code></td>
   <td>Sjabloonauteurs <br /> </td>
   <td>lezen, schrijven, repliceren</td>
   <td>Sjabloonauteurs die sjablonen maken, lezen, bijwerken, verwijderen en repliceren in sitespecifieke <code>/conf</code> ruimte</td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>lezen</td>
   <td>De anonieme Gebruiker van het Web moet malplaatjes lezen terwijl het teruggeven van een pagina</td>
  </tr>
  <tr>
   <td>Inhoudsauteurs</td>
   <td>repliceren</td>
   <td>ReplicateContent-auteurs moeten de sjablonen van een pagina activeren wanneer ze een pagina activeren</td>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/policies</code></td>
   <td><code>Template Author</code></td>
   <td>lezen, schrijven, repliceren</td>
   <td>Sjabloonauteurs die sjablonen maken, lezen, bijwerken, verwijderen en repliceren in sitespecifieke <code>/conf</code> ruimte</td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>lezen</td>
   <td>De anonieme Gebruiker van het Web moet beleid lezen terwijl het teruggeven van een pagina</td>
  </tr>
  <tr>
   <td>Inhoudsauteurs</td>
   <td>repliceren</td>
   <td>Auteurs van inhoud moeten het beleid van een sjabloon op een pagina activeren wanneer ze een pagina activeren</td>
  </tr>
  <tr>
   <td rowspan="2"><code>/conf/&lt;site&gt;/settings/template-types</code></td>
   <td>Sjabloonauteur</td>
   <td>lezen</td>
   <td>Sjabloonauteur maakt een nieuwe sjabloon op basis van een van de vooraf gedefinieerde sjabloontypen.</td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>none</td>
   <td>De anonieme Gebruiker van het Web moet tot de malplaatjetypes niet toegang hebben</td>
  </tr>
 </tbody>
</table>

Deze standaardgroep `template-authors` geldt alleen voor de projectinstellingen, waarbij alle `template-authors` -leden toegang hebben tot alle sjablonen en deze mogen samenstellen. Voor complexere montages, waar de veelvoudige groepen van malplaatjeauteurs nodig zijn om toegang tot malplaatjes te scheiden, moeten meer de auteursgroepen van het douanemalplaatje worden gecreeerd. Nochtans zouden de toestemmingen voor de groepen van malplaatjeauteurs nog het zelfde zijn.

## Sjabloontype {#template-type}

Wanneer u een sjabloon maakt, moet u een sjabloontype opgeven:

* Sjabloontypen bieden sjablonen voor een sjabloon. Wanneer u een sjabloon maakt, worden de structuur en de initiële inhoud van het geselecteerde sjabloontype gebruikt om aan de nieuwe sjabloon te maken.

   * Het sjabloontype wordt gekopieerd om de sjabloon te maken.
   * Zodra het exemplaar is voorgekomen, is de enige verbinding tussen het malplaatje en het malplaatjetype een statische verwijzing voor informatiedoeleinden.

* Met sjabloontypen kunt u het volgende definiëren:

   * Het middeltype van de paginacomponent.
   * Het beleid van de wortelknoop, die de componenten bepaalt die in de malplaatjeredacteur worden toegestaan.
   * Het wordt aanbevolen de onderbrekingspunten voor het responsieve raster en de instelling van de mobiele emulator op te geven voor het sjabloontype.

* AEM biedt een kleine selectie van sjabloontypen die buiten het vak vallen, zoals HTML5 Pagina en Aangepaste formulierpagina.

   * De extra voorbeelden worden verstrekt als deel van het [ WKND leerprogramma ](/help/implementing/developing/introduction/develop-wknd-tutorial.md).

* Sjabloontypen worden meestal gedefinieerd door ontwikkelaars.

De sjabloontypen voor de out-of-the-box worden opgeslagen onder:

* `/libs/settings/wcm/template-types`

>[!CAUTION]
>
>U mag niets wijzigen in het `/libs` -pad. De reden hiervoor is dat de inhoud van `/libs` op elk moment kan worden overschreven door een update naar AEM.

Uw sitespecifieke sjabloontypen moeten worden opgeslagen op de vergelijkbare locatie:

* `/apps/settings/wcm/template-types`

Definities voor uw aangepaste sjabloontypen moeten worden opgeslagen in door de gebruiker gedefinieerde mappen (aanbevolen) of anders in `global` . Bijvoorbeeld:

* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/template-types`
* `/conf/<my-folder>/settings/wcm/template-types`
* `/conf/global/settings/wcm/template-types`

>[!CAUTION]
>
>De sjabloontypen moeten de juiste mapstructuur (dat wil zeggen `/settings/wcm/...` ) respecteren, anders worden de sjabloontypen niet gevonden.

<!--
### Template Type and Mobile Device Groups {#template-type-and-mobile-device-groups-br}

The [device groups](/help/sites-developing/mobile.md#device-groups) used for an editable template (set as relative path of the property `cq:deviceGroups`) define which mobile devices are available as emulators in the [layout mode](/help/sites-authoring/responsive-layout.md) of page authoring. This value can be set in two places:

* On the editable template type
* On the editable template

When creating an editable template, the value is copied from the template type to the individual template. If the value is not set on the type, it can be set on the template. Once a template is created, there is no inheritance from the type to the template.

>[!CAUTION]
>
>The value of `cq:deviceGroups` must be set as a relative path such as `mobile/groups/responsive` and not as an absolute path such as `/etc/mobile/groups/responsive`.

>[!NOTE]
>
>With static templates /help/sites-developing/page-templates-static.md, the value of `cq:deviceGroups` could be set at the root of the site.
>
>With editable templates, this value is now stored at the template level and is not supported at the page root level.
-->

### Sjabloontypen maken {#creating-template-types}

Als u een sjabloon hebt gemaakt die als basis voor andere sjablonen kan dienen, kunt u deze sjabloon kopiëren als een sjabloontype.

1. Maak een sjabloon op dezelfde manier als een paginasjabloon. Zie [ Malplaatjes om Pagina&#39;s tot stand te brengen die met de Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/templates.md#creating-a-new-template-template-author) editable zijn. Dit zal als basis van uw malplaatjetype dienen.
1. Gebruikend CRXDE Lite, kopieer het gecreeerde malplaatje van de `templates` knoop aan de `template-types` knoop onder de [ malplaatjeomslag ](#template-folders).
1. Schrap het malplaatje van de `templates` knoop onder de [ malplaatjeomslag ](#template-folders).
1. Verwijder in de kopie van de sjabloon onder het knooppunt `template-types` alle eigenschappen `cq:template` en `cq:templateType` uit alle `jcr:content` knooppunten.

U kunt uw eigen malplaatjetype ook ontwikkelen gebruikend een voorbeeld editable malplaatje als basis, beschikbaar op GitHub.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [ open a-sites-example-custom-template-type project op GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type)
* Download het project als [ een dossier van het PIT ](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type/archive/master.zip)

## Sjabloondefinities {#template-definitions}

De definities voor editable malplaatjes worden opgeslagen [ user-defined omslagen ](#template-folders) (geadviseerd) of alternatief in `global`. Bijvoorbeeld:

* `/conf/<my-folder>/settings/wcm/templates`
* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/templates`
* `/conf/global/settings/wcm/templates`

Het hoofdknooppunt van de sjabloon is van het type `cq:Template` met een skeletstructuur van:

```xml
<template-name>
  initial
    jcr:content
      root
        <component>
        ...
        <component>
  jcr:content
    @property status
  policies
    jcr:content
      root
        @property cq:policy
        <component>
          @property cq:policy
        ...
        <component>
          @property cq:policy
  structure
    jcr:content
      root
        <component>
        ...
        <component>
      cq:responsive
        breakpoints
  thumbnail.png
```

De belangrijkste elementen zijn:

* `<template-name>`

   * ` [initial](#initial-content)`
   * `jcr:content`
   * ` [structure](#structure)`
   * ` [policies](#policies)`
   * `thumbnail.png`

### jcr:inhoud {#jcr-content}

Dit knooppunt bevat eigenschappen voor de sjabloon:

* **Naam**: `jcr:title`
* **Naam**: `status`
   * &quot;**Type**: `String`
   * **Waarde**: `draft`, `enabled` of `disabled`

### Structuur {#structure}

Hiermee definieert u de structuur van de resulterende pagina:

* Wordt bij het maken van een pagina samengevoegd met de oorspronkelijke inhoud ( `/initial` ).
* Wijzigingen in de structuur worden weerspiegeld in alle pagina&#39;s die met de sjabloon zijn gemaakt.
* Het knooppunt `root` ( `structure/jcr:content/root` ) definieert de lijst met componenten die beschikbaar zijn op de resulterende pagina.
   * Componenten die zijn gedefinieerd in de sjabloonstructuur kunnen niet worden verplaatst op of verwijderd van resulterende pagina&#39;s.
   * Nadat een component is ontgrendeld, wordt de eigenschap `editable` ingesteld op `true` .
   * Nadat een component die al inhoud bevat, is ontgrendeld, wordt deze inhoud naar de `initial` -vertakking verplaatst.

* Het knooppunt `cq:responsive` bevat definities voor de responsieve indeling.

### Oorspronkelijke inhoud {#initial-content}

Definieert de eerste inhoud die een nieuwe pagina krijgt wanneer deze wordt gemaakt:

* Bevat een knooppunt `jcr:content` dat naar nieuwe pagina&#39;s wordt gekopieerd.
* Wordt bij het maken van een pagina samengevoegd met de structuur ( `/structure` ).
* Bestaande pagina&#39;s worden niet bijgewerkt als de oorspronkelijke inhoud na het maken wordt gewijzigd.
* Het knooppunt `root` bevat een lijst met componenten om te definiëren wat beschikbaar is op de resulterende pagina.
* Als er inhoud wordt toegevoegd aan een component in de structuurmodus en die component vervolgens wordt ontgrendeld (of omgekeerd), wordt deze inhoud gebruikt als initiële inhoud.

### Layout {#layout}

Wanneer [ het uitgeven van een malplaatje u de lay-out ](/help/sites-cloud/authoring/page-editor/templates.md) kunt bepalen, gebruikt dit [ standaard ontvankelijke lay-out ](/help/sites-cloud/administering/responsive-layout.md), die [ op de pagina door de inhoudauteur ](/help/sites-cloud/authoring/page-editor/responsive-layout.md) kan worden gevormd.

### Inhoudsbeleid {#content-policies}

Het inhoudsbeleid definieert de ontwerpeigenschappen van een component. Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen. Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt). Het inhoudsbeleid kan worden gemaakt en geselecteerd in de sjablooneditor.

* De eigenschap `cq:policy` op het knooppunt `root`
  `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/root`
Verstrekt een relatieve verwijzing naar het inhoudsbeleid voor het de paragraafsysteem van de pagina.

* De eigenschap `cq:policy` biedt op de componentexpliciete knooppunten onder `root` koppelingen naar het beleid voor de afzonderlijke componenten.

* De feitelijke beleidsdefinities worden opgeslagen onder:
  `/conf/<your-folder>/settings/wcm/policies/wcm/foundation/components`

>[!NOTE]
>
>De paden van beleidsdefinities zijn afhankelijk van het pad van de component. `cq:policy` bevat een relatieve verwijzing naar de configuratie zelf.

### Paginabeleid {#page-policies}

Het beleid van de pagina staat u toe om het [ inhoudsbeleid ](#content-policies) voor de pagina (belangrijkste parsys), in of het malplaatje of de resulterende pagina&#39;s te bepalen.

### Een sjabloon inschakelen en toestaan voor gebruik {#enabling-and-allowing-a-template-for-use}

1. **laat het Malplaatje** toe

   Voordat een sjabloon kan worden gebruikt, moet deze zijn ingeschakeld door:

   * [ toelatend het malplaatje ](/help/sites-cloud/authoring/page-editor/templates.md) van de **console van Malplaatjes**.

   * Setting the status property on the `jcr:content` node.

      * Bijvoorbeeld op:

        `/conf/<your-folder>/settings/wcm/templates/<your-template>/jcr:content`

      * Definieer de eigenschap:

         * Naam: status
         * Type: String
         * Waarde: `enabled`

1. **Toegestane Malplaatjes**

   * [ bepaalt de Toegestane weg(en) van het Malplaatje op de **Eigenschappen van de Pagina**](/help/sites-cloud/authoring/page-editor/templates.md#allowing-a-template-author) van de aangewezen pagina of wortelpagina van een subtak.
   * Stel de eigenschap in:

     `cq:allowedTemplates`
Op het `jcr:content` -knooppunt van de vereiste vertakking.

   Bijvoorbeeld met een waarde van:

   `/conf/<your-folder>/settings/wcm/templates/.*`

## Resulterende inhoudspagina&#39;s {#resultant-content-pages}

Pagina&#39;s gemaakt op basis van bewerkbare sjablonen:

* Wordt gemaakt met een substructuur die wordt samengevoegd van `structure` en `initial` in de sjabloon

* Verwijzingen hebben naar in de template opgeslagen informatie en naar het sjabloontype. Dit wordt bereikt met een knooppunt `jcr:content` met de eigenschappen:

   * `cq:template` - Verstrekt de dynamische verwijzing naar het daadwerkelijke malplaatje; laat toe dat veranderingen in het malplaatje worden weerspiegeld op de daadwerkelijke pagina&#39;s.

   * `cq:templateType` - Verstrekt een verwijzing naar het malplaatjetype.

![ hoe de malplaatjes, de inhoud, en de componenten ](assets/templates-content-components.png) met elkaar in verband brengen

In het bovenstaande diagram ziet u hoe sjablonen, inhoud en componenten met elkaar verweven zijn:

* Controller - `/content/<my-site>/<my-page>` - De resulterende pagina die naar de sjabloon verwijst. De inhoud bepaalt het gehele proces. Volgens de definities heeft het toegang tot de toepasselijke sjabloon en componenten.
* Configuratie - `/conf/<my-folder>/settings/wcm/templates/<my-template>` - het [ malplaatje en verwante inhoudsbeleid ](#template-definitions) bepalen de paginasonfiguratie.
* Model - de bundels OSGi - de [ bundels OSGI ](/help/implementing/deploying/configuring-osgi.md) voeren de functionaliteit uit.
* Weergave - `/apps/<my-site>/components` - In zowel de auteur- als de publicatieomgeving wordt de inhoud gerenderd door componenten.

Bij het weergeven van een pagina:

* **Malplaatjes**:

   * De eigenschap `cq:template` van het knooppunt `jcr:content` wordt gebruikt voor toegang tot de sjabloon die overeenkomt met die pagina.

* **Componenten**:

   * De pagina-component voegt de `structure/jcr:content` -structuur van de sjabloon samen met de `jcr:content` -structuur van de pagina.
      * Met de paginacomponent kan de auteur alleen de knooppunten van de sjabloonstructuur bewerken die als bewerkbaar zijn gemarkeerd (en eventuele onderliggende knooppunten).
      * Wanneer u een component op een pagina rendert, wordt het relatieve pad van die component opgehaald uit het knooppunt `jcr:content` . Vervolgens wordt hetzelfde pad onder het knooppunt `policies/jcr:content` van de sjabloon doorzocht.
         * De eigenschap `cq:policy` van dit knooppunt verwijst naar het daadwerkelijke inhoudsbeleid (dat wil zeggen dat het de ontwerpconfiguratie voor die component bevat).
            * Dit laat u veelvoudige malplaatjes hebben die de zelfde configuraties van het inhoudsbeleid opnieuw gebruiken.

### Beschikbaarheid sjabloon {#template-availability}

Wanneer u een pagina maakt in de interface voor sitebeheer, is de lijst met beschikbare sjablonen afhankelijk van de locatie van de nieuwe pagina en de plaatsingsbeperkingen die in elke sjabloon zijn opgegeven.

De volgende eigenschappen bepalen of een sjabloon `T` mag worden gebruikt voor een nieuwe pagina die als onderliggend item van pagina `P` moet worden geplaatst. Elk van deze eigenschappen is een tekenreeks met meerdere waarden die nul of meer reguliere expressies bevat die worden gebruikt voor overeenkomsten met paden:

* De eigenschap `cq:allowedTemplates` van de `jcr:content` subnode van `P` of een voorouder van `P` .

* De eigenschap `allowedPaths` van `T` .

* De eigenschap `allowedParents` van `T` .

* De eigenschap `allowedChildren` van de sjabloon `P` .

De evaluatie werkt als volgt:

* De eerste niet-lege `cq:allowedTemplates` eigenschap die wordt gevonden terwijl de paginahiërarchie oploopt, beginnend met `P` , komt overeen met het pad van `T` . Als geen van de waarden overeenkomt, wordt `T` afgewezen.

* Als `T` een niet-lege `allowedPaths` eigenschap heeft, maar geen van de waarden overeenkomen met het pad van `P` , wordt `T` afgewezen.

* Als beide bovenstaande eigenschappen leeg of niet bestaan, wordt `T` afgewezen, tenzij het tot dezelfde toepassing behoort als `P` . `T` behoort tot dezelfde toepassing als `P` als en alleen als de naam van het tweede niveau van het pad van `T` gelijk is aan de naam van het tweede niveau van het pad van `P` . De sjabloon `/apps/wknd/templates/foo` behoort bijvoorbeeld tot dezelfde toepassing als de pagina `/content/wknd` .

* Als `T` een niet-lege `allowedParents` eigenschap heeft, maar geen van de waarden overeenkomen met het pad van `P` , wordt `T` afgewezen.

* Als de sjabloon van `P` een niet-lege eigenschap `allowedChildren` heeft, maar geen van de waarden overeenkomen met het pad van `T` , wordt `T` afgewezen.

* In alle andere gevallen is `T` toegestaan.

Het volgende diagram toont het sjabloonevaluatieproces:

![ het evaluatieproces van het Malplaatje ](assets/template-evaluation.png)

>[!CAUTION]
>
>AEM biedt veelvoudige eigenschappen aan om de malplaatjes te controleren die onder **Plaatsen** worden toegestaan. Het combineren van deze regels kan echter leiden tot zeer complexe regels die moeilijk te volgen en te beheren zijn.
>
>Daarom adviseert de Adobe dat u eenvoudig begint, door te bepalen:
>
>* alleen de eigenschap `cq:allowedTemplates`
>
>* alleen in de hoofdmap van de site
>
>Voor een voorbeeld, zie de [ WKND leerprogramma ](/help/implementing/developing/introduction/develop-wknd-tutorial.md) inhoud: `/content/wknd/jcr:content`
>
>De eigenschappen `allowedPaths`, `allowedParents` en `allowedChildren` kunnen ook op de sjablonen worden geplaatst om geavanceerdere regels te definiëren. Nochtans, waar mogelijk, is het veel *eenvoudiger om verdere `cq:allowedTemplates` eigenschappen op subsecties van de plaats te bepalen als er een behoefte is om de toegestane malplaatjes verder te beperken.*
>
>Een extra voordeel is dat de `cq:allowedTemplates` eigenschappen door een auteur op het **Geavanceerde** lusje van de **Eigenschappen van de Pagina** kunnen worden bijgewerkt. De andere malplaatjeeigenschappen kunnen niet worden bijgewerkt gebruikend (standaard) UI, zodat zou een ontwikkelaar nodig hebben om de regels en een codeplaatsing voor elke verandering te handhaven.

#### Sjablonen beperken die worden gebruikt in onderliggende pagina&#39;s {#limiting-templates-used-in-child-pages}

Als u wilt beperken welke sjablonen kunnen worden gebruikt om onderliggende pagina&#39;s onder een bepaalde pagina te maken, gebruikt u de eigenschap `cq:allowedTemplates` van het knooppunt `jcr:content` van de pagina om de lijst met sjablonen op te geven die als onderliggende pagina&#39;s moeten worden toegestaan. Elke waarde in de lijst moet een absoluut pad zijn naar een sjabloon voor een toegestane onderliggende pagina, bijvoorbeeld `/apps/wknd/templates/page-content` .

U kunt de eigenschap `cq:allowedTemplates` op het knooppunt `jcr:content` van de sjabloon gebruiken om deze configuratie toe te passen op alle gemaakte pagina&#39;s die deze sjabloon gebruiken.

Als u meer beperkingen wilt toevoegen, bijvoorbeeld met betrekking tot de sjabloonhiërarchie, kunt u de eigenschappen `allowedParents/allowedChildren` op de sjabloon gebruiken. U kunt dan uitdrukkelijk specificeren dat de pagina&#39;s die van een malplaatjeT worden gecreeerd ouderpagina/kinderen van pagina&#39;s moeten zijn die van een malplaatjeT worden gecreeerd.
