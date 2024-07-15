---
title: Nota's van de versie voor 2020.11.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release voor 2020.11.0."
exl-id: 8066c0fb-c2f5-4625-9448-b0c74ff4e192
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1213'
ht-degree: 0%

---

# Opmerkingen bij de release voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor [!DNL Experience Manager] as a Cloud Service beschreven.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2020.11.0 is 2 december 2020.
De volgende release (20.12.0) vindt plaats op 17 december 2020

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Nieuwe functies in [!DNL Sites] {#what-is-new-sites}

* **[Lanceert het Beheer van de Hiërarchie ](/help/sites-cloud/authoring/launches/managing-pages.md) &amp; [ Toekomstige Tijdverdraaiing](/help/sites-cloud/authoring/launches/preview.md)**: Nieuwe UI om pagina&#39;s binnen een lancering toe te voegen/te verwijderen, en het doorbladeren van plaats met Tijdverdraaiing toont toekomstige staat van Lanceringen.

* **[Uitgebreide Modellen van het Fragment van de Inhoud &amp; Redacteur](/help/assets/content-fragments/content-fragments-models.md)**: De nieuwe opties voor inputbevestiging op diverse gegevenstypes, het verbeterde gegevenstype van de Opsomming met nieuwe vormvisualisaties, en de het modelnaam van het Fragment van de Inhoud wordt getoond en doorzoekbaar in Assets UI.

* **sorteer de Levende pagina&#39;s van het Exemplaar beschikbaar voor rollout**: Nieuwe optie om de Levende pagina&#39;s van het Exemplaar beschikbaar voor rollout te sorteren gebruikend [!UICONTROL Name], [!UICONTROL Last modified date], en [!UICONTROL Last rollout date] eigenschappen. De [!UICONTROL Last rollout date] voor een pagina is een nieuwe eigenschap.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Nieuw in [!DNL Assets] en [!DNL Dynamic Media] {#what-is-new-assets}

* **Bulk activaopname**: Verstrek klanten van de scalable, wolk-inheemse dienst die [!DNL Experience Manager] as a Cloud Service architectuur met inbegrip van activa microservices gebruikt. Belangrijke gebruiksgevallen zijn onder andere schaling op schaal met bewaking, rapportage en planning, terwijl de mogelijkheid bestaat om middelen eerst over te brengen naar de gegevensopslag in de cloud met gebruik van de gebruikelijke tools voor uploaden naar de cloud. Zie [ activa bulkingestor hulpmiddel ](/help/assets/add-assets.md#asset-bulk-ingestor).

  Dit hulpmiddel is voor systeembeheerder, adviseur, of de persona&#39;s van de implementatiepartner. Deze functie maakt het mogelijk om op grote schaal in te nemen en wordt bij voorkeur gebruikt tijdens de eerste opname of bij incidentele grote inname. Voor kleinere opnemingstaken, gebruik [[!DNL Experience Manager]  Desktop app ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html) of [ uploadt gebruikend Assets gebruikersinterface ](/help/assets/add-assets.md#upload-assets).

  ![ Configuratie van bulkimporteur ](/help/assets/assets/bulk-import-config-low-res.png)

* Gebruikers kunnen de digitale elementen nu sorteren in de Kaart- en kolomweergave.

  ![ soortactiva ](/help/assets/assets/asset-sort-options.png)

* De volgende verbeteringen zijn doorgevoerd voor toegankelijkheid in [!DNL Experience Manager Assets] in deze release. Voor meer informatie, zie [ toegankelijkheidseigenschappen in  [!DNL Assets]](/help/assets/accessibility.md).

   * Wanneer u door de tijdlijn navigeert met een toetsenbord, kunt u met de toets Esc de optie Alles tonen samenvouwen zonder de focus te verliezen.
   * Wanneer u navigeert met de Tab-toets op het toetsenbord, blijft het tagveld actief nadat u de laatste tag uit de toegevoegde tags hebt verwijderd.
   * [!DNL Experience Manager] -componenten bevatten nu de juiste informatie voor de naam, rol en waarde die door schermlezers moeten worden gebruikt.
   * Nadat u de keuzelijst Type/Grootte, keuzelijst Koppeling, keuzelijst Taal of Tekstbewerking hebt verwijderd, keert de toetsenbordfocus terug naar de volgende of vorige gebruikersinterface-elementen of naar een meer relevant gebruikersinterface-element.
   * Als u de aanwijzer op opties plaatst, worden er tips zoals Selecteren en Downloaden weergegeven. Gebruikers die een schermvergroting gebruiken, zien de miniaturen van het bestand mogelijk niet vanwege deze tips. Nu is het mogelijk om de focus te behouden nadat u de optie hebt verwijderd met de toets `Escape` .
   * Wanneer u een rastercel selecteert uit het raster dat aanwezig is op de pagina, wordt de focus verschoven naar de actiebalk die op het scherm wordt weergegeven.
   * Visuele gebruikers kunnen onderscheid maken tussen normale tekst en een koppeling, omdat er visuele aanwijzingen (onderstreping en chevron-pictogram) worden weergegeven voor koppelingen naar alle oplossingen op de startpagina van [!DNL Experience Manager] .

* **de Reeks van de Partij vooraf instelt in Dynamic Media**: Nu kunt u de verwezenlijking en de organisatie van veelvoudige activa in een beeldreeks automatiseren of draaien die op het tijdstip wordt geplaatst u activa dossiers aan een omslag of individueel uploadt of bulkingestitie gebruikt.

  Zie [ Ongeveer Geplaatste Partij vooraf instelt ](/help/assets/dynamic-media/batch-set-presets-dm.md).

* De volgende toegankelijkheidsverbeteringen zijn nu beschikbaar in [!DNL Dynamic Media] :

   * Schermlezers (JAWS, Narrator) vertellen de naam, de rol en de status van de menu-items in de menuoptie Grootte insluiten.
   * Gebruikers kunnen met de toets `Tab` door het dialoogvenster E-mailkoppeling navigeren.
   * De workflow voor het maken van videocoderingsprofielen is gebruiksvriendelijker gezien de schermlezerverbetering.
   * Wanneer u navigeert met de `Tab` -toets, wordt de focus verplaatst naar de juiste gebruikersinterface-elementen in de workflow om een interactieve video te maken.
   * De Publish-pagina, de pagina Element bewerken, de pagina Slimme uitsnijdingen bewerken en de pagina Editor afbeeldingsset zijn verbeterd en voldoen nu aan de webstandaarden. Gebruikers met hulpprogramma&#39;s (AT) kunnen nu gemakkelijk door deze pagina&#39;s navigeren en er op reageren, zoals afbeeldingen uitsnijden.
   * Gebruikers kunnen nu beter met een toetsenbord navigeren.
   * Gebruikers van het toetsenbord en de schermlezer kunnen de uitsnijdfunctionaliteit gebruiken.
   * De gebruikers van het toetsenbord kunnen de hotspots beter beheren.

  Zie [ Toegang in  [!DNL Dynamic Media]](/help/assets/dynamic-media/accessibility-dm.md).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Release CIF Venia Reference Site - 2020.11.05 die de snelste versie CIF Core Components v1.5.0 bevat. Zie [ CIF de Plaats van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.27) voor meer details.

* Uitgegeven CIF Core Components v1.5.0. Zie [ CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.5.0) voor meer details.

### Opgeloste problemen {#bug-fixes-commerce}

* GraphQL client config is niet goed gelezen wanneer de config niet rechtstreeks in de Sling CA config is opgegeven, maar in een van de bovenliggende configuraties. Dit is opgelost.

## Cloud Manager {#cloud-manager}

### Releasedatum {#release-date-cm}

De Releasedatum voor Cloud Manager in AEM as a Cloud Service 2020.11.0 is 12 november 2020.

### Nieuwe functies in [!DNL Cloud Manager] {#what-is-new-cm}

* Een nieuwe menuoptie **Lokale Login** is nu beschikbaar aan gebruikers van de opties van het milieumenu op de **3} kaart van Milieu&#39;s {en** summiere pagina&#39;s van Milieu **.**
Zie [ het Leiden Milieu ](/help/implementing/cloud-manager/manage-environments.md#login-locally) voor meer details.

* Het **Leer** lusje in Cloud Manager is verfrist met nieuwe beelden in UI.

### Opgeloste problemen {#bug-fixes-cloud-manager}

* Voor het laden van afhankelijkheden die zijn uitgevoerd voordat de build werd uitgevoerd, moest een Maven-plug-in worden gedownload.
* Met de koppeling in de voettekst van Cloud Manager waarmee u een taal kunt selecteren, navigeert u nu naar de juiste locatie.
* Soms wordt tijdens het scannen van code het SonarQube-proces niet gestart. Dit wordt nu automatisch gedetecteerd en er wordt geprobeerd opnieuw te starten.
* Alle bestaande productiepijpleidingen worden automatisch ingeschakeld met de stap Experience Audit.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* Er is ondersteuning toegevoegd voor het zoeken naar workflowinstanties op basis van workflowtitel, workflowmodel, status, initiator, Payload Path en Begindatum. Zie {de Instanties van het Werkschema van 0} Onderzoek ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/workflows-administering.html).[

### Synchronisatie van gebruikersgegevens op Publish-niveau {#user-sync}

* Gebruikersgegevens, waaronder profielkenmerken en groepslidmaatschappen, kunnen op de publicatielijst worden voortgezet. Leer meer over deze eigenschap in [ Registratie, Login, en de documentatie van het Profiel van de Gebruiker ](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md).

### SDK Build Analyzers {#analyzers}

De AEM as a Cloud Service SDK Build Analyzer Maven Plugin ontdekt problemen in een bepaald project, met inbegrip van ontbrekende gebiedsdelen. Het biedt ontwikkelaars de mogelijkheid om problemen tijdens lokale ontwikkeling te ontdekken, ruim voordat ze met Cloud Manager naar Cloud-omgevingen implementeren. Voor meer informatie, zie de documentatie [ hier ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html#developing) en [ ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html#building-for-the-sdk).

### Overige {#others-foundation}

De nieuwe [ &quot;httpd -t&quot;syntaxis ](/help/implementing/dispatcher/disp-overview.md#local-validation) controle voor apache en verzender configuratie die tijdens de bouw van Cloud Manager wordt uitgevoerd, die ook kan worden in werking gesteld gebruikend de Hulpmiddelen van Dispatcher van AEM as a Cloud Service SDK.

## Inhoud overbrengen {#content-transfer-tool}

Volg deze sectie om over te leren wat nieuw en de updates voor [ het Hulpmiddel van de Overdracht van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Versie v1.1.12 is.

### Nieuwe functies {#what-is-new-ctt}

* De gebruikerservaring voor logbestanden is verbeterd. Tijdstempels toegevoegd aan extractie- en insluitingslogboeken. Bericht toegevoegd om aan te geven of de logbestanden leeg zijn.

### Opgeloste problemen {#ctt-bug-fixes}

* Met het gereedschap Inhoud overbrengen slaat u inhoudsbestanden over als de migratieset paden bevat met gedeeltelijk vergelijkbare bestandsnamen. Dit is opgelost.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa}

De datum van de Versie voor de Analysator van Beste praktijken is 13 November, 2020.

### Nieuwe functies in [!DNL Best Practices Analyzer] {#what-is-new-bpa}

* Cloud Readiness Analyzer is nu Best Practices Analyzer (BPA). BPA biedt een evaluatie van best practices voor uw huidige AEM-implementatie en helpt u te beoordelen of het mogelijk is van een bestaande AEM over te stappen op AEM as a Cloud Service.

* Er is een nieuwe detector toegevoegd om het gebruik van `java.io.InputStream` te detecteren. Dit kan problemen veroorzaken bij gebruik in AEM as a Cloud Service.

### Opgeloste problemen {#bpa-bug-fixes}

* Bug die de positieven met betrekking tot de *textfield stichting* veroorzaakte component vast.
