---
title: Uitbreidend  [!DNL Adobe Experience Manager]  as a Cloud Service gebruikend Adobe Developer App Builder.
description: Uitbreidend  [!DNL Adobe Experience Manager]  as a Cloud Service gebruikend Adobe Developer App Builder.
exl-id: 50d82745-5deb-4bfa-961b-714842403601
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] as a Cloud Service uitbreiden met Adobe Developer App Builder {#extend-using-app-builder}

## Wat is App Builder voor AEM as a Cloud Service {#project-appbuilder}

De nieuwe Adobe Developer App Builder biedt een uitbreidbaarheidskader voor een ontwikkelaar om functies in AEM as a Cloud Service eenvoudig uit te breiden.

App Builder biedt een uniform uitbreidbaarheidskader van derden voor het integreren en maken van aangepaste ervaringen die Adobe Experience Manager uitbreiden. Met dit complete uitbreidingsframework, gebaseerd op de infrastructuur van de Adobe, kunnen ontwikkelaars aangepaste microservices bouwen, Adobe Experience Manager uitbreiden en integreren in alle Adobe oplossingen en de rest van de IT-stack.

App Builder biedt klanten de mogelijkheid om Adobe Experience Manager in verschillende gebruiksgevallen eenvoudig uit te breiden:

* Uitbreidbaarheid middleware - Sluit externe systemen aan op Adobe-toepassingen die aangepaste connectors maken of gebruik maken van een reeks vooraf gebouwde integraties.
* De Uitbreidbaarheid van de Diensten van de kern - breid kerntoepassingsmogelijkheden door het standaardgedrag met douaneeigenschappen &amp; bedrijfslogica uit te breiden.
* Gebruikerservaring Uitbreidbaarheid: breid de kernervaring uit om bedrijfsvereisten te ondersteunen of klantspecifieke digitale eigenschappen, winkelcentra en back-office toepassingen te ontwikkelen.

App Builder is sinds zomer 2020 beschikbaar voor zakelijke klanten en partners via de Developer Preview van Adobe. De algemene beschikbaarheid (GA) van App Builder is gepland voor december 2021. De Adobe verwelkomt ontwikkelaars om App Builder door het [ Proefprogramma ](https://developer.adobe.com/app-builder/trial/) uit te proberen.

>[!NOTE]
>
> Voor AEM 6.5 klanten die App Builder willen gebruiken, zie [ Uitbreidend Adobe Experience Manager 6.5 gebruikend Adobe Developer App Builder ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/app-builder.html).

## Architectuur {#architecture}

In plaats van een out-of-the-box oplossing biedt Adobe Developer App Builder een gemeenschappelijk, consistent, gestandaardiseerd ontwikkelingsplatform voor het uitbreiden van Adobe Cloud-oplossingen, zoals AEM:

* Adobe Developer Console — Voor de ontwikkeling van aangepaste microservices en extensies kunnen ontwikkelaars projecten maken en beheren en tegelijkertijd toegang krijgen tot alle benodigde gereedschappen en API&#39;s, zodat ze plug-ins en integratie kunnen maken.
* Gereedschappen voor ontwikkelaars — Open-source-gereedschappen, SDK&#39;s en bibliotheken waarmee ontwikkelaars eenvoudig aangepaste extensies en integratie kunnen maken. Gebruik React Spectrum (UI toolkit van Adobe) zodat u één gemeenschappelijke gebruikersinterface voor alle Adobe apps hebt.
* Services — I/O-runtime voor het hosten van infrastructuren op het serverplatform van de Adobe en I/O-gebeurtenissen voor op gebeurtenissen gebaseerde integratie. Adobe biedt ook out-of-the-box ondersteuning voor het opslaan van gegevens en bestanden.
* Adobe Experience Cloud — Ontwikkelaars kunnen extensies en integraties indienen die binnen hun Experience Cloud Org worden gepubliceerd. Systeembeheerders kunnen deze extensies vervolgens controleren, beheren en goedkeuren. Na publicatie vindt u naast andere Adobe Experience Cloud-apps ook aangepaste App Builder-extensies en -gereedschappen.

In het volgende diagram ziet u hoe een standaardtoepassing die op App Builder is gebouwd deze functies gebruikt:

![Architectuur](/help/implementing/developing/extending/assets/appbuilder-architecture.jpg)

Voor meer details over de architectuur van App Builder, heb een blik bij [ Overzicht van de Architectuur ](https://developer.adobe.com/app-builder/docs/guides/).

## Aan de slag met App Builder {#additional-resources}

Adobe heeft Aan de slag-documentatie gemaakt, zodat u aan de slag kunt met App Builder:

* [ Aan de slag App Builder ](https://developer.adobe.com/app-builder/docs/getting_started/)

## Doorgaan met leren met documentatie {#appbuilder-documentation}

App Builder biedt video&#39;s en documentatie voor ontwikkelaars, waaronder hulplijnen en documentatie voor naslagwerken, waarmee u uw eigen aangepaste toepassingen kunt ontwikkelen:

* [ documentatie van App Builder ](https://developer.adobe.com/app-builder/docs/overview/)
* [ de video&#39;s van App Builder ](https://www.youtube.com/playlist?list=PLcVEYUqU7VRfDij-Jbjyw8S8EzW073F_o)

## Een van de voorbeeldtoepassingen uitproberen {#appbuilder-codesamples}

Klaar om te beginnen met ontwikkelen? Adobe bevat veel voorbeeldtoepassingen waarmee u snel aan de slag kunt:

* [ de Etiketten van de Code van App Builder op de Website van Adobe Developer ](https://developer.adobe.com/app-builder/docs/resources/)