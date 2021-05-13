---
title: Hoe u met uw headless toepassing kunt gaan werken
description: In dit deel van de AEM Headless Developer Journey leert u hoe u een toepassing zonder kop kunt implementeren door uw lokale code in Git te nemen en deze naar Cloud Manager Git voor de CI/CD-pijplijn te verplaatsen.
hide: true
hidefromtoc: true
index: false
exl-id: f79b5ada-8f59-4706-9f90-bc63301b2b7d
source-git-commit: 309fae113f98111e8dc548226a7fba1b72f16248
workflow-type: tm+mt
source-wordcount: '1836'
ht-degree: 0%

---

# Hoe te met Uw Hoofdloze Toepassing {#go-live} leven

>[!CAUTION]
>
>WERK IN VOORTGANG - De opstelling van dit document is aan de gang en mag niet worden opgevat als volledig of definitief en mag niet worden gebruikt voor productiedoeleinden.

In dit deel van [AEM Headless Developer Journey,](overview.md) leert u hoe u een toepassing zonder kop kunt implementeren door uw lokale code in Git te nemen en deze naar Cloud Manager Git voor de CI/CD-pijplijn te verplaatsen.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM headless reis, [Hoe te om het allen samen te zetten - Uw App en Uw Inhoud in AEM Koploze](put-it-all-together.md) leerde u hoe te om uw eigen AEM headless project voor te bereiden om levend te gaan en u zou nu moeten:

* Begrijp de vereisten om live te gaan.

Dit artikel bouwt op die grondbeginselen voort zodat begrijpt u hoe te om uw AEM Project zonder hoofd levend te brengen.

## Doelstelling {#objective}

Met dit document krijgt u inzicht in de publicatiepijplijn zonder kop en in de prestatieaspecten die u moet kennen voordat u live gaat met uw toepassing.

* Meer informatie over de AEM SDK en de vereiste ontwikkelingstools
* Een lokale ontwikkelingstijd instellen om uw inhoud te simuleren voordat u live gaat
* Inhoudsreplicatie en basiskennis van AEM inhoud in cache
* De toepassing beveiligen en schalen voordat deze wordt gestart
* Prestaties bewaken en problemen met foutopsporing opsporen

## De AEM-SDK {#the-aem-sdk}

Het bevat de volgende artefacten:

* De QuickStart-jar - een uitvoerbaar JAR-bestand dat kan worden gebruikt om een auteur- en een publicatie-instantie in te stellen
* De hulpmiddelen van de verzending - de module van de Dispatcher en zijn gebiedsdelen voor Vensters en op UNIX gebaseerde systemen
* Java API Jar - De Java Jar/Maven-afhankelijkheid die alle toegestane Java API&#39;s beschikbaar maakt die kunnen worden gebruikt om zich te ontwikkelen tegen AEM
* Javadoc jar - de javadocs voor de Java API jar

## Ontwikkelingsgereedschappen {#development-tools}

Naast de AEM SDK hebt u aanvullende gereedschappen nodig die het ontwikkelen en testen van uw code en inhoud lokaal vergemakkelijken:

* Java
* De AEM SDK
* Git
* Apache Maven
* De Node.js-bibliotheek
* De IDE van uw keuze

Omdat AEM een Java-toepassing is, moet u Java en de Java SDK installeren om de ontwikkeling van AEM als Cloud Service te ondersteunen.

De AEM SDK wordt gebruikt om aangepaste code te maken en in te voeren. Het is het belangrijkste hulpmiddel u nodig om uw toepassing zonder kop te testen alvorens te leven.

Git is wat u zult gebruiken om broncontrole te beheren evenals de veranderingen in de Manager van de Wolk te controleren en dan hen op te stellen aan een productie instantie.

AEM gebruikt Apache Maven om projecten te bouwen die uit AEM Maven Project archetype worden geproduceerd. Alle belangrijke IDEs verstrekt integratiesteun voor Maven.

