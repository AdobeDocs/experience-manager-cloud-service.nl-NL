---
title: Nota's van de versie voor 2024.4.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2024.4.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 153a3172-676f-4434-94d4-12fab8e17734
feature: Release Information
role: Admin
source-git-commit: 8be0a9894bb5b3a138c0ec40a437d6c8e4bc7e25
workflow-type: tm+mt
source-wordcount: '2699'
ht-degree: 0%

---

# Opmerkingen bij de release 2024.4.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2024.4.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2024.4.0) is 25 april 2024. De volgende release met functies (2024.5.0) is gepland voor 30 mei 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van april 2024 voor een overzicht van de functies die zijn toegevoegd in de release van 2024.4.0:

>[!VIDEO](https://video.tv.adobe.com/v/3429111?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Programma voor vroege adoptie {#sites-early-adopter}

**produceer Variaties**

Hefboomgaard GenAI door de nieuwe eigenschap van AEM, [ produceert variaties ](/help/generative-ai/generate-variations.md), nu toegankelijk in Cloud Service. Met het genereren van variaties kunt u inhoud genereren en schalen met behulp van generatieve AI. Neem contact op met uw Adobe-accountteam voor hulp in het programma.

**het doorbladeren van activa in de Console van het Fragment van de Inhoud**

Inhoudsauteurs kunnen nu door afbeeldingen en andere elementen bladeren, deze weergeven en deze activeren zonder dat ze de Content Fragment Console hoeven te verlaten.

![ het Bladeren van activa ](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Wilt u de functie proberen en feedback delen? Stuur een e-mail naar aemcs-headless-adopter@adobe.com vanuit uw officiële e-mailadres voor meer informatie over het programma voor vroege adoptie.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in de Assets-weergave {#assets-view-new-features}


**Contextual Onderzoek**

U kunt nu ook [ onderzoeksactiva beschikbaar in de bewaarplaats door tekstherinneringen ](/help/assets/search-assets-view.md#contextual-search) te bepalen. Experience Manager Assets transformeert automatisch die tekstherinneringen om filters te zoeken en toont de onderzoeksresultaten. Met het deelvenster Filters kunt u automatische filters weergeven en wijzigen om de zoekresultaten verder te beperken.

![ Contextual Onderzoek ](/help/assets/assets/contextual-search-text-prompt1.png)

**Uitdrukkelijke video snelle acties**

Experience Manager Assets omvat nu [ gemakkelijke en intuïtieve video het uitgeven hulpmiddelen die door Adobe Express ](/help/assets/edit-videos-assets-view.md) worden aangedreven om inhoud te verhogen hergebruik en inhoudssnelheid te versnellen. Tot de bewerkingsopties behoren bijsnijden, bijsnijden, het formaat van een video wijzigen en het omzetten van een MP4 in een GIF-bestand.

![ gewas video met Adobe Express ](/help/assets/assets/adobe-express-crop-video.png)

**Dynamische vertoningen**

U kunt dynamische vertoningen (met inbegrip van slimme gewassen) ](/help/assets/renditions.md) in Experience Manager Assets nu bekijken en downloaden. [ Dynamische uitvoeringen zijn aangepaste versies van afbeeldingselementen die in real-time worden gemaakt om aan specifieke behoeften te voldoen, zoals het formaat van afbeeldingen wijzigen op basis van de apparaatresolutie of het uitsnijden om aan verschillende hoogte-breedteverhoudingen te voldoen. Deze vertoningen stellen organisaties in staat om gepersonaliseerde en geoptimaliseerde ervaringen aan diverse publieksbehoeften te leveren.

![ Dynamische vertoningen ](/help/assets/assets/preset_smart_crop.png)

**op plaats anders noemt voor activa en omslagen**

Experience Manager Assets biedt nu een vereenvoudigde gebruikerservaring aan door [ capaciteit te verstrekken om activa of een omslag via één enkele klik ](/help/assets/manage-organize-assets-view.md) anders te noemen.

**wijs of verwijder meta-gegevensvorm aan veelvoudige omslagen toe**

U kunt nu [ meta-gegevensvorm aan veelvoudige omslagen ](/help/assets/metadata-assets-view.md#assign-metadata-form-to-a-folder) toewijzen of verwijderen.

### Nieuwe functies in de beheerweergave {#admin-view-new-features}

**de configuratie van het aandeel van de Verbinding**

Een nieuwe betere gebruikerservaring voor [ het creëren van verbindingsaandelen ](/help/assets/share-assets.md) samen met een gloednieuwe reeks configuraties die beheerders het standaardgedrag van dit vermogen voor uw gebruikers laten aanpassen.

![ Configuratie van het Aandeel van de Verbinding ](/help/assets/assets/config-email-service.png)



## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Nieuwe functies in AEM Forms {#forms-new-features}

* **Verbeterde Visuele Redacteur van de Regel voor de Component Gebaseerde Aangepaste Forms van de Kern**: Deze versie brengt een significante verbetering aan de visuele regelredacteur voor adaptieve vormen die op kerncomponenten worden gebaseerd. Deze versie brengt een significante verbetering aan de visuele regelredacteur voor adaptieve vormen die op kerncomponenten worden gebaseerd. Deze update is gericht op het stroomlijnen van interacties met aangepaste functies, zodat u robuustere en efficiëntere formulieren kunt maken.

  U kunt aangepaste functieinteracties nu stroomlijnen door:

   * [ Leveraging nieuwe aantekeningen om duidelijkere functiedefinities ](/help/forms/create-and-use-custom-functions.md#supported-javascript-annotations-for-custom-function) te verstrekken.
   * [ Gebruikend caching mechanismen voor douanefuncties, die tot snellere vormprestaties ](/help/forms/create-and-use-custom-functions.md#caching-support-for-custom-function) leiden.
   * [ naadloos werkend met globale voorwerpen binnen douanefuncties ](/help/forms/create-and-use-custom-functions.md#field-and-global-scope-objects-in-custom-functions).
   * [ het bepalen van en het gebruiken van facultatieve parameters binnen douanefuncties ](/help/forms/create-and-use-custom-functions.md#parameter).

  Deze update brengt ook de volgende verhogingen aan de functionaliteit van de regelredacteur. U kunt:

   * Implementeer krachtige [ &quot;wanneer-toen-anders&quot;](/help/forms/rule-editor-core-components.md#when) logica voor voorwaardelijke uitvoering.
   * Maak gebruik van moderne JavaScript-functies, zoals &#39;let and arrow&#39;-functies (ES10-ondersteuning).
   * Valideer of stel niet alleen gebieden, maar ook volledige panelen en vormen terug, die controle over gebruikersinteractie uitbreiden.

  Deze vooruitgang verstrekt een intuïtievere en krachtige ervaring voor het ontwerpen van regels en douanefuncties binnen de visuele regelredacteur.

* **[creeer veelvoudige versies van een Aangepast Vorm](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md)**: U kunt variaties van bestaande vormen nu gemakkelijk beheren. Dit vereenvoudigt versiecontrole en vergemakkelijkt vergelijking voor vormoptimalisering, allen binnen één enkele, gestroomlijnde werkschema.

* **[vergelijk Aangepaste Vorm](/help/forms/compare-forms.md)**: U kunt twee vormen nu gemakkelijk vergelijken om verschillen tussen twee vormen te identificeren. Het vergemakkelijkt vlotte samenwerking door teamleden toe te laten om revisies te vergelijken en veranderingen efficiënt te bespreken.

* **de Verbeteringen van de Toegankelijkheid voor de Krabbelige Component van de Handtekening**: Deze update brengt significante toegankelijkheidsverbeteringen aan de Krabbelcomponent van de Handtekening:

  **Verbeterde Navigatie van het Toetsenbord:**
   * Als u op de Tab-toets drukt, kunnen gebruikers door alle interactieve elementen navigeren in het dialoogvenster Handtekening.
   * Het dialoogvenster wordt gesloten wanneer u ondertekent met een penseel of toetsenbord en op Enter drukt.
   * De focus blijft op het besturingselement voor handtekeningen nadat u hebt ondertekend en op &quot;OK&quot; hebt geklikt.

  **Duidelijke Functionaliteit van de Handtekening:**

   * Een duidelijk kruispictogram voor het wissen van de handtekening is toegankelijk via de Tab-toets.
   * Het dialoogvenster Handtekeningbevestiging wissen is ook toegankelijk via tabnavigatie.

  **Verbeterde Etiketten en Controles:**
   * Het label voor de knop voor toetsenbordondertekening is nu duidelijker en met &quot;aria-label&quot; kunt u functionaliteit aankondigen (zoals &quot;aria-label=&#39;Ondertekenen met toetsenbord&#39;&#39;).
   * Het verbeterde contrast zorgt ervoor dat alle besturingselementen binnen de krabbelhandtekening gemakkelijk te onderscheiden zijn.
   * De knop OK/vinkje geeft nu visueel aan wanneer deze inactief is.

  **de Terugkoppeling van de Handtekening voor de Lezers van het Scherm:**
   * Wanneer een handtekening wordt getypt, kunnen gebruikers van schermlezers de tekst horen die wordt gebruikt om de handtekening te maken.

Deze update zorgt voor een inclusievere ervaring voor gebruikers met een handicap door navigatie, helderheid en feedback voor de component Krabbelhandtekening te verbeteren.

### Programma voor vroege adoptie {#forms-early-adopter}

* **[voorlegt een Aangepast Vorm aan het Scenario van de Fusie van Adobe Workfront](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service biedt een uit-van-de-doosoptie aan om een Aangepast Vorm met Adobe Workfront moeiteloos aan te sluiten. Dit vereenvoudigt het proces om een Adaptief Formulier aan een scenario van Adobe Workfront voor te leggen, toelatend u een scenario van de Fusie van Workfront op voorlegging van een Aangepast Vorm teweegbrengt.

  <br/> ![ Adobe Workfront ](/help/forms/assets/adobe-workfront.png) <br/> Gebruikend de Schakelaar van de Fusie van Adobe Workfront, kunt u werkschema&#39;s ontwerpen die automatisch op voorlegging van een Aangepast Vorm worden teweeggebracht. Stel bijvoorbeeld dat een workflow wordt gestart om een specifieke persoon de taak te geven de ingediende gegevens te beoordelen, zodat een aanvraag kan worden goedgekeurd of afgewezen op basis van de informatie die via het adaptieve formulier is vastgelegd. Deze gestroomlijnde integratie verbetert de efficiëntie en zorgt voor een nieuw niveau van automatisering van uw workflowprocessen.|

* **[de Dienst van de Uitbreiding van Reader](/help/forms/aem-forms-cloud-service-communications-introduction.md#reader-extension-service)**: De Communicatie van AEM Forms APIs heeft de Dienst van de Uitbreiding van Reader gebracht om u toe te staan om functionaliteit zoals het invullen van en het becommentariëren aan regelmatige PDFs toe te voegen, die hen voor gebruikers met de vrije Lezer van Adobe interactief maken.

* [ Recht aan linkertaalsteun ](/help/forms/supporting-new-language-localization-core-components.md): De adaptieve Forms die op de Componenten van de Kern wordt gebouwd kan nu in een (RTL) taal zoals Arabisch, Perzisch, en Urdu worden voorgesteld. De RTL-talen worden wereldwijd gesproken door meer dan 2 miljard mensen. Door een formulier in RTL-taal te gebruiken, kunt u het bereik van uw adaptieve formulieren uitbreiden naar deze verschillende doelgroepen en selecteren in RTL-markten. In bepaalde regio&#39;s is het ook een wettelijk mandaat om formulieren in de lokale taal te verstrekken. Door lokale talen aan te passen, opent u niet alleen deuren voor een breder publiek, maar zorgt u ook voor naleving van relevante wetten en regels.

* **[bescherm uw documenten met DocAssurance APIs (Deel van Communicatie APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: De DocAssurance APIs machtigt u om gevoelige informatie te beschermen door de documenten te ondertekenen en te coderen. Door versleuteling wordt de inhoud van een document omgezet in een onleesbare indeling, zodat alleen geautoriseerde gebruikers toegang hebben. Deze versterkte beschermingslaag beschermt niet alleen waardevolle gegevens tegen ongeoorloofde ogen, maar zorgt ook voor gemoedsrust. Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen.

  U kunt vanuit uw officiële e-mailid naar `aem-forms-ea@adobe.com` schrijven om deel te nemen aan het programma voor vroegtijdige adoptie en toegang tot deze functie aanvragen.

* **[u kunt hefboomwerking de Operationele Dienst van Telemetrie](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** om cliënt-zijinzameling voor AEM as a Cloud Service toe te laten.
De operationele telemetrieservice biedt een nauwkeuriger weergave van gebruikersinteracties, waardoor een betrouwbare maatstaf voor de betrokkenheid van websites wordt gegarandeerd. Het is een geweldige kans om geavanceerde inzichten in uw paginaprestaties te krijgen. Terwijl dit voor klanten nuttig is die of Adobe-Geleide CDN of niet-Adobe-Beheerde CDN gebruiken. Bovendien, voor klanten die een niet-Adobe beheerde CDN gebruiken, kan het geautomatiseerde verkeer nu voor hen worden toegelaten, waarbij de behoefte wordt weggenomen om het even welk verkeersrapport met Adobe te delen.

  Als u interesse hebt in het testen van deze nieuwe functie en het delen van uw feedback, stuurt u een e-mail naar `aemcs-rum-adopter@adobe.com`, samen met uw domeinnaam voor elk van de omgevingen waarvoor u Operationele telemetrie wilt inschakelen via uw e-mailadres dat is gekoppeld aan uw Adobe ID. Het productteam van Adobe zal dan de Operationele Dienst van de Telemetrie voor u toelaten.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Domeintoewijzing {#cdn-config}

Vorm verkeer bij Adobe CDN op de volgende manieren:

* [ de transformaties van het Verzoek ](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations) - wijzig aspecten van inkomende verzoeken, met inbegrip van wegen, vraagparameters, en de kopballen van HTTP alvorens zij aan AEM worden verpletterd.
* [ transformaties van de Reactie ](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations) - de kopballen van HTTP van de uitgaande reacties veranderen alvorens zij aan browser worden gediend.
* [ de selecteurs van de Oorsprong ](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations#origin-selectors) - routeverkeer door CDN aan off-AEM plaatsen en toepassingen.

Zodra deze regels in broncontrole (git) worden verklaard, kunt u hen aan CDN opstellen gebruikend de Pijpleiding van de Configuratie van Cloud Manager. Zie ook de omleidingsfunctie aan de clientzijde in de sectie voor vroege gebruikers hieronder.

### Aangepaste CDN-foutpagina&#39;s {#cdn-error-pages}

In het onwaarschijnlijke geval dat CDN geen verkeer aan de oorsprong van AEM kan leiden, kan een pagina van de douanefout worden verklaard, die de generische versie vervangt. [ leer meer ](/help/implementing/dispatcher/cdn-error-pages.md) over hoe te om branded foutenpagina&#39;s te dienen.

### Programma&#39;s voor vroege adoptie {#foundation-early-adopter}

#### Server-side omleidingen (Early-adopter-programma) {#server-side-redirects-early-adopter}

Vorm 301/302 server-zij richt in broncontrole, en stel aan CDN op. [ leer meer ](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors) en sluit zich aan bij het vroege adopterprogramma door te e-mailen **<aemcs-cdn-config-adopter@adobe.com>**.

#### Waarschuwingen over verkeersfilterregels (vroege adopter-programma) {#traffic-filter-rules-alerts-early-adopter}

Onlangs vrijgegeven {de Regels van de Filter van het Verkeer ](/help/security/traffic-filter-rules-including-waf.md), die de naar keuze licentiebare regels van de Firewall van de Toepassing van het Web (WAF) omvatten, laat u vormen welk verkeer zou moeten worden toegestaan of worden ontkend.[

Nu kunt u **<aemcs-cdn-config-adopter@adobe.com>** per e-mail verzenden om deel te nemen aan het vroege adoptieprogramma zodat kunt u worden gewaarschuwd wanneer uw regels van de verkeersfilter worden teweeggebracht. De e-mailberichten van het Centrum van acties zullen u op de hoogte houden wanneer bepaalde verkeersvoorwaarden voorkomen zodat kunt u aangewezen maatregelen nemen.

#### Apache/Dispatcher Runtime Ingestie van herschrijfkaarten (programma voor vroege adopters) {#apache-rewritemaps-early-adopter}

Net als AEM 6.5 neemt Apache/dispatcher herschrijfkaarten in die op een specifieke locatie in de publicatieopslagplaats zijn geplaatst en laadt deze kaarten, zonder dat een pijpleiding op een webniveau hoeft te worden uitgevoerd. Dit opent mogelijkheden voor een bedrijfsgebruiker om omleidingen te verklaren gebruikend UI, zoals die aangeboden door ACS Commons Redirect de Manager van de Kaart. Neem contact op met **<aemcs-cdn-config-adopter@adobe.com>** voor meer informatie.

#### Edge Side Includes (ESI) for Loading Dynamic Content (Early Introducter Program) {#esi-early-adopter}

De door Adobe beheerde CDN biedt nu ondersteuning voor ESI (Edge Side Includes), een opmaaktaal voor dynamische webinhoud-assemblage op randniveau. Door ESI fragmenten op te nemen, kunt u de algemene pagina van HTML bij CDN met hogere TTLs in het voorgeheugen plaatsen, terwijl het halen van uit oorsprong die kleinere secties die hogere toegangsupdates (lagere TTLs) vereisen. Neem contact op met **<aemcs-cdn-config-adopter@adobe.com>** voor meer informatie.

#### RDE-ondersteuning voor front-end code met behulp van sitemenu&#39;s en sitemasjablonen (programma voor vroege adopters) {#rde-frontend-early-adopter}

{de milieu&#39;s van de Snelle Ontwikkeling van 0} (RDEs) ](/help/implementing/developing/introduction/rapid-development-environments.md) steunen nu front-end code die op [ plaatsthema&#39;s ](/help/sites-cloud/administering/site-creation/site-themes.md) en [ plaatsmalplaatjes ](/help/sites-cloud/administering/site-creation/site-templates.md) wordt gebaseerd, voor vroege adopters. [ Met RDEs, wordt dit gedaan gebruikend een richtlijn van de bevellijn, eerder dan a [ front-end pijpleiding ](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Neem contact op met **<aemcs-rde-support@adobe.com>** om het uit te proberen en feedback te geven.

#### Verbeterde logboekregistratie voor RDE&#39;s (Early Introducter Program) {#rde-logging-early-adopter}

Terwijl het zuiveren van code in a [ Snelle Milieu van de Ontwikkeling (RDE) ](/help/implementing/developing/introduction/rapid-development-environments.md), kunnen de ontwikkelaars logboeken nu vormen en stromen efficiënter, gebruikend de bevellijn, en zonder eigenschappen te wijzigen OSGI in versiecontrole. Functies:

* Logniveaus declareren op een niveau per pakket of klasse
* de indeling voor loguitvoer aanpassen
* meerdere logbestanden parallel streamen

Neem contact op met **<aemcs-rde-support@adobe.com>** om het uit te proberen en feedback te geven.

## [!DNL Experience Manager] Hulplijnen {#guides}

### Mogelijkheid om inhoud in meerdere talen te vertalen met behulp van vooraf geconfigureerde taalgroepen

Met Experience Manager Guides kunt u nu taalgroepen maken en uw inhoud eenvoudig in meerdere talen vertalen. Met deze functie kunt u vertalingen volgens de behoeften van uw organisatie ordenen en beheren.

Als u bijvoorbeeld uw inhoud voor bepaalde landen in Europa wilt vertalen, kunt u een taalgroep voor Europese talen maken, zoals Engels (EN), Frans (FR), Duits (DE), Spaans (ES) en Italiaans (IT).

![ vertaalpaneel ](/help/release-notes/assets/guides/translation-languages-2404.png)

*selecteer de taalgroepen of de talen u uw documenten wilt vertalen.*

>[!NOTE]
>
>Als de doelmap van een taal ontbreekt of als de doeltaal gelijk is aan de bron, wordt deze grijs weergegeven en wordt een waarschuwingsteken weergegeven.

Als beheerder kunt u taalgroepen maken en deze configureren naar meerdere mapprofielen. Als auteur kunt u de taalgroepen weergeven die zijn geconfigureerd in uw mapprofiel.


Het maken van taalgroepen verbetert over het algemeen de efficiëntie en productiviteit van vertaalprojecten en verbetert uiteindelijk het lokalisatieproces in meerdere talen.


Leer hoe te [ documenten van de Redacteur van het Web ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/user-guide/author-content/create-preview-topics/author-content-aem-guides/work-with-web-editor/translate-documents-web-editor) vertalen

### Nieuwe ervaring voor het zoeken naar en filteren van bestanden in de gegevensopslagweergave

Nu hebt u een verbeterde ervaring bij het filteren van bestanden. De vernieuwde functionaliteit voor het filteren van bestanden biedt een verbeterde manier om bestanden moeiteloos te doorzoeken en door te bladeren.

![ onderzoeksdossiers in bewaarplaatmening ](/help/release-notes/assets/guides/repository-filter-search-2404.png)

*Onderzoek naar de dossiers die de tekst bevatten`general purpose.`*

Geniet van voordelen zoals snellere toegang tot relevante bestanden en een intuïtievere gebruikersinterface, waardoor uw zoekervaring vloeiender en efficiënter wordt.

![ snel zoekfilter ](/help/release-notes/assets/guides/repository-filter-search-quick.png)

*gebruik de snelle filters om naar DITA en niet-DITA dossiers te zoeken.*

Leer meer over de **eigenschap van het Onderzoek van de Filter** in de [ Linkerpaneel ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/user-guide/author-content/create-preview-topics/author-content-aem-guides/work-with-web-editor/web-editor-features#id2051EA0M0HS) sectie.

### Verbeteringen in de Data Source Connectors

De volgende verbeteringen zijn aangebracht in de gegevensbronconnectors voor de release 2024.4.0:

#### Verbind met Salsify, Akeneo, en Microsoft Azure DevOps Boards (ADO) Gegevensbronnen

Naast de bestaande out-of-the-box connectors biedt Experience Manager Guides ook connectors voor Salsify-, Akeneo- en Microsoft Azure DevOps Boards (ADO)-gegevensbronnen. Als beheerder kunt u deze connectors downloaden en installeren. Dan, vorm de geïnstalleerde schakelaars.

#### De voorbeeldquery kopiëren en plakken om een inhoudsfragment of onderwerp te maken

U kunt een vraag van steekproefgegevens in de generator gemakkelijk kopiëren en kleven om een inhoudsfragment of een onderwerp tot stand te brengen. Met deze eigenschap, moet u niet de syntaxis herinneren of een vraag manueel creëren. In plaats van de vraag manueel te typen, kunt u een steekproefvraag kopiëren en kleven, het uitgeven, en het gebruiken om de gegevens volgens uw vereisten te halen.

![ neem de dialoogdoos van het inhoudsfragment op ](/help/release-notes/assets/guides/insert-content-snippet.png)

*Exemplaar en geef een steekproefvraag uit om het inhoudsfragment tot stand te brengen.*

#### Verbinding maken met JSON-gegevensbestanden via een bestandsverbinding


Nu, als beheerder, kunt u een JSON dossierschakelaar vormen om JSON- gegevensdossiers als gegevensbron te gebruiken. Gebruik de connector om de JSON-bestanden van uw computer of de Adobe Experience Manager Assets te importeren. Vervolgens kunt u als auteur met behulp van de generatoren inhoudsfragmenten of onderwerpen maken.

Met deze functie kunt u de gegevens die in uw JSON-bestanden zijn opgeslagen, gebruiken en opnieuw gebruiken in verschillende fragmenten. De inhoud wordt ook dynamisch bijgewerkt wanneer u de JSON-bestanden bijwerkt.

#### Vorm Meerdere Middel URLs voor een Schakelaar om Inhoud Fragmenten of Onderwerpen tot stand te brengen

Als beheerder, kunt u veelvoudige middel URLs voor sommige schakelaars zoals de Generische Cliënt van de REST, Salsify, Akeneo, en Microsoft Azure DevOps Boards (ADO) vormen.
Dan, als auteur, verbind met de gegevensbronnen om inhoudsfragmenten of onderwerpen tot stand te brengen gebruikend de generators. Deze functie is handig omdat u geen gegevensbron hoeft te maken voor elke URL. Het helpt u om gegevens van om het even welke middelen voor een bepaalde gegevensbron in één enkel inhoudsfragment of onderwerp snel te halen. Bekijk meer details over de gegevensbronschakelaars en hoe te [ een gegevensbronschakelaar van het gebruikersinterface ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/install-guide/cs-ig/web-editor-configs-cs/conf-data-source-connector-tools) vormen. Leer hoe te [ gegevens van uw gegevensbron ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/user-guide/author-content/create-preview-topics/author-content-aem-guides/work-with-web-editor/web-editor-content-snippet) gebruiken.

Voor meer informatie over de nieuwe eigenschappen en de verhogingen, geeft de mening [ Experience Manager Guides informatie ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap) vrij.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
