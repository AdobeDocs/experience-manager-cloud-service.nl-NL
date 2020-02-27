---
title: Aangepaste en nieuwe functies - Adobe Experience Manager as a Cloud Service
description: 'Aangepaste en nieuwe functies - Adobe Experience Manager (AEM) as a Cloud Service. '
translation-type: tm+mt
source-git-commit: 160db0dabc99eccdef5bd579f8ccc26a861b1380

---


# Nieuwe en aangepaste functies {#what-is-new-and-what-is-different}

AEM is al vele jaren beschikbaar:

* On-Premise

* als een Managed Service

Er zijn intrinsieke verschillen tussen deze eerdere benaderingen en AEM as a Cloud Service:

* [Architectuur](#architecture)
* [Upgrades](#upgrades)
* [Cloud Manager](#cloud-manager)
* [On-boarding](#onboarding)
* [Ontwikkeling](#developing)
* [Bewerkingen en prestaties](#operations-and-performance)
* [Identity Management](#identity-management)
* [Gebruikersinterface voor authoring](#authoring-user-interface)
* [AEM Sites](#aem-sites)
* [AEM Assets](#aem-assets)

>[!NOTE]
>
>Deze overzichten zijn niet volledig, maar bedoeld als inleiding.

>[!NOTE]
>
>Raadpleeg de documentatieset voor [AEM 6.5](https://helpx.adobe.com/support/experience-manager/6-5.html) voor meer informatie over de versies On-Premise en Managed Service.

## Architectuur {#architecture}

>[!NOTE]
>
>Zie [Architectuur](/help/core-concepts/architecture.md) voor meer informatie.

AEM as a Cloud Service heeft nu:

* Een dynamische architectuur met een variabel aantal AEM-installatiekopieën.

![Dynamische architectuur](assets/introduction-03.png "Dynamische architectuur")

Deze architectuur:

* Wordt geschaald op basis van het *werkelijke* verkeer en de *werkelijke* activiteit.

* Bevat afzonderlijke instanties die alleen worden uitgevoerd wanneer dat nodig is.

* Gebruikt modulaire applicaties.

* Heeft een authoringcluster als standaard; dit voorkomt uitvaltijd voor onderhoudstaken.

Hierdoor is automatische schaling mogelijk voor variërende gebruikspatronen:

![Automatisch schalen voor variërende gebruikspatronen](assets/introduction-04.png "Automatisch schalen voor variërende gebruikspatronen")


## Upgrades {#upgrades}

>[!NOTE]
>
>Voor meer details zie de [het Opstellen Inleiding](/help/implementing/deploying/overview.md).

AEM as a Cloud Service gebruikt nu Continuous Integration en Continuous Delivery (CI/CD) om ervoor te zorgen dat uw projecten volledig up-to-date zijn. Dit betekent dat alle upgradebewerkingen volledig geautomatiseerd zijn, en de gebruikers dus geen onderbreking van de service ervaren.

Adobe zorgt proactief voor het updaten van alle operationele instanties van de service naar de nieuwste versie van de AEM-codebasis:

* Bugfixes:

   * Kunnen dagelijks worden uitgebracht.

   * Instanties worden vaak bijgewerkt met de recentste bugfixes. Aangezien veranderingen regelmatig worden toegepast, is het effect cumulatief, wat minder invloed heeft op uw service.

   * De meeste updates betreffen onderhouds- en beveiligingskwesties.

* Nieuwe functies:

   * Worden uitgebracht via een voorspelbaar maandschema.

>[!NOTE]
>
>Zie [Implementatiearchitectuur](/help/core-concepts/architecture.md#deployment-architecture) voor meer informatie.

## Cloud Manager {#cloud-manager}

Adobe Cloud Manager is een integraal onderdeel van de continue upgrademethode van AEM as a Cloud Service, aangezien deze alle updates voor uw instanties regelt. Dit is verplicht.

Adobe kan updates activeren wanneer er een nieuwe versie van de cloudservice beschikbaar is. U kunt de applicatie-updates ook activeren via de pijplijnen van Cloud Manager.

Cloud Manager:

* Wordt gebruikt voor het beheer van AEM-programma&#39;s en -omgevingen;

* Is een essentieel onderdeel van AEM as a Cloud Service; elke nieuwe tenant krijgt als eerste toegang tot Cloud Manager;

* Is het enige ingangspunt voor het personeel voor operations en ontwikkeling.

Met name het aantal en het type AEM-programma&#39;s dat met Cloud Manager kan worden gemaakt, zijn afgeleid van:

* van de licentieovereenkomst voor klanten,

* Interne actoren wanneer AEM as a Cloud Service wordt gebruikt voor activering of training;

* Externe processen zoals testen die worden gestart vanuit Adobe.com.

Cloud Manager heeft zich ontwikkeld als een zelfbedieningsportal waar de belangrijkste onderdelen van AEM as a Cloud Service kunnen worden gemaakt en geconfigureerd:

* Nieuwe programma&#39;s maken en beheren.

* De AEM-omgevingen binnen deze programma&#39;s maken en beheren.

* De pijplijnen creëren en beheren voor implementatie van de klantcode en de bijbehorende configuratie in een bepaalde omgeving.

* Meldingen ontvangen van belangrijke levenscyclusgebeurtenissen voor deze onderdelen (zoals productupdates).

Cloud Manager kan omgevingen maken in drie geografische regio&#39;s (meer regio&#39;s zullen volgen):

* VS (Oost)

* EMEA (Nederland)

* APAC (Australië)

## On-boarding {#onboarding}

>[!NOTE]
>
>For further details see [Onboarding](/help/onboarding/home.md).

Het starten en beheren van een AEM-project is eenvoudig wanneer u AEM gebruikt als cloudservice omdat Adobe verantwoordelijk is voor vele aspecten:

* AEM-basisinstallatiekopieën zijn geoptimaliseerd voor specifieke gebruiksgevallen.

* Veel van de handmatige configuratietaken zijn overbodig geworden.

Er zijn ook aanzienlijke verschillen door de aanwezigheid van:

* Een beoordelingsfase om ervoor te zorgen dat aan alle voorwaarden is voldaan, waaronder:

   * Wettelijke vereisten

   * Contractuele overeenkomsten

   * Technische vereisten voor bestaande content of code die door de klant is aangepast

* Implementatievereisten:

   * Code-updates; alle klantapplicaties die voor een vorige versie van AEM zijn ontwikkeld, moeten worden herzien en mogelijk bijgewerkt.

   * Contentmigratie

## Ontwikkeling {#developing}

>[!NOTE]
>
>Voor meer informatie kunt u beginnen met [Ontwikkelingsrichtlijnen](/help/implementing/developing/introduction/development-guidelines.md) en [Ontwikkelen - de WKND-zelfstudie](/help/implementing/developing/introduction/develop-wknd-tutorial.md).

De nieuwe architectuur die AEM as a Cloud Service ondersteunt, omvat een paar belangrijke wijzigingen in de algemene ontwikkelaarservaring. Een van de belangrijkste doelstellingen voor AEM as a Cloud Service is om ervaren klanten (die AEM op locatie of in de context van Adobe Managed Services hebben gebruikt) de mogelijkheid te bieden om zo snel mogelijk te migreren naar AEM as a Cloud Service, zonder het grootste deel van hun aangepaste code te hoeven herschrijven. Hiervoor zijn mogelijk wat aanpassingen vereist.

### Cloudontwikkeling {#aem-as-a-cloud-service-developing-cloud-development}

Voor bestaande AEM-applicaties die worden uitgevoerd in AEM as a Cloud Service, worden de volgende stappen verwacht:

* De applicatiecode en -configuratie moeten worden opgeslagen in de Git-code-repository van het bijbehorende Cloud Manager-programma.
* De applicatiecode en -configuratie moeten compatibel zijn met de nieuwste versie van de AEM-basisinstallatiekopie (die dagelijks kan wijzigen).
   * De klantapplicatie moet worden gebouwd en geïmplementeerd met behulp van de Cloud Manager-pijplijn die is gekoppeld aan de Cloud Manager-omgeving.
* De klantapplicatie moet alle &#39;gates&#39; voor codekwaliteit, veiligheid en prestatie in de pijplijn passeren.
* De installatiekopieën die voor de klantapplicatie zijn gemaakt, moeten door de Cloud Manager-pijplijn worden geïmplementeerd.

Dit proces wordt meestal &#39;Cloud-first&#39;-ontwikkeling genoemd. Aangezien de &#39;end-to-end&#39; duur naar verwachting minuten in beslag zal nemen (van 20 tot 50, afhankelijk van de complexiteit van de applicatie), is het noodzakelijk om methoden voor snelle ontwikkeling te gebruiken voordat de code en configuratiewijzigingen in de cloud worden uitgeprobeerd.

De webconsole, waar OSGI-bundels en de bijbehorende configuratie worden beheerd en die voorheen deel uitmaakte van de AEM QuickStart, is niet meer rechtstreeks toegankelijk voor gebruikers in een omgeving van AEM as a Cloud Service. Deze interface is in de modus voor alleen-lezen nog toegankelijk door een nieuwe ontwikkelaarsconsole te gebruiken. Met deze console kunnen de ontwikkelaars rechtstreeks elke node van een authoring- of publicatieservice selecteren en zich aanmelden, en vervolgens naar de gebieden gaan die standaard zijn geblokkeerd.

>[!NOTE]
>
>Zie ook Configuratie [OSGi](/help/implementing/deploying/overview.md#osgi-configuration)

Een andere veelvoorkomende eis voor ontwikkelaars is snelle toegang tot de logbestanden van de verschillende omgevingen. Met AEM as a Cloud Service worden de logbestanden van de verschillende nodes in de authoring- en publicatienode beschikbaar gesteld via Cloud Manager, in de vorm van bestanden die kunnen worden gedownload, of via API&#39;s.

Dankzij de duidelijke scheiding van code en content kunnen ontwikkelaars een bepaald proces gebruiken voor het bijwerken van content als onderdeel van een implementatie. Vaak voorkomende gebruiksgevallen van veranderlijke content zijn:

* *Standaard* content die deel uitmaakt van het klantproject (bijvoorbeeld mappen, sjablonen, workflows, enz.)

* Zoekindexdefinities

* ACL&#39;s en toestemmingen

* Servicegebruikers en -gebruikersgroepen

### Lokale ontwikkeling {#aem-as-a-cloud-service-developing-local-development}

Om snelle herhalingen en ontwikkeling te ondersteunen is het ook mogelijk om AEM-applicaties buiten de context van AEM as a Cloud Service te ontwikkelen. Daarvoor worden de volgende artefacten aan de ontwikkelaars ter beschikking gesteld:

* AEM as a Cloud Service QuickStart: een `.jar`-gebaseerd, zelfstandig installatieprogramma van de nieuwste AEM-codebase, met hetzelfde functionele en API-oppervlak.

* AEM as a Cloud Service Dispatcher SDK: een op de installatiekopie gebaseerd proces voor het lokaal testen en valideren van Dispatcher-configuraties

>[!NOTE]
>
>Houd er rekening mee dat in Cloud QuickStart niet alle functies van AEM Sites en AEM Assets mogelijk zijn. Het programma bestaat uit een eenvoudige authoringomgeving waar de meeste uitbreidingen kunnen worden ontwikkeld en getest.

## Bewerkingen en prestaties {#operations-and-performance}

>[!NOTE]
>
>Begin met [Back-up](/help/operations/backup.md), [Indexering](/help/operations/indexing.md) en [andere Onderhoudstaken](/help/operations/maintenance.md) voor meer details.

Met AEM as a Cloud Service worden dergelijke bewerkingen geautomatiseerd, zodat de service niet meer hoeft te worden onderbroken.

Op deze gebieden:

* Zijn veel taken geautomatiseerd.

* Zijn topologieën geoptimaliseerd voor maximale flexibiliteit en efficiëntie; zo is de standaard bijvoorbeeld &#39;binary-less&#39; replicatie.

* Zijn zwaar belastende taken zoals wachtrijen, taken en bulkverwerkingstaken uit de kern van de AEM-instantie verplaatst en worden deze afgehandeld door gedeelde en speciale microservices.

Bewerkingen voor AEM as a Cloud Service worden ook ondersteund door een nieuwe infrastructuur voor bewaking, rapportage en waarschuwingen. Hierdoor kunnen de Adobe SRE&#39;s (Site Reliability Engineers) de service proactief gezond houden. De verschillende elementen van de architectuur zijn uitgerust met diverse statuscontroles. Als om een of andere reden een bepaalde node van de architectuur ongezond wordt bevonden, wordt het uit de service verwijderd en stilzwijgend vervangen door een nieuwe, gezonde node.

## Identity Management {#identity-management}

>[!NOTE]
>
>Zie [Beveiliging - IMS-ondersteuning](/help/security/ims-support.md)voor meer informatie.

Een belangrijke wijziging in AEM as Cloud Service is het volledig geïntegreerde gebruik van Adobe ID&#39;s voor toegang tot de authoringlaag.

Hiervoor moet de [Adobe Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html) worden gebruikt om gebruikers en gebruikersgroepen te beheren. Met gebruikersaccounts hebben uw gebruikers toegang tot Adobe-producten en -services, aangezien gebruikersprofielgegevens zijn gecentraliseerd in het Adobe Identity Management System (IMS) en deze gegevens worden gedeeld door alle cloudservices. Zodra de gebruikersaccounts toegang tot AEM hebben gekregen, kan er in AEM as a Cloud Service naar worden verwezen (zoals vroeger), bijvoorbeeld voor het definiëren van rollen en toestemmingen vanuit de gebruikersinterfaces van AEM Security.

Dit biedt een combinatie van de volgende voordelen:

* U kunt Adobe Identity Management System (IMS) gebruiken om u één keer aan te melden voor alle Adobe-cloudapplicaties.

* Gebruikersvoorkeuren blijven lokaal voor elke specifieke instantie van AEM as a Cloud Service.

## Gebruikersinterface voor authoring {#authoring-user-interface}

>[!NOTE]
>
>Voor meer details, is de [Basisbehandeling](/help/sites-cloud/authoring/getting-started/basic-handling.md) een goed uitgangspunt.

De basisbeginselen van de authoringgebruikersinterface (UI), zowel voor Sites als Assets, zullen heel vertrouwd zijn voor iedereen die AEM vroeger heeft gebruikt.

Het belangrijkste verschil is dat de gebruikersinterface alleen met aanraking werkt. De klassieke interface is niet meer beschikbaar. Verder zijn de basisbeginselen ongewijzigd, met alleen kleine zichtbare wijzigingen.

## AEM Sites {#aem-sites}

Met Adobe Experience Manager Sites as a Cloud Service kunt u uw klanten persoonlijke, contentgestuurde ervaringen bieden door de kracht van het AEM Content Management System te combineren met AEM Digital Asset Management.

Zie het overzicht van [Wijzigingen in Sites](/help/sites-cloud/sites-cloud-changes.md) voor meer informatie.

## AEM Assets {#aem-assets}

Adobe Experience Manager Assets as a Cloud Service biedt een in cloud-native SaaS-oplossing voor bedrijven, niet alleen om hun Digital Asset Management- en Dynamic Media-bewerkingen snel en doeltreffend uit te voeren, maar ook om intelligente mogelijkheden van de volgende generatie te gebruiken zoals AI/ML, vanuit een systeem dat altijd actueel en beschikbaar is en altijd bezig is met leren.

Het Assets-aanbod omvat assetverwerking van de volgende generatie in de cloud, en hoogkwalitatieve opname en zoekfunctie van assets.

Zie [overzicht en inleiding tot Assets as a Cloud Service](/help/assets/overview.md) voor meer informatie.
