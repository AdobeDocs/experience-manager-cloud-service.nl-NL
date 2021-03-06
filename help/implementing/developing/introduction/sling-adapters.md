---
title: Sling Adapters
description: Sling biedt een adapterpatroon om objecten die de Aanpasbare interface implementeren, gemakkelijk te vertalen
exl-id: 8ffe3bbd-01fe-44c2-bf60-7a4d25a6ba2b
source-git-commit: c08e442e58a4ff36e89a213aa7b297b538ae3bab
workflow-type: tm+mt
source-wordcount: '2219'
ht-degree: 0%

---

# Sling Adapters {#using-sling-adapters}

[Sling](https://sling.apache.org) biedt een [Adapterpatroon](https://sling.apache.org/site/adapters.html) om objecten die het [Aanpasbaar](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) interface. Deze interface verstrekt een generiek [adjustTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) methode die het object omzet in het klassentype dat als argument wordt doorgegeven.

Bijvoorbeeld om een voorwerp van het Middel aan het overeenkomstige voorwerp van de Knoop te vertalen, kunt u eenvoudig doen:

```java
Node node = resource.adaptTo(Node.class);
```

## Gevallen gebruiken {#use-cases}

Er zijn de volgende gebruiksgevallen:

* Hiermee krijgt u implementatiespecifieke objecten.

   Bijvoorbeeld een op JCR gebaseerde implementatie van het generieke [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) interface biedt toegang tot het onderliggende JCR [`Node`](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html).

* Het maken van sneltoetsen voor objecten waarvoor interne contextobjecten moeten worden doorgegeven.

   Bijvoorbeeld op basis van de JCR [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) bevat een verwijzing naar de [`JCR Session`](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html), die op zijn beurt nodig is voor veel objecten die op die aanvraagsessie zullen werken, zoals de [`PageManager`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageManager.html) of [`UserManager`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/security/UserManager.html).

* Snelkoppeling naar services.

   Een zeldzame zaak - `sling.getService()` is ook eenvoudig.

### Null-retourwaarde {#null-return-value}

`adaptTo()` kan null retourneren.

Hiervoor zijn verschillende redenen, waaronder:

* de implementatie ondersteunt het doeltype niet
* een adapterfabriek die deze zaak afhandelt, is niet actief (bijv. vanwege ontbrekende serviceverwijzingen)
* interne voorwaarde is mislukt
* service is niet beschikbaar

Het is belangrijk dat u de null-case netjes afhandelt. Voor jsp-renderingen kan het acceptabel zijn dat de jsp mislukt als dat resulteert in een leeg stuk inhoud.

### Caching {#caching}

Om de prestaties te verbeteren, kunnen implementaties het object dat door een `obj.adaptTo()` vraag. Als de `obj` gelijk is, is het geretourneerde object hetzelfde.

Deze caching wordt uitgevoerd voor alle `AdapterFactory` gegronde gevallen.

Er is echter geen algemene regel: het object kan een nieuw of een bestaand object zijn. Dit betekent dat u niet op ????n van beide gedrag kunt vertrouwen. Daarom is het belangrijk, vooral binnen `AdapterFactory`, dat de objecten in dit scenario opnieuw kunnen worden gebruikt.

### Hoe werkt het {#how-it-works}

Er zijn verschillende manieren om `Adaptable.adaptTo()` kan worden uitgevoerd:

* door het object zelf; het implementeren van de methode zelf en het toewijzen aan bepaalde objecten.
* Met een [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html), die willekeurige objecten kunnen toewijzen.

   De objecten moeten de `Adaptable` interface en moet worden uitgebreid [`SlingAdaptable`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (die de `adaptTo` aanroep aan een centrale adaptermanager).

   Hierdoor kunnen haken in de `adaptTo` mechanisme voor bestaande klassen, zoals `Resource`.

* Een combinatie van beide.

In het eerste geval kunnen de javadocs aangeven wat `adaptTo-targets` zijn mogelijk. Voor specifieke subklassen zoals de op JCR gebaseerde Resource is dit echter vaak niet mogelijk. In het laatste geval worden `AdapterFactory` ze maken doorgaans deel uit van de klassen van het type private van een bundel en worden dus niet weergegeven in een client-API, en worden ook niet vermeld in javadocs. Theoretisch gezien zou het mogelijk zijn om alle `AdapterFactory` implementaties van de [OSGi](/help/implementing/deploying/configuring-osgi.md) de dienstruntime en kijken naar hun &quot;aanpasbare&quot;configuraties (bronnen en doelstellingen), maar niet om hen aan elkaar in kaart te brengen. Uiteindelijk hangt dit af van de interne logica, die moet worden gedocumenteerd. Vandaar deze verwijzing.

## Referentie {#reference}

### Sling {#sling}

[**Resource**](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) aanpassen aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Als dit een JCR-node-based resource is of een JCR-eigenschap die verwijst naar een knooppunt.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">Eigenschap</a></td>
   <td>Als dit een op JCR-eigenschap gebaseerde bron is.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">Item</a></td>
   <td>Als dit een op JCR gebaseerde bron (knooppunt of eigenschap) is.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api//java/util/Map.html">Kaart</a></td>
   <td>Keert een kaart van de eigenschappen terug, als dit een JCR-knoop-gebaseerd middel (of andere middel ondersteunend waardekaarten) is.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td>
   <td>Retourneert een handig te gebruiken kaart van de eigenschappen, als dit een JCR-node-based resource (of andere resource die waardekaarten ondersteunt) is. Kan ook (eenvoudiger) worden bereikt door<br /> <code><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code> (handelt null case enz. af).</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td>
   <td>Verlenging van <a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a> waarmee bij het zoeken naar eigenschappen rekening kan worden gehouden met de hi??rarchie van bronnen.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ModifiableValueMap.html">ModisibleValueMap</a></td>
   <td>Een uitbreiding van de <a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>, waarmee u eigenschappen op dat knooppunt kunt wijzigen.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td>
   <td>Retourneert de binaire inhoud van een bestandsbron (als dit een JCR-node-gebaseerde resource is en het knooppunttype is <code>nt:file</code> of <code>nt:resource</code>; als dit een bundelbron is; bestandsinhoud als dit een bestandssysteembron is) of de gegevens van een binaire JCR-eigenschapbron.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/net/URL.html">URL</a></td>
   <td>Retourneert een URL naar de bron (de URL van de gegevensopslagruimte van dit knooppunt als dit een op JCR-knooppunten gebaseerde bron is; jar bundle URL if this is a bundle resource; bestand-URL als dit een bestandssysteembron is).</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/File.html">Bestand</a></td>
   <td>Als dit een bestandssysteembron is.</td>
  </tr>
  <tr>
   <td><a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/api/scripting/SlingScript.html">SlingScript</a></td>
   <td>Als deze bron een script (bijvoorbeeld jsp-bestand) is waarvoor een scriptengine is geregistreerd met sling.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/products/servlet/2.2/javadoc/javax/servlet/Servlet.html">Servlet</a></td>
   <td>Als deze bron een script (bijvoorbeeld jsp-bestand) is waarvoor een scriptengine is geregistreerd met sling of als dit een servlet-resource is.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html">String</a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Boolean.html">Boolean</a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Long.html">Lang</a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Double.html">Dubbel</a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/util/Calendar.html">Kalender</a><br /> <a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Value.html">Waarde</a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html">String[]</a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Boolean.html">Boolean[]</a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Long.html">Lang[]</a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/util/Calendar.html">Kalender[]</a><br /> <a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Value.html">Waarde[]</a></td>
   <td>Retourneert de waarde(n) als dit een JCR-eigenschap-gebaseerde resource is (en de value-fit).</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Als dit een op JCR-knooppunten gebaseerde bron is.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Page.html">Pagina</a></td>
   <td>Als dit een JCR-node-gebaseerde resource is en het knooppunt een <code>cq:Page</code> (of <code>cq:PseudoPage</code>).</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/components/Component.html">Component</a></td>
   <td>Als dit een <code>cq:Component</code> knooppuntbron.</td>
  </tr>  
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/designer/Design.html">Ontwerp</a></td>
   <td>Als dit een ontwerpknooppunt is (<code>cq:Page</code>).</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Template.html">Sjabloonmodel</a></td>
   <td>Als dit een <code>cq:Template</code> knooppuntbron.</td>
  </tr>  
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/msm/api/Blueprint.html">Blauwdruk</a></td>
   <td>Als dit een <code>cq:Template</code> knooppuntbron.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/dam/api/Asset.html">Element</a></td>
   <td>Als dit een dam:Middelen van de knoop van Activa is.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/dam/api/Rendition.html">Vertoning</a></td>
   <td>Als dit een dam is:Vertoning van activa (nt:dossier onder de vertoningsomslag van een dam:Assert)</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/Tag.html">Tag</a></td>
   <td>Als dit een <code>cq:Tag</code> knooppuntbron.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td>
   <td>Gebaseerd op de zitting JCR als dit een op JCR-Gebaseerde middel is en de gebruiker toestemmingen heeft om tot UserManager toegang te hebben.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Toestemming</a></td>
   <td>Autorisable is de gemeenschappelijke basisinterface voor Gebruiker en Groep.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/User.html">Gebruiker</a></td>
   <td>De gebruiker is een speciale Authorizable die voor authentiek en kan worden verklaard.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/SimpleSearch.html">SimpleSearch</a></td>
   <td>Zoekt onder de bron (of gebruik setSearchIn()) als dit een op JCR gebaseerde bron is.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/workflow/status/WorkflowStatus.html">WorkflowStatus</a></td>
   <td>Workflowstatus voor het opgegeven payload-knooppunt voor de pagina/workflow.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/ReplicationStatus.html">ReplicationStatus</a></td>
   <td>Replicatiestatus voor de opgegeven resource of het JCR:content-subknooppunt (eerst ingeschakeld).</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/connector/ConnectorResource.html">ConnectorResource</a></td>
   <td>Retourneert een aangepaste connectorbron voor bepaalde typen als dit een op JCR-knooppunten gebaseerde bron is.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/contentsync/config/package-summary.html">Config</a></td>
   <td>Als dit een <code>cq:ContentSyncConfig</code> knooppuntbron.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/contentsync/config/package-summary.html">ConfigEntry</a></td>
   <td>Als dit onder een a <code>cq:ContentSyncConfig</code> knooppuntbron.</td>
  </tr>
 </tbody>
</table>

[**ResourceResolver**](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ResourceResolver.html) aanpassen aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">Sessie</a></td>
   <td>De JCR-sessie van het verzoek, als dit een op JCR gebaseerde resourceoplosser is (standaardwaarde).</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td>
   <td>??</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td>
   <td>??</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td>
   <td>??</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td>
   <td>Gebaseerd op de zitting JCR, als dit op JCR-Gebaseerde middeloplosser is.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td>
   <td>Gebaseerd op de zitting JCR, als dit op JCR-Gebaseerde middeloplosser is.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/UserManager.html">UserManager</a></td>
   <td>De UserManager biedt toegang tot en middelen om machtigbare objecten, d.w.z. gebruikers en groepen, te onderhouden. De UserManager is gebonden aan een bepaalde Zitting.
   </td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Toestemming</a> </td>
   <td>De huidige gebruiker.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/User.html">Gebruiker</a><br /> </td>
   <td>De huidige gebruiker.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/Externalizer.html">ExternalAlizer</a></td>
   <td>Voor het extern maken van absolute URL's, zelfs met het aanvraagobject.<br /> </td>
  </tr>
 </tbody>
</table>

[**SlingHttpServletRequest**](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) aanpassen aan:

Geen doelstellingen nog, maar voert Aangepast uit en kon als bron in een douane AdapterFactory worden gebruikt.

[**SlingHttpServletResponse**](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) aanpassen aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td>
   <td>Als dit een sling rewriter reactie is.</td>
  </tr>
 </tbody>
</table>

#### WCM {#wcm}

**[Pagina](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Page.html)** aanpassen aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><br /> </td>
   <td>Bron van de pagina.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Gelabelde bron (== dit).</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Knooppunt van de pagina.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alles waaraan de bron van de pagina kan worden aangepast.</td>
  </tr>
 </tbody>
</table>

**[Component](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/components/Component.html)** aanpassen aan:

| [Resource](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) | Bron van de component. |
|---|---|
| [LabeledResource](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html) | Gelabelde bron (== dit). |
| [Knooppunt](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knooppunt van de component. |
| ... | Alles waaraan de bron van de component kan worden aangepast. |

**[Sjabloon](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Template.html)** aanpassen aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td>
   <td>Bron van de sjabloon.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Gelabelde bron (== dit).</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Knooppunt van deze sjabloon.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alles waaraan de bron van de sjabloon kan worden aangepast.</td>
  </tr>
 </tbody>
</table>

#### Beveiliging {#security}

**Toestemming**, **Gebruiker** en **Groep** aanpassen aan:

| [Knooppunt](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Retourneert het thuisknooppunt van de gebruiker/groep. |
|---|---|
| [ReplicationStatus](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/ReplicationStatus.html) | Retourneert de replicatiestatus voor het thuisknooppunt van de gebruiker/groep. |

#### DAM {#dam}

**Element** aanpassen aan:

| [Resource](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) | Middelen van het actief. |
|---|---|
| [Knooppunt](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Node of the asset. |
| ... | Alles waaraan de middelen van het actief kunnen worden aangepast. |

#### Tags {#tagging}

**Tag** aanpassen aan:

| [Resource](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) | Bron van de tag. |
|---|---|
| [Knooppunt](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knooppunt van de tag. |
| ... | Alles waaraan de bron van de tag kan worden aangepast. |

#### Overig {#other}

Daarnaast biedt Sling / JCR / OCM ook een [`AdapterFactory`](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory) voor aangepaste OCM ([Objectinhoud toewijzen](https://jackrabbit.apache.org/object-content-mapping.html)).
