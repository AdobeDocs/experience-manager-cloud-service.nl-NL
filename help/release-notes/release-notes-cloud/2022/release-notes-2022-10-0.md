---
title: Opmerkingen bij de release 2022.10.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2022.10.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 8fce7c50-f322-4bcf-bd76-390faedfd5b7
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 0%

---

# Opmerkingen bij de release 202.10.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de release met functies voor de versie 2022.10.0 van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige maandelijkse release (2022.10.0) is 10 november 2022. De volgende maandelijkse release (2023.1.0) is gepland voor 9 februari 2023.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van oktober 2022 voor een overzicht van de functies die in de release van 2022.10.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3409801/?quality=12)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}


### Nieuwe functies in [!DNL Sites] {#sites-features}

* De [Tab voor aanpassen aan ervaringsfragmenten](/help/sites-cloud/authoring/fragments/content-fragments.md#personalization-experience-fragment) staat segmentatiespecificatiemogelijkheden aan de Redacteur van het Fragment van de Ervaring en de flexibiliteit toe om genestelde Fragmenten van de Ervaring tot stand te brengen waardoor de veranderingen van kopballen en footers voor veelvoudige segmenten kunnen worden gecreeerd. Vóór de lancering van deze eigenschap, personalisatie die door AEM wordt aangeboden is slechts beschikbaar voor plaatspagina&#39;s, maar niet voor de Fragments van de Ervaring

* De [Console voor inhoudsfragment](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) gebruikers kunnen nu op efficiënte wijze vertaalde inhoudsfragmenten beheren. Er is 1-klik toegang beschikbaar om ook alle taalkopieën weer te geven. Gebruikers kunnen de tabelweergave ook filteren op de landinstelling van hun interesse.

![Talen voor inhoudsfragmenten](/help/release-notes/assets/cfconsole-languages.png)

* Verminder verder de laadtijd van de pagina voor bezoekers door de afbeeldingsgrootten in sjablonen te optimaliseren. Meer informatie over de afbeeldingscomponent vindt u op [Core WCM-component](https://github.com/adobe/aem-core-wcm-components)

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Met Experience Manager Assets kunt u nu documenten uploaden in andere ondersteunde indelingen en[een voorvertoning ervan weergeven met de meegeleverde viewer voor Documenten Cloud](/help/assets/manage-pdf-documents.md). Tot de ondersteunde indelingstypen behoren TXT, RTF, DOC, DOCX, PPT, PPTX, XLS en XLSX.

  ![PDF-uitvoering voor andere indelingen](/help/release-notes/assets/multi-page-other-formats.png)


### Nieuwe functies in [!DNL Assets] prerelease {#prerelease-features-assets}

* Experience Manager Assets maakt nu gebruik van een verbeterd kunstmatig intelligentiekader voor slimme tags voor afbeeldingen. Deze inhoudsinfo geeft een betere relevantie en nauwkeurigheid van slimme tags die beschikbaar zijn voor alle afbeeldingselementen bij opname. Bovendien wordt de richtingsinformatie ingevuld in `cq:tags`, waarmee u betere zoekresultaten kunt bereiken met het filter Richting.

  Als u geïnteresseerd bent in deelname aan de bètaversie, [Dit formulier invullen](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4epXZrTVKKdJkUiHeolccf9UNEwyNEpHVEFaODdBNFZQSlFDREZQOVRRTy4u) uiterlijk op 14 november.

* Experience Manager Assets nu [ondersteunt SAS Token](/help/assets/add-assets.md#asset-bulk-ingestor) naast de toegangstoets voor verificatie bij de verbinding met de Azure Blob Storage-gegevensbron voor het opnemen van elementen met het Bulk Import-gereedschap.

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#prerelease-features-forms}

* **Adaptieve Forms-sjablooneditor**: Met Sjablooneditor kunt u de basisstructuur en het uiterlijk van Adaptieve Forms van een organisatie vooraf definiëren. Deze versie brengt volgende verbeteringen aan de malplaatjeredacteur:
   * **[Formuliergegevensmodel in sjablooneditor](/help/forms/creating-adaptive-form.md#edit-form-model-properties-of-an-adaptive-form-edit-form-model)**: U kunt een formuliergegevensmodelschema koppelen aan een adaptieve formuliersjabloon in de sjablooneditor. Het vermindert de tijd die nodig is om een adaptief formulier te maken. De optie wordt ook toegevoegd aan de Adaptive Forms-editor, zodat gebruikers het formuliergegevensmodel voor bestaande formulieren kunnen selecteren of wijzigen.
   * **[Document met record in sjablooneditor](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform)**: U kunt het genereren van documenten nu standaardiseren voor alle formulieren die met een sjabloon zijn gemaakt. Dit helpt naleving en normalisatie voor org vereisten verbeteren.

* **[De wizard Adaptief formulier starten vanaf een AEM Sites-pagina](/help/forms/embed-adaptive-form-aem-sites.md)**: AEM Sites-pagina biedt uitgebreide ondersteuning voor Adaptive Forms. U kunt nu een adaptief formulier maken of een bestaand adaptief formulier insluiten terwijl u op de AEM Sites-pagina blijft staan.
* **[De vertoningsgroepering van de verandering voor controledozen en radioknoop in DoR](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#customize-the-branding-information-in-document-of-record-customize-the-branding-information-in-document-of-record)**: U kunt nu de gewenste uitlijning (Horizontaal, Verticaal, Hetzelfde als Adaptief Forms) instellen voor het selectievakje en het keuzerondje in het Document of Record. Met deze optie bepaalt u de positie van de opties voor het selectievakje en het keuzerondje in het document of record.

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Auteurs kunnen productlijsten dynamisch verrijken met Experience Fragments (bijvoorbeeld: banner plaatsen tussen productlijsten).
* De component List ondersteunt nu gekoppelde product-/categoriepagina&#39;s om gerelateerde pagina&#39;s dynamisch weer te geven.
* Er is ondersteuning toegevoegd voor Peregrine 12.5-componenten.
* Er is steun toegevoegd voor het laden van de prijs aan de clientzijde in productgummetje en carrousel.

## [!DNL Experience Manager as a Cloud Service] Stichting {#foundation}

### Nieuwe functies {#what-is-new-foundation}

* AEM as a Cloud Service (de Dienst van de Auteur) is nu geïntegreerd met Verenigde Shell om de gebruikerservaring te verbeteren en het met alle andere toepassingen van het Experience Cloud te verenigen. Zie AEM als een [Cloud Service op Unified Shell](/help/overview/aem-cloud-service-on-unified-shell.md) voor meer informatie .

* Zoals eerder vermeld in versienota&#39;s, wordt het gebruiken van het scherm van de replicatieagent of replicatie API voor het verspreiden van inhoudspakketten groter dan 10 MB (knopen met eigenschappen, exclusief binaire getallen) nu afgekeurd en afgedwongen. Zie [Publicatie beheren](/help/operations/replication.md#manage-publication) of de [Workflow Inhoudsstructuur publiceren](/help/operations/replication.md#publish-content-tree-workflow) voor gesuggereerde benaderingen voor het repliceren van deze grote inhoudspakketten.

* De configuratie van de afzender verwijst nu naar een dossier dat van gemeenschappelijke de vraagparameters van de marketing campagne een lijst maakt. Klanten kunnen ervoor kiezen om de commentaarmarkering van de parameters die voor hen relevant zijn, ongedaan te maken, wat resulteert in betere caching. Zie [Parameters van de marketingcampagne](/help/implementing/dispatcher/caching.md#marketing-parameters) voor meer informatie .

## Cloud Manager {#cloud-manager}

U vindt een volledige lijst met maandreleases van Cloud Manager [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migratiehulpmiddelen {#migration-tools}

U vindt een volledige lijst met de releases van de migratiehulpmiddelen [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
