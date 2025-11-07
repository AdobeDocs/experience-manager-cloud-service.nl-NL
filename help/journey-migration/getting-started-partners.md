---
title: Migratiehandleiding voor Experience Manager as a Cloud Service for Partners
description: Migratiehandleiding voor Experience Manager as a Cloud Service for Partners
exl-id: 9d5a72b8-06af-4b82-ab20-e65aea7903b3
feature: Migration
role: Admin
source-git-commit: 2e257634313d3097db770211fe635b348ffb36cf
workflow-type: tm+mt
source-wordcount: '1471'
ht-degree: 4%

---

# Migratiehandleiding voor Adobe Experience Manager as a Cloud Service for Partners {#Overview}

>[!CONTEXTUALHELP]
>id="aemcloud_migration_overview"
>title="Migratie naar AEM als cloudservice"
>abstract="Geeft een overzicht van de aanbevolen gefaseerde aanpak voor klanten van verschillende Experience Manager-implementaties naar Experience Manager as a Cloud Service en helpt bestaande klanten verbonden, continue ervaringen te leveren"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html" text="Nieuwe en andere functies?"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/introduction.html" text="Inleiding tot AEM as a Cloud Service."

Adobe Experience Manager (AEM) as a Cloud Service biedt een bijgewerkte architectuur voor Experience Manager. Deze basis is gebaseerd op een containergebaseerde infrastructuur, API-gestuurde ontwikkeling en het geleide DevOps-proces. Dit staat marketers en ontwikkelaars toe om voor de kromme in het beheerinnovaties van de klantenervaring te blijven.

Cloud Service combineert de rijke externe mogelijkheden en uitbreidbaarheid van Adobe Experience Manager met de flexibiliteit van de moderne cloud-native architectuur, waardoor merken kunnen voldoen aan de voortdurend veranderende consumentenvraag.

Deze pagina beschrijft de gefaseerde aanpak die wordt aanbevolen om klanten over te stappen van vorige Experience Manager-implementaties naar Experience Manager as a Cloud Service. Het nieuwe, doelgerichte platform helpt u verbonden, continue ervaringen te bieden.

<!-- It primarily focuses on:
* Getting Started with Adobe Experience Manager as a Cloud Service
* Developer Journey in Adobe Experience Manager as a Cloud Service
* Moving to Adobe Experience Manager as a Cloud Service -->

Zie het onderstaande diagram voor een algemene weergave van de migratiereis.

