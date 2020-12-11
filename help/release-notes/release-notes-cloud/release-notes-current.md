---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
translation-type: tm+mt
source-git-commit: 3aff98256eb26176bca52a49286bf2853290b5ef
workflow-type: tm+mt
source-wordcount: '1195'
ht-degree: 0%

---


# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] als Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor [!DNL Experience Manager] als Cloud Service weergegeven.

## Releasedatum {#release-date}

De datum van de Versie voor [!DNL Adobe Experience Manager] als Cloud Service 2020.11.0 is 2 December, 2020.
De volgende release (20.12.0) vindt plaats op 17 december 2020

## [!DNL Adobe Experience Manager Sites] als Cloud Service  {#sites}

### Nieuw in [!DNL Sites] {#what-is-new-sites}

* **[Start Hiërarchiebeheer](/help/sites-cloud/authoring/launches/managing-pages.md)  en  [Toekomstige tijdverdraaiing](/help/sites-cloud/authoring/launches/preview.md)**: De nieuwe interface voor het toevoegen/verwijderen van pagina&#39;s binnen een lancering, en het doorbladeren van plaats met Timewarp toont toekomstige staat van Lanceringen.

* **[Extended Content Fragment Models &amp; Editor](/help/assets/content-fragments/content-fragments-models.md)**: Nieuwe opties voor invoervalidatie voor verschillende gegevenstypen, verbeterd gegevenstype voor opsommingsgegevens met nieuwe formuliervisualisaties en de modelnaam van het inhoudsfragment wordt weergegeven en kan worden doorzocht in de interface Elementen.

* **Sorteer de Live Copy-pagina&#39;s die beschikbaar zijn voor rollout**: Nieuwe optie voor het sorteren van Live Copy-pagina&#39;s die beschikbaar zijn voor rollout met de  [!UICONTROL Name],  [!UICONTROL Last modified date]en  [!UICONTROL Last rollout date] eigenschappen. De [!UICONTROL Last rollout date] voor een pagina is een nieuwe eigenschap die is geïntroduceerd.

## [!DNL Adobe Experience Manager Assets] als Cloud Service  {#assets}

### Nieuw in [!DNL Assets] en [!DNL Dynamic Media] {#what-is-new-assets}

