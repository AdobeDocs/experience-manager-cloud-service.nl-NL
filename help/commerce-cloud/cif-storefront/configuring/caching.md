---
title: Caching en prestaties
description: Leer over de verschillende beschikbare configuraties om GraphQL en inhoud het in cache plaatsen toe te laten om de prestaties van uw handelsimplementatie te optimaliseren.
exl-id: 21ccdab8-4a2d-49ce-8700-2cbe129debc6
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 80bd8da1531e009509e29e2433a7cbc8dfe58e60
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 0%

---


# Caching en prestaties {#caching}

## Component &amp; GraphQL Response Caching {#graphql}

De AEM CIF Core-componenten beschikken al over geïntegreerde ondersteuning voor het in cache plaatsen van GraphQL-reacties voor afzonderlijke componenten. Deze functie kan worden gebruikt om het aantal GraphQL backend vraag met een grote factor te verminderen. Een efficiënte caching kan vooral voor het herhalen van vragen zoals het terugwinnen van de categorieboom voor een navigatiecomponent of het halen van alle beschikbare samenvoegingen/facetwaarden worden bereikt die op de productonderzoek en categoriepagina&#39;s worden getoond.

Voor de AEM CIF Core-componenten wordt caching geconfigureerd op componentbasis, zodat het mogelijk is om te bepalen of (en hoe lang) GraphQL-verzoeken/-reacties voor elke component in de cache worden opgeslagen. Het is ook mogelijk om het caching gedrag voor de diensten te bepalen OSGi gebruikend de cliënt van GraphQL.

### Configuratie {#configuration}

Zodra gevormd voor een bepaalde component, begint het geheime voorgeheugen GraphQL vragen en antwoorden zoals die door elke ingang van de geheim voorgeheugenconfiguratie worden bepaald op te slaan. De grootte van het geheime voorgeheugen en de in het voorgeheugen onderbrengingsduur van elke ingang wordt bepaald op een projectbasis, die, bijvoorbeeld op het volgende afhangt:

* Hoe vaak de catalogusgegevens kunnen veranderen.
* Hoe kritiek het is dat een component altijd de recentste mogelijke gegevens, etc. toont.

Er is geen cachevervalsing, dus wees voorzichtig wanneer het plaatsen van de geheim voorgeheugenduur.

Wanneer het vormen caching voor componenten, moet de geheim voorgeheugennaam de naam van de **volmacht** componenten zijn die u in uw project bepaalt.

Alvorens de cliënt een verzoek van GraphQL verzendt, controleert het als dat **nauwkeurig** zelfde verzoek van GraphQL reeds in het voorgeheugen ondergebracht is en misschien de caching reactie terugkeert. Om aan te passen, moet het verzoek van GraphQL __ precies aanpassen. Namelijk de vraag, verrichtingsnaam (als om het even welk), variabelen (als om het even welk) _moet_ allen aan het caching verzoek gelijk zijn. En, moeten alle kopballen van douaneHTTP die _zouden kunnen worden geplaatst_ ook het zelfde zijn. Bijvoorbeeld, moet de Adobe Commerce `Store` kopbal __ aanpassen.

### Voorbeelden {#examples}

Adobe raadt u aan om caching te configureren voor de zoekservice waarmee alle beschikbare aggregaties/facetwaarden worden opgehaald die worden weergegeven op de productzoekpagina en categoriepagina&#39;s. Deze waarden veranderen doorgaans alleen wanneer een nieuw kenmerk aan producten wordt toegevoegd, bijvoorbeeld. De duur van deze cachevermelding kan dus &#39;groot&#39; zijn als de set met productkenmerken niet vaak wordt gewijzigd. Hoewel deze vermelding projectspecifiek is, beveelt Adobe waarden aan van een paar minuten in de projectontwikkelingsfasen en een paar uur in stabiele productiesystemen.

Deze instelling wordt doorgaans geconfigureerd met de volgende cachevermelding:

