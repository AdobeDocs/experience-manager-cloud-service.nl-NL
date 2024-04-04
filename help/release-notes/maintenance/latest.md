---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: d07fc976fe9c8e7872468048f80e525fe8484339
workflow-type: tm+mt
source-wordcount: '2584'
ht-degree: 0%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 15787 {#release-15787}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 15787 samengevat, die op 4 april 2024 openbaar werd gemaakt. De vorige onderhoudrelease was release 15575.

2024.3.0 Activering van functies biedt de volledige functionaliteit die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-15787}

* SITES-19059 - Content Fragments - OpenAPI - Allow defaultValue for enum fields
* SITES-20013 - Content Fragments - OpenAPI - WCMScriptHelper zou het teruggeven moeten afbreken wanneer geen ServerResolver aanwezig is
* SITES-19926 - Inhoudsfragmenten - OpenAPI - Verbeteringen aan OnOffTriggerProcessor
* SITES-17945 - Content Fragments - OpenAPI - Get last modified metadata for each version
* SITES-17298 - Content Fragments - OpenAPI - Content Fragment Models Permissions
* SITES-14255 - Content Fragments - OpenAPI - Valideer eenheid van tekstveld als een unieke markering is ingesteld in het fragmentmodel
* SITES-1557 - Content Fragments - OpenAPI - Allow defaultValue for enum fields
* SITES-1559 - Inhoudsfragmenten - OpenAPI - CF-lijst-API bijwerken om alleen fragmenten van directe onderliggende inhoud (BE) op te halen
* SITES-16052 - Inhoudsfragmenten - OpenAPI - Voeg de URL toe voor de instantie waar een bron kan worden gebruikt
* SITES-17944 - Inhoudsfragmenten - OpenAPI - Juiste JCR ACLs afbeelding aan het eindpunt van de Toestemmingen van CF
* SITES-17513 - Content Fragment Control Plane - Unpublish content fragments
* SITES-8831 - Content Fragment Control Plane - PUT - Update a fragment with full information
* SITES-8836 - Inhoudsfragmenten - OpenAPI - Controlevlak - GET Referenties - Bovenliggende referenties van een fragment ophalen (door UUID)
* SITES-8986 - Inhoudsfragmenten - OpenAPI - Inhoudsfragmentmodel publiceren
* SITES-18073 - Content Fragments - OpenAPI - PreviewURL Pattern for a CFM
* SITES-15242 - Inhoudsfragmenten - OpenAPI - De publicatiegebeurtenissen uitbreiden om informatie over de laag te verschaffen
* SITES-18702 - Inhoudsfragmenten - OpenAPI - [Achtergrond] Publiceren op mapniveau
* SITES-20020 - Inhoudsfragmenten - OpenAPI - Verwijderen `X-Adobe-Accept-Unsupported-API` voor GA
* SITES-16066 - Inhoudsfragmenten - Fragmenteditor - JS URL voor kiezer voor element wijzigen
* SITES-19326 - Inhoudsfragmenten - Fragmenteditor - Koppelingen in Elementen-UI bijwerken om CF te openen in de nieuwe CF-editor
* SITES-10515 - Content Fragments - GraphQL API - GraphQL - AbstractFetcher Performance Issue Loading referenced Content Fragments
* SITES-17364 - Content Fragments - GraphQL API - Return Full Name for the Modified by and Published by properties
* SITES-19165 - Content Fragments - GraphQL API - Allow global models to be used, referenced and queryable in all GraphQL endpoints
* SITES-17768 - Inhoudsfragmenten - GraphQL API - Dynamic Media-URL voor afbeeldingen beschikbaar maken via _dmS7Url
* SITES-11057 - Core Backend - Laad niet alle versies wanneer u Tijdlijn > Versies opent
* SKYOPS-63033 - HTTPD - Witruimten van verzender milieuvariabelen bijsnijden
* SKYOPS-65518 - HTTPD - De validator kan niet worden gevalideerd als er ongeldige bestandsnamen in de map dispatcher staan
* SITES-19626 - Launches - Voeg DAM-CFM lastUpdate-velden samen tot hoofd
* SITES-19251 - Quick Site - Creation Wizard - Support sites admin ui side rail when theme reference not equals site name
* SITES-15430 - Universele Redacteur - Universele Redacteur onder AEM Domein
* CQ-4344966 - WCM - Vertaling - Basiskader creëren voor structurele update van sites en bestaande bijwerken voor middelen
* CQ-4347312 - WCM - Vertaling - Een workflow maken om &quot;cq:translationsourcejcruid&quot; in bestaande bron- en taalkopieën te koppelen
* CQ-4354509 - WCM - Vertaling - Publicatie van vertaalwerkzaamheden [OSGi EventAdmin]
* SITES-16318 - Crosswalk - AEM-based authoring with Edge Delivery Services
* FORMS-9889: De gebruiker kan de POST URL en de configuratie van de Wolk terwijl het vormen van de Submit actie voor voorleggen aan het Eindpunt van REST toevoegen
* In de regeleditor kunnen gebruikers:
   * FORMS-12160: Valideer een veld, deelvenster of formulier in de sectie Dan van de voorwaarde Wanneer.
   * FORMS-12570: Een veld, deelvenster of formulier opnieuw instellen in de sectie Dan van de voorwaarde Wanneer.
   * FORMS-11541: Gebruik veldobjecten en globale objecten in de regeleditor via de aangepaste functies.
   * FORMS-11714: Definieer parameters als optioneel in de aangepaste functie. Parameters die in aangepaste functies worden gedeclareerd, zijn standaard verplicht.
   * FORMS-11756: Gebruik caching voor douanefuncties om de reactietijd te verbeteren wanneer het terugwinnen van de lijst van de douanefunctie in de regelredacteur.
   * FORMS-12053: Voeg een instructie &#39;else&#39; toe in de voorwaarde &#39;When&#39; om geneste voorwaarden te implementeren.
   * FORMS-11269: gebruik moderne ES10 JavaScript-functies zoals let- en pijlfuncties in de aangepaste functie voor basiscomponenten gebaseerde formulieren.

