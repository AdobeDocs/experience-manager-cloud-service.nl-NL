---
title: Beste praktijken voor de opstelling en het gebruik van AEM GraphQL met Inhoudsfragmenten
description: Leer de geadviseerde Beste praktijken voor de opstelling en het gebruik van AEM GraphQL met de Fragments van de Inhoud.
exl-id: 4d6a5aaa-c8be-4858-ad07-085dc4fb77e7
feature: Headless
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 1%

---

# Beste praktijken voor de opstelling en het gebruik van AEM GraphQL met Inhoudsfragmenten{#best-practices-setup-use-aem-graphql-content-fragments}

Deze richtlijnen vatten de geadviseerde beste praktijken voor vestiging samen, vormend en het gebruiken AEM met GraphQL en de Fragments van de Inhoud.

## Aan de slag {#getting-started}

Zo kunt u sneller:

* [Wat is Headless?](/help/headless/what-is-headless.md)
* Een overzicht van de verschillende omgevingen in de AEM [Architectuur](/help/headless/deployment/architecture.md)

## Instellen {#setup}

Als u AEM GraphQL veilig wilt instellen voor gebruik met Content Fragments en uw apps, moet u verschillende componenten configureren.

### GraphQL-eindpunt maken (inclusief beveiliging) {#graphql-endpoint-creation}

Het eindpunt is het pad dat wordt gebruikt om toegang te krijgen tot GraphQL voor AEM. Deze eindpunten moeten worden gemaakt en gepubliceerd, zodat ze veilig toegankelijk zijn.

#### Details {#details-graphql-endpoint-creation}

[GraphQL-eindpunten beheren in AEM](/help/headless/graphql-api/graphql-endpoint.md)

#### Omgevingen {#environments-graphql-endpoint-creation}

De eindpunten moeten worden gevormd in:

* Auteur
* Voorvertoning
* Publiceren

Voor:

* Ontwikkeling
* Testen
* Productie

### AEM Dispatcher caching {#dispatcher-caching}

