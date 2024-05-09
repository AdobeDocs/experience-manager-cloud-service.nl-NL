---
title: Opvallende wijzigingen in [!DNL Adobe Experience Manager Assets] als [!DNL Cloud Service]
description: Opvallende wijzigingen in [!DNL Adobe Experience Manager Assets] in [!DNL Experience Manager] als [!DNL Cloud Service] in vergelijking met [!DNL Adobe Experience Manager] 6.5
feature: Release Information
role: User,Leader,Architect,Admin
exl-id: 93e7dbcd-016e-4ef2-a1cd-c554efb5ad34
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 0%

---

# Opvallende wijzigingen in [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#notable-changes}

[!DNL Adobe Experience Manager] als [!DNL Cloud Service] brengt vele nieuwe eigenschappen en mogelijkheden om uw projecten van de Experience Manager te beheren. Er zijn veel verschillen tussen [!DNL Experience Manager Assets] on-premisse of gehost als Adobe Managed Service in vergelijking met [!DNL Experience Manager] als [!DNL Cloud Service]. In dit artikel worden de belangrijke verschillen voor [!DNL Assets] mogelijkheden.

De belangrijkste verschillen ten opzichte van [!DNL Experience Manager] 6.5 bevinden zich op de volgende gebieden:

* [Inname, uploaden en verwerken van bedrijfsmiddelen](#asset-ingestion).
* [Asset microservices voor cloud-native verwerking](#asset-microservices).
* [Verwijderen van klassieke gebruikersinterface](#classic-ui).

## Inname, verwerking en distributie van bedrijfsmiddelen {#asset-ingestion-distribution}

Het uploaden van middelen is geoptimaliseerd voor efficiëntie door betere schaling van inname, snellere uploads, snellere verwerking met behulp van microservices en bulkopname mogelijk te maken. Productmogelijkheden (webgebruikersinterfaces, desktopclients) worden bijgewerkt. Dit kan ook van invloed zijn op sommige bestaande aanpassingen.

* [!DNL Experience Manager] gebruikt het directe binaire toegangsbeginsel om activa te uploaden en te downloaden en activa microservices te gebruiken om activa te verwerken. Zie [overzicht van microdiensten](/help/assets/asset-microservices-overview.md).
   * Elementen uploaden [met directe binaire toegang](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Voor technische details, zie [direct binair upload protocol en APIs](/help/assets/developer-reference-material-apis.md#upload-binary).
   * Zie voor een vergelijking van de beschikbare API-methoden voor basis-CRUD-bewerkingen [API&#39;s en middelenbewerkingen](/help/assets/developer-reference-material-apis.md#use-cases-and-apis).
* De standaardworkflow **[!UICONTROL DAM Asset Update]** in eerdere versies van [!DNL Experience Manager] is niet meer beschikbaar. In plaats daarvan, verstrekken de activa microservices een scalable, gemakkelijk beschikbare dienst die het grootste deel van de standaardactiva verwerkt (vertoningen, meta-gegevensextractie, en tekst het indexeren) behandelt.
   * Zie [assetmicroservices configureren en gebruiken](/help/assets/asset-microservices-configure-and-use.md)
   * Om aangepaste werkstroomstappen in de verwerking te hebben, [nabewerkingsworkflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) kan worden gebruikt.

* De websitecomponenten die een binair bestand leveren zonder transformatie kunnen rechtstreeks downloaden. De Sling GET servlet wordt bijgewerkt zodat ontwikkelaars dit standaard kunnen doen. De websitecomponenten die een binair getal met een transformatie leveren (bijvoorbeeld de grootte ervan wijzigen via een servlet) kunnen ongewijzigd blijven werken.

De standaardvertoningen die met asset microservices worden gegenereerd, worden achterwaarts compatibel opgeslagen in de knooppunten van de opslagplaats van middelen met dezelfde naamgevingsconventies.

## Middelen-microservices ontwikkelen en testen {#asset-microservices}

Asset microservices bieden een schaalbare en veerkrachtige verwerking van middelen met behulp van cloudservices. Adobe beheert de cloudservices voor een optimale afhandeling van verschillende typen bedrijfsmiddelen en verwerkingsopties. Asset microservices helpen te voorkomen dat er weergavehulpmiddelen en -methoden van derden nodig zijn (zoals [!DNL ImageMagick]) en vereenvoudigt configuraties, terwijl functionaliteit in de box voor algemene bestandstypen wordt geboden. U kunt nu een [brede waaier van dossiertypes](/help/assets/file-format-support.md) het bedekken van meer formaten uit-van-de-doos dan wat met vorige versies van Experience Manager mogelijk is. Zo is het nu mogelijk dat miniatuurextractie van PSD- en PSB-indelingen plaatsvindt waarbij eerder vereiste oplossingen van derden, zoals [!DNL ImageMagick]. U kunt de complexe configuraties van [!DNL ImageMagick] voor de [!UICONTROL Processing Profiles] configuratie. Gebruiken [!DNL Dynamic Media] voor geavanceerde MPEG-transcodering van video&#39;s en gebruik verwerkingsprofielen voor [basistranscodering van MP4-video&#39;s](/help/assets/manage-video-assets.md#transcode-video).

Asset microservices is een service in de cloud die automatisch wordt ingericht en bekabeld naar [!DNL Experience Manager] in programma&#39;s en omgevingen van klanten die worden beheerd in Cloud Manager. Om uit te breiden of aan te passen [!DNL Experience Manager]kunnen de ontwikkelaars de bestaande inhoud of elementen gebruiken met uitvoeringen die zijn gegenereerd in een cloudomgeving, om hun code te testen en te valideren met behulp van, het weergeven en downloaden van elementen.

Als u een end-to-end validatie van de code en het proces wilt uitvoeren, inclusief het opnemen en verwerken van bedrijfsmiddelen, implementeert u de codewijzigingen in een cloud-dev-omgeving met [de pijpleiding](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) en test met volledige uitvoering van de verwerking van asset microservices.

## pariteit van functies met [!DNL Experience Manager] 6,5 {#cloud-service-feature-status}

[!DNL Experience Manager] als [!DNL Cloud Service] introduceert vele nieuwe eigenschappen en krachtigere manieren om bestaande eigenschappen te werken. Wanneer u echter van [!DNL Experience Manager] 6,5 tot [!DNL Experience Manager] als [!DNL Cloud Service]Sommige functies werken mogelijk anders, zijn niet beschikbaar of zijn gedeeltelijk beschikbaar. Hieronder volgt een lijst met dergelijke functies. Zie ook de [vervangen en verwijderde functies](/help/release-notes/deprecated-removed-features.md).

| Functionaliteit of gebruikscase | Status in [!DNL Experience Manager] als [!DNL Cloud Service] | Opmerkingen |
|-----|-----|-----|
| [Elementdetectie dupliceren](/help/assets/detect-duplicate-assets.md) | Werkt anders | Zie [hoe het werkte [!DNL Experience Manager] 6,5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/duplicate-detection.html). |
| [Alleen voor FPO-uitvoeringen (Placement Only)](/help/assets/configure-fpo-renditions.md) | Werkt anders | Bij de verwerking van profielen worden de asset-microservices gebruikt om FPO-uitvoeringen te genereren. In Experience Manager 6.5, een derdeoplossing zoals [!DNL ImageMagick] was beschikbaar om de uitvoeringen te genereren. |
| Metagegevens terugschrijven | Werkt anders | Standaard uitgeschakeld. Schakel indien nodig de bijbehorende workflow voor het starten van de workflow in. Terugkoppeling wordt afgehandeld door middel van asset microservices. |
| Verwerking van geüploade elementen met gebruik van Package Manager | Handmatige interventie vereist | Handmatig opnieuw verwerken met de opdracht **[!UICONTROL Reprocess Asset]** handeling. |
| MIME-typedetectie | Niet ondersteund. | Als u een digitaal element uploadt zonder extensie of met een onjuiste extensie, wordt het mogelijk niet naar wens verwerkt. De gebruikers kunnen de binaire dossiers zonder een uitbreiding in DAM nog opslaan. Zie [MIME-typedetectie in [!DNL Experience Manager] 6,5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/detect-asset-mime-type-with-tika.html). |
| Subasset genereren voor samengestelde activa | Niet ondersteund. | Het is mogelijk dat niet wordt voldaan aan afhankelijke gebruiksgevallen, zoals annotaties. Zie [subelement maken in [!DNL Experience Manager] 6,5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/managing-linked-subassets.html#generate-subassets). Voorvertoning van PDF van bepaalde bestandstypen is beschikbaar vanaf [release 2021.7.0](/help/release-notes/release-notes-cloud/release-notes-current.md). |
| Afbeeldingen bewerken | Niet ondersteund | Het bewerken van elementen wordt niet ondersteund in as a Cloud Service Experience Manager. Zie [hoe het werkte in Experience Manager 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#editing-images). |
| Homepage | Niet ondersteund | Zie [[!DNL Assets] Introductiepagina [!DNL Experience Manager] 6,5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-home-page.html) |
| Elementen extraheren uit ZIP-archief | Niet ondersteund | Zie [ZIP-extractie in [!DNL Experience Manager] 6,5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#extractzip). |
| Waarderingen activa | Niet ondersteund | De beoordelingswidget in de schema-editor voor metagegevens wordt niet ondersteund. |
| Inhoudsverwijderingsfilter | Niet ondersteund | Een veelgebruikte optie voor `ContentDispositionFilter` is om beheerders te laten configureren [!DNL Experience Manager] om HTML-bestanden te bedienen en PDF-bestanden inline te openen in plaats van deze te downloaden. In de publicatie-instanties kunt u de indeling beheren met de Dispatcher-configuratie. In de instanties Auteur wordt in de Adobe geen wijziging in de koptekst voor het verplaatsen van inhoud aanbevolen. Zie [Filter Inhoud verplaatsen in [!DNL Experience Manager] 6,5](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/content-disposition-filter.html). |
| Fotosjabloon voor product | Niet ondersteund | Zie [productfotosjabloon in [!DNL Experience Manager] 6,5](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/projects/managing-product-information.html). |
| Slimme omzetting | Niet ondersteund | [Slimme vertaling](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/translation/smart-translation-search-feature-video-use.html) wordt niet ondersteund in [!DNL Experience Manager] als [!DNL Cloud Service]. |
| WebDAV | Niet ondersteund | Voor alternatieven, zie [[!DNL Creative Cloud] integratie](/help/assets/aem-cc-integration-best-practices.md) of [Referentiemateriaal voor ontwikkelaars](/help/assets/developer-reference-material-apis.md). |
| Klassieke interface | Niet ondersteund | Alleen een gebruikersinterface met aanraakbediening is beschikbaar. |

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Middelen publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>De volgende bronnen zijn beschikbaar voor [!DNL Experience Manager] als [!DNL Cloud Service]:
>
>* [Lijst met vervangen en verwijderde functies](/help/release-notes/deprecated-removed-features.md)
>* [Een inleiding](/help/overview/introduction.md)
>* [Nieuwe en aangepaste functies](/help/overview/what-is-new-and-different.md)
>* [De architectuur](/help/overview/architecture.md)
>* [Opvallende wijzigingen](/help/release-notes/aem-cloud-changes.md)
>* [Opvallende wijzigingen [!DNL Sites]](/help/sites-cloud/sites-cloud-changes.md)
>* [Videozelfstudies](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html)
