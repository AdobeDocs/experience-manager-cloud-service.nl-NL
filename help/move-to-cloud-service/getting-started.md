---
title: De Gids van de migratie aan Experience Manager as a Cloud Service voor Partners
description: De Gids van de migratie aan Experience Manager as a Cloud Service voor Partners
exl-id: 4d1addcf-b22d-41a3-ba5c-e5c42244e5cd
source-git-commit: bcbf4e4ba1330bef9f2c8c473419903e40ac0e58
workflow-type: tm+mt
source-wordcount: '2092'
ht-degree: 8%

---

# Migratiehandleiding voor Adobe Experience Manager as a Cloud Service for Partners {#Overview}

>[!CONTEXTUALHELP]
>id="aemcloud_migration_overview"
>title="Migratie naar AEM als cloudservice"
>abstract="Omlijnt de geadviseerde gefaseerde benadering van overgangs klanten van diverse plaatsingen van de Experience Manager aan Experience Manager as a Cloud Service en hulp bestaande klanten leveren verbonden, ononderbroken ervaringen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=en" text="Nieuwe en andere functies?"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en" text="Inleiding tot AEM as a Cloud Service."

Adobe Experience Manager (AEM) as a Cloud Service biedt een herarchitected basis voor Experience Manager, die is gebaseerd op een containergebaseerde infrastructuur, API-gestuurde ontwikkeling en het geleide DevOps-proces, waardoor marketers en ontwikkelaars altijd op de curve kunnen blijven vooruitlopen in innovaties op het gebied van het beheer van de gebruikerservaring.

Cloud Service combineert de rijke mogelijkheden en uitbreidbaarheid van Adobe Experience Manager buiten de box met de flexibiliteit van de moderne cloudnative architectuur die merken in staat stelt aan de voortdurend veranderende consumentenvraag te voldoen.

Deze één-pager schetst de geadviseerde gefaseerde benadering van overgangs klanten van diverse Experience Manager plaatsingen aan Experience Manager as a Cloud Service en de hulp bestaande klanten leveren verbonden, ononderbroken ervaringen op dit moderne, doelgericht-gebouwde platform voor ervaringsbeheer.

<!-- It primarily focuses on:
* Getting Started with Adobe Experience Manager as a Cloud Service
* Developer Journey in Adobe Experience Manager as a Cloud Service
* Moving to Adobe Experience Manager as a Cloud Service -->

<br>

## Aan de slag met Adobe Experience Manager as a Cloud Service {#getting-started}

