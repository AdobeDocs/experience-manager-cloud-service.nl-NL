---
title: Opmerkingen bij de release 2024.1.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2024.1.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: 7d35376057297bac8653341cd5309debbc640e51
workflow-type: tm+mt
source-wordcount: '1027'
ht-degree: 0%

---


# Opmerkingen bij de release 2024.1.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de release met functies voor de versie 2024.1.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Kijk eens naar de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie over de volgende activering van functies voor [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release met functies (2024.1.0) is 25 januari 2024. De volgende release met functies (2024.3.0) is gepland voor 11 april 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van januari 2024 voor een overzicht van de functies die in de release van 2024.1.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3427041?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Extension Manager in AEM Sites {#sites-extension-manager}

**Ontdek de nieuwe [Extension Manager in AEM Sites](https://developer.adobe.com/uix/docs/extension-manager/)** om uw AEM opstelling te personaliseren door uitbreidingen te vormen UI.

![Extension Manager in AEM Sites](/help/assets/sites/extension-manager/homepage.png)

Met de Extension Manager in AEM Sites kunnen ontwikkelaars en beoefenaars toegang krijgen tot de toepassing, beheren en aanpassen [UI-extensies](https://developer.adobe.com/uix/docs/) gebouwd met [Adobe App Builder](https://developer.adobe.com/app-builder/) verbeteren van de functionaliteit van AEM Sites.
Met de Extension Manager kunt u:

* Extensies per geval in- of uitschakelen;
* Configureren van extensieparameters;
* Een voorvertoning weergeven van extensies en een deelbare voorbeeldkoppeling genereren;
* Detecteer functies voor uitbreidbaarheid van de gebruikersinterface via interactieve demo&#39;s.
* Toegang tot experimentele functies van de Adobe via eersteklas uitbreidingen.

We zijn actief op zoek naar feedback en nieuwe gebruiksgevallen voor UI-extensies. Stuur een e-mail naar `uix@adobe.com`.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Functies van de vooruitgave in de beheerdersweergave {#admin-view-prerelease}

**Voorvertoning van vertoningen weergeven voor alle ondersteunde videotypen**

Experience Manager Assets genereert nu standaard voorvertoningen van alle ondersteunde videotypen zonder dat hiervoor een configuratie met een verwerkingsprofiel nodig is

### Weergave Elementen {#assets-view-features}

**Lijst van gewezen personen slimme tags**

Met Assets Essentials kunt u nu lijst van gewezen personen definiëren die woorden bevat die niet als slimme tags aan elementen mogen worden toegevoegd wanneer deze naar de opslagplaats worden geüpload. Met deze functie kunt u de naleving van het merk handhaven en de inspanningen voor het reduceren van slimme tags verminderen.

![Lijst van gewezen personen Slimme tags](/help/assets/assets/block-tags.png)


## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Programma voor vroege adoptie {#forms-early-adopter}

* **[Een adaptief formulier verzenden naar het Adobe Workfront Fusion-scenario](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service biedt een out-of-the-box optie om een adaptief formulier moeiteloos aan te sluiten op Adobe Workfront. Dit vereenvoudigt het proces om een Adaptief Formulier aan een scenario van Adobe Workfront voor te leggen, toelatend u een scenario van de Fusie van Workfront op voorlegging van een Aangepast Vorm teweegbrengt.

* **[Ondersteuning voor talen van rechts naar links](/help/forms/supporting-new-language-localization-core-components.md)**: Adaptieve Forms die is gebaseerd op Core Components, kan nu worden weergegeven in een RTL-taal (rechts naar links), zoals Arabisch, Perzisch en Urdu. De RTL-talen worden wereldwijd gesproken door meer dan 2 miljard mensen. Door een formulier in RTL-taal te gebruiken, kunt u het bereik van uw adaptieve formulieren uitbreiden naar deze verschillende doelgroepen en selecteren in RTL-markten. In bepaalde regio&#39;s is het ook een wettelijk mandaat om formulieren in de lokale taal te verstrekken. Door lokale talen aan te passen, opent u niet alleen deuren voor een breder publiek, maar zorgt u ook voor naleving van relevante wetten en regels.

  ![Ondersteuning voor talen van rechts naar links](/help/forms/assets/right-to-left-language-support.png)

* **[Protect uw documenten met DocAssurance-API&#39;s (onderdeel van communicatie-API&#39;s)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: De DocAssurance-API&#39;s stellen u in staat gevoelige informatie te beveiligen door de documenten te ondertekenen en te versleutelen. Door versleuteling wordt de inhoud van een document omgezet in een onleesbare indeling, zodat alleen geautoriseerde gebruikers toegang hebben. Deze versterkte beschermingslaag beschermt niet alleen waardevolle gegevens tegen ongeoorloofde ogen, maar zorgt ook voor gemoedsrust. Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen.

  U kunt schrijven naar `aem-forms-early-adopter-program@adobe.com` van uw officiële e-mailidentiteitskaart om zich bij het vroege adoptieprogramma aan te sluiten en toegang tot het vermogen te verzoeken.

* **[U kunt gebruikmaken van de gegevensservice Real User Monitoring (RUM)](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** om client-side verzameling voor AEM as a Cloud Service in te schakelen.
Real User Monitoring (RUM) Data Service biedt een nauwkeuriger weergave van gebruikersinteracties, waardoor een betrouwbare maatstaf voor de betrokkenheid van websites wordt geboden. Het is een geweldige kans om geavanceerde inzichten in uw paginaprestaties te krijgen. Terwijl dit voor klanten nuttig is die of Adobe-beheerde CDN of niet-Adobe-beheerde CDN gebruiken. Bovendien, voor klanten die een niet-Adobe beheerde CDN gebruiken, kan het geautomatiseerde verkeer nu voor hen worden toegelaten, waarbij de behoefte wordt verwijderd om het even welk verkeersrapport met Adobe te delen.

  Als je deze nieuwe functie wilt testen en je feedback wilt delen, stuur dan een e-mail naar `aemcs-rum-adopter@adobe.com`, samen met uw domeinnaam voor elk van de omgevingen waarvoor u RUM wilt inschakelen vanaf uw e-mailadres dat is gekoppeld aan uw Adobe ID. Het productteam van Adobe zal dan de Echte Dienst van Gegevens van de Controle van de Gebruiker (RUM) voor u toelaten.

## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### Ondersteuning voor Dynatrace {#dynatrace}

Dynatrace-klanten kunnen hun AEM controleren. [Lees hoe](/help/implementing/cloud-manager/dynatrace.md) om connectiviteit met uw milieu van de Accolade voor toepassingsprestatie controle te verzoeken. Houd er rekening mee dat New Relic APM, dat voor alle klanten beschikbaar is, geen gegevens meer zal verzamelen als Dynatrace is ingeschakeld.

### RDE-ondersteuning voor front-end code met behulp van sitemenu&#39;s en sitesjablonen: Vroege adopter-programma {#rde-frontend-early-adopter}

[Rapid Development Environment (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) nu ondersteuning voor front-end code op basis van [sitethema&#39;s](/help/sites-cloud/administering/site-creation/site-themes.md) en [sitesjablonen](/help/sites-cloud/administering/site-creation/site-templates.md), voor vroege adoptie. Met RDEs, wordt dit gedaan gebruikend een richtlijn van de bevellijn, eerder dan een [front-end pijpleiding](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Neem contact op met **aemcs-rde-support@adobe.com** om het uit te proberen en feedback te geven.

### Programma voor vroege adopter van CDN-configuratie {#cdn-config-early-adopter}

Naast de onlangs vrijgelaten [Regels voor verkeersfilters](/help/security/traffic-filter-rules-including-waf.md), die de naar keuze licentiable regels van de Firewall van de Toepassing van het Web (WAF) omvat, is er een kans om de Pijpleiding van de Configuratie te gebruiken om te verklaren en op te stellen [andere typen CDN-configuratie](/help/implementing/dispatcher/cdn-configuring-traffic.md). Deelnemen aan het programma voor vroege adoptie via e-mail **aemcs-cdn-config-adopter@adobe.com** toegang krijgen tot:
* 301/302 omleidingen op de client
* verzoeken aan de rand van willekeurige oorsprong proxying
* URL-transformaties
* verzoek- of antwoordheaders instellen of wijzigen
* aangepaste foutpagina&#39;s wanneer de CDN AEM niet kan bereiken

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
