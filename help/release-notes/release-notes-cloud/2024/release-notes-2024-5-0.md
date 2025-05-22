---
title: Nota's van de versie voor 2024.5.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2024.5.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 7b7a27f9-ba57-4eb2-9fcb-653b5213af04
source-git-commit: 8be0a9894bb5b3a138c0ec40a437d6c8e4bc7e25
workflow-type: tm+mt
source-wordcount: '1943'
ht-degree: 0%

---

# Opmerkingen bij de release 2024.5.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2024.5.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2022 of 2023, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=nl-NL) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2024.5.0) is 30 mei 2024. De volgende release met functies (2024.6.0) is gepland voor 27 juni 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van mei 2024 voor een overzicht van de functies die in de release van 2024.5.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3429503?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in sites {#sites-new-features}

#### AEM-vertaalintegratie {#translation-integration}

Handelingen en workflows voor het vertalen van inhoud activeren nu gebeurtenissen om relevante processtappen en statussen van externe toepassingen te kunnen volgen. De volgende gebeurtenissen worden gegenereerd. Gebruikers kunnen zich abonneren op gebeurtenissen met de Adobe Developer Console.

* `TRANSLATION_JOB_CREATED`
* `TRANSLATION_JOB_CONTENT_ADDITION_STARTED`
* `TRANSLATION_JOB_CONTENT_ADDITION_COMPLETED`
* `TRANSLATION_JOB_CONTENT_DELETION_STARTED`
* `TRANSLATION_JOB_CONTENT_DELETION_COMPLETED`
* `TRANSLATION_JOB_COMMITTED_FOR_TRANSLATION`
* `TRANSLATION_JOB_READY_FOR_REVIEW`
* `TRANSLATION_JOB_APPROVED`
* `TRANSLATION_JOB_COMPLETED`
* `TRANSLATION_JOB_CANCELLED`
* `TRANSLATION_JOB_ERROR`

#### Operationele telemetrieservice {#real-use-monitoring}

