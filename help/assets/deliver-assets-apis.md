---
title: Leverings-API's
description: Leer hoe u de leverings-API's kunt gebruiken.
role: User
source-git-commit: 540aa876ba7ea54b7ef4324634f6c5e220ad19d3
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# Leverings-API&#39;s {#delivery-apis}

Alles [goedgekeurde activa](approve-assets.md) beschikbaar zijn in de gegevensopslagplaats van Experience Manager [doorzocht](search-assets-api.md) en wordt vervolgens geleverd aan geïntegreerde downstreamtoepassingen met behulp van een Delivery URL.

Wijzigingen die worden aangebracht in goedgekeurde elementen in DAM, inclusief versies-updates en wijzigingen in metagegevens, worden automatisch doorgevoerd in de URL&#39;s van de levering. Met een korte tijd-aan-Levende (TTL) waarde van 10 minuten die voor activa levering via CDN wordt gevormd, worden de updates zichtbaar over alle creatie en gepubliceerde interfaces binnen onder 10 minuten.

De volgende afbeelding illustreert de beschikbare URL&#39;s voor levering:

![Leverings-API&#39;s](assets/delivery-url.png)

In de volgende tabel wordt het gebruik van de verschillende beschikbare API&#39;s voor levering geïllustreerd:

| Leverings-API | Beschrijving |
|---|---|
| [Web-geoptimaliseerde binaire vertegenwoordiging van de activa in gevraagde outputformaat](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetSeoFormat) | Retourneert de voor het web geoptimaliseerde binaire representatie van het element in de gevraagde uitvoerindeling op basis van de element-id die in de aanvraag is verzonden. Daarnaast kunt u verschillende afbeeldingsaanpassingen definiëren, zoals breedte, hoogte, roteren, spiegelen, kwaliteit, uitsnijden, opmaken en [slim uitsnijden](/help/assets/dynamic-media/image-profiles.md). Zie de [API-details](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetSeoFormat) voor ondersteunde indelingen en afbeeldingsmodifiers.<br>Adobe raadt u aan deze API te gebruiken voor alle typen afbeeldingsindelingen. |
| [Web-geoptimaliseerde binaire vertegenwoordiging van de activa](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAsset) | API voor gebruiksgemak die standaard wordt toegepast op een voor het web geoptimaliseerde binaire representatie van het element dat in de reactie wordt geretourneerd. De standaardinstellingen zijn onder andere de standaardinstellingen JPEG/WEBP, quality => 65 en width => 1024. |
| [Oorspronkelijk geüploade binair getal van het element](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetOriginal) | Retourneert de oorspronkelijk geüploade binaire bestanden voor het element. Adobe raadt u aan deze API te gebruiken voor typen documentindelingen en SVG-afbeeldingen. |
| [Vooraf gegenereerde uitvoering van het beschikbare element in de AEM Assets-ontwerpomgeving](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetRendition) | Retourneert de bitstream van de elementuitvoering die beschikbaar is in de AEM Assets-ontwerpomgeving op basis van de element-id en de naam van de uitvoering die in de aanvraag is verzonden. |
| [Metagegevens van element](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetMetadata) | Retourneert de eigenschappen die aan een element zijn gekoppeld, zoals titel, beschrijving, CreateDate, ModifyDate enzovoort. |
| [Player-container voor het video-element](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/videoPlayerDelivery) | Retourneert de spelercontainer voor het video-element. U kunt de speler insluiten in een iframe HTML-element en de video afspelen. |
| [Afspeelmanifesten in de geselecteerde indeling](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/videoManifestDelivery) | Retourneert het afspeelmanifestbestand voor het opgegeven video-element in de geselecteerde uitvoerindeling. U moet een aangepaste speler maken die het afspeelmanifestbestand kan ophalen en de video kan afspelen door middel van HLS- of DASH-protocollen. |

## Eindpunten van bezorgings-API&#39;s {#delivery-apis-endpoint}

De API eindpunten variëren voor elke levering API. Het API-eindpunt voor `Web-optimized binary representation of the asset in the requested output format` API is:
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/{assetId}/as/{seoName}.{format}`

Het leveringsdomein is gelijkaardig in structuur aan het domein van de de auteur van de Experience Manager. Het enige verschil is het vervangen van de term `author` with `delivery`.

`pXXXX` verwijst naar de programma-id

`eYYYY` verwijst naar de milieu-id

Zie [API-details](https://adobe-aem-assets-delivery-experimental.redoc.ly/#tag/Assets) voor meer informatie .

## Aanvraagmethode voor bezorgings-API&#39;s {#delivery-api-request-method}

GET

## Leverings-API&#39;s {#deliver-assets-api-header}

U moet de volgende details verstrekken terwijl het bepalen van een kopbal in de kopbal van levering APIs:

```java
headers: {
      'If-None-Match': 'string',
      Authorization: 'Bearer <YOUR_JWT_HERE>'
    }
```

Voor het aanroepen van de API&#39;s voor levering is een IMS-token vereist in het dialoogvenster `Authorization` details om een beperkt actief te leveren. De token IMS wordt opgehaald van een technische account. Zie [Credentials van AEM as a Cloud Service ophalen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) om een nieuwe technische rekening op te stellen. Zie [Het toegangstoken genereren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) om het token IMS te genereren en het op de juiste wijze te gebruiken in de aanvraagheader van de API voor levering.

Als u aanvraagvoorbeelden, responsvoorbeelden en responscodes wilt weergeven, raadpleegt u [Leverings-API&#39;s](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/getAssetSeoFormat).

