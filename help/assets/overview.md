---
title: DAM (Digital Asset Management) van de Adobe met AEM
description: Krijg inzicht in het gebruik en beheer van Adobe Digital Asset Management (DAM) met Experience Manager Assets as a Cloud Service.
contentOwner: AK
feature: Asset Management
role: User, Leader, Architect
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 2%

---


# Introductie van Assets als [!DNL Cloud Service] voor Digital Asset Management in AEM {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Adobe Experience Manager Assets als [!DNL Cloud Service] biedt een native PaaS-oplossing in de cloud waarmee bedrijven niet alleen hun activiteiten op het gebied van Digital Asset Management en Dynamic Media met snelheid en impact kunnen uitvoeren, maar ook intelligente mogelijkheden van de volgende generatie, zoals AI/ML, kunnen gebruiken vanuit een systeem dat altijd actueel, altijd beschikbaar en altijd leerzaam is.

Gelijktijdige inname van vele activa of complexe activa is middel-intensieve taak voor een instantie van de Auteur van de Experience Manager. De primaire instantie verbruikt aanzienlijke CPU-, geheugen- en I/O-bronnen wanneer middelen worden toegevoegd, verwerkt of zelfs gemigreerd. Dergelijke prestatieproblemen zijn van invloed op het ontwerpen en bladeren door eindgebruikers.

Bedrijven hebben ondersteuning nodig voor een groot aantal verschillende bestandsindelingen en inhoudsresoluties voor meervoudige apparaten, transgeografische situaties en meertalige gebruiksgevallen. Voor de verwerking en opslag van bedrijfsmiddelen zijn middelen en mogelijkheden nodig die een traditionele oplossing kunnen overbelasten. Soms leveren technische beperkingen van de verwerking van activa niet de gewenste resultaten op en op andere tijdstippen vormen de opslagkosten een belemmering voor winstmarges.

