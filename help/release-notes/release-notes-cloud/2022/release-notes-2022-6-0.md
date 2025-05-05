---
title: Nota's van de versie voor 2022.6.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2022.6.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: cf2133dc-56cd-4a07-ab11-72e16f015ff5
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# Opmerkingen bij de release 2022.6.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2022.6.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release (2022.6.0) is 30 juni 2022.

De volgende release (2022.7.0) is gepland voor 8 augustus 2022.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van juni 2022 voor een overzicht van de functies die in de release van 2022.6.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/344308/?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#sites-features}

* Een nieuw [ gebruikersinterface ](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) is nu beschikbaar voor inhoudsbeheerders en inhoudsauteurs om efficiënt te beheren (zoals publiceren, unpublish, exemplaar, beweging, etc.), onderzoek/filter, en inhoudsfragmenten voor Hoofdloze gebruik-gevallen tot stand te brengen.

  ![ de Console van het Fragment van de Inhoud ](/help/release-notes/assets/cf-ui.png)

* De nieuwe [ Component van de Inhoudsopgave ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/tableofcontents.html) werkt niet alleen met de Componenten van de Kern maar met alle componenten, automatisch teruggevend ToCs op inhoudspagina&#39;s. En omdat het server-kant wordt teruggegeven en volledig in het voorgeheugen ondergebracht door de verzender, is het ook efficiënt te laden.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

Experience Manager Assets gebruikt de mogelijkheden van Adobe Sensei AI aan nu [ tussen kleuren in een beeld onderscheid maken en die als markeringen automatisch op opname toepassen ](/help/assets/color-tag-images.md). Deze tags maken een verbeterde zoekervaring mogelijk op basis van de compositie van de afbeeldingskleur. U kunt het aantal kleuren binnen een bereik van 1 tot 40 configureren dat aan een afbeelding is gelabeld, zodat u later kunt zoeken naar afbeeldingen op basis van die kleuren.

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#forms-features}

* **[Integreer Aanpassings Forms met de Macht van Microsoft®](/help/forms/forms-microsoft-power-automate-integration.md)**: U kunt een Aangepast Vorm nu vormen om een Stroom van de Macht van Microsoft® in werking te stellen Automate Cloud bij voorlegging. Met het geconfigureerde adaptieve formulier worden vastgelegde gegevens, bijlagen en het document met records naar Power Automate Cloud Flow verzonden voor verwerking. Het helpt u om een aangepaste ervaring op het gebied van gegevensvastlegging op te bouwen en tegelijk de kracht van Microsoft® Power Automate te benutten om bedrijfslogics rond vastgelegde gegevens te bouwen en de workflows van klanten te automatiseren.

* **Tovenaar om een AanpassingsVorm** tot stand te brengen: U kunt zaken gebruiken - gebruikersvriendelijke tovenaar aan snel auteur Aangepaste Forms. De wizard biedt een snelle tabnavigatie waarmee u eenvoudig vooraf geconfigureerde sjablonen, stijlen, velden en verzendopties kunt selecteren om een adaptief formulier te maken.

  ![ Tovenaar om een Aangepaste Vorm ](/help/release-notes/assets/wizard.png) tot stand te brengen

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Pagina met eigenschappen van cockpit-eigenschappen voor nieuwe producten voor een beter en vereenvoudigd overzicht

![ overzicht van de eigenschappen van de productcockpit ](/help/assets/CIF/product_cockpit_properties_overview.png)

* Verbeterde compatibiliteit en robuustheid voor connectors van derden op I/O Runtime

* Verbeterde ondersteuning voor overschreven GQL Client-configuratie (bijvoorbeeld aangepaste caching-functionaliteit instellen)

* Meerdere eindpunten voor handel worden nu offline ondersteund en kunnen via Cloud Manager worden geconfigureerd. U kunt details in CIF blog [ hier ](https://medium.com/adobetech/use-aem-as-a-cloud-service-with-multiple-adobe-commerce-systems-9295612a9554) vinden.


### Bugfixes {#bug-fixes-cif}

* In het veld Meerwaardeproductkiezer worden de tweede en aanvullende producten als ongeldig weergegeven

* De productkiezer wordt soms verborgen achter componenten

## Invoegtoepassing demo&#39;s referentie {#cloud-services-demos}

### Nieuwe functies {#what-is-new-demos}

* Nieuwe WKND-sjabloon voor inhoud en Commerce die WKND uitbreidt met een E2E-winkelervaring met productcatalogus, winkelwagentje, kassa en mijnAccount. Dit malplaatje gebruikt CIF en zijn CIF Componenten van de Kern, zodat moet u ook CIF toe:voegen-op installeren. U kunt details in CIF blog [ hier ](https://medium.com/adobetech/learn-how-to-create-a-shoppable-experience-with-the-new-wknd-reference-site-and-cif-b3b2c161f67e) vinden.

![ WKND shop ](/help/assets/CIF/wknd_shop.png)

![ WKND pdp ](/help/assets/CIF/wknd_pdp.png)

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* Zoals vermeld in Mei (2022.5.0) versienota&#39;s, werd de &quot;Add boom&quot;optie onder het scherm van de replicatieagent admin **verdeelt** tabel verwijderd. De pakketten met een boomhiërarchie van inhoud zouden in plaats daarvan moeten worden herhaald gebruikend [ Publicatie ](/help/operations/replication.md#manage-publication) of het [ 3&rbrace; werkschema van de Inhoudsboom van Publish beheren.](/help/operations/replication.md#manage-publication#publish-content-tree-workflow)

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
