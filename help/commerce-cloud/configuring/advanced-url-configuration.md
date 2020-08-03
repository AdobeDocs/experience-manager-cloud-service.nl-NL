---
title: Geavanceerde URL-configuraties
description: Geavanceerde URL-configuraties
translation-type: tm+mt
source-git-commit: 3a235e3d8e2d97e413f445df1f0bfe52e97024b3
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 2%

---


# Geavanceerde URL-configuraties {#url}

[AEM CIF Core Components](https://github.com/adobe/aem-core-cif-components) biedt geavanceerde configuraties om de URL&#39;s voor product- en categoriepagina&#39;s aan te passen. In veel implementaties worden deze URL&#39;s aangepast voor SEO-doeleinden (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s).  In de volgende video ziet u hoe u de `UrlProvider` service en functies van [Sling Mapping](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) configureert om de URL&#39;s voor product- en categoriepagina&#39;s aan te passen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Configuratie {#configuration}

Om de `UrlProvider` dienst volgens de eisen van SEO te vormen en een project moet een project een config OSGI voor de configuratie van de &quot;CIF URL van de Leverancier&quot;verstrekken, en de dienst vormen zoals hieronder beschreven.

>[!NOTE]
>
> Het project van het [Venia Reference store](https://github.com/adobe/aem-cif-guides-venia) , zie hieronder, omvat steekproefconfiguraties om het gebruik van douane URLs voor product en categoriepagina&#39;s aan te tonen.

### URL-sjabloon productpagina {#product}

Hierdoor worden de URL&#39;s van de productpagina&#39;s geconfigureerd met de volgende eigenschappen:

* **Sjabloon** voor product-URL: Hiermee definieert u de opmaak van URL&#39;s met een set plaatsaanduidingen. De standaardwaarde is `{{page}}.{{url_key}}.html#{{variant_sku}}`, die uiteindelijk URL&#39;s genereert, zoals bijvoorbeeld `/content/venia/us/en/products/product-page.chaz-kangeroo-hoodie.html#MH01-M-Orange` waar
   * `{{page}}` vervangen door `/content/venia/us/en/products/product-page`
   * `{{url_key}}` is vervangen door hier de `url_key` eigenschap Magento van het product, `chaz-kangeroo-hoodie`
   * `{{variant_sku}}` is vervangen door de geselecteerde variant, hier `MH01-M-Orange`
* **Locatie** van product-id: definieert de locatie van de id die wordt gebruikt om de productgegevens op te halen. De standaardwaarde is `SELECTOR`, de andere mogelijke waarde is `SUFFIX`. Met het vorige voorbeeld-URL betekent dit dat de id `chaz-kangeroo-hoodie` wordt gebruikt om de productgegevens op te halen.
* **Type** product-id: definieert het type id dat moet worden gebruikt bij het ophalen van de productgegevens. De standaardwaarde is `URL_KEY`, de andere mogelijke waarde is `SKU`. Met het vorige voorbeeld-URL betekent dit dat de productgegevens worden opgehaald met een Magento GraphQL-filter, zoals `filter:{url_key:{eq:"chaz-kangeroo-hoodie"}}`.

### URL-sjabloon van productlijstpagina {#product-list}

Hiermee configureert u de URL&#39;s van de pagina&#39;s met categorieën of productlijsten met de volgende eigenschappen:

* **Categorie-URL-sjabloon**: Hiermee definieert u de opmaak van URL&#39;s met een set plaatsaanduidingen. De standaardwaarde is `{{page}}.{{id}}.html`, die uiteindelijk URL&#39;s genereert, zoals bijvoorbeeld `/content/venia/us/en/products/category-page.3.html` waar
   * `{{page}}` vervangen door `/content/venia/us/en/products/category-page`
   * `{{id}}` is vervangen door de eigenschap Magento `id` van de categorie `3`
* **Locatie** van categorie-id: definieert de locatie van de id die wordt gebruikt om de productgegevens op te halen. De standaardwaarde is `SELECTOR`, de andere mogelijke waarde is `SUFFIX`. Met het vorige voorbeeld-URL betekent dit dat de id `3` wordt gebruikt om de productgegevens op te halen.
* **Type** categorie-id: definieert het type id dat moet worden gebruikt bij het ophalen van de productgegevens. De standaardwaarde en momenteel alleen de ondersteunde waarde is `ID`. Met het vorige voorbeeld-URL betekent dit dat de categoriegegevens worden opgehaald met een Magento GraphQL-filter, zoals `category(id:3)`.

Het is mogelijk om aangepaste eigenschappen toe te voegen voor elke sjabloon, zolang de corresponderende gegevens door de componenten worden ingesteld met behulp van de `UrlProvider`. Controleer bijvoorbeeld de code van de `ProductListItemImpl` klasse om te zien hoe dit wordt geïmplementeerd.

Het is ook mogelijk om de `UrlProvider` dienst met een volledig aangepaste dienst te vervangen OSGi. In dit geval, moet men de `UrlProvider` interface uitvoeren en het met een hogere de dienstrangschikking registreren om de standaardimplementatie te vervangen.

## Combineren met Sling Mappings {#sling-mapping}

Naast het `UrlProvider`, is het ook mogelijk om [Verschuivende Toewijzingen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) te vormen om URLs te herschrijven en te verwerken. Het project van Archetype van het AEM verstrekt ook [een voorbeeldconfiguratie](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) om sommige Toewijzingen Sling voor haven 4503 (publiceren) en 80 (verzender) te vormen.

## Combineren met AEM Dispatcher {#dispatcher}

URL herschrijft kan ook worden bereikt door AEM server van HTTP van Dispatcher met `mod_rewrite` module te gebruiken. Het [AEM Archetype](https://github.com/adobe/aem-project-archetype) van het Project verstrekt een verwijzing AEM Dispatcher config die reeds basisherschrijft regels [](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) voor de geproduceerde grootte omvat.

## Voorbeeld

Het project van het [Venia Reference store](https://github.com/adobe/aem-cif-guides-venia) bevat voorbeeldconfiguraties waarmee het gebruik van aangepaste URL&#39;s voor product- en categoriepagina&#39;s wordt getoond. Hierdoor kan elk project afzonderlijke URL-patronen instellen voor product- en categoriepagina&#39;s op basis van hun SEO-behoeften. Er wordt een combinatie van CIF- `UrlProvider` en Sling Mappings gebruikt zoals hierboven beschreven.

>[!NOTE]
>
>Deze configuratie moet met het externe domein worden aangepast dat door het project wordt gebruikt. Sling Mappings werkt gebaseerd op hostname en domein. Daarom is deze configuratie onbruikbaar gemaakt door gebrek en moet vóór plaatsing worden toegelaten. Om dit te doen anders noemt de Verschuivende `hostname.adobeaemcloud.com` omslag van de Toewijzing in `ui.content/src/main/content/jcr_root/etc/map.publish/https` volgens de gebruikte domeinnaam en laat dit config toe door `resource.resolver.map.location="/etc/map.publish"` aan `JcrResourceResolver` config van het project toe te voegen.

## Aanvullende bronnen

* [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
* [Brontoewijzing AEM](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/configuring/resource-mapping.html)
* [Sling Mappings](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
