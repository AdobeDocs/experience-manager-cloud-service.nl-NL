---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
translation-type: tm+mt
source-git-commit: 9a2b52a873e4e0662da252bba2af6ac2a46cd08e
workflow-type: tm+mt
source-wordcount: '1588'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als een Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] als Cloud Service weergegeven.

>[!NOTE]
>Vanuit deze locatie kunt u navigeren om notities van eerdere versies weer te geven. bijvoorbeeld voor die in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De Releasedatum voor [!DNL Adobe Experience Manager] als Cloud Service 2021.3.0 is 25 maart 2021.
De volgende release (2021.4.0) vindt plaats op 29 april 2021.

## [!DNL Adobe Experience Manager Sites] als Cloud Service  {#sites}

* [Een Progressieve versie van de Web App (PWA) van het Web van een ](/help/sites-cloud/authoring/features/enable-pwa.md) sitecan wordt nu toegelaten op het projectniveau via eenvoudige configuratie.
* Extensies inhoudsfragmentmodel - nu mogelijk om gegevenstypen met meerdere regels te definiëren als lijsten met meerdere velden.
* Verbeteringen in de Content Fragment Editor UX: geneste onderliggende fragmenten die nu worden weergegeven in de broodkruimel en verbeterde weergave van acties voor publiceren, opslaan en opslaan en afsluiten

## [!DNL Adobe Experience Manager Assets] als  [!DNL Cloud Service] {#assets}

### Nieuw in [!DNL Assets] {#what-is-new-assets}

<!-- TBD: refine this list of features and enh. for Feb release.

Customers using the Connected Assets feature can now easily view and track assets used on remote Sites instances. This affords customers a complete view of being used across all Sites powered pages, allowing for better tracking, management, and brand consistency.  

Indicators for expired, approved, and rejected statuses now available for assets in Column view.

Ability to select a root path. select if a minimum number of tags is required. 

Add a Boolean or radio widget type to metadata schema setup. -->

