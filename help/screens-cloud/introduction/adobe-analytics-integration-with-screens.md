---
title: Adobe Analytics-integratie met AEM Screens Cloud
seo-title: Adobe Analytics Integration with AEM Screens
description: Volg deze pagina om meer te weten te komen over de integratie van AEM Screens met Adobe Analytics in de doos en geeft u een proefdruk van het spel.
seo-description: Follow this page to learn about out of the box integration of AEM Screens with Adobe Analytics and provides you with a proof of play.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: trushton
content-type: reference
products: SG_EXPERIENCEMANAGER/Cloud/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
role: Admin, Developer
level: Intermediate
exl-id: e22242ce-e5ce-4486-bba4-e6a89ac4fb5e
source-git-commit: 75d147886c8151f8b8ac41af907e17b5deff5a9c
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# Adobe Analytics-integratie met AEM Screens Cloud {#adobe-analytics-integration-with-aem-screens}

In deze sectie worden de volgende onderwerpen behandeld:

* **Overzicht**
* **Architectuurgegevens**

## Overzicht {#overview}

***AEM Screens*** Gebruikt Adobe Analytics, en daarmee kunt u iets uniek in de markt - dwars-kanaalanalyses bereiken die helpen inhoud correleren die in plaats met andere gegevensbronnen wordt getoond.

AEM Screens biedt een uitweg uit de box-integratie met Adobe Analytics en biedt u een bewijs van spel.

In deze sectie wordt de volgende functionaliteit beschreven die betrokken is bij het verbinden van een AEM Screens-project met Adobe Analytics:

* Staat voor bewijs van spel rapportering door apparaat toe
* Staat toe dat de verslaggeving van de play-out per actief wordt aangetoond
* Hiermee zorgt u ervoor dat alle spelergebeurtenissen worden vastgelegd en voorzien van een tijdstempel
* Hiermee zorgt u ervoor dat alle spelergebeurtenissen lokaal worden opgeslagen als het afspelen niet is verbonden met een netwerk
* Hiermee kunnen feedbacklussen worden gemaakt die gebeurtenissen bijhouden
* Hiermee kan het systeem inhoud en lay-outs wijzigen op basis van succescriteria die door de auteur van de inhoud zijn gedefinieerd

Adobe Analytics Integration with AEM Screens dwingt dus het volgende af *doelen*:

* ROI van de implementatie van de digitale handtekening inschakelen
* Analyses integreren als basis voor toekomstige mogelijkheden voor het verzamelen en analyseren van gebruiksinformatie

## Architectuurgegevens {#architectural-details}

Een AEM Screens-klant wil weten welke inhoud op welk moment en voor hoe lang (geaggregeerd) is weergegeven. Dit is gemeenschappelijk vermogen van signaleringsoplossing. In plaats van onze eigen analyses op te stellen, zal AEM Screens Adobe Analytics benutten en daarmee kunnen we iets anders bereiken op de markt - kanaaloverschrijdende analyses die de inhoud die op locatie wordt getoond, helpen correleren met andere gegevensbronnen.

In het volgende architectuurdiagram wordt de Adobe Analytics Integration met AEM Screens uitgelegd:

![Integratie met Adobe Analytics](/help/screens-cloud/assets/analytics-architecture.png)

## Adobe Analytics inschakelen in AEM Screens Cloud {#enabling-adobe-analytics-in-aem-screens-cloud}

Neem contact op met uw Adobe Relationship Manager om Adobe-analysemogelijkheden in te schakelen in de cloud.

## Adobe Analytics Service gebruiken in AEM Screens Cloud {#using-adobe-analytics-service-in-aem-screens}

Dit scenario haalt Analytics API door de vraag van het HART van een analysedienst in de ingebouwde programmatuur en de apparaat scherm-kern componenten aan om gebeurtenissen uitdrukkelijk tot stand te brengen en te verzenden specifiek voor een bepaald gebruiksgeval terwijl het toestaan van rekbaarheid waar om het even welk douanebericht naar Analytics van een douane ontwikkeld kanaal kan worden verzonden.

Analytische gebeurtenissen worden offline opgeslagen in geïndexeerdeDB en later afgekapt en naar de cloud verzonden.

>[!NOTE]
>Raadpleeg voor meer informatie over de rangschikking en het standaardgegevensmodel voor gebeurtenissen [Adobe Analytics voor AEM Screens configureren](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/analytics-integration/configuring-adobe-analytics-aem-screens.html) voor meer informatie.