>[!NOTE]
>Als caching in de Dispatcher wordt toegelaten dan [CORS instellen](#cors-setup) is niet nodig en kan dus worden genegeerd.

Caching van persisted query&#39;s wordt niet standaard ingeschakeld in de Dispatcher. De standaard enablement is niet mogelijk aangezien de klanten die CORS (het Delen van het Middel van de Cross-Origin) met veelvoudige oorsprong gebruiken hun configuratie van de Verzender moeten herzien en misschien bijwerken.

#### Details {#details-dispatcher-caching}

[GraphQL Persisted Queries - caching inschakelen in Dispatcher](/help/headless/deployment/dispatcher-caching.md)

#### Omgevingen {#environments-dispatcher-caching}

De Dispatcher wordt gewoonlijk gevormd voor:

* Publish: productie

### CORS instellen {#cors-setup}

>[!NOTE]
>Als het caching in [AEM Dispatcher](#dispatcher-caching) wordt toegelaten dan is de opstelling CORS niet nodig, en zodat kan deze sectie worden genegeerd.

Om tot het eindpunt van GraphQL toegang te hebben, moet een beleid CORS worden gevormd en aan een AEM Project worden toegevoegd dat aan AEM via de Manager van de Wolk wordt opgesteld. Dit wordt gedaan door een aangewezen OSGi CORS configuratiedossier voor het gewenste eindpunt (s) toe te voegen.

#### Details {#details-cors-setup}

[Configuratie voor het delen van bronnen tussen verschillende bronnen (CORS)](/help/headless/deployment/cross-origin-resource-sharing.md)

#### Omgevingen {#environments-cors-setup}

CORS wordt gewoonlijk geconfigureerd voor:

* Publish: productie

### Verificatie {#authentication}

Een van de belangrijkste gebruiksscenario&#39;s voor de Adobe Experience Manager as a Cloud Service (AEM) GraphQL API voor het leveren van inhoudsfragmenten is het accepteren van externe query&#39;s van toepassingen of services van derden. Deze externe query&#39;s vereisen mogelijk geverifieerde API-toegang om de levering van inhoud zonder kop te beveiligen.

#### Details {#details-authentication}

[Verificatie voor externe AEM GraphQL-query&#39;s op inhoudsfragmenten](/help/headless/security/authentication.md)

#### Omgevingen {#environments-authentication}

De authentificatie wordt gewoonlijk gevormd voor:

* Voorvertoning
* Publiceren

Voor:

* Ontwikkeling
* Testen
* Productie

### Machtigingen {#permissions}

Met een implementatie zonder kop zijn er verschillende gebieden met beveiliging en machtigingen die moeten worden aangepakt. Machtigingen en personen kunnen globaal worden overwogen op basis van de AEM omgeving **Auteur** of **Publiceren**. Elke omgeving bevat verschillende personen en met verschillende behoeften.

#### Details {#details-permissions}

[Bevoegdheidsoverwegingen voor inhoud zonder kop](/help/headless/security/permissions.md)

#### Omgevingen {#environments-permissions}

De toestemmingen worden gewoonlijk gevormd voor:

* Auteur
* Voorvertoning
* Publiceren

Voor:

* Ontwikkeling
* Testen
* Productie

### Een CDN (Content Delivery Network) gebruiken {#cdn}

GraphQL-query&#39;s en hun JSON-antwoorden kunnen in de cache worden geplaatst als ze worden toegewezen aan `GET` vraagt wanneer het gebruiken van een CDN. Aanvragen zonder cache kunnen daarentegen zeer (bron)duur zijn en traag verlopen, met mogelijk verdere nadelige gevolgen voor de middelen van de oorsprong.

#### Details {#details-cdn}

[CDN in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md)

#### Omgevingen {#environments-cdn}

Een CDN wordt gewoonlijk gevormd voor:

* Publish: productie

### Inhoudsfragmenten configureren en maken {#cconfigure-create-content-fragments}

AEM GraphQL wordt gebruikt om informatie van uw Contentfragmenten terug te winnen. Deze moeten worden gevormd, dan wordt een structuur en een plaats bepaald, alvorens u de inhoud kunt tot stand brengen.

#### Details {#details-content-fragments}

* [Een configuratie maken](/help/headless/setup/create-configuration.md)
* [Een fragmentmodel voor inhoud maken](/help/headless/setup/create-content-model.md)
* [Een middelenmap maken](/help/headless/setup/create-assets-folder.md)
* [Inhoudsfragmenten maken en bewerken](/help/headless/setup/create-content-fragment.md)

#### Omgevingen {#eenvironments-content-fragments}

Inhoudsfragmenten worden gedefinieerd, geschreven, getest, gepubliceerd en geopend op:

* Auteur
* Voorvertoning
* Publiceren

Voor:

* Ontwikkeling
* Testen
* Productie

## AEM GraphQL gebruiken {#use-aem-graphql}

### GraphQL-query&#39;s optimaliseren {#optimize-graphql-queries}

Deze richtlijnen zijn bedoeld om prestatieproblemen met uw GraphQL-query&#39;s te voorkomen.

#### Details {#details-optimize-graphql-queries}

[GraphQL-query&#39;s optimaliseren](/help/headless/graphql-api/graphql-optimization.md)

>[!NOTE]
>
>De optimalisatierichtlijnen behandelen geheim voorgeheugenconfiguratie, reeds behandeld in [Instellen](#setup).

### GraphQL openen vanuit uw apps {#access-graphql-from-your-apps}

AEM CMS zonder kop geeft ontwikkelaars de vrijheid om uitzonderlijke ervaringen op te bouwen en te leveren met behulp van de talen, frameworks en tools die ze al kennen.

#### Details {#details-your-apps}

* [De SDK van AEM installeren en gebruiken voor ontwikkeling](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/aem-headless-sdk.html)
* [Bronnen voor ontwikkelaars zonder hoofd AEM](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* Voorbeelden, waaronder [Reageren](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/react-app.html), [Next.js](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/next-js.html), [Node.js](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/server-to-server-app.html), onder andere

#### Omgevingen {#environments-your-apps}

Apps worden gewoonlijk ontwikkeld, getest en gebruikt op:

* Voorvertoning
* Publiceren

Voor:

* Ontwikkeling
* Testen
* Productie

### Aanvullende bronnen

Raadpleeg de volgende secties voor meer informatie over AEM GraphQL en Content Fragments:

* [GraphQL API AEM voor gebruik met inhoudsfragmenten](/help/headless/graphql-api/content-fragments.md)
* [GraphiQL IDE gebruiken](/help/headless/graphql-api/graphiql-ide.md)
* [Bronnen voor ontwikkelaars zonder hoofd AEM](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
