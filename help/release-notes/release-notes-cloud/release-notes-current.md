---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
translation-type: tm+mt
source-git-commit: 539fa16396519b66d53b91745bf69c819c5d5ea1
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---


# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] als Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor [!DNL Experience Manager] als Cloud Service weergegeven.

## Releasedatum {#release-date}

De Releasedatum voor [!DNL Adobe Experience Manager] als Cloud Service 2020.12.0 is 17 december 2020.
De volgende release (2021.1.0) vindt plaats op 28 januari 2020.

## [!DNL Adobe Experience Manager Sites] als Cloud Service  {#sites}

* **[HTTP-API voor](/help/assets/content-fragments/assets-api-content-fragments.md)** inhoudsfragment: Voeg de mogelijkheid toe om variaties van inhoudsfragmenten toe te voegen/bij te werken en te verwijderen met de HTTP-API.

## [!DNL Adobe Experience Manager Assets] als  [!DNL Cloud Service] {#assets}

* Integratie met [!DNL Adobe InDesign Server] is nu beschikbaar voor [!DNL Experience Manager] als [!DNL Cloud Service]. Het biedt automatisering om [!DNL Adobe InDesign] dossiers te verwerken gebruikend [!DNL Adobe InDesign Server] scripting en laat gebruikers [!DNL Assets] malplaatjegebruikersinterface gebruiken om brochures of advertenties tot stand te brengen. Alleen [!DNL InDesign Server] wordt gehost door [!DNL Adobe Managed Services] wordt ondersteund voor [!DNL Experience Manager as a Cloud Service]. <!-- TBD: Add link to article. -->

* [!DNL Experience Manager] wordt verbeterd om elementverwijzingen bij te houden en weer te geven wanneer een element wordt gebruikt in een externe  [!DNL Experience Manager Sites] implementatie met de functionaliteit Verbonden elementen. Een nieuw [!UICONTROL References] lusje in activa [!UICONTROL Properties] pagina maakt nu een lijst van lokale en verre verwijzingen van de activa. Met de verwijzingen kunnen DAM-gebruikers elementgebruik bijhouden op [!DNL Sites] pagina&#39;s en in samengestelde elementen in [!DNL Assets]. Zie [Aangesloten elementen configureren en gebruiken](/help/assets/use-assets-across-connected-assets-instances.md).

* [!DNL Dynamic Media] De mogelijkheden zijn nu toegankelijk via  [!DNL Sites] op afbeeldingen gebaseerde Core Components. Auteurs kunnen snel componenten configureren voor het gebruik van Voorinstellingen voor afbeeldingen, SmartCrop en Image Modifiers bij het maken van webpagina&#39;s. Zie [Core Components 2.13.0 release](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.13.0).

* [!DNL Experience Manager] met de bureaubladtoepassing kunnen gebruikers bestanden en mappen uploaden door de bestanden vanuit Windows Explorer of Mac Finder naar de bureaubladinterface te slepen. Zie [Elementen toevoegen met de bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem).

## Adobe Experience Manager Commerce als Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Uitgebrachte CIF Venia Reference Site - 2020.12.01 met de snelste versie van CIF Core Components v1.6.0. Raadpleeg [CIF Venia Reference Site](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.12.01) voor meer informatie.

* Uitgebrachte CIF Core Components v1.6.0. Raadpleeg [CIF Core Components](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.6.0) voor meer informatie.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2020.12.0 is 10 december 2020.

### Nieuw in [!DNL Cloud Manager] {#what-is-new-cm}

* Zelfservicebeheer van [SSL-certificaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) en [Aangepaste domeinnamen](/help/implementing/cloud-manager/custom-domain-names/introduction.md).

* Zelfservicebeheer van [IP-Lijsten van gewenste personen](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

* De bijgewerkte **Environment** detailpagina staat nu gebruikers toe om de Namen van het Domein van de Douane en IP Lijsten van gewenste personen op hun milieu&#39;s te beheren.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* Sommige gevallen van fouten tijdens het scannen van code zonder dat de resultaten worden verholpen.

* De kaart van het milieu gaf niet constant **Add** knoop.

## Tools voor herstructurering van code {#code-refactoring-tools}

### Nieuw in [!DNL Code Refactoring Tools] {#what-is-new-crt}

* Nieuwe versie van AIO-CLI-plug-in uitgebracht. De meest recente versie van deze plug-in bevat foutoplossingen voor de AEM Dispatcher Converter en de Repository Modernizer en ondersteunt ook een nieuw hulpprogramma - Index Converter. Raadpleeg [Unified Experience](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits) voor meer informatie over deze plug-in.

* De Omzetter van de index is een nut dat kan worden gebruikt om de Definities van de Index van de Douane van een klant om te zetten in AEM als Cloud Service compatibele Definities van de Index OAK. Raadpleeg [Indexconverter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) voor meer informatie.

* Nieuwe functie toegevoegd aan [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) die een afzonderlijk pakket `ui.config` maakt om alle OSGi-configuraties te bevatten.

### Opgeloste problemen {#crt-bug-fixes}

* Verscheidene insectenmoeilijke situaties die op de AEM Convertor van de Verzender en de Modernizer van de Bewaarplaats worden gedaan hulpmiddelen. Raadpleeg [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) en [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).
