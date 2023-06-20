---
title: Gereedheidsfase
description: Leer meer over de stappen die u moet nemen om ervoor te zorgen dat uw AEM installatie klaar is om naar de cloud te worden verplaatst
exl-id: 3bc8c037-d82a-4455-bce6-3c80c359a4ae
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '2074'
ht-degree: 6%

---

# Gereedheidsfase {#readiness-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_planning"
>title="Overgang plannen"
>abstract="Voordat u het overgangstraject naar Cloud Service start, moet u AEM as a Cloud Service leren kennen en op de hoogte zijn van de belangrijke recente veranderingen, zodat u weet welke functies zijn vervangen of verouderd."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html" text="Analysator van best practices"

In deze fase van de AEM as a Cloud Service Migratiereis, zult u zich met AEM as a Cloud Service vertrouwd maken, de opmerkelijke veranderingen herzien die het heeft geïntroduceerd en begrijpen wat het vergt om voor een succesvolle migratie naar de wolk te plannen.

## Het verhaal tot nu toe {#story-so-far}

Het vorige document, [Aan de slag met Verplaatsen naar AEM as a Cloud Service](/help/journey-migration/getting-started.md)schetst u een lijst met fasen die u moet ondergaan om te kunnen migreren naar AEM as a Cloud Service en de voordelen hiervan.

## Doelstelling {#objective}

Dit document helpt u te begrijpen welke factoren u moet overwegen zodat u ervoor kunt zorgen dat uw AEM installatie klaar is om naar de cloud te worden verplaatst:

* Meer informatie over opmerkelijke wijzigingen en verouderde functies
* Begrijp hoe te om voor de migratie aan AEM as a Cloud Service te plannen

## Bekijk de opmerkelijke veranderingen in de AEM as a Cloud Service Architectuur {#notable-changes-in-aem-cloud-service-architecture}

AEM as a Cloud Service biedt veel nieuwe functies en mogelijkheden voor het beheer van uw AEM-projecten.

Samen met deze verbeteringen zijn er verschillende verschillen ontstaan tussen on-premise installaties van AEM en Adobe Managed Services, in vergelijking met AEM as a Cloud Service.

De lijst met items in de onderstaande tabel is de subset van de wijzigingen die het meest relevant zijn voor een migratie naar AEM as a Cloud Service. U kunt de volledige lijst met opmerkelijke wijzigingen raadplegen [hier](/help/release-notes/aem-cloud-changes.md).

