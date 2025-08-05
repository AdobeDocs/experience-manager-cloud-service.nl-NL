---
title: Inleiding en overzicht
description: De verschillende winkelopties begrijpen
thumbnail: introducing-aem-commerce.jpg
exl-id: 29410f76-a63f-4b0a-b817-2ed724ad1a3c
feature: Commerce Integration Framework
role: Admin
source-git-commit: 145cd4961bd9c0c7bb7e39a1d6dae67f240ecb4d
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---


# Inhoud en Commerce {#content-commerce}

Aangezien de klantenverwachtingen voor op bedoeling-gebaseerde en krachtige handelservaringen groeien, zijn de merken onder druk om meer inhoud sneller-zonder kwaliteit te offeren te leveren. Met Adobe Experience Manager kunnen merken sneller schalen en innoveren om overweldigende ervaringen met handel te creëren en meer verkeer vast te leggen en online uitgaven te doen toenemen.

Adobe Experience Manager biedt krachtige tools voor het maken en beheren van content-rijke, persoonlijke ervaringen van klanten. Door AEM te integreren met een handelsoplossing, zoals Adobe Commerce, Salesforce Commerce, SAP Commerce Cloud of een andere oplossing, kunnen merken inhoud en handel verenigen om naadloze winkelreizen langs verschillende kanalen te leveren.

## Overzicht van storefronbenaderingen {#overview}

AEM kan je steunen op basis van je situatie en voorkeuren. Gebruik de volgende richtlijnen om de juiste benadering voor u te kiezen:

* [Edge Delivery Services gebruiken (aanbevolen)](#edge)
* [Gebruik je eigen winkel (zonder kop AEM-integratie)](#own-storefront)
* [AEM CIF-winkel gebruiken](#cif)

### Edge Delivery Services gebruiken (aanbevolen) {#edge}

Als uw zaken het snelste en AI-vriendelijkste winkelcentrum op het Web willen en uw ontwikkelaars een de modernste ontwikkelaarservaring willen, gebruik [ Edge Delivery Services.](../edge/overview.md) Edge Delivery Services voldoet aan alle vereisten van vandaag en morgen. Afhankelijk van onze back-end en oplossing hebt u verschillende opties:

#### &#x200B;1. Integratie met Adobe Commerce as a Cloud Service {#acaacs}

Dit is de perfecte oplossing als u Edge Delivery en [ Adobe Commerce Storefront ](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=nl-NL) als uitgangspunt gebruikt. De winkel wordt geleverd met een bouwsteenplaat die vooraf is geïntegreerd met Adobe Commerce-services, API&#39;s en die een groot aantal Commerce-drop-in-componenten biedt om snel een winkel te bouwen.

Geschikt: typische storefront-ervaring met Adobe Commerce as a Cloud Service

#### &#x200B;2. Integratie met Adobe Commerce Optimizer (voor elke oplossing van derden) {#aco}

Als u uw bestaande handelsoplossing wilt integreren en uw catalogusprestaties verhogen, moet de aanbeveling van Adobe [ Adobe Commerce Optimizer ](https://experienceleague.adobe.com/nl/docs/commerce-learn/tutorials/adobe-commerce-optimizer/overview) als moderne integratielaag gebruiken. Commerce Optimizer verbetert uw handelsoplossing met de krachtige diensten SaaS voor catalogus en handel. Zoals met Adobe Commerce as a Cloud Service, [ Adobe Commerce Storefront ](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=nl-NL) werkt uit-van-de-doos met het.

Integraties met commerciële handelsoplossingen zoals Salesforce Commerce zijn beschikbaar. Neem contact op met je Adobe-vertegenwoordiger.

Geschikt: typische storefronervaring met een bestaande handelsoplossing

#### &#x200B;3. Aangepaste integratie {#custom}

Adobe raadt u ook aan Edge Delivery Services te gebruiken als u een aangepaste integratie wilt maken. U kunt of van kras beginnen of bestaande JS-Kader handelcomponenten (b.v. voor het transactionele deel) in uw Edge Delivery opslag opnieuw gebruiken. Op die manier krijgen uw klanten een razendsnelle boodschapervaring die agentisch vriendelijk is, terwijl u uw bestaande investeringen kunt hergebruiken om TTV te verhogen. Uw uitgangspunt is het gebrek [ Boilerplate van Edge Delivery ](https://www.aem.live/developer/tutorial).

Goed passend: lage waarde uit de Edge Deliery storefront

### Gebruik uw eigen winkel (Headless AEM-integratie) {#own-storefront}

U hebt een bestaande winkel (bijvoorbeeld gebouwd met React JS) en wilt Adobe Experience Manager gebruiken voor inhoudsbeheer en levering (Content Fragments), activa, plus in-context het uitgeven (Universele Redacteur). Uw uitgangspunt voor een integratie is [ Inleiding aan Adobe Experience Manager als Hoofdloze CMS ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/headless/introduction) en [ toe:voegen-op CIF ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/content-and-commerce/storefront/authoring/enrich-product-associated-content). Met de invoegtoepassing CIF kunt u uw productgegevens naadloos integreren in AEM (zoek-, blader- en zoekproducten in de AEM-interface) waarmee u specifieke ervaringen op handelsgebied kunt opbouwen.

### AEM CIF storefront {#cif}

Adobe adviseert en referentiearchitectuur is Edge Delivery Services te gebruiken. De CIF storefront met de AEM CIF Core Components bevindt zich nu in de onderhoudsmodus en mag niet worden gebruikt in nieuwe projecten. Voor verwijzing, gelieve te zien de [ documentatie van CIF.](/help/commerce-cloud/cif-introduction.md)

>[!NOTE]
>
>Bestaande klanten die de nieuwe AEM-/Commerce-functionaliteit willen benutten, moeten hun website naar Edge Delivery verplaatsen. Een gangbaar patroon is om te beginnen door alleen een subset van pagina&#39;s naar Edge Delivery te verplaatsen en Edge Deliery- en CIF-pagina&#39;s naast elkaar uit te voeren. Het is ook mogelijk om de componenten van AEM CIF met de nieuwe [ drop-in componenten van Commerce ](https://experienceleague.adobe.com/developer/commerce/storefront/dropins/all/introduction/?lang=nl-NL) aan hefboomwerking nieuwe mogelijkheden van Commerce te vervangen.
