---
title: Opvallende wijzigingen in Adobe Experience Manager Assets als Cloud Service
description: Opvallende wijzigingen in activa van Adobe Experience Managers in AEM Cloud Service in vergelijking met Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: e381807d7c199113689304e9481dfe2022ee5f93
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 5%

---


# Notable changes to Experience Manager Assets as a Cloud Service {#notable-changes}

Adobe Experience Manager als Cloud Service biedt veel nieuwe functies en mogelijkheden om uw AEM-projecten te beheren. Er zijn echter veel verschillen tussen Experience Manager Assets on-premise of in Adobe Managed Service in vergelijking met Experience Manager als Cloud Service. In dit document worden de belangrijke verschillen voor middelenmogelijkheden belicht.

De belangrijkste verschillen ten opzichte van Experience Manager 6.5 zijn op de volgende gebieden:

* [Inname en uploaden](#asset-ingestion)van bedrijfsmiddelen.
* [Asset microservices voor cloudverwerking](#asset-microservices).
* [Verwijderen van klassieke gebruikersinterface](#classic-ui).

>[!NOTE]
>In dit document worden de belangrijkste wijzigingen in AEM Assets gemarkeerd. Voor veranderingen algemeen in AEM als Cloud Service, en andere modules, zie:
>
>* [Inleiding tot Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
>* Een [overzicht van AEM als Cloud Service - wat Nieuw is en wat verschillend is](/help/overview/what-is-new-and-different.md)
>* De [architectuur](/help/core-concepts/architecture.md) van Adobe Experience Manager as a Cloud Service
>* [Opvallende wijzigingen in AEM als Cloud Service (opmerkingen bij de release)](/help/release-notes/aem-cloud-changes.md)
>* [Opvallende wijzigingen in AEM Sites als Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
>* [Zelfstudies voor Adobe Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/overview.html)


## Inname en uploaden van bedrijfsmiddelen {#asset-ingestion}

Het uploaden van middelen is geoptimaliseerd voor efficiëntie door het beter schalen van het opnemen van middelen en het sneller uploaden van middelen mogelijk te maken. Productmogelijkheden (webgebruikersinterfaces, desktopclients) zijn bijgewerkt. Dit kan echter gevolgen hebben voor een aantal bestaande aanpassingen.

* Experience Manager hanteert het directe binaire toegangsprincipe voor het uploaden en downloaden en voor elementmicroservices voor het verwerken van bedrijfsmiddelen. Zie [overzicht van het opnemen van elementen](/help/assets/asset-microservices-overview.md).
   * Asset upload [met directe binaire toegang](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Voor technische details, zie van [direct binair upload protocol en APIs](/help/assets/developer-reference-material-apis.md#overview-binary-upload).
* De standaardworkflow **[!UICONTROL DAM Asset Update]** in eerdere versies van AEM is niet meer beschikbaar. In plaats daarvan bieden de assetmicroservices een schaalbare, gemakkelijk beschikbare service die het grootste deel van de standaardverwerking van middelen bestrijkt (uitvoeringen, metagegevensextractie, tekstextractie voor indexering).
   * Zie [configureren en gebruiken van asset microservices](/help/assets/asset-microservices-configure-and-use.md)
   * Voor aangepaste workflowstappen in de verwerking kunnen [naverwerkingsworkflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) worden gebruikt.
* Elementen die via Package Manager worden binnengebracht, moeten handmatig worden opgebouwd met behulp van de **[!UICONTROL Reprocess Asset]** handeling in de Elementeninterface.

Standaarduitvoeringen die met asset microservices worden gegenereerd, worden op een manier opgeslagen die compatibel is met eerdere versies in knooppunten in de opslagplaats van middelen (dezelfde naamgevingsconventies).

## Middelen-microservices ontwikkelen en testen {#asset-microservices}

Asset microservices bieden een schaalbare en veerkrachtige verwerking van middelen met behulp van cloudservices. Adobe beheert de cloudservices voor een optimale verwerking van verschillende elementtypen en verwerkingsopties. Middelenmicroservices helpen u te voorkomen dat er van derden rendertools en -methoden nodig zijn (zoals ImageMagick) en vereenvoudigen configuraties, terwijl ze tevens functionaliteit bieden die buiten de box valt voor algemene bestandstypen. U kunt nu een [groot aantal bestandstypen](/help/assets/file-format-support.md) verwerken die meer indelingen buiten het vak bestrijken dan in eerdere versies van Experience Manager mogelijk is. Zo is het nu mogelijk miniatuurextractie van PSD- en PSB-indelingen uit te voeren waarvoor eerder oplossingen van derden, zoals ImageMagick, waren vereist. U kunt niet de complexe configuraties van ImageMagick voor de [!UICONTROL Processing Profiles] configuratie gebruiken. Gebruik deze optie ook [!DNL Dynamic Media] voor MPEG-transcodering van video&#39;s.

Asset microservices is een cloudservice die automatisch wordt ingericht en via Experience Manager wordt verzonden in programma&#39;s en omgevingen van klanten die worden beheerd in Cloud Manager. Om Experience Manager uit te breiden of aan te passen, kunnen de ontwikkelaars de bestaande inhoud of activa met vertoningen gebruiken die in een wolkenmilieu worden geproduceerd, om hun code te testen en te bevestigen gebruikend, tonend, downloadend activa.

Om een volledige bevestiging van de code en het proces met inbegrip van activa het opnemen en verwerking te doen, stel de codeveranderingen in een wolk-ontwikkelomgeving op gebruikend [de pijpleiding](/help/implementing/cloud-manager/configure-pipeline.md) en test met volledige uitvoering van activa microservices verwerking.

## Verwijderen van klassieke gebruikersinterface {#classic-ui}

De klassieke gebruikersinterface is niet meer beschikbaar in Experience Manager als Cloud Service. De standaardinterface is de interface met aanraakbediening.
