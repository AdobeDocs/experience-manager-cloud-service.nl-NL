---
title: Nota's van de versie voor 2020.8.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release voor 2020.8.0."
exl-id: 83413130-ae90-4419-bcf7-42fdc740452b
feature: Release Information
role: Admin
source-git-commit: cfaa3be31195929b80310610120a779a20537c61
workflow-type: tm+mt
source-wordcount: '1025'
ht-degree: 0%

---

# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] as a Cloud Service 2020.8.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor Experience Manager as a Cloud Service 2020.8.0 beschreven.


## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Nieuwe functies in [!DNL Sites] {#what-is-new-sites}

* Mogelijkheid om [ pagina&#39;s en subpagina&#39;s (paginabomen) aan een vroegere versie ](/help/sites-cloud/authoring/sites-console/page-versions.md#reinstating-versions) te herstellen.

* Mogelijkheid om [ Lanceringen ](/help/sites-cloud/authoring/launches/overview.md) in AEM [ SPA Redacteur ](/help/implementing/developing/hybrid/introduction.md) tot stand te brengen.


## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Nieuwe functies in [!DNL Assets] {#what-is-new-assets}

* Videotranscodering wordt nu ondersteund met middelenmicroservices. In een nieuwe sectie in de [!UICONTROL Processing Profiles] -configuratie kunt u de bitsnelheid en afmetingen voor de video instellen. De uitvoerindeling is MP4 met H.264-codec. Voor details, zie [ videoactiva ](/help/assets/manage-video-assets.md#transcode-video) beheren. Gebruik [!DNL Dynamic Media] add-on voor meer transcoderingsopties en voor het afleveren van video.

* Bij nieuwe [!DNL Experience Manager Assets] implementaties is de functionaliteit voor slimme tags nu standaard geconfigureerd. U hoeft niet handmatig te integreren met [!DNL Adobe Developer Console] . Bij bestaande implementaties configureren beheerders de integratie van slimme tags zoals voorheen.

* Een nieuwe [ ervaring van de activadownload ](/help/assets/download-assets-from-aem.md) staat toe,

   * Asynchrone download voor grote downloads zodat de gebruikers niet hoeven te wachten.
   * Een nieuwe modulaire API voor uitbreidbaarheid voor ontwikkelaars.

* De extractie van metagegevens voor assetmicroservices levert betere prestaties op. Het verhoogt de algemene productie van activa.

* Gebruik een verwerkingsprofiel om aangepaste metagegevens te genereren met gebruik van de Compute Service. Zie [ meta-gegevens van de Douane gebruikend verwerkingsprofiel ](/help/assets/manage-metadata.md#metadata-compute-service).

* Een eenvoudigere downloadervaring voor Brand Portal-gebruikers die beheerders kunnen configureren. Zie [ overzicht van de downloadervaring ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html#download-configurations).

* PDF-documentvoorvertoningen met een native en hoge getrouwheid zijn nu beschikbaar in Brand Portal. Zie [ overzicht van de documentkijker ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html#doc-viewer).

* U kunt de CDN-cache (Content Delivery Network) nu rechtstreeks vanuit [!DNL Dynamic Media] in AEM as a Cloud Service ongeldig maken (in tegenstelling tot het gebruik van [!DNL Dynamic Media Classic] ). Hiermee zorgt u ervoor dat de nieuwste middelen binnen minuten worden gebruikt in plaats van binnen uren. Zie [ het Invalideren van het CDN geheime voorgeheugen als Dynamic Media ](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md).

* Verbeterde toegankelijkheidsondersteuning wordt toegevoegd aan besturingselementen voor gebruikersinterfaces, navigatie, bladeren en zoekervaring in [!DNL Assets] .

   * Als u na het selecteren van de optie [!UICONTROL Add Rendition] op de Esc-toets drukt, keert de focus terug naar de werkbalk. <!-- via CQ-4293594-->
   * De toetsenbordfocus werkt zoals u had verwacht bij het gebruik van het invoervak E-mail. <!-- via CQ-4286215 -->
   * De accordeonelementen in de sectie met zoekfilters worden geïnterpreteerd als standaard uitbreidbare accordeons. <!-- via CQ-4273103 -->
   * Wanneer u een tag toepast op een element, worden labels in het dialoogvenster weergegeven als boomelementen. ARIA-kenmerken worden op de juiste wijze toegepast op de boomelementen om ze nu toegankelijk te maken. <!-- via CQ-4272964 -->

* [!DNL AEM Desktop app] 2.0.3-release is nu beschikbaar. Het verbetert de compatibiliteit met het servicepack [!DNL Experience Manager] 6.5.5 en heeft een bijgewerkte lijst met OS-compatibiliteit voor clients. [!DNL Windows] 7- en [!DNL macOS] -versies ouder dan 10.14 worden niet ondersteund.

### Buizen gecorrigeerd in [!DNL Assets] {#bugs-fixed}

* De optie Relate en unrelationship reageert niet wanneer voor het eerst geklikt. (CQ-4299022)
* Als u tijdens het downloaden van een element de optie selecteert om het via e-mail te ontvangen, wordt het e-mailbericht niet verzonden. (CQ-4299146)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Wat is er nieuw? {#what-is-new-commerce}

* De functie Productconsole is nu beschikbaar. Dit staat marketers/auteurs in AEM toe om categorieën en producten te bekijken en te navigeren die in de handelskern worden opgeslagen. Er wordt ook ondersteuning geboden voor eigenschappen voor categorieën en producten in de productconsole.

* Product- en rubriekkiezers zijn verbeterd zodat marketers hun product via SKU kunnen selecteren of een categorie kunnen selecteren via rubriek-id.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor [!UICONTROL Cloud Manager] versie 2020.8.0 is 6 augustus 2020.

### Wat is er nieuw? {#what-is-new-cloud-manager}

* De Controle van de inhoud is een eigenschap die op de Pijpleidingen van de Productie van de Plaatsen van Cloud Manager wordt toegelaten. De configuratie van de Pijpleiding van de Productie voor programma&#39;s met Plaatsen omvat nu een derde lusje genoemd **Controle van de Inhoud**. Wanneer een productiepijplijn in werking wordt gesteld, is een nieuwe stap van de Controle van de Inhoud inbegrepen in de pijpleiding na douane functioneel testen die de plaats tegen verscheidene dimensies met inbegrip van prestaties, SEO (de Optimalisering van de Motor van het Onderzoek), toegankelijkheid, beste praktijken en PWA (Progressieve App van het Web) evalueert.


  >[!NOTE]
  >De naam van Content Audit is sindsdien gewijzigd in Experience Audit.

  Zie [ het Testen van de Controle van de Ervaring ](/help/implementing/cloud-manager/experience-audit-dashboard.md) voor meer details.

* Nieuwe omgevingen in Assets-programma&#39;s worden nu automatisch geconfigureerd met Smart Content Services.

* De gebedde milieu&#39;s kunnen van de Cloud Manager **pagina van het Overzicht** worden ontbonden.

* Mogelijkheid om ervaringscontroles uit te voeren op pagina&#39;s, aangedreven door Google Lighthouse. Als onderdeel van de Cloud Manager-pijplijn kunnen maximaal 25 pagina&#39;s worden gecontroleerd en gevalideerd op basis van de ervaring met KPI&#39;s en scores worden weergegeven in de gebruikersinterface van Cloud Manager.

### Opgeloste problemen {#bug-fixes-cm}

* Enkele onnodige en ongewenste SonarQube-plug-ins werden uitgevoerd als onderdeel van het scannen van codekwaliteit.

* Op de pagina van de pijpleiding uitvoerde, was de taknaam onjuist geformatteerd.

* In sommige gevallen werden voltooide executies van pijpleidingen niet met succes geregistreerd als voltooid, waardoor nieuwe executies van de pijpleiding werden voorkomen.

* De uitvoeringen van de pijpleiding zouden soms *geplakt* toe te schrijven aan interne communicatie kwesties krijgen.

* Bij levering van een nieuwe organisatie, werden sommige gebruikers met administratieve rollen buiten systeembeheerders foutief toegang tot Cloud Manager verleend.

* Onder bepaalde voorwaarden werd de update-indexeertaak meerdere keren parallel gestart, wat leidde tot een implementatiefout.

* De knopinfo op de programmakaarten was niet consistent correct.

* De gebruikersinterface stond abusievelijk toe dat bewerkingen werden uitgevoerd in een omgeving terwijl deze werd verwijderd.

* Er was een kleurenwanverhouding op de Cloud Manager **pagina van het Overzicht**.

### Bekende problemen {#known-issues-cm}

* Ongeldige pagina&#39;s worden opgenomen waardoor de gemiddelde score voor controle van inhoud lager wordt dan wat ze moeten zijn.

* Op het tabblad Inhoudscontrole wordt de basis-URL onjuist weergegeven met behulp van het auteurdomein in plaats van het publicatiedomein.

* Om de stap van de Controle van de Inhoud te activeren, moeten de gebruikers de pijpleiding uitgeven en, naar keuze, pagina&#39;s toevoegen. Als er geen pagina&#39;s worden toegevoegd, wordt de startpagina gecontroleerd.

## Inhoud overbrengen {#content-transfer-tool}

Volg deze sectie om te leren over wat nieuw is en de updates voor Versie van het Hulpmiddel van de Overdracht van de Inhoud v1.0.4.

### Wat is er nieuw? {#what-is-new-ctt}

* Content Transfer Tool biedt nu ondersteuning voor Shared S3 DataStore.

### Opgeloste problemen {#ctt-bug-fixes}

* Er zijn extra onderbrekingen toegevoegd voor het gereedschap om de handelingen te voltooien.

* De gebruikersinterface van eerdere versies toonde soms een geslaagde extractie, ook al toonde het logboek fouten.

## Gereedschappen voor het verfijnen van code {#code-refactoring-tools}

Volg deze sectie om te leren over wat nieuw en de updates voor de Hulpmiddelen van het Refactoring van de Code is.

### Wat is er nieuw? {#what-is-new-refactoring}

* De insteekmodule AIO-CLI wordt vrijgegeven om code refactoring hulpmiddelen te verenigen om ontwikkelaars toe te laten om code refactoring hulpmiddelen van één plaats aan te halen en uit te voeren. Zie [ Middel van de Git: ao-cli-stop-aem-wolk-dienst-migratie ](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) voor meer details.

* AEM Dispatcher Converter uitgebreid om conversies van Managed Services Dispatcher-configuraties op locatie en in Adobe naar Dispatcher-compatibele configuraties te ondersteunen. Zie [ Middel van de Git: Convertor van AEM Cloud Service Dispatcher ](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) voor meer details.

* AEM Dispatcher Converter herschreven in ` node.js ` en geïntegreerd met de AIO-CLI-plug-in.
