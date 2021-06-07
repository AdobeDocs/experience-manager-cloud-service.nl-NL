---
title: Migratie naar Experience Manager als Cloud Service
description: Migratie naar Experience Manager als Cloud Service
exl-id: 4d1addcf-b22d-41a3-ba5c-e5c42244e5cd
source-git-commit: a446efacb91f1a620d227b9413761dd857089c96
workflow-type: tm+mt
source-wordcount: '2117'
ht-degree: 7%

---

# Migratie naar Adobe Experience Manager als Cloud Service {#Overview}

>[!CONTEXTUALHELP]
>id="aemcloud_migration_overview"
>title="Migratie naar AEM als cloudservice"
>abstract="Omlijnt de geadviseerde gefaseerde benadering van overgangs klanten van diverse plaatsingen van de Experience Manager aan Experience Manager als Cloud Service en hulp bestaande klanten leveren verbonden, ononderbroken ervaringen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=en" text="Nieuwe en andere functies?"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en" text="Inleiding tot AEM as a Cloud Service."

Adobe Experience Manager (AEM) als Cloud Service biedt een opnieuw ontwikkelde basis voor Experience Manager, die is gebaseerd op een containergebaseerde infrastructuur, API-gestuurde ontwikkeling en het geleide DevOps-proces, waardoor marketers en ontwikkelaars altijd op de curve kunnen blijven vooruitlopen in innovaties op het gebied van het beheer van de klantenervaring.

Cloud Service combineert de rijke mogelijkheden en uitbreidbaarheid van Adobe Experience Manager buiten de box met de flexibiliteit van de moderne cloudnative architectuur die merken in staat stelt aan de voortdurend veranderende consumentenvraag te voldoen.

Deze één-pager schetst de geadviseerde gefaseerde benadering van overgangs klanten van diverse plaatsingen van de Experience Manager aan Experience Manager als Cloud Service en helpt bestaande klanten verbonden, ononderbroken ervaringen op dit moderne, doel-gebouwde platform voor ervaringsbeheer leveren.

<!-- It primarily focuses on:
* Getting Started with Adobe Experience Manager as a Cloud Service
* Developer Journey in Adobe Experience Manager as a Cloud Service
* Moving to Adobe Experience Manager as a Cloud Service -->

<br>

## Aan de slag met Adobe Experience Manager als een Cloud Service {#getting-started}

