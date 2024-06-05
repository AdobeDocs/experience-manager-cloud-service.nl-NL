---
title: De container voor lay-out en de lay-outmodus configureren
description: Leer hoe u de lay-outcontainer en de lay-outmodus configureert om responsieve lay-outs voor de auteurs van de inhoud in te schakelen.
exl-id: 469e8151-8231-4ccc-b7f6-855545f87440
solution: Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 0%

---

# De container voor lay-out en de lay-outmodus configureren {#configuring-layout-container-and-layout-mode}

[Responsieve lay-out](/help/sites-cloud/authoring/page-editor/responsive-layout.md) is een mechanisme om te realiseren [responsief webontwerp.](https://en.wikipedia.org/wiki/Responsive_web_design) Hierdoor kan de auteur van de inhoud webpagina&#39;s maken met een indeling en afmetingen die afhankelijk zijn van de apparaten die de gebruikers gebruiken.

AEM realiseert responsieve lay-out voor uw pagina&#39;s gebruikend een combinatie mechanismen:

* **[Layout Container](/help/sites-cloud/authoring/page-editor/responsive-layout.md#adding-a-layout-container-and-its-content-edit-mode)** - Deze component biedt een rasteralineasysteem waarmee u componenten kunt toevoegen en positioneren binnen een responsief raster.
   * Het kan als standaardparsys voor uw pagina worden gebruikt en/of ter beschikking gesteld aan auteurs in componentenbrowser.
   * De standaardwaarde **Layout Container** component wordt gedefinieerd onder `/libs/wcm/foundation/components/responsivegrid`.
   * U kunt lay-outcontainers definiëren:
      * Als een component die de gebruiker aan een pagina kan toevoegen.
      * Als standaardparsys voor de pagina.
      * Als zowel component als standaard parsys.
         * U kunt de lay-outcontainer als standaard voor de pagina hebben, terwijl het toestaan van de gebruiker om verdere lay-outcontainers binnen dit toe te voegen; bijvoorbeeld, om kolomcontrole te bereiken.
* **[Lay-outmodus](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector)** - Als de lay-outcontainer eenmaal op de pagina is geplaatst, kunt u de opdracht **Layout** om de inhoud binnen het responsieve raster te plaatsen.
* **[Emulator](/help/sites-cloud/authoring/page-editor/responsive-layout.md#selecting-a-device-to-emulate)** - Zo kunt u responsieve websites maken en bewerken die de lay-out op basis van de grootte van het apparaat of venster opnieuw rangschikken door de grootte van componenten interactief aan te passen. De gebruiker kan dan zien hoe de inhoud wordt gerenderd met de emulator.

Met deze responsieve rastermechanismen kunt u:

* Gebruik onderbrekingspunten (die apparaatgroepering aangeven) om een verschillend gedrag voor de inhoud te definiëren op basis van de apparaatlay-out.
* Componenten verbergen op basis van apparaatgroep (definiëren op welk onderbrekingspunt een component wordt verborgen).
* Gebruik horizontale uitlijning op het raster (plaats componenten in het raster, wijzig de grootte naar wens en definieer wanneer ze naast elkaar of boven/onder moeten samenvouwen/opnieuw moeten plaatsen).
* Kolombesturingselement realiseren.

>[!NOTE]
>
>Wanneer u een site maakt op basis van de [Projectarchetype](#addlink) of van de [Standaardsitesjabloon](#addlink), wordt de ontvankelijke lay-out over het algemeen gevormd. Anders moet u [De component Layout Container activeren](#enable-the-layout-container-component-for-page) voor uw pagina&#39;s.

## De emulator inschakelen {#enabling-emulator}

De [Projectarchetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) en de [Standaardsitesjabloon](/help/sites-cloud/administering/site-creation/site-templates.md#standard-site-template) zijn al ingeschakeld om de emulator te gebruiken. Als u uw eigen inhoud hebt ontwikkeld die niet is gebaseerd op de Core Components of archetype, raadpleegt u het document [Responsief ontwerp](/help/implementing/developing/introduction/responsive-design.md) voor meer informatie over hoe u uw componenten kunt ontwikkelen terwijl u deze functies gebruikt.

## Lay-outmodus voor uw site activeren {#activate-layout-mode-for-your-site}

**Layout** kunt u de emulator gebruiken om de lay-out van uw inhoud voor verschillende apparaten aan te passen. De WKND-voorbeeldsite is al ingeschakeld voor **Layout** -modus. Voer de volgende stappen uit om uw eigen site in te schakelen.

### Onderbrekingspunten configureren {#configure-breakpoints}

Onderbrekingspunten zijn van essentieel belang voor een responsief ontwerp en definiëren hoe en wanneer de inhoud wordt aangepast aan het doelapparaat. Wees echter voorzichtig, want elk breekpunt dat u introduceert, zal extra werk voor uw auteurs genereren om de inhoud aan te passen. Vaak kunnen twee onderbrekingspunten volstaan, inclusief het standaardonderbrekingspunt dat er altijd is. Adobe raadt aan niet meer dan drie onderbrekingspunten te maken, inclusief de standaardinstelling, dat wil zeggen niet meer dan twee onderliggende knooppunten `cq:responsive/breakpoint`.

* Onderbrekingspunten hebben een titel en een breedte:
   * De titel beschrijft de algemene apparaatgroepering, met richtlijn indien nodig.
      * Bijvoorbeeld: `phone`, `tablet`
   * De breedte bepaalt de maximumbreedte in pixel voor die generische apparatengroepering.
      * Bijvoorbeeld, als de breekpunttelefoon een breedte van 768 heeft dan dat het de maximumbreedte van de lay-out heeft die voor een telefoonapparaat wordt gebruikt.
* Onderbrekingspunten kunnen worden gedefinieerd:
   * Op het paginasjabloon, vanaf waar de instellingen worden gekopieerd naar pagina&#39;s die met die sjabloon zijn gemaakt.
   * Op het paginaknooppunt, vanwaar de montages door om het even welke kindpagina&#39;s worden geërft.
* Onderbrekingspunten zijn zichtbaar als markeringen boven aan de pagina-editor wanneer u de emulator gebruikt.
* Onderbrekingspunten worden overgeërfd van de hiërarchie van bovenliggende knooppunten en kunnen willekeurig worden overschreven.
* Er is een standaardbreekpunt (uit-van-de-doos) dat alles boven het laatste gevormde breekpunt behandelt.
* Onderbrekingspunten kunnen worden gedefinieerd met behulp van CRXDE Lite of XML.

Voor zowel nieuwe als bestaande projecten moeten onderbrekingspunten in overweging worden genomen.

* Als u opstelling een nieuw project, zou u breekpunten aan de malplaatjes moeten toevoegen.
* Als u een bestaand project (met bestaande inhoud) migreert, moet u:
   * Voeg onderbrekingspunten toe aan de sjablonen.
   * Voeg dezelfde onderbrekingspunten toe aan de bestaande pagina&#39;s.

Vanwege overerving hoeft u dit alleen te doen voor de basispagina van uw inhoud.

#### Onderbrekingspunten configureren met CRXDE Lite {#configuring-breakpoints-using-crxde-lite}

1. Navigeer met CRXDE Lite naar:

   * Uw sjabloondefinitie.
   * De `jcr:content` knooppunt van uw pagina.

1. Onder `jcr:content` Maak het knooppunt:

   * Naam: `cq:responsive`
   * Type: `nt:unstructured`

1. Onder dit creeer de knoop:

   * Naam: `breakpoints`
   * Type: `nt:unstructured`

1. Onder het knooppunt voor onderbrekingspunten kunt u een willekeurig aantal onderbrekingspunten maken. Elke definitie is één knooppunt met de volgende eigenschappen:

   * Naam: `<descriptive name>`
   * Type: `nt:unstructured`
   * Titel: `String <descriptive title seen in Emulator>`
   * Breedte: `Decimal <value of breakpoint>`

#### Onderbrekingspunten configureren met XML {#configuring-breakpoints-using-xml}

Onderbrekingspunten bevinden zich in de `<jcr:content>` van de `.context.html` in de juiste sjabloonmap (of inhoudsmap).

Een voorbeelddefinitie:

```xml
<cq:responsive jcr:primaryType="nt:unstructured">
  <breakpoints jcr:primaryType="nt:unstructured">
    <phone jcr:primaryType="nt:unstructured" title="{String}Phone" width="{Decimal}768"/>
    <tablet jcr:primaryType="nt:unstructured" title="{String}Tablet" width="{Decimal}1200"/>
  </breakpoints>
</cq:responsive>
```

## Component resizing voor de pagina inschakelen {#enable-component-resizing-for-the-page}

Het formaat van componenten wijzigen in **Layout** De modus is een belangrijk onderdeel van responsief ontwerp en kan worden gebruikt op de WKND-voorbeeldsite. Voer de volgende stappen uit om uw eigen site in te schakelen.

### De container van de Lay-out instellen als HoofdParsys {#set-layout-container-as-main-parsys}

Om hoofdparsys van uw pagina te plaatsen om een lay-outcontainer te zijn, bepaal parsys als:

`wcm/foundation/components/responsivegrid`

In één van beide:

* Pagina-component
* Paginasjabloon (voor toekomstig gebruik)

De volgende twee voorbeelden illustreren de definitie:

* **HTL:**

  ```xml
  <sly data-sly-resource="${'par' @ resourceType='wcm/foundation/components/responsivegrid'}/>
  ```

* **JSP:**

  ```xml
  <cq:include path="par" resourceType="wcm/foundation/components/responsivegrid" />
  ```

### Inclusief de responsieve CSS {#include-the-responsive-css}

#### CSS voor onderbrekingspunten die MINDER gebruiken {#css-for-breakpoints-using-less}

AEM gebruikt LESS om delen van noodzakelijke CSS te produceren, moeten deze voor uw projecten worden omvat.

U moet een [clientbibliotheek](/help/implementing/developing/introduction/clientlibs.md) om extra configuratie en functievraag te verstrekken. Het volgende LESS extract is een voorbeeld van het minimum dat u aan uw project moet toevoegen:

```java
@import (once) "/libs/wcm/foundation/clientlibs/grid/grid_base.less";

/* maximum amount of grid cells to be provided */
@max_col: 12;

/* default breakpoint */
.aem-Grid {
  .generate-grid(default, @max_col);
}

/* phone breakpoint */
@media (max-width: 768px) {
  .aem-Grid {
    .generate-grid(phone, @max_col);
  }
}

/* tablet breakpoint */
@media (min-width: 769px) and (max-width: 1200px) {
  .aem-Grid {
    .generate-grid(tablet, @max_col);
  }
}
```

De definitie van het basisraster is te vinden onder:

`/libs/wcm/foundation/clientlibs/grid/grid_base.less`

#### Overwegingen bij opmaken {#styling-considerations}

Componenten die in een responsieve container worden vastgehouden, worden vergroot of verkleind (samen met hun respectievelijke HTML DOM-elementen) op basis van de responsieve rastergrootte. Daarom wordt in deze omstandigheden aanbevolen definities van DOM-elementen met een vaste breedte (bevat) te vermijden (of bij te werken).

Bijvoorbeeld:

* Voor:

   * `width=100px`

* Na:

   * `max-width=100px`

#### Compatibiliteit van afbeeldingen vergroten/verkleinen en aanpassen {#resizing-and-adaptive-image-compliance}

Als u de grootte van een component in het raster wijzigt, worden de volgende listeners geactiveerd, indien van toepassing:

* `beforeedit`
* `beforechildedit`
* `afteredit`
* `afterchildedit`

Als u de inhoud van een adaptieve afbeelding in een responsief raster op de juiste wijze wilt vergroten of verkleinen en bijwerken, moet u een `afterEdit` instellen op `REFRESH_PAGE` listener in de `EditConfig` bestand van elke component in het bestand.

Bijvoorbeeld:

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`

Het mechanisme voor adaptieve afbeeldingen is beschikbaar via een script dat de selectie van de juiste afbeelding voor de huidige grootte van het venster bepaalt. De gebeurtenis wordt geactiveerd nadat de DOM gereed is of wanneer een specifieke gebeurtenis wordt ontvangen. De pagina moet momenteel worden vernieuwd om het resultaat van de actie van de gebruiker correct weer te geven.

>[!CAUTION]
>
>Aangepaste stijlbladclientlibs moeten worden geladen als onderdeel van de koptekst, anders kunnen ze niet alleen worden gepubliceerd, maar ook goed werken op de auteur.

## De Containercomponent voor lay-out inschakelen voor pagina {#enable-the-layout-container-component-for-page}

Voor een effectieve responsieve lay-out moet de auteur van de inhoud instanties van de component Layout Container naar de pagina kunnen slepen. Dit is al ingeschakeld voor de WKND-voorbeeldsite. Voer de volgende stappen uit om uw eigen site in te schakelen.

### De Containercomponent voor lay-out inschakelen voor paginabewerking {#enable-the-layout-container-component-for-page-editing}

Auteurs kunnen meer responsieve rasters toevoegen aan de inhoudspagina&#39;s als u de component Layout Container voor uw pagina wilt inschakelen. U kunt dit doen door:

* **Via de auteursomgeving** - [Uw paginasjablonen bewerken](/help/sites-cloud/authoring/sites-console/templates.md) om de container voor lay-out in te schakelen voor een pagina.
* **Componentdefinitie** - Gebruik `allowedComponent` of een statische include-opdracht wanneer de component wordt gedefinieerd.

### Het raster van de container van de layout configureren {#configure-the-grid-of-the-layout-container}

U kunt het aantal kolommen vormen beschikbaar voor elke specifieke instantie van lay-outcontainer [door uw paginasjablonen te bewerken.](/help/sites-cloud/authoring/sites-console/templates.md)
