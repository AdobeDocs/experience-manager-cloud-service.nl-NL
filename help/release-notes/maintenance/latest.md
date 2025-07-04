---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 080a79cdc0e48a54570ea53618b1f0be164d5156
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 21331 {#21331}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 21331 samengevat, die op 24 juni 2025 openbaar werd gemaakt. De vorige onderhoudsrelease was release 2193.

De activering van de 2025.7.0-functie biedt de volledige functionaliteit die is ingesteld voor deze onderhoudsrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-21331}

* CQ-4356522: `WorkflowResourceStatusProvider` optimalisatie.
* FORMS-16458: UI voor het kiezen van fonteigenschappen (font).
* FORMS-17707: AEP-connector werkt niet voor AEP-platformfase.
* FORMS-19125: ondersteuning voor automatische fragmenttoewijzing in AF-editor.
* FORMS-1936: Onderzoek toegevoegd in de Boom van Gegevens Source in AF redacteur.
* FORMS-19417: Ondersteuning voor keuzerondjes in Hiërarchieweergave.
* FORMS-19603: Ondersteuning voor stramienpagina en ontwerppagina, beide in Rule-editor.
* SITES-5358: Content Fragments Rest API: Copy CFs with children.
* SITES-10575: De &quot;Lader van het Bloomfilter van de Vervaging MSM&quot;probeert om meer dan 100000 rijen te laden.
* SITES-14542: Het anders noemen van/het bewegen van een levende exemplaarbron pagina zou het publiceren van de anders genoemde/verplaatste levende exemplaarpagina moeten teweegbrengen voor het geval het eerder werd gepubliceerd.
* SITES-19754: Edge Delivery met Universal Editor: voeg een leesbare foutmelding toe als de integratie problemen heeft.
* SITES-23499: Edge Delivery met Universal Editor: voeg ondersteuning toe voor meerdere velden die worden gebruikt voor blokopties.
* SITES-23518: Edge Delivery met Universal Editor: voeg ondersteuning toe voor Edge Delivery-specifieke asset-uitvoeringen.
* SITES-24436: Content Fragments Rest API: Introduced local cache to speed up the retrieve duplicate references.
* SITES-25155: Content Fragments Rest API: Remove deprecated &quot;enabledForFolder&quot;vraagparam on Models list.
* SITES-25913: Content Fragments Rest API: time-box bevestiging van middelen alvorens de publicatiewerkschema te beginnen.
* SITES-25976: Koppelingen binnen ervaringsfragmenten die zich niet aanpassen na MSM-implementatie.
* SITES-26271: Content Fragments Rest API: switch to BFS Traversal for the GET Variation Endend.
* SITES-27486: Universal Editor - AEM Integration.
* SITES-2775: Geoptimaliseerde zoekopdracht naar verwijzingen tijdens publicatie (metagegevens worden niet geladen).
* SITES-27782: Edge Delivery met Universal Editor: voeg specifieke implementatie van uitgevers-abonnees toe om inhoud te publiceren naar Edge Delivery (vroege toegang).
* SITES-27792: Edge Delivery met Universal Editor: voeg een speciale Edge Delivery Service Configuration-sjabloon toe.
* SITES-2857: Content Fragments Rest API: Allow using ETags retrieve by call `/cf/fragments/{fragmentId}` with `references=direct` to patch a Content Fragment.
* SITES-28683: Sta de onderzoeken van MSM LiveRelationship toe om geavanceerde status over te slaan.
* SITES-29601: Content Fragments Rest API: Validation for long text fields’ content fragment references.
* SITES-29614: Content Fragments Rest API: Haal een werkschema terug gebruikend het `/cf/workflows/{workflowInstanceId}` eindpunt, waar een workflowInstanceIda identiteitskaart door het publicatieverzoek is teruggekeerd.
* SITES-29615: Content Fragments Rest API: List all batch request created via POST `/cf/batch` using `GET /cf/batch`.
* SITES-29874: Content Fragments Rest API: References from long text fields of content fragments are now retrieve and hydrated.
* SITES-29930: Content Fragments Rest API: add metrics for the Content Fragment Publish workflow.
* SITES-29986: Content Fragments Rest API: support CF Model technical naming.
* SITES-30088: Content Fragments Rest API: CF Publish - skip terugwinning van verwijzingen wanneer filterReferencesByStatus leeg is.
* SITES-30126: Content Fragments Rest API: CF Publish performance improvements: vervang de controle als een bron een fragment is met een minimale controle.
* SITES-30328: Edge Delivery met Universal Editor: voeg ondersteuning toe voor voorvertoning vanuit Sidekick.
* SITES-30445: Content Fragments Rest API: CF Model UI schema: voeg een optie toe om aanvankelijke staat van inklapbaar te controleren.
* SITES-30604: Content Fragments Rest API: support Model Metadata Schema adoption in new UI.
* SITES-30885: Geoptimaliseerde verwerking JSON in persisted query.
* SITES-30886: Content Fragments Rest API: GET-workflows voor het eindpunt van Content Fragment op basis van fragmenthulpprogramma&#39;s die zijn opgeslagen in workflowmetagegevens.
* SITES-31005: Verbeter de interface van de Taak van de Uitvoer om de vooruitgang te tonen.
* SITES-31020: Verbeter de functie Live kopie maken om de voortgang weer te geven.
* SITES-3111: Content Fragments Rest API: Allow variation patch API to accept Content Fragment references within Content Fragment launches.
* SITES-31343: De Rest API van de Fragmenten van de inhoud: Voeg het filtreren en paginering door datum aan eindpunt toe dat van partijverzoeken een lijst maakt.
* SITES-31472: Launch (Starten van verwijderen) kan ertoe leiden dat de repository wordt gepauzeerd als het programma massaal wordt gestart.
* SITES-31641: Content Fragments Rest API: Add property to model fields for storage dynamic maps related to extensions.
* SITES-31677: Aangepaste werkruimte ondersteunt AEM Content fragment dat wordt geëxporteerd naar Doel.
* SITES-31770: Content Fragments Rest API: PATCH performance improvements.
* SITES-31782: Content Fragments Rest API: add a description for local assets.
* SITES-32175: Sta tussenliggende verbintenissen voor zowel het creëren van Actieve Exemplaar als de Inschrijving van de Pagina toe MSM.

