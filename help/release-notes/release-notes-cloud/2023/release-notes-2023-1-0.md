---
title: Nota's van de versie voor 2023.1.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2023.1.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: f134fdbc-224b-404c-b20f-44cae8bad681
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.1.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.1.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2021, 2022, enzovoort.
>
>Heb een blik bij de [&#x200B; Experience Manager geeft Roadmap &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=nl-NL) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Zie [&#x200B; Recente Updates van de Documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] 2023.1.0-functieversie is 9 februari 2023. De volgende release met functies (2023.2.0) is gepland voor 12 april 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van januari 2023 voor een overzicht van de functies die in de release van 2023.1.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3413479/?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] prerelease {#prerelease-features-sites}

* De AEM de inhoudslevering API van GraphQL steunt nu GraphQL [&#x200B; het pagineren &#x200B;](/help/headless/graphql-api/content-fragments.md#paging) en [&#x200B; het sorteren &#x200B;](/help/headless/graphql-api/content-fragments.md#sorting), om het halen en het teruggeven van grote inhoudssets efficiënter te maken. De paginering van GraphQL staat toe om de tijd van de vraagreactie te verbeteren door resultaten in subsets in tegenstelling tot allen in één keer terug te keren. Met GraphQL-sortering kunnen inhoudssets in de gewenste volgorde worden geplaatst, waardoor het voor een clienttoepassing eenvoudiger wordt om de inhoud te verwerken.  De responstijd van de query wordt verder verbeterd met Hybride filters in de AEM GraphQL-engine. Inhoud wordt nu vanuit JCR gelezen in kleinere sets die overeenkomen met queryfilters.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* De Rapporten van Assets omvatten nu de capaciteit voor Beheerders om [&#x200B; rapporten van de activadownload &#x200B;](/help/assets/asset-reports.md) van de as a Cloud Service plaatsing van Experience Manager Assets te produceren. Deze gegevens stellen Admins verder in staat om inzichten af te leiden van belangrijke succesmetingen om de acceptatie van Assets binnen uw onderneming en door klanten te meten.

  ![&#x200B; de vertoning van de PDF voor andere formaten &#x200B;](/help/release-notes/assets/choose_report.png)

* Experience Manager Assets [&#x200B; steunt nu SAS Token &#x200B;](/help/assets/add-assets.md#asset-bulk-ingestor) naast de Sleutel van de Toegang voor authentificatie terwijl het verbinden met de gegevensbron van de Opslag van Azure Blob voor het opnemen van activa die het Bulk hulpmiddel van de Invoer gebruiken.

* Verbeterd beheer van CMYK-afbeeldingen in Asset compute, zodat u slimme uitsnijdtags en slimme tags voor CMYK-afbeeldingen kunt genereren.

### Nieuwe functies in [!DNL Assets] prerelease {#prerelease-features-assets}

* Experience Manager Assets steunt nu [&#x200B; grootschalige opname van activa van het Platform van de Wolk van Google &#x200B;](/help/assets/add-assets.md#asset-bulk-ingestor) gebruikend het Bulk hulpmiddel van de Invoer.

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] {#new-features-available-in-channel}

* **[stappen van het Werkschema om niet-interactieve documenten van PDF en bedrukbare output](/help/forms/aem-forms-workflow-step-reference.md)** te produceren: Automatiseer de verwezenlijking van niet-interactieve documenten van PDF en bedrukbare output voor uw bedrijfsprocessen met AEM stappen van het Werkschema, die uw proces van de documentgeneratie stroomlijnen en tijd besparen.
* **[de Voetnoten van het Gebruik om citaties of extra informatie in Aanpassings Forms](/help/forms/footnotes-richtextsupport.md)** te verstrekken: Gebruik Voetnoten in een adaptieve vorm om de informatie te tonen over hoe te om een vorm te voltooien of te gebruiken. U kunt het ook gebruiken om tussen haakjes informatie, auteursrechttoestemmingen, en andere nuttige informatie te verstrekken.

### Nieuwe functies in [!DNL Forms] prerelease {#prerelease-features-forms}

* **[Gegevens van het Gebruik vangen kerncomponenten om Aangepaste Forms &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) te bouwen**: [&#x200B; de Aangepaste redacteur van Forms van het Gebruik &#x200B;](/help/forms/creating-adaptive-form-core-components.md) om vormen tot stand te brengen die op gestandaardiseerde gegevens worden gebaseerd vangen componenten (de Componenten van de Kern). Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijvingservaring.
* **[Frontend pijpleidingssteun voor het stileren van kerncomponent gebaseerde Aangepaste Forms](/help/forms/using-themes-in-core-components.md)**: Gebruik gemakkelijk aanpasbare op BEM-Gebaseerde thema&#39;s voor op kern-Componenten-Gebaseerde Aangepaste Forms door hen met de pijpleiding van de Plaatsing van het Front op te stellen om de blik en het gevoel van uw vormen te verbeteren.
* **[produceer Document van Verslag voor kerncomponent gebaseerde Adaptieve Forms](/help/forms/generate-document-of-record-core-components.md)**: Creeer een verslag voor kerncomponent gebaseerd Aangepast Vorm op voorlegging voor langetermijnarchivering, in druk of in het documentformaat.

![&#x200B; https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[legt Aangepast Forms aan Microsoft SharePoint en Microsoft OneDrive](/help/forms/configuring-submit-actions.md)** voor: stroomlijnt gegevensvoorlegging met de capaciteit om de Adaptieve gegevens van de Vorm aan zowel Microsoft SharePoint als Microsoft OneDrive direct te verzenden. U kunt zowel schema-gebaseerde als schema-loze gegevens voorleggen. Deze verzendacties vormen een aanvulling op de reeds beschikbare verzendacties.
* **[efficiënte vorm-bouw met sparen een AanpassingsVorm als malplaatjeeigenschap](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: Stroomlijn uw vorm-bouwend proces door een Aangepast Vorm als malplaatje op te slaan en de malplaatjes voor uw volgende AanpassingsVorm opnieuw te gebruiken.
* **[verbind AEM Forms met JDBC-Gesteunde gegevensbestanden](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: Verbind gemakkelijk uw gegevensmodel van AEM Forms met gegevensbestanden die JDBC steunen, die u toestaan om gegevens te lezen en te schrijven foutloos.
* **[integreer met REST Eindpunten die Open API 3.0 gebruiken](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: Verbind AEM Forms as a Cloud Service Modellen van Gegevens van de Vorm met REST eindpunten die Open API specificatieversie 3.0 steunen, toestaand u om gegevens met gemak te verzenden en te ontvangen.
* **[Deel een AanpassingsVorm voor overzicht](/help/forms/create-reviews-forms.md)**: Gebruik het Aanpassings Forms overzichtsmechanisme om één of meerdere recensenten toe te staan om de vorm te herzien.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* [&#x200B; Snelle Milieu&#39;s van de Ontwikkeling &#x200B;](/help/implementing/developing/introduction/rapid-development-environments.md) - RDEs laat ontwikkelaars toe om kwesties snel problemen op te lossen en nieuwe eigenschappen op AEM as a Cloud Service op te stellen.

  Snelle ontwikkelomgevingen zijn een nieuw type cloudomgeving dat is ontworpen als een snelle, consistente en uitbreidbare manier om die code te valideren en die lokaal werkt, en werken ook zoals wordt verwacht in de cloud. Gebruik de Hulpmiddelen van de Lijn van het Bevel, snel &quot;synchroniseer&quot;inhoudspakketten, bundels, inhoudsdossiers, configuratie OSGI, of berichtconfiguratie aan RDE. Zie dit in actie in de video hieronder:

  >[!VIDEO](https://video.tv.adobe.com/v/3413508/?quality=12&learn=on)

  Nadat code met succes in RDE wordt bevestigd, wordt het aangemoedigd om aan een Milieu van de Ontwikkelaar van de Wolk op te stellen om de de kwaliteitskates van Cloud Manager uit te oefenen, alvorens via productiepijpleiding aan stadium en productiemilieu&#39;s te opstellen.

  Elk programma omvat één RDE en naar keuze, kunnen meer worden vergunning gegeven.

  >[!NOTE]
  >
  >RDEs zal geleidelijk in de komende weken worden ingevoerd; u kunt een e-mail naar aemcs-rde-support@adobe.com verzenden om aan de voorzijde van de lijn over te slaan.

* [&#x200B; Uitgebreide steun voor server-kant API toegangstokens &#x200B;](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) - u kunt veelvoudige geloofsbrieven nu produceren, die voor scenario&#39;s nuttig is waar APIs verschillende kenmerken hebben. Het is nu ook mogelijk om geloofsbrieven op een zelfbediening manier in te trekken.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [&#x200B; hier &#x200B;](/help/release-notes/maintenance/latest.md) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [&#x200B; hier &#x200B;](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [&#x200B; hier &#x200B;](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
