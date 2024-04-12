---
title: API-referentiematerialen
description: AEM beschikt over uitgebreide en krachtige API's die u kunt gebruiken voor uw digitale-ervaringsproject.
exl-id: d4ef3040-5a0a-4149-9e99-09eda9605038
source-git-commit: 674db680f46a4fd4772cb10fe7cb396652354dfe
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 1%

---

# API-referentiematerialen {#api-reference-materials}

Adobe Experience Manager (AEM) biedt veel API&#39;s voor het ontwikkelen van toepassingen en het uitbreiden van AEM. AEM is gebouwd bovenop verschillende open-source-technologieën, die ook kunnen worden gebruikt.

## Core-API&#39;s AEM {#core-aem-apis}

De volgende API&#39;s zijn essentieel voor AEM.

| API | Beschrijving |
|---|---|
| [Adobe Experience Manager as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | Productabstracties zoals pagina&#39;s, middelen, workflows enzovoort. |
| [Graniet-interface](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html#) | De Open Web-stapel van de Adobe, die diverse essentiële componenten verstrekt (De 6.5 Materialen van Granite zijn op AEMaaCS van toepassing) |
| [Koraalinterface](https://opensource.adobe.com/coral-spectrum/documentation/) | De visuele stijl van de Adobe voor wolk UIs, die wordt ontworpen om consistentie in de gebruikerservaring te verstrekken |

<!---
|Editor core JavaScript API reference|Provides all the base objects and concepts to support authoring of content resources|
--->

>[!NOTE]
>
>Voor de meest recente informatie over Experience Manager-API&#39;s gaat u ook naar [Adobe Experience Manager as a Cloud Service API&#39;s](https://developer.adobe.com/experience-cloud/experience-manager-apis/).

## Aanvullende kaders {#additional-apis}

AEM vertrouwt op verscheidene extra open-bron APIs.

| API | Beschrijving |
|---|---|
| [Apache Sling](https://sling.apache.org/apidocs/sling11/) | Webframework dat gebruikmaakt van een JCR (Java Content Repository) voor het opslaan en beheren van inhoud |
| [Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | Implementeer een schaalbare en krachtige hiërarchische Java Content Repository (JCR) voor gebruik als basis voor moderne websites van wereldklasse |
| [Java Content Repository](https://www.adobe.io/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html) | Specificatie voor JCR-versie 2.0 |
| [Apache Felix](https://felix.apache.org) | Implementatie van het OSGi (Open Services Gateway Initiative)-framework en -serviceplatform |

## API-voorkeursrichtlijnen {#guidelines}

AEM is gebaseerd op de volgende vier primaire Java API-sets in aflopende volgorde van voorkeur.

| Prioriteit | API | Beschrijving |
|---|---|---|
| 1 | [Adobe Experience Manager as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | Productabstracties zoals pagina&#39;s, middelen, workflows enzovoort. |
| 2 | [Apache Sling](https://sling.apache.org/apidocs/sling11/) | REST en op bron-gebaseerde abstracties zoals middelen, waardekaarten, en HTTP- verzoeken. |
| 3 | [Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | Abstracties van gegevens en inhoud, zoals knooppunten, eigenschappen en sessies. |
| 4 | [Apache Felix](https://felix.apache.org/) | OSGi de abstracties van de toepassingscontainer zoals de diensten en (OSGi) componenten. |

Als een API door AEM wordt verstrekt, verkies het over Sling, JCR, en OSGi. Als AEM geen API aanbiedt, kiest u Verdelen boven JCR en OSGi.

>[!TIP]
>
>Zie het document voor meer informatie over deze richtlijnen [Tips en trucs voor Java API begrijpen.](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html)

## Services en API&#39;s voor levering en contentbeheer AEM {#delivery-apis}

AEM biedt aanpasbare componenten en leveringsopties voor inhoud.

| Functie | Beschrijving |
|---|---|
| [De kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) | De gestandaardiseerde componenten van het Beheer van de Inhoud van het Web (WCM) voor AEM om ontwikkelingstijd te versnellen en onderhoudskosten van uw websites te drukken |
| [JSON-exportfunctie](/help/implementing/developing/components/json-exporter.md) | De inhoud van elke AEM pagina leveren in de indeling van het JSON-gegevensmodel |
| [JSON-export inschakelen voor een component](/help/implementing/developing/components/enabling-json-exporter.md) | JSON-export van componentinhoud genereren op basis van een modellerframework |
| [Elementen-API](/help/assets/mac-api-assets.md) | Hiermee kunt u CRUD-bewerkingen (read-read-update-delete) maken voor elementen, waaronder binaire elementen, metagegevens, uitvoeringen en opmerkingen. Zie AEM Assets HTTP API |
| [HTTP-API voor contentfragmenten](/help/assets/content-fragments/assets-api-content-fragments.md) | Inhoud rechtstreeks benaderen via de HTTP-API via CRUD-bewerkingen |
| [GraphQL API voor inhoudsfragment](/help/headless/graphql-api/content-fragments.md) | Efficiënte levering van inhoudsfragmenten aan JavaScript-clients inschakelen in CMS-implementaties zonder kop |
| [Content Fragments Assets HTTP API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html) | De exacte indeling van ondersteunde HTTP-elementaanvragen |
| [Inhoudsfragment en Inhoudsfragmentmodel OpenAPI&#39;s](/help/headless/content-fragment-openapis.md) | Inhoudsfragment en Inhoudsfragmentmodel OpenAPI&#39;s |

## SPA-specifieke API&#39;s {#spa-apis}

AEM SDK-framework van de Editor (SPA) voor één pagina biedt specifieke JavaScript API-referenties.

| API | Beschrijving |
|---|---|
| [Componenttoewijzing](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping) | Biedt een manier voor de toepassing Eén pagina om front-end componenten toe te wijzen aan Adobe Experience Manager-brontypen (AEM Components) |
| [Paginamodel](https://www.npmjs.com/package/@adobe/aem-spa-page-model-manager) | Een interpreter tussen de Adobe Experience Manager Editor en de Adobe Experience Manager Single Page Application (SPA) Editor |
| [Bewerkbare componenten Reageren](https://www.npmjs.com/package/@adobe/aem-react-editable-components) | Verstrekt React componenten en integratielaag om u met de Redacteur van de Plaats van Adobe Experience Manager te beginnen |
| [Bewerkbare angulars](https://www.npmjs.com/package/@adobe/aem-angular-editable-components) | Verstrekt de componenten van de Angular en integratielaag om u met de Redacteur van de Plaats van Adobe Experience Manager te beginnen |

>[!TIP]
>
>Kijk uit de [SPA Inleiding en Analyse](/help/implementing/developing/hybrid/introduction.md) voor meer informatie over toepassingen van één pagina.
