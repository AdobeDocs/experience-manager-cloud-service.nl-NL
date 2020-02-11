---
title: AEM als richtlijnen voor de ontwikkeling van cloudservices
description: 'In te vullen '
translation-type: tm+mt
source-git-commit: 13c0a670330532f574c2b38823b8a924c609e8e4

---


# AEM als richtlijnen voor de ontwikkeling van cloudservices {#aem-as-a-cloud-service-development-guidelines}

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
* [OK Http](OK Http (niet verstrekt door AEM)) (Niet verstrekt door AEM)

## Controle en foutopsporing {#monitoring-and-debugging}

### Logboeken {#logs}

* Voor lokale ontwikkeling worden logbestandvermeldingen geschreven naar lokale bestanden
   * `./crx-quickstart/logs`
* In cloudomgevingen kunnen ontwikkelaars logbestanden downloaden via Cloud Manager of een opdrachtregelprogramma gebruiken om de logbestanden vast te zetten. <!-- See the [Cloud Manager documentation](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->
* Om de logboekniveaus voor de milieu&#39;s van de Wolk te veranderen, zou de het Registreren van de Sling configuratie OSGI moeten worden gewijzigd, gevolgd door een volledige herplaatsing. Aangezien dit niet onmiddellijk is, ben voorzichtig om uitgebreide logboeken op productiemilieu&#39;s toe te laten die veel verkeer ontvangen. In de toekomst is het mogelijk dat er mechanismen zijn om het logniveau sneller te wijzigen.

### Thread Dumps {#thread-dumps}

Thread dumps op Cloud-omgevingen worden voortdurend verzameld, maar kunnen op dit moment niet op een zelfserverende manier worden gedownload. Ondertussen, gelieve te contacteren AEM steun als de draaddumps voor het zuiveren van een kwestie nodig zijn, specificerend het nauwkeurige tijdvenster.

### CRX/DE Lite en de Console van het Systeem {#crxde-lite-and-system-console}

## Lokale ontwikkeling {#local-development}

Voor lokale ontwikkeling hebben ontwikkelaars volledige toegang tot CRXDE Lite (`/crx/de`) en de AEM Webconsole (`/system/console`).

Let op: bij lokale ontwikkeling (met gebruik van de snelstartprocedure voor de cloud) `/apps` en `/libs` kan rechtstreeks naar deze map worden geschreven. Dit is anders dan in cloudomgevingen waar deze mappen op hoofdniveau onveranderbaar zijn.

## AEM als ontwikkelingsprogramma&#39;s voor cloudservices {#aem-as-a-cloud-service-development-tools}

Klanten hebben toegang tot CRXDE-site in de ontwikkelomgeving, maar niet tot het stadium of de productie. Er kan niet naar de onveranderlijke opslagplaats (`/libs`, `/apps`) worden geschreven bij uitvoering, zodat dit tot fouten leidt.

In de Developer Console for dev, stage, and production environment is een set tools beschikbaar voor foutopsporing in AEM als een Cloud Service Developer-omgeving. De URL kan als volgt worden bepaald door de URL van de auteur of de publicatieservice aan te passen:

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

**AEM Staging- en productieservice**

Klanten hebben geen toegang tot ontwikkelaarstools voor testomgevingen en productieomgevingen.

### Diagnostiek {#diagnostics}

Systeemconsole is beschikbaar voor ontwikkelomgevingen. Er zijn echter geen diagnostische dumpen voor het opvoeren en produceren beschikbaar.