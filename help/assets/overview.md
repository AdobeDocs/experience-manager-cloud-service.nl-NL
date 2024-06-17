---
title: DAM (Digital Asset Management) van de Adobe met AEM
description: Krijg inzicht in het gebruik en beheer van Adobe Digital Asset Management (DAM) met Experience Manager Assets as a Cloud Service.
contentOwner: AK
feature: Asset Management
role: User, Leader, Architect
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 2%

---


# Elementen introduceren als een [!DNL Cloud Service] voor Digital Asset Management in AEM {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

Adobe Experience Manager Assets als [!DNL Cloud Service] biedt een cloud-native, PaaS-oplossing voor bedrijven om niet alleen hun Digital Asset Management- en Dynamic Media-bewerkingen met snelheid en impact uit te voeren, maar ook intelligente mogelijkheden van de volgende generatie, zoals AI/ML, te gebruiken vanuit een systeem dat altijd actueel, altijd beschikbaar en altijd leerend is.

Gelijktijdige inname van vele activa of complexe activa is middel-intensieve taak voor een instantie van de Auteur van de Experience Manager. De primaire instantie verbruikt aanzienlijke CPU-, geheugen- en I/O-bronnen wanneer middelen worden toegevoegd, verwerkt of zelfs gemigreerd. Dergelijke prestatieproblemen zijn van invloed op het ontwerpen en bladeren door eindgebruikers.

Bedrijven hebben ondersteuning nodig voor een groot aantal verschillende bestandsindelingen en inhoudsresoluties voor meervoudige apparaten, transgeografische situaties en meertalige gebruiksgevallen. Voor de verwerking en opslag van bedrijfsmiddelen zijn middelen en mogelijkheden nodig die een traditionele oplossing kunnen overbelasten. Soms leveren technische beperkingen van de verwerking van activa niet de gewenste resultaten op en op andere tijdstippen vormen de opslagkosten een belemmering voor winstmarges.

