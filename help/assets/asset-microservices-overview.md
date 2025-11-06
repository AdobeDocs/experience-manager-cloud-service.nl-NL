---
title: Elementen verwerken met behulp van asset-microservices
description: Verwerk uw digitale middelen met gebruik van cloudnative en schaalbare services voor het verwerken van bedrijfsmiddelen.
contentOwner: AG
feature: Asset Compute Microservices, Asset Ingestion, Asset Processing
role: Developer, Admin
exl-id: 1e069b95-a018-40ec-be01-9a74ed883b77
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# Overzicht van het opnemen en verwerken van bedrijfsmiddelen met asset microservices {#asset-microservices-overview}

Adobe Experience Manager als [!DNL Cloud Service] biedt een methode in de cloud om Experience Manager-toepassingen en -mogelijkheden te gebruiken. Een van de belangrijkste elementen van deze nieuwe architectuur is het opnemen en verwerken van bedrijfsmiddelen, aangedreven door microservices voor bedrijfsmiddelen. Asset microservices bieden een schaalbare en veerkrachtige verwerking van middelen met behulp van cloudservices. Adobe beheert de cloudservices voor een optimale afhandeling van verschillende typen bedrijfsmiddelen en verwerkingsopties. De belangrijkste voordelen van cloudnative assetmicroservices zijn:

