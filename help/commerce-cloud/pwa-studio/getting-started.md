---
title: Aan de slag met AEM extensie voor PWA Studio
description: Leer hoe te om een project van de Inhoud en van de Handel van de AEM zonder titel met PWA Studio op te stellen.
topics: Commerce
feature: Kader voor integratie in de handel
thumbnail: 37843.jpg
source-git-commit: 2d5207733a0ad5d88a321826727eb02440765faf
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 0%

---


# Aan de slag met AEM extensie voor PWA Studio {#getting-started-pwa}

PWA Studio kan naadloos worden geïntegreerd met de Adobe Commerce via GraphQL en biedt onbeperkte mogelijkheden voor het creëren van innovatieve en boeiende winkels en andere digitale ervaringen.

Inhoudsfragmenten zijn stukken inhoud met een vooraf gedefinieerde structuur waarmee ze zonder kop kunnen worden verbruikt met GraphQL als API in verschillende indelingen (bijvoorbeeld JSON, Markdown) en onafhankelijk kunnen worden gerenderd. Inhoudsfragmenten omvatten alle gegevenstypen en velden die vereist zijn voor GraphQL om ervoor te zorgen dat uw toepassing alleen vraagt wat beschikbaar is en ontvangt wat wordt verwacht. De flexibiliteit die ze bieden in termen van de structuur ervan maakt ze perfect voor gebruik op meerdere locaties en via meerdere kanalen.

U kunt de gewenste structuur eenvoudig ontwerpen met de Content Fragment Model Editor in Adobe Experience Manager. De belangrijkste uitdaging aan het integreren van de Fragments van de Inhoud van Adobe Experience Manager (of om het even welke andere gegevens) met uw toepassing van de PWA Studio is het halen van gegevens van veelvoudige eindpunten GraphQL. Dit is omdat uit de doos, PWA Studio met één enkel eindpunt van GraphQL van de Handel van Adobe werkt.

## Architectuur {#architecture}

![PWA zonder kop](/help/commerce-cloud/assets/PWA-Studio_Architecture.png)

## PWA Studio instellen {#setup-pwa}

