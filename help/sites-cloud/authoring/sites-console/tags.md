---
title: Tags gebruiken
description: Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren
exl-id: d2a9f578-fe0a-48ea-851c-2c84463661e0
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 6%

---

# Tags gebruiken {#using-tags}

Tags zijn een snelle en eenvoudige methode om inhoud binnen een website te classificeren. Tags kunnen worden beschouwd als trefwoorden of labels die aan een pagina, element of andere inhoud kunnen worden gekoppeld, zodat zoekopdrachten naar die inhoud en verwante inhoud kunnen worden uitgevoerd.

* Zie [ het Beheer Markeringen ](/help/sites-cloud/administering/tags.md) voor informatie over het creëren van en het leiden van markeringen, en waarop inhoudsmarkeringen zijn toegepast.
* Zie [ Tags voor Ontwikkelaars ](/help/implementing/developing/introduction/tagging-framework.md) voor informatie over het etiketterende kader en het omvatten van en het uitbreiden van markeringen in douanetoepassingen.

## Tien redenen voor het gebruik van tags {#ten-reasons-to-use-tagging}

1. **Organiserend Inhoud** - het Etiketteren maakt het leven voor auteurs gemakkelijker aangezien zij inhoud met weinig inspanning kunnen snel organiseren.
1. **het Organiseren van Markeringen** - terwijl de markeringen inhoud organiseren, organiseren de hiërarchische taxonomieën/namespaces markeringen.
1. **diep Georganiseerde Markeringen** - met de capaciteit om markeringen en sub-markeringen tot stand te brengen wordt het mogelijk om volledige taxonomische systemen uit te drukken, die termijnen, subterms en hun verhoudingen behandelen. Zo kunt u een tweede (of derde) inhoudshiërarchie maken die parallel is aan de officiële inhoudshiërarchie.
1. **Gecontroleerde Tagging** - het Etiketteren kan worden gecontroleerd door toestemmingen op markeringen en/of namespaces toe te passen om markeringsverwezenlijking en toepassing te controleren.
1. **Flexibele het Etiketteren** - de markeringen hebben vele namen en gezichten: markeringen, taxonomie termijnen, categorieën, etiketten en vele meer. Ze zijn flexibel in hun inhoudsmodel en in de manier waarop ze kunnen worden gebruikt, bijvoorbeeld bij het beschrijven van doeldemografie, het categoriseren en classificeren van inhoud of het creëren van een secundaire inhoudshiërarchie.
1. **Verbeterd het Zoeken** - de standaardonderzoekscomponent in AEM omvat globaal gecreeerde markeringen en toegepaste markeringen waarop de filters kunnen worden toegepast om de resultaten aan die te beperken die relevant zijn.
1. **SEO die** toelaat - de Markeringen die als paginaeigenschappen worden toegepast zullen automatisch in de metatags van de pagina verschijnen die het zichtbaar maken aan onderzoeksmotoren.
1. **Eenvoudige Verfijning** - de markeringen kunnen eenvoudig van een woord en de aanraking van een knoop worden gecreeerd. Daarna kunt u een titel, beschrijving en een onbeperkt label toevoegen om meer semantiek aan de tag toe te voegen.
1. **Consistentie van de Kern** - het etiketterende systeem is een kerncomponent van AEM en door alle AEM mogelijkheden gebruikt om inhoud te categoriseren. Verder is de API voor codering beschikbaar voor ontwikkelaars die toepassingen met codering willen maken die toegang hebben tot dezelfde taxonomieën.
1. **combineert Structuur &amp; Flexibiliteit** - AEM is ideaal voor het werken met gestructureerde informatie, toe te schrijven aan het nesten van pagina&#39;s en wegen. Het is even krachtig wanneer het werken met ongestructureerde informatie, toe te schrijven aan de ingebouwde full-text onderzoek. Tags combineren de sterke punten van structuur en flexibiliteit.

Wanneer u de inhoudsstructuur voor een site en het metagegevensschema voor elementen ontwerpt, moet u rekening houden met de lichte en toegankelijke manier waarop u tags kunt toewijzen.

## Tags toepassen {#applying-tags}

In het auteursmilieu, kunnen de auteurs markeringen toepassen door tot de paginaeigenschappen toegang te hebben en één of meerdere markeringen in het **Markeringen/Trefwoorden** gebied in te gaan.

Als u vooraf gedefinieerde tags wilt toepassen, gebruikt u in het venster **Pagina-eigenschappen** het veld **Tags** en het venster **Tags selecteren**. Het tabblad **Standaardtags** is de standaardnaamruimte, wat betekent dat er geen `namespace-string:` als voorvoegsel is voor de taxonomie. <!-- To apply [pre-defined tags](/help/sites-administering/tags.md), in the **Page Properties** window use the **Tags** field and the **Select Tags** window.-->

![ Uitgezochte veelvoudige markeringen ](/help/sites-cloud/authoring/assets/tags-select.png)

## Codes publiceren {#publishing-tags}

Net als bij de manier waarop u pagina&#39;s kunt publiceren en de publicatie ervan ongedaan kunt maken, kunt u het volgende uitvoeren op tags en naamruimten:

### Activeren {#activate}

* Afzonderlijke tags activeren.

  Net als bij pagina&#39;s moeten gemaakte tags worden geactiveerd voordat deze beschikbaar komen in de publicatieomgeving.

>[!NOTE]
>
>Wanneer u een pagina activeert, wordt automatisch een dialoogvenster geopend waarin u niet-geactiveerde tags die bij de pagina horen, kunt activeren.

### Deactiveren {#deactivate}

* Deactiveer de geselecteerde labels.
