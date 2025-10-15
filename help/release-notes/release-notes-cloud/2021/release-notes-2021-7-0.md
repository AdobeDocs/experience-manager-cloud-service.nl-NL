---
title: Nota's van de versie voor 2021.7.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2021.7.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 848f6a29-2e0f-4976-8ed7-6b7f69408c1b
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Hier kunt u navigeren om notities van eerdere versies vrij te geven, bijvoorbeeld voor de versies in 2020 en 2021.

>[!NOTE]
>
>Zie [&#x200B; Recente Updates van de Documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release (2021.7.0) is 29 juli 2021.
De volgende release (2021.8.0) vindt plaats op 26 augustus 2021.

## Video vrijgeven {#release-video}

Heb een blik bij de [&#x200B; juli 2021 video van het Overzicht van de Versie van de Versie &#x200B;](https://video.tv.adobe.com/v/335580) voor een samenvatting van de toegevoegde eigenschappen.

## Experience Manager Foundation as a Cloud Service {#foundation}

### Wat is er nieuw? {#what-is-new-foundation}

* Meer flexibele Dispatcher-configuratie: projecten kunnen gemakkelijker worden georganiseerd. U kunt nu bijvoorbeeld meerdere herschrijfregelbestanden opnemen die de sitestructuur weerspiegelen. [&#x200B; Leer over &#x200B;](/help/implementing/dispatcher/disp-overview.md#validation-debug) deze flexibele wijze, met inbegrip van hoe te om uw configuratie van Dispatcher te structureren zodat kunt u uit het voordeel halen.
* De boomreplicatie UI onder het &quot;Distribute&quot;lusje van de replicatieagent zou moeten worden beschouwd als afgekeurd en werd verwijderd na 30 September, 2021. [&#x200B; leer over &#x200B;](/help/operations/replication.md#tree-activation) alternatieve replicatiestrategieën.
* Bundel `org.apache.sling.datasource-1.0.4.jar` voor de ondersteuning van SQL-gegevensbronnen is verwijderd, omdat deze verouderde functionaliteit heeft en niet door klanten wordt gebruikt.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Met de functie voor automatisering van inhoud kan [!DNL Experience Manager Assets] de API&#39;s van [!DNL Adobe Creative Cloud] gebruiken om de productie van elementen op schaal te automatiseren. Het verbetert de snelheid van de inhoud door de benodigde tijd en herhalingen aanzienlijk te verminderen om variaties van hetzelfde element te maken. Voor deze functionaliteit is geen programmering vereist en werken vanuit de DAM. Zie [&#x200B; variaties van activa produceren gebruikend de integratie van het Creative Cloud &#x200B;](/help/assets/cc-api-integration.md).

* [!DNL Experience Manager Assets] bevat de [!DNL Document Cloud] PDF Viewer om een voorvertoning van PDF-documenten te bekijken. Met deze functie kunnen gebruikers PDF-bestanden met meerdere pagina&#39;s voorvertonen zonder dat er bestanden hoeven te worden verwerkt of geconverteerd. Deze functie verbetert de pariteit met [!DNL Experience Manager] 6.5. De besturingselementen die beschikbaar zijn in de viewer zijn onder andere zoomen, naar pagina&#39;s navigeren, besturingselementen loskoppelen en op volledig scherm weergeven. Gebruikers kunnen ook een voorvertoning weergeven van pagina&#39;s en bladwijzers. Opmerkingen over het bestand zelf worden ondersteund. Opmerkingen en annotaties over de inhoud in het PDF-bestand zijn gepland voor een toekomstige release.

  ![&#x200B; PDF dossiers van de Voorproef in [!DNL Experience Manager] gebruikend de Kijker van de PDF &#x200B;](/help/assets/assets/preview-pdf-file-viewer.png)

* De functie voor het delen van koppelingen gebruikt asynchrone downloads die de downloadsnelheid verhogen. Voor meer informatie, zie [&#x200B; Gedeelde activa van de Download gebruikend verbinding het delen &#x200B;](/help/assets/download-assets-from-aem.md#link-share-download).

  ![&#x200B; Inbox van de Download &#x200B;](/help/assets/assets/download-inbox.png)

* De weergave-instellingen worden verbeterd zodat gebruikers een standaardweergave en een standaardsorteerparameter kunnen kiezen.

  ![&#x200B; plaats standaardmening in [!UICONTROL View Settings]](/help/assets/assets/view-settings-for-defaults.png)

* Gebruikers kunnen de mappen zoeken en filteren op basis van voorspelden van eigenschappen.

  ![&#x200B; de onderzoeksomslagen van de Filter gebruikend onderzoek predikaten &#x200B;](/help/assets/assets/search-folders-via-predicates.png)

### Nieuwe functies die beschikbaar zijn in het [!DNL Assets] prereleasekanaal {#assets-prerelease-features}

<!-- TBD: Not sure about GA of these enh. Shall check with the team.

* A user experience enhancements displays the number of assets present in a folder. For more than 1000 assets in a folder, [!DNL Assets] displays 1000+.

  ![Number of assets in a folder are displayed on the interface](/help/assets/assets/browse-folder-number-of-assets.png)

* You can directly apply a metadata schemas to a folder in its [!UICONTROL Properties].

  ![Add metadata schema from folder properties](/help/assets/assets/metadata-schema-folder-properties.png)
-->

* Wanneer u digitale elementen deelt als een koppeling, kunnen gebruikers de URL naar het klembord kopiëren. Dankzij deze verbetering kunt u elementen sneller en handiger delen.

### Buizen gecorrigeerd in [!DNL Assets] {#assets-bugs-fixed}

De API `com.day.cq.dam.api.collection.SmartCollection` is niet beschikbaar in [!DNL Experience Manager] as a [!DNL Cloud Service] . (CQ-4326322)

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* U kunt de dienst van de Automatede form conversion aan [&#x200B; nu gebruiken zet PDF forms in het Frans, Duits, en Spaans taal &#x200B;](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=nl-NL&#language-specific-meta-model) in aanpassingsvormen om.
* Er is een apart deelvenster toegevoegd aan de sjablooneditor om fouten weer te geven met betrekking tot adaptieve formuliercomponenten. Hiermee kunt u alle adaptieve formulierfouten op één locatie consolideren en de resolutietijd verminderen.

### Nieuwe functies beschikbaar in [!DNL Forms] prereleasekanaal {#beta-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [&#x200B; Communicatie APIs &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html?lang=nl-NL) hulp u XDP malplaatjes en de gegevens van XML combineert om drukdocumenten in diverse formaten te produceren. Met de service kunt u documenten in synchrone modus genereren. Met de API&#39;s kunt u toepassingen maken waarmee u:
   * Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   * Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   * Afdruk-PDF-bestanden genereren op basis van een XFA-formulier met PDF en Adobe Acrobat-formulier.

* **Variabele die Extern van Gegevens**: U kunt gegevens van AEM variabelen van het Werkschema op een extern opslagsysteem bewaren door uw organisatie wordt geleid.

* **op acroform-Gebaseerd Document van Verslag**: U kunt ook [&#x200B; de Vorm van Adobe Acrobat PDF (Acroform PDF) &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=nl-NL) als malplaatje voor Document van Verslag naast op XFA-Gebaseerd vormmalplaatje gebruiken.

* **Microsoft® Azure schakelaar van de gegevensopslag**: U kunt [&#x200B; het Model van de Gegevens van de Vorm aan Microsoft® Azure Opslag &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage.html?lang=nl-NL) nu verbinden. Hiermee kunt u adaptieve formuliergegevens ophalen en opslaan naar Microsoft® Azure Storage als een BLOB.

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* CIF Core Components v2
   * Vereenvoudigde en verbeterde configuraties voor PDP/PLP URL en SEO
   * Visuele indicator voor gefaseerde productgegevens op auteurswijze voor betere zichtbaarheid van aanstaande veranderingen
   * Nieuwe sitemapcomponent voor inhoud- en handelspagina&#39;s

* Steun voor [&#x200B; het ProductAanbeveling van Sensei van Adobe Commerce, aangedreven door Adobe Sensei &#x200B;](https://business.adobe.com/nl/products/magento/product-recommendations.html) in AEM Storefront gebruikend vooraf bepaalde of ter plekke gecreeerde aanbevelingen

## [!DNL Experience Manager Screens] als een [!DNL Cloud Service] {#screens}

### Opgeloste problemen {#bug-fixes-screens}

* De instellingen van de inhoudsprovider worden nu gevalideerd tijdens het maken of bijwerken.

* Alle weergaveweergaven hebben mappenkolom.

* U kunt de Screens Content Structure uitbreiden.

* In `bulk-offline-update-service` ontbreken alle machtigingen voor bepaalde omgevingen.

* De bijgewerkte koppeling Help die overeenkomt met de nieuwe documentatie van de schermwolk.

* De toewijzing van afspeellijsten ongedaan maken en het verwijderen van afspeellijsten met toegewezen spelers niet toestaan, werkt nu.

* De speler downloadt nu Assets wanneer de cache ALLE wordt gewist.

* Herhaal nu plannend werken, als de *Tijd van het Eind* voor de volgende dag wordt geplaatst.

* `Back&Forward` werkt nu in de as a Cloud Service gebruikersinterface van Screens.

* Labels met dezelfde naam maar verschillende naamruimten kunnen niet eerder worden gemaakt.

## XML Documentation for Experience Manager as a Cloud Service {#xml-documentation}

### Nieuwe functies {#what-is-new-xml-documentation}

XML Documentation for Experience Manager as a Cloud Service is over het algemeen beschikbaar. Klanten van as a Cloud Service Experience Managers kunnen hiermee een XML Documentation-add-on aanschaffen om technische inhoud te importeren, maken, beheren en leveren via meerdere kanalen, waaronder Experience Manager Sites.

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.7.0 beschreven.

### Releasedatum {#release-cm-july}

De Releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.7.0 is 15 juli 2021.
De volgende release is gepland voor 12 augustus 2021.

### Wat is er nieuw? {#what-is-new-cm-july}

* De klanten kunnen Azul 8 en 11 JDKs voor hun Cloud Manager nu gebruiken bouwt processen en kunnen of selecteren om één van deze JDKs voor toolketens-compatibele Maven plugins *of* de volledige Maven procesuitvoering te gebruiken.

* Uitgaande uitgang IP wordt nu het programma geopend in het dossier van het bouwstijlstaplogboek.

* De milieu&#39;s van het stadium en van de Productie die oude versies van AEM in werking stellen melden nu een status van **Beschikbare Update**.

* Het maximum aantal ondersteunde SSL-certificaten is gestegen tot 20 per programma.

* Het maximumaantal domeinen dat kan worden gevormd is verhoogd tot 500 per milieu.

* De **beheert knoop van het Git** is hernoemd aan **Info van het Git van de Toegang** en de dialoogdoos is visueel verfrist.

* De versie van het AEM Project Archetype dat door Cloud Manager wordt gebruikt, is bijgewerkt naar versie 28.

### Opgeloste problemen {#bug-fixes-cm-july}

* In sommige situaties, was de Voorproef geen beschikbare optie toen het binden van een IP lijst van gewenste personen aan een milieu.

* Wanneer u handmatig naar de pagina met uitvoeringsdetails voor een niet-bestaande uitvoering navigeerde, werd geen fout weergegeven, alleen een eindeloos laadscherm.

* Het foutbericht dat wordt weergegeven wanneer het maximumaantal SSL-certificaten is bereikt, is niet nuttig.

* In sommige omstandigheden, zou er een discrepantie in de versieversie kunnen zijn die in de pijpleidingskaart op de **1&rbrace; pagina van het Overzicht &lbrace;wordt getoond.**

* De wizard Programma toevoegen heeft onjuist aangegeven dat de naam na het maken niet meer kan worden gewijzigd.

### Bekende problemen {#known-issues-cm-july}

Klanten die overstappen op de Azul JDK&#39;s moeten weten dat niet alle bestaande toepassingen zonder fout compileren op de Azul JDK. De Adobe adviseert dat u plaatselijk alvorens omschakeling test.

## Cloud Acceleration Manager {#cam}

### Releasedatum {#release-date-july-cam}

De releasedatum voor Cloud Acceleration Manager is 15 juli 2021.

### Nieuwe functies {#what-is-new-cam}

Cloud Acceleration Manager is een cloudgebaseerde toepassing die is ontworpen om uw IT-teams te begeleiden tijdens de transitietraject, van de planning tot het live gaan van de Cloud Service. Stel uw team in voor een geslaagde migratie met aanbevolen Adobe procedures, tips, documentatie en tools voor elke fase van de reis naar AEM als Cloud Service. Leer meer [&#x200B; hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=nl-NL).

>[!NOTE]
>
> Controle uit deze [&#x200B; de demo video van Cloud Acceleration Manager &#x200B;](https://video.tv.adobe.com/v/335547).
