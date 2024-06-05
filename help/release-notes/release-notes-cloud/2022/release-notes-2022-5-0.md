---
title: Opmerkingen bij de release 2022.5.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2022.5.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 1b867582-e34c-435b-b8f8-fc71dddcaccb
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---

# Opmerkingen bij de release 202.5.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de release met functies voor de versie 2022.5.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release (2022.5.0) is 9 juni 2022.
De volgende release (2022.6.0) is gepland voor 30 juni 2022.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van mei 2022 voor een overzicht van de functies die in de release van 2022.5.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/343321/?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies beschikbaar in [!DNL Sites] prerelease-kanaal {#prerelease-features-sites}

* Verschillende GraphQL-functies
* A [nieuwe console](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) geoptimaliseerd voor gebruik zonder kop van inhoudsfragmenten

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* [Dynamic Media Smart Imaging](https://medium.com/adobetech/one-solution-fits-all-smart-imaging-with-aem-dynamic-media-be690b62df9f) biedt nu ondersteuning voor AVIF-bestandsindeling - verdere verbetering van Google Core Web Vital (Grootste voorwaardelijke verf), waarbij AVIF een extra reductie van 20% biedt ten opzichte van WebP. In totaal kan AVIF tot 41% reductie van gemiddelde grootte bieden in vergelijking met JPEG (in sommige afbeeldingen zelfs tot 76%).

* [!UICONTROL Experience Manager Assets Brand Portal] Voert nu elke 12 uur automatische taken uit om alle Brand Portal-middelen te verwijderen die naar AEM worden gepubliceerd. U hoeft daarom de middelen in de map Contribution niet handmatig te verwijderen om de mapgrootte onder de drempelwaarde te houden. Zie [Nieuwe functies in Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html).

### Nieuwe functies beschikbaar in [!DNL Assets] prerelease-kanaal {#prerelease-features-assets}

Experience Manager Assets gebruikt tot nu toe Adobe Sensei AI-mogelijkheden [onderscheid maken tussen kleuren in een afbeelding en deze als tags automatisch toepassen bij opname](/help/assets/color-tag-images.md). Deze tags maken een verbeterde zoekervaring mogelijk op basis van de compositie van de afbeeldingskleur. U kunt het aantal kleuren binnen een bereik van 1 tot 40 configureren dat aan een afbeelding is gelabeld, zodat u later kunt zoeken naar afbeeldingen op basis van die kleuren.


## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#prerelease-features-forms}

* **Adaptieve Forms integreren met Microsoft® Power Automate**: U kunt nu een adaptief formulier configureren om een Microsoft® Power Automate Cloud Flow uit te voeren bij verzending. Met het geconfigureerde adaptieve formulier worden vastgelegde gegevens, bijlagen en het document met records naar Power Automate Cloud Flow verzonden voor verwerking. Het helpt u om een aangepaste ervaring op het gebied van gegevensvastlegging op te bouwen en tegelijk de kracht van Microsoft® Power Automate te benutten om bedrijfslogics rond vastgelegde gegevens te bouwen en de workflows van klanten te automatiseren.

* **Wizard voor het maken van een adaptief formulier**: U kunt de gebruiksvriendelijke wizard van uw bedrijf gebruiken om Adaptive Forms snel te ontwerpen. De wizard biedt een snelle tabnavigatie waarmee u eenvoudig vooraf geconfigureerde sjablonen, stijlen, velden en verzendopties kunt selecteren om een adaptief formulier te maken.

  ![Wizard voor het maken van een adaptief formulier](/help/release-notes/assets/wizard.png)

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Snelle toegang tot productcockpit: eenvoudig toegang tot volledige gedetailleerde productinformatie met één klik in de Sites Editor

<!-- Image was not found during PR validation despite correct path   ![Enable wantlist](/help/assets/CIF/enable-wishlist.png) -->

* Steun voor extra marketing commerciële componenten: De componenten kunnen worden gevormd om toe:voegen-aan-kart en toe:voegen-aan-wantlist vraag-aan-actie te tonen

  ![Snelkoppeling naar productcockpit in Sites-editor](/help/assets/CIF/sites-editor-shortcut-to-cockpit.png)


## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* De optie &quot;structuur toevoegen&quot; onder het beheerscherm van de replicatieagent **Tabblad Distribueren**, die eerder als afgekeurd werd aangekondigd, werd ingetrokken op 20 juni 2022 of kort daarna. Pakketten met een boomstructuur van inhoud moeten worden gerepliceerd met [Publicatie beheren](/help/operations/replication.md#manage-publication) of de [Workflow Inhoudsstructuur publiceren](/help/operations/replication.md#publish-content-tree-workflow).

* Het gebruik van de API voor beheer van replicatieagent of replicatie voor het distribueren van inhoudspakketten groter dan 10 MB (knooppunten met eigenschappen, exclusief binaire getallen) is afgekeurd en afgedwongen op 12 september 2022 of kort daarna. In plaats daarvan, [Publicatie beheren](/help/operations/replication.md#manage-publication) of de [Workflow Inhoudsstructuur publiceren](/help/operations/replication.md#publish-content-tree-workflow) moeten worden gebruikt om deze grote inhoudspakketten te repliceren. In juli, zal een waarschuwingsbericht in het scherm van de replicatieagent admin verschijnen **Tabblad Distribueren** als u probeert deze grote inhoudspakketten te repliceren en ook in het AEM foutenlogboek wanneer de replicatie-API wordt gebruikt om deze grote inhoudspakketten te repliceren. In september werden waarschuwingen vervangen door fouten. Pas uw processen dienovereenkomstig aan.

### Nieuwe functies beschikbaar in [!DNL Experience Manager] prerelease-kanaal {#prerelease-features-foundation}

* AEM as a Cloud Service is nu geïntegreerd met Verenigde Shell om de gebruikerservaring te verbeteren en het met alle andere toepassingen van het Experience Cloud te verenigen. Zie [AEM as a Cloud Service op Verenigde Shell](/help/overview/aem-cloud-service-on-unified-shell.md) voor meer informatie .

## [!DNL Experience Manager] als [!DNL Cloud Service] Foundation Security {#foundation-security}

### TLS 1.0, 1.1-afleiding

Vanaf 30 juni 2022 vereist as a Cloud Service Experience Manager een veiligere netwerkcommunicatie en gegevensuitwisseling met gebruikerssystemen. AEM zal uitsluitend de Veiligheid van de Laag van het Vervoer (TLS), 1.2 protocol gebruiken. Oudere TLS versies 1.0 en 1.1 zijn nu afgekeurd.

Als u oudere versies van TLS blijft gebruiken als 1.0 of 1.1, kan de toegang tot as a Cloud Service Experience Manager verloren gaan.

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
