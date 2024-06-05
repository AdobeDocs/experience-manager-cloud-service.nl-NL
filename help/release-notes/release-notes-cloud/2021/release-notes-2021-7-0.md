---
title: Opmerkingen bij de release 2021.7.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2021.7.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 848f6a29-2e0f-4976-8ed7-6b7f69408c1b
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Hier kunt u navigeren om notities van eerdere versies vrij te geven, bijvoorbeeld voor de versies in 2020 en 2021.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release (2021.7.0) is 29 juli 2021.
De volgende release (2021.8.0) vindt plaats op 26 augustus 2021.

## Video vrijgeven {#release-video}

Kijk eens naar de [Overzicht release juli 2021](https://video.tv.adobe.com/v/335580) video voor een overzicht van de toegevoegde functies.

## Experience Manager Foundation as a Cloud Service {#foundation}

### Wat is er nieuw? {#what-is-new-foundation}

* Meer flexibele configuratie van de Verzender: De projecten kunnen gemakkelijker worden georganiseerd. U kunt nu bijvoorbeeld meerdere herschrijfregelbestanden opnemen die de sitestructuur weerspiegelen. [Meer informatie over](/help/implementing/dispatcher/disp-overview.md#validation-debug) deze flexibele wijze, met inbegrip van hoe te om uw configuratie van de Verzender te structureren zodat kunt u uit het voordeel halen.
* De boomreplicatie UI onder het &quot;Distribute&quot;lusje van de replicatieagent zou moeten worden beschouwd als afgekeurd en werd verwijderd na 30 September, 2021. [Meer informatie over](/help/operations/replication.md#tree-activation) alternatieve replicatiestrategieën.
* Bundel `org.apache.sling.datasource-1.0.4.jar` voor de steun van de Gegevensbron van Sling is verwijderd, aangezien het verouderde functionaliteit heeft en niet in gebruik door klanten is.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Met de functionaliteit voor automatisering van inhoud kunt u [!DNL Experience Manager Assets] gebruiken [!DNL Adobe Creative Cloud] API&#39;s om de productie van bedrijfsmiddelen op schaal te automatiseren. Het verbetert de snelheid van de inhoud door de benodigde tijd en herhalingen aanzienlijk te verminderen om variaties van hetzelfde element te maken. Voor deze functionaliteit is geen programmering vereist en werken vanuit de DAM. Zie [variaties van elementen genereren met behulp van Creative Cloud-integratie](/help/assets/cc-api-integration.md).

* [!DNL Experience Manager Assets] bevat de [!DNL Document Cloud] PDF Viewer voor een native voorvertoning van PDF-documenten. Met deze functie kunnen gebruikers PDF-bestanden met meerdere pagina&#39;s voorvertonen zonder dat er bestanden hoeven te worden verwerkt of geconverteerd. Met deze functie verbetert u de pariteit met [!DNL Experience Manager] 6.5. De besturingselementen in de viewer zijn onder andere zoomen, naar pagina&#39;s navigeren, besturingselementen loskoppelen en op volledig scherm weergeven. Gebruikers kunnen ook een voorvertoning weergeven van pagina&#39;s en bladwijzers. Opmerkingen over het bestand zelf worden ondersteund. Opmerkingen en annotaties over de inhoud in het PDF-bestand zijn gepland voor een toekomstige release.

  ![PDF-bestanden voorvertonen in [!DNL Experience Manager] PDF Viewer gebruiken](/help/assets/assets/preview-pdf-file-viewer.png)

* De functie voor het delen van koppelingen gebruikt asynchrone downloads die de downloadsnelheid verhogen. Zie voor meer informatie [Elementen downloaden die via koppelingen delen worden gedeeld](/help/assets/download-assets-from-aem.md#link-share-download).

  ![Postvak IN downloaden](/help/assets/assets/download-inbox.png)

* De weergave-instellingen worden verbeterd zodat gebruikers een standaardweergave en een standaardsorteerparameter kunnen kiezen.

  ![Standaardweergave instellen in [!UICONTROL View Settings]](/help/assets/assets/view-settings-for-defaults.png)

* Gebruikers kunnen de mappen zoeken en filteren op basis van voorspelden van eigenschappen.

  ![Zoekmappen filteren met behulp van voorvertoningen zoeken](/help/assets/assets/search-folders-via-predicates.png)

### Nieuwe functies beschikbaar in het dialoogvenster [!DNL Assets] prerelease-kanaal {#assets-prerelease-features}

<!-- TBD: Not sure about GA of these enh. Shall check with the team.

* A user experience enhancements displays the number of assets present in a folder. For more than 1000 assets in a folder, [!DNL Assets] displays 1000+.

  ![Number of assets in a folder are displayed on the interface](/help/assets/assets/browse-folder-number-of-assets.png)

* You can directly apply a metadata schemas to a folder in its [!UICONTROL Properties].

  ![Add metadata schema from folder properties](/help/assets/assets/metadata-schema-folder-properties.png)
-->

* Wanneer u digitale elementen deelt als een koppeling, kunnen gebruikers de URL naar het klembord kopiëren. Dankzij deze verbetering kunt u elementen sneller en handiger delen.

### Buizen vastgesteld in [!DNL Assets] {#assets-bugs-fixed}

De API `com.day.cq.dam.api.collection.SmartCollection` is niet beschikbaar in [!DNL Experience Manager] als [!DNL Cloud Service]. (CQ-4326322)

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* U kunt de dienst van de Automatede form conversion nu gebruiken aan [PDF forms converteren in het Frans, Duits en Spaans](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) aan adaptieve formulieren.
* Er is een apart deelvenster toegevoegd aan de sjablooneditor om fouten weer te geven met betrekking tot adaptieve formuliercomponenten. Hiermee kunt u alle adaptieve formulierfouten op één locatie consolideren en de resolutietijd verminderen.

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#beta-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Communicatie-API&#39;s](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html) Hiermee kunt u XDP-sjablonen en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met de service kunt u documenten in synchrone modus genereren. Met de API&#39;s kunt u toepassingen maken waarmee u:
   * Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   * Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   * Afdruk-PDF-bestanden genereren op basis van een XFA-formulier met PDF en Adobe Acrobat-formulier.

* **Variabele-gegevensexternalizer**: U kunt gegevens van AEM workflowvariabelen opslaan op een extern opslagsysteem dat wordt beheerd door uw organisatie.

* **Op acroform gebaseerd document of record**: U kunt ook [Adobe Acrobat Form PDF gebruiken (Acroform PDF)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html) als een sjabloon voor Document of Record naast XFA-formuliersjabloon.

* **Microsoft® Azure Data Store-connector**: U kunt nu [Formuliergegevensmodel aansluiten op Microsoft® Azure Storage](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage.html). Hiermee kunt u adaptieve formuliergegevens ophalen en opslaan naar Microsoft® Azure Storage als een BLOB.

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* CIF Core Components v2
   * Vereenvoudigde en verbeterde configuraties voor PDP/PLP URL en SEO
   * Visuele indicator voor gefaseerde productgegevens op auteurswijze voor betere zichtbaarheid van aanstaande veranderingen
   * Nieuwe sitemapcomponent voor inhoud- en handelspagina&#39;s

* Ondersteuning voor [Adobe Commerce Sensei Product Recommendation, aangedreven door Adobe Sensei](https://business.adobe.com/products/magento/product-recommendations.html) in AEM Storefront met behulp van vooraf gedefinieerde of tijdens de vlucht gemaakte aanbevelingen

## [!DNL Experience Manager Screens] als [!DNL Cloud Service] {#screens}

### Opgeloste problemen {#bug-fixes-screens}

* De instellingen van de inhoudsprovider worden nu gevalideerd tijdens het maken of bijwerken.

* Alle weergaveweergaven hebben mappenkolom.

* U kunt de structuur van de Inhoud van het scherm uitbreiden.

* `bulk-offline-update-service` ontbrak alle machtigingen voor bepaalde omgevingen.

* De bijgewerkte koppeling Help die overeenkomt met de nieuwe documentatie van de schermwolk.

* De toewijzing van afspeellijsten ongedaan maken en het verwijderen van afspeellijsten met toegewezen spelers niet toestaan, werkt nu.

* De speler downloadt nu elementen opnieuw wanneer de cache ALLE wordt gewist.

* Herhaling plannen werkt nu als de optie *Eindtijd* is ingesteld voor de volgende dag.

* `Back&Forward` werkt nu in de as a Cloud Service gebruikersinterface voor schermen.

* Labels met dezelfde naam maar verschillende naamruimten kunnen niet eerder worden gemaakt.

## XML Documentation for Experience Manager as a Cloud Service {#xml-documentation}

### Nieuwe functies {#what-is-new-xml-documentation}

XML Documentation for Experience Manager as a Cloud Service is over het algemeen beschikbaar. Klanten van as a Cloud Service Experience Manager kunnen hiermee een XML Documentation-invoegtoepassing aanschaffen om technische inhoud te importeren, maken, beheren en leveren via meerdere kanalen, waaronder Experience Manager Sites.

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.7.0 beschreven.

### Releasedatum {#release-cm-july}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.7.0 is 15 juli 2021.
De volgende release is gepland voor 12 augustus 2021.

### Wat is er nieuw? {#what-is-new-cm-july}

* Klanten kunnen nu gebruikmaken van 8 en 11 JDK&#39;s voor hun buildprocessen in Cloud Manager en kunnen een van deze JDK&#39;s selecteren voor gebruik van met toolketens compatibele Maven-plug-ins *of* de volledige Maven procesuitvoering.

* Uitgaande uitgang IP wordt nu het programma geopend in het dossier van het bouwstijlstaplogboek.

* Stage- en productieomgevingen met oude versies van AEM rapporteren nu de status van **Update beschikbaar**.

* Het maximum aantal ondersteunde SSL-certificaten is gestegen tot 20 per programma.

* Het maximumaantal domeinen dat kan worden gevormd is verhoogd tot 500 per milieu.

* De **Git beheren** knop is hernoemd naar **Toegang tot informatie over toegang** en het dialoogvenster is visueel vernieuwd.

* De versie van het AEM Project Archetype dat wordt gebruikt door Cloud Manager is bijgewerkt naar versie 28.

### Opgeloste problemen {#bug-fixes-cm-july}

* In sommige situaties, was de Voorproef geen beschikbare optie toen het binden van een IP lijst van gewenste personen aan een milieu.

* Wanneer u handmatig naar de pagina met uitvoeringsdetails voor een niet-bestaande uitvoering navigeerde, werd geen fout weergegeven, alleen een eindeloos laadscherm.

* Het foutbericht dat wordt weergegeven wanneer het maximumaantal SSL-certificaten is bereikt, is niet nuttig.

* In sommige omstandigheden kan er een discrepantie optreden in de releaseversie die wordt weergegeven op de pijplijnkaart op de **Overzicht** pagina.

* De wizard Programma toevoegen heeft onjuist aangegeven dat de naam na het maken niet meer kan worden gewijzigd.

### Bekende problemen {#known-issues-cm-july}

Klanten die overstappen op de Azul JDK&#39;s moeten weten dat niet alle bestaande toepassingen zonder fout compileren op de Azul JDK. De Adobe adviseert dat u plaatselijk alvorens omschakeling test.

## Cloud Acceleration Manager {#cam}

### Releasedatum {#release-date-july-cam}

De releasedatum voor Cloud Acceleration Manager is 15 juli 2021.

### Nieuwe functies {#what-is-new-cam}

Cloud Acceleration Manager is een cloudgebaseerde toepassing die ontworpen is om uw IT-teams te begeleiden tijdens de overgang van planning tot live gaan met Cloud Service. Stel uw team in voor een geslaagde migratie met aanbevolen Adobe procedures, tips, documentatie en tools voor elke fase van de reis naar AEM als Cloud Service. Meer informatie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/getting-started-cam.html).

>[!NOTE]
>
> Bekijk dit [Video over demo van cloudversnellingsbeheer](https://video.tv.adobe.com/v/335547).
