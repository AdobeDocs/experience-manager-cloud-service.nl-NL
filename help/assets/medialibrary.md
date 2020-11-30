---
title: AEM Assets versus AEM MediaLibrary
description: Veelgestelde vragen over AEM Assets en. AEM Mediabibliotheek, inclusief verschillen tussen de twee.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 1%

---


# AEM Assets versus AEM MediaLibrary veelgestelde vragen {#aem-assets-vs-aem-medialibrary}

Adobe Experience Manager (AEM) Activa maken integrerend deel uit van het AEM. Deze soepele integratie wordt gezien als een groot voordeel van AEM en zorgt voor consistentie in inhoudsbeheer en hoge productiviteit voor auteurs van inhoud.

## Wat is AEM Assets? {#what-is-aem-assets}

AEM Assets is een toepassing op het AEM-Platform waarmee onze klanten hun digitale middelen (afbeeldingen, video&#39;s, documenten en audioclips) kunnen beheren in een opslagplaats op internet. AEM Assets biedt ondersteuning voor metagegevens, uitvoeringen, de Digital Asset Management Finder en beheer via de gebruikersinterface.

## Wat is de AEM-mediabibliotheek? {#what-is-the-aem-media-library}

De AEM Mediabibliotheek is een aangewezen onderdeel van de AEM WCM-inhoudsopslagruimte waar afbeeldingen en andere gedeelde bronnen worden opgeslagen. De mediabibliotheek gebruikt de Digital Asset Management-mogelijkheden van AEM WCM.

## Wat krijg ik van AEM Assets dat geen deel uitmaakt van AEM WCM? {#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

De unieke functies die alleen beschikbaar zijn voor klanten van AEM Assets zijn:

1. de mogelijkheid om andere metagegevens dan titel, tags en beschrijving te extraheren en te bewerken.
1. Klik op de tweede knop naast de sitebeheerder in het welkomstscherm op AEM Assets Admin.
1. Alle workflowstappen met betrekking tot Digital Asset Management, namelijk AEM Assets Ingestie, AEM Assets Deletion, AEM Assets Sub-Asset-Handling, extractie van AEM Assets-metagegevens.
1. bibliotheken , waaronder &quot; dam &quot; im package space .

Voor het gebruik van deze functies is een geldige AEM Assets-licentie vereist.

## Is AEM Assets beschikbaar als apart pakket? {#is-aem-assets-available-as-a-separate-package}

Nee. Om de installatie en implementatie te vereenvoudigen, worden alle AEM toepassingen en invoegtoepassingen geleverd in één pakket met alle functionaliteit inbegrepen. Dit betekent niet dat u toestemming hebt om alle functies in het pakket te gebruiken.

## Ik wil metagegevens van digitale elementen bewerken. Heb ik AEM Assets nodig? {#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

Als u andere metagegevens dan titel, beschrijving en tags wilt bewerken, is een licentie voor AEM Assets vereist.

## Ik wil de categorie voorspellen gebruiken op mijn website. Heb ik AEM Assets nodig? {#i-want-to-use-the-category-predicate-on-my-website-do-i-need-aem-assets}

Ja, de categorie voorspelt, samen met alle andere componenten die in het Centrum van de Pers van de Geometrixx worden gebruikt deel van AEM Assets uitmaken en een vergunning van AEM Assets vereisen.

## Ik wil afbeeldingen automatisch vergroten of verkleinen tijdens het importeren. Heb ik AEM Assets nodig? {#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

Ja. Afbeeldingen vergroten/verkleinen en automatische workflowgestuurde transformaties en de mogelijkheid om uitvoeringen te beheren maken deel uit van AEM Assets en hebben een AEM Assets-licentie nodig.

## Ik wil afbeeldingen vergroten of verkleinen met een aangepaste afbeeldingscomponent. Heb ik AEM Assets nodig? {#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

De afbeeldingscomponent maakt deel uit van AEM WCM. De grafische bibliotheek die door de afbeeldingscomponent (maar ook door AEM Assets) wordt gebruikt, maakt deel uit van het AEM platform en heeft geen AEM Assets-licentie nodig.

## Hoe kan ik voorkomen dat mijn gebruikers AEM Assets gebruiken als ik geen licentie voor AEM Assets heb verleend? {#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

U kunt alle AEM Assets-specifieke workflows, componenten, taxonomieën, opties en de AEM Assets-beheerder uit AEM verwijderen. Zo voorkomt u dat gebruikers per ongeluk AEM Assets-functies gebruiken waarvoor u geen licentie hebt verleend.

## Ik wil afbeeldingen aan een pagina toevoegen en deze afbeeldingen uitsnijden en vergroten of verkleinen. Heb ik AEM Assets nodig? {#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

In dit geval is het niet verplicht om AEM Assets te kopen, zelfs als de mediabibliotheek niet hoeft te worden gebruikt om afbeeldingen op een website te gebruiken, omdat de component smart image het uploaden van afbeeldingen naar de pagina toestaat.

## Een gedetailleerde lijst met functies die beschikbaar zijn in AEM Assets versus Media Library {#listoffeatures}

**AEM Assets**

* Verzamelingen en lichtbak
* Geavanceerde eigenschappen en beheer van metagegevens
* Adobe Asset Link (verbinding maken met Creative Cloud voor bedrijf)
* Bureaubladapp AEM
* Profielen verwerken
* InDesign-serverintegratie
* Middelensjablonen en kader voor catalogusproducenten
* Adobe Photoshop, Illustrator en aan InDesign gekoppelde middelen
* Meertalig beheer van bedrijfsmiddelen
* PIM-integratie
* Rights Management
* Camera Raw ondersteuning
* Beheer en configuratie van zoekfactoren
* Vooraf gebouwde DAM-workflows (bijvoorbeeld foto&#39;s)
* Rapportage en analyse van bedrijfsmiddelen: Asset Insights
* 3D-beheer van bedrijfsmiddelen
* Gekoppelde assets
* Brand Portal
* Zelfbedieningstoegang
* Bladeren, zoeken en downloaden
* Verzamelingen en het delen van mappen
* Admin Tools
* Slimme tags
* Visueel zoeken
* Interface voor middelenbeheer

**Mediabibliotheek**

* Eigenschappen van standaardmetagegevens
* Tagbeheer
* Versiebeheer
* Statische uitvoeringen
* Projecten, Taken, het Authoring van het werkschema
* Activiteitenstroom (tijdlijn)
* Query Builder (API)
* Marketing Cloud-integratie
* UI-aanpassing en -uitbreiding
* Opmerkingen en annotatie