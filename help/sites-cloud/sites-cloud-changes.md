---
title: Opvallende wijzigingen in AEM Sites in AEM Cloud Service
description: 'Opvallende wijzigingen in AEM Sites in AEM Cloud Service '
translation-type: tm+mt
source-git-commit: e381807d7c199113689304e9481dfe2022ee5f93
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 16%

---


# Belangrijke wijzigingen in AEM Sites as a Cloud Service {#notable-changes}

AEM Sites als Cloud Service biedt mogelijkheden voor ervaringsbeheer als onderdeel van de cloud-native AEM als Cloud Service-platform. Naast de belangrijkste voordelen van AEM als Cloud Service, zoals wolk-inheemse scalability, uptime, en altijd bijgewerkt zijn, verstrekt AEM Sites als Cloud Service ook een aantal plaatsen-specifieke veranderingen en toevoegingen.

>[!NOTE]
>In dit document worden de belangrijkste wijzigingen in AEM Sites gemarkeerd. Voor veranderingen algemeen aan AEM als Cloud Service, en andere modules, zie:
>
>* [Inleiding tot Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
>* An [Overview of AEM as a Cloud Service - What is New and What is Different](/help/overview/what-is-new-and-different.md)
>* De [architectuur](/help/core-concepts/architecture.md) van Adobe Experience Manager as a Cloud Service
>* [Belangrijke wijzigingen in AEM as a Cloud Service (releaseopmerkingen)](/help/release-notes/aem-cloud-changes.md)
>* [Belangrijke wijzigingen in AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)
>* [Inleiding tot AEM Assets as a Cloud Service](/help/assets/overview.md)
>* [Tutorials voor Adobe Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/overview.html)


De wijzigingen en toevoegingen in AEM Sites als Cloud Service zijn als volgt:

* [Asynchrone paginabewerkingen](#asynchronous-page-operations)
* [Nieuwe naslagsite en zelfstudie](#new-reference-site-and-tutorial)

## Asynchrone paginabewerkingen {#asynchronous-page-operations}

In AEM Cloud-service zijn bewerkingen die de gebruikersinterface van oudsher hebben geblokkeerd, opgedeeld in kleinere taken die op de achtergrond worden uitgevoerd.

* Pagina&#39;s verplaatsen
* Pagina&#39;s uitrollen

De initiatiefnemer van dergelijke acties kan hun status in een nieuwe UI bij `/mnt/overlay/dam/gui/content/asyncjobs.html` controleren.

>[!NOTE]
>
>De gebruiker van het systeem hoeft deze nieuwe functie niet te wijzigen. Het wordt hier eenvoudig genoteerd als verandering in gedrag van vorige on-premise versies van AEM.

## Nieuwe referentiesite en zelfstudie {#new-reference-site-and-tutorial}

[WKND](https://wknd.site/), een nieuwe AEM verwijzingsplaats, is bijgewerkt en gepubliceerd om beste praktijken te weerspiegelen voor om een website met AEM, en de uitvoerige reeks mogelijkheden, componenten, en plaatsingsmodellen te bouwen die in AEM beschikbaar zijn. De nieuwe verwijzingsplaats en [begeleidend leerprogramma](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) behandelen fundamentele onderwerpen zoals projectopstelling, de Componenten van de Kern, Bewerkbare Malplaatjes, cliëntbibliotheken, en componentenontwikkeling met Adobe Experience Manager Sites.

Eerder, werd Wij.Retail geïnstalleerd door gebrek met AEM (behalve wanneer begonnen op productiemodus).  Een referentiesite wordt nu standaard niet geïnstalleerd.  In plaats daarvan worden de [git repo](https://github.com/adobe/aem-guides-wknd/) en [flankerende zelfstudie](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) met de bijgewerkte WKND-referentiesite-code gegeven.

## Mogelijkheden niet beschikbaar bij uitvoering {#capabilities-not-available-at-runtime}

AEM als Cloud Service is altijd ingeschakeld en altijd up-to-date. Om dit te bereiken, moet de AEM opslagplaats in onveranderbare en veranderbare inhoud worden gescheiden, en moet toegang tot onveranderlijke inhoud bij runtime worden verboden. Zie [Mutable versus Immuable Area van de Repository](/help/implementing/developing/introduction/aem-project-content-package-structure.md#mutable-vs-immutable) voor meer informatie over muteerbare versus onveranderlijke inhoud.

Aangezien onveranderlijke inhoud niet toegankelijk is bij uitvoering, zijn de volgende AEM Sites-bewerkingen niet beschikbaar bij uitvoering:

* i18n-woordenboekvertaling
* Modus voor ontwikkelaars in de AEM Sites Page Editor

Deze mogelijkheden kunnen via lokale, zelfstandige instanties van ontwikkelaars van AEM als Cloud Service worden gebruikt, voor het bijwerken van inhoud en code in de AEM als Cloud Service GIT-opslagplaats, maar niet in gehoste runtime instanties.
