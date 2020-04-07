---
title: Inhoudsfragmenten die componenten voor rendering configureren
description: Inhoudsfragmenten die componenten voor rendering configureren
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Inhoudsfragmenten die componenten voor rendering configureren{#content-fragments-configuring-components-for-rendering}

Er zijn verschillende [geavanceerde services](#definition-of-advanced-services-that-need-configuration) voor het renderen van inhoudsfragmenten. Om deze diensten te gebruiken, moeten de middeltypes van dergelijke componenten zich aan het kader van inhoudsfragmenten bekendmaken.

Dit wordt gedaan door de Dienst [te vormen OSGi - de Configuratie](#osgi-service-content-fragment-component-configuration)van de Component van het Fragment van de Inhoud.

Deze informatie is vereist wanneer:

* U moet uw eigen op fragmenten gebaseerde component voor inhoudsfragmenten implementeren,
* We moeten gebruik maken van de geavanceerde services.

Het wordt echter aanbevolen de Core Components (Basiscomponenten) te gebruiken.

>[!CAUTION]
>
>* **Als u de hieronder beschreven[geavanceerde services](#definition-of-advanced-services-that-need-configuration)**niet nodig hebt, kunt u deze configuratie negeren.
   >
   >
* **Wanneer u of de uit-van-de-doos component(en)** uitbreidt gebruikt, wordt het niet geadviseerd om de configuratie te veranderen OSGi.
   >
   >
* **U kunt een geheel nieuwe component schrijven die alleen de API voor inhoudsfragmenten gebruikt, zonder geavanceerde services**. In een dergelijk geval moet u de component echter zodanig ontwikkelen dat deze de juiste verwerking afhandelt.
>
>
Daarom wordt aanbevolen de Core Components te gebruiken.

## Definitie van de Geavanceerde Diensten die Configuratie vereisen {#definition-of-advanced-services-that-need-configuration}

De diensten die de registratie van een component vereisen zijn:

* De afhankelijkheden correct bepalen tijdens de publicatie (zorg er dus voor dat fragmenten en modellen automatisch met een pagina kunnen worden gepubliceerd als ze zijn gewijzigd sinds de laatste publicatie).
* Ondersteuning voor inhoudsfragmenten in volledige tekstzoekopdracht.
* Het beheer/de afhandeling van *tussen inhoud.*
* Beheer/verwerking van *gemengde media-elementen.*
* Dispatcher flush for referenced fragments (if a page containing a fragment is re-published).
* Op alinea&#39;s gebaseerde rendering gebruiken.

Als u één of meerdere van deze eigenschappen nodig hebt, dan (typisch) is het gemakkelijker om de uit-van-de-doos Geavanceerde Diensten te gebruiken, in plaats van hen van kras te ontwikkelen.

## OSGi Service - Configuratie van de Component van het Fragment van de Inhoud {#osgi-service-content-fragment-component-configuration}

De configuratie moet aan de Configuratie **van de Component van het Fragment van de Component van de** Inhoud worden gebonden OSGi:

`com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl`

>[!NOTE]
>
>Zie [Configuratie](/help/implementing/deploying/overview.md#osgi-configuration) OSGi voor verdere details.

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
   <td>Het type bron dat moet worden geregistreerd; bijv. <br /> <p><span class="cmp-examples-demo__property-value"><code>core/wcm/components/contentfragment/v1/contentfragment</code></code></p> </td>
  </tr>
  <tr>
   <td><strong>Verwijzing, eigenschap</strong></td>
   <td><code>dam.cfm.component.fileReferenceProp</code></td>
   <td>De naam van de eigenschap die de verwijzing naar het fragment bevat; bijv. <code>fragmentPath</code> of <code>fileReference</code></td>
  </tr>
  <tr>
   <td><strong>Element(en), eigenschap</strong></td>
   <td><code>dam.cfm.component.elementsProp</code></td>
   <td>De naam van de eigenschap die de naam of namen bevat van het element of de elementen die moeten worden gerenderd; bijv.<code>elementName</code></td>
  </tr>
  <tr>
   <td><strong>Variatie, eigenschap</strong><br /> </td>
   <td><code>dam.cfm.component.variationProp</code></td>
   <td>De naam van de eigenschap die de naam bevat van de wijziging die moet worden gerenderd; bijv.<code>variationName</code></td>
  </tr>
 </tbody>
</table>

Voor bepaalde functionaliteit moet de component zich aan vooraf gedefinieerde conventies houden. In de volgende tabel worden de eigenschappen beschreven die door de component voor elke alinea (d.w.z. `jcr:paragraph` voor elke componentinstantie) moeten worden gedefinieerd, zodat de services deze op de juiste wijze kunnen detecteren en verwerken.

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
   <td><p>Een tekenreekseigenschap die definieert hoe alinea's moeten worden uitgevoerd als <em>één element wordt gerenderd</em>.</p> <p>Waarden:</p>
    <ul>
     <li><code>all</code> : om alle alinea's te renderen</li>
     <li><code>range</code> : om het bereik van alinea's te bepalen dat wordt verschaft door <code>paragraphRange</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphRange</code></td>
   <td><p>Een tekenreekseigenschap die het bereik definieert van alinea's die moeten worden uitgevoerd in de rendermodus <em>van</em>één element.</p> <p>Format:</p>
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
   <td>Een Booleaanse eigenschap die definieert of koppen (bijvoorbeeld <code>h1</code>, <code>h2</code>, <code>h3</code>) worden geteld als alinea's (<code>true</code>) of niet (<code>false</code>)</td>
  </tr>
 </tbody>
</table>

## Voorbeeld {#example}

Zie het volgende voorbeeld (bij een AEM-instantie buiten de box):

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

