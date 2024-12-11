---
title: Notable veranderingen in  [!DNL Adobe Experience Manager Assets]  als a  [!DNL Cloud Service]
description: Notable veranderingen in  [!DNL Adobe Experience Manager Assets]  in  [!DNL Experience Manager]  als a  [!DNL Cloud Service]  in vergelijking met  [!DNL Adobe Experience Manager]  6.5.
feature: Release Information
role: User, Leader, Architect, Admin
exl-id: 93e7dbcd-016e-4ef2-a1cd-c554efb5ad34
source-git-commit: 979c4accca8b271ba2ff0ba176985c94b6d469c7
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 0%

---

# Notable changes to [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#notable-changes}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

[!DNL Adobe Experience Manager] als [!DNL Cloud Service] brengt vele nieuwe eigenschappen en mogelijkheden om uw projecten van de Experience Manager te beheren. Er zijn veel verschillen tussen [!DNL Experience Manager Assets] on-premise of hosted als Adobe Managed Service in vergelijking met [!DNL Experience Manager] as a [!DNL Cloud Service] . In dit artikel worden de belangrijke verschillen voor [!DNL Assets] -mogelijkheden belicht.

De belangrijkste verschillen ten opzichte van [!DNL Experience Manager] 6.5 zijn op de volgende gebieden:

