---
title: Kader voor tags AEM
description: Taginhoud en gebruik de AEM Tags toevoegen-infrastructuur om de inhoud te categoriseren en in te delen.
exl-id: 25418d44-aace-4e73-be1a-4b1902f40403
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '1569'
ht-degree: 0%

---

# Het kader voor AEM {#aem-tagging-framework}

Door tags toe te wijzen, kunt u inhoud indelen en ordenen. Tags kunnen worden geclassificeerd door een naamruimte en een taxonomie. Voor gedetailleerde informatie over het gebruik van tags:

* Zie [Tags gebruiken](/help/sites-cloud/authoring/features/tags.md) voor informatie over het labelen van inhoud als auteur van inhoud.
* Zie Tags beheren voor een beheerder. Het standpunt van de beheerder over het maken en beheren van tags en waarop inhoudstags zijn toegepast.

Dit artikel richt zich op het onderliggende kader dat het etiketteren in AEM steunt en hoe te om het als ontwikkelaar te gebruiken.

## Inleiding {#introduction}

U kunt als volgt de inhoud labelen en de AEM Tags toevoegen-infrastructuur gebruiken:

* De tag moet bestaan als een knooppunt van het type [`cq:Tag`](#cq-tag-node-type) onder de [taxonomie root node.](#taxonomy-root-node)
* Het knooppunt voor gecodeerde inhoud `NodeType` moet de [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin.
* De [`TagID`](#tagid) wordt toegevoegd aan de inhoud van het knooppunt [`cq:tags`](#cq-tags-property) eigenschap en wordt omgezet in een knooppunt van het type [`cq:Tag`.](#cq-tag-node-type)

## cq:Type tagknooppunt {#cq-tag-node-type}

De declaratie van een tag wordt vastgelegd in de repository in een knooppunt van het type `cq:Tag.`

* Een tag kan een eenvoudig woord zijn (bijvoorbeeld `sky`) of een hiërarchische taxonomie vertegenwoordigen (bijvoorbeeld `fruit/apple`, dat wil zeggen zowel de generieke vruchten als de meer specifieke appel).
* Tags worden geïdentificeerd door een unieke `TagID`.
* Een tag bevat optionele metagegevens, zoals een titel, gelokaliseerde titels en een beschrijving. De titel moet worden weergegeven in gebruikersinterfaces in plaats van de `TagID`, indien aanwezig.

Het coderingskader beperkt auteurs en sitebezoekers ook tot het gebruik van alleen specifieke, vooraf gedefinieerde tags.

### Tagkenmerken {#tag-characteristics}

* Het knooppunttype is `cq:Tag`.
* De knooppuntnaam is een component van [`TagID`.](#tagid)
* De [`TagID`](#tagid) bevat altijd een [naamruimte.](#tag-namespace)
* De `jcr:title` eigenschap (de titel die in de UI moet worden weergegeven) is optioneel.
* De `jcr:description` eigenschap is optioneel.
* Wanneer onderliggende knooppunten worden opgenomen, wordt dit een [containertag.](#container-tags)
* De tag wordt in de repository opgeslagen onder een basispad dat het basispad heet [taxonomie root node.](#taxonomy-root-node)

### TagID {#tagid}

A `TagID` identificeert een weg die aan een markeringsknoop in de bewaarplaats oplost.

De `TagID` is een steno `TagID` beginnen met de naamruimte of deze kan absoluut zijn `TagID` vanaf de [taxonomie root node.](#taxonomy-root-node)

Als inhoud is gelabeld en nog niet bestaat, wordt het [`cq:tags`](#cq-tags-property) eigenschap wordt toegevoegd aan het inhoudsknooppunt en de `TagID` wordt toegevoegd aan de eigenschap `String` arraywaarde.

De `TagID` bestaat uit een [namespace](#tag-namespace) gevolgd door de lokale `TagID`. [Containerlabels](#container-tags) beschikken over subtags die een hiërarchische volgorde in de taxonomie aangeven. Subtags kunnen worden gebruikt om naar labels te verwijzen op dezelfde manier als lokale `TagID`. Inhoud bijvoorbeeld labelen met `fruit` is toegestaan, zelfs als het een containertag met subtags is, zoals `fruit/apple` en `fruit/banana`.

### Taxonomy Root Node {#taxonomy-root-node}

Het basisknooppunt van de taxonomie is het basispad voor alle tags in de gegevensopslagruimte. Het knooppunt van de taxonomiwortel moet *niet* zijn een knooppunt van het type `cq:Tag`.

In AEM is het basispad `/content/cq:tags` en de hoofdnode is van het type `cq:Folder`.

### Tagnaamruimte {#tag-namespace}

Met naamruimten kunt u items groeperen. Het meest gangbare gebruik-hoofdlettergebruik is het hebben van een naamruimte per site (bijvoorbeeld public versus internal) of per grotere toepassing (bijvoorbeeld Sites of Assets), maar naamruimten kunnen voor verschillende andere behoeften worden gebruikt. Naamruimten worden in de gebruikersinterface gebruikt om alleen de subset van tags (dat wil zeggen tags van een bepaalde naamruimte) weer te geven die van toepassing is op de huidige inhoud.

De naamruimte van de tag is het eerste niveau in de taxonomy-substructuur. Dit is het knooppunt direct onder de [taxonomie root node.](#taxonomy-root-node) Een naamruimte is een knooppunt van het type `cq:Tag` waarvan de ouder geen `cq:Tag` knooppunttype.

Alle tags hebben een naamruimte. Als er geen naamruimte is opgegeven, wordt de tag toegewezen aan de standaardnaamruimte, die `TagID` `default`, dat wil zeggen: `/content/cq:tags/default`. De titel is standaard ingesteld op `Standard Tags`in dergelijke gevallen.

### Containerlabels {#container-tags}

Een containertag is een knooppunt van het type `cq:Tag` met een willekeurig aantal onderliggende knooppunten en een willekeurig type onderliggende knooppunten, waardoor het tagmodel kan worden verbeterd met aangepaste metagegevens.

Bovendien fungeren containercodes (of super-tags) in een taxonomie als de subsummatie van alle subtags. Inhoud die bijvoorbeeld is gelabeld met `fruit/apple` wordt beschouwd als getagd met `fruit`, ook. Met andere woorden, zoeken naar inhoud waaraan labels zijn toegevoegd `fruit` zou ook de inhoud vinden waaraan `fruit/apple`.

### TagID&#39;s oplossen {#resolving-tagids}

Als de tag-id een dubbele punt bevat (`:`), scheidt de dubbele punt de naamruimte van de tag of subtaxonomie, die vervolgens worden gescheiden met normale schuine strepen (`/`). Als de tag-id geen dubbele punt heeft, wordt de standaardnaamruimte geïmpliceerd.

De standaardlocatie en de enige locatie voor tags is lager dan `/content/cq:tags`.

Tags die verwijzen naar niet-bestaande paden of paden die niet naar een `cq:Tag` knooppunt wordt als ongeldig beschouwd en wordt genegeerd.

In de volgende tabel ziet u een voorbeeld `TagID`s, hun elementen en hoe `TagID` wordt omgezet in een absoluut pad in de opslagplaats:

| `TagID` | Naamruimte | Lokale id | Containerlabels | Label blad | Absoluut tagpad opslagplaats |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`,`apple` | `braeburn` | `content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | (geen) | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | (geen) | (geen) | (geen) | `/content/cq:tags/dam` |
| `content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `content/cq:tags/category/car` |

### Localisatie van tagtitel {#localization-of-tag-title}

Wanneer de tag de optionele titeltekenreeks bevat `jcr:title`, is het mogelijk de titel voor weergave te lokaliseren door de eigenschap toe te voegen `jcr:title.<locale>`.

Raadpleeg de volgende secties voor meer informatie:

* [Tags in verschillende talen](tagging-applications.md#tags-in-different-languages) het gebruik van de API&#39;s als ontwikkelaar beschrijven
* Tags beheren in verschillende talen, die het gebruik van de tagconsole als beheerder beschrijven

### Toegangsbeheer {#access-control}

Tags bestaan als knooppunten in de opslagplaats onder [taxonomie root node.](#taxonomy-root-node) Het toestaan of ontkennen van auteurs en plaatsbezoekers om markeringen in een bepaalde namespace tot stand te brengen kan worden bereikt door aangewezen ACLs in de bewaarplaats te plaatsen.

Door het weigeren van leesmachtigingen voor bepaalde tags of naamruimten wordt de mogelijkheid ingesteld om codes toe te passen op specifieke inhoud.

Een gebruikelijke praktijk omvat:

* De `tag-administrators` groep/rol schrijven toegang tot alle namespaces (toevoegen/wijzigen onder `/content/cq:tags`). Deze groep wordt geleverd met AEM out-of-the-box.
* Gebruikers/auteurs toegang verlenen tot alle naamruimten die voor hen (meestal alle) leesbaar moeten zijn.
* Gebruikers/auteurs toegang toestaan tot naamruimten waar tags vrij kunnen worden gedefinieerd door gebruikers/auteurs (`add_node` krachtens `/content/cq:tags/some_namespace`)

## Tagable Content: cq:Tagable Mixin {#taggable-content-cq-taggable-mixin}

Als ontwikkelaars van toepassingen tags aan een inhoudstype willen koppelen, moet u de registratie van het knooppunt ([CND](https://jackrabbit.apache.org/jcr/node-type-notation.html)) moet de `cq:Taggable` mengen of `cq:OwnerTaggable` mixin.

De `cq:OwnerTaggable` mixin, dat overerft van `cq:Taggable`, is bedoeld om aan te geven dat de inhoud door de eigenaar/auteur kan worden geclassificeerd. In AEM is het alleen een kenmerk van de `cq:PageContent` knooppunt. De `cq:OwnerTaggable` Het coderingsframework vereist geen mixin.

>[!NOTE]
>
>Het wordt aanbevolen alleen labels in te schakelen op het knooppunt op het hoogste niveau van een samengevoegd inhoudsitem (of op het bijbehorende item `jcr:content` knooppunt). Voorbeelden zijn:
>
>* Pagina&#39;s (`cq:Page`) waarbij de `jcr:content`node is type `cq:PageContent`, met inbegrip van de `cq:Taggable` mixin.
>* Activa (`cq:Asset`) waarbij de `jcr:content/metadata` node heeft altijd de `cq:Taggable` mixin.

### Node Type Notation (CND) {#node-type-notation-cnd}

Node Type definities bestaan in de bewaarplaats als Cnd- dossiers. De CND-notatie wordt gedefinieerd als onderdeel van de [JCR-documentatie](https://jackrabbit.apache.org/jcr/node-type-notation.html).

De belangrijkste definities voor de in AEM opgenomen knooppunttypen zijn:

```xml
[cq:Tag] > mix:title, nt:base
    orderable
    - * (undefined) multiple
    - * (undefined)
    + * (nt:base) = cq:Tag version

[cq:Taggable]
    mixin
    - cq:tags (string) multiple

[cq:OwnerTaggable] > cq:Taggable
    mixin
```

## cq:eigenschap tags {#cq-tags-property}

De `cq:tags` eigenschap is een `String` array die wordt gebruikt om een of meer `TagID`s wanneer zij op inhoud door auteurs of plaatsbezoekers worden toegepast. De eigenschap heeft alleen betekenis wanneer deze wordt toegevoegd aan een knooppunt dat is gedefinieerd met het [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin.

>[!NOTE]
>
>Als u AEM coderingsfunctionaliteit wilt gebruiken, mogen door aangepaste toepassingen alleen eigenschappen van tags worden gedefinieerd `cq:tags`.

## Labels verplaatsen en samenvoegen {#moving-and-merging-tags}

Hieronder volgt een beschrijving van de effecten in de opslagplaats bij het verplaatsen of samenvoegen van tags met behulp van de Tagging-console.

Wanneer tag A wordt verplaatst of samengevoegd met tag B onder `/content/cq:tags`:

* Label A wordt niet verwijderd en ontvangt een `cq:movedTo` eigenschap.
   * `cq:movedTo` verwijst naar label B.
   * Deze eigenschap betekent dat tag A is verplaatst of samengevoegd met tag B.
   * Als u tag B verplaatst, wordt deze eigenschap dienovereenkomstig bijgewerkt.
   * Tag A is daarom verborgen en wordt alleen in de gegevensopslagruimte bewaard, zodat tags-id&#39;s kunnen worden opgelost in inhoudsknooppunten die verwijzen naar tag A.
   * De opschoonfunctie voor ongewenste details verwijdert tags zoals tag A, als er geen inhoudsknooppunten meer naar wijzen.
   * Een speciale waarde voor de `cq:movedTo` eigenschap is `nirvana`, die wordt toegepast wanneer de tag wordt verwijderd, maar niet kan worden verwijderd uit de opslagplaats omdat er subtags zijn met een `cq:movedTo` dat moet worden bewaard.

     >[!NOTE]
     >
     >De `cq:movedTo` De eigenschap wordt alleen aan de verplaatste of samengevoegde tag toegevoegd als aan een van deze voorwaarden wordt voldaan:
     >
     > 1. De tag wordt gebruikt in inhoud (wat betekent dat de tag een referentie heeft). OF
     > 1. De tag bevat onderliggende elementen die al zijn verplaatst.
     >
* Label B wordt gemaakt (als er sprake is van een verplaatsing) en ontvangt een `cq:backlinks` eigenschap.
   * `cq:backlinks` houdt de verwijzingen in de andere richting. Dit betekent dat er een lijst wordt bijgehouden met alle tags die zijn verplaatst naar of samengevoegd met tag B.
   * Deze functionaliteit is meestal vereist voor behoud `cq:movedTo` eigenschappen zijn up-to-date wanneer tag B wordt verplaatst/samengevoegd/verwijderd of wanneer tag B wordt geactiveerd; in dat geval moeten ook alle tags met de achtergrond worden geactiveerd.

     >[!NOTE]
     >
     >De `cq:backlinks` De eigenschap wordt alleen aan de verplaatste of samengevoegde tag toegevoegd als aan een van deze voorwaarden wordt voldaan:
     >
     > 1. De tag wordt gebruikt in inhoud (wat betekent dat deze een referentie heeft), of
     > 1. De tag bevat onderliggende elementen die al zijn verplaatst.

Een `cq:tags` Voor eigenschap van een inhoudsknooppunt wordt de volgende resolutie gebruikt:

1. Als er geen overeenkomst onder `/content/cq:tags`, er wordt geen tag geretourneerd.
1. Als de tag een `cq:movedTo` eigenschap ingesteld, wordt de tag-id waarnaar wordt verwezen gevolgd.
   * Deze stap wordt herhaald zolang de volgende tag een `cq:movedTo` eigenschap.
1. Als de volgende tag geen `cq:movedTo` eigenschap, wordt de tag gelezen.

Als u de wijziging wilt publiceren wanneer een tag is verplaatst of samengevoegd, gaat u naar `cq:Tag` node en al zijn backlinks moeten worden gerepliceerd. Deze replicatie wordt automatisch uitgevoerd wanneer de tag wordt geactiveerd in de beheerconsole van de tag.

Later wordt de pagina bijgewerkt met `cq:tags` de oude referenties automatisch opruimen. De opschoning wordt geactiveerd omdat het omzetten van een verplaatste tag via de API de doeltag retourneert, waardoor de doeltag-id wordt opgegeven.
