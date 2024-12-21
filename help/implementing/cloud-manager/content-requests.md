---
title: Verzoeken om Cloud Service-inhoud begrijpen
description: Als u licenties voor inhoudsaanvragen van Adobe hebt aangeschaft, leert u meer over de typen inhoudsaanvragen die Adobe Experience Cloud als een service meet en over de verschillen met de analytische rapportagehulpprogramma's van een organisatie.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 18d19acfedce57a3ae52020d36785689b715ed08
workflow-type: tm+mt
source-wordcount: '1249'
ht-degree: 0%

---

# Inhoudsverzoeken voor Cloud Service begrijpen

## Inleiding {#introduction}

Inhoudsverzoeken hebben betrekking op verzoeken die aan AEM Sites zijn gedaan, waaronder verzoeken met betrekking tot Edge Delivery Services of door de klant geleverde caching-systemen zoals een Content Delivery Network. Deze verzoeken leveren inhoud of gegevens in HTML formaat door paginameningen (bijvoorbeeld, pagina&#39;s en de Fragmenten van de Ervaring) of in formaat JSON door API vraag op een headless manier. Inhoudsverzoeken worden geteld als een paginaweergave of vijf API-aanroepen en worden gemeten bij de ingang van het eerste cachesysteem dat een inhoudsverzoek ontvangt. Bepaalde HTTP-aanvragen worden opgenomen of uitgesloten voor het tellen van inhoudsaanvragen. De volledige lijst van dergelijke opgenomen en uitgesloten HTTP-aanvragen en de technische definities daarvan zijn beschikbaar in de documentatie.

## Over verzoeken om Cloud Service-inhoud {#understanding-cloud-service-content-requests}

Voor klanten die uit-van-de-doos CDN gebruiken, worden de de inhoudsverzoeken van de Cloud Service gemeten via server-zijinzameling van gegevens. Deze inzameling wordt toegelaten via CDN logboekanalyse. AEM (Adobe Experience Manager) verzamelt inhoud automatisch op de server bij de rand. Hiermee worden logbestanden geanalyseerd die zijn gegenereerd door de AEM as a Cloud Service CDN. Dit proces wordt uitgevoerd door de aanvragen die HTML `(text/html)` - of JSON `(application/json)` -inhoud retourneren, te isoleren van de CDN en is gebaseerd op verschillende hieronder beschreven insluitings- en uitsluitingsregels. Een inhoudsverzoek komt ongeacht voor of de inhoud van het geheime voorgeheugen CDN wordt gediend of aan de oorsprong CDN (AEM verzenders) teruggekeerd.

<!-- REMOVED AS PER EMAIL REQUEST FROM SHWETA DUA, JULY 30, 2024 TO RICK BROUGH AND ALEXANDRU SARCHIZ   For customers employing their own CDN, client-side collection offers a more precise reflection of interactions, ensuring a reliable measure of website engagement via the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) service. This gives customers advanced insights into their page traffic and performance. While it is beneficial for all customers, it offers a representative reflection of user interactions, ensuring a reliable measure of website engagement by capturing the number of page views from the client side. 

For customers that bring their own CDN on top of AEM as a Cloud Service, server-side reporting results in numbers that cannot be used to compare with the licensed content requests. With the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md), Adobe can reflect a reliable measure of website engagement. -->

### Variaties in aanvragen voor inhoud van Cloud Service {#content-requests-variances}

Inhoudsverzoeken kunnen variaties hebben binnen de rapportagehulpprogramma&#39;s voor Analytics van een organisatie, zoals wordt samengevat in de volgende tabel. In het algemeen geldt dat u geen analyseprogramma&#39;s moet gebruiken die afhankelijk zijn van instrumenten aan de clientzijde om het aantal aanvragen voor inhoud voor een site te melden. Deze hulpmiddelen missen vaak een groot deel van verkeer omdat zij van gebruikerstoestemming afhangen om worden geactiveerd. De hulpmiddelen van de analyse die gegevensserver-kant in logboekdossiers verzamelen, of CDN- rapporten voor klanten die hun eigen CDN bovenop AEM as a Cloud Service toevoegen, verstrekken betere tellingen.

