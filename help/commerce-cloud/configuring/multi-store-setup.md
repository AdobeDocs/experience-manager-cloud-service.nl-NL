---
title: Commerce Multi-Store Setup
description: Leer hoe u meerdere winkelweergaven van Adobe Commerce naar Adobe Experience Manager kunt toewijzen. Hierdoor kunnen projecten ondersteuning bieden voor meertalige en meertalige gebruiksgevallen.
sub-product: Commerce
version: Cloud Service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 3046
thumbnail: 28952.jpg
exl-id: 4385c9e5-2b25-4f95-952f-72349431cf94
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# Commerce Multi-Store Setup {#multi-store}

De Adobe Experience Manager (AEM) CIF Core Components kan op meerdere AEM sitestructuren worden gebruikt en de onderliggende GraphQL client-implementatie kan verbinding maken met verschillende Adobe Commerce-winkels/winkelweergaven. Hierdoor kunnen projecten complexe multistore-/multisite-instellingen implementeren.

In een video wordt een overzicht gegeven van de opties voor het integreren van meerdere Adobe Commerce Store Views met Adobe Experience Manager Sites.

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

AEM functies voor beheer van meerdere sites van Live Copy en Taal Copy worden samen met het Commerce integration framework gebruikt om sites wereldwijd te beheren in verschillende regio&#39;s en regio&#39;s.

De aanbevolen setup bestaat uit het gebruik van een 1:1-relatie tussen de AEM site en de Adobe Commerce-winkelweergave.

Ga als volgt te werk als u een AEM site wilt verbinden en CIF Core Components aan een toegewijde winkelweergave wilt AEM:

## Configuratie {#configuration}

1. Vorm veelvoudige opslag &amp; opslagmeningen volgens het patroon dat in [ wordt beschreven Websites van Adobe Commerce, Opslag &amp; Weergaven ](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html)

2. Controleer of de verbinding tussen AEM en Adobe Commerce werkt.

3. Creeer een kindconfiguratie van CIF Cloud Service config die deze stappen volgt:

   * In AEM gaan naar Hulpmiddelen > Algemeen > [ Browser van de Configuratie ](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)
   * Selecteer de basisconfiguratie die u hebt gemaakt
   * Een configuratie maken met de stappen die hierboven in punt 2 worden beschreven

   Deze nieuwe configuratie wordt gecreeerd als kindconfiguratie van de basis. U kunt nu naar Extra > Algemeen > de Browser van de Configuratie gaan en de configuratiemontages creëren.

   >[!TIP]
   >
   > Commerce-catalogi kunnen worden geadresseerd met behulp van id&#39;s of UID&#39;s. UID&#39;s zijn geïntroduceerd in Adobe Commerce 2.4.2. Schakel deze optie alleen in als uw commerciële backend een GraphQL-schema van versie 2.4.2 of hoger ondersteunt.

4. Wijs de kindconfiguratie aan een AEM plaats toe

   * Ga naar de AEM Sites-console
   * Navigeer naar de hoofdmap van het gebied of de taal van de sitestructuur. Bijvoorbeeld `/content/venia/us _or_ /content/venia/us/en` voor de voorbeeldpagina van Venia
   * Selecteer de pagina en open de pagina-eigenschappen
   * Selecteer het tabblad Geavanceerd
   * Selecteer in de sectie `Configuration` de configuratie die u in stap 3 hebt gemaakt

## Aanvullende bronnen

* [ Websites van Adobe Commerce, Opslag &amp; Mening ](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html)
* [ AEM CIF de Componenten van de Kern - de Configuratie van de Multistore/van de plaats ](https://github.com/adobe/aem-core-cif-components#multi-store--site-configuration)
* [ Gebruikend Manager Van meerdere plaatsen ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html)
* [Inhoud opnieuw gebruiken: Sitebeheer en Live kopiëren](/help/sites-cloud/administering/msm/overview.md)
