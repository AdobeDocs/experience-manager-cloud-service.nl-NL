---
title: Inhoudsverzoeken van Cloud Servicen begrijpen
description: Als u licenties voor inhoudsaanvragen van Adobe hebt aangeschaft, leert u meer over de typen inhoudsaanvragen die Adobe Experience Cloud als een service meet en over de verschillen met de analytische rapportagehulpprogramma's van een organisatie.
source-git-commit: e34b21194e35b2f56dd1e7df2165c3fa5c0cb7da
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 0%

---


# Verzoeken om Cloud Service-inhoud

## Variaties in aanvragen voor inhoud van Cloud Servicen{#content-requests-variances}

De Verzoeken van de inhoud kunnen variaties met Analytics van een organisatie hebben rapporteringshulpmiddelen zoals samengevat in de volgende lijst. In het algemeen, hulpmiddelen van de Analyse die gegevens via cliënt-zijinstrumentatie verzamelen <b>mag niet worden gebruikt</b> rapporteren over het aantal inhoudsaanvragen voor een bepaalde site, simpelweg omdat deze vaak afhankelijk zijn van de toestemming van de eindgebruiker om in werking te treden, waardoor ze ontbreken op een aanzienlijk deel van het verkeer. De hulpmiddelen van de analyse die gegevensserver-kant in logboekdossiers verzamelen, of CDN- rapporten voor klanten die hun eigen CDN bovenop AEM as a Cloud Service toevoegen, zullen betere tellingen verstrekken. Voor het melden van paginaweergaven en de bijbehorende prestaties is de Adobe RUM Data Service de aanbevolen optie voor de Adobe.

| Reden voor variantie | Toelichting |
|---|---|
| Goedkeuring eindgebruiker | Analytische hulpmiddelen die afhankelijk zijn van instrumentvermelding aan de clientzijde zijn vaak afhankelijk van de toestemming van de eindgebruiker om te worden geactiveerd. Dit zou de meerderheid van het verkeer kunnen vertegenwoordigen dat niet wordt gevolgd. Voor klanten die inhoudsverzoeken op hun willen meten, wordt het geadviseerd om zich op analysehulpmiddelen te baseren die gegevensserver-kant of CDN- rapporten verzamelen. |
| Tags | Alle pagina&#39;s of API-aanroepen die worden bijgehouden als Adobe Experience Manager-inhoudsaanvragen (AEM), worden mogelijk niet gelabeld met Analytics tracking. |
| Tag Management-regels | Instellingen voor regels voor het beheer van tags kunnen leiden tot verschillende configuraties voor gegevensverzameling op een pagina. Dit leidt tot enige combinatie van verschillen met het bijhouden van de inhoudsaanvraag. |
| Bots | Onbekende bots die niet vooraf zijn geïdentificeerd en door AEM zijn verwijderd, kunnen verschillen in het bijhouden van gegevens veroorzaken. |
| Rapportageopties | Pagina&#39;s die deel uitmaken van hetzelfde AEM exemplaar en domein, kunnen gegevens naar verschillende analytische rapportsuites verzenden. |
| Instrumenten voor toezicht en beveiliging van derden | Met de hulpprogramma&#39;s voor controle en beveiligingsscans kunt u verzoeken om inhoud genereren voor AEM die niet worden bijgehouden in analytische rapporten. |
| API-toegang | Programmatische toegang tot pagina&#39;s of tot Adobe Experience Manager API&#39;s kan inhoudsverzoeken voor AEM genereren die niet worden bijgehouden in analyserapporten. |
| Prefetverzoeken | Als u een prefetch-service gebruikt om pagina&#39;s vooraf te laden om de snelheid te verhogen, kan dit leiden tot aanzienlijke toename van het verkeer van inhoudsverzoeken. |
| DDOS | Terwijl de Adobe al het mogelijke doet om verkeer van aanvallen DDOS automatisch te ontdekken en uit te filtreren, is er geen garantie dat alle mogelijke aanvallen DDOS worden ontdekt |
| Verkeersblokkers | Als u een tracker-blokker in een browser gebruikt, kunnen sommige aanvragen niet worden bijgehouden. |
| Firewalls | Firewalls kunnen het bijhouden van analyses blokkeren. Dit scenario komt vaker voor bij bedrijfsfirewalls. |