Om te beginnen, begrijp [voordelen van een cloudeigen aanbod](#solution-benefits) voor Digital Asset Management. Uitchecken wat er in de tabel staat [wijzigingen in Experience Manager als een [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md) die ook gevolgen had voor Experience Manager Assets, gevolgd door de opmerkelijke [wijzigingen in elementen](/help/assets/assets-cloud-changes.md).

Lees verder om de [details van de nieuwe middelenmogelijkheden](#whats-new-assets) en de [bekende problemen](/help/release-notes/maintenance/latest.md). Zie een lijst met [vervangen of verwijderde functionaliteit](/help/release-notes/deprecated-removed-features.md) om te weten wat er is verwijderd uit deze release. Tot slot, begrijp de termen van de Experience Manager met behulp van dit [woordenlijst](/help/overview/terminology.md).

## Oplossingsvoordelen {#solution-benefits}

Hieronder worden de belangrijkste voordelen van activa als [!DNL Cloud Service] voor Digital Asset Management. Zie voor meer informatie [overzicht van de Experience Manager als een [!DNL Cloud Service]](/help/overview/introduction.md).

* **Moderne cloudservices voor middelenverwerking**: De nieuwe assetmicroservices zijn een cloudgebaseerde, schaalbare, betrouwbare en probleemloze service voor de verwerking van bedrijfsmiddelen.
* **Zeer schaalbaar**: Elastische schaalbaarheid voor alle typen implementaties. Praktisch onbeperkte middelen die op bestelling, zoals en wanneer nodig beschikbaar zijn. Bespart de kosten van overontwerp in vergelijking met een traditioneel systeem.
* **Nieuwste software**: Altijd bijgewerkt en bijgewerkt. Alle gebruikers beschikken alleen over de nieuwste software met alle patches, functies, beveiliging en oplossingen voor problemen die voor hen beschikbaar zijn. Ontwikkelaars en integrators werken met de nieuwste set API&#39;s zonder ondersteuning voor meerdere versies.
* **Altijd online**: Geen downtime (0dt), dankzij de instantie die is geïmplementeerd in een cluster met back-ups en redundantie. Upgrades zijn ook 0dt.
* **Constante bewaking**: De controle van het systeem wordt geautomatiseerd en ingebouwde controles en trekkers helpen de prestaties, de beschikbaarheid, en algemene robuustheid handhaven.
* **Hapeloze implementaties**: Experience Manager in de Cloud-bewerkingen wordt volledig geautomatiseerd en hoeft niet handmatig te worden uitgevoerd. Voor geautomatiseerde implementaties automatiseert de component Cloud Manager (CM) de opbouw van implementeerbare Docker-afbeeldingen die uw aangepaste code bevatten.

## Beschikbare persoonlijke ervaringen voor Digital Asset Management {#persona-based-experiences}

Adobe biedt robuuste DAM-oplossingen (Digital Asset Management) waarmee u optimaal kunt profiteren van uw digitale middelen. Adobe Experience Manager Assets heeft twee aparte ervaringen die dezelfde gegevensopslagruimte voor Cloud Servicen gebruiken:

* **Admin View**: De as a Cloud Service gebruikersinterface voor bestaande elementen. Gebruik de beheerweergave voor alle geavanceerde mogelijkheden voor beheer van digitale bedrijfsmiddelen, zoals integratie, workflows, automatisering van inhoud, publicatie en meer.

* **Weergave Elementen**: De lichte ervaring van de Adobe op het gebied van middelenbeheer voor het opslaan, beheren, ontdekken en gebruiken van digitale middelen. Gestroomlijnde gebruikersinterface met essentiële mogelijkheden voor beheer van digitale bedrijfsmiddelen. Ontworpen voor de lichtgewicht DAM-gebruikers met focus op uploaden, metagegevensbeheer, zoeken, downloaden en delen.

Gebruikers met toegang tot de beheerweergave hebben ook toegang tot de weergave Middelen. De weergave Elementen biedt een vereenvoudigde gebruikersinterface waarmee u uw digitale elementen eenvoudig kunt beheren, ontdekken en distribueren. Een brede reeks gebruikers van verschillende functies, met inbegrip van creatieve, marketing en brancheteams kunnen aan activa samenwerken en tot het recht toegang hebben, erkende activa wanneer en waar zij hen nodig hebben. Veel incidentele DAM-gebruikers geven de voorkeur aan de weergave Middelen, omdat deze alleen een subset functies bevat. De ervaring is gericht op creatieve personen, alleen-lezen klanten en minder belangrijke DAM-gebruikers.

DAM-bibliotheken, ontwikkelaars en supergebruikers kunnen de Admin-weergave blijven gebruiken of, indien nodig, schakelen tussen de gebruikersinterfaces. U kunt de ervaring selecteren die het beste voor uw rol werkt.

![add-tags](assets/newui-overview.svg)

Voor informatie over hoe u toegang kunt krijgen tot de weergave Middelen en over enkele vereenvoudigingen die deze aanbiedt via de beheerweergave, raadpleegt u [Inleiding tot de weergave Middelen](/help/assets/assets-view-introduction.md).

## Integratie met op documenten gebaseerde authoring voor Edge Delivery Services {#integrate-doc-authoring-edge-and-assets}

Met Edge Delivery kunt u snel aantrekkelijke websites maken waar auteurs inhoud snel kunnen bijwerken en publiceren en nieuwe sites snel kunnen worden gestart.

Integreer AEM Assets met Document-based Authoring voor Edge Delivery Services zodat websiteauteurs afbeeldingen kunnen gebruiken die beschikbaar zijn in AEM Assets repositories tijdens het ontwerpen van documenten in Microsoft Word of Google Docs. Zie voor meer informatie [AEM Assets integreren met op documenten gebaseerde authoring](/help/edge/using.md#integrate-assets-edge).

## Integratie met Adobe Journey Optimizer {#integration-with-ajo}

[Adobe Journey Optimizer](https://business.adobe.com/products/journey-optimizer/adobe-journey-optimizer.html) vereenvoudigt het reisbeheer voor klanten om omnichannel campagnes van intelligente besluitvorming en inzichten te voorzien. Wanneer u berichten ontwerpt met Journey Optimizer, hebt u rechtstreeks vanuit de Journey Optimizer-interface toegang tot de as a Cloud Service gegevensopslagruimte voor middelen. Gebruikers krijgen toegang tot elementen via de ingesloten gebruikersinterface van Experience Manager Assets. Zie voor meer informatie [Elementen maken en beheren met Experience Manager Assets](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/assets-images/assets.html).

## Nieuwe middelenmogelijkheden {#whats-new-assets}

De belangrijkste nieuwe mogelijkheden zijn:

* [Asset-microservices](/help/assets/asset-microservices-overview.md)
* [Methoden voor het uploaden van middelen](/help/assets/add-assets.md)

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Middelen publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
