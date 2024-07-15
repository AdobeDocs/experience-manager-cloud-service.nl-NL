---
title: Nota's van de versie voor 2021.3.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release voor 2021.3.0."
exl-id: 0c07364c-ba25-4081-8e35-3c1c84ed556f
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>Hier kunt u navigeren om notities van eerdere versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2021.3.0 is 25 maart 2021.
De volgende release (2021.4.0) vindt plaats op 29 april 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* [ A Progressieve versie van de Web App (PWA) van een plaats ](/help/sites-cloud/authoring/sites-console/enable-pwa.md) kan nu op het projectniveau via eenvoudige configuratie worden toegelaten.
* Extensies inhoudsfragmentmodel - nu mogelijk om gegevenstypen met meerdere regels te definiëren als lijsten met meerdere velden.
* Verbeteringen in de Content Fragment Editor UX: geneste onderliggende fragmenten die nu worden weergegeven in de broodkruimel en verbeterde weergave van acties voor publiceren, opslaan en opslaan en afsluiten

## [!DNL Adobe Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#what-is-new-assets}

<!-- TBD: refine this list of features and enh. for Feb release.

Customers using the Connected Assets feature can now easily view and track assets used on remote Sites instances. This affords customers a complete view of being used across all Sites powered pages, allowing for better tracking, management, and brand consistency.  

Indicators for expired, approved, and rejected statuses now available for assets in Column view.

Ability to select a root path. select if a minimum number of tags is required. 

Add a Boolean or radio widget type to metadata schema setup. -->

