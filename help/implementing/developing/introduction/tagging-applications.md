---
title: Tags samenstellen in AEM toepassingen
description: Programmaticaal werken met tags of tags uitbreiden binnen een aangepaste AEM.
exl-id: a106dce1-5d51-406a-a563-4dea83987343
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 0%

---

# Tags samenstellen in AEM toepassingen {#building-tagging-into-aem-applications}

In dit document wordt beschreven hoe u programmatisch kunt werken met tags of tags wilt uitbreiden binnen een aangepaste AEM.

* [Tags-API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service-javadoc/com/day/cq/tagging/package-summary.html)

die met de

* [Kader voor tags](tagging-framework.md)

Voor gerelateerde informatie over codering:

* Zie [Tags gebruiken](/help/sites-cloud/authoring/features/tags.md) voor informatie over het labelen van inhoud als auteur van inhoud.
* Zie Tags beheren voor een beheerder. Het perspectief van de beheerder op het maken en beheren van tags en op welke inhoudstags zijn toegepast.

## Overzicht van de API voor labelen {#overview-of-the-tagging-api}

Met de implementatie van het [tagging framework](tagging-framework.md) in AEM kunt u tags en code-inhoud beheren met de JCR API. `TagManager` zorgt ervoor dat tags die zijn ingevoerd als waarden in de eigenschap  `cq:tags` string array niet worden gedupliceerd, verwijdert deze tags die verwijzen naar niet-bestaande tags en updates  `TagID`  `TagID`voor verplaatste of samengevoegde tags. `TagManager` gebruikt een JCR-observatielistener die onjuiste wijzigingen retourneert. De hoofdklassen bevinden zich in het [com.day.cq.tagging](https://experienceleague.adobe.com/docs/experience-manager-cloud-service-javadoc/com/day/cq/tagging/package-summary.html) pakket:

* `JcrTagManagerFactory` - retourneert een JCR-gebaseerde implementatie van een  `TagManager`. Dit is de referentie-implementatie van de API voor labelen.
* `TagManager` - Hiermee kunt u tags oplossen en maken op basis van paden en namen.
* `Tag` - definieert het labelobject.

### Een op JCR gebaseerde tagbeheer ophalen {#getting-a-jcr-based-tagmanager}

Om een `TagManager` instantie terug te winnen, moet u JCR `Session` hebben en `getTagManager(Session)` roepen:

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

In de typische het Verkopen context kunt u aan `TagManager` van `ResourceResolver` ook aanpassen:

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### Een tagobject {#retrieving-a-tag-object} ophalen

Een `Tag` kan door `TagManager` worden teruggewonnen, of het oplossen van een bestaande markering of het creëren van nieuwe:

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

Voor de op JCR-Gebaseerde implementatie, die `Tags` op JCR `Nodes` in kaart brengt, kunt u het mechanisme van Sling direct gebruiken `adaptTo` als u het middel (b.v. zoals `/content/cq:tags/default/my/tag`) hebt:

```java
Tag tag = resource.adaptTo(Tag.class);
```

Hoewel een tag alleen *vanuit* een bron (geen knooppunt) mag worden omgezet, kan een tag *worden omgezet in* zowel een knooppunt als een bron:

```java
Node node = tag.adaptTo(Node.class);
Resource node = tag.adaptTo(Resource.class);
```

>[!NOTE]
>
>Directe aanpassing van `Node` aan `Tag` is niet mogelijk, omdat `Node` de methode Sling `Adaptable.adaptTo(Class)` niet implementeert.

### Labels {#getting-and-setting-tags} ophalen en instellen

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
>De geldige `RangeIterator` is:
>
>`com.day.cq.commons.RangeIterator`

### Labels {#deleting-tags} verwijderen

```java
tagManager.deleteTag(tag);
```

### Codes {#replicating-tags} dupliceren

Het is mogelijk om de replicatieservice (`Replicator`) met markeringen te gebruiken omdat de markeringen van type `nt:hierarchyNode` zijn:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## De opschoonfunctie voor tags {#the-tag-garbage-collector}

De opschoonfunctie voor tags is een service op de achtergrond die verborgen en ongebruikte tags opruimt. Verborgen en ongebruikte tags zijn tags onder `/content/cq:tags` die een eigenschap `cq:movedTo` hebben en niet worden gebruikt op een inhoudsknooppunt. Ze hebben een getal van nul. Door dit lazy schrappingsproces te gebruiken, moet de inhoudsknoop (d.w.z. het `cq:tags` bezit) niet als deel van de beweging of de fusieverrichting worden bijgewerkt. De verwijzingen in het `cq:tags` bezit worden automatisch bijgewerkt wanneer `cq:tags` bezit wordt bijgewerkt, bijvoorbeeld door de dialoog van de pagina eigenschappen.

De opschoonfunctie voor tags wordt standaard eenmaal per dag uitgevoerd. Dit kan worden gevormd bij:

`http://<host>:<port>/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector`

## Tag zoeken en taglijst {#tag-search-and-tag-listing}

De zoekopdracht naar tags en het tagoverzicht werkt als volgt:

* De zoekopdracht naar `TagID` zoekt naar de tags waarvan de eigenschap `cq:movedTo` is ingesteld op `TagID` en doorloopt de `cq:movedTo` `TagID`s.
* De zoekopdracht naar tagtitel zoekt alleen de tags zonder de eigenschap `cq:movedTo`.

## Tags in verschillende talen {#tags-in-different-languages}

Een tag `title` kan in verschillende talen worden gedefinieerd. Vervolgens wordt een taalgevoelige eigenschap toegevoegd aan het tagknooppunt. Deze eigenschap heeft de notatie `jcr:title.<locale>`, bijvoorbeeld `jcr:title.fr` voor de Franse vertaling. `<locale>` moet een ISO-tekenreeks voor kleine letters zijn en onderstrepingsteken (`_`) gebruiken in plaats van een koppelteken/streepje (`-`), bijvoorbeeld:  `de_ch`.

Wanneer bijvoorbeeld de tag **Animals** wordt toegevoegd aan de pagina **Products**, wordt de waarde `stockphotography:animals` toegevoegd aan de eigenschap `cq:tags` van het knooppunt `/content/wknd/en/products/jcr:content`. Er wordt naar de vertaling verwezen vanuit het tagknooppunt.

De server-side API heeft gelokaliseerde `title` verwante methodes:

* [`com.day.cq.tagging.Tag`](https://experienceleague.adobe.com/docs/experience-manager-cloud-service-javadoc/com/day/cq/tagging/Tag.html)
   * `getLocalizedTitle(Locale locale)`
   * `getLocalizedTitlePaths()`
   * `getLocalizedTitles()`
   * `getTitle(Locale locale)`
   * `getTitlePath(Locale locale)`
* [`com.day.cq.tagging.TagManager`](https://experienceleague.adobe.com/docs/experience-manager-cloud-service-javadoc/com/day/cq/tagging/TagManager.html)
   * `canCreateTagByTitle(String tagTitlePath, Locale locale)`
   * `createTagByTitle(String tagTitlePath, Locale locale)`
   * `resolveByTitle(String tagTitlePath, Locale locale)`

In AEM kan de taal worden opgehaald uit de paginataal of uit de taal van de gebruiker.

Bij het labelen hangt de lokalisatie af van de context, aangezien tag `titles` kan worden weergegeven in de paginataal, in de gebruikerstaal of in een andere taal.

### Een nieuwe taal toevoegen aan het dialoogvenster Tag bewerken {#adding-a-new-language-to-the-edit-tag-dialog}

In de volgende procedure wordt beschreven hoe u een nieuwe taal (bijvoorbeeld Fins) kunt toevoegen aan het dialoogvenster **Tag Edit**:

1. Bewerk in **CRXDE** de eigenschap multi-value `languages` van het knooppunt `/content/cq:tags`.
1. Voeg `fi_fi` toe, die de Finse landinstelling vertegenwoordigt, en sla de wijzigingen op.

Het Fins is nu beschikbaar in het tagdialoogvenster van de pagina-eigenschappen en in het dialoogvenster **Tag bewerken** wanneer u een tag bewerkt in de **Tags toevoegen**-console.

>[!NOTE]
>
>De nieuwe taal moet een van de AEM erkende talen zijn, d.w.z. het moet beschikbaar zijn als een knooppunt onder `/libs/wcm/core/resources/languages`.