Node.js is een runtimeomgeving JavaScript die wordt gebruikt om met de front-end activa van het subproject ui.frontend van een AEM project te werken. Node.js wordt gedistribueerd met npm, is de facto het pakketbeheer Node.js, dat wordt gebruikt om JavaScript gebiedsdelen te beheren.

## Componenten van een AEM systeem in één oogopslag {#components-of-an-aem-system-at-a-glance}

Een volledige AEM omgeving bestaat uit een Auteur, Publish en Dispatcher. Deze componenten worden beschikbaar gesteld in de lokale ontwikkelingstijd zodat u gemakkelijker een voorvertoning van uw code en inhoud kunt bekijken voordat u live gaat.

* **De** service Auteur biedt interne gebruikers de mogelijkheid inhoud te maken, te beheren en voor te vertonen.

* **De** service Publiceren wordt beschouwd als de &quot;live&quot;-omgeving en is doorgaans de omgeving waarmee eindgebruikers werken. Inhoud wordt na bewerking en goedkeuring in de service Auteur gedistribueerd naar de service Publiceren. Het meest gebruikelijke implementatiepatroon met toepassingen zonder kop is dat de productieversie van de toepassing verbinding maakt met een AEM-publicatieservice.

* **De** Dispatcher is een statische webserver die is aangevuld met de AEM dispatcher-module. Webpagina&#39;s die door de instantie publish worden gemaakt, worden in het cachegeheugen opgeslagen om de prestaties te verbeteren.

## De lokale ontwikkelingsworkflow {#the-local-development-workflow}

Het lokale ontwikkelingsproject is gebaseerd op Apache Maven en gebruikt Git voor broncontrole. Om het project bij te werken, kunnen de ontwikkelaars hun aangewezen geïntegreerde ontwikkelomgeving, zoals Eclipse, de Code van Visual Studio of IntelliJ, onder andere gebruiken.

Als u code- of inhoudsupdates wilt testen die door uw toepassing zonder kop worden opgenomen, moet u de updates voor de lokale AEM-runtime implementeren, die lokale instanties van de AEM auteur en publicatieservices bevat.

Let op het verschil tussen de verschillende componenten in de lokale AEM runtime, want het is belangrijk dat u de updates test op de plaatsen waar ze het belangrijkst zijn. Test bijvoorbeeld de inhoud van updates op de auteur of test nieuwe code op de publicatie-instantie.

In een productiesysteem, zullen een verzender en een server http Apache altijd voor een AEM publicatiegeval zitten. Zij verlenen caching en de dienstdiensten voor het AEM systeem, zodat is het uiterst belangrijk om code en inhoudsupdates tegen de verzender eveneens te testen.

Zodra u ervoor hebt gezorgd dat alles is getest en correct werkt, kunt u uw code-updates naar een gecentraliseerde Git-opslagplaats in Cloud Manager verzenden.

Nadat de updates zijn geüpload naar Cloud Manager, kunnen ze worden geïmplementeerd als een Cloud Service met de CI/CD-pijplijn van Cloud Manager.

## Een lokale voorvertoning van uw code en inhoud weergeven in de lokale ontwikkelomgeving {#previewing-your-code-and-content-locally-with-the-local-development-environment}

Als u uw AEM project zonder kop wilt voorbereiden op de start, moet u ervoor zorgen dat alle onderdelen van uw project goed werken.

Om dat te doen, moet je alles samenvoegen: code, inhoud en configuratie en test het in een lokale ontwikkelomgeving voor go live gereedheid.

De lokale ontwikkelomgeving bestaat uit drie hoofdgebieden:

1. Het AEM Project - dit zal alle douanecode, configuratie en inhoud bevatten de AEM ontwikkelaars zullen werken aan
1. Lokale AEM Runtime - lokale versies van de AEM auteur en publiceer de diensten die zullen worden gebruikt om code van het AEM project op te stellen
1. De lokale Dispatcher Runtime - een lokale versie van de Apache htttpd-webserver die de Dispatcher-module bevat

