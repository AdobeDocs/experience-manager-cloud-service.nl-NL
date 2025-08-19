---
title: AEM-CIF-kerncomponenten en Adobe Experience Platform-integratie
description: Leer hoe u via de CIF-Experience Platform-connector gegevens over storefront-gebeurtenissen van een door AEM gerenderde productpagina naar de Experience Platform verzendt.
sub-product: Commerce
version: Experience Manager as a Cloud Service
activity: setup
feature: Commerce Integration Framework
topic: Commerce
role: Architect, Developer
level: Beginner
kt: 10834
thumbnail: 346811.jpeg
exl-id: 30bb9b2c-5f00-488e-ad5c-9af7cd2c4735
index: false
source-git-commit: 80bd8da1531e009509e29e2433a7cbc8dfe58e60
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 0%

---


# AEM-CIF-kerncomponenten en Adobe Experience Platform-integratie {#aem-cif-aep-integration}

De [ Commerce integration framework (CIF) ](https://github.com/adobe/aem-core-cif-components) kerncomponenten verstrekken naadloze integratie met [ Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-overview.html) om storefront gebeurtenissen en hun gegevens van cliënt-zijinteractie zoals __toe te voegen aan wagentje__.

Het [ project van de Componenten van de Kern van AEM CIF ](https://github.com/adobe/aem-core-cif-components) verstrekt een bibliotheek van JavaScript genoemd [ schakelaar van Adobe Experience Platform voor Adobe Commerce ](https://github.com/adobe/aem-core-cif-components/tree/master/extensions/experience-platform-connector) om gebeurtenisgegevens van uw Commerce storefront te verzamelen. Deze gebeurtenisgegevens worden naar de Experience Platform verzonden waar ze worden gebruikt in andere Adobe Experience Cloud-producten, zoals Adobe Analytics en Adobe Target, om een profiel van 360 graden te maken dat een klantentraject bestrijkt. Door Commerce-gegevens aan te sluiten op andere producten in de Adobe Experience Cloud, kunt u taken uitvoeren zoals het gebruikersgedrag op uw site analyseren, AB-tests uitvoeren en gepersonaliseerde campagnes maken.

Leer meer over de [ reeks van de Gegevensverzameling van 0&rbrace; Experience Platform van technologieën die u toestaan om gegevens van de klantenervaring van cliënt-zijbronnen te verzamelen.](https://experienceleague.adobe.com/docs/experience-platform/collection/home.html)

## `addToCart` -gebeurtenisgegevens verzenden naar Experience Platform {#send-addtocart-to-aep}

In de volgende stappen wordt getoond hoe u de gebeurtenisgegevens van `addToCart` van door AEM gerenderde productpagina&#39;s naar de Experience Platform verzendt via de CIF - Experience Platform Connector. Met de Adobe Experience Platform Debugger-browserextensie kunt u de verzonden gegevens testen en bekijken.

![ de gebeurtenisgegevens van de Overzicht addToCart in Adobe Experience Platform Debugger ](../assets/aep-integration/EventData-AEM-AEP.png)

## Vereisten {#prerequisites}

Gebruik een lokale ontwikkelomgeving om deze demo te voltooien. Dit omvat een lopende instantie van AEM die wordt gevormd en met een instantie van Adobe Commerce verbonden. Herzie de vereisten en de stappen voor [ vestiging lokale ontwikkeling met AEM as a Cloud Service SDK.](/help/commerce-cloud/cif-storefront/develop.md)

U hebt ook toegang tot [ Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-ui/ui-guide.html) en toestemmingen nodig om het schema, de dataset, en de gegevensstromen voor gegevensinzameling tot stand te brengen. Voor meer informatie, zie [ beheer van de Toestemming.](https://experienceleague.adobe.com/docs/experience-platform/collection/permissions.html)

## AEM Commerce as a Cloud Service instellen {#aem-setup}

Om een werkende __AEM Commerce as a Cloud Service__ lokaal milieu met de noodzakelijke code en config te hebben, voltooi de volgende stappen.

### Lokale instellingen

Volg de [ Lokale 1&rbrace; stappen van de Opstelling &lbrace;zodat kunt u het werkende milieu van AEM as a Cloud Service hebben.](/help/commerce-cloud/cif-storefront/develop.md#local-setup)

### Projectinstelling

Volg de [ stappen van de Archetype van het Project van 0&rbrace; AEM &lbrace;zodat kunt u een gloednieuw project van AEM Commerce (CIF) tot stand brengen.](/help/commerce-cloud/cif-storefront/develop.md#project)

>[!TIP]
>
>In het volgende voorbeeld krijgt het AEM Commerce-project de naam: `My Demo Storefront` , maar u kunt uw eigen projectnaam kiezen.

![ AEM Commerce Project ](../assets/aep-integration/aem-project-with-commerce.png)


Bouw en stel het gecreeerde project van AEM Commerce aan de lokale SDK van AEM door het volgende bevel van de wortelfolder van het project in werking te stellen.

```bash
$ mvn clean install -PautoInstallSinglePackage
```

De lokaal opgestelde `My Demo StoreFront` handelsplaats met standaardcode en inhoud kijkt als het volgende:

![ Standaard AEM Commerce Plaats ](../assets/aep-integration/demo-aem-storefront.png)

### Afhankelijkheden van Peregrine- en CIF-AEP-connectors installeren

Als u de gebeurtenisgegevens van de categorie- en productpagina&#39;s van deze AEM Commerce-site wilt verzamelen en verzenden, installeert u de `npm` -sleutelpakketten in de module `ui.frontend` van het AEM Commerce-project.

Navigeer naar de module `ui.frontend` en installeer de vereiste pakketten door de volgende opdrachten vanaf de opdrachtregel uit te voeren.

```bash
npm i --save lodash.get@^4.4.2 lodash.set@^4.3.2
npm i --save apollo-cache-persist@^0.1.1
npm i --save redux-thunk@~2.3.0
npm i --save @adobe/apollo-link-mutation-queue@~1.1.0
npm i --save @magento/peregrine@~12.5.0
npm i --save @adobe/aem-core-cif-react-components --force
npm i --save-dev @magento/babel-preset-peregrine@~1.2.1
npm i --save @adobe/aem-core-cif-experience-platform-connector --force
```

>[!IMPORTANT]
>
>Het `--force` argument wordt vereist soms aangezien [ PWA Studio ](https://developer.adobe.com/commerce/pwa-studio/) met de gesteunde peer gebiedsdelen restrictief is. Gewoonlijk zou dit geen problemen mogen veroorzaken.


### Maven configureren voor gebruik van argument `--force`

Als onderdeel van het Maven-ontwikkelproces wordt de npm clean install (using `npm ci` ) geactiveerd. Hiervoor is ook het argument `--force` vereist.

Navigeer naar het basis-POM-bestand van het project `pom.xml` en zoek het `<id>npm ci</id>` -uitvoeringsblok. Werk het blok bij zodat het als het volgende kijkt:

```xml
<execution>
    <id>npm ci</id>
    <goals>
    <goal>npm</goal>
    </goals>
    <configuration>
    <arguments>ci --force</arguments>
    </configuration>
</execution>
```

### Babel-configuratieopmaak wijzigen

Schakel van de standaard `.babelrc` bestands relatieve configuratie bestandsindeling naar `babel.config.js` indeling. Dit is een configuratieformaat voor het hele project en staat de stop-ins en de voorinstellingen toe om op `node_module` met grotere controle worden toegepast.

1. Navigeer naar de module `ui.frontend` en verwijder het bestaande `.babelrc` -bestand.

1. Maak een `babel.config.js` -bestand waarin de `peregrine` -voorinstelling wordt gebruikt.

   ```javascript
   const peregrine = require('@magento/babel-preset-peregrine');
   
   module.exports = (api, opts = {}) => {
       const config = {
           ...peregrine(api, opts),
           sourceType: 'unambiguous'
       } 
   
       config.plugins = config.plugins.filter(plugin => plugin !== 'react-refresh/babel');
   
       return config;
   }
   ```

### Webpack configureren voor gebruik van Babel

Bewerk het `babel-loader` -bestand als u de JavaScript-bestanden wilt omzetten met behulp van Babel loader ( `webpack.common.js` ) en webpack.

Navigeer naar de module `ui.frontend` en werk het bestand `webpack.common.js` bij, zodat u de volgende regel binnen de waarde van de eigenschap `module` kunt gebruiken:

```javascript
{
    test: /\.jsx?$/,
    exclude: /node_modules\/(?!@magento\/)/,
    loader: 'babel-loader'
}
```

### Apollo-client configureren

De [ Cliënt van Apollo ](https://www.apollographql.com/docs/react/) wordt gebruikt om zowel lokale als verre gegevens met GraphQL te beheren. De resultaten van GraphQL-query&#39;s worden ook opgeslagen in een lokale, genormaliseerde cache in het geheugen.

[`InMemoryCache` ](https://www.apollographql.com/docs/react/caching/cache-configuration/) werken effectief, hebt u een `possibleTypes.js` dossier nodig. Om dit dossier te produceren, zie [ het Genereren van possibleTypes automatisch.](https://www.apollographql.com/docs/react/data/fragments/#generating-possibletypes-automatically)

Ook, zie de [ de verwijzingsimplementatie van PWA Studio ](https://github.com/magento/pwa-studio/blob/1977f38305ff6c0e2b23a9da7beb0b2f69758bed/packages/pwa-buildpack/lib/Utilities/graphQL.js#L106-L120) en een voorbeeld van a [`possibleTypes.js`](../assets/aep-integration/possibleTypes.js) dossier.

1. Ga naar de module `ui.frontend` en sla het bestand op als `./src/main/possibleTypes.js`

1. Werk de sectie `webpack.common.js` file `DefinePlugin` bij zodat u de vereiste statische variabelen tijdens bouwtijd kunt vervangen.

   ```javascript
   const { DefinePlugin } = require('webpack');
   const { POSSIBLE_TYPES } = require('./src/main/possibleTypes');
   
   ...
   
   plugins: [
       ...
       new DefinePlugin({
           'process.env.USE_STORE_CODE_IN_URL': false,
           POSSIBLE_TYPES
       })
   ]
   ```

### Basiscomponenten van Peregrine en CIF initialiseren

Als u de op React gebaseerde Peregrine- en CIF-kerncomponenten wilt initialiseren, maakt u de vereiste configuratie- en JavaScript-bestanden.

1. Navigeer naar de module `ui.frontend` en maak de volgende map: `src/main/webpack/components/commerce/App`

1. Maak een `config.js` -bestand met de volgende inhoud:

   ```javascript
   // get and parse the CIF store configuration from the <head>
   const storeConfigEl = document.querySelector('meta[name="store-config"]');
   const storeConfig = storeConfigEl ? JSON.parse(storeConfigEl.content) : {};
   
   // the following global variables are needed for some of the peregrine features
   window.STORE_VIEW_CODE = storeConfig.storeView || 'default';
   window.AVAILABLE_STORE_VIEWS = [
       {
           code: window.STORE_VIEW_CODE,
           base_currency_code: 'USD',
           default_display_currency_code: 'USD',
           id: 1,
           locale: 'en',
           secure_base_media_url: '',
           store_name: 'My Demo StoreFront'
       }
   ];
   window.STORE_NAME = window.STORE_VIEW_CODE;
   window.DEFAULT_COUNTRY_CODE = 'en';
   
   export default {
       storeView: window.STORE_VIEW_CODE,
       graphqlEndpoint: storeConfig.graphqlEndpoint,
       // Can be GET or POST. When selecting GET, this applies to cache-able GraphQL query requests only.
       // Mutations will always be executed as POST requests.
       graphqlMethod: storeConfig.graphqlMethod,
       headers: storeConfig.headers,
   
       mountingPoints: {
           // TODO: define the application specific mount points as they may be used by <Portal> and <PortalPlacer>
       },
       pagePaths: {
           // TODO: define the application specific paths/urls as they may be used by the components
           baseUrl: storeConfig.storeRootUrl
       },
       eventsCollector: {
           eventForwarding: {
               acds: true,
               aep: false,
           }
       }
   };
   ```

   >[!IMPORTANT]
   >
   >Terwijl u reeds met het [`config.js` ](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.frontend/src/main/components/App/config.js) dossier van __AEM Guides - het Project van CIF Venia__ zou kunnen vertrouwd zijn, zijn er een paar veranderingen u aan dit dossier moet aanbrengen. Eerst, herzie om het even welke __TODO__ commentaren. Zoek vervolgens binnen de eigenschap `eventsCollector` het object `eventsCollector > aep` en werk de eigenschappen `orgId` en `datastreamId` bij naar de juiste waarden. [ leer meer.](#add-aep-values-to-aem)

1. Maak een `App.js` -bestand met de volgende inhoud. Dit bestand lijkt op een typisch React-startpuntbestand en bevat React en aangepaste haken en React-contextgebruik om de Experience Platform-integratie te vergemakkelijken.

   ```javascript
   import config from './config';
   
   import React, { useEffect } from 'react';
   import ReactDOM from 'react-dom';
   import { IntlProvider } from 'react-intl';
   import { BrowserRouter as Router } from 'react-router-dom';
   import { combineReducers, createStore } from 'redux';
   import { Provider as ReduxProvider } from 'react-redux';
   import { createHttpLink, ApolloProvider } from '@apollo/client';
   import { ConfigContextProvider, useCustomUrlEvent, useReferrerEvent, usePageEvent, useDataLayerEvents, useAddToCartEvent } from '@adobe/aem-core-cif-react-components';
   import { EventCollectorContextProvider, useEventCollectorContext } from '@adobe/aem-core-cif-experience-platform-connector';
   import { useAdapter } from '@magento/peregrine/lib/talons/Adapter/useAdapter';
   import { customFetchToShrinkQuery } from '@magento/peregrine/lib/Apollo/links';
   import { BrowserPersistence } from '@magento/peregrine/lib/util';
   import { default as PeregrineContextProvider } from '@magento/peregrine/lib/PeregrineContextProvider';
   import { enhancer, reducers } from '@magento/peregrine/lib/store';
   
   const storage = new BrowserPersistence();
   const store = createStore(combineReducers(reducers), enhancer);
   
   storage.setItem('store_view_code', config.storeView);
   
   const App = () => {
       const [{ sdk: mse }] = useEventCollectorContext();
   
       // trigger page-level events
       useCustomUrlEvent({ mse });
       useReferrerEvent({ mse });
       usePageEvent({ mse });
       // listen for add-to-cart events and enable forwarding to the magento storefront events sdk
       useAddToCartEvent(({ mse }));
       // enable CIF specific event forwarding to the Adobe Client Data Layer
       useDataLayerEvents();
   
       useEffect(() => {
           // implement a proper marketing opt-in, for demo purpose you hard-set the consent cookie
           if (document.cookie.indexOf('mg_dnt') < 0) {
               document.cookie += '; mg_dnt=track';
           }
       }, []);
   
       // TODO: use the App to create Portals and PortalPlaceholders to mount the CIF / Peregrine components to the server side rendered markup
       return <></>;
   };
   
   const AppContext = ({ children }) => {
       const { storeView, graphqlEndpoint, graphqlMethod = 'POST', headers = {}, eventsCollector } = config;
       const { apolloProps } = useAdapter({
           apiUrl: new URL(graphqlEndpoint, window.location.origin).toString(),
           configureLinks: (links, apiBase) =>
               // reconfigure the HTTP link to use the configured graphqlEndpoint, graphqlMethod and storeView header
   
               links.set('HTTP', createHttpLink({
                   fetch: customFetchToShrinkQuery,
                   useGETForQueries: graphqlMethod !== 'POST',
                   uri: apiBase,
                   headers: { ...headers, 'Store': storeView }
               }))
       });
   
       return (
           <ApolloProvider {...apolloProps}>
               <IntlProvider locale='en' messages={{}}>
                   <ConfigContextProvider config={config}>
                       <ReduxProvider store={store}>
                           <PeregrineContextProvider>
                               <EventCollectorContextProvider {...eventsCollector}>
                                   {children}
                               </EventCollectorContextProvider>
                           </PeregrineContextProvider>
                       </ReduxProvider>
                   </ConfigContextProvider>
               </IntlProvider>
           </ApolloProvider>
       );
   };
   
   window.onload = async () => {
       const root = document.createElement('div');
       document.body.appendChild(root);
   
       ReactDOM.render(
           <Router>
               <AppContext>
                   <App />
               </AppContext>
           </Router>,
           root
       );
   };
   ```

   De `EventCollectorContext` exporteert de context React die:

   - laadt de bibliotheek commerce-events-sdk en commerce-events-collector;
   - initialiseert hen met een bepaalde configuratie voor Experience Platform en/of ACDS
   - schrijft zich in voor alle gebeurtenissen uit Peregrine en stuurt ze door naar de gebeurtenissen in SDK

   U kunt de implementatiedetails van `EventCollectorContext` controleren. Zie [ aem-core-cif-componenten op GitHub.](https://github.com/adobe/aem-core-cif-components/blob/3d4e44d81fff2f398fd2376d24f7b7019f20b31b/extensions/experience-platform-connector/src/events-collector/EventCollectorContext.js)

### Het bijgewerkte AEM-project bouwen en implementeren {#build-and-deploy}

Om ervoor te zorgen dat de bovenstaande pakketinstallatie, de code, en config veranderingen correct zijn, herbouwt, en stelt het bijgewerkte project van AEM Commerce op gebruikend het volgende Geweven bevel: `$ mvn clean install -PautoInstallSinglePackage`.

## Experience Platform instellen {#aep-setup}

Voer de volgende stappen uit om de gebeurtenisgegevens die afkomstig zijn van de AEM Commerce-pagina&#39;s, zoals categorie en product, te ontvangen en op te slaan:

>[!AVAILABILITY]
>
>Zorg ervoor u deel van de correcte __Profielen van het Product__ onder __Adobe Experience Platform__ en __de Inzameling van Gegevens van Adobe Experience Platform__ uitmaakt. Indien nodig, werk met uw systeembeheerder om, __Profielen van het Product__ tot stand te brengen bij te werken of toe te wijzen onder [ Admin Console.](https://adminconsole.adobe.com/)

### Schema maken met Commerce-veldgroep {#create-schema}

Om de structuur voor de gegevens van de handelsgebeurtenis te bepalen, moet u een schema van de Gegevens van de Ervaring van het Model (XDM) tot stand brengen. Een schema is een set regels die de structuur en indeling van gegevens vertegenwoordigen en valideren.

1. In browser, navigeer aan de __Adobe Experience Platform__ pagina van het producthuis. Bijvoorbeeld <https://experience.adobe.com/#/@YOUR-ORG-NAME/sname:prod/platform/home> .

1. Bepaal de plaats van het __menu van Schema&#39;s__ in de linkernavigatiesectie, klik __creeer Schema__ knoop van de top-right sectie, en selecteer __XDM ExperienceEvent__.

   ![ AEP creeert Schema ](../assets/aep-integration/AEP-Schema-EventSchema-1.png)

1. Geef uw schema een naam gebruikend het __gebied van de Eigenschappen van het Schema > van de Naam van de Vertoning__ en voeg de groepen van het Gebied toe door de __Samenstelling > van het Gebied >__ knoop toe te gebruiken.

   ![ de Definitie van het Schema van AEP ](../assets/aep-integration/AEP-Schema-Definition.png)

1. In __voeg de dialoog van de Groepen van het Gebied__ toe, onderzoek naar `Commerce`, selecteer __Commerce Details__ checkbox, en klik __voeg de groepen van het Gebied__ toe.

   ![ de Definitie van het Schema van AEP ](../assets/aep-integration/AEP-Schema-Field-Group.png)


>[!TIP]
>
>Zie de [ Grondbeginselen van schemacompositie ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html) voor meer informatie.

### Gegevensset maken {#create-dataset}

Om de gebeurtenisgegevens op te slaan, moet u een Dataset tot stand brengen die aan de schemadefinitie voldoet. Een dataset is een opslag en beheersconstructie voor een inzameling van gegevens - typisch een lijst-die een schema (kolommen) en gebieden (rijen) bevat.

1. In browser, navigeer aan de __Adobe Experience Platform__ pagina van het producthuis. Bijvoorbeeld <https://experience.adobe.com/#/@YOUR-ORG-NAME/sname:prod/platform/home> .

1. Bepaal de plaats van het __menu van Datasets__ in de linkernavigatiesectie en klik __creëren dataset__ knoop van de top-right sectie.

   ![ AEP creeert Datasets ](../assets/aep-integration/AEP-Datasets-Create.png)

1. Voor de nieuwe pagina, creeer __dataset van schema__ kaart.

   ![ AEP creeert de Optie van het Schema van Datasets ](../assets/aep-integration/AEP-Datasets-Schema-Option.png)

   Voor de nieuwe pagina, __onderzoek en selecteer__ het schema u in de vorige stap creeerde, en klik de __Volgende__ knoop.

   ![ AEP creeert Datasets Uitgezochte Schema ](../assets/aep-integration/AEP-Datasets-Select-Schema.png)

1. Naam uw Dataset gebruikend __vormt dataset > het gebied van de Naam__ en klikt de __Afwerking__ knoop.

   ![ AEP creeert Naam Datasets ](../assets/aep-integration/AEP-Datasets-Name.png)

>[!TIP]
>
>Zie het [ overzicht van Datasets ](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html) voor meer informatie.


### DataStream maken {#create-datastream}

Voer de volgende stappen uit zodat u een DataStream kunt maken in de Experience Platform.

1. In browser, navigeer aan de __Adobe Experience Platform__ pagina van het producthuis. Bijvoorbeeld <https://experience.adobe.com/#/@YOUR-ORG-NAME/sname:prod/platform/home> .

1. Bepaal de plaats van het __menu van Gegevensstromen__ in de linkernavigatiesectie en klik de __Nieuwe knoop DataStream__ van de top-juiste sectie.

   ![ AEP leidt tot gegevensstromen ](../assets/aep-integration/AEP-Datastream-Create.png)

1. Noem uw DataStream gebruikend het __Naam__ vereiste gebied. Onder het __gebied van het Schema van de Gebeurtenis 0&rbrace;, selecteer het gecreeerde schema en klik__ sparen __.__

   ![ AEP bepaalt gegevensstromen ](../assets/aep-integration/AEP-Datastream-Define.png)

1. Open gecreeerde DataStream, en klik __voegt de Dienst__ toe.

   ![ AEP Datastreams voegt de Dienst ](../assets/aep-integration/AEP-Datastream-Add-Service.png) toe

1. Onder het __gebied van de Dienst__, selecteer de __Adobe Experience Platform__ optie. Onder __Dataset van de Gebeurtenis__ gebied, selecteer de datasetnaam van de vorige stap en klik __sparen__.

   ![ AEP Datastreams voegt de Details van de Dienst ](../assets/aep-integration/AEP-Datastream-Add-Service-Define.png) toe

>[!TIP]
>
>Zie het [ Overzicht DataStream ](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) voor meer informatie.

## Gegevensstroomwaarde toevoegen aan AEM Commerce-configuratie {#add-aep-values-to-aem}

Na de voltooiing van de bovengenoemde opstelling van Experience Platform, zou u `datastreamId` in het linkerspoor van de gegevens moeten hebben DataStream en `orgId` in de hoger-juiste hoek van het __Beeld van het Profiel > de informatie van de Rekening > de modaal van de Informatie van de Gebruiker__.

![ identiteitskaart van Gegevens van AEP ](../assets/aep-integration/AEP-Datastream-ID.png)

1. Werk in de module `ui.frontend` van het AEM Commerce-project het `config.js` -bestand bij en specifiek de objecteigenschappen `eventsCollector > aep` .

1. Het bijgewerkte AEM Commerce-project bouwen en implementeren


## Trigger `addToCart` -gebeurtenis activeren en gegevensverzameling controleren {#event-trigger-verify}

De bovenstaande stappen voltooien de installatie van AEM Commerce en Experience Platform. U kunt een `addToCart` gebeurtenis nu teweegbrengen en gegevensinzameling verifiëren gebruikend de de uitbreiding van Google Chrome _Inspecteur van de Snowplow_ en dataset __Metriek en grafieken__ knevel in product UI.

Als u de gebeurtenis wilt activeren, kunt u de AEM-auteur of de publicatieservice gebruiken vanuit uw lokale instellingen. In dit voorbeeld gebruikt u de AEM-auteur door u aan te melden bij uw account.

1. Van de pagina van Plaatsen, selecteer __Mijn Demo StoreFront > ons > en__ pagina en klik __uitgeven__ in hoogste actiebar.

1. Van de hoogste actiebar, klik __Mening zoals Gepubliceerd__, dan om het even welke aangewezen categorie van de navigatie van de opslag.

1. Klik om het even welke aangewezen productkaart in de __Pagina van het Product__, dan uitgezochte __kleur, grootte__ om __toe te laten voeg aan Kar__ knoop toe.

1. Open de __uitbreiding van de Inspecteur van de Snowplow__ van het browser uitbreidingspaneel en selecteer __Experience Platform Wed SDK__ in het linkerspoor.

1. Terugkeer aan de __Pagina van het Product__ en klik __toevoegen aan de knoop van de Kar__. Hiermee worden gegevens naar de Experience Platform verzonden. De __Adobe Experience Platform Debugger__ uitbreiding toont de gebeurtenisdetails.

   ![ AEP Debugger toe:voegen-aan-Kaart gebeurtenis-Gegevens ](../assets/aep-integration/AEP-Debugger-AddToCart-EventData.png)

1. Binnen het product UI van Experience Platform, navigeer aan __Datasets > Mijn Demo StoreFront__, onder de __activiteit van de Dataset__ tabel. Als __Metriek en grafieken__ wordt toegelaten, worden de gebeurtenis-gegevens stats getoond.

   ![ de statistieken van Gegevens van de Dataset van Experience Platform ](../assets/aep-integration/AEP-Dataset-AddToCart-EventData.png)

## Implementatiedetails {#implementation-details}

De [ Schakelaar van CIF Experience Platform ](https://github.com/adobe/aem-core-cif-components/tree/master/extensions/experience-platform-connector) wordt voortgebouwd bovenop de [ Verbinding van Gegevens voor Adobe Commerce ](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html), die deel van het [ PWA Studio ](https://developer.adobe.com/commerce/pwa-studio/) project uitmaakt.

Met het PWA Studio-project kunt u Progressive Web Application (PWA)-winkels maken die worden aangedreven door Adobe Commerce of Magento Open Source. Het project bevat ook een componentenbibliotheek genoemd [ Peregrin ](https://developer.adobe.com/commerce/pwa-studio/api/peregrine/) voor het toevoegen van logica aan visuele componenten. De [ bibliotheek Peregrin ](https://developer.adobe.com/commerce/pwa-studio/api/peregrine/) verstrekt ook de haken van het douaneantwoord die door [ de Schakelaar van CIF Experience Platform ](https://github.com/adobe/aem-core-cif-components/tree/master/extensions/experience-platform-connector) worden gebruikt om met Experience Platform naadloos te integreren.

## Ondersteunde gebeurtenissen {#supported-events}

Vanaf nu worden de volgende gebeurtenissen ondersteund:

__Experience XDM Events :__

1. Toevoegen aan winkelwagentje (AEM)
1. Pagina weergeven (AEM)
1. Product weergeven (AEM)
1. Zoekaanvraag verzonden (AEM)
1. Respons zoekopdracht ontvangen (AEM)

Wanneer [ Peregrine componenten ](https://developer.adobe.com/commerce/pwa-studio/guides/packages/peregrine/) in het project van AEM Commerce opnieuw worden gebruikt:

__Experience XDM Events :__

1. Verwijderen uit winkelwagen
1. Winkelwagentje openen
1. Winkelwagentje bekijken
1. Direct aanschaffen
1. Afhandeling starten
1. Uitchecken voltooien

__Profile XDM Events :__

1. Aanmelden
1. Account maken
1. Account bewerken

## Aanvullende bronnen {#additional-resources}

Zie de volgende bronnen voor meer informatie:

- [ PWA Studio ](https://developer.adobe.com/commerce/pwa-studio/)
- [[!DNL Data Connection]  overzicht ](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/overview.html)
- [[!DNL Data Connection]  Gebeurtenissen ](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/event-forwarding/events.html)
- [ overzicht van Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/landing/home.html)
