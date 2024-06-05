---
title: Inhoudsfragmenten die componenten voor rendering configureren
description: Inhoudsfragmenten die componenten voor rendering configureren
exl-id: 6606dc3b-f1b8-4941-8fd0-f69cbd414afa
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---

# Inhoudsfragmenten die componenten voor rendering configureren{#content-fragments-configuring-components-for-rendering}

Er zijn verschillende [geavanceerde services](#definition-of-advanced-services-that-need-configuration) gerelateerd aan de rendering van inhoudsfragmenten. Om deze diensten te gebruiken, moeten de middeltypes van dergelijke componenten zich aan het kader van inhoudsfragmenten bekendmaken.

Dit wordt gedaan door te vormen [OSGi Service - Configuratie van de Component van het Fragment van de Inhoud](#osgi-service-content-fragment-component-configuration).

Deze informatie is vereist wanneer:

* U moet uw eigen op fragmenten gebaseerde component voor inhoudsfragmenten implementeren,
* En de geavanceerde services moeten worden gebruikt.

Adobe raadt u aan de Core Components (Basiscomponenten) te gebruiken.

>[!CAUTION]
>
>* **Als u het [geavanceerde services](#definition-of-advanced-services-that-need-configuration)** hieronder beschreven, kunt u deze configuratie negeren.
>
>* **Wanneer u de component(en) buiten de doos uitbreidt of gebruikt**, wordt het niet geadviseerd om de configuratie te veranderen OSGi.
>
>* **U kunt een geheel nieuwe component schrijven die alleen de API voor inhoudsfragmenten gebruikt, zonder geavanceerde services**. In een dergelijk geval moet u de component echter zodanig ontwikkelen dat deze de juiste verwerking afhandelt.
>
>Daarom wordt aanbevolen de Core Components te gebruiken.

## Definitie van de Geavanceerde Diensten die Configuratie vereisen {#definition-of-advanced-services-that-need-configuration}

De diensten die de registratie van een component vereisen zijn:

* De afhankelijkheden correct bepalen tijdens de publicatie (dat wil zeggen dat fragmenten en modellen automatisch met een pagina kunnen worden gepubliceerd als ze zijn gewijzigd sinds de laatste publicatie).
* Ondersteuning voor inhoudsfragmenten in volledige tekstzoekopdracht.
* Het beheer/de verwerking van *tussenliggende inhoud.*
* Het beheer/de verwerking van *gemengde media-elementen.*
* Dispatcher flush for referenced fragments (if a page containing a fragment is re-published).
* Op alinea&#39;s gebaseerde rendering gebruiken.

Als u één of meerdere van deze eigenschappen nodig hebt, dan (typisch) is het gemakkelijker om de uit-van-de-doos Geavanceerde Diensten te gebruiken, in plaats van hen van kras te ontwikkelen.

## OSGi Service - Configuratie van de Component van het Fragment van de Inhoud {#osgi-service-content-fragment-component-configuration}

De configuratie moet aan de dienst worden gebonden OSGi **Configuratie van inhoudsfragmentcomponent**:

`com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl`

>[!NOTE]
>
>Zie [OSGi-configuratie](/help/implementing/deploying/overview.md#osgi-configuration) voor nadere bijzonderheden.

Bijvoorbeeld:

![Configuratie van OSGi-component van fragmentatie van configuratieinhoud](assets/cf-component-configuration-osgi.png)

De configuratie OSGi is:

<table>
 <thead>
  <tr>
   <td>Label</td>
   <td>OSGi-configuratie<br /> </td>
   <td>Beschrijving</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><strong>Het type Resource</strong></td>
   <td><code>dam.cfm.component.resourceType</code></td>
   <td>Het brontype dat moet worden geregistreerd, bijvoorbeeld <br /> <p><span class="cmp-examples-demo__property-value"><code>core/wcm/components/contentfragment/v1/contentfragment</code></code></p> </td>
  </tr>
  <tr>
   <td><strong>Verwijzing, eigenschap</strong></td>
   <td><code>dam.cfm.component.fileReferenceProp</code></td>
   <td>De naam van de eigenschap die de verwijzing naar het fragment bevat, bijvoorbeeld <code>fragmentPath</code> of <code>fileReference</code></td>
  </tr>
  <tr>
   <td><strong>Element(en), eigenschap</strong></td>
   <td><code>dam.cfm.component.elementsProp</code></td>
   <td>De naam van de eigenschap die de naam/namen bevat van het element/de elementen die moeten worden gerenderd, bijvoorbeeld<code>elementName</code></td>
  </tr>
  <tr>
   <td><strong>Variatie, eigenschap</strong><br /> </td>
   <td><code>dam.cfm.component.variationProp</code></td>
   <td>De naam van de eigenschap die de naam bevat van de variatie die moet worden gerenderd, bijvoorbeeld<code>variationName</code></td>
  </tr>
 </tbody>
</table>

Voor bepaalde functionaliteit moet de component zich aan vooraf gedefinieerde conventies houden. In de volgende tabel worden de eigenschappen weergegeven die door de component voor elke alinea moeten worden gedefinieerd (dat wil zeggen: `jcr:paragraph` voor elke componentinstantie) zodat de services deze op de juiste wijze kunnen detecteren en verwerken.

<table>
 <thead>
  <tr>
   <td>Eigenschapnaam</td>
   <td>Beschrijving</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>paragraphScope</code></td>
   <td><p>Een tekenreekseigenschap die definieert hoe alinea's moeten worden uitgevoerd als ze zich in <em>rendermodus voor één element</em>.</p> <p>Waarden:</p>
    <ul>
     <li><code>all</code> : alle alinea's renderen</li>
     <li><code>range</code> : voor het weergeven van het bereik van alinea's die worden geleverd door <code>paragraphRange</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphRange</code></td>
   <td><p>Een tekenreekseigenschap die het bereik definieert van alinea's die moeten worden uitgevoerd als deze zich in <em>rendermodus voor één element</em>.</p> <p>Indeling:</p>
    <ul>
     <li><code>1</code> of <code>1-3</code> of <code>1-3;6;7-8</code> of <code>*-3;5-*</code>
     <ul>
       <li><code>-</code> bereikindicator</li>
       <li><code>;</code> lijstscheidingsteken</li>
       <li><code>*</code> jokerteken</li>
     </ul>
     </li>
     <li>alleen geëvalueerd als <code>paragraphScope</code> is ingesteld op <code>range</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphHeadings</code></td>
   <td>Een Booleaanse eigenschap die definieert of koppen (bijvoorbeeld <code>h1</code>, <code>h2</code>, <code>h3</code>) worden als alinea's (<code>true</code>) of niet (<code>false</code>)</td>
  </tr>
 </tbody>
</table>

## Voorbeeld {#example}

Zie bijvoorbeeld het volgende (op een uit-van-de-doos AEM instantie):

```
/apps/core/wcm/config/com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl-core-comp-v1.config
```

Dit bevat:

```
dam.cfm.component.resourceType="core/wcm/components/contentfragment/v1/contentfragment"
dam.cfm.component.fileReferenceProp="fragmentPath"
dam.cfm.component.elementsProp="elementName"
dam.cfm.component.variationProp="variationName"
```
