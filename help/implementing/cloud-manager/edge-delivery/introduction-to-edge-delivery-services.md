---
title: Inleiding tot Edge Delivery Services in Cloud Manager
description: Leer hoe u Cloud Manager-projecten kunt leveren met behulp van Edge Delivery Services.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: abd0fa0ea3e6e18187bcb60731ec6fe823a98e45
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 1%

---


# Inleiding tot Edge Delivery Services in Cloud Manager {#edge-delivery-services}

Edge Delivery Services is een samenstellbare set services die u in staat stelt om op zeer flexibele wijze inhoud op uw website te schrijven. Op deze manier kunt u het volgende doen:

* Maak snelle sites met een perfecte Lighthouse Score.
* Bewaking van de prestaties voortdurend via RUM (Real Use Monitoring).
* Verhoog de efficiëntie bij het ontwerpen door inhoudsbronnen te ontkoppelen.

U kunt zowel AEM inhoudsbeheer als WYSIWYG-authoring gebruiken met de Universal Editor en op document gebaseerde authoring.

Met Cloud Manager in AEM as a Cloud Service kunt u Edge Delivery Service inschakelen voor uw project.

>[!TIP]
>
>Voor details over Edge Delivery Services en hoe het met AEM kan worden gebruikt, zie het [ overzicht van Edge Delivery Services ](/help/edge/overview.md).

## Edge Delivery Services in Cloud Manager {#edge-in-cloud-manager}

Als u Edge Delivery Services als deel van Adobe Experience Manager Sites vergunning hebt gegeven, kunt u aan boord uw plaats met Edge Delivery Services direct in Cloud Manager en gaan levend [ gebruikend een geleide, zelfbediening ervaring ](/help/implementing/cloud-manager/managing-code/private-repositories.md).

Bovendien kunt u tot een verenigde ervaring toegang hebben voor het beheren van al uw AEM eigenschappen terwijl het verzekeren van consistentie over zeer belangrijke werkschema&#39;s. Deze workflows omvatten domeinnaambeheer, SSL-certificaatbeheer en CDN-toewijzingen.

## Voordelen van het gebruik van het aanbevolen pad voor Adoben {#recommended-path-eds}

Maximaliseer uw voordelen van Adobe door uw licentie voor Edge Delivery Services te openen en te gebruiken via Cloud Manager. Als u dit doet, kunt u verschillende belangrijke voordelen benutten.

