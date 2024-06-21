---
title: Architectuur van AEM headless
description: Meer informatie over de architectuur op hoog niveau voor Adobe Experience Manager omdat deze betrekking heeft op een headless-implementatie. Begrijp de rol van AEM auteur, Voorproef, en de diensten van Publish en het geadviseerde plaatsingspatroon voor headless toepassingen.
feature: Headless, Content Fragments,GraphQL API
exl-id: 5ba6921f-b06e-463d-b956-d1fb434090c9
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# Architectuur van AEM headless

Een typische AEM omgeving bestaat uit een Auteur Service, Publish Service en een optionele Voorvertoningsservice.

* **De service Auteur** In dit deelvenster kunnen interne gebruikers inhoud maken, beheren en voorvertonen.

* **De service Publiceren** wordt beschouwd als de &quot;live&quot;-omgeving en is doorgaans de interactie tussen eindgebruikers. Inhoud wordt na bewerking en goedkeuring in de service Auteur gedistribueerd naar de service Publiceren. Het gemeenschappelijkste plaatsingspatroon met AEM hoofdloze toepassingen moet de productieversie van de toepassing hebben met de AEM publicatieservice verbinden.

* **De service Voorvertoning** is functioneel gelijk aan **Publish Service**. Het wordt echter alleen ter beschikking gesteld van interne gebruikers. Hierdoor is het een ideaal systeem voor fiatteurs om aanstaande wijzigingen in de inhoud te controleren voordat deze live voor eindgebruikers worden gemaakt.

* **De verzender** is een statische webserver die is uitgebreid met de AEM dispatchermodule. Het verstrekt caching mogelijkheden en een andere laag van veiligheid. De **Dispatcher** voor de **Publiceren** en **Voorvertoning** diensten.

Binnen een AEM as a Cloud Service Programma kunt u veelvoudige milieu&#39;s, Dev, Stadium en Prod hebben. Elke omgeving zou een eigen unieke omgeving hebben **Auteur**, **Publiceren**, en **Voorvertoning** diensten. Meer informatie over het beheren [omgevingen hier](/help/implementing/cloud-manager/manage-environments.md)

## Publish-model auteur

Het gemeenschappelijkste plaatsingspatroon met AEM hoofdloze toepassingen moet de productieversie van de toepassing hebben met de AEM publicatieservice verbinden.

![Publish-architectuur van auteur](assets/autho-publish-architecture-diagram.png)

Het diagram hierboven toont dit gemeenschappelijke plaatsingspatroon.

1. A **Inhoudsauteur** gebruikt de AEM Auteur-service om inhoud te maken, te bewerken en te beheren.
1. De **Inhoudsauteur** en andere interne gebruikers kunnen de inhoud rechtstreeks op de service Auteur voorvertonen. Er kan een voorvertoningsversie van de toepassing worden ingesteld die verbinding maakt met de service Auteur.
1. Nadat de inhoud is goedgekeurd, kan deze worden gepubliceerd naar de AEM Publish-service.
1. De **Dispatcher** is een laag voor de **Publiceren** de dienst die bepaalde verzoeken in het voorgeheugen onderbrengen en een laag van veiligheid verstrekt.
1. Eindgebruikers hebben interactie met de productieversie van de toepassing. De productietoepassing maakt verbinding met de Publish-service via de Dispatcher en gebruikt de GraphQL API&#39;s om inhoud aan te vragen en te gebruiken.

## Publish-implementatie voor voorvertoning van auteur

Een andere optie voor headless plaatsingen is een **Voorvertoning AEM** service. Met deze aanpak kan inhoud eerst worden gepubliceerd op de **Voorvertoning** en een voorvertoningsversie van de toepassing zonder kop kan hiermee verbinding maken. Het voordeel van deze aanpak is dat **Voorvertoning** de dienst kan opstelling met de zelfde authentificatievereisten en toestemmingen zoals **Publiceren** , waardoor het gemakkelijker wordt om de produktie-ervaring te simuleren.

![Authorvoorvertoning en Publish-architectuur](assets/author-preview-publish-architecture-diagram.png)

1. A **Inhoudsauteur** gebruikt de AEM Auteur-service om inhoud te maken, te bewerken en te beheren.
1. Inhoud wordt eerst gepubliceerd naar de service AEM.
1. Er kan een voorvertoningsversie van de toepassing worden ingesteld die verbinding maakt met de service Voorvertoning.
1. Nadat de inhoud is gecontroleerd en goedgekeurd, kan deze worden gepubliceerd naar de service AEM Publish.
1. Eindgebruikers hebben interactie met de productieversie van de toepassing. De productietoepassing maakt verbinding met de Publish-service via de Dispatcher en gebruikt de GraphQL API&#39;s om inhoud aan te vragen en te gebruiken.
