---
title: Multi-Store instellen
description: Multi-Store instellen
translation-type: tm+mt
source-git-commit: 94c6abef36b6add300ba3b24855ebf3edf10e1ed
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# Multi-Store instellen {#multi-store}

De AEM CIF Core Componenten kunnen op veelvoudige AEM plaatsstructuren worden gebruikt en de onderliggende cliënt GraphQL implementatie kan met verschillende Magento opslag/opslagmeningen verbinden. Hierdoor kunnen projecten complexe multistore-/multisite-instellingen implementeren.

In een video wordt een overzicht gegeven van de opties voor het integreren van meerdere Magento Store Views met Adobe Experience Manager Sites.

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

AEM functies voor beheer van meerdere sites van Live Copy en Language Copy worden in combinatie met het Commerce Integration Framework gebruikt om sites wereldwijd te beheren in verschillende regio&#39;s en regio&#39;s.

De geadviseerde opstelling is een 1:1 verhouding tussen AEM plaats en de opslagmening van de Magento te gebruiken.

Volg onderstaande stappen om een AEM-site aan te sluiten en CIF Core-componenten te AEM zodat ook deze kunnen worden gekoppeld aan een toegewijde winkelweergave:

## Configuratie {#configuration}

1. Meerdere winkels en winkelweergaven configureren volgens het patroon dat wordt beschreven in [Magento-websites, -winkels en -weergaven](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)

2. Zorg ervoor dat de verbinding tussen AEM &amp; Magento werkt.

3. Creeer een kindconfiguratie van CIF Cloud Service config die deze stappen volgt:

   * Ga in AEM naar Extra -> Algemeen -> Configuratiebrowser
   * Selecteer de basisconfiguratie die u hebt gemaakt
   * Een nieuwe configuratie maken met de stappen die hierboven in punt 2 worden beschreven

   Deze nieuwe configuratie zal als kindconfiguratie van de basis worden gecreeerd. U kunt nu naar Extra -> Algemeen -> Browser van de Configuratie gaan en de configuratiemontages creëren.

4. Wijs de kindconfiguratie aan een AEM plaats toe

   * Ga naar AEM Sites-console
   * Navigeer naar het gebied of de hoofdtaal van uw sitestructuur, bijvoorbeeld /content/venia/us _of_ /content/venia/us/nl voor de voorbeeldpagina van Venia
   * Pagina-eigenschappen selecteren en pagina-eigenschappen openen
   * Selecteer het tabblad Geavanceerd
   * Selecteer in de `Configuration` sectie de configuratie die u stapsgewijs hebt gemaakt

## Aanvullende bronnen

* [Magento-websites, -winkels en -weergaven](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)
* [AEM CIF Core-componenten - Configuratie van meerdere winkels/sites](https://github.com/adobe/aem-core-cif-components/wiki/configuration#multi-store--site-configuration)
* [Beheer van meerdere sites gebruiken](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html)
* [Inhoud opnieuw gebruiken: Beheer van meerdere sites en Live Copy](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/msm.html)
