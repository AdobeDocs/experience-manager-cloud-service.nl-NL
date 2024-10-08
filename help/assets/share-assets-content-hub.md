---
title: Assets delen in  [!DNL the Content Hub]
description: Assets delen in  [!DNL the Content Hub]
role: User
exl-id: 5284d229-1596-40bf-aa5f-af4b6500ebdf
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Elementen delen in Content Hub {#search-assets-as-a-link}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![ de bannerbeeld van het Aandeel activa ](assets/share-assets-banner.png)

Het delen van elementen via een koppeling is een handige manier om de bronnen beschikbaar te maken voor [!DNL the Content Hub] -gebruikers. Met deze functionaliteit kunnen geautoriseerde gebruikers de elementen die met hen worden gedeeld, openen en downloaden. Wanneer u elementen downloadt van een gedeelde koppeling, gebruikt [!DNL the Content Hub] een asynchrone service waarmee u bestanden sneller en zonder onderbreking kunt downloaden.

## Vereisten {#prerequisites}

[ de gebruikers van Content Hub ](deploy-content-hub.md#onboard-content-hub-users) kunnen acties uitvoeren die in dit artikel worden vermeld.

## Eén element delen {#share-a-single-asset}

U kunt één element delen door de volgende stappen uit te voeren:

1. Selecteer een activa en klik het ![ pictogram van het aandeel ](assets/share.svg) om activa te delen.

   ![ het Delen van enige activa ](assets/sharing-single-asset.png)

1. Gebruik het veld **[!UICONTROL Expiration]** om een vervaldatum voor de koppeling op te geven. Selecteer een van de beschikbare opties, zoals 24 uur, 1 week, 30 dagen, 90 dagen, 1 jaar of geef een aangepaste datum op.

1. Klik op **[!UICONTROL Copy share link]**. U kunt de gekopieerde koppeling vervolgens delen met de ontvanger.

## Meerdere elementen delen {#share-multiple-assets}

Met [!DNL The Content Hub] kunt u meerdere elementen delen via een gedeelde koppeling. Voer de volgende stappen uit:

1. Selecteer elementen die u met de geautoriseerde ontvanger wilt delen. U kunt meerdere elementen een voor een selecteren of op **[!UICONTROL Select All]** klikken om alle beschikbare elementen tegelijk te selecteren. De optie **[!UICONTROL Select All]** wordt alleen weergegeven wanneer u ten minste één element selecteert.

1. Klik het ![ pictogram van het aandeel ](assets/share.svg) pictogram.

   ![ het Delen van veelvoudige activa ](assets/sharing-multiple-assets.png)

1. In de voorbeeldsectie kunt u ook elementen verwijderen naar wens. Gebruik het veld **[!UICONTROL Expiration]** om een vervaldatum voor de koppeling op te geven. Selecteer een van de beschikbare opties, zoals 24 uur, 1 week, 30 dagen, 90 dagen, 1 jaar of geef een aangepaste datum op.

1. Klik op **[!UICONTROL Copy share link]**. U kunt de gekopieerde koppeling vervolgens delen met de ontvanger.

## Elementen voorvertonen en delen {#preview-assets}

U kunt een voorvertoning weergeven van een digitaal element dat u wilt delen, voordat u het deelt met een ontvanger van de koppeling. Klik op het element waarvan u een voorvertoning wilt weergeven. [!DNL Content Hub] toont de [ gedetailleerde mening voor de activa ](asset-properties-content-hub.md).

Klik het ![ pictogram van het aandeel ](assets/share.svg) pictogram om een activa te delen. Gebruik het veld **[!UICONTROL Expiration]** om een vervaldatum voor de koppeling op te geven. Selecteer een van de beschikbare opties, zoals 24 uur, 1 week, 30 dagen, 90 dagen, 1 jaar of geef een aangepaste datum op. Klik op **[!UICONTROL Copy share link]**. U kunt de gekopieerde koppeling vervolgens delen met de ontvanger.

![ activa van de Voorproef in Content Hub ](assets/preview-assets-content-hub.png)

## Toegang tot gedeelde elementen {#access-shared-assets}

Nadat de koppeling voor elementen is gedeeld, kunnen de geautoriseerde ontvangers op de koppeling klikken om een voorbeeld van de gedeelde elementen te bekijken of deze te downloaden in een webbrowser.

Klik op de gedeelde koppeling en klik op het downloadpictogram op de elementenkaart om een element te downloaden.  U kunt ook meerdere elementen selecteren en op **[!UICONTROL Download]** klikken. <!--You can either download original assets or Original+Renditions of an asset.--> [!DNL The Content Hub] downloadt elk element één voor één naar het lokale bestandssysteem.

![ Toegang Gedeelde Verbindingen ](assets/content-hub-access-shared-links.png)
