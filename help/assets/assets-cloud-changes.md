---
title: Opvallende wijzigingen in [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service]
description: Noteerbare wijzigingen in [!DNL Adobe Experience Manager Assets] in [!DNL Experience Manager] as a [!DNL Cloud Service] vergeleken met [!DNL Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 201abba4352362b1bb97b6a25bd84f95e8ed8483
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 0%

---


# Opvallende wijzigingen in [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#notable-changes}

[!DNL Adobe Experience Manager] als  [!DNL Cloud Service] brengt u vele nieuwe functies en mogelijkheden om uw projecten van de Experience Manager te beheren. Er zijn veel verschillen tussen [!DNL Experience Manager Assets] on-premise of gehost als Adobe Managed Service in vergelijking met [!DNL Experience Manager] als [!DNL Cloud Service]. In dit artikel worden de belangrijke verschillen voor [!DNL Assets] mogelijkheden belicht.

De belangrijkste verschillen ten opzichte van [Experience Manager] 6.5 zijn op de volgende gebieden:

* [Het opnemen, uploaden en verwerken](#asset-ingestion) van bedrijfsmiddelen.
* [Asset microservices voor cloudnative verwerking](#asset-microservices).
* [Verwijderen van klassieke gebruikersinterface](#classic-ui).

## Inname en verwerking van bedrijfsmiddelen {#asset-ingestion}

Het uploaden van middelen is geoptimaliseerd voor efficiëntie door betere schaling van inname, snellere uploads, snellere verwerking met behulp van microservices en bulkopname mogelijk te maken. Productmogelijkheden (webgebruikersinterfaces, desktopclients) worden bijgewerkt. Dit kan ook van invloed zijn op sommige bestaande aanpassingen.

* [!DNL Experience Manager] gebruikt het directe binaire toegangsbeginsel om activa te uploaden en te downloaden en activa microservices te gebruiken om activa te verwerken. Zie [overzicht van microservices](/help/assets/asset-microservices-overview.md).
   * Asset upload [met directe binaire toegang](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Voor technische details, zie [direct binair upload protocol en APIs](/help/assets/developer-reference-material-apis.md#upload-binary).
   * Zie [API&#39;s en elementbewerkingen](/help/assets/developer-reference-material-apis.md#use-cases-and-apis) voor een vergelijking van de beschikbare API-methoden voor standaard CRUD-bewerkingen.
* De standaardworkflow **[!UICONTROL DAM Asset Update]** in eerdere versies van [!DNL Experience Manager] is niet meer beschikbaar. In plaats daarvan, verstrekken de activa microservices een scalable, gemakkelijk beschikbare dienst die het grootste deel van de standaardactiva verwerkt (vertoningen, meta-gegevensextractie, en tekst extractie voor indexering) behandelt.
   * Zie [Elementmicroservices configureren en gebruiken](/help/assets/asset-microservices-configure-and-use.md)
   * Als u aangepaste workflowstappen in de verwerking wilt gebruiken, kunt u [workflows na verwerking](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) gebruiken.

De standaardvertoningen die met asset microservices worden gegenereerd, worden achterwaarts compatibel opgeslagen in de knooppunten van de opslagplaats van middelen met dezelfde naamgevingsconventies.

## Middelen-microservices ontwikkelen en testen {#asset-microservices}

Asset microservices bieden een schaalbare en veerkrachtige verwerking van middelen met behulp van cloudservices. Adobe beheert de cloudservices voor een optimale afhandeling van verschillende typen bedrijfsmiddelen en verwerkingsopties. Middelenmicroservices helpen u te voorkomen dat er van derden rendertools en -methoden nodig zijn (zoals ImageMagick) en vereenvoudigen configuraties, terwijl ze tevens functionaliteit bieden die buiten de box valt voor algemene bestandstypen. U kunt een [brede waaier van dossiertypes ](/help/assets/file-format-support.md) nu verwerken die meer formaten uit-van-de-doos dan wat met vorige versies van Experience Manager mogelijk is. Zo is het nu mogelijk miniatuurextractie van PSD- en PSB-indelingen uit te voeren waarvoor eerder oplossingen van derden, zoals ImageMagick, waren vereist. U kunt niet de complexe configuraties van ImageMagick voor de [!UICONTROL Processing Profiles] configuratie gebruiken. Gebruik [!DNL Dynamic Media] voor geavanceerde MPEG-transcodering van video&#39;s en gebruik verwerkingsprofielen voor [standaardtranscodering van MP4-video&#39;s](/help/assets/manage-video-assets.md#transcode-video).

Asset microservices is een service in de cloud die automatisch wordt ingericht en via [!DNL Experience Manager] wordt verzonden in programma&#39;s en omgevingen van klanten die worden beheerd in Cloud Manager. Om [!DNL Experience Manager] uit te breiden of aan te passen, kunnen de ontwikkelaars de bestaande inhoud of activa met vertoningen gebruiken die in een wolkenmilieu worden geproduceerd, om hun code te testen en te bevestigen gebruikend, tonend, downloadend activa.

Als u de code en het proces van begin tot einde wilt valideren, inclusief het opnemen en verwerken van bedrijfsmiddelen, implementeert u de codewijzigingen in een cloud-dev-omgeving met de [pijplijn](/help/implementing/cloud-manager/configure-pipeline.md) en test u met de volledige uitvoering van de verwerking van asset-microservices.


## pariteit van de eigenschap met [!DNL Experience Manager] 6.5 {#cloud-service-feature-status}

[!DNL Experience Manager] als  [!DNL Cloud Service] introduceert u veel nieuwe functies en betere manieren om bestaande functies te laten werken. Wanneer u echter van [!DNL Experience Manager] 6.5 naar [!DNL Experience Manager] als [!DNL Cloud Service] gaat, ziet u wellicht dat sommige functies anders werken, niet beschikbaar zijn of gedeeltelijk beschikbaar zijn. Hieronder volgt een lijst met dergelijke functies:

| Functionaliteit of gebruikscase | Status in [!DNL Experience Manager] als [!DNL Cloud Service] | Opmerkingen |
|-----|-----|-----|
| [Elementdetectie dupliceren](/help/assets/manage-digital-assets.md#detect-duplicate-assets) | Werkt anders. | Zie [hoe het in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/duplicate-detection.html) werkte. |
| [Alleen voor FPO-uitvoeringen (Placement Only)](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/configure-aem-assets-for-asset-link.ug.html#configfporendition) | Werkt anders |  |
| Metagegevens terugschrijven | Niet ondersteund. | Zie [metagegevensschrijver in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/xmp-writeback.html) |
| Verwerking van geüploade elementen met gebruik van Package Manager | Moet handmatig worden ingegrepen. | Handmatig opnieuw verwerken met de handeling **[!UICONTROL Reprocess Asset]**. |
| MIME-typedetectie | Niet ondersteund. | Als u een digitaal element uploadt zonder extensie of met een onjuiste extensie, wordt het mogelijk niet naar wens verwerkt. De gebruikers kunnen de binaire dossiers zonder een uitbreiding in DAM nog opslaan. Zie [MIME-typedetectie in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/detect-asset-mime-type-with-tika.html). |
| Genereren van subactiva voor samengestelde activa | Niet ondersteund. | Er is niet voldaan aan de eisen voor afhankelijk gebruik. De annotatie van PDF-bestanden met meerdere pagina&#39;s wordt bijvoorbeeld beïnvloed. Zie [maken van subelementen in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/managing-linked-subassets.html#generate-subassets). |
| Homepage | Niet ondersteund. | Zie [[!DNL Assets] Home Page experience in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-home-page.html) |
| Elementen extraheren uit ZIP-archief | Niet ondersteund. | Zie [ZIP-extractie in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.htmln#extractzip). |
| Klassieke interface | Niet ondersteund. | Alleen interface met aanraakbediening is beschikbaar. |

>[!MORELIKETHIS]
>
>De volgende bronnen zijn beschikbaar voor [!DNL Experience Manager] als [!DNL Cloud Service]:
>
>* [Een inleiding](/help/overview/introduction.md)
>* [Nieuwe en aangepaste functies](/help/overview/what-is-new-and-different.md)
>* [De architectuur](/help/core-concepts/architecture.md)
>* [Opvallende wijzigingen](/help/release-notes/aem-cloud-changes.md)
>* [Opvallende wijzigingen [!DNL Sites]](/help/sites-cloud/sites-cloud-changes.md)
>* [Videozelfstudies](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html)

