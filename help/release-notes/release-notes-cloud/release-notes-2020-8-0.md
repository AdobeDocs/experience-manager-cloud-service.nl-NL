---
title: Opmerkingen bij de release voor 2020.8.0 [!DNL Adobe Experience Manager] van een Cloud Service.
description: '[!DNL Adobe Experience Manager] als opmerkingen bij de release van Cloud Servicen voor 2020.8.0.'
translation-type: tm+mt
source-git-commit: 130603301212cdb29ae7f395ebc05fc58f64686e
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 0%

---


# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] als Cloud Service 2020.8.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor Experience Manager beschreven als Cloud Service 2020.8.0.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Experience Manager] als Cloud Service 2020.8.0 is 27 augustus 2020.

## [!DNL Adobe Experience Manager Sites] als Cloud Service {#sites}

### What is new in [!DNL Sites] {#what-is-new-sites}

* Mogelijkheid om pagina&#39;s en subpagina&#39;s (paginastructuren) te [herstellen naar een eerdere versie](/help/sites-cloud/authoring/features/page-versions.md#reinstating-versions).

* Mogelijkheid om Launches [te](/help/sites-cloud/authoring/launches/overview.md) maken in AEM [SPA Editor.](/help/implementing/developing/spa/introduction.md)

## [!DNL Adobe Experience Manager Assets] als Cloud Service {#assets}

### What is new in [!DNL Assets] {#what-is-new-assets}

