---
title: Real Use Monitoring voor AEM as a Cloud Service
description: Leer hoe u Real Use Monitoring (RUM) gebruikt om de digitale gebruikerservaring van een website of toepassing in real-time vast te leggen en te analyseren.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
feature: Administering
role: Admin
source-git-commit: 2515bc51fd54b014ffb701a8aef38cd08d6725b3
workflow-type: tm+mt
source-wordcount: '1274'
ht-degree: 0%

---

# Real Use Monitoring Service voor AEM as a Cloud Service {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!NOTE]
>
>De echte dienst van de Controle van het Gebruik, de cliënt-zijinzameling van gegevens, is de geautomatiseerde dienst. Er is geen installatie van de klant vereist.

>[!INFO]
>
>De controle van de cliënt-kant werkt slechts voor klanten met AEM (Adobe Experience Manager) versie van de Cloud Service **2024.5.16461** en hierboven.

## Overzicht {#overview}

De service RUM (Real Use Monitoring) is een technologie voor prestatiebewaking die de digitale gebruikerservaring van een website of toepassing in real-time vastlegt en analyseert. Het biedt inzicht in de real-time prestaties van een webtoepassing en biedt meer inzicht in de gebruikerservaring. De service richt zich op het optimaliseren van de prestaties door het controleren van websiteverbindingen in plaats van op de gebruikers zelf.

Met RUM, worden de zeer belangrijke prestatiesmetriek van de aanvang van URL gevolgd tot het verzoek aan browser wordt teruggegeven. Ontwikkelaars kunnen de toepassing verbeteren, zodat deze eenvoudig kan worden gebruikt voor eindgebruikers.

>[!INFO]
>
>&quot;Real User Monitoring&quot; is hernoemd naar &quot;Real Use Monitoring&quot;, omdat het de ware essentie van de service beter weerspiegelt.

## Wie kan van de Echte dienst van de Controle van het Gebruik profiteren? {#who-can-benefit-from-rum-service}

AEM heeft RUM ontwikkeld om klanten en Adobe te helpen begrijpen hoe bezoekers met AEM sites communiceren. RUM kan worden gebruikt om prestatieproblemen te diagnostiseren en de doeltreffendheid van experimenten te meten. RUM behoudt de privacy van bezoekers door middel van steekproeven - slechts een klein deel van alle paginameningen wordt gecontroleerd - en geen persoonlijk identificeerbare informatie (PII) wordt verzameld.


## Begrijp hoe de Echte dienst van de Controle van het Gebruik werkt {#understand-how-the-rum-service-works}

AEM gebruikt RUM om klanten en Adobe te helpen begrijpen hoe de bezoekers met AEM plaatsen in wisselwerking staan. Het helpt hen prestatieskwesties diagnostiseren, en de doeltreffendheid van experimenten meten. RUM behoudt de privacy van bezoekers door middel van steekproeven - slechts een klein deel van alle paginameningen wordt gecontroleerd - en geen persoonlijk identificeerbare informatie (PII) wordt verzameld.

## Real Use Monitoring Service en privacy {#rum-service-and-privacy}

De Echte dienst van de Controle van het Gebruik in AEM wordt ontworpen om bezoekersprivacy te bewaren en gegevensinzameling te minimaliseren. Als bezoeker betekent dit dat de site die u bezoekt of ter beschikking van de Adobe wordt gesteld, geen persoonlijke gegevens verzamelt.

Als plaatsexploitant, wordt geen extra opt-in vereist om controle door deze eigenschap toe te laten. Er is geen extra pop-up of toestemmingsvorm voor de eindgebruikers om voor het toelaten RUM goed te keuren.

## Bemonstering van gegevens van de bewakingsservice &quot;Real Use Monitoring&quot; {#rum-service-data-sampling}

Traditionele webanalytische oplossingen proberen gegevens te verzamelen voor elke bezoeker. AEM de dienst RUM vangt slechts informatie van een klein fractie van paginameningen. De dienst is bedoeld om te worden bemonsterd en geanonimiseerd in plaats van als vervanging voor analyses. Pagina&#39;s hebben standaard een bemonsteringsverhouding van 1:100. Site-operators kunnen de bemonsteringsfrequentie op dit moment niet verhogen of verlagen. Om totaal verkeer nauwkeurig te schatten, voor elke 100 paginameningen, worden de gegevens verzameld van 1, die u een betrouwbare benadering van algemeen verkeer geven.

Als u besluit of de gegevens worden verzameld, wordt deze per pagina weergegeven en is het vrijwel onmogelijk interacties op meerdere pagina&#39;s bij te houden. RUM heeft standaard geen concept van bezoekers of sessies, alleen van paginaweergaven.

## Welke gegevens worden verzameld? {#what-data-is-being-collected}

De Echte dienst van de Controle van het Gebruik wordt ontworpen om de inzameling van persoonlijk identificeerbare informatie te verhinderen. De volledige door het RUM verzamelde informatie wordt hieronder weergegeven:

