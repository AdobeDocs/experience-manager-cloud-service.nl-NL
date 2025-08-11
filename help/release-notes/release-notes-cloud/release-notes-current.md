---
title: De huidige Nota's van de Versie voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Huidige versienota's voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 401eaaaa0bb8dad054c7105533cbd4486964c484
workflow-type: tm+mt
source-wordcount: '2269'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies, zoals 2023 of 2024, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [ Update van het Product van de Prioriteit Adobe ](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2025.7.0) is 7 augustus 2025. De volgende release met functies (2025.8.0) is gepland voor 28 augustus 2025.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in Experience Manager Sites {#enhancements-sites}

* U kunt nu inhoudsfragmenten met fragmenten waarnaar wordt verwezen (onderliggende fragmenten) in één bewerking kopiëren. Zo kunt u bestaande structuren voor inhoudsfragmenten opnieuw gebruiken om nieuwe inhoud te maken.
* In de Admin UI van de Fragmenten van de Inhoud kunt u nu de werkschemastatus voor inhoudsfragmenten, met gedetailleerde informatie over verleden en momenteel lopende werkschema&#39;s voor een geselecteerd fragment bekijken.
* Als u de naam van een bronpagina voor een live kopie wijzigt of een bronpagina voor een live kopie verplaatst, wordt het opnieuw publiceren van een overeenkomstige hernoemde of verplaatste pagina voor live kopieën nu geactiveerd.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

**voegt vormen aan Dynamische malplaatjes van Media** toe

U kunt vormlagen [ nu toevoegen aan Dynamische malplaatjes van Media ](/help/assets/dynamic-media/dynamic-media-templates.md#add-shapes-to-the-canvas) in Experience Manager Assets. Vormlagen ondersteunen parameters voor realtime updates via de sjabloon-URL, net als afbeeldings- en tekstlagen. U kunt ook call-to-action-koppelingen (CTA) naar vormen in uw sjablonen opnemen.

![ voegt vormen aan Dynamische malplaatjes van Media ](/help/assets/assets/enable-uniform-radius-shape.png) toe

**AI-Gegenereerde meta-gegevensverhogingen**

AEM Assets laat u nu toe om de vertoning van activa titels in de mening van de Kaart of de mening van de Lijst [ op de Activa te vormen doorbladert pagina. ](/help/assets/smart-tags.md#configure-ai-generated-titles) U kunt ervoor kiezen om de door u gedefinieerde elementtitel weer te geven, de titel die met AI is gegenereerd, of alleen een door AI gegenereerde titel te gebruiken als er geen bestaande titel voor het element bestaat.

![ vorm AI-Gegenereerde titels ](/help/assets/assets/configure-title-ai-generated.png)

U kunt nu ook door AI gegenereerde metagegevens op mapniveau uitschakelen.

### Nieuwe functies in Content Hub {#new-features-content-hub}

**Verbeterde het brandmerken flexibiliteit in Content Hub**

Dankzij de bestaande personalisatiefuncties kunnen beheerders in Content Hub hun implementatie verder aanpassen door aangepaste logoafbeeldingen toe te voegen. De ondersteuning voor de TIFF-bestandsindeling is ook toegevoegd voor zowel banner- als logoafbeeldingen, waardoor het ontwerp flexibeler wordt.

**Slimmer delen met titelverbindingen**

U kunt nu een titel toevoegen wanneer u een gedeelde koppeling genereert. Dit kan in de weergave Elementdetails of nadat u een of meer elementen hebt geselecteerd. Hierdoor kunnen ontvangers gemakkelijker het doel van elke koppeling identificeren, met name bij het ontvangen van meerdere gedeelde elementen.

![ privé en openbare verbinding ](/help/assets/assets/shared-link-for-assets.png)

**Verbeterde filternavigatie**

Content Hub omvat nu a **tonen Al** optie binnen filters, toestaand gebruikers om alle beschikbare facetten samen met activa tellingen van de huidige beperking van het bekijken van slechts tien facetten te bekijken. De verbeterde mogelijkheden voor zoeken en sorteren binnen elk filter maken het gemakkelijker om middelen efficiënter te ontdekken en te beheren.

### AEM Desktop App release 3.0.0 {#desktop-app-release-3.0.0}

Geniet van geautomatiseerde upload van nieuwe bestanden en mappen, verbeterde bestandsbewerkingen, slimmere detectie van middelen en naadloze integratie met AEM—waardoor contentbeheer sneller, duidelijker en intuïtiever wordt.

Voor de volledige lijst van eigenschappen, zie {de Nota&#39;s van de Versie van de App van 0} Desktop [.](https://experienceleague.adobe.com/en/docs/experience-manager-desktop-app/using/release-notes)

### Nieuwe functies in dynamische media met OpenAPI-mogelijkheden {#new-features-dynamic-media-with-openapi}

**activa van de Voorproef alvorens** te publiceren

In [!DNL Dynamic Media with OpenAPI capabilities] kunt u nu rechtstreeks een voorvertoning van elementen weergeven op auteurspagina&#39;s van [!DNL AEM Sites] voordat u deze openbaar maakt. Deel voorvertoningspagina&#39;s met belanghebbenden om feedback te verzamelen over de visuele kwaliteit en contextafhankelijke weergave. Tijdens de revisiecyclus kunt u meerdere elementversies maken en beheren voordat u deze voltooit voor publicatie.

**Verbeterde Slimme Beeldvorming voor OpenAPI beeldverzoeken**

Alle OpenAPI-afbeeldingsaanvragen maken nu volledig gebruik van Smart Imaging met logica voor automatische promotie en fallback. Deze verbetering optimaliseert beelden die op apparaat en netwerkvoorwaarden worden gebaseerd, leverend snellere paginadalading en verminderd bandbreedtegebruik-terwijl het handhaven van visuele kwaliteit.


## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in AEM Forms {#forms-new-features}

**Universele Redacteur voor AanpassingsForms en de Fragmenten van de Vorm**

De [ Universele Redacteur ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) steunt nu de verwezenlijking van zowel Aanpassings Forms als herbruikbare Fragments van de Vorm. Auteurs kunnen visueel formulieren maken, verzendacties configureren en reCAPTCHA-validatie toevoegen, allemaal in een vereenvoudigde WYSIWYG-ontwerpomgeving. Deze mogelijkheid versnelt het maken van formulieren, verbetert de consistentie en verbetert de bescherming tegen spam en geautomatiseerd misbruik.

![ Universele Redacteur ](/help/edge/docs/forms/universal-editor/assets/universal-editor.png){width=80%, align-center}


**de Verzenddienst van Forms voor Edge Delivery Services Forms**

Zie [ de Dienst van de Verzending van Forms ](/help/forms/forms-submission-service.md). kunt u gegevens van Aangepaste formulierverzendingen naadloos opslaan in populaire spreadsheetplatforms zoals Google Sheets, Microsoft OneDrive of SharePoint. Deze integratie stroomlijnt het gegevensbeheer door de directe verzending van formuliergegevens naar het door u gekozen werkblad mogelijk te maken, handmatige gegevensoverdracht te voorkomen en fouten te beperken.

Belangrijkste voordelen zijn:

* **Directe integratie:** vorm uw vormen om gegevens aan een gespecificeerde spreadsheet direct voor te leggen.
* **de gegevenstoewijzing van de Douane:** kaart vormgebieden aan overeenkomstige spreadsheetkolommen voor georganiseerde opslag.
* **controle van de Toegang:** hefboomwerking bestaande spreadsheettoestemmingen om te beheren wie tot voorgelegde gegevens kan toegang hebben of wijzigen.

**produceer en synchroniseer AFP-uitvoeringen van Adaptieve Forms**

De [ API van de Synchronisatie van de Output van AFP ](/help/forms/document-generation-afp-api.md) laat beheerders en gebruikers toe om AFP (Geavanceerde Presentatie van de Functie) output van Adaptieve Forms te produceren en de output met externe systemen of opslagplaatsen te synchroniseren. AFP is een krachtige documentindeling die is geoptimaliseerd voor afdrukken en die vaak wordt gebruikt in grootschalige bedrijfsomgevingen.

<!-- ### New pre-release features in AEM Forms {#forms-new-pre-release-features}

**Enhancements in Rule Editor**

* The `validate` method in the function list now supports validation at the panel, field, and form levels.
* Client-side custom function parsing now supports ES10+ JavaScript features and static imports.
* The button to download Document of Record (DoR) is now available as an out-of-the-box (OOTB) option in the rule editor.
* Rules now support the use of dynamic variables.
* Custom event-based rules are now supported.
* Repeatable panel rules are now executed based on context, rather than only on the last panel instance.
* Rules can now be triggered based on query parameters, UTM parameters, and browser parameters.
* Form-specific custom function scripts are now supported for Adaptive Forms in Edge Delivery Services.

 -->

### Nieuwe functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms-programma voor vroege toegang biedt u een unieke kans om exclusieve toegang te krijgen tot geavanceerde innovaties en om de ontwikkeling ervan te helpen vormgeven.

In deze releaseopmerkingen worden de innovaties vermeld die in de huidige release zijn geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie {de documentatie van het Programma van de Vroege Toegang van AEM Forms [.](/help/forms/early-access-ea-features.md)


<!-- **Forms Optimization opportunities**

Forms Optimization uses AI to analyze your forms and suggest improvements for better performance. It highlights forms with low engagement, flags accessibility issues, and generates AI-powered variations to help increase conversion rates and compliance with WCAG standards.

>[!VIDEO](https://video.tv.adobe.com/v/3469472/) 

Key optimization opportunities include:

* Increasing visibility for forms with low views
* Improving completion rates for forms with low conversions
* Addressing accessibility compliance issues
* Streamlining navigation to enhance user experience

With Forms Optimization, you get automated, data-driven recommendations and variations, making it easier to boost engagement and ensure your forms are effective and inclusive. -->

**Redacteur van de Regel voor Interactieve Communicatie Redacteur**

Creëer dynamische, gegevensgestuurde acties rechtstreeks in uw documenten met behulp van een intuïtieve, wijs-en-klik-interface. U kunt eenvoudig voorwaardelijke logica definiëren, workflows automatiseren en inhoud personaliseren zonder code te schrijven.

**CLI van de Server van AEM Forms voor de Componenten van de Douane**

>[!VIDEO] (https://video.tv.adobe.com/v/3470514/aem-forms)

Versnel uw AEM Forms Edge Delivery Services-ontwikkeling met dit CLI-programma. Produceer meteen de code en de bedrading nodig om de ontwikkeling van de douanecomponent te kickstart — geen boilerplate, geen gedoe.

**API het Hulpmiddel van de Integratie voor Dynamische Gegevens van de Vorm**

Met het API Integration Tool kunnen formulierauteurs dynamische, intelligente formulieren maken die automatisch gegevens ophalen en vullen van externe REST API&#39;s op basis van gebruikersinteracties. Deze integratiefunctie zonder code transformeert statische formulieren naar responsieve interfaces voor gegevensverzameling.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Knooppuntweergave voor machtigingenbeheer {#node-view}

AEM introduceert het beheer voor Node-weergavemachtigingen. De belangrijkste functionaliteit blijft het zelfde als klassieke UI, maar is gebruikersvriendelijker en efficiënter. Zie het [ specifieke artikel ](/help/security/touch-ui-principal-view.md) voor verdere informatie.

### Bijgewerkt implementatieproces {#updated-deprecation-process}

Adobe controleert regelmatig functies, bibliotheken, API&#39;s en configuraties om ervoor te zorgen dat deze voldoen aan de standaarden voor prestaties, beveiliging en waarde. Wanneer de mogelijkheden niet meer aan deze normen voldoen, zijn zij duidelijk voor verval en het gebruik moet tegen een gespecificeerde verwijderingsdatum ophouden. Adobe leidt tot deze datum en herinnert klanten aan e-mailmeldingen en acties die in Cloud Manager moeten worden uitgevoerd voordat ze nieuwe builds gaan gebruiken of implementeren. Als u de vereiste actie niet uitvoert, kan dit ertoe leiden dat u niet kunt upgraden naar nieuwe versies van AEM. Dit kan gevolgen hebben voor de beveiliging, prestaties, betrouwbaarheid en beschikbaarheid.

Zie het [ afgekeuringsartikel ](/help/release-notes/deprecated-removed-features.md) voor verdere informatie.

#### Verouderde Java API&#39;s en OSGi-configuratie die verwijderingsdatums naderen {#deprecated-near-removals}

Vouw de onderstaande lijst uit om de verouderde API&#39;s en OSGi-configuraties weer te geven die niet meer moeten worden gebruikt. Raadpleeg het artikel over veroudering voor volledige informatie, inclusief de tijdlijn voor verwijderen.

<details>
  <summary>Uitvouwen om de afwaarderingen weer te geven</summary>

Java API&#39;s:

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

OSGi-eigenschappen:

* `org.apache.sling.commons.log.LogManager` (alle eigenschappen)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file` , `org.apache.sling.commons.log.pattern`)

</details>

### Java 11 Runtime Deprecation {#java11-runtime-deprecation}

**Java 11 runtime* - is nu afgekeurd, en de meeste milieu&#39;s zijn reeds bevorderd aan uitvoerigere **runtime Java 21**.

Als uw milieu niet wegens niet gesteunde gebiedsdelen (zie [ runtime van Java 21 vereisten ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)) kon worden bevorderd, zou u een e-mail van Adobe met specifieke volgende stappen moeten ontvangen. Gelieve te verzekeren alle vereiste updates tegen **28 augustus, 2025** worden voltooid, zodat kan uw milieu zonder verstoring worden bevorderd.

Opmerking: de runtimeversie staat los van de build-versie van uw code. We raden u aan om samen te werken met Java 21, maar Java 11-builds worden voorlopig nog wel ondersteund. In de toekomst wordt een afzonderlijke aankondiging voor het vervangen van Java 11-builds gedeeld.

### Handhaving van het configuratiebeleid van AEM Java Logs {#logconfig-policy}

Zoals vermeld in de opmerkingen bij de release van april, moeten AEM Java-logboeken een standaardindeling gebruiken voor betrouwbare bewaking in alle klantomgevingen. Aangepaste logboekconfiguraties, zoals wijzigingen in de logbestandsindeling, uitvoerbestanden of standaardlogniveaus, worden niet meer ondersteund. De logbestanden moeten naar de standaardbestanden worden geleid en de standaardlogniveaus voor AEM-productcode moeten worden behouden. Zie volledige details in het [ Registreren artikel ](/help/implementing/developing/introduction/logging.md#configuration-loggers).

Beginnend in **eind Augustus**, zullen om het even welke niet gestaafde overrides van het douaneregistreren worden genegeerd. Op basis van onze analyse zullen de meeste klanten niet worden beïnvloed en heeft Adobe contact opgenomen met klanten van wie de huidige configuratie mogelijk wordt beïnvloed.

Gelieve te herzien en bij te werken om het even welke stroomafwaartse processen die zich op het gedrag van het douaneregistreren baseren. Bijvoorbeeld:

* Als uw logboek het door:sturen systeem een formaat van het douanelogboek verwacht, kunt u uw innameregels moeten aanpassen.
* Als u eerder logboekbreedheid hebt verminderd door logboekniveaus te veranderen, gelieve te merken dat het terugkeren aan standaardniveaus logboekvolume kan verhogen.

### Standaard leegmaken van oudere versies en controlelogboeken {#mt-defaults}

Momenteel, hebben de inhoudsversies en de controlelogboeken hun bijbehorende *purge onderhoudstaken - onbruikbaar gemaakt door gebrek en zo worden geen gegevens verwijderd tenzij uitdrukkelijk gevormd.

Om de prestaties van de opslagplaats te optimaliseren, wordt het leegmaken standaard ingeschakeld op een aangekondigde toekomstige datum, waarbij de volgende richtlijnen worden gevolgd:

#### Inhoudversies {#mt-content}

* **Nieuwe milieu&#39;s* - (gecreeerd na een aanstaande datum (die later worden meegedeeld)
   * De versies ouder dan **30 dagen* - zullen periodiek worden geschrapt.
   * De meest recente vijf versies in de afgelopen 30 dagen blijven behouden, samen met de meest recente versie en de huidige versie, ongeacht hun leeftijd.

* **Bestaande milieu&#39;s* - (gecreeerd vóór deze aanstaande datum):
   * De versies ouder dan **7 jaar* - zullen periodiek worden geschrapt.
   * Alle versies in de afgelopen 7 jaar blijven behouden.
   * Deze hoge standaarddrempel voorkomt dat recente gegevens onbedoeld worden verwijderd. Het wordt echter aanbevolen lagere waarden te configureren om de prestaties van de opslagplaats te optimaliseren.

* U kunt deze gebreken door configuratie wijzigen YAML, die gebruikend de config pijpleiding wordt opgesteld.

#### Controlelogboek {#mt-auditlogs}

* **Nieuwe milieu&#39;s* - (gecreeerd na een aanstaande datum, die afzonderlijk zal worden meegedeeld):
   * De replicatie, DAM, en de logboeken van de paginacontrole ouder dan * *7 dagen* - zullen periodiek worden geschrapt.
   * Alle gebeurtenissen worden standaard geregistreerd.

* **Bestaande milieu&#39;s* - (gecreeerd vóór deze aanstaande datum):
   * De replicatie, DAM, en de logboeken van de paginacontrole ouder dan * *7 jaar* - zullen periodiek worden geschrapt.
   * Alle gebeurtenissen worden standaard geregistreerd.
   * Deze hoge standaarddrempel voorkomt dat recente gegevens onbedoeld worden verwijderd. Het wordt echter aanbevolen lagere waarden te configureren om de prestaties van de opslagplaats te optimaliseren.

* U kunt deze gebreken door configuratie wijzigen YAML, die gebruikend de config pijpleiding wordt opgesteld.

Voor meer details, zie het [ artikel van de Taken van het Onderhoud ](/help/operations/maintenance.md#defaults).

### Edge Computing (Alpha-programma) {#edge-computing}

Met Edge Computing kunt u JavaScript uitvoeren op de CDN-laag, waardoor de gegevensverwerking dichter bij de eindgebruiker komt te staan. Dit vermindert latentie en maakt responsieve, dynamische ervaringen aan de rand mogelijk.

Vaak voorkomende gevallen van gebruik zijn:

* Gebruikers verifiëren met een identiteitsprovider voordat toegang tot inhoud wordt verleend
* Inhoud aanpassen op basis van geolocatie, apparaattype of gebruikerskenmerken
* Handelend als middleware tussen CDN en uw oorsprong
* Reacties van externe API&#39;s opnieuw opmaken (en wellicht meerdere API&#39;s samenvoegen) voordat deze naar de browser worden verzonden
* Door de server gerenderde HTML aan de rand samenstellen en bedienen met inhoud die vanuit verschillende achtergronden is geplaatst
* Het blootstellen van een server MCP voor LLMs zoals ChatGPT en Claude om tot douanegereedschappen toegang te hebben

We hebben een beperkt aantal mogelijkheden voor AEM Publish Delivery- of Edge Delivery Services-projecten voor live productiesites. Als u in het deelnemen geinteresseerd bent of meer wilt leren, gelieve [ aemcs-edgecompute-feedback@adobe.com ](mailto:aemcs-edgecompute-feedback@adobe.com) met een korte beschrijving van uw gebruiksgeval te e-mailen.

### CDN-configuratie voor Edge Delivery Services (Beta-programma) {#cdn-eds-beta}

Adobe-Beheerde CDN biedt flexibele configuratieopties aan, zoals die in het [ wordt beschreven Config Artikel van de Pijpleiding ](/help/operations/config-pipeline.md#configurations).

Nu in een bèta, stel een config pijpleiding voor eigenschappen met inbegrip van CDN oorsprongselectors, reactie en verzoektransformaties, CDN logboek op door:sturen en meer. Gelieve te bereiken uit aan [ aemcs-cdn-config-adopter@adobe.com ](mailto:aemcs-cdn-config-adopter@adobe.com) met de details van uw gebruiksgeval.

### Momentopnamen voor RDE&#39;s (Alpha-programma) {#rde-snapshot-beta}

In alfa, steunen de Snelle Milieu&#39;s van de Ontwikkeling (RDEs) nu een eigenschap om een momentopname van de huidige staat van code en inhoud te nemen, die op een recentere tijd kan worden hersteld. Dit kan nuttig zijn wanneer het synchroniseren van code die kan moeten worden teruggekeerd, of wanneer het schakelen tussen ontwikkeling van verschillende eigenschappen. Het is ook mogelijk om alleen de veranderbare inhoud te herstellen als een bekend beginpunt voor het testen.

Gelieve te e-mail [ aemcs-rde-support@adobe.com ](mailto:aemcs-rde-support@adobe.com) als er belang in het verstrekken van terugkoppelt op deze eigenschap is.

### AEM Log-Forwarding aan Meer Doelen (het Programma van Beta) {#log-forwarding-beta}

Hoewel de logboeken van Cloud Manager kunnen worden gedownload, vinden vele organisaties het nuttig om die logboeken aan een aangewezen registrerenbestemming te stromen. AEM biedt al ondersteuning voor het doorsturen van AEM- en CDN-logbestanden naar Azure Blob Storage, Datadog, HTTPS, Elasticsearch (en OpenSearch) en Splunk. Deze eigenschap wordt gevormd op een zelf-servermanier, en opgesteld gebruikend de Pijpleiding Config.

Nu in bèta kunt u AEM-logs doorsturen naar Amazon S3, Sumo Logic, Dynatrace en uw eigen New Relic-account (niet naar het door Adobe verschafte account). Merk op dat de logboeken van AEM (met inbegrip van Apache/Dispatcher) voor deze registrerenbestemmingen, maar niet CDN- logboeken worden gesteund. E-mail [ aemcs-logforwarding-beta@adobe.com ](mailto:aemcs-logforwarding-beta@adobe.com) voor toegang.

Leer meer in het [ logboek door:sturen documentatie ](/help/implementing/developing/introduction/log-forwarding.md).

## [!DNL Experience Manager] Hulplijnen {#guides}

U kunt een volledige lijst van nieuwe en verbeterde eigenschappen van de recentste versie van Adobe Experience Manager Guides [ hier ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.

## Universele editor {#universal-editor}

U kunt een volledige lijst van Universele versies van de Redacteur [ hier ](/help/release-notes/universal-editor/current.md) vinden.

## Variaties genereren {#generate-variations}

U kunt een volledige lijst van Generate de versies van Variaties [ hier ](/help/generative-ai/release-notes-generate-variations.md) vinden.

## Opmerkingen bij de release van Experience Cloud {#experience-cloud}

U kunt informatie over versies van andere toepassingen van Experience Cloud [ hier ](https://experienceleague.adobe.com/en/docs/release-notes/experience-cloud/current) vinden.
