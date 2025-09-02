---
title: Operationele telemetrie voor AEM as a Cloud Service
description: Leer over Operationele Telemetrie, een geautomatiseerde dienst die toestaat om de cliënt-zijinzameling van gegevens te controleren.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
feature: Administering
role: Admin
source-git-commit: d02569f5fcca0e53c8f258be8a193663364ac31f
workflow-type: tm+mt
source-wordcount: '1134'
ht-degree: 0%

---

# Operationele telemetrieservice voor AEM as a Cloud Service {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!NOTE]
>
>De operationele dienst van Telemetrie, de cliënt-zijinzameling van gegevens, is een geautomatiseerde dienst. Er is geen installatie van de klant vereist.

>[!INFO]
>
>De controle van de cliënt-kant werkt slechts voor klanten met de versie van AEM (Adobe Experience Manager) Cloud Service **2024.5.16461** en hierboven.

## Overzicht {#overview}

De Operationele dienst van de Telemetrie is een prestatiescontroletechnologie die het cliënt-zijverkeer op een website of een toepassing in real time controleert. Deze service richt zich op het verzamelen van meetgegevens en gegevens die van essentieel belang zijn voor het optimaliseren van de prestaties door het controleren van websiteafspraken, in plaats van de gebruikers zelf. Met Operationele Telemetrie, worden de zeer belangrijke prestatiesmetriek gevolgd van de initialisering van URL tot het verzoek terug naar browser wordt gediend.

## Wie kan van de Operationele dienst van de Telemetrie profiteren? {#who-can-benefit-from-operational-telemetry-service}

Met Operationele Telemetrie kunnen klanten en Adobe begrijpen hoe eindgebruikers met AEM-sites werken. Met Operationele telemetrie blijft de privacy van bezoekers behouden door beperkte gegevensverzameling en -bemonstering. Slechts een klein deel van alle paginaweergaven wordt gecontroleerd.

## Gegevensbemonstering van de operationele telemetrieservice {#operational-telemetry-service-data-sampling}

Traditionele webanalytische oplossingen proberen gegevens te verzamelen voor elke bezoeker. De AEM-service Operationele telemetrie legt alleen informatie van een klein deel van de paginaweergaven vast. De dienst is bedoeld om te worden bemonsterd en geanonimiseerd in plaats van als vervanging voor analyses. Pagina&#39;s hebben standaard een bemonsteringsverhouding van 1 :100 . Site-operators kunnen de bemonsteringsfrequentie op dit moment niet verhogen of verlagen. Om totaal verkeer nauwkeurig te schatten, voor elke 100 paginameningen, worden de gegevens verzameld van 1, die u een betrouwbare benadering van algemeen verkeer geven.

Als u besluit of de gegevens worden verzameld, wordt deze per pagina weergegeven en is het vrijwel onmogelijk interacties op meerdere pagina&#39;s bij te houden. Operationele telemetrie heeft door ontwerp geen concept van bezoekers of sessies, alleen van paginaweergaven.

## Welke gegevens worden verzameld? {#what-data-is-being-collected}

