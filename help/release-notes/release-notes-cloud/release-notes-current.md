---
title: De huidige Nota's van de Versie voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Huidige versienota's voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: edfec41a9e33fbe818cb19f878ac42d435d62419
workflow-type: tm+mt
source-wordcount: '1419'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies, zoals 2023 of 2024, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [ Update van het Product van de Prioriteit Adobe ](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2025.2.0) is 4 maart 2025. De volgende release met functies (2025.3.0) is gepland voor 27 maart 2025.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

<!-- 

## Release Video {#release-video}

Have a look at the February 2025 Release Overview video for a summary of the features added in the 2025.2.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}


### Nieuwe functies in AEM Sites {#new-features-sites}

** Automatische tags voor inhoudsfragmenten **

Bij het maken van inhoudsfragmenten is het nu mogelijk automatisch codes over te nemen die zijn toegewezen aan het inhoudsmodel. Dit maakt een krachtige automatische classificatie mogelijk van inhoud die is opgeslagen in inhoudsfragmenten.

** Ondersteuning voor UUID-fragmenten van inhoudsfragmenten **

De UUID-ondersteuning voor inhoudsfragmenten is nu GA. De nieuwe capaciteit verandert niet het op weg-gebaseerde gedrag van verrichtingen binnen AEM, zoals beweging, anders noemen, rollout, waar de wegen automatisch worden aangepast, maar het kan externe consumptie van de Fragmenten van de Inhoud gemakkelijker en stabieler maken, vooral wanneer het gebruiken van de vragen van GraphQL die individuele fragmenten met vragen direct richten ByPath. Dergelijke query&#39;s kunnen worden onderbroken als een fragmentpad verandert. Wanneer het gebruiken van het nieuwe DoorId vraagtype, blijft de vraag nu stabiel aangezien UUID van een fragment niet in gevallen verandert waar de wegen dat doen.

** Dynamische media met OpenAPI-ondersteuning in Inhoudsfragmenteditor en GraphQL **

Assets die in verschillende AEM as a Cloud Service-programma&#39;s zijn opgeslagen dan Content Fragments en die zijn ingeschakeld met de nieuwe Dynamic Media met OpenAPI-mogelijkheid, kan nu worden gebruikt in Content Fragments. Met de afbeeldingskiezer in de nieuwe Content Fragment Editor kunt u nu &quot;externe&quot; opslagruimten selecteren als bron voor afbeeldingselementen waarnaar moet worden verwezen in het fragment. En bij levering van dergelijke inhoudsfragmenten met AEM GraphQL bevat het JSON-antwoord nu vereiste eigenschappen voor externe elementen (assetId, repositoryId), zodat clienttoepassingen respectievelijke dynamische media kunnen maken met OpenAPI-URL&#39;s om de afbeelding op te halen.

** Vertaal HTTP-API **

De AEM Translation HTTP REST API die al een tijdje in de eerste adoptermodus is. De documentatie kan [ hier ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/translation/) worden gevonden. Met de API kunnen de vereiste stappen in het vertaalbeheerproces voor inhoud in AEM worden geautomatiseerd.


## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in AEM Assets {#new-features-assets}

**Dynamische media nieuwe het verpakken structuur**

Er is nu een vernieuwde structuur voor het verpakken van dynamische media beschikbaar die beter aansluit bij de marktverwachtingen en het bijhouden van de ondersteuning. De nieuwe verpakkingsstructuur omvat:

* Dynamic Media Prime, die Dynamic Media met OpenAPI&#39;s en video bevat om de levering te verbeteren.

* Dynamic Media Ultimate voegt bezorgings- en transformatiefuncties toe om aan zwaardere gebruiksvereisten te voldoen.

U moet Assets as a Cloud Service Prime of Ultimate hebben om van de nieuwe verpakkingsstructuur te profiteren.

**AI-Gegenereerde videotitels**

