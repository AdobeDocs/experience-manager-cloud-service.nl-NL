---
title: Inleiding tot de architectuur van Adobe Experience Manager as a Cloud Service
description: Inleiding tot de architectuur van Adobe Experience Manager as a Cloud Service.
exl-id: 3fe856b7-a0fc-48fd-9c03-d64c31a51c5d
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '2658'
ht-degree: 8%

---

# Inleiding tot de architectuur van Adobe Experience Manager as a Cloud Service {#an-introduction-to-the-architecture-adobe-experience-manager-as-a-cloud-service}

>[!CONTEXTUALHELP]
>id="intro_aem_cloudservice_architecture"
>title="Inleiding tot AEM as a Cloud Service architectuur"
>abstract="Op dit tabblad kunt u de nieuwe architectuur van AEM as a Cloud Service bekijken en de wijzigingen begrijpen. AEM heeft geresulteerd in een dynamische architectuur met een variabel aantal afbeeldingen, dus het is belangrijk de tijd te nemen om de cloudarchitectuur te begrijpen."
>additional-url="https://video.tv.adobe.com/v/330542/" text="Overzicht van architectuur"

Adobe Experience Manager (AEM) as a Cloud Service biedt een reeks composable services voor het creëren en beheren van ervaringen met een hoog effect.

Deze pagina verstrekt een inleiding aan de logische architectuur, de de dienstarchitectuur, de systeemarchitectuur, en de ontwikkelingsarchitectuur voor AEM as a Cloud Service.

## Logische architectuur {#logical-architecture}

AEM as a Cloud Service bestaat uit oplossingen op hoog niveau zoals AEM Sites, AEM Assets en AEM Forms. Deze diensten zijn vergunning individueel, maar kunnen in samenwerking worden gebruikt. Elke oplossing gebruikt een combinatie van composable diensten die door AEM as a Cloud Service worden verleend, afhankelijk van hun respectieve gebruiksgevallen.

### Programma&#39;s {#programs}

AEM aanvragen worden in de vorm van een [Programma](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) die u maakt in de toepassing Cloud Manager, op basis van uw licentierechten. Deze programma&#39;s geven u volledige controle over hoe de bijbehorende AEM toepassing wordt genoemd, gevormd en hoe de toestemmingen, in de context van een bepaald project worden toegewezen.

Als klant wordt u gewoonlijk door Adobe geïdentificeerd als a **huurder**, ook bekend als *IMS-organisatie* (Identity Management-systeem). Een huurder kan zo vele programma&#39;s hebben zoals nodig, en vergunning hebben. Het is bijvoorbeeld gebruikelijk om een centraal programma voor AEM Assets te zien, terwijl AEM Sites kan worden gebruikt in meerdere programma&#39;s die aansluiten op meerdere online ervaringen.

>[!NOTE]
>
>AEM Edge Delivery Services worden als een oplossing op hoofdniveau weergegeven in Cloud Manager en maken vanuit een licentiestandpunt deel uit van de andere hoofdoplossingen. Bijvoorbeeld AEM Sites met Edge Delivery Services.

Een programma kan met om het even welke combinatie oplossingen op hoog niveau worden gevormd, en elke oplossing kan van één aan vele toe:voegen-ons steunen. Bijvoorbeeld Handel of Schermen voor AEM Sites, Dynamic Media of Brand Portal voor AEM Assets.