<table>
<thead>
  <tr>
    <th>Wat is er veranderd?</th>
    <th>Referentie</th>
    <th>Key Takeaways</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Meerdere en onveranderbare filters scheiden in overeenkomende pakketten</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=en">as a Cloud Service opmerkelijke wijzigingen AEM</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html#mutable-vs-immutable">AEM projectstructuur voor AEM as a Cloud Service</a></td>
    <td>Een enkel pakket dat in AEM as a Cloud Service kan worden geïmplementeerd, kan subpakketten bevatten, voornamelijk om muteerbare en onveranderlijke inhoud te bevatten die in hun eigen pakketten is gescheiden.</td>
  </tr>
  <tr>
    <td>Reparatie-item</td>
    <td><a href="https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language">Documentatie Apache Sling RepoInit</a></td>
    <td>Scripts opnieuw aanwijzen is de beste manier om initiële knooppuntstructuren, gebruikers, groepen of servicegebruikers te maken. Aangezien deze manuscripten door looppas wijze kunnen worden gericht en door code pakketplaatsing kunnen worden beheerd, verstrekken zij veel flexibiliteit om bewaarplaatsininitialisatietaken te bereiken.</td>
  </tr>
  <tr>
    <td>Aangepaste uitvoermodi zijn niet toegestaan</td>
    <td></td>
    <td>Alleen uitvoeringsmodi die buiten het vak met AEM as a Cloud Service zijn opgegeven, worden ondersteund.<br>Wanneer de extra milieu's van de Ontwikkeling alle hen worden toegevoegd binden aan de "dev"looppaswijze.</td>
  </tr>
  <tr>
    <td>Uitvoeren van de pijplijn van de Manager van de wolk is de enige manier om op te stellen</td>
    <td></td>
    <td>In AEM as a Cloud Service, is de toegang tot /system/console niet toegestaan, vandaar moeten alle configuraties OSGi deel van code uitmaken, en zouden als code moeten worden opgesteld.<br>De OSGi-configuraties zijn beschikbaar in de modus Alleen-lezen en kunnen worden bekeken via de Developer Console via Cloud Manager</td>
  </tr>
  <tr>
    <td>Replication Agents worden vervangen door Sling Content Distribution</td>
    <td></td>
    <td>Het concept van de replicatieagent wordt vervangen door de Distributie van de Inhoud van het Sing. Als er aanpassingen zijn die replicatieagenten leveraging, moeten zij worden opnieuw ontworpen.<br>Reverse Replication wordt niet ondersteund</td>
  </tr>
  <tr>
    <td>CRX/DE en de Manager van het Pakket</td>
    <td></td>
    <td>CRX/DE is toegestaan slechts op de milieu van de Ontwikkeling.<br>De Manager van het pakket is toegankelijk op alle auteursinstanties maar de pakketten die zullen worden opgesteld moeten slechts veranderbare inhoud bevatten (bijvoorbeeld: /content of /conf)</td>
  </tr>
  <tr>
    <td>Ingebouwd CDN en krijgt uw eigen CDN</td>
    <td></td>
    <td>AEM as a Cloud Service omvat CDN voor alle milieu's die voor de meeste gebruiksgevallen wordt geoptimaliseerd.<br>Als u aan opstelling uw eigen CDN wenst, moet u een verzoek aan de Steun van Adobe voor het indienen om worden goedgekeurd.<br>Als het wordt goedgekeurd, zal CDN aan Vast en niet aan AEM instanties in enige milieu's richten.</td>
  </tr>
  <tr>
    <td>Lange banen</td>
    <td></td>
    <td>Vermijd het uitvoeren van lange lopende Banen zoals het Verschuiven van Planners of de banen van het Gewas, aangezien de AEM instanties die in de containers uitvoeren op om het even welk ogenblik kunnen komen en gaan.<br>Herdenk deze functies om ze naar Adobe I/O te verplaatsen.</td>
  </tr>
  <tr>
    <td>Overschakelen naar asynchrone bewerkingen</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/asynchronous-jobs.html?lang=en#configuring-asynchronous-msm-operations">Asynchrone bewerkingen configureren</a></td>
    <td>Om de algehele prestaties van uw omgevingen te verbeteren, worden bepaalde bewerkingen uitgevoerd in de asynchrone modus. De async banen worden een rij gevormd en lopen wanneer de systeembronnen beschikbaar zijn.</td>
  </tr>
  <tr>
    <td>Tokengebaseerde verificatie- en integratiestrategieën</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#the-server-to-server-flow">Toegangstokens genereren voor server-side API's</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication">Zelfstudie over verificatie op basis van token</a></td>
    <td>Het is gebruikelijk dat systemen buiten AEM HTTP-bewerkingen binnen AEM proberen uit te voeren.<br>De geadviseerde benadering is de strategieën uit te voeren die hier eerder dan het baseren op het creëren van lokale gebruikersnamen met wachtwoorden in AEM worden geschetst.</td>
  </tr>
  <tr>
    <td>Bestands-IO/schijfgebruik</td>
    <td></td>
    <td>Aangezien er geen garantie is voor hoeveel schijfruimte wordt toegewezen en de instanties in containers komen en gaan, is het niet raadzaam de I/O-bewerkingen van het bestand te gebruiken om te schrijven of te lezen van de schijf die aan de AEM-instantie is gekoppeld.</td>
  </tr>
  <tr>
    <td>DAM Update Asset Workflow</td>
    <td><a href="https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html?lang=en">asset compute</a></td>
    <td>De stappen voor mediaverwerking die deel uitmaken van de DAM Update Asset-workflow worden nu vervangen door de Asset compute Service</td>
  </tr>
  <tr>
    <td>Methoden voor het uploaden van middelen en ondersteunde stappen voor workflowproces in AEM as a Cloud Service</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/developer-reference-material-apis.html?lang=en#post-processing-workflows-steps">Upload API-vergelijkingen en ondersteunde stappen voor het WF-proces</a></td>
    <td>In AEM as a Cloud Service, of tijdens het uploaden of het downloaden van activa stromen de activa direct in of uit binaire opslag.</br>Niet alle stappen van het werkstroomproces worden ondersteund in AEMaaCS.</td>
  </tr>
  <tr>
    <td>Workflowstartprogramma's</td>
    <td></td>
    <td>Verwijder alle werkstroomopstarters die OOTB of de aangepaste DAM Update Asset Workflow activeren uit uw code.</br>Alle in AEM as a Cloud Service geüploade activa worden door de Asset Processing Service verwerkt. Voor aangepaste stappen raadpleegt u <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=en#post-processing-workflows"> Workflows na verwerking</a> voor het instellen en configureren van workflows na verwerking.</td>
  </tr>
  <tr>
    <td>Aangepaste stappen voor vertoning</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/asset-microservices-configure-and-use.html?lang=en#manage">Profielen verwerken</a></td>
    <td>Elke aangepaste renditie, conversie van afbeeldingen of videocodering moet naar de Asset Processing Service worden verschoven door overeenkomstige verwerkingsprofielen te maken.</td>
  </tr>
  <tr>
    <td>Inhoud zoeken en indexeren</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en">Wijzigingen in zoeken en indexeren van inhoud</a></td>
    <td>Er zijn aanzienlijke veranderingen in de onderliggende verwerking van indexen en wanneer deze begint.<br>Begrijp en vernieuw volledig de Indexen van de Eik alvorens hen in de code te leiden die u zult opstellen.</td>
  </tr>
  <tr>
    <td>Niet zijn alle onderhoudstaken configureerbaar</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/maintenance.html?lang=en">as a Cloud Service onderhoudstaken AEM</a></td>
    <td>U kunt alleen bepaalde onderhoudstaken configureren met AEM as a Cloud Service.</td>
  </tr>
  <tr>
    <td>Wijzigingen in de publicatieopslagplaats</td>
    <td></td>
    <td>Directe wijzigingen in de publicatieopslagplaats zijn niet toegestaan, behalve wijzigingen onder /home. Het wordt altijd aanbevolen de wijzigingen aan te brengen bij de auteur en deze te verspreiden. Alle code en configuratieveranderingen moeten door de overeenkomstige pijpleiding van de Manager van de Wolk worden opgesteld.</td>
  </tr>
  <tr>
    <td>Dispatcher Configurations en Caching</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#content-delivery">Dispatcher in de cloud</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/caching.html?lang=en#other-content">Cachebeheer<br></td>
    <td>De Dispatcher-configuraties moeten een specifieke structuur volgen.<br>De configuraties moeten als onderdeel van code worden beheerd en via de pijplijn van de Manager van de Wolk worden opgesteld.</td>
  </tr>
  <tr>
    <td>Back-up en herstel</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/backup.html?lang=en">as a Cloud Service back-up en herstel AEM</a></td>
    <td></td>
  </tr>
  <tr>
    <td>Wijzigingen in verificatie</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html?lang=en">IMS-ondersteuning voor AEM as a Cloud Service</td>
    <td>Als u eerder SAML 2.0-integratie gebruikte op zowel auteur als publicatie voordat u naar de Cloud Service ging, is de belangrijkste wijziging dat AEM as a Cloud Service auteur alleen integreert met Adobe IMS. Nochtans, AEM de as a Cloud Service Publish rij kan nog SAML of andere authentificatieintegratie gebruiken. AEM as a Cloud Service biedt alleen ondersteuning voor IMS-verificatie voor authoring-, beheer- en ontwikkelaargebruikers. De IMS-verificatie biedt geen ondersteuning voor externe eindgebruikers van klantsites zoals sitebezoekers.</td>
  </tr>
