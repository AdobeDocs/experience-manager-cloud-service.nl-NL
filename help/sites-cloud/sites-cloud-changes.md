---
title: Opvallende wijzigingen in AEM-sites in AEM Cloud Service
description: 'Opvallende wijzigingen in AEM-sites in AEM Cloud Service '
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Opvallende wijzigingen in AEM-sites als cloudservice {#notable-changes}

AEM Sites as a Cloud Service biedt mogelijkheden voor ervaringsbeheer als onderdeel van de native AEM voor de cloud als een Cloud Service-platform. Naast de belangrijkste voordelen van AEM als cloudservice, zoals eigen schaalbaarheid in de cloud, uptime en altijd up-to-date, biedt AEM-sites als cloudservice ook een aantal specifieke wijzigingen en toevoegingen voor sites.

>[!NOTE]
>In dit document worden de belangrijkste wijzigingen in AEM-sites gemarkeerd. Zie voor algemene wijzigingen in AEM in de cloud:
>
>* [Opmerkelijke wijzigingen in Adobe Experience Manager (AEM) als cloudservice](/help/release-notes/aem-cloud-changes.md)


Wijzigingen en toevoegingen in AEM-sites als Cloud Service zijn als volgt:

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

[WKND](https://wknd.site/), een nieuwe AEM-referentiesite, is bijgewerkt en gepubliceerd met de best practices voor het samenstellen van een website met AEM en de uitgebreide reeks mogelijkheden, componenten en implementatiemodellen die beschikbaar zijn in AEM. De nieuwe verwijzingsplaats en het [begeleidende leerprogramma](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) behandelen fundamentele onderwerpen zoals projectopstelling, de Componenten van de Kern, Bewerkbare Malplaatjes, cliëntbibliotheken, en componentenontwikkeling met de Plaatsen van de Manager van de Ervaring van Adobe.

Eerder, werd Wij.Retail geïnstalleerd door gebrek met AEM (behalve wanneer begonnen op productiemodus).  Een referentiesite wordt nu standaard niet geïnstalleerd.  In plaats daarvan wordt de [git-repo](https://github.com/adobe/aem-guides-wknd/) en de [bijbehorende zelfstudie](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) met de bijgewerkte WKND-referentiesite vermeld.

## Mogelijkheden niet beschikbaar bij uitvoering {#capabilities-not-available-at-runtime}

AEM als cloudservice is altijd ingeschakeld en altijd up-to-date. Om dit te bereiken, moet de AEM-opslagplaats worden gescheiden in onveranderbare en veranderbare inhoud en moet toegang tot onveranderlijke inhoud tijdens runtime worden verboden. Zie [Mutable versus Immuable Areas van de Repository](/help/implementing/developing/introduction/aem-project-content-package-structure.md#mutable-vs-immutable)voor meer informatie over muteerbare versus onveranderlijke inhoud.

Aangezien onveranderlijke inhoud niet toegankelijk is bij uitvoering, zijn de volgende bewerkingen voor AEM-sites niet beschikbaar bij uitvoering:

* i18n-woordenboekvertaling
* Modus voor ontwikkelaars in de AEM Sites Page Editor

Deze mogelijkheden kunnen via lokale, zelfstandige ontwikkelaarsinstanties van AEM als Cloud Service worden gebruikt voor het bijwerken van inhoud en code in de AEM als een GIT-opslagplaats voor cloudservice, maar niet in gehoste runtime-instanties.