Nadat de lokale ontwikkelomgeving is ingesteld, kunt u inhoud die in de React-app wordt gebruikt, simuleren door een statische Node-server lokaal te implementeren.

Zie [Production Deployment with an AEM Publish Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/production-deployment.html?lang=en#prerequisites) voor een meer gedetailleerde uitleg van het instellen van een lokale ontwikkelomgeving en alle afhankelijkheden die nodig zijn voor voorvertoning van inhoud.

## Distribueren naar productie {#deploy-to-production}

Zodra u al uw code en inhoud plaatselijk hebt getest, bent u bereid om een productielocatie met AEM te beginnen.

U kunt uw code beginnen op te stellen door de Ci/CD-pijplijn van de Manager van de Wolk te gebruiken, die uitgebreid [hier](/help/implementing/deploying/overview.md) wordt behandeld.

## Uw AEM toepassing zonder koppen voorbereiden voor Go-Live {#prepare-your-aem-headless-application-for-golive}

Nu is het tijd om uw AEM headless toepassing klaar te maken voor lancering, door de hieronder geschetste beste praktijken te volgen.

### Beveilig en schaal uw toepassing zonder hoofd alvorens {#secure-and-scale-before-launch} te lanceren

1. [Op token gebaseerde verificatie](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) configureren
1. Beveiligde webhaken
1. Caching en schaalbaarheid configureren

### Modelstructuur versus GraphQL-uitvoer {#structure-vs-output}

* Maak geen query&#39;s die meer dan 15 kB van JSON uitvoeren (gecomprimeerd gzip). Lange JSON-bestanden zijn bronintensief, zodat de clienttoepassing kan parseren.
* Vermijd meer dan vijf geneste niveaus van fragmenthiërarchieën. Met extra niveaus kunnen auteurs van inhoud de gevolgen van hun wijzigingen moeilijk in overweging nemen.
* Gebruik multiobject query&#39;s in plaats van query&#39;s met afhankelijkheidshiërarchieën binnen de modellen te modelleren. Hierdoor is meer flexibiliteit op lange termijn mogelijk om JSON-uitvoer te herstructureren zonder dat er veel wijzigingen in de inhoud moeten worden aangebracht.

### CDN-hoogte-breedteverhouding in cache maximaliseren {#maximize-cdn}

* Gebruik geen directe vragen GraphQL, tenzij u levende inhoud van de oppervlakte verzoekt.
   * Gebruik in plaats daarvan doorlopende query&#39;s.
   * Verstrek CDN TTL boven 600 seconden zodat CDN hen kan in het voorgeheugen onderbrengen.
   * AEM kan het effect van een modelwijziging op bestaande query&#39;s berekenen.
* Splits JSON- dossiers/GraphQL- vragen tussen laag en hoge tarief van de inhoudsverandering om cliëntverkeer aan CDN te verminderen en hogere TTL toe te wijzen. Dit minimaliseert CDN die JSON met de oorsprongserver opnieuw bevestigt.
* Als u de inhoud van de CDN actief ongeldig wilt maken, gebruikt u Zacht wissen. Hierdoor kan de CDN de inhoud opnieuw downloaden zonder dat een cache-fout optreedt.

### Tijd voor downloaden van inhoud zonder kop {#improve-download-time} verbeteren

* Zorg ervoor dat HTTP-clients HTTP/2 gebruiken.
* Zorg ervoor dat HTTP-clients de headeraanvraag voor gzip accepteren.
* Minimaliseer het aantal domeinen dat wordt gebruikt om JSON te hosten en referenced artefacten.
* Gebruik `Last-modified-since` om bronnen te vernieuwen.
* Gebruik `_reference` uitvoer in JSON-bestand om te beginnen met het downloaden van elementen zonder dat u volledige JSON-bestanden hoeft te parseren.

## Prestatiebewaking {#performance-monitoring}

Om gebruikers de best mogelijke ervaring te geven bij het gebruik van de AEM toepassing zonder kop, is het belangrijk dat u de belangrijkste prestatiewaarden in de gaten houdt, zoals hieronder wordt beschreven:

* Voorvertoning- en productieversies van de app valideren
* Verifieer AEM statuspagina&#39;s voor huidige de status van de de dienstbeschikbaarheid
* Toegang tot prestatierapporten
   * Leveringsprestaties
      * Fastly (CDN) - controleaantal vraag, geheim voorgeheugentarief, foutentarieven, ladingsverkeer
      * De servers van de oorsprong - aantal vraag, foutentarieven, cpu laadt, loonladingsverkeer
   * Auteursprestaties
      * Aantal gebruikers, aanvragen en laden controleren
* Toepassings- en ruimtespecifieke prestatierapporten openen
   * Als de server is geactiveerd, controleert u of de algemene meetwaarden groen/oranje/rood zijn en identificeert u vervolgens specifieke toepassingsproblemen
   * Open dezelfde rapporten die hierboven zijn gefilterd naar app/space (zoals Photoshop-bureaublad, paywall, enz.)
   * Logbestand-API&#39;s van Splunk gebruiken om toegang te krijgen tot service- en toepassingsprestaties
   * Neem contact op met de Klantenondersteuning als er andere problemen zijn.

## Problemen oplossen {#troubleshooting}

### Foutopsporing {#debugging}

Volg deze beste praktijken als algemene benadering van het zuiveren:

* Functionaliteit en prestaties valideren met de voorvertoningsversie van de toepassing
* Functionaliteit en prestaties valideren met de productieversie van de toepassing
* Valideren met de JSON-voorvertoning van de Content Fragment Editor
* Inspect de JSON in de clienttoepassing om te controleren of er problemen zijn met de clienttoepassing of levering
* Inspect de JSON met GraphQL om te controleren of er problemen zijn met inhoud of AEM in cache.

### Een probleem aanmelden met ondersteuning {#logging-a-bug-with-support}

Volg de onderstaande stappen om een bug efficiënt te kunnen aanmelden bij Support voor het geval u verdere hulp nodig hebt:

* Maak, indien nodig, screenshots van het probleem
* Een manier documenteren om het probleem te reproduceren
* Documenteer de inhoud waarmee de uitgave wordt gereproduceerd
* Logboek een kwestie door het portaal van de Steun van de AEM met de aangewezen prioriteit

## Volgende {#what-is-next}

Nu u dit deel van de AEM Headless Developer Journey hebt voltooid, moet u:

* Inhoudsreplicatie en basiskennis van AEM inhoud in cache begrijpen.
* Zorg dat u weet hoe u de vereiste gereedschappen configureert om live te gaan voor uw toepassing zonder kop.
* Zorg dat u weet hoe u de toepassing kunt beveiligen en schalen voordat u de toepassing start.
* Begrijp hoe te om Prestaties te controleren en te zuiveren Kwesties.

U moet uw AEM zonder kop voortzetten door het document [Post Launch](post-launch.md) te bekijken waar u leert hoe u uw headless ervaring kunt behouden.

## Aanvullende bronnen {#additional-resources}

* [Een lokale AEM instellen](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html)
* [De AEM als Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
* [Een overzicht van het Opstellen aan AEM als Cloud Service](/help/implementing/deploying/overview.md)
* [Cloud Manager gebruiken om uw code te implementeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html)
* [Integreer de gegevensopslagruimte van de Intel Health Care Management Suite van Cloud Manager met een externe opslagplaats voor Git en implementeer een project om als Cloud Service te AEM](https://git.corp.adobe.com/AdobeDocs/experience-manager-cloud-service.en/blob/master/help/implementing/developing/headless-journey/access-your-content.md)