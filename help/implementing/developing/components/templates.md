---
title: Paginasjablonen
description: Paginasjablonen worden gebruikt bij het maken van een pagina die wordt gebruikt als basis voor de nieuwe pagina
translation-type: tm+mt
source-git-commit: 73e7f9a5b0976ebd5228c182d47c1058290f7629
workflow-type: tm+mt
source-wordcount: '3296'
ht-degree: 0%

---


# Paginasjablonen {#page-templates}

Wanneer u een pagina maakt, moet u een sjabloon selecteren. De paginasjabloon wordt gebruikt als basis voor de nieuwe pagina. De sjabloon definieert de structuur van de resulterende pagina, eventuele initiële inhoud en de componenten die kunnen worden gebruikt (ontwerpeigenschappen). Dit heeft verschillende voordelen:

* Met paginasjablonen kunnen gespecialiseerde auteurs [sjablonen maken en bewerken](/help/sites-cloud/authoring/features/templates.md).
   * Dergelijke gespecialiseerde auteurs worden **sjabloonauteurs** genoemd
   * Sjabloonauteurs moeten lid zijn van de groep `template-authors`.
* Paginasjablonen behouden een dynamische verbinding met alle pagina&#39;s die daaruit zijn gemaakt. Zo zorgt u ervoor dat wijzigingen in de sjabloon ook op de pagina&#39;s zelf worden doorgevoerd.
* Met paginasjablonen wordt de paginacomponent generischer, zodat de basispaginacomponent zonder aanpassing kan worden gebruikt.

Met paginasjablonen worden de onderdelen die een pagina maken, geïsoleerd in onderdelen. U kunt de noodzakelijke combinaties componenten in een UI vormen, daardoor eliminerend de behoefte aan een nieuwe paginacomponent die voor elke paginariatie moet worden ontwikkeld.

Dit document:

* Geeft een overzicht van het maken van een paginasjabloon
* Beschrijft de admin/ontwikkelaarstaken die worden vereist om editable malplaatjes tot stand te brengen
* Beschrijft de technische onderbouwing van editable malplaatjes
* Beschrijft hoe AEM de beschikbaarheid van een malplaatje evalueert

>[!NOTE]
>
>In dit document wordt ervan uitgegaan dat u vertrouwd bent met het maken en bewerken van sjablonen. Zie het ontwerpdocument [Paginasjablonen maken](/help/sites-cloud/authoring/features/templates.md), waarin de mogelijkheden van bewerkbare sjablonen worden beschreven zoals deze aan de sjabloonauteur worden getoond.

>[!TIP]
>
>[De WKND-](/help/implementing/developing/introduction/develop-wknd-tutorial.md) zelfstudie gaat diepgaand in hoe u paginasjablonen kunt gebruiken door een voorbeeld te implementeren. Deze zelfstudie is erg handig voor het begrijpen van hoe u een sjabloon kunt instellen in een nieuw project

## Een nieuwe sjabloon maken {#creating-a-new-template}

Het creëren van de Malplaatjes van de Pagina wordt hoofdzakelijk gedaan met [malplaatjeconsole en malplaatjeredacteur](/help/sites-cloud/authoring/features/templates.md) door een malplaatjeauteur. In deze paragraaf wordt een overzicht gegeven van dit proces en wordt een beschrijving gegeven van wat er op technisch niveau gebeurt.

Bij het maken van een nieuwe bewerkbare sjabloon:

