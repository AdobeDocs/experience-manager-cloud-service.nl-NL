---
title: CIF Core-componenten aanpassen
description: CIF Core-componenten aanpassen
translation-type: tm+mt
source-git-commit: dd6973085ae34dd6ea7296c36d0a14f699440269
workflow-type: tm+mt
source-wordcount: '2520'
ht-degree: 0%

---


# AEM CIF Core-componenten aanpassen {#customize-cif-components}

[AEM de Componenten](https://github.com/adobe/aem-core-cif-components) van de Kern van CIF verstrekt een standaardreeks componenten van de Handel die kunnen worden gebruikt om een project te versnellen dat Adobe Experience Manager (AEM) en Magento oplossingen integreert. Deze componenten zijn klaar voor productie en kunnen [gemakkelijk met CSS](style-cif-component.md)worden gestileerd. Vele implementaties zullen deze componenten ook willen uitbreiden om aan bedrijfsspecifieke vereisten te voldoen.

In deze zelfstudie bespreken we verschillende extensiepunten die door AEM CIF Core Components en AEM in het algemeen worden geboden. We doen dit door de mogelijkheden van de [Product Teaser](https://github.com/adobe/aem-core-cif-components/tree/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser) -component uit te breiden met de mogelijkheid om een &quot;Nieuwe&quot; banner te renderen. Inhoudsauteurs kunnen deze banner in- en uitschakelen en bepalen hoe lang de banner moet worden weergegeven. De &quot;leeftijd&quot; van het product wordt gebaseerd op de aanmaakdatum ervan in de catalogus Magento. Zodra een product een bepaalde hoeveelheid dagen oud is, zou de &quot;Nieuwe&quot;banner automatisch moeten verdwijnen.

![Nieuwe banner uitgebreid](/help/commerce-cloud/assets/customize-cif-components/new-banner-productteaser.png)

## Vereisten {#prerequisites}

De volgende gereedschappen en technologieën zijn vereist:

* [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html)
* [Apache Maven](https://maven.apache.org/) (3.3.9 of hoger)
* [Cloud-SKD AEM met CIF-invoegtoepassing](../develop.md)
* Magento compatibel met CIF Core-componenten

U wordt aangeraden de volgende inhoud te bekijken voordat u verdergaat met deze zelfstudie:

* [Invoering van een kader voor de integratie van de handel in AEM als Cloud Service](/help/commerce-cloud/overview.md)
* [Stijl AEM CIF Core-componenten - Zelfstudie](style-cif-component.md)

## Starter-project

We hebben een startproject beschikbaar gesteld voor deze zelfstudie. Het project werd geproduceerd gebruikend [v0.7.0](https://github.com/adobe/aem-cif-project-archetype/releases/tag/cif-project-archetype-0.7.0) van het Project van CIF Archetype. Het wordt beschouwd als beste praktijken om de [recentste versie](https://github.com/adobe/aem-cif-project-archetype/releases/latest) van archetype altijd te gebruiken wanneer het beginnen van een nieuw project.

1. Download het startproject [**acme-store.zip **](/help/commerce-cloud/assets/customize-cif-components/acme-store.zip)naar uw bureaublad.

1. Unzip **acme-store.zip** en de volgende mapstructuur moet worden weergegeven:

   ```plain
   /acme-store
      /ui.content
      /ui.apps
      /samplecontent
      /core
      /all
      + pom.xml
      + README.md
   ```

1. Open een nieuw eindvenster en bouw en stel het project aan een lokaal geval van AEM op;

   ```shell
   $ cd acme-store/
   $ mvn clean install -PautoInstallAll
   ```

1. Voeg de noodzakelijke configuraties OSGi toe om uw AEM instantie met een instantie van de Magento te verbinden of de configuraties aan het onlangs gecreeerd project toe te voegen.

1. Op dit punt zou u een werkende versie van een storefront moeten hebben die met een instantie van Magento wordt verbonden. Navigeer naar de pagina `US` > `Home` op: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

   Je moet zien dat de winkel het thema Venia gebruikt. Als u het hoofdmenu van de storefront uitbreidt, ziet u verschillende categorieën die aangeven dat de Magento van de verbinding werkt.

   ![Storefront geconfigureerd met het Venia-thema](/help/commerce-cloud/assets/customize-cif-components/acme-store-configured.png)

## Auteur van de producttaser {#author-product-teaser}

Tijdens deze zelfstudie zullen we de Product Teaser Component uitbreiden. Als eerste stap, zullen wij een nieuw geval van de Teaser van het Product aan de Homepage toevoegen om de basislijnfunctionaliteit te begrijpen.

1. Ga naar de **startpagina** van de site: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

1. Voeg een nieuwe **Product Teaser** Component in de hoofdlay-outcontainer op de pagina in.

   ![Productteam invoegen](/help/commerce-cloud/assets/customize-cif-components/product-teaser-add-component.png)

1. Vouw het zijpaneel uit (als dit nog niet het geval is) en schakel het vervolgkeuzemenu voor het zoeken naar **producten** in. Dit zou een lijst van beschikbare producten van een verbonden instantie van de Magento moeten tonen. Selecteer een product en **sleep** het naar de **productlasercomponent** op de pagina.

   ![Slepen en productteam neerzetten](/help/commerce-cloud/assets/customize-cif-components/drag-drop-product-teaser.png)

   > Nota, kunt u het getoonde product ook vormen door de component te vormen gebruikend de dialoog (klikkend het *moersleutelpictogram* ).

1. Er wordt nu een product weergegeven door de Product Teaser. De naam van het product en de prijs van het product zijn standaardkenmerken die worden weergegeven.

   ![Productteam - standaardstijl](/help/commerce-cloud/assets/customize-cif-components/product-teaser-default-style.png)

## De opmaak van de producttaser aanpassen {#customize-markup-product-teaser}

Een algemene uitbreiding van AEM componenten is het wijzigen van de markering die door de component wordt gegenereerd. Dit wordt gedaan door het manuscript [met voeten te treden](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html) HTML dat de component gebruikt om zijn prijsverhoging terug te geven. HTML Template Language (HTL) is een lichte sjabloontaal die AEM componenten gebruiken om markeringen dynamisch te renderen op basis van geschreven inhoud, zodat de componenten opnieuw kunnen worden gebruikt. De producttaser kan bijvoorbeeld steeds opnieuw worden gebruikt om verschillende producten weer te geven.

In ons geval willen we een banner boven op het gummetje weergeven om aan te geven dat het product &quot;Nieuw&quot; is en onlangs aan de catalogus is toegevoegd. Het ontwerppatroon voor het [aanpassen van de opmaak](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html#customizing-the-markup) van een component is in feite standaard voor alle AEM Componenten, niet alleen voor de AEM CIF Core-componenten.

Gebruik winde van uw keus om het starter project te [openen dat aan het begin van het leerprogramma wordt gedownload](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment) .

1. Navigeer en vouw de module **ui.apps** uit en vouw de omslaghiërarchie uit aan: `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser` en inspecteer het `.content.xml` bestand.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:description="Product Teaser Component"
       jcr:primaryType="cq:Component"
       jcr:title="Product Teaser"
       sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"
       componentGroup="acme"/>
   ```

   Hierboven vindt u de componentdefinitie voor de Product Teaser Component in ons project. Let op de eigenschap `sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"`. Dit is een voorbeeld van het maken van een [Proxy-component](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/using.html#create-proxy-components). In plaats van alle HTML-scripts van de Product Teaser te kopiëren en te plakken van de AEM CIF Core Components, kunnen we de code gebruiken `sling:resourceSuperType` om alle functionaliteit over te nemen.

1. Open een nieuwe browser en navigeer naar [CRXDE-Lite](http://localhost:4502/crx/de/index.jsp#/apps/core/cif/components/commerce/productteaser/v1/productteaser) in AEM. Breid de boom uit om de `productteaser` component onder te bekijken: `/apps/core/cif/components/commerce/productteaser/v1/productteaser`:

   ![CRXDE Lite Product Teaser](/help/commerce-cloud/assets/customize-cif-components/crxde-productteaser.png)

   Dit is de volledige componentendefinitie voor de component van de Teaser van het Product.

1. Ga terug naar uw IDE en het Acme Store-project. Maak een nieuw bestand met de naam `productteaser.html` eronder `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser`.

1. Kopieer de inhoud van `productteaser.html` van [CRXDE-Lite](http://localhost:4502/crx/de/index.jsp#/apps/core/cif/components/commerce/productteaser/v1/productteaser/productteaser.html) en kleef het in het Acme-Opslag project in het onlangs gecreeerd `productteaser.html` dossier.

   ![Producttaser html overschrijven](/help/commerce-cloud/assets/customize-cif-components/productteaser-html-overwrite.png)

1. In het Acme-Opslag project wijzig het `productteaser.html` dossier en neem een nieuw div op die een badge boven de prijsverhoging van het productbeeld vertegenwoordigt:

   ```html
   ...
   <div data-sly-test.isvalid="${product.url}" class="item__root" data-cmp-is="productteaser">
       <!-- Add Badge -->
       <div class="item__badge">
           <span>New</span>
       </div>
       <!-- end add badge -->
       <a class="item__images" href=${product.url}>
           <img class="item__image" width="100%" height="100%"
                   src="${product.image}" alt="${product.image}"/>
       </a>
       <a class="item__name" href=${product.url}><span>${product.name}</span></a>
       <div class="item__price">
           <span> ${product.formattedPrice} </span>
       </div>
       <sly data-sly-call="${actionsTpl.actions @ product=product}"></sly>
   </div>
   ```

1. Stel de bijgewerkte code aan de lokale instantie van AEM op gebruikend uw beproefde vaardigheden of gebruikend [de eigenschappen van uw winde](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html#set-up-an-integrated-development-environment):

   ```shell
   $ cd ui.apps
   $ mvn -PautoInstallPackage clean install
   ```

1. Ga in de browser terug naar de [startpagina van de winkel voor](http://localhost:4502/editor.html/content/acme/us/en.html) in AEM. Vernieuwen en u ziet dat er een &quot;nieuwe&quot; banner in de rechterbovenhoek van de component wordt weergegeven.

   ![Nieuwe banner uitgebreid](/help/commerce-cloud/assets/customize-cif-components/new-banner-productteaser.png)

   Er is momenteel geen logica achter wanneer de banner wordt weergegeven. In de volgende oefeningen zullen we dat corrigeren.

   > Opmerking: de CSS om de banner te renderen is opgegeven als onderdeel van het startproject en is te vinden op: `ui.apps/../apps/acme/clientlibs/theme/components/productteaser/teaser.css`. Voor meer details bekijk de [Stijlende zelfstudie](style-cif-component.md)van de Componenten van de Kern van CIF.

## Het dialoogvenster van de producttaser aanpassen {#customize-dialog-product-teaser}

Daarna, zullen wij de dialoog van de component van de Teaser van het Product aanpassen om een Auteur toe te staan om de datumwaaier te bepalen waarvoor een product &quot;nieuw&quot;wordt beschouwd en als de banner zou moeten worden getoond. Dit doen we door de dialoog [van de producttaser aan te](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html#customizing-dialogs) passen in het kader van het Acme Store-project.

1. Open het Acme Store-project in IDE van uw keuze en navigeer naar `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser`.

1. Voeg onder de `productteaser` map een nieuwe map met de naam `_cq_dialog`. Voeg een nieuw bestand toe aan de `_cq_dialog` map met de naam `.content.xml`. U hebt nu de volgende bestandsstructuur:

   ```plain
   ../acme
       /components
           /commerce
               /productteaser
                  /_cq_dialog
                     + .content.xml
                  /_cq_template
                  + .content.xml
                  + productteaser.html
   ```

1. Bijwerken `_cq_dialog/.content.xml` met de volgende XML:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" 
       xmlns:cq="http://www.day.com/jcr/cq/1.0" 
       xmlns:jcr="http://www.jcp.org/jcr/1.0" 
       xmlns:nt="http://www.jcp.org/jcr/nt/1.0" 
       jcr:primaryType="nt:unstructured" 
       jcr:title="My Product Teaser" 
       sling:resourceType="cq/gui/components/authoring/dialog" 
       trackingFeature="cif-core-components:productteaser:v1">
       <content jcr:primaryType="nt:unstructured" 
           sling:resourceType="granite/ui/components/coral/foundation/container">
           <items jcr:primaryType="nt:unstructured">
               <tabs jcr:primaryType="nt:unstructured" 
                   sling:resourceType="granite/ui/components/coral/foundation/tabs" 
                   maximized="{Boolean}true">
                   <items jcr:primaryType="nt:unstructured">
                       <badge jcr:primaryType="nt:unstructured" 
                           jcr:title="Badge" 
                           sling:resourceType="granite/ui/components/coral/foundation/container" 
                           margin="{Boolean}true">
                           <items jcr:primaryType="nt:unstructured">
                               <columns jcr:primaryType="nt:unstructured" 
                                   sling:resourceType="granite/ui/components/coral/foundation/fixedcolumns" 
                                   margin="{Boolean}true">
                                   <items jcr:primaryType="nt:unstructured">
                                       <column jcr:primaryType="nt:unstructured" 
                                           sling:resourceType="granite/ui/components/coral/foundation/container">
                                           <items jcr:primaryType="nt:unstructured">
                                               <badge jcr:primaryType="nt:unstructured" 
                                                   sling:resourceType="granite/ui/components/coral/foundation/form/checkbox" 
                                                   text="Display 'New' badge" 
                                                   value="true" 
                                                   uncheckedValue="false" 
                                                   name="./badge" />
                                               <age jcr:primaryType="nt:unstructured" 
                                                   sling:resourceType="granite/ui/components/coral/foundation/form/numberfield" 
                                                   fieldDescription="The maximum age in days the 'new' badge should be shown" 
                                                   fieldLabel="Max Product Age" 
                                                   name="./age"
                                                   min="{Long}0" 
                                                   value="10" />
                                               <ageTypeHint jcr:primaryType="nt:unstructured" 
                                                   sling:resourceType="granite/ui/components/foundation/form/hidden" 
                                                   ignoreData="{Boolean}true" 
                                                   name="./age@TypeHint" 
                                                   value="Long" />
                                           </items>
                                       </column>
                                   </items>
                               </columns>
                           </items>
                       </badge>
                   </items>
               </tabs>
           </items>
       </content>
   </jcr:root>
   ```

   Hierboven zijn twee extra velden toegevoegd als onderdeel van een nieuw tabblad en één verborgen veld.

   1. Selectievakje voor nieuwe badge weergeven
   2. Het gebied van het aantal om de Maximale Leeftijd van het Product te bepalen
   3. Verborgen veld om ervoor te zorgen dat de maximale productleeftijd als lang wordt opgeslagen (zie [@TypeHint](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) voor meer informatie)

   Dialoogvensters die als onderdeel van een proxycomponent worden gedefinieerd, overerven alle bestaande dialoogvelden met een functie die bekend staat als [Sling Resource Merger](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/sling-resource-merger.html). Daarom moeten we de bestaande velden die deel uitmaken van de producttaser niet opnieuw definiëren.

1. Werk de badge bij `productteaser.html` en voeg er een `data-sly-test` aan toe `<div>` . Dit wordt een eenvoudige test om te beslissen of de badge moet worden weergegeven als de gebruiker &quot;true&quot; heeft ingeschakeld.

   ```html
       ...
       <div data-sly-test.isvalid="${product.url}" class="item__root" data-cmp-is="productteaser">
   
           <!--/* add test to see if properties.badge equals true */-->
           <div data-sly-test="${properties.badge == 'true'}" class="item__badge">
               <span>New</span>
           </div>
   ...
   ```

1. Stel de bijgewerkte code aan de lokale instantie van AEM op gebruikend eigenschappen van uw winde of door uw beven vaardigheden te gebruiken:

   ```shell
   $ cd ui.apps
   $ mvn -PautoInstallPackage clean install
   ```

1. Keer terug naar de component van de Teaser van het Product en klik het *moersleutelpictogram* om de Dialoog te openen. Er wordt nu een tabblad voor de **Badge** weergegeven met twee extra velden. Als u deze velden bijwerkt, blijven de waarden die u wilt AEM behouden. U moet de badge in- of uitschakelen met het selectievakje:

   ![Badge schakelen](/help/commerce-cloud/assets/customize-cif-components/toggle-badge-checkbox.gif)

   Dit geeft de auteur wat controle over wanneer de badge verschijnt. Het zou echter ideaal zijn om de badge automatisch te laten verdwijnen zodra het product een bepaalde leeftijd in de dag heeft bereikt, op basis van de vermelding voor **Max Productleeftijd**. Hiervoor moeten we een aantal achterwaartse logica invoeren.

## Het verkoopmodel voor de producttaser bijwerken {#updating-sling-model-product-teaser}

Daarna, zullen wij de bedrijfslogica van de Teaser van het Product uitbreiden door een het Verkopen Model uit te voeren. [Sling Models](https://sling.apache.org/documentation/bundles/models.html), zijn annotation-gedreven &quot;POJOs&quot; (Vaste Oude Voorwerpen van Java) die om het even welke bedrijfslogica uitvoeren nodig door de component. Sling Models worden gebruikt in combinatie met de HTML-scripts als onderdeel van de component. We zullen het [delegatiepatroon voor Sling Models](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) volgen, zodat we alleen maar onderdelen van het bestaande productassortiment kunnen uitbreiden.

Sling Models worden uitgevoerd als Java en kunnen in de **kernmodule** van het geproduceerde project worden gevonden.

1. Open het Acme Store-project in IDE van uw keuze en navigeer onder de **kernmodule** naar: `core/src/main/java/com/acme/cif/core/models/MyProductTeaser.java`. **MyProductTeaser.java** is een Java-interface die we vooraf hebben gemaakt en die de interface CIF **ProductTeaser** uitbreidt.

1. Open vervolgens het bestand **MyProductTeaserImpl.java** in: `core/src/main/java/com/acme/cif/core/models/MyProductTeaserImpl.java`. `MyProductTeaserImpl` is de implementatieklasse voor de interface `MyProductTeaser`.

   Met behulp van het [delegatiepatroon voor Sling Models](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) kunnen we naar de `ProductTeaser` klasse verwijzen via de `sling:resourceSuperType` eigenschap:

   ```java
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductTeaser productTeaser;
   ```

   Voor alle methodes die wij niet willen met voeten treden of veranderen, kunnen wij eenvoudig de waarde terugkeren die het `ProductTeaser` terugkeert:

   ```java
   @Override
   public String getImage() {
       return productTeaser.getImage();
   }
   ```

1. Een van de extra extensiepunten die door AEM CIF Core Components wordt geboden, is de extensie `AbstractProductRetriever` waarmee we toegang krijgen tot specifieke productkenmerken. Voeg de volgende methode toe om het `AbstractProductRetriever` in de `init()` methode te initialiseren:

   ```java
   import javax.annotation.PostConstruct;
   ...
   @Model(adaptables = SlingHttpServletRequest.class, adapters = MyProductTeaser.class, resourceType = MyProductTeaserImpl.RESOURCE_TYPE)
   public class MyProductTeaserImpl implements MyProductTeaser {
       ...
       private AbstractProductRetriever productRetriever;
   
       /* add this method to intialize the proudctRetriever */
       @PostConstruct
       public void initModel() {
           productRetriever = productTeaser.getProductRetriever();
   
       }
   ...
   ```

1. Hiermee kunt u deze wijzigingen uittesten door de opgemaakte prijs te wijzigen en de logica in te overschrijven `getFormattedPrice()`. Voer de volgende updates uit, zodat we de prijs expliciet opmaken op basis van de landinstelling in Duitsland. (of kies een ander land!)

   ```java
           import java.util.Locale;
           import java.text.NumberFormat;
            ...
   
               @Override
                   public String getFormattedPrice() 
                   {
                   //return productTeaser.getFormattedPrice();
                   NumberFormat germanCurrencyFormat = NumberFormat.getCurrencyInstance(Locale.GERMANY);
                   Double price =  productRetriever.fetchProduct().getPrice().getRegularPrice().getAmount().getValue();
                       if(price != null) 
                       {
                           return germanCurrencyFormat.format(price);
                       }
                   return null;
                   }
   ```

   Let op hoe het `productRetriever` object ons via de `ProductInterface` methode toegang geeft tot het `fetchProduct()` object. U kunt hier [alle](https://github.com/adobe/commerce-cif-magento-graphql/blob/master/src/main/java/com/adobe/cq/commerce/magento/graphql/ProductInterface.java)beschikbare methoden zien.

   > Opmerking* Het aanpassen van de landinstelling aan het Duits is slechts een leuk voorbeeld om de overschrijving te zien. In werkelijkheid gebruikt ProductTeaser de landinstelling van de [pagina om de indeling](https://github.com/adobe/aem-core-cif-components/blob/master/bundles/core/src/main/java/com/adobe/cq/commerce/core/components/internal/models/v1/productteaser/ProductTeaserImpl.java#L173)te bepalen.

1. Vervolgens moeten we het bestand **productteaser.html** in de module **ui.apps** bijwerken en verwijzen naar ons nieuwe verkoopmodel op: `com.acme.cif.core.models.MyProductTeaser`.

   ```diff
     <!--/* productteaser.html - change the use.product to point to MyProductTeaser */-->
     <sly data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html"
   -  data-sly-use.product="com.adobe.cq.commerce.core.components.models.productteaser.ProductTeaser"
   +  data-sly-use.product="com.acme.cif.core.models.MyProductTeaser"
      data-sly-use.actionsTpl="actions.html">
       ...
   ```

   Sla de wijzigingen op in `productteaser.html`.

1. Stel de codebasis aan de lokale instantie van AEM op. Aangezien er wijzigingen zijn aangebracht in zowel de **ui.apps** als de **kernmodules** , kunt u het project vanaf de hoofdmap bouwen en implementeren:

   ```shell
   $ cd acme-store
   $ mvn -PautoInstallPackage clean install
   ```

1. Open een browser en navigeer naar: [http://localhost:4502/system/console/status-slingmodels](http://localhost:4502/system/console/status-slingmodels). Deze console toont alle die Modellen van de Verkoop in het systeem worden geregistreerd. Dubbelcontrole om ervoor te zorgen dat MyTeaserModelImpl werd opgesteld en correct in kaart gebracht. Je zou iets moeten kunnen zien als:

   ```plain
   com.acme.cif.core.models.MyProductTeaserImpl - acme/components/commerce/productteaser
   ```

1. Navigeer ten slotte naar de plaats waar u de Product Teaser-component hebt gemaakt en de prijs wordt nu weergegeven met de notatie voor de Duitse valuta:

   ![Prijsindeling bijgewerkt](/help/commerce-cloud/assets/customize-cif-components/german-currency-update.png)

## De logica isShowBadge implementeren {#implement-isshowbadge}

Nu we de kans hebben gehad om te experimenteren met het overschrijven van de Sling Model-methoden, kunnen we de logica implementeren voor wanneer we de &#39;nieuwe&#39; badge moeten weergeven.

1. Ga terug naar uw IDE en open het bestand **MyProductTeaser.java** op: `core/src/main/java/com/acme/cif/core/models/MyProductTeaser.java`.

1. Voeg een nieuwe methode, `isShowBadge()` aan de interface toe:

   ```java
   @ProviderType
   public interface MyProductTeaser extends ProductTeaser {
       // Extend the existing interface with the additional properties which you
       // want to expose to the HTL template.
       public Boolean isShowBadge();
   }
   ```

   Dit is een nieuwe methode die we zullen introduceren om de logica van het al dan niet tonen van de badge in te kapselen.

1. Vervolgens opent u **MyProductTeaserImpl.java** opnieuw op `core/src/main/java/com/acme/cif/core/models/MyProductTeaserImpl.java`.

1. De logica voor hoe lang de &quot;nieuwe&quot;badge zal worden getoond zal op de `created_at` attributen van het Product gebaseerd zijn. Om toegang tot dat attribuut te hebben, moeten wij de vraag uitbreiden **GraphQL** die door ProductTeaser wordt uitgevoerd. We kunnen dit doen door de `init()` methode in **MyProductTeaserImpl.java** bij te werken:

   ```java
   //MyProductTeaserImpl.java
   
   @PostConstruct
   public void initModel() {
       productRetriever = productTeaser.getProductRetriever();
   
       if (productRetriever != null) {
           // Pass your custom partial query to the ProductRetriever. This class will
           // automatically take care of executing your query as soon
           // as you try to access any product property.
           productRetriever.extendProductQueryWith(p ->
               p.addCustomSimpleField("created_at")
           );
       }
   }
   ```

   Toevoegen aan de `extendProductQueryWith` methode is een krachtige manier om ervoor te zorgen dat aanvullende productkenmerken beschikbaar zijn voor de rest van het model. Het minimaliseert ook het aantal uitgevoerde vragen.

   >[!NOTE]
   >In de bovenstaande code gebruiken we het`addCustomSimpleField` om de `created_at` eigenschap op te halen. Dit illustreert hoe u voor om het even welke douanekenmerken kunt vragen die deel van het schema van de Magento uitmaken.
   >
   > De `created_at` eigenschap is echter daadwerkelijk geïmplementeerd als onderdeel van de [productinterface](https://github.com/adobe/commerce-cif-magento-graphql/blob/master/src/main/java/com/adobe/cq/commerce/magento/graphql/ProductInterface.java) en een betere praktijk zou zijn om de methode opnieuw te gebruiken zoals: `productRetriever.extendProductQueryWith(p -> p.createdAt());`. De meeste algemeen gevonden schemakenmerken zijn uitgevoerd, zodat gebruik slechts `addCustomSimpleField` voor echt douanekenmerken.

1. Vervolgens zullen we de `isShowBadge()` methode implementeren:

   ```java
   import java.time.format.DateTimeFormatter;
   import java.util.Locale;
   import java.time.temporal.ChronoUnit;
   
   ...
   
   @Override
   public Boolean isShowBadge() {
        final DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
   
        //Look at the checkbox from the dialog to see if we should even attempt to show the badge
        final boolean showBadge = properties.get("badge", false);
        if (showBadge) {
   
            //Look at the numberfield set from the dialog to determine the max "age" in days to compare too
            final int maxAgeProp = properties.get("age", 0);
   
           String createdAtString;
           try {
               //Grab the created_at property from the product
               //Here we show the example of retrieving the attribute as if it was a custom attribute
               // an alternative that would work is productRetriever.fetchProduct().getCreatedAt()
               createdAtString = productRetriever.fetchProduct().getAsString("created_at");
               log.info("***CREATED_AT**** " + createdAtString);
           } catch (SchemaViolationError e) {
               //it is possible that a schema error could be thrown if the attribute is not part of the schema
               log.error("Error determining to showBadge" , e);
               return false;
           }
   
            // Custom code to calc the date difference of the product creation
            // compared to today
           final LocalDate createdAt = LocalDate.parse(createdAtString, formatter);
            if (createdAt != null) {
   
                final long ageInDays = ChronoUnit.DAYS.between(createdAt, LocalDate.now());
                if (ageInDays < maxAgeProp) {
                    return true;
                }
            }
        }
        return false;
    }
   ```

   In de bovenstaande methode controleren we eerst of de auteur de badge-functionaliteit heeft ingeschakeld met het selectievakje. Vervolgens lezen we de waarde van de eigenschap `age` die is ingesteld als onderdeel van het dialoogvenster en die het maximumaantal dagen vertegenwoordigt dat een product moet hebben tot de banner verdwijnt. Tot slot berekenen we hoe oud het product is op de `created_at` datum. Als na het vergelijken van de twee waarden wij terugkeren `true` `false` om de badge, in alle andere gevallen te tonen.

1. Tot slot moet er nog een toevoeging aan het `productteaser.html` script worden aangebracht om de `isShowBadge()` methode aan te roepen. Open het bestand om `ui.apps/src/main/content/jcr_root/apps/acme/components/commerce/productteaser/productteaser.html`. Voer de volgende update uit:

   ```diff
   ...
   - <div data-sly-test="${properties.badge == 'true'}" class="item__badge">
   + <div data-sly-test="${product.showBadge}" class="item__badge">
        <span>New</span>
    </div>
   ...
   ```

1. Stel de codebasis aan de lokale instantie van AEM op. Aangezien er wijzigingen zijn aangebracht in zowel de **ui.apps** als de **kernmodules** , kunt u het project vanaf de hoofdmap bouwen en implementeren:

   ```shell
   $ cd acme-store
   $ mvn -PautoInstallPackage clean install
   ```

1. Ga terug naar AEM en de ProductTeaser component en experimenteer met verschillende getallen om de maximale leeftijd van het product weer te geven. Afhankelijk van hoe oud het product is, moet u mogelijk enkele zeer grote getallen invoeren om de badge te kunnen weergeven.

   ![Max. productleeftijd 999](/help/commerce-cloud/assets/customize-cif-components/max-age-working.png)

1. Tot slot onderzoek de AEM logboeken om de logboekverklaring te zien die in stap 5 hierboven wordt ingegaan. Hiermee wordt de waarde afgedrukt van de `created_at` eigenschap die afkomstig is van Magento. U kunt de logboeken van AEM bekijken door het `error.log` dossier te openen. Dit bestand bevindt zich onder de `crx-quickstart/logs/error.log` locatie waar de AEM is geïnstalleerd. U kunt een lijstitem als het volgende verwachten:

   ```plain
   com.acme.cif.core.models.MyProductTeaser ***CREATED_AT**** 2019-06-05 06:51:33
   ```

   Nu kunt u verifiëren dat de logica die wij hebben uitgevoerd correct is!

### Gefeliciteerd {#congratulations}

U hebt zojuist uw eerste AEM CIF-component aangepast! Download het [voltooide oplossingspakket hier](/help/commerce-cloud/assets/customize-cif-components/acme-store-solution.zip).

## Aanvullende bronnen {#additional-resources}

* [AEM Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)
* [AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components)
* [Aanpassen AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components/wiki/Customizing-CIF-Core-Components)
* [Kerncomponenten aanpassen](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html)
