---
title: JSON-LD-metagegevens
description: Leer hoe u de functie JSON+LD in AEM CIF kunt inschakelen en controleren.
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 5fef97e5c0963529aac6d210cb17326864e6d248
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 1%

---


# JSON-LD-metagegevens {#json-ld}

In deze handleiding wordt uitgelegd hoe u de functie JSON+LD in AEM CIF kunt inschakelen en controleren.

## JSON+LD inschakelen in CIF-configuratie {#enabling}

Door gebrek, **laat JSON+LD** checkbox toe is niet zichtbaar in de configuratie van CIF. Om deze eigenschap toe te laten, moet het project de noodzakelijke configuratie OSGi omvatten, die checkbox om toestaat worden getoond. Met deze configuratie kunnen gebruikers JSON+LD-scriptondersteuning op productpagina&#39;s in- en uitschakelen.
Om **toe te laten JSON+LD** checkbox beschikbaar in de configuratie van CIF, voeg de volgende configuratie OSGi aan uw project toe: &grave;
com.adobe.cq.cif.components.models.JsonLdFeatureEnable&grave;.
Voor verdere details bij het toevoegen van deze configuratie, verwijs naar [ toevoegt configuratie voor json-Ld ](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.cif.components.models.JsonLdFeatureEnable.cfg.json) in de openbare aem-cif-guides-venia bewaarplaats.

Zodra deze configuratie wordt toegevoegd en opgesteld, wordt checkbox zichtbaar in de de configuratiemontages van CIF en hier zijn de stappen om **JSON+LD** toe te laten:

1. Navigeer naar de CIF-configuratie in AEM.
1. Overerving annuleren.
1. Controleer **toelaten JSON+LD** checkbox.
1. Sla de configuratie op.

## JSON+LD controleren op een pagina met productdetails (PDP) {#verify}

Om de stappen te illustreren om JSON+LD te verifiëren, wordt het project van Venia gebruikt als voorbeeld, waar de vereiste configuratie JSON+LD reeds wordt toegevoegd om de eigenschap toe te laten. Hier volgen de volgende stappen:

1. Ga naar uw lokale AEM-exemplaar en open de pagina met productdetails (PDP): http://localhost:4502/editor.html/content/venia/us/en/products/product-page.html
1. Maak een product op de pagina met productdetails (PDP).
1. Schakelaar aan **Mening als Publish** wijze.
1. Open de **Pagina van de Mening Source** in uw browser.
1. Zoeken naar JSON+LD in de paginabron.

Indien correct gevormd, vindt u het manuscript JSON+LD verbonden aan het product dat in de pagina wordt ingespoten.

## Voorbeeld van JSON+LD-structuur voor een product {#sample}

Hieronder is een voorbeeld **JSON+LD** structuur voor Agatha Skirt, die op de PDP pagina in het project van Venia wordt geschreven:

```
<script type="application/ld+json">
{
  "@context": "http://schema.org",
  "@type": "Product",
  "sku": "VSK05",
  "name": "Agatha Skirt",
  "image": "https://mcstaging.catalogservice4commerce.fun/media/catalog/product/cache/926ea6fc2ad48a7202ff4587b6c2768e/v/s/vsk05-pe_main_2.jpg",
  "description": "The Agatha Skirt has a large circumference that lends itself to all sorts of drama...",
  "@id": "product-ef4fa1dc72",
  "offers": [
    {
      "@type": "Offer",
      "sku": "VSK05-KH-S",
      "url": "/content/venia/us/en/products/product-page.html/agatha-skirt.html",
      "priceCurrency": "USD",
      "price": 78.0
    },
    {
      "@type": "Offer",
      "sku": "VSK05-RN-XS",
      "availability": "InStock",
      "priceSpecification": {
        "@type": "UnitPriceSpecification",
        "priceType": "https://schema.org/ListPrice",
        "price": 18.0,
        "priceCurrency": "USD"
      },
      "price": 46.0
    }
  ]
}
</script>
```

## JSON+LD-kenmerken toewijzen aan GraphQL {#mapping}

JSON+LD-kenmerken kunnen worden toegewezen aan GraphQL-query&#39;s in AEM CIF, zodat gestructureerde gegevens dynamisch de productinformatie weerspiegelen die via GraphQL is opgehaald.

### Voorbeeld van producttoewijzing {#example}

| JSON+LD-kenmerk | Magento GraphQL-kenmerk | Vereist (J/N) |
|---------------------------------|-------------------|---|
| sku | sku | N |
| offers.url | Aangepaste logica | N |
| offers.SpecialPricedate | special_to_date | N |
| offers.sku | sku | N |
| offers.priceSpecification.priceCurrency | valuta | Y |
| offers.priceSpecification.price | normal_price | N |
| offers.priceCurrency | valuta | Y |
| offers.price | special_price | Y |
| offers.image | media_galerie.url | N |
| offers.availability | stock_status | N |
| name | name | Y |
| image | media_galerie.url | Y |
| beschrijving | beschrijving | N |
| aggregateRating.reviewCount | review_count | N |
| aggregateRating.ratingValue | rating_summary | N |
| @id | id | N |

Deze toewijzing zorgt ervoor dat het JSON+LD-script dynamisch wordt gevuld op basis van productgegevens die via GraphQL-query&#39;s zijn opgehaald.

Om uw structuur te testen JSON+LD, kunt u de [ Rijke Test van Resultaten gebruiken - de Console van het Onderzoek van Google ](https://search.google.com/test/rich-results/result?id=wtU3LVIEM8H7Aaf5qqK9qw). Dit hulpmiddel verstrekt gedetailleerde terugkoppelt, met inbegrip van of de vereiste attributen aanwezig zijn of ontbreken, en helpt ervoor zorgen dat uw gestructureerde gegevens correct wordt uitgevoerd.
