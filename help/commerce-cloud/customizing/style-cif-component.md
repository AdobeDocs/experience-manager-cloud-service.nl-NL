---
title: Stijl AEM CIF Core-componenten
description: Leer hoe u AEM CIF Core Components opmaakt. In de zelfstudie wordt uitgelegd hoe bibliotheken of clientlibs aan de clientzijde worden gebruikt voor de implementatie en het beheer van CSS en Javascript voor een Adobe Experience Manager (AEM) Commerce-implementatie. Deze zelfstudie behandelt ook hoe de module ui.frontend en een webpack-project worden geïntegreerd in het end-to-end buildproces.
sub-product: handel
topics: front-end-development
version: cloud-service
doc-type: tutorial
activity: develop
audience: developer
kt: 3456
thumbnail: 3456-style-cif.jpg
translation-type: tm+mt
source-git-commit: 1e8603a27af30ab394297b9f40491d93bc7d4ef4
workflow-type: tm+mt
source-wordcount: '2604'
ht-degree: 0%

---


# Stijl AEM CIF Core-componenten {#style-aem-cif-core-components}

Het [CIF Venia-project](https://github.com/adobe/aem-cif-guides-venia) is een referentiecode voor het gebruik van [CIF Core Components](https://github.com/adobe/aem-core-cif-components). In deze zelfstudie inspecteert u het Venia-referentieproject en begrijpt u hoe CSS en JavaScript die door AEM CIF Core-componenten worden gebruikt, zijn geordend. U maakt ook een nieuwe stijl met CSS om de standaardstijl van de **component Product Teaser** bij te werken.

>[!TIP]
>
> Gebruik [AEM archetype](https://github.com/adobe/aem-project-archetype) van het Project wanneer het beginnen van uw eigen handelsimplementatie.

## Wat u gaat maken

Er wordt een nieuwe stijl geïmplementeerd voor de component Product Teaser die op een kaart lijkt.

![Wat u gaat maken](../assets/style-cif-component/what-you-will-build.png)

## Vereisten {#prerequisites}

U hebt een lokale ontwikkelomgeving nodig om deze zelfstudie te voltooien. Dit omvat een lopende instantie van AEM die wordt gevormd en met een instantie van Magento verbonden. Herzie de vereisten en de stappen voor [vestiging een lokale ontwikkeling met AEM als Cloud Service SDK](../develop.md).

## Het Venia-project klonen {#clone-venia-project}

We klonen het [Venia-project](https://github.com/adobe/aem-cif-guides-venia) en overschrijven vervolgens de standaardstijlen.

>[!NOTE]
>
> **Voel u vrij om een bestaand project** te gebruiken (gebaseerd op het AEM Projectarchetype met CIF inbegrepen) en deze sectie over te slaan.

1. Voer de volgende git-opdracht uit om het project te klonen:

   ```shell
   $ git clone git@github.com:adobe/aem-cif-guides-venia.git
   ```

1. Bouw en stel het project aan een lokaal geval van AEM op:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

1. Voeg de noodzakelijke configuraties OSGi toe om uw AEM instantie met een instantie van de Magento te verbinden of de configuraties aan het onlangs gecreeerd project toe te voegen.

1. Op dit punt zou u een werkende versie van een storefront moeten hebben die met een instantie van Magento wordt verbonden. Navigeer naar de pagina `US` > `Home` op: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

   Je moet zien dat de winkel het thema Venia gebruikt. Als u het hoofdmenu van de storefront uitbreidt, ziet u verschillende categorieën die aangeven dat de Magento van de verbinding werkt.

   ![Storefront geconfigureerd met Venia-thema](../assets/style-cif-component/venia-store-configured.png)

## Clientbibliotheken en de module ui.frontend {#introduction-to-client-libraries}

De CSS en JavaScript die verantwoordelijk zijn voor het renderen van het thema of de stijlen van de storefront worden in AEM beheerd door een [clientbibliotheek](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html) of door clientlibs voor korte tijd. Clientbibliotheken bieden een mechanisme voor het indelen van CSS en Javascript in de code van een project en leveren vervolgens op de pagina.

Brand-specifieke stijlen kunnen worden toegepast op AEM CIF Core-componenten door de CSS die door deze clientbibliotheken wordt beheerd, toe te voegen en te overschrijven. Inzicht in de structuur van clientbibliotheken en de inhoud van deze bibliotheken op de pagina is van essentieel belang.

Het [bestand ui.frontend](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/uifrontend.html) is een speciaal [webpack](https://webpack.js.org/) -project voor het beheer van alle front-end assets voor een project. Op deze manier kunnen ontwikkelaars aan de voorzijde elk aantal talen en technologieën gebruiken, zoals [TypeScript](https://www.typescriptlang.org/), [Sass](https://sass-lang.com/) en nog veel meer.

De `ui.frontend` module is ook een Geweven module en geïntegreerd met het grotere project door het gebruik van een module NPM de [aem-clientlib-generator](https://github.com/wcm-io-frontend/aem-clientlib-generator). Tijdens een build worden de gecompileerde CSS- en JavaScript-bestanden naar een clientbibliotheek in de `aem-clientlib-generator` `ui.apps` module gekopieerd.

![ui.frontend naar ui.apps-architectuur](../assets/style-cif-component/ui-frontend-architecture.png)

*Gecompileerde CSS en Javascript worden gekopieerd van de`ui.frontend`module in de`ui.apps`module als bibliotheek van de Cliënt tijdens een Maven bouwt*

## Teastijl bijwerken {#ui-frontend-module}

Breng vervolgens een kleine wijziging aan in de stijl Teaser om te zien hoe de `ui.frontend` module en clientbibliotheken werken. Gebruik [de IDE van uw keus](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#set-up-the-development-ide) om het project van Venia in te voeren. De gebruikte schermafbeeldingen zijn van winde van de Code van [Visual Studio](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#microsoft-visual-studio-code).

1. Navigeer en vouw de module **ui.frontend** uit en breid de omslaghiërarchie uit aan: `ui.frontend/src/main/styles/commerce`:

   ![ui.frontend commercemap](../assets/style-cif-component/ui-frontend-commerce-folder.png)

   U ziet dat de map meerdere bestanden voor de slacht (`.scss`) bevat. Dit zijn de specifieke stijlen van de Handel voor elk van de componenten van de Handel.

1. Open the file `_productteaser.scss`.

1. Werk de `.item__image` regel bij en wijzig de randregel:

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

   De bovenstaande regel moet een zeer vette, roze rand toevoegen aan de Product Teaser Component.

1. Open een nieuw terminalvenster en navigeer naar de `ui.frontend` map:

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

   Inspect de einduitvoer. U zult zien dat het Geweven bevel verscheidene manuscripten NPM met inbegrip van uitvoerde `npm run build`. Het `npm run build` bevel wordt bepaald in het `package.json` dossier en heeft het effect van het compileren van het webpack project en het teweegbrengen van de cliëntbibliotheek.

1. Inspect het bestand `ui.frontend/dist/clientlib-site/site.css`:

   ![Gecompileerde site-CSS](../assets/style-cif-component/comiled-site-css.png)

   Het bestand is de gecompileerde en geminiatuurde versie van alle bestanden in het project.

   >[!NOTE]
   >
   > Bestanden als deze worden genegeerd vanuit de broncontrole omdat deze tijdens de ontwikkeltijd moeten worden gegenereerd.

1. Inspect het bestand `ui.frontend/clientlib.config.js`.

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

   Dit is het configuratiebestand voor [aem-clientlib-generator](https://github.com/wcm-io-frontend/aem-clientlib-generator) en bepaalt waar en hoe de gecompileerde CSS en JavaScript worden getransformeerd in een AEM clientbibliotheek.

1. Controleer het bestand in de `ui.apps` module: `ui.apps/src/main/content/jcr_root/apps/venia/clientlibs/clientlib-site/css/site.css`:

   ![Gecompileerde site-CSS in ui.apps](../assets/style-cif-component/comiled-css-ui-apps.png)

   Dit het gekopieerde `site.css` dossier in het `ui.apps` project. Het maakt nu deel uit van een clientbibliotheek die is benoemd `clientlib-site` met een categorie `venia.site`. Zodra het dossier deel van de `ui.apps` module uitmaakt kan het aan AEM worden opgesteld.

   >[!NOTE]
   >
   > Bestanden als deze worden ook genegeerd vanuit de broncontrole omdat deze tijdens de ontwikkeltijd moeten worden gegenereerd.

1. Inspecteer dan de andere cliëntbibliotheken die door het project worden geproduceerd:

   ![Andere clientbibliotheken](../assets/style-cif-component/other-clientlibs.png)

   Deze cliëntbibliotheken worden niet beheerd door de `ui.frontend` module. In plaats daarvan bevatten deze clientbibliotheken CSS- en JavaScript-afhankelijkheden die door Adobe worden verschaft. De definitie voor deze clientbibliotheken staat in het `.content.xml` bestand onder elke map.

   **clientlib-base** - Dit is een lege clientbibliotheek die eenvoudig de noodzakelijke afhankelijkheden van [AEM Core Components](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html)insluit. De categorie is `venia.base`.

   **ClientLib-cif** - Dit is ook een lege cliëntbibliotheek die eenvoudig de noodzakelijke gebiedsdelen van [AEM](https://github.com/adobe/aem-core-cif-components)van de Kern van CIF inbedt. De categorie is `venia.cif`.

   **clientlib-grid** - Dit omvat de CSS nodig om AEM functie Responsief raster in te schakelen. Met het AEM schakelt u de [Lay-outmodus](https://docs.adobe.com/content/help/en/experience-manager-65/administering/operations/configuring-responsive-layout.html#include-the-responsive-css) in de AEM-editor in en stelt u de auteurs van de inhoud in staat de grootte van componenten te wijzigen. De categorie is ingesloten in de `venia.grid` `venia.base` bibliotheek.

1. Inspect de bestanden `customheaderlibs.html` en `customfooterlibs.html` eronder `ui.apps/src/main/content/jcr_root/apps/venia/components/page`:

   ![Scripts voor Aangepaste kopteksten en voetteksten](../assets/style-cif-component/custom-header-footer-script.png)

   Deze scripts bevatten **venia.base** - en **venia.cif** -bibliotheken als onderdeel van alle pagina&#39;s.

   >[!NOTE]
   >
   > Alleen de basisbibliotheken zijn &#39;hard-coded&#39; als onderdeel van de paginascripts. `venia.site` is niet opgenomen in deze bestanden en wordt in plaats daarvan opgenomen als onderdeel van de paginasjabloon voor meer flexibiliteit. Dit wordt later geïnspecteerd.

1. Van de terminal, bouw en stel het volledige project aan een lokaal geval van AEM op:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

## Auteur van een producttaser {#author-product-teaser}

Nu de codeupdates zijn opgesteld, voeg een nieuw geval van de component van de Teaser van het Product aan de homepage van de plaats toe gebruikend de AEM auteurshulpmiddelen. Hierdoor kunnen we de bijgewerkte stijlen bekijken.

1. Open een nieuw browsertabblad en navigeer naar de **startpagina** van de site: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Vouw de Finder voor middelen (de zijspoor) uit in de modus **Bewerken** . Schakel het filter Element naar **Producten**.

   ![De Finder en het filter Middelen uitvouwen op producten](../assets/style-cif-component/drag-drop-product-page.png)

1. Sleep een nieuw product naar de startpagina in de container van de hoofdlay-out:

   ![Producttaser met roze rand](../assets/style-cif-component/pink-border-product-teaser.png)

   Het productteam heeft nu een helderroze rand die is gebaseerd op de eerder gemaakte CSS-regelwijziging.

## Clientbibliotheken op de pagina controleren {#verify-client-libraries}

Controleer vervolgens de opname van de clientbibliotheken op de pagina.

1. Ga naar de **startpagina** van de site: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Selecteer het menu **Pagina-informatie** en klik op **Weergeven als gepubliceerd**:

   ![Weergeven als gepubliceerd](../assets/style-cif-component/view-as-published.png)

   Hierdoor wordt de pagina geopend zonder dat de AEM auteur javascript is geladen, zoals deze op de gepubliceerde site wordt weergegeven. Bericht dat url de vraagparameter heeft `?wcmmode=disabled` toegevoegd. Bij het ontwikkelen van CSS en Javascript is het een goede praktijk om deze parameter te gebruiken om de pagina met om het even wat van AEM auteur te vereenvoudigen.

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

   Clientbibliotheken die aan de pagina worden geleverd, worden vooraf gekoppeld `/etc.clientlibs` en via een [proxy](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet) aangeboden, zodat alles wat gevoelig is in `/apps` of `/libs`niet wordt belicht.

   Opmerking `venia/clientlibs/clientlib-site.min.css` en `venia/clientlibs/clientlib-site.min.js`. Dit zijn de gecompileerde CSS en Javascript dossiers die uit de `ui.frontend` module worden afgeleid.

## Opname van clientbibliotheek met paginasjablonen {#client-library-inclusion-pagetemplates}

Er zijn verschillende opties voor het opnemen van een bibliotheek aan de clientzijde. Ga vervolgens na hoe het gegenereerde project de `clientlib-site` bibliotheken via [paginasjablonen](https://docs.adobe.com/content/help/en/experience-manager-65/developing/platform/templates/page-templates-editable.html)bevat.

1. Navigeer naar de **startpagina** van de site in de AEM Editor: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

1. Selecteer het menu **Pagina-informatie** en klik op Sjabloon **** bewerken:

   ![De sjabloon bewerken](../assets/style-cif-component/edit-template.png)

   Hiermee wordt de sjabloon voor de **landingspagina** geopend waarop de **startpagina** is gebaseerd.

   >[!NOTE]
   >
   > Navigeer naar **Gereedschappen** > **Algemeen** > **Sjablonen** om alle beschikbare sjablonen weer te geven vanuit het scherm Start.

1. Selecteer in de linkerbovenhoek het pictogram **Pagina-informatie** en klik op **Paginabeleid**.

   ![Menu-item voor paginabeleid](../assets/style-cif-component/page-policy-menu.png)

1. Hiermee wordt het paginabeleid voor de sjabloon Openingspagina geopend:

   ![Paginabeleid - bestemmingspagina](../assets/style-cif-component/page-policy-properties.png)

   Rechts ziet u een lijst met **categorieën** Client Libraries die worden opgenomen op alle pagina&#39;s die deze sjabloon gebruiken.

   * `venia.dependencies` - Biedt leveranciersbibliotheken die `venia.site` hiervan afhankelijk zijn.
   * `venia.site` - Dit is de categorie voor `clientlib-site` de `ui.frontend` module.

   Andere sjablonen gebruiken hetzelfde beleid, dezelfde **inhoudspagina**, dezelfde **bestemmingspagina**, enzovoort.. Door hetzelfde beleid opnieuw te gebruiken, kunnen we ervoor zorgen dat dezelfde clientbibliotheken op alle pagina&#39;s worden opgenomen.

   Het voordeel van het gebruiken van Malplaatjes en het beleid van de Pagina om de opneming van cliëntbibliotheken te beheren is dat u het beleid per malplaatje kunt veranderen. U beheert bijvoorbeeld twee verschillende merken binnen dezelfde AEM. Elk merk heeft zijn eigen unieke stijl of *thema* , maar de basisbibliotheken en -code zijn hetzelfde. Een ander voorbeeld: als u een grotere clientbibliotheek had die u alleen op bepaalde pagina&#39;s wilde weergeven, kon u een uniek paginabeleid maken, alleen voor die sjabloon.

## Ontwikkeling van lokale webpakketten {#local-webpack-development}

In de vorige oefening, werd een update gemaakt aan een dossiers van de Klasse in de `ui.frontend` module en toen na het uitvoeren van een Maven bouwt de veranderingen worden opgesteld aan AEM. Vervolgens bekijken we hoe we een webpack-dev-server kunnen gebruiken om de front-end stijlen snel te ontwikkelen.

Met de webpack-dev-server worden afbeeldingen en sommige van de CSS/JavaScript-code uit de lokale versie van AEM beschikbaar gemaakt, maar kan de ontwikkelaar de stijlen en JavaScript-code in de `ui.frontend` module wijzigen.

1. Navigeer in de browser naar de pagina **Home** en **View as Published**: [http://localhost:4502/content/venia/us/en.html?wcmmode=disabled](http://localhost:4502/content/venia/us/en.html?wcmmode=disabled).

1. Bekijk de bron van de pagina en de **kopie** van de onbewerkte HTML van de pagina.

1. Keer terug naar winde van uw keus onder de `ui.frontend` module open het dossier: `ui.frontend/src/main/static/index.html`

   ![Statisch HTML-bestand](../assets/style-cif-component/static-index-html.png)

1. Overschrijf de inhoud van de HTML die u in de vorige stap hebt gekopieerd `index.html` en **plak** deze.

1. Zoek de include-bestanden voor deze bestanden `clientlib-site.min.css`en `clientlib-site.min.js` verwijder **** ze.

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

   Deze worden verwijderd omdat ze de gecompileerde versie vertegenwoordigen van de CSS en JavaScript die door de `ui.frontend` module zijn gegenereerd. Laat de andere clientbibliotheken ongewijzigd, omdat ze van de actieve AEM worden proxy&#39;s.

1. Open een nieuw terminalvenster en navigeer naar de `ui.frontend` map. Voer de opdracht uit `npm start`:

   ```shell
   $ cd ui.frontend
   $ npm start
   ```

   Hiermee wordt de webpack-dev-server gestart op [http://localhost:8080/](http://localhost:8080/)

   >[!CAUTION]
   >
   > Als er een fout met betrekking tot de score optreedt, stopt u de server en voert u de opdracht uit `npm rebuild node-sass` en herhaalt u de bovenstaande stappen. Dit kan voorkomen als een verschillende versie van `npm` en `node` dan gespecificeerd in het project `aem-cif-guides-venia/pom.xml`.

1. Navigeer naar [http://localhost:8080/](http://localhost:8080/) op een nieuw tabblad met dezelfde browser als een AEM die u hebt aangemeld. U moet de startpagina van Venia zien via de webpack-dev-server:

   ![Webpack-ontwikkelserver op poort 80](../assets/style-cif-component/webpack-dev-server-port80.png)

   Laat de webpack-dev-server actief. Het zal in de volgende oefening worden gebruikt.

## Kaartstijl voor productteam implementeren {#update-css-product-teaser}

Wijzig vervolgens de Sass-bestanden in de `ui.frontend` module om een op kaarten lijkende stijl voor de Product Teaser te implementeren. De webpack-dev-server wordt gebruikt om de wijzigingen snel te zien.

Terugkeer aan winde en het geproduceerde project.

1. Open in de module **ui.frontend** het bestand opnieuw `_productteaser.scss` bij `ui.frontend/src/main/styles/commerce/_productteaser.scss`.

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

1. Werk de mediaquery onderaan bij om de naam en de prijs te stapelen in schermen kleiner dan **992 px**.

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

   ![Wijzigingen in het testprogramma van WebPack Dev Server](../assets/style-cif-component/webpack-dev-server-teaser-changes.png)

   De wijzigingen zijn echter nog niet AEM. U kunt het [oplossingsdossier hier](../assets/style-cif-component/_productteaser.scss)downloaden.

1. Implementeer de updates om uw Maven-vaardigheden te AEM gebruiken via een opdrachtregelterminal:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

   >[!NOTE]
   >Er zijn extra Opstelling [van winde en Hulpmiddelen](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) die projectdossiers aan een lokale AEM instantie rechtstreeks kunnen synchroniseren zonder het moeten een volledige Gemaakt bouwstijl uitvoeren.

## Bijgewerkte producttaser weergeven {#view-updated-product-teaser}

Nadat de code voor het project aan AEM is opgesteld, zouden wij nu de veranderingen in de Teaser van het Product moeten kunnen zien.

1. Ga terug naar uw browser en vernieuw de startpagina: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html). De bijgewerkte stijlen voor productgummeters moeten worden toegepast.

   ![Bijgewerkte stijl van de Teaser van het Product](../assets/style-cif-component/product-teaser-new-style.png)

1. Experimenteer door extra Product teasers toe te voegen. Gebruik de modus Lay-out om de breedte en verschuiving van de componenten te wijzigen en meerdere trappen in een rij weer te geven.

   ![Meerdere productteams](../assets/style-cif-component/multiple-teasers-final.png)

## Problemen oplossen {#troubleshooting}

U kunt in [CRXDE-Lite](http://localhost:4502/crx/de/index.jsp) verifiëren dat het bijgewerkte CSS dossier is opgesteld: [http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css](http://localhost:4502/crx/de/index.jsp#/apps/venia/clientlibs/clientlib-site/css/site.css)

Bij het implementeren van nieuwe CSS- en/of JavaScript-bestanden is het ook belangrijk ervoor te zorgen dat de browser geen schaalbestanden aanbiedt. U kunt dit voorkomen door de browsercache te wissen of een nieuwe browsersessie te starten.

AEM probeert ook clientbibliotheken in cache te plaatsen voor prestaties. Af en toe, na een codeplaatsing worden de oudere dossiers gediend. U kunt AEM cache van de clientbibliotheek handmatig ongeldig maken met het gereedschap [Clientbibliotheken](http://localhost:4502/libs/granite/ui/content/dumplibs.rebuild.html)opnieuw samenstellen. *Schakel de voorkeursmethode Caches ongeldig maken in als u vermoedt dat AEM een oude versie van een clientbibliotheek in het cachegeheugen heeft opgeslagen. Het opnieuw samenstellen van bibliotheken is inefficiënt en tijdrovend.*

## Gefeliciteerd {#congratulations}

U hebt zojuist uw eerste AEM CIF Core-component vormgegeven en u hebt een webpack-ontwikkelserver gebruikt!

## Bonus Challenge {#bonus-challenge}

Gebruik het systeem [](https://docs.adobe.com/content/help/en/experience-manager-65/developing/components/style-system.html) AEM stijl om twee stijlen te maken die door de auteur van de inhoud in- en kunnen worden in- en uitgeschakeld. [Het ontwikkelen met het Systeem](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html) van de Stijl omvat gedetailleerde stappen en informatie over hoe te om dit te verwezenlijken.

![Bonus Challenge - Stijl Systeem](../assets/style-cif-component/bonus-challenge.png)

## Aanvullende bronnen {#additional-resources}

* [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)
* [AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components)
* [Een lokale AEM ontwikkelomgeving instellen](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html)
* [Client-Side bibliotheken](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html)
* [Aan de slag met AEM Sites](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)
* [Ontwikkelen met het Stijlsysteem](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html)
