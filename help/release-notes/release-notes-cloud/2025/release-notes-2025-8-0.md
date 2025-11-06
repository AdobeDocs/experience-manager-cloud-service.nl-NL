---
title: Nota's van de versie voor 2025.8.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2025.8.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1919'
ht-degree: 0%

---

# Opmerkingen bij de release 2025.8.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2025.8.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies, zoals 2023 of 2024, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [ Update van het Product van de Prioriteit Adobe ](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2025.8.0) is 28 augustus 2025. De volgende release met functies (2025.9.0) is gepland voor 25 september 2025.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

<!-- 

## Release Video {#release-video}

Have a look at the July 2025 Release Overview video for a summary of the features added in the 2025.7.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## Experience Hub {#experience-hub}

[ Experience Hub ](/help/experience-hub.md) is uw gecentraliseerd uitgangspunt voor de toegang tot van alle mogelijkheden van AEM. Het is gepersonaliseerd op basis van uw gebruikersnaam en de licenties waarover u beschikt, zodat elke gebruiker zijn resultaten efficiënt kan uitvoeren.

## AI Assistant in AEM {#AI-assistant}

De [ AI Medewerker ](/help/implementing/cloud-manager/ai-assistant-in-aem.md) voor AEM biedt een gespreksinterface aan die wordt ontworpen om u onmiddellijke antwoorden aan uw product-verwante vragen van AEM te krijgen (*beschikbaar aan alle gebruikers*) en de verwezenlijking van het steunkaartje te automatiseren (*beschikbaar aan Admins van de Steun*). Het is rechtstreeks ingesloten in AEM en toegankelijk vanuit AEM Experience Hub, Cloud Manager en de gebruikersinterface van de auteur.

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in Experience Manager Sites {#enhancements-sites}

* In de Admin UI van de Fragmenten van de Inhoud kunt u nu de werkschemastatus voor inhoudsfragmenten, met gedetailleerde informatie over verleden en momenteel lopende werkschema&#39;s voor een geselecteerd fragment bekijken.
* De prestaties voor het openen van inhoudsfragmenten in de nieuwe inhoudsfragmenteditor zijn in algemene scenario&#39;s met 25% verbeterd door fragmenten te openen via UUID in plaats van via pad.
* Wanneer u inhoudsfragmenten kopieert met fragmenten waarnaar wordt verwezen, worden kopieën van de fragmenten waarnaar wordt verwezen nu opgeslagen op dezelfde locatie als de bovenliggende fragmentkopie.
* U kunt nu een aangepaste werkruimte configureren in de mapinstellingen om de inhoudsfragmenten te exporteren naar de geconfigureerde werkruimte in Adobe Target.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in Content Hub {#new-features-content-hub}

**BulkOnderzoek via de eigenschappen van de Filter**

Content Hub maakt het nu sneller om de middelen te ontdekken die u nodig hebt. Met het nieuwe Onduidelijke vermogen van het Onderzoek, kunt u veelvoudige waarden voor om het even welk filterbezit-die door een scheidingsteken (bijvoorbeeld, veelvoudige SKU IDs) wordt gescheiden ingaan-en onmiddellijk alle passende activa terugwinnen gebruikend één enkel onderzoek.

### Nieuwe functies in dynamische media met OpenAPI-mogelijkheden {#new-features-dynamic-media-with-openapi}

**Gemarkeerde en Leesbare Levering URLs van Activa**

Dynamische media met OpenAPI-URL&#39;s leesbaarder maken door Vanity-URL&#39;s te gebruiken in Dynamic Media met OpenAPI. Met URL&#39;s met Vanity kunnen lange, door het systeem gegenereerde, moeilijk te onthouden UUID&#39;s in URL&#39;s voor het leveren van elementen worden vervangen door korte, door het merk gecontroleerde id&#39;s. Hierdoor zijn Vanity-URL&#39;s korter, gemakkelijker te lezen en te delen en kunt u ze beter aanpassen aan uw merk of campagnes. URL&#39;s met Vanity worden tijdens runtime automatisch omgezet in de oorspronkelijke UUID van het element zonder bestaande workflows te onderbreken.

>[!NOTE]
>
>Deze functie is beschikbaar als functie voor beperkte beschikbaarheid. Zie [ dit artikel ](/help/assets/vanity-urls.md) om begonnen te worden.

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

* [ Component van de Invoer van de Datum &amp; van de Tijd ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-time-component): Een component van de Datum &amp; van de Tijd is nu beschikbaar, toelatend gebruikers om zowel datum en tijd te selecteren gebruikend een kalender en klokinterface, of door waarden in een gesteund formaat manueel in te gaan.
* [ Verbeterde de Behandeling van de Fout voor Dossier uploadt ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment#basic-tab): De component van de Bijlage van het Dossier bevestigt nu automatisch het geuploade dossiertype tegen de lijst van gewenste personen. Als een gebruiker een bestand in een niet-ondersteunde indeling uploadt, wordt tijdens het verzenden een fout weergegeven. De component controleert ook de bestandsinhoud om het type te valideren, waardoor de algemene beveiliging van het formulier wordt verbeterd.
* [ specificeerde de Reactie van de Fout voor Douane legt Actie ](/help/forms/custom-submit-action-troubleshooting.md) voor: Wanneer een douane voorlegt actie een niet behandelde fout ontmoet, foutencode 502 is teruggekeerd. Dit helpt identificeren dat de kwestie met de douane verwant is voorlegt actie, die het zuiveren gemakkelijker maakt.
* [ exclusief Verborgen Gebieden van Document van Verslag ](/help/forms/generate-document-of-record-core-components.md#document-of-record-settings): Een nieuw bezit is toegevoegd om uitsluiting van verborgen gebieden van het Document van Verslag toe te staan. Deze optie is standaard niet geselecteerd en is van toepassing op alle formuliervelden.

### Functies vóór de release in AEM Forms

* [ produceert en synchroniseert de Vertoningen van AFP ](/help/forms/document-generation-afp-api.md): U kunt de Communicatie API van AEM Forms nu gebruiken om een XDP dossier in formaat om te zetten AFP. AFP is een krachtige indeling die op grote schaal wordt gebruikt bij het afdrukken in grote ondernemingen.
* **Verbeteringen in de Redacteur van de Regel**
   * [ bevestigt Methode in de Lijst van de Functie ](/help/forms/rule-editor-enhancements-use-cases.md#validate-method-in-function-list): Bevestig en stel methodes nu uitvoering op het paneel, gebied, en vormniveaus terug. Eerder werden deze alleen ondersteund op formulierniveau.
   * [ Moderne Steun van JavaScript ](/help/forms/rule-editor-core-components-difference-tables.md): De steun voor ECMAScript 2019 en recentere eigenschappen is toegevoegd voor douanefuncties, die u toestaan om efficiëntere, modulaire, en herbruikbare code te schrijven
   * [ Optie van DoR van de Download in de Redacteur van de Regel ](/help/forms/rule-editor-enhancements-use-cases.md#downloaddor-as-ootb-fuction-in-rule-editor): Een functie om het Document van Verslag (DoR) te downloaden is toegevoegd als uit-van-de-doos (OTB) optie in de Redacteur van de Regel.
     ![ document-van-Verslag ](/help/forms/assets/document-of-record-rn.gif)
   * [ Dynamische Variabelen in de Redacteur van de Regel ](/help/forms/rule-editor-enhancements-use-cases.md#support-for-dynamic-variables-in-rules): U kunt dynamische (tijdelijke) variabelen in de Redacteur van de Regel voor grotere flexibiliteit nu gebruiken in het bepalen van voorwaarden en acties. Verborgen velden zijn niet meer vereist voor het opslaan van tijdelijke waarden.
   * [ de Gebaseerde Steun van de Regels van de Gebeurtenis van de Douane ](/help/forms/rule-editor-enhancements-use-cases.md#custom-event-based-rules-support): U kunt douanegebeurtenissen en trekkerregels nu bepalen die op die gebeurtenissen worden gebaseerd.
   * [ context-Adequate Regels van het Comité ](/help/forms/rule-editor-enhancements-use-cases.md#context-based-rule-execution-for-repeatable-panels): In herhaalbare panelen, worden de regels nu uitgevoerd gebaseerd op context, in plaats van slechts op de laatste paneelinstantie worden toegepast.
   * [ Regels die door Parameters ](/help/forms/rule-editor-enhancements-use-cases.md#url-and-browser-parameter-based-rules-in-adaptive-forms) worden teweeggebracht: De Redacteur van de Regel steunt nu regeluitvoering die op vraagparameters, parameters UTM, of browser parameters wordt gebaseerd.
   * [ vorm-Specifieke Functies van de Douane ](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md#organizing-custom-functions-across-different-forms): Edge Delivery Services Forms steunt nu vorm-specifieke manuscripten van de douanefunctie, die grotere flexibiliteit in het beheren van herbruikbare logica verstrekken.
   * [ Statische Invoer voor de Functies van de Douane ](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md#static-imports-for-custom-functions): De Redacteur van de Regel in Universele Redacteur steunt nu statische invoer, toestaand ontwikkelaars om, functies over veelvoudige vormen te organiseren te delen en opnieuw te gebruiken.

### Functies voor vroege adopters in AEM Forms

* [ de Component van de Handtekening van de Krabbels ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/scribble-signature): U kunt de component van de Handtekening nu gebruiken om gebruikers te helpen hun handtekeningen aan een vorm, zoals in een overeenkomstenvorm toevoegen. Met de component kunnen gebruikers hun handtekening rechtstreeks in het formulier tekenen met een muis, pen of touchscreen.
* [ Directe API Integratie in de Redacteur van de Regel ](/help/forms/api-integration-in-rule-editor.md): De adaptieve Forms steunt nu directe API integratie in de Visuele Redacteur van de Regel zonder een Model van de Gegevens van de Vorm te vereisen. Auteurs kunnen API&#39;s configureren met behulp van een URL- of cURL-import, invoer-/uitvoerparameters toewijzen en aanroepen beveiligen met verificatie.

<!--
**Forms Optimization opportunities**

Forms Optimization uses AI to analyze your forms and suggest improvements for better performance. It highlights forms with low engagement, flags accessibility issues, and generates AI-powered variations to help increase conversion rates and compliance with WCAG standards.

>[!VIDEO](https://video.tv.adobe.com/v/3469472/) 

Key optimization opportunities include:

* Increasing visibility for forms with low views
* Improving completion rates for forms with low conversions
* Addressing accessibility compliance issues
* Streamlining navigation to enhance user experience

With Forms Optimization, you get automated, data-driven recommendations and variations, making it easier to boost engagement and ensure your forms are effective and inclusive. -->

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### JavaScript Compilation Update {#javascript-compilation}

De standaard client-side bibliotheek (clientlibs) JavaScript-compilatie richt zich nu op ECMASCRIPT_2018 in plaats van ECMASCRIPT5. Deze update kan in het verleden worden overschreven, maar maakt prestatieverbeteringen, moderne JavaScript-syntaxis en functies standaard mogelijk.

### Opkomende Java API-implementaties {#java-api-deprecation}

Verschillende verouderde API&#39;s richten zich op verwijdering op 31 augustus en moeten daarom niet langer worden vermeld. Begin september worden de kennisgevingen van het Actions Center verzonden als API-gebruik wordt gedetecteerd. Na 25 september verschijnen er berichten tijdens Cloud Manager-builds om het belang van het verwijderen van het gebruik te versterken. Zie het [ afgekeuringsartikel ](/help/release-notes/deprecated-removed-features.md#aem-apis) voor volledige details, maar voor gemak, zijn deze APIs hieronder vermeld:

<details>
  <summary>Uitvouwen om de afgekeurde Java API's weer te geven</summary>

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

</details>

<!--
OSGi properties:

* `org.apache.sling.commons.log.LogManager` (all properties)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)
* 

-->

### Java 11 Runtime Deprecation {#java11-runtime-deprecation}

*Java 11 runtime* is nu afgekeurd, en de meeste milieu&#39;s zijn reeds bevorderd aan uitvoerigere **runtime Java 21**.

Als uw milieu niet wegens niet gesteunde gebiedsdelen (zie [ runtime van Java 21 vereisten ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)) kon worden bevorderd, zou u een e-mail van Adobe met specifieke volgende stappen moeten ontvangen. Gelieve te verzekeren alle vereiste updates tegen **1 Oktober, 2025** worden voltooid, zodat kan uw milieu zonder verstoring worden bevorderd.

Opmerking: de runtimeversie staat los van de build-versie van uw code. We raden u aan om samen te werken met Java 21, maar Java 11-builds worden voorlopig nog wel ondersteund. In de toekomst wordt een afzonderlijke aankondiging voor het vervangen van Java 11-builds gedeeld.

### Handhaving van het configuratiebeleid van AEM Java Logs {#logconfig-policy}

Zoals vermeld in de opmerkingen bij de release van april, moeten AEM Java-logboeken een standaardindeling gebruiken voor betrouwbare bewaking in alle klantomgevingen. Aangepaste logboekconfiguraties, zoals wijzigingen in de logbestandsindeling, uitvoerbestanden of standaardlogniveaus, worden niet meer ondersteund. De logbestanden moeten naar de standaardbestanden worden geleid en de standaardlogniveaus voor AEM-productcode moeten worden behouden. Zie volledige details in het [ Registreren artikel ](/help/implementing/developing/introduction/logging.md#configuration-loggers).

Beginnend op **25th September**, zullen om het even welke niet gesteunde douanehet registreren met voeten treden worden genegeerd. Op basis van onze analyse zullen de meeste klanten niet worden beïnvloed en heeft Adobe contact opgenomen met klanten van wie de huidige configuratie mogelijk wordt beïnvloed.

Gelieve te herzien en bij te werken om het even welke stroomafwaartse processen die zich op het gedrag van het douaneregistreren baseren. Bijvoorbeeld:

* Als uw logboek het door:sturen systeem een formaat van het douanelogboek verwacht, kunt u uw innameregels moeten aanpassen.
* Als u eerder logboekbreedheid hebt verminderd door logboekniveaus te veranderen, gelieve te merken dat het terugkeren aan standaardniveaus logboekvolume kan verhogen.

### Edge Computing (Beta-programma) {#edge-computing}

Met Edge Computing kunt u JavaScript uitvoeren op de CDN-laag, waardoor de gegevensverwerking dichter bij de eindgebruiker komt te staan. Dit vermindert latentie en maakt responsieve, dynamische ervaringen aan de rand mogelijk.

Vaak voorkomende gevallen van gebruik zijn:

* Gebruikers verifiëren met een identiteitsprovider voordat toegang tot inhoud wordt verleend
* Inhoud aanpassen op basis van geolocatie, apparaattype of gebruikerskenmerken
* Handelend als middleware tussen CDN en uw oorsprong
* Reacties van externe API&#39;s opnieuw opmaken (en wellicht meerdere API-reacties samenvoegen) voordat deze naar de browser worden verzonden
* Door de server gerenderde HTML aan de rand samenstellen en bedienen met inhoud die vanuit verschillende achtergronden is geplaatst
* Het blootstellen van een server MCP voor LLMs zoals ChatGPT en Claude om tot douanegereedschappen toegang te hebben

We hebben een beperkt aantal mogelijkheden voor AEM Publish Delivery- of Edge Delivery Services-projecten voor live productiesites. Als u in het deelnemen geinteresseerd bent of meer wilt leren, gelieve [ aemcs-edgecompute-feedback@adobe.com ](mailto:aemcs-edgecompute-feedback@adobe.com) met een korte beschrijving van uw gebruiksgeval te e-mailen.

### CDN-configuratie voor Edge Delivery Services (Beta-programma) {#cdn-eds-beta}

Adobe-Beheerde CDN biedt flexibele configuratieopties aan, zoals die in het [ wordt beschreven Config Artikel van de Pijpleiding ](/help/operations/config-pipeline.md#configurations).

Nu in bèta, kunt u een config pijpleiding voor eigenschappen met inbegrip van CDN oorsprongselectors, reactie en verzoektransformaties, CDN logboek opstellen door:sturen en meer. Gelieve te bereiken uit aan [ aemcs-cdn-config-adopter@adobe.com ](mailto:aemcs-cdn-config-adopter@adobe.com) met de details van uw gebruiksgeval.

### Momentopnamen voor RDE&#39;s (Alpha-programma) {#rde-snapshot-program}

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
