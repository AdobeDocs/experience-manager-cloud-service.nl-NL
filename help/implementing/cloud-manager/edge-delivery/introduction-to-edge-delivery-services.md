---
title: Inleiding tot Edge Delivery Services in Cloud Manager
description: Leer hoe je Cloud Manager-projecten kunt leveren met Edge Delivery Services.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 086aaf323291279d0782c71982baa1a5867784a1
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 1%

---


# Inleiding tot Edge Delivery Services in Cloud Manager {#edge-delivery-services}

Edge Delivery Services is een set services die u kunt samenstellen en waarmee u een hoge mate van flexibiliteit hebt bij het schrijven van inhoud op uw website. Op deze manier kunt u het volgende doen:

* Maak snelle sites met een perfecte Lighthouse Score.
* Bewaking van de prestaties voortdurend via RUM (Real Use Monitoring).
* Verhoog de efficiëntie bij het ontwerpen door inhoudsbronnen te ontkoppelen.

U kunt zowel AEM-inhoudsbeheer als WYSIWYG-authoring gebruiken met behulp van de Universal Editor en documentgebaseerde authoring.

Met Cloud Manager in AEM as a Cloud Service kunt u Edge Delivery Service inschakelen voor uw project.

>[!TIP]
>
>Voor details over Edge Delivery Services en hoe het met AEM kan worden gebruikt, zie het [ overzicht van Edge Delivery Services ](/help/edge/overview.md).

## Over Edge Delivery Services in Cloud Manager {#edge-in-cloud-manager}

Als u Edge Delivery Services als deel van Adobe Experience Manager Sites vergunning hebt gegeven, kunt u aan boord uw plaats met Edge Delivery Services direct in Cloud Manager en gaan levend [ gebruikend een geleide, zelfbediening ervaring ](/help/implementing/cloud-manager/managing-code/private-repositories.md).

Daarnaast hebt u toegang tot één ervaring voor het beheer van al uw AEM-eigenschappen, terwijl u zorgt voor consistentie tussen belangrijke workflows. Deze workflows omvatten domeinnaambeheer, SSL-certificaatbeheer en CDN-toewijzingen.

## Voordelen van het door Adobe aanbevolen pad voor Edge Delivery Services {#recommended-path-eds}

Maximaliseer uw voordelen van Adobe door uw Edge Delivery Services-licentie te openen en te gebruiken via Cloud Manager. Als u dit doet, kunt u verschillende belangrijke voordelen benutten.

