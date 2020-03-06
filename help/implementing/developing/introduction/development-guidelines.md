---
title: Ontwikkelingsrichtlijnen voor AEM as a Cloud Service
description: 'In te vullen '
translation-type: tm+mt
source-git-commit: 9777dd5772ab443b5b3dabbc74ed0d362e52df60

---


# Ontwikkelingsrichtlijnen voor AEM as a Cloud Service {#aem-as-a-cloud-service-development-guidelines}

De code die in AEM als Dienst van de Wolk loopt moet zich van het feit bewust zijn dat het altijd in een cluster loopt. Dit betekent dat er altijd meer dan één instantie lopend is. De code moet veerkrachtig zijn vooral aangezien een instantie op om het even welk punt in tijd zou kunnen worden tegengehouden.

Tijdens de update van AEM als Dienst van de Wolk, zullen er instanties met oude en nieuwe code zijn die parallel lopen. Daarom moet de oude code niet met inhoud breken die door nieuwe code wordt gecreeerd en de nieuwe code moet oude inhoud kunnen behandelen.
<!--

>[!NOTE]
> All of the best practices mentioned here hold true for on-premise deployments of AEM, if not stated otherwise. An instance can always stop due to various reasons. However, with Skyline it is more likely to happen therefore an instance stopping is the rule not an exception.

-->

Als er de behoefte is om de meester in de cluster te identificeren, kan Apache Sling Ontdekking API worden gebruikt om het te ontdekken.

## Status in geheugen {#state-in-memory}

De staat mag niet in het geheugen worden bewaard, maar moet in de bewaarplaats blijven. Anders, zou deze staat verloren kunnen worden als een instantie wordt tegengehouden.

## Staat op het bestandssysteem {#state-on-the-filesystem}

Het dossiersysteem van de instantie zou niet in AEM als Dienst van de Wolk moeten worden gebruikt. De schijf is tijdelijk en zal worden verwijderd wanneer de instanties worden gerecycled. Beperkt gebruik van het bestandssysteem voor tijdelijke opslag in verband met de verwerking van afzonderlijke aanvragen is mogelijk, maar mag niet worden misbruikt voor grote bestanden. Dit is omdat het een negatieve invloed op de quota van het middelgebruik kan hebben en in schijfbeperkingen in werking stelt.

Als voorbeeld waar het gebruik van het dossiersysteem niet wordt gesteund, zou de Publish rij ervoor moeten zorgen dat om het even welke gegevens die moeten worden voortgeduurd wordt verscheept naar de externe dienst voor opslag op langere termijn.

## Waarneming {#observation}

Evenzo kan, met alles wat asynchroon gebeurt als optreden bij observatiegebeurtenissen, niet worden gegarandeerd dat het lokaal wordt uitgevoerd en daarom met zorg moet worden gebruikt. Dit is waar voor zowel gebeurtenissen JCR als het Verdelen van middelgebeurtenissen. Op het ogenblik een verandering gebeurt, kan de instantie worden geschrapt en door een verschillende instantie worden vervangen. Andere instanties in de topologie die op dat ogenblik actief zijn zullen aan die gebeurtenis kunnen reageren. In dit geval zal dit echter geen lokale gebeurtenis zijn en er zou zelfs geen actieve leider kunnen zijn in het geval van een permanente verkiezing van de leider op het moment dat het evenement wordt uitgeschreven.

## De achtergrond Taken en Lange Lopende Banen {#background-tasks-and-long-running-jobs}

De code die als achtergrondtaken wordt uitgevoerd moet veronderstellen dat de instantie het binnen loopt kan op elk ogenblik worden verminderd. Daarom moet de code veerkrachtig zijn en de meeste invoer herbruikbaar. Dat betekent dat als de code opnieuw wordt uitgevoerd het niet van het begin opnieuw zou moeten beginnen maar eerder dicht bij van waar het weg verliet. Hoewel dit geen nieuw vereiste voor dit soort code is, is het in AEM als Dienst van de Wolk waarschijnlijker dat een instantie neer zal treden zal voorkomen.

