---
title: Tags gebruiken
description: Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Tags gebruiken {#using-tags}

Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren. Tags kunnen worden beschouwd als trefwoorden of labels die aan een pagina, element of andere inhoud kunnen worden gekoppeld, zodat zoekopdrachten naar die inhoud en verwante inhoud kunnen worden uitgevoerd.

* Zie Tags beheren voor informatie over het maken en beheren van tags en over de inhoudstags die zijn toegepast. <!-- See [Administering Tags](/help/sites-administering/tags.md) for information about creating and managing tags, as well as to which content tags have been applied.-->
* Zie Tags toevoegen voor ontwikkelaars voor meer informatie over het codeerframework en voor het opnemen en uitbreiden van tags in aangepaste toepassingen. <!-- See [Tagging for Developers](/help/sites-developing/tags.md) for information about the tagging framework as well as including and extending tags in custom applications.-->

## Tien redenen voor het gebruik van tags {#ten-reasons-to-use-tagging}

1. **Inhoud** ordenen - Met tags kunnen auteurs het leven gemakkelijker maken, omdat ze inhoud snel en eenvoudig kunnen ordenen.
1. **Tags** ordenen - Terwijl tags inhoud ordenen, ordenen hiërarchische taxonomieën/naamruimten tags.
1. **Deed Organised Tags** - Met de mogelijkheid om tags en subtags te maken, wordt het mogelijk om volledige taxonomische systemen uit te drukken, inclusief termen, subtermen en hun relaties. Zo kunt u een tweede (of derde) inhoudshiërarchie maken die parallel is aan de officiële inhoudshiërarchie.
1. **Gecontroleerde labeling** - Tags kunnen worden beheerd door machtigingen toe te passen op tags en/of naamruimten om het maken en de toepassing van tags te regelen.
1. **Flexibele tags toepassen** - Tags hebben veel namen en gezichten: tags, taxonomie termen, categorieën, labels en nog veel meer. Zij zijn flexibel in hun inhoudsmodel en in de manier waarop zij kunnen worden gebruikt; bijvoorbeeld bij het schetsen van doeldemografie, het categoriseren en classificeren van inhoud of het creëren van een secundaire inhoudshiërarchie.
1. **Verbeterd zoeken** - De standaardzoekcomponent in AEM bevat over het algemeen gemaakte tags en toegepaste tags waarop filters kunnen worden toegepast om de resultaten te beperken tot de relevante waarden.
1. **SEO Inschakelen** - Labels die als pagina-eigenschappen zijn toegepast, worden automatisch weergegeven in de tags van de pagina, zodat deze zichtbaar zijn voor zoekmachines.
1. **Eenvoudig, geavanceerd** - tags kunnen eenvoudig worden gemaakt op basis van een woord en de aanraking met een knop. Daarna kunt u een titel, beschrijving en een onbeperkt label toevoegen om meer semantiek aan de tag toe te voegen.
1. **Basisconsistentie** : het coderingssysteem is een kernonderdeel van AEM en wordt door alle AEM-mogelijkheden gebruikt om inhoud te categoriseren. Verder is de API voor codering beschikbaar voor ontwikkelaars die toepassingen met codering willen maken die toegang hebben tot dezelfde taxonomieën.
1. **Combineert structuur en flexibiliteit** - AEM is ideaal voor het werken met gestructureerde informatie, door het nesten van pagina&#39;s en paden. Het is even krachtig wanneer het werken met ongestructureerde informatie, toe te schrijven aan de ingebouwde full-text onderzoek. Tags combineren de sterke punten van structuur en flexibiliteit.

Wanneer u de inhoudsstructuur voor een site en het metagegevensschema voor elementen ontwerpt, moet u rekening houden met de lichte en toegankelijke manier waarop u tags kunt toewijzen.

## Tags toepassen {#applying-tags}

In de auteursomgeving, kunnen de auteurs markeringen toepassen door tot de pagina eigenschappen toegang te hebben en één of meerdere markeringen in het gebied van **Markeringen/Trefwoorden** in te gaan.

Als u vooraf gedefinieerde labels wilt toepassen, gebruikt u in het venster **Pagina-eigenschappen** het veld **Codes** en het venster **Codes** selecteren. Het tabblad **Standaardcodes** is de standaardnaamruimte, wat betekent dat er geen `namespace-string:` voorvoegsel is voor de taxonomie. <!-- To apply [pre-defined tags](/help/sites-administering/tags.md), in the **Page Properties** window use the **Tags** field and the **Select Tags** window.-->

![Meerdere tags selecteren](/help/sites-cloud/authoring/assets/tags-select.png)

## Codes publiceren {#publishing-tags}

Net als bij de manier waarop u pagina&#39;s kunt publiceren en de publicatie ervan ongedaan kunt maken, kunt u het volgende uitvoeren op tags en naamruimten:

### Activeren {#activate}

* Afzonderlijke tags activeren.

   Net als bij pagina&#39;s moeten nieuwe tags worden geactiveerd voordat deze beschikbaar komen in de publicatieomgeving.

>[!NOTE]
>
>Wanneer u een pagina activeert, wordt automatisch een dialoogvenster geopend waarin u niet-geactiveerde tags die bij de pagina horen, kunt activeren.

### Deactiveren {#deactivate}

* Deactiveer de geselecteerde labels.
