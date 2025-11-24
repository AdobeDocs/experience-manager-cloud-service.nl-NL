---
title: Inleiding tot Edge Delivery Services in Cloud Manager
description: Leer hoe je Cloud Manager-projecten kunt leveren met Edge Delivery Services.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 897f6376c594604527231f6f5a05a8b85d6858f3
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 1%

---


# Inleiding tot Edge Delivery Services in Cloud Manager {#edge-delivery-services}

Edge Delivery Services is een set services die u kunt samenstellen en waarmee u een hoge mate van flexibiliteit hebt bij het schrijven van inhoud op uw website. Op deze manier kunt u het volgende doen:

* Maak snelle sites met een perfecte Lighthouse Score.
* De prestaties continu bewaken via Operationele Telemetrie.
* Verhoog de efficiëntie bij het ontwerpen door inhoudsbronnen te ontkoppelen.

U kunt zowel AEM-inhoudsbeheer als WYSIWYG-authoring gebruiken met behulp van de Universal Editor en documentgebaseerde authoring.

Met Cloud Manager in AEM as a Cloud Service kunt u Edge Delivery Service inschakelen voor uw project.

>[!TIP]
>
>Voor details over Edge Delivery Services en hoe het met AEM kan worden gebruikt, zie het [&#x200B; overzicht van Edge Delivery Services &#x200B;](/help/edge/overview.md).

## Over Edge Delivery Services in Cloud Manager {#edge-in-cloud-manager}

Als u Edge Delivery Services als deel van Adobe Experience Manager Sites vergunning hebt gegeven, kunt u aan boord uw plaats met Edge Delivery Services direct in Cloud Manager en gaan levend [&#x200B; gebruikend een geleide, zelfbediening ervaring &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).

Daarnaast hebt u toegang tot één ervaring voor het beheer van al uw AEM-eigenschappen, terwijl u zorgt voor consistentie tussen belangrijke workflows. Deze workflows omvatten domeinnaambeheer, SSL-certificaatbeheer en CDN-toewijzingen.

## Voordelen van het door Adobe aanbevolen pad voor Edge Delivery Services {#recommended-path-eds}

Maximaliseer uw voordelen van Adobe door uw Edge Delivery Services-licentie te openen en te gebruiken via Cloud Manager. Als u dit doet, kunt u verschillende belangrijke voordelen benutten.

* [&#x200B; Verbruik uw vergunning op uw gekozen programma &#x200B;](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md), of [&#x200B; werk andere programma&#39;s &#x200B;](/help/implementing/cloud-manager/edge-delivery/manage-edge-delivery-sites.md) bij, of allebei.
* Haal voordeel uit [&#x200B; API-eerste &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/) voordelen voor het uitvoeren van (creeer, Gelezen, Update, Schrapping) verrichtingen CRUD.
* [SLA-rapportage openen](/help/implementing/cloud-manager/reports/report-sla.md)
* [&#x200B; de toegang van de winst tot de steun van Adobe &#x200B;](/help/edge/overview.md#support-ticket) voor uw geregistreerde productieprogramma&#39;s.

Als u een vergunning van Edge Delivery Services (EDS) hebt, kunt u een [&#x200B; Adobe-Beheerde CDN &#x200B;](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) voor uw plaats van Edge Delivery gebruiken. Dit laat zelfbediening CDN beheer en DV certificaten toe die automatisch om de drie maanden vernieuwen tenzij u het certificaat schrapt.

Als u ervoor kiest om uw CDN (een niet door Adobe beheerde CDN) te gebruiken, ongeacht uw Edge Delivery Services-licentie, moet u de CDN configureren op het `aem.live` -platform. Zie [&#x200B; BYO CDN Opstelling &#x200B;](https://www.aem.live/docs/byo-cdn-setup).


## Informatie over het toevoegen van Edge Delivery Services aan een productieprogramma of sandboxprogramma

Een Edge Delivery Services kan op verschillende manieren worden toegevoegd, afhankelijk van de manier waarop u met uw project bent begonnen of wanneer u de site wilt maken.

| Hoofdletters gebruiken | Beschrijving |
| --- | --- |
| Ik wil Edge Delivery Services toevoegen aan een nieuw productieprogramma. | Zie [&#x200B; productieprogramma&#39;s &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) creëren.<br> in de tovenaar, onder het **Oplossingen &amp; toe:voegen-ons** lusje, uitgezochte **Edge Delivery Services**. |
| Ik wil Edge Delivery Services toevoegen aan een bestaand productieprogramma. | Zie [&#x200B; programma&#39;s &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) uitgeven.<br> in **geef de dialoogdoos van het Programma** uit, onder het **Oplossingen &amp; toe:voegen-ons** lusje, uitgezochte **Edge Delivery Services**. |
| Ik wil een Edge Delivery-site toevoegen aan Cloud Manager | Zie [&#x200B; een plaats van Edge Delivery &#x200B;](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) toevoegen. |
| Ik wil nu een Edge Delivery-site maken | Zie [&#x200B; snel een plaats van Edge Delivery in Cloud Manager met de klik van een knoop &#x200B;](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md) creëren. |
| Ik wil Edge Delivery Services toevoegen aan een nieuw of bestaand sandboxprogramma. | Zie [&#x200B; zandbakprogramma&#39;s &#x200B;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) creëren.<br> wanneer u een zandbakprogramma creeert, wordt Edge Delivery Services toegevoegd aan het programma door gebrek; u te hoeven niet om het te selecteren.<br> Bestaande zandbakprogramma&#39;s voorafgaand aan de algemene beschikbaarheid van Edge Delivery, erven automatisch Edge Delivery Services. |

>[!NOTE]
>
>* Om programma&#39;s toe te voegen of uit te geven, moet u een lid van de **rol van de Bedrijfs Eigenaar {zijn 0} of toestemming worden gegeven om dit te doen.**
>* Uw organisatie moet een ongebruikte Edge Delivery Services-licentie hebben voordat deze kan worden toegepast op een productieprogramma.
>* Zodra de Edge Delivery Services-licentie wordt toegepast op of verwijderd uit een programma, wordt de wijziging onmiddellijk van kracht zonder dat een pijpleiding hoeft te worden uitgevoerd.


## De Edge Delivery-lijst voor te doen in Cloud Manager {#ed-todo-list}

<!-- &#x2460; for "1" inside circle -->

De **Edge Delivery om lijst** in Cloud Manager te doen is een onboarding taak controlelijst die wordt bedoeld om u door onboarding te begeleiden, die uw plaats van Edge Delivery helemaal beheren aan [&#x200B; gaan-Levend &#x200B;](/help/journey-onboarding/go-live-checklist.md).

![&#x200B; de plaats van Edge Delivery aan-doe lijst in Cloud Manager &#x200B;](/help/implementing/cloud-manager/assets/cm-eds-todo-list.png)

|   | Taak | Beschrijving |
| --- | --- | --- |
| 1 | Deelnemen aan het samenwerkingskanaal voor producten | Het klikken **legt nu verzoek** voor een verzoek aan Adobe om een kanaal voor uw bedrijf tot stand te brengen. Als het kanaal reeds bestaat, door:sturen u aan het kanaal van uw bedrijf. |
| 2 | Volledige voorwaarden | Zie [&#x200B; Mening die Begonnen leerprogramma &#x200B;](https://www.aem.live/developer/tutorial) krijgen. |
| 3 | Edge Delivery-site toevoegen OF <br> Nu een site maken | Zie [&#x200B; een plaats van Edge Delivery &#x200B;](#eds-add-site) toevoegen.<br> zie [&#x200B; een plaats van Edge Delivery in Cloud Manager &#x200B;](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md) creëren. |
| 4 | Een Edge Delivery-site configureren voor het gebruik van een externe Git-opslagplaats | Zie [&#x200B; een plaats van Edge Delivery vormen om een externe bewaarplaats van het Git te gebruiken &#x200B;](/help/implementing/cloud-manager/edge-delivery/config-edge-delivery-site-with-byog.md). |
| 5 | Domein toevoegen | Zie [&#x200B; een naam van het douanedomein &#x200B;](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen. |
| 6 | SSL-certificaat toevoegen | Zie [&#x200B; SSL certificaat &#x200B;](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toevoegen. |
| 7 | De CDN van uw Edge Delivery-site configureren | Zie [&#x200B; een Toewijzing van het Domein &#x200B;](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md) toevoegen. |
| 8 | Pushvalidatie instellen | Zie [&#x200B; de dupbevestiging van de Opstelling voor een plaats van Edge Delivery &#x200B;](/help/implementing/cloud-manager/edge-delivery/cdn-setup-push-invalidation.md). |
| 9 | Go-Live | Zie [&#x200B; gaan-Levende checklist &#x200B;](https://www.aem.live/docs/go-live-checklist). |

>[!VIDEO](https://video.tv.adobe.com/v/3441567?captions=dut&learn=on)

## Een ondersteuningsticket vastleggen {#eds-support-ticket}

{{support-ticket}}



