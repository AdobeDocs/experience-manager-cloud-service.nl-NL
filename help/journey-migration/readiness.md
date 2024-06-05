---
title: Gereedheidsfase
description: Leer meer over de stappen die u moet ondernemen om ervoor te zorgen dat uw AEM installatie klaar is om naar de cloud te worden verplaatst.
exl-id: 3bc8c037-d82a-4455-bce6-3c80c359a4ae
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1900'
ht-degree: 1%

---

# Gereedheidsfase {#readiness-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_planning"
>title="Overgang plannen"
>abstract="Voordat u begint met de overgang naar de Cloud Service, moet u zich vertrouwd maken met AEM as a Cloud Service. Bekijk de opmerkelijke wijzigingen die erin zijn aangebracht en de functies die zijn vervangen of vervangen."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html" text="Analysator van best practices"

In deze fase van de AEM as a Cloud Service Migratiereis, vertrouwt u zich met AEM as a Cloud Service. U kunt de belangrijkste wijzigingen die zijn geïntroduceerd bekijken en begrijpen wat nodig is om een geslaagde migratie naar de cloud te plannen.

## Het verhaal tot nu toe {#story-so-far}

Het vorige document, [Aan de slag met Verplaatsen naar AEM as a Cloud Service](/help/journey-migration/getting-started.md)schetst u een lijst met fasen die u moet doorlopen voordat u kunt migreren naar AEM as a Cloud Service. Het schetst ook de voordelen van migratie.

## Doelstelling {#objective}

Dit document helpt u te begrijpen welke factoren u moet overwegen zodat u ervoor kunt zorgen dat uw AEM installatie klaar is om naar de cloud te worden verplaatst:

* Meer informatie over opmerkelijke wijzigingen en verouderde functies
* Begrijp hoe te voor de migratie aan AEM as a Cloud Service plannen

## Bekijk de opmerkelijke veranderingen in de AEM as a Cloud Service Architectuur {#notable-changes-in-aem-cloud-service-architecture}

AEM as a Cloud Service brengt vele nieuwe eigenschappen en mogelijkheden voor het beheren van uw AEMProjecten.

