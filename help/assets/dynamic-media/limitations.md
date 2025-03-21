---
title: Dynamische mediabeperkingen
description: Leer over de beste praktijken en de gedwongen grenzen wanneer u een Reeks van het Beeld of een Reeks van de Draai creeert, of een PDF uploadt. Meer informatie over niet-ondersteunde combinaties van webbrowsers en besturingssystemen voor Dynamic Media.
contentOwner: Rick Brough
content-type: reference
products: SG_EXPERIENCEMANAGER/Dynamic-Media-Classic
geptopics: SG_SCENESEVENONDEMAND_PK/categories/ecatalogs
feature: Dynamic Media Classic,Asset Management,Image Sets,Spin Sets,eCatalog
role: User
exl-id: fb63e2d4-2c8c-48dd-a0dc-fdfbbfb57b30
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 1%

---

# Dynamische medialimieten

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

In de volgende secties worden beperkingen in Dynamic Media beschreven.

Dit onderwerp omvat de volgende secties:

* [Best practices en gedwongen beperkingen door Dynamic Media voor elementtypen](#best-practice-enforced-limits)
* [Niet-ondersteunde combinaties van webbrowser en besturingssysteem voor Dynamic Media](#unsupported-browser-os)

## Best practices en gedwongen beperkingen door Dynamic Media voor elementtypen {#best-practice-enforced-limits}

Als u een centrifugeset of een Afbeeldingsset maakt of PDF&#39;s uploadt voor het uitnemen van pagina&#39;s, raadt Adobe de volgende aanbevolen procedures aan en past het de volgende limieten toe:

| Element - Type limiet | Beste praktijken | Oplegde limiet |
| --- | --- | --- |
| **Beeld** - Aantal Slimme Gewas per beeld | 5 | 100 |
| **Alle reeksen** - Aantal dubbele activa per reeks | Geen duplicaten | 20 |
| **Alle reeksen** - Maximum aantal activa per reeks | 5-10 afbeeldingen per set | 1000 |
| **Reeks van de Draai** - Maximum aantal rijen/kolommen per 2D reeks | 12-18 afbeeldingen per set | 1000 |
| **PDF** - Maximum aantal pagina&#39;s voor PDF dat voor extractie moet worden overwogen |  | 100 (voor alle PDF&#39;s) |

<!-- See also [Dynamic Media limitations](/help/assets/limitations.md). -->

## Niet-ondersteunde combinaties van webbrowser en besturingssysteem voor Dynamic Media {#unsupported-browser-os}

Dynamic Media ondersteunt de volgende combinaties van webbrowsers en besturingssystemen niet.

* Internet Explorer 11 + Windows 7
* Internet Explorer 11 + Windows 8.1
* Internet Explorer 11 + Windows Phone 8.1
* Internet Explorer 11 + Windows Phone 8.1-update
* Safari 6 + iOS 6.0.1
* Safari 7 + iOS 7.1
* Safari 7 + OS X 10.9 Mavericks
* Safari 8 + iOS 8.4
* Safari 8 + OS X 10.10 Yosemite

## Einde van steun voor Veilige Laag 2.0 en 3.0 van de Contactdoos en de Veiligheid van de Laag van het Vervoer 1.0 en 1.1 {#tls}

<!-- CQDOC-19433 (original ticket)
and CQDOC-19792 (removed as per this ticket December 5, 2022) -->

Vanaf 30 april 2024 eindigt de ondersteuning voor Adobe Dynamic Media voor:

* SSL (Secure Socket Layer) 2.0
* SSL 3.0
* TLS (Transport Layer Security) 1.0 en 1.1
* De volgende zwakke ciphers in TLS 1.2:
   * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
   * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
   * `TLS_RSA_WITH_AES_256_GCM_SHA384`
   * `TLS_RSA_WITH_AES_256_CBC_SHA256`
   * `TLS_RSA_WITH_AES_256_CBC_SHA`
   * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
   * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
   * `TLS_RSA_WITH_AES_128_GCM_SHA256`
   * `TLS_RSA_WITH_AES_128_CBC_SHA256`
   * `TLS_RSA_WITH_AES_128_CBC_SHA`
   * `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
   * `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
   * `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
   * `TLS_RSA_WITH_SDES_EDE_CBC_SHA`
