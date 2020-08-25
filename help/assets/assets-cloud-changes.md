---
title: Opvallende wijzigingen in Adobe Experience Manager Assets als Cloud Service
description: Opvallende wijzigingen in Adobe Experience Manager Assets in AEM Cloud Service in vergelijking met Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 0a9a462f1b92a0dcb712163574bbf57582f8145c
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 8%

---


# Notable changes to Experience Manager Assets as a Cloud Service {#notable-changes}

Adobe Experience Manager als Cloud Service biedt veel nieuwe functies en mogelijkheden om uw AEM projecten te beheren. Nochtans, zijn er vele verschillen tussen de Activa van de Experience Manager op-gebouw of in Adobe Beheerde Dienst in vergelijking met Experience Manager als Cloud Service. In dit document worden de belangrijke verschillen voor middelenmogelijkheden belicht.

De belangrijkste verschillen ten opzichte van Experience Manager 6.5 zijn op de volgende gebieden:

* [Inname en uploaden](#asset-ingestion)van bedrijfsmiddelen.
* [Asset microservices voor cloudnative verwerking](#asset-microservices).
* [Verwijderen van klassieke gebruikersinterface](#classic-ui).

>[!NOTE]
>
>In dit document worden de belangrijkste wijzigingen in AEM Assets gemarkeerd. Voor veranderingen algemeen aan AEM als Cloud Service, en andere modules, zie:
>
>* [Inleiding tot Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
>* Een [overzicht van AEM als Cloud Service - wat Nieuw is en wat verschillend is](/help/overview/what-is-new-and-different.md)
>* De [architectuur](/help/core-concepts/architecture.md) van Adobe Experience Manager as a Cloud Service
>* [Belangrijke wijzigingen in AEM as a Cloud Service (releaseopmerkingen)](/help/release-notes/aem-cloud-changes.md)
>* [Belangrijke wijzigingen in AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
>* [Tutorials voor Adobe Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/overview.html)


## Inname en uploaden van bedrijfsmiddelen {#asset-ingestion}

Het uploaden van middelen is geoptimaliseerd voor efficiëntie door het beter schalen van het opnemen van middelen en het sneller uploaden van middelen mogelijk te maken. Productmogelijkheden (webgebruikersinterfaces, desktopclients) zijn bijgewerkt. Dit kan echter gevolgen hebben voor een aantal bestaande aanpassingen.

* Experience Manager gebruikt het directe binaire toegangsbeginsel voor upload en download en activa microservices voor activaverwerking. Zie [overzicht van het opnemen van elementen](/help/assets/asset-microservices-overview.md).
   * Asset upload [met directe binaire toegang](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Voor technische details, zie van [direct binair upload protocol en APIs](/help/assets/developer-reference-material-apis.md#upload-binary).
* De standaardworkflow **[!UICONTROL DAM Asset Update]** in vorige versies van AEM is niet meer beschikbaar. In plaats daarvan bieden de assetmicroservices een schaalbare, gemakkelijk beschikbare service die het grootste deel van de standaardverwerking van middelen bestrijkt (uitvoeringen, metagegevensextractie, tekstextractie voor indexering).
   * Zie [configureren en gebruiken van assetmicroservices](/help/assets/asset-microservices-configure-and-use.md)
   * Voor aangepaste workflowstappen in de verwerking kunnen [naverwerkingsworkflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) worden gebruikt.
* Elementen die via Package Manager worden binnengebracht, moeten handmatig worden opgebouwd met behulp van de **[!UICONTROL Reprocess Asset]** handeling in de Elementeninterface.

Standaarduitvoeringen die met asset microservices worden gegenereerd, worden op een manier opgeslagen die compatibel is met eerdere versies in knooppunten in de opslagplaats van middelen (dezelfde naamgevingsconventies).

## Middelen-microservices ontwikkelen en testen {#asset-microservices}

Asset microservices bieden een schaalbare en veerkrachtige verwerking van middelen met behulp van cloudservices. Adobe beheert de cloudservices voor een optimale afhandeling van verschillende typen bedrijfsmiddelen en verwerkingsopties. Middelenmicroservices helpen u te voorkomen dat er van derden rendertools en -methoden nodig zijn (zoals ImageMagick) en vereenvoudigen configuraties, terwijl ze tevens functionaliteit bieden die buiten de box valt voor algemene bestandstypen. U kunt nu een [groot aantal bestandstypen](/help/assets/file-format-support.md) verwerken die meer indelingen buiten het vak bestrijken dan met eerdere versies van Experience Manager mogelijk is. Zo is het nu mogelijk miniatuurextractie van PSD- en PSB-indelingen uit te voeren waarvoor eerder oplossingen van derden, zoals ImageMagick, waren vereist. U kunt niet de complexe configuraties van ImageMagick voor de [!UICONTROL Processing Profiles] configuratie gebruiken. Gebruik deze optie ook [!DNL Dynamic Media] voor MPEG-transcodering van video&#39;s.

Asset microservices is een cloudservice die automatisch wordt ingericht en via de Experience Manager wordt verbonden in programma&#39;s en omgevingen van klanten die worden beheerd in Cloud Manager. Om Experience Manager uit te breiden of aan te passen, kunnen de ontwikkelaars de bestaande inhoud of activa met vertoningen gebruiken die in een wolkenmilieu worden geproduceerd, om hun code te testen en te bevestigen gebruikend, tonend, downloadend activa.

Om een volledige bevestiging van de code en het proces met inbegrip van activa het opnemen en verwerking te doen, stel de codeveranderingen in een wolk-ontwikkelomgeving op gebruikend [de pijpleiding](/help/implementing/cloud-manager/configure-pipeline.md) en test met volledige uitvoering van activa microservices verwerking.

## Verwijderen van klassieke gebruikersinterface {#classic-ui}

De klassieke gebruikersinterface is niet meer beschikbaar in de Experience Manager als Cloud Service. De standaardinterface is de interface met aanraakbediening.
