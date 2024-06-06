---
title: Real Use Monitoring for AEM as a Cloud Service
description: Leer hoe u Real Use Monitoring (RUM) gebruikt om de digitale gebruikerservaring van een website of toepassing in real-time vast te leggen en te analyseren.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
source-git-commit: 948eb304c17ad86dcbab2b0685428ae51f38f488
workflow-type: tm+mt
source-wordcount: '1409'
ht-degree: 0%

---

# Real Use Monitoring Service voor AEM as a Cloud Service {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!NOTE]
>
>We zijn erg blij om de [GA-rollout](/help/release-notes/release-notes-cloud/release-notes-current.md#real-use-monitoring) voor de Echte dienst van de Controle van het Gebruik, de cliënt-zijinzameling van gegevens. Het is een geautomatiseerde dienst en er is geen klantenopstelling vereist.

>[!INFO]
>
>Clientbewaking werkt alleen voor klanten met AEM Cloud Service-versie **2024 516461** en hoger.

## Overzicht {#overview}

De Real Use Monitoring-service (RUM) is een technologie voor het bewaken van de prestaties die de digitale gebruikerservaring van een website of toepassing in real-time vastlegt en analyseert. Het biedt inzicht in de real-time prestaties van een webtoepassing en biedt meer inzicht in de gebruikerservaring. &quot;Real User Monitoring&quot; is omgedoopt tot &quot;Real Use Monitoring&quot; omdat het beter de ware essentie van de service weerspiegelt, die gericht is op het optimaliseren van prestaties door het controleren van websiterelaties, in plaats van de gebruikers zelf.

Met RUM, worden de zeer belangrijke prestatiesmetriek van de inleiding van URL gevolgd tot het verzoek terug naar browser wordt gediend, die de ontwikkelaars allen helpt de toepassing verbeteren om het voor het eind gemakkelijk te gebruiken - gebruikers te maken.

## Wie kan profiteren van de werkelijk gebruikte bewakingsservice? {#who-can-benefit-from-rum-service}

De echte dienst van de Controle van het Gebruik is voordelig voor alle klanten. Deze weergave biedt een representatieve weergave van gebruikersinteracties en zorgt voor een betrouwbare maatstaf voor de betrokkenheid van websites door het aantal weergaven van de pagina&#39;s aan de clientzijde vast te leggen.

Voor alle klanten van de Adobe, verstrekt deze dienst waardevolle inzichten in gebruikersinteractie. De klanten die hun eigen CDN in dienst nemen, kunnen van vereenvoudigde verkeer profiteren rapportering, aangezien de Adobe nu direct de gegevensinzameling integreert, die de behoefte aan afzonderlijke rapporten tijdens vernieuwingscycli elimineert.

Wilt u het volledige potentieel van uw website ontgrendelen, met het visualisatieprogramma van de Verkenner van de Ouderwetse van de Ouderwetse van de Adobe om nuttige inzichten in uw websitebetrokkenheid te verkrijgen? Dit hulpmiddel kan inzichten in uw paginaprestaties, met inbegrip van metriek op het aantal kliks, de Kernsteden van het Web (CWV), omzettingen, en de kaarten van de klantenreis verstrekken. Door deze krachtige inzichten te gebruiken, kunt u uw digitale ervaringen verfijnen om effectiever aan de behoeften van uw gebruikers te voldoen. Als u meer wilt weten en toegang wilt krijgen, kunt u ons een e-mail sturen op `rum-explorer@adobe.com`.

## Begrijp hoe de Echte Dienst van de Controle van het Gebruik werkt {#understand-how-the-rum-service-works}

Adobe Experience Manager gebruikt Real Use Monitoring (RUM) om klanten en Adobe te helpen begrijpen hoe bezoekers met Adobe Experience Manager-sites communiceren, prestatieproblemen te diagnosticeren en de doeltreffendheid van experimenten te meten. RUM behoudt de privacy van bezoekers door middel van steekproeven - slechts een klein deel van alle paginameningen wordt gecontroleerd - en geen persoonlijk identificeerbare informatie (PII) wordt verzameld.

## Real Use Monitoring Service en Privacy {#rum-service-and-privacy}

De Echte dienst van de Controle van het Gebruik in Adobe Experience Manager wordt ontworpen om bezoekersprivacy te bewaren en gegevensinzameling te minimaliseren. Als bezoeker betekent dit dat er geen persoonlijke gegevens worden verzameld op de site die u bezoekt of ter beschikking van de Adobe worden gesteld.

Als plaatsexploitant, wordt geen extra opt-in vereist om controle door deze eigenschap toe te laten. Er is geen extra pop-up of toestemmingsvorm voor de eindgebruikers om voor het toelaten RUM goed te keuren.

## Bemonstering van gegevens van de bewakingsservice voor echt gebruik {#rum-service-data-sampling}

Traditionele webanalytische oplossingen proberen gegevens te verzamelen voor elke bezoeker. Met de Adobe Experience Manager-service RUM wordt alleen informatie uit een klein deel van de paginaweergaven vastgelegd. De dienst is bedoeld om te worden bemonsterd en geanonimiseerd in plaats van als vervanging voor analyses. Pagina&#39;s hebben standaard een bemonsteringsverhouding van 1:100. Site-operators kunnen de bemonsteringsfrequentie op dit moment niet verhogen of verlagen. Om totaal verkeer nauwkeurig te schatten, voor elke 100 paginameningen, worden de gegevens verzameld van 1, die u een betrouwbare benadering van algemeen verkeer geven.

Aangezien de beslissing of de gegevens worden verzameld, per paginaweergave wordt genomen, is het vrijwel onmogelijk interacties op meerdere pagina&#39;s bij te houden. RUM heeft standaard geen concept van bezoekers of sessies, alleen van paginaweergaven.

## Welke gegevens worden verzameld {#what-data-is-being-collected}

De Echte dienst van de Controle van het Gebruik wordt ontworpen om de inzameling van persoonlijk identificeerbare informatie te verhinderen. De volledige reeks informatie die door RUM kan worden verzameld, is hieronder vermeld:

* De hostnaam van de site die wordt bezocht, bijvoorbeeld: `experienceleague.adobe.com`
* Het brede type van gebruikersagent en werkend systeem dat wordt gebruikt om de pagina, zoals te tonen: `desktop:windows` of `mobile:ios`
* De tijd van de gegevensverzameling, zoals: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* De URL van de pagina die wordt bezocht, bijvoorbeeld: `https://experienceleague.adobe.com/docs`
* De URL van de verwijzer (de URL van de pagina die aan de huidige pagina is gekoppeld, als de gebruiker een koppeling heeft gevolgd)
* Een willekeurig gegenereerde id van de paginaweergave, in een indeling die vergelijkbaar is met: `2Ac6`
* het gewicht of de omkering van de bemonsteringsfrequentie, zoals: `100`. Dit betekent dat slechts één op de honderd paginaweergaven is opgenomen
* Het controlepunt of de naam van een bepaalde gebeurtenis in de volgorde waarin de pagina wordt geladen of waarmee de gebeurtenis als bezoeker wordt gebruikt
* De bron, of herkenningsteken van het element DOM dat de gebruiker met voor het hierboven vermelde controlepunt in wisselwerking staat. Dit kan bijvoorbeeld een afbeelding zijn
* Het doel, of verbinding met een externe pagina of een middel dat de gebruiker met voor het hierboven vermelde controlepunt in wisselwerking staat. Bijvoorbeeld: `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* De prestaties van de KernWeb van de Aanwezigen (CWV), met inbegrip van de Grootste Inhoudelijke Verf (LCP), de Eerste Vertraging van de Input (FID), Cumulatieve Verschuiving van de Lay-out (CLS), en Tijd aan Eerste Byte (TTFB) die de kwaliteit van de ervaring van de bezoeker beschrijven.

## Hoe de Echte Controle van het Gebruik voor een klant werkt {#how-rum-works-for-a-customer}

De echte Controle van het Gebruik controleert automatisch cliënt-zijverkeer om u van waardevolle inzichten te voorzien. Als klant van de Adobe, te hoeven u geen extra stappen te nemen, aangezien deze dienst naadloos in uw bestaande opstelling wordt geïntegreerd. Met de algemene implementatie van de beschikbaarheid (GA) profiteert u automatisch van deze nieuwe functie.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Hoe de Echte Gegevens van de Dienst van de Controle van het Gebruik worden gebruikt {#how-rum-service-data-is-being-used}

RUM-gegevens zijn nuttig voor de volgende doeleinden:

* Om prestatiesknelpunten voor klantenplaatsen te identificeren en te bevestigen
* Om geautomatiseerde verkeersraadpleging te stroomlijnen die de Mening van de Pagina omvat.
* Als u wilt begrijpen hoe Adobe Experience Manager werkt met andere scripts (zoals analyses, doelwitten of externe bibliotheken) op dezelfde pagina, kunt u de compatibiliteit verbeteren.

## Beperkingen en begrip van variatie in paginaweergaven en prestatiewaarden {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Tijdens het analyseren van RUM-gegevens kunnen er verschillen zijn in paginaweergaven en andere maatstaven voor prestaties. Deze variaties kunnen worden toegeschreven aan verschillende factoren die inherent zijn aan realtime bewaking aan de clientzijde. Hier zijn belangrijke overwegingen voor klanten om in mening te houden wanneer het interpreteren van hun gegevens RUM:

1. **Blockers van Beheer**

   * Eindgebruikers die tracker-blokkers of privacy-extensies gebruiken, kunnen het verzamelen van RUM-gegevens belemmeren, aangezien deze gereedschappen de uitvoering van trackingscripts beperken. Deze beperking kan leiden tot ondergemelde paginaweergaven en gebruikersinteracties, waardoor een discrepantie ontstaat tussen de werkelijke siteactiviteit en de gegevens die door RUM worden vastgelegd.

1. **Beperkingen bij het vastleggen van API/JSON-aanroepen zonder kop**

   * De RUM gegevensdienst concentreert zich op de cliënt-zijervaring en vangt niet de achterste API of vraag JSON die van een niet AEM headless app op dit ogenblik wordt gemaakt. De uitsluiting van deze vraag van de dienstgegevens van het RUM zal tot variaties van de inhoudsverzoeken leiden die door Analytics CDN worden gemeten.

## Veelgestelde vragen {#faq}


1. **Kunnen klanten de dienstmanuscripten RUM met derdesystemen zoals Dynatrace integreren?**

   Ja.

1. **Worden &quot;Interactie met volgende verf&quot;, &quot;Tijd tot eerste byte&quot; en &quot;Eerste contenteuze verf&quot; webvitals Metrics verzameld?**

   De interactie met volgende verf (INP) en Tijd aan eerste byte (TTFB) wordt verzameld.  De eerste inhoudelijke verf wordt momenteel niet verzameld.

1. **De `/.rum` Het pad is geblokkeerd op mijn site. Hoe los ik het op?**

   De `/.rum` De weg wordt vereist voor de inzameling van het RUM om te werken.  Als u een CDN vóór hebt wat de Adobe als deel van AEM as a Cloud Service verstrekt, moet u ervoor zorgen dat `/.rum` naar dezelfde AEM als de rest van de AEM.

1. **Telt de inzameling RUM op inhoudsverzoeken voor contractuele doeleinden?**

   Noch de bibliotheek RUM noch de inzameling RUM tellen als inhoudsverzoeken en zullen niet het gemelde aantal paginameningen of API vraag verhogen. Bovendien, voor klanten die uit-van-de-doos CDN met AEM as a Cloud Service gebruiken, [server-side verzameling](#serverside-collection) is de basis voor verzoeken om inhoud.

1. **Hoe kan ik me afmelden?**

   We raden u ten zeerste aan de Real Use Monitoring (RUM) te gebruiken vanwege de aanzienlijke voordelen ervan en om u in staat te stellen uw digitale ervaringen te optimaliseren. Het biedt waardevolle inzichten die de prestaties van uw website kunnen verbeteren. De service is ontworpen om naadloos te zijn en heeft geen invloed op de prestaties van uw website.

   Weigeren betekent dat je deze inzichten niet kunt gebruiken. Neem contact op met de ondersteuning van Adoben als er problemen optreden.
