---
title: Opmerkingen bij de release 2022.4.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2022.4.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 6c86838a-cabf-4770-b1ae-618af70193a2
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 0%

---

# Opmerkingen bij de release 202.4.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de release met functies voor de versie 2022.4.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release (2022.4.0) is 5 mei 2022.
De volgende release (2022.5.0) is gepland voor 9 juni 2022.

## Video vrijgeven {#release-video}

Kijk eens naar de [Overzicht release april 2022](https://video.tv.adobe.com/v/342612?quality=12) video voor een overzicht van de functies die in de release 2022.4.0 zijn toegevoegd.

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#sites-features}

* Gegevenstypen van inhoudsmodel kunnen nu worden gedefinieerd als [vertaalbaar](/help/assets/content-fragments/content-fragments-models.md#properties) het gebruiken van een eenvoudig controlevakje in de redacteur van het inhoudsmodel. Bovendien worden AEM vertaalregels en -configuraties automatisch bijgewerkt.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* U kunt nu [sorteertags](/help/assets/organize-assets.md#use-tags-to-organize-assets) in het venster met de tagkiezer in oplopende of aflopende volgorde op basis van de tagnaam, aanmaakdatum of wijzigingsdatum.


## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* **Communicatie - Ondersteuning voor API&#39;s voor documentmanipulatie in Forms as a Cloud Service SDK**: [Documentmanipulatie-API&#39;s](/help/forms/aem-forms-cloud-service-communications.md) Help bij het combineren, herschikken en valideren van PDF-documenten. U kunt nu communicatie - API&#39;s voor documentgeneratie gebruiken in een lokale ontwikkelomgeving met behulp van de as a Cloud Service SDK van AEM Forms.

* **Aangepaste XCI gebruiken voor het genereren van een document met records**: U kunt nu [gebruik een aangepast XCI-bestand om verschillende eigenschappen van een document of record in te stellen](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#use-a-custom-xci-file). De aangepaste wijzigingen hebben voorrang op de hoofd-XCI. Het verstrekt meer controle over de generatie van Documenten van Verslag, het verhogen van verpersoonlijking, en aanpassingskansen.

* **Onzichtbare CAPTCHA gebruiken in een adaptieve vorm**: U kunt de opdracht [onzichtbare CAPTCHA om de CAPTCHA-uitdaging alleen te laten zien in het geval van een verdachte activiteit](/help/forms/captcha-adaptive-forms.md). Als er geen verdachte activiteit wordt gevonden, wordt de CAPTCHA-uitdaging niet weergegeven. Het helpt menselijke vormvoltooiing zonder controledoosvereisten beoordelen, aanpassingsinspanningen verminderen, en de eindgebruikerservaring verbeteren.

* **Configuraties van formuliergegevensmodellen**: U kunt nu [Configuraties van het formuliergegevensmodel opnieuw gebruiken in verschillende omgevingen](/help/forms/create-form-data-models.md#runmode-specific-context-aware-config), het vereenvoudigen van gegevensintegratie en het verlagen van IT-kosten.


## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### SDK Build Analyzers {#sdk-build-analyzers}

De AEM as a Cloud Service SDK bouwt Analyzer Maven Plugin ontdekt problemen in een bepaald project, met inbegrip van ontbrekende gebiedsdelen. Het biedt ontwikkelaars de mogelijkheid om problemen tijdens lokale ontwikkeling op te sporen, ruim voordat ze met Cloud Manager naar een cloud-omgeving implementeren.

Er is onlangs een nieuwe analysator toegevoegd:

* `content-packages-validation` - valideert voor een goed gevormde inhoudssyntaxis en -structuur voor pakketten die tijdens de implementatie worden geïnstalleerd

U wordt ten zeerste aangeraden uw gemaakte project bij te werken met de nieuwste versie van de analysator of de analysator op te nemen als u dat nog niet hebt gedaan. Raadpleeg de documentatie voor meer informatie [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html).

## [!DNL Experience Manager] als [!DNL Cloud Service] Foundation Security {#foundation-security}

### TLS 1.0, 1.1-afleiding

Vanaf 30 juni 2022 vereist as a Cloud Service Experience Manager een veiligere netwerkcommunicatie en gegevensuitwisseling met gebruikerssystemen. AEM is van plan om exclusief de Veiligheid van de Laag van het Vervoer (TLS), 1.2 protocol te gebruiken. Oudere TLS versies 1.0 en 1.1 zijn nu afgekeurd.

Als u oudere versies van TLS blijft gebruiken als 1.0 of 1.1, kan de toegang tot as a Cloud Service Experience Manager verloren gaan.

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
