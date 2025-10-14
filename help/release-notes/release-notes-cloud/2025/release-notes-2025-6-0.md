---
title: Nota's van de versie voor 2025.6.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2025.6.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 6bd35c41-4caf-481c-8cf5-b739307e70da
source-git-commit: 92077a34aa02daf177ca760dafca1a6190a8acb8
workflow-type: tm+mt
source-wordcount: '1363'
ht-degree: 0%

---

# Opmerkingen bij de release 2025.6.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2025.6.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies, zoals 2023 of 2024, vrij te geven.
>
>Heb een blik bij [&#x200B; Experience Manager geeft Roadmap &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [&#x200B; Update van het Product van de Prioriteit Adobe &#x200B;](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2025.6.0) is 26 juni 2025. De volgende release met functies (2025.7.0) is gepland voor 7 augustus 2025.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [&#x200B; hier &#x200B;](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van juni 2025 voor een overzicht van de functies die in de release van 2025.6.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3470884?quality=12&captions=dut)

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

**Verbeterd beheer van de Vorm van Meta-gegevens in de Mening van Assets**

U kunt metagegevensformulieren nu rechtstreeks vanuit de beheerweergave importeren in de Assets-weergave. Wijzigingen die in de weergave Assets in deze formulieren worden aangebracht, weerspiegelen automatisch in de beheerweergave, zodat ze consistent blijven in beide ervaringen. Deze mogelijkheid biedt ondersteuning voor een naadloze overgang naar de nieuwe Assets-weergave, terwijl de continuïteit met de bestaande configuraties van metagegevens behouden blijft.

![&#x200B; AI geproduceerde meta-gegevens &#x200B;](/help/assets/assets/import-metadata-forms-page.png)

### Nieuwe functies in Content Hub {#new-features-content-hub}

**het bestuur van Inzamelingen**

Content Hub laat u [&#x200B; nu toegang tot inzamelingen tijdens verwezenlijking controleren, die slechts erkende gebruikers verzekeren kan gegroepeerde activa &#x200B;](/help/assets/collections-content-hub.md##create-collections) bekijken of beheren. Het zorgt voor betere veiligheid, betere samenwerking, georganiseerd activabeheer, en vereenvoudigd bestuur.

>[!VIDEO](https://video.tv.adobe.com/v/3463336)

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Bijgewerkt implementatieproces {#updated-deprecation-process}

Adobe controleert regelmatig functies, bibliotheken, API&#39;s en configuraties om ervoor te zorgen dat deze voldoen aan de standaarden voor prestaties, beveiliging en waarde. Wanneer de mogelijkheden niet meer aan deze normen voldoen, zijn zij duidelijk voor verval en het gebruik moet tegen een gespecificeerde verwijderingsdatum ophouden. Adobe leidt tot deze datum en herinnert klanten aan e-mailmeldingen en acties die in Cloud Manager moeten worden uitgevoerd voordat ze nieuwe builds gaan gebruiken of implementeren. Als u de vereiste actie niet uitvoert, kan dit ertoe leiden dat u niet kunt upgraden naar nieuwe versies van AEM. Dit kan gevolgen hebben voor de beveiliging, prestaties, betrouwbaarheid en beschikbaarheid.

Zie het [&#x200B; afgekeuringsartikel &#x200B;](/help/release-notes/deprecated-removed-features.md) voor verdere informatie.

#### Verouderde Java API&#39;s en OSGi-configuratie die verwijderingsdatums naderen {#deprecated-near-removals}

Vouw de onderstaande lijst uit om de verouderde API&#39;s en OSGi-configuraties weer te geven die niet meer moeten worden gebruikt. Raadpleeg het artikel over veroudering voor volledige informatie, inclusief de tijdlijn voor verwijderen.

+++Uitvouwen om de afwaarderingen weer te geven

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

+++

### Java 11 Runtime Deprecation {#java11-runtime-deprecation}

**Java 11 runtime** is nu afgekeurd, en de meeste milieu&#39;s zijn reeds bevorderd aan uitvoerigere **runtime Java 21**.

Als uw milieu niet wegens niet gesteunde gebiedsdelen (zie [&#x200B; runtime van Java 21 vereisten &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)) kon worden bevorderd, zou u een e-mail van Adobe met specifieke volgende stappen moeten ontvangen. Gelieve te verzekeren alle vereiste updates tegen **28 augustus, 2025** worden voltooid, zodat kan uw milieu zonder verstoring worden bevorderd.

Opmerking: de runtimeversie staat los van de build-versie van uw code. We raden u aan om samen te werken met Java 21, maar Java 11-builds worden voorlopig nog wel ondersteund. In de toekomst wordt een afzonderlijke aankondiging voor het vervangen van Java 11-builds gedeeld.

### Handhaving van het configuratiebeleid van AEM Java Logs {#logconfig-policy}

Zoals vermeld in de opmerkingen bij de release van april, moeten AEM Java-logboeken een standaardindeling gebruiken voor betrouwbare bewaking in alle klantomgevingen. Aangepaste logboekconfiguraties, zoals wijzigingen in de logbestandsindeling, uitvoerbestanden of standaardlogniveaus, worden niet meer ondersteund. De logbestanden moeten naar de standaardbestanden worden geleid en de standaardlogniveaus voor AEM-productcode moeten worden behouden. Zie volledige details in het [&#x200B; Registreren artikel &#x200B;](/help/implementing/developing/introduction/logging.md#configuration-loggers).

Beginnend in **eind Augustus**, zullen om het even welke niet gestaafde overrides van het douaneregistreren worden genegeerd. Op basis van onze analyse zullen de meeste klanten niet worden beïnvloed en heeft Adobe contact opgenomen met klanten van wie de huidige configuratie mogelijk wordt beïnvloed.

Gelieve te herzien en bij te werken om het even welke stroomafwaartse processen die zich op het gedrag van het douaneregistreren baseren. Bijvoorbeeld:

* Als uw logboek het door:sturen systeem een formaat van het douanelogboek verwacht, kunt u uw innameregels moeten aanpassen.
* Als u eerder logboekbreedheid hebt verminderd door logboekniveaus te veranderen, gelieve te merken dat het terugkeren aan standaardniveaus logboekvolume kan verhogen.

### Standaard leegmaken van oudere versies en controlelogboeken {#mt-defaults}

Momenteel, hebben de inhoudsversies en de controlelogboeken hun bijbehorende *taken van het zuiveringsonderhoud* gehandicapt door gebrek en zo wordt geen gegeven verwijderd tenzij uitdrukkelijk gevormd.

Nochtans, om bewaarplaatsprestaties te optimaliseren, die in **begin juli 2025** beginnen, zal het zuiveren door gebrek worden toegelaten, die deze richtlijnen volgen:

#### Inhoudversies {#mt-content}

* **Nieuwe milieu&#39;s** (gecreeerd na een aanstaande datum die later moet worden meegedeeld)
   * Versies ouder dan **30 dagen** zullen periodiek worden geschrapt.
   * De meest recente vijf versies in de afgelopen 30 dagen blijven behouden, samen met de meest recente versie en de huidige versie, ongeacht hun leeftijd.

* **Bestaande milieu&#39;s** (gecreeerd vóór deze aanstaande datum):
   * Versies ouder dan **7 jaar** zullen periodiek worden geschrapt.
   * Alle versies in de afgelopen 7 jaar blijven behouden.
   * Deze hoge standaarddrempel voorkomt dat recente gegevens onbedoeld worden verwijderd. Het wordt echter aanbevolen lagere waarden te configureren om de prestaties van de opslagplaats te optimaliseren.

* U kunt deze gebreken door configuratie wijzigen YAML, die gebruikend de config pijpleiding wordt opgesteld.

#### Controlelogboek {#mt-auditlogs}

* **Nieuwe milieu&#39;s** (gecreeerd na een aanstaande datum, die afzonderlijk zal worden meegedeeld):
   * De replicatie, DAM, en de logboeken van de paginacontrole ouder dan **7 dagen** zullen periodiek worden geschrapt.
   * Alle gebeurtenissen worden standaard geregistreerd.

* **Bestaande milieu&#39;s** (gecreeerd vóór deze aanstaande datum):
   * De replicatie, DAM, en de logboeken van de paginacontrole ouder dan **7 jaar** zullen periodiek worden geschrapt.
   * Alle gebeurtenissen worden standaard geregistreerd.
   * Deze hoge standaarddrempel voorkomt dat recente gegevens onbedoeld worden verwijderd. Het wordt echter aanbevolen lagere waarden te configureren om de prestaties van de opslagplaats te optimaliseren.

* U kunt deze gebreken door configuratie wijzigen YAML, die gebruikend de config pijpleiding wordt opgesteld.

Voor meer details, zie het [&#x200B; artikel van de Taken van het Onderhoud &#x200B;](/help/operations/maintenance.md#defaults).

### Edge Computing (Alpha-programma) {#edge-computing}

Met Edge Computing kunt u JavaScript uitvoeren op de CDN-laag, waardoor de gegevensverwerking dichter bij de eindgebruiker komt te staan. Dit vermindert latentie en maakt responsieve, dynamische ervaringen aan de rand mogelijk.

Vaak voorkomende gevallen van gebruik zijn:

* Gebruikers verifiëren met een identiteitsprovider voordat toegang tot inhoud wordt verleend
* Inhoud aanpassen op basis van geolocatie, apparaattype of gebruikerskenmerken
* Handelend als middleware tussen CDN en uw oorsprong
* Reacties van externe API&#39;s opnieuw opmaken (en wellicht meerdere API&#39;s samenvoegen) voordat deze naar de browser worden verzonden
* Door de server gerenderde HTML aan de rand samenstellen en bedienen met inhoud die vanuit verschillende achtergronden is geplaatst

We hebben een beperkt aantal mogelijkheden voor AEM Publish Delivery- of Edge Delivery Services-projecten voor live productiesites. Als u in het deelnemen geinteresseerd bent of meer wilt leren, gelieve [&#x200B; aemcs-edgecompute-feedback@adobe.com &#x200B;](mailto:aemcs-edgecompute-feedback@adobe.com) met een korte beschrijving van uw gebruiksgeval te e-mailen.

### CDN-configuratie voor Edge Delivery Services (Beta-programma) {#cdn-eds-beta}

Adobe-Beheerde CDN biedt flexibele configuratieopties aan, zoals die in het [&#x200B; wordt beschreven Config Artikel van de Pijpleiding &#x200B;](/help/operations/config-pipeline.md#configurations).

Nu in een bèta, stel een config pijpleiding voor eigenschappen met inbegrip van CDN oorsprongselectors, reactie en verzoektransformaties, en meer op. Gelieve te bereiken uit aan [&#x200B; aemcs-cdn-config-adopter@adobe.com &#x200B;](mailto:aemcs-cdn-config-adopter@adobe.com) met de details van uw gebruiksgeval.

### AEM Log-Forwarding aan Meer Doelen (het Programma van Beta) {#log-forwarding-beta}

Hoewel de logboeken van Cloud Manager kunnen worden gedownload, vinden vele organisaties het nuttig om die logboeken aan een aangewezen registrerenbestemming te stromen. AEM biedt al ondersteuning voor het doorsturen van AEM- en CDN-logbestanden naar Azure Blob Storage, Datadog, HTTPS, Elasticsearch (en OpenSearch) en Splunk. Deze eigenschap wordt gevormd op een zelf-servermanier, en opgesteld gebruikend de Pijpleiding Config.

Nu in bèta kunt u AEM-logs doorsturen naar Amazon S3, Sumo Logic en uw eigen New Relic-account (niet naar het door Adobe verschafte account). Merk op dat de logboeken van AEM (met inbegrip van Apache/Dispatcher) voor deze registrerenbestemmingen, maar niet CDN- logboeken worden gesteund. E-mail [&#x200B; aemcs-logforwarding-beta@adobe.com &#x200B;](mailto:aemcs-logforwarding-beta@adobe.com) voor toegang.

Leer meer in het [&#x200B; logboek door:sturen documentatie &#x200B;](/help/implementing/developing/introduction/log-forwarding.md).

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
