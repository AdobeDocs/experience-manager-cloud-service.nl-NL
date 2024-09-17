---
title: Inleiding tot Edge Delivery Services in Cloud Manager
description: Leer hoe u Cloud Manager-projecten kunt leveren met behulp van Edge Delivery Services.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5dc3d571c553f2972295172c7a6d0249be3285b8
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 1%

---

# Inleiding tot Edge Delivery Services in Cloud Manager {#edge-delivery-services}

Edge Delivery Services is een samenstellbare set services die u in staat stelt om op zeer flexibele wijze inhoud op uw website te schrijven. Op deze manier kunt u het volgende doen:

* Maak snelle sites met een perfecte Lighthouse Score.
* Bewaking van de prestaties voortdurend via RUM (Real Use Monitoring).
* Verhoog de efficiëntie bij het ontwerpen door inhoudsbronnen te ontkoppelen.

U kunt zowel AEM inhoudsbeheer als WYSIWYG-authoring gebruiken met behulp van de Universal Editor en op document gebaseerde authoring.

Met Cloud Manager in AEM as a Cloud Service kunt u Edge Delivery Service inschakelen voor uw project.

>[!TIP]
>
>Voor details over Edge Delivery Services en hoe het met AEM kan worden gebruikt, zie [ overzicht van Edge Delivery Services ](/help/edge/overview.md).

