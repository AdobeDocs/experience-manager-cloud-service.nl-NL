---
title: Afbeeldingseditor
description: De Afbeeldingseditor is een AEM en kan door componenten worden gebruikt om het bewerken van afbeeldingen door makers van inhoud te vergemakkelijken.
translation-type: tm+mt
source-git-commit: 83c27daae4e8ae2ae6a8f115c9da9527971c6ecb
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---


# Afbeeldingseditor {#image-editor}

De Afbeeldingseditor is een AEM en kan door componenten worden gebruikt om het bewerken van afbeeldingen door makers van inhoud te vergemakkelijken.

## Relatieve eenheden voor afbeelding met hyperlinks {#relative-units-for-image-map}

In de Afbeeldingseditor blijven afbeeldingskaartgebieden behouden als absolute en relatieve eenheden. Relatieve eenheden zijn handig wanneer deze worden opgegeven als gegevenskenmerken voor het dynamisch wijzigen van de grootte van een afbeeldingskaart (ten opzichte van de afbeeldingsgrootte) aan de clientzijde in een responsieve afbeeldingscomponent.

### imageMap, eigenschap {#imagemap-property}

De coördinaten van de afbeelding met hyperlinks blijven als een `imageMap` eigenschap bij de JCR. Deze heeft de volgende indeling.

In de eigenschap worden kaartgebieden als volgt opgeslagen:

`[area1][area2][...]`

Vlakindeling:

`[SHAPE(COORDINATES)"HREF"|"TARGET"|"ALT"|(RELATIVE_COORDINATES)]`

Voorbeeld:

`[rect(0,0,10,10)"https://www.adobe.com"|"_self"|"alt"|(0,0,0.8,0.8)]`
`[circle(10,10,10)"https://www.adobe.com"|"_self"|"alt"|(0.8,0.8,0.8)]`

## Ondersteuning voor SVG-afbeeldingen {#support-for-svg-images}

SVG (Scalable Vector Graphics) wordt ondersteund door de Afbeeldingseditor.

* Het slepen en neerzetten van een SVG-element van DAM en het uploaden van een SVG-bestandsupload vanuit een lokaal bestandssysteem worden beide ondersteund.

## Plug-ins inschakelen op basis van MIME-type {#enabling-plugins-by-mime-type}

In bepaalde situaties moeten ontwerpacties voor bepaalde MIME-typen worden beperkt, omdat er geen ondersteuning is voor verwerking op de server. Het bewerken van SVG-afbeeldingen is bijvoorbeeld niet toegestaan.

Plug-ins in de Afbeeldingseditor kunnen selectief worden ingeschakeld door het MIME-type door een `supportedMimeTypes` eigenschap in te stellen op het configuratieknooppunt van de afzonderlijke plug-in.

### Voorbeeld {#example}

Stel bijvoorbeeld dat de mogelijkheid om uit te snijden alleen is toegestaan voor GIF-, JPEG-, PNG-, WEBP- en TIFF-afbeeldingen.

De `supportedMimeTypes` eigenschap moet vervolgens worden ingesteld als een tekenreeks van de toegestane MIME-typen op het configuratieknooppunt van de insteekmodule op het `cq:editConfig` knooppunt van de afbeeldingscomponent.

`/apps/core/wcm/components/image/v2/image/cq:editConfig`

```xml
 jcr:primaryType="cq:EditConfig">
     <cq:dropTargets jcr:primaryType="nt:unstructured">
         <image ...>
            ...
         </image>
     </cq:dropTargets>
     <cq:inplaceEditing
         jcr:primaryType="cq:InplaceEditingConfig"
         active="{Boolean}true"
         editorType="image">
         <config jcr:primaryType="nt:unstructured">
             <plugins jcr:primaryType="nt:unstructured">
                 <crop
                     jcr:primaryType="nt:unstructured"
                     supportedMimeTypes="[image/gif,image/jpeg,image/png,image/webp,image/tiff]"
                     features="*">
                     <aspectRatios jcr:primaryType="nt:unstructured">
                        ...
                     </aspectRatios>
                 </crop>
                 ...
             </plugins>
             <ui jcr:primaryType="nt:unstructured">
                 ...
             </ui>
         </config>
     </cq:inplaceEditing>
 </jcr:root>
```
