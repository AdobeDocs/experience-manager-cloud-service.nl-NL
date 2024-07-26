---
title: Inhoudsverzoeken van Cloud Servicen begrijpen
description: Als u licenties voor inhoudsaanvragen van Adobe hebt aangeschaft, leert u meer over de typen inhoudsaanvragen die Adobe Experience Cloud als een service meet en over de verschillen met de analytische rapportagehulpprogramma's van een organisatie.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: af2985f29cb867162061bbac465b19637aa0ecad
workflow-type: tm+mt
source-wordcount: '1405'
ht-degree: 0%

---

# Verzoeken om Cloud Service-inhoud

## Inleiding {#introduction}

Inhoudsverzoeken zijn aanvragen die in AEM Sites (inclusief in verband met Edge Delivery Services voor AEM Sites) of een door de klant beschikbaar cachesysteem (zoals een Content Delivery Network) worden ingediend om inhoud of gegevens in HTML-indeling via paginaweergaven (bijvoorbeeld pagina&#39;s en ervaringsfragmenten) of in JSON-indeling via API-aanroepen (zonder kop) te leveren. De verzoeken van de inhoud worden of als paginamening of 5 API Vraag geteld, en bij de ingang van het eerste caching systeem gemeten om een inhoudsverzoek te ontvangen. Bepaalde HTTP-aanvragen worden opgenomen of uitgesloten voor het tellen van inhoudsaanvragen. De volledige lijst van dergelijke opgenomen en uitgesloten HTTP-aanvragen en de technische definities daarvan zijn beschikbaar in de documentatie.

## Inhoudsverzoeken van Cloud Servicen begrijpen {#understanding-cloud-service-content-requests}

Voor klanten die uit-van-de-doos CDN gebruiken, worden de de inhoudsverzoeken van de Cloud Service gemeten via server-zijinzameling van gegevens. Deze inzameling wordt toegelaten via CDN logboekanalyse. Aanvragen voor inhoud worden automatisch op de server aan de rand van Adobe Experience Manager as a Cloud Service verzameld, via automatische analyse van de logbestanden die afkomstig zijn van AEM as a Cloud Service CDN. Hiervoor isoleert u de aanvragen die HTML `(text/html)` - of JSON `(application/json)` -inhoud retourneren van de CDN en is de CDN-naam gebaseerd op verschillende hieronder beschreven insluitings- en uitsluitingsregels. Een inhoudsverzoek komt onafhankelijk van de teruggekeerde inhoud voor die van CDN caches wordt gediend of de inhoud die terug naar de oorsprong van CDN (AEM verzenders) gaat.

Voor klanten die hun eigen CDN gebruiken, biedt de cliënt-zijinzameling een nauwkeurigere bezinning van interactie aan, die een betrouwbare maatregel van websiteovereenkomst door de [ Echte dienst van de Controle van het Gebruik ](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) verzekeren. Dit geeft klanten geavanceerde inzichten in hun paginaverkeer en prestaties. Hoewel deze service alle klanten ten goede komt, biedt deze een representatieve weergave van gebruikersinteracties, zodat een betrouwbare mate van betrokkenheid van websites wordt gewaarborgd door het aantal paginaweergaven van de zijde van de client vast te leggen.

Voor klanten die hun eigen CDN bovenop AEM as a Cloud Service brengen, leidt de server-zijrapportering in aantallen die niet kunnen worden gebruikt om met de vergunning gegeven inhoudsverzoeken te vergelijken. Met de [ Echte Controle van het Gebruik ](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md), kan de Adobe op een betrouwbare maatregel van websiteovereenkomst wijzen.


### Variaties in aanvragen voor inhoud van Cloud Servicen {#content-requests-variances}

De verzoeken van de inhoud kunnen variaties binnen de analytische rapporteringshulpmiddelen van een organisatie zoals samengevat in de volgende lijst hebben. In het algemeen, *gebruiken geen* analysehulpmiddelen die gegevens als cliënt-zijinstrumentatie verzamelen om over het aantal inhoudverzoeken voor een bepaalde plaats te rapporteren, eenvoudig omdat zij vaak van gebruikerstoestemming afhangen om worden teweeggebracht, daarom ontbrekend een significante fractie van het verkeer. De hulpmiddelen van de analyse die gegevensserver-kant in logboekdossiers verzamelen, of CDN- rapporten voor klanten die hun eigen CDN bovenop AEM as a Cloud Service toevoegen, zullen betere tellingen verstrekken. Voor het melden van paginameningen en hun bijbehorende prestaties, is de [ Dienst van de Gegevens van de Adobe RUM ](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) de Adobe geadviseerde optie.

| Reden voor variantie | Toelichting |
|---|---|
| Goedkeuring eindgebruiker | Analysemiddelen die afhankelijk zijn van instrumenten aan de clientzijde zijn vaak afhankelijk van de toestemming van de gebruiker om te worden geactiveerd. Dit zou de meerderheid van het verkeer kunnen vertegenwoordigen dat niet wordt gevolgd. Voor klanten die inhoudsverzoeken op hun willen meten, wordt het geadviseerd om zich op analysehulpmiddelen te baseren die gegevensserver-kant of CDN- rapporten verzamelen. |
| Tags | Alle pagina&#39;s of API-aanroepen die als Adobe Experience Manager-inhoudsaanvragen worden bijgehouden, worden mogelijk niet gelabeld met Analytics tracking. |
| Tag Management-regels | Instellingen voor regels voor het beheer van tags kunnen leiden tot verschillende configuraties voor gegevensverzameling op een pagina. Dit leidt tot enige combinatie van verschillen met het bijhouden van de inhoudsaanvraag. |
| Bots | Onbekende bots die niet vooraf zijn geïdentificeerd en door AEM zijn verwijderd, kunnen verschillen in het bijhouden van gegevens veroorzaken. |
| Rapportageopties | Pagina&#39;s die deel uitmaken van hetzelfde AEM exemplaar en domein, kunnen gegevens naar verschillende analytische rapportsuites verzenden. |
| Instrumenten voor toezicht en beveiliging van derden | Met de hulpprogramma&#39;s voor controle en beveiligingsscans kunt u verzoeken om inhoud genereren voor AEM die niet worden bijgehouden in analytische rapporten. |
| API-toegang | Programmatische toegang tot pagina&#39;s of tot Adobe Experience Manager API&#39;s kan inhoudsverzoeken voor AEM genereren die niet worden bijgehouden in analyserapporten. |
| Prefetverzoeken | Als u een prefetch-service gebruikt om pagina&#39;s vooraf te laden om de snelheid te verhogen, kan dit leiden tot aanzienlijke toename van het verkeer van inhoudsverzoeken. |
| DDOS | Terwijl de Adobe pogingen doet om verkeer van aanvallen DDOS automatisch te ontdekken en uit te filtreren, is er geen garantie dat alle mogelijke aanvallen DDOS worden ontdekt. |
| Verkeersblokkers | Als u een tracker-blokker in een browser gebruikt, kunnen sommige aanvragen niet worden bijgehouden. |
| Firewalls | Firewalls kunnen het bijhouden van analyses blokkeren. Dit scenario komt vaker voor bij bedrijfsfirewalls. |

Zie ook [ Dashboard van de Vergunning ](/help/implementing/cloud-manager/license-dashboard.md).

## Regels voor verzamelingen op de server {#serverside-collection}

Er bestaan regels om bekende bots uit te sluiten, waaronder bekende services die regelmatig de site bezoeken om hun zoekindex of service te vernieuwen.

### Typen opgenomen inhoudsaanvragen {#included-content-requests}

| Type aanvraag | Content Request | Beschrijving |
| --- | --- | --- |
| HTTP-code 100-299 | Opgenomen | Dit zijn regelmatige verzoeken die alle of gedeeltelijke inhoud leveren. |
| HTTP-bibliotheken voor automatisering | Opgenomen | Voorbeelden:<br>・ Amazon CloudFront <br>・ Apache Http Client <br>・ Asynchronous Http Client <br>・ Axios <br>・ Azureus <br>・ Curl <br>・ GitHub Node Fetch <br>・ Guzzle <br>・ Go-http-client <br>・ Headless Chrome <br>・ Java™ Client 1}・ Jersey <br>・ Node Oembed <br>・ okhttp <br>・ Python-verzoeken <br>・ Reactor Netty <br>・ Wget <br>・ WinHTTP<br> |
| Gereedschappen voor toezicht en gezondheidscontrole | Opgenomen | Deze worden opgezet door de klant om een bepaald aspect van de plaats te controleren. Bijvoorbeeld, beschikbaarheid of real-world gebruikersprestaties.Als deze specifieke eindpunten zoals /system/sonds/gezondheid voor gezondheidscontroles richten, adviseren wij dat u `/system/probes/health` eindpunt en niet de daadwerkelijke HTML pagina&#39;s van de plaats gebruikt.[ zie hieronder ](#excluded-content-request)<br> Voorbeelden:<br>・ Amazon-Route53-Health-Check-Service <br>・ EyeMonIT_bot_version_0.1_[ (https://www.eyemon.it/) ](https://www.eyemon.it/) <br>・ Investis-Site24x7 <br>・ Mozilla/5.0+ (compatibel; UptimeRobot/2.0; [ https://uptimerobot.com/ 9}) <br>・ ThousandEyes-Dragonfly-x1 ](https://uptimerobot.com/)・ OmtrBot/1.0 <br>・ WebMon/2.0.0<br> |
| `<link rel="prefetch">` aanvragen | Opgenomen | Om de snelheid van het laden van de volgende pagina te verhogen, kunnen klanten browser een reeks pagina&#39;s hebben laden alvorens de gebruiker verbinding-zodat zij reeds in het geheime voorgeheugen zijn. *Gedacht: Dit verhoogt significant het verkeer* - afhankelijk van hoeveel van deze pagina&#39;s vooraf ingesteld zijn. |
| Het verkeer dat Adobe Analytics of Googles Analytics het melden blokkeert | Opgenomen | Het is meer gebruikelijk dat bezoekers van sites privacysoftware (Ad-blockers, enzovoort) hebben geïnstalleerd die van invloed is op de nauwkeurigheid van Googles Analytics of Adobe Analytics. AEM as a Cloud Service telt verzoeken op het eerste ingangspunt in de door de Adobe beheerde infrastructuur en niet op de client. |

