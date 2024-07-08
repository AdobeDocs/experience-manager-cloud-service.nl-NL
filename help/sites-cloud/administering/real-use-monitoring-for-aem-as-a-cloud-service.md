---
title: Real Use Monitoring voor AEM als een cloudservice
description: Leer hoe u Real Use Monitoring (RUM) kunt gebruiken om de digitale gebruikerservaring van een website of toepassing in real-time vast te leggen en te analyseren.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
feature: Administering
role: Admin
source-git-commit: 8ccef0103ae7fb75171431eeb36f7352f6467d56
workflow-type: tm+mt
source-wordcount: '1302'
ht-degree: 0%

---

# Real Use Monitoring-service voor AEM als een cloudservice {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!NOTE]
>
>Real Use Monitoring service, de client-side verzameling van gegevens, is een geautomatiseerde service. Installatie van klanten is niet vereist.

>[!INFO]
>
>Bewaking aan clientzijde werkt alleen voor klanten met AEM Cloud-serviceversie **2024.5.16461** en hoger.

## Overzicht {#overview}

De service Real Use Monitoring (RUM) is een technologie voor prestatiecontrole die de digitale gebruikerservaringen van een website of toepassing in real-time vastlegt en analyseert. Deze functie biedt inzicht in de real-time prestaties van een webtoepassing en meer inzicht in de ervaring van de eindgebruiker. De service is gericht op het optimaliseren van de prestaties door websitebetrokkenheid te controleren in plaats van de gebruikers zelf.

Met RUM worden de belangrijkste prestatiegegevens bijgehouden vanaf het starten van de URL totdat de aanvraag wordt teruggestuurd naar de browser. Ontwikkelaars kunnen de toepassing verbeteren, zodat ze deze gemakkelijker kunnen gebruiken door de eindgebruikers.

>[!INFO]
>
>&quot;Real User Monitoring&quot; heeft een nieuwe naam gekregen in &quot;Real Use Monitoring&quot; omdat het de ware essentie van de service beter weerspiegelt.

## Wie kan profiteren van een monitoring service voor gebruik? {#who-can-benefit-from-rum-service}

De Real Use Monitoring service is gunstig voor alle klanten. Het biedt een representatieve weerspiegeling van gebruikersinteracties en zorgt voor een betrouwbare mate van websitebetrokkenheid door het aantal paginaweergaven aan de clientzijde vast te leggen.

Deze service biedt voor alle Adobe-klanten waardevolle inzichten in de interactie met de gebruiker. Klanten die hun eigen CDN gebruiken, kunnen profiteren van vereenvoudigde verkeersrapportage, aangezien Adobe de gegevensverzameling nu rechtstreeks integreert, waardoor afzonderlijke rapporten tijdens de verlengingscycli niet meer nodig zijn.

## Begrijpen hoe de Real Use Monitoring Service werkt {#understand-how-the-rum-service-works}

Adobe Experience Manager (AEM) gebruikt Real Use Monitoring (RUM) om klanten en Adobe te helpen begrijpen hoe bezoekers communiceren met AEM-sites. Het helpt hen prestatieproblemen te diagnosticeren en de effectiviteit van experimenten te meten. RUM behoudt de privacy van bezoekers door middel van sampling - slechts een klein deel van alle paginaweergaven wordt gecontroleerd - en er wordt geen persoonlijk identificeerbare informatie (PII) verzameld.

## Real Use Monitoring Service en Privacy {#rum-service-and-privacy}

De Real Use Monitoring-service in AEM is ontworpen om de privacy van bezoekers te beschermen en het verzamelen van gegevens tot een minimum te beperken. Als bezoeker betekent dit dat de site die u bezoekt of die beschikbaar is gesteld aan Adobe, geen persoonlijke informatie verzamelt.

Als site-operator is geen extra opt-in vereist om monitoring via deze functie mogelijk te maken. Er is geen extra pop-up- of toestemmingsformulier dat eindgebruikers kunnen accepteren voor het inschakelen van RUM.

## Gegevensmonsters van de monitoringdienst voor echt gebruik {#rum-service-data-sampling}

Traditionele webanalyseoplossingen proberen gegevens over elke bezoeker te verzamelen. De RUM-service van AEM legt alleen informatie vast van een klein gedeelte van de paginaweergaven. De service is bedoeld als monster en anonieme service, in plaats van een vervanging voor analyses. Pagina&#39;s hebben standaard een samplingverhouding van 1:100. Site-operatoren kunnen op dit moment de bemonsteringsfrequentie niet verhogen of verlagen. Om het totale verkeer nauwkeurig te schatten, worden voor elke 100 paginaweergaven gegevens verzameld van 1, zodat u een betrouwbare benadering van het totale verkeer krijgt.

Als de beslissing of de gegevens worden verzameld, wordt het gemaakt op basis van paginaweergave per paginaweergave en wordt het vrijwel onmogelijk om interacties op meerdere pagina&#39;s bij te houden. Rum heeft geen concept van bezoekers of sessies, alleen van paginaweergaven.

## Welke gegevens worden verzameld {#what-data-is-being-collected}

De Real Use Monitoring-service is ontworpen om het verzamelen van persoonlijk identificeerbare informatie te voorkomen. De volledige set met informatie die door RUM wordt verzameld, wordt hieronder vermeld:

