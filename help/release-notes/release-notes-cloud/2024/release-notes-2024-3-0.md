---
title: Nota's van de versie voor 2024.3.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2024.3.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: b3816929-2c0a-4d6a-b583-c928d2182ecd
feature: Release Information
role: Admin
source-git-commit: 8be0a9894bb5b3a138c0ec40a437d6c8e4bc7e25
workflow-type: tm+mt
source-wordcount: '2283'
ht-degree: 0%

---

# Opmerkingen bij de release 2024.3.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2024.3.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=nl-NL) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2024.3.0) is 11 april 2024. De volgende release met functies (2024.4.0) is gepland voor 25 april 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van maart 2024 voor een overzicht van de functies die zijn toegevoegd in de release van 2024.3.0:

>[!VIDEO](https://video.tv.adobe.com/v/3428342?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Experience Manager Sites] {#sites-features}

**Authoring van AEM voor Edge Delivery Services**

AEM Sites kan nu worden gebruikt als inhoudsbron voor Edge Delivery Services. Auteurs beheren hun websites in AEM met de nieuwe Universal Editor met in-context ontwerpen. Hierdoor kunnen bedrijven met Edge Delivery Services snelle, krachtige webpagina&#39;s maken en tegelijk gebruikmaken van de krachtige AEM-mogelijkheden voor contentbeheer.

![ AEM Authoring ](/help/edge/assets/universal_editor_edge_delivery_services.png)

Voor meer informatie, zie de [ documentatie ](/help/edge/overview.md) en bekijk [ AEM Gems - die met de Authoring van AEM en Edge Delivery Services ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/aem-gems-getting-started-with-aem-authoring-and-edge-delivery/m-p/652694#M43905) worden begonnen

**Universele Redacteur voor Hoofdloze Implementaties**

Met de Universal Editor kunnen ook ontkoppelde webtoepassingen dezelfde intuïtieve in-context WYSIWYG-authoring gebruiken die voorheen exclusief was voor traditionele sites. Inhoudsmakers kunnen nu lay-outs visueel samenstellen met gebruik van Content Fragments met dezelfde snelheid als componenten binnen pagina&#39;s.

Wat de Universal Editor onderscheidt, is het aanpassingsvermogen aan verschillende webarchitecturen, waarbij zowel server- als client-side rendering wordt aangepast, het framework-agnostisch blijft en AEM-hosting overbodig wordt. Het is eenvoudig om bestaande webtoepassingen te integreren met de Universal Editor voor het bewerken van inhoud, waarbij ontwikkelaars vooral specifieke gegevenskenmerken moeten opnemen in hun opmaak.

Met dat, verzekert de Universele Redacteur een verenigbare het uitgeven ervaring, ongeacht inhoudsstructuur of onderliggende technologiestapel. Voor meer informatie, zie de [ Universele Inleiding van de Redacteur ](/help/implementing/universal-editor/introduction.md).

**OpenAPIs van het Beheer van de Inhoud voor de Fragmenten en Modellen van de Inhoud**

Ontwikkelaars kunnen nu programmatisch communiceren met Content Fragments en Content Fragment-modellen en er CruD-bewerkingen op uitvoeren met gebruik van OpenAPI&#39;s voor inhoudsbeheer. Voor meer informatie, zie [ API documentatie ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)

**Multisite steun van het Beheer voor de Fragmenten van de Ervaring**

Ondersteuning voor beheer op meerdere locaties is uitgebreid voor mapstructuren waarin ervaringsfragmenten worden opgeslagen, zodat gebruikers een volledige inhoudsstructuur met ervaringsfragmenten kunnen implementeren.

**versies van het Fragment van de Inhoud vergelijken**

Met de nieuwe Content Fragment Editor kunnen auteurs van inhoud nu verschillen tussen de huidige versie van een inhoudsfragment en een vorige versie vergelijken en bekijken.

### Programma voor vroege adoptie {#sites-early-adopter}

**produceer Variaties**

Hefboomgaard GenAI door de nieuwe eigenschap van AEM, [ produceert variaties ](/help/generative-ai/generate-variations.md), nu toegankelijk in Cloud Service. Met het genereren van variaties kunt u inhoud genereren en schalen met behulp van generatieve AI. Neem contact op met uw Adobe-accountteam voor hulp in het programma.

**het doorbladeren van activa in de Console van het Fragment van de Inhoud**

Inhoudsauteurs kunnen nu door afbeeldingen en andere elementen bladeren, deze weergeven en deze activeren zonder dat ze de Content Fragment Console hoeven te verlaten.

![ het Bladeren van activa ](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Wilt u de functie proberen en feedback delen? Stuur een e-mail naar aemcs-headless-adopter@adobe.com vanuit uw officiële e-mailadres voor meer informatie over het programma voor vroege adoptie.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in de beheerweergave {#admin-view}

**Inheemse integratie met Adobe Express**

AEM Assets kan op een native manier worden geïntegreerd met Adobe Express, waardoor u rechtstreeks vanuit de Adobe Express-gebruikersinterface toegang hebt tot de elementen die in AEM Assets zijn opgeslagen. U kunt inhoud die in AEM Assets wordt beheerd, op het Express-canvas plaatsen en vervolgens nieuwe of bewerkte inhoud opslaan in een AEM Assets-opslagplaats.

![ omvat activa van Assets toe:voegen-op ](/help/assets/assets/adobe-express-native-integration.png)

**de vertoningen van de Voorproef voor alle gesteunde videotypes**

Experience Manager Assets genereert nu standaard voorvertoningsuitvoeringen van alle ondersteunde videotypen zonder dat hiervoor een configuratie met het verwerkingsprofiel nodig is.

### Nieuwe functies in de Assets-weergave {#assets-view}

**beheert toestemmingen voor inzamelingen**

De Hoofdzaak van activa staat de beheerders toe om toegangsniveaus voor privé inzamelingen te beheren beschikbaar in de bewaarplaats. Als beheerder, kunt u gebruikersgroepen tot stand brengen en toestemmingen aan die groepen toewijzen om toegangsniveaus te beheren. U kunt ook de bevoegdheden voor machtigingsbeheer delegeren aan gebruikersgroepen.


## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Nieuwe functies voor AEM Forms {#forms-new-features}

* **[Adobe Experience Manager Forms Edge Delivery Services](/help/edge/docs/forms/overview.md)**: Edge Delivery Services voor AEM Forms is een composable reeks diensten die een snelle ontwikkelomgeving toelaat waar de auteurs, nieuwe vormen kunnen bijwerken publiceren en snel lanceren. Deze services bieden buitengewone en zeer belangrijke vormen van ervaring die de betrokkenheid en conversies stimuleren. Deze formulieren zijn gemakkelijk te ontwerpen en te ontwikkelen.

  ![ EDS Forms Eigenschappen ](/help/edge/assets/eds-forms-features.png)

Met deze services kunt u:

* Werk met meerdere inhoudsbronnen op dezelfde formuliersite en gebruik de gewenste ontwerpgereedschappen, zoals Microsoft Excel, Google Sheets of de Adaptive Forms Editor.
* Lever de Digitale Inschrijving ervaringen die snel en onophoudelijk uw vormprestaties door Operationele Telemetrie laden en teruggeven controleren.
* Gebruik gewoon HTML, modern CSS en vanilla JavaScript om uitzonderlijke ervaringen te creëren, waarbij de steile leercurve van een specifiek framework wordt vermeden.


### Nieuwe functies in Prerelease voor AEM Forms {#forms-pre-release}

* **Verbeterde Visuele Redacteur van de Regel voor de Component Gebaseerde Aangepaste Forms van de Kern**: Deze versie brengt een significante verbetering aan de visuele regelredacteur voor adaptieve vormen die op kerncomponenten worden gebaseerd. Deze versie brengt een significante verbetering aan de visuele regelredacteur voor adaptieve vormen die op kerncomponenten worden gebaseerd. Deze update is gericht op het stroomlijnen van interacties met aangepaste functies, zodat u robuustere en efficiëntere formulieren kunt maken.

  U kunt aangepaste functieinteracties nu stroomlijnen door:

   * Nieuwe annotaties gebruiken om duidelijkere functiedefinities te bieden.
   * Het gebruik van mechanismen voor het in cache plaatsen van aangepaste functies, wat leidt tot snellere formulierprestaties.
   * Naadloos werken met globale objecten binnen aangepaste functies.
   * Optionele parameters definiëren en gebruiken binnen aangepaste functies.

  Deze update brengt ook de volgende verhogingen aan de functionaliteit van de regelredacteur. U kunt:

   * Implementeer krachtige logica &#39;when-then-else&#39; voor voorwaardelijke uitvoering.
   * Maak gebruik van moderne JavaScript-functies, zoals &#39;let and arrow&#39;-functies (ES10-ondersteuning).
   * Valideer of stel niet alleen gebieden, maar ook volledige panelen en vormen terug, die controle over gebruikersinteractie uitbreiden.

  Deze vooruitgang verstrekt een intuïtievere en krachtige ervaring voor het ontwerpen van regels en douanefuncties binnen de visuele regelredacteur.

* **creeer veelvoudige versies van een Aangepast Vorm**: U kunt variaties van bestaande vormen nu gemakkelijk beheren. Dit vereenvoudigt versiecontrole en vergemakkelijkt vergelijking voor vormoptimalisering, allen binnen één enkele, gestroomlijnde werkschema.

* **vergelijk Aangepaste Vorm**: U kunt twee vormen nu gemakkelijk vergelijken om verschillen tussen twee vormen te identificeren. Het vergemakkelijkt vlotte samenwerking door teamleden toe te laten om revisies te vergelijken en veranderingen efficiënt te bespreken.

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

* **de Dienst van de Uitbreiding van Reader**: De Communicatie van AEM Forms APIs heeft de Dienst van de Uitbreiding van Reader gebracht om u toe te staan om functionaliteit zoals het invullen van en het becommentariëren aan regelmatige PDFs toe te voegen, die hen voor gebruikers met de vrije Lezer van Adobe interactief maken.

* [ Recht aan linkertaalsteun ](/help/forms/supporting-new-language-localization-core-components.md): De adaptieve Forms die op de Componenten van de Kern wordt gebouwd kan nu in een (RTL) taal zoals Arabisch, Perzisch, en Urdu worden voorgesteld. De RTL-talen worden wereldwijd gesproken door meer dan 2 miljard mensen. Door een formulier in RTL-taal te gebruiken, kunt u het bereik van uw adaptieve formulieren uitbreiden naar deze verschillende doelgroepen en selecteren in RTL-markten. In bepaalde regio&#39;s is het ook een wettelijk mandaat om formulieren in de lokale taal te verstrekken. Door lokale talen aan te passen, opent u niet alleen deuren voor een breder publiek, maar zorgt u ook voor naleving van relevante wetten en regels.

* **[bescherm uw documenten met DocAssurance APIs (Deel van Communicatie APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: De DocAssurance APIs machtigt u om gevoelige informatie te beschermen door de documenten te ondertekenen en te coderen. Door versleuteling wordt de inhoud van een document omgezet in een onleesbare indeling, zodat alleen geautoriseerde gebruikers toegang hebben. Deze versterkte beschermingslaag beschermt niet alleen waardevolle gegevens tegen ongeoorloofde ogen, maar zorgt ook voor gemoedsrust. Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen.

  U kunt vanuit uw officiële e-mailid naar `aem-forms-ea@adobe.com` schrijven om deel te nemen aan het programma voor vroegtijdige adoptie en toegang tot deze functie aanvragen.

* **[u kunt hefboomwerking de Operationele Dienst van Telemetrie](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** om cliënt-zijinzameling voor AEM as a Cloud Service toe te laten.
De operationele telemetrieservice biedt een nauwkeuriger weergave van gebruikersinteracties, waardoor een betrouwbare maatstaf voor de betrokkenheid van websites wordt gegarandeerd. Het is een geweldige kans om geavanceerde inzichten in uw paginaprestaties te krijgen. Terwijl dit voor klanten nuttig is die of Adobe-Geleide CDN of niet-Adobe-Beheerde CDN gebruiken. Bovendien, voor klanten die een niet-Adobe beheerde CDN gebruiken, kan het geautomatiseerde verkeer nu voor hen worden toegelaten, waarbij de behoefte wordt weggenomen om het even welk verkeersrapport met Adobe te delen.

  Als u interesse hebt in het testen van deze nieuwe functie en het delen van uw feedback, stuurt u een e-mail naar `aemcs-rum-adopter@adobe.com`, samen met uw domeinnaam voor elk van de omgevingen waarvoor u Operationele telemetrie wilt inschakelen via uw e-mailadres dat is gekoppeld aan uw Adobe ID. Het productteam van Adobe zal dan de Operationele Dienst van de Telemetrie voor u toelaten.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Programma&#39;s voor vroege adoptie {#foundation-early-adopter}

#### Waarschuwingen over verkeersfilterregels (vroege adopter-programma) {#traffic-filter-rules-alerts-early-adopter}

Onlangs vrijgegeven &lbrace;de Regels van de Filter van het Verkeer [&#128279;](/help/security/traffic-filter-rules-including-waf.md), die de naar keuze licentiebare regels van de Firewall van de Toepassing van het Web (WAF) omvatten, laat u vormen welk verkeer zou moeten worden toegestaan of worden ontkend.

Nu kunt u **<aemcs-cdn-config-adopter@adobe.com>** per e-mail verzenden om deel te nemen aan het vroege adoptieprogramma zodat kunt u worden gewaarschuwd wanneer uw regels van de verkeersfilter worden teweeggebracht. De e-mailberichten van het Centrum van acties zullen u op de hoogte houden wanneer bepaalde verkeersvoorwaarden voorkomen zodat kunt u aangewezen maatregelen nemen.

#### Domeintoewijzing (programma voor vroege adoptie) {#cdn-config-early-adopter}

Naast onlangs vrijgegeven [ Regels van de Filter van het Verkeer ](/help/security/traffic-filter-rules-including-waf.md), die de naar keuze licentiebare regels van de Firewall van de Toepassing van het Web (WAF) omvatten, is er een kans om de Pijpleiding van de Configuratie te gebruiken om andere types van configuratie te verklaren en op te stellen CDN. [ leer meer ](/help/implementing/dispatcher/cdn-configuring-traffic.md) en sluit zich aan bij het vroege adopterprogramma door **<aemcs-cdn-config-adopter@adobe.com>** te e-mailen om toegang te krijgen tot:

* 301/302 serveromleidingen
* verzoeken aan de rand van willekeurige oorsprong proxying (zoals niet-AEM-toepassingen)
* URL-transformaties
* verzoek- of antwoordheaders instellen of wijzigen
* aangepaste foutpagina&#39;s wanneer de CDN AEM niet kan bereiken

#### Apache/Dispatcher Runtime Ingestie van herschrijfkaarten (programma voor vroege adopters) {#apache-rewritemaps-early-adopter}

Net als AEM 6.5 neemt Apache/dispatcher herschrijfkaarten in die op een specifieke locatie in de publicatieopslagplaats zijn geplaatst en laadt deze kaarten, zonder dat een pijpleiding op een webniveau hoeft te worden uitgevoerd. Dit opent mogelijkheden voor een bedrijfsgebruiker om omleidingen te verklaren gebruikend UI, zoals die aangeboden door ACS Commons Redirect de Manager van de Kaart. Neem contact op met **<aemcs-cdn-config-adopter@adobe.com>** voor meer informatie.

#### Edge Side Includes (ESI) for Loading Dynamic Content (Early Introducter Program) {#esi-early-adopter}

De door Adobe beheerde CDN biedt nu ondersteuning voor ESI (Edge Side Includes), een opmaaktaal voor dynamische webinhoud-assemblage op randniveau. Door ESI fragmenten op te nemen, kunt u de algemene pagina van HTML bij CDN met hogere TTLs in het voorgeheugen plaatsen, terwijl het halen van uit oorsprong die kleinere secties die hogere toegangsupdates (lagere TTLs) vereisen. Neem contact op met **<aemcs-cdn-config-adopter@adobe.com>** voor meer informatie.

#### RDE-ondersteuning voor front-end code met behulp van sitemenu&#39;s en sitemasjablonen (programma voor vroege adopters) {#rde-frontend-early-adopter}

{de milieu&#39;s van de Snelle Ontwikkeling van 0} (RDEs) [&#128279;](/help/implementing/developing/introduction/rapid-development-environments.md) steunen nu front-end code die op [ plaatsthema&#39;s ](/help/sites-cloud/administering/site-creation/site-themes.md) en [ plaatsmalplaatjes ](/help/sites-cloud/administering/site-creation/site-templates.md) wordt gebaseerd, voor vroege adopters.  Met RDEs, wordt dit gedaan gebruikend een richtlijn van de bevellijn, eerder dan a [ front-end pijpleiding ](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Neem contact op met **<aemcs-rde-support@adobe.com>** om het uit te proberen en feedback te geven.

#### Verbeterde logboekregistratie voor RDE&#39;s (Early Introducter Program) {#rde-logging-early-adopter}

Terwijl het zuiveren van code in a [ Snelle Milieu van de Ontwikkeling (RDE) ](/help/implementing/developing/introduction/rapid-development-environments.md), kunnen de ontwikkelaars logboeken nu vormen en stromen efficiënter, gebruikend de bevellijn, en zonder eigenschappen te wijzigen OSGI in versiecontrole. Functies:

* Logniveaus declareren op een niveau per pakket of klasse
* de indeling voor loguitvoer aanpassen
* meerdere logbestanden parallel streamen

Neem contact op met **<aemcs-rde-support@adobe.com>** om het uit te proberen en feedback te geven.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
