---
title: Opvallende wijzigingen in AEM Sites in AEM Cloud Service
description: Opvallende wijzigingen in AEM Sites in AEM Cloud Service
exl-id: 60b1aec4-75a0-459f-bf77-8d8c1af757ce
source-git-commit: 8e06dff01e06ced62686a4784619278f29345082
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 15%

---


# Belangrijke wijzigingen in AEM Sites as a Cloud Service {#notable-changes}

AEM Sites as a Cloud Service biedt mogelijkheden voor ervaringsbeheer als onderdeel van het cloud-native AEM as a Cloud Service platform. Naast de belangrijkste voordelen van AEM as a Cloud Service, zoals wolkenkrabber-inheemse scalability, uptime, en altijd bijgewerkt zijn, verstrekt as a Cloud Service AEM Sites ook een aantal plaatsen-specifieke veranderingen en toevoegingen.

>[!NOTE]
>In dit document worden de belangrijkste wijzigingen in AEM Sites gemarkeerd. Voor veranderingen algemeen in AEM as a Cloud Service, en andere modules, zie:
>
>* [Inleiding tot Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
>* An [Overzicht van AEM as a Cloud Service - Wat is Nieuw en Wat is verschillend](/help/overview/what-is-new-and-different.md)
>* De [architectuur](/help/overview/architecture.md) van Adobe Experience Manager as a Cloud Service
>* [Belangrijke wijzigingen in AEM as a Cloud Service (releaseopmerkingen)](/help/release-notes/aem-cloud-changes.md)
>* [Belangrijke wijzigingen in AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)
>* [Inleiding tot AEM Assets as a Cloud Service](/help/assets/overview.md)
>* [Tutorials voor Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html)


De as a Cloud Service wijzigingen en toevoegingen in AEM Sites zijn als volgt:

* [Asynchrone paginabewerkingen](#asynchronous-page-operations)
* [Nieuwe naslagsite en zelfstudie](#new-reference-site-and-tutorial)

## Asynchrone paginabewerkingen {#asynchronous-page-operations}

In AEM Cloud-service zijn bewerkingen die de gebruikersinterface van oudsher hebben geblokkeerd, opgedeeld in kleinere taken die op de achtergrond worden uitgevoerd.

* Pagina&#39;s verplaatsen
* Pagina&#39;s uitrollen

De initiatiefnemer van dergelijke acties kan hun status in een nieuwe UI controleren op `/mnt/overlay/dam/gui/content/asyncjobs.html`.

>[!NOTE]
>
>De gebruiker van het systeem hoeft deze nieuwe functie niet te wijzigen. Het wordt hier eenvoudig genoteerd als verandering in gedrag van vorige on-premise versies van AEM.

## Nieuwe naslagsite en zelfstudie {#new-reference-site-and-tutorial}

[WKND](https://wknd.site/), is een nieuwe AEM referentiesite bijgewerkt en gepubliceerd met de beste werkwijzen om een website met AEM te bouwen, en met de uitgebreide reeks mogelijkheden, componenten, en plaatsingsmodellen die in AEM beschikbaar zijn. De nieuwe referentiesite en [begeleidend lesbestand](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) behandelt fundamentele onderwerpen zoals projectopstelling, de Componenten van de Kern, editable malplaatjes, cliëntbibliotheken, en componentenontwikkeling met Adobe Experience Manager Sites.

Eerder, werd Wij.Retail geïnstalleerd door gebrek met AEM (behalve wanneer begonnen op productiemodus). In AEM as a Cloud Service wordt een referentiesite niet standaard geïnstalleerd. In plaats daarvan [git repo](https://github.com/adobe/aem-guides-wknd/) en [begeleidend lesbestand](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) met de bijgewerkte WKND-referentiesite.

## Mogelijkheden niet beschikbaar bij uitvoering {#capabilities-not-available-at-runtime}

AEM as a Cloud Service is altijd ingeschakeld en altijd up-to-date. Om dit te bereiken, moet de AEM opslagplaats in onveranderbare en veranderbare inhoud worden gescheiden, en moet toegang tot onveranderlijke inhoud bij runtime worden verboden. Zie voor meer informatie over muteerbare versus onveranderlijke inhoud [Mutable versus Immuable Areas of the Repository](/help/implementing/developing/introduction/aem-project-content-package-structure.md#mutable-vs-immutable).

Aangezien onveranderlijke inhoud niet toegankelijk is bij uitvoering, zijn de volgende AEM Sites-bewerkingen niet beschikbaar bij uitvoering:

* i18n-woordenboekvertaling
* Modus voor ontwikkelaars in de AEM Sites Page Editor

Deze mogelijkheden kunnen worden gebruikt via lokale, zelfstandige instanties voor ontwikkelaars van AEM as a Cloud Service, voor het bijwerken van inhoud en code in de AEM as a Cloud Service GIT-opslagplaats, maar niet in gehoste runtime-instanties.
