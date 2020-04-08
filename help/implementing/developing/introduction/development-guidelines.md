---
title: Ontwikkelingsrichtlijnen voor AEM as a Cloud Service
description: In te vullen
translation-type: tm+mt
source-git-commit: 114bc678fc1c6e3570d6d2a29bc034feb68aa56d

---


# Ontwikkelingsrichtlijnen voor AEM as a Cloud Service {#aem-as-a-cloud-service-development-guidelines}

Code die in AEM als Cloud Service wordt uitgevoerd, moet zich ervan bewust zijn dat deze altijd in een cluster wordt uitgevoerd. Dit betekent dat er altijd meer dan één instantie actief is. De code moet veerkrachtig zijn, vooral omdat een instantie op om het even welk ogenblik zou kunnen worden tegengehouden.

Tijdens de update van AEM als Cloud Service zijn er exemplaren met oude en nieuwe code die parallel lopen. Daarom moet oude code niet breken met inhoud die door nieuwe code wordt gecreeerd en de nieuwe code moet oude inhoud kunnen behandelen.
<!--

>[!NOTE]
> All of the best practices mentioned here hold true for on-premise deployments of AEM, if not stated otherwise. An instance can always stop due to various reasons. However, with Skyline it is more likely to happen therefore an instance stopping is the rule not an exception.

-->

Als de master in de cluster moet worden geïdentificeerd, kan de API voor detectie van Apache Sling worden gebruikt om deze te detecteren.

## Staat in geheugen {#state-in-memory}

De staat moet niet in geheugen worden bewaard maar in bewaarplaats voortbestaan. Anders kan deze status verloren gaan als een instantie wordt gestopt.

## Status van het bestandssysteem {#state-on-the-filesystem}

Het bestandssysteem van de instantie mag niet in AEM worden gebruikt als cloudservice. De schijf is ephenaal en wordt verwijderd wanneer instanties worden gerecycled. Beperkt gebruik van het bestandssysteem voor tijdelijke opslag in verband met de verwerking van afzonderlijke aanvragen is mogelijk, maar mag niet worden misbruikt voor grote bestanden. Dit is omdat het een negatieve invloed op het hulpmiddelgebruiksquotum kan hebben en op schijfbeperkingen in werking kan stellen.

Als voorbeeld waar het gebruik van het dossiersysteem niet wordt gesteund, zou de Publish rij ervoor moeten zorgen dat om het even welke gegevens die moeten worden voortgeduurd naar een externe dienst voor opslag op langere termijn wordt verscheept.

## Waarneming {#observation}

Net als bij alles wat asynchroon gebeurt, zoals bij observatiegebeurtenissen, kan niet worden gegarandeerd dat het lokaal wordt uitgevoerd en moet het daarom met zorg worden gebruikt. Dit geldt zowel voor JCR-gebeurtenissen als voor Sling-brongebeurtenissen. Op het moment dat een wijziging plaatsvindt, kan de instantie worden verwijderd en worden vervangen door een andere instantie. Andere instanties in de topologie die op dat ogenblik actief zijn zullen op die gebeurtenis kunnen reageren. In dit geval zal dit echter geen lokale gebeurtenis zijn en is er misschien zelfs geen actieve leider in het geval van een doorlopende verkiezing van de leider op het moment dat het evenement wordt uitgegeven.

## Achtergrondtaken en langdurige taken {#background-tasks-and-long-running-jobs}

Code die als achtergrondtaken wordt uitgevoerd, moet ervan uitgaan dat de instantie waarin deze wordt uitgevoerd, op elk gewenst moment kan worden ingedrukt. Daarom moet de code veerkrachtig zijn en het meest invoer herbruikbaar. Dat betekent dat als de code opnieuw wordt uitgevoerd, deze niet opnieuw van het begin moet beginnen, maar eerder dicht bij het punt waar de code is gebleven. Hoewel dit geen nieuwe vereiste voor dit soort code is, is het in AEM als Cloud Service waarschijnlijker dat een instantie zal verdwijnen.

Om de problemen tot een minimum te beperken, moeten zo mogelijk langdurige banen worden vermeden, en deze moeten ten minste herbruikbaar zijn. Voor het uitvoeren van dergelijke banen gebruikt u Sling Jobs, die minstens eenmaal een garantie hebben en die daarom zo snel mogelijk opnieuw zal worden uitgevoerd als ze worden onderbroken. Maar ze zouden waarschijnlijk niet opnieuw van het begin moeten beginnen. Voor het plannen van dergelijke banen, is het best om de het [Verkopen planner van Banen](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) als dit opnieuw minstens één uitvoering te gebruiken.

