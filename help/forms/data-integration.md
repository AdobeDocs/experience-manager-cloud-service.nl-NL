---
title: Hoe te om een gegevensbestand met  [!DNL AEM Forms]  as a Cloud Service te verbinden?
description: Haal gegevens op en sla deze op voor RESTful-webservices, op SOAP gebaseerde webservices en OData-services van een adaptief formulier of een AEM-workflow.
feature: Adaptive Forms, Form Data Model
role: Admin, User
exl-id: 9d146275-de0a-4861-b060-d205ed6305f3
source-git-commit: 8f39bffd07e3b4e88bfa200fec51572e952ac837
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---

# AEM Forms verbinden met een database {#aem-forms-data-integration}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/data-integration.html) |
| AEM as a Cloud Service | Dit artikel |



![ de Integratie van Gegevens ](do-not-localize/data-integeration.png)

De infrastructuur van de onderneming omvat verschillende back-end systemen of gegevensbronnen zoals gegevensbestanden, Webdiensten, de diensten van REST, de diensten van OData, en de oplossingen van CRM. Samengesteld, maken zij een informatiesysteem dat gegevens aan ondernemingstoepassingen dient om zaken van dag tot dag uit te voeren. Anderzijds leggen toepassingen gegevens vast en sturen deze terug naar bijgewerkte gegevensbronnen.

Wanneer u een adaptief formulier aansluit op een database, is integratie met gegevensbronnen vereist om klantgegevens op te halen tijdens het genereren van formulieren. Er zijn gevallen waarin gegevens worden opgehaald uit gegevensbronnen die zijn gebaseerd op gebruikersinvoer in Adaptive Forms. Wanneer u een adaptief formulier naar een database verzendt, kunnen bovendien de verzonden Adaptieve formuliergegevens worden teruggeschreven om de respectieve gegevensbronnen bij te werken.

Terwijl een verdeeld, modulair systeem zijn eigen voordelen heeft, ligt de uitdaging in het integreren van en het creëren van gegevensverenigingen over gegevensbronnen. De integratie van gegevens is de sleutel tot een functionele en efficiënte ondernemingsinfrastructuur met verschillende gegevensbronnen verbonden aan toepassingen voor de uitwisseling van bedrijfsgegevens.

## Overzicht van gegevensintegratie {#data-integration-overview}

![ aem-vormen-gegeven-integratie ](assets/aem-forms-data-integeration.png)

[!DNL AEM Forms] Dankzij gegevensintegratie kunt u verschillende gegevensbronnen configureren en verbinden met [!DNL AEM Forms] . Het verstrekt een intuïtieve gebruikersinterface om een verenigd schema van de gegevensvertegenwoordiging van bedrijfsentiteiten en de diensten over verbonden gegevensbronnen tot stand te brengen. De verenigde vertegenwoordiging is gekend als model van vormgegevens (FDM), een uitbreiding van het schema JSON. De entiteiten in een formuliergegevensmodel (FDM) worden gegevensmodelobjecten genoemd. Met een formuliergegevensmodel (FDM) kunt u:

* Toegang tot gegevensmodelobjecten, eigenschappen en services van verbonden gegevensbronnen.
* Objecten en eigenschappen van een aangepast gegevensmodel maken
* Bouw verenigingen tussen de voorwerpen van het gegevensmodel binnen en over gegevensbronnen.
* Roep gegevensmodelobjectservices aan om gegevens van en naar gegevensbronnen te zoeken of te schrijven.

Nadat u een formuliergegevensmodel (FDM) hebt gemaakt, kunt u dit gebruiken om:

* Adaptieve Forms maken op basis van een formuliergegevensmodel (FDM)
* Adaptieve Forms vooraf vullen met geconfigureerde gegevensbronnen
* Gegevensbronservices/bewerkingen aanroepen met behulp van adaptieve formulierregels
* Verzonden adaptieve formuliergegevens naar gegevensbronnen schrijven

## Toepassings- en gebruiksgevallen

### Verzekeringen

## Kan AEM Forms worden gebruikt voor verzekeringspolistoepassingen?

Ja. AEM Forms kan worden gebruikt om formulieren voor digitale verzekeringstoepassingen te maken die aanvraaggegevens verzamelen, inputs valideren en integreren met systemen voor backend-underwriting.

## Biedt AEM Forms ondersteuning voor het overnemen van workflows?

Ja, met workflows en integratie. AEM Forms ondersteunt workflowgestuurde processen en backendintegratie die toepassingsgegevens in verzekerings- en beslissingssystemen laten stromen.

## Kan AEM Forms integreren met kernsystemen voor verzekeringen?

Ja. AEM Forms ondersteunt integratie met behulp van REST- en SOAP API&#39;s, zodat deze verbinding kan maken met beleidsbeheersystemen, claimbeheersystemen en CRM&#39;s.

## Kan AEM Forms formuliergegevens terugschrijven naar verzekeringssystemen?

Ja. AEM Forms biedt ondersteuning voor het terugschrijven van gegevens naar back-endsystemen als onderdeel van het verzenden van formulieren en het uitvoeren van workflows.

## Aan de slag met gegevensintegratie {#get-started-with-data-integration}

De eerste stap voor het implementeren van gegevensintegratie om Adaptief formulier naar een database te verzenden, is het identificeren en configureren van gegevensbronnen die informatie opslaan die u wilt gebruiken in Adaptief Forms. Daarna, creeert u een Model van de Gegevens van de Vorm (FDM) dat de voorwerpen, de eigenschappen, en de diensten van het gegevensmodel van één of meerdere gegevensbronnen gebruikt. U kunt Adaptief Forms maken op basis van een FDM (Form Data Model), waarbij Adaptive Form-velden zijn gebonden aan de desbetreffende gegevensbroneigenschappen.

Met [!DNL AEM Forms] kunt u ook een formuliergegevensmodel (FDM) maken dat onafhankelijk is van gegevensbronnen en kunt u later gegevensmodelobjecten en eigenschappen in het formuliergegevensmodel (FDM) koppelen aan of binden met gegevensbron. Hiermee worden afhankelijkheden van gegevensbronnen verwijderd terwijl u werkt aan een formuliergegevensmodel (FDM).

Lees het volgende om gegevensintegratie te beginnen, te begrijpen en te implementeren:

* [Gegevensbronnen configureren](configure-data-sources.md)
* [Formuliergegevensmodel maken (FDM)](create-form-data-models.md)
* [Werken met het formuliergegevensmodel (FDM)](work-with-form-data-model.md)
* [Formuliergegevensmodel (FDM) gebruiken](using-form-data-model.md)

<!--

>[!NOTE]
>
>[!UICONTROL Experience Manager Forms] does not support relational database.

-->