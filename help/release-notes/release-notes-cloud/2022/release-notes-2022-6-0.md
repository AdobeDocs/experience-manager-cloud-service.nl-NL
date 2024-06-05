---
title: Opmerkingen bij de release 2022.6.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2022.6.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: cf2133dc-56cd-4a07-ab11-72e16f015ff5
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# Opmerkingen bij de release 202.6.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de release met functies voor de versie 2022.6.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release (2022.6.0) is 30 juni 2022.

De volgende release (2022.7.0) is gepland voor 8 augustus 2022.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van juni 2022 voor een overzicht van de functies die in de release van 2022.6.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/344308/?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#sites-features}

* Een nieuwe [gebruikersinterface](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) is nu beschikbaar voor beheerders van inhoud en auteurs van inhoud om efficiënt te beheren (zoals publiceren, ongedaan maken, kopiëren, verplaatsen enzovoort), te zoeken/filteren en inhoudsfragmenten te maken voor gebruik in hoofdletters.

  ![Console voor inhoudsfragment](/help/release-notes/assets/cf-ui.png)

* De nieuwe [Component Inhoudsopgave](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/tableofcontents.html) werkt niet alleen met de Componenten van de Kern maar met alle componenten, automatisch teruggevend ToCs op inhoudspagina&#39;s. En omdat het server-kant wordt teruggegeven en volledig in het voorgeheugen ondergebracht door de verzender, is het ook efficiënt te laden.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

Experience Manager Assets gebruikt tot nu toe Adobe Sensei AI-mogelijkheden [onderscheid maken tussen kleuren in een afbeelding en deze als tags automatisch toepassen bij opname](/help/assets/color-tag-images.md). Deze tags maken een verbeterde zoekervaring mogelijk op basis van de compositie van de afbeeldingskleur. U kunt het aantal kleuren binnen een bereik van 1 tot 40 configureren dat aan een afbeelding is gelabeld, zodat u later kunt zoeken naar afbeeldingen op basis van die kleuren.

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#forms-features}

* **[Adaptieve Forms integreren met Microsoft® Power Automate](/help/forms/forms-microsoft-power-automate-integration.md)**: U kunt nu een adaptief formulier configureren om een Microsoft® Power Automate Cloud Flow uit te voeren bij verzending. Met het geconfigureerde adaptieve formulier worden vastgelegde gegevens, bijlagen en het document met records naar Power Automate Cloud Flow verzonden voor verwerking. Het helpt u om een aangepaste ervaring op het gebied van gegevensvastlegging op te bouwen en tegelijk de kracht van Microsoft® Power Automate te benutten om bedrijfslogics rond vastgelegde gegevens te bouwen en de workflows van klanten te automatiseren.

* **Wizard voor het maken van een adaptief formulier**: Met een gebruiksvriendelijke wizard voor bedrijven kunt u snel Adaptive Forms ontwerpen. De wizard biedt een snelle tabnavigatie waarmee u eenvoudig vooraf geconfigureerde sjablonen, stijlen, velden en verzendopties kunt selecteren om een adaptief formulier te maken.

  ![Wizard voor het maken van een adaptief formulier](/help/release-notes/assets/wizard.png)

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Pagina met eigenschappen van cockpit-eigenschappen voor nieuwe producten voor een beter en vereenvoudigd overzicht

![overzicht van de eigenschappen van productcockpit](/help/assets/CIF/product_cockpit_properties_overview.png)

* Verbeterde compatibiliteit en robuustheid voor connectors van derden op I/O Runtime

* Verbeterde ondersteuning voor overschreven GQL Client-configuratie (bijvoorbeeld aangepaste caching-functionaliteit instellen)

* Meerdere eindpunten voor handel worden nu offline ondersteund en kunnen worden geconfigureerd via Cloud Manager. Meer informatie vindt u in de CIF blog [hier](https://medium.com/adobetech/use-aem-as-a-cloud-service-with-multiple-adobe-commerce-systems-9295612a9554).


### Bugfixes {#bug-fixes-cif}

* In het veld Meerwaardeproductkiezer worden de tweede en aanvullende producten als ongeldig weergegeven

* De productkiezer wordt soms verborgen achter componenten

## Invoegtoepassing demo&#39;s referentie {#cloud-services-demos}

### Nieuwe functies {#what-is-new-demos}

* Nieuwe WKND-sjabloon voor inhoud en Commerce die WKND uitbreidt met een E2E-winkelervaring met productcatalogus, winkelwagentje, kassa en mijnAccount. Dit malplaatje gebruikt CIF en zijn CIF Componenten van de Kern, zodat moet u ook CIF toe:voegen-op installeren. Meer informatie vindt u in de CIF blog [hier](https://medium.com/adobetech/learn-how-to-create-a-shoppable-experience-with-the-new-wknd-reference-site-and-cif-b3b2c161f67e).

![WKND-winkel](/help/assets/CIF/wknd_shop.png)

![WKND pdp](/help/assets/CIF/wknd_pdp.png)

## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* Zoals vermeld in de de versienota&#39;s van mei (2022.5.0), &quot;voeg boom&quot;optie onder het scherm van de replicatieagent admin toe **Distribueren** is verwijderd. Pakketten met een boomstructuur van inhoud moeten worden gerepliceerd met [Publicatie beheren](/help/operations/replication.md#manage-publication) of de [Inhoudsstructuur publiceren](/help/operations/replication.md#manage-publication#publish-content-tree-workflow) workflow.

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
