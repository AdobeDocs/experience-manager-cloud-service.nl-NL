---
title: Caching en prestaties
description: Leer over de verschillende beschikbare configuraties om GraphQL en inhoud het in cache plaatsen toe te laten om de prestaties van uw handelsimplementatie te optimaliseren.
exl-id: 21ccdab8-4a2d-49ce-8700-2cbe129debc6
feature: Commerce Integration Framework
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 0%

---

# Caching en prestaties {#caching}

## Component &amp; GraphQL Response Caching {#graphql}

De AEM CIF Core Components hebben al ingebouwde ondersteuning voor het in cache plaatsen van GraphQL-reacties voor afzonderlijke componenten. Deze functie kan worden gebruikt om het aantal GraphQL backend vraag met een grote factor te verminderen. Een efficiënte caching kan vooral voor het herhalen van vragen zoals het terugwinnen van de categorieboom voor een navigatiecomponent of het halen van alle beschikbare samenvoegingen/facetwaarden worden bereikt die op de productonderzoek en categoriepagina&#39;s worden getoond.

Voor de AEM CIF de Componenten van de Kern, wordt het in cache plaatsen gevormd op componentenbasis, zodat is het mogelijk om te controleren als (en hoe lang) de verzoeken/de reacties van GraphQL voor elke component in het voorgeheugen worden opgeslagen. Het is ook mogelijk om het caching gedrag voor de diensten te bepalen OSGi gebruikend de cliënt van GraphQL.

### Configuratie {#configuration}

Zodra gevormd voor een bepaalde component, begint het geheime voorgeheugen GraphQL vragen en antwoorden zoals die door elke ingang van de geheim voorgeheugenconfiguratie worden bepaald op te slaan. De grootte van het geheime voorgeheugen en de in het voorgeheugen onderbrengingsduur van elke ingang wordt bepaald op een projectbasis, die, bijvoorbeeld op het volgende afhangt:

* Hoe vaak de catalogusgegevens kunnen veranderen.
* Hoe kritiek het is dat een component altijd de recentste mogelijke gegevens, etc. toont.

Er is geen cachevervalsing, dus wees voorzichtig wanneer het plaatsen van de geheim voorgeheugenduur.

Wanneer het vormen caching voor componenten, moet de geheim voorgeheugennaam de naam van zijn **proxy** componenten die u in uw project definieert.

Voordat de client een GraphQL-aanvraag verzendt, wordt gecontroleerd of **exact** dezelfde GraphQL-aanvraag is al in de cache opgeslagen en retourneert mogelijk de in de cache opgeslagen reactie. Om overeen te komen, de GraphQL-aanvraag _moet_ exact overeenkomen. Dat wil zeggen: de query, de naam van de bewerking (indien aanwezig), variabelen (indien aanwezig) _moet_ allen zijn gelijk aan het caching verzoek. En alle aangepaste HTTP-headers die kunnen worden ingesteld _moet_ ook hetzelfde zijn. De Adobe Commerce `Store` header _moet_ match.

### Voorbeelden {#examples}

De Adobe adviseert dat u wat caching voor de onderzoeksdienst vormt die alle beschikbare samenvoegingen/facetwaarden haalt die op het productonderzoek en categoriepagina&#39;s worden getoond. Deze waarden veranderen doorgaans alleen wanneer een nieuw kenmerk aan producten wordt toegevoegd, bijvoorbeeld. De duur van deze cachevermelding kan dus &#39;groot&#39; zijn als de set met productkenmerken niet vaak wordt gewijzigd. Hoewel deze vermelding projectspecifiek is, beveelt de Adobe waarden aan van een paar minuten in projectontwikkelingsfasen en een paar uur in stabiele productiesystemen.

Deze instelling wordt doorgaans geconfigureerd met de volgende cachevermelding:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:10:3600
```

Een ander voorbeeldscenario waar de eigenschap GraphQl caching voor gebruik wordt geadviseerd is de navigatiecomponent. De reden is dat het dezelfde GraphQL-query op alle pagina&#39;s verzendt. In dit geval wordt de cachevermelding doorgaans ingesteld op:

```
venia/components/structure/navigation:true:10:600
```

Overwegende dat de [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) wordt gebruikt. Let op het gebruik van de naam van de componentproxy `venia/components/structure/navigation`, en **niet** de naam van de CIF navigatiecomponent (`core/cif/components/structure/navigation/v1/navigation`).

Caching voor andere componenten zou op een projectbasis, gewoonlijk in coördinatie met caching moeten worden bepaald die op het niveau van de Verzender wordt gevormd. Herinner dat er geen actieve ongeldigverklaring van deze geheime voorgeheugens is, zodat zou de caching duur zorgvuldig moeten worden geplaatst. Er zijn geen standaardwaarden die overeenkomen met alle mogelijke projecten en gebruiksgevallen. Zorg ervoor dat u een caching strategie op het projectniveau bepaalt die het best de vereisten van uw project aanpast.

## Caching van Dispatcher {#dispatcher}

Pagina&#39;s of fragmenten in cache AEM in het deelvenster [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) is een beste praktijk voor om het even welk AEM project. Doorgaans is dit afhankelijk van validatietechnieken die ervoor zorgen dat inhoud die in AEM is gewijzigd, correct wordt bijgewerkt in de Dispatcher. Deze functie is de kern van de strategie voor het in cache plaatsen van AEM Dispatcher.

Naast zuivere AEM-beheerde inhoud CIF, kan een pagina handelsgegevens typisch tonen die dynamisch van Adobe Commerce via GraphQL wordt opgehaald. Hoewel de paginastructuur zelf misschien nooit verandert, kan de commerciële inhoud veranderen. Als productgegevens, zoals naam en prijs, bijvoorbeeld veranderen in Adobe Commerce.

Om ervoor te zorgen dat CIF pagina&#39;s gedurende een beperkte tijd in de AEM Dispatcher in het cachegeheugen worden opgeslagen, raadt de Adobe aan [Tijdgebaseerde cachevalidatie](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring-time-based-cache-invalidation-enablettl) (ook wel op TTL gebaseerd caching genoemd) wanneer het caching CIF pagina&#39;s in de AEM Dispatcher. Deze functie kan worden geconfigureerd in AEM met de extra [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/) pakket.

Met op TTL gebaseerde caching, bepaalt een ontwikkelaar typisch één of veelvoudige caching duur voor geselecteerde AEM pagina&#39;s. Deze duur zorgt ervoor dat CIF pagina&#39;s slechts in het voorgeheugen ondergebracht in de AEM Dispatcher tot de gevormde duur zijn en dat de inhoud vaak wordt bijgewerkt.

>[!NOTE]
>
>Hoewel gegevens aan de serverzijde door de AEM Dispatcher in het cachegeheugen kunnen worden opgeslagen, zijn er enkele CIF `product`, `productlist`, en `searchresults` de componenten veranderen typisch altijd productprijzen in een cliënt-zijbrowser verzoek wanneer de pagina wordt geladen. Zo zorgt u ervoor dat cruciale dynamische inhoud altijd bij het laden van een pagina wordt opgehaald.

## Aanvullende bronnen {#additional}

* [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
* [GraphQL-cacheconfiguratie](https://github.com/adobe/commerce-cif-graphql-client#caching)
* [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html)
