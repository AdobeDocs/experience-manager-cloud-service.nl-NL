---
title: Meer informatie over CMS Headless Development
description: In dit deel van de AEM Headless Developer Journey, leer over technologie zonder kop en waarom je het zou gebruiken.
exl-id: 8c1fcaf7-1551-4133-b363-6f50af681661
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1626'
ht-degree: 0%

---

# Meer informatie over CMS Headless Development {#learn-about}

In dit deel van [ AEM de Zwaardeloze Reis van de Ontwikkelaar ](overview.md), leer over headless technologie en waarom u het zou gebruiken.

## Doelstelling {#objective}

Met dit document krijgt u inzicht in de levering van inhoud zonder kop en waarom het moet worden gebruikt. Na het lezen moet u:

* Begrijp de basisconcepten en de terminologie van de inhoud zonder kop levering
* Begrijpen waarom en wanneer een kop zonder kop nodig is
* Op hoog niveau weten hoe concepten zonder kop worden gebruikt en hoe ze met elkaar verweven zijn

## Volledige levering van inhoud {#full-stack}

Sinds de opkomst van gebruiksvriendelijke, grootschalige contentbeheersystemen (CMS&#39;s) hebben organisaties deze als centrale locatie gebruikt voor het beheer van berichten, branding en communicatie. Het gebruik van de CMS als centraal punt voor het beheer van ervaringen heeft geleid tot een verbeterde efficiëntie doordat het niet nodig is taken in verschillende systemen te dupliceren.

![ de klassieke volledig-stapel CMS ](assets/full-stack.png)

In een CMS met volledige stapel bevindt de functionaliteit voor het manipuleren van uw inhoud zich in de CMS. De functies van het systeem bestaan uit verschillende onderdelen van de CMS-stapel. De full-stack oplossing heeft veel voordelen.

* U hebt één systeem om te onderhouden.
* Inhoud wordt centraal beheerd.
* Alle diensten van het systeem zijn geïntegreerd.
* Inhoud schrijven is naadloos.

Als u dus een nieuw kanaal wilt toevoegen of nieuwe soorten ervaringen wilt ondersteunen, kunt u een (of meer) nieuwe componenten in de stapel invoegen en hebt u slechts één plaats om uw wijzigingen aan te brengen.

![ Toevoegend een nieuw kanaal aan de stapel ](assets/adding-channel.png)

De complexiteit van de afhankelijkheden in de stapel wordt snel zichtbaar, aangezien u ziet dat andere items in de stapel moeten worden aangepast aan de wijzigingen.

## Limieten voor volledige stapellevering {#limits}

De full-stack aanpak creëert inherent een silo waar alle landen in één systeem ervaren. Wijzigingen of toevoegingen aan één component van de silo vereisen wijzigingen in andere componenten, waardoor de tijd veel tijd kost en de kosten kostbaar zijn.

Dit geldt met name voor het presentatiesysteem, dat in traditionele instellingen vaak nauw verbonden is met de CMS. Een nieuw kanaal betekent doorgaans een update van het presentatiesysteem, die van invloed kan zijn op alle andere kanalen.

![ de Complexiteit groeit aangezien de kanalen aan een stapel ](assets/presentation-complexity.png) worden toegevoegd

De beperkingen van deze natuurlijke silo kunnen duidelijk worden aangezien u meer inspanning besteedt om veranderingen over alle componenten van uw stapel te coördineren.

Gebruikers verwachten betrokkenheid, ongeacht het platform of aanraakpunt, waardoor u flexibel moet zijn in de manier waarop u uw ervaringen kunt aanbieden.  Deze multikanaalbenadering is de standaard van digitale ervaringen en een aanpak met volledige stapel kan in bepaalde omstandigheden onflexibel blijken.

## De kop in de kop {#the-head}

Het hoofd van een systeem is doorgaans de uitvoerrenderer van dat systeem, meestal in de vorm van een grafische interface of andere grafische uitvoer.

Een server zonder kop bijvoorbeeld zit waarschijnlijk ergens in een rack in een serverruimte en heeft geen monitor aangesloten. Om tot het toegang te hebben moet u ver met het verbinden. In dit geval is de monitor de kop omdat deze zorgt voor het renderen van de uitvoer van de server. Als consument van de service geeft u uw eigen hoofd (de monitor) op wanneer u op afstand verbinding maakt.

Als we het hebben over een CMS zonder kop, beheert de CMS de inhoud en blijft ze leveren aan de consument. Nochtans, door slechts de **inhoud** op een gestandaardiseerde manier te leveren, weglaat een headless CMS de definitieve output die teruggeeft, verlatend de **presentatie** van de inhoud aan de verbruikende dienst.

![ Headless CMS ](assets/headless-cms.png)

De verbruikende services, of het nu gaat om AIR, een webshop, mobiele ervaring, progressieve webapps (PWA), enzovoort, nemen inhoud van de CMS zonder kop in en bieden hun eigen rendering. Ze zorgen ervoor dat ze hun eigen hoofd geven aan je inhoud.

Als u de kop weglaat, wordt de CMS vereenvoudigd doordat de complexiteit wordt weggenomen. Hierdoor wordt ook de verantwoordelijkheid voor het renderen van de inhoud verplaatst naar de diensten die de inhoud nodig hebben en die vaak beter geschikt zijn voor dergelijke rendering.

## Ontkoppelen {#decoupling}

De levering zonder kop is mogelijk door een reeks robuuste en flexibele API&#39;s (Application Programming Interfaces) beschikbaar te maken die al uw ervaringen kunnen selecteren. De API dient als een gemeenschappelijke taal tussen de diensten, die hen op het inhoudsniveau door gestandaardiseerde inhoudslevering binden, maar hen de flexibiliteit toestaan om hun eigen oplossingen uit te voeren.

Met Headless kunt u bijvoorbeeld inhoud loskoppelen van de presentatie. Of in een generischere betekenis, ontkoppelt het vooreind van het achtereind van uw de dienststapel. In een headless opstelling, wordt het presentatiesysteem (het hoofd) losgemaakt van het inhoudsbeheer (staart). De twee werken slechts door API vraag in wisselwerking.

Deze ontkoppeling betekent dat elke verbruikende service (front-end) zijn ervaring kan opbouwen op basis van dezelfde inhoud die via de API&#39;s wordt geleverd, zodat de inhoud hergebruikt en consistent blijft. De verbruikende diensten kunnen hun eigen presentatiesystemen dan uitvoeren, toestaand de stapel van het inhoudsbeheer (het achtereind) om horizontaal te schrapen.

## Technologische onderbouwing {#technology}

Met een headless-aanpak kunt u een technologiestapel maken die u eenvoudig en snel kunt aanpassen aan de eisen van toekomstige digitale ervaringen.

In het verleden waren de API&#39;s voor CMS&#39;s meestal gebaseerd op REST. Representatiestatus-overdracht (REST) biedt bronnen als tekst op statenloze wijze. Hierdoor kunnen de bronnen worden gelezen en gewijzigd met een vooraf gedefinieerde set bewerkingen. REST maakte een grote interoperabiliteit tussen diensten op het web mogelijk door te zorgen voor een statenloze weergave van de inhoud.

Er is nog steeds behoefte aan robuuste REST API&#39;s. REST-verzoeken kunnen echter groot en uitgebreid zijn. Als er meerdere consumenten zijn die REST-oproepen voor al uw kanalen uitvoeren, kunnen deze uitgebreide verbindingen en prestaties worden beïnvloed.

Bij de levering van inhoud zonder kop wordt vaak gebruikgemaakt van GraphQL API&#39;s. GraphQL staat voor een gelijkaardige stateless overdracht toe, maar staat voor meer gerichte vragen toe, die het totale aantal vereiste vragen verminderen, en prestaties verbeteren. Het is gebruikelijk om oplossingen te zien die een combinatie van REST en GraphQL gebruiken, in feite het beste instrument kiezen voor de taak die hier ligt.

Wat de gekozen API ook is, door een headless-systeem te definiëren op basis van gemeenschappelijke API&#39;s, kunt u de nieuwste browser en andere webtechnologieën gebruiken, zoals progressieve webapps (PWA). API&#39;s maken een standaardinterface die eenvoudig kan worden uitgebreid en aangepast.

Inhoud wordt doorgaans weergegeven aan de clientzijde. Dit betekent doorgaans dat iemand uw inhoud op een mobiel apparaat aanroept, dat uw CMS de inhoud levert en dat het mobiele apparaat (de client) verantwoordelijk is voor het renderen van de inhoud die u hebt bediend. Als het apparaat oud of anderszins langzaam is, is uw digitale ervaring ook langzaam.

Door de inhoud los te koppelen van de presentatie kan er meer controle zijn over dergelijke prestatieproblemen aan de clientzijde. De server-kant teruggeven (SSR) brengt de verantwoordelijkheid over om de inhoud van browser van de cliënt aan de server terug te geven. Zo kunt u als leverancier van de inhoud uw publiek een niveau van gegarandeerde prestaties aanbieden als dat is wat wordt vereist.

## Organisatorische uitdagingen {#organization}

Met headless hebt u de beschikking over een wereld van flexibiliteit om uw digitale beleving te bieden. Maar deze flexibiliteit kan ook zijn eigen uitdaging vormen.

Als er veel verschillende kanalen zijn, kan dat betekenen dat ze elk hun eigen presentatiesystemen hebben. Hoewel ze allemaal dezelfde inhoud gebruiken via dezelfde API&#39;s, kan de ervaring verschillen vanwege de verschillende presentaties. De consistentie van de ervaring van de klant moet in het oog worden gehouden en er moet zorg voor worden gedragen.

Door zorgvuldige ontwerpsystemen uit te voeren, patroonbibliotheken te delen, herbruikbare ontwerpcomponenten te gebruiken en gevestigde open client-side frameworks te gebruiken, kunnen consistente ervaringen worden gegarandeerd, maar dit moet worden gepland.

## De toekomst is zonder kop en de toekomst is nu {#future}

Digitale ervaringen zullen blijven bepalen hoe merken met klanten communiceren. Wat aan headless ontwerp opwindend is is de flexibiliteit het ons geeft om aan evoluerende klantenverwachtingen te antwoorden.

Het is onmogelijk om de toekomst te voorspellen, maar zonder kop geeft u de flexibiliteit om te reageren op wat de toekomst brengt.

## AEM en zonder kop {#aem-and-headless}

Terwijl u deze ontwikkelaarstraject doorloopt, leert u hoe AEM levering zonder kop ondersteunt langs de volledige leveringsmogelijkheden van de stapel.

Als marktleider op het gebied van digitaal ervaringsbeheer realiseert de Adobe zich dat de ideale oplossing voor echte uitdagingen die ontwerpers ervaren zelden een binaire keuze is. Daarom AEM niet alleen beide modellen worden ondersteund, maar ook de naadloze hybride combinatie van beide, waarbij de voordelen van een volledig en zonder kop stapel worden gecombineerd, zodat u de consumenten van uw inhoud het beste kunt dienen, waar ze zich ook bevinden.

Deze reis concentreert zich op het hoofdloze-enige model van inhoudlevering. Maar als je deze basiskennis hebt, kun je verder verkennen hoe je de kracht van beide modellen kunt gebruiken.

## Volgende functies {#what-is-next}

Bedankt dat je aan de slag bent gegaan met je AEM tocht zonder kop! Nu u dit document leest, moet u:

* Begrijp de basisconcepten en de terminologie van koploze inhoudlevering.
* Begrijp waarom en wanneer de kop niet nodig is.
* Op hoog niveau weten hoe headless-concepten worden gebruikt en hoe ze met elkaar verweven zijn.

Bouw op deze kennis voort en ga uw AEM headless reis door het document [ opnieuw te bekijken Begonnen het worden Begonnen met AEM as a Cloud Service zonder hoofd ](getting-started.md) waar u leert hoe te opstelling de noodzakelijke hulpmiddelen en hoe te beginnen nadenken over hoe AEM de levering van de inhoud zonder kop en zijn eerste vereisten benadert.

## Aanvullende bronnen {#additional-resources}

Terwijl het wordt geadviseerd dat u zich op het volgende deel van de headless ontwikkelingsreis door het document [ te herzien Begonnen worden met AEM as a Cloud Service zonder hoofd ](getting-started.md) beweegt, zijn het volgende sommige extra, facultatieve middelen die een diepere duik op sommige die concepten in dit document doen worden vermeld, maar zij worden niet vereist om op de headless reis verder te gaan.

* [ een Inleiding aan de Architectuur van Adobe Experience Manager as a Cloud Service ](/help/overview/architecture.md) - begrijp de structuur van AEM as a Cloud Service
* Een [ Inleiding aan AEM als Zwaarloze CMS ](/help/headless/introduction.md)
* Het [ AEM Portaal van de Ontwikkelaar ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [ AEM Tutorials zonder kop ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html) - gebruik deze hands-on leerprogramma&#39;s om te onderzoeken hoe te om de diverse opties te gebruiken om inhoud aan headless eindpunten met AEM te leveren en te kiezen wat voor u juist is.
