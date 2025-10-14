---
title: Inhoudsfragmenten gebruiken met Adobe Journey Optimizer
description: Leer hoe u Content Fragments kunt integreren en gebruiken met Adobe Journey Optimizer.
feature: Content Fragments
role: User, Developer, Architect
solution: Experience Manager Sites
exl-id: 4090ee41-80f1-4389-8961-e4af891f01ff
source-git-commit: 0fd7b2633488ceb14d34b1978a91a3a830d8762a
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 2%

---

# Inhoudsfragmenten met Adobe Journey Optimizer {#content-fragments-with-journey-optimizer}

[&#x200B; Adobe Journey Optimizer &#x200B;](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/get-started/get-started) helpt u verbonden, contextafhankelijke, en gepersonaliseerde ervaringen aan uw klanten leveren. Door Adobe Experience Manager (AEM) as a Cloud Service te integreren met Adobe Journey Optimizer (AJO), kunt u AEM-inhoud hergebruiken in uw inkomende AJO-kanalen en in uw uitgaande AJO-kanalen, zoals web, SMS, e-mail en andere kanalen.

U kunt bijvoorbeeld:

* neem naadloos uw [&#x200B; Fragmenten van de Inhoud van AEM &#x200B;](/help/sites-cloud/administering/content-fragments/overview.md) in uw [&#x200B; e-mailinhoud van Journey Optimizer &#x200B;](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/channels/email/email-landing-page) op
* rechtstreeks vanuit AEM een voorbeeld van de AJO-ervaring bekijken

De verbinding tussen Content Fragments en AJO vereenvoudigt het proces van toegang tot en hefboomwerking van de inhoud van AEM, toelatend de verwezenlijking van gepersonaliseerde en dynamische campagnes en reizen.

Voor meer informatie start u met de documentatie van AJO:

* [&#x200B; Gebruikend Inhoudsfragmenten in AJO &#x200B;](https://experienceleague.adobe.com/docs/journey-optimizer/using/integrations/aem-fragments.html?lang=nl-NL#integrations)
* [&#x200B; de Aanbiedingen van AJO van de Integratie met het Fragment van de Inhoud &#x200B;](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/decisioning/offer-decisioning/managing-offers-in-the-offer-library/configure-offers/add-representations#urls)

## Dispatcher-configuratie {#dispatcher-configuration}

Om AJO toe te staan om tot de Fragmenten van de Inhoud van AEM door het [&#x200B; Beheer API van het Fragment van de Inhoud toegang te hebben &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/), moet u Dispatcher vormen:

* In `dispatcher/src/conf.dispatcher.d/filters/filters.any`:

* Toevoegen:

  ```xml
  # Allow Content Fragments API requests, required for integration with AJO 
  /200 {/type "allow" /url "/adobe/sites/cf/*" }
  ```

## Aanvullende informatie {#further-information}

Zie voor meer informatie:

* De [&#x200B; uitbreiding van de Verwijzingen van AJO Externe &#x200B;](/help/sites-cloud/administering/content-fragments/extension-content-fragment-ajo-external-references.md)
