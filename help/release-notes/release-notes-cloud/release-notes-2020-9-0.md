---
title: Opmerkingen bij de release voor 2020.9.0 [!DNL Adobe Experience Manager] van een Cloud Service.
description: '[!DNL Adobe Experience Manager] als opmerkingen bij de release van de Cloud Service voor 2020.9.0.'
translation-type: tm+mt
source-git-commit: db5ca67c583166f4ecb09884a064dfc1378f436e
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 1%

---


# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] als Cloud Service 2020.9.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release [!DNL Experience Manager] als Cloud Service 2020.9.0 beschreven.

## Releasedatum {#release-date}

De Releasedatum voor [!DNL Adobe Experience Manager] als Cloud Service 2020.9.0 is 24 september 2020.

## [!DNL Adobe Experience Manager Sites] als Cloud Service {#sites}

### What is new in [!DNL Sites] {#what-is-new-sites}

* De Single Page Application (SPA) Editor JavaScript SDK [is nu open source.](/help/implementing/developing/spa/reference-materials.md)

## [!DNL Adobe Experience Manager Assets] als Cloud Service {#assets}

### What is new in [!DNL Assets] {#what-is-new-assets}

* Watermerken van afbeeldingsbestanden wordt ondersteund voor uitvoeringen die worden gegenereerd met elementmicroservices. Deze kan worden geconfigureerd als een verwerkingsprofiel en gebruikt een PNG-bestand als watermerk. Zie [watermerk uw elementen](/help/assets/watermark-assets.md).

* Verbeteringen in [!DNL Dynamic Media]

   * Selectieve publicatie - Een marketingteam kan nu toegang krijgen tot [!DNL Dynamic Media] SmartCrop-afbeeldingen en dynamische uitvoeringen die zijn gesynchroniseerd, [!DNL Dynamic Media] zodat ze promotiemateriaal kunnen maken zonder dat ze deze elementen hoeven te publiceren [!DNL Dynamic Media] voor wereldwijde levering. [!DNL Experience Manager] en [!DNL Dynamic Media] publicatie wordt ontkoppeld en kan afzonderlijk plaatsvinden om dit te bereiken. Zie [Selectieve publicatie](/help/assets/dynamic-media/selective-publishing.md).
   * Beheerders kunnen nu het wachtwoord voor [!DNL Dynamic Media] Cloud Servicen opnieuw instellen dat bij provisioning wordt ontvangen. U kunt de instellingen opnieuw instellen in de [!DNL Experience Manager] gebruikersinterface zonder dat u de [!DNL Dynamic Media Classic] bureaubladtoepassing hoeft te gebruiken.

* Zie [wat nieuw is in Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html)voor informatie over de volgende verbeteringen.

   * Uitgebreide PDF-voorvertoning met integratie van Adobe Document Cloud View SDK.
   * Downloadfunctionaliteit met één klik.
   * Nieuwe beheerconfiguraties voor de downloadervaring.

<!--
### Bugs Fixed {#bugs-fixed-assets}

TBD: list of Assets aaCS bugs that are fixed.
-->

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Uitgebrachte CIF Core Components v1.3.0. Raadpleeg [CIF Core Components](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.3.0) voor meer informatie.

* Voorvertoningsmogelijkheden met product/categorie voor product- en categoriesjablonen zijn nu beschikbaar. Zo kunnen zakelijke gebruikers/marketers in AEM de product-/categoriesjablonen met echte gegevens bekijken.

* De pagina van eigenschappen die aan producten en categorieën wordt toegevoegd om bedrijfsgebruikers toe te staan om details te bekijken verbonden aan product SKU/categorie identiteitskaart

* De sorteerfunctie die aan de productconsole is toegevoegd, zorgt ervoor dat producten/categorieën op naam of prijskenmerken kunnen worden gesorteerd.

* Productzoekfunctionaliteit toegevoegd aan productconsole.

### Bug Fixes {#bug-fixes-commerce}

* Commerce Cloud configuraties respecteerden overerving niet. Dit is gecorrigeerd om ervoor te zorgen dat de configuratie waarden erft.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor [!UICONTROL Cloud Manager] versie 2020.9.0 is 3 september 2020.

### Wat is er nieuw?{#what-is-new-cloud-manager}

* De controle van de inhoud is opnieuw geëtiketteerd als ErvingsControle.
* Het bouwstijlproces is gescheiden in drie afzonderlijke Maven bevelen.
* Als de Git Repository niet wordt gekloond, zal het tot drie keer worden herhaald.

### Bug Fixes {#bug-fixes-cm}

* Op het tabblad Inhoudscontrole wordt de basis-URL onjuist weergegeven met behulp van het auteurdomein in plaats van het publicatiedomein.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

Volg deze sectie om te weten te komen wat nieuw is en de updates voor Cloud Readiness Analyzer Release v1.1.0.

### Nieuwe functies {#what-is-new-cra}

* De Cloud Readiness Analyzer (CRA) heeft een beginstatusconsole die een expliciete knop Rapport **** genereren weergeeft waarop de gebruiker kan klikken om de CRA uit te voeren.

* De CRA UI toont vooruitgang terwijl het loopt. Er worden items weergegeven die worden geanalyseerd en bevindingen tijdens de uitvoering worden gevonden.

* Het CRA-rapport geeft een samenvatting en het aantal bevindingen in tabelvorm, ingedeeld naar het type bevinding en het belangrijkste niveau. Wanneer u op het nummer van die bevinding klikt, wordt automatisch naar de locatie van die bevinding in het rapport geschoven.

### Bug Fixes {#cra-bug-fixes}

* In bepaalde gevallen werd het CRA-rapport niet bijgewerkt nadat het werd afgedwongen om te vernieuwen. Dit is opgelost in deze versie.

## De tool Content Transfer {#content-transfer-tool}

Volg deze sectie om te leren over wat nieuw is en de updates voor Versie van het Hulpmiddel van de Overdracht van de Inhoud v1.1.10.

### Nieuwe functies {#what-is-new-ctt}

* De CTT (Content Transfer Tool) biedt ondersteuning voor Azure Blob Store Data Store.

* De CTT-gebruikersinterface heeft een functie voor automatisch opnieuw laden waarmee de overzichtspagina elke 30 seconden opnieuw wordt geladen.

* Knop die aan CTT gebruikersinterface wordt toegevoegd om *Toegangstoken* gemakkelijk terug te winnen.

* Er is een beschrijvend validatiebericht toegevoegd voor de naam *van de* URL *en de* migratieset.

## Tools voor herstructurering van code {#code-refactoring}

Volg deze sectie om te leren over wat nieuw en de updates voor de Hulpmiddelen van het Refactoring van de Code is.

### Nieuwe functies {#what-is-new-refactoring}

* De insteekmodule AIO-CLI ondersteunt Repository Modernizer en stelt gebruikers in staat het gereedschap uit te voeren met de insteekmodule.

   Zie [Git Resource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) voor meer informatie.

* Het nut van de Modernizer van de Bewaarplaats kan worden gebruikt om bestaande projectpakketten in pakketten te herstructureren die met de projectstructuur compatibel zijn die voor AEM als Cloud Service wordt bepaald.

   Zie [Git Resource: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) voor meer informatie.