* [ Verbruik uw vergunning op uw gekozen programma ](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md), of [ werk andere programma&#39;s ](/help/implementing/cloud-manager/edge-delivery/manage-edge-delivery-sites.md) bij, of allebei.
* Haal voordeel uit [ API-eerste ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) voordelen voor het uitvoeren van (creeer, Gelezen, Update, Schrapping) verrichtingen CRUD.
* [ Toegang SLA die ](/help/implementing/cloud-manager/sla-reporting.md) meldt (*binnenkort komt*)
* [ de toegang van de winst tot de steun van de Adobe ](/help/edge/overview.md#support-ticket) voor uw geregistreerde productieprogramma&#39;s.

Bovendien het gebruiken van Cloud Manager laat u [ beheerde Adobe CDN ](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) voor uw plaats van Edge Delivery gebruiken en uit zeer belangrijke voordelen zoals zelfbediening CDN beheer, met inbegrip van de configuratie en de toevoeging van DV certificaten voordeel halen. Bovendien, nadat een DV- certificaat wordt gecreeerd, vernieuwt de Adobe het automatisch om de drie maanden, tenzij het wordt geschrapt. Als u geen Edge Delivery Services vergunning met Adobe hebt en besluit om deze voordelen over te slaan, kunt u uw zelf-beheerde CDN slechts gebruiken. Deze opstelling moet op het [`aem.live` platform ](https://www.aem.live/docs/go-live-checklist#cdn-configuration) zijn.

## Edge Delivery Services toevoegen aan een productieprogramma of sandboxprogramma

Een Edge Delivery Services kan op verschillende manieren worden toegevoegd afhankelijk van hoe u met uw project bent begonnen.

| Hoofdletters gebruiken | Beschrijving |
| --- | --- |
| Ik wil Edge Delivery Services toevoegen aan een nieuw productieprogramma. | Zie [ productieprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) creëren.<br> in de tovenaar, onder het **Oplossingen &amp; toe:voegen-ons** lusje, uitgezochte **Edge Delivery Services**. |
| Ik wil Edge Delivery Services toevoegen aan een bestaand productieprogramma. | Zie [ programma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) uitgeven.<br> in **geef de dialoogdoos van het Programma** uit, onder het **Oplossingen &amp; toe:voegen-ons** lusje, uitgezochte **Edge Delivery Services**. |
| Ik wil een Edge Delivery-site toevoegen aan Cloud Manager | Zie [ een plaats van Edge Delivery ](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) toevoegen. |
| Ik wil Edge Delivery Services toevoegen aan een nieuw of bestaand sandboxprogramma. | Zie [ zandbakprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) creëren.<br> wanneer u een zandbakprogramma creeert, worden de Edge Delivery Services toegevoegd aan het programma door gebrek; u te hoeven niet om het te selecteren.<br> Bestaande zandbakprogramma&#39;s voorafgaand aan de algemene beschikbaarheid van Edge Delivery, erven automatisch Edge Delivery Services. |

>[!NOTE]
>
>* Om programma&#39;s toe te voegen of uit te geven, moet u een lid van de **rol van de Bedrijfs Eigenaar {zijn 0} of toestemming worden gegeven om dit te doen.**
>* Uw organisatie moet een licentie voor ongebruikte Edge Delivery Services hebben voordat deze kan worden toegepast op een productieprogramma.
>* Zodra de vergunning van Edge Delivery Services wordt toegepast op of uit een programma verwijderd, wordt de verandering onmiddellijk van kracht zonder de behoefte om een pijpleiding in werking te stellen.


## De Edge Delivery-lijst met taken {#ed-todo-list}

<!-- &#x2460; for "1" inside circle -->

De **Edge Delivery om lijst** te doen is een onboarding taak controlelijst die wordt bedoeld om u door onboarding te begeleiden, uw plaats van Edge Delivery te beheren al manier aan [ gaan-Levend ](/help/journey-onboarding/go-live-checklist.md).

![ de plaats van Edge Delivery om lijst ](/help/implementing/cloud-manager/assets/cm-eds-todo-list.png) te doen

|   | Taak | Beschrijving |
| --- | --- | --- |
| 1 | Deelnemen aan het samenwerkingskanaal voor producten | Het klikken **legt nu verzoek voor** legt een verzoek aan Adobe voor om een kanaal voor uw bedrijf tot stand te brengen. Als het kanaal reeds bestaat, door:sturen u aan het kanaal van uw bedrijf. |
| 2 | Volledige voorwaarden | Zie [ Mening die Begonnen leerprogramma ](https://www.aem.live/developer/tutorial) krijgen. |
| 3 | Edge Delivery-site toevoegen | Zie [ een plaats van Edge Delivery ](#eds-add-site) toevoegen. |
| 4 | Domein toevoegen | Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen. |
| 5 | SSL-certificaat toevoegen | Zie [ SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toevoegen. |
| 6 | De CDN van uw Edge Delivery-site configureren | Zie [ een configuratie CDN ](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) toevoegen. |
| 7 | Pushvalidatie instellen | Zie [ de dupbevestiging van de Opstelling voor een plaats van Edge Delivery ](/help/implementing/cloud-manager/edge-delivery/cdn-setup-push-invalidation.md). |
| 8 | Go-Live | Zie [ gaan-Levende checklist ](/help/edge/docs/go-live-checklist.md). |

>[!VIDEO](https://video.tv.adobe.com/v/3428020?learn=on)

## Een ondersteuningsticket vastleggen {#eds-support-ticket}

{{support-ticket}}