<!-- RELEASED TO GA SEPTEMBER 5, 2024
>[!NOTE]
>
>This feature is only available to [the early adopter program](/help/implementing/cloud-manager/release-notes/current.md#early-adoption). -->


## Edge Delivery Services in Cloud Manager {#edge-in-cloud-manager}

Als u Edge Delivery Services als deel van Adobe Experience Manager Sites vergunning hebt gegeven, kunt u aan boord uw plaats met Edge Delivery Services direct in Cloud Manager en gaan levend [ gebruikend een geleide, zelfbediening ervaring ](/help/implementing/cloud-manager/managing-code/private-repositories.md).

Bovendien kunt u tot een verenigde ervaring toegang hebben voor het beheren van al uw AEM eigenschappen terwijl het verzekeren van consistentie over zeer belangrijke werkschema&#39;s. Dit zijn domeinnaambeheer, SSL-certificaatbeheer en CDN-toewijzingen.

## Edge Delivery Services toevoegen aan een productieprogramma of sandboxprogramma

Om programma&#39;s toe te voegen of uit te geven, moet u een lid van de **rol van de Bedrijfs Eigenaar {zijn 0} of toestemming worden gegeven om dit te doen.**

Uw organisatie moet een licentie voor ongebruikte Edge Delivery Services hebben voordat deze kan worden toegepast op een productieprogramma.

>[!NOTE]
>
>Zodra de vergunning van Edge Delivery Services wordt toegepast op of uit een programma verwijderd, wordt de verandering onmiddellijk van kracht zonder de behoefte om een pijpleiding in werking te stellen. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

Voer afhankelijk van uw gebruiksgeval een van de volgende handelingen uit:

| Hoofdletters gebruiken | Beschrijving |
| --- | --- |
| Ik wil Edge Delivery Services toevoegen aan een nieuw productieprogramma. | Zie [ productieprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) creëren.<br> in de tovenaar, onder het **Oplossingen &amp; toe:voegen-ons** lusje, uitgezochte **Edge Delivery Services**. |
| Ik wil Edge Delivery Services toevoegen aan een bestaand productieprogramma. | Zie [ programma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) uitgeven.<br> in **geef de dialoogdoos van het Programma** uit, onder het **Oplossingen &amp; toe:voegen-ons** lusje, uitgezochte **Edge Delivery Services**. |
| Ik wil een Edge Delivery-site toevoegen aan Cloud Manager | Zie [ een plaats van Edge Delivery ](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) toevoegen. |
| Ik wil Edge Delivery Services toevoegen aan een nieuw of bestaand sandboxprogramma. | Zie [ zandbakprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) creëren.<br> wanneer u een zandbakprogramma creeert, worden de Edge Delivery Services toegevoegd aan het programma door gebrek; u te hoeven niet om het te selecteren.<br> Bestaande zandbakprogramma&#39;s voorafgaand aan de algemene beschikbaarheid van Edge Delivery, erven automatisch Edge Delivery Services. |

## Adobe aanbevolen pad voor klanten met een licentie {#recommended-path-eds}

Als gelicentieerde klant, zorg ervoor u uw voordelen van Adobe door tot uw vergunning van Edge Delivery Services toegang te hebben en te verbruiken door Cloud Manager maximaliseert. Deze benadering laat u [ beheerde Adobe gebruiken CDN ](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) en uit zeer belangrijke voordelen zoals zelfbediening CDN beheer, met inbegrip van de configuratie en de toevoeging van DV certificaten voordeel halen. Bovendien, nadat een DV- certificaat wordt gecreeerd, vernieuwt de Adobe het automatisch om de drie maanden, tenzij het wordt geschrapt. Als u geen Edge Delivery Services vergunning met Adobe hebt en besluit om deze voordelen over te slaan, kunt u een klant-beheerde CDN slechts gebruiken. Deze instelling moet zich op het `aem.live` -platform bevinden.

Als u een licentie hebt voor licenties voor AEM as a Cloud Service Sites-Edge Delivery Services, meldt u zich aan bij Cloud Manager om ervoor te zorgen dat u het volgende kunt doen:

* Gebruik uw licentie voor uw gekozen programma.
* Haal voordeel uit [ API-eerste ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) voordelen voor het uitvoeren van (creeer, Gelezen, Update, Schrapping) verrichtingen CRUD.
<!-- REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+Self-service+access+to+Edge+Delivery+Services+and+Adobe+Managed+CDN * Access to license dashboard and reporting -->
* Toegang SLA die (*binnenkort komt*) <!-- ADD LINK TO IT WHEN FINALLY ADDED --> meldt
* Ondersteuning voor Adobe. Zorg ervoor dat de sites van uw Edge Delivery Services zijn geregistreerd via een productieprogramma in Cloud Manager voor een correcte herkenning en ondersteuning door de Adobe.


## De Edge Delivery-lijst met taken {#ed-todo-list}

De **Edge Delivery om lijst** te doen is een onboarding taak controlelijst die wordt bedoeld om u door onboarding te begeleiden, uw plaats van Edge Delivery te beheren al manier aan [ gaan-Levend ](/help/journey-onboarding/go-live-checklist.md).

![ de plaats van Edge Delivery om lijst ](/help/implementing/cloud-manager/assets/cm-eds-todo-list.png) te doen

|  | Taak | Beschrijving |
| --- | --- | --- |
| 1 | Deelnemen aan het samenwerkingskanaal voor producten | Het klikken **legt nu verzoek voor** legt een verzoek aan Adobe voor om een kanaal voor uw bedrijf tot stand te brengen. Als het kanaal reeds bestaat, door:sturen u aan het kanaal van uw bedrijf. |
| 2 | Volledige voorwaarden | Het klikken van **Mening die Begonnen leerprogramma** krijgt, leidt u aan [ Begonnen het worden - Leerprogramma van de Ontwikkelaar ](https://www.aem.live/developer/tutorial). |
| 3 | Edge Delivery-site toevoegen | Zie [ een plaats van Edge Delivery ](#eds-add-site) toevoegen. |
| 4 | Domein toevoegen | Zie [ een naam van het douanedomein ](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen. |
| 5 | SSL-certificaat toevoegen | Zie [ SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toevoegen. |
| 6 | De CDN van uw Edge Delivery-site configureren | Zie [ een configuratie CDN ](#add-cdn) toevoegen. |

>[!VIDEO](https://video.tv.adobe.com/v/3428020?learn=on)

<!--
Edge Delivery Services can be enabled when adding a new production program or editing an existing one.

![Add production program with Edge Delivery Services](assets/add-production-program-with-edge.png)

For more information about adding programs, see the following:

* [Create Production programs](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
* [Create Sandbox programs](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) -->