### Opgeloste problemen {#fixed-issues-21331}

* CQ-4359756: De vertaalregels bevatten nu filtereigenschappen op componentniveau.
* CQ-4359826: Hiermee verhelpt u een inconsistente status in het referentievenster voor inhoudsfragmenten.
* CQ-4359866: De klasse LanguageUtils ondersteunt nu eenheidstest zonder extra afhankelijkheid toe te voegen.
* FORMS-13990: Forms Service API&#39;s: Document Generation : gegevensveld wanneer leeg gelaten nadat deze is geselecteerd, geeft 200 wanneer verwacht wordt 400.
* FORMS-14309: Forms Service APIs: Rectificatie van de Code van de Reactie van de Gegevens van het Uittreksel.
* FORMS-18526: Wanneer een regel met meerdere velden in voorwaarden wordt gekopieerd, verandert het vaste veld niet.
* FORMS-18977: DOR-service geeft geen titel van het document door.
* FORMS-19047: Vertalingen ontbreken na publicatie van een adaptief formulier op AEM Forms op SP22.
* FORMS-19234: De tijdlijnfunctie van PDF&#39;s kan niet worden gebruikt in AEM-formulieren.
* FORMS-19628: In automatisch gegenereerde DOR, met uitzondering van de geneste venstertitel, verbergt u ook de titel van het hoofdvenster.
* FORMS-19651: De regel van de correctie wanneer een geklikte knoop in binaire voorwaarde wordt gebruikt en ook wordt de zelfde knoop gebruikt in toen verklaring.
* FORMS-19808: FormsPortal - Concepten kunnen niet worden verwijderd wanneer het laden is ingeschakeld.
* FORMS-1987: Toegang eigenschap werkt niet in HTML5 Preview.
* SITES-15452: Unieke CF-elementen mogen in de lancering niet op hun kopieën worden gecontroleerd.
* SITES-24492: De tablijst van ARIA heeft geen toegankelijke naam.
* SITES-24623: Content Fragments Rest API: fix ETag mismatch tussen eindpunten voor zelfde CF.
* SITES-24668: Verwijzingen naar de spoorwegfunctionaliteit worden onderbroken wanneer het zoomen wordt verhoogd tot 400%.
* SITES-24678: References Rail statusbericht wordt niet aangekondigd door schermlezer.
* SITES-24697: De laadstatus van het afbeeldingsmodel wordt niet aangekondigd door de schermlezer.
* SITES-24708: De functionaliteit van de Spoorstaaf van filters breekt wanneer het gezoem tot 400% wordt verhoogd.
* SITES-25235: Bericht bij het laden van inhoud per spoor filteren wordt niet door schermlezers aangekondigd.
* SITES-25254: De horizontale schuifbalk wordt weergegeven in de Carousel-module wanneer de inhoud wordt weergegeven bij een resolutie van 320 px.
* SITES-25433: Edge Delivery met Universal Editor: Fix rendering van paginaversies voor meertalige sitestructuren.
* SITES-26064: Content Fragments Rest API: Fix status code returned when creating a fragment and getting an `AccessDeniedException` in the backend.
* SITES-26890: Bij gebruik van Keyboard is de focus van het toetsenbord &#39;Tabelkoppen&#39; in bereik niet zichtbaar op de pagina Publicatie beheren.
* SITES-29075: Live Copy-overzicht werkt niet voor websites met grote volumes.
* SITES-29514: Edge Delivery met Universal Editor: maak GitHub/Project-URL verplicht wanneer u een nieuwe site maakt.
* SITES-29691: Kan de pagina niet verplaatsen in specifieke gevallen van opstarten.
* SITES-29745: Content Fragments Rest API: implementeer hydratie van referenties variaties in BFS traversal.
* SITES-29748: Corrigeer renderconditions om beheerpublicatie/quickpublish-handelingen in de CF-editor weer te geven.
* SITES-29789: Component link change issue on copy root pages.
* SITES-29987: Content Fragments Rest API: Create &amp; Edit Content Fragment Model don&#39;t support `previewUrlPattern` (Engelstalig).
* SITES-30140: probleem met twee vensters bij het maken van een verwijzing naar een inhoudsfragment.
* SITES-30327: Content Fragments Rest API: het publiceren CFs zonder toestemmingen leidt tot afzonderlijke werkschema&#39;s voor elke nuttige ladingsmiddel.
* SITES-30333: Lees metagegevens over elementen van jcr om problemen met xmp-parsering te voorkomen.
* SITES-30353: GraphQL DataFetchingExceptions for &quot;src&quot; Field in AEM Content Fragments.
* SITES-30377: Edge Delivery met Universal Editor: organiseer- en sitenames.
* SITES-30386: Edge Delivery met Universal Editor: verwijder gedupliceerde, verouderde UE `cors.js` .
* SITES-30583: Content Fragments Rest API: Find &amp; Replace tool changing all characters to lower case.
* SITES-30585: Content Fragments Rest API: `previewUrlPattern` niet ingesteld bij het maken van CFM&#39;s met verwijzingen.
* SITES-30634: RTF-tekst en -uitlijning van afbeelding met RTE werken niet consistent.
* SITES-30660: ADA-compatibiliteitsprobleem met aangepaste AEM-component.
* SITES-30695: Edge Delivery met Universal Editor: de rangorde van de rewriter-pijplijn verhogen om zich niet te mengen in aangepaste code.
* SITES-30727: Kan componenten niet slepen en neerzetten in de Editor van de productieauteur.
* SITES-30752: Gebruik `If-modified-since` niet/ `last-modified` kopballen wanneer het produceren van voortgezette vraagreactie.
* SITES-30871: De Updates van het DOM nadat de nabewerkingsluisteraar wordt teweeggebracht.
* SITES-30877: Onjuiste status voor rollout van onderliggende pagina.
* SITES-30899: Met de optie Later uitrollen kunt u doorgaan zonder dat een datum is geselecteerd.
* SITES-30947: Null-aanwijzeruitzondering vanwege ontbrekende eigenschap &quot;behavior&quot; op blauwdruk tijdens rollout.
* SITES-31157: Content Fragments Rest API: patch Fails is specific case.
* SITES-31162: Content Fragments Rest API: Fix casting issue for `DateTimeField` field in `ModelFieldMapper` .
* SITES-31174: Content Fragments Rest API: Tags zijn niet samen met een publicatieverzoek gepubliceerd.
* SITES-31272: Kan Assets-taalkopie niet maken via PageManager.copy.
* SITES-31327: Content Fragments Rest API: remove ETag validation in GET Fragment request.
* SITES-31387: JavaScript-fout &quot;ns.ui.alert is geen functie&quot; wanneer overerving van spookcomponenten opnieuw wordt ingeschakeld.
* SITES-31454: Content Fragments Rest API: Relax pattern for fragment reference fields to accept UUUIDs.
* SITES-31455: Content Fragments Rest API: fix ETag Mismatch Between Endpoints for the same Content Fragment Model.
* SITES-31459: Content Fragments Rest API: CF Live copy kan niet worden bewerkt wanneer er een content-reference veld is.
* SITES-31467: js-errors van contextthub.authoring-aak.js in de pagina-editor.
* SITES-31487: Content Fragments Rest API: Allow permissions eindpunt to be called for root folder.
* SITES-31621: Edge Delivery met Universal Editor: verwijder lege rij uit werkbladen die live kopieën zijn.
* SITES-31676: Bij het ontwerpen of verwijderen van componenten blijft er onder aan de pagina een lege ruimte staan.
* SITES-31822: ClassicUI Checkbox-label ontbreekt &amp; gecodeerde HTML.
* SITES-31857: De creatie van CF ontbreekt in omslagen met enige citaten.
* SITES-31888: De schrapping van de Fragmenten van de inhoud kan niet aan Voorproef verspreiden.
* SITES-31922: Content Fragments Rest API: de paginaverwijzingen zijn niet teruggekeerd door referencedBy eindpunt.
* SITES-31987: toon voorproef geen URLs voor de Fragmenten van de Inhoud wanneer het publiceren van hen aan Voorproef.
* SITES-32095: Automatisch vernieuwen mislukt na verwijderen van gebeurtenislistener in Live Copy.
* SITES-32237: Edge Delivery met Universal Editor: herstel van lege/onjuist gevormde tekstcomponenten herstellen.

### Bekende problemen {#known-issues-21331}

* SITES-33177: Sectiestijlen die zijn opgeslagen als door komma&#39;s gescheiden tekenreeksen, worden verbroken.

### Verouderde functies en API&#39;s {#deprecated-21331}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-21331}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 21 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-21331}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 80,0 | [ Oak API 1.80.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.28-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2 29,0 | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
