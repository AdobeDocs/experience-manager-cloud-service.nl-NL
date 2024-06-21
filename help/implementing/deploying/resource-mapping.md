---
title: Brontoewijzing
description: Leer hoe te om omleidingen, ijdelheid URLs, en virtuele gastheren voor AEM te bepalen door middel van middeltoewijzing.
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Configuring
exl-id: 1a1bb23c-d1d1-4e2b-811b-753e6a90a01b
role: Admin
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Brontoewijzing{#resource-mapping}

De afbeelding van het middel wordt gebruikt om omleidingen, ijdelheid URLs, en virtuele gastheren voor AEM te bepalen.

U kunt bijvoorbeeld de volgende toewijzingen gebruiken:

* Alle aanvragen vooraf bevestigen met `/content` zodat de interne structuur verborgen is voor de bezoekers van uw website.
* Definieer een omleiding, zodat alle verzoeken aan de `/content/en/gateway` pagina van uw website wordt omgeleid naar `https://gbiv.com/`.

Eén mogelijke HTTP-toewijzing vooraf bepaalt alle aanvragen aan `localhost:4503` with `/content`. Een dergelijke afbeelding kan worden gebruikt om de interne structuur te verbergen voor bezoekers van de website, voor zover dat mogelijk is:

`localhost:4503/content/we-retail/en/products.html`

Te benaderen via:

`localhost:4503/we-retail/en/products.html`

Als de toewijzing automatisch het voorvoegsel toevoegt `/content` tot `/we-retail/en/products.html`.

>[!CAUTION]
>
>Vanity URLs steunt geen regex patronen.

>[!NOTE]
>
>Zie de documentatie over verkopers, en [Toewijzingen voor resolutie van bronnen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) en [Bronnen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) voor nadere informatie.

## Definities voor weergavetoewijzing {#viewing-mapping-definitions}

De toewijzingen uit twee lijsten die de Resolver van het Middel JCR (top-down) evalueert om een gelijke te vinden.

Deze lijsten kunnen (samen met configuratiegegevens) onder de **JCR ResourceResolver** optie van de Felix-console, bijvoorbeeld `https://<*host*>:<*port*>/system/console/jcrresolver`:

* De configuratie toont de huidige configuratie (zoals die voor [Resolver Apache Sling-resource](/help/overview/seo-and-url-management.md#etc-map)).

* De Test van de configuratie dit laat u een URL of middelweg ingaan. Klikken **Oplossen** of **Kaart** om te bevestigen hoe het systeem de ingang transformeert.

* **Resolver Map-items**
De lijst van ingangen die door de methodes ResourceResolver.resolve worden gebruikt om URLs aan Middelen in kaart te brengen.

* **Toewijzingskaartitems**
De lijst van ingangen die door de methodes ResourceResolver.map worden gebruikt om de Wegen van het Middel aan URLs in kaart te brengen.

De twee lijsten tonen verschillende ingangen, met inbegrip van die ingangen die als gebreken door de toepassingen worden bepaald. Deze ingangen zijn vaak bedoeld om URLs voor de gebruiker te vereenvoudigen.

De lijsten vormen een paar **Patroon**, een reguliere expressie die overeenkomt met de aanvraag, met een **Vervanging** Hiermee definieert u de omleiding die moet worden toegepast.

Bijvoorbeeld:

**Patroon** `^[^/]+/[^/]+/welcome$`

Triggert het volgende:

**Vervanging** `/libs/cq/core/content/welcome.html`.

Een aanvraag doorsturen:

`https://localhost:4503/welcome` &quot;

Aan:

`https://localhost:4503/libs/cq/core/content/welcome.html`

Er worden nieuwe toewijzingsdefinities gemaakt in de repository.

>[!NOTE]
>
>Er zijn vele beschikbare middelen die helpen verklaren hoe te om regelmatige uitdrukkingen te bepalen. Bijvoorbeeld: [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

### Toewijzingsdefinities maken in AEM {#creating-mapping-definitions-in-aem}

In een standaardinstallatie van AEM kunt u de map vinden:

`/etc/map/http`

Deze map is de structuur die wordt gebruikt bij het definiëren van toewijzingen voor het HTTP-protocol. Overige mappen ( `sling:Folder`) kan worden gemaakt onder `/etc/map` voor andere protocollen die u in kaart wilt brengen.

#### Het vormen van Intern Redirect aan /content {#configuring-an-internal-redirect-to-content}

Om de afbeelding tot stand te brengen die om het even welk verzoek aan https://localhost:4503/ met prefixen `/content`:

1. Met CRXDE navigeert u naar `/etc/map/http`.

1. Een knooppunt maken:

   * **Type** `sling:Mapping`
Dit knooppunttype is bedoeld voor dergelijke afbeeldingen, hoewel het gebruik ervan niet verplicht is.

   * **Naam** `localhost_any`

1. Klikken **Alles opslaan**.
1. **Toevoegen** de volgende eigenschappen voor dit knooppunt:

   * **Naam** `sling:match`

      * **Type** `String`

      * **Waarde** `localhost.4503/`

   * **Naam** `sling:internalRedirect`

      * **Type** `String`

      * **Waarde** `/content/`

1. Klikken **Alles opslaan**.

Deze afbeelding behandelt een verzoek zoals:
`localhost:4503/geometrixx/en/products.html`
alsof:
`localhost:4503/content/geometrixx/en/products.html`
is aangevraagd.

>[!NOTE]
>
>Zie [Bronnen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) in de Verschuivende Documentatie voor verdere informatie over de beschikbare hellingseigenschappen en hoe zij kunnen worden gevormd.
>Bijvoorbeeld: [Tekenreeksinterpolatie](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html#string-interpolation-for-etcmap) is nuttig omdat het u een afbeelding laat vormen die per milieuwaarden door omgevingsvariabelen krijgt.

>[!NOTE]
>
>U kunt `/etc/map.publish` om de configuraties voor het publicatiemilieu te houden. Deze configuraties moeten worden gerepliceerd en de nieuwe locatie ( `/etc/map.publish`) geconfigureerd voor de **Toewijzingslocatie** van de [Resolver Apache Sling-resource](/help/overview/seo-and-url-management.md#etc-map) van de publicatieomgeving.
