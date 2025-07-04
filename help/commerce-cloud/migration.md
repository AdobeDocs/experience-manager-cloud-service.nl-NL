---
title: Migratie naar de invoegtoepassing AEM Commerce integration framework (CIF)
description: Migreren naar de AEM Commerce integration framework-invoegtoepassing (CIF) vanuit een oude versie
exl-id: 0db03a05-f527-4853-b52f-f113bce929cf
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Migratiehandleiding voor de Experience Manager Cloud Service {#cif-migration}

Deze handleiding helpt u de gebieden te identificeren die u moet bijwerken voor de Experience Manager Cloud Service-migratie.

## CIF-invoegtoepassing

Voor Experience Manager as a Cloud Service is de CIF add-on de enige ondersteunde handelsintegratieoplossing voor Adobe Commerce en handelsoplossingen van derden. De invoegtoepassing CIF wordt automatisch geïmplementeerd voor klanten op Experience Manager as a Cloud Service. Handmatige implementatie is niet nodig. Zie [ Begonnen het worden met AEM Commerce as a Cloud Service ](getting-started.md).

Om projecten te steunen die CIF Adobe opstellen verstrekken [ AEM CIF Core Componenten ](https://github.com/adobe/aem-core-cif-components).

CIF toe:voegen-op is beschikbaar voor AEM 6.5 evenals via het [ portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Het is compatibel en biedt dezelfde functies als de CIF-invoegtoepassing voor Experience Manager as a Cloud Service. Aanpassingen zijn niet vereist.

Klassieke CIF met zijn afhankelijkheden is niet meer beschikbaar. Code die afhankelijk is van deze CIF-versie met behulp van `com.adobe.cq.commerce.api` Java API&#39;s moet worden aangepast aan de CIF-invoegtoepassing en de bijbehorende principes.

De eerder beschikbare CIF-connector kan niet meer worden geïnstalleerd. Code die op deze aansluiting steunt, moet worden aangepast aan de CIF-invoegtoepassing en de bijbehorende beginselen.

## Projectstructuur

Leer de [ Structuur van het Project van AEM ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=nl-NL) en de kenmerken van AEM as a Cloud Service. Pas de projectinstelling aan op de AEM as a Cloud Service-lay-out.
Vergeleken met AEM 6.5-implementaties zijn er hier twee grote verschillen:

* De de cliëntbundel OSGI van GraphQL **moet niet** meer in het project van AEM worden omvat, wordt het opgesteld via CIF toe:voegen-on
* OSGI vormt voor de cliënt van GraphQL en de Grafieke Dienst van Gegevens **moet niet** meer in het project van AEM worden omvat

>[!TIP]
>
>Controle uit het [ project van de Opslag van de Verwijzing van AEM Venia ](https://github.com/adobe/aem-cif-guides-venia) op GitHub. Dit project biedt Maven-profielen voor AEM as a Cloud Service en on-premise implementaties die rekening houden met de verschillende raamvoorwaarden.

## Productcatalogus

Het importeren van productcatalogusgegevens wordt niet meer ondersteund. Het gebruik van de CIF add-on principals product- en catalogusaanvragen vindt u op aanvraag via realtime aanroepen naar een externe handelsoplossing. Ga naar hoofdstuk Integrating om meer over het integreren van een handelsoplossing te leren.

>[!TIP]
>
>Als er geen real-time API&#39;s beschikbaar zijn, moet een externe productcache met API&#39;s worden gebruikt voor de integratie. Voorbeeld [ open-source van Magento ](https://business.adobe.com/products/magento/open-source.html).

## Ervaringen met productcatalogi met AEM-rendering

Als u catalogusblauwdruk gebruikt met Classic CIF, moet u de workflow voor de productcatalogus bijwerken. De invoegtoepassing CIF geeft nu direct ervaringen met productcatalogi weer met AEM-catalogussjablonen. Geen replicatie van productgegevens of productpagina&#39;s meer wordt vereist.

## Niet-cacheable gegevens en winkelinteractie

De cliënt-zijverzoeken voor niet cacheable gegevens en de interactie (bijvoorbeeld, toe:voegen-aan-kart, onderzoek) zouden rechtstreeks naar het handelseindpunt (of handelsoplossing of integratielaag) via CDN/Dispatcher moeten gaan. Verwijder om het even welke vraag waar AEM enkel een volmacht was.
