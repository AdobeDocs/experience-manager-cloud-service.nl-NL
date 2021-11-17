---
title: Geavanceerde URL-configuraties
description: Leer hoe u de URL's voor product- en categoriepagina's aanpast. Hiermee kunnen implementaties URL's optimaliseren voor zoekprogramma's en detectie bevorderen.
sub-product: Commerce
version: cloud-service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
exl-id: 314494c4-21a9-4494-9ecb-498c766cfde7,363cb465-c50a-422f-b149-b3f41c2ebc0f
source-git-commit: 9844a092f440f4520b4dd75e6a6253a4593eb630
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 6%

---

# Geavanceerde URL-configuraties {#url}

>[!NOTE]
>
> SEO (Search Engine Optimization, zoekmachineoptimalisatie) is voor veel marketeers een belangrijke zorg geworden. Daarom moeten SEO-problemen in veel Adobe Experience Manager (AEM) as a Cloud Service-projecten worden opgelost. Lees [Aanbevolen werkwijzen voor SEO- en URL-beheer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/seo-and-url-management.html) voor aanvullende informatie.

[AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components) biedt geavanceerde configuraties om de URL&#39;s voor product- en categoriepagina&#39;s aan te passen. In veel implementaties worden deze URL&#39;s aangepast voor SEO-doeleinden (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s). De volgende videodetails hoe te om te vormen `UrlProvider` Service en kenmerken van [Sling Mapping](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) om de URL&#39;s voor product- en categoriepagina&#39;s aan te passen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Configuratie {#configuration}

Om het `UrlProvider` De dienst volgens de eisen van SEO en vereist een project moet een configuratie OSGI voor de &quot;configuratie van de Leverancier CIF URL&quot;verstrekken.

>[!NOTE]
>
> Sinds versie 2.0.0 van de AEM CIF Core Components, verstrekt de configuratie van de Leverancier URL slechts vooraf bepaalde url formaten, in plaats van vrij-tekst configureerbare formaten die van 1.x versies worden gekend. Bovendien is het gebruik van kiezers voor het doorgeven van gegevens in URL&#39;s vervangen door achtervoegsels.

### URL-indeling van productpagina {#product}

Hiermee configureert u de URL&#39;s van de productpagina&#39;s en ondersteunt u de volgende opties:

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (standaardwaarde)
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`

In het geval van de [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` wordt vervangen door `/content/venia/us/en/products/product-page`
* `{{sku}}` worden vervangen door de sku van het product, bijvoorbeeld `VP09`
* `{{url_key}}` worden vervangen door de `url_key` eigenschap, bijvoorbeeld `lenora-crochet-shorts`
* `{{url_path}}` worden vervangen door de `url_path`, bijvoorbeeld `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` worden vervangen door de momenteel geselecteerde variant, bijvoorbeeld `VP09-KH-S`

Met de bovenstaande voorbeeldgegevens ziet een product-variant-URL die is opgemaakt met de standaard-URL-indeling er ongeveer zo uit `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S`.

### Categorie Pagina-URL-indeling {#product-list}

Hiermee configureert u de URL&#39;s van de pagina&#39;s in de categorie- of productlijst en ondersteunt u de volgende opties:

* `{{page}}.html/{{url_path}}.html` (standaardwaarde)
* `{{page}}.html/{{url_key}}.html`

In het geval van de [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` wordt vervangen door `/content/venia/us/en/products/category-page`
* `{{url_key}}` worden vervangen door de categorie `url_key` eigenschap
* `{{url_path}}` worden vervangen door de categorie `url_path`

Met de bovenstaande voorbeeldgegevens ziet een categoriepagina-URL die is opgemaakt met de standaard-URL-indeling eruit als `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html`.

>[!NOTE]
> 
> De `url_path` is een aaneenschakeling van `url_keys` van een product of categorie en het product of de categorie `url_key` gescheiden door `/` schuine streep.

## Aangepaste URL-indelingen {#custom-url-format}

Als u een aangepaste URL-indeling wilt opgeven, kan een project de opdracht [`UrlFormat` interface](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/UrlFormat.html) en registreer de implementatie als dienst OSGI, die of als categorie pagina of productpagina url formaat gebruikt. De `UrlFormat#PROP_USE_AS` het de dienstbezit wijst erop, welke van de gevormde vooraf bepaalde formaten te vervangen:

* `useAs=productPageUrlFormat`, vervangt de geconfigureerde URL-indeling van de productpagina
* `useAs=categoryPageUrlFormat`, vervangt de geconfigureerde URL-indeling voor de categoriepagina

Als er veelvoudige implementaties van zijn `UrlFormat` die als OSGI-diensten is geregistreerd, vervangt degene met de hoogste rangorde de dienst(en) door de lagere rangorde.

De `UrlFormat` moet een paar methodes uitvoeren om een URL van een bepaalde Kaart van parameters te bouwen en een URL te ontleden om de zelfde Kaart van parameters terug te keren. De parameters zijn hetzelfde als hierboven beschreven, alleen voor categorieën en `{{uid}}` wordt de `UrlFormat`.

## Combineren met Sling Mappings {#sling-mapping}

Naast de `UrlProvider`is het ook mogelijk [Sling Mappings](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) om URL&#39;s te herschrijven en te verwerken. Het project AEM Archetype biedt ook [een voorbeeldconfiguratie](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) om sommige Toewijzingen van de Verschuiving voor haven 4503 (publiceren) en 80 (verzender) te vormen.

## Combineren met AEM Dispatcher {#dispatcher}

URL herschrijft kan ook worden bereikt door AEM Dispatcher HTTP-server te gebruiken met `mod_rewrite` module. De [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype) verstrekt een verwijzing AEM Dispatcher config die reeds basisomvat [herschrijfregels](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) voor de gegenereerde grootte.

## Voorbeeld

De [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) Het project bevat voorbeeldconfiguraties om het gebruik van aangepaste URL&#39;s voor product- en categoriepagina&#39;s aan te tonen. Hierdoor kan elk project afzonderlijke URL-patronen instellen voor product- en categoriepagina&#39;s op basis van hun SEO-behoeften. Een combinatie van CIF `UrlProvider` en Sling Mappings zoals hierboven beschreven wordt gebruikt.

>[!NOTE]
>
>Deze configuratie moet met het externe domein worden aangepast dat door het project wordt gebruikt. Sling Mappings werkt gebaseerd op hostname en domein. Daarom is deze configuratie onbruikbaar gemaakt door gebrek en moet vóór plaatsing worden toegelaten. De naam van de functie voor het toewijzen van objecten wijzigen `hostname.adobeaemcloud.com` map in `ui.content/src/main/content/jcr_root/etc/map.publish/https` volgens de gebruikte domeinnaam en laat dit config toe door toe te voegen `resource.resolver.map.location="/etc/map.publish"` aan de `JcrResourceResolver` config van het project.

## Aanvullende bronnen

* [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
* [Brontoewijzing AEM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html)
* [Sling Mappings](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
