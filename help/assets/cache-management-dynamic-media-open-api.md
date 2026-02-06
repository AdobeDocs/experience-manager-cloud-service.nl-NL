---
title: Cachebeheer in dynamische media met open API's
description: Cachebeheer in dynamische media met open API's
role: User
exl-id: 203a5291-edb5-4900-8b0a-32e1ebae5395
source-git-commit: 8c9e59108d28ee02a4609c58bf7a2543783f47e2
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---

# Cachebeheer in dynamische media met open API&#39;s {#cache-management-dynamic-media-open-apis}

Effectief cachebeheer is essentieel voor het leveren van krachtige, schaalbare en up-to-date digitale middelen. In Dynamische Media met Open APIs, bepaalt het geheim voorgeheugenbeheer hoe de inhoud wordt opgeslagen, verfrist, en over de diverse lagen van de leveringspijpleiding geleverd. Antwoorden voor de levering van middelen worden in cache geplaatst op meerdere lagen voor optimale prestaties en snelle levering van inhoud.

Het verlengde caching in Dynamische Media met Open APIs bestaat uit [&#x200B; CDN Laag Caching &#x200B;](#cdn-layer-caching) en [&#x200B; Externe Controle van het Geheime voorgeheugen (BYOCDN &amp; Browser Caching) &#x200B;](#byocdn-browser-caching).

## CDN-laag in cache plaatsen {#cdn-layer-caching}

De leveringsreacties van activa worden in het voorgeheugen ondergebracht bij [&#x200B; Adobe Beheerde CDN &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn#aem-managed-cdn) voor een uitgebreide periode om prestaties te maximaliseren en lading op de oorsprong te minimaliseren. Deze caching wordt volledig beheerd door Adobe om ervoor te zorgen dat eindgebruikers een consistente ervaring van hoge kwaliteit hebben. De duur van de cache is opzettelijk geoptimaliseerd voor prestaties en kan niet door gebruikers worden aangepast om betrouwbaarheid en efficiënte levering van inhoud voor alle klanten te garanderen.

Alle bezorgings-URL&#39;s worden gedurende langere tijd in de cache geplaatst bij de rand (snelst) voor optimale prestaties. De leveringsobjecten in de cache omvatten statische vertoningen, video&#39;s, binaire afbeeldingen van originele afbeeldingen en dynamisch getransformeerde afbeeldingen, zoals elementen waarvan de grootte is gewijzigd of die opnieuw zijn opgemaakt met URL-parameters. <!--The CDN is designed to serve these assets directly from the cache without revalidating them, unless an explicit purge is performed.-->

## External Cache Control (BYOCDN en Browser Caching) {#byocdn-browser-caching}

De antwoorden van de levering van activa omvatten a `Cache-Control` kopbal met een gebrek `max-age` van **10 minuten** voor stroomafwaartse caching lagen. Dit is op douane *toe:voegen-uw-eigen-CDN (BYOCDN) configuraties*, *eindgebruikerbrowsers*, en om het even welke *tussenliggende in het voorgeheugen onderbrengende volmachten* van toepassing, die verenigbare geheim voorgeheugencontrole over de volledige leveringsweg verzekeren.

### De koppen van Cache Control aanpassen {#customizing-cache-control-headers}

Het verhogen van geheim voorgeheugentijd aan levende waarden voorbij de standaardconfiguratie verhoogt de waarschijnlijkheid van het dienen van statische inhoud, die de zichtbaarheid van inhoudsupdates in de eindgebruikerervaring kan vertragen. Als u het gedrag van de geheim voorgeheugencontrole voor uw specifiek gebruiksgeval moet wijzigen, kunt u de regels van douaneCDN vormen om reactiekopballen aan te passen. Op deze manier kunt u op basis van uw vereisten een andere tijdsduur voor de cache instellen. Verwijs naar [&#x200B; Aangepaste CDN van AEM Regels voor de Kopballen van de Reactie &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic).

```
responseTransformations:
    rules:
      - name: cache-asset-delivery
        when:
          allOf:
            - reqProperty: path
              like: '/adobe/assets/urn:aaid:aem:*'
            - reqProperty: tier
              equals: delivery
        actions:
          - type: set
            respHeader: Cache-Control
            value: max-age=300
```

Voor extra hulp of vragen over geheim voorgeheugenbeheer, contacteer [&#x200B; de Steun van Adobe &#x200B;](https://helpx.adobe.com/in/contact.html).

## Active Cache-validatie {#active-cache-invalidation}

Wanneer een middel wordt bijgewerkt, geschrapt, of gewijzigd (om het even welke meta-gegevensveranderingen), maakt de Dynamische Media met Open APIs automatisch elke bijbehorende levering URL op Adobe Beheerde CDN ongeldig. Dit is van toepassing op URL&#39;s die vanity-id&#39;s of aliassen gebruiken, samen met URL&#39;s die transformatieparameters bevatten, zoals breedte, opmaak of kwaliteit. Deze door gebeurtenissen gestuurde validatie zorgt ervoor dat uw gebruikers altijd de meest actuele versie van uw middelen ontvangen zonder handmatige tussenkomst.

### Handmatig leegmaken van cache {#manual-cache-purging}

Als cacheinhoud handmatig moet worden leeggemaakt, kunt u dit doen met de AEM-mogelijkheden voor het ongeldig maken van cache. Voor gedetailleerde instructies op hoe te om specifieke geheime voorgeheugen URLs te zuiveren, verwijs naar [&#x200B; de Invalidatie van het Geheime voorgeheugen van AEM CDN &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-cache-purge#single-purge).

## Veelgestelde vragen{#faq-cache-management}

+++**hoe beïnvloedt het geheim voorgeheugenbeheer bestaande integratie?**

Middel URLs blijft onveranderd, en de kopbal van de geheim voorgeheugencontrole die naar browsers (en andere stroomafwaartse intermediairs) van Adobe Beheerde CDN wordt verzonden blijft 10 minuten met a [`stale-while-revalidate directive` &#x200B;](https://web.dev/articles/stale-while-revalidate#whats_it_mean) zijn, die ervoor zorgen dat stroomafwaartse systemen hun geheime voorgeheugens optimaal blijven gebruiken.

+++

+++**wat een geheim voorgeheugenontruiming teweegbrengt?**

Het leegmaken van de cache wordt automatisch geactiveerd wanneer een element wordt bijgewerkt, gewijzigd, gearchiveerd of verwijderd.

<!--The cache purge triggers automatically in the following circumstances:
 
 - when an asset is updated, modified, or archived.
 - when an asset reaches `ready_for_delivery` state after approval.-->

+++

<!--
+++ **How long does it take for the cache to refresh after updating an asset?**

Any time the asset changes, the cache refreshes usually in *less than 60 seconds*.

+++

<!--
+++ **What happens if the cache purge system fails?**
The following mechanisms can be followed:
 
 - **Automatic retries:** 3 retry attempts with exponential backoff
 - **Monitoring:** Sev-2 alert fires if staleness exceeds 10 minutes
 - **Natural expiry:** Even without purge, cache expires after 10 hours maximum
 - **Manual override:** Engineers can manually purge via CLI tool

+++
-->

+++ **wat alle activa types voor lange levende caching worden gesteund?**

De langdurige caching met gebeurtenisgestuurde actieve cachevalidatie is van toepassing op alle typen elementen in de dynamische media met open API&#39;s, ongeacht het type element of de indeling.

+++

+++ **kan ik uit lang-levend caching voor mijn bewaarplaats opteren?**

Om uit langdurig caching te kiezen, contacteer [&#x200B; Steun van Adobe &#x200B;](https://helpx.adobe.com/in/contact.html) en verstrek de redenering voor uw verzoek.

+++


>[!MORELIKETHIS]
>
>- [&#x200B; integreer de Selector van Activa met diverse toepassingen &#x200B;](/help/assets/integrate-asset-selector.md)
>- [&#x200B; Vanity URLs &#x200B;](/help/assets/vanity-urls.md)
