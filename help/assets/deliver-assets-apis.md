---
title: Leverings-API's
description: Leer hoe u de leverings-API's kunt gebruiken.
role: User
exl-id: 806ca38f-2323-4335-bfd8-a6c79f6f15fb
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# Leverings-API&#39;s {#delivery-apis}

Alle [ goedgekeurde activa ](approve-assets.md) beschikbaar in de activa van Experience Manager bewaarplaats kan [ worden gezocht ](search-assets-api.md) en dan aan geïntegreerde stroomafwaartse toepassingen worden geleverd gebruikend een Levering URL.

Wijzigingen die worden aangebracht in goedgekeurde elementen in DAM, inclusief versies-updates en wijzigingen in metagegevens, worden automatisch doorgevoerd in de URL&#39;s van de levering. Met een korte tijd-aan-Levende (TTL) waarde van 10 minuten die voor activa levering via CDN wordt gevormd, worden de updates zichtbaar over alle creatie en gepubliceerde interfaces binnen onder 10 minuten.

De volgende afbeelding illustreert de beschikbare URL&#39;s voor levering:

![ Levering APIs ](assets/delivery-url.png)

In de volgende tabel wordt het gebruik van de verschillende beschikbare API&#39;s voor levering geïllustreerd:

| Leverings-API | Beschrijving |
|---|---|
| [ Web-geoptimaliseerde binaire vertegenwoordiging van de activa in gevraagd uitvoerformaat ](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat) | Retourneert de voor het web geoptimaliseerde binaire representatie van het element in de gevraagde uitvoerindeling op basis van de element-id die in de aanvraag is verzonden. Bovendien kunt u diverse beeldbepalingen zoals, breedte, hoogte bepalen, roteren, afknippen, kwaliteit, gewas, formaat, en [ slimme gewas ](/help/assets/dynamic-media/image-profiles.md). Zie [ API details ](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat) voor gesteunde formaten en beeldbepalingen.<br> Adobe adviseert gebruikend dit API voor alle types van beeldformaat. |
| [ Web-geoptimaliseerde binaire vertegenwoordiging van de activa ](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAsset) | API voor gebruiksgemak die standaard wordt toegepast op een voor het web geoptimaliseerde binaire representatie van het element dat in de reactie wordt geretourneerd. De standaardwaarden zijn JPEG/WEBP, quality => 65 en width => 1024. |
| [ Origineel geupload binair getal van de activa ](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetOriginal) | Retourneert de oorspronkelijk geüploade binaire bestanden voor het element. Adobe raadt u aan deze API te gebruiken voor documentindelingstypen en SVG-afbeeldingen. |
| [ pre-geproduceerde vertoning van de activa beschikbaar op het auteursmilieu van AEM Assets ](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetRendition) | Retourneert de bitstream van de elementuitvoering die beschikbaar is in de AEM Assets-ontwerpomgeving op basis van de element-id en de naam van de uitvoering die in de aanvraag is verzonden. |
| [ meta-gegevens van Activa ](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetMetadata) | Retourneert de eigenschappen die aan een element zijn gekoppeld, zoals titel, beschrijving, CreateDate, ModifyDate enzovoort. |
| [ de container van de Speler voor de videoactiva ](https://adobe-aem-assets-delivery.redoc.ly/#operation/videoPlayerDelivery) | Retourneert de spelercontainer voor het video-element. U kunt de speler insluiten in een iFrame HTML-element en de video afspelen. |
| [ manifests van de Playback in het geselecteerde outputformaat ](https://adobe-aem-assets-delivery.redoc.ly/#operation/videoManifestDelivery) | Retourneert het afspeelmanifestbestand voor het opgegeven video-element in de geselecteerde uitvoerindeling. U moet een aangepaste speler maken die het afspeelmanifestbestand kan ophalen en de video kan afspelen door middel van HLS- of DASH-protocollen. |

Dynamische media met OpenAPI-mogelijkheden ondersteunen ook lange formuliervideo&#39;s. De video&#39;s kunnen tot 50 GB en 2 uur steunen.

Voor informatie over het beschikbare Dynamische dienstenaanbod van Media en hun mogelijkheden, zie [ Dynamische Media Prime en Ultimate ](/help/assets/dynamic-media/dm-prime-ultimate.md).

## Eindpunten van bezorgings-API&#39;s {#delivery-apis-endpoint}

De API eindpunten variëren voor elke levering API. Het API-eindpunt voor de `Web-optimized binary representation of the asset in the requested output format` API is bijvoorbeeld:
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/{assetId}/as/{seoName}.{format}`

Het leveringsdomein is qua structuur vergelijkbaar met het domein van de Experience Manager-auteuromgeving. Het enige verschil is het vervangen van de term `author` door `delivery` .

`pXXXX` verwijst naar de programma-id

`eYYYY` verwijst naar de milieu-id

Zie [ API details ](https://adobe-aem-assets-delivery.redoc.ly/#tag/Assets) voor meer informatie.

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

Om de leverings-API&#39;s aan te roepen, is in de `Authorization` -details een IMS-token vereist voor het leveren van een beperkt middel. De token IMS wordt opgehaald van een technische account. Zie [ Vetsen de Referenties van AEM as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=nl-NL#fetch-the-aem-as-a-cloud-service-credentials) om een nieuwe technische rekening tot stand te brengen. Zie [ Genererend het toegangstoken ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=nl-NL#generating-the-access-token) om het teken IMS te produceren en het te gebruiken geschikt in de de verzoekkopbal van levering APIs.


Om verzoeksteekproeven, reactiemonsters, en reactiecodes te bekijken, zie [ Levering APIs ](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat).
