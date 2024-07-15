---
title: De Gids van de migratie aan Experience Manager as a Cloud Service voor Partners
description: De Gids van de migratie aan Experience Manager as a Cloud Service voor Partners
exl-id: 9d5a72b8-06af-4b82-ab20-e65aea7903b3
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1464'
ht-degree: 4%

---

# Migratiehandleiding voor Adobe Experience Manager as a Cloud Service for Partners {#Overview}

>[!CONTEXTUALHELP]
>id="aemcloud_migration_overview"
>title="Migratie naar AEM als cloudservice"
>abstract="Omlijnt de geadviseerde gefaseerde benadering van overgangs klanten van diverse plaatsingen van de Experience Manager aan Experience Manager as a Cloud Service en hulp bestaande klanten leveren verbonden, ononderbroken ervaringen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html" text="Nieuwe en andere functies?"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/introduction.html" text="Inleiding tot AEM as a Cloud Service."

Adobe Experience Manager (AEM) as a Cloud Service biedt een herarchitected basis voor Experience Manager, die is gebaseerd op een containergebaseerde infrastructuur, API-gestuurde ontwikkeling en het geleide DevOps-proces, waardoor marketers en ontwikkelaars altijd op de curve kunnen blijven vooruitlopen in innovaties op het gebied van het beheer van de gebruikerservaring.

Cloud Service combineert de rijke mogelijkheden en uitbreidbaarheid van Adobe Experience Manager buiten de box met de flexibiliteit van de moderne cloudnative architectuur die merken in staat stelt aan de voortdurend veranderende consumentenvraag te voldoen.

Deze één-pager schetst de geadviseerde gefaseerde benadering van overgangs klanten van diverse plaatsingen van de Experience Manager aan Experience Manager as a Cloud Service en de hulp bestaande klanten leveren verbonden, ononderbroken ervaringen op dit moderne, doelgericht-gebouwde platform voor ervaringsbeheer.

<!-- It primarily focuses on:
* Getting Started with Adobe Experience Manager as a Cloud Service
* Developer Journey in Adobe Experience Manager as a Cloud Service
* Moving to Adobe Experience Manager as a Cloud Service -->

Zie het onderstaande diagram voor een algemene weergave van de migratiereis.

![afbeelding](/help/journey-migration/assets/migration-process.png)

## Aan de slag met Adobe Experience Manager as a Cloud Service {#getting-started}

