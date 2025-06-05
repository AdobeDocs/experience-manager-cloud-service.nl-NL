---
title: De huidige Nota's van de Versie voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Huidige versienota's voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 949a3956a88ae8075e1c518e50400f81b603924d
workflow-type: tm+mt
source-wordcount: '2067'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies, zoals 2023 of 2024, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [ Update van het Product van de Prioriteit Adobe ](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}


De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2025.5.0) is 5 juni 2025. De volgende release met functies (2025.6.0) is gepland voor 26 juni 2025.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

<!-- 

## Release Video {#release-video}

Have a look at the February 2025 Release Overview video for a summary of the features added in the 2025.2.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

-->

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

**AI-Gegenereerde meta-gegevens**

AEM Assets gebruikt nu [ AI om meta-gegevens, met inbegrip van Titel, Beschrijving, en Sleutelwoorden ](/help/assets/metadata-assets-view.md#ai-smart-tags) automatisch te produceren. Deze door AI gegenereerde velden verbeteren de nauwkeurigheid van metagegevens, waardoor de elementen gemakkelijker kunnen worden doorzocht, ingedeeld en aanbevolen. Deze aanpak verbetert niet alleen de efficiëntie door handmatige codering te elimineren, maar zorgt ook voor consistentie en schaalbaarheid op grote volumes digitale inhoud.

![ AI geproduceerde meta-gegevens ](/help/assets/assets/enhanced-smart-tags.png)

**Integratie met Figma**

AEM Assets integreert native met Figma, waardoor ontwerpers rechtstreeks vanuit de gebruikersinterface van Figma toegang hebben tot de elementen die in AEM Assets zijn opgeslagen. U kunt inhoud die in AEM Assets wordt beheerd, in het Figma-canvas plaatsen en vervolgens nieuwe of bewerkte inhoud opslaan in de AEM Assets-opslagruimte.

![ Integratie met Figma ](/help/assets/assets/figma-integration.png)


### Nieuwe functies in Content Hub {#new-features-content-hub}

**Op attributen-Gebaseerd Toegangsbeheer (ABAC)**

Met Content Hub kunt u nu op regels gebaseerde beperkingen toepassen op toegang tot elementen. Machtigingen voor bedrijfsmiddelen zorgen voor governance en zorgen er ook voor dat alleen de relevante bedrijfsmiddelen toegankelijk zijn voor gebruikers.

De regels voor het beperken van elementen zijn gebaseerd op metagegevens en als de voorwaarden die in de regel zijn gedefinieerd overeenkomen met de metagegevens van het element, wordt het element weergegeven aan de gebruikersgroepen.

Enkele belangrijke voordelen van op Attribuut-Gebaseerd Toegangsbeheer omvatten:

* Elimineert de afhankelijkheid van de mapstructuur voor machtigingen

* Staat beheerders toe om activa te uploaden en toestemmingsstructuren met terugwerkende kracht te bepalen

* Vermindert het aantal duplicaten - verbetert de integriteit van elementen. Er zijn dubbele machtigingen nodig in op mappen gebaseerde machtigingen wanneer dezelfde elementen met verschillende groepen worden gedeeld.

**het Brandmerken UI**

In Content Hub kunnen beheerders nu de gebruikersinterface aanpassen met merkspecifieke elementen, zoals bannerafbeeldingen, bannertitels en platte tekst, en met primaire en secundaire kleuren. Deze verbeteringen zorgen voor consistentie tussen merken, vereenvoudigen het instappen van gebruikers en bouwen vertrouwen.

![ het Brandmerken UI ](/help/assets/assets/content-hub-ui-branding.png)

**Openbare verbinding delend**

Content Hub ondersteunt nu het genereren van deelbare koppelingen, zodat externe gebruikers zonder toegang tot de toepassing metagegevens van middelen kunnen bekijken of elementen kunnen downloaden.

![ het Brandmerken UI ](/help/assets/assets/public-and-private-link.png)

**het bestuur van Inzamelingen**

Met Content Hub kunt u nu de toegang tot verzamelingen tijdens het maken beheren, zodat alleen geautoriseerde gebruikers gegroepeerde elementen kunnen weergeven of beheren. Het zorgt voor betere veiligheid, betere samenwerking, georganiseerd activabeheer, en vereenvoudigd bestuur.

![ het bestuur van Inzamelingen ](/help/assets/assets/collection-permissions.png)

>[!NOTE]
>
>Beheer van verzamelingen is een beperkte beschikbaarheid. U kunt het toegelaten krijgen door een steunkaartje te creëren.

**Download veelvoudige activa als ZIP**

Met Content Hub kunt u nu ook de geselecteerde elementen en de bijbehorende uitvoeringen downloaden in een ZIP-bestand en niet als afzonderlijke bestanden die het bestandsbeheer voor u vereenvoudigen.

**Dynamische vertoningen van Media in Content Hub**

Open al uw dynamische vooraf ingestelde vertoningen van Media en slimme gewassen voor download, direct van binnen de Gebruikersinterface van Content Hub.

&#x200B; ![ Dynamische vertoningen van Media ](/help/assets/assets/dm-renditions-content-hub.png)

### Nieuwe functies in dynamische media {#new-features-dynamic-media}

**Dynamische integratie van Media inheemse met de &#x200B; van AJO B2C**

Native integratie van Experience Manager (AEM) Dynamic Media met Journey Optimizer (AJO) B2C, waardoor marketers AEM Dynamic Media-elementen (uitvoering en DM-sjabloon) gemakkelijk kunnen insluiten in AJO-inhoud en real-time updates en hyperpersoonlijke ervaringen via kanalen kunnen bieden.

&#x200B; ![ Dynamische vertoningen van Media ](/help/assets/assets/dm-ajo-integration.png)

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Functies vóór de release

* [ Universele Redacteur - de Fragmenten van de Vorm ](/help/edge/docs/forms/universal-editor/creating-form-fragments.md): De Universele Redacteur staat u nu toe om de Fragmenten van de Vorm voor Adaptieve Forms tot stand te brengen en opnieuw te gebruiken. Deze fragmenten zijn herbruikbare formuliersecties (bijvoorbeeld contactgegevens, toestemmingsvelden) die één keer kunnen worden gemaakt en op meerdere formulieren kunnen worden toegepast. Met deze functie stroomlijnt u het maken van formulieren, zorgt u voor consistentie en verbetert u de efficiëntie van het ontwerpen.

* [ de Bibliotheek van het Document van SharePoint - sparen Bijlagen met Oorspronkelijke Filenames ](/help/forms/connect-forms-to-sharepoint-document-library.md#connect-an-adaptive-form-to-microsoft-sharepoint-document-library): U hebt nu de optie om vormgehechtheid te bewaren gebruikend hun originele filenames wanneer het opslaan van hen in een Bibliotheek van het Document van SharePoint. Deze verbetering vereenvoudigt de identificatie en het beheer van geüploade bestanden.

* **Redacteur van de Regel**:
   * [ Binaire Voorwaarde met de Gebeurtenis van de Klik in &quot;wanneer&quot;Clausule ](/help/forms/rule-editor-core-components-events-operators.md#available-operator-types-and-events-in-rule-editor): De Redacteur van de Regel staat nu toe combinerend een gebeurtenis van de knoopklik (_wordt geklikt_) met andere voorwaarden binnen de &quot;wanneer&quot;clausule. Dit laat nauwkeurigere controle over regeluitvoering toe die op gebruikersinteractie en andere factoren wordt gebaseerd. Opmerking: wanneer u meerdere voorwaarden gebruikt, moet de gebeurtenis click de eerste weergegeven voorwaarde zijn.
   * [ de Voorwaarden van de Bevestiging voor Gebieden en Comités ](/help/forms/rule-editor-core-components-usecases.md): De Redacteur van de Regel omvat nu _IsValid_ en _IsNotValid_ voorwaarden. Hiermee kunt u de validatiestatus controleren van specifieke velden of volledige deelvensters (zoals lay-outs zoals Horizontale tabbladen, Verticale tabbladen, Accordeons en Wizards), waardoor de navigatie en gebruikerservaring van formulieren op basis van validatieresultaten wordt verbeterd.
* [ Verbeterd Beheer van het Toepassingsgebied voor de Lijsten van SharePoint ](/help/forms/connect-forms-to-sharepoint-list.md): De plaatsen van SharePoint steunen nu alle beheerde wegen, bijvoorbeeld, /sites en /teams. Deze verbetering maakt een bredere integratie mogelijk in verschillende SharePoint-sitestructuren, waardoor u flexibeler kunt werken met organisatorische inhoud.
* [ Steun voor het Opslaan van Document van Verslag aan de Lijst van SharePoint ](/help/forms/generate-document-of-record-core-components.md#bind-adaptive-form-components-with-template-fields): Forms die gebruikend een op lijst-Gebaseerd Model van de Gegevens van de Vorm van SharePoint (FDM) wordt gecreeerd kan het Document van Verslag (DoR) aan de Lijsten van SharePoint nu opslaan door het Document van het het gebiedsbezit van de Verwijzing van de Bind van het Verslag te vormen. Dankzij deze verbetering kunnen ondersteunde formuliergegevens en -documenten naadloos worden geïntegreerd met SharePoint-opslag.

### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties en om de ontwikkeling ervan vorm te geven.

Deze release bevat een overzicht van de innovaties die in de huidige release worden geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie &lbrace;de documentatie van het Programma van de Vroege Toegang van AEM Forms [&#128279;](/help/forms/early-access-ea-features.md).

#### Adobe Experience Platform (AEP) Integratie met Forms

De integratiemogelijkheden tussen Forms en AEP zijn nu beschikbaar voor beginnende gebruikers.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

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

**Java 11 runtime** is nu afgekeurd, en de meeste milieu&#39;s zijn reeds bevorderd aan uitvoerigere **runtime Java 21**.

Als uw milieu niet wegens niet gesteunde gebiedsdelen (zie [ runtime van Java 21 vereisten ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)) kon worden bevorderd, zou u een e-mail van Adobe met specifieke volgende stappen moeten ontvangen. Gelieve te verzekeren alle vereiste updates tegen **28 augustus, 2025** worden voltooid, zodat kan uw milieu zonder verstoring worden bevorderd.

Opmerking: de runtimeversie staat los van de build-versie van uw code. We raden u aan om samen te werken met Java 21, maar Java 11-builds worden voorlopig nog wel ondersteund. In de toekomst wordt een afzonderlijke aankondiging voor het vervangen van Java 11-builds gedeeld.

### Handhaving van het configuratiebeleid van AEM Java Logs {#logconfig-policy}

Zoals vermeld in de opmerkingen bij de release van april, moeten AEM Java-logboeken een standaardindeling gebruiken voor betrouwbare bewaking in alle klantomgevingen. Aangepaste logboekconfiguraties, zoals wijzigingen in de logbestandsindeling, uitvoerbestanden of standaardlogniveaus, worden niet meer ondersteund. De logbestanden moeten naar de standaardbestanden worden geleid en de standaardlogniveaus voor AEM-productcode moeten worden behouden. Zie volledige details in het [ Registreren artikel ](/help/implementing/developing/introduction/logging.md#configuration-loggers).

Beginnend in **eind Augustus**, zullen om het even welke niet gestaafde overrides van het douaneregistreren worden genegeerd. Gebaseerd op onze analyse, zullen de meeste klanten niet beïnvloed worden en Adobe zal direct om het even welke klanten contacteren waarvan huidige configuratie kan worden beïnvloed.

Gelieve te herzien en bij te werken om het even welke stroomafwaartse processen die zich op het gedrag van het douaneregistreren baseren. Bijvoorbeeld:

* Als uw logboek het door:sturen systeem een formaat van het douanelogboek verwacht, kunt u uw innameregels moeten aanpassen.
* Als u eerder logboekbreedheid hebt verminderd door logboekniveaus te veranderen, gelieve te merken dat het terugkeren aan standaardniveaus logboekvolume kan verhogen.

### Standaard leegmaken van oudere versies en controlelogboeken {#mt-defaults}

Momenteel, hebben de inhoudsversies en de controlelogboeken hun bijbehorende *taken van het zuiveringsonderhoud* gehandicapt door gebrek en zo wordt geen gegeven verwijderd tenzij uitdrukkelijk gevormd via hun respectieve eigenschappen OSGi.

Nochtans, om bewaarplaatsprestaties te optimaliseren, die in **eind juni 2025** beginnen, zal het zuiveren door gebrek worden toegelaten, die deze richtlijnen volgen:

#### Inhoudversies {#mt-content}

* **Nieuwe milieu&#39;s** (gecreeerd na een aanstaande datum (die later worden meegedeeld)
   * Versies ouder dan **30 dagen** zullen periodiek worden geschrapt.
   * De meest recente vijf versies in de afgelopen 30 dagen blijven behouden, samen met de meest recente versie en de huidige versie, ongeacht hun leeftijd.

* **Bestaande milieu&#39;s** (gecreeerd vóór deze aanstaande datum):
   * Versies ouder dan **7 jaar** zullen periodiek worden geschrapt.
   * Alle versies in de afgelopen 7 jaar blijven behouden.
   * Deze hoge standaarddrempel voorkomt dat recente gegevens onbedoeld worden verwijderd. Het wordt echter aanbevolen lagere waarden te configureren om de prestaties van de opslagplaats te optimaliseren.

* U kunt deze gebreken door OSGi configuratieoverschrijvingen wijzigen.

#### Controlelogboek {#mt-auditlogs}

* **Nieuwe milieu&#39;s** (gecreeerd na een aanstaande datum, die afzonderlijk zal worden meegedeeld):
   * De replicatie, DAM, en de logboeken van de paginacontrole ouder dan **7 dagen** zullen periodiek worden geschrapt.
   * Alle gebeurtenissen worden standaard geregistreerd.

* **Bestaande milieu&#39;s** (gecreeerd vóór deze aanstaande datum):
   * De replicatie, DAM, en de logboeken van de paginacontrole ouder dan **7 jaar** zullen periodiek worden geschrapt.
   * Alle gebeurtenissen worden standaard geregistreerd.
   * Deze hoge standaarddrempel voorkomt dat recente gegevens onbedoeld worden verwijderd. Het wordt echter aanbevolen lagere waarden te configureren om de prestaties van de opslagplaats te optimaliseren.

* U kunt deze gebreken door OSGi configuratieoverschrijvingen wijzigen.

Voor meer details, zie het [ artikel van de Taken van het Onderhoud ](/help/operations/maintenance.md#default).

### Edge Computing (Alpha-programma) {#edge-computing}

Met Edge Computing kunt u JavaScript uitvoeren op de CDN-laag, waardoor de gegevensverwerking dichter bij de eindgebruiker komt te staan. Dit vermindert latentie en maakt responsieve, dynamische ervaringen aan de rand mogelijk.

Vaak voorkomende gevallen van gebruik zijn:

* Gebruikers verifiëren met een identiteitsprovider voordat toegang tot inhoud wordt verleend
* Inhoud aanpassen op basis van geolocatie, apparaattype of gebruikerskenmerken
* Handelend als middleware tussen CDN en uw oorsprong
* Reacties van externe API&#39;s (en wellicht meerdere API&#39;s) opnieuw opmaken voordat deze naar de browser worden verzonden
* Door de server gerenderde HTML aan de rand samenstellen en bedienen met inhoud die vanuit verschillende achtergronden is geplaatst

We hebben een beperkt aantal mogelijkheden voor AEM Publish Delivery- of Edge Delivery Services-projecten voor live productiesites. Als u in het deelnemen geinteresseerd bent of meer wilt leren, gelieve [ aemcs-edgecompute-feedback@adobe.com ](mailto:aemcs-edgecompute-feedback@adobe.com) met een korte beschrijving van uw gebruiksgeval te e-mailen.

### CDN-configuratie voor Edge Delivery Services (Beta-programma) {#cdn-eds-beta}

Adobe-Beheerde CDN biedt flexibele configuratieopties aan, zoals die in het [ wordt beschreven Config Artikel van de Pijpleiding ](/help/operations/config-pipeline.md#configurations).

Nu in een bèta, stel een config pijpleiding voor eigenschappen met inbegrip van CDN oorsprongselectors, reactie en verzoektransformaties, en meer op. Gelieve te bereiken uit aan [ aemcs-cdn-config-adopter@adobe.com ](mailto:aemcs-cdn-config-adopter@adobe.com) met de details van uw gebruiksgeval.

### AEM Log-Forwarding aan Meer Doelen (het Programma van Beta) {#log-forwarding-beta}

Hoewel de logboeken van Cloud Manager kunnen worden gedownload, vinden vele organisaties het nuttig om die logboeken aan een aangewezen registrerenbestemming te stromen. AEM biedt al ondersteuning voor het doorsturen van AEM- en CDN-logbestanden naar Azure Blob Storage, Datadog, HTTPS, Elasticsearch (en OpenSearch) en Splunk. Deze eigenschap wordt gevormd op een zelf-servermanier, en opgesteld gebruikend de Pijpleiding Config.

Nu in bèta kunt u AEM-logs doorsturen naar Amazon S3, Sumo Logic en uw eigen New Relic-account (niet naar het door Adobe verschafte account). Merk op dat de logboeken van AEM (met inbegrip van Apache/Dispatcher) voor deze registrerenbestemmingen, maar niet CDN- logboeken worden gesteund. E-mail [ aemcs-logforwarding-beta@adobe.com ](mailto:aemcs-logforwarding-beta@adobe.com) voor toegang.

Leer meer in het [ logboek door:sturen documentatie ](/help/implementing/developing/introduction/log-forwarding.md).

## [!DNL Experience Manager] Hulplijnen {#guides}

U kunt een volledige lijst van nieuwe en verbeterde eigenschappen van de recentste versie van Adobe Experience Manager Guides [ hier ](https://experienceleague.adobe.com/nl/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.

## Universele editor {#universal-editor}

U kunt een volledige lijst van Universele versies van de Redacteur [ hier ](/help/release-notes/universal-editor/current.md) vinden.

## Variaties genereren {#generate-variations}

U kunt een volledige lijst van Generate de versies van Variaties [ hier ](/help/generative-ai/release-notes-generate-variations.md) vinden.

## Opmerkingen bij de release van Experience Cloud {#experience-cloud}

U kunt informatie over versies van andere toepassingen van Experience Cloud [ hier ](https://experienceleague.adobe.com/nl/docs/release-notes/experience-cloud/current) vinden.
