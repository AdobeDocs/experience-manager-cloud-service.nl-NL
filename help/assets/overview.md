---
title: Inleiding tot elementen als een [!DNL Cloud Service]
description: Meer weten over nieuwe functies en de voordelen van Experience Manager Assets als [!DNL Cloud Service]. Een geïntegreerde PaaS-oplossing voor bedrijven in de cloud.
contentOwner: AK
feature: Asset Management
role: User,Leader,Architect
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: a4601d95076d37ed5df79b7c9dabb8beab8353d0
workflow-type: tm+mt
source-wordcount: '825'
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

Hieronder worden de belangrijkste voordelen van activa als [!DNL Cloud Service]. Zie voor meer informatie [overzicht van de Experience Manager als een [!DNL Cloud Service]](/help/overview/introduction.md).

* **Moderne cloudservices voor middelenverwerking**: De nieuwe assetmicroservices zijn een cloudgebaseerde, schaalbare, betrouwbare en probleemloze service voor de verwerking van bedrijfsmiddelen.
* **Zeer schaalbaar**: Elastische schaalbaarheid voor alle typen implementaties. Praktisch onbeperkte middelen die op bestelling, zoals en wanneer nodig beschikbaar zijn. Bespart de kosten van overontwerp in vergelijking met een traditioneel systeem.
* **Nieuwste software**: Altijd bijgewerkt en bijgewerkt. Alle gebruikers beschikken alleen over de nieuwste software met alle patches, functies, beveiliging en oplossingen voor problemen die voor hen beschikbaar zijn. Ontwikkelaars en integrators werken met de nieuwste set API&#39;s zonder ondersteuning voor meerdere versies.
* **Altijd online**: Geen downtime (0dt), dankzij de instantie die is geïmplementeerd in een cluster met back-ups en redundantie. Upgrades zijn ook 0dt.
* **Constante bewaking**: De controle van het systeem wordt geautomatiseerd en ingebouwde controles en trekkers helpen de prestaties, de beschikbaarheid, en algemene robuustheid handhaven.
* **Hapeloze implementaties**: Experience Manager in de Cloud-bewerkingen wordt volledig geautomatiseerd en hoeft niet handmatig te worden uitgevoerd. Voor geautomatiseerde implementaties automatiseert de component Cloud Manager (CM) de opbouw van implementeerbare Docker-afbeeldingen die uw aangepaste code bevatten.

## Beschikbare persoonlijke ervaringen {#persona-based-experiences}

Adobe biedt robuuste DAM-oplossingen (Digital Asset Management) waarmee u optimaal kunt profiteren van uw digitale middelen. Adobe Experience Manager Assets heeft twee aparte ervaringen die dezelfde gegevensopslagruimte voor Cloud Servicen gebruiken:

* **Admin View**: De as a Cloud Service gebruikersinterface voor bestaande elementen. Gebruik de beheerweergave voor alle geavanceerde mogelijkheden voor middelenbeheer, zoals integratie, workflows, automatisering van inhoud, publicatie en meer.

* **Weergave Elementen**: De lichte ervaring van de Adobe op het gebied van middelenbeheer voor het opslaan, beheren, ontdekken en gebruiken van digitale middelen. Gestroomlijnde gebruikersinterface met essentiële mogelijkheden voor middelenbeheer. Ontworpen voor de lichtgewicht DAM-gebruikers met focus op uploaden, metagegevensbeheer, zoeken, downloaden en delen.

Gebruikers met toegang tot de beheerweergave hebben ook toegang tot de weergave Middelen. De weergave Elementen biedt een vereenvoudigde gebruikersinterface waarmee u uw digitale elementen eenvoudig kunt beheren, ontdekken en distribueren. Een brede reeks gebruikers van verschillende functies, met inbegrip van creatieve, marketing en brancheteams kunnen aan activa samenwerken en tot het recht toegang hebben, erkende activa wanneer en waar zij hen nodig hebben. Veel incidentele DAM-gebruikers geven de voorkeur aan de weergave Middelen, omdat deze alleen een subset functies bevat. De ervaring is gericht op creatieve personen, alleen-lezen klanten en minder belangrijke DAM-gebruikers.

DAM-bibliotheken, ontwikkelaars en supergebruikers kunnen de Admin-weergave blijven gebruiken of, indien nodig, schakelen tussen de gebruikersinterfaces. U kunt de ervaring selecteren die het beste voor uw rol werkt.

![add-tags](assets/newui-overview.svg)

Voor informatie over hoe u toegang kunt krijgen tot de weergave Middelen en over enkele vereenvoudigingen die deze aanbiedt via de beheerweergave, raadpleegt u [Inleiding tot de weergave Middelen](/help/assets/assets-view-introduction.md).

## Integratie met op documenten gebaseerde authoring voor Edge Delivery Services {#integrate-doc-authoring-edge-and-assets}

Met Edge Delivery kunt u snel aantrekkelijke websites maken waar auteurs inhoud snel kunnen bijwerken en publiceren en nieuwe sites snel kunnen worden gestart.

Integreer AEM Assets met op documenten gebaseerde authoring voor Edge Delivery Services zodat websiteauteurs afbeeldingen kunnen gebruiken die beschikbaar zijn in AEM Assets-opslagruimten tijdens het ontwerpen van documenten in Microsoft Word of Google Docs. Zie voor meer informatie [AEM Assets integreren met op documenten gebaseerde authoring](/help/edge/using.md#integrate-assets-edge).

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