Zie ook [ Dashboard van de Vergunning ](/help/implementing/cloud-manager/license-dashboard.md).

### Typen verzoeken om uitgesloten inhoud {#excluded-content-request}

| Type aanvraag | Content Request | Beschrijving |
| --- | --- | --- |
| HTTP-code 500+ | Uitgesloten | Fouten die aan de bezoeker zijn geretourneerd wanneer er iets verkeerd gaat op AEM as a Cloud Service of de aangepaste code van de klant. |
| HTTP-code 400-499 | Uitgesloten | Fouten die aan de bezoeker zijn geretourneerd wanneer de inhoud niet bestaat (404) of wanneer er andere problemen zijn met inhoud of verzoeken. |
| HTTP-code 300-399 | Uitgesloten | Dit zijn goede verzoeken die of controleren of iets op de server is veranderd, of het verzoek aan een andere middel opnieuw richten. Ze bevatten geen inhoud op zich en kunnen daarom niet worden gefactureerd. |
| Verzoeken naar /libs/* | Uitgesloten | AEM interne JSON-aanvragen, zoals de CSRF-token die niet kan worden opgevraagd. |
| Verkeer van aanvallen DDOS | Uitgesloten | DDOS-bescherming. AEM detecteert sommige DDOS-aanvallen automatisch en blokkeert deze. DDOS-aanvallen indien gedetecteerd, kunnen niet worden opgeladen. |
| AEM as a Cloud Service New Relic Monitoring | Uitgesloten | AEM as a Cloud Service global monitoring. |
| URL voor klanten om hun programma van de Cloud Service te controleren | Uitgesloten | Wij adviseerden om URL te gebruiken om de beschikbaarheid of de gezondheidscontrole extern te controleren.<br><br>`/system/probes/health` |
| AEM as a Cloud Service Pod Warm-up Service | Uitgesloten |
| Agent: skyline-service-warmup/1.* |
| Bekende zoekmachines, sociale netwerken en HTTP-bibliotheken (getagd door Snelst) | Uitgesloten | De bekende diensten die de plaats regelmatig bezoeken om hun onderzoeksindex of de dienst te verfrissen:<br><br> Voorbeelden:<br>・ AddSearchBot <br>・ AhrefsBot <br>・ Applebot <br>・ Vraag Jeeves Corporate Spider <br>・ Bingbot <br>・ BingPreview <br>・ BLEXBot <br>・ BouwtWith <br> <br>・ CrawlerKengo <br>・ Facebookexternalhit <br>・ Google AdsBot <br>・ Google AdsBot Mobile <br>・ Googlebot <br>・ Googlebot Mobile <br>・ lmspin <br>・ LucidWorks <br>・ MJ12bot <br>・ Prité <br>・ Pinterest <br>・ SembrushBot <br>・ SiteImproved <br>・ StashBot <br>・ StatusCake <br>・ YandexBot |
| Commerce integration framework-aanroepen uitsluiten | Uitgesloten | Dit zijn verzoeken aan AEM die door:sturen aan het Commerce integration framework-URL begint met `/api/graphql`-om dubbel tellen te vermijden, zijn zij niet factureerbaar voor Cloud Service. |
| Uitsluiten `manifest.json` | Uitgesloten | Manifest is geen API-aanroep. Het is hier om informatie op te geven over het installeren van websites op computers of mobiele telefoons. Adobe mag JSON-aanvraag niet tellen naar `/etc.clientlibs/*/manifest.json` |
| Uitsluiten `favicon.ico` | Uitgesloten | Terwijl de teruggekeerde inhoud niet HTML of JSON zou moeten zijn, zien wij dat in sommige scenario&#39;s zoals de authentificatiestromen van SAML, de favicons kunnen zijn teruggekeerd aangezien HTML daarom uitdrukkelijk van de telling wordt uitgesloten. |
