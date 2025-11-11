---
title: Cloud Service-inhoudsverzoeken begrijpen
description: Als u licenties voor inhoudsaanvragen van Adobe hebt aangeschaft, leest u meer over de typen inhoudsaanvragen die Adobe Experience Cloud als een service meet en de verschillen met de analytische rapportagehulpprogramma's van een organisatie.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: f9a767e3d5ae33cd46dc100c2ee59ec9ce8f63ac
workflow-type: tm+mt
source-wordcount: '1918'
ht-degree: 0%

---

# Inhoudsverzoeken van Cloud Service begrijpen

## Inleiding {#introduction}

Inhoudsverzoeken omvatten aanvragen die naar AEM Sites worden verzonden. Deze verzoeken kunnen door Edge Delivery Services of klant-verstrekt caching systemen zoals een Netwerk van de Levering van de Inhoud (CDN) leiden. Deze verzoeken leveren gestructureerde gegevens in HTML- of JSON-indeling en ondersteunen paginaweergaven (bijvoorbeeld pagina&#39;s en ervaringsfragmenten) of JSON retourneert zonder kop via API&#39;s.

Het systeem telt inhoudsverzoeken wanneer een gebruiker een pagina gebruikend HTML of JSON bekijkt. Het meet het verzoek op het punt waar het eerste caching systeem het ontvangt. Bepaalde HTTP-aanvragen worden opgenomen of uitgesloten voor het tellen van inhoudsaanvragen. Zie de volledige lijst van HTTP [ inbegrepen inhoudsverzoeken ](#included-content-requests) en [ uitgesloten inhoudsverzoeken ](#excluded-content-request).

>[!NOTE]
>
>De gegevens die worden weergegeven in de weergave Verzoeken om de 24 uur worden vernieuwd.

## Over Cloud Service-inhoudsaanvragen {#understanding-cloud-service-content-requests}

A *paginaverzoek* verwijst naar een HTTP- verzoek dat kern gestructureerde inhoud (bijvoorbeeld, HTML of JSON) noodzakelijk terugwint om de belangrijkste paginaervaring terug te geven. Het omvat geen verzoeken om elementen, zoals afbeeldingen of scripts.

Voor klanten die uit-van-de-doos CDN gebruiken, telt AEM as a Cloud Service inhoudsverzoeken zoals die op het server-zijniveau worden gemeten. Deze meting wordt automatisch uitgevoerd en is niet afhankelijk van het bijhouden van analyses op de client.

AEM (Adobe Experience Manager) as a Cloud Service identificeert inhoudsverzoeken die op de reactietypes worden gebaseerd die door de instantie van AEM worden geproduceerd en bij CDN worden ontvangen. Specifiek, verzoeken dat de terugkeer HTML (`text/html`) of JSON (`application/json`) wordt geteld. Deze indelingen leveren doorgaans inhoud op de primaire pagina, voor traditionele rendering van sites of voor levering zonder kop.

Aanvragen voor statische elementen zoals JavaScript-bestanden, CSS-stijlpagina&#39;s en afbeeldingen worden niet geteld als aanvragen voor inhoud.

>[!NOTE]
>Als een API-verzoek HTML of JSON retourneert die fungeert als inhoud op paginaniveau (bijvoorbeeld in koploze levering), kan het nog steeds worden geteld als een inhoudsaanvraag, afhankelijk van de context.

De verzoeken van de inhoud worden gemeten ongeacht of de reactie van het CDN geheime voorgeheugen of door:sturen aan het milieu van oorsprong AEM werd gediend.

<!-- REMOVED AS PER EMAIL REQUEST FROM SHWETA DUA, JULY 30, 2024 TO RICK BROUGH AND ALEXANDRU SARCHIZ   For customers employing their own CDN, client-side collection offers a more precise reflection of interactions, ensuring a reliable measure of website engagement via the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) service. This gives customers advanced insights into their page traffic and performance. While it is beneficial for all customers, it offers a representative reflection of user interactions, ensuring a reliable measure of website engagement by capturing the number of page views from the client side. 

For customers that bring their own CDN on top of AEM as a Cloud Service, server-side reporting results in numbers that cannot be used to compare with the licensed content requests. With the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md), Adobe can reflect a reliable measure of website engagement. -->

