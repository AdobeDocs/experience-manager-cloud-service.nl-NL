---
title: Inleiding tot elementen als een [!DNL Cloud Service]
description: Nieuwe functies in Elementen als een [!DNL Cloud Service].
contentOwner: AG
feature: Asset Management
role: User,Leader,Architect
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: f075c6032edb23f9cf52ad53ae2a628915e76ec2
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 1%

---

# Elementen introduceren als een [!DNL Cloud Service] {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

Adobe Experience Manager Assets as a [!DNL Cloud Service] biedt een cloud-native, PaaS-oplossing voor bedrijven om niet alleen hun Digital Asset Management- en Dynamic Media-bewerkingen met snelheid en impact uit te voeren, maar ook intelligente mogelijkheden van de volgende generatie, zoals AI/ML, te gebruiken vanuit een systeem dat altijd actueel, altijd beschikbaar en altijd leerend is.

Gelijktijdige inname van vele activa of complexe activa is middel-intensieve taak voor een instantie van de Auteur van de Experience Manager. De primaire instantie verbruikt aanzienlijke CPU-, geheugen- en I/O-bronnen wanneer middelen worden toegevoegd, verwerkt of zelfs gemigreerd. Dergelijke prestatieproblemen zijn van invloed op het ontwerpen en bladeren door eindgebruikers.

Bedrijven hebben ondersteuning nodig voor een groot aantal verschillende bestandsindelingen en inhoudsresoluties voor meervoudige apparaten, transgeografische situaties en meertalige gebruiksgevallen. Voor de verwerking en opslag van bedrijfsmiddelen zijn middelen en mogelijkheden nodig die een traditionele oplossing kunnen overbelasten. Soms leveren technische beperkingen van de verwerking van activa niet de gewenste resultaten op en op andere tijdstippen vormen de opslagkosten een belemmering voor winstmarges.

Om te beginnen, begrijp [voordelen van een cloudeigen aanbod](#solution-benefits). Uitchecken wat er in de tabel staat [wijzigingen in Experience Manager als een [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md) die ook gevolgen had voor Experience Manager Assets, gevolgd door de opmerkelijke [wijzigingen in elementen](/help/assets/assets-cloud-changes.md).

Lees verder om de [details van de nieuwe middelenmogelijkheden](#whats-new-assets) en de [bekende problemen](/help/release-notes/maintenance/latest.md). Zie een lijst met [vervangen of verwijderde functionaliteit](/help/release-notes/deprecated-removed-features.md) om te weten wat er is verwijderd uit deze release. Tot slot, begrijp de termen van de Experience Manager met behulp van dit [woordenlijst](/help/overview/terminology.md).

## Oplossingsvoordelen {#solution-benefits}

Hieronder worden de belangrijkste voordelen van activa als een [!DNL Cloud Service]. Zie voor meer informatie [overzicht van de Experience Manager als [!DNL Cloud Service]](/help/overview/introduction.md).

* **Moderne cloudservices voor de verwerking van bedrijfsmiddelen**: De nieuwe assetmicroservices zijn een cloudgebaseerde, schaalbare, betrouwbare en probleemloze service voor de verwerking van bedrijfsmiddelen.
* **Zeer schaalbaar**: Elastische schaalbaarheid voor alle typen implementaties. Praktisch onbeperkte middelen die op bestelling, zoals en wanneer nodig beschikbaar zijn. Bespart de kosten van overontwerp in vergelijking met een traditioneel systeem.
* **Nieuwste software**: Altijd actueel en altijd bijgewerkt. Alle gebruikers beschikken alleen over de nieuwste software met alle patches, functies, beveiliging en oplossingen voor problemen die voor hen beschikbaar zijn. Ontwikkelaars en integrators werken met de nieuwste set API&#39;s zonder ondersteuning voor meerdere versies.
* **Altijd online**: Geen downtime (0dt), dankzij de instantie die in een cluster met back-ups en redundantie is geïmplementeerd. Upgrades zijn ook 0dt.
* **Constante bewaking**: De controle van het systeem is geautomatiseerde en ingebouwde controles en trekkers helpen de prestaties, de beschikbaarheid, en algemene robuustheid handhaven.
* **Hapeloze implementaties**: Experience Manager in de Cloud-bewerkingen wordt volledig geautomatiseerd en hoeft niet handmatig te worden uitgevoerd. Voor geautomatiseerde implementaties automatiseert de component Cloud Manager (CM) de opbouw van implementeerbare Docker-afbeeldingen die uw aangepaste code bevatten.

## Beschikbare persoonlijke ervaringen

Adobe biedt robuuste DAM-oplossingen (Digital Asset Management) waarmee u optimaal kunt profiteren van uw digitale middelen. Adobe Experience Manager Assets heeft twee aparte ervaringen die dezelfde gegevensopslagruimte voor Cloud Services gebruiken:

* **Admin View**: De bestaande Assets as a Cloud Service gebruikersinterface. Gebruik de beheerweergave voor alle geavanceerde mogelijkheden voor middelenbeheer, zoals integratie, workflows, automatisering van inhoud, publicatie en meer.

* **Weergave Elementen**: Adobe-tweight-beheerervaring voor opslag, beheer, detectie en gebruik van digitale elementen. Gestroomlijnde gebruikersinterface met essentiële mogelijkheden voor middelenbeheer. Ontworpen voor de lichtgewicht DAM-gebruikers met focus op uploaden, metagegevensbeheer, zoeken, downloaden en delen.

Gebruikers met toegang tot de beheerweergave hebben ook toegang tot de weergave Middelen. De weergave Elementen biedt een vereenvoudigde gebruikersinterface waarmee u uw digitale elementen eenvoudig kunt beheren, ontdekken en distribueren. Een brede reeks gebruikers van verschillende functies, met inbegrip van creatieve, marketing en brancheteams kunnen aan activa samenwerken en tot het recht toegang hebben, erkende activa wanneer en waar zij hen nodig hebben. Veel incidentele DAM-gebruikers geven de voorkeur aan de weergave Middelen, omdat deze alleen een subset functies bevat. De ervaring is gericht op creatieve personen, alleen-lezen klanten en minder belangrijke DAM-gebruikers.

DAM-bibliotheken, ontwikkelaars en supergebruikers kunnen de Admin-weergave blijven gebruiken of, indien nodig, schakelen tussen de gebruikersinterfaces. U kunt de ervaring selecteren die het beste voor uw rol werkt.

![add-tags](assets/newui-overview.svg)

Zie de weergave Elementen voor informatie over hoe u toegang kunt krijgen tot de weergave Middelen en over enkele vereenvoudigingen die deze aanbiedt via de beheerweergave.

## Nieuwe middelenmogelijkheden {#whats-new-assets}

De belangrijkste nieuwe mogelijkheden zijn:

* [Asset-microservices](/help/assets/asset-microservices-overview.md)
* [Methoden voor het uploaden van middelen](/help/assets/add-assets.md)

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [HTTP-API voor assets](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Assets doorzoeken](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Rapporten over assets](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Facetten doorzoeken](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
