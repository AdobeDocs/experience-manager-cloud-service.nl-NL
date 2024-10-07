---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: ee3e1bedddddff0aa41665359a91a0de48fd19c8
workflow-type: tm+mt
source-wordcount: '1411'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 17964 {#release-17964}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 17964 samengevat, die op 25 september 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 17689. Release 17882 is privé gemaakt vanwege een uitgave.

De activering van de 2024.10.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-17964}

* ASSETS - 37750: [ Prioriteit 4 ] [ GraphQL ] Steun voor DM scene7 URLs: beeld slimme gewassen.
* CQ - 4354583: [ AEMaaCS ] verzendt de gebeurtenissen van het vertaalproces via de Pijpleiding van de Adobe.
* CQ - 4357642: Werk MSFT-referenties bij in OOTB-connector.
* CQ - 4358217: Deserialize request body from request entity.
* CQ - 4358342: Registreer RequestProcessors voor slechts één HTTP-methode.
* FORMS - 10781: Verbeter regeleditor om regels te maken voor volgende/vorige item in een deelvenster.
* FORMS - 14595: ] de Waarden van de Eigenschap 0} Browserless ontbreken in DoR wanneer de vooraf ingevulde gegevens worden gebruikt om DoR voor Browser het teruggeven te berekenen.[
* FORMS - 15619: AEM Forms Updated Translation Kit.
* FORMS - 16113: [ Adobe Sign ] Onbekwaam om overeenkomststatus door een verschillende gebruiker bij te werken.
* FORMS - 16155: [ de Redacteur van de Regel ] voert functie Async uit.
* GRANITE - 53872: voeg nieuwe env vars toe voor IMS Client ID.
* SITES - 23738: Release Core Components 2.27.0.
* SITES - 16610: Content Fragments: Get lanceringsdetails eindpunt.
* SITES - 16614: Content Fragments: Rebase Launch eindpunt.
* SITES - 16615: Content Fragments: Promote het eindpunt van de Lancering.
* SITES - 24215: De Fragmenten van de inhoud: Voer krijgen de bronnen van de Lancering eindpunt uit.
* SITES - 2036: Inhoudsfragmenten: Verbeter de validatie bij het verwijderen van een Inhoudsfragmentmodel.
* SITES - 21090: Content Fragments: Add support for fractional min/max values for number fields
* SITES - 21658: Content Fragments: Upgrade to use UUID-references.
* SITES - 23054: Content Fragments: Copy Content Fragment Models.
* SITES - 23264: Content Fragments: Create a static schema of a model.
* SITES - 23265: De Fragmenten van de inhoud: blootstellen het statische schema van een model door het het schemaeindpunt van UI.
* SITES - 23266: Content Fragments: Capability to add constraints to Content Fragment Models.
* SITES - 23778: Content Fragments: Search Content Fragment Models should allow search for models that have never been published.
* SITES - 23335: Content Fragments: Add support for external asset references.
* SITES - 24626: Inhoudsfragmenten: RTC: Machtigingen voor UUID-migratie: 2.
* SITES - 24786: Inhoudsfragmenten: Verbeteringen voor het eindpunt `referencesTree` .
* SITES - 24833: Inhoudsfragmenten: verwijder de validatie van invoer van HTML aan de hand van een lijst met toegestane HTML-tags.
* SITES - 23380: GraphQL: gebruik de juiste API voor het lezen van metagegevens van elementen.
* SITES - 22864: [ Edge Delivery ] Universele redacteur met de nieuwe integratie van de AEM inhoudsstructuur H2 2024.
* SITES - 23584: De componenttests van de Stichting ontbreken op Java 17.
* SITES - 23662: Event: User that triggers a publish request cannot be extracted from JCR log statements in server logs.
* SITES - 23301: Voeg ondersteuning toe voor het starten van een nieuwe workflow om mapstructuren te maken bij het maken van vertalingen van inhoudsfragmenten.
* SITES - 2336: Content Fragments: Add support for external asset references
* SITES - 24091: Splitsing MSM-inhoudspakket: stramien.
* SITES - 24114: isSourceRenderCondition: Verminder het bericht van het foutenlogboek aan DEBUG.
* SITES - 24166: Verre activa matiging voor redacteur touch-UI.
* SITES - 24409: Registreer alle request processors op slechts één HTTP-methode.
* SITES - 25008: Verbeter de behandeling van PersistenceExceptions en toestemmingsproblemen.
* SITES - 24821: Make aem.page / aem.live the default.

### Opgeloste problemen {#fixed-issues-17964}

* CQ - 4356887: Inconsistentie in de status van vertaalprojecten voor Akamai Technologies Inc.
* CQ - 4357878: Het vertaalkader stelt geen foutenstatus bij de vertaling van mislukte leveranciers in.
* CQ - 4358028: Kan project niet maken als de miniatuur wordt geüpload.
* CQ - 4358290: De doelinstelling werkt niet op gepubliceerde pagina.
* FORMS - 13173: Verkeerd uitlijnen vervolgkeuzelijst in Adaptief formulier > Regeleditor > Slagobjectveld.
* FORMS - 13873: AFv2: (&quot;-&quot;) in de naam van de component resulteert in een fout in de regels.
* FORMS - 14340: fout in het concretiseren van FormsAndDocumentOmniSearchHandler en CloudStorageSubmitActionInserter.
* FORMS - 15363: Weergegeven naam in de Regeleditor.
* FORMS - 15381: UI enhancement of Authorization Scope message.
* FORMS - 15595: AEM Formulier TnC Component Consent Text line break issue.
* FORMS - 15623: AEMaaCS Forms - Alternatieven voor het bijwerken van meerdere tabellen in dynamiek met één POST.
* FORMS - 15682: AEM Forms - Kan DOR niet binden aan Dynamics FDM.
* FORMS - 15799: Adobe Sign GovCloud-pagina voor handtekeningen wordt niet weergegeven in iframe.
* FORMS - 15835: URL na verzending herschrijft uitgave.
* FORMS - 16091: De geherstructureerde Binary.java gebruiken.
* FORMS - 16.096: Forms-gebruiker heeft geen toegang tot het dialoogvenster voor het opnieuw instellen van het eindpunt.
* FORMS - 16139: vereiste logboekregistratie voor DoR toevoegen in de vorm van kerncomponenten.
* FORMS - 6935: De toestand van de actieve component heeft een contrastverhouding van 3 tot 1.
* FORMS - 7018: Leeg element krijgt focus.
* GRANITE - 53028: NPE in ExternalProcessPollingHandler.
* GRANITE - 53907: Kan de servicegebruiker niet identificeren als supergebruiker van de workflow.
* SITES - 24405: Content Fragments: Extended Info for enums should be veerlient
* SITES - 23024: Inhoudsfragmenten: opsomming retourneert niet vergrendeld: true in GET-fragmenten.
* SITES - 23269: Content Fragments: Creating Content Fragments allows set locked fields.
* SITES - 2337: Content Fragments: Batch-eindpunt met `body` mislukt met casting-uitzondering.
* SITES - 23474: Content Fragments: Pagination should exclude broken resources in Search Content Fragments.
* SITES - 23615: Content Fragments: Content Fragment copy Authoring Info is not updated
* SITES - 23668: Content Fragments: Patch live copy with multifield failed with 400
* SITES - 23695: Content Fragments: Tab description is not available in UiSchema
* SITES - 23704: Content Fragments: Multi-value enums not supported in _extendedInfo
* SITES - 23781: Inhoudsfragmenten: dubbele waarden niet toegestaan in opsommingsvelden
* SITES - 24150: Content Fragments: Content Fragment Version Authoring data about creation is missing
* SITES - 24230: Content Fragments: Fix filtering after `modified` replication status in Search Content Fragment Models
* SITES - 24233: Inhoudsfragmenten: Filteren op `publishedBy` kan niet-gepubliceerde bronnen bevatten in Modellen met zoekinhoudfragmenten
* SITES - 24355: Inhoudsfragmenten: Live relatie wordt niet gerespecteerd voor voor mappen gemaakte inhoudsfragmenten
* SITES - 24816: Content Fragments: ValidationStatus messages order inconsistent.
* SITES - 23896: Eventing: Meer gebeurtenissen komen samen met een gebeurtenis Pagina verplaatsen
* SITES - 23899: Event: Page events are delayed or not generated at all
* SITES - 23961: Event: Creating Content Fragment Models with references failed when configuration folder is present
* SITES - 23963: Gebeurtenis: gebeurtenissen die worden verwijderd uit de pagina komen soms niet voor
* SITES - 23443: GraphQL: GraphQL Cursor query inconsistent gedrag.
* SITES - 10994: De focusvolgorde van het toetsenbord is niet logisch.
* SITES - 16357: AEM: De knop wordt afgekapt op het tabblad Setup Analytics van het menu Sites.
* SITES - 19836: Ghost-component in container wordt weergegeven op publicatie- en voorvertoningsinstanties.
* SITES - 22348: Live Copy Overview page kan niet worden geladen als de pagina&#39;s meer dan 100 live kopieën voor een project bevatten.
* SITES - 22960: Niet-afgesloten resource resolver in ContentFragmentModelOmniSearchHandler.
* SITES - 23284: URL-codering leidt tot een leeg dialoogvenster van de padbrowser.
* SITES - 23505: Componenten geven onjuiste URL&#39;s weer wanneer de pagina naar een andere locatie wordt verplaatst.
* SITES - 23574: Kan voor veel pagina&#39;s geen voorvertoning/vergelijking maken met de huidige versies
* SITES - 23585: Issue with Restoring Inheritance for components having cq:responsive node
* SITES - 23650: Discrepancy in Incoming Links Count in AEM Author Environment
* SITES - 23659: Content Language Servlet regression due by the toggle FT_* SITES - 9757
* SITES - 23759: Assets toegevoegd aan ervaringsfragment wordt niet gepubliceerd met Startpagina&#39;s
* SITES - 24025: 302 Omleidt in AEM terugkerende plaatsheader gebruikend interne DNS in plaats van openbare DNS
* SITES - 24036: Onderzoek vereist voor AEM blijvende tekens van RTE in ASCII-indeling
* SITES - 24317: Proxyconfiguratie werkt niet met basisverificatie
* SITES - 24918: bevestig 504 fouten die af en toe zijn teruggekeerd wanneer het gebruiken van specifiek ip egress.

### Bekende problemen {#known-issues-17964}

* FORMS - 15818: Component descriptor-item `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` niet gevonden instructies in serverlogboeken. Dit zijn ongevaarlijke loginstructies.

### Verouderde functies en API&#39;s {#deprecated-17964}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

Hieronder volgt een overzicht van onlangs vervangen functies of functies die verouderd zijn.

#### JavaScript Use API {#javascript-use-api}

[ het Gebruik API van JavaScript ](https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#42-javascript-use-api) wordt officieel verouderd toe te schrijven aan uitdagingen hebben de gebruikers het zuiveren en het handhaven van code die hefboomwerkingen API, evenals prestatiesbeperkingen in vergelijking met het alternatief van Java.

U zou overgang aan [ het Gebruik API van Java moeten overschakelen, ](https://experienceleague.adobe.com/en/docs/experience-manager-htl/content/java-use-api) dat betere prestaties, gemakkelijkere zuivering, en grotere steun op lange termijn aanbiedt.

#### com.day.cq.wcm.api {#com-day-cq-wcm-api}

Houd er rekening mee dat de Adobe bezig is met het bijwerken van `com.day.cq.wcm.api` . Sommige methoden en klassen zijn in de huidige release gemarkeerd als `@Deprecated` . Deze worden in toekomstige versies verwijderd. Overstappen op de voorgestelde alternatieven.

### Beveiligingsproblemen {#security-17964}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 16 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-17964}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 68,0 | [ Oak API 1.68.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.68.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | {de Specificatie van de Taal van het Malplaatje 0} HTML ](https://github.com/adobe/htl-spec)[ |
| AEM-kerncomponenten | 2 27,0 | [ AEM de Componenten van de Kern WCM ](https://github.com/adobe/aem-core-wcm-components) |