* De hostnaam van de site die wordt bezocht, bijvoorbeeld: `experienceleague.adobe.com`
* Het brede gebruikersagenttype en het besturingssysteem waarmee de pagina wordt weergegeven, zoals: `desktop:windows` of `mobile:ios`
* Het tijdstip van de gegevensverzameling, zoals: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* De URL van de pagina die wordt bezocht, bijvoorbeeld: `https://experienceleague.adobe.com/docs`
* De verwijzings-URL (de URL van de pagina die gekoppeld is aan de huidige pagina, als de gebruiker een koppeling heeft gevolgd)
* Een willekeurig gegenereerde id van de paginaweergave, in een indeling die lijkt op: `2Ac6`
* De dikte of het omgekeerde van de bemonsteringssnelheid, zoals: `100`. Dit betekent dat er slechts één van de honderd paginaweergaven wordt geregistreerd
* Het controlepunt, of de naam van een bepaalde gebeurtenis in de volgorde waarin de pagina wordt geladen. Of interactie ermee als bezoeker
* De bron, of id, van het DOM-element waarmee de gebruiker communiceert voor het hierboven vermelde checkpoint. Het kan bijvoorbeeld een afbeelding zijn
* Het doelpunt of de koppeling naar een externe pagina of bron waarmee de gebruiker werkt voor het hierboven vermelde controlepunt. Bijvoorbeeld: `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* De prestatiegegevens van de Core Web Vitals (CWV), waaronder de LCP (Largest Contentful Paint, First Input Delay, FID), Cumulative Layout Shift (CLS) en Time To First Byte (TTFB), die de ervaringskwaliteit van de bezoeker beschrijven.

## Hoe Real Use Monitoring werkt voor een klant {#how-rum-works-for-a-customer}

Real Use Monitoring houdt automatisch het verkeer van klanten in de gaten om u waardevolle inzichten te geven. Als Adobe-klant hoeft u geen extra stappen te nemen, omdat deze service naadloos in uw bestaande configuratie kan worden geïntegreerd. Met de implementatie van de algemene beschikbaarheid profiteert u automatisch van deze nieuwe functie.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Hoe Real Use Monitoring Service Data worden gebruikt {#how-rum-service-data-is-being-used}

RUM-gegevens zijn nuttig voor de volgende doeleinden:

* Prestatieknelpunten voor klantsites identificeren en corrigeren
* Hiermee stroomlijnt u het automatisch opzoeken van verkeer met paginaweergaven.
* Om te begrijpen hoe AEM op dezelfde pagina omgaat met andere scripts (zoals analyses, targeting of externe bibliotheken), om de compatibiliteit te verbeteren.

## Beperkingen en inzicht in variatie in paginaweergaven en prestatiestatistieken {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Tijdens het analyseren van RUM-gegevens kunnen er verschillen zijn in de paginaweergaven en andere prestatiegegevens. Deze variatie kan worden toegeschreven aan verschillende factoren die inherent zijn aan real-time monitoring van de klant. Hier volgen de belangrijkste overwegingen waar klanten rekening mee moeten houden bij het interpreteren van hun RUM-gegevens:

1. **Blokkers voor Beheer**

   * Eindgebruikers die Tracker-blockers of privacy-extensies gebruiken, kunnen de verzameling van RUM-gegevens belemmeren, omdat deze tools de uitvoering van de trackingscripts beperken. Deze beperking kan leiden tot onderrapportage voor paginaweergaven en gebruikersinteracties, waardoor een discrepantie ontstaat tussen de werkelijke site-activiteit en de gegevens die zijn vastgelegd door RUM.

1. **Beperkingen bij het vastleggen van headless API/JSON-aanroepen**

   * RUM-dataservice richt zich op de client-side ervaring en legt de backend-API- of JSON-aanroepen die momenteel worden gemaakt vanuit een niet-AEM headless-app, niet vast. Dat deze aanroepen niet worden aangeroepen in RUM-servicegegevens, leidt tot verschillen met de inhoudsaanvragen die door CDN Analytics zijn gemeten.

## FAQ {#faq}


1. **Kunnen klanten de RUM-servicescripts integreren met systemen van derden, zoals Dynatrace?**

   Ja.

1. **Worden &quot;Interactie met volgende verf&quot;, &quot;Tijd tot eerste byte&quot; en &quot;Eerste contentful verf&quot; Web vitals Metrics verzameld?**

   De interactie tussen volgende verf (INP) en Time To First Byte (TTFB) wordt verzameld.  De eerste contentful verf wordt op dit moment niet verzameld.

1. **Het `/.rum` pad is geblokkeerd op mijn site. Hoe moet ik dit corrigeren?**

   Het `/.rum` pad is vereist om RUM-verzameling te gebruiken. Als u een CDN hebt vóór wat Adobe biedt als onderdeel van AEM als een Cloud-service, moet u ervoor zorgen dat het `/.rum` pad wordt doorsturen naar dezelfde AEM-oorsprong als de rest van uw AEM-inhoud. En zorg ervoor dat het op geen enkele manier wordt aangepast.

1. **Telt de RUM-verzameling mee voor inhoudsaanvragen voor contractuele doeleinden?**

   De RUM-bibliotheek en de RUM-verzameling worden niet als inhoudsaanvragen beschouwd en het gerapporteerde aantal paginaweergaven of API-aanroepen wordt niet verhoogd. Voor klanten die kant-en-klare CDN-bestanden met AEM as a Cloud Service gebruiken, [vormt deze verzameling](#serverside-collection) op de server de basis voor inhoudsaanvragen.

1. **Hoe kan ik me afmelden?**

   Adobe raadt het gebruik van Real Use Monitoring (RUM) aan vanwege de aanzienlijke voordelen ervan en dat u hiermee uw digitale ervaringen kunt optimaliseren. Dit kan waardevolle inzichten bieden die de websiteprestaties kunnen verbeteren. De service is ontworpen om naadloos te zijn en heeft geen invloed op de prestaties van uw website.

   Afmelden betekent dat je deze inzichten mist. Neem bij problemen echter contact op met de ondersteuning van Adobe.
