---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 7ee2e43ab8a5726b2ecf7f157f67b5f3cc73fcff
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---


# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies weer te geven. bijvoorbeeld voor die in 2020, 2021, enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release (2022.4.0) is 5 mei 2022.
De volgende release (2022.5.0) is gepland voor 26 mei 2022.

## Video vrijgeven {#release-video}

Kijk eens naar de [Overzicht release april 2022](https://video.tv.adobe.com/v/342612?quality=12) video voor een overzicht van de functies die in de release 2022.4.0 zijn toegevoegd.

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#sites-features}

* Gegevenstypen van inhoudsmodel kunnen nu worden gedefinieerd als [vertaalbaar](/help/assets/content-fragments/content-fragments-models.md#properties) het gebruiken van een eenvoudig controlevakje in de redacteur van het inhoudsmodel. Bovendien worden AEM vertaalregels en configuraties automatisch bijgewerkt.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* U kunt nu [sorteertags](/help/assets/organize-assets.md#use-tags-to-organize-assets) in het venster met de tagkiezer in oplopende of aflopende volgorde op basis van de tagnaam, aanmaakdatum of wijzigingsdatum.


## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* **Communicatie - Ondersteuning voor API&#39;s voor documentmanipulatie in Forms as a Cloud Service SDK**: [Documentmanipulatie-API&#39;s](/help/forms/aem-forms-cloud-service-communications.md) Help bij het combineren, herschikken en valideren van PDF-documenten. U kunt nu communicatie - API&#39;s voor documentgeneratie gebruiken in een lokale ontwikkelomgeving met behulp van de as a Cloud Service SDK van AEM Forms.

* **Aangepaste XCI gebruiken voor het genereren van een document met records**: U kunt nu [gebruik een aangepast XCI-bestand om verschillende eigenschappen van een document of record in te stellen](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#use-a-custom-xci-file). Het treedt master XCI met de douaneveranderingen met voeten. Het verstrekt meer controle over de generatie van Documenten van Verslag, het verhogen van verpersoonlijking, en aanpassingskansen.

* **Onzichtbare CAPTCHA gebruiken in een adaptieve vorm**: U kunt de [onzichtbare CAPTCHA om de CAPTCHA-uitdaging alleen te laten zien in het geval van een verdachte activiteit](/help/forms/captcha-adaptive-forms.md). Als er geen verdachte activiteit wordt gevonden, wordt de CAPTCHA-uitdaging niet weergegeven. Het helpt menselijke vormvoltooiing zonder controledoosvereisten beoordelen, aanpassingsinspanningen verminderen, en de eindgebruikerservaring verbeteren.

* **Configuraties van formuliergegevensmodellen**: U kunt nu [Configuraties van het formuliergegevensmodel opnieuw gebruiken in verschillende omgevingen](/help/forms/create-form-data-models.md#runmode-specific-context-aware-config), het vereenvoudigen van gegevensintegratie en het verlagen van IT-kosten.

## CIF-invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Snelle toegang tot productcockpit: Eenvoudig toegang tot volledige gedetailleerde productinformatie met één klik in de Editor voor sites

   ![Enable wishlist](/help/assets/CIF/enable-wishlist.png)

* Steun voor extra marketingcomponenten: De componenten kunnen worden gevormd om toe:voegen-aan-kar en toe:voegen-aan-wenslijst vraag-aan-actie te tonen

   ![Snelkoppeling naar productcockpit in Sites-editor](/help/assets/CIF/sites-editor-shortcut-to-cockpit.png)

## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### SDK Build Analyzers {#sdk-build-analyzers}

De AEM as a Cloud Service SDK bouwt Analyzer Maven Plugin ontdekt problemen in een bepaald project, met inbegrip van ontbrekende gebiedsdelen. Het biedt ontwikkelaars de mogelijkheid om problemen tijdens lokale ontwikkeling op te sporen, ruim voordat ze met Cloud Manager naar een cloud-omgeving implementeren.

Er is onlangs een nieuwe analysator toegevoegd:

* `content-packages-validation` - valideert voor een goed gevormde inhoudssyntaxis en -structuur voor pakketten die tijdens de implementatie worden geïnstalleerd

U wordt ten zeerste aangeraden uw gemaakte project bij te werken met de nieuwste versie van de analysator of de analysator op te nemen als u dat nog niet hebt gedaan. Raadpleeg de documentatie voor meer informatie [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html).

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.28 is 22 april 2022.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om het gebruik van niet-ondersteunde API&#39;s van Asset Manager te detecteren en hierover verslag uit te brengen. Er zijn vier API&#39;s die niet meer worden ondersteund in AEM as a Cloud Service. Klanten moeten ervoor zorgen dat ze deze API&#39;s niet meer gebruiken en moeten de nieuwe methode voor het uploaden van middelen gebruiken.

* Mogelijkheid om het gebruik van sjablonen voor inhoudsfragmenten te detecteren. Sjablonen voor inhoudsfragmenten worden niet meer ondersteund voor het maken van nieuwe inhoudsfragmenten op AEM as a Cloud Service. Klanten moeten contentfragmentmodellen maken om sjablonen voor inhoudsfragmenten te vervangen.

* Mogelijkheid om activa met meer dan 100 afstammingen onder het metadatknooppunt van het actief in de repository te detecteren. Het wordt aanbevolen om metagegevensknooppunten te verwijderen die niet nodig zijn om de prestaties te verbeteren wanneer mappen met dergelijke elementen worden geladen.

* Mogelijkheid om het gebruikte type gegevensopslag te detecteren en te rapporteren.

* Patroon bijgewerkt voor AEM formulierportal.

### Opgeloste problemen {#bug-fixes-bpa}

* BPA rapporteerde bevindingen voor kerncomponenten in plaats van alleen op klantcomponenten te rapporteren. Dit is opgelost.
