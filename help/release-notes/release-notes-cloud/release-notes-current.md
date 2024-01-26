---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 8c33426c38b087c83b945572374089ad9cb44daf
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de release met functies voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Kijk eens naar de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie over de volgende activering van functies voor [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release met functies (2024.1.0) is 25 januari 2024. De volgende release met functies (2024.2.0) is gepland voor 29 februari 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van januari 2024 voor een overzicht van de functies die in de release van 2024.1.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3427041?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Extension Manager in AEM Sites {#sites-extension-manager}

**Ontdek de nieuwe [Extension Manager in AEM Sites](https://developer.adobe.com/uix/docs/extension-manager/)** om uw AEM opstelling te personaliseren door uitbreidingen te vormen UI.

![Extension Manager in AEM Sites](/help/assets/sites/extension-manager/homepage.png)

Met de Extension Manager in AEM Sites kunnen ontwikkelaars en professionals UI-extensies die zijn gemaakt om de functionaliteit van AEM Sites te verbeteren, openen, beheren en aanpassen.
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

## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### Ondersteuning voor Dynatrace {#dynatrace}

Dynatraciklanten kunnen hun AEM gebruiken controleren. [Lees hoe](/help/implementing/cloud-manager/dynatrace.md) om connectiviteit met uw milieu van de Accolade voor toepassingsprestatie controle te verzoeken. Merk op dat New Relic APM, dat voor alle klanten beschikbaar is, zal ophouden met het verzamelen van gegevens als Dynatrace wordt toegelaten.

### RDE-ondersteuning voor front-end code met behulp van sitemenu&#39;s en sitesjablonen: Vroege adopter-programma {#rde-frontend-early-adopter}

[Rapid Development Environment (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) nu ondersteuning voor front-end code op basis van [sitethema&#39;s](/help/sites-cloud/administering/site-creation/site-themes.md) en [sitesjablonen](/help/sites-cloud/administering/site-creation/site-templates.md), voor vroege adoptie. Met RDEs, wordt dit gedaan gebruikend een richtlijn van de bevellijn, eerder dan een [front-end pijpleiding](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Neem contact op met **aemcs-rde-support@adobe.com** om het uit te proberen en feedback te geven.

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
