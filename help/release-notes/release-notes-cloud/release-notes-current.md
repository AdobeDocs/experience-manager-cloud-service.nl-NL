---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 18f07bab308b707952b8df6b980dd3a6a9e024e9
workflow-type: tm+mt
source-wordcount: '2321'
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

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release met functies (2024.3.0) is 11 april 2024. De volgende release met functies (2024.4.0) is gepland voor 25 april 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van maart 2024 voor een overzicht van de functies die zijn toegevoegd in de release van 2024.3.0:

>[!VIDEO](https://video.tv.adobe.com/v/3428342?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Experience Manager Sites] {#sites-features}

**AEM Authoring voor Edge Delivery Services**

AEM Sites kan nu worden gebruikt als inhoudsbron voor Edge Delivery Services. Auteurs beheren hun websites in AEM met de nieuwe Universal Editor met in-context ontwerpen. Hierdoor kunnen bedrijven snelle, krachtige webpagina&#39;s met Edge Delivery Services maken en tegelijkertijd AEM krachtige mogelijkheden voor inhoudsbeheer benutten.

![AEM maken](/help/edge/assets/universal_editor_edge_delivery_services.png)

Zie de klasse [documentatie](/help/edge/overview.md) en bekijk de [AEM Gems - Aan de slag met AEM Authoring en Edge Delivery Services](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/aem-gems-getting-started-with-aem-authoring-and-edge-delivery/m-p/652694#M43905)

**Universal Editor voor Headless-implementaties**

De Universele Redacteur laat ook ontkoppelde Webtoepassingen toe om het zelfde intuïtieve in-contextWYSIWYG te gebruiken die eerder exclusief aan traditionele plaatsen was. Inhoudsmakers kunnen nu lay-outs visueel samenstellen met gebruik van Content Fragments met dezelfde snelheid als componenten binnen pagina&#39;s.

Wat de Universele Redacteur onderscheidt is zijn aanpassingsvermogen aan diverse Webarchitecturen, die zowel server-als cliënt-zijteruggeven aanpassen, die kader-agnostiek blijven, en de noodzaak voor AEM het ontvangen elimineren. Het is eenvoudig om bestaande webtoepassingen te integreren met de Universal Editor voor het bewerken van inhoud, waarbij ontwikkelaars vooral specifieke gegevenskenmerken moeten opnemen in hun opmaak.

Met dat, verzekert de Universele Redacteur een verenigbare het uitgeven ervaring, ongeacht inhoudsstructuur of onderliggende technologiestapel. Zie de klasse [Introductie van Universal Editor](/help/implementing/universal-editor/introduction.md).

**OpenAPI&#39;s voor inhoudsbeheer voor fragmenten en modellen**

Ontwikkelaars kunnen nu programmatisch communiceren met Content Fragments en Content Fragment-modellen en er CruD-bewerkingen op uitvoeren met gebruik van OpenAPI&#39;s voor inhoudsbeheer. Zie voor meer informatie [API-documentatie](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)

**Ondersteuning voor multisite beheer voor ervaringsfragmenten**

Ondersteuning voor beheer op meerdere locaties is uitgebreid voor mapstructuren waarin ervaringsfragmenten worden opgeslagen, zodat gebruikers een volledige inhoudsstructuur met ervaringsfragmenten kunnen implementeren.

**Versies van inhoudsfragmenten vergelijken**

Met de nieuwe Content Fragment Editor kunnen auteurs van inhoud nu verschillen tussen de huidige versie van een inhoudsfragment en een vorige versie vergelijken en bekijken.

### Programma voor vroege adoptie {#sites-early-adopter}

**Variaties genereren**

Hefboomwerking GenAI door AEM nieuwe eigenschap, [variaties genereren](/help/generative-ai/generate-variations.md), nu toegankelijk in de Cloud Service. Met het genereren van variaties kunt u inhoud genereren en schalen met behulp van generatieve AI. Neem contact op met het accountteam van uw Adobe voor advies in het programma.

**Bladeren door middelen in de inhoudsfragmentconsole**

Inhoudsauteurs kunnen nu door afbeeldingen en andere elementen bladeren, deze weergeven en deze activeren zonder dat ze de Content Fragment Console hoeven te verlaten.

![Bladeren door middelen](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Wilt u de functie proberen en feedback delen? Stuur een e-mail naar aemcs-headless-adopter@adobe.com vanuit uw officiële e-mailadres voor meer informatie over het programma voor vroege adoptie.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in de beheerweergave {#admin-view}

**Native integratie met Adobe Express**

AEM Assets integreert native met Adobe Express, waardoor u rechtstreeks vanuit de gebruikersinterface van de Adobe Express toegang hebt tot de elementen die in AEM Assets zijn opgeslagen. U kunt inhoud die in AEM Assets wordt beheerd, op het Express-canvas plaatsen en vervolgens nieuwe of bewerkte inhoud opslaan in een AEM Assets-opslagplaats.

![Elementen opnemen uit de invoegtoepassing Elementen](/help/assets/assets/adobe-express-native-integration.png)

**Voorvertoning van vertoningen weergeven voor alle ondersteunde videotypen**

Experience Manager Assets genereert nu standaard voorvertoningsuitvoeringen van alle ondersteunde videotypen zonder dat hiervoor een configuratie met het verwerkingsprofiel nodig is.

**Configuratie van delen koppelen**

Een nieuwe verbeterde gebruikerservaring voor [koppelingen maken](/help/assets/share-assets.md) samen met een gloednieuwe set configuraties waarmee beheerders het standaardgedrag van deze functie voor uw gebruikers kunnen aanpassen.

![E-mailservice configureren](/help/assets/assets/config-email-service.png)

### Nieuwe functies in de weergave Elementen {#assets-view}

**Rechten voor verzamelingen beheren**

Met Assets Essentials kunnen beheerders toegangsniveaus beheren voor privéverzamelingen die beschikbaar zijn in de opslagplaats. Als beheerder, kunt u gebruikersgroepen tot stand brengen en toestemmingen aan die groepen toewijzen om toegangsniveaus te beheren. U kunt ook de bevoegdheden voor machtigingsbeheer delegeren aan gebruikersgroepen.


## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Nieuwe functies voor AEM Forms {#forms-new-features}

* **[Adobe Experience Manager Forms Edge Delivery Services](/help/edge/docs/forms/overview.md)**: AEM Forms-Edge Delivery Services zijn een set services die een snelle ontwikkelomgeving mogelijk maakt waarin auteurs snel nieuwe formulieren kunnen bijwerken, publiceren en lanceren. Deze services bieden buitengewone en zeer belangrijke vormen van ervaring die de betrokkenheid en conversies stimuleren. Deze formulieren zijn gemakkelijk te ontwerpen en te ontwikkelen.

  ![EDS Forms-functies](/help/edge/assets/eds-forms-features.png)

Met deze services kunt u:

* Werk met meerdere inhoudsbronnen op dezelfde formuliersite en gebruik de gewenste ontwerpgereedschappen, zoals Microsoft Excel, Google Sheets of de Adaptive Forms Editor.
* Lever Digitale Inschrijving ervaringen die snel en onophoudelijk uw vormprestaties door echte gebruiker controle (RUM) laden en teruggeven.
* Gebruik gewoon HTML, modern CSS en vanilla JavaScript om uitzonderlijke ervaringen te creëren, waarbij de steile leercurve van een bepaald framework wordt vermeden.


### Nieuwe functies in Prerelease voor AEM Forms {#forms-pre-release}

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

### Programma&#39;s voor vroege adoptie {#foundation-early-adopter}

#### Waarschuwingen over verkeersfilterregels (vroege adopter-programma) {#traffic-filter-rules-alerts-early-adopter}

Onlangs vrijgegeven [Regels voor verkeersfilters](/help/security/traffic-filter-rules-including-waf.md), die de naar keuze licentiable regels van de Firewall van de Toepassing van het Web (WAF) omvatten, laat u vormen welk verkeer zou moeten worden toegestaan of worden ontkend.

Nu kunt u e-mailen **<aemcs-cdn-config-adopter@adobe.com>** om zich bij het vroege adopterprogramma aan te sluiten zodat kunt u worden gewaarschuwd wanneer uw regels van de verkeersfilter worden teweeggebracht. De e-mailberichten van het Centrum van acties zullen u op de hoogte houden wanneer bepaalde verkeersvoorwaarden voorkomen zodat kunt u aangewezen maatregelen nemen.

#### CDN-configuratie (programma voor vroege adoptie) {#cdn-config-early-adopter}

Naast de onlangs vrijgelaten [Regels voor verkeersfilters](/help/security/traffic-filter-rules-including-waf.md), die de naar keuze licentiable regels van de Firewall van de Toepassing van het Web (WAF) omvatten, is er een kans om de Pijpleiding van de Configuratie te gebruiken om andere types van configuratie te verklaren en op te stellen CDN. [Meer informatie](/help/implementing/dispatcher/cdn-configuring-traffic.md) en deelnemen aan het programma voor vroegtijdige adoptie via e-mail **<aemcs-cdn-config-adopter@adobe.com>** toegang krijgen tot:

* 301/302 omleidingen op de client
* verzoeken aan de rand van willekeurige oorsprong opnieuw exporteren (zoals niet-AEM toepassingen)
* URL-transformaties
* verzoek- of antwoordheaders instellen of wijzigen
* aangepaste foutpagina&#39;s wanneer de CDN AEM niet kan bereiken

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

