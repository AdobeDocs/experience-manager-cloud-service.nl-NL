---
title: Adobe Analytics-integratie met AEM Screens Cloud
description: Volg deze pagina om meer te weten te komen over de integratie van AEM Screens met Adobe Analytics in de doos en geeft u een proefdruk van het spel.
contentOwner: trushton
content-type: reference
products: SG_EXPERIENCEMANAGER/Cloud/SCREENS
topic-tags: administering
docset: aem65
role: Admin, Developer
level: Intermediate
exl-id: e22242ce-e5ce-4486-bba4-e6a89ac4fb5e
feature: Screens Deployments
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# Adobe Analytics-integratie met AEM Screens Cloud {#adobe-analytics-integration-with-aem-screens}

In deze sectie worden de volgende onderwerpen behandeld:

* **Overzicht**
* **Architecturale Details**

## Overzicht {#overview}

***AEM Screens*** hefboomwerkingen Adobe Analytics, en met dat kunt u iets uniek in de markt - dwars-kanaalanalyse bereiken die helpen inhoud correleren die in plaats met andere gegevensbronnen wordt getoond.

AEM Screens biedt een uitweg uit de box-integratie met Adobe Analytics en biedt u een bewijs van spel.

In deze sectie wordt de volgende functionaliteit beschreven die betrokken is bij het verbinden van een AEM Screens-project met Adobe Analytics:

* Staat voor bewijs van spel rapportering door apparaat toe
* Staat toe dat de verslaggeving van de play-out per actief wordt aangetoond
* Hiermee zorgt u ervoor dat alle spelergebeurtenissen worden vastgelegd en voorzien van een tijdstempel
* Hiermee zorgt u ervoor dat alle spelergebeurtenissen lokaal worden opgeslagen als het afspelen niet is verbonden met een netwerk
* Hiermee kunnen feedbacklussen worden gemaakt die gebeurtenissen bijhouden
* Hiermee kan het systeem inhoud en lay-outs wijzigen op basis van succescriteria die door de auteur van de inhoud zijn gedefinieerd

De Integratie van Adobe Analytics met AEM Screens dwingt zo de volgende *doelstellingen* af:

* ROI van de implementatie van de digitale handtekening inschakelen
* Analyses integreren als basis voor toekomstige mogelijkheden voor het verzamelen en analyseren van gebruiksinformatie

## Architectuurgegevens {#architectural-details}

Een AEM Screens-klant wil weten welke inhoud op welk moment en voor hoe lang (geaggregeerd) is weergegeven. Dit is gemeenschappelijk vermogen van signaleringsoplossing. In plaats van onze eigen analyses te maken, gebruikt AEM Screens Adobe Analytics, en daarmee kunt u iets unieke op de markt bereiken - kanaaloverschrijdende analyse die de inhoud die op locatie wordt getoond, kan correleren met andere gegevensbronnen.

In het volgende architectuurdiagram wordt de Adobe Analytics Integration met AEM Screens uitgelegd:

![ Integratie met Adobe Analytics ](/help/screens-cloud/assets/analytics-architecture.png)

## Adobe Analytics inschakelen in AEM Screens Cloud {#enabling-adobe-analytics-in-aem-screens-cloud}

Neem contact op met uw Adobe Relationship Manager om Adobe-analysemogelijkheden in Screens Cloud in te schakelen.

## Adobe Analytics Service gebruiken in AEM Screens Cloud {#using-adobe-analytics-service-in-aem-screens}

Dit scenario haalt Analytics API door de vraag van het HART van een analysedienst in de ingebouwde programmatuur en de apparaat scherm-kern componenten aan om gebeurtenissen uitdrukkelijk tot stand te brengen en te verzenden specifiek voor een bepaald gebruiksgeval terwijl het toestaan van rekbaarheid waar om het even welk douanebericht naar Analytics van een douane ontwikkeld kanaal kan worden verzonden.

Analytische gebeurtenissen worden offline opgeslagen in geïndexeerdeDB en later afgekapt en naar de cloud verzonden.

>[!NOTE]
>Meer over het Opeenvolgen en het Standaard Model van Gegevens voor Gebeurtenissen leren, zie [ Vormend Adobe Analytics voor AEM Screens ](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/analytics-integration/configuring-adobe-analytics-aem-screens.html?lang=nl-NL) voor details.