Door AI gegenereerde videobijschriften in Adobe Dynamic Media gebruiken kunstmatige intelligentie om automatisch bijschriften te genereren voor video-inhoud. Deze functie is ontworpen om de toegankelijkheid te verbeteren en de gebruikerservaring te verbeteren door nauwkeurige bijschriften te bieden. Bijschriften worden gegenereerd op basis van de originele audio, eventuele extra audiotracks of extra bijschriften worden weergegeven op het tabblad &quot;Bijschriften en audio&quot; op de pagina met video-eigenschappen. Met ondersteuning voor meer dan 60 talen kunt u bijschriften reviseren en een voorvertoning weergeven voordat u de video publiceert.

**pas onderzoeksfilters** aan

Met de filters Aangepast zoeken kunt u nauwkeuriger en efficiënter relevante informatie zoeken. Het staat voor meer op maat gesneden onderzoeken, het filtreren gegevens toe volgens specifieke attributen zoals merk, product, categorie, of andere zeer belangrijke herkenningstekens. Hierdoor wordt de organisatie verbeterd, de tijd die nodig is om te controleren, verminderd door irrelevante resultaten en wordt de besluitvorming sneller. Het steunt ook scalability, aangezien de grote datasets gemakkelijker worden om te navigeren en te analyseren.

![ pas onderzoeksfilters ](/help/assets/assets/custom-search-filters.png) aan


### Functies voor vroege toegang in Content Hub {#early-access-content-hub}

In Content Hub kunt u nu naast de bestaande statische uitvoeringen ook dynamische en slimme uitsnijdingen weergeven en downloaden. Als beheerder van Content Hub, kunt u de beschikbaarheid van deze vertoningen aan gebruikers ook vormen gebruikend het Gebruikersinterface van de Configuratie.

![ dynamische vertoningen ](/help/assets/assets/download-single-asset-renditions-dynamic.png)



## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties en om de ontwikkeling ervan vorm te geven.