Samen met deze verbeteringen zijn er verschillende verschillen ontstaan tussen installaties op locatie van AEM en Adobe Managed Services, in vergelijking met AEM as a Cloud Service.

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
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html">as a Cloud Service opmerkelijke wijzigingen AEM</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html#mutable-vs-immutable">AEM projectstructuur voor AEM as a Cloud Service</a></td>
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
    <td>Alleen uitvoeringsmodi die buiten het vak met AEM as a Cloud Service zijn opgegeven, worden ondersteund.<br>Wanneer extra ontwikkelomgevingen worden toegevoegd, worden ze allemaal gekoppeld aan de "dev"-uitvoeringsmodus.</td>
  </tr>
  <tr>
    <td>Uitvoeren van de pijplijn van de Manager van de wolk is de enige manier om op te stellen</td>
    <td></td>
    <td>In AEM as a Cloud Service, is de toegang tot /system/console niet toegestaan, vandaar moeten alle configuraties OSGi deel van code uitmaken, en zouden als code moeten worden opgesteld.<br>De OSGi-configuraties zijn beschikbaar in de modus Alleen-lezen en kunnen worden bekeken via de Developer Console via Cloud Manager</td>
  </tr>
  <tr>
    <td>Replication Agents worden vervangen door Sling Content Distribution</td>
    <td></td>
    <td>Het concept van de replicatieagent wordt vervangen door de Distributie van de Inhoud van Sing. Als er aanpassingen zijn die replicatieagenten gebruiken, moeten zij worden opnieuw ontworpen.<br>Reverse Replication wordt niet ondersteund</td>
  </tr>
  <tr>
    <td>CRX/DE en de Manager van het Pakket</td>
    <td></td>
    <td>CRX/DE is toegestaan slechts op de milieu van de Ontwikkeling.<br>De Manager van het pakket is toegankelijk op alle auteursinstanties maar de pakketten die zullen worden opgesteld moeten slechts veranderbare inhoud (bijvoorbeeld: /content of /conf) bevatten</td>
  </tr>
  <tr>
    <td>Ingebouwd CDN en krijgt uw eigen CDN</td>
    <td></td>
    <td>AEM as a Cloud Service omvat CDN voor alle milieu's die voor de meeste gebruiksgevallen wordt geoptimaliseerd.<br>Als u opstelling uw eigen CDN wilt, moet u een verzoek aan de Steun van de Adobe voor het indienen om worden goedgekeurd.<br>Als het wordt goedgekeurd, wijst CDN aan Vast en niet aan AEM instanties in om het even welke milieu's.</td>
  </tr>
  <tr>
    <td>Lange banen</td>
    <td></td>
    <td>Vermijd lange lopende Banen zoals het Verschuiven van Planners of de banen van het Gewas, aangezien de AEM instanties die in de containers lopen op om het even welk punt kunnen komen en gaan.<br>U kunt deze functies opnieuw bekijken zodat u ze naar Adobe Developer kunt verplaatsen.</td>
  </tr>
  <tr>
    <td>Overschakelen naar asynchrone bewerkingen</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/asynchronous-jobs.html#configuring-asynchronous-msm-operations">Asynchrone bewerkingen configureren</a></td>
    <td>Om de algemene prestaties van uw milieu's te verbeteren, worden bepaalde verrichtingen in asynchrone wijze in werking gesteld. De async banen worden een rij gevormd en lopen wanneer de systeemmiddelen beschikbaar zijn.</td>
  </tr>
  <tr>
    <td>Tokengebaseerde verificatie- en integratiestrategieën</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html#the-server-to-server-flow">Toegangstokens genereren voor server-side API's</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html#authentication">Zelfstudie over verificatie op basis van token</a></td>
    <td>Het is gebruikelijk dat systemen buiten de AEM HTTP-bewerkingen binnen AEM uitvoeren.<br>De geadviseerde benadering is de strategieën uit te voeren die hier eerder dan het baseren op het creëren van lokale gebruikersnamen met wachtwoorden in AEM worden geschetst.</td>
  </tr>
  <tr>
    <td>Bestands-IO/schijfgebruik</td>
    <td></td>
    <td>Er is geen garantie voor hoeveel schijfruimte wordt toegewezen en de instanties in containers komen en gaan. Daarom is het niet aan te raden bestands-I/O-bewerkingen te gebruiken om te schrijven of te lezen vanaf de schijf die aan de AEM-instantie is gekoppeld.</td>
  </tr>
  <tr>
    <td>DAM Update Asset Workflow</td>
    <td><a href="https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html">Asset compute</a></td>
    <td>De stappen voor mediaverwerking die deel uitmaken van de DAM Update Asset-workflow worden nu vervangen door de Asset compute Service</td>
  </tr>
  <tr>
    <td>Methoden voor het uploaden van middelen en ondersteunde stappen voor workflowproces in AEM as a Cloud Service</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/developer-reference-material-apis.html#post-processing-workflows-steps">Upload API-vergelijkingen en ondersteunde stappen voor het WF-proces</a></td>
    <td>In AEM as a Cloud Service, of tijdens het uploaden of het downloaden van activa stromen de activa direct binnen of uit binaire opslag. <br>Niet alle stappen van het werkstroomproces worden ondersteund in AEMaaCS.</td>
  </tr>
  <tr>
    <td>Workflowstartprogramma's</td>
    <td></td>
    <td>Verwijder om het even welke Lanceerders van het Werkschema die of uit-van-de-doos of de douaneWerkschema van het Activa van de Update DAM uit uw code teweegbrengen. <br>Alle in AEM as a Cloud Service geüploade activa worden door de Asset Processing Service verwerkt. Zie voor aangepaste stappen <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html#post-processing-workflows"> Workflows na verwerking</a> voor het instellen en configureren van workflows na verwerking.</td>
  </tr>
  <tr>
    <td>Aangepaste stappen voor vertoning</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html">Profielen verwerken</a></td>
    <td>Elke aangepaste renditie, afbeeldingsconversie of videocodering moet naar de Asset Processing Service worden verschoven door de bijbehorende verwerkingsprofielen te maken.</td>
  </tr>
  <tr>
    <td>Inhoud zoeken en indexeren</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html">Wijzigingen in zoeken en indexeren van inhoud</a></td>
    <td>Er zijn aanzienlijke veranderingen in de onderliggende verwerking van indexen en wanneer deze begint.<br>Begrijp en vernieuw volledig de Indexen van de Eik alvorens hen in de code te beheren die u opstelt.</td>
  </tr>
  <tr>
    <td>Niet zijn alle onderhoudstaken configureerbaar</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/maintenance.html">as a Cloud Service onderhoudstaken AEM</a></td>
    <td>U kunt slechts bepaalde onderhoudstaken met AEM as a Cloud Service vormen.</td>
  </tr>
  <tr>
    <td>Wijzigingen in de publicatieopslagplaats</td>
    <td></td>
    <td>Directe wijzigingen in de publicatieopslagplaats zijn niet toegestaan, behalve wijzigingen onder /home. Het wordt altijd aanbevolen om eventuele wijzigingen die zijn aangebracht op de auteur, te verspreiden. Alle code en configuratieveranderingen moeten door de overeenkomstige pijpleiding van de Manager van de Wolk worden opgesteld.</td>
  </tr>
  <tr>
    <td>Dispatcher Configurations en Caching</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html">Dispatcher in de cloud</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/caching.html#other-content">Cachebeheer<br></td>
    <td>De Dispatcher-configuraties moeten een specifieke structuur volgen.<br>De configuraties moeten als onderdeel van code worden beheerd en via de pijplijn van de Manager van de Wolk worden opgesteld.</td>
  </tr>
  <tr>
    <td>Back-up en herstel</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/backup.html">as a Cloud Service back-up en herstel AEM</a></td>
    <td></td>
  </tr>
  <tr>
    <td>Wijzigingen in verificatie</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html">IMS-ondersteuning voor AEM as a Cloud Service</td>
    <td>Als u eerder SAML 2.0-integratie op zowel auteur als publicatie gebruikte voordat u naar Cloud Service ging, is de belangrijkste wijziging dat AEM as a Cloud Service auteur alleen integreert met Adobe IMS. Nochtans, AEM de as a Cloud Service Publish rij kan nog SAML of andere authentificatieintegratie gebruiken. AEM as a Cloud Service biedt alleen ondersteuning voor IMS-verificatie voor auteur-, Admin- en Dev-gebruikers. De IMS-verificatie biedt geen ondersteuning voor externe eindgebruikers van klantsites zoals sitebezoekers.</td>
  </tr>
