---
title: Commerce Multi-Store Setup
description: Leer hoe u meerdere winkelweergaven van Adobe Commerce naar Adobe Experience Manager kunt toewijzen. Hierdoor kunnen projecten ondersteuning bieden voor meertalige en meertalige gebruiksgevallen.
sub-product: Commerce
version: Experience Manager as a Cloud Service
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 3046
thumbnail: 28952.jpg
exl-id: 4385c9e5-2b25-4f95-952f-72349431cf94
role: Admin
source-git-commit: 1bd36e584d956c5ae8da7b1d618e155da86a74f5
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# Commerce Multi-Store Setup {#multi-store}

De Adobe Experience Manager (AEM) CIF Core Components kan op meerdere AEM-sitestructuren worden gebruikt en de onderliggende GraphQL-clientimplementatie kan verbinding maken met verschillende Adobe Commerce-winkels/winkelweergaven. Hierdoor kunnen projecten complexe multistore-/multisite-instellingen implementeren.

In een video wordt een overzicht gegeven van de opties voor het integreren van meerdere Adobe Commerce Store Views met Adobe Experience Manager Sites.

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

De AEM Multi-Site Management-functies van Live Copy en Language Copy worden samen met de Commerce integration framework gebruikt voor het wereldwijd beheren van sites in verschillende regio&#39;s en regio&#39;s.

De aanbevolen setup bestaat uit het gebruik van een 1:1-relatie tussen de AEM-site en de Adobe Commerce-winkelweergave.

Ga als volgt te werk om een AEM-site en AEM CIF Core Components te verbinden met een toegewijde winkelweergave:

## Configuratie {#configuration}

1. Vorm veelvoudige opslag &amp; opslagmeningen volgens het patroon dat in [ wordt beschreven Websites van Adobe Commerce, Opslag &amp; Weergaven ](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=nl-NL)

2. Controleer of de verbinding tussen AEM en Adobe Commerce werkt.

3. Creeer een kindconfiguratie van CIF Cloud Service config die deze stappen volgt:

   * In AEM gaat naar Hulpmiddelen > Algemeen > [ Browser van de Configuratie ](/help/implementing/developing/introduction/configurations.md#using-configuration-browser)
   * Selecteer de basisconfiguratie die u hebt gemaakt
   * Een configuratie maken met de stappen die hierboven in punt 2 worden beschreven

   Deze nieuwe configuratie wordt gecreeerd als kindconfiguratie van de basis. U kunt nu naar Extra > Algemeen > de Browser van de Configuratie gaan en de configuratiemontages creëren.

   >[!TIP]
   >
   > Commerce-catalogi kunnen worden geadresseerd met behulp van id&#39;s of UID&#39;s. UID&#39;s zijn geïntroduceerd in Adobe Commerce 2.4.2. Schakel deze optie alleen in als uw commerciële backend een GraphQL-schema van versie 2.4.2 of hoger ondersteunt.

4. Wijs de kindconfiguratie aan een plaats van AEM toe

   * Ga naar de AEM Sites-console
   * Navigeer naar de hoofdmap van het gebied of de taal van de sitestructuur. Bijvoorbeeld `/content/venia/us _or_ /content/venia/us/en` voor de voorbeeldpagina van Venia
   * Selecteer de pagina en open de pagina-eigenschappen
   * Selecteer het tabblad Geavanceerd
   * Selecteer in de sectie `Configuration` de configuratie die u in stap 3 hebt gemaakt

## Aanvullende bronnen

* [ Websites van Adobe Commerce, Opslag &amp; Mening ](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=nl-NL)
* [ de Componenten van de Kern van AEM CIF - Multistore/plaatconfiguratie ](https://github.com/adobe/aem-core-cif-components#multi-store--site-configuration)
* [ Gebruikend Manager Van meerdere plaatsen ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html?lang=nl-NL)
* [Inhoud opnieuw gebruiken: Sitebeheer en Live kopiëren](/help/sites-cloud/administering/msm/overview.md)
