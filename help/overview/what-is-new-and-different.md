---
title: Wat is anders en wat is nieuw - Adobe Experience Manager als cloudservice
description: 'Wat is anders en wat is nieuw - Adobe Experience Manager (AEM) als cloudservice. '
translation-type: tm+mt
source-git-commit: eb28fedae5b87a67460f4cac97959f65972e652a

---


# Wat is nieuw en wat is anders {#what-is-new-and-what-is-different}

AEM is al vele jaren beschikbaar:

* Op locatie

* als een beheerde service

Er zijn intrinsieke verschillen tussen deze eerdere benaderingen en AEM als Cloud Service:

* [Architectuur](#architecture)
* [Upgrades](#upgrades)
* [Cloud Manager](#cloud-manager)
* [Onboarding](#onboarding)
* [Ontwikkelen](#developing)
* [Exploitatie en prestaties](#operations-and-performance)
* [Identiteitsbeheer](#identity-management)
* [Gebruikersinterface voor ontwerpen](#authoring-user-interface)
* [AEM-sites](#aem-sites)
* [AEM-middelen](#aem-assets)

>[!NOTE]
>
>Deze overzichten zijn niet uitputtend, maar zijn bedoeld om een inleiding te geven.

<!-- change link when 6.5 hub page migrated -->

>[!NOTE]
>
>Raadpleeg de documentatieset voor [AEM 6.5](https://helpx.adobe.com/support/experience-manager/6-5.html)voor meer informatie over de serviceversies Op locatie en Beheerd.

<!-- * [Miscellaneous](#miscellaneous) -->

## Architectuur {#architecture}

>[!NOTE]
>
>Zie [Architectuur](/help/core-concepts/architecture.md)voor meer informatie.

### Vorige versies {#previous-versions-architecture}

Zowel AEM op-gebouw, als AEM onder Beheerde Diensten gebruikte een statische architectuur die uit een vast aantal machines en instanties bestond.

![Statische](assets/introduction-01.png "architectuurStatic")

Deze:

* De grootte van de onderneming was afgestemd op het *piekverkeer* (internet) en de *piekactiviteit* (marketing), wat ertoe leidde dat zij gedurende aanzienlijke perioden niet-actief waren:
   ![De statische structuur moet rekening houden met variërende gebruikspatronenDe statische structuur moet rekening houden met variërende gebruikspatronen](assets/introduction-02.png "")

* waren monoolithische toepassingen (de snelstart).

* had één instantie van de auteur; die tijdens onderhoudsbeurten onderbreking ondervond.

### AEM als cloudservice {#aem-as-a-cloud-service-architecture}

AEM als Cloud Service heeft nu:

* Een dynamische architectuur met een variabel aantal AEM-afbeeldingen.

![Dynamische](assets/introduction-03.png "architectuurDynamische architectuur")

Deze architectuur:

* Wordt geschaald op basis van het *werkelijke* verkeer en de *werkelijke* activiteit.

* Bevat afzonderlijke instanties die alleen worden uitgevoerd wanneer dat nodig is.

* Gebruikt modulaire toepassingen.

* Heeft een auteurcluster als gebrek; dit voorkomt downtime voor onderhoudstaken.

Hierdoor wordt automatische schaling ingeschakeld voor verschillende gebruikspatronen:

![Automatisch schalen voor verschillende gebruikspatronenAutomatisch](assets/introduction-04.png "schalen voor verschillende gebruikspatronen")


## Upgrades {#upgrades}

<!--
>[!NOTE]
>
>For further details see the [Deploying Introduction](/help/sites/deploying/introduction.md).
-->

### Vorige versies {#previous-versions-upgrades}

Zowel AEM op-gebouw, als AEM onder Beheerde Diensten waren onderworpen aan een vast patroon van een jaarlijkse belangrijke uitgave die door de dienstpakken, eigenschapspakken en heet-moeilijke situaties werd uitgebreid. Vaak zou een grote versie twee of meer jaar duren.

Afhankelijk van het upgradetype kan het proces aanzienlijke voorbereiding vereisen, bestaande uit analyse, ontwikkeling en testen, gevolgd door een venster van downtime voor de daadwerkelijke upgrade.

### AEM als cloudservice {#aem-as-a-cloud-service-upgrades}

AEM als Cloud Service gebruikt nu Continuous Integration en Continuous Delivery (CI/CD) om ervoor te zorgen dat uw projecten volledig up-to-date zijn. Dit betekent dat alle verbeteringsverrichtingen volledig geautomatiseerd zijn, zodat vereist geen onderbreking van de dienst voor gebruikers.

Adobe werkt proactief alle operationele instanties van de service bij naar de nieuwste versie van de AEM-codebasis:

* Bugfixes:

   * Kan dagelijks worden vrijgegeven.

   * De instanties worden vaak bijgewerkt met de recentste insectenmoeilijke situaties. Aangezien de veranderingen regelmatig worden toegepast, is het effect stijgend, verminderend het effect op uw dienst.

   * De meeste updates zijn om onderhouds- en beveiligingsredenen.

* Nieuwe functies:

   * Wordt vrijgegeven via een voorspelbaar maandschema.

>[!NOTE]
>
>Dit wordt bereikt met [Cloud Manager](#cloud-manager).

## Cloud Manager {#cloud-manager}

>[!NOTE]
>
>Zie [Implementatiearchitectuur](/help/core-concepts/architecture.md#deployment-architecture)voor meer informatie.

### Vorige versies {#previous-versions-cloud-manager}

Cloud Manager werd gebruikt als plaatsingshulpmiddel voor Beheerde instanties van de Diensten van AEM.

De belangrijkste verschillen tussen Cloud Manager voor AMS en voor de Diensten van de Wolk, zijn wanneer een huurder wordt gecreeerd, zal het met kredieten worden bevolkt die op SKUs worden gebaseerd die door de klant zijn gekocht.

>[!NOTE]
>Hoewel dit vanuit operationeel oogpunt van essentieel belang is, wordt het concept van *credits* niet rechtstreeks weergegeven in de gebruikersinterface van Cloud Manager.

Het maken van een normaal programma verbruikt geen kredieten, maar er moet wel een kernkrediet bestaan om een dergelijk programma te kunnen maken.
Raadpleeg [Een programma](/help/onboarding/getting-access-to-aem-in-cloud/creating-a-program.md)maken voor meer informatie over het maken van verschillende programma&#39;s.

### AEM als cloudservice {#aem-as-a-cloud-service-cloud-manager}

Adobe Cloud Manager is een integraal onderdeel van de continue upgradeaanpak van AEM als cloudservice, aangezien deze alle updates voor uw instanties regelt - dit is verplicht.

Adobe kan updates activeren wanneer er een nieuwe versie van de cloudservice beschikbaar is. U kunt de toepassingsupdates ook activeren via de pijpleidingen die worden geleverd door Cloud Manager.

Cloud Manager is:

* worden gebruikt voor het beheer van AEM-programma&#39;s en -omgevingen;

* een essentieel onderdeel van AEM als cloudservice; elke nieuwe huurder eerst wordt voorzien voor de toegang van de Manager van de Wolk,

* het enige ingangspunt voor uw verrichtingen en ontwikkelingspersoneel.

Meer bepaald worden het aantal en het type AEM-programma&#39;s dat met Cloud Manager kan worden gemaakt, afgeleid van:

* van de licentieovereenkomst voor klanten, in de vorm van een pool van kredieten;

* van interne actoren wanneer AEM als cloudservice wordt gebruikt voor activering of training,

* van externe processen, zoals tests die zijn gestart op Adobe.com.

Cloud Manager is geëvolueerd als een zelfbedieningsportal waar de belangrijkste componenten van AEM als Cloud Service kunnen worden gemaakt en geconfigureerd:

* Nieuwe programma&#39;s maken en beheren.

* De AEM-omgevingen binnen deze programma&#39;s maken en beheren.

* Het creëren van en het leiden van de pijpleidingen voor het opstellen van de klantencode en de verwante configuratie aan een specifiek milieu.

* Er wordt een melding ontvangen van belangrijke levenscyclusgebeurtenissen voor deze componenten (bijvoorbeeld productupdates).

Cloud Manager kan momenteel omgevingen maken in drie geografische regio&#39;s (met meer regio&#39;s):

* VS (Oost)

* EMEA (Nederland)

* APAC (Australië)

## Onboarding {#onboarding}

<!--
>[!NOTE]
>
>For further details see [Onboarding - An Overview](/help/onboarding/overview.md).
-->

### Vorige versies {#previous-versions-onboarding}

Bij de uitvoering van een AEM-project werden in principe de traditionele methoden voor projectbeheer gevolgd.

### AEM als cloudservice {#aem-as-a-cloud-service-onboarding}

Het starten en beheren van een AEM-project is aanzienlijk eenvoudiger wanneer u AEM gebruikt als cloudservice omdat Adobe verantwoordelijk is voor vele aspecten:

* AEM-basislijnafbeeldingen zijn geoptimaliseerd voor specifieke gebruiksgevallen.

* Veel van de handmatige configuratietaken zijn overbodig geworden.

Het is ook aanzienlijk anders, aangezien er nu sprake is van:

* een beoordelingsfase om te waarborgen dat aan alle voorwaarden is voldaan; met inbegrip van bijvoorbeeld:

   * Wettelijke vereisten

   * Contractuele overeenkomsten

   * Technische vereisten voor bestaande inhoud en/of code die door de klant zijn aangepast

* Implementatievereisten:

   * Code-updates; alle klanttoepassingen die voor een vorige versie van AEM zijn ontwikkeld, moeten worden beoordeeld en eventueel worden bijgewerkt.

   * Inhoud migreren

## Ontwikkelen {#developing}

>[!NOTE]
>
>Voor meer informatie, begin met de documentatie van de [Ontwikkelingsrichtsnoeren](/help/implementing/developing/introduction/development-guidelines.md) .

<!--
>[!NOTE]
>
>For further details start with [The Developing Experience](/help/sites/developing/introduction/developer-experience.md, [Developing - The Basics](/help/sites/developing/introduction/the-basics.md) and [Developing Best Practices](/help/sites/best-practices/developing.md).
-->

### Vorige versies {#previous-versions-developing}

<!-- needs more detail -->
Ontwikkeling was een intensieve taak die lokaal werd uitgevoerd, gevolgd door implementatie op de productie-instantie.

### AEM als cloudservice {#aem-as-a-cloud-service-developing}

<!-- Will need information for new customers -->
De nieuwe architectuur die AEM als Cloud Service ondersteunt, brengt enkele belangrijke wijzigingen aan in de algemene ontwikkelaarservaring. Een van de belangrijkste doelstellingen voor AEM als Cloud Service is om ervaren klanten (die AEM op locatie of in de context van de Adobe Managed Services hebben gebruikt) toe te staan zo snel mogelijk naar AEM te migreren als een Cloud Service, zonder het grootste deel van hun aangepaste code te hoeven herschrijven. Het is echter mogelijk dat er nog enkele aanpassingen nodig zijn.

#### Cloud Development {#aem-as-a-cloud-service-developing-cloud-development}

Voor bestaande AEM-toepassingen die als cloudservice op AEM worden uitgevoerd, worden de volgende stappen verwacht:

* De toepassingscode en configuratie moeten worden opgeslagen in de Git-codeopslagplaats van het bijbehorende Cloud Manager-programma.
* De toepassingscode en configuratie moeten compatibel zijn met de nieuwste versie van de AEM-basislijnafbeelding (die dagelijks kan worden gewijzigd).
   * De klanttoepassing moet worden gebouwd en geïmplementeerd met behulp van de Cloud Manager-pijplijn die is gekoppeld aan de Cloud Manager-omgeving.
* De klantentoepassing moet al die codekwaliteit, veiligheid en prestatiegates overgaan in de pijpleiding wordt afgedwongen.
* De afbeeldingen die voor de klanttoepassing zijn gemaakt, moeten door de Cloud Manager-pijplijn worden geïmplementeerd.

<!-- duration of what? -->
Dit proces wordt doorgaans aangeduid als &#39;Cloud-first&#39;-ontwikkeling. Aangezien de end-to-end duur naar verwachting minuten in beslag zal nemen (van 20 tot 50, afhankelijk van de complexiteit van de toepassing), is het noodzakelijk om snelle ontwikkelingsmethodologieën te omarmen voordat de code en configuratiewijzigingen in behandeling in de cloud worden geprobeerd.

<!-- is this really relevant at this point? -->
De webconsole, waar OSGI-bundels en de bijbehorende configuratie worden beheerd en die voorheen deel uitmaakte van de AEM QuickStart, is niet langer rechtstreeks toegankelijk voor gebruikers van een AEM als een Cloud Service-omgeving. Deze interface kan nog op read-only wijze worden betreden door een nieuwe ontwikkelaarsconsole te gebruiken. Met deze console, kunnen de ontwikkelaars en login rechtstreeks aan om het even welke bepaalde knoop van een auteur selecteren of de publicatieservice, dan tot de gebieden toegang hebben die door gebrek worden geblokkeerd.

Een andere veelvoorkomende vereiste voor ontwikkelaars is snelle toegang tot de logbestanden van de verschillende omgevingen. Met AEM als Cloud Service worden de logbestanden van de verschillende knooppunten in de auteur en de publicatieknooppunten beschikbaar gesteld via Cloud Manager, in de vorm van bestanden die kunnen worden gedownload of via API&#39;s.

Vanwege de duidelijke scheiding van code en inhoud kunnen ontwikkelaars een bepaald proces gebruiken voor het bijwerken van inhoud als onderdeel van een implementatie. Doorgaans worden muteerbare inhoud gebruikt:

* Standaard *standaardinhoud* die deel uitmaakt van het klantproject (bijvoorbeeld mappen, sjablonen, workflows, enz.)

* Indexdefinities zoeken

* ACLs en toestemmingen

* Gebruikers en gebruikersgroepen van services

#### Lokale ontwikkeling {#aem-as-a-cloud-service-developing-local-development}

Om snelle herhalingen en ontwikkeling te ondersteunen, is het ook mogelijk om AEM-toepassingen buiten de AEM als cloudservicecontext te ontwikkelen. Hiertoe worden de volgende artefacten ter beschikking gesteld van de ontwikkelaars:

* De AEM als Cloud Service QuickStart: een `.jar` gebaseerd, zelfstandig installatieprogramma van de nieuwste AEM-codebasis, met hetzelfde functionele en API-oppervlak.

* De AEM als een Cloud Service Dispatcher SDK: een op afbeeldingen gebaseerd proces voor het lokaal testen en valideren van Dispatcher-configuraties

>[!NOTE]
>
>Houd er rekening mee dat de Cloud QuickStart niet alle functies van AEM-sites en AEM-middelen toestaat. Het bestaat uit een eenvoudige auteursomgeving waar de meerderheid van de uitbreidingen kan worden ontwikkeld en worden getest.

## Exploitatie en prestaties {#operations-and-performance}

>[!NOTE]
>
>Voor meer details begin met [Steun](/help/operations/backup.md), [Indexering](/help/operations/indexing.md), en [andere onderhoudstaken](/help/operations/maintenance.md).

### Vorige versies {#previous-versions-operations-and-performance}

In het verleden, en met name aan de zijde van de auteur, was het nodig een instantie periodiek te stoppen; voor routinematige onderhoudswerkzaamheden en upgrades en updates. Voor sommige klanten resulteerde dit wekelijks in uren van geplande onderbreking.

### AEM als cloudservice {#aem-as-a-cloud-service-operatioms-and-performance}

Met AEM als Cloud Service worden dergelijke bewerkingen geautomatiseerd zodat een onderbreking van de service niet langer nodig is.

Op deze gebieden:

* Veel taken zijn geautomatiseerd.

* De technologieën worden geoptimaliseerd voor maximale veerkracht en efficiency; binaryless replicatie is bijvoorbeeld het gebrek.

* Zware ladingstaken, zoals rijen, banen en bulkverwerkingstaken, zijn uit de kern-AEM-instantie verplaatst die door gedeelde en specifieke microdiensten moet worden afgehandeld.

Bewerkingen voor AEM als Cloud Service worden ook ondersteund door een nieuwe infrastructuur voor bewaking, rapportage en waarschuwingen. Hierdoor kunnen de Adobe SRE&#39;s (Site Reliability Engineers) de service proactief gezond houden. De verschillende elementen van de architectuur zijn uitgerust met een verscheidenheid aan gezondheidscontroles. Als om een of andere reden een bepaald knooppunt van de architectuur ongezond wordt geacht, wordt het uit de service verwijderd en stilzwijgend vervangen door een nieuw, gezond knooppunt.

## Identiteitsbeheer {#identity-management}

<!--
>[!NOTE]
>
>For further details see [Security - Single Sign-On](/help/sites/security/single-sign-on.md).
-->

### Vorige versies {#previous-versions-identity-management}

Standaard was identiteitsbeheer intern voor AEM.

>[!NOTE]
>
>AEM 6.4.3.0 introduceerde:
>
>* Ondersteuning voor beheerconsole voor AEM-instanties.
>* Op Adobe IMS (Identity Management System) gebaseerde verificatie voor klanten van door AEM beheerde services.


### AEM als cloudservice {#aem-as-a-cloud-service-identity-management}

Een belangrijke wijziging in AEM als cloudservice is het volledig geïntegreerde gebruik van Adobe-id&#39;s voor toegang tot de auteurslaag.

Hiervoor is het gebruik van de [Adobe Admin-console](https://helpx.adobe.com/enterprise/using/admin-console.html) vereist voor het beheer van gebruikers en gebruikersgroepen. Met gebruikersaccounts hebben uw gebruikers toegang tot Adobe-producten en -services, aangezien gebruikersprofielgegevens zijn gecentraliseerd in het Adobe Identity Management System (IMS) en deze gegevens worden gedeeld door alle cloudservices. Zodra toegang tot AEM is toegewezen, kunnen de gebruikersaccounts in AEM als Cloud Service (zoals voorheen) worden genoemd. bijvoorbeeld voor het definiëren van rollen en machtigingen vanuit de gebruikersinterfaces van AEM Security.

Dit combineert de voordelen van:

* Met het Adobe Identity Management System (IMS) kunt u zich aanmelden voor alle Adobe-cloudtoepassingen.

* Gebruikersvoorkeuren blijven lokaal voor elke specifieke instantie van AEM als cloudservice.

## Gebruikersinterface voor ontwerpen {#authoring-user-interface}

<!--
>[!NOTE]
>
>For further details, the [Basic Handling](/help/sites/authoring/getting-started/basic-handling.md) and [Best Practices](/help/sites/best-practices/authoring.md) are good starting points.
-->

### Vorige versies {#previous-versions-authoring}

De gebruikersinterface van de auteurinstantie (UI), voor zowel Plaatsen als Activa, werd progressief ontwikkeld en geoptimaliseerd om voor alle gebruik-gevallen te behandelen, gebruikend zowel aanraking-toegelaten als klassieke UIs.

### AEM als cloudservice {#aem-as-a-cloud-service-authoring}

De basisbeginselen van het auteursgebruikersinterface (UI), voor zowel Plaatsen als Activa, zullen zeer vertrouwd aan iedereen zijn die AEM in het verleden heeft gebruikt.

Het belangrijkste verschil is dat de gebruikersinterface alleen aanraakingeschakeld is. de klassieke interface niet meer beschikbaar is. Anders blijven de grondbeginselen ongewijzigd, waarbij slechts kleine wijzigingen zichtbaar zijn.

## AEM-sites {#aem-sites}

Met Adobe Experience Manager Sites as a Cloud Service kunt u uw klanten persoonlijke ervaringen met inhoud bieden door de kracht van het AEM Content Management System te combineren met AEM Digital Asset Management.

Zie het overzicht van [Wijzigingen in sites](/help/sites-cloud/sites-cloud-changes.md)voor meer informatie.

## AEM-middelen {#aem-assets}

Adobe Experience Manager Assets as a Cloud Service biedt een in de cloud geïntegreerde SaaS-oplossing voor bedrijven die niet alleen hun Digital Asset Management- en Dynamic Media-bewerkingen met snelheid en impact uitvoeren, maar ook intelligente mogelijkheden van de volgende generatie gebruiken, zoals AI/ML, vanuit een systeem dat altijd actueel, altijd beschikbaar en altijd leerbaar is.

Het aanbod van bedrijfsmiddelen omvat de verwerking van bedrijfsmiddelen van de volgende generatie in de cloud en het opnemen en zoeken van bedrijfsmiddelen van hoge kwaliteit.

Zie [overzicht en inleiding tot Elementen als Cloud Service](/help/assets/overview.md)voor meer informatie.

<!--

#### Previous Versions {#previous-versions-aem-sites}

tbc

#### AEM as a Cloud Service {#aem-as-a-cloud-service-aem-sites}

tbc

-->

<!--

#### Previous Versions* {#previous-versions-aem-assets}

tbc

#### AEM as a Cloud Service {#aem-as-a-cloud-service-aem-assets}

tbc 

-->

<!--

### Miscellaneous {#miscellaneous}

#### AEM as a Cloud Service {#aem-as-a-cloud-service-miscellaneous}

Additionally???

-->