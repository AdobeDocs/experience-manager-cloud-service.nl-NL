---
title: Inleiding tot AEM Screens as a Cloud Service
description: Krijg inzicht in AEM Screens as a Cloud Service.
exl-id: b1cc0a63-ecd3-4d89-ac49-f384cc610cdc
feature: Screens Deployments
role: Admin, Developer, User
source-git-commit: 53086e2ec6d9d962a8f1cb1cc40f0601da74ac63
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 1%

---


# Inleiding tot AEM Screens as a Cloud Service {#introduction-screens-cloud}

Met Adobe Experience Manager (AEM) Screens as a Cloud Service, kunt u boeiende en dynamische digitale signage ervaringen creëren die bedoeld zijn om in openbare ruimten te worden verbruikt. Het is de volgende evolutie van het AEM Screens-product en betekent een grote stap voorwaarts in bruikbaarheid en schaalbaarheid.

AEM Screens as a Cloud Service is een digitale signaaloplossing waarmee marketers dynamische digitale ervaringen op schaal kunnen creëren en beheren. Daarnaast worden verschillende soorten fysieke schermen betrokken als onderdeel van een uitgebreide strategie voor digitale marketing. Het breidt het aanbod van de Adobe in het omni-kanaal uit tot meer dan het gebruikelijke web en mobiele kanalen, en omvat ook digitale signaalkanalen die overal om ons heen zijn. AEM Screens as a Cloud Service maakt relevantere, contextafhankelijke, productieve en anticipatieve gebruikerservaring mogelijk door een diepgaand inzicht in het maken van inhoud, het samenstellen van inhoud, geactiveerd gebeurtenisbeheer en het afspelen van media voor alle consumenten en bezoekers in een openbare ruimte.

## Componenten in Screens as a Cloud Service begrijpen {#understanding-components}

Screens as a Cloud Service bestaat uit twee hoofdonderdelen:

* **[Leverancier van de Inhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=nl-NL)**, die Screens toe:voegen-op lopend op AEM Cloud Service of op Adobe Managed Services (AMS) is. Met Screens Content Provider kan de auteur van de inhoud kanalen maken en beheren. De auteurs van de inhoud kunnen nieuwe inhoud toevoegen, de inhoud bewerken zonder zich zorgen te maken over de details van het maken van weergaven of spelerregistratie. De Content Provider biedt een abstractie van de onderliggende details van het ontwikkelen van inhoud, weergaven of spelerregistratie.

* **[Dienstverlener van de Diensten &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/navigating-to-screens-services-provider.html?lang=nl-NL)**, die de digitale dienst van het signaalbeheer is die op Adobe I/O Runtime loopt. Met Screens Services Provider kunnen auteurs, ontwikkelaars en beheerders van inhoud weergaven en spelers voor het afspelen van inhoud beheren zodra de inhoud aan de kanalen is toegevoegd. De Screens Services Provider informeert de organisator ook waar en wanneer inhoud op hoog niveau wordt afgespeeld.


## Overzicht van architectuur {#architectural-overview}

Als as a Cloud Service AEM Screens-gebruiker kunt u inhoud toevoegen en beheren in kanalen. U kunt vertoningen en spelers van de interfaces registreren en beheren die specifiek voor Screens as a Cloud Service worden ontworpen, namelijk, **de Dienstverlener van Screens** en **Screens Content Provider**.

![&#x200B; Architecturaal Overzicht &#x200B;](/help/screens-cloud/assets/architecture-screenscloud.png)
