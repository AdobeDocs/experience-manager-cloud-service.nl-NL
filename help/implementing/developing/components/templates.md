---
title: Paginasjablonen
description: Paginasjablonen worden gebruikt bij het maken van een pagina die als basis voor de nieuwe pagina wordt gebruikt
exl-id: ea42fce9-9af2-4349-a4e4-547e6e8da05c
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '3267'
ht-degree: 0%

---

# Paginasjablonen {#page-templates}

Wanneer u een pagina maakt, moet u een sjabloon selecteren. De paginasjabloon wordt gebruikt als basis voor de nieuwe pagina. De sjabloon definieert de structuur van de resulterende pagina, eventuele initiële inhoud en de componenten die kunnen worden gebruikt (ontwerpeigenschappen). Dit heeft verschillende voordelen:

* Met paginasjablonen kunnen gespecialiseerde auteurs [sjablonen maken en bewerken](/help/sites-cloud/authoring/sites-console/templates.md).
   * Dergelijke gespecialiseerde auteurs worden genoemd **sjabloonauteurs**
   * Sjabloonauteurs moeten lid zijn van de `template-authors` groep.
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
>In dit document wordt ervan uitgegaan dat u vertrouwd bent met het maken en bewerken van sjablonen. Zie het ontwerpdocument [Paginasjablonen maken](/help/sites-cloud/authoring/sites-console/templates.md), waarin de mogelijkheden van bewerkbare sjablonen worden beschreven zoals deze aan de sjabloonauteur worden getoond.

>[!TIP]
>
>[De WKND-zelfstudie](/help/implementing/developing/introduction/develop-wknd-tutorial.md) gaat diepgaand in hoe te om de Malplaatjes van de Pagina te gebruiken door een voorbeeld uit te voeren en is vrij nuttig voor het begrip hoe te opstelling een malplaatje in een nieuw project

## Een nieuwe sjabloon maken {#creating-a-new-template}

Het maken van paginasjablonen gebeurt vooral met de opdracht [sjabloonconsole en sjablooneditor](/help/sites-cloud/authoring/sites-console/templates.md) door een sjabloonauteur. In deze paragraaf wordt een overzicht gegeven van dit proces en wordt een beschrijving gegeven van wat er op technisch niveau gebeurt.

Bij het maken van een bewerkbare sjabloon:

