---
title: Inhoudsverzoeken van Cloud Servicen begrijpen
description: Als u licenties voor inhoudsaanvragen van Adobe hebt aangeschaft, leert u meer over de typen inhoudsaanvragen die Adobe Experience Cloud als een service meet en over de verschillen met de analytische rapportagehulpprogramma's van een organisatie.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '2688'
ht-degree: 0%

---

# Verzoeken om Cloud Service-inhoud

## Inleiding {#introduction}

De de inhoudsverzoeken van de Cloud Service worden gemeten via server-zijinzameling van gegevens. De inzameling wordt toegelaten via CDN logboekanalyse.

>[!NOTE]
>Daarnaast geldt voor een beperkt aantal [Klanten met vroege adoptie](/help/release-notes/release-notes-cloud/release-notes-current.md#sites-early-adopter), de cliënt-zijinzameling zal ook via de Echte de dienstmeting van de Controle van de Gebruiker worden toegelaten. U kunt meer leren door de documentatie te raadplegen in [dit artikel](#real-user-monitoring-for-aem-as-a-cloud-service).

## Inhoudsverzoeken van Cloud Servicen begrijpen {#understaing-cloud-service-content-requests}

Aanvragen voor inhoud worden automatisch op de server aan de rand van Adobe Experience Manager as a Cloud Service verzameld, via automatische analyse van de logbestanden die afkomstig zijn van de AEM as a Cloud Service CDN. Dit wordt gedaan door de verzoeken te isoleren die HTML terugkeren `(text/html)` of JSON `(application /Json)` inhoud van CDN, en gebaseerd op verscheidene hieronder gedetailleerde opname en uitsluitingsregels. Een inhoudsverzoek komt onafhankelijk van de teruggekeerde inhoud voor die van de CDN geheime voorgeheugens wordt gediend of de inhoud die terug naar de oorsprong van CDN (AEM verzenders) gaat.

De Echte dienst van de Controle van de Gebruiker, de cliënt-zijinzameling, biedt een nauwkeurigere weerspiegeling van gebruikersinteractie, die een betrouwbare meting van websitebetrokkenheid verzekert. Dit geeft klanten geavanceerde inzichten in hun paginaverkeer en prestaties. Terwijl dit voor beide klanten voordelig is die of de Adobe beheerde CDN of een niet-Adobe beheerde CDN gebruiken. Bovendien kan het automatische verkeer die voor klanten nu rapporteren worden toegelaten die een niet-Adobe beheerde CDN gebruiken, waarbij de behoefte wordt verwijderd om het even welke verkeersrapporten met Adobe te delen.

Voor klanten die hun eigen CDN bovenop AEM as a Cloud Service brengen, zal de server-zijrapportering in aantallen resulteren die niet kunnen worden gebruikt om met de vergunning gegeven inhoudsverzoeken te vergelijken. Deze aantallen zullen door de klant bij de rand van buitenste CDN moeten worden gemeten. Voor deze klanten, cliënt-zijrapportering en bijbehorende prestaties, [Adobe RUM Data Service](#real-user-monitoring-for-aem-as-a-cloud-service) Dit is de aanbevolen Adobe. Zie de [releaseopmerkingen](/help/release-notes/release-notes-cloud/release-notes-current.md#sites-early-adopter) voor informatie over de wijze van opt-in.

## Verzameling op server {#serverside-collection}

Er bestaan regels om bekende bots uit te sluiten, waaronder bekende services die regelmatig de site bezoeken om hun zoekindex of service te vernieuwen.

### Variaties in aanvragen voor inhoud van Cloud Servicen {#content-requests-variances}

De Verzoeken van de inhoud kunnen variaties met Analytics van een organisatie hebben rapporteringshulpmiddelen zoals samengevat in de volgende lijst. In het algemeen: *niet* analytische hulpmiddelen gebruiken die gegevens door middel van instrumentatie aan de clientzijde verzamelen om over het aantal inhoudsverzoeken voor een bepaalde plaats te rapporteren, eenvoudig omdat zij vaak afhankelijk zijn van de toestemming van de gebruiker om in werking te worden gesteld, waardoor zij ontbreken op een significant deel van het verkeer. De hulpmiddelen van de analyse die gegevensserver-kant in logboekdossiers verzamelen, of CDN- rapporten voor klanten die hun eigen CDN bovenop AEM as a Cloud Service toevoegen, zullen betere tellingen verstrekken. Voor het melden van paginaweergaven en de bijbehorende prestaties is de Adobe RUM Data Service de aanbevolen optie voor de Adobe.

| Reden voor variantie | Toelichting |
|---|---|
| Goedkeuring eindgebruiker | Analytische hulpmiddelen die afhankelijk zijn van instrumentvermelding op de client zijn vaak afhankelijk van de toestemming van de gebruiker om te worden geactiveerd. Dit zou de meerderheid van het verkeer kunnen vertegenwoordigen dat niet wordt gevolgd. Voor klanten die inhoudsverzoeken op hun willen meten, wordt het geadviseerd om zich op analysehulpmiddelen te baseren die gegevensserver-kant of CDN- rapporten verzamelen. |
| Tags | Alle pagina&#39;s of API-aanroepen die worden bijgehouden als Adobe Experience Manager-inhoudsaanvragen (AEM), worden mogelijk niet gelabeld met Analytics tracking. |
| Tag Management-regels | Instellingen voor regels voor het beheer van tags kunnen leiden tot verschillende configuraties voor gegevensverzameling op een pagina. Dit leidt tot enige combinatie van verschillen met het bijhouden van de inhoudsaanvraag. |
| Bots | Onbekende bots die niet vooraf zijn geïdentificeerd en door AEM zijn verwijderd, kunnen verschillen in het bijhouden van gegevens veroorzaken. |
| Rapportageopties | Pagina&#39;s die deel uitmaken van hetzelfde AEM exemplaar en domein, kunnen gegevens naar verschillende analytische rapportsuites verzenden. |
| Instrumenten voor toezicht en beveiliging van derden | Met de hulpprogramma&#39;s voor controle en beveiligingsscans kunt u verzoeken om inhoud genereren voor AEM die niet worden bijgehouden in analytische rapporten. |
| API-toegang | Programmatische toegang tot pagina&#39;s of tot Adobe Experience Manager API&#39;s kan inhoudsverzoeken voor AEM genereren die niet worden bijgehouden in analyserapporten. |
| Prefetverzoeken | Als u een prefetch-service gebruikt om pagina&#39;s vooraf te laden om de snelheid te verhogen, kan dit leiden tot aanzienlijke toename van het verkeer van inhoudsverzoeken. |
| DDOS | Terwijl de Adobe pogingen doet om verkeer van aanvallen DDOS automatisch te ontdekken en uit te filtreren, is er geen garantie dat alle mogelijke aanvallen DDOS worden ontdekt. |
| Verkeersblokkers | Als u een tracker-blokker in een browser gebruikt, kunnen sommige aanvragen niet worden bijgehouden. |
| Firewalls | Firewalls kunnen het bijhouden van analyses blokkeren. Dit scenario komt vaker voor bij bedrijfsfirewalls. |

Zie ook [Licentiedashboard](/help/implementing/cloud-manager/license-dashboard.md).

### Typen opgenomen inhoudsaanvragen {#included-content-requests}

| Type aanvraag | Content Request | Beschrijving |
| --- | --- | --- |
| HTTP-code 100-299 | Opgenomen | Dit zijn regelmatige verzoeken die alle of gedeeltelijke inhoud leveren. |
| HTTP-bibliotheken voor automatisering | Opgenomen | Voorbeelden:<br>Amazon CloudFront<br>Apache Http Client<br>・ Asynchrone HTTP-client<br>Axios<br>Azureus<br>・ Curl<br>・ GitHub Node Fetch<br>・ Guzzle<br>・ Go-http-client<br>・ Hoofdloze chroom<br>・ Java™-client<br>Jersey<br>・ Node Oembed<br>・ okhttp<br>Python-verzoeken<br>・ Reactor-netwerk<br>・ Wget<br>WinHTTP |
| Gereedschappen voor toezicht en gezondheidscontrole | Opgenomen | Deze worden opgezet door de klant om een bepaald aspect van de plaats te controleren. Bijvoorbeeld beschikbaarheid of real-world gebruikersprestaties. Gebruiken `/system/probes/health` en niet de daadwerkelijke HTML pagina&#39;s van de plaats.<br>Voorbeelden:<br>・ Amazon-Route53-Health-Check-Service<br>・ EyeMonIT_bot_version_0.1_[https://www.eyemon.it/)](https://www.eyemon.it/)<br>・ Investis-Site24x7<br>・ Mozilla/5.0+(compatibel; UptimeRobot/2.0; [https://uptimerobot.com/](https://uptimerobot.com/))<br>・ ThousandEyes-Dragonfly-x1<br>OmtrBot/1.0<br>・ WebMon/2.0.0 |
| `<link rel="prefetch">` verzoeken | Opgenomen | Om de snelheid van het laden van de volgende pagina te verhogen, kunnen klanten browser een reeks pagina&#39;s hebben laden alvorens de gebruiker verbinding-zodat zij reeds in het geheime voorgeheugen zijn. *Mind: Dit verhoogt het verkeer aanzienlijk*—afhankelijk van het aantal van deze pagina&#39;s dat vooraf is ingesteld. |
| Het verkeer dat Adobe Analytics of Googles Analytics het melden blokkeert | Opgenomen | Het is meer gebruikelijk dat bezoekers van sites privacysoftware (Ad-blockers, enzovoort) hebben geïnstalleerd die van invloed is op de nauwkeurigheid van Googles Analytics of Adobe Analytics. AEM verzoeken om as a Cloud Service tellingen op het eerste ingangspunt in de door de Adobe beheerde infrastructuur en niet aan de clientzijde. |

Zie ook [Licentiedashboard](/help/implementing/cloud-manager/license-dashboard.md).

### Typen verzoeken om uitgesloten inhoud {#excluded-content-request}

| Type aanvraag | Content Request | Beschrijving |
| --- | --- | --- |
| HTTP-code 500+ | Uitgesloten | Fouten die aan de bezoeker zijn geretourneerd wanneer er iets mis gaat met AEM as a Cloud Service of aangepaste code van de klant. |
| HTTP-code 400-499 | Uitgesloten | Fouten die aan de bezoeker zijn geretourneerd wanneer de inhoud niet bestaat (404) of wanneer er andere problemen zijn met inhoud of verzoeken. |
| HTTP-code 300-399 | Uitgesloten | Dit zijn goede verzoeken die of controleren of iets op de server is veranderd, of het verzoek aan een andere middel opnieuw richten. Ze bevatten geen inhoud op zich en kunnen daarom niet worden gefactureerd. |
| Verzoeken naar /libs/* | Uitgesloten | AEM interne JSON-aanvragen, zoals de CSRF-token die niet kan worden opgevraagd. |
| Verkeer van aanvallen DDOS | Uitgesloten | DDOS-bescherming. AEM detecteert sommige DDOS-aanvallen automatisch en blokkeert deze. DDOS-aanvallen indien gedetecteerd, kunnen niet worden opgeladen. |
| AEM as a Cloud Service NewRelic Monitoring | Uitgesloten | AEM as a Cloud Service wereldwijde monitoring. |
| URL voor klanten om hun programma van de Cloud Service te controleren | Uitgesloten | Aanbevolen URL om de beschikbaarheid extern te controleren.<br><br>`/system/probes/health` |
| as a Cloud Service pod Warm-up service AEM | Uitgesloten | Gebruikersagent: skyline-service-warmup/1.* |
| Bekende zoekmachines, sociale netwerken en HTTP-bibliotheken (getagd door Snelst) | Uitgesloten | De bekende diensten die de plaats regelmatig bezoeken om hun onderzoeksindex of de dienst te verfrissen:<br><br>Voorbeelden:<br>・ AddSearchBot<br>AhrefsBot<br>Applebot<br>・ Vraag Jeeves Corporate Spider<br>Bingbot<br>・ BingPreview<br>・ BLEXBot<br>・ BuiltWith<br>Bytespider<br>CrawlerKengo<br>Facebook externalhit<br>Google AdsBot<br>・ Google AdsBot Mobile<br>Googlebot<br>Googlebot Mobile<br>lmspider<br>・ LucidWorks<br>MJ12bot<br>・ VK<br>pinterest<br>・ SemspitseBot<br>・ SiteImproved<br>・ StashBot<br>・ StatusCake<br>YandexBot |
| Commerce integration framework-aanroepen uitsluiten | Uitgesloten | Dit zijn verzoeken aan AEM die door:sturen aan het Commerce integration framework-URL begint met `/api/graphql`—om dubbeltellingen te voorkomen, kunnen zij niet voor Cloud Service in rekening worden gebracht. |
| Uitsluiten `manifest.json` | Uitgesloten | Manifest is geen API-aanroep. Het is hier om informatie op te geven over het installeren van websites op computers of mobiele telefoons. Adobe mag JSON-verzoek niet tellen voor `/etc.clientlibs/*/manifest.json` |
| Uitsluiten `favicon.ico` | Uitgesloten | Terwijl de teruggekeerde inhoud niet HTML of JSON zou moeten zijn, zien wij dat in sommige scenario&#39;s zoals de authentificatiestromen van SAML, de favicons kunnen zijn teruggekeerd aangezien HTML daarom uitdrukkelijk van de telling wordt uitgesloten. |

## Clientverzameling {#cliendside-collection}

### Real User Monitoring Service voor AEM as a Cloud Service {#real-user-monitoring-service-for-aem-as-a-cloud-service}

>[!INFO]
>
>Deze functie is alleen beschikbaar voor programma voor vroege adoptie.
>U moet de AEM Cloud Service-versie gebruiken **2023 11 1427** en hoger om de RUM-datadienst mogelijk te maken.

### Overzicht {#overview}

De Real User Monitoring-service is een type technologie voor prestatiebewaking waarmee de digitale gebruikerservaring van een website of toepassing in real-time wordt vastgelegd en geanalyseerd. Het biedt inzicht in de real-time prestaties van een webtoepassing en biedt een accuraat inzicht in de gebruikerservaring.

De Echte dienst van de Controle van de Gebruiker verstrekt diep inzicht in zeer belangrijke prestatiesmetriek onmiddellijk vanaf de opening van URL tot het verzoek terug naar browser wordt gediend allen die de ontwikkelaars helpen de toepassing verbeteren om het voor het eind gemakkelijk te gebruiken - gebruikers te maken.

### Wie kan van de Echte Dienst van de Controle van de Gebruiker profiteren? {#who-can-benefit-from-rum-service}

De Dienst van Gegevens van het RUM is voordelig voor alle klanten of het gebruiken van Adobe, of hun eigen CDN. Deze weergave biedt een preciezere weergave van gebruikersinteracties, zodat een betrouwbare maatstaf voor de betrokkenheid van websites wordt verkregen door het aantal paginaweergaven op de client weer te geven.

Met name voor Adobe CDN-gebruikers worden gebruikersinteracties nauwkeurig bijgehouden voor een directe vergelijking van client-side paginaweergaven met server-side CDN-logboeken.

Voor klanten die hun eigen CDN in dienst nemen kunnen zij van vereenvoudigd verkeer profiteren dat rapporteert, aangezien de Adobe nu direct deze Weergaven van Pagina integreert, die de behoefte aan afzonderlijke rapporten elimineren.

Bovendien krijgen alle klanten diepgaande inzichten in paginaprestaties om hun digitale ervaringen effectief te optimaliseren.

### Begrijp hoe de Echte Dienst van de Controle van de Gebruiker werkt {#understand-how-the-rum-service-works}

Adobe Experience Manager gebruikt Real User Monitoring (RUM) om klanten en Adobe te helpen begrijpen, hoe bezoekers op Adobe Experience Manager-gebaseerde sites reageren, prestatieproblemen te diagnosticeren en de doeltreffendheid van experimenten te meten. RUM behoudt de privacy van bezoekers door middel van steekproeven - slechts een klein deel van alle paginaweergaven zal worden gecontroleerd - en oordeelkundige uitsluiting van alle persoonlijk identificeerbare informatie (PII).

### Real User Monitoring Service en Privacy {#rum-service-and-privacy}

De Echte dienst van de Controle van de Gebruiker in Adobe Experience Manager wordt ontworpen om bezoekersprivacy te bewaren en gegevensinzameling te minimaliseren. Als bezoeker betekent dit dat er geen persoonlijke gegevens worden verzameld op de site die u bezoekt of ter beschikking van de Adobe worden gesteld.

Als plaatsexploitant, betekent dit geen extra opt-in wordt vereist om controle door deze eigenschap toe te laten.Zo, zal er geen extra pop-up voor de eindgebruikers zijn om voor het toelaten van controle RUM te aanvaarden.

### Real User Monitoring Service Data Sampling {#rum-service-data-sampling}

Traditionele webanalytische oplossingen proberen gegevens te verzamelen voor elke bezoeker. De Echte dienst van de Controle van de Gebruiker van Adobe Experience Manager vangt slechts informatie van een klein gedeelte van paginameningen. De gegevens van de Echte dienst van de Controle van de Gebruiker zijn bedoeld om worden bemonsterd en worden geanonimiseerd eerder dan een vervanging voor analyses. Pagina&#39;s hebben standaard een bemonsteringsverhouding van 1:100. Site-beheerders kunnen dit aantal niet configureren om het bemonsteringsfrequentie vanaf vandaag te verhogen of te verlagen. Om het totale verkeer nauwkeurig te schatten, voor elke 100 paginagezichten, verzamelen wij gedetailleerde gegevens van één, die u een betrouwbare benadering van algemeen verkeer geven.&quot;

Aangezien de beslissing of de gegevens worden verzameld, per paginaweergave wordt genomen, is het vrijwel onmogelijk interacties op meerdere pagina&#39;s bij te houden. RUM heeft geen concept van bezoeken, bezoekers, of zittingen, slechts van paginameningen. Dit is door ontwerp.

### Welke gegevens worden verzameld {#what-data-is-being-collected}

De Echte dienst van de Controle van de Gebruiker wordt ontworpen om de inzameling van persoonlijk identificeerbare informatie te verhinderen. De volledige reeks informatie die kan worden verzameld door de Adobe Experience Manager Real User Monitoring-service wordt hieronder weergegeven:

* De hostnaam van de site die wordt bezocht, bijvoorbeeld: `experienceleague.adobe.com`
* Het algemene type gebruikersagent waarmee de pagina wordt weergegeven, bijvoorbeeld: bureaublad of mobiel
* De tijd van de gegevensverzameling, zoals: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* De URL van de pagina die wordt bezocht, bijvoorbeeld: `https://experienceleague.adobe.com/docs`
* De URL van de verwijzer (de URL van de pagina die aan de huidige pagina is gekoppeld, als de gebruiker een koppeling heeft gevolgd)
* Een willekeurig gegenereerde id van de paginaweergave, in een indeling die vergelijkbaar is met: `2Ac6`
* het gewicht of de omkering van de bemonsteringsfrequentie, zoals: `100`. Dit betekent dat slechts één op de honderd paginaweergaven wordt opgenomen
* Het controlepunt of de naam van een bepaalde gebeurtenis in de volgorde waarin de pagina wordt geladen of waarmee de gebeurtenis als bezoeker wordt gebruikt
* De bron, of herkenningsteken van het element DOM dat de gebruiker met voor het hierboven vermelde controlepunt in wisselwerking staat. Dit kan bijvoorbeeld een afbeelding zijn
* Het doel, of verbinding met een externe pagina of een middel dat de gebruiker met voor het hierboven vermelde controlepunt in wisselwerking staat. Bijvoorbeeld: `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* De prestatiemetriek van het Web van de Kern (CWV), de Grootste Inhoudelijke Verf (LCP), de Eerste Vertraging van de Input (FID), en Cumulatieve Verschuiving van de Lay-out (CLS) die de kwaliteit van de ervaring van de bezoeker beschrijven.

### Hoe te opstelling de Echte Dienst van de Controle van de Gebruiker {#how-to-set-up-the-rum-service}

* Als u wilt deelnemen aan ons programma voor vroege adoptie, kunt u een e-mail sturen naar `aemcs-rum-adopter@adobe.com`, samen met uw domeinnaam voor de productie-, stage- en ontwikkelomgeving via uw e-mailadres dat aan uw Adobe ID is gekoppeld. Het productteam van Adobe zal dan de Echte Dienst van Gegevens van de Controle van de Gebruiker (RUM) voor u toelaten.
* Zodra dit is voltooid, zal het productteam van Adobe een Kanaal van de Samenwerking van de Klant creëren.
* Het team van het Product van de Adobe zal naar u richten om u van de domeinsleutel en het gegevensdashboard URL te voorzien waar u de Mening van de Pagina kunt bekijken en [De Kernwebinstellingen (CWV)](https://web.dev/vitals/) metriek die door de cliënt-kant Echte de dienstinzameling van de Controle van de Gebruiker wordt verzameld.
* Vervolgens wordt u begeleid hoe u de domeinsleutel kunt gebruiken om toegang te krijgen tot de URL van het gegevensdashboard en de metriek te bekijken.

### Hoe de Echte Gegevens van de Dienst van de Controle van de Gebruiker worden gebruikt {#how-rum-service-data-is-being-used}

RUM-gegevens zijn nuttig voor de volgende doeleinden:

* Om prestatiesknelpunten voor klantenplaatsen te identificeren en te bevestigen
* Gestroomlijnd, automatisch verkeer rapporteert dat de Mening van de Pagina voor klanten gebruikend hun eigen CDN omvat, wat betekent zij geen verkeersrapport met Adobe moeten delen.
* Als u wilt begrijpen hoe Adobe Experience Manager werkt met andere scripts (zoals analyses, doelwitten of externe bibliotheken) op dezelfde pagina, kunt u de compatibiliteit verbeteren.

### Beperkingen en begrip van variatie in paginaweergaven en prestatiewaarden {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Aangezien u deze gegevens zult analyseren, zouden er misschien variaties in paginameningen en andere prestatiesmetriek kunnen zijn die door Reële Controle van de Gebruiker (RUM) worden gemeld. Deze variaties kunnen worden toegeschreven aan verschillende factoren die inherent zijn aan realtime bewaking aan de clientzijde. Hier zijn belangrijke overwegingen voor klanten om in mening te houden wanneer het interpreteren van hun gegevens RUM:

1. **Blokkeringen van Beheer**

   * Eindgebruikers die tracker blockers of privacyuitbreidingen gebruiken kunnen de gegevensinzameling van de Echte dienst van de Controle van de Gebruiker belemmeren, aangezien deze hulpmiddelen de uitvoering van de volgende manuscripten beperken. Deze beperking kan leiden tot ondergemelde paginaweergaven en gebruikersinteracties, waardoor een discrepantie ontstaat tussen de werkelijke siteactiviteit en de gegevens die door RUM worden vastgelegd.

1. **Beperkingen bij het vastleggen van API/JSON-aanroepen**

   * De de gegevensdienst van het RUM concentreert zich op de cliënt-zijervaring en vangt niet de achterste API of vraag JSON op dit ogenblik. De uitsluiting van deze vraag van de Echte de dienstgegevens van de Controle van de Gebruiker zal tot variaties van de inhoudsverzoeken leiden die door Analytics CDN worden gemeten.

### Veelgestelde vragen {#faq}

1. **Hoe kan ik wegen vormen om in controle te omvatten of uit te sluiten?**

   Klanten kunnen paden configureren om de URL&#39;s voor controle op te nemen of uit te sluiten door de omgevingsvariabelen in de configuratie in Cloud Manager in te stellen met behulp van de volgende variabelen: `AEM_WEBVITALS_EXCLUDE` en `AEM_WEBVITALS_INCLUDE_PATHS`

   Houd er rekening mee dat de instelling voor &#39;include&#39; standaard is ingesteld op target &#39;/content&#39;. Het is belangrijk om te herinneren dat de wegen u hier moet vormen inhoudswegen binnen het systeem, niet de wegen URL u in uw browser ziet. Dit onderscheid is zeer belangrijk voor nauwkeurige vestiging en het aanpassen van uw configuratie om aan uw specifieke behoeften te voldoen.

1. **Zou de Adobe alle paginameningen kunnen volgen alvorens de interactie klant beheerde CDN of op het punt bereikt wanneer de interactie de klant beheerde CDN bereikt?**

   Ja.

1. **Zullen klanten de dienstmanuscripten van de RUM van de gegevensdienst met derdesystemen zoals Dynatrace kunnen integreren?**

   Ja.

1. **Worden &quot;Interactie met volgende verf&quot;, &quot;Tijd tot eerste byte&quot; en &quot;Eerste contenteuze verf&quot; webvitals Metrics verzameld?**

   De interactie met volgende verf (INP) en Tijd aan eerste byte (TTFB) wordt verzameld.  De eerste inhoudelijke verf wordt momenteel niet verzameld.