* [!DNL Experience Manager] breidt de Connected Assets-functionaliteit uit om het gebruik van  [!DNL Dynamic Media] afbeeldingen in de ondersteunde kerncomponenten te ondersteunen. Zie [Aangesloten elementen gebruiken](/help/assets/use-assets-across-connected-assets-instances.md).
* Beheerders van Experience Managers kunnen het opnemen van grote hoeveelheden elementen op een bepaalde datum of tijd plannen. Ook, kunnen de beheerders terugkomende ingesties plannen die op datum en tijd worden gebaseerd. Zie [bulkopname van elementen](/help/assets/add-assets.md#asset-bulk-ingestor).

### Opgeloste problemen in [!DNL Assets] {#bug-fixes-assets}

* De copyrightpagina wordt niet weergegeven wanneer u meerdere middelen met rechtenbeheer probeert te downloaden. (CQ-4314403)
* Wanneer u ervoor kiest een INDD-bestand te bewerken, verandert de resolutie onverwacht. (CQ-4317376)
* Alleen de laatste pagina van de InDesign-sjabloon staat in de PDF-vertoning. (CQ-4317305)
* De tagkiezer kan lang worden geopend wanneer de kiezer deel uitmaakt van een complex metagegevensschema. (CQ-4316426)
* Wanneer u elementen uploadt met dezelfde bestandsnaam als een bestaand bestand, wordt het dialoogvenster voor naamconflict niet weergegeven om de gebruiker te vragen een versie te maken. (CQ-4315424)
* Eigenschappen van metagegevens van mappen kunnen worden ingesteld en opgeslagen via het pop-upmenu op de pagina Eigenschappen van een map. De selectie wordt opgeslagen in de gegevensopslagruimte en wordt niet weergegeven wanneer de eigenschappen van de metagegevens van de map opnieuw worden geopend. (CQ-4314429)
* Elementen met bestandsnamen die spaties of speciale tekens bevatten, worden via de browser geüpload. (CQ-4318381)

## [!DNL Adobe Experience Manager Forms] als  [!DNL Cloud Service] {#forms}

AEM Forms heeft veel organisaties geholpen om in de loop der jaren geweldige ervaring op het gebied van instapweigering en inschrijving te bieden. Deze ervaringen hebben organisaties geholpen bij het omzetten van leads naar verkoop, het verwerken van vastgelegde klantgegevens, het leveren van responsieve ervaringen op basis van het profiel van het publiek en nog veel meer. AEM Forms is nu beschikbaar als cloudservice.

Met [AEM Forms kunt u als Cloud Service ](https://experienceleague.corp.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html) digitale formulieren maken, formulieren verbinden met bestaande gegevensbronnen, formulieren integreren met Adobe Sign om e-handtekeningen toe te voegen aan formulieren, Document of Record genereren (DoR) om verzonden formulieren als PDF-bestanden te archiveren. De service kan uw bestaande PDF forms ook converteren naar digitale formulieren. Naast de standaard AEM Forms-functies biedt de service verschillende mogelijkheden in de cloud, zoals automatisch schalen, geen downtime voor upgrades en ontwikkelomgeving in de cloud. Lees [dit blogbericht](https://blog.adobe.com/en/publish/2021/03/11/experience-manager-forms-as-a-cloud-service.html) voor meer informatie over de mogelijkheden en functies van AEM Forms als Cloud Service.

U kunt een demo afspelen bij uw Adobe-medewerker of u aanmelden voor de service.

## Adobe Experience Manager Commerce als Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Ondersteuning voor Magento 2.4.2

* Productdetailcomponent kan nu worden gebruikt en geconfigureerd op elke inhoudspagina

* Uitgebrachte CIF Venia Reference Site - 2021.03.25 met de nieuwste versie van CIF Core Components v1.9.0. Raadpleeg [CIF Venia Reference Site](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.03.25) voor meer informatie.

* Uitgebrachte CIF Core Components v1.9.0. Raadpleeg [CIF Core Components](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.9.0) voor meer informatie.


## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM beschreven als Cloud Service 2021.4.0 en 2021.3.0.

### Releasedatum {#release-date-cm-april}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.4.0 is 8 april 2021.
De volgende release is gepland voor 6 mei 2021.

### Wat is er nieuw?{#what-is-new-april}

* UI werkt aan de Add en Edit de werkschema&#39;s van het Programma om het intuïtiever te maken.

* Een gebruiker met vereiste toestemmingen kan het commerciële eindpunt via UI nu voorleggen.

* De variabelen van het milieu kunnen nu aan de specifieke dienst, of auteur of publiceren worden onderworpen. Vereist AEM versie `2021.03.5104.20210328T185548Z` of hoger.

* De **Manage knoop van Git** wordt getoond op de kaart van Pijpleidingen zelfs wanneer geen pijpleidingen zijn gevormd.

* De versie van het AEM projectarchetype dat door de Manager van de Wolk wordt gebruikt is bijgewerkt aan versie 27.

* Projecten in de Adobe I/O Developer Console die door Cloud Manager zijn gemaakt, kunnen niet langer per ongeluk worden bewerkt of verwijderd.

* Wanneer een gebruiker een nieuwe omgeving toevoegt, wordt hem meegedeeld dat een nieuwe omgeving niet naar een andere regio kan worden verplaatst.

* De variabelen van het milieu kunnen nu aan de specifieke dienst, of auteur of publiceren worden onderworpen. Vereist AEM versie 2021.03.5104.20210328T185548Z of hoger.

* Het foutbericht bij het starten van een pijpleiding wanneer een omgeving werd verwijderd, is verduidelijkt.

* OSGi-bundels die door Eclipse-projecten worden geleverd, zijn nu uitgesloten van regel `CQBP-84--dependencies`.

### Opgeloste problemen {#bug-fixes-cm-april}

* Wanneer het uitgeven van de de controlepagina van de Ervaring van een pijpleiding, zal een inputweg die met een schuine streep `( / )` begint niet meer resulteren in het plakken van de stap in wachtende status.

* Wanneer een nieuwe productiepijplijn wordt gecreeerd, als geen de opheffing van de inhoudscontrole door de gebruiker wordt toegevoegd, werd de standaardhomepage niet gecontroleerd.

* De kwesties voor `CloudServiceIncompatibleWorkflowProcess` hadden de onjuiste strengheid in het downloadbare dossier van de uitgave CSV.

* De `Runmode` controle produceerde valse positieven op niet omslagknopen.


### Releasedatum {#release-date-cm-march}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.3.0 is 11 maart 2021.

### Wat is er nieuw?{#what-is-new-march}

* Klanten met omgevingen met reeds bestaande aangepaste domeinnaamconfiguraties voor [IP-Lijsten van gewenste personen](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [SSL-certificaten](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) en [Aangepaste domeinnamen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) zullen een bericht zien over hun eerdere bestaande configuraties en zullen zichzelf kunnen bedienen via de gebruikersinterface.

* Gebruikers met de vereiste machtigingen kunnen nu een programma bewerken, zodat zij het volgende op een zelfbedieningsmanier kunnen doen:

   * Voeg de oplossing van Plaatsen aan een bestaand programma met Activa of vice versa toe.
   * Sites of middelen verwijderen uit een bestaand programma met zowel Sites als Middelen.
   * Voeg tweede, ongebruikte oplossingsrechten toe aan een bestaand programma of aan een nieuw programma.

* **AEM Push** Updatelabel wordt nu weergegeven voor zowel  *Pipeline* Execution als  ** Activiteitsschermen.

* Als een milieu gehiberneerd maar er ook een AEM beschikbare update is, zal **Gesambernated** status belangrijkheid over **beschikbare Update** nemen.

* Gebruikers kunnen nu hun rol(en) in de cloud Manager zien door de optie &#39;Rol(en) in de cloud-manager weergeven&#39; te selecteren nadat ze naar het pictogram Gebruikersprofiel (rechtsboven) van Unified Shell zijn genavigeerd.

* Het label **Goedkeuringsaanvraag** is voor meer duidelijkheid opnieuw gelabeld aan **Productiegoedkeuring**.

* Het **Version**-label is opnieuw gelabeld aan **Git Tag** in het uitvoeringsscherm van de productiepijplijn.

* De labels die het gedrag bepalen wanneer belangrijke metriek niet aan de bepaalde drempel voldoet, zijn opnieuw geëtiketteerd om op hun ware gedrag te wijzen: **Onmiddellijk annuleren** en **Direct goedkeuren**.

* De lijsten van de klasse en van de methodevervanging zijn bijgewerkt gebaseerd op versie `2021.3.4997.20210303T022849Z-210225` van de AEM Cloud Service SDK.

* De productiepijplijn van de Manager van de wolk zal [Aangepaste UI het Testen](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) capaciteit nu omvatten.

### Opgeloste problemen {#bug-fixes-cm-march}

* Pakketversie is in sommige gevallen overgeslagen tijdens AEM upgrade.

* Bepaalde kwaliteitsproblemen zijn niet goed ontdekt wanneer pakketten in andere pakketten waren ingesloten.

* In duistere situaties, zou de standaardprogrammanaam die bij het openen van de Add dialoog van het Programma wordt geproduceerd een duplicaat van een bestaande programmanaam kunnen zijn.

* Wanneer de gebruiker bij gelegenheid vanaf de pagina voor de uitvoering van de pijpleiding navigeert onmiddellijk nadat een pijpleiding is gestart, wordt een foutbericht weergegeven met de mededeling dat de handeling is mislukt, hoewel de uitvoering daadwerkelijk wordt gestart.

* De bouwstijlstap werd onnodig opnieuw begonnen toen de klant bouwt in ongeldige pakketten resulteerde.

* Soms, kan de gebruiker een groene &quot;actieve&quot;status naast een IP Lijst van gewenste personen zien zelfs wanneer die configuratie niet werd opgesteld.

* Alle bestaande productiepijpleidingen worden automatisch ingeschakeld met behulp van de stap Experience Audit.

## De tool Content Transfer {#content-transfer-tool}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.3.4 is 19 maart 2021.

### Opgeloste problemen {#bug-fixes-ctt}

* CTT heeft inhoud overgeslagen uit mappen met dezelfde naam, maar met een afbreekstreepje in de naam. Dit is opgelost.

### Releasedatum {#release-date-ctt-march}

De releasedatum voor Content Transfer Tool v1.3.0 is 4 maart 2021.

### Nieuw in gereedschap voor inhoudsoverdracht {#what-is-new-ctt-march}

* CTT installeert nu aan `/apps` in plaats van `/libs` Browser referenties aan bepaalde pagina&#39;s kan niet meer geldig zijn.
* Wanneer CTT wordt geïnstalleerd, zal de gebruiker een extra niveau moeten navigeren om aan de pagina van de Overdracht van de Inhoud te krijgen. Zie [Het gereedschap Inhoud overbrengen gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html) voor meer informatie.

### Opgeloste problemen {#bug-fixes-ctt-march}

* Tijdens het migreren van inhoud van een specifiek pad, trekt CTT zich aan niet-gerelateerde bronnen. Dit is opgelost

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.12 is 12 april 2021.

### Opgeloste problemen {#bug-fixes-bpa-april}

* Er zijn dubbele rijen aangetroffen in het BPA-rapport. Dit is opgelost.
* BPA UI op AEM versie 6.4.2 werpt een fout JS die de Generate knoop van het Rapport onbruikbaar maakte. Dit is opgelost


## Tools voor herstructurering van code {#code-refactoring-tools}

### Nieuw in de Hulpmiddelen {#what-is-new-crt} van de Refactoring van de Code

* Nieuwe en verbeterde functies voor Repository Modernizer. Verwijs naar [Middel GitHub: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) voor de nieuwste versie.
   * Normaliseer OSGi vormt (behalve vormen RepoInit) aan het aangewezen.cfg.json formaat.
   * Wijzig de naam van de OSGi config-mappen in de opgegeven indeling.
   * Genereer het project ui.apps.structure.
   * Maak de analysemodule.

* Nieuwe en verbeterde functies voor Dispatcher Converter. Verwijs naar [Middel GitHub: Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)
   * Het maken van afzonderlijke bestanden voor verschillende insluitingen in plaats van voor het uitlijnen van de inhoud.
   * Mogelijkheid om zowel het mappad van hosts als het pad naar de hostbestanden af te handelen.
   * De generatie van landbouwbedrijfdossiers met grote klantenconfiguraties in waaier van 600 en meer.