| Wat is anders? | Overzicht van architectuur |
|--------------------------|--------------------------|
| <ul><li>[ Moderne Architectuur ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/architecture.html)</li><li>[ Automatische Updates ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates.html)</li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html)</li><li>[ Microservices van Activa ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/asset-microservices-overview.html)</li><li>[ direct-Toegang binaire getallen ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/asset-microservices-overview.html)</li><li>[ Scheiding van code en inhoud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html)</li><li>[ Replicatie als Dienst ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/replication.html)</li><li>[ Admin console, Groep/Gebruikerslidmaatschap en ACLs ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html)</li></ul> | <ul><li>[ Inleiding aan AEM Architectuur ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-architecture.html#underlying-technology)</li><li>[ de Stapel van het Milieu ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/architecture.html)</li><li>[ Reeks van de Auteur ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html#underlying-technology)</li><li>[ Rij Publish ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html#underlying-technology)</li><li>[ Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html)</li><li>[ CDN ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html) </li><li>[ Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html) (CI/CD)</li><li>[ Identity Management ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html) via [ Admin Console ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html)</li><li>[ Dienst van de Asset compute ](https://experienceleague.adobe.com/docs/asset-compute/using/home.html)</li></ul> |

![AEM as a Cloud Service - Runtimearchitectuur](/help/overview/assets/concepts-03.png "AEM as a Cloud Service - Runtimearchitectuur")

<br>

## Developer Journey in Adobe Experience Manager as a Cloud Service {#developer-journey}

### Ontwikkelen

De grondbeginselen van codeontwikkeling zijn in Adobe Experience Manager as a Cloud Service vergelijkbaar met de oplossingen Adobe Experience Manager On Premise en Managed Services.

Ontwikkelaars schrijven code en testen deze lokaal, wat vervolgens wordt doorgegeven aan externe Adobe Experience Manager as a Cloud Service-omgevingen.

Zie zelf-hulp middelen over implementatie voor Experience Manager as a Cloud Service leren hoe te om uw as a Cloud Service plaatsing van de Experience Manager aan te passen.

| Local Development Setup | Informatie voordat je begint |
|-----------|------------|
| <ol><li>Herzie ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html) documentatie van SDK van 0} Adobe Experience Manager {om meer te leren.[</li><li>Controle [ installeert Dispatcher SDK ](https://video.tv.adobe.com/v/30601) om te begrijpen hoe te om Dispatcher SDK te installeren</li><li>Controle [ vormt Dispatcher SDK ](https://video.tv.adobe.com/v/30602) om op te begrijpen hoe te om Dispatcher SDK te vormen</li><li>De documentatie van de Opstelling van de Ontwikkeling van het overzicht [ Lokale ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html#local-development-environment-set-up) om meer te leren</li><li>Het vormen toegang tot Experience Manager [ lopen-door ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html#accessing)</li></ol> | <ol><li>[ Grondbeginselen van de Ontwikkeling ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html)</li><li>[ Richtlijnen van de Ontwikkeling ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html)</li><li>[ Begrijpend de Structuur van het Project van de Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html)</li><li>[ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)</li><li>[ Digitale Vervaging van de Stichting ](https://solutionpartners.adobe.com/content/dam/solution/en/spp_assets/restricted/community/community_31/digital_foundation_best_practices_and_documentation.zip)</li><li>[Stijlsysteem](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/features/style-system.html)</li><li>[ Bedekkingen ](/help/implementing/developing/introduction/overlays.md)</li><li>[ Experience Manager as a Cloud Service API verwijzing ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/)</li></ol> |

>[!TIP]
> Zie leerprogramma op hoe te [ ontwikkelen en WKND op lokale Experience Manager SDK opstellen ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

### Implementeren

Ontwikkelaars schrijven code en testen deze lokaal, wat vervolgens wordt doorgegeven aan externe AEM as a Cloud Service-omgevingen.

Cloud Manager, een optioneel hulpprogramma voor het leveren van inhoud voor Managed Services, is vereist. Dit is nu het enige mechanisme voor het implementeren van code in AEM as a Cloud Service-omgevingen.

Zie voor zelfhulp bronnen over het configureren en implementeren van AEM as a Cloud Service-omgevingen.

1. [ vorm de Pijpleidingen van CM ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/cicd-pipelines/introduction-ci-cd-pipelines.html)
   * Productiepijpleiding
   * Uitsluitend pijplijnen zonder productie en codekwaliteit
2. [ stel Code ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html) op
3. [ Begrijpend Uw Resultaten van de Test ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/test-results/overview-test-results.html)
4. **Toegang tot Logs**
   * [ via CM UI ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs.html)
   * [ via Adobe i/o cli ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html#debugging)
5. [ Verrichtingen en Onderhoud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/home.html)
   * [ het Vormen configuratie OSGI ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html)
   * [Back-up en herstel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/backup.html)

>[!TIP]
> Zie leerprogramma op hoe te [ WKND aan Experience Manager Cloud Service opstellen ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

### Help en bronnen

1. [ het Zuiveren uiteinden en trucs ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html#debugging-aem-as-a-cloud-service)
2. [Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html#debugging)
3. [ CRXDE Lite ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html) (slechts beschikbaar op lokale milieu&#39;s van SDK en van de Wolk van de Experience Manager Dev)
4. [ Logboeken en registreren ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html#debugging)
   * [ Logboeken van CM ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html#debugging) (bouwstijl-eenheid-test, code-aftasten, bouwt-beeld, stelt op)
   * [ Logboeken van de Experience Manager Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html#debugging) (aemerror, aemaccess, aemrequest, aemdispatcher, httpderror, httpaccess)
   * Lokale SDK-logbestanden (onder host:port/crx-quickstart/logs)

>[!NOTE]
> Voor extra hulp, kunt u willen:
>1. [ Contacteer het Team van de Steun van de Experience Manager ](https://experienceleague.adobe.com/docs/customer-one/using/home.html)
>2. Onderzoek [ de Gemeenschappen &amp; de Forums van de Experience Manager ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)

<br>

## Naar Adobe Experience Manager as a Cloud Service {#move-to-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_move_to_cloud"
>title="Naar Adobe Experience Manager as a Cloud Service"
>abstract="Deze één-pager schetst de geadviseerde gefaseerde benadering van overgangs klanten van diverse plaatsingen van de Experience Manager aan Experience Manager as a Cloud Service en de hulp bestaande klanten leveren verbonden, ononderbroken ervaringen op dit moderne, doelgericht-gebouwde platform voor ervaringsbeheer."

**de as a Cloud Service van de Experience Manager verstrekt een scalable, veilige, en mobiele technologiestichting voor Experience Manager Sites en Assets, toelatend marketers en IT om zich op het leveren van impactful ervaringen bij schaal te concentreren.**

Met Experience Manager as a Cloud Service, kunnen uw teams zich op het vernieuwen in plaats van planning voor productverbeteringen concentreren. Nieuwe productfuncties worden grondig getest en zonder onderbreking aan uw teams geleverd, zodat zij altijd toegang hebben tot de geavanceerde toepassing.

De overgang naar Cloud Service bestaat uit drie fasen: Planning, Executie en Post Go-live.
Voor een geslaagde en soepele overgang moet u zorgen voor een goede planning en volgt u de best practices die in deze gids worden beschreven.

In de onderstaande afbeelding ziet u een afbeelding op hoog niveau van de aanbevolen overgang naar Cloud Service.

![afbeelding](/help/journey-migration/assets/home-img1.png)

<br>

### Planning

Voordat u begint met de overgang naar de Cloud Service, dient u uzelf vertrouwd te maken met de Experience Manager as a Cloud Service en de opmerkelijke wijzigingen te bekijken die erin zijn aangebracht. U dient ook de functies te bekijken die zijn vervangen of vervangen.

<table>
<tr>
<td>Ontdekking en evaluatie van projecten</td>
<td><ul><li>Zie <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html"> Notable Veranderingen in as a Cloud Service Experience Manager </a> om de belangrijke verschillen tussen Adobe Experience Manager as a Cloud Service en Experience Manager 6.x te begrijpen.</li><li>Zie <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/deprecated-removed-features.html"> Vervangen Eigenschappen </a> om meer over eigenschappen en mogelijkheden te leren die als afgekeurd zijn gemerkt.</li><li>[Voor de Migratie van de Cloud Service slechts] het Assessing Cloud Service Readiness: stel <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html"> Analyzer van Beste praktijken (BPA) </a> op bronmilieu in werking </li><li>Voltooi een beoordeling tegen opmerkelijke veranderingen en verouderde eigenschappen in Experience Manager CS</li></ul></td>
</tr>
<tr>
<td>Controleren</td>
<td><ul><li>Op basis van detectie, oefeningen uitvoeren voor het schatten van de inspanning en het aanwenden van middelen</li></ul></td>
</tr>
<tr>
<td>Meetlat</td>
<td><ul><li><a href="https://experienceleague.adobe.com/welcome/aem/part6.html"> Vestig Project KPIs </a>, succescriteria en projectchronologie</li></ul></td>
</tr>
</table>

>[!NOTE]
>Het Rapport van de Analysator van Beste praktijken versnelt het proces om de tijd en de kosten te schatten die aan overgang aan AEM as a Cloud Service worden vereist door informatie te verstrekken die anders manueel zou moeten worden verzameld en worden geëvalueerd.


<br>

### Uitvoering

Alvorens u de fase van de Uitvoering van een project begint, zou u aan Cloud Service moeten worden ingezien. U moet zich ook vertrouwd maken met Cloud Manager. Dit is het mechanisme om projectcode aan een instantie van de Experience Manager Cloud Service op te stellen.

Cloud Manager stelt organisaties in staat zelf Experience Manager te beheren in de cloud. Het omvat een ononderbroken integratie en ononderbroken levering ([ CI/CD ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/overview/ci-cd-pipelines.html)) kader dat de teams van IT en de implementatiepartners de levering van aanpassingen of updates zonder prestaties of veiligheid te compromitteren laat versnellen.

#### Inhoud migreren

1. [ het Hulpmiddel van de Overdracht van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html#migration) : wordt gebruikt om bestaande inhoud over van een bron AEM instantie (op-gebouw of AMS) aan de instantie van doelAEM Cloud Service te bewegen.
2. [ Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html#package-manager) : gebruikt voor het invoeren en het uitvoeren van veranderlijke inhoud van de bewaarplaats.


#### Refactor/optimaliseren

| Aan de slag | Revisie- en reactorcode | Dispatcher Review |
|---|---|---|
| <ul><li>[ Lokale Dev opstelling ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html#local-development-environment-set-up)</li><li>[ Lokale Opstelling van Dispatcher ](https://video.tv.adobe.com/v/30602/)</li><li>[ compileert uw code gebruikend SDK API jar ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html)</li><li>[ Overzicht AEM Dev Richtlijnen ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html)<ul><li>Achtergrondtaken en langdurige taken</li><li>Verschuivende planners</li><li>Gebruik van invoerstroom &amp; meer</li></ul></li></ul> | <ul><li>Stel de [ Analysator van Beste praktijken (BPA) ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html) op bronmilieu in werking.[**slechts Migratie**]<ul><li>De Structurerende overwegingen van het project (die op [ worden gebaseerd Archetype van de Wolk ](https://github.com/adobe/aem-project-archetype))<ul><li>Scheiding van code en inhoud (Mutable versus Immuable)</li><li>[ de indexdefinities van de Douane ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html)</li><li>[ Runmodes van de Douane ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html)</li></ul></li></ul></li><li>Herzie en voer indien nodig wijzigingen uit</li><li>[ stelt ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) het op lokale SDK op</li><li>Rooktests uitvoeren via AEM SDK</li></ul> | <ul><li>Het overzicht {de configuraties van 0} Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html) voor refactoring[</li><li>Gebruik [ Dispatcher Converter ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/dispatcher-transformation-utility-tools.html) hulpmiddel waar aangewezen. [**slechts Migratie**]</li><li>Het testen kan worden uitgevoerd gebruikend [ Dispatcher SDK ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html#prerequisites)</li></ul> |

>[!TIP]
> De Klanten van Assets: De Werkschema&#39;s van Assets van het overzicht &amp; van de Refactor gebruikend [ het hulpmiddel van de Migratie van de Wolk van Activa ](https://github.com/adobe/aem-cloud-migration)


#### Implementatie/GoLive

1. [ opstellen aan Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/git-integration.html) git
2. De klantencode van de looppas door de [ Pijl van de Kwaliteit van Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/code-quality-testing.html)
3. [ opstellen aan het Milieu van de Ontwikkeling ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html#debugging)
4. [**migratie slechts**] de overdracht van de Inhoud gebruikend pakketten of [ het Hulpmiddel van de Overdracht van de Inhoud ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) (CTT)
5. Aanbevolen testcycli uitvoeren (rook, QA en meer)
6. Bevorderen tot de Cloud Manager Production Pipeline
7. Validatie van de rooktest
8. Go-Live

<br>

### Post Go-Live

In de fase na Go-Live moet u ervoor zorgen dat tijdelijke bestanden worden opgeschoond. Het is ook tijd om de best practices te evalueren voor continue ontwikkeling en voor het beheer van de logbestanden.

>[!TIP]
> Er zijn hulpprogramma&#39;s beschikbaar voor het oplossen van problemen in de AEM as a Cloud Service-omgeving
>1. [Developer Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html)
>2. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html)
>3. [Tool voor beheren van logbestanden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs.html)

<br>

### Hulpmiddelen &amp; Middelen

| Beoordeling | Refactoring | Modernisering van de Experience Manager | Inhoud migreren |
|------------|-------------|---------------------------------|-------------------|
| <ul><li>[ Analyzer van Beste praktijken ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html)</li></li> | <ul><li>[ Verenigde Insteekmodule van de Ervaring ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/unified-experience.html)</li></ul> | <ul><li>[ Statische malplaatjes aan editable malplaatjes ](https://opensource.adobe.com/aem-modernize-tools/pages/structure.html)</li><li>[ configuraties van het Ontwerp aan beleid ](https://opensource.adobe.com/aem-modernize-tools/pages/policy.html) <li>[ Componenten van de Stichting aan de Componenten van de Kern ](https://opensource.adobe.com/aem-modernize-tools/pages/component.html)</li><li>[ Klassieke UI aan aanraking-Toegelaten UI ](https://opensource.adobe.com/aem-modernize-tools/pages/all-in-one.html)</li></ul> | <ul><li>[ het Hulpmiddel van de Overdracht van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html)</li><li>[ de Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html#contentmanagement)</li></ul> |

>[!NOTE]
> Voor extra hulp, kunt u willen:
>1. [ Contacteer het Team van de Steun van de Experience Manager ](https://experienceleague.adobe.com/docs/customer-one/using/home.html)
>2. Onderzoek [ de Gemeenschappen &amp; de Forums van de Experience Manager ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)