* De hostnaam van de site die wordt bezocht, bijvoorbeeld: `experienceleague.adobe.com`
* Het brede type gebruikersagent en besturingssysteem dat wordt gebruikt om de pagina weer te geven, zoals: `desktop:windows` of `mobile:ios`
* De tijd van de gegevensverzameling, zoals: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* De URL van de pagina die wordt bezocht, bijvoorbeeld: `https://experienceleague.adobe.com/docs`
* De URL van de verwijzer (de URL van de pagina die aan de huidige pagina is gekoppeld, als de gebruiker een koppeling heeft gevolgd)
* Een willekeurig gegenereerde id van de paginaweergave, in een indeling die vergelijkbaar is met: `2Ac6`
* Het gewicht of het omgekeerde van de bemonsteringsfrequentie, bijvoorbeeld: `100` . Dit betekent dat slechts één op de honderd paginaweergaven wordt opgenomen
* Het controlepunt, of de naam, van een bepaalde gebeurtenis in de volgorde waarin de pagina wordt geladen. Of, interactie met het als bezoeker
* De bron, of id, van het DOM-element waarmee de gebruiker werkt voor het hierboven vermelde controlepunt. Het kan bijvoorbeeld een afbeelding zijn
* Het doel, of verbinding met een externe pagina of een middel dat de gebruiker met voor het hierboven vermelde controlepunt in wisselwerking staat. Bijvoorbeeld: `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* De prestaties van de KernWeb van de Aanwezigen (CWV), met inbegrip van de Grootste Inhoudelijke Verf (LCP), de Eerste Vertraging van de Input (FID), Cumulatieve Verschuiving van de Lay-out (CLS), en Tijd aan Eerste Byte (TTFB) die de kwaliteit van de ervaring van de bezoeker beschrijven.

## Hoe de Echte Controle van het Gebruik voor een klant werkt {#how-rum-works-for-a-customer}

De echte Controle van het Gebruik controleert automatisch cliënt-zijverkeer om u van waardevolle inzichten te voorzien. Als klant van de Adobe, te hoeven u geen extra stappen te nemen, aangezien deze dienst naadloos in uw bestaande opstelling wordt geïntegreerd. Met de algemene beschikbaarheid (GA)-implementatie profiteert u automatisch van deze nieuwe functie.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Hoe de Echte gegevens van de Dienst van de Controle van het Gebruik worden gebruikt {#how-rum-service-data-is-being-used}

RUM-gegevens zijn nuttig voor de volgende doeleinden:

* Om prestatiesknelpunten voor klantenplaatsen te identificeren en te bevestigen
* Om geautomatiseerde verkeersraadpleging te stroomlijnen die paginameningen omvat.
* Als u wilt begrijpen hoe AEM met andere scripts (zoals analyses, doelwitten of externe bibliotheken) op dezelfde pagina werkt, vergroot u de compatibiliteit.

## Beperkingen en begrip van verschillen in paginaweergaven en prestatiemetriek {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Tijdens het analyseren van RUM-gegevens kunnen er verschillen zijn in paginaweergaven en andere maatstaven voor prestaties. Deze variaties kunnen worden toegeschreven aan verschillende factoren die inherent zijn aan realtime bewaking aan de clientzijde. Hier zijn belangrijke overwegingen voor klanten om in mening te houden wanneer het interpreteren van hun gegevens RUM:

1. **de blokkeerders van de Trekker**

   * Eindgebruikers die tracker-blokkers of privacy-extensies gebruiken, kunnen het verzamelen van RUM-gegevens belemmeren, aangezien deze gereedschappen de uitvoering van trackingscripts beperken. Deze beperking kan leiden tot ondergemelde paginaweergaven en gebruikersinteracties, waardoor een discrepantie ontstaat tussen de werkelijke siteactiviteit en de gegevens die door RUM worden vastgelegd.

1. **Beperkingen in het vangen van hoofd API/JSON vraag**

   * De RUM gegevensdienst concentreert zich op de cliënt-zijervaring en vangt niet de achterste API of vraag JSON die van een niet AEM headless app op dit ogenblik wordt gemaakt. De uitsluiting van deze vraag van de dienstgegevens van het RUM leidt tot variaties van de inhoudsverzoeken die door Analytics CDN worden gemeten.

## Veelgestelde vragen {#faq}


1. **kunnen de klanten de de dienstmanuscripten van RUM met derdesystemen zoals Dynatrace integreren?**

   Ja.

1. **zijn &quot;Interactie aan volgende verf,&quot;Tijd aan eerste byte,&quot;en &quot;Eerste contenteuze verf&quot;Metriek van het Web dat wordt verzameld?**

   De interactie met volgende verf (INP) en Tijd aan Eerste Byte (TTFB) wordt verzameld.  De eerste inhoudelijke verf wordt momenteel niet verzameld.

1. **de `/.rum` weg wordt geblokkeerd op mijn plaats, hoe zou ik moeten bevestigen?**

   De weg `/.rum` wordt vereist voor de inzameling van het RUM om te werken. Als u een CDN gebruikt vóór de AEM as a Cloud Service van de Adobe, zorg ervoor dat de `/.rum` weg naar de zelfde AEM oorsprong zoals uw andere AEM inhoud door:sturen. En zorg ervoor dat het op geen enkele manier wordt aangepast.

1. **telt de inzamelingstelling RUM naar inhoudsverzoeken voor contractuele doeleinden?**

   De bibliotheek RUM en de inzameling RUM tellen niet als inhoudsverzoeken en verhogen niet het gemelde aantal paginameningen of API vraag. Bovendien, voor klanten die uit-van-de-doos CDN met AEM as a Cloud Service gebruiken, [ server-kant inzameling ](#serverside-collection) is de basis voor inhoudverzoeken.

1. **Hoe kan ik opteren?**

   Adobe raadt u aan de Real Use Monitoring (RUM) te gebruiken vanwege de grote voordelen ervan en om uw digitale ervaringen te optimaliseren. Het biedt waardevolle inzichten die de prestaties van websites kunnen verbeteren. De service is ontworpen om naadloos te zijn en heeft geen invloed op de prestaties van uw website.

   Weigeren betekent dat deze inzichten ontbreken. Als u echter problemen ondervindt, neemt u contact op met de ondersteuning van Adoben.
