---
title: Integratie van AEM en handel van derden met behulp van het kader voor integratie van de handel
description: Ondernemingen kunnen aanvullende handelsoplossingen van derden nodig hebben om hun winkel te kunnen bedienen. Het Kader van de Integratie van de Handel (CIF) kan in dergelijke integratiescenario's worden gebruikt om een derde handelsoplossing met Adobe Experience Manager te verbinden gebruikend I/O Runtime.
thumbnail: cif-third-party-architecture.jpg
exl-id: 3ebdb8eb-65ba-46be-aca3-6c06c8d1600c,42dd8922-540d-4a93-9e45-b5e83dc11e16
source-git-commit: a53ef07cd9da636c8d938c711de6defb9eb8e05f
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# Integratie van AEM en handel van derden met behulp van het kader voor integratie van de handel {#aem-third-party}

De integratie van niet-Adobe Commerce-oplossingen is een algemeen scenario voor CIF. Oplossingen van derden met verschillende API&#39;s en schema&#39;s worden verbonden via een integratielaag.

## Architectuur {#architecture}

De architectuur ziet er als volgt uit:

![Overzicht van architectuur van niet-Magento/derden AEM](../assets//AEM_nonMagento_Architecture.png)

Het doel van deze integratielaag is om API&#39;s en schema&#39;s van derden toe te wijzen aan de hand van de ondersteunde Adobe Commerce GraphQL API&#39;s en schema&#39;s buiten de Experience Manager. Dankzij deze inkapseling kunnen de integratielogica en -systemen worden bijgewerkt zonder code in de Experience Manager te wijzigen.

## Oplossingsvereisten voor integratie

Als de Experience Manager op aanvraag gegevens ophaalt, zijn realtime API&#39;s voor de productcatalogus vereist.

>[!TIP]
>
>Als er geen real-time API&#39;s beschikbaar zijn, moet een externe productcache met API&#39;s worden gebruikt voor de integratie. Voorbeeld [Magento opensource](https://magento.com/products/magento-open-source).

Het is niet nodig om het volledige schema GraphQL uit te voeren, enkel de voorwerpen van het schema om de gewenste gebruik-gevallen toe te laten.

## Gebruiksscenario&#39;s voor backend

CIF breidt de Experience Manager met de hulpmiddelen van het de productcatalogustoegang in real time en van het de ervaringsbeheer van het product uit. Deze naadloze integratie laat auteurs toe om tot handelsgegevens toegang te hebben gebruikend ingebedde UIs wanneer nodig zonder de inhoudscontext te verlaten.

De integratie van de productcatalogus-API&#39;s is vereist om deze gebruiksgevallen te ontgrendelen.

## Voorlopige gebruiksgevallen

[AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components) gegevens ophalen en uitwisselen via de door CIF ondersteunde Adobe Commerce API&#39;s. Om componenten te hergebruiken, moeten de respectieve APIs worden uitgevoerd.

De aanbeveling voor prestaties kritieke cliënt-zijcomponenten moet direct met de derdeoplossing communiceren om latentie te vermijden.

## Ontwikkeling van integratie {#develop-integration}

We raden u aan [Adobe I/O Runtime](https://www.adobe.io/apis/experienceplatform/runtime.html) voor de integratielaag. Het is opgenomen in de cif-invoegtoepassing voor derden. Aangezien het met een microdienst-als benadering werkt, is het geschikt om gemakkelijk veelvoudige oplossingen te integreren.

De [referentieimplementatie](https://github.com/adobe/commerce-cif-graphql-integration-reference) is een groot uitgangspunt om de integratie aan uw handelsoplossing te bouwen. Hoewel GraphQL wordt ondersteund, kan deze ook worden geïntegreerd met elk ander type API, zoals REST.

Deze integratielaag is niet vereist als er een laag van derden beschikbaar is (bijvoorbeeld Mulesoft) of als de integratie op de oplossing van derden wordt gebouwd.

## Vooraf gebouwde connectors {#connectors}

De schakelaars verstrekken een goede aanvang voor projecten. Ze worden geleverd met een specifieke verbinding met een handelsoplossing en standaard-API-toewijzing. Deze schakelaars worden gebouwd door derden en niet door Adobe gehandhaafd. Neem contact op met de betreffende partner voor meer informatie.

* [SAP Commerce](https://github.com/diconium/commerce-cif-graphql-integration-hybris), gebouwd door Diconium
* [Commercetools](https://github.com/diconium/commerce-cif-graphql-integration-commercetool), gebouwd door Diconium

>[!TIP]
>
>Terwijl de schakelaars projecten helpen om de handelsintegratie te versnellen, zijn zij niet stop-in-spel. De commerciële oplossingen van de onderneming zijn gewoonlijk zwaar aangepast en vereisen een douaneintegratie. Goede kennis van het handelsplatform, de schema&#39;s van Adobe Commerce GraphQL, en Adobe I/O Runtime wordt vereist.