* Videotranscodering wordt nu ondersteund met middelenmicroservices. Met een nieuwe sectie in de [!UICONTROL Processing Profiles] configuratie kunt u de bitsnelheid en afmetingen voor de video instellen. De uitvoerindeling is MP4 met H.264-codec. Zie Video-elementen [beheren voor meer informatie](/help/assets/manage-video-assets.md#transcode-video). Gebruik [!DNL Dynamic Media] add-on voor meer transcoderingsopties en voor het afleveren van video.

* Voor nieuwe [!DNL Experience Manager Assets] plaatsingen, wordt de slimme etiketteringsfunctionaliteit nu gevormd door gebrek. U hoeft niet handmatig te integreren met [!DNL Adobe Developer Console]. Bij bestaande implementaties [configureren beheerders de integratie](/help/assets/smart-tags-configuration.md#aio-integration) van slimme tags zoals voorheen.

* Een nieuwe ervaring [bij het downloaden van](/help/assets/download-assets-from-aem.md) middelen is mogelijk.

   * Asynchrone download voor grote downloads zodat de gebruikers niet hoeven te wachten.
   * Een nieuwe modulaire API voor uitbreidbaarheid voor ontwikkelaars.

* De extractie van metagegevens voor assetmicroservices levert betere prestaties op. Het verhoogt de algemene productie van activa.

* Gebruik een verwerkingsprofiel om aangepaste metagegevens te genereren met gebruik van de Compute Service. Zie [Aangepaste metagegevens met verwerkingsprofiel](/help/assets/manage-metadata.md#metadata-compute-service).

* Een eenvoudigere downloadervaring voor gebruikers van het Brand Portal die beheerders kunnen configureren. Zie Overzicht [van](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html#download-configurations)downloadervaring.

* Voorvertoningen van PDF-documenten met een standaardkwaliteit en hoge kwaliteit zijn nu beschikbaar in Brand Portal. Zie Overzicht [van de](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html#doc-viewer)documentviewer.

* U kunt het CDN-cachegeheugen (Content Delivery Network) nu direct [!DNL Dynamic Media] in AEM invalideren als een Cloud Service (in tegenstelling tot [!DNL Dynamic Media Classic]). Hiermee zorgt u ervoor dat de nieuwste middelen binnen minuten worden gebruikt in plaats van binnen uren. Zie De CDN-cache [ongeldig maken met behulp van Dynamic Media](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md).

* Verbeterde toegankelijkheidsondersteuning wordt toegevoegd aan besturingselementen voor gebruikersinterfaces, navigatie, browse en zoekervaring in [!DNL Assets].

   * Als u na het selecteren van de [!UICONTROL Add Rendition] optie op de Esc-toets drukt, keert de focus terug naar de werkbalk. <!-- via CQ-4293594-->
   * De toetsenbordfocus werkt zoals u had verwacht bij het gebruik van het invoervak E-mail. <!-- via CQ-4286215 -->
   * De accordeonelementen in de sectie met zoekfilters worden geïnterpreteerd als standaard uitbreidbare accordeons. <!-- via CQ-4273103 -->
   * Wanneer u een tag toepast op een element, worden labels in het dialoogvenster weergegeven als boomelementen. ARIA-kenmerken worden op de juiste wijze toegepast op de boomelementen om ze nu toegankelijk te maken. <!-- via CQ-4272964 -->

* [!DNL AEM Desktop app] 2.0.3-release is nu beschikbaar. Het verbetert verenigbaarheid met [!DNL Experience Manager] 6.5.5 de dienstpak en heeft een bijgewerkte lijst van de verenigbaarheid van cliëntOS. [!DNL Windows] 7 en [!DNL macOS] versies lager dan 10.14 worden niet ondersteund.

### Buizen vastgesteld in [!DNL Assets] {#bugs-fixed}

* De optie Relate en unrelationship reageert niet wanneer voor het eerst geklikt. (CQ-4299022)
* Als u tijdens het downloaden van een element de optie selecteert om het via e-mail te ontvangen, wordt het e-mailbericht niet verzonden. (CQ-4299146)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### What&#39;s New {#what-is-new-commerce}

* De functie Productconsole is nu beschikbaar. Dit staat marketers/auteurs in AEM toe om categorieën en producten te bekijken en te navigeren die in de handelskern worden opgeslagen. Er wordt ook ondersteuning geboden voor eigenschappen voor categorieën en producten in de productconsole.

* Product- en rubriekkiezers zijn verbeterd zodat marketers hun product via SKU kunnen selecteren of een categorie kunnen selecteren via rubriek-id.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor [!UICONTROL Cloud Manager] versie 2020.8.0 is 6 augustus 2020.

### What&#39;s New {#what-is-new-cloud-manager}

* De Controle van de inhoud is een eigenschap die op de Pijpleidingen van de Productie van de Plaatsen van de Manager van de Wolk wordt toegelaten. De configuratie van de Pijpleiding van de Productie voor programma&#39;s met Plaatsen omvat nu een derde lusje genoemd **Inhoud Controle**. Wanneer een productiepijpleiding in werking wordt gesteld, zal een nieuwe stap van de Controle van de Inhoud in de pijpleiding na douane functionele tests worden omvat die de plaats tegen een aantal dimensies met inbegrip van prestaties, SEO (de Optimalisering van de Motor van het Onderzoek), toegankelijkheid, beste praktijken en PWA (Progressieve App van het Web) zullen evalueren.

   >[!NOTE]
   >De naam van Content Audit is sindsdien gewijzigd in Experience Audit.

   Raadpleeg [Experience Audit Testing](/help/implementing/cloud-manager/experience-audit-testing.md) voor meer informatie.

* Nieuw gemaakte omgevingen in middelenprogramma&#39;s worden nu automatisch geconfigureerd met Smart Content Services.

* Gesamberde omgevingen kunnen worden gedehiberneerd op de pagina **Overzicht** van Cloud Manager.

* Mogelijkheid om ervaringscontroles uit te voeren op pagina&#39;s, aangedreven door Google Lighthouse. Als onderdeel van de Cloud Manager-pijplijn kunnen maximaal 25 pagina&#39;s worden gecontroleerd en gevalideerd op basis van ervaringen met KPI&#39;s en scores worden weergegeven in de gebruikersinterface van Cloud Manager.

### Bug Fixes {#bug-fixes-cm}

* Enkele onnodige en ongewenste SonarQube-plug-ins werden uitgevoerd als onderdeel van het scannen van codekwaliteit.

* Op de pagina van de pijpleiding uitvoerde, was de taknaam onjuist geformatteerd.

* In sommige gevallen werden voltooide executies van pijpleidingen niet met succes geregistreerd als voltooid, waardoor nieuwe executies van de pijpleiding werden voorkomen.

* De executies van pijpleidingen zouden af en toe *vastzitten* als gevolg van interne communicatieproblemen.

* Bij de provisioning van een nieuwe organisatie kregen sommige gebruikers met andere beheerrollen dan systeembeheerders ten onrechte toegang tot Cloud Manager.

* Onder bepaalde voorwaarden werd de update-indexeertaak meerdere keren parallel gestart, wat leidde tot een implementatiefout.

* De knopinfo op de programmakaarten was niet consistent correct.

* De gebruikersinterface stond abusievelijk toe dat bewerkingen werden uitgevoerd in een omgeving terwijl deze werd verwijderd.

* Er is een kleurfout opgetreden op de pagina **Overzicht** van Cloud Manager.

### Bekende problemen {#known-issues-cm}

* Ongeldige pagina&#39;s worden opgenomen waardoor de gemiddelde score voor controle van inhoud lager wordt dan wat ze moeten zijn.

* Op het tabblad Inhoudscontrole wordt de basis-URL onjuist weergegeven met behulp van het auteurdomein in plaats van het publicatiedomein.

* Om de stap van de Controle van de Inhoud te activeren, moeten de gebruikers de pijpleiding uitgeven en, naar keuze, pagina&#39;s toevoegen. Als er geen pagina&#39;s worden toegevoegd, wordt de startpagina gecontroleerd.

## De tool Content Transfer {#content-transfer-tool}

Volg deze sectie om te leren over wat nieuw is en de updates voor Versie van het Hulpmiddel van de Overdracht van de Inhoud v1.0.4.

### What&#39;s New {#what-is-new-ctt}

* Content Transfer Tool biedt nu ondersteuning voor Shared S3 DataStore.

### Bug Fixes {#ctt-bug-fixes}

* Er zijn extra onderbrekingen toegevoegd voor het gereedschap om de handelingen te voltooien.

* De gebruikersinterface van eerdere versies toonde soms een geslaagde extractie, ook al toonde het logboek fouten.

## Tools voor herstructurering van code {#code-refactoring-tools}

Volg deze sectie om te leren over wat nieuw en de updates voor de Hulpmiddelen van het Refactoring van de Code is.

### What&#39;s New {#what-is-new-refactoring}

* De insteekmodule AIO-CLI wordt vrijgegeven om code refactoring hulpmiddelen te verenigen om ontwikkelaars toe te laten om code refactoring hulpmiddelen van één plaats aan te halen en uit te voeren. Zie [Git Resource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) voor meer informatie.

* AEM Dispatcher Converter uitgebreid om conversies van On-premise- en Adobe Managed Services Dispatcher-configuraties in AEM te ondersteunen als met Cloud Service compatibele Dispatcher-configuraties. Zie [Git Resource: AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) voor meer informatie.

* AEM Dispatcher Converter herschreven in ` node.js ` en geïntegreerd met de AIO-CLI-plug-in.