Zie ook [Licentiedashboard](/help/implementing/cloud-manager/license-dashboard.md).

## Inhoudsverzoeken van Cloud Servicen begrijpen {#about-content-request}

Inhoudsverzoeken worden automatisch bijgehouden aan de rand van de as a Cloud Service Adobe Experience Manager (AEM), via geautomatiseerde analyse van de logbestanden die afkomstig zijn van de AEM as a Cloud Service CDN, waarbij de aanvragen die HTML (text/html) of JSON (application/json) inhoud retourneren, van de CDN worden geïsoleerd en op basis van een aantal hieronder beschreven opname- en uitsluitingsregels. Een inhoudsverzoek gebeurt onafhankelijk van de teruggekeerde inhoud die van CDN caches wordt gediend of die terug naar de oorsprong van CDN (AEM verzenders) gaat.

Voor klanten die hun eigen CDN bovenop AEM as a Cloud Service brengen, zal dit volgen in aantallen resulteren die niet kunnen worden gebruikt om met de vergunning gegeven inhoudsverzoeken te vergelijken, die door de klant bij de rand van buitenste CDN zullen moeten worden gemeten.

Er bestaan regels om bekende bots uit te sluiten, waaronder bekende services die regelmatig de site bezoeken om hun zoekindex of service te vernieuwen.

### Typen opgenomen inhoudsaanvragen{#included-content-requests}

| Type aanvraag | Content Request | Beschrijving |
| --- | --- | --- |
| HTTP-code 100-299 | Opgenomen | Dit zijn regelmatige verzoeken die alle of gedeeltelijke inhoud leveren. |
| HTTP-bibliotheken voor automatisering | Opgenomen | Voorbeelden:<br>Amazon CloudFront<br>Apache Http Client<br>・ Asynchrone HTTP-client<br>Axios<br>Azureus<br>・ Curl<br>・ GitHub Node Fetch<br>・ Guzzle<br>・ Go-http-client<br>・ Hoofdloze chroom<br>・ Java™-client<br>Jersey<br>・ Node Oembed<br>・ okhttp<br>Python-verzoeken<br>・ Reactor-netwerk<br>・ Wget<br>WinHTTP |
| Gereedschappen voor toezicht en gezondheidscontrole | Opgenomen | Deze worden opgezet door de klant om een bepaald aspect van de plaats te controleren. Bijvoorbeeld beschikbaarheid of real-world gebruikersprestaties. Gebruiken `/system/probes/health` en niet de daadwerkelijke HTML pagina&#39;s van de plaats.<br>Voorbeelden:<br>・ Amazon-Route53-Health-Check-Service<br>・ EyeMonIT_bot_version_0.1_[https://www.eyemon.it/)](https://www.eyemon.it/)<br>・ Investis-Site24x7<br>・ Mozilla/5.0+(compatibel; UptimeRobot/2.0; [https://uptimerobot.com/](https://uptimerobot.com/))<br>・ ThousandEyes-Dragonfly-x1<br>OmtrBot/1.0<br>・ WebMon/2.0.0 |
| `<link rel="prefetch">` verzoeken | Opgenomen | Om de snelheid van het laden van de volgende pagina te verhogen, kunnen klanten browser een reeks pagina&#39;s hebben laden alvorens de gebruiker verbinding-zodat zij reeds in het geheime voorgeheugen zijn. *Mind: Dit verhoogt het verkeer aanzienlijk*—afhankelijk van het aantal van deze pagina&#39;s dat vooraf is ingesteld. |
| Het verkeer dat Adobe Analytics of Googles Analytics het melden blokkeert | Opgenomen | Het is meer gebruikelijk dat bezoekers van sites privacysoftware (Ad-blockers, enzovoort) hebben geïnstalleerd die van invloed is op de nauwkeurigheid van Googles Analytics of Adobe Analytics. AEM verzoeken om as a Cloud Service tellingen op het eerste ingangspunt in de door de Adobe beheerde infrastructuur en niet aan de clientzijde. |

