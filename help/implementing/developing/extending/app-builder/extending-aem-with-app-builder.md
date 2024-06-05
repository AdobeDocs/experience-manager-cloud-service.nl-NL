---
title: Uitbreiden [!DNL Adobe Experience Manager] as a Cloud Service met Adobe Developer App Builder.
description: Uitbreiden [!DNL Adobe Experience Manager] as a Cloud Service met Adobe Developer App Builder.
exl-id: 50d82745-5deb-4bfa-961b-714842403601
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# Uitbreiden [!DNL Adobe Experience Manager] as a Cloud Service met Adobe Developer App Builder {#extend-using-app-builder}

## Wat is App Builder voor AEM as a Cloud Service {#project-appbuilder}

De nieuwe Adobe Developer App Builder biedt een uitbreidingsframework waarmee een ontwikkelaar functies eenvoudig kan uitbreiden in AEM as a Cloud Service.

App Builder biedt een geïntegreerd extern uitbreidingsframework voor het integreren en maken van aangepaste ervaringen die Adobe Experience Manager uitbreiden. Met dit complete uitbreidingsframework, gebaseerd op de infrastructuur van de Adobe, kunnen ontwikkelaars aangepaste microservices bouwen, Adobe Experience Manager uitbreiden en integreren in alle Adobe oplossingen en de rest van de IT-stack.

App Builder biedt klanten een manier om Adobe Experience Manager in verschillende gebruiksgevallen eenvoudig uit te breiden:

* Uitbreidbaarheid middleware - Sluit externe systemen aan op Adobe-toepassingen die aangepaste connectors maken of gebruik maken van een reeks vooraf gebouwde integraties.
* De Uitbreidbaarheid van de Diensten van de kern - breid kerntoepassingsmogelijkheden door het standaardgedrag met douaneeigenschappen &amp; bedrijfslogica uit te breiden.
* Gebruikerservaring Uitbreidbaarheid: breid de kernervaring uit om bedrijfsvereisten te ondersteunen of klantspecifieke digitale eigenschappen, winkelcentra en back-office toepassingen te ontwikkelen.

App Builder is sinds zomer 2020 beschikbaar voor zakelijke klanten en partners via de Developer Preview van Adobe. De algemene beschikbaarheid (GA) van App Builder is gepland voor december 2021. Adobe verwelkomt ontwikkelaars om App Builder uit te proberen via de [Proefprogramma](https://developer.adobe.com/app-builder/trial/).

>[!NOTE]
>
> Voor AEM 6.5 klanten die de App Builder willen gebruiken, zie [Adobe Experience Manager 6.5 uitbreiden met Adobe Developer App Builder](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/app-builder.html).

## Architectuur {#architecture}

In plaats van een out-of-the-box oplossing biedt Adobe Developer App Builder een gemeenschappelijk, consistent en gestandaardiseerd ontwikkelingsplatform voor het uitbreiden van Adobe Cloud-oplossingen, zoals AEM:

* Adobe Developer Console — Voor de ontwikkeling van aangepaste microservices en extensies kunnen ontwikkelaars projecten maken en beheren en tegelijkertijd toegang krijgen tot alle benodigde gereedschappen en API&#39;s, zodat ze plug-ins en integratie kunnen maken.
* Gereedschappen voor ontwikkelaars — Open-source-gereedschappen, SDK&#39;s en bibliotheken waarmee ontwikkelaars eenvoudig aangepaste extensies en integratie kunnen maken. Gebruik React Spectrum (UI toolkit van Adobe) zodat u één gemeenschappelijke gebruikersinterface voor alle Adobe apps hebt.
* Services — I/O-runtime voor het hosten van infrastructuren op het serverplatform van de Adobe en I/O-gebeurtenissen voor op gebeurtenissen gebaseerde integratie. Adobe biedt ook out-of-the-box ondersteuning voor het opslaan van gegevens en bestanden.
* Adobe Experience Cloud — Ontwikkelaars kunnen extensies en integraties indienen die binnen hun Experience Cloud Org worden gepubliceerd. Systeembeheerders kunnen deze extensies vervolgens controleren, beheren en goedkeuren. Na publicatie vindt u naast andere Adobe Experience Cloud-apps ook de aangepaste App Builder-extensies en -gereedschappen.

Het volgende diagram illustreert hoe een standaardtoepassing die op App Builder wordt gebouwd deze functionaliteit gebruikt:

![Architectuur](/help/implementing/developing/extending/assets/appbuilder-architecture.jpg)

Voor meer details over de architectuur van App Builder, heb een blik bij [Overzicht van architectuur](https://developer.adobe.com/app-builder/docs/guides/).

## Aan de slag met App Builder {#additional-resources}

Adobe heeft Aan de slag-documentatie gemaakt, zodat u aan de slag kunt met App Builder:

* [Aan de slag met App Builder](https://developer.adobe.com/app-builder/docs/getting_started/)

## Doorgaan met leren met documentatie {#appbuilder-documentation}

App Builder biedt video&#39;s en documentatie voor ontwikkelaars, waaronder hulplijnen en documentatie over naslaggidsen, waarmee u uw eigen aangepaste toepassingen kunt ontwikkelen:

* [Documentatie voor App Builder](https://developer.adobe.com/app-builder/docs/overview/)
* [Video&#39;s over App Builder](https://www.youtube.com/playlist?list=PLcVEYUqU7VRfDij-Jbjyw8S8EzW073F_o)

## Een van de voorbeeldtoepassingen uitproberen {#appbuilder-codesamples}

Klaar om te beginnen met ontwikkelen? Adobe bevat veel voorbeeldtoepassingen waarmee u snel aan de slag kunt:

* [Code-labels voor App Builder op de Adobe Developer-website](https://developer.adobe.com/app-builder/docs/resources/)