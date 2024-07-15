---
title: Opvallende wijzigingen in AEM Sites in AEM Cloud Service
description: Krijg inzicht in ontwerpen en beheren met AEM Sites as a Cloud Service en in het aanbrengen van opvallende wijzigingen aan AEM Sites in AEM Cloud Service.
exl-id: 60b1aec4-75a0-459f-bf77-8d8c1af757ce
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 15%

---


# Opvallende wijzigingen in AEM Sites as a Cloud Service {#notable-changes}

AEM Sites as a Cloud Service biedt mogelijkheden voor ervaringsbeheer als onderdeel van het AEM as a Cloud Service-platform in de cloud. Naast de belangrijkste voordelen van AEM as a Cloud Service, zoals cloud-native schaalbaarheid, uptime en altijd up-to-date zijn, biedt AEM Sites as a Cloud Service ook verschillende Sites-specifieke wijzigingen en toevoegingen.

>[!NOTE]
>In dit document worden de belangrijkste wijzigingen in AEM Sites gemarkeerd. Zie voor algemene wijzigingen in AEM as a Cloud Service en andere modules:
>
>* [Inleiding tot Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
>* Een [ Overzicht van AEM as a Cloud Service - wat Nieuw is en wat verschillend is ](/help/overview/what-is-new-and-different.md)
>* De [architectuur](/help/overview/architecture.md) van Adobe Experience Manager as a Cloud Service
>* [Belangrijke wijzigingen in AEM as a Cloud Service (releaseopmerkingen)](/help/release-notes/aem-cloud-changes.md)
>* [Belangrijke wijzigingen in AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)
>* [Inleiding tot AEM Assets as a Cloud Service](/help/assets/overview.md)
>* [Tutorials voor Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html)

Wijzigingen en toevoegingen in AEM Sites as a Cloud Service zijn als volgt:

* [Asynchrone paginabewerkingen](#asynchronous-page-operations)
* [Nieuwe naslagsite en zelfstudie](#new-reference-site-and-tutorial)

## Asynchrone paginabewerkingen {#asynchronous-page-operations}

In AEM Cloud-service zijn bewerkingen die de gebruikersinterface van oudsher hebben geblokkeerd, opgedeeld in kleinere taken die op de achtergrond worden uitgevoerd.

* Pagina&#39;s verplaatsen
* Pagina&#39;s uitrollen

De aanvrager van dergelijke acties kan zijn status in een nieuwe UI bij `/mnt/overlay/dam/gui/content/asyncjobs.html` controleren.

>[!NOTE]
>
>De gebruiker van het systeem hoeft deze nieuwe functie niet te wijzigen. Het wordt hier eenvoudig genoteerd als verandering in gedrag van vorige on-premise versies van AEM.

## Nieuwe naslagsite en zelfstudie {#new-reference-site-and-tutorial}

[ WKND ](https://wknd.site/), een nieuwe AEM verwijzingsplaats, is bijgewerkt en gepubliceerd om op beste praktijken te wijzen om een website met AEM, en met de uitvoerige reeks mogelijkheden, componenten, en plaatsingsmodellen te bouwen die in AEM beschikbaar zijn. De nieuwe verwijzingsplaats en [ begeleidende leerprogramma ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) behandelen fundamentele onderwerpen zoals projectopstelling, de Componenten van de Kern, editable malplaatjes, cliëntbibliotheken, en componentenontwikkeling met Adobe Experience Manager Sites.

Eerder, werd Wij.Retail geïnstalleerd door gebrek met AEM (behalve wanneer begonnen op productiemodus). In AEM as a Cloud Service is een referentiesite niet standaard geïnstalleerd. In plaats daarvan wordt de [ git repo ](https://github.com/adobe/aem-guides-wknd/) en [ begeleidende zelfstudie ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) met de bijgewerkte code van de WKND verwijzingsplaats verstrekt.

## Mogelijkheden niet beschikbaar bij uitvoering {#capabilities-not-available-at-runtime}

AEM as a Cloud Service is altijd actief en altijd up-to-date. Om dit te bereiken, moet de AEM opslagplaats in onveranderbare en veranderbare inhoud worden gescheiden, en moet toegang tot onveranderlijke inhoud bij runtime worden verboden. Voor meer details op mutable versus onveranderlijke inhoud zie [ Mutable versus Immuable Gebieden van de Bewaarplaats ](/help/implementing/developing/introduction/aem-project-content-package-structure.md#mutable-vs-immutable).

Aangezien onveranderlijke inhoud niet toegankelijk is bij uitvoering, zijn de volgende AEM Sites-bewerkingen niet beschikbaar bij uitvoering:

* i18n-woordenboekvertaling
* Modus voor ontwikkelaars in de AEM Sites Page Editor

Deze mogelijkheden kunnen worden gebruikt via lokale, zelfstandige ontwikkelaarsinstanties van AEM as a Cloud Service, voor het bijwerken van inhoud en code in de AEM as a Cloud Service GIT-opslagplaats, maar niet in gehoste runtime-instanties.
