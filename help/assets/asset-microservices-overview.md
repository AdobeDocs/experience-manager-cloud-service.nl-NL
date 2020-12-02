---
title: Elementen verwerken met behulp van asset microservices
description: Verwerk uw digitale middelen met gebruik van cloudnative en schaalbare services voor het verwerken van bedrijfsmiddelen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: b1586cd9d6b3e9da115bff802d840a72d1207e4a
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 0%

---


# Overzicht van het opnemen en verwerken van bedrijfsmiddelen met asset microservices {#asset-microservices-overview}

Adobe Experience Manager als Cloud Service biedt een &#39;cloud-native&#39; methode om toepassingen en mogelijkheden voor Experience Managers te benutten. Een van de belangrijkste elementen van deze nieuwe architectuur is het opnemen en verwerken van bedrijfsmiddelen, aangedreven door microservices voor bedrijfsmiddelen. Asset microservices bieden een schaalbare en veerkrachtige verwerking van middelen met behulp van cloudservices. Adobe beheert de cloudservices voor een optimale afhandeling van verschillende typen bedrijfsmiddelen en verwerkingsopties. De belangrijkste voordelen van cloudnative assetmicroservices zijn:

* Schaalbare architectuur die een naadloze verwerking mogelijk maakt voor bronintensieve bewerkingen.
* Efficiënte indexering en tekstextracties die geen invloed hebben op de prestaties van uw Experience Managers.
* Minimaliseer de behoefte aan werkschema&#39;s om activa verwerking in het milieu van de Experience Manager te behandelen. Dit bevrijdt omhoog middelen, minimaliseert lading op Experience Manager, en verstrekt scalability.
* Verbeterde veerkracht van de verwerking van bedrijfsmiddelen. Mogelijke problemen bij het verwerken van atypische bestanden, zoals beschadigde bestanden of extreem grote bestanden, hebben geen gevolgen meer voor de prestaties van de implementatie.
* Vereenvoudigde configuratie van middelenverwerking voor beheerders.
* De instellingen voor middelenverwerking worden beheerd en onderhouden door Adobe om de best bekende configuratie te bieden voor de verwerking van uitvoeringen, metagegevens en tekstextractie voor verschillende bestandstypen
* Native Adobe-bestandsverwerkingsservices worden waar van toepassing gebruikt, waardoor een hoogwaardige uitvoer mogelijk wordt en [een efficiënte verwerking van door eigendomsrechten beschermde indelingen](file-format-support.md) mogelijk wordt.
* Mogelijkheid om een workflow voor naverwerking te configureren om gebruikersspecifieke acties en integratie toe te voegen.

Middelenmicroservices helpen u te voorkomen dat er van derden renderingtools en -methoden nodig zijn (zoals ImageMagick- en MPEG-transcodering) en vereenvoudigen configuraties, terwijl ze tevens functionaliteit bieden die buiten de box valt voor algemene bestandstypen.

## Architectuur op hoog niveau {#asset-microservices-architecture}

Een architectuurdiagram op hoog niveau geeft de belangrijkste elementen weer van het opnemen en verwerken van bedrijfsmiddelen en de stroom van bedrijfsmiddelen in het systeem.

<!-- Proposed DRAFT diagram for asset microservices overview - see section "Asset processing - high-level diagram" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![Inname en verwerking van bedrijfsmiddelen met ](assets/asset-microservices-overview.png "microservices voor bedrijfsmiddelenInname en verwerking van bedrijfsmiddelen met microservices voor bedrijfsmiddelen")

De belangrijkste stappen van de opname en verwerking met behulp van asset microservices zijn:

