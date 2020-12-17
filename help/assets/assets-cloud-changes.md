---
title: Opvallende wijzigingen in Adobe Experience Manager Assets als a [!DNL Cloud Service]
description: Opvallende wijzigingen in Adobe Experience Manager Assets in Experience Manager [!DNL Cloud Service] ten opzichte van Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 0838f384b31c59fe95087e1a71741656eedcd13b
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---


# Noteerbare wijzigingen in Experience Manager Assets als een [!DNL Cloud Service] {#notable-changes}

Adobe Experience Manager als een [!DNL Cloud Service] biedt veel nieuwe functies en mogelijkheden om uw Experience Managers te beheren. Er zijn veel verschillen tussen Experience Manager-middelen op locatie of gehost als Adobe Beheerde service in vergelijking met [!DNL Experience Manager] als [!DNL Cloud Service]. In dit artikel worden de belangrijke verschillen voor [!DNL Assets] mogelijkheden belicht.

De belangrijkste verschillen ten opzichte van [Experience Manager] 6.5 zijn op de volgende gebieden:

* [Het opnemen, uploaden en verwerken](#asset-ingestion) van bedrijfsmiddelen.
* [Asset microservices voor cloudnative verwerking](#asset-microservices).
* [Verwijderen van klassieke gebruikersinterface](#classic-ui).

## Inname en verwerking van bedrijfsmiddelen {#asset-ingestion}

Het uploaden van middelen is geoptimaliseerd voor efficiëntie door het beter schalen van het opnemen van bedrijfsmiddelen, sneller uploaden, snellere verwerking met behulp van microservices en bulkopname mogelijk te maken. Productmogelijkheden (webgebruikersinterfaces, desktopclients) zijn bijgewerkt. Dit kan echter gevolgen hebben voor een aantal bestaande aanpassingen.

* Experience Manager gebruikt het directe binaire toegangsbeginsel voor upload en download en activa microservices voor activaverwerking. Zie [overzicht van het opnemen van elementen](/help/assets/asset-microservices-overview.md).
   * Asset upload [met directe binaire toegang](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Voor technische details, zie van [direct binair uploadprotocol en APIs](/help/assets/developer-reference-material-apis.md#upload-binary).
   * Zie [API&#39;s en elementbewerkingen](/help/assets/developer-reference-material-apis.md#use-cases-and-apis) voor een vergelijking van de beschikbare API-methoden voor standaard CRUD-bewerkingen.
* De standaardworkflow **[!UICONTROL DAM Asset Update]** in eerdere versies van [!DNL Experience Manager] is niet meer beschikbaar. In plaats daarvan, verstrekken de activa microservices een scalable, gemakkelijk beschikbare dienst die het grootste deel van de standaardactiva verwerkt (vertoningen, meta-gegevensextractie, en tekst extractie voor indexering) behandelt.
   * Zie [Elementmicroservices configureren en gebruiken](/help/assets/asset-microservices-configure-and-use.md)
   * Voor aangepaste workflowstappen in de verwerking kunt u [workflows na verwerking](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) gebruiken.
* De activa die via de Manager van het Pakket binnen komen vereisen handherverwerking gebruikend de **[!UICONTROL Reprocess Asset]** actie in de interface van Activa.

Standaarduitvoeringen die met asset microservices worden gegenereerd, worden op een manier opgeslagen die compatibel is met eerdere versies in knooppunten in de opslagplaats van middelen (dezelfde naamgevingsconventies).

## Middelen-microservices ontwikkelen en testen {#asset-microservices}

Asset microservices bieden een schaalbare en veerkrachtige verwerking van middelen met behulp van cloudservices. Adobe beheert de cloudservices voor een optimale afhandeling van verschillende typen bedrijfsmiddelen en verwerkingsopties. Middelenmicroservices helpen u te voorkomen dat er van derden rendertools en -methoden nodig zijn (zoals ImageMagick) en vereenvoudigen configuraties, terwijl ze tevens functionaliteit bieden die buiten de box valt voor algemene bestandstypen. U kunt een [brede waaier van dossiertypes ](/help/assets/file-format-support.md) nu verwerken die meer formaten uit-van-de-doos dan wat met vorige versies van Experience Manager mogelijk is. Zo is het nu mogelijk miniatuurextractie van PSD- en PSB-indelingen uit te voeren waarvoor eerder oplossingen van derden, zoals ImageMagick, waren vereist. U kunt niet de complexe configuraties van ImageMagick voor de [!UICONTROL Processing Profiles] configuratie gebruiken. Gebruik [!DNL Dynamic Media] voor geavanceerde MPEG-transcodering van video&#39;s en gebruik verwerkingsprofielen voor [standaardtranscodering van MP4-video&#39;s](/help/assets/manage-video-assets.md#transcode-video).

Asset microservices is een cloudservice die automatisch wordt ingericht en via de Experience Manager wordt verbonden in programma&#39;s en omgevingen van klanten die worden beheerd in Cloud Manager. Om Experience Manager uit te breiden of aan te passen, kunnen de ontwikkelaars de bestaande inhoud of activa met vertoningen gebruiken die in een wolkenmilieu worden geproduceerd, om hun code te testen en te bevestigen gebruikend, tonend, downloadend activa.

Als u de code en het proces van begin tot einde wilt valideren, inclusief het opnemen en verwerken van bedrijfsmiddelen, implementeert u de codewijzigingen in een cloud-dev-omgeving met de [pijplijn](/help/implementing/cloud-manager/configure-pipeline.md) en test u met de volledige uitvoering van de verwerking van asset-microservices.

## Verwijderen van klassieke gebruikersinterface {#classic-ui}

De klassieke interface is niet meer beschikbaar in de Experience Manager als [!DNL Cloud Service]. De standaardinterface is de interface met aanraakbediening.

>[!MORELIKETHIS]
>
>* [Inleiding  [!DNL Adobe Experience Manager] tot [!DNL Cloud Service]](/help/overview/introduction.md)
>* An [overview of [!DNL Experience Manager] as a [!DNL Cloud Service] - What is New and What is Different](/help/overview/what-is-new-and-different.md)
>* De [architectuur](/help/core-concepts/architecture.md) van [!DNL Experience Manager] als [!DNL Cloud Service]
>* [Opvallende wijzigingen  [!DNL Experience Manager] in [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md)
>* [Opvallende wijzigingen  [!DNL Experience Manager Sites] in [!DNL Cloud Service]](/help/sites-cloud/sites-cloud-changes.md)
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html)