De operationele dienst van de Telemetrie wordt ontworpen om gegevensinzameling te minimaliseren. De volledige verzameling informatie die door Operationele Telemetrie wordt verzameld, wordt hieronder weergegeven:

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
* De {(CWV) [ prestatiesmetriek 1} van het Web van de Kern ](https://web.dev/articles/lcp) Grootste Voorwaardelijke Verf (LCP) [, ](https://web.dev/articles/lcp) Interactie aan Volgende Verf (INP) [ en ](https://web.dev/articles/inp) Cumulatieve Verschuiving van de Lay-out (CLS) [ die de kwaliteit van de bezoeker van ervaring beschrijven.](https://web.dev/articles/cls)

## Hoe de Operationele Telemetrie voor een klant werkt {#how-operational-telemetry-works-for-a-customer}

Operationele telemetrie bewaakt automatisch het clientverkeer. Als Adobe-klant hoeft u geen aanvullende stappen te ondernemen, aangezien deze service naadloos in uw bestaande installatie is geïntegreerd. Met de operationele dienst van de Telemetrie die algemeen beschikbaar is, profiteert u automatisch van deze nieuwe eigenschap. De operationele dienst van Telemetrie stelt geen klant bloot die metriek vandaag onder ogen ziet om te controleren. We werken eraan om deze functionaliteit zo snel mogelijk aan u te leveren.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Hoe Adobe operationele telemetrie gebruikt {#how-operational-telemetry-data-is-being-used}

Operationele telemetriegegevens worden gebruikt voor de volgende doeleinden:

* Om prestatiesknelpunten voor klantenplaatsen te identificeren en te bevestigen
* Als u wilt begrijpen hoe AEM op dezelfde pagina werkt met andere scripts (zoals analyses, doelbibliotheken of externe bibliotheken), vergroot u de compatibiliteit.
<!--
## Limitations and understanding variance in page views and performance metrics {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Here are key considerations for customers to keep in mind when interpreting their Operational Telemetry data:

1. **Tracker blockers**

   * End-users employing tracker blockers or privacy extensions can impede Operational Telemetry data collection, as these tools restrict the tracking scripts' execution. This restriction may lead to underreported page views and user interactions, creating a discrepancy between actual site activity and the data captured by Operational Telemetry.

1. **Limitations in capturing headless API/JSON calls**

   * Operational Telemetry data service focuses on the client-side experience and doesn't capture the backend API or JSON calls made from a non-AEM headless app at this time. The exclusion of these calls from Operational Telemetry service data creates variances from the content requests measured by CDN Analytics.
-->

## Veelgestelde vragen {#faq}

<!-- REMOVED THIS FAQ AS PER EMAIL REQUEST FROM SHWETA DUA, SEPTEMBER 4, 2024 TO THE DL-AEM-DOCS GROUP 
1. **Can customers integrate the Operational Telemetry service scripts with third-party systems like Dynatrace?**

   Yes.
-->

1. **zijn &quot;Interactie aan volgende verf,&quot;Tijd aan eerste byte,&quot;en &quot;Eerste contenteuze verf&quot;metriek die worden verzameld?**

   De interactie met volgende verf (INP) en Tijd aan Eerste Byte (TTFB) wordt verzameld.  De eerste inhoudelijke verf wordt momenteel niet verzameld.

1. **de `/.rum` weg wordt geblokkeerd op mijn plaats, hoe zou ik moeten bevestigen?**

   Het pad `/.rum` is vereist voor de operationele Telemetrieverzameling. Als u een CDN vóór Adobe AEM as a Cloud Service gebruikt, moet u ervoor zorgen dat het `/.rum` -pad naar dezelfde AEM-oorsprong wordt doorgestuurd als de andere AEM-inhoud. En zorg ervoor dat het op geen enkele manier wordt aangepast. Alternatief, kunt u de gastheer veranderen die voor Operationele Telemetrie aan `rum.hlx.page` moet worden gebruikt door [ het plaatsen van een milieu variabele in Cloud Manager ](/help/implementing/cloud-manager/environment-variables.md#add-variables) genoemd `AEM_OPTEL_EXTERNAL` aan de waarde `true`. Als u terug naar zelfde domeinverzoeken op een recentere punt wilt veranderen, verwijder eenvoudig die omgevingsvariabele opnieuw.

1. **telt de Operationele inzameling van Telemetrie naar inhoudsverzoeken voor contractuele doeleinden?**

   De operationele telemetriebibliotheek en de operationele telemetrieverzameling tellen niet als inhoudsverzoeken en verhogen het gerapporteerde aantal paginaweergaven of API-aanroepen niet. Bovendien, voor klanten die uit-van-de-doos CDN met AEM as a Cloud Service gebruiken, [ server-kant inzameling ](#serverside-collection) is de basis voor inhoudverzoeken.

1. **hoe kan ik Operationele Telemetrie onbruikbaar maken?**

   Adobe raadt u aan de operationele telemetrie te gebruiken vanwege de aanzienlijke voordelen ervan en om Adobe in staat te stellen uw digitale ervaringen te optimaliseren door de prestaties van de website te verbeteren. De service is ontworpen om naadloos te zijn en heeft geen invloed op de prestaties van uw website.

   Weigeren kan betekenen dat er een kans ontbreekt om de betrokkenheid van het verkeer op uw website te verbeteren. Nochtans, als u om het even welke kwesties ontmoet, kunt u Operationele Telemetrie onbruikbaar maken door [ het plaatsen van een milieu variabele in Cloud Manager ](/help/implementing/cloud-manager/environment-variables.md#add-variables) genoemd `AEM_OPTEL_DISABLED` aan de waarde `true`. Als u Operationele Telemetrie op een later punt opnieuw wilt toelaten, verwijder eenvoudig die omgevingsvariabele opnieuw.

1. **Kan ik een beleid voor inhoudsbeveiliging gebruiken met één keer?

   De ondersteuning voor Operationele telemetrie bevat een experimentele functie ter ondersteuning van een beleid voor inhoudsbeveiliging met een nonce. Deze eigenschap kan worden toegelaten door [ plaatsend een milieu variabele in Cloud Manager ](/help/implementing/cloud-manager/environment-variables.md#add-variables) genoemd `AEM_OPTEL_NONCE` aan de waarde `true`. Als u dit later opnieuw wilt uitschakelen, verwijdert u gewoon de omgevingsvariabele opnieuw.

   Neem contact op met Adobe Support als er problemen optreden met deze functie.

1. **Hoe kan ik Operationele Telemetrie slechts voor bepaalde pagina&#39;s toelaten?**

   De operationele telemetrie wordt standaard ingeschakeld voor alle pagina&#39;s onder de map `/content` in de opslagplaats. Door [ te plaatsen zal een milieu variabele in Cloud Manager ](/help/implementing/cloud-manager/environment-variables.md#add-variables) genoemd `AEM_OPTEL_INCLUDED_PATHS` aan een lijst van komma-afzonderlijke wegen in de bewaarplaats, Operationele Telemetrie slechts voor die pagina&#39;s worden toegelaten. Daarnaast kunt u `AEM_OPTEL_EXCLUDED_PATHS` instellen op een lijst met paden in de repository die worden uitgesloten. Met de combinatie van deze twee instellingen kunt u de opname van Operationele Telemetrie aanpassen aan uw vereisten.

