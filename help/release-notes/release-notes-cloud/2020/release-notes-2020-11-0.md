---
title: Release-aantekeningen voor 2020.11.0-release van [!DNL Adobe Experience Manager] als Cloud Service.
description: '[!DNL Adobe Experience Manager] als opmerkingen bij de Cloud Service voor 2020.11.0.'
translation-type: tm+mt
source-git-commit: c0db892d58f762bd5659596371ece86950e9cdd7
workflow-type: tm+mt
source-wordcount: '1259'
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

De releasedatum voor Cloud Manager in AEM als Cloud Service 2020.11.0 is 12 november 2020.

### Nieuw in [!DNL Cloud Manager] {#what-is-new-cm}

* Een nieuwe menuoptie **Lokale aanmelding** is nu beschikbaar voor gebruikers via de opties in het menu Omgeving op de **Kaart met omgevingen** en de overzichtspagina&#39;s **Omgevingen**.
Raadpleeg [Omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md##login-locally) voor meer informatie.

* Het tabblad **Leren** in Cloud Manager is vernieuwd en bevat nieuwe afbeeldingen in de gebruikersinterface.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* Voor het laden van afhankelijkheden die zijn uitgevoerd voordat de build werd uitgevoerd, moest een Maven-plug-in worden gedownload.
* Met de koppeling in de voettekst van Cloud Manager om een taal te selecteren, gaat u nu naar de juiste locatie.
* Soms wordt tijdens het scannen van code het SonarQube-proces niet gestart. Dit wordt nu automatisch gedetecteerd en er wordt geprobeerd opnieuw te starten.
* Alle bestaande productiepijpleidingen worden automatisch ingeschakeld met behulp van de stap Experience Audit.

## Adobe Experience Manager als Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* Er is ondersteuning toegevoegd voor het zoeken naar workflowinstanties op basis van workflowtitel, workflowmodel, status, initiator, Payload Path en Begindatum. Zie [Workflowinstanties zoeken](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/administering/workflows-administering.html).

### Synchronisatie van gebruikersgegevens op publicatieniveau {#user-sync}

* Gebruikersgegevens, waaronder profielkenmerken en groepslidmaatschappen, kunnen op de publicatielijst worden voortgezet. Meer informatie over deze functie vindt u in de documentatie [Registratie, aanmelding en gebruikersprofiel](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md).

### SDK Build Analyzers {#analyzers}

De AEM als Cloud Service SDK bouwt Analyzer Maven Plugin ontdekt problemen in een bepaald project, met inbegrip van ontbrekende gebiedsdelen. Het biedt ontwikkelaars de mogelijkheid om problemen tijdens lokale ontwikkeling op te sporen, ruim voordat ze met Cloud Manager naar een cloud-omgeving implementeren. Zie de documentatie [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=en#developing) en [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#building-for-the-sdk) voor meer informatie.

### Overige{#others-foundation}

Nieuwe [&quot;httpd -t&quot;syntaxis](/help/implementing/dispatcher/disp-overview.md#local-validation) controle op apache en verzender configuratie uitgevoerd tijdens de Bouwstijl van de Manager van de Wolk, die ook kan worden in werking gesteld gebruikend AEM als de Hulpmiddelen van de Verzender van SDK van de Cloud Service.

## De tool Content Transfer {#content-transfer-tool}

Volg deze sectie om te leren over wat nieuw is en de updates voor [Content Transfer Tool](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Release v1.1.12.

### Nieuwe functies {#what-is-new-ctt}

* De gebruikerservaring voor logbestanden is verbeterd. Tijdstempels toegevoegd aan extractie- en insluitingslogboeken. Bericht toegevoegd om aan te geven of de logbestanden leeg zijn.

### Opgeloste problemen {#ctt-bug-fixes}

* Met het gereedschap Inhoud overbrengen slaat u inhoudsbestanden over als de migratieset paden bevat met gedeeltelijk vergelijkbare bestandsnamen. Dit is opgelost.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa}

De datum van de Versie voor de Analysator van Beste praktijken is 13 November, 2020.

### Nieuw in [!DNL Best Practices Analyzer] {#what-is-new-bpa}

* Cloud Readiness Analyzer is nu Best Practices Analyzer (BPA). BPA verstrekt een beste praktijkbeoordeling van uw huidige AEM implementatie en helpt de bereidheid beoordelen om van een bestaande AEM instantie aan AEM als Cloud Service over te gaan.

* Er is een nieuwe detector toegevoegd om het gebruik van `java.io.InputStream` te detecteren, wat problemen kan veroorzaken als AEM als Cloud Service wordt gebruikt.

### Opgeloste problemen {#bpa-bug-fixes}

* Fout die de positieven met betrekking tot *textfield foundation* component veroorzaakte werd bevestigd.