Om met te beginnen, begrijp de [ voordelen van een wolk-inheemse aanbieding ](#solution-benefits) voor het Beheer van Digitale Activa. Controle uit de opmerkelijke [ veranderingen in Experience Manager als a  [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md) die ook Experience Manager Assets beïnvloeden volgde de opmerkelijke [ veranderingen in Assets ](/help/assets/assets-cloud-changes.md).

Lees op om de [ details van de nieuwe mogelijkheden van Assets ](#whats-new-assets) en de [ bekende kwesties ](/help/release-notes/maintenance/latest.md) te kennen. Zie een lijst van [ afgekeurde of verwijderde functionaliteit ](/help/release-notes/deprecated-removed-features.md) om te weten wat in deze versie wordt verwijderd. Tot slot begrijp de termijnen van de Experience Manager met de hulp van deze [ verklarende woordenlijst ](/help/overview/terminology.md).

## Oplossingsvoordelen {#solution-benefits}

Hieronder ziet u de belangrijkste voordelen van Assets als [!DNL Cloud Service] voor Digital Asset Management. Meer weten, zie [ overzicht van Experience Manager als a  [!DNL Cloud Service]](/help/overview/introduction.md).

* **Moderne wolkendiensten voor activa verwerking**: De nieuwe activa microdiensten zijn de op wolk-gebaseerde, scalable, betrouwbare, en probleemloze dienst van de activaverwerking.
* **hoogst scalable**: Elastische scalability over alle soorten plaatsingen. Praktisch onbeperkte middelen die op bestelling, zoals en wanneer nodig beschikbaar zijn. Bespart de kosten van overontwerp in vergelijking met een traditioneel systeem.
* **Meest recente software**: Altijd huidig en altijd bijgewerkt. Alle gebruikers beschikken alleen over de nieuwste software met alle patches, functies, beveiliging en oplossingen voor problemen die voor hen beschikbaar zijn. Ontwikkelaars en integrators werken met de nieuwste set API&#39;s zonder ondersteuning voor meerdere versies.
* **altijd online**: Nul onderbreking (0dt), dankzij de instantie die in een cluster met steunen en overtolligheid wordt opgesteld. Upgrades zijn ook 0dt.
* **Constante controle**: De controle van het systeem is geautomatiseerde en ingebouwde controles en trekkers helpen de prestaties, de beschikbaarheid, en algemene robuustheid handhaven.
* **Hassle-vrije plaatsingen**: De Experience Manager in de verrichtingen van de Wolk wordt volledig geautomatiseerd die geen handinterventie vereisen. Voor geautomatiseerde implementaties automatiseert de Cloud Manager-component (CM) de opbouw van implementeerbare Docker-afbeeldingen die uw aangepaste code bevatten.

## Beschikbare persoonlijke ervaringen voor Digital Asset Management {#persona-based-experiences}

Adobe biedt robuuste DAM-oplossingen (Digital Asset Management) waarmee u optimaal kunt profiteren van uw digitale middelen. Adobe Experience Manager Assets heeft twee aparte ervaringen die dezelfde gegevensopslagruimte voor Cloud Servicen gebruiken:

* **Mening Admin**: Het bestaande as a Cloud Service gebruikersinterface van Assets. Gebruik de beheerweergave voor alle geavanceerde mogelijkheden voor beheer van digitale bedrijfsmiddelen, zoals integratie, workflows, automatisering van inhoud, publicatie en meer.

* **Mening van Assets**: De lichte ervaring van het activabeheer van de Adobe om, digitale activa op te slaan te beheren, te ontdekken en te gebruiken. Gestroomlijnde gebruikersinterface met essentiële mogelijkheden voor beheer van digitale bedrijfsmiddelen. Ontworpen voor de lichtgewicht DAM-gebruikers met focus op uploaden, metagegevensbeheer, zoeken, downloaden en delen.

Gebruikers met toegang tot de beheerweergave hebben ook toegang tot de Assets-weergave. Assets View biedt een vereenvoudigde gebruikersinterface waarmee u uw digitale middelen eenvoudig kunt beheren, ontdekken en distribueren. Een brede reeks gebruikers van verschillende functies, met inbegrip van creatieve, marketing en brancheteams kunnen aan activa samenwerken en tot het recht toegang hebben, erkende activa wanneer en waar zij hen nodig hebben. Veel gebruikers van DAM geven de voorkeur aan de Assets-weergave omdat deze alleen een subset functies bevat. De ervaring is gericht op creatieve personen, alleen-lezen klanten en minder belangrijke DAM-gebruikers.

DAM-bibliotheken, ontwikkelaars en supergebruikers kunnen de Admin-weergave blijven gebruiken of, indien nodig, schakelen tussen de gebruikersinterfaces. U kunt de ervaring selecteren die het beste voor uw rol werkt.

![ toe:voegen-markeringen ](assets/newui-overview.svg)

Voor informatie over hoe te om tot de mening van Assets en sommige vereenvoudigingen toegang te hebben die het over mening Admin aanbiedt, zie [ Inleiding aan de mening van Assets ](/help/assets/assets-view-introduction.md).

## Integratie met op documenten gebaseerde authoring voor Edge Delivery Services {#integrate-doc-authoring-edge-and-assets}

Met Edge Delivery kunt u snel aantrekkelijke websites maken waar auteurs inhoud snel kunnen bijwerken en publiceren en nieuwe sites snel kunnen worden gestart.

Integreer AEM Assets met Document-based Authoring voor Edge Delivery Services zodat websiteauteurs afbeeldingen kunnen gebruiken die beschikbaar zijn in AEM Assets repositories tijdens het ontwerpen van documenten in Microsoft Word of Google Docs. Voor meer informatie, zie [ AEM Assets met op document-Gebaseerde Authoring ](/help/edge/using.md#integrate-assets-edge) integreren.

## Integratie met Adobe Journey Optimizer {#integration-with-ajo}

[ Adobe Journey Optimizer ](https://business.adobe.com/products/journey-optimizer/adobe-journey-optimizer.html) vereenvoudigt reisbeheer voor klanten om omnichannel campagnes van intelligente besluitvorming en inzichten te voorzien. Bij het ontwerpen van berichten met Journey Optimizer hebt u rechtstreeks vanuit de Journey Optimizer-interface toegang tot de as a Cloud Service gegevensopslagruimte van Assets. Gebruikers krijgen toegang tot elementen via de ingesloten gebruikersinterface van Experience Manager Assets. Voor meer informatie, zie [ activa met Experience Manager Assets ](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/assets-images/assets.html) creëren en beheren.

## Nieuwe Assets-mogelijkheden {#whats-new-assets}

De belangrijkste nieuwe mogelijkheden zijn:

* [Asset-microservices](/help/assets/asset-microservices-overview.md)
* [Methoden voor het uploaden van middelen](/help/assets/add-assets.md)

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Publish Assets naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