* [!DNL Experience Manager] breidt de Connected Assets-functionaliteit uit om het gebruik van [!DNL Dynamic Media] -afbeeldingen in de ondersteunde kerncomponenten te ondersteunen. Zie [ gebruik Verbonden Assets ](/help/assets/use-assets-across-connected-assets-instances.md).
* Beheerders van Experience Managers kunnen het opnemen van grote hoeveelheden elementen op een bepaalde datum of tijd plannen. Ook, kunnen de beheerders terugkomende ingesties plannen die op datum en tijd worden gebaseerd. Zie [ bulkactiva opnemen ](/help/assets/add-assets.md#asset-bulk-ingestor).

### Opgeloste problemen in [!DNL Assets] {#bug-fixes-assets}

* De copyrightpagina wordt niet weergegeven wanneer u meerdere middelen met rechtenbeheer probeert te downloaden. (CQ-4314403)
* Wanneer u ervoor kiest een INDD-bestand te bewerken, verandert de resolutie onverwacht. (CQ-4317376)
* Alleen de laatste pagina van de InDesign Sjabloon staat in de PDF Rendition. (CQ-4317305)
* De tagkiezer kan lang worden geopend wanneer de kiezer deel uitmaakt van een complex metagegevensschema. (CQ-4316426)
* Wanneer u elementen uploadt met dezelfde bestandsnaam als een bestaand bestand, wordt het dialoogvenster voor naamconflict niet weergegeven om de gebruiker te vragen een versie te maken. (CQ-4315424)
* Eigenschappen van metagegevens van mappen kunnen worden ingesteld en opgeslagen via het pop-upmenu op de pagina Eigenschappen van een map. De selectie wordt opgeslagen in de gegevensopslagruimte en wordt niet weergegeven wanneer de eigenschappen van de metagegevens van de map opnieuw worden geopend. (CQ-4314429)
* Assets met bestandsnamen die spaties of speciale tekens bevatten, wordt geüpload via de browser. (CQ-4318381)

## [!DNL Adobe Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

AEM Forms heeft veel organisaties geholpen om in de loop der jaren geweldige ervaring op het gebied van instapweigering en inschrijving te bieden. Deze ervaringen hebben organisaties geholpen bij het omzetten van leads naar verkoop, het verwerken van vastgelegde klantgegevens, het leveren van responsieve ervaringen op basis van het profiel van het publiek en nog veel meer. AEM Forms is nu beschikbaar als cloudservice.

U kunt [ as a Cloud Service van AEM Forms ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html) gebruiken om digitale vormen tot stand te brengen, vormen met bestaande gegevensbronnen te verbinden, vormen met Adobe Sign te integreren om e-handtekeningen aan vormen toe te voegen, Document van Verslag te produceren (DoR) om ingediende vormen als PDF dossiers te archiveren. De service kan uw bestaande PDF forms ook converteren naar digitale formulieren. Naast de standaard AEM Forms-functies biedt de service verschillende mogelijkheden in de cloud, zoals automatisch schalen, geen downtime voor upgrades en ontwikkelomgeving in de cloud.

U kunt een demo indienen bij uw Adobe of u aanmelden voor de service.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Ondersteuning voor Adobe Commerce 2.4.2

* Productdetailcomponent kan nu worden gebruikt en geconfigureerd op elke inhoudspagina

* Release CIF Venia Reference Site - 2021.03.25 die de nieuwste versie CIF Core Components versie v1.9.0 bevat. Zie [ CIF de Plaats van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.03.25) voor meer details.

* Uitgegeven CIF Core Components v1.9.0. Zie [ CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.9.0) voor meer details.


## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.3.0 beschreven.

## Releasedatum {#release-date-cm-march}

De Releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.3.0 is 11 maart 2021.
De volgende release is gepland voor 8 april 2021.

### Wat is er nieuw? {#what-is-new-march}

* De klanten met milieu&#39;s met reeds bestaande configuraties van de Naam van het Domein van de Douane voor [ IP Lijsten van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md#pre-existing-cdn), [ SSL Certificaten ](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md#pre-existing-cdn) en [ Namen van het Domein van de Douane ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) zien een bericht over hun eerder bestaande configuraties en kunnen als gebruikersinterface zelf-dienen.

* Gebruikers met de vereiste machtigingen kunnen nu een programma bewerken, zodat zij het volgende op een zelfbedieningsmanier kunnen doen:

   * Voeg Sites-oplossing toe aan een bestaand programma met Assets of omgekeerd.
   * Sites of Assets verwijderen uit een bestaand programma met zowel Sites als Assets.
   * Voeg tweede, ongebruikte oplossingsrechten toe aan een bestaand programma of aan een nieuw programma.

* **AEM het etiket van de Update van de Duw** zal nu voor zowel *de Uitvoering van de Pijpleiding* en *Activiteiten* schermen worden getoond.

* Als een milieu wordt gehiberneerd maar er ook een beschikbare AEM update is, zal de **Gesamberneerde** status belangrijkheid over **beschikbare Update** nemen.

* Gebruikers kunnen hun Cloud Manager-rol(en) nu zien door de optie &#39;Cloud Manager-rol(en) weergeven&#39; te selecteren na naar het pictogram Gebruikersprofiel (rechtsboven) van Unified Shell te navigeren.

* De etiket **Toepassing voor Goedkeuring** is opnieuw geëtiketteerd aan **Goedkeuring van de Productie** voor grotere duidelijkheid.

* Het **etiket van de Versie** is opnieuw geëtiketteerd aan **Markering van het Git** in het scherm van de de pijpleiding van de Productie.

* De etiketten die het gedrag bepalen wanneer de belangrijke metriek niet de bepaalde drempel ontmoet zijn opnieuw geëtiketteerd om op hun ware gedrag te wijzen: **annuleert onmiddellijk** en **keurt onmiddellijk** goed.

* De lijsten met klasse- en methodeafgekeuringen zijn bijgewerkt op basis van versie `2021.3.4997.20210303T022849Z-210225` van de SDK van AEM Cloud Service.

* De pijpleiding van de Productie van Cloud Manager zal nu [ het Testen UI van de Douane ](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) vermogen omvatten.

### Opgeloste problemen {#bug-fixes-cm-march}

* Pakketversie is in sommige gevallen overgeslagen tijdens AEM upgrade.

* Bepaalde kwaliteitsproblemen zijn niet goed ontdekt wanneer pakketten in andere pakketten waren ingesloten.

* In duistere situaties, zou de standaardprogrammanaam die bij het openen van de Add dialoog van het Programma wordt geproduceerd een duplicaat van een bestaande programmanaam kunnen zijn.

* Wanneer de gebruiker bij gelegenheid vanaf de pagina voor de uitvoering van de pijpleiding navigeert onmiddellijk nadat een pijpleiding is gestart, wordt een foutbericht weergegeven met de mededeling dat de handeling is mislukt, hoewel de uitvoering daadwerkelijk wordt gestart.

* De bouwstijlstap werd onnodig opnieuw begonnen toen de klant bouwt in ongeldige pakketten resulteerde.

* Soms, kan de gebruiker een groene &quot;actieve&quot;status naast een IP Lijst van gewenste personen zien zelfs wanneer die configuratie niet werd opgesteld.

* Alle bestaande productiepijpleidingen worden automatisch ingeschakeld met de stap Experience Audit.

## Inhoud overbrengen {#content-transfer-tool}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.3.4 is 19 maart 2021.

### Opgeloste problemen {#bug-fixes-ctt}

* CTT heeft inhoud overgeslagen uit mappen met dezelfde naam, maar met een afbreekstreepje in de naam. Dit is opgelost.

### Releasedatum {#release-date-ctt-march}

De releasedatum voor Content Transfer Tool v1.3.0 is 4 maart 2021.

### Nieuw in gereedschap voor inhoudsoverdracht {#what-is-new-ctt-march}

* CTT wordt nu geïnstalleerd op `/apps` in plaats van `/libs` Bladwijzers in de browser naar bepaalde pagina&#39;s zijn mogelijk niet meer geldig.
* Wanneer CTT wordt geïnstalleerd, zal de gebruiker een extra niveau moeten navigeren om aan de pagina van de Overdracht van de Inhoud te krijgen. Zie [ Gebruikend het Hulpmiddel van de Overdracht van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html) voor meer details.

### Opgeloste problemen {#bug-fixes-ctt-march}

* Tijdens het migreren van inhoud van een specifiek pad, trok CTT zich aan niet-gerelateerde bronnen. Dit is opgelost

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.8 is 22 maart 2021.

### Nieuwe functies in Analyzer best practices {#what-is-new-bpa}

* Mogelijkheid om ACS-gemeenschappelijke bevindingen uit het BPA- rapport in het gebruikersinterface en uit het rapport uit te filteren dat als CSV- dossier wordt uitgevoerd.

## Gereedschappen voor het verfijnen van code {#code-refactoring-tools}

### Nieuw in de Hulpmiddelen van de Refactoring van de Code {#what-is-new-crt}

* Nieuwe en verbeterde functies voor Repository Modernizer. Zie [ Middel GitHub: Modernizer van de Bewaarplaats ](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) voor de recentste versie.
   * Normaliseer OSGi vormt (behalve vormen RepoInit) aan het aangewezen.cfg.json formaat.
   * Wijzig de naam van de OSGi config-mappen in de opgegeven indeling.
   * Genereer het project ui.apps.structure.
   * Maak de analysemodule.

* Nieuwe en verbeterde functies voor Dispatcher Converter. Zie [ Middel GitHub: Converter van Dispatcher ](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)
   * Het maken van afzonderlijke bestanden voor verschillende insluitingen in plaats van voor het uitlijnen van de inhoud.
   * Mogelijkheid om zowel het mappad van hosts als het pad naar de hostbestanden af te handelen.
   * De generatie van landbouwbedrijfdossiers met grote klantenconfiguraties in waaier van 600 en meer.