Om de problemen tot een minimum te beperken, moeten zo mogelijk lange loopbanen worden vermeden en moeten ze minimaal herbruikbaar zijn. Om dergelijke banen uit te voeren, zal gebruik worden gemaakt van Sling Jobs, die minstens één garantie hebben en daarom als ze worden onderbroken zo snel mogelijk weer worden uitgevoerd. Maar ze zouden waarschijnlijk niet opnieuw van het begin moeten beginnen. Voor het plannen van dergelijke banen, is het best om de Planner van de Banen [van het](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) Verdelen als dit opnieuw te gebruiken minstens-eens uitvoering.

De het Verdelen Planner van Commons zou niet voor het plannen moeten worden gebruikt aangezien de uitvoering niet kan worden gewaarborgd. Het is gewoon waarschijnlijker dat het gepland zal worden.

Op dezelfde manier met alles dat asynchroon gebeurt, zoals acteren op observatiegebeurtenissen, (het zijn JCR gebeurtenissen of het Verdelen van middelgebeurtenissen), kan niet worden gegarandeerd om worden uitgevoerd en daarom moet met voorzichtigheid worden gebruikt. Dit geldt nu al voor AEM-implementaties.

## Uitgaande HTTP-verbindingen {#outgoing-http-connections}

Het wordt sterk geadviseerd dat om het even welke uitgaande die verbindingen van HTTP redelijk plaatsen verbinden en onderbrekingen lezen. Voor code die deze onderbrekingen niet toepast, zullen de instanties AEM die op AEM als Dienst van de Wolk lopen een globale onderbrekingen afdwingen. Deze onderbrekingswaarden zijn 10 seconden voor verbind vraag en 60 seconden voor gelezen vraag naar verbindingen die door de volgende populaire bibliotheken van Java worden gebruikt:

