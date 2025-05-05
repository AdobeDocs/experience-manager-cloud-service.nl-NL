---
title: Nota's van de versie voor 2020.12.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2020.12.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 16875180-1f23-477d-9d4d-e220998c4983
feature: Release Information
role: Admin
source-git-commit: 64344b9b2cce8d7c7f05d3e5ba94049346308a9d
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 0%

---

# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor [!DNL Experience Manager] as a Cloud Service beschreven.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2020.12.0 is 17 december 2020.
De volgende release (2021.1.0) is 28 januari 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* **[HTTP API van het Fragment van de Inhoud van HTTP](/help/assets/content-fragments/assets-api-content-fragments.md)**: Voeg de capaciteit toe om de variaties van het Fragment van de Inhoud toe te voegen/bij te werken en te schrappen gebruikend HTTP API.

## [!DNL Adobe Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

* Integratie met [!DNL Adobe InDesign Server] is nu beschikbaar voor [!DNL Experience Manager] as a [!DNL Cloud Service] . Het biedt automatisering voor het verwerken van [!DNL Adobe InDesign] -bestanden met behulp van [!DNL Adobe InDesign Server] -scripts en biedt gebruikers de mogelijkheid om [!DNL Assets] -sjablonen in de gebruikersinterface te gebruiken om brochures of advertenties te maken. Alleen [!DNL InDesign Server] dat wordt gehost door [!DNL Adobe Managed Services] , wordt ondersteund voor [!DNL Experience Manager as a Cloud Service] . <!-- TBD: Add link to article. -->

* [!DNL Experience Manager] wordt uitgebreid om elementverwijzingen bij te houden en weer te geven wanneer een element wordt gebruikt in een externe [!DNL Experience Manager Sites] -implementatie met behulp van de Connected Assets-functionaliteit. Een nieuw tabblad [!UICONTROL References] op de pagina [!UICONTROL Properties] van het element bevat nu lokale en externe verwijzingen naar het element. Met de verwijzingen kunnen DAM-gebruikers het gebruik van elementen bijhouden in [!DNL Sites] -pagina&#39;s en in samengestelde elementen in [!DNL Assets] . Zie [ vormen en gebruiken Verbonden Assets ](/help/assets/use-assets-across-connected-assets-instances.md).

* De mogelijkheden van [!DNL Dynamic Media] zijn nu toegankelijk via AEM [!DNL Sites] op afbeeldingen gebaseerde Core Components. Auteurs kunnen snel componenten configureren voor het gebruik van Voorinstellingen voor afbeeldingen, SmartCrop en Image Modifiers bij het maken van webpagina&#39;s. Zie {de versie van de Componenten 2.13.0 van de Kern van 0} [&#128279;](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.13.0).

* Met de bureaubladtoepassing [!DNL Experience Manager] kunnen gebruikers bestanden en mappen uploaden door de bestanden vanuit Windows Explorer of Mac Finder naar de interface van de bureaubladtoepassing te slepen. Zie [ activa toevoegen gebruikend Desktop app ](https://experienceleague.adobe.com/nl/docs/experience-manager-desktop-app/using/using#upload-and-add-new-assets-to-aem).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Release CIF Venia Reference Site - 2020.12.01 die de nieuwste versie CIF Core Components v1.6.0 bevat. Zie [ CIF de Plaats van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.12.01) voor meer details.

* Uitgegeven CIF Core Components v1.6.0. Zie [ CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.6.0) voor meer details.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De Releasedatum voor Cloud Manager in Adobe Experience Manager (AEM) as a Cloud Service 2020.12.0 is 10 december 2020.

### Nieuwe functies in [!DNL Cloud Manager] {#what-is-new-cm}

* Zelfbediening beheer van [ SSL Certificaten ](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) en [ Inleiding aan de Namen van het Domein van de Douane ](/help/implementing/cloud-manager/custom-domain-names/introduction.md).

* Zelfbediening beheer van [ IP Lijsten van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

* De bijgewerkte **detailspagina van het Milieu** staat nu gebruikers toe om de Namen van het Domein van de Douane en IP Lijsten van gewenste personen op hun milieu&#39;s te beheren.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* Er wordt iets gedaan aan sommige gevallen van fouten in het scannen van code zonder resultaten op te leveren.

* De kaart van het milieu gaf niet constant **toe** knoop.

## Gereedschappen voor het verfijnen van code {#code-refactoring-tools}

### Nieuwe functies in [!DNL Code Refactoring Tools] {#what-is-new-crt}

* Nieuwe versie van AIO-CLI-plug-in uitgebracht. De meest recente versie van deze plug-in bevat foutoplossingen voor de AEM Dispatcher Converter en de Repository Modernizer en biedt ook ondersteuning voor een nieuw hulpprogramma - Index Converter. Zie [ Verenigde Ervaring ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/unified-experience#benefits) waar u meer over deze elektrisch toestel kunt leren.

* Indexconverter is een hulpprogramma waarmee de aangepaste Oak-indexdefinities van een klant kunnen worden getransformeerd naar Oak-compatibele indexdefinities. Zie [ Omzetter van de Index ](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) voor meer details.

* Nieuwe eigenschap die aan [ wordt toegevoegd de Modernizer van de Bewaarplaats ](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) die tot een afzonderlijk pakket `ui.config` leidt om alle configuraties te bevatten OSGi.

### Opgeloste problemen {#crt-bug-fixes}

* Er zijn verschillende foutoplossingen uitgevoerd voor de AEM Dispatcher Converter en Repository Modernizer. Zie [ AEM de Convertor van Dispatcher ](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) en [ Modernizer van de Bewaarplaats ](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.1.20 is 8 januari 2021.

### Nieuwe functies in [!DNL Content Transfer Tool] {#what-is-new-ctt}

* Gebruikers kunnen nu leren of hun toegangstoken is verlopen door de muisaanwijzer op het statuspictogram in de gebruikersinterface van het hulpmiddel voor inhoudsoverdracht (CTT) te plaatsen. Zij worden ook meegedeeld in de Vastgestelde UI van de Details van de Migratie dat zij niet met hun instantie van de Cloud Service kunnen verbinden.

### Opgeloste problemen {#ctt-bug-fixes}

* De status van de gebruikersinterface van Content Transfer Tool (CTT) voor een migratieset bleef niet bestaan en werd niet gewijzigd na een periode van inactiviteit. Dit probleem is nu opgelost.
* De optie voor het weergeven van logboeken is uitgeschakeld als de logboeken niet beschikbaar waren. Deze kwestie is nu opgelost en het overseinen wordt nu toegevoegd om gebruikers mee te delen waarom de logboeken ontbreken.
* De gebruikersinterfacestatus van het hulpmiddel van de Overdracht van de inhoud toonde *MISLUKT* toen de gebruiker een opname tegenhield. Deze kwestie wordt nu bevestigd om *GESTOPT* te tonen.