* [ Verbruik uw vergunning op uw gekozen programma ](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md), of [ werk andere programma&#39;s ](/help/implementing/cloud-manager/edge-delivery/manage-edge-delivery-sites.md) bij, of allebei.
* Haal voordeel uit [ API-eerste ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) voordelen voor het uitvoeren van (creeer, Gelezen, Update, Schrapping) verrichtingen CRUD.
* [ Toegang SLA die ](/help/implementing/cloud-manager/sla-reporting.md) meldt (*binnenkort komt*)
* [ de toegang van de winst tot de steun van Adobe ](/help/edge/overview.md#support-ticket) voor uw geregistreerde productieprogramma&#39;s.

Bovendien het gebruiken van Cloud Manager laat u [ Adobe beheerde CDN ](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) voor uw plaats van Edge Delivery gebruiken en uit zeer belangrijke voordelen zoals zelfbediening CDN beheer, met inbegrip van de configuratie en de toevoeging van DV certificaten voordeel halen. Bovendien vernieuwt Adobe het DV-certificaat na het maken ervan automatisch elke drie maanden, tenzij het wordt verwijderd. Als u geen Edge Delivery Services-licentie voor Adobe hebt en besluit deze voordelen te omzeilen, kunt u alleen uw eigen CDN gebruiken. Deze opstelling moet op het [`aem.live` platform ](https://www.aem.live/docs/go-live-checklist#cdn-configuration) zijn.

## Informatie over het toevoegen van Edge Delivery Services aan een productieprogramma of sandboxprogramma

Een Edge Delivery Services kan op verschillende manieren worden toegevoegd, afhankelijk van de manier waarop u met uw project bent begonnen of wanneer u de site wilt maken.

| Hoofdletters gebruiken | Beschrijving |
| --- | --- |
| Ik wil Edge Delivery Services toevoegen aan een nieuw productieprogramma. | Zie [ productieprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) creëren.<br> in de tovenaar, onder het **Oplossingen &amp; toe:voegen-ons** lusje, uitgezochte **Edge Delivery Services**. |
| Ik wil Edge Delivery Services toevoegen aan een bestaand productieprogramma. | Zie [ programma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) uitgeven.<br> in **geef de dialoogdoos van het Programma** uit, onder het **Oplossingen &amp; toe:voegen-ons** lusje, uitgezochte **Edge Delivery Services**. |
| Ik wil een Edge Delivery-site toevoegen aan Cloud Manager | Zie [ een plaats van Edge Delivery ](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) toevoegen. |
| Ik wil nu een Edge Delivery-site maken | Zie [ snel een plaats van Edge Delivery in Cloud Manager met de klik van een knoop ](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md) creëren. |
| Ik wil Edge Delivery Services toevoegen aan een nieuw of bestaand sandboxprogramma. | Zie [ zandbakprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) creëren.<br> wanneer u een zandbakprogramma creeert, wordt Edge Delivery Services toegevoegd aan het programma door gebrek; u te hoeven niet om het te selecteren.<br> Bestaande zandbakprogramma&#39;s voorafgaand aan de algemene beschikbaarheid van Edge Delivery, erven automatisch Edge Delivery Services. |

>[!NOTE]
>
>* Om programma&#39;s toe te voegen of uit te geven, moet u een lid van de **rol van de Bedrijfs Eigenaar {zijn 0} of toestemming worden gegeven om dit te doen.**
>* Uw organisatie moet een ongebruikte Edge Delivery Services-licentie hebben voordat deze kan worden toegepast op een productieprogramma.
>* Zodra de Edge Delivery Services-licentie wordt toegepast op of verwijderd uit een programma, wordt de wijziging onmiddellijk van kracht zonder dat een pijpleiding hoeft te worden uitgevoerd.


## De Edge Delivery-lijst voor te doen in Cloud Manager {#ed-todo-list}

<!-- &#x2460; for "1" inside circle -->

De **Edge Delivery om lijst** in Cloud Manager te doen is een onboarding taak controlelijst die wordt bedoeld om u door onboarding te begeleiden, die uw plaats van Edge Delivery helemaal beheren aan [ gaan-Levend ](/help/journey-onboarding/go-live-checklist.md).

![ de plaats van Edge Delivery om lijst in Cloud Manager te doen.](/help/implementing/cloud-manager/assets/cm-eds-todo-list.png)

|   | Taak | Beschrijving |
| --- | --- | --- |
| 1 | Deelnemen aan het samenwerkingskanaal voor producten | Het klikken **legt nu verzoek** voor een verzoek aan Adobe om een kanaal voor uw bedrijf tot stand te brengen. Als het kanaal reeds bestaat, door:sturen u aan het kanaal van uw bedrijf. |
| 2 | Volledige voorwaarden | Zie [ Mening die Begonnen leerprogramma ](https://www.aem.live/developer/tutorial) krijgen. |
| 3 | Edge Delivery-site toevoegen OF <br> Site maken | Zie [ een plaats van Edge Delivery ](#eds-add-site) toevoegen.<br> zie [ een plaats van Edge Delivery in Cloud Manager ](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md) creëren. |
| 4 | Domein toevoegen | Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen. |
| 5 | SSL-certificaat toevoegen | Zie [ SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toevoegen. |
| 6 | De CDN van uw Edge Delivery-site configureren | Zie [ een configuratie CDN ](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) toevoegen. |
| 7 | Pushvalidatie instellen | Zie [ de dupbevestiging van de Opstelling voor een plaats van Edge Delivery ](/help/implementing/cloud-manager/edge-delivery/cdn-setup-push-invalidation.md). |
| 8 | Go-Live | Zie [ gaan-Levende checklist ](/help/edge/docs/go-live-checklist.md). |

>[!VIDEO](https://video.tv.adobe.com/v/3428020?learn=on)

## Een ondersteuningsticket vastleggen {#eds-support-ticket}

{{support-ticket}}



