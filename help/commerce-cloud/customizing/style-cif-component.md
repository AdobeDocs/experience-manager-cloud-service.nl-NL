---
title: Stijl AEM CIF Core-componenten
description: Stijl AEM CIF Core-componenten
translation-type: tm+mt
source-git-commit: 48805b21500ff3f2629efd6aecb40bb1cdc38cd6
workflow-type: tm+mt
source-wordcount: '2568'
ht-degree: 0%

---


# Stijl AEM CIF Core-componenten {#style-aem-cif-core-components}

Het archetype [van het Project](https://github.com/adobe/aem-cif-project-archetype) CIF leidt tot een minimaal Adobe Experience Manager (AEM) CIF project als uitgangspunt voor klantenprojecten gebruikend [AEM de Componenten](https://github.com/adobe/aem-core-cif-components)van de Kern van CIF. In eerste instantie wordt een standaardstijl, het zogenaamde merk Venia, op de site toegepast. In deze zelfstudie inspecteert u een nieuw AEM CIF-project, gegenereerd door het archetype, en begrijpt u hoe CSS en JavaScript die door AEM CIF Core-componenten worden gebruikt, zijn geordend. U maakt ook een nieuwe stijl met CSS die de standaardstijl van de component Product Teaser vervangt.

![Wat u gaat maken](/help/commerce-cloud/assets/style-cif-component/what-you-will-build.png)

>[!NOTE]
> Er wordt een nieuwe stijl geïmplementeerd voor de component Product Teaser die op een kaart lijkt.

## Vereisten {#prerequisites}

De volgende gereedschappen en technologieën zijn vereist:

* [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/index.html) of [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html) (alleen AEM 6.5+)
* [Apache Maven](https://maven.apache.org/) (3.3.9 of hoger)
* Adobe Experience Manager (lokale instantie)
   * [AEM 6,5](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/introduction/technical-requirements.html)
   * [AEM 6.4.4+](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/sp-release-notes.html)
* Magento die een [versie in werking stellen compatibel met archetype](https://github.com/adobe/aem-cif-project-archetype#requirements)

## Een project genereren {#generate-project}

Wij zullen een nieuw AEM CIF project produceren gebruikend het archetype [van het Project van](https://github.com/adobe/aem-cif-project-archetype) CIF en dan de standaardstijlen met voeten treden.

**Voel u vrij om een bestaand project** te gebruiken (gebaseerd op het CIF Project Archetype) en deze sectie over te slaan.

1. Bepaal de recentste versie van CIF Project Archetype door [de recentste versie op GitHub](https://github.com/adobe/aem-cif-project-archetype/releases/latest)te bekijken. In de volgende stap vervangt u de versie `x.y.z` van de nieuwste versie.

1. Stel het volgende Gemaakt bevel in werking om een nieuw project op [partijwijze](https://maven.apache.org/archetype/maven-archetype-plugin/examples/generate-batch.html)te produceren.

   ```terminal
   mvn archetype:generate -B \
       -DarchetypeGroupId="com.adobe.commerce.cif" \
       -DarchetypeArtifactId="cif-project-archetype" \
       -DarchetypeVersion=x.y.z \
       -DgroupId="com.acme.cif" \
       -DartifactId="acme-store" \
       -Dversion=0.0.1-SNAPSHOT \
       -Dpackage="com.acme.cif" \
       -DappsFolderName="acme" \
       -DartifactName="Acme Store" \
       -DcontentFolderName="acme" \
       -DpackageGroup="acme" \
       -DsiteName="Acme Store" \
       -DoptionAemVersion=6.5.0 \
       -DoptionIncludeExamples=y \
       -DoptionEmbedConnector=y
   ```

1. Bouw en stel het project aan een lokaal geval van AEM op:

   ```shell
   $ cd acme-store/
   $ mvn clean install -PautoInstallAll
   ```

1. Voeg de noodzakelijke configuraties OSGi toe om uw AEM instantie met een instantie van de Magento te verbinden of de configuraties aan het onlangs gecreeerd project toe te voegen.

1. Op dit punt zou u een werkende versie van een storefront moeten hebben die met een instantie van Magento wordt verbonden. Navigeer naar de pagina `US` > `Home` op: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

   Je moet zien dat de winkel het thema Venia gebruikt. Als u het hoofdmenu van de storefront uitbreidt, ziet u verschillende categorieën die aangeven dat de Magento van de verbinding werkt.

   ![Storefront geconfigureerd met het Venia-thema](/help/commerce-cloud/assets/style-cif-component/acme-store-configured.png)

## Inleiding tot clientbibliotheken {#introduction-to-client-libraries}

De CSS en JavaScript die verantwoordelijk zijn voor het renderen van het thema of de stijlen van de storefront worden in AEM beheerd door een [clientbibliotheek](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html) of door clientlibs voor korte tijd. Clientbibliotheken bieden een mechanisme voor het indelen van CSS en Javascript in de code van een project en leveren vervolgens op de pagina.

We kunnen merkspecifieke stijlen toepassen op AEM CIF Core Components door de CSS die door deze clientbibliotheken wordt beheerd, toe te voegen en te overschrijven. Inzicht in de structuur van clientbibliotheken en de inhoud van deze bibliotheken op de pagina is van essentieel belang.

### Projectclientbibliotheken {#project-client-libraries}

Daarna zullen wij de cliëntbibliotheken inspecteren die automatisch door archetype worden geproduceerd. Gebruik winde van uw keus om het project in te [voeren dat in de vorige oefening](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment)wordt geproduceerd.

1. Navigeer en vouw de module **ui.apps** uit en vouw de omslaghiërarchie uit aan: `ui.apps/src/main/content/jcr_root/apps/acme/clientlibs`:

   ![ui.apps clientlibs](/help/commerce-cloud/assets/style-cif-component/ui-apps-clientli-folder.png)

   Er zijn twee omslagen onder, **cliëntlib-basis** en **thema**.

1. **clientlib-base** - Dit is een lege clientbibliotheek die eenvoudig de noodzakelijke afhankelijkheden van [AEM Core Components](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html)insluit.

   ![Clientlib-basis](/help/commerce-cloud/assets/style-cif-component/clientlib-base-folderhierarchy.png)

   Hieronder ziet u de XML-definitie van **clientlib-base** (het `.content.xml` bestand):

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:ClientLibraryFolder"
       allowProxy="{Boolean}true"
       categories="[acme.wcm.base]"
       embed="[core.wcm.components.accordion.v1,core.wcm.components.tabs.v1,core.wcm.components.carousel.v1,core.wcm.components.image.v2,core.wcm.components.breadcrumb.v2,core.wcm.components.search.v1,core.wcm.components.form.text.v2]"/>
   ```

   `acme.wcm.base` is de categorie voor deze clientbibliotheek. U kunt een categorie zien als een tag. Hiermee wordt de bibliotheek op de pagina opgenomen of ingesloten.

   Let op de `embed` eigenschap en de array van andere clientlib-categorieën. Elk van deze categorieën vertegenwoordigt een clientbibliotheek. Dit is bijvoorbeeld het `core.wcm.components.accordion.v1` Javascript-object dat nodig is om de [component](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/accordion.html) Accordion te laten werken.

   Met de eigenschappen `embed` en `categories` eigenschappen kunt u clientbibliotheken van verschillende projecten beheren en opnemen.

   `allowProxy=true` zorgt ervoor dat de CSS- en JavaScript-clientbibliotheek worden aangeboden via een pad dat vooraf is ingesteld op: `/etc.clientlibs`. Zo blijft de toepassingscode onder `/apps` beschermd tegen eindgebruikers, maar CSS en JavaScript die nodig zijn om de website te laten functioneren, kunnen anoniem worden weergegeven. Meer informatie over de eigenschap [allowProxy vindt u hier](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet).

1. **theme** - This is the client library that contains the starting theme and CSS for the CIF project. Deze clientbibliotheek is ontworpen om door elke implementatie te worden aangepast en het is handig om met een aantal bestaande stijlen te beginnen, zodat de componenten functioneel zijn om mee te beginnen.

   ![theme-clientbibliotheek](/help/commerce-cloud/assets/style-cif-component/clientlib-theme-folder-hierarchy.png)

   Hieronder vindt u de XML-definitie van **thema**:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:ClientLibraryFolder"
       allowProxy="{Boolean}true"
       categories="[acme.theme]"/>
   ```

   `acme.theme` is de categorie voor deze clientbibliotheek en zo wordt de clientbibliotheek op de pagina opgenomen.

1. Onder de **thematclient-bibliotheek** ziet u een bestand met de naam **css.txt** op: `ui.apps/src/main/content/jcr_root/apps/acme/clientlibs/theme/css.txt`:

   ```plain
   #base=.
   common/common.css
   
   components/button/button.css
   
   components/featuredcategorylist/categorylist.css
   
   ...
   ```

   Het bestand **css.txt** (en **js.txt**) fungeert als manifesten die de volgorde bepalen waarin afzonderlijke bestanden in het uiteindelijke CSS-bestand worden opgenomen. Orden is belangrijk voor zowel CSS als JavaScript en het is handig om meerdere bestanden te kunnen maken om de code beter te kunnen beheren. Wanneer u het bestand **css.txt** doorzoekt, ziet u dat de bestanden zijn ingedeeld op basis van de componenten waarop de stijlen zijn toegepast.

1. Inspect de CSS-bestanden onder het **thema of de componenten** om een idee te krijgen van de stijlen van de taakcomponent. Enkele van deze bestanden worden later in de zelfstudie bijgewerkt.

### Insluiting clientbibliotheek met basispaginacomponent

Vervolgens wordt gecontroleerd hoe clientbibliotheken op een pagina worden opgenomen met [HTML](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html#using-htl) en de component Pagina.

1. Navigeer in de module **ui.apps** naar de definitie van de `page` component onder: `ui.apps/src/main/content/jcr_root/apps/acme/components/structure/page`. Deze **paginacomponent** , die door archetype wordt geproduceerd, is het ingangspunt dat wordt gebruikt om alle pagina&#39;s in het project terug te geven.

1. Als u de definitie van de **component page** (`page/.content.xml`) inspecteert, zult u een bezit opmerken `sling:resourceSuperType` dat aan `core/cif/components/structure/page/v1/page`richt. Dit betekent dat de **paginacomponent** van ons project (Acme) alle functionaliteit van de component van de Pagina [van de Kern van](https://github.com/adobe/aem-core-cif-components/tree/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/structure/page/v1/page) CIF zal erven, en ons toestaat om minder code te beheren.

1. Onder de **paginacomponent** vindt u twee bestanden: **customheaderlibs.html** en **customfooterlibs.html**.

   ```html
   <!--/* customheaderlibs.html */-->
   <sly data-sly-use.clientLib="/libs/granite/sightly/templates/clientlib.html"
    data-sly-call="${clientlib.css @ categories='acme.wcm.base'}"/>
   ```

   **customheaderlibs.html** is een HTML-script dat wordt gerenderd aan de kop van de pagina. Het is een gemeenschappelijk manuscript om project specifieke logica met voeten te treden en toe te voegen. In dit geval gebruiken wij het om de cliëntbibliotheek met een categorie van `acme.wcm.base`te omvatten. Volgens de best practices voor webontwikkeling nemen we de CSS alleen in de koptekst van de pagina op.

   ```html
   <!--/* customfooterlibs.html */-->
   <sly data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html">
       <sly data-sly-call="${clientlib.js @ categories='acme.wcm.base'}"/>
   </sly>
   ```

   **customfooterlibs.html** is een HTML- manuscript dat bij de bodem van de pagina, vlak vóór de sluitende `</body>` markering zal worden teruggegeven. De categorie van `acme.wcm.base` wordt opnieuw gebruikt, maar dit keer wordt alleen het JavaScript van de clientbibliotheek geladen.

Als u de HTML-scripts van de **paginacomponent** wijzigt, bepaalt u hoe deze op alle pagina&#39;s `acme.wcm.base` worden opgenomen. Maar hoe zit het met `acme.theme`? In de volgende oefening zullen wij een andere optie bekijken om cliëntbibliotheken op te nemen.

### Opname van clientbibliotheek met paginasjablonen {#client-library-inclusion-pagetemplates}

Er zijn verschillende opties voor het opnemen van een bibliotheek aan de clientzijde. Vervolgens wordt gecontroleerd hoe het gegenereerde project de bibliotheken aan de clientzijde van het thema bevat via [paginasjablonen](https://docs.adobe.com/content/help/en/experience-manager-65/developing/platform/templates/page-templates-editable.html).

Open een nieuwe browser en login aan de AEM instantie waarin u het project aan het begin van dit leerprogramma opstelde.

1. Navigeer in het scherm AEM Start naar **Gereedschappen** > **Algemeen** > **Sjablonen**.

   ![Sjabloonnavigatie](/help/commerce-cloud/assets/style-cif-component/template-location.png)

1. Navigeer naar de map **Acme Store Configuration** . Open het Sjabloon **voor** categoriepagina door het *potloodpictogram* te selecteren.

   ![categoriepagina-sjabloonkaart](/help/commerce-cloud/assets/style-cif-component/category-page-template.png)

1. Selecteer in de linkerbovenhoek het pictogram **Pagina-informatie** en klik op **Paginabeleid**.

   ![Menu-item voor paginabeleid](/help/commerce-cloud/assets/style-cif-component/page-policy-menu.png)

1. Hiermee opent u het paginabeleid voor de sjabloon Cataloguspagina:

   ![Paginabeleid - cataloguspagina](/help/commerce-cloud/assets/style-cif-component/page-policy-properties.png)

   Rechts ziet u een lijst met **categorieën** Client Libraries die worden opgenomen op alle pagina&#39;s die deze sjabloon gebruiken.

   * **wcm.foundation.components.page.responsive** - Verstrekt CSS nodig om [ontvankelijke lay-outcontroles](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/siteandpage/responsive-layout.html) door auteurs toe te laten.
   * **acme.theme** - Dit is het uitgangspunt dat archetype automatisch produceert. Standaard wordt deze stijl gebruikt, zoals in de voorbeeldwinkel van Venia. Nochtans zoals u van de naam kunt zien, is het bedoeld om door de projectimplementatie worden aangepast. *Dat is wat wij in de volgende paragraaf zullen wijzigen!*
   * **core.cif.components.response** - Dit is een gecompileerde clientbibliotheek met verschillende React-componenten die worden gebruikt voor dynamische functies zoals het Shopping Cart. Meer [informatie vindt u hier](https://github.com/adobe/aem-core-cif-components/tree/master/react-components).

   Andere sjablonen gebruiken hetzelfde beleid, dezelfde **inhoudspagina**, dezelfde **bestemmingspagina**, enzovoort.. Door hetzelfde beleid opnieuw te gebruiken, kunnen we ervoor zorgen dat dezelfde clientbibliotheken op alle pagina&#39;s worden opgenomen.

   Het voordeel van het gebruiken van Malplaatjes en het beleid van de Pagina om de opneming van cliëntbibliotheken te beheren is dat u het beleid per malplaatje kunt veranderen. U beheert bijvoorbeeld twee verschillende merken binnen dezelfde AEM. Elk merk heeft zijn eigen unieke stijl of *thema* , maar de basisbibliotheken en -code zijn hetzelfde. Een ander voorbeeld: als u een grotere clientbibliotheek had die u alleen op bepaalde pagina&#39;s wilde weergeven, kon u een uniek paginabeleid maken, alleen voor die sjabloon. Het andere voordeel

### Clientbibliotheken op de pagina controleren {#verify-client-libraries}

Op dit punt hebben wij herzien hoe te om cliëntbibliotheken te omvatten gebruikend HTML met de **douanheaderlibs.html** en **customfooterlibs.html** manuscripten en hoe het de paginabeleid van een Malplaatje kan worden gebruikt om extra cliëntbibliotheken te omvatten. Vervolgens wordt gecontroleerd of de clientbibliotheken op de site zijn opgenomen.

1. Navigeer in het scherm AEM Start naar **Sites** > **Acme Store** > **Verenigde Staten** > **Engels** en open de pagina voor bewerking: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html).

1. Selecteer het menu **Pagina-informatie** en klik op **Weergeven als gepubliceerd**:

   ![Weergeven als gepubliceerd](/help/commerce-cloud/assets/style-cif-component/view-as-published.png)

   Hierdoor wordt de pagina geopend zonder dat de AEM auteur javascript is geladen, zoals deze op de gepubliceerde site wordt weergegeven. Bericht dat url de vraagparameter heeft `?wcmmode=disabled` toegevoegd. Bij het ontwikkelen van CSS en Javascript is het een goede praktijk om deze parameter te gebruiken om de pagina met om het even wat van AEM auteur te vereenvoudigen.

1. Bekijk de paginabron en u zou de volgende cliëntbibliotheken moeten kunnen identificeren zijn inbegrepen: **acme.wcm.base**, **wcm.foundation.components.page.responsive**, **acme.theme**, **core.cif.components.response**

   ```html
   <!DOCTYPE html>
   <html lang="en-US">
   <head>
       ...
       <link rel="stylesheet" href="/etc.clientlibs/acme/clientlibs/clientlib-base.css" type="text/css">
       <link rel="stylesheet" href="/libs/wcm/foundation/components/page/responsive.css" type="text/css">
       <link rel="stylesheet" href="/etc.clientlibs/acme/clientlibs/theme.css" type="text/css">
   </head>
   ...
   
       <script type="text/javascript" src="/etc.clientlibs/core/cif/clientlibs/react-components.js"></script>
       <script type="text/javascript" src="/etc.clientlibs/acme/clientlibs/clientlib-base.js"></script>
   </body>
   </html>
   ```

## De producttaser opmaken {#style-product-teaser}

Nu wij de structuur van de cliëntbibliotheek begrijpen die door archetype wordt geproduceerd, kunnen wij beginnen om de AEM componenten van de Kern aan te passen CIF. Wij zullen de stijlen van de component van de Teaser van het Product wijzigen zodat het meer als een &quot;kaart&quot;kijkt.

### Auteur van de producttaser {#author-product-teaser}

Als eerste stap, zullen wij een nieuw geval van de component van de Teaser van het Product aan de homepage van onze plaats gebruikend de AEM auteurshulpmiddelen toevoegen.

1. Open een nieuw browsertabblad en navigeer naar de **startpagina** van de site: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html).

1. Voeg een nieuwe **Product Teaser** Component in de hoofdlay-outcontainer op de pagina in.

   ![Productteam invoegen](/help/commerce-cloud/assets/style-cif-component/product-teaser-add-component.png)

1. Vouw het zijpaneel uit (als dit nog niet het geval is) en schakel het vervolgkeuzemenu voor het zoeken naar **producten** in. Dit zou een lijst van beschikbare producten van een verbonden instantie van de Magento moeten tonen. Selecteer een product en **sleep** het naar de **productlasercomponent** op de pagina.

   ![Slepen en productteam neerzetten](/help/commerce-cloud/assets/style-cif-component/drag-drop-product-teaser.png)

   > Nota, kunt u het getoonde product ook vormen door de component te vormen gebruikend de dialoog (klikkend het *moersleutelpictogram* ).

1. Er wordt nu een product weergegeven door de Product Teaser. De naam van het product en de prijs van het product zijn standaardkenmerken die worden weergegeven.

   ![Productteam - standaardstijl](/help/commerce-cloud/assets/style-cif-component/product-teaser-default-style.png)

### CSS bijwerken voor de producttaser {#update-css-product-teaser}

Vervolgens wijzigt u de CSS in de **themaclient** om een op een kaart lijkende stijl te implementeren voor de Product Teaser.

Terugkeer aan winde en het geproduceerde project.

1. Navigeer in de module **ui.apps** naar de map: `ui.apps/src/main/content/jcr_root/apps/acme/clientlibs/theme/components/productteaser`. Hier worden alle stijlen voor de producttaser gedefinieerd.

1. Open het bestand **teaser.css** en werk de bijbehorende CSS-regels bij (of download het bestand [teaser.css en vervang de](/help/commerce-cloud/assets/style-cif-component/solution-teaser.css) oplossing).

   Voeg een slagschaduw toe en neem afgeronde hoeken op in de producttaser.

   ```css
    .productteaser .item__root {
        position: relative;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
        border-radius: 5px;
        float: left;
        margin-left: 12px;
        margin-right: 12px;
   }
   
   .productteaser .item__root:hover {
      box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
   }
   ```

   Wijzig de rand voor de afbeelding in de producttaser.

   ```css
   .productteaser .item__image {
       border-bottom: 1px solid #c0c0c0;
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

   Werk de naam van het product bij zodat deze onder aan het gummetje wordt weergegeven en wijzig de tekstkleur.

   ```css
   .productteaser .item__name {
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

   Werk de prijs van het product bij zodat deze ook onder aan het gummetje wordt weergegeven en wijzig de tekstkleur.

   ```css
   .productteaser .item__price {
       color: #000;
       display: block;
       float: left;
       font-size: 18px;
       font-weight: 900;
       padding: 0.75em;
       padding-bottom: 2em;
       width: 25%;
   }
   ```

   Werk de mediaquery onderaan bij om de naam en de prijs te stapelen in schermen die kleiner zijn dan 992 px.

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

   Sla de wijzigingen in **teaser.css** op. U kunt het bestand [Solution teaser.css hier](/help/commerce-cloud/assets/style-cif-component/solution-teaser.css)downloaden.

1. Implementeer de updates van de module **ui.apps** om AEM gebruik te maken van uw Maven-vaardigheden, via een opdrachtregelterminal:

   ```shell
           $ cd acme-store/ui.apps/
           $ mvn -PautoInstallPackage clean install
           ...
           saving approx 0 nodes...
           Package imported.
           Package installed in 61ms.
           [INFO] ------------------------------------------------------------------------
           [INFO] BUILD SUCCESS
           [INFO] ------------------------------------------------------------------------
           [INFO] Total time:  6.903 s
           [INFO] Finished at: 2020-02-06T13:21:36-08:00
            [INFO] ------------------------------------------------------------------------
   ```

   >[!NOTE]
   >Er zijn extra Opstelling [van winde en Hulpmiddelen](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) die projectdossiers aan een lokale AEM instantie rechtstreeks kunnen synchroniseren zonder het moeten een volledige Gemaakt bouwstijl uitvoeren.

### Bijgewerkte producttaser weergeven {#view-updated-product-teaser}

Nadat de code voor het project aan AEM is opgesteld, zouden wij nu de veranderingen in de Teaser van het Product moeten kunnen zien.

1. Ga terug naar uw browser en vernieuw de startpagina: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html). De bijgewerkte stijlen voor productgummeters moeten worden toegepast.

   ![Bijgewerkte stijl van de Teaser van het Product](/help/commerce-cloud/assets/style-cif-component/product-teaser-new-style.png)

1. Experimenteer door extra Product teasers toe te voegen. Gebruik de modus Lay-out om de breedte en verschuiving van de componenten te wijzigen en meerdere trappen in een rij weer te geven.

   ![Meerdere productteams](/help/commerce-cloud/assets/style-cif-component/multiple-teasers-final.png)

   >[!NOTE]
   >Elk productgummetje bevat dezelfde stijl.

### Problemen oplossen {#troubleshooting}

U kunt in [CRXDE-Lite](http://localhost:4502/crx/de/index.jsp) verifiëren dat het bijgewerkte CSS dossier is opgesteld: [http://localhost:4502/crx/de/index.jsp#/apps/acme/clientlibs/theme/components/productteaser/teaser.css](http://localhost:4502/crx/de/index.jsp#/apps/acme/clientlibs/theme/components/productteaser/teaser.css)

Bij het implementeren van nieuwe CSS- en/of JavaScript-bestanden is het ook belangrijk ervoor te zorgen dat de browser geen schaalbestanden aanbiedt. U kunt dit voorkomen door de browsercache te wissen of een nieuwe browsersessie te starten.

AEM probeert ook clientbibliotheken in cache te plaatsen voor prestaties. Af en toe, na een codeplaatsing worden de oudere dossiers gediend. U kunt AEM cache van de clientbibliotheek handmatig ongeldig maken met het gereedschap [Clientbibliotheken](http://localhost:4502/libs/granite/ui/content/dumplibs.rebuild.html)opnieuw samenstellen. *Schakel de voorkeursmethode Caches ongeldig maken in als u vermoedt dat AEM een oude versie van een clientbibliotheek in het cachegeheugen heeft opgeslagen. Het opnieuw samenstellen van bibliotheken is inefficiënt en tijdrovend.*

### Gefeliciteerd {#congratulations}

U hebt zojuist uw eerste AEM CIF Core Component vormgegeven!

### Bonus Challenge {#bonus-challenge}

Gebruik het systeem [](https://docs.adobe.com/content/help/en/experience-manager-65/developing/components/style-system.html) AEM stijl om twee stijlen te maken die door de auteur van de inhoud in- en kunnen worden in- en uitgeschakeld. [Het ontwikkelen met het Systeem](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html) van de Stijl omvat gedetailleerde stappen en informatie over hoe te om dit te verwezenlijken.

![Bonus Challenge - Stijl Systeem](/help/commerce-cloud/assets/style-cif-component/bonus-challenge.png)

## Aanvullende bronnen {#additional-resources}

* [AEM CIF Archetype](https://github.com/adobe/aem-cif-project-archetype)

* [AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components)

* [Een lokale AEM ontwikkelomgeving instellen](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html)

* [Client-Side bibliotheken](https://docs.adobe.com/content/help/en/experience-manager-65/developing/introduction/clientlibs.html)
* [Aan de slag met AEM Sites](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

* [Ontwikkelen met het Stijlsysteem](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/style-system.html)
