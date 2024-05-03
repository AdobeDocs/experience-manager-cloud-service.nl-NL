---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: ee16d3a0fe1fc93c215d31f7dea0e9c21e051350
workflow-type: tm+mt
source-wordcount: '1963'
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

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release met functies (2024.4.0) is 25 april 2024. De volgende release met functies (2024.5.0) is gepland voor 30 mei 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

<!-- ## Release Video {#release-video}

Have a look at the April 2024 Release Overview video for a summary of the features added in the 2024.4.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3428342?quality=12)

-->

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Programma voor vroege adoptie {#sites-early-adopter}

**Variaties genereren**

Hefboomwerking GenAI door AEM nieuwe eigenschap, [variaties genereren](/help/generative-ai/generate-variations.md), nu toegankelijk in de Cloud Service. Met het genereren van variaties kunt u inhoud genereren en schalen met behulp van generatieve AI. Neem contact op met het accountteam van uw Adobe voor advies in het programma.

**Bladeren door middelen in de inhoudsfragmentconsole**

Inhoudsauteurs kunnen nu door afbeeldingen en andere elementen bladeren, deze weergeven en deze activeren zonder dat ze de Content Fragment Console hoeven te verlaten.

![Bladeren door middelen](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Wilt u de functie proberen en feedback delen? Stuur een e-mail naar aemcs-headless-adopter@adobe.com vanuit uw officiële e-mailadres voor meer informatie over het programma voor vroege adoptie.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in de weergave Elementen {#assets-view-new-features}


**Contextueel zoeken**

U kunt nu ook [zoekmiddelen beschikbaar in de repository door tekstaanwijzingen te definiëren](/help/assets/search-assets-view.md#contextual-search). Experience Manager Assets transformeert automatisch die tekstherinneringen om filters te zoeken en toont de onderzoeksresultaten. Met het deelvenster Filters kunt u automatische filters weergeven en wijzigen om de zoekresultaten verder te beperken.

![Contextueel zoeken](/help/assets/assets/contextual-search-text-prompt1.png)

**Snelle videohandelingen**

Experience Manager Assets bevat nu [eenvoudige en intuïtieve videobewerkingsgereedschappen, aangedreven door Adobe Express](/help/assets/edit-videos-assets-view.md) om het hergebruik van inhoud te verhogen en de snelheid van de inhoud te versnellen. Tot de bewerkingsopties behoren bijsnijden, bijsnijden, het formaat van een video wijzigen en het omzetten van een MP4 in een GIF-bestand.

![video uitsnijden met Adobe Express](/help/assets/assets/adobe-express-crop-video.png)

**Dynamische uitvoeringen**

U kunt nu [dynamische uitvoeringen (inclusief slimme gewassen) weergeven en downloaden](/help/assets/renditions.md) in Experience Manager Assets. Dynamische uitvoeringen zijn aangepaste versies van afbeeldingselementen die in real-time worden gemaakt om aan specifieke behoeften te voldoen, zoals het formaat van afbeeldingen wijzigen op basis van de apparaatresolutie of het uitsnijden om aan verschillende hoogte-breedteverhoudingen te voldoen. Deze vertoningen stellen organisaties in staat om gepersonaliseerde en geoptimaliseerde ervaringen aan diverse publieksbehoeften te leveren.

![Dynamische uitvoeringen](/help/assets/assets/preset_smart_crop.png)

**Naam op plaats wijzigen voor elementen en mappen**

Experience Manager Assets biedt nu een vereenvoudigde gebruikerservaring door [mogelijkheid om de naam van een middel of een omslag te wijzigen door één klik](/help/assets/manage-organize-assets-view.md).

**Metagegevensformulier toewijzen aan of verwijderen uit meerdere mappen**

U kunt nu [metagegevensformulier toewijzen aan of verwijderen uit meerdere mappen](/help/assets/metadata-assets-view.md#assign-metadata-form-to-a-folder).



## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Nieuwe functies in AEM Forms {#forms-new-features}

* **Verbeterde Visual Rule Editor voor op kerncomponenten gebaseerde adaptieve Forms**: Deze release brengt een aanzienlijke upgrade naar de visuele regeleditor voor adaptieve formulieren op basis van kerncomponenten. Deze versie brengt een significante verbetering aan de visuele regelredacteur voor adaptieve vormen die op kerncomponenten worden gebaseerd. Deze update is gericht op het stroomlijnen van interacties met aangepaste functies, zodat u robuustere en efficiëntere formulieren kunt maken.

  U kunt aangepaste functieinteracties nu stroomlijnen door:

   * [Nieuwe annotaties gebruiken om duidelijkere functiedefinities te bieden](/help/forms/create-and-use-custom-functions.md#supported-javascript-annotations-for-custom-function).
   * [Het gebruik van caching mechanismen voor douanefuncties die tot snellere vormprestaties leiden](/help/forms/create-and-use-custom-functions.md#caching-support-for-custom-function).
   * [Naadloos werken met globale objecten binnen aangepaste functies](/help/forms/create-and-use-custom-functions.md#field-and-global-scope-objects-in-custom-functions).
   * [Optionele parameters definiëren en gebruiken binnen aangepaste functies](/help/forms/create-and-use-custom-functions.md#parameter).

  Deze update brengt ook de volgende verhogingen aan de functionaliteit van de regelredacteur. U kunt:

   * Krachtig implementeren [&quot;when-then-else&quot;](/help/forms/rule-editor-core-components.md#when) logica voor voorwaardelijke uitvoering.
   * Maak gebruik van moderne JavaScript-functies, zoals let- en pijlfuncties (ES10-ondersteuning).
   * Valideer of stel niet alleen gebieden, maar ook volledige panelen en vormen terug, die controle over gebruikersinteractie uitbreiden.

  Deze vooruitgang verstrekt een intuïtievere en krachtige ervaring voor het ontwerpen van regels en douanefuncties binnen de visuele regelredacteur.

* **[Meerdere versies van een adaptief formulier maken](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md)**: U kunt nu gemakkelijk variaties van bestaande formulieren beheren. Dit vereenvoudigt versiecontrole en vergemakkelijkt vergelijking voor vormoptimalisering, allen binnen één enkele, gestroomlijnde werkschema.

* **[Adaptief formulier vergelijken](/help/forms/compare-forms.md)**: U kunt nu gemakkelijk twee formulieren vergelijken om de verschillen tussen twee formulieren vast te stellen. Het vergemakkelijkt vlotte samenwerking door teamleden toe te laten om revisies te vergelijken en veranderingen efficiënt te bespreken.

* **Verbeterde toegankelijkheid voor componenten voor scriptbare handtekeningen**: Deze update biedt aanzienlijke toegankelijkheidsverbeteringen voor de component Scripthandtekening:

  **Verbeterde toetsenbordnavigatie:**
   * Als u op de Tab-toets drukt, kunnen gebruikers door alle interactieve elementen navigeren in het dialoogvenster Handtekening.
   * Het dialoogvenster wordt gesloten wanneer u ondertekent met een penseel of toetsenbord en op Enter drukt.
   * De focus blijft op het besturingselement voor handtekeningen nadat u hebt ondertekend en op &quot;OK&quot; hebt geklikt.

  **Handtekeningfunctionaliteit wissen:**

   * Een duidelijk kruispictogram voor het wissen van de handtekening is toegankelijk via de Tab-toets.
   * Het dialoogvenster Handtekeningbevestiging wissen is ook toegankelijk via tabnavigatie.

  **Verbeterde labels en besturingselementen:**
   * Het label voor de knop voor toetsenbordondertekening is nu duidelijker en met &quot;aria-label&quot; kunt u functionaliteit aankondigen (zoals &quot;aria-label=&#39;Ondertekenen met toetsenbord&#39;&#39;).
   * Het verbeterde contrast zorgt ervoor dat alle besturingselementen binnen de krabbelhandtekening gemakkelijk te onderscheiden zijn.
   * De knop OK/vinkje geeft nu visueel aan wanneer deze inactief is.

  **Feedback van handtekening voor Readers van scherm:**
   * Wanneer een handtekening wordt getypt, kunnen gebruikers van schermlezers de tekst horen die wordt gebruikt om de handtekening te maken.

Deze update zorgt voor een inclusievere ervaring voor gebruikers met een handicap door navigatie, helderheid en feedback voor de component Krabbelhandtekening te verbeteren.

### Programma voor vroege adoptie {#forms-early-adopter}

* **[Een adaptief formulier verzenden naar het Adobe Workfront Fusion-scenario](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service beschikt over een optie om een adaptief formulier moeiteloos aan te sluiten op Adobe Workfront. Dit vereenvoudigt het proces om een Adaptief Formulier aan een scenario van Adobe Workfront voor te leggen, toelatend u een scenario van de Fusie van Workfront op voorlegging van een Aangepast Vorm teweegbrengt.

  <br/> ![Adobe Workfront](/help/forms/assets/adobe-workfront.png) <br/> Met de Adobe Workfront Fusion Connector kunt u workflows ontwerpen die automatisch worden geactiveerd na verzending van een adaptief formulier. Stel bijvoorbeeld dat een workflow wordt gestart om een specifieke persoon de taak te geven de ingediende gegevens te beoordelen, zodat een aanvraag kan worden goedgekeurd of afgewezen op basis van de informatie die via het adaptieve formulier is vastgelegd. Deze gestroomlijnde integratie verbetert de efficiëntie en zorgt voor een nieuw niveau van automatisering van uw workflowprocessen.|

* **[Reader Extension Service](/help/forms/aem-forms-cloud-service-communications-introduction.md#reader-extension-service)**: AEM Forms Communication API&#39;s hebben de Extension Service van Readers geïntroduceerd zodat u functies zoals het invullen van formulieren en opmerkingen kunt toevoegen aan gewone PDF, waardoor ze interactief zijn voor gebruikers met de gratis Adobe Reader.

* [Ondersteuning voor talen van rechts naar links](/help/forms/supporting-new-language-localization-core-components.md): Adaptieve Forms die is gebaseerd op Core Components, kan nu worden weergegeven in een RTL-taal (rechts naar links), zoals Arabisch, Perzisch en Urdu. De RTL-talen worden wereldwijd gesproken door meer dan 2 miljard mensen. Door een formulier in RTL-taal te gebruiken, kunt u het bereik van uw adaptieve formulieren uitbreiden naar deze verschillende doelgroepen en selecteren in RTL-markten. In bepaalde regio&#39;s is het ook een wettelijk mandaat om formulieren in de lokale taal te verstrekken. Door lokale talen aan te passen, opent u niet alleen deuren voor een breder publiek, maar zorgt u ook voor naleving van relevante wetten en regels.

* **[Protect uw documenten met DocAssurance-API&#39;s (onderdeel van communicatie-API&#39;s)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: De DocAssurance-API&#39;s stellen u in staat gevoelige informatie te beveiligen door de documenten te ondertekenen en te versleutelen. Door versleuteling wordt de inhoud van een document omgezet in een onleesbare indeling, zodat alleen geautoriseerde gebruikers toegang hebben. Deze versterkte beschermingslaag beschermt niet alleen waardevolle gegevens tegen ongeoorloofde ogen, maar zorgt ook voor gemoedsrust. Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen.

  U kunt schrijven naar `aem-forms-ea@adobe.com` van uw officiële e-mailidentiteitskaart om zich bij het vroege adoptieprogramma aan te sluiten en toegang tot het vermogen te verzoeken.

* **[U kunt gebruikmaken van de gegevensservice Real User Monitoring (RUM)](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** om client-side verzameling voor AEM as a Cloud Service in te schakelen.
Real User Monitoring (RUM) Data Service biedt een nauwkeuriger weergave van gebruikersinteracties, waardoor een betrouwbare maatstaf voor de betrokkenheid van websites wordt geboden. Het is een geweldige kans om geavanceerde inzichten in uw paginaprestaties te krijgen. Terwijl dit voor klanten nuttig is die of Adobe-beheerde CDN of niet-Adobe-beheerde CDN gebruiken. Bovendien, voor klanten die een niet-Adobe beheerde CDN gebruiken, kan het geautomatiseerde verkeer nu voor hen worden toegelaten, waarbij de behoefte wordt verwijderd om het even welk verkeersrapport met Adobe te delen.

  Als je deze nieuwe functie wilt testen en je feedback wilt delen, stuur dan een e-mail naar `aemcs-rum-adopter@adobe.com`, samen met uw domeinnaam voor elk van de omgevingen waarvoor u RUM wilt inschakelen vanaf uw e-mailadres dat is gekoppeld aan uw Adobe ID. Het productteam van Adobe zal dan de Echte Dienst van Gegevens van de Controle van de Gebruiker (RUM) voor u toelaten.

## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### CDN-configuratie {#cdn-config}

Vorm verkeer bij Adobe CDN op de volgende manieren:

* [Transformaties aanvragen](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) - wijzig aspecten van inkomende verzoeken, met inbegrip van wegen, vraagparameters, en de kopballen van HTTP alvorens zij aan AEM worden verpletterd.
* [Responstransformaties](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) - wijzig de HTTP-koppen van de uitgaande reacties voordat deze worden verzonden naar de browser.
* [Oorspronkelijke kiezers](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations#origin-selectors) - routeverkeer door CDN aan off-AEM plaatsen en toepassingen.

Zodra deze regels in broncontrole (git) worden verklaard, kunt u hen aan CDN opstellen gebruikend de Pijpleiding van de Configuratie van de Manager van de Wolk. Zie ook de omleidingsfunctie aan de clientzijde in de sectie voor vroege gebruikers hieronder.

### Aangepaste CDN-foutpagina&#39;s {#cdn-error-pages}

In de onwaarschijnlijke gebeurtenis dat CDN geen verkeer aan de AEM oorsprong kan leiden, kan een pagina van de douanefout worden verklaard, die de generische versie vervangt. [Meer informatie](/help/implementing/dispatcher/cdn-error-pages.md) informatie over hoe u pagina&#39;s met brandfouten kunt bedienen.

### Programma&#39;s voor vroege adoptie {#foundation-early-adopter}

#### Client-side omleidingen (Early-adopter-programma) {#client-side-redirects-early-adopter}

Vorm 301/302 cliënt-zij richt in broncontrole, en stel aan CDN op. [Meer informatie](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) en deelnemen aan het programma voor vroegtijdige adoptie via e-mail **<aemcs-cdn-config-adopter@adobe.com>**.

#### Waarschuwingen over verkeersfilterregels (vroege adopter-programma) {#traffic-filter-rules-alerts-early-adopter}

Onlangs vrijgegeven [Regels voor verkeersfilters](/help/security/traffic-filter-rules-including-waf.md), die de naar keuze licentiable regels van de Firewall van de Toepassing van het Web (WAF) omvatten, laat u vormen welk verkeer zou moeten worden toegestaan of worden ontkend.

Nu kunt u e-mailen **<aemcs-cdn-config-adopter@adobe.com>** om zich bij het vroege adopterprogramma aan te sluiten zodat kunt u worden gewaarschuwd wanneer uw regels van de verkeersfilter worden teweeggebracht. De e-mailberichten van het Centrum van acties zullen u op de hoogte houden wanneer bepaalde verkeersvoorwaarden voorkomen zodat kunt u aangewezen maatregelen nemen.

#### Apache/Dispatcher Runtime Ingestie van het Herschrijven Kaarten (Vroege Programma van de Aannemer) {#apache-rewritemaps-early-adopter}

Net als AEM 6.5 neemt Apache/dispatcher herschrijfkaarten op die op een specifieke locatie in de publicatieopslagplaats zijn geplaatst, en laadt ze, zonder dat een pijpleiding op een webniveau hoeft te worden uitgevoerd. Dit opent mogelijkheden voor een bedrijfsgebruiker om omleidingen te verklaren gebruikend UI, zoals die aangeboden door ACS Commons Redirect de Manager van de Kaart. Neem contact op met **<aemcs-cdn-config-adopter@adobe.com>** voor meer informatie .

#### Edge Side Includes (ESI) for Loading Dynamic Content (Early Introducter Program) {#esi-early-adopter}

De Adobe Beheerde CDN ondersteunt nu Edge Side Includes (ESI), een opmaaktaal voor dynamische webinhoud-assemblage op randniveau. Door ESI fragmenten op te nemen, kunt u de algemene pagina van de HTML bij CDN met hogere TTLs in het voorgeheugen plaatsen, terwijl vaker het halen van van oorsprong die kleinere secties die hogere tijdigheidsupdates (lagere TTLs) vereisen. Neem contact op met **<aemcs-cdn-config-adopter@adobe.com>** voor meer informatie .

#### RDE-ondersteuning voor front-end code met behulp van sitemenu&#39;s en sitemasjablonen (programma voor vroege adopters) {#rde-frontend-early-adopter}

[Rapid Development Environment (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) nu ondersteuning voor front-end code op basis van [sitethema&#39;s](/help/sites-cloud/administering/site-creation/site-themes.md) en [sitesjablonen](/help/sites-cloud/administering/site-creation/site-templates.md), voor vroege adoptie. Met RDEs, wordt dit gedaan gebruikend een richtlijn van de bevellijn, eerder dan een [front-end pijpleiding](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Neem contact op met **<aemcs-rde-support@adobe.com>** om het uit te proberen en feedback te geven.

#### Verbeterde logboekregistratie voor RDE&#39;s (Early Introducter Program) {#rde-logging-early-adopter}

Tijdens foutopsporing in een [Rapid Development Environment (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md)Ontwikkelaars kunnen logbestanden nu efficiënter configureren en streamen, met de opdrachtregel en zonder de OSGI-eigenschappen in versiebeheer te wijzigen. Functies:

* Logniveaus declareren op een niveau per pakket of klasse
* de indeling voor loguitvoer aanpassen
* meerdere logbestanden parallel streamen

Neem contact op met **<aemcs-rde-support@adobe.com>** om het uit te proberen en feedback te geven.

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
