---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: bed5a88a545efa4dbfe5c20f4713c0c6adb9847b
workflow-type: tm+mt
source-wordcount: '1541'
ht-degree: 0%

---


# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] als Cloud Service weergegeven.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies weer te geven. bijvoorbeeld voor die in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De Releasedatum voor [!DNL Adobe Experience Manager] als Cloud Service 2021.6.0 is 28 juni 2021.
De volgende release (2021.7.0) vindt plaats op 29 juli 2021.

## Video vrijgeven {#release-video}

Bekijk de video [Juni 2021 van de Versie Overzicht](https://video.tv.adobe.com/v/334296) voor een samenvatting van de toegevoegde eigenschappen.

## XML-documentatie voor AEM als cloudservice {#xml-documentation}

### Wat is er nieuw? {#what-is-new-xml-documentation}

* De Documentatie van XML voor AEM als Cloud Service is nu GA.
* Dit zal bestaande AEM klanten van de Cloud Service toestaan om de Documentatie van XML voor het invoeren van, het creëren van, het beheren van en het leveren van technische inhoud over veelvoudige kanalen met inbegrip van AEM plaatsen aan te kopen

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM beschreven als Cloud Service 2021.6.0 en 2021.5.0.

### Releasedatum {#release-date-june-cm}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.6.0 is 10 juni 2021.
De volgende release is gepland voor 15 juli 2021.

### Wat is er nieuw? {#what-is-new-junecm}

* De Voorproefdienst zal op rolbasis aan alle Programma&#39;s worden opgesteld. Klanten worden in-product op de hoogte gesteld wanneer hun programma is ingeschakeld voor de Voorvertoningsservice. Raadpleeg [Toegang tot voorvertoningsservice](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) voor meer informatie.

* Geweven Gedeelten die tijdens de bouwstijlstap worden gedownload zullen nu in het voorgeheugen ondergebracht tussen pijpleidinguitvoeringen worden. Deze functie wordt de komende weken ingeschakeld voor klanten.

* De naam van het programma kan nu worden bewerkt in het dialoogvenster Programma bewerken.

* De standaardtaknaam die tijdens zowel project verwezenlijking als in het gebrek wordt gebruikt duw bevel via beheert git werkschema is veranderd in `main`.

* De ervaring met het bewerken van programma&#39;s in de gebruikersinterface is vernieuwd.

* De kwaliteitsregel `ImmutableMutableMixCheck` is bijgewerkt om `/oak:index` knopen als onveranderlijk te classificeren.

* De kwaliteitsregels `CQBP-84` en `CQBP-84--dependencies` zijn geconsolideerd in één enkele regel. Als onderdeel van deze consolidatie, identificeert het aftasten van gebiedsdelen nauwkeuriger kwesties in derdegebiedsdelen die aan AEM runtime worden opgesteld.

* Om verwarring te voorkomen, zijn de segmentrijen van de AEM Publish en Publish Dispatcher op de pagina van de Details van het Milieu geconsolideerd.

   ![](/help/onboarding/release-notes-cloud-manager/assets/aem-dispatcher.png)

* Er is een nieuwe code kwaliteitsregel toegevoegd om de structuur van `damAssetLucene` indexen te valideren. Raadpleeg [Custom DAM Asset Lucene Oak Indexes](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check) voor meer informatie.

* De pagina met omgevingsdetails geeft nu meerdere domeinnamen weer voor de services Publiceren en Voorvertonen (al naargelang van toepassing). Raadpleeg [Omgevingsdetails](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) voor meer informatie.

### Opgeloste problemen {#bug-fixes-junecm}

* JCR-knooppuntdefinities die een nieuwe regel bevatten nadat de naam van het hoofdelement niet correct is geparseerd.

* De API voor opslagplaatsen weergeven filtert geen verwijderde opslagplaatsen.

* Er is een onjuist foutbericht weergegeven wanneer een ongeldige waarde voor de planningsstap is opgegeven.

* Soms kan de gebruiker een groene *actieve* status naast een IP Lijst van gewenste personen zien zelfs wanneer die configuratie niet werd opgesteld.

* Sommige programma&#39;s die opeenvolgingen uitgeven zouden in de onmogelijkheid kunnen resulteren om de productiepijplijn tot stand te brengen of uit te geven.

* Sommige programma&#39;s die opeenvolgingen uitgeven zouden in **Overzicht** pagina kunnen resulteren die een misleidend bericht toont om programma opstelling opnieuw uit te voeren.

## [!DNL Experience Manager Assets] als  [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#ga-features-assets}

* Met de functionaliteit voor automatisering van inhoud kan [!DNL Experience Manager Assets] de API&#39;s van [!DNL Adobe Creative Cloud] gebruiken om de productie van elementen op schaal te automatiseren. Het verbetert de snelheid van de inhoud door de benodigde tijd en herhalingen aanzienlijk te verminderen om variaties van hetzelfde element te maken. Voor deze functionaliteit is geen programmering vereist en werken vanuit de DAM. Zie [Variaties van elementen genereren met behulp van Creative Cloud-integratie](/help/assets/cc-api-integration.md).

* [[!DNL Adobe Asset Link] v3.0](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) for  [!DNL Adobe Photoshop],  [!DNL Adobe Illustrator]and  [!DNL Adobe InDesign] and  [[!DNL Adobe Asset Link] v2.0](https://helpx.adobe.com/enterprise/using/adobe-asset-link-for-xd.html) for  [!DNL Adobe XD] is beschikbaar. Het voorziet in:

   * Ondersteuning voor [!DNL Assets Essentials].
   * Mogelijkheid om automatisch verbinding te maken met [!DNL Experience Manager] als [!DNL Cloud Service] of [!DNL Assets Essentials].

* Met het gereedschap [Bulkinspuiting voor element](/help/assets/add-assets.md#asset-bulk-ingestor) kunt u metagegevens toevoegen tijdens een bulkopname.

### Nieuwe functies beschikbaar in het prerelease-kanaal [!DNL Assets] {#beta-features-assets}

* De weergave-instellingen worden verbeterd zodat gebruikers een standaardweergave en een standaardsorteerparameter kunnen kiezen.

   ![Standaardweergave instellen in Weergave-instellingen](/help/assets/assets/view-settings-for-defaults.png)

* De downloadfunctionaliteit van Linkshare gebruikt asynchrone downloads die de downloadsnelheid verhogen.

* Gebruikers kunnen de mappen zoeken en filteren op basis van voorspelden van eigenschappen.

   ![Zoekmappen filteren met behulp van voorvertoningen zoeken](/help/assets/assets/search-folders-via-predicates.png)

* [!DNL Experience Manager Assets] Hiermee sluit u de PDF Viewer in om een voorvertoning van de ondersteunde documentindelingen weer te geven. Het wordt aangedreven door [!DNL Adobe Document Cloud]. Met deze functie kunnen gebruikers PDF- en andere bestanden met meerdere pagina&#39;s voorvertonen zonder dat er sprake is van complexe verwerking. Dit verbetert de eigenschappariteit met [!DNL Experience Manager] 6.5. De besturingselementen in de voorvertoning zijn zoomen, naar pagina&#39;s navigeren, besturingselementen loskoppelen en op volledig scherm weergeven. De geïntegreerde PDF-viewer ondersteunt de bestandsindelingen AI, DOCX, INDD, PDF en PSD. U kunt opmerkingen maken over het element zelf, maar opmerkingen en annotaties in het PDF-bestand worden niet ondersteund.

   ![Voorbeeld van PDF-bestanden weergeven in  [!DNL Experience Manager] PDF Viewer](/help/assets/assets/preview-pdf-file-viewer.png)

* Dankzij de verbeteringen in de gebruikerservaring wordt het aantal elementen in een map weergegeven. [!DNL Assets] geeft 1000+ weer voor meer dan 1000 elementen in een map.

   ![Het aantal elementen in een map wordt weergegeven op de interface](/help/assets/assets/browse-folder-number-of-assets.png)

* U kunt een meta-gegevensschema&#39;s op een omslag in zijn [!UICONTROL Properties] direct toepassen.

   ![Metagegevensschema toevoegen uit mapeigenschappen](/help/assets/assets/metadata-schema-folder-properties.png)

### Buizen vastgesteld in [!DNL Assets] {#bugs-fixed-assets}

* Wanneer u een eigenaar toevoegt aan een submap, voegt [!DNL Assets] ook dezelfde gebruiker toe als een eigenaar van de bovenliggende map. (CQ-4323737)
* Als een gebruiker bij het toevoegen van elementen aan verzamelingen een filter toepast op de zoekopdracht Verzamelingen, kan de gebruiker de Verzamelingen niet weergeven in de lijstweergave. (CQ-4323181)
* Wanneer u naar bestanden en mappen zoekt en de gebruiker een filter toepast en [!UICONTROL Files & Folders] selecteert, worden alleen de bestanden weergegeven, maar niet de map. (CQ-4319543)

## [!DNL Experience Manager Sites] als  [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#ga-features-sites}

* Publiceren naar voorvertoningsniveau wordt nu weergegeven als paginastatus in de gebruikersinterface voor Sitebeheer
* Publiceren op Voorvertoning van niveau surfact nu de URL van de voorvertoning aan het einde van de handeling en doorgaan met de URL in pagina-eigenschappen voor latere referentie

## [!DNL Adobe Experience Manager Forms] als  [!DNL Cloud Service] {#forms}

### Nieuw in [!DNL Forms] {#what-is-new-forms}

* Toegevoegde mogelijkheid om aangepaste kolommen in AEM Inbox te filteren.
* Mogelijkheid toegevoegd om de themaeditor en stijllaag van een aangepaste formuliereditor te gebruiken voor het opmaken van de component captcha.
* Verbeterde snelheid en nauwkeurigheid voor het automatisch detecteren van logische secties in de bron-PDF forms en het converteren van deze secties naar overeenkomstige adaptieve formulierdeelvensters.
* Toegevoegde verplaatsingsactie om een PDF- of XDP-bestand van de ene map naar de andere te verplaatsen.

### Bètafunctie van [!DNL Forms] {#what-is-new-forms-prerelease}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: Via communicatie-API&#39;s kunt u XDP-sjablonen en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone modus. Met de API&#39;s kunt u toepassingen maken waarmee u:
   * Definitieve formulierdocumenten genereren door sjabloonbestanden te vullen met XML-gegevens.
   * Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   * Afdruk-PDF&#39;s genereren op basis van een XFA-formulier, PDF en Adobe Acrobat-formulier (AcroForm).

* **Variabele-gegevensexternalizer**: U kunt gegevens van AEM workflowvariabelen opslaan op een extern opslagsysteem dat door uw organisatie wordt beheerd.

U kunt naar [!DNL formscsbeta@adobe.com] schrijven om u aan te melden voor het bètaprogramma.

### Buizen vastgesteld in [!DNL Forms] {#forms-bugs-fixed}

* Wanneer een veld wordt gevalideerd voordat gegevens worden verzonden naar de service Back-end via het Form Data Model (FDM), slagen validaties erin, maar wordt postvalidatie niet aangeroepen door de service Form Data Model.
* Wanneer u een formulier verzendt met een standaard HTML-uploadveld van een Apple iOS-apparaat, wordt soms de inhoud van het bestand niet verzonden en wordt aan het andere einde een bestand van 0 byte ontvangen. Dit is een bekend probleem in Apple iOS. [FB9117687](https://feedbackassistant.apple.com/feedback/9117687)

## [!DNL Adobe Experience Manager Screens] als  [!DNL Cloud Service] {#screens}

Deze sectie schetst de Nota&#39;s van de Versie voor AEM Screens als Cloud Service.

### Releasedatum {#release-date-june-screens}

De Releasedatum voor AEM Screens als Cloud Service is 24 juni 2021.

### Wat is er nieuw? {#what-is-new-screens-june}

>[!NOTE]
>Zie [AEM Screens als een Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/home.html?lang=en) Guide voor basiskennis die vereist is voor het met succes installeren, configureren en uitvoeren van rasters als een Cloud Service en een koppeling naar gedetailleerde concepten en technische documentatie.

* Bulk Device Registration Management betekent dat het provisioning van enorme hoeveelheden spelerapparaten sneller en efficiënter verloopt.

* Verbeterde zoek- en filteropties voor de inventarisweergaven Apparaat, Weergave en Kanaal.

* Momentopname van apparaatgezondheid bespaart tijd door een kritieke status in één oogopslag te bieden.

* De pagina met objectdetails bevat een overzicht van de meest relevante informatie voor elk object in uw project.

## CIF-invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Nieuwe CIF-product- en categoriereferentiedetypen voor inhoudsfragmenten (incl. product/categoriekiezer (ondersteuning voor gebruikersinterface)
* New Commerce Content Fragment Core Component
* Full-text zoekopdracht ondersteund in AEM achterkant
* Commerce Core Components support Adobe Commerce Sensei Recs data collection
* Verbeterde SEO-vriendelijke URL&#39;s voor categoriepagina&#39;s
* Ondersteuning voor aangepaste HTTP-headers per site/config

## De tool Content Transfer {#content-transfer-tool}

### Releasedatum {#release-date-ctt-latest}

De releasedatum voor Content Transfer Tool v1.5.4 is 28 juni 2021.

### Wat is er nieuw? {#what-is-new-ctt-latest}

* Ondersteuning voor een optionele [pre-copy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en)-stap toegevoegd aan gebruik met CTT. De pre-exemplaarstap kan worden gebruikt om de extractie en inname fasen van de activiteit van de inhoudoverdracht beduidend te versnellen wanneer de bron AEM instantie wordt gevormd om een gegevensbestand van de Opslag van Amazon S3 of van Azure Blob te gebruiken.

* Guardrail toegevoegd aan CTT om te voorkomen dat gebruikers een opname stoppen en mogelijk gegevens beschadigen zodra deze het kritieke punt tijdens de innamefase heeft bereikt.

* De logboeken van de uitwinning maakten beschrijvender om met het oplossen van problemen te helpen.

* Meer beschrijvende statusberichten voor inname zijn toegevoegd in de gebruikersinterface.

### Opgeloste problemen {#bug-fixes-ctt-latest}

* Terwijl het tegenhouden van een opname op de instantie van de Auteur, overlapt UI een eerder gebeëindigde opname op de instantie van de Publish aan `STOPPED` van `FINISHED`. Dit is opgelost.


