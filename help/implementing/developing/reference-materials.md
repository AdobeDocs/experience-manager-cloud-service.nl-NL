---
title: API-referentiematerialen
description: AEM beschikt over uitgebreide en krachtige API's die u kunt gebruiken voor uw digitale-ervaringsproject.
exl-id: d4ef3040-5a0a-4149-9e99-09eda9605038
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 1%

---

# API-referentiematerialen {#api-reference-materials}

Adobe Experience Manager (AEM) biedt veel API&#39;s voor het ontwikkelen van toepassingen en het uitbreiden van AEM. AEM is gebouwd bovenop verschillende open-source-technologieën, die ook kunnen worden gebruikt.

## Core-API&#39;s AEM {#core-aem-apis}

De volgende API&#39;s zijn essentieel voor AEM.

| API | Beschrijving |
|---|---|
| [ Adobe Experience Manager as a Cloud Service ](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | Productabstracties zoals pagina&#39;s, middelen, workflows enzovoort. |
| [ graniet UI ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html#) | De Open Web-stapel van Adobe, die diverse essentiële componenten verstrekt (De 6.5 Materialen van Granite zijn op AEMaaCS van toepassing) |
| [ Koraal UI ](https://opensource.adobe.com/coral-spectrum/documentation/) | De visuele stijl van de Adobe voor wolk UIs, die wordt ontworpen om consistentie in de gebruikerservaring te verstrekken |

<!---
|Editor core JavaScript API reference|Provides all the base objects and concepts to support authoring of content resources|
--->

>[!NOTE]
>
>Voor de recentste informatie over Experience Manager APIs, gelieve ook [ Adobe Experience Manager as a Cloud Service APIs ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) te bezoeken.

## Aanvullende kaders {#additional-apis}

AEM vertrouwt op verscheidene extra open-bron APIs.

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

Als een API door AEM wordt verstrekt, verkies het over Sling, JCR, en OSGi. Als AEM geen API aanbiedt, geeft u de voorkeur aan Sling boven JCR en OSGi.

>[!TIP]
>
>Voor details van deze richtlijnen, zie het document [ de Beste praktijken van Java API ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html) begrijpen.

## Services en API&#39;s voor levering en contentbeheer AEM {#delivery-apis}

AEM biedt aanpasbare componenten en leveringsopties voor inhoud.

| Functie | Beschrijving |
|---|---|
| [ de Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) | De gestandaardiseerde componenten van het Beheer van de Inhoud van het Web (WCM) voor AEM om ontwikkelingstijd te versnellen en onderhoudskosten van uw websites te drukken |
| [ JSON Exporter ](/help/implementing/developing/components/json-exporter.md) | De inhoud van elke AEM pagina leveren in de indeling van het JSON-gegevensmodel |
| [ toelatend de Uitvoer JSON voor een Component ](/help/implementing/developing/components/enabling-json-exporter.md) | JSON-export van componentinhoud genereren op basis van een modellerframework |
| [ het Fragment van de Inhoud en ModelAPIs van het Fragment van de Inhoud ](/help/headless/content-fragment-openapis.md) | Inhoudsfragment en Inhoudsfragmentmodel OpenAPI&#39;s |
| [ AEM REST OpenAPI voor levering van inhoudsfragmenten ](/help/headless/aem-rest-openapi-content-fragment-delivery.md) | Een HTTP REST API op AEM Edge Delivery Services, die wordt ontworpen om gestructureerde inhoud van de Fragments van de Inhoud in formaat te leveren JSON. |
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
| [ de ModelManager van de Pagina ](https://www.npmjs.com/package/@adobe/aem-spa-page-model-manager) | Een interpreter tussen de Adobe Experience Manager Editor en de Adobe Experience Manager Single Page Application (SPA) Editor |
| [ Reageer Bewerkbare Componenten ](https://www.npmjs.com/package/@adobe/aem-react-editable-components) | Verstrekt React componenten en integratielaag om u met de Redacteur van de Plaats van Adobe Experience Manager te beginnen |
| [ Angular Bewerkbare Componenten ](https://www.npmjs.com/package/@adobe/aem-angular-editable-components) | Verstrekt de componenten van de Angular en integratielaag om u met de Redacteur van de Plaats van Adobe Experience Manager te beginnen |

>[!TIP]
>
>Controle uit de [ SPA Inleiding en Analyse ](/help/implementing/developing/hybrid/introduction.md) voor meer informatie over enig-paginatoepassingen.
