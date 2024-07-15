---
title: Migratie naar het AEM Commerce integration framework (CIF)
description: Hoe te om aan het Commerce integration framework van het AEM (CIF) toe:voegen-aan van een oude versie te migreren
exl-id: 0db03a05-f527-4853-b52f-f113bce929cf
feature: Commerce Integration Framework
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Migratiehandleiding voor de Experience Manager Cloud Service {#cif-migration}

Deze handleiding helpt u de gebieden te identificeren die u voor de migratie van de Experience Manager Cloud Service moet bijwerken.

## CIF

Voor Experience Manager as a Cloud Service is de CIF toe:voegen-on de enige gesteunde handelsintegratieoplossing voor Adobe Commerce en derdehandel oplossingen. De CIF invoegtoepassing wordt automatisch geïmplementeerd voor klanten met een as a Cloud Service Experience Manager. Handmatige implementatie is niet nodig. Zie [ Begonnen het worden met AEM as a Cloud Service van Commerce ](getting-started.md).

Om projecten te steunen die CIF Adobe opstellen verstrekken [ AEM CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components).

CIF toe:voegen-op is beschikbaar voor AEM 6.5 evenals via het [ portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Het is compatibel en biedt dezelfde functies als de CIF invoegtoepassing voor Experience Manager as a Cloud Service - er zijn geen aanpassingen nodig.

Klassieke CIF met zijn gebiedsdelen is niet meer beschikbaar. Code die afhankelijk is van deze CIF versie met behulp van `com.adobe.cq.commerce.api` Java API&#39;s moet worden aangepast aan de CIF invoegtoepassing en de bijbehorende beginselen.

De eerder beschikbare CIF kan niet meer worden geïnstalleerd. Code die op deze aansluiting steunt, moet worden aangepast aan de CIF en de beginselen ervan.

## Projectstructuur

Leer de [ AEM Structuur van het Project ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) en de kenmerken van AEM as a Cloud Service. Pas de projectinstelling aan op de AEM as a Cloud Service-lay-out.
Vergeleken met AEM 6.5-implementaties zijn er hier twee grote verschillen:

* De de cliëntbundel OSGI van GraphQL **moet niet** in het AEM project meer worden omvat, wordt het opgesteld via CIF toe:voegen-aan
* OSGI vormt voor de cliënt van GraphQL en de Grafieke Dienst van Gegevens **moet niet** meer in het AEM project worden omvat

>[!TIP]
>
>Controle uit het [ AEM project van de Opslag van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia) op GitHub. Dit project biedt Maven-profielen voor AEM as a Cloud Service en on-premise implementaties die rekening houden met de verschillende raamvoorwaarden.

## Productcatalogus

Het importeren van productcatalogusgegevens wordt niet meer ondersteund. Het gebruiken van de CIF toe:voegen-op belangrijkste producten product &amp; catalogusverzoeken zijn op bestelling via vraag in real time aan een externe handelsoplossing. Ga naar hoofdstuk Integrating om meer over het integreren van een handelsoplossing te leren.

>[!TIP]
>
>Als er geen real-time API&#39;s beschikbaar zijn, moet een externe productcache met API&#39;s worden gebruikt voor de integratie. Voorbeeld [ Magento open-source ](https://business.adobe.com/products/magento/open-source.html).

## De catalogus van het product ervaart met AEM teruggeven

Als u catalogusblauwdruk gebruikt in combinatie met klassieke CIF, moet u de workflow van de productcatalogus bijwerken. De CIF invoegtoepassing geeft nu direct ervaringen met productcatalogi weer met AEM catalogussjablonen. Geen replicatie van productgegevens of productpagina&#39;s meer wordt vereist.

## Niet-cacheable gegevens en winkelinteractie

De cliënt-zijverzoeken voor niet cacheable gegevens en de interactie (bijvoorbeeld, toe:voegen-aan-kart, onderzoek) zouden rechtstreeks naar het handelseindpunt (of handelsoplossing of integratielaag) via CDN/Dispatcher moeten gaan. Verwijder om het even welke vraag waar AEM enkel een volmacht was.
