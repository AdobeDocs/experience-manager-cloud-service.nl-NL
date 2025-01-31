---
title: De huidige Nota's van de Versie voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Huidige versienota's voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 52c3c780802025e0895bacc675ba60e97fdce4c5
workflow-type: tm+mt
source-wordcount: '1750'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies, zoals 2023 of 2024, vrij te geven.
>
>Heb een blik bij de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates over de versienota&#39;s van de Experience Cloud te ontvangen, onderteken aan de [ Update van het Product van de Prioriteit van de Adobe ](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2025.1.0) is 30 januari 2025. De volgende release met functies (2025.2.0) is gepland voor 27 februari 2025.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

<!-- 

## Release Video {#release-video}

Have a look at the January 2025 Release Overview video for a summary of the features added in the 2025.1.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

**de Redacteur van het Fragment van de Inhoud nu over het algemeen beschikbaar**

Werk eenvoudig samen met collega&#39;s wanneer het ontwerpen AEM de Fragmenten van de Inhoud door de nieuwe en gemoderniseerde opmerkingsdienst in de Redacteur van het Fragment van de AEM te gebruiken.
[ las meer ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/authoring?#commenting-on-your-fragment).

**de Redacteur van het Fragment van de Inhoud en de Interfaces van de Gebruiker Admin, bijgewerkte de versiessteun van AEM as a Cloud Service**

De minimaal ondersteunde AEM as a Cloud Service-versie voor de nieuwe gebruikersinterfaces van Inhoudsfragmentbeheer en Editor is nu 2023.8.13099. Eerdere versies van vóór de algemene beschikbaarheidsversie van de nieuwe gebruikersinterfaces worden niet meer gesteund

### Programma voor vroege adoptie {#sites-early-adopter}

**Verbeterde de Fragmenten van de Inhoud**

Verbeterd [ het Fragment van de Inhoud van verwijzingen voorzien met unieke op identiteitskaart-Gebaseerde verwijzingen ](/help/headless/graphql-api/uuid-reference-upgrade.md), die helpen om de vragen van GraphQL voor individuele inhoudsfragmenten te verzekeren kan stabiel blijven zelfs als het fragment naar een andere plaats werd verplaatst. Dit is nu mogelijk met &quot;ByID&quot;-query&#39;s. Terwijl de wegen kunnen veranderen, potentieel het breken &quot;ByPath&quot;vragen, UUIDs is stabiel. De nieuwe id&#39;s kunnen ook worden geretourneerd als eigenschappen in een query of andere toepasselijke API-aanvraag. Huidige beperking (2025.1): Paginaverwijzingen worden nog niet ondersteund met unieke id&#39;s. Als er in inhoudsfragmenten wordt verwezen naar pagina&#39;s, mag deze mogelijkheid niet worden gebruikt. De beperking wordt verwijderd in de volgende release van AEM as a Cloud Service.

**AEM REST OpenAPI voor levering van inhoudsfragmenten**

[ AEM REST OpenAPI voor de Levering van het Fragment van de Inhoud ](/help/headless/aem-rest-openapi-content-fragment-delivery.md) is nu beschikbaar voor AEM as a Cloud Service.

### Verouderde functies {#sites-deprecated}

#### SPA Editor {#spa-editor}

[ de Redacteur van de SPA ](/help/implementing/developing/hybrid/introduction.md) is afgekeurd voor nieuwe projecten die met versie 2025.1.0 beginnen. De SPA Editor blijft ondersteund voor bestaande projecten, maar mag niet worden gebruikt voor nieuwe projecten.

De voorkeur gaat nu uit naar editors voor het beheer van inhoud zonder kop in AEM:

* [ de Universele Redacteur ](/help/edge/wysiwyg-authoring/authoring.md) voor het visuele uitgeven.
* [ de Redacteur van het Fragment van de Inhoud ](/help/assets/content-fragments/content-fragments-managing.md) voor op vorm-gebaseerde het uitgeven.

#### PWA-functies {#pwa-features}

[ progressieve Web app (PWA) eigenschappen ](/help/sites-cloud/authoring/sites-console/enable-pwa.md) voor AEM Sites worden nu afgekeurd voor nieuwe projecten die met versie 2025.1.0 beginnen. Deze functie blijft ondersteund voor bestaande projecten, maar mag niet worden gebruikt voor nieuwe projecten

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in AEM Assets {#new-features-assets}

**de malplaatjes van Dynamic Media**

Pas de afbeelding- en tekstbanners direct aan met een gebruiksvriendelijke WYSIWYG Dynamic Media Template Editor door de URL in te sluiten in een toepassing van de eerste of derde partij, zodat u bijzonder aantrekkelijke ervaringen hebt met real-time updates van bannerinhoud.

![ dynamische vertoningen ](/help/assets/assets/dm-templates-smart-text-resize.png)

**de leveringsrapporten van Dynamic Media**

Verkrijg leveringsinzichten voor activa die door Dynamic Media worden geleverd, met inbegrip van activa-vlakke levering tellingen, verwijzingsdetails, activa wegen in AEM Assets, en unieke activa IDs. Genereer rapporten voor alle elementen in de AEM Assets-opslagplaats of specifieke maphiërarchieën. Met deze inzichten kunt u de ROI van geleverde elementen meten, de kanaalprestaties evalueren en geïnformeerde beslissingen nemen voor middelenbeheer.

![ dynamische vertoningen ](/help/assets/assets/referrer.png)

**Dynamic Media Multi-audio en titel**

[ Multi-caption en multi-audiospoorsteun voor video&#39;s in Dynamic Media ](/help/assets/dynamic-media/video.md#about-msma) - u kunt veelvoudige titels en veelvoudige audiosporen aan een primaire video nu gemakkelijk toevoegen. Dit betekent dat uw video&#39;s toegankelijk zijn voor een wereldwijd publiek. U kunt één gepubliceerde primaire video aanpassen aan een wereldwijd publiek in meerdere talen en de richtlijnen voor toegankelijkheid voor verschillende geografische regio&#39;s naleven. Auteurs kunnen de bijschriften en audiotracks ook beheren vanaf één tabblad in de gebruikersinterface.

**Dynamisch Aangepast Streamen over de steun van HTTP**

Nieuwe protocolondersteuning gestart (DASH - Dynamic Adaptive Streaming via HTTP) voor Adaptive streaming in Dynamic Media-video (met CMAF ingeschakeld):

* Adaptief streamen (DASH/HLS) zorgt voor een betere kijkervaring voor video&#39;s.

* DASH is het internationale standaardprotocol voor adaptieve videostreaming en wordt op grote schaal toegepast in de branche

**Betrekkingen van Activa**

De Assets-weergave biedt nu ondersteuning voor het weergeven en bewerken van relaties met middelen in een vereenvoudigd deelvenster met gegevens over elementen. Voeg eenvoudig relaties zoals Source en Derivative toe aan inhoud, zodat gebruikers op een effectievere manier relevante hoofdinhoud kunnen vinden.

**opnieuw verwerken activa**

De Assets-weergave ondersteunt nu het opwerken van middelen die beschikbaar zijn in een map. U kunt selecteren om of de **Volledige optie van het Proces** te gebruiken of geavanceerde opties, zoals, standaardvoorproefvertoningen, meta-gegevens, post-verwerkingswerkschema, en verwerkingsprofiel te gebruiken.

### Functies voor vroege toegang in AEM Assets {#early-access-features-assets}

**AI-Gegenereerde videotitels**

Door AI gegenereerde videobijschriften in Adobe Dynamic Media gebruiken kunstmatige intelligentie om automatisch bijschriften te genereren voor video-inhoud. Deze functie is ontworpen om de toegankelijkheid te verbeteren en de gebruikerservaring te verbeteren door nauwkeurige, real-time bijschriften te bieden. Bijschriften worden gegenereerd op basis van de originele audio, eventuele extra audiotracks of extra bijschriften die op het tabblad &quot;Bijschriften en audio&quot; op de pagina met video-eigenschappen staan. Met ondersteuning voor meer dan 60 talen kunt u bijschriften reviseren en een voorvertoning weergeven voordat u de video publiceert.

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in AEM Forms {#forms-new-features}

* **beheer Publicatie**: U kunt het &quot;Manage Publication&quot;werkschema gebruiken om vormen over milieu&#39;s, typisch van de auteursinstantie aan te publiceren en voorproefinstanties te publiceren. Gebruikers kunnen de publicatie van inhoud op een gestroomlijnde manier publiceren, ongedaan maken of plannen.

* **[auto-sparen een ontwerp voor de Componenten van de Kern baseerde Adaptieve Forms](/help/forms/save-core-component-based-form-as-draft.md)**: De gebruikers kunnen nu van een auto-sparen eigenschap profiteren die een gedeeltelijk voltooide vorm als ontwerp automatisch opslaat. Ze kunnen later terugkeren om de vulling op hetzelfde of een ander apparaat te voltooien. Met deze functie worden de conversietarieven voor organisaties verbeterd doordat het aantal gebruikers dat het formulier afsluit, wordt verminderd, omdat gebruikers niet vanaf het begin hoeven te beginnen met het invullen van het formulier.

* **[de redacteursverhogingen van de Regel](/help/forms/invoke-service-enhancements-rule-editor.md)**: Voor Aangepaste Forms die op de Componenten van de Kern wordt gebaseerd, kunt u de output van de Invoke Dienst gebruiken om drop-down opties te bevolken en herhaalbare of individuele panelen te plaatsen. Bovendien kan deze uitvoer worden gebruikt om andere velden te valideren.

* **[verbeter de Ervaring van de Gebruiker met de Knopen van de Navigatie in Comité Lay-outs](/help/forms/rule-editor-core-components-usecases.md#navigating-among-panels-using-button)**: U kunt navigatieknopen aan uw paneellay-outs, zoals Horizontale Lusjes, Verticale Lusjes, Accordeons, of Tovenaar nu toevoegen. Met deze knoppen vergroot u de gebruikerservaring door de overgangen tussen deelvensters te vereenvoudigen en de focus op het geselecteerde deelvenster te richten.


### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties en om de ontwikkeling ervan vorm te geven.

Deze release bevat een overzicht van de innovaties die in de huidige release worden geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie {de documentatie van het Programma van de Vroege Toegang van AEM Forms ](/help/forms/early-access-ea-features.md).[

#### [ HTML e-mailMalplaatjes in Aangepaste Forms ](/help/forms/html-email-templates-in-adaptive-forms.md)

Met Adaptive Forms kunt u e-mailsjablonen voor HTML gebruiken. Met e-mailsjablonen voor HTML kunt u rijke, persoonlijke en visueel aantrekkelijke e-mails verzenden wanneer een formulier wordt verzonden. Deze e-mailberichten kunnen worden aangepast met formuliergegevens en uitgebreid met behulp van verschillende e-mailtags, zoals afbeeldingen en koppelingen. Met Adaptief Forms kunt u een bestand uploaden dat een HTML-sjabloon bevat of een normale teksteditor gebruiken om deze sjablonen te maken.

![ HTML e-mailmalplaatjes ](/help/forms/assets/html-email.png)

#### Verbeterde ondersteuning voor cloudopslag: rechtstreekse PDF uploaden naar Azure Blob Storage

AEM Forms-API&#39;s voor documentgeneratie bieden nu ondersteuning voor het direct uploaden van gegenereerde PDF-documenten naar Azure Blob Storage. Deze verbetering stroomlijnt opslag en terugwinning, verbeterend efficiency en integratie met de werkschema&#39;s van de wolk.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Java 21-ondersteuning {#java21}

U kunt nu code maken met Java 21, die nieuwe functies bevat (bijvoorbeeld patroonovereenkomsten voor switch-instructies, verzegelde klassen) en prestatieverbeteringen. Java 17-builds worden ook nieuw ondersteund. Voor configuratiestappen, met inbegrip van het bijwerken van uw Gemaakt project en bibliotheekversies, zie het [ milieu ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support) artikel bouwen.

Krachtigere Java 21 **runtime** zal automatisch worden opgesteld wanneer Java 17 of 21 bouwt wordt ontdekt. Nochtans, adviseren wij ook opting in Java 21 runtime voor milieu&#39;s die met Java 11 worden gebouwd, door [ aemcs-java-adopter@adobe.com ](mailto:aemcs-java-adopter@adobe.com) te e-mailen. Leer over [ Java 21 runtime vereisten ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> Java 21 **runtime** zal geleidelijk aan **worden opgesteld alle** milieu&#39;s (behalve die reeds gebouwd met Java 17 of 21, die reeds runtime Java 21 hebben), die met zandbakken en dev/RDE in Februari, en toen stadium/productie in April beginnen.

### Sandbox-programma&#39;s ondersteunen configuratieleidingen {#sandbox-config-pipelines}

Sandbox-programma&#39;s bieden nu ondersteuning voor configuratieleidingen, die in Cloud Manager kunnen worden geconfigureerd om uw bestanden te implementeren die in git blijven bestaan.

[ Leer meer ](/help/operations/config-pipeline.md) over config pijpleidingen, die voor configuratie van CDN, logboek het door:sturen, en versie zuivert/het onderhoudstaken van de controlelogboek toestaan.

### API&#39;s op basis van OpenAPI&#39;s - Vroege adopter-programma {#open-apis-earlyadopter}

Ontwikkelaars kunnen AEM als functies voor Cloud Servicen diep integreren in hun eigen toepassingen en gereedschappen. Nieuwe AEM as a Cloud Service API&#39;s volgen de OpenAPI-specificatie, met als doel consistent, goed gedocumenteerd en gebruikersvriendelijk te zijn. De geloofsbrieven voor eindpunten die authentificatie vereisen worden geproduceerd door de projecten van Adobe Developer Console te creëren.

Leer meer over [ OpenAPI-Gebaseerde AEM APIs ](/help/implementing/developing/open-api-based-apis.md) en probeer uit een [ leerprogramma van begin tot eind ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) die configuratie en gebruik illustreren.

Concreet zijn de API-eindpunten die hieronder worden vermeld, beschikbaar als onderdeel van een programma voor vroege adoptie. Als geinteresseerd, e-mail [ aem-apis@adobe.com ](mailto:aem-apis@adobe.com) beschrijvend hoe u van hen van plan bent gebruik te maken.

* [ de Fragmenten APIs van de Inhoud van Plaatsen ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)
* [ Assets APIs ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* [ Plaatsen en de Omslagen APIs van Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/folders/)
* [ Communicatie APIs van Forms ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### Edge Computing - Verzoek om feedback! {#edge-computing-feedback}

Edge Computing brengt gegevensverwerking dichter bij de browser, wat voordelen heeft, zoals minder latentie. Adobe zou graag horen of deze technologie nuttig is voor AEM Publish Delivery- en Edge Delivery Services-projecten. Bovendien, laat ons weten wat u van plan bent om het als input in de product roadmap te gebruiken. E-mail [ aemcs-edgecompute-feedback@adobe.com ](mailto:aemcs-edgecompute-feedback@adobe.com) met vragen en commentaren!

### New AEM Developer Console (Public Beta) {#aem-developer-console-beta}

Probeer uit gevernieuwde [ AEM Developer Console ](/help/implementing/developing/introduction/aem-developer-console.md), die een meer interactieve ervaring voor het zuiveren van code in de milieu&#39;s van de Wolk aanbiedt.

Iedereen kan tot de openbare bèta toegang hebben door de *Nieuwe Beschikbare Console* knoop van de Console in huidige AEM Developer Console te klikken. De Adobe verwelkomt terugkoppelt, die u aan [ aemcs-new-devconsole-ui-beta@adobe.com ](mailto:aemcs-new-devconsole-ui-beta@adobe.com) kunt e-mailen

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

## Opmerkingen bij de release Experience Cloud {#experience-cloud}

U kunt informatie over versies van andere toepassingen van het Experience Cloud [ hier ](https://experienceleague.adobe.com/en/docs/release-notes/experience-cloud/current) vinden.
