---
title: Aangepaste kenmerken voor CIF Product Carousel
description: Leer hoe u de AEM CIF Product Carousel-component kunt uitbreiden door het Sling Model bij te werken en de markering aan te passen.
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: 758e0e13-c4d8-4d32-bcc9-91a36b3ffa98
index: false
source-git-commit: 80bd8da1531e009509e29e2433a7cbc8dfe58e60
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# Aangepaste kenmerken voor CIF Product Carousel {#product-carousel}

Leer hoe u de AEM CIF Product Carousel-component kunt uitbreiden door het Sling Model bij te werken en de markering aan te passen.

## Inleiding {#intro}

De component Product Carousel wordt uitgebreid door deze zelfstudie. Als eerste stap voegt u een exemplaar van de productcarrousel toe aan de startpagina om inzicht te krijgen in de basislijnfunctionaliteit:

1. Navigeer aan de Homepage van de plaats, bijvoorbeeld [ http://localhost :4502 /editor.html/content/acme/us/en.html ](http://localhost:4502/editor.html/content/acme/us/en.html)
1. Plaats een nieuwe productcarrouselcomponent in de hoofdlay-outcontainer op de pagina.

   ![ component van de Carrousel van het Product ](/help/commerce-cloud/cif-storefront/assets/product-carousel-component.png)

1. Breid het Zijpaneel (als niet reeds) van een knevel voorzien en schakelaar de activa finder dropdown aan **Producten**.

   ![ Carrouselproducten ](/help/commerce-cloud/cif-storefront/assets/carousel-products.png)

1. Dit zou een lijst van beschikbare producten van een verbonden instantie van Adobe Commerce moeten tonen.

   ![ Verbonden Instantie ](/help/commerce-cloud/cif-storefront/assets/connected-instance.png)

1. Producten worden hieronder weergegeven met standaardeigenschappen:

   ![ Product dat met Eigenschappen ](/help/commerce-cloud/cif-storefront/assets/discount.png) wordt getoond

## Het verkoopmodel bijwerken {#update-sling-model}

U kunt de bedrijfslogica van de Carousel van het Product uitbreiden door een het Verkopen Model uit te voeren:

1. In uw winde, navigeer onder de kernmodule aan `core/src/main/java/com/venia/core/models/commerce` en creeer een Interface CustomCarousel die de interface van CIF ProductCarousel uitbreidt:

   ```text
   package com.venia.core.models.commerce;
   import com.adobe.cq.commerce.core.components.models.productcarousel.ProductCarousel;
   public interface CustomCarousel extends ProductCarousel {
   }
   ```

1. Maak vervolgens een implementatieklasse `CustomCarouselImpl.java` op `core/src/main/java/com/venia/core/models/commerce/CustomCarouselImpl.java` .

   Met het delegatiepatroon voor Sling Models kan `CustomCarouselImpl` via de eigenschap `ProductCarousel` model verwijzen: `sling:resourceSuperType`

   ```text
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductCarousel productCarousel;
   ```

1. De `@PostConstruct` -annotatie zorgt ervoor dat deze methode wordt aangeroepen wanneer het Sling-model wordt geïnitialiseerd. De GraphQL-query voor het product is al uitgebreid met de methode extendProductQueryWith om kenmerken op te halen. Werk de GraphQL-query bij om het kenmerk in de gedeeltelijke query op te nemen:

   ```javascript
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

   In de bovenstaande code wordt `addCustomSimpleField` gebruikt om het kenmerk `accessory_gemstone_addon` op te halen.

## De opmaak aanpassen {#customize-markup}

De markering verder aanpassen:

1. Maak een kopie van `productcard.html` van `/apps/core/cif/components/commerce/productcarousel/v1/productcarousel` (het kerncomponentkruispad) naar de module ui.apps `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productcarousel/productcard.html` .

1. Bewerk `productcard.html` om het aangepaste kenmerk aan te roepen, dat in de implementatieklasse wordt vermeld:

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

1. Sparen de veranderingen en stel de updates aan AEM op gebruikend uw Maven bevel, van een bevel-lijn terminal. U kunt de aangepaste kenmerkwaarde `accessory_gemstone_addon` voor de geselecteerde producten op de pagina zien.
