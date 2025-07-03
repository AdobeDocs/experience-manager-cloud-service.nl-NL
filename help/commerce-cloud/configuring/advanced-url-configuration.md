---
title: Geavanceerde URL-configuraties
description: Leer hoe u de URL's voor product- en categoriepagina's aanpast. Met Aanpassen kunnen implementaties URL's optimaliseren voor zoekprogramma's en detectie bevorderen.
sub-product: Commerce
version: Experience Manager as a Cloud Service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
exl-id: 314494c4-21a9-4494-9ecb-498c766cfde7
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: tm+mt
source-wordcount: '2059'
ht-degree: 0%

---

# Geavanceerde URL-configuraties {#url}

>[!NOTE]
>
> SEO (Search Engine Optimization, zoekmachineoptimalisatie) is voor veel marketeers een belangrijke zorg geworden. Daarom moeten de SEO-zorgen over veel projecten op Adobe Experience Manager (AEM) as a Cloud Service worden aangepakt. Zie [ SEO en de Beste praktijken van het Beheer URL ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/seo-and-url-management.html?lang=nl-NL) voor extra informatie.

[ de Componenten van de Kern van AEM CIF van ](https://github.com/adobe/aem-core-cif-components) verstrekt geavanceerde configuraties om URLs voor product en categoriepagina&#39;s aan te passen. In veel implementaties worden deze URL&#39;s aangepast voor SEO-doeleinden (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s). De volgende videodetails hoe te om de `UrlProvider` Dienst en eigenschappen van [ het Schipen Afbeelding ](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) te vormen om URLs voor product en categoriepagina&#39;s aan te passen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Configuratie {#configuration}

Om de `UrlProvider` dienst volgens de eisen en de behoeften van SEO te vormen, moet een project een configuratie OSGI voor de _configuratie van de Leverancier van CIF URL_ verstrekken.

>[!NOTE]
>
> Sinds versie 2.0.0 van de AEM CIF Core Components, verstrekt de configuratie van de Leverancier URL slechts vooraf bepaalde formaten URL, in plaats van vrij-tekst configureerbare formaten die van 1.x versies bekend worden. Bovendien is het gebruik van kiezers voor het doorgeven van gegevens in URL&#39;s vervangen door achtervoegsels.

### URL-indeling van productpagina {#product}

Vormt URLs van de productpagina&#39;s en steunt de volgende opties:

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (standaardwaarde)
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{category}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`

Als er de [ opslag van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia) is:

* `{{page}}` wordt vervangen door `/content/venia/us/en/products/product-page`
* `{{sku}}` wordt bijvoorbeeld vervangen door de SKU van het product `VP09`
* `{{url_key}}` wordt bijvoorbeeld vervangen door de eigenschap `url_key` van het product. `lenora-crochet-shorts`
* `{{url_path}}` wordt bijvoorbeeld vervangen door `url_path` van het product `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` wordt vervangen door de geselecteerde variant, bijvoorbeeld `VP09-KH-S`

Aangezien de `url_path` is vervangen, gebruiken de vooraf gedefinieerde product-URL-indelingen de indeling van een product `url_rewrites` en kiezen de indeling met de meeste padsegmenten als alternatief als de `url_path` niet beschikbaar is.

Met de bovenstaande voorbeeldgegevens ziet een URL voor een productvariant die is opgemaakt met de standaard-URL-indeling eruit als `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S` .

### Categorie Pagina-URL-indeling {#product-list}

Hiermee configureert u de URL&#39;s van de pagina&#39;s in de categorie- of productlijst en ondersteunt u de volgende opties:

* `{{page}}.html/{{url_path}}.html` (standaardwaarde)
* `{{page}}.html/{{url_key}}.html`

Als er de [ opslag van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia) is:

* `{{page}}` wordt vervangen door `/content/venia/us/en/products/category-page`
* `{{url_key}}` wordt vervangen door de eigenschap `url_key` van de categorie
* `{{url_path}}` wordt vervangen door de categorie `url_path`

Met de bovenstaande voorbeeldgegevens ziet een categoriepagina-URL die is opgemaakt met de standaard-URL-indeling eruit als `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html` .

>[!NOTE]
> 
> `url_path` is een samenvoeging van de `url_keys` van de voorouders van een product of categorie en de `url_key` van het product of de categorie gescheiden door `/` slash. Elke `url_key` wordt beschouwd als uniek binnen een bepaalde winkel.

### Winkelspecifieke configuratie {#store-specific-urlformats}

De de categorie en van de productpagina URL formaten die door de _configuratie van de Leverancier van CIF URL_ worden geplaatst kunnen voor elke opslag worden veranderd.

In de Configuratie van CIF, kan een redacteur een alternatief product of een formaat van de categoriepagina URL selecteren. Als daar niets wordt geselecteerd, valt de implementatie terug naar de systeem-brede configuratie.

Het wijzigen van de URL-indeling van een live website kan een negatief effect hebben op het organische verkeer van uw site. Zie [ Beste praktijken ](#best-practices) hieronder en plant zorgvuldig de verandering van het formaat URL vooraf.

![ Url formaten in de Configuratie van CIF ](assets/store-specific-url-formats.png)

>[!NOTE]
>
> De opslag-specifieke configuratie van de formaten URL vereist [ de Componenten 2.6.0 van de Kern van CIF ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) en de recentste versie van de Inhoud van Adobe Experience Manager en Commerce toe:voegen-on.

## URL&#39;s voor productpagina&#39;s die zijn afgestemd op de categorie {#context-aware-pdps}

Omdat het mogelijk is om categoriegegevens te coderen in een product-URL, kunnen producten die in meerdere categorieën zijn ook worden geadresseerd met meerdere product-URL&#39;s.

Met de standaard-URL-indelingen selecteert u een van de mogelijke alternatieven met behulp van het volgende schema:

* als `url_path` door de e-commerce achterste wordt bepaald gebruik het (afgekeurd)
* van `url_rewrites` gebruiken de URL&#39;s die eindigen met de interface van het product `url_key` als alternatief
* van deze alternatieven wordt de versie met de meeste padsegmenten gebruikt
* als er meerdere zijn, neemt u de eerste in de volgorde van de e-commerce-backend

Dit schema selecteert de `url_path` met de meeste voorouders, op basis van de aanname dat een onderliggende categorie specifieker is dan de bovenliggende categorie. Geselecteerde `url_path` wordt beschouwd als _canonical_ en altijd gebruikt als canonieke verbinding op productpagina&#39;s of in de productsitemap.

Wanneer een winkelier echter van een categoriepagina naar een productpagina navigeert, of van de ene productpagina naar de andere gerelateerde productpagina in dezelfde categorie, is het nuttig om de huidige categoriecontext te behouden. In dit geval, zou de `url_path` selectie alternatieven moeten verkiezen die binnen de huidige categoriecontext over de _canonieke_ hierboven beschreven selectie zijn.

Deze eigenschap moet in de _configuratie van de Leverancier van CIF worden toegelaten URL_. Als deze optie is ingeschakeld, worden alternatieven voor de selectiescore hoger weergegeven, wanneer

* ze komen overeen met delen van een bepaalde categorie `url_path` vanaf het begin (wazzy prefix matching)
* of ze komen overeen met de `url_key` -waarde van een bepaalde categorie (exact gedeeltelijke overeenkomst)

Bijvoorbeeld, overweeg de reactie voor a [ productvraag ](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) hieronder. Gezien het volgende:

* de gebruiker bevindt zich op de categoriepagina &quot;New Products / New in Summer 2022&quot;
* de winkel gebruikt de standaard URL-indeling van de categoriepagina

Het alternatief &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot;past twee van de de wegsegmenten van de context van het begin aan. Dat wil zeggen: &quot;nieuwe producten&quot; en &quot;nieuwe-in-zomer-2022&quot;. Als de winkel een URL-indeling van een categoriepagina gebruikt die alleen de categorie `url_key` bevat, wordt hetzelfde alternatief nog steeds geselecteerd als het op een willekeurige plaats aansluit bij de context `url_key` . In beide gevallen wordt de URL van de productpagina gemaakt voor &quot;new-products/new-in-summer-2022/gold-cirque-earrings.html&quot; `url_path` .

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
> Categorie-bewuste product-URL&#39;s vereisen [ CIF Core Components 2.6.0 ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) of nieuwer.

## Specifieke categorie en productpagina&#39;s {#specific-pages}

Het is mogelijk om [ multi-category en productpagina&#39;s ](../authoring/multi-template-usage.md) voor slechts een specifieke ondergroep van categorieën of producten van een catalogus tot stand te brengen.

### Selectiecriteria {#specific-pages-selection}

De selectie van een specifieke categoriepagina is recht vooruit, op basis van de categorieën `url_path` of `url_key` . Overeenkomende subcategorieën worden alleen ondersteund voor URL-indelingen die de volledige categorie `url_path` bevatten. Anders is alleen een exacte overeenkomst van `url_key` mogelijk.

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
> Het selecteren van specifieke productpagina&#39;s door categorie vereist [ de Componenten 2.6.0 van de Kern van CIF ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) of nieuwer.

### Diepe koppeling {#specific-pages-deep-linking}

`UrlProvider` is vooraf geconfigureerd om diepgaande koppelingen te genereren naar specifieke categorie- en productpagina&#39;s op instanties van de auteurslaag. Deze mogelijkheid is handig voor editors die in de modus Voorbeeld door een site bladeren, naar een specifiek product of een bepaalde categoriepagina navigeren en terugschakelen naar de modus Bewerken om de pagina te bewerken.

Op publicatielagen moeten URL&#39;s van cataloguspagina&#39;s echter stabiel blijven om bijvoorbeeld geen winsten te verliezen op beoordelingen van zoekmachines. Vanwege die publicatielaag worden op instanties standaard geen diepgaande koppelingen naar specifieke cataloguspagina&#39;s weergegeven. Om dit gedrag te veranderen, kan de _CIF URL-provider Specifieke paginastrategie_ worden gevormd om altijd specifieke pagina-URL&#39;s te genereren.

### Meerdere cataloguspagina&#39;s {#multiple-product-pages}

Wanneer editors volledige controle willen hebben over de navigatie op hoofdniveau van een site, is het mogelijk dat u niet de hoogste categorieën van een catalogus wilt weergeven met één cataloguspagina. In plaats daarvan kunnen editors meerdere cataloguspagina&#39;s maken, één voor elke categorie van de catalogus die ze in de navigatie op hoofdniveau willen opnemen.

In dat geval kan op elke cataloguspagina een verwijzing staan naar een product- en categoriepagina die specifiek is voor de categorie die voor de cataloguspagina is geconfigureerd. `UrlProvider` gebruikt deze verbindingen om verbindingen voor de pagina&#39;s en de categorieën in de gevormde categorie tot stand te brengen. Om prestatieredenen worden echter alleen de onderliggende elementen van de directe cataloguspagina van de basis-/landingspagina van een site in overweging genomen.

Het wordt aanbevolen dat de product- en categoriepagina&#39;s van een cataloguspagina aan die cataloguspagina worden gekoppeld, anders werken componenten zoals Navigatie of Breadcrumb mogelijk niet correct.

>[!NOTE]
>
> De volledige steun voor veelvoudige cataloguspagina&#39;s vereist [ Componenten 2.10.0 van de Kern van CIF ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.10.0) of nieuwer.

## Aanpassingen {#customization}

### Aangepaste URL-indelingen {#custom-url-format}

Om een formaat van douaneURL te verstrekken, kan een project of [`ProductUrlFormat` uitvoeren ](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) of de [`CategoryUrlFormat` ](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) de dienstinterface en de implementatie registreren als dienst OSGI. Deze implementaties, indien beschikbaar, vervangen de geconfigureerde, vooraf gedefinieerde indeling. Als er veelvoudige geregistreerde implementaties zijn, vervangt één met de hogere de dienstrangschikking degenen met de lagere de dienstrangschikking.

De de formaatimplementaties van douaneURL moeten een paar methodes uitvoeren om een URL van bepaalde parameters te bouwen, en een URL te ontleden om de zelfde parameters respectievelijk terug te keren.

### Combineren met Sling Mappings {#sling-mapping}

Naast `UrlProvider`, is het ook mogelijk om [ het Schuiven Mappings ](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) te vormen om URLs te herschrijven en te verwerken. Het project van Archetype van AEM verstrekt ook [ een voorbeeldconfiguratie ](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) om sommige Wijzen voor haven 4503 (te vormen publiceert) en 80 (Dispatcher).

### Combineren met AEM Dispatcher {#dispatcher}

URL herschrijft kan ook worden bereikt door AEM Dispatcher HTTP-server met `mod_rewrite` module te gebruiken. Het [ Archetype van het Project van AEM ](https://github.com/adobe/aem-project-archetype) verstrekt een referentieAEM Dispatcher config die reeds basis[ herschrijft regels ](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) voor de geproduceerde grootte omvat.

## Aanbevolen procedures {#best-practices}

### Kies de beste URL-indeling {#choose-url-format}

Zoals vermeld voordat u een van de beschikbare standaardindelingen selecteert of zelfs een aangepaste indeling implementeert, is de toepassing in hoge mate afhankelijk van de behoeften en vereisten van een winkel. De volgende suggesties kunnen helpen een goed opgeleid besluit te nemen.

_&#x200B;**gebruik een formaat van productpagina URL dat SKU bevat.**&#x200B;_

De CIF Core-componenten gebruiken de SKU als primaire id in alle componenten. Als de URL-indeling van de productpagina niet de SKU bevat, is een GraphQL-query nodig om deze op te lossen. Deze resolutie kan van invloed zijn op de tijd-aan-eerste-byte. Ook, kan het gewenst zijn, dat de kopers producten door SKU kunnen vinden gebruikend onderzoeksmotoren.

_&#x200B;**gebruik een formaat van productpagina URL dat de categoriecontext bevat.**&#x200B;_

Sommige functies van de CIF URL Provider zijn alleen beschikbaar wanneer u product-URL-indelingen gebruikt die de categoriecontext coderen, zoals de categorie `url_key` of de categorie `url_path` . Zelfs als deze functies niet vereist zijn voor een nieuwe winkel, helpt het gebruik van een van deze URL-indelingen in het begin de migratie-inspanningen in de toekomst te verminderen.

_&#x200B;**Saldo tussen URL lengte en gecodeerde informatie.**&#x200B;_

Afhankelijk van de grootte van de catalogus, met name de grootte en diepte van de categoriestructuur, is het wellicht niet verstandig om de volledige `url_path` categorieën in de URL te coderen. In dat geval kan de lengte van de URL worden verminderd door alleen de categorie `url_key` in plaats daarvan op te nemen. Deze methode ondersteunt de meeste functies die beschikbaar zijn wanneer u de categorie `url_path` gebruikt.

Ook, gebruik [ het Schuiven Toewijzingen ](#sling-mapping) om SKU met het product `url_key` te combineren. In de meeste e-commercesystemen, volgt SKU een bepaald formaat en het scheiden van SKU van `url_key` voor inkomende verzoeken zou gemakkelijk moeten mogelijk zijn. Daarom moet het mogelijk zijn om de URL van een productpagina te herschrijven naar `/p/{{category}}/{{sku}}-{{url_key}}.html` en een categorie-URL naar `/c/{{url_key}}.html` . Het voorvoegsel `/p` en `/c` zijn nog steeds nodig om product- en categoriepagina&#39;s te onderscheiden van andere inhoudspagina&#39;s.

### Migreren naar een nieuwe URL-indeling {#migrate-url-formats}

Veel van de standaard-URL-indelingen zijn op de een of andere manier compatibel met elkaar. Dit betekent dat URL&#39;s die door een van deze indelingen zijn opgemaakt, door een andere kunnen worden geparseerd. Hierdoor kunt u gemakkelijker migreren tussen URL-indelingen.

Aan de andere kant hebben zoekprogramma&#39;s tijd nodig om alle cataloguspagina&#39;s opnieuw in te delen met de nieuwe URL-indeling. Om dit proces te ondersteunen en ook de gebruikerservaring te verbeteren, wordt aanbevolen om omleidingen te bieden die de gebruiker van de oude URL&#39;s naar de nieuwe URL&#39;s sturen.

Eén manier om dat mogelijk te doen, is een werkgebiedomgeving verbinden met de back-end van de e-commerce productie en deze zodanig configureren dat de nieuwe URL-indeling wordt gebruikt. Daarna verkrijg de [ product sitemap die door de producten van CIF wordt geproduceerd de generator van sitemap ](../../overview/seo-and-url-management.md) voor zowel het stadium als het productiemilieu, en gebruik hen om een [ Apache httpd te creëren kaart ](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html) herschrijft. Deze herschrijfkaart kan vervolgens samen met de uitrol van de nieuwe URL-indeling worden geïmplementeerd op de Dispatcher.

## Voorbeeld {#example}

Het [ project van de opslag van de Verwijzing van 0&rbrace; Venia &lbrace;omvat steekproefconfiguraties om het gebruik van douane URLs voor product en categoriepagina&#39;s aan te tonen. ](https://github.com/adobe/aem-cif-guides-venia) Met deze configuratie kan elk project afzonderlijke URL-patronen instellen voor product- en categoriepagina&#39;s op basis van hun SEO-behoeften. Een combinatie van CIF `UrlProvider` en Sling Mappings zoals hierboven beschreven wordt gebruikt.

>[!NOTE]
>
>Deze configuratie moet met het externe domein worden aangepast dat door het project wordt gebruikt. Sling Mappings werkt gebaseerd op hostname en domein. Daarom is deze configuratie onbruikbaar gemaakt door gebrek en moet vóór plaatsing worden toegelaten. Hiervoor wijzigt u de naam van de map Sling Mapping `hostname.adobeaemcloud.com` in `ui.content/src/main/content/jcr_root/etc/map.publish/https` op basis van de gebruikte domeinnaam en schakelt u deze configuratie in door `resource.resolver.map.location="/etc/map.publish"` toe te voegen aan de `JcrResourceResolver` config van het project.

## Aanvullende bronnen {#additional}

* [ de opslag van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia)
* [ het Middel van AEM Afbeelding ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html?lang=nl-NL)
* [ Sling Mappings ](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
