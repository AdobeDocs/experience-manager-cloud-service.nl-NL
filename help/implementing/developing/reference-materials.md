---
title: API-referentiematerialen
description: AEM heeft uitgebreide en krachtige API's die u kunt gebruiken voor uw digitale-ervaringsproject.
exl-id: d4ef3040-5a0a-4149-9e99-09eda9605038
feature: Developing
role: Admin, Architect, Developer
source-git-commit: d9db32110e1e0aaa5bdc20bd6b4bff6da6a3a3a3
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
| [ Adobe Experience Manager as a Cloud Service ](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | Productabstracties zoals pagina&#39;s, middelen, workflows enzovoort. |
| [ graniet UI ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html#) | Adobe Open Web stack, die verschillende essentiële componenten biedt (de 6.5 Granite-materialen zijn van toepassing op AEMaaCS) |
| [ Koraal UI ](https://opensource.adobe.com/coral-spectrum/documentation/) | Adobe visuele stijl voor cloud-gebruikersinterface, ontworpen om consistentie in de gebruikerservaring te bieden |

<!---
|Editor core JavaScript API reference|Provides all the base objects and concepts to support authoring of content resources|
--->

>[!NOTE]
>
>Voor de recentste informatie over Experience Manager APIs, gelieve ook [ Adobe Experience Manager as a Cloud Service APIs ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) te bezoeken.

## Aanvullende kaders {#additional-apis}

AEM is afhankelijk van verschillende extra open-source API&#39;s.

| API | Beschrijving |
|---|---|
| [ Apache Sling ](https://sling.apache.org/apidocs/sling11/) | Webframework dat gebruikmaakt van een JCR (Java Content Repository) voor het opslaan en beheren van inhoud |
| [ Apache Jackrabbit Oak ](https://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | Implementeer een schaalbare en krachtige hiërarchische Java Content Repository (JCR) voor gebruik als basis voor moderne websites van wereldklasse |
| [ Inhoudsplaats van de Inhoud van Java ](https://www.adobe.io/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html) | Specificatie voor JCR-versie 2.0 |
| [ Apache Felix ](https://felix.apache.org) | Implementatie van het OSGi (Open Services Gateway Initiative)-framework en -serviceplatform |

## API-voorkeursrichtlijnen {#guidelines}

AEM is gebaseerd op de volgende vier primaire Java API-sets in aflopende volgorde van voorkeur.

| Prioriteit | API | Beschrijving |
|---|---|---|
| 1 | [ Adobe Experience Manager as a Cloud Service ](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | Productabstracties zoals pagina&#39;s, middelen, workflows enzovoort. |
| 2 | [ Apache Sling ](https://sling.apache.org/apidocs/sling11/) | REST en op bron-gebaseerde abstracties zoals middelen, waardekaarten, en HTTP- verzoeken. |
| 3 | [ Apache Jackrabbit Oak ](https://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | Abstracties van gegevens en inhoud, zoals knooppunten, eigenschappen en sessies. |
| 4 | [ Apache Felix ](https://felix.apache.org/) | OSGi de abstracties van de toepassingscontainer zoals de diensten en (OSGi) componenten. |

Als een API door AEM wordt verstrekt, verkies het over Sling, JCR, en OSGi. Als AEM geen API biedt, geeft u de voorkeur aan Sling boven JCR en OSGi.

>[!TIP]
>
>Voor details van deze richtlijnen, zie het document [ de Beste praktijken van Java API ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html) begrijpen.

## AEM Delivery and Content Management Services en API&#39;s {#delivery-apis}

AEM biedt aanpasbare componenten en leveringsopties voor inhoud.

| Functie | Beschrijving |
|---|---|
| [ de Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) | De gestandaardiseerde componenten van het Beheer van de Inhoud van het Web (WCM) voor AEM om ontwikkelingstijd te versnellen en onderhoudskosten van uw websites te drukken |
| [ JSON Exporter ](/help/implementing/developing/components/json-exporter.md) | De inhoud van AEM-pagina&#39;s afleveren in JSON-gegevensmodelindeling |
| [ toelatend de Uitvoer JSON voor een Component ](/help/implementing/developing/components/enabling-json-exporter.md) | JSON-export van componentinhoud genereren op basis van een modellerframework |
| [ het Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) | Inhoudsfragment en Inhoudsfragmentmodel OpenAPI&#39;s |
| [ de Levering van het Fragment van de Inhoud van AEM met OpenAPI ](/help/headless/aem-content-fragment-delivery-with-openapi.md) | Een HTTP REST-API op AEM Edge Delivery Services die is ontworpen om gestructureerde inhoud van Content Fragments in JSON-indeling te leveren. |
| [ het Fragment van de Inhoud GraphQL API ](/help/headless/graphql-api/content-fragments.md) | Efficiënte levering van inhoudsfragmenten aan JavaScript-clients in CMS-implementaties zonder kop inschakelen |
|  |  |
| [ Assets API ](/help/assets/mac-api-assets.md) | Hiermee kunt u CRUD-bewerkingen (read-read-update-delete) maken voor elementen, waaronder binaire elementen, metagegevens, uitvoeringen en opmerkingen. Zie AEM Assets HTTP API |
| [ de Fragmenten van de Inhoud HTTP API ](/help/assets/content-fragments/assets-api-content-fragments.md) | Inhoud rechtstreeks benaderen via de HTTP-API via CRUD-bewerkingen |
| [ de Fragmenten van de Inhoud Assets HTTP API ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html) | Exacte indeling van ondersteunde HTTP-elementaanvragen |

>[!NOTE]
>
>Zie [ AEM APIs voor Gestructureerde Inhoudslevering en Beheer ](/help/headless/apis-headless-and-content-fragments.md) voor een overzicht van diverse beschikbare APIs en vergelijking van sommige betrokken concepten.

## SPA-specifieke API&#39;s {#spa-apis}

AEM Single-Page Application (SPA) Editor SDK-framework biedt specifieke JavaScript API-referenties.

| API | Beschrijving |
|---|---|
| [ Component Mapping ](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping) | Biedt een manier voor de toepassing Eén pagina om front-end componenten toe te wijzen aan Adobe Experience Manager-brontypen (AEM Components) |
| [ de ModelManager van de Pagina ](https://www.npmjs.com/package/@adobe/aem-spa-page-model-manager) | Een tolk tussen de Redacteur van Adobe Experience Manager en de Redacteur van de Toepassing van de Enige Pagina van Adobe Experience Manager (SPA) |
| [Bewerkbare onderdelen van React](https://www.npmjs.com/package/@adobe/aem-react-editable-components) | Verstrekt React componenten en integratielaag om u met de Redacteur van de Plaats van Adobe Experience Manager te beginnen |
| [ Bewerkbare Componenten van Angular ](https://www.npmjs.com/package/@adobe/aem-angular-editable-components) | Biedt de Angular-componenten en de integratielaag om u te helpen aan de slag te gaan met de Adobe Experience Manager Site Editor |

>[!TIP]
>
>Controle uit de [ Inleiding van het KUUROORD en Analyse ](/help/implementing/developing/hybrid/introduction.md) voor meer informatie over enig-paginatoepassingen.
