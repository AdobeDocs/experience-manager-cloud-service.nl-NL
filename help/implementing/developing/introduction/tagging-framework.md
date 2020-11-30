---
title: Kader voor tags AEM
description: Taginhoud en gebruik de AEM Taginginfrastructuur om deze te categoriseren en te ordenen.
translation-type: tm+mt
source-git-commit: 4bf023068aa69fb6b69c6f2443703ea2bbbf7d42
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 0%

---


# Het kader voor AEM {#aem-tagging-framework}

Door tags toe te wijzen, kunt u inhoud indelen en ordenen. Tags kunnen worden geclassificeerd door een naamruimte en een taxonomie. Voor gedetailleerde informatie over het gebruik van tags:

* Zie [Tags](/help/sites-cloud/authoring/features/tags.md) gebruiken voor informatie over het labelen van inhoud als auteur van inhoud.
* Zie Tags beheren voor een beheerder. Het perspectief van de beheerder op het maken en beheren van tags en op welke inhoudstags zijn toegepast.

Dit artikel richt zich op het onderliggende kader dat het etiketteren in AEM steunt en hoe te om het als ontwikkelaar te gebruiken.

## Inleiding {#introduction}

U kunt als volgt de inhoud labelen en de infrastructuur voor AEM tags gebruiken:

* De tag moet bestaan als een knooppunt van het type [`cq:Tag`](#cq-tag-node-type) onder het [taxonomy root-knooppunt.](#taxonomy-root-node)
* Het gelabelde inhoudsknooppunt `NodeType` moet de [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mix bevatten.
* Het [`TagID`](#tagid) wordt toegevoegd aan het [`cq:tags`](#cq-tags-property) bezit van de inhoudsknoop en lost aan een knoop van type op [`cq:Tag`.](#cq-tag-node-type)

## cq:Type tagknooppunt {#cq-tag-node-type}

De declaratie van een tag wordt vastgelegd in de repository in een knooppunt van het type `cq:Tag.`

* Een tag kan een eenvoudig woord zijn (bijvoorbeeld `sky`) of een hiërarchische taxonomie vertegenwoordigen (bijvoorbeeld `fruit/apple`, dat wil zeggen zowel de generieke vruchten als de meer specifieke appel).
* Tags worden geïdentificeerd door een unieke `TagID`.
* Een tag bevat optionele metagegevens, zoals een titel, gelokaliseerde titels en een beschrijving. De titel moet worden weergegeven in gebruikersinterfaces in plaats van de `TagID`, indien aanwezig.

Met het coderingsframework kunt u auteurs en sitebezoekers ook beperken tot het gebruik van specifieke, vooraf gedefinieerde tags.

### Tagkenmerken {#tag-characteristics}

* Het knooppunttype is `cq:Tag`.
* De knooppuntnaam is een component van [`TagID`.](#tagid)
* Het veld bevat [`TagID`](#tagid) altijd een [naamruimte.](#tag-namespace)
* De `jcr:title` eigenschap (de titel die in de UI moet worden weergegeven) is optioneel.
* The `jcr:description` property is optional.
* Wanneer onderliggende knooppunten worden opgenomen, wordt dit een [containertag genoemd.](#container-tags)
* De tag wordt in de repository opgeslagen onder een basispad dat het [taxonomy root node wordt genoemd.](#taxonomy-root-node)

### TagID {#tagid}

A `TagID` identificeert een weg die aan een markeringsknoop in de bewaarplaats oplost.

Doorgaans `TagID` is de waarde een steno die `TagID` begint met de naamruimte, of kan de waarde een absolute `TagID` beginwaarde zijn die begint bij het knooppunt van de [taxonomiwortel.](#taxonomy-root-node)

Wanneer inhoud wordt gelabeld en nog niet bestaat, wordt de [`cq:tags`](#cq-tags-property) eigenschap toegevoegd aan het inhoudsknooppunt en `TagID` toegevoegd aan de `String` arraywaarde van de eigenschap.

Het `TagID` bestaat uit een [naamruimte](#tag-namespace) gevolgd door de lokale `TagID`. [Containertags](#container-tags) hebben subtags die een hiërarchische volgorde in de taxonomie aangeven. Subcodes kunnen worden gebruikt om naar labels te verwijzen zoals elke lokale `TagID`tag. Inhoud bijvoorbeeld labelen met `fruit` is toegestaan, zelfs als het een containertag met subtags, zoals `fruit/apple` en `fruit/banana`.

### Taxonomy Root Node {#taxonomy-root-node}

Het basisknooppunt van de taxonomie is het basispad voor alle tags in de gegevensopslagruimte. Het knooppunt van de taxonomiwortel mag *geen* knooppunt van het type zijn `cq:Tag`.

In AEM is het basispad `/content/cq:tags` en het basisknooppunt van het type `cq:Folder`.

### Tagnaamruimte {#tag-namespace}

Met naamruimten kunt u items groeperen. Het meest gangbare gebruik-hoofdlettergebruik is een naamruimte per site (bijvoorbeeld public versus internal) of per grotere toepassing (bijvoorbeeld Sites of Assets), maar naamruimten kunnen voor verschillende andere behoeften worden gebruikt. Naamruimten worden in de gebruikersinterface gebruikt om alleen de subset van tags (d.w.z. tags van een bepaalde naamruimte) weer te geven die van toepassing is op de huidige inhoud.

De naamruimte van de tag is het eerste niveau in de taxonomy-substructuur, dat het knooppunt is dat zich direct onder het [taxonomy-hoofdknooppunt bevindt.](#taxonomy-root-node) Een naamruimte is een knooppunt van het type `cq:Tag` waarvan het bovenliggende element geen `cq:Tag` knooppunttype is.

Alle tags hebben een naamruimte. Als er geen naamruimte is opgegeven, wordt de tag toegewezen aan de standaardnaamruimte, `TagID` dat wil zeggen `default`. `/content/cq:tags/default`.  In dergelijke `Standard Tags`gevallen wordt de titel standaard toegepast.

### Containerlabels {#container-tags}

Een containertag is een knooppunt van het type `cq:Tag` dat een willekeurig aantal onderliggende knooppunten en type bevat, zodat het tagmodel kan worden verbeterd met aangepaste metagegevens.

Bovendien fungeren containercodes (of supercodes) in een taxonomie als de subsom van alle subcodes: inhoud die bijvoorbeeld is gelabeld met `fruit/apple` wordt `fruit` ook beschouwd als gelabeld, d.w.z. als u zoekt naar inhoud die alleen is gelabeld met, `fruit` wordt de inhoud ook gelabeld met `fruit/apple`.

### TagID&#39;s oplossen {#resolving-tagids}

Als de tag-id een dubbele punt (`:`) bevat, scheidt de dubbele punt de naamruimte van de tag of subtaxonomie, die vervolgens worden gescheiden met normale schuine strepen (`/`). Als de tag-id geen dubbele punt heeft, wordt de standaardnaamruimte geïmpliceerd.

De standaardlocatie en de enige locatie voor tags is hieronder `/content/cq:tags`.

Labels die verwijzen naar niet-bestaande paden of paden die niet naar een `cq:Tag` knooppunt verwijzen, worden als ongeldig beschouwd en worden genegeerd.

In de volgende tabel worden enkele voorbeelden `TagID`van voorbeelden, hun elementen en de manier waarop het `TagID` wordt omgezet in een absoluut pad in de opslagplaats:

| `TagID` | Naamruimte | Lokale id | Containertag(s) | Label blad | Absoluut tagpad opslagplaats |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`,`apple` | `braeburn` | `content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | (none) | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | (none) | (none) | (none) | `/content/cq:tags/dam` |
| `content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `content/cq:tags/category/car` |

### Localisatie van tagtitel {#localization-of-tag-title}

Wanneer de tag de optionele titeltekenreeks bevat, is het mogelijk de titel voor weergave te lokaliseren door de eigenschap toe te voegen `jcr:title``jcr:title.<locale>`.

Zie voor meer informatie:

* [Tags in verschillende talen,](tagging-applications.md#tags-in-different-languages) waarmee het gebruik van de API&#39;s als ontwikkelaar wordt beschreven
* Het beheren van Markeringen in Verschillende Talen, die gebruik van de Tagingconsole als beheerder beschrijft

### Toegangsbeheer {#access-control}

Tags bestaan als knooppunten in de opslagplaats onder het [hoofdknooppunt van de taxonomie.](#taxonomy-root-node) Het toestaan of ontkennen van auteurs en plaatsbezoekers om markeringen in een bepaalde namespace tot stand te brengen kan worden bereikt door aangewezen ACLs in de bewaarplaats te plaatsen.

Door het weigeren van leesmachtigingen voor bepaalde tags of naamruimten wordt de mogelijkheid ingesteld om codes toe te passen op specifieke inhoud.

Een gebruikelijke praktijk omvat:

* Het toestaan van de `tag-administrators` groep/de rol schrijft toegang tot alle namespaces (voeg toe/wijzig onder `/content/cq:tags`). Deze groep wordt geleverd met AEM out-of-the-box.
* Gebruikers/auteurs toegang verlenen tot alle naamruimten die voor hen (meestal alle) leesbaar moeten zijn.
* Gebruikers/auteurs toegang toestaan tot naamruimten waar tags vrij kunnen worden gedefinieerd door gebruikers/auteurs (`add_node` onder `/content/cq:tags/some_namespace`)

## Tagable Content: cq:Tagable Mixin {#taggable-content-cq-taggable-mixin}

Toepassingsontwikkelaars kunnen codering aan een inhoudstype koppelen als de registratie ([CND](https://jackrabbit.apache.org/node-type-notation.html)) van het knooppunt de `cq:Taggable` mixin of de `cq:OwnerTaggable` mixin bevat.

De `cq:OwnerTaggable` mix, die overerft van `cq:Taggable`, is bedoeld om aan te geven dat de inhoud kan worden geclassificeerd door de eigenaar/auteur. In AEM, is het slechts een attribuut van de `cq:PageContent` knoop. Het `cq:OwnerTaggable` coderingskader vereist geen mixine.

>[!NOTE]
>
>Het wordt aanbevolen alleen tags in te schakelen op het knooppunt op het hoogste niveau van een samengevoegd inhoudsitem (of op het `jcr:content` knooppunt). Voorbeelden zijn:
>
>* Pagina&#39;s (`cq:Page`) waarvan het `jcr:content`knooppunt van het type is `cq:PageContent`, inclusief de `cq:Taggable` mix.
>* Elementen (`cq:Asset`) waarbij het `jcr:content/metadata` knooppunt altijd de `cq:Taggable` mix heeft.


### Node Type Notation (CND) {#node-type-notation-cnd}

Node Type definities bestaan in de bewaarplaats als Cnd- dossiers. De CND-notatie wordt gedefinieerd als onderdeel van de [JCR-documentatie.](https://jackrabbit.apache.org/node-type-notation.html).

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

De `cq:tags` eigenschap is een `String` array die wordt gebruikt om een of meer `TagID`s op te slaan wanneer deze door auteurs of bezoekers van de site op inhoud worden toegepast. De eigenschap heeft alleen betekenis wanneer deze wordt toegevoegd aan een knooppunt dat met de [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mix is gedefinieerd.

>[!NOTE]
>
>Als u AEM tagfuncties wilt gebruiken, moeten aangepaste toepassingen alleen tageigenschappen definiëren `cq:tags`.

## Labels verplaatsen en samenvoegen {#moving-and-merging-tags}

Hieronder volgt een beschrijving van de effecten in de opslagplaats bij het verplaatsen of samenvoegen van tags met behulp van de Tagging-console.

Wanneer tag A wordt verplaatst of samengevoegd in tag B onder `/content/cq:tags`:

* Tag A wordt niet verwijderd en ontvangt een `cq:movedTo` eigenschap.
   * `cq:movedTo` verwijst naar label B.
   * Deze eigenschap betekent dat tag A is verplaatst of samengevoegd met tag B.
   * Als tag B wordt verplaatst, wordt deze eigenschap dienovereenkomstig bijgewerkt.
   * Tag A is dus verborgen en wordt alleen in de opslagplaats bewaard om tag-id&#39;s op te lossen in inhoudsknooppunten die verwijzen naar tag A.
   * De opschoonfunctie voor ongewenste details verwijdert tags zoals tag A, als er geen inhoudsknooppunten meer naar wijzen.
   * Er is een speciale waarde voor de `cq:movedTo` eigenschap `nirvana`, die wordt toegepast wanneer de tag wordt verwijderd, maar niet kan worden verwijderd uit de opslagplaats omdat er subtags zijn met een `cq:movedTo` eigenschap die moet worden bewaard.

      >[!NOTE]
      >
      >De `cq:movedTo` eigenschap wordt alleen aan de verplaatste of samengevoegde tag toegevoegd als aan een van deze voorwaarden wordt voldaan:
      >
      > 1. De tag wordt gebruikt in inhoud (wat betekent dat de tag een referentie heeft). OF
      > 1. De tag bevat onderliggende elementen die al zijn verplaatst.


* Label B wordt gemaakt (in het geval van een verplaatsing) en ontvangt een `cq:backlinks` eigenschap.
   * `cq:backlinks` houdt de verwijzingen in de andere richting, d.w.z. het houdt een lijst bij van alle markeringen die zijn verplaatst naar of samengevoegd met markering B.
   * Dit is vooral nodig om de `cq:movedTo` eigenschappen up-to-date te houden wanneer tag B ook wordt verplaatst/samengevoegd/verwijderd of als tag B wordt geactiveerd. In dat geval moeten alle tags voor de achtergrond ook worden geactiveerd.

      >[!NOTE]
      >
      >De `cq:backlinks` eigenschap wordt alleen aan de verplaatste of samengevoegde tag toegevoegd als aan een van deze voorwaarden wordt voldaan:
      >
      > 1. De tag wordt gebruikt in inhoud (wat betekent dat de tag een referentie heeft). OF
      > 1. De tag bevat onderliggende elementen die al zijn verplaatst.


Bij het lezen van een `cq:tags` eigenschap van een inhoudsknooppunt wordt de volgende resolutie gebruikt:

1. Als er geen overeenkomst onder `/content/cq:tags`is, wordt geen tag geretourneerd.
1. Als de tag een `cq:movedTo` eigenschapset heeft, wordt de tag-id waarnaar wordt verwezen gevolgd.
   * Deze stap wordt herhaald zolang de volgende tag een `cq:movedTo` eigenschap heeft.
1. Als de volgende tag geen `cq:movedTo` eigenschap heeft, wordt de tag gelezen.

Als u de wijziging wilt publiceren wanneer een tag is verplaatst of samengevoegd, moeten het `cq:Tag` knooppunt en alle bijbehorende back-ups worden gerepliceerd. Dit wordt automatisch gedaan wanneer de markering in de console van het markeringsbeleid wordt geactiveerd.

Verderop worden de oude verwijzingen automatisch aangepast aan de `cq:tags` eigenschap van de pagina. Dit wordt geactiveerd omdat het omzetten van een verplaatste tag via de API de doeltag retourneert, waardoor de doeltag-id wordt opgegeven.