Adobe adviseert het gebruik van de verstrekte Cliënt 4.x van [Apache HttpComponents van de Cliënt](https://hc.apache.org/httpcomponents-client-ga/) Apache voor het maken van de verbindingen van HTTP.

Alternatieven waarvan bekend is dat ze werken, maar die het nodig kunnen maken dat ze zelf afhankelijk zijn, zijn:

* [java.net.URL](https://docs.oracle.com/javase/7/docs/api/java/net/URL.html) en/of [java.net.URLConnection](https://docs.oracle.com/javase/7/docs/api/java/net/URLConnection.html) (geleverd door AEM)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (niet aanbevolen omdat deze verouderd is en vervangen wordt door versie 4.x)
* [OK Http](https://square.github.io/okhttp/) (niet verstrekt door AEM)

## Geen Klassieke UI-aanpassingen {#no-classic-ui-customizations}

AEM als Cloud Service ondersteunt alleen Touch UI voor klantcode van andere leveranciers. Klassieke UI is niet beschikbaar voor aanpassing.

## Vermijd inheemse bindmiddelen {#avoid-native-binaries}

De code zal niet binaire getallen bij runtime kunnen downloaden noch hen wijzigen. Bijvoorbeeld, zal het niet kunnen uitpakken `jar` of `tar` dossiers.

## Geen Streaming Binaries via AEM als Cloud Service {#no-streaming-binaries}

De binaire getallen zouden door CDN moeten worden betreden, die binaire getallen buiten de kernAEM diensten zal dienen.

Bijvoorbeeld, gebruik niet `asset.getOriginal().getStream()`, die het downloaden van een binair getal op de tijdelijke schijf van de dienst AEM teweegbrengt.

## Geen omgekeerde replicatiemiddelen {#no-reverse-replication-agents}

De omgekeerde replicatie van Publish aan Auteur wordt niet gesteund in AEM als Dienst van de Wolk. Als zulk een strategie nodig is, kunt u een externe persistentieopslag gebruiken die onder het landbouwbedrijf van Publish instanties en potentieel de cluster van de Auteur wordt gedeeld.

## De voorwaartse Agenten van de Replicatie zouden kunnen moeten worden geporteerd {#forward-replication-agents}

De inhoud wordt herhaald van Auteur om door een submechanisme te publiceren. De de replicatieagenten van de douane worden niet gesteund.

## Monitoring en foutopsporing {#monitoring-and-debugging}

### Logboeken {#logs}

* Voor lokale ontwikkeling, worden de logboekingangen geschreven aan lokale dossiers
   * `./crx-quickstart/logs`
* Voor de milieu&#39;s van de Wolk, kunnen de ontwikkelaars logboeken door de Manager van de Wolk downloaden of een hulpmiddel van de bevellijn gebruiken om de logboeken te staart. <!-- See the [Cloud Manager documentation](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->
* Om de logboekniveaus voor de milieu&#39;s van de Wolk te veranderen, zou de het Sling Registreren configuratie OSGI moeten worden gewijzigd, gevolgd door een volledige herplaatsing. Aangezien dit niet onmiddellijk is, ben voorzichtigheid over het toelaten van breedsprakige logboeken op productiemilieu&#39;s die veel verkeer ontvangen. In de toekomst, is het mogelijk dat er mechanismen zullen zijn om het logboekniveau sneller te veranderen.

### Dresdeerpompen {#thread-dumps}

De dumps van de draad op de milieu&#39;s van de Wolk worden verzameld op een voortdurende basis, maar kunnen niet op een zelf-servermanier op dit ogenblik worden gedownload. Ondertussen, te contacteren gelieve AEM steun als de draaddumps voor het zuiveren van een kwestie nodig zijn, specificerend het nauwkeurige tijdvenster.

## CRX/DE Lite en de Console van het Systeem {#crxde-lite-and-system-console}

### Lokale ontwikkeling {#local-development}

Voor lokale ontwikkeling, hebben de Ontwikkelaars volledige toegang tot CRXDE Lite (`/crx/de`) en de Console van het Web AEM (`/system/console`).

Merk op dat op lokale ontwikkeling (het gebruiken van de wolk-klaar snelle start), `/apps` en `/libs` kan worden geschreven aan direct, dat van de milieu&#39;s van de Wolk verschillend is waar die hoogste niveauomslagen onveranderlijk zijn.

### AEM as a Cloud Service Development tools {#aem-as-a-cloud-service-development-tools}

De klanten kunnen tot CRXDE lijst op de ontwikkelomgeving maar niet stadium of productie toegang hebben. De onveranderlijke bewaarplaats (`/libs`, `/apps`) kan niet aan bij runtime worden geschreven zodat zal het proberen om dit te doen in fouten resulteren.

Een reeks hulpmiddelen om AEM als ontwikkelaarmilieu&#39;s van de Dienst van de Wolk te zuiveren is beschikbaar in de Console van de Ontwikkelaar voor ontwikkelaar voor ontwikkelings, stadium, en productiemilieu&#39;s. De URL kan worden bepaald door de Auteur aan te passen of de de diensturls van de Publish als volgt aan te passen:

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

Als kortere weg, kan het volgende CLI bevel van de Manager van de Wolk worden gebruikt om de ontwikkelaarconsole te lanceren die op een milieuparameter wordt gebaseerd die hieronder wordt beschreven:

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

Zie [deze pagina](/help/release-notes/home.md) voor meer informatie.

De ontwikkelaars kunnen statusinformatie produceren, en diverse middelen oplossen.

Zoals hieronder wordt geïllustreerd, omvat de beschikbare statusinformatie de staat van bundels, componenten, configuraties OSGI, eiken indexen, diensten OSGI, en het Sling banen.

![Dev Console 1](/help/implementing/developing/introduction/assets/devconsole1.png)

Zoals hieronder geïllustreerd, kunnen de ontwikkelaars pakketgebiedsdelen en servers oplossen:

![Dev Console 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![Dev Console 3](/help/implementing/developing/introduction/assets/devconsole3.png)

Ook nuttig om te zuiveren, heeft de console van de Ontwikkelaar een verbinding aan het Verklaar hulpmiddel van de Vraag:

![Dev Console 4](/help/implementing/developing/introduction/assets/devconsole4.png)

### AEM-fasering en -productie {#aem-staging-and-production-service}

De klanten zullen geen toegang tot ontwikkelaarhulpmiddelen voor het opvoeren en productiemilieu&#39;s hebben.

### Prestatiebewaking {#performance-monitoring}

Adobe controleert toepassingsprestaties en neemt maatregelen om te richten als de verslechtering wordt waargenomen. Op dit ogenblik, kunnen de toepassingsmetriek niet worden gehoorzaamd.