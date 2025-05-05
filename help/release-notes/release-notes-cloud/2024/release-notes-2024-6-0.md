---
title: Nota's van de versie voor 2024.6.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2024.6.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 4033abf4-7094-4ce4-ba93-c936062667e3
source-git-commit: 650014d0c093b9e7c1947a8fe870a5452f3083e5
workflow-type: tm+mt
source-wordcount: '1972'
ht-degree: 0%

---

# Opmerkingen bij de release 2024.6.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2024.6.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2022 of 2023, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [ Update van het Product van de Prioriteit Adobe ](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2024.6.0) is 27 juni 2024. De volgende release met functies (2024.7.0) is gepland voor 25 juli 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van juni 2024 voor een overzicht van de functies die in de release van 2024.6.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3430779?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functie in Experience Manager Sites {#new-feature-sites}

**Echte Dienst van Gegevens van de Controle van het Gebruik (RUM)** {#real-use-monitoring}

De [ Echte Dienst van Gegevens van de Controle van het Gebruik (RUM) ](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) is nu algemeen beschikbaar, toelatend cliënt-zijgegevensinzameling voor AEM as a Cloud Service. Deze service biedt een nauwkeurigere weergave van gebruikersinteracties en zorgt voor een betrouwbare maatstaf voor de betrokkenheid van websites. Het biedt klanten geavanceerde inzichten in hun paginaverkeer en prestaties aan, die een waardevolle kans bieden om paginaprestaties te begrijpen en te verbeteren.

### Programma voor vroege adoptie {#sites-early-adopter}

**produceer Variaties**

Hefboomgaard GenAI door de nieuwe eigenschap van AEM, [ produceert variaties ](/help/generative-ai/generate-variations.md), nu toegankelijk in Cloud Service. Met het genereren van variaties kunt u inhoud genereren en schalen met behulp van generatieve AI. Neem contact op met uw Adobe-accountteam voor hulp in het programma.

**het doorbladeren van activa in de Console van het Fragment van de Inhoud**

Inhoudsauteurs kunnen nu door afbeeldingen en andere elementen bladeren, deze weergeven en deze activeren zonder dat ze de Content Fragment Console hoeven te verlaten.

![ het Bladeren van activa ](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Wilt u de functie proberen en feedback delen? Stuur een e-mail naar aemcs-headless-adopter@adobe.com vanuit uw officiële e-mailadres voor meer informatie over het programma voor vroege adoptie.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in Experience Manager Assets {#new-features-assets}



**Content Hub**

Content Hub is beschikbaar als onderdeel van Experience Manager Assets as a Cloud Service voor het democratiseren van de toegang tot online-inhoud voor organisaties en hun zakelijke partners. Met Content Hub kunt u eenvoudig middelen zoeken en distribueren, nieuwe on-brand variaties hergebruiken en maken en de activering op schaal versnellen.

![ Content Hub gebruikersinterface ](/help/release-notes/assets/content-hub-ui.png)

**Dynamische Media met Mogelijkheden OpenAPI**

Dynamic Media met OpenAPI-mogelijkheden breidt de DAM uit in Adobe- en externe toepassingen, waardoor toegang mogelijk is tot digitaal materiaal met een merk, in elk kanaal, via Asset Selector of OpenAPI-stack. Belangrijke elementen - geen binaire kopieën, elementen zijn geoptimaliseerd en getransformeerd aan de rand voor snelle prestaties, leveren elementen openbaar of veilig.

![ Nieuw Dynamisch diagram van de gegevensstroom van Media ](/help/assets/assets/dm-openapi-dfd.png)


### Nieuwe functies in de Assets-weergave {#assets-view-new-features}

**Meer opties zijn beschikbaar in het dashboard van de Inzichten van Assets**

Asset Count op type en grootte zijn nu beschikbaar op het Assets Insights-dashboard. Deze opties leveren realtime gegevens in uw Assets-weergaveomgeving. Ze geven een gedetailleerd overzicht van het aantal en het percentage van de elementen per grootteklasse en type element.

**Updates aan ingebedde redacteur van Adobe Express**

* Verbeterde gebruikerservaring voor het opslaan als een nieuw element in plaats van het opslaan als een nieuwe versie.

* Exporteren van uit meerdere pagina&#39;s bestaande Express-documenten (voorheen werd slechts één pagina ondersteund) in zowel PDF- als afbeeldingsindelingen met meerdere pagina&#39;s. Als u afbeeldingsindelingen selecteert, wordt elke pagina opgeslagen als een afzonderlijk element in de DAM voor downstreamdistributie.

* Ondersteuning voor het toevoegen van metagegevens in het dialoogvenster Opslaan terwijl u een element opslaat.

<!--


**Content Credentials**

Content Credentials feature in Assets view now provides detailed asset provenance data adhered to an asset. This helps to trace the enroute edits along the asset's lifecycle to prevent users from deception through deliberately tempered assets. This ensures content authenticity among users and fosters trust through transparency.

When looking at the asset details, any image with content credentials added, such as those created with GenAI, displays the manifest details in a dedicated panel. If the asset is downloaded, published, or shared, the credentials remain intact with the asset.

![check publish status1](/help/release-notes/assets/content-credentials.png)

-->

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Nieuwe functies in AEM Forms {#forms-new-prerelease-features}

#### Verbeterde Visual Rule Editor voor op kerncomponenten gebaseerde adaptieve Forms

Deze versie brengt een significante verbetering aan de Visuele Redacteur van de Regel voor adaptieve vormen die op kerncomponenten worden gebaseerd. U kunt nu het volgende doen:

* Creeer regels in de Visuele Redacteur van de Regel aan [ met voeten treden de standaardberichten van de vormvoorlegging succes/mislukking ](/help/forms/create-and-use-custom-functions.md#use-case-override-form-submission-success-and-error-handlers).

* In de Adaptieve Redacteur van de Regel van Forms, voegde de capaciteit toe om [ verschillende types van gebieden voor de WHEN verrichting ](/help/forms/rule-editor-core-components.md#allowed-multiple-fields-in-when) te selecteren.

* Een vormauteur kan douanefuncties op [ preprocess gegevens vóór voorlegging ](/help/forms/create-and-use-custom-functions.md#use-case-submit-altered-data-to-the-server) nu toepassen.

* Gebruik [**sparen als 1&rbrace; functionaliteit van het Ontwerp &lbrace;om gedeeltelijk voltooide vormen voor recentere voorlegging te bewaren.**](/help/forms/save-core-component-based-form-as-draft.md) Deze functionaliteit is handig in situaties waarin gebruikers het invullen van een formulier moeten onderbreken en er later op moeten terugkomen.

### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties voordat iemand anders ze ontwikkelt. Het programma biedt toegang tot meerdere innovaties.

Deze release bevat een overzicht van de innovaties die in de huidige release worden geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie &lbrace;de documentatie van het Programma van de Vroege Toegang van AEM Forms [&#128279;](/help/forms/early-access-ea-features.md).

#### Verbeterde methoden voor botbeveiliging

AEM Forms heeft zijn beveiligingsfuncties verbeterd door ondersteuning toe te voegen voor twee populaire CAPTCHA-oplossingen: Cloudflare Turnstile en hCaptcha. Deze functionaliteit is een aanvulling op de bestaande Google reCAPTCHA en biedt gebruikers extra opties. Het vergroot de flexibiliteit om hun formulieren te beschermen tegen bots en spam.

* **Wolkenflare Turnstile**: Dit frictionless CAPTCHA verifieert gebruikers door een eenvoudige uitdaging die geen expliciete interactie vereist. De toepassing wordt naadloos geïntegreerd in uw formulieren, waardoor de gebruikerservaring wordt verbeterd.
* **hCaptcha**: Deze privacy-geconcentreerde CAPTCHA biedt een gebruikersvriendelijk alternatief met een nadruk op gegevensprivacy aan. Het is bedoeld om een evenwicht te vinden tussen veiligheid en gebruikerservaring.
* **Google reCAPTCHA**: AEM Forms blijft zowel reCAPTCHA v2 als reCAPTCHA Onderneming steunen, die een betrouwbare en gevestigde oplossing aanbieden.

Door meerdere CAPTCHA-opties aan te bieden, hebt AEM Forms u de mogelijkheid om de oplossing te selecteren die het beste aansluit bij uw specifieke behoeften.

Klaar om een van deze CAPTCHA-oplossingen te integreren met uw Adaptive Forms? De documentatie van Adobe verstrekt gedetailleerde instructies voor elk: [ Cloudflare Turnstile ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-turnstile-core-components), [ hCaptcha ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-hcaptcha-core-components), en [ Google reCAPTCHA ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/captcha-adaptive-forms-core-components).


### Forms Service

Forms-service genereert een interactieve PDF forms voor het vastleggen van gegevens. Het kan ook worden gebruikt om gegevens te importeren of te exporteren naar en vanuit een bestaand interactief PDF-formulier en ingediende gegevens te valideren. Hier volgt een uitsplitsing van de functies:

* **teruggevend Forms**: Produceer een interactieve vorm van PDF van een malplaatje dat gebruikend AEM Forms Designer en, naar keuze, de gegevens van XML wordt gecreeerd. Met deze functie wordt een optioneel vooraf ingevuld PDF-formulier gemaakt.
* **Extractie en de Invoer van Gegevens**: De gegevens van de invoer in een bestaande vorm van PDF evenals extraheren gegevens uit een gevulde vorm van PDF. Zowel XDP- als XML-gegevensindelingen worden ondersteund en het importeren naar niet-XFA PDF forms (ook wel AcroForms genoemd) biedt daarnaast ondersteuning voor FDF- en XFDF-gegevens.
* **Bevestiging van Gegevens**: Valideer voorgelegde gegevens, in formaat XDP of van XML, tegen een malplaatje dat gebruikend AEM Forms Designer wordt gecreeerd.

>[!IMPORTANT]
>
> Als u in het aansluiten van bij het Vroege Programma van de Toegang van Adobe voor om het even welke vroege toegangsinnovatie geinteresseerd bent, verzend eenvoudig een e-mail van uw officieel adres aan [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com) om toegang te verzoeken. U kunt toegang vragen tot alle of tot specifieke innovaties.


## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Kennisgevingen van het Centrum voor activiteiten in verband met de gezondheid van de inhoud Vroege adopter-programma {#actions-center-notifications}

[ Centrum van Acties ](/help/operations/actions-center.md) verzendt e-mailberichten wanneer de belangrijke incidenten gebeuren, of als iets over uw code of configuratie wordt opgemerkt waar u proactieve actie zou moeten nemen. Adobe heeft nu verschillende nieuwe typen berichten geïntroduceerd die zijn gekoppeld aan de status van uw inhoud. Deze functie is beschikbaar via een programma voor vroege adoptie. Neem contact op met de klantenservice van Adobe om deel te nemen.

#### Pagina&#39;s bevatten veel knooppunten {#page-nodes}

Een groot aantal knooppunten kan de renderprestaties verlagen en de laadtijden van de pagina verminderen. Ontvang een pro-actieve melding via het Actions Center wanneer een groot aantal knooppunten op een pagina wordt gedetecteerd, zodat u de nodige stappen kunt ondernemen om het totale aantal knooppunten op een pagina te verminderen.

#### Groot aantal actieve workflowinstanties {#running-workflows}

De prestaties van de workflowengine worden beïnvloed wanneer er een groot aantal actieve workflows is in de ontwerpomgeving. U ontvangt een proactief bericht via het Actions Center wanneer een groot aantal actieve workflowinstanties wordt gedetecteerd. Met dit proces kunt u een opschoningstaak configureren om overbodige workflows te beëindigen.

#### Gebruikers die rechtstreeks aan aangepaste groepen zijn toegevoegd {#users-customgroups}

U ontvangt een proactief bericht via het Actions Center wanneer gebruikers rechtstreeks aan aangepaste groepen worden toegevoegd. Met dit proces kunt u de best practices van IMS volgen door gebruikers toe te voegen aan relevante IMS-groepen en deze IMS-groepen vervolgens op te nemen als leden van AEM-groepen.

#### Ontbrekende JCR-inhoud {#jcr-content}

Het Centrum van acties brengt u proactief op de hoogte wanneer het missen van inhoud JCR wordt ontdekt. Op deze manier kunt u de ontbrekende inhoud toevoegen en het mislukken van bepaalde AEM Assets-functies voorkomen.

#### Voltooide workflows niet gewist {#workflows}

Het Centrum van acties brengt proactief u op de hoogte wanneer voltooide werkschema&#39;s ouder dan 90 dagen niet zijn gezuiverd. Deze aanpak verbetert de prestaties van de workflowengine door het aantal workflowexemplaren te verminderen.

#### Ontbrekende verkoopbron {#sling-resource}

Het Centrum van acties brengt pro-actief u op de hoogte wanneer een ontbrekende het verdelen middel wordt ontdekt. Op deze manier kunt u de ontbrekende bron toevoegen en het mislukken van bepaalde AEM Assets-functies voorkomen.

### Inhoudsgerelateerde programma&#39;s voor vroege adoptie {#foundation-early-adopter}

E-mail **<aemcs-cdn-config-adopter@adobe.com>** waarin wordt aangegeven in welke van de onderstaande programma&#39;s voor vroege adoptie u geïnteresseerd bent.

#### Basisverificatie bij de CDN (programma voor vroege adopters) {#basicauth-cdn}

Bescherm bepaalde inhoudsbronnen door een standaarddialoogvenster weer te geven waarin een gebruikersnaam en wachtwoord zijn vereist. Deze eigenschap richt hoofdzakelijk lichte kwesties van het authentificatiegebruik, zoals bedrijfsbelanghebbenden die inhoud herzien, eerder dan het dienen als een uitvoerige oplossing voor de rechten van de eindgebruikertoegang. De lijst van gebruikersbenaming en wachtwoorden in beheerd door een configuratiedossier in git dat via de Pijpleiding van de Configuratie, met een verwijzing naar geheim-type de milieuvariabelen van Cloud Manager wordt opgesteld. [ leer meer ](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

#### Inhoud op de CDN wissen met een zelfbedieningsAPI-sleutel (programma voor vroege adopters) {#purge-cdn}

Registreer een CDN zuivering API sleutel op een zelfbediening manier, en gebruik het om inhoud bij CDN, of globaal, of voor één of meerdere middelen ongeldig te maken. [ leer meer ](/help/implementing/dispatcher/cdn-cache-purge.md).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Self-Serve Creation of X-AEM-Edge-Key for Customer-Managed CDN (BYOCDN) (Vroege-adopter-programma) {#byocdn-keys}

Eerder, was een steunkaartje nodig om X-AEM-Edge-Sleutel te produceren die voor configuratie van een klant-beheerde CDN wordt vereist. Dit resultaat kan nu op een zelfbediende manier door een configuratiedossier worden verwezenlijkt dat gebruikend de Pijpleiding van de Configuratie wordt opgesteld, verwijderend om het even welke vertraging in het aan boord gaan van een nieuw milieu. [ leer meer ](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Server-Side Redirects (Early-adopter-programma) {#server-side-redirects-early-adopter}

Vorm 301/302 server-zij richt in broncontrole, en stel aan CDN op. [ leer meer ](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> Merk op dat er verscheidene andere eigenschappen reeds beschikbaar met betrekking tot [ CDN configuratie ](/help/implementing/dispatcher/cdn-configuring-traffic.md) zijn, met inbegrip van verzoek en reactietransformaties, en verpletterend verkeer aan off-AEM plaatsen.

#### Waarschuwingen over verkeersfilterregels (vroege adopter-programma) {#traffic-filter-rules-alerts-early-adopter}

Onlangs vrijgegeven &lbrace;de Regels van de Filter van het Verkeer [&#128279;](/help/security/traffic-filter-rules-including-waf.md), die de naar keuze licentiebare regels van de Firewall van de Toepassing van het Web (WAF) omvatten, laat u vormen welk verkeer zou moeten worden toegestaan of worden ontkend.

Sluit zich aan bij het vroege adoptieprogramma zodat kunt u worden gealarmeerd wanneer uw regels van de verkeersfilter worden teweeggebracht. Met e-mailmeldingen van het Actions Center kunt u op de hoogte worden gehouden wanneer bepaalde verkeersvoorwaarden zich voordoen, zodat u de juiste maatregelen kunt nemen.

#### Zakelijke gebruikers kunnen omleidingen buiten Git declareren (vroege adopter-programma) {#apache-rewritemaps-early-adopter}

Net als AEM 6.5 voert Apache/dispatcher opnieuw schrijfkaarten in die op een specifieke locatie in de publicatieopslagplaats zijn geplaatst, en laadt ze, zonder dat een pijpleiding op een webniveau hoeft te worden uitgevoerd. Deze benadering laat bedrijfsgebruikers redirects verklaren gebruikend een spreadsheet of een UI, zoals ACS Commons Redirect de Manager van de Kaart of een douanetoepassing. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### Edge Side Includes (ESI) for Loading Dynamic Content (Early Introducter Program) {#esi-early-adopter}

Adobe beheerde CDN steunt nu [ de Zijde van Edge omvat (ESI) ](/help/implementing/dispatcher/edge-side-includes.md), een prijsverhogingstaal voor de dynamische assemblage van de Webinhoud van het randniveau. Door ESI fragmenten op te nemen, kunt u de algemene pagina van HTML bij CDN met hogere TTLs in het voorgeheugen plaatsen, terwijl het halen van uit oorsprong die kleinere secties die hogere toegangsupdates (lagere TTLs) vereisen. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

## [!DNL Experience Manager] Hulplijnen {#guides}

U kunt een volledige lijst van nieuwe en verbeterde eigenschappen van de recentste versie van Adobe Experience Manager Guides [ hier ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap) vinden.

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
