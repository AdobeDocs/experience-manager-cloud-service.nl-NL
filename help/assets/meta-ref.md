---
title: Referentie metagegevensschema
description: 'Leer meer over standaardconventies voor het beschrijven van metagegevens van elementen, zoals Dublin Core, IPTC en ander metagegevensschema. '
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Referentie metagegevensschema {#metadata-schemata-reference}

De volgende naslaggids bevat informatie over een bepaald metagegevensschema (in alfabetische volgorde) en een lijst met eigenschappen en de bijbehorende definities.

## Dublin Core {#dublin-core}

De meta-gegevens van de Kern van Dublin verstrekt een gestandaardiseerde reeks overeenkomsten voor het beschrijven van activa om hen gemakkelijker te maken te vinden. In AEM Assets, beschrijft de Kern van Dublin digitale activa met inbegrip van video, geluid, beelden, en documenten.

De eenvoudige Dublin Core Metadata Element Set (DCMES) bevat 15 metagegevenselementen die in de volgende tabel worden vermeld. Elk Dublin Core-element is optioneel en kan worden herhaald. U kunt Dublin Core-metagegevens toevoegen of verwijderen op dezelfde manier als voor mediatype-specifieke metagegevens.

Naast het DCMES zijn er andere metagegevenselementen die door het Dublin Core-initiatief zijn gecreëerd. Zie het [Dublin Core-initiatief](https://dublincore.org/) voor meer informatie.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td> 
   <td><strong>Beschrijving</strong></td> 
  </tr>
  <tr>
   <td>contribuant</td> 
   <td>De persoon die of het bedrijf dat verantwoordelijk is voor het leveren van bijdragen aan de inhoud.</td> 
  </tr>
  <tr>
   <td>dekking</td> 
   <td>De geografische locatie of tijdsperiode waarop het actief betrekking heeft.<br /> </td> 
  </tr>
  <tr>
   <td>schepper</td> 
   <td>De persoon of het bedrijf die verantwoordelijk is voor het maken van de inhoud.</td> 
  </tr>
  <tr>
   <td>date</td> 
   <td>Datum of periode die aan het element is gekoppeld.<br /> </td> 
  </tr>
  <tr>
   <td>beschrijving</td> 
   <td>Meer informatie over het element.</td> 
  </tr>
  <tr>
   <td>format</td> 
   <td>De bestandsindeling, het fysieke medium of de afmetingen van het element. AEM gebruikt <code>dc:format</code> om het mime-type van de activa aan te duiden.<br /> </td> 
  </tr>
  <tr>
   <td>id</td> 
   <td>Een unieke verwijzing naar het element.</td> 
  </tr>
  <tr>
   <td>language</td> 
   <td>De taal van het element (bijvoorbeeld en voor Engels).</td> 
  </tr>
  <tr>
   <td>uitgever</td> 
   <td>De persoon of het bedrijf die verantwoordelijk is voor het ter beschikking stellen van het actief.</td> 
  </tr>
  <tr>
   <td>relation</td> 
   <td>Een gerelateerd actief.</td> 
  </tr>
  <tr>
   <td>rechten</td> 
   <td>Informatie over wie de rechten op dit actief heeft.</td> 
  </tr>
  <tr>
   <td>source</td> 
   <td>Een gerelateerd actief waarvan het actief is afgeleid.</td> 
  </tr>
  <tr>
   <td>onderwerp</td> 
   <td>Het onderwerp van de activa.<br /> </td> 
  </tr>
  <tr>
   <td>title</td> 
   <td>Een naam voor het element.</td> 
  </tr>
  <tr>
   <td>type</td> 
   <td>De aard of het genre van het actief.</td> 
  </tr>
 </tbody>
</table>

## IPTC {#iptc}

De International Press Telecommunications Council (IPTC) is een consortium van nieuwsagentschappen over de hele wereld - een van de doelstellingen is het ontwikkelen en handhaven van technische normen. In de IPTC is een reeks standaarden voor fotometagegevens gedefinieerd voor afbeeldingen die vrijwel overal door fotografen worden geaccepteerd. Deze metagegevensstandaarden maakten deel uit van de bredere standaard die bekend staat als het IPTC Information Interchange Model (IIM) dat in de jaren negentig is gemaakt.

Hoewel de IPTC-headerinformatie meestal is vervangen door XMP, zijn een IPTC-kernschema en een extensieschema beschikbaar voor XMP. In afbeeldingsprogramma&#39;s worden zowel de XMP- als de IPTC-eigenschappen gesynchroniseerd.
