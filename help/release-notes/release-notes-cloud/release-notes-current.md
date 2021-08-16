---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 2f08b1487c1a7fc7b94678e78f8fd72054ff51cb
workflow-type: tm+mt
source-wordcount: '1630'
ht-degree: 0%

---


# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] als Cloud Service weergegeven.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies weer te geven. bijvoorbeeld voor die in 2020, 2021, enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release (2021.7.0) is 29 juli 2021.
De volgende release (2021.8.0) vindt plaats op 26 augustus 2021.

## Video vrijgeven {#release-video}

Bekijk de video [Juli 2021 van de Versie Overzicht](https://video.tv.adobe.com/v/335580) voor een samenvatting van de toegevoegde eigenschappen.

## [!DNL Experience Manager] als  [!DNL Cloud Service] stichting {#foundation}

### Wat is er nieuw? {#what-is-new-foundation}

* Meer flexibele configuratie van de verzender: Projecten kunnen gemakkelijker worden georganiseerd. U kunt nu bijvoorbeeld meerdere herschrijfregelbestanden opnemen die de sitestructuur weerspiegelen. [Leer ](/help/implementing/dispatcher/disp-overview.md#validation-debug) over deze flexibele wijze, met inbegrip van hoe te om uw dispatcherconfiguratie te structureren om uit het voordeel te halen.
* De boomreplicatie UI onder het &quot;Distribute&quot;lusje van de replicatieagent zou moeten worden beschouwd als afgekeurd en is gepland om na 30 september worden verwijderd. [Leer ](/help/operations/replication.md#tree-activation) over alternatieve replicatiestrategieën.
* Bundel `org.apache.sling.datasource-1.0.4.jar` voor Sling-gegevensbronondersteuning is verwijderd, omdat deze verouderde functionaliteit heeft en niet door klanten wordt gebruikt.

## [!DNL Experience Manager Assets] als  [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Met de functionaliteit voor automatisering van inhoud kan [!DNL Experience Manager Assets] de API&#39;s van [!DNL Adobe Creative Cloud] gebruiken om de productie van elementen op schaal te automatiseren. Het verbetert de snelheid van de inhoud door de benodigde tijd en herhalingen aanzienlijk te verminderen om variaties van hetzelfde element te maken. Voor deze functionaliteit is geen programmering vereist en werken vanuit de DAM. Zie [Variaties van elementen genereren met behulp van Creative Cloud-integratie](/help/assets/cc-api-integration.md).

* [!DNL Experience Manager Assets] bevat de  [!DNL Document Cloud] PDF Viewer om een voorvertoning van PDF-documenten te bekijken. Met deze functie kunnen gebruikers PDF-bestanden met meerdere pagina&#39;s voorvertonen zonder dat er bestanden hoeven te worden verwerkt of geconverteerd. Deze functie verbetert de pariteit met [!DNL Experience Manager] 6.5. De besturingselementen die beschikbaar zijn in de viewer zijn onder andere zoomen, naar pagina&#39;s navigeren, besturingselementen loskoppelen en op volledig scherm weergeven. Gebruikers kunnen ook een voorvertoning weergeven van pagina&#39;s en bladwijzers. Opmerkingen over het bestand zelf worden ondersteund en opmerkingen en annotaties over inhoud in het PDF-bestand worden toegevoegd in een toekomstige versie.

   ![Voorbeeld van PDF-bestanden weergeven in  [!DNL Experience Manager] PDF Viewer](/help/assets/assets/preview-pdf-file-viewer.png)

* De downloadfunctionaliteit van Linkshare gebruikt asynchrone downloads die de downloadsnelheid verhogen. Zie [Gedeelde elementen downloaden via koppelingen delen](/help/assets/download-assets-from-aem.md#link-share-download).

   ![Postvak IN downloaden](/help/assets/assets/download-inbox.png)

* De weergave-instellingen worden verbeterd zodat gebruikers een standaardweergave en een standaardsorteerparameter kunnen kiezen.

   ![Standaardweergave instellen in  [!UICONTROL View Settings]](/help/assets/assets/view-settings-for-defaults.png)

* Gebruikers kunnen de mappen zoeken en filteren op basis van voorspelden van eigenschappen.

   ![Zoekmappen filteren met behulp van voorvertoningen zoeken](/help/assets/assets/search-folders-via-predicates.png)

### Nieuwe functies beschikbaar in het prerelease-kanaal [!DNL Assets] {#assets-prerelease-features}

<!-- TBD: Not sure about GA of these enh. Shall check with the team.

* A user experience enhancements displays the number of assets present in a folder. For more than 1000 assets in a folder, [!DNL Assets] displays 1000+.

  ![Number of assets in a folder are displayed on the interface](/help/assets/assets/browse-folder-number-of-assets.png)

* You can directly apply a metadata schemas to a folder in its [!UICONTROL Properties].

  ![Add metadata schema from folder properties](/help/assets/assets/metadata-schema-folder-properties.png)
-->

* Wanneer u digitale elementen deelt als een koppeling, kunnen gebruikers de URL naar het klembord kopiëren. Dankzij deze verbetering kunt u elementen sneller en gemakkelijker delen.

### Buizen vastgesteld in [!DNL Assets] {#assets-bugs-fixed}

De API `com.day.cq.dam.api.collection.SmartCollection` is niet beschikbaar in [!DNL Experience Manager] als [!DNL Cloud Service]. (CQ-4326322)

## [!DNL Experience Manager Forms] als  [!DNL Cloud Service] {#forms}

### Nieuw in [!DNL Forms] {#what-is-new-forms}

* U kunt nu de service Automatede form conversion gebruiken om PDF forms in het Frans, Duits en Spaans ](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) om te zetten in aangepaste formulieren.[
* Een apart deelvenster toegevoegd aan de sjablooneditor om fouten weer te geven die betrekking hebben op adaptieve formuliercomponenten. Hiermee kunt u alle adaptieve formulierfouten op één locatie consolideren en de resolutietijd verminderen.

### Nieuwe functies beschikbaar in het prerelease-kanaal [!DNL Forms] {#beta-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**:  [Communicatie-](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html) APIschappen combineren XDP-sjablonen en XML-gegevens om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone modus. Met de API&#39;s kunt u toepassingen maken waarmee u:
   * Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   * Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   * Genereer PDF-bestanden voor afdrukken vanuit een XFA-formulier, PDF- en Adobe Acrobat-formulier.

* **Variabele-gegevensexternalizer**: U kunt gegevens van AEM workflowvariabelen opslaan op een extern opslagsysteem dat door uw organisatie wordt beheerd.

* **Op acroform gebaseerd Document of Record**: U kunt ook het Adobe Acrobat Form PDF (Acroform PDF)  [gebruiken ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html) als sjabloon voor Document of Record, naast een XFA-formuliersjabloon.

* **Microsoft Azure Data Store-connector**: U kunt nu het Model van de Gegevens van het Vorm met de Opslag [ van Microsoft Azure ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html)verbinden. Hiermee kunt u adaptieve formuliergegevens ophalen en opslaan naar Microsoft Azure Storage als een BLOB.

## CIF-invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* CIF Core Components v2
   * Vereenvoudigde en verbeterde configuraties voor PDP/PLP URL en SEO
   * Visuele indicator voor gefaseerde productgegevens op auteurswijze voor betere zichtbaarheid van aanstaande veranderingen
   * Nieuwe sitemapcomponent voor inhoud- en handelspagina&#39;s

* Ondersteuning voor [Adobe Commerce Sensei Product Recommendation, aangedreven door Adobe Sensei](https://business.adobe.com/products/magento/product-recommendations.html) in AEM Storefront met behulp van vooraf gedefinieerde of ter plekke gemaakte aanbevelingen

## [!DNL Experience Manager Screens] als  [!DNL Cloud Service] {#screens}

### Opgeloste problemen {#bug-fixes-screens}

* De instellingen van de inhoudsprovider worden nu gevalideerd tijdens het maken of bijwerken.

* Alle weergaven hebben mappenkolom.

* U kunt de structuur van de Inhoud van het scherm uitbreiden.

* `bulk-offline-update-service` ontbrak alle machtigingen voor bepaalde omgevingen.

* De bijgewerkte koppeling Help die overeenkomt met de nieuwe documentatie van de schermwolk.

* Afspeellijsten niet toewijzen en het verwijderen van afspeellijsten met toegewezen speler(en) niet toestaan, werkt nu.

* De speler downloadt nu elementen opnieuw wanneer de &quot;ALLE&quot;Cache wordt ontruimd.

* Herhaal planning nu werkt als de *Eindtijd* is ingesteld op de volgende dag.

* `Back&Forward` werkt nu in Schermen als Cloud Service UI.

* Labels met dezelfde naam maar verschillende naamruimten kunnen niet eerder worden gemaakt.

## XML-documentatie voor Experience Manager als Cloud Service {#xml-documentation}

### Nieuwe functies {#what-is-new-xml-documentation}

De Documentatie van XML voor Experience Manager als Cloud Service is over het algemeen beschikbaar. Het staat Experience Manager als klanten van de Cloud Service toe om de Documentatie van XML toe te kopen addon om, technische inhoud over veelvoudige kanalen met inbegrip van de Plaatsen van de Experience Manager in te voeren tot stand te brengen, te leiden en te leveren.

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM beschreven als Cloud Service 2021.8.0 en 2021.7.0.

## Releasedatum {#release-date-cm-aug}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.8.0 is 12 augustus 2021.
De volgende release is gepland voor 9 september 2021.

### Wat is er nieuw? {#what-is-new-aug}

* Klanten van Cloud Servicen kunnen nu SLA-rapporten (Service Level Agreement) weergeven in Cloud Manager. Dit zal de komende maanden geleidelijk beschikbaar worden gesteld.
Zie [SLA Rapportering](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html) om meer te leren.

* Het type en de strengheid van de IndexType en `IndexDamAssetLucene` kwaliteitsregels zijn veranderd. Dit zijn nu beide bugs van Blocker *serverity*.

* De nieuwe de kwaliteitsregels van de indexkwaliteit van de eikel zijn geïntroduceerd om asynchrone en tika configuraties te behandelen.

* Verhoog de maximale SSL-certs per programma tot 50.

* Self-service mogelijkheid om gebruikers in staat te stellen meerdere opslagruimten te maken en te beheren via de interface van Cloud Manager.

* SonarQube leest onnodig de gegevens uit de Git-geschiedenis. Op grote codebasis, zou dit tot een onnodige bouwstijlprestaties kunnen leiden.

* Er is nu een API beschikbaar om het Geweven gebiedsdeelheidsgeheime voorgeheugen per pijpleiding ongeldig te maken.

* De versie van het AEM Project Archetype dat wordt gebruikt door Cloud Manager is bijgewerkt naar versie 29.

### Opgeloste problemen {#bug-fixes-aug}

* Update Available status should not be displayed when the latest release is less than the current release.

* De eerste instapweigering mislukte voor nieuwe organisaties met zeer lange namen.

* Af en toe, wanneer een pijpleiding tweemaal om één of andere reden wordt teweeggebracht, resulteert het in één van de uitvoeringen die met *geen status van de pijpleidingsuitvoering kan bijwerken* fout.

### Releasedatum {#release-cm-july}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.7.0 is 15 juli 2021.
De volgende release is gepland voor 12 augustus 2021.

### Wat is er nieuw? {#what-is-new-cm-july}

* Klanten kunnen nu Azul 8 en 11 JDK&#39;s gebruiken voor hun buildprocessen in Cloud Manager en kunnen een van deze JDK&#39;s selecteren voor met toolketens compatibele Maven-plug-ins *of* voor de volledige uitvoering van het Maven-proces.

* Uitgaande uitgang IP zal nu het programma worden geopend het dossier van het bouwstijlstaplogboek.

* Werkgebied- en productieomgevingen met oude versies van AEM rapporteren nu de status **Update Available**.

* Het maximum aantal ondersteunde SSL-certificaten is gestegen tot 20 per programma.

* Het maximumaantal domeinen dat kan worden gevormd is verhoogd tot 500 per milieu.

* De knoppen **Git beheren** hebben een nieuwe naam gekregen in **Git-info benaderen** en het dialoogvenster is visueel vernieuwd.

* De versie van het AEM Project Archetype dat wordt gebruikt door Cloud Manager is bijgewerkt naar versie 28.

### Opgeloste problemen {#bug-fixes-cm-july}

* In sommige situaties, was de Voorproef geen beschikbare optie toen het binden van een IP Lijst van gewenste personen aan een milieu.

* Wanneer u handmatig naar de pagina met uitvoeringsdetails voor een niet-bestaande uitvoering navigeerde, werd geen fout weergegeven, alleen een eindeloos laadscherm.

* Het foutbericht dat wordt weergegeven wanneer het maximumaantal SSL-certificaten is bereikt, is niet nuttig.

* In sommige omstandigheden, zou er een discrepantie in de versieversie kunnen zijn die in de pijpleidingskaart op **Overview** pagina wordt getoond.

* De wizard Programma toevoegen heeft onjuist aangegeven dat de naam na het maken niet kan worden gewijzigd.

### Bekende problemen {#known-issues-cm-july}

Klanten die overstappen op de Azul JDK&#39;s moeten zich ervan bewust zijn dat niet alle bestaande toepassingen zonder fout zullen compileren op Azul JDK. Het wordt hoogst geadviseerd om plaatselijk vóór omschakeling te testen.

## De tool Content Transfer {#content-transfer-tool}

### Releasedatum {#release-date-ctt-latest}

De releasedatum voor Content Transfer Tool v1.5.6 is 11 augustus 2021.

### Opgeloste problemen {#bug-fixes-ctt}

* In sommige gevallen zijn niet alle gebruikers gemigreerd naar de doelinstantie. Om deze moeilijke CTT v1.5.6 te krijgen wordt vereist samen met aem-ethos-hulpmiddelen 1.2.354 of recentere versie op het doel AEM als instantie van de Cloud Service.

* De **Stop Ingestie** knoop werd onbruikbaar gemaakt tijdens opname aan de Publish instantie. Dit is niet nodig omdat er geen stap voor het herstellen van het mongo is tijdens de opname van Publiceren.

* CTT heeft de map `/tmp` niet opgeschoond na een geslaagde extractie. Dit leidde soms tot problemen met schijfruimte.


## Cloud Acceleration Manager {#cam}

### Releasedatum {#release-date-july-cam}

De releasedatum voor Cloud Acceleration Manager is 15 juli 2021.

### Nieuwe functies {#what-is-new-cam}

Cloud Acceleration Manager is een cloudgebaseerde toepassing die ontworpen is om uw IT-teams te begeleiden tijdens de overgang van planning tot live gaan met Cloud Service. Stel uw teams in voor een geslaagde migratie met aanbevolen Adobe-procedures, tips, documentatie en tools om u te helpen bij elke fase van de reis naar AEM als Cloud Service. Meer [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=en).

>[!NOTE]
>
> Schakel deze [demo voor Cloud Acceleration Manager](https://video.tv.adobe.com/v/335547) in.