![&#x200B; Algemene vertegenwoordiging van de migratiereis &#x200B;](/help/journey-migration/assets/migration-process.png)

## Aan de slag met Adobe Experience Manager as a Cloud Service {#getting-started}

| Wat is anders? | Overzicht van architectuur |
|--------------------------|--------------------------|
| <ul><li>[&#x200B; Moderne Architectuur &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/architecture.html)</li><li>[&#x200B; Automatische Updates &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/aem-version-updates.html)</li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html)</li><li>[&#x200B; Microservices van Activa &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/asset-microservices-overview.html)</li><li>[&#x200B; direct-Toegang binaire getallen &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/asset-microservices-overview.html)</li><li>[&#x200B; Scheiding van code en inhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html)</li><li>[&#x200B; Replicatie als Dienst &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/replication.html)</li><li>[&#x200B; Admin console, Groep/Gebruikerslidmaatschap en ACLs &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html)</li></ul> | <ul><li>[&#x200B; Inleiding aan de Architectuur van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-architecture.html#underlying-technology)</li><li>[&#x200B; de Stapel van het Milieu &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/architecture.html)</li><li>[&#x200B; Reeks van de Auteur &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html#underlying-technology)</li><li>[&#x200B; publiceer Rij &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html#underlying-technology)</li><li>[&#x200B; Dispatcher &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html)</li><li>[&#x200B; CDN &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html) </li><li>[&#x200B; Cloud Manager &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html) (CI/CD)</li><li>[&#x200B; Identity Management &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html) via [&#x200B; Admin Console &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html)</li><li>[&#x200B; de Dienst van Asset Compute &#x200B;](https://experienceleague.adobe.com/docs/asset-compute/using/home.html)</li></ul> |

![AEM as a Cloud Service - Runtimearchitectuur](/help/overview/assets/concepts-03.png "AEM as a Cloud Service - Runtimearchitectuur")

<br>

## Developer Journey in Adobe Experience Manager as a Cloud Service {#developer-journey}

### Ontwikkelen

De grondbeginselen van codeontwikkeling in Adobe Experience Manager as a Cloud Service zijn vergelijkbaar met die in de oplossingen Adobe Experience Manager On Premise en Managed Services.

Ontwikkelaars schrijven code en testen deze lokaal en drukken deze vervolgens naar externe Adobe Experience Manager as a Cloud Service-omgevingen.

Zie de hulpmiddelen voor zelfhulp over implementatie voor Experience Manager as a Cloud Service om te leren hoe u uw Experience Manager as a Cloud Service-implementatie kunt aanpassen.

| Local Development Setup | Informatie voordat je begint |
|-----------|------------|
| <ol><li>Herzie {de documentatie van SDK van 0} Adobe Experience Manager [&#x200B; om meer te leren.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html)</li><li>Controle [&#x200B; installeert Dispatcher SDK &#x200B;](https://video.tv.adobe.com/v/30601) om te begrijpen hoe te om Dispatcher SDK te installeren</li><li>Controle [&#x200B; vormt Dispatcher SDK &#x200B;](https://video.tv.adobe.com/v/30602) om op te begrijpen hoe te om Dispatcher SDK te vormen</li><li>De documentatie van de Opstelling van de Ontwikkeling van het overzicht [&#x200B; Lokale &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html#local-development-environment-set-up) om meer te leren</li><li>Het vormen toegang tot Experience Manager [&#x200B; lopen-door &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html#accessing)</li></ol> | <ol><li>[&#x200B; Grondbeginselen van de Ontwikkeling &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html)</li><li>[&#x200B; Richtlijnen van de Ontwikkeling &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html)</li><li>[&#x200B; Begrijpend de Structuur van het Project van Experience Manager &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html)</li><li>[&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)</li><li>[&#x200B; Digitale Vervaging van de Stichting &#x200B;](https://solutionpartners.adobe.com/content/dam/solution/en/spp_assets/restricted/community/community_31/digital_foundation_best_practices_and_documentation.zip)</li><li>[Stijlsysteem](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/features/style-system.html)</li><li>[&#x200B; Bedekkingen &#x200B;](/help/implementing/developing/introduction/overlays.md)</li><li>[&#x200B; Experience Manager as a Cloud Service API verwijzing &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/)</li></ol> |

>[!TIP]
> Zie leerprogramma&#39;s op hoe te [&#x200B; ontwikkelen en WKND op lokale Experience Manager SDK opstellen &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

### Implementeren

Ontwikkelaars schrijven code en testen deze lokaal en drukken deze vervolgens naar externe AEM as a Cloud Service-omgevingen.

Cloud Manager, een optioneel hulpprogramma voor het leveren van inhoud voor Managed Services, is nu vereist. Het is het enige mechanisme voor het implementeren van code in AEM as a Cloud Service-omgevingen.

Zie voor zelfhulp bronnen over het configureren en implementeren van AEM as a Cloud Service-omgevingen.

1. [&#x200B; vorm de Pijpleidingen van CM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/cicd-pipelines/introduction-ci-cd-pipelines.html)

   * Productiepijpleiding
   * Uitsluitend pijplijnen zonder productie en codekwaliteit

1. [&#x200B; stel Code &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html) op
1. [&#x200B; Begrijpend Uw Resultaten van de Test &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/test-results/overview-test-results.html)
1. **Toegang tot Logs**

   * [&#x200B; via CM UI &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs.html)
   * [&#x200B; via Adobe i/o cli &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html#debugging)

1. [&#x200B; Verrichtingen en Onderhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/home.html)

   * [&#x200B; het Vormen configuratie OSGI &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html)
   * [Back-up en herstel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/backup.html)

>[!TIP]
> Zie leerprogramma op hoe te [&#x200B; WKND aan Experience Manager Cloud Service opstellen &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

### Help en bronnen

1. [&#x200B; het Zuiveren uiteinden en trucs &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html#debugging-aem-as-a-cloud-service)
1. [Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html#debugging)
1. [&#x200B; CRXDE Lite &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html) (slechts beschikbaar op lokale milieu&#39;s van SDK en van de Wolk van Experience Manager Dev)
1. [&#x200B; Logboeken en registreren &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html#debugging)

   * [&#x200B; Logboeken van CM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html#debugging) (bouwstijl-eenheid-test, code-aftasten, bouwt-beeld, stelt op)
   * [&#x200B; Logs van Experience Manager Cloud Service &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html#debugging) (aemerror, aemaccess, aemrequest, aemdispatcher, httpderror, httpaccess)
   * Lokale SDK-logbestanden (onder host :port/crx-quickstart/logs)

>[!NOTE]
>
> Voor extra hulp, kunt u willen:
>
>1. [&#x200B; contacteer het Team van de Steun van Experience Manager &#x200B;](https://experienceleague.adobe.com/docs/customer-one/using/home.html)
>1. Onderzoek [&#x200B; de Gemeenschappen &amp; de Forums van Experience Manager &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)

<br>

## Naar Adobe Experience Manager as a Cloud Service {#move-to-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_move_to_cloud"
>title="Naar Adobe Experience Manager as a Cloud Service"
>abstract="Deze één-pager schetst de geadviseerde gefaseerde benadering van overgangs klanten van diverse Experience Manager plaatsingen aan Experience Manager as a Cloud Service en de hulp bestaande klanten leveren verbonden, ononderbroken ervaringen op dit moderne, doelgericht-gebouwde platform voor ervaringsbeheer."

**Experience Manager as a Cloud Service verstrekt een scalable, veilige, en mobiele technologiestichting voor Experience Manager Sites en Assets, toelatend marketers en IT om zich op het leveren van impactful ervaringen bij schaal te concentreren.**

Met Experience Manager as a Cloud Service kunnen uw teams zich richten op innovatie in plaats van op het plannen van productupgrades. Nieuwe productfuncties worden grondig getest en zonder onderbreking aan uw teams geleverd, zodat zij altijd toegang hebben tot de geavanceerde toepassing.

De overgang naar Cloud Service bestaat uit drie fasen: Planning, Executie en Nav.
Voor een geslaagde en soepele overgang moet u zorgen voor een goede planning en volgt u de best practices die in deze gids worden beschreven.

In onderstaande afbeelding ziet u een voorstelling op hoog niveau van de aanbevolen overgang naar Cloud Service.

![&#x200B; vertegenwoordiging op hoog niveau van de geadviseerde overgangsreis aan Cloud Service &#x200B;](/help/journey-migration/assets/home-img1.png)

<br>

### Planning

Voordat u begint met uw overgang naar Cloud Service, moet u:

* vertrouwd maken met Experience Manager as a Cloud Service
* bekijk de opmerkelijke wijzigingen die erin zijn aangebracht
* de vervangen of vervangen functies controleren

<table>
<tr>
<td>Ontdekking en evaluatie van projecten</td>
<td><ul><li>Zie <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html"> Notable Veranderingen in Experience Manager as a Cloud Service </a> om de belangrijke verschillen tussen Adobe Experience Manager as a Cloud Service en Experience Manager 6.x te begrijpen.</li><li>Zie <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/deprecated-removed-features.html"> Vervangen Eigenschappen </a> om meer over eigenschappen en mogelijkheden te leren die als afgekeurd zijn gemerkt.</li><li>[Voor de Migraties van Cloud Service slechts] die de Gereedheid van Cloud Service beoordelen: stel <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html"> Analyzer van Beste praktijken (BPA) </a> op bronmilieu in werking </li><li>Voltooi een evaluatie met opmerkelijke wijzigingen en vervangen functies in Experience Manager CS</li></ul></td>
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

Voordat u de uitvoeringsfase van een project start, moet u aan boord zijn van Cloud Service. U moet zich ook vertrouwd maken met Cloud Manager. Dit is het mechanisme voor het opstellen van projectcode aan een instantie van Experience Manager Cloud Service.

Cloud Manager stelt organisaties in staat om Experience Manager zelf te beheren in de cloud. Het omvat een ononderbroken integratie en ononderbroken levering ([&#x200B; CI/CD &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/overview/ci-cd-pipelines.html)) kader dat de teams van IT en de implementatiepartners de levering van aanpassingen of updates zonder prestaties of veiligheid te compromitteren laat versnellen.

#### Inhoud migreren

1. [&#x200B; Hulpmiddel van de Overdracht van de Inhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html#migration) : wordt gebruikt om bestaande inhoud over van een bronAEM instantie (op-gebouw of AMS) aan de instantie van de de Dienst van de Doopvaring van doelAEM te bewegen.
1. [&#x200B; Manager van het Pakket &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html#package-manager) : gebruikt voor het invoeren en het uitvoeren van veranderlijke inhoud van de bewaarplaats.


#### Refactor/optimaliseren

| Aan de slag | Revisie- en reactorcode | Dispatcher Review |
|---|---|---|
| <ul><li>[&#x200B; Lokale Dev opstelling &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html#local-development-environment-set-up)</li><li>[&#x200B; Lokale Opstelling van Dispatcher &#x200B;](https://video.tv.adobe.com/v/30602/)</li><li>[&#x200B; compileer uw code gebruikend SDK API jar &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html)</li><li>[&#x200B; de Richtlijnen van AEM Dev van het overzicht &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html)<ul><li>Achtergrondtaken en langdurige taken</li><li>Verschuivende planners</li><li>Gebruik van invoerstroom &amp; meer</li></ul></li></ul> | <ul><li>Stel de [&#x200B; Analysator van Beste praktijken (BPA) &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html) op bronmilieu in werking.[**slechts Migratie**]<ul><li>De Structurerende overwegingen van het project (die op [&#x200B; worden gebaseerd Archetype van de Wolk &#x200B;](https://github.com/adobe/aem-project-archetype))<ul><li>Scheiding van code en inhoud (Mutable versus Immuable)</li><li>[&#x200B; de indexdefinities van de Douane &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html)</li><li>[&#x200B; Runmodes van de Douane &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html)</li></ul></li></ul></li><li>Herzie en voer indien nodig wijzigingen uit</li><li>[&#x200B; stel &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) het op lokale SDK op</li><li>Rooktests uitvoeren via AEM SDK</li></ul> | <ul><li>Het overzicht {de configuraties van 0} Dispatcher [&#x200B; voor refactoring](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html)</li><li>Gebruik [&#x200B; Dispatcher Converter &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/dispatcher-transformation-utility-tools.html) hulpmiddel waar aangewezen. [**slechts Migratie**]</li><li>Het testen kan worden uitgevoerd gebruikend [&#x200B; Dispatcher SDK &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html#prerequisites)</li></ul> |

>[!TIP]
> De Klanten van Assets: De Werkschema&#39;s van Assets van het overzicht &amp; van de Refactor gebruikend [&#x200B; het hulpmiddel van de Migratie van de Wolk van Activa &#x200B;](https://github.com/adobe/aem-cloud-migration)


#### Implementatie/GoLive

1. [&#x200B; opstellen aan Cloud Manager &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/git-integration.html) git
2. De klantencode van de looppas door de [&#x200B; Pijl van de Kwaliteit van Cloud Manager &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/code-quality-testing.html)
3. [&#x200B; opstellen aan het Milieu van de Ontwikkeling &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html#debugging)
4. **migratie slechts** de overdracht van de Inhoud gebruikend pakketten of [&#x200B; het Hulpmiddel van de Overdracht van de Inhoud &#x200B;](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) (CTT)
5. Aanbevolen testcycli uitvoeren (rook, QA en meer)
6. Bevorderen tot de Cloud Manager Production Pipeline
7. Validatie van de rooktest
8. Go-Live

<br>

### Post Go-Live

In de fase na Go-Live moet u ervoor zorgen dat tijdelijke bestanden worden opgeschoond. Het is ook tijd om de best practices te evalueren voor continue ontwikkeling en voor het beheer van de logbestanden.

>[!TIP]
>
> Er zijn hulpprogramma&#39;s beschikbaar voor het oplossen van problemen in de AEM as a Cloud Service-omgeving
>
>1. [Developer Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html)
>1. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/repository-browser.html)
>1. [Tool voor beheren van logbestanden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs.html)

<br>

### Hulpmiddelen &amp; Middelen

| Beoordeling | Refactoring | Experience Manager-modernisering | Inhoud migreren |
|------------|-------------|---------------------------------|-------------------|
| <ul><li>[&#x200B; Analyzer van Beste praktijken &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html)</li></li> | <ul><li>[&#x200B; Verenigde Insteekmodule van de Ervaring &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/unified-experience.html)</li></ul> | <ul><li>[&#x200B; Statische malplaatjes aan editable malplaatjes &#x200B;](https://opensource.adobe.com/aem-modernize-tools/pages/structure.html)</li><li>[&#x200B; configuraties van het Ontwerp aan beleid &#x200B;](https://opensource.adobe.com/aem-modernize-tools/pages/policy.html) <li>[&#x200B; Componenten van de Stichting aan de Componenten van de Kern &#x200B;](https://opensource.adobe.com/aem-modernize-tools/pages/component.html)</li><li>[&#x200B; Klassieke UI aan aanraking-Toegelaten UI &#x200B;](https://opensource.adobe.com/aem-modernize-tools/pages/all-in-one.html)</li></ul> | <ul><li>[&#x200B; het Hulpmiddel van de Overdracht van de Inhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html)</li><li>[&#x200B; de Manager van het Pakket &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html#contentmanagement)</li></ul> |

>[!NOTE]
>
> Voor extra hulp, kunt u willen:
>
>1. [&#x200B; contacteer het Team van de Steun van Experience Manager &#x200B;](https://experienceleague.adobe.com/docs/customer-one/using/home.html)
>1. Onderzoek [&#x200B; de Gemeenschappen &amp; de Forums van Experience Manager &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)
