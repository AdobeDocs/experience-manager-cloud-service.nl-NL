---
title: Stijl Adobe Experience Manager CIF Core-onderdelen
description: Leer hoe u Adobe Experience Manager (AEM) CIF Core Components opmaakt. In de zelfstudie wordt uitgelegd hoe bibliotheken of clientlibs aan de clientzijde worden gebruikt voor de implementatie en het beheer van CSS en JavaScript voor een AEM Commerce-implementatie. Deze zelfstudie behandelt ook hoe de module ui.frontend en een webpack-project in het end-to-end buildproces zijn geïntegreerd.
sub-product: Commerce
topics: Development
version: Cloud Service
doc-type: tutorial
activity: develop
audience: developer
feature: Commerce Integration Framework
kt: 3456
thumbnail: 3456-style-cif.jpg
exl-id: 521c1bb8-7326-4ee8-aba3-f386727e2b34
role: Admin
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '2342'
ht-degree: 0%

---

# Stijl AEM CIF kerncomponenten {#style-aem-cif-core-components}

Het [ CIF Project van Venia ](https://github.com/adobe/aem-cif-guides-venia) is een basis van de verwijzingscode voor het gebruiken van [ CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components). In deze zelfstudie inspecteert u het Venia-referentieproject en begrijpt u hoe CSS en JavaScript die door AEM Core-componenten worden gebruikt, worden georganiseerd. U creeert ook een stijl gebruikend CSS om de standaardstijl van de **component bij te werken van de Teaser van het 0} Product.**

>[!TIP]
>
> Gebruik [ AEM archetype van het Project ](https://github.com/adobe/aem-project-archetype) wanneer het beginnen van uw eigen handelsimplementatie.

## Wat u gaat maken

In deze zelfstudie wordt een nieuwe stijl geïmplementeerd voor de component Product Teaser die op een kaart lijkt. De lessen die in het leerprogramma worden geleerd kunnen op andere Componenten van de Kern worden toegepast CIF.

![ wat u ](../assets/style-cif-component/what-you-will-build.png) zult bouwen

## Vereisten {#prerequisites}

U hebt een lokale ontwikkelomgeving nodig om deze zelfstudie te voltooien. Deze omgeving bevat een actieve instantie van AEM die is geconfigureerd en is verbonden met een Adobe Commerce-instantie. Herzie de vereisten en de stappen voor [ vestiging een lokale ontwikkeling met AEM as a Cloud Service SDK ](../develop.md).

## Het Venia-project klonen {#clone-venia-project}

U gaat het [ Project van Venia ](https://github.com/adobe/aem-cif-guides-venia) klonen, en dan de standaardstijlen met voeten treden.

>[!NOTE]
>
> **voelt vrij om een bestaand project** (gebaseerd op het AEM Archieftype van Project met inbegrepen CIF) te gebruiken en deze sectie over te slaan.

1. Voer de volgende git-opdracht uit, zodat u het project kunt klonen:

   ```shell
   $ git clone git@github.com:adobe/aem-cif-guides-venia.git
   ```

1. Bouw en stel het project aan een lokaal geval van AEM op:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

1. Voeg de noodzakelijke configuraties OSGi toe zodat kunt u uw AEM instantie met een instantie van Adobe Commerce verbinden of de configuraties toevoegen aan het gecreeerde project.

1. Op dit moment hebt u een werkende versie van een winkel die is verbonden met een Adobe Commerce-instantie. Navigeer aan `US` > `Home` pagina bij: [ http://localhost:4502/editor.html/content/venia/us/en.html ](http://localhost:4502/editor.html/content/venia/us/en.html).

   Je moet zien dat de winkel het Venia-thema gebruikt. Als u het hoofdmenu van de winkel uitbreidt, ziet u verschillende categorieën die aangeven dat de verbinding met Adobe Commerce werkt.

   ![ Storefront die met het Thema van Venia wordt gevormd ](../assets/style-cif-component/venia-store-configured.png)

## Client Libraries en ui.frontend Module {#introduction-to-client-libraries}

CSS en JavaScript verantwoordelijk voor het teruggeven van het thema/de stijlen van de storefront wordt beheerd in AEM door a [ cliëntbibliotheek ](/help/implementing/developing/introduction/clientlibs.md) of &quot;clientlibs&quot;voor kort. Clientbibliotheken bieden een mechanisme om CSS en JavaScript in de code van een project te organiseren en vervolgens op de pagina te leveren.

Brand-specifieke stijlen kunnen op AEM Componenten van de Kern worden toegepast door CSS toe te voegen en met voeten te treden die door deze cliëntbibliotheken wordt geleid. Inzicht in de structuur van clientbibliotheken en de inhoud van deze bibliotheken op de pagina is essentieel.

[ ui.frontend ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uifrontend.html) is een specifiek [ webpack ](https://webpack.js.org/) project om alle front-end activa voor een project te beheren. Dit webpack laat front-end ontwikkelaars om het even welk aantal talen en technologieën zoals [ gebruiken TypeScript ](https://www.typescriptlang.org/), [ Volgen ](https://sass-lang.com/), en veel meer.

De `ui.frontend` module is ook een GMaven module en geïntegreerd met het grotere project door een module NPM te gebruiken [ aem-client-clientlib-generator ](https://github.com/wcm-io-frontend/aem-clientlib-generator). Tijdens een build kopieert `aem-clientlib-generator` de gecompileerde CSS- en JavaScript-bestanden naar een clientbibliotheek in de module `ui.apps` .

![ ui.frontend aan ui.apps architectuur ](../assets/style-cif-component/ui-frontend-architecture.png)

*Gecompileerde CSS en JavaScript worden gekopieerd van de `ui.frontend` module in de `ui.apps` module als cliëntbibliotheek tijdens een Maven bouwt*

## Teastijl bijwerken {#ui-frontend-module}

Breng vervolgens een kleine wijziging aan in de stijl Taser om te zien hoe de module `ui.frontend` en de clientbibliotheken werken. Gebruik [ winde van uw keus ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#set-up-the-development-ide) om het project van Venia in te voeren. De gebruikte schermafbeeldingen zijn van [ winde van de Code van Visual Studio ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#microsoft-visual-studio-code).

1. Navigeer en breid **ui.frontend** module uit en breid de omslaghiërarchie aan uit: `ui.frontend/src/main/styles/commerce`

   ![ ui.frontend handelsomslag ](../assets/style-cif-component/ui-frontend-commerce-folder.png)

   Merk op dat er veelvoudige dossiers van de Klasse (`.scss`) onder de omslag zijn. Dit zijn de Commerce-specifieke stijlen voor elk van de Commerce-componenten.

1. Open het bestand `_productteaser.scss` .

1. Werk de regel `.item__image` bij en wijzig de randregel:

   ```scss
   .item__image {
       border: #ea00ff 8px solid; /* <-- modify this rule */
       display: block;
       grid-area: main;
       height: auto;
       opacity: 1;
       transition-duration: 512ms;
       transition-property: opacity, visibility;
       transition-timing-function: ease-out;
       visibility: visible;
       width: 100%;
   }
   ```

   Met de bovenstaande regel moet u een vette, roze rand toevoegen aan de Product Teaser Component.

1. Open een nieuw terminalvenster en navigeer naar de map `ui.frontend` :

   ```shell
   $ cd <project-location>/aem-cif-guides-venia/ui.frontend
   ```

1. Voer de volgende Maven-opdracht uit:

   ```shell
   $ mvn clean install
   ...
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   [INFO] Total time:  29.497 s
   [INFO] Finished at: 2020-08-25T14:30:44-07:00
   [INFO] ------------------------------------------------------------------------
   ```

   Inspect de einduitvoer. U ziet dat de opdracht Geweven verschillende NPM-scripts uitvoert, waaronder `npm run build` . De opdracht `npm run build` wordt gedefinieerd in het `package.json` -bestand en compileert het webpack-project en activeert het genereren van de clientbibliotheek.

1. Inspect het bestand `ui.frontend/dist/clientlib-site/site.css` :

   ![ Gecompileerde Plaats CSS ](../assets/style-cif-component/comiled-site-css.png)

   Het dossier is de gecompileerde en geminificeerde versie van alle dossiers van de Klasse in het project.

   >[!NOTE]
   >
   > Bestanden als deze worden genegeerd vanuit de broncontrole omdat deze tijdens de ontwikkeltijd moeten worden gegenereerd.

1. Inspect het bestand `ui.frontend/clientlib.config.js` .

   ```js
   /* clientlib.config.js*/
   ...
   // Config for `aem-clientlib-generator`
   module.exports = {
       context: BUILD_DIR,
       clientLibRoot: CLIENTLIB_DIR,
       libs: [
           {
               ...libsBaseConfig,
               name: 'clientlib-site',
               categories: ['venia.site'],
               dependencies: ['venia.dependencies', 'aem-core-cif-react-components'],
               assets: {
   ...
   ```

   Dit configuratiedossier is voor [ aem-clientlib-generator ](https://github.com/wcm-io-frontend/aem-clientlib-generator) en bepaalt waar en hoe gecompileerde CSS en JavaScript in een AEM cliëntbibliotheek worden omgezet.

1. Controleer het bestand in de module `ui.apps` : `ui.apps/src/main/content/jcr_root/apps/venia/clientlibs/clientlib-site/css/site.css`

   ![ Gecompileerde Plaats CSS in ui.apps ](../assets/style-cif-component/comiled-css-ui-apps.png)

   Dit bestand wordt `site.css` gekopieerd naar het `ui.apps` -project. Het maakt nu deel uit van een clientbibliotheek met de naam `clientlib-site` en een categorie `venia.site` . Zodra het bestand deel uitmaakt van de module `ui.apps` , kan het worden geïmplementeerd op AEM.

   >[!NOTE]
   >
   > Bestanden als deze worden ook genegeerd vanuit de broncontrole omdat deze tijdens de ontwikkeltijd moeten worden gegenereerd.

1. Inspecteer dan de andere cliëntbibliotheken die door het project worden geproduceerd:

   ![ Andere bibliotheken van de Cliënt ](../assets/style-cif-component/other-clientlibs.png)

   Deze clientbibliotheken worden niet beheerd door de module `ui.frontend` . In plaats daarvan bevatten deze clientbibliotheken CSS- en JavaScript-afhankelijkheden die door Adobe worden verschaft. De definitie voor deze clientbibliotheken staat in het `.content.xml` -bestand onder elke map.

   **clientlib-basis** - een lege cliëntbibliotheek die eenvoudig de noodzakelijke gebiedsdelen van [ AEM de Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) inbedt. De categorie is `venia.base` .

   **client-cif** - een lege cliëntbibliotheek die eenvoudig de noodzakelijke gebiedsdelen van [ inbedt AEM de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components) CIF. De categorie is `venia.cif` .

   **clientlib-net** - omvat CSS om AEM het Responsieve bezit van het Net toe te laten. Het gebruiken van het AEM net laat [ Wijze van de Lay-out ](/help/sites-cloud/authoring/page-editor/responsive-layout.md) in de AEMRedacteur toe en geeft inhoudsauteurs de capaciteit resize componenten. De categorie is `venia.grid` en is ingesloten in de `venia.base` -bibliotheek.

1. Inspect de bestanden `customheaderlibs.html` en `customfooterlibs.html` beneath `ui.apps/src/main/content/jcr_root/apps/venia/components/page` :

   ![ de manuscripten van de Kopbal en van de Voettekst van de Douane ](../assets/style-cif-component/custom-header-footer-script.png)

   Deze manuscripten omvatten **venia.base** en **venia.cif** bibliotheken als deel van alle pagina&#39;s.

   >[!NOTE]
   >
   > Alleen de basisbibliotheken zijn &#39;hard-coded&#39; als onderdeel van de paginascripts. `venia.site` is niet opgenomen in deze bestanden en maakt in plaats daarvan deel uit van de paginasjabloon voor meer flexibiliteit. Dit proces wordt later geïnspecteerd.

1. Van de terminal, bouw en stel het volledige project aan een lokaal geval van AEM op:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

## Auteur van een producttaser {#author-product-teaser}

Nu de codeupdates zijn opgesteld, voeg een geval van de component van de Teaser van het Product aan de homepage van de plaats toe gebruikend de AEM auteurshulpmiddelen. Hiermee kunnen we de bijgewerkte stijlen weergeven.

1. Open een nieuw browser lusje en navigeer aan de **Pagina van het Huis** van de plaats: [ http://localhost:4502/editor.html/content/venia/us/en.html ](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Breid de Vinder van Activa (de zijspoor) op **uit geeft** wijze uit. Schakelaar de filter van Activa aan **Producten**.

   ![ breid de Vinder en de filter van Activa door Producten ](../assets/style-cif-component/drag-drop-product-page.png) uit

1. Sleep een nieuw product naar de startpagina in de container van de hoofdlay-out:

   ![ Teaser van het Product met roze grens ](../assets/style-cif-component/pink-border-product-teaser.png)

   U moet zien dat de Product Teaser nu een helderroze rand heeft die is gebaseerd op de eerder gemaakte CSS-regelwijziging.

## Clientbibliotheken op de pagina controleren {#verify-client-libraries}

Controleer vervolgens de opname van de clientbibliotheken op de pagina.

1. Navigeer aan de **Pagina van het Huis** van de plaats: [ http://localhost:4502/editor.html/content/venia/us/en.html ](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Selecteer het **menu van de Informatie van de Pagina** en klik **Mening zoals Gepubliceerd**:

   ![ Mening zoals Gepubliceerd ](../assets/style-cif-component/view-as-published.png)

   Deze pagina wordt geopend zonder dat de AEM auteur JavaScript is geladen, zoals deze op de gepubliceerde site wordt weergegeven. De URL bevat de queryparameter `?wcmmode=disabled` . Bij het ontwikkelen van CSS en JavaScript is het aan te raden deze parameter te gebruiken om de pagina te vereenvoudigen zonder dat AEM auteur dit doet.

1. Bekijk de paginabron en u zou verscheidene cliëntbibliotheken moeten kunnen identificeren inbegrepen zijn:

   ```html
   <!DOCTYPE html>
   <html lang="en-US">
   <head>
       ...
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-base.min.css" type="text/css">
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-site.min.css" type="text/css">
   </head>
   ...
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-site.min.js"></script>
       <script type="text/javascript" src="/etc.clientlibs/core/wcm/components/commons/site/clientlibs/container.min.js"></script>
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-base.min.js"></script>
   <script type="text/javascript" src="/etc.clientlibs/core/cif/clientlibs/common.min.js"></script>
   <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-cif.min.js"></script>
   </body>
   </html>
   ```

   De bibliotheken van de cliënt wanneer geleverd aan de pagina worden vooraf bepaald met `/etc.clientlibs` en via a [ volmacht ](/help/implementing/developing/introduction/clientlibs.md) gediend om het even wat binnen te vermijden blootstellend gevoelig `/apps` of `/libs`.

   Opmerking `venia/clientlibs/clientlib-site.min.css` en `venia/clientlibs/clientlib-site.min.js` . Deze bestanden zijn de gecompileerde CSS- en JavaScript-bestanden die zijn afgeleid van de module `ui.frontend` .

## Opname van clientbibliotheek met paginasjablonen {#client-library-inclusion-pagetemplates}

Er zijn verschillende opties voor het opnemen van een bibliotheek aan de clientzijde. Inspecteer daarna hoe het geproduceerde project de `clientlib-site` bibliotheken via [ Malplaatjes van de Pagina ](/help/implementing/developing/components/templates.md) omvat.

1. Navigeer aan de **Pagina van het Huis** van de plaats binnen de Redacteur van de AEM: [ http://localhost:4502/editor.html/content/venia/us/en.html ](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Selecteer het **menu van de Informatie van de Pagina** en klik **uitgeven Malplaatje**:

   ![ geef het malplaatje ](../assets/style-cif-component/edit-template.png) uit

   Het **Landing malplaatje van de Pagina** wordt geopend dat de **3} pagina van het Huis {op wordt gebaseerd.**

   >[!NOTE]
   >
   > Om alle beschikbare malplaatjes van het AEM scherm van het Begin te bekijken, navigeer aan **Hulpmiddelen** > **Algemeen** > **Malplaatjes**.

1. In de hogere linkerhoek, selecteer het **pictogram van de Informatie van de Pagina** en klik **Beleid van de Pagina**.

   ![ het menupunt van het beleid van de Pagina ](../assets/style-cif-component/page-policy-menu.png)

1. Het paginabeleid wordt geopend voor de sjabloon Openingspagina:

   ![ Beleid van de Pagina - landende pagina ](../assets/style-cif-component/page-policy-properties.png)

   Aan de rechterkant, kunt u een lijst van de Bibliotheken van de Cliënt **categorieën** zien die op alle pagina&#39;s inbegrepen zijn die dit malplaatje gebruiken.

   * `venia.dependencies` - Biedt leveranciersbibliotheken waarvan `venia.site` afhankelijk is.
   * `venia.site` - De categorie voor `clientlib-site` die de module `ui.frontend` genereert.

   Bericht dat andere malplaatjes het zelfde beleid gebruiken, **de Pagina van de Inhoud**, **het Bestaan Pagina**, etc. Door hetzelfde beleid opnieuw te gebruiken, zorgt het ervoor dat dezelfde clientbibliotheken op alle pagina&#39;s worden opgenomen.

   Het voordeel van het gebruiken van Malplaatjes en het beleid van de Pagina om de opneming van cliëntbibliotheken te beheren is dat u het beleid per malplaatje kunt veranderen. U beheert bijvoorbeeld twee verschillende merken binnen dezelfde AEM. Elk merk heeft zijn eigen unieke stijl of *thema* maar de basisbibliotheken en de code zijn het zelfde. Een ander voorbeeld: als u een grotere clientbibliotheek had die u alleen op bepaalde pagina&#39;s wilde weergeven, kon u een uniek paginabeleid maken, alleen voor die sjabloon.

## Lokale WebPack-ontwikkeling {#local-webpack-development}

In de vorige oefening, werd een update gemaakt aan een dossier van de Klasse in de `ui.frontend` module en toen na het uitvoeren van een Maven bouwt de veranderingen aan AEM worden opgesteld. Vervolgens kunt u een webpack-dev-server gebruiken om de front-end stijlen snel te ontwikkelen.

Met de webpack-dev-server worden afbeeldingen en sommige van de CSS/JavaScript vanuit de lokale versie van AEM geleverd, maar kan de ontwikkelaar de stijlen en JavaScript in de module `ui.frontend` wijzigen.

1. In browser navigeer aan het **Huis** pagina en **Mening zoals Gepubliceerd**: [ http://localhost:4502/content/venia/us/en.html?wcmmode=disabled ](http://localhost:4502/content/venia/us/en.html?wcmmode=disabled).

1. Bekijk de bron van de pagina en **exemplaar** de ruwe HTML van de pagina.

1. Ga terug naar de IDE van uw keuze onder de module `ui.frontend` om het bestand te openen: `ui.frontend/src/main/static/index.html`

   ![ Statisch Dossier van HTML ](../assets/style-cif-component/static-index-html.png)

1. Overschrijf de inhoud van `index.html` en **deeg** de HTML die in de vorige stap wordt gekopieerd.

1. Zoek &quot;omvat&quot;voor `clientlib-site.min.css`, `clientlib-site.min.js`, en **verwijdert** hen.

   ```html
   <head>
       <!-- remove this link -->
       <link rel="stylesheet" href="/etc.clientlibs/venia/clientlibs/clientlib-base.min.css" type="text/css">
       ...
   </head>
   <body>
       ...
        <!-- remove this link -->
       <script type="text/javascript" src="/etc.clientlibs/venia/clientlibs/clientlib-site.min.js"></script>
   </body>
   ```

   Deze include-bestanden worden verwijderd omdat ze de gecompileerde versie van de CSS en JavaScript vertegenwoordigen die door de module `ui.frontend` worden gegenereerd. Laat de andere clientbibliotheken ongewijzigd, omdat ze vanaf de actieve AEM worden proxy.

1. Open een nieuw terminalvenster en navigeer naar de map `ui.frontend` . Voer de opdracht `npm start` uit:

   ```shell
   $ cd ui.frontend
   $ npm start
   ```

   Dit bevel begint webpack-dev-server op [ http://localhost:8080/](http://localhost:8080/)

   >[!CAUTION]
   >
   > Als er een fout met betrekking tot Voldoende antwoorden optreedt, stopt u de server en voert u de opdracht `npm rebuild node-sass` uit. Herhaal de bovenstaande stappen. Deze fout kan optreden als u een andere versie van `npm` en `node` hebt dan in het project `aem-cif-guides-venia/pom.xml` is opgegeven.

1. Navigeer aan [ http://localhost:8080/ ](http://localhost:8080/) in een nieuw lusje met zelfde browser zoals het programma geopende geval van AEM. U moet de startpagina van Venia zien via de webpack-dev-server:

   ![ WebPack dev server op haven 80 ](../assets/style-cif-component/webpack-dev-server-port80.png)

   Laat de webpack-dev-server actief. Het wordt gebruikt in de volgende oefening.

## Kaartstijl voor productteam implementeren {#update-css-product-teaser}

Wijzig vervolgens de bestanden Sass in de module `ui.frontend` om een kaartachtige stijl voor de producttaser te implementeren. De webpack-dev-server wordt gebruikt om de wijzigingen snel te zien.

Terugkeer aan winde en het geproduceerde project.

1. In de {**module 0} ui.frontend, open het dossier `_productteaser.scss` bij `ui.frontend/src/main/styles/commerce/_productteaser.scss` opnieuw.**

1. Breng de volgende wijzigingen aan in de rand Product Teaser:

   ```diff
       .item__image {
   -       border: #ea00ff 8px solid;
   +       border-bottom: 1px solid #c0c0c0;
           display: block;
           grid-area: main;
           height: auto;
           opacity: 1;
           transition-duration: 512ms;
           transition-property: opacity, visibility;
           transition-timing-function: ease-out;
           visibility: visible;
           width: 100%;
       }
   ```

   Sla de wijzigingen op en de webpack-dev-server moet automatisch vernieuwen met de nieuwe stijlen.

1. Voeg een slagschaduw toe en neem afgeronde hoeken op in de producttaser.

   ```scss
    .item__root {
        position: relative;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
        border-radius: 5px;
        float: left;
        margin-left: 12px;
        margin-right: 12px;
   }
   
   .item__root:hover {
      box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
   }
   ```

1. Werk de naam van het product bij zodat deze onder aan het gummetje wordt weergegeven en wijzig de tekstkleur.

   ```css
   .item__name {
       color: #000;
       display: block;
       float: left;
       font-size: 22px;
       font-weight: 900;
       line-height: 1em;
       padding: 0.75em;
       text-transform: uppercase;
       width: 75%;
   }
   ```

1. Werk de prijs van het product bij zodat deze ook onder aan het gummetje wordt weergegeven en wijzig de tekstkleur.

   ```css
   .price {
       color: #000;
       display: block;
       float: left;
       font-size: 18px;
       font-weight: 900;
       padding: 0.75em;
       padding-bottom: 2em;
       width: 25%;
   
       ...
   ```

1. Werk de media vraag bij de bodem bij, zodat kunt u de naam en de prijs in schermen stapelen kleiner dan **992px**.

   ```css
   @media (max-width: 992px) {
       .productteaser .item__name {
           font-size: 18px;
           width: 100%;
       }
       .productteaser .item__price {
           font-size: 14px;
           width: 100%;
       }
   }
   ```

   De kaartstijl wordt nu weerspiegeld in de webpack-dev-server:

   ![ het teaserveranderingen van de Server van de Dev van de Pakket Dev ](../assets/style-cif-component/webpack-dev-server-teaser-changes.png)

   De wijzigingen zijn echter nog niet AEM. U kunt [ het oplossingsdossier hier ](../assets/style-cif-component/_productteaser.scss) downloaden.

1. Stel de updates op om AEM te gebruiken uw Maven vaardigheden, van een bevel-lijn terminal:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

   >[!NOTE]
   >Er zijn extra [ Opstelling van winde en Hulpmiddelen ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) die projectdossiers rechtstreeks aan een lokale AEM instantie kunnen synchroniseren zonder het moeten een volledige Gemaakt bouwstijl uitvoeren.

## Bijgewerkte producttaser weergeven {#view-updated-product-teaser}

Nadat de code voor het project aan AEM is opgesteld, zou u de veranderingen in de Teaser van het Product nu moeten kunnen zien.

1. Keer aan uw browser terug en vernieuw de Homepage: [ http://localhost:4502/editor.html/content/venia/us/en.html ](http://localhost:4502/editor.html/content/venia/us/en.html). De bijgewerkte stijlen voor productgummeters moeten worden toegepast.

   ![ Bijgewerkte stijl van de Teaser van het Product ](../assets/style-cif-component/product-teaser-new-style.png)

1. Experimenteer door extra Product teasers toe te voegen. Gebruik de modus Lay-out om de breedte en verschuiving van de componenten te wijzigen en meerdere trappen in een rij weer te geven.

   ![ Veelvoudige Teasers van het Product ](../assets/style-cif-component/multiple-teasers-final.png)

## Problemen oplossen {#troubleshooting}

U kunt in [ CRXDE-Lite ](http://localhost:4502/crx/de/index.jsp) verifiëren dat het bijgewerkte CSS dossier is opgesteld: [ http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css ](http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css)

Bij het implementeren van nieuwe CSS-bestanden of JavaScript-bestanden, of beide, is het ook belangrijk ervoor te zorgen dat de browser geen bestanden met een vaste status levert. U kunt dit potentiële probleem verhelpen door het cachegeheugen van de browser te wissen of een nieuwe browsersessie te starten.

AEM probeert ook clientbibliotheken in cache te plaatsen voor prestaties. Soms, na een codeplaatsing worden de oudere dossiers gediend. U kunt AEM het geheime voorgeheugen van de cliëntbibliotheek manueel ongeldig maken gebruikend het [ hulpmiddel van de Bibliotheken van de Cliënt van de Rebuild ](http://localhost:4502/libs/granite/ui/content/dumplibs.rebuild.html). *ongeldig Caches is de aangewezen methode als u vermoedt AEM een oude versie van een cliëntbibliotheek in het voorgeheugen onder heeft gebracht. Het opnieuw bouwen van Bibliotheken is inefficiënt en tijdrovend.*

## Gefeliciteerd {#congratulations}

U hebt uw eerste AEM Core Component opgemaakt en u hebt een webpack Dev-server gebruikt!

## Bonus Challenge {#bonus-challenge}

Gebruik het [ systeem van de Stijl van de AEM ](/help/sites-cloud/authoring/page-editor/style-system.md) om twee stijlen tot stand te brengen die of van door een inhoudsauteur kunnen worden van een knevel voorzien. [ het Ontwikkelen met het Systeem van de Stijl ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/style-system.html) omvat gedetailleerde stappen en informatie over hoe te om deze taak te verwezenlijken.

![ Uitdaging van de Bonus - stijlSysteem ](../assets/style-cif-component/bonus-challenge.png)

## Aanvullende bronnen {#additional-resources}

* [ AEM Archetype van het Project ](https://github.com/adobe/aem-project-archetype)
* [ AEM CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components)
* [ opstelling een Lokale Milieu van de Ontwikkeling van de AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html)
* [Client-Side bibliotheken](/help/implementing/developing/introduction/clientlibs.md)
* [ Begonnen het worden met AEM Sites ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)
* [ het Ontwikkelen met het Systeem van de Stijl ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/style-system.html)
