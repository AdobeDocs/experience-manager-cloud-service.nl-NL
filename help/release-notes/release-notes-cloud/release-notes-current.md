---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 092338947ef7c8f34bda4604e1c901344e966be0
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Current Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>From here, you can navigate to release notes of previous versions; for example, for those in 2020, 2021, and so on.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

The release date of [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] current release (2022.4.0) is May 5, 2022.
De volgende release (2022.5.0) is gepland voor 26 mei 2022.

## Release Video {#release-video}

Kijk eens naar de [Overzicht release april 2022](https://video.tv.adobe.com/v/342612?quality=12) video voor een overzicht van de functies die in de release 2022.4.0 zijn toegevoegd.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#sites-features}

* Gegevenstypen van inhoudsmodel kunnen nu worden gedefinieerd als [vertaalbaar](/help/assets/content-fragments/content-fragments-models.md#properties) het gebruiken van een eenvoudig controlevakje in de redacteur van het inhoudsmodel. Bovendien worden AEM vertaalregels en configuraties automatisch bijgewerkt.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* You can now [sort tags](/help/assets/organize-assets.md#use-tags-to-organize-assets) in the tag picker window in ascending or descending order based on the tag name, date of creation, or date of modification.


## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* **Communicatie - Ondersteuning voor API&#39;s voor documentmanipulatie in Forms as a Cloud Service SDK**: [Documentmanipulatie-API&#39;s](/help/forms/aem-forms-cloud-service-communications.md) Help bij het combineren, herschikken en valideren van PDF-documenten. You can now use Communications - Document Generation APIs on a local development environment with the help of AEM Forms as a Cloud Service SDK.

* **Aangepaste XCI gebruiken voor het genereren van een document met records**: U kunt nu [gebruik een aangepast XCI-bestand om verschillende eigenschappen van een document of record in te stellen](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#use-a-custom-xci-file). It overrides the master XCI with the custom changes. It provides more control over the generation of Documents of Record, increasing personalization, and customization opportunities.

* **Onzichtbare CAPTCHA gebruiken in een adaptieve vorm**: U kunt de [onzichtbare CAPTCHA om de CAPTCHA-uitdaging alleen te laten zien in het geval van een verdachte activiteit](/help/forms/captcha-adaptive-forms.md). Als er geen verdachte activiteit wordt gevonden, wordt de CAPTCHA-uitdaging niet weergegeven. Het helpt menselijke vormvoltooiing zonder controledoosvereisten beoordelen, aanpassingsinspanningen verminderen, en de eindgebruikerservaring verbeteren.

* **Form Data Model Configurations**: You can now [reuse Form Data Model configurations across environments](/help/forms/create-form-data-models.md#runmode-specific-context-aware-config), simplifying data integrations and reducing IT costs.

## CIF-invoegtoepassing {#cloud-services-cif}

### What is New {#what-is-new-cif}

* Quick access to product cockpit: Easily access full detailed product information with one-click in Sites Editor

   ![Enable wishlist](/help/assets/CIF/enable-wishlist.png)

* Steun voor extra marketingcomponenten: De componenten kunnen worden gevormd om toe:voegen-aan-kar en toe:voegen-aan-wenslijst vraag-aan-actie te tonen

   ![Snelkoppeling naar productcockpit in Sites-editor](/help/assets/CIF/sites-editor-shortcut-to-cockpit.png)

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### SDK Build Analyzers {#sdk-build-analyzers}

De AEM as a Cloud Service SDK bouwt Analyzer Maven Plugin ontdekt problemen in een bepaald project, met inbegrip van ontbrekende gebiedsdelen. Het biedt ontwikkelaars de mogelijkheid om problemen tijdens lokale ontwikkeling op te sporen, ruim voordat ze met Cloud Manager naar een cloud-omgeving implementeren.

A new analyzer has been recently added:

* `content-packages-validation` - valideert voor een goed gevormde inhoudssyntaxis en -structuur voor pakketten die tijdens de implementatie worden geïnstalleerd

U wordt ten zeerste aangeraden uw gemaakte project bij te werken met de nieuwste versie van de analysator of de analysator op te nemen als u dat nog niet hebt gedaan. Raadpleeg de documentatie voor meer informatie [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html).

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Migratiehulpmiddelen {#migration-tools}

You can find a complete list of Migration Tools releases [here](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