* **Opname van bulkmiddelen**: Klanten een schaalbare, in de cloud geïntegreerde innameservice bieden die  [!DNL Experience Manager] als een Cloud Service-architectuur wordt gebruikt, inclusief services voor het microgebruik van bedrijfsmiddelen. Belangrijke gebruiksgevallen zijn onder andere schaling op schaal met bewaking, rapportage en planning, terwijl de mogelijkheid bestaat om middelen eerst over te brengen naar de gegevensopslag in de cloud met gebruik van de gebruikelijke tools voor uploaden naar de cloud. Zie [tool voor het bulksgewijs invoegen van middelen](/help/assets/add-assets.md#asset-bulk-ingestor).
Dit hulpmiddel is voor systeembeheerder, adviseur, of de persona&#39;s van de implementatiepartner. Deze functie maakt het mogelijk om op grote schaal in te nemen en wordt bij voorkeur gebruikt tijdens de eerste opname of bij incidentele grote inname. Gebruik voor kleinere taken bij insluiten de [[!DNL Experience Manager] desktop app](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html?lang=en) of [upload met de gebruikersinterface van Elementen](/help/assets/add-assets.md#upload-assets).

   ![Configuratie van bulkimporteur](/help/assets/assets/bulk-import-config-low-res.png)

* Gebruikers kunnen de digitale elementen nu sorteren in de Kaart- en kolomweergave.

   ![sorteerelementen](/help/assets/assets/asset-sort-options.png)

* De volgende verbeteringen zijn aangebracht voor de toegankelijkheid in [!DNL Experience Manager Assets] in deze release. Zie [toegankelijkheidsfuncties in [!DNL Assets]](/help/assets/accessibility.md) voor meer informatie.

   * Wanneer u door de tijdlijn navigeert met een toetsenbord, kunt u met de toets Esc de optie Alles tonen samenvouwen zonder de focus te verliezen.
   * Wanneer u navigeert met de Tab-toets op het toetsenbord, blijft het tagveld actief nadat u de laatste tag uit de toegevoegde tags hebt verwijderd.
   * [!DNL Experience Manager] componenten bevatten nu de juiste informatie voor de naam, rol en waarde die door schermlezers moeten worden gebruikt.
   * Nadat u de keuzelijst Type/Grootte, keuzelijst Koppeling, keuzelijst Taal of Tekstbewerking hebt verwijderd, keert de toetsenbordfocus terug naar de volgende of vorige gebruikersinterface-elementen of naar een meer relevant gebruikersinterface-element.
   * Als u de aanwijzer op opties plaatst, worden er tips zoals Selecteren en Downloaden weergegeven. Gebruikers die een schermvergroting gebruiken, zien de miniaturen van het bestand mogelijk niet vanwege deze tips. Nu is het mogelijk om de focus te behouden nadat u de optie hebt verwijderd met de `Escape`-toets.
   * Wanneer u een rastercel selecteert uit het raster dat aanwezig is op de pagina, wordt de focus verschoven naar de actiebalk die op het scherm wordt weergegeven.
   * Visuele gebruikers kunnen onderscheid maken tussen normale tekst en een koppeling, aangezien visuele aanwijzingen (onderstreping en chevron-pictogram) worden weergegeven voor koppelingen naar alle oplossingen op de startpagina [!DNL Experience Manager].

* **Voorinstellingen batchset in Dynamic Media**: Nu kunt u het maken en ordenen van meerdere elementen in een afbeeldingsset automatiseren of de elementen laten draaien die zijn ingesteld op het moment dat u elementbestanden uploadt naar een map, afzonderlijk of met behulp van bulkopname.

   Zie [Voorinstellingen batchset](/help/assets/dynamic-media/batch-set-presets-dm.md).

* De volgende toegankelijkheidsverbeteringen zijn nu beschikbaar in [!DNL Dynamic Media]:

   * Schermlezers (JAWS, Narrator) vertellen de naam, de rol en de status van de menu-items in de menuoptie Grootte insluiten.
   * Gebruikers kunnen in het dialoogvenster E-mailkoppeling navigeren met de `Tab`-toets.
   * De workflow voor het maken van videocoderingsprofielen is gebruiksvriendelijker gezien de schermlezerverbetering.
   * Wanneer u navigeert met de `Tab`-toets, wordt de focus verplaatst naar de juiste gebruikersinterface-elementen in de workflow om een interactieve video te maken.
   * De pagina Publiceren, Asset-pagina bewerken, Smart Crops bewerken en de pagina Editor afbeeldingsset zijn verbeterd en voldoen nu aan de webstandaarden. Gebruikers met hulpprogramma&#39;s (AT) kunnen nu gemakkelijk door deze pagina&#39;s navigeren en acties uitvoeren, zoals het uitsnijden van afbeeldingen.
   * Gebruikers kunnen nu beter met een toetsenbord navigeren.
   * Gebruikers van het toetsenbord en de schermlezer kunnen de uitsnijdfunctionaliteit gebruiken.
   * De gebruikers van het toetsenbord kunnen de hotspots beter beheren.

   Zie [Toegankelijkheid in [!DNL Dynamic Media]](/help/assets/dynamic-media/accessibility-dm.md).

## Adobe Experience Manager Commerce als Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Uitgebrachte CIF Venia Reference Site - 2020.11.05 met de snelste versie van CIF Core Components v1.5.0. Raadpleeg [CIF Venia Reference Site](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.27) voor meer informatie.

* Uitgebrachte CIF Core Components v1.5.0. Raadpleeg [CIF Core Components](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.5.0) voor meer informatie.

### Opgeloste problemen {#bug-fixes-commerce}

* De de cliëntconfig van GraphQL werd niet correct gelezen wanneer config niet direct in het Verdelen CA config wordt gespecificeerd, maar in één van de ouder vormt. Dit is opgelost.

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

## Adobe Experience Manager als Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* Er is ondersteuning toegevoegd voor het zoeken naar workflowinstanties op basis van workflowtitel, workflowmodel, status, initiator, Payload Path en Begindatum. Zie [Workflowinstanties zoeken](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/administering/workflows-administering.html).

### Synchronisatie van gebruikersgegevens op publicatieniveau {#user-sync}

* Gebruikersgegevens, waaronder profielkenmerken en groepslidmaatschappen, kunnen op de publicatielijst worden voortgezet. Meer informatie over deze functie vindt u in de documentatie [Registratie, aanmelding en gebruikersprofiel](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md).

### SDK Build Analyzers {#analyzers}

De AEM als Cloud Service SDK bouwt Analyzer Maven Plugin ontdekt problemen in een bepaald project, met inbegrip van ontbrekende gebiedsdelen. Het biedt ontwikkelaars de mogelijkheid om problemen tijdens lokale ontwikkeling op te sporen, ruim voordat ze met Cloud Manager naar een cloud-omgeving implementeren. Zie de documentatie [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=en#developing) en [hier](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#building-for-the-sdk) voor meer informatie.

### Overige{#others-foundation}

Nieuwe [&quot;httpd -t&quot;syntaxis](/help/implementing/dispatcher/disp-overview.md#local-validation) controle op apache en verzender configuratie uitgevoerd tijdens de Bouwstijl van de Manager van de Wolk, die ook kan worden in werking gesteld gebruikend AEM als de Hulpmiddelen van de Verzender van SDK van de Cloud Service.

## Tools voor herstructurering van code {#code-refactoring-tools}

### Nieuw in [!DNL Code Refactoring Tools] {#what-is-new-crt}

* Nieuwe versie van AIO-CLI-plug-in uitgebracht. De meest recente versie van deze plug-in bevat foutoplossingen voor de AEM Dispatcher Converter en de Repository Modernizer en ondersteunt ook een nieuw hulpprogramma - Index Converter. Raadpleeg [Unified Experience](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits) voor meer informatie over deze plug-in.

* De Omzetter van de index is een nut dat kan worden gebruikt om de Definities van de Index van de Douane van een klant om te zetten in AEM als Cloud Service compatibele Definities van de Index OAK.
Raadpleeg [Indexconverter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) voor meer informatie.

* Nieuwe functie toegevoegd aan [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) die een afzonderlijk pakket `ui.config` maakt om alle OSGi-configuraties te bevatten.

### Opgeloste problemen {#crt-bug-fixes}

* Verscheidene insectenmoeilijke situaties die op de AEM Convertor van de Verzender en de Modernizer van de Bewaarplaats worden gedaan hulpmiddelen.
Raadpleeg [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) en [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).