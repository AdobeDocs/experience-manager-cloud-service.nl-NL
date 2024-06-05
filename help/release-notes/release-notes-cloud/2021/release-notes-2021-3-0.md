---
title: Opmerkingen bij de release 2021.3.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release 2021.3.0."
exl-id: 0c07364c-ba25-4081-8e35-3c1c84ed556f
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>Hier kunt u navigeren om notities van eerdere versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2021.3.0 is 25 maart 2021.
De volgende release (2021.4.0) vindt plaats op 29 april 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* [Een progressieve Web App (PWA)-versie van een site](/help/sites-cloud/authoring/sites-console/enable-pwa.md) kan nu op projectniveau via eenvoudige configuratie worden toegelaten.
* Extensies inhoudsfragmentmodel - nu mogelijk om gegevenstypen met meerdere regels te definiëren als lijsten met meerdere velden.
* Verbeteringen in de Content Fragment Editor UX: geneste onderliggende fragmenten die nu worden weergegeven in de broodkruimel en verbeterde weergave van acties voor publiceren, opslaan en opslaan en afsluiten

## [!DNL Adobe Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#what-is-new-assets}

<!-- TBD: refine this list of features and enh. for Feb release.

Customers using the Connected Assets feature can now easily view and track assets used on remote Sites instances. This affords customers a complete view of being used across all Sites powered pages, allowing for better tracking, management, and brand consistency.  

Indicators for expired, approved, and rejected statuses now available for assets in Column view.

Ability to select a root path. select if a minimum number of tags is required. 

Add a Boolean or radio widget type to metadata schema setup. -->

* [!DNL Experience Manager] breidt de Connected Assets-functionaliteit uit om het gebruik van [!DNL Dynamic Media] afbeeldingen in de ondersteunde kerncomponenten. Zie [Aangesloten elementen gebruiken](/help/assets/use-assets-across-connected-assets-instances.md).
* Beheerders van Experience Managers kunnen het opnemen van grote hoeveelheden elementen op een bepaalde datum of tijd plannen. Ook, kunnen de beheerders terugkomende ingesties plannen die op datum en tijd worden gebaseerd. Zie [bulkasset-opname](/help/assets/add-assets.md#asset-bulk-ingestor).

### Bugfixes in [!DNL Assets] {#bug-fixes-assets}

* De copyrightpagina wordt niet weergegeven wanneer u meerdere middelen met rechtenbeheer probeert te downloaden. (CQ-4314403)
* Wanneer u ervoor kiest een INDD-bestand te bewerken, verandert de resolutie onverwacht. (CQ-4317376)
* Alleen de laatste pagina van de InDesign Sjabloon staat in de PDF Rendition. (CQ-4317305)
* De tagkiezer kan lang worden geopend wanneer de kiezer deel uitmaakt van een complex metagegevensschema. (CQ-4316426)
* Wanneer u elementen uploadt met dezelfde bestandsnaam als een bestaand bestand, wordt het dialoogvenster voor naamconflict niet weergegeven om de gebruiker te vragen een versie te maken. (CQ-4315424)
* Eigenschappen van metagegevens van mappen kunnen worden ingesteld en opgeslagen via het pop-upmenu op de pagina Eigenschappen van een map. De selectie wordt opgeslagen in de gegevensopslagruimte en wordt niet weergegeven wanneer de eigenschappen van de metagegevens van de map opnieuw worden geopend. (CQ-4314429)
* Elementen met bestandsnamen die spaties of speciale tekens bevatten, worden via de browser geüpload. (CQ-4318381)

## [!DNL Adobe Experience Manager Forms] als [!DNL Cloud Service] {#forms}

AEM Forms heeft veel organisaties geholpen om in de loop der jaren geweldige ervaring op het gebied van instapweigering en inschrijving te bieden. Deze ervaringen hebben organisaties geholpen bij het omzetten van leads naar verkoop, het verwerken van vastgelegde klantgegevens, het leveren van responsieve ervaringen op basis van het profiel van het publiek en nog veel meer. AEM Forms is nu beschikbaar als cloudservice.

U kunt [AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html) Als u digitale formulieren wilt maken, sluit u formulieren aan op bestaande gegevensbronnen, integreert u formulieren met Adobe Sign om e-handtekeningen aan formulieren toe te voegen, genereert u Document of Record (DoR) om verzonden formulieren als PDF-bestanden te archiveren. De service kan uw bestaande PDF forms ook converteren naar digitale formulieren. Naast de standaard AEM Forms-functies biedt de service verschillende mogelijkheden in de cloud, zoals automatisch schalen, geen downtime voor upgrades en ontwikkelomgeving in de cloud.

U kunt een demo indienen bij uw Adobe of u aanmelden voor de service.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Ondersteuning voor Adobe Commerce 2.4.2

* Productdetailcomponent kan nu worden gebruikt en geconfigureerd op elke inhoudspagina

* Release CIF Venia Reference Site - 2021.03.25 die de nieuwste versie CIF Core Components versie v1.9.0 bevat. Zie [CIF Venia-referentiegebied](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.03.25) voor meer informatie .

* Uitgegeven CIF Core Components v1.9.0. Zie [CIF kerncomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.9.0) voor meer informatie .


## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.3.0 beschreven.

## Releasedatum {#release-date-cm-march}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.3.0 is 11 maart 2021.
De volgende release is gepland voor 8 april 2021.

### Wat is er nieuw? {#what-is-new-march}

* Klanten met omgevingen met bestaande aangepaste domeinnaamconfiguraties voor [IP-Lijsten van gewenste personen](/help/implementing/cloud-manager/ip-allow-lists/managing-ip-allow-lists.md#pre-existing-cdn), [SSL-certificaten](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md#pre-existing-cdn) en [Aangepaste domeinnamen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) zie een bericht over hun eerder bestaande configuraties en kan als gebruikersinterface zelf-dienen.

* Gebruikers met de vereiste machtigingen kunnen nu een programma bewerken, zodat zij het volgende op een zelfbedieningsmanier kunnen doen:

   * Voeg de oplossing van Plaatsen aan een bestaand programma met Activa toe of omgekeerd.
   * Sites of middelen verwijderen uit een bestaand programma met zowel sites als middelen.
   * Voeg tweede, ongebruikte oplossingsrechten toe aan een bestaand programma of aan een nieuw programma.

* **AEM bijwerken** label wordt nu weergegeven voor beide *Uitvoering pijpleiding* en *Activiteit* schermen.

* Als een omgeving is gehiberneerd maar er ook een AEM update beschikbaar is, kunt u het **Gesamberneerd** status heeft voorrang op **Update beschikbaar**.

* Gebruikers kunnen nu hun rol(en) in de cloud Manager zien door de optie &#39;Rol(en) in de cloud-manager weergeven&#39; te selecteren nadat ze naar het pictogram Gebruikersprofiel (rechtsboven) van Unified Shell zijn gegaan.

* Het label **Goedkeuringsaanvraag** is opnieuw gelabeld aan **Erkenning van productie** voor meer duidelijkheid.

* De **Versie** label is opnieuw gelabeld aan **Git-tag** in het scherm Productiepijpleiding.

* De labels die het gedrag bepalen wanneer belangrijke metriek niet aan de bepaalde drempel voldoet, zijn opnieuw geëtiketteerd om op hun ware gedrag te wijzen: **Direct annuleren** en **Direct goedkeuren**.

* De lijsten met klassen en methoden zijn bijgewerkt op basis van versie `2021.3.4997.20210303T022849Z-210225` van de SDK van AEM Cloud Service.

* De productiepijplijn van Cloud Manager wordt nu opgenomen [Aangepaste UI-tests](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) capaciteit.

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

* CTT wordt nu geïnstalleerd op `/apps` in plaats van `/libs` Browserbladwijzers naar bepaalde pagina&#39;s zijn mogelijk niet meer geldig.
* Wanneer CTT wordt geïnstalleerd, zal de gebruiker een extra niveau moeten navigeren om aan de pagina van de Overdracht van de Inhoud te krijgen. Zie [Het gereedschap Inhoud overbrengen gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html) voor meer informatie .

### Opgeloste problemen {#bug-fixes-ctt-march}

* Tijdens het migreren van inhoud van een specifiek pad, trok CTT zich aan niet-gerelateerde bronnen. Dit is opgelost

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.8 is 22 maart 2021.

### Nieuwe functies in Analyzer best practices {#what-is-new-bpa}

* Mogelijkheid om ACS-gemeenschappelijke bevindingen uit het BPA- rapport in het gebruikersinterface en uit het rapport uit te filteren dat als CSV- dossier wordt uitgevoerd.

## Gereedschappen voor het verfijnen van code {#code-refactoring-tools}

### Nieuw in de Hulpmiddelen van de Refactoring van de Code {#what-is-new-crt}

* Nieuwe en verbeterde functies voor Repository Modernizer. Zie [GitHub Resource: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) voor de meest recente versie.
   * Normaliseer OSGi vormt (behalve vormen RepoInit) aan het aangewezen.cfg.json formaat.
   * Wijzig de naam van de OSGi config-mappen in de opgegeven indeling.
   * Genereer het project ui.apps.structure.
   * Maak de analysemodule.

* Nieuwe en verbeterde functies voor Dispatcher Converter. Zie [GitHub Resource: Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)
   * Het maken van afzonderlijke bestanden voor verschillende insluitingen in plaats van voor het uitlijnen van de inhoud.
   * Mogelijkheid om zowel het mappad van hosts als het pad naar de hostbestanden af te handelen.
   * De generatie van landbouwbedrijfdossiers met grote klantenconfiguraties in waaier van 600 en meer.
