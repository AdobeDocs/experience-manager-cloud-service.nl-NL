---
title: Aangepaste en nieuwe functies - Adobe Experience Manager as a Cloud Service
description: Aangepaste en nieuwe functies - Adobe Experience Manager (AEM) as a Cloud Service.
exl-id: d1ce126e-960c-4367-b741-af709dd81010
feature: Release Information
role: Admin
source-git-commit: 73bd693d47f37b453209208816dfed15d65e9e09
workflow-type: tm+mt
source-wordcount: '1883'
ht-degree: 66%

---

# Wat is nieuw en wat is anders {#what-is-new-and-what-is-different}

AEM is al vele jaren beschikbaar:

* On-Premise

* als een Managed Service

Er zijn intrinsieke verschillen tussen deze eerdere benaderingen en AEM as a Cloud Service:

* [Architectuur](#architecture)
* [Upgrades](#upgrades)
* [Cloud Manager](#cloud-manager)
* [Onboarding](#onboarding)
* [Ontwikkelen](#developing)
* [Exploitatie en prestaties](#operations-and-performance)
* [Identity Management](#identity-management)
* [Gebruikersinterface voor ontwerpen](#authoring-user-interface)
* [AEM Sites](#aem-sites)
* [AEM Assets](#aem-assets)

>[!NOTE]
>
>Deze overzichten zijn niet volledig, maar bedoeld als inleiding.

>[!NOTE]
>
>Voor meer details over de Versies van de Dienst Op locatie en Beheerde, zie [AEM 6.5-documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html) .

## Architectuur {#architecture}

>[!NOTE]
>
>Zie voor meer informatie [Architectuur](/help/overview/architecture.md).

AEM as a Cloud Service heeft nu:

* Een dynamische architectuur met een variabel aantal AEM-installatiekopieën.

![Dynamische architectuur](assets/introduction-03.png "Dynamische architectuur")

Deze architectuur:

* Wordt geschaald op basis van de *werkelijke* traffic en de *werkelijke* activiteit.

* Bevat afzonderlijke instanties die alleen worden uitgevoerd wanneer dat nodig is.

* Gebruikt modulaire applicaties.

* Heeft een authoringcluster als standaard; dit voorkomt uitvaltijd voor onderhoudstaken.

Hierdoor is automatische schaling mogelijk voor variërende gebruikspatronen:

![Automatisch schalen voor variërende gebruikspatronen](assets/introduction-04.png "Automatisch schalen voor variërende gebruikspatronen")


## Updates AEM {#aem-updates}

AEM as a Cloud Service gebruikt nu ononderbroken integratie en ononderbroken levering (CI/CD) om ervoor te zorgen dat uw projecten op de huidigste AEM versie zijn. Dit betekent dat de productie en het opvoeren instanties aan de recentste AEM versie zonder enige onderbreking van de dienst voor gebruikers worden bijgewerkt.

>[!NOTE]
>
>Als de update naar de productieomgeving mislukt, wordt de testomgeving automatisch teruggedraaid in Cloud Manager. Dit wordt automatisch gedaan om ervoor te zorgen dat nadat een update voltooit, zowel de het opvoeren als productiemilieu&#39;s op de zelfde AEM versie zijn.

Er zijn twee typen AEM versie-updates:

* **AEM onderhoudsupdates**

   * Kunnen dagelijks worden uitgebracht.
   * Deze bestanden zijn vooral bedoeld voor onderhoudsdoeleinden, zoals de nieuwste oplossingen voor problemen en beveiligingsupdates.
   * minimaal effect hebben, aangezien de wijzigingen regelmatig worden toegepast.

* **Nieuwe functies bijwerken**

   * Wordt vrijgegeven via een voorspelbaar maandschema.

>[!TIP]
>
>Zie voor meer informatie [Versie-updates AEM](/help/implementing/deploying/aem-version-updates.md).

## Cloud Manager {#cloud-manager}

Adobe Cloud Manager is een integraal onderdeel van de continue upgrademethode van AEM as a Cloud Service, aangezien deze alle updates voor uw instanties regelt. Dit is verplicht.

Adobe kan updates activeren wanneer er een nieuwe versie van de cloudservice beschikbaar is. U kunt de applicatie-updates ook activeren via de pijplijnen van Cloud Manager.

Cloud Manager:

* Wordt gebruikt voor het beheer van AEM-programma&#39;s en -omgevingen;

* Is een essentieel onderdeel van AEM as a Cloud Service; elke nieuwe tenant krijgt als eerste toegang tot Cloud Manager;

* Is het enige ingangspunt voor het personeel voor operations en ontwikkeling.

Met name het aantal en het type AEM-programma&#39;s dat met Cloud Manager kan worden gemaakt, zijn afgeleid van:

* De licentieovereenkomst voor klanten;

* Interne actoren wanneer AEM as a Cloud Service wordt gebruikt voor activering of training;

* Externe processen zoals testen die worden gestart vanuit Adobe.com.

Cloud Manager heeft zich ontwikkeld als een zelfbedieningsportal waar de belangrijkste onderdelen van AEM as a Cloud Service kunnen worden gemaakt en geconfigureerd:

* Nieuwe programma&#39;s maken en beheren. Zie [Programma&#39;s en programmatypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) voor meer informatie .

* De AEM omgevingen binnen deze programma&#39;s maken en beheren. Zie [Omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md) voor meer informatie .

* Het creëren van en het leiden van de pijpleidingen voor het opstellen van de klantencode en de verwante configuratie aan een specifiek milieu. Zie [Het vormen van uw CI-CD Pijpleiding](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) voor meer informatie .

* Meldingen ontvangen van belangrijke levenscyclusgebeurtenissen voor deze onderdelen (zoals productupdates).

Cloud Manager creëert omgevingen in datacenters in veel geografische regio&#39;s, wat zorgt voor wereldwijde dekking. De Punten van Aanwezigheid CDN (PoPs) verzekeren laag-latentie inhoudslevering voor klanten die over de hele wereld worden gevestigd.


## Onboarding {#onboarding}

Het starten en beheren van een AEM-project is heel eenvoudig wanneer u AEM as a Cloud Service gebruikt, omdat Adobe verantwoordelijk is voor vele aspecten:

* AEM-basisinstallatiekopieën zijn geoptimaliseerd voor specifieke gebruiksgevallen.

* Veel van de handmatige configuratietaken zijn overbodig geworden.

Er zijn ook aanzienlijke verschillen door de aanwezigheid van:

* Een beoordelingsfase om ervoor te zorgen dat aan alle voorwaarden is voldaan, waaronder:

   * Wettelijke vereisten

   * Contractuele overeenkomsten

   * Technische vereisten voor bestaande content of code die door de klant is aangepast

* Implementatievereisten:

   * Code-updates; alle klanttoepassingen die voor een vorige versie van AEM zijn ontwikkeld, moeten worden gecontroleerd en eventueel worden bijgewerkt.

   * Contentmigratie

>[!TIP]
>
>Voor een volledig overzicht van het instapproces raadpleegt u de [instapreis](/help/journey-onboarding/overview.md).

## Ontwikkelen {#developing}

>[!NOTE]
>
>Voor meer details kunt u beginnen met [Richtlijnen voor ontwikkeling](/help/implementing/developing/introduction/development-guidelines.md) en [Ontwikkelen - De WKND-zelfstudie](/help/implementing/developing/introduction/develop-wknd-tutorial.md).

De nieuwe architectuur die AEM as a Cloud Service ondersteunt, omvat een paar belangrijke wijzigingen in de algemene ontwikkelaarservaring. Een van de belangrijkste doelstellingen voor AEM as a Cloud Service is om ervaren klanten (die AEM op locatie of in de context van Adobe Managed Services hebben gebruikt) de mogelijkheid te bieden om zo snel mogelijk te migreren naar AEM as a Cloud Service, zonder het grootste deel van hun aangepaste code te hoeven herschrijven. Hiervoor zijn mogelijk wat aanpassingen vereist.

### Cloud Development {#aem-as-a-cloud-service-developing-cloud-development}

Voor bestaande AEM-applicaties die worden uitgevoerd in AEM as a Cloud Service, worden de volgende stappen verwacht:

* De applicatiecode en -configuratie moeten worden opgeslagen in de Git-code-repository van het bijbehorende Cloud Manager-programma.
* De applicatiecode en -configuratie moeten compatibel zijn met de nieuwste versie van de AEM-basisinstallatiekopie (die dagelijks kan wijzigen).
   * De klantapplicatie moet worden gebouwd en geïmplementeerd met behulp van de Cloud Manager-pijplijn die is gekoppeld aan de Cloud Manager-omgeving.
* De klantapplicatie moet alle &#39;gates&#39; voor codekwaliteit, veiligheid en prestatie in de pijplijn passeren.
* De installatiekopieën die voor de klantapplicatie zijn gemaakt, moeten door de Cloud Manager-pijplijn worden geïmplementeerd.

Dit proces wordt meestal &#39;Cloud-first&#39;-ontwikkeling genoemd. Aangezien de &#39;end-to-end&#39; duur naar verwachting minuten in beslag zal nemen (van 20 tot 50, afhankelijk van de complexiteit van de applicatie), is het noodzakelijk om methoden voor snelle ontwikkeling te gebruiken voordat de code en configuratiewijzigingen in de cloud worden uitgeprobeerd.

De console van het Web, waar de bundels OSGI en hun bijbehorende configuratie worden beheerd, en eerder deel van AEM QuickStart, is niet meer beschikbaar in AEM as a Cloud Service. De nieuwe ontwikkelaarsconsole verstrekt een read-only interface voor de meeste runtime informatie. Met deze console, kunnen de ontwikkelaars en login rechtstreeks aan om het even welk bepaald knooppunt van een auteur selecteren of de publicatieservice, en de relevante informatie bekijken.

>[!NOTE]
>
>Zie ook [OSGi-configuratie](/help/implementing/deploying/overview.md#osgi-configuration)

Een andere veelvoorkomende eis voor ontwikkelaars is snelle toegang tot de logbestanden van de verschillende omgevingen. Met AEM as a Cloud Service worden de logbestanden van de verschillende nodes in de authoring- en publicatienode beschikbaar gesteld via Cloud Manager, in de vorm van bestanden die kunnen worden gedownload, of via API&#39;s.

Dankzij de duidelijke scheiding van code en content kunnen ontwikkelaars een bepaald proces gebruiken voor het bijwerken van content als onderdeel van een implementatie. Vaak voorkomende gebruiksgevallen van veranderlijke content zijn:

* Standaard *default* inhoud die deel uitmaakt van het klantenproject (bijvoorbeeld mappen, sjablonen, workflows, enzovoort)

* Zoekindexdefinities

* ACL&#39;s en toestemmingen

* Servicegebruikers en -gebruikersgroepen

### Lokale ontwikkeling {#aem-as-a-cloud-service-developing-local-development}

Om snelle herhalingen en ontwikkeling te ondersteunen, is het ook mogelijk om AEM toepassingen buiten de AEM as a Cloud Service context te ontwikkelen. Daarvoor worden de volgende artefacten aan de ontwikkelaars ter beschikking gesteld:

* AEM as a Cloud Service QuickStart: een `.jar`-gebaseerd, zelfstandig installatieprogramma van de nieuwste AEM-codebase, met hetzelfde functionele en API-oppervlak.

* AEM as a Cloud Service Dispatcher SDK: een op de installatiekopie gebaseerd proces voor het lokaal testen en valideren van Dispatcher-configuraties

>[!NOTE]
>
>Houd er rekening mee dat in Cloud QuickStart niet alle functies van AEM Sites en AEM Assets mogelijk zijn. Het programma bestaat uit een eenvoudige authoringomgeving waar de meeste uitbreidingen kunnen worden ontwikkeld en getest.

## Exploitatie en prestaties {#operations-and-performance}

>[!NOTE]
>
>Voor meer details, begin met [inhoudsherstel](/help/operations/restore.md), [Indexeren](/help/operations/indexing.md), en [overige onderhoudstaken](/help/operations/maintenance.md).

Met AEM as a Cloud Service worden dergelijke bewerkingen geautomatiseerd, zodat de service niet meer hoeft te worden onderbroken.

Op deze gebieden:

* Zijn veel taken geautomatiseerd.

* Zijn topologieën geoptimaliseerd voor maximale flexibiliteit en efficiëntie; zo is de standaard bijvoorbeeld &#39;binary-less&#39; replicatie.

* Zijn zwaar belastende taken zoals wachtrijen, taken en bulkverwerkingstaken uit de kern van de AEM-instantie verplaatst en worden deze afgehandeld door gedeelde en speciale microservices.

Bewerkingen voor AEM as a Cloud Service worden ook ondersteund door een nieuwe infrastructuur voor bewaking, rapportage en waarschuwingen. Hierdoor kunnen de Adobe SRE&#39;s (Site Reliability Engineers) de service proactief gezond houden. De verschillende elementen van de architectuur zijn uitgerust met diverse statuscontroles. Als om een of andere reden een bepaalde node van de architectuur ongezond wordt bevonden, wordt het uit de service verwijderd en stilzwijgend vervangen door een nieuwe, gezonde node.

## Identity Management {#identity-management}

>[!NOTE]
>
>Zie [Beveiliging - IMS-ondersteuning](/help/security/ims-support.md).

Een belangrijke wijziging in AEM as Cloud Service is het volledig geïntegreerde gebruik van Adobe ID&#39;s voor toegang tot de authoringlaag.

Hiervoor moet de [Adobe Admin Console](https://helpx.adobe.com/nl/enterprise/using/admin-console.html) worden gebruikt om gebruikers en gebruikersgroepen te beheren. Met gebruikersaccounts hebben uw gebruikers toegang tot Adobe-producten en -services, aangezien gebruikersprofielgegevens zijn gecentraliseerd in het Adobe Identity Management System (IMS) en deze gegevens worden gedeeld door alle cloudservices. Zodra de gebruikersaccounts toegang tot AEM hebben gekregen, kan er in AEM as a Cloud Service naar worden verwezen (zoals vroeger), bijvoorbeeld voor het definiëren van rollen en toestemmingen vanuit de gebruikersinterfaces van AEM Security.

Dit biedt een combinatie van de volgende voordelen:

* U kunt Adobe Identity Management System (IMS) gebruiken om u één keer aan te melden voor alle Adobe-cloudapplicaties.

* Gebruikersvoorkeuren blijven lokaal voor elke specifieke instantie van AEM as a Cloud Service.

## Gebruikersinterface voor ontwerpen {#authoring-user-interface}

>[!NOTE]
>
>Voor meer details, [Basisverwerking](/help/sites-cloud/authoring/basic-handling.md) is een goed uitgangspunt.

De basisbeginselen van de authoringgebruikersinterface (UI), zowel voor Sites als Assets, zullen heel vertrouwd zijn voor iedereen die AEM vroeger heeft gebruikt.

Het belangrijkste verschil is dat de gebruikersinterface alleen met aanraking werkt. De klassieke interface is niet meer beschikbaar. Verder zijn de basisbeginselen ongewijzigd, met alleen kleine zichtbare wijzigingen.

## AEM Sites {#aem-sites}

Met Adobe Experience Manager Sites as a Cloud Service kunt u uw klanten persoonlijke, contentgestuurde ervaringen bieden door de kracht van het AEM Content Management System te combineren met AEM Digital Asset Management.

Zie het overzicht van [Wijzigingen in Sites](/help/sites-cloud/sites-cloud-changes.md) voor meer informatie.

## AEM Assets {#aem-assets}

Adobe Experience Manager Assets as a Cloud Service biedt een cloud-native PaaS-oplossing voor bedrijven om niet alleen hun activiteiten op het gebied van Digital Asset Management en Dynamic Media met snelheid en impact uit te voeren, maar ook intelligente mogelijkheden van de volgende generatie, zoals AI/ML, te gebruiken vanuit een systeem dat altijd actueel, altijd beschikbaar en altijd leerend is.

Het Assets-aanbod omvat assetverwerking van de volgende generatie in de cloud, en hoogkwalitatieve opname en zoekfunctie van assets.

Zie [overzicht en inleiding tot Assets as a Cloud Service](/help/assets/overview.md) voor meer informatie.

## Adobe Experience Manager as a Cloud Service leren kennen {#getting-to-know-aem-as-cloud-service}

Zie voor meer informatie:

* [Inleiding tot Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
* De [architectuur](/help/overview/architecture.md) van Adobe Experience Manager as a Cloud Service
* [Opvallende wijzigingen in AEM as a Cloud Service (opmerkingen bij de release)](/help/release-notes/aem-cloud-changes.md)
* [Opvallende wijzigingen in AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
* [Opvallende wijzigingen in AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)
* [Introductie van AEM Assets as a Cloud Service](/help/assets/overview.md)
* [Tutorials voor Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html)

>[!TIP]
>
>Wanneer u een overzicht hebt van AEM as a Cloud Service, kunt u snel aan boord gaan door het [Onboarding Journaal](/help/journey-onboarding/overview.md).
>
>Hebt u al een functie voor het testen van AEM? Installeer de [AEM Reference Demos Add-on](/help/journey-sites/demos-add-on/overview.md) om AEM krachtige functies te verkennen aan de hand van rijke voorbeelden.
