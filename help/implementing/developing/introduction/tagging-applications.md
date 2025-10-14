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

* [&#x200B; Tagging API &#x200B;](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/package-summary.html)

die met de

* [Kader voor tags](tagging-framework.md)

Voor gerelateerde informatie over codering:

* Zie [&#x200B; Gebruikend Markeringen &#x200B;](/help/sites-cloud/authoring/sites-console/tags.md) voor informatie over het etiketteren van inhoud als inhoudauteur.
* Zie Tags beheren voor een beheerder. Het standpunt van de beheerder over het maken en beheren van tags en waarop inhoudstags zijn toegepast.

## Overzicht van de API voor tags {#overview-of-the-tagging-api}

De implementatie van het [&#x200B; etiketterende kader &#x200B;](tagging-framework.md) in AEM staat beheer van markeringen en markeringsinhoud toe gebruikend JCR API. `TagManager` zorgt ervoor dat tags die zijn ingevoerd als waarden voor de eigenschap `cq:tags` string array, niet worden gedupliceerd, `TagID` verwijdert het aanwijzen van niet-bestaande tags en werkt `TagID` s bij voor verplaatste of samengevoegde tags. `TagManager` gebruikt een JCR-observatielistener die onjuiste wijzigingen retourneert. De belangrijkste klassen zijn in het [&#x200B; com.day.cq.tagging &#x200B;](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/package-summary.html) pakket:

* `JcrTagManagerFactory` - retourneert een op JCR gebaseerde implementatie van een `TagManager` . Dit is de referentie-implementatie van de API voor labelen.
* `TagManager` - Hiermee kunt u tags oplossen en maken op basis van paden en namen.
* `Tag` - definieert het tagobject.

### Een op JCR gebaseerde tagbeheer ophalen {#getting-a-jcr-based-tagmanager}

Als u een `TagManager` -instantie wilt ophalen, hebt u een JCR `Session` nodig en moet u `getTagManager(Session)` aanroepen:

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

In de standaardcontext van Verdelen kunt u zich ook aanpassen aan een `TagManager` van `ResourceResolver`:

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### Een tagobject ophalen {#retrieving-a-tag-object}

Een `Tag` kan via `TagManager` worden opgehaald door een bestaande tag op te lossen of een bestaande tag te maken:

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

Voor de op JCR gebaseerde implementatie, die `Tags` op JCR `Nodes` in kaart brengt, kunt u het mechanisme van `adaptTo` van Sling direct gebruiken als u de bron hebt (bijvoorbeeld, zoals `/content/cq:tags/default/my/tag`):

```java
Tag tag = resource.adaptTo(Tag.class);
```

Terwijl een markering slechts *van* een middel (niet een knoop) kan worden omgezet, kan een markering *in* zowel een knoop als een middel worden omgezet:

```java
Node node = tag.adaptTo(Node.class);
Resource node = tag.adaptTo(Resource.class);
```

>[!NOTE]
>
>Rechtstreeks aanpassen van `Node` naar `Tag` is niet mogelijk, omdat `Node` de methode Sling `Adaptable.adaptTo(Class)` niet implementeert.

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
>De geldige `RangeIterator` die moet worden gebruikt is:
>
>`com.day.cq.commons.RangeIterator`

### Tags verwijderen {#deleting-tags}

```java
tagManager.deleteTag(tag);
```

### Codes dupliceren {#replicating-tags}

Het is mogelijk om de replicatieservice (`Replicator`) met markeringen te gebruiken omdat de markeringen van type `nt:hierarchyNode` zijn:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## De opschoonfunctie voor tags {#the-tag-garbage-collector}

De opschoonfunctie voor tags is een service op de achtergrond die verborgen en ongebruikte tags opruimt. Verborgen en ongebruikte tags zijn tags onder `/content/cq:tags` die een eigenschap `cq:movedTo` hebben en niet worden gebruikt op een inhoudsknooppunt. Ze hebben een getal van nul. Door dit luie verwijderingsproces te gebruiken, hoeft het inhoudsknooppunt (de eigenschap `cq:tags` ) niet te worden bijgewerkt als onderdeel van de verplaatsings- of samenvoegbewerking. De verwijzingen in de eigenschap `cq:tags` worden automatisch bijgewerkt wanneer de eigenschap `cq:tags` wordt bijgewerkt, bijvoorbeeld via het dialoogvenster met pagina-eigenschappen.

De opschoonfunctie voor tags wordt standaard eenmaal per dag uitgevoerd. Dit kan worden gevormd bij:

`http://<host>:<port>/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector`

## Zoeken naar tags en taglijst {#tag-search-and-tag-listing}

De zoekopdracht naar tags en het tagoverzicht werkt als volgt:

* Bij de zoekopdracht naar `TagID` wordt gezocht naar de tags waarvan de eigenschap `cq:movedTo` is ingesteld op `TagID` en wordt de `cq:movedTo` `TagID` -tag gevolgd.
* De zoekopdracht naar de titel van een tag zoekt alleen naar de tags zonder de eigenschap `cq:movedTo` .

## Tags in verschillende talen {#tags-in-different-languages}

Een tag `title` kan in verschillende talen worden gedefinieerd. Vervolgens wordt een taalgevoelige eigenschap toegevoegd aan het tagknooppunt. Deze eigenschap heeft de notatie `jcr:title.<locale>` , bijvoorbeeld `jcr:title.fr` voor de Franse vertaling. `<locale>` moet een tekenreeks met een kleine ISO-landinstelling zijn en een onderstrepingsteken (`_` ) gebruiken in plaats van een koppelteken/streepje (`-` ), bijvoorbeeld: `de_ch` .

Bijvoorbeeld, wanneer de **Dieren** markering aan de **Produkten** pagina wordt toegevoegd, wordt de waarde `stockphotography:animals` toegevoegd aan het bezit `cq:tags` van de knoop `/content/wknd/en/products/jcr:content`. Er wordt naar de vertaling verwezen vanuit het tagknooppunt.

De server-side API heeft gelokaliseerde `title` -gerelateerde methoden:

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

Bij het labelen hangt de lokalisatie af van de context, aangezien de tag `titles` kan worden weergegeven in de paginataal, in de gebruikerstaal of in een andere taal.

### Een nieuwe taal toevoegen aan het dialoogvenster Tag bewerken {#adding-a-new-language-to-the-edit-tag-dialog}

De volgende procedure beschrijft hoe te om een nieuwe taal (bijvoorbeeld, Fins) aan de **markering toe te voegen geeft** dialoog uit:

1. In **CRXDE**, geef het multi-waardebezit `languages` van de knoop `/content/cq:tags` uit.
1. Voeg `fi_fi` toe, die de Finse landinstelling vertegenwoordigt, en sla de wijzigingen op.

Het Fins is nu beschikbaar in de markeringsdialoog van de paginaeigenschappen en in **uitgeeft de dialoog van de Markering** wanneer het uitgeven van een markering in de **Tags** console.

>[!NOTE]
>
>De nieuwe taal moet een van de AEM erkende talen zijn. Dit wil zeggen dat de code beschikbaar moet zijn als een knooppunt onder `/libs/wcm/core/resources/languages` .
