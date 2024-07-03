---
title: Aangepaste kenmerken voor CIF productcarrousel
description: Leer hoe u de AEM CIF component Product Carousel kunt uitbreiden door het verkoopmodel bij te werken en de markering aan te passen.
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 594f0e6ec88851c86134be8d5d7f1719f74ddf4f
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# Aangepaste kenmerken voor CIF productcarrousel {#product-carousel}

## Inleiding {#intro}

De component Product Carousel wordt uitgebreid door deze zelfstudie. Als eerste stap voegt u een exemplaar van de productcarrousel toe aan de startpagina om inzicht te krijgen in de basislijnfunctionaliteit:

1. Ga bijvoorbeeld naar de startpagina van de site [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)
1. Plaats een nieuwe productcarrouselcomponent in de hoofdlay-outcontainer op de pagina.
   ![Productcarrouselcomponent](/help/commerce-cloud/assets/product-carousel-component.png)
1. Vouw het zijpaneel uit (indien nog niet in-/uitgeschakeld) en schakel het vervolgkeuzemenu voor het zoeken van elementen naar **Producten**.
     ![Carrouselproducten](/help/commerce-cloud/assets/carousel-products.png)    
1. Dit zou een lijst van beschikbare producten van een verbonden instantie van Adobe Commerce moeten tonen.
   ![Verbonden instantie](/help/commerce-cloud/assets/connected-instance.png)
1. Producten worden hieronder weergegeven met standaardeigenschappen:
   ![Product weergegeven met eigenschappen](/help/commerce-cloud/assets/discount.png)

## Het verkoopmodel bijwerken {#update-sling-model}

U kunt de bedrijfslogica van de Carousel van het Product uitbreiden door een het Verkopen Model uit te voeren:

1. In uw winde, navigeer onder de kernmodule aan `core/src/main/java/com/venia/core/models/commerce` en maak een CustomCarousel-interface die de CIF ProductCarousel-interface uitbreidt:

   ```
   package com.venia.core.models.commerce;
   import com.adobe.cq.commerce.core.components.models.productcarousel.ProductCarousel;
   public interface CustomCarousel extends ProductCarousel {
   }
   ```
1. Maak vervolgens een implementatieklasse `CustomCarouselImpl.java` om `core/src/main/java/com/venia/core/models/commerce/CustomCarouselImpl.java`.
Het delegatiepatroon voor verkoopmodellen maakt `CustomCarouselImpl` verwijzing `ProductCarousel` model via de `sling:resourceSuperType` eigenschap:

   ```
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductCarousel productCarousel;
   ```

1. De @PostConstruct-annotatie zorgt ervoor dat deze methode wordt aangeroepen wanneer het Sling-model wordt geïnitialiseerd. De GraphQL-query voor het product is al uitgebreid met de methode extendProductQueryWith om kenmerken op te halen. Werk de GraphQL-query bij om het kenmerk in de gedeeltelijke query op te nemen:

   ```
   @PostConstruct
   private void initModel() {
   productsRetriever = productCarousel.getProductsRetriever();
   
   if(productCarousel.getProductsRetriever() != null)
   productCarousel.getProductsRetriever().extendProductQueryWith(p -> p
   .createdAt()
   .addCustomSimpleField("accessory_gemstone_addon")
   );
   }
   ```

   In de bovenstaande code worden de `addCustomSimpleField` wordt gebruikt om de `accessory_gemstone_addon` kenmerk.

## De opmaak aanpassen {#customize-markup}

De markering verder aanpassen:

1. Een kopie maken van `productcard.html` van `/apps/core/cif/components/commerce/productcarousel/v1/productcarousel` (het kerncomponentpad) naar de module ui.apps `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productcarousel/productcard.html`.

1. Bewerken `productcard.html` om het douanekenmerk te roepen, dat in de implementatieklasse wordt vermeld:

   ```xml
   ..
   <div
       data-product-sku="${product.commerceIdentifier.value}"
       data-product-base-sku="${product.combinedSku.baseSku}"
       id="${product.id}"
       data-cmp-data-layer="${product.data.json}"
       class="card product__card">
       <span>${product.product.responseData['accessory_gemstone_addon']}</span>
       <a href="${product.URL}"
           target="${productCarousel.linkTarget}"
   ..
   ```

1. Sparen de veranderingen en stel de updates in om het gebruiken van uw Gemaakt bevel, van een bevel-lijn terminal te AEM. Het aangepaste kenmerk wordt weergegeven `accessory_gemstone_addon` waarde voor de geselecteerde producten op de pagina.