* Clients, zoals webbrowsers of Adobe Asset Link, verzenden een uploadverzoek naar de Experience Manager en beginnen het binaire bestand rechtstreeks te uploaden naar de binaire cloudopslag.
* Wanneer de directe binaire upload voltooit, brengt de cliënt Experience Manager op de hoogte.
* Experience Manager verzendt een verwerkingsverzoek naar de diensten van asset microservices. De inhoud van het verzoek is afhankelijk van de configuratie van de verwerkingsprofielen in Experience Manager die specificeert, welke vertoningen te produceren.
* De back-end van de microservices van activa ontvangt het verzoek, verzendt het naar één of meerdere microservices die op het verzoek worden gebaseerd. Elke microservice krijgt rechtstreeks vanuit de binaire cloudopslag toegang tot het oorspronkelijke binaire bestand.
* De resultaten van de verwerking, zoals uitvoeringen, worden opgeslagen in de binaire cloudopslag.
* De Experience Manager wordt op de hoogte gesteld van het feit dat de verwerking compleet is en dat er directe aanwijzers naar de gegenereerde binaire bestanden (uitvoeringen) worden gestuurd. De gegenereerde uitvoeringen zijn beschikbaar in Experience Manager voor het geüploade element.

Dit is de basisstroom van activa het opnemen en verwerken. Indien geconfigureerd, kan Experience Manager ook een aangepast workflowmodel starten voor naverwerking van het element. Voer bijvoorbeeld aangepaste stappen uit die specifiek zijn voor uw omgeving, zoals het ophalen van informatie van een bedrijfssysteem en het toevoegen van elementen aan eigenschappen.

De opname en de verwerkingsstroom zijn de belangrijkste concepten van de de dienstenarchitectuur van activa microservices voor Experience Manager.

* **Directe binaire toegang**: Elementen worden naar de Cloud Binary Store getransporteerd (en geüpload) als ze eenmaal zijn geconfigureerd voor Experience Manager-omgevingen, en vervolgens AEM, asset microservices, en ten slotte krijgen klanten directe toegang tot deze services om hun werk uit te voeren. Dit minimaliseert de lading op netwerken en duplicatie van opgeslagen binaire bestanden
* **Externe verwerking**: De verwerking van middelen vindt plaats buiten AEM omgeving en bespaart de bronnen (CPU, geheugen) voor het bieden van essentiële functies voor het beheer van digitale middelen en het ondersteunen van interactief werk met het systeem voor eindgebruikers

## Middelen uploaden met directe binaire toegang {#asset-upload-with-direct-binary-access}

De cliënten van de Experience Manager, die een deel van product aanbieden, allen steunen uploadt met directe binaire toegang door gebrek. Dit zijn onder andere uploaden via de webinterface, Adobe Asset Link en AEM bureaubladtoepassing.

U kunt aangepaste uploadgereedschappen gebruiken die rechtstreeks werken met AEM HTTP-API&#39;s. U kunt deze APIs direct gebruiken, of de volgende open-bronprojecten gebruiken en uitbreiden die het uploadprotocol uitvoeren:

* [Uploadbibliotheek met open bron](https://github.com/adobe/aem-upload)
* [Opensource opdrachtregelprogramma](https://github.com/adobe/aio-cli-plugin-aem)

Zie [Elementen uploaden](add-assets.md) voor meer informatie.

## Aangepast element nabewerken {#add-custom-asset-post-processing} toevoegen

Terwijl de meeste klanten al hun behoeften van de activaverwerking van de configureerbare activa microservices zouden moeten krijgen, zouden sommige extra activa kunnen vereisen verwerkend. Dit geldt met name wanneer activa moeten worden verwerkt op basis van informatie die via integratie van andere systemen afkomstig is. In dergelijke gevallen kunnen aangepaste nabewerkingsworkflows worden gebruikt.

Nabewerkingsworkflows zijn gewone AEM workflowmodellen die zijn gemaakt en beheerd in AEM Workfloweditor. Klanten kunnen de workflows configureren om aanvullende verwerkingsstappen uit te voeren op een middel, waaronder het gebruik van beschikbare workflowstappen buiten de box en aangepaste workflows.

Adobe Experience Manager kan zo worden geconfigureerd dat de naverwerkingsworkflows automatisch worden geactiveerd nadat de verwerking van de middelen is voltooid.

<!-- TBD asgupta, Engg: Create some asset-microservices-data-flow-diagram.
-->

>[!MORELIKETHIS]
>
>* [Aan de slag met microservices voor assets](asset-microservices-configure-and-use.md)
>* [Ondersteunde bestandsindelingen](file-format-support.md)
>* [Adobe-itemkoppeling](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [[!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)
>* [Apache Oak-documentatie over directe binaire toegang](https://jackrabbit.apache.org/oak/docs/features/direct-binary-access.html)

