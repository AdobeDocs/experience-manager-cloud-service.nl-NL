---
title: '[!DNL Live Search] CIF component Product Listening Page'
description: Het gebruiken van CIF componenten om  [!DNL Live Search]  component van de Pagina van het Product toe te laten van een AEM plaats
exl-id: 7f2d9a43-a7cb-4d9d-a108-b016cd1ff81e
feature: Commerce Integration Framework
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# [!DNL Live Search] CIF {#live-search-cif-component}

Live zoeken naar Adobe Commerce biedt een snelle, relevante en intuïtieve zoekervaring zonder extra kosten. Live zoeken, aangedreven door Adobe Sensei, maakt gebruik van kunstmatige intelligentie en computerleeralgoritmen om een diepgaande analyse van geaggregeerde bezoekersgegevens uit te voeren. Als deze gegevens in combinatie met uw Adobe Commerce-catalogus worden gebruikt, krijgt u een relevante en gepersonaliseerde winkelervaring.

In dit onderwerp wordt beschreven hoe u een AEM CIF gebruikt om de widget [!DNL Live Search] Product Listing Page (PLP) in uw AEM-site te implementeren.

## Vereisten {#prerequisites}

Dit onderwerp veronderstelt u een lokale [ AEM milieu ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html) opstelling hebt.

De component PLP vereist de [[!DNL Live Search]  Popover CIF component ](live-search-popover.md) om worden geïnstalleerd. Voor de PLP-widget is een browsersessievariabele nodig die door de pop-over wordt gegenereerd.

## Composer bijwerken {#update-composer}

Voeg gebeurtenismodules toe aan `ui.frontend/package.json`.

Bij regel 27, wijziging:

```json
...
  },

  "devDependencies": {

    "@babel/core": "^7.3.4",
...
```

tot:

```json
...
  },
  "type": "module",
  "devDependencies": {
    "@adobe/magento-storefront-event-collector": "^1.5.4",
    "@adobe/magento-storefront-events-sdk": "^1.5.4",
    "@babel/core": "^7.3.4",
...
```

## Bestanden wijzigen {#files-changes}

Meerdere bestanden moeten worden bijgewerkt om de functie [!DNL Live Search] in te schakelen. Bewerk de volgende bestanden. Regelnummers kunnen iets anders zijn dan hier weergegeven.

* ui.apps/src/main/content/jcr_root/apps/venia/clientlibs/clientlib-cif/.content.xml

  Voeg `core.cif.productlist.v1` aan de `embed` lijn toe.

  ```
  embed="[core.cif.components.common,core.cif.components.product.v3,core.cif.components.productcarousel.v1,core.cif.components.productcollection.v2,core.cif.components.productteaser.v1,core.cif.components.searchbar.v2,core.cif.components.header.v1,core.cif.components.carousel.v1,core.cif.components.categorycarousel.v1,core.cif.components.featuredcategorylist.v1,core.cif.components.storefront-events.v1,core.cif.components.extensions.product-recs.storefront-events-collector.v1,core.wcm.components.commons.site.link,core.cif.productlist.v1]"
  ```

* ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productlist/clientlibs/.content.xml

  Een bestand maken `.content.xml` :

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
    jcr:primaryType="cq:ClientLibraryFolder"
    allowProxy="{Boolean}true"
    categories="[core.cif.productlist.v1]"
    jsProcessor="[default:none,min:none]"/>
  ```

* ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productlist/clientlibs/css.txt

  Maak het bestand `css.txt` :

  ```text
  #base=css
  
  productlist.css
  ```

* ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productlist/clientlibs/css/productlist.css

  Het bestand maken `productlist.css`

  ```css
    /* #search-plp-root */
  
  html {
    font-size: 62.5% !important;
  }
  
  body {
    font-size: 1.6rem;
  }
  
  .root.container {
    max-width: inherit;
  }
  
  .container {
    margin-left: auto;
    margin-right: auto;
  }
  
  div.ds-sdk-sort-dropdown {
    z-index: 9;
  }
  ```

* ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productlist/clientlibs/js.txt

  Maak het bestand `js.txt` :

  ```text
  js/productlist.js
  ```

* ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productlist/clientlibs/js/productlist.js

  Maak het bestand `productlist.js` :

  ```javascript
  /*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  ~ Copyright 2023 Adobe
  ~
  ~ Licensed under the Apache License, Version 2.0 (the "License");
  ~ you may not use this file except in compliance with the License.
  ~ You may obtain a copy of the License at
  ~
  ~     http://www.apache.org/licenses/LICENSE-2.0
  ~
  ~ Unless required by applicable law or agreed to in writing, software
  ~ distributed under the License is distributed on an "AS IS" BASIS,
  ~ WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  ~ See the License for the specific language governing permissions and
  ~ limitations under the License.
  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
  "use strict";
  
  class ProductList {
    constructor() {
      const stateObject = {
        categoryName: null,
        currentCategoryUrlPath: null,
      };
      this._state = stateObject;
      this._init();
    }
  
    _init() {
      this._initWidgetPLP();
    }
  
    _injectStoreScript(src) {
      const script = document.createElement("script");
      script.type = "text/javascript";
      script.src = src;
  
      document.head.appendChild(script);
    }
  
    async _getStoreData() {
      // get from session storage
      const sessionData = sessionStorage.getItem(
        "WIDGET_STOREFRONT_INSTANCE_CONTEXT"
      );
      // WIDGET_STOREFRONT_INSTANCE_CONTEXT is set from searchbar/clientlibs/js/searchbar.js
      // if not, we will need to retrieve from graphql separately here.
  
      if (sessionData) {
        this._state.dataServicesSessionContext = JSON.parse(sessionData);
        return;
      }
    }
  
    getStoreConfigMetadata() {
      const storeConfig = JSON.parse(
        document
          .querySelector("meta[name='store-config']")
          .getAttribute("content")
      );
  
      const { storeRootUrl } = storeConfig;
      const redirectUrl = storeRootUrl.split(".html")[0];
      return { storeConfig, redirectUrl };
    }
  
    async _initWidgetPLP() {
      if (!window.LiveSearchPLP) {
        const liveSearchPlpSrc =
          "https://plp-widgets-ui.magento-ds.com/v1/search.js";
        this._injectStoreScript(liveSearchPlpSrc);
        // wait until script is loaded
        await new Promise((resolve) => {
          const interval = setInterval(() => {
            if (window.LiveSearchPLP && window.LiveSearchAutocomplete) {
              // Widget expects LiveSearchAutocomplete already loaded to rely on data-service-graphql
              clearInterval(interval);
              resolve();
            }
          }, 200);
        });
      }
      await this._getStoreData();
      const { dataServicesSessionContext } = this._state;
      if (!dataServicesSessionContext) {
        console.log("no dataServicesSessionContext");
        return;
      }
  
      const root = document.getElementById("search-plp-root");
      if (!root) {
        console.log("plp root not found.");
        return;
      }
      // get dataset from root
      const categoryUrlPath = root.getAttribute("data-plp-urlPath") || "";
      const categoryName = root.getAttribute("data-plp-title") || "";
      const storeDetails = {
        environmentId: dataServicesSessionContext.environment_id,
        environmentType: dataServicesSessionContext.environment,
        apiKey: dataServicesSessionContext.api_key,
        websiteCode: dataServicesSessionContext.website_code,
        storeCode: dataServicesSessionContext.store_code,
        storeViewCode: dataServicesSessionContext.store_view_code,
        config: {
          pageSize: dataServicesSessionContext.page_size,
          perPageConfig: {
            pageSizeOptions: dataServicesSessionContext.page_size_options,
            defaultPageSizeOption:
              dataServicesSessionContext.default_page_size_option,
          },
          minQueryLength: dataServicesSessionContext.min_query_length,
          currencySymbol: dataServicesSessionContext.currency_symbol,
          currencyRate: dataServicesSessionContext.currency_rate,
          displayOutOfStock: dataServicesSessionContext.display_out_of_stock,
          allowAllProducts: dataServicesSessionContext.allow_all_products,
          locale: dataServicesSessionContext.locale,
          currentCategoryUrlPath: categoryUrlPath,
          categoryName,
          displayMode: "", // "" for plp || "PAGE" for category/catalog
        },
        context: {
          customerGroup: dataServicesSessionContext.customer_group,
        },
        route: ({ sku }) => {
          return `${
            this.getStoreConfigMetadata().redirectUrl
          }.cifproductredirect.html/${sku}`;
        },
        searchQuery: "search_query",
      };
      setTimeout(() => {
        console.log("init PLP");
        window.LiveSearchPLP({ storeDetails, root });
      }, 0);
    }
  }
  
  (function () {
    function onDocumentReady() {
      new ProductList({});
    }
  
    if (document.readyState !== "loading") {
      onDocumentReady();
    } else {
      document.addEventListener("DOMContentLoaded", onDocumentReady);
    }
  })();
  ```

* ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productlist/productlist.html

  Bestand maken `productlist.html`:

  ```html
  <div
  data-sly-use.productList="com.adobe.cq.commerce.core.components.models.productlist.ProductList"
  id="search-plp-root"
  class="productlist__root"
  data-plp-urlPath="${productList.storefrontContext.urlPath}"
  data-plp-title="${productList.title}">
  </div>
  ```

* ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/searchresults/.content.xml

  Bewerk `.content.xml` op regel 6:

  ```xml
  sling:resourceSuperType="venia/components/commerce/productlist"
  ```

* ui.content/src/main/content/jcr_root/content/venia/language-masters/en/search/.content.xml

  Bewerk `.content.xml` op regel 21-22:

  ```xml
  sling:resourceType="venia/components/commerce/productlist"
  ```

* ui.content/src/main/content/jcr_root/content/venia/us/en/search/.content.xml

  Bewerk `.content.xml` op regel 26:

  ```xml
  sling:resourceType="venia/components/commerce/productlist"
  ```

* ui.frontend/src/main/components/App/App.js

  Bewerk `App.js` op regel 47, net boven `../../site/main.scss` :

  ```javascript
  import '@adobe/magento-storefront-event-collector';
  ```

* ui.tests/test-module/specs/venia/productlist-dialog.js

  Bewerk `productlist-dialog.js` en wijzig `describe` in `describe.skip` op regel 20:

  ```javascript
  describe.skip('Product List Component Dialog', function () {
  ```

## Niet-PLP pagina&#39;s {#non-plp-pages}

Er kunnen categorieën zijn waarin de standaardcategorie of cataloguspagina gewenst is, in plaats van de PLP-widget te gebruiken. In AEM moeten deze categoriepagina&#39;s handmatig worden geconfigureerd.

1. Selecteer op de pagina Auteur een paginasjabloon voor een categorie. _Winkel van Venia - Huis_ > _de Pagina van de Catalogus_ > _Winkel van Venia - de Pagina van de Categorie_ en selecteert &quot;Schaf de blik&quot;of creeer een nieuw paginamalplaatje.

![ selecteer het malplaatje ](../assets/cif-widget-1.jpg)

1. Klik de _sectie van Eigenschappen_ en selecteer _Commerce_ tabel.

![ kies Eigenschappen ](../assets/cif-widget-2.jpg)

1. Kies de categorie die u wilt weergeven met de geselecteerde paginasjabloon voor rubrieken.

![ selecteer de categorie ](../assets/cif-widget-3.jpg)
