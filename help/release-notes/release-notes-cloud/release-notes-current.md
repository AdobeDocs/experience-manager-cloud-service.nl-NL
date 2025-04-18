---
title: De huidige Nota's van de Versie voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Huidige versienota's voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: bbf66195593032eb2ccf073ec78685c9d9726235
workflow-type: tm+mt
source-wordcount: '1092'
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

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2025.3.0) is 27 maart 2025. De volgende release met functies (2025.4.0) is gepland voor 24 april 2025.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

<!-- 

## Release Video {#release-video}

Have a look at the February 2025 Release Overview video for a summary of the features added in the 2025.2.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in Dynamic Media {#new-features-dynamic-media}

**Lange vormsteun voor video&#39;s die gebruikend Dynamische Media met Open API** worden geleverd

Dynamische media met OpenAPI ondersteunt nu lange formuliervideo&#39;s. De lange formuliervideo&#39;s bieden ondersteuning voor maximaal 50 GB en 2 uur.

### Dynamic Media Classic {#dmc}

<!-- CARRY OVER TO APRIL 2025 RELEASE NOTES -->

Het tabblad Bandbreedte in het rapportagedashboard van Dynamic Media Classic wordt vanaf april 2025 niet meer ondersteund.

Zie [Bandbreedte en opslag, Typen rapporten](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/setup/administration-setup#types-of-reports).


## Nieuwe functies in de weergave Activa {#new-features-assets-view}


**Ondersteuning voor root-tags**

AEM Assets ondersteunt nu het toewijzen van een tag-eigenschap in een metagegevensvorm aan aangepaste metagegevens. Daarnaast kunt u als beheerder de beschikbaarheid van tags voor gebruikers beperken door de toegang tot een specifieke roottag en de tags die onder de roottag bestaan, te beperken.

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties en om de ontwikkeling ervan vorm te geven.

Deze release bevat een overzicht van de innovaties die in de huidige release worden geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie {de documentatie van het Programma van de Vroege Toegang van AEM Forms ](/help/forms/early-access-ea-features.md).[

#### HTML-e-mailsjablonen in Adaptive Forms

De adaptieve Forms staat u toe om [ e-mailmalplaatjes van HTML ](/help/forms/html-email-templates-in-adaptive-forms.md) te gebruiken. Met HTML-e-mailsjablonen kunt u rijke, persoonlijke en visueel aantrekkelijke e-mails verzenden wanneer een formulier wordt verzonden. Deze e-mailberichten kunnen worden aangepast met formuliergegevens en uitgebreid met behulp van verschillende e-mailtags, zoals afbeeldingen en koppelingen. Met Adaptief Forms kunt u een bestand uploaden dat een HTML-sjabloon bevat of een normale teksteditor gebruiken om deze sjablonen te maken.

![ HTML e-mailmalplaatjes ](/help/forms/assets/html-email.png)

#### Verbeterde ondersteuning voor cloudopslag: Direct PDF Uploaden naar Azure Blob Storage

De Generatie APIs van het Document van AEM Forms laat u [ geproduceerde documenten van PDF ](/help/forms/early-access-ea-features.md#doc-generation-api) aan Azure BlobOpslag direct uploaden. Deze verbetering stroomlijnt de opslag en opvraging, waardoor de efficiëntie en integratie met cloudworkflows worden verbeterd.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Java 21-ondersteuning {#java21}

Vanaf de release van januari kunt u code maken met Java 21 en Java 17. U krijgt toegang tot nieuwe functies zoals patroonaanpassing, verzegelde klassen en verschillende prestatieverbeteringen. Voor configuratiestappen, met inbegrip van het bijwerken van uw Gemaakt project en bibliotheekversies, zie het [ Milieu van de Bouwstijl ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support) artikel.

Krachtigere Java 21 **runtime** wordt automatisch opgesteld wanneer Java 17 of 21 bouwt wordt ontdekt. Adobe raadt echter ook aan om voor de Java 21-runtime te kiezen voor omgevingen die zijn gebouwd met Java 11, door aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com) te e-mailen[. Leer over [ Java 21 runtime vereisten ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> Java 21 **runtime** werd opgesteld aan uw milieu&#39;s dev/RDE in februari; het zal op uw stadium/productiemilieu&#39;s op **28 april en 29** worden toegepast. Merk op dat **bouwend code** met Java 21 (of Java 17) onafhankelijk van Java 21 runtime is — u moet stappen uitdrukkelijk nemen om code met Java 21 (of Java 17) te bouwen.

### AEM Log Forwarding to more destination - Beta Program {#log-forwarding-earlyadopter}

In bèta kunt u nu AEM-logboeken doorsturen naar New Relic (met behulp van HTTPS), Amazon S3 en Sumo Logic. AEM-logbestanden (inclusief Apache/Dispatcher) worden wel ondersteund, maar geen CDN-logbestanden. E-mail [ aemcs-logforwarding-beta@adobe.com ](mailto:aemcs-logforwarding-beta@adobe.com) voor toegang.

Hoewel de logboeken van Cloud Manager kunnen worden gedownload, vinden vele organisaties het nuttig om die logboeken aan een aangewezen registrerenbestemming te stromen. AEM biedt al ondersteuning voor het doorsturen van AEM- en CDN-logbestanden naar Azure Blob Storage, Datadog, HTTPS, Elasticsearch (en OpenSearch) en Splunk. Deze eigenschap wordt gevormd op een zelf-servermanier, en opgesteld gebruikend de Pijpleiding Config.

Leer meer in het [ logboek door:sturen documentatie ](/help/implementing/developing/introduction/log-forwarding.md).

### Edge Computing - Verzoek om feedback! {#edge-computing-feedback}

Edge Computing brengt gegevensverwerking dichter bij de browser, wat voordelen heeft, zoals minder latentie. Adobe wil graag weten of deze technologie nuttig is voor AEM Publish Delivery- en Edge Delivery Services-projecten. Laat ons bovendien weten waarvoor u het voor ogen heeft als input voor de productroadmap.

Enkele mogelijke gebruiksscenario&#39;s:

* Verificatie met een IdP om toegang tot inhoud te verkrijgen
* Dynamische (gepersonaliseerde, gelokaliseerde) inhoud renderen op basis van geolocatie, apparaattype, gebruikerskenmerken, enz.
* Geavanceerde beeldmanipulatie
* Middleware tussen CDN en een oorsprong
* Een laag tussen de browser en een API van derden, misschien om de API-respons opnieuw in te delen
* Gegevens van meerdere oorsprong samenvoegen om het voor de clientbrowser gemakkelijker te maken om deze weer te geven

Mail [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) met vragen en opmerkingen!

### OpenAPI-gebaseerde API&#39;s - Early Adopter-programma {#open-apis-earlyadopter}

Ontwikkelaars kunnen AEM as Cloud Service-functies diep integreren in hun eigen toepassingen en hulpprogramma&#39;s. Nieuwe AEM as a Cloud Service-API&#39;s volgen de OpenAPI-specificatie, met als doel consistent, goed gedocumenteerd en gebruiksvriendelijk te zijn. De geloofsbrieven voor eindpunten die authentificatie vereisen worden geproduceerd door de projecten van Adobe Developer Console te creëren.

Leer meer over [ OpenAPI-Gebaseerde AEM APIs ](/help/implementing/developing/open-api-based-apis.md) en probeer uit een [ leerprogramma van begin tot eind ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/openapis/invoke-api-using-oauth-s2s) die configuratie en gebruik illustreren.

Concreet zijn de API-eindpunten die hieronder worden vermeld, beschikbaar als onderdeel van een programma voor vroege adoptie. Als geinteresseerd, e-mail [ aem-apis@adobe.com ](mailto:aem-apis@adobe.com) beschrijvend hoe u van hen van plan bent gebruik te maken.

* [ de Fragmenten APIs van de Inhoud van Plaatsen ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)
* [ Assets APIs ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* [ Plaatsen en de Omslagen APIs van Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/folders/)
* [ Communicatie APIs van Forms ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### Nieuwe AEM Developer Console (openbare bèta) {#aem-developer-console-beta}

Probeer uit een vernieuwde [ AEM Developer Console ](/help/implementing/developing/introduction/aem-developer-console.md), die een meer interactieve ervaring voor het zuiveren van code in de milieu&#39;s van de Wolk aanbiedt.

Iedereen kan tot de openbare bèta toegang hebben door de *Nieuwe Beschikbare Console* knoop van de Console in huidige AEM Developer Console te klikken. Adobe verwelkomt terugkoppelen, die u aan [ aemcs-new-devconsole-ui-beta@adobe.com ](mailto:aemcs-new-devconsole-ui-beta@adobe.com) kunt e-mailen

## [!DNL Experience Manager] Hulplijnen {#guides}

U kunt een volledige lijst van nieuwe en verbeterde eigenschappen van de recentste versie van Adobe Experience Manager Guides [ hier ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2025-releases/2502-release/whats-new-2025-02-0) vinden.

<!-- THE FOLLOWING URL WAS USED ABOVE BUT IT WAS 404. IT WAS REPLACED WITH THE URL ABOVE 
(https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2410-release/2410-0-release/whats-new-2024-10-0). -->

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.

## Universele editor {#universal-editor}

Je kunt hier](/help/release-notes/universal-editor/current.md) een volledige lijst van Universal Editor-releases [vinden.

## Variaties genereren {#generate-variations}

U kunt hier](/help/generative-ai/release-notes-generate-variations.md) een volledige lijst van Generate Variations releases [vinden.

## Release-opmerkingen voor Experience Cloud {#experience-cloud}

U kunt informatie over versies van andere toepassingen van Experience Cloud [ hier ](https://experienceleague.adobe.com/en/docs/release-notes/experience-cloud/current) vinden.