1. Maak een [map voor de sjablonen](#template-folders). Dit is niet verplicht, maar aanbevolen beste praktijken.
1. Selecteer een [sjabloontype](#template-type). Dit wordt gekopieerd om [malplaatjedefinitie](#template-definitions) tot stand te brengen.

   >[!NOTE]
   >
   >Een selectie van sjabloontypen is beschikbaar buiten het vak. U kunt desgewenst ook [uw eigen sitespecifieke sjabloontypen maken](#creating-template-types).

1. Vorm de structuur, inhoudsbeleid, aanvankelijke inhoud, en lay-out van het nieuwe malplaatje.

   **Structuur**

   * Met de structuur kunt u componenten en inhoud voor de sjabloon definiëren.
   * Componenten die in de sjabloonstructuur zijn gedefinieerd, kunnen niet op een resulterende pagina worden verplaatst of uit resulterende pagina&#39;s worden verwijderd.
   * Als u wilt dat auteurs van pagina&#39;s componenten kunnen toevoegen en verwijderen, voegt u een alineasysteem toe aan de sjabloon.
   * Componenten kunnen worden ontgrendeld en opnieuw worden vergrendeld, zodat u de initiële inhoud kunt definiëren.

   Zie [Paginasjablonen maken](/help/sites-cloud/authoring/features/templates.md#editing-a-template-structure-template-author) voor meer informatie over de manier waarop een sjabloonauteur de structuur definieert.

   Zie [Structuur](#structure) in dit document voor technische details over de structuur.

   **Beleid**

   * Het inhoudsbeleid definieert de ontwerpeigenschappen van een component.

      * Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen.
   * Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

   Zie [Paginasjablonen maken](/help/sites-cloud/authoring/features/templates.md#editing-a-template-structure-template-author) voor meer informatie over hoe een sjabloonauteur beleid definieert.

   Voor technische details van beleid, zie [Inhoudsbeleid](#content-policies) in dit document.

   **Oorspronkelijke inhoud**

   * Met Eerste inhoud wordt inhoud gedefinieerd die wordt weergegeven wanneer een pagina voor het eerst wordt gemaakt op basis van de sjabloon.
   * De initiële inhoud kan vervolgens worden bewerkt door auteurs van pagina&#39;s.

   Zie [Paginasjablonen maken](/help/sites-cloud/authoring/features/templates.md#editing-a-template-initial-content-author) voor meer informatie over de manier waarop een sjabloonauteur de structuur definieert.

   Zie [Initiële inhoud](#initial-content) in dit document voor technische details over de initiële inhoud.

   **Indeling**

   * U kunt de sjabloonlay-out voor een reeks apparaten definiëren.
   * De responsieve indeling voor sjablonen werkt op dezelfde manier als voor het ontwerpen van pagina&#39;s.

   Zie [Paginasjablonen maken](/help/sites-cloud/authoring/features/templates.md#editing-a-template-layout-template-author) voor meer informatie over hoe de sjabloonauteur de sjabloonlay-out definieert.

   Zie [Layout](#layout) in dit document voor technische details over sjabloonlay-out.

1. Schakel de sjabloon in en sta deze vervolgens toe voor specifieke inhoudstructuren.

   * U kunt een sjabloon in- of uitschakelen om de sjabloon beschikbaar of niet beschikbaar te maken voor auteurs van pagina&#39;s.
   * Een sjabloon kan beschikbaar worden gesteld of niet beschikbaar zijn voor bepaalde paginasvertakkingen.

   Zie [Paginasjablonen maken](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author) voor meer informatie over hoe een sjabloonauteur een sjabloon inschakelt.

   Voor technische details bij het toelaten van een malplaatje, zie [Het toelaten van en het Toestaan van een Malplaatje voor Gebruik](#enabling-and-allowing-a-template-for-use)e in dit document

1. Gebruik dit besturingselement om inhoudspagina&#39;s te maken.

   * Wanneer u een sjabloon gebruikt om een nieuwe pagina te maken, is er geen zichtbaar verschil en is er geen indicatie tussen statische en bewerkbare sjablonen.
   * Voor de auteur van de pagina is het proces transparant.

   Zie [Pagina&#39;s maken en ordenen](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#templates) voor meer informatie over hoe een auteur van een pagina sjablonen gebruikt om een pagina te maken.

   Zie [Resulterende inhoudspagina&#39;s](#resultant-content-pages) in dit document voor technische details over het maken van pagina&#39;s met bewerkbare sjablonen.

>[!TIP]
>
>Voer nooit informatie in die u wilt internationaliseren in een sjabloon. Voor internalisatiedoeleinden worden de [lokalisatiefuncties van de Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html) aanbevolen.

>[!NOTE]
>
>Sjablonen zijn krachtige gereedschappen om de workflow voor het maken van pagina&#39;s te stroomlijnen. Te veel sjablonen kunnen de auteurs echter overweldigen en tot verwarring bij het maken van pagina&#39;s leiden. Een goede regel is om het aantal sjablonen onder de 100 te houden.
>
>Adobe adviseert niet om meer dan 1000 malplaatjes wegens potentiële prestatiesgevolgen te hebben.

>[!NOTE]
>
>In de clientbibliotheek van de editor wordt ervan uitgegaan dat de naamruimte `cq.shared` aanwezig is op inhoudspagina&#39;s. Als deze ontbreekt, resulteert de JavaScript-fout `Uncaught TypeError: Cannot read property 'shared' of undefined`.
>
>Alle pagina&#39;s met voorbeeldinhoud bevatten `cq.shared`, dus alle inhoud die hierop is gebaseerd, bevat automatisch `cq.shared`. Als u echter besluit uw eigen inhoudspagina&#39;s helemaal zelf te maken zonder deze op voorbeeldinhoud te baseren, moet u de naamruimte `cq.shared` invoegen.
>
>Zie [Client-Side Libraries](/help/implementing/developing/introduction/clientlibs.md) gebruiken voor meer informatie.



## Sjabloonmappen {#template-folders}

Voor het organiseren van uw sjablonen kunt u de volgende mappen gebruiken:

* `global`
* Sitespecifiek

>[!NOTE]
>
>Hoewel u uw omslagen kunt nesten, wanneer de gebruiker hen in **Templates** console bekijkt, worden zij voorgesteld als vlakke structuur.

In een standaardinstelling AEM de map `global` bestaat al in de sjabloonconsole. Dit houdt standaardmalplaatjes vast en doet dienst als reserve als geen beleid en/of malplaatje-types in de huidige omslag worden gevonden. U kunt uw standaardsjablonen toevoegen aan deze map of een nieuwe map maken (aanbevolen).

>[!NOTE]
>
>Het wordt aanbevolen een nieuwe map te maken waarin uw aangepaste sjablonen staan en de map `global` niet te gebruiken.

>[!CAUTION]
>
>Mappen moeten worden gemaakt door een gebruiker met `admin` rechten.

Sjabloontypen en beleid worden in alle mappen overgeërfd volgens de volgende prioriteitsvolgorde:

1. De huidige map
1. Bovenliggend item of bovenliggende items van de huidige map
1. `/conf/global`
1. `/apps`
1. `/libs`

Er wordt een lijst met alle toegestane vermeldingen gemaakt. Als configuraties elkaar overlappen ( `path`/ `label`), wordt alleen de instantie die zich het dichtst bij de huidige map bevindt, aan de gebruiker getoond.

Als u een nieuwe map wilt maken, kunt u het volgende doen:

* Programmaticaal of met CRXDE Lite
* Het gebruiken van [Browser van de Configuratie](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)

## CRXDE Lite {#using-crxde-lite} gebruiken

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
   * Waarde: De titel (voor de map) die u wilt weergeven in de console **Sjablonen**.

1. Naast de standaardmachtigingen en -bevoegdheden (bijvoorbeeld `content-authors`) moet u nu groep(en) toewijzen en de vereiste toegangsrechten (ACL&#39;s) definiëren voor uw auteurs om sjablonen in de nieuwe map te kunnen maken.

   De `template-authors` groep is de standaardgroep die moet worden toegewezen. Zie de sectie [ACLs en Groepen](#acls-and-groups) voor details.

   <!--See [Access Right Management](/help/sites-administering/user-group-ac-admin.md#access-right-management) for full details on managing and assigning access rights.-->

### De configuratiebrowser gebruiken {#using-the-configuration-browser}

1. Ga naar **Algemene navigatie** -> **Gereedschappen** > [**Configuratiebrowser**.](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)

   De bestaande mappen worden links weergegeven, inclusief de map `global`.

1. Klik **Maken**.
1. In het **Create Configuratie** dialoog moeten de volgende gebieden worden gevormd:

   * **Titel**: Geef een titel op voor de configuratiemap
   * **Bewerkbare sjablonen**: Tik om bewerkbare sjablonen toe te staan in deze map

1. Klik **Maken**

>[!NOTE]
>
>In [de Browser van de Configuratie, ](/help/implementing/developing/introduction/configurations.md#using-configuration-browser) kunt u de globale omslag uitgeven en **Bewerkbare Malplaatjes activeren** optie als u wenst om malplaatjes binnen deze omslag tot stand te brengen, nochtans wordt dit niet geadviseerd beste praktijken.

### ACLs en Groepen {#acls-and-groups}

Zodra uw malplaatjeomslagen (of via CRXDE of met Browser van de Configuratie) worden gecreeerd, moet ACLs voor de aangewezen groepen voor de malplaatjeomslagen worden bepaald om juiste veiligheid te verzekeren.

De malplaatjeomslagen voor [WKND leerprogramma](/help/implementing/developing/introduction/develop-wknd-tutorial.md) kunnen als voorbeeld worden gebruikt.

#### The template-authors Group {#the-template-authors-group}

De `template-authors` groep is de groep die wordt gebruikt om toegang tot malplaatjes te beheren en komt standaard met AEM, maar is leeg. Gebruikers moeten worden toegevoegd aan de groep voor het project of de site.

>[!CAUTION]
>
>De groep `template-authors` is alleen voor gebruikers die nieuwe sjablonen moeten kunnen maken.
>
>Het bewerken van sjablonen is bijzonder krachtig en als dit niet het geval is, kunnen bestaande sjablonen worden verbroken. Daarom moet deze rol worden toegespitst en alleen gekwalificeerde gebruikers omvatten.

In de volgende tabel worden de benodigde machtigingen voor sjabloonbewerking weergegeven.

<table>
 <tbody>
  <tr>
   <th>Pad</th>
   <th>Rol/groep</th>
   <th>Machtigingen<br /> </th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/templates</code></td>
   <td>Sjabloonauteurs<br /> </td>
   <td>lezen, schrijven, repliceren</td>
   <td>Sjabloonauteurs die sjablonen maken, lezen, bijwerken, verwijderen en repliceren in sitespecifieke <code>/conf</code>-ruimte</td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>read</td>
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
   <td>Sjabloonauteurs die sjablonen maken, lezen, bijwerken, verwijderen en repliceren in sitespecifieke <code>/conf</code>-ruimte</td>
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

Deze standaard `template-authors` groep behandelt slechts de projectmontages, waar alle `template-authors` leden tot toegang hebben en alle malplaatjes mogen schrijven. Voor complexere montages, waar de veelvoudige groepen van malplaatjeauteurs nodig zijn om toegang tot malplaatjes te scheiden, moeten meer de auteursgroepen van het douanemalplaatje worden gecreeerd. De machtigingen voor de groepen sjabloonauteurs zijn echter nog steeds hetzelfde.

## Sjabloontype {#template-type}

Wanneer u een nieuwe sjabloon maakt, moet u een sjabloontype opgeven:

* Sjabloontypen bieden sjablonen voor een sjabloon. Wanneer u een nieuwe sjabloon maakt, worden de structuur en initiële inhoud van het geselecteerde sjabloontype gebruikt om aan de nieuwe sjabloon te maken.

   * Het sjabloontype wordt gekopieerd om de sjabloon te maken.
   * Zodra het exemplaar is voorgekomen, is de enige verbinding tussen het malplaatje en het malplaatjetype een statische verwijzing voor informatiedoeleinden.

* Met sjabloontypen kunt u het volgende definiëren:

   * Het middeltype van de paginacomponent.
   * Het beleid van de wortelknoop, die de componenten bepaalt die in de malplaatjeredacteur worden toegestaan.
   * Het wordt aanbevolen de onderbrekingspunten voor het responsieve raster en de instelling van de mobiele emulator op te geven voor het sjabloontype.

* AEM biedt een kleine selectie van out-of-box sjabloontypen, zoals HTML5 Page en Adaptive Form Page.

   * Aanvullende voorbeelden worden gegeven als onderdeel van de [WKND-zelfstudie.](/help/implementing/developing/introduction/develop-wknd-tutorial.md)

* Sjabloontypen worden meestal gedefinieerd door ontwikkelaars.

De sjabloontypen voor de out-of-the-box worden opgeslagen onder:

* `/libs/settings/wcm/template-types`

>[!CAUTION]
>
>U mag niets in de `/libs` weg veranderen. De reden hiervoor is dat de inhoud van `/libs` op elk moment kan worden overschreven door een update naar AEM.

Uw sitespecifieke sjabloontypen moeten worden opgeslagen op de vergelijkbare locatie:

* `/apps/settings/wcm/template-types`

De definities voor uw aangepaste malplaatjetypes zouden in user-defined omslagen (geadviseerd) of anders in `global` moeten worden opgeslagen. Bijvoorbeeld:

* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/template-types`
* `/conf/<my-folder>/settings/wcm/template-types`
* `/conf/global/settings/wcm/template-types`

>[!CAUTION]
>
>De sjabloontypen moeten de juiste mapstructuur in acht nemen (d.w.z. `/settings/wcm/...`), anders worden de sjabloontypen niet gevonden.

<!--
### Template Type and Mobile Device Groups {#template-type-and-mobile-device-groups-br}

The [device groups](/help/sites-developing/mobile.md#device-groups) used for an editable template (set as relative path of the property `cq:deviceGroups`) define which mobile devices are available as emulators in the [layout mode](/help/sites-authoring/responsive-layout.md) of page authoring. This value can be set in two places:

* On the editable template type
* On the editable template

When creating a new editable template, the value is copied from the template type to the individual template. If the value is not set on the type, it can be set on the template. Once a template is created, there is no inheritance from the type to the template.

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

1. Creeer een malplaatje zoals u om het even welk Malplaatje [zoals hier beschreven](/help/sites-cloud/authoring/features/templates.md#creating-a-new-template-template-author), die als basis van uw malplaatjetype zal dienen.
1. Met CRXDE Lite kopieert u de nieuw gemaakte sjabloon van de `templates`-node naar de `template-types`-node onder de [sjabloonmap](#template-folders).
1. Verwijder de sjabloon uit het knooppunt `templates` onder de sjabloonmap [a2/>.](#template-folders)
1. Verwijder in de kopie van de sjabloon onder het knooppunt `template-types` alle `cq:template`- en `cq:templateType` `jcr:content`-eigenschappen.

U kunt uw eigen malplaatjetype ook ontwikkelen gebruikend een voorbeeld editable malplaatje als basis, beschikbaar op GitHub.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open a-plaatsen-voorbeeld-douane-malplaatje-type project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type/archive/master.zip)

## Sjabloondefinities {#template-definitions}

Definities voor bewerkbare sjablonen worden [door de gebruiker gedefinieerde mappen](#template-folders) (aanbevolen) of `global` opgeslagen. Bijvoorbeeld:

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

### jcr:content {#jcr-content}

Dit knooppunt bevat eigenschappen voor de sjabloon:

* **Naam**:  `jcr:title`
* **Naam**:  `status`
   * &quot;**Type**: `String`
   * **Waarde**:  `draft`,  `enabled` of  `disabled`

### Structuur {#structure}

Hiermee definieert u de structuur van de resulterende pagina:

* Wordt samengevoegd met de oorspronkelijke inhoud ( `/initial`) bij het maken van een nieuwe pagina.
* Wijzigingen in de structuur worden weerspiegeld in alle pagina&#39;s die met de sjabloon worden gemaakt.
* Het `root` ( `structure/jcr:content/root`) knoop bepaalt de lijst van componenten die in de resulterende pagina beschikbaar zullen zijn.
   * Componenten die zijn gedefinieerd in de sjabloonstructuur kunnen niet worden verplaatst op of verwijderd van resulterende pagina&#39;s.
   * Wanneer een component is ontgrendeld, wordt de eigenschap `editable` ingesteld op `true`.
   * Wanneer een component die al inhoud bevat, is ontgrendeld, wordt deze inhoud naar de `initial`-vertakking verplaatst.

* Het `cq:responsive` knooppunt bevat definities voor de responsieve lay-out.

### Eerste inhoud {#initial-content}

Definieert de eerste inhoud die een nieuwe pagina krijgt wanneer deze wordt gemaakt:

* Bevat een `jcr:content`-knooppunt dat naar nieuwe pagina&#39;s wordt gekopieerd.
* Wordt samengevoegd met de structuur ( `/structure`) bij het maken van een nieuwe pagina.
* Bestaande pagina&#39;s worden niet bijgewerkt als de oorspronkelijke inhoud na het maken wordt gewijzigd.
* Het knooppunt `root` bevat een lijst met componenten om te definiëren wat beschikbaar is op de resulterende pagina.
* Als er inhoud wordt toegevoegd aan een component in de structuurmodus en die component vervolgens wordt ontgrendeld (of vice versa), wordt deze inhoud gebruikt als initiële inhoud.

### Indeling {#layout}

Als u een sjabloon [bewerkt, kunt u de layout](/help/sites-cloud/authoring/features/templates.md) definiëren, gebruikt u [responsieve standaardlay-out](/help/sites-cloud/authoring/features/responsive-layout.md).

<!-- that can also be [configured](/help/sites-administering/configuring-responsive-layout.md). -->

### Inhoudsbeleid {#content-policies}

Het inhoudsbeleid definieert de ontwerpeigenschappen van een component. Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen. Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt). Het inhoudsbeleid kan worden gemaakt en geselecteerd in de sjablooneditor.

* De eigenschap `cq:policy` op het knooppunt `root`
   `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/root`
Verstrekt een relatieve verwijzing naar het inhoudsbeleid voor het de paragraafsysteem van de pagina.

* De eigenschap `cq:policy`, op de componentexpliciete knooppunten onder `root`, biedt koppelingen naar het beleid voor de afzonderlijke componenten.

* De feitelijke beleidsdefinities worden opgeslagen onder:
   `/conf/<your-folder>/settings/wcm/policies/wcm/foundation/components`

>[!NOTE]
>
>De paden van beleidsdefinities zijn afhankelijk van het pad van de component. `cq:policy` bevat een relatieve verwijzing naar de configuratie zelf.

### Paginabeleid {#page-policies}

Het beleid van de pagina staat u toe om [inhoudsbeleid](#content-policies) voor de pagina (belangrijkste parsys), in of het malplaatje of resulterende pagina&#39;s te bepalen.

### Een sjabloon inschakelen en toestaan voor gebruik {#enabling-and-allowing-a-template-for-use}

1. **Sjabloon inschakelen**

   Voordat een sjabloon kan worden gebruikt, moet deze zijn ingeschakeld door:

   * [Het toelaten van het ](/help/sites-cloud/authoring/features/templates.md) malplaatje van  **** Templatesconsole.

   * Setting the status property on the `jcr:content` node.

      * Bijvoorbeeld op:
         `/conf/<your-folder>/settings/wcm/templates/<your-template>/jcr:content`

      * Definieer de eigenschap:

         * Naam: status
         * Type: String
         * Waarde: `enabled`

1. **Toegestane sjablonen**

   * [Definieer de toegestane sjabloonpaden op de  **Pagina-**](/help/sites-cloud/authoring/features/templates.md#allowing-a-template-author) eigenschappen van de desbetreffende pagina of basispagina van een subvertakking.
   * Stel de eigenschap in:
      `cq:allowedTemplates`
Op de 
`jcr:content` knooppunt van de vereiste vertakking.
   Bijvoorbeeld met een waarde van:

   `/conf/<your-folder>/settings/wcm/templates/.*`

## Resulterende inhoudspagina&#39;s {#resultant-content-pages}

Pagina&#39;s die zijn gemaakt op basis van bewerkbare sjablonen:

* Wordt gemaakt met een substructuur die uit `structure` en `initial` in de sjabloon is samengevoegd

* Verwijzingen hebben naar in de template opgeslagen informatie en naar het sjabloontype. Dit wordt bereikt met een `jcr:content` knoop met de eigenschappen:

   * `cq:template` - Verstrekt de dynamische verwijzing naar het daadwerkelijke malplaatje; Hiermee kunnen wijzigingen in de sjabloon op de werkelijke pagina&#39;s worden weergegeven.

   * `cq:templateType` - Verstrekt een verwijzing naar het malplaatjetype.

![Hoe sjablonen, inhoud en componenten met elkaar samenhangen](assets/templates-content-components.png)

In het bovenstaande diagram ziet u hoe sjablonen, inhoud en componenten met elkaar verweven zijn:

* Controller - `/content/<my-site>/<my-page>` - De resulterende pagina die naar de sjabloon verwijst. De inhoud bepaalt het gehele proces. Volgens de definities heeft het toegang tot de toepasselijke sjabloon en componenten.
* Configuratie - `/conf/<my-folder>/settings/wcm/templates/<my-template>` - De [sjabloon en het verwante inhoudsbeleid](#template-definitions) bepalen de paginasonfiguratie.
* Model - OSGi-bundels - De [OSGI-bundels](/help/implementing/deploying/configuring-osgi.md) implementeren de functionaliteit.
* Weergave - `/apps/<my-site>/components` - In zowel de auteur- als de publicatieomgeving wordt de inhoud gerenderd door componenten.

Bij het weergeven van een pagina:

* **Sjablonen**:

   * De eigenschap `cq:template` van het `jcr:content`-knooppunt wordt gebruikt voor toegang tot de sjabloon die overeenkomt met die pagina.

* **Onderdelen**:

   * De paginacomponent voegt de `structure/jcr:content` boom van het malplaatje met `jcr:content` boom van de pagina samen.
      * Met de paginacomponent kan de auteur alleen de knooppunten van de sjabloonstructuur bewerken die als bewerkbaar zijn gemarkeerd (en eventuele onderliggende knooppunten).
      * Bij het renderen van een component op een pagina wordt het relatieve pad van die component overgenomen uit het knooppunt `jcr:content`; hetzelfde pad onder het knooppunt `policies/jcr:content` van de sjabloon wordt vervolgens doorzocht.
         * De eigenschap `cq:policy` van dit knooppunt verwijst naar het daadwerkelijke inhoudsbeleid (de ontwerpconfiguratie voor die component is dus beschikbaar).
            * Dit staat u toe om veelvoudige malplaatjes te hebben die de zelfde configuraties van het inhoudsbeleid opnieuw gebruiken.

### Beschikbaarheid van sjabloon {#template-availability}

Wanneer u een nieuwe pagina maakt in de interface voor sitebeheer, is de lijst met beschikbare sjablonen afhankelijk van de locatie van de nieuwe pagina en de plaatsingsbeperkingen die in elke sjabloon zijn opgegeven.

De volgende eigenschappen bepalen of een sjabloon `T` mag worden gebruikt voor een nieuwe pagina die als onderliggend item van pagina `P` moet worden geplaatst. Elk van deze eigenschappen is een tekenreeks met meerdere waarden die nul of meer reguliere expressies bevat die worden gebruikt voor overeenkomsten met paden:

* De eigenschap `cq:allowedTemplates` van het `jcr:content`-subknooppunt van `P` of een voorouder van `P`.

* De eigenschap `allowedPaths` van `T`.

* De eigenschap `allowedParents` van `T`.

* De eigenschap `allowedChildren` van de sjabloon `P`.

De evaluatie werkt als volgt:

* De eerste niet-lege `cq:allowedTemplates`-eigenschap die wordt gevonden terwijl de paginahiërarchie oploopt, beginnend met `P`, wordt vergeleken met het pad van `T`. Als geen van de waarden overeenkomt, wordt `T` geweigerd.

* Als `T` een niet-lege `allowedPaths` eigenschap heeft, maar geen van de waarden komt overeen met het pad van `P`, wordt `T` afgewezen.

* Als beide bovenstaande eigenschappen leeg of niet bestaan, wordt `T` geweigerd, tenzij het tot dezelfde toepassing behoort als `P`. `T` behoort tot dezelfde toepassing als  `P` alleen als de naam van het tweede niveau van het pad van dezelfde  `T` is als de naam van het tweede niveau van het pad van  `P`. De sjabloon `/apps/wknd/templates/foo` behoort bijvoorbeeld tot dezelfde toepassing als de pagina `/content/wknd`.

* Als `T` een niet-lege `allowedParents` eigenschap heeft, maar geen van de waarden komt overeen met het pad van `P`, wordt `T` afgewezen.

* Als de sjabloon van `P` een niet-lege `allowedChildren` eigenschap heeft, maar geen van de waarden komt overeen met het pad van `T`, wordt `T` afgewezen.

* In alle andere gevallen is `T` toegestaan.

Het volgende diagram toont het sjabloonevaluatieproces:

![Sjabloonevaluatieproces](assets/template-evaluation.png)

>[!CAUTION]
>
>AEM biedt veelvoudige eigenschappen aan om de malplaatjes te controleren die onder **Plaatsen** worden toegestaan. Het combineren ervan kan echter leiden tot zeer complexe regels die moeilijk te volgen en te beheren zijn.
>
>Daarom adviseert Adobe dat u eenvoudig begint, door te bepalen:
>
>* alleen de eigenschap `cq:allowedTemplates`
   >
   >
* alleen in de hoofdmap van de site
>
>
Zie voor een voorbeeld de [WKND-zelfstudie](/help/implementing/developing/introduction/develop-wknd-tutorial.md)-inhoud: `/content/wknd/jcr:content`
>
>De eigenschappen `allowedPaths`, `allowedParents`, en `allowedChildren` kunnen ook op de malplaatjes worden geplaatst om verfijndere regels te bepalen. Waar mogelijk is het *veel* eenvoudiger om verdere `cq:allowedTemplates` eigenschappen op subsecties van de site te definiëren als de toegestane sjablonen verder moeten worden beperkt.
>
>Een extra voordeel is dat de `cq:allowedTemplates` eigenschappen door een auteur op **Geavanceerd** lusje van **Pagina-eigenschappen** kunnen worden bijgewerkt. De andere malplaatjeeigenschappen kunnen niet worden bijgewerkt gebruikend (standaard) UI, zodat zou een ontwikkelaar nodig hebben om de regels en een codeplaatsing voor elke verandering te handhaven.

#### Sjablonen beperken die worden gebruikt op onderliggende pagina&#39;s {#limiting-templates-used-in-child-pages}

Om te beperken welke malplaatjes kunnen worden gebruikt om kindpagina&#39;s onder een bepaalde pagina tot stand te brengen, gebruik `cq:allowedTemplates` bezit van `jcr:content` knoop van de pagina om de lijst van malplaatjes te specificeren die als kindpagina&#39;s moeten worden toegestaan. Elke waarde in de lijst moet een absoluut pad zijn naar een sjabloon voor een toegestane onderliggende pagina, bijvoorbeeld `/apps/wknd/templates/page-content`.

U kunt het `cq:allowedTemplates` bezit op de `jcr:content` knoop van het malplaatje gebruiken om deze configuratie toe te passen op alle pas gecreëerde pagina&#39;s die dit malplaatje gebruiken.

Als u meer beperkingen wilt toevoegen, bijvoorbeeld met betrekking tot de sjabloonhiërarchie, kunt u de eigenschappen `allowedParents/allowedChildren` op de sjabloon gebruiken. U kunt dan uitdrukkelijk specificeren dat de pagina&#39;s die van een malplaatjeT worden gecreeerd ouderpagina/kinderen van pagina&#39;s moeten zijn die van een malplaatjeT worden gecreeerd.
