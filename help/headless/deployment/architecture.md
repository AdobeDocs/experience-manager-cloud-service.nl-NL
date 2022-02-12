---
title: Architectuur van AEM headless
description: Meer informatie over de architectuur op hoog niveau voor Adobe Experience Manager omdat deze betrekking heeft op een headless-implementatie. Begrijp de rol van AEM Auteur, Voorproef, en publiceer de diensten en het geadviseerde plaatsingspatroon voor koploze toepassingen.
feature: Content Fragments,GraphQL API
source-git-commit: 64b2beb4af2297e19e39ad534856bce33ffcfcf8
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# Architectuur van AEM headless

Een typische AEM omgeving bestaat uit een Auteur-service, een Service voor publiceren en een optionele Voorvertoning.

* **De service Auteur** In dit deelvenster kunnen interne gebruikers inhoud maken, beheren en voorvertonen.

* **De service Publiceren** wordt beschouwd als de &quot;live&quot;-omgeving en is doorgaans de interactie tussen eindgebruikers. Inhoud wordt na bewerking en goedkeuring in de service Auteur gedistribueerd naar de service Publiceren. Het meest gebruikelijke implementatiepatroon met toepassingen zonder kop is dat de productieversie van de toepassing verbinding maakt met een AEM-publicatieservice.

* **De service Voorvertoning** is functioneel gelijk aan **Service voor publiceren**. Het wordt echter alleen ter beschikking gesteld van interne gebruikers. Hierdoor is het een ideaal systeem voor fiatteurs om aanstaande wijzigingen in de inhoud te controleren voordat deze live voor eindgebruikers worden gemaakt.

* **De verzender** is een statische webserver die is uitgebreid met de AEM dispatchermodule. Het verstrekt caching mogelijkheden en een andere laag van veiligheid. De **Dispatcher** voor de **Publiceren** en **Voorvertoning** diensten.

Binnen een AEM as a Cloud Service Programma kunt u veelvoudige milieu&#39;s, Dev, Stadium en Prod hebben. Elke omgeving zou een eigen unieke omgeving hebben **Auteur**, **Publiceren**, en **Voorvertoning** diensten. Meer informatie over het beheren [omgevingen hier](/help/implementing/cloud-manager/manage-environments.md)

## Publicatiemodel auteur

Het meest gebruikelijke implementatiepatroon met toepassingen zonder kop is dat de productieversie van de toepassing verbinding maakt met een AEM-publicatieservice.

![Auteur-publicatiearchitectuur](assets/autho-publish-architecture-diagram.png)

Het diagram hierboven toont dit gemeenschappelijke plaatsingspatroon.

1. A **Inhoudsauteur** gebruikt de AEM-auteurservice om inhoud te maken, bewerken en beheren.
1. De **Inhoudsauteur** en andere interne gebruikers kunnen de inhoud rechtstreeks op de service Auteur voorvertonen. Er kan een voorvertoningsversie van de toepassing worden ingesteld die verbinding maakt met de service Auteur.
1. Nadat de inhoud is goedgekeurd, kan deze worden gepubliceerd naar de AEM-publicatieservice.
1. De **Dispatcher** is een laag voor de **Publiceren** de dienst die bepaalde verzoeken in het voorgeheugen onderbrengen en een laag van veiligheid verstrekt.
1. Eindgebruikers hebben interactie met de productieversie van de toepassing. De productietoepassing maakt verbinding met de publicatieservice via de Dispatcher en gebruikt de GraphQL API&#39;s om inhoud aan te vragen en te verbruiken.

## Implementatie van publicatievoorvertoning voor auteur

Een andere optie voor headless plaatsingen is een **Voorvertoning AEM** service. Met deze aanpak kan inhoud eerst worden gepubliceerd op de **Voorvertoning** en een voorvertoningsversie van de toepassing zonder kop kan hiermee verbinding maken. Het voordeel van deze aanpak is dat **Voorvertoning** de dienst kan opstelling met de zelfde authentificatievereisten en toestemmingen zoals **Publiceren** , waardoor het gemakkelijker wordt om de produktie-ervaring te simuleren.

![Architectuur voor voorvertonen en publiceren door auteurs](assets/author-preview-publish-architecture-diagram.png)

1. A **Inhoudsauteur** gebruikt de AEM-auteurservice om inhoud te maken, bewerken en beheren.
1. Inhoud wordt eerst gepubliceerd naar de service AEM.
1. Er kan een voorvertoningsversie van de toepassing worden ingesteld die verbinding maakt met de service Voorvertoning.
1. Nadat de inhoud is gereviseerd en goedgekeurd, kan deze worden gepubliceerd naar de AEM-publicatieservice.
1. Eindgebruikers hebben interactie met de productieversie van de toepassing. De productietoepassing maakt verbinding met de publicatieservice via de Dispatcher en gebruikt de GraphQL API&#39;s om inhoud aan te vragen en te verbruiken.