* FORMS-9014: Verschillende verbeteringen op het gebied van toegankelijkheid voor de component Scripthandtekening


### Opgeloste problemen {#fixed-issues-15787}

* Verschillende problemen met toegankelijkheid en internationalisatie zijn opgelost
* SITES-16966 - AEM: Niet-gelokaliseerd &quot;Niet versioned!&quot; string in Sites > Herstellen > Tree herstellen
* SITES-16208 - De ContentFragmentModelIdentifier stelt een misleidende titel-eigenschap bloot
* SITES-18024 - Wanneer de if-Match kopbal mist, moet de reactie 428 zijn
* SITES-18003 - De gebruiker die een versie creeerde is niet correct teruggekeerd
* SITES-17937 - De gebeurtenis Gemaakt inhoudsfragment wordt verzonden voordat de auteurspods zijn gesynchroniseerd
* SITES-18029 - De afsluitende verwerkingspijplijn loopt vast wanneer deze gelijktijdig door de waarnemingen van het JCR wordt aangemeld
* SITES-17882 - De maximale lengte van fragmenttekstvelden verwijderen uit het schema
* SITES-19252 - Inconsistenties in verband met de HTTP-statuscode 406 en 415 herstellen
* SITES-16964 - [Achtergrond] Sorteren op &quot;Gewijzigd door&quot; werkt niet correct
* SITES-17519 - Site Page properties Editor - Lange paginanaam maakt de knoppen niet-klikbaar
* SITES-16852 - Publicatie-API publiceert verwijzingen met NIEUWE status
* SITES-18833 - Uniqueness constraint in not visible in OpenAPI endpoints
* SITES-1553 - Het zijpaneel van XF kan niet worden geladen als de URL van XF een kiezer bevat
* SITES-14340 - NPE in VersioningTimelineEventProvider.accept
* SITES-1605 - [Sites] DeletePageCommand genereert NPE in het geval van null source-path
* SITES-16308 - [GB18030]: Er wordt een waarschuwingsbericht weergegeven wanneer u een nieuwe map Sites maakt met de naam GB18030-tekens
* SITES-16304 - [GB18030]: Er wordt een waarschuwingsbericht weergegeven wanneer u de nieuwe map Experience Fragments maakt met GB18030-tekens
* SITES-8769 - De prestaties van StyleImpl verbeteren
* CQ-4343815 - Campagne - gericht - De standaardvariant van een gummetje heeft lege URL
* CQ-4355889 - Campagne - gericht - creeer het verzoek van het Publiek ontbreekt met Config IMS.
* SITES-12460 - Campagne Integration - Campagne / AEM Cloud Service Integration verbroken
* SITES-11571 - Content Fragments - GraphQL API - PersistedQueryServlet zou 400 s op misvormde URLs moeten verzenden
* SITES-19946 - Inhoudsfragmenten - GraphQL API - Modellen worden bij het opstarten niet meer gescand
* SITES-1605 - de Achtergrond van de Kern - DeletePageCommand werpt NPE in geval van ongeldige bron-weg
* SITES-5429 - Kernback-end - ChildrenListServlet itemResourceType staat directe uitvoering van code toe
* SITES-1553 - Fragmenten voor ervaring - Het zijpaneel van XF kan niet worden geladen als de URL van de XF een kiezer bevat
* SITES-13666 - Headless - Admin - Error Log False Positive &quot;com.adobe.cq.dam.cfm.headless.ui.impl.models.CFHomeCardModelImpl Config Id must not be null&quot;
* SITES-17164 - Pagina-editor - [Wolk, 6.5 Forms] De voorvertoning van de AF-themaeditor is verbroken
* SITES-14340 - Sites Admin UI - NPE in VersioningTimelineEventProvider.accept
* SKYOPS-68611 - het Sling - herricht - de helling van de Haven herricht leidt wegmoeilijke situatie in de onderhoudstak
* CQ-4354678 - WCM - Vertaling - Vertaaltaken exporteren vertaalde inhoud
* CQ-4355167 - WCM - Vertaling - Geen pop-up krijgen tijdens het markeren van een Vertaaltaak voltooid of Archief
* CQ-4355913 - WCM - Vertaling - Vertaling van projecttaalkaarten voor vertaalprojecten
* GRANITE-47694 - Workflow - Kan geen subtaken ophalen in een workflow in de cloud voor gebruikers die geen beheerder zijn
* ASSETS-31097 - Assets Cloud - Logboeken ingevuld met index Doorgestuurde waarschuwingen voor /bin/numberofentitiesinfolders.json
* ASSETS-35860 - Assets Cloud - Onjuiste tijdzoneconversie in de kolomweergave van AEM Assets
* SITES-15260 - Klassieke UI (Verouderd) - Bulkedit voegt EMPTY-eigenschappen op de pagina toe als vel wordt gebruikt
* SITES-16834 - Klassieke UI (Verouderd) - Tekst die na het bewerken van tekst ontbreekt met de Bulk-editor wanneer tekst komma&#39;s bevat
* SITES-17767 - Inhoudsfragmenten - Admin - Ondersteuning toegestaan cf-modellen ook voor mappen zonder een jcr:content-knooppunt
* SITES-17683 - Inhoudsfragmenten - Core Backend - Inhoudsfragmenten zijn niet serialiseerbaar met Jackson-exportfunctie
* SITES-18797 - Inhoudsfragmenten - Core Backend - GraphQL-resultaten gedupliceerd na indexaanpassing
* SITES-18076 - Content Fragments - Core Backend - Multi-value tekst heeft onjuiste @TypeHint
* SITES-17856 - Inhoudsfragmenten - Modellen &amp; ModelRedacteur - CF Modellen niet getoond als config geen omslag is
* SITES-17071 - Core Backend - Specifieke pagina geeft geen versie weer in tijdlijn
* SITES-17285 - Core Components - Inline Image Crop is different on Author and Publish in AEMaCS
* SITES-19187 - Core Components - Twee methoden voor het plaatsen van elementen in een afbeeldingscomponent geven verschillende resultaten bij het dialoogvenster
* SITES-2007 - Core Components - Inline Image Crop - uitsnijden is onjuist en afbeeldingen zijn wazig
* SITES-17211 - Ervaar Fragmenten - Ervaar het dialoogvenster Padkiezer van de component Fragmenten die ervaringsfragmenten toont die worden verwijderd
* SITES-17894 - Launches - De bevordering van geneste lanceringen keert lanceringsinhoud aan een versie van zijn voorvader terug
* SITES-16042 - MSM - Live kopieën - Annotaties worden na rollouts onjuist weergegeven in de Livecopy
* SITES-16691 - MSM - Actieve kopieën - Wanneer de klant &#39;rollout&#39; of &#39;rollout to&#39; selecteert vanuit het &#39;rollout&#39;-pictogram op een component, wordt de knop &#39;continue&#39; grijs weergegeven.
* SITES-16733 - MSM - Actieve kopieën - De pagina van de index van de blauwdruk kan niet worden uitgevoerd wanneer rep:policy op knoop wordt toegepast
* SITES-17155 - MSM - Live kopieën - Kopteksten en voetteksten worden naar het Engels vertaald wanneer de naam van LiveCopy wordt gewijzigd
* SITES-17492 - MSM - Live kopieën - Inconsistenties layout van Live kopie van pagina AEM
* SITES-19316 - MSM - Actieve kopieën - De koppeling Verwijzing naar ervaringsfragment wordt niet bijgewerkt in een taalkopie
* SITES-19347 - MSM - Live Kopieën - Trage berichten van de Auteur van de Prod en de dienststroomonderbreking - pods die vaak opnieuw beginnen - gezondheidsalarm
* SITES-19790 - MSM - Live kopieën - Onjuiste voorvertoningsgegevens na het maken van LiveCopy
* SITES-20086 - MSM - Actieve kopieën - MSM-uitrol voor CF in Assets zal alle levende exemplaren uitrollen, zelfs als één levende kopie is geselecteerd om te worden uitgerold
* SITES-2008 - MSM - Live kopieën - Blanco pagina Issue Post XF Rollout in Properties - AEM as a Cloud Service
* SITES-16854 - Pagina-editor - Dropdoel-bedekking bedekt parsys in componenten met de functie &#39;Deelvenster selecteren&#39;
* CQ-4355563 - Projecten - de wegparameter is verkeerd. Bezig met vullen van &quot;?appId=aemshell&quot; voor zoekscript in postvak van project
* SITES-16876 - Quick Site - Thema-implementatie - CSS en JS ontbreken op voorvertoningspagina&#39;s 2
* SITES-18418 - Sites Admin UI - Functionaliteit voor weergeven/verbergen voor padveld-widget werkt niet correct wanneer veld is vereist
* SITES-19534 - Sites Admin UI - Kan geen efficiënte de Dialoogvenster van Toestemmingen Post AEM 6.5.19 Verbetering openen
* SITES-19203 - Sjablooneditor - Bewerkbaar sjabloonbeleid Tekst verkeerd uitgelijnd en Stijlen overlappen verwijderknop
* CQ-4354881 - WCM - Vertaling - Het pad naar inhoudsfragmenten wordt ingesteld op bron (en-us) wanneer inhoudsfragmenten worden vertaald als onderdeel van een pagina
* CQ-4355289 - WCM - Vertaling - Alleen de eerste 40 elementen worden weergegeven in Cloud Servicen voor vertaling
* CQ-4355866 - WCM - Vertaling - Vertaalworkflow met foutmelding voor bestaande pagina&#39;s
* CQ-4355797 - Workflow - Kan stap OTB-workflow niet gebruiken
* GRANITE-48938 - Workflow - Auteur die in een &quot;hangende publicatie&quot;staat voor activa toont. Probleem in de nieuwe geduurde cache van de payload map.
* GRANITE-49036 - Workflow - verzoek om functies | Mogelijkheid om het leegmaken van workflowpakketten te plannen en te configureren
* SITES-17393 - Workflowextensies - De structuur met de publicatie van inhoud mislukt bij gebruik van workflowdraagraketten voor cq:Tag
* SITES-17759 - Workflowextensies - Tree-Activation-Workflow voor tags die niet werken in AEMaaCS
* FORMS-12411: Op Android-apparaten wordt de `Maximum Number of Characters Validation` werkt niet voor de component Adaptief tekstvak.
* FORMS-13377: Wanneer een gebruiker probeert om de douanefont toe te voegen en de pijpleiding in werking te stellen om het te vormen, ontbreekt het met de fout &quot;ContainersNotReady&quot;
* FORMS-13267: Wanneer een gebruiker een component Adaptief formulier neerzetten toevoegt, kan de id voor het vervolgkeuzemenu niet worden gegenereerd
* FORMS-13544: Wanneer een gebruiker een component Adaptief formulier met een wizardindeling toevoegt, werkt dit niet correct tijdens het ontwerpen van formulieren
* FORMS-13091, FORMS-13414: Als een gebruiker een aangepaste domein-URL probeert te configureren in de opslag van Azure Blob, mislukt dit
* FORMS-13595: Wanneer een gebruiker het formulier probeert op een andere locatie op te slaan, kan de gebruiker de knoppen Map selecteren en Annuleren niet zien als de browserresolutie is ingesteld op 100%. De optie is echter zichtbaar wanneer de resolutie is ingesteld op 75%
* FORMS-10952: Wanneer een gebruiker een component Adaptief formulier neerzetten toevoegt aan een adaptief formulier en de eigenschap &#39;Opties instellen&#39; gebruikt op basis van verschillende aangepaste regels, werkt de eigenschap &#39;Opties instellen&#39; alleen voor de laatste regel
* FORMS-11471: Het lazy laden van een fragment ontbreekt wanneer de vraag &quot;emitter.json&quot;wegens een netwerkonderbreking ontbreekt.
* FORMS-11786: Wanneer een gebruiker in de kalenderwidget tussen maanden schakelt, toont de component van de datumkiezer een extra rij.
* FORMS-12093, FORMS-12093: Wanneer een gebruiker op het selectievakje Adaptief formulier tikt om een formulier te verzenden, wordt de onjuiste waarde met een extra  `\` wordt opgeslagen in het tekstvak
* FORMS-1993: Wanneer een gebruiker op een afbeelding klikt met de optie &#39;Een foto maken&#39; in de bijlage op een iOS-apparaat, worden alle afbeeldingen toegevoegd aan de map met dezelfde naam
* FORMS-12555: Wanneer een gebruiker AEM Forms probeert te integreren in een mailingplatform met een AEM gepubliceerde URL, voegt AEM Forms method=post niet toe tijdens het weergeven van de pagina. Dit probleem doet zich voor, ook al is POST ingesteld in de verzendactie met de URL. Hierdoor herkent het mailplatform dit niet als een formulier
* FORMS-12938: De HTML5-formulieren werken niet of worden niet goed geladen in de Microsoft Edge-browser met IE-compatibiliteitsmodus
* FORMS-12032: wanneer een gebruiker een formulier verzendt, wijst het pad voor het verzendactiepad niet correct.
* FORMS-12445: onjuiste waarden worden vastgelegd in het formuliergegevensmodel nadat de volgorde van de keuzerondjes is gewijzigd en het formulier is gepubliceerd.
* FORMS-12947: wanneer een gebruiker een nieuwe taal aan een bestaand woordenboek toevoegt, kan deze niet worden samengevoegd of toegevoegd
* FORMS-11363: Wanneer een gebruiker een formulier verzendt via Workspace, doet zich tijdens het genereren een weergaveprobleem voor in de tabellen
* FORMS-11756: Wanneer een gebruiker de JavaScript-functies ES6 toevoegt, zoals `let` en `const` in douanefuncties, ontbreekt de regelredacteur om te openen. Deze onderhoudrelease biedt ondersteuning voor ES10
* FORMS-13164: Als de gebruiker een PDF genereert, worden er na verzending onverwachte lege regels aan toegevoegd
* FORMS-13789: Wanneer een gebruiker meerdere PDF probeert te genereren, mislukt de uitvoerbatch-API.
* FORMS-11483: wanneer een gebruiker PDF in PDF/A-2B of PDF/A-3B omzet, kan deze geen validatiefout converteren en weergeven
* FORMS-10501: Wanneer een gebruiker HSM aanroept, worden de documenten gecertificeerd, maar wordt LTV niet ingeschakeld
* FORMS-11546: Wanneer een formulierauteur herhaalde deelvensters in een adaptieve vorm gebruikt, ontbreekt het kenmerk ARIA in de HTML-tags. Hierdoor wordt de toegankelijkheid van herhaalde deelvensters van het adaptieve formulier verbeterd
* FORMS-11826: Dankzij de overeenkomende labels Arial® en Arial® kunnen schermlezers deze twee niet onderscheiden. Om het probleem op te lossen, wordt het label &quot;aria-labelledby&quot; vervangen door &quot;aria-describe by&quot; voor de formuliervelden. (F). Dit verbetert de toegankelijkheid van Adaptive Forms
* FORMS-12626, FORMS-13094: gebruikers hebben geen toegang tot de werkbalk via het toetsenbord om inhoud op te slaan of te bewerken op de pagina met formuliereditors. Dit toegankelijkheidsprobleem is opgelost
* FORMS-13102: Tijdens het formulierontwerpproces ontbreken de pictogrammen op de pagina Forms en Documenten beschrijvende functies voor personen met een verschillende handicap. Dit toegankelijkheidsprobleem is opgelost

### Bekende problemen {#known-issues-15787}

* SITES-17934 - Inhoudsfragmenten - Voorvertoning mislukt vanwege DoS-bescherming voor grote boomstructuur met fragmenten. Zie [KB](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-23945)

### Verouderde functies en API&#39;s {#deprecated-15787}

* [JWT Credentials Deprection in Adobe Developer Console](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

Kijk eens naar [Verouderde en verwijderde functies en API&#39;s](/help/release-notes/deprecated-removed-features.md) om te weten wat in AEM as a Cloud Service is vervangen of verwijderd.

### Kennisgeving wijzigen {#change-notice-15787}

**Handelingen vereist**

#### CM Java-versie instellen op 11 {#set-java-version-11}

De nieuwe versie van aem-sdk-api bevat klassen die met een doel Java 11 worden gecompileerd, die niet compatibel is met de milieu-standaard JDK versie 1.8 van de Manager van de Wolk bouwt. Deze update vereist dat Maven wordt uitgevoerd met JDK 11.

Klanten wordt aangeraden een `.cloudmanager/java-version` bestand naar de hoofdmap van hun waarschuwingsbericht met de inhoud: `11`. Zie [Build Environment / Setting the Maven JDK Version](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#alternate-maven-jdk-version).


### Ingesloten technologieën {#embedded-tech-15787}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM AK | 1,60-T20240131102219-0cde853 | [API voor eik 1.60.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| AEM SLING-API | Versie 2.27.2 | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.2.4 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