* **[de Operationele Dienst van Telemetrie is nu GA](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** toelatend cliënt-zijinzameling van gegevens voor AEM as a Cloud Service.
De Echte Dienst van de Controle van het Gebruik, de cliënt-zijinzameling, biedt een preciezere weerspiegeling van interactie aan, die een betrouwbare maat van websitebetrokkenheid verzekeren. Het laat klanten met geavanceerde inzichten in hun paginaverkeer en prestaties toe. Het is een geweldige kans om meer te weten te komen over de prestaties van uw pagina en meer inzicht te krijgen in de manier waarop u deze kunt verbeteren.

#### AEM Authoring voor Edge Delivery Services {#edge-enhancements}

Verbeterde stabiliteit en diverse verbeteringen voor een betere ontwerpervaring.

### Programma voor vroege adoptie {#sites-early-adopter}

**produceer Variaties**

Hefboomgaard GenAI door de nieuwe eigenschap van AEM, [ produceert variaties ](/help/generative-ai/generate-variations.md), nu toegankelijk in Cloud Service. Met het genereren van variaties kunt u inhoud genereren en schalen met behulp van generatieve AI. Neem contact op met uw Adobe-accountteam voor hulp in het programma.

**het doorbladeren van activa in de Console van het Fragment van de Inhoud**

Inhoudsauteurs kunnen nu door afbeeldingen en andere elementen bladeren, deze weergeven en deze activeren zonder dat ze de Content Fragment Console hoeven te verlaten.

![ het Bladeren van activa ](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Wilt u de functie proberen en feedback delen? Stuur een e-mail naar aemcs-headless-adopter@adobe.com vanuit uw officiële e-mailadres voor meer informatie over het programma voor vroege adoptie.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in de beheerweergave {#admin-view-new-features}

* WebM is nu een ondersteund uitvoerbestand in verwerkingsprofiel voor video.
* MP4 wordt nu ondersteund in de native integratie van AEM in Express (importeren en exporteren).

### Nieuwe functies in de Assets-weergave {#assets-view-new-features}

**publiceer activa aan AEM en Dynamische Media**

Experience Manager Assets laat u nu toe om snel [ activa aan Experience Manager en Dynamische Media ](/help/assets/publish-assets-to-aem-and-dm.md) te publiceren gebruikend de mening van Assets zonder aan de mening te schakelen Admin. U kunt elementen publiceren tijdens het uploaden, bladeren en zoeken in elementen.

![ controle publiceert status1 ](/help/assets/assets/check-publish-status1.png)

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Nieuwe functies voor pre-release in AEM Forms {#forms-new-prerelease-features}

#### Verbeterde Visual Rule Editor voor op kerncomponenten gebaseerde adaptieve Forms

Deze versie brengt een significante verbetering aan de visuele regelredacteur voor adaptieve vormen die op kerncomponenten worden gebaseerd. U kunt nu het volgende doen:

* Creeer regels in de Visuele redacteur van de Regel aan [ met voeten treden standaardberichten van de vormvoorlegging succes/mislukking ](/help/forms/create-and-use-custom-functions.md#use-case-override-form-submission-success-and-error-handlers).

* In de Adaptieve Redacteur van de Regel van Forms, voegde de capaciteit toe om [ verschillende types van gebieden voor de WHEN verrichting ](/help/forms/rule-editor-core-components.md#allowed-multiple-fields-in-when) te selecteren.

* Een vormauteur kan douanefuncties op [ preprocess gegevens vóór voorlegging ](/help/forms/create-and-use-custom-functions.md#use-case-submit-altered-data-to-the-server) nu toepassen.

* Gebruik [**sparen als 1&rbrace; functionaliteit van het Ontwerp &lbrace;om gedeeltelijk voltooide vormen voor recentere voorlegging te bewaren.**](/help/forms/save-core-component-based-form-as-draft.md) Dit is handig in situaties waarin gebruikers het invullen van een formulier moeten onderbreken en er later op moeten terugkomen.



### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties voordat iemand anders ze ontwikkelt. Het programma biedt toegang tot meerdere innovaties.

Deze release bevat een overzicht van de innovaties die in deze release zijn geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie &lbrace;de documentatie van het Programma van de Vroege Toegang van AEM Forms [&#128279;](/help/forms/early-access-ea-features.md).

#### Verbeterde methoden voor botbeveiliging

AEM Forms heeft zijn beveiligingsfuncties verbeterd door ondersteuning toe te voegen voor twee populaire CAPTCHA-oplossingen: Cloudflare Turnstile en hCaptcha. Dit voegt toe aan de reeds beschikbare Google reCAPTCHA, die gebruikers meer keus en flexibiliteit verleent om hun vormen tegen bots en spam voorlegging te beschermen.

* **de Draai van de Wolk**: Dit frictionless CAPTCHA verifieert gebruikers door een eenvoudige uitdaging die geen expliciete interactie vereist. De toepassing wordt naadloos geïntegreerd in uw formulieren, waardoor de gebruikerservaring wordt verbeterd.
* **hCaptcha**: Deze privacy-geconcentreerde CAPTCHA biedt een gebruikersvriendelijk alternatief met een nadruk op gegevensprivacy aan. Het is bedoeld om een evenwicht te vinden tussen veiligheid en gebruikerservaring.
* **Google reCAPTCHA**: AEM Forms blijft zowel reCAPTCHA v2 als reCAPTCHA Onderneming steunen, die een betrouwbare en gevestigde oplossing aanbieden.

Door meerdere CAPTCHA-opties aan te bieden, hebt AEM Forms u de mogelijkheid om de oplossing te selecteren die het beste aansluit bij uw specifieke behoeften.

Klaar om een van deze CAPTCHA-oplossingen te integreren met uw Adaptive Forms? Onze documentatie verstrekt gedetailleerde instructies voor elk: [ Cloudflare Turnstile ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-turnstile-core-components), [ hCaptcha ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-hcaptcha-core-components), en [ Google reCAPTCHA ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/captcha-adaptive-forms-core-components).


### Forms Service

Forms-service genereert een interactieve PDF forms voor het vastleggen van gegevens. Het kan ook worden gebruikt om gegevens te importeren of te exporteren naar en vanuit een bestaand interactief PDF-formulier en ingediende gegevens te valideren. Hier volgt een uitsplitsing van de functies:

* **teruggevend Forms**: Produceer een interactieve vorm van PDF van een malplaatje dat gebruikend AEM Forms Designer en, naar keuze, de gegevens van XML wordt gecreeerd. Hiermee wordt in feite een optioneel vooraf ingevuld PDF-formulier gemaakt dat kan worden ingevuld met gegevens.
* **Extractie en de Invoer van Gegevens**: De gegevens van de invoer in een bestaande vorm van PDF evenals extraheren gegevens uit een gevulde vorm van PDF. Zowel XDP- als XML-gegevensindelingen worden ondersteund en het importeren naar niet-XFA PDF forms (ook wel AcroForms genoemd) biedt daarnaast ondersteuning voor FDF- en XFDF-gegevens.
* **Bevestiging van Gegevens**: Valideer voorgelegde gegevens, in formaat XDP of van XML, tegen een malplaatje dat gebruikend AEM Forms Designer wordt gecreeerd.

>[!IMPORTANT]
>
> Als u in het aansluiten van bij ons programma van de Vroege Toegang voor om het even welke vroege toegangsinnovatie geinteresseerd bent, verzend eenvoudig een e-mail van uw officieel adres aan [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com) om toegang te verzoeken. U kunt toegang vragen tot alle of tot specifieke innovaties.


## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### OAuth Server-to-Server aanmeldingsondersteuning voor AEM-integratie met andere Adobe-oplossingen {#S2S-OAuth-credentials}

Adobe Developer Console wordt gebruikt om referenties te genereren voor toegang tot verschillende API&#39;s. Een van die referentietypen, de referenties van de serviceaccount (JWT), is vervangen door OAuth Server-to-Server-referenties, die nu door AEM Cloud Service worden ondersteund voor integratie met andere Adobe-oplossingen zoals Adobe Analytics en Adobe Target.

[ leest over de verval ](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md) en [ hoe te om de auteur UI van AEM te gebruiken ](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md) om integratie met andere oplossingen van Adobe te vormen.

### Verkeerspiek bij waarschuwingen over oorsprong {#traffic-spike-origin}

[ ontvang pro-actieve berichten ](/help/security/traffic-filter-rules-including-waf.md#traffic-spike-at-origin-alert) door het Centrum van Acties wanneer de verkeerspatronen bij de oorsprong van een aanval van DDoS indicatief zijn, toestaand u om de regels van de verkeersfilter te onderzoeken en te vormen.

### Nieuwe Eigenschappen voor RDEs {#RDE-new-features}

{de milieu&#39;s van de Snelle Ontwikkeling van 0} (RDEs) [&#128279;](/help/implementing/developing/introduction/rapid-development-environments.md) laten ontwikkelaars snel opstellen, herzien, en testveranderingen in de Wolk.  In de maand juni worden verschillende nieuwe functies geïntroduceerd. Wij nodigen u ook uit om rechtstreeks met de techniek van Adobe bij het [ kanaal van de Opmaak van RDE ](https://discord.com/channels/1131492224371277874/1245304281184079872) in dienst te nemen.


#### RDE-ondersteuning voor front-end code met gebruik van Sitethema&#39;s en Sitesjablonen {#rde-frontend}

[ RDEs steunt nu front-end code ](/help/implementing/developing/introduction/rapid-development-environments.md#deploying-themes-to-rde) die op [ plaatsthema&#39;s ](/help/sites-cloud/administering/site-creation/site-themes.md) en [ plaatsmalplaatjes ](/help/sites-cloud/administering/site-creation/site-templates.md) wordt gebaseerd, voor vroege adopters. Met RDEs, wordt dit gedaan gebruikend een richtlijn van de bevellijn, eerder dan a [ front-end pijpleiding ](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md).

#### Verbeterd registreren voor RDEs {#rde-logging}

Terwijl het zuiveren van code in RDE, kunnen de ontwikkelaars nu [ vormen en logboeken productiever ](/help/implementing/developing/introduction/rapid-development-environments.md#rde-logging) stromen, gebruikend de bevellijn, en zonder eigenschappen OSGI in versiecontrole te wijzigen. Functies:

* logboekniveaus declareren op een pakket- of klassenniveau
* het aanpassen van het formaat van de logboekoutput
* meerdere logbestanden tegelijk streamen

#### Verbeteringen voor RDE CLI {#rde-cli-enhancements}

De interface van de het bevellijn van RDE heeft sommige nieuwe eigenschappen, die de ontwikkelaarservaring verbeteren:

* [ het opstellingsbevel is interactief ](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools-interactive), makend het gemakkelijker om tussen organisaties, programma&#39;s en milieu&#39;s te kiezen. Het is nu ook mogelijk deze waarden op de opdrachtregel te overschrijven.
* [ stille wijze ](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) voor een minder uitgebreide output.
* [ json wijze ](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) voor nuttige output wanneer programmatically aangehaald.

### Nieuwe meldingen in het actiecentrum {#actions-center-notifications}

[ Centrum van Acties ](/help/operations/actions-center.md) verzendt e-mailberichten wanneer de belangrijke incidenten gebeuren, of als wij iets over uw code of configuratie opmerken waar u pro-actieve actie zou moeten nemen. Er zijn drie nieuwe typen meldingen:

* te veel uitgaande verbindingen door geavanceerde voorzien van een netwerkinfrastructuur
* gebruik van een verouderde indeling voor het toewijzen van gebruikers aan services
* er een potentiële DDoS-aanval gaande is

### Programma&#39;s voor vroege adoptie {#foundation-early-adopter}

E-mail **<aemcs-cdn-config-adopter@adobe.com>** waarin wordt aangegeven in welke van de onderstaande programma&#39;s voor vroege adoptie u geïnteresseerd bent.

#### Inhoud op de CDN wissen met een API-sleutel voor zelfbediening (programma voor vroege adopters) {#purge-cdn}

Registreer een CDN zuivering API sleutel op een zelfbediening manier, en gebruik het om inhoud bij CDN, of globaal, of voor één of meerdere middelen ongeldig te maken. [ leer meer ](/help/implementing/dispatcher/cdn-cache-purge.md).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Zelf-serververwezenlijking van x-AEM-Edge-Sleutel voor klant-beheerde CDN (BYOCDN) (het Vroege Programma van de Aannemer) {#byocdn-keys}

Eerder, was een steunkaartje nodig om X-AEM-Edge-Sleutel te produceren die voor configuratie van een klant-beheerde CDN wordt vereist. Dit kan nu op een zelfbediende manier door een configuratiedossier worden verwezenlijkt dat gebruikend de Pijpleiding van de Configuratie wordt opgesteld, verwijderend om het even welke vertraging in het aan boord gaan van een nieuw milieu. [ leer meer ](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Server-side omleidingen (Early-adopter-programma) {#server-side-redirects-early-adopter}

Vorm 301/302 server-zij richt in broncontrole, en stel aan CDN op. [ leer meer ](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> Merk op dat er verscheidene andere eigenschappen reeds beschikbaar met betrekking tot [ CDN configuratie ](/help/implementing/dispatcher/cdn-configuring-traffic.md) zijn, met inbegrip van verzoek en reactietransformaties, en verpletterend verkeer aan off-AEM plaatsen.

#### Waarschuwingen over verkeersfilterregels (vroege adopter-programma) {#traffic-filter-rules-alerts-early-adopter}

Onlangs vrijgegeven &lbrace;de Regels van de Filter van het Verkeer [&#128279;](/help/security/traffic-filter-rules-including-waf.md), die de naar keuze licentiebare regels van de Firewall van de Toepassing van het Web (WAF) omvatten, laat u vormen welk verkeer zou moeten worden toegestaan of worden ontkend.

Sluit zich aan bij het vroege adoptieprogramma zodat kunt u worden gealarmeerd wanneer uw regels van de verkeersfilter worden teweeggebracht. De e-mailberichten van het Centrum van acties zullen u op de hoogte houden wanneer bepaalde verkeersvoorwaarden voorkomen zodat kunt u aangewezen maatregelen nemen.

#### Zakelijke gebruikers kunnen omleidingen buiten Git declareren (programma voor vroege adoptie) {#apache-rewritemaps-early-adopter}

Net als AEM 6.5 neemt Apache/dispatcher herschrijfkaarten in die op een specifieke locatie in de publicatieopslagplaats zijn geplaatst en laadt deze kaarten, zonder dat een pijpleiding op een webniveau hoeft te worden uitgevoerd. Dit opent mogelijkheden voor een bedrijfsgebruiker om omleidingen te verklaren gebruikend of een spreadsheet of UI, zoals die aangeboden door ACS Commons Redirect de Manager van de Kaart of die als deel van een klantentoepassing wordt gecreeerd. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### Edge Side Includes (ESI) for Loading Dynamic Content (Early Introducter Program) {#esi-early-adopter}

Adobe beheerde CDN steunt nu [ de Zijde van Edge omvat (ESI) ](/help/implementing/dispatcher/edge-side-includes.md), een prijsverhogingstaal voor de dynamische assemblage van de Webinhoud van het randniveau. Door ESI fragmenten op te nemen, kunt u de algemene pagina van HTML bij CDN met hogere TTLs in het voorgeheugen plaatsen, terwijl het halen van uit oorsprong die kleinere secties die hogere toegangsupdates (lagere TTLs) vereisen. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

## [!DNL Experience Manager] Hulplijnen {#guides}

* **publiceer een onderwerp of zijn elementen aan een Fragment van de Ervaring**
Nu, staat Experience Manager Guides u toe om een onderwerp of zijn elementen aan een Fragment van de Ervaring te publiceren. Een ervaringsfragment is een modulaire inhoudseenheid waarin zowel de inhoud als de lay-out worden geïntegreerd.  De Fragmenten van de ervaring zijn nuttig en kunnen u helpen verenigbare en het in dienst nemen ervaringen tot stand brengen.
* **Mogelijkheid om de meta-gegevens van de onderwerpactiva tot de Inheemse output van PDF over te gaan**
U kunt de meta-gegevens van de onderwerpactiva toevoegen terwijl het produceren van de Eigen output van PDF. Deze eigenschap helpt u specifieke meta-gegevens voor verschillende onderwerpen, zoals de onderwerptitel en de auteur, aan de kopballen en footers van de onderwerppagina toevoegen.

Voor meer informatie over de nieuwe en verbeterde eigenschappen en kwesties die in de versie worden bevestigd, bekijk de [ versie van Experience Manager Guides roadmap ](https://experienceleague.adobe.com/nl/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.

## Opmerkingen bij de release van Experience Cloud {#experience-cloud}

U kunt informatie over versies van andere toepassingen van Experience Cloud [ hier ](https://experienceleague.adobe.com/nl/docs/release-notes/experience-cloud/current) vinden.
Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [ Update van het Product van de Prioriteit Adobe ](https://www.adobe.com/subscription/priority-product-update.html).