Volg de Adobe Commerce [PWA Studio documentatie](https://magento.github.io/pwa-studio/tutorials/) om uw PWA Studio app te installeren.

Om PWA Studio met het eindpunt GraphQL van AEM te verbinden, kunt u [AEM Uitbreiding voor PWA Studio](https://github.com/adobe/aem-pwa-studio-extensions) gebruiken.

1. Ontdek de opslagplaats

1. Voeg de extensie toe als ontwikkelafhankelijkheid in de toepassing PWA Studio.

   ```javascript
   yarn add --dev file:{path-to-extension}/extension
   ```

1. Voeg de omslag van de Verbinding van Apollo aan uw toepassing van de PWA Studio toe. Breng de volgende wijzigingen aan in pwa-root/src/index.js:

   ```javascript
     import { linkWrapper } from '@adobe/pwa-studio-aem-cfm-blog-extension';
   
   // ...
   
   <Adapter apiBase={apiBase} apollo={{ link: linkWrapper(apolloLink) }} store={store}>
   ```

   U kunt meer details over de aanpassing van de Cliënt van Apollo in [linkWrapper.js](https://github.com/adobe/aem-pwa-studio-extensions/blob/master/aem-cfm-blog-extension/extension/src/linkWrapper.js) vinden.

1. Als u de navigatiecomponent wilt uitbreiden met een blogbericht, voegt u de volgende aanpassingen toe aan pwa-root/local-intercept.js:

   ```javascript
   const addBlogToNavigation = require('@adobe/pwa-studio-aem-cfm-blog-extension/src/addBlogToNavigation');
   
   function localIntercept(targets) {
       addBlogToNavigation(targets);
   }    
   ```

   U kunt meer details over de aanpassing van de component van de Navigatie in [addBlogToNavigation.js](https://github.com/adobe/aem-pwa-studio-extensions/blob/master/aem-cfm-blog-extension/extension/src/addBlogToNavigation.js) en in de [documentatie van het Kader van de Rekbaarheid](https://magento.github.io/pwa-studio/pwa-buildpack/extensibility-framework/) van PWA Studio vinden.

1. De Apollo-client verwacht het eindpunt AEM GraphQL op <https://pwa-studio/endpoint.js>. Om het eindpunt aan deze plaats in kaart te brengen, zult u de configuratie UPWARD van uw toepassing van de PWA Studio moeten aanpassen:
a. Voeg de variabele AEM_CFM_GRAPHQL aan pwa-root/.env toe en pas het aan punt aan uw AEM eindpunt van de Fragmenten van de Inhoud GraphQL aan.

   Voorbeeld: AEM_CFM_GRAPHQL=<http://localhost:4503/content/graphql/global>

   b. Voeg een volmachtsoplosser aan uw configuratie UPWARD toe. Een voorbeeld-UPWARD-configuratie kan er als volgt uitzien:

```json
   response:
     resolver: conditional
     when:
       - matches: request.url.pathname
         pattern: ^/endpoint.json(/|$)
         use: aemProxy
     default: veniaResponse

   aemProxy:
     resolver: proxy
     target: env.AEM_CFM_GRAPHQL
     ignoreSSLErrors: true

   status: response.status
   headers: response.headers
   body: response.body
```

## AEM instellen {#setup-aem}

Volg de documentatie van de Fragmenten van de Inhoud van de AEM aan opstelling een eindpunt GraphQL voor uw AEM project. Bovendien, in uw AEM project, voeg de volgende configuraties toe om uw toepassing van de PWA Studio toe te staan om tot het eindpunt toegang te hebben GraphQL:

* Beleid voor het delen van bronnen tussen verschillende Adobe-oorsprong (com.adobe.granite.cors.impl.CORSPopolicyImpl)

   Stel de toegestane oorspronkelijke eigenschap in op de volledige hostnaam van de PWA-toepassing.

   Voorbeeld:  <https://pwa-studio-test-vflyn.local.pwadev:9366>

* Apache Sling Referrer-filter (org.apache.sling.security.impl.ReferrerFilter.cfg.json)

   Stel de eigenschap allow.hosts in op de hostnaam van uw PWA-toepassing.

   Voorbeeld: pwa-studio-test-vflyn.local.pwadev

Hier vindt u volledige voorbeelden van beide configuraties: <https://github.com/adobe/aem-pwa-studio-extensions/tree/master/aem-cfm-blog-extension/aem/config/src/main/content/jcr_root/apps/blog-demo/config>.

Om het eindpunt te tonen GraphQL, hebben wij sommige modellen en gegevens van het Fragment van de steekproefinhoud via een inhoudspakket voorbereid. Deze werken goed samen met de React Componenten die van de uitbreiding van de PWA Studio worden voorzien.

## Het gebruik {#how-to-use}

Deze uitbreiding wordt beschouwd als een voorbeeldimplementatie van hoe te om een toepassing van de PWA Studio met AEM te verbinden om inhoud via GraphQL terug te winnen en terug te geven.

Afhankelijk van uw gebruiksgeval, wilt u uw eigen modellen van het Fragment van de douaneInhoud tot stand brengen die in een douaneschema GraphQL resulteren dat dan door uw eigen componenten van het Antwoord kan worden verbruikt.

Productie-instellingen kunnen in meerdere opzichten verschillen.

* U kunt één enkel gefedereerd eindpunt hebben GraphQL dat AEM en Magento gegevens GraphQL in plaats van het aanpassen van cliënt van Apollo combineert.
* Uw toepassing van de PWA Studio kon de AEM eindpunt URL GraphQL, zonder een volmacht met UPWARD direct gebruiken. De proxy kan ook naar een andere laag worden verplaatst (bijvoorbeeld CDN).
* Welke benadering het beste voor u ook past hangt sterk af van hoe u de toepassing van de PWA Studio aan het eind - gebruiker levert.

Deze extensie bevat twee voorbeelden.

### Blog {#blog}

Blogberichten weergeven op basis van bepaalde modellen van inhoudsfragmenten. Bovendien bevat het voorbeelden van hoe te om de cliënt van Apollo te vormen om met het AEM eindpunt te werken GraphQL en hoe te om de navigatiecomponent in PWA Studio uit te breiden. Zie [GitHub](https://github.com/adobe/aem-pwa-studio-extensions/tree/master/aem-cfm-blog-extension) voor meer details.

### PDP-verrijking {#pdp-enrichment}

Laat marketers toe om PDPs met extra inhoud gemakkelijk te verrijken die als Fragments van de Inhoud wordt beheerd.  Zie [GitHub](https://github.com/adobe/aem-pwa-studio-extensions/tree/master/aem-cif-product-page-extension) voor meer details.