| Wat is anders? | Overzicht van architectuur |
|--------------------------|--------------------------|
| <ul><li>[Moderne architectuur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/architecture.html)</li><li>[Automatische updates](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/aem-version-updates.html?lang=en#aem-version-updates)</li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)</li><li>[Asset Microservices](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html)</li><li>[Directe toegangsbinaire bestanden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html?lang=en#asset-upload-with-direct-binary-access)</li><li>[Scheiding van code en inhoud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=en#developing)</li><li>[Replicatie als service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/replication.html?lang=en)</li><li>[Admin-console, Group/User Membership en ACL&#39;s](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html)</li></ul> | <ul><li>[Inleiding tot AEM architectuur](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-architecture.html?lang=en#underlying-technology)</li><li>[Omgevingsstapel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/architecture.html)</li><li>[Auteurlaag](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[Lijst publiceren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-author-publish.html?lang=en#underlying-technology)</li><li>[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#content-delivery)</li><li>[CDN](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/cdn.html?lang=en#content-delivery) </li><li>[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) (CI/CD)</li><li>[Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#onboarding-users-in-admin-console) via [Admin-console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html)</li><li>[asset compute](https://experienceleague.adobe.com/docs/asset-compute/using/home.html)</li></ul> |

![AEM as a Cloud Service - Runtimearchitectuur](/help/overview/assets/concepts-03.png "AEM as a Cloud Service - Runtimearchitectuur")

<br>

## Developer Journey in Adobe Experience Manager as a Cloud Service {#developer-journey}

### Ontwikkeling

De grondbeginselen van codeontwikkeling zijn in Adobe Experience Manager as a Cloud Service vergelijkbaar met de oplossingen Adobe Experience Manager On Premise en Managed Services.

Ontwikkelaars schrijven code en testen deze lokaal, wat vervolgens wordt doorgegeven aan externe Adobe Experience Manager as a Cloud Service-omgevingen.

Zie zelf-hulp middelen over implementatie voor as a Cloud Service Experience Manager om te leren hoe te om uw Experience Manager as a Cloud Service plaatsing aan te passen.

| Local Development Setup | Informatie voordat je begint |
|-----------|------------|
| <ol><li>Controleren [Adobe Experience Manager SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing) documentatie voor meer informatie.</li><li>Controle [Dispatcher SDK installeren](https://video.tv.adobe.com/v/30601) voor meer informatie over het installeren van Dispatcher SDK</li><li>Controle [Dispatcher SDK configureren](https://video.tv.adobe.com/v/30602) om te begrijpen hoe te om Dispatcher SDK te vormen</li><li>Controleren [Local Development Setup](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up) documentatie voor meer informatie</li><li>Toegang tot Experience Manager configureren [doorlopen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=en#accessing)</li></ol> | <ol><li>[Grondbeginselen van ontwikkeling](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[Richtlijnen voor ontwikkeling](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#developing)</li><li>[Werken met de projectstructuur van Experience Managers](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=en#developing)</li><li>[Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)</li><li>[Blauwdruk digitale basis](https://solutionpartners.adobe.com/content/dam/spp_assets/restricted/community/community_31/digital_foundation_best_practices_and_documentation.zip)</li><li>[Stijlsysteem](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/style-system.html?lang=en#authoring)</li><li>[Bedekkingen](/help/implementing/developing/introduction/overlays.md)</li><li>[Experience Manager as a Cloud Service API-referentie](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/)</li></ol> |

>[!TIP]
> Zie zelfstudie over hoe u kunt [WKND ontwikkelen en implementeren op de SDK van lokale Experience Managers](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

### Implementeren

Ontwikkelaars schrijven code en testen deze lokaal, wat vervolgens wordt doorgegeven aan externe AEM as a Cloud Service omgevingen.

Cloud Manager, een optioneel hulpprogramma voor het leveren van inhoud voor Managed Services, is vereist. Dit is nu het enige mechanisme voor het opstellen van code aan AEM as a Cloud Service milieu&#39;s.

Zie zelf-hulp middelen over hoe te om aan AEM as a Cloud Service milieu&#39;s te vormen en op te stellen.

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
> Zie zelfstudie over hoe u kunt [WKND naar Experience Manager Cloud Service implementeren](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)

### Help en bronnen

1. [Tips en trucs voor foutopsporing](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=en#debugging-aem-as-a-cloud-service)
2. [Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=en#debugging)
3. [CRXDE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=en#debugging) (Alleen beschikbaar in lokale SDK- en Experience Manager Cloud Dev-omgevingen)
4. [Logbestanden en logboekregistratie](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging)
   * [CM-logbestanden](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging) (build-unit-testing, code-scanning, build-image, implementatie)
   * [Logbestanden Experience Manager Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html?lang=en#debugging) (aemerror, aemaccess, aemrequest, aemdispatcher, httpderror, httpaccess)
   * Lokale SDK-logbestanden (onder host:port/crx-quickstart/logs)

>[!NOTE]
> Voor extra hulp, kunt u willen:
>1. [Neem contact op met het ondersteuningsteam van de Experience Manager](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. Verkennen [Experience Managers en forums](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)


<br>

## Verplaatsen naar Adobe Experience Manager as a Cloud Service {#move-to-cloud}

>[!CONTEXTUALHELP]
>id="aemcloud_move_to_cloud"
>title="Verplaatsen naar Adobe Experience Manager as a Cloud Service"
>abstract="Deze één-pager schetst de geadviseerde gefaseerde benadering van overgangs klanten van diverse Experience Manager plaatsingen aan Experience Manager as a Cloud Service en de hulp bestaande klanten leveren verbonden, ononderbroken ervaringen op dit moderne, doelgericht-gebouwde platform voor ervaringsbeheer."

**as a Cloud Service Experience Manager biedt een schaalbare, veilige en flexibele technologiebasis voor Experience Manager Sites en Assets, waardoor marketeers en IT zich kunnen richten op het leveren van indrukwekkende ervaringen op schaal.**

Met as a Cloud Service Experience Manager, kunnen uw teams zich op het vernieuwen in plaats van planning voor productverbeteringen concentreren. Nieuwe productfuncties worden grondig getest en zonder systeemonderbreking aan uw teams geleverd, zodat zij altijd toegang hebben tot de nieuwste en meest geavanceerde applicaties.

De overgang naar Cloud Service bestaat uit drie fasen: planning, uitvoering en de stappen na Go-Live.
Voor een geslaagde en soepele overgang moet u zorgen voor een goede planning en volgt u de best practices die in deze gids worden beschreven.

De onderstaande afbeelding toont de aanbevolen overgang naar Cloud Service.

![afbeelding](/help/journey-migration/assets/home-img1.png)

<br>

### Planning

Voordat u begint met de overgang naar de Cloud Service, moet u zich vertrouwd maken met de as a Cloud Service Experience Manager en de opmerkelijke wijzigingen die erin zijn aangebracht, bekijken en ook de functies bekijken die zijn vervangen of vervangen.

<table>
<tr>
<td>Ontdekking en evaluatie van projecten</td>
<td><ul><li>Zie <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=en">Opvallende wijzigingen in as a Cloud Service Experience Manager</a> om inzicht te krijgen in de belangrijke verschillen tussen Adobe Experience Manager as a Cloud Service en Experience Manager 6.x.</li><li>Zie <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/deprecated-removed-features.html?lang=en#deprecated-features">Verouderde functies</a> voor meer informatie over functies en mogelijkheden die zijn gemarkeerd als afgekeurd.</li><li>[Alleen voor migraties van Cloud Servicen] Gereedheid van Cloud Servicen beoordelen: Voer de <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration">Best Practices Analyzer (BPA)</a> over de bronomgeving </li><li>Voltooi een beoordeling tegen opmerkelijke veranderingen en verouderde eigenschappen in Experience Manager CS</li></ul></td>
</tr>
<tr>
<td>Controleren</td>
<td><ul><li>Op basis van detectie, oefeningen uitvoeren voor het schatten van de inspanningen en het inzetten van middelen</li></ul></td>
</tr>
<tr>
<td>Meetlat</td>
<td><ul><li><a href="https://experienceleague.adobe.com/welcome/aem/part6.html">Project-KPI's maken</a>, succescriteria en projecttijdschema's</li></ul></td>
</tr>
</table>

>[!NOTE]
>Het Rapport van de Analysator van Beste praktijken versnelt het proces om de tijd en de kosten te schatten die worden vereist om naar AEM as a Cloud Service over te gaan door informatie te verstrekken die anders manueel zou moeten worden verzameld en worden geëvalueerd.


<br>

### Uitvoering

Alvorens u de fase van de Uitvoering van een project begint, zou u aan Cloud Service moeten worden ingezien. U moet zich ook vertrouwd maken met Cloud Manager. Dit is het mechanisme om projectcode aan een instantie van de Experience Manager Cloud Service op te stellen.

Met Cloud Manager kunnen organisaties zelf Experience Manager beheren in de cloud. Het omvat een continue integratie en doorlopende levering ([CI/CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/overview/ci-cd-pipeline.html?lang=en#overview)) die IT-teams en implementatiepartners in staat stelt de levering van aanpassingen of updates te versnellen zonder de prestaties of beveiliging in gevaar te brengen.

#### Inhoud migreren

1. [Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration) - Wordt gebruikt om bestaande inhoud te verplaatsen van een bron-AEM (on-premise of AMS) naar de AEM Cloud Service-doelinstantie.
2. Pakketbeheer - Wordt gebruikt voor het importeren en exporteren van muteerbare inhoud van de opslagplaats.


#### Refactor/optimaliseren

| Aan de slag | Revisie- en reactorcode | Dispatcher Review |
|---|---|---|
| <ul><li>[Lokale Dev-instellingen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-development-environment-set-up)</li><li>[Local Dispatcher Setup](https://video.tv.adobe.com/v/30602/)</li><li>[Uw code compileren met SDK API-jar](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#developing)</li><li>[Richtlijnen voor AEM bekijken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#developing)<ul><li>Achtergrondtaken en langdurige taken</li><li>Verschuivende planners</li><li>Gebruik van invoerstroom &amp; meer</li></ul></li></ul> | <ul><li>Voer de [Best Practices Analyzer (BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration) op de bronomgeving.[**Alleen migratie**]<ul><li>Overwegingen voor projectstructuur (gebaseerd op [Cloud Archetype](https://github.com/adobe/aem-project-archetype))<ul><li>Scheiding van code en inhoud (Mutable versus Immuable)</li><li>[Aangepaste indexdefinities](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#indexing)</li><li>[Aangepaste runmodi](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#runmodes)</li></ul></li></ul></li><li>Herzie en voer indien nodig wijzigingen uit</li><li>[Implementeren](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en) het op lokale SDK</li><li>Rooktests uitvoeren via AEM SDK</li></ul> | <ul><li>Controleren [Dispatcher-configuraties](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#local-validation-of-dispatcher-configuration) voor refactoring</li><li>Hefboomwerking [Dispatcher Converter](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/dispatcher-transformation-utility-tools.html?lang=en#introduction-dispatcher) in voorkomend geval. [**Alleen migratie**]</li><li>Testen kan worden uitgevoerd met [Dispatcher SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=en#prerequisites)</li></ul> |

>[!TIP]
> Klanten middelen: Workflows van revisies en reactorelementen gebruiken [Migratie van de cloud van middelen](https://github.com/adobe/aem-cloud-migration) gereedschap


#### Implementatie/GoLive

1. [Distribueren naar Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html?lang=en#managing-code) git
2. De klantencode van de looppas door [Kwaliteitspipet Wolkenbeheer](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use)
3. [Distribueren naar ontwikkelomgeving](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/build-and-deployment.html?lang=en#debugging)
4. [**Alleen migratie**] Inhoud overbrengen met pakketten of [Inhoud overbrengen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md)(CTT)
5. Aanbevolen testcycli uitvoeren (rook, QA en meer)
6. Promoten naar de productiepijplijn van Cloud Manager
7. Validatie van de rooktest
8. Go-Live

<br>

### Post Go-Live

In de fase na Go-Live moet u ervoor zorgen dat tijdelijke bestanden worden opgeschoond. Het is ook tijd om de best practices te evalueren voor continue ontwikkeling en voor het beheer van de logbestanden.

>[!TIP]
> Er zijn hulpprogramma&#39;s beschikbaar om problemen op te lossen AEM as a Cloud Service omgevingen
>1. [Ontwerpconsole](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#aem-as-a-cloud-service-development-tools)
>2. [CRX/DE Lite](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/crxde-lite.html?lang=en#debugging)
>3. [Tool voor beheren van logbestanden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=en#using-cloud-manager)


<br>

### Hulpmiddelen &amp; Middelen

| Beoordeling | Refactoring | Modernisering van de Experience Manager | Inhoud migreren |
|------------|-------------|---------------------------------|-------------------|
| <ul><li>[Analysator van best practices](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=en#cloud-migration)</li></li> | <ul><li>[Insteekmodule voor Unified Experience](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#refactoring-tools)</li></ul> | <ul><li>[Statische sjablonen converteren naar bewerkbare sjablonen](https://opensource.adobe.com/aem-modernize-tools/pages/tools/page-structure.html)</li><li>[Ontwerpconfiguraties omzetten naar beleid](https://opensource.adobe.com/aem-modernize-tools/pages/tools/policy-importer.html) <li>[Elementaire componenten omzetten naar kerncomponenten](https://opensource.adobe.com/aem-modernize-tools/pages/tools/component.html)</li><li>[De klassieke interface converteren naar een interface met aanraakbediening](https://opensource.adobe.com/aem-modernize-tools/pages/tools/dialog.html)</li></ul> | <ul><li>[De tool Content Transfer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#cloud-migration)</li><li>[Pakketbeheer](/help/implementing/developing/tools/package-manager.md)</li></ul> |

>[!NOTE]
> Voor extra hulp, kunt u willen:
>1. [Neem contact op met het ondersteuningsteam van de Experience Manager](https://experienceleague.adobe.com/docs/customer-one/using/home.html?lang=en)
>2. Verkennen [Experience Managers en forums](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community)