* [ Inname van activa, upload, en verwerking ](#asset-ingestion).
* [ de microdiensten van Activa voor wolk-inheemse verwerking ](#asset-microservices).
* [ Verwijdering van Klassieke UI ](#classic-ui).

## Inname, verwerking en distributie van bedrijfsmiddelen {#asset-ingestion-distribution}

Het uploaden van middelen is geoptimaliseerd voor efficiëntie door betere schaling van inname, snellere uploads, snellere verwerking met behulp van microservices en bulkopname mogelijk te maken. Productmogelijkheden (webgebruikersinterfaces, desktopclients) worden bijgewerkt. Deze dingen kunnen ook van invloed zijn op bepaalde bestaande aanpassingen.

* [!DNL Experience Manager] gebruikt het directe binaire toegangsbeginsel om activa te uploaden en te downloaden en gebruikt de middelen microservices om activa te verwerken. Zie een [ overzicht van microdiensten ](/help/assets/asset-microservices-overview.md).
   * Het middel uploadt [ met directe binaire toegang ](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Voor technische details, zie [ direct binair upload protocol en APIs ](/help/assets/developer-reference-material-apis.md#upload-binary).
   * Voor een vergelijking van de beschikbare API methodes voor basisCRUD verrichtingen, zie [ APIs en activaverrichtingen ](/help/assets/developer-reference-material-apis.md#use-cases-and-apis).
* De standaardworkflow **[!UICONTROL DAM Asset Update]** in eerdere versies van [!DNL Experience Manager] is niet meer beschikbaar. In plaats daarvan, verstrekken de activa microservices een scalable, gemakkelijk beschikbare dienst die het grootste deel van de standaardactiva verwerkt (vertoningen, meta-gegevensextractie, en tekst het indexeren) behandelt.
   * Zie [ activa microservices ](/help/assets/asset-microservices-configure-and-use.md) vormen en gebruiken
   * Om aangepaste werkschemastappen in de verwerking te hebben, [ post-verwerkende werkschema&#39;s ](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) kunnen worden gebruikt.

* De websitecomponenten die een binair bestand leveren zonder transformatie kunnen rechtstreeks downloaden. Het Sling GET servlet wordt bijgewerkt om deze functionaliteit door gebrek toe te laten. De websitecomponenten die een binair getal met een transformatie leveren (bijvoorbeeld de grootte ervan wijzigen via een servlet) kunnen ongewijzigd blijven werken.

De standaardvertoningen die met asset microservices worden gegenereerd, worden achterwaarts compatibel opgeslagen in de knooppunten van de opslagplaats van middelen met dezelfde naamgevingsconventies.

## Middelen-microservices ontwikkelen en testen {#asset-microservices}

Asset microservices bieden een schaalbare en veerkrachtige verwerking van middelen met behulp van cloudservices. Adobe beheert de cloudservices voor een optimale afhandeling van verschillende typen bedrijfsmiddelen en verwerkingsopties. Asset microservices helpen te voorkomen dat er van derden weergavegereedschappen en -methoden nodig zijn (zoals [!DNL ImageMagick] ) en vereenvoudigen configuraties, terwijl ze ook functionaliteit bieden die buiten de box valt voor algemene bestandstypen. U kunt a [ brede waaier van dossiertypes ](/help/assets/file-format-support.md) nu verwerken die meer formaten uit-van-de-doos behandelen dan wat met vorige versies van Experience Manager mogelijk is. Zo is het nu mogelijk miniatuurextractie van PSD- en PSB-indelingen uit te voeren waarvoor eerder oplossingen van derden waren vereist, zoals [!DNL ImageMagick] . U kunt de complexe configuraties van [!DNL ImageMagick] niet gebruiken voor de [!UICONTROL Processing Profiles] -configuratie. Gebruik [!DNL Dynamic Media] voor geavanceerde transcodering MPEG van video&#39;s en gebruiksverwerkingsprofielen voor [ basistranscodering van MP4 video&#39;s ](/help/assets/manage-video-assets.md#transcode-video).

Asset microservices is een service in de cloud die automatisch wordt ingericht en via [!DNL Experience Manager] wordt verzonden in programma&#39;s en omgevingen van klanten die in Cloud Manager worden beheerd. Om [!DNL Experience Manager] uit te breiden of aan te passen, kunnen ontwikkelaars bestaande inhoud of activa met vertoningen gebruiken die in een wolkenmilieu worden geproduceerd. Hierdoor kunnen ze hun code testen en valideren door elementen te gebruiken, weer te geven of te downloaden.

Om een bevestiging van begin tot eind van de code en het proces met inbegrip van activaopname en verwerking te doen, stel de codeveranderingen in een wolk-dev milieu op gebruikend [ de pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) en test met volledige uitvoering van activa microservices verwerking.

## pariteit van functies met [!DNL Experience Manager] 6.5 {#cloud-service-feature-status}

[!DNL Experience Manager] als een [!DNL Cloud Service] bevat veel nieuwe functies en betere manieren om bestaande functies te laten werken. Wanneer u echter van [!DNL Experience Manager] 6.5 naar [!DNL Experience Manager] as a [!DNL Cloud Service] gaat, kunnen sommige functies anders werken, niet beschikbaar of gedeeltelijk beschikbaar zijn. Hieronder volgt een lijst met dergelijke functies. Bovendien zie [ afgekeurde en verwijderde eigenschappen ](/help/release-notes/deprecated-removed-features.md).

| Functionaliteit of gebruikscase | Status in [!DNL Experience Manager] als een [!DNL Cloud Service] | Opmerkingen |
|-----|-----|-----|
| [ Dubbele activaopsporing ](/help/assets/detect-duplicate-assets.md) | Dit werkt anders | Zie [ hoe het in  [!DNL Experience Manager]  6.5 ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/managing/duplicate-detection) werkte. |
| [ voor slechts (FPO) vertoningen van de Plaatsing ](/help/assets/configure-fpo-renditions.md) | Dit werkt anders | Bij de verwerking van profielen worden de asset-microservices gebruikt om FPO-uitvoeringen te genereren. In Experience Manager 6.5 was een oplossing van derden, zoals [!DNL ImageMagick] , beschikbaar om de uitvoeringen te genereren. |
| Metagegevens terugschrijven | Dit werkt anders | Standaard uitgeschakeld. Schakel indien nodig de bijbehorende workflow voor het starten van de workflow in. Asset microservices handelt de callback af. |
| Verwerking van geüploade elementen met gebruik van Package Manager | Dit vereist handmatige interventie | Handmatig opnieuw verwerken met de handeling **[!UICONTROL Reprocess Asset]** . |
| MIME-typedetectie | Niet ondersteund. | Als u een digitaal element uploadt zonder extensie of met een onjuiste extensie, wordt het mogelijk niet naar wens verwerkt. De gebruikers kunnen de binaire dossiers zonder een uitbreiding in DAM nog opslaan. Zie [ MIME typeopsporing in  [!DNL Experience Manager]  6.5 ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/administer/detect-asset-mime-type-with-tika). |
| Subasset genereren voor samengestelde activa | Niet ondersteund. | Het is mogelijk dat niet wordt voldaan aan afhankelijke gebruiksgevallen, zoals annotaties. Zie [ subasset verwezenlijking in  [!DNL Experience Manager]  6.5 ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/managing/managing-linked-subassets#generate-subassets). De voorproef van PDF van sommige dossiertypes is beschikbaar beginnend [ versie 2021.7.0 ](/help/release-notes/release-notes-cloud/release-notes-current.md). |
| Afbeeldingen bewerken | Niet ondersteund | Het bewerken van elementen wordt niet ondersteund in Experience Manager as a Cloud Service. Zie [ hoe het in Experience Manager 6.5 ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/managing/manage-assets#editing-images) werkte. |
| Homepage | Niet ondersteund | Zie {de ervaring van de Pagina van 0} Huis in  [!DNL Experience Manager]  6.5 ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/using/assets-home-page)[[!DNL Assets]  |
| Elementen extraheren uit ZIP-archief | Niet ondersteund | Zie {de extractie van 0} ZIP in  [!DNL Experience Manager]  6.5 ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/managing/manage-assets#extractzip).[ |
| Assets-ratings | Niet ondersteund | De beoordelingswidget in de schema-editor voor metagegevens wordt niet ondersteund. |
| Inhoudsverwijderingsfilter | Niet ondersteund | Een veelgebruikte manier van werken in `ContentDispositionFilter` is om beheerders [!DNL Experience Manager] zodanig te configureren dat deze bestanden HTML-bestanden kunnen leveren en PDF-bestanden inline kunnen openen in plaats van ze te downloaden. Bij de publicatie-instanties kunt u de indeling beheren met behulp van de Dispatcher-configuratie. In de ontwerpinstanties wordt door Adobe geen wijziging in de header voor het verplaatsen van inhoud aanbevolen. Zie {het filter van de Verplaatsing van 0} Inhoud in  [!DNL Experience Manager]  6.5 ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/content-disposition-filter).[ |
| Fotosjabloon voor product | Niet ondersteund | Zie [ malplaatje van de productfotoshoot in  [!DNL Experience Manager]  6.5 ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/sites/authoring/projects/managing-product-information). |
| Slimme omzetting | Niet ondersteund | Slimme vertaling wordt niet ondersteund in [!DNL Experience Manager] als een [!DNL Cloud Service] . |
| WebDAV | Niet ondersteund | Voor alternatieven, zie [[!DNL Creative Cloud]  integratie ](/help/assets/aem-cc-integration-best-practices.md) of [ het verwijzingsmateriaal van de Ontwikkelaar ](/help/assets/developer-reference-material-apis.md). |
| Klassieke interface | Niet ondersteund | Alleen een gebruikersinterface met aanraakbediening is beschikbaar. |

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Publish Assets naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>De volgende bronnen zijn beschikbaar voor [!DNL Experience Manager] als [!DNL Cloud Service] :
>
>* [ Lijst van afgekeurde en verwijderde eigenschappen ](/help/release-notes/deprecated-removed-features.md)
>* [ Een inleiding ](/help/overview/introduction.md)
>* [Nieuwe en aangepaste functies](/help/overview/what-is-new-and-different.md)
>* [ de architectuur ](/help/overview/architecture.md)
>* [ Notable veranderingen ](/help/release-notes/aem-cloud-changes.md)
>* [ Notable veranderingen  [!DNL Sites]](/help/sites-cloud/sites-cloud-changes.md)
>* [ Videozelfstudies ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/overview)
