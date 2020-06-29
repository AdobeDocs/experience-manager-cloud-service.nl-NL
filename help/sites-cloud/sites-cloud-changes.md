---
title: Opvallende wijzigingen in AEM Sites in AEM Cloud Service
description: 'Opvallende wijzigingen in AEM Sites in AEM Cloud Service '
translation-type: tm+mt
source-git-commit: e381807d7c199113689304e9481dfe2022ee5f93
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 11%

---


# Belangrijke wijzigingen in AEM Sites as a Cloud Service {#notable-changes}

AEM Sites als Cloud Service bieden mogelijkheden voor ervaringsbeheer als onderdeel van de in de cloud geïntegreerde AEM als een Cloud Service-platform. Naast de belangrijkste voordelen van AEM als Cloud Service, zoals wolk-inheemse scalability, uptime, en altijd bijgewerkt zijn, verstrekken de AEM Sites als Cloud Service ook een aantal plaatsen-specifieke veranderingen en toevoegingen.

>[!NOTE]
>In dit document worden de belangrijkste wijzigingen in de AEM Sites gemarkeerd. Voor veranderingen algemeen in AEM als Cloud Service, en andere modules, zie:
>
>* [Inleiding tot Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
>* Een [overzicht van AEM als Cloud Service - wat Nieuw is en wat verschillend is](/help/overview/what-is-new-and-different.md)
>* De [architectuur](/help/core-concepts/architecture.md) van Adobe Experience Manager as a Cloud Service
>* [Opvallende wijzigingen in AEM als Cloud Service (opmerkingen bij de release)](/help/release-notes/aem-cloud-changes.md)
>* [Opvallende wijzigingen in AEM Assets als Cloud Service](/help/assets/assets-cloud-changes.md)
>* [AEM Assets introduceren als Cloud Service](/help/assets/overview.md)
>* [Zelfstudies voor Adobe Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/overview.html)


Wijzigingen en toevoegingen in AEM Sites als Cloud Service zijn als volgt:

* [Asynchrone paginabewerkingen](#asynchronous-page-operations)
* [Nieuwe naslagsite en zelfstudie](#new-reference-site-and-tutorial)

## Asynchrone paginabewerkingen {#asynchronous-page-operations}

In de AEM Cloud-service zijn bewerkingen die de gebruikersinterface van oudsher hebben geblokkeerd, opgedeeld in kleinere taken die op de achtergrond worden uitgevoerd.

* Pagina&#39;s verplaatsen
* Pagina&#39;s uitrollen

De initiatiefnemer van dergelijke acties kan hun status in een nieuwe UI bij controleren `/mnt/overlay/dam/gui/content/asyncjobs.html`.

>[!NOTE]
>
>De gebruiker van het systeem hoeft deze nieuwe functie niet te wijzigen. Het wordt hier eenvoudig vermeld als een verandering in gedrag van vorige op-premise versies van AEM.

## Nieuwe naslagsite en zelfstudie {#new-reference-site-and-tutorial}

[WKND](https://wknd.site/), een nieuwe AEM-referentiesite, is bijgewerkt en gepubliceerd met de best practices voor het samenstellen van een website met AEM en de uitgebreide reeks mogelijkheden, componenten en implementatiemodellen die beschikbaar zijn in AEM. De nieuwe verwijzingsplaats en het [begeleidende leerprogramma](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) behandelen fundamentele onderwerpen zoals projectopstelling, de Componenten van de Kern, Bewerkbare Malplaatjes, cliëntbibliotheken, en componentenontwikkeling met de Plaatsen van de Adobe Experience Manager.

Eerder, werd Wij.Retail geïnstalleerd door gebrek met AEM (behalve wanneer begonnen op productiemodus).  Een referentiesite wordt nu standaard niet geïnstalleerd.  In plaats daarvan wordt de [git-repo](https://github.com/adobe/aem-guides-wknd/) en de [bijbehorende zelfstudie](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) met de bijgewerkte WKND-referentiesite vermeld.

## Mogelijkheden niet beschikbaar bij uitvoering {#capabilities-not-available-at-runtime}

AEM als Cloud Service is altijd ingeschakeld en altijd up-to-date. Om dit te bereiken, moet de AEM-opslagplaats worden gescheiden in onveranderbare en veranderbare inhoud en moet toegang tot onveranderlijke inhoud tijdens runtime worden verboden. Zie [Mutable versus Immuable Areas van de Repository](/help/implementing/developing/introduction/aem-project-content-package-structure.md#mutable-vs-immutable)voor meer informatie over muteerbare versus onveranderlijke inhoud.

Aangezien onveranderlijke inhoud niet toegankelijk is bij uitvoering, zijn de volgende AEM Sites niet beschikbaar bij uitvoering:

* i18n-woordenboekvertaling
* Modus Ontwikkelaar in AEM Sites Pagina-editor

Deze mogelijkheden kunnen via lokale, zelfstandige instanties voor ontwikkelaars van AEM als Cloud Service worden gebruikt voor het bijwerken van inhoud en code in de AEM als Cloud Service GIT-opslagplaats, maar niet in gehoste runtime-instanties.
