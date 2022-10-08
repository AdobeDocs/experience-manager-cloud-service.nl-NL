---
title: Migratie naar de AEM Commerce Integration Framework (CIF)-invoegtoepassing
description: Hoe te om aan het AEM Kader van de Integratie van de Handel (CIF) toe:voegen-on van een oude versie te migreren
exl-id: 0db03a05-f527-4853-b52f-f113bce929cf
source-git-commit: ca849bd76e5ac40bc76cf497619a82b238d898fa
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# Migratiehandleiding voor de Experience Manager Cloud Service {#cif-migration}

Deze handleiding helpt u de gebieden te identificeren die u voor de migratie van de Experience Manager Cloud Service moet bijwerken.

## CIF-invoegtoepassing

Voor as a Cloud Service Experience Manager is de toe:voegen-on CIF de enige gesteunde handelsintegratieoplossing voor Adobe Commerce en derdehandelsoplossingen. De CIF-invoegtoepassing wordt automatisch geïmplementeerd voor klanten met as a Cloud Service Experience Manager. Handmatige implementatie is niet nodig. Zie [Aan de slag met AEM as a Cloud Service Handel](getting-started.md).

Om projecten te steunen die CIF Adobe gebruiken verstrekken [AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components).

CIF-invoegtoepassing is beschikbaar voor AEM 6.5 en via de [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Het is compatibel en biedt dezelfde functies als de CIF-invoegtoepassing voor as a Cloud Service Experience Manager - er zijn geen aanpassingen nodig.

Klassieke CIF met zijn gebiedsdelen is niet meer beschikbaar. Code die op deze CIF versie baseert die `com.adobe.cq.commerce.api` Java API&#39;s moeten worden aangepast aan de cif-invoegtoepassing en de bijbehorende beginselen.

De eerder beschikbare CIF-connector kan niet meer worden geïnstalleerd. Code die op deze aansluiting steunt, moet worden aangepast aan de CIF-invoegtoepassing en de bijbehorende beginselen.

## Projectstructuur

Meer informatie over [AEM projectstructuur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) en de kenmerken van AEM as a Cloud Service. Pas de projectinstelling aan aan de AEM as a Cloud Service indeling.
Vergeleken met AEM 6.5-implementaties zijn er hier twee grote verschillen:

* De GraphQL client OSGI-bundel **mogen** worden opgenomen in het AEM-project, wordt het geïmplementeerd via de CIF-invoegtoepassing
* OSGI-configuraties voor GraphQL-client en Graphql Data Service **mogen** worden opgenomen in het AEM-project

>[!TIP]
>
>Kijk uit de [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) project op GitHub. Dit project biedt Maven-profielen voor AEM as a Cloud Service en on-premise implementaties die rekening houden met de verschillende raamvoorwaarden.

## Productcatalogus

Het importeren van productcatalogusgegevens wordt niet meer ondersteund. Het gebruiken van de toe:voegen-op belangrijkste CIF product en catalogusverzoeken zijn op bestelling via vraag in real time aan een externe handelsoplossing. Ga naar hoofdstuk Integrating om meer over het integreren van een handelsoplossing te leren.

>[!TIP]
>
>Als er geen real-time API&#39;s beschikbaar zijn, moet een externe productcache met API&#39;s worden gebruikt voor de integratie. Voorbeeld [Magento opensource](https://business.adobe.com/products/magento/open-source.html).

## De catalogus van het product ervaart met AEM teruggeven

Als u catalogusblauwdruk gebruikt met Klassieke CIF, moet u de workflow van de productcatalogus bijwerken. Met de invoegtoepassing CIF worden de ervaringen met productcatalogi nu direct weergegeven met AEM catalogussjablonen. Geen replicatie van productgegevens of productpagina&#39;s meer wordt vereist.

## Niet-cacheable gegevens en winkelinteractie

De cliënt-zijverzoeken voor niet cacheable gegevens en interactie (bijvoorbeeld, toe:voegen-aan-kart, onderzoek) zouden rechtstreeks naar het handelseindpunt (of handelsoplossing of integratielaag) via CDN/Dispatcher moeten gaan. Verwijder om het even welke vraag waar AEM enkel een volmacht was.
