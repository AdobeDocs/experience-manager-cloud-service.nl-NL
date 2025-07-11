---
title: Nota's van de versie voor 2025.4.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2025.4.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 48e09824-5c67-49d8-8896-358d679649fc
source-git-commit: c8391e09b7e2888423187f48360423c52b18fe0a
workflow-type: tm+mt
source-wordcount: '1828'
ht-degree: 0%

---

# Opmerkingen bij de release 2025.4.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2025.4.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies, zoals 2023 of 2024, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [ Update van het Product van de Prioriteit Adobe ](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2025.4.0) is 24 april 2025. De volgende release met functies (2025.5.0) is gepland voor 5 juni 2025.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van april 2025 voor een overzicht van de functies die zijn toegevoegd in de release van 2025.4.0:

>[!VIDEO](https://video.tv.adobe.com/v/3464008?quality=12&captions=dut)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in Experience Manager Sites {#enhancements-sites}

**Nieuwe ModelAdmin UI van het Fragmentmodel van het Inhoud**

Als u de lijst met nieuwe gebruikersinterfaces aan de clientzijde verder invult wanneer u werkt met AEM Content Fragments, is er nu een nieuwe beheerinterface beschikbaar voor modellen van inhoudsfragmenten. De nieuwe UI verstrekt een schone en moderne lijstmening die het zoeken van modellen met filters toestaat, en die modelmarkeringen toont en welke inhoudsfragmenten bestaan die op een bepaald model gebaseerd zijn. De documentatie kan [ hier ](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md) worden gevonden.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Dynamische media (Scene7) {#dynamic-media-scene7}

**Dynamische Media (Scene7) niet gesteund in de Verbeterde milieu&#39;s van de Veiligheid**

Dynamic Media (Scene7) op AEM as a Cloud Service is niet geschikt voor HIPAA en kan niet worden gebruikt in AEM-omgevingen waar uitgebreide beveiliging is ingeschakeld.

Vanaf de release van AEM as a Cloud Service van april 2025 voorkomt een technische beperking dat Dynamic Media (Scene7) wordt geconfigureerd in omgevingen met uitgebreide beveiliging. Dientengevolge, is de **Dynamische 1&rbrace; kaart van de Configuratie van Media onder** Hulpmiddelen **>** de Diensten van de Wolk **niet meer zichtbaar in deze milieu&#39;s.**

Bovendien, zouden de klanten die AEM 6.5 gebruiken zich ervan bewust moeten zijn dat de Dynamische stapel van Media (Scene7) niet HIPAA-klaar is.

### Dynamic Media Classic {#dynamic-media-classic}

**Meldend**

Het tabblad Bandbreedte in het Dynamic Media Classic-rapportagedashboard wordt niet meer ondersteund vanaf april 2025.

Zie [ Bandbreedte en Opslag, Types van rapporten ](https://experienceleague.adobe.com/nl/docs/dynamic-media-classic/using/setup/administration-setup#types-of-reports).

## Nieuwe functies in Assets View {#new-features-assets-view}

**Betrekkingen van Activa**

De Assets-weergave biedt nu ondersteuning voor het weergeven en bewerken van relaties met middelen in een vereenvoudigd deelvenster met gegevens over elementen. Voeg eenvoudig relaties zoals Source en Derivative toe aan inhoud, zodat gebruikers op een effectievere manier relevante hoofdinhoud kunnen vinden.

![ Assets relatievoorbeeld ](/help/assets/assets/asset-relations-example.png)

**vergelijkt versies van een activa**

Met de Assets-weergave kunt u nu snel elke versie van een element selecteren en vergelijken met de meest recente versie.

![ vergelijk versies van activa ](/help/assets/assets/version-compare2.png)


## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Functies vóór de release

* [ Universele Redacteur voor AanpassingsForms en de Fragmenten van de Vorm ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md): De Universele Redacteur steunt nu de verwezenlijking van zowel AanpassingsForms als herbruikbare Fragments van de Vorm. Auteurs kunnen visueel formulieren maken, verzendacties configureren en reCAPTCHA-validatie toevoegen, allemaal in een vereenvoudigde WYSIWYG-ontwerpomgeving. Deze mogelijkheid versnelt het maken van formulieren, verbetert de consistentie en verbetert de bescherming tegen spam en geautomatiseerd misbruik.

* [ de Bibliotheek van het Document van SharePoint - sparen Bijlagen met Oorspronkelijke Filenames ](/help/forms/connect-forms-to-sharepoint-document-library.md#connect-an-adaptive-form-to-microsoft-sharepoint-document-library): U hebt nu de optie om vormgehechtheid te bewaren gebruikend hun originele filenames wanneer het opslaan van hen in een Bibliotheek van het Document van SharePoint. Deze verbetering vereenvoudigt de identificatie en het beheer van geüploade bestanden.

* **Redacteur van de Regel**:
   * [ Binaire Voorwaarde met de Gebeurtenis van de Klik in &quot;wanneer&quot;Clausule ](/help/forms/rule-editor-core-components-events-operators.md#available-operator-types-and-events-in-rule-editor): De Redacteur van de Regel staat nu toe combinerend een gebeurtenis van de knoopklik (_wordt geklikt_) met andere voorwaarden binnen de &quot;wanneer&quot;clausule. Dit laat nauwkeurigere controle over regeluitvoering toe die op gebruikersinteractie en andere factoren wordt gebaseerd. Opmerking: wanneer u meerdere voorwaarden gebruikt, moet de gebeurtenis click de eerste weergegeven voorwaarde zijn.
   * [ de Voorwaarden van de Bevestiging voor Gebieden en Comités ](/help/forms/rule-editor-core-components-usecases.md): De Redacteur van de Regel omvat nu _IsValid_ en _IsNotValid_ voorwaarden. Hiermee kunt u de validatiestatus controleren van specifieke velden of volledige deelvensters (zoals lay-outs zoals Horizontale tabbladen, Verticale tabbladen, Accordeons en Wizards), waardoor de navigatie en gebruikerservaring van formulieren op basis van validatieresultaten wordt verbeterd.
* [ Verbeterd Beheer van het Toepassingsgebied voor de Lijsten van SharePoint ](/help/forms/connect-forms-to-sharepoint-list.md): De plaatsen van SharePoint steunen nu alle beheerde wegen, bijvoorbeeld, /sites en /teams. Deze verbetering maakt een bredere integratie mogelijk in verschillende SharePoint-sitestructuren, waardoor u flexibeler kunt werken met organisatorische inhoud.
* [ Steun voor het Opslaan van Document van Verslag aan de Lijst van SharePoint ](/help/forms/generate-document-of-record-core-components.md#bind-adaptive-form-components-with-template-fields): Forms die gebruikend een op lijst-Gebaseerd Model van de Gegevens van de Vorm van SharePoint (FDM) wordt gecreeerd kan het Document van Verslag (DoR) aan de Lijsten van SharePoint nu opslaan door het Document van het het gebiedsbezit van de Verwijzing van de Bind van het Verslag te vormen. Dankzij deze verbetering kunnen ondersteunde formuliergegevens en -documenten naadloos worden geïntegreerd met SharePoint-opslag.
* [ auto-Toewijzing Steun voor de AanpassingsFragmenten van de Vorm ](/help/forms/adaptive-form-fragments-core-components.md#auto-mapping-support-for-fragments-in-an-adaptive-form): De adaptieve Forms steunt nu automatische toevoeging van passende fragmenten wanneer de schemavoorwerpen zich op een bepaalde fragmentstructuur richten, vormverwezenlijking stroomlijnen en hergebruik bevorderen.

### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties en om de ontwikkeling ervan vorm te geven.

Deze release bevat een overzicht van de innovaties die in de huidige release worden geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie &lbrace;de documentatie van het Programma van de Vroege Toegang van AEM Forms [.](/help/forms/early-access-ea-features.md)

#### Adobe Experience Platform (AEP) Integratie met Forms

* [ Integratie van AEM Forms met Adobe Experience Platform ](/help/forms/aem-forms-aep-connector.md): AEM Forms aan de Schakelaar van Adobe Experience Platform laat naadloze integratie tussen Aanpassings Forms en Adobe Experience Platform toe. Met deze functie kunnen formuliergegevens worden toegewezen aan XDM-schema&#39;s en in real-time rechtstreeks naar AEP worden verzonden. Het stroomlijnt gegevensvangst voor verpersoonlijking en activeringsgebruiksgevallen over de oplossingen van Adobe Experience Cloud.

## CIF-invoegtoepassing {#cloud-services-cif}

### Verbeteringen {#enhancements-cif}

* Selectie van productvarianten toevoegen voor referentietype van CIF-product
* **Experimental**: [ JSON+LD in de Componenten van de Kern van CIF in PDPs ](/help/commerce-cloud/customizing/json-ld.md)
* **Experimental**: [ de capaciteit van CIF om geheim voorgeheugen ](/help/commerce-cloud/configuring/clear-cache.md) te ontruimen

### Bugfixes {#bug-fixes-cif}

* Zoekprobleem in productveld verhelpen
* De URL-indeling van het product werkt niet zoals u had verwacht voor #variant_sku
* Kan niet meer dan 20 SKU&#39;s toevoegen aan de component Productlijst

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Op OpenAPI gebaseerde API&#39;s {#open-apis}

Ontwikkelaars kunnen AEM als Cloud Service-functies diep integreren in hun eigen toepassingen en tools. Nieuwe AEM as a Cloud Service API&#39;s volgen de OpenAPI-specificatie, met als doel consistent, goed gedocumenteerd en gebruikersvriendelijk te zijn. De geloofsbrieven voor eindpunten die authentificatie vereisen worden geproduceerd door de projecten van Adobe Developer Console tot stand te brengen en steun OAuth server-aan-Server, Web App, en Enige Pagina App (SPA).

[ zie de volledige lijst ](https://developer.adobe.com/experience-cloud/experience-manager-apis/#openapi-based-apis) van op OpenAPI-Gebaseerde APIs, [ meer ](/help/implementing/developing/open-api-based-apis.md) leren, en probeert uit een [ leerprogramma van begin tot eind ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/aem-apis/openapis/invoke-api-using-oauth-s2s) illustrerend configuratie en gebruik.

Bekijk deze video om te leren hoe u een geverifieerde API voor later gebruik kunt configureren:

>[!VIDEO](https://video.tv.adobe.com/v/3457510?quality=12&learn=on)

### Verbeteringen op gebied van CDN-configuratie {#cdn-enhancements}

Adobe-Beheerde CDN biedt flexibele configuratieopties aan, zoals die in het [ wordt beschreven Config Artikel van de Pijpleiding ](/help/operations/config-pipeline.md#configurations). Hier volgen enkele recente functies:

#### Aanvullende eigenschappen opnemen in CDN-logbestanden {#props-in-cdnlogs}

Nuttig voor scenario&#39;s met inbegrip van het zuiveren en gegevensanalyse, kunt u meer informatie in uw CDN- logboeken voorbij de standaardeigenschappen omvatten door de `logProperty` actie in [ verzoek en reactietransformaties ](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) te plaatsen.

#### Gebied, Continent en Organisatie-eigenschappen als overeenkomende voorwaarden {#matching-conditions}

CDN-regels kunnen nu op basis van regio, continent en organisatie overeenkomen voor gebruik, waaronder het blokkeren van verkeer en omleiding. `clientRegion` en `clientContinent` vergroten de reeds ondersteunde `clientCountry` overeenkomsten op basis van geografie, terwijl `clientAsName` en `clientAsNumber` overeenkomen met Autonomous Systems om grote ISP&#39;s, bedrijven of cloudproviders te identificeren. Leer meer over deze [ onlangs blootgestelde verzoekeigenschappen ](/help/security/traffic-filter-rules-including-waf.md#condition-structure).

#### Cookie-waarde instellen {#cookie-attributes}

U kunt koekjesattributen in [ reactietransformaties ](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) plaatsen.

### Java 21-ondersteuning {#java21}

Vanaf de release van januari kunt u code maken met Java 21 en Java 17. U krijgt toegang tot nieuwe functies zoals patroonaanpassing, verzegelde klassen en verschillende prestatieverbeteringen. Voor configuratiestappen, met inbegrip van het bijwerken van uw Gemaakt project en bibliotheekversies, zie het [ Milieu van de Bouwstijl ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#using-java-support) artikel.

Krachtigere Java 21 **runtime** wordt automatisch opgesteld wanneer Java 17 of 21 bouwt wordt ontdekt. Nochtans, beveelt Adobe ook het kiezen in Java 21 runtime voor milieu&#39;s aan die met Java 11 worden gebouwd, door [ aemcs-java-adopter@adobe.com ](mailto:aemcs-java-adopter@adobe.com) te e-mailen. Leer over [ Java 21 runtime vereisten ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).

>[!IMPORTANT]
>
> Java 21 **runtime** werd opgesteld aan uw milieu&#39;s dev/RDE in februari; het zal op uw stadium/productiemilieu&#39;s op **28 april en 29** worden toegepast. Merk op dat **bouwend code** met Java 21 (of Java 17) onafhankelijk van Java 21 runtime is — u moet stappen uitdrukkelijk nemen om code met Java 21 (of Java 17) te bouwen.

### Handhaving van het configuratiebeleid voor AEM Logging {#logconfig-policy}

AEM Java-logboeken moeten een consistente indeling hebben en mogen niet worden overschreven door aangepaste configuraties, zodat de omgeving van de klant effectief wordt gecontroleerd. De output van het logboek moet aan de standaarddossiers worden geleid. Voor AEM-productcode moeten de standaardlogniveaus worden behouden. Nochtans, is het aanvaardbaar om logboekniveaus voor klant-ontwikkelde code aan te passen.

Daartoe moeten de volgende OSGi-eigenschappen niet worden gewijzigd:
* **Apache Sling Logconfiguratie** (PID: `org.apache.sling.commons.log.LogManager`) — *alle eigenschappen*
* **Apache Sling Logging Logger Configuratie** (PID van de Fabriek: `org.apache.sling.commons.log.LogManager.factory.config`):
   * `org.apache.sling.commons.log.file`
   * `org.apache.sling.commons.log.pattern`

Medio mei zal AEM een beleid afdwingen waarbij eventuele aangepaste wijzigingen in deze eigenschappen worden genegeerd. Controleer uw downstreamprocessen en pas deze aan. Bijvoorbeeld, als u het logboek door:sturen eigenschap gebruikt:
* Als uw registrerenbestemming een douane (niet-gebrek) logboekformaat verwacht, kunt u uw spelingsregels moeten bijwerken.
* Als de veranderingen in logboekniveaus verminderde logboekbreedtegraad, zich ervan bewust zijn dat de standaardlogboekniveaus in een significante verhoging van logboekvolume kunnen resulteren.

### AEM Log Forwarding to More Destination - Beta Program {#log-forwarding-earlyadopter}

In bèta kunt u nu AEM-logboeken doorsturen naar New Relic (met behulp van HTTPS), Amazon S3 en Sumo Logic. AEM-logbestanden (inclusief Apache/Dispatcher) worden wel ondersteund, maar geen CDN-logbestanden. E-mail [ aemcs-logforwarding-beta@adobe.com ](mailto:aemcs-logforwarding-beta@adobe.com) voor toegang.

Hoewel de logboeken van Cloud Manager kunnen worden gedownload, vinden vele organisaties het nuttig om die logboeken aan een aangewezen registrerenbestemming te stromen. AEM biedt al ondersteuning voor het doorsturen van AEM- en CDN-logbestanden naar Azure Blob Storage, Datadog, HTTPS, Elasticsearch (en OpenSearch) en Splunk. Deze eigenschap wordt gevormd op een zelf-servermanier, en opgesteld gebruikend de Pijpleiding Config.

Leer meer in het [ logboek door:sturen documentatie ](/help/implementing/developing/introduction/log-forwarding.md).

### Edge Computing - Verzoek om feedback! {#edge-computing-feedback}

Edge Computing brengt gegevensverwerking dichter bij de browser, wat voordelen heeft, zoals minder latentie. Adobe wil graag weten of deze technologie nuttig is voor AEM Publish Delivery- en Edge Delivery Services-projecten. Bovendien, laat ons weten wat u van plan bent om het als input in de product roadmap te gebruiken.

Sommige gebruiksgevallen:

* Verificatie met een IdP om toegang tot inhoud te verkrijgen
* Personalization door dynamische inhoud te renderen op basis van geolocatie, apparaattype, gebruikerskenmerken, enz.
* Geavanceerde beeldmanipulatie
* Middleware tussen CDN en een oorsprong
* Een laag tussen de browser en een externe API, bijvoorbeeld om de API-reactie opnieuw op te maken
* Gegevens van meerdere origines samenvoegen om het voor de clientbrowser eenvoudiger te maken om deze te renderen

E-mail [ aemcs-edgecompute-feedback@adobe.com ](mailto:aemcs-edgecompute-feedback@adobe.com) met vragen en commentaren!

## [!DNL Experience Manager] Hulplijnen {#guides}

U kunt een volledige lijst van nieuwe en verbeterde eigenschappen van de recentste versie van Adobe Experience Manager Guides [ hier ](https://experienceleague.adobe.com/nl/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.

## Universele editor {#universal-editor}

U kunt een volledige lijst van Universele versies van de Redacteur [ hier ](/help/release-notes/universal-editor/current.md) vinden.

## Variaties genereren {#generate-variations}

U kunt een volledige lijst van Generate de versies van Variaties [ hier ](/help/generative-ai/release-notes-generate-variations.md) vinden.

## Opmerkingen bij de release van Experience Cloud {#experience-cloud}

U kunt informatie over versies van andere toepassingen van Experience Cloud [ hier ](https://experienceleague.adobe.com/nl/docs/release-notes/experience-cloud/current) vinden.
