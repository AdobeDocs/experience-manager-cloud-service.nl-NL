---
title: AEM en Commerce-integratie van derden met Commerce integration framework
description: Ondernemingen kunnen aanvullende commerciële oplossingen van derden nodig hebben om hun winkel te bedienen. Commerce integration framework (CIF) kan in dergelijke integratiescenario's worden gebruikt om een derdehandelsoplossing aan Adobe Experience Manager te verbinden gebruikend I/O Runtime.
thumbnail: cif-third-party-architecture.jpg
exl-id: 3ebdb8eb-65ba-46be-aca3-6c06c8d1600c
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 80bd8da1531e009509e29e2433a7cbc8dfe58e60
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# AEM en Commerce-integratie van derden met Commerce integration framework {#aem-third-party}

De integratie van niet-Adobe Commerce-oplossingen is een gemeenschappelijk scenario voor CIF. De oplossingen van de derde met verschillende APIs en schema&#39;s worden verbonden via een integratielaag.

## Architectuur {#architecture}

De architectuur ziet er als volgt uit:

![ AEM niet-Magento/het Overzicht van de Architectuur van de Derde ](../assets/AEM_nonMagento_Architecture.png)

Het doel van deze integratielaag is om API&#39;s en schema&#39;s van derden toe te wijzen aan de ondersteunde Adobe Commerce GraphQL API&#39;s en schema&#39;s buiten de Experience Manager. Dankzij deze inkapseling kunnen de integratielogica en -systemen worden bijgewerkt zonder code in de Experience Manager te wijzigen.

## Oplossingsvereisten voor integratie {#requirements}

Als de Experience Manager op aanvraag gegevens ophaalt, zijn real-time API&#39;s voor de productcatalogus vereist.

>[!TIP]
>
>Als er geen real-time API&#39;s beschikbaar zijn, moet een externe productcache met API&#39;s worden gebruikt voor de integratie. Voorbeeld [ Adobe Commerce Open Source ](https://business.adobe.com/products/magento/open-source.html)

Het is niet nodig om het volledige schema van GraphQL uit te voeren, enkel de voorwerpen van het schema om de gewenste gebruik-gevallen toe te laten.

## Gebruiksscenario&#39;s voor backend {#backend}

CIF breidt de Experience Manager uit met realtime tools voor toegang tot productcatalogi en beheer van productervaring. Deze naadloze integratie laat auteurs toe om tot handelsgegevens toegang te hebben gebruikend ingebedde UIs wanneer nodig zonder de inhoudscontext te verlaten.

De integratie van de productcatalogus-API&#39;s is vereist om deze gebruiksgevallen te ontgrendelen.

## Voorste gebruikscenario&#39;s {#frontend}

[ AEM CIF Core Components ](https://github.com/adobe/aem-core-cif-components) wint en ruilt gegevens via CIF gesteunde Adobe Commerce APIs terug. Om componenten opnieuw te gebruiken, moeten de respectieve APIs worden uitgevoerd.

De aanbeveling voor prestaties kritieke cliënt-zijcomponenten moet direct met de derdeoplossing communiceren om latentie te vermijden.

## Ontwikkeling van integratie {#develop-integration}

Adobe adviseert dat u [ Runtime van Adobe Developer ](https://developer.adobe.com/runtime/) voor de integratielaag gebruikt. Het is opgenomen in de invoegtoepassing CIF voor derden. Aangezien het met een microdienst-als benadering werkt, is het geschikt om gemakkelijk veelvoudige oplossingen te integreren.

De [ verwijzingsimplementatie ](https://github.com/adobe/commerce-cif-graphql-integration-reference) is een groot uitgangspunt om de integratie aan uw handelsoplossing te bouwen. Hoewel deze functie GraphQL ondersteunt, kan deze ook worden geïntegreerd met elk ander type API, zoals REST.

Deze integratielaag wordt niet vereist als een derdelaag (bijvoorbeeld, Mulesoft) beschikbaar is of de integratie op de derdeoplossing wordt gebouwd.

## Vooraf gebouwde connectors {#connectors}

De schakelaars verstrekken een goede aanvang voor projecten. Zij komen met een handel oplossing-specifieke verbinding en gebrek API afbeelding. Deze schakelaars worden gebouwd door derden en niet gehandhaafd door Adobe. Vraag de respectievelijke partner om informatie.

* [ SAP Commerce ](https://github.com/diconium/commerce-cif-graphql-integration-hybris), die door Diconium wordt gebouwd
* [ Commercetools ](https://github.com/diconium/commerce-cif-graphql-integration-commercetool), die door Diconium worden gebouwd

>[!TIP]
>
>Terwijl de schakelaars projecten helpen om de handelsintegratie te versnellen, zijn zij niet stop-in-spel. De commerciële oplossingen van de onderneming zijn sterk aangepast en vereisen een douaneintegratie. Goede kennis van het handelsplatform, Adobe Commerce GraphQL-schema&#39;s en Adobe I/O Runtime is vereist.
