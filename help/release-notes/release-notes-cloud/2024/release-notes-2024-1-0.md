---
title: Nota's van de versie voor 2024.1.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2024.1.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 9f5d97c6-6536-4593-acbf-cbe8bf9b5eeb
feature: Release Information
role: Admin
source-git-commit: 8be0a9894bb5b3a138c0ec40a437d6c8e4bc7e25
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---

# Opmerkingen bij de release 2024.1.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2024.1.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=nl-NL) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2024.1.0) is 25 januari 2024. De volgende release met functies (2024.3.0) is gepland voor 11 april 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van januari 2024 voor een overzicht van de functies die in de release van 2024.1.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3427041?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Extension Manager in AEM Sites {#sites-extension-manager}

**Onderzoek nieuwe [ Extension Manager in AEM Sites ](https://developer.adobe.com/uix/docs/extension-manager/)** om uw opstelling van AEM te personaliseren door uitbreidingen te vormen UI.

![ Extension Manager in AEM Sites ](/help/assets/sites/extension-manager/homepage.png)

Extension Manager in AEM Sites laat ontwikkelaars en artsen toe om tot [ uitbreidingen UI ](https://developer.adobe.com/uix/docs/) toegang te hebben te beheren en aan te passen die met [ App Builder van Adobe ](https://developer.adobe.com/app-builder/) worden gebouwd om de functionaliteit van AEM Sites te verbeteren.
Met de Extension Manager kunt u:

* Extensies per geval in- of uitschakelen;
* Configureren van extensieparameters;
* Een voorvertoning weergeven van extensies en een deelbare voorbeeldkoppeling genereren;
* Detecteer functies voor uitbreidbaarheid van de gebruikersinterface via interactieve demo&#39;s.
* Toegang tot experimentele Adobe-functies via eersteklas extensies.

We zijn actief op zoek naar feedback en nieuwe gebruiksgevallen voor UI-extensies. Stuur een e-mail naar `uix@adobe.com` als u verbinding wilt maken.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Functies van de vooruitgave in de beheerdersweergave {#admin-view-prerelease}

**de vertoningen van de Voorproef voor alle gesteunde videotypes**

Experience Manager Assets genereert nu standaard voorvertoningen van alle ondersteunde videotypen zonder dat hiervoor een configuratie met een verwerkingsprofiel nodig is

### Assets-weergave {#assets-view-features}

**Slimme lijst van gewezen personen van markeringen**

Met de Elementen kunt u nu lijst van gewezen personen definiëren die woorden bevat die niet als slimme tags aan elementen mogen worden toegevoegd wanneer ze naar de opslagplaats worden geüpload. Met deze functie kunt u de naleving van het merk handhaven en de inspanningen voor het reduceren van slimme tags verminderen.

![ Slimme lijst van gewezen personen van Markeringen ](/help/assets/assets/block-tags.png)


## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Programma voor vroege adoptie {#forms-early-adopter}

* **[voorlegt een Aangepast Vorm aan het Scenario van de Fusie van Adobe Workfront](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service biedt een uit-van-de-doosopties aan om een Aangepast Vorm met Adobe Workfront moeiteloos aan te sluiten. Dit vereenvoudigt het proces om een Adaptief Formulier aan een scenario van Adobe Workfront voor te leggen, toelatend u een scenario van de Fusie van Workfront op voorlegging van een Aangepast Vorm teweegbrengt.

* **[Recht aan linkertaalsteun](/help/forms/supporting-new-language-localization-core-components.md)**: De adaptieve Forms die op de Componenten van de Kern wordt gebouwd kan nu in een (RTL) taal zoals Arabisch, Perzisch, en Urdu worden voorgesteld. De RTL-talen worden wereldwijd gesproken door meer dan 2 miljard mensen. Door een formulier in RTL-taal te gebruiken, kunt u het bereik van uw adaptieve formulieren uitbreiden naar deze verschillende doelgroepen en selecteren in RTL-markten. In bepaalde regio&#39;s is het ook een wettelijk mandaat om formulieren in de lokale taal te verstrekken. Door lokale talen aan te passen, opent u niet alleen deuren voor een breder publiek, maar zorgt u ook voor naleving van relevante wetten en regels.

  ![ Recht aan linkertaalsteun ](/help/forms/assets/right-to-left-language-support.png)

* **[bescherm uw documenten met DocAssurance APIs (Deel van Communicatie APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: De DocAssurance APIs machtigt u om gevoelige informatie te beschermen door de documenten te ondertekenen en te coderen. Door versleuteling wordt de inhoud van een document omgezet in een onleesbare indeling, zodat alleen geautoriseerde gebruikers toegang hebben. Deze versterkte beschermingslaag beschermt niet alleen waardevolle gegevens tegen ongeoorloofde ogen, maar zorgt ook voor gemoedsrust. Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen.

  U kunt vanuit uw officiële e-mailid naar `aem-forms-early-adopter-program@adobe.com` schrijven om deel te nemen aan het programma voor vroegtijdige adoptie en toegang tot deze functie aanvragen.

* **[u kunt hefboomwerking de Operationele Dienst van Telemetrie](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** om cliënt-zijinzameling voor AEM as a Cloud Service toe te laten.
De operationele telemetrieservice biedt een nauwkeuriger weergave van gebruikersinteracties, waardoor een betrouwbare maatstaf voor de betrokkenheid van websites wordt gegarandeerd. Het is een geweldige kans om geavanceerde inzichten in uw paginaprestaties te krijgen. Terwijl dit voor klanten nuttig is die of Adobe-Geleide CDN of niet-Adobe-Beheerde CDN gebruiken. Bovendien, voor klanten die een niet-Adobe beheerde CDN gebruiken, kan het geautomatiseerde verkeer nu voor hen worden toegelaten, waarbij de behoefte wordt weggenomen om het even welk verkeersrapport met Adobe te delen.

  Als u interesse hebt in het testen van deze nieuwe functie en het delen van uw feedback, stuurt u een e-mail naar `aemcs-rum-adopter@adobe.com`, samen met uw domeinnaam voor elk van de omgevingen waarvoor u Operationele telemetrie wilt inschakelen via uw e-mailadres dat is gekoppeld aan uw Adobe ID. Het productteam van Adobe zal dan de Operationele Dienst van de Telemetrie voor u toelaten.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Ondersteuning voor Dynatrace {#dynatrace}

Dynatrace-klanten kunnen hun AEM-gebruik controleren. [ las hoe ](/help/implementing/cloud-manager/dynatrace.md) om connectiviteit met uw milieu van Dynatrace voor toepassingsprestatie controle te verzoeken. Houd er rekening mee dat New Relic APM, dat voor alle klanten beschikbaar is, geen gegevens meer zal verzamelen als Dynatrace is ingeschakeld.

### RDE-ondersteuning voor front-end code met behulp van sitemenu&#39;s en sitesjablonen: Vroege adopter-programma {#rde-frontend-early-adopter}

{de milieu&#39;s van de Snelle Ontwikkeling van 0} (RDEs) [&#128279;](/help/implementing/developing/introduction/rapid-development-environments.md) steunen nu front-end code die op [ plaatsthema&#39;s ](/help/sites-cloud/administering/site-creation/site-themes.md) en [ plaatsmalplaatjes ](/help/sites-cloud/administering/site-creation/site-templates.md) wordt gebaseerd, voor vroege adopters.  Met RDEs, wordt dit gedaan gebruikend een richtlijn van de bevellijn, eerder dan a [ front-end pijpleiding ](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Gelieve te bereiken uit aan **aemcs-rde-support@adobe.com** om het uit te proberen en te verstrekken terugkoppelt.

### Programma voor vroege adoptie van domeintoewijzing {#cdn-config-early-adopter}

Naast onlangs vrijgegeven [ Regels van de Filter van het Verkeer ](/help/security/traffic-filter-rules-including-waf.md), die de naar keuze licentiebare regels van de Firewall van de Toepassing van het Web (WAF) omvat, is er een kans om de Pijpleiding van de Configuratie te gebruiken om [ andere types van configuratie CDN ](/help/implementing/dispatcher/cdn-configuring-traffic.md) te verklaren en op te stellen. Sluit me aan bij het vroege adoptieprogramma door **aemcs-cdn-config-adopter@adobe.com** te e-mailen om toegang tot te krijgen:
* 301/302 omleidingen op de client
* verzoeken aan de rand van willekeurige oorsprong proxying
* URL-transformaties
* verzoek- of antwoordheaders instellen of wijzigen
* aangepaste foutpagina&#39;s wanneer de CDN AEM niet kan bereiken

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
