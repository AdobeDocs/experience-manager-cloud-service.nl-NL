---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: d202b0543020b277de982e3965475074a71b286d
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de release met functies voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Vanaf hier kunt u navigeren om notities van eerdere versies weer te geven. bijvoorbeeld voor die in 2021, 2022, enzovoort.
>
>Kijk eens naar de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie over de volgende activering van functies voor [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release met functies (2023.2.0) is 12 april 2023. De volgende release met functies (2023.4.0) is gepland voor 25 mei 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van februari 2023 voor een overzicht van de functies die zijn toegevoegd in de release van 2023.2.0:

>[!VIDEO](https://video.tv.adobe.com/v/3416885/?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Experience Manager Sites] prelease {#prerelease-sites}

* Exporteer inhoudsfragmenten van AEM als cloudservice naar Adobe target zoals JSON biedt.
* Ondersteuning voor paginering en sortering van GraphQL en verbeteringen in de interne cache helpen nu de prestaties van losgekoppelde clienttoepassingen te verbeteren wanneer u grote inhoudssets ophaalt van AEM met behulp van complexe GraphQL-query&#39;s en -filters.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Ondersteuning voor het nieuwe protocol (DASH - Dynamic Adaptive Streaming via HTTP) dat is gestart voor Adaptive streaming in Dynamic Media-video (met CMAF ingeschakeld):
   * Adaptief streamen (DASH/HLS) zorgt voor een betere weergave voor eindgebruikers voor video&#39;s
   * DASH is het internationale standaardprotocol voor adaptieve videostreaming en wordt op grote schaal toegepast in de branche
   * Beschikbaar in NA, beschikbaar via een ondersteuningsticket, binnenkort verkrijgbaar in APAC, EMEA

* Extra ondersteuning voor WebP-afbeeldingen om automatisch metagegevens te extraheren, miniaturen en aangepaste uitvoeringen te genereren. De functie Slimme tag wordt nu ook ondersteund voor deze bestanden.

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] {#new-features-available-in-channel}

* **[Gebruik kerncomponenten voor gegevensvastlegging om Adaptive Forms te bouwen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en)**: [Adaptieve Forms-editor gebruiken](/help/forms/creating-adaptive-form-core-components.md) formulieren maken op basis van gestandaardiseerde componenten voor het vastleggen van gegevens (Core Components). Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijvingservaring.

* **[Ondersteuning voor de front-end pijpleiding voor de styling van de core component, gebaseerd op Adaptive Forms](/help/forms/using-themes-in-core-components.md)**: Gebruik gestandaardiseerde BEM-gebaseerde thema&#39;s voor Core Components-based Adaptive Forms door deze te implementeren met Front-end Deployment-pijplijn om de vormgeving van uw formulieren te verbeteren en zich aan te passen aan de door uw organisatie goedgekeurde ontwerprichtlijnen.

* **[Document met record genereren voor op kerncomponenten gebaseerde adaptieve Forms](/help/forms/generate-document-of-record-core-components.md)**: Maak een recorddocument met overgelegde gegevens voor Adaptive Forms die zijn gemaakt met kerncomponenten voor archivering of referentie voor eindgebruikers, in gedrukte vorm of in documentindeling.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[Efficiënt formulieren maken met de functie Een adaptief formulier opslaan als sjabloon](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: De ontwikkeling van formulieren versnellen en standaardiseren door bestaande, door een merk goedgekeurde formulieren op te slaan als formuliersjablonen en deze snel weer te gebruiken.

* **[AEM Forms verbinden met databases die door JDBC worden ondersteund](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: Maak rechtstreeks vanuit AEM Cloud-service verbinding met bedrijfsdatabases via het JDBC-protocol, zonder dat u deze via de REST API toegankelijk hoeft te maken.

* **[Integreer met REST Endpoints die Open API 3.0 gebruiken](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: Naadloos integreren in recordsystemen die Open API 3.0 ondersteunen voor het opslaan en ophalen van gegevens met behulp van formuliergegevensmodellen.

* **[Een adaptief formulier delen voor revisie](/help/forms/create-reviews-forms.md)**: Met het mechanisme voor adaptieve Forms-revisie kan een of meer revisoren het formulier reviseren.


### Functies in [!DNL Forms] prerelease {#prerelease-features-forms}

* **[Adaptieve Forms verzenden naar Microsoft SharePoint en Microsoft OneDrive](/help/forms/configuring-submit-actions.md)**: Verbeter de flexibiliteit van zakelijke gebruikers om snel nieuwe formulieren te starten en verzonden gegevens op te slaan in de dagelijkse tools die ze gebruiken, zoals de Microsoft SharePoint-site of de OneDrive-map.

![Adaptieve Forms verzenden naar Microsoft SharePoint en Microsoft OneDrive](/help/forms/assets/onedrive-and-sharepoint.jpg)


## Forms-programma voor vroege adoptie zonder adapter {#forms-early-adopter}

Gebruik Headless Adaptive Forms om uw ontwikkelaars in staat te stellen interactieve formulieren te maken, te publiceren en te beheren die via API&#39;s kunnen worden geopend en gebruikt in plaats van via een traditionele grafische gebruikersinterface. Met behulp van hoofdloze adaptieve formulieren kunt u:

* multikanaalformulieren van hoge kwaliteit maken in de programmeertaal van uw keuze
* U kunt zelf formulieren integreren in uw bureaublad en mobiele apps, websites en chattoepassingen
* gebruik uw eigen UI-componenten opnieuw met formuliertoepassingen
* de kracht van Adobe Experience Manager Forms benutten

U kunt vanaf uw officiële e-mailadres een e-mail sturen naar aem-forms-headless@adobe.com om deel te nemen aan het programma voor vroegtijdige adoptie.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier.](/help/implementing/cloud-manager/release-notes/current.md)

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst vinden van de versies van de Hulpmiddelen van de Migratie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
