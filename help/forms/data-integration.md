---
title: Hoe te om een gegevensbestand met te verbinden [!DNL AEM Forms] as a Cloud Service?
seo-title: AEM Forms Data Integration
description: U kunt gegevens ophalen en opslaan in RESTful-webservices, SOAP-webservices en OData-services van [!DNL AEM Forms] as a Cloud Service. De service biedt een speciaal hulpmiddel voor het ophalen, testen, valideren en verzenden van gegevens naar verschillende typen gegevensbronnen.
exl-id: 9d146275-de0a-4861-b060-d205ed6305f3
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# Verbind uw gegevensbronnen met Cloud Service {#aem-forms-data-integration}

![Gegevensintegratie](do-not-localize/data-integeration.png)

De infrastructuur van de onderneming omvat verschillende back-end systemen of gegevensbronnen zoals gegevensbestanden, Webdiensten, de diensten van REST, de diensten van OData, en de oplossingen van CRM. Samengesteld, maken zij een informatiesysteem dat gegevens aan ondernemingstoepassingen dient om zaken van dag tot dag uit te voeren. Anderzijds leggen toepassingen gegevens vast en sturen deze terug naar bijgewerkte gegevensbronnen.

[!DNL AEM Forms] toepassingen zoals Adaptive Forms en interactieve communicatie vereisen integratie met gegevensbronnen om klantgegevens op te halen tijdens het genereren van formulieren en het maken van interactieve communicatie. Er zijn gevallen waarin gegevens worden opgehaald uit gegevensbronnen die zijn gebaseerd op gebruikersinvoer in Adaptive Forms. Bovendien kunnen de ingediende gegevens van het adaptieve formulier worden teruggeschreven om de respectieve gegevensbronnen bij te werken.

Terwijl een verdeeld, modulair systeem zijn eigen voordelen heeft, ligt de uitdaging in het integreren van en het creëren van gegevensverenigingen over gegevensbronnen. De integratie van gegevens is de sleutel tot een functionele en efficiënte ondernemingsinfrastructuur met verschillende gegevensbronnen verbonden aan toepassingen voor de uitwisseling van bedrijfsgegevens.

## Overzicht van gegevensintegratie {#data-integration-overview}

![aem-forms-data-integer](assets/aem-forms-data-integeration.png)

[!DNL AEM Forms] Dankzij gegevensintegratie kunt u verschillende gegevensbronnen configureren en verbinden met [!DNL AEM Forms]. Het verstrekt een intuïtieve gebruikersinterface om een verenigd schema van de gegevensvertegenwoordiging van bedrijfsentiteiten en de diensten over verbonden gegevensbronnen tot stand te brengen. De verenigde vertegenwoordiging is genoemd geworden vormgegevensmodel, een uitbreiding van het schema JSON. De entiteiten in een formuliergegevensmodel worden gegevensmodelobjecten genoemd. Met een formuliergegevensmodel kunt u:

* Toegang tot gegevensmodelvoorwerpen, eigenschappen, en de diensten van verbonden gegevensbronnen.
* Objecten en eigenschappen van een aangepast gegevensmodel maken
* Bouw verenigingen tussen de voorwerpen van het gegevensmodel binnen en over gegevensbronnen.
* Roep gegevensmodelobjectservices aan om gegevens van en naar gegevensbronnen te zoeken of te schrijven.

Nadat u een formuliergegevensmodel hebt gemaakt, kunt u het gebruiken in verschillende workflows voor adaptieve formulieren en interactieve communicatie, zoals:

* Adaptieve Forms en interactieve communicatie maken op basis van het gegevensmodel van het formulier
* Aangepaste Forms en interactieve communicatie vooraf vullen vanuit geconfigureerde gegevensbronnen
* Gegevensbronservices/bewerkingen aanroepen met behulp van adaptieve formulierregels
* Verzonden adaptieve formuliergegevens naar gegevensbronnen schrijven

## Aan de slag met gegevensintegratie {#get-started-with-data-integration}

De eerste stap om gegevensintegratie uit te voeren is gegevensbronnen te identificeren en te vormen die informatie opslaan u in Aanpassings Forms en interactieve communicatie gebruiksgevallen wilt gebruiken. Vervolgens maakt u een formuliergegevensmodel dat gebruikmaakt van gegevensmodelobjecten, eigenschappen en services van een of meer gegevensbronnen. U kunt adaptieve Forms en interactieve communicatie maken op basis van een formuliergegevensmodel, waarbij adaptieve formuliervelden of plaatsaanduidingen in interactieve communicatie zijn gebonden aan de desbetreffende gegevensbroneigenschappen.

[!DNL AEM Forms] Hiermee kunt u ook een formuliergegevensmodel maken dat onafhankelijk is van gegevensbronnen en kunt u later gegevensmodelobjecten en eigenschappen in het formuliergegevensmodel koppelen aan of binden met gegevensbron. Hiermee worden afhankelijkheden van gegevensbronnen verwijderd terwijl u werkt aan een formuliergegevensmodel.

Herzie het volgende om, gegevensintegratie te beginnen te begrijpen en uit te voeren.

* [Gegevensbronnen configureren](configure-data-sources.md)
* [Formuliergegevensmodel maken](create-form-data-models.md)
* [Werken met formuliergegevensmodel](work-with-form-data-model.md)
* [Formuliergegevensmodel gebruiken](using-form-data-model.md)

>[!NOTE]
>
>[!UICONTROL Experience Manager Forms] ondersteunt geen relationele database.