1. Een [map voor de sjablonen](#template-folders). Dit is niet verplicht, maar aanbevolen beste praktijken.
1. Selecteer een [sjabloontype](#template-type). Deze wordt gekopieerd om de [sjabloondefinitie](#template-definitions).

   >[!NOTE]
   >
   >Een selectie van sjabloontypen is beschikbaar buiten het vak. U kunt [uw eigen sitespecifieke sjabloontypen maken](#creating-template-types) indien nodig.

1. Vorm de structuur, inhoudsbeleid, aanvankelijke inhoud, en lay-out van het nieuwe malplaatje.

   **Structuur**

   * Met de structuur kunt u componenten en inhoud voor de sjabloon definiëren.
   * Componenten die in de sjabloonstructuur zijn gedefinieerd, kunnen niet op een resulterende pagina worden verplaatst of uit resulterende pagina&#39;s worden verwijderd.
   * Als u wilt dat auteurs van pagina&#39;s componenten kunnen toevoegen en verwijderen, voegt u een alineasysteem toe aan de sjabloon.
   * Componenten kunnen worden ontgrendeld en opnieuw worden vergrendeld, zodat u de initiële inhoud kunt definiëren.

   Zie voor meer informatie over de manier waarop een sjabloonauteur de structuur definieert [Paginasjablonen maken](/help/sites-cloud/authoring/sites-console/templates.md#editing-a-template-structure-template-author).

   Voor technische details van de structuur, zie [Structuur](#structure) in dit document.

   **Beleid**

   * Het inhoudsbeleid definieert de ontwerpeigenschappen van een component.

      * Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen.

   * Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

   Zie voor meer informatie over hoe een sjabloonauteur beleid definieert [Paginasjablonen maken](/help/sites-cloud/authoring/sites-console/templates.md#editing-a-template-structure-template-author).

   Voor technische details van het beleid raadpleegt u [Inhoudsbeleid](#content-policies) in dit document.

   **Oorspronkelijke inhoud**

   * Met Eerste inhoud wordt inhoud gedefinieerd die wordt weergegeven wanneer een pagina voor het eerst wordt gemaakt op basis van de sjabloon.
   * De initiële inhoud kan vervolgens worden bewerkt door auteurs van pagina&#39;s.

   Zie voor meer informatie over de manier waarop een sjabloonauteur de structuur definieert [Paginasjablonen maken](/help/sites-cloud/authoring/sites-console/templates.md#editing-a-template-initial-content-author).

   Voor technische details over de initiële inhoud raadpleegt u [Oorspronkelijke inhoud](#initial-content) in dit document.

   **Layout**

   * U kunt de sjabloonlay-out voor een reeks apparaten definiëren.
   * De responsieve indeling voor sjablonen werkt op dezelfde manier als voor het ontwerpen van pagina&#39;s.

   Zie voor meer informatie over de manier waarop de sjabloonlay-out door de sjabloonauteur wordt gedefinieerd [Paginasjablonen maken](/help/sites-cloud/authoring/sites-console/templates.md#editing-a-template-layout-template-author).

   Voor technische details over de indeling van de template raadpleegt u [Layout](#layout) in dit document.

1. Schakel de sjabloon in en sta deze vervolgens toe voor specifieke inhoudstructuren.

   * U kunt een sjabloon in- of uitschakelen om de sjabloon beschikbaar of niet beschikbaar te maken voor auteurs van pagina&#39;s.
   * Een sjabloon kan beschikbaar worden gesteld of niet beschikbaar zijn voor bepaalde paginasvertakkingen.

   Voor details over hoe een malplaatjeauteur een malplaatje toelaat, zie [Paginasjablonen maken](/help/sites-cloud/authoring/sites-console/templates.md#enabling-and-allowing-a-template-template-author).

   Zie voor technische details over het inschakelen van een sjabloon [Een sjabloon voor ons inschakelen en toestaan](#enabling-and-allowing-a-template-for-use)e in dit document

1. Gebruik dit besturingselement om inhoudspagina&#39;s te maken.

   * Wanneer u een sjabloon gebruikt om een pagina te maken, is er geen zichtbaar verschil en is er geen indicatie tussen statische en bewerkbare sjablonen.
   * Voor de auteur van de pagina is het proces transparant.

   Zie voor meer informatie over hoe een auteur van een pagina sjablonen gebruikt om een pagina te maken [Pagina&#39;s maken en ordenen](/help/sites-cloud/authoring/sites-console/organizing-pages.md#templates).

   Voor technische details over het maken van pagina&#39;s met bewerkbare sjablonen raadpleegt u [Resulterende inhoudspagina&#39;s](#resultant-content-pages) in dit document.

>[!TIP]
>
>Voer nooit informatie in die geïnternationaliseerd moet worden in een sjabloon. Voor internaliseringsdoeleinden wordt de [lokalisatiefuncties van de Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html) aanbevolen.

>[!NOTE]
>
>Sjablonen zijn krachtige gereedschappen om de workflow voor het maken van pagina&#39;s te stroomlijnen. Te veel sjablonen kunnen de auteurs echter overweldigen en tot verwarring bij het maken van pagina&#39;s leiden. Een goede regel is om het aantal sjablonen onder de 100 te houden.
>
>Adobe raadt niet aan meer dan 1000 sjablonen te hebben vanwege mogelijke gevolgen voor de prestaties.

>[!NOTE]
>
>In de clientbibliotheek van de editor wordt ervan uitgegaan dat de editor `cq.shared` naamruimte in inhoudspagina&#39;s en als deze ontbreekt, de JavaScript-fout `Uncaught TypeError: Cannot read property 'shared' of undefined` resulteert.
>
>Alle pagina&#39;s met voorbeeldinhoud bevatten `cq.shared`, dus alle inhoud die erop is gebaseerd, omvat automatisch `cq.shared`. Als u echter besluit zelf inhoudspagina&#39;s te maken zonder deze op voorbeeldinhoud te baseren, moet u ervoor zorgen dat u de `cq.shared` naamruimte.
>
>Zie [Client-Side bibliotheken gebruiken](/help/implementing/developing/introduction/clientlibs.md) voor nadere informatie.



## Sjabloonmappen {#template-folders}

Voor het organiseren van uw sjablonen kunt u de volgende mappen gebruiken:

* `global`
* Sitespecifiek

>[!NOTE]
>
>Ook al kunt u uw mappen nesten, wanneer de gebruiker ze in het dialoogvenster **Sjablonen** worden weergegeven als een platte structuur.

In een standaardinstelling AEM `global` bestaat al in de sjabloonconsole. Dit houdt standaardmalplaatjes vast en doet dienst als reserve als geen beleid en/of malplaatje-types in de huidige omslag worden gevonden. U kunt uw standaardsjablonen toevoegen aan deze map of een map maken (aanbevolen).

>[!NOTE]
>
>Het is aan te raden een map te maken waarin uw aangepaste sjablonen staan en niet de `global` map.

>[!CAUTION]
>
>Mappen moeten worden gemaakt door een gebruiker met `admin` rechten.

Sjabloontypen en beleid worden in alle mappen overgeërfd volgens de volgende prioriteitsvolgorde:

1. De huidige map
1. Bovenliggend item of bovenliggende items van de huidige map
1. `/conf/global`
1. `/apps`
1. `/libs`

Er wordt een lijst met alle toegestane vermeldingen gemaakt. Als een van de configuraties elkaar overlappen ( `path`/ `label`), wordt alleen de instantie die zich het dichtst bij de huidige map bevindt, aan de gebruiker getoond.

Als u een map wilt maken, kunt u het volgende doen:

* Programmaticaal of met CRXDE Lite
* Met de [Configuratiebrowser](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)

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
   * Waarde: de titel (voor de map) die u wilt weergeven in het dialoogvenster **Sjablonen** console.

1. Naast de standaardmachtigingen en -bevoegdheden (bijvoorbeeld `content-authors`) moet u nu groep(en) toewijzen en de vereiste toegangsrechten (ACL&#39;s) definiëren voor uw auteurs om sjablonen in de nieuwe map te kunnen maken.

   De `template-authors` groep is de standaardgroep die moet worden toegewezen. Zie de sectie [ACLs en Groepen](#acls-and-groups) voor meer informatie.

   <!--See [Access Right Management](/help/sites-administering/user-group-ac-admin.md#access-right-management) for full details on managing and assigning access rights.-->

### De configuratiebrowser gebruiken {#using-the-configuration-browser}

1. Ga naar **Algemene navigatie** > **Gereedschappen** > [**Configuratiebrowser**](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

   De bestaande mappen worden links weergegeven, inclusief `global` map.

1. Klikken **Maken**.
1. In de **Configuratie maken** moeten de volgende velden worden geconfigureerd:

   * **Titel**: Geef een titel op voor de configuratiemap
   * **Bewerkbare sjablonen**: Tik om bewerkbare sjablonen in deze map toe te staan

1. Klikken **Maken**

>[!NOTE]
>
>In de [Configuratiebrowser,](/help/implementing/developing/introduction/configurations.md#using-configuration-browser) u kunt de algemene map bewerken en de **Bewerkbare sjablonen** als u sjablonen in deze map wilt maken, wordt dit echter niet aanbevolen.

### ACLs en Groepen {#acls-and-groups}

Zodra uw malplaatjeomslagen (of via CRXDE of met Browser van de Configuratie) worden gecreeerd, moet ACLs voor de aangewezen groepen voor de malplaatjeomslagen worden bepaald om juiste veiligheid te verzekeren.

De sjabloonmappen voor de [WKND-zelfstudie](/help/implementing/developing/introduction/develop-wknd-tutorial.md) kan als voorbeeld worden gebruikt.

#### De groep sjabloonauteurs {#the-template-authors-group}

De `template-authors` de groep is de groep wordt gebruikt om toegang tot malplaatjes te beheren en komt standaard met AEM, maar is leeg. Gebruikers moeten worden toegevoegd aan de groep voor het project of de site.

>[!CAUTION]
>
>De `template-authors` Deze groep is alleen bedoeld voor gebruikers die nieuwe sjablonen moeten kunnen maken.
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
   <td>Sjabloonauteurs die sjablonen maken, lezen, bijwerken, verwijderen en repliceren in sitespecifieke sjablonen <code>/conf</code> spatie</td>
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
   <td>Sjabloonauteurs die sjablonen maken, lezen, bijwerken, verwijderen en repliceren in sitespecifieke sjablonen <code>/conf</code> spatie</td>
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

Deze standaard `template-authors` groep omvat alleen de projectinstellingen, waarbij alle `template-authors` leden hebben toegang tot alle sjablonen en mogen deze samenstellen. Voor complexere montages, waar de veelvoudige groepen van malplaatjeauteurs nodig zijn om toegang tot malplaatjes te scheiden, moeten meer de auteursgroepen van het douanemalplaatje worden gecreeerd. Nochtans zouden de toestemmingen voor de groepen van malplaatjeauteurs nog het zelfde zijn.

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

   * Als onderdeel van het [WKND-zelfstudie](/help/implementing/developing/introduction/develop-wknd-tutorial.md).

* Sjabloontypen worden meestal gedefinieerd door ontwikkelaars.

De sjabloontypen voor de out-of-the-box worden opgeslagen onder:

* `/libs/settings/wcm/template-types`

>[!CAUTION]
>
>U mag niets wijzigen in het dialoogvenster `/libs` pad. Dit komt omdat de inhoud van `/libs` kan op elk moment worden overschreven door een update naar AEM.

Uw sitespecifieke sjabloontypen moeten worden opgeslagen op de vergelijkbare locatie:

* `/apps/settings/wcm/template-types`

De definities voor uw aangepaste malplaatjetypes zouden in user-defined omslagen (geadviseerd) of anders in moeten worden opgeslagen `global`. Bijvoorbeeld:

* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/template-types`
* `/conf/<my-folder>/settings/wcm/template-types`
* `/conf/global/settings/wcm/template-types`

>[!CAUTION]
>
>De sjabloontypen moeten de juiste mapstructuur in acht nemen (dat wil zeggen: `/settings/wcm/...`), anders worden de sjabloontypen niet gevonden.

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

1. Een sjabloon maken zoals een paginasjabloon [zoals hier beschreven](/help/sites-cloud/authoring/sites-console/templates.md#creating-a-new-template-template-author), die als basis voor uw sjabloontype zal dienen.
1. Kopieer de gemaakte sjabloon met CRXDE Lite uit de `templates` aan de `template-types` knooppunt onder [sjabloonmap](#template-folders).
1. De sjabloon verwijderen uit het dialoogvenster `templates` knooppunt onder [sjabloonmap](#template-folders).
1. In de kopie van de sjabloon die zich onder de `template-types` knooppunt, alles verwijderen `cq:template` en `cq:templateType` eigenschappen van alle `jcr:content` knooppunten.

U kunt uw eigen malplaatjetype ook ontwikkelen gebruikend een voorbeeld editable malplaatje als basis, beschikbaar op GitHub.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open a-plaatsen-voorbeeld-douane-malplaatje-type project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type/archive/master.zip)

## Sjabloondefinities {#template-definitions}

Definities voor bewerkbare sjablonen worden opgeslagen [door de gebruiker gedefinieerde mappen](#template-folders) (aanbevolen) of als alternatief in `global`. Bijvoorbeeld:

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

* Is samengevoegd met de oorspronkelijke inhoud ( `/initial`) bij het maken van een pagina.
* Wijzigingen in de structuur worden weerspiegeld in alle pagina&#39;s die met de sjabloon zijn gemaakt.
* De `root` ( `structure/jcr:content/root`) definieert de lijst met componenten die beschikbaar zijn op de resulterende pagina.
   * Componenten die zijn gedefinieerd in de sjabloonstructuur kunnen niet worden verplaatst op of verwijderd van resulterende pagina&#39;s.
   * Nadat een component is ontgrendeld, `editable` eigenschap is ingesteld op `true`.
   * Nadat een component die al inhoud bevat, is ontgrendeld, wordt deze inhoud naar de `initial` vertakking.

* De `cq:responsive` node bevat definities voor de responsieve lay-out.

### Oorspronkelijke inhoud {#initial-content}

Definieert de eerste inhoud die een nieuwe pagina krijgt wanneer deze wordt gemaakt:

* Bevat een `jcr:content` knooppunt dat naar nieuwe pagina&#39;s wordt gekopieerd.
* Is samengevoegd met de structuur ( `/structure`) bij het maken van een pagina.
* Bestaande pagina&#39;s worden niet bijgewerkt als de oorspronkelijke inhoud na het maken wordt gewijzigd.
* De `root` het knooppunt bevat een lijst met componenten om te definiëren wat beschikbaar is in de resulterende pagina.
* Als er inhoud wordt toegevoegd aan een component in de structuurmodus en die component vervolgens wordt ontgrendeld (of omgekeerd), wordt deze inhoud gebruikt als initiële inhoud.

### Layout {#layout}

Wanneer [bewerken van een sjabloon die u kunt definiëren](/help/sites-cloud/authoring/sites-console/templates.md)gebruikt [standaardresponsieve indeling](/help/sites-cloud/authoring/page-editor/responsive-layout.md).

<!-- that can also be [configured](/help/sites-administering/configuring-responsive-layout.md). -->

### Inhoudsbeleid {#content-policies}

Het inhoudsbeleid definieert de ontwerpeigenschappen van een component. Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen. Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt). Het inhoudsbeleid kan worden gemaakt en geselecteerd in de sjablooneditor.

* De eigenschap `cq:policy`, over de `root` node
  `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/root`
Verstrekt een relatieve verwijzing naar het inhoudsbeleid voor het de paragraafsysteem van de pagina.

* De eigenschap `cq:policy`, op de componentexpliciete knooppunten onder `root`koppelingen naar het beleid voor de afzonderlijke componenten te verschaffen.

* De feitelijke beleidsdefinities worden opgeslagen onder:
  `/conf/<your-folder>/settings/wcm/policies/wcm/foundation/components`

>[!NOTE]
>
>De paden van beleidsdefinities zijn afhankelijk van het pad van de component. `cq:policy` bevat een relatieve verwijzing naar de configuratie zelf.

### Paginabeleid {#page-policies}

Met paginabeleid kunt u de [inhoudsbeleid](#content-policies) voor de pagina (belangrijkste parsys), in of het malplaatje of resulterende pagina&#39;s.

### Een sjabloon inschakelen en toestaan voor gebruik {#enabling-and-allowing-a-template-for-use}

1. **Sjabloon inschakelen**

   Voordat een sjabloon kan worden gebruikt, moet deze zijn ingeschakeld door:

   * [De sjabloon inschakelen](/help/sites-cloud/authoring/sites-console/templates.md) van de **Sjablonen** console.

   * De statuseigenschap instellen op de knop `jcr:content` knooppunt.

      * Bijvoorbeeld op:
        `/conf/<your-folder>/settings/wcm/templates/<your-template>/jcr:content`

      * Definieer de eigenschap:

         * Naam: status
         * Type: String
         * Waarde: `enabled`

1. **Toegestane sjablonen**

   * [Definieer de toegestane sjabloonpaden op het tabblad **Pagina-eigenschappen**](/help/sites-cloud/authoring/sites-console/templates.md#allowing-a-template-author) van de desbetreffende pagina of basispagina van een subvertakking.
   * Stel de eigenschap in:
     `cq:allowedTemplates`
Op de `jcr:content` knooppunt van de vereiste vertakking.

   Bijvoorbeeld met een waarde van:

   `/conf/<your-folder>/settings/wcm/templates/.*`

## Resulterende inhoudspagina&#39;s {#resultant-content-pages}

Pagina&#39;s gemaakt op basis van bewerkbare sjablonen:

* Wordt gemaakt met een substructuur waaruit wordt samengevoegd `structure` en `initial` in de sjabloon

* Verwijzingen hebben naar in de template opgeslagen informatie en naar het sjabloontype. Dit wordt bereikt met een `jcr:content` knooppunt met de eigenschappen:

   * `cq:template` - Verstrekt de dynamische verwijzing naar het daadwerkelijke malplaatje; laat toe dat veranderingen in het malplaatje worden weerspiegeld op de daadwerkelijke pagina&#39;s.

   * `cq:templateType` - Verstrekt een verwijzing naar het malplaatjetype.

![Hoe sjablonen, inhoud en componenten met elkaar samenhangen](assets/templates-content-components.png)

In het bovenstaande diagram ziet u hoe sjablonen, inhoud en componenten met elkaar verweven zijn:

* Controller - `/content/<my-site>/<my-page>` - De resulterende pagina die naar de sjabloon verwijst. De inhoud bepaalt het gehele proces. Volgens de definities heeft het toegang tot de toepasselijke sjabloon en componenten.
* Configuratie - `/conf/<my-folder>/settings/wcm/templates/<my-template>` - de [sjabloonbeleid en beleid inzake gerelateerde inhoud](#template-definitions) definieert u de paginaconfiguratie.
* Model - OSGi-bundels - De [OSGI-pakketten](/help/implementing/deploying/configuring-osgi.md) de functionaliteit implementeren.
* Weergeven - `/apps/<my-site>/components` - In zowel de auteur- als de publicatieomgeving wordt de inhoud gerenderd door componenten.

Bij het weergeven van een pagina:

* **Sjablonen**:

   * De `cq:template` eigendom van zijn `jcr:content` node wordt referenced to access the template that corresponding to that page.

* **Componenten**:

   * De component page voegt de `structure/jcr:content` structuur van de sjabloon met de `jcr:content` boomstructuur van de pagina.
      * Met de paginacomponent kan de auteur alleen de knooppunten van de sjabloonstructuur bewerken die als bewerkbaar zijn gemarkeerd (en eventuele onderliggende knooppunten).
      * Wanneer u een component op een pagina rendert, wordt het relatieve pad van die component overgenomen van de `jcr:content` knooppunt; hetzelfde pad onder `policies/jcr:content` het knooppunt van de sjabloon wordt doorzocht.
         * De `cq:policy` Het bezit van deze knoop wijst aan het daadwerkelijke inhoudsbeleid (namelijk houdt het de ontwerpconfiguratie voor die component).
            * Dit laat u veelvoudige malplaatjes hebben die de zelfde configuraties van het inhoudsbeleid opnieuw gebruiken.

### Beschikbaarheid sjabloon {#template-availability}

Wanneer u een pagina maakt in de interface voor sitebeheer, is de lijst met beschikbare sjablonen afhankelijk van de locatie van de nieuwe pagina en de plaatsingsbeperkingen die in elke sjabloon zijn opgegeven.

De volgende eigenschappen bepalen of een sjabloon `T` mag worden gebruikt voor een nieuwe pagina die als onderliggend item van een pagina moet worden geplaatst `P`. Elk van deze eigenschappen is een tekenreeks met meerdere waarden die nul of meer reguliere expressies bevat die worden gebruikt voor overeenkomsten met paden:

* De `cq:allowedTemplates` eigendom van de `jcr:content` subknooppunt van `P` of een voorouder van `P`.

* De `allowedPaths` eigenschap van `T`.

* De `allowedParents` eigenschap van `T`.

* De `allowedChildren` eigenschap van de template van `P`.

De evaluatie werkt als volgt:

* De eerste niet-lege `cq:allowedTemplates` eigenschap gevonden tijdens oplopende paginahiërarchie, beginnend met `P` komt overeen met het pad van `T`. Als geen van de waarden overeenkomt, `T` wordt verworpen.

* Indien `T` heeft een niet-leeg `allowedPaths` eigenschap, maar geen van de waarden komt overeen met het pad van `P`, `T` wordt verworpen.

* Als beide bovengenoemde eigenschappen leeg of niet bestaan, `T` wordt afgewezen, tenzij het tot dezelfde aanvraag behoort als `P`. `T` behoort tot dezelfde toepassing als `P` als en alleen als de naam van het tweede niveau van het pad van `T` is gelijk aan de naam van het tweede niveau van het pad van `P`. De sjabloon `/apps/wknd/templates/foo` behoort tot dezelfde toepassing als de pagina `/content/wknd`.

* Indien `T` heeft een niet-leeg `allowedParents` eigenschap, maar geen van de waarden komt overeen met het pad van `P`, `T` wordt verworpen.

* Indien de template van `P` heeft een niet-leeg `allowedChildren` eigenschap, maar geen van de waarden komt overeen met het pad van `T`, `T` wordt verworpen.

* In alle andere gevallen `T` is toegestaan.

Het volgende diagram toont het sjabloonevaluatieproces:

![Sjabloonevaluatieproces](assets/template-evaluation.png)

>[!CAUTION]
>
>AEM biedt meerdere eigenschappen om de sjablonen te beheren die zijn toegestaan onder **Sites**. Het combineren van deze regels kan echter leiden tot zeer complexe regels die moeilijk te volgen en te beheren zijn.
>
>Daarom adviseert de Adobe dat u eenvoudig begint, door te bepalen:
>
>* alleen de `cq:allowedTemplates` eigenschap
>
>* alleen in de hoofdmap van de site
>
>Zie voor een voorbeeld de [WKND-zelfstudie](/help/implementing/developing/introduction/develop-wknd-tutorial.md) inhoud: `/content/wknd/jcr:content`
>
>De eigenschappen `allowedPaths`, `allowedParents`, en `allowedChildren` kan ook op de malplaatjes worden geplaatst om verfijndere regels te bepalen. Waar mogelijk is het echter *veel* eenvoudiger te definiëren `cq:allowedTemplates` eigenschappen op subsecties van de site als de toegestane sjablonen verder moeten worden beperkt.
>
>Een extra voordeel is dat de `cq:allowedTemplates` eigenschappen kunnen door een auteur worden bijgewerkt in het dialoogvenster **Geavanceerd** tabblad van het **Pagina-eigenschappen**. De andere malplaatjeeigenschappen kunnen niet worden bijgewerkt gebruikend (standaard) UI, zodat zou een ontwikkelaar nodig hebben om de regels en een codeplaatsing voor elke verandering te handhaven.

#### Sjablonen beperken die worden gebruikt in onderliggende pagina&#39;s {#limiting-templates-used-in-child-pages}

Als u wilt beperken welke sjablonen kunnen worden gebruikt om onderliggende pagina&#39;s onder een bepaalde pagina te maken, gebruikt u de opdracht `cq:allowedTemplates` eigenschap van `jcr:content` knooppunt van de pagina om de lijst op te geven met sjablonen die als onderliggende pagina&#39;s zijn toegestaan. Elke waarde in de lijst moet een absoluut pad zijn naar een sjabloon voor bijvoorbeeld een toegestane onderliggende pagina. `/apps/wknd/templates/page-content`.

U kunt de `cq:allowedTemplates` eigenschap op de sjabloon  `jcr:content` knoop om deze configuratie toe te passen op alle gecreeerde pagina&#39;s die dit malplaatje gebruiken.

Als u meer beperkingen wilt toevoegen, bijvoorbeeld met betrekking tot de sjabloonhiërarchie, kunt u de opdracht `allowedParents/allowedChildren` eigenschappen op de sjabloon. U kunt dan uitdrukkelijk specificeren dat de pagina&#39;s die van een malplaatjeT worden gecreeerd ouderpagina/kinderen van pagina&#39;s moeten zijn die van een malplaatjeT worden gecreeerd.
