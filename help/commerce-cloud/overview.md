---
title: Inleiding tot AEM Handel als Cloud Service
description: Nieuwe functies in AEM Handel als Cloud Service.
translation-type: tm+mt
source-git-commit: c5694cf8651cf8ba5331c730fa1b1180310dd35a
workflow-type: tm+mt
source-wordcount: '1331'
ht-degree: 0%

---


# Introducing AEM Commerce as a Cloud Service {#commerce-intro}

De Handel van de Experience Manager als Cloud Service bestaat uit het Kader van de Integratie van de Handel (CIF), dat Adobe aanbevolen patroon is om de handelsdiensten en andere derde handelsoplossingen met de Experience Cloud te integreren en uit te breiden. Hierdoor kunnen Adobe-klanten buitengewone en gepersonaliseerde omnichannel-shopping-ervaring bieden op basis van geavanceerde technologie.

Het kader van de Integratie van de Handel is een add-on module voor Experience Manager als Cloud Service en verstrekt een reeks auteursinstrumenten, componenten, en een verwijzingsopslag om de ontwikkeling van integratie tussen Experience Manager als Cloud Service en handelsoplossingen te versnellen.

## CIF-uitkeringen {#cif-benefits}

De belangrijkste voordelen zijn:

* De integratie is een abstractielaag om integratie met veelvoudige systemen te standaardiseren en in te kapselen.

* CIF steunt hoofdloze/omnichannel ervaringen:

   * Toepassingen met één pagina en toepassingen met meerdere pagina&#39;s
   * GraphQL-eindpunten

* CIF verstrekt serverless, op microservice-gebaseerde proces en bedrijfslogische laag voor aanpassing en uitbreiding van de handelsdiensten.

* CIF verstrekt out-of-the-box integratie met oplossingen van Adobe zoals AEM en Magento

## CIF-elementen {#cif-elements}

![CIF-elementen](/help/commerce-cloud/assets/cif-overview1.jpg)


### CIF-invoegtoepassing voor ontwerpgereedschappen {#add-on-authoring-tools}

CIF toe:voegen-On verleent toegang tot handel auteursgereedschap zoals de Console van het Product, Product &amp; de Bestellers van de Categorie of productonderzoek voor auteurs om hen toe te staan om rijke ervaringen met marketing en handelsinhoud tot stand te brengen. Invoegtoepassing beheert ook de achterste verbinding aan Magento (of alternatief handelsysteem) via GraphQL. Zodra toe:voegen-op wordt voorzien wordt het opgesteld op AEM als milieu&#39;s van de Cloud Service automatisch.

### AEM CIF Core-componenten {#aem-cif-core}

De AEM CIF Core-componenten zijn aan de serverzijde en client-side gerenderde componenten met ondersteuning voor Magento GraphQL. Ze worden gebruikt om statische, cacheable en SEO-vriendelijke handelsopslagproducten te maken op basis van AEM technologieën.

De basiscomponenten worden verstrekt, gemeenschappelijk over handelsimplementaties zoals het Detail van het Product, de Lijst van het Product, Navigatie, Onderzoek, enz. Ze kunnen ongewijzigd worden gebruikt of worden uitgebreid.

