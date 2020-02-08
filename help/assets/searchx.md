---
title: Zoekopties en functies in Adobe Experience Manager-middelen uitbreiden
description: Breid de zoekmogelijkheden van Middelen uit.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Zoeken naar elementen uitbreiden {#extend-assets-search}

U kunt de zoekmogelijkheden van Adobe Experience Manager (AEM)-middelen uitbreiden. AEM Assets zoekt in het tekstvak naar elementen op tekenreeksen.

Het zoeken wordt gedaan via de interface QueryBuilder zodat kan het onderzoek met verscheidene predikaten worden aangepast. U kunt de standaardset voorspelden in de volgende map bedekken: `/apps/dam/content/search/searchpanel/facets`.

U kunt ook extra tabbladen toevoegen aan het beheerpaneel van AEM-middelen.

## Bedekking {#overlay}

Om preconfigured preconfigured te bedekken, kopieer de `facets` knoop van `/libs/dam/content/search/searchpanel` aan `/apps/dam/content/search/searchpanel/` of specificeer een ander `facetURL` bezit in de configuratie van het onderzoekspaneel (het gebrek is aan `/libs/dam/content/search/searchpanel/facets.overlay.infinity.json`).

>[!NOTE]
>
>Standaard bestaat de onderliggende mapstructuur `/apps` niet en moet deze worden gemaakt. Zorg ervoor dat de knooptypes die onder aanpassen `/libs`.

### Tabs toevoegen {#add-tabs}

U kunt extra tabbladen voor zoeken toevoegen door deze te configureren in AEM Assets Admin. Extra tabbladen maken:

1. Maak de mappenstructuur `/apps/wcm/core/content/damadmin/tabs,`als deze nog niet bestaat en kopieer het `tabs` knooppunt van `/libs/wcm/core/content/damadmin` en plak het.
1. Maak en configureer het tweede tabblad naar wens.

   >[!NOTE]
   >
   >Wanneer u een tweede bestand maakt, moet u een `siteadminsearchpanel``id` eigenschap instellen om formulierconflicten te voorkomen.

### Aangepaste voorspelling maken {#create-custom-predicates}

AEM Assets wordt geleverd met een set vooraf gedefinieerde voorspellingen die kunnen worden gebruikt om een pagina voor het delen van bedrijfsmiddelen aan te passen.
<!-- In addition to using pre-existing predicates, AEM developers can also create their own predicates using the [Query Builder API](/help/sites-developing/querybuilder-api.md). -->

Voor het maken van aangepaste predikaten is basiskennis van het [Widget-framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html)vereist.

De beste praktijken moeten een bestaand predikaat kopiëren en het aanpassen. Voorspelregels voor voorbeelden bevinden zich in **/libs/cq/search/components/predicates**.

#### Voorbeeld: Een eenvoudige voorspelling van eigenschappen maken {#example-build-a-simple-property-predicate}

Een voorspelling van eigenschappen maken:

1. Maak een componentmap in de projectmap, bijvoorbeeld **/apps/geometrixx/components/titlepreate**.
1. Add **content.xml**:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Title Predicate"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Toevoegen `titlepredicate.jsp`.

   ```xml
   <%--
   
     Sample title predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Title</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:title";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // createId adds a counter to the predicate name - useful in case this predicate
           // is inserted multiple times on the same page.
           var id = qb.createId(predicateName);
   
           // Hidden field that defines the property to search for; in our case this
           // is the "dc:title" metadata. The name "property" (or "1_property", "2_property" etc.)
           // indicates the server to use the property predicate
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id,
               "value": propertyName
           });
   
           // The visible text field. The name has to be like the one of the hidden field above
           // plus the ".value" suffix.
           qb.addField({
               "xtype": "textfield",
               "renderTo": elemId,
               "name": id + ".value"
           });
   
           // Depending on the predicate additional parameters allow to configure the
           // predicate. Here we add an operation parameter to create a "like" query.
           // Again note the name set to the id and a suffix.
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id + ".operation",
               "value": "like"
           });
       });
   </script>
   ```

1. Als u de component beschikbaar wilt maken, moet u deze kunnen bewerken. Als u een component bewerkbaar wilt maken in CRXDE, voegt u een knooppunt **cq:editConfig** van het primaire type **cq:EditConfig** toe. U kunt alinea&#39;s verwijderen door een eigenschap met meerdere waarden **cq:handelingen** met één waarde van **DELETE** toe te voegen.
1. Navigeer naar de browser en schakel op de voorbeeldpagina (bijvoorbeeld **press.html**) de ontwerpmodus in en schakel de nieuwe component in voor het alineasysteem &#39;prediken&#39; (bijvoorbeeld **links**).

1. In de modus **Bewerken** is de nieuwe component nu beschikbaar in de assistent (in de groep **Zoeken** ). Voeg de component in de kolom **Voorspelden** in en typ een zoekwoord, bijvoorbeeld **Ruitje** , en klik op het vergrootglas om de zoekopdracht te starten.

   >[!NOTE]
   >
   >Zorg er bij het zoeken voor dat u de term exact typt, inclusief het juiste hoofdlettergebruik.

#### Voorbeeld: Een eenvoudige groepspreiding maken {#example-build-a-simple-group-predicate}

Om een groep te bouwen predikaat:

1. Maak een componentmap in de projectmap, bijvoorbeeld **/apps/geometrixx/components/picspredicate.**
1. Add **content.xml**:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Formats"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Voeg **titlePredicate.jsp** toe:

   ```xml
   <%--
   
     Sample group predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page.
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Image Formats</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:format";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // Create a unique group ID; will return e.g. "1_group".
           var groupId = qb.createGroupId();
   
           // Hidden field that defines the property to search for  - in our case "dc:format" -
           // and declares the group of predicates. "property" in the name ("1_group.property")
           // indicates to the server to use the "property predicate"
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": "<%= elemId %>",
               "name": groupId + "." + predicateName, // 1_group.property
               "value": propertyName
           });
   
           // Declare to combine the multiple values using OR.
           qb.add(new CQ.Ext.form.Hidden({
               "name": groupId + ".p.or",  // 1_group.p.or
               "value": "true"
           }));
   
           // The options
           var options = [
               { "label":"JPEG", "value":"image/jpeg"},
               { "label":"PNG",  "value":"image/png" },
               { "label":"GIF",  "value":"image/gif" }
           ];
   
           // Build a checkbox for each option.
           for (var i = 0; i < options.length; i++) {
               qb.addField({
                   "xtype": "checkbox",
                   "renderTo": "<%= elemId %>",
                   // 1_group.property.0_value, 1_group.property.1_value etc.
                   "name": groupId + "." +  predicateName + "." + i + "_value",
                   "inputValue": options[i].value,
                   "boxLabel": options[i].label,
                   "listeners": {
                       "check": function() {
                           // Submit the search form when checking/unchecking a checkbox.
                           qb.submit();
                       }
                   }
               });
           }
       });
   ```

1. Als u de component beschikbaar wilt maken, moet u deze kunnen bewerken. Als u een component bewerkbaar wilt maken in CRXDE, voegt u een knooppunt **cq:editConfig** van het primaire type **cq:EditConfig** toe. U kunt alinea&#39;s verwijderen door een eigenschap met meerdere waarden **cq:handelingen** met één waarde van **DELETE** toe te voegen.
1. Navigeer naar de browser en schakel op de voorbeeldpagina (bijvoorbeeld **press.html**) de ontwerpmodus in en schakel de nieuwe component in voor het alineasysteem &#39;prediken&#39; (bijvoorbeeld **links**).
1. In de modus **Bewerken** is de nieuwe component nu beschikbaar in de assistent (in de groep **Zoeken** ). Voeg de component in de kolom **Voorspelden** in.

### Vooraf geïnstalleerde widgets {#installed-predicate-widgets}

De volgende voorspelling is beschikbaar als vooraf geconfigureerde ExtJS-widgets.

#### FulltextPredicate {#fulltextpredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap<br /> </strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>predikaatName</td>
   <td>Tekenreeks</td>
   <td>Naam van de voorspelling. Heeft als standaardwaarde 'fulltext'</td>
  </tr>
  <tr>
   <td>searchCallback</td>
   <td>Functie</td>
   <td>Callback voor het activeren van zoeken naar 'keyup' van gebeurtenissen. Standaard naar 'CQ.wcm.SiteAdmin.doSearch'</td>
  </tr>
 </tbody>
</table>

#### PropertyPredicate {#propertypredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap<br /> </strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>predikaatName</td>
   <td>Tekenreeks</td>
   <td>Naam van de voorspelling. Heeft als standaardwaarde 'eigenschap'</td>
  </tr>
  <tr>
   <td>propertyName</td>
   <td>Tekenreeks </td>
   <td>Naam van de eigenschap JCR. Standaard naar 'jcr:title'</td>
  </tr>
  <tr>
   <td>defaultValue<br /> </td>
   <td>Tekenreeks<br /> </td>
   <td>Standaardwaarde vooraf ingevuld.<br /> </td>
  </tr>
 </tbody>
</table>

#### PathPredicate {#pathpredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap<br /> </strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>predikaatName</td>
   <td>Tekenreeks</td>
   <td>Naam van de voorspelling. Heeft als standaardwaarde 'path'</td>
  </tr>
  <tr>
   <td>rootPath</td>
   <td>Tekenreeks </td>
   <td>Hoofdpad van de voorspelling. Standaard naar '/content/dam'</td>
  </tr>
  <tr>
   <td>pathFieldPredicateName</td>
   <td>Tekenreeks</td>
   <td>Standaard naar map</td>
  </tr>
  <tr>
   <td>showFlatOption</td>
   <td>Boolean</td>
   <td>Markering voor het selectievakje 'Zoeken in submappen' weergeven. Heeft als standaardwaarde true.</td>
  </tr>
 </tbody>
</table>

#### DatePredicate {#datepredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap<br /> </strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>predikaatName</td>
   <td>Tekenreeks</td>
   <td>Naam van de voorspelling. Wordt standaard ingesteld op 'daterange'</td>
  </tr>
  <tr>
   <td>eigenschapsnaam</td>
   <td>Tekenreeks</td>
   <td>Naam van de eigenschap JCR. Standaard naar 'jcr:content/jcr:lastModified'</td>
  </tr>
  <tr>
   <td>defaultValue </td>
   <td>Tekenreeks </td>
   <td>Vooraf ingestelde standaardwaarde </td>
  </tr>
 </tbody>
</table>

#### OptionsPredicate {#optionspredicate}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap<br /> </strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>title </td>
   <td>Tekenreeks </td>
   <td>Hiermee wordt een extra bovenste titel toegevoegd </td>
  </tr>
  <tr>
   <td>predikaatName</td>
   <td>Tekenreeks</td>
   <td>Naam van de voorspelling. Wordt standaard ingesteld op 'daterange'</td>
  </tr>
  <tr>
   <td>eigenschapsnaam</td>
   <td>Tekenreeks</td>
   <td>Naam van de eigenschap JCR. Standaard naar 'jcr:content/metadata/cq:tags'</td>
  </tr>
  <tr>
   <td>samenvouwen</td>
   <td>Tekenreeks</td>
   <td>Niveau samenvouwen. Heeft als standaardwaarde 'niveau1'</td>
  </tr>
  <tr>
   <td>triggerSearch</td>
   <td>Boolean </td>
   <td>Markering voor het activeren van zoekopdrachten bij controle. Standaard ingesteld op false</td>
  </tr>
  <tr>
   <td>searchCallback</td>
   <td>Functie</td>
   <td>Callback voor het teweegbrengen van onderzoek. Wordt standaard ingesteld op 'CQ.wcm.SiteAdmin.doSearch'</td>
  </tr>
  <tr>
   <td>searchTimeoutTime</td>
   <td> Getal</td>
   <td>Time-out voordat searchCallback wordt gestart. Wordt standaard ingesteld op 800 ms</td>
  </tr>
 </tbody>
</table>
