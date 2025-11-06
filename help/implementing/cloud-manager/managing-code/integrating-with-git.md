---
title: Git gebruiken met Cloud Manager
description: Leer hoe u Cloud Manager git-opslagruimten kunt gebruiken en hoe u uw eigen, door de klant beheerde git-opslagplaats op locatie kunt integreren met Cloud Manager.
exl-id: 57e71b8a-4546-4d7f-825c-a1637d08e608
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Git gebruiken met Cloud Manager {#git-integration}

Adobe Cloud Manager wordt geleverd met één git-opslagplaats die wordt gebruikt om code te implementeren met behulp van Cloud Manager CI/CD-leidingen.

U kunt de Cloud Manager git-opslagplaats uit de verpakking gebruiken, maar u hebt ook de mogelijkheid om een door de klant beheerde git-opslagplaats te integreren met Cloud Manager.

## Overzicht van Git-integratie {#git-integration-overview}

Deze videoreeks verkent verschillende gebruiksgevallen bij de integratie van een door de klant beheerde it-opslagplaats met Cloud Manager, waaronder:

* [Beginsynchronisatie](#initial-sync)
* [Basisvertakkingsstrategie](#branching-strategy)
* [Ontwikkeling van de functiescherm](#feature-development)
* [Implementatie van productie](#production-deployment)
* [Releasetags synchroniseren](#sync-tags)

De videoreeks veronderstelt een basiskennis van git en broncontrolebeheer. Zie de [ extra middelen hieronder ](#additional-resources) voor meer details op git.

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

De stappen en naamgevingsconventies die in deze videoreeks worden beschreven, zijn enkele aanbevolen werkwijzen voor het werken met een door de klant beheerde it-opslagplaats in Cloud Manager. Verwacht wordt dat de getoonde conventies en workflows zijn aangepast voor individuele gevallen van gebruik.

## Eerste synchronisatie {#initial-sync}

In deze video leert u de eerste stappen voor het synchroniseren van een door de klant beheerde Git-opslagplaats met de Cloud Manager Git-opslagplaats.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Basisvertakkingsstrategie {#branching-strategy}

In deze video leert u basisvertakkingsstrategieën.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Ontwikkeling van filialen {#feature-development}

Gebruik een eigenschapvertakking om codeveranderingen in een klant-beheerde git bewaarplaats te isoleren en met Cloud Manager te synchroniseren git bewaarplaats om een niet productiepijplijn voor codekwaliteit en bevestigingstests te gebruiken.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Implementatie van productie {#production-deployment}

Code voorbereiden voor een productieleserie in een door de klant beheerde it-opslagplaats en synchroniseren met de Cloud Manager git-opslagplaats om deze te implementeren in werkgebied- en productieomgevingen.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Release-labels synchroniseren {#sync-tags}

Synchroniseer releasetags van een Cloud Manager-it-opslagplaats naar een door de klant beheerde it-opslagplaats, zodat u kunt zien welke code is geïmplementeerd in testomgevingen en productieomgevingen.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Aanvullende bronnen {#additional-resources}

* [ Middelen GitHub ](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
* [ Atlassiaanse Zelfstudies van de Git ](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [ Git Cheat Sheet ](https://education.github.com/git-cheat-sheet-education.pdf)
