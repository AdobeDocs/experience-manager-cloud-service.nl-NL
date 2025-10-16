---
title: Aanbevolen procedures voor het instellen en gebruiken van AEM GraphQL met Content Fragments
description: Leer de geadviseerde Beste praktijken voor de opstelling en het gebruik van AEM GraphQL met Inhoudsfragmenten.
exl-id: 4d6a5aaa-c8be-4858-ad07-085dc4fb77e7
feature: Headless
role: Admin, Developer
source-git-commit: 38a4bf89e099432163163e90e08aa0f47407724f
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 1%

---

# Aanbevolen procedures voor het instellen en gebruiken van AEM GraphQL met Content Fragments{#best-practices-setup-use-aem-graphql-content-fragments}

In deze richtlijnen wordt een overzicht gegeven van de aanbevolen aanbevolen procedures voor het instellen, configureren en gebruiken van AEM met GraphQL en Content Fragments.

## Aan de slag {#getting-started}

Zo kunt u sneller:

* [Wat is Headless?](/help/headless/what-is-headless.md)
* Een overzicht van de diverse milieu&#39;s in de Architectuur van AEM [&#x200B; &#x200B;](/help/headless/deployment/architecture.md)

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

### AEM Dispatcher in cache plaatsen {#dispatcher-caching}

>[!NOTE]
>Als het in het voorgeheugen onderbrengen in Dispatcher dan wordt toegelaten is de [&#x200B; opstelling CORS &#x200B;](#cors-setup) niet nodig, en kan zo worden genegeerd.

Het in cache plaatsen van doorlopende query&#39;s is niet standaard ingeschakeld in de Dispatcher. Standaardactivering is niet mogelijk omdat klanten die gebruikmaken van CORS (Cross-Origin Resource Sharing) met meerdere origines hun Dispatcher-configuratie moeten controleren en mogelijk bijwerken.

#### Details {#details-dispatcher-caching}

[GraphQL Persisted Queries - caching inschakelen in Dispatcher](/help/headless/deployment/dispatcher-caching.md)

#### Omgevingen {#environments-dispatcher-caching}

De Dispatcher is gewoonlijk geconfigureerd voor:

* Publiceren: productie

### CORS instellen {#cors-setup}

>[!NOTE]
>Als caching in [&#x200B; AEM Dispatcher &#x200B;](#dispatcher-caching) wordt toegelaten dan is de opstelling CORS niet nodig, en zo kan deze sectie worden genegeerd.

Om tot het eindpunt van GraphQL toegang te hebben, moet een beleid CORS worden gevormd en aan een Project van AEM worden toegevoegd dat aan AEM via Cloud Manager wordt opgesteld. Dit wordt gedaan door een aangewezen OSGi CORS configuratiedossier voor het gewenste eindpunt (s) toe te voegen.

#### Details {#details-cors-setup}

[Configuratie voor het delen van bronnen tussen verschillende bronnen (CORS)](/help/headless/deployment/cross-origin-resource-sharing.md)

#### Omgevingen {#environments-cors-setup}

CORS wordt gewoonlijk geconfigureerd voor:

* Publiceren: productie

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

Met een implementatie zonder kop zijn er verschillende gebieden met beveiliging en machtigingen die moeten worden aangepakt. De toestemmingen en de personen kunnen globaal worden overwogen gebaseerd op het milieu van AEM **Auteur** of **publiceren**. Elke omgeving bevat verschillende personen en met verschillende behoeften.

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

GraphQL-query&#39;s en hun JSON-antwoorden kunnen in de cache worden geplaatst als ze worden aangewezen als `GET` -aanvragen bij het gebruik van een CDN. Aanvragen zonder cache kunnen daarentegen zeer (bron)duur zijn en traag verlopen, met mogelijk verdere nadelige gevolgen voor de middelen van de oorsprong.

#### Details {#details-cdn}

[CDN in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md)

#### Omgevingen {#environments-cdn}

Een CDN wordt gewoonlijk gevormd voor:

* Publiceren: productie

### Inhoudsfragmenten configureren en maken {#cconfigure-create-content-fragments}

AEM GraphQL wordt gebruikt om informatie op te halen uit uw inhoudsfragmenten. Deze moeten worden gevormd, dan wordt een structuur en een plaats bepaald, alvorens u de inhoud kunt tot stand brengen.

#### Details {#details-content-fragments}

* [Een configuratie maken](/help/headless/setup/create-configuration.md)
* [Een fragmentmodel voor inhoud maken](/help/headless/setup/create-content-model.md)
* [Een Assets-map maken](/help/headless/setup/create-assets-folder.md)
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
>De optimalisatierichtlijnen behandelen geheim voorgeheugenconfiguratie, reeds behandeld in [&#x200B; Opstelling &#x200B;](#setup).

### GraphQL openen vanuit uw apps {#access-graphql-from-your-apps}

AEM headless CMS geeft ontwikkelaars de vrijheid om uitzonderlijke ervaringen op te bouwen en te leveren met behulp van de talen, frameworks en tools die ze al kennen.

#### Details {#details-your-apps}

* [&#x200B; installeer, en gebruik, AEM SDK voor ontwikkeling &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/aem-headless-sdk.html?lang=nl-NL)
* [&#x200B; AEM Headless Developer Resources &#x200B;](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=nl-NL)
* De voorbeelden, met inbegrip van [&#x200B; Reageren &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/react-app.html?lang=nl-NL), [&#x200B; Next.js &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/next-js.html), [&#x200B; Node.js &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/example-apps/server-to-server-app.html?lang=nl-NL), onder andere

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

* [AEM GraphQL API voor gebruik met inhoudsfragmenten](/help/headless/graphql-api/content-fragments.md)
* [GraphiQL IDE gebruiken](/help/headless/graphql-api/graphiql-ide.md)
* [&#x200B; AEM Headless Developer Resources &#x200B;](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=nl-NL)