### Variaties in Cloud Service-inhoudsaanvragen {#content-requests-variances}

Inhoudsverzoeken kunnen variaties hebben binnen de analytische rapportagehulpprogramma&#39;s van een organisatie, zoals wordt samengevat in de volgende tabel. In het algemeen geldt dat u geen analyseprogramma&#39;s moet gebruiken die afhankelijk zijn van instrumenten aan de clientzijde om het aantal aanvragen voor inhoud voor een site te melden. Deze hulpmiddelen missen vaak een groot deel van verkeer omdat zij van gebruikerstoestemming afhangen om worden geactiveerd. De hulpmiddelen van de analyse die gegevensserver-kant in logboekdossiers verzamelen, of CDN- rapporten voor klanten die hun eigen CDN bovenop AEM as a Cloud Service toevoegen, verstrekken betere tellingen.

| Reden voor variantie | Toelichting |
|---|---|
| Goedkeuring eindgebruiker | Analysemiddelen die afhankelijk zijn van instrumenten aan de clientzijde zijn vaak afhankelijk van de toestemming van de gebruiker om te worden geactiveerd. Dit werkschema kon het grootste deel van het verkeer vertegenwoordigen dat niet wordt gevolgd. Voor klanten die inhoudsverzoeken op hun willen meten, adviseert Adobe dat u zich op analysehulpmiddelen baseert om gegevens van server-kant of CDN- rapporten te verzamelen. |
| Tags | Alle pagina&#39;s of API-aanroepen die als Adobe Experience Manager-inhoudsaanvragen worden bijgehouden, worden mogelijk niet gelabeld met Analytics tracking. |
| Tag Management-regels | Instellingen voor regels voor het beheer van tags kunnen leiden tot verschillende configuraties voor gegevensverzameling op een pagina. Dit leidt tot enige combinatie van verschillen met het bijhouden van de inhoudsaanvraag. |
| Bots | Onbekende bots die AEM niet vooraf heeft geïdentificeerd en verwijderd, kunnen verschillen in het bijhouden van gegevens veroorzaken. |
| Rapportageopties | Pagina&#39;s binnen hetzelfde AEM-exemplaar kunnen naar verschillende analytische rapportsets rapporteren. Dit proces kan gegevens over veelvoudige reeksen, afhankelijk van configuratie verdelen. |
| Instrumenten voor toezicht en beveiliging van derden | Met de controle- en beveiligingsscangereedschappen (bijvoorbeeld uptime-checkers of kwetsbaarheidsscanners) kunnen pagina&#39;s worden aangevraagd. Zo worden aan de serverzijde inhoudsverzoeken gegenereerd die niet zichtbaar zijn in analyserapporten. |
| API-toegang | Aanvragen van AEM-pagina&#39;s of inhoud via API&#39;s (bijvoorbeeld via Adobe Experience Manager als een Headless CMS) worden nog steeds beschouwd als aanvragen voor inhoud, maar activeren het bijhouden van analyses niet. |
| Prefetverzoeken | Bij prefetching (bijvoorbeeld met een serviceworker of randfunctie) kunnen de volumes van het verkeer toenemen door van tevoren pagina&#39;s aan te vragen. Deze verzoeken worden geteld aan de serverzijde, maar voeren geen analytische code aan de clientzijde uit. |
| DDOS | Adobe gebruikt het filtreren om vele aanvallen te ontdekken en te blokkeren DDoS. Nochtans, kunnen sommige aanvalsverzoeken nog als inhoudseverzoeken worden geteld alvorens de filters van toepassing zijn. |
| Verkeersblokkers | Privacy-functies in de browser of bedrijfsfirewalls kunnen het laden van analysescripts blokkeren. Deze gebruikers genereren nog steeds verzoeken om inhoud op de server. |
| Firewalls | Met bedrijfsfirewalls of regionale firewalls kan worden voorkomen dat analytische aanroepen Adobe-servers bereiken, wat leidt tot onderrapportage in analyses, terwijl het aantal aan de serverzijde ongewijzigd blijft. |

