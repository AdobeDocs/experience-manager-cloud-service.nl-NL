---
title: Nota's van de versie voor 2022.4.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2022.4.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 6c86838a-cabf-4770-b1ae-618af70193a2
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 0%

---

# Opmerkingen bij de release 2022.4.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2022.4.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [&#x200B; Recente Updates van de Documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release (2022.4.0) is 5 mei 2022.
De volgende release (2022.5.0) is gepland voor 9 juni 2022.

## Video vrijgeven {#release-video}

Heb een blik bij de [&#x200B; April 2022 het Overzicht van de Versie &#x200B;](https://video.tv.adobe.com/v/342612?quality=12) video voor een samenvatting van de eigenschappen die in de versie 2022.4.0 worden toegevoegd.

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#sites-features}

* De types van modelgegevens van de inhoud kunnen nu als [&#x200B; vertaalbaar &#x200B;](/help/assets/content-fragments/content-fragments-models.md#properties) worden bepaald gebruikend eenvoudige checkbox in de redacteur van het inhoudsmodel. Bovendien worden AEM vertaalregels en -configuraties automatisch bijgewerkt.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* U kunt [&#x200B; soortmarkeringen &#x200B;](/help/assets/organize-assets.md#use-tags-to-organize-assets) in het venster van de markeringsplukker nu in het stijgen of dalende orde die op de markeringsnaam, datum van verwezenlijking, of datum van wijziging wordt gebaseerd.


## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* **Mededelingen - de steun van APIs van de Manipatie van het Document in Forms as a Cloud Service SDK**: [&#x200B; de Manipatie APIs van het Document &#x200B;](/help/forms/aem-forms-cloud-service-communications.md) helpen om, PDF documenten te combineren te herschikken en te bevestigen. U kunt nu communicatie - API&#39;s voor documentgeneratie gebruiken in een lokale ontwikkelomgeving met behulp van AEM Forms as a Cloud Service SDK.

* **douane XCI van het Gebruik voor het produceren van een Document van Verslag**: U kunt [&#x200B; een douaneXCI dossier nu gebruiken om diverse eigenschappen van een Document van Verslag &#x200B;](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#use-a-custom-xci-file) te plaatsen. De aangepaste wijzigingen hebben voorrang op de hoofd-XCI. Het verstrekt meer controle over de generatie van Documenten van Verslag, het verhogen van verpersoonlijking, en aanpassingskansen.

* **Onzichtbare CAPTCHA van het Gebruik in een adaptieve vorm**: U kunt [&#x200B; onzichtbare CAPTCHA gebruiken om de uitdaging CAPTCHA slechts in het geval van een verdachte activiteit &#x200B;](/help/forms/captcha-adaptive-forms.md) te tonen. Als er geen verdachte activiteit wordt gevonden, wordt de CAPTCHA-uitdaging niet weergegeven. Het helpt menselijke vormvoltooiing zonder controledoosvereisten beoordelen, aanpassingsinspanningen verminderen, en de eindgebruikerservaring verbeteren.

* **de ModelConfiguraties van Gegevens van de Vorm**: U kunt [&#x200B; configuraties van het Model van Gegevens van de Vorm over milieu&#39;s &#x200B;](/help/forms/create-form-data-models.md#runmode-specific-context-aware-config) nu opnieuw gebruiken, die gegevensintegratie vereenvoudigen en de kosten van IT drukken.


## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### SDK Build Analyzers {#sdk-build-analyzers}

De AEM as a Cloud Service SDK Build Analyzer Maven Plugin ontdekt problemen in een bepaald project, met inbegrip van ontbrekende gebiedsdelen. Het biedt ontwikkelaars de mogelijkheid om problemen tijdens lokale ontwikkeling te ontdekken, ruim voordat ze met Cloud Manager naar Cloud-omgevingen implementeren.

Er is onlangs een nieuwe analysator toegevoegd:

* `content-packages-validation` - valideert voor een goed gevormde inhoudssyntaxis en -structuur voor pakketten die tijdens de implementatie worden geïnstalleerd

U wordt ten zeerste aangeraden uw gemaakte project bij te werken met de nieuwste versie van de analysator of de analysator op te nemen als u dat nog niet hebt gedaan. Voor meer informatie, zie de documentatie [&#x200B; hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=nl-NL).

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation Security {#foundation-security}

### TLS 1.0, 1.1-afleiding

Vanaf 30 juni 2022 zal de as a Cloud Service van de Experience Manager een veiligere netwerkmededeling en gegevensuitwisseling met gebruikerssystemen vereisen. AEM is van plan om exclusief de Veiligheid van de Laag van het Vervoer (TLS), 1.2 protocol te gebruiken. Oudere TLS versies 1.0 en 1.1 zijn nu afgekeurd.

Als u oudere versies van TLS blijft gebruiken als 1.0 of 1.1, kan de toegang tot Experience Manager as a Cloud Service verloren gaan.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [&#x200B; hier &#x200B;](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [&#x200B; hier &#x200B;](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
