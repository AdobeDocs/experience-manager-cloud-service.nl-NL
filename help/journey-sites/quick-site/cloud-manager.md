---
title: Understand Cloud Manager and the Quick Site Creation Workflow
description: Learn about Cloud Manager and how it ties together the new Quick Site Creation process.
source-git-commit: efeb97d4bd7e7c11ec2c0ba1244a32b8b9affdab
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 0%

---


# Inzicht krijgen in Cloud Manager en de workflow voor snel maken van sites {#understand-cloud-manager}

Leer meer over Cloud Manager en hoe dit het nieuwe proces voor het maken van de Snelle site samenbrengt.

>[!CAUTION]
>
>Het gereedschap Snel site maken is momenteel een technische voorvertoning. It is made available for testing and evaluation purposes and is not intended for production use unless agreed with Adobe Support.

>[!TIP]
>
>Als uw rol exclusief front-end ontwikkeling is, kunt u aan het artikel overslaan [Toegangsgegevens van opslagplaats ophalen](retrieve-access.md) tijdens deze reis.
>
>Als u een AEM beheerder bent, is een beheerder van de Manager van de Wolk, verantwoordelijk voor zowel front-end ontwikkeling als beheerderstaken, of eenvoudig het proces van begin tot eind in AEM voor front-end ontwikkeling wilt begrijpen, blijven lezend het huidige document en ga op deze reis verder.

## Objective {#objective}

Dit document helpt u begrijpen hoe het AEM Snelle hulpmiddel van de Plaats werkt en geeft u een overzicht van de stroom van begin tot eind. Na het lezen moet u:

* Begrijp hoe AEM Sites en Cloud Manager samenwerken om de ontwikkeling op de voorgrond te vergemakkelijken
* Ontdek hoe de stap voor aanpassing volledig losgekoppeld is van AEM en geen AEM kennis vereist.

This document focuses on understanding these fundamental pieces of the Quick Site creation solution before moving on to the next step of the journey where you begin configuration.

Hoewel het aangeraden is stap voor stap door te gaan met deze reis, kunt u als u al begrijpt dat AEM Sites en Cloud Manager samenwerken en rechtstreeks met de configuratie willen beginnen [Ga verder met de volgende stap van de reis.](create-site.md)

## Responsible Role {#responsible-role}

Dit gedeelte van de reis is van toepassing op zowel de beheerder van de AEM als de beheerder van de Manager van de Wolk.

## Eisen en voorwaarden {#requirements-prerequisites}

There are several requirements before you begin creating and customizing sites using the Quick Site Creation tool.

Omdat deze reis voor zowel front-end ontwikkelaars, beheerders, als combinaties van alle rollen is bestemd, zijn de vereisten voor allebei hier vermeld.

Het is belangrijk te begrijpen dat voor de front-end ontwikkelaar geen AEM toegang of kennis noodzakelijk is.

### Kennis {#knowledge}

| Kennis | Rol |
|---|---|
| Inzicht in de standaardinstrumenten en -processen van front-end ontwikkeling | Front-endontwikkelaar |
| Basiskennis van het maken en beheren van sites in AEM | AEM-beheerder |
| Basiskennis van Cloud Manager | Cloud Manager-beheerder |

For the front-end developer, no AEM knowledge is necessary.

### Opties {#tools}

| Gereedschap | Rol |
|---|---|
| Voorkeursontwikkelomgeving | Front-endontwikkelaar |
| npm | Front-End Developer |
| webpack | Front-endontwikkelaar |
| Access to Cloud Manager | Cloud Manager-beheerder |
| Lid zijn van **Zakelijke eigenaar** rol in Cloud Manager | Cloud Manager-beheerder |
| Sys Admin in Cloud Manager zijn | Cloud Manager Administrator |
| Access to Admin Console | Cloud Manager-beheerder |
| Lid zijn van de **Implementatiebeheer** rol in Cloud Manager | Cloud Manager-beheerder |
| Lid zijn van de **Implementatiebeheer** rol in Cloud Manager | Front-endontwikkelaar |

Voor de front-end ontwikkelaar, is geen gebruik van AEM noodzakelijk.

