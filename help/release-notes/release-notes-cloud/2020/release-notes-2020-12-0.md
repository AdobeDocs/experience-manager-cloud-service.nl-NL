---
title: Opmerkingen bij de release 2020.12.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2020.12.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 16875180-1f23-477d-9d4d-e220998c4983
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 0%

---

# Opmerkingen bij de release [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release beschreven voor [!DNL Experience Manager] as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2020.12.0 is 17 december 2020.
De volgende release (2021.1.0) is 28 januari 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* **[HTTP-API voor inhoudsfragment](/help/assets/content-fragments/assets-api-content-fragments.md)**: Voeg de mogelijkheid toe om variaties van inhoudsfragmenten toe te voegen/bij te werken en te verwijderen met de HTTP-API.

## [!DNL Adobe Experience Manager Assets] als [!DNL Cloud Service] {#assets}

* Integratie met [!DNL Adobe InDesign Server] is nu beschikbaar voor [!DNL Experience Manager] als [!DNL Cloud Service]. Het verstrekt automatisering om te verwerken [!DNL Adobe InDesign] bestanden gebruiken [!DNL Adobe InDesign Server] scripts maken en gebruikers de mogelijkheid bieden [!DNL Assets] sjabloongebruikersinterface om brochures of advertenties te maken. Alleen [!DNL InDesign Server] gehost door [!DNL Adobe Managed Services] wordt ondersteund voor [!DNL Experience Manager as a Cloud Service]. <!-- TBD: Add link to article. -->

* [!DNL Experience Manager] is verbeterd voor het bijhouden en weergeven van elementverwijzingen wanneer een element op een externe server wordt gebruikt [!DNL Experience Manager Sites] implementatie met behulp van de Connected Assets-functionaliteit. Een nieuwe [!UICONTROL References] in het element [!UICONTROL Properties] De pagina bevat nu lokale en externe verwijzingen naar het element. Met de referenties kunnen DAM-gebruikers het gebruik van middelen bijhouden in [!DNL Sites] pagina&#39;s en in samengestelde elementen in [!DNL Assets]. Zie [Connected Assets configureren en gebruiken](/help/assets/use-assets-across-connected-assets-instances.md).

* [!DNL Dynamic Media] de mogelijkheden zijn nu via AEM toegankelijk [!DNL Sites] op afbeeldingen gebaseerde kerncomponenten. Auteurs kunnen snel componenten configureren voor het gebruik van Voorinstellingen voor afbeeldingen, SmartCrop en Image Modifiers bij het maken van webpagina&#39;s. Zie [Core Components 2.13.0-release](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.13.0).

* De [!DNL Experience Manager] met de bureaubladtoepassing kunnen gebruikers bestanden en mappen uploaden door de bestanden vanuit Windows Explorer of Mac Finder naar de bureaubladinterface te slepen. Zie [elementen toevoegen met de bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Release CIF Venia Reference Site - 2020.12.01 die de nieuwste versie CIF Core Components v1.6.0 bevat. Zie [CIF Venia-referentiegebied](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.12.01) voor meer informatie .

* Uitgegeven CIF Core Components v1.6.0. Zie [CIF kerncomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.6.0) voor meer informatie .

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor Cloud Manager in Adobe Experience Manager (AEM) as a Cloud Service 2020.12.0 is 10 december 2020.

### Nieuwe functies in [!DNL Cloud Manager] {#what-is-new-cm}

* Zelfbediening beheer van [SSL-certificaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) en [Aangepaste domeinnamen](/help/implementing/cloud-manager/custom-domain-names/introduction.md).

* Zelfbediening beheer van [IP-Lijsten van gewenste personen](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

* De bijgewerkte **Omgeving** De detailspagina staat nu gebruikers toe om de Namen van het Domein van de Douane en IP Lijsten van gewenste personen op hun milieu&#39;s te beheren.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* Er wordt iets gedaan aan sommige gevallen van fouten in het scannen van code zonder resultaten op te leveren.

* De milieucard gaf niet consistent de **Toevoegen** knop.

## Gereedschappen voor het verfijnen van code {#code-refactoring-tools}

### Nieuwe functies in [!DNL Code Refactoring Tools] {#what-is-new-crt}

* Nieuwe versie van AIO-CLI-plug-in uitgebracht. De meest recente versie van deze plug-in bevat foutoplossingen voor de AEM Dispatcher Converter en de Repository Modernizer en biedt ook ondersteuning voor een nieuw hulpprogramma - Index Converter. Zie [Unieke ervaring](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/unified-experience.html#benefits) waar u meer kunt weten over deze plug-in.

* De Omzetter van de index is een nut dat kan worden gebruikt om de Definities van de Index van de Eik van de Douane van een klant om te zetten in AEM as a Cloud Service compatibele Definities van de Index van de Eik. Zie [Indexconversie](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) voor meer informatie .

* Nieuwe functie toegevoegd aan [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) dat een afzonderlijk pakket maakt `ui.config` om alle configuraties te bevatten OSGi.

### Opgeloste problemen {#crt-bug-fixes}

* Er zijn verschillende foutoplossingen uitgevoerd op de AEM Dispatcher Converter en Repository Modernizer. Zie [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) en [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.1.20 is 8 januari 2021.

### Nieuwe functies in [!DNL Content Transfer Tool] {#what-is-new-ctt}

* Gebruikers kunnen nu leren of hun toegangstoken is verlopen door de muisaanwijzer op het statuspictogram in de gebruikersinterface van het hulpmiddel voor inhoudsoverdracht (CTT) te plaatsen. Zij worden ook meegedeeld in de Vastgestelde UI van de Details van de Migratie dat zij niet met hun instantie van de Cloud Service kunnen verbinden.

### Opgeloste problemen {#ctt-bug-fixes}

* De status van de gebruikersinterface van Content Transfer Tool (CTT) voor een migratieset bleef niet bestaan en werd niet gewijzigd na een periode van inactiviteit. Dit is opgelost.
* De optie voor het weergeven van logboeken is uitgeschakeld als de logboeken niet beschikbaar waren. Dit is opgelost en het overseinen is toegevoegd om gebruikers mee te delen waarom de logboeken ontbreken.
* Status van de gebruikersinterface van Content Transfer Tool is weergegeven *MISLUKT* wanneer de gebruiker een opname heeft gestopt. Dit is gecorrigeerd voor weergave *GESTOPT* in plaats daarvan.
