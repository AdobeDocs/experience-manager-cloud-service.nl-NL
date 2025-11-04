---
title: De huidige Nota's van de Versie voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Huidige versienota's voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 247a501660475d2f3ae9cff735a1845094d02c82
workflow-type: tm+mt
source-wordcount: '1628'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies, zoals 2023 of 2024, vrij te geven.
>
>Heb een blik bij [&#x200B; Experience Manager geeft Roadmap &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [&#x200B; Update van het Product van de Prioriteit Adobe &#x200B;](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2025.10.0) is 30 oktober 2025. De volgende functieversie (2025.11.0) is gepland voor 20 november 2025.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [&#x200B; hier &#x200B;](/help/release-notes/maintenance/latest.md) vinden.

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in Experience Manager Sites {#new-sites}

* De [&#x200B; Redacteur van het ModelInhoud voor de Fragmenten van de Inhoud van AEM &#x200B;](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) is gemoderniseerd om zich met andere React op spectrum-Gebaseerde interfaces in AEM te richten. De implementatie- en uitbreidingsmodellen van de gebruikersinterface zijn nu consistent met de Content Fragment Editor en de Universal Editor. De nieuwe Modelbewerker is nu standaard wanneer deze wordt geopend vanuit de nieuwe beheerinterface voor inhoudsmodellen. Als u een inhoudsmodel opent in de Touch-gebruikersinterface, wordt de Touch UI-editor geopend en kunt u de nieuwe editor uitproberen.

* [&#x200B; Lanceringen voor de Fragmenten van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/launches-for-content-fragments.md): Het lusje van Lancties van de console van de Fragmenten van de Inhoud staat u toe om lanceringen tot stand te brengen, van alle bestaande lanceringen een lijst te maken, zeer belangrijke eigenschappen te zien, en acties op hen te voeren.

<!--

### New Features in Content Hub {#new-features-content-hub}

**Mark Collections as Favourites**

You can now mark collections as Favorites in Content Hub, making it easier to organize and retrieve them. Once added, your favourite collections are conveniently available from the **Favourites** tab on the Content Hub home page.

**Pin collections for quick access**

Content Hub Administrators can now pin collections in Content Hub for quick access. Pinned collections are displayed in a dedicated **Pinned** section on the Collections home page, making it easier to keep important collections within reach.

>[!NOTE]
>
>These features are available as Limited Availability features. You can [create and submit an Adobe Customer Support case](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) to enable it for your deployment.

-->

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in Experience Manager Forms {#new-features-forms}

**Universele Redacteur voor AanpassingsForms en de Fragmenten van de Vorm**

De Universal Editor biedt nu een uniforme ontwerpervaring voor het maken van adaptieve Forms en herbruikbare formulierfragmenten. Auteurs kunnen visueel formulieren ontwerpen, verzendhandelingen configureren en reCAPTCHA-validatie integreren in een intuïtieve WYSIWYG-omgeving.

<!-- ### Pre-Release features in AEM Forms 

**Rule Editor Enhancements**

The Rule Editor now supports enhanced navigation and allows use of function and mathematical expressions in input parameters.

**Enhanced Navigation with Event Payload Support**
 
The `Navigate To` action in the Invoke Service handlers now supports `EVENT_PAYLOAD`, enabling form authors to configure follow-up actions based on event responses. This enhancement offers greater flexibility in designing post-submission workflows, ensuring smoother transitions and more personalized user experiences. For more information, see [Enhanced Navigation with Event Payload Support](/help/forms/invoke-service-enhancements-rule-editor.md#use-case-5-use-event-payload-in-navigate-to-action-in-invoke-service).

**Function and Mathematical Expression Support in Input Parameters**
 
Input parameters now support both function calls and mathematical expressions, enabling form authors to pass dynamically computed values directly. This enhancement streamlines rule configurations, eliminates the need for extra fields, and makes forms more adaptable to complex logic and calculation-driven scenarios. For more information, see [Function and Mathematical Expression Support in Input Parameters](/help/forms/rule-editor-core-components-user-interface.md#function-and-mathematical-expression-support-in-input-parameters). -->

### Nieuwe functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms-programma voor vroege toegang biedt u een unieke kans om exclusieve toegang te krijgen tot geavanceerde innovaties en om de ontwikkeling ervan te helpen vormgeven.

In deze releaseopmerkingen worden de innovaties vermeld die in de huidige release zijn geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie &lbrace;de documentatie van het Programma van de Vroege Toegang van AEM Forms [.](/help/forms/early-access-ea-features.md)

#### Verbeteringen voor interactieve communicatie

##### Sjabloon vergrendelen

Inhoud en lay-outelementen binnen sjablonen vergrendelen om de brandintegriteit te behouden en ongeoorloofde wijzigingen te voorkomen. Dit verzekert ontwerpconsistentie over alle mededelingen.

##### Ondersteuning voor overloop van inhoud

Introductie van de optie Pagina-einden binnen inhoud toestaan voor stroombare indelingen. Deze verbetering maakt probleemloze bewerkingen met meerdere pagina&#39;s en een beter tekstbeheer voor complexe documenten mogelijk.

##### XDP Bestandsbewerking

De Interactieve Communicatie redacteur steunt nu het uitgeven XDP, met inbegrip van fragmentintegratie. U kunt nu XDP-bestanden bewerken in een browser in plaats van Forms Designer die alleen op het bureaublad van Microsoft Windows wordt uitgevoerd.

##### Dynamische paginanummering

Geef automatisch &quot;Pagina nr. van ##&quot; weer op basispagina&#39;s voor duidelijke, consistente paginering in documenten met meerdere pagina&#39;s.

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
>E-mail [&#x200B; aemcs-update-free@adobe.com &#x200B;](mailto:aemcs-update-free@adobe.com) om het op uw programma&#39;s te krijgen geactiveerd.

### AEM Log-Forwarding naar Meer Doelen {#log-forwarding}

Het is nu mogelijk om AEM-logbestanden door te sturen naar Amazon S3, Sumo Logic, Dynatrace en uw eigen New Relic-account (niet naar het door Adobe verschafte account). Merk op dat de logboeken van AEM (met inbegrip van Apache/Dispatcher) voor deze registrerenbestemmingen, maar niet CDN- logboeken worden gesteund.

Zie de volledige reeks van [&#x200B; gesteund logboek door:sturen bestemmingen &#x200B;](/help/implementing/developing/introduction/log-forwarding.md).

### Config Pipeline voor Edge Delivery Services {#config-pipeline-eds}

Config Pipelines worden nu ondersteund voor sites die met Edge Delivery Services zijn gemaakt en breiden deze mogelijkheid uit tot meer dan alleen AEM Author en AEM publicatiebezorging. U kunt Pijpleidingen Config gebruiken om montages zoals configuratie te beheren CDN, met inbegrip van de regels van de verkeersfilter en oorsprongselecteurs. Zie [&#x200B; Ondersteunde Configuraties &#x200B;](/help/operations/config-pipeline.md#configurations).

Edge Delivery config pijpleidingen steunen ook geheimen door de pijpleidingsvariabelen van Cloud Manager.

Zie [&#x200B; toevoegen de Pijpleiding van Edge Delivery &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md).

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

Adobe bevorderde **het Stadium** en **de milieu&#39;s van de Productie** aan hoog-prestaties **Java 21 runtime** op 14 oktober, 2025. Vanaf eind januari werken de AEM Cloud Service SDK en eventuele cloudomgevingen niet met Java 11-runtime.

>[!NOTE]
>
> Als u wilt profiteren van de nieuwste prestatieoptimalisaties en taalverbeteringen, kunt u het beste bouwen met Java 17 of Java 21 (voorkeur). Samenstellen met Java 8 en Java 11 blijft voorlopig ondersteund, maar wordt in een volgende release vervangen. Een afzonderlijke mededeling zal vóór afschrijving worden uitgegeven. Zie *vereisten van de bouwstijltijd* sectie van [&#x200B; dit artikel &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements).
>

### Handhaving van het configuratiebeleid van AEM Java Logs {#logconfig-policy}

Zoals vermeld in de opmerkingen bij de release van april, moeten AEM Java-logboeken een standaardindeling gebruiken voor betrouwbare bewaking in alle klantomgevingen. Aangepaste logboekconfiguraties, zoals wijzigingen in de logbestandsindeling, uitvoerbestanden of standaardlogniveaus, worden niet meer ondersteund. De logbestanden moeten naar de standaardbestanden worden geleid en de standaardlogniveaus voor AEM-productcode moeten worden behouden. Zie volledige details in het [&#x200B; Registreren artikel &#x200B;](/help/implementing/developing/introduction/logging.md#configuration-loggers).

Beginnend op **November 20th**, zullen om het even welke niet gesteunde douane het registreren met voeten treden worden genegeerd. Op basis van onze analyse zullen de meeste klanten niet worden beïnvloed en heeft Adobe contact opgenomen met klanten van wie de huidige configuratie mogelijk wordt beïnvloed.

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


### AI-antwoorden - slimmere, contextbewuste reacties voor AEM Sites (Beta-programma) {#ai-answers-beta}

AI-antwoorden introduceert een nieuwe manier voor bezoekers om te communiceren met uw inhoud. Met behulp van de RAG-technologie (Retrieval-Augmented Generation) maakt het gebruik van uw door AEM beheerde gegevens om nauwkeurige, merkbestendige antwoorden direct in uw digitale ervaringen te leveren.

Als onderdeel van deze bètaversie kunt u veilig de AI-antwoorden verkennen in uw AEM Cloud Service-omgeving. Met deze aanpak kunt u prestaties, nauwkeurigheid en algemene ervaring valideren voordat u deze ter beschikking stelt van uw livepubliek. Zodra bevestigd, kunt u uw ervaring van AI Antwoorden aan volledige productie bevorderen.

Om bètatoegang aan te vragen of uw te delen, gelieve te contacteren [&#x200B; feedback-ai-answers@adobe.com &#x200B;](mailto:feedback-ai-answers@adobe.com).


### Momentopnamen voor RDE&#39;s (Alpha-programma) {#rde-snapshot-program}

In alfa, steunen de Snelle Milieu&#39;s van de Ontwikkeling (RDEs) nu een eigenschap om een momentopname van de huidige staat van code en inhoud te nemen, die op een recentere tijd kan worden hersteld. Dit kan nuttig zijn wanneer het synchroniseren van code die kan moeten worden teruggekeerd, of wanneer het schakelen tussen ontwikkeling van verschillende eigenschappen. Het is ook mogelijk om alleen de veranderbare inhoud te herstellen als een bekend beginpunt voor het testen.

Gelieve te e-mail [&#x200B; aemcs-rde-support@adobe.com &#x200B;](mailto:aemcs-rde-support@adobe.com) als er belang in het verstrekken van terugkoppelt op deze eigenschap is.

### Uitgebreide Application Performance Monitoring (APM) (Alpha-programma) {#apm-alpha}

Voor waarneming, steunt de Dienst van de Wolk AEM momenteel Adobe-Geleverde [&#x200B; New Relic One &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic) en klant-geleide [&#x200B; Dynatrace &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/dynatrace). Aangezien wij steun voor extra opties van APM onderzoeken, gelieve ons in [&#x200B; aemcs-apm-beta@adobe.com &#x200B;](mailto:aemcs-apm-beta@adobe.com) met uw aangewezen verkoper of technologie, samen met gebruiksgevallen te e-mailen.

## [!DNL Experience Manager] Hulplijnen {#guides}

U kunt een volledige lijst van nieuwe en verbeterde eigenschappen van de recentste versie van Adobe Experience Manager Guides [&#x200B; hier &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [&#x200B; hier &#x200B;](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [&#x200B; hier &#x200B;](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.

## Universele editor {#universal-editor}

U kunt een volledige lijst van Universele versies van de Redacteur [&#x200B; hier &#x200B;](/help/release-notes/universal-editor/current.md) vinden.

## Variaties genereren {#generate-variations}

U kunt een volledige lijst van Generate de versies van Variaties [&#x200B; hier &#x200B;](/help/generative-ai/release-notes-generate-variations.md) vinden.

## Opmerkingen bij de release van Experience Cloud {#experience-cloud}

U kunt informatie over versies van andere toepassingen van Experience Cloud [&#x200B; hier &#x200B;](https://experienceleague.adobe.com/en/docs/release-notes/experience-cloud/current) vinden.
