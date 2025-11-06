---
title: AEM Tagging Framework
description: Tags toewijzen aan inhoud en de AEM Tags toevoegen-infrastructuur gebruiken om de inhoud te categoriseren en te ordenen.
exl-id: 25418d44-aace-4e73-be1a-4b1902f40403
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1559'
ht-degree: 0%

---

# AEM Tagging Framework {#aem-tagging-framework}

Door tags toe te wijzen, kunt u inhoud indelen en ordenen. Tags kunnen worden geclassificeerd door een naamruimte en een taxonomie. Voor gedetailleerde informatie over het gebruik van tags:

* Zie [&#x200B; Gebruikend Markeringen &#x200B;](/help/sites-cloud/authoring/sites-console/tags.md) voor informatie over het etiketteren van inhoud als inhoudauteur.
* Zie Tags beheren voor een beheerder. Het standpunt van de beheerder over het maken en beheren van tags en waarop inhoudstags zijn toegepast.

Dit artikel richt zich op het onderliggende kader dat het etiketteren in AEM steunt en hoe te om het als ontwikkelaar te gebruiken.

## Inleiding {#introduction}

U kunt als volgt inhoud labelen en de AEM-taginfrastructuur gebruiken:

* De markering moet als knoop van type [`cq:Tag`](#cq-tag-node-type) onder de [&#x200B; taxonomy wortelknoop &#x200B;](#taxonomy-root-node) bestaan.
* In het knooppunt `NodeType` met gecodeerde inhoud moet de [`cq:Taggable`](#taggable-content-cq-taggable-mixin) -mix zijn opgenomen.
* [`TagID`](#tagid) wordt toegevoegd aan de eigenschap [`cq:tags`](#cq-tags-property) van het inhoudsknooppunt en wordt omgezet in een knooppunt van het type [`cq:Tag`](#cq-tag-node-type) .

## cq:Tag Type knooppunt {#cq-tag-node-type}

De declaratie van een tag wordt vastgelegd in de repository in een knooppunt van het type `cq:Tag.`

* Een tag kan een eenvoudig woord zijn (bijvoorbeeld `sky` ) of een hiërarchische taxonomie vertegenwoordigen (bijvoorbeeld `fruit/apple` , wat zowel de algemene vrucht als de specifiekere appel betekent).
* Tags worden aangeduid met een unieke `TagID` .
* Een tag bevat optionele metagegevens, zoals een titel, gelokaliseerde titels en een beschrijving. De titel moet worden weergegeven in gebruikersinterfaces in plaats van de `TagID` , indien aanwezig.

Het coderingskader beperkt auteurs en sitebezoekers ook tot het gebruik van alleen specifieke, vooraf gedefinieerde tags.

### Tagkenmerken {#tag-characteristics}

* Het knooppunttype is `cq:Tag` .
* De knooppuntnaam is een component van [`TagID`](#tagid).
* [`TagID`](#tagid) omvat altijd a [&#x200B; namespace &#x200B;](#tag-namespace).
* De eigenschap `jcr:title` (de titel die in de UI moet worden weergegeven) is optioneel.
* De eigenschap `jcr:description` is optioneel.
* Wanneer het bevatten van kindknopen, wordt bedoeld als a [&#x200B; containermarkering &#x200B;](#container-tags).
* De markering wordt opgeslagen in de bewaarplaats onder een basisweg genoemd de [&#x200B; taxonomie wortelknoop &#x200B;](#taxonomy-root-node).

### TagID {#tagid}

Een `TagID` identificeert een pad dat wordt omgezet naar een tagknooppunt in de opslagplaats.

Typisch, is `TagID` een steno `TagID` die met namespace begint of het kan een absolute `TagID` zijn die van de [&#x200B; taxonomy wortelknoop &#x200B;](#taxonomy-root-node) begint.

Wanneer inhoud wordt gelabeld en nog niet bestaat, wordt de eigenschap [`cq:tags`](#cq-tags-property) toegevoegd aan het inhoudsknooppunt en wordt de eigenschap `TagID` toegevoegd aan de arraywaarde van de eigenschap `String` .

`TagID` bestaat uit a [&#x200B; namespace &#x200B;](#tag-namespace) die door lokaal `TagID` wordt gevolgd. [&#x200B; de markeringen van de Container &#x200B;](#container-tags) hebben subtags die een hiërarchische orde in de taxonomie vertegenwoordigen. Subtags kunnen worden gebruikt om naar labels te verwijzen zoals elke lokale `TagID` . Inhoud bijvoorbeeld labelen met `fruit` is toegestaan, zelfs als het een containertag met subtags betreft, zoals `fruit/apple` en `fruit/banana` .

### Taxonomy Root Node {#taxonomy-root-node}

Het basisknooppunt van de taxonomie is het basispad voor alle tags in de gegevensopslagruimte. De taxonomie wortelknoop moet ** geen knoop van type `cq:Tag` zijn.

In AEM is het basispad `/content/cq:tags` en het basisknooppunt is van het type `cq:Folder` .

### Tagnaamruimte {#tag-namespace}

Met naamruimten kunt u items groeperen. Het meest gangbare gebruik-hoofdlettergebruik is het hebben van een naamruimte per site (bijvoorbeeld public versus internal) of per grotere toepassing (bijvoorbeeld Sites of Assets), maar naamruimten kunnen voor verschillende andere behoeften worden gebruikt. Naamruimten worden in de gebruikersinterface gebruikt om alleen de subset van tags (dat wil zeggen tags van een bepaalde naamruimte) weer te geven die van toepassing is op de huidige inhoud.

De namespace van de markering is het eerste niveau in taxonomy subtree, die de knoop onmiddellijk onder de [&#x200B; taxonomy wortelknoop &#x200B;](#taxonomy-root-node) is. Een naamruimte is een knooppunt van het type `cq:Tag` waarvan het bovenliggende element geen knooppunttype `cq:Tag` is.

Alle tags hebben een naamruimte. Wanneer geen naamruimte is opgegeven, wordt de tag toegewezen aan de standaardnaamruimte, namelijk `TagID` `default` , dat wil zeggen `/content/cq:tags/default` . In dergelijke gevallen wordt Titel standaard ingesteld op `Standard Tags` .

### Containerlabels {#container-tags}

Een containertag is een knooppunt van het type `cq:Tag` dat een willekeurig aantal onderliggende knooppunten en type bevat, zodat het tagmodel kan worden verbeterd met aangepaste metagegevens.

Bovendien fungeren containercodes (of super-tags) in een taxonomie als de subsummatie van alle subtags. Inhoud die is gelabeld met `fruit/apple` wordt bijvoorbeeld ook beschouwd als gelabeld met `fruit` . Als u dus zoekt naar inhoud die is gelabeld met `fruit` , wordt ook de inhoud gevonden die is gelabeld met `fruit/apple` .

### TagID&#39;s oplossen {#resolving-tagids}

Als de tag-id een dubbele punt (`:`) bevat, scheidt de dubbele punt de naamruimte van de tag of subtaxonomie, die vervolgens worden gescheiden met normale schuine strepen (`/` ). Als de tag-id geen dubbele punt heeft, wordt de standaardnaamruimte geïmpliceerd.

De standaardlocatie en de enige locatie voor tags is lager dan `/content/cq:tags` .

Labels die verwijzen naar niet-bestaande paden of paden die niet naar een knooppunt `cq:Tag` verwijzen, worden als ongeldig beschouwd en worden genegeerd.

In de volgende tabel ziet u een voorbeeld `TagID` s, de bijbehorende elementen en de manier waarop `TagID` wordt omgezet in een absoluut pad in de opslagplaats:

| `TagID` | Naamruimte | Lokale id | Containerlabels | Label blad | Absoluut tagpad opslagplaats |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`, `apple` | `braeburn` | `content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | (geen) | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | (geen) | (geen) | (geen) | `/content/cq:tags/dam` |
| `content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `content/cq:tags/category/car` |

### Localisatie van tagtitel {#localization-of-tag-title}

Wanneer de tag de optionele titeltekenreeks `jcr:title` bevat, is het mogelijk de titel voor weergave te lokaliseren door de eigenschap `jcr:title.<locale>` toe te voegen.

Raadpleeg de volgende secties voor meer informatie:

* [&#x200B; de Markeringen in Verschillende Talen &#x200B;](tagging-applications.md#tags-in-different-languages) beschrijven het gebruik van APIs als ontwikkelaar
* Tags beheren in verschillende talen, die het gebruik van de tagconsole als beheerder beschrijven

### Toegangsbeheer {#access-control}

De markeringen bestaan als knopen in de bewaarplaats onder de [&#x200B; taxonomie wortelknoop &#x200B;](#taxonomy-root-node). Het toestaan of ontkennen van auteurs en plaatsbezoekers om markeringen in een bepaalde namespace tot stand te brengen kan worden bereikt door aangewezen ACLs in de bewaarplaats te plaatsen.

Door het weigeren van leesmachtigingen voor bepaalde tags of naamruimten wordt de mogelijkheid ingesteld om codes toe te passen op specifieke inhoud.

Een gebruikelijke praktijk omvat:

* De `tag-administrators` -groep/rol schrijftoegang toestaan tot alle naamruimten (toevoegen/wijzigen onder `/content/cq:tags` ). Deze groep wordt geleverd met AEM.
* Gebruikers/auteurs toegang verlenen tot alle naamruimten die voor hen (meestal alle) leesbaar moeten zijn.
* Gebruikers/auteurs toegang toestaan tot naamruimten waar tags vrij kunnen worden gedefinieerd door gebruikers/auteurs (`add_node` onder `/content/cq:tags/some_namespace` )

## Tagable Content : cq :Taggable Mixin {#taggable-content-cq-taggable-mixin}

Voor toepassingsontwikkelaars om het etiketteren aan een inhoudstype vast te maken, moet de registratie van de knoop ([&#x200B; CND &#x200B;](https://jackrabbit.apache.org/jcr/node-type-notation.html)) `cq:Taggable` mengen of `cq:OwnerTaggable` mengen omvatten.

De `cq:OwnerTaggable` -mix, die overerft van `cq:Taggable` , geeft aan dat de inhoud kan worden geclassificeerd door de eigenaar/auteur. In AEM is het alleen een kenmerk van het knooppunt `cq:PageContent` . Het coderingsframework vereist de `cq:OwnerTaggable` -mix niet.

>[!NOTE]
>
>Het wordt aanbevolen alleen tags in te schakelen op het knooppunt op het hoogste niveau van een samengevoegd inhoudsitem (of op het knooppunt `jcr:content` ervan). Voorbeelden zijn:
>
>* De pagina&#39;s (`cq:Page`) waar de `jcr:content` knoop van type `cq:PageContent` is, die `cq:Taggable` mixin omvat.
>* Assets (`cq:Asset`) waar het `jcr:content/metadata` -knooppunt altijd de `cq:Taggable` -mix heeft.

### Node Type Notation (CND) {#node-type-notation-cnd}

Node Type definities bestaan in de bewaarplaats als Cnd- dossiers. De aantekening CND wordt bepaald als deel van de [&#x200B; documentatie JCR &#x200B;](https://jackrabbit.apache.org/jcr/node-type-notation.html).

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

## cq:tags Eigenschap {#cq-tags-property}

De eigenschap `cq:tags` is een `String` -array die wordt gebruikt om een of meer `TagID` s op te slaan wanneer deze door auteurs of sitebezoekers op inhoud worden toegepast. De eigenschap heeft alleen betekenis wanneer deze wordt toegevoegd aan een knooppunt dat met de [`cq:Taggable`](#taggable-content-cq-taggable-mixin) -mix is gedefinieerd.

>[!NOTE]
>
>Als u de AEM-tagfuncties wilt gebruiken, moeten aangepaste toepassingen geen andere tageigenschappen definiëren dan `cq:tags` .

## Labels verplaatsen en samenvoegen {#moving-and-merging-tags}

Hieronder volgt een beschrijving van de effecten in de opslagplaats bij het verplaatsen of samenvoegen van tags met behulp van de Tagging-console.

Wanneer tag A onder `/content/cq:tags` wordt verplaatst of samengevoegd in tag B:

* Label A wordt niet verwijderd en ontvangt een eigenschap `cq:movedTo` .
   * `cq:movedTo` verwijst naar label B.
   * Deze eigenschap betekent dat tag A is verplaatst of samengevoegd met tag B.
   * Als u tag B verplaatst, wordt deze eigenschap dienovereenkomstig bijgewerkt.
   * Tag A is daarom verborgen en wordt alleen in de gegevensopslagruimte bewaard, zodat tags-id&#39;s kunnen worden opgelost in inhoudsknooppunten die verwijzen naar tag A.
   * De opschoonfunctie voor ongewenste details verwijdert tags zoals tag A, als er geen inhoudsknooppunten meer naar wijzen.
   * Een speciale waarde voor de eigenschap `cq:movedTo` is `nirvana` , die wordt toegepast wanneer de tag wordt verwijderd, maar niet uit de opslagplaats kan worden verwijderd omdat er subtags met een `cq:movedTo` zijn die moeten worden bewaard.

     >[!NOTE]
     >
     >De eigenschap `cq:movedTo` wordt alleen aan de verplaatste of samengevoegde tag toegevoegd als aan een van deze voorwaarden wordt voldaan:
     >
     > 1. De tag wordt gebruikt in inhoud (wat betekent dat de tag een referentie heeft). OF
     > 1. De tag bevat onderliggende elementen die al zijn verplaatst.
     >
* Label B wordt gemaakt (als er sprake is van een verplaatsing) en ontvangt een eigenschap `cq:backlinks` .
   * `cq:backlinks` houdt de verwijzingen in de andere richting. Dit betekent dat er een lijst wordt bijgehouden met alle tags die zijn verplaatst naar of samengevoegd met tag B.
   * Deze functionaliteit is vooral vereist om de eigenschappen van `cq:movedTo` up-to-date te houden wanneer tag B wordt verplaatst/samengevoegd/verwijderd of als tag B wordt geactiveerd. In dat geval moeten alle tags voor de achtergrond ook worden geactiveerd.

     >[!NOTE]
     >
     >De eigenschap `cq:backlinks` wordt alleen aan de verplaatste of samengevoegde tag toegevoegd als aan een van deze voorwaarden wordt voldaan:
     >
     > 1. De tag wordt gebruikt in inhoud (wat betekent dat deze een referentie heeft), of
     > 1. De tag bevat onderliggende elementen die al zijn verplaatst.

Het lezen van een eigenschap `cq:tags` van een inhoudsknooppunt heeft de volgende resolutie:

1. Als er geen overeenkomst is onder `/content/cq:tags` , wordt geen tag geretourneerd.
1. Als de tag een eigenschap `cq:movedTo` heeft ingesteld, wordt de tag-id waarnaar wordt verwezen gevolgd.
   * Deze stap wordt herhaald zolang de volgende tag de eigenschap `cq:movedTo` heeft.
1. Als de volgende tag geen eigenschap `cq:movedTo` heeft, wordt de tag gelezen.

Als u de wijziging wilt publiceren wanneer een tag is verplaatst of samengevoegd, moeten het knooppunt `cq:Tag` en alle bijbehorende back-ups worden gerepliceerd. Deze replicatie wordt automatisch uitgevoerd wanneer de tag wordt geactiveerd in de beheerconsole van de tag.

Verderop worden de oude verwijzingen automatisch opgeschoond door de `cq:tags` -eigenschap van de pagina bij te werken. De opschoning wordt geactiveerd omdat het omzetten van een verplaatste tag via de API de doeltag retourneert, waardoor de doeltag-id wordt opgegeven.
