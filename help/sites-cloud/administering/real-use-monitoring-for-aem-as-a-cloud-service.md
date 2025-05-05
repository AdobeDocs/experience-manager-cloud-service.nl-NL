---
title: Real Use Monitoring voor AEM as a Cloud Service
description: Leer over de Controle van het Echte Gebruik (RUM), een geautomatiseerde dienst die toestaat om de cliënt-zijinzameling van gegevens te controleren.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
feature: Administering
role: Admin
source-git-commit: f3091a3868ac57150afd6f1640709ce3e9566bac
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 0%

---

# Real Use Monitoring Service voor AEM as a Cloud Service {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!NOTE]
>
>De echte dienst van de Controle van het Gebruik, de cliënt-zijinzameling van gegevens, is de geautomatiseerde dienst. Er is geen installatie van de klant vereist.

>[!INFO]
>
>De controle van de cliënt-kant werkt slechts voor klanten met de versie van AEM (Adobe Experience Manager) Cloud Service **2024.5.16461** en hierboven.

## Overzicht {#overview}

De RUM-service (Real Use Monitoring) is een prestatiebewakingstechnologie die het client-side verkeer op een website of een toepassing in real-time controleert. Deze service richt zich op het verzamelen van meetgegevens en gegevens die van essentieel belang zijn voor het optimaliseren van de prestaties door het controleren van websiteafspraken, in plaats van de gebruikers zelf. Met RUM, worden de zeer belangrijke prestatiesmetriek van de aanvang van URL gevolgd tot het verzoek aan browser wordt teruggegeven.

## Wie kan van de Echte dienst van de Controle van het Gebruik profiteren? {#who-can-benefit-from-rum-service}

Real Use Monitoring helpt klanten en Adobe te begrijpen hoe eindgebruikers met AEM-sites werken. Met Real Use Monitoring blijft de privacy van bezoekers behouden door beperkte gegevensverzameling en -sampling. Slechts een klein deel van alle paginaweergaven wordt gecontroleerd.

## Bemonstering van gegevens van de bewakingsservice &quot;Real Use Monitoring&quot; {#rum-service-data-sampling}

Traditionele webanalytische oplossingen proberen gegevens te verzamelen voor elke bezoeker. Met de AEM-service Real Use Monitoring (RUM) wordt alleen informatie uit een klein deel van de paginaweergaven vastgelegd. De dienst is bedoeld om te worden bemonsterd en geanonimiseerd in plaats van als vervanging voor analyses. Pagina&#39;s hebben standaard een bemonsteringsverhouding van 1:100. Site-operators kunnen de bemonsteringsfrequentie op dit moment niet verhogen of verlagen. Om totaal verkeer nauwkeurig te schatten, voor elke 100 paginameningen, worden de gegevens verzameld van 1, die u een betrouwbare benadering van algemeen verkeer geven.

Als u besluit of de gegevens worden verzameld, wordt deze per pagina weergegeven en is het vrijwel onmogelijk interacties op meerdere pagina&#39;s bij te houden. RUM heeft standaard geen concept van bezoekers of sessies, alleen van paginaweergaven.

## Welke gegevens worden verzameld? {#what-data-is-being-collected}

De Echte dienst van de Controle van het Gebruik wordt ontworpen om gegevensinzameling te minimaliseren. De volledige door het RUM verzamelde informatie wordt hieronder weergegeven:

