---
title: Nota's van de versie voor 2023.2.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2023.2.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 671056e6-84cc-4c2c-bca3-fde68d5cc835
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---

# Opmerkingen bij de release 2023.2.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2023.2.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2021, 2022, enzovoort.
>
>Heb een blik bij de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2023.2.0) is 12 april 2023. De volgende release met functies (2023.4.0) is gepland voor 7 juni 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van februari 2023 voor een overzicht van de functies die zijn toegevoegd in de release van 2023.2.0:

>[!VIDEO](https://video.tv.adobe.com/v/3416885/?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Experience Manager Sites] prelease {#prerelease-sites}

* Exporteer inhoudsfragmenten van AEM als cloudservice naar het doel van de Adobe dat JSON biedt.
* Ondersteuning voor paginering en sortering van GraphQL en verbeteringen in de interne cache helpen nu de prestaties van losgekoppelde clienttoepassingen te verbeteren wanneer u grote inhoudssets ophaalt van AEM met behulp van complexe GraphQL-query&#39;s en -filters.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Ondersteuning voor het nieuwe protocol (DASH - Dynamic Adaptive Streaming via HTTP) dat is gestart voor Adaptive streaming in Dynamic Media-video (met CMAF ingeschakeld):
   * Adaptief streamen (DASH/HLS) zorgt voor een betere kijkervaring voor video&#39;s
   * DASH is het internationale standaardprotocol voor adaptieve videostreaming en wordt op grote schaal toegepast in de branche
   * Beschikbaar in NA, beschikbaar via een ondersteuningsticket, binnenkort verkrijgbaar in APAC, EMEA

* Extra ondersteuning voor WebP-afbeeldingen om automatisch metagegevens te extraheren, miniaturen en aangepaste uitvoeringen te genereren. De mogelijkheden Slimme tags en Slim uitsnijden worden nu ook ondersteund voor deze bestanden.

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] {#new-features-available-in-channel}

* **[Gegevens van het Gebruik vangen kerncomponenten om Aangepaste Forms ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) te bouwen**: [ de Aangepaste redacteur van Forms van het Gebruik ](/help/forms/creating-adaptive-form-core-components.md) om vormen tot stand te brengen die op gestandaardiseerde gegevens worden gebaseerd vangen componenten (de Componenten van de Kern). Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijvingservaring.

* **[Frontend pijpleidingssteun voor het stileren van kerncomponent gebaseerde Aangepaste Forms](/help/forms/using-themes-in-core-components.md)**: Gebruik gestandaardiseerde op BEM-Gebaseerde thema&#39;s voor op kern-componenten-Gebaseerde Aangepaste Forms door hen met de pijpleiding van de Plaatsing van de Voorkant op te stellen om de blik en het gevoel van uw vormen te verbeteren en zich aan de merkgoedgekeurde ontwerprichtlijnen van uw organisatie te richten.

* **[produceer Document van Verslag voor kerncomponent gebaseerde Adaptieve Forms](/help/forms/generate-document-of-record-core-components.md)**: Creeer een document van verslag dat voorgelegde gegevens voor Adaptief Forms bevat die gebruikend kerncomponenten voor archivering of verwijzing aan eind - gebruikers, in druk of in het documentformaat worden gebouwd.

![ https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[efficiënte vorm-bouw met sparen een Aangepast Vorm als malplaatjeeigenschap](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: Versnelde en normaliseer vormontwikkeling door bestaande merk goedgekeurde vormen als vormmalplaatjes voor snel hergebruik op te slaan.

* **[verbind AEM Forms met JDBC-Gesteunde gegevensbestanden](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: verbind rechtstreeks met ondernemingsgegevensbestanden van AEM de dienst van de Wolk gebruikend protocol JDBC, zonder de behoefte om hen over REST API bloot te stellen.

* **[integreert met de Eindpunten van REST die Open API 3.0 gebruiken](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: Naadloos integreren in systemen van verslag die Open API 3.0 steunen om gegevens op te slaan en te halen gebruikend de modellen van vormgegevens.

* **[Deel een AanpassingsVorm voor overzicht](/help/forms/create-reviews-forms.md)**: Gebruik het Aanpassings Forms overzichtsmechanisme om één of meerdere recensenten toe te staan om de vorm te herzien.


### Functies in [!DNL Forms] prerelease {#prerelease-features-forms}

* **[legt Aangepaste Forms aan Microsoft SharePoint en Microsoft OneDrive voor](/help/forms/configuring-submit-actions.md)**: Verbeter bedrijfsgebruikersbehendigheid om nieuwe vormen snel te lanceren en voorgelegde gegevens in alledaagse hulpmiddelen op te slaan zij zoals plaats Microsoft SharePoint of omslag OneDrive gebruiken.

![ legt Aangepaste Forms aan Microsoft SharePoint en Microsoft OneDrive voor ](/help/forms/assets/onedrive-and-sharepoint.jpg)


## Forms-programma voor vroege adoptie zonder adapter {#forms-early-adopter}

Gebruik Headless Adaptive Forms om uw ontwikkelaars in staat te stellen interactieve formulieren te maken, te publiceren en te beheren die via API&#39;s kunnen worden geopend en gebruikt in plaats van via een traditionele grafische gebruikersinterface. Met behulp van hoofdloze adaptieve formulieren kunt u:

* multikanaalformulieren van hoge kwaliteit maken in de programmeertaal van uw keuze
* U kunt zelf formulieren integreren in uw bureaublad en mobiele apps, websites en chattoepassingen
* gebruik uw eigen UI-componenten opnieuw met formuliertoepassingen
* de kracht van Adobe Experience Manager Forms gebruiken

U kunt vanaf uw officiële e-mailadres een e-mail sturen naar aem-forms-headless@adobe.com om deel te nemen aan het programma voor vroegtijdige adoptie.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