* Schaalbare architectuur die een naadloze verwerking mogelijk maakt voor bronintensieve bewerkingen.
* Efficiënte indexering en tekstextracties die de prestaties van uw Experience Manager-omgevingen niet beïnvloeden.
* Minimaliseer de behoefte aan werkschema&#39;s om activa verwerking in het milieu van Experience Manager te behandelen. Hierdoor worden bronnen vrijgemaakt, wordt de belasting op Experience Manager tot een minimum beperkt en is schaalbaarheid mogelijk.
* Verbeterde veerkracht van de verwerking van bedrijfsmiddelen. Mogelijke problemen bij het verwerken van atypische bestanden, zoals beschadigde bestanden of extreem grote bestanden, hebben geen gevolgen meer voor de prestaties van de implementatie.
* Vereenvoudigde configuratie van middelenverwerking voor beheerders.
* Assets-verwerkingsinstellingen worden beheerd en onderhouden door Adobe om de best bekende configuratie te bieden voor de verwerking van uitvoeringen, metagegevens en tekstextractie voor verschillende bestandstypen
* De inheemse diensten van de het dossierverwerking van Adobe worden gebruikt waar toepasselijk, die high-fidelity output en [&#x200B; efficiënte behandeling van merkgebonden formaten van Adobe verstrekken &#x200B;](file-format-support.md).
* Mogelijkheid om een workflow voor naverwerking te configureren om gebruikersspecifieke acties en integratie toe te voegen.

Met Asset microservices voorkomt u de behoefte aan renderingtools en -methoden van derden (zoals [!DNL ImageMagick] en MPEG-transcodering) en vereenvoudigt u configuraties, terwijl u standaard basisfunctionaliteit voor de algemene bestandsindelingen biedt.

## Architectuur op hoog niveau {#asset-microservices-architecture}

Een architectuurdiagram op hoog niveau geeft de belangrijkste elementen weer van het opnemen en verwerken van bedrijfsmiddelen en de stroom van bedrijfsmiddelen in het systeem.

<!-- Proposed DRAFT diagram for asset microservices overview - see section "Asset processing - high-level diagram" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![&#x200B; Inname van activa en verwerking met activa microservices &#x200B;](assets/asset-microservices-overview.png " Inname van Activa en verwerking met activa microservices ")

De belangrijkste stappen van de opname en verwerking met behulp van asset microservices zijn:

* Clients, zoals webbrowsers of Adobe Asset Link, verzenden een uploadverzoek naar [!DNL Experience Manager] en beginnen het binaire bestand rechtstreeks te uploaden naar de binaire cloudopslag.
* Wanneer het directe binaire uploaden is voltooid, brengt de client [!DNL Experience Manager] op de hoogte.
* [!DNL Experience Manager] verzendt een verwerkingsverzoek naar de services van asset microservices. De inhoud van de aanvraag is afhankelijk van de configuratie van de verwerkingsprofielen in [!DNL Experience Manager] die aangeven welke uitvoeringen moeten worden gegenereerd.
* Asset microservices back-end ontvangt de aanvraag en verzendt deze naar een of meer microservices op basis van de aanvraag. Elke microservice krijgt rechtstreeks vanuit de binaire cloudopslag toegang tot het oorspronkelijke binaire bestand.
* De resultaten van de verwerking, zoals uitvoeringen, worden opgeslagen in de binaire cloudopslag.
* Experience Manager wordt op de hoogte gesteld van het feit dat de verwerking voltooid is en dat er directe aanwijzers naar de gegenereerde binaire bestanden (uitvoeringen) worden gestuurd. De gegenereerde uitvoeringen zijn beschikbaar in [!DNL Experience Manager] voor het geüploade element.

Dit is de basisstroom van activa het opnemen en verwerken. Indien dit is geconfigureerd, kan Experience Manager ook een aangepast workflowmodel starten voor naverwerking van het middel. Voer bijvoorbeeld aangepaste stappen uit die specifiek zijn voor uw omgeving, zoals het ophalen van informatie van een bedrijfssysteem en het toevoegen van elementen aan eigenschappen.

De opname- en verwerkingsstroom zijn de belangrijkste concepten van de architectuur voor assetmicroservices voor Experience Manager.

* **Directe binaire toegang**: Assets wordt vervoerd (en geupload) aan de Binaire Opslag van de Wolk zodra gevormd voor de milieu&#39;s van Experience Manager, en dan [!DNL Experience Manager], activa microservices, en tenslotte krijgen de cliënten directe toegang tot hen om hun werk uit te voeren. Dit minimaliseert de lading op netwerken en duplicatie van opgeslagen binaire bestanden
* **Buiten het milieu van** wordt de Extern verwerkte verwerking: De verwerking van activa wordt gedaan, en bespaart zijn middelen (CPU, geheugen) voor het verstrekken van zeer belangrijke functionaliteit van het Beheer van Digitale Activa (DAM) en het steunen van interactief werk met het systeem voor eind - gebruikers[!DNL Experience Manager]

## Middelen uploaden met directe binaire toegang {#asset-upload-with-direct-binary-access}

Experience Manager-clients, die onderdeel zijn van productaanbiedingen, bieden standaard standaard standaard ondersteuning voor uploaden met directe binaire toegang. Dit zijn onder andere uploaden via de webinterface, Adobe Asset Link en de bureaubladtoepassing [!DNL Experience Manager] .

U kunt aangepaste uploadgereedschappen gebruiken die rechtstreeks werken met [!DNL Experience Manager] HTTP-API&#39;s. U kunt deze APIs direct gebruiken, of de volgende open-bronprojecten gebruiken en uitbreiden die het uploadprotocol uitvoeren:

* [&#x200B; open-bron uploadt bibliotheek &#x200B;](https://github.com/adobe/aem-upload)
* [&#x200B; open-bron bevel-lijn hulpmiddel &#x200B;](https://github.com/adobe/aio-cli-plugin-aem)

Voor meer informatie, zie [&#x200B; activa &#x200B;](add-assets.md) uploaden.

## Aangepaste naverwerking van elementen toevoegen {#add-custom-asset-post-processing}

Terwijl de meeste klanten al hun behoeften van de activaverwerking van de configureerbare activa microservices zouden moeten krijgen, zouden sommige extra activa kunnen vereisen verwerkend. Dit geldt met name wanneer activa moeten worden verwerkt op basis van informatie die via integratie van andere systemen afkomstig is. In dergelijke gevallen kunnen aangepaste nabewerkingsworkflows worden gebruikt.

Nabewerkingsworkflows zijn gewone [!DNL Experience Manager] workflowmodellen die zijn gemaakt en beheerd in de [!DNL Experience Manager] Workflow-editor. Klanten kunnen de workflows configureren om aanvullende verwerkingsstappen uit te voeren op een middel, waaronder het gebruik van beschikbare workflowstappen buiten de box en aangepaste workflows.

Adobe Experience Manager kan zo worden geconfigureerd dat de naverwerkingsworkflows automatisch worden geactiveerd nadat de verwerking van de middelen is voltooid.

<!-- TBD asgupta, Engg: Create some asset-microservices-data-flow-diagram.
-->

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
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Aan de slag met microservices voor assets](asset-microservices-configure-and-use.md)
>* [Ondersteunde bestandsindelingen](file-format-support.md)
>* [&#x200B; de Verbinding van Activa van Adobe &#x200B;](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [[!DNL Experience Manager]  Desktop app &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)
>* [&#x200B; Apache Oak documentatie op directe binaire toegang &#x200B;](https://jackrabbit.apache.org/oak/docs/features/direct-binary-access.html)
