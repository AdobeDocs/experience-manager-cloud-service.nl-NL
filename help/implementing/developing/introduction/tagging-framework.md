---
title: Kader voor tags AEM
description: Taginhoud en gebruik de AEM Taginginfrastructuur om deze te categoriseren en te ordenen.
translation-type: tm+mt
source-git-commit: 4bf023068aa69fb6b69c6f2443703ea2bbbf7d42
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 0%

---


# Het AEM Tagging Framework {#aem-tagging-framework}

Door tags toe te wijzen, kunt u inhoud indelen en ordenen. Tags kunnen worden geclassificeerd door een naamruimte en een taxonomie. Voor gedetailleerde informatie over het gebruik van tags:

* Zie [Tags gebruiken](/help/sites-cloud/authoring/features/tags.md) voor informatie over het labelen van inhoud als auteur van inhoud.
* Zie Tags beheren voor een beheerder. Het perspectief van de beheerder op het maken en beheren van tags en op welke inhoudstags zijn toegepast.

Dit artikel richt zich op het onderliggende kader dat het etiketteren in AEM steunt en hoe te om het als ontwikkelaar te gebruiken.

## Inleiding {#introduction}

U kunt als volgt de inhoud labelen en de infrastructuur voor AEM tags gebruiken:

* De tag moet bestaan als een knooppunt van het type [`cq:Tag`](#cq-tag-node-type) onder het [taxonomy root-knooppunt.](#taxonomy-root-node)
* De `NodeType` van het gecodeerde inhoudsknooppunt moet de [`cq:Taggable`](#taggable-content-cq-taggable-mixin)-mix bevatten.
* [`TagID`](#tagid) wordt toegevoegd aan [`cq:tags`](#cq-tags-property) bezit van de inhoudsknoop en aan een knoop van type [`cq:Tag`.](#cq-tag-node-type).

## cq:Type tagknooppunt {#cq-tag-node-type}

De declaratie van een tag wordt vastgelegd in de repository in een knooppunt van het type `cq:Tag.`

* Een tag kan een eenvoudig woord zijn (bijvoorbeeld `sky`) of een hiërarchische taxonomie vertegenwoordigen (bijvoorbeeld `fruit/apple`, dat wil zeggen zowel de generieke vrucht als de meer specifieke appel).
* Tags worden aangeduid met een unieke `TagID`.
* Een tag bevat optionele metagegevens, zoals een titel, gelokaliseerde titels en een beschrijving. De titel moet worden weergegeven in gebruikersinterfaces in plaats van `TagID`, indien aanwezig.

Met het coderingsframework kunt u auteurs en sitebezoekers ook beperken tot het gebruik van specifieke, vooraf gedefinieerde tags.

### Tagkenmerken {#tag-characteristics}

* Het knooppunttype is `cq:Tag`.
* De knooppuntnaam is een component van [`TagID`.](#tagid)
* [`TagID`](#tagid) bevat altijd een [naamruimte.](#tag-namespace)
* De eigenschap `jcr:title` (de titel die in de UI moet worden weergegeven) is optioneel.
* De eigenschap `jcr:description` is optioneel.
* Wanneer onderliggende knooppunten worden opgenomen, wordt dit een [containertag.](#container-tags)
* De tag wordt in de repository opgeslagen onder een basispad dat het [taxonomy root node wordt genoemd.](#taxonomy-root-node)

### TagID {#tagid}

A `TagID` identificeert een weg die aan een markeringsknoop in de bewaarplaats oplost.

De `TagID` is doorgaans een steno `TagID` die begint met de naamruimte of een absolute `TagID` die begint met het [taxonomy root-knooppunt.](#taxonomy-root-node)

Wanneer inhoud wordt geëtiketteerd, als het nog niet bestaat, wordt het [`cq:tags`](#cq-tags-property) bezit toegevoegd aan de inhoudsknoop en `TagID` wordt toegevoegd aan de `String` seriewaarde van het bezit.

De `TagID` bestaat uit een [naamruimte](#tag-namespace) gevolgd door de lokale `TagID`. [Container-](#container-tags) tags die een hiërarchische volgorde in de taxonomie aangeven. Subtags kunnen worden gebruikt om naar labels te verwijzen zoals elke lokale `TagID`. Inhoud bijvoorbeeld labelen met `fruit` is toegestaan, zelfs als het een containertag met subtags is, zoals `fruit/apple` en `fruit/banana`.

### Taxonomie basisknooppunt {#taxonomy-root-node}

Het basisknooppunt van de taxonomie is het basispad voor alle tags in de gegevensopslagruimte. De taxonomy wortelknoop moet *not* een knoop van type `cq:Tag` zijn.

In AEM is het basispad `/content/cq:tags` en het basisknooppunt is van het type `cq:Folder`.

### Tagnaamruimte {#tag-namespace}

Met naamruimten kunt u items groeperen. Het meest gangbare gebruik-hoofdlettergebruik is een naamruimte per site (bijvoorbeeld public versus internal) of per grotere toepassing (bijvoorbeeld Sites of Assets), maar naamruimten kunnen voor verschillende andere behoeften worden gebruikt. Naamruimten worden in de gebruikersinterface gebruikt om alleen de subset van tags (d.w.z. tags van een bepaalde naamruimte) weer te geven die van toepassing is op de huidige inhoud.

De naamruimte van de tag is het eerste niveau in de taxonomy-substructuur. Dit is het knooppunt direct onder het [taxonomy-hoofdknooppunt.](#taxonomy-root-node) Een naamruimte is een knooppunt van het type  `cq:Tag` waarvan het bovenliggende element geen  `cq:Tag` knooppunttype is.

Alle tags hebben een naamruimte. Als er geen naamruimte is opgegeven, wordt de tag toegewezen aan de standaardnaamruimte, te weten `TagID` `default`, d.w.z. `/content/cq:tags/default`.  In dergelijke gevallen wordt de titel standaard `Standard Tags`ingesteld.

### Containercodes {#container-tags}

Een containertag is een knooppunt van het type `cq:Tag` dat een willekeurig aantal onderliggende knooppunten en type bevat, waardoor het mogelijk is het tagmodel te verbeteren met aangepaste metagegevens.

Bovendien fungeren containercodes (of supercodes) in een taxonomie als de subsom van alle subcodes: inhoud die bijvoorbeeld is gelabeld met `fruit/apple` wordt ook beschouwd als gelabeld met `fruit`, d.w.z. als u zoekt naar inhoud die net gelabeld is met `fruit`, wordt ook de inhoud gevonden die gelabeld is met `fruit/apple`.

### TagID&#39;s oplossen {#resolving-tagids}

Als de tag-id een dubbele punt (`:`) bevat, scheidt de dubbele punt de naamruimte van de tag of de subtaxonomie, die vervolgens worden gescheiden met normale schuine strepen (`/`). Als de tag-id geen dubbele punt heeft, wordt de standaardnaamruimte geïmpliceerd.

De standaard en enige locatie van tags is lager dan `/content/cq:tags`.

Labels die verwijzen naar niet-bestaande paden of paden die niet verwijzen naar een `cq:Tag`-knooppunt, worden als ongeldig beschouwd en worden genegeerd.

In de volgende tabel ziet u een voorbeeld `TagID`s, de bijbehorende elementen en hoe de `TagID` wordt omgezet in een absoluut pad in de opslagplaats:

| `TagID` | Naamruimte | Lokale id | Containertag(s) | Label blad | Absoluut tagpad opslagplaats |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`,`apple` | `braeburn` | `content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | (none) | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | (geen) | (geen) | (geen) | `/content/cq:tags/dam` |
| `content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `content/cq:tags/category/car` |

### Lokalisatie van tagtitel {#localization-of-tag-title}

Wanneer de tag de optionele titeltekenreeks `jcr:title` bevat, is het mogelijk de titel voor weergave te lokaliseren door de eigenschap `jcr:title.<locale>` toe te voegen.

Zie voor meer informatie:

* [Tags in verschillende talen, ](tagging-applications.md#tags-in-different-languages) waarmee het gebruik van de API&#39;s als ontwikkelaar wordt beschreven
* Het beheren van Markeringen in Verschillende Talen, die gebruik van de Tagingconsole als beheerder beschrijft

### Toegangsbeheer {#access-control}

Tags bestaan als knooppunten in de opslagruimte onder het basisknooppunt [taxonomie.](#taxonomy-root-node) Het toestaan of ontkennen van auteurs en plaatsbezoekers om markeringen in een bepaalde namespace tot stand te brengen kan worden bereikt door aangewezen ACLs in de bewaarplaats te plaatsen.

Door het weigeren van leesmachtigingen voor bepaalde tags of naamruimten wordt de mogelijkheid ingesteld om codes toe te passen op specifieke inhoud.

Een gebruikelijke praktijk omvat:

* Het toestaan van `tag-administrators` groep/rol schrijft toegang tot alle namespaces (voeg toe/wijzig onder `/content/cq:tags`). Deze groep wordt geleverd met AEM out-of-the-box.
* Gebruikers/auteurs toegang verlenen tot alle naamruimten die voor hen (meestal alle) leesbaar moeten zijn.
* Gebruikers/auteurs toegang toestaan tot naamruimten waar tags vrij kunnen worden gedefinieerd door gebruikers/auteurs (`add_node` onder `/content/cq:tags/some_namespace`)

## Tagable Content: cq:Tagable Mixin {#taggable-content-cq-taggable-mixin}

Toepassingsontwikkelaars kunnen labels aan een inhoudstype koppelen als de registratie van het knooppunt ([CND](https://jackrabbit.apache.org/node-type-notation.html)) de `cq:Taggable`-mix of de `cq:OwnerTaggable`-mix bevat.

De `cq:OwnerTaggable` mix, die overerft van `cq:Taggable`, is bedoeld om aan te geven dat de inhoud kan worden geclassificeerd door de eigenaar/auteur. In AEM, is het slechts een attribuut van de `cq:PageContent` knoop. Het coderingsframework vereist geen `cq:OwnerTaggable`-mix.

>[!NOTE]
>
>Het wordt aanbevolen alleen tags in te schakelen op het knooppunt op het hoogste niveau van een samengevoegd inhoudsitem (of op het knooppunt `jcr:content`). Voorbeelden zijn:
>
>* Pagina&#39;s (`cq:Page`) waar het `jcr:content`knooppunt van het type `cq:PageContent` is, dat de `cq:Taggable`-mix bevat.
>* Middelen (`cq:Asset`) waar de `jcr:content/metadata` knoop altijd `cq:Taggable` mengt heeft.


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

De eigenschap `cq:tags` is een `String`-array die wordt gebruikt om een of meer `TagID`s op te slaan wanneer deze door auteurs of bezoekers van de site op inhoud worden toegepast. De eigenschap heeft alleen betekenis wanneer deze wordt toegevoegd aan een knooppunt dat is gedefinieerd met de [`cq:Taggable`](#taggable-content-cq-taggable-mixin)-mix.

>[!NOTE]
>
>Als u AEM tagfuncties wilt gebruiken, moeten aangepaste toepassingen alleen `cq:tags`-eigenschappen definiëren.

## Labels {#moving-and-merging-tags} verplaatsen en samenvoegen

Hieronder volgt een beschrijving van de effecten in de opslagplaats bij het verplaatsen of samenvoegen van tags met behulp van de Tagging-console.

Wanneer tag A wordt verplaatst of samengevoegd in tag B onder `/content/cq:tags`:

* Label A wordt niet verwijderd en ontvangt een eigenschap `cq:movedTo`.
   * `cq:movedTo` verwijst naar label B.
   * Deze eigenschap betekent dat tag A is verplaatst of samengevoegd met tag B.
   * Als tag B wordt verplaatst, wordt deze eigenschap dienovereenkomstig bijgewerkt.
   * Tag A is dus verborgen en wordt alleen in de opslagplaats bewaard om tag-id&#39;s op te lossen in inhoudsknooppunten die verwijzen naar tag A.
   * De opschoonfunctie voor ongewenste details verwijdert tags zoals tag A, als er geen inhoudsknooppunten meer naar wijzen.
   * Een speciale waarde voor de eigenschap `cq:movedTo` is `nirvana`, die wordt toegepast wanneer de tag wordt verwijderd, maar niet kan worden verwijderd uit de repository omdat er subtags zijn met een `cq:movedTo` die moeten worden bewaard.

      >[!NOTE]
      >
      >De eigenschap `cq:movedTo` wordt alleen toegevoegd aan de verplaatste of samengevoegde tag als aan een van deze voorwaarden wordt voldaan:
      >
      > 1. De tag wordt gebruikt in inhoud (wat betekent dat de tag een referentie heeft). OF
      > 1. De tag bevat onderliggende elementen die al zijn verplaatst.


* Label B wordt gemaakt (in het geval van een verplaatsing) en ontvangt een eigenschap `cq:backlinks`.
   * `cq:backlinks` houdt de verwijzingen in de andere richting, d.w.z. het houdt een lijst bij van alle markeringen die zijn verplaatst naar of samengevoegd met markering B.
   * Dit is vooral nodig om de `cq:movedTo`-eigenschappen up-to-date te houden wanneer tag B wordt verplaatst/samengevoegd/verwijderd of wanneer tag B wordt geactiveerd. In dat geval moeten alle tags met terugblik ook worden geactiveerd.

      >[!NOTE]
      >
      >De eigenschap `cq:backlinks` wordt alleen toegevoegd aan de verplaatste of samengevoegde tag als aan een van deze voorwaarden wordt voldaan:
      >
      > 1. De tag wordt gebruikt in inhoud (wat betekent dat de tag een referentie heeft). OF
      > 1. De tag bevat onderliggende elementen die al zijn verplaatst.


Bij het lezen van een eigenschap `cq:tags` van een inhoudsknooppunt wordt de volgende resolutie gebruikt:

1. Als er geen overeenkomst onder `/content/cq:tags` is, wordt geen markering teruggekeerd.
1. Als voor de tag een eigenschap `cq:movedTo` is ingesteld, wordt de tag-id waarnaar wordt verwezen gevolgd.
   * Deze stap wordt herhaald zolang de volgende markering een `cq:movedTo` bezit heeft.
1. Als de volgende tag geen eigenschap `cq:movedTo` heeft, wordt de tag gelezen.

Als u de wijziging wilt publiceren wanneer een tag is verplaatst of samengevoegd, moeten het knooppunt `cq:Tag` en alle bijbehorende back-ups worden gerepliceerd. Dit wordt automatisch gedaan wanneer de markering in de console van het markeringsbeleid wordt geactiveerd.

Later worden de oude verwijzingen automatisch opgeschoond door de `cq:tags`-eigenschap van de pagina. Dit wordt geactiveerd omdat het omzetten van een verplaatste tag via de API de doeltag retourneert, waardoor de doeltag-id wordt opgegeven.