Zie het [ dashboard van de Vergunning ](/help/implementing/cloud-manager/license-dashboard.md) voor informatie over het bekijken en het volgen gebruik van de inhoudsverzoek tegen uw vergunningsgrenzen.

## Regels voor verzamelingen op de server {#serverside-collection}

AEM as a Cloud Service past verzamelingsregels aan de serverzijde toe op aanvragen voor telinhoud. Deze regels sluiten bekende bots (zoals zoekmachinecrawlers) en een reeks controlediensten uit die regelmatig de plaats pingelen. Ander synthetisch of controle-type verkeer niet op deze uitsluitingslijst wordt geteld als factureerbare inhoudverzoeken.

In de volgende tabellen worden de typen opgenomen en uitgesloten inhoudsaanvragen vermeld, met korte beschrijvingen van elk.

### Typen opgenomen inhoudsaanvragen {#included-content-requests}

>[!NOTE]
>Als een API-aanvraag een HTML-reactie retourneert, kan deze, afhankelijk van de gebruikscontext, worden geclassificeerd als een inhoudsaanvraag. API-aanvragen die niet-UI-gegevens retourneren, worden meestal uitgesloten.

| Type aanvraag | Content Request | Beschrijving |
| --- | --- | --- |
| HTTP-code 100-299 | Opgenomen | Omvat succesvolle verzoeken die volledige of gedeeltelijke HTML of inhoud JSON terugkeren.<br> Code 206 van HTTP: Deze verzoeken leveren slechts een gedeelte van de volledige inhoud. Bijvoorbeeld een video of een grote afbeelding. Gedeeltelijke inhoudsaanvragen worden opgenomen wanneer ze een deel van een HTML- of JSON-reactie leveren die wordt gebruikt bij het renderen van pagina-inhoud. |
| HTTP-bibliotheken voor automatisering | Opgenomen | Verzoeken die zijn gemaakt door gereedschappen of bibliotheken die pagina-inhoud ophalen. Voorbeelden zijn: <br>・ Amazon CloudFront <br>・ Apache Http Client <br>・ Asynchronous HTTP Client <br>・ Axios <br>・ Azureus <br>・ Curl <br>・ GitHub Node Fetch <br>・ Guzzle <br>・ Go-http-client <br>・ Headless Chrome <br>・ Java™ Client {1 <br>・ Jersey <br>・ Node Oembed <br>・ okhttp<br>・ Python-verzoeken <br>・ Reactor Netty <br>・ Wget <br>・ WinHTTP <br>・ Fast HTTP <br>・ GitHub Node Fetch <br>・ Reactor Netty |
| Gereedschappen voor toezicht en gezondheidscontrole | Opgenomen | Verzoeken die worden gebruikt om de gezondheid of beschikbaarheid van pagina&#39;s te controleren.<br> zie [ Types van uitgesloten inhoudsverzoeken ](#excluded-content-request).<br> Voorbeelden omvatten het volgende:<br>・ `Amazon-Route53-Health-Check-Service`<br>・ EyeMonIT_bot_version_0.1_[ (https://eyemonit.com/) ](https://eyemonit.com/) <br>・ Investis-Site24x7 <br>・ Mozilla/5.0+ (compatibel; UptimeRobot/2.0; [ https://uptimerobot.com/ ](https://uptimerobot.com/)) <br>・ ThousandEyes-gonfly-x1 <br>・ OmtrBot/1.0 <br>・ WebMon/2.0.0 |
| `<link rel="prefetch">` aanvragen | Opgenomen | Wanneer klanten vooraf inhoud laden of vooraf instellen (bijvoorbeeld met `<link rel="prefetch">`), telt het systeem die serververzoeken. Let erop dat deze benadering het verkeer kan verhogen, afhankelijk van het aantal van deze pagina&#39;s dat vooraf is ingesteld. |
| Verkeer dat Adobe Analytics- of Google Analytics-rapportage blokkeert | Opgenomen | Het is meer gebruikelijk dat bezoekers van sites privacysoftware (Ad-blockers, enzovoort) hebben geïnstalleerd die van invloed is op de nauwkeurigheid van Google Analytics of Adobe Analytics. AEM as a Cloud Service telt verzoeken op het eerste toegangspunt tot de door Adobe geëxploiteerde infrastructuur en niet op de client. |

Zie ook [ Dashboard van de Vergunning ](/help/implementing/cloud-manager/license-dashboard.md).

### Typen verzoeken om uitgesloten inhoud {#excluded-content-request}

| Type aanvraag | Content Request | Beschrijving |
| --- | --- | --- |
| HTTP-code 500+ | Uitgesloten | Fouten die aan de bezoeker zijn geretourneerd wanneer er iets verkeerd gaat op AEM as a Cloud Service of de aangepaste code van de klant. |
| HTTP-code 400-499 | Uitgesloten | Fouten die aan de bezoeker zijn geretourneerd wanneer de inhoud niet bestaat (404) of wanneer er andere problemen zijn met inhoud of verzoeken. |
| HTTP-code 300-399 | Uitgesloten | De goede verzoeken dat of controleren of iets op de server is veranderd, of het verzoek aan een andere middel opnieuw richten. Ze bevatten geen inhoud op zich en kunnen daarom niet worden gefactureerd. |
| Verzoeken naar `/libs/`* | Uitgesloten | AEM interne JSON-aanvragen, zoals de CSRF-token die niet kan worden opgevraagd. |
| Verkeer van aanvallen DDOS | Uitgesloten | DDOS-bescherming. AEM detecteert sommige DDOS-aanvallen automatisch en blokkeert deze. DDOS-aanvallen indien gedetecteerd, kunnen niet worden opgeladen. |
| AEM as a Cloud Service New Relic Monitoring | Uitgesloten | AEM as a Cloud Service global monitoring. |
| URL voor klanten om hun Cloud Service-programma te controleren | Uitgesloten | Adobe adviseert dat u URL gebruikt om de beschikbaarheid of de gezondheidscontrole uiterlijk te controleren.<br><br>`/system/probes/health` |
| AEM as a Cloud Service Pod Warm-up Service | Uitgesloten | Agent: skyline-service-warmup/1.* |
| Bekende zoekmachines, sociale netwerken en HTTP-bibliotheken (getagd door Snelst) | Uitgesloten | De bekende diensten die de plaats regelmatig bezoeken om hun onderzoeksindex of de dienst te verfrissen:<br><br> Voorbeelden:<br>・ AddSearchBot <br>・ AhrefsBot <br>・ Applebot <br>・ Vraag Jeeves Corporate Spider <br>・ Bingbot <br>・ BingPreview <br>・ BLEXBot <br>・ BouwtWith <br> <br>・ CrawlerKengo <br>・ Facebookexternalhit <br>・ Google AdsBot <br>・ Google AdsBot Mobile <br>・ Googlebot <br>・ Googlebot Mobile <br>・ lmspin <br>・ LucidWorks <br>・ `MJ12bot`<br> Pinterest <br>・ SembrushBot <br>・ SiteImproved <br>・ StashBot <br>・ StatusCake <br>・ YandexBot <br>・ ContentKing <br>・ Claudebot |
| Commerce integration framework-oproepen uitsluiten | Uitgesloten | Verzoeken die zijn ingediend bij AEM en die worden doorgestuurd naar de Commerce integration framework—de URL begint met `/api/graphql`—om dubbeltellingen te voorkomen, kunnen niet worden gefactureerd voor Cloud Service. |
| Uitsluiten `manifest.json` | Uitgesloten | Manifest is geen API-oproep. Hier vindt u informatie over het installeren van websites op een desktopcomputer of mobiele telefoon. Adobe moet JSON-aanvraag niet tellen naar `/etc.clientlibs/*/manifest.json` |
| Uitsluiten `favicon.ico` | Uitgesloten | Hoewel de geretourneerde inhoud HTML of JSON niet moet zijn, zijn er bij bepaalde scenario&#39;s, zoals SAML-verificatiestromen, favicons geretourneerd als HTML. Dientengevolge, worden de favicons uitdrukkelijk uitgesloten van de telling. |
| Experience Fragment (XF) - hergebruik op hetzelfde domein | Uitgesloten | Aanvragen van XF-paden (zoals `/content/experience-fragments/...` ) die zijn gedaan vanaf pagina&#39;s die worden gehost op hetzelfde domein (zoals wordt aangegeven door de verwijzingsheader die overeenkomt met de aanvraaghost).<br><br> Voorbeeld: een homepage van `aem.customer.com` die in een XF voor een banner of kaart van het zelfde domein trekt.<br><br>・ URL gelijken /content/experience-fragments/...<br>・ het domeinovereenkomsten van de Verwijzing `request_x_forwarded_host`<br><br>**Nota:** als de weg van het Fragment van de Ervaring wordt aangepast (bijvoorbeeld gebruikend `/XFrags/...` of om het even welk weg buiten `/content/experience-fragments/`), zal het verzoek niet worden uitgesloten en kan worden geteld, zelfs als het zelfde-domein is. We raden u aan de standaard XF-padstructuur van Adobe te gebruiken om te zorgen dat de uitsluitingslogica correct wordt toegepast. |

## Inhoudsverzoeken beheren {#managing-content-requests}

Zoals vermeld in de bovengenoemde sectie [ Varianties van de inhoudsverzoeken van Cloud Service ](#content-requests-variances), kunnen de inhoudsverzoeken hoger zijn dan verwacht toe te schrijven aan een aantal redenen, met een gemeenschappelijke draad die verkeer dat CDN raakt.  Het is voor u als AEM-klant nuttig om uw inhoudsaanvragen te controleren en te beheren om binnen uw licentiebudget te passen.  Het beheren van inhoudverzoeken is over het algemeen een combinatie implementatietechnieken en [ regels van de verkeersfilter ](/help/security/traffic-filter-rules-including-waf.md).

### Implementatietechnieken voor het beheer van inhoudsaanvragen {#implementation-techniques-to-manage-crs}

* Zorg ervoor dat de niet-gevonden reacties op de pagina worden geleverd met de HTTP-status 404.  Als ze worden geretourneerd met de status 200, tellen ze voor inhoudsaanvragen.
* De de gezondheidscontrole of controlehulpmiddelen van de route aan /system/sonds/gezondheid URL of gebruik de methode van HEAD in plaats van GET om het veroorzaken van inhoudsverzoeken te vermijden.
* Breng uw behoeften aan versheid van inhoud in evenwicht met AEM-licentiekosten voor elke aangepaste zoekfunctie die u met uw site hebt geïntegreerd.  Een al te agressieve krawler kan veel inhoudsverzoeken consumeren.
* Omleiding als server-side (status 301 of 302) in plaats van client-side (status 200 met javascript redirect) afhandelen om twee afzonderlijke inhoudsaanvragen te voorkomen.
* Combineer of verminder API vraag, die JSON reacties van AEM zijn die kunnen worden geladen om de pagina terug te geven.

### De filterregels van het verkeer om inhoudsverzoeken te beheren {#traffic-filter-rules-to-manage-crs}

* Een gemeenschappelijk beide patroon is het gebruiken van een lege gebruikersagent.  U zult uw implementatie en verkeerspatronen moeten herzien om te zien of is de lege gebruikersagent nuttig of niet.  Als u dit verkeer zou willen blokkeren, geadviseerde [ syntaxis ](/help/security/traffic-filter-rules-including-waf.md#rules-syntax) is:

```
trafficFilters:
  rules:
    - name: block-missing-user-agent
      when:
        anyOf:
          - { reqHeader: user-agent, exists: false }
          - { reqHeader: user-agent, equals: '' }
      action: block
```

* Sommige brouten raakten op een dag erg zwaar en verdwijnen de volgende.  Dit kan om het even welke pogingen om een specifiek IP adres of een gebruikersagent te blokkeren dwarsbomen.  Één generische benadering moet de regel van de a [ tariefgrens ](/help/security/traffic-filter-rules-including-waf.md#rate-limit-rules) introduceren.  Herzie de [ voorbeelden ](/help/security/traffic-filter-rules-including-waf.md#ratelimiting-examples) en vecht een regel die uw tolerantie voor een snel tarief van verzoeken aanpast.  Herzie de [ syntaxis van de Structuur van de Voorwaarde ](/help/security/traffic-filter-rules-including-waf.md#condition-structure) voor om het even welke uitzonderingen u aan een generische tariefgrens kunt wensen toe te staan.
