---
title: De Selecteur van activa voor  [!DNL Adobe Experience Manager]  als a  [!DNL Cloud Service]
description: Integreer de kiezer voor middelen met verschillende Adobe-, niet-Adobe- en externe toepassingen.
role: Admin, User
exl-id: 1c0051a3-549c-4783-9fc1-594f424a70c3
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Asset Selector integreren met Vanilla JS {#integration-using-vanilla-js}

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

U kunt elke [!DNL Adobe] -toepassing of niet-Adobe-toepassing integreren in de [!DNL Experience Manager Assets] -opslagplaats en elementen selecteren vanuit de toepassing. Zie [ de Integratie van de Selecteur van Activa met diverse toepassingen ](#asset-selector-integration-with-apps).

De integratie gebeurt door het pakket Asset Selector te importeren en verbinding te maken met de Assets as a Cloud Service via de Vanilla JavaScript-bibliotheek. Bewerk een `index.html` of een ander geschikt bestand in uw toepassing om:

* De verificatiedetails definiëren
* Toegang krijgen tot de Assets as a Cloud Service-opslagplaats
* De weergave-eigenschappen voor de middelenkiezer configureren

U kunt verificatie uitvoeren zonder enkele IMS-eigenschappen te definiëren, als:

* U integreert een [!DNL Adobe] toepassing op [ Verenigde Shell ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=nl-NL).
* Er is al een IMS-token gegenereerd voor verificatie.

## Asset Selector integreren met verschillende toepassingen {#asset-selector-integration-with-apps}

U kunt Asset Selector integreren met verschillende toepassingen, zoals:

* [Integreer de Selecteur van Activa met een  [!DNL Adobe]  toepassing](/help/assets/integrate-asset-selector-adobe-app.md)
* [Asset Selector integreren met een niet-Adobe-toepassing](/help/assets/integrate-asset-selector-non-adobe-app.md)
* [Integratie voor dynamische media met OpenAPI-mogelijkheden](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)


>[!MORELIKETHIS]
>
>* [ de aanpassingen van de Selecteur van Activa ](/help/assets/asset-selector-customization.md)
>* [ Eigenschappen van de Selecteur van Activa ](/help/assets/asset-selector-properties.md)
>* [ integreer de Selector van Activa met Dynamische Media met mogelijkheden OpenAPI ](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
