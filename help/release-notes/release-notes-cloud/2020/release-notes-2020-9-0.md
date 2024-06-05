---
title: Opmerkingen bij de release 2020.9.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release 2020.9.0."
exl-id: 2332512f-8c52-4569-a006-faa36a7670a1
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---

# Opmerkingen bij de release [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release beschreven voor [!DNL Experience Manager] as a Cloud Service 2020.9.0.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 is 24 september 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Nieuwe functies in [!DNL Sites] {#what-is-new-sites}

* De Single Page Application (SPA) Editor JavaScript SDK [is nu open bron](/help/implementing/developing/hybrid/reference-materials.md).

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Nieuwe functies in [!DNL Assets] {#what-is-new-assets}

* Watermerken van afbeeldingsbestanden wordt ondersteund voor uitvoeringen die worden gegenereerd met elementmicroservices. Deze kan worden geconfigureerd als een verwerkingsprofiel en gebruikt een PNG-bestand als watermerk. Zie [watermerk uw elementen](/help/assets/watermark-assets.md).

* Verbeteringen in [!DNL Dynamic Media]

   * Selectieve publicatie - Een marketingteam kan nu toegang krijgen [!DNL Dynamic Media] SmartCrop-afbeeldingen en dynamische uitvoeringen die zijn gesynchroniseerd met [!DNL Dynamic Media] zodat ze promotiemateriaal kunnen maken zonder dat ze deze middelen hoeven te publiceren naar [!DNL Dynamic Media] voor wereldwijde levering. [!DNL Experience Manager] en [!DNL Dynamic Media] publicatie is ontkoppeld en kan afzonderlijk plaatsvinden om dit te bereiken. Zie [selectief publiceren](/help/assets/dynamic-media/selective-publishing.md).
   * Beheerders kunnen nu opnieuw instellen [!DNL Dynamic Media] Wachtwoord van de Cloud Service dat bij levering wordt ontvangen. U kunt de voorinstelling uitvoeren in [!DNL Experience Manager] gebruikersinterface, zonder de noodzaak om [!DNL Dynamic Media Classic] bureaubladtoepassing.

* Zie voor meer informatie over de volgende verbeteringen [nieuwe functies in Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html).

   * Verbeterde PDF-voorvertoning dankzij de integratie met Adobe Document Cloud View SDK.
   * Downloadfunctionaliteit met één klik.
   * Nieuwe beheerconfiguraties voor de downloadervaring.

<!--
### Bugs Fixed {#bugs-fixed-assets}

TBD: list of Assets aaCS bugs that are fixed.
-->

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Uitgegeven CIF Core Components v1.3.0. Zie [CIF kerncomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.3.0) voor meer informatie .

* Voorvertoningsmogelijkheden met product/categorie voor product- en categoriesjablonen zijn nu beschikbaar. Zo kunnen zakelijke gebruikers/marketers in AEM de product-/categoriesjablonen met echte gegevens bekijken.

* De pagina van eigenschappen die aan producten en categorieën wordt toegevoegd om bedrijfsgebruikers toe te staan om details te bekijken verbonden aan product SKU/categorie identiteitskaart

* De sorteerfunctie die aan de productconsole is toegevoegd, zorgt ervoor dat producten/categorieën op naam of prijskenmerken kunnen worden gesorteerd.

* Productzoekfunctionaliteit toegevoegd aan productconsole.

### Opgeloste problemen {#bug-fixes-commerce}

* Bij configuraties van Commercen Cloud is de overerving niet gerespecteerd. Dit is gecorrigeerd om ervoor te zorgen dat de configuratie waarden erft.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor [!UICONTROL Cloud Manager] Versie 202.9.0 is 3 september 2020.

### Wat is er nieuw? {#what-is-new-cloud-manager}

* De controle van de inhoud is opnieuw geëtiketteerd als ErvingsControle.
* Het bouwstijlproces is gescheiden in drie afzonderlijke Maven bevelen.
* Als de Git Repository niet wordt gekloond, wordt het tot drie keer opnieuw gemaakt.

### Opgeloste problemen {#bug-fixes-cm}

* Op het tabblad Inhoudscontrole wordt de basis-URL onjuist weergegeven met behulp van het auteurdomein in plaats van het publicatiedomein.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

Volg deze sectie voor meer informatie over nieuwe functies en de updates voor Cloud Readiness Analyzer Release v1.1.0.

### Nieuwe functies {#what-is-new-cra}

* De Cloud Readiness Analyzer (CRA) heeft een startstatusconsole die een expliciete **Rapport genereren** klikt de gebruiker om de CRA uit te voeren.

* De CRA UI toont vooruitgang terwijl het loopt. Er worden items weergegeven die worden geanalyseerd en bevindingen tijdens de uitvoering worden gevonden.

* Het CRA-rapport geeft een samenvatting en het aantal bevindingen in tabelvorm, ingedeeld naar het type bevinding en het belangrijkste niveau. Wanneer u op het nummer van die bevinding klikt, wordt automatisch naar de locatie van die bevinding in het rapport geschoven.

### Opgeloste problemen {#cra-bug-fixes}

* In bepaalde gevallen werd het CRA-rapport niet bijgewerkt nadat het werd afgedwongen om te vernieuwen. Dit is opgelost in deze versie.

## Inhoud overbrengen {#content-transfer-tool}

Volg deze sectie om te leren over wat nieuw is en de updates voor Versie van het Hulpmiddel van de Overdracht van de Inhoud v1.1.10.

### Nieuwe functies {#what-is-new-ctt}

* De CTT (Content Transfer Tool) biedt ondersteuning voor Azure Blob Store Data Store.

* De CTT-gebruikersinterface heeft een functie voor automatisch opnieuw laden waarmee de overzichtspagina elke 30 seconden opnieuw wordt geladen.

* Knop die wordt toegevoegd aan de CTT-gebruikersinterface om op te halen *Toegangstoken* gemakkelijk.

* Beschrijving van validatiebericht toegevoegd voor *URL* en *Naam migratieset*.

## Gereedschappen voor het verfijnen van code {#code-refactoring}

Volg deze sectie om te leren over wat nieuw en de updates voor de Hulpmiddelen van het Refactoring van de Code is.

### Nieuwe functies {#what-is-new-refactoring}

* De insteekmodule AIO-CLI ondersteunt Repository Modernizer en stelt gebruikers in staat het gereedschap uit te voeren met de insteekmodule.

  Zie [Git-bron: audio-cli-plugin-aem-cloud-service-migratie](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) voor meer informatie .

* Het nut van de Modernizer van de Bewaarplaats kan worden gebruikt om bestaande projectpakketten in pakketten te herstructureren die met de projectstructuur compatibel zijn die voor AEM as a Cloud Service wordt bepaald.

  Zie [Git Resource: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) voor meer informatie .