| Wat is anders? | Overzicht van architectuur |
|--------------------------|--------------------------|
| <ul><li>[Moderne architectuur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html)</li><li>[Automatische updates](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/aem-version-updates.html?lang=en#aem-version-updates)</li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)</li><li>[Asset Microservices](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html)</li><li>[Directe toegangsbinaire bestanden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html?lang=en#asset-upload-with-direct-binary-access)</li><li>[Scheiding van code en inhoud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=en#developing)</li><li>[Replicatie als service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/replication.html?lang=en)</li><li>[Admin-console, Group/User Membership en ACL&#39;s](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html)</li></ul> | <ul><li>[Inleiding tot AEM architectuur](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-architecture.html?lang=en#underlying-technology)</li><li>[Omgevingsstapel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html)</li><li>[Auteurlaag](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[Lijst publiceren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#content-delivery)</li><li>[CDN](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/cdn.html?lang=en#content-delivery) </li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)  (CI/CD)</li><li>[Identiteitsbeheer ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#onboarding-users-in-admin-console) via  [beheerconsole](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html)</li><li>[asset compute](https://experienceleague.adobe.com/docs/asset-compute/using/home.html)</li></ul> |

![AEM as a Cloud Service - Runtimearchitectuur](/help/core-concepts/assets/concepts-03.png "AEM as a Cloud Service - Runtimearchitectuur")

<br>

## Ontwikkelaarsreis in Adobe Experience Manager als Cloud Service {#developer-journey}

### Ontwikkeling

De grondbeginselen van codeontwikkeling zijn in Adobe Experience Manager vergelijkbaar met een Cloud Service in vergelijking met de oplossingen Adobe Experience Manager On Premise en Managed Services.

Ontwikkelaars schrijven code en testen deze lokaal, wat vervolgens als een Cloud Service wordt doorgegeven aan externe Adobe Experience Manager.

Zie zelf-hulp middelen over implementatie voor Experience Manager als Cloud Service leren hoe te om uw Experience Manager als plaatsing van de Cloud Service aan te passen.

| Local Development Setup | Informatie voordat je begint |
|-----------|------------|
| <ol><li>Raadpleeg de documentatie bij [Adobe Experience Manager SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing) voor meer informatie.</li><li>Bekijk [Dispatcher SDK installeren](https://video.tv.adobe.com/v/30601) om te begrijpen hoe u Dispatcher SDK installeert</li><li>Controle [Vorm Dispatcher SDK](https://video.tv.adobe.com/v/30602) om te begrijpen hoe te om de SDK van de Ontvanger te vormen</li><li>Raadpleeg de [Local Development Setup](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up)-documentatie voor meer informatie</li><li>Toegang tot Experience Manager [doorlopen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=en#accessing) configureren</li></ol> | <ol><li>[Grondbeginselen van ontwikkeling](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[Richtlijnen voor ontwikkeling](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#developing)</li><li>[Werken met de projectstructuur van Experience Managers](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=en#developing)</li><li>[Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)</li><li>[Blauwdruk digitale basis](https://solutionpartners.adobe.com/content/dam/spp_assets/restricted/community/community_31/digital_foundation_best_practices_and_documentation.zip)</li><li>[Stijlsysteem](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/style-system.html?lang=en#authoring)</li><li>[Bedekkingen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/overlays.html?lang=en#developing)</li><li>[Experience Manager als Cloud Service API-referentie](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/)</li></ol> |

>[!TIP]
> Zie zelfstudie over het [WKND ontwikkelen en implementeren op SDK van lokale Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en)

### Implementeren

Ontwikkelaars schrijven code en testen deze lokaal, wat vervolgens als een Cloud Service-omgeving wordt doorgegeven aan externe AEM.

Cloud Manager, een optioneel hulpprogramma voor het leveren van inhoud voor Managed Services, is vereist. Dit is nu het enige mechanisme voor het opstellen van code aan AEM als milieu&#39;s van de Cloud Service.

Zie zelf-hulp middelen over om te vormen en op te stellen aan AEM als milieu&#39;s van de Cloud Service.

1. [CM-pijpleidingen configureren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=en#using-cloud-manager)
   * Productiepijpleiding
   * Uitsluitend pijplijnen zonder productie en codekwaliteit
2. [Code implementeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#using-cloud-manager)
3. [De testresultaten begrijpen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/overview-test-results.html?lang=en#using-cloud-manager)
4. **Logbestanden openen**
   * [via CM-gebruikersinterface](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=en#using-cloud-manager)
   * [via Adobe i/o cli](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
5. [Exploitatie en onderhoud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/home.html?lang=en)
   * [Configuratie van OSGI configureren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#deploying)
   * [Back-up en herstel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/backup.html?lang=en)

>[!TIP]
> Zie zelfstudie over het [implementeren van WKND in Experience Manager Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/develop-wknd-tutorial.html?lang=en)

### Help en bronnen

1. [Tips en trucs voor foutopsporing](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=en#debugging-aem-as-a-cloud-service)
2. [Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=en#debugging)
3. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=en#debugging) (Alleen beschikbaar in lokale SDK- en Experience Manager Cloud Dev-omgevingen)
4. [Logbestanden en logboekregistratie](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
   * [CM Logs](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging)  (build-unit-testing, code-scanning, build-image, implementatie)
   * [Experience Manager Cloud Service Logs](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging) (aemerror, aemaccess, aemrequest, aemdispatcher, httpderror, httpaccess)
   * Lokale SDK-logbestanden (onder host:port/crx-quickstart/logs)

>[!NOTE]
> Voor extra hulp, kunt u willen:
>1. [Neem contact op met het ondersteuningsteam van de Experience Manager](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. [Experience Managers van gemeenschappen &amp; forums](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community) verkennen


<br>

## Naar Adobe Experience Manager gaan als een Cloud Service {#move-to-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_move_to_cloud"
>title="Als Cloud Service naar Adobe Experience Manager gaan"
>abstract="Deze één-pager schetst de geadviseerde gefaseerde benadering van overgangs klanten van diverse plaatsingen van de Experience Manager aan Experience Manager als Cloud Service en helpt bestaande klanten verbonden, ononderbroken ervaringen op dit moderne, doel-gebouwde platform voor ervaringsbeheer leveren."

**Experience Manager als Cloud Service biedt een schaalbare, veilige en flexibele technologiebasis voor de Experience Manager van sites en bedrijfsmiddelen, waardoor marketers en IT zich kunnen richten op het leveren van indrukwekkende ervaringen op schaal.**

Met Experience Manager als Cloud Service, kunnen uw teams zich op het innoveren in plaats van planning voor productverbeteringen concentreren. Nieuwe productfuncties worden grondig getest en zonder systeemonderbreking aan uw teams geleverd, zodat zij altijd toegang hebben tot de nieuwste en meest geavanceerde applicaties.

De overgang naar Cloud Service bestaat uit drie fasen: planning, uitvoering en de stappen na Go-Live.
Voor een geslaagde en soepele overgang moet u zorgen voor een goede planning en volgt u de best practices die in deze gids worden beschreven.

De onderstaande afbeelding toont de aanbevolen overgang naar Cloud Service.

![afbeelding](/help/move-to-cloud-service/assets/home-img1.png)

<br>

### Planning

Voordat u begint met de overgang naar de Cloud Service, dient u uzelf vertrouwd te maken met de Experience Manager als Cloud Service en de opmerkelijke wijzigingen die erin zijn aangebracht te controleren en ook de functies te bekijken die zijn vervangen of vervangen.

<table>
<tr>
<td>Ontdekking en evaluatie van projecten</td>
<td><ul><li>Verwijs naar <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=en">Notable Veranderingen in Experience Manager als Cloud Service</a> om de belangrijke verschillen tussen Adobe Experience Manager als Cloud Service en Experience Manager 6.x te begrijpen.</li><li>Raadpleeg <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/deprecated-removed-features.html?lang=en#deprecated-features">Vervangen functies</a> voor meer informatie over functies en mogelijkheden die zijn gemarkeerd als verouderd.</li><li>[Alleen voor migraties van Cloud Servicen] Gereedheid van Cloud Servicen beoordelen: <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration">Analysator van Beste praktijken (BPA)</a> op bronmilieu in werking stellen </li><li>Voltooi een beoordeling tegen opmerkelijke veranderingen en verouderde eigenschappen in Experience Manager CS</li></ul></td>
</tr>
<tr>
<td>Controleren</td>
<td><ul><li>Op basis van detectie, oefeningen uitvoeren voor het schatten van de inspanningen en het inzetten van middelen</li></ul></td>
</tr>
<tr>
<td>Meetlat</td>
<td><ul><li><a href="https://experienceleague.adobe.com/welcome/aem/part6.html">Vaststellen van KPI's</a> voor projecten, succescriteria en projecttijdlijnen</li></ul></td>
</tr>
</table>

>[!NOTE]
>Het Rapport van de Analysator van Beste praktijken versnelt het proces om de tijd en de kosten te schatten die worden vereist om naar AEM als Cloud Service over te gaan door informatie te verstrekken die anders manueel zou moeten worden verzameld en worden geëvalueerd.


<br>

### Uitvoering

Alvorens u de fase van de Uitvoering van een project begint, zou u aan Cloud Service moeten worden ingezien. U moet zich ook vertrouwd maken met Cloud Manager. Dit is het mechanisme om projectcode aan een instantie van de Experience Manager Cloud Service op te stellen.

Met Cloud Manager kunnen organisaties zelf Experience Manager beheren in de cloud. Het omvat een ononderbroken integratie en ononderbroken levering ([CI/CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/overview/ci-cd-pipeline.html?lang=en#overview)) kader dat de teams van IT en implementatiepartners de levering van aanpassingen of updates zonder prestaties of veiligheid te compromitteren laat versnellen.

#### Inhoud migreren

1. [Gereedschap](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration)  Inhoud overbrengen: gebruikt om bestaande inhoud van een bron AEM instantie (on-premise of AMS) naar de AEM instantie van de Cloud Service te verplaatsen.
2. [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#package-manager) : worden gebruikt voor het importeren en exporteren van veranderbare inhoud van de gegevensopslagruimte.


#### Refactor/optimaliseren

| Aan de slag | Revisie- en reactorcode | Dispatcher Review |
|---|---|---|
| <ul><li>[Lokale Dev-instellingen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up)</li><li>[Local Dispatcher Setup](https://video.tv.adobe.com/v/30602/)</li><li>[Uw code compileren met SDK API-jar](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[Richtlijnen voor AEM bekijken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#developing)<ul><li>Achtergrondtaken en langdurige taken</li><li>Verschuivende planners</li><li>Gebruik van invoerstroom &amp; meer</li></ul></li></ul> | <ul><li>Voer [Best Practices Analyzer (BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration) op bronmilieu in.[**Alleen migratie**]<ul><li>Overwegingen voor projectstructuur (gebaseerd op [Cloud Archetype](https://github.com/adobe/aem-project-archetype))<ul><li>Scheiding van code en inhoud (Mutable versus Immuable)</li><li>[Aangepaste indexdefinities](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#indexing)</li><li>[Aangepaste runmodi](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#runmodes)</li></ul></li></ul></li><li>Herzie en voer indien nodig wijzigingen uit</li><li>[](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en) Implementatie op lokale SDK</li><li>Rooktests uitvoeren via AEM SDK</li></ul> | <ul><li>Revisie [Dispatcherconfiguraties](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#local-validation-of-dispatcher-configuration) voor refactoring</li><li>Gebruik, indien van toepassing, [Dispatcher Converter](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/dispatcher-transformation-utility-tools.html?lang=en#introduction-dispatcher). [**Alleen migratie**]</li><li>Testen kan worden uitgevoerd met [Dispatcher SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=en#prerequisites)</li></ul> |

>[!TIP]
> Klanten middelen: Workflows voor revisie- en reflectorelementen met de gereedschappen [Migratie van Asset Cloud](https://github.com/adobe/aem-cloud-migration)


#### Implementatie/GoLive

1. [Distribueren naar Cloud ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html?lang=en#managing-code) Manager
2. Clientcode uitvoeren via [Cloud Manager Quality Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use)
3. [Distribueren naar ontwikkelomgeving](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging)
4. [**Alleen migratie**] Inhoud overbrengen met behulp van pakketten of  [Content Transfer Tool](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md) (CTT)
5. Aanbevolen testcycli uitvoeren (rook, QA en meer)
6. Promoten naar de productiepijplijn van Cloud Manager
7. Validatie van de rooktest
8. Go-Live

<br>

### Post Go-Live

In de fase na Go-Live moet u ervoor zorgen dat tijdelijke bestanden worden opgeschoond. Het is ook tijd om de best practices te evalueren voor continue ontwikkeling en voor het beheer van de logbestanden.

>[!TIP]
> De hulpmiddelen zijn beschikbaar om AEM als milieu&#39;s van de Cloud Service problemen op te lossen
>1. [Ontwerpconsole](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#aem-as-a-cloud-service-development-tools)
>2. [CRX/DE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=en#debugging)
>3. [Tool voor beheren van logbestanden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=en#using-cloud-manager)


<br>

### Hulpmiddelen &amp; Middelen

| Beoordeling | Refactoring | Modernisering van de Experience Manager | Inhoud migreren |
|------------|-------------|---------------------------------|-------------------|
| <ul><li>[Analysator van best practices](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration)</li></li> | <ul><li>[Insteekmodule voor Unified Experience](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#refactoring-tools)</li></ul> | <ul><li>[Statische sjablonen converteren naar bewerkbare sjablonen](https://opensource.adobe.com/aem-modernize-tools/pages/tools/page-structure.html)</li><li>[Ontwerpconfiguraties omzetten naar beleid](https://opensource.adobe.com/aem-modernize-tools/pages/tools/policy-importer.html) <li>[Elementaire componenten omzetten naar kerncomponenten](https://opensource.adobe.com/aem-modernize-tools/pages/tools/component.html)</li><li>[De klassieke interface converteren naar een interface met aanraakbediening](https://opensource.adobe.com/aem-modernize-tools/pages/tools/dialog.html)</li></ul> | <ul><li>[De tool Content Transfer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#cloud-migration)</li><li>[Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en#contentmanagement)</li></ul> |

>[!NOTE]
> Voor extra hulp, kunt u willen:
>1. [Neem contact op met het ondersteuningsteam van de Experience Manager](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. [Experience Managers van gemeenschappen &amp; forums](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community) verkennen

