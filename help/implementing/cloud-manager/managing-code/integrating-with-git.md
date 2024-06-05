---
title: Git gebruiken met Cloud Manager
description: Leer hoe u de git-opslagruimten van Cloud Manager kunt gebruiken en hoe u uw eigen, door de klant beheerde git-opslagruimte op locatie kunt integreren met Cloud Manager.
exl-id: 57e71b8a-4546-4d7f-825c-a1637d08e608
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Git gebruiken met Cloud Manager {#git-integration}

Adobe Cloud Manager wordt geleverd met één git-opslagplaats die wordt gebruikt om code te implementeren via de CI/CD-leidingen van Cloud Manager.

U kunt de git-opslagplaats van Cloud Manager uit de doos gebruiken, maar u kunt ook een door de klant beheerde git-opslagplaats integreren met Cloud Manager.

## Overzicht van GIT-integratie {#git-integration-overview}

Deze videoreeks verkent verschillende gebruiksgevallen bij de integratie van een door de klant beheerde it-opslagplaats met Cloud Manager, waaronder:

* [Beginsynchronisatie](#initial-sync)
* [Basisvertakkingsstrategie](#branching-strategy)
* [Ontwikkeling van de functiescherm](#feature-development)
* [Implementatie van productie](#production-deployment)
* [Releasetags synchroniseren](#sync-tags)

De videoreeks veronderstelt een basiskennis van git en broncontrolebeheer. Zie de [extra bronnen onder](#additional-resources) voor meer informatie over git .

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

De stappen en naamconventies die in deze videoreeks worden beschreven, zijn enkele aanbevolen werkwijzen voor het werken met een door de klant beheerde it-opslagplaats in Cloud Manager. Verwacht wordt dat de getoonde conventies en workflows zijn aangepast voor individuele gevallen van gebruik.

## Beginsynchronisatie {#initial-sync}

In deze video leert u de eerste stappen voor het synchroniseren van een door de klant beheerde Git-opslagplaats met de Git-opslagplaats van Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Basisvertakkingsstrategie {#branching-strategy}

In deze video leert u basisvertakkingsstrategieën.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Ontwikkeling van de functiescherm {#feature-development}

Gebruik een eigenschapvertakking om codeveranderingen in een klant-beheerde git bewaarplaats te isoleren en met de git bewaarplaats van de Manager van de Wolk te synchroniseren om een niet productiepijplijn voor codekwaliteit en bevestigingstests te gebruiken.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Implementatie van productie {#production-deployment}

Code voorbereiden voor een productievrijgave in een door de klant beheerde it-opslagplaats en synchroniseren met de git-opslagplaats van Cloud Manager om te implementeren in werkgebied- en productieomgevingen.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Releasetags synchroniseren {#sync-tags}

Synchroniseer releasetags van een cloudbeheeropslagplaats naar een door de klant beheerde it-opslagplaats om te bepalen welke code is geïmplementeerd in testomgevingen en productieomgevingen.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Aanvullende bronnen {#additional-resources}

* [GitHub-bronnen](https://try.github.io)
* [Atlassiaanse Tutorials](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
