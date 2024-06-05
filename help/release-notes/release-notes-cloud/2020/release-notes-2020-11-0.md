---
title: Opmerkingen bij de release 2020.11.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release 2020.11.0."
exl-id: 8066c0fb-c2f5-4625-9448-b0c74ff4e192
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1213'
ht-degree: 0%

---

# Opmerkingen bij de release [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release beschreven voor [!DNL Experience Manager] as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2020.11.0 is 2 december 2020.
De volgende release (20.12.0) vindt plaats op 17 december 2020

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Nieuwe functies in [!DNL Sites] {#what-is-new-sites}

* **[Hiermee wordt hiërarchiebeheer gestart](/help/sites-cloud/authoring/launches/managing-pages.md) &amp; [Future Timewarp](/help/sites-cloud/authoring/launches/preview.md)**: Nieuwe interface voor het toevoegen/verwijderen van pagina&#39;s binnen een opstart en het bladeren naar een site met tijdverdraaiing geeft de toekomstige status van Launches aan.

* **[Extended Content Fragment Models &amp; Editor](/help/assets/content-fragments/content-fragments-models.md)**: Nieuwe opties voor invoervalidatie voor verschillende gegevenstypen, verbeterd gegevenstype Opsomming met nieuwe formuliervisualisaties en de modelnaam van het inhoudsfragment wordt weergegeven en kan worden doorzocht in de interface Elementen.

* **Live Copy-pagina&#39;s die beschikbaar zijn voor rollout sorteren**: Nieuwe optie om de pagina&#39;s van Live Copy die beschikbaar zijn voor rollout te sorteren met de opdracht [!UICONTROL Name], [!UICONTROL Last modified date], en [!UICONTROL Last rollout date] eigenschappen. De [!UICONTROL Last rollout date] voor een pagina is een nieuwe eigenschap geïntroduceerd.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Nieuwe functies in [!DNL Assets] en [!DNL Dynamic Media] {#what-is-new-assets}

* **Opname van bulkactiva**: Bied klanten een schaalbare, in de cloud geïntegreerde service die gebruikmaakt van [!DNL Experience Manager] as a Cloud Service architectuur, met inbegrip van de diensten van activa microservices. Belangrijke gebruiksgevallen zijn onder andere schaling op schaal met bewaking, rapportage en planning, terwijl de mogelijkheid bestaat om middelen eerst over te brengen naar de gegevensopslag in de cloud met gebruik van de gebruikelijke tools voor uploaden naar de cloud. Zie [gereedschap voor het bulkmiddel](/help/assets/add-assets.md#asset-bulk-ingestor).

  Dit hulpmiddel is voor systeembeheerder, adviseur, of de persona&#39;s van de implementatiepartner. Deze functie maakt het mogelijk om op grote schaal in te nemen en wordt bij voorkeur gebruikt tijdens de eerste opname of bij incidentele grote inname. Gebruik voor kleinere taken de opdracht [[!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html) of [uploaden met de gebruikersinterface van Elementen](/help/assets/add-assets.md#upload-assets).

  ![Configuratie van bulkimporteur](/help/assets/assets/bulk-import-config-low-res.png)

* Gebruikers kunnen de digitale elementen nu sorteren in de Kaart- en kolomweergave.

  ![sorteerelementen](/help/assets/assets/asset-sort-options.png)

* De volgende verbeteringen zijn aangebracht voor toegankelijkheid in [!DNL Experience Manager Assets] in deze release. Zie voor meer informatie [toegankelijkheidsfuncties in [!DNL Assets]](/help/assets/accessibility.md).

   * Wanneer u door de tijdlijn navigeert met een toetsenbord, kunt u met de toets Esc de optie Alles tonen samenvouwen zonder de focus te verliezen.
   * Wanneer u navigeert met de Tab-toets op het toetsenbord, blijft het tagveld actief nadat u de laatste tag uit de toegevoegde tags hebt verwijderd.
   * [!DNL Experience Manager] componenten bevatten nu de juiste informatie voor de naam, rol en waarde die door schermlezers moeten worden gebruikt.
   * Nadat u de keuzelijst Type/Grootte, keuzelijst Koppeling, keuzelijst Taal of Tekstbewerking hebt verwijderd, keert de toetsenbordfocus terug naar de volgende of vorige gebruikersinterface-elementen of naar een meer relevant gebruikersinterface-element.
   * Als u de aanwijzer op opties plaatst, worden er tips zoals Selecteren en Downloaden weergegeven. Gebruikers die een schermvergroting gebruiken, zien de miniaturen van het bestand mogelijk niet vanwege deze tips. Nu is het mogelijk om de focus te behouden nadat u de optie hebt verwijderd met `Escape` toets.
   * Wanneer u een rastercel selecteert uit het raster dat aanwezig is op de pagina, wordt de focus verschoven naar de actiebalk die op het scherm wordt weergegeven.
   * Visuele gebruikers kunnen onderscheid maken tussen normale tekst en een koppeling, aangezien visuele aanwijzingen (onderstreping en chevron-pictogram) worden weergegeven voor koppelingen naar alle oplossingen in [!DNL Experience Manager] homepage.

* **Voorinstellingen batchset in Dynamic Media**: Nu kunt u het maken en organiseren van meerdere elementen in een afbeeldingsset automatiseren of de elementen laten draaien die zijn ingesteld op het moment dat u elementbestanden uploadt naar een map, afzonderlijk of met behulp van bulkopname.

  Zie [Voorinstellingen batchset](/help/assets/dynamic-media/batch-set-presets-dm.md).

* De volgende toegankelijkheidsverbeteringen zijn nu beschikbaar in [!DNL Dynamic Media]:

   * Schermlezers (JAWS, Narrator) vertellen de naam, de rol en de status van de menu-items in de menuoptie Grootte insluiten.
   * Gebruikers kunnen in het dialoogvenster E-mailkoppeling navigeren met het dialoogvenster `Tab` toets.
   * De workflow voor het maken van videocoderingsprofielen is gebruiksvriendelijker gezien de schermlezerverbetering.
   * Bij navigeren met `Tab` key, de focus wordt verplaatst naar de juiste gebruikersinterface-elementen in de workflow om een interactieve video te maken.
   * De pagina Publiceren, de pagina Element bewerken, de pagina Slimme uitsnijdingen bewerken en de pagina Editor afbeeldingsset zijn verbeterd en voldoen nu aan de webstandaarden. Gebruikers met hulpprogramma&#39;s (AT) kunnen nu gemakkelijk door deze pagina&#39;s navigeren en er op reageren, zoals afbeeldingen uitsnijden.
   * Gebruikers kunnen nu beter met een toetsenbord navigeren.
   * Gebruikers van het toetsenbord en de schermlezer kunnen de uitsnijdfunctionaliteit gebruiken.
   * De gebruikers van het toetsenbord kunnen de hotspots beter beheren.

  Zie [Toegankelijkheid [!DNL Dynamic Media]](/help/assets/dynamic-media/accessibility-dm.md).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Release CIF Venia Reference Site - 2020.11.05 die de snelste versie CIF Core Components v1.5.0 bevat. Zie [CIF Venia-referentiegebied](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.27) voor meer informatie .

* Uitgegeven CIF Core Components v1.5.0. Zie [CIF kerncomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.5.0) voor meer informatie .

### Opgeloste problemen {#bug-fixes-commerce}

* GraphQL client config is niet goed gelezen wanneer de config niet rechtstreeks in de Sling CA config is opgegeven, maar in een van de bovenliggende configuraties. Dit is opgelost.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2020.11.0 is 12 november 2020.

### Nieuwe functies in [!DNL Cloud Manager] {#what-is-new-cm}

* Een nieuwe menuoptie **Lokale aanmelding** is nu beschikbaar voor gebruikers via de opties in het menu Omgeving op het tabblad **Omgevingen** kaart en **Omgevingen** samenvattingspagina&#39;s.
Zie [Omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md#login-locally) voor meer informatie .

* De **Meer informatie** is vernieuwd met nieuwe afbeeldingen in de gebruikersinterface.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* Voor het laden van afhankelijkheden die zijn uitgevoerd voordat de build werd uitgevoerd, moest een Maven-plug-in worden gedownload.
* Met de koppeling in de voettekst van Cloud Manager om een taal te selecteren, gaat u nu naar de juiste locatie.
* Soms wordt tijdens het scannen van code het SonarQube-proces niet gestart. Dit wordt nu automatisch gedetecteerd en er wordt geprobeerd opnieuw te starten.
* Alle bestaande productiepijpleidingen worden automatisch ingeschakeld met de stap Experience Audit.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* Er is ondersteuning toegevoegd voor het zoeken naar workflowinstanties op basis van workflowtitel, workflowmodel, status, initiator, Payload Path en Begindatum. Zie [Workflowinstanties zoeken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/workflows-administering.html).

### Synchronisatie van gebruikersgegevens op publicatieniveau {#user-sync}

* Gebruikersgegevens, waaronder profielkenmerken en groepslidmaatschappen, kunnen op de publicatielijst worden voortgezet. Meer informatie over deze functie vindt u in [Documentatie voor registratie, aanmelding en gebruikersprofiel](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md).

### SDK Build Analyzers {#analyzers}

De AEM as a Cloud Service SDK bouwt Analyzer Maven Plugin ontdekt problemen in een bepaald project, met inbegrip van ontbrekende gebiedsdelen. Het biedt ontwikkelaars de mogelijkheid om problemen tijdens lokale ontwikkeling op te sporen, ruim voordat ze met Cloud Manager naar een cloud-omgeving implementeren. Raadpleeg de documentatie voor meer informatie [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html#developing) en [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html#building-for-the-sdk).

### Overige {#others-foundation}

Nieuw [syntaxis &quot;httpd -t&quot;](/help/implementing/dispatcher/disp-overview.md#local-validation) controleren of de configuratie van apache en dispatcher is uitgevoerd tijdens de build van Cloud Manager, die ook kan worden uitgevoerd met AEM Dispatcher Tools van as a Cloud Service SDK.

## Inhoud overbrengen {#content-transfer-tool}

Volg deze sectie voor meer informatie over nieuwe functies en de updates voor [Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Release v1.1.12.

### Nieuwe functies {#what-is-new-ctt}

* De gebruikerservaring voor logbestanden is verbeterd. Tijdstempels toegevoegd aan extractie- en insluitingslogboeken. Bericht toegevoegd om aan te geven of de logbestanden leeg zijn.

### Opgeloste problemen {#ctt-bug-fixes}

* Met het gereedschap Inhoud overbrengen slaat u inhoudsbestanden over als de migratieset paden bevat met gedeeltelijk vergelijkbare bestandsnamen. Dit is opgelost.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa}

De datum van de Versie voor de Analysator van Beste praktijken is 13 November, 2020.

### Nieuwe functies in [!DNL Best Practices Analyzer] {#what-is-new-bpa}

* Cloud Readiness Analyzer is nu Best Practices Analyzer (BPA). BPA biedt een evaluatie van best practices voor uw huidige AEM-implementatie en helpt u te beoordelen of het mogelijk is van een bestaande AEM over te stappen op AEM as a Cloud Service.

* Er is een nieuwe detector toegevoegd om het gebruik van `java.io.InputStream`, die problemen kan veroorzaken als deze worden gebruikt in AEM as a Cloud Service.

### Opgeloste problemen {#bpa-bug-fixes}

* Bug veroorzaakt de positieve effecten van de *textfield, stichting* component was fixed.
