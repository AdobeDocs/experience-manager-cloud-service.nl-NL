---
title: Integreren met Git
description: Integreren met Git - Cloud Services
exl-id: 57e71b8a-4546-4d7f-825c-a1637d08e608
source-git-commit: 21669a29fbfd1072b637f407f5220825c4d1edbb
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 2%

---

# Git integreren met Adobe Cloud Manager {#git-integration}

Adobe Cloud Manager wordt geleverd met één git-opslagplaats die wordt gebruikt om code te implementeren via de CI/CD-leidingen van Cloud Manager. Klanten kunnen de git-opslagruimte van Cloud Manager uit de doos gebruiken. Klanten hebben ook de mogelijkheid om een on-premise of **door de klant beheerde** git-opslagplaats te integreren met Cloud Manager.

## Overzicht van GIT-integratie {#git-integration-overview}

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

In deze videoreeks worden verschillende gebruiksgevallen besproken met betrekking tot de integratie van een door de klant beheerde git-opslagplaats met Cloud Manager, waaronder:

* [Beginsynchronisatie](#initial-sync)
* [Basisvertakkingsstrategie](#branching-strategy)
* [Ontwikkeling van de functiescherm](#feature-development)
* [Implementatie van productie](#production-deployment)
* [Releasetags synchroniseren](#sync-tags)

De videoreeks veronderstelt een basiskennis van git en broncontrolebeheer. Zie de [aanvullende bronnen onder](#additional-resources) voor meer informatie over git.

>[!NOTE]
>
>De stappen en naamgevingsconventies die in deze videoreeks worden beschreven, zijn enkele aanbevolen werkwijzen voor het werken met een door de klant beheerde git-opslagplaats en Cloud Manager. Verwacht wordt dat de getoonde conventies en workflows zullen worden aangepast voor individuele ontwikkelingsteams.

## Beginsynchronisatie {#initial-sync}

Eerste stappen voor het synchroniseren van een door de klant beheerde Git-opslagplaats met de Git-opslagplaats van Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Basisvertakkingsstrategie {#branching-strategy}

Volg de onderstaande video om de basisvertakkingsstrategieën te leren.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Ontwikkeling van de functiescherm {#feature-development}

Gebruik een eigenschapvertakking om codeveranderingen in een klant-beheerde git bewaarplaats te isoleren en met de git bewaarplaats van de Manager van de Wolk te synchroniseren om een niet productiepijplijn voor codekwaliteit en bevestigingstests te gebruiken.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Implementatie van productie {#production-deployment}

Code voorbereiden voor een productievrijgave in een door de klant beheerde it-opslagplaats en synchroniseren met de git-opslagplaats van Cloud Manager om te implementeren in werkgebied- en productieomgevingen.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Releasetags synchroniseren {#sync-tags}

Synchroniseer releasetags van een cloudbeheeropslagplaats naar een door de klant beheerde it-opslagplaats om te bepalen welke code is geïmplementeerd in werkgebied- en productieomgevingen.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Aanvullende bronnen {#additional-resources}

* [GitHub-bronnen](https://try.github.io)
* [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
