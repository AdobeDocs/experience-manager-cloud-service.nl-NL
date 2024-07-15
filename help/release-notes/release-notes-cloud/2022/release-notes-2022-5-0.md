---
title: Nota's van de versie voor 2022.5.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2022.5.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 1b867582-e34c-435b-b8f8-fc71dddcaccb
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---

# Opmerkingen bij de release 2022.5.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2022.5.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release (2022.5.0) is 9 juni 2022.
De volgende release (2022.6.0) is gepland voor 30 juni 2022.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van mei 2022 voor een overzicht van de functies die in de release van 2022.5.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/343321/?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies beschikbaar in [!DNL Sites] prereleasekanaal {#prerelease-features-sites}

* Verschillende GraphQL-functies
* A [ nieuwe console ](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) geoptimaliseerd voor Hoofdloos gebruik van de Fragmenten van de Inhoud

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* [ de Slimme Beeldvorming van Dynamic Media ](https://medium.com/adobetech/one-solution-fits-all-smart-imaging-with-aem-dynamic-media-be690b62df9f) steunt nu AVIF dossierformaat - verbetert verder de Vital van de Kern van Google (de Grootste Inhoudelijke Verf), met AVIF die 20% extra groottevermindering over WebP verstrekken. In totaal kan AVIF tot 41% reductie van gemiddelde grootte bieden in vergelijking met JPEG (in sommige afbeeldingen zelfs tot 76%).

* [!UICONTROL Experience Manager Assets Brand Portal] voert nu elke 12 uur automatische taken uit om alle Brand Portal-elementen te verwijderen die naar AEM worden gepubliceerd. U hoeft daarom de middelen in de map Contribution niet handmatig te verwijderen om de mapgrootte onder de drempelwaarde te houden. Zie [ wat in Experience Manager Assets Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html) nieuw is.

### Nieuwe functies beschikbaar in [!DNL Assets] prereleasekanaal {#prerelease-features-assets}

Experience Manager Assets gebruikt de mogelijkheden van Adobe Sensei AI aan nu [ tussen kleuren in een beeld onderscheid maken en die als markeringen automatisch op opname toepassen ](/help/assets/color-tag-images.md). Deze tags maken een verbeterde zoekervaring mogelijk op basis van de compositie van de afbeeldingskleur. U kunt het aantal kleuren binnen een bereik van 1 tot 40 configureren dat aan een afbeelding is gelabeld, zodat u later kunt zoeken naar afbeeldingen op basis van die kleuren.


## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] prereleasekanaal {#prerelease-features-forms}

* **Integreer Aanpassings Forms met de Macht van Microsoft®**: U kunt een Aangepast Vorm nu vormen om een Stroom van de Macht van Microsoft® in werking te stellen Automate Cloud bij voorlegging. Met het geconfigureerde adaptieve formulier worden vastgelegde gegevens, bijlagen en het document met records naar Power Automate Cloud Flow verzonden voor verwerking. Het helpt u om een aangepaste ervaring op het gebied van gegevensvastlegging op te bouwen en tegelijk de kracht van Microsoft® Power Automate te benutten om bedrijfslogics rond vastgelegde gegevens te bouwen en de workflows van klanten te automatiseren.

* **Tovenaar om een AanpassingsVorm** tot stand te brengen: U kunt zaken - gebruiksvriendelijke tovenaar gebruiken om snel auteur Aangepaste Forms te schrijven. De wizard biedt een snelle tabnavigatie waarmee u eenvoudig vooraf geconfigureerde sjablonen, stijlen, velden en verzendopties kunt selecteren om een adaptief formulier te maken.

  ![ Tovenaar om een Aangepaste Vorm ](/help/release-notes/assets/wizard.png) tot stand te brengen

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Snelle toegang tot productcockpit: eenvoudig toegang tot volledige gedetailleerde productinformatie met één klik in de Sites Editor

<!-- Image was not found during PR validation despite correct path   ![Enable wantlist](/help/assets/CIF/enable-wishlist.png) -->

* Steun voor extra marketing commerciële componenten: De componenten kunnen worden gevormd om toe:voegen-aan-kart en toe:voegen-aan-wantlist vraag-aan-actie te tonen

  ![ de redacteurskortere weg van Plaatsen aan productcockpit ](/help/assets/CIF/sites-editor-shortcut-to-cockpit.png)


## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* De &quot;add boom&quot;optie onder het scherm van het beheer van de replicatieagent **verdeelt lusje**, dat eerder als afgekeurd werd aangekondigd, werd verwijderd 20 juni, 2022 of snel daarna. De pakketten met een boomhiërarchie van inhoud zouden in plaats daarvan moeten worden herhaald gebruikend [ Publicatie ](/help/operations/replication.md#manage-publication) of het [ werkschema van de Inhoudsboom van Publish ](/help/operations/replication.md#publish-content-tree-workflow) leiden.

* Het gebruik van de API voor beheer van replicatieagent of replicatie voor het distribueren van inhoudspakketten groter dan 10 MB (knooppunten met eigenschappen, exclusief binaire getallen) is afgekeurd en afgedwongen op 12 september 2022 of kort daarna. In plaats daarvan, [ beheert Publicatie ](/help/operations/replication.md#manage-publication) of het [ werkschema van de Boom van de Inhoud van Publish ](/help/operations/replication.md#publish-content-tree-workflow) moet worden gebruikt om deze grote inhoudspakketten te herhalen. In Juli, zal een waarschuwingsbericht in het scherm van de replicatieagent admin **het lusje** verdelen als het proberen om deze grote inhoudspakketten en ook in het AEM foutenlogboek te herhalen wanneer de replicatie API wordt gebruikt om deze grote inhoudspakketten te herhalen. In september werden waarschuwingen vervangen door fouten. Pas uw processen dienovereenkomstig aan.

### Nieuwe functies beschikbaar in [!DNL Experience Manager] prereleasekanaal {#prerelease-features-foundation}

* AEM as a Cloud Service is nu geïntegreerd met Verenigde Shell om de gebruikerservaring te verbeteren en het met alle andere toepassingen van het Experience Cloud te verenigen. Zie [ AEM as a Cloud Service op Verenigde Shell ](/help/overview/aem-cloud-service-on-unified-shell.md) voor meer details.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation Security {#foundation-security}

### TLS 1.0, 1.1-afleiding

Vanaf 30 juni 2022 zal de as a Cloud Service van de Experience Manager een veiligere netwerkmededeling en gegevensuitwisseling met gebruikerssystemen vereisen. AEM zal uitsluitend de Veiligheid van de Laag van het Vervoer (TLS), 1.2 protocol gebruiken. Oudere TLS versies 1.0 en 1.1 zijn nu afgekeurd.

Als u oudere versies van TLS blijft gebruiken als 1.0 of 1.1, kan de toegang tot Experience Manager as a Cloud Service verloren gaan.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