* De hostnaam van de site die wordt bezocht, bijvoorbeeld: `experienceleague.adobe.com`
* Het brede type gebruikersagent en besturingssysteem dat wordt gebruikt om de pagina weer te geven, zoals: `desktop:windows` of `mobile:ios`
* De tijd van de gegevensverzameling, zoals: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* De URL van de pagina die wordt bezocht, bijvoorbeeld: `https://experienceleague.adobe.com/docs?lang=nl-NL`
* De URL van de verwijzer (de URL van de pagina die aan de huidige pagina is gekoppeld, als de gebruiker een koppeling heeft gevolgd)
* Een willekeurig gegenereerde id van de paginaweergave, in een indeling die vergelijkbaar is met: `2Ac6`
* Het gewicht of het omgekeerde van de bemonsteringsfrequentie, bijvoorbeeld: `100` . Dit betekent dat slechts één op de honderd paginaweergaven wordt opgenomen
* Het controlepunt, of de naam, van een bepaalde gebeurtenis in de volgorde waarin de pagina wordt geladen. Of, interactie met het als bezoeker
* De bron, of id, van het DOM-element waarmee de gebruiker werkt voor het hierboven vermelde controlepunt. Het kan bijvoorbeeld een afbeelding zijn
* Het doel, of verbinding met een externe pagina of een middel dat de gebruiker met voor het hierboven vermelde controlepunt in wisselwerking staat. Bijvoorbeeld: `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* De {(CWV) [&#128279;](https://web.dev/articles/lcp) prestatiesmetriek 1} van het Web van de Kern [ Grootste Voorwaardelijke Verf (LCP) ](https://web.dev/articles/lcp), [ Interactie aan Volgende Verf (INP) ](https://web.dev/articles/inp) en [ Cumulatieve Verschuiving van de Lay-out (CLS) ](https://web.dev/articles/cls) die de kwaliteit van de bezoeker van ervaring beschrijven.

## Hoe de Echte Controle van het Gebruik voor een klant werkt {#how-rum-works-for-a-customer}

De echte Controle van het Gebruik controleert automatisch cliënt-zijverkeer. Als Adobe-klant hoeft u geen aanvullende stappen te ondernemen, aangezien deze service naadloos in uw bestaande installatie is geïntegreerd. Met de Echte dienst van de Controle van het Gebruik (RUM) die algemeen beschikbaar is, profiteert u automatisch van deze nieuwe eigenschap. De echte dienst van de Controle van het Gebruik stelt geen klant bloot die metriek vandaag onder ogen ziet om te controleren. We werken eraan om deze functionaliteit zo snel mogelijk aan u te leveren.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Hoe Adobe Real Use Monitoring gebruikt {#how-rum-data-is-being-used}

Reëel gebruik de Gegevens van de Controle worden gebruikt voor de volgende doeleinden:

* Om prestatiesknelpunten voor klantenplaatsen te identificeren en te bevestigen
* Als u wilt begrijpen hoe AEM op dezelfde pagina werkt met andere scripts (zoals analyses, doelbibliotheken of externe bibliotheken), vergroot u de compatibiliteit.
<!--
## Limitations and understanding variance in page views and performance metrics {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Here are key considerations for customers to keep in mind when interpreting their RUM data:

1. **Tracker blockers**

   * End-users employing tracker blockers or privacy extensions can impede RUM data collection, as these tools restrict the tracking scripts' execution. This restriction may lead to underreported page views and user interactions, creating a discrepancy between actual site activity and the data captured by RUM.

1. **Limitations in capturing headless API/JSON calls**

   * RUM data service focuses on the client-side experience and doesn't capture the backend API or JSON calls made from a non-AEM headless app at this time. The exclusion of these calls from RUM service data creates variances from the content requests measured by CDN Analytics.
-->

## Veelgestelde vragen {#faq}

<!-- REMOVED THIS FAQ AS PER EMAIL REQUEST FROM SHWETA DUA, SEPTEMBER 4, 2024 TO THE DL-AEM-DOCS GROUP 
1. **Can customers integrate the RUM service scripts with third-party systems like Dynatrace?**

   Yes.
-->

1. **zijn &quot;Interactie aan volgende verf,&quot;Tijd aan eerste byte,&quot;en &quot;Eerste contenteuze verf&quot;metriek die worden verzameld?**

   De interactie met volgende verf (INP) en Tijd aan Eerste Byte (TTFB) wordt verzameld.  De eerste inhoudelijke verf wordt momenteel niet verzameld.

1. **de `/.rum` weg wordt geblokkeerd op mijn plaats, hoe zou ik moeten bevestigen?**

   De weg `/.rum` wordt vereist voor de inzameling van het RUM om te werken. Als u een CDN vóór Adobe AEM as a Cloud Service gebruikt, moet u ervoor zorgen dat het `/.rum` -pad naar dezelfde AEM-oorsprong wordt doorgestuurd als de andere AEM-inhoud. En zorg ervoor dat het op geen enkele manier wordt aangepast.

1. **telt de inzamelingstelling RUM naar inhoudsverzoeken voor contractuele doeleinden?**

   De bibliotheek RUM en de inzameling RUM tellen niet als inhoudsverzoeken en verhogen niet het gemelde aantal paginameningen of API vraag. Bovendien, voor klanten die uit-van-de-doos CDN met AEM as a Cloud Service gebruiken, [ server-kant inzameling ](#serverside-collection) is de basis voor inhoudverzoeken.

1. **hoe kan ik RUM onbruikbaar maken?**

   Adobe raadt aan om de Real Use Monitoring (RUM) te gebruiken vanwege de aanzienlijke voordelen ervan en om Adobe in staat te stellen uw digitale ervaringen te optimaliseren door de prestaties van websites te verbeteren. De service is ontworpen om naadloos te zijn en heeft geen invloed op de prestaties van uw website.

   Weigeren kan betekenen dat er een kans ontbreekt om de betrokkenheid van het verkeer op uw website te verbeteren. Neem contact op met Adobe Support als er problemen optreden.