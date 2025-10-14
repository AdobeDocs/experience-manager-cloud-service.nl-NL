---
title: Sling Adapters gebruiken
description: Sling biedt een adapterpatroon om objecten die de Aanpasbare interface implementeren, gemakkelijk te vertalen
exl-id: 8ffe3bbd-01fe-44c2-bf60-7a4d25a6ba2b
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 0%

---

# Sling Adapters gebruiken {#using-sling-adapters}

[&#x200B; het Verschuiven &#x200B;](https://sling.apache.org) biedt een [&#x200B; patroon van de Adapter &#x200B;](https://sling.apache.org/documentation/the-sling-engine/adapters.html) aan om voorwerpen gemakkelijk te vertalen die de [&#x200B; Aanpasbare &#x200B;](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) interface uitvoeren. Deze interface verstrekt een generische [&#x200B; adjustTo () &#x200B;](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) methode die het voorwerp aan het klassentype vertaalt dat als argument wordt overgegaan.

Als u bijvoorbeeld een Resource-object naar het corresponderende Node-object wilt vertalen, kunt u gewoon het volgende doen:

```java
Node node = resource.adaptTo(Node.class);
```

## Gevallen gebruiken {#use-cases}

Er zijn de volgende gebruiksgevallen:

* Hiermee krijgt u implementatiespecifieke objecten.

  Bijvoorbeeld, verleent een op JCR-Gebaseerde implementatie van de generische [`Resource` &#x200B;](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) interface toegang tot onderliggende JCR [`Node` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html).

* Het maken van sneltoetsen voor objecten waarvoor interne contextobjecten moeten worden doorgegeven.

  Bijvoorbeeld, op JCR-Gebaseerd [`ResourceResolver` &#x200B;](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) houdt een verwijzing naar verzoek [`JCR Session` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html), die beurtelings voor vele voorwerpen nodig is die op die verzoekzitting, zoals [`PageManager` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageManager.html) of [`UserManager` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/security/UserManager.html) werken.

* Snelkoppeling naar services.

  Een zeldzaam geval - `sling.getService()` is ook eenvoudig.

### Null-retourwaarde {#null-return-value}

`adaptTo()` Kan null retourneren.

Er zijn diverse redenen voor de ongeldige terugkeer, met inbegrip van het volgende:

* de implementatie ondersteunt het doeltype niet
* een adapterfabriek die deze kwestie behandelt is niet actief (bijvoorbeeld wegens ontbrekende de dienstverwijzingen)
* interne voorwaarde is mislukt
* service is niet beschikbaar

Het is belangrijk dat u de null-case netjes afhandelt. Voor JPEG-renderingen kan het acceptabel zijn dat de JPEG-opname mislukt als deze resulteert in een leeg stuk inhoud.

### Caching {#caching}

Om de prestaties te verbeteren, kunnen implementaties het object dat door een `obj.adaptTo()` -aanroep is geretourneerd, in de cache plaatsen. Wanneer `obj` hetzelfde is, is het geretourneerde object hetzelfde.

Deze caching wordt uitgevoerd voor alle `AdapterFactory` gebaseerde gevallen.

Er is echter geen algemene regel: het object kan een nieuw of een bestaand object zijn. Als zodanig betekent dit dat u niet op één van beide gedrag kunt vertrouwen. Daarom is het belangrijk, vooral binnen `AdapterFactory`, dat objecten in dit scenario opnieuw kunnen worden gebruikt.

### Hoe werkt het {#how-it-works}

U kunt `Adaptable.adaptTo()` op verschillende manieren implementeren:

* Door het object zelf; de methode zelf implementeren en aan bepaalde objecten toewijzen.
* Door een [`AdapterFactory` &#x200B;](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html), die willekeurige voorwerpen in kaart kan brengen.

  De objecten moeten nog steeds de `Adaptable` interface implementeren en moeten [`SlingAdaptable` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/adapter/SlingAdaptable.html) uitbreiden (die de `adaptTo` aanroep aan een centrale adaptermanager doorgeeft).

  Met deze methode kunt u haken toevoegen aan het mechanisme `adaptTo` voor bestaande klassen, zoals `Resource` .

* Een combinatie van beide.

In het eerste geval kunnen de Java™-documenten aangeven wat `adaptTo-targets` mogelijk is. Voor specifieke subklassen zoals de op JCR gebaseerde Resource is deze instructie echter vaak niet mogelijk. In het laatste geval maken implementaties van `AdapterFactory` doorgaans deel uit van de klassen van het type private van een bundel en worden deze dus niet weergegeven in een client-API, en worden ze niet vermeld in Java™-documenten. Theoretisch, is het mogelijk om tot alle `AdapterFactory` implementaties van [&#x200B; OSGi &#x200B;](/help/implementing/deploying/configuring-osgi.md) de dienstruntime toegang te hebben en hun &quot;adaptables&quot;(bronnen en doelstellingen) configuraties te bekijken, maar niet om hen aan elkaar in kaart te brengen. Uiteindelijk hangt het af van de interne logica, die moet worden gedocumenteerd. Vandaar deze verwijzing.

## Referentie {#reference}

### Sling {#sling}

[**Middel** &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) past aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Als het een op JCR-knooppunten gebaseerde bron of een JCR-eigenschap is, verwijzen naar een knooppunt</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">Eigenschap</a></td>
   <td>Als het een op JCR-eigenschap gebaseerde resource is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">Item</a></td>
   <td>Als het een op JCR gebaseerde bron (knooppunt of eigenschap) is</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Map.html">Kaart</a></td>
   <td>Keert een kaart van de eigenschappen terug, als het een JCR-knoop-gebaseerd middel (of andere middel ondersteunend waardekaarten) is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td>
   <td>Keert een geschikt-aan-gebruiks kaart van de eigenschappen terug, als het een JCR-knoop-gebaseerd middel (of andere middel ondersteunend waardekaarten) is. Kan ook (eenvoudigere) worden bereikt door <br /> <code><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ResourceUtil.html">ResourceUtil.getValueMap(Resource)</a></code> (handelt null case af, enzovoort) te gebruiken</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td>
   <td>Uitbreiding van <a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ValueMap.html"> ValueMap </a> die de hiërarchie van middelen toestaat om worden rekenschap gegeven wanneer het zoeken van eigenschappen</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ModifiableValueMap.html">ModisibleValueMap</a></td>
   <td>Een uitbreiding van <a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ValueMap.html"> ValueMap </a>, die u eigenschappen op die knoop laat wijzigen</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td>
   <td>Retourneert de binaire inhoud van een bestandsbron (als het een JCR-knooppuntgebaseerde bron is en het knooppunttype <code>nt:file</code> of <code>nt:resource</code> is; als het een bundelbron is; bestandsinhoud, als het een bestandssysteembron is). Of retourneert de gegevens van een binaire JCR-eigenschapbron.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/net/URL.html">URL</a></td>
   <td>Hiermee wordt een URL naar de bron geretourneerd (de URL van de opslagplaats van dit knooppunt als het een JCR-knooppuntbron is; de URL van de jar-bundel als het een bundelbron is; de bestands-URL als het een bestandssysteembron is)</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/io/File.html">Bestand</a></td>
   <td>Als het een bestandssysteembron is</td>
  </tr>
  <tr>
   <td><a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/api/scripting/SlingScript.html">SlingScript</a></td>
   <td>Als de bron een script (bijvoorbeeld jsp-bestand) is waarvoor een scriptengine is geregistreerd met sling</td>
  </tr>
  <tr>
   <td><a href="https://www.oracle.com/java/technologies/servlet-technology.html">Servlet</a></td>
   <td>Als het middel een manuscript (bijvoorbeeld, jsp- dossier) is waarvoor een manuscriptmotor met het verbinden wordt geregistreerd, of als het een servletmiddel is</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/String.html"> Koord </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Boolean.html"> Van Boole </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Long.html"> Lang </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Double.html"> tweemaal </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Calendar.html"> Kalender </a><br /> <a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Value.html"> Waarde </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/String.html"> Koord [] </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Boolean.html"> Van Boole [] </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Long.html"> Lang [] </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Calendar.html"> Kalender [] </a><br /> 9&rbrace; <a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Value.html"> Waarde [] </a></td>
   <td>Retourneert de waarden als het een JCR-eigenschap-gebaseerde resource (en de value-standaard) is.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Als het een op JCR-knooppunten gebaseerde bron is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Page.html">Pagina</a></td>
   <td>Als het een op JCR-knooppunten gebaseerde bron is en het knooppunt een <code>cq:Page</code> (of <code>cq:PseudoPage</code> ) is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/components/Component.html">Component</a></td>
   <td>Als het een knooppuntbron <code>cq:Component</code> is</td>
  </tr>  
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/designer/Design.html">Ontwerp</a></td>
   <td>Als het een ontwerpknoop (<code>cq:Page</code>) is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Template.html">Sjabloon</a></td>
   <td>Als het een knooppuntbron <code>cq:Template</code> is</td>
  </tr>  
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/msm/api/Blueprint.html">Blauwdruk</a></td>
   <td>Als het een knooppuntbron <code>cq:Template</code> is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/dam/api/Asset.html">Element</a></td>
   <td>Als het een dam is:Middelen van de knoop van activa</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/dam/api/Rendition.html">Vertoning</a></td>
   <td>Als het een dam:de uitvoering van activa (nt:dossier onder de vertoningsomslag van een dam:Assert) is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/Tag.html">Tag</a></td>
   <td>Als het een knooppuntbron <code>cq:Tag</code> is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td>
   <td>Gebaseerd op de zitting JCR als het een op JCR-Gebaseerde middel is en de gebruiker toestemmingen heeft om tot UserManager toegang te hebben</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Toestemming</a></td>
   <td>Autorisable is de gemeenschappelijke basisinterface voor Gebruiker en Groep</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/User.html">Gebruiker</a></td>
   <td>De gebruiker is een speciale Vergunning die voor authentiek kan worden verklaard en kan worden nagedacht</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/SimpleSearch.html">SimpleSearch</a></td>
   <td>Zoekt onder de bron (of gebruik setSearchIn()) als het een JCR-gebaseerde resource is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/workflow/status/WorkflowStatus.html">WorkflowStatus</a></td>
   <td>Workflowstatus voor de opgegeven pagina/workflow-payload node</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/ReplicationStatus.html">ReplicationStatus</a></td>
   <td>Replicatiestatus voor de opgegeven resource of het JCR:content-subknooppunt (eerst gecontroleerd)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/connector/ConnectorResource.html">ConnectorResource</a></td>
   <td>Retourneert een aangepaste connectorbron voor bepaalde typen als het een JCR-node-gebaseerde resource is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/contentsync/config/package-summary.html">Config</a></td>
   <td>Als het een knooppuntbron <code>cq:ContentSyncConfig</code> is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/contentsync/config/package-summary.html">ConfigEntry</a></td>
   <td>Als deze zich onder een node <code>cq:ContentSyncConfig</code> -resource bevindt</td>
  </tr>
 </tbody>
</table>

[**ResourceResolver** &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/ResourceResolver.html) past aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">Sessie</a></td>
   <td>De JCR-sessie van het verzoek, als dit een op JCR gebaseerde resourceoplosser is (standaardwaarde)</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td>
   <td>Gebaseerd op de zitting JCR, als het een op JCR-Gebaseerde middeloplosser is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td>
   <td>Gebaseerd op de zitting JCR, als het een op JCR-Gebaseerde middeloplosser is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/UserManager.html">UserManager</a></td>
   <td>De UserManager verleent toegang tot en middelen om toegelaten voorwerpen, namelijk gebruikers en groepen te handhaven. De UserManager is gebonden aan een bepaalde Zitting
   </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html"> Toegelaten </a> </td>
   <td>De huidige gebruiker</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/jackrabbit/api/security/user/User.html"> Gebruiker </a><br /> </td>
   <td>De huidige gebruiker</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/Externalizer.html">ExternalAlizer</a></td>
   <td>Voor het externaliseren van absolute URLs, zelfs zonder het verzoekvoorwerp <br /> </td>
  </tr>
 </tbody>
</table>

[**SlingHttpServletRequest** &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) past aan:

Geen doelstellingen nog, maar voert Aangepast uit en kon als bron in een douane AdapterFactory worden gebruikt.

[**SlingHttpServletResponse** &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) past aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/org/xml/sax/ContentHandler.html"> ContentHandler </a><br /> (XML)</td>
   <td>Als het een slingerrewriter-reactie is</td>
  </tr>
 </tbody>
</table>

#### WCM {#wcm}

**[Pagina &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Page.html)** past aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html"> Middel </a><br /> </td>
   <td>Bron van de pagina.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Gelabelde bron (== dit).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Knooppunt van de pagina.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alles waaraan de bron van de pagina kan worden aangepast.</td>
  </tr>
 </tbody>
</table>

**[Component &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/components/Component.html)** past aan:

| [&#x200B; Middel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) | Bron van de component. |
|---|---|
| [&#x200B; LabeledResource &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html) | Gelabelde bron (== dit). |
| [&#x200B; Knoop &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knooppunt van de component. |
| ... | Alles waaraan de bron van de component kan worden aangepast. |

**[Malplaatje &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/Template.html)** past aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html"> Middel </a> <a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td>
   <td>Bron van de sjabloon.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Gelabelde bron (== dit).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Knooppunt van deze sjabloon.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alles waaraan de bron van de sjabloon kan worden aangepast.</td>
  </tr>
 </tbody>
</table>

#### Beveiliging {#security}

**Toegelaten**, **Gebruiker**, en **Groep** past aan:

| [&#x200B; Knoop &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Retourneert het thuisknooppunt van de gebruiker/groep. |
|---|---|
| [&#x200B; ReplicationStatus &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/ReplicationStatus.html) | Retourneert de replicatiestatus voor het thuisknooppunt van de gebruiker/groep. |

#### DAM {#dam}

**Activa** past aan:

| [&#x200B; Middel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) | Middelen van het actief. |
|---|---|
| [&#x200B; Knoop &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Node of the asset. |
| ... | Alles waaraan de middelen van het actief kunnen worden aangepast. |

#### Tags {#tagging}

**markering** past aan:

| [&#x200B; Middel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) | Bron van de tag. |
|---|---|
| [&#x200B; Knoop &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knooppunt van de tag. |
| ... | Alles waaraan de bron van de tag kan worden aangepast. |

#### Overige {#other}

Voorts verstrekt het Verdelen / JCR / OCM ook [`AdapterFactory` &#x200B;](https://sling.apache.org/documentation/the-sling-engine/adapters.html) voor douaneOCM ([&#x200B; de Inhoud van de Toewijzing van Objecten &#x200B;](https://jackrabbit.apache.org/jcr/object-content-mapping.html)) voorwerpen.