```text
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:10:3600
```

Een ander voorbeeldscenario waar de eigenschap GraphQl caching voor gebruik wordt geadviseerd is de navigatiecomponent. De reden is dat het dezelfde GraphQL-query op alle pagina&#39;s verzendt. In dit geval wordt de cachevermelding doorgaans ingesteld op:

```text
venia/components/structure/navigation:true:10:600
```

Ervan uitgaande dat de [ opslag van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia) wordt gebruikt. Neem nota van het gebruik van de naam van de componentenvolmacht `venia/components/structure/navigation`, en **niet** de naam van de navigatiecomponent van CIF (`core/cif/components/structure/navigation/v1/navigation`).

Caching voor andere componenten zou op projectbasis, gewoonlijk in coördinatie met caching moeten worden bepaald die op het niveau van Dispatcher wordt gevormd. Herinner dat er geen actieve ongeldigverklaring van deze geheime voorgeheugens is, zodat zou de caching duur zorgvuldig moeten worden geplaatst. Er zijn geen standaardwaarden die overeenkomen met alle mogelijke projecten en gebruiksgevallen. Zorg ervoor dat u een caching strategie op het projectniveau bepaalt die het best de vereisten van uw project aanpast.

## Dispatcher Caching {#dispatcher}

Het in cache plaatsen van AEM pagina&#39;s of fragmenten in [ AEM Dispatcher ](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/dispatcher) is een beste praktijk voor om het even welk project van AEM. Doorgaans is dit afhankelijk van validatietechnieken die ervoor zorgen dat alle inhoud die in AEM is gewijzigd, correct wordt bijgewerkt in de Dispatcher. Deze functie is de kern van de AEM Dispatcher caching-strategie.

Naast de zuivere door AEM beheerde inhoud CIF, kan een pagina typisch handelsgegevens tonen die dynamisch van Adobe Commerce via GraphQL wordt opgehaald. Hoewel de paginastructuur zelf misschien nooit verandert, kan de commerciële inhoud veranderen. Als productgegevens, zoals naam en prijs, bijvoorbeeld veranderen in Adobe Commerce.

Om ervoor te zorgen dat de pagina&#39;s van CIF voor een beperkte tijd in AEM Dispatcher in het voorgeheugen worden opgenomen, adviseert Adobe het gebruiken van [ Op tijd-Gebaseerde de Invalidatie van het Geheime voorgeheugen ](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration#configuring-time-based-cache-invalidation-enablettl) (die als op TTL-Gebaseerd caching wordt bekend) wanneer het in het voorgeheugen onderbrengen van de pagina&#39;s van CIF in AEM Dispatcher. Deze eigenschap kan in AEM met het gebruiken van het extra [ ACS AEM Commons ](https://adobe-consulting-services.github.io/acs-aem-commons/) pakket worden gevormd.

Met op TTL gebaseerde caching, bepaalt een ontwikkelaar typisch één of veelvoudige caching duur voor geselecteerde pagina&#39;s van AEM. Deze duur zorgt ervoor dat CIF-pagina&#39;s alleen in de AEM Dispatcher in de cache worden geplaatst tot de geconfigureerde duur en dat de inhoud regelmatig wordt bijgewerkt.

>[!NOTE]
>
>Hoewel gegevens aan de serverzijde mogelijk door de AEM Dispatcher in de cache worden opgeslagen, worden productprijzen in sommige CIF-componenten zoals de componenten `product` , `productlist` en `searchresults` doorgaans altijd aangepast in een browserverzoek aan de clientzijde wanneer de pagina wordt geladen. Zo zorgt u ervoor dat cruciale dynamische inhoud altijd bij het laden van een pagina wordt opgehaald.

## Aanvullende bronnen {#additional}

* [ de opslag van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia)
* [ GraphQL caching configuratie ](https://github.com/adobe/commerce-cif-graphql-client#caching)
* [ AEM Dispatcher ](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/dispatcher)
