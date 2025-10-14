---
title: Nota's van de versie voor 2023.12.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2023.12.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: b36add58-a2ba-4299-94be-e0026e9c553c
feature: Release Information
role: Admin
source-git-commit: 8be0a9894bb5b3a138c0ec40a437d6c8e4bc7e25
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.12.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.12.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Heb een blik bij [&#x200B; Experience Manager geeft Roadmap &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=nl-NL) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Zie [&#x200B; Recente Updates van de Documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2023.12.0) is 14 december 2023. De volgende release met functies (2024.1.0) is gepland voor 25 januari 2023.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [&#x200B; hier &#x200B;](/help/release-notes/maintenance/latest.md) vinden.

<!-- 

## Release Video {#release-video}

Have a look at the December 2023 Release Overview video for a summary of the features added in the 2023.12.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

-->

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Programma voor vroege adoptie {#sites-early-adopter}

**u kunt hefboomwerking de [&#x200B; Operationele Dienst van Telemetrie](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** om cliënt-zijinzameling voor AEM as a Cloud Service toe te laten.

Operationele telemetriegegevensservice biedt een nauwkeuriger weergave van gebruikersinteracties, waardoor een betrouwbare maatstaf voor de betrokkenheid van websites wordt geboden. Het is een geweldige kans om geavanceerde inzichten in uw paginaprestaties te krijgen. Terwijl dit voor klanten nuttig is die of Adobe-Geleide CDN of niet-Adobe-Beheerde CDN gebruiken. Bovendien, voor klanten die een niet-Adobe beheerde CDN gebruiken, kan het geautomatiseerde verkeer nu voor hen worden toegelaten, waarbij de behoefte wordt weggenomen om het even welk verkeersrapport met Adobe te delen.

Als u deze nieuwe functie wilt testen en uw feedback wilt delen, stuurt u een e-mail naar `aemcs-rum-adopter@adobe.com` met uw domeinnaam voor de productie-, stage- en ontwikkelomgeving via uw e-mailadres dat bij uw Adobe ID hoort. Het productteam van Adobe zal dan de Operationele Dienst van de Gegevens van de Telemetrie voor u toelaten.


## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in Assets View {#assets-view-features}

**creeer beelden GenAI met Adobe Firefly**

Maak nieuwe afbeeldingen op basis van zoekopdrachten met de Adobe Firefly-functie voor tekst naar afbeelding (Adobe Firefly-licentie vereist).

![&#x200B; de integratie van Assets Firefly &#x200B;](/help/assets/assets/assets-firefly-integration.png)

**vind Vergelijkbare Beelden**

U kunt nu eenvoudig inhoud zoeken door een afbeelding te selecteren en vergelijkbare afbeeldingen weer te geven in de Experience Manager Assets-opslagplaats.

<!--

* **Smart tags blocklist**: Experience Manager Assets now enables you to define a list of blocked tags. These tags are automatically removed from the auto-generated smart tags when you upload assets to the repository. This capability performs tags governance and saves a lot of time as you can add a tag to the block list and AEM Assets automatically excludes it from the list of tags for any of the assets that are added to the repository.

  ![storage usage insights](/help/assets/assets/block-tags.png)


**Video Preview**: AEM Assets now generates preview renditions of all supported video formats by default, without the need to configure a processing profile.

-->

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Experience Manager Forms] {#forms-features}

* **[verbind een Aangepaste Forms met de Lijst van SharePoint Microsoft®](/help/forms/configure-submit-actions-core-components.md#submit-to-sharepoint)**: AEM Forms verstrekt een integratie OTB om vormgegevens rechtstreeks naar de Lijst van SharePoint voor te leggen, latend u de mogelijkheden van de Lijsten van SharePoint gebruiken. U kunt de Lijst van Microsoft SharePoint als gegevensbron voor een Model van de Gegevens van de Vorm vormen en **gebruiken voorleggen gebruikend het Model van de Gegevens van de Vorm** actie om een Aangepast Vorm met de Lijst van SharePoint te verbinden.

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Programma voor vroege adoptie {#forms-early-adopter}

* **[voorlegt een Aangepast Vorm aan het Scenario van de Fusie van Adobe Workfront](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service biedt een uit-van-de-doosopties aan om een Aangepast Vorm met Adobe Workfront moeiteloos aan te sluiten. Dit vereenvoudigt het proces om een Adaptief Formulier aan een scenario van Adobe Workfront voor te leggen, toelatend u een scenario van de Fusie van Workfront op voorlegging van een Aangepast Vorm teweegbrengt.

* **[Recht aan linkertaalsteun](/help/forms/supporting-new-language-localization-core-components.md)**: De adaptieve Forms die op de Componenten van de Kern wordt gebouwd kan nu in een (RTL) taal zoals Arabisch, Perzisch, en Urdu worden voorgesteld. De RTL-talen worden wereldwijd gesproken door meer dan 2 miljard mensen. Door een formulier in RTL-taal te gebruiken, kunt u het bereik van uw adaptieve formulieren uitbreiden naar deze verschillende doelgroepen en selecteren in RTL-markten. In bepaalde regio&#39;s is het ook een wettelijk mandaat om formulieren in de lokale taal te verstrekken. Door lokale talen aan te passen, opent u niet alleen deuren voor een breder publiek, maar zorgt u ook voor naleving van relevante wetten en regels.

  ![&#x200B; Recht aan linkertaalsteun &#x200B;](/help/forms/assets/right-to-left-language-support.png)

* **[bescherm uw documenten met DocAssurance APIs (Deel van Communicatie APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: De DocAssurance APIs machtigt u om gevoelige informatie te beschermen door de documenten te ondertekenen en te coderen. Door versleuteling wordt de inhoud van een document omgezet in een onleesbare indeling, zodat alleen geautoriseerde gebruikers toegang hebben. Deze versterkte beschermingslaag beschermt niet alleen waardevolle gegevens tegen ongeoorloofde ogen, maar zorgt ook voor gemoedsrust. Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen.

  U kunt vanuit uw officiële e-mailid naar `aem-forms-ea@adobe.com` schrijven om deel te nemen aan het programma voor vroegtijdige adoptie en toegang tot deze functie aanvragen.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Programma voor vroege adoptie van domeintoewijzing {#cdn-config-early-adopter}

Naast onlangs vrijgegeven [&#x200B; Regels van de Filter van het Verkeer &#x200B;](/help/security/traffic-filter-rules-including-waf.md), die de naar keuze licentiebare regels van de Firewall van de Toepassing van het Web (WAF) omvat, is er een kans om de Pijpleiding van de Configuratie te gebruiken om andere types van configuratie te verklaren en op te stellen CDN. We zouden graag iets over uw gebruiksgevallen horen, zoals:
* 301/302 omleidingen op de client
* verzoeken aan de rand van willekeurige oorsprong proxying
* URL-transformaties
* verzoek- of antwoordheaders instellen of wijzigen
* aangepaste foutpagina&#39;s wanneer de CDN AEM niet kan bereiken
* verificatie via gebruikersnaam/wachtwoord
* andere handige CDN-configuraties

Verzend een e-mail naar **aemcs-cdn-config-adopter@adobe.com** van uw officiële e-mailidentiteitskaart met uw terugkoppelt.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [&#x200B; hier &#x200B;](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [&#x200B; hier &#x200B;](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
