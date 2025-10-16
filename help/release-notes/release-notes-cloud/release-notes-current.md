---
title: De huidige Nota's van de Versie voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Huidige versienota's voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 245ad07ba6abbf18e2011cb71a15948c9b92f80f
workflow-type: tm+mt
source-wordcount: '1981'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies, zoals 2023 of 2024, vrij te geven.
>
>Heb een blik bij [&#x200B; Experience Manager geeft Roadmap &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [&#x200B; Update van het Product van de Prioriteit Adobe &#x200B;](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2025.9.0) is 25 september 2025. De volgende release met functies (2025.10.0) is gepland voor 30 oktober 2025.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [&#x200B; hier &#x200B;](/help/release-notes/maintenance/latest.md) vinden.

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440926?captions=dut&quality=12)

-->

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in Experience Manager Sites Prerelease {#prerelease-sites}

De Content Model Editor voor AEM Content Fragments is gemoderniseerd en uitgelijnd met andere React Spectrum-gebaseerde interfaces in AEM. De implementatie- en uitbreidingsmodellen van de gebruikersinterface zijn nu consistent met de Content Fragment Editor en de Universal Editor. De nieuwe Modelbewerker is nu standaard wanneer deze wordt geopend vanuit de nieuwe beheerinterface voor inhoudsmodellen. Als u een inhoudsmodel opent in de Touch-gebruikersinterface, wordt de Touch UI-editor geopend en kunt u de nieuwe editor uitproberen.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in de Assets-weergave {#new-features-assets-view}

**Verbeterde Opmaak van de Tekst met Substrings in Dynamische Malplaatjes van Media**

U kunt nu opmaak toepassen op subtekenreeksen binnen tekstlagen van de sjabloon Dynamische media. Een geselecteerd woord of een geselecteerde woordgroep wordt beschouwd als een aparte laag, zodat u het lettertype, de tekengrootte, de kleur en meer kunt aanpassen. De subtekenreekslaag wordt geparametriseerd zodat u het in real time kunt bijwerken gebruikend de levering URL van het malplaatje

### Nieuwe functies in dynamische media met OpenAPI-mogelijkheden {#new-features-dynamic-media-with-openapi}

**Gemarkeerde en Leesbare Levering URLs van Activa**

Dynamische media met OpenAPI-URL&#39;s leesbaarder maken door Vanity-URL&#39;s te gebruiken in Dynamic Media met OpenAPI. Met URL&#39;s met Vanity kunnen lange, door het systeem gegenereerde, moeilijk te onthouden UUID&#39;s in URL&#39;s voor het leveren van elementen worden vervangen door korte, door het merk gecontroleerde id&#39;s. Hierdoor zijn Vanity-URL&#39;s korter, gemakkelijker te lezen en te delen en kunt u ze beter aanpassen aan uw merk of campagnes. URL&#39;s met Vanity worden tijdens runtime automatisch omgezet in de oorspronkelijke UUID van het element zonder bestaande workflows te onderbreken.

>[!NOTE]
>
>Deze functie is beschikbaar als functie voor beperkte beschikbaarheid. U kunt [&#x200B; tot stand brengen en een geval van de Steun van de Klant van Adobe voorleggen &#x200B;](https://helpx.adobe.com/nl/enterprise/using/support-for-experience-cloud.html) om het voor uw plaatsing toe te laten.

<!--

### New Features in Content Hub {#new-features-content-hub}

**Mark Collections as Favourites**

You can now mark collections as Favorites in Content Hub, making it easier to organize and retrieve them. Once added, your favourite collections are conveniently available from the **Favourites** tab on the Content Hub home page.

**Pin collections for quick access**

Content Hub Administrators can now pin collections in Content Hub for quick access. Pinned collections are displayed in a dedicated **Pinned** section on the Collections home page, making it easier to keep important collections within reach.

>[!NOTE]
>
>These features are available as Limited Availability features. You can [create and submit an Adobe Customer Support case](https://helpx.adobe.com/nl/enterprise/using/support-for-experience-cloud.html) to enable it for your deployment.

-->

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in Experience Manager Forms {#new-features-forms}

**aanhaalt de Stap van het ModelWerkschema van de Gegevens van de Vorm voor de Bijlagen van de Lijst van SharePoint**

De workflowstap Formuliergegevensmodel aanroepen ondersteunt nu de verwerking van metagegevens aan de werkschemazijde voor Base64-gecodeerde bijlagearrays in SharePoint List-based Form Data Models. Met deze verbetering, kan de werkschemastap meta-gegevens zoals dossier - naam, type MIME, en douaneeigenschappen voor elke gehechtheid overgaan, opslaan en terugwinnen. Deze mogelijkheid maakt een uitgebreider gegevensbeheer mogelijk en vergemakkelijkt naadloze integratie in de downstreamfase. Voor details, zie [&#x200B; Verbeterde steun in de Invoke stap van het werkschemamodel van de Gegevens van de Vorm voor de gehechtheid van de Lijst van SharePoint &#x200B;](/help/forms/aem-forms-workflow-step-reference.md#invoke-form-data-model-fdm-service-step).

### Functies vóór de release in AEM Forms

**Verbeteringen van de Redacteur van de Regel**

De Redacteur van de Regel steunt nu verbeterde navigatie en staat gebruik van functie en wiskundige uitdrukkingen in inputparameters toe.

**Verbeterde Navigatie met de Steun van de Payload van de Gebeurtenis**

De handeling `Navigate To` in de handlers van de Invoke-service ondersteunt nu `EVENT_PAYLOAD` , waarmee formulierauteurs follow-upacties kunnen configureren op basis van gebeurtenisreacties. Deze verbetering biedt meer flexibiliteit bij het ontwerpen van workflows na verzending, waardoor vloeiendere overgangen en meer persoonlijke gebruikerservaring worden gegarandeerd. Voor meer informatie, zie [&#x200B; Verbeterde Navigatie met de Steun van de Payload van de Gebeurtenis &#x200B;](/help/forms/invoke-service-enhancements-rule-editor.md#use-case-5-use-event-payload-in-navigate-to-action-in-invoke-service).

**Functie en Wiskundige Steun van de Uitdrukking in de Parameters van de Input**

Invoerparameters ondersteunen nu zowel functieaanroepen als wiskundige expressies, waardoor formulierauteurs dynamisch berekende waarden rechtstreeks kunnen doorgeven. Deze verbetering stroomlijnt regelconfiguraties, elimineert de behoefte aan extra gebieden, en maakt vormen meer aanpasbaar aan complexe logica en berekening-gedreven scenario&#39;s. Voor meer informatie, zie [&#x200B; Functie en de Wiskundige Steun van de Uitdrukking in de Parameters van de Input &#x200B;](/help/forms/rule-editor-core-components-user-interface.md#function-and-mathematical-expression-support-in-input-parameters).

### Nieuwe functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms-programma voor vroege toegang biedt u een unieke kans om exclusieve toegang te krijgen tot geavanceerde innovaties en om de ontwikkeling ervan te helpen vormgeven.

In deze releaseopmerkingen worden de innovaties vermeld die in de huidige release zijn geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie &lbrace;de documentatie van het Programma van de Vroege Toegang van AEM Forms [.](/help/forms/early-access-ea-features.md)

**Voorproef PDF in Interactieve Communicatie Redacteur**

Gebruikers kunnen een voorvertoning weergeven van interactieve communicatie-PDF&#39;s zonder gegevens, met lokale JSON-gegevensbestanden of met gegevens van een gegevensmodel, zodat u flexibele gegevensgestuurde tests kunt uitvoeren. Voor meer informatie, zie [&#x200B; Voorproef van PDF in Interactieve Communicatie Redacteur &#x200B;](/help/forms/interactive-communication/pdf-preview-in-interactive-communication-editor-with-different-data-options.md).

**Steun van de Doopvonten van de Douane in Interactieve Mededeling**

Met de functie Aangepaste lettertypen kunnen gebruikers aangepaste of door de organisatie goedgekeurde lettertypen insluiten in de interactieve communicatie, zodat een consistente en branded PDF-rendering op alle apparaten en platforms wordt gegarandeerd. Voor meer informatie, zie [&#x200B; Steun van de Doopvonten van de Douane in Interactieve Mededeling &#x200B;](/help/forms/interactive-communication/add-custom-fonts-to-interactive-communication-editor.md).

**de Invoer en de Uitvoer Interactieve Mededelingen**

Deze eigenschap laat migratie en hergebruik van Interactieve Mededelingen over verschillende milieu&#39;s toe. U kunt nu een interactieve communicatie samen met de bijbehorende fragmenten en gegevensmodellen vanuit de ene omgeving exporteren en in een andere omgeving importeren. Voor meer informatie, zie [&#x200B; Interactieve Mededelingen van de Invoer en van de Uitvoer &#x200B;](/help/forms/interactive-communication/import-and-export-interactive-communications.md).

<!--
**Forms Optimization opportunities**

Forms Optimization uses AI to analyze your forms and suggest improvements for better performance. It highlights forms with low engagement, flags accessibility issues, and generates AI-powered variations to help increase conversion rates and compliance with WCAG standards.

>[!VIDEO](https://video.tv.adobe.com/v/3469472/) 

Key optimization opportunities include:

* Increasing visibility for forms with low views
* Improving completion rates for forms with low conversions
* Addressing accessibility compliance issues
* Streamlining navigation to enhance user experience

With Forms Optimization, you get automated, data-driven recommendations and variations, making it easier to boost engagement and ensure your forms are effective and inclusive. 
-->

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Nieuwe functies in releasebeheer {#new-features-release-management}

**de Automatische Updates van het Onderhoud van de onderbreking**

Go-live dagen, live gebeurtenissen, piekverkoop-deze momenten kunnen niet breken. [&#x200B; onze nieuwe zelfbediening eigenschappen &#x200B;](/help/implementing/deploying/quiet-hours-update-free-periods.md) stoppen automatische onderhoudsupdates wanneer het van belang is, zodat blijven uw teams geconcentreerd.

* Quiet Hours: Blokkeer automatisch onderhoud tijdens ingestelde tijden elke dag. Ideaal voor arbeidsuren, nachtelijke ritten of ochtendcutovers.
* Periode zonder update: automatisch onderhoud gedurende een volledige week blokkeren. Gebruik deze optie voor lanceringen, promoties of jaarlijkse vastlopen.

>[!NOTE]
>
>Beschikbaar als Beperkte Beschikbaarheid eigenschap op 25 september.
>&#x200B;>E-mail [&#x200B; aemcs-update-free@adobe.com &#x200B;](mailto:aemcs-update-free@adobe.com) om het op uw programma&#39;s te krijgen geactiveerd.

### Nieuwe release van AEM Developer Tools voor Eclipse {#aem-develeper-tools-for-eclipse}

Versie 1.4.0 van de AEM Developer Tools for Eclipse is uitgebracht. Deze versie voegt ondersteuning toe voor Eclipse IDE 2022-12 of hoger en is gevalideerd met de huidige versie (2025-09). Het gereedschap werkt nu met moderne versies van het AEM Project Archetype en bevat verbeteringen van de Sling IDE Tooling 1.3.0.

Installeer van de [&#x200B; Marketplace van de Verduistering &#x200B;](https://marketplace.eclipse.org/content/aem-developer-tools-eclipse) en zie de [&#x200B; pagina van de Hulpmiddelen van de Ontwikkelaar van AEM &#x200B;](https://eclipse.adobe.com) voor meer details.

### Opkomende Java API-implementaties {#java-api-deprecation}

Verschillende vervangen API&#39;s zijn gemarkeerd voor verwijdering op 31 augustus en moeten daarom niet langer worden vermeld. U ontvangt meldingen van het Actions Center als verouderd API-gebruik in uw code wordt gedetecteerd. Na 13 november worden tijdens Cloud Manager builds berichten weergegeven om het belang van het verwijderen van het gebruik te benadrukken. Zie het [&#x200B; afgekeuringsartikel &#x200B;](/help/release-notes/deprecated-removed-features.md#aem-apis) voor volledige details, maar voor gemak, zijn deze APIs hieronder vermeld:

+++ Uitvouwen om de afgekeurde Java API&#39;s weer te geven

* `org.apache.sling.commons.auth`
* `org.apache.felix.webconsole`
* `org.eclipse.jetty`
* `com.mongodb`
* `org.apache.abdera`
* `org.apache.felix.http.whiteboard`
* `org.apache.cocoon.xml`
* `ch.qos.logback`
* `org.slf4j.spi`
* `org.slf4j.event`
* `org.apache.log4j`
* `com.google.common`
* `com.drew`
* `org.bson`
* `org.apache.jackrabbit.oak.plugins.blob`
* `org.apache.jackrabbit.oak.plugins.memory`

+++

<!--
OSGi properties:

* `org.apache.sling.commons.log.LogManager` (all properties)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)
* 

-->

### Java 11 Runtime Deprecation {#java11-runtime-deprecation}

*Java 11 runtime* wordt afgekeurd, en de meeste milieu&#39;s zijn reeds bevorderd aan hoog-prestaties **Java 21 runtime**.

Als uw milieu niet wegens niet gesteunde gebiedsdelen (zie [&#x200B; Java 21 runtime vereisten &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)) kon worden bevorderd, zou u een e-mail van Adobe met volgende stappen moeten ontvangen. Zoals daar beschreven, verbeterde Adobe uw **Dev** en **RDE** milieu&#39;s op **September 18, 2025** zodat kunt u uw plaats en processen bevestigen en om het even welke kwesties richten. De verbeteringen voor **Stadium** en **Productie** zullen op **14 oktober, 2025** te werk gaan.

>[!NOTE]
>
>De runtimeversie staat los van de build-versie van uw code. We raden u aan om samen te werken met Java 21, maar Java 11-builds zijn nog steeds geaccepteerd. In de toekomst wordt een afzonderlijke aankondiging voor het vervangen van Java 11-builds gedeeld.

### Handhaving van het configuratiebeleid van AEM Java Logs {#logconfig-policy}

Zoals vermeld in de opmerkingen bij de release van april, moeten AEM Java-logboeken een standaardindeling gebruiken voor betrouwbare bewaking in alle klantomgevingen. Aangepaste logboekconfiguraties, zoals wijzigingen in de logbestandsindeling, uitvoerbestanden of standaardlogniveaus, worden niet meer ondersteund. De logbestanden moeten naar de standaardbestanden worden geleid en de standaardlogniveaus voor AEM-productcode moeten worden behouden. Zie volledige details in het [&#x200B; Registreren artikel &#x200B;](/help/implementing/developing/introduction/logging.md#configuration-loggers).

Beginnend op **30th van Oktober**, zullen om het even welke niet gestaafde overrides van het douaneregistreren worden genegeerd. Op basis van onze analyse zullen de meeste klanten niet worden beïnvloed en heeft Adobe contact opgenomen met klanten van wie de huidige configuratie mogelijk wordt beïnvloed.

Gelieve te herzien en bij te werken om het even welke stroomafwaartse processen die zich op het gedrag van het douaneregistreren baseren. Bijvoorbeeld:

* Als uw logboek het door:sturen systeem een formaat van het douanelogboek verwacht, kunt u uw innameregels moeten aanpassen.
* Als u eerder logboekbreedheid hebt verminderd door logboekniveaus te veranderen, gelieve te merken dat het terugkeren aan standaardniveaus logboekvolume kan verhogen.

### Edge Computing (Beta-programma) {#edge-computing}

Met Edge Computing kunt u JavaScript uitvoeren op de CDN-laag, waardoor de gegevensverwerking dichter bij de eindgebruiker komt te staan. Dit vermindert latentie en maakt responsieve, dynamische ervaringen aan de rand mogelijk.

Vaak voorkomende gevallen van gebruik zijn:

* Inhoud aanpassen op basis van geolocatie, apparaattype of gebruikerskenmerken
* Handelend als middleware tussen CDN en uw oorsprong
* Reacties van externe API&#39;s opnieuw opmaken (en wellicht meerdere API-reacties samenvoegen) voordat deze naar de browser worden verzonden
* Door de server gerenderde HTML aan de rand samenstellen en bedienen met inhoud die vanuit verschillende achtergronden is geplaatst
* Het blootstellen van een server MCP voor LLMs zoals ChatGPT en Claude om tot douanegereedschappen toegang te hebben

We hebben een beperkt aantal mogelijkheden voor AEM Publish Delivery- of Edge Delivery Services-projecten voor live productiesites. Als u in het deelnemen geinteresseerd bent of meer wilt leren, gelieve [&#x200B; aemcs-edgecompute-feedback@adobe.com &#x200B;](mailto:aemcs-edgecompute-feedback@adobe.com) met een korte beschrijving van uw gebruiksgeval te e-mailen.

### Edge-verificatie voor Edge Delivery Services (Beta-programma) {#edge-authentication}

Met Edge-verificatie kunt u de toegang tot Edge Delivery Services-pagina&#39;s beperken tot gebruikers die zijn geverifieerd bij uw identiteitsprovider (IdP). Dit wordt bereikt door het implementeren van een YAML-bestand met OpenID Connect-configuratie (OIDC).

Als geinteresseerd, gelieve [&#x200B; aemcs-edgecompute-feedback@adobe.com &#x200B;](mailto:aemcs-edgecompute-feedback@adobe.com) met een korte beschrijving van uw gebruiksgeval en om het even welke vragen te e-mailen u kunt hebben.

<!--
### CDN Configuration for Edge Delivery Services (Beta Program) {#cdn-eds-beta}

The Adobe-Managed CDN offers flexible configuration options, as described in the [Config Pipeline article](/help/operations/config-pipeline.md#configurations). 

Now in beta, youcan deploy a config pipeline for features including CDN origin selectors, response and request transformations, CDN log forwarding and more. Please reach out to [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com) with the details of your use case.

-->

### Kanarische productie-inzetposten naar testcode vóór toelating van het verkeer (Beta-programma) {#canary-beta}

Valideer een productie bouwt met intern-slechts testverkeer alvorens het aan eind - gebruikers bloot te stellen. Schip aan productie, route slechts kanarieverkeer (gebruikend een speciale kopbal), monitorgedrag, dan of bevordert aan levend verkeer of rol terug-zonder klanten te beïnvloeden.

Stel uw code versies aan productie op, maar beperkt het tot slechts intern testverkeer alvorens te beslissen of om levend verkeer tegenover het rollen terug te nemen.

E-mail [&#x200B; aemcs-canary-deployments-beta@adobe.com &#x200B;](mailto:aemcs-canary-deployments-beta@adobe.com) om toegang te verzoeken en terugkoppelen te delen.

### Momentopnamen voor RDE&#39;s (Alpha-programma) {#rde-snapshot-program}

In alfa, steunen de Snelle Milieu&#39;s van de Ontwikkeling (RDEs) nu een eigenschap om een momentopname van de huidige staat van code en inhoud te nemen, die op een recentere tijd kan worden hersteld. Dit kan nuttig zijn wanneer het synchroniseren van code die kan moeten worden teruggekeerd, of wanneer het schakelen tussen ontwikkeling van verschillende eigenschappen. Het is ook mogelijk om alleen de veranderbare inhoud te herstellen als een bekend beginpunt voor het testen.

Gelieve te e-mail [&#x200B; aemcs-rde-support@adobe.com &#x200B;](mailto:aemcs-rde-support@adobe.com) als er belang in het verstrekken van terugkoppelt op deze eigenschap is.

### AEM Log-Forwarding aan Meer Doelen (het Programma van Beta) {#log-forwarding-beta}

Hoewel de logboeken van Cloud Manager kunnen worden gedownload, vinden vele organisaties het nuttig om die logboeken aan een aangewezen registrerenbestemming te stromen. AEM biedt al ondersteuning voor het doorsturen van AEM- en CDN-logbestanden naar Azure Blob Storage, Datadog, HTTPS, Elasticsearch (en OpenSearch) en Splunk. Deze eigenschap wordt gevormd op een zelf-servermanier, en opgesteld gebruikend de Pijpleiding Config.

Nu in bèta kunt u AEM-logs doorsturen naar Amazon S3, Sumo Logic, Dynatrace en uw eigen New Relic-account (niet naar het door Adobe verschafte account). Merk op dat de logboeken van AEM (met inbegrip van Apache/Dispatcher) voor deze registrerenbestemmingen, maar niet CDN- logboeken worden gesteund. E-mail [&#x200B; aemcs-logforwarding-beta@adobe.com &#x200B;](mailto:aemcs-logforwarding-beta@adobe.com) voor toegang.

Leer meer in het [&#x200B; logboek door:sturen documentatie &#x200B;](/help/implementing/developing/introduction/log-forwarding.md).

### Uitgebreide Application Performance Monitoring (APM) (Alpha-programma) {#apm-alpha}

Voor waarneming, steunt de Dienst van de Wolk AEM momenteel Adobe-Geleverde [&#x200B; New Relic One &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic) en klant-geleide [&#x200B; Dynatrace &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/dynatrace). Aangezien wij steun voor extra opties van APM onderzoeken, gelieve ons in [&#x200B; aemcs-apm-beta@adobe.com &#x200B;](mailto:aemcs-apm-beta@adobe.com) met uw aangewezen verkoper of technologie, samen met gebruiksgevallen te e-mailen.


## [!DNL Experience Manager] Hulplijnen {#guides}

U kunt een volledige lijst van nieuwe en verbeterde eigenschappen van de recentste versie van Adobe Experience Manager Guides [&#x200B; hier &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [&#x200B; hier &#x200B;](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [&#x200B; hier &#x200B;](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.

## Universele editor {#universal-editor}

U kunt een volledige lijst van Universele versies van de Redacteur [&#x200B; hier &#x200B;](/help/release-notes/universal-editor/current.md) vinden.

## Variaties genereren {#generate-variations}

U kunt een volledige lijst van Generate de versies van Variaties [&#x200B; hier &#x200B;](/help/generative-ai/release-notes-generate-variations.md) vinden.

## Opmerkingen bij de release van Experience Cloud {#experience-cloud}

U kunt informatie over versies van andere toepassingen van Experience Cloud [&#x200B; hier &#x200B;](https://experienceleague.adobe.com/nl/docs/release-notes/experience-cloud/current) vinden.
