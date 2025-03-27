---
title: Leverings-API's
description: Leer hoe u de leverings-API's kunt gebruiken.
role: User
exl-id: 806ca38f-2323-4335-bfd8-a6c79f6f15fb
source-git-commit: 2ec0b4125aa0990b6e022350a1f861fe394e6b1f
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# Leverings-API&#39;s {#delivery-apis}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

>[!AVAILABILITY]
>
>De handleiding Dynamic Media met OpenAPI-mogelijkheden is nu beschikbaar in PDF-indeling. Download de volledige handleiding en gebruik Adobe Acrobat AI Assistant om je vragen te beantwoorden.
>
>[!BADGE  Dynamische Media met OpenAPI mogelijkhedenGids PDF ]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

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

Om de leverings-API&#39;s aan te roepen, is in de `Authorization` -details een IMS-token vereist voor het leveren van een beperkt middel. De token IMS wordt opgehaald van een technische account. Zie [ Vetsen de Referenties van AEM as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) om een nieuwe technische rekening tot stand te brengen. Zie [ Genererend het toegangstoken ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) om het teken IMS te produceren en het te gebruiken geschikt in de de verzoekkopbal van levering APIs.


Om verzoeksteekproeven, reactiemonsters, en reactiecodes te bekijken, zie [ Levering APIs ](https://adobe-aem-assets-delivery.redoc.ly/#operation/getAssetSeoFormat).