| Reden voor variantie | Toelichting |
|---|---|
| Goedkeuring eindgebruiker | Analysemiddelen die afhankelijk zijn van instrumenten aan de clientzijde zijn vaak afhankelijk van de toestemming van de gebruiker om te worden geactiveerd. Dit werkschema kon het grootste deel van het verkeer vertegenwoordigen dat niet wordt gevolgd. Voor klanten die inhoudsverzoeken op hun willen meten, wordt het geadviseerd om zich op analysehulpmiddelen te baseren die gegevensserver-kant of CDN- rapporten verzamelen. |
| Tags | Alle pagina&#39;s of API-aanroepen die als Adobe Experience Manager-inhoudsaanvragen worden bijgehouden, worden mogelijk niet gelabeld met Analytics tracking. |
| Tag Management-regels | Instellingen voor regels voor het beheer van tags kunnen leiden tot verschillende configuraties voor gegevensverzameling op een pagina. Dit leidt tot enige combinatie van verschillen met het bijhouden van de inhoudsaanvraag. |
| Bots | Onbekende bots die AEM niet vooraf geïdentificeerd en verwijderd heeft, kunnen afwijkingen bij het bijhouden van gegevens veroorzaken. |
| Rapportageopties | Pagina&#39;s die deel uitmaken van hetzelfde AEM exemplaar en domein, kunnen gegevens naar verschillende analytische rapportsuites verzenden. |
| Instrumenten voor toezicht en beveiliging van derden | Met de hulpprogramma&#39;s voor controle en beveiligingsscans kunt u verzoeken om inhoud genereren voor AEM die niet worden bijgehouden in analytische rapporten. |
| API-toegang | Programmatische toegang tot pagina&#39;s of tot Adobe Experience Manager API&#39;s kan inhoudsverzoeken voor AEM genereren die niet worden bijgehouden in analyserapporten. |
| Prefetverzoeken | Als u een prefetch-service gebruikt om pagina&#39;s vooraf te laden om de snelheid te verhogen, kan dit leiden tot aanzienlijke toename van het verkeer van inhoudsverzoeken. |
| DDOS | Terwijl de Adobe pogingen doet om verkeer van aanvallen automatisch van DDOS te ontdekken en uit te filtreren, is er geen garantie dat alle mogelijke aanvallen DDOS worden ontdekt. |
| Verkeersblokkers | Als u een tracker-blokker in een browser gebruikt, kunnen sommige aanvragen niet worden bijgehouden. |
| Firewalls | Firewalls kunnen het bijhouden van analyses blokkeren. Dit scenario komt vaker voor bij bedrijfsfirewalls. |

Zie ook [ Dashboard van de Vergunning ](/help/implementing/cloud-manager/license-dashboard.md).

## Regels voor verzamelingen op de server {#serverside-collection}

Er bestaan regels om bekende bots uit te sluiten, waaronder bekende services die regelmatig de site bezoeken om hun zoekindex of service te vernieuwen.

### Typen opgenomen inhoudsaanvragen {#included-content-requests}

| Type aanvraag | Content Request | Beschrijving |
| --- | --- | --- |
| HTTP-code 100-299 | Opgenomen | Gewone verzoeken die alle of gedeeltelijke inhoud leveren. |
| HTTP-bibliotheken voor automatisering | Opgenomen | Voorbeelden:<br>・ Amazon CloudFront <br>・ Apache HTTP Client <br>・ Asynchrone HTTP Client <br>・ Axios <br>・ Azureus <br>・ Curl <br>・ GitHub Node Fetch <br>・ Guzzle <br>・ Go-http-client <br>・ Headless Chrome <br>・ Java™ Client <br> ・ Jersey <br>・ Node Oembed <br>・ okhttp <br>・ Python-verzoeken <br>・ Reactor Netty <br>・ Wget <br>・ WinHTTP <br>・ Fast HTTP <br>・ GitHub Node Fetch <br>・ Reactor Netty |
| Gereedschappen voor toezicht en gezondheidscontrole | Opgenomen | Instellen door de klant om een bepaald aspect van de site te controleren. Bijvoorbeeld beschikbaarheid of real-world gebruikersprestaties. Als deze zich richten op specifieke eindpunten zoals `/system/probes/health` voor gezondheidscontroles, raadt de Adobe u aan het `/system/probes/health` -eindpunt te gebruiken en niet de feitelijke HTML-pagina&#39;s van de site. [ zie hieronder ](#excluded-content-request)<br> Voorbeelden:<br>・ `Amazon-Route53-Health-Check-Service`<br>・ EyeMonIT_bot_version_0.1_ [ (https://eyemonit.com/) ](https://eyemonit.com/) <br>・ Investis-Site24x7 <br>・ Mozilla/5.0+ (compatibel; UptimeRobot/2.0; [ https://uptimerobot.com/ ](https://uptimerobot.com/)) <br>・ Thousand Eyes-Dragonfly-x1 <br>・ OmtrBot/1.0 <br>・ WebMon/2.0.0 |
| `<link rel="prefetch">` aanvragen | Opgenomen | Om de snelheid van het laden van de volgende pagina te verhogen, kunnen klanten browser een reeks pagina&#39;s hebben laden alvorens de gebruiker verbinding-zodat zij reeds in het geheime voorgeheugen zijn. *Gedacht: Deze benadering verhoogt beduidend het verkeer* - afhankelijk van hoeveel van deze pagina&#39;s vooraf ingesteld zijn. |
| Het verkeer dat Adobe Analytics of Googles Analytics het melden blokkeert | Opgenomen | Het is meer gebruikelijk dat bezoekers van sites privacysoftware (Ad-blockers, enzovoort) hebben geïnstalleerd die van invloed is op de nauwkeurigheid van Googles Analytics of Adobe Analytics. AEM as a Cloud Service telt verzoeken op het eerste ingangspunt in de door de Adobe beheerde infrastructuur en niet op de client. |