![AEM as a Cloud Service - Programma&#39;s](assets/architecture-aem-edge-programs.png "AEM as a Cloud Service - implementatiearchitectuur")

### Omgevingen {#environments}

Zodra een programma met de oplossingen van AEM Sites, AEM Assets of AEM Forms wordt gecreeerd, zullen de bijbehorende AEM instanties in de vorm van AEM milieu&#39;s in dit programma worden vertegenwoordigd.

Er zijn vier typen [milieu](/help/implementing/cloud-manager/manage-environments.md) beschikbaar bij AEM as a Cloud Service:

* Productieomgeving:

   * Een productiemilieu bewaart de toepassingen voor de bedrijfsartsen en stelt de levende ervaringen in werking.

* Werkgebiedomgeving:

   * Een werkgebiedomgeving wordt meestal gekoppeld aan een productieomgeving in een 1:1-relatie.
   * De werkgebiedomgeving is vooral ontworpen voor automatische tests voordat wijzigingen in de toepassing worden doorgevoerd in de productieomgeving.
      * Dit is onafhankelijk van de veranderingen die of door Adobe als deel van een onderhoudsupdate, of door uw codeplaatsingen in werking worden gesteld.
      * U kunt handtests ook uitvoeren in het geval van een code-implementatie.
   * De inhoud van de werkgebiedomgeving wordt meestal gesynchroniseerd gehouden met de productie-inhoud met de functie voor het kopiëren van zelfbedieningsinhoud.
* Ontwikkelomgeving:
   * Met een ontwikkelomgeving kunnen uw ontwikkelaars AEM toepassingen implementeren en testen onder dezelfde runtimevoorwaarden als in de fase- en productieomgeving.
   * De veranderingen gaan door een plaatsingspijpleiding toe die voor de zelfde codekwaliteit en veiligheidspoorten zoals in de pijpleidingen van de productieleiding toestaat.
* Snelle ontwikkelomgeving (RDE):
   * Een milieu RDE staat voor snelle ontwikkelingsherhalingen toe wanneer het opstellen van nieuwe of bestaande code in de instanties RDE, zonder het gaan door een formele plaatsingspijpleiding zoals die op regelmatige ontwikkelomgevingen wordt gevonden.

### Edge Delivery Services {#logical-architecture-edge-delivery-services}

Een AEM programma kan met worden gevormd [Edge Delivery Services](/help/edge/overview.md) ook.

Zodra gevormd, kan AEM GitHub codeopslagplaatsen van verwijzingen voorzien die voor de bouw van de ervaringen met Edge Delivery Services worden gebruikt. Dientengevolge, worden de nieuwe configuratieopties beschikbaar voor de bijbehorende ervaringen. Deze omvatten vestiging Adobe-Beheerde CDN, en de toegang tot van vergunningsmetriek of SLA- rapporten.

## Servicearchitectuur {#service-architecture}

De lijst van de diensten op hoog niveau composable in AEM as a Cloud Service kan met twee segmenten - Inhoudsbeheer en Ervaring Levering worden vertegenwoordigd:

![as a Cloud Service overzicht AEM - met Edge Delivery Services](assets/architecture-aem-edge.png "as a Cloud Service overzicht AEM - met Edge Delivery Services")

Voor inhoudsbeheer zijn er twee hoofdsets services voor het ontwerpen van inhoud, die beide worden vertegenwoordigd als *inhoudsbronnen*:

* De laag AEM auteur: biedt een webinterface (met gekoppelde API&#39;s) voor het beheer van webinhoud. Dit geldt voor beide benaderingen:
   * Hoofdtekst - via de pagina-editor en de Universal Editor
   * Koploos - via de editor voor inhoudsfragmenten
* De op documenten gebaseerde ontwerplaag: hiermee kunt u inhoud schrijven met behulp van standaardtoepassingen, zoals:
   * Microsoft Word en Excel - via SharePoint
   * Google Docs and Sheets - via Google Drive

Voor ervaringslevering, wanneer het gebruiken van AEM Sites of AEM Forms, zijn er ook twee belangrijkste reeksen diensten, niet wederzijds - exclusief en werkend onder een gedeelde Adobe-Beheerde CDN (het Netwerk van de Levering van de Inhoud) als verschillende oorsprong:

* De AEM publicatielaag:
   * Voert een landbouwbedrijf van standaard AEM uitgevers en verzenders in werking, die voor het dynamische teruggeven van Web-pagina&#39;s en API inhoud (bijvoorbeeld, GraphQL) toestaan die met gepubliceerde inhoud wordt samengesteld.
   * Is hoofdzakelijk gebaseerd op server-zijtoepassingslogica.
* Het Edge Delivery-publicatieniveau:
   * Hiermee wordt het dynamisch weergeven van webpagina&#39;s en API-inhoud vanuit diverse inhoudsbronnen toegestaan, zoals de AEM Auteur-laag of de op document gebaseerde ontwerplaag.
   * Is gebaseerd op toepassingslogica aan de clientzijde en ontworpen voor maximale prestaties.

Er zijn ook de belangrijkste aangrenzende services:

* The Edge Delivery Assets tier:
   * Staat de levering toe van goedgekeurde en gepubliceerde media-items van AEM Assets. Bijvoorbeeld afbeeldingen en video&#39;s.
   * Meestal wordt naar de media-items verwezen op basis van ervaringen die worden uitgevoerd op de AEM publicatielaag, de Edge Delivery-publicatielaag of een andere Adobe Experience Cloud-toepassing die is geïntegreerd met AEM Assets.
* De AEM voorvertoningslaag en de voorvertoningslaag voor Edge Delivery Services:
   * Deze services zijn ook beschikbaar voor ervaringen die zijn ontwikkeld met de publicatielaag AEM Publiceren of de publicatielaag voor Edge Delivery.
   * Hiermee kunnen auteurs van inhoud inhoud in context een voorvertoning van inhoud weergeven voordat ze bewerkingen publiceren.

>[!NOTE]
>
>Standaard hebben alleen-middelenprogramma&#39;s geen publicatielaag of voorvertoningslaag.

Er zijn andere aangrenzende services:

* De replicatieservice:
   * Geplaatst tussen de laag voor inhoudsbeheer en de leveringslaag voor ervaring.
   * is verantwoordelijk voor de verwerking van de *publish* bewerkingen die zijn uitgegeven door auteurs van inhoud en die de gepubliceerde inhoud vervolgens leveren aan de publicatieniveaus (AEM of Edge Delivery).

  >[!NOTE]
  >De replicatieservice heeft een volledig nieuw ontwerp doorgemaakt in vergelijking met de 6.x-versies van AEM, aangezien het replicatieframework van vorige versies van AEM niet meer wordt gebruikt om inhoud te publiceren.
  >
  >De nieuwste architectuur is gebaseerd op een *publiceren en abonneren* aanpak met rijen van inhoud in de cloud. Voor de AEM publicatielijst kan een variabel aantal uitgevers zich abonneren op de publicatie-inhoud en is dit een essentieel onderdeel van het realiseren van echte en snelle automatische schaling voor AEM as a Cloud Service

* De service voor opslagplaatsen voor inhoud:
   * Wordt gebruikt door de AEM auteurslaag.
   * Is een cloudgebaseerde instantie van een JCR-compatibele opslagplaats voor inhoud, geïmplementeerd door de Apache Oak-technologie.
   * De persistentie van inhoud is voornamelijk gebaseerd op cloudopslag op basis van blob.
* De CI/CD-service:
   * Vertegenwoordigt de subset van functies van Cloud Manager die zijn gewijd aan het beheren van distributiepijpleidingen naar de AEM omgevingen.
* De testservice:
   * Vertegenwoordigt de onderliggende infrastructuur die wordt gebruikt om uit te voeren:
      * functionele tests;
      * UI-tests: bijvoorbeeld op basis van Selenium- of Cypress-scripts;
      * praktijkexamens: bijvoorbeeld Lighthouse-scores;

     als deel van een plaatsingspijpleiding aan een AEM milieu, of als deel van een vraag van GitHub aan een de codebewaarplaats van de Levering van de Rand.
* De gegevensservice:
   * Is verantwoordelijk voor het blootstellen van klantgegevens zoals licentiemetriek (bijvoorbeeld inhoudsverzoeken, opslag, gebruikers) of gebruiksrapporten (zoals het aantal uploads, downloads).
   * De klantgegevens kunnen worden weergegeven via API&#39;s en binnen gebruikersinterfaces van het product (zoals Cloud Manager).
* De Real-User Metric (RUM) dienst:
   * Is verantwoordelijk voor het verzamelen van zeer belangrijke metriek van een klantenervaring (zoals paginameningen, kernWeb vitals, omzettingsgebeurtenissen), en het antwoorden aan bijbehorende vragen (bijvoorbeeld, hoogste paginameningen voor een bepaald domein in de laatste 7 dagen).
* The Assets Compute service:
   * is verantwoordelijk voor het verwerken van geüploade afbeeldingen, video&#39;s en documenten, bijvoorbeeld PDF- en Adobe Photoshop-bestanden. Bij verwerking kunt u Adobe Sensei gebruiken om metagegevens van afbeeldingen en video te extraheren (zoals beschrijvende tags of primaire kleurtonen) en vervolgens uitvoeringen genereren (zoals verschillende formaten of formaten), met toegang tot API&#39;s zoals de Adobe Photoshop- en Adobe Lightroom-API&#39;s.
* De Identity Management Service (IMS):
   * Is de centrale plaats verantwoordelijk voor het beheren en verifiëren van gebruikers en gebruikersgroepen voor een bepaalde Adobe Experience Cloud-toepassing (bijvoorbeeld Cloud Manager of de AEM auteurslaag).
   * Wordt benaderd via de Adobe Admin Console.

## Systeemarchitectuur {#system-architecture}

### AEM tips voor auteur, voorvertoning en publicatie {#aem-author-preview-publish-tiers}

De AEM Auteur en Publish lijsten worden uitgevoerd als reeks containers van Docker, die door een standaardDienst van de Orchestratie van de Container worden beheerd. De resulterende containerarchitectuur betekent een volledig dynamisch systeem met een variabel aantal pods, afhankelijk van werkelijke activiteit (voor inhoudsbeheer) en het werkelijke verkeer (voor ervaringslevering). Dit laat AEM as a Cloud Service toe om uw verkeerspatronen aan te passen aangezien zij veranderen.

De AEM Auteur-laag wordt gebruikt als een cluster van AEM auteurspods die één opslagplaats voor inhoud delen. Een minimum van twee pods staat voor bedrijfscontinuïteit toe terwijl de onderhoudstaken lopen, of terwijl een plaatsingsproces gebeurt.

De AEM publicatielaag wordt gebruikt als een farm van AEM publicatieinstanties, elk met hun eigen inhoudsopslagruimte van gepubliceerde inhoud. Elke uitgever wordt gekoppeld aan één enkele instantie Apache die met de AEM verzendermodule voor een materialized mening van de inhoud wordt uitgerust, die als oorsprong voor Adobe-beheerde CDN dienst doet. Een minimum van twee pods staat ook voor bedrijfscontinuïteit toe, maar het is niet ongebruikelijk om dit aantal in periodes van hoog verkeer te zien groeien.

De AEM voorvertoningslaag bestaat uit één AEM. Dit wordt gebruikt voor kwaliteitsborging van inhoud alvorens aan te publiceren publiceert rij. Soms kunnen er downtime optreden, vooral tijdens implementaties, op de voorvertoningslaag.

### Edge Delivery Services {#system-architecture-edge-delivery-services}

De Edge Delivery Services worden boven op een CDN en serverloze infrastructuur gebruikt om de pagina&#39;s op de meest presterende manier samen te stellen. Wanneer een middel wordt gevraagd, is de serverinfrastructuur verantwoordelijk voor het omzetten van de gepubliceerde inhoud in semantische HTML en dient als oorsprong aan CDN.

De conversie naar semantische HTML vindt plaats op basis van de gepubliceerde inhoud die wordt aangeboden in de AEM auteurslaag of de op documenten gebaseerde ontwerpomgeving.

In het volgende diagram ziet u hoe u Sites-inhoud in Microsoft Word (op documenten gebaseerd ontwerp) kunt bewerken en naar Edge Delivery kunt publiceren. Ook wordt met de verschillende editors de traditionele AEM-publicatiemethode weergegeven.

![AEM Sites as a Cloud Service - met Edge Delivery Services](assets/architecture-aem-edge-author-publish.png "AEM Sites as a Cloud Service - met Edge Delivery Services")

Aangezien Edge Delivery Services deel uitmaken van Adobe Experience Manager en als zodanig kunnen Edge Delivery, AEM Sites en AEM Assets op hetzelfde domein naast elkaar bestaan. Dit is een veelvoorkomend geval voor het gebruik van grotere websites. Bijvoorbeeld, zou een klant een bepaalde pagina met hoog verkeer aan Edge Delivery Services kunnen willen migreren, terwijl alle andere pagina&#39;s op de AEM Publish Rij zouden kunnen blijven.

## Ontwikkelarchitectuur {#development-architecture}

### Codeopslagplaatsen {#code-repositories}

De code en de configuratie voor AEM projecten wordt opgeslagen in een codebewaarplaats, waarvan plaatsingspijpleidingen worden uitgegeven wanneer de veranderingen worden aangebracht. Er zijn verschillende typen gegevensopslagruimten voor code:

* AEM volledige stapel:
   * Voor het opslaan van Java-code en OSGI-configuraties aan de serverzijde voor de AEM auteur en publicatielagen.
* AEM voorzijde:
   * Voor het opslaan van client-side JS-, CSS- en HTML-code voor de AEM auteur- en publicatielagen.
Zie voor meer informatie over clientlibs [Client-Side Libraries gebruiken op AEM as a Cloud Service.](/help/implementing/developing/introduction/clientlibs.md)
* AEM weblaag:
   * Hiermee slaat u de configuratiebestanden van de verzender op voor de AEM publicatielijst.
* AEM configuratie:
   * Staat voor het opslaan van diverse configuratieopties (zoals montages CDN, of de montages van onderhoudstaken) voor AEM toe publiceren rij en de Edge Delivery Services publiceren rij.
* AEM randlevering:
   * Voor het opslaan van de client-side JS-, CSS- en HTML-code voor sites die zijn gemaakt met de Edge Delivery Services

### Plaatsingspijpleidingen {#deployment-pipelines}

Ontwikkelaars en beheerders beheren de AEM as a Cloud Service toepassing met behulp van de Continuous Integration/Continuous Delivery (CI/CD)-service, die beschikbaar wordt gesteld via de Cloud Manager. Cloud Manager stelt ook alles bloot wat te maken heeft met bewaking, onderhoud, probleemoplossing (bijvoorbeeld toegang tot logbestanden) en licenties.

![AEM as a Cloud Service - Implementatiearchitectuur](assets/architecture-aem-edge-deployment-pipelines.png "AEM as a Cloud Service - Implementatiearchitectuur")

Cloud Manager beheert alle updates van de as a Cloud Service AEM. Het is verplicht, omdat dit de enige manier is om de klanttoepassing te maken, testen en implementeren voor de auteur, de voorvertoning en de publicatielagen. Deze updates kunnen worden geactiveerd door Adobe, wanneer een nieuwe versie van de AEM Cloud Service gereed is of door uzelf wanneer een nieuwe versie van de toepassing gereed is.

Dit wordt uitgevoerd door een plaatsingspijpleiding, die aan elk milieu binnen een programma wordt gekoppeld. Wanneer een Cloud Manager-pijplijn wordt uitgevoerd, maakt deze een nieuwe versie van de klantapplicatie, zowel voor de authoring- als voor de publicatielaag. Dit wordt bereikt door de nieuwste klantpakketten te combineren met de nieuwste Adobe image voor de basislijn.

De plaatsingspijpleiding wordt teweeggebracht of wanneer de klanten codeveranderingen aanbrengen, of wanneer de Adobe een nieuwe onderhoudsversie opstelt.

In beide gevallen wordt dezelfde set geautomatiseerde tests uitgevoerd. Het bestaat uit tests:

* door de Adobe wordt bijgedragen om de productintegriteit te waarborgen
* door de klant geleverde tests
   * Functionele tests: via http-verzoeken aan de AEM auteur of publicatielaag
   * UI-tests: gebaseerd op Selenium- of Cypress-technologie

Deze geautomatiseerde tests worden uitgevoerd in de Stage-omgeving. Daarom is het belangrijk dat de Stage-omgeving zo dicht mogelijk bij de inhoud van de Production-instantie blijft.

Zodra alle tests met succes overgaan, wordt de nieuwe code opgesteld aan het milieu van de Productie.

### Rolling updates {#rolling-updates}

De Cloud Manager automatiseert volledig de cut-over aan de recentste versie van de AEM toepassing door alle de dienstknopen bij te werken gebruikend een het rollen updatepatroon. Dit betekent dat er **geen downtime** voor de auteur of de publicatieservice.

## Belangrijke innovaties sinds AEM 6.x {#major-innovations-since-aem-6x}

De meest recente architectuur voor AEM as a Cloud Service introduceert enkele fundamentele veranderingen en innovaties in vergelijking met de vorige generaties (AEM 6.x en vorige):

* Alle bestanden worden rechtstreeks geüpload en via een Cloud Data Store verzonden. De bijbehorende bitstroom gaat nooit door de JVM van de AEM Author- en Publish-services. Hierdoor kunnen de knooppunten van de AEM auteur- en publicatieservices kleiner van grootte zijn en zijn deze dus beter compatibel met de verwachting van snelle automatische schaling. Voor zakelijke gebruikers leidt dit tot een snellere ervaring bij het uploaden en downloaden van afbeeldingen, video en andere taken.

* Alle bewerkingen die bestaan uit het publiceren van content, bevatten nu een pijplijn die een abonnementspatroon volgt. Gepubliceerde content wordt verplaatst naar diverse wachtrijen in de pijplijn, waarop alle nodes van de publicatieservice zijn geabonneerd. Daarom hoeft de authoringlaag niets te weten over het aantal nodes in de publicatieservice; hierdoor kan de publicatielaag snel automatisch worden geschaald.

* De architectuur scheidt de applicatiecontent volledig van de applicatiecode en de configuratie. Alle code en configuraties zijn praktisch onveranderlijk en ingebouwd in de basisinstallatiekopie die wordt gebruikt om de diverse nodes van de authoring- en publicatieservices te maken. Daardoor is absoluut gegarandeerd dat alle nodes identiek zijn, en kunnen veranderingen in de code en configuratie uitsluitend globaal worden aangebracht door een Cloud Manager-pijplijn uit te voeren.

* De architectuur omvat veelvoudige microdiensten die op serverloze technologie, vooral met Adobe I/O runtime worden gebouwd

## Aanvullende informatie {#further-information}

Zie ook:

* Edge Delivery Services:

   * [as a Cloud Service overzicht AEM - met Edge Delivery Services](/help/edge/overview.md)
   * [Edge Delivery Services gebruiken](/help/edge/using.md)
   * [Ontdek de onderliggende architectuur en belangrijke AEM die as a Cloud Service zijn met Edge Delivery Services](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/introduction/architecture.html)