</tbody>
</table>

## Verouderde functies {#deprecated-features}

Adobe evalueert continu de productfuncties, zodat oudere functies na verloop van tijd kunnen worden bijgewerkt of vervangen door modernere alternatieven om de algehele waarde voor de klant te verbeteren. Hierbij wordt altijd zorgvuldig gekeken naar compatibiliteit met oudere versies.

We raden u aan de [Verouderde functies](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/deprecated-removed-features.html#deprecated-features) om zich met de eigenschappen en de mogelijkheden vertrouwd te maken die als verouderd in as a Cloud Service Experience Manager zijn gemerkt en te zien wat het effect voor uw AEM plaatsing is.

## Plan voor een Herziening van uw AEM Installatie {#review-planning}

Nadat u zich met de veranderingen vertrouwd hebt gemaakt die met AEM as a Cloud Service worden geïntroduceerd, is het tijd beginnen voor een overzicht van uw bestaande installatie te plannen. Op deze manier kunt u het niveau van de vereiste wijzigingen voor het verplaatsen naar de cloud meten.

In de volgende afbeelding ziet u de belangrijkste stappen die tijdens de beoordelingsfase zijn ondernomen:

![afbeelding](/help/journey-migration/assets/planning-phaseimg1.png)

Vervolgens zullen we in detail bekijken wat elk van deze stappen betekent.

### Gereedheid van Cloud Service beoordelen {#assess-cloud-readiness}

De eerste stap is uw bereidheid te beoordelen om zich van uw bestaande AEM aan Cloud Service te bewegen en gebieden te bepalen die refactoring vereisen om met AEM as a Cloud Service compatibel te zijn.

U zult een uitvoerige beoordeling van uw huidige AEM broncode tegen de opmerkelijke veranderingen en verouderde eigenschappen moeten uitvoeren om het niveau van inspanning te bepalen die in de overgangsreis wordt verwacht.

Het aantal bevindingen zal rechtstreeks van invloed zijn op de tijdlijnen en het algehele succes van het project. Daarom wordt aangeraden om zoveel mogelijk te ontdekken dat de levering wordt gepland of dat de gesprekken worden geïnitieerd die nodig zijn om aanpassingen aan te passen aan AEM as a Cloud Service beste praktijken.

**Best Practice Analyzer**

U kunt de beoordeling versnellen door de Analysator van Beste praktijken tegen uw huidige AEM in werking te stellen. Een goed begrip van hoe het werkt is essentieel om uw evaluatie planning te versnellen.

U kunt de werking van de [Analysator van best practices](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) documentatie.

**Een Rapport voor gereedheidsevaluatie voor cloud maken**

De volgende stap is het opstellen van een verslag op basis van alle tot nu toe verworven kennis. U kunt dit doen door de rapporten van de Analysator van Beste praktijken van de Instanties van het Stadium en van de Productie te produceren, [uploaden naar Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#readiness-phase-cam) voor een verteerbaar rapport van actioneerbare producten.

Een typisch rapport moet deze input bevatten:

* Documentatie met de functieset van uw specifieke AEM-installatie
* Gegevens over uw AEM aangepaste configuraties en code
* Configuraties van productiedescripts
* CDN-configuraties (indien aanwezig)

**Het verslag socialiseren**

Nadat de rapporten van de Analysator van Beste praktijken volledig zijn, deel hen met de relevante teams zodat kunt u uw bevindingen bevestigen en voor uw volgende stappen plannen. Afhankelijk van de voorkeur, kunt u een gedrukte versie van het rapport ook verspreiden door te gebruiken [Afdrukvoorbeeld](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#print-preview-cam).

### Resourceplanning controleren {#review-resource-planning}

Zodra u het niveau van inspanning hebt geschat dat wordt vereist om zich aan Cloud Service te bewegen, zou u middelen moeten identificeren, een team tot stand brengen, en rollen en verantwoordelijkheden voor het overgangsproces in kaart brengen.

### KPI&#39;s instellen {#establish-kpis}

Als u geen Belangrijkste Indicatoren van Prestaties (KPIs) eerder hebt gevestigd, wordt het geadviseerd om KPIs voor uw AEM implementatie te vestigen om uw team te helpen zich concentreren op wat het belangrijkst is.

Zie [KPI&#39;s ontwikkelen](https://guided.adobe.com/welcome/aem/part6.html) om te leren hoe te om juiste KPIs voor uw bedrijfsdoelstellingen te kiezen.

## Volgende functies {#what-is-next}

Zodra u het werkingsgebied van de veranderingen begrijpt die worden vereist om zich aan AEM as a Cloud Service te bewegen, is het tijd om [Uw code en inhoud in de cloud klaar maken](/help/journey-migration/implementation.md) voordat de migratie daadwerkelijk wordt uitgevoerd.

## Aanvullende bronnen {#additional-resources}

* [Aan de slag met Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md) - Een uitgebreide gids over het gebruik van Cloud Acceleration Manager om sneller naar de cloud te gaan
* [AEM as a Cloud Service: Inleiding, architectuur en anders denken](https://experienceleague.adobe.com/?launch=ExperienceManager-D-1-2021.1.migration&amp;recommended=ExperienceManager-D-1-2021.1.migration&amp;lang=en#dashboard/learning)
* [Een Cloud Service thuis AEM](/help/overview/home.md) - Voor een overzicht van de as a Cloud Service documentatie van de Experience Manager, begin hier.
* [as a Cloud Service overzicht AEM](/help/overview/home.md) - Deze handleiding biedt een overzicht van Experience Manager als cloudservice, inclusief een inleiding, terminologie en architectuur.
* [Onboarding Journaal](/help/journey-onboarding/overview.md)- Deze gids verstrekt een samenvatting van hoe te beginnen met as a Cloud Service Experience Manager, met inbegrip van hoe te om toegang te krijgen en opstelling uw team
