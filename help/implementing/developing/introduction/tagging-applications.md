---
title: Tags samenstellen in AEM toepassingen
description: Programmaticaal werken met tags of tags uitbreiden binnen een aangepaste AEM.
exl-id: a106dce1-5d51-406a-a563-4dea83987343
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---

# Tags samenstellen in AEM toepassingen {#building-tagging-into-aem-applications}

In dit document wordt beschreven hoe u programmatisch kunt werken met tags of tags wilt uitbreiden binnen een aangepaste AEM.

* [Tags-API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/package-summary.html)

die met de

* [Kader voor tags](tagging-framework.md)

Voor gerelateerde informatie over codering:

* Zie [Tags gebruiken](/help/sites-cloud/authoring/sites-console/tags.md) voor informatie over het labelen van inhoud als auteur van inhoud.
* Zie Tags beheren voor een beheerder. Het standpunt van de beheerder over het maken en beheren van tags en waarop inhoudstags zijn toegepast.

## Overzicht van de API voor tags {#overview-of-the-tagging-api}

De uitvoering van de [coderingskader](tagging-framework.md) in AEM staat het beheer van tags en tag-inhoud met behulp van de JCR API toe. `TagManager` zorgt ervoor dat tags die zijn ingevoerd als waarden in het dialoogvenster `cq:tags` array-eigenschap string wordt niet gedupliceerd, maar verwijderd `TagID`verwijst naar niet-bestaande tags en updates `TagID`s voor verplaatste of samengevoegde markeringen. `TagManager` gebruikt een JCR-observatielistener die onjuiste wijzigingen retourneert. De hoofdklassen bevinden zich in de [com.day.cq.tagging](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/package-summary.html) pakket:

* `JcrTagManagerFactory` - retourneert een JCR-gebaseerde implementatie van een `TagManager`. Dit is de referentie-implementatie van de API voor labelen.
* `TagManager` - Hiermee kunt u tags oplossen en maken op basis van paden en namen.
* `Tag` - definieert het labelobject.

### Een op JCR gebaseerde tagbeheer ophalen {#getting-a-jcr-based-tagmanager}

Om een `TagManager` -instantie, hebt u een JCR nodig `Session` en te bellen `getTagManager(Session)`:

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

In de typische verkoopcontext kunt u zich ook aanpassen aan een `TagManager` van de `ResourceResolver`:

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### Een tagobject ophalen {#retrieving-a-tag-object}

A `Tag` kan worden opgehaald via de `TagManager`door een bestaande tag op te lossen of een bestaande tag te maken:

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

Voor de op JCR gebaseerde implementatie, die kaarten `Tags` op JCR `Nodes`, kunt u rechtstreeks gebruikmaken van de `adaptTo` mechanisme als u de bron hebt (bijvoorbeeld `/content/cq:tags/default/my/tag`):

```java
Tag tag = resource.adaptTo(Tag.class);
```

Een tag mag alleen worden omgezet *van* een bron (geen knooppunt), een tag kan worden omgezet *tot* zowel een knooppunt als een bron:

```java
Node node = tag.adaptTo(Node.class);
Resource node = tag.adaptTo(Resource.class);
```

>[!NOTE]
>
>Rechtstreeks aanpassen van `Node` tot `Tag` is niet mogelijk, omdat `Node` implementeert Sling niet `Adaptable.adaptTo(Class)` methode.

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
>De geldige `RangeIterator` te gebruiken is:
>
>`com.day.cq.commons.RangeIterator`

### Tags verwijderen {#deleting-tags}

```java
tagManager.deleteTag(tag);
```

### Codes dupliceren {#replicating-tags}

Het is mogelijk om de replicatiedienst te gebruiken (`Replicator`) met tags omdat tags van het type zijn `nt:hierarchyNode`:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## De opschoonfunctie voor tags {#the-tag-garbage-collector}