Zie ook [Licentiedashboard](/help/implementing/cloud-manager/license-dashboard.md).

### Typen verzoeken om uitgesloten inhoud{#excluded-content-request}

| Type aanvraag | Content Request | Beschrijving |
| --- | --- | --- |
| HTTP-code 500+ | Uitgesloten | Fouten die aan de bezoeker zijn geretourneerd wanneer er iets mis gaat met AEM as a Cloud Service of aangepaste code van de klant. |
| HTTP-code 400-499 | Uitgesloten | Fouten die aan de bezoeker zijn geretourneerd wanneer de inhoud niet bestaat (404) of wanneer er andere problemen zijn met inhoud of verzoeken. |
| HTTP-code 300-399 | Uitgesloten | Dit zijn goede verzoeken die of controleren of iets op de server is veranderd, of het verzoek aan een andere middel opnieuw richten. Ze bevatten geen inhoud op zich en kunnen daarom niet worden gefactureerd. |
| Verzoeken naar /libs/* | Uitgesloten | AEM interne JSON-aanvragen, zoals de CSRF-token die niet kan worden opgevraagd. |
| Verkeer van aanvallen DDOS | Uitgesloten | DDOS-bescherming. AEM detecteert sommige DDOS-aanvallen automatisch en blokkeert deze. DDOS-aanvallen indien gedetecteerd, kunnen niet worden opgeladen.<br><br>Automatisch gedetecteerde DDOS-typen:<br>・ DDOSBlockedCiphersSHA<br>・ DDOSBlockedPattern<br>・ DDOSSuspiciousRequest |
| AEM as a Cloud Service NewRelic Monitoring | Uitgesloten | AEM as a Cloud Service wereldwijde monitoring. |
| URL voor klanten om hun programma van de Cloud Service te controleren | Uitgesloten | Aanbevolen URL om de beschikbaarheid extern te controleren.<br><br>`/system/probes/health` |
| as a Cloud Service pod Warm-up service AEM | Uitgesloten | Gebruikersagent: skyline-service-warmup/1.* |
| Bekende zoekmachines, sociale netwerken en HTTP-bibliotheken (getagd door Snelst) | Uitgesloten | De bekende diensten die de plaats regelmatig bezoeken om hun onderzoeksindex of de dienst te verfrissen:<br><br>Voorbeelden:<br>・ AddSearchBot<br>AhrefsBot<br>Applebot<br>・ Vraag Jeeves Corporate Spider<br>Bingbot<br>・ BingPreview<br>・ BLEXBot<br>・ BuiltWith<br>Bytespider<br>CrawlerKengo<br>Facebook externalhit<br>Google AdsBot<br>・ Google AdsBot Mobile<br>Googlebot<br>Googlebot Mobile<br>lmspider<br>・ LucidWorks<br>MJ12bot<br>・ VK<br>pinterest<br>・ SemspitseBot<br>・ SiteImproved<br>・ StashBot<br>・ StatusCake<br>YandexBot |
| Commerce integration framework-aanroepen uitsluiten | Uitgesloten | Dit zijn verzoeken aan AEM die door:sturen aan het Commerce integration framework-URL begint met `/api/graphql`—om dubbeltellingen te voorkomen, kunnen zij niet voor Cloud Service in rekening worden gebracht. |
| Uitsluiten `manifest.json` | Uitgesloten | Manifest is geen API-aanroep. Het is hier om informatie op te geven over het installeren van websites op computers of mobiele telefoons. Adobe mag JSON-verzoek niet tellen voor `/etc.clientlibs/*/manifest.json` |
| Uitsluiten `favicon.ico` | Uitgesloten | Terwijl de teruggekeerde inhoud niet HTML of JSON zou moeten zijn, zien wij dat in sommige scenario&#39;s zoals de authentificatiestromen van SAML, de favicons kunnen zijn teruggekeerd aangezien HTML daarom uitdrukkelijk van de telling wordt uitgesloten. |


