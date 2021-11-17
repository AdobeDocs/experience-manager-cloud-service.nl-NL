---
title: Caching en prestaties
description: Leer over de verschillende beschikbare configuraties om GrafiekQL en inhoudcaching toe te laten om de prestaties van uw handelsimplementatie te optimaliseren.
exl-id: 21ccdab8-4a2d-49ce-8700-2cbe129debc6,8b969821-5073-4540-a997-95c74a11e4f0
source-git-commit: 460aa927453964f4878a8a969794a7052a2d3778
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---

# Caching en prestaties {#caching}

## Component &amp; GraphQL Response Caching {#graphql}

De AEM CIF Core Components hebben reeds ingebouwde steun voor caching GraphQL reacties voor individuele componenten. Deze eigenschap kan worden gebruikt om het aantal graafQL achterste vraag door een grote factor te verminderen. Een efficiënte caching kan vooral voor het herhalen van vragen zoals het terugwinnen van de categorieboom voor een navigatiecomponent of het halen van alle beschikbare samenvoegingen/facetwaarden worden bereikt die op de productonderzoek en categoriepagina&#39;s worden getoond.

Voor de AEM componenten van de Kern van CIF, wordt het in cache plaatsen gevormd op componentenbasis, zodat is het mogelijk om te controleren als (en hoe lang) de verzoeken/de reacties GraphQL voor elke component in het voorgeheugen worden opgeslagen. Het is ook mogelijk om het caching gedrag voor de diensten te bepalen OSGi gebruikend de cliënt GraphQL.

### Configuratie

Zodra gevormd voor een bepaalde component, begint het geheime voorgeheugen het opslaan van vragen GraphQL en reacties zoals die door elke ingang van de geheim voorgeheugenconfiguratie worden bepaald. De grootte van het geheime voorgeheugen en de caching duur van elke ingang moeten op een projectbasis worden bepaald, afhankelijk bijvoorbeeld van hoe vaak de catalogusgegevens zouden kunnen veranderen, hoe kritiek het is dat een component altijd de recentste mogelijke gegevens, enz. toont. Merk op dat er geen geheim voorgeheugenongeldigverklaring is, zo zorgvuldig wanneer het plaatsen van de geheim voorgeheugenduur is.

Wanneer het vormen caching voor componenten, moet de geheim voorgeheugennaam de naam van zijn **proxy** componenten die u in uw project definieert.

Alvorens de cliënt een verzoek GraphQL verzendt, zal het controleren of dat **exact** zelfde GraphQL- verzoek is reeds caching en zal misschien de caching reactie terugkeren. Om aan elkaar te passen, MOET het verzoek GraphQL precies aanpassen, namelijk de vraag, verrichtingsnaam (als om het even welk), variabelen (als om het even welk) moeten allen aan het caching verzoek gelijk zijn, en ook alle kopballen van douaneHTTP die zouden kunnen worden geplaatst MOET het zelfde zijn. De Magento `Store` koptekst MOET overeenkomen.

### Voorbeelden

Wij adviseren dat u wat caching voor de onderzoeksdienst vormt die alle beschikbare samenvoegingen/facetwaarden haalt die op het productonderzoek en categoriepagina&#39;s worden getoond. Deze waarden veranderen gewoonlijk slechts wanneer een nieuw attribuut bijvoorbeeld aan producten wordt toegevoegd, zodat kan de duur voor deze geheim voorgeheugeningang &quot;groot&quot;zijn als de reeks productattributen niet vaak verandert. Terwijl dit project-specifiek is, adviseren wij waarden van een paar minuten in projectontwikkelingsfasen en een paar uren op stabiele productiesystemen.

Dit wordt typisch gevormd met de volgende geheim voorgeheugeningang:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:10:3600
```

Een ander voorbeeldscenario waar de eigenschap GraphQl in het voorgeheugen onderbrengend wordt geadviseerd om te worden gebruikt is de navigatiecomponent omdat het de zelfde vraag GraphQL op alle pagina&#39;s verzendt. In dit geval wordt de cachevermelding doorgaans ingesteld op:

```
venia/components/structure/navigation:true:10:600
```

bij het overwegen van de [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) wordt gebruikt. Let op het gebruik van de naam van de componentproxy `venia/components/structure/navigation`, en **niet** de naam van de CIF-navigatiecomponent (`core/cif/components/structure/navigation/v1/navigation`).

Caching voor andere componenten zou op een projectbasis, gewoonlijk in coördinatie met caching moeten worden bepaald die op het niveau van de Verzender wordt gevormd. Herinner dat er geen actieve ongeldigverklaring van deze geheime voorgeheugens is, zodat zou de caching duur zorgvuldig moeten worden geplaatst. Er zijn geen standaardwaarden voor één grootte die overeenkomen met alle mogelijke projecten en gebruiksgevallen. Zorg ervoor dat u een caching strategie op het projectniveau bepaalt die het best de vereisten van uw project aanpast.

## Caching van Dispatcher {#dispatcher}

Pagina&#39;s of fragmenten in cache AEM in het deelvenster [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) is een beste praktijk voor om het even welk AEM project. Doorgaans is dit afhankelijk van validatietechnieken die ervoor zorgen dat inhoud die in AEM is gewijzigd, correct wordt bijgewerkt in de Dispatcher. Dit is een kernelement van de strategie voor het in cache plaatsen van AEM Dispatcher.

Naast zuivere AEM beheerde inhoud CIF kan een pagina commerciële gegevens typisch tonen die dynamisch van Magento via GraphQL wordt gehaald. Hoewel de paginastructuur zelf misschien nooit verandert, kan de commerciële inhoud veranderen, bijvoorbeeld, als sommige productgegevens (naam, prijs, enz.) in Magento veranderen.

Om ervoor te zorgen dat CIF-pagina&#39;s gedurende een beperkte periode in de AEM dispatcher in cache kunnen worden opgeslagen, raden we u daarom aan om het volgende te doen: [Op tijd gebaseerde invalidatie van cache](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring-time-based-cache-invalidation-enablettl) (ook wel op TTL gebaseerd in cache plaatsen genoemd) wanneer het in cache plaatsen van CIF-pagina&#39;s in de AEM Dispatcher. Deze eigenschap kan in AEM met het gebruiken van extra worden gevormd [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/) pakket.

Met op TTL gebaseerde caching, bepaalt een ontwikkelaar typisch één of veelvoudige caching duur voor geselecteerde AEM pagina&#39;s. Dit zorgt ervoor dat de pagina&#39;s CIF slechts in het voorgeheugen onder in de AEM verzender tot de gevormde duur worden gebracht en dat de inhoud vaak zal worden bijgewerkt.

>[!NOTE]
>
>Hoewel gegevens aan de serverzijde door de AEM kunnen worden opgeslagen in de cache, zijn er CIF-componenten zoals de `product`, `productlist`, en `searchresults` componenten halen doorgaans altijd de productprijzen opnieuw op in een browserverzoek aan de clientzijde wanneer de pagina wordt geladen. Dit zorgt ervoor dat cruciale dynamische inhoud altijd wordt opgehaald bij het laden van een pagina.

## Aanvullende bronnen

- [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Configuratie van GraphQL-caching](https://github.com/adobe/commerce-cif-graphql-client#caching)
- [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html)