De opschoonfunctie voor tags is een service op de achtergrond die verborgen en ongebruikte tags opruimt. Verborgen en ongebruikte tags zijn onderliggende codes `/content/cq:tags` die een `cq:movedTo` en worden niet gebruikt op een inhoudsknooppunt. Ze hebben een getal van nul. Door dit lazy schrappingsproces te gebruiken, de inhoudknoop (namelijk `cq:tags` eigenschap) hoeft niet te worden bijgewerkt als onderdeel van de verplaatsings- of samenvoegbewerking. De verwijzingen in de `cq:tags` eigenschap wordt automatisch bijgewerkt wanneer de `cq:tags` Deze eigenschap wordt bijvoorbeeld bijgewerkt via het dialoogvenster Pagina-eigenschappen.

De opschoonfunctie voor tags wordt standaard eenmaal per dag uitgevoerd. Dit kan worden gevormd bij:

`http://<host>:<port>/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector`

## Zoeken naar tags en taglijst {#tag-search-and-tag-listing}

De zoekopdracht naar tags en het tagoverzicht werkt als volgt:

* De zoekopdracht naar `TagID` zoekt naar de tags met de eigenschap `cq:movedTo` instellen op `TagID` en volgt de `cq:movedTo` `TagID`s.
* De zoekopdracht naar de titel van een tag zoekt alleen naar de tags zonder een `cq:movedTo` eigenschap.

## Tags in verschillende talen {#tags-in-different-languages}

Een tag `title` kunnen in verschillende talen worden gedefinieerd. Vervolgens wordt een taalgevoelige eigenschap toegevoegd aan het tagknooppunt. Deze eigenschap heeft de indeling `jcr:title.<locale>`, bijvoorbeeld `jcr:title.fr` voor de Franse vertaling. `<locale>` moet een ISO-tekenreeks voor kleine letters zijn en een onderstrepingsteken gebruiken (`_`) in plaats van koppelteken/streepje (`-`), bijvoorbeeld: `de_ch`.

Als u bijvoorbeeld **Dieren** -tag wordt toegevoegd aan de **Producten** pagina, de waarde `stockphotography:animals` wordt toegevoegd aan de eigenschap `cq:tags` van het knooppunt `/content/wknd/en/products/jcr:content`. Er wordt naar de vertaling verwezen vanuit het tagknooppunt.

De server-side API heeft gelokaliseerd `title`-gerelateerde methoden:

* [`com.day.cq.tagging.Tag`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/Tag.html)
   * `getLocalizedTitle(Locale locale)`
   * `getLocalizedTitlePaths()`
   * `getLocalizedTitles()`
   * `getTitle(Locale locale)`
   * `getTitlePath(Locale locale)`
* [`com.day.cq.tagging.TagManager`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/TagManager.html)
   * `canCreateTagByTitle(String tagTitlePath, Locale locale)`
   * `createTagByTitle(String tagTitlePath, Locale locale)`
   * `resolveByTitle(String tagTitlePath, Locale locale)`

In AEM kan de taal worden opgehaald uit de paginataal of uit de taal van de gebruiker.

Bij het labelen is lokalisatie afhankelijk van de context als tag `titles` kan worden weergegeven in de paginataal, in de gebruikerstaal of in een andere taal.

### Een nieuwe taal toevoegen aan het dialoogvenster Tag bewerken {#adding-a-new-language-to-the-edit-tag-dialog}

In de volgende procedure wordt beschreven hoe u een nieuwe taal (bijvoorbeeld Fins) aan de **Tag bewerken** dialoogvenster:

1. In **CRXDE**, bewerkt u de eigenschap voor meerdere waarden `languages` van het knooppunt `/content/cq:tags`.
1. Toevoegen `fi_fi`, die staat voor de Finse landinstelling, en sla de wijzigingen op.

Het Fins is nu beschikbaar in het tagdialoogvenster van de pagina-eigenschappen en in het dialoogvenster **Tag bewerken** wanneer u een tag bewerkt in het dialoogvenster **Tags** console.

>[!NOTE]
>
>De nieuwe taal moet een van de AEM erkende talen zijn. Dit wil zeggen dat het bestand beschikbaar moet zijn als een hieronder opgegeven knooppunt `/libs/wcm/core/resources/languages`.
