---
title: Release-aantekeningen voor 2020.9.0-release van [!DNL Adobe Experience Manager] als Cloud Service.
description: '[!DNL Adobe Experience Manager] als opmerkingen bij de release van de Cloud Service voor 2020.9.0.'
translation-type: tm+mt
source-git-commit: 701d9ff3c9553c28bce0ef417487facedb22373f
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 1%

---


# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] als Cloud Service 2020.9.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor [!DNL Experience Manager] beschreven als een Cloud Service 2020.9.0.

## Releasedatum {#release-date}

De Releasedatum voor [!DNL Adobe Experience Manager] als Cloud Service 2020.9.0 is 24 september 2020.

## [!DNL Adobe Experience Manager Sites] als Cloud Service  {#sites}

### Nieuw in [!DNL Sites] {#what-is-new-sites}

* De JavaScript SDK [van de Editor voor één pagina-toepassing (SPA) is nu open bron.](/help/implementing/developing/hybrid/reference-materials.md)

## [!DNL Adobe Experience Manager Assets] als Cloud Service  {#assets}

### Nieuw in [!DNL Assets] {#what-is-new-assets}

* Watermerken van afbeeldingsbestanden wordt ondersteund voor uitvoeringen die worden gegenereerd met elementmicroservices. Deze kan worden geconfigureerd als een verwerkingsprofiel en gebruikt een PNG-bestand als watermerk. Zie [watermerk uw elementen](/help/assets/watermark-assets.md).

* Verbeteringen in [!DNL Dynamic Media]

   * Selectieve publicatie - Een marketingteam heeft nu toegang tot [!DNL Dynamic Media] slimme-uitsnijdafbeeldingen en dynamische uitvoeringen die zijn gesynchroniseerd met [!DNL Dynamic Media], zodat ze promotiemateriaal kunnen maken, zonder dat ze deze middelen hoeven te publiceren naar [!DNL Dynamic Media] voor wereldwijde levering. [!DNL Experience Manager] en  [!DNL Dynamic Media] publicatie wordt ontkoppeld en kan afzonderlijk plaatsvinden om dit te bereiken. Zie [selectief publiceren](/help/assets/dynamic-media/selective-publishing.md).
   * Beheerders kunnen het [!DNL Dynamic Media]-wachtwoord voor Cloud Servicen dat bij provisioning is ontvangen, nu opnieuw instellen. Het opnieuw instellen kan in [!DNL Experience Manager] gebruikersinterface worden gedaan, zonder de behoefte om [!DNL Dynamic Media Classic] Desktopapp te gebruiken.

* Zie [nieuw in Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html) voor informatie over de volgende verbeteringen.

   * Uitgebreide PDF-voorvertoning met integratie van Adobe Document Cloud View SDK.
   * Downloadfunctionaliteit met één klik.
   * Nieuwe beheerconfiguraties voor de downloadervaring.

<!--
### Bugs Fixed {#bugs-fixed-assets}

TBD: list of Assets aaCS bugs that are fixed.
-->

## Adobe Experience Manager Commerce als Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Uitgebrachte CIF Core Components v1.3.0. Raadpleeg [CIF Core Components](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.3.0) voor meer informatie.

* Voorvertoningsmogelijkheden met product/categorie voor product- en categoriesjablonen zijn nu beschikbaar. Zo kunnen zakelijke gebruikers/marketers in AEM de product-/categoriesjablonen met echte gegevens bekijken.

* De pagina van eigenschappen die aan producten en categorieën wordt toegevoegd om bedrijfsgebruikers toe te staan om details te bekijken verbonden aan product SKU/categorie identiteitskaart

* De sorteerfunctie die aan de productconsole is toegevoegd, zorgt ervoor dat producten/categorieën op naam of prijskenmerken kunnen worden gesorteerd.

* Productzoekfunctionaliteit toegevoegd aan productconsole.

### Opgeloste problemen {#bug-fixes-commerce}

* Commerce Cloud configuraties respecteerden overerving niet. Dit is gecorrigeerd om ervoor te zorgen dat de configuratie waarden erft.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De datum van de Versie voor [!UICONTROL Cloud Manager] Versie 2020.9.0 is September 03, 2020.

### Wat is er nieuw?{#what-is-new-cloud-manager}

* De controle van de inhoud is opnieuw geëtiketteerd als ErvingsControle.
* Het bouwstijlproces is gescheiden in drie afzonderlijke Maven bevelen.
* Als de Git Repository niet wordt gekloond, zal het tot drie keer worden herhaald.

### Opgeloste problemen {#bug-fixes-cm}

* Op het tabblad Inhoudscontrole wordt de basis-URL onjuist weergegeven met behulp van het auteurdomein in plaats van het publicatiedomein.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

Volg deze sectie om te weten te komen wat nieuw is en de updates voor Cloud Readiness Analyzer Release v1.1.0.

### Nieuwe functies {#what-is-new-cra}

* De Cloud Readiness Analyzer (CRA) heeft een beginstatusconsole die een expliciete **Generate Report** knoop voor de gebruiker toont om CRA uit te voeren.

* De CRA UI toont vooruitgang terwijl het loopt. Er worden items weergegeven die worden geanalyseerd en bevindingen tijdens de uitvoering worden gevonden.

* Het CRA-rapport geeft een samenvatting en het aantal bevindingen in tabelvorm, ingedeeld naar het type bevinding en het belangrijkste niveau. Wanneer u op het nummer van die bevinding klikt, wordt automatisch naar de locatie van die bevinding in het rapport geschoven.

### Opgeloste problemen {#cra-bug-fixes}

* In bepaalde gevallen werd het CRA-rapport niet bijgewerkt nadat het werd afgedwongen om te vernieuwen. Dit is opgelost in deze versie.

## De tool Content Transfer {#content-transfer-tool}

Volg deze sectie om te leren over wat nieuw is en de updates voor Versie van het Hulpmiddel van de Overdracht van de Inhoud v1.1.10.

### Nieuwe functies {#what-is-new-ctt}

* De CTT (Content Transfer Tool) biedt ondersteuning voor Azure Blob Store Data Store.

* De CTT-gebruikersinterface heeft een functie voor automatisch opnieuw laden waarmee de overzichtspagina elke 30 seconden opnieuw wordt geladen.

* Knop die aan CTT gebruikersinterface wordt toegevoegd om *Toegangstoken* gemakkelijk terug te winnen.

* Beschrijvend bevestigingsbericht toegevoegd voor *URL* en *Naam migratieset*.

## Tools voor herstructurering van code {#code-refactoring}

Volg deze sectie om te leren over wat nieuw en de updates voor de Hulpmiddelen van het Refactoring van de Code is.

### Nieuwe functies {#what-is-new-refactoring}

* De insteekmodule AIO-CLI ondersteunt Repository Modernizer en stelt gebruikers in staat het gereedschap uit te voeren met de insteekmodule.

   Zie [Git Resource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) voor meer informatie.

* Het nut van de Modernizer van de Bewaarplaats kan worden gebruikt om bestaande projectpakketten in pakketten te herstructureren die met de projectstructuur compatibel zijn die voor AEM als Cloud Service wordt bepaald.

   Zie [Git Resource: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) voor meer informatie.