Zie ook [ Dashboard van de Vergunning ](/help/implementing/cloud-manager/license-dashboard.md).

### Typen verzoeken om uitgesloten inhoud {#excluded-content-request}

| Type aanvraag | Content Request | Beschrijving |
| --- | --- | --- |
| HTTP-code 500+ | Uitgesloten | Fouten die aan de bezoeker zijn geretourneerd wanneer er iets verkeerd gaat op AEM as a Cloud Service of de aangepaste code van de klant. |
| HTTP-code 400-499 | Uitgesloten | Fouten die aan de bezoeker zijn geretourneerd wanneer de inhoud niet bestaat (404) of wanneer er andere problemen zijn met inhoud of verzoeken. |
| HTTP-code 300-399 | Uitgesloten | De goede verzoeken dat of controleren of iets op de server is veranderd, of het verzoek aan een andere middel opnieuw richten. Ze bevatten geen inhoud op zich en kunnen daarom niet worden gefactureerd. |
| Verzoeken naar /libs/* | Uitgesloten | AEM interne JSON-aanvragen, zoals de CSRF-token die niet kan worden opgevraagd. |
| Verkeer van aanvallen DDOS | Uitgesloten | DDOS-bescherming. AEM detecteert sommige DDOS-aanvallen automatisch en blokkeert deze. DDOS-aanvallen indien gedetecteerd, kunnen niet worden opgeladen. |
| AEM as a Cloud Service New Relic Monitoring | Uitgesloten | AEM as a Cloud Service global monitoring. |
| URL voor klanten om hun programma van de Cloud Service te controleren | Uitgesloten | De Adobe adviseert dat u URL gebruikt om de beschikbaarheid of de gezondheidscontrole extern te controleren.<br><br>`/system/probes/health` |
| AEM as a Cloud Service Pod Warm-up Service | Uitgesloten |
| Agent: skyline-service-warmup/1.* |
| Bekende zoekmachines, sociale netwerken en HTTP-bibliotheken (getagd door Snelst) | Uitgesloten | De bekende diensten die de plaats regelmatig bezoeken om hun onderzoeksindex of de dienst te verfrissen:<br><br> Voorbeelden:<br>・ AddSearchBot <br>・ AhrefsBot <br>・ Applebot <br>・ Vraag Jeeves Corporate Spider <br>・ Bingbot <br>・ BingPreview <br>・ BLEXBot <br>・ BouwtWith <br> <br>・ CrawlerKengo <br>・ Facebookexternalhit <br>・ Google AdsBot <br>・ Google AdsBot Mobile <br>・ Googlebot <br>・ Googlebot Mobile <br>・ lmspin <br>・ LucidWorks <br>・ `MJ12bot`<br> Pinterest <br>・ SembrushBot <br>・ SiteImproved <br>・ StashBot <br>・ StatusCake <br>・ YandexBot <br>・ Claudebot |
| Commerce integration framework-aanroepen uitsluiten | Uitgesloten | Verzoeken die zijn gemaakt voor AEM die worden doorgestuurd naar het Commerce integration framework—de URL begint met `/api/graphql`—om dubbeltellingen te voorkomen, kunnen niet worden doorberekend voor Cloud Service. |
| Uitsluiten `manifest.json` | Uitgesloten | Manifest is geen API-oproep. Hier vindt u informatie over het installeren van websites op een desktopcomputer of mobiele telefoon. Adobe mag JSON-aanvraag niet tellen naar `/etc.clientlibs/*/manifest.json` |
| Uitsluiten `favicon.ico` | Uitgesloten | Hoewel de teruggekeerde inhoud niet HTML of JSON zou moeten zijn, zijn bepaalde scenario&#39;s zoals de authentificatiestromen van SAML waargenomen om favicons als HTML terug te keren. Dientengevolge, worden de favicons uitdrukkelijk uitgesloten van de telling. |
