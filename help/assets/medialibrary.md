---
title: AEM Assets vs. AEM MediaLibrary
description: Veelgestelde vragen over AEM Assets en. AEM-mediabibliotheek, inclusief verschillen tussen de twee.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 1%

---


# Veelgestelde vragen over AEM-middelen en AEM MediaLibrary {#aem-assets-vs-aem-medialibrary}

Adobe Experience Manager (AEM)-middelen maken integraal deel uit van het AEM-platform. Deze soepele integratie wordt gezien als een groot voordeel van AEM en zorgt voor consistentie in inhoudsbeheer en hoge productiviteit voor auteurs van inhoud.

## Wat zijn AEM-middelen? {#what-is-aem-assets}

AEM Assets is een toepassing op het AEM Platform die onze klanten toestaat om hun digitale activa (beelden, video&#39;s, documenten en audioclips) in een Web-based bewaarplaats te beheren. AEM Assets omvat meta-steun, vertoningen, de Vinder van het Beheer van Digitale Middelen en beheer via gebruikersinterface.

## Wat is de AEM-mediabibliotheek? {#what-is-the-aem-media-library}

De AEM-mediabibliotheek is een aangewezen onderdeel van de AEM WCM-inhoudsopslagruimte waar afbeeldingen en andere gedeelde bronnen worden opgeslagen. De mediabibliotheek gebruikt de Digital Asset Management-mogelijkheden van AEM WCM.

## Wat krijg ik van AEM-middelen die geen deel uitmaken van AEM WCM? {#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

Unieke functies die alleen beschikbaar zijn voor klanten van AEM Assets zijn:

1. de mogelijkheid om andere metagegevens dan titel, tags en beschrijving te extraheren en te bewerken.
1. AEM Assets Admin, beschikbaar bij het welkomstscherm door op de tweede knop naast de sitebeheerder te klikken.
1. Alle workflowstappen met betrekking tot Digital Asset Management, namelijk AEM Assets Ingestie, AEM Assets Deletion, AEM Assets Sub-Asset-Handling, AEM Assets-metagegevensextractie.
1. bibliotheken , waaronder &quot; dam &quot; im package space .

Voor het gebruik van deze functies is een geldige licentie voor AEM Assets vereist.

## Is AEM-middelen beschikbaar als een afzonderlijk pakket? {#is-aem-assets-available-as-a-separate-package}

Nee. Om de installatie en implementatie te vereenvoudigen, worden alle AEM-toepassingen en invoegtoepassingen geleverd in één pakket met alle functionaliteit inbegrepen. Dit betekent niet dat u toestemming hebt om alle functies in het pakket te gebruiken.

## Ik wil metagegevens van digitale elementen bewerken. Heb ik AEM-middelen nodig? {#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

Als u andere metagegevens dan titel, beschrijving en tags wilt bewerken, moet u een licentie voor AEM-elementen maken.

## Ik wil de categorie voorspellen gebruiken op mijn website. Heb ik AEM-middelen nodig? {#i-want-to-use-the-category-predicate-on-my-website-do-i-need-aem-assets}

Ja, de categorie voorspelt, samen met alle andere componenten die in het Geometrixx Press Center worden gebruikt maakt deel uit van AEM Assets en vereist een AEM Assets vergunning.

## Ik wil afbeeldingen automatisch vergroten of verkleinen tijdens het importeren. Heb ik AEM-middelen nodig? {#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

Ja. Afbeeldingen vergroten/verkleinen en automatische workflowgestuurde transformaties en de mogelijkheid om uitvoeringen te beheren maken deel uit van AEM Assets en hebben een AEM Assets-licentie nodig.

## Ik wil afbeeldingen vergroten of verkleinen met een aangepaste afbeeldingscomponent. Heb ik AEM-middelen nodig? {#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

De afbeeldingscomponent maakt deel uit van AEM WCM. De grafische bibliotheek die door de afbeeldingscomponent (maar ook door AEM Assets) wordt gebruikt, maakt deel uit van het AEM-platform en heeft geen AEM Assets-licentie nodig.

## Hoe kan ik voorkomen dat mijn gebruikers AEM Assets gebruiken als ik geen licentie heb verleend voor AEM Assets? {#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

U kunt alle AEM Assets-specifieke workflows, componenten, taxonomieën, opties en de AEM Assets-beheerder verwijderen uit AEM. Zo voorkomt u dat uw gebruikers de functies van AEM-middelen die u niet hebt geautoriseerd, op vertrouwelijke wijze gebruiken.

## Ik wil afbeeldingen aan een pagina toevoegen en deze afbeeldingen uitsnijden en vergroten of verkleinen. Heb ik AEM-middelen nodig? {#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

In dit geval is het niet verplicht AEM-elementen te kopen, zelfs niet het gebruik van de mediabibliotheek is vereist om afbeeldingen op een website te gebruiken omdat de component Smart Image het uploaden van afbeeldingen naar de pagina toestaat.

## Een gedetailleerde lijst met functies die beschikbaar zijn in AEM Assets versus Media Library {#listoffeatures}

**AEM Assets**

* Verzamelingen en lichtbak
* Geavanceerde eigenschappen en beheer van metagegevens
* Adobe Asset Link (verbinding maken met Creative Cloud voor ondernemingen)
* AEM-bureaubladtoepassing
* Profielen verwerken
* Integratie van InDesign-servers
* Middelensjablonen en kader voor catalogusproducenten
* Aan Adobe Photoshop, Illustrator en InDesign gekoppelde middelen
* Meertalig beheer van bedrijfsmiddelen
* PIM-integratie
* Rechtenbeheer
* Camera RAW-ondersteuning
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
* Integratie van marketingcloud
* UI-aanpassing en -uitbreiding
* Opmerkingen en annotatie