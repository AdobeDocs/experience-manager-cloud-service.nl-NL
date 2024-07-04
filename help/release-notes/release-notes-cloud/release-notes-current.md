---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige release voor [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 1566963898fb7f6999e3fad796b938128521bcce
workflow-type: tm+mt
source-wordcount: '1957'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de release met functies voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2022 of 2023, vrij te geven.
>
>Kijk eens naar de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie over de volgende activering van functies voor [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release met functies (2024.6.0) is 27 juni 2024. De volgende release met functies (2024.7.0) is gepland voor 25 juli 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

<!--  ## Release Video {#release-video}

Have a look at the June 2024 Release Overview video for a summary of the features added in the 2024.6.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3429503?quality=12)

-->

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functie in Experience Manager Sites {#new-feature-sites}

**Real Use Monitoring (RUM) Data Service** {#real-use-monitoring}

De [Real Use Monitoring (RUM) Data Service](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) is nu algemeen beschikbaar, waardoor gegevensverzameling aan de clientzijde voor AEM as a Cloud Service mogelijk is. Deze service biedt een nauwkeurigere weergave van gebruikersinteracties en zorgt voor een betrouwbare maatstaf voor de betrokkenheid van websites. Het biedt klanten geavanceerde inzichten in hun paginaverkeer en prestaties aan, die een waardevolle kans bieden om paginaprestaties te begrijpen en te verbeteren.

### Programma voor vroege adoptie {#sites-early-adopter}

**Variaties genereren**

Hefboomwerking GenAI door AEM nieuwe eigenschap, [variaties genereren](/help/generative-ai/generate-variations.md), nu toegankelijk in de Cloud Service. Met het genereren van variaties kunt u inhoud genereren en schalen met behulp van generatieve AI. Neem contact op met het accountteam van uw Adobe voor advies in het programma.

**Bladeren door middelen in de inhoudsfragmentconsole**

Inhoudsauteurs kunnen nu door afbeeldingen en andere elementen bladeren, deze weergeven en deze activeren zonder dat ze de Content Fragment Console hoeven te verlaten.

![Bladeren door middelen](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Wilt u de functie proberen en feedback delen? Stuur een e-mail naar aemcs-headless-adopter@adobe.com vanuit uw officiële e-mailadres voor meer informatie over het programma voor vroege adoptie.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in Experience Manager Assets {#new-features-assets}



**Content Hub**

Content Hub is beschikbaar als onderdeel van Experience Manager Assets as a Cloud Service voor het democratiseren van de toegang tot online-inhoud voor organisaties en hun zakelijke partners. Met Content Hub kunt u eenvoudig middelen zoeken en distribueren, nieuwe on-brand variaties hergebruiken en maken en de activering op schaal versnellen.

![Content Hub-gebruikersinterface](/help/release-notes/assets/content-hub-ui.png)

**Dynamic Media met OpenAPI-mogelijkheden**

Dynamic Media met OpenAPI-mogelijkheden breidt de DAM uit tussen Adobe- en externe toepassingen, waardoor toegang mogelijk is tot door een merk goedgekeurde digitale middelen in elk kanaal, via Asset Selector of OpenAPI-stack. Belangrijke elementen - geen binaire kopieën, elementen zijn geoptimaliseerd en getransformeerd aan de rand voor snelle prestaties, leveren elementen openbaar of veilig.

![Nieuw Dynamic Media-gegevensstroomdiagram](/help/assets/assets/dm-openapi-dfd.png)


### Nieuwe functies in de Assets-weergave {#assets-view-new-features}

**Meer opties zijn beschikbaar op het dashboard voor Assets-inzichten**

Asset Count op type en grootte zijn nu beschikbaar op het Assets Insights-dashboard. Deze opties leveren realtime gegevens in uw Assets-weergaveomgeving. Ze geven een gedetailleerd overzicht van het aantal en het percentage van de elementen per grootteklasse en type element.

**Updates voor ingesloten Adobe Express-editor**

* Verbeterde gebruikerservaring voor het opslaan als een nieuw element in plaats van het opslaan als een nieuwe versie.

* Exporteren van uit meerdere pagina&#39;s bestaande Express-documenten (voorheen werd slechts één pagina ondersteund) in zowel de PDF- als afbeeldingsindeling met meerdere pagina&#39;s. Als u afbeeldingsindelingen selecteert, wordt elke pagina opgeslagen als een afzonderlijk element in de DAM voor downstreamdistributie.

* Ondersteuning voor het toevoegen van metagegevens in het dialoogvenster Opslaan terwijl u een element opslaat.

<!--


**Content Credentials**

Content Credentials feature in Assets view now provides detailed asset provenance data adhered to an asset. This helps to trace the enroute edits along the asset's lifecycle to prevent users from deception through deliberately tempered assets. This ensures content authenticity among users and fosters trust through transparency.

When looking at the asset details, any image with content credentials added, such as those created with GenAI, displays the manifest details in a dedicated panel. If the asset is downloaded, published, or shared, the credentials remain intact with the asset.

![check publish status1](/help/release-notes/assets/content-credentials.png)

-->

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Nieuwe functies in AEM Forms {#forms-new-prerelease-features}

#### Verbeterde Visual Rule Editor voor op kerncomponenten gebaseerde adaptieve Forms

Deze versie brengt een significante verbetering aan de Visuele Redacteur van de Regel voor adaptieve vormen die op kerncomponenten worden gebaseerd. U kunt nu het volgende doen:

* Creeer regels in de Visuele Redacteur van de Regel aan [De standaardberichten voor het verzenden van formulieren met succes/fout negeren](/help/forms/create-and-use-custom-functions.md#use-case-override-form-submission-success-and-error-handlers).

* In de Adaptive Forms Rule Editor hebt u de mogelijkheid toegevoegd om [verschillende typen velden selecteren voor de WHEN-bewerking](/help/forms/rule-editor-core-components.md#allowed-multiple-fields-in-when).

* Een formulierauteur kan nu aangepaste functies toepassen op [gegevens voorafgaand aan verzending](/help/forms/create-and-use-custom-functions.md#use-case-submit-altered-data-to-the-server).

* Gebruik de [**Opslaan als concept**](/help/forms/save-core-component-based-form-as-draft.md) om gedeeltelijk ingevulde formulieren op te slaan en later te verzenden. Deze functionaliteit is handig in situaties waarin gebruikers het invullen van een formulier moeten onderbreken en er later op moeten terugkomen.

### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties voordat iemand anders ze ontwikkelt. Het programma biedt toegang tot meerdere innovaties.

Deze release bevat een overzicht van de innovaties die in de huidige release worden geleverd. Voor de volledige lijst van innovaties die beschikbaar zijn in het kader van het programma voor vroege toegang, zie [Documentatie over AEM Forms Early Access Program](/help/forms/early-access-ea-features.md).

#### Verbeterde methoden voor botbeveiliging

AEM Forms heeft zijn beveiligingsfuncties verbeterd door ondersteuning toe te voegen voor twee populaire CAPTCHA-oplossingen: Cloudflare Turnstile en hCaptcha. Deze functionaliteit is een aanvulling op de bestaande Google reCAPTCHA en biedt gebruikers extra opties. Het vergroot de flexibiliteit om hun formulieren te beschermen tegen bots en spam.

* **Cloudflare Turnstile**: Deze frictionless CAPTCHA verifieert gebruikers door een eenvoudige uitdaging die geen expliciete interactie vereist. De toepassing wordt naadloos geïntegreerd in uw formulieren, waardoor de gebruikerservaring wordt verbeterd.
* **hCaptcha**: Deze op privacy gerichte CAPTCHA biedt een gebruiksvriendelijk alternatief met focus op de privacy van gegevens. Het is bedoeld om een evenwicht te vinden tussen veiligheid en gebruikerservaring.
* **Google reCAPTCHA**: AEM Forms blijft zowel reCAPTCHA v2 als reCAPTCHA Enterprise ondersteunen en biedt een betrouwbare en gevestigde oplossing.

Door meerdere CAPTCHA-opties aan te bieden, hebt AEM Forms u de mogelijkheid om de oplossing te selecteren die het beste aansluit bij uw specifieke behoeften.

Klaar om een van deze CAPTCHA-oplossingen te integreren met uw Adaptive Forms? De documentatie van de Adobe bevat gedetailleerde instructies voor elk: [Cloudflare Turnstile](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-turnstile-core-components), [hCaptcha](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-hcaptcha-core-components), en [Google reCAPTCHA](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/captcha-adaptive-forms-core-components).


### Forms Service

Forms-service genereert interactieve PDF forms voor het vastleggen van gegevens. Het kan ook worden gebruikt om gegevens naar en van een bestaand interactief PDF formulier te importeren of te exporteren en ingediende gegevens te valideren. Hier volgt een uitsplitsing van de functies:

* **Forms renderen**: Genereer een interactief PDF-formulier op basis van een sjabloon die is gemaakt met AEM Forms Designer en eventueel XML-gegevens. Met deze functie wordt een optioneel vooraf ingevuld PDF-formulier gemaakt.
* **Gegevens extraheren en importeren**: Importeer gegevens in een bestaand PDF-formulier en extraheer gegevens uit een ingevuld PDF-formulier. Zowel XDP- als XML-gegevensindelingen worden ondersteund en het importeren naar niet-XFA-PDF forms (ook wel AcroForms genoemd) biedt daarnaast ondersteuning voor FDF- en XFDF-gegevens.
* **Gegevensvalidatie**: Valideer verzonden gegevens in XDP- of XML-indeling op basis van een sjabloon die is gemaakt met AEM Forms Designer.

>[!IMPORTANT]
>
> Als u geïnteresseerd bent in deelname aan het programma Vroege toegang van Adobe voor innovaties op het gebied van vroege toegang, stuurt u gewoon een e-mail van uw officiële adres naar [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) om toegang aan te vragen. U kunt toegang vragen tot alle of tot specifieke innovaties.


## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### Kennisgevingen van het Centrum voor activiteiten in verband met de gezondheid van de inhoud Vroege adopter-programma {#actions-center-notifications}

[Handelingencentrum](/help/operations/actions-center.md) verzendt e-mailberichten wanneer zich belangrijke incidenten voordoen of als er iets over uw code of configuratie wordt opgemerkt waar u proactieve actie moet ondernemen. Adobe heeft nu verschillende nieuwe typen berichten geïntroduceerd die zijn gekoppeld aan de status van uw inhoud. Deze functie is beschikbaar via een programma voor vroege adoptie. Neem contact op met de klantenservice van de Adobe om deel te nemen.

#### Pagina&#39;s bevatten veel knooppunten {#page-nodes}

Een groot aantal knooppunten kan de renderprestaties verlagen en de laadtijden van de pagina verminderen. Ontvang een pro-actieve melding via het Actions Center wanneer een groot aantal knooppunten op een pagina wordt gedetecteerd, zodat u de nodige stappen kunt ondernemen om het totale aantal knooppunten op een pagina te verminderen.

#### Groot aantal actieve workflowinstanties {#running-workflows}

De prestaties van de workflowengine worden beïnvloed wanneer er een groot aantal actieve workflows is in de ontwerpomgeving. U ontvangt een proactief bericht via het Actions Center wanneer een groot aantal actieve workflowinstanties wordt gedetecteerd. Met dit proces kunt u een opschoningstaak configureren om overbodige workflows te beëindigen.

#### Gebruikers die rechtstreeks aan aangepaste groepen zijn toegevoegd {#users-customgroups}

U ontvangt een proactief bericht via het Actions Center wanneer gebruikers rechtstreeks aan aangepaste groepen worden toegevoegd. Met dit proces kunt u de best practices van IMS volgen door gebruikers toe te voegen aan relevante IMS-groepen en deze IMS-groepen vervolgens als leden van AEM groepen op te nemen.

#### Ontbrekende JCR-inhoud {#jcr-content}

Het Centrum van acties brengt u proactief op de hoogte wanneer het missen van inhoud JCR wordt ontdekt. Op deze manier kunt u de ontbrekende inhoud toevoegen en het mislukken van bepaalde AEM Assets-functies voorkomen.

#### Voltooide workflows niet gewist {#workflows}

Het Centrum van acties brengt proactief u op de hoogte wanneer voltooide werkschema&#39;s ouder dan 90 dagen niet zijn gezuiverd. Deze aanpak verbetert de prestaties van de workflowengine door het aantal workflowexemplaren te verminderen.

#### Ontbrekende verkoopbron {#sling-resource}

Het Centrum van acties brengt pro-actief u op de hoogte wanneer een ontbrekende het verdelen middel wordt ontdekt. Op deze manier kunt u de ontbrekende bron toevoegen en het mislukken van bepaalde AEM Assets-functies voorkomen.

### Inhoudsgerelateerde programma&#39;s voor vroege adoptie {#foundation-early-adopter}

E-mail **<aemcs-cdn-config-adopter@adobe.com>**, waarin wordt aangegeven in welke van de onderstaande programma&#39;s voor vroege adoptie u geïnteresseerd bent.

#### Basisverificatie bij de CDN (programma voor vroege adopters) {#basicauth-cdn}

Protect bepaalde inhoudsbronnen door een standaarddialoogvenster weer te geven waarvoor een gebruikersnaam en wachtwoord vereist zijn. Deze eigenschap richt hoofdzakelijk lichte kwesties van het authentificatiegebruik, zoals bedrijfsbelanghebbenden die inhoud herzien, eerder dan het dienen als een uitvoerige oplossing voor de rechten van de eindgebruikertoegang. De lijst van gebruikersbenaming en wachtwoorden in beheerd door een configuratiedossier in git dat via de Pijpleiding van de Configuratie, met een verwijzing naar geheim-type de milieuvariabelen van Cloud Manager wordt opgesteld. [Meer informatie](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

#### Inhoud op de CDN wissen met een zelfbedieningsAPI-sleutel (programma voor vroege adopters) {#purge-cdn}

Registreer een CDN zuivering API sleutel op een zelfbediening manier, en gebruik het om inhoud bij CDN, of globaal, of voor één of meerdere middelen ongeldig te maken. [Meer informatie](/help/implementing/dispatcher/cdn-cache-purge.md).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Self-Serve Creatie van x-AEM-Edge-Sleutel voor klant-Beheerde CDN (BYOCDN) (Vroege Programma van de Aannemer) {#byocdn-keys}

Eerder, was een steunkaartje nodig om X-AEM-Edge-Sleutel te produceren die voor configuratie van een klant-beheerde CDN wordt vereist. Dit resultaat kan nu op een zelfbediende manier door een configuratiedossier worden verwezenlijkt dat gebruikend de Pijpleiding van de Configuratie wordt opgesteld, verwijderend om het even welke vertraging in het aan boord gaan van een nieuw milieu. [Meer informatie](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Client-Side Redirects (Early-adopter-programma) {#client-side-redirects-early-adopter}

Vorm 301/302 cliënt-zij richt in broncontrole, en stel aan CDN op. [Meer informatie](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> Er zijn al verschillende andere functies beschikbaar die betrekking hebben op [CDN-configuratie](/help/implementing/dispatcher/cdn-configuring-traffic.md), met inbegrip van verzoek en reactietransformaties, en verpletterend verkeer aan off-AEM plaatsen.

#### Waarschuwingen over verkeersfilterregels (vroege adopter-programma) {#traffic-filter-rules-alerts-early-adopter}

Onlangs vrijgegeven [Regels voor verkeersfilters](/help/security/traffic-filter-rules-including-waf.md), die de naar keuze licentiable regels van de Firewall van de Toepassing van het Web (WAF) omvatten, laat u vormen welk verkeer zou moeten worden toegestaan of worden ontkend.

Sluit zich aan bij het vroege adoptieprogramma zodat kunt u worden gealarmeerd wanneer uw regels van de verkeersfilter worden teweeggebracht. Met e-mailmeldingen van het Actions Center kunt u op de hoogte worden gehouden wanneer bepaalde verkeersvoorwaarden zich voordoen, zodat u de juiste maatregelen kunt nemen.

#### Zakelijke gebruikers kunnen omleidingen buiten Git declareren (vroege adopter-programma) {#apache-rewritemaps-early-adopter}

Net als AEM 6.5 voert Apache/dispatcher opnieuw schrijfkaarten in die op een specifieke locatie in de publicatieopslagplaats zijn geplaatst, en laadt ze, zonder dat een pijpleiding op een webniveau hoeft te worden uitgevoerd. Deze benadering laat bedrijfsgebruikers redirects verklaren gebruikend een spreadsheet of een UI, zoals ACS Commons Redirect de Manager van de Kaart of een douanetoepassing. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### Edge Side Includes (ESI) for Loading Dynamic Content (Early Introducter Program) {#esi-early-adopter}

De Adobe Beheerde CDN ondersteunt nu [Edge Side Includes (ESI)](/help/implementing/dispatcher/edge-side-includes.md), een opmaaktaal voor dynamische webinhoud-verzameling op randniveau. Door ESI fragmenten op te nemen, kunt u de algemene pagina van de HTML bij CDN met hogere TTLs in het voorgeheugen plaatsen, terwijl vaker het halen van van oorsprong die kleinere secties die hogere tijdigheidsupdates (lagere TTLs) vereisen. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

## [!DNL Experience Manager] Hulplijnen {#guides}

U vindt een volledige lijst met nieuwe en verbeterde functies van de nieuwste release van Adobe Experience Manager Guides [hier](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2406-release/whats-new-2024-06-0).

## Cloud Manager {#cloud-manager}

Een volledige lijst met maandelijkse Cloud Manager-releases vindt u [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

## Universele editor {#universal-editor}

U vindt een volledige lijst met Universal Editor-releases [hier](/help/release-notes/universal-editor/current.md).

## Variaties genereren {#generate-variations}

U kunt een volledige lijst vinden van Generate de versies van Variaties [hier](/help/generative-ai/release-notes-generate-variations.md).

## Opmerkingen bij de release Experience Cloud {#experience-cloud}

U kunt informatie over versies van andere toepassingen van het Experience Cloud vinden [hier](https://experienceleague.adobe.com/en/docs/release-notes/experience-cloud/current).
Als u maandelijks een e-mailbericht wilt ontvangen over updates van opmerkingen bij de release van Experiencen Cloud, meldt u zich aan bij de [Adobe Prioriteit productupdate](https://www.adobe.com/subscription/priority-product-update.html).