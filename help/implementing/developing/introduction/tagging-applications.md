---
title: Tags samenstellen in AEM toepassingen
description: Programmaticaal werken met tags of tags uitbreiden binnen een aangepaste AEM.
translation-type: tm+mt
source-git-commit: ce55065c3ae6a2350ed06811af76477df7c11291
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 0%

---


# Tags samenstellen in AEM toepassingen {#building-tagging-into-aem-applications}

In dit document wordt beschreven hoe u programmatisch kunt werken met tags of tags wilt uitbreiden binnen een aangepaste AEM.

* [Tags-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/package-summary.html)

die met de

* [Kader voor tags](tagging-framework.md)

Voor gerelateerde informatie over codering:

* Zie [Tags](/help/sites-cloud/authoring/features/tags.md) gebruiken voor informatie over het labelen van inhoud als auteur van inhoud.
* Zie Tags beheren voor een beheerder. Het perspectief van de beheerder op het maken en beheren van tags en op welke inhoudstags zijn toegepast.

## Overzicht van de API voor tags {#overview-of-the-tagging-api}

Door de implementatie van het [coderingsframework](tagging-framework.md) in AEM kunt u tags en code-inhoud beheren met de JCR API. `TagManager` zorgt ervoor dat tags die zijn ingevoerd als waarden in de `cq:tags` array-eigenschap string niet worden gedupliceerd, verwijdert deze tags die verwijzen naar niet-bestaande tags en updates `TagID``TagID`voor verplaatste of samengevoegde tags. `TagManager` gebruikt een JCR-observatielistener die onjuiste wijzigingen retourneert. De belangrijkste klassen bevinden zich in het [com.day.cq.tagging](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/package-summary.html) pakket:

* `JcrTagManagerFactory` - retourneert een JCR-gebaseerde implementatie van een `TagManager`. Dit is de referentie-implementatie van de API voor labelen.
* `TagManager` - Hiermee kunt u tags oplossen en maken op basis van paden en namen.
* `Tag` - definieert het labelobject.

### Een op JCR gebaseerde tagbeheer ophalen {#getting-a-jcr-based-tagmanager}

Om een `TagManager` instantie terug te winnen, moet u JCR hebben `Session` en roepen `getTagManager(Session)`:

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

In de typische context van het Verkopen kunt u zich aan een `TagManager` van `ResourceResolver`:

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### Een tagobject ophalen {#retrieving-a-tag-object}

U `Tag` kunt een bestaande tag opvragen `TagManager`door een nieuwe tag te maken:

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

Voor de op JCR-Gebaseerde implementatie, die kaarten `Tags` op JCR `Nodes`, kunt u het `adaptTo` mechanisme van Sling direct gebruiken als u het middel (b.v. `/content/cq:tags/default/my/tag`) hebt:

```java
Tag tag = resource.adaptTo(Tag.class);
```

Hoewel een tag alleen *vanuit* een bron (geen knooppunt) mag worden omgezet, kan een tag worden omgezet *in* zowel een knooppunt als een bron:

```java
Node node = tag.adaptTo(Node.class);
Resource node = tag.adaptTo(Resource.class);
```

>[!NOTE]
>
>Directe aanpassing van `Node` aan `Tag` is niet mogelijk, omdat `Node` de methode Sling niet wordt geïmplementeerd `Adaptable.adaptTo(Class)` .

### Labels ophalen en instellen {#getting-and-setting-tags}

```java
// Getting the tags of a Resource:
Tag[] tags = tagManager.getTags(resource);

// Setting tags to a Resource:
tagManager.setTags(resource, tags);
```

### Zoeken naar tags {#searching-for-tags}

```java
// Searching for the Resource objects that are tagged with the tag object:
Iterator<Resource> it = tag.find();

// Retrieving the usage count of the tag object:
long count = tag.getCount();

// Searching for the Resource objects that are tagged with the tagID String:
 RangeIterator<Resource> it = tagManager.find(tagID);
```

>[!NOTE]
>
>De geldige waarden `RangeIterator` zijn:
>
>`com.day.cq.commons.RangeIterator`

### Tags verwijderen {#deleting-tags}

```java
tagManager.deleteTag(tag);
```

### Codes dupliceren {#replicating-tags}

Het is mogelijk om de replicatieservice (`Replicator`) met markeringen te gebruiken omdat de markeringen van type zijn `nt:hierarchyNode`:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## De opschoonfunctie voor tags {#the-tag-garbage-collector}

De opschoonfunctie voor tags is een service op de achtergrond die verborgen en ongebruikte tags opruimt. Verborgen en ongebruikte tags zijn onderliggende tags `/content/cq:tags` die een `cq:movedTo` eigenschap hebben en niet worden gebruikt op een inhoudsknooppunt. Ze hebben een getal van nul. Door dit lazy schrappingsproces te gebruiken, moet de inhoudsknoop (d.w.z. het `cq:tags` bezit) niet als deel van de beweging of de fusieverrichting worden bijgewerkt. De verwijzingen in het `cq:tags` bezit worden automatisch bijgewerkt wanneer het `cq:tags` bezit wordt bijgewerkt, bijvoorbeeld door de dialoog van de pagina eigenschappen.

De opschoonfunctie voor tags wordt standaard eenmaal per dag uitgevoerd. Dit kan worden gevormd bij:

`http://<host>:<port>/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector`

## Zoeken en taglijst {#tag-search-and-tag-listing}

De zoekopdracht naar tags en het tagoverzicht werkt als volgt:

* De zoekopdracht `TagID` zoekt naar de tags waarvoor de eigenschap is `cq:movedTo` ingesteld op `TagID` en volgt de `cq:movedTo` `TagID`s.
* De zoekopdracht naar de titel van een tag zoekt alleen naar de tags die geen `cq:movedTo` eigenschap hebben.

## Tags in verschillende talen {#tags-in-different-languages}

Een tag `title` kan in verschillende talen worden gedefinieerd. Vervolgens wordt een taalgevoelige eigenschap toegevoegd aan het tagknooppunt. Deze eigenschap heeft de indeling `jcr:title.<locale>`, bijvoorbeeld `jcr:title.fr` voor de Franse vertaling. `<locale>` moet een ISO-tekenreeks voor kleine letters zijn en onderstrepingsteken (`_`) gebruiken in plaats van een koppelteken/streepje (`-`), bijvoorbeeld: `de_ch`.

Wanneer bijvoorbeeld de tag **Dieren** wordt toegevoegd aan de pagina **Producten** , `stockphotography:animals` wordt de waarde toegevoegd aan de eigenschap `cq:tags` van het knooppunt `/content/wknd/en/products/jcr:content`. Er wordt naar de vertaling verwezen vanuit het tagknooppunt.

De server-side API heeft gelokaliseerde `title`gerelateerde methoden:

* [`com.day.cq.tagging.Tag`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/Tag.html)
   * `getLocalizedTitle(Locale locale)`
   * `getLocalizedTitlePaths()`
   * `getLocalizedTitles()`
   * `getTitle(Locale locale)`
   * `getTitlePath(Locale locale)`
* [`com.day.cq.tagging.TagManager`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/TagManager.html)
   * `canCreateTagByTitle(String tagTitlePath, Locale locale)`
   * `createTagByTitle(String tagTitlePath, Locale locale)`
   * `resolveByTitle(String tagTitlePath, Locale locale)`

In AEM kan de taal worden opgehaald uit de paginataal of uit de taal van de gebruiker.

Bij het labelen hangt de lokalisatie af van de context, aangezien de tag in de paginataal, in de gebruikerstaal of in een andere taal `titles` kan worden weergegeven.

### Een nieuwe taal toevoegen aan het dialoogvenster Tag bewerken {#adding-a-new-language-to-the-edit-tag-dialog}

De volgende procedure beschrijft hoe u een nieuwe taal (bijvoorbeeld Fins) kunt toevoegen aan het dialoogvenster **Tags bewerken** :

1. Bewerk in **CRXDE** de eigenschap voor meerdere waarden `languages` van het knooppunt `/content/cq:tags`.
1. Voeg toe `fi_fi`, die de Finse landinstelling vertegenwoordigt, en sla de wijzigingen op.

Het Fins is nu beschikbaar in het tagdialoogvenster van de pagina-eigenschappen en in het dialoogvenster Tag **** bewerken wanneer u een tag bewerkt in de **tagconsole** .

>[!NOTE]
>
>De nieuwe taal moet een van de AEM erkende talen zijn, d.w.z. het moet beschikbaar zijn als hieronder knooppunt `/libs/wcm/core/resources/languages`.