Deze release bevat een overzicht van de innovaties die in de huidige release worden geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie {de documentatie van het Programma van de Vroege Toegang van AEM Forms ](/help/forms/early-access-ea-features.md).[

#### HTML-e-mailsjablonen in Adaptive Forms

De adaptieve Forms staat u toe om [ e-mailmalplaatjes van HTML ](/help/forms/html-email-templates-in-adaptive-forms.md) te gebruiken. Met HTML-e-mailsjablonen kunt u rijke, persoonlijke en visueel aantrekkelijke e-mails verzenden wanneer een formulier wordt verzonden. Deze e-mailberichten kunnen worden aangepast met formuliergegevens en uitgebreid met behulp van verschillende e-mailtags, zoals afbeeldingen en koppelingen. Met Adaptief Forms kunt u een bestand uploaden dat een HTML-sjabloon bevat of een normale teksteditor gebruiken om deze sjablonen te maken.

![ HTML e-mailmalplaatjes ](/help/forms/assets/html-email.png)

#### Verbeterde ondersteuning voor cloudopslag: Direct PDF Uploaden naar Azure Blob Storage

De Generatie APIs van het Document van AEM Forms staat u nu toe om [ geproduceerde documenten van PDF ](/help/forms/early-access-ea-features.md#doc-generation-api) aan Azure BlobOpslag direct te uploaden. Deze verbetering stroomlijnt opslag en terugwinning, verbeterend efficiency en integratie met de werkschema&#39;s van de wolk.


## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Java 21-ondersteuning {#java21}

Zoals vermeld in de opmerkingen bij de release van januari kunt u nu code maken met Java 21. Deze bevat nieuwe functies (bijvoorbeeld patroonovereenkomsten voor switch-instructies, verzegelde klassen) en prestatieverbeteringen. Java 17-builds worden ook nieuw ondersteund. Voor configuratiestappen, met inbegrip van het bijwerken van uw Gemaakt project en bibliotheekversies, zie het [ milieu ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support) artikel bouwen.

Krachtigere Java 21 **runtime** zal automatisch worden opgesteld wanneer Java 17 of 21 bouwt wordt ontdekt. Nochtans, adviseren wij ook opting in Java 21 runtime voor milieu&#39;s die met Java 11 worden gebouwd, door [ aemcs-java-adopter@adobe.com ](mailto:aemcs-java-adopter@adobe.com) te e-mailen. Leer over [ Java 21 runtime vereisten ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> In februari, werd Java 21 **runtime** opgesteld aan ontwikkelings/RDE milieu&#39;s (behalve die reeds gebouwd met Java 17 of 21, die reeds runtime Java 21 hebben). Java 21 wordt in april toegepast op stadium-/productieomgevingen.

### Edge Computing - Verzoek om feedback! {#edge-computing-feedback}

Edge Computing brengt gegevensverwerking dichter bij de browser, wat voordelen heeft, zoals minder latentie. Adobe wil graag weten of deze technologie nuttig is voor AEM Publish Delivery- en Edge Delivery Services-projecten. Bovendien, laat ons weten wat u van plan bent om het als input in de product roadmap te gebruiken.

Sommige gebruiksgevallen:
* Verificatie met een IdP om toegang tot inhoud te verkrijgen
* Dynamische (gepersonaliseerde, gelokaliseerde) inhoud renderen op basis van geolocatie, apparaattype, gebruikerskenmerken, enz.
* Geavanceerde beeldmanipulatie
* Middleware tussen CDN en een oorsprong
* Een laag tussen de browser en een externe API, bijvoorbeeld om de API-reactie opnieuw op te maken
* Gegevens van meerdere origines samenvoegen om het voor de clientbrowser eenvoudiger te maken om deze te renderen

E-mail [ aemcs-edgecompute-feedback@adobe.com ](mailto:aemcs-edgecompute-feedback@adobe.com) met vragen en commentaren!

### API&#39;s op basis van OpenAPI&#39;s - Vroege adopter-programma {#open-apis-earlyadopter}

Ontwikkelaars kunnen AEM als Cloud Service-functies diep integreren in hun eigen toepassingen en tools. Nieuwe AEM as a Cloud Service API&#39;s volgen de OpenAPI-specificatie, met als doel consistent, goed gedocumenteerd en gebruikersvriendelijk te zijn. De geloofsbrieven voor eindpunten die authentificatie vereisen worden geproduceerd door de projecten van Adobe Developer Console te creëren.

Leer meer over [ OpenAPI-Gebaseerde AEM APIs ](/help/implementing/developing/open-api-based-apis.md) en probeer uit een [ leerprogramma van begin tot eind ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) die configuratie en gebruik illustreren.

Concreet zijn de API-eindpunten die hieronder worden vermeld, beschikbaar als onderdeel van een programma voor vroege adoptie. Als geinteresseerd, e-mail [ aem-apis@adobe.com ](mailto:aem-apis@adobe.com) beschrijvend hoe u van hen van plan bent gebruik te maken.

* [ de Fragmenten APIs van de Inhoud van Plaatsen ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)
* [ Assets APIs ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* [ Plaatsen en de Omslagen APIs van Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/folders/)
* [ Communicatie APIs van Forms ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### New AEM Developer Console (Public Beta) {#aem-developer-console-beta}

Probeer uit een vernieuwde [ AEM Developer Console ](/help/implementing/developing/introduction/aem-developer-console.md), die een meer interactieve ervaring voor het zuiveren van code in de milieu&#39;s van de Wolk aanbiedt.

Iedereen kan tot de openbare bèta toegang hebben door de *Nieuwe Beschikbare Console* knoop van de Console in huidige AEM Developer Console te klikken. Adobe verwelkomt terugkoppelen, die u aan [ aemcs-new-devconsole-ui-beta@adobe.com ](mailto:aemcs-new-devconsole-ui-beta@adobe.com) kunt e-mailen

## [!DNL Experience Manager] Hulplijnen {#guides}

U kunt een volledige lijst van nieuwe en verbeterde eigenschappen van de recentste versie van Adobe Experience Manager Guides [ hier ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2410-release/2410-0-release/whats-new-2024-10-0) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.

## Universele editor {#universal-editor}

U kunt een volledige lijst van Universele versies van de Redacteur [ hier ](/help/release-notes/universal-editor/current.md) vinden.

## Variaties genereren {#generate-variations}

U kunt een volledige lijst van Generate de versies van Variaties [ hier ](/help/generative-ai/release-notes-generate-variations.md) vinden.

## Opmerkingen bij de release van Experience Cloud {#experience-cloud}

U kunt informatie over versies van andere toepassingen van Experience Cloud [ hier ](https://experienceleague.adobe.com/en/docs/release-notes/experience-cloud/current) vinden.
