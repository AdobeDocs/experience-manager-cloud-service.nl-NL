---
title: Opmerkingen bij de release 2023.1.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2023.1.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: f134fdbc-224b-404c-b20f-44cae8bad681
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.1.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.1.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2021, 2022, enzovoort.
>
>Kijk eens naar de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie over de volgende activering van functies voor [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] 2023.1.0 is de eigenschapversie 9 februari 2023. De volgende release met functies (2023.2.0) is gepland voor 12 april 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van januari 2023 voor een overzicht van de functies die in de release van 2023.1.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3413479/?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] prerelease {#prerelease-features-sites}

* De API voor het leveren van AEM GraphQL-inhoud ondersteunt nu GraphQL [Paginering](/help/headless/graphql-api/content-fragments.md#paging) en [Sorteren](/help/headless/graphql-api/content-fragments.md#sorting)om het ophalen en renderen van grote content efficiënter te maken. De paginering van GraphQL staat toe om de tijd van de vraagreactie te verbeteren door resultaten in subsets in tegenstelling tot allen in één keer terug te keren. Met GraphQL-sortering kunnen inhoudssets in de gewenste volgorde worden geplaatst, waardoor het voor een clienttoepassing eenvoudiger wordt om de inhoud te verwerken.  De responstijd van de query wordt verder verbeterd met Hybride filters in de AEM GraphQL-engine. Inhoud wordt nu vanuit JCR gelezen in kleinere sets die overeenkomen met queryfilters.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* In middelenrapporten is nu de mogelijkheid opgenomen voor beheerders om [downloadrapporten voor bestanden genereren](/help/assets/asset-reports.md) van de as a Cloud Service Experience Manager Assets-implementatie. Deze gegevens stellen Admins verder in staat om inzichten af te leiden van belangrijke succesmaatstaven om de acceptatie van Activa binnen uw onderneming en door klanten te meten.

  ![PDF-uitvoering voor andere indelingen](/help/release-notes/assets/choose_report.png)

* Experience Manager Assets nu [ondersteunt SAS Token](/help/assets/add-assets.md#asset-bulk-ingestor) naast de toegangstoets voor verificatie bij de verbinding met de Azure Blob Storage-gegevensbron voor het opnemen van elementen met het Bulk Import-gereedschap.

* Verbeterd beheer van CMYK-afbeeldingen in Asset compute, zodat u slimme uitsnijdtags en slimme tags voor CMYK-afbeeldingen kunt genereren.

### Nieuwe functies in [!DNL Assets] prerelease {#prerelease-features-assets}

* Experience Manager Assets ondersteunt nu [grootschalige ingebruikname van middelen van het Google Cloud Platform](/help/assets/add-assets.md#asset-bulk-ingestor) met het gereedschap Bulk importeren.

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] {#new-features-available-in-channel}

* **[Workflowstappen om niet-interactieve PDF-documenten en afdrukbare uitvoer te genereren](/help/forms/aem-forms-workflow-step-reference.md)**: Automatiseer het maken van niet-interactieve PDF-documenten en afdrukbare uitvoer voor uw bedrijfsprocessen met AEM workflowstappen, stroomlijnt het genereren van documenten en bespaart tijd.
* **[Gebruik voetnoten om citaten of extra informatie te verstrekken in Adaptief Forms](/help/forms/footnotes-richtextsupport.md)**: Gebruik voetnoten in een adaptief formulier om de informatie weer te geven over het invullen of gebruiken van een formulier. U kunt het ook gebruiken om tussen haakjes informatie, auteursrechttoestemmingen, en andere nuttige informatie te verstrekken.

### Nieuwe functies in [!DNL Forms] prerelease {#prerelease-features-forms}

* **[Gebruik kerncomponenten voor het vastleggen van gegevens om Adaptieve Forms te bouwen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)**: [Adaptieve Forms-editor gebruiken](/help/forms/creating-adaptive-form-core-components.md) formulieren maken op basis van gestandaardiseerde componenten voor het vastleggen van gegevens (Core Components). Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijvingservaring.
* **[Ondersteuning voor de front-end pijpleiding voor de styling van de core component, gebaseerd op Adaptive Forms](/help/forms/using-themes-in-core-components.md)**: Gebruik eenvoudig aanpasbare BEM-gebaseerde thema&#39;s voor Core Components-based Adaptive Forms door deze te implementeren met de Front-end-implementatiepijplijn om de vormgeving van uw formulieren te verbeteren.
* **[Document met record genereren voor op kerncomponenten gebaseerde adaptieve Forms](/help/forms/generate-document-of-record-core-components.md)**: Maak een record voor een op kerncomponenten gebaseerd adaptief formulier bij verzending voor langetermijnarchivering, in afdruk of in de documentindeling.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[Adaptieve Forms verzenden naar Microsoft SharePoint en Microsoft OneDrive](/help/forms/configuring-submit-actions.md)**: Stroomlijn de gegevensverzending met de mogelijkheid om adaptieve formuliergegevens rechtstreeks naar Microsoft SharePoint en Microsoft OneDrive te verzenden. U kunt zowel schema-gebaseerde als schema-loze gegevens voorleggen. Deze verzendacties vormen een aanvulling op de reeds beschikbare verzendacties.
* **[Efficiënt formulieren maken met de functie Een adaptief formulier opslaan als sjabloon](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: stroomlijn het formulieropbouwproces door een adaptief formulier op te slaan als een sjabloon en de sjablonen voor het volgende adaptieve formulier opnieuw te gebruiken.
* **[AEM Forms verbinden met databases die door JDBC worden ondersteund](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: Sluit uw AEM Forms-gegevensmodel eenvoudig aan op databases die JDBC ondersteunen, zodat u gegevens naadloos kunt lezen en schrijven.
* **[Integreer met REST Endpoints die Open API 3.0 gebruiken](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: Connect AEM Forms as a Cloud Service Form Data Models to REST endpoints die Open API Specification versie 3.0 ondersteunen, zodat u gegevens eenvoudig kunt verzenden en ontvangen.
* **[Een adaptief formulier delen voor revisie](/help/forms/create-reviews-forms.md)**: Gebruik het revisiemechanisme van Adaptive Forms om een of meer revisoren in staat te stellen het formulier te reviseren.

## [!DNL Experience Manager as a Cloud Service] Stichting {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* [Snelle ontwikkelomgevingen](/help/implementing/developing/introduction/rapid-development-environments.md) - RDE&#39;s stellen ontwikkelaars in staat om problemen snel op te lossen en nieuwe functies op AEM as a Cloud Service te implementeren.

  Snelle ontwikkelomgevingen zijn een nieuw type cloudomgeving dat is ontworpen als een snelle, consistente en uitbreidbare manier om die code te valideren en die lokaal werkt, en werken ook zoals wordt verwacht in de cloud. Gebruik de Hulpmiddelen van de Lijn van het Bevel, snel &quot;synchroniseer&quot;inhoudspakketten, bundels, inhoudsdossiers, configuratie OSGI, of berichtconfiguratie aan RDE. Zie dit in actie in de video hieronder:

  >[!VIDEO](https://video.tv.adobe.com/v/3413508/?quality=12&learn=on)

  Nadat code in de RDE met succes is gevalideerd, wordt het aangeraden om te worden geïmplementeerd in een Cloud Dev Environment om de kwaliteitspoorten van Cloud Manager uit te oefenen voordat u de code via productiepijplijn naar stadium- en productieomgevingen implementeert.

  Elk programma omvat één RDE en naar keuze, kunnen meer worden vergunning gegeven.

  >[!NOTE]
  >
  >RDEs zal geleidelijk in de komende weken worden ingevoerd; u kunt een e-mail naar aemcs-rde-support@adobe.com verzenden om aan de voorzijde van de lijn over te slaan.

* [Uitgebreide ondersteuning voor API-toegangstokens aan de serverzijde](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) - U kunt nu meerdere referenties genereren. Dit is handig voor scenario&#39;s waarin API&#39;s verschillende kenmerken hebben. Het is nu ook mogelijk om geloofsbrieven op een zelfbediening manier in te trekken.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U vindt de meest recente opmerkingen in de onderhoudsrelease [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
