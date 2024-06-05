---
title: Opmerkingen bij de release 2023.10.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2023.10.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 81a6cbd2-7101-429b-8572-2650c5bea963
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.10.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.10.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2021 of 2022, vrij te geven.
>
>Kijk eens naar de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie over de volgende activering van functies voor [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release met functies (2023.10.0) is 26 oktober 2023. De volgende functieversie (2023.11.0) is gepland voor 30 november 2023.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van oktober 2023 voor een overzicht van de functies die zijn toegevoegd in de release van 2023.10.0:

>[!VIDEO](https://video.tv.adobe.com/v/3425186/?quality=12)

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies {#assets-features}

**AEM Assets-invoegtoepassing voor Adobe Express**: Experience Manager Assets biedt nu een invoegtoepassing voor Adobe Express. Met de invoegtoepassing hebt u rechtstreeks vanuit de gebruikersinterface van de Adobe Express toegang tot de elementen die in Experience Manager Assets zijn opgeslagen. U kunt inhoud die in AEM Assets wordt beheerd, op het Express-canvas plaatsen en vervolgens nieuwe of bewerkte inhoud opslaan in een AEM Assets-opslagplaats. De invoegtoepassing biedt de volgende belangrijke voordelen:

* Groter hergebruik van inhoud door nieuwe elementen te bewerken en op te slaan in AEM

* Minder tijd en moeite in het algemeen om nieuwe elementen te maken of nieuwe versies van bestaande elementen te maken

  ![Elementen opnemen uit de invoegtoepassing Elementen](/help/assets/assets/aem-assets-add-on-include-assets.png)

### Nieuwe functies in de weergave Elementen {#assets-view-features}

* **Bulkimportmiddelen van OneDrive-gegevensbron**: Beheerders kunnen nu [Een groot aantal middelen importeren van OneDrive naar AEM Assets](/help/assets/bulk-import-assets-view.md#onedrive-developer-application). Tot de bijgewerkte lijst voor de ondersteunde gegevensbronnen voor bulkimport behoren Azure, AWS, Google Cloud, Dropbox en OneDrive.

  ![metagegevensformulier toewijzen aan een map](/help/assets/assets/bulk-import-source-details-onedrive.png)

* **Ondersteuning voor interdomeinrechten voor bibliotheken**: Experience Manager Assets stelt u nu in staat om toegang tot Creatives Cloud bibliotheken in een andere IMS-organisatie te configureren. Het maakt gemakkelijker toegang tot de recentste productoverschrijdende werkschema&#39;s tussen Creative Cloud en Experience Manager mogelijk en vermindert tijd en moeite voor creatieve personen.

### Functies voor pre-release beschikbaar in [!DNL Experience Manager Assets] {#prerelease-features-assets}

* **Dynamic Media**: [Ondersteuning voor multicaption- en multiaudiotracks voor video&#39;s in Dynamic Media](/help/assets/dynamic-media/video.md#about-msma)—U kunt nu eenvoudig meerdere bijschriften en audiotracks toevoegen aan een primaire video. Dit betekent dat uw video&#39;s toegankelijk zijn voor een breed publiek. U kunt één gepubliceerde primaire video aanpassen aan een wereldwijd publiek in meerdere talen en de richtlijnen voor toegankelijkheid voor verschillende geografische regio&#39;s naleven. Auteurs kunnen de bijschriften en audiotracks ook beheren vanaf één tabblad in de gebruikersinterface.

  ![Het tabblad Bijschriften en audiotracks op de pagina Eigenschappen van een geselecteerd video-element.](/help/release-notes/assets/msma-aem-cs.png)*Het tabblad Bijschriften en audiotracks op de pagina Eigenschappen van een geselecteerd video-element.*

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Experience Manager Forms] {#forms-features}

* **[Aangepaste eigenschappen voor Adaptive Forms](/help/forms/template-editor-core-components.md#add-a-custom-group-name-in-the-policy-of-template-editor)**: U kunt aangepaste kenmerken (sleutelwaardeparen) koppelen aan een formuliersjabloon of aan een adaptieve formuliercomponent, zodat formulierontwikkelaars dynamisch formuliergedrag kunnen aanbieden dat wordt aangepast op basis van de waarden van deze aangepaste kenmerken. Ontwikkelaars kunnen bijvoorbeeld verschillende uitvoeringen van een Forms-component zonder koptekst maken op mobiele apparaten, desktops of webplatforms, op basis van de waarden van aangepaste kenmerken. Hierdoor wordt de gebruikerservaring aanzienlijk verbeterd voor een groot aantal apparaten.

* **Thema&#39;s en sjablonen**: Kickstart uw formulierontwerpproces met onze nieuwe thema&#39;s en sjablonen, speciaal ontworpen voor ervaren professionals en nieuwe auteurs van formulieren. Dankzij deze nauwgezette thema&#39;s en sjablonen, die naadloos zijn gebouwd met Adaptive Forms Core Components, kunt u snel formulieren maken voor veelgebruikte toepassingen.

  ![Sjablonen uit de keuzelijst](/help/forms/assets/form-templates-ootb.png)


### Programma voor vroegtijdige adoptie {#forms-early-adopter}

* **[Protect uw documenten met DocAssurance-API&#39;s (onderdeel van communicatie-API&#39;s)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: De DocAssurance-API&#39;s stellen u in staat gevoelige informatie te beveiligen door de documenten te ondertekenen en te versleutelen. Door versleuteling wordt de inhoud van een document omgezet in een onleesbare indeling, zodat alleen geautoriseerde gebruikers toegang hebben. Deze versterkte beschermingslaag beschermt niet alleen waardevolle gegevens tegen ongeoorloofde ogen, maar zorgt ook voor gemoedsrust. Met de handtekening-API&#39;s kunt u de beveiliging en privacy van Adobe PDF-documenten die door uw organisatie worden gedistribueerd en ontvangen, beschermen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat alleen de beoogde ontvangers documenten kunnen wijzigen.

  U kunt schrijven naar `aem-forms-ea@adobe.com` van uw officiële e-mailidentiteitskaart om zich bij het vroege adoptieprogramma aan te sluiten en toegang tot het vermogen te verzoeken.

## [!DNL Experience Manager] als [!DNL Cloud Service] Stichting {#foundation}

### Regels voor verkeersfilters, inclusief WAF {#traffic-filter-rules-waf}

[Het verkeer van de filter bij de Adobe Beheerde CDN](/help/security/traffic-filter-rules-including-waf.md) door regels te verklaren die websiteverkeer door eigenschappen met inbegrip van url, IP adres, en gebruikersagent aanpassen - of de grenzen van het douaneverkeer plaatsen om tegen de aanvallen van Dos te beschermen. Klanten kunnen ook een licentie verlenen voor een set geavanceerde WAF-regels (Web Application Firewall) voor extra bescherming tegen geavanceerde websitebedreigingen.

Wij moedigen u aan om vertrouwd te raken met de regels van de verkeersfilter door [een zelfstudie proberen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/security/traffic-filter-and-waf-rules/overview.html)! Het begeleidt u door vestiging een nieuwe Pijpleiding van de Configuratie van de Manager van de Wolk, verklarende regels in een configuratiedossier, en het analyseren van CDN- logboeken voor kwaadwillig verkeer.

De filterregels van het verkeer zijn nu beschikbaar op ontwikkelomgevingen, met een geleidelijke uitrol aan stadium en prod milieu&#39;s in November. U kunt eerder toegang aanvragen in het werkgebied en de proefperiode via e-mail **aemcs-waf-adopter@adobe.com**.

De geavanceerde het verkeersfilterregels van WAF kunnen later dit jaar door de Verbeterde Veiligheid of WAF-DoS het dienstenaanbod van de Bescherming worden vergunning gegeven.

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
