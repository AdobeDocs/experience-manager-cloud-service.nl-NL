---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: b6061690fa278ccb883656cefd065d06ab924499
workflow-type: tm+mt
source-wordcount: '1767'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de release met functies voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Kijk eens naar de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie over de volgende activering van functies voor [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release met functies (2024.5.0) is 30 mei 2024. De volgende release met functies (2024.6.0) is gepland voor 27 juni 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van mei 2024 voor een overzicht van de functies die in de release van 2024.5.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3429503?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in sites {#sites-new-features}

**AEM Authoring voor Edge Delivery Services**

Verbeterde stabiliteit en diverse verbeteringen voor een betere ontwerpervaring.

### Programma voor vroege adoptie {#sites-early-adopter}

**Variaties genereren**

Hefboomwerking GenAI door AEM nieuwe eigenschap, [variaties genereren](/help/generative-ai/generate-variations.md), nu toegankelijk in de Cloud Service. Met het genereren van variaties kunt u inhoud genereren en schalen met behulp van generatieve AI. Neem contact op met het accountteam van uw Adobe voor advies in het programma.

**Bladeren door middelen in de inhoudsfragmentconsole**

Inhoudsauteurs kunnen nu door afbeeldingen en andere elementen bladeren, deze weergeven en deze activeren zonder dat ze de Content Fragment Console hoeven te verlaten.

![Bladeren door middelen](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Wilt u de functie proberen en feedback delen? Stuur een e-mail naar aemcs-headless-adopter@adobe.com vanuit uw officiële e-mailadres voor meer informatie over het programma voor vroege adoptie.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in de beheerweergave {#admin-view-new-features}

* WebM is nu een ondersteund uitvoerbestand in verwerkingsprofiel voor video.
* MP4 wordt nu ondersteund in de native integratie van AEM in Express (importeren en exporteren).

### Nieuwe functies in de weergave Elementen {#assets-view-new-features}

**Elementen publiceren naar AEM en Dynamic Media**

Met Experience Manager Assets kunt u nu snel [middelen publiceren naar Experience Manager en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md) de middelenweergave gebruiken zonder over te schakelen naar de beheerweergave. U kunt elementen publiceren tijdens het uploaden, bladeren en zoeken in elementen.

![publicatiestatus controleren1](/help/assets/assets/check-publish-status1.png)

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Nieuwe functies voor pre-release in AEM Forms {#forms-new-prerelease-features}

#### Verbeterde Visual Rule Editor voor op kerncomponenten gebaseerde adaptieve Forms

Deze versie brengt een significante verbetering aan de visuele regelredacteur voor adaptieve vormen die op kerncomponenten worden gebaseerd. U kunt nu het volgende doen:

* Creeer regels in de Visuele redacteur van de Regel aan [Standaardberichten voor het verzenden van formulieren negeren/mislukken](/help/forms/create-and-use-custom-functions.md#use-case-override-form-submission-success-and-error-handlers).

* In de Adaptive Forms Rule Editor hebt u de mogelijkheid toegevoegd om [verschillende typen velden selecteren voor de WHEN-bewerking](/help/forms/rule-editor-core-components.md#allowed-multiple-fields-in-when).

* Een formulierauteur kan nu aangepaste functies toepassen op [gegevens voorafgaand aan verzending](/help/forms/create-and-use-custom-functions.md#use-case-submit-altered-data-to-the-server).

* Gebruik de [**Opslaan als concept**](/help/forms/save-core-component-based-form-as-draft.md) om gedeeltelijk ingevulde formulieren op te slaan en later te verzenden. Dit is handig in situaties waarin gebruikers het invullen van een formulier moeten onderbreken en er later op moeten terugkomen.



### Functies voor vroege adopters in AEM Forms {#forms-new-early-adopter-features}

Het AEM Forms Early Introducter-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties voordat anderen die ontwikkelen.
Het programma biedt toegang tot meerdere innovaties.

Deze release bevat een overzicht van de innovaties die in deze release zijn geleverd. Voor de volledige lijst van innovaties die beschikbaar zijn in het kader van het programma voor vroegtijdige adoptie, zie [Documentatie over AEM Forms Early Introducter Program](/help/forms/early-adopter-ea-features.md).

#### Verbeterde methoden voor botbeveiliging

AEM Forms heeft zijn beveiligingsfuncties verbeterd door ondersteuning toe te voegen voor twee populaire CAPTCHA-oplossingen: Cloudflare Turnstile en hCaptcha. Dit voegt toe aan de reeds beschikbare Google reCAPTCHA, die gebruikers meer keus en flexibiliteit verleent om hun vormen tegen bots en spam voorlegging te beschermen.

* **Cloudflare Turnstile**: Deze frictionless CAPTCHA verifieert gebruikers door een eenvoudige uitdaging die geen expliciete interactie vereist. De toepassing wordt naadloos geïntegreerd in uw formulieren, waardoor de gebruikerservaring wordt verbeterd.
* **hCaptcha**: Deze op privacy gerichte CAPTCHA biedt een gebruiksvriendelijk alternatief met focus op de privacy van gegevens. Het is bedoeld om een evenwicht te vinden tussen veiligheid en gebruikerservaring.
* **Google reCAPTCHA**: AEM Forms blijft zowel reCAPTCHA v2 als reCAPTCHA Enterprise ondersteunen en biedt een betrouwbare en gevestigde oplossing.

Door meerdere CAPTCHA-opties aan te bieden, hebt AEM Forms u de mogelijkheid om de oplossing te selecteren die het beste aansluit bij uw specifieke behoeften.

Klaar om een van deze CAPTCHA-oplossingen te integreren met uw Adaptive Forms? Onze documentatie bevat gedetailleerde instructies voor elk van deze: [Cloudflare Turnstile](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-turnstile-core-components), [hCaptcha](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-hcaptcha-core-components), en [Google reCAPTCHA](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/captcha-adaptive-forms-core-components).


### Forms Service

Forms-service genereert interactieve PDF forms voor het vastleggen van gegevens. Het kan ook worden gebruikt om gegevens naar en van een bestaand interactief PDF formulier te importeren en ingediende gegevens te valideren. Hier volgt een uitsplitsing van de functies:

* **Forms renderen**: Genereer een interactief PDF-formulier op basis van een sjabloon die is gemaakt met AEM Forms Designer en eventueel XML-gegevens. Hiermee wordt in feite een optioneel vooraf ingevuld formulier met PDF gemaakt.
* **Gegevens extraheren en importeren**: Importeer gegevens in een bestaand PDF-formulier en extraheer gegevens uit een ingevuld PDF-formulier. Zowel XDP- als XML-gegevensindelingen worden ondersteund en het importeren naar niet-XFA-PDF forms (ook wel AcroForms genoemd) biedt daarnaast ondersteuning voor FDF- en XFDF-gegevens.
* **Gegevensvalidatie**: - Valideer verzonden gegevens in XDP- of XML-indeling op basis van een sjabloon die is gemaakt met AEM Forms Designer.

>[!IMPORTANT]
>
> Als u geïnteresseerd bent in deelname aan ons programma voor vroege adopters voor innovaties op het gebied van vroege adopters, stuurt u gewoon een e-mail van uw officiële adres naar [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) om toegang aan te vragen. U kunt toegang vragen tot alle of tot specifieke innovaties.


## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### OAuth Server-aan-Server geloofsbrieven steun voor AEM integratie met andere oplossingen van de Adobe {#S2S-OAuth-credentials}

Met Adobe Developer Console worden referenties gegenereerd voor toegang tot verschillende API&#39;s. Een van die referentietypen, de referenties van de Servicerekening (JWT), is vervangen door OAuth Server-to-Server-referenties, die AEM Cloud Service nu ondersteunt voor integratie met andere Adobe-oplossingen zoals Adobe Analytics en Adobe Target.

[Meer informatie over de afgekeurde afbeelding](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md) en [leren hoe u de gebruikersinterface van de AEM gebruikt](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md) om integratie met andere oplossingen van de Adobe te vormen.

### Verkeerspiek bij waarschuwingen over oorsprong {#traffic-spike-origin}

[Proactieve meldingen ontvangen](/help/security/traffic-filter-rules-including-waf.md#traffic-spike-at-origin-alert) door het Centrum van Acties wanneer de verkeerspatronen bij de oorsprong van een aanval wijzen DDoS, die u toestaan om de regels van de verkeersfilter te onderzoeken en te vormen.

### Nieuwe Eigenschappen voor RDEs {#RDE-new-features}

[Rapid Development Environment (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) Laat ontwikkelaars snel wijzigingen implementeren, evalueren en testen in de cloud. In de maand juni worden verschillende nieuwe functies geïntroduceerd. We nodigen u ook uit om rechtstreeks contact op te nemen met Adobe engineering op de [RDE Disorder-kanaal](https://discord.com/channels/1131492224371277874/1245304281184079872).


#### RDE-ondersteuning voor front-end code met gebruik van Sitethema&#39;s en Sitesjablonen {#rde-frontend}

[RDE&#39;s ondersteunen nu front-end code](/help/implementing/developing/introduction/rapid-development-environments.md#deploying-themes-to-rde) gebaseerd op [sitethema&#39;s](/help/sites-cloud/administering/site-creation/site-themes.md) en [sitesjablonen](/help/sites-cloud/administering/site-creation/site-templates.md), voor vroege adoptie. Met RDEs, wordt dit gedaan gebruikend een richtlijn van de bevellijn, eerder dan een [front-end pijpleiding](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md).

#### Verbeterd registreren voor RDEs {#rde-logging}

Tijdens het opsporen van fouten in code in een RDE kunnen ontwikkelaars nu [vorm en stroom logboeken productiever](/help/implementing/developing/introduction/rapid-development-environments.md#rde-logging), met gebruik van de opdrachtregel en zonder wijzigingen van de eigenschappen van OSGI in versiebeheer. Functies:

* logboekniveaus declareren op een pakket- of klassenniveau
* het aanpassen van het formaat van de logboekoutput
* meerdere logbestanden tegelijk streamen

#### Verbeteringen voor RDE CLI {#rde-cli-enhancements}

De interface van de het bevellijn van RDE heeft sommige nieuwe eigenschappen, die de ontwikkelaarservaring verbeteren:

* [de opdracht setup is interactief](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools-interactive), waardoor het gemakkelijker wordt te kiezen tussen organisaties, programma&#39;s en omgevingen. Het is nu ook mogelijk deze waarden op de opdrachtregel te overschrijven.
* [stille modus](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) voor een minder uitgebreide uitvoer.
* [json, modus](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) voor nuttige output wanneer aangehaald programmatically.

### Nieuwe meldingen in het actiecentrum {#actions-center-notifications}

[Handelingencentrum](/help/operations/actions-center.md) verzendt e-mailberichten wanneer zich belangrijke incidenten voordoen, of als er iets aan uw code of configuratie is waar u proactieve actie moet ondernemen. Er zijn drie nieuwe typen meldingen:

* te veel uitgaande verbindingen door geavanceerde voorzien van een netwerkinfrastructuur
* gebruik van een verouderde indeling voor het toewijzen van gebruikers aan services
* er een potentiële DDoS-aanval gaande is

### Programma&#39;s voor vroege adoptie {#foundation-early-adopter}

E-mail **<aemcs-cdn-config-adopter@adobe.com>**, waarin wordt aangegeven in welke van de onderstaande programma&#39;s voor vroege adoptie u geïnteresseerd bent.

#### Inhoud op de CDN wissen met een API-sleutel voor zelfbediening (programma voor vroege adopters) {#purge-cdn}

Registreer een CDN zuivering API sleutel op een zelfbediening manier, en gebruik het om inhoud bij CDN, of globaal, of voor één of meerdere middelen ongeldig te maken. [Meer informatie](/help/implementing/dispatcher/cdn-cache-purge.md).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Zelf-serververwezenlijking van x-AEM-rand-Sleutel voor klant-beheerde CDN (BYOCDN) (het Vroege Programma van de Aannemer) {#byocdn-keys}

Eerder, was een steunkaartje nodig om X-AEM-rand-Sleutel te produceren die voor configuratie van een klant-beheerde CDN wordt vereist. Dit kan nu op een zelfbediende manier door een configuratiedossier worden verwezenlijkt dat gebruikend de Pijpleiding van de Configuratie wordt opgesteld, verwijderend om het even welke vertraging in het aan boord gaan van een nieuw milieu. [Meer informatie](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Client-side omleidingen (Early-adopter-programma) {#client-side-redirects-early-adopter}

Vorm 301/302 cliënt-zij richt in broncontrole, en stel aan CDN op. [Meer informatie](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> Er zijn al verschillende andere functies beschikbaar die betrekking hebben op [CDN-configuratie](/help/implementing/dispatcher/cdn-configuring-traffic.md), met inbegrip van verzoek en reactietransformaties, en verpletterend verkeer aan off-AEM plaatsen.

#### Waarschuwingen over verkeersfilterregels (vroege adopter-programma) {#traffic-filter-rules-alerts-early-adopter}

Onlangs vrijgegeven [Regels voor verkeersfilters](/help/security/traffic-filter-rules-including-waf.md), die de naar keuze licentiable regels van de Firewall van de Toepassing van het Web (WAF) omvatten, laat u vormen welk verkeer zou moeten worden toegestaan of worden ontkend.

Sluit zich aan bij het vroege adoptieprogramma zodat kunt u worden gealarmeerd wanneer uw regels van de verkeersfilter worden teweeggebracht. De e-mailberichten van het Centrum van acties zullen u op de hoogte houden wanneer bepaalde verkeersvoorwaarden voorkomen zodat kunt u aangewezen maatregelen nemen.

#### Zakelijke gebruikers kunnen omleidingen buiten Git declareren (programma voor vroege adoptie) {#apache-rewritemaps-early-adopter}

Net als AEM 6.5 neemt Apache/dispatcher herschrijfkaarten op die op een specifieke locatie in de publicatieopslagplaats zijn geplaatst, en laadt ze, zonder dat een pijpleiding op een webniveau hoeft te worden uitgevoerd. Dit opent mogelijkheden voor een bedrijfsgebruiker om omleidingen te verklaren gebruikend of een spreadsheet of UI, zoals die aangeboden door ACS Commons Redirect de Manager van de Kaart of die als deel van een klantentoepassing wordt gecreeerd. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### Edge Side Includes (ESI) for Loading Dynamic Content (Early Introducter Program) {#esi-early-adopter}

De Adobe Beheerde CDN ondersteunt nu [Inclusief rand (ESI)](/help/implementing/dispatcher/edge-side-includes.md), een opmaaktaal voor dynamische webinhoud-verzameling op randniveau. Door ESI fragmenten op te nemen, kunt u de algemene pagina van de HTML bij CDN met hogere TTLs in het voorgeheugen plaatsen, terwijl vaker het halen van van oorsprong die kleinere secties die hogere tijdigheidsupdates (lagere TTLs) vereisen. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

#### Real Use Monitoring (RUM) Data Service (Early Introducter Program)

* **Real Use Monitoring (RUM) Data Service is nu GA(/help/implementing/cloud-manager/content-requests.md#real-use-monitoring-for-aem-as-a-cloud-service)** het toelaten van cliënt-zijinzameling van gegevens voor AEM as a Cloud Service.
De Echte Dienst van de Controle van het Gebruik, de cliënt-zijinzameling, biedt een preciezere weerspiegeling van interactie aan, die een betrouwbare maat van websitebetrokkenheid verzekeren. Het laat klanten met geavanceerde inzichten in hun paginaverkeer en prestaties toe. Het is een geweldige kans om meer te weten te komen over de prestaties van uw pagina en meer inzicht te krijgen in de manier waarop u deze kunt verbeteren.

## [!DNL Experience Manager] Hulplijnen {#guides}

U vindt een volledige lijst met nieuwe en verbeterde functies van de nieuwste versie van Adobe Experience Manager Guides [hier](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2404-release/whats-new-2024-04-0).

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