>[!TIP]
>
>Als u niet bekend bent met de rollen en het rolbeheer van Cloud Manager, raadpleegt u het document Rolgebaseerde machtigingen in het dialoogvenster [Aanvullende bronnen](#additional-resources) sectie.

## Cloud Manager {#cloud-manager}

Cloud Manager is een essentieel onderdeel van AEM as a Cloud Service en fungeert als één ingangspunt voor het platform.

Om klanten met de montages van de ondernemingsontwikkeling te steunen, AEM as a Cloud Service volledig met de Manager van de Wolk en zijn doel-gebouwde CI/CD pijpleidingen integreren. Met het gereedschap Snel site maken kunt u deze functies uitbreiden voor ondersteuning van speciale front-end ontwikkelingspijplijnen.

For the purposes of this journey, a complete understanding of Cloud Manager is not necessary. Op hoog niveau bestaat Cloud Manager uit verschillende structuurniveaus.

![Cloud Manager structure](assets/cloud-manager-structure.png)

* **TENANT** - Every customer is provisioned with a tenant. **WKND Travel and Adventure Enterprises** might be a tenant.
* **PROGRAMMA&#39;S** - Elke huurder heeft een of meer programma&#39;s. De **WKND Reizen- en avontuurbedrijven** een huurder heeft **WKND Nightlife** en **WKND-projecten** programma.
* **ENVIRONMENTS** - Each program has multiple environments such as production for live content, and staging and dev for development purposes. **WKND Nightlife** and **WKND Afternoon Projects** programs would both have dev, stage, and production environments.
* **BEVESTIGING** - De omgevingen beschikken over git-opslagruimten waar de toepassing en front-end code worden onderhouden.
* **GEREEDSCHAPPEN EN WORKFLOWS** - De pijpleidingen beheren de implementatie van code van de gegevensbanken aan de milieu&#39;s.

## De snelle ontwikkeling van de Site Creation Front-End {#flow}

De algehele flow is eenvoudig en intuïtief, zelfs als u nog geen uitgebreide ervaring hebt met Cloud Manager.

1. The AEM administrator signs into an AEM environment, and creates a new site using a site template.
1. De beheerder van de Manager van de Wolk leidt tot een front-end pijpleiding in de Manager van de Wolk. De pijpleiding organiseert de plaatsing van code van een git bewaarplaats aan een AEM milieu.
1. De AEM beheerder voert het plaatsthema van de AEM instantie van het programma uit en verstrekt het aan de front-end ontwikkelaar.
1. De beheerder van de Manager van de Wolk verleent de front-end ontwikkelaar toegang tot de AEM git bewaarplaats waar de aanpassingen kunnen worden begaan.
1. De voorste eindontwikkelaar wint toegangsgeloofsbrieven aan toegangskit en de pijpleiding terug.
1. De front-end ontwikkelaar past het thema aan, test het het gebruikend daadwerkelijke inhoud van de plaats gebruikend een volmacht en begaat dan de veranderingen in de git bewaarplaats.
1. De front-end ontwikkelaar voert de pijpleiding uit om de themaaanpassingen aan het productiemilieu van het programma op te stellen.

![Snelle workflow voor het maken van sites](assets/qsc-flow.png)

The major advantage of using the Quick Site Creation tool is that the pure front-end developer is only responsible the actual customization. De front-end ontwikkelaar heeft geen interactie met AEM of heeft enige kennis van AEM nodig.

## What&#39;s Next {#what-is-next}

Nu u dit gedeelte van de AEM Quick Site Creation-reis hebt voltooid, moet u:

* Begrijp hoe AEM Sites en Cloud Manager samenwerken om de ontwikkeling op de voorgrond te vergemakkelijken
* Ontdek hoe de stap voor aanpassing volledig losgekoppeld is van AEM en geen AEM kennis vereist.

Gebaseerd op deze kennis en doorgaan met uw AEM snelle site-creatie door het document opnieuw te bekijken [Site maken van sjabloon,](create-site.md) Hier leert u hoe u snel een nieuwe AEM-site kunt maken met een sjabloon.

## Aanvullende bronnen {#additional-resources}

Terwijl u wordt aangeraden naar het volgende gedeelte van de reis Snel site maken te gaan door het document te bekijken [Site maken van sjabloon,](create-site.md) hieronder volgen enkele aanvullende , optionele bronnen die een dieper beeld geven van bepaalde in dit document genoemde concepten , maar die niet verplicht zijn om op de reis verder te gaan .

* [Cloud Manager documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - If you would like more details on Cloud Manager&#39;s features, you may want to directly consult the in-depth technical docs.
* [Role Based Permissions](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/role-based-permissions.html) - Cloud Manager has pre-configured roles with appropriate permissions. Raadpleeg dit document voor meer informatie over deze rollen en hoe u deze kunt beheren.
* [npm](https://www.npmjs.com) - AEM themes used to quickly build sites are based on npm.
* [webpack](https://webpack.js.org) - AEM thema&#39;s die worden gebruikt om sites snel op te bouwen, zijn gebaseerd op webpack.
