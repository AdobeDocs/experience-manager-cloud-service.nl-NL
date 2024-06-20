---
title: Geavanceerde URL-configuraties
description: Leer hoe u de URL's voor product- en categoriepagina's aanpast. Met Aanpassen kunnen implementaties URL's optimaliseren voor zoekprogramma's en detectie bevorderen.
sub-product: Commerce
version: Cloud Service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
exl-id: 314494c4-21a9-4494-9ecb-498c766cfde7
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '2059'
ht-degree: 0%

---

# Geavanceerde URL-configuraties {#url}

>[!NOTE]
>
> SEO (Search Engine Optimization, zoekmachineoptimalisatie) is voor veel marketeers een belangrijke zorg geworden. Daarom moeten de SEO-zorgen over veel as a Cloud Service projecten op het gebied van Adobe Experience Manager (AEM) worden aangepakt. Zie [Aanbevolen werkwijzen voor SEO- en URL-beheer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/seo-and-url-management.html) voor aanvullende informatie.

[CIF kerncomponenten AEM](https://github.com/adobe/aem-core-cif-components) biedt geavanceerde configuraties om de URL&#39;s voor product- en categoriepagina&#39;s aan te passen. In veel implementaties worden deze URL&#39;s aangepast voor SEO-doeleinden (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s). De volgende videodetails hoe te om te vormen `UrlProvider` Service en kenmerken van [Sling Mapping](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) om de URL&#39;s voor product- en categoriepagina&#39;s aan te passen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Configuratie {#configuration}

Om te vormen `UrlProvider` een project moet voorzien in een configuratie op basis van de _Configuratie URL-provider CIF_.

>[!NOTE]
>
> Sinds versie 2.0.0 van de AEM CIF Core Components, verstrekt de configuratie van de Leverancier URL slechts vooraf bepaalde formaten URL, in plaats van vrij-tekst configureerbare formaten die van 1.x versies bekend worden. Bovendien is het gebruik van kiezers voor het doorgeven van gegevens in URL&#39;s vervangen door achtervoegsels.

### URL-indeling van productpagina {#product}

Vormt URLs van de productpagina&#39;s en steunt de volgende opties:

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (standaard)
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`

Als er een [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` wordt vervangen door `/content/venia/us/en/products/product-page`
* `{{sku}}` wordt bijvoorbeeld vervangen door de SKU van het product, `VP09`
* `{{url_key}}` wordt vervangen door `url_key` eigenschap, bijvoorbeeld `lenora-crochet-shorts`
* `{{url_path}}` wordt vervangen door `url_path`, bijvoorbeeld `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` wordt vervangen door bijvoorbeeld de geselecteerde variant; `VP09-KH-S`

Aangezien de `url_path` verouderd zijn, de vooraf gedefinieerde product-URL-indelingen gebruiken de indeling van een product `url_rewrites` en kies het pad met de meeste padsegmenten als alternatief `url_path` is niet beschikbaar.

Met de bovenstaande voorbeeldgegevens ziet een product-variant-URL die is opgemaakt met de standaard-URL-indeling eruit als `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S`.

### Categorie Pagina-URL-indeling {#product-list}

Hiermee configureert u de URL&#39;s van de pagina&#39;s in de categorie- of productlijst en ondersteunt u de volgende opties:

* `{{page}}.html/{{url_path}}.html` (standaard)
* `{{page}}.html/{{url_key}}.html`

Als er een [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` wordt vervangen door `/content/venia/us/en/products/category-page`
* `{{url_key}}` wordt vervangen door de categorie `url_key` eigenschap
* `{{url_path}}` wordt vervangen door de categorie `url_path`

Met de bovenstaande voorbeeldgegevens ziet een categoriepagina-URL die is opgemaakt met de standaard-URL-indeling eruit als `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html`.

>[!NOTE]
> 
> De `url_path` is een aaneenschakeling van `url_keys` van een product of categorie en het product of de categorie `url_key` gescheiden door `/` slash. Elk `url_key` wordt beschouwd als uniek binnen een bepaalde winkel.

### Winkelspecifieke configuratie {#store-specific-urlformats}

De categorie- en URL-indelingen voor productpagina&#39;s die voor het hele systeem zijn ingesteld door de _Configuratie URL-provider CIF_ kan voor elke winkel worden gewijzigd.

In de Configuratie van de CIF, kan een redacteur een alternatief product of formaat van de categoriepagina URL selecteren. Als daar niets wordt geselecteerd, valt de implementatie terug naar de systeem-brede configuratie.

Het wijzigen van de URL-indeling van een live website kan een negatief effect hebben op het organische verkeer van uw site. Zie [Aanbevolen procedures](#best-practices) en plant de wijziging van de URL-indeling vooraf zorgvuldig.

![Url-indelingen in CIF Configuration](assets/store-specific-url-formats.png)

>[!NOTE]
>
> De store-specific configuratie van de formaten URL vereist [CIF Core Components 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) en de nieuwste versie van de invoegtoepassing Adobe Experience Manager Content en Commerce.

## URL&#39;s voor productpagina&#39;s die zijn afgestemd op de categorie {#context-aware-pdps}

Omdat het mogelijk is om categoriegegevens te coderen in een product-URL, kunnen producten die in meerdere categorieën zijn ook worden geadresseerd met meerdere product-URL&#39;s.

Met de standaard-URL-indelingen selecteert u een van de mogelijke alternatieven met behulp van het volgende schema:

* als de `url_path` wordt bepaald door de e-commerce achterste gebruik het (afgekeurd)
* van de `url_rewrites` gebruik de URL&#39;s die eindigen met de `url_key` als alternatieven
* van deze alternatieven wordt de versie met de meeste padsegmenten gebruikt
* als er meerdere zijn, neemt u de eerste in de volgorde van de e-commerce-backend

Met dit schema selecteert u de `url_path` met de meeste voorouders, op basis van de veronderstelling dat een onderliggende categorie specifieker is dan de bovenliggende categorie. De geselecteerde `url_path` wordt beschouwd _canonicaal_ en wordt altijd gebruikt als de canonieke koppeling op productpagina&#39;s of in de sitemap van het product.

Wanneer een winkelier echter van een categoriepagina naar een productpagina navigeert, of van de ene productpagina naar de andere gerelateerde productpagina in dezelfde categorie, is het nuttig om de huidige categoriecontext te behouden. In dit geval worden de `url_path` de selectie moet de voorkeur geven aan alternatieven die zich binnen de huidige categoriecontext bevinden boven de _canonicaal_ hierboven beschreven selectie.

Deze functie moet zijn ingeschakeld in het dialoogvenster _Configuratie URL-provider CIF_. Als deze optie is ingeschakeld, worden alternatieven voor de selectiescore hoger weergegeven, wanneer

* ze komen overeen met delen van een bepaalde categorie `url_path` vanaf het begin (wazig voorvoegsel afstemmen)
* of ze komen overeen met een bepaalde categorie `url_key` overal (nauwkeurige gedeeltelijke aanpassing)

Neem bijvoorbeeld de reactie voor een [productquery](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) hieronder. Gezien het volgende:

* de gebruiker bevindt zich op de categoriepagina &quot;New Products / New in Summer 2022&quot;
* de winkel gebruikt de standaard URL-indeling van de categoriepagina

Het alternatief &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot;past twee van de de wegsegmenten van de context van het begin aan. Dat wil zeggen: &quot;nieuwe producten&quot; en &quot;nieuwe-in-zomer-2022&quot;. Als de winkel een URL-indeling voor de rubriekpagina gebruikt die alleen de categorie bevat `url_key`, blijft hetzelfde alternatief geselecteerd omdat het overeenkomt met de context `url_key` overal. In beide gevallen wordt de URL van de productpagina gemaakt voor &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot; `url_path`.

```
{
  "data": {
    "products": {
      "items": [
        {
          "sku": "VA18-GO-NA",
          "url_key": "gold-cirque-earrings",
          "url_rewrites": [
            {
              "url": "gold-cirque-earrings.html"
            },
            {
              "url": "venia-accessories/gold-cirque-earrings.html"
            },
            {
              "url": "venia-accessories/venia-jewelry/gold-cirque-earrings.html"
            },
            {
              "url": "new-products/gold-cirque-earrings.html"
            },
            {
              "url": "new-products/new-in-summer-2022/gold-cirque-earrings.html"
            }
          ]
        }
      ]
    }
  }
}
```

>[!NOTE]
>
> URL&#39;s van producten die geschikt zijn voor rubrieken zijn vereist [CIF Core Components 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) of hoger.

## Specifieke categorie en productpagina&#39;s {#specific-pages}

Het is mogelijk [meerdere categorieën en productpagina&#39;s](../authoring/multi-template-usage.md) alleen voor een specifieke subset van categorieën of producten van een catalogus.

### Selectiecriteria {#specific-pages-selection}

De selectie van een specifieke categoriepagina is recht vooruit, op basis van de categorie `url_path` of `url_key`. Overeenkomende subcategorieën worden alleen ondersteund voor URL-indelingen die de volledige categorie bevatten `url_path`. Anders alleen een exacte overeenkomst met de `url_key` is mogelijk.

Specifieke productpagina&#39;s worden geselecteerd door de SKU of de categorie van het product. Voor deze laatste is het vereist dat bepaalde categoriemo-informatie in de URL van het product wordt gecodeerd. Deze functionaliteit is alleen beschikbaar voor bepaalde standaard-URL-indelingen. Zie de volgende lijst voor een vergelijking die het formaat URL specifieke paginaselectie door SKU of categorie steunt.


| URL-indeling | door SKU | op categorie |
| ----------------------------------------------------- | ------ | ---------------- |
| `{{page}}.html/{{url_key}}.html` | nee | nee |
| `{{page}}.html/{{category}}/{{url_key}}.html` | nee | alleen exacte overeenkomst |
| `{{page}}.html/{{url_path}}.html` | nee | ja |
| `{{page}}.html/{{sku}}.html` | ja | nee |
| `{{page}}.html/{{sku}}/{{url_key}}.html` | ja | nee |
| `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html` | ja | alleen exacte overeenkomst |
| `{{page}}.html/{{sku}}/{{url_path}}.html` | ja | ja |

{style="table-layout:auto"}

>[!NOTE]
>
> Voor het selecteren van specifieke productpagina&#39;s per categorie is vereist [CIF Core Components 2.6.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) of hoger.

### Diepe koppeling {#specific-pages-deep-linking}

De `UrlProvider` is vooraf geconfigureerd om diepgaande koppelingen naar specifieke categorie- en productpagina&#39;s te genereren op instanties van de auteurslaag. Deze mogelijkheid is handig voor editors die in de modus Voorbeeld door een site bladeren, naar een specifiek product of een bepaalde categoriepagina navigeren en terugschakelen naar de modus Bewerken om de pagina te bewerken.

Op publicatielagen moeten URL&#39;s van cataloguspagina&#39;s echter stabiel blijven om bijvoorbeeld geen winsten te verliezen op beoordelingen van zoekmachines. Vanwege die publicatielaag worden op instanties standaard geen diepgaande koppelingen naar specifieke cataloguspagina&#39;s weergegeven. Als u dit gedrag wilt wijzigen, _Specifieke paginastrategie voor URL-provider CIF_ kan worden gevormd om specifieke pagina URLs altijd te produceren.

### Meerdere cataloguspagina&#39;s {#multiple-product-pages}

Wanneer editors volledige controle willen hebben over de navigatie op hoofdniveau van een site, is het mogelijk dat u niet de hoogste categorieën van een catalogus wilt weergeven met één cataloguspagina. In plaats daarvan kunnen editors meerdere cataloguspagina&#39;s maken, één voor elke categorie van de catalogus die ze in de navigatie op hoofdniveau willen opnemen.

In dat geval kan op elke cataloguspagina een verwijzing staan naar een product- en categoriepagina die specifiek is voor de categorie die voor de cataloguspagina is geconfigureerd. De `UrlProvider` gebruikt deze verbindingen om verbindingen voor de pagina&#39;s en de categorieën in de gevormde categorie tot stand te brengen. Om prestatieredenen worden echter alleen de onderliggende elementen van de directe cataloguspagina van de basis-/landingspagina van een site in overweging genomen.

Het wordt aanbevolen dat de product- en categoriepagina&#39;s van een cataloguspagina aan die cataloguspagina worden gekoppeld, anders werken componenten zoals Navigatie of Breadcrumb mogelijk niet correct.

>[!NOTE]
>
> Volledige ondersteuning voor meerdere cataloguspagina&#39;s is vereist [CIF Core Components 2.10.0](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.10.0) of hoger.

## Aanpassingen {#customization}

### Aangepaste URL-indelingen {#custom-url-format}

Om een formaat van douaneURL te verstrekken, kan een project of uitvoeren [`ProductUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) of de [`CategoryUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) de dienstinterface en registreert de implementatie als dienst OSGI. Deze implementaties, indien beschikbaar, vervangen de geconfigureerde, vooraf gedefinieerde indeling. Als er veelvoudige geregistreerde implementaties zijn, vervangt één met de hogere de dienstrangschikking degenen met de lagere de dienstrangschikking.

De de formaatimplementaties van douaneURL moeten een paar methodes uitvoeren om een URL van bepaalde parameters te bouwen, en een URL te ontleden om de zelfde parameters respectievelijk terug te keren.

### Combineren met Sling Mappings {#sling-mapping}

Naast de `UrlProvider`is het ook mogelijk om [Sling Mappings](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) om URL&#39;s te herschrijven en te verwerken. Het project AEM Archetype biedt ook [een voorbeeldconfiguratie](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) om sommige Wijzen van het Monteren voor haven 4503 (publiceren) en 80 (Verzender) te vormen.

### Combineren met AEM Dispatcher {#dispatcher}

URL herschrijft kan ook worden bereikt door AEM Dispatcher HTTP-server met `mod_rewrite` -module. De [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype) verstrekt een verwijzing AEM Dispatcher config die reeds basisomvat [herschrijfregels](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) voor de gegenereerde grootte.

## Aanbevolen procedures {#best-practices}

### Kies de beste URL-indeling {#choose-url-format}

Zoals vermeld voordat u een van de beschikbare standaardindelingen selecteert of zelfs een aangepaste indeling implementeert, is de toepassing in hoge mate afhankelijk van de behoeften en vereisten van een winkel. De volgende suggesties kunnen helpen een goed opgeleid besluit te nemen.

_**Gebruik een indeling van de URL van de productpagina die de SKU bevat.**_

De CIF Componenten van de Kern gebruiken SKU als primaire herkenningsteken in alle componenten. Als de URL-indeling van de productpagina niet de SKU bevat, is een GraphQL-query nodig om deze op te lossen. Deze resolutie kan van invloed zijn op de tijd-aan-eerste-byte. Ook, kan het gewenst zijn, dat de kopers producten door SKU kunnen vinden gebruikend onderzoeksmotoren.

_**Gebruik een URL-indeling van de productpagina die de categoriecontext bevat.**_

Sommige functies van de CIF URL-provider zijn alleen beschikbaar wanneer u product-URL-indelingen gebruikt die de categoriecontext coderen, zoals de categorie `url_key` of de categorie `url_path`. Zelfs als deze functies niet vereist zijn voor een nieuwe winkel, helpt het gebruik van een van deze URL-indelingen in het begin de migratie-inspanningen in de toekomst te verminderen.

_**Balans tussen URL-lengte en gecodeerde informatie.**_

Afhankelijk van de grootte van de catalogus, met name de grootte en diepte van de categoriestructuur, is het wellicht niet verstandig om de volledige `url_path` van categorieën in de URL. In dat geval kan de lengte van de URL worden verminderd door alleen de categorie&#39;s `url_key` in plaats daarvan. Deze methode ondersteunt de meeste functies die beschikbaar zijn wanneer u de categorie gebruikt `url_path`.

Ook gebruiken [Sling Mappings](#sling-mapping) om SKU met het product te combineren `url_key`. In de meeste elektronische handelsystemen, volgt SKU een bepaald formaat en scheidt SKU van `url_key` voor binnenkomende verzoeken moet gemakkelijk mogelijk zijn. Daarom moet het mogelijk zijn om de URL van een productpagina te herschrijven naar `/p/{{category}}/{{sku}}-{{url_key}}.html`en een categorie-URL naar `/c/{{url_key}}.html` respectievelijk. De `/p` en `/c` voorvoegsel is nog steeds nodig om product- en categoriepagina&#39;s te onderscheiden van andere inhoudspagina&#39;s.

### Migreren naar een nieuwe URL-indeling {#migrate-url-formats}

Veel van de standaard-URL-indelingen zijn op de een of andere manier compatibel met elkaar. Dit betekent dat URL&#39;s die door een van deze indelingen zijn opgemaakt, door een andere kunnen worden geparseerd. Hierdoor kunt u gemakkelijker migreren tussen URL-indelingen.

Aan de andere kant hebben zoekprogramma&#39;s tijd nodig om alle cataloguspagina&#39;s opnieuw in te delen met de nieuwe URL-indeling. Om dit proces te ondersteunen en ook de gebruikerservaring te verbeteren, wordt aanbevolen om omleidingen te bieden die de gebruiker van de oude URL&#39;s naar de nieuwe URL&#39;s sturen.

Eén manier om dat mogelijk te doen, is een werkgebiedomgeving verbinden met de back-end van de e-commerce productie en deze zodanig configureren dat de nieuwe URL-indeling wordt gebruikt. Verkrijg daarna de [sitemap van CIF producten wordt gegenereerd door de sitemapgenerator](../../overview/seo-and-url-management.md) voor zowel het stadium als de productieomgeving, en deze gebruiken om een [Apache httpd-kaart herschrijven](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html). Deze herschrijfkaart kan vervolgens samen met de rollout van de nieuwe URL-indeling worden geïmplementeerd op de Dispatcher.

## Voorbeeld {#example}

De [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) Het project bevat voorbeeldconfiguraties om het gebruik van aangepaste URL&#39;s voor product- en categoriepagina&#39;s aan te tonen. Met deze configuratie kan elk project afzonderlijke URL-patronen instellen voor product- en categoriepagina&#39;s op basis van hun SEO-behoeften. Een combinatie van CIF `UrlProvider` en Sling Mappings zoals hierboven beschreven wordt gebruikt.

>[!NOTE]
>
>Deze configuratie moet met het externe domein worden aangepast dat door het project wordt gebruikt. Sling Mappings werkt gebaseerd op hostname en domein. Daarom is deze configuratie onbruikbaar gemaakt door gebrek en moet vóór plaatsing worden toegelaten. U doet dit door de naam van de sorteerfunctie te wijzigen `hostname.adobeaemcloud.com` map in `ui.content/src/main/content/jcr_root/etc/map.publish/https` volgens de gebruikte domeinnaam en laat dit config toe door toe te voegen `resource.resolver.map.location="/etc/map.publish"` aan de `JcrResourceResolver` config van het project.

## Aanvullende bronnen {#additional}

* [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
* [Brontoewijzing AEM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html)
* [Sling Mappings](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