</tbody>
</table>

## Verouderde functies {#deprecated-features}

Adobe evalueert continu de productfuncties, zodat oudere functies na verloop van tijd kunnen worden bijgewerkt of vervangen door modernere alternatieven om de algehele waarde voor de klant te verbeteren. Hierbij wordt altijd zorgvuldig gekeken naar compatibiliteit met oudere versies.

Adobe beveelt aan dat u [Verouderde functies](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/deprecated-removed-features.html#deprecated-features) om u vertrouwd te maken met de functies en mogelijkheden die zijn gemarkeerd als verouderd in as a Cloud Service Experience Manager. Bekijk wat de impact is op uw AEM implementatie.

## Plan voor een Herziening van uw AEM Installatie {#review-planning}

Nadat u zich met de veranderingen vertrouwd hebt gemaakt die met AEM as a Cloud Service worden geïntroduceerd, is het tijd beginnen voor een overzicht van uw bestaande installatie te plannen. Op deze manier kunt u het niveau van de vereiste wijzigingen voor het verplaatsen naar de cloud meten.

In de volgende afbeelding ziet u de belangrijkste stappen die tijdens de beoordelingsfase zijn ondernomen:

![afbeelding](/help/journey-migration/assets/planning-phaseimg1.png)

Hierna gaat u na wat elk van deze stappen in detail betekent.

### Gereedheid van Cloud Service beoordelen {#assess-cloud-readiness}

De eerste stap is uw bereidheid te beoordelen om zich van uw bestaande AEM aan Cloud Service te bewegen en gebieden te bepalen die refactoring vereisen om met AEM as a Cloud Service compatibel te zijn.

Voer een uitgebreide beoordeling van uw huidige AEM broncode uit tegen de opmerkelijke veranderingen en verouderde eigenschappen om het niveau van inspanning te bepalen die in de overgangsreis wordt verwacht.

Het aantal bevindingen kan rechtstreeks van invloed zijn op de tijdlijnen en het algehele succes van het project. Daarom adviseert de Adobe dat u zoveel mogelijk ontdekt zodat u de levering kunt plannen. U kunt ook gesprekken starten zodat u aanpassingen opnieuw kunt ontwerpen die nodig zijn om aan te sluiten bij AEM as a Cloud Service best practices.

**Best Practice Analyzer**

U kunt de beoordeling versnellen door de Analysator van Beste praktijken tegen uw huidige AEM in werking te stellen. Een goed begrip van hoe het werkt is essentieel om uw evaluatie planning te versnellen.

U kunt de werking van de [Analysator van best practices](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) documentatie.

**Een Rapport voor gereedheidsevaluatie voor cloud maken**

De volgende stap is het opstellen van een verslag op basis van alle tot nu toe verworven kennis. U maakt het rapport door de rapporten van de Analysator van Beste praktijken van de Instanties van het Stadium en van de Productie te produceren, [uploadt u deze vervolgens naar Cloud AccelerManager](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#readiness-phase-cam) voor een verteerbaar rapport van actioneerbare producten.

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

Zie [KPI&#39;s ontwikkelen](https://experienceleague.adobe.com/welcome/aem/part6.html) zodat kunt u leren hoe te om juiste KPIs voor uw bedrijfsdoelstellingen te kiezen.

## Volgende functies {#what-is-next}

Zodra u het werkingsgebied van de veranderingen begrijpt die worden vereist om zich aan AEM as a Cloud Service te bewegen, is het tijd om [Uw code en inhoud in de cloud klaar maken](/help/journey-migration/implementation.md) voordat de migratie daadwerkelijk wordt uitgevoerd.

## Aanvullende bronnen {#additional-resources}

* [Aan de slag met Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md) - Een uitgebreide handleiding voor het gebruik van Cloud Acceleration Manager om sneller naar de cloud te gaan.
* [AEM as a Cloud Service: Introductie, architectuur en anders denken](https://experienceleague.adobe.com/?launch=ExperienceManager-D-1-2021.1.migration&amp;recommended=ExperienceManager-D-1-2021.1.migration&amp;lang=en#dashboard/learning)
* [Een Cloud Service thuis AEM](/help/overview/introduction.md) - Voor een overzicht van de as a Cloud Service documentatie van de Experience Manager, begin hier.
* [as a Cloud Service overzicht AEM](/help/overview/introduction.md) - Deze handleiding biedt een overzicht van Experience Manager als cloudservice, inclusief een inleiding, terminologie en architectuur.
* [Onboarding Journaal](/help/journey-onboarding/overview.md)- Deze gids verstrekt een samenvatting van hoe te beginnen met as a Cloud Service Experience Manager, met inbegrip van hoe te om toegang te krijgen en uw team te vestigen.
