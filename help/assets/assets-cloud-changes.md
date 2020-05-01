---
title: Opvallende wijzigingen in Adobe Experience Manager-middelen als cloudservice
description: Opmerkelijke wijzigingen in de Adobe Experience Manager-middelen in AEM Cloud Service in vergelijking met Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 37ff6912837ba78c90526e8f8322b9002e9a4304

---


# Notable changes to Experience Manager Assets as a Cloud Service {#notable-changes}

Adobe Experience Manager als Cloud Service biedt veel nieuwe functies en mogelijkheden om uw AEM-projecten te beheren. Er zijn echter veel verschillen tussen de middelen van Experience Manager op locatie of in de beheerde service van Adobe in vergelijking met Experience Manager als cloudservice. In dit document worden de belangrijke verschillen voor middelenmogelijkheden belicht. Voor andere veranderingen, zie de generische [veranderingen in de Manager van de Ervaring als de Dienst](/help/release-notes/aem-cloud-changes.md)van de Wolk.

De belangrijkste verschillen ten opzichte van Experience Manager 6.5 zijn op de volgende gebieden:

* [Inname en uploaden](#asset-ingestion)van bedrijfsmiddelen.
* [Asset microservices voor cloudverwerking](#asset-microservices).
* [Verwijderen van klassieke gebruikersinterface](#classic-ui).

## Inname en uploaden van bedrijfsmiddelen {#asset-ingestion}

Het uploaden van middelen is geoptimaliseerd voor efficiëntie door het beter schalen van het opnemen van middelen en het sneller uploaden van middelen mogelijk te maken. Productmogelijkheden (webgebruikersinterfaces, desktopclients) zijn bijgewerkt. Dit kan echter gevolgen hebben voor een aantal bestaande aanpassingen.

* De Manager van de ervaring gebruikt direct binair toegangsbeginsel voor upload en download en activa microservices voor activaverwerking. Zie [overzicht van het opnemen van elementen](/help/assets/asset-microservices-overview.md).
   * Asset upload [met directe binaire toegang](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Voor technische details, zie van [direct binair upload protocol en APIs](/help/assets/developer-reference-material-apis.md#overview-binary-upload).
* De standaardworkflow **[!UICONTROL DAM Asset Update]** in eerdere versies van AEM is niet meer beschikbaar. In plaats daarvan bieden de assetmicroservices een schaalbare, gemakkelijk beschikbare service die het grootste deel van de standaardverwerking van middelen bestrijkt (uitvoeringen, metagegevensextractie, tekstextractie voor indexering).
   * Zie [configureren en gebruiken van assetmicroservices](/help/assets/asset-microservices-configure-and-use.md)
   * Voor aangepaste workflowstappen in de verwerking kunnen [naverwerkingsworkflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) worden gebruikt.
* Middelen die via Package Manager worden binnengebracht, moeten handmatig worden opgerold met behulp van de handeling **[!UICONTROL Element]** opnieuw verwerken in de interface Middelen.

Standaarduitvoeringen die met asset microservices worden gegenereerd, worden op een manier opgeslagen die compatibel is met eerdere versies in knooppunten in de opslagplaats van middelen (dezelfde naamgevingsconventies).

## Middelen-microservices ontwikkelen en testen {#asset-microservices}

Asset microservices bieden een schaalbare en veerkrachtige verwerking van middelen met behulp van cloudservices. Adobe beheert de cloudservices voor een optimale verwerking van verschillende elementtypen en verwerkingsopties. Middelenmicroservices helpen u te voorkomen dat er van derden rendertools en -methoden nodig zijn (zoals ImageMagick) en vereenvoudigen configuraties, terwijl ze tevens functionaliteit bieden die buiten de box valt voor algemene bestandstypen. U kunt nu een [groot aantal bestandstypen](/help/assets/file-format-support.md) verwerken die meer indelingen buiten het vak bestrijken dan met eerdere versies van Experience Manager mogelijk is. Zo is het nu mogelijk miniatuurextractie van PSD- en PSB-indelingen uit te voeren waarvoor eerder oplossingen van derden, zoals ImageMagick, waren vereist. U kunt niet de complexe configuraties van ImageMagick voor de configuratie van Profielen [!UICONTROL van de] Verwerking gebruiken. Gebruik deze optie ook [!DNL Dynamic Media] voor MPEG-transcodering van video&#39;s.

Asset microservices is een cloudservice die automatisch wordt ingericht en bekabeld voor Experience Manager in programma&#39;s en omgevingen die worden beheerd in Cloud Manager. Om Experience Manager uit te breiden of aan te passen, kunnen de ontwikkelaars de bestaande inhoud of elementen gebruiken met uitvoeringen die zijn gegenereerd in een wolkenomgeving, om hun code te testen en te valideren met behulp van, het weergeven en downloaden van elementen.

Om een volledige bevestiging van de code en het proces met inbegrip van activa het opnemen en verwerking te doen, stel de codeveranderingen in een wolk-ontwikkelomgeving op gebruikend [de pijpleiding](/help/implementing/cloud-manager/configure-pipeline.md) en test met volledige uitvoering van activa microservices verwerking.

## Verwijderen van klassieke gebruikersinterface {#classic-ui}

De klassieke gebruikersinterface is niet meer beschikbaar in Experience Manager als cloudservice. De standaardinterface is de interface met aanraakbediening.
