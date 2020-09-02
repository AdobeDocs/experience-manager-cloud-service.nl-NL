---
title: CIF Core-componenten aanpassen
description: Leer hoe u AEM CIF Core-componenten aanpast. In de zelfstudie wordt uitgelegd hoe u een CIF Core-component veilig kunt uitbreiden om aan bedrijfsspecifieke vereisten te voldoen. Leer hoe te om een vraag uit te breiden GraphQL om een douanekenmerk terug te keren en de nieuwe attributen in een Component van de Kern te tonen CIF.
sub-product: handel
topics: development
version: cloud-service
doc-type: tutorial
activity: develop
audience: developer
kt: 4279
thumbnail: 4279-customize-cif.jpg
translation-type: tm+mt
source-git-commit: 34b4dc697d3fb8c3f81e16ee3cab5d768e42b99c
workflow-type: tm+mt
source-wordcount: '2550'
ht-degree: 0%

---


# AEM CIF Core-componenten aanpassen {#customize-cif-components}

Het [CIF Venia-project](https://github.com/adobe/aem-cif-guides-venia) is een referentiecode voor het gebruik van [CIF Core Components](https://github.com/adobe/aem-core-cif-components). In deze zelfstudie breidt u de [component Product Teaser](https://github.com/adobe/aem-core-cif-components/tree/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser) verder uit om een aangepast kenmerk van Magento weer te geven. U zult ook meer over de integratie GraphQL tussen AEM en Magento en de uitbreidingshaken leren die door de Componenten van de Kern CIF worden verstrekt.

>[!TIP]
>
> Gebruik [AEM archetype](https://github.com/adobe/aem-project-archetype) van het Project wanneer het beginnen van uw eigen handelsimplementatie.

## Wat u gaat maken

Het merk Venia is onlangs begonnen met het vervaardigen van bepaalde producten met behulp van duurzame materialen en het bedrijf wil graag een **milieuvriendelijk** merkteken weergeven als onderdeel van de Product Teaser. In Magento wordt een nieuw aangepast kenmerk gemaakt om aan te geven of een product het **milieuvriendelijke** materiaal gebruikt. Dit douanekenmerk zal dan als deel van de vraag GraphQL worden toegevoegd en op de Teaser van het Product voor gespecificeerde producten getoond.

![Eco-vriendelijke badge - definitieve implementatie](../assets/customize-cif-components/final-product-teaser-eco-badge.png)

## Vereisten {#prerequisites}

U hebt een lokale ontwikkelomgeving nodig om deze zelfstudie te voltooien. Dit omvat een lopende instantie van AEM die wordt gevormd en met een instantie van Magento verbonden. Herzie de vereisten en de stappen voor [vestiging een lokale ontwikkeling met AEM als Cloud Service SDK](../develop.md). Om de zelfstudie volledig te volgen, zult u toestemmingen nodig hebben om [Attributen aan een Product](https://docs.magento.com/user-guide/catalog/product-attributes-add.html) in Magento toe te voegen.

U zult ook winde GraphQL zoals [GraphiQL](https://github.com/graphql/graphiql) of een browser uitbreiding nodig hebben om de codesteekproeven en leerprogramma&#39;s in werking te stellen. Als u een browserextensie installeert, moet u ervoor zorgen dat deze de mogelijkheid heeft om aanvraagheaders in te stellen. Op Google Chrome is de [Altair GraphQL-client](https://chrome.google.com/webstore/detail/altair-graphql-client/flnheeellpciglgpaodhkhmapeljopja) één uitbreiding die de taak kan uitvoeren.

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

   ![Storefront geconfigureerd met Venia-thema](../assets/customize-cif-components/venia-store-configured.png)

## Auteur van de producttaser {#author-product-teaser}

De component Product Teaser wordt tijdens deze zelfstudie uitgebreid. Als eerste stap voegt u een nieuw exemplaar van de Product Teaser toe aan de startpagina om de basislijnfunctionaliteit te begrijpen.

1. Ga naar de **startpagina** van de site: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

2. Voeg een nieuwe **Product Teaser** Component in de hoofdlay-outcontainer op de pagina in.

   ![Productteam invoegen](../assets/customize-cif-components/product-teaser-add-component.png)

3. Vouw het zijpaneel uit (als dit nog niet het geval is) en schakel het vervolgkeuzemenu voor het zoeken naar **producten** in. Dit zou een lijst van beschikbare producten van een verbonden instantie van de Magento moeten tonen. Selecteer een product en **sleep** het naar de **productlasercomponent** op de pagina.

   ![Slepen en productteam neerzetten](../assets/customize-cif-components/drag-drop-product-teaser.png)

   >[!NOTE]
   >
   > Nota, kunt u het getoonde product ook vormen door de component te vormen gebruikend de dialoog (klikkend het *moersleutelpictogram* ).

4. Er wordt nu een product weergegeven door de Product Teaser. De naam van het product en de prijs van het product zijn standaardkenmerken die worden weergegeven.

   ![Productteam - standaardstijl](../assets/customize-cif-components/product-teaser-default-style.png)

## Een aangepast kenmerk toevoegen in Magento {#add-custom-attribute}

De in AEM weergegeven producten en productgegevens worden opgeslagen in Magento. Voeg vervolgens een nieuw kenmerk voor **Eco Friendly** toe als onderdeel van het productkenmerk dat is ingesteld met de Magento UI.

>[!TIP]
>
> Hebt u al een aangepast kenmerk **Ja/Nee** als onderdeel van de set productkenmerken? Voel u vrij om het te gebruiken en sla deze sectie over.

1. Meld u aan bij uw Magento-instantie.
1. Ga naar **Catalogus** > **Producten**.
1. Werk het onderzoeksfilter bij om het **Configurable Product** te vinden dat wanneer toegevoegd aan de component van het Teaser in de vorige oefening wordt gebruikt. Open het product in de bewerkingsmodus.

   ![Zoeken naar Valeria-product](../assets/customize-cif-components/search-valeria-product.png)

1. Klik in de productweergave op Kenmerk **** toevoegen > Nieuw kenmerk **** maken.
1. Vul het formulier **Nieuw kenmerk** in met de volgende waarden (standaardinstellingen voor andere waarden behouden)

   | Veldset | Veldlabel | Waarde |
   |-----------|-------------|---------|
   | Eigenschappen van kenmerk | Kenmerklabel | **Eco Friendly** |
   | Eigenschappen van kenmerk | Invoertype catalogus | **Ja/Nee** |
   | Geavanceerde kenmerkeigenschappen | Kenmerkcode | **ecovriendelijk** |

   ![Nieuw kenmerkformulier](../assets/customize-cif-components/attribute-new-form.png)

   Klik op Kenmerk **** opslaan als u klaar bent.

1. Blader naar de onderkant van het product en vouw de kop **Kenmerken** uit. Je moet het nieuwe **Eco Friendly** veld zien. Schakel de schakeloptie in op **Ja**.

   ![Overschakelen op ja](../assets/customize-cif-components/eco-friendly-toggle-yes.png)

   **Sla** de wijzigingen in het product op.

   >[!TIP]
   >
   > Meer informatie over het beheer van [productkenmerken vindt u in de gebruikershandleiding](https://docs.magento.com/user-guide/catalog/attribute-best-practices.html)Magento.

1. Ga naar **Systeem** > **Gereedschappen** > **Cachebeheer**. Aangezien een update aan het gegevensschema is gemaakt moeten wij sommige Types van Geheime voorgeheugen in Magento ongeldig maken.
1. Schakel het vakje naast **Configuratie** in en verzend het cachetype voor **Vernieuwen**

   ![Type configuratiecache vernieuwen](../assets/customize-cif-components/refresh-configuration-cache-type.png)

   >[!TIP]
   >
   > Meer informatie over [het Beheer van het Geheime voorgeheugen kan in de de gebruikersgids](https://docs.magento.com/user-guide/system/cache-management.html)van de Magento worden gevonden.

## Gebruik GrafiekQL winde om attribuut te verifiëren {#use-graphql-ide}

Alvorens in AEM code te springen is het nuttig om [Magento GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/) te onderzoeken gebruikend winde GraphQL. De integratie van Magento met AEM wordt hoofdzakelijk gedaan via een reeks vragen GraphQL. Het begrip van en het wijzigen van de vragen GraphQL is één van de belangrijkste manieren waarin de Componenten van de Kern CIF kunnen worden uitgebreid.

Daarna, gebruik IDE GraphQL om te verifiëren dat het `eco_friendly` attribuut aan de reeks van productattributen is toegevoegd. Schermafbeeldingen in deze zelfstudie gebruiken de [Altair GraphQL-client](https://chrome.google.com/webstore/detail/altair-graphql-client/flnheeellpciglgpaodhkhmapeljopja).

1. Open GrafiekQL winde en ga URL `http://<magento-server>/graphql` in de bar URL van uw winde of uitbreiding in.
2. Voeg de volgende [productvraag](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) toe waar `YOUR_SKU` is **SKU** van het product dat in de vorige oefening wordt gebruikt:

   ```json
     {
       products(
       filter: { sku: { eq: "YOUR_SKU" } }
       ) {
           items {
           name
           sku
           eco_friendly
           }
       }
   }
   ```

3. Voer de vraag uit en u zou een reactie als het volgende moeten krijgen:

   ```json
   {
   "data": {
       "products": {
           "items": [
               {
               "name": "Valeria Two-Layer Tank",
               "sku": "VT11",
               "eco_friendly": 1
               }
           ]
           }
       }
   }
   ```

   ![Sample GraphlQL-respons](../assets/customize-cif-components/sample-graphql-query.png)

   De waarde van **Ja** is een geheel getal van **1**. Dit zal nuttig zijn wanneer wij de vraag GraphQL in Java schrijven.

   >[!TIP]
   >
   > Meer gedetailleerde documentatie over [Magento GraphQL vindt u hier](https://devdocs.magento.com/guides/v2.4/graphql/index.html).

## Het verkoopmodel voor de producttaser bijwerken {#updating-sling-model-product-teaser}

Daarna, zullen wij de bedrijfslogica van de Teaser van het Product uitbreiden door een het Verkopen Model uit te voeren. [Sling Models](https://sling.apache.org/documentation/bundles/models.html), zijn annotation-gedreven &quot;POJOs&quot; (Vaste Oude Voorwerpen van Java) die om het even welke bedrijfslogica uitvoeren nodig door de component. Sling Models worden gebruikt in combinatie met de HTML-scripts als onderdeel van de component. We zullen het [delegatiepatroon voor Sling Models](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) volgen, zodat we alleen maar onderdelen van het bestaande productassortiment kunnen uitbreiden.

Sling Models worden uitgevoerd als Java en kunnen in de **kernmodule** van het geproduceerde project worden gevonden.

Gebruik [de IDE van uw keus](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#set-up-the-development-ide) om het project van Venia in te voeren. De gebruikte schermafbeeldingen zijn van winde van de Code van [Visual Studio](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#microsoft-visual-studio-code).

1. In uw winde, navigeer onder de **kernmodule** aan: `core/src/main/java/com/venia/core/models/commerce/MyProductTeaser.java`.

   ![Core location IDE](../assets/customize-cif-components/core-location-ide.png)

   `MyProductTeaser.java` is een interface van Java die de interface van CIF [ProductTeaser](https://github.com/adobe/aem-core-cif-components/blob/master/bundles/core/src/main/java/com/adobe/cq/commerce/core/components/models/productteaser/ProductTeaser.java) uitbreidt.

   Er is al een nieuwe methode toegevoegd met de naam `isShowBadge()` om een badge weer te geven als het product als &quot;Nieuw&quot; wordt beschouwd.

1. Voeg een nieuwe methode, `isEcoFriendly()` aan de interface toe:

   ```java
   @ProviderType
   public interface MyProductTeaser extends ProductTeaser {
       // Extend the existing interface with the additional properties which you
       // want to expose to the HTL template.
       public Boolean isShowBadge();
   
       public Boolean isEcoFriendly();
   }
   ```

   Dit is een nieuwe methode die we zullen introduceren om de logica in te kapselen om aan te geven of het product het `eco_friendly` attribuut heeft dat aan **Ja** of **Nee** wordt geplaatst.

1. Ga vervolgens naar de `MyProductTeaserImpl.java` at `core/src/main/java/com/venia/core/models/commerce/MyProductTeaserImpl.java`.

   Met het [delegatiepatroon voor Sling Models](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) kan `MyProductTeaserImpl` worden verwezen naar `ProductTeaser` het model via de `sling:resourceSuperType` eigenschap:

   ```java
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductTeaser productTeaser;
   ```

   Voor alle methodes die wij niet willen met voeten treden of veranderen, kunnen wij eenvoudig de waarde terugkeren die de `ProductTeaser` winst. Bijvoorbeeld:

   ```java
   @Override
   public String getImage() {
       return productTeaser.getImage();
   }
   ```

   Hierdoor minimaliseert u de hoeveelheid Java-code die een implementatie moet schrijven.

1. Een van de extra extensiepunten die door AEM CIF Core Components wordt geboden, is de `AbstractProductRetriever` instantie die toegang biedt tot specifieke productkenmerken. Inspect de `initModel()` methode:

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
   
           if (productRetriever != null) {
               productRetriever.extendProductQueryWith(p -> p.createdAt());
           }
   
       }
   ...
   ```

   De `@PostConstruct` aantekening zorgt ervoor dat deze methode wordt geroepen zodra het het Verdelen Model wordt geïnitialiseerd.

   Bericht dat de vraag van product GraphQL reeds gebruikend de `extendProductQueryWith` methode is uitgebreid om de extra `created_at` attributen terug te winnen. Dit kenmerk wordt later gebruikt als onderdeel van de `isShowBadge()` methode.

1. Werk de vraag GraphQL bij om de `eco_friendly` attributen in de gedeeltelijke vraag te omvatten:

   ```java
   //MyProductTeaserImpl.java
   
   private static final String ECO_FRIENDLY_ATTRIBUTE = "eco_friendly";
   
   @PostConstruct
   public void initModel() {
       productRetriever = productTeaser.getProductRetriever();
   
       if (productRetriever != null) {
           productRetriever.extendProductQueryWith(p ->
                productRetriever.extendProductQueryWith(p -> p
                   .createdAt()
                   .addCustomSimpleField(ECO_FRIENDLY_ATTRIBUTE)
               );
           );
       }
   }
   ```

   Toevoegen aan de `extendProductQueryWith` methode is een krachtige manier om ervoor te zorgen dat aanvullende productkenmerken beschikbaar zijn voor de rest van het model. Het minimaliseert ook het aantal uitgevoerde vragen.

   In de bovenstaande code wordt het`addCustomSimpleField` kenmerk gebruikt om het `eco_friendly` kenmerk op te halen. Dit illustreert hoe u voor om het even welke douanekenmerken kunt vragen die deel van het schema van de Magento uitmaken.

   >[!NOTE]
   >
   > De `createdAt()` methode is daadwerkelijk geïmplementeerd als onderdeel van de [productinterface](https://github.com/adobe/commerce-cif-magento-graphql/blob/master/src/main/java/com/adobe/cq/commerce/magento/graphql/ProductInterface.java). De meeste algemeen gevonden schemakenmerken zijn uitgevoerd, zodat gebruik slechts `addCustomSimpleField` voor echt douanekenmerken.

1. Voeg een registreerapparaat toe voor foutopsporing in de Java-code:

   ```java
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   ...
   @Model(adaptables = SlingHttpServletRequest.class, adapters = MyProductTeaser.class, resourceType = MyProductTeaserImpl.RESOURCE_TYPE)
   public class MyProductTeaserImpl implements MyProductTeaser {
   
   private static final Logger LOGGER = LoggerFactory.getLogger(MyProductTeaserImpl.class);
   ```

1. Implementeer vervolgens de `isEcoFriendly()` methode:

   ```java
   @Override
   public Boolean isEcoFriendly() {
   
       Integer ecoFriendlyValue;
       try {
           ecoFriendlyValue = productRetriever.fetchProduct().getAsInteger(ECO_FRIENDLY_ATTRIBUTE);
           if(ecoFriendlyValue != null && ecoFriendlyValue.equals(Integer.valueOf(1))) {
               LOGGER.info("*** Product is Eco Friendly**");
               return true;
           }
       } catch (SchemaViolationError e) {
           LOGGER.error("Error retrieving eco friendly attribute");
       }
       LOGGER.info("*** Product is not Eco Friendly**");
       return false;
   }
   ```

   In de bovenstaande methode `productRetriever` wordt de methode gebruikt om het product op te halen en wordt de `getAsInteger()` methode gebruikt om de waarde van het `eco_friendly` kenmerk op te halen. Gebaseerd op de vragen GraphQL wij vroeger in werking stelden weten wij dat de verwachte waarde wanneer het `eco_friendly` attribuut aan &quot;**ja**&quot;wordt geplaatst eigenlijk een geheel van **1** is.

   Nu het Sling Model is bijgewerkt, moet de prijsverhoging van de Component worden bijgewerkt om eigenlijk een indicator van **Milieuvriendelijk** te tonen die op het het Verschilderen Model wordt gebaseerd.

## De opmaak van de producttaser aanpassen {#customize-markup-product-teaser}

Een algemene uitbreiding van AEM componenten is het wijzigen van de markering die door de component wordt gegenereerd. Dit wordt gedaan door het manuscript [met voeten te treden](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html) HTML dat de component gebruikt om zijn prijsverhoging terug te geven. HTML Template Language (HTL) is een lichte sjabloontaal die AEM componenten gebruiken om markeringen dynamisch te renderen op basis van geschreven inhoud, zodat de componenten opnieuw kunnen worden gebruikt. De producttaser kan bijvoorbeeld steeds opnieuw worden gebruikt om verschillende producten weer te geven.

In ons geval willen we een banner boven op het gummetje weergeven om aan te geven dat het product &quot;Eco Friendly&quot; is op basis van een aangepast kenmerk. Het ontwerppatroon voor het [aanpassen van de opmaak](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html#customizing-the-markup) van een component is in feite standaard voor alle AEM Componenten, niet alleen voor de AEM CIF Core-componenten.

1. In winde, navigeer en breid de `ui.apps` module uit en breid de omslaghiërarchie uit aan: `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productteaser` en inspecteer het `.content.xml` bestand.

   ![Productieteams ui.apps](../assets/customize-cif-components/product-teaser-ui-apps-ide.png)

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0" xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
       jcr:description="Product Teaser Component"
       jcr:primaryType="cq:Component"
       jcr:title="Product Teaser"
       sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"
       componentGroup="Venia - Commerce"/>
   ```

   Hierboven vindt u de componentdefinitie voor de Product Teaser Component in ons project. Let op de eigenschap `sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"`. Dit is een voorbeeld van het maken van een [Proxy-component](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/using.html#create-proxy-components). In plaats van alle HTML-scripts van de Product Teaser te kopiëren en te plakken van de AEM CIF Core Components, kunnen we de code gebruiken `sling:resourceSuperType` om alle functionaliteit over te nemen.

1. Open the file `productteaser.html`. Dit is een kopie van het `productteaser.html` bestand van de [CIF Product Teaser](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser/productteaser.html)

   ```html
   <!--/* productteaser.html */-->
   <sly data-sly-use.product="com.venia.core.models.commerce.MyProductTeaser"
       data-sly-use.templates="core/wcm/components/commons/v1/templates.html"
       data-sly-use.actionsTpl="actions.html"
       data-sly-test.isConfigured="${properties.selection}"
       data-sly-test.hasProduct="${product.url}">
   ```

   U ziet dat het Sling-model voor `MyProductTeaser` wordt gebruikt en aan de `product` variabele is toegewezen.

1. Wijzig `productteaser.html` om een vraag aan de `isEcoFriendly` methode te maken die in de vorige oefening wordt uitgevoerd:

   ```html
   ...
   <div data-sly-test="${isConfigured && hasProduct}" class="item__root" data-cmp-is="productteaser" data-virtual="${product.virtualProduct}">
       <div data-sly-test="${product.showBadge}" class="item__badge">
           <span>${properties.text || 'New'}</span>
       </div>
       <!--/* Insert call to Eco Friendly here */-->
       <div data-sly-test="${product.ecoFriendly}" class="item__eco">
           <span>Eco Friendly</span>
       </div>
   ...
   ```

   Wanneer het roepen van een het Verdelen Model methode in HTML wordt het `get` en `is` gedeelte van de methode gelaten vallen en de eerste brief wordt verlaagd. Dus `isShowBadge()` wordt `.showBadge` en `isEcoFriendly` wordt `.ecoFriendly`. Gebaseerd op de booleaanse waarde die van is teruggekeerd `.isEcoFriendly()` bepaalt als het `<span>Eco Friendly</span>` wordt getoond.

   Meer informatie over `data-sly-test` en andere [HTML-blokinstructies vindt u hier](https://docs.adobe.com/content/help/en/experience-manager-htl/using/htl/block-statements.html#test).

1. Sparen de veranderingen en stel de updates in om het gebruiken van uw Maven vaardigheden, van een terminal van de bevellijn te AEM:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

1. Open een nieuw browservenster en navigeer naar AEM en de **OSGi-console** > **Status** > **Sling Models**: [http://localhost:4502/system/console/status-slingmodels](http://localhost:4502/system/console/status-slingmodels)

1. Zoek naar `MyProductTeaserImpl` en u zou een lijn als het volgende moeten zien:

   ```plain
   com.venia.core.models.commerce.MyProductTeaserImpl - venia/components/commerce/productteaser
   ```

   Dit wijst erop dat het het Verdelen Model behoorlijk is opgesteld en aan de correcte component in kaart gebracht.

1. Vernieuw naar de startpagina **van** Venia op [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html) waar de Product Teaser is toegevoegd.

   ![Eco Friendly message displayed](../assets/customize-cif-components/eco-friendly-text-displayed.png)

   Als het `eco_friendly` kenmerk van het product is ingesteld op **Ja**, ziet u de tekst &quot;Milieuvriendelijk&quot; op de pagina. Probeer over te schakelen op verschillende producten om de gedragswijziging te zien.

1. Open vervolgens de AEM `error.log` om de loginstructies te bekijken die we hebben toegevoegd. De `error.log` locatie is `<AEM SDK Install Location>/crx-quickstart/logs/error.log`.

   Zoek in de AEM logboeken naar de logboekinstructies die in het Sling-model zijn toegevoegd:

   ```plain
   2020-08-28 12:57:03.114 INFO [com.venia.core.models.commerce.MyProductTeaserImpl] *** Product is Eco Friendly**
   ...
   2020-08-28 13:01:00.271 INFO [com.venia.core.models.commerce.MyProductTeaserImpl] *** Product is not Eco Friendly**
   ...
   ```

   >[!CAUTION]
   >
   > U kunt ook enkele stacksporen zien als het product dat in de teaser wordt gebruikt, niet het `eco_friendly` kenmerk heeft als onderdeel van de kenmerkset van het apparaat.

## Stijlen toevoegen voor Eco-vriendelijke badge {#add-styles}

Op dit moment werkt de logica voor het weergeven van de **milieuvriendelijke** badge, maar voor de normale tekst kunnen enkele stijlen worden gebruikt. Voeg vervolgens een pictogram en stijlen toe aan de `ui.frontend` module om de implementatie te voltooien.

1. Download het bestand [eco_vriendelijk.svg](../assets/customize-cif-components/eco_friendly.svg) . Dit wordt gebruikt als **milieuvriendelijk** badge.
1. Ga terug naar winde en navigeer aan de `ui.frontend` omslag.
1. Voeg het `eco_friendly.svg` bestand toe aan de `ui.frontend/src/main/resources/images` map:

   ![Eco Friendly SVG toegevoegd](../assets/customize-cif-components/eco-friendly-svg-added.png)

1. Open het bestand `productteaser.scss` om `ui.frontend/src/main/styles/commerce/_productteaser.scss`.
1. Voeg de volgende regels van de Golf binnen de `.productteaser` klasse toe:

   ```scss
   .productteaser {
       ...
       .item__eco {
           width: 60px;
           height: 60px;
           left: 0px;
           overflow: hidden;
           position: absolute;
           padding: 5px;
   
       span {
           display: block;
           position: absolute;
           width: 45px;
           height: 45px;
           text-indent: -9999px;
           background: no-repeat center center url('../resources/images/eco_friendly.svg'); 
           }
       }
   ...
   }
   ```

   >[!NOTE]
   >
   > Bekijk de [stijlvolle CIF Core-componenten](./style-cif-component.md) voor meer informatie over front-end workflows.

1. Sparen de veranderingen en stel de updates in om het gebruiken van uw Maven vaardigheden, van een terminal van de bevellijn te AEM:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallPackage,cloud
   ```

1. Vernieuw naar de startpagina **van** Venia op [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html) waar de Product Teaser is toegevoegd.

   ![Eco-vriendelijke badge - definitieve implementatie](../assets/customize-cif-components/final-product-teaser-eco-badge.png)

## Gefeliciteerd {#congratulations}

U hebt zojuist uw eerste AEM CIF-component aangepast! Download de [voltooide oplossingsdossiers hier](../assets/customize-cif-components/customize-cif-component-SOLUTION_FILES.zip).

## Bonus Challenge {#bonus-challenge}

Controleer de functionaliteit van de **nieuwe** badge die al is geïmplementeerd in de producttaser. Probeer een extra selectievakje voor auteurs toe te voegen om te bepalen wanneer de **milieuvriendelijk** badge moet worden weergegeven. U moet het dialoogvenster voor componenten bijwerken op `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productteaser/_cq_dialog/.content.xml`.

![Nieuwe uitdaging voor Badge-implementatie](../assets/customize-cif-components/new-badge-implementation-challenge.png)

## Aanvullende bronnen {#additional-resources}

* [AEM Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)
* [AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components)
* [Aanpassen AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components/wiki/Customizing-CIF-Core-Components)
* [Kerncomponenten aanpassen](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/customizing.html)
* [Aan de slag met AEM Sites](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)