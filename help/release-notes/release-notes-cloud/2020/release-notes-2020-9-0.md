---
title: Nota's van de versie voor 2020.9.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release voor 2020.9.0."
exl-id: 2332512f-8c52-4569-a006-faa36a7670a1
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---

# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor [!DNL Experience Manager] as a Cloud Service 2020.9.0 beschreven.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 is 24 september 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Nieuwe functies in [!DNL Sites] {#what-is-new-sites}

* De enige Toepassing van de Pagina (SPA) Redacteur JavaScript SDK [ is nu open bron ](/help/implementing/developing/hybrid/reference-materials.md).

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Nieuwe functies in [!DNL Assets] {#what-is-new-assets}

* Watermerken van afbeeldingsbestanden wordt ondersteund voor uitvoeringen die worden gegenereerd met elementmicroservices. Deze kan worden geconfigureerd als een verwerkingsprofiel en gebruikt een PNG-bestand als watermerk. Zie [ watermerk uw activa ](/help/assets/watermark-assets.md).

* Verbeteringen in [!DNL Dynamic Media]

   * Selectieve Publish - Een marketingteam kan nu toegang krijgen tot [!DNL Dynamic Media] Smart crop images en dynamische uitvoeringen die zijn gesynchroniseerd met [!DNL Dynamic Media] , zodat ze promotiematerialen kunnen maken zonder dat ze deze middelen naar [!DNL Dynamic Media] hoeven te publiceren voor levering wereldwijd. [!DNL Experience Manager] en [!DNL Dynamic Media] publishing is ontkoppeld en kan afzonderlijk plaatsvinden om dit te bereiken. Zie [ selectief publiceren ](/help/assets/dynamic-media/selective-publishing.md).
   * Beheerders kunnen nu het wachtwoord voor de Cloud Service van [!DNL Dynamic Media] opnieuw instellen dat bij provisioning wordt ontvangen. U kunt de instellingen opnieuw instellen in de gebruikersinterface van [!DNL Experience Manager] zonder dat u de bureaubladtoepassing van [!DNL Dynamic Media Classic] hoeft te gebruiken.

* Om over de volgende verhogingen te weten, zie [ wat in Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=nl-NL) nieuw is.

   * Verbeterde PDF-voorvertoning dankzij de integratie met Adobe Document Cloud View SDK.
   * Downloadfunctionaliteit met één klik.
   * Nieuwe beheerconfiguraties voor de downloadervaring.

<!--
### Bugs Fixed {#bugs-fixed-assets}

TBD: list of Assets aaCS bugs that are fixed.
-->

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Uitgegeven CIF Core Components v1.3.0. Zie [ CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.3.0) voor meer details.

* Voorvertoningsmogelijkheden met product/categorie voor product- en categoriesjablonen zijn nu beschikbaar. Zo kunnen zakelijke gebruikers/marketers in AEM de product-/categoriesjablonen met echte gegevens bekijken.

* De pagina van eigenschappen die aan producten en categorieën wordt toegevoegd om bedrijfsgebruikers toe te staan om details te bekijken verbonden aan product SKU/categorie identiteitskaart

* De sorteerfunctie die aan de productconsole is toegevoegd, zorgt ervoor dat producten/categorieën op naam of prijskenmerken kunnen worden gesorteerd.

* Productzoekfunctionaliteit toegevoegd aan productconsole.

### Opgeloste problemen {#bug-fixes-commerce}

* Bij configuraties van Commercen Cloud is de overerving niet gerespecteerd. Dit is gecorrigeerd om ervoor te zorgen dat de configuratie waarden erft.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor [!UICONTROL Cloud Manager] versie 2020.9.0 is 3 september 2020.

### Wat is er nieuw? {#what-is-new-cloud-manager}

* De controle van de inhoud is opnieuw geëtiketteerd als ErvingsControle.
* Het bouwstijlproces is gescheiden in drie afzonderlijke Maven bevelen.
* Als de Git Repository niet wordt gekloond, wordt het tot drie keer opnieuw gemaakt.

### Opgeloste problemen {#bug-fixes-cm}

* Op het tabblad Inhoudscontrole wordt de basis-URL onjuist weergegeven met behulp van het auteurdomein in plaats van het publicatiedomein.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

Volg deze sectie voor meer informatie over nieuwe functies en de updates voor Cloud Readiness Analyzer Release v1.1.0.

### Nieuwe functies {#what-is-new-cra}

* De Analysator van de Bereidheid van de Wolk (CRA) heeft een console van de beginstaat die expliciete **toont produceert de knoop van het Rapport** voor de gebruiker om te klikken om CRA uit te voeren.

* De CRA UI toont vooruitgang terwijl het loopt. Er worden items weergegeven die worden geanalyseerd en bevindingen tijdens de uitvoering worden gevonden.

* Het CRA-rapport geeft een samenvatting en het aantal bevindingen in tabelvorm, ingedeeld naar het type bevinding en het belangrijkste niveau. Wanneer u op het nummer van die bevinding klikt, wordt automatisch naar de locatie van die bevinding in het rapport geschoven.

### Opgeloste problemen {#cra-bug-fixes}

* In bepaalde gevallen werd het CRA-rapport niet bijgewerkt nadat het werd afgedwongen om te vernieuwen. Dit is opgelost in deze versie.

## Inhoud overbrengen {#content-transfer-tool}

Volg deze sectie om te leren over wat nieuw is en de updates voor Versie van het Hulpmiddel van de Overdracht van de Inhoud v1.1.10.

### Nieuwe functies {#what-is-new-ctt}

* De CTT (Content Transfer Tool) biedt ondersteuning voor Azure Blob Store Data Store.

* De CTT-gebruikersinterface heeft een functie voor automatisch opnieuw laden waarmee de overzichtspagina elke 30 seconden opnieuw wordt geladen.

* Knoop die aan CTT gebruikersinterface wordt toegevoegd om *Symbolisch van de Toegang* gemakkelijk terug te winnen.

* Het beschrijvende bevestigingsbericht dat voor *wordt toegevoegd URL* en *de Vastgestelde Naam van de Migratie*.

## Gereedschappen voor het verfijnen van code {#code-refactoring}

Volg deze sectie om te leren over wat nieuw en de updates voor de Hulpmiddelen van het Refactoring van de Code is.

### Nieuwe functies {#what-is-new-refactoring}

* De insteekmodule AIO-CLI ondersteunt Repository Modernizer en stelt gebruikers in staat het gereedschap uit te voeren met de insteekmodule.

  Zie [ Middel van de Git: ao-cli-stop-aem-wolk-dienst-migratie ](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) voor meer details.

* Het nut van de Modernizer van de Bewaarplaats kan worden gebruikt om bestaande projectpakketten in pakketten te herstructureren die met de projectstructuur verenigbaar zijn die voor AEM as a Cloud Service wordt bepaald.

  Zie [ Middel van de Git: Modernizer van de Bewaarplaats ](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) voor meer details.
