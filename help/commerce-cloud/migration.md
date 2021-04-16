---
title: Migratie naar de AEM Commerce Integration Framework (CIF)-invoegtoepassing
description: Hoe te om aan het AEM Kader van de Integratie van de Handel (CIF) toe:voegen-on van een oude versie te migreren
translation-type: tm+mt
source-git-commit: cda25048e171f6aacd5349706ad4192965e703db
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 1%

---

# Migratiehandleiding voor de Experience Manager Cloud Service {#cif-migration}

Deze handleiding helpt u de gebieden te identificeren die u voor de migratie van de Experience Manager Cloud Service moet bijwerken.

## CIF-invoegtoepassing

Voor Experience Manager als Cloud Service is de toe:voegen-on CIF de enige gesteunde handelsintegratieoplossing voor de Handel van de Adobe en derdehandel oplossingen. De toe:voegen-op CIF wordt automatisch opgesteld voor klanten op Experience Manager als Cloud Service, geen handplaatsing wordt vereist. Zie [Aan de slag met AEM Handel als Cloud Service](getting-started.md).

Om projecten te steunen die CIF Adobe opstellen verstrekken [AEM de Componenten van de Kern van CIF](https://github.com/adobe/aem-core-cif-components).

De toe:voegen-on CIF is beschikbaar voor AEM 6.5 evenals via [het portaal van de Distributie van de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Het is compatibel en biedt dezelfde functies als de CIF-invoegtoepassing voor Experience Manager als een Cloud Service. Er zijn geen aanpassingen nodig.

Klassieke CIF met zijn gebiedsdelen is niet meer beschikbaar. Code die afhankelijk is van deze CIF-versie met behulp van Java API&#39;s van `com.adobe.cq.commerce.api` moet worden aangepast aan de CIF-invoegtoepassing en de bijbehorende beginselen.

De eerder beschikbare CIF-connector kan niet meer worden geïnstalleerd. Code die op deze aansluiting steunt, moet worden aangepast aan de CIF-invoegtoepassing en de bijbehorende beginselen.

## Projectstructuur

Leer de [AEM Projectstructuur](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) en de kenmerken van AEM als Cloud Service. Pas de projectinstelling aan op de AEM als Cloud Service-indeling.
Vergeleken met AEM 6.5-implementaties zijn er hier twee grote verschillen:

* De GraphQL-client OSGI-bundel **mag niet** meer in het AEM-project worden opgenomen, maar wordt geïmplementeerd via de CIF-invoegtoepassing
* OSGI-configuraties voor GraphQL-client en Graphql Data Service **mogen niet** meer in het AEM-project worden opgenomen

>[!TIP]
>
>Bekijk het [AEM project van de Referentie van Venia ](https://github.com/adobe/aem-cif-guides-venia) op GitHub. Dit project biedt Maven-profielen voor AEM als Cloud Service en on-premise implementaties die rekening houden met de verschillende randvoorwaarden.

## Productcatalogus

Het importeren van productcatalogusgegevens wordt niet meer ondersteund. Het gebruiken van de toe:voegen-op belangrijkste CIF product en catalogusverzoeken zijn op bestelling via vraag in real time aan een externe handelsoplossing. Ga naar hoofdstuk Integrating om meer over het integreren van een handelsoplossing te leren.

>[!TIP]
>
>Als er geen real-time API&#39;s beschikbaar zijn, moet een externe productcache met API&#39;s worden gebruikt voor de integratie. Voorbeeld [Magento open-source](https://magento.com/products/magento-open-source).

## De catalogus van het product ervaart met AEM teruggeven

Als u catalogusblauwdruk gebruikt met Klassieke CIF, moet u de workflow van de productcatalogus bijwerken. De CIF-invoegtoepassing geeft productcataloguservaringen nu direct weer met behulp van AEM catalogussjablonen. Geen replicatie van productgegevens of productpagina&#39;s meer wordt vereist.

## Niet-cacheable gegevens en winkelinteractie

De cliënt-zijverzoeken voor niet cacheable gegevens en interactie (b.v. toe:voegen-aan-kart, onderzoek) zouden rechtstreeks naar het handelseindpunt (of handelsoplossing of integratielaag) via CDN/Dispatcher moeten gaan. Verwijder om het even welke vraag waar AEM enkel een volmacht was.
