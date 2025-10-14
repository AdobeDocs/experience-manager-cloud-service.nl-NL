---
title: Uitvoeringen weergeven en beheren in Experience Manager Assets
description: Leer hoe AEM Assets en Dynamic Media effectief imagebeheer vereenvoudigen met statische en dynamische afbeeldingsuitvoeringen.
exl-id: 006dc493-c400-4d0f-b314-c1978582b7fb
feature: Renditions
role: User
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 0%

---

# Uitvoeringen weergeven en beheren in Experience Manager Assets{#renditions}

Uitvoeringen in Adobe Experience Manager (AEM) zijn aangepaste versies van digitale elementen, zoals afbeeldingen, die zijn ontworpen voor verschillende apparaten en platforms voor optimale prestaties. AEM vereenvoudigt het maken en beheren van deze uitvoeringen en verbetert de gebruikerservaring. U kunt miniaturen maken, afbeeldingen optimaliseren voor internet of mobiele apparaten, watermerken toevoegen, dynamische uitvoeringen of Smart Crop-uitvoeringen weergeven en downloaden en nog veel meer doen.

Dynamische voorinstellingen voor mediaafbeeldingen en SmartCrop-uitvoeringen bevorderen een systematisch imagebeheer dat is afgestemd op de standaarden van het merk, waardoor de cohesie van het merk wordt gemaximaliseerd. Dit vereenvoudigt het proces waarbij dynamische afbeeldingsuitvoeringen snel worden gevonden en gebruikt zonder dat er beheerfuncties beschikbaar zijn.

Uitvoeringen worden geclassificeerd als statisch en dynamisch, elk type dat unieke kenmerken en mogelijkheden presenteert die verder in detail worden besproken.

## Statische vertoningen {#static-renditions}

Statische uitvoeringen zijn vooraf gegenereerde versies van digitale elementen, die gewoonlijk worden gemaakt tijdens het opnemen of wijzigen van elementen. Deze uitvoeringen zijn geoptimaliseerd voor specifieke doeleinden en platforms, zoals webminiaturen, mobiele indelingen voor responsief ontwerp of versies met hoge resolutie voor afdrukken, zodat u over een efficiënte en consistente ervaring beschikt.
Leer hoe te [&#x200B; om statische vertoningen &#x200B;](#view-and-download-static-renditions) in Experience Manager Assets te bekijken en te downloaden.

### Statische vertoningen weergeven en downloaden{#view-and-download-static-renditions}

Voer de volgende stappen uit om de elementuitvoeringen weer te geven en te downloaden:

1. Op de Mening van Assets, klik **Assets**, navigeer aan een omslag, selecteer een activa, en klik **Details**.
1. Klik op het pictogram van de vertoning in het rechterdeelvenster.
1. Selecteer een vertoning aan voorproef het, en klik ![&#x200B; downloadpictogram &#x200B;](/help/assets/assets/download-icon.svg) om het te downloaden.

   ![&#x200B; Mening en download Dynamische vertoningen &#x200B;](/help/assets/assets/view-download-static-rendition.png)

## Dynamische uitvoeringen {#dynamic-renditions}

Dynamische uitvoeringen zijn aangepaste versies van elementen die in realtime zijn gemaakt om aan specifieke behoeften te voldoen, zoals het formaat van afbeeldingen wijzigen op basis van de apparaatresolutie of het bijsnijden om aan verschillende hoogte-breedteverhoudingen te voldoen.
Deze vertoningen stellen organisaties in staat om gepersonaliseerde en geoptimaliseerde ervaringen aan diverse publieksbehoeften te leveren. U kunt dynamische uitvoeringen weergeven en downloaden in Experience Manager Assets.

## Dynamische media-uitvoeringen {#dynamic-media-renditions}

### Voordat u begint

* U moet een AEM Dynamic Media-gebruiker met licentie zijn.
* Gebruik de lus [!UICONTROL Admin view] om in te stellen:
   * [&#x200B; Slimme Profielen van het Beeld van het Gewas &#x200B;](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles)
   * [Voorinstellingen voor afbeeldingen](/help/assets/dynamic-media/managing-image-presets.md)

  U kunt [&#x200B; schakelaar de mening &#x200B;](/help/assets/assets-view-introduction.md#how-to-access-assets-view) later aan voorproef dynamische vertoningen in de mening van Assets.
* Publiceer elementen naar Dynamic Media om dynamische media-uitvoeringen beschikbaar te maken in de Assets-weergave. Voor meer informatie, zie [&#x200B; publiceren Assets aan AEM en Dynamische Media &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm).


### Dynamische media-uitvoeringen weergeven en downloaden {#view-download-dm-renditions}

Voer de volgende stappen uit om dynamische uitvoeringen van afbeeldingen in Experience Manager Assets weer te geven of te downloaden:

1. Ga naar **[!UICONTROL Assets Management]** > **[!UICONTROL Assets]** .

1. Navigeer naar de toepasselijke elementenmap.

1. Klik op het element dat u wilt weergeven en klik op **[!UICONTROL Details]** .

1. Klik in het rechtermenu op het pictogram **[!UICONTROL Dynamic Media]** . In het deelvenster **[!UICONTROL Dynamic Media]** worden dynamische media en SmartCrop-uitvoeringen weergegeven.

   ![&#x200B; dynamische vertoningen &#x200B;](/help/assets/assets/dm-scene7-renditions.png)
   <!-- ![dynamic renditions](assets/preset_smart_crop_view.png) -->

1. Selecteer de vertoning aan voorproef en klik **Exemplaar URL** om URL van de geselecteerde vertoning te kopiëren. Klik **Vertoning van de Download** om de vertoningen van beeldactiva te downloaden.
1. Selecteer de Slimme vertoning van het Gewas aan voorproef en klik **Exemplaar URL** om URL van de geselecteerde vertoning te kopiëren.
1. Klik ![&#x200B; downloadpictogram &#x200B;](assets/do-not-localize/download-icon.png) om alle beschikbare Slimme vertoningen van het Gewas als één enkel ZIP dossier te downloaden.
   ![&#x200B; downloadpictogram &#x200B;](/help/assets/assets/smartcrop-rendition.png)

   >[!NOTE]
   >
   >Deze uitvoeringen zijn alleen beschikbaar voor afbeeldingselementen.

## Dynamische media met OpenAPI Capabilities-uitvoeringen {#dm-with-openapi-renditions}

### Voordat u begint {#prereqs-dm-with-openapi-renditions}

* U moet een AEM Dynamic Media-gebruiker met licentie zijn.
* Assets moet zijn goedgekeurd voor weergave van Dynamic Media met OpenAPI-mogelijkheden. Voor meer informatie, zie [&#x200B; activa in Experience Manager goedkeuren &#x200B;](/help/assets/approve-assets.md#copy-delivery-url-approved-assets)
* Dynamische media met OpenAPI-mogelijkheden moeten zijn ingeschakeld op uw AEM as a Cloud Service-instantie.

### Dynamische media weergeven met OpenAPI Capabilities-uitvoeringen {#view-download-dm-with-openapi-renditions}

1. Selecteer de activa en klik **Details**.
1. Klik op het pictogram Dynamische media in het rechterdeelvenster. In het deelvenster Dynamische media wordt de uitvoering Dynamische media met OpenAPI-mogelijkheden voor alle elementtypen weergegeven.
   ![&#x200B; downloadpictogram &#x200B;](/help/assets/assets/dm-with-open-api-copy-url.png)
1. Selecteer **Dynamische Media met OpenAPI** optie en klik dan **Exemplaar URL** om de levering URL van de activa te kopiëren.


