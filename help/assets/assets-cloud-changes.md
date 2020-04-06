---
title: Opvallende wijzigingen in Adobe Experience Manager-middelen als cloudservice
description: Opmerkelijke wijzigingen in de Adobe Experience Manager-middelen in AEM Cloud Service in vergelijking met Experience Manager 6.5
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Notable changes to Experience Manager Assets as a Cloud Service {#notable-changes}

Adobe Experience Manager als Cloud Service biedt veel nieuwe functies en mogelijkheden om uw AEM-projecten te beheren. Er zijn echter een aantal verschillen tussen Experience Manager-middelen op locatie of in Adobe Managed Service in vergelijking met Experience Manager als cloudservice. In dit document worden de belangrijke verschillen belicht.

>[!NOTE]
>
>In dit document worden de opmerkelijke wijzigingen gemarkeerd die specifiek zijn voor Experience Manager Assets als Cloud Service. Zie de algemene [wijzigingen in Experience Manager als Cloud Service](/help/release-notes/aem-cloud-changes.md).

De belangrijkste verschillen ten opzichte van Experience Manager 6.5 zijn op de volgende gebieden:

* [Inname van bedrijfsmiddelen](#asset-ingestion)
* [Verwijderen van klassieke gebruikersinterface](#classic-ui)

## Inname van bedrijfsmiddelen {#asset-ingestion}

Het uploaden van middelen is geoptimaliseerd om efficiënter het toelaten van activa het opnemen van activa en snellere uploads toe te laten. Productmogelijkheden (webgebruikersinterfaces, desktopclients) zijn bijgewerkt. Dit kan echter invloed hebben op sommige bestaande aangepaste code.

* De Manager van de ervaring gebruikt direct binair toegangsbeginsel voor upload en download en activa microservices voor activaverwerking. Zie [Overzicht van het opnemen van elementen](/help/assets/asset-microservices-overview.md)
   * Middelen uploaden [met directe binaire toegang](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access)
   * Voor technische details, zie van [direct binair upload protocol en APIs](/help/assets/developer-reference-material-apis.md#overview-binary-upload)
* De standaardworkflow **[!UICONTROL DAM Asset Update]** in eerdere versies van AEM is niet meer beschikbaar. In plaats daarvan bieden de assetmicroservices een schaalbare, gemakkelijk beschikbare service die het grootste deel van de standaardverwerking van middelen bestrijkt (uitvoeringen, metagegevensextractie, tekstextractie voor indexering).
   * Zie [configureren en gebruiken van assetmicroservices](/help/assets/asset-microservices-configure-and-use.md)
   * Voor aangepaste workflowstappen in de verwerking kunnen [naverwerkingsworkflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) worden gebruikt
* Elementen die via Package Manager worden binnengebracht, moeten handmatig opnieuw worden verwerkt met behulp van de handeling **[!UICONTROL Element]** opnieuw verwerken in de interface Elementen.

Standaarduitvoeringen die met asset microservices worden gegenereerd, worden op een manier opgeslagen die compatibel is met eerdere versies in knooppunten in de opslagplaats van middelen (dezelfde naamgevingsconventies).

## Middelen-microservices ontwikkelen en testen {#developing-testing-asset-microservices}

Asset microservices is een native cloudservice die automatisch wordt ingericht en bekabeld voor Experience Manager in programma&#39;s en omgevingen die worden beheerd in Cloud Manager. Ontwikkelaars die werken om Experience Manager uit te breiden of aangepaste bewerkingen uit te voeren, kunnen de bestaande inhoud (of elementen met uitvoeringen die zijn gegenereerd in een cloud-omgeving) gebruiken om hun code te testen en te valideren met behulp van, het weergeven en downloaden van elementen.

Om een volledige bevestiging van de code en het proces met inbegrip van activaopname en verwerking te doen, stel de codeveranderingen in een wolk-ontwikkelomgeving op gebruikend de pijpleiding en test met volledige uitvoering van de verwerking van activa-microdiensten.

## Verwijderen van klassieke gebruikersinterface {#classic-ui}

De klassieke gebruikersinterface is niet meer beschikbaar in Experience Manager als cloudservice.
