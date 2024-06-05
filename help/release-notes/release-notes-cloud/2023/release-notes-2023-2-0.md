---
title: Opmerkingen bij de release 2023.2.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2023.2.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 671056e6-84cc-4c2c-bca3-fde68d5cc835
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.2.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.2.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2021, 2022, enzovoort.
>
>Kijk eens naar de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie over de volgende activering van functies voor [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release met functies (2023.2.0) is 12 april 2023. De volgende release met functies (2023.4.0) is gepland voor 7 juni 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van februari 2023 voor een overzicht van de functies die zijn toegevoegd in de release van 2023.2.0:

>[!VIDEO](https://video.tv.adobe.com/v/3416885/?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Experience Manager Sites] prelease {#prerelease-sites}

* Exporteer inhoudsfragmenten van AEM als cloudservice naar het doel van de Adobe dat JSON biedt.
* Ondersteuning voor paginering en sortering van GraphQL en verbeteringen in de interne cache helpen nu de prestaties van losgekoppelde clienttoepassingen te verbeteren wanneer u grote inhoudssets ophaalt van AEM met behulp van complexe GraphQL-query&#39;s en -filters.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Ondersteuning voor het nieuwe protocol (DASH - Dynamic Adaptive Streaming via HTTP) dat is gestart voor Adaptive streaming in Dynamic Media-video (met CMAF ingeschakeld):
   * Adaptief streamen (DASH/HLS) zorgt voor een betere kijkervaring voor video&#39;s
   * DASH is het internationale standaardprotocol voor adaptieve videostreaming en wordt op grote schaal toegepast in de branche
   * Beschikbaar in NA, beschikbaar via een ondersteuningsticket, binnenkort verkrijgbaar in APAC, EMEA

* Extra ondersteuning voor WebP-afbeeldingen om automatisch metagegevens te extraheren, miniaturen en aangepaste uitvoeringen te genereren. De mogelijkheden Slimme tags en Slim uitsnijden worden nu ook ondersteund voor deze bestanden.

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] {#new-features-available-in-channel}

* **[Gebruik kerncomponenten voor het vastleggen van gegevens om Adaptieve Forms te bouwen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)**: [Adaptieve Forms-editor gebruiken](/help/forms/creating-adaptive-form-core-components.md) formulieren maken op basis van gestandaardiseerde componenten voor het vastleggen van gegevens (Core Components). Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijvingservaring.

* **[Ondersteuning voor de front-end pijpleiding voor de styling van de core component, gebaseerd op Adaptive Forms](/help/forms/using-themes-in-core-components.md)**: Gebruik gestandaardiseerde BEM-gebaseerde thema&#39;s voor Core Components-based Adaptive Forms door deze te implementeren met Frontend Deployment-pijplijn om het uiterlijk van uw formulieren te verbeteren en zich aan te passen aan de door uw organisatie goedgekeurde ontwerprichtlijnen.

* **[Document met record genereren voor op kerncomponenten gebaseerde adaptieve Forms](/help/forms/generate-document-of-record-core-components.md)**: Maak een recorddocument dat overgelegde gegevens voor Adaptive Forms bevat die zijn gemaakt met kerncomponenten voor archivering of referentie voor eindgebruikers, in gedrukte vorm of in documentindeling.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[Efficiënt formulieren maken met de functie Een adaptief formulier opslaan als sjabloon](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: Versnel en standaardiseer de ontwikkeling van formulieren door bestaande, door een merk goedgekeurde formulieren op te slaan als formuliersjablonen en deze snel te hergebruiken.

* **[AEM Forms verbinden met databases die door JDBC worden ondersteund](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: Maak rechtstreeks vanuit AEM Cloud-service verbinding met bedrijfsdatabases via het JDBC-protocol, zonder dat u deze via de REST API toegankelijk hoeft te maken.

* **[Integreer met REST Endpoints die Open API 3.0 gebruiken](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: Naadloos integreren in recordsystemen die Open API 3.0 ondersteunen voor het opslaan en ophalen van gegevens met behulp van formuliergegevensmodellen.

* **[Een adaptief formulier delen voor revisie](/help/forms/create-reviews-forms.md)**: Gebruik het revisiemechanisme van Adaptive Forms om een of meer revisoren in staat te stellen het formulier te reviseren.


### Functies in [!DNL Forms] prerelease {#prerelease-features-forms}

* **[Adaptieve Forms verzenden naar Microsoft SharePoint en Microsoft OneDrive](/help/forms/configuring-submit-actions.md)**: Verbeter de flexibiliteit van zakelijke gebruikers om snel nieuwe formulieren te starten en verzonden gegevens op te slaan in de dagelijkse tools die ze gebruiken, zoals de Microsoft SharePoint-site of de OneDrive-map.

![Adaptieve Forms verzenden naar Microsoft SharePoint en Microsoft OneDrive](/help/forms/assets/onedrive-and-sharepoint.jpg)


## Forms-programma voor vroege adoptie zonder adapter {#forms-early-adopter}

Gebruik Headless Adaptive Forms om uw ontwikkelaars in staat te stellen interactieve formulieren te maken, te publiceren en te beheren die via API&#39;s kunnen worden geopend en gebruikt in plaats van via een traditionele grafische gebruikersinterface. Met behulp van hoofdloze adaptieve formulieren kunt u:

* multikanaalformulieren van hoge kwaliteit maken in de programmeertaal van uw keuze
* U kunt zelf formulieren integreren in uw bureaublad en mobiele apps, websites en chattoepassingen
* gebruik uw eigen UI-componenten opnieuw met formuliertoepassingen
* de kracht van Adobe Experience Manager Forms gebruiken

U kunt vanaf uw officiële e-mailadres een e-mail sturen naar aem-forms-headless@adobe.com om deel te nemen aan het programma voor vroegtijdige adoptie.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