De [AEM CIF de Componenten](https://github.com/adobe/aem-core-cif-components) van de Kern van de [AEM Sites werken als de Componenten](https://github.com/adobe/aem-core-wcm-components) van de Kern maar zijn gewijd aan handel specifieke gebruik-gevallen.

De belangrijkste voordelen van deze componenten zijn:

* Ze zijn eenvoudig te gebruiken in uw projecten.
* Ze kunnen ongewijzigd of met zeer minimale wijzigingen worden gebruikt.
* Deze API&#39;s bieden de beste werkwijzen voor het maken van verbinding met Magento via GraphQL API&#39;s of REST API&#39;s

Componenten zoals Product Teaser en Product Carousel worden geleverd om AEM Author in staat te stellen ervaringspagina&#39;s in AEM te maken, waarbij marketinginhoud en commerciële inhoud worden gecombineerd. Deze componenten kunnen gemakkelijk worden gesleept en op een inhoudspagina worden gelaten vallen die in AEM wordt gecreeerd en met specifieke producten of categorieën verbonden gebruikend de Hulpmiddelen van de Authoring CIF zoals het Product of de Plukker van de Categorie in Cloud Service wordt gecreeerd.

Alle componenten zijn open-sourced op [GitHub](https://github.com/adobe/aem-core-cif-components). Dit toont volledige transparantie over veranderingen die in de toekomst worden aangebracht en staat u toe om de recentste versie zeer gemakkelijk te krijgen. U kunt ook aantrekverzoeken voor verbeteringen en foutoplossingen opgeven die kunnen worden opgenomen.

### AEM Venia Storefront {#aem-venia-storefront}

De [AEM Venia Storefront](https://github.com/adobe/aem-cif-guides-venia) is een moderne, productiegerichte referentie-winkel die een elementaire B2C-handelsreis laat zien. Het kan worden gebruikt om handelsprojecten te versnellen en projecten te versnellen gebruikend AEM, CIF, en Magento. Het toont beste praktijken voor het integreren van AEM en Magento en toont hoe te om de [AEM componenten](https://github.com/adobe/aem-core-cif-components) van de Kern van CIF en de Componenten [van de](https://github.com/adobe/aem-core-wcm-components) AEM Siteste gebruiken en de eindpunten van GraphQL van de Handel van Adobe te steunen. Het voorziet ook pre-sales van een verwijzingsplaats om de integratie tussen AEM en Magento aan te tonen.

De AEM Venia Storefront is een toepassing van gemengde pagina&#39;s waarin AEM het glas en de Magento bezit op een volkomen ongeëvenaarde manier de handelsnedes steunt. Zowel rendering aan de serverzijde als renderen aan de clientzijde worden in de storefront gebruikt. Rendering aan de serverzijde wordt gebruikt om statische inhoud te leveren en renderen aan de clientzijde wordt gebruikt om dynamische inhoud te leveren.

De pagina&#39;s van het product en van de catalogus zijn vrij statisch en worden teruggegeven server-kant gebruikend AEM de Componenten van de Kern van CIF zoals het Detail van het Product en de Lijst van het Product op generische malplaatjes die in AEM worden gecreeerd. Deze componenten krijgen gegevens van Magento via GraphQL APIs.
Deze pagina&#39;s worden dynamisch gemaakt, op de server weergegeven, in het cachegeheugen opgeslagen op de AEM dispatcher en vervolgens aan de browser geleverd.
Voor meer dynamische kenmerken, zoals voorraad of prijs, worden daarentegen componenten aan de clientzijde gebruikt. Client-side componenten of de componenten van het Web halen gegevens direct van Magento via GraphQL APIs en de inhoud wordt dan teruggegeven op browser.

#### Afhandeling {#checkout}

Deze verwijzingswinkel gebruikt de client-side component van de Kart die het het winkelwagentje en de controlevorm teruggeeft om een volledig ervaringsintegratiepatroon aan te tonen waar u commerciële ervaringen met Magento kunt leveren die op een volledig onopvallende manier lopen en AEM het glas bezit. Aanbevolen wordt gebruik te maken van de geleverde, geabstraheerde betalingsmethoden. Dit zet de browser cliënt in directe communicatie met de leverancier van de betaalgateway zodat noch Adobe noch de wolken van de Magento PCI gevoelige gegevens houden of overgaan.

#### Accountbeheer {#account-management}

Het beheer van de rekening wordt behandeld door Magento en de verwijzingsopslag gebruikt cliënt-kant React-gebaseerde componenten om AEM toe te laten om de ervaring voor de volgende functionaliteit terug te geven: Account maken, aanmelden en wachtwoord vergeten.

Het project van AEM Venia Storefront is een open bron en voor meer informatie, zie [AEM Venia Storefront](https://github.com/adobe/aem-cif-guides-venia).

### Projectarchetype AEM {#aem-project-archtype}

Het [AEM Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html) van het Project kan worden gebruikt om tot een minimaal, op best-praktijken-gebaseerd project van de Adobe Experience Manager als uitgangspunt voor uw eigen AEM projecten te leiden. Optioneel kunnen [AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components) worden opgenomen in een nieuw gegenereerd project.

### CIF-uitbreidingslaag {#cif-extension}

De CIF uitbreidingslaag is een middenlaag om complexe bedrijfslogica te ontvangen. Het runt het Adobe I/O Runtime-platform dat op het serverloze platform Adobe is. Het staat u toe om de dienstvraag van begin tot eind uit te breiden door zaken en proceslogica op een microserviceniveau te injecteren. De bedrijfslogica zou bijvoorbeeld plaats en kanaal moeten gebruiken om een inventarisstrategie te bepalen. De logica van het proces zou bijvoorbeeld zijn om gepersonaliseerde informatie terug te winnen.

### CIF-integratielaag {#cif-integration-layer}

De de integratielaag van CIF wordt gebruikt om integratie met andere handelsoplossingen te standaardiseren. Het stelt het platform van Adobe I/O Runtime in werking dat Adobe op het serverloze platform is en toelaat op een microserviceniveau door derde in kaart te brengen APIs tegen Adobe Handel APIs. Om u te helpen aan de bouw van derdeintegratie met AEM beginnen, hebben wij een [verwijzingsimplementatie](https://github.com/adobe/commerce-cif-graphql-integration-reference) gecreeerd om aan te tonen hoe een niet-Magento handelsafstand via de Handel APIs van de Adobe (Magento GraphQL APIs) kan worden geïntegreerd.

## Integratiepatronen AEM handel {#aem-commerce-integration}

Enkele algemeen uitgevoerde AEM de integratiepatronen van de Handel worden hieronder getoond.

![AEM CIF-integratiepatronen](/help/commerce-cloud/assets/aem-cif-integration-patterns-updated.JPG)


### Integratiepatroon 1 {#integration-pattern-one}

Dit is ons aanbevolen integratiepatroon waarbij AEM eigenaar is van het volledige glas en handelsdiensten integreert via Adobe Commerce GraphQL API&#39;s. Dit patroon ontgrendelt AEM volledige flexibiliteit om geavanceerde mediasiteontwerpen op verschillende apparaten aan te passen. Dit integratiepatroon wordt door CIF ondersteund als een out-of-the-box oplossing.


### Integratiepatroon 2 {#integration-pattern-two}

Dit patroon toont een volledig ongekende manier om inhoud en handel te leveren. De levering is volledig clientzijde. In dit patroon wordt inhoud geleverd via API en de gegevens van de Handel van HTML worden geleverd via GraphQL. Dit patroon wordt momenteel niet ondersteund door CIF out-of-the-box.


### Integratiepatroon 3 {#integration-pattern-three}

In dit patroon is Magento eigenaar van het glas en sluit het AEM geschreven inhoud in. De AEM geschreven inhoud kan worden geleverd via Experience Fragments of Content Fragments. Dit integratiepatroon vereist projectspecifiek werk en kan niet buiten de doos met CIF worden uitgevoerd.


### Integratiepatroon 4 {#integration-pattern-four}

Dit is een gangbaar integratiepatroon waarbij de glas- of presentatielaag wordt verdeeld tussen AEM en een handelsoplossing. Doorgaans levert de oplossing Handel de niet-marketingpagina&#39;s zoals Afrekenen en Mijn account en AEM de marketingpagina&#39;s en de ervaring met de winkelcatalogus. In dit patroon moet u ervoor zorgen dat winkelwagentjes en gebruikerssessies op de juiste wijze tussen de twee systemen worden afgehandeld om een ongekoppelde gebruikerservaring te voorkomen. Zo slaat Magento de winkelwagentje en de gebruikerssessie op in een cookie, die kan worden gedeeld tussen AEM &amp; Magento. Dit patroon zal project-specifiek werk vereisen en kan niet uit-van-de-doos met CIF worden uitgevoerd.
