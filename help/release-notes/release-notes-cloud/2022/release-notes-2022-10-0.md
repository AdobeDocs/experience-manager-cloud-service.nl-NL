---
title: Nota's van de versie voor 2022.10.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2022.10.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 8fce7c50-f322-4bcf-bd76-390faedfd5b7
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 0%

---

# Opmerkingen bij de release 2022.10.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2022.10.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige maandelijkse release (2022.10.0) is 10 november 2022. De volgende maandelijkse release (2023.1.0) is gepland voor 9 februari 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van oktober 2022 voor een overzicht van de functies die in de release van 2022.10.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3409801/?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}


### Nieuwe functies in [!DNL Sites] {#sites-features}

* Het [ Lusje van Personalization voor de Fragmenten van de Ervaring ](/help/sites-cloud/authoring/fragments/content-fragments.md#personalization-experience-fragment) staat segmentatiespecificatiemogelijkheden aan de Redacteur van het Fragment van de Ervaring en de flexibiliteit toe om genestelde Fragmenten van de Ervaring tot stand te brengen waardoor de kopballen en footers variaties voor veelvoudige segmenten kunnen worden gecreeerd. Vóór de lancering van deze eigenschap, personalisatie die door AEM wordt aangeboden is slechts beschikbaar voor plaatspagina&#39;s, maar niet voor de Fragments van de Ervaring

* De [ Console van het Fragment van de Inhoud ](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) laat nu gebruikers toe om vertaalde inhoudsfragmenten efficiënt te beheren. Er is 1-klik toegang beschikbaar om ook alle taalkopieën weer te geven. Gebruikers kunnen de tabelweergave ook filteren op de landinstelling van hun interesse.

![ de Talen van de Fragmenten van de Inhoud ](/help/release-notes/assets/cfconsole-languages.png)

* Verminder verder de laadtijd van de pagina voor bezoekers door de afbeeldingsgrootten in sjablonen te optimaliseren. Vind meer informatie voor de beeldcomponent bij [ Component van WCM van de Kern ](https://github.com/adobe/aem-core-wcm-components)

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Experience Manager Assets laat u nu documenten in andere gesteunde formaattypes uploaden en [ voorproef hen gebruikend de inbegrepen kijker van het Document Cloud ](/help/assets/manage-pdf-documents.md). Tot de ondersteunde indelingstypen behoren TXT, RTF, DOC, DOCX, PPT, PPTX, XLS en XLSX.

  ![ de vertoning van de PDF voor andere formaten ](/help/release-notes/assets/multi-page-other-formats.png)


### Nieuwe functies in [!DNL Assets] prerelease {#prerelease-features-assets}

* Experience Manager Assets maakt nu gebruik van een verbeterd kunstmatig intelligentiekader voor slimme tags voor afbeeldingen. Deze inhoudsinfo geeft een betere relevantie en nauwkeurigheid van slimme tags die beschikbaar zijn voor alle afbeeldingselementen bij opname. Daarnaast worden oriëntatiegegevens ingevuld in `cq:tags` , zodat u betere zoekresultaten kunt gebruiken met het filter Richting.

  Als u in het deelnemen in Beta geinteresseerd bent, [ vul deze vorm ](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4epXZrTVKKdJkUiHeolccf9UNEwyNEpHVEFaODdBNFZQSlFDREZQOVRRTy4u) tegen 14 november.

* Experience Manager Assets [ steunt nu SAS Token ](/help/assets/add-assets.md#asset-bulk-ingestor) naast de Sleutel van de Toegang voor authentificatie terwijl het verbinden met de gegevensbron van de Opslag van Azure Blob voor het opnemen van activa die het Bulk hulpmiddel van de Invoer gebruiken.

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] prereleasekanaal {#prerelease-features-forms}

* **Aangepaste het malplaatjeredacteur van Forms**: De redacteur van het Malplaatje laat u de basisstructuur en de verschijning van Aangepaste Forms van een organisatie vooraf bepalen. Deze versie brengt volgende verbeteringen aan de malplaatjeredacteur:
   * **[Model van de Gegevens van de Vorm in malplaatjeredacteur](/help/forms/creating-adaptive-form.md#edit-form-model-properties-of-an-adaptive-form-edit-form-model)**: U kunt een Model van de Gegevens van de Vorm aan een Adaptief malplaatje van de Vorm in de malplaatjedacteur associëren. Het vermindert de tijd die nodig is om een adaptief formulier te maken. De optie wordt ook toegevoegd aan de Adaptive Forms-editor, zodat gebruikers het formuliergegevensmodel voor bestaande formulieren kunnen selecteren of wijzigen.
   * **[Document van Verslag in malplaatjeredacteur](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform)**: U kunt Document van de generatie van het Verslag nu standaardiseren voor alle vormen die gebruikend een malplaatje worden gecreeerd. Dit helpt naleving en normalisatie voor org vereisten verbeteren.

* **[lanceer de Adaptieve tovenaar van de Vorm van een Pagina van AEM Sites](/help/forms/embed-adaptive-form-aem-sites.md)**: De pagina van AEM Sites heeft steun voor Aanpassings Forms uitgebreid. U kunt nu een adaptief formulier maken of een bestaand adaptief formulier insluiten terwijl u op de AEM Sites-pagina blijft staan.
* **[de vertoningsgroepering van de Verandering voor controledozen en radiobutton in DoR](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#customize-the-branding-information-in-document-of-record-customize-the-branding-information-in-document-of-record)**: U kunt de gewenste groepering (Horizontaal, Verticaal, Gelijk zoals Aangepast Forms) voor checkbox en radioknoop op het Document van Verslag nu plaatsen. Met deze optie bepaalt u de positie van de opties voor het selectievakje en het keuzerondje in het document of record.

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Auteurs kunnen productlijsten dynamisch verrijken met Experience Fragments (bijvoorbeeld: banner plaatsen tussen productlijsten).
* De component List ondersteunt nu gekoppelde product-/categoriepagina&#39;s om gerelateerde pagina&#39;s dynamisch weer te geven.
* Er is ondersteuning toegevoegd voor Peregrine 12.5-componenten.
* Er is steun toegevoegd voor het laden van de prijs aan de clientzijde in productgummetje en carrousel.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* AEM as a Cloud Service (de Dienst van de Auteur) is nu geïntegreerd met Verenigde Shell om de gebruikerservaring te verbeteren en het met alle andere toepassingen van het Experience Cloud te verenigen. Zie AEM als a [ Cloud Service op Verenigde Shell ](/help/overview/aem-cloud-service-on-unified-shell.md) voor meer details.

* Zoals eerder vermeld in versienota&#39;s, wordt het gebruiken van het scherm van de replicatieagent of replicatie API voor het verspreiden van inhoudspakketten groter dan 10 MB (knopen met eigenschappen, exclusief binaire getallen) nu afgekeurd en afgedwongen. Zie [ Publicatie ](/help/operations/replication.md#manage-publication) of het [ werkschema van de Boom van de Inhoud van Publish ](/help/operations/replication.md#publish-content-tree-workflow) voor voorgestelde benaderingen beheren om deze grote inhoudspakketten te herhalen.

* De configuratie van Dispatcher verwijst nu naar een dossier dat van gemeenschappelijke de vraagparameters van de marketing campagne een lijst maakt. Klanten kunnen ervoor kiezen om de commentaarmarkering van de parameters die voor hen relevant zijn, ongedaan te maken, wat resulteert in betere caching. Zie [ de campagneparameters van de Marketing ](/help/implementing/dispatcher/caching.md#marketing-parameters) voor meer details.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.
