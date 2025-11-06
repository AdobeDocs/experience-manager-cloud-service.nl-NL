---
title: API-referentiematerialen
description: AEM heeft uitgebreide en krachtige API's die u kunt gebruiken voor uw digitale-ervaringsproject.
exl-id: d4ef3040-5a0a-4149-9e99-09eda9605038
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 1%

---

# API-referentiematerialen {#api-reference-materials}

Adobe Experience Manager (AEM) biedt veel API&#39;s voor het ontwikkelen van toepassingen en het uitbreiden van AEM. AEM is gebouwd bovenop verschillende open-source-technologieën, die ook kunnen worden gebruikt.

## AEM Core-API&#39;s {#core-aem-apis}

De volgende API&#39;s zijn van wezenlijk belang voor AEM.

| API | Beschrijving |
|---|---|
| [&#x200B; Adobe Experience Manager as a Cloud Service &#x200B;](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | Productabstracties zoals pagina&#39;s, middelen, workflows enzovoort. |
| [&#x200B; graniet UI &#x200B;](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html#) | Adobe Open Web stack, die verschillende essentiële componenten biedt (de 6.5 Granite-materialen zijn van toepassing op AEMaaCS) |
| [&#x200B; Koraal UI &#x200B;](https://opensource.adobe.com/coral-spectrum/documentation/) | Adobe visuele stijl voor cloud-gebruikersinterface, ontworpen om consistentie in de gebruikerservaring te bieden |

<!---
|Editor core JavaScript API reference|Provides all the base objects and concepts to support authoring of content resources|
--->

>[!NOTE]
>
>Voor de recentste informatie over Experience Manager APIs, gelieve ook [&#x200B; Adobe Experience Manager as a Cloud Service APIs &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/) te bezoeken.

## Aanvullende kaders {#additional-apis}

AEM is afhankelijk van verschillende extra open-source API&#39;s.

| API | Beschrijving |
|---|---|
| [&#x200B; Apache Sling &#x200B;](https://sling.apache.org/apidocs/sling11/) | Webframework dat gebruikmaakt van een JCR (Java Content Repository) voor het opslaan en beheren van inhoud |
| [&#x200B; Apache Jackrabbit Oak &#x200B;](https://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | Implementeer een schaalbare en krachtige hiërarchische Java Content Repository (JCR) voor gebruik als basis voor moderne websites van wereldklasse |
| [&#x200B; Inhoudsplaats van de Inhoud van Java &#x200B;](https://www.adobe.io/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html) | Specificatie voor JCR-versie 2.0 |
| [&#x200B; Apache Felix &#x200B;](https://felix.apache.org) | Implementatie van het OSGi (Open Services Gateway Initiative)-framework en -serviceplatform |

## API-voorkeursrichtlijnen {#guidelines}

AEM is gebaseerd op de volgende vier primaire Java API-sets in aflopende volgorde van voorkeur.

| Prioriteit | API | Beschrijving |
|---|---|---|
| 1 | [&#x200B; Adobe Experience Manager as a Cloud Service &#x200B;](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | Productabstracties zoals pagina&#39;s, middelen, workflows enzovoort. |
| 2 | [&#x200B; Apache Sling &#x200B;](https://sling.apache.org/apidocs/sling11/) | REST en op bron-gebaseerde abstracties zoals middelen, waardekaarten, en HTTP- verzoeken. |
| 3 | [&#x200B; Apache Jackrabbit Oak &#x200B;](https://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | Abstracties van gegevens en inhoud, zoals knooppunten, eigenschappen en sessies. |
| 4 | [&#x200B; Apache Felix &#x200B;](https://felix.apache.org/) | OSGi de abstracties van de toepassingscontainer zoals de diensten en (OSGi) componenten. |

Als een API door AEM wordt verstrekt, verkies het over Sling, JCR, en OSGi. Als AEM geen API biedt, geeft u de voorkeur aan Sling boven JCR en OSGi.

>[!TIP]
>
>Voor details van deze richtlijnen, zie het document [&#x200B; de Beste praktijken van Java API &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html) begrijpen.

## AEM Delivery and Content Management Services en API&#39;s {#delivery-apis}

AEM biedt aanpasbare componenten en leveringsopties voor inhoud.

| Functie | Beschrijving |
|---|---|
| [&#x200B; de Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) | De gestandaardiseerde componenten van het Beheer van de Inhoud van het Web (WCM) voor AEM om ontwikkelingstijd te versnellen en onderhoudskosten van uw websites te drukken |
| [&#x200B; JSON Exporter &#x200B;](/help/implementing/developing/components/json-exporter.md) | De inhoud van AEM-pagina&#39;s afleveren in JSON-gegevensmodelindeling |
| [&#x200B; toelatend de Uitvoer JSON voor een Component &#x200B;](/help/implementing/developing/components/enabling-json-exporter.md) | JSON-export van componentinhoud genereren op basis van een modellerframework |
| [&#x200B; het Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud &#x200B;](/help/headless/content-fragment-openapis.md) | Inhoudsfragment en Inhoudsfragmentmodel OpenAPI&#39;s |
| [&#x200B; de Levering van het Fragment van de Inhoud van AEM met OpenAPI &#x200B;](/help/headless/aem-content-fragment-delivery-with-openapi.md) | Een HTTP REST-API op AEM Edge Delivery Services die is ontworpen om gestructureerde inhoud van Content Fragments in JSON-indeling te leveren. |
| [&#x200B; het Fragment van de Inhoud GraphQL API &#x200B;](/help/headless/graphql-api/content-fragments.md) | Efficiënte levering van inhoudsfragmenten aan JavaScript-clients in CMS-implementaties zonder kop inschakelen |
|  |  |
| [&#x200B; Assets API &#x200B;](/help/assets/mac-api-assets.md) | Hiermee kunt u CRUD-bewerkingen (read-read-update-delete) maken voor elementen, waaronder binaire elementen, metagegevens, uitvoeringen en opmerkingen. Zie AEM Assets HTTP API |
| [&#x200B; de Fragmenten van de Inhoud HTTP API &#x200B;](/help/assets/content-fragments/assets-api-content-fragments.md) | Inhoud rechtstreeks benaderen via de HTTP-API via CRUD-bewerkingen |
| [&#x200B; de Fragmenten van de Inhoud Assets HTTP API &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html) | Exacte indeling van ondersteunde HTTP-elementaanvragen |

>[!NOTE]
>
>Zie [&#x200B; AEM APIs voor Gestructureerde Inhoudslevering en Beheer &#x200B;](/help/headless/apis-headless-and-content-fragments.md) voor een overzicht van diverse beschikbare APIs en vergelijking van sommige betrokken concepten.

## SPA-specifieke API&#39;s {#spa-apis}

AEM Single-Page Application (SPA) Editor SDK-framework biedt specifieke JavaScript API-referenties.

| API | Beschrijving |
|---|---|
| [&#x200B; Component Mapping &#x200B;](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping) | Biedt een manier voor de toepassing Eén pagina om front-end componenten toe te wijzen aan Adobe Experience Manager-brontypen (AEM Components) |
| [&#x200B; de ModelManager van de Pagina &#x200B;](https://www.npmjs.com/package/@adobe/aem-spa-page-model-manager) | Een tolk tussen de Redacteur van Adobe Experience Manager en de Redacteur van de Toepassing van de Enige Pagina van Adobe Experience Manager (SPA) |
| [&#x200B; Reageer Bewerkbare Componenten &#x200B;](https://www.npmjs.com/package/@adobe/aem-react-editable-components) | Verstrekt React componenten en integratielaag om u met de Redacteur van de Plaats van Adobe Experience Manager te beginnen |
| [&#x200B; Bewerkbare Componenten van Angular &#x200B;](https://www.npmjs.com/package/@adobe/aem-angular-editable-components) | Biedt de Angular-componenten en de integratielaag om u te helpen aan de slag te gaan met de Adobe Experience Manager Site Editor |

>[!TIP]
>
>Controle uit de [&#x200B; Inleiding van het KUUROORD en Analyse &#x200B;](/help/implementing/developing/hybrid/introduction.md) voor meer informatie over enig-paginatoepassingen.