De Sling Commons Planner zou niet voor het plannen moeten worden gebruikt aangezien de uitvoering niet kan worden gewaarborgd. Het is nog waarschijnlijker dat het zal worden gepland.

Op dezelfde manier, met alles dat asynchroon gebeurt, zoals handelend op observatiegebeurtenissen, (het zijn gebeurtenissen JCR of Sling resource), kan niet gegarandeerd worden uitgevoerd en daarom met voorzichtigheid worden gebruikt. Dit geldt al voor AEM-implementaties in het heden.

## Uitgaande HTTP-verbindingen {#outgoing-http-connections}

Het wordt sterk geadviseerd dat om het even welke uitgaande verbindingen van HTTP redelijk plaatsen verbind en lees onderbrekingen. Voor code die deze time-outs niet toepast, dwingen AEM-instanties die als Cloud Service op AEM worden uitgevoerd een algemene time-out af. Deze onderbrekingswaarden zijn 10 seconden voor verbind vraag en 60 seconden voor gelezen vraag naar verbindingen die door de volgende populaire bibliotheken van Java worden gebruikt:

Adobe raadt het gebruik van de meegeleverde [Apache HttpComponents Client 4.x-bibliotheek](https://hc.apache.org/httpcomponents-client-ga/) aan voor het maken van HTTP-verbindingen.

Alternatieven waarvan bekend is dat ze werken, maar waarvoor de afhankelijkheid zelf nodig kan zijn, zijn:

* [java.net.URL](https://docs.oracle.com/javase/7/docs/api/java/net/URL.html) en/of [java.net.URLConnection](https://docs.oracle.com/javase/7/docs/api/java/net/URLConnection.html) (geleverd door AEM)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (niet aanbevolen omdat het verouderd is en vervangen wordt door versie 4.x)
* [OK Http](https://square.github.io/okhttp/) (niet verstrekt door AEM)

## Geen Klassieke UI-aanpassingen {#no-classic-ui-customizations}

AEM als Cloud Service ondersteunt alleen de Touch UI voor klantcode van derden. Klassieke UI is niet beschikbaar voor aanpassing.

## Native binaire getallen vermijden {#avoid-native-binaries}

Code kan geen binaire bestanden downloaden tijdens runtime en deze niet wijzigen. Zo kan het bijvoorbeeld geen bestanden uitpakken `jar` of `tar` uitpakken.

## Geen streamingbinaries via AEM als cloudservice {#no-streaming-binaries}

De binaire getallen zouden door CDN moeten worden betreden, die binaire getallen buiten de kernAEM diensten zal dienen.

Gebruik bijvoorbeeld niet `asset.getOriginal().getStream()`, waardoor het downloaden van een binair getal naar de vaste schijf van de AEM-service wordt geactiveerd.

## Geen reverse Replication-agents {#no-reverse-replication-agents}

De omgekeerde replicatie van Publiceren naar Auteur wordt niet ondersteund in AEM als Cloud Service. Als een dergelijke strategie nodig is, kunt u een externe persistentieopslag gebruiken die onder het landbouwbedrijf van Publish instanties en potentieel de cluster van de Auteur wordt gedeeld.

## De voorwaartse Medewerkers van de Replicatie zouden kunnen moeten worden gesteund {#forward-replication-agents}

Inhoud wordt van Auteur naar Publiceren gerepliceerd via een submechanisme. Aangepaste replicatiemiddelen worden niet ondersteund.

## Controle en foutopsporing {#monitoring-and-debugging}

### Logboeken {#logs}

Voor lokale ontwikkeling worden logbestandvermeldingen naar lokale bestanden in de `/crx-quickstart/logs` map geschreven.

In cloudomgevingen kunnen ontwikkelaars logbestanden downloaden via Cloud Manager of een opdrachtregelprogramma gebruiken om de logbestanden vast te zetten. <!-- See the [Cloud Manager documentation](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->

**Logniveau instellen**

Om de logboekniveaus voor de milieu&#39;s van de Wolk te veranderen, zou de het Registreren van de Sling configuratie OSGI moeten worden gewijzigd, gevolgd door een volledige herplaatsing. Aangezien dit niet onmiddellijk is, ben voorzichtig om uitgebreide logboeken op productiemilieu&#39;s toe te laten die veel verkeer ontvangen. In de toekomst is het mogelijk dat er mechanismen zijn om het logniveau sneller te wijzigen.

>[!NOTE]
>
>Om de hieronder vermelde configuratieveranderingen uit te voeren, moet u hen op een lokale ontwikkelomgeving tot stand brengen en dan hen duwen aan een AEM als instantie van de Dienst van de Wolk. Zie [Distribueren naar AEM als Cloud Service](/help/implementing/deploying/overview.md)voor meer informatie over hoe u dit kunt doen.

**Het FOUTOPSPORINGSlogniveau activeren**

Het standaardlogboekniveau is INFO, dat wil zeggen, worden de DEBUG- berichten niet geregistreerd.
Als u het niveau van het FOUTOPSPORINGSlogbestand wilt activeren, stelt u de optie

``` /libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level ```

eigenschap voor foutopsporing. Verlaat het logboek bij het DEBUG logboekniveau niet langer dan nodig, aangezien het veel logboeken produceert.
Een lijn in zuivert dossier begint gewoonlijk met DEBUG, en verstrekt dan het logboekniveau, de installeractie en het logboekbericht. Bijvoorbeeld:

``` DEBUG 3 WebApp Panel: WebApp successfully deployed ```

De logniveaus zijn als volgt:

| 0 | Fatale fout | De handeling is mislukt en het installatieprogramma kan niet doorgaan. |
|---|---|---|
| 1 | Fout | De handeling is mislukt. De installatie gaat door, maar een deel van CRX is niet correct geïnstalleerd en werkt niet. |
| 2 | Waarschuwing | De actie is geslaagd maar heeft problemen ondervonden. CRX werkt mogelijk niet correct. |
| 3 | Informatie | De actie is geslaagd. |

### Thread Dumps {#thread-dumps}

Thread dumps op Cloud-omgevingen worden voortdurend verzameld, maar kunnen op dit moment niet op een zelfserverende manier worden gedownload. Ondertussen, gelieve te contacteren AEM steun als de draaddumps voor het zuiveren van een kwestie nodig zijn, specificerend het nauwkeurige tijdvenster.

## CRX/DE Lite en de Console van het Systeem {#crxde-lite-and-system-console}

### Lokale ontwikkeling {#local-development}

Voor lokale ontwikkeling hebben ontwikkelaars volledige toegang tot CRXDE Lite (`/crx/de`) en de AEM Webconsole (`/system/console`).

Let op: bij lokale ontwikkeling (met gebruik van de snelstartprocedure voor de cloud) `/apps` en `/libs` kan rechtstreeks naar deze map worden geschreven. Dit is anders dan in cloudomgevingen waar deze mappen op hoofdniveau onveranderbaar zijn.

### AEM as a Cloud Service Development tools {#aem-as-a-cloud-service-development-tools}

Klanten hebben toegang tot CRXDE-site in de ontwikkelomgeving, maar niet tot het stadium of de productie. Er kan niet naar de onveranderlijke opslagplaats (`/libs`, `/apps`) worden geschreven bij uitvoering, zodat dit tot fouten leidt.

In de Developer Console for dev, stage, and production environment is een set tools beschikbaar voor foutopsporing in AEM als een Cloud Service Developer-omgeving. De URL kan worden bepaald door de URL van de service Auteur of Publiceren als volgt aan te passen:

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

Als kortere weg, kan het volgende CLI bevel van de Manager van de Wolk worden gebruikt om de ontwikkelaarsconsole te lanceren die op een milieuparameter wordt gebaseerd die hieronder wordt beschreven:

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

Zie [deze pagina](/help/release-notes/home.md) voor meer informatie.

Ontwikkelaars kunnen statusinformatie genereren en diverse bronnen oplossen.

Zoals hieronder wordt geïllustreerd, omvat de beschikbare statusinformatie de staat van bundels, componenten, configuraties OSGI, eikenindexen, diensten OSGI, en het Sling banen.

![Dev Console 1](/help/implementing/developing/introduction/assets/devconsole1.png)

Zoals hieronder geïllustreerd, kunnen de ontwikkelaars pakketgebiedsdelen en servlets oplossen:

![Dev Console 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![Dev Console 3](/help/implementing/developing/introduction/assets/devconsole3.png)

Ook nuttig voor het zuiveren, heeft de console van de Ontwikkelaar een verbinding aan het Uitleg hulpmiddel van de Vraag:

![Dev Console 4](/help/implementing/developing/introduction/assets/devconsole4.png)

### AEM Staging- en productieservice {#aem-staging-and-production-service}

Klanten hebben geen toegang tot ontwikkelaarstools voor testomgevingen en productieomgevingen.

### Prestatiebewaking {#performance-monitoring}

Adobe bewaakt de prestaties van de toepassing en neemt maatregelen om verslechtering te verhelpen. Op dit moment kunnen maatgegevens van toepassingen niet worden nageleefd.